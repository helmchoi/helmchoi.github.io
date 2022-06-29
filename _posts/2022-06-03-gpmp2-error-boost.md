---
layout: post
title:  Boost error while installing gpmp2
categories: Notes
---

Ubuntu 18.04

If Boost-related errors occur while installing gpmp2, add following lines to CMakeLists.txt (maybe near Boost-same requirement as gtsam )
```
find_package(Boost COMPONENTS chrono REQUIRED)
find_package(Boost COMPONENTS date_time REQUIRED)
find_package(Boost COMPONENTS timer REQUIRED)
```
