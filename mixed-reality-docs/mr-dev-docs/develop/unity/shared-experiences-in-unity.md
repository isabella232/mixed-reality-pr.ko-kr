---
title: Unity의 공유 환경
description: Azure 공간 앵커를 사용 하 여 Unity 응용 프로그램에서 여러 사용자 간에 동일한 holograms를 공유 하는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 공유, 고정, WorldAnchor, MR 공유 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure 공간 고정, GLOBAL.ASA, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: a82439d5676bf4bcb7898a33aafc29b43e91a49f
ms.sourcegitcommit: b13c517df19179ca281362a1f006914289c58ad4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98031959"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="2b013-104">Unity의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="2b013-104">Shared experiences in Unity</span></span>

<span data-ttu-id="2b013-105">공유 환경을 통해 각각의 HoloLens, iOS 또는 Android 장치를 포함 하는 여러 사용자가 동일한 홀로그램을 전체적으로 보고 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b013-105">A shared experience lets multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram.</span></span> <span data-ttu-id="2b013-106">Holograms는 공간 고정 공유를 통해 공간에서 고정 된 지점에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b013-106">Holograms are positioned at a fixed point in space through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="2b013-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="2b013-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="2b013-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 는 응용 프로그램이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있는 내구성이 있는 클라우드 지원 공간 앵커를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2b013-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="2b013-109">여러 장치에서 공통 공간 앵커를 공유 하 여 각 사용자는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b013-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span> 

<span data-ttu-id="2b013-110">HoloLens, iOS 및 Android 장치에서 비동기 홀로그램 지 속성에 대해 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b013-110">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="2b013-111">내구성이 있는 클라우드 공간 앵커를 공유 하 여 여러 장치는 동시에 함께 제공 되지 않더라도 시간이 지남에 따라 동일한 지속형 홀로그램을 관찰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b013-111">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="2b013-112">Unity에서 공유 환경 빌드를 시작 하려면 5 분 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 공간 앵커 Unity 퀵 스타트</a>를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="2b013-112">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="2b013-113">Azure 공간 앵커가 설정 되 면 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b013-113">Once Azure Spatial Anchors is set up, you can <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="2b013-114">로컬 앵커 전송</span><span class="sxs-lookup"><span data-stu-id="2b013-114">Local anchor transfers</span></span>

<span data-ttu-id="2b013-115">Azure 공간 앵커를 사용할 수 없는 경우 [로컬 앵커 전송은](../../out-of-scope/local-anchor-transfers-in-unity.md) 한 hololens 장치에서 앵커를 내보내 두 번째 hololens가 가져올 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b013-115">In situations where you can't use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor so that a second HoloLens can import it.</span></span>  <span data-ttu-id="2b013-116">이 접근 방식은 iOS 및 Android 장치에서 지원 되지 않으며, Azure 공간 앵커 보다 더 강력 하지 않은 앵커 회수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b013-116">This approach is not supported on iOS and Android devices, and provides less robust anchor recall than Azure Spatial Anchors.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2b013-117">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="2b013-117">Next Development Checkpoint</span></span>

<span data-ttu-id="2b013-118">앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 혼합 현실 플랫폼 기능과 Api를 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2b013-118">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="2b013-119">여기에서 다음 섹션으로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b013-119">From here, you can continue to the next section:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2b013-120">위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="2b013-120">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="2b013-121">또는 디바이스나 에뮬레이터에서 앱 배포로 직접 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2b013-121">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2b013-122">HoloLens 또는 Windows Mixed Reality 몰입 형 헤드셋에 배포</span><span class="sxs-lookup"><span data-stu-id="2b013-122">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="2b013-123">언제든지 [Unity 개발 검사점](unity-development-overview.md#3-platform-capabilities-and-apis)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b013-123">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b013-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2b013-124">See also</span></span>
* [<span data-ttu-id="2b013-125">혼합 현실의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="2b013-125">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="2b013-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="2b013-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="2b013-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity 용 Azure 공간 앵커 SDK</a></span><span class="sxs-lookup"><span data-stu-id="2b013-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
