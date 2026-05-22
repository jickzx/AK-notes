---
notion-id: 2ea982ca-e761-8074-abee-e0aad797728b
---
![[l9-11-ethernet-and-internetworking-01.png]]

7 bytes of alternating 1s & 0s (preamble) followed by two 1s.

![[l9-11-ethernet-and-internetworking-02.png]]

CRC enables error detection, the receiver generates a CRC from the data it receives and checks if they match.

CRC is good at catching burst errors, which are changes in a single location to a small set of bits

Small changes in the data result in large changes in the CRC 

## Limits of Ethernet

Practical limits (wired), electrical limits (physical distance degrades signal so length limit on cable)

Latency increases.

Can solve distance issue with repeaters but increases latency

## Store-and-Forward

![[l9-11-ethernet-and-internetworking-03.png]]

Filtering allows packets to travel across bridges only if they need to get to the other side of the repeater. This prevents collisions.

Bridge maintains forwarding table for each network interface, storing the MACs of machines on that side of the bridge.

It builds the forwarding table by learning MACs as packets are sent on the network.

▪ Eventually the bridge can build up a picture of where every machine is
▪ So will only forward packets if necessary
▪ Based around two simple rules:
▪ Receiving a frame tells us what network the sending machine is on
▪ If we don’t know which network a machine is on, forward it regardless

![[l9-11-ethernet-and-internetworking-04.png]]

Ethernet switches are more modern and behave like a star topology.
