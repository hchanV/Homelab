# Proxmox Install Notes

## Date
- Install date: 2026-05-05

## What I did today
- Created a Proxmox VE USB installer using Rufus.
- Booted the big server from the USB drive.
- Started the Proxmox graphical installer.
- Chose `ext4` for the Proxmox boot filesystem.
- Configured the Proxmox management network.
- Installed Proxmox onto the big server.
- Rebooted after installation.
- Confirmed the server can reach the Proxmox web UI.
- Logged into the Proxmox web interface from my Windows computer.

## Current Proxmox access
- Web UI URL: https://10.0.0.64:8006
- Login user: root
- Realm: Linux PAM standard authentication
- Hostname: pve-main.home.arpa
- Gateway: 10.0.0.1
- DNS server: 75.75.75.75

## Install decisions

### Why Proxmox
I chose Proxmox because I want a central server to run multiple services separately using VMs and containers.

Planned services include:
- File server
- Print server
- Media server
- Security/camera system
- Self-hosted password manager
- Other future homelab services

Using Proxmox should make it easier to keep services isolated, back them up, restore them, and experiment without breaking everything at once.

### Why ext4 for the Proxmox boot drive
I chose `ext4` for the Proxmox boot drive because this is my first Proxmox install and I wanted a simple reliable setup.

The plan is:
- Use `ext4` for the Proxmox operating system boot drive.
- Consider ZFS later for main storage drives.

### Why I did not choose mirrored boot yet
A mirrored Proxmox boot drive would help if one boot SSD dies, but it adds extra complexity.

For now, I am prioritizing:
- Simple install
- Learning basics
- Redundancy and increased infrastructure complexity later

## Current known configuration

### Main server
- Purpose: Primary Proxmox server
- RAM: Unknown
- CPU: Unknown
- Boot drive: Unknown
- Number of drives installed: Unknown
- Available storage space: Unknown
- Network interface used for Proxmox management: Unknown / needs verification

### Smaller server
- Purpose: Future backup server, Pi-hole, or lightweight services
- Specs: Unknown

## Things I still need to verify

### Hardware
- CPU model
- Total RAM
- Boot drive model and size
- Number of internal drives
- Drive types: SSD, HDD, NVMe
- Available storage space
- Network adapter model
- Whether any old Windows drive still exists

### Proxmox
- Confirm Proxmox boots automatically without needing manual boot menu selection.
- Confirm the management IP address is static/reserved.
- Confirm which disk Proxmox was installed on.
- Check available updates.
- Configure repositories later.
- Decide storage layout before creating important VMs.

## How to find these details next time

### From the Proxmox web UI
Check:
- Node name
- Summary page
- CPU
- Memory
- Storage
- Network interfaces
- Disks

### From the Proxmox shell
Useful commands to run later:

```bash
lscpu