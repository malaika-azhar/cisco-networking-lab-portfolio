# Routing Protocols — OSPF, EIGRP, RIP & Static

**Domain:** Networking  
**Difficulty:** Intermediate — Advanced  
**Tools:** Cisco Packet Tracer  

---

## 🎯 Objective
Configure, compare and optimize Static, RIP v2, EIGRP and OSPF routing protocols across a multi-router enterprise topology. Implement OSPF multi-area, MD5 authentication, passive interfaces, floating static routes, loopback interfaces and default route redistribution.

---

## 🛠️ Tools & Technologies
| Tool | Purpose |
|------|---------|
| Cisco Packet Tracer | Network simulation |
| Router 2911 x3 | Multi-protocol routing |
| Switch 2960 x2 | LAN switching |
| Static Routing | Manual route + floating backup |
| RIP v2 | Distance vector — legacy reference |
| EIGRP | Cisco hybrid — enterprise networks |
| OSPF Multi-Area | Industry standard link state routing |
| Loopback Interfaces | Stable router ID and management |
| MD5 Authentication | Secure routing updates |
| Passive Interface | Security + bandwidth optimization |
| Default Route Redistribution | Advertise internet route via OSPF |
| Floating Static Route | Backup redundancy |

---

## 📊 Protocol Comparison
| Protocol | Type | AD | Metric | Real World Use |
|----------|------|----|--------|----------------|
| Static | Manual | 1 | None | Small networks, default routes |
| Floating Static | Manual Backup | Custom | None | Redundancy backup |
| RIP v2 | Distance Vector | 120 | Hop count | Legacy networks only |
| EIGRP | Hybrid | 90 | Bandwidth + Delay | Cisco enterprise |
| OSPF | Link State | 110 | Cost (bandwidth) | Industry standard |

---

## 🖧 Topology

### Devices
- 3 Routers (2911)
- 2 Switches (2960)
- 2 PCs
- Loopback interfaces on all routers

### Physical Connections
| From | To | Interface | Cable |
|------|----|-----------|-------|
| PC1 | Switch1 | Fa0/1 | Straight-Through |
| Switch1 | R1 | Fa0/23 — G0/0 | Straight-Through |
| R1 | R2 | G0/1 — G0/0 | Cross-Over |
| R2 | R3 | G0/1 — G0/0 | Cross-Over |
| R3 | Switch2 | G0/1 — Fa0/23 | Straight-Through |
| Switch2 | PC2 | Fa0/1 | Straight-Through |

---

## 🌐 IP Addressing
| Device | Interface | IP Address | Subnet Mask | Description |
|--------|-----------|------------|-------------|-------------|
| R1 | G0/0 | 192.168.1.1 | 255.255.255.0 | LAN 1 Gateway |
| R1 | G0/1 | 10.0.0.1 | 255.255.255.252 | WAN Link to R2 |
| R1 | Loopback0 | 1.1.1.1 | 255.255.255.255 | Router ID |
| R2 | G0/0 | 10.0.0.2 | 255.255.255.252 | WAN Link to R1 |
| R2 | G0/1 | 10.0.0.5 | 255.255.255.252 | WAN Link to R3 |
| R2 | Loopback0 | 2.2.2.2 | 255.255.255.255 | Router ID |
| R3 | G0/0 | 10.0.0.6 | 255.255.255.252 | WAN Link to R2 |
| R3 | G0/1 | 192.168.2.1 | 255.255.255.0 | LAN 2 Gateway |
| R3 | Loopback0 | 3.3.3.3 | 255.255.255.255 | Router ID |
| PC1 | — | 192.168.1.10 | 255.255.255.0 | Gateway 192.168.1.1 |
| PC2 | — | 192.168.2.10 | 255.255.255.0 | Gateway 192.168.2.1 |

---

## 🗺️ OSPF Area Design
| Area | Routers | Networks |
|------|---------|----------|
| Area 0 (Backbone) | R1, R2 | 10.0.0.0/30, 10.0.0.4/30 |
| Area 1 | R2, R3 | 192.168.2.0/24 |
| ABR | R2 | Connects Area 0 and Area 1 |

---

## 💻 PC IP Configuration
| PC | IP Address | Subnet Mask | Gateway |
|----|------------|-------------|---------|
| PC1 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC2 | 192.168.2.10 | 255.255.255.0 | 192.168.2.1 |

---

## 📋 Steps & Screenshots

### Step 1 — Build the Topology
![Topology](./screenshots/01-topology.png)

### Step 2 — Configure Hostnames, Banners and Loopback Interfaces
![Loopback Config](./screenshots/02-loopback-config.png)

### Step 3 — Configure IP Addressing on All Routers
![IP Addressing](./screenshots/03-ip-addressing.png)

### Step 4 — Configure Static Routes
![Static Routes](./screenshots/04-static-routes.png)

### Step 5 — Test Static Route Connectivity
![Static Test](./screenshots/05-static-test.png)

