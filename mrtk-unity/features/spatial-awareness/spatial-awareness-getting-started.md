---
title: 공간 인식 시작
description: MRTK의 공간 인식에 대해 설명합니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: bbe5b923ea7da965424e7fac98adca180c6f91d0c9b4c4ca7a0477e301c362f9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204331"
---
# <a name="spatial-awareness-getting-started"></a>공간 인식 시작

![공간 인식](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

공간 인식 시스템은 혼합 현실 애플리케이션에서 실제 환경 인식을 제공합니다. Microsoft HoloLens 도입된 공간 인식은 환경의 기하 도형을 나타내는 메시 컬렉션을 제공했으며, 이는 홀로그램과 실제 세계 간의 매력적인 상호 작용을 허용합니다.

> [!NOTE]
> 현재 Mixed Reality Toolkit 원래 HoloToolkit에 패키지된 Spatial Understanding 알고리즘과 함께 제공하지 않습니다. Spatial Understanding은 일반적으로 공간 메시 데이터를 변환하여 평면, 벽, 바닥, 최대값 등과 같은 간소화된 및/또는 그룹화된 Mesh 데이터를 만드는 것을 포함합니다.

## <a name="getting-started"></a>시작

공간 인식에 대한 지원을 추가하려면 Mixed Reality Toolkit 두 가지 주요 구성 요소인 공간 인식 시스템과 지원되는 플랫폼 공급자가 필요합니다.

1. 공간 인식 시스템 [사용](#enable-the-spatial-awareness-system)
2. 메시 데이터를 제공하도록 하나 이상의 공간 관찰자 [등록](#register-observers) 및 [구성](configuring-spatial-awareness-mesh-observer.md)
3. 공간 인식을 지원하는 플랫폼 [빌드 및 배포](#build-and-deploy)

### <a name="enable-the-spatial-awareness-system"></a>공간 인식 시스템 사용

공간 인식 시스템은 MixedRealityToolkit 개체(또는 다른 [서비스 등록자](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 구성 요소)에 의해 관리됩니다. *MixedRealityToolkit* 프로필에서 *공간 인식 시스템을* 사용하거나 사용하지 않도록 설정하려면 다음 단계를 수행합니다.

Mixed Reality Toolkit 미리 구성된 몇 가지 기본 프로필과 함께 제공합니다. 이러한 시스템 중 일부는 기본적으로 공간 인식 시스템을 사용하거나 사용하지 않도록 설정되어 있습니다. 특히 사용하지 않도록 설정되는 경우 이 사전 구성의 목적은 메시를 계산하고 렌더링하는 시각적 오버헤드를 방지하는 것입니다.

| 프로필 | 기본적으로 시스템 사용 |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1) | False |
| `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2) | False |
| `DefaultMixedRealityToolkitConfigurationProfile` (자산/MRTK/SDK/프로필) | True |

1. 장면 계층 구조에서 MixedRealityToolkit 개체를 선택하여 검사기 패널에서 엽니다.

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

1. *공간 인식 시스템* 섹션으로 이동하여 *공간 인식 시스템 사용을* 선택합니다.

    ![공간 인식 사용](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. 원하는 공간 인식 시스템 구현 형식을 선택합니다. [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem)는 제공된 기본값입니다.

    ![공간 인식 시스템 구현 선택](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>관찰자 등록

Mixed Reality Toolkit 서비스에는 플랫폼별 데이터 및 구현 컨트롤을 통해 주 서비스를 보완하는 [Data Provider 서비스가](../../architecture/systems-extensions-providers.md) 있을 수 있습니다. 이 예제는 다양한 플랫폼별 API에서 컨트롤러 및 기타 관련 입력 정보를 얻을 수 있는 [여러 데이터 공급자가](../input/input-providers.md) 있는 Mixed Reality 입력 시스템입니다.

공간 인식 시스템은 데이터 공급자가 실제 세계에 대한 메시 데이터를 시스템에 제공한다는 점에서 비슷합니다. 공간 인식 프로필에는 하나 이상의 공간 관찰자가 등록되어 있어야 합니다. 공간 관찰자는 일반적으로 플랫폼별 엔드포인트에서 다양한 유형의 메시 데이터를 표면화하기 위한 공급자 역할을 하는 플랫폼별 구성 요소입니다(즉, HoloLens).

1. 공간 인식 *시스템 프로필* 열기 또는 확장

    ![공간 인식 시스템 프로필](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. *"공간 관찰자 추가"* 단추를 클릭합니다.
1. 원하는 공간 *관찰자 구현 형식* 선택

    ![공간 관찰자 구현 선택](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. 필요에 따라 [관찰자의 구성 속성 수정](configuring-spatial-awareness-mesh-observer.md)

> [!NOTE]
> `DefaultMixedRealityToolkitConfigurationProfile`(Assets/MRTK/SDK/Profiles)의 사용자는 클래스를 사용하는 Windows Mixed Reality 플랫폼에 대해 미리 구성된 공간 인식 시스템을 갖게 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 됩니다.

### <a name="build-and-deploy"></a>빌드 및 배포

공간 인식 시스템이 원하는 관찰자로 구성되면 프로젝트를 빌드하고 대상 플랫폼에 배포할 수 있습니다.

> [!IMPORTANT]
> Windows Mixed Reality 플랫폼을 대상으로 하는 경우(예: HoloLens) 디바이스에서 공간 인식 시스템을 사용하려면 [공간 인식 기능을](/windows/mixed-reality/spatial-mapping-in-unity) 사용하도록 설정하는 것이 중요합니다.

> [!WARNING]
> Microsoft HoloLens 비롯한 일부 플랫폼은 Unity 내에서 원격 실행을 지원합니다. 이 기능을 사용하면 빌드 및 배포 단계 없이도 신속한 개발 및 테스트를 수행할 수 있습니다. 대상 하드웨어 및 플랫폼에서 실행되는 애플리케이션의 빌드 및 배포 버전을 사용하여 최종 승인 테스트를 수행해야 합니다.

## <a name="next-steps"></a>다음 단계

공간 인식 시스템을 사용하도록 설정하기 위해 위의 절차에 따라 시스템을 더 자세히 구성하고 제어할 수 있습니다.

검사기에서 관찰자를 구성하는 방법에 대한 정보:

- [디바이스 사용 시 에 대한 관찰자 구성](configuring-spatial-awareness-mesh-observer.md)
- [편집기 내 사용을 위한 관찰자 구성](spatial-object-mesh-observer.md)

코드를 통해 관찰자를 제어하고 확장하기 위한 정보:

- [코드를 통해 관찰자 구성](usage-guide.md)
- [사용자 지정 관찰자 만들기](create-data-provider.md)

## <a name="see-also"></a>추가 정보

- [공간 인식 API 설명서](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [공간 매핑 개요 WMR](/windows/mixed-reality/spatial-mapping)
- [Unity WMR의 공간 매핑](/windows/mixed-reality/spatial-mapping-in-unity)
