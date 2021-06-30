---
title: 포팅 개요
description: HoloLens 및 VR용 Mixed Reality 기존 애플리케이션을 가져오기 위한 다양한 이식 옵션에 대한 개요입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, unity, middleware, engine, UWP, Win32
ms.openlocfilehash: 167559d69cc4e65f971a8970b56e41e6e3ca8b22
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042274"
---
# <a name="porting-overview"></a><span data-ttu-id="75870-104">포팅 개요</span><span class="sxs-lookup"><span data-stu-id="75870-104">Porting overview</span></span>

<span data-ttu-id="75870-105">Mixed Reality 위해 기존 프로젝트를 포팅하거나 업그레이드하는 경우 포팅 여정은 앱이 Unity 또는 Unreal Engine으로 빌드되는지에 따라 달라지고 HoloLens(1세대) 또는 HoloLens 2 또는 SteamVR을 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="75870-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="75870-106">이 개요 페이지에는 각 플랫폼 및 디바이스에 대한 현재 권장 사항이 포함되어 있습니다. 이러한 프로세스는 항상 변경되기 때문에 다시 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75870-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="75870-107">먼저 [Unity](#unity) 및 [Unreal](#unreal) 권장 사항에 따라 프로젝트 대상을 설정한 다음, 하나 이상의 포팅 시나리오를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="75870-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="75870-108">HoloLens(1세대)에서 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="75870-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="75870-109">몰입형 VR 헤드셋</span><span class="sxs-lookup"><span data-stu-id="75870-109">Immersive VR headsets</span></span>](#immersive-vr-headsets)
- [<span data-ttu-id="75870-110">2D UWP 앱</span><span class="sxs-lookup"><span data-stu-id="75870-110">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="75870-111">권장되는 프로젝트 대상</span><span class="sxs-lookup"><span data-stu-id="75870-111">Recommended project targets</span></span>

<span data-ttu-id="75870-112">앱을 다른 대상 디바이스로 이식하는지 여부에 관계없이 프로젝트를 최신 상태로 유지하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="75870-112">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="75870-113">현재 권장 사항은 아래에 나열된 엔진 기반 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75870-113">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="75870-114">Unity</span><span class="sxs-lookup"><span data-stu-id="75870-114">Unity</span></span>

<span data-ttu-id="75870-115">권장 Unity 및 MRTK [버전에](../unity/choosing-unity-version.md) 대한 최신 지침은 Unity 버전 선택 페이지를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75870-115">See the [Choosing a Unity version](../unity/choosing-unity-version.md) page for up-to-date guidance on the recommended Unity and MRTK versions.</span></span>

### <a name="unreal"></a><span data-ttu-id="75870-116">Unreal</span><span class="sxs-lookup"><span data-stu-id="75870-116">Unreal</span></span>

<span data-ttu-id="75870-117">권장되는 Unreal 및 MRTK 버전에 대한 최신 지침은 Unreal 프로젝트 설정 페이지를 [참조하세요.](../unreal/unreal-project-setup.md)</span><span class="sxs-lookup"><span data-stu-id="75870-117">See the [Setting up your Unreal project](../unreal/unreal-project-setup.md) page for up-to-date guidance on the recommended Unreal and MRTK versions.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="75870-118">포팅 시나리오</span><span class="sxs-lookup"><span data-stu-id="75870-118">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="75870-119">HoloLens 2 HoloLens(1세대) Unity 앱</span><span class="sxs-lookup"><span data-stu-id="75870-119">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="75870-120">HoloLens 2 이식하려는 기존 HoloLens(1세대) Unity 애플리케이션이 있는 경우 [HoloLens 이식 문서의](./porting-hl1-hl2.md)지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="75870-120">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="immersive-vr-headsets"></a><span data-ttu-id="75870-121">몰입형 VR 헤드셋</span><span class="sxs-lookup"><span data-stu-id="75870-121">Immersive VR headsets</span></span>

<span data-ttu-id="75870-122">다른 VR 디바이스용 콘텐츠를 빌드한 경우 공급업체별 VR SDK 및 잠재적으로 입력 매핑 API의 대상을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75870-122">If you've built content for other VR devices, you'll need to retarget any vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="75870-123">[몰입형 앱](porting-guides.md)포팅 가이드 에서 Unity 및 Unreal 이식 시나리오 모두에 대한 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75870-123">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

<span data-ttu-id="75870-124">Windows Mixed Reality 헤드셋에 대해 업데이트하려는 SteamVR 환경은 [SteamVR 업데이트 가이드를](updating-your-steamvr-application-for-windows-mixed-reality.md)참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75870-124">For SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="75870-125">2D 유니버설 Windows 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="75870-125">2D Universal Windows applications</span></span>

<span data-ttu-id="75870-126">Windows Mixed Reality 몰입형 헤드셋 또는 HoloLens로 이식하려는 기존 2D UWP 앱이 있는 경우 Windows Mixed Reality [지침에 대한 이식 2D UWP 앱을](building-2d-apps.md) 따르세요.</span><span class="sxs-lookup"><span data-stu-id="75870-126">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>