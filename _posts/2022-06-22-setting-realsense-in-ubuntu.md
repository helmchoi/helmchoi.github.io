---
layout: post
title:  Setting Realsense in Ubuntu
categories: Notes
---

Setting Realsense with ROS in Ubuntu 16.04, ROS Kinetic 

## 1. Installing librealsense
follow
https://github.com/IntelRealSense/librealsense/blob/master/doc/distribution_linux.md
[Note] if librealsense-ros to be installed, install dev/debug packages!

## 2. Installing ROS Wrapper for Realsense
follow (step 3~)
https://github.com/IntelRealSense/realsense-ros

[Possible Errors] after cmake..
### 2-1) ddynamic-reconfigure
```
Could not find the required component 'ddynamic_reconfigure'. The following CMake error indicates that you either need to install the package with the same name or change your environment so that it can be found.
CMake Error at /opt/ros/kinetic/share/catkin/cmake/catkinConfig.cmake:83 (find_package):
  Could not find a package configuration file provided by
  "ddynamic_reconfigure" with any of the following names:

    ddynamic_reconfigureConfig.cmake
    ddynamic_reconfigure-config.cmake

  Add the installation prefix of "ddynamic_reconfigure" to CMAKE_PREFIX_PATH
  or set "ddynamic_reconfigure_DIR" to a directory containing one of the
  above files.  If "ddynamic_reconfigure" provides a separate development
  package or SDK, be sure it has been installed.
Call Stack (most recent call first):
  realsense-ros/realsense2_camera/CMakeLists.txt:11 (find_package)


-- Configuring incomplete, errors occurred!
See also "/home/pmi/catkin_ws/build/CMakeFiles/CMakeOutput.log".
See also "/home/pmi/catkin_ws/build/CMakeFiles/CMakeError.log".
Invoking "cmake" failed
```
#### ==> Solution
install ddynamic_reconfigure
```
sudo apt install ros-kinetic-ddynamic-reconfigure
```
If it does not work, clone from Github to catkin_ws/src:
```
git clone https://github.com/pal-robotics/ddynamic_reconfigure.git
```


### 2-2) librealsense2 not found error (although it is installed)
```
CMake Warning at realsense-ros/realsense2_camera/CMakeLists.txt:44 (find_package):
  By not providing "Findrealsense2.cmake" in CMAKE_MODULE_PATH this project
  has asked CMake to find a package configuration file provided by
  "realsense2", but CMake did not find one.

  Could not find a package configuration file provided by "realsense2"
  (requested version 2.50.0) with any of the following names:

    realsense2Config.cmake
    realsense2-config.cmake

  Add the installation prefix of "realsense2" to CMAKE_PREFIX_PATH or set
  "realsense2_DIR" to a directory containing one of the above files.  If
  "realsense2" provides a separate development package or SDK, be sure it has
  been installed.


CMake Error at realsense-ros/realsense2_camera/CMakeLists.txt:48 (message):
  

  

   Intel RealSense SDK 2.0 is missing, please install it from https://github.com/IntelRealSense/librealsense/releases
```
#### ==> Solution

Install developer packages of librealsense (https://github.com/IntelRealSense/librealsense/blob/master/doc/distribution_linux.md)


## 3. Pyrealsense2
```
pip install pyrealsense2
```
