# EtherChannel Lab

## Objective

To configure EtherChannel using LACP and understand how multiple physical links can function as a single logical link.

## Topology

![PC1 ---- Switch1 ==== Switch2 ---- PC2](/Topology.png)

Where:

- Switch1 and Switch2 are connected using 4 physical interfaces
- EtherChannel groups these interfaces into one logical link

## Devices Used

- 2 Cisco switches
- 2 PCs

## IP Addressing

| Device | IP Address | Subnet Mask |
|----------|------------|--------------|
| PC1 | 192.168.1.10 | 255.255.255.0 |
| PC2 | 192.168.1.20 | 255.255.255.0 |

## Configuration Summary

Configured:

- LACP
- Port Channel 1
- Trunk interfaces
- VLAN 10 and 20
- access ports

Example:

```bash
interface range fa0/1-4
channel-group 1 mode active

interface port-channel 1
switchport mode trunk
interface range fa0/5-10
switchport mode access
switchport access vlan 10
interface range fa0/11-15
switchport mode access
switchport access vlan 20
```

## Verification

Commands used:

```bash
show etherchannel summary
ping 192.168.1.20
```
![EtherChannel-Info-Screenshot](/verification.png)
## Testing Performed

- Continuous ping test
- Disconnected individual links
- Verified traffic continued through remaining links
![Redundancy](/redundancy.png)

---

## Key Learning Points

- Multiple links appear as one logical connection
- Provides redundancy
- Increases bandwidth
- Simplifies management