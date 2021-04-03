---
title: Unity 용 Mixed Reality OpenXR 플러그 인 사용
description: Unity 프로젝트용 Mixed Reality OpenXR 플러그 인을 사용 하도록 설정 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 보강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작
ms.openlocfilehash: ebe7d32b236e28259b2ed9a7915bd337f84f8762
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088516"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="1f2e7-104">Unity 용 Mixed Reality OpenXR 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="1f2e7-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="1f2e7-105">Unity 버전 2020.2부터 Microsoft의 Mixed Reality OpenXR 플러그 인 패키지는 UPM (Unity 패키지 관리자)를 사용 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1f2e7-106">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="1f2e7-106">Prerequisites</span></span>

* <span data-ttu-id="1f2e7-107">Unity 2020.3 LTS 이상</span><span class="sxs-lookup"><span data-stu-id="1f2e7-107">Unity 2020.3 LTS or later</span></span>
* <span data-ttu-id="1f2e7-108">Unity OpenXR plugin 1.0.3 이상</span><span class="sxs-lookup"><span data-stu-id="1f2e7-108">Unity OpenXR plugin 1.0.3 or later</span></span>
* <span data-ttu-id="1f2e7-109">Visual Studio 2019 이상</span><span class="sxs-lookup"><span data-stu-id="1f2e7-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="1f2e7-110">HoloLens 2 앱 용 Unity에서 **UWP** 플랫폼 지원 설치</span><span class="sxs-lookup"><span data-stu-id="1f2e7-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="1f2e7-111">Windows PC에서 VR 응용 프로그램을 작성 하는 경우 Mixed Reality OpenXR 플러그 인이 반드시 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="1f2e7-112">그러나 HP 반향 G2 컨트롤러에 대 한 컨트롤러 매핑을 사용자 지정 하거나 HoloLens 2와 VR 헤드셋 모두에서 작동 하는 앱을 빌드하는 경우에는 플러그 인을 설치 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="1f2e7-113">MRTK를 사용 하 여 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="1f2e7-113">Setting up your project with MRTK</span></span>

<span data-ttu-id="1f2e7-114">Unity용 MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-114">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="1f2e7-115">MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼용 애플리케이션 개발을 가속화하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-115">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="1f2e7-116">이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-116">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1f2e7-117">MRTK를 사용 하 여 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="1f2e7-117">Set up your project using MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="1f2e7-118">추가 기능에 대 한 자세한 내용은 [Mrtk의 설명서](/windows/mixed-reality/mrtk-unity) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-118">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="1f2e7-119">MRTK 없이 수동 설치</span><span class="sxs-lookup"><span data-stu-id="1f2e7-119">Manual setup without MRTK</span></span>

