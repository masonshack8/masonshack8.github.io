---
layout: post
title:  "Improved Thermal System"
categories: EcoCAR
image: /assets/images/ThermalImprovement.png
---

Designed new thermal system for electric motors to increase the flow and prevent them from overheating during max torque requests.

## Problem

1) The motors overheat due to insufficient flow. They are supposed to get 10 L/min but only get 8 and 6.5 L/min for the front and rear motors, respectively. The issue was known to be flow since the front motor didn't overheat as much.

2) A flow of at least 8 L/min is required to request maximum torque from the drive units in what is called 'boost mode'.

<figure>
  <img src="{{ '/assets/images/Overheat.png' | relative_url }}" alt="Rear Inverter Overheating" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Rear Inverter Overheating</h3>
</div>

## Increasing Flow

To increase flow we planned to add a pump to the existing thermal system, but this was not allowed by the competition. We would need to interface with the stock sytem via a water-water heat exchanger and then add our own pump. This required the design of a full thermal system. I selected a heat exchanger, pump, coolant reservoir, flow restrictor, bleeder valve, flow meter, and pressure sensor and housing.

## Heat Exchanger Selection

The flow requirement was known to be 11.3 L/min on the stock side and 20 L/min on the team side. The pressure drop needed to be less than 36.6 kPa to avoid there being too little flow on the stock side, but the smaller the pressure drop the better.

The thermal requirement was calculated by estimating the maximum power lost as heat. This was determined by calculating the power out as a function of rpm and torque and using the efficiency map to estimate the power loss at each operation point.

<figure>
  <img src="{{ '/assets/images/ThermalRequirementEq.png' | relative_url }}" alt="Thermal Requirement Equations" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Thermal Requirement Equations</h3>
</div>

Heat exchanger suppliers don't provide enough information to use heat tranfer equations to determine the thermal capability of a heat exchanger. Instead, I had to rely on the provided maximum thermal capability or heat exchanger selection tools. From these, I generated a table of possible options and selected the best. I selected row 8 because it met all the requirements, was cheap enough, and could be shipped in time.

<figure>
  <img src="{{ '/assets/images/HXOptions.png' | relative_url }}" alt="Heat Exchanger Options" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Heat Exchanger Options</h3>
</div>

## Pump Selection

The main requirement for the pump is the pressure drop. The pump is expected to operate at 20 L/min. The pressure drop across the new thermal loop is expected to be 38.4 kPa taking into account the pressure drop of the motors, flow meters, and heat exchanger at 20 L/min. Since the pump power can always be reduced, but never increased, a factor of safety of 1.5 is added: 38.4 * 1.5 = 58 kPa.

A Bosch PCE 0392024078 cooling pump was selected because it operates off 12V, is small, and can provide 87 kPa at 20 L/min.

## Remaining Component Selection

Many specific parts were selected, ordered, and implemented which allowed the new thermal system to be successful. Below is a detailed diagram of parts that were selected and added:

<figure>
  <img src="{{ '/assets/images/DetailedThermalDiagram.png' | relative_url }}" alt="Detailed Thermal Diagram" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Detailed Thermal Diagram</h3>
</div>

These components were combined to the stock thermal loop to create a dual thermal loop as shown below:

<figure>
  <img src="{{ '/assets/images/GeneralThermalDiagram.png' | relative_url }}" alt="General Thermal Diagram" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> General Thermal Diagram</h3>
</div>

## Component Mounting

The heat exchanger, pump and coolant reservoir then needed to placed in the vehicle and mounted. Multiple mounting locations were considered for each, often going as far as designing and validating a mount for each location. I then manufactured the mounts from steel using a waterjet and TIG welder.

(Pictures are not included since they are all confidential.)

## Result

A flow rate of 9 L/min was achieved in both motors (balanced using the flow restrictor). Boost mode was activated multiple times and the motors no longer overheat, as proven by the figure below. The thermal improvement occured between year 3 and 4. The ambient temperature in year 3 was higher, but the max temperature was limited by the motor derating when it reached 95 °C. If this didn't occur it would easily reach 110 °C. If the year 4 data were 10 °C hotter, the maximum temperature would still be under 95 °C (the overheating limit).

<figure>
  <img src="{{ '/assets/images/ThermalImprovement.png' | relative_url }}" alt="Motors Don't Overheat" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Motors Don't Overheat</h3>
</div>

<figure>
  <img src="{{ '/assets/images/HeatExchanger.png' | relative_url }}" alt="Heat Exchanger" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Heat Exchanger</h3>
</div>

<figure>
  <img src="{{ '/assets/images/Pump.png' | relative_url }}" alt="Pump" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Pump</h3>
</div>

<figure>
  <img src="{{ '/assets/images/CoolantReservoir.png' | relative_url }}" alt="Coolant Reservoir" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Coolant Reservoir</h3>
</div>