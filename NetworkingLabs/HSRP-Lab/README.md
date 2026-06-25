# HSRP Lab

## Objective

To configure HSRP and understand gateway redundancy and failover.

## Topology

![hsrp-network-topology](/topology.png)

## Devices Used

- 2 Routers
- 1 Switch
- 1 PC

## IP Addressing

| Device | IP Address |
|----------|------------|
| Router1 | 192.168.10.2 |
| Router2 | 192.168.10.3 |
| Virtual Gateway | 192.168.10.1 |
| PC1 | 192.168.10.100 |

## Configuration Summary

Router-0:

```bash
interface g0/0
ip address 192.168.10.4 255.255.255.0
standby 1 ip 192.168.10.1
standby 1 priority 130
standby 1 preempt
```


Router-1:

```bash
interface g0/0
ip address 192.168.10.2 255.255.255.0
standby 1 ip 192.168.10.1
standby 1 priority 120
standby 1 preempt
```

Router-2:

```bash
interface g0/0
ip address 192.168.10.3 255.255.255.0
standby 1 ip 192.168.10.1
standby 1 priority 100
standby 1 preempt
```

## Verification

Commands used:

```bash
show standby
ping 192.168.10.1
```
![hsrp-verification](/R1-hsrp-verifcation.png)
---
![hsrp-verification](/R2-hsrp-verifcation.png)
## Testing Performed
![testing image screenshot](/failover-verification.png)
- Continuous ping from PC
- Shutdown of active router interface
- Observed automatic failover
- Restored router and verified preemption

## Key Learning Points

- HSRP provides high availability
- Hosts use a virtual gateway
- Failover occurs automatically
- Priority determines active router