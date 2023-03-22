---
layout: post
title: "OpenCV findHomography()"
author: "wano"
excerpt_separator: <!--more-->
tags: ['opencv', 'dev']
use_math: true
lastmode: 2023-03-23 00:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

A minor issue in OpenCV's findHomography() function<!--more-->

The findHomography() function takes a pair of point sets as input and outputs a 3 by 3 matrix that can be used to transform the first set of points into the second set.

If a singular case occurs, the findHomography() function returns a 0 by 0 matrix as the output.

As a result, when the function returns a 0 by 0 matrix in the singular case, printing its rows or columns will naturally output 0.

However, the dims value in this case is not 0.

Therefore, it is not recommended to use dims to check for singularity in this function.

When checking if a matrix is valid in OpenCV, it is generally recommended to use the empty() function instead of relying on rows, cols, or dims.