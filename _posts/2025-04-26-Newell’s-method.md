---
layout: post
title: "Newell’s Method"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2025-04-25 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Fast Polygon Normal Calculation<!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요. (➔[How-To](https://cgvfxmath.github.io/2023-03-18/math-renderer))*

다음 그림과 같이 네 점 $\mathbf{P}_1$, $\mathbf{P}_2$, $\mathbf{P}_3$, $\mathbf{P}_4$로 구성되는 3차원 공간상의 사각형이 있다고 가정해 보겠습니다.

<center><figure><img src="https://cgvfxmath.github.io/assets/img/newell01.jpg" width="50%"></figure></center>

단, 위 수식에서 $N=4$이고, $(x_{N+1},y_{N+1},z_{N+1})=(x_{1},y_{1},z_{1})$를 의미합니다.

뉴웰 방법은 주어진 다각형의 법선 벡터의 각 성분은 각 2차원 평면으로 투영한 다각형의 넓이에 비례한다는 사실에 기반합니다. 즉, 주어진 다각형의 법선 벡터 다음과 같습니다.

<p style="text-align: center;">$\overrightarrow{\mathbf{M}}=(A_{yz},A_{zx}, A_{xy})\;\;\;\Longrightarrow\;\;\;\overrightarrow{\mathbf{N}}=\frac{\overrightarrow{\mathbf{M}}}{\Vert \overrightarrow{\mathbf{M}} \Vert}$</p>

 Q.E.D.


