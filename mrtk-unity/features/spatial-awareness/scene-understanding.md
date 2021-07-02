---
title: 관찰자의 관찰자 이해
description: MRTK의 장면 이해에 대해 설명 합니다.
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 장면 이해
ms.openlocfilehash: d5430e7885055a550347c4ccebc1452f68125922
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176237"
---
# <a name="scene-understanding-observer"></a>관찰자의 관찰자 이해

[장면 이해](/windows/mixed-reality/scene-understanding) 는 장면 엔터티에 대 한 의미 체계와 __HoloLens 2__ 에서의 기하학적 형태를 반환 합니다 (HoloLens 1 Gen은 지원 되지 않음).

이 기술의 몇 가지 예상 사용 사례는 다음과 같습니다.
* 특정 종류의 가장 가까운 표면 (예: 벽 및 층)에 개체를 삽입 합니다.
* 구성 탐색-플랫폼 스타일 게임의 메시
* Quads로 물리학 엔진 친화적인 기 하 도형을 제공 합니다.
* 비슷한 알고리즘을 작성할 필요가 없도록 하 여 개발 가속화

장면 이해는 MRTK 2.6에서 __실험적__ 기능으로 도입 되었습니다. 이라는 [공간 관찰자](spatial-awareness-getting-started.md#register-observers) 로 MRTK에 통합 됩니다 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) . 장면 이해는 레거시 XR 파이프라인과 XR SDK 파이프라인 (OpenXR (mrtk 2.7에서 시작) 및 Windows XR Plugin) 모두에서 작동 합니다. 두 경우 모두 `WindowsSceneUnderstandingObserver` 이 사용 됩니다.

> [!NOTE] 
> 원격에서 장면 이해를 사용 하는 것은 지원 되지 않습니다.

## <a name="observer-overview"></a>관찰자 개요

메시지가 표시 되 면는 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 응용 프로그램에서 주변을 이해 하는 데 유용한 특성과 함께 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) 를 반환 합니다. 관찰 빈도, 반환 된 개체 형식 (예: 벽, 층) 및 기타 관찰자 동작은 프로필을 통한 관찰자의 구성에 따라 달라 집니다. 예를 들어 폐색 mask가 필요한 경우 관찰자는 quads를 생성 하도록 구성 되어야 합니다. 관찰 된 장면을 나중에 로드 하 여 편집기 재생 모드에서 장면을 다시 만들 수 있도록 serialize 된 파일로 저장할 수 있습니다.

## <a name="setup"></a>설치 프로그램

> [!IMPORTANT]
> 장면 이해는 HoloLens 2 및 Unity 2019.4 이상 에서만 지원 됩니다.

