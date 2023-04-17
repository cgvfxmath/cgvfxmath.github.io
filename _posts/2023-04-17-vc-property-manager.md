---
layout: post
title: "VC Property Manager"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev', 'visual studio']
use_math: true
lastmode: 2023-04-17 01:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

How to inherit project environment settings in Visual Studio<!--more-->

Visual Studio에서  작업을 하다 보면 하나의 솔루션(solution) 안에 여러 개의 프로젝트(project)를 만들어서 관리해야 하는 경우가 생긴다. 이때 각 프로젝트 마다 개별적으로 설정을 해주는 것은 여간 귀찮은 일이 아니다. (예를 들면, 헤더 파일이 있는 디렉토리 경로 지정 등) 이러한 문제를 해결하고자 Visual Studio에서는 하나의 프로젝트 설정으로 여러 개의 프로젝트의 속성을 관리할 수 있는 방법을 제공한다.

보기(V) > 다른 창(E) > 속성 관리자(Property Manager)를 선택한다.

<center><figure><img src="https://cgvfxmath.github.io/assets/img/VC_Property_Manager01.jpg" width="90%"></figure></center>
<br/>

Visual Studio 버전에 따라 메뉴 위치가 다를 수 있는데, 만약 위의 그림과 다르다면 Visual Studio의 검색창(Ctrl+Q)에서 "속성 관리자"를 입력하면 된다.

원하는 모드에 속성을 추가한다.

<center><figure><img src="https://cgvfxmath.github.io/assets/img/VC_Property_Manager02.jpg" width="90%"></figure></center>
<center><figure><img src="https://cgvfxmath.github.io/assets/img/VC_Property_Manager03.jpg" width="90%"></figure></center>
<center><figure><img src="https://cgvfxmath.github.io/assets/img/VC_Property_Manager04.jpg" width="90%"></figure></center>
<br/>

새로 추가한 속성 시트에 공통된 설정을 해준다.

<center><figure><img src="https://cgvfxmath.github.io/assets/img/VC_Property_Manager05.jpg" width="90%"></figure></center>
<center><figure><img src="https://cgvfxmath.github.io/assets/img/VC_Property_Manager06.jpg" width="90%"></figure></center>
<br/>

이렇게 하면 PropertySheet.pros 라는 파일이 생기는데, 각 프로젝트 별로 이 파일을 "기존 속성 시트 추가"로 읽어들여 주면 된다.

<center><figure><img src="https://cgvfxmath.github.io/assets/img/VC_Property_Manager07.jpg" width="90%"></figure></center>
<br/>

공통 속성 시트에 설정한 내용을 개별 프로젝트에 적용해주려면 각 프로젝트 속성의 항목에서 "부모 또는 프로젝트 기본값에서 상속"을 선택해주면 된다. 대부분 이 옵션이 체크되어 있기 때문에 속성 관리자(Property Manager)에서 프로젝트 별로 PropertySheet.pros 파일만 import해주면 된다.

<center><figure><img src="https://cgvfxmath.github.io/assets/img/VC_Property_Manager08.jpg" width="90%"></figure></center>
<br/>