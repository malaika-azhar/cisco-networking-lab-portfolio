# Enterprise Network VLAN & InterVLAN Routing

**Domain:** Networking
**Difficulty:** Intermediate — Advanced
**Tools:** Cisco Packet Tracer

---

## 🎯 Objective
Configure VLANs, InterVLAN routing, VTP, Management VLAN, DHCP, SSH, Port Security, ACLs and security hardening across a two-switch enterprise network.

---

## 🛠️ Tools & Technologies
| Tool | Purpose |
|------|---------|
| Cisco Packet Tracer | Network simulation |
| Router 2911 | InterVLAN routing via subinterfaces |
| Switch 2960 x2 | VLAN switching, VTP, port security |
| VTP | VLAN synchronization across switches |
| DHCP | Automatic IP assignment per VLAN |
| SSH v2 | Secure remote management |
| ACLs | Inter-VLAN traffic filtering |
| Port Security | MAC-based access control |
| BPDU Guard | STP loop prevention |

---

## 🖧 Topology

### Devices
- 1 Router (2911)
- 2 Switches (2960)
- 4 PCs
- 1 Admin PC (for SSH management)

### Physical Connections

**PCs to Switches:**
| PC | Switch | Port |
|----|--------|------|
| PC0 | Switch1 | Fa0/1 |
| PC1 | Switch1 | Fa0/2 |
| PC2 | Switch2 | Fa0/1 |
| PC3 | Switch2 | Fa0/2 |
| Admin PC | Switch1 | Fa0/3 |

**Switch to Switch:**
| From | To | Cable |
|------|----|-------|
| Switch1 Fa0/24 | Switch2 Fa0/24 | Copper Cross-Over |

**Router to Switches:**
| Router Interface | Switch | Switch Port | Cable |
|-----------------|--------|-------------|-------|
| G0/0 | Switch1 | Fa0/23 | Copper Straight-Through |
| G0/1 | Switch2 | Fa0/23 | Copper Straight-Through |


---

## 🗂️ VLAN Design
| VLAN | Name | Network | Gateway |
|------|------|---------|---------|
| VLAN 10 | Sales | 192.168.10.0/24 | 192.168.10.1 |
| VLAN 20 | IT | 192.168.20.0/24 | 192.168.20.1 |
| VLAN 99 | Management | 192.168.99.0/24 | 192.168.99.1 |

---

## 💻 PC IP Configuration
| PC | VLAN | IP | Mask | Gateway |
|----|------|----|------|---------|
| PC0 | 10 | DHCP | auto | auto |
| PC1 | 20 | DHCP | auto | auto |
| PC2 | 10 | DHCP | auto | auto |
| PC3 | 20 | DHCP | auto | auto |
| Admin PC | 99 | 192.168.99.10 | 255.255.255.0 | 192.168.99.1 |

---

## 📋 Steps & Screenshots

### Step 1 — Build the Topology
Set up all devices and connect cables exactly as shown above.
![Topology](./screenshots/01-topology.png)

---

### Step 2 — Configure VTP on Switch1 (Server)
Set Switch1 as VTP Server so it can push VLANs to Switch2 automatically.
![VTP Server](./screenshots/02-vtp-server.png)

---

### Step 3 — Configure VTP on Switch2 (Client)
Set Switch2 as VTP Client so it receives VLANs from Switch1.
![VTP Client](./screenshots/03-vtp-client.png)

---

### Step 4 — Create VLANs on Switch1 Only
Create VLAN 10, 20, 99 on Switch1. Switch2 will sync automatically via VTP.
![VLANs Created](./screenshots/04-vlans-created.png)

---

### Step 5 — Verify VLAN Sync
Confirm VLANs appear on Switch2.
![VTP Sync](./screenshots/05-vtp-sync.png)

---

### Step 6 — Configure Switch1 Ports
Assign VLANs on Switch1.
![Switch1 Ports](./screenshots/06-switch1-ports.png)

---

