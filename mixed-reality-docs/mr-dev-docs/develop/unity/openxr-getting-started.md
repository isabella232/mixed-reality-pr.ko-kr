---
title: 혼합 현실 OpenXR 플러그 인 사용
description: Unity 프로젝트에 Mixed Reality OpenXR 플러그 인을 사용하도록 설정하는 방법을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 증강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작
ms.openlocfilehash: 733bbbd75dd170241e8781e24989d23902781fb9
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333445"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="852c5-104">혼합 현실 OpenXR 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="852c5-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="852c5-105">Unity 2020을 대상으로 하는 개발자가 HoloLens 2 빌드하거나 애플리케이션을 Mixed Reality 경우 플랫폼 간 호환성을 높이기 위해 WindowsXR 플러그 인 대신 OpenXR 플러그 인을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="852c5-106">Mixed Reality OpenXR 플러그 인은 최신 Mixed Reality 기능 도구 에서도 잘 [작동합니다.](welcome-to-mr-feature-tool.md)</span><span class="sxs-lookup"><span data-stu-id="852c5-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="852c5-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="852c5-107">Prerequisites</span></span>

* <span data-ttu-id="852c5-108">최신 Unity 2020.3 LTS는 2020.3.6f1 이상을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-108">Latest Unity 2020.3 LTS, recommend 2020.3.6f1 or above.</span></span>
* <span data-ttu-id="852c5-109">최신 Unity OpenXR 플러그 인, 1.2 이상 권장</span><span class="sxs-lookup"><span data-stu-id="852c5-109">Latest Unity OpenXR plugin, recommend 1.2 or later</span></span>
* <span data-ttu-id="852c5-110">[HoloLens 2 개발을 위한](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist) 최신 도구</span><span class="sxs-lookup"><span data-stu-id="852c5-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="852c5-111">최신 MRTK(선택 사항), 버전 2.6 이상 권장</span><span class="sxs-lookup"><span data-stu-id="852c5-111">Latest MRTK (optional), recommend version 2.6 or later</span></span>
* <span data-ttu-id="852c5-112">최신 Mixed Reality OpenXR 플러그 인, 버전 0.9.5 이상 권장</span><span class="sxs-lookup"><span data-stu-id="852c5-112">Latest Mixed Reality OpenXR Plugin, recommend version 0.9.5 or later</span></span>

> [!NOTE]
> <span data-ttu-id="852c5-113">Windows PC VR 애플리케이션을 빌드하는 경우 Mixed Reality OpenXR 플러그 인이 반드시 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-113">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="852c5-114">그러나 HP Reverb G2 컨트롤러에 대한 컨트롤러 매핑을 사용자 지정하거나 HoloLens 2 헤드셋과 VR 헤드셋 모두에서 작동하는 앱을 빌드하는 경우 플러그 인을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-114">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="852c5-115">MRTK를 통해 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="852c5-115">Setting up your project with MRTK</span></span>

<span data-ttu-id="852c5-116">Unity용 MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-116">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="852c5-117">MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼용 애플리케이션 개발을 가속화하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-117">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="852c5-118">이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-118">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="852c5-119">MRTK를 사용하여 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="852c5-119">Set up your project using MRTK</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="852c5-120">기능에 대한 자세한 내용은 [MRTK 설명서](/windows/mixed-reality/mrtk-unity)를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="852c5-120">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="852c5-121">MRTK 없이 수동 설정</span><span class="sxs-lookup"><span data-stu-id="852c5-121">Manual setup without MRTK</span></span>

