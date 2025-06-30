---
layout: post
title:  Setting ROS2 on Windows 10
categories: Notes
---

Follow the official instruction:
https://docs.ros.org/en/humble/Installation/Windows-Install-Binary.html

Installing binary version is recommended.
Visual Studio Community 2022 also works.

Troubleshooting:
1) asio, cunit, etc. installation error (key exists)
   -> There would be registries left in "HKEY_LOCAL_MACHINE\SOFTWARE\Kitware\CMake\Packages". Remove them and retry.
2) Failed to start process OR rclpy-related error
   -> Python version mismatch. Don't trust the official guideline: the python version should match the version in the zip file (Lib/site-packages/), not 3.8.3. Or could be done by using ROS2 version compiled with python 3.8.3 (e.g., Humble 20240807).
