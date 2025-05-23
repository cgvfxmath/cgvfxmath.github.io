---
layout: post
title: "Clairaut's Theorem"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2025-05-23 10:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Proof on Clairaut's Theorem<!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요. (➔[How-To](https://cgvfxmath.github.io/2023-03-18/math-renderer))*

클레로 정리 (Clairaut's Theorem) $\frac{\partial^2 f}{\partial x_1 \partial x_2} = \frac{\partial^2 f}{\partial x_2 \partial x_1}$를 증명해 보겠습니다.

$f_{xy} = \frac{\partial}{\partial y}f_x(x,y) = \lim_{h\rightarrow 0}\frac{f_x(x,y+h)-f_x(x,y)}{h}$


<p style="text-align: center;">$f(X=x) = \frac{1}{\sigma \sqrt{2 \pi}} e^{-\frac{1}{2} \left(\frac{x-\mu}{\sigma}\right)^2}$</p>

2차원 평면상의 임의의 점 $(x,y)$에 다트가 맞을 확률을 $p$라 하면 $p(x,y)=p(r)$이고, 앞에서의 가정에 의해 다음의 관계가 성립합니다.

<p style="text-align: center;">$p(r)=p(\sqrt{x^2+y^2})=f(x)f(y)$</p>

이때, $(x,y)=(r,0)$을 대입하면 $p(r)=f(r)f(0)$이 되는데, 여기서 $f(0)$은 0이 아닌 어떠한 상수이므로 이 값을 $\lambda$라 하면, 두 확률분포 함수 p와 f는 다음과 같은 관계를 가진다는 사실을 알 수 있습니다.

<p style="text-align: center;">$p(t)=\lambda f(t)$</p>

$p(\sqrt{x^2+y^2})=f(x)f(y)$에 이 결과를 적용하겠습니다.

<p style="text-align: center;">$\lambda f(\sqrt{x^2+y^2})=f(x)f(y)\;\;\; \Longleftrightarrow \;\;\;\frac{f(\sqrt{x^2+y^2})}{\lambda} = \frac{f(x)}{\lambda} \frac{f(y)}{\lambda}$</p>

여기서 $g(t)=\frac{f(t)}{\lambda}$라 하면 위의 식은 다음과 같이 쓸 수 있습니다.

<p style="text-align: center;">$g(\sqrt{x^2+y^2})=g(x)g(y)$</p>

여기서 수학적인 직관력을 발휘해 보겠습니다. 이러한 성질을 가지는 함수를 우리는 알고 있습니다. 바로 지수함수입니다.

<p style="text-align: center;">$g(\sqrt{x^2+y^2})=a^{-b(x^2+y^2)} = a^{-bx^2-by^2} =a^{-bx^2} a^{-by^2}=g(x)g(y)$</p>

즉, $g(t)=a^{- b t^2}$라고 놓을 수 있습니다.

그런데, 이 식은 $k=b\ln{a}$라 치환하면 함수 $g(t)=e^{- k t^2}$로 쓸 수 있습니다. 이렇게 밑이 임의의 실수인 지수함수를 자연상수가 밑이 되도록 변환하는 트릭은 수학에서 종종 사용됩니다. 이것은 마치 로그함수를 사용할 때 일반적으로 자연로그를 사용하는 이유와 일맥상통합니다. $a^{-b t^2}=e^{-k t^2}$의 양변에 자연로그를 취하면 $- b t^2 \ln a = - k t^2 \ln e$가 됩니다. $\ln e = 1$이므로 이식의 양변을 $-t^2$로 나누고 정리하면 $k = b \ln{a}$가 되기 때문입니다.

한편, 현재 우리는 평균일 확률이 가장 높은 종 모양 곡선 형태의 확률밀도함수를 찾고 있습니다. 따라서 $k>0$이어야 합니다. 그러므로 임의의 실수 $h$에 대하여 라고 치환할 수 있고, 이때 함수 $f(t)$는 다음과 같은 형태가 됩니다.

<p style="text-align: center;">$f(t)=\lambda g(t)=\lambda e^{-h^2 t^2}$</p>

이제 $h$와 $\lambda$의 값을 정하면 함수 f(t)의 식이 완성됩니다. 미지수가 2개 이므로 방정식이 2개 필요합니다. 다음과 같은 두 가지 조건을 사용하여 $h$와 $\lambda$의 값을 구해보겠습니다.

전체확률은 1이므로 $\int_{-\infty}^{+\infty}f(t)dt=1$이며, 분산의 정의에 의해 $\int_{-\infty}^{+\infty} f(t) t^2 dt = \sigma^2$인 사실을 사용하겠습니다.

첫 번째 조건에 의해 다음의 등식이 성립해야 합니다.

<p style="text-align: center;">$\lambda \int_{-\infty}^{+\infty} e^{-h^2 t^2} dt =1$</p>

이때 $u=ht$라고 치환하면 $du=hdt$이고, $t \rightarrow \pm \infty$일 때 $u \rightarrow \pm \infty$이므로 함수 $f(t)$의 아래 부분 넓이는 '가우스 적분'을 이용하면 다음과 같이 정리할 수 있습니다.

<p style="text-align: center;">$\lambda\int_{-\infty}^{+\infty}e^{-h^2 t^2}dt=\frac{\lambda}{h}\int_{-\infty}^{+\infty}e^{-u^2}du=\frac{\lambda}{h} \sqrt{\pi}=1$</p>

양변을 제곱하면 다음과 같은 첫 번째 방정식을 얻을 수 있습니다.

<p style="text-align: center;">$h^2 = \pi \lambda^2$</p>

이 결과와 두 번째 조건에 의해 다음의 등식이 성립해야 합니다.

<p style="text-align: center;">$\lambda \int_{-\infty}^{+\infty} e^{-\pi {\lambda}^2 t^2} t^2 dt = \sigma^2$</p>

여기서 부분적분 공식 $\int_{b}^{a} u \mathrm{d}v = uv \Big|_a^b -\int_{b}^{a} v du$를 적용하기 위해 $u$와 $v$를 다음과 같이 치환하겠습니다.

<p style="text-align: center;">$u=x, v=-\frac{1}{2 \pi \lambda^2} e ^ {- \pi \lambda^2 t^2}$</p>

그러면 $du=dx$이고, $dv = t e ^ {- \pi \lambda^2 t^2}$이므로 다음과 같이 정리할 수 있습니다.

<p style="text-align: center;">$\lambda \int_{-\infty}^{+\infty} u dv = \lambda \left(uv \Big|_{-\infty}^{+\infty} - \int_{-\infty}^{+\infty} v du \right) = \sigma^2$</p>

여기서 첫 번째 항은 다음과 같이 $0$이 되어 소거됩니다.

<p style="text-align: center;">$uv \Big|_{-\infty}^{+\infty} = -\frac{x}{2 \pi \lambda } e^{- \pi \lambda^2 t^2} \Big|_{-\infty}^{+\infty} = 0$</p>

두 번째 항을 정리하면 다음과 같습니다.

<p style="text-align: center;">$-\int_{-\infty}^{+\infty} v du = \frac{1}{2 \pi \lambda^2} \int_{-\infty}^{+\infty} e ^ {- \pi \lambda^2 t^2} dt = \frac{1}{2 \pi \lambda^2} \int_{-\infty}^{+\infty} f(t) dt = \frac{1}{2 \pi \lambda^2} = \sigma^2$</p>

<p style="text-align: center;">$\therefore \lambda = \frac{1}{\sigma \sqrt{2 \pi}}, h^2 = \pi \lambda^2 = \frac{1}{2 \sigma^2}$</p>

이 두 값을 $f(t)=\lambda e^{-h^2 t^2}$에 대입하면 다음과 같은 정규 확률 분포의 함수식을 얻을 수 있습니다.

<p style="text-align: center;">$f(t) = \frac{1}{\sigma \sqrt{2 \pi}} e^{-\frac{t^2}{2 \sigma^2}}$</p>

여기서 $t$축으로만큼 평행이동하면 다음과 같은 형태를 얻게 됩니다.

<p style="text-align: center;">$f(t) = \frac{1}{\sigma \sqrt{2 \pi}} e^{-\frac{(t-\mu)^2}{2 \sigma^2}}$</p>

Q.E.D.


