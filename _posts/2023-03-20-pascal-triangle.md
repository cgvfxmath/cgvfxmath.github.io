---
layout: post
title: "Pascal's Triangle"
author: "wano"
excerpt_separator: <!--more-->
tags: Math
use_math: true
---

Pascal's triangle is a triangular array of the binomial coefficients.<!--more-->

다음과 같이 두 변수 $a$와 $b$로 이루어진 이항식(二項式, binomial = 항이 2개인 다항식)의 거듭제곱식을 전개하면 다음과 같다.

<p style="text-align: center;">$(a+b)^2 = a^2 + 2ab + b^2$</p>
<p style="text-align: center;">$(a+b)^3 = a^3 + 3a^2b + 3ab^2 + b^3$</p>

무언가 규칙이 있는 것처럼 보인다. 일반적인 자연수 $n(= 1, 2, 3, 4, \cdots)$에 대한 $(a+b)^n$의 전개는 어떻게 될까?

$(a+b)^n$을 전개한 식의 $k$번째 항의 계수를 $_{n} C _{k-1}$라 하면 다음과 같이 쓸 수 있다.

<p style="text-align: center;">$(a+b)^n = _{n} C _{0} a^n b^0 + _{n} C _{1} a^{n-1} b^1 + \cdots + _{n} C _{k-1} a^{n-k+1} b^{k-1} + _{n} C _{k} a^{n-k} b^k + \cdots + _{n} C _{n} a^0 b^n$</p>

위의 식은 $a$에 대한 내림차순으로 정리한 식으로 $a^n b^0$항을 시작으로 $a$의 차수는 1씩 감소하고, $b$의 차수는 1씩 증가하여 총 $n+1$개의 항을 가지는 다항식이다. 이처럼 이항식의 거듭제곱을 일련의 단항식들의 합으로 전개하는 것을 이항정리(二項定理, binomial theorem)라고 한다.

여기서 $_{n} C _{k-1}$의 $C$는 계수(coefficient)의 약자로 사용되었지만 조합(combination)의 의미 또한 가진다. 이와 관련된 내용은 뒤에서 다시 살펴보겠다.

한편 마찬가지 방법으로 차수가 하나 작은 $(a+b)^{n-1}$을 전개한 식의 $k$번째 항의 계수를 $_{n-1} C _{k-1}$라 할 수 있으므로 $(a+b)^{n-1}$을 전개하면 다음과 같다.

<p style="text-align: center;">$(a+b)^{n-1} = _{n-1} C _{0} a^{n-1} b^0 + _{n-1} C _{1} a^{n-2} b^1 + \cdots + _{n-1} C _{k-1} a^{n-k} b^{k-1} + _{n-1} C _{k} a^{n-k-1} b^k + \cdots$</p>

여기서 $a^{n-k-1} b^k$보다 뒤에 있는 항들은 중요하지 않으므로 생략하였다.

그런데 $(a+b)^n = (a+b)^{n-1} (a+b)$이므로 $(a+b)^n$의 $k+1$번째 항은 $(a+b)^{n-1}$의 $k$번째 항과 $k+1$ 항에 각각 $b$와 $a$를 곱해서 만들어지는 것을 알 수 있다.

<p style="text-align: center;">$\cdots + _{n} C _{k} a^{n-k} b^{k} + \cdots = (\cdots + _{n-1} C _{k-1} a^{n-k} b^{k-1} + _{n-1} C _{k} a^{n-k-1} b^{k} + \cdots) \times (a+b)$</p>

위의 식이 복잡하게 보이지만 사실 단순한 분배법칙을 적용한 것에 불과하기 때문에 천천히 따져보면 어렵지 않게 이해할 수 있다.

1. $(a+b)^{n}$의 $k+1$번째 항: $_{n} C _{k} a^{n-k} b^{k}$
2. $(a+b)^{n-1}$의 $k$번째 항: $_{n-1} C _{k-1} +  a^{n-k} b^{k-1}$ (위의 1번 항과 비교하여 $b$의 차수가 하나 작음)
3. $(a+b)^{n-1}$의 $k+1$번째 항: $_{n-1} C _{k} a^{n-k-1} b^{k}$ (위의 1번 항과 비교하여 $a$의 차수가 하나 작음)

즉, 2번 항의 계수와 3번 항의 계수가 합해져서 1번 항의 계수가 된다. 따라서 다음과 같은 사실이 성립합을 알 수 있다.

<p style="text-align: center;">$\color{red}{_{n} C _{k} = _{n-1} C _{k-1} + _{n-1} C _{k}}$</p>

위의 수식이 이번 포스팅의 핵심 내용이다.

