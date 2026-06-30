# 🌐 Networking Labs

> 11 hands-on labs · Cisco Packet Tracer · ✅ All Completed

---

## 📋 Lab Index

| # | Lab | Key Skills |
|---|-----|------------|
| 01 | [Enterprise Network VLAN & InterVLAN Routing](./enterprise-network-vlan-intervlan-routing) | VLAN segmentation, trunk ports, subinterfaces, Layer 3 switching |
| 02 | [Routing Protocols — OSPF, EIGRP, RIP, Static](./routing-protocols-ospf-eigrp-rip-static) | Dynamic routing, administrative distance, route tables, protocol comparison |
| 03 | [NAT & PAT Address Translation](./nat-pat-address-translation) | Static NAT, dynamic NAT, PAT/overload, inside/outside interface config |
| 04 | [DHCP Multi-VLAN Deployment](./dhcp-multi-vlan-deployment) | DHCP pools, excluded addresses, helper addresses, relay agents |
| 05 | [IP Addressing, Subnetting, VLSM & CIDR](./enterprise-ip-addressing-vlsm-cidr) | Subnet calculations, VLSM design, CIDR notation, IP planning |
| 06 | [Network Troubleshooting Case Studies](./enterprise-network-troubleshooting-vlan-intervlan-routing) | Systematic fault isolation, ping, traceroute, show commands |
| 07 | [HSRP — Network Redundancy & Failover](./hsrp-redundancy-failover) | Active/standby routers, virtual IP, preemption, failover testing |
| 08 | [OSPF Single Area Routing](./enterprise_network_ospf_single_area_routing_lab) | Single area OSPF, DR/BDR election, neighbor adjacency, OSPF verification |
| 09 | [OSPF Multi-Area — ABR & ASBR](./multi-area-ospf-lab) | Multi-area design, area border routers, inter-area route propagation |
| 10 | [Route Redistribution — OSPF & EIGRP](./ospf-eigrp-redistribution) | Inter-protocol routing, metric conversion, redistribute commands |
| 11 | [Syslog Server Configuration](./syslog-multisite-logging-enterprise) | Centralized logging, log severity levels, timestamps, ACL-based log hardening |

---

## 🧠 Skills Covered

**Routing & Switching**
- OSPF (single-area and multi-area), EIGRP, RIP, and static routing configured and verified
- OSPF neighbor adjacencies, DR/BDR elections, and inter-area route propagation (O vs O IA)
- Route redistribution between OSPF and EIGRP with correct metric mapping
- HSRP gateway redundancy with active/standby failover and preemption

**Network Design & Addressing**
- IP addressing using VLSM and CIDR
- VLANs, trunk ports, and subinterfaces for Router-on-a-Stick InterVLAN routing
- DHCP pools per VLAN with helper addresses for cross-subnet relay
- Static NAT, Dynamic NAT, and PAT/overload

**Security & Monitoring**
- Centralized Syslog server across a two-site WAN
- Log timestamps using `service timestamps log datetime msec`
- ACL-based hardening to restrict Syslog access to authorized devices only

**Troubleshooting**
- Fault isolation using `ping`, `traceroute`, `show ip route`, `show ip interface brief`, `show ip ospf neighbor`
- VLAN misassignments, duplex mismatches, and interface config errors diagnosed and resolved

---

## ✅ Completion Status

| Domain | Labs | Status |
|--------|------|--------|
| Networking | 11 / 11 | ✅ Completed |
