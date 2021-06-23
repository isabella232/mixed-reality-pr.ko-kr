---
ms.openlocfilehash: c965eb1b4edc91421e0b8b2e96893a04431aef6e
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112535727"
---
# <a name="openxr"></a>[<span data-ttu-id="07fdf-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="07fdf-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="07fdf-102">새 Mixed Reality 기능 도구 애플리케이션을 사용하여 OpenXR 플러그 인을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-102">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="07fdf-103">설치 [및 사용 지침에](../../welcome-to-mr-feature-tool.md) 따라 **플랫폼 지원** 범주에서 **Mixed Reality OpenXR 플러그 인** 패키지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-103">Follow the [installation and usage instructions](../../welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the **Platform Support** category:</span></span>

![열려 있는 xr 플러그 인이 강조 표시된 Mixed Reality 기능 도구 패키지 창](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a><span data-ttu-id="07fdf-105">빌드 대상 설정</span><span class="sxs-lookup"><span data-stu-id="07fdf-105">Setting your build target</span></span>

<span data-ttu-id="07fdf-106">Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-106">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

<span data-ttu-id="07fdf-108">HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-108">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="07fdf-109">**파일 > 빌드 설정...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="07fdf-110">플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-110">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="07fdf-111">**아키텍처** 를 **ARM64** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-111">Set **Architecture** to **ARM64**</span></span>
4. <span data-ttu-id="07fdf-112">**Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-112">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="07fdf-113">**Build Type(빌드 형식)** 을 **D3D Project(D3D 프로젝트)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-113">Set **Build Type** to **D3D Project**</span></span>
6. <span data-ttu-id="07fdf-114">**대상 SDK 버전을** 최신 **설치로** 설정</span><span class="sxs-lookup"><span data-stu-id="07fdf-114">Set **Target SDK Version** to **Latest installed**</span></span>

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="07fdf-116">OpenXR용 XR 플러그 인 관리 구성</span><span class="sxs-lookup"><span data-stu-id="07fdf-116">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="07fdf-117">OpenXR을 Unity의 런타임으로 설정하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-117">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="07fdf-118">Unity 편집기에서 **프로젝트 설정 > 편집으로** 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-118">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="07fdf-119">설정 목록에서 **XR 플러그 인 관리를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-119">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="07fdf-120">**XR 플러그 인 관리가** 강조 표시된 ![ Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷이 표시되면 XR 플러그 인 관리 설치를 선택합니다.](../../images/wmr-config-img-5.png)</span><span class="sxs-lookup"><span data-stu-id="07fdf-120">Select **Install XR Plugin Management** if it appears ![Screenshot of Project Settings window open in unity editor with XR Plugin management highlighted](../../images/wmr-config-img-5.png)</span></span>
4. <span data-ttu-id="07fdf-121">시작 시 **XR 초기화** 상자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-121">Check the **Initialize XR on Startup** box</span></span>
5. <span data-ttu-id="07fdf-122">데스크톱 VR을 대상으로 하는 경우 PC 독립 실행형 탭(모니터)을 유지하고 **OpenXR** 및 **Windows Mixed Reality 기능 집합** 상자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-122">If targeting Desktop VR, stay on the PC Standalone tab (the monitor) and check the **OpenXR** and **Windows Mixed Reality feature set** boxes</span></span>
6. <span data-ttu-id="07fdf-123">HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 탭(Windows 로고)으로 전환하고 **OpenXR** 및 **Microsoft HoloLens 기능 집합** 상자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-123">If targeting HoloLens 2, switch to the Universal Windows Platform tab (the Windows logo) and select the **OpenXR** and **Microsoft HoloLens feature set** boxes</span></span>

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](../../images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="07fdf-125">**OpenXR 플러그 인** 옆에 노란색 경고 아이콘이 표시되면 아이콘을 클릭하고 계속하기 전에 **모두 수정을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-125">If you see a yellow warning icon next to **OpenXR Plugin**, click the icon and select **Fix All** before continuing.</span></span> <span data-ttu-id="07fdf-126">Unity Editor를 다시 시작해야 변경 내용이 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-126">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR 프로젝트 유효성 검사 창의 스크린샷](../../images/openxr-img-06.png)

### <a name="optimization"></a><span data-ttu-id="07fdf-128">Optimization</span><span class="sxs-lookup"><span data-stu-id="07fdf-128">Optimization</span></span>

<span data-ttu-id="07fdf-129">HoloLens 2 위해 개발하는 경우 앱 성능을 향상하려면 **Mixed Reality > 프로젝트 > HoloLens 2** 권장 프로젝트 설정 적용 메뉴 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-129">If you're developing for HoloLens 2, select the **Mixed Reality > Project > Apply recommended project settings for HoloLens 2** menu item to get better app performance.</span></span>

![OpenXR이 선택된 혼합 현실 메뉴 항목의 스크린샷](../../images/openxr-img-08.png)

<span data-ttu-id="07fdf-131">이제 Unity에서 OpenXR로 개발을 시작할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-131">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="07fdf-132">OpenXR 샘플을 사용하는 방법을 알아보려면 다음 섹션으로 계속 진행하세요.</span><span class="sxs-lookup"><span data-stu-id="07fdf-132">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="07fdf-133">OpenXR 및 HoloLens 2 대한 Unity 샘플 프로젝트</span><span class="sxs-lookup"><span data-stu-id="07fdf-133">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="07fdf-134">Mixed Reality OpenXR 플러그 인을 사용하여 HoloLens 2 또는 Mixed Reality 헤드셋용 Unity 애플리케이션을 빌드하는 방법을 보여주는 샘플 Unity 프로젝트에 대한 OpenXR Mixed Reality [샘플 리포지션을](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="07fdf-134">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="07fdf-135">또는 빈 프로젝트에서 직접 시작할 준비가 되면 [카메라 설정](../../camera-in-unity.md) 문서로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-135">Or, if you're ready to get started on your own from a blank project, proceed to the [Camera setup](../../camera-in-unity.md) article.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="07fdf-136">Windows XR</span><span class="sxs-lookup"><span data-stu-id="07fdf-136">Windows XR</span></span>](#tab/windowsxr)

