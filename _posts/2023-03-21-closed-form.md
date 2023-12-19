---
layout: post
title: "Closed Form"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2023-03-21 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Closed Form vs Open Form<!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요. (➔[How-To](https://cgvfxmath.github.io/2023-03-18/math-renderer))*

닫힌 형태(closed form)란 방정식(equation)의 해(solution)를 해석적(analytic)으로 표현할 수 있는 종류의 문제를 말한다. 즉, 닫힌 형태를 가지는 방정식의 해는 변수(variable), 상수(constant), 사칙연산( +−×÷), 그리고 잘 알려진 기본 함수(삼각함수, 로그함수, 제곱근 등) 등을 조합해서 “해 = …” 꼴로 표현될 수 있다. 대표적인 닫힌 형태 해(closed form solution)의 예로는 2차 방정식의 근의 공식을 들 수 있다.

<p style="text-align: center;">$ax^2 + bx + c = 0 \; (a \neq 0) \;\;\; \Longleftrightarrow \;\;\; x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$</p>


닫힌 형태의 반대 개념으로 열린 형태(open form)라는 것도 있다. 열린 형태란 유한개(finite number)의 수학적 표현을 사용해서 정확하게 해를 표현할 수 없는 문제를 말한다. 이와 같이 주어진 문제가 열린 형태여서 명확한 해가 존재하지 않을 경우에는 컴퓨터를 이용한 수치해석 기법으로 근사해(approximation)을 구할 수 있다. 수치해석으로 근사해를 구하는 기법은 다양하지만 대부분의 방식들이 반복적으로 조금씩 해에 접근해 가는 반복해법(iterative method) 범주에 속한다. 따라서 일반적으로 닫힌 형태의 문제가 열린 형태의 문제보다 답을 빠르고 정확하게 구할 수 있다.

<p style="text-align: center;">$\text{Repeat } \theta \rightarrow \theta + \delta \theta \;\;\; s.t. \;\;\;L(\theta + \delta \theta) < L(\theta) \text{ until } \left \| L(\theta + \delta \theta) - L(\theta) \right \| < \epsilon$</p>


정리하면 닫힌 형태(closed form)의 문제란 주어진 문제를 수학적으로 잘 수식화(formulation)해서 해석적인 해가 존재하는 형태의 방정식으로 바꿨다는 의미로 이해를 하면 된다.

선형 회귀(linear regression) 문제의 답을 최소제곱법(least square)으로 구하는 것도 닫힌 형태의 문제로 볼 수 있다. 반복해법을 사용해서 최소제곱법을 풀 수도 있지만, 이 경우에도 해 자체는 “해 = …” 꼴로 표현할 수 있기 때문에 닫힌 형태의 문제로 볼 수 있다.

<p style="text-align: center;">$\underset{a, b}{\mathrm{argmin}} \sum \left \| y_i - (ax_i + b) \right \| \;\;\; \Longleftrightarrow \;\;\; a = \overline{y} - b \overline{x}, \;\;\; b = \frac{\sum(x_i - \overline{x})(y_i - \overline{y})}{\sum(x_i - \overline{x})^2}$</p>

닫힌 형태를 가지는 공학 문제들은 결국 $\mathbf{Ax=b}$ 꼴의 행렬 방정식을 푸는 문제로 귀결되는데, 이때 시스템 행렬(system matrix)인 $\mathbf{A}$의 고유값(eigenvalue)과 고유벡터(eigenvector)를 이용하면 해의 특성을 분석하고 예측하는데 도움이 된다.

