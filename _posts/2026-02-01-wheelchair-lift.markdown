---
layout: post
title:  "Wheelchair Lift"
categories: EcoCAR
image: /assets/images/Uplift.png
---

Within 5 days, I designed a wheelchair lift that fit within tight geometric constraints, could lift up to 60 lbs, and cost less than $900.

## Background

Another subteam on the Georgia Tech EcoCAR team was tasked with making a wheelchair lift, but they needed help getting a functioning prototype. I started from scratch and designed a sturdy wheelchair lift that only had a few issues when built.

## Hand Calculations/FEA

I first designed the base to ensure the design was feasible. It had to be attached to the vehicle using the seat bolts and fit between the seat and the door. I used FEA for this since all parts were rigidly connected.

<figure>
  <img src="{{ '/assets/images/UpliftBaseFEA.png' | relative_url }}" alt="Wheelchair Lift Base FEA" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Wheelchair Lift Base FEA</h3>
</div>

The remainder of the mechanism was designed using hand calculations for the parts in isolation because the interface between the components was imprecise. The remainder of the lift was reliant on the parts pushing on each other.

<figure>
  <img src="{{ '/assets/images/HandCalcSummary.png' | relative_url }}" alt="Hand Calculations Summary" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Hand Calculations Summary</h3>
</div>

More detail on the hand calculations and system can be found in the following slides:

[Wheelchair Lift Prototype Hand Calculations and FEA]({{ "/assets/files/Prototype CAD, FEA, Analysis.pdf" | relative_url }})

## Fabrication

I was responsible for waterjetting the steel plates (Tyson Tran helped me with this part) and welding the plates and aluminum t-slots together. This process took about 25 hours.

<figure>
  <img src="{{ '/assets/images/WaterjetPieces.png' | relative_url }}" alt="Waterjet Pieces" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Waterjet Pieces</h3>
</div>

<figure>
  <img src="{{ '/assets/images/BaseWelded.png' | relative_url }}" alt="Base Welded" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Base Welded</h3>
</div>

<figure>
  <img src="{{ '/assets/images/SupportsWelded.png' | relative_url }}" alt="Supports Welded" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Supports Welded</h3>
</div>

<figure>
  <img src="{{ '/assets/images/MotorandBase.png' | relative_url }}" alt="Motor and Mount" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Motor and Mount</h3>
</div>

This mount for the motor was actually a separate project for which I designed, fabricated, and installed the mount in 12 hours.

<figure>
  <img src="{{ '/assets/images/FullAssem.png' | relative_url }}" alt="Full Wheelchair Lift Assembly" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Full Wheelchair Lift Assembly</h3>
</div>

## Issues

1) The wheelchair lift was too tall and didn't allow a wheelchair to enter the vehicle. If it were any shorter, however, it would not aid the user much.
2) The pulley meant for the end of the lift didn't fit betweeen the support plates when folded. It was merely removed.
3) The rope got tangled in the 45° support when the lift was folded up. The support had to be removed completely when folded to resolve this issue.