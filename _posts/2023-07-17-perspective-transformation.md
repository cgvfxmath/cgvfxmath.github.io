---
layout: post
title: "Perspective Transformation"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev', 'math', 'opencv']
use_math: true
lastmode: 2023-07-17 11:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Image distortion and perspective adjustment technique used in computer vision and graphics<!--more-->

ChatGPT는 perspective transformation에 대해서 다음과 같이 설명합니다.

퍼스펙티브 변환(Perspective Transformation)은 컴퓨터 비전과 그래픽스 분야에서 사용되는 기술로, 이미지나 영상의 투시 변환을 수행하는 방법입니다. 이 변환은 이미지의 원근감을 조정하거나, 물체를 다른 시각으로 보이게 하거나, 평면 이미지를 3D 공간으로 매핑하는 등 다양한 응용에 사용됩니다.

퍼스펙티브 변환은 일반적으로 이미지의 네 개의 코너 지점을 기준으로 수행됩니다. 변환 과정에서는 원근 효과를 모방하기 위해, 각각의 코너 지점을 이용하여 이미지를 변환합니다. 이 때, 원근감을 조절하거나 물체의 왜곡을 수정하기 위해 코너 지점들을 이동, 회전 및 스케일링합니다.

퍼스펙티브 변환은 주로 컴퓨터 비전 분야에서 사용되며, 이미지 정합, 객체 추적, 영상 합성 등 다양한 응용 분야에서 활용됩니다. 또한, 컴퓨터 그래픽스에서도 3D 장면을 2D 이미지로 투영하는 과정에서 사용되며, 가상 현실(VR), 증강 현실(AR) 등의 기술 개발에도 적용됩니다.

요약하면, 퍼스펙티브 변환은 이미지나 영상의 원근감을 조정하거나, 물체의 형태를 왜곡시키는 등 다양한 변형을 적용하는 기술입니다. 이를 통해 시각적 효과를 개선하거나, 물체의 위치와 모양을 조정하여 다양한 응용 분야에서 활용할 수 있습니다.

---

다음은 정사각형 형태의 텍스쳐입니다.

<center>
  <figure>
    <img src="https://cgvfxmath.github.io/assets/img/perspective_transformation_01.jpg">
  </figure>
</center>

위의 텍스쳐를 정사각형 평면에 매핑(mapping)하여 가상의 카메라로 렌더링하는 모습은 다음과 같습니다.

<center>
  <figure>
    <img src="https://cgvfxmath.github.io/assets/img/perspective_transformation_02.jpg">
  </figure>
</center>

다음은 렌더링한 결과 이미지입니다.

<center>
  <figure>
    <img src="https://cgvfxmath.github.io/assets/img/perspective_transformation_03.jpg">
  </figure>
</center>

다음은 원본 정사각형을 복구하기 위해서 네 개 코너 지점의 좌표값을 지정한 결과입니다.

<center>
  <figure>
    <img src="https://cgvfxmath.github.io/assets/img/perspective_transformation_04.jpg">
  </figure>
</center>

다음은 원래의 정사각형으로 복원한 결과입니다.

<center>
  <figure>
    <img src="https://cgvfxmath.github.io/assets/img/perspective_transformation_05.jpg">
  </figure>
</center>

이와 같은 결과를 만드는 코드는 다음과 같습니다.

```python
import cv2
import numpy as np

img = cv2.imread('rendered.jpg')

pts1 = np.float32([[140,198], [361,587], [706,421], [490,91]])

width, height = 800, 800
pts2 = np.float32([[0,0], [0,height], [width,height], [width,0]])

matrix = cv2.getPerspectiveTransform(pts1, pts2)
imgOutput = cv2.warpPerspective(img, matrix, (width, height))
cv2.imwrite('restored.jpg', imgOutput)
cv2.waitKey(0)
```



