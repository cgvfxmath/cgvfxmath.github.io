---
layout: post
title: "How to install Dlib on Linux"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev', 'linux']
use_math: true
lastmode: 2023-04-19 09:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Dlib is a C++ library used for computer vision, image processing, and machine learning applications, providing functionalities such as face detection and facial landmark recognition.<!--more-->

You can download “dlib-19.16.tar.bz2” at [http://dlib.net](http://dlib.net).

```bash
tar xvf dlib-19.16.tar.bz2
cd dlib-19.16
python setup.py install
```

---
## **How to build shared library**

```bash
mkdir shared_build
cd shared_build
cmake -DBUILD_SHARED_LIBS=1 -DUSE_AVX_INSTRUCTIONS=ON ..
cmake –build . –config Release
make install
```

AVX works on processors released after 2011, which is the fastest one.   
SSE2 works for most Intel or AMD chips: -DUSE_SSE2_INSTRUCTIONS=ON   
SSE4 works for most current machines: -DUSE_SSE4_INSTRUCTIONS=ON   

---
## **How to check my CPU supports AVX/AVX2 on Linux**

```bash
grep avx /proc/cpuinfo
grep avx2 /proc/cpuinfo
```
