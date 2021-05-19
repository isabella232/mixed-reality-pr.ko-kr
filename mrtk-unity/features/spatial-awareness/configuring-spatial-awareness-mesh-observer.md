---
title: 공간 인식 메시 관찰자 구성
description: MRTK에서 기본 공간 메시 관찰자를 구성 하는 방법
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 0d71a32d76624698e78b8123f427ddefc08f3d0b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144960"
---
# <a name="configuring-mesh-observers-for-device"></a>장치에 대 한 메시 관찰자 구성

이 가이드에서는 Windows 혼합 현실 플랫폼 (예:)을 지 원하는 MRTK에서 기본 공간 메시 관찰자를 구성 하는 과정을 안내 합니다. HoloLens). Mixed Reality Toolkit에서 제공 되는 기본 구현은 [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 클래스입니다. 그러나이 문서의 많은 속성은 다른 [사용자 지정 관찰자 구현](create-data-provider.md)에 적용 됩니다.

## <a name="profile-settings"></a>프로필 설정

[공간 인식 시스템](spatial-awareness-getting-started.md)에 대해 공간 메시 관찰자 프로필을 구성할 때 먼저 다음 두 항목을 정의 해야 합니다.

1. 구체적인 관찰자 형식 구현
1. 이 관찰자를 실행 하는 데 지원 되는 플랫폼 목록

> [!NOTE]
> 모든 관찰자가 [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 인터페이스를 확장 해야 합니다.

![메시 관찰자 일반 설정 플랫폼 형식](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>일반 설정

![메시 관찰자 일반 설정 Genral 설정](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**시작 동작**

시작 동작은 관찰자가 처음 인스턴스화될 때 실행을 시작할지 여부를 지정 합니다. 다음은 두 가지 옵션입니다.

* *자동 시작* -초기화 후 관찰자가 작업을 시작 하는 기본값입니다.
* *수동 시작* -관찰자가 시작 될 때까지 대기 합니다.

*수동 시작* 을 사용 하는 경우 [코드를 통해 런타임 시 다시 시작 하 고 일시 중단](usage-guide.md#starting-and-stopping-mesh-observation)해야 합니다.

**업데이트 간격**

플랫폼에서 공간 메시 데이터를 업데이트 하는 요청 사이의 시간 (초)입니다. 일반적인 값의 범위는 0.1에서 5.0 초 사이입니다.

**고정 관찰자인가요?**

관찰자가 고정된 상태를 유지할지 아니면 사용자와 함께 이동하고 업데이트할지 여부를 나타냅니다. true이면 *관찰 익스텐트에서* 정의된 볼륨이 있는 *관찰자 도형은* 시작 시 원본에 유지됩니다. false이면 관찰자 공간은 사용자의 머리 뒤에 도형의 원점이 됩니다.

고정 관찰자, *관찰자 도형** 및 *관찰 익스텐트* 속성에 정의된 대로 관찰자 공간 외부의 물리적 영역에 대해 *계산된* 메시 데이터는 없습니다.

**관찰자 셰이프**

관찰자 모양은 메시 관찰자가 메시를 관찰할 때 사용할 볼륨의 유형을 정의합니다. 지원되는 옵션은 다음과 같습니다.

* *축 맞춤 큐브* - 애플리케이션 시작 시 결정된 대로 세계 좌표계의 축에 맞춰 유지되는 사각형 모양입니다.
* *사용자 맞춤 큐브* - 사용자 로컬 좌표계에 맞게 회전하는 사각형 모양입니다.
* *구* - 세계 공간 원점의 중심이 있는 구형 볼륨입니다. *관찰 익스텐트* 속성의 X 값은 구의 반지름으로 사용됩니다.

**관찰 익스텐트**

관찰 익스텐트 는 메시가 관찰될 관찰 지점으로부터의 거리를 정의합니다.

### <a name="physics-settings"></a>물리학 설정

![Mesh Observer Physics 설정](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**물리학 계층**

Unity 물리학 및 RayCast 시스템과 상호 작용하기 위해 공간 메시 개체를 배치할 물리학 계층입니다.

> [!NOTE]
> Mixed Reality 도구 키트는 공간 인식 관찰자가 사용할 *계층 31을* 기본적으로 예약합니다.

**정규 다시 계산**

메시 관찰자가 관찰 후 망상의 법선을 다시 계산할지 여부를 지정 합니다. 이 설정은 응용 프로그램이 메시를 사용 하 여 반환 하지 않는 플랫폼에서 유효한 법선 데이터를 포함 하는 메시를 받도록 하는 데 사용할 수 있습니다.

### <a name="level-of-detail-settings"></a>세부 정보 설정 수준

![메시 관찰자 수준 세부 설정](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**세부 정보 수준**

공간 메시 데이터의 세부 수준 (LOD)을 지정 합니다. 현재 정의 된 값은 거칠게, 세밀 하 고 사용자 지정입니다.

* *거칠게* 는 응용 프로그램 성능에 미치는 영향을 최소화 하 고 탐색/평면 검색에 적합 합니다.

* *중간 규모* 의 설정은 폐색 세부 정보 뿐만 아니라 규모가 뛰어난 기능, 층 및 벽 모두를 지속적으로 검색 하는 환경에 유용 합니다.

* *자세히* -일반적으로 응용 프로그램 성능에 더 큰 영향을 폐색 메시를 위한 유용한 옵션입니다.

* *사용자 지정* -응용 프로그램에서 *삼각형/입방 측정기* 속성을 지정 하 고, 응용 프로그램에서 공간 메시 관찰자의 정확도와 성능 영향을 조정할 수 있도록 합니다.

> [!NOTE]
> 모든 플랫폼에서 모든 *삼각형/입방 미터* 값을 허용 하는 것은 아닙니다. 사용자 지정 LOD를 사용 하는 경우 실험 및 프로 파일링은 매우 권장 됩니다.

**입방 미터 당 삼각형**

**Detail 속성 수준** 에 대 한 *사용자 지정* 설정을 사용 하는 경우 유효 하 고 공간 메시의 삼각형 밀도를 지정 합니다.

### <a name="display-settings"></a>디스플레이 설정

![메시 관찰자 표시 설정](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**표시 옵션**

관찰자가 공간 메시를 표시 하는 방법을 지정 합니다. 지원되는 값은 다음과 같습니다.

* *없음* -관찰자가 메시를 렌더링 하지 않습니다.
* *가시-* 표시 되는 *재질* 을 사용 하 여 메시 데이터를 볼 수 있습니다.
* *폐색* - 메시 데이터는 폐색 재질을 사용하여 장면의 항목을 *폐색합니다.*

![공간 인식 시스템 구현 선택](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

공간 관찰자는 [코드를 통해 런타임에 다시 시작/일시 중단될](usage-guide.md#starting-and-stopping-mesh-observation) 수 있습니다.

> [!WARNING]
> *표시 옵션을* *없음으로* 설정해도 관찰자의 실행이 **중지되지** 않습니다. 모든 관찰자를 중지하려는 경우 애플리케이션은 를 통해 모든 관찰자를 일시 중단해야 합니다. [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**표시되는 재질**

공간 메시를 시각화할 때 사용할 재질을 나타냅니다.

**폐색 재질**

공간 메시가 홀로그램을 가리는 데 사용할 재질을 나타냅니다.

## <a name="see-also"></a>참고 항목

* [공간 인식 시스템](spatial-awareness-getting-started.md)
* [코드를 통해 공간 인식 시스템 구성](usage-guide.md)
* [IMixedRealitySpatialAwarenessObserver API 설명서](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [IMixedRealitySpatialAwarenessMeshObserver API 설명서](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [BaseSpatialObserver API 설명서](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
