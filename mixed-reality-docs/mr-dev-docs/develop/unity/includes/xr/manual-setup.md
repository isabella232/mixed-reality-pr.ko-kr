---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394587"
---
# <a name="openxr"></a>[<span data-ttu-id="41af7-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="41af7-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="41af7-102">새 Mixed Reality 기능 도구 애플리케이션을 사용하여 OpenXR 플러그 인을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="41af7-103">설치 [및 사용 지침에](../../welcome-to-mr-feature-tool.md) 따라 Mixed Reality Toolkit 범주에서 **Mixed Reality OpenXR 플러그 인** 패키지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![열려 있는 xr 플러그 인이 강조 표시된 Mixed Reality 기능 도구 패키지 창](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="41af7-105">빌드 대상 설정</span><span class="sxs-lookup"><span data-stu-id="41af7-105">Setting your build target</span></span>

<span data-ttu-id="41af7-106">Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

<span data-ttu-id="41af7-108">HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="41af7-109">**파일 > 빌드 설정...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="41af7-110">플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="41af7-111">**Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-111">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="41af7-112">**Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="41af7-113">**Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="41af7-114">**UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-114">Set **UWP SDK** to **Latest installed**</span></span>

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="41af7-116">OpenXR용 XR 플러그 인 관리 구성</span><span class="sxs-lookup"><span data-stu-id="41af7-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="41af7-117">OpenXR을 Unity의 런타임으로 설정하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="41af7-118">Unity 편집기에서 **프로젝트 설정 > 편집으로** 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="41af7-119">설정 목록에서 **XR 플러그 인 관리를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="41af7-120">시작 시 **XR 초기화** 및 **OpenXR** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-120">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="41af7-121">HoloLens 2 대상으로 하는 경우 UWP 플랫폼에 있는지 확인하고 **Microsoft HoloLens 기능 집합을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-121">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](../../images/openxr-img-05.png)

### <a name="optimization"></a><span data-ttu-id="41af7-123">Optimization</span><span class="sxs-lookup"><span data-stu-id="41af7-123">Optimization</span></span>

<span data-ttu-id="41af7-124">HoloLens 2 위해 개발하는 경우 **Mixed Reality> OpenXR > 앱** 성능을 향상하기 위해 HoloLens 2 권장 프로젝트 설정 적용으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-124">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![OpenXR이 선택된 혼합 현실 메뉴 항목의 스크린샷](../../images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="41af7-126">**OpenXR 플러그 인** 옆에 노란색 경고 아이콘이 표시되면 아이콘을 클릭하고 계속하기 전에 **모두 수정을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-126">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="41af7-127">Unity Editor를 다시 시작해야 변경 내용이 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-127">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 프로젝트 유효성 검사 창의 스크린샷](../../images/openxr-img-06.png)

<span data-ttu-id="41af7-129">이제 Unity에서 OpenXR로 개발을 시작할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-129">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="41af7-130">OpenXR 샘플을 사용하는 방법을 알아보려면 다음 섹션으로 계속 진행하세요.</span><span class="sxs-lookup"><span data-stu-id="41af7-130">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="41af7-131">OpenXR 및 HoloLens 2 대한 Unity 샘플 프로젝트</span><span class="sxs-lookup"><span data-stu-id="41af7-131">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="41af7-132">Mixed Reality OpenXR 플러그 인을 사용하여 HoloLens 2 또는 Mixed Reality 헤드셋용 Unity 애플리케이션을 빌드하는 방법을 보여주는 샘플 Unity 프로젝트에 대한 OpenXR Mixed Reality [샘플 리포지션을](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="41af7-132">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="41af7-133">Windows XR</span><span class="sxs-lookup"><span data-stu-id="41af7-133">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="41af7-134">Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-134">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

<span data-ttu-id="41af7-136">HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-136">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="41af7-137">**파일 > 빌드 설정...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-137">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="41af7-138">플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-138">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="41af7-139">**Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-139">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="41af7-140">**Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-140">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="41af7-141">**Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-141">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="41af7-142">**UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-142">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="41af7-143">디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

