# k8s-via-vagrant

A Vagrant-based Kubernetes cluster setup with 1 Master and 2 Worker nodes using **Flannel CNI** for pod networking.

---

## 📋 Table of Contents

- [k8s-via-vagrant](#k8s-via-vagrant)
  - [📋 Table of Contents](#-table-of-contents)
  - [Overview](#overview)
  - [Prerequisites](#prerequisites)
  - [Quick Start](#quick-start)
- [Clone the repository](#clone-the-repository)
- [Start the cluster (takes ~10-15 minutes)](#start-the-cluster-takes-10-15-minutes)
- [SSH into master node](#ssh-into-master-node)
- [Verify cluster status](#verify-cluster-status)
- [SSH into master](#ssh-into-master)
- [Check all nodes are Ready](#check-all-nodes-are-ready)
- [Expected output:](#expected-output)
- [NAME      STATUS   ROLES           AGE   VERSION   INTERNAL-IP](#name------status---roles-----------age---version---internal-ip)
- [master    Ready    control-plane   10m   v1.30.x   192.168.56.24](#master----ready----control-plane---10m---v130x---1921685624)
- [worker1   Ready              8m    v1.30.x   192.168.56.25](#worker1---ready--------------8m----v130x---1921685625)
- [worker2   Ready              6m    v1.30.x   192.168.56.26](#worker2---ready--------------6m----v130x---1921685626)
- [Check all system pods are running](#check-all-system-pods-are-running)
- [Check Flannel pods specifically](#check-flannel-pods-specifically)
- [Check CoreDNS is running](#check-coredns-is-running)
- [Test DNS resolution](#test-dns-resolution)
- [Test nginx pod deployment](#test-nginx-pod-deployment)
- [Test cross-node pod communication](#test-cross-node-pod-communication)
- [Check Flannel subnet allocation](#check-flannel-subnet-allocation)
- [Check kubelet logs](#check-kubelet-logs)
- [Check containerd status](#check-containerd-status)
- [Check flannel interface](#check-flannel-interface)
- [Check node routes](#check-node-routes)
- [Check Flannel logs](#check-flannel-logs)
- [Check CoreDNS logs](#check-coredns-logs)
- [Describe a problem pod](#describe-a-problem-pod)
  - [Summary of Updates Made](#summary-of-updates-made)

---

## Overview

This project provisions a fully functional Kubernetes cluster on your local machine using Vagrant and VirtualBox. It's designed for learning, development, and testing purposes.

| Component | Version |
|-----------|---------|
| Kubernetes | v1.30.x |
| Containerd | v1.7.24 |
| CNI Plugin | Flannel (latest) |
| OS | Ubuntu 22.04 |

---

## Prerequisites

- **VirtualBox** 6.x or 7.x
- **Vagrant** 2.3+
- **RAM**: Minimum 12GB available on host machine
- **CPU**: Minimum 4 cores recommended

---

## Quick Start

```bash
# Clone the repository
git clone <repository-url>
cd k8s-via-vagrant

# Start the cluster (takes ~10-15 minutes)
vagrant up

# SSH into master node
vagrant ssh master

# Verify cluster status
kubectl get nodes -o wide
kubectl get pods -A


🌐 Network Architecture
📊 Complete Network Diagram
<pre> +---------------------------------------------------------------------------------+ | YOUR LAPTOP / HOST MACHINE | | | | +------------+ | | | Internet | | | +------|-----+ | | | | | +--------------------------------|----------------------------------------+ | | | VIRTUALBOX | | | | | | | | +------------------------------------------------------------------+ | | | | | NAT NETWORK (10.0.2.0/24) | | | | | | (Internet Access for all VMs) | | | | | +---------|----------------------|----------------------|----------+ | | | | | | | | | | | 10.0.2.15 10.0.2.15 10.0.2.15 | | | | (eth0) (eth0) (eth0) | | | | | | | | | | | +---------|---------+ +---------|----------+ +--------|----------+ | | | | | MASTER | | WORKER1 | | WORKER2 | | | | | | 192.168.56.24 | | 192.168.56.25 | | 192.168.56.26 | | | | | | (5GB RAM) | | (3GB RAM) | | (3GB RAM) | | | | | | 2 CPUs | | 2 CPUs | | 2 CPUs | | | | | | | | | | | | | | | | +---------------+ | | +----------------+ | | +---------------+ | | | | | | | Control Plane | | | | Workloads | | | | Workloads | | | | | | | | • API Server | | | | | | | | | | | | | | | | • Scheduler | | | | +-----------+ | | | | +-----------+ | | | | | | | | • Controller | | | | | nginx-pod | | | | | | test-pod | | | | | | | | | • etcd | | | | | 10.244.1.x| | | | | |10.244.2.x | | | | | | | | +---------------+ | | | +-----------+ | | | | +-----------+ | | | | | | | | | +----------------+ | | +---------------+ | | | | | | +---------------+ | | | | | | | | | | | System Pods | | | +----------------+ | | +---------------+ | | | | | | | • CoreDNS x2 | | | | • kubelet | | | | • kubelet | | | | | | | | • kube-proxy | | | | • kube-proxy | | | | • kube-proxy | | | | | | | | • flannel | | | | • flannel | | | | • flannel | | | | | | | +---------------+ | | +----------------+ | | +---------------+ | | | | | | | | | | | | | | | | flannel.1 | | flannel.1 | | flannel.1 | | | | | | (VXLAN iface) | | (VXLAN iface) | | (VXLAN iface) | | | | | +---------|----------+ +---------|----------+ +---------|--------+ | | | | | | | | | | | +---------|=======================|=======================|---------+ | | | | | | FLANNEL VXLAN OVERLAY (10.244.0.0/16) | | | | | | | | (Pod-to-Pod Communication) | | | | | | | +------|-------+ +-------|-------+ +-------|-----+ | | | | | | | | 10.244.0.0/24| |10.244.1.0/24 | |10.244.2.0/24| | | | | | | | | Master | | Worker1 | | Worker2 | | | | | | | | +--------------+ +---------------+ +-------------+ | | | | | | +----------------------------------------------------------+---------+ | | | | | | | | | | | (eth1) (eth1) (eth1) | | | | +---------|=======================|=======================|---------+ | | | | | HOST-ONLY NETWORK (192.168.56.0/24) | | | | | | (Node-to-Node Communication) | | | | | | Flannel uses this for VXLAN tunneling | | | | | +-------------------------------------------------------------------+ | | | +-------------------------------------------------------------------------+ | +----------------------------------------------------------------------------------+ </pre>
🔍 Network Layers Explained
Layer	Network	Interface	Purpose
Layer 1	NAT 10.0.2.0/24	eth0	Internet access (apt, container image pulls)
Layer 2	Host-Only 192.168.56.0/24	eth1	Node-to-node communication
Layer 3	Flannel VXLAN 10.244.0.0/16	flannel.1	Pod-to-pod communication
🔗 IP Address Allocation
<pre> +-----------------------------------------------------------------+ | IP ADDRESS MAP | | | | NODE IPs (192.168.56.0/24): | | |-- 192.168.56.24 ----------> Master | | |-- 192.168.56.25 ----------> Worker1 | | `-- 192.168.56.26 ----------> Worker2 | | | | POD CIDRs (10.244.0.0/16 - Flannel): | | |-- 10.244.0.0/24 ----------> Pods on Master | | |-- 10.244.1.0/24 ----------> Pods on Worker1 | | `-- 10.244.2.0/24 ----------> Pods on Worker2 | | | | SERVICE CIDR (10.96.0.0/12): | | |-- 10.96.0.1 ----------> kubernetes (API Server) | | `-- 10.96.0.10 ----------> kube-dns (CoreDNS) | | | | NAT IPs (10.0.2.0/24): | | `-- 10.0.2.15 ----------> All VMs (shared for internet) | | | +-----------------------------------------------------------------+ </pre>
⚡ Why Flannel Instead of Calico?
The Problem with Calico in VirtualBox Environment
We initially attempted to use Calico (via Tigera Operator) as the CNI plugin, but encountered persistent networking issues. Here's why Calico failed and why Flannel is the better choice for this setup:

🔴 Calico Failure Analysis
<pre> ┌─────────────────────────────────────────────────────────────────────────┐ │ WHY CALICO FAILED IN VIRTUALBOX │ ├─────────────────────────────────────────────────────────────────────────┤ │ │ │ ISSUE 1: WRONG INTERFACE AUTO-DETECTION │ │ ─────────────────────────────────────── │ │ │ │ VirtualBox VMs have multiple interfaces: │ │ • eth0 (NAT) → 10.0.2.15 (SAME IP on all VMs!) │ │ • eth1 (Host-Only) → 192.168.56.x (unique per VM) │ │ │ │ Calico auto-detected eth0 (wrong interface) by default! │ │ │ │ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ │ │ │ MASTER │ │ WORKER1 │ │ WORKER2 │ │ │ │ eth0: │ │ eth0: │ │ eth0: │ │ │ │ 10.0.2.15 ◄─┼─────┼─ 10.0.2.15 ─┼─────┼► 10.0.2.15 │ SAME IP! │ │ │ │ │ │ │ │ CAN'T ROUTE! │ │ └─────────────┘ └─────────────┘ └─────────────┘ │ │ │ ├─────────────────────────────────────────────────────────────────────────┤ │ │ │ ISSUE 2: BGP ROUTING BLOCKED │ │ ──────────────────────────── │ │ │ │ Calico uses BGP (TCP port 179) by default for routing: │ │ • VirtualBox NAT network blocks BGP traffic │ │ • Nodes couldn't establish BGP peering │ │ │ │ BGP Traffic (TCP 179) ──────X────── BLOCKED BY NAT │ │ │ ├─────────────────────────────────────────────────────────────────────────┤ │ │ │ ISSUE 3: VXLANCrossSubnet MISCONFIGURATION │ │ ────────────────────────────────────────── │ │ │ │ Original config used: │ │ encapsulation: VXLANCrossSubnet │ │ │ │ Calico detected all nodes on "same subnet" (10.0.2.x via eth0) │ │ → Tried direct routing instead of VXLAN tunneling │ │ → Packets couldn't reach destination pods │ │ │ ├─────────────────────────────────────────────────────────────────────────┤ │ │ │ ISSUE 4: HIGHER RESOURCE REQUIREMENTS │ │ ───────────────────────────────────── │ │ │ │ Calico components: │ │ • Tigera Operator: ~100MB │ │ • calico-node: ~150MB per node │ │ • Calico API Server: ~100MB │ │ • Typha (optional): ~50MB │ │ Total: ~400MB+ │ │ │ │ Flannel: ~50MB per node │ │ │ └─────────────────────────────────────────────────────────────────────────┘ </pre>
🟢 Why Flannel Works
<pre> ┌─────────────────────────────────────────────────────────────────────────┐ │ WHY FLANNEL WORKS IN VIRTUALBOX │ ├─────────────────────────────────────────────────────────────────────────┤ │ │ │ 1. EXPLICIT INTERFACE CONFIGURATION │ │ ───────────────────────────────── │ │ We explicitly tell Flannel to use eth1: │ │ │ │ --iface=eth1 ◄── Added to kube-flannel.yml │ │ │ │ 2. SIMPLE VXLAN OVERLAY (ALWAYS) │ │ ────────────────────────────── │ │ Flannel ALWAYS uses VXLAN tunneling, no complex auto-detection: │ │ │ │ Pod A ──► VXLAN Encap ──► eth1 ──► eth1 ──► VXLAN Decap ──► Pod B │ │ │ │ 3. SINGLE COMPONENT │ │ ──────────────── │ │ Only flanneld DaemonSet - fewer things that can break │ │ │ │ 4. LIGHTWEIGHT │ │ ─────────── │ │ ~50MB per node - works great on 3GB worker nodes │ │ │ └─────────────────────────────────────────────────────────────────────────┘ </pre>
📊 Calico vs Flannel Comparison
Feature	Calico	Flannel
Complexity	Complex (5+ components)	Simple (1 component)
Network Model	BGP / VXLAN / IPIP	VXLAN overlay
Network Policies	✅ Full support	❌ No (needs addon)
Memory Usage	~150MB+ per node	~50MB per node
VirtualBox Compatible	⚠️ Requires manual config	✅ Works with --iface flag
Setup Difficulty	Moderate to Complex	Easy
Best For	Production, Enterprise	Dev, Learning, Small clusters
🎯 Recommendation
Environment	Recommended CNI
Local development (VirtualBox/Vagrant)	Flannel
Learning Kubernetes	Flannel
Production with Network Policies	Calico (with proper config)
Cloud providers (AWS/GCP/Azure)	Calico or Cloud CNI
🖥️ Node Configuration
Cluster Nodes
Node	Hostname	IP Address	RAM	CPUs	Role
Master	master	192.168.56.24	5GB	2	Control Plane
Worker1	worker1	192.168.56.25	3GB	2	Workloads
Worker2	worker2	192.168.56.26	3GB	2	Workloads
Installed Components
Component	Version	Purpose
containerd	1.7.24	Container runtime
runc	1.2.2	OCI runtime
CNI plugins	1.6.0	Container networking
Kubernetes	1.30.x	Container orchestration
Flannel	latest	Pod networking (CNI)
🔄 Traffic Flow Examples
1. Pod-to-Pod (Same Node)
<pre> +-------------------------------------------------+ | WORKER1 | | | | +----------+ +----------+ | | | Pod A | -------> | Pod B | | | |10.244.1.5| Direct |10.244.1.6| | | +----------+ (veth) +----------+ | | | | Traffic stays on same node (Fast!) | +-------------------------------------------------+ </pre>
2. Pod-to-Pod (Different Nodes via Flannel VXLAN)
<pre> ┌──────────────────────────────────────────────────────────────────────────────┐ │ POD-TO-POD TRAFFIC FLOW │ └──────────────────────────────────────────────────────────────────────────────┘ WORKER1 (192.168.56.25) WORKER2 (192.168.56.26) ┌─────────────────────┐ ┌─────────────────────┐ │ nginx-pod │ │ test-pod │ │ 10.244.1.5 │ │ 10.244.2.8 │ └─────────┬───────────┘ └──────────▲──────────┘ │ │ │ ① Pod sends packet to 10.244.2.8 │ ⑤ Packet delivered ▼ │ to test-pod ┌─────────────────────┐ ┌──────────┴──────────┐ │ flannel.1 (VXLAN) │ │ flannel.1 (VXLAN) │ │ Encapsulates in │ │ Decapsulates │ │ VXLAN header │ │ VXLAN packet │ └─────────┬───────────┘ └──────────▲──────────┘ │ │ │ ② VXLAN packet sent │ ④ VXLAN packet │ via eth1 │ received ▼ │ ┌─────────────────────┐ ┌──────────┴──────────┐ │ eth1 │ │ eth1 │ │ 192.168.56.25 │────────────────────│ 192.168.56.26 │ └─────────────────────┘ ③ Host-Only └─────────────────────┘ Network 192.168.56.0/24 </pre>
3. Pod-to-Internet
<pre> +--------------------------------------------------------------+ | | | +----------+ +----------+ +----------+ +-----+ | | | Pod A |---->| Node |---->| NAT |---->| WWW | | | |10.244.1.5| | eth0 | | 10.0.2.x | | | | | +----------+ |10.0.2.15 | +----------+ +-----+ | | +----------+ | | | | Flannel NAT Outgoing: Pod IP ---> Node IP ---> Internet | | | +--------------------------------------------------------------+ </pre>
4. External-to-Service (NodePort)
<pre> +--------------------------------------------------------------+ | | | External NodePort Service Pod | | Request (30080) ClusterIP | | | | +------+ +----------+ +----------+ +----------+ | | |Client|---->|Worker1 |---->|10.96.x.x |---->|10.244.1.5| | | | | |:30080 | |:80 | |:8080 | | | +------+ |192.168. | +----------+ +----------+ | | |56.25 | | | +----------+ | | | +--------------------------------------------------------------+ </pre>
✅ Verification Commands
After cluster is up, verify everything is working:

bash

Copy code
# SSH into master
vagrant ssh master

# Check all nodes are Ready
kubectl get nodes -o wide

# Expected output:
# NAME      STATUS   ROLES           AGE   VERSION   INTERNAL-IP
# master    Ready    control-plane   10m   v1.30.x   192.168.56.24
# worker1   Ready    <none>          8m    v1.30.x   192.168.56.25
# worker2   Ready    <none>          6m    v1.30.x   192.168.56.26

# Check all system pods are running
kubectl get pods -A

# Check Flannel pods specifically
kubectl get pods -n kube-flannel

# Check CoreDNS is running
kubectl get pods -n kube-system -l k8s-app=kube-dns

# Test DNS resolution
kubectl run dns-test --image=busybox:1.28 --rm -it --restart=Never -- nslookup kubernetes

# Test nginx pod deployment
kubectl run nginx-pod --image=nginx:latest --restart=Never --port=80
kubectl get pod nginx-pod -o wide

# Test cross-node pod communication
kubectl run test-pod --image=nginx --restart=Never
kubectl get pods -o wide  # Note which nodes they're on
kubectl exec nginx-pod -- curl -s <test-pod-IP>:80

# Check Flannel subnet allocation
kubectl get nodes -o jsonpath='{range .items[*]}{.metadata.name}{"\t"}{.spec.podCIDR}{"\n"}{end}'

🔧 Troubleshooting
Common Issues and Solutions
Issue	Symptom	Solution
Nodes not Ready	kubectl get nodes shows NotReady	Check Flannel pods: kubectl get pods -n kube-flannel
Pods stuck in Pending	Pods can't be scheduled	Verify nodes are Ready and have resources
DNS not working	nslookup fails inside pods	Check CoreDNS pods: kubectl get pods -n kube-system -l k8s-app=kube-dns
Cross-node pod communication fails	Pods can't reach pods on other nodes	Verify flannel.1 interface exists on all nodes
join.sh not found	Workers can't join cluster	Wait longer or check master provisioning logs
Useful Debug Commands
bash

Copy code
# Check kubelet logs
sudo journalctl -u kubelet -f

# Check containerd status
sudo systemctl status containerd

# Check flannel interface
ip addr show flannel.1

# Check node routes
ip route

# Check Flannel logs
kubectl logs -n kube-flannel -l app=flannel

# Check CoreDNS logs
kubectl logs -n kube-system -l k8s-app=kube-dns

# Describe a problem pod
kubectl describe pod <pod-name>

📋 Network Summary Tables
🌐 Layered Network Architecture
Layer	Network	Range	Purpose
Physical	Host-Only	192.168.56.0/24	Node-to-node communication
Physical	NAT	10.0.2.0/24	Internet access (Outbound)
Overlay	Pod Network (Flannel)	10.244.0.0/16	Pod-to-pod via VXLAN
Virtual	Service	10.96.0.0/12	Kubernetes ClusterIP range
📊 Key Configuration Settings
Setting	Value	Purpose
--pod-network-cidr	10.244.0.0/16	Flannel default pod CIDR
--apiserver-advertise-address	192.168.56.24	API server binds to correct IP
--node-ip (kubelet)	192.168.56.x	Kubelet advertises correct node IP
--iface=eth1 (Flannel)	eth1	Flannel uses Host-Only network
sandbox_image	pause:3.9	Containerd pause container
📝 Changelog
v2.0.0 (Current) - Flannel Migration
Change	Before	After
CNI Plugin	Calico (Tigera Operator)	Flannel
Pod CIDR	172.16.0.0/16	10.244.0.0/16
Interface Config	Auto-detect (broken)	Explicit --iface=eth1
Complexity	5+ components	1 component
Memory Usage	~400MB+	~50MB per node
Reliability	❌ Network issues	✅ Stable
v1.0.0 (Previous) - Initial Setup Fixes
Issue	Original (❌)	Fixed (✅)
Containerd Version	2.0.0 (unstable)	1.7.24 (stable)
Variable Name	START (undefined)	START_OCTET (consistent)
Node IP Config	Not set	Explicitly set via KUBELET_EXTRA_ARGS
API Server Address	Not set	Set --apiserver-advertise-address
Master Memory	2458 MB	5120 MB (5GB)
Worker Memory	1500 MB	3072 MB (3GB)
Sandbox Image	Not configured	Set to pause:3.9
Package Hold	No	Yes (apt-mark hold)
Vagrant User Kubeconfig	No	Yes
Worker Wait Loop	No	Yes (waits up to 5 min)
Missing Package	No socat	Includes socat
Pre-pull Images	No	Yes (kubeadm config images pull)
Primary Node Flag	No	Yes (master is primary)
/etc/hosts Setup	Unused	Applied to all nodes
📜 License
MIT License - Feel free to use and modify for your learning and development needs.

🤝 Contributing
Contributions are welcome! Please feel free to submit issues or pull requests.

css

Copy code

---

## Summary of Updates Made

| Section | Changes |
|---------|---------|
| **Title & Overview** | Added version table, clarified Flannel usage |
| **Table of Contents** | Added new sections |
| **Network Diagrams** | Updated Pod CIDR to `10.244.0.0/16` |
| **New Section** | Added "Why Flannel Instead of Calico?" with detailed explanation |
| **IP Address Map** | Fixed Pod CIDRs to reflect Flannel |
| **Traffic Flow** | Updated to show Flannel VXLAN |
| **Verification Commands** | Added comprehensive testing commands |
| **Troubleshooting** | New section with common issues |
| **Changelog** | Added v2.0.0 with all migration details |

