### 📚 Kubernetes Cluster Setup - Complete Documentation
**What You Need to Set Up a Kubernetes Cluster from Scratch**

### 🏗️ Overview: Cluster Setup Flow

<pre>
+-----------------------------------------------------------------------------+
|                        KUBERNETES CLUSTER SETUP FLOW                        |
|                                                                             |
| STEP 1: Prerequisites (All Nodes)                                           |
| |-- Disable Swap                                                            |
| |-- Load Kernel Modules (overlay, br_netfilter)                             |
| |-- Configure Sysctl Parameters (IP forwarding, bridge)                     |
| `-- Install Base Tools                                                      |
|                           |                                                 |
|                           v                                                 |
| STEP 2: Container Runtime (All Nodes)                                       |
| |-- Install Containerd                                                      |
| |-- Install Runc                                                            |
| |-- Install CNI Plugins                                                     |
| `-- Configure Containerd (SystemdCgroup, sandbox image)                     |
|                           |                                                 |
|                           v                                                 |
| STEP 3: Kubernetes Tools (All Nodes)                                        |
| |-- Install kubeadm                                                         |
| |-- Install kubelet                                                         |
| |-- Install kubectl                                                         |
| `-- Configure Kubelet (Node IP)                                             |
|                           |                                                 |
|                           v                                                 |
| STEP 4: Initialize Cluster (Master Only)                                    |
| |-- kubeadm init                                                            |
| |-- Setup kubeconfig                                                        |
| |-- Install CNI (Calico/Flannel)                                            |
| `-- Generate join command                                                   |
|                           |                                                 |
|                           v                                                 |
| STEP 5: Join Workers (Workers Only)                                         |
| `-- kubeadm join                                                            |
|                           |                                                 |
|                           v                                                 |
|  READY!                                                                     |
|                                                                             |
+-----------------------------------------------------------------------------+
</pre>

### 📋 Detailed Requirements
**1️⃣ PREREQUISITES (All Nodes)**

**A. Disable Swap**
```
# Why: Kubernetes requires swap to be disabled for proper memory management
swapoff -a
sed -i '/swap/d' /etc/fstab
```

| Requirement    | Reason                                             |
| :------------- | :------------------------------------------------- |
| **Swap OFF**   | Kubelet won't start if swap is enabled             |
| `overlay`      | Required for overlay filesystem (container layers) |
| `br_netfilter` | Required for iptables to see bridged traffic       |

**B. Kernel Modules**
```
# Why: Required for container networking
cat <<EOF | tee /etc/modules-load.d/k8s.conf
overlay
br_netfilter
EOF

modprobe overlay
modprobe br_netfilter
```

| Requirement  | Reason                                 |
| ------------ | -------------------------------------- |
| **Swap OFF** | Kubelet won't start if swap is enabled |
| `overlay`    | Required for overlay filesystem        |

**C. Sysctl Parameters**
```
# Why: Enable network forwarding and bridge traffic filtering
cat <<EOF | tee /etc/sysctl.d/k8s.conf
net.bridge.bridge-nf-call-iptables  = 1
net.bridge.bridge-nf-call-ip6tables = 1
net.ipv4.ip_forward                 = 1
EOF

sysctl --system
```

| Requirement                           | Reason                                                 |
| :------------------------------------ | :----------------------------------------------------- |
| `net.bridge.bridge-nf-call-iptables`  | Allow `iptables` to filter bridge traffic              |
| `net.bridge.bridge-nf-call-ip6tables` | Same for IPv6                                          |
| `net.ipv4.ip_forward`                 | Enable IP forwarding (required for pod-to-pod traffic) |

**D. Base Tools**
```
apt-get install -y \
  apt-transport-https \
  ca-certificates \
  curl \
  wget \
  gnupg \
  conntrack \
  socat