### Step 7 — Configure Switch2 Ports
Assign VLANs on Switch2.
![Switch2 Ports](./screenshots/07-switch2-ports.png)

---

### Step 8 — Unused Ports Security
Disable unused ports.
![Unused Ports](./screenshots/08-unused-ports.png)

---

### Step 9 — Port Security
Enable port security.
![Port Security](./screenshots/09-port-security.png)

---

### Step 10 — Management VLAN
Configure management VLAN.
![Management VLAN](./screenshots/10-mgmt-vlan.png)

---

### Step 11 — SSH Switches
Enable SSH.
![SSH Switches](./screenshots/11-ssh-switches.png)

---

### Step 12 — Router Configuration
Configure router for InterVLAN routing.
![Router Config](./screenshots/12-router-config.png)

---

### Step 13 — DHCP Pools
Configure DHCP.
![DHCP Pools](./screenshots/13-dhcp-pools.png)

---

### Step 14 — PC DHCP
Verify DHCP IP assignment.
![PC DHCP](./screenshots/14-pc-dhcp.png)

---

### Step 15 — DHCP Binding
Confirm leases.
![DHCP Binding](./screenshots/15-dhcp-binding.png)

---

### Step 16 — Pre ACL Ping Test
Test connectivity before ACL.
![Pre ACL Ping](./screenshots/16-pre-acl-ping.png)

---

### Step 17 — ACL Configuration
Configure ACL rules on the router.
![ACL Config](./screenshots/17-acl-config.png)

---

### Step 18 — ACL Test
Verify ACL blocking/allowing traffic.
![ACL Test](./screenshots/18-acl-test.png)

---

### Step 19 — SSH Test
Test SSH remote access to switches.
![SSH Test](./screenshots/19-ssh-test.png)

---

### Step 20 — Final Verification
Check full network.
![Final Verify](./screenshots/20-final-verify.png)

---

### Step 21 — Save Config
Save configuration.
![Save Config](./screenshots/21-save-config.png)



## 📟 Summary of Commands
| Command | Purpose |
|---------|---------|
| `vtp mode server/client` | Set VTP role |
| `vtp domain` | Set VTP domain |
| `vlan 10` | Create VLAN |
| `switchport mode access/trunk` | Set port mode |
| `switchport access vlan 10` | Assign port to VLAN |
| `spanning-tree portfast` | Enable PortFast |
| `spanning-tree bpduguard enable` | Enable BPDU Guard |
| `switchport port-security` | Enable port security |
| `interface vlan 99` | Create management SVI |
| `ip default-gateway` | Set switch gateway |
| `crypto key generate rsa` | Generate SSH keys |
| `ip ssh version 2` | Enable SSH v2 |
| `encapsulation dot1Q` | Tag subinterface |
| `ip dhcp pool` | Create DHCP pool |
| `ip dhcp excluded-address` | Reserve IPs |
| `access-list 110 deny` | Create ACL rule |
| `ip access-group 110 in` | Apply ACL |
| `copy running-config startup-config` | Save config |

---

## ⚠️ Challenges & How I Solved Them
| Challenge | Solution |
|-----------|----------|
| VLANs not syncing to Switch2 | Verified VTP domain name matched exactly on both switches |
| PCs not getting DHCP IP | Checked excluded address range and DHCP pool network match |
| SSH not connecting | Confirmed RSA key size 1024+ and SSH v2 enabled |
| ACL blocking wrong traffic | Reviewed wildcard masks and access-group direction (in/out) |
| Trunk port not passing VLANs | Verified allowed VLAN list on trunk interface |

---

## 🧠 What I Learned
How to build a complete enterprise network with VLANs, VTP synchronization, InterVLAN routing, Management VLAN, DHCP automation, SSH remote access, Port Security, BPDU Guard, ACL traffic filtering and security hardening — all in one lab.

---

## 📁 Files
| File | Description |
|------|-------------|
| `enterprise-network-vlan-intervlan-routing.md` | Full lab documentation |
| `enterprise-network-vlan-intervlan-routing.pkt` | Packet Tracer file |
