# MOJ Enterprise Network Simulation (Cisco Packet Tracer)
---
!Network Topology (topology/logical_topology.png)

## Overview

This project is a simulated enterprise network implementation built in Cisco Packet Tracer using a three-tier architecture (Core, Distribution, and Access layers).

The design implements:

* Hierarchical enterprise network design
* OSPF dynamic routing
* HSRP gateway redundancy
* EtherChannel using LACP
* DHCP relay architecture
* Cisco ASA firewall segmentation
* NAT/PAT configuration
* VLAN segmentation
* Wireless LAN Controller integration
* Redundant paths and failover testing

The implementation was completed in phased stages following a High-Level Design (HLD), with corrections applied where Packet Tracer limitations or inconsistencies in the original design affected deployment.

---

## Topology

The network contains:

### Core Layer

* 2 Cisco 2911 routers
* 2 Cisco 3650 multilayer switches
* Cisco ASA firewall
* NMS server
* Wireless LAN Controller

### Distribution Layer

* 4 Cisco 3650 multilayer switches

### Access Layer

* 4 Cisco 3650 access switches
* PCs
* IP phones
* Access points

---

## Implemented Technologies

| Feature            | Status   |
| ------------------ | -------- |
| VLAN Segmentation  | Complete |
| DHCP Relay         | Complete |
| OSPF Area 0        | Complete |
| EtherChannel       | Complete |
| HSRP               | Complete |
| NAT/PAT            | Complete |
| ACLs               | Complete |
| Redundancy Testing | Complete |

---

## Verification Commands

### OSPF

```cisco
show ip ospf neighbor
show ip route ospf
show ip protocols
```

### HSRP

```cisco
show standby brief
show standby
```

### EtherChannel

```cisco
show etherchannel summary
show interfaces port-channel1
```

### Routing

```cisco
show ip route
ping
traceroute
```

---

## Lessons Learned

During implementation I discovered several design inconsistencies and corrected them:

* Layer 3 uplinks required `no switchport`
* Some interface addressing conflicted between design sections
* Loopback interfaces were necessary for stable OSPF router IDs
* Packet Tracer required practical adaptations for technologies such as IRF

---
# Packet Tracer Limitations and Design Adaptations

## Purpose

This document explains implementation decisions where Cisco Packet Tracer differs from real enterprise deployments.

---

## IRF Simulation

Real H3C Intelligent Resilient Framework (IRF) operates as a hardware stacking technology with a dedicated control plane.

Packet Tracer does not support IRF.

Adaptation used:

* Parallel links bundled with LACP EtherChannel
* Routed Port-Channels used to simulate redundancy behavior

---

## Firewall Dynamic Routing

Real enterprise firewalls frequently participate in OSPF or BGP.

Packet Tracer ASA functionality is simplified.

Adaptation used:

* Static routing on ASA
* OSPF restricted to routers and multilayer switches

---

## Simplified Internet Representation

The cloud object in Packet Tracer does not emulate a complete ISP infrastructure.

Adaptation used:

* Cloud object treated as upstream internet connectivity

---

## Wireless Controller Simplification

Packet Tracer WLC behavior differs significantly from production Cisco controllers.

Adaptation used:

* Basic management configuration only
* Functional demonstration of centralized wireless management

---

## Failover Behavior

Packet Tracer protocol timers may behave differently from real Cisco devices.

Examples:

* HSRP convergence timing
* OSPF adjacency timing
* EtherChannel convergence timing

Therefore observed failover timing in the simulation should not be treated as production values.

---
## Author

Jonathan Oyo

Network Engineering | Cisco | Infrastructure | Enterprise Networking
