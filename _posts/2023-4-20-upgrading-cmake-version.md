---
layout: post
title:  Upgrading CMake version in Ubuntu (18.04)
categories: Notes
---

In case of using ROS, one may not remove CMake to reinstall it, since doing so blows up some part of ROS.
The following is an alternative, which overrides existing one.
Everytime the new CMake version is used the 'export' commands must be preceeded.

```
cd ~/Downloads/cmake-x.xx.x/
./bootstrap --prefix=$HOME/cmake-install
make
make install
export PATH=$HOME/cmake-install/bin:$PATH
export CMAKE_PREFIX_PATH=$HOME/cmake-install:$CMAKE_PREFIX_PATH
```

Reference: [https://github.com/colmap/colmap/issues/188#issuecomment-447265919](https://answers.ros.org/question/293119/how-can-i-updateremove-cmake-without-partially-deleting-my-ros-distribution/?answer=297523#post-id-297523)
