# packet-tracer-projects
A collection of my projects around Networking and how a navigate around setting up systems and maintaining them from one small network to a corporate sized network.


## Project 1: Two PCs, One Switch (with Router)

Basic Layer 2 connectivity test — proving devices on the same LAN can communicate through a switch, extended with a router to test Layer 3 reachability as well.

### What I did
- Connected 2 PCs to a switch, with a router also attached to the topology
- Assigned static IPs to each PC and the router interface, all on the same subnet (192.168.1.0/24)
- Tested connectivity between PC0, PC1, and the router using ping
- Confirmed all pings successful

### Tools used
- Cisco Packet Tracer

### What I learned
- How basic switch connectivity works at Layer 2
- How to verify reachability using ping and the PDU list simulation tool
- Static IP configuration fundamentals

<img width="1366" height="156" alt="Screenshot_2026-08-13_14-59-18" src="https://github.com/user-attachments/assets/eb1b19d6-f2a0-4198-99ca-a8261477f5e2" />
<img width="1366" height="699" alt="Screenshot_2026-08-13_15-05-48" src="https://github.com/user-attachments/assets/fce9cd97-2c1f-4dba-9c33-336a5bcfc112" />

---

## Project 2: Basic LAN with DHCP

Configured a router to automatically assign IP addresses to devices on the network, instead of manual static configuration.

### What I did
- Configured a DHCP pool on a Cisco 1941 router via CLI (no GUI DHCP option exists on routers in Packet Tracer — only on dedicated server devices)
- Set the default gateway, DNS server, and address range for the pool
- Excluded the router's own address from the DHCP range
- Set PCs to obtain IP addresses automatically and confirmed successful address assignment

### Tools used
- Cisco Packet Tracer
- Router CLI (IOS commands)

### What I learned
- DHCP isn't configurable via GUI on Cisco routers in Packet Tracer — it requires CLI, which gave early exposure to IOS command syntax
- How a DHCP pool, default gateway, and exclusions work together
- First hands-on CLI experience on a Cisco device

<img width="1366" height="701" alt="Screenshot_2026-08-13_15-15-14" src="https://github.com/user-attachments/assets/e8c1bcfb-1364-4fa0-8278-e8006af71cd1" />
<img width="835" height="713" alt="Screenshot_2026-08-13_15-15-36" src="https://github.com/user-attachments/assets/7a557a7b-0e88-4bb4-9ede-a8864f817a1e" />
<img width="839" height="712" alt="Screenshot_2026-08-13_15-15-59" src="https://github.com/user-attachments/assets/fefc4843-ab1d-4052-8224-50eb6af244b5" />
<img width="1364" height="176" alt="Screenshot_2026-08-13_15-17-27" src="https://github.com/user-attachments/assets/b2b7a181-f8a7-4ce2-bc02-a80bb69981c5" />

---

## Project 3: VLAN Segmentation

Built a switched network with 3 separate VLANs to demonstrate Layer 2 network isolation between departments.

### What I did
- Created 3 VLANs on a switch and assigned each a distinct subnet (192.168.2.0, 192.168.3.0, 192.168.4.0)
- Assigned switch ports to their respective VLANs in access mode
- Assigned static IPs to PCs based on their VLAN
- Tested connectivity within and across VLANs using ping and the PDU list tool

### Tools used
- Cisco Packet Tracer

### What I learned
- How VLANs isolate traffic at Layer 2, even when devices are on the same physical switch
- The difference between access mode (single VLAN, device-facing) and trunk mode (multiple VLANs, switch-to-switch/router links)
- That a failed cross-VLAN ping is expected proof the segmentation is working correctly, not a mistake
- Devices in the same VLAN communicate normally; devices in different VLANs are fully isolated until inter-VLAN routing is configured (next project)

<img width="1366" height="700" alt="Screenshot_2026-08-13_14-54-54" src="https://github.com/user-attachments/assets/9e66cef9-ff0c-423d-9db3-207f2f0b0fe8" />
<img width="1366" height="211" alt="Screenshot_2026-08-13_14-55-34" src="https://github.com/user-attachments/assets/e8440a1e-b3c1-4528-99f6-a9895ce2bdfd" />
<img width="840" height="717" alt="Screenshot_2026-08-13_14-56-28" src="https://github.com/user-attachments/assets/3bed2a54-3ffc-4127-877e-c3fdd38f27d9" />
