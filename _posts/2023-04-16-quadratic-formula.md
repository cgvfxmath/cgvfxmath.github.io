---
layout: post
title: "Quadratic Formula"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2023-03-19 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

It provides the solution(s) to a quadratic equation.<!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요.*

이차방정식(quadratic equation)의 일반꼴은 다음과 같습니다.

<p style="text-align: center;">$ax^2 + bx + c = 0$</p>

여기서 $a$, $b$, $c$는 모두 실수이고, $a \neq 0$이라고 가정하겠습니다. (만약 $a = 0$이라면 주어진 식은 이차가 아닌 선형식이 되기 때문입니다.)

이차방정식은 일반적으로 서로 다른 두 해를 가집니다. 이 두 해를 각각 $\alpha$와 $\beta$라고 한다면 위의 식은 다음과 같이 인수분해꼴로 표현할 수 있습니다.

<p style="text-align: center;">$a(x - \alpha)(x - \beta) = 0$</p>

이 식을 전개하여 일반꼴의 각 항과 비교하면 다음과 같은 "근과 계수와의 관계"가 성립하는 것을 알 수 있습니다.

<p style="text-align: center;">$\alpha + \beta = -\frac{b}{a}, \;\;\; \alpha \beta = \frac{c}{a}$</p>

---

만약 $x^2 + 5x + 6 = (x-2)(x-3) = 0$과 같이 쉽게 인수분해꼴로 바꿀 수 있다면 두 해를 쉽게 구할 수 있지만, 현실에서 마주하는 문제들 중에는 그렇지 않은 경우가 더 많습니다.

만약 주어진 이차방정식을 쉽게 인수분해할 수 없는 경우에는 다음과 같은 근의공식을 사용하여 두 해를 구할 수 있습니다.

<p style="text-align: center;">$\alpha = -\frac{-b - \sqrt{b^2 - 4ac}}{2a}, \;\;\; \beta = -\frac{-b + \sqrt{b^2 - 4ac}}{2a}$</p>

근의공식은 자주 사용되고 중요하기 때문에 반드시 암기를 해야 하는 가장 대표적인 공식 중 하나입니다. 하지만 유도과정을 반드시 알고 있어야 합니다.

근의공식의 유도과정이 다소 복잡해보일 수 있는데, 기본적으로는 등식의 성질(등식의 양변을 같은 수로 더하거나, 빼거나, 곱하거나, 나누어도 여전히 등식은 성립한다.)을 이용하여 $x = \square$ 꼴로 정리하는 과정에 불과하다는 기본적인 방향성을 염두하면서 보면 쉽게 이해할 수 있습니다.

1) 양변을 $a$로 나눈다. ($a \neq 0$ 이므로 양변을 $a$로 나눌 수 있다.)
<p style="text-align: center;">$x^2 + \frac{b}{a}x + \frac{c}{a} = 0$</p>

2) 양변에 각각 $-\frac{c}{a}$를 더한다.
<p style="text-align: center;">$x^2 + \frac{b}{a}x = -\frac{c}{a}$</p>

3) 양변에 각각 ${(\frac{b}{2a})}^2$를 더한다.
<p style="text-align: center;">$x^2 + \frac{b}{a}x + {(\frac{b}{2a})}^2 = -\frac{c}{a} + {(\frac{b}{2a})}^2$</p>

4) 좌변을 완전제곱식으로 묶는다. 그리고 우변은 통분한다.
<p style="text-align: center;">$(x + \frac{b}{2a})^2 = \frac{b^2-4ac}{4a^2}$</p>

5) 양변에 루트를 씌운다.
<p style="text-align: center;">$x + \frac{b}{2a} = \pm \sqrt{\frac{b^2-4ac}{4a^2}}$</p>

6) 양변에 각각 $-\frac{b}{2a}$를 더한다.
<p style="text-align: center;">$x = \frac{b}{2a} \pm \sqrt{\frac{b^2-4ac}{4a^2}}$</p>

7) 우변을 통분한다.
<p style="text-align: center;">$x = \frac{-b \pm \sqrt{b^2-4ac}}{2a}$</p>

