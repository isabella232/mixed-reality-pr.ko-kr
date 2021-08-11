---
title: 사용자 인터페이스 만들기
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 정적 및 동적 사용자 인터페이스를 만드는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, 프리팹, 홀로그램, 도구 설명
ms.localizationpriority: high
ms.openlocfilehash: 605379be0e2f3238ddb5de5c47b6df005c4bf2eb82a2e04156f1317e0e7659fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227852"
---
# <a name="6-creating-user-interfaces"></a>6. 사용자 인터페이스 만들기

이 자습서에서는 Unity의 TextMeshPro 구성 요소와 함께 MRTK의 단추와 메뉴 프리팹을 사용하여 간단한 사용자 인터페이스를 만드는 방법에 대해 알아봅니다. 또한 이벤트를 트리거하도록 단추를 구성하고, 사용자에게 추가 정보를 제공하기 위해 동적 도구 설명 UI 요소를 추가하는 방법에 대해서도 알아봅니다.

## <a name="objectives"></a>목표

* 컬렉션에서 단추를 구성하는 방법 알아보기
* MRTK의 메뉴 프리팹을 사용하는 방법 알아보기
* UI 요소 및 단추를 사용하여 홀로그램과 상호 작용하는 방법 알아보기
* 텍스트 요소를 추가하는 방법 알아보기
* 개체에 대한 도구 설명을 동적으로 생성하는 방법 알아보기

## <a name="creating-a-static-panel-of-buttons"></a>정적 단추 패널 만들기

[계층 구조] 창에서 마우스 오른쪽 단추로 **RoverExplorer** 개체를 클릭하고, **빈 항목 만들기** 를 선택하여 빈 개체를 RoverExplorer의 자식으로 추가하고, 개체 이름을 **Buttons** 로 지정하고, **변환** 구성 요소를 다음과 같이 구성합니다.

* **위치**: X = -0.6, Y = 0.036, Z = -0.5
* **회전**: X = 90, Y = 0, Z = 0
* **배율**: X = 1, Y = 1, Z = 1

![새로 만든 Buttons 개체가 선택되고 배치된 Unity](images/mr-learning-base/base-06-section1-step1-1.png)

