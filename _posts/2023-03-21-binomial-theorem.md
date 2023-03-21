---
layout: post
title: "Binomial Theorem"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2023-03-21 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Binomial theorem (or binomial expansion) describes the algebraic expansion of powers of a binomial.<!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요.*

[파스칼의 삼각형](https://cgvfxmath.github.io/2023-03-20/pascal-triangle)에서 계수를 나타내는 $_{n} C _{k}$는 조합(combination)을 의미한다고 언급하였다.

왜냐하면 $(a+b)^n$을 전개한 식의 $k+1$번째 항은 $ _{n} C _{k} a^{n-k} b^{k} $인데, 이 항의 계수인 $ _{n} C _{k} $는 두 개의 구슬 $a$와 $b$를 가지는 $n$개의 주머니에서 순서에 상관없이 $k$개를 뽑는 것과 같은 경우의 수를 가지기 때문이다.

$n=4$인 경우에 $a^3 b$항의 계수에 대해서 생각해보자. $(a+b)^4 = (a+b)(a+b)(a+b)(a+b)$ 이다. 이 식을 전개한 항들을 계수를 제외하고 나열하면 다음과 같다.

<p style="text-align: center;">$aaaa$, $aaab$, $aaba$, $abaa$, $baaa$, $aabb$, $abab$, $abba$, $baab$, $baba$, $bbaa$, $abbb$, $babb$, $bbab$, $bbba$, $bbbb$</p>

$a^3 b$는 $a$를 3개, $b$를 1개 가지고 있으므로 이중에서 4개 항($aaab$, $aaba$, $abaa$, $baaa$)이 합해져서 만들어진다. 즉, 4개 중에서 순서에 상관없이 3개를 뽑는 경우의 수이므로 이 항의 계수는 $ _{4} C _{3}  = 4$가 됨을 알 수 있다.

$n$개 중에서 순서대로 $k$개를 뽑는 경우의 수는 순열(permutation)이다. 제일 처음에 $n$개 중 한 개, 그 다음에는 이미 뽑은 것을 제외한 $n-1$개 중 한 개, 그 다음에는 앞에서 뽑은 것을 제외한 $n-2$개 중 한 개, $\cdots$ 이런 방식으로 $k$번 뽑는 경우의 수이기 때문에 순열은 다음과 같이 정의한다.

<p style="text-align: center;">$_{n} P _{k} = n(n-1)(n-2) \cdots (n-k+1)$</p>

이 식의 분자와 분모에 각각 $(n-k)!$를 곱해서 변형하면 다음과 같은 순열에 대한 공식을 얻을 수 있다.

<p style="text-align: center;">$_{n} P _{k} = \frac{n(n-1)(n-2) \cdots (n-k+1)(n-k)!}{(n-k)!} = \frac{n!}{(n-k)!}$</p>

조합(combination)은 순열(permutation)에서 $k$개에 대한 순서를 제거한 것이기 때문에 $_{n} P _{k}$를 $k$개를 순서대로 나열하는 경우의 수인 $k!$로 나누면 얻을 수 있다.

<p style="text-align: center;">$_{n} C _{k} = \frac{ _{n} P _{k} }{ k! } = \frac{ n! }{ k! (n-k)! }$</p>

[파스칼의 삼각형](https://cgvfxmath.github.io/2023-03-20/pascal-triangle)에서 유도한 다음의 등식은 이러한 조합(combination)과 순열(permutation)의 정의를 이용해서도 증명할 수 있다.

<p style="text-align: center;">$\color{red}{_{n} C _{k} = _{n-1} C _{k-1} + _{n-1} C _{k}}$</p>

<p style="text-align: center;">$_{n-1} C _{k-1} + _{n-1} C _{k} = \frac{ (n-1)! }{ (k-1)! (n-k)! } + \frac{ (n-1)! }{ k! (n-k-1)! } = (n-1)! \left( \frac{k}{k! (n-k)!} + \frac{n-k}{k! (n-k)!} \right) $</p>  
<p style="text-align: center;">$ = (n-1)! \frac{ n }{ k! (n-k)!} = \frac{ n! }{ k! (n-k)! } = _{n} C _{k} $</p>  


한편 이항정리를 이용하여 다음과 같은 항등식을 얻을 수 있다. ($a=1$, $b=x$인 경우)
<p style="text-align: center;">$(1+x)^n = _{n} C _{0} x^0 + _{n} C _{1} x^1 + _{n} C _{2} x^2 + \cdots + _{n} C _{n} x^n $</p>

* 양변에 $x=1$을 대입하면 다음과 같은 공식을 얻을 수 있다. (이항계수들의 총합)
<p style="text-align: center;">$_{n} C _{0} + _{n} C _{1} + _{n} C _{2} + \cdots + _{n} C _{n} = 2^n$</p>

* 양변에 $x=-1$을 대입하면 다음과 같은 공식을 얻을 수 있다.
<p style="text-align: center;">$_{n} C _{0} - _{n} C _{1} + _{n} C _{2} + \cdots + (-1)^n \cdot _{n} C _{n} = 0$</p>

* 위의 두 식을 더한 후 2로 나누면 다음과 같은 공식을 얻을 수 있다. (홀수 번째 항의 계수들의 총합)
<p style="text-align: center;">$_{n} C _{0} + _{n} C _{2} + _{n} C _{4} + \cdots = 2^{n-1}$</p>

* 위의 두 식을 뺀 후 2로 나누면 다음과 같은 공식을 얻을 수 있다. (짝수 번째 항의 계수들의 총합)
<p style="text-align: center;">$_{n} C _{1} + _{n} C _{3} + _{n} C _{5} + \cdots = 2^{n-1}$</p>

따라서 (홀수 번째 항의 계수들의 총합)과 (짝수 번째 항의 계수들의 총합)은 같음을 알 수 있다.

