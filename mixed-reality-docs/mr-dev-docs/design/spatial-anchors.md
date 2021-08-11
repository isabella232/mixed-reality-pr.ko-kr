---
title: Spatial Anchors
description: 공간 앵커를 사용 하 여 혼합 현실 응용 프로그램에서 안정적인 holograms를 렌더링 하기 위한 모범 사례에 대해 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 좌표계, 공간 좌표 시스템, 세계 규모, 세계, 규모, 위치, 방향, 앵커, 공간 고정, 전 세계 잠금, 세계 잠금, 지 속성, 공유, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens
ms.openlocfilehash: dc9b57d51f4202499d82abb8d210261d2ee36dc60bb90ed039a7554f82af79a0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193517"
---
# <a name="spatial-anchors"></a>Spatial Anchors

공간 앵커는 시간이 지남에 따라 시스템이 추적 하는 세계에서 중요 한 지점을 나타냅니다. 각 앵커에는 고정 된 holograms 정확 하 게 유지 되도록 하기 위해 다른 앵커 또는 참조 프레임을 기준으로 조정 가능한 [좌표 시스템이](coordinate-systems.md)있습니다.  앵커의 좌표계에서 홀로그램을 렌더링 하면 지정 된 시간에 해당 홀로그램에 대해 가장 정확 하 게 배치할 수 있습니다. 이는 시스템에서 실제 환경에 따라 지속적으로 다시 이동 하는 동안 홀로그램의 위치에 대 한 시간에 따른 작은 조정 비용을 발생 시킵니다.

또한 응용 프로그램 세션 및 장치 간에 공간 앵커를 유지 하 고 공유할 수 있습니다.
* 로컬 공간 앵커를 디스크에 저장 하 고 나중에 다시 로드 하면 응용 프로그램에서 단일 HoloLens에 대해 여러 응용 프로그램 세션 간에 실제 세계의 동일한 위치를 계산할 수 있습니다.
* <a href="/azure/spatial-anchors/overview" target="_blank">Azure 공간</a> 앵커를 사용 하 여 클라우드 앵커를 만들면 응용 프로그램은 여러 HoloLens, iOS 및 Android 장치에서 공간 앵커를 공유할 수 있습니다. 각 장치가 동일한 공간 앵커를 사용 하 여 홀로그램을 렌더링 하도록 하면 홀로그램은 실제 세계의 동일한 위치에 표시 됩니다. 이렇게 실제 세계 공유 환경을 제공합니다.
* HoloLens, iOS 및 Android 장치에서 비동기 홀로그램 지 속성에 대해 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용할 수도 있습니다. 내구성이 있는 클라우드 공간 앵커를 공유 하 여 여러 장치는 동시에 함께 제공 되지 않더라도 시간이 지남에 따라 동일한 지속형 홀로그램을 관찰할 수 있습니다.

