---
title: Unreal의 UMG 및 키보드
description: 영역 없는 동작 그래픽을 사용 하 여 widget에서 UI 시스템을 만드는 방법에 대해 알아봅니다.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, HoloLens 2, 눈 추적, 응시 입력, 헤드 탑재 디스플레이, Unreal engine, 혼합 현실 헤드셋, windows Mixed reality 헤드셋, 가상 현실 헤드셋, 위젯, UI, UMG, Unreal 움직임 그래픽, Unreal Engine, UE, UE4
ms.openlocfilehash: 9f22a5f7a13732727b6b122d385aad7e708a1343
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355407"
---
# <a name="umg-and-keyboard-in-unreal"></a>Unreal의 UMG 및 키보드

UNSUMG (실제 동작 그래픽)는 메뉴 및 텍스트 상자와 같은 인터페이스를 만드는 데 사용 되는 실제 엔진의 기본 제공 UI 시스템입니다. UMG로 빌드된 사용자 인터페이스는 위젯을 구성 합니다. 이 가이드에서는 예를 들어 시스템 키보드를 사용 하 여 새 위젯을 만들고,이를 세계 공간에 추가 하 고, 혼합 현실에서 해당 위젯에 대 한 상호 작용을 사용 하도록 설정 하는 방법을 보여 줍니다. 공식 Unreal Engine [설명서](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)에서 umg에 대해 자세히 알아볼 수 있습니다. 

## <a name="create-a-new-widget"></a>새 위젯 만들기

- 위젯 청사진을 만들어 게임 UI를 레이아웃 합니다.

![Unreal 메뉴에서 위젯 청사진을 추가 하는 스크린샷](images/unreal-umg-img-01.png)

- 새 청사진을 열고 색상표의 구성 요소를 캔버스에 추가 합니다.  이 경우 "Input" 섹션에서 두 개의 텍스트 상자 구성 요소를 추가 했습니다.

![텍스트 위젯 구성 요소가 강조 표시 되 고 확장 된 계층 창의 스크린샷](images/unreal-umg-img-02.png)

- 계층 구조 또는 디자이너 창에서 위젯을 선택 하 고 세부 정보 패널에서 매개 변수를 수정 합니다.  이 경우 위젯 상호 작용할 준비가 되었다는 피드백을 제공 하기 위해 커서가 텍스트 상자를 가리킬 때 몇 가지 기본 "힌트 텍스트"와 색조 색을 추가 했습니다.  텍스트 상자는 다음과 상호 작용할 때 HoloLens의 가상 키보드를 팝 합니다.

![계층 구조 창에서 수정 된 매개 변수의 스크린샷](images/unreal-umg-img-03.png)

- 세부 정보 패널에서 이벤트를 구독할 수도 있습니다.

![세부 정보 패널 이벤트의 스크린샷](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a>세계 공간에 위젯 추가

- 새 행위자를 만들고, 위젯 구성 요소를 추가 하 고, 장면에 행위자를 추가 합니다.

![위젯이 첨부 된 행위자의 스크린샷](images/unreal-umg-img-05.png)

- 위젯의 세부 정보 패널에서 **위젯 클래스** 를 앞에서 만든 위젯 청사진으로 설정 합니다.

![위젯 클래스 집합을 사용 하는 청사진 정보 패널의 스크린샷](images/unreal-umg-img-06.png)

- 텍스트 위젯에 대해 **하드웨어 입력 수신** 이 선택 취소 되어 있는지 확인 하 여 가상 키보드의 텍스트만 업데이트 합니다.

![하드웨어 입력 수신이 있는 상호 작용 섹션의 스크린샷 선택 취소 됨](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a>위젯 상호 작용

UMG 위젯은 일반적으로 마우스에서 입력을 받습니다.  HoloLens 또는 VR에서는 동일한 이벤트를 가져오기 위해 위젯 상호 작용 구성 요소를 사용 하 여 마우스를 시뮬레이션 해야 합니다.

- 새 행위자를 만들고, **위젯 상호 작용** 구성 요소를 추가 하 고, 장면에 행위자를 추가 합니다.

![위젯 상호 작용 구성 요소가 강조 표시 된 새 행위자의 스크린샷](images/unreal-umg-img-08.png)

- 위젯 상호 작용 구성 요소에 대 한 세부 정보 패널에서 상호 작용 거리를 원하는 거리로 설정 하 고, **상호 작용 원본을** **사용자 지정** 으로 설정 하 고, 개발의 경우 **Show Debug** 를 **true** 로 설정 합니다.

![위젯 상호 작용 및 디버깅 구성 요소 속성의 스크린샷](images/unreal-umg-img-09.png)

상호 작용 소스에 대 한 기본값은 "세계" 이며,이는 위젯 상호 작용 구성 요소의 세계 위치를 기준으로 raycasts를 전송 해야 하지만 AR 및 VR에서이는 대/소문자를 표시 하지 않습니다.  개발 중에 "디버그 표시"를 사용 하도록 설정 하 고 마우스로 가리킨 항목 색조를 위젯에 추가 하면 위젯 상호 작용 구성 요소가 필요한 작업을 수행 하 고 있는지 확인 하는 것이 중요 합니다.  해결 방법은 사용자 지정 원본을 사용 하 고 핸드 레이에서 이벤트 그래프에 raycast를 설정 하는 것입니다.  

여기서는 Event Tick에서이를 호출 합니다.

![Event tick의 청사진](images/unreal-umg-img-10.png)

그런 다음, HoloLens 입력에 반응 하는 위젯 상호 작용 구성 요소에 가상 마우스 포인터 이벤트를 추가 합니다.  이 경우 손을 grasped 때 왼쪽 마우스 누르기 이벤트를 보내고 grasped 하지 않을 경우 왼쪽 마우스 릴리스 이벤트를 보냅니다.

![가상 마우스 포인터 이벤트가 추가 된 청사진](images/unreal-umg-img-13.png)

이제 HoloLens 2에 앱을 배포 하는 경우 오른쪽에서 연장 된 손 모양으로 표시 됩니다. 편집 가능한 텍스트 상자와 공중 탭 중 하나를 사용 하는 경우 시스템 키보드는 앞에 표시 되며 텍스트를 입력할 수 있습니다. 
 
> [!NOTE]
> HoloLens 시스템 키보드에는 Unreal Engine 4.26 이상이 필요 합니다. 또한 앱이 장치에서 실행 되는 경우에만 Unreal 편집기에서 헤드셋으로 스트리밍되는 경우 키보드가 나타나지 않습니다.

## <a name="see-also"></a>참고 항목:
* [Unreal의 UMG 설명서](https://docs.unrealengine.com/Engine/UMG/index.html)
* [Unreal의 UMG 자습서](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
