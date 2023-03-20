---
layout: post
title: "Pascal's Triangle"
author: "wano"
excerpt_separator: <!--more-->
tags: Math
use_math: true
---

Pascal's triangle is a triangular array of the binomial coefficients.<!--more-->

다음과 같이 두 변수 $a$와 $b$로 이루어진 이항식(=항이 2개인 다항식)의 제곱식을 전개하면 다음과 같다.

<p style="text-align: center;">$(a+b)^2 = a^2 + 2ab + b^2$</p>
<p style="text-align: center;">$(a+b)^3 = a^3 + 3a^2b + 3ab^2 + b^3$</p>

무언가 규칙이 있는 것처럼 보인다. 일반적인 자연수 $n(= 2, 3, 4, \cdots)$ 에 대한 $(a+b)^n$의 전개는 어떻게 될까?

$(a+b)^n$을 전개한 식의 $k$번째 항의 계수를 $_{n} C _{k-1}$라 하면 다음과 같이 쓸 수 있다.

<p style="text-align: center;">$(a+b)^n = _{n} C _{0} a^n b^0 + _{n} C _{1} a^{n-1} b^1 + \cdots + _{n} C _{k-1} a^{n-k+1} b^{k-1} + _{n} C _{k} a^{n-k} b^k + \cdots + _{n} C _{n} a^0 b^n$</p>

위의 식은 $a$에 대한 내림차순으로 정리한 식으로 $a^n b^0$항을 시작으로 $a$의 차수는 1씩 감소하고, $b$의 차수는 1씩 증가하여 총 $n+1$개의 항을 가지는 다항식이다. 이처럼 이항식의 거듭제곱을 일련의 단항식들의 합으로 전개하는 것을 이항정리(二項定理, binomial theorem)라고 한다.

여기서 $_{n} C _{k-1}$는 조합(combination)을 나타내며, $n$개 중에서 $k-1$개를 순서없이 뽑는 경우의 수를 의미한다. 이와 관련된 내용은 뒤에서 다시 살펴보겠다.

한편 마찬가지 방법으로 차수가 하나 작은 $(a+b)^{n-1}$을 전개한 식의 $k$번째 항의 계수를 $_{n-1} C _{k-1}$라 할 수 있으므로 $(a+b)^{n-1}$을 전개하면 다음과 같다.

<p style="text-align: center;">$(a+b)^{n-1} = _{n-1} C _{0} a^{n-1} b^0 + _{n-1} C _{1} a^{n-2} b^1 + \cdots + _{n-1} C _{k-1} a^{n-k} b^{k-1} + _{n-1} C _{k} a^{n-k-1} b^k + \cdots$</p>

여기서 $a^{n-k-1} b^k$보다 뒤에 있는 항들은 중요하지 않으므로 생략하였다.

그런데 $(a+b)^n = (a+b)^{n-1} (a+b)$이므로 $(a+b)^n$의 $k+1$번째 항은 $(a+b)^{n-1}$의 $k$번째 항과 $k+1$ 항에 각각 $b$와 $a$를 곱해서 만들어지는 것을 알 수 있다.
1. $(a+b)^{n}$의 $k+1$번째 항: $_{n} C _{k} a^{n-k} b^{k}$
2. $(a+b)^{n-1}$의 $k$번째 항: $_{n-1} C _{k-1} +  a^{n-k} b^{k-1}$ (위의 1번 항과 비교하여 $b$의 차수가 하나 작음)
3. $(a+b)^{n-1}$의 $k+1$번째 항: $_{n-1} C _{k} a^{n-k-1} b^{k}$ (위의 1번 항과 비교하여 $a$의 차수가 하나 작음)

<p style="text-align: center;">$\cdots + _{n} C _{k} a^{n-k} b^{k} + \cdots = (\cdots + _{n-1} C _{k-1} a^{n-k} b^{k-1} + _{n-1} C _{k} a^{n-k-1} b^{k} + \cdots) \times (a+b)$</p>

위의 식이 복잡하게 보이지만 사실 단순한 분배법칙을 적용한 것에 불과하기 때문에 천천히 따져보면 어렵지 않게 이해할 수 있을 것이다.

따라서 다음과 같은 사실이 성립합을 알 수 있다.

<p style="text-align: center;">$_{n} C _{k} = _{n-1} C _{k-1} + _{n-1} C _{k}$</p>

