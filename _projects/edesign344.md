---
layout: page
title: Solar-powered light system
description: Semester project for Design (E) 344.
img: /assets/img/edesign344/photo.jpg
importance: 1
category: work
---

<p>
    <img width="95%" src="/assets/img/edesign344/photo.jpg">
</p>

## Introduction
Design (E) 344 is the second independent design module that EE students at Stellenbosch University take.
The entire module is focused on researching, designing, building, testing, and documenting an analogue electronic system with a given theme and specifications.
Since certain aspects of the project may be reused in this class in future, I will not provide in-depth design details here.
Please contact me personally if you would like more information.

In 2021 each student was tasked with creating a light system charged through solar power with variable brightness control, and capable of reporting current draw and various voltage levels to an application running on a desktop computer.


## Requirements
Some of the system requirements that were met:
- The 6V battery could be charged either through a 12V DC supply provided by an AC adapter or by a 5W PV module.
- Charging consisted of a stable 7.2V supply to the battery with the charging current limited to 400mA.
- The charging could be controlled by a high-side switch.
- Battery charge state monitoring with a Schmitt Trigger controlling the battery output to ensure battery charge did not drop below 6V.
- Low-noise current measurement ranging from 150mA delivered to the load to 450 mA supplied during charging.
- Digital load control through a low-side switch.
- Supply- and battery- voltage measurement.
- Ambient brightness detection.
- The load could only switch on once ambient brightness was low enough, and the user had pressed the required button, as well as a pilot light to indicate when the light could be switched on successfully for the user.
- Firmware was developed for an Arduino Beetle to take digital measurements of all sensors.
- Measurements were communicated to a desktop application over a serial connection with further user prompts being communicated from the application to the system over the same connection.
- A state-of-charge indicator was included to allow the user to evaluate the battery voltage without the application on hand.
- An analogue brightness control mechanism was provided for situations where the application connection was not on hand.


## Significant Work
As can be seen by the photos of the system, there are far too many individual sub-systems to be discussed in-depth here, but several classes of sub-systems can be lumped together.

#### Analogue Amplifiers
Operational Amplifiers were used extensively in the sub-systems.
Some of the configurations used were:
- voltage follower
- inverting amplifier
- differential amplifier

In order to get as much performance from the system, amplifiers were often designed to cover as much of their operating range as possible so common-mode- and differential- input constraints had to be adhered to.
Furthermore, the noise of other components had to be measured and compensated.

#### Logic Systems
MOSFETs were used for high- and low-side switches, while more Operational Amplifiers were used to implement necessary logic systems including:
- comparator
- Schmitt Trigger
- digital AND gates using high-gain non-inverting summing amplifiers
- variable PWM oscillator

#### Interface between Analogue and Digital
The Arduino Beetle only had eight pins available.
No unnecessary sensors could thus be used, and remaining output pins had to be capable of controlling the entire system.
The firmware compensated for some discrepancies or unavoidable noise in the measurements.
Sensors calibration was available at a software level.    

#### GUI Application
The application was developed with Python and Tkinter.
Graphs were created with MatPlotLib, and the serial connection was handled by a university-provided communication library.
A theme was applied to make the Tkinter interface more user-friendly.

## Personal Experience
This project and module consumed a significant amount of my time between August and October 2021.
It was incredibly satisfying to see all of the complexity coming together in a working system with each sub-system playing its role in providing meaningful data and control capability to a user for an otherwise complicated circuit.

My report writing skills were put to the test, and I would consider myself more confident in my ability to convey technical design decisions and present results concisely.
This is in large part due to the feedback and criticism I received from my peers as well as from seeing several exceptional reports from other students.