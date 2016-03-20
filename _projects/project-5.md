---
layout: project
title: Human Character Mapping
date: 1/2015 to 03/2015
image: human_char.png
---

## Overview

The goal of this project is to leverage OpenNI skeleton data from Kinect to map human motion to a rigid body character 

<iframe width="560" height="315" src="https://www.youtube.com/embed/m98IJ71wfu0" frameborder="0" allowfullscreen></iframe>

### Details 

* The music stand has one spherical joint and seven revolute joints, so in total 10 degrees of freedom. The spherical joint connects the body link and one of the three legs.

  The URDF of the character model was built in RViz. 

  ![Alt text](/Portfolio//projects/urdf.png)

* Projection of NITE transform data onto the human model.
  
  Every joint angle of a revolute joint was calculated using NITE translation data from three relevant frames. 
  
  Three Euler angels for the spheical joint were derived from the NITE rotation data between `/right_elbow` and `/right_shoulder` 

* Mapping from human joint angles to character joints is illustrated in the following sketch:

  The joint connecting Link 3 and link 7 is a spherical joint and all the others are revolute joint. 

  ![Alt text](/Portfolio//projects/mapping.png)

* The system was developed in ROS using Python on Linux platform. The code can be found in this [repository](https://github.com/YunchuLiu/Human-Character-Mapping)
 on GitHub. 
  
  
### Future work  

* Map all degrees of human model to a human-like character
* Animate mapping (Right now mannually) 
* Topology mapping optimization
* Gesture recognition 


