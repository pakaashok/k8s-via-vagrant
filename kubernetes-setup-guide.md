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
A. Disable Swap
```
# Why: Kubernetes requires swap to be disabled for proper memory management
swapoff -a
sed -i '/swap/d' /etc/fstab
```

