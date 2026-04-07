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

### POINT -TO -NOTE ###

<pre>

┌─────────────────────────────────────────────────────────────────────────┐
│                     CALICO FAILED BECAUSE OF:                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  ❌ REASON 1: WRONG INTERFACE DETECTION                                 │
│  ──────────────────────────────────────                                 │
│                                                                         │
│     VirtualBox VMs have 2 interfaces:                                   │
│       • eth0 (NAT)       → 10.0.2.15  (SAME on all VMs!)               │
│       • eth1 (Host-Only) → 192.168.56.x (Unique per VM)                │
│                                                                         │
│     Calico auto-detected eth0 (wrong one)                              │
│     All nodes appeared to have the SAME IP → Routing broken!           │
│                                                                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  ❌ REASON 2: BGP BLOCKED BY NAT                                        │
│  ───────────────────────────────                                        │
│                                                                         │
│     Calico uses BGP (TCP port 179) by default                          │
│     VirtualBox NAT network blocks this traffic                         │
│     Nodes couldn't establish routing between each other                │
│                                                                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  ❌ REASON 3: VXLANCrossSubnet DIDN'T WORK                              │
│  ─────────────────────────────────────────                              │
│                                                                         │
│     We configured: encapsulation: VXLANCrossSubnet                     │
│     Calico saw all nodes on "same subnet" (10.0.2.x via eth0)          │
│     → Skipped VXLAN tunneling → Direct routing failed                  │
│                                                                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  ❌ REASON 4: TOO COMPLEX FOR LOCAL DEV                                 │
│  ──────────────────────────────────────                                 │
│                                                                         │
│     Calico: 5+ components (~400MB RAM)                                 │
│     Flannel: 1 component (~50MB RAM)                                   │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘

</pre>


<pre>

┌─────────────────────────────────────────────────────────────────────────┐
│               KUBERNETES CLUSTER - FULLY OPERATIONAL 🎉                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  NODES:                                                                 │
│  ├── master    ✅ Ready   192.168.56.24   control-plane                │
│  ├── worker1   ✅ Ready   192.168.56.25   worker                       │
│  └── worker2   ✅ Ready   192.168.56.26   worker                       │
│                                                                         │
│  NETWORKING:                                                            │
│  ├── Flannel CNI         ✅ Working (pod-to-pod communication)         │
│  ├── CoreDNS             ✅ Working (service discovery)                │
│  ├── kube-proxy          ✅ Working (service routing)                  │
│  └── NodePort            ✅ Working (external access)                  │
│                                                                         │
│  TESTS PASSED:                                                          │
│  ├── All nodes Ready     ✅                                            │
│  ├── Pods running        ✅                                            │
│  ├── DNS resolution      ✅                                            │
│  └── Cross-node network  ✅                                            │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘

</pre>

### Why Flannel Works ###

| Problem | Calico | Flannel |
| :--- | :--- | :--- |
| **Interface detection** | ❌ Auto-detected wrong interface (`eth0`) | ✅ We specify `--iface=eth1` explicitly |
| **Routing method** | ❌ BGP blocked by NAT | ✅ Always uses VXLAN (works through NAT) |
| **Complexity** | ❌ 5+ components to configure | ✅ Single component (`flanneld`) |
| **Resource usage** | ❌ ~400MB+ | ✅ ~50MB per node |


### Comparison Table ###

| Issue | Original (❌) | Fixed (✅) |
| :--- | :--- | :--- |
| **Containerd Version** | 2.0.0 (unstable) | 1.7.24 (stable) |
| **Pod CIDR** | 192.168.0.0/16 (overlaps nodes) | 172.16.0.0/16 (no conflict) |
| **Node IP Config** | Not set (wrong NIC binding) | Explicitly set via `KUBELET_EXTRA_ARGS` |
| **API Server Address** | Not set (may bind to NAT) | Set to `--apiserver-advertise-address` |
| **Master Memory** | 2458 MB (too low) | 5120 MB (5GB) |
| **Worker Memory** | 1500 MB (borderline) | 3072 MB (3GB) |
| **Sandbox Image** | Not configured | Set to `pause:3.9` |
| **Package Hold** | No | Yes (`apt-mark hold`) |
| **Vagrant User Kubeconfig** | No | Yes |
| **Worker Wait Loop** | No (may fail) | Yes (waits up to 5 min) |
| **Calico Install** | Simple manifest | Tigera Operator (production) |
| **Missing Package** | No `socat` | Includes `socat` |
| **Pre-pull Images** | No | Yes (`kubeadm config images pull`) |
| **Primary Node Flag** | No | Yes (master is primary) |


### Bottom Line ###
Calico is great for production, but requires proper network configuration. In VirtualBox with multiple NICs, Calico's auto-detection fails. Flannel is simpler and allows explicit interface configuration, making it ideal for local Vagrant/VirtualBox development environments.

