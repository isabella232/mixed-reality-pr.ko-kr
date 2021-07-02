---
title: 경계 시스템 개요
description: MRTK의 경계 시스템에 대한 방문 페이지
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 경계 시스템,
ms.openlocfilehash: fd70479e5183e9a7557de5c5a532cc87161be017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177079"
---
# <a name="boundary-system-overview"></a>경계 시스템 개요

경계 시스템은 혼합 현실 애플리케이션에서 가상 현실 경계 구성 요소를 시각화하기 위한 지원을 제공합니다. 경계는 VR 헤드셋을 걸 때 사용자가 안전하게 이동할 수 있는 영역을 정의합니다. 경계는 사용자가 VR 헤드셋을 걸 때 보이지 않는 장애물을 방지하는 데 도움이 되는 혼합 현실 환경의 중요한 구성 요소입니다.

많은 Virtual Reality 플랫폼은 사용자 또는 컨트롤러가 경계에 가까워지면 가상 세계에 겹쳐진 흰색 윤곽선과 같은 자동 디스플레이를 제공합니다. Mixed Reality Toolkit 경계 시스템은 이 기능을 확장하여 추적된 영역의 개요, 평면 및 사용자에게 추가 정보를 제공하는 데 사용할 수 있는 기타 기능을 표시할 수 있도록 합니다.

## <a name="getting-started"></a>시작

경계에 대한 지원을 추가하려면 Mixed Reality Toolkit 두 가지 주요 구성 요소인 경계 시스템과 경계로 구성된 가상 현실 플랫폼이 필요합니다.

1. 경계 시스템 [사용](#enable-boundary-system)
2. 경계 시각화 [구성](#configure-boundary-visualization)
3. 구성된 경계를 사용하여 VR 플랫폼 [빌드 및 배포](#build-and-deploy)

## <a name="enable-boundary-system"></a>경계 시스템 사용

경계 시스템은 MixedRealityToolkit 개체(또는 다른 [서비스 등록 기관](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 구성 요소)에 의해 관리됩니다.

다음 단계에서는 MixedRealityToolkit 개체의 사용을 가정합니다. 다른 서비스 등록 기관에 필요한 단계는 다를 수 있습니다.

1. 장면 계층 구조에서 MixedRealityToolkit 개체를 선택합니다.

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

1. 검사기 패널을 경계 시스템 섹션으로 이동하고 사용을 선택합니다.

    ![경계 시스템 사용](../images/boundary/MRTKConfig_Boundary.png)

1. 경계 시스템 구현을 선택합니다. MRTK에서 제공하는 기본 클래스 구현은 입니다. [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

    ![경계 시스템 구현 선택](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> 모든 경계 시스템 구현은 다음을 확장해야 합니다. [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)

## <a name="configure-boundary-visualization"></a>경계 시각화 구성

[경계 시스템은 구성 프로필을 사용하여](configuring-boundary-visualization.md) 표시할 경계 구성 요소를 지정하고 모양을 구성합니다.

![경계 시각화 옵션](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> 기본 `DefaultMixedRealityBoundaryVisualizationProfile` 프로필(자산/MRTK/SDK/프로필)의 사용자는 평면, 재생 영역 및 추적된 영역을 표시하도록 미리 구성된 경계 시스템을 갖게 됩니다.

## <a name="build-and-deploy"></a>빌드 및 배포

경계 시스템이 원하는 시각화 옵션으로 구성되면 프로젝트를 대상 플랫폼에 배포하여 빌드할 수 있습니다.

> [!NOTE]
> Unity 재생 모드를 사용하면 구성된 경계를 편집기 내 시각화할 수 있습니다. 이 기능을 사용하면 빌드 및 배포 단계 없이도 신속한 개발 및 테스트를 수행할 수 있습니다. 대상 하드웨어 및 플랫폼에서 실행되는 애플리케이션의 빌드 및 배포 버전을 사용하여 최종 승인 테스트를 수행해야 합니다.

## <a name="accessing-boundary-system-via-code"></a>코드를 통해 경계 시스템에 액세스

사용하도록 설정되고 구성된 경우 CoreServices 정적 도우미 클래스를 통해 경계 시스템에 액세스할 수 있습니다. 그런 다음 참조를 사용하여 경계 매개 변수를 동적으로 변경하고 시스템에서 관리하는 관련 GameObjects에 액세스할 수 있습니다.

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a>참조

- [경계 API 설명서](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [경계 시각화 구성](configuring-boundary-visualization.md)
