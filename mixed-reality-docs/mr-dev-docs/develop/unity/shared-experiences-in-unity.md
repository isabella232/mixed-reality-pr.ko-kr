---
title: Unity의 공유 환경
description: Unity 응용 프로그램에서 여러 사용자 간에 동일한 holograms를 공유 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 공유, 고정, WorldAnchor, MR 공유 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure 공간 고정, GLOBAL.ASA, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: c9f432a2ef26e28a2329f9fd191f680a4148ca7e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678462"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="114df-104">Unity의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="114df-104">Shared experiences in Unity</span></span>

<span data-ttu-id="114df-105">공유 환경은 각 사용자가 각각의 HoloLens, iOS 또는 Android 장치를 포함 하는 여러 사용자가 일정 한 위치에 배치 된 동일한 홀로그램을 전체적으로 보고 상호 작용 하는 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="114df-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="114df-106">공간 고정 공유를 통해 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="114df-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="114df-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="114df-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="114df-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용 하 여 앱이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있는 내구성이 뛰어난 클라우드 지원 공간 앵커를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114df-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="114df-109">여러 장치에서 공통 공간 앵커를 공유 하 여 각 사용자는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114df-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="114df-110">이렇게 실제 세계 공유 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="114df-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="114df-111">HoloLens, iOS 및 Android 디바이스에서 비대칭 홀로그램 지속에 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114df-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="114df-112">유지되는 클라우드 공간 앵커를 공유하면 여러 디바이스가 동시에 함께 존재하지 않는 경우에도 시간 경과에 따라 같은 지속형 홀로그램을 관찰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114df-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="114df-113">Unity에서 공유 환경 빌드를 시작 하려면 5 분 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 공간 앵커 Unity 퀵 스타트</a>를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="114df-113">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="114df-114">Azure 공간 앵커를 사용 하 여 실행 하면 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114df-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="114df-115">로컬 앵커 전송</span><span class="sxs-lookup"><span data-stu-id="114df-115">Local anchor transfers</span></span>

<span data-ttu-id="114df-116">Azure 공간 앵커를 사용할 수 없는 경우 [로컬 앵커 전송](../../out-of-scope/local-anchor-transfers-in-unity.md) 에서는 한 hololens 장치에서 두 번째 hololens 장치에서 가져올 앵커를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114df-116">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="114df-117">이 방법은 Azure 공간 앵커 보다 더 강력 하지 않은 앵커 회수를 제공 하며, iOS 및 Android 장치는이 방식에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="114df-117">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="114df-118">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="114df-118">Next Development Checkpoint</span></span>

<span data-ttu-id="114df-119">앞서 소개한 Unity 개발 검사점 경험을 팔로 하는 경우 혼합 현실 플랫폼 기능과 Api를 탐색 하는 과정을 진행 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114df-119">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="114df-120">여기에서 다음 항목을 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114df-120">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="114df-121">위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="114df-121">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="114df-122">또는 디바이스나 에뮬레이터에서 앱 배포로 직접 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="114df-122">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="114df-123">HoloLens 또는 Windows Mixed Reality 몰입 형 헤드셋에 배포</span><span class="sxs-lookup"><span data-stu-id="114df-123">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="114df-124">언제든지 [Unity 개발 검사점](unity-development-overview.md#3-platform-capabilities-and-apis)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114df-124">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="114df-125">참조</span><span class="sxs-lookup"><span data-stu-id="114df-125">See also</span></span>
* [<span data-ttu-id="114df-126">혼합 현실의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="114df-126">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="114df-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="114df-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="114df-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity 용 Azure 공간 앵커 SDK</a></span><span class="sxs-lookup"><span data-stu-id="114df-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
