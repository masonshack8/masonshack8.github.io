---
layout: post
title:  "High Voltage Distribution Boxes Design"
categories: Electrical EcoCAR
image: /assets/images/RearHVBox.jpg
---

Designed three high voltage distribution boxes with fuses, HVIL, GFD, contactors, and a test connector.

## Description

I designed three high voltage distribution boxes in Siemens NX for the positive bus of the front motor, negative bus of the front motor, and the rear motor. These boxes include fuses, high voltage interlock loop (HVIL) switches, a ground fault detection device (GFD), contactors, and a test connector. I designed and built the boxes to safely supply high voltage power to two motors for a 6,000 lb vehicle.

<figure>
  <img src="{{ '/assets/images/FrontPosHVBox.JPG' | relative_url }}" alt="Front Positive HV Box" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Front Positive High Voltage Distribution Box</h3>
</div>

<figure>
  <img src="{{ '/assets/images/FrontNegHVBox.JPG' | relative_url }}" alt="Front Negative HV Box" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Front Negative High Voltage Distribution Box</h3>
</div>

<figure>
  <img src="{{ '/assets/images/RearHVBox.jpg' | relative_url }}" alt="Rear HV Box" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Rear High Voltage Distribution Box</h3>
</div>

<figure>
  <img src="{{ '/assets/images/HVSchematic.svg' | relative_url }}" alt="HV Schematic" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> High Voltage Schematic</h3>
</div>

## Main Requirements

There were over 30 requirements for the high voltage boxes. The main requirements are included below as examples. Download any of the documents provided at the bottom of the post for more detail.

1) Copper bus bar must have a cross sectional area of at least 242.0mm^2 to have 400 A of 
current

2) If both high and low voltages are present in an enclosure, they must be separated by an 
insulating barrier with adequate dielectric strength, or must maintain the following spacing 
through the air: 3cm if voltage is over 200 V.

3) There must be at least 9.5mm through air between any two uninsulated live parts of opposite 
polarity if the voltage is over 300 V. 

4) HVIL is required to be incorporated into all HV enclosures, including connectors that can be 
removed and lids/covers. 

## Learnings

Due to the massive amount of conflicting requirements for the high voltage boxes which were frequently changed during their design, I learned how to efficiently make complex designs. I drafted possible configurations of components, ensured they fit the requirements, and compared them to choose the best design for maintenance and assembly. I would then add more details such as holes for the lugs, cable glands, and fasteners and double check the requirements. Inevitably, I would miss a requirement or break one rule trying to follow another, so many iterations were necessary to follow all requirements at the same time.

Download any of the following documents to learn more about the specific requirements for the boxes and details on my design process:

[Front Positive High Voltage Distribution Box Report]({{ "/assets/files/FrontPosHVBoxReport.pdf" | relative_url }})

[Front Negative High Voltage Distribution Box Report]({{ "/assets/files/FrontNegHVBoxReport.pdf" | relative_url }})

[Rear High Voltage Distribution Box Report]({{ "/assets/files/RearHVBoxReport.pdf" | relative_url }})