---
layout: post
title:  Installing COLMAP in Ubuntu (18.04)
categories: Notes
---

Follow instructions of https://colmap.github.io/install.html

[Error] If colmap_exe related error occurs like
```
CMake Warning at cmake/CMakeHelper.cmake:160 (add_executable):
  Cannot generate a safe runtime search path for target colmap_exe because
  files in some directories may conflict with libraries in implicit
  directories:

    runtime library [libgmp.so.10] in /usr/lib/x86_64-linux-gnu may be hidden by files in:
      /home/hyelim/anaconda3/lib

  Some of these libraries may not be found correctly.
Call Stack (most recent call first):
  src/exe/CMakeLists.txt:38 (COLMAP_ADD_EXECUTABLE)
```
this is a Qt issue, and setting the Qt path right resolves it.
Add `SET(CMAKE_PREFIX_PATH "/usr/lib/x86_64-linux-gnu/cmake")` to CMakeLists.txt in colmap folder.

Reference: https://github.com/colmap/colmap/issues/188#issuecomment-447265919
