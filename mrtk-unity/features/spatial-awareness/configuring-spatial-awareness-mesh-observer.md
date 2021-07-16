---
title: 디바이스에 대한 메시 관찰자 구성
description: MRTK에서 첫 번째 공간 메시 관찰자를 구성하는 방법
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: aba49e88d4fc555a88fe42e4b09858f1d2453ddc
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281937"
---
# <a name="configuring-mesh-observers-for-device"></a>디바이스에 대한 메시 관찰자 구성

이 가이드에서는 Windows Mixed Reality 플랫폼을 지원하는 MRTK에서 첫 번째 공간 메시 관찰자를 구성하는 과정을 안내합니다(즉, HoloLens). Mixed Reality Toolkit 제공되는 기본 구현은 [WindowsMixedRealitySpatialMeshObserver 클래스입니다.](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 그러나 이 문서의 많은 속성은 다른 사용자 지정 관찰자 구현 에 [적용됩니다.](create-data-provider.md)

## <a name="profile-settings"></a>프로필 설정

[공간 인식 시스템에](spatial-awareness-getting-started.md)대한 공간 메시 관찰자 프로필을 구성할 때 다음 두 항목을 먼저 정의해야 합니다.

1. 구체적인 관찰자 형식 구현
1. 이 관찰자를 실행할 수 있는 지원되는 플랫폼 목록

> [!NOTE]
> 모든 관찰자는 [IMixedRealitySpatialAwarenessObserver 인터페이스를](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 확장해야 합니다.

![Mesh Observer 일반 설정 플랫폼 유형](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>일반 설정

![Mesh Observer 일반 설정 Genral 설정](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**시작 동작**

시작 동작은 관찰자가 처음 인스턴스화될 때 실행을 시작할지 여부를 지정합니다. 다음은 두 가지 옵션입니다.

* *자동 시작* - 관찰자가 초기화 후 작업을 시작하는 기본값입니다.
* *수동 시작* - 관찰자가 시작하도록 대기합니다.

수동 *시작* 를 사용하는 경우 [코드를 통해 런타임에](usage-guide.md#starting-and-stopping-mesh-observation)다시 시작하고 일시 중단해야 합니다.

**업데이트 간격**

공간 메시 데이터를 업데이트하기 위한 플랫폼 요청 사이의 시간(초)입니다. 일반적인 값은 0.1 및 5.0초 범위에 속합니다.

**고정 관찰자인가요?**

관찰자가 고정된 상태를 유지할지 아니면 사용자와 함께 이동하고 업데이트할지 여부를 나타냅니다. true이면 *관찰 익스텐트에서* 정의된 볼륨이 있는 *관찰자 도형은* 시작 시 원본에 유지됩니다. false이면 관찰자 공간은 사용자의 머리 뒤에 도형의 원점이 됩니다.

고정 관찰자, *관찰자 도형** 및 *관찰 익스텐트* 속성에 정의된 대로 관찰자 공간 외부의 물리적 영역에 대해 *계산된* 메시 데이터는 없습니다.

**관찰자 도형**

관찰자 모양은 메시 관찰자가 메시를 관찰할 때 사용할 볼륨의 유형을 정의합니다. 지원되는 옵션은 다음과 같습니다.

* *축 맞춤 큐브* - 애플리케이션 시작 시 결정된 대로 세계 좌표계의 축에 맞춰 유지되는 사각형 모양입니다.
* *사용자 맞춤 큐브* - 사용자 로컬 좌표계에 맞게 회전하는 사각형 모양입니다.
* *구* - 세계 우주 원점의 중심이 있는 구형 볼륨입니다. *관찰 익스텐트* 속성의 X 값은 구의 반지름으로 사용됩니다.

**관찰 익스텐트**

관찰 익스텐트 는 메시가 관찰될 관찰 지점으로부터의 거리를 정의합니다.

### <a name="physics-settings"></a>물리학 설정

![Mesh Observer Physics 설정](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**물리학 계층**

Unity 물리학 및 RayCast 시스템과 상호 작용하기 위해 공간 메시 개체를 배치할 물리학 계층입니다.

> [!NOTE]
> Mixed Reality Toolkit 공간 인식 관찰자가 사용할 *계층 31을* 기본적으로 예약합니다.

**정규 다시 계산**

메시 관찰자가 관찰 후 메시의 법선 다시 계산 여부를 지정합니다. 이 설정은 애플리케이션이 메시와 함께 반환하지 않는 플랫폼에서 유효한 일반 데이터가 포함된 메시를 수신하도록 하는 데 사용할 수 있습니다.

### <a name="level-of-detail-settings"></a>세부 정보 설정 수준

![메시 관찰자 세부 정보 수준 설정](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**세부 정보 수준**

공간 메시 데이터의 LOD(세부 정보 수준)를 지정합니다. 현재 정의된 값은 거친 값, 미세 및 사용자 지정입니다.

* *거친* - 애플리케이션 성능에 더 작은 영향을 미치며 탐색/평면 찾기에 매우 적합합니다.

* *중간* - 분산 설정은 환경의 큰 기능, 바닥 및 벽뿐만 아니라 폐색 세부 정보를 지속적으로 검사하는 환경에 유용합니다.

* *미세* - 일반적으로 애플리케이션 성능에 더 높은 영향을 미치며 폐색 메시에 적합한 옵션입니다.

* *사용자 지정* - 애플리케이션에서 *삼각형/입방형 미터* 속성을 지정해야 하며 애플리케이션이 공간 메시 관찰자의 정확도와 성능 영향을 조정할 수 있도록 합니다.

> [!NOTE]
> 모든 *삼각형/입방 미터* 값이 모든 플랫폼에서 보장되는 것은 아닙니다. 사용자 지정 LOD를 사용하는 경우 실험 및 프로파일링이 권장됩니다.

**입방 미터당 삼각형**

**세부 정보 수준** 속성에 사용자 *지정* 설정을 사용할 때 유효하며 공간 메시의 삼각형 밀도를 지정합니다.

### <a name="display-settings"></a>디스플레이 설정

![메시 관찰자 표시 설정](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**표시 옵션**

관찰자가 공간 메시를 표시하는 방법을 지정합니다. 지원되는 값은 다음과 같습니다.

* *없음* - 관찰자가 메시를 렌더링하지 않음
* *표시* - 메시 데이터는 표시되는 *재질을* 사용하여 표시됩니다.
* *폐색* - 메시 데이터는 폐색 재질을 사용하여 장면의 항목을 *폐색합니다.*

![공간 인식 시스템 구현 선택](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

공간 관찰자는 [코드를 통해 런타임에 다시 시작/일시 중단될](usage-guide.md#starting-and-stopping-mesh-observation) 수 있습니다.

> [!WARNING]
> *표시 옵션을* *없음으로* 설정해도 관찰자의 실행이 **중지되지** 않습니다. 모든 관찰자를 중지하려는 경우 애플리케이션은 를 통해 모든 관찰자를 일시 중단해야 합니다. [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**표시되는 재질**

공간 메시를 시각화할 때 사용할 재질을 나타냅니다.

**폐색 재질**

공간 메시가 홀로그램을 가리도록 하는 데 사용할 재질을 나타냅니다.

## <a name="see-also"></a>참조

* [공간 인식 시스템](spatial-awareness-getting-started.md)
* [코드를 통해 공간 인식 시스템 구성](usage-guide.md)
* [IMixedRealitySpatialAwarenessObserver API 설명서](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [IMixedRealitySpatialAwarenessMeshObserver API 설명서](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [BaseSpatialObserver API 설명서](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
