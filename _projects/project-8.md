---
layout: project
title: Automatic Detection of Gait Mode for Robotics Prothesis Laboratory 
date: 10/12/2016
image: ambulation_lab.png
---

## Overview

The main goal of this project was developing a sensing system to locate the user with the prosthesis leg and automatically switch modes based on the user location in the Ambulation Lab. [The project report](https://docs.google.com/document/d/1p9NUiAjyq4ZqS9eabb7aCLV2O0axVvJ6hDps2XZaHfI/edit?usp=sharing) covers the details of the implementation. 

## Background 

In the robot prosthesis lab in RIC (Rehabilitation Institute Chicago), the control of advanced robotics leg uses machine learning algorithms that classify user’s activity, specifically, walking on different terrains (level ground, ramp and stairs). To train the algorithms, the data collected should be properly labeled. Currently, the switching mode of the controller on the robotics leg is remotely controlled manually by a researcher watching the amputee subject’s location and switching the controller. 

In order to automatically collect and label the training data, we would like to automate the selection of activity mode by sensing when the amputee is on the stairs, ramp, or level ground.

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

I ended up with the implementation of webcam-based vision sensing. The right leg (eventually will be the prosthesis leg) was labeled with a large patch of red tapes. A Standard USB web camera that streams the images in real time on Raspberry Pi 3 was fixedly placed at transitions between level ground and stairs for testing, on the level ground before the first stair or at the top of the stairs. An OpenCV-Python script running on the Raspberry Pi 3 created two threads: one grabbed and stored the current frame and the other processed the frame with red color detection, counted the number of red pixels and sent out a string as a TCP/IP client. The threshold of 1000 to trigger the switch was evaluated by trial and error.

## Testing 

The goal of the test was to determine whether or not the webcam vision sensing triggers the mode switch quickly enough. The timestamps to record when message is received by the TCP/IP server on Wi-Fi key fob should be no later than the latest key press. I was up the stairs with red patch attached at the outside of my right leg. During testing, the webcam was placed on the level ground at bottom or top of the stairs (as illustrated in the Fig 1, 2 and 3). Ten trials were conducted when I transitioned from the stairs to level ground and sixteen trials from the level ground to stairs. Two researchers were operating the key press using the App on the phone.

![Alt text](/Portfolio//projects/stairtop.png)

## Result

The figure below shows the average time before the latest key press from two types of trials. The result indicates the vision sensing implementation is feasible to detect transitions and trigger mode switch. 

![Alt text](/Portfolio//projects/timebefore.png)

## Conclusion and future study 

The project proves the feasibility of implementing webcam vision sensing to detect the transition and automate the mode switch of the controller on the prosthesis leg. There has been no triggering of a state change that should not happen and 100% of the transition has been detected.

In the future, more testing should be conducted on different transitions with webcams and Raspberry Pis mounted on multiple positions. Patients wearing prosthesis legs would be recruited to participate in the testing as well as more able-bodied subjects.






