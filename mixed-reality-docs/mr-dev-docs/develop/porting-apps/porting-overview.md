---
title: 포팅 개요
description: HoloLens 및 VR용 Mixed Reality 기존 애플리케이션을 가져오기 위한 다양한 이식 옵션에 대한 개요입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, unity, middleware, engine, UWP, Win32
ms.openlocfilehash: 9b056bd81a725fea23c1e7f3bfcd9844680086c6
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600502"
---
# <a name="porting-overview"></a><span data-ttu-id="57f81-104">포팅 개요</span><span class="sxs-lookup"><span data-stu-id="57f81-104">Porting overview</span></span>

<span data-ttu-id="57f81-105">Mixed Reality 위해 기존 프로젝트를 포팅하거나 업그레이드하는 경우 포팅 여정은 앱이 Unity 또는 Unreal Engine으로 빌드되는지에 따라 달라지고 HoloLens(1세대) 또는 HoloLens 2 또는 SteamVR을 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="57f81-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="57f81-106">이 개요 페이지에는 각 플랫폼 및 디바이스에 대한 현재 권장 사항이 포함되어 있습니다. 이러한 프로세스는 항상 변경되기 때문에 다시 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57f81-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="57f81-107">먼저 [Unity](#unity) 및 [Unreal](#unreal) 권장 사항에 따라 프로젝트 대상을 설정한 다음, 하나 이상의 포팅 시나리오를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="57f81-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="57f81-108">HoloLens(1세대)에서 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="57f81-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="57f81-109">Windows Mixed Reality 헤드셋</span><span class="sxs-lookup"><span data-stu-id="57f81-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="57f81-110">SteamVR 앱</span><span class="sxs-lookup"><span data-stu-id="57f81-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="57f81-111">2D UWP 앱</span><span class="sxs-lookup"><span data-stu-id="57f81-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="57f81-112">권장되는 프로젝트 대상</span><span class="sxs-lookup"><span data-stu-id="57f81-112">Recommended project targets</span></span>

<span data-ttu-id="57f81-113">앱을 다른 대상 디바이스로 이식하는지 여부에 관계없이 프로젝트를 최신 상태로 유지하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="57f81-113">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="57f81-114">현재 권장 사항은 아래에 나열된 엔진 기반 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57f81-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="57f81-115">Unity</span><span class="sxs-lookup"><span data-stu-id="57f81-115">Unity</span></span>

<span data-ttu-id="57f81-116">Mixed Reality 사용한 Unity 개발에 대한 현재 권장 사항은 **레거시 XR 패키지를 사용하는 Unity 2019 LTS입니다.**</span><span class="sxs-lookup"><span data-stu-id="57f81-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="57f81-117">프로젝트에서 Mixed Reality 도구 키트를 사용하는 경우 현재 **MRTK-Unity 2.5** 최신 버전인지 다시 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="57f81-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="57f81-118">이 버전의 Unity에서 XR SDK를 사용할 수 있지만 Azure Spatial Anchors 현재 이 설정과 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57f81-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="57f81-119">이 권장 사항은 Unity용 Azure Spatial Anchors 패키지의 이후 릴리스로 업데이트될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="57f81-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span>
> 
> * <span data-ttu-id="57f81-120">Azure Spatial Anchors 필요하지 않은 경우 [XR용 Unity 프로젝트를 구성하고](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) [MRTK 및 XR SDK를 시작할](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk)수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57f81-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk).</span></span>
> 
> * <span data-ttu-id="57f81-121">현재 프로젝트에서 XR SDK를 사용하고 있고 Azure Spatial Anchors 사용하려는 경우 XR SDK를 제거하고 레거시 XR 패키지를 다시 설치하여 프로젝트 설정을 되돌려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57f81-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>

### <a name="unreal"></a><span data-ttu-id="57f81-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="57f81-122">Unreal</span></span>

<span data-ttu-id="57f81-123">Mixed Reality Unreal 개발을 위한 현재 권장 사항은 **Unreal Engine 4.26입니다.**</span><span class="sxs-lookup"><span data-stu-id="57f81-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="57f81-124">프로젝트에서 Mixed Reality 도구 키트 UX 도구를 사용하는 경우 현재 **UXT 0.10인** 최신 버전을 사용하고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="57f81-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="57f81-125">포팅 시나리오</span><span class="sxs-lookup"><span data-stu-id="57f81-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="57f81-126">HoloLens 2 HoloLens(1세대) Unity 앱</span><span class="sxs-lookup"><span data-stu-id="57f81-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="57f81-127">HoloLens 2 이식하려는 기존 HoloLens(1세대) Unity 애플리케이션이 있는 경우 [HoloLens 이식 문서의](./porting-hl1-hl2.md)지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="57f81-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="57f81-128">Windows Mixed Reality 헤드셋</span><span class="sxs-lookup"><span data-stu-id="57f81-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="57f81-129">OculusTar 또는 HP Reverb G2와 같은 다른 디바이스용 콘텐츠를 빌드한 경우 공급업체별 VR SDK 및 잠재적으로 입력 매핑 API의 대상을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57f81-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to retarget vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="57f81-130">[몰입형 앱](porting-guides.md)포팅 가이드 에서 Unity 및 Unreal 이식 시나리오 모두에 대한 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57f81-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="57f81-131">SteamVR 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="57f81-131">SteamVR applications</span></span>

<span data-ttu-id="57f81-132">Windows Mixed Reality 헤드셋에 대해 업데이트하려는 모든 SteamVR 환경은 [SteamVR 업데이트 가이드를](updating-your-steamvr-application-for-windows-mixed-reality.md)참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57f81-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="57f81-133">2D 유니버설 Windows 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="57f81-133">2D Universal Windows applications</span></span>

<span data-ttu-id="57f81-134">Windows Mixed Reality 몰입형 헤드셋 또는 HoloLens로 이식하려는 기존 2D UWP 앱이 있는 경우 Windows Mixed Reality [지침에 대한 이식 2D UWP 앱을](building-2d-apps.md) 따르세요.</span><span class="sxs-lookup"><span data-stu-id="57f81-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>