---
notion-id: 2a8982ca-e761-8079-9224-c54d5a81a9d9
---
# Routing

We want to get packets between networks, what do we do?

We route to another machine that is between the two networks

Packet gets unwrapped in the intermediate machine, then wrapped again with a different destination IP

# IP

▪ The Internet is a network of networks
▪ Packets are passed between networks to reach the destination machine
▪ IP: Internet Protocol

IP acts as a layer of abstraction between networks of different types so data can be sent to any machine on any network

▪ IPv4 defines an address as 4 bytes, usually written in the dotted decimal system: 128.243.28.210
▪ Notionally gives space for 4 billion devices, but we’ve run out
▪ Originally, IPv4 partitioned the address space by using various classes of addresses…

## IP Address Classes

▪ Class A – 16.7m addresses per network
1.x.x.x to 127.x.x.x
▪ Class B – 65,536 addresses per network
128.0.x.x to 191.255.x.x
▪ Class C – 256 addresses per network
192.0.0.x to 223.255.255.x
▪ Class D – used for multicast
224.0.0.0 to 239.255.255.255
▪ Class E – reserved
240.0.0.0 to 255.255.255.255

## Class Inter-Domain Routing

▪ Aimed to slow IP address space exhaustion
▪ As well as the rapid growth of routing tables…
▪ Allows a variable number of bits to be used to identify the
network (not just a fixed multiple of 8-bits)
▪ Generally written as an IP address followed by the number of
bits that represent the network
▪ E.g. 10.0.0.1/8, 192.168.1.1/24, 81.143.155.173/30

You specify the number of bits in your network, so you are not restricted to 8 bit increments of networks, so you could get a network size closer to your number of devices. So if you have the first 16 bits as your network you have all the extra bits to specify the device.

![[lecture-13-routing-and-ip-01.png]]


▪ Even with CIDR, IPv4 address space was very quickly used up
▪ By the 1990s, it became clear IPv4 address space would run out
▪ In the late 90s, IPv6 developed to combat this
▪ IPv6 uses 128-bits to represent the address
▪ Addresses tend to be written in hexadecimal notation:
2a00:1450:4009:c0b::93
▪ Again, split into the network part and the machine part
▪ Starting to gain widespread adoption…

## IPv6

▪ Even with CIDR, IPv4 address space was very quickly used up
▪ By the 1990s, it became clear IPv4 address space would run out
▪ In the late 90s, IPv6 developed to combat this
▪ IPv6 uses 128-bits to represent the address
▪ Addresses tend to be written in hexadecimal notation:
2a00:1450:4009:c0b::93
▪ Again, split into the network part and the machine part
▪ Starting to gain widespread adoption…

▪ Network part allocated by standards body
▪ Within the network, you are free to divide it up as you wish
▪ May have many smaller networks internally
▪ Address configuration can be:
▪ Configurable – you specify the IP address (called a static IP address)
▪ Dynamic – computer automatically allocates an address

# Routing

![[lecture-13-routing-and-ip-02.png]]

▪ Routing tends to be a layer 3 concept
▪ Packets are sent with the destination address specifying both the network and machine (IP address)
▪ Router examines the packet to see which is the best place to send it next to reach the destination
▪ I.e. which of its network interfaces will it send it out on
▪ Traffic between networks massively reduced

## Store and forward

▪ Router fully receives the packet before then sending it out on another network
▪ Networks might be of differing speeds
▪ Or receive packets from two networks for the same destination network at the same time
▪ Router needs memory to buffer the packets as they arrive before sending them out

▪ Data will be rewrapped into a different Layer 2 packet
▪ Networks don’t need to be of the same type
▪ Router doesn’t necessarily need to be directly connected to the destination network
▪ May send the packet to a second router which is connected to the destination network

▪ Sending packets now becomes more complicated for every machine
▪ We now have both Layer 3 and Layer 2 packets to think about…
▪ Layer 3 packet contains destination address specifying both the network and machine (IP address)
▪ Layer 2 packet need to be addressed for the specific local network it is on
▪ Can we send packet directly over the local network to the destination machine?
▪ Or do we send it via another machine?

![[lecture-13-routing-and-ip-03.gif]]

How does a computer know where to send a packet?
▪ Doesn’t need to know the whole path to any machine
▪ Just the next hop
▪ This is stored in the routing table

▪ Each machine’s routing table maps a destination address to the next hop
▪ Next hop is just the address of the next machine to send it to
▪ Each computer will have its own, and possibly different, routing table
▪ Depending on how it is connected to the network(s)