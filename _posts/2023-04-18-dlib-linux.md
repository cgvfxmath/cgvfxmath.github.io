---
layout: post
title: "How to install Dlib on Linux"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev', 'linux']
use_math: true
lastmode: 2023-04-18 09:00:00
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

AVX는 "Advanced Vector Extensions"의 약자로, 인텔(Intel)이 개발한 명령어 집합(Instruction Set) 중 하나입니다. 이는 인텔 프로세서에서 벡터화 연산(vectorized operation)을 보다 효율적으로 처리하기 위해 개발된 기술입니다.

AVX는 이전의 SSE(SIMD Extensions) 기술보다 더 긴 벡터를 지원하여, 단일 명령어로 여러 데이터 요소를 처리할 수 있습니다. 이를 통해 프로세서의 성능을 향상시키고, 계산 시간을 단축시킬 수 있습니다.

AVX는 주로 과학 계산, 그래픽 처리, 멀티미디어 애플리케이션 등에서 활용됩니다. 또한, 인텔의 최신 프로세서에서는 AVX-512라는 더 발전된 형태의 AVX 기술을 지원하여, 더 많은 데이터 요소를 한 번에 처리할 수 있습니다.
