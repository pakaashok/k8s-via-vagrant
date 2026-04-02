Windows@AaaDee MINGW64 ~/k8s (master)
$ vagrant up --no-parallel
Bringing machine 'master' up with 'virtualbox' provider...
Bringing machine 'worker1' up with 'virtualbox' provider...
Bringing machine 'worker2' up with 'virtualbox' provider...
==> master: Importing base box 'generic/ubuntu2204'...
==> master: Matching MAC address for NAT networking...
==> master: Checking if box 'generic/ubuntu2204' version '4.3.2' is up to date...
==> master: Setting the name of the VM: k8s_master_1775146939683_6415
==> master: Clearing any previously set network interfaces...
==> master: Preparing network interfaces based on configuration...
    master: Adapter 1: nat
    master: Adapter 2: hostonly
==> master: Forwarding ports...
    master: 22 (guest) => 2222 (host) (adapter 1)
==> master: Running 'pre-boot' VM customizations...
==> master: Booting VM...
==> master: Waiting for machine to boot. This may take a few minutes...
    master: SSH address: 127.0.0.1:2222
    master: SSH username: vagrant
    master: SSH auth method: private key
    master: Warning: Connection reset. Retrying...
    master: Warning: Connection reset. Retrying...
    master: Warning: Connection reset. Retrying...
    master: Warning: Connection reset. Retrying...
    master: Warning: Connection reset. Retrying...
    master: Warning: Connection reset. Retrying...
    master: Warning: Connection reset. Retrying...
    master: Warning: Connection reset. Retrying...
    master: Warning: Connection reset. Retrying...
    master: Warning: Connection reset. Retrying...
    master: Warning: Connection reset. Retrying...
    master: Warning: Connection reset. Retrying...
    master:
    master: Vagrant insecure key detected. Vagrant will automatically replace
    master: this with a newly generated keypair for better security.
    master:
    master: Inserting generated public key within guest...
    master: Removing insecure key from the guest if it's present...
    master: Key inserted! Disconnecting and reconnecting using new SSH key...
==> master: Machine booted and ready!
==> master: Checking for guest additions in VM...
    master: The guest additions on this VM do not match the installed version of
    master: VirtualBox! In most cases this is fine, but in rare cases it can
    master: prevent things such as shared folders from working properly. If you see
    master: shared folder errors, please make sure the guest additions within the
    master: virtual machine match the version of VirtualBox you have installed on
    master: your host and reload your VM.
    master:
    master: Guest Additions Version: 6.1.38
    master: VirtualBox Version: 7.1
==> master: Setting hostname...
==> master: Configuring and enabling network interfaces...
==> master: Mounting shared folders...
    master: C:/Users/Windows/k8s => /vagrant
==> master: Running provisioner: shell...
    master: Running: inline script
    master: ++ NODE_IP=192.168.56.24
    master: ++ swapoff -a
    master: ++ sed -i /swap/d /etc/fstab
    master: ++ systemctl disable --now systemd-zram-setup@zram0.service
    master: ++ true
    master: ++ apt-get update -y
    master: Hit:1 https://mirrors.edge.kernel.org/ubuntu jammy InRelease
    master: Get:2 https://mirrors.edge.kernel.org/ubuntu jammy-updates InRelease [128 kB]
    master: Get:3 https://mirrors.edge.kernel.org/ubuntu jammy-backports InRelease [127 kB]
    master: Get:4 https://mirrors.edge.kernel.org/ubuntu jammy-security InRelease [129 kB]
    master: Get:5 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 Packages [3,365 kB]
    master: Get:6 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main Translation-en [512 kB]
    master: Get:7 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 c-n-f Metadata [19.6 kB]
    master: Get:8 https://mirrors.edge.kernel.org/ubuntu jammy-updates/restricted amd64 Packages [5,608 kB]
    master: Get:9 https://mirrors.edge.kernel.org/ubuntu jammy-updates/restricted Translation-en [1,075 kB]
    master: Get:10 https://mirrors.edge.kernel.org/ubuntu jammy-updates/restricted amd64 c-n-f Metadata [676 B]
    master: Get:11 https://mirrors.edge.kernel.org/ubuntu jammy-updates/universe amd64 Packages [1,262 kB]
    master: Get:12 https://mirrors.edge.kernel.org/ubuntu jammy-updates/universe Translation-en [316 kB]
    master: Get:13 https://mirrors.edge.kernel.org/ubuntu jammy-updates/universe amd64 c-n-f Metadata [30.5 kB]
    master: Get:14 https://mirrors.edge.kernel.org/ubuntu jammy-updates/multiverse amd64 Packages [59.0 kB]
    master: Get:15 https://mirrors.edge.kernel.org/ubuntu jammy-updates/multiverse Translation-en [13.5 kB]
    master: Get:16 https://mirrors.edge.kernel.org/ubuntu jammy-updates/multiverse amd64 c-n-f Metadata [612 B]
    master: Get:17 https://mirrors.edge.kernel.org/ubuntu jammy-backports/main amd64 Packages [69.4 kB]
    master: Get:18 https://mirrors.edge.kernel.org/ubuntu jammy-backports/main Translation-en [11.5 kB]
    master: Get:19 https://mirrors.edge.kernel.org/ubuntu jammy-backports/main amd64 c-n-f Metadata [412 B]
    master: Get:20 https://mirrors.edge.kernel.org/ubuntu jammy-backports/universe amd64 Packages [30.4 kB]
    master: Get:21 https://mirrors.edge.kernel.org/ubuntu jammy-backports/universe Translation-en [16.9 kB]
    master: Get:22 https://mirrors.edge.kernel.org/ubuntu jammy-backports/universe amd64 c-n-f Metadata [672 B]
    master: Get:23 https://mirrors.edge.kernel.org/ubuntu jammy-security/main amd64 Packages [3,068 kB]
    master: Get:24 https://mirrors.edge.kernel.org/ubuntu jammy-security/main Translation-en [438 kB]
    master: Get:25 https://mirrors.edge.kernel.org/ubuntu jammy-security/main amd64 c-n-f Metadata [14.1 kB]
    master: Get:26 https://mirrors.edge.kernel.org/ubuntu jammy-security/restricted amd64 Packages [5,356 kB]
    master: Get:27 https://mirrors.edge.kernel.org/ubuntu jammy-security/restricted Translation-en [1,025 kB]
    master: Get:28 https://mirrors.edge.kernel.org/ubuntu jammy-security/restricted amd64 c-n-f Metadata [680 B]
    master: Get:29 https://mirrors.edge.kernel.org/ubuntu jammy-security/universe amd64 Packages [1,025 kB]
    master: Get:30 https://mirrors.edge.kernel.org/ubuntu jammy-security/universe Translation-en [226 kB]
    master: Get:31 https://mirrors.edge.kernel.org/ubuntu jammy-security/universe amd64 c-n-f Metadata [22.8 kB]
    master: Get:32 https://mirrors.edge.kernel.org/ubuntu jammy-security/multiverse amd64 Packages [51.9 kB]
    master: Get:33 https://mirrors.edge.kernel.org/ubuntu jammy-security/multiverse Translation-en [10.6 kB]
    master: Get:34 https://mirrors.edge.kernel.org/ubuntu jammy-security/multiverse amd64 c-n-f Metadata [388 B]
    master: Fetched 24.0 MB in 5min 55s (67.7 kB/s)
    master: Reading package lists...
    master: ++ apt-get install -y apt-transport-https ca-certificates curl wget gnupg lsb-release net-tools iproute2 bash-completion conntrack socat
    master: Reading package lists...
    master: Building dependency tree...
    master: Reading state information...
    master: bash-completion is already the newest version (1:2.11-5ubuntu1).
    master: bash-completion set to manually installed.
    master: iproute2 is already the newest version (5.15.0-1ubuntu2).
    master: iproute2 set to manually installed.
    master: lsb-release is already the newest version (11.1.0ubuntu4).
    master: The following additional packages will be installed:
    master:   dirmngr gnupg-l10n gnupg-utils gpg gpg-agent gpg-wks-client gpg-wks-server
    master:   gpgconf gpgsm gpgv libcurl4
    master: Suggested packages:
    master:   pinentry-gnome3 tor parcimonie xloadimage scdaemon
    master: The following NEW packages will be installed:
    master:   apt-transport-https conntrack net-tools socat
    master: The following packages will be upgraded:
    master:   ca-certificates curl dirmngr gnupg gnupg-l10n gnupg-utils gpg gpg-agent
    master:   gpg-wks-client gpg-wks-server gpgconf gpgsm gpgv libcurl4 wget
    master: 15 upgraded, 4 newly installed, 0 to remove and 252 not upgraded.
    master: Need to get 3,821 kB of archives.
    master: After this operation, 2,429 kB of additional disk space will be used.
    master: Get:1 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpg-wks-client amd64 2.2.27-3ubuntu2.5 [62.7 kB]
    master: Get:2 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 dirmngr amd64 2.2.27-3ubuntu2.5 [293 kB]
    master: Get:3 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpg-wks-server amd64 2.2.27-3ubuntu2.5 [57.6 kB]
    master: Get:4 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gnupg-utils amd64 2.2.27-3ubuntu2.5 [309 kB]
    master: Get:5 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpg-agent amd64 2.2.27-3ubuntu2.5 [209 kB]
    master: Get:6 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpg amd64 2.2.27-3ubuntu2.5 [519 kB]
    master: Get:7 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpgconf amd64 2.2.27-3ubuntu2.5 [94.3 kB]
    master: Get:8 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gnupg-l10n all 2.2.27-3ubuntu2.5 [54.5 kB]
    master: Get:9 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gnupg all 2.2.27-3ubuntu2.5 [315 kB]
    master: Get:10 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpgsm amd64 2.2.27-3ubuntu2.5 [197 kB]
    master: Get:11 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpgv amd64 2.2.27-3ubuntu2.5 [137 kB]
    master: Get:12 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 ca-certificates all 20240203~22.04.1 [162 kB]
    master: Get:13 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 wget amd64 1.21.2-2ubuntu1.1 [339 kB]
    master: Get:14 https://mirrors.edge.kernel.org/ubuntu jammy-updates/universe amd64 apt-transport-https all 2.4.14 [1,510 B]
    master: Get:15 https://mirrors.edge.kernel.org/ubuntu jammy/main amd64 conntrack amd64 1:1.4.6-2build2 [33.5 kB]
    master: Get:16 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 curl amd64 7.81.0-1ubuntu1.23 [194 kB]
    master: Get:17 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 libcurl4 amd64 7.81.0-1ubuntu1.23 [290 kB]
    master: Get:18 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 net-tools amd64 1.60+git20181103.0eebece-1ubuntu5.4 [204 kB]
    master: Get:19 https://mirrors.edge.kernel.org/ubuntu jammy/main amd64 socat amd64 1.7.4.1-3ubuntu4 [349 kB]
    master: dpkg-preconfigure: unable to re-open stdin: No such file or directory
    master: Fetched 3,821 kB in 1min 20s (47.6 kB/s)
