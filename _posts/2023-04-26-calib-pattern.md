---
layout: post
title: "Camera Calibration Pattern"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev']
use_math: true
lastmode: 2023-04-26 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

How to generate a calibration pattern image for both Chessboard and ChArUco<!--more-->

```python
import cv2
import numpy as np

def create_calibration_pattern_image(cols, rows, img_width, img_height, aruco_type=cv2.aruco.DICT_6X6_250):
    # chessboard pattern
    if aruco_type == None:
        chessboard = np.zeros((rows, cols), dtype=np.uint8) # black
        chessboard[1::2, ::2] = 255 # white for odd column & even row
        chessboard[::2, 1::2] = 255 # white for even row & odd column
        img = cv2.resize(chessboard, (img_height, img_width), interpolation=cv2.INTER_NEAREST)
    # charuco pattern
    else:
        dict = cv2.aruco.getPredefinedDictionary(aruco_type)
        board = cv2.aruco.CharucoBoard((cols, rows), 1.0, 0.5, dict)
        img = board.generateImage((img_height, img_width))
    img = cv2.cvtColor(img, cv2.COLOR_GRAY2BGR)
    return img
```

<center>
  <figure>
    <img src="https://cgvfxmath.github.io/assets/img/calib_pattern.jpg">
  </figure>
</center>




