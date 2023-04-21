---
layout: post
title: "Maya Context"
author: "wano"
excerpt_separator: <!--more-->
tags: ['maya', 'dev']
use_math: true
lastmode: 2023-03-23 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Maya context is a UI element in Autodesk Maya<!--more-->

Autodesk Maya에서 context란 마우스의 이벤트에 반응하여 어떠한 특정 작업 수행이 가능한 Maya의 특수 모드를 말합니다. Maya에서의 context는 tool과 동일한 개념으로 사용됩니다. (graphical user interface 기준에서는 tool이고, programming interface 기준에서는 context라고 이해하면 됩니다.)

"setToolTo [context name]" 명령어를 사용하여 특정 context 모드로 들어갈 수 있습니다. 현재 어떠한 context 모드에 있는지 알 수 있는 명령어는 currentCtx입니다.

다음과 같은 세 가지 API 클래스를 상속받아서 자신만의 custom context를 만들 수 있습니다.
1. MPxContext
2. MPxContextCommand
3. MPxToolCommand

* MPxContext가 실제 컨텍스트 구현부를 담당하고, MPxContextCommand가 컨텍스트 등록을 담당합니다.

* MPxToolCommand의 사용은 필수사항은 아니지만, 만약 undo/redo 기능을 사용하려면 반드시 있어야 합니다.

* MPxContext의 doPress(), doDrag(), doRelease() 함수를 이용하여 원하는 기능을 구현하면 되는데, 보통의 경우 doRelease()가 호출되었을 때 새로운 MPxToolCommand를 만들고, MPxToolCommand의 redoIt(), finalize() 함수를 호출하게 되면 자동적으로 undo/redo 기능을 사용할 수 있게 됩니다.

Context 실행시 각 함수들의 실행순서는 다음과 같습니다.

* 플러그인을 로드하면..   
MPxContextCommand::creator()   
MPxContextCommand::MPxContextCommand()   

* setToolTo를 실행하면..   
MPxContextCommand::appendSyntax()   
MPxContextCommand::makeObj()   
MPxContext::MPxContext()   
MPxConTextCommand::doEditFlags()   
MPxContextCommand::doQueryFlags()   
MPxContext::toolOnSetup()   
MPxContext::getClassName()   

* 마우스 버튼을 클릭, 드래그를 하면..   
MPxContext::doPress()   
MPxContext::doDrag()   
...   
MPxContext::doDrag()   

* 마우스 버튼을 떼면..   
MPxContext::doRelease()   
MPxToolCommand::newSyntax(): 처음 한 번만 호출됨   
MPxToolCommand::creator()   
MPxToolCommand::MPxToolCommand()   
MPxToolCommand::redoIt()   
MPxToolCommand::finalize()   

* undo를 실행하면..   
MPxToolCommand::undoIt()   

* redo를 실행하면..   
MPxToolCommand::redoIt()   

* Context를 빠져나오면..   
MPxContext::toolOffCleanup()   
