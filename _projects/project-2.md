---
layout: project
title: EOG Eye Tracking
date: 10/2014 to 03/2015
image: eog.png
---

## Overview
The E.O.G (Electrooculography) is the technique for measuring the potential difference.  In the my application, the measuring system can be decomposed into the three active electrodes mounted on goggles, the amplifier and filter circuit and the oscilloscope to display the resulting signal (Electrooculogram). Pairs of the electrodes are needed for measuring Electrooculogram. The pair placed on the left and right detects the horizontal eye movements.Although blinking signal is mainly a vertical eye movement, it can be detected in horizontal channel, which is normally a spike with much shorter time duration than horizontal eye movement but usually bigger potential difference between two electrodes.

![Alt text](/Portfolio//projects/concept.png)

### Instrumental amplifier and low pass filter 
The Instrumentation Amplifier design consisted of two stages of the amplifier. The front end is two non-inverting amplifiers coupled together by a common resistor,which is usually called the Gain Stage and the second stage named as Difference Amplifier Stage  is a differential amplifier. The low pass filter was implemented to remove the high frequency noise.

![Alt text](/Portfolio//projects/circuit1.jpg)

### Active Notch Filter 
The 50 Hz powerline noise would be amplified at the mean time when the E.O.G signals would. Therefore, the active notch filter with 50 Hz in the narrow stop band (high Q factor) suited the requirement.


