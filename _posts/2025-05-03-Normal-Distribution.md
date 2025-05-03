---
layout: post
title: "Normal Distribution"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2025-05-03 10:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Proof on Normal Distribution<!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요. (➔[How-To](https://cgvfxmath.github.io/2023-03-18/math-renderer))*

정규 분포의 함수식이 다음과 같음을 증명해 보겠습니다.

<p style="text-align: center;">$f(X=x) = \frac{1}{\sigma \sqrt{2 \pi}} e^{-\frac{1}{2} \left(\frac{x-\mu}{\sigma}\right)^2}$</p>

2차원 평면상의 임의의 점 $(x,y)$에 다트가 맞을 확률을 $p$라 하면 $p(x,y)=p(r)$이고, 앞에서의 가정에 의해 다음의 관계가 성립합니다.

<p style="text-align: center;">$p(r)=p(\sqrt{x^2+y^2})=f(x)f(y)$</p>

이때, $(x,y)=(r,0)$을 대입하면 $p(r)=f(r)\,f(0)$가 되는데, 여기서 $f(0)$은 0이 아닌 어떠한 상수이므로 이 값을 $\lambda$라 하면, 두 확률분포 함수 p와 f는 다음과 같은 관계를 가진다는 사실을 알 수 있습니다.

<p style="text-align: center;">$p(t)=\lambda f(t)$</p>

$p(\sqrt{x^2+y^2})=f(x)\,f(y)$에 이 결과를 적용하겠습니다.

<p style="text-align: center;">$\lambda f(\sqrt{x^2+y^2})=f(x)f(y)\;\;\; \Longleftrightarrow \;\;\;\frac{f(\sqrt{x^2+y^2})}{\lambda} = \frac{f(x)}{\lambda} \frac{f(y)}{\lambda}$</p>

여기서 $g(t)=\frac{f(t)}{\lambda}$라 하면 위의 식은 다음과 같이 쓸 수 있습니다.

<p style="text-align: center;">$g(\sqrt{x^2+y^2})=g(x)\, g(y)$</p>

Q.E.D.