1. 빌드 설정에서 플랫폼이 UWP로 설정 되었는지 확인 합니다.
1. [혼합 현실 기능 도구](https://aka.ms/MRFeatureTool)를 통해 장면 이해 패키지를 가져옵니다.

## <a name="using-scene-understanding"></a>장면 이해 사용

장면 이해를 시작 하는 가장 빠른 방법은 샘플 장면을 확인 하는 것입니다.

### <a name="scene-understanding-sample-scene"></a>장면 이해 샘플 장면

Unity에서 Project 탐색기를 사용 하 여에서 장면 파일을 열고 `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` play를 누릅니다.

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> MRTK 2.6.0에만 적용 됩니다. 혼합 현실 기능 도구를 사용 하거나, 다른 방법으로는 UPM를 통해 가져오는 경우 종속성 문제로 인해 실험적-SceneUnderstanding 샘플을 가져오기 전에 SpatialAwareness 샘플을 가져오세요. 자세한 내용은 [이 GitHub 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 를 참조 하세요.

::: moniker-end
장면에서는 다음을 보여 줍니다.

* 관찰자를 구성 하기 위한 응용 프로그램 UI에서 관찰 된 장면 개체의 시각화
* `DemoSceneUnderstandingController`관찰자 설정을 변경 하 고 관련 이벤트를 수신 하는 방법을 보여 주는 예제 스크립트
* 오프 라인 개발을 위해 장치에 장면 데이터 저장
* 편집기에서 개발 워크플로를 지원 하기 위해 이전에 저장 된 장면 데이터 (바이트 파일) 로드

> [!IMPORTANT]
> 기본적으로 `ShouldLoadFromFile` 관찰자의 속성은 false로 설정 됩니다. 직렬화 된 샘플 대화방의 시각화를 보려면 아래의 [관찰자 서비스 구성](#configuring-the-observer-service) 섹션을 참조 하 고 편집기에서 속성을 true로 설정 하세요.
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> 샘플 장면은 레거시 XR 파이프라인을 기반으로 합니다. XR SDK 파이프라인을 사용 하는 경우 프로필을 적절 하 게 수정 해야 합니다. 제공 된 장면 공간 인식 시스템 프로필 ( `DemoSceneUnderstandingSystemProfile` ) 및 장면 이해 관찰자 프로필 ( `DefaultSceneUnderstandingObserverProfile` 및)은 `DemoSceneUnderstandingObserverProfile` 두 파이프라인 모두에서 작동 합니다.
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> 샘플 장면에서는 `There is no active AsyncCoroutineRunner when an action is posted.` 초기화/스레드 실행 순서로 인해 특정 상황에서 경고를 기록 합니다. `AsyncCoroutineRunner`구성 요소가 "Demo Controller" GameObject에 연결 되어 있는지 확인 하 고 구성 요소/GameObject가 장면 (기본 경우)에서 사용 하도록 설정 된 상태를 유지 하도록 할 수 있는 경우 경고를 안전 하 게 무시할 수 있습니다. **그러나 장면 이해를 사용 하 여 새 장면을 만들 때 루트에 빈 GameObject를 만들어 `AsyncCoroutineRunner` 스크립트를 연결 해야 합니다. 그렇지 않으면 장면 이해가 제대로 작동 하지 않을 수 있습니다.**
::: moniker-end

#### <a name="configuring-the-observer-service"></a>관찰자 서비스 구성

' MixedRealityToolkit ' 게임 개체를 선택 하 고 검사기를 확인 합니다.

![계층 구조에서 위치를 이해 하는 장면](../images/spatial-awareness/MRTKHierarchy.png)

![검사기의 MRTK 위치](../images/spatial-awareness/MRTKLocation.png)

이러한 옵션은를 구성 하는 데 사용할 수 `WindowsSceneUnderstandingObserver` 있습니다.

### <a name="example-script"></a>예제 스크립트

예제 스크립트 _DemoSceneUnderstandingController_ 는 장면 이해 서비스를 사용 하는 주요 개념을 보여 줍니다.

* 장면 이해 이벤트 구독
* 장면 이해 이벤트 처리
* `WindowsSceneUnderstandingObserver`런타임에 구성

장면의 패널에 대 한 토글은이 샘플 스크립트의 public 함수를 호출 하 여 관찰자를 이해 하는 장면의 동작을 변경 합니다.

*인스턴스화 Prefabs* 을 켜면 부모 개체 아래에서 깔끔하게 수집 된 모든 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)에 맞게 크기를 조정 하는 개체를 만드는 것을 보여 줍니다.

![데모 컨트롤러 옵션](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>빌드된 앱 메모

표준 방식으로 HoloLens를 빌드하고 배포 합니다. 실행 한 후에는 기능을 사용 하 여 많은 단추가 표시 되어야 합니다.

관찰자에 게 쿼리를 만드는 일부 pit가 있습니다. 인출 요청이 잘못 구성 되 면 이벤트 페이로드가 필요한 데이터를 포함 하지 않습니다. 예를 들어 quads를 요청 하지 않는 경우 폐색 mask 질감이 표시 되지 않습니다. 예를 들어 관찰자가 메시를 요청 하도록 구성 되지 않은 경우에는 세계 메쉬가 나타나지 않습니다. `DemoSceneUnderstandingController`스크립트는 이러한 종속성 중 일부를 처리 하지만 모두는 처리 하지 않습니다.

저장 된 장면 파일은에서 [장치 포털](/windows/mixed-reality/using-the-windows-device-portal) 을 통해 액세스할 수 있습니다 `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` . 이러한 장면 파일은 검사기에서 찾은 관찰자 프로필에 지정 하 여 편집기에서 사용할 수 있습니다.

![바이트 파일의 장치 포털 위치](../images/spatial-awareness/BytesInDevicePortal.png)

![관찰자의 serialize 된 장면 바이트](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>참고 항목

* [장면 이해 개요](/windows/mixed-reality/scene-understanding)
* [장면 이해 SDK 개요](/windows/mixed-reality/scene-understanding-sdk)
