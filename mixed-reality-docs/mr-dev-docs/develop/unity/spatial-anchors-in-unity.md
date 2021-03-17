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
# <a name="spatial-anchors-in-unity"></a><span data-ttu-id="86e10-104">Unity의 공간 앵커</span><span class="sxs-lookup"><span data-stu-id="86e10-104">Spatial Anchors in Unity</span></span>

<span data-ttu-id="86e10-105">공간 앵커는 응용 프로그램 세션 간에 실제 공간에 holograms를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="86e10-105">Spatial anchors save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="86e10-106">HoloLens의 앵커 저장소에 저장 한 후에는 서로 다른 세션에서 검색 하 고 로드할 수 있으며 인터넷에 연결 되지 않은 경우 이상적인 대체입니다.</span><span class="sxs-lookup"><span data-stu-id="86e10-106">Once saved in the HoloLens' anchor store, they can be found and loaded in different sessions and are an ideal fallback when there's no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86e10-107">로컬 앵커는 디바이스에 저장되는 반면, Azure Spatial Anchors는 클라우드에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="86e10-107">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="86e10-108">Azure Cloud Services를 사용하여 앵커를 저장하려는 경우 [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors) 통합 과정을 안내하는 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86e10-108">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span></span> <span data-ttu-id="86e10-109">로컬 및 Azure 앵커는 동일한 프로젝트에서 충돌 없이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86e10-109">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="understanding-anchors"></a><span data-ttu-id="86e10-110">앵커 이해</span><span class="sxs-lookup"><span data-stu-id="86e10-110">Understanding Anchors</span></span>

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a><span data-ttu-id="86e10-111">AnchorStore 사용</span><span class="sxs-lookup"><span data-stu-id="86e10-111">Using the AnchorStore</span></span>

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="86e10-112">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="86e10-112">Next Development Checkpoint</span></span>

<span data-ttu-id="86e10-113">앞서 설명한 Unity 개발 검사점 경험을 팔로 사용할 경우 혼합 현실 핵심 빌딩 블록을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="86e10-113">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="86e10-114">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86e10-114">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="86e10-115">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="86e10-115">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="86e10-116">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="86e10-116">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="86e10-117">공유 환경</span><span class="sxs-lookup"><span data-stu-id="86e10-117">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="86e10-118">언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86e10-118">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="86e10-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86e10-119">See Also</span></span>
* [<span data-ttu-id="86e10-120">공간 앵커 지 속성</span><span class="sxs-lookup"><span data-stu-id="86e10-120">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="86e10-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="86e10-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="86e10-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity 용 Azure 공간 앵커 SDK</a></span><span class="sxs-lookup"><span data-stu-id="86e10-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
* [<span data-ttu-id="86e10-123">환경 크기 조정</span><span class="sxs-lookup"><span data-stu-id="86e10-123">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="86e10-124">공간 스테이지</span><span class="sxs-lookup"><span data-stu-id="86e10-124">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="86e10-125">Unity의 손실 추적</span><span class="sxs-lookup"><span data-stu-id="86e10-125">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="86e10-126">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="86e10-126">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="86e10-127">Unity의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="86e10-127">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)