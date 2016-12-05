---
layout: project
title: Automatic Detection of Gait Mode for Robotics Prothesis Laboratory 
date: 10/12/2016
image: ambulation_lab.png
---

## Overview
In the robot prosthesis lab in RIC (Rehabilitation Institute Chicago), the control of advanced robotics leg uses machine learning algorithms that classify user's activity, specifically, walking on different terrains (level ground, ramp and stairs). To train the algorithms, the data collected should be properly labeled. Currently, the switching mode of the controller on the robotics leg is remotely controlled by a person watching the amputee subject's location and press the button. The goal of this project is to develop a sensing system to locate the user with the prosthesis leg and automatically switch modes based on the user location in the environment (Ambulation lab). 

## Scope
The student will design and build prototype that meets the following specification. The evaluation of potential sensors, for example, IR sensors , Kinect and Ultrasonic should be documented to summarize the pros/cons of different sensor types and provide guidance for people who may continue this project in the future. A well drawn diagram of the complete system will include the existing
controller on the robotics leg and show what the system is composed of and their relationships. The mode switching must be completed within the period of one stride, approximately 1 second. The
system should have zero false positive.

## Evaluation of the potential sensors
Before looking into the detailed specification of the sensors, several bullet points of requirements were clarified:

* Budget: $500 - $1000
* Frame rate: The switching should be competed within 400 ~ 500ms
* Resolution/Accuracy: a quarter meter
* Latency 
* Coverage: Dimension of the lab room: 30 (length) x 20 (width) x 8.5 (height) feet  Dimension of the equipment: 15/18 (length) x 20 (width) x 8.5 (height) feet  Dimension of the square level ground: 4 x 4 inches  Number of the stairs: 3
* Robustness: No false positive 

Evaluated sensor candidates that would be a good fit for this application include: Kinect, Ultrasound, IR, Optical motion tracking system and Home surveillance system. [This documentation](https://drive.google.com/file/d/0B58hvswRIFctZDJYbW53YXplUXc/view?usp=sharing) contains the pros/cons for each type. 

## Design 









