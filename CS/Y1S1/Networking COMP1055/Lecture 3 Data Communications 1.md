---
notion-id: 285982ca-e761-804d-b77b-c1929e455366
---
# Physical Networking

Layer 1 sends binary signals over a physical network

# RS232

Two computers want to talk, each has three pins.

Transmit pin, receive pin and Ground pin

Transmit pins talk to receive pins and ground pins connect

Uses different voltages to represent bits, +15V for 0, -15V for 1

RS232 is serial, meaning bits are sent sequentially, as opposed to parallel where multiple bits are transmitted and received

RS232 is asynchronous

Both ends need the same settings for controlling how characters are transmitted, like is the MSB received first or the LSB, as well as the bitrate and number of bits

LSB first means little-endian,

MSB first means big-endian

Ethernet is byte big-endian, bit little-endian

Async transmission sends extra bits are the start of the transmission to allow the receiver to synchronise.

Synchronous transmission uses framing to help synchronisation, sends specified idle sequence if there is no data to send.

RS232 uses a start bit and a stop bit to identify the beginning and end of the transmission

Transmissions begin with transition from 1 to 0, 8 transmitted bits later, will return to 1 again, if not then we have a framing error and we need to resynchronise.

For each 8 bit character, 2 bits are start and stop, so 

# Half and full duplex

Half duplex: information can go both ways but not at the same time

Full duplex: information can be transmitted in both both directions at the same time, not waiting for the other machine to finish transmitting


