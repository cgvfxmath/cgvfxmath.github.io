---
layout: post
title: "Linux Memory Mechanism"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev', 'linux']
use_math: true
lastmode: 2023-03-29 09:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Information collected from the web about the memory usage mechanism in Linux<!--more-->

리눅스 시스템의 메모리 사용 방식은 윈도우즈와 다르다. 리눅스는 커널(kernel)이 메모리를 제어한다. 그런데 데이터를 디스크에서 읽어 오는 것보다 메모리에서 읽어오는 것이 훨씬 효율적이기 때문에 (대략 1000배 정도) 리눅스 커널(kernel)은 시스템 성능의 향상을 위해서 최근 사용한 것들을 그때마다 바로 지워버리지 않고 메모리상에 캐쉬화(caching)해서 남겨 둔다. 용량이 큰 파일을 처음 로드할 때 보다 그 다음에 로드할 때 속도가 더 빨라지는 것은 이러한 이유 때문이다.

쉘(shell)에서 **free -m** (-m 옵션은 MB 단위로 출력) 명령어를 실행해보면 현재 메모리 사용 내용을 볼 수 있다.

예를 들면, 8기가 메모리가 장착되어 있는 시스템에서 **free -m**을 실행하게 되면 다음과 같은 항목들을 확인할 수 있다.
* <span style="color:blue">**total: 7986**</span>
* <span style="color:red">**used: 6004**</span>
* <span style="color:green">**free: 1982**</span>
* <span style="color:gray">**shared: 0**</span>
* <span style="color:goldenrod">**buffers: 42**</span>
* <span style="color:purple">**cached: 2156**</span>

여기서 <span style="color:blue">**total(7986)**</span>은 장착되어 있는 전체 메모리 용량이므로 다음과 같은 관계가 성립한다.

<span style="color:blue;font-weight:bold">total(7986)</span>
<span style="color:black;font-weight:bold"> = </span>
<span style="color:red;font-weight:bold"> used(6004) </span>
<span style="color:black;font-weight:bold"> + </span>
<span style="color:green;font-weight:bold"> free(1982) </span>

다음 줄에 출력되는 내용은 다음과 같다.

<span style="color:black;font-weight:bold"> -/+ buffer/cache: </span>
<span style="color:darkorange;font-weight:bold">used(3805)</span>
<span style="color:black;font-weight:bold">, </span>
<span style="color:chartreuse;font-weight:bold">free(4181)</span>

이것은 어플리케이션의 관점에서 보는 내용이다. 역시 다음과 같은 관계식이 성립한다.

<span style="color:blue;font-weight:bold">total(7986)</span>
<span style="color:black;font-weight:bold"> = </span>
<span style="color:darkorange;font-weight:bold">used(3805)</span>
<span style="color:black;font-weight:bold"> + </span>
<span style="color:chartreuse;font-weight:bold">free(4181)</span>

또한 다음과 같은 관계식도 성립한다.

<span style="color:red;font-weight:bold"> used(6004) </span>
<span style="color:black;font-weight:bold"> = </span>
<span style="color:darkorange;font-weight:bold">used(3805)</span>
<span style="color:black;font-weight:bold"> + </span>
<span style="color:goldenrod;font-weight:bold">buffers(42)</span>
<span style="color:black;font-weight:bold"> + </span> 
<span style="color:purple;font-weight:bold">cached(2156)</span>

<span style="color:black;font-weight:bold">-/+ buffer/cache</span>에 표시되는 내용이 "System Monitor"에 출력되는 "User Memory"라고 생각하면 된다.

참고로 8기가 메모리가 장착되어 있다면 <span style="color:blue;font-weight:bold">total</span>에 8192가 표시되어야 하지만 7986으로 표시되어 차이가 나는 이유는 커널(kernel)이 상주하는 영역 때문이며 (이 영역은 swap되면 안되므로 아예 배제시킴), 또한 하드웨어 또는 다른 시스템 아키텍쳐에 사용을 위해 남겨둔 영역이 있기 때문이다.

리눅스 부팅 후 이것저것 프로그램들을 사용하게 되면 <span style="color:red;font-weight:bold">used</span>와 <span style="color:purple;font-weight:bold">cached</span>는 계속 증가하고, 반대로 <span style="color:chartreuse;font-weight:bold">free</span>는 계속 감소하는 것을 확인할 수 있는데, 앞에서 설명한 이유로 크게 걱정하지 않아도 된다.

<span style="color:purple;font-weight:bold">cached</span> 영역은 언제든지 임의 어플리케이션에 의해서 사용될 수 있는 free영역으로 생각하면 된다. (앞의 예제에서는 전체 메모리 용량중에 <span style="color:purple;font-weight:bold">cached(2156)</span>를 디스크 캐쉬 용도로 사용하고 있음.) 어쨌든 <span style="color:darkblue;font-weight:bold">Swap used = 0</span>이라면 메모리가 부족하여 디스크를 가상 메모리로 사용하게되는 상태는 아니라고 이해하면 된다.

만약 <span style="color:purple;font-weight:bold">cached</span> 영역을 강제로 삭제하고 싶다면 다음과 같이 1,2,3 중에 하나의 값을 설정해서 drop_caches를 이용하면 된다. (커널 버전 2.6.16 이상에서 사용 가능)

* To free pagecache
echo 1 > /proc/sys/vm/drop_caches

* To free dentries and inodes
echo 2 > /proc/sys/vm/drop_caches

* To free pagecache, dentries and inodes
echo 3 > /proc/sys/vm/drop_caches

단 수행하기 점에 sync 명령어를 먼저 실행하는 것을 권장한다.

As this is a non-destructive operation, and dirty objects are not freeable, the user should run "sync" first in order to make sure all cached objects are freed.
