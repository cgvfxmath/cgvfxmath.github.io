---
layout: post
title: "Quadratic Curve #3"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2023-12-18 11:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Hyperbola <!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요.*

쌍곡선의 정의: 두 초점 $\mathbf{F}^{\prime}(-c,0)$, $\mathbf{F}(c,0)$으로부터의 거리의 차가 일정한 점들의 집합

일정한 거리의 차를 $2a$, 쌍곡선 위의 임의의 점을 $\mathbf{P}(x,y)$라 하자.

그러면 다음과 같은 등식이 성립한다.

$| \overline{\mathbf{F}^{\prime}\mathbf{P}} - \overline{\mathbf{FP}} | = 2a$



<p style="text-align: center;">$\sqrt{(x+c)^2+y^2} - \sqrt{(x-c)^2+y^2} = \pm 2a$</p>
<p style="text-align: center;">$\sqrt{x^2+2cx+c^2+y^2} - \sqrt{x^2-2cx+c^2+y^2} = \pm 2a$</p>
<p style="text-align: center;">$\sqrt{x^2+2cx+c^2+y^2} = \sqrt{x^2-2cx+c^2+y^2} \pm 2a$</p>
<p style="text-align: center;">$x^2+2cx+c^2+y^2 = (x^2-2cx+c^2+y^2) \pm 4a \sqrt{x^2-2cx+c^2+y^2} + 4a^2$</p>
<p style="text-align: center;">$2cx = -2cx \pm 4a \sqrt{x^2-2cx+c^2+y^2} + 4a^2$</p>
<p style="text-align: center;">$4cx - 4a^2 = \pm 4a \sqrt{x^2-2cx+c^2+y^2}$</p>
<p style="text-align: center;">$cx - a^2 = \pm a \sqrt{x^2-2cx+c^2+y^2}$</p>
<p style="text-align: center;">$(cx - a^2)^2 = a^2 (x^2-2cx+c^2+y^2)$</p>
<p style="text-align: center;">$c^2x^2 - 2ca^2x + a^4 = a^2x^2 - 2ca^2x + a^2c^2 + a^2y^2$</p>
<p style="text-align: center;">$c^2x^2 + a^4 = a^2x^2 + a^2c^2 + a^2y^2$</p>
<p style="text-align: center;">$(c^2-a^2)x^2 - a^2y^2 = a^2(c^2 - a^2)$</p>
<p style="text-align: center;">$b^2x^2 - a^2y^2 = a^2b^2$</p>
<p style="text-align: center;">$\frac{x^2}{b^2} - \frac{y^2}{a^2} = 1$</p>


