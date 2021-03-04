---
title: 포팅 개요
description: 기존 응용 프로그램을 HoloLens 및 VR의 혼합 현실로 가져오기 위한 다양 한 이식 옵션에 대 한 개요입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: 포팅, unity, 미들웨어, 엔진, UWP, Win32
ms.openlocfilehash: 693891d67ae26098f0810a539059da8d34f4731c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759114"
---
# <a name="porting-overview"></a><span data-ttu-id="c646f-104">포팅 개요</span><span class="sxs-lookup"><span data-stu-id="c646f-104">Porting overview</span></span>

<span data-ttu-id="c646f-105">혼합 현실에 대 한 기존 프로젝트를 이식 하거나 업그레이드 하는 경우에는 앱이 Unity 또는 Unreal Engine을 사용 하 여 빌드 되었는지, HoloLens (1 Gen) 또는 HoloLens 2 또는 SteamVR를 대상으로 하는지 여부에 따라 포팅 기능이 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="c646f-106">이 개요 페이지에는 각 플랫폼 및 장치에 대 한 현재 권장 사항이 포함 되어 있습니다. 이러한 프로세스는 항상 변경 될 때 다시 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="c646f-107">먼저 [Unity](#unity) 및 [unreal](#unreal) 권장 사항에 따라 프로젝트 대상을 설정 하 고 포팅 시나리오 중 하나 이상을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="c646f-108">Hololens (첫 번째 Gen)-HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c646f-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="c646f-109">Windows Mixed Reality 헤드셋</span><span class="sxs-lookup"><span data-stu-id="c646f-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="c646f-110">SteamVR 앱</span><span class="sxs-lookup"><span data-stu-id="c646f-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="c646f-111">2D UWP 앱</span><span class="sxs-lookup"><span data-stu-id="c646f-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="c646f-112">권장 프로젝트 대상</span><span class="sxs-lookup"><span data-stu-id="c646f-112">Recommended project targets</span></span>

<span data-ttu-id="c646f-113">앱을 다른 대상 장치로 포팅 하는지 여부에 관계 없이 프로젝트를 최신 상태로 유지 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-113">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="c646f-114">현재 권장 사항은 아래에 나열 된 엔진 기반 리소스를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c646f-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="c646f-115">Unity</span><span class="sxs-lookup"><span data-stu-id="c646f-115">Unity</span></span>

<span data-ttu-id="c646f-116">혼합 현실에서 Unity 개발에 대 한 현재 권장 사항은 **레거시 XR 패키지를 사용 하는 unity 2019 LTS** 입니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="c646f-117">프로젝트가 Mixed Reality Toolkit를 사용 하는 경우 현재 **Mrtk-Unity 2.5** 인 최신 버전을 사용 하 고 있는지 다시 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="c646f-118">XR SDK는이 버전의 Unity와 함께 사용할 수 있지만, Azure 공간 앵커는 현재이 설정과 호환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="c646f-119">이 권장 사항은 Unity 용 Azure 공간 앵커 패키지의 이후 릴리스에서 업데이트 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span> 
> 
> * <span data-ttu-id="c646f-120">Azure 공간 앵커가 필요 하지 않은 경우 [XR에 대 한 Unity 프로젝트를 구성](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) 하 고 [MRTK 및 XR SDK를 사용 하 여 시작할](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/getting-started-with-mrtk-and-xrsdk.md)수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/getting-started-with-mrtk-and-xrsdk.md).</span></span>
> 
> * <span data-ttu-id="c646f-121">현재 프로젝트에서 XR SDK를 사용 하 고 있으며 Azure 공간 앵커를 사용 하려는 경우 XR SDK를 제거 하 고 레거시 XR 패키지를 다시 설치 하 여 프로젝트 설정을 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>


### <a name="unreal"></a><span data-ttu-id="c646f-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="c646f-122">Unreal</span></span> 

<span data-ttu-id="c646f-123">혼합 현실에서의 실제 개발에 대 한 현재 권장 사항은 **Unreal Engine 4.26** 입니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="c646f-124">프로젝트가 Mixed Reality Toolkit UX 도구를 사용 하는 경우 현재 **Uxt 0.10** 최신 버전을 사용 하 고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="c646f-125">포팅 시나리오</span><span class="sxs-lookup"><span data-stu-id="c646f-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="c646f-126">Hololens (첫 번째 Gen) Unity 앱-HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c646f-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="c646f-127">HoloLens 2로 이식할 기존 HoloLens (첫 번째 Gen) Unity 응용 프로그램이 있는 경우 [hololens 포팅 문서의](./porting-hl1-hl2.md)지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="c646f-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="c646f-128">Windows Mixed Reality 헤드셋</span><span class="sxs-lookup"><span data-stu-id="c646f-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="c646f-129">Oculus Rift 또는 HP 반향 G2와 같은 다른 장치에 대 한 콘텐츠를 빌드한 경우 공급 업체별 VR Sdk 및 잠재적으로 입력 매핑 Api의 대상을 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to retarget vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="c646f-130">[모던 앱 포팅 가이드](porting-guides.md)에서 Unity 및 unreal 포팅 시나리오에 대 한 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c646f-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="c646f-131">SteamVR 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="c646f-131">SteamVR applications</span></span>

<span data-ttu-id="c646f-132">Windows Mixed Reality 헤드셋에 대해 업데이트 하려는 SteamVR 환경의 경우 [SteamVR 업데이트 가이드](updating-your-steamvr-application-for-windows-mixed-reality.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c646f-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="c646f-133">2D 유니버설 Windows 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="c646f-133">2D Universal Windows applications</span></span>

<span data-ttu-id="c646f-134">Windows Mixed Reality 몰입 형 헤드셋 또는 HoloLens로 이식 하려는 기존 2D UWP 앱이 있는 경우 [Windows Mixed reality 용 2D uwp 앱 포팅](building-2d-apps.md) 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="c646f-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>