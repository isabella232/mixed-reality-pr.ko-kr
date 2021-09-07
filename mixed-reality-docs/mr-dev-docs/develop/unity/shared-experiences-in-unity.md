---
title: Unity의 공유 환경
description: Azure 공간 앵커를 사용 하 여 Unity 응용 프로그램에서 여러 사용자 간에 동일한 holograms를 공유 하는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 공유, 고정, WorldAnchor, MR 공유 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure 공간 고정, GLOBAL.ASA, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: f7725c8282d1b5a93d555ac0f55ee936b910ff6c
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244189"
---
# <a name="shared-experiences-in-unity"></a>Unity의 공유 환경

공유 환경에서는 여러 사용자가 고유한 HoloLens, iOS 또는 Android 장치를 사용 하 여 동일한 홀로그램을 전체적으로 보고 상호 작용할 수 있습니다. 공간 고정 공유를 통해 홀로그램스 고정 된 지점에 배치 됩니다.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

### <a name="automated-with-world-locking-tools"></a>세계 잠금 도구를 사용 하 여 자동화

로컬 앵커와 마찬가지로 세계 잠금 도구는 개별 개체를 잠그기 위해 개별 앵커를 사용 하는 대신 Azure 공간 앵커 그룹을 사용 하 여 실제 세계에 상대적인 전체 좌표 공간을 잠글 수 있습니다. 전체 공간을 잠그는 것은 정확한 레이아웃에 더 취약 환경을 제공 하는 것이 아니라 개발자 시간 및 런타임 리소스에도 더 효율적입니다.

Azure 공간 앵커를 활용 하 여 HoloLens, Android 및 iOS 장치에서 좌표계를 공유 하 고 세션 간에 공간을 유지 하는 방법에 대 한 자세한 내용과 샘플은 [세계 잠금 도구 설명서](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLT_ASA.html)를 참조 하세요.

### <a name="manual-configuration-of-azure-spatial-anchors"></a>Azure 공간 앵커의 수동 구성

<a href="/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 는 앱이 여러 HoloLens, iOS 및 Android 장치에서 찾을 수 있는 내구성이 있는 클라우드 지원 공간 앵커를 만듭니다.  여러 장치에서 공통 공간 앵커를 공유 하 여 각 사용자는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.

HoloLens, iOS 및 Android 장치에서 비동기 홀로그램 지 속성에 대해 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용할 수도 있습니다.  내구성이 있는 클라우드 공간 앵커를 공유 하 여 여러 장치는 동시에 함께 제공 되지 않더라도 시간이 지남에 따라 동일한 지속형 홀로그램을 관찰할 수 있습니다.

Unity에서 공유 환경 빌드를 시작 하려면 5 분 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 공간 앵커 Unity 퀵 스타트</a>를 사용해 보세요.

Azure 공간 앵커가 설정 되 면 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.

## <a name="local-anchor-transfers"></a>로컬 앵커 전송

Azure 공간 앵커를 사용할 수 없는 경우 [로컬 앵커 전송은](../../out-of-scope/local-anchor-transfers-in-unity.md) 한 HoloLens 장치가 앵커를 내보내 두 번째 HoloLens 가져올 수 있도록 합니다.  이 접근 방식은 iOS 및 Android 장치에서 지원 되지 않으며, Azure 공간 앵커 보다 더 강력 하지 않은 앵커 회수를 제공 합니다.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 혼합 현실 플랫폼 기능과 Api를 탐색 하는 것이 좋습니다. 여기에서 다음 섹션으로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [위치를 찾을 수 있는 카메라](locatable-camera-in-unity.md)

또는 디바이스나 에뮬레이터에서 앱 배포로 직접 이동합니다.

> [!div class="nextstepaction"]
> [HoloLens 또는 Windows Mixed Reality 모던 헤드셋에 배포](../platform-capabilities-and-apis/using-visual-studio.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#3-advanced-features)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목
* [혼합 현실의 공유 환경](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity 용 Azure 공간 앵커 SDK</a>