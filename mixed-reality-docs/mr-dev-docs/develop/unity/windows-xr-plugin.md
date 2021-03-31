---
title: Windows XR 플러그 인 사용
description: Windows XR 지원을 사용 하 여 MRTK를 사용 하거나 사용 하지 않고 Unity 프로젝트를 설정 하는 방법을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, mixed reality, 개발, 시작, 새 프로젝트, Windows Mixed Reality, UWP, XR, 성능, 레거시, mrtk, Windows
ms.openlocfilehash: 24da4b5116b926cfd5eda12db6eedee2f9e85621
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938123"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="66645-104">Windows XR 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="66645-104">Using Windows XR plugin</span></span>

<span data-ttu-id="66645-105">Unity 2020를 대상으로 하는 개발자를 위해 Windows XR 플러그 인을 사용 하면 HoloLens 2 및 Windows Mixed Reality 헤드셋의 혼합 현실 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66645-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="66645-106">이 플러그 인은 Unity 2019 에서도 지원 되지만, 해당 버전에서이 플러그 인을 사용 하는 경우 Azure 공간 앵커와의 알려진 비 호환성은 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66645-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="66645-107">Microsoft 및 커뮤니티에서는 WMR 환경을 자동으로 설정 하는 [mrtk (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 와 같은 활용 도구를 만들었으므로 많은 개발자 들이 처음부터 환경을 구축 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="66645-108">다음 설명서에서는 MRTK를 사용 하는지 여부에 관계 없이 혼합 현실 개발용으로 프로젝트를 올바르게 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="66645-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="66645-109">변경 해야 하는 설정은 프로젝트 당 설정 및 장면 별 설정의 두 가지 범주로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66645-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="66645-110">MRTK를 사용 하 여 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="66645-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="66645-111">Unity용 MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="66645-112">MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼용 애플리케이션 개발을 가속화하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="66645-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="66645-113">이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66645-114">MRTK 자습서를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="66645-114">Try out our MRTK tutorials</span></span>](tutorials/mr-learning-base-01.md)

<span data-ttu-id="66645-115">추가 기능에 대 한 자세한 내용은 [Mrtk의 설명서](/windows/mixed-reality/mrtk-unity) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66645-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="66645-116">MRTK 없이 수동 설치</span><span class="sxs-lookup"><span data-stu-id="66645-116">Manual setup without MRTK</span></span>

<span data-ttu-id="66645-117">데스크톱 VR를 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택 된 PC 독립 실행형 플랫폼을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="66645-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![PC, Mac & 독립 실행형 플랫폼이 강조 표시 된 unity 편집기에서 열리는 빌드 설정 창의 스크린샷](images/wmr-config-img-3.png)

<span data-ttu-id="66645-119">HoloLens 2를 대상으로 하는 경우 유니버설 Windows 플랫폼로 전환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="66645-120">**파일 > 빌드 설정** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="66645-121">플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="66645-122">**아키텍처** 를 **ARM 64** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="66645-123">**대상 장치** 를 **HoloLens** 로 설정</span><span class="sxs-lookup"><span data-stu-id="66645-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="66645-124">**빌드 유형을** **D3D** 로 설정</span><span class="sxs-lookup"><span data-stu-id="66645-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="66645-125">**UWP SDK** 를 **최신 설치** 로 설정</span><span class="sxs-lookup"><span data-stu-id="66645-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="66645-126">디버그에 알려진 성능 문제가 있으므로 **빌드 구성을** **릴리스로** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![유니버설 Windows 플랫폼 강조 표시 된 unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-4.png)

<span data-ttu-id="66645-128">플랫폼을 설정한 후에는 내보낼 때 Unity에서 2D 보기 대신 [몰입 형 보기](../../design/app-views.md) 를 만들도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="66645-129">Unity 편집기에서 **편집 > 프로젝트 설정** 으로 이동 하 고 **XR 플러그 인 관리** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="66645-130">**XR 플러그 인 관리 설치** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-130">Select **Install XR Plugin Management**</span></span>

![XR 플러그 인 관리가 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-5.png)

3. <span data-ttu-id="66645-132">시작 및 **Windows Mixed Reality** **에서 XR 초기화를** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![XR 플러그 인 관리가 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-7.png)

4. <span data-ttu-id="66645-134">**XR 플러그 인 관리** 섹션을 확장 하 고 **유니버설 Windows 플랫폼 설정** 탭을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="66645-135">Unity 2020 이상 버전을 사용 하는 경우 **OpenXR** 또는 **Windows Mixed Reality** 를 확인 하는 옵션이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66645-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="66645-136">런타임 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66645-136">You can choose either runtime.</span></span>  <span data-ttu-id="66645-137">HoloLens 2 또는 HP 반향 G2에 대해 구체적으로 개발 하 고 **OpenXR** 을 시도 하기로 결정 한 경우 OpenXR 상자를 선택 하 고이 자습서로 돌아가기 전에 [Mixed Reality OpenXR 플러그 인 Unity를 사용 하 여](openxr-getting-started.md) 이러한 장치에 대해 올바르게 설정 하는 가이드를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="66645-138">Unity 2020 LTS부터 Microsoft는 OpenXR을 사용 하 여 개발을 수용 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66645-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="66645-139">이 경로로 마이그레이션하는 동안 Unity 2021.1에서 Windows XR 플러그 인이 지원 되지 않고 2021.2에서 OpenXR만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66645-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="66645-140">[Mixed Reality OpenXR 플러그 인을 사용 하 여](openxr-getting-started.md)에서 자세한 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66645-140">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="66645-141">**Windows Mixed Reality** 플러그 인을 선택 하기로 결정 한 경우 모든 상자를 선택 하 고 **깊이 전송 모드** 를 **깊이 16 비트로** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="66645-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Windows Mixed Reality 섹션이 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-8.png)
