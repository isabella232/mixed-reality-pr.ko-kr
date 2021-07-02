---
title: 탄력적 시스템
description: MRTK의 탄력적 시뮬레이션과 관련된 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, ElasticsSystem,
ms.openlocfilehash: 44110cac9ac5aadb7b5e680f18a5e93f43efce12
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177799"
---
# <a name="elastic-system"></a>탄력적 시스템

![탄력 시스템](../images/elastics/Elastics_Main1.gif)

MRTK는 4차원 4차원 쿼터니언 Spring, 3차원 볼륨 Spring 및 간단한 선형 Spring 시스템에 대한 바인딩을 제공하는 다양하고 유연하고 다양한 서브클래스를 포함하는 탄력적 시뮬레이션 시스템과 함께 제공됩니다.

현재 [탄력적 관리자를](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) 지원하는 다음 MRTK 구성 요소는 탄력적 기능을 활용할 수 있습니다.

- [경계 컨트롤](../ux-building-blocks/bounds-control.md)
- [개체 조작자](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a>Elastics 관리자

![탄력적 시스템 2](../images/elastics/Elastics_Main.gif)

탄력적 관리자는 전달된 변환을 처리하고 탄력적 시스템에 공급합니다.

사용자 지정 구성 요소에 대한 탄력적 사용을 다음 두 단계로 수행할 수 있습니다.

1. 조작 시작 시 Initialize 메서드를 호출하여 현재 호스트 변환으로 시스템을 업데이트합니다.
1. 업데이트된 대상 변환에서 탄력적 계산을 수행해야 할 때마다 ApplyHostTransform을 쿼리합니다.

탄력적은 조작이 종료되면(Elastics Manager 업데이트 루프를 통해) 시뮬레이션을 계속합니다. 동작을 차단하기 위해 Elastics 자동 업데이트 [EnableElasticsUpdate를](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) false로 설정할 수 있습니다.

기본적으로 elastics Manager 구성 요소는 게임 개체에 추가될 때 변환 형식에 대해 활성화된 탄력적 을 갖지 않습니다.
선택한 `Manipulation types using elastic feedback` 형식에 대한 탄력적 구성 및 익스텐트 만들기를 위해 특정 변환 형식에 대해 필드를 사용하도록 설정해야 합니다.

### <a name="elastics-configurations"></a>탄력적 구성

범위 [제어 구성과](../ux-building-blocks/bounds-control.md#configuration-objects)마찬가지로 탄력적 관리자는 스크립팅 가능한 개체로 저장하고 서로 다른 인스턴스 또는 프리팹 간에 공유할 수 있는 구성 개체 집합과 함께 제공됩니다. 구성은 개별 스크립팅 가능한 자산 파일 또는 프리팹 내에 중첩된 스크립팅 가능한 자산으로 공유 및 연결될 수 있습니다. 추가 구성은 외부 또는 중첩된 스크립트 가능 자산에 연결하지 않고 인스턴스에서 직접 정의할 수도 있습니다.

Elastics 관리자 검사기는 속성 검사기에서 메시지를 표시하여 구성이 현재 인스턴스의 일부로 공유되는지 또는 인라인되는지 여부를 나타냅니다. 또한 공유 인스턴스는 Elastics Manager 속성 창 자체에서 직접 편집할 수 없지만 대신 연결되는 자산은 공유 구성에서 실수로 변경되지 않도록 직접 수정해야 합니다.

Elastics 관리자는 다음과 같은 변환 형식에 대한 구성 개체 옵션을 제공하며, 각 옵션은 [탄력적 구성 개체](#elastic-configuration-object)로 표시됩니다.

- 탄력적 변환
- 회전 탄력적
- 탄력적 크기 조정

#### <a name="elastic-configuration-object"></a>탄력적 구성 개체

탄력적 구성은 비동기 오실레이터 차등 시스템의 속성을 정의합니다.
다음 속성을 조정할 수 있지만 MRTK의 기본값 집합이 이미 제공됩니다.

- **Mass**: 시뮬레이션된 oscillator 요소의 대용량입니다.
- **HandK**: 손 Spring 상수입니다.
- **EndK**: 끝 캡 spring 상수입니다.
- **SnapK**: snap point spring 상수입니다.
- **끌기:** 끌기/비저장 요소로, 속도에 비례합니다.

### <a name="elastics-extents"></a>탄력적 익스텐트

탄력적 익스텐트 설정은 조작 유형에 따라 달라집니다. 변환 및 배율 은 [볼륨 탄력적 익스텐트로](#volume-elastic-extent) 표시되고 회전은 [쿼터니언 탄력적 익스텐트](#quaternion-elastic-extent)로 표시됩니다.

#### <a name="volume-elastic-extent"></a>볼륨 탄력적 범위

볼륨 익스텐트 는 3차원 공간을 정의합니다. 이 공간은 비워진 음산 오실레이터를 자유롭게 이동할 수 있습니다.

![탄력적 볼륨 스트레치 범위](../images/elastics/Elastics_Volume_Bounds.gif)

- **StretchBounds**: 탄력적 공간의 하한을 나타냅니다.
- **UseBounds:** 시스템에서 확장 범위를 적용해야 하는지 여부입니다. true이면 대상 위치의 현재 반복이 늘이기 범위를 벗어나면 끝 강제가 적용됩니다.
- **SnapPoints:** 시스템이 맞춰질 공간 내부를 가리킵니다.
- **RepeatSnapPoints**: 맞춤 지점을 무한대로 반복합니다. 기존 맞춤 지점은 실제 맞춤 지점이 모든 맞춤 지점의 가장 가까운 정수 배수에 매핑되는 모듈로 역할을 합니다.
- **SnapRadius:** 맞춤 지점이 강제로 봄을 적용하기 시작하는 거리입니다.

![탄력적 볼륨 맞춤 표](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a>4원수 탄력적 익스텐트

쿼터니언 익스텐트 는 4차원 회전 공간을 정의합니다. 이 공간은 습한 경기성 오실레이터를 자유롭게 회전할 수 있습니다.

![탄력적 회전 예제](../images/elastics/Elastics_Rotation.gif)

- **SnapPoints:** 시스템이 맞춰질 내러 각도입니다.
- **RepeatSnapPoints**: 맞춤 지점을 반복합니다. 기존 맞춤 지점은 실제 맞춤 지점이 모든 맞춤 지점의 가장 가까운 정수 배수에 매핑되는 모듈로 역할을 합니다.
- **SnapRadius:** 맞춤 지점이 유러 도의 탄력을 강제하기 시작하는 원호 각도입니다.

## <a name="elastics-example-scene"></a>탄력적 예제 장면

장면에서 탄력적 구성의 예를 찾을 수 `ElasticSystemExample` 있습니다.

![Elastics 예제 장면](../images/elastics/Elastics_Example_Scene.png)
