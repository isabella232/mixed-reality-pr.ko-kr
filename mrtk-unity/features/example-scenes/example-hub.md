---
title: MRTK 예제 허브
description: MRTK의 예제 장면 개요
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: b7a55e46b2c283b5a75395b9e99874af6020a171
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282004"
---
# <a name="mrtk-examples-hub"></a>MRTK 예제 허브

![MRTK 예제 허브](../images/examples-hub/MRTK_ExamplesHub.png)

MRTK 예제 허브는 여러 장면을 쉽게 경험할 수 있는 Unity 장면입니다. MRTK의 장면 시스템을 사용하여 장면을 & 로드합니다.

**MRTKExamplesHub.unity는** 및 를 비롯한 공유 구성 요소가 있는 컨테이너 ``MixedRealityToolkit`` ``MixedRealityPlayspace`` 장면입니다. **MRTKExamplesHubMainMenu.unity** 장면에는 큐브 단추가 있습니다.

## <a name="prerequisite"></a>필수 조건

MRTK 예제 허브는 [장면 전환 서비스](../extensions/scene-transition-service.md) 및 관련 스크립트를 사용합니다. Unity 패키지를 통해 MRTK를 사용하는 경우 **Microsoft.MixedReality.Toolkit 가져오세요. 릴리스 패키지 의 일부인 Unity.Extensions.x.x.x.unitypackage** [](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) 리포지토리 복제본을 통해 MRTK를 사용하는 경우 프로젝트에 **MRTK/Extensions 폴더가** 이미 있어야 합니다.

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>MRTKExamplesHub 장면 및 장면 시스템

**MrTKExamplesHub.unity를** 엽니다. `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit, MixedRealityPlayspace 및 LoadHubOnStartup이 있는 빈 장면입니다. 이 장면 MRTK의 장면 시스템을 사용 하 여 구성 합니다. `MixedRealitySceneSystem`MixedRealityToolkit 아래를 클릭합니다. 검사기 패널에 장면 시스템의 정보가 표시됩니다.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

검사기 아래쪽에는 장면 시스템 프로필에 정의된 장면 목록이 표시됩니다. 장면 이름을 클릭하여 로드/언로드할 수 있습니다.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">목록에서 장면 이름을 클릭하여 _MRTKExamplesHub_ 장면을 로드하는 예제입니다.
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">_HandInteractionExamples_ 장면을 로드하는 예제입니다.
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
여러 장면을 로드하는 예제입니다.

## <a name="running-the-scene"></a>장면 실행

이 장면은 Unity의 게임 모드와 디바이스 모두에서 작동합니다. Unity 편집기에서 **MRTKExamplesHub** 장면을 실행하고 MRTK의 입력 시뮬레이션을 사용하여 장면 콘텐츠와 상호 작용합니다. 빌드 및 배포하려면 장면 시스템의 목록에 포함된 다른 장면으로 **MRTKExamplesHub** 장면을 빌드하기만 하면됩니다. 또한 검사기를 사용하면 빌드 설정 장면을 쉽게 추가할 수 있습니다. Building 설정 **MRTKExamplesHub** 장면이 인덱스 0의 목록 맨 위에 있는지 확인합니다.

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a>MRTKExamplesHub가 장면을 로드하는 방법

**MRTKExamplesHub** 장면에서 프리팹을 찾을 수 ``ExamplesHubButton`` 있습니다.
를 포함하는 **FrontPlate** 개체가 프리팹에 ``Interactable`` 있습니다.
Interactable의 및 이벤트를 사용하여 ``OnClick()`` ``OnTouch()`` **LoadContentScene** 스크립트의 **LoadContent()** 함수를 트리거합니다.
**LoadContentScene** 스크립트의 검사기에서 로드할 장면 이름을 정의할 수 있습니다.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

스크립트는 장면 시스템의 LoadContent() 함수를 사용하여 장면을 로드합니다.
자세한 내용은 [장면 시스템](../scene-system/scene-system-getting-started.md) 페이지를 참조하세요.

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a>주 메뉴 장면으로 돌아가기

주 메뉴 장면(MRTKExamplesHubMainMenu 장면)으로 돌아가려면 동일한 장면 시스템 메서드를 사용할 수 `LoadContent()` 있습니다. **ToggleFeaturesPanelExamplesHub.prefab은** **LoadContentScene** 스크립트를 포함하는 '홈' 단추를 제공합니다. 이 프리팹을 사용하거나 각 장면에서 사용자 지정 홈 단추를 제공하여 사용자가 기본 장면으로 돌아갈 수 있도록 합니다. **MRTKExamplesHub가** 공유 컨테이너 장면이므로 항상 표시되도록 **ToggleFeaturesPanelExamplesHub.prefab을** **MRTKExamplesHub** 장면에 배치할 수 있습니다. 각 예제 장면에서 **ToggleFeaturesPanel.prefab을** 숨기/비활성화해야 합니다.

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>단추 추가

**CubeCollection** 개체에서 _ExampleHubButton_ 프리팹을 복제(또는 추가)하고 에서 **컬렉션 업데이트를** `GridObjectCollection` 클릭합니다.
그러면 새 총 단추 수에 따라 실린더 레이아웃이 업데이트됩니다.
자세한 내용은 [개체 컬렉션](../ux-building-blocks/object-collection.md) 페이지를 참조하세요.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

단추를 추가한 후 **LoadContentScene** 스크립트(위에서 설명)에서 장면 이름을 업데이트합니다.
장면 시스템의 프로필에 장면을 더 추가합니다.
