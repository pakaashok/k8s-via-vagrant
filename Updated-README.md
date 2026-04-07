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


### Why Flannel Works ###

| Problem | Calico | Flannel |
| :--- | :--- | :--- |
| **Interface detection** | ❌ Auto-detected wrong interface (`eth0`) | ✅ We specify `--iface=eth1` explicitly |
| **Routing method** | ❌ BGP blocked by NAT | ✅ Always uses VXLAN (works through NAT) |
| **Complexity** | ❌ 5+ components to configure | ✅ Single component (`flanneld`) |
| **Resource usage** | ❌ ~400MB+ | ✅ ~50MB per node |


### Bottom Line ###
Calico is great for production, but requires proper network configuration. In VirtualBox with multiple NICs, Calico's auto-detection fails. Flannel is simpler and allows explicit interface configuration, making it ideal for local Vagrant/VirtualBox development environments.