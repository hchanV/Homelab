# Hardware Configuration

Last updated: 2026-05-14

---

# System Identity
# Pulled with hostnamectl

Hostname: pxve-main

System Manufacturer: Lenovo

System Model: ThinkStation P720 

# For motherboard dmidecode -t baseboard
Motherboard Manufacturer: Lenovo

Motherboard Model: SDK0Q40104 3305666913227

BIOS Vendor: Lenovo 

BIOS Version: S04KT65A

BIOS Release Date: 2023-4-20  

---

# CPU
# Pulled with lscpu

Model: Intel(R) Xeon(R) Silver 4110 CPU @ 2.10GHz

Cores: 32 

Threads: 2 per core

Virtualization Support:VT-x

---

# Memory
# Pulled with free -h

Total RAM: 46 GB

RAM Type: DDR4

RAM Speed: 2600-3000 MT/S
- 
Available Slots: 8?

---

# Storage
# lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINTS,MODEL
## Proxmox Boot Drive

Device:
- /dev/nvme0n1

Model:
- WDC PC SN730 SDBQNTY-512G-1001

Capacity:
- 476.9G

Filesystem:
- LVM

Purpose:
- Proxmox host

---

## Secondary NVMe

Device:
- /dev/nvme1n1

Model:
- SAMSUNG MZVKW512HMJP-000L7

Capacity:
- 476.9G

Filesystem:
- NTFS

Purpose:
- Previous Windows install / candidate for reuse

---

## HDD

Device:
- /dev/sda

Model:
- ST2000DM006-2DM164

Capacity:
- 1.8T

Filesystem:
- NTFS

Purpose:
- Candidate for storage pool

---

# PCI Devices
#lspci | grep -i vga
GPU: NVIDIA Corporation GP107GL [Quadro P1000] (rev a1)
 
# lspci | grep -i ethernet
Primary NIC: 
00:1f.6 Ethernet controller: how Intel Corporation Ethernet Connection (3) I219-LM (rev 09)
04:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03) 

Additional Devices:

---

# Notes / Discovery Process

## Commands Used

```bash
hostnamectl
lscpu
free -h
dmidecode -t memory
dmidecode -t baseboard
dmidecode -t bios
lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINTS,MODEL
lspci
```

## Discovery Notes

- Initial hardware inventory performed after Proxmox installation
- Windows drive identified via NTFS partitions
- Proxmox boot drive confirmed via LVM partitions
- Additional storage identified for future ZFS planning 