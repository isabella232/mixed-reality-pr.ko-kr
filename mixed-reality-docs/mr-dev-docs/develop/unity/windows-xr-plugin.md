---
title: Windows XR 플러그 인 사용
description: Windows XR 지원을 사용하여 MRTK를 사용하든 사용하지 않고 Unity 프로젝트를 설정하는 방법을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트, Windows Mixed Reality, UWP, XR, 성능, 레거시, mrtk, windows
ms.openlocfilehash: c9733d58236d97db370ce4f58dc1760bdf4eda86
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110238"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="8311c-104">Windows XR 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="8311c-104">Using Windows XR plugin</span></span>

<span data-ttu-id="8311c-105">Unity 2020을 대상으로 하는 개발자의 경우 Windows XR 플러그 인을 사용하면 HoloLens 2 및 Windows Mixed Reality 헤드셋에서 혼합 현실 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="8311c-106">이 플러그 인은 Unity 2019에서도 지원되지만, 해당 버전에서 이 플러그 인을 사용하는 경우 Azure Spatial Anchors 호환되지 않는 것으로 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="8311c-107">Microsoft와 커뮤니티는 WMR 환경을 자동으로 설정하는 [MRTK(Mixed Reality Toolkit)와](/windows/mixed-reality/mrtk-unity/configuration/usingupm) 같은 오픈 소스 도구를 만들었지만 많은 개발자는 처음부터 환경을 구축하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="8311c-108">다음 설명서에서는 MRTK 사용 여부에 관계없이 Mixed Reality 개발을 위한 프로젝트를 올바르게 설정하는 방법을 보여 드립니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="8311c-109">변경해야 하는 설정은 프로젝트별 설정 및 장면별 설정의 두 가지 범주로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="8311c-110">MRTK를 통해 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="8311c-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="8311c-111">Unity용 MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="8311c-112">MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼용 애플리케이션 개발을 가속화하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="8311c-113">이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8311c-114">MRTK 자습서 사용해보기</span><span class="sxs-lookup"><span data-stu-id="8311c-114">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=winxr)

<span data-ttu-id="8311c-115">기능에 대한 자세한 내용은 [MRTK 설명서](/windows/mixed-reality/mrtk-unity)를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="8311c-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="8311c-116">MRTK 없이 수동 설정</span><span class="sxs-lookup"><span data-stu-id="8311c-116">Manual setup without MRTK</span></span>

<span data-ttu-id="8311c-117">Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-3.png)

<span data-ttu-id="8311c-119">HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="8311c-120">**파일 > 빌드 설정...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="8311c-121">플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="8311c-122">**Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="8311c-123">**Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="8311c-124">**Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="8311c-125">**UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="8311c-126">디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-4.png)

<span data-ttu-id="8311c-128">플랫폼을 설정하면 내보낼 때 2D 보기 대신 [몰입형 보기를](../../design/app-views.md) 만들도록 Unity에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="8311c-129">Unity 편집기에서 **프로젝트 설정 > 편집으로** 이동하고 **XR 플러그 인 관리를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="8311c-130">**XR 플러그 인 관리 설치를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-130">Select **Install XR Plugin Management**</span></span>

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](images/wmr-config-img-5.png)

3. <span data-ttu-id="8311c-132">**시작 시 XR 초기화를** 선택하고 **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="8311c-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](images/wmr-config-img-7.png)

4. <span data-ttu-id="8311c-134">**XR 플러그 인 관리 섹션을** 확장하고 **Univeral Windows 플랫폼 설정** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="8311c-135">Unity 2020 이상에서는 **OpenXR을** 확인하거나 **를 Windows Mixed Reality** 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="8311c-136">런타임 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-136">You can choose either runtime.</span></span>  <span data-ttu-id="8311c-137">HoloLens 2 또는 HP Reverb G2용으로 특별히 개발하고 **OpenXR을** 사용해 보려는 경우 OpenXR 상자를 선택하고 이 자습서로 돌아가기 전에 [Unity용 Mixed Reality OpenXR 플러그 인 사용](openxr-getting-started.md) 가이드를 검토하여 이러한 디바이스에 대해 올바르게 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="8311c-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="8311c-138">Unity 2020 LTS부터 Microsoft는 OpenXR 개발을 수용하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="8311c-139">이 경로로 마이그레이션할 때 Unity 2021.1에서는 Windows XR 플러그 인이 더 이상 사용되지 않으며 2021.2에서 제거되어 OpenXR이 유일하게 지원되는 경로가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="8311c-140">자세한 내용은 Mixed Reality [OpenXR 플러그 인 사용을](openxr-getting-started.md)참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8311c-140">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="8311c-141">**Windows Mixed Reality** 플러그 인을 선택하려는 경우 모든 확인란을 선택하고 **깊이 제출 모드를** **깊이 16비트로** 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8311c-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Windows Mixed Reality 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](images/wmr-config-img-8.png)