[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** 폴더로 차례로 이동하고, **PressableRoundButton** 프리팹을 클릭하여 **Buttons** 개체로 끈 다음, 마우스 오른쪽 단추로 PressableRoundButton을 클릭하고, **중복** 을 선택하여 복사본을 만듭니다. 총 세 개의 PressableRoundButton 개체 복사본을 만들 때까지 반복합니다.

![새로 추가한 PressableRoundButton 프리팹이 있는 Unity](images/mr-learning-base/base-06-section1-step1-2.png)

[계층 구조] 창에서 **Buttons** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **GridObjectCollection** 구성 요소를 추가하고 다음과 같이 구성합니다.

* **정렬 유형**: 자식 순서
* **레이아웃**: 수평
* **셀 너비**: 0.2
* **앵커**: 왼쪽 가운데

그런 다음, **컬렉션 업데이트** 단추를 클릭하여 Buttons 개체의 자식 개체에 대한 위치를 업데이트합니다.

![GridObjectCollection 구성 요소가 추가, 구성 및 적용된 Unity Buttons 개체](images/mr-learning-base/base-06-section1-step1-3.png)

[계층 구조] 창에서 단추 이름을 **Hints**, **Explode** 및 **Reset** 으로 지정합니다.

각 단추에 대해 **SeeItSayItLabel** > **TextMeshPro** 자식 개체를 차례로 선택한 다음, [검사기] 창에서 각 **TextMeshPro - 텍스트** 구성 요소 텍스트를 단추 이름과 일치하도록 변경합니다.

![단추 텍스트 레이블이 구성된 Unity](images/mr-learning-base/base-06-section1-step1-4.png)

완료되면 Buttons 개체의 자식 개체를 접습니다.

[계층 구조] 창에서 **Hints** 단추 개체를 선택한 다음, [검사기] 창에서 **Interactable.OnClick ()** 이벤트를 다음과 같이 구성합니다.

* **RoverAssembly** 개체를 **없음(개체)** 필드에 할당합니다.
* **함수 없음** 드롭다운에서 **PlacementHintsController** > **TogglePlacementHints ()** 를 차례로 선택하여 이 함수를 이벤트가 트리거될 때 실행할 작업으로 설정합니다.

![Hints 단추 개체 OnClick 이벤트가 구성된 Unity](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> Interactable 구성 요소는 모든 객체가 입력에 쉽게 상호 작용하고 응답할 수 있도록 하는 일체형 컨테이너입니다. Interactable은 터치, 손 광선, 말하기 등을 포함한 모든 유형의 입력에 대한 캐치 올(catch-all) 역할을 하며 이러한 상호 작용을 이벤트 및 시각적 테마 응답으로 전달합니다. 다양한 입력 유형에 맞게 구성하고 시각적 테마를 사용자 지정하는 방법에 대한 자세한 내용은 [MRTK 설명서 포털](/windows/mixed-reality/mrtk-unity/)의 [Interactable](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) 가이드를 참조할 수 있습니다.

[계층 구조] 창에서 **Explode** 단추 개체를 선택한 다음, [검사기] 창에서 **Interactable.OnClick ()** 이벤트를 다음과 같이 구성합니다.

* **RoverAssembly** 개체를 **없음(개체)** 필드에 할당합니다.
* **함수 없음** 드롭다운에서 **ExplodedViewController** > **ToggleExplodedView ()** 를 차례로 선택하여 이 함수를 이벤트가 트리거될 때 실행할 작업으로 설정합니다.

![Explode 단추 개체 OnClick 이벤트가 구성된 Unity](images/mr-learning-base/base-06-section1-step1-6.png)

[재생] 단추를 눌러 게임 모드를 시작한 다음, 스페이스 바 단추를 길게 눌러 손을 활성화하고, 마우스를 사용하여 **Hints** 단추를 눌러 배치 힌트 개체의 표시 유형을 설정/해제합니다.

![Hints 단추가 눌러져 있는 Unity 재생 모드 분할 보기](images/mr-learning-base/base-06-section1-step1-7.png)

그리고 **Explode** 단추를 눌러 분해된 보기를 설정/해제합니다.

![Explode 단추가 눌러져 있는 Unity 재생 모드 분할 보기](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a>사용자를 따르는 동적 메뉴 만들기

Project 창에서 **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus** 폴더로 차례로 이동하고, **NearMenu4x1** 프리팹을 클릭하여 Hierarchy 창으로 끈 다음, 해당 변환 **위치** 를 X = 0, Y = -0.4, Z = 0으로 설정하고 다음과 같이 구성합니다.

* **SolverHandler** 구성 요소의 **추적 대상 형식** 이 **Head** 로 설정되어 있는지 확인합니다.
* **RadialView** 해결기 구성 요소 옆에 있는 확인란을 선택하여 기본적으로 사용하도록 설정합니다.

![새로 추가한 Near Menu 프리팹이 선택된 Unity](images/mr-learning-base/base-06-section2-step1-1.png)

[계층 구조] 창에서 개체 이름을 **Menu** 로 바꾼 다음, 해당 **ButtonCollection** 자식 개체를 펼쳐서 4개의 단추를 표시합니다.

![Menu 개체가 선택되고 ButtonCollection 개체가 펼쳐진 Unity](images/mr-learning-base/base-06-section2-step1-2.png)

ButtonCollection에서 첫 번째 단추의 이름을 Indicator로 바꾼 다음, 검사기 창에서 단추 구성 도우미(스크립트) 구성 요소를 다음과 같이 구성합니다.

* **기본 레이블 텍스트** 를 단추 이름과 일치하도록 변경합니다.
* 갈매기형 Indicator 개체를 None (Object)(없음(개체)) 필드에 할당합니다.
* **함수 없음** 드롭다운에서 **GameObject** > **SetActive(부울)** 를 차례로 선택하여 이 함수를 이벤트가 트리거될 때 실행할 작업으로 설정합니다.
* 인수 확인란이 **선택되어** 있는지 확인합니다.
* **아이콘** 을 '검색' 아이콘으로 변경합니다.

![Indicator 단추 개체 Button Config Helper가 구성된 Unity](images/mr-learning-base/base-06-section2-step1-3.png)

갈매기형 Indicator 개체를 사용하지 않으려면 Hierarchy(계층 구조) 창에서 갈매기형 Indicator 개체를 선택한 다음, Inspector(검사기) 창에서 다음을 수행합니다.

* 이름 옆에 있는 확인란을 선택 취소하여 기본적으로 비활성화합니다.
* **구성 요소 추가** 단추를 사용하여 **Directional Indicator Controller(스크립트)** 구성 요소를 추가합니다.

![Indicator 개체가 선택되어 사용하지 않도록 설정되고 DirectionalIndicatorController 구성 요소가 추가된 Unity](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> 이제 앱이 시작되면 갈매기형 Indicator(검사기)가 기본적으로 사용하지 않도록 설정되며, Indicator(검사기) 단추를 눌러 사용하도록 설정할 수 있습니다.

> [!NOTE]
> Directional Indicator Controller(스크립트)는 MRTK의 일부는 아니지만 자습서 자산에 포함되어 있습니다.

두 번째 단추의 이름을 **TapToPlace** 로 바꾼 다음, [검사기] 창에서 **단추 구성 도우미(스크립트)** 구성 요소를 다음과 같이 구성합니다.

* **기본 레이블 텍스트** 를 단추 이름과 일치하도록 변경합니다.
* RoverExplorer > **RoverAssembly** 개체를 **없음(개체)** 필드에 할당합니다.
* **함수 없음** 드롭다운에서 **TapToPlace** > **부울 사용** 을 차례로 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트합니다.
* 인수 확인란이 **선택되어** 있는지 확인합니다.
* **아이콘** 을 '광선이 있는 손' 아이콘으로 변경합니다.

![TapToPlace 단추 개체 Button Config Helper가 구성된 Unity](images/mr-learning-base/base-06-section2-step1-5.png)

[계층 구조] 창에서 **RoverAssembly** 개체를 선택한 다음, [검사기] 창에서 다음과 같이 **탭하여 위치 지정(스크립트)** 구성 요소를 구성합니다.

* 이름 옆에 있는 확인란을 선택 취소하여 기본적으로 비활성화합니다.
* **On Placing Stopped ()** 이벤트 섹션에서 **+** 아이콘을 클릭하여 새 이벤트를 추가합니다.
* RoverExplorer > **RoverAssembly** 개체를 **없음(개체)** 필드에 할당합니다.
* **함수 없음** 드롭다운에서 **TapToPlace** > **부울 사용** 을 차례로 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트합니다.
* 인수 확인란이 **선택 취소되어** 있는지 확인합니다.

![TapToPlace 구성 요소가 다시 구성된 Unity](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> 이제 앱이 시작되면 Tap to Place(탭하여 위치 지정) 기능이 기본적으로 사용하지 않도록 설정되며, Tap to Place 단추를 눌러 사용하도록 설정할 수 있습니다. 또한 탭하여 위치 지정이 완료되면 자체적으로 사용하지 않도록 설정됩니다.

## <a name="adding-text-to-the-scene"></a>장면에 텍스트 추가

[계층 구조] 창에서 마우스 오른쪽 단추로 **Table** 개체를 클릭하고, **3D 개체** > **텍스트 - TextMeshPro** 를 차례로 선택하여 텍스트 개체를 Table 개체의 자식으로 추가한 다음, [검사기] 창에서 **사각형 변환** 구성 요소를 다음과 같이 구성합니다.

* **세로 위치** 를 1로 변경합니다.
* **너비** 를 1로 변경합니다.
* **높이** 를 1로 변경합니다.
* **회전 X** 를 90으로 변경합니다.

![새로 만든 TextMeshPro 개체가 선택된 Unity](images/mr-learning-base/base-06-section3-step1-1.png)

그런 다음, **TextMeshPro - 텍스트** 구성 요소를 다음과 같이 구성합니다.

* **텍스트** 를 Rover Explorer로 변경합니다.
* **글꼴 스타일** 을 [굵게]로 변경합니다.
* **글꼴 크기** 를 1로 변경합니다.
* 추가 설정 > **여백** 을 0.03으로 변경합니다.

![TextMeshPro 구성 요소가 구성된 Unity](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a>도구 설명 추가

Project 창에서 **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** 폴더로 이동하여 도구 설명 프리팹을 찾습니다.

![ToolTips 폴더가 선택된 Unity 프로젝트 창](images/mr-learning-base/base-06-section4-step1-1.png)

[계층 구조] 창에서 RoverExplorer > **RoverParts** 개체를 차례로 펼치고, 해당 자식 로버 부품 개체를 모두 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **ToolTipSpawner** 구성 요소를 추가하고 다음과 같이 구성합니다.

* 사용자가 도구 설명이 표시되는 부품을 살펴볼 수 있도록 하려면 **포커스 사용** 확인란이 선택되어 있는지 확인합니다.
* 프로젝트 창에서 **Simple Line ToolTip(한 줄 도구 설명)** 프리팹을 **Prefab(프리팹)** 필드에 할당합니다.
* 도구 설명 재정의 설정 > **설정 모드** 를 **재정의** 로 변경합니다.
* 도구 설명 재정의 설정 > **수동 피벗 로컬 위치 Y** 를 **1.5** 로 변경합니다.

![모든 로버 부품 개체가 선택되고 ToolTipSpawner 구성 요소가 추가되고 구성된 Unity](images/mr-learning-base/base-06-section4-step1-2.png)

계층 구조 창에서 Camera_Part, RoverParts > **Camera_Part** 를 차례로 선택하고, **ToolTipSpawner** 구성 요소를 다음과 같이 구성합니다.

* 부품 이름(예: **Camera**)을 반영하도록 **도구 설명 텍스트** 를 변경합니다.

![Camera ToolTipText가 구성된 Unity](images/mr-learning-base/base-06-section4-step1-3.png)

각 로버 부품 개체에 대해 이 단계를 **반복** 하여 **ToolTipSpawner** 구성 요소를 다음과 같이 구성합니다.

* **Generator_Part** 에 대한 **도구 설명 텍스트** 를 **발전기** 로 변경합니다.
* **Lights_Part** 에 대한 **도구 설명 텍스트** 를 **조명** 으로 변경합니다.
* **UHFAntenna_Part** 에 대한 **도구 설명 텍스트** 를 **UHF 안테나** 필드로 변경합니다.
* **Spectrometer_Part** 에 대한 **도구 설명 텍스트** 를 **분광계** 로 변경합니다.

[재생] 단추를 눌러 게임 모드를 시작한 다음, 시선이 부품 중 하나에 적중하여 해당 부품에 대한 도구 설명이 표시될 때까지 마우스 오른쪽 단추를 누른 채 마우스를 움직입니다.

![응시로 트리거된 도구 설명이 있는 Unity 재생 모드 분할 보기](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 Unity의 TextMeshPro 구성 요소와 함께 MRTK에서 제공하는 단추 및 메뉴 프리팹을 사용하여 간단한 사용자 인터페이스를 만드는 방법 및 눌렀을 때 이벤트를 트리거하도록 단추를 구성하는 방법을 알아보았습니다. 또한 동적 도구 설명 UI 요소를 추가하여 사용자에게 추가 정보를 제공하는 방법도 알아보았습니다.

> [!div class="nextstepaction"]
> [다음 자습서: 7. 3D 개체와 상호 작용](mr-learning-base-07.md)
