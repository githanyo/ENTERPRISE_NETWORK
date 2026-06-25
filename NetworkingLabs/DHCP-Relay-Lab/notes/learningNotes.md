# Learning Notes

## What I learned

Initially, the DHCP request failed because the DHCP server and client were on different subnets. The DHCP Discover message was sent as a broadcast and could not cross the router.

After configuring:

ip helper-address 192.168.20.2

the router acted as a relay agent and forwarded the DHCP requests to the server.

Simulation Mode in Packet Tracer made it easier to visualize the sequence:

DHCP Discover → DHCP Offer → DHCP Request → DHCP ACK

This lab demonstrated how enterprise networks can use a centralized DHCP server to provide addressing services to multiple network segments.