<span data-ttu-id="41af7-145">플랫폼을 설정하면 내보낼 때 2D 보기 대신 [몰입형 보기를](../../../../design/app-views.md) 만들도록 Unity에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-145">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="41af7-146">Unity 편집기에서 **프로젝트 설정 > 편집으로** 이동하고 **XR 플러그 인 관리를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-146">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="41af7-147">**XR 플러그 인 관리 설치를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-147">Select **Install XR Plugin Management**</span></span>

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="41af7-149">**시작 시 XR 초기화를** 선택하고 **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="41af7-149">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="41af7-151">**XR 플러그 인 관리 섹션을** 확장하고 **Univeral Windows 플랫폼 설정** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-151">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="41af7-152">Unity 2020 이상에서는 **OpenXR을** 확인하거나 **를 Windows Mixed Reality** 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-152">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="41af7-153">런타임 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-153">You can choose either runtime.</span></span>  <span data-ttu-id="41af7-154">HoloLens 2 또는 HP Reverb G2용으로 특별히 개발하고 **OpenXR을** 사용해 보려는 경우 OpenXR 상자를 선택하고 이 자습서로 돌아가기 전에 [Unity용 Mixed Reality OpenXR 플러그 인 사용](../../openxr-getting-started.md) 가이드를 검토하여 이러한 디바이스에 대해 올바르게 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="41af7-154">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](../../openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="41af7-155">Unity 2020 LTS부터 Microsoft는 OpenXR 개발을 수용하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-155">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="41af7-156">이 경로로 마이그레이션할 때 Unity 2021.1에서는 Windows XR 플러그 인이 더 이상 사용되지 않으며 2021.2에서 제거되어 OpenXR이 유일하게 지원되는 경로가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-156">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="41af7-157">자세한 내용은 Mixed Reality [OpenXR 플러그 인 사용을](../../openxr-getting-started.md)참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="41af7-157">You can find more information in [Using the Mixed Reality OpenXR plugin](../../openxr-getting-started.md).</span></span>

6. <span data-ttu-id="41af7-158">**Windows Mixed Reality** 플러그 인을 선택하려는 경우 모든 확인란을 선택하고 **깊이 제출 모드를** **깊이 16비트로** 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-158">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Windows Mixed Reality 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="41af7-160">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="41af7-160">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="41af7-161">Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-161">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

<span data-ttu-id="41af7-163">HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-163">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="41af7-164">**파일 > 빌드 설정...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-164">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="41af7-165">플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-165">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="41af7-166">**Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-166">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="41af7-167">**Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-167">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="41af7-168">**Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-168">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="41af7-169">**UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-169">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="41af7-170">디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-170">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

<span data-ttu-id="41af7-172">플랫폼을 설정하면 내보낼 때 2D 보기 대신 [몰입형 보기를](../../../../design/app-views.md) 만들도록 Unity에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-172">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="41af7-173">레거시 XR은 Unity 2019에서 더 이상 사용되지 않으며 Unity 2020에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-173">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="41af7-174">빌드 **설정...에서 플레이어 설정...을** **엽니다. 창** 및 **XR 설정** 그룹 확장</span><span class="sxs-lookup"><span data-stu-id="41af7-174">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="41af7-175">**XR 설정** 섹션에서 **가상 현실 지원됨을** 선택하여 가상 현실 디바이스 목록을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-175">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="41af7-176">**깊이 형식을** **16비트 깊이로** 설정하고 **깊이 버퍼 공유를** 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="41af7-176">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="41af7-177">**스테레오 렌더링 모드를** **단일 패스 인스턴스로** 설정</span><span class="sxs-lookup"><span data-stu-id="41af7-177">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="41af7-178">홀로그램 **Remoting을 사용하려면 WSA 홀로그램 Remoting 지원됨을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41af7-178">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![플레이어 설정 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-9.png)