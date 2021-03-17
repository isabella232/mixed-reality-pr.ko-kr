---
title: Unity의 공간 앵커
description: Unity mixed reality 응용 프로그램에서 공간 앵커를 만들고, 저장 하 고, 페치하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity, 공간 앵커, 앵커 저장소, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623623"
---
# <a name="spatial-anchors-in-unity"></a>Unity의 공간 앵커

공간 앵커는 응용 프로그램 세션 간에 실제 공간에 holograms를 저장 합니다. HoloLens의 앵커 저장소에 저장 한 후에는 서로 다른 세션에서 검색 하 고 로드할 수 있으며 인터넷에 연결 되지 않은 경우 이상적인 대체입니다.

> [!IMPORTANT]
> 로컬 앵커는 디바이스에 저장되는 반면, Azure Spatial Anchors는 클라우드에 저장됩니다. Azure Cloud Services를 사용하여 앵커를 저장하려는 경우 [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors) 통합 과정을 안내하는 문서를 참조하세요. 로컬 및 Azure 앵커는 동일한 프로젝트에서 충돌 없이 사용할 수 있습니다.

## <a name="understanding-anchors"></a>앵커 이해

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a>AnchorStore 사용

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞서 설명한 Unity 개발 검사점 경험을 팔로 사용할 경우 혼합 현실 핵심 빌딩 블록을 탐색 하는 것이 좋습니다. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [공간 매핑](spatial-mapping-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목
* [공간 앵커 지 속성](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity 용 Azure 공간 앵커 SDK</a>
* [환경 크기 조정](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [공간 스테이지](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity의 손실 추적](tracking-loss-in-unity.md)
* [Spatial Anchors](../../design/spatial-anchors.md)
* [Unity의 공유 환경](shared-experiences-in-unity.md)