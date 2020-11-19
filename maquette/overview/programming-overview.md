---
title: 프로그래밍 개요
description: 스크립팅을 사용 하 여 Maquette 개체 및 인터페이스에 액세스 하는 방법을 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, 프로토타입, 혼합 현실, 가상 현실, VR, MR, 피드백, 피드백 허브, 버그
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935605"
---
# <a name="programming-overview"></a>프로그래밍 개요

<!-- TODO(Harrison): Need consolidated logo with text -->

![로고](../images/MaquetteIcon.png) 프로그래밍 개요

Microsoft Maquette는 [Jint](https://github.com/sebastienros/jint) 인터프리터에 따라 JavaScript (확장에 ECMAScript 5.1)를 사용 합니다. 확장은 `.mqjs` 일반 javascript에서 Maquette javascript 파일을 구분 하는 데 사용 됩니다.

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
Maquette 개체 및 인터페이스는 개체를 통해 액세스 하 고 스크립팅할 수 있습니다 `Maquette` . Maquette 개체 및 인터페이스에 대 한 설명서는 Maquette의 API 참조에서 제공 됩니다.

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
MaquetteScript는 새로운 추가 및 flux 이므로 변경이 필요 합니다. 더 자세한 설명서와 업데이트가 곧 제공 될 예정입니다.

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a>스크립팅에 집중

* TBD-샘플/자습서로 포커스가 있는 스크립팅 집중
  * 2x 이미지/캡션 – 스포트라이트 페이지에 연결

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a>MaquetteScript 시작 하기

* Mqjs 및 .JS
* 프로그래밍 모델
  * 편집 및 실행 중
* 프로그래밍 워크플로 링크
* 공유 결과에 대 한 링크

## <a name="programming-workflow"></a>프로그래밍 워크플로

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
TBD
* REPL
* 스크립팅 작업
* 디버거 작업
* 디버깅 루프
* 코드를 복사 하 여 붙여 넣으 시겠습니까?

## <a name="running-mqjs-scripts"></a>Mqjs 스크립트 실행

<!-- TODO(Stefan): Need screenshot -->
MaquetteScript 파일을 실행 하려면 Maquette의 부록 창으로 이동 하 여 스크립팅 탭을 열고 스크립트를 찾습니다.

> [!NOTE] 
> 일부 옵션은 스크립트를 제공 하지 않았으므로 아직 작동 하지 않습니다.

## <a name="vscode-editor-workflow"></a>VSCode 편집기 워크플로

VSCode 내에서 Maquette의 스크립트를 평가 하려면 사용자가 두 가지 명령을 알고 있어야 합니다.

   `CTRL-5` 선택한 텍스트 또는 커서가 있는 전체 줄을 계산 합니다. 

   `CTRL-SHIFT-5` 전체 파일을 평가 합니다.

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
텍스트는 JavaScript 환경에서 계산 되는 Maquette로 전송 되며, 결과는 VSCode의 출력 콘솔로 다시 전송 됩니다. 이를 REPL (읽기-평가-인쇄-루프)으로 사용할 수 있습니다.

## <a name="example-first-step"></a>예제 첫 번째 단계

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
VSCode의 파일에 다음 코드를 복사 합니다.

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
코드 또는 섹션을 선택 하 고 `CTRL-5` 실행 하도록 적중 합니다. 이렇게 하면 큐브가 생성 되 고 앞에 놓고 색이 변경 됩니다.

확장을 통해 더 많은 예제를 찾을 수 있습니다.

## <a name="sharing-results"></a>결과 공유

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
사용자/팀 간에 공유 하는 방법
* Documents 디렉터리의 Zip 프로젝트
* 프로젝트를 파일 공유에 복사
* Maquette 팀에 팀 공유 서브 미션의 파일 위치 추가

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
TBD
* 포함, 상대/절대 경로를 사용 하는 코드에 대 한 참조, 모듈
* 라이브러리인?
* 런타임 지원
* 확인 되지 않은 외부-항목이 누락/충돌 하는 경우의 동작
* 특정 개체와 연결 된 스크립트를 추가/편집/관찰할 수 있나요?
  * 이 스크립트를 다른 곳에 복사/붙여 넣을 수 있나요?
  * 개체 속성은 무엇 인가요?
  * 내 장면에서 개체의 이름을 지정 하 시겠습니까? (스크립트 이름 바꾸기)
  * 개체와 연결 된 스크립트에 대 한 THIS 또는 SELF 키워드
  * 개체를 마우스 오른쪽 단추로 클릭 하면 해당 개체와 관련 된 코드 (및 모든 계층 구조)를 볼 수 있습니다.
  * UI에서 선택 하 여 VSCode의 코드에서 가져올 수 있나요?
  * 스크립트 소스 파일에서 개체와 연결 된 코드를 "함께" 유지
  * 개체를 클릭할 때 속성 창을 개체 위로 가져오기 VR 및 주 탭에서
* 보안 문제
* 테스트-TBD 일 수 있지만 스크립트를 통해 비디오 또는 프레임 잡기를 제안할 수 있습니다.
* 버그 보고 메커니즘이 있는 경우 다른 사용자를 위해 스크립트를 통해 액세스할 수 있도록 설정할 수 있습니다. 후반
* 배포 – 결과를 "공유" 하는 방법, EXE로 패키지
* 데모 또는 spectating/모니터링 실행/제어
* 플레이어 모드
* 공유를 위해 "구성 요소"를 만드는 방법에 대 한 세그먼트가 있을 수 있습니다. (tbd 일 수 있음)
  * #Include 있나요? 이는 네임 스페이스 충돌이 있는 것으로 가정 하 고 있는 순수한 JS를 처리 합니다.
  * Maquette가 JS 코드와 일치 하도록 명명 된 개체와 다른 maquette를 통합 하기 위해 수행할 수 있는 작업은 무엇 인가요?
