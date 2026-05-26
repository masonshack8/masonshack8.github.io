---
layout: post
title:  "Flowmeter Controller"
categories: Software Electrical EcoCAR
image: /assets/images/FlowmeterReal.jpg
---

Designed electronics, wrote software, tested, and validated flowmeter for EcoCAR.

## Description

Coolant temperature and flow is needed to safely operate the motors for the vechicle to avoid overheating. I built the hardware and software to read the flow and temperature of coolant in the Georgia Tech EcoCAR LYRIQ using a SEN-FM18T10 Coolant Flow Meter with Temperature Sensor from Koolance and Teensy 4.0. The Teensy 4.0 powers the flow meter, reads the corresponding signals, and send the measurements via CAN to the LYRIQ controller. The Teensy 4.0 is run off of Simulink and has been used to help diagnose cooling issues in the vehicle. I tested the flow and temperature reading for accuracy and reliability.

<figure>
  <img src="{{ '/assets/images/FlowmeterDiagram1.png' | relative_url }}" alt="Flowmeter Diagram" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Diagram of Flowmeter System Including Teensy 4.0 that Reads and Sends Signals</h3>
</div>

<figure>
  <img src="{{ '/assets/images/FlowmeterSchematic.png' | relative_url }}" alt="Flowmeter Schematic" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Electrical Schematic of Flowmeter</h3>
</div>

## Design

The team-added controller didn't have enough analog ports, requiring the addition of a microcontroller: Teensy 4.0. The temperature sensor is a resistor. A voltage divider was used to measure the resistance and temperature of the sensor.

<figure>
  <img src="{{ '/assets/images/VoltageDivider.png' | relative_url }}" alt="Voltage Divider" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Diagram of Voltage Divider for Temperature Sensor</h3>
</div>

The flow sensor is a reed switch which means there is continuity every rotation. The period was calculated for each rotation, which was then used to calculate the rpm and corresponding flow. Below are images of how the flow was calculated, the raw signal, and calculated flow.

<figure>
  <img src="{{ '/assets/images/FlowSimulink.png' | relative_url }}" alt="Flow Simulink" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Simulink Code for Converting Voltage Reading into Flow</h3>
</div>

<figure>
  <img src="{{ '/assets/images/FlowSimulink2.png' | relative_url }}" alt="Flow Simulink2" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Subsystem of Simulink Code</h3>
</div>

<figure>
  <img src="{{ '/assets/images/FlowReading.png' | relative_url }}" alt="Flow Reading" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Voltage Reading of Flow Sensor and Calculated Flow</h3>
</div>

## Testing

To test the temperature sensing capability, I placed different resistors in the circuit in place of the flowmeter to verify the Teensy was reading the correct resistance. I then plugged in the flowmeter and verified the Teensy would read the correct room temperature to validate the resistance to temperature relationship.

To test the flow sensor I added an integrator to the flow, filled up a 0.5L water bottle, and ensured that 0.5L of fluid passed through the flow meter.

<figure>
  <img src="{{ '/assets/images/FlowTest.png' | relative_url }}" alt="Flow Test" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Integrated Flow Meter Data Showing it Can Read Flow Correctly</h3>
</div>

## Diagnosing Intermittent Issue

Periodically, the rear flowmeter would send odd temperature data and would otherwise have a lot of noise. I inspected the circuit, tested the resistance between the wires, soldered the pins to the connector to ensure a good connection, plugged it back in and it worked. After it broke again, I removed it and tested the reistance between each part of the same solder node. I found that one of the solder joints was discontinuous in parts, so I resoldered the joint and permanently fixed the issue. From this experience I learned the importance of thoroughly heating solder joints when adding new wires.

<figure>
  <img src="{{ '/assets/images/BrokenSolder.png' | relative_url }}" alt="Broken Solder" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Solder Joint that was Broken and Causing False Readings</h3>
</div>

## Takeaways

I have since learned about signal conditioning and filtering and realize I should have added capacitors to reduce the noise in the signals instead of using a moving mean in Simulink. When making and testing the circuit, I learned the importance of never soldering in the microcontroller so that it can be removed, separately tested, and the circuit resistances can be verified much easier. I also added LEDs to the flow sensors to visually ensure the interal fan was spinning during testing. This also helped me know when the flow should be zero.