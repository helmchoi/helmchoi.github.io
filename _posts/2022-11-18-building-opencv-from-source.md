---
layout: post
title:  Building OpenCV from source (Ubuntu 18.04)
categories: Notes
---

Refer to: https://jdu-stuff.tistory.com/74

```
cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local -D BUILD_WITH_DEBUG_INFO=OFF -D BUILD_EXAMPLES=ON -D BUILD_opencv_python3=ON -D INSTALL_PYTHON_EXAMPLES=ON -D OPENCV_ENABLE_NONFREE=ON -D OPENCV_EXTRA_MODULES_PATH=../opencv_contrib-4.0.0/modules -D OPENCV_GENERATE_PKGCONFIG=ON -D WITH_TBB=ON ../opencv-4.0.0/
```
