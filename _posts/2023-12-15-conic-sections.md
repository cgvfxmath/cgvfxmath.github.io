---
layout: post
title: "Conic Sections"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2023-12-15 11:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Curves obtained from a cone's surface intersecting a plane <!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요. (➔[How-To](https://cgvfxmath.github.io/2023-03-18/math-renderer))*

다음 그림과 같이 원뿔을 임의의 평면으로 잘랐을 때 얻어지는 곡선을 이차곡선(또는 원뿔곡선 또는 원추곡선)이라고 부릅니다. 이렇게 얻어지는 곡선의 종류로는 원(circle), 타원(ellipse), 포물선(parabola), 쌍곡선(hyperbola)이 있습니다.

<center><img src="https://cgvfxmath.github.io/assets/img/conic_sections.jpg"></center>

두 변수 $x$와 $y$에 대한 이차다항식의 일반형은 다음과 같습니다.

<p style="text-align: center;">$ax^2 + by^2 + cx + dy + exy + f = 0$</p>

여기서 $xy$항은 편의상 생략하겠습니다. 즉, $e=0$으로 가정하겠습니다. ($xy$항은 축에 정렬되어 있는 이차곡선을 회전시킨 결과로 나타나는 항이기 때문에 이차곡선의 본질과는 직접적으로 관련이 없습니다.)

이때 다음과 같은 조건에 따라 위의 이차곡선 중 하나를 나타내게 됩니다.

1. 원(circle): $a = b$, $ab \neq 0$, $f \neq 0$
2. 타원(ellipse): $a \neq b$, $ab>0$, $f \neq 0$
3. 쌍곡선(hyperbola): $a \neq b$, $ab<0$, $f \neq 0$
4. 포물선(parabola)
	1. 축이 $x$축에 평행한 경우: $a = 0$, $b \neq 0$, $c \neq 0$
	2. 축이 $y$축에 평행한 경우: $a \neq 0$, $b = 0$, $d \neq 0$

그리고 위에서 $c$나 $d$, 또는 $f$가 0이 아닌 경우는 기본 그래프를 $x$축 또는 $y$축으로 평행이동 한 것을 의미합니다. 타원의 경우를 예로 들어 살펴보겠습니다. 중심이 원점에 있고 각 축의 길이가 각각 $2a$와 $2b$인 타원을 나타내는 방정식은 다음과 같습니다.

<p style="text-align: center;">$\frac{x^2}{a^2} + \frac{y^2}{b^2} = 1$</p>

여기서 $x$축으로 $\alpha$만큼, $y$축으로 $\beta$만큼 이동하면 $x$ 대신에 $x-\alpha$, $y$ 대신에 $y-\beta$를 대입하면 되기 때문에 $(x-\alpha)^2$을 전개한 결과로 $x$항이 생기고 $(y-\beta)^2$을 전개한 결과로 $y$항이 생기게 됩니다. 또한 전개하는 과정에서 생성되는 상수항의 계수는 $f$에 영향을 줍니다.