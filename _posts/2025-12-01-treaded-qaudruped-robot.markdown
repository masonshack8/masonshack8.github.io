---
layout: post
title:  "Treaded Quadruped Robot"
categories: Electrical Software
image: /assets/images/Treaded Quadruped.png
---

Robot capable of walking and treaded locomotion for capstone project.

<iframe width="100%" height="315" src="https://www.youtube.com/embed/SE4VRGaMIrc" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="max-width: 100%;"></iframe>

<iframe width="100%" height="315" src="https://www.youtube.com/embed/0X_4qd6fd5w" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="max-width: 100%;"></iframe>

<iframe width="100%" height="315" src="https://www.youtube.com/embed/CqQDbab0szo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="max-width: 100%;"></iframe>

## Description

I worked with Matthew Fernandez, Arunn Sankar, Dante Santaniello, and Harbin Singh on this capstone project to help search and rescue people in collapsed buildings. Collapsed buildings have rubble that must be stepped over as well tight crevices to fit between in order to search the entire pile independently. The primary goal of this project was to make a robot that can navigate both types of obstacles using treads and legs. We wanted it to be mechanically and electrically robust and fluidly transform between the two locomotion methods. We hoped to master the software required to drive and walk, laying the groundwork for the controls needed to step over obstacles. The physical robot required mechanical design, strength analysis, manufacturing, and assembly as well as electrical design, assembly/troubleshooting, and testing. To operate the robot, we needed to develop a full software stack ranging from low level motor control to high level inverse kinematics and stability control. Bringing MORPH (Multi-Obstacle Rescue Platform for Hazards) to life required a wide range of mechanical fabrication tools (e.g. waterjet, sandblaster, manual mill), electronics equipment (e.g. soldering tools, multimeter, oscilloscope), and software tools (e.g. Python libraries, MATLAB simulations, MuJoCo).

To learn more about the project, see our [poster](https://expo.gatech.edu/prod1/portal/portal.jsp?c=17462&p=413142918&g=413665329&id=417673547), [Behance post](https://www.behance.net/inventionstudio1) or download our [final report.]({{ "/assets/files/SAR Multi-Modal Robot – Final Report.zip" | relative_url }})

## My Contributions

### Software

My primary responsibility was writing, testing, and developing the high level software for walking. My initial walking strategy was largely based on the paper: [Stable Stair-Climbing of a Quadruped Robot](https://arxiv.org/pdf/1809.02891) because it discusses the control of quadrupeds with 2 DOF legs without the use of additional sensors or complex software. The first iteration of walking software focused on keeping the center of mass (COM) of the robot in the stability triangle: the shape made by the legs still in contact with the ground during each step of the walking gait. To accomplish this, the quadruped carries out an “initialization sequence” to first reach a stable starting pose before beginning to walk. Also included in the paper is a gait trajectory that slows the motion of each foot as it approaches the ground, preventing jerky steps.

<figure>
  <img src="{{ '/assets/images/StabilityTriangle.png' | relative_url }}" alt="Stability Triangle" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Graphic of Stability Triangle for Quadruped</h3>
</div>

I built a 2D Python animation and set up a physics-based 3D simulation tool called MuJoCo for testing the software before it reached the physical robot. Both simulations were useful throughout testing. MuJoCo was a close representation for how the robot would respond in real life, but the 2D simulation would allow me to slow down the walking and exaggerate the kinematics without the robot falling over from gravity. Together I was able to rapidly improve the software allowing the quadruped to walk.

<iframe width="100%" height="500" src="https://www.youtube.com/embed/KynjmCCVzbU" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="max-width: 100%;"></iframe>

<div class="center">
  <h3 class="text-small"> Video Comparing Kinematics of Physical and MuJoCo Robot</h3>
</div>

Using MuJoCo and physical robot testing, we quickly learned that keeping the COM in the stability triangle isn't enough to prevent the robot from tipping over at each step from its own inertia. We tested a slew of modifications to improve the gait. First, I tried increasing the speed of each step to limit the time the robot was falling. Regardless, the robot continued to pitch toward the raised leg, resulting in harsh motions as the foot was then driven sharply into the ground. To reduce this choppiness, I pivoted the robot body away from the stepping leg. This compensates for the robot falling and lets the stepping foot move to where the robot thinks the ground is. The kinematics required to achieve this pivoting motion as well as the initialization sequence are demonstrated in the following video:

<iframe width="100%" height="500" src="https://www.youtube.com/embed/16GvYvhqMnE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="max-width: 100%;"></iframe>

<div class="center">
  <h3 class="text-small"> Slow Motion Video of Initialization Sequence and Pivoting Kinematics</h3>
</div>

### Electrical

MORPH’s electrical system is built on a 24V architecture powered by a 6S LiPo battery. To reliably monitor and split power between the robot's actuators, we use a drone power distribution board (PDB). The PDB's 5V output powers the 4 leg-locking servo motors, and each of its 4 24V outputs powers 2-3 Unitree GO-M8010-6 motors (10 total). Each group of Unitree motors is linked in series, allowing for daisy-chained RS-485 communication. A separate voltage regulator steps down the input voltage for the Raspberry Pi controlling the robot. I helped choose the electrical components, size the wires and fuses, and assemble the electronics system.

<figure>
  <img src="{{ '/assets/images/Electronics.png' | relative_url }}" alt="Electrical Schematic" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Electrical Schematic for Complete Robot</h3>
</div>

Upon startup, MORPH's motors act as large capacitors, slowly building up charge until they equilibrate with the battery voltage. A pre-charge circuit containing a high-power resistor limits the peak current in this startup period to 2A, protecting the expensive Unitree motors from damage. The pre-charge and main circuits are always sequentially powered on using MOSFET-actuated relays. These MOSFETs can be switched remotely through the Pi or with buttons on the robot's rear IO panel (which also houses status LEDs for each circuit).

<figure>
  <img src="{{ '/assets/images/labeled_robot_front.png' | relative_url }}" alt="Switches and LEDs" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Front of Robot with Switches and LEDs Labeled</h3>
</div>

MORPH’s wires and components are protected by current-limiting fuses. In addition, TVS diodes are used to limit supply voltage spikes. These diodes allow spikes over 28V to “leak” to ground, protecting components that cannot handle higher voltages.

Before powering on the robot, we carried out an extensive series of tests. I built a testing matrix shown below which includes continuity tests to catch any shorts to ground and ensure low resistance connections between components on the same node. We also used a current-limited power supply to test the function of sections of the assembly. One of the surprising behaviors we found was that small voltage spikes would trigger the MOSFETs; pressing the E-stop when main power was on, for example, would trigger the pre-charge circuit. I determined that the addition of a noise-filtering capacitor quickly resolved the issue.

<figure>
  <img src="{{ '/assets/images/ElectricalChecks.png' | relative_url }}" alt="Electrical Test Matrix" class="full-width">
</figure>

<div class="center">
  <h3 class="text-small"> Testing Matrix for Electrical System Safety & Functionality</h3>
</div>