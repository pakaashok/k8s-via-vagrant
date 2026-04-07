# k8s-via-vagrant

### 🌐 Network Diagram for Kubernetes Cluster

### 📊 Complete Network Architecture

<pre>

+---------------------------------------------------------------------------------+
|                        YOUR LAPTOP / HOST MACHINE                               |
|                                                                                 |
|                              +------------+                                     |
|                              |  Internet  |                                     |
|                              +------|-----+                                     |
|                                     |                                           |
|    +--------------------------------|----------------------------------------+  |
|    |                           VIRTUALBOX                                    |  |
|    |                                                                         |  |
|    |   +------------------------------------------------------------------+  |  |
|    |   |                  NAT NETWORK (10.0.2.0/24)                       |  |  |
|    |   |               (Internet Access for all VMs)                      |  |  |
|    |   +---------|----------------------|----------------------|----------+  |  |
|    |             |                      |                      |             |  |
|    |         10.0.2.15              10.0.2.15              10.0.2.15         |  |
|    |           (eth0)                 (eth0)                 (eth0)          |  |
|    |             |                      |                      |             |  |
|    |   +---------|---------+  +---------|----------+  +--------|----------+  |  |
|    |   |       MASTER      |  |       WORKER1      |  |       WORKER2     |  |  |
|    |   |  192.168.56.24    |  |   192.168.56.25    |  |   192.168.56.26   |  |  |
|    |   |     (5GB RAM)     |  |     (3GB RAM)      |  |     (3GB RAM)     |  |  |
|    |   |      2 CPUs       |  |       2 CPUs       |  |       2 CPUs      |  |  |
|    |   |                   |  |                    |  |                   |  |  |
|    |   | +---------------+ |  | +----------------+ |  | +---------------+ |  |  |
|    |   | | Control Plane | |  | |    Workloads   | |  | |   Workloads   | |  |  |
|    |   | | • API Server  | |  | |                | |  | |               | |  |  |
|    |   | | • Scheduler   | |  | |  +-----------+ | |  | | +-----------+ | |  |  |
|    |   | | • Controller  | |  | |  | nginx-pod | | |  | | | test-pod  | | |  |  |
|    |   | | • etcd        | |  | |  | 10.244.1.x| | |  | | |10.244.2.x | | |  |  |
|    |   | +---------------+ |  | |  +-----------+ | |  | | +-----------+ | |  |  |
|    |   |                   |  | +----------------+ |  | +---------------+ |  |  |
|    |   | +---------------+ |  |                    |  |                   |  |  |
|    |   | | System Pods   | |  | +----------------+ |  | +---------------+ |  |  |
|    |   | | • CoreDNS x2  | |  | | • kubelet      | |  | | • kubelet     | |  |  |
|    |   | | • kube-proxy  | |  | | • kube-proxy   | |  | | • kube-proxy  | |  |  |
|    |   | | • flannel     | |  | | • flannel      | |  | | • flannel     | |  |  |
|    |   | +---------------+ |  | +----------------+ |  | +---------------+ |  |  |
|    |   |                   |  |                    |  |                   |  |  |
|    |   |  flannel.1        |  |  flannel.1         |  |  flannel.1        |  |  |
|    |   |  (VXLAN iface)    |  |  (VXLAN iface)     |  |  (VXLAN iface)    |  |  |
|    |   +---------|----------+  +---------|----------+  +---------|--------+  |  |
|    |             |                       |                       |           |  |
|    |   +---------|=======================|=======================|---------+ |  |
|    |   |         |    FLANNEL VXLAN OVERLAY (10.244.0.0/16)      |         | |  |
|    |   |         |         (Pod-to-Pod Communication)            |         | |  |
|    |   |  +------|-------+   +-------|-------+   +-------|-----+ |         | |  |
|    |   |  | 10.244.0.0/24|   |10.244.1.0/24  |   |10.244.2.0/24| |         | |  |
|    |   |  |    Master    |   |   Worker1     |   |   Worker2   | |         | |  |
|    |   |  +--------------+   +---------------+   +-------------+ |         | |  |
|    |   +----------------------------------------------------------+------+ | |  |
|    |             |                       |                       |           |  |
|    |         (eth1)                   (eth1)                  (eth1)         |  |
|    |   +---------|=======================|=======================|---------+ |  |
|    |   |              HOST-ONLY NETWORK (192.168.56.0/24)                  | |  |
|    |   |                  (Node-to-Node Communication)                     | |  |
|    |   |              Flannel uses this for VXLAN tunneling                | |  |
|    |   +-------------------------------------------------------------------+ |  |
|    +-------------------------------------------------------------------------+  |
+----------------------------------------------------------------------------------+
</pre>

