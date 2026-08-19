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

---

## Project 4: Inter-VLAN Routing (Router-on-a-Stick)

Connected a router to the VLAN-segmented switch from Project 3, allowing devices in different VLANs to communicate with each other through a single physical link — a setup known as "router-on-a-stick."

### What I did
- Connected a router to the switch using a single physical link
- Configured the switch port facing the router as a trunk, allowing multiple VLANs to travel over that one connection
- Created a subinterface on the router for each VLAN (G0/0.2, G0/0.3, G0/0.4), each tagged with 802.1Q encapsulation matching its VLAN
- Assigned each subinterface an IP address acting as the default gateway for that VLAN
- Set static IPs and matching default gateways on each PC based on their VLAN
- Verified all interfaces were up using `show ip interface brief`
- Tested and confirmed successful ping between PCs in different VLANs

### Tools used
- Cisco Packet Tracer
- Router CLI (IOS commands)

### What I learned
- How a single physical link can carry multiple VLANs using trunking and 802.1Q tagging
- How router subinterfaces act as separate logical gateways for each VLAN, despite sharing one physical interface
- The full path traffic takes between VLANs: PC → gateway (subinterface) → router → destination VLAN's subinterface → destination PC
- How to troubleshoot systematically using `show ip interface brief` to isolate configuration issues rather than guessing
- That a single dropped packet on the very first ping attempt between two devices is normal (ARP resolution), not a fault
- This concept took real effort to click — had to rebuild the mental model from scratch before the configuration actually worked, which reinforced the "why" behind each command rather than just memorizing syntax

### Screenshots

<img width="1358" height="555" alt="Screenshot_2026-08-16_16-43-43" src="https://github.com/user-attachments/assets/6be6df4e-9cd8-49f0-ac7a-497d3eb7310d" />
<img width="1366" height="733" alt="Screenshot_2026-08-16_16-45-39" src="https://github.com/user-attachments/assets/9f392bed-f2f7-4ea4-8b3f-caebed51a297" />
<img width="1366" height="277" alt="Screenshot_2026-08-16_16-44-05" src="https://github.com/user-attachments/assets/474ad379-2069-4041-bbe7-fadee34df094" />
<img width="753" height="650" alt="Screenshot_2026-08-16_16-44-38" src="https://github.com/user-attachments/assets/420b4c8d-698e-429d-b2a3-400fb70d477f" />

--

## Project 5: Multi-Site Network with Static Routing

Connected 3 separate site networks (simulating different company office locations) using routers linked in a triangle topology, with manually configured static routes allowing full communication between all sites.

### What I did
- Built 3 separate LAN sites, each with its own switch and PC
- Connected 3 routers in a triangle topology using serial links, with each link on its own dedicated subnet
- Configured static routes on each router to reach the other two sites' LAN networks
- Verified connectivity at each stage — router-to-router first, then full end-to-end PC-to-PC across all sites

### Tools used
- Cisco Packet Tracer
- Router CLI (IOS commands)

### What I learned
- The critical difference between a destination network address, a next-hop IP, and a device IP — mixing these up was the root cause of a multi-day troubleshooting struggle
- How static routes work: telling a router "to reach this network, send traffic to this neighbor" rather than the router discovering it automatically
- The importance of testing incrementally — confirming direct router-to-router connectivity before layering static routes on top, rather than testing everything at once
- Real persistence in troubleshooting — this project took several days longer than expected due to one small misconfiguration, and getting through it taught more than a smooth build would have

### Screenshots

<img width="1364" height="558" alt="Screenshot_2026-08-19_00-07-36" src="https://github.com/user-attachments/assets/81606088-a767-4b8b-bb45-600032594273" />
<img width="1366" height="216" alt="Screenshot_2026-08-19_00-17-45" src="https://github.com/user-attachments/assets/4dedb297-5de2-4f71-8c15-302c1fb783b7" />
<img width="1366" height="734" alt="Screenshot_2026-08-19_00-16-51" src="https://github.com/user-attachments/assets/9c4823d8-84a2-42a0-b96e-e90f581aa6b7" />
<img width="700" height="604" alt="Screenshot_2026-08-18_23-59-32" src="https://github.com/user-attachments/assets/90d51273-f131-4dd2-b04d-024dce88fcad" />

---

## Project 6: DHCP + DNS Server Setup

Configured a dedicated server device to provide both DHCP and DNS services to a LAN, replacing router-based DHCP with a more realistic dedicated-server setup, and adding name resolution on top.

### What I did
- Added a Server device to the LAN with a static IP
- Configured and enabled a DHCP pool on the server, correctly excluding the server's own address after initially misconfiguring the pool to include itself
- Enabled DNS services on the same server
- Added a DNS record mapping a hostname to an IP address
- Set PCs to obtain IP addresses automatically via DHCP
- Tested name resolution by pinging a hostname instead of an IP, confirming DNS correctly resolved to the target address

### Tools used
- Cisco Packet Tracer

### What I learned
- DHCP and DNS are commonly run together on the same server in real small-to-medium networks, not necessarily separated
- A DHCP server's address pool must exclude its own IP, otherwise it can end up trying to hand out its own address
- The difference between a DNS resolution failure and a reachability failure — a "destination unreachable" result with the correct IP showing means DNS worked, the issue is routing/connectivity, not name resolution
- Servers need a static IP themselves before they can reliably serve DHCP/DNS to other devices

### Screenshots

<img width="1366" height="701" alt="Screenshot_2026-08-19_23-53-26" src="https://github.com/user-attachments/assets/81fd8420-90df-4d53-9a73-1704f646af9c" />
<img width="1366" height="736" alt="Screenshot_2026-08-19_23-50-52" src="https://github.com/user-attachments/assets/032f6077-dc23-4249-9986-5667061f532a" />
<img width="1366" height="733" alt="Screenshot_2026-08-19_23-51-05" src="https://github.com/user-attachments/assets/e535970c-b1a2-4a83-8fc0-9e0c3386d740" />
<img width="1366" height="736" alt="Screenshot_2026-08-19_23-53-08" src="https://github.com/user-attachments/assets/de502c06-cef6-49ca-b51b-6bf5740530f7" />

