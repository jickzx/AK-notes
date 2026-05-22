---
notion-id: 2e9982ca-e761-805c-99bc-f83c298e4d19
---
Right to left from Top Level domains like .uk, .com and so on 

13 Root servers to start from

![[dns-ip-and-routing-01.png]]

![[dns-ip-and-routing-02.png]]

![[dns-ip-and-routing-03.png]]

## Internet Control Message Protocol

IP is a best-effort service but it still reports errors through ICMP.

## Time-To-Live

Packets can end up in a loop when being packet switched as routes change dynamically whilst the packet is in transit. To guard against this, IP packets have a TTL field in their header that is decremented at each router it passes through. When it hits 0, the packet is dropped and ICMP message is returned to sender.

## Fragmentation

As IP packets are passed between different networks, the packet size that each network can handle may be different. This is called the MTU. When the MTU is smaller than the size of the packet, the packet must be fragmented to have a size ≤ the MTU of the networks it passes through. 

Packets are split into chunks that are multiples of 8 bytes long, and are reconstructed at destination machine. 

### “Don’t Fragment” flag

Single bit specifying whether to fragment the packet
If a router receives a packet larger than its MTU that has the DF flag on, it will drop the packet and send a message containing the router’s MTU back to the source machine via ICMP.

## Path MTU Discovery

Source machine finds the maximum packet size that can be sent across the network by finding the minimum MTU on path to the destination, then uses that as the MTU for fragmenting packets.

If a router receives a packet greater than its MTU:
▪ Drop the packet
▪ Send ICMP message including its MTU back to the source
▪ If source receives this message, reduces its path MTU to match the new limit, resends the data (now split into more than one)
packet)
▪ If any of these packets reach a router with a lower MTU, cause another ICMP message to be sent back to the source
▪ And so on… until the path MTU is small enough that data reaches its destination

## Netmasking

Netmasks can be used to test if an IP address is in a particular network

▪ Netmask can be used very simply to test to see if an IP address is in a particular network
▪ Just AND the destination IP address with the netmask for the network, bit by bit
▪ If the IP address is in the network, the result will be equal to that network’s IP address AND netmask
▪ So the next hop for that IP address would be the destination for that network…

![[dns-ip-and-routing-04.png]]

![[dns-ip-and-routing-05.png]]

### Default Path

There can be a default path set for packets whose destination address isn’t on the network.

![[dns-ip-and-routing-06.png]]

## Routing Tables

![[dns-ip-and-routing-07.png]]

Static Routing Tables are created and filled in when the router boots and calculates the possible routes to different networks. This is inflexible because it cannot adapt to changes in the network. 

Dynamic Routing Tables begin with an initial routing table then update the network as conditions change. Allows the system to work around failures in routes.

Dynamic Routing Tables are calculated with Dijkstra's beginning from the router executing it. 

### Distributed Routing Algorithms

Dijkstra’s needs the entire network structure to be known to the router executing it, when this isn’t the case, a distributed algorithm can be used to build the table.

![[dns-ip-and-routing-08.png]]

