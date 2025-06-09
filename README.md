# Network Security Project

### Topology:
![pic2](https://github.com/user-attachments/assets/88d1db52-36de-4aaf-a2d6-40b7c647e647)


# This Project Contains :

## Note : 
    - All routers have the enable password set to: cisco12345

## 🔧Basic configuration Includes:

- Subnetting (VLSM)
- OSPF Routing
- Switching
- Wireless Connectivity
- DHCP
- Encrypt Passwords
- SSH Remote Access
- Full End-to-End Reachability

## 🔐Security configuration

- OSPF Authentication
- Layer 2 Security
- VLAN and SVI Hardening
- port security --> sticky
- DHCP spoofing
- DAI "Dynamic Arp Inspection"
- STP "spanning tree" Mitigation
- Privileged Access Control
- Zone Policy Firewall(ZPF)
- Access Control List (ACLs)
- IPsec VPN
- IPS
- 802.1x Authentication
- AAA (TACACS+ & RADIUS)
- Wireless Network Security
- Cisco ASA Firewall

---
## Subnetting Strategy

We used efficient subnetting techniques to build a secure and scalable design.

### /28 subnet

Used for smaller internal LANs.
To subnet the network 192.168.10.0/24 into /28 subnets, we'll break down the address space as follows:

Step 1: Understanding the /28 Subnet Mask
Original network: 172.16.16.0/24 (Subnet Mask: 255.255.255.0)
New subnet mask: /28 (Subnet Mask: 255.255.255.240)
Step 2: Determine Subnet Details
Number of subnets: Going from /24 to /28 increases the number of bits for subnetting by 4 (from 24 to 28), which gives us

## ![1](https://github.com/user-attachments/assets/1a0d1d6c-7944-4cb8-a557-359aa9b48245)



### /29 subnet

Used for SVI Network.

Step 1: Understanding the /29 Subnet Mask
Original subnet: 172.16.16.160/28 (Subnet Mask: 255.255.255.240)
New subnet mask: /29 (Subnet Mask: 255.255.255.248)
Step 2: Determine Subnet Details
Number of subnets: Going from /28 to /29 increases the number of bits for subnetting by 1 (from 28 to 30), giving us

## ![2](https://github.com/user-attachments/assets/2194ed37-fb25-4971-9f31-acf7cb510a6c)


### /30 subnet

Used for point-to-point router links.

Step 1: Understanding the /30 Subnet Mask
Original subnet: 172.16.16.168/29 (Subnet Mask: 255.255.255.248)
New subnet mask: /30 (Subnet Mask: 255.255.255.252)
Step 2: Determine Subnet Details
Number of subnets: Going from /29 to /30 increases the number of bits for subnetting by 1 (from 29 to 30), giving us

## ![3](https://github.com/user-attachments/assets/b3741a73-84ef-4814-8abf-71bbef1f90a5)


## 🧩 Topology Details

### 🔸Router 1

- Connects to Cisco ASA Firewall

---

### 🔸Router 2

- Includes Loopback Interface
- Configured with IPv4 ACLs

---

### 🔸Router 3

** Admin Access:
    admin3 / admin3pa55
    Enable: ciscopa55
    View1: view1 / view1pa55
    View2: view2 / view2pa55
    View3: view3 / view3pa55

- Role-Based Administrative Access (3 Views)

---

### 🔸Router 4

** Admin Access: Admin4 / admin4pa55

- 4 VLANs with Inter-VLAN Routing
- VLAN Security
- SVI Hardening
- Core & Access Switches
- L2 Security Features
- Server Running TACACS+, NTP, and Syslog
---

### 🔸Router 5

** Admin Access: admin5 / admin5pa55

- Apply Port Security for wired PCs
- Apply 802.1x for wireless PCs
- Wireless LAN(WLAN) security
- Authentication with AAA RADIUS Server

---

### 🔸Router 6

** Admin Access: admin6 / admin6pa55

- Implements Zone-Based Policy Firewall (ZPF)
- Sticky Port Security

---

### 🔸Router 7

** Admin Access: admin7 / admin7pa55

- Intrusion Prevention System (IPS)
  - Outside-to-Inside traffic is restricted
  - Inside-to-Outside traffic is allowed
- Connects to Router 8

---

### 🔸Router 8

** Admin Access: admin8 / admin8pa55

- Interfaces with 3 IPv6 networks (Loopback + G0/0/0 + G0/0/1)

---

### 🔸Router3 ↔ Router5

- IPsec Site-to-Site VPN with encryption

---

### 🔥 Cisco ASA Firewall

** Admin: admin / admin12345

- Configured with 3 Security Zones:
    - INSIDE
    - OUTSIDE
    - DMZ (Hosting Web Server)

🔐 Access Rules:
    - OUTSIDE ↔ DMZ: Allowed (HTTP, HTTPS, SMTP)
    - INSIDE ↔ DMZ: Allowed
    - INSIDE ↔ OUTSIDE: Allowed