```

| Requirement    | Reason                                          |
| :------------- | :---------------------------------------------- |
| `curl`, `wget` | Download files and artifacts                    |
| `conntrack`    | Required for connection tracking (networking)   |
| `socat`        | Required for `kubectl port-forward` to function |


### 3️⃣ KUBERNETES TOOLS (All Nodes)

**A. Install kubeadm, kubelet, kubectl**
```
# Add Kubernetes repository
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.30/deb/Release.key | gpg --dearmor -o /etc/apt/trusted.gpg.d/k8s.gpg
echo "deb [signed-by=/etc/apt/trusted.gpg.d/k8s.gpg] https://pkgs.k8s.io/core:/stable:/v1.30/deb/ /" > /etc/apt/sources.list.d/kubernetes.list

# Install
apt-get update
apt-get install -y kubelet kubeadm kubectl

# Prevent automatic upgrades
apt-mark hold kubelet kubeadm kubectl
```

| Requirement | Reason                                      |
| :---------- | :------------------------------------------ |
| `kubeadm`   | Bootstrap and manage the Kubernetes cluster |
| `kubelet`   | Node agent responsible for running pods     |
| `kubectl`   | CLI tool used to interact with the cluster  |


**B. Configure Kubelet Node IP**

```
# Why: Tell kubelet which IP to use (important with multiple NICs)
NODE_IP="192.168.56.24"  # Set to node's private IP
echo "KUBELET_EXTRA_ARGS=--node-ip=${NODE_IP}" > /etc/default/kubelet
```

**C. Pre-pull Images**

```
# Why: Speeds up cluster initialization
kubeadm config images pull
```

### 4️⃣ INITIALIZE CLUSTER (Master Only)

**A. Run kubeadm init**

```
kubeadm init \
  --apiserver-advertise-address=192.168.56.24 \
  --pod-network-cidr=172.16.0.0/16 \
  --cri-socket unix:///run/containerd/containerd.sock
```

| Parameter                       | Purpose                                                                            |
| :------------------------------ | :--------------------------------------------------------------------------------- |
| `--apiserver-advertise-address` | The IP address that the API server will advertise to other nodes                   |
| `--pod-network-cidr`            | The IP address range for the pod network (must not conflict with host network!)    |
| `--cri-socket`                  | The path to the container runtime socket (e.g., `/run/containerd/containerd.sock`) |


**B. Setup kubeconfig**
```
# For root user
mkdir -p /root/.kube
cp /etc/kubernetes/admin.conf /root/.kube/config
chown root:root /root/.kube/config

# For regular user
mkdir -p /home/vagrant/.kube
cp /etc/kubernetes/admin.conf /home/vagrant/.kube/config
chown vagrant:vagrant /home/vagrant/.kube/config
```

**C. Install CNI Plugin (Calico)**

```
# Install Tigera Operator
kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.28.0/manifests/tigera-operator.yaml

# Configure Calico
cat <<EOF | kubectl apply -f -
apiVersion: operator.tigera.io/v1
kind: Installation
metadata:
  name: default
spec:
  calicoNetwork:
    ipPools:
    - cidr: 172.16.0.0/16
      encapsulation: VXLANCrossSubnet
      natOutgoing: Enabled
      nodeSelector: all()
