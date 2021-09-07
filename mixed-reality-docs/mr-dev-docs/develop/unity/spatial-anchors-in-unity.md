---
title: Unity의 세계 잠금 및 공간 앵커
description: Unity 혼합 현실 애플리케이션에서 World Locking Tools 및 spatial anchors를 사용하는 방법을 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 04/7/2021
ms.topic: article
keywords: Unity, 공간 앵커, 앵커 저장소, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 세계 잠금 도구, 홀로그램
ms.openlocfilehash: 1de3571d0ad43308acad459021f2c2e9a1a6e1e7
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244303"
---
# <a name="world-locking-and-spatial-anchors-in-unity"></a>Unity의 세계 잠금 및 공간 앵커

![세계 잠금 도구 영웅 이미지](images/wlt-img-01.jpeg)

홀로그램을 제 위치에 유지하거나, 사용자와 함께 이동하거나, 경우에 따라 다른 홀로그램을 기준으로 배치하는 것은 Mixed Reality 애플리케이션을 만드는 데 중요한 부분입니다. 이 문서에서는 World Locking Tools를 사용하는 권장 솔루션을 안내하지만 Unity 프로젝트에서 공간 앵커를 수동으로 설정하는 방법도 설명합니다. 코드를 시작하기 전에 Unity가 자체 엔진에서 좌표 공간 및 앵커를 처리하는 방법을 이해하는 것이 중요합니다.

## <a name="world-scale-coordinate-systems"></a>세계적 크기 조정 좌표계

오늘날 게임, 데이터 시각화 앱 또는 가상 현실 앱을 작성할 때 일반적인 방법은 다른 모든 좌표가 안정적으로 다시 매핑할 수 있는 하나의 절대 **세계 좌표계를** 설정하는 것입니다. 이 환경에서는 항상 해당 세계의 두 개체 간의 관계를 정의하는 안정적인 변환을 찾을 수 있습니다. 이러한 개체를 이동하지 않은 경우 상대 변환은 항상 동일하게 유지됩니다. 이러한 종류의 전역 좌표계는 모든 기하 도형을 미리 알고 있는 순수 가상 세계를 렌더링할 때 쉽게 파악할 수 있습니다. 오늘날 방 규모 VR 앱은 일반적으로 이러한 종류의 절대 방 크기 조정 좌표계를 층의 원점으로 설정합니다.

반면, HoloLens 같은 테더링되지 않은 혼합 현실 디바이스는 전 세계에 대한 동적 센서 기반의 이해를 가지고 있으며, 건물 전체 층에서 여러 미터를 걸으며 사용자 주변 시간에 따른 지식을 지속적으로 조정합니다. 세계적 환경의 경우 모든 홀로그램을 순진한 고정 좌표계에 배치하면 이러한 홀로그램은 세계 또는 서로를 기준으로 시간이 지남에 따라 드리프트됩니다.

예를 들어 헤드셋은 현재 전 세계 두 위치가 4미터 떨어져 있다고 생각한 다음, 나중에 해당 위치가 실제로 3.9미터 떨어져 있다는 것을 알게 됨을 이해하도록 구체화할 수 있습니다. 처음에 홀로그램이 단일 고정 좌표계에서 4미터 떨어져 있는 경우 그 중 하나는 항상 실제 세계에서 0.1미터 떨어져 표시됩니다.

사용자가 모바일일 때 실제 세계에서 홀로그램의 위치를 유지하기 위해 Unity에 **공간 앵커를** 수동으로 배치할 수 있습니다. 그러나 이렇게 하면 가상 세계 내에서 자체 일관성이 없어질 수 있습니다. 서로 다른 앵커는 지속적으로 서로 관련해서 이동하며 전역 좌표 공간을 통해서도 이동합니다. 이 시나리오에서는 레이아웃과 같은 간단한 작업이 어려워지고 물리학 시뮬레이션에 문제가 있습니다.

**World Locking Tools는** 사용자가 이동할 때 가상 장면 전체에 분산된 공간 앵커의 내부 공급으로 단일 고정 좌표계를 안정화하여 두 세계의 최고를 제공합니다. 도구는 카메라의 좌표를 분석하고 해당 공간 앵커는 모든 프레임을 고정합니다. 사용자 머리 좌표의 수정 사항을 보정하기 위해 전 세계의 모든 좌표를 변경하는 대신, 도구는 머리의 좌표를 수정하기만 합니다.

## <a name="choosing-your-world-locking-approach"></a>세계 잠금 방법 선택

* 모든 홀로그램 위치 관리 요구 사항에 **대해 World Locking Tools를** 사용하는 것이 좋습니다.
    * World Locking Tools는 가상 세계 표식과 실제 표식 간의 표시 불일치를 최소화하는 안정적인 좌표계를 제공합니다. 다시 말해서, 각 개체 그룹을 그룹 고유의 개별 앵커로 잠그지 않고 앵커의 공유 풀을 통해 전체 장면을 잠금합니다.
    * World Locking Tools는 공간 앵커의 모든 생성 및 관리를 내부적으로 자동으로 처리합니다. 홀로그램을 세계 잠금 상태로 유지하기 위해 **ARAnchorManager** 또는 **WorldAnchor와** 상호 작용할 필요가 없습니다.
* **OpenXR 또는 Windows XR 플러그 인을 사용하는 Unity 2019/2020의 경우** **ARAnchorManager를** 사용해야 합니다.
* **이전 Unity 버전 또는 WSA** 프로젝트의 경우 **WorldAnchor를** 사용해야 합니다.

## <a name="setting-up-world-locking"></a>세계 잠금 설정

[!INCLUDE[](includes/world-locking/world-locking-setup.md)]

## <a name="persistent-world-locking"></a>영구 세계 잠금

공간 앵커는 애플리케이션 세션 간의 실제 공간에 홀로그램을 저장합니다. HoloLens 앵커 저장소에 저장되면 다른 세션에서 찾아서 로드할 수 있으며 인터넷에 연결되지 않은 경우 이상적인 대체(fallback)입니다.

> [!IMPORTANT]
> 로컬 앵커는 디바이스에 저장되는 반면, Azure Spatial Anchors는 클라우드에 저장됩니다. Azure Cloud Services를 사용하여 앵커를 저장하려는 경우 [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors) 통합 과정을 안내하는 문서를 참조하세요. 로컬 및 Azure 앵커는 동일한 프로젝트에서 충돌 없이 사용할 수 있습니다.

[!INCLUDE[](includes/world-locking/world-locking-persistence.md)]

## <a name="sharing-coordinate-spaces"></a>좌표 공간 공유

세계 잠금 좌표 공간을 공유하려면 포괄적인 [공유 환경 설명서를 확인하세요.](shared-experiences-in-unity.md)

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unity 개발 검사점 여정을 수행하는 경우 Mixed Reality 핵심 구성 요소 탐색을 진행하게 됩니다. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [공간 매핑](spatial-mapping-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목
* [World Locking Tools 소개](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/IntroFAQ.html)
* [빠른 시작 가이드](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/QuickStart.html)
* [자습서](https://microsoft.github.io/MixedReality-WorldLockingTools-Samples/Tutorial/01_Minimal/01_Minimal.html)
* [샘플](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/SampleApplications.html)
* [공간 앵커 지속성](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity용 Azure Spatial Anchors SDK</a>
* [환경 크기 조정](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [공간 단계](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity의 손실 추적](tracking-loss-in-unity.md)
* [Spatial Anchors](../../design/spatial-anchors.md)
* [Unity의 공유 환경](shared-experiences-in-unity.md)
