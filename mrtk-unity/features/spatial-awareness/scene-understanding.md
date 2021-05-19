---
title: 장면 이해
description: MRTK의 Scene Understanding에 대해 설명합니다.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Scene Understanding
ms.openlocfilehash: ac90359a71267dc64e659f446f35ec2510c42599
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143880"
---
# <a name="scene-understanding"></a>장면 이해

[Scene Understanding은](/windows/mixed-reality/scene-understanding) 장면 엔터티의 의미 체계 표현과 __HoloLens 2__ 기하학적 형식을 반환합니다(HoloLens 1세대는 지원되지 않음).

이 기술의 몇 가지 예상 사용 사례는 다음과 같습니다.
* 특정 종류의 가장 가까운 표면(예: 벽 및 바닥)에 개체를 배치합니다.
* 플랫폼 스타일 게임을 위한 탐색 메시 생성
* 물리학 엔진에 친숙한 기하 도형을 쿼드로 제공
* 유사한 알고리즘을 작성할 필요가 없도록 하여 개발 가속화

Scene Understanding은 MRTK 2.6부터 __실험적__ 기능으로 사용할 수 있습니다. MRTK는 라는 [공간 관찰자로](spatial-awareness-getting-started.md#register-observers) 통합됩니다. [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) Scene Understanding은 레거시 XR 파이프라인 및 XR SDK 파이프라인에서 모두 작동합니다. 두 경우 모두 가 `WindowsSceneUnderstandingObserver` 사용됩니다.

## <a name="observer-overview"></a>관찰자 개요

요청되면 는 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 애플리케이션이 주변을 이해하는 데 유용한 특성과 함께 [SpatialAwarenessSceneObject를](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) 반환합니다. 관찰 빈도, 반환된 개체 유형(예: 벽, 층) 및 기타 관찰자 동작은 프로필을 통한 관찰자 구성에 따라 달라집니다. 예를 들어 폐색 마스크를 원하는 경우 관찰자는 4분면을 생성하도록 구성해야 합니다. 관찰된 장면을 나중에 로드하여 편집기 재생 모드에서 장면을 다시 만들 수 있는 직렬화된 파일로 저장할 수 있습니다.

## <a name="setup"></a>설치 프로그램

> [!IMPORTANT]
> Scene Understanding은 HoloLens 2 및 Unity 2019.4 이상에서만 지원됩니다.

1. 빌드 설정에서 플랫폼이 UWP로 설정 되었는지 확인 합니다.
1. [혼합 현실 기능 도구](https://aka.ms/MRFeatureTool)를 통해 장면 이해 패키지를 가져옵니다.

## <a name="using-scene-understanding"></a>장면 이해 사용

장면 이해를 시작 하는 가장 빠른 방법은 샘플 장면을 확인 하는 것입니다.

### <a name="scene-understanding-sample-scene"></a>장면 이해 샘플 장면

Unity에서 프로젝트 탐색기를 사용 하 여에서 장면 파일을 열고 `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` play를 누릅니다.

> [!IMPORTANT]
> Mixed Reality 기능 도구를 사용 하거나 UPM를 통해 다른 방법으로 가져오는 경우 종속성 문제로 인해 실험적-SceneUnderstanding 샘플을 가져오기 전에 SpatialAwareness 샘플을 가져오세요. 자세한 내용은 [이 GitHub 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 를 참조 하세요.

장면에서는 다음을 보여 줍니다.

* 관찰자를 구성 하기 위한 응용 프로그램 UI에서 관찰 된 장면 개체의 시각화
* `DemoSceneUnderstandingController`관찰자 설정을 변경 하 고 관련 이벤트를 수신 하는 방법을 보여 주는 예제 스크립트
* 오프 라인 개발을 위해 장치에 장면 데이터 저장
* 편집기에서 개발 워크플로를 지원 하기 위해 이전에 저장 된 장면 데이터 (바이트 파일) 로드

> [!NOTE] 
> 샘플 장면은 레거시 XR 파이프라인을 기반으로 합니다. XR SDK 파이프라인을 사용 하는 경우 프로필을 적절 하 게 수정 해야 합니다. 제공 된 장면 공간 인식 시스템 프로필 ( `DemoSceneUnderstandingSystemProfile` ) 및 장면 이해 관찰자 프로필 ( `DefaultSceneUnderstandingObserverProfile` 및)은 `DemoSceneUnderstandingObserverProfile` 두 파이프라인 모두에서 작동 합니다.

#### <a name="configuring-the-observer-service"></a>관찰자 서비스 구성

' MixedRealityToolkit ' 게임 개체를 선택 하 고 검사기를 확인 합니다.

![계층 구조에서 위치를 이해 하는 장면](../images/spatial-awareness/MRTKHierarchy.png)

![검사기의 MRTK 위치](../images/spatial-awareness/MRTKLocation.png)

이러한 옵션을 사용하면 를 구성할 수 `WindowsSceneUnderstandingObserver` 있습니다.

### <a name="example-script"></a>예제 스크립트

_DemoSceneUnderstandingController.cs_ 예제 스크립트는 Scene Understanding 서비스 작업의 주요 개념을 보여줍니다.

* Scene Understanding 이벤트 구독
* Scene Understanding 이벤트 처리
* `WindowsSceneUnderstandingObserver`런타임에 구성

장면의 패널에서 토글은 이 샘플 스크립트의 공용 함수를 호출하여 장면 이해 관찰자의 동작을 변경합니다.

*Prefabs 인스턴스화* 를 설정하면 부모 개체 아래에 깔끔하게 수집된 모든 [SpatialAwarenessSceneObject에](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)맞게 크기가 인 개체를 만드는 방법을 보여 줄 수 있습니다.

![데모 컨트롤러 옵션](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>빌드된 앱 정보

표준 방식으로 HoloLens를 빌드하고 배포합니다. 실행되면 기능을 사용할 수 있는 단추가 여러 개 표시됩니다.

관찰자에게 쿼리를 만드는 데는 몇 가지 문제가 있습니다. 페치 요청을 잘못 구성하면 이벤트 페이로드에 예상 데이터가 포함되지 않습니다. 예를 들어 쿼드를 요청하지 않으면 폐색 마스크 질감이 없습니다. 마찬가지로 관찰자가 메시를 요청하도록 구성되지 않은 경우 세계 메시는 표시되지 않습니다. `DemoSceneUnderstandingController`스크립트는 이러한 일부 의존성만 처리하지만 전부는 아닙니다.

저장된 장면 파일은 에서 [디바이스 포털을](/windows/mixed-reality/using-the-windows-device-portal) 통해 액세스할 수 `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` 있습니다. 이러한 장면 파일은 검사기에서 찾은 관찰자 프로필에 지정하여 편집기에서 사용할 수 있습니다.

![바이트 파일의 위치 장치 포털](../images/spatial-awareness/BytesInDevicePortal.png)

![관찰자의 직렬화된 장면 바이트](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>참고 항목

* [공간 매핑 개요 WMR](/windows/mixed-reality/scene-understanding)
* [공간 매핑 개요 WMR](/windows/mixed-reality/scene-understanding-sdk)