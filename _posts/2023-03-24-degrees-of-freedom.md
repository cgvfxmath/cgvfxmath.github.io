---
layout: post
title: "DoF"
author: "wano"
excerpt_separator: <!--more-->
tags: ['math', 'physics', 'mechanics', 'XR']
use_math: true
lastmode: 2023-03-24 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Degrees of Freedom is the number of independent parameters that define its configuration or state.<!--more-->

다음은 SIGGRAPH Asia 2019 XR Presentations & Talks에 대한 소개입니다.

<center><figure><img src="https://cgvfxmath.github.io/assets/img/dof_01.png" width="90%"><figcaption>그림 출처: https://sa2019.siggraph.org/attend/xr/session_slot/494</figcaption></figure></center>
<br/>

여기서 등장하는 6Dof란 무엇일까요?

우선 DoF는 “Degree of Freedom”의 약자로 자유도(自由度)라는 의미입니다.

자유도의 의미를 다음의 두 가지 간단한 예를 통해서 살펴보겠습니다.

<center><figure><img src="https://cgvfxmath.github.io/assets/img/dof_02_03.png" width="90%"></figure></center>
<br/>

왼쪽 그림에서 중력이 없다고 가정하면 스프링 끝에 달려 있는 질점은 좌우로만 왔다 갔다 하게 됩니다. 이러한 경우의 자유도는 1입니다. 왜냐하면 질점의 변위를 $x$라는 하나의 변수로 기술할 수 있기 때문입니다.

오른쪽 그림은 대표적인 3차원 저작툴인 Autodesk Maya에서 사용하는 manipulator의 모습입니다. 여기서 말하는 manipulator란 선택한 물체의 자세(pose) 및 크기(size)를 직관적으로 수정할 수 있도록 도와주는 GUI(Graphical User Interface) 요소를 말합니다. 이처럼 3차원 이동(translation), 회전(rotation), 크기(scale)를 모두 변경할 수 있는 manipulator의 자유도는 9입니다. 왜냐하면 이동(tx, ty, tz), 회전(rx, ry, rz), 크기(sx, sy, sz) 이렇게 총 9개의 변수로 움직임을 기술할 수 있기 때문입니다.

이제 우리는 자유도의 의미를 대략적으로 알게 되었습니다.

보다 엄밀한 자유도의 정의는 다음과 같습니다.
* 주어진 시스템에서 독립적으로 달라질 수 있는 매개 변수의 개수
* 주어진 조건 하에서 자유롭게 변화할 수 있는 변인의 수

따라서 앞에서 언급한 “6 DoF video”란 촬영된 영상을 보는 이용자가 6개의 자유도를 가지고 움직이면서 시점을 변화시킬 수 있는 동영상 매체라는 것을 의미합니다.

3차원 물체의 자세(pose)는 다음과 같이 6개의 변수로 나타낼 수 있습니다. (이동 3개, 회전 3개)

<center><figure><img src="https://cgvfxmath.github.io/assets/img/dof_04.gif" width="80%"><figcaption>그림 출처: https://alex4d.com/notes/item/what-is-six-degrees-of-freedom-360-video</figcaption></figure></center>
<br/>

참고로 3차원 회전은 회전의 중심이 되는 좌표축의 종류에 따라서 yaw, roll, pitch라는 이름으로 불리는데, 이것은 자동차, 선박, 항공기 등의 자세를 표현할 때 일반적으로 사용되는 개념이기 때문에 상식적인 수준에서 알아두면 좋습니다.

<center><figure><img src="https://cgvfxmath.github.io/assets/img/yaw_roll_pitch.gif" width="80%"><figcaption>그림 출처: https://gfycat.com/ko/discover/pitch-roll-yaw-gifs</figcaption></figure></center>
<br/>

현재 6 DoF의 사용자 경험을 구현하기 위해서 가장 많이 사용하는 방식은 360 video입니다. 다음과 같은 특수 카메라를 이용하여 주변의 모든 경도(longitude)와 위도(latitude)에 대한 시각 정보를 저장할 수 있는 방식입니다.

<center><figure><img src="https://cgvfxmath.github.io/assets/img/dof_05.png" width="80%"><figcaption>그림 출처: https://www.onsetfacilities.com/look-facebooks-new-360-volumetric-video-cameras</figcaption></figure></center>
<br/>

이렇게 만들어진 360 형식의 동영상을 구(sphere)에 매핑(mapping)해서 보여주면 사용자는 자신의 위치를 중심으로 자유도를 얻을 수 있습니다.

<center><figure><img src="https://cgvfxmath.github.io/assets/img/dof_06_07.png" width="80%"><figcaption>그림 출처: https://wordpress.discretization.de/houdini/home/advanced-2/textures</figcaption></figure></center>
<center><figure><img src="https://cgvfxmath.github.io/assets/img/dof_08.png" width="80%"><figcaption>그림 출처: https://www.pinterest.co.kr/pin/216946907035230677</figcaption></figure></center>
<br/>

하지만 이러한 방식은 회전(rotation)에 비해 이동(translation)에 대한 자유도 범위가 넓지 않아 진정한 의미의 6 DoF 콘텐츠라고 보기는 어렵습니다. 진정한 의미의 6 DoF를 경험하려면 실시간(real-time)으로 사용자의 위치(position)와 방향(orientation)을 추척(tracking)하고 해당 시야에 맞는 360도 영상을 렌더링(rendering)하는 full interactive VR 기술이 필요합니다.

<center><figure><img src="https://cgvfxmath.github.io/assets/img/dof_09.png" width="80%"><figcaption>그림 출처: https://toast.gg/4-things-to-know-about-vr-before-you-buy-a-headset</figcaption></figure></center>
<center><figure><img src="https://cgvfxmath.github.io/assets/img/dof_10.png" width="80%"><figcaption>그림 출처: https://www.gsmarena.com/samsungs_next_vr_headset_will_have_insideout_tracking-news-28375.php</figcaption></figure></center>
<br/>

이와 더불어 특수한 음향(sound) 효과가 제공된다면 콘텐츠를 체험하는 사용자의 몰입감은 더욱 높아질 수 있습니다.

<center><figure><img src="https://cgvfxmath.github.io/assets/img/dof_11.png" width="80%"><figcaption>그림 출처: https://developer.qualcomm.com/blog/designing-user-freedom-vr</figcaption></figure></center>
<br/>
