---
notion-id: 327982ca-e761-80a0-96c5-c6ba1ff17ea5
---
HVAC IN 2050? Climate change cooking people, also datacentre prominence increases, good HVAC saves power

smart HVAC uses a lot more data than the low level

low-level data in

- internal temperature inside the box (of the pcb)
- motor torque
- power
- setpoint & position
- direction & tag ? 

normalised position data out

raspberry pi w influx db exposes local data

> [!note]+ # IDEAS
> TWO MAIN IDEAS:
> 
> - We want to handle the data in a way that reduces complexity for a third party integrator, as belimo only sell individual HVAC devices. this is essentially an optimisation problem, DANIEL can help up with this
> - WHAT IF ONE BREAKS? could we take in normal data from the device and analyse it for faults? we could even analyse the effects of a broken device on airflow in the whole building? this means that you find the broken device earlier and replace it faster, which they stated was an issue.
> 

QUESTIONS:

THESE WORK FOR AIR AND WATER (this is invariant) - stick with air bc it is easily testable





