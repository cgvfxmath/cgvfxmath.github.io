---
layout: post
title: "nvidia-smi vs nvcc -V"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev', 'cuda']
use_math: true
lastmode: 2023-04-18 01:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

How nvidia-smi differs from nvcc -V<!--more-->

*nvidia-smi*는 NVIDIA System Management Interface를 나타내며, GPU에 대한 정보를 제공합니다. 예를 들어 현재 시스템에서 사용 가능한 GPU의 수, GPU의 이름 및 모델, 현재 GPU의 메모리 사용량 등을 확인할 수 있습니다. 또한, nvidia-smi를 사용하여 GPU의 성능, 온도, 전력 소비 등의 정보를 확인할 수도 있습니다.

반면에 *nvcc -V*는 NVIDIA CUDA Compiler version을 나타내며, CUDA 개발을 위해 사용되는 컴파일러의 버전 정보를 확인할 수 있습니다.

즉, *nvidia-smi*는 GPU에 대한 정보를 제공하고, *nvcc -V*는 컴파일러에 대한 정보를 제공합니다.

따라서 두 명령어의 결과에서 나오는 CUDA 버전의 의미하는 바는 다음과 같습니다.
* nvidia-smi: 현재 설치된 드라이버에서 지원하는 최대 CUDA 버전
* nvcc-V: 실제로 설치되어 빌드시 사용되는 CUDA 버전

<center><figure><img src="https://cgvfxmath.github.io/assets/img/nvidia-smi.jpg" width="90%"></figure></center>
<center><figure><img src="https://cgvfxmath.github.io/assets/img/nvcc-V.jpg" width="90%"></figure></center>
<br/>