---
layout: project
title: Human Character Mapping
date: 01/2015 to 03/2015
image: human_char.png
---

## Overview

3D computer animation has been developed and used to create blockbuster films and computer games. The goal of this project is to leverage Kinect-based OpenNI skeleton tracking to animate virtual characters in real-time. A music stand was chosen as the virtual charater and has sufficient DOF for exciting 3D animation.   

Regarding the techniques used in Computer Animation (CA) to decompose virtual characters, most animation systems are based on a representation of a character's skeleton. The skeleton is used to compute the positions and orientations of selected mesh of the charater. In this case, the skeleton was written up in URDF and visualized in RViz under ROS. 

It is very handy to use Microsoft Kinect to produce physical interface. 

<p align="center">

<iframe width="560" height="315" src="https://www.youtube.com/embed/m98IJ71wfu0" frameborder="0" allowfullscreen></iframe>

</p>

### Pre-requisites

* Download OpenNI on this [site](http://openni.ru/openni-sdk/openni-sdk-history-2/index.html)

* Install [openni_tracker](http://wiki.ros.org/openni_tracker), the main skeleton tracking for ROS 

## Details  

* The music stand has one spherical joint and seven revolute joints, so in total 10 degrees of freedom. The spherical joint links the body of the music stand and one of its legs.

  The [URDF](http://wiki.ros.org/urdf) of the character model was written in [my_robot.urdf](https://github.com/YunchuLiu/Human-Character-Mapping/blob/master/urdf/my_robot.urdf). The spherical joint was created by chaining three revolute joints together. Between every two joints, a 'virtual link' was placed, which can just has a name without other parameters.  
  
  The URDF can be visualized in [RViz](http://wiki.ros.org/rviz), the 3D visualization environment for [ROS](http://www.ros.org/about-ros). Setting the value of parameters `gui` to 1 and `self_joint_publisher` to 0 by the following command line:
  
  `roslaunch human_char_mapping myrobot.launch gui:=1 self_joint_publisher:=0`
  
  A GUI will pop up that allows controlling the values of all the non-fixed joints. 
  
<div style="text-align:center">

<img src ="/Portfolio//projects/urdf.png" />

</div>
  
* Projection of NITE transform data onto the human model.
  
  The joint angle of a revolute joint such as the angle of the left elbow was decided by: 
  
  ![Alt text](/Portfolio//projects/formula.png)

  where `Vse` is the vector from the left shoulder to elbow, and `Veh` is the vector from the left elbow to hand.
  Using [TransformListener](http://wiki.ros.org/tf/Overview/Using%20Published%20Transforms), vectors were obtained by calling `lookupTransform()` from `target_frame` to `source_frame`
   
  Three Euler angels for the spheical joint were derived from the NITE rotation data between `/right_elbow` and `/right_shoulder` Since the original data from TransformListener is in Quaternion, the [Transformations.py](https://github.com/ros/geometry/blob/hydro-devel/tf/src/tf/transformations.py) module was used for conversion. 
   
* Mapping from human joint angles to character joints is illustrated in the following sketch. The joint connecting Link 3 and link 7 is a spherical joint and the rest are revolute joints. 
  
  The real-time mapping was completed in [first.py](https://github.com/YunchuLiu/Human-Character-Mapping/blob/master/src/first.py) The utility functions can be sourced in [utility.py](https://github.com/YunchuLiu/Human-Character-Mapping/blob/master/src/utility.py). Once the calibration is completed, typing `roslaunch human_char_mapping myrobot.launch` in another terminal, an RViz will pop up and allows the user to visualize the animation.  
  
<div style="text-align:center">

<img src ="/Portfolio//projects/mapping.png" />

</div>

* The system was developed in ROS using Python on Linux platform. The code can be found in this [repository](https://github.com/YunchuLiu/Human-Character-Mapping)
 on GitHub. 
  
  
## Future work  

* Map all degrees of human model to a human-like character
* Animate mapping (Right now mannually) 
* Topology mapping optimization
* Gesture recognition 


