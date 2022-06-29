---
layout: post
title:  Installing GTSAM in Ubuntu 18.04
categories: Notes
---

## GTSAM install in Anaconda virtual environment
```
git clone [repository]
cd gtsam
git checkout wrap-export
mkdir build && cd build
cmake .. -DGTSAM_ALLOW_DEPRECATED_SINCE_V4=0
```
