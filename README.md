# CART SLAM System
## Campus Autonomous Robot Tours SLAM System
This project is a SLAM subsystem that can run as a payload on a mobile platform such as the Clearpath Husky or Boston Dynamics Spot that can be used to aid in giving a virtual tour of the CSUN Campus. The SLAM subsystem is responsible for creating a realtime map as the mobile robot moves through the environment.

## Current State
Currently, the full SLAM system runs from a Docker container created by Nvidia and customized by us to use the latest version of certain software packages. 
  
**Hardware:**  
- Jetson Nano 4GB version
- Intel Realsense D455  
  
**Software for performing SLAM:**
- librealsense sdk built with CUDA support to allow for faster processing of D455 images. (Biggest performance boost thus far)
- realsense-ros for ROS 2 foxy to interface D455 with ROS 2
- rtabmap and rtabmap-ros which is what actually performs SLAM
- imu_filter_madgwick for ROS 2 to aid in odometry using D455 on-board IMU

**Other Software**
- JetPack Version 4.6.1 https://developer.nvidia.com/embedded/jetpack-sdk-461
- ROS 2 Foxy (running inside a docker container) https://github.com/dusty-nv/jetson-containers

