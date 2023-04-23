---
layout: post
title: "Properties of Quadratic Equations"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2023-04-22 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Several Important facts about quadratic equations<!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요.*

이차다항식은 대수학에서 매우 중요한 개념 중 하나입니다. 이차다항식은 $x$의 2차항이 있는 다항식으로, 그래프가 포물선 모양을 가지기 때문에 수학, 물리학, 공학 등에서 많이 사용됩니다. 예를 들어 이차다항식은 자유낙하운동의 운동방정식, 추락체의 높이나 거리를 계산하는 문제, 최소값과 최대값을 찾는 최적화 문제, 그리고 딥러닝의 비용함수(cost function)에서도 활용됩니다.

다음과 같은 일반형을 가지는 이차다항식의 몇 가지 중요한 성질들을 살펴보겠습니다.
<p style="text-align: center;">$f(x) = ax^2 + bx + c \; (a \neq 0)$</p>

일단 위의 이차함수는 다음과 같은 표준형으로 바꿀 수 있습니다. 
<p style="text-align: center;">$f(x) = a(x-p)^2 + q$</p>
여기서 $p = -\frac{b}{2a}$ 이고, $q = -\frac{b^2-4ac}{4a}$ 입니다. 이것은 표준형에 $p$, $q$를 대입하여 정리하면 어렵지 않게 증명할 수 있습니다.

이차함수의 표준형에서 $(p, q)$는 꼭지점을 의미하며, 이 함수의 그래프는 $x=p$에 대해서 대칭입니다. 그리고  정의역이 실수 전체의 집합일 때, $a>0$이면 아래로 볼록하기 때문에 전역최소값(global minimum) $q$를 가지고, $a<0$이면 위로 볼록하기 때문에 전역최대값(global minimum) $q$를 가집니다. 만약 정의역이 실수 전체의 집합이 아니고 특정구간으로 주어진다면, $x=p$가 이 구간에 속하는지 여부에 따라 경우를 나누어서 최대값 및 최소값을 따져봐야 합니다.

그리고 $f(x)=0$의 두 해를 $\alpha$, $\beta$ (단, $\alpha \leq \beta$)라고 하면 주어진 이차함수는 다음과 같은 인수분해형으로 쓸 수도 있습니다
<p style="text-align: center;">$f(x) = a(x-\alpha)(x-\beta)$</p>
여기서 $\alpha = \frac{-b-\sqrt{b^2-4ac}}{2a}$, $\beta = \frac{-b+\sqrt{b^2-4ac}}{2a}$ 입니다. 이것을 근의공식이라고 부르며 완전제곱식을 이용하여 어렵지 않게 [증명](https://cgvfxmath.github.io/2023-04-14/quadratic-formula)할 수 있습니다.

인수분해형을 전개하여 일반형과 계수비교를 하거나, 아니면 위의 $\alpha$, $\beta$에서 직접 계산하면 다음과 같은 근과 계수와의 관계가 성립합니다.
<p style="text-align: center;">$\alpha + \beta = -\frac{b}{a}, \;\;\; \alpha \beta = \frac{c}{a}$</p>
두 근의 합과 곱 외에 두 근의 차 또한 다음과 같이 구할 수 있습니다.
<p style="text-align: center;">$|\alpha - \beta| = \beta - \alpha = \frac{\sqrt{b^2-4ac}}{a}$</p>

대칭축 $x=p$를 근과 계수와의 관계 $\alpha + \beta = -\frac{b}{a}$와 연관지어 다음과 같이 정리할 수 있습니다.
<p style="text-align: center;">$x=p=-\frac{b}{2a}=\frac{\alpha+\beta}{2}$</p>
이것은 대칭축의 $x$값인 $p$가 $\alpha$와 $\beta$의 평균과 같다는 의미입니다. 두 해 $\alpha$와 $\beta$는 각각 함수 $f(x)$가 $x$축과 만나는 두 점의 위치를 의미하는데, 이차함수의 그래프는 축 $x=p$에 대해서 대칭이기 때문에 당연하게 성립하는 성질입니다.

이러한 사실을 조금 더 확장해보겠습니다. 만약 같은 $y$값을 가지게 하는 두 수 $x=m$과 $x=n$이 있다면 이 두 수의 평균인 $\frac{m+n}{2}$이 대칭축을 정의하는 $p$의 값이 된다는 것을 알 수 있습니다. (위의 $p=\frac{\alpha+\beta}{2}$는 $y=0$인 특별한 경우를 의미 됩니다.) 즉, $f(m)=f(n)$이면 $p=\frac{m+n}{2}$ 됩니다. 그리고 만약 $f(m)=f(n)=F$이면, $m$과 $n$은 $g(x)=f(x)-F$의 두 해가 됩니다. 왜냐하면 $g(m) = g(n) = 0$이 되기 때문입니다.

한편 만약 $f(x)=ax^2+bx+c$의 두 근이 $\alpha$, $\beta$이면 계수의 순서를 반대로 뒤집은 $h(x)=cx^2+bx+a$의 두 근은 $\frac{1}{\alpha}$, $\frac{1}{\beta}$가 됩니다. 왜냐하면 $f(\alpha)=a\alpha^2+b\alpha+c=0$와 $f(\beta)=a\beta^2+b\beta+c=0$에서 양변을 각각 $\alpha^2$과 $\beta^2$으로 나누면 $h(\frac{1}{\alpha})=h(\frac{1}{\beta})=0$ 되기 때문입니다.
