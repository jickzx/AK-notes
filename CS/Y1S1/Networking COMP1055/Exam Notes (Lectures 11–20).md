---
notion-id: 2d6982ca-e761-8025-bdc2-f3d254b97324
---
## Lecture 11: Ethernet in Practice

- Early Ethernet was designed for **small-scale LANs** using a **shared coaxial bus**
- Scaling Ethernet introduces:
    - Electrical signal degradation
    - Increased collision probability
    - Practical cabling limitations
- Electrical limits of Ethernet:
    - Cables exhibit resistance and capacitance
    - Signals attenuate over distance
    - Voltage levels drop and edges become less sharp
    - Eventually signals become undecodable
- Propagation delay increases with cable length, increasing collision likelihood
- **Repeaters**:
    - Operate purely at **Layer 1**
    - Regenerate electrical signals to overcome attenuation
    - Forward *everything*, including noise and collisions
    - Do not reduce collision domains
- **Multiport repeaters (hubs)**:
    - Physically form a star topology
    - Logically behave as a bus
    - All devices share a single collision domain
- **Bridges**:
    - Operate at **Layer 2**
    - Use store-and-forward to copy complete frames only
    - Do not forward collisions
    - Split collision domains
- **Switches**:
    - Multiport Layer 2 bridges
    - Each port is its own collision domain
    - Frames forwarded selectively based on MAC addresses
- Logical topology can differ significantly from physical topology

---

## Lecture 12: Transport Layer Overview

- The transport layer provides **end-to-end communication** between applications
- Operates above IP and below application protocols
- Supports **multiplexing** using port numbers
- Port numbers identify:
    - Sending application
    - Receiving application
- **TCP**:
    - Reliable delivery
    - Ordered data stream
    - Flow control and congestion control
    - Treats data as a continuous byte stream
- **UDP**:
    - Connectionless
    - No delivery or ordering guarantees
    - Minimal protocol overhead
    - Preserves message boundaries

---

## Lecture 13: Routing and IP

- The Internet is a **network of networks**
- Different networks may use different physical and data link technologies
- **Internet Protocol (IP)**:
    - Layer 3 protocol
    - Connectionless
    - Provides best-effort packet delivery
- **Best-effort networking**:
    - Packets forwarded independently
    - No guarantees of delivery, order, duplication, or delay
    - Routers may drop packets due to congestion, errors, TTL expiry, or MTU limits
    - Reliability handled by higher layers (e.g. TCP)
- IPv4 addresses are **32 bits**
- Address structure identifies:
    - Network
    - Host within the network
- Routers forward packets based only on **destination IP address**
- Routers determine the **next hop**, not the full path
- Routing tables map destination networks to next hops

---

## Lecture 14–15: Client–Server and TCP

- Networking commonly follows the **client–server model**
- **Server**:
    - Passive
    - Listens for incoming connections on a port
- **Client**:
    - Actively initiates communication
- **TCP**:
    - Reliable, connection-oriented transport protocol
    - Guarantees in-order delivery
    - Prevents duplication
    - Performs retransmission when packets are lost
- TCP provides a **byte-stream abstraction**
- Packet boundaries are hidden from applications
- **Sockets**:
    - Programming interface for network communication
    - Treated as file descriptors
    - Abstract underlying network details

---

## Lecture 16: UDP Sockets

- UDP provides a **connectionless transport service**
- No handshake or connection setup phase
- Each packet sent independently
- Socket API uses:
    - socket()
    - sendto()
    - recvfrom()
    - close()
- UDP provides:
    - No reliability
    - No ordering
    - No congestion control
- Applications must handle loss if required
- Used where low latency is prioritised over reliability

---

## Lecture 17: DNS and UDP in Practice

- Humans prefer names; networks require IP addresses
- **DNS maps domain names to IP addresses**
- DNS is:
    - Distributed
    - Hierarchical
    - Scalable
- Resolution begins at **root servers**
- Types of DNS servers:
    - Authoritative
    - Recursive
    - Caching
- DNS messages consist of:
    - Header
    - Question
    - Answer
    - Authority
    - Additional sections
- DNS typically uses UDP due to low overhead
- **QNAME encoding**:
    - Domain split into labels
    - Each label preceded by a length byte
    - Terminated with a zero-length label

---

## Lecture 18: IP Fragmentation and Path MTU Discovery

- **Time To Live (TTL)**:
    - Field in IP header
    - Decremented by each router
    - Packet dropped when TTL reaches zero
    - Prevents routing loops
- **Maximum Transmission Unit (MTU)**:
    - Largest packet a network can carry
    - Defined by network technology
    - Ethernet MTU typically 1500 bytes
- IP packets larger than MTU:
    - Must be fragmented
    - Or dropped if DF flag is set
- **Fragmentation**:
    - Packet split into multiple fragments
    - Each fragment has its own IP header
    - Fragment offset specifies data position
- **Don’t Fragment (DF) flag**:
    - Prevents fragmentation
    - Causes packet drop and ICMP error if MTU exceeded
- **Path MTU Discovery**:
    - Sender sets DF flag
    - Learns smallest MTU along path via ICMP messages
    - Sender adjusts packet size accordingly
    - Required behaviour in IPv6

