# RoboRacing Software [![CircleCI](https://circleci.com/gh/RoboJackets/roboracing-software.svg?style=svg)](https://circleci.com/gh/RoboJackets/roboracing-software)

![alt text](https://raw.githubusercontent.com/wiki/RoboJackets/roboracing-software/images/RaceCar.JPG "Picture of first RoboRacing car.")

This repository contains [ROS](http://ros.org) packages for the [RoboJackets](http://robojackets.org) RoboRacing team.

## Organization

Most folders in this repository are ROS packages.

**avc**: This package contains intelligence code for the [Sparkfun Autonomous Vehicle Challenge](http://avc.sparkfun.com).

**iarrc**: This package contains intelligence code for the [International Autonomous Robot Racing Challenge](http://robotracing.wordpress.com).

**rr_description**: This package contains URDFs and meshes that describe the platform's layout.

**rr_gazebo**: This package contains resources for running the car in the [Gazebo](http://gazebosim.org) simulator.

**rr_platform**: This package contains code for interfacing with the various cars built and maintained by the team.

**sandbox**: This package contains utilities and non-ROS code. This includes tools for working with log files and the Arduino code for the car.

The following files and folders enable our continuous integration system.

* external
* util
* circle.yml
* config.docif

## Installation

1. Make sure you have the appropriate ROS version installed for your version of Ubuntu.

2. Clone this repo into the _src_ directory of your catkin workspace.

3. Unfortunately, some dependecies have to be installed manually.
   1. libuvc - for accessing generic USB Cameras
   
      From your home directory, or wherever you feel like keeping the libuvc source   
      ```
      git clone git@github.com:ktossell/libuvc.git
      cd libuvc
      mkdir build && cd build
      make && sudo make install
      ```
   2. libuvc_ros - ROS API for libuvc
   
      From within the `src` directory of your catkin workspace,
      ```
      git clone git@github.com:ktossell/libuvc_ros.git
      ```
  
4. Install the remaining dependencies with the following command in your catkin workspace folder:

   ```
   rosdep install --from-path src --ignore-src -y
   ```
    
5. You should now be able to build the project with `catkin_make`.

## Simulation

You can get started with the RoboRacing code base right away by launching our simulator!

The following command will load our platform in the Sparkfun AVC track:
```
roslaunch rr_gazebo speedi_avc.launch
```
Then, the following command will start our race AI and drive the car around the track:
```
roslaunch avc avc.launch
```
Alternatively, you can control the car manually with a USB gamepad with this command:
```
roslaunch rr_platform joystick_driver.launch
```