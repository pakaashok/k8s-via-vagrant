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