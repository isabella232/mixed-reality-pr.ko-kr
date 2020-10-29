---
title: DirectX의 공유 공간 앵커
description: 공간 앵커를 공유 하 여 두 HoloLens 장치를 동기화 하는 방법을 설명 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, 동기화, 공간 앵커, 전송, 여럿이, 보기, 시나리오, 연습, 샘플 코드, Azure, Azure 공간 앵커, 자신
ms.openlocfilehash: 2d6485e46a9802e1ee7e5adc12d6e0d026c79ae9
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684912"
---
# <a name="shared-experiences-in-directx"></a><span data-ttu-id="6892b-104">DirectX의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="6892b-104">Shared experiences in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="6892b-105">이 문서는 레거시 WinRT 네이티브 Api와 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6892b-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="6892b-106">새 네이티브 앱 프로젝트의 경우 **[OPENXR API](../native/openxr-getting-started.md)** 를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6892b-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)** .</span></span>

<span data-ttu-id="6892b-107">공유 환경은 각 사용자가 각각의 HoloLens, iOS 또는 Android 장치를 포함 하는 여러 사용자가 일정 한 위치에 배치 된 동일한 홀로그램을 전체적으로 보고 상호 작용 하는 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="6892b-107">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="6892b-108">공간 고정 공유를 통해 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6892b-108">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="6892b-109">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="6892b-109">Azure Spatial Anchors</span></span>

<span data-ttu-id="6892b-110"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용 하 여 앱이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있는 내구성이 뛰어난 클라우드 지원 공간 앵커를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6892b-110">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="6892b-111">여러 장치에서 공통 공간 앵커를 공유 하 여 각 사용자는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6892b-111">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="6892b-112">이렇게 실제 세계 공유 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6892b-112">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="6892b-113">HoloLens, iOS 및 Android 디바이스에서 비대칭 홀로그램 지속에 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6892b-113">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="6892b-114">유지되는 클라우드 공간 앵커를 공유하면 여러 디바이스가 동시에 함께 존재하지 않는 경우에도 시간 경과에 따라 같은 지속형 홀로그램을 관찰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6892b-114">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="6892b-115">HoloLens 앱에서 공유 환경 빌드를 시작 하려면 5 분 <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 공간 앵커 HoloLens 빠른</a>시작을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="6892b-115">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="6892b-116">Azure 공간 앵커를 사용 하 여 실행 하면 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens에서 앵커를 만들고 찾을</a>수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6892b-116">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="6892b-117"><a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 및 iOS</a> 에 대 한 연습을 사용할 수 있으므로 모든 장치에서 동일한 앵커를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6892b-117">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="6892b-118">로컬 앵커 전송</span><span class="sxs-lookup"><span data-stu-id="6892b-118">Local anchor transfers</span></span>

<span data-ttu-id="6892b-119">Azure 공간 앵커를 사용할 수 없는 경우 [로컬 앵커 전송](../../out-of-scope/local-anchor-transfers-in-directx.md) 에서는 한 hololens 장치에서 두 번째 hololens 장치에서 가져올 앵커를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6892b-119">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-directx.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="6892b-120">이 방법은 Azure 공간 앵커 보다 더 강력 하지 않은 앵커 회수를 제공 하며, iOS 및 Android 장치는이 방식에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6892b-120">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="6892b-121">참조</span><span class="sxs-lookup"><span data-stu-id="6892b-121">See also</span></span>
* [<span data-ttu-id="6892b-122">혼합 현실의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="6892b-122">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="6892b-123"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="6892b-123"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="6892b-124"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">HoloLens 용 Azure 공간 앵커 SDK</a></span><span class="sxs-lookup"><span data-stu-id="6892b-124"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK for HoloLens</a></span></span>