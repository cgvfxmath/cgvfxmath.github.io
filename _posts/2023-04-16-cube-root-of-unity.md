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

정리하면 다음과 같은 조건 중 하나가 주어지면 $\omega$의 3주기 성질을 사용하여 문제를 풀 수 있다는 사실을 알아야 합니다.

1) $x^3 = 1$

2) $x^2 + x + 1 = 0$
: $x \neq 1$이므로 양변에 $(x-1)$을 곱하 1번식으로 변형할 수 있습니다.

3) $x + \frac{1}{x} = -1$
: 양변에 $x$를 곱하여 정리하면 2번식으로 변형할 수 있습니다.

4) $x = \frac{-1 \pm \sqrt{3}i}{2}$
: 근의공식에 의해 2번식의 해이므로 2번식과 같은 의미를 가집니다.

---

이러한 개념을 조금 더 확장해보겠습니다.

$x^n - 1$은 다음과 같이 인수분해할 수 있습니다.

<p style="text-align: center;">$x^n - 1 = (x-1)(x^{n-1} + x^{n-2} + \cdots + x + 1)$</p>

이 식은 복잡해보이지만 어렵지 않게 이해할 수 있습니다.

<p style="text-align: center;">$(x-1)(x^{n-1} + x^{n-2} + \cdots + x + 1)$ 에서</p>

1) 최고차항인 $x^n$은 $x \times x^{n-1}$로 만들어집니다.

2) 그 다음 최고차항인 $x^{n-1}$은
<p style="text-align: center;">$x \times x^{n-2}$과 $-1 \times x^{n-1}$</p>
로 만들어지는데 두 결과가 상쇄되기 때문에 사라집니다.

3) 그 다음 고차항인 $x^{n-2}$은
<p style="text-align: center;">$x \times x^{n-3}$과 $-1 \times x^{n-2}$</p>
로 만들어지는데 두 결과가 상쇄되기 때문에 사라집니다.

<p style="text-align: center;">$\vdots$</p>

따라서 임의의 자연수 $n$에 대해 $x^{n-1} + x^{n-2} + \cdots + x + 1 = 0$라는 조건이 주어지면 $x^n = 1$이 되는 것을 알 수 있고, 이것은 $n$주기 성질을 가지고 차수줄이기를 할 수 있다는 것을 의미합니다.

예를 들어 $x^3 + x^2 + x + 1 = 0$이라는 조건이 주어졌다면 다음과 같은 식의 정리가 가능합니다.

<p style="text-align: center;">$1 + x + x^2 + x^3 + \cdots + x^{98} = 14 \times (1 + x + x^2 + x^3) + (1 + x) = 1 + x$</p>