### Step 6 — Configure Floating Static Route (Backup)
![Floating Static](./screenshots/06-floating-static.png)

### Step 7 — Migrate to RIP v2
![RIP Config](./screenshots/07-rip-config.png)

### Step 8 — Test RIP Connectivity
![RIP Test](./screenshots/08-rip-test.png)

### Step 9 — Migrate to EIGRP
![EIGRP Config](./screenshots/09-eigrp-config.png)

### Step 10 — Test EIGRP Connectivity
![EIGRP Test](./screenshots/10-eigrp-test.png)

### Step 11 — Migrate to OSPF Multi-Area
![OSPF Config](./screenshots/11-ospf-config.png)

### Step 12 — Verify OSPF Neighbors and Areas
![OSPF Neighbors](./screenshots/12-ospf-neighbors.png)

### Step 13 — Configure OSPF MD5 Authentication
![OSPF Auth](./screenshots/13-ospf-auth.png)

### Step 14 — Configure Passive Interfaces
![Passive Interface](./screenshots/14-passive-interface.png)

### Step 15 — Configure Default Route Redistribution
![Default Route](./screenshots/15-default-route.png)

### Step 16 — Final Verification
![Final Verify](./screenshots/16-final-verify.png)

### Step 17 — Save Configuration
![Save Config](./screenshots/17-save-config.png)

---

## 📟 Summary of Commands
| Command | Purpose |
|---------|---------|
| `hostname R1` | Set router hostname |
| `banner motd` | Set login warning banner |
| `interface loopback 0` | Create loopback interface |
| `ip route` | Configure static route |
| `ip route AD` | Floating static route with high AD |
| `router rip` | Enable RIP |
| `version 2` | Use RIP version 2 |
| `no auto-summary` | Disable auto summarization |
| `router eigrp 100` | Enable EIGRP AS 100 |
| `show ip eigrp neighbors` | Verify EIGRP neighbors |
| `router ospf 1` | Enable OSPF process 1 |
| `router-id 1.1.1.1` | Set OSPF router ID manually |
| `network x.x.x.x area 0` | Add network to OSPF area |
| `passive-interface g0/0` | Stop OSPF updates on LAN |
| `default-information originate` | Redistribute default route |
| `ip ospf authentication message-digest` | Enable MD5 auth |
| `ip ospf message-digest-key 1 md5` | Set MD5 key |
| `show ip route` | View full routing table |
| `show ip ospf neighbor` | Verify OSPF neighbors |
| `show ip ospf database` | View OSPF link state database |
| `show ip ospf interface brief` | View OSPF interfaces |
| `show ip eigrp topology` | View EIGRP topology table |
| `show ip protocols` | View active routing protocol |
| `copy running-config startup-config` | Save config |

---

## 📸 Screenshot Summary
| File Name | When to Take It |
|-----------|----------------|
| `01-topology.png` | After building full topology |
| `02-loopback-config.png` | After creating loopback interfaces |
| `03-ip-addressing.png` | After `show ip interface brief` all routers |
| `04-static-routes.png` | After `show ip route static` |
| `05-static-test.png` | Successful ping with static routing |
| `06-floating-static.png` | After configuring floating static route |
| `07-rip-config.png` | After `show ip protocols` RIP |
| `08-rip-test.png` | Successful ping with RIP — R routes |
| `09-eigrp-config.png` | After `show ip eigrp neighbors` |
| `10-eigrp-test.png` | Successful ping with EIGRP — D routes |
| `11-ospf-config.png` | After `show ip route ospf` |
| `12-ospf-neighbors.png` | After `show ip ospf neighbor` |
| `13-ospf-auth.png` | After MD5 authentication config |
| `14-passive-interface.png` | After `show ip protocols` |
| `15-default-route.png` | After default route redistribution |
| `16-final-verify.png` | All final show commands |
| `17-save-config.png` | After saving configuration |

---

## ⚠️ Challenges & How I Solved Them
| Challenge | Solution |
|-----------|----------|
| OSPF neighbors not forming | Verified wildcard masks and area numbers match |
| EIGRP neighbors not forming | Confirmed AS number 100 matches all routers |
| OSPF auth breaking adjacency | Matched MD5 key number and password both sides |
| Passive interface breaking OSPF | Only applied on LAN interfaces not WAN links |
| Multi-area OSPF not working | Verified R2 is ABR with interfaces in both areas |
| Loopback not used as router ID | Configured `router-id` manually |

---

## 🧠 What I Learned
How to design and implement a multi-protocol routing environment, migrate between routing protocols, secure OSPF with MD5 authentication, implement multi-area OSPF for scalability, configure floating static routes for redundancy, and optimize routing with passive interfaces and default route redistribution.

---

## 📁 Files
| File | Description |
|------|-------------|
| `README.md` | Full lab documentation |
| `routing-protocols-ospf-eigrp-rip-static.pkt` | Packet Tracer file |
