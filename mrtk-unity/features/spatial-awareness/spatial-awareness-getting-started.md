---
title: 공간 인식 시작
description: MRTK의 공간 인식에 대해 설명 합니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 46bb78bc4e2574fd4da14f19edf52624b7b301c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176712"
---
# <a name="spatial-awareness-getting-started"></a>공간 인식 시작

![공간 인식](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

공간 인식 시스템은 혼합 현실 응용 프로그램에서 실제 환경 인식을 제공 합니다. Microsoft HoloLens에 대해 도입 된 공간 인식에서는 환경의 기 하 도형을 나타내는 메시 컬렉션을 제공 하 여 holograms와 실제 환경 간의 강력한 상호 작용을 수행할 수 있습니다.

> [!NOTE]
> 이번에는 혼합 현실 Toolkit HoloToolkit에서 원래 패키지 된 공간을 인식 하는 알고리즘과 함께 제공 되지 않습니다. 일반적으로 공간을 이해 하려면 공간 메시 데이터를 변환 하 여 평면, 벽, 층, 최대값이 등의 단순화 및/또는 그룹화 된 메시 데이터를 생성 해야 합니다.

## <a name="getting-started"></a>시작

공간 인식에 대 한 지원을 추가 하려면 혼합 현실 Toolkit의 두 가지 주요 구성 요소 (공간 인식 시스템 및 지원 되는 플랫폼 공급자)가 필요 합니다.

1. 공간 인식 시스템 [사용](#enable-the-spatial-awareness-system)
2. 하나 이상의 공간 관찰자를 [등록](#register-observers) 하 고 [구성](configuring-spatial-awareness-mesh-observer.md) 하 여 메시 데이터 제공
3. 공간 인식을 지 원하는 플랫폼에 [빌드 및 배포](#build-and-deploy)

### <a name="enable-the-spatial-awareness-system"></a>공간 인식 시스템 사용

공간 인식 시스템은 MixedRealityToolkit 개체 또는 다른 [서비스 등록자](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 구성 요소에 의해 관리 됩니다. *MixedRealityToolkit* 프로필에서 *공간 인식 시스템* 을 사용 하거나 사용 하지 않도록 설정 하려면 다음 단계를 수행 합니다.

혼합 현실 Toolkit는 미리 구성 된 몇 가지 기본 프로필과 함께 제공 됩니다. 이러한 중 일부에는 기본적으로 공간 인식 시스템이 활성화 되거나 비활성화 됩니다. 특히 사용 하지 않도록 설정 된 경우이 사전 구성의 의도는 메시를 계산 하 고 렌더링 하는 시각적 오버 헤드를 방지 하는 것입니다.

| 프로필 | 기본적으로 시스템 사용 |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (자산/m RTK/SDK/Profiles/HoloLens1) | False |
| `DefaultHoloLens2ConfigurationProfile` (자산/m RTK/SDK/Profiles/HoloLens2) | False |
| `DefaultMixedRealityToolkitConfigurationProfile` (자산/m RTK/SDK/프로필) | True |

1. 장면 계층 구조에서 MixedRealityToolkit 개체를 선택 하 여 검사기 패널에서 엽니다.

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

1. *공간 인식 시스템* 섹션으로 이동 하 여 *공간 인식 시스템 사용* 을 선택 합니다.

    ![공간 인식 사용](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. 원하는 공간 인식 시스템 구현 유형을 선택 합니다. 는 [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) 제공 된 기본값입니다.

    ![공간 인식 시스템 구현 선택](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>관찰자 등록

혼합 현실 Toolkit의 서비스에는 플랫폼 특정 데이터 및 구현 제어와 함께 주 서비스를 보완 하는 [Data Provider 서비스가](../../architecture/systems-extensions-providers.md) 있을 수 있습니다. 이에 대 한 예는 다양 한 플랫폼별 Api에서 컨트롤러 및 기타 관련 입력 정보를 가져오기 위해 [여러 데이터 공급자](../input/input-providers.md) 가 있는 혼합 현실 입력 시스템입니다.

공간 인식 시스템은 데이터 공급자가 시스템에 실제 환경을 위한 메시 데이터를 제공 한다는 점에서 비슷합니다. 공간 인식 프로필에는 하나 이상의 공간 관찰자가 등록 되어 있어야 합니다. 일반적으로 공간 관찰자는 플랫폼 특정 끝점에서 다양 한 유형의 메시 데이터를 제공 하기 위한 공급자 역할을 하는 플랫폼별 구성 요소입니다 (즉, HoloLens).

1. *공간 인식 시스템 프로필* 을 열거나 확장 합니다.

    ![공간 인식 시스템 프로필](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. *"공간 관찰자 추가"* 단추를 클릭 합니다.
1. 원하는 *공간 관찰자 구현 유형을* 선택 합니다.

    ![공간 관찰자 구현을 선택 합니다.](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. 필요 [에 따라 관찰자의 구성 속성을 수정](configuring-spatial-awareness-mesh-observer.md) 합니다.

> [!NOTE]
> `DefaultMixedRealityToolkitConfigurationProfile`(asset/mrtk/SDK/profile)의 사용자에 게는 클래스를 사용 하는 Windows Mixed Reality 플랫폼용으로 미리 구성 된 공간 인식 시스템이 있습니다 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) .

### <a name="build-and-deploy"></a>빌드 및 배포

공간 인식 시스템이 원하는 관찰자로 구성 되 면 프로젝트를 빌드하고 대상 플랫폼에 배포할 수 있습니다.

> [!IMPORTANT]
> Windows Mixed Reality 플랫폼을 대상으로 하는 경우 (예: HoloLens) 장치에서 공간 인식 시스템을 사용 하기 위해 [공간 인식 기능이](/windows/mixed-reality/spatial-mapping-in-unity) 사용 되도록 설정 되어 있는지 확인 하는 것이 중요 합니다.

> [!WARNING]
> Microsoft HoloLens를 비롯 한 일부 플랫폼은 Unity 내에서 원격 실행을 지원 합니다. 이 기능을 사용 하면 빌드 및 배포 단계를 요구 하지 않고 신속 하 게 개발 하 고 테스트할 수 있습니다. 대상 하드웨어 및 플랫폼에서 실행 되는 응용 프로그램의 빌드 및 배포 버전을 사용 하 여 최종 승인 테스트를 수행 해야 합니다.

## <a name="next-steps"></a>다음 단계

위의 절차에 따라 공간 인식 시스템을 사용 하도록 설정 하면 시스템을 더 자세히 구성 하 고 제어할 수 있습니다.

Inspector에서 관찰자를 구성 하는 방법에 대 한 정보:

- [장치 사용에 대 한 관찰자 구성](configuring-spatial-awareness-mesh-observer.md)
- [편집기에서 사용 하기 위한 관찰자 구성](spatial-object-mesh-observer.md)

코드를 통해 관찰자를 제어 및 확장 하는 방법에 대 한 정보:

- [코드를 통해 관찰자 구성](usage-guide.md)
- [사용자 지정 관찰자 만들기](create-data-provider.md)

## <a name="see-also"></a>참조

- [공간 인식 API 설명서](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [공간 매핑 개요 WMR](/windows/mixed-reality/spatial-mapping)
- [Unity WMR의 공간 매핑](/windows/mixed-reality/spatial-mapping-in-unity)
