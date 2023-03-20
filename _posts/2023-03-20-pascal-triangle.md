---
layout: post
title: "Pascal's Triangle"
author: "wano"
excerpt_separator: <!--more-->
tags: Math
use_math: true
---

Pascal's triangle is a triangular array of the binomial coefficients.<!--more-->

두 변수 $a$와 $b$로 이루어진 다항식의 제곱식을 전개하면 다음과 같다.

$$(a+b)^2 = a^2 + 2ab + b^2$$

$$(a+b)^3 = a^3 + 3a^2b + 3ab^2 + b^3$$

무언가 규칙이 있는 것 같아 보인다. 일반적인 자연수 $n(= 2, 3, 4, \cdots)$ 에 대한 $(a+b)^n$의 전개는 어떻게 될까?

$(a+b)^n$을 전개한 식의 $k$번째 항의 계수를 $_{n} C _{k-1}$라 하면 다음과 같이 쓸 수 있다.

$$(a+b)^n = _{n} C _{0} a^n b^0 + _{n} C _{1} a^{n-1} b^1 + \cdots + _{n} C _{k-1} a^{n-k+1} b^{k-1} + _{n} C _{k} a^{n-k} b^k + \cdots + _{n} C _{n} a^0 b^n $$

위의 식은 $a$에 대한 내림차순으로 정리한 식으로 $a^n b^0$항을 시작으로 $a$의 차수는 1씩 감소하고, $b$의 차수는 1씩 증가하여 총 $n+1$개의 항을 가지는 다항식이다.
