---
layout: project
title: Switching Time Optimization 
date: 10/06/2016
image: roomba.png
---

## Overview

This is the final project for the course: ME454: Optimal Control of Nonlinear Systems

Collaborated on a two-student team, our project was based on  iRobot roomba which was set to follow a sine wave path and then a straight path. The goal was to find the best switching time point for roomba to change from sine wave path to the straight one which could result in the most efficient way (low energy) over the 30-second movement. 

We firstly tried to find the ending status of the sine wave path which could be seen in functions named path1.
By using the cost function:

![Alt text](/Portfolio//projects/costfunction.png)

the status elements q and u was obtained. Our cost function for finding switching time was set to be:

![Alt text](/Portfolio//projects/energyfunc1.png)

which indicated the energy roomba took, where vL was the velocity of roomba's left wheel and vR was the velocity of roomba's right one, t0 was the ending time of sine wave path. 
 
In the second part of the movement, the switching time cost function was set to be

![Alt text](/Portfolio//projects/energyfunc2.png)

where t=30 was the ending time of whole movement. 

Then we combined these two cost functions and tried to find the t0 which could minimize  it. In order to simplify the calculation, we set t0 to be discrete numbers from 1 to 29 and compared the results of them. Using Mathematica, the minimizer of the cost function was achieved at t0=10 that is our optimized switching time.

The iRobot Roomba was programmed to switch trajectory at diffent time point for different trials and the sum of encoders of two wheels was counted. The result corresponds to the theoretical result calculated by Mathematica 

<iframe width="560" height="315" src="https://www.youtube.com/embed/G4FD0E2922k" frameborder="0" allowfullscreen></iframe>

 