5 미터 지름 내에 유지 되는 테더 링 된 desktop 헤드셋에 대 한 대규모 또는 공간 규모의 환경을 위해 일반적으로 모든 콘텐츠를 렌더링할 단일 좌표계를 제공 하는 공간 앵커 대신 [스테이지 프레임](coordinate-systems.md#stage-frame-of-reference) 을 사용할 수 있습니다. 그러나 응용 프로그램에서 사용자가 HoloLens에서 5 미터를 초과 하 여 건물 전체에 걸쳐 작동 하는 경우 콘텐츠를 안정적으로 유지 하려면 공간 앵커가 필요 합니다.

공간 앵커는 세계에서 고정 상태를 유지해야 하는 홀로그램에 적합합니다. 배치된 앵커는 이동할 수 없습니다. 동적 holograms 사용자와 함께 태그를 추가 하는 데 더 적합 한 앵커에 대 한 대안이 있습니다. 고정 된 참조 프레임 (Unity의 세계 좌표에 대 한 기초) 또는 참조의 연결 된 프레임을 사용 하 여 동적 holograms를 배치 하는 것이 가장 좋습니다.

## <a name="best-practices"></a>모범 사례

이 공간 앵커 지침은 실제 세계를 정확하게 따르는 고정 홀로그램을 렌더링하는 데 도움이 됩니다.

### <a name="create-spatial-anchors-where-users-place-them"></a>사용자가 배치하는 공간 앵커 만들기

일반적으로 사용자는 공간 앵커를 명시적으로 배치 합니다.

예를 들어 HoloLens에서 응용 프로그램은 사용자의 [응시](gaze-and-commit.md) 광선과 [공간 매핑](spatial-mapping.md) 메시를 교차 하 여 사용자가 홀로그램 위치를 결정할 수 있도록 합니다. 사용자가 해당 홀로그램 위치를 클릭 하 여 교차 지점에 공간 앵커를 만든 다음 해당 앵커 좌표계의 원점에 홀로그램을 놓습니다.

로컬 공간 앵커는 쉽고 빠르게 만들 수 있습니다. 여러 앵커가 기본 센서 데이터를 공유할 수 있는 경우 시스템은 내부 데이터를 결합 합니다. Holograms의 고정 그룹과 같이 아래에 설명 된 경우를 제외 하 고 사용자가 명시적으로 배치 하는 각 홀로그램에 대해 새 로컬 공간 앵커를 만드는 것이 좋습니다.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>항상 앵커의 3미터 범위 내에서 고정된 홀로그램 렌더링

공간 앵커는 앵커의 원점 근처에 좌표계를 안정화합니다. 원본에서 3 미터를 초과 하 여 holograms을 렌더링 하는 경우 holograms은 레버 arm 효과 때문에 해당 원본 으로부터의 거리에 비례하여 눈에 띄는 위치 오류가 발생할 수 있습니다. 사용자가 사용자와 멀리 떨어져 있기 때문에 사용자가 앵커 근처를 사용 하는 경우에도 마찬가지입니다. 즉, 먼 홀로그램의 각도 오류는 작습니다. 그러나 사용자가 해당 하는 홀로그램으로 이동할 경우 보기에서 크기가 크므로 멀리 떨어진 앵커 원본의 레버-arm 효과를 명확 하 게 만들 수 있습니다.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>고정 클러스터를 형성하는 홀로그램 그룹화

응용 프로그램에서 서로 고정 관계를 유지 해야 하는 경우 여러 holograms 동일한 공간 앵커를 공유할 수 있습니다.

예를 들어 방에 있는 holographic 태양계에 애니메이션을 적용 하는 경우 모든 태양계 개체를 중앙의 단일 앵커에 연결 하는 것이 좋습니다. 이렇게 하면 서로를 기반으로 원활 하 게 이동 합니다. 이 경우 구성 요소 부분이 앵커를 기준으로 동적으로 이동 하는 경우에도 해당 구성 요소가 고정 된 전체 시스템입니다.

홀로그램 안정성을 유지 하는 데 중요 한 점은 위의 3 미터 규칙을 따르는 것입니다.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>로컬 공간 앵커가 아닌 고정 참조 프레임을 사용하여 매우 동적인 홀로그램 렌더링

대화방을 중심으로 하는 문자 또는 사용자 근처의 벽을 따라 이어지는 부동 UI와 같은 매우 동적인 홀로그램을 사용 하는 경우 로컬 공간 앵커를 건너뛰고 [고정 참조 프레임](coordinate-systems.md#stationary-frame-of-reference)에서 제공 하는 좌표계에서 직접 이러한 holograms를 렌더링 하는 것이 가장 좋습니다. Unity에서는 WorldAnchor 없이 세계 좌표에 직접 holograms를 배치 하 여이를 달성할 수 있습니다. 고정 참조 프레임의 홀로그램스는 사용자가 홀로그램에서 멀리 떨어져 있을 때 드리프트가 발생할 수 있습니다. 그러나이는 동적 holograms 눈에 띄는 것은 아닙니다. 즉, 홀로그램은 계속 해 서 이동 하는 것입니다. 또는 해당 동작을 계속 해 서 드리프트를 최소화 하는 사용자에 게 가깝게 유지 합니다.

동적 홀로그램의 흥미로운 사례 하나는 고정된 좌표계 사이를 애니메이션으로 이동하는 개체입니다. 예를 들어 각각 다른 성에 cannonball 실행 하는 단일 성이 있는 고유한 공간 앵커를 사용 하 여 두 개의 성 10 미터를 가질 수 있습니다. Cannonball이 발생 하면 고정 참조 프레임의 적절 한 위치에이를 렌더링 하 여 첫 번째 성의 고정 좌표계에서 대포와 일치 시킬 수 있습니다. 그런 다음, 탄환이 공중으로 10미터 날아갈 때 고정 참조 프레임의 궤도를 따를 수 있습니다. Cannonball 다른 성에 도달할 때이를 두 번째 성의 고정 좌표계로 이동 하 여 해당 성의 고정 본문을 사용 하는 물리학 계산을 수행할 수 있습니다.

장치에서 매우 동적인 홀로그램을 공유 하는 경우 참조의 고정 프레임을 장치 간에 공유할 수 없기 때문에 부모 역할을 하는 클라우드 공간 앵커를 선택 합니다.  그러나 홀로그램은 모든 장치에서 안정적으로 표시 되도록 동적 홀로그램 또는이를 보는 장치가 앵커의 3 미터 반지름 내에 유지 되는지 확인 해야 합니다.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>공간 앵커 그리드를 만들지 않음

사용자가 이동할 때 동적 개체를 앵커에서 앵커로 전환 하는 것 처럼 응용 프로그램이 공간 고정의 일반 표를 삭제 하도록 할 수 있습니다. 그러나 시스템 자체에서 내부적으로 유지 관리 하는 심층 센서 데이터의 장점 없이 응용 프로그램에 대 한 더 많은 관리가 수반 됩니다. 이러한 경우 위의 섹션에서 설명한 대로 참조의 고정 프레임에 holograms를 배치 하 여 더 나은 결과를 달성할 수 있습니다.
정적 공간에 대 한 클라우드 공간 앵커 집합의 위치를 미리 지정 하는 경우 앵커의 임의 그리드를 만들지 않고 위의 원칙에 따라 사용자가 holograms 키의 위치에 공간 앵커를 배치 하는 것이 좋습니다. 이렇게 하면 해당 키 홀로그램의 안정성을 극대화할 수 있습니다.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>더 이상 필요하지 않은 로컬 공간 앵커 릴리스

로컬 공간 앵커가 활성 상태인 동안 시스템은 해당 앵커 근처의 센서 데이터를 우선 순위를 유지 합니다. 더 이상 공간 앵커를 사용 하 고 있지 않은 경우 좌표계에 대 한 액세스를 중지 합니다. 따라서 필요에 따라 기본 센서 데이터를 제거할 수 있습니다.

이는 공간 앵커 저장소에 유지 된 로컬 앵커에서 특히 중요 합니다. 이러한 앵커 뒤의 센서 데이터는 응용 프로그램이 이후 세션에서 해당 앵커를 찾을 수 있도록 영구적으로 유지 되므로 다른 앵커를 추적 하는 데 사용할 수 있는 공간이 줄어듭니다. 이후 세션에서 다시 확인 해야 하는 로컬 앵커만 유지 합니다. 사용자에 게 더 이상 의미가 없을 때 저장소에서 제거 하는 것이 좋습니다.

클라우드 공간 앵커의 경우 상황에 따라 스토리지를 확장할 수 있습니다. 필요한 만큼 클라우드 앵커를 저장 하 고 사용자에 게 다시 앵커가 필요 하지 않을 때 릴리스를 해제할 수 있습니다.

## <a name="see-also"></a>추가 정보

* [좌표계](coordinate-systems.md)
* [혼합 현실의 공유 환경](../develop/platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Unity의 지속성](../develop/unity/persistence-in-unity.md)
* [DirectX의 공간 앵커](../develop/native/coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [사례 연구 - 현실의 구멍 속 살펴보기](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)