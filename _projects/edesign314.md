---
layout: page
title: Dot-Matrix Arcade Game Console
description: Semester project for Design (E) 314.
img: assets/img/12.jpg
importance: 1
category: work
---

## Introduction
Design (E) 314 is the first independent design module that EE students at Stellenbosch University take.
The focus is on implementing a small digital system with a given theme and performance targets that must be met.
The project culminates in a large report describing the design of the system.
As a similar topic could be used in future, a detailed design will not be provided here.
Please contact me personally if you would like more information.

In 2021 each student was tasked with designing and assembling a simple arcade game system with an 8x8 LED Dot Matrix screen.


## Requirements
The whole system was powered by a 9V battery.
User input was available through: 
- five push-buttons: four directional buttons, and one middle button
- physically tilting the system away from its resting position (measured by an inertial measurement unit)
- a sliding input

The system was able to run two games:
- moving a ball through one of four mazes
- controlling a bat in a tennis/pong/breakout game

At the heart of the system was a STM32F103RB development board.
A serial output line was available with debug information, and a test connector was available to allow for automated testing.


## Significant Work
The three largest sub-systems of the project are described below.

#### Output
The 8x8 screen was assembled by hand on a prototyping board.
Although 64 LEDs were used, only 16 GPIO pins were used, saving a significant number of microcontroller peripheral connections.
This was possible because screen updates were performed through row scanning with the full screen updating at 125Hz.

#### Software
Peripheral access was provided by the STM Hardware Abstraction Layer.
Inputs were passed to a state machine which implemented all of the required functionality.
To make debugging and development easier, the entire state machine used pure functions to determine the next state before updating states.
Software-level screen updates were triggered by a 1ms interrupt with the handler copying a row from the screen buffer to the relevant GPIO pins controlling the screen.  
#### IO Interface
The system peripherals used a wide range of interfaces.
The screen used a custom row-scanning interface controlled by standard GPIO pins.
Serial debugging made use of UART and the IMU was controlled through I2C.
The slider input was read through an ADC.
Each component had its own voltage, and noise tolerances which needed to be calculated and compensated for if necessary.

## Personal Experience
I became significantly more confident with hardware development through this project.
Due to my second-year being almost entirely online due to COVID-19, I felt I had missed many useful electronics and microcontroller practicals.
Within two weeks I felt confident in my soldering abilities and felt I had gained a new appreciation for the complexities of digital systems. 

I was quite proud of the robust software that I implemented as it significantly reduced my development time after an initial development investment.
Given this, I wish I had spent more time testing my debouncing algorithm.
This was the only assessment point at which my system failed.
I had attempted to implement a digital low-pass filter, but a simpler system would have sufficed and been easier to test.