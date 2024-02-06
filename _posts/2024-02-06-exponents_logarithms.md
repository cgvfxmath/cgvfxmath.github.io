---
layout: post
title: "Exponents & Logarithms"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2024-02-06 11:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Assumptions of Exponents and Logarithms <!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요. (➔[How-To](https://cgvfxmath.github.io/2023-03-18/math-renderer))*

로그는 다음과 같이 정의합니다.

<p style="text-align: center;">$a^x=b \;\;\; \Longleftrightarrow \;\;\; x=\log_a b$</p>

여기서 $a$를 밑(base), $x$를 지수(exponent), $b$를 진수(argument)라고 부릅니다.

만약 $a$, $b$, $x$가 모두 실수라면 다음과 같은 조건이 필수적으로 따라 붙습니다.

<p style="text-align: center;">$a \neq 1$, $\;\;\; $$a > 0$, $\;\;\;$$b > 0$</p>

처음 지수를 배울 때에는 지수 $x$가 정수인 경우만 생각하지만, 고등학교 교과과정에서 지수인 $x$를 유리수 또는 실수로 확장하게 되면서 붙는 전제들입니다. 이렇게 되어야 하는 이유는 다음과 같습니다.

<br />
***
<br />

1) $b > 0$이어야 하는 이유

$2^x = -2$를 만족하는 실수 $x$는 존재하지 않으므로 $b$가 0보다 작은 경우는 고려하지 않습니다.

<br />
***
<br />

2) $a \neq 1$이어야 하는 이유

만약 $a=1$이라면 로그의 정의에 의해 다음과 같은 등식들이 성립합니다.

<p style="text-align: center;">$1^2=1 \;\;\; \Longleftrightarrow \;\;\; 2=\log_1 1$</p>
<p style="text-align: center;">$1^3=1 \;\;\; \Longleftrightarrow \;\;\; 3=\log_1 1$</p>

그런데 이렇게 되면 $2 = 3$이라는 모순이 발생하므로 $a$는 1인 경우는 고려하지 않습니다.

<br />
***
<br />

3) $a > 0$이어야 하는 이유

$a < 0$이면 지수법칙이 성립하지 않는 경우가 발생합니다.

한 가지 예를 들어 보겠습니다.

<p style="text-align: center;">$\{(-2)^2\}^{\frac{1}{2}} = 4^{\frac{1}{2}} = 2$</p>

그런데 이 식은 지수법칙에 의해 다음과 같은 답을 얻을 수도 있습니다.

<p style="text-align: center;">$\{(-2)^2\}^{\frac{1}{2}} = (-2)^1 = -2$</p>

그런데 이렇게 되면 $2 = -2$이라는 모순이 발생하므로 $a$가 0보다 작은 경우는 고려하지 않습니다.


