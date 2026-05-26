---
layout: post
title:  "Automotive Display"
categories: Software EcoCAR
image: /assets/images/Display.png
---

In 5 weeks I designed, coded, tested, and improved a team-added display for EcoCAR.

<figure>
  <img src="{{ '/assets/images/Display.png' | relative_url }}" alt="Display Interface" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> First Page of Team-Added Display Interface</h3>
</div>

## Description

I designed and coded the display which allows the user to view and interact with the parts of the vehicle the team added such as the motors and autonomous driving features. I also coded the microcontroller that communicates between the display and the vehicle. The challenge was making a microcontroller send and receive messages from the display and the vehicle using different communication methods that had to be coded and decoded manually. I wrote 2000 lines of C++ code to transfer messages using this microcontroller.

<figure>
  <img src="{{ '/assets/images/DisplaySystemDiagram.png' | relative_url }}" alt="Display System Diagram" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Diagram of Vehicle, Microcontroller, and Display and Their Communication Protocols</h3>
</div>

## Design

The software for the display itself was fairly simple, but the software for the messenger microcontroller was not. The real challenge was setting up a CAN and serial communication system to work simultaneously. 

I built an [Arduino CAN example file](https://github.com/masonshack8/CANTeensyLibrary.git) from the [FlexCAN_T4 library](https://github.com/tonton81/FlexCAN_T4) for future reference. I am unable to post the software used to control the display for confidentiality reasons, but the code is currently 2000 lines due to the amount of messages it must handle.

<figure>
  <img src="{{ '/assets/images/ArduinoExample1.png' | relative_url }}" alt="Arduino Example" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Segment of Arduino Example File for CAN Communication</h3>
</div>

Properly communicating with the display using serial messages was not easy either. I spent hours reading the documentation, sending signals from the display, and sending signals from the Teensy to get messages to send reliably.

## Electrical

The electrical system for the display was very simple since it only required connecting the Teensy to one of the CAN buses of the LYRIQ and the Teensy and display together for serial communication. Noise in the serial wires was still an issue and caused the display to freeze after a few minutes of use during early testing. I reduced the baud rate to temporarily fix this issue until the noise could be reduced.

<figure>
  <img src="{{ '/assets/images/DisplayElectricalDiagram.png' | relative_url }}" alt="Display Electrical Diagram" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Electrical Diagram of Display and Teensy</h3>
</div>

## Testing

Since the testing time available on the vehicle is always limited, I built my own testing hardware and software. I set up a second Teensy 4.0 that would send CAN messages from Simulink to ensure the communication pipeline was working all the way to the display.

<figure>
  <img src="{{ '/assets/images/TestSystemDiagram.png' | relative_url }}" alt="Test System Diagram" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Diagram of Testing Microcontroller, Display Microcontroller, and Display and Their Communication Protocols</h3>
</div>

Testing with this system ensured that when I plugged the display into the vehicle, there were very few surprises. I was able to add new features, redevelop code, test using the above system, and then direclty plug the display back in to the vehicle with no issues.

<figure>
  <img src="{{ '/assets/images/SimulinkExample1.png' | relative_url }}" alt="Simulink Example" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Segment of Simulink Code for Testing System</h3>
</div>