EOF
```

**D. Generate Join Command**
```
# Create join command for workers
kubeadm token create --print-join-command > /vagrant/join.sh
chmod +x /vagrant/join.sh
```

### 5️⃣ JOIN WORKERS (Worker Nodes Only)
```
# Run the join command from master
bash /vagrant/join.sh --cri-socket unix:///run/containerd/containerd.sock
```

### 📊 Summary: What's Needed vs What Was Missing

| Component                        | Original File                | Fixed File                |
| :------------------------------- | :--------------------------- | :------------------------ |
| **Disable Swap**                 | ✅ Yes                        | ✅ Yes                     |
| **Kernel Modules**               | ✅ Yes                        | ✅ Yes                     |
| **Sysctl Parameters**            | ✅ Yes                        | ✅ Yes                     |
| **Containerd**                   | ⚠️ Version 2.0 (unstable)     | ✅ Version 1.7.24 (stable) |
| **Runc**                         | ✅ Yes                        | ✅ Yes                     |
| **CNI Plugins**                  | ✅ Yes                        | ✅ Yes                     |
| **SystemdCgroup**                | ✅ Yes                        | ✅ Yes                     |
| **Sandbox Image Config**         | ❌ Missing                    | ✅ Added                   |
| **kubeadm, kubelet, kubectl**    | ✅ Yes                        | ✅ Yes                     |
| **apt-mark hold**                | ❌ Missing                    | ✅ Added                   |
| **Node IP Config**               | ❌ Missing                    | ✅ Added                   |
| **Pre-pull Images**              | ❌ Missing                    | ✅ Added                   |
| **API Server Advertise Address** | ❌ Missing                    | ✅ Added                   |
| **Pod CIDR**                     | ⚠️ 192.168.0.0/16 (conflicts) | ✅ 172.16.0.0/16           |
| **Kubeconfig for vagrant user**  | ❌ Missing                    | ✅ Added                   |
| **Calico Installation**          | ⚠️ Simple manifest            | ✅ Tigera Operator         |
| **Worker Wait Loop**             | ❌ Missing                    | ✅ Added                   |
| **Memory Allocation**            | ⚠️ Too low                    | ✅ Adequate                |
| **socat package**                | ❌ Missing                    | ✅ Added                   |


### 🎯 Quick Reference: Minimum Requirements

┌─────────────────────────────────────────────────────────────────┐
│              KUBERNETES CLUSTER CHECKLIST                       │
│                                                                 │
│  □ Swap disabled                                                │
│  □ Kernel modules loaded (overlay, br_netfilter)                │
│  □ Sysctl parameters set (ip_forward, bridge-nf-call)           │
│  □ Container runtime installed (containerd)                     │
│  □ Runc installed                                               │
│  □ CNI plugins installed                                        │
│  □ Containerd configured (SystemdCgroup, sandbox image)         │
│  □ kubeadm, kubelet, kubectl installed                          │
│  □ Kubelet node IP configured                                   │
│  □ Cluster initialized (kubeadm init)                           │
│  □ CNI plugin installed (Calico/Flannel)                        │
│  □ Workers joined (kubeadm join)                                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

### 📁 Component Diagram
┌─────────────────────────────────────────────────────────────────┐
│                     KUBERNETES NODE                             │
│                                                                 │
│  ┌───────────────────────────────────────────────────────────┐ │
│  │                    KUBERNETES LAYER                         │ │
│  │  ┌─────────┐  ┌─────────┐  ┌─────────┐                    │ │
│  │  │ kubectl │  │ kubeadm │  │ kubelet │                    │ │
│  │  │  (CLI)  │  │ (Setup) │  │ (Agent) │                    │ │
│  │  └─────────┘  └─────────┘  └────┬────┘                    │ │
│  └──────────────────────────────────┼────────────────────────┘ │
│                                     │                           │
│  ┌──────────────────────────────────┼────────────────────────┐ │
│  │              CONTAINER RUNTIME LAYER                       │ │
│  │                                  ▼                         │ │
│  │  ┌─────────────────────────────────────────────────────┐  │ │
│  │  │                   CONTAINERD                        │  │ │
│  │  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  │  │ │
│  │  │  │ CNI Plugins │  │    Runc     │  │    Images   │  │  │ │
│  │  │  └─────────────┘  └─────────────┘  └─────────────┘  │  │ │
│  │  └─────────────────────────────────────────────────────┘  │ │
│  └────────────────────────────────────────────────────────────┘ │
│                                                                 │
│  ┌────────────────────────────────────────────────────────────┐ │
│  │                      LINUX KERNEL                          │ │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌───────────┐   │ │
│  │  │ overlay  │  │br_netfil │  │ cgroups  │  │namespaces │   │ │
│  │  │  (fs)    │  │  ter     │  │          │  │           │   │ │
│  │  └──────────┘  └──────────┘  └──────────┘  └───────────┘   │ │
│  └────────────────────────────────────────────────────────────┘ │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