<span data-ttu-id="1f2e7-120">새 Mixed Reality 기능 도구 응용 프로그램을 사용 하 여 OpenXR 플러그 인을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-120">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="1f2e7-121">[설치 및 사용 지침](welcome-to-mr-feature-tool.md) 을 따르고 Mixed reality Toolkit 범주의 **Mixed Reality OpenXR 플러그 인** 패키지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-121">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Open xr 플러그 인이 강조 표시 된 혼합 현실 기능 도구 패키지 창](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="1f2e7-123">빌드 대상 설정</span><span class="sxs-lookup"><span data-stu-id="1f2e7-123">Setting your build target</span></span>

<span data-ttu-id="1f2e7-124">데스크톱 VR를 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택 된 PC 독립 실행형 플랫폼을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-124">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![PC, Mac & 독립 실행형 플랫폼이 강조 표시 된 unity 편집기에서 열리는 빌드 설정 창의 스크린샷](images/wmr-config-img-3.png)

<span data-ttu-id="1f2e7-126">HoloLens 2를 대상으로 하는 경우 유니버설 Windows 플랫폼로 전환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-126">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="1f2e7-127">**파일 > 빌드 설정** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-127">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="1f2e7-128">플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-128">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="1f2e7-129">**아키텍처** 를 **ARM 64** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-129">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="1f2e7-130">**대상 장치** 를 **HoloLens** 로 설정</span><span class="sxs-lookup"><span data-stu-id="1f2e7-130">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="1f2e7-131">**빌드 유형을** **D3D** 로 설정</span><span class="sxs-lookup"><span data-stu-id="1f2e7-131">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="1f2e7-132">**UWP SDK** 를 **최신 설치** 로 설정</span><span class="sxs-lookup"><span data-stu-id="1f2e7-132">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="1f2e7-133">디버그에 알려진 성능 문제가 있으므로 **빌드 구성을** **릴리스로** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-133">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![유니버설 Windows 플랫폼 강조 표시 된 unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-4.png)

<span data-ttu-id="1f2e7-135">플랫폼을 설정한 후에는 내보낼 때 Unity에서 2D 보기 대신 [몰입 형 보기](../../design/app-views.md) 를 만들도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-135">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="1f2e7-136">OpenXR에 대 한 XR 플러그 인 관리 구성</span><span class="sxs-lookup"><span data-stu-id="1f2e7-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="1f2e7-137">OpenXR을 Unity에서 런타임으로 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="1f2e7-138">Unity 편집기에서 **편집 > 프로젝트 설정** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="1f2e7-139">설정 목록에서 **XR 플러그 인 관리** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="1f2e7-140">**INITIALIZE XR On Startup** and **OpenXR** 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="1f2e7-141">HoloLens 2를 대상으로 하는 경우 UWP 플랫폼에 있는지 확인 하 고 **Microsoft HoloLens 기능 집합** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![XR 플러그 인 관리를 강조 표시 한 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="1f2e7-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="1f2e7-143">Optimization</span></span>

<span data-ttu-id="1f2e7-144">HoloLens 2 용으로 개발 하는 경우 **> OpenXR> Mixed Reality로 이동 하 여 hololens 2에 권장 되는 프로젝트 설정을 적용** 하 여 더 나은 앱 성능을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![OpenXR가 선택 된 혼합 현실 메뉴 항목 열기의 스크린샷](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="1f2e7-146">**OpenXR 플러그 인** 옆에 빨간색 경고 아이콘이 표시 되 면이 아이콘을 클릭 하 고 계속 하기 전에 **모두 수정** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="1f2e7-147">Unity 편집기를 다시 시작 해야 변경 내용이 적용 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 프로젝트 유효성 검사 창의 스크린샷](images/openxr-img-06.png)

<span data-ttu-id="1f2e7-149">이제 Unity에서 OpenXR를 사용 하 여 개발을 시작할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="1f2e7-150">OpenXR 샘플을 사용 하는 방법을 알아보려면 다음 섹션을 계속 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="1f2e7-151">Unity 샘플 장면을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-151">Try out the Unity sample scenes</span></span>

### <a name="hololens-2-samples"></a><span data-ttu-id="1f2e7-152">HoloLens 2 샘플</span><span class="sxs-lookup"><span data-stu-id="1f2e7-152">HoloLens 2 samples</span></span>

1. <span data-ttu-id="1f2e7-153">Unity 편집기에서 **창 > 패키지 관리자** 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-153">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="1f2e7-154">패키지 목록에서 **Mixed Reality OpenXR 플러그 인** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-154">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="1f2e7-155">**샘플 목록에서** 샘플을 찾고 **가져오기** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-155">Locate the sample in the **Samples** list and select **Import**</span></span>

![Unity 편집기에서 open Reality OpenXR 플러그 인을 선택 하 고 샘플 가져오기 단추가 강조 표시 된 Unity 패키지 관리자의 스크린샷](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="1f2e7-157">패키지가 업데이트 되 면 Unity는 가져온 샘플을 업데이트 하는 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-157">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="1f2e7-158">가져온 샘플을 업데이트 하면 샘플 및 연결 된 자산에 대 한 모든 변경 내용이 덮어쓰여집니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-158">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="1f2e7-159">OpenXR 지원과 함께 MRTK 사용</span><span class="sxs-lookup"><span data-stu-id="1f2e7-159">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="1f2e7-160">MRTK-Unity 2.5.3 릴리스부터 혼합 현실 OpenXR 플러그 인을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-160">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="1f2e7-161">혼합 현실 [기능 도구](welcome-to-mr-feature-tool.md) 를 다시 열어 혼합 현실 도구 키트 (아직 없는 경우)를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-161">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="1f2e7-162">OpenXR 지원은 **Foundation** 패키지에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-162">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="1f2e7-163">검사기에서 MixedReality Toolkit 구성 요소 스크립트로 이동 하 고 **Defaultopenxrconfigurationprofile** 프로필로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-163">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![검사기의 Mixed Reality Toolkit 구성 요소에서 MRTK 구성 전환 스크린샷](images/openxr-img-11.png)

    1. <span data-ttu-id="1f2e7-165">[OpenXR로 마이그레이션하](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)는 방법에 대 한 자세한 내용은 MRTK 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-165">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="1f2e7-166">이전 버전의 MRTK에서 업그레이드 하는 경우 asset **/MixedRealityToolkit/link.xml** 파일에 다음 줄이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-166">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="1f2e7-167">이 줄은 MRTK 2.5.4 이상으로 시작한 경우 기본적으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-167">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1f2e7-168">다음 단계</span><span class="sxs-lookup"><span data-stu-id="1f2e7-168">Next steps</span></span>

<span data-ttu-id="1f2e7-169">이제 OpenXR에 대해 프로젝트를 구성 하 고 샘플에 액세스할 수 있으므로, OpenXR 플러그 인에서 현재 지원 되는 [기능](openxr-supported-features.md) 을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-169">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="1f2e7-170">피드백이 있나요?</span><span class="sxs-lookup"><span data-stu-id="1f2e7-170">Have Feedback?</span></span>

<span data-ttu-id="1f2e7-171">OpenXR는 여전히 실험적 이므로 피드백을 제공 하는 데 도움이 되도록 피드백을 보내 주셔서 감사 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-171">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="1f2e7-172">[](https://aka.ms/unityforums) **Microsoft**  +  **OpenXR** 및 **HoloLens 2** 또는 **Windows Mixed Reality** 를 사용 하 여 포럼 게시물에 태그를 지정 하 여 Unity 포럼에서이를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f2e7-172">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f2e7-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f2e7-173">See also</span></span>

* [<span data-ttu-id="1f2e7-174">MRTK를 사용하지 않고 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="1f2e7-174">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="1f2e7-175">Unity 권장 설정</span><span class="sxs-lookup"><span data-stu-id="1f2e7-175">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="1f2e7-176">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="1f2e7-176">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
