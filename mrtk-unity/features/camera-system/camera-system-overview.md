---
title: 카메라 시스템 개요
description: MRTK의 카메라 시스템에 대 한 방문 페이지
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 카메라,
ms.openlocfilehash: 1dc5328f2a6390246918063b6564837f150d28d8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144476"
---
# <a name="camera-system"></a>카메라 시스템

카메라 시스템은 Microsoft Mixed Reality 도구 키트를 사용 하 여 혼합 현실 응용 프로그램에서 사용할 수 있도록 응용 프로그램의 카메라를 구성 하 고 최적화 합니다. 카메라 시스템을 사용 하 여 각 유형의 표시를 구분 하는 코드를 작성할 필요 없이 불투명 (예: 가상 현실) 및 투명 (예: Microsoft HoloLens) 장치를 모두 지원 하도록 응용 프로그램을 작성할 수 있습니다.

## <a name="enabling-the-camera-system"></a>카메라 시스템 사용

카메라 시스템은 MixedRealityToolkit 개체 (또는 다른 서비스 등록자 구성 요소)를 통해 관리 됩니다.

다음 단계에서는 MixedRealityToolkit 개체를 사용 하는 것으로 가정 합니다. 다른 서비스 등록 기관 필요한 단계는 다를 수 있습니다.

1. 장면 계층 구조에서 MixedRealityToolkit 개체를 선택 합니다.

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

2. 검사기 패널에서 카메라 시스템 섹션으로 이동 하 여 **카메라 시스템 사용** 이 선택 되어 있는지 확인 합니다.

    ![카메라 시스템 사용](../images/camera-system/EnableCameraSystem.png)

3. 카메라 시스템 구현을 선택 합니다. MRTK에서 제공 하는 기본 클래스 구현은입니다 `MixedRealityCameraSystem` .

    ![카메라 시스템 구현 선택](../images/camera-system/SelectCameraSystemType.png)

4. 원하는 구성 프로필을 선택 합니다.

    ![카메라 시스템 프로필 선택](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a>카메라 시스템 구성

### <a name="settings-providers"></a>설정 공급자

![카메라 설정 공급자](../images/camera-system/CameraSettingsProviders.png)

카메라 설정 공급자는 카메라의 플랫폼별 구성을 사용하도록 설정합니다. 이러한 설정에는 사용자 지정 구성 단계 및/또는 구성 요소가 포함될 수 있습니다.

카메라 설정 공급자 추가 단추를 클릭하여 **공급자를 추가할** 수 있습니다. 공급자 이름 오른쪽에 있는 단추를 클릭하여 제거할 수 **-** 있습니다.

> [!Note]
> 모든 플랫폼에 카메라 설정 공급자가 필요한 것은 아닙니다. 애플리케이션이 실행되는 플랫폼과 호환되는 공급자가 없는 경우 Microsoft Mixed Reality 도구 키트가 기본 기본값을 적용합니다.

### <a name="display-settings"></a>디스플레이 설정

![카메라 표시 설정](../images/camera-system/CameraDisplaySettings.png)

표시 설정은 불투명(예: 가상 현실) 및 투명(예: Microsoft HoloLens) 디스플레이 모두에 대해 지정됩니다. 카메라는 런타임에 이러한 설정을 사용하여 구성됩니다.

**Near Clip**

근거리 클립 평면은 가상 개체가 카메라에 있을 수 있고 여전히 렌더링될 수 있는 가장 가까운 미터(미터)입니다. 사용자의 편의를 위해 이 값을 0보다 큰 값으로 만드는 것이 좋습니다. 이전 이미지에는 다양한 디바이스에서 편안하게 발견된 값이 포함되어 있습니다.

**원거리 클립**

원거리 클립 평면은 가상 개체가 카메라에 있을 수 있고 여전히 렌더링될 수 있는 가장 먼 길이(미터)입니다. 투명 디바이스의 경우 이 값은 실제 공간을 과도하게 초과하지 않고 애플리케이션의 몰입형 품질을 끊지 않도록 상대적으로 가깝게 하는 것이 좋습니다.

**플래그 지우기**

플래그 지우기 값은 표시가 그려질 때 지워지는 방법을 나타냅니다. 가상 현실 환경의 경우 이 값은 대부분 Skybox로 설정됩니다. 투명 디스플레이의 경우 색으로 설정 하는 것이 좋습니다.

**배경색**

Clear 플래그를 Skybox로 설정 하지 않으면 배경색 속성이 표시 됩니다.

**품질 설정**

품질 설정 값은 Unity가 장면을 렌더링할 때 사용 해야 하는 그래픽 품질을 나타냅니다. 품질 수준은 프로젝트 수준 설정이 며 한 카메라에 국한 되지 않습니다. 자세한 내용은 Unity 설명서의 [품질](https://docs.unity3d.com/Manual/class-QualitySettings.html) 문서를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [카메라 시스템 API 설명서](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [카메라 설정 공급자 만들기](create-settings-provider.md)