> [!CAUTION]
> <span data-ttu-id="07fdf-137">Windows XR 플러그 인은 Unity 2021.1에서 더 이상 사용되지 않으며 Unity 2021.2에서 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-137">The Windows XR plugin is deprecated in Unity 2021.1 and will be removed in Unity 2021.2.</span></span>  <span data-ttu-id="07fdf-138">Unity 2020 개발의 경우 OpenXR 플러그 인을 대신 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-138">For Unity 2020 development, Microsoft recommends the OpenXR plugin instead.</span></span>

<span data-ttu-id="07fdf-139">Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-139">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

<span data-ttu-id="07fdf-141">HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-141">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="07fdf-142">**파일 > 빌드 설정...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-142">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="07fdf-143">플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-143">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="07fdf-144">**아키텍처** 를 **ARM64** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-144">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="07fdf-145">**Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-145">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="07fdf-146">**Build Type(빌드 형식)** 을 **D3D Project(D3D 프로젝트)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-146">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="07fdf-147">**대상 SDK 버전을** 최신 **설치로** 설정</span><span class="sxs-lookup"><span data-stu-id="07fdf-147">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="07fdf-148">디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-148">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

<span data-ttu-id="07fdf-150">플랫폼을 설정하면 내보낼 때 2D 보기 대신 [몰입형 보기를](../../../../design/app-views.md) 만들도록 Unity에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-150">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="07fdf-151">Unity 편집기에서 **프로젝트 설정 > 편집으로** 이동하고 **XR 플러그 인 관리를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-151">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="07fdf-152">표시되는 경우 **XR 플러그 인 관리 설치를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-152">Select **Install XR Plugin Management** if it appears</span></span>

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-5.png)

3. <span data-ttu-id="07fdf-154">**시작 시 XR 초기화를** 선택하고 **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="07fdf-154">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-7.png)

4. <span data-ttu-id="07fdf-156">**XR 플러그 인 관리**  >  **Windows Mixed Reality** 섹션을 선택하고, 모든 확인란을 선택하고, **깊이 버퍼 형식을 깊이 버퍼** **16비트로** 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-156">Select the **XR Plug-in Management** > **Windows Mixed Reality** section, check all boxes and set **Depth Buffer Format** to **Depth Buffer 16 Bit**</span></span>

![Windows Mixed Reality 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[<span data-ttu-id="07fdf-158">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="07fdf-158">Legacy XR</span></span>](#tab/legacy)

> [!CAUTION]
> <span data-ttu-id="07fdf-159">레거시 XR은 Unity 2019에서 더 이상 사용되지 않으며 Unity 2020에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-159">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

<span data-ttu-id="07fdf-160">Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-160">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

<span data-ttu-id="07fdf-162">HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-162">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="07fdf-163">**파일 > 빌드 설정...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-163">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="07fdf-164">플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-164">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="07fdf-165">**아키텍처** 를 **ARM64** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-165">Set **Architecture** to **ARM64**</span></span>
4.  <span data-ttu-id="07fdf-166">**Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-166">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="07fdf-167">**Build Type(빌드 형식)** 을 **D3D Project(D3D 프로젝트)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-167">Set **Build Type** to **D3D Project**</span></span>
6.  <span data-ttu-id="07fdf-168">**대상 SDK 버전을** 최신 **설치로** 설정</span><span class="sxs-lookup"><span data-stu-id="07fdf-168">Set **Target SDK Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="07fdf-169">디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-169">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

<span data-ttu-id="07fdf-171">플랫폼을 설정하면 내보낼 때 2D 보기 대신 [몰입형 보기를](../../../../design/app-views.md) 만들도록 Unity에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-171">After setting your platform, you need to let Unity know to create an [immersive view](../../../../design/app-views.md) instead of a 2D view when exported.</span></span>

1. <span data-ttu-id="07fdf-172">빌드 **설정...에서 플레이어 설정...을** **엽니다. 창** 및 **XR 설정** 그룹 확장</span><span class="sxs-lookup"><span data-stu-id="07fdf-172">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="07fdf-173">**XR 설정** 섹션에서 **가상 현실 지원됨을** 선택하여 가상 현실 디바이스 목록을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-173">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="07fdf-174">**깊이 형식을** **16비트 깊이로** 설정하고 **깊이 버퍼 공유 사용을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-174">Set **Depth Format** to **16-bit depth** and check **Enable Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="07fdf-175">**Stereo Rendering Mode(스테레오 렌더링 모드)** 를 **Single Pass Instanced(단일 패스 인스턴스화됨)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-175">Set **Stereo Rendering Mode** to **Single Pass Instanced**</span></span>
5. <span data-ttu-id="07fdf-176">홀로그램 재생 모드 **Remoting을 사용하려면 WSA 홀로그램 Remoting 지원됨을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07fdf-176">Select **WSA Holographic Remoting Supported** if you'd like to use holographic play mode remoting</span></span>

![플레이어 설정 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-9.png)
