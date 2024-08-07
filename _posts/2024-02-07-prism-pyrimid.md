---
layout: post
title: "Prism & Pyramid"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2024-02-07 11:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

The reason why the volume of a pyramid is one-third of that of a prism <!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요. (➔[How-To](https://cgvfxmath.github.io/2023-03-18/math-renderer))*

다음 그림과 같이 밑면의 가로와 세로 길이, 그리고 높이가 각각 $a$, $b$, $h$인 일반적인 사각기둥과 사각뿔이 있다고 생각해 보겠습니다.

<center><img src="https://cgvfxmath.github.io/assets/img/prism_pyramid_01.jpg"></center>

이 사각기둥과 사각뿔의 부피는 다음과 같습니다.

* 사각기둥의 부피: $V_{prism} = a \times b \times h$</p>

* 사각뿔의 부피: $V_{pyramid} = \frac{1}{3} \times a \times b \times h$</p>

즉, 사각기둥의 부피와 사각뿔의 부피 사이에는 다음과 같은 관계식이 성립합니다.

<p style="text-align: center;">$V_{prism} = \frac{1}{3} V_{pyramid}$</p>

여기서 1/3이라는 수가 어떻게 나왔는지는, 정적분을 이용하면 깔끔하게 증명할 수 있습니다. 하지만 여기서는 적분을 사용하지 않고 증명을 해보겠습니다.

앞의 공식처럼 사각뿔의 부피 공식은 다음과 같습니다.

<p style="text-align: center;">$\frac{1}{3} \times$ (밑면의 넓이) $\times$ (높이)</p>

따라서, 다음 두 사각뿔의 부피는 같습니다.

<center><img src="https://cgvfxmath.github.io/assets/img/prism_pyramid_02.jpg"></center>

즉, 형태가 다르더라도 밑면의 넓이와 높이가 같으면 두 사각뿔의 부피는 동일합니다.

이것은 다음 그림과 같이 사각뿔을 잘게 슬라이스(slice) 내어서 수평방향으로 이동한 결과이기 때문이라고 직관적으로 이해할 수도 있습니다.

<center><img src="https://cgvfxmath.github.io/assets/img/prism_pyramid_03.jpg"></center>


=======
밑면의 넓이와 높이가 같을 때, 삼각뿔과 삼각기둥의 부피 사이에는 다음과 같은 관계가 성립합니다.

<center><img src="https://cgvfxmath.github.io/assets/img/prism_pyramid_01.jpg"></center>

여기서 1/3이라는 수가 어떻게 나왔는지는, 정적분을 사용하여 깔끔하게 증명할 수 있습니다. 하지만 여기서는 적분을 사용하지 않고 증명을 해보겠습니다.

우선 형태가 다르더라도 밑면의 넓이와 높이가 같다면 두 사각뿔의 부피는 같습니다.

이것은 다음 그림과 같이 사각뿔을 무한히 얇은 층으로 슬라이싱(slicing) 하여 수평 방향으로 이동시켜서 어떤 형태의 사각뿔도 표현할 수 있기 때문이라고 직관적으로 이해할 수 있습니다.

<center><img src="https://cgvfxmath.github.io/assets/img/prism_pyramid_03.jpg"></center>

이 원리는 밑변의 길이와 높이가 동일한 모든 삼각형의 넓이가 같다는 잘 알려진 사실을 부피로 확장한 개념이기도 합니다.

<center><img src="https://cgvfxmath.github.io/assets/img/prism_pyramid_04.jpg"></center>

사각뿔과 마찬가지 이유로 밑면의 넓이와 높이가 동일한 두 삼각뿔의 부피는 같습니다.

한편, 다음 그림과 같이 삼각기둥(①)은 삼각쐐기(②)와 삼각뿔(③)로 분할할 수 있고, 삼각쐐기(②)는 다시 두 개의 삼각뿔(④와 ⑤)로 분할할 수 있습니다.

<center><img src="https://cgvfxmath.github.io/assets/img/prism_pyramid_02.jpg"></center>

이때 다음과 같은 두 가지 사실이 성립합니다.

* 두 삼각뿔 ④와 ⑤는 밑면(노란색 면)의 넓이가 같고, 높이(노란색 선)가 같기 때문에 부피가 같습니다.

* 두 삼각뿔 ③과 ⑤는 밑면(파란색 면)의 넓이가 같고, 높이(파란색 선)가 같기 때문에 부피가 같습니다.

* ④=⑤ 이고 ③=⑤ 이기 때문에 세 삼각뿔 ③, ④, ⑤는 모두 부피가 같습니다.

따라서 다음과 같은 관계가 성립합니다.

<p style="text-align: center;">③ = ④ = ⑤ = $\frac{1}{3} \times$ ①</p>

이러한 관계는 사각기둥-사각뿔, 오각기둥-오각뿔, 육각기둥-육각뿔, ... 의 경우에 대해서도 마찬가지로 성립합니다. 왜냐하면 임의의 다각뿔은 같은 높이를 가지는 $n$개의 삼각뿔로 분할할 수 있기 때문입니다.

<center><img src="https://cgvfxmath.github.io/assets/img/prism_pyramid_05.jpg"></center>

그리고 이러한 사실은 원기둥-원뿔에도 동일하게 적용됩니다. 왜냐하면 원기둥과 원뿔은 각각 무한각기둥과 무한각뿔이라고 볼 수 있기 때문입니다. 따라서, 원뿔의 부피는 원기둥 부피의 3분의 1이 된다는 사실을 알 수 있습니다.
