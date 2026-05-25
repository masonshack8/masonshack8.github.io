---
layout: post
title:  "Thermal Sensor System"
categories: Electrical Software EcoCAR
image: /assets/images/ThermalSensingSignals.png
featured: true
---

Within 24 hours, I designed, built, and tested hardware and software to read the flow, temperature, and pressure of an automotive cooling system.

## Background

This project was completed so quickly because the basic building blocks had already been tested by the 'Flowmeter Controller' project, which this replaced in the vehicle. These flowmeters (which include a temperature sensor) on the motor side were used to ensure sufficient flow was always reaching the motors. The flowmeter and pressure sensor on the stock loop were used to verify the added components match the stock pressure drop and flow. This ensures the stock components are cooled as intended.

## Electrical

<figure>
  <img src="{{ '/assets/images/Teensy4.0V4.png' | relative_url }}" alt="Electrical Schematic" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Electrical Schematic</h3>
</div>

## Software

All software was made in Simulink.

<figure>
  <img src="{{ '/assets/images/FullSoftware.png' | relative_url }}" alt="Full Software" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Full Software</h3>
</div>

<figure>
  <img src="{{ '/assets/images/TempSoftware.png' | relative_url }}" alt="Temperature Sensing Software" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Temperature Sensing Software</h3>
</div>

<figure>
  <img src="{{ '/assets/images/FlowSoftware.png' | relative_url }}" alt="Flow Sensing Software" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Flow Sensing Software</h3>
</div>

<figure>
  <img src="{{ '/assets/images/PumpSoftware.png' | relative_url }}" alt="Pump PWM Software" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Pump PWM Software</h3>
</div>

<figure>
  <img src="{{ '/assets/images/PressureSensor.png' | relative_url }}" alt="Pressure Sensing Software" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Pressure Sensing Software</h3>
</div>

## Functionality

<figure>
  <img src="{{ '/assets/images/ThermalSensingSignals.png' | relative_url }}" alt="Thermal Sensing Signals" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Thermal Sensing Signals</h3>
</div>