---

## Lecture 19: IP and Routing Tables

- Routing tables contain:
    - Destination network
    - Netmask
    - Next hop
- Routing is **hierarchical**
- Only network prefixes are stored, not individual hosts
- **Default routes**:
    - Used when no specific route matches
    - Reduce routing table size
- **CIDR**:
    - Allows variable-length network prefixes
    - Written as IP/prefix length
- **Netmask matching**:
    - Destination IP AND netmask
    - Result compared to network address
    - Determines selected route
- Packet forwarding depends jointly on:
    - Routing table
    - MTU constraints
    - TTL value

---

## Lecture 20: Routing Algorithms and TCP

- Routing tables determine how packets are forwarded through a network
- Routing tables can be constructed:
    - **Statically**:
        - Built when router boots
        - Do not change until reboot
    - **Dynamically**:
        - Built when router boots
        - Updated automatically as network conditions change
- Dynamic routing preferred for large or changing networks

---

### Optimal Routing and Graph Models

- Networks modelled as a **graph**
- Nodes represent **networks**
- Edges represent **links between networks**
- Each edge assigned a **weight**
- Distance between networks is the sum of edge weights
- Routing aims to find **shortest paths**
- Shortest path may not be the most intuitive route

---

### Dijkstra’s Algorithm (Shortest Path First)

- Algorithm used to compute shortest paths from a source network
- Requires:
    - Complete knowledge of the network graph
    - Knowledge of all edge weights
- Modified version records **next hop**, not full path
- Data structures used:
    - **S**: set of nodes whose shortest path is not yet finalised
    - **D[v]**: shortest distance from source to node *v*
    - **R[v]**: next hop from source to reach *v*
- Initialisation:
    - S contains all nodes except the source
    - For each node *v*:
        - D[v] = weight(source, v) or infinity
        - R[v] = *v* if directly connected, else 0
- Iterative process:
    - Select node *u* in S with smallest D[u]
    - Remove *u* from S
    - For each neighbour *v* of *u* still in S:
        - c = D[u] + weight(u, v)
        - If c < D[v]:
            - Update D[v]
            - Update R[v]

---

### Distributed Routing Algorithms

- Full network graph not always available
- Routers:
    - Build routing tables from local knowledge
    - Exchange routing information with neighbouring routers
    - Update tables when new information is received

---

### Distance-Vector Routing

- Routers periodically send vectors containing:
    - Destination networks
    - Distance to each destination
- On receiving a vector:
    - Router updates its table if a shorter path is found
- Simple but slower to respond to network failures

---

### Link-State Routing (Shortest Path First)

- Routers send messages when:
    - Links go up
    - Links go down
- Each router builds a complete network graph locally
- Shortest paths calculated locally
- Faster adaptation to network changes

---

### Reliability and Best-Effort Networks

- IP is a **best-effort** protocol
- Provides no guarantees of:
    - Delivery
    - Ordering
- Packet loss more likely across multiple networks
- Reliability provided by higher-level protocols
- Reliability can increase latency and overhead

---

### TCP/IP Model

- **IP** operates at Layer 3
- **TCP** operates at Layer 4
- TCP provides reliable communication on top of IP

---

### Transmission Control Protocol (TCP)

- TCP provides:
    - Reliable
    - End-to-end
    - Full-duplex
    - Virtual connections
- Connection-oriented protocol
- Supports multiplexing using **65,536 ports**

---

### TCP Connections and Ports

- A TCP connection is identified by:
    - Source IP address
    - Source port
    - Destination IP address
    - Destination port
- Connections are explicitly opened and closed

---

### TCP Packet Structure

- TCP header contains:
    - Source port
    - Destination port
    - Sequence number
    - Acknowledgement number
    - Control flags
    - Window
    - Checksum
- Minimum TCP header size is **20 bytes**

---

### Sequence Numbers

- Every byte transmitted is assigned a **32-bit sequence number**
- TCP header stores the sequence number of the first byte in the packet
- Sequence numbers wrap at 2³²
- Used to handle:
    - Out-of-order delivery
    - Packet loss

---

### Out-of-Order Delivery

- IP does not guarantee packet order
- TCP uses sequence numbers to reorder packets
- Data delivered to applications in correct order

---

### Packet Loss and Retransmission

- IP does not guarantee packet delivery
- TCP uses acknowledgements to detect loss
- If no acknowledgement received:
    - Packet is retransmitted
- Retransmission timeout is adaptive

---

### Acknowledgements

- TCP header includes an acknowledgement field
- ACK value equals the sequence number of the **next expected byte**
- Sender infers which data has been received successfully

---

### Windowing

- Stop-and-wait transmission is inefficient
- TCP uses a **sliding window**
- Sender may transmit multiple packets without waiting for ACKs
- Receiver advertises available buffer space
- Window size adjusted dynamically
- Used for flow control and congestion control

---

### TCP Connection Lifecycle

- **Connection establishment**:
    - Uses the three-way handshake:
        - SYN
        - SYN + ACK
        - ACK
- **Connection termination**:
    - Uses FIN and ACK packets
    - Ensures all data delivered before closing