---
notion-id: 2e9982ca-e761-8082-937e-dba81b337ef8
---
# Random Access Protocols

## Carrier Sense

Checks if the channel is idle by listening on the channel to see if anything else is transmitting before sending data.

## ALOHA

Data transmitted wirelessly in fixed packet sizes

Central computer sends an acknowledgement to client when packet is received

If there is a collision due to multiple responses being sent out at the same time, the packets are randomly resent with exponential backoff

## Reliability of Ethernet

Ethernet has collision detection but that does not make it reliable as when more nodes are added to the network, the chance of a collision increases. Due to exponential backoff, computers will spend more time waiting to resend packets. This limits network sizes.

## Wi-Fi

As Wi-Fi is a wireless transmission method, it has to deal with the hidden node problem.

It does this using CSMA/CA, the CS means it doesnt transmit when it sees something is being transmitted by sending a small pilot packet to reserve the bus, and if that doesn’t collide with anything then it can begin transmitting data.

### RTS & CTS

Pilot message is a request to send data. Modem can send CTS signal in response to RTS to help alleviate the hidden node problem. RTS and CTS packets reserve the bus for the constituent device.

It isn’t used for all transmissions as that would be too much overhead for sending small amounts of data.

If RTS are sent by two devices at the same time, the basestation would detect it and not send the CTS, which would trigger random backoff for resending the RTS for each device.

