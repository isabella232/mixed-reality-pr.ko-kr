---
title: 공간 인식
description: MRTK의 공간 인식에 대해 설명 합니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 776033dbb4736ccaa44cdb683c4fce284758a51c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144463"
---
# <a name="spatial-awareness"></a>공간 인식

![공간 인식](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

공간 인식 시스템은 혼합 현실 응용 프로그램에서 실제 환경 인식을 제공 합니다. Microsoft HoloLens에 도입 된 공간 인식에서는 holograms와 실제 환경 간의 강력한 상호 작용에 사용할 수 있는 환경의 기 하 도형을 나타내는 메시의 컬렉션을 제공 합니다.

> [!NOTE]
> 이번에는 혼합 현실 도구 키트가 HoloToolkit에서 원래 패키지 된 공간을 인식 하지 못합니다. 일반적으로 공간을 이해 하려면 공간 메시 데이터를 변환 하 여 평면, 벽, 층, 최대값이 등의 단순화 및/또는 그룹화 된 메시 데이터를 생성 해야 합니다.

## <a name="getting-started"></a>시작

공간 인식 지원을 추가 하려면 혼합 현실 도구 키트의 두 가지 주요 구성 요소인 공간 인식 시스템과 지원 되는 플랫폼 공급자가 필요 합니다.

1. 공간 인식 시스템 [사용](#enable-the-spatial-awareness-system)
2. 하나 이상의 공간 관찰자를 [등록](#register-observers) 하 고 [구성](configuring-spatial-awareness-mesh-observer.md) 하 여 메시 데이터 제공
3. 공간 인식을 지 원하는 플랫폼에 [빌드 및 배포](#build-and-deploy)

### <a name="enable-the-spatial-awareness-system"></a>공간 인식 시스템 사용

공간 인식 시스템은 MixedRealityToolkit 개체 또는 다른 [서비스 등록자](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 구성 요소에 의해 관리 됩니다. *MixedRealityToolkit* 프로필에서 *공간 인식 시스템* 을 사용 하거나 사용 하지 않도록 설정 하려면 다음 단계를 수행 합니다.

혼합 현실 도구 키트는 미리 구성 된 몇 가지 기본 프로필을 제공 합니다. 이러한 중 일부에는 기본적으로 공간 인식 시스템이 활성화 되거나 비활성화 됩니다. 특히 사용 하지 않도록 설정 된 경우이 사전 구성의 의도는 메시를 계산 하 고 렌더링 하는 시각적 오버 헤드를 방지 하는 것입니다.

| 프로필 | 기본적으로 시스템 사용 |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (자산/m RTK/SDK/Profiles/HoloLens1) | 거짓 |
| `DefaultHoloLens2ConfigurationProfile` (자산/m RTK/SDK/Profiles/HoloLens2) | 거짓 |
| `DefaultMixedRealityToolkitConfigurationProfile` (자산/m RTK/SDK/프로필) | True |

1. 장면 계층 구조에서 MixedRealityToolkit 개체를 선택 하 여 검사기 패널에서 엽니다.

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

1. *공간 인식 시스템* 섹션으로 이동하여 *공간 인식 시스템 사용을* 선택합니다.

    ![공간 인식 사용](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. 원하는 공간 인식 시스템 구현 형식을 선택합니다. [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem)는 제공된 기본값입니다.

    ![공간 인식 시스템 구현 선택](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>관찰자 등록

Mixed Reality 도구 키트의 [서비스에는](../../architecture/systems-extensions-providers.md) 플랫폼별 데이터 및 구현 컨트롤을 사용하여 기본 서비스를 보완하는 Data Provider 서비스가 있을 수 있습니다. 이 예제는 다양한 플랫폼별 API에서 컨트롤러 및 기타 관련 입력 정보를 얻을 수 있는 [여러 데이터 공급자가](../input/input-providers.md) 있는 Mixed Reality 입력 시스템입니다.

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

## <a name="see-also"></a>참고 항목

- [공간 인식 API 설명서](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [공간 매핑 개요 WMR](/windows/mixed-reality/spatial-mapping)
- [Unity WMR의 공간 매핑](/windows/mixed-reality/spatial-mapping-in-unity)