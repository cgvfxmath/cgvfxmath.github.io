---
layout: post
title: "Prism & Pyramid"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2024-02-07 11:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

The reason why the volume of a pyramid is one-third of that of a prism <!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요. (➔[How-To](https://cgvfxmath.github.io/2023-03-18/math-renderer))*

다음 그림과 같이 밑면의 가로와 세로 길이, 그리고 높이가 각각 $a$, $b$, $h$인 일반적인 사각기둥과 사각뿔이 있다고 생각해 보겠습니다.

<center><img src="https://cgvfxmath.github.io/assets/img/prism_pyramid_01.jpg"></center>

이 사각기둥과 사각뿔의 부피는 다음과 같습니다.

* 사각기둥의 부피: $V_{prism} = a \times b \times h$</p>

* 사각뿔의 부피: $V_{pyramid} = \frac{1}{3} \times a \times b \times h$</p>

즉, 사각기둥의 부피와 사각뿔의 부피 사이에는 다음과 같은 관계식이 성립합니다.

<p style="text-align: center;">$V_{prism} = \frac{1}{3} V_{pyramid}$</p>

여기서 1/3이라는 수가 어떻게 나왔는지는, 정적분을 이용하면 깔끔하게 증명할 수 있습니다. 하지만 여기서는 적분을 사용하지 않고 증명을 해보겠습니다.

앞의 공식처럼 사각뿔의 부피 공식은 다음과 같습니다.

<p style="text-align: center;">$\frac{1}{3} \times$ (밑면의 넓이) $\times$ (높이)</p>

따라서, 다음 두 사각뿔의 부피는 같습니다.

<center><img src="https://cgvfxmath.github.io/assets/img/prism_pyramid_02.jpg"></center>

즉, 형태가 다르더라도 밑면의 넓이와 높이가 같으면 두 사각뿔의 부피는 동일합니다.

이것은 다음 그림과 같이 사각뿔을 잘게 슬라이스(slice) 내어서 수평방향으로 이동한 결과이기 때문이라고 직관적으로 이해할 수도 있습니다.

<center><img src="https://cgvfxmath.github.io/assets/img/prism_pyramid_03.jpg"></center>


