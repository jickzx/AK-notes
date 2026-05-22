---
notion-id: 286982ca-e761-805c-b925-eb9c48966daf
---
[l04_moodle.pdf](https://moodle.nottingham.ac.uk/pluginfile.php/12421079/mod_label/intro/l04_moodle.pdf)

![[lecture-4-data-communications-2-01.png]]

# Modulation

RS232 uses +- 15V to represent binary, which is only suitable for short distances.

Continuous oscillating signals can go much further distances so comms systems tend to use a continuous wave as a carrier for the data which is then modulated to represent binary.

![[lecture-4-data-communications-2-02.png]]

# Demodulation

Does the opposite of a modulator

![[lecture-4-data-communications-2-03.png]]

# MoDem

Modulation can be done with analogue and digital signals. Digital modulation is referred to as shift keying. 

A modem modulates and demodulates signals. 

Types of modulation are: 

- Amplitude Modulation
- Frequency Modulation
- Phase Shift Modulation

# Digital Signals

![[lecture-4-data-communications-2-04.png]]

This is more susceptible to noise though so we usually just use Manchester Encoding

![[lecture-4-data-communications-2-05.png]]

# Transmission Rates

Defined in bits per second, depends on two things:

1. Baud Rate - how many times signal changes per second
2. Number of symbols we can send

$$

\text{bits per second} = \text{baud rate} \cdot \left\lfloor \log_2(\text{number of symbols}) \right\rfloor
$$

Increasing baud rate means the system must respond faster

Increasing number of symbols makes the system more susceptible to noise

# Forming Networks

To connect N computers point-to-point, we need $0.5(N^2 - N)$ connections.

Using a shared medium to connect computers instead of connecting them point-to-point mitigates this. Any computer can still talk to any other but must use addressing to know which to send messages to. Only one computer can send data at a time which is called access control.

![[lecture-4-data-communications-2-06.png]]