<span data-ttu-id="852c5-122">새 Mixed Reality 기능 도구 애플리케이션을 사용하여 OpenXR 플러그 인을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-122">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="852c5-123">설치 [및 사용 지침에](welcome-to-mr-feature-tool.md) 따라 Mixed Reality Toolkit 범주에서 **Mixed Reality OpenXR 플러그 인** 패키지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-123">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![열려 있는 xr 플러그 인이 강조 표시된 Mixed Reality 기능 도구 패키지 창](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="852c5-125">빌드 대상 설정</span><span class="sxs-lookup"><span data-stu-id="852c5-125">Setting your build target</span></span>

<span data-ttu-id="852c5-126">Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-126">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-3.png)

<span data-ttu-id="852c5-128">HoloLens 2를 대상으로 하는 경우 유니버설 Windows 플랫폼로 전환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-128">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="852c5-129">**파일 > 빌드 설정** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-129">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="852c5-130">플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-130">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="852c5-131">**Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-131">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="852c5-132">**Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-132">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="852c5-133">**Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-133">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="852c5-134">**UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-134">Set **UWP SDK** to **Latest installed**</span></span>

![유니버설 Windows 플랫폼 강조 표시 된 unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="852c5-136">OpenXR에 대 한 XR 플러그 인 관리 구성</span><span class="sxs-lookup"><span data-stu-id="852c5-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="852c5-137">OpenXR을 Unity에서 런타임으로 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="852c5-138">Unity 편집기에서 **편집 > 프로젝트 설정** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="852c5-139">설정 목록에서 **XR 플러그 인 관리** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="852c5-140">**INITIALIZE XR On Startup** and **OpenXR** 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="852c5-141">HoloLens 2를 대상으로 하는 경우 UWP 플랫폼에 있는지 확인 하 고 **Microsoft HoloLens 기능 집합** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![XR 플러그 인 관리를 강조 표시 한 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="852c5-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="852c5-143">Optimization</span></span>

<span data-ttu-id="852c5-144">HoloLens 2 용으로 개발 하는 경우 **> OpenXR> Mixed Reality로 이동 하 여 hololens 2에 권장 되는 프로젝트 설정을 적용** 하 여 더 나은 앱 성능을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![OpenXR가 선택 된 혼합 현실 메뉴 항목 열기의 스크린샷](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="852c5-146">**OpenXR 플러그 인** 옆에 빨간색 경고 아이콘이 표시 되 면이 아이콘을 클릭 하 고 계속 하기 전에 **모두 수정** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="852c5-147">Unity Editor를 다시 시작해야 변경 내용이 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 프로젝트 유효성 검사 창의 스크린샷](images/openxr-img-06.png)

<span data-ttu-id="852c5-149">이제 Unity에서 OpenXR를 사용 하 여 개발을 시작할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="852c5-150">OpenXR 샘플을 사용 하는 방법을 알아보려면 다음 섹션을 계속 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="852c5-151">OpenXR 및 HoloLens 용 Unity 샘플 프로젝트 2</span><span class="sxs-lookup"><span data-stu-id="852c5-151">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="852c5-152">Sample unity 프로젝트에 대 한 [OpenXR Mixed Reality 샘플 리포지토리](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 를 확인 합니다. 보여주는 Mixed reality OpenXR 플러그 인을 사용 하 여 HoloLens 2 용 unity 응용 프로그램을 빌드하는 방법 또는 mixed reality 헤드셋을 빌드하는 방법.</span><span class="sxs-lookup"><span data-stu-id="852c5-152">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="852c5-153">OpenXR 지원과 함께 MRTK 사용</span><span class="sxs-lookup"><span data-stu-id="852c5-153">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="852c5-154">MRTK-Unity 2.5.3 릴리스부터 Mixed Reality OpenXR 플러그 인을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-154">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="852c5-155">Mixed Reality [기능 도구를](welcome-to-mr-feature-tool.md) 다시 열어 아직 설치하지 않은 경우 Mixed Reality 도구 키트를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-155">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="852c5-156">OpenXR 지원은 **Foundation** 패키지에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-156">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="852c5-157">검사기에서 MixedReality Toolkit 구성 요소 스크립트로 이동하고 **DefaultOpenXRConfigurationProfile 프로필로** 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-157">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![검사기의 Mixed Reality Toolkit 구성 요소에서 MRTK 구성을 전환하는 스크린샷](images/openxr-img-11.png)

    1. <span data-ttu-id="852c5-159">[OpenXR로 마이그레이션하는](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)자세한 내용은 MRTK 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="852c5-159">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="852c5-160">이전 버전의 MRTK에서 업그레이드하는 경우 **Assets/MixedRealityToolkit.Generated/link.xml** 파일에 다음 줄이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-160">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="852c5-161">MRTK 2.5.4 이상으로 시작한 경우 이 줄이 기본적으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-161">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="852c5-162">다음 단계</span><span class="sxs-lookup"><span data-stu-id="852c5-162">Next steps</span></span>

<span data-ttu-id="852c5-163">이제 OpenXR에 대해 프로젝트를 구성하고 샘플에 액세스할 수 있게 했으므로 OpenXR 플러그 인에서 현재 지원되는 [기능을](openxr-supported-features.md) 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="852c5-163">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="852c5-164">피드백이 있나요?</span><span class="sxs-lookup"><span data-stu-id="852c5-164">Have Feedback?</span></span>

<span data-ttu-id="852c5-165">OpenXR은 아직 실험적이므로 더 나은 도움을 줄 수 있는 피드백을 보내 주시면 감사하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="852c5-165">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="852c5-166">**Microsoft** OpenXR로 포럼 게시물에 태그를 지정하고 HoloLens 2 또는 Windows Mixed Reality [Unity 포럼에서](https://aka.ms/unityforums) 찾을 수  +   있습니다.  </span><span class="sxs-lookup"><span data-stu-id="852c5-166">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="852c5-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="852c5-167">See also</span></span>

* [<span data-ttu-id="852c5-168">MRTK를 사용하지 않고 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="852c5-168">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="852c5-169">Unity 권장 설정</span><span class="sxs-lookup"><span data-stu-id="852c5-169">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="852c5-170">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="852c5-170">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