### 🔍 Detailed Node View with Interfaces

<pre>

┌─────────────────────────────────────────────────────────────────────────────┐
│                          NODE IPs (Layer 2)                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│  MASTER:   192.168.56.24                                                    │
│  WORKER1:  192.168.56.25                                                    │
│  WORKER2:  192.168.56.26                                                    │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│                     POD NETWORK CIDRs (Layer 3 - Flannel)                   │
├─────────────────────────────────────────────────────────────────────────────┤
│  MASTER  Pod CIDR:   10.244.0.0/24  (pods get 10.244.0.x)                   │
│  WORKER1 Pod CIDR:   10.244.1.0/24  (pods get 10.244.1.x)                   │
│  WORKER2 Pod CIDR:   10.244.2.0/24  (pods get 10.244.2.x)                   │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│                         SERVICE NETWORK                                     │
├─────────────────────────────────────────────────────────────────────────────┤
│  Cluster IP Range:  10.96.0.0/12 (default)                                  │
│  Kubernetes API:    10.96.0.1                                               │
│  CoreDNS:           10.96.0.10                                              │
└─────────────────────────────────────────────────────────────────────────────┘

</pre>

### 🌐 Pod Network (Calico Overlay)

<pre>

┌──────────────────────────────────────────────────────────────────────────────┐
│                           POD-TO-POD TRAFFIC FLOW                            │
└──────────────────────────────────────────────────────────────────────────────┘

  WORKER1 (192.168.56.25)                    WORKER2 (192.168.56.26)
  ┌─────────────────────┐                    ┌─────────────────────┐
  │     nginx-pod       │                    │      test-pod       │
  │    10.244.1.5       │                    │     10.244.2.8      │
  └─────────┬───────────┘                    └──────────▲──────────┘
            │                                           │
            │ ① Pod sends packet to 10.244.2.8         │ ⑤ Packet delivered
            ▼                                           │    to test-pod
  ┌─────────────────────┐                    ┌──────────┴──────────┐
  │   flannel.1 (VXLAN) │                    │   flannel.1 (VXLAN) │
  │   Encapsulates in   │                    │   Decapsulates      │
  │   VXLAN header      │                    │   VXLAN packet      │
  └─────────┬───────────┘                    └──────────▲──────────┘
            │                                           │
            │ ② VXLAN packet sent                      │ ④ VXLAN packet
            │    via eth1                              │    received
            ▼                                           │
  ┌─────────────────────┐                    ┌──────────┴──────────┐
  │   eth1              │                    │   eth1              │
  │   192.168.56.25     │────────────────────│   192.168.56.26     │
  └─────────────────────┘   ③ Host-Only      └─────────────────────┘
                              Network
                           192.168.56.0/24

</pre>


### 📊 Network Summary Table

| Network | CIDR | Purpose | Used By |
| :--- | :--- | :--- | :--- |
| **NAT** | `10.0.2.0/24` | Internet access | All VMs (`eth0`) |
| **Host-Only** | `192.168.56.0/24` | Node communication | All VMs (`eth1`) |
| **Pod Network** | `172.16.0.0/16` | Pod-to-Pod communication | All Pods |
| **Service Network** | `10.96.0.0/12` | Kubernetes Services | ClusterIP services |

### 🔗 IP Address Allocation

<pre>

+-----------------------------------------------------------------+
|                         IP ADDRESS MAP                          |
|                                                                 |
| NODE IPs (192.168.56.0/24):                                     |
| |-- 192.168.56.24  ----------> Master                           |
| |-- 192.168.56.25  ----------> Worker1                          |
| `-- 192.168.56.26  ----------> Worker2                          |
|                                                                 |
| POD CIDRs (172.16.0.0/16):                                      |
| |-- 172.16.0.0/24  ----------> Pods on Master                   |
| |-- 172.16.1.0/24  ----------> Pods on Worker1                  |
| `-- 172.16.2.0/24  ----------> Pods on Worker2                  |
|                                                                 |
| SERVICE CIDR (10.96.0.0/12):                                    |
| |-- 10.96.0.1      ----------> kubernetes (API Server)          |
| `-- 10.96.0.10     ----------> kube-dns (CoreDNS)               |
|                                                                 |
| NAT IPs (10.0.2.0/24):                                          |
| `-- 10.0.2.15      ----------> All VMs (shared for internet)    |
|                                                                 |
+-----------------------------------------------------------------+

