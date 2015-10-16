---
layout: project
title: Line Following Robot
date: 01/2014 to 04/2014
image: eggrace.png
---

## Overview
For the project, we were given a task to construct a robot to follow a track made of a black tape on white background. The track consisted of various turns. The robot was required to stably carry an egg on a spoon throughout the journey.

### Amplifier design for Analogue to Digital Conversion 
Implementing the operational amplifiers, we raised up the output voltages of sensors for detecting white as logic one and kept them low as login zero when detecting the black.  For better performance and easy design, we made a decision to raise the voltage to the saturate.

### Software development for stepper motor 
A well-structured PIC16F648 embededd C program controlled the Y129 stepper motor.The program reverted back to full step drive control with two coils always being active as this provided the highest level of drive torque for driving the robot. The two stepper motors driven independently required the use of a hardware timer and an interrupt routine. We generated the clock pulses of a software implemented Finite State Machine with Timer0 (RTCC) of the PIC.

![Alt text](/Portfolio//projects/robot.png)


