# Server Specifications

05-11-2026

Found a bunch of information through proxmox on my hardware specs and general network config below is how and what. 
Below will also be sorted into a hardware/network configuration document


# System Identity
Was gathered through the Proxmox web UI and shell commands

Proxmox web UI:

```text
Node → Summary
Node → System → Network
Node → Disks
```

Proxmox shell:

```bash
hostnamectl
lscpu
free -h
dmidecode -t memory
dmidecode -t baseboard
dmidecode -t bios
ip a
ip route
cat /etc/resolv.conf
lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINTS,MODEL
lspci
```

Notes:
- Initial hardware inventory performed after Proxmox installation
- Network settings verified before creating first VMs

---

# System Identity

Hostname:
- __________________

Command used:

```bash
hostnamectl
```

Notes:
- Proxmox host identity

---

# CPU

## How found
Proxmox shell:

```bash
lscpu
```

Manufacturer:
- __________________

Model:
- __________________

Architecture:
- __________________

Cores:
- __________________

Threads:
- __________________

Virtualization:
- __________________

Notes:
- Hardware virtualization should be enabled for VM hosting

---

# Memory

## How found
Proxmox shell:

```bash
free -h
dmidecode -t memory
```

Total RAM:
- __________________

RAM Type:
- __________________

Speed:
- __________________

DIMM layout:
- __________________

ECC:
- __________________

Notes:
- Confirm available memory for future VM allocation

---

# Motherboard

## How found
Proxmox shell:

```bash
dmidecode -t baseboard
```

Manufacturer:
- __________________

Model:
- __________________

Version:
- __________________

Notes:
- Useful for BIOS updates and expansion planning

---

# BIOS / Firmware

## How found
Proxmox shell:

```bash
dmidecode -t bios
```

Vendor:
- __________________

Version:
- __________________

Release Date:
- __________________

UEFI:
- [ ] Yes
- [ ] No

Notes:
- Proxmox installed in UEFI mode if `/boot/efi` exists

---

# Network Interfaces

## How found
Proxmox shell:

```bash
ip a
```

## Management Interface

Interface:
- vmbr0

Bridge:
- vmbr0

Physical NIC:
- nic0

MAC Address:
- 70:20:84:09:85:f6

IP Address:
- 10.0.0.64

CIDR:
- /24

Notes:
- Proxmox uses a Linux bridge (`vmbr0`) for host + VM networking

## Additional Interfaces

Unused interfaces discovered:
- nic1
- wlp94s0

Notes:
- Secondary NIC and Wi-Fi currently unused

---

# Network Configuration

## How found
Proxmox shell:

```bash
ip route
cat /etc/resolv.conf
```

Subnet:
- 10.0.0.0/24

Host IP:
- 10.0.0.64

Gateway:
- 10.0.0.1

DNS Server:
- 75.75.75.75

Search Domain:
- hyperverse.arpa

Notes:
- Current DNS provided by ISP
- May switch to router DNS or Pi-hole later

---

# Storage Devices

## How found
Proxmox shell:

```bash
lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINTS,MODEL
```

## Boot Drive

Device:
- /dev/nvme0n1

Model:
- WDC PC SN730 SDBQNTY-512G-1001

Capacity:
- 476.9G

Filesystem:
- LVM

Notes:
- Proxmox host drive
- DO NOT WIPE

## Windows Drive

Device:
- /dev/nvme1n1

Model:
- SAMSUNG MZVKW512HMJP-000L7

Capacity:
- 476.9G

Filesystem:
- NTFS

Notes:
- Previous Windows installation
- Candidate for wipe/reuse

## Additional Storage

Device:
- /dev/sda

Model:
- ST2000DM006-2DM164

Capacity:
- 1.8T

Filesystem:
- NTFS

Notes:
- Storage drive
- Evaluate for ZFS or passthrough

---

# Planned Roles

- [x] Proxmox host
- [ ] File server
- [ ] Media server
- [ ] Print server
- [ ] Camera/security
- [ ] Password manager
- [ ] Pi-hole / DNS
- [ ] Backup server

---

# Issues / Observations

## Issue 1

Problem:
- Proxmox not appearing as boot option

Root cause:
- Windows drive had boot priority

Fix:
- Wiped Windows drive

---

## Issue 2

Problem:
- Needed to identify safe disk for wiping

Fix:
- Used `lsblk` to identify Windows partitions (`NTFS`)

Result:
- Confirmed `/dev/nvme1n1` is safe to repurpose

---

# Next Steps

- [ ] Reserve `10.0.0.64` in router DHCP
- [ ] Decide on static IP strategy
- [ ] Decide ZFS pool layout
- [ ] Create first file server VM