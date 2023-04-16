---
layout: post
title: "Cube Root of Unity"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2023-03-19 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

The root of unity is a number which is complex in nature and gives 1 if raised to the power of a positive integer n.<!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요.*

$x^3 = 1$의 허근에 대해서 알아보겠습니다.

이 식은 다음과 같이 인수분해할 수 있습니다.

<p style="text-align: center;">$x^3 - 1 = (x-1)(x^2 + x + 1) = 0$</p>

따라서 $x^3 = 1$의 한 허근을 $\omega$라고 하면 다음과 같은 두 등식을 얻을 수 있습니다.

<p style="text-align: center;">$\omega^3 = 1$</p>
<p style="text-align: center;">$\omega^2 + \omega + 1 = 0$</p>

이 성질을 이용하면 0이상인 임의의 정수 $n$에 대해 $\omega^n$을 1차 또는 0차(상수)로 줄일 수 있습니다.

몇 가지 예를 들어보겠습니다.

$\omega^0 = 1$

$\omega^1 = \omega$

$\omega^2 = -\omega - 1$

$\omega^3 = 1$

$\omega^4 = \omega^3 \cdot \omega = \omega $

$\omega^5 = \omega^3 \cdot \omega^2 = \omega^2 = -\omega - 1$

$\omega^6 = (\omega^3)^2 = 1^2 = 1$

$\vdots$

위의 패턴을 살펴보면 $n$이 3의 배수일 때 마다 1이 반복적으로 나타나는 3주기 성질을 가지는 것을 알 수 있습니다.

그리고 다음과 같은 문제 또한 $\omega$의 3주기 성질을 이용하여 풀 수 있습니다.

<p style="text-align: center;">$1 + \omega + \omega^2 + \omega^3 + \cdots + \omega^{98} = ?$</p>

$1 + \omega + \omega^2 + \omega^3 + \cdots + \omega^{98}$

$= (1 + \omega + \omega^2) + \omega^3(1 + \omega + \omega^2) + \omega^6(1 + \omega + \omega^2) + \cdots + \omega^{3 \times 32}(1 + \omega + \omega^2)$

$= 0 \times 33$

$= 0$

