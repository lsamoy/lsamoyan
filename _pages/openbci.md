---
layout: default
title: FPV Drone Building
filename: fpv_drone.md
permalink: /fpv_drone
---

# FPV Drone Build

## Purpose

Evaluate the resources of Ukraine in building FPV drones for their war efforts. Benchmarking the quality and time necessary to spend on construction of these drones. Improvements to this effort were also made. Two teams participated to have better results, both teams with a diverse group of individuals from those who have technical skills, to those who do not.

## Instructions

This project was run by an engineering team at my previous company. I was a team leader of one of two teams in order to benchmark and provide an average time it takes to build, flash, and fly an FPV drone.

1. All drone components needed to be sourced. They were ordered utilizing the following video: https://www.youtube.com/watch?v=3NaTwaRA78Q&t=2798s
    - Frame: Mark4 v2 / XL10 V6
    - Stack: SpeedyBee v4 55A
    - Motors: FlashHobby 3115 900kv
    - Propeller: HQ MacroQuad Prop 10x5x3
    - Camera: Caddx Ratel Pro
    - VTX: Rush Max Solo 2.5w
    - VTX Antenna: Rush Cherry 2
    - RX: Happy Model Diversity RX
    - Controller: RadioMaster TX16

2. This video was also followed for constructed the drone. This included: building the frame, soldering the motors, camera, the TX modules, and RX modules to the flight controller stack.

3. For the FC antennas and VTX antennas, 3D models were modified from the provided pieces (which cannot be put here due to security restrictions) using Solidworks 2023. Then, they were sliced using PrusaSlicer and printed out on the Prusa MK4S utilizing PETG filament due to its durability over PLA.

4. The drone was flashed with the ArduPilot firmware. This is because of its compatibility with TAK, and due to it being a platform I had used previously for non-FPV drones. Due to my pre-existing understanding of the firmware and parameters, I felt it was a better choice when the purpose of the drone was not for racing.

## Results

The team I built the drone for, Team Blue, clocked in a build time of about 5.5 hours over the span of a few weeks. This was logged with a time sheet on hours worked on the drone. The drone was utilized in some testing and demonstrations of FPV drone capabilities. It was also paired with a few of the other start-up's we are involved in.
