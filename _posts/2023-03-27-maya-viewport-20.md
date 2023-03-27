---
layout: post
title: "Maya Viewport 2.0"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev', 'maya']
use_math: true
lastmode: 2023-03-27 00:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Viewport 2.0 is the viewport and hardware renderer in Maya<!--more-->

Viewport 2.0(이하 VP2)은 Maya 2012 부터 도입된 Autodesk사의 새로운 rendering architecture이다. VP2는 AutoCAD와 3ds MAX 등의 제품군에서도 활용되는 backend system이다. VP2는 programmable shader system, high-quality per-pixel lighting 등의 강력한 기능을 제공한다. 하지만 완전히 새로운 rendering system이기 때문에 기존에 만들어 놓은 plug-in들을 지원하지 않는다. 예를들면 custom locator node는 Legacy Default Viewport에서만 작동하고 VP2에서는 draw() 함수가 호출조차 되지 않는다. Custom locator node에서 OpenGL을 이용해서 그린 결과가 VP2에서 나타나게 하려면 추가적인 조치가 필요하다. VP2 기능 구현을 위한 class들은 MHWRender namespace 내에 정의되어 있으며 OpenMayaRender SDK를 이용하여 구현할 수 있다. VP2의 가장 큰 문제는 제 3의 rendering architecture이기 때문에 Maya 내에서 무언가를 drawing하고 VP2가 지원하는 형식의 data로 만들어주는 과정이 매우 복잡하다는 점이다.

MPxLocatorNode에서 상속받은 custom locator node의 경우 MPxDrawOverride에서 상속받는 class를 구현하고 MPxDrawOverride::draw(const MHWRender::MDrawContext&, const MUserData*) 함수 내에 OpenGL 관련 code를 작성하여 VP2에서 drawing되도록 할 수 있다. 이러한 방법으로 거의 모든 OpenGL 기능들을 사용하는 것이 가능하다. 하지만 이 방법은 picking selection이 작동하지 않는 문제점을 가지고 있다. Maya2016 이하 version에서는 picking selection이 잘 작동하지만 Maya2016 extension 2, Maya2017에서는 pivot point에 대한 marquee selection만 작동하고 picking selection이 작동하지 않는다. Maya2016 extension 2를 기점으로 무언가 내부 구조가 달라진 것으로 추정된다.

Picking selection이 작동하기 위한 방법으로 ${MAYA_INSTALL_PATH}/devkit/plug-ins/footPrintNode 예제를 참고할 수 있다. 이 예제는 addUIDrawables() 함수 안에서 MUIDrawManager를 이용하여 drawing 하는 방법을 제시해주고 있다. 이렇게 MUIDrawManager를 이용하여 그려주게 되면 picking selection 문제가 해결된다. 하지만 MUIDrawManager는 극히 단순한 몇 가지 drawing 기능만 제공하기 때문에 lighting effect, GLSL 등의 기능 구현이 불가능하다.

그 다음으로 생각해볼 수 있는 방법은 MPxSurfaceShape에서 상속을 받는 custom shape node 형식으로 만드는 것이다. Autodesk에서 제공하는 custom shape node 관련 단 하나의 예제는 ${MAYA_INSTALL_PATH}/devkit/plug-ins/apiMeshShape 이다. 이 예제에서는 MPxGeometryOverride를 상속받은 class를 구현하고 이 안에서 vertex buffer를 이용하여 원하는 결과를 VP2에 drawing할 수 있다. (여기서 말하는 vertex buffer는 OpenGL에서 사용하는 vertex buffer object가 아니다. Maya에서 제공하는 MVertexBuffer class를 사용해야 한다.) MPxGeometryOverride는 MPxDrawOverride와 비슷하지만 훨씬 더 복잡한 구조를 가지고 있으며 보다 다양한 기능들을 제공한다. MPxGeometryOverride를 이용하면 picking selection 문제를 해결할 수 있다. 하지만 apiMeshShape 예제는 매우 복잡하다. 특히, apiMeshGeometryOverride.cpp의 경우 3300 line 이상의 긴 code로 이루어져 있으며 그 내용을 정확하게 파악하는 것은 불가능에 가깝다. MPxGeometryOverride를 상속받는 apiMeshGeometryOverride를 내용을 파악하여 원하는대로 변형하는 것보다는 apiMeshGeometryOverride를 그대로 둔 채 (class의 이름만 바꾼 채), 이 class가 원하는 형태에 맞추어서 custom shape node를 만드는 것이 훨씬 더 정신 건강에 좋다.

${MAYA_INSTALL_PATH}/devkit/plug-ins/footPrintNode_GeometryOverride 예제는 MPxGeometryOverride를 이용하여 MPxLocatorNode를 VP2에 drawing하게끔 해주는 예제인데 apiMeshShape 예제보다 훨씬 더 간결하다. 만약 결과값의 단순한 drawing을 원한다면 구조가 매우 복잡한 MPxSurfaceShape 보다는 이 방법을 이용하는 편이 좋다. 하지만 이 예제 역시 apiMeshShape 예제와 마찬가지로 MVertexBuffer class를 이용하여 drawing하는 방식이기 때문에 OpenGL 함수들을 사용할 수 없다. 즉, lighting effect, GLSL 등을 이용하여 내 마음대로 drawing할 수 없다. (보다 정확하게 말하면 사용할 수 있는 방법을 찾아낼 길이 없다. 아직까지 찾아내지 못했다.)

Maya 예제에서 제시하고 있지는 않지만 MPxSurfaceShape과 MDrawOverride(MGeometryOverride가 아닌 MDrawOverride)를 이용하는 방법 또한 가능하다. 이 방식은 MPxSurfaceShapeUI를 구현하지 않고, 제일 처음에 언급한 MPxDrawOverride::draw(const MHWRender::MDrawContext&, const MUserData*) 함수를 이용하여 OpenGL 기능을 마음대로 구현할 수 있기 때문에 output connection이 없이도 update가 되면서, picking selection 기능이 작동할 필요가 없는 경우에 최선의 선택이 될 수 있다.
