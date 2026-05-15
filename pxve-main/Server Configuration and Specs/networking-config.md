# Network Configuration

Last updated: 2026-05-14

---

# Network Identity

Management Interface:
- vmbr0

Bridge Name:
- vmbr0

Physical NIC:
- nic0

MAC Address:
- 70:20:84:09:85:f6

IP Address:
- 10.0.0.64

CIDR:
- /24

Network Subnet:
- 10.0.0.0/24

Gateway:
- 10.0.0.1

DNS Server:
- 75.75.75.75

Search Domain:
- hyperverse.arpa

---

# Additional Interfaces

Secondary NIC:
- nic1 (down)

Wireless Adapter:
- wlp94s0 (down)

---

# Current Networking Decisions

DHCP Reservation:
- Pending

Static IP:
- Appears configured

Remote Access:
- Planned via VPN

Internal DNS:
- Planned later

---

# Notes / Discovery Process

## Commands Used

```bash
ip a
ip route
cat /etc/resolv.conf
cat /etc/network/interfaces
```

## Discovery Notes

- Proxmox management interface uses Linux bridge (`vmbr0`)
- Physical interface `nic0` attached to bridge
- Router/gateway identified as `10.0.0.1`
- Current DNS provided by ISP
- Secondary NIC and Wi-Fi adapter currently unused
- Proxmox networking confirmed operational