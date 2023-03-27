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

### Visual Studio (MSVC)

Please refer to other resources regarding MSVC installation.

### CMake

1. Download cmake-3.23.1-windows-x86_64.msi file from https://cmake.org.
2. Run it as an administrator.

### Eigen3

Eigen3 is a header only library, there is no need to build/install Eigen3 to use it if you include it manually.
So you don't need to add any path related to it in MSVC's "Additional Libraries Directory".
Just add the path that includes its header files to MSVC's "Additional Include Directories".

However, we should to build and install it so that other 3rd party libraries that will be installed later know the existence of Eigen3.

1. Download eigen-3.4.0.zip file from GitHub and unzip it to "C:\tmp\eigen-3.4.0".

2. In CMake-gui:
* Specify the directory where the source code is located. We'll refer to it as {source}.
* Specify the directory where the binary will be created. We'll refer to it as {build} = {source}\build.

3. Click "Configure" button.
* Visual Studio 17 2022
* Use default native compilers

4. Specify the appropriate options. Please refer to the captured PNG file for details.

5. Click "Generate" button, then you can find Eigen3Config.cmake file in {build} directory.

6. Click "Open Project" button.

7. Build "INSTALL" project inside MSVC.

8. You can see that the files are created in "C:\tmp\built".
(Here, "unsupported" directory means the codes that is no longer supported because development has stopped.)

9. Copy:
* "C:\tmp\built\include\eigen3\Eigen" directory -> "$(DIBLAT_PATH)\extern\include\Eigen".

10. Open DisableStupidWarnings.h and replace all occurrences of "diag_suppress" with "nv_diag_suppress".