(Reading database ... 76032 files and directories currently installed.)
    master: Preparing to unpack .../00-gpg-wks-client_2.2.27-3ubuntu2.5_amd64.deb ...
    master: Unpacking gpg-wks-client (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    master: Preparing to unpack .../01-dirmngr_2.2.27-3ubuntu2.5_amd64.deb ...
    master: Unpacking dirmngr (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    master: Preparing to unpack .../02-gpg-wks-server_2.2.27-3ubuntu2.5_amd64.deb ...
    master: Unpacking gpg-wks-server (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    master: Preparing to unpack .../03-gnupg-utils_2.2.27-3ubuntu2.5_amd64.deb ...
    master: Unpacking gnupg-utils (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    master: Preparing to unpack .../04-gpg-agent_2.2.27-3ubuntu2.5_amd64.deb ...
    master: Unpacking gpg-agent (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    master: Preparing to unpack .../05-gpg_2.2.27-3ubuntu2.5_amd64.deb ...
    master: Unpacking gpg (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    master: Preparing to unpack .../06-gpgconf_2.2.27-3ubuntu2.5_amd64.deb ...
    master: Unpacking gpgconf (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    master: Preparing to unpack .../07-gnupg-l10n_2.2.27-3ubuntu2.5_all.deb ...
    master: Unpacking gnupg-l10n (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    master: Preparing to unpack .../08-gnupg_2.2.27-3ubuntu2.5_all.deb ...
    master: Unpacking gnupg (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    master: Preparing to unpack .../09-gpgsm_2.2.27-3ubuntu2.5_amd64.deb ...
    master: Unpacking gpgsm (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    master: Preparing to unpack .../10-gpgv_2.2.27-3ubuntu2.5_amd64.deb ...
    master: Unpacking gpgv (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    master: Setting up gpgv (2.2.27-3ubuntu2.5) ...
(Reading database ... 76032 files and directories currently installed.)
    master: Preparing to unpack .../0-ca-certificates_20240203~22.04.1_all.deb ...
    master: Unpacking ca-certificates (20240203~22.04.1) over (20230311ubuntu0.22.04.1) ...
    master: Preparing to unpack .../1-wget_1.21.2-2ubuntu1.1_amd64.deb ...
    master: Unpacking wget (1.21.2-2ubuntu1.1) over (1.21.2-2ubuntu1) ...
    master: Selecting previously unselected package apt-transport-https.
    master: Preparing to unpack .../2-apt-transport-https_2.4.14_all.deb ...
    master: Unpacking apt-transport-https (2.4.14) ...
    master: Selecting previously unselected package conntrack.
    master: Preparing to unpack .../3-conntrack_1%3a1.4.6-2build2_amd64.deb ...
    master: Unpacking conntrack (1:1.4.6-2build2) ...
    master: Preparing to unpack .../4-curl_7.81.0-1ubuntu1.23_amd64.deb ...
    master: Unpacking curl (7.81.0-1ubuntu1.23) over (7.81.0-1ubuntu1.13) ...
    master: Preparing to unpack .../5-libcurl4_7.81.0-1ubuntu1.23_amd64.deb ...
    master: Unpacking libcurl4:amd64 (7.81.0-1ubuntu1.23) over (7.81.0-1ubuntu1.13) ...
    master: Selecting previously unselected package net-tools.
    master: Preparing to unpack .../6-net-tools_1.60+git20181103.0eebece-1ubuntu5.4_amd64.deb ...
    master: Unpacking net-tools (1.60+git20181103.0eebece-1ubuntu5.4) ...
    master: Selecting previously unselected package socat.
    master: Preparing to unpack .../7-socat_1.7.4.1-3ubuntu4_amd64.deb ...
    master: Unpacking socat (1.7.4.1-3ubuntu4) ...
    master: Setting up net-tools (1.60+git20181103.0eebece-1ubuntu5.4) ...
    master: Setting up wget (1.21.2-2ubuntu1.1) ...
    master: Setting up apt-transport-https (2.4.14) ...
    master: Setting up conntrack (1:1.4.6-2build2) ...
    master: Setting up ca-certificates (20240203~22.04.1) ...
    master: Updating certificates in /etc/ssl/certs...
    master: rehash: warning: skipping ca-certificates.crt,it does not contain exactly one certificate or CRL
    master: 14 added, 5 removed; done.
    master: Setting up gnupg-l10n (2.2.27-3ubuntu2.5) ...
    master: Setting up socat (1.7.4.1-3ubuntu4) ...
    master: Setting up gpgconf (2.2.27-3ubuntu2.5) ...
    master: Setting up libcurl4:amd64 (7.81.0-1ubuntu1.23) ...
    master: Setting up curl (7.81.0-1ubuntu1.23) ...
    master: Setting up gpg (2.2.27-3ubuntu2.5) ...
    master: Setting up gnupg-utils (2.2.27-3ubuntu2.5) ...
    master: Setting up gpg-agent (2.2.27-3ubuntu2.5) ...
    master: Setting up gpgsm (2.2.27-3ubuntu2.5) ...
    master: Setting up dirmngr (2.2.27-3ubuntu2.5) ...
    master: Setting up gpg-wks-server (2.2.27-3ubuntu2.5) ...
    master: Setting up gpg-wks-client (2.2.27-3ubuntu2.5) ...
    master: Setting up gnupg (2.2.27-3ubuntu2.5) ...
    master: Processing triggers for libc-bin (2.35-0ubuntu3.3) ...
    master: Processing triggers for man-db (2.10.2-1) ...
    master: Processing triggers for install-info (6.8-4build1) ...
    master: Processing triggers for ca-certificates (20240203~22.04.1) ...
    master: Updating certificates in /etc/ssl/certs...
    master: 0 added, 0 removed; done.
    master: Running hooks in /etc/ca-certificates/update.d...
    master: done.
    master:
    master: Running kernel seems to be up-to-date.
    master:
    master: No services need to be restarted.
    master:
    master: No containers need to be restarted.
    master:
    master: No user sessions are running outdated binaries.
    master:
    master: No VM guests are running outdated hypervisor (qemu) binaries on this host.
    master: ++ VERSION=1.7.24
    master: ++ wget -q https://github.com/containerd/containerd/releases/download/v1.7.24/containerd-1.7.24-linux-amd64.tar.gz
    master: ++ tar Cxzvf /usr/local containerd-1.7.24-linux-amd64.tar.gz
    master: bin/
    master: bin/ctr
    master: bin/containerd
    master: bin/containerd-shim
    master: bin/containerd-shim-runc-v1
    master: bin/containerd-stress
    master: bin/containerd-shim-runc-v2
    master: ++ mkdir -p /usr/local/lib/systemd/system
    master: ++ wget -q -P /usr/local/lib/systemd/system https://raw.githubusercontent.com/containerd/containerd/main/containerd.service
    master: ++ systemctl daemon-reload
    master: ++ systemctl enable --now containerd
    master: Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /usr/local/lib/systemd/system/containerd.service.
    master: ++ RUNC=v1.2.2
    master: ++ wget -q https://github.com/opencontainers/runc/releases/download/v1.2.2/runc.amd64
    master: ++ install -m 755 runc.amd64 /usr/local/sbin/runc
    master: ++ CNI=v1.6.0
    master: ++ mkdir -p /opt/cni/bin
    master: ++ wget -q https://github.com/containernetworking/plugins/releases/download/v1.6.0/cni-plugins-linux-amd64-v1.6.0.tgz
    master: ++ tar Cxzvf /opt/cni/bin cni-plugins-linux-amd64-v1.6.0.tgz
    master: ./
    master: ./vrf
    master: ./firewall
    master: ./LICENSE
    master: ./macvlan
    master: ./static
    master: ./host-device
    master: ./host-local
    master: ./loopback
    master: ./sbr
    master: ./tuning
    master: ./bridge
    master: ./README.md
    master: ./ptp
    master: ./bandwidth
    master: ./vlan
    master: ./portmap
    master: ./ipvlan
    master: ./dummy
    master: ./tap
    master: ./dhcp
    master: ++ mkdir -p /etc/containerd
    master: ++ containerd config default
    master: ++ sed -i 's/SystemdCgroup = false/SystemdCgroup = true/' /etc/containerd/config.toml
    master: ++ sed -i 's|sandbox_image = "registry.k8s.io/pause:3.8"|sandbox_image = "registry.k8s.io/pause:3.9"|' /etc/containerd/config.toml
    master: ++ systemctl restart containerd
    master: ++ tee /etc/modules-load.d/k8s.conf
    master: ++ cat
    master: overlay
    master: br_netfilter
    master: ++ modprobe overlay
    master: ++ modprobe br_netfilter
    master: ++ cat
    master: ++ tee /etc/sysctl.d/k8s.conf
    master: net.bridge.bridge-nf-call-iptables=1
    master: net.bridge.bridge-nf-call-ip6tables=1
    master: net.ipv4.ip_forward=1
    master: ++ sysctl --system
    master: * Applying /etc/sysctl.d/10-console-messages.conf ...
    master: kernel.printk = 4 4 1 7
    master: * Applying /etc/sysctl.d/10-ipv6-privacy.conf ...
    master: net.ipv6.conf.all.use_tempaddr = 2
    master: net.ipv6.conf.default.use_tempaddr = 2
    master: * Applying /etc/sysctl.d/10-kernel-hardening.conf ...
    master: kernel.kptr_restrict = 1
    master: * Applying /etc/sysctl.d/10-magic-sysrq.conf ...
    master: kernel.sysrq = 176
    master: * Applying /etc/sysctl.d/10-network-security.conf ...
    master: net.ipv4.conf.default.rp_filter = 2
    master: net.ipv4.conf.all.rp_filter = 2
    master: * Applying /etc/sysctl.d/10-ptrace.conf ...
    master: kernel.yama.ptrace_scope = 1
    master: * Applying /etc/sysctl.d/10-zeropage.conf ...
    master: vm.mmap_min_addr = 65536
    master: * Applying /usr/lib/sysctl.d/50-default.conf ...
    master: kernel.core_uses_pid = 1
    master: net.ipv4.conf.default.rp_filter = 2
    master: net.ipv4.conf.default.accept_source_route = 0
    master: sysctl: setting key "net.ipv4.conf.all.accept_source_route": Invalid argument
    master: net.ipv4.conf.default.promote_secondaries = 1
    master: sysctl: setting key "net.ipv4.conf.all.promote_secondaries": Invalid argument
    master: net.ipv4.ping_group_range = 0 2147483647
    master: net.core.default_qdisc = fq_codel
    master: fs.protected_hardlinks = 1
    master: fs.protected_symlinks = 1
    master: fs.protected_regular = 1
    master: fs.protected_fifos = 1
    master: * Applying /usr/lib/sysctl.d/50-pid-max.conf ...
    master: kernel.pid_max = 4194304
    master: * Applying /usr/lib/sysctl.d/99-protect-links.conf ...
    master: fs.protected_fifos = 1
    master: fs.protected_hardlinks = 1
    master: fs.protected_regular = 2
    master: fs.protected_symlinks = 1
    master: * Applying /etc/sysctl.d/99-sysctl.conf ...
    master: net.ipv6.conf.all.disable_ipv6 = 1
    master: * Applying /etc/sysctl.d/k8s.conf ...
    master: net.bridge.bridge-nf-call-iptables = 1
    master: net.bridge.bridge-nf-call-ip6tables = 1
    master: net.ipv4.ip_forward = 1
    master: * Applying /etc/sysctl.conf ...
    master: net.ipv6.conf.all.disable_ipv6 = 1
    master: ++ curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.30/deb/Release.key
    master: ++ gpg --dearmor -o /etc/apt/trusted.gpg.d/k8s.gpg
    master: ++ echo 'deb [signed-by=/etc/apt/trusted.gpg.d/k8s.gpg] https://pkgs.k8s.io/core:/stable:/v1.30/deb/ /'
    master: ++ apt-get update
    master: Hit:2 https://mirrors.edge.kernel.org/ubuntu jammy InRelease
    master: Hit:3 https://mirrors.edge.kernel.org/ubuntu jammy-updates InRelease
    master: Hit:4 https://mirrors.edge.kernel.org/ubuntu jammy-backports InRelease
    master: Hit:5 https://mirrors.edge.kernel.org/ubuntu jammy-security InRelease
    master: Get:1 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  InRelease [1,192 B]
    master: Get:6 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  Packages [20.3 kB]
    master: Fetched 21.5 kB in 12s (1,840 B/s)
    master: Reading package lists...
    master: ++ apt-get install -y kubelet kubeadm kubectl
    master: Reading package lists...
    master: Building dependency tree...
    master: Reading state information...
    master: The following additional packages will be installed:
    master:   cri-tools kubernetes-cni
    master: The following NEW packages will be installed:
    master:   cri-tools kubeadm kubectl kubelet kubernetes-cni
    master: 0 upgraded, 5 newly installed, 0 to remove and 252 not upgraded.
    master: Need to get 93.7 MB of archives.
    master: After this operation, 343 MB of additional disk space will be used.
    master: Get:1 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  cri-tools 1.30.1-1.1 [21.3 MB]
    master: Get:2 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  kubeadm 1.30.14-1.1 [10.5 MB]
    master: Get:3 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  kubectl 1.30.14-1.1 [10.9 MB]
    master: Get:4 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  kubernetes-cni 1.4.0-1.1 [32.9 MB]
    master: Get:5 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  kubelet 1.30.14-1.1 [18.2 MB]
    master: dpkg-preconfigure: unable to re-open stdin: No such file or directory
    master: Fetched 93.7 MB in 10min 20s (151 kB/s)
    master: Selecting previously unselected package cri-tools.
(Reading database ... 76139 files and directories currently installed.)
    master: Preparing to unpack .../cri-tools_1.30.1-1.1_amd64.deb ...
    master: Unpacking cri-tools (1.30.1-1.1) ...
    master: Selecting previously unselected package kubeadm.
    master: Preparing to unpack .../kubeadm_1.30.14-1.1_amd64.deb ...
    master: Unpacking kubeadm (1.30.14-1.1) ...
    master: Selecting previously unselected package kubectl.
    master: Preparing to unpack .../kubectl_1.30.14-1.1_amd64.deb ...
    master: Unpacking kubectl (1.30.14-1.1) ...
    master: Selecting previously unselected package kubernetes-cni.
    master: Preparing to unpack .../kubernetes-cni_1.4.0-1.1_amd64.deb ...
    master: Unpacking kubernetes-cni (1.4.0-1.1) ...
    master: Selecting previously unselected package kubelet.
    master: Preparing to unpack .../kubelet_1.30.14-1.1_amd64.deb ...
    master: Unpacking kubelet (1.30.14-1.1) ...
    master: Setting up kubectl (1.30.14-1.1) ...
    master: Setting up cri-tools (1.30.1-1.1) ...
    master: Setting up kubernetes-cni (1.4.0-1.1) ...
    master: Setting up kubeadm (1.30.14-1.1) ...
    master: Setting up kubelet (1.30.14-1.1) ...
    master:
    master: Running kernel seems to be up-to-date.
    master:
    master: No services need to be restarted.
    master:
    master: No containers need to be restarted.
    master:
    master: No user sessions are running outdated binaries.
    master:
    master: No VM guests are running outdated hypervisor (qemu) binaries on this host.
    master: ++ apt-mark hold kubelet kubeadm kubectl
    master: kubelet set on hold.
    master: kubeadm set on hold.
    master: kubectl set on hold.
    master: ++ mkdir -p /etc/default
    master: ++ echo KUBELET_EXTRA_ARGS=--node-ip=192.168.56.24
    master: ++ systemctl enable kubelet
    master: ++ kubeadm config images pull
    master: I0402 17:01:03.592039    8431 version.go:256] remote version is much newer: v1.35.3; falling back to: stable-1.30
    master: [config/images] Pulled registry.k8s.io/kube-apiserver:v1.30.14
    master: [config/images] Pulled registry.k8s.io/kube-controller-manager:v1.30.14
    master: [config/images] Pulled registry.k8s.io/kube-scheduler:v1.30.14
    master: [config/images] Pulled registry.k8s.io/kube-proxy:v1.30.14
    master: [config/images] Pulled registry.k8s.io/coredns/coredns:v1.11.3
    master: [config/images] Pulled registry.k8s.io/pause:3.9
    master: [config/images] Pulled registry.k8s.io/etcd:3.5.15-0
==> master: Running provisioner: shell...
    master: Running: inline script
    master: ++ NODE_IP=192.168.56.24
    master: ++ '[' '!' -f /etc/kubernetes/admin.conf ']'
    master: ++ kubeadm init --apiserver-advertise-address=192.168.56.24 --pod-network-cidr=172.16.0.0/16 --cri-socket unix:///run/containerd/containerd.sock
    master: I0402 17:22:21.704339    8530 version.go:256] remote version is much newer: v1.35.3; falling back to: stable-1.30
    master: [init] Using Kubernetes version: v1.30.14
    master: [preflight] Running pre-flight checks
    master: [preflight] Pulling images required for setting up a Kubernetes cluster
    master: [preflight] This might take a minute or two, depending on the speed of your internet connection
    master: [preflight] You can also perform this action in beforehand using 'kubeadm config images pull'
    master: [certs] Using certificateDir folder "/etc/kubernetes/pki"
    master: [certs] Generating "ca" certificate and key
    master: [certs] Generating "apiserver" certificate and key
    master: [certs] apiserver serving cert is signed for DNS names [kubernetes kubernetes.default kubernetes.default.svc kubernetes.default.svc.cluster.local master] and IPs [10.96.0.1 192.168.56.24]
    master: [certs] Generating "apiserver-kubelet-client" certificate and key
    master: [certs] Generating "front-proxy-ca" certificate and key
    master: [certs] Generating "front-proxy-client" certificate and key
    master: [certs] Generating "etcd/ca" certificate and key
    master: [certs] Generating "etcd/server" certificate and key
    master: [certs] etcd/server serving cert is signed for DNS names [localhost master] and IPs [192.168.56.24 127.0.0.1 ::1]
    master: [certs] Generating "etcd/peer" certificate and key
    master: [certs] etcd/peer serving cert is signed for DNS names [localhost master] and IPs [192.168.56.24 127.0.0.1 ::1]
    master: [certs] Generating "etcd/healthcheck-client" certificate and key
    master: [certs] Generating "apiserver-etcd-client" certificate and key
    master: [certs] Generating "sa" key and public key
    master: [kubeconfig] Using kubeconfig folder "/etc/kubernetes"
    master: [kubeconfig] Writing "admin.conf" kubeconfig file
    master: [kubeconfig] Writing "super-admin.conf" kubeconfig file
    master: [kubeconfig] Writing "kubelet.conf" kubeconfig file
    master: [kubeconfig] Writing "controller-manager.conf" kubeconfig file
    master: [kubeconfig] Writing "scheduler.conf" kubeconfig file
    master: [etcd] Creating static Pod manifest for local etcd in "/etc/kubernetes/manifests"
    master: [control-plane] Using manifest folder "/etc/kubernetes/manifests"
    master: [control-plane] Creating static Pod manifest for "kube-apiserver"
    master: [control-plane] Creating static Pod manifest for "kube-controller-manager"
    master: [control-plane] Creating static Pod manifest for "kube-scheduler"
    master: [kubelet-start] Writing kubelet environment file with flags to file "/var/lib/kubelet/kubeadm-flags.env"
    master: [kubelet-start] Writing kubelet configuration to file "/var/lib/kubelet/config.yaml"
    master: [kubelet-start] Starting the kubelet
    master: [wait-control-plane] Waiting for the kubelet to boot up the control plane as static Pods from directory "/etc/kubernetes/manifests"
    master: [kubelet-check] Waiting for a healthy kubelet at http://127.0.0.1:10248/healthz. This can take up to 4m0s
    master: [kubelet-check] The kubelet is healthy after 1.013267453s
    master: [api-check] Waiting for a healthy API server. This can take up to 4m0s
    master: [api-check] The API server is healthy after 24.007764653s
    master: [upload-config] Storing the configuration used in ConfigMap "kubeadm-config" in the "kube-system" Namespace
    master: [kubelet] Creating a ConfigMap "kubelet-config" in namespace kube-system with the configuration for the kubelets in the cluster
    master: [upload-certs] Skipping phase. Please see --upload-certs
    master: [mark-control-plane] Marking the node master as control-plane by adding the labels: [node-role.kubernetes.io/control-plane node.kubernetes.io/exclude-from-external-load-balancers]
    master: [mark-control-plane] Marking the node master as control-plane by adding the taints [node-role.kubernetes.io/control-plane:NoSchedule]
    master: [bootstrap-token] Using token: eagu1g.x3ewk839ip6zb42y
    master: [bootstrap-token] Configuring bootstrap tokens, cluster-info ConfigMap, RBAC Roles
    master: [bootstrap-token] Configured RBAC rules to allow Node Bootstrap tokens to get nodes
    master: [bootstrap-token] Configured RBAC rules to allow Node Bootstrap tokens to post CSRs in order for nodes to get long term certificate credentials
    master: [bootstrap-token] Configured RBAC rules to allow the csrapprover controller automatically approve CSRs from a Node Bootstrap Token
    master: [bootstrap-token] Configured RBAC rules to allow certificate rotation for all node client certificates in the cluster
    master: [bootstrap-token] Creating the "cluster-info" ConfigMap in the "kube-public" namespace
    master: [kubelet-finalize] Updating "/etc/kubernetes/kubelet.conf" to point to a rotatable kubelet client certificate and key
    master: [addons] Applied essential addon: CoreDNS
    master: [addons] Applied essential addon: kube-proxy
    master:
    master: Your Kubernetes control-plane has initialized successfully!
    master:
    master: To start using your cluster, you need to run the following as a regular user:
    master:
    master:   mkdir -p $HOME/.kube
    master:   sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
    master:   sudo chown $(id -u):$(id -g) $HOME/.kube/config
    master:
    master: Alternatively, if you are the root user, you can run:
    master:
    master:   export KUBECONFIG=/etc/kubernetes/admin.conf
    master:
    master: You should now deploy a pod network to the cluster.
    master: Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
    master:   https://kubernetes.io/docs/concepts/cluster-administration/addons/
    master:
    master: Then you can join any number of worker nodes by running the following on each as root:
    master:
    master: kubeadm join 192.168.56.24:6443 --token eagu1g.x3ewk839ip6zb42y \
    master:     --discovery-token-ca-cert-hash sha256:224cb78242ba07967f90cf2b3d0c8c9300b7967c372ef61119185c4960603a2b
    master: ++ mkdir -p /root/.kube
    master: ++ cp /etc/kubernetes/admin.conf /root/.kube/config
    master: ++ chown root:root /root/.kube/config
    master: ++ mkdir -p /home/vagrant/.kube
    master: ++ cp /etc/kubernetes/admin.conf /home/vagrant/.kube/config
    master: ++ chown vagrant:vagrant /home/vagrant/.kube/config
    master: ++ kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.28.0/manifests/tigera-operator.yaml
    master: namespace/tigera-operator created
    master: customresourcedefinition.apiextensions.k8s.io/bgpconfigurations.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/bgpfilters.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/bgppeers.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/blockaffinities.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/caliconodestatuses.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/clusterinformations.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/felixconfigurations.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/globalnetworkpolicies.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/globalnetworksets.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/hostendpoints.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/ipamblocks.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/ipamconfigs.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/ipamhandles.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/ippools.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/ipreservations.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/kubecontrollersconfigurations.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/networkpolicies.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/networksets.crd.projectcalico.org created
    master: customresourcedefinition.apiextensions.k8s.io/apiservers.operator.tigera.io created
    master: customresourcedefinition.apiextensions.k8s.io/imagesets.operator.tigera.io created
    master: customresourcedefinition.apiextensions.k8s.io/installations.operator.tigera.io created
    master: customresourcedefinition.apiextensions.k8s.io/tigerastatuses.operator.tigera.io created
    master: serviceaccount/tigera-operator created
    master: clusterrole.rbac.authorization.k8s.io/tigera-operator created
    master: clusterrolebinding.rbac.authorization.k8s.io/tigera-operator created
    master: deployment.apps/tigera-operator created
    master: ++ sleep 10
    master: ++ cat
    master: ++ kubectl apply -f -
    master: installation.operator.tigera.io/default created
    master: apiserver.operator.tigera.io/default created
    master: Waiting for Calico to be ready...
    master: ++ echo 'Waiting for Calico to be ready...'
    master: ++ sleep 30
    master: ++ kubeadm token create --print-join-command
    master: ++ chmod +x /vagrant/join.sh
==> worker1: Importing base box 'generic/ubuntu2204'...
==> worker1: Matching MAC address for NAT networking...
==> worker1: Checking if box 'generic/ubuntu2204' version '4.3.2' is up to date...
==> worker1: Setting the name of the VM: k8s_worker1_1775150691539_56200
==> worker1: Fixed port collision for 22 => 2222. Now on port 2200.
==> worker1: Clearing any previously set network interfaces...
==> worker1: Preparing network interfaces based on configuration...
    worker1: Adapter 1: nat
    worker1: Adapter 2: hostonly
==> worker1: Forwarding ports...
    worker1: 22 (guest) => 2200 (host) (adapter 1)
==> worker1: Running 'pre-boot' VM customizations...
==> worker1: Booting VM...
==> worker1: Waiting for machine to boot. This may take a few minutes...
    worker1: SSH address: 127.0.0.1:2200
    worker1: SSH username: vagrant
    worker1: SSH auth method: private key
    worker1: Warning: Connection reset. Retrying...
    worker1: Warning: Connection reset. Retrying...
    worker1: Warning: Connection reset. Retrying...
    worker1: Warning: Connection reset. Retrying...
    worker1: Warning: Connection reset. Retrying...
    worker1: Warning: Connection reset. Retrying...
    worker1: Warning: Connection reset. Retrying...
    worker1: Warning: Connection reset. Retrying...
    worker1: Warning: Connection reset. Retrying...
    worker1: Warning: Connection reset. Retrying...
    worker1: Warning: Connection reset. Retrying...
    worker1: Warning: Connection reset. Retrying...
    worker1: Warning: Connection reset. Retrying...
    worker1:
    worker1: Vagrant insecure key detected. Vagrant will automatically replace
    worker1: this with a newly generated keypair for better security.
    worker1:
    worker1: Inserting generated public key within guest...
    worker1: Removing insecure key from the guest if it's present...
    worker1: Key inserted! Disconnecting and reconnecting using new SSH key...
==> worker1: Machine booted and ready!
==> worker1: Checking for guest additions in VM...
    worker1: The guest additions on this VM do not match the installed version of
    worker1: VirtualBox! In most cases this is fine, but in rare cases it can
    worker1: prevent things such as shared folders from working properly. If you see
    worker1: shared folder errors, please make sure the guest additions within the
    worker1: virtual machine match the version of VirtualBox you have installed on
    worker1: your host and reload your VM.
    worker1:
    worker1: Guest Additions Version: 6.1.38
    worker1: VirtualBox Version: 7.1
==> worker1: Setting hostname...
==> worker1: Configuring and enabling network interfaces...
==> worker1: Mounting shared folders...
    worker1: C:/Users/Windows/k8s => /vagrant
==> worker1: Running provisioner: shell...
    worker1: Running: inline script
    worker1: ++ NODE_IP=192.168.56.25
    worker1: ++ swapoff -a
    worker1: ++ sed -i /swap/d /etc/fstab
    worker1: ++ systemctl disable --now systemd-zram-setup@zram0.service
    worker1: ++ true
    worker1: ++ apt-get update -y
    worker1: Hit:1 https://mirrors.edge.kernel.org/ubuntu jammy InRelease
    worker1: Get:2 https://mirrors.edge.kernel.org/ubuntu jammy-updates InRelease [128 kB]
    worker1: Get:3 https://mirrors.edge.kernel.org/ubuntu jammy-backports InRelease [127 kB]
    worker1: Get:4 https://mirrors.edge.kernel.org/ubuntu jammy-security InRelease [129 kB]
    worker1: Get:5 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 Packages [3,365 kB]
    worker1: Get:6 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main Translation-en [512 kB]
    worker1: Get:7 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 c-n-f Metadata [19.6 kB]
    worker1: Get:8 https://mirrors.edge.kernel.org/ubuntu jammy-updates/restricted amd64 Packages [5,608 kB]
    worker1: Get:9 https://mirrors.edge.kernel.org/ubuntu jammy-updates/restricted Translation-en [1,075 kB]
    worker1: Get:10 https://mirrors.edge.kernel.org/ubuntu jammy-updates/restricted amd64 c-n-f Metadata [676 B]
    worker1: Get:11 https://mirrors.edge.kernel.org/ubuntu jammy-updates/universe amd64 Packages [1,262 kB]
    worker1: Get:12 https://mirrors.edge.kernel.org/ubuntu jammy-updates/universe Translation-en [316 kB]
    worker1: Get:13 https://mirrors.edge.kernel.org/ubuntu jammy-updates/universe amd64 c-n-f Metadata [30.5 kB]
    worker1: Get:14 https://mirrors.edge.kernel.org/ubuntu jammy-updates/multiverse amd64 Packages [59.0 kB]
    worker1: Get:15 https://mirrors.edge.kernel.org/ubuntu jammy-updates/multiverse Translation-en [13.5 kB]
    worker1: Get:16 https://mirrors.edge.kernel.org/ubuntu jammy-updates/multiverse amd64 c-n-f Metadata [612 B]
    worker1: Get:17 https://mirrors.edge.kernel.org/ubuntu jammy-backports/main amd64 Packages [69.4 kB]
    worker1: Get:18 https://mirrors.edge.kernel.org/ubuntu jammy-backports/main Translation-en [11.5 kB]
    worker1: Get:19 https://mirrors.edge.kernel.org/ubuntu jammy-backports/main amd64 c-n-f Metadata [412 B]
    worker1: Get:20 https://mirrors.edge.kernel.org/ubuntu jammy-backports/universe amd64 Packages [30.4 kB]
    worker1: Get:21 https://mirrors.edge.kernel.org/ubuntu jammy-backports/universe Translation-en [16.9 kB]
    worker1: Get:22 https://mirrors.edge.kernel.org/ubuntu jammy-backports/universe amd64 c-n-f Metadata [672 B]
    worker1: Get:23 https://mirrors.edge.kernel.org/ubuntu jammy-security/main amd64 Packages [3,068 kB]
    worker1: Get:24 https://mirrors.edge.kernel.org/ubuntu jammy-security/main Translation-en [438 kB]
    worker1: Get:25 https://mirrors.edge.kernel.org/ubuntu jammy-security/main amd64 c-n-f Metadata [14.1 kB]
    worker1: Get:26 https://mirrors.edge.kernel.org/ubuntu jammy-security/restricted amd64 Packages [5,356 kB]
    worker1: Get:27 https://mirrors.edge.kernel.org/ubuntu jammy-security/restricted Translation-en [1,025 kB]
    worker1: Get:28 https://mirrors.edge.kernel.org/ubuntu jammy-security/restricted amd64 c-n-f Metadata [680 B]
    worker1: Get:29 https://mirrors.edge.kernel.org/ubuntu jammy-security/universe amd64 Packages [1,025 kB]
    worker1: Get:30 https://mirrors.edge.kernel.org/ubuntu jammy-security/universe Translation-en [226 kB]
    worker1: Get:31 https://mirrors.edge.kernel.org/ubuntu jammy-security/universe amd64 c-n-f Metadata [22.8 kB]
    worker1: Get:32 https://mirrors.edge.kernel.org/ubuntu jammy-security/multiverse amd64 Packages [51.9 kB]
    worker1: Get:33 https://mirrors.edge.kernel.org/ubuntu jammy-security/multiverse Translation-en [10.6 kB]
    worker1: Get:34 https://mirrors.edge.kernel.org/ubuntu jammy-security/multiverse amd64 c-n-f Metadata [388 B]
    worker1: Fetched 24.0 MB in 6min 43s (59.6 kB/s)
    worker1: Reading package lists...
    worker1: ++ apt-get install -y apt-transport-https ca-certificates curl wget gnupg lsb-release net-tools iproute2 bash-completion conntrack socat
    worker1: Reading package lists...
    worker1: Building dependency tree...
    worker1: Reading state information...
    worker1: bash-completion is already the newest version (1:2.11-5ubuntu1).
    worker1: bash-completion set to manually installed.
    worker1: iproute2 is already the newest version (5.15.0-1ubuntu2).
    worker1: iproute2 set to manually installed.
    worker1: lsb-release is already the newest version (11.1.0ubuntu4).
    worker1: The following additional packages will be installed:
    worker1:   dirmngr gnupg-l10n gnupg-utils gpg gpg-agent gpg-wks-client gpg-wks-server
    worker1:   gpgconf gpgsm gpgv libcurl4
    worker1: Suggested packages:
    worker1:   pinentry-gnome3 tor parcimonie xloadimage scdaemon
    worker1: The following NEW packages will be installed:
    worker1:   apt-transport-https conntrack net-tools socat
    worker1: The following packages will be upgraded:
    worker1:   ca-certificates curl dirmngr gnupg gnupg-l10n gnupg-utils gpg gpg-agent
    worker1:   gpg-wks-client gpg-wks-server gpgconf gpgsm gpgv libcurl4 wget
    worker1: 15 upgraded, 4 newly installed, 0 to remove and 252 not upgraded.
    worker1: Need to get 3,821 kB of archives.
    worker1: After this operation, 2,429 kB of additional disk space will be used.
    worker1: Get:1 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpg-wks-client amd64 2.2.27-3ubuntu2.5 [62.7 kB]
    worker1: Get:2 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 dirmngr amd64 2.2.27-3ubuntu2.5 [293 kB]
    worker1: Get:3 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpg-wks-server amd64 2.2.27-3ubuntu2.5 [57.6 kB]
    worker1: Get:4 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gnupg-utils amd64 2.2.27-3ubuntu2.5 [309 kB]
    worker1: Get:5 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpg-agent amd64 2.2.27-3ubuntu2.5 [209 kB]
    worker1: Get:6 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpg amd64 2.2.27-3ubuntu2.5 [519 kB]
    worker1: Get:7 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpgconf amd64 2.2.27-3ubuntu2.5 [94.3 kB]
    worker1: Get:8 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gnupg-l10n all 2.2.27-3ubuntu2.5 [54.5 kB]
    worker1: Get:9 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gnupg all 2.2.27-3ubuntu2.5 [315 kB]
    worker1: Get:10 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpgsm amd64 2.2.27-3ubuntu2.5 [197 kB]
    worker1: Get:11 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpgv amd64 2.2.27-3ubuntu2.5 [137 kB]
    worker1: Get:12 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 ca-certificates all 20240203~22.04.1 [162 kB]
    worker1: Get:13 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 wget amd64 1.21.2-2ubuntu1.1 [339 kB]
    worker1: Get:14 https://mirrors.edge.kernel.org/ubuntu jammy-updates/universe amd64 apt-transport-https all 2.4.14 [1,510 B]
    worker1: Get:15 https://mirrors.edge.kernel.org/ubuntu jammy/main amd64 conntrack amd64 1:1.4.6-2build2 [33.5 kB]
    worker1: Get:16 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 curl amd64 7.81.0-1ubuntu1.23 [194 kB]
    worker1: Get:17 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 libcurl4 amd64 7.81.0-1ubuntu1.23 [290 kB]
    worker1: Get:18 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 net-tools amd64 1.60+git20181103.0eebece-1ubuntu5.4 [204 kB]
    worker1: Get:19 https://mirrors.edge.kernel.org/ubuntu jammy/main amd64 socat amd64 1.7.4.1-3ubuntu4 [349 kB]
    worker1: dpkg-preconfigure: unable to re-open stdin: No such file or directory
    worker1: Fetched 3,821 kB in 1min 32s (41.7 kB/s)
(Reading database ... 76032 files and directories currently installed.)
    worker1: Preparing to unpack .../00-gpg-wks-client_2.2.27-3ubuntu2.5_amd64.deb ...
    worker1: Unpacking gpg-wks-client (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker1: Preparing to unpack .../01-dirmngr_2.2.27-3ubuntu2.5_amd64.deb ...
    worker1: Unpacking dirmngr (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker1: Preparing to unpack .../02-gpg-wks-server_2.2.27-3ubuntu2.5_amd64.deb ...
    worker1: Unpacking gpg-wks-server (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker1: Preparing to unpack .../03-gnupg-utils_2.2.27-3ubuntu2.5_amd64.deb ...
    worker1: Unpacking gnupg-utils (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker1: Preparing to unpack .../04-gpg-agent_2.2.27-3ubuntu2.5_amd64.deb ...
    worker1: Unpacking gpg-agent (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker1: Preparing to unpack .../05-gpg_2.2.27-3ubuntu2.5_amd64.deb ...
    worker1: Unpacking gpg (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker1: Preparing to unpack .../06-gpgconf_2.2.27-3ubuntu2.5_amd64.deb ...
    worker1: Unpacking gpgconf (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker1: Preparing to unpack .../07-gnupg-l10n_2.2.27-3ubuntu2.5_all.deb ...
    worker1: Unpacking gnupg-l10n (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker1: Preparing to unpack .../08-gnupg_2.2.27-3ubuntu2.5_all.deb ...
    worker1: Unpacking gnupg (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker1: Preparing to unpack .../09-gpgsm_2.2.27-3ubuntu2.5_amd64.deb ...
    worker1: Unpacking gpgsm (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker1: Preparing to unpack .../10-gpgv_2.2.27-3ubuntu2.5_amd64.deb ...
    worker1: Unpacking gpgv (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker1: Setting up gpgv (2.2.27-3ubuntu2.5) ...
(Reading database ... 76032 files and directories currently installed.)
    worker1: Preparing to unpack .../0-ca-certificates_20240203~22.04.1_all.deb ...
    worker1: Unpacking ca-certificates (20240203~22.04.1) over (20230311ubuntu0.22.04.1) ...
    worker1: Preparing to unpack .../1-wget_1.21.2-2ubuntu1.1_amd64.deb ...
    worker1: Unpacking wget (1.21.2-2ubuntu1.1) over (1.21.2-2ubuntu1) ...
    worker1: Selecting previously unselected package apt-transport-https.
    worker1: Preparing to unpack .../2-apt-transport-https_2.4.14_all.deb ...
    worker1: Unpacking apt-transport-https (2.4.14) ...
    worker1: Selecting previously unselected package conntrack.
    worker1: Preparing to unpack .../3-conntrack_1%3a1.4.6-2build2_amd64.deb ...
    worker1: Unpacking conntrack (1:1.4.6-2build2) ...
    worker1: Preparing to unpack .../4-curl_7.81.0-1ubuntu1.23_amd64.deb ...
    worker1: Unpacking curl (7.81.0-1ubuntu1.23) over (7.81.0-1ubuntu1.13) ...
    worker1: Preparing to unpack .../5-libcurl4_7.81.0-1ubuntu1.23_amd64.deb ...
    worker1: Unpacking libcurl4:amd64 (7.81.0-1ubuntu1.23) over (7.81.0-1ubuntu1.13) ...
    worker1: Selecting previously unselected package net-tools.
    worker1: Preparing to unpack .../6-net-tools_1.60+git20181103.0eebece-1ubuntu5.4_amd64.deb ...
    worker1: Unpacking net-tools (1.60+git20181103.0eebece-1ubuntu5.4) ...
    worker1: Selecting previously unselected package socat.
    worker1: Preparing to unpack .../7-socat_1.7.4.1-3ubuntu4_amd64.deb ...
    worker1: Unpacking socat (1.7.4.1-3ubuntu4) ...
    worker1: Setting up net-tools (1.60+git20181103.0eebece-1ubuntu5.4) ...
    worker1: Setting up wget (1.21.2-2ubuntu1.1) ...
    worker1: Setting up apt-transport-https (2.4.14) ...
    worker1: Setting up conntrack (1:1.4.6-2build2) ...
    worker1: Setting up ca-certificates (20240203~22.04.1) ...
    worker1: Updating certificates in /etc/ssl/certs...
    worker1: rehash: warning: skipping ca-certificates.crt,it does not contain exactly one certificate or CRL
    worker1: 14 added, 5 removed; done.
    worker1: Setting up gnupg-l10n (2.2.27-3ubuntu2.5) ...
    worker1: Setting up socat (1.7.4.1-3ubuntu4) ...
    worker1: Setting up gpgconf (2.2.27-3ubuntu2.5) ...
    worker1: Setting up libcurl4:amd64 (7.81.0-1ubuntu1.23) ...
    worker1: Setting up curl (7.81.0-1ubuntu1.23) ...
    worker1: Setting up gpg (2.2.27-3ubuntu2.5) ...
    worker1: Setting up gnupg-utils (2.2.27-3ubuntu2.5) ...
    worker1: Setting up gpg-agent (2.2.27-3ubuntu2.5) ...
    worker1: Setting up gpgsm (2.2.27-3ubuntu2.5) ...
    worker1: Setting up dirmngr (2.2.27-3ubuntu2.5) ...
    worker1: Setting up gpg-wks-server (2.2.27-3ubuntu2.5) ...
    worker1: Setting up gpg-wks-client (2.2.27-3ubuntu2.5) ...
    worker1: Setting up gnupg (2.2.27-3ubuntu2.5) ...
    worker1: Processing triggers for libc-bin (2.35-0ubuntu3.3) ...
    worker1: Processing triggers for man-db (2.10.2-1) ...
    worker1: Processing triggers for install-info (6.8-4build1) ...
    worker1: Processing triggers for ca-certificates (20240203~22.04.1) ...
    worker1: Updating certificates in /etc/ssl/certs...
    worker1: 0 added, 0 removed; done.
    worker1: Running hooks in /etc/ca-certificates/update.d...
    worker1: done.
    worker1:
    worker1: Running kernel seems to be up-to-date.
    worker1:
    worker1: No services need to be restarted.
    worker1:
    worker1: No containers need to be restarted.
    worker1:
    worker1: No user sessions are running outdated binaries.
    worker1:
    worker1: No VM guests are running outdated hypervisor (qemu) binaries on this host.
    worker1: ++ VERSION=1.7.24
    worker1: ++ wget -q https://github.com/containerd/containerd/releases/download/v1.7.24/containerd-1.7.24-linux-amd64.tar.gz
    worker1: ++ tar Cxzvf /usr/local containerd-1.7.24-linux-amd64.tar.gz
    worker1: bin/
    worker1: bin/ctr
    worker1: bin/containerd
    worker1: bin/containerd-shim
    worker1: bin/containerd-shim-runc-v1
    worker1: bin/containerd-stress
    worker1: bin/containerd-shim-runc-v2
    worker1: ++ mkdir -p /usr/local/lib/systemd/system
    worker1: ++ wget -q -P /usr/local/lib/systemd/system https://raw.githubusercontent.com/containerd/containerd/main/containerd.service
    worker1: ++ systemctl daemon-reload
    worker1: ++ systemctl enable --now containerd
    worker1: Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /usr/local/lib/systemd/system/containerd.service.
    worker1: ++ RUNC=v1.2.2
    worker1: ++ wget -q https://github.com/opencontainers/runc/releases/download/v1.2.2/runc.amd64
    worker1: ++ install -m 755 runc.amd64 /usr/local/sbin/runc
    worker1: ++ CNI=v1.6.0
    worker1: ++ mkdir -p /opt/cni/bin
    worker1: ++ wget -q https://github.com/containernetworking/plugins/releases/download/v1.6.0/cni-plugins-linux-amd64-v1.6.0.tgz
    worker1: ++ tar Cxzvf /opt/cni/bin cni-plugins-linux-amd64-v1.6.0.tgz
    worker1: ./
    worker1: ./vrf
    worker1: ./firewall
    worker1: ./LICENSE
    worker1: ./macvlan
    worker1: ./static
    worker1: ./host-device
    worker1: ./host-local
    worker1: ./loopback
    worker1: ./sbr
    worker1: ./tuning
    worker1: ./bridge
    worker1: ./README.md
    worker1: ./ptp
    worker1: ./bandwidth
    worker1: ./vlan
    worker1: ./portmap
    worker1: ./ipvlan
    worker1: ./dummy
    worker1: ./tap
    worker1: ./dhcp
    worker1: ++ mkdir -p /etc/containerd
    worker1: ++ containerd config default
    worker1: ++ sed -i 's/SystemdCgroup = false/SystemdCgroup = true/' /etc/containerd/config.toml
    worker1: ++ sed -i 's|sandbox_image = "registry.k8s.io/pause:3.8"|sandbox_image = "registry.k8s.io/pause:3.9"|' /etc/containerd/config.toml
    worker1: ++ systemctl restart containerd
    worker1: ++ cat
    worker1: ++ tee /etc/modules-load.d/k8s.conf
    worker1: overlay
    worker1: br_netfilter
    worker1: ++ modprobe overlay
    worker1: ++ modprobe br_netfilter
    worker1: ++ tee /etc/sysctl.d/k8s.conf
    worker1: ++ cat
    worker1: net.bridge.bridge-nf-call-iptables=1
    worker1: net.bridge.bridge-nf-call-ip6tables=1
    worker1: net.ipv4.ip_forward=1
    worker1: ++ sysctl --system
    worker1: * Applying /etc/sysctl.d/10-console-messages.conf ...
    worker1: kernel.printk = 4 4 1 7
    worker1: * Applying /etc/sysctl.d/10-ipv6-privacy.conf ...
    worker1: net.ipv6.conf.all.use_tempaddr = 2
    worker1: net.ipv6.conf.default.use_tempaddr = 2
    worker1: * Applying /etc/sysctl.d/10-kernel-hardening.conf ...
    worker1: kernel.kptr_restrict = 1
    worker1: * Applying /etc/sysctl.d/10-magic-sysrq.conf ...
    worker1: kernel.sysrq = 176
    worker1: * Applying /etc/sysctl.d/10-network-security.conf ...
    worker1: net.ipv4.conf.default.rp_filter = 2
    worker1: net.ipv4.conf.all.rp_filter = 2
    worker1: * Applying /etc/sysctl.d/10-ptrace.conf ...
    worker1: kernel.yama.ptrace_scope = 1
    worker1: * Applying /etc/sysctl.d/10-zeropage.conf ...
    worker1: vm.mmap_min_addr = 65536
    worker1: * Applying /usr/lib/sysctl.d/50-default.conf ...
    worker1: kernel.core_uses_pid = 1
    worker1: net.ipv4.conf.default.rp_filter = 2
    worker1: net.ipv4.conf.default.accept_source_route = 0
    worker1: sysctl: setting key "net.ipv4.conf.all.accept_source_route": Invalid argument
    worker1: net.ipv4.conf.default.promote_secondaries = 1
    worker1: sysctl: setting key "net.ipv4.conf.all.promote_secondaries": Invalid argument
    worker1: net.ipv4.ping_group_range = 0 2147483647
    worker1: net.core.default_qdisc = fq_codel
    worker1: fs.protected_hardlinks = 1
    worker1: fs.protected_symlinks = 1
    worker1: fs.protected_regular = 1
    worker1: fs.protected_fifos = 1
    worker1: * Applying /usr/lib/sysctl.d/50-pid-max.conf ...
    worker1: kernel.pid_max = 4194304
    worker1: * Applying /usr/lib/sysctl.d/99-protect-links.conf ...
    worker1: fs.protected_fifos = 1
    worker1: fs.protected_hardlinks = 1
    worker1: fs.protected_regular = 2
    worker1: fs.protected_symlinks = 1
    worker1: * Applying /etc/sysctl.d/99-sysctl.conf ...
    worker1: net.ipv6.conf.all.disable_ipv6 = 1
    worker1: * Applying /etc/sysctl.d/k8s.conf ...
    worker1: net.bridge.bridge-nf-call-iptables = 1
    worker1: net.bridge.bridge-nf-call-ip6tables = 1
    worker1: net.ipv4.ip_forward = 1
    worker1: * Applying /etc/sysctl.conf ...
    worker1: net.ipv6.conf.all.disable_ipv6 = 1
    worker1: ++ curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.30/deb/Release.key
    worker1: ++ gpg --dearmor -o /etc/apt/trusted.gpg.d/k8s.gpg
    worker1: ++ echo 'deb [signed-by=/etc/apt/trusted.gpg.d/k8s.gpg] https://pkgs.k8s.io/core:/stable:/v1.30/deb/ /'
    worker1: ++ apt-get update
    worker1: Hit:2 https://mirrors.edge.kernel.org/ubuntu jammy InRelease
    worker1: Get:3 https://mirrors.edge.kernel.org/ubuntu jammy-updates InRelease [128 kB]
    worker1: Get:1 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  InRelease [1,192 B]
    worker1: Get:4 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  Packages [20.3 kB]
    worker1: Get:5 https://mirrors.edge.kernel.org/ubuntu jammy-backports InRelease [127 kB]
    worker1: Get:6 https://mirrors.edge.kernel.org/ubuntu jammy-security InRelease [129 kB]
    worker1: Fetched 406 kB in 7s (60.4 kB/s)
    worker1: Reading package lists...
    worker1: ++ apt-get install -y kubelet kubeadm kubectl
    worker1: Reading package lists...
    worker1: Building dependency tree...
    worker1: Reading state information...
    worker1: The following additional packages will be installed:
    worker1:   cri-tools kubernetes-cni
    worker1: The following NEW packages will be installed:
    worker1:   cri-tools kubeadm kubectl kubelet kubernetes-cni
    worker1: 0 upgraded, 5 newly installed, 0 to remove and 252 not upgraded.
    worker1: Need to get 93.7 MB of archives.
    worker1: After this operation, 343 MB of additional disk space will be used.
    worker1: Get:1 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  cri-tools 1.30.1-1.1 [21.3 MB]
    worker1: Get:2 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  kubeadm 1.30.14-1.1 [10.5 MB]
    worker1: Get:3 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  kubectl 1.30.14-1.1 [10.9 MB]
    worker1: Get:4 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  kubernetes-cni 1.4.0-1.1 [32.9 MB]
    worker1: Get:5 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  kubelet 1.30.14-1.1 [18.2 MB]
    worker1: dpkg-preconfigure: unable to re-open stdin: No such file or directory
    worker1: Fetched 93.7 MB in 10min 11s (153 kB/s)
    worker1: Selecting previously unselected package cri-tools.
(Reading database ... 76139 files and directories currently installed.)
    worker1: Preparing to unpack .../cri-tools_1.30.1-1.1_amd64.deb ...
    worker1: Unpacking cri-tools (1.30.1-1.1) ...
    worker1: Selecting previously unselected package kubeadm.
    worker1: Preparing to unpack .../kubeadm_1.30.14-1.1_amd64.deb ...
    worker1: Unpacking kubeadm (1.30.14-1.1) ...
    worker1: Selecting previously unselected package kubectl.
    worker1: Preparing to unpack .../kubectl_1.30.14-1.1_amd64.deb ...
    worker1: Unpacking kubectl (1.30.14-1.1) ...
    worker1: Selecting previously unselected package kubernetes-cni.
    worker1: Preparing to unpack .../kubernetes-cni_1.4.0-1.1_amd64.deb ...
    worker1: Unpacking kubernetes-cni (1.4.0-1.1) ...
    worker1: Selecting previously unselected package kubelet.
    worker1: Preparing to unpack .../kubelet_1.30.14-1.1_amd64.deb ...
    worker1: Unpacking kubelet (1.30.14-1.1) ...
    worker1: Setting up kubectl (1.30.14-1.1) ...
    worker1: Setting up cri-tools (1.30.1-1.1) ...
    worker1: Setting up kubernetes-cni (1.4.0-1.1) ...
    worker1: Setting up kubeadm (1.30.14-1.1) ...
    worker1: Setting up kubelet (1.30.14-1.1) ...
    worker1:
    worker1: Running kernel seems to be up-to-date.
    worker1:
    worker1: No services need to be restarted.
    worker1:
    worker1: No containers need to be restarted.
    worker1:
    worker1: No user sessions are running outdated binaries.
    worker1:
    worker1: No VM guests are running outdated hypervisor (qemu) binaries on this host.
    worker1: ++ apt-mark hold kubelet kubeadm kubectl
    worker1: kubelet set on hold.
    worker1: kubeadm set on hold.
    worker1: kubectl set on hold.
    worker1: ++ mkdir -p /etc/default
    worker1: ++ echo KUBELET_EXTRA_ARGS=--node-ip=192.168.56.25
    worker1: ++ systemctl enable kubelet
    worker1: ++ kubeadm config images pull
    worker1: I0402 18:04:00.107328    8041 version.go:256] remote version is much newer: v1.35.3; falling back to: stable-1.30
    worker1: [config/images] Pulled registry.k8s.io/kube-apiserver:v1.30.14
    worker1: [config/images] Pulled registry.k8s.io/kube-controller-manager:v1.30.14
    worker1: [config/images] Pulled registry.k8s.io/kube-scheduler:v1.30.14
    worker1: [config/images] Pulled registry.k8s.io/kube-proxy:v1.30.14
    worker1: [config/images] Pulled registry.k8s.io/coredns/coredns:v1.11.3
    worker1: [config/images] Pulled registry.k8s.io/pause:3.9
    worker1: [config/images] Pulled registry.k8s.io/etcd:3.5.15-0
==> worker1: Running provisioner: shell...
    worker1: Running: inline script
    worker1: ++ for i in {1..30}
    worker1: ++ '[' -f /vagrant/join.sh ']'
    worker1: ++ break
    worker1: ++ '[' -f /vagrant/join.sh ']'
    worker1: ++ bash /vagrant/join.sh --cri-socket unix:///run/containerd/containerd.sock
    worker1: [preflight] Running pre-flight checks
    worker1: [preflight] Reading configuration from the cluster...
    worker1: [preflight] FYI: You can look at this config file with 'kubectl -n kube-system get cm kubeadm-config -o yaml'
    worker1: [kubelet-start] Writing kubelet configuration to file "/var/lib/kubelet/config.yaml"
    worker1: [kubelet-start] Writing kubelet environment file with flags to file "/var/lib/kubelet/kubeadm-flags.env"
    worker1: [kubelet-start] Starting the kubelet
    worker1: [kubelet-check] Waiting for a healthy kubelet at http://127.0.0.1:10248/healthz. This can take up to 4m0s
    worker1: [kubelet-check] The kubelet is healthy after 1.509209332s
    worker1: [kubelet-start] Waiting for the kubelet to perform the TLS Bootstrap
    worker1:
    worker1: This node has joined the cluster:
    worker1: * Certificate signing request was sent to apiserver and a response was received.
    worker1: * The Kubelet was informed of the new secure connection details.
    worker1:
    worker1: Run 'kubectl get nodes' on the control-plane to see this node join the cluster.
    worker1:
==> worker2: Importing base box 'generic/ubuntu2204'...
==> worker2: Matching MAC address for NAT networking...
==> worker2: Checking if box 'generic/ubuntu2204' version '4.3.2' is up to date...
==> worker2: Setting the name of the VM: k8s_worker2_1775154174462_60228
==> worker2: Fixed port collision for 22 => 2222. Now on port 2201.
==> worker2: Clearing any previously set network interfaces...
==> worker2: Preparing network interfaces based on configuration...
    worker2: Adapter 1: nat
    worker2: Adapter 2: hostonly
==> worker2: Forwarding ports...
    worker2: 22 (guest) => 2201 (host) (adapter 1)
==> worker2: Running 'pre-boot' VM customizations...
==> worker2: Booting VM...
==> worker2: Waiting for machine to boot. This may take a few minutes...
    worker2: SSH address: 127.0.0.1:2201
    worker2: SSH username: vagrant
    worker2: SSH auth method: private key
    worker2: Warning: Connection reset. Retrying...
    worker2: Warning: Connection reset. Retrying...
    worker2: Warning: Connection reset. Retrying...
    worker2: Warning: Connection reset. Retrying...
    worker2: Warning: Connection reset. Retrying...
    worker2: Warning: Connection reset. Retrying...
    worker2: Warning: Connection reset. Retrying...
    worker2: Warning: Connection reset. Retrying...
    worker2: Warning: Connection reset. Retrying...
    worker2: Warning: Connection reset. Retrying...
    worker2: Warning: Connection reset. Retrying...
    worker2: Warning: Connection reset. Retrying...
    worker2:
    worker2: Vagrant insecure key detected. Vagrant will automatically replace
    worker2: this with a newly generated keypair for better security.
    worker2:
    worker2: Inserting generated public key within guest...
    worker2: Removing insecure key from the guest if it's present...
    worker2: Key inserted! Disconnecting and reconnecting using new SSH key...
==> worker2: Machine booted and ready!
==> worker2: Checking for guest additions in VM...
    worker2: The guest additions on this VM do not match the installed version of
    worker2: VirtualBox! In most cases this is fine, but in rare cases it can
    worker2: prevent things such as shared folders from working properly. If you see
    worker2: shared folder errors, please make sure the guest additions within the
    worker2: virtual machine match the version of VirtualBox you have installed on
    worker2: your host and reload your VM.
    worker2:
    worker2: Guest Additions Version: 6.1.38
    worker2: VirtualBox Version: 7.1
==> worker2: Setting hostname...
==> worker2: Configuring and enabling network interfaces...
==> worker2: Mounting shared folders...
    worker2: C:/Users/Windows/k8s => /vagrant
==> worker2: Running provisioner: shell...
    worker2: Running: inline script
    worker2: ++ NODE_IP=192.168.56.26
    worker2: ++ swapoff -a
    worker2: ++ sed -i /swap/d /etc/fstab
    worker2: ++ systemctl disable --now systemd-zram-setup@zram0.service
    worker2: ++ true
    worker2: ++ apt-get update -y
    worker2: Hit:1 https://mirrors.edge.kernel.org/ubuntu jammy InRelease
    worker2: Get:2 https://mirrors.edge.kernel.org/ubuntu jammy-updates InRelease [128 kB]
    worker2: Get:3 https://mirrors.edge.kernel.org/ubuntu jammy-backports InRelease [127 kB]
    worker2: Get:4 https://mirrors.edge.kernel.org/ubuntu jammy-security InRelease [129 kB]
    worker2: Get:5 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 Packages [3,365 kB]
    worker2: Get:6 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main Translation-en [512 kB]
    worker2: Get:7 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 c-n-f Metadata [19.6 kB]
    worker2: Get:8 https://mirrors.edge.kernel.org/ubuntu jammy-updates/restricted amd64 Packages [5,608 kB]
    worker2: Get:9 https://mirrors.edge.kernel.org/ubuntu jammy-updates/restricted Translation-en [1,075 kB]
    worker2: Get:10 https://mirrors.edge.kernel.org/ubuntu jammy-updates/restricted amd64 c-n-f Metadata [676 B]
    worker2: Get:11 https://mirrors.edge.kernel.org/ubuntu jammy-updates/universe amd64 Packages [1,262 kB]
    worker2: Get:12 https://mirrors.edge.kernel.org/ubuntu jammy-updates/universe Translation-en [316 kB]
    worker2: Get:13 https://mirrors.edge.kernel.org/ubuntu jammy-updates/universe amd64 c-n-f Metadata [30.5 kB]
    worker2: Get:14 https://mirrors.edge.kernel.org/ubuntu jammy-updates/multiverse amd64 Packages [59.0 kB]
    worker2: Get:15 https://mirrors.edge.kernel.org/ubuntu jammy-updates/multiverse Translation-en [13.5 kB]
    worker2: Get:16 https://mirrors.edge.kernel.org/ubuntu jammy-updates/multiverse amd64 c-n-f Metadata [612 B]
    worker2: Get:17 https://mirrors.edge.kernel.org/ubuntu jammy-backports/main amd64 Packages [69.4 kB]
    worker2: Get:18 https://mirrors.edge.kernel.org/ubuntu jammy-backports/main Translation-en [11.5 kB]
    worker2: Get:19 https://mirrors.edge.kernel.org/ubuntu jammy-backports/main amd64 c-n-f Metadata [412 B]
    worker2: Get:20 https://mirrors.edge.kernel.org/ubuntu jammy-backports/universe amd64 Packages [30.4 kB]
    worker2: Get:21 https://mirrors.edge.kernel.org/ubuntu jammy-backports/universe Translation-en [16.9 kB]
    worker2: Get:22 https://mirrors.edge.kernel.org/ubuntu jammy-backports/universe amd64 c-n-f Metadata [672 B]
    worker2: Get:23 https://mirrors.edge.kernel.org/ubuntu jammy-security/main amd64 Packages [3,068 kB]
    worker2: Get:24 https://mirrors.edge.kernel.org/ubuntu jammy-security/main Translation-en [438 kB]
    worker2: Get:25 https://mirrors.edge.kernel.org/ubuntu jammy-security/main amd64 c-n-f Metadata [14.1 kB]
    worker2: Get:26 https://mirrors.edge.kernel.org/ubuntu jammy-security/restricted amd64 Packages [5,356 kB]
    worker2: Get:27 https://mirrors.edge.kernel.org/ubuntu jammy-security/restricted Translation-en [1,025 kB]
    worker2: Get:28 https://mirrors.edge.kernel.org/ubuntu jammy-security/restricted amd64 c-n-f Metadata [680 B]
    worker2: Get:29 https://mirrors.edge.kernel.org/ubuntu jammy-security/universe amd64 Packages [1,025 kB]
    worker2: Get:30 https://mirrors.edge.kernel.org/ubuntu jammy-security/universe Translation-en [226 kB]
    worker2: Get:31 https://mirrors.edge.kernel.org/ubuntu jammy-security/universe amd64 c-n-f Metadata [22.8 kB]
    worker2: Get:32 https://mirrors.edge.kernel.org/ubuntu jammy-security/multiverse amd64 Packages [51.9 kB]
    worker2: Get:33 https://mirrors.edge.kernel.org/ubuntu jammy-security/multiverse Translation-en [10.6 kB]
    worker2: Get:34 https://mirrors.edge.kernel.org/ubuntu jammy-security/multiverse amd64 c-n-f Metadata [388 B]
    worker2: Fetched 24.0 MB in 2min 38s (152 kB/s)
    worker2: Reading package lists...
    worker2: ++ apt-get install -y apt-transport-https ca-certificates curl wget gnupg lsb-release net-tools iproute2 bash-completion conntrack socat
    worker2: Reading package lists...
    worker2: Building dependency tree...
    worker2: Reading state information...
    worker2: bash-completion is already the newest version (1:2.11-5ubuntu1).
    worker2: bash-completion set to manually installed.
    worker2: iproute2 is already the newest version (5.15.0-1ubuntu2).
    worker2: iproute2 set to manually installed.
    worker2: lsb-release is already the newest version (11.1.0ubuntu4).
    worker2: The following additional packages will be installed:
    worker2:   dirmngr gnupg-l10n gnupg-utils gpg gpg-agent gpg-wks-client gpg-wks-server
    worker2:   gpgconf gpgsm gpgv libcurl4
    worker2: Suggested packages:
    worker2:   pinentry-gnome3 tor parcimonie xloadimage scdaemon
    worker2: The following NEW packages will be installed:
    worker2:   apt-transport-https conntrack net-tools socat
    worker2: The following packages will be upgraded:
    worker2:   ca-certificates curl dirmngr gnupg gnupg-l10n gnupg-utils gpg gpg-agent
    worker2:   gpg-wks-client gpg-wks-server gpgconf gpgsm gpgv libcurl4 wget
    worker2: 15 upgraded, 4 newly installed, 0 to remove and 252 not upgraded.
    worker2: Need to get 3,821 kB of archives.
    worker2: After this operation, 2,429 kB of additional disk space will be used.
    worker2: Get:1 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpg-wks-client amd64 2.2.27-3ubuntu2.5 [62.7 kB]
    worker2: Get:2 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 dirmngr amd64 2.2.27-3ubuntu2.5 [293 kB]
    worker2: Get:3 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpg-wks-server amd64 2.2.27-3ubuntu2.5 [57.6 kB]
    worker2: Get:4 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gnupg-utils amd64 2.2.27-3ubuntu2.5 [309 kB]
    worker2: Get:5 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpg-agent amd64 2.2.27-3ubuntu2.5 [209 kB]
    worker2: Get:6 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpg amd64 2.2.27-3ubuntu2.5 [519 kB]
    worker2: Get:7 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpgconf amd64 2.2.27-3ubuntu2.5 [94.3 kB]
    worker2: Get:8 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gnupg-l10n all 2.2.27-3ubuntu2.5 [54.5 kB]
    worker2: Get:9 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gnupg all 2.2.27-3ubuntu2.5 [315 kB]
    worker2: Get:10 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpgsm amd64 2.2.27-3ubuntu2.5 [197 kB]
    worker2: Get:11 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 gpgv amd64 2.2.27-3ubuntu2.5 [137 kB]
    worker2: Get:12 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 ca-certificates all 20240203~22.04.1 [162 kB]
    worker2: Get:13 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 wget amd64 1.21.2-2ubuntu1.1 [339 kB]
    worker2: Get:14 https://mirrors.edge.kernel.org/ubuntu jammy-updates/universe amd64 apt-transport-https all 2.4.14 [1,510 B]
    worker2: Get:15 https://mirrors.edge.kernel.org/ubuntu jammy/main amd64 conntrack amd64 1:1.4.6-2build2 [33.5 kB]
    worker2: Get:16 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 curl amd64 7.81.0-1ubuntu1.23 [194 kB]
    worker2: Get:17 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 libcurl4 amd64 7.81.0-1ubuntu1.23 [290 kB]
    worker2: Get:18 https://mirrors.edge.kernel.org/ubuntu jammy-updates/main amd64 net-tools amd64 1.60+git20181103.0eebece-1ubuntu5.4 [204 kB]
    worker2: Get:19 https://mirrors.edge.kernel.org/ubuntu jammy/main amd64 socat amd64 1.7.4.1-3ubuntu4 [349 kB]
    worker2: dpkg-preconfigure: unable to re-open stdin: No such file or directory
    worker2: Fetched 3,821 kB in 43s (87.9 kB/s)
(Reading database ... 76032 files and directories currently installed.)
    worker2: Preparing to unpack .../00-gpg-wks-client_2.2.27-3ubuntu2.5_amd64.deb ...
    worker2: Unpacking gpg-wks-client (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker2: Preparing to unpack .../01-dirmngr_2.2.27-3ubuntu2.5_amd64.deb ...
    worker2: Unpacking dirmngr (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker2: Preparing to unpack .../02-gpg-wks-server_2.2.27-3ubuntu2.5_amd64.deb ...
    worker2: Unpacking gpg-wks-server (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker2: Preparing to unpack .../03-gnupg-utils_2.2.27-3ubuntu2.5_amd64.deb ...
    worker2: Unpacking gnupg-utils (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker2: Preparing to unpack .../04-gpg-agent_2.2.27-3ubuntu2.5_amd64.deb ...
    worker2: Unpacking gpg-agent (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker2: Preparing to unpack .../05-gpg_2.2.27-3ubuntu2.5_amd64.deb ...
    worker2: Unpacking gpg (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker2: Preparing to unpack .../06-gpgconf_2.2.27-3ubuntu2.5_amd64.deb ...
    worker2: Unpacking gpgconf (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker2: Preparing to unpack .../07-gnupg-l10n_2.2.27-3ubuntu2.5_all.deb ...
    worker2: Unpacking gnupg-l10n (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker2: Preparing to unpack .../08-gnupg_2.2.27-3ubuntu2.5_all.deb ...
    worker2: Unpacking gnupg (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker2: Preparing to unpack .../09-gpgsm_2.2.27-3ubuntu2.5_amd64.deb ...
    worker2: Unpacking gpgsm (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker2: Preparing to unpack .../10-gpgv_2.2.27-3ubuntu2.5_amd64.deb ...
    worker2: Unpacking gpgv (2.2.27-3ubuntu2.5) over (2.2.27-3ubuntu2.1) ...
    worker2: Setting up gpgv (2.2.27-3ubuntu2.5) ...
(Reading database ... 76032 files and directories currently installed.)
    worker2: Preparing to unpack .../0-ca-certificates_20240203~22.04.1_all.deb ...
    worker2: Unpacking ca-certificates (20240203~22.04.1) over (20230311ubuntu0.22.04.1) ...
    worker2: Preparing to unpack .../1-wget_1.21.2-2ubuntu1.1_amd64.deb ...
    worker2: Unpacking wget (1.21.2-2ubuntu1.1) over (1.21.2-2ubuntu1) ...
    worker2: Selecting previously unselected package apt-transport-https.
    worker2: Preparing to unpack .../2-apt-transport-https_2.4.14_all.deb ...
    worker2: Unpacking apt-transport-https (2.4.14) ...
    worker2: Selecting previously unselected package conntrack.
    worker2: Preparing to unpack .../3-conntrack_1%3a1.4.6-2build2_amd64.deb ...
    worker2: Unpacking conntrack (1:1.4.6-2build2) ...
    worker2: Preparing to unpack .../4-curl_7.81.0-1ubuntu1.23_amd64.deb ...
    worker2: Unpacking curl (7.81.0-1ubuntu1.23) over (7.81.0-1ubuntu1.13) ...
    worker2: Preparing to unpack .../5-libcurl4_7.81.0-1ubuntu1.23_amd64.deb ...
    worker2: Unpacking libcurl4:amd64 (7.81.0-1ubuntu1.23) over (7.81.0-1ubuntu1.13) ...
    worker2: Selecting previously unselected package net-tools.
    worker2: Preparing to unpack .../6-net-tools_1.60+git20181103.0eebece-1ubuntu5.4_amd64.deb ...
    worker2: Unpacking net-tools (1.60+git20181103.0eebece-1ubuntu5.4) ...
    worker2: Selecting previously unselected package socat.
    worker2: Preparing to unpack .../7-socat_1.7.4.1-3ubuntu4_amd64.deb ...
    worker2: Unpacking socat (1.7.4.1-3ubuntu4) ...
    worker2: Setting up net-tools (1.60+git20181103.0eebece-1ubuntu5.4) ...
    worker2: Setting up wget (1.21.2-2ubuntu1.1) ...
    worker2: Setting up apt-transport-https (2.4.14) ...
    worker2: Setting up conntrack (1:1.4.6-2build2) ...
    worker2: Setting up ca-certificates (20240203~22.04.1) ...
    worker2: Updating certificates in /etc/ssl/certs...
    worker2: rehash: warning: skipping ca-certificates.crt,it does not contain exactly one certificate or CRL
    worker2: 14 added, 5 removed; done.
    worker2: Setting up gnupg-l10n (2.2.27-3ubuntu2.5) ...
    worker2: Setting up socat (1.7.4.1-3ubuntu4) ...
    worker2: Setting up gpgconf (2.2.27-3ubuntu2.5) ...
    worker2: Setting up libcurl4:amd64 (7.81.0-1ubuntu1.23) ...
    worker2: Setting up curl (7.81.0-1ubuntu1.23) ...
    worker2: Setting up gpg (2.2.27-3ubuntu2.5) ...
    worker2: Setting up gnupg-utils (2.2.27-3ubuntu2.5) ...
    worker2: Setting up gpg-agent (2.2.27-3ubuntu2.5) ...
    worker2: Setting up gpgsm (2.2.27-3ubuntu2.5) ...
    worker2: Setting up dirmngr (2.2.27-3ubuntu2.5) ...
    worker2: Setting up gpg-wks-server (2.2.27-3ubuntu2.5) ...
    worker2: Setting up gpg-wks-client (2.2.27-3ubuntu2.5) ...
    worker2: Setting up gnupg (2.2.27-3ubuntu2.5) ...
    worker2: Processing triggers for libc-bin (2.35-0ubuntu3.3) ...
    worker2: Processing triggers for man-db (2.10.2-1) ...
    worker2: Processing triggers for install-info (6.8-4build1) ...
    worker2: Processing triggers for ca-certificates (20240203~22.04.1) ...
    worker2: Updating certificates in /etc/ssl/certs...
    worker2: 0 added, 0 removed; done.
    worker2: Running hooks in /etc/ca-certificates/update.d...
    worker2: done.
    worker2:
    worker2: Running kernel seems to be up-to-date.
    worker2:
    worker2: No services need to be restarted.
    worker2:
    worker2: No containers need to be restarted.
    worker2:
    worker2: No user sessions are running outdated binaries.
    worker2:
    worker2: No VM guests are running outdated hypervisor (qemu) binaries on this host.
    worker2: ++ VERSION=1.7.24
    worker2: ++ wget -q https://github.com/containerd/containerd/releases/download/v1.7.24/containerd-1.7.24-linux-amd64.tar.gz
    worker2: ++ tar Cxzvf /usr/local containerd-1.7.24-linux-amd64.tar.gz
    worker2: bin/
    worker2: bin/ctr
    worker2: bin/containerd
    worker2: bin/containerd-shim
    worker2: bin/containerd-shim-runc-v1
    worker2: bin/containerd-stress
    worker2: bin/containerd-shim-runc-v2
    worker2: ++ mkdir -p /usr/local/lib/systemd/system
    worker2: ++ wget -q -P /usr/local/lib/systemd/system https://raw.githubusercontent.com/containerd/containerd/main/containerd.service
    worker2: ++ systemctl daemon-reload
    worker2: ++ systemctl enable --now containerd
    worker2: Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /usr/local/lib/systemd/system/containerd.service.
    worker2: ++ RUNC=v1.2.2
    worker2: ++ wget -q https://github.com/opencontainers/runc/releases/download/v1.2.2/runc.amd64
    worker2: ++ install -m 755 runc.amd64 /usr/local/sbin/runc
    worker2: ++ CNI=v1.6.0
    worker2: ++ mkdir -p /opt/cni/bin
    worker2: ++ wget -q https://github.com/containernetworking/plugins/releases/download/v1.6.0/cni-plugins-linux-amd64-v1.6.0.tgz
    worker2: ++ tar Cxzvf /opt/cni/bin cni-plugins-linux-amd64-v1.6.0.tgz
    worker2: ./
    worker2: ./vrf
    worker2: ./firewall
    worker2: ./LICENSE
    worker2: ./macvlan
    worker2: ./static
    worker2: ./host-device
    worker2: ./host-local
    worker2: ./loopback
    worker2: ./sbr
    worker2: ./tuning
    worker2: ./bridge
    worker2: ./README.md
    worker2: ./ptp
    worker2: ./bandwidth
    worker2: ./vlan
    worker2: ./portmap
    worker2: ./ipvlan
    worker2: ./dummy
    worker2: ./tap
    worker2: ./dhcp
    worker2: ++ mkdir -p /etc/containerd
    worker2: ++ containerd config default
    worker2: ++ sed -i 's/SystemdCgroup = false/SystemdCgroup = true/' /etc/containerd/config.toml
    worker2: ++ sed -i 's|sandbox_image = "registry.k8s.io/pause:3.8"|sandbox_image = "registry.k8s.io/pause:3.9"|' /etc/containerd/config.toml
    worker2: ++ systemctl restart containerd
    worker2: ++ tee /etc/modules-load.d/k8s.conf
    worker2: ++ cat
    worker2: overlay
    worker2: br_netfilter
    worker2: ++ modprobe overlay
    worker2: ++ modprobe br_netfilter
    worker2: ++ cat
    worker2: ++ tee /etc/sysctl.d/k8s.conf
    worker2: net.bridge.bridge-nf-call-iptables=1
    worker2: net.bridge.bridge-nf-call-ip6tables=1
    worker2: net.ipv4.ip_forward=1
    worker2: ++ sysctl --system
    worker2: * Applying /etc/sysctl.d/10-console-messages.conf ...
    worker2: kernel.printk = 4 4 1 7
    worker2: * Applying /etc/sysctl.d/10-ipv6-privacy.conf ...
    worker2: net.ipv6.conf.all.use_tempaddr = 2
    worker2: net.ipv6.conf.default.use_tempaddr = 2
    worker2: * Applying /etc/sysctl.d/10-kernel-hardening.conf ...
    worker2: kernel.kptr_restrict = 1
    worker2: * Applying /etc/sysctl.d/10-magic-sysrq.conf ...
    worker2: kernel.sysrq = 176
    worker2: * Applying /etc/sysctl.d/10-network-security.conf ...
    worker2: net.ipv4.conf.default.rp_filter = 2
    worker2: net.ipv4.conf.all.rp_filter = 2
    worker2: * Applying /etc/sysctl.d/10-ptrace.conf ...
    worker2: kernel.yama.ptrace_scope = 1
    worker2: * Applying /etc/sysctl.d/10-zeropage.conf ...
    worker2: vm.mmap_min_addr = 65536
    worker2: * Applying /usr/lib/sysctl.d/50-default.conf ...
    worker2: kernel.core_uses_pid = 1
    worker2: net.ipv4.conf.default.rp_filter = 2
    worker2: net.ipv4.conf.default.accept_source_route = 0
    worker2: sysctl: setting key "net.ipv4.conf.all.accept_source_route": Invalid argument
    worker2: net.ipv4.conf.default.promote_secondaries = 1
    worker2: sysctl: setting key "net.ipv4.conf.all.promote_secondaries": Invalid argument
    worker2: net.ipv4.ping_group_range = 0 2147483647
    worker2: net.core.default_qdisc = fq_codel
    worker2: fs.protected_hardlinks = 1
    worker2: fs.protected_symlinks = 1
    worker2: fs.protected_regular = 1
    worker2: fs.protected_fifos = 1
    worker2: * Applying /usr/lib/sysctl.d/50-pid-max.conf ...
    worker2: kernel.pid_max = 4194304
    worker2: * Applying /usr/lib/sysctl.d/99-protect-links.conf ...
    worker2: fs.protected_fifos = 1
    worker2: fs.protected_hardlinks = 1
    worker2: fs.protected_regular = 2
    worker2: fs.protected_symlinks = 1
    worker2: * Applying /etc/sysctl.d/99-sysctl.conf ...
    worker2: net.ipv6.conf.all.disable_ipv6 = 1
    worker2: * Applying /etc/sysctl.d/k8s.conf ...
    worker2: net.bridge.bridge-nf-call-iptables = 1
    worker2: net.bridge.bridge-nf-call-ip6tables = 1
    worker2: net.ipv4.ip_forward = 1
    worker2: * Applying /etc/sysctl.conf ...
    worker2: net.ipv6.conf.all.disable_ipv6 = 1
    worker2: ++ curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.30/deb/Release.key
    worker2: ++ gpg --dearmor -o /etc/apt/trusted.gpg.d/k8s.gpg
    worker2: ++ echo 'deb [signed-by=/etc/apt/trusted.gpg.d/k8s.gpg] https://pkgs.k8s.io/core:/stable:/v1.30/deb/ /'
    worker2: ++ apt-get update
    worker2: Hit:2 https://mirrors.edge.kernel.org/ubuntu jammy InRelease
    worker2: Hit:3 https://mirrors.edge.kernel.org/ubuntu jammy-updates InRelease
    worker2: Hit:4 https://mirrors.edge.kernel.org/ubuntu jammy-backports InRelease
    worker2: Hit:5 https://mirrors.edge.kernel.org/ubuntu jammy-security InRelease
    worker2: Get:1 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  InRelease [1,192 B]
    worker2: Get:6 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  Packages [20.3 kB]
    worker2: Fetched 21.5 kB in 11s (1,895 B/s)
    worker2: Reading package lists...
    worker2: ++ apt-get install -y kubelet kubeadm kubectl
    worker2: Reading package lists...
    worker2: Building dependency tree...
    worker2: Reading state information...
    worker2: The following additional packages will be installed:
    worker2:   cri-tools kubernetes-cni
    worker2: The following NEW packages will be installed:
    worker2:   cri-tools kubeadm kubectl kubelet kubernetes-cni
    worker2: 0 upgraded, 5 newly installed, 0 to remove and 252 not upgraded.
    worker2: Need to get 93.7 MB of archives.
    worker2: After this operation, 343 MB of additional disk space will be used.
    worker2: Get:1 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  cri-tools 1.30.1-1.1 [21.3 MB]
    worker2: Get:2 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  kubeadm 1.30.14-1.1 [10.5 MB]
    worker2: Get:3 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  kubectl 1.30.14-1.1 [10.9 MB]
    worker2: Get:4 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  kubernetes-cni 1.4.0-1.1 [32.9 MB]
    worker2: Get:5 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.30/deb  kubelet 1.30.14-1.1 [18.2 MB]
    worker2: dpkg-preconfigure: unable to re-open stdin: No such file or directory
    worker2: Fetched 93.7 MB in 10min 1s (156 kB/s)
    worker2: Selecting previously unselected package cri-tools.
(Reading database ... 76139 files and directories currently installed.)
    worker2: Preparing to unpack .../cri-tools_1.30.1-1.1_amd64.deb ...
    worker2: Unpacking cri-tools (1.30.1-1.1) ...
    worker2: Selecting previously unselected package kubeadm.
    worker2: Preparing to unpack .../kubeadm_1.30.14-1.1_amd64.deb ...
    worker2: Unpacking kubeadm (1.30.14-1.1) ...
    worker2: Selecting previously unselected package kubectl.
    worker2: Preparing to unpack .../kubectl_1.30.14-1.1_amd64.deb ...
    worker2: Unpacking kubectl (1.30.14-1.1) ...
    worker2: Selecting previously unselected package kubernetes-cni.
    worker2: Preparing to unpack .../kubernetes-cni_1.4.0-1.1_amd64.deb ...
    worker2: Unpacking kubernetes-cni (1.4.0-1.1) ...
    worker2: Selecting previously unselected package kubelet.
    worker2: Preparing to unpack .../kubelet_1.30.14-1.1_amd64.deb ...
    worker2: Unpacking kubelet (1.30.14-1.1) ...
    worker2: Setting up kubectl (1.30.14-1.1) ...
    worker2: Setting up cri-tools (1.30.1-1.1) ...
    worker2: Setting up kubernetes-cni (1.4.0-1.1) ...
    worker2: Setting up kubeadm (1.30.14-1.1) ...
    worker2: Setting up kubelet (1.30.14-1.1) ...
    worker2:
    worker2: Running kernel seems to be up-to-date.
    worker2:
    worker2: No services need to be restarted.
    worker2:
    worker2: No containers need to be restarted.
    worker2:
    worker2: No user sessions are running outdated binaries.
    worker2:
    worker2: No VM guests are running outdated hypervisor (qemu) binaries on this host.
    worker2: ++ apt-mark hold kubelet kubeadm kubectl
    worker2: kubelet set on hold.
    worker2: kubeadm set on hold.
    worker2: kubectl set on hold.
    worker2: ++ mkdir -p /etc/default
    worker2: ++ echo KUBELET_EXTRA_ARGS=--node-ip=192.168.56.26
    worker2: ++ systemctl enable kubelet
    worker2: ++ kubeadm config images pull
    worker2: I0402 18:56:37.637628    7965 version.go:256] remote version is much newer: v1.35.3; falling back to: stable-1.30
    worker2: [config/images] Pulled registry.k8s.io/kube-apiserver:v1.30.14
    worker2: [config/images] Pulled registry.k8s.io/kube-controller-manager:v1.30.14
    worker2: [config/images] Pulled registry.k8s.io/kube-scheduler:v1.30.14
    worker2: [config/images] Pulled registry.k8s.io/kube-proxy:v1.30.14
    worker2: [config/images] Pulled registry.k8s.io/coredns/coredns:v1.11.3
    worker2: [config/images] Pulled registry.k8s.io/pause:3.9
    worker2: [config/images] Pulled registry.k8s.io/etcd:3.5.15-0
==> worker2: Running provisioner: shell...
    worker2: Running: inline script
    worker2: ++ for i in {1..30}
    worker2: ++ '[' -f /vagrant/join.sh ']'
    worker2: ++ break
    worker2: ++ '[' -f /vagrant/join.sh ']'
    worker2: ++ bash /vagrant/join.sh --cri-socket unix:///run/containerd/containerd.sock
    worker2: [preflight] Running pre-flight checks
    worker2: [preflight] Reading configuration from the cluster...
    worker2: [preflight] FYI: You can look at this config file with 'kubectl -n kube-system get cm kubeadm-config -o yaml'
    worker2: [kubelet-start] Writing kubelet configuration to file "/var/lib/kubelet/config.yaml"
    worker2: [kubelet-start] Writing kubelet environment file with flags to file "/var/lib/kubelet/kubeadm-flags.env"
    worker2: [kubelet-start] Starting the kubelet
    worker2: [kubelet-check] Waiting for a healthy kubelet at http://127.0.0.1:10248/healthz. This can take up to 4m0s
    worker2: [kubelet-check] The kubelet is healthy after 2.003776686s
    worker2: [kubelet-start] Waiting for the kubelet to perform the TLS Bootstrap
    worker2:
    worker2: This node has joined the cluster:
    worker2: * Certificate signing request was sent to apiserver and a response was received.
    worker2: * The Kubelet was informed of the new secure connection details.
    worker2:
    worker2: Run 'kubectl get nodes' on the control-plane to see this node join the cluster.
    worker2:

Windows@AaaDee MINGW64 ~/k8s (master)
$ date
Fri Apr  3 01:00:30 IST 2026

Windows@AaaDee MINGW64 ~/k8s (master)
$