이 등식을 3개의 6각형을 사용하여 도식화하면 다음과 같다.
![img](https://cgvfxmath.github.io/assets/Pascal_Triangle_01.png)

이것을 모든 자연수 $n$과 $k$에 대해서 일반화하여 그리면 다음과 같다.
![img](https://cgvfxmath.github.io/assets/Pascal_Triangle_02.png)

임의의 수에 0을 더하면 원래의 수와 같기 때문에 다음과 같이 가상의 0으로 둘러싸인 개념으로 생각할 수도 있다.
![img](https://cgvfxmath.github.io/assets/Pascal_Triangle_03.png)

이러한 삼각형을 파스칼의 삼각형(Pascal’s Triangle)이라고 한다. 인도의 수학자들은 이것을 “메루산의 계단”이라는 이름으로 불렀고, 이란과 중국에서는 각각 “카얌 삼각형”과 “양휘의 삼각형”이라고 불렀으나, 후대에 프랑스의 수학자인 파스칼이 집대성하여 그의 이름이 붙여졌다고 한다.

파스칼의 삼각형을 이용하면 이항식을 전개한 각 항의 계수를 쉽게 구할 수 있다. 각 행(row)의 숫자가 차례대로 $(a+b)^n$를 전개한 항의 계수이기 때문이다.
![img](https://cgvfxmath.github.io/assets/Pascal_Triangle_04.png)

파스칼의 삼각형이 유명해진 이유는 이 외에도 여러 가지 신기한 성질들을 가지기 때문이다. 파스칼의 삼각형이 가지는 몇 가지 대표적인 패턴은 다음과 같다.

성질 1) 파스칼의 삼각형은 좌우대칭이다.

성질 2) 다음과 같은 위치의 숫자들을 순서대로 나열하면 자연수들의 집합이 된다.
![img](https://cgvfxmath.github.io/assets/Pascal_Triangle_05.png)

성질 3) 다음과 같은 위치의 숫자들은 정삼각형을 구성하는 점들의 개수를 의미한다.
![img](https://cgvfxmath.github.io/assets/Pascal_Triangle_06.png)

성질 4) 각 행을 모두 합한 수는 2의 거듭제곱과 같다.
![img](https://cgvfxmath.github.io/assets/Pascal_Triangle_07.png)

성질 5) 파스칼의 삼각형 안에는 피보나치 수열(Fibonacci sequence)가 숨어있다.
![img](https://cgvfxmath.github.io/assets/Pascal_Triangle_08.png)

앞에서 $_{n} C _{k-1}$는 조합(combination)을 의미한다고 언급하였다. 즉, $n$개 중에서 $k-1$개를 순서없이 뽑는 경우의 수를 의미한다. $(a+b)^n$을 전개한 식의 $k$번째 계수는 두 개의 구슬 $a$와 $b$를 가지는 $n$개의 주머니에서 순서에 상관없이 $k-1$개를 뽑는 것과 같은 경우의 수를 가지기 떄문이다.

$n$개 중에서 순서대로 $k$개를 뽑는 경우의 수는 순열(permutation)이다. 제일 처음에 $n$개 중 한 개, 그 다음에는 이미 뽑은 것을 제외한 $n-1$개 중 한 개, 그 다음에는 앞에서 뽑은 것을 제외한 $n-2$개 중 한 개, $cdots$ 이런 방식으로 $k$번 뽑는 경우의 수이기 때문에 순열은 다음과 같이 정의한다.

<p style="text-align: center;">$_{n} P _{k} = n(n-1)(n-2) \cdots (n-k+1)$</p>

이 식의 분자와 분모에 각각 $(n-k)!$를 곱해서 변형하면 다음과 같은 순열에 대한 공식을 얻을 수 있다.

<p style="text-align: center;">$_{n} P _{k} = {n(n-1)(n-2) \cdots (n-k+1)(n-k)!} / {(n-k)!} = {n!} / {(n-k)!}$</p>

조합(combination)은 순열(permutation)에서 $k$개에 대한 순서를 제거한 것이기 때문에 $_{n} P _{k}$를 $k$개를 순서대로 나열하는 경우의 수인 $k!$로 나누면 얻을 수 있다.

<p style="text-align: center;">$_{n} C _{k} = { _{n} P _{k} } / { k! } = { n! } / { (n-k)! k! }$</p>

이항정리를 이용하여 다음과 같은 항등식을 얻을 수 있다. ($a=1$, $b=x$를 대입)
<p style="text-align: center;">$(1+x)^n = _{n} C _{0} x^0 + _{n} C _{1} x^1 + _{n} C _{2} x^2 + \cdots + _{n} C _{n} x^n $</p>

1. 양변에 $x=1$을 대입하면 다음과 같은 공식을 얻을 수 있다. (이항계수들의 총합)
<p style="text-align: center;">$_{n} C _{0} + _{n} C _{1} + _{n} C _{2} + \cdots + _{n} C _{n} = 2^n$</p>

2. 양변에 $x=-1$을 대입하면 다음과 같은 공식을 얻을 수 있다.
<p style="text-align: center;">$_{n} C _{0} - _{n} C _{1} + _{n} C _{2} + \cdots + (-1)^n \cdot _{n} C _{n} = 0$</p>

3. 위의 두 식을 더한 후 2로 나누면 다음과 같은 공식을 얻을 수 있다. (홀수 번째 항의 계수들의 총합)
<p style="text-align: center;">$_{n} C _{0} + _{n} C _{2} + _{n} C _{4} + \cdots + = 2^{n-1}$</p>

4. 위의 두 식을 뺀 후 2로 나누면 다음과 같은 공식을 얻을 수 있다. (짝수 번째 항의 계수들의 총합)
<p style="text-align: center;">$_{n} C _{1} + _{n} C _{3} + _{n} C _{5} + \cdots + = 2^{n-1}$</p>

따라서 (홀수 번째 항의 계수들의 총합)과 (짝수 번째 항의 계수들의 총합)은 같음을 알 수 있다.