</pre>

### 🔄 Traffic Flow Examples

**1. Pod-to-Pod (Same Node)**

<pre>
+-------------------------------------------------+
|                    WORKER1                      |
|                                                 |
|  +----------+          +----------+             |
|  |  Pod A   | -------> |  Pod B   |             |
|  |172.16.1.5|  Direct  |172.16.1.6|             |
|  +----------+  (veth)  +----------+             |
|                                                 |
|  Traffic stays on same node (Fast!)             |
+-------------------------------------------------+
</pre>

**2. Pod-to-Pod (Different Nodes)**

<pre>

+------------------+                    +------------------+
|     WORKER1      |                    |     WORKER2      |
|                  |                    |                  |
|  +----------+    |                    |    +----------+  |
|  |  Pod A   |    |                    |    |  Pod B   |  |
|  |172.16.1.5|    |                    |    |172.16.2.3|  |
|  +----|-----+    |                    |    +----^-----+  |
|       |          |                    |         |        |
|       v          |                    |         |        |
|  +----------+    |                    |    +----|-----+  |
|  |  Calico  |    |    VXLAN Tunnel    |    |  Calico  |  |
|  |  vxlan   |----+--------------------+--->|  vxlan   |  |
|  +----------+    |                    |    +----------+  |
|       |          |                    |                  |
|  192.168.56.25   |                    |   192.168.56.26  |
+------------------+                    +------------------+

</pre>

**3. Pod-to-Internet**

<pre>
+--------------------------------------------------------------+
|                                                              |
|  +----------+     +----------+     +----------+     +-----+  |
|  |  Pod A   |---->|  Node    |---->|   NAT    |---->| WWW |  |
|  |172.16.1.5|     |  eth0    |     | 10.0.2.x |     |     |  |
|  +----------+     |10.0.2.15 |     +----------+     +-----+  |
|                   +----------+                               |
|                                                              |
|  Calico NAT Outgoing: Pod IP ---> Node IP ---> Internet      |
|                                                              |
+--------------------------------------------------------------+
</pre>

**4. External-to-Service (NodePort)**

<pre>
+--------------------------------------------------------------+
|                                                              |
|   External      NodePort        Service         Pod          |
|   Request       (30080)        ClusterIP                     |
|                                                              |
|  +------+     +----------+     +----------+     +----------+ |
|  |Client|---->|Worker1   |---->|10.96.x.x |---->|172.16.1.5| |
|  |      |     |:30080    |     |:80       |     |:8080     | |
|  +------+     |192.168.  |     +----------+     +----------+ |
|               |56.25     |                                   |
|               +----------+                                   |
|                                                              |
+--------------------------------------------------------------+
</pre>


### ✅ Network Summary

### 🌐 Layered Network Architecture

| Layer | Network | Range | Notes |
| :--- | :--- | :--- | :--- |
| **Physical** | Host-Only | `192.168.56.0/24` | Node-to-node communication |
| **Physical** | NAT | `10.0.2.0/24` | Internet access (Outbound) |
| **Overlay** | Pod Network | `172.16.0.0/16` | Calico VXLAN encapsulation |
| **Virtual** | Service | `10.96.0.0/12` | Kubernetes ClusterIP range |


### 📊 Comparison Table

| Issue | Original (❌) | Fixed (✅) |
| :--- | :--- | :--- |
| **Containerd Version** | `2.0.0` (unstable) | `1.7.24` (stable) |
| **Pod CIDR** | `192.168.0.0/16` (overlaps nodes) | `172.16.0.0/16` (no conflict) |
| **Node IP Config** | Not set (wrong NIC binding) | Explicitly set via `KUBELET_EXTRA_ARGS` |
| **API Server Address** | Not set (may bind to NAT) | Set to `--apiserver-advertise-address` |
| **Master Memory** | `2458 MB` (too low) | `5120 MB` (5GB) |
| **Worker Memory** | `1500 MB` (borderline) | `3072 MB` (3GB) |
| **Sandbox Image** | Not configured | Set to `pause:3.9` |
| **Package Hold** | No | **Yes** (`apt-mark hold`) |
| **Vagrant User Kubeconfig** | No | **Yes** |
| **Worker Wait Loop** | No (may fail) | **Yes** (waits up to 5 min) |
| **Calico Install** | Simple manifest | **Tigera Operator** (production) |
| **Missing Package** | No `socat` | Includes `socat` |
| **Pre-pull Images** | No | **Yes** (`kubeadm config images pull`) |
| **Primary Node Flag** | No | **Yes** (master is primary) |
