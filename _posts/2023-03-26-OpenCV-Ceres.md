---
layout: post
title: "OpenCV & Ceres Solver"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev', 'opencv', 'ceres', 'eigen3', 'openexr', 'suitesparse']
use_math: true
lastmode: 2023-03-25 04:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

The Journey to Install OpenCV & Ceres Solver on Windows<!--more-->

### CUDA with cuDNN

Please refer to other resources regarding CUDA installation. After installation, add the environment variable below to the system environment variables.

[Variable name] CUDA_PATH_V11_6
[Variable value] C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.6

[Variable name] CUDA_PATH
[Variable value] $(CUDA_PATH_V11_6)