---
title: Unity의 공유 환경
description: Azure 공간 앵커를 사용 하 여 Unity 응용 프로그램에서 여러 사용자 간에 동일한 holograms를 공유 하는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 공유, 고정, WorldAnchor, MR 공유 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure 공간 고정, GLOBAL.ASA, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 7762a76e1eaa944f69153b13fb0f380c7dce643e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583364"
---
# <a name="shared-experiences-in-unity"></a>Unity의 공유 환경

공유 환경을 통해 각각의 HoloLens, iOS 또는 Android 장치를 포함 하는 여러 사용자가 동일한 홀로그램을 전체적으로 보고 상호 작용할 수 있습니다. Holograms는 공간 고정 공유를 통해 공간에서 고정 된 지점에 배치 됩니다.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

<a href="/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 는 응용 프로그램이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있는 내구성이 있는 클라우드 지원 공간 앵커를 만듭니다.  여러 장치에서 공통 공간 앵커를 공유 하 여 각 사용자는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다. 

HoloLens, iOS 및 Android 장치에서 비동기 홀로그램 지 속성에 대해 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용할 수도 있습니다.  내구성이 있는 클라우드 공간 앵커를 공유 하 여 여러 장치는 동시에 함께 제공 되지 않더라도 시간이 지남에 따라 동일한 지속형 홀로그램을 관찰할 수 있습니다.

Unity에서 공유 환경 빌드를 시작 하려면 5 분 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 공간 앵커 Unity 퀵 스타트</a>를 사용해 보세요.

Azure 공간 앵커가 설정 되 면 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.

## <a name="local-anchor-transfers"></a>로컬 앵커 전송

Azure 공간 앵커를 사용할 수 없는 경우 [로컬 앵커 전송은](../../out-of-scope/local-anchor-transfers-in-unity.md) 한 hololens 장치에서 앵커를 내보내 두 번째 hololens가 가져올 수 있도록 합니다.  이 접근 방식은 iOS 및 Android 장치에서 지원 되지 않으며, Azure 공간 앵커 보다 더 강력 하지 않은 앵커 회수를 제공 합니다.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 혼합 현실 플랫폼 기능과 Api를 탐색 하는 것이 좋습니다. 여기에서 다음 섹션으로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [위치를 찾을 수 있는 카메라](locatable-camera-in-unity.md)

또는 디바이스나 에뮬레이터에서 앱 배포로 직접 이동합니다.

> [!div class="nextstepaction"]
> [HoloLens 또는 Windows Mixed Reality 몰입 형 헤드셋에 배포](../platform-capabilities-and-apis/using-visual-studio.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#3-advanced-features)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목
* [혼합 현실의 공유 환경](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity 용 Azure 공간 앵커 SDK</a>