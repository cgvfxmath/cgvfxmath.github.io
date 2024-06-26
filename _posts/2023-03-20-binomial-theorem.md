---
layout: post
title: "Binomial Theorem"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2023-03-20 00:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Binomial theorem (or binomial expansion) describes the algebraic expansion of powers of a binomial.<!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요. (➔[How-To](https://cgvfxmath.github.io/2023-03-18/math-renderer))*

[파스칼의 삼각형](https://cgvfxmath.github.io/2023-03-19/pascal-triangle)에서 계수를 나타내는 $\_{n}C\_{k}$는 조합(combination)을 의미한다고 언급하였다.

왜냐하면 $(a+b)^n$을 전개한 식의 $k+1$번째 항은 $\_{n}C\_{k} a^{n-k} b^{k}$인데, 이 항의 계수인 $\_{n}C\_{k}$는 두 개의 구슬 $a$와 $b$를 가지는 $n$개의 주머니에서 순서에 상관 없이 구슬을 하나씩 꺼낼 때 $k$개의 $b$가 존재하는 경우의 수와 같기 때문이다.

$n=4$인 경우에 대해서 생각해보자. $n=4$이면 $(a+b)^{4} = (a+b)(a+b)(a+b)(a+b)$이고, 이 식을 전개하면 다음과 같은 항들이 만들어진다.

<p style="text-align: center;">$aaaa, aaab, aaba, abaa, baaa, aabb, abab, abba, baab, baba, bbaa, abbb, babb, bbab, bbba, bbbb$</p>  

$(a+b)^{4}$를 전개하여 생성된 항들 중에서 $ab^{3}$은 위의 항들중에서 3개의 $b$를 가지고 있는 $abbb, babb, bbab, bbba$가 합해져서 만들어진다. 즉, 4개 주머니에서 구슬을 하나씩 꺼낼 때 순서에 상관 없이 3개의 구슬 $b$가 존재하는 경우의 수이므로 이 항의 계수는 $\_{4}C\_{3}$가 됨을 알 수 있다.

$n$개 중에서 순서대로 $k$개를 뽑는 경우의 수를 의미하는 개념은 순열(permutation)이다. 제일 처음에 $n$개 중 한 개, 그 다음에는 이미 뽑은 것을 제외한 $n-1$개 중 한 개, 그 다음에는 앞에서 뽑은 것을 제외한 $n-2$개 중 한 개, $\cdots$ 이런 방식으로 $k$번 뽑는 경우의 수이기 때문에 순열은 다음과 같이 정의한다.

<p style="text-align: center;">$_{n}P_{k} = n(n-1)(n-2) \cdots (n-k+1)$</p>

이 식의 분자와 분모에 각각 $(n-k)!$를 곱해서 변형하면 다음과 같은 순열에 대한 공식을 얻을 수 있다.

<p style="text-align: center;">$_{n}P_{k} = \frac{n(n-1)(n-2) \cdots (n-k+1)(n-k)!}{(n-k)!} = \frac{n!}{(n-k)!}$</p>

조합(combination)은 순열(permutation)에서 $k$개에 대한 순서를 제거한 것이기 때문에 $\_{n}P\_{k}$를 $k$개를 순서대로 나열하는 경우의 수인 $k!$로 나누면 얻을 수 있다.

<p style="text-align: center;">$_{n}C_{k} = \frac{_{n}P_{k}}{k!} = \frac{n!}{k!(n-k)!}$</p>

[파스칼의 삼각형](https://cgvfxmath.github.io/2023-03-19/pascal-triangle)에서 유도한 다음의 등식은 이러한 조합(combination)과 순열(permutation)의 정의를 이용해서도 증명할 수 있다.

<p style="text-align: center;">$_{n}C_{k} = _{n-1}C_{k-1} + _{n-1}C_{k}$</p>

<p style="text-align: center;">$_{n-1}C_{k-1} + _{n-1}C_{k} = \frac{(n-1)!}{(k-1)!(n-k)!} + \frac{(n-1)!}{k!(n-k-1)!} = (n-1)! \left( \frac{k}{k!(n-k)!} + \frac{n-k}{k!(n-k)!} \right) = (n-1)! \frac{n}{k!(n-k)!} = \frac{n!}{k!(n-k)!} = _{n}C_{k} $</p>  

한편 이항정리를 이용하여 다음과 같은 항등식을 얻을 수 있다. ($a=1$, $b=x$인 경우)
<p style="text-align: center;">$(1+x)^{n} = _{n}C_{0} x^0 + _{n}C_{1} x^1 + _{n}C_{2} x^2 + \cdots + _{n}C_{n} x^n$</p>

* 양변에 $x=1$을 대입하면 다음과 같은 공식을 얻을 수 있다. (이항계수들의 총합)
<p style="text-align: center;">$_{n}C_{0} + _{n}C_{1} + _{n}C_{2} + \cdots + _{n}C_{n} = 2^n$</p>

* 양변에 $x=-1$을 대입하면 다음과 같은 공식을 얻을 수 있다.
<p style="text-align: center;">$_{n}C_{0} - _{n}C_{1} + _{n}C_{2} + \cdots + (-1)^n \cdot _{n}C_{n} = 0$</p>

* 위의 두 식을 더한 후 2로 나누면 다음과 같은 공식을 얻을 수 있다. (홀수 번째 항의 계수들의 총합)
<p style="text-align: center;">$_{n}C_{0} + _{n}C_{2} + _{n}C_{4} + \cdots = 2^{n-1}$</p>

* 위의 두 식을 뺀 후 2로 나누면 다음과 같은 공식을 얻을 수 있다. (짝수 번째 항의 계수들의 총합)
<p style="text-align: center;">$_{n}C_{1} + _{n}C_{3} + _{n}C_{5} + \cdots = 2^{n-1}$</p>

따라서 (홀수 번째 항의 계수들의 총합)과 (짝수 번째 항의 계수들의 총합)은 같음을 알 수 있다.

