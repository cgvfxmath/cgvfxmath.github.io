---
layout: post
title: "How to enable C++17 in your MSVC CUDA project"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev', 'visual studio', 'cuda']
use_math: true
lastmode: 2023-04-18 01:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

The way to use C++17 in your MSVC CUDA project<!--more-->

1. Open your CUDA project in Visual Studio.

2. Right-click on your project in the Solution Explorer and select "Properties" from the context menu.

3. In the left-hand pane of the project properties window, select "CUDA C/C++" > "Command Line".

4. Write the following in the additional options.

```ini
-std=c++17 -Xcompiler "/std:c++17"
```

<center><figure><img src="https://cgvfxmath.github.io/assets/img/VC_CUDA_C++17.jpg" width="90%"></figure></center>
<br/>