---
notion-id: 27e982ca-e761-80f1-b073-c5c3097857b8
cover: "[[lecture-1-osi-and-addressing-01.jpeg]]"
---
---

## Lecture Slides

[https://moodle.nottingham.ac.uk/pluginfile.php/12399954/mod_label/intro/l02_moodle.pdf](https://moodle.nottingham.ac.uk/pluginfile.php/12399954/mod_label/intro/l02_moodle.pdf)

---

## Layers

==**TCP/IP Stack does not have the Session and Presentation layers**==

![[lecture-1-osi-and-addressing-02.png]]

### OSI Model

| Layer | Name | Definition | Examples |
| --- | --- | --- | --- |
| 1 | Physical | How data is converted into physical signals | Ethernet, WiFi, 5G |
| 2 | Data Link | Data formed into frames with details on communicating over a single network. Eg, who the packet is for and its size | Ethernet, WiFi, PPP |
| 3 | Network | Enables packet forwarding between networks.<br>Packets just sent to the destination - connectionless service<br>With networks like the internet, can<br>think of like a boundary | IPv4, IPv6 |
| 4 | Transport |  ▪ End-to-end communication<br>▪ Provides reliability, flow control, and<br>multiplexing | TCP, UDP |
| 5 | ==Session== | Managing a session between end-user applications |   |
| 6 | ==Presentation== | How the data is presented to the application |   |
| 7 | Application |  ▪ In the OSI model, the user interface<br>▪ In TCP/IP, protocols that detail<br>communication between applications | HTTP, POP3, IMAP |

### Sending data

Each layer provides a service capable of transmitting data

Used by the service above to send data, so ==each layer must provide an interface for the layer above to interact with.==

Layer will be presented with the data plus metadata like destination address, etc.

### Receiving data

Layers must also be capable of receiving data from the equivalent layer on another peer.

The layer below will inform it that data has arrived.

For connectionless services this is straightforward because data is just received. 

### Connectionless vs connection oriented 

This difference is akin to sending a text vs making a phone call

Connectionless service:
▪ Packets just sent to the destination
▪ Just provides a way of getting a packet from one computer to another
Connection-oriented:
▪ Computers must first agree to form a connection
▪ Communication can only happen once connection established between the two sides

A connection-oriented service comprises three phases:
▪ Connection set-up
▪ Data transfer (transmission or receipt)
▪ Connection release
Each phase requires two functions:
▪ One in the layer to initiate the function
▪ One in the layer below to inform it that a peer has initiated the function

# Addressing

Different layers serve different purposes so have different kinds of addresses and there must be a mechanism to convert between them.
▪ Layer 3 (IP) addresses need to specify both a machine and the network it is on
▪ Layer 2 addresses need to uniquely identify machines on the same network
▪ At the Application layer, may want understandable addresses

Eg: Ethernet (L2) vs IP(L3). Ethernet uses MAC addresses, unique per manufacturer, in two parts that identify manufacturer and the individual card. IP addresses identify the network and the machine, are also split into two parts, and aren’t fixed. 

So how does IP over ethernet work?

![[lecture-1-osi-and-addressing-03.png]]

### Translating addresses

To translate between IP and MAC, a translation table is used. 

Computer maintains a table in memory that maps IP addresses to Ethernet MAC addresses
Can then look up the IP address in the table, and get the MAC address

To populate the translation table, the Address Resolution Protocol (ARP) is used, which specifies the algorithm used to translate, what packets are sent, what the response to receiving one should be and how they are sent

Eg:

![[lecture-1-osi-and-addressing-04.png]]

When ethernet packets are sent to all machines on a network it is known as a broadcast packet. (Address is all 1s in binary)

![[lecture-1-osi-and-addressing-05.png|Request]]

![[lecture-1-osi-and-addressing-06.png|Reply]]

To reduce requests, when A asks for B’s MAC, since A-B communication is probably bidirectional, B saves A’s IP and translates it to MAC to keep in its own translation table before replying to A. This means B doesn’t have to send another broadcast packet to talk to A.

![[lecture-1-osi-and-addressing-07.png]]

# TL:DR

![[lecture-1-osi-and-addressing-08.png]]