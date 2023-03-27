---
layout: post
title: "OpenCV & Ceres Solver"
author: "wano"
excerpt_separator: <!--more-➜
tags: ['dev', 'opencv', 'ceres', 'eigen3', 'openexr', 'suitesparse']
use_math: true
lastmode: 2023-03-25 04:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

The Journey to Install OpenCV & Ceres Solver on Windows<!--more-➜

### CUDA with cuDNN

Please refer to other resources regarding CUDA installation. After installation, add the environment variable below to the system environment variables.

[Variable name] CUDA_PATH_V11_6  
[Variable value] C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.6

[Variable name] CUDA_PATH  
[Variable value] $(CUDA_PATH_V11_6)

### Visual Studio (MSVC)

Please refer to other resources regarding MSVC installation.

### CMake

1. Download cmake-3.23.1-windows-x86_64.msi file from [https://cmake.org](https://cmake.org).
2. Run it as an administrator.

### Eigen3

Eigen3 is a header only library, there is no need to build/install Eigen3 to use it if you include it manually. So you don't need to add any path related to it in MSVC's "Additional Libraries Directory". Just add the path that includes its header files to MSVC's "Additional Include Directories". However, we should to build and install it so that other 3rd party libraries that will be installed later know the existence of Eigen3.

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

8. You can see that the files are created in "C:\tmp\built". (Here, "unsupported" directory means the codes that is no longer supported because development has stopped.)

9. Copy:
* "C:\tmp\built\include\eigen3\Eigen" directory ➜ "$(DIBLAT_PATH)\extern\include\Eigen".

10. Open DisableStupidWarnings.h and replace all occurrences of "diag_suppress" with "nv_diag_suppress".

### zlib

1. Download zlib1213.zip file from GitHub and unzip it to "C:\tmp\Imath-main".

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

9. Copy:
* "C:\tmp\built\include\zlib" directory ➜ "$(DIBLAT_PATH)\extern\include\zlib"
* "C:\tmp\built\lib*.lib" files ➜ "$(DIBLAT_PATH)\extern\lib".
* "C:\tmp\built\bin*.dll" files ➜ "$(DIBLAT_PATH)\extern\bin".
* "C:\tmp\built\bin\Release*.exe" files ➜ "$(DIBLAT_PATH)\extern\bin".

### Imath

1. Download Imath-main.zip file from GitHub and unzip it to "C:\tmp\zlib-1.2.13".

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

9. Copy:
* "C:\tmp\built\include\Imath" directory ➜ "$(DIBLAT_PATH)\extern\include\Imath"
* "C:\tmp\built\lib*.lib" files ➜ "$(DIBLAT_PATH)\extern\lib".
* "C:\tmp\built\bin*.dll" files ➜ "$(DIBLAT_PATH)\extern\bin".

### OpenEXR

The math library used by OpenEXR has been changed from IlmBase to Imath.
To specify this, you must use cmake in the Command Prompt instead of CMake-gui.

1. Download openexr-main.zip file from GitHub and unzip it to "C:\tmp\openexr-main".

2. In the the Command Prompt:
* cd C:\tmp\openexr-main
* mkdir build
* cd build
* cmake -G"Visual Studio 17 2022" -A x64 -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=C:\tmp\built -DZLIB_ROOT=C:\tmp\built\include\zlib -DILMBASE_PACKAGE_PREFIX=C:\tmp\built ..
* cmake --build . --config Release
* cmake --install .

3. Copy:
* "C:\tmp\built\include\OpenEXR" ➜ "$(DIBLAT_PATH)\extern\include\OpenEXR"
* "C:\tmp\built\lib*.lib" files ➜ "$(DIBLAT_PATH)\extern\lib".
* "C:\tmp\built\bin*.dll" files ➜ "$(DIBLAT_PATH)\extern\bin".
* "C:\tmp\built\bin*.exe" files ➜ "$(DIBLAT_PATH)\extern\bin".

### NASM

1. Download nasm-2.15.05-installer-x64.exe file from https://www.nasm.us.
2. Run it as an administrator.
3. After installation, add the following path to the Path environment variable.
* C:\Program Files\NASM (The path where nasm.exe exists)

### OpenCV

1. Download opencv-4.x.zip file from GitHub and unzip it to "C:\tmp\opencv-4.x".

2. Download opencv_contrib-4.x.zip file from GitHub and unzip it to "C:\tmp\opencv_contrib-4.x".

3. In CMake-gui:
* Specify the directory where the source code is located. We'll refer to it as {source}.
* Specify the directory where the binary will be created. We'll refer to it as {build} = {source}\build.

4. Click "Configure" button.
* Visual Studio 17 2022
* Use default native compilers

5. Specify the appropriate options. Please refer to the captured PNG file for details.

6. Click "Generate" button.

7. Click "Open Project" button.

8. Build "OpenCV" solution inside MSVC.

9. You can see that the files are created in "C:\tmp\built".

10. Copy:
* "C:\tmp\built\include\opencv2" directory ➜ "$(DIBLAT_PATH)\extern\include\opencv2"
* "C:\tmp\built\x64\vc17\lib*.lib" files ➜ "$(DIBLAT_PATH)\extern\lib".
* "C:\tmp\built\x64\vc17\bin*.dll" files ➜ "$(DIBLAT_PATH)\extern\bin".
* "C:\tmp\built\x64\vc17\bin*.exe" files ➜ "$(DIBLAT_PATH)\extern\bin".

### gflags (formerly Google Commandline Flags)

1. Download gflags-master.zip file from GitHub and unzip it to “C:\tmp\gflags-master”.

2. In CMake-gui:
* Specify the directory where the source code is located. We’ll refer to it as {source}.
* Specify the directory where the binary will be created. We’ll refer to it as {build} = {source}\mybuild. (due to “BUILD” file already exists.)

3. Click “Configure” button.
* Visual Studio 17 2022
* Use default native compilers

4. Specify the appropriate options. Please refer to the captured PNG file for details.

5. Click “Generate” button.

6. Click “Open Project” button.

7. Build “INSTALL” project in release mode inside MSVC.

8. You can see that the files are created in “C:\tmp\built”.

9. Copy:
* “C:\tmp\built\include\gflags” directory ➜ “$(DIBLAT_PATH)\extern\include\gflags”
* “C:\tmp\built\lib*.lib” files ➜ “$(DIBLAT_PATH)\extern\lib”
* “C:\tmp\built\bin*.dll” files ➜ “$(DIBLAT_PATH)\extern\bin”

### glog (Google Logging Library)

1. Download glog-master.zip file from GitHub and unzip it to "C:\tmp\glog-master".

2. In CMake-gui:
* Specify the directory where the source code is located. We'll refer to it as {source}.
* Specify the directory where the binary will be created. We'll refer to it as {build} = {source}\build.

3. Click "Configure" button.
* Visual Studio 17 2022
* Use default native compilers

4. Specify the appropriate options. Please refer to the captured PNG file for details.

5. Click "Generate" button.

6. Click "Open Project" button.

7. Build "INSTALL" project in release mode inside MSVC.

8. You can see that the files are created in "C:\tmp\built".

9. Copy:
* "C:\tmp\built\include\glog" directory ➜ "$(DIBLAT_PATH)\extern\include\glog"
* "C:\tmp\built\lib*.lib" files ➜ "$(DIBLAT_PATH)\extern\lib"
* "C:\tmp\built\bin*.dll" files ➜ "$(DIBLAT_PATH)\extern\bin"

### SuiteSparse

1. Download suitesparse-metis-for-windows-master.zip file from GitHub and unzip it to "C:\tmp\suitesparse-metis-for-windows-master".

2. In CMake-gui:
* Specify the directory where the source code is located. We'll refer to it as {source}.
* Specify the directory where the binary will be created. We'll refer to it as {build} = {source}\build.

3. Click "Configure" button.
* Visual Studio 17 2022
* Use default native compilers

4. Specify the appropriate options. Please refer to the captured PNG file for details.

5. Click "Generate" button.

6. Click "Open Project" button.

7. Build "INSTALL" project in release mode inside MSVC.

8. You can see that the files are created in "C:\tmp\built".

9. Copy:
* "C:\tmp\built\include\suitesparse" directory ➜ "$(DIBLAT_PATH)\extern\include\suitesparse"
* "C:\tmp\built\lib*.lib" files ➜ "$(DIBLAT_PATH)\extern\lib"
* "C:\tmp\built\bin*.dll" files ➜ "$(DIBLAT_PATH)\extern\bin"

### Ceres Solver

CMake-gui does not find the already installed CXSparse and SuiteSparse. So I'll use the Command Prompt.

1. Download ceres-solver-2.1.0.tar.gz file from https://ceres-solver.googlesource.com/ceres-solver.

2. Unzip it by "tar xvfz ceres-solver-2.1.0.tar.gz" in the Prompt Command.

3. Move the create directory to "C:\tmp\ceres-solver-2.1.0".

4. In the the Command Prompt:
* cd C:\tmp\ceres-solver-2.1.0
* mkdir mybuild (due to "BUILD" file already exists.)
* cd mybuild
* cmake ..
* cmake --build . --config Release
* cmake --install .

5. Copy:
* "C:\tmp\built\include\ceres" directory ➜ "$(DIBLAT_PATH)\extern\include\ceres"
* "C:\tmp\built\lib*.lib" files ➜ "$(DIBLAT_PATH)\extern\lib"
* "C:\tmp\built\bin*.dll" files ➜ "$(DIBLAT_PATH)\extern\bin"

---

If some errors occur while building your source code by linking the Ceres library as shown below,
change "SDL checks" to "No(/sdl-)".

* C4996 'ceres::GradientProblem::parameterization_'
* C4996 'ceres::LocalParameterization': LocalParameterizations will be removed from the Ceres Solver API in version 2.2.0. Use Manifolds instead.
* C4996 'j0': The POSIX name for this item is deprecated. Instead, use the ISO C and C++ conformant name: _j0. See online help for details.

<center><img src="https://cgvfxmath.github.io/assets/img/opencv_ceres_01.png" width="80%"></center>
<center><img src="https://cgvfxmath.github.io/assets/img/opencv_ceres_02.png" width="80%"></center>

SDL check is a setting to improve program security. When SDL is set, only functions with enhanced security can be used. If functions that can cause security problems are used, they are treated as errors, not warnings, and compilation stops. For example, when using SDL, scanf_s should be used instead of scanf.