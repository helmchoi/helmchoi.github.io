---
layout: post
title:  Building a custom cv_bridge
categories: Notes
---

## Building a custom cv_bridge (ROS melodic)

In ROS melodic, the default version of OpenCV is 3.2, and using cv_bridge that comes with ROS together with another version of OpenCV (e.g., 4.0.0) causes error.
Although many OpenCV functions still work with this mismatch, some others do not.
In my case, I needed to use OpenCV 4.0.0 for line detector, and the error came from it while other image subscription and imshow worked okay.
The error was resolved by installing cv_bridge from a Github source (vision_opencv: https://github.com/ros-perception/vision_opencv) with OpenCV 4.0.0 instead of installing cv_bridge with something like ros-melodic-cv-bridge.

## Install
First install OpenCV version of your interest.
I removed all OpenCV packages (I had 3.2 & 4.0) and reinstalled 4.0.

```
cd
mkdir cvbridge_ws & cd cvbridge_ws
mkdir src
catkin init
cd src
git clone -b melodic https://github.com/ros-perception/vision_opencv.git
cd ..
catkin build cv_bridge
source devel/setup.bash --extend
```
(Referred to: https://velog.io/@openjr/ROS-Melodic-Python3-CvBridge-%EB%B9%8C%EB%93%9C)

[CAUTION] Some changes have to be made on the repository to use it with OpenCV 4. Follow: https://github.com/ros-perception/vision_opencv/issues/272#issuecomment-471311300
