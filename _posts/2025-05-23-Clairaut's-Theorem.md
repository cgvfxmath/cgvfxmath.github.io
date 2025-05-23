---
layout: post
title: "Clairaut's Theorem"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math']
use_math: true
lastmode: 2025-05-23 10:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Proof on Clairaut's Theorem<!--more-->

*본 포스트에는 수식이 포함되어 있습니다. 분수 등의 수식이 정상적으로 보이지 않는 경우에는 수식을 마우스 오른쪽 버튼으로 클릭한 후 "Math Renderer"를 SVG로 바꿔주세요. (➔[How-To](https://cgvfxmath.github.io/2023-03-18/math-renderer))*

클레로 정리 (Clairaut's Theorem) $\frac{\partial^2 f}{\partial x_1 \partial x_2} = \frac{\partial^2 f}{\partial x_2 \partial x_1}$를 증명해 보겠습니다.

$f_{xy} = \frac{\partial}{\partial y}f_x(x,y) = \lim_{h\rightarrow 0}\frac{f_x(x,y+h)-f_x(x,y)}{h}$

$= \lim_{h\rightarrow 0} \frac{\lim_{r\rightarrow 0}\frac{f(x+r,y+h)-f(x,y+h)}{r}-\lim_{r\rightarrow 0}\frac{f(x+r,y)-f(x,y+h)}{r}}{h}$

$= \lim_{h\rightarrow 0} \frac{\frac{f(x+h,y+h)-f(x,y+h)}{h} - \frac{f(x+h,y)-f(x,y)}{h}}{h}$

$= \lim_{h\rightarrow 0} \frac{\frac{f(x+h,y+h)-f(x+h,y)}{h} - \frac{f(x,y+h)-f(x,y)}{h}}{h}$

$= \lim_{h\rightarrow 0} \frac{\lim_{r\rightarrow 0}\frac{f(x+h,y+r)-f(x+h,y)}{r}-\lim_{r\rightarrow 0}\frac{f(x,y+r)-f(x,y)}{r}}{h}$

$$

$$

Q.E.D.


