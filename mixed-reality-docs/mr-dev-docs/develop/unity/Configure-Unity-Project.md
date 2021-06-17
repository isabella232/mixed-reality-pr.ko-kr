---
title: MRTK 없이 프로젝트 구성
description: Mixed Reality Toolkit 없이 Windows Mixed Reality 새 Unity 프로젝트를 구성하는 방법을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트, Windows Mixed Reality, UWP, XR, 성능
ms.openlocfilehash: c496dc415ff09eea3015b5195e131554c43a98f1
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110252"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="21c4a-104">MRTK를 사용하지 않고 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="21c4a-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="21c4a-105">WMR(Windows Mixed Reality)은 Windows 10 운영 체제의 일부로 도입된 Microsoft 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="21c4a-106">WMR 플랫폼을 사용하면 홀로그램 및 VR 디스플레이 디바이스에서 디지털 콘텐츠를 렌더링하는 애플리케이션을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="21c4a-107">Microsoft와 커뮤니티는 WMR 환경을 자동으로 설정하는 [MRTK(Mixed Reality Toolkit)와](/windows/mixed-reality/mrtk-unity/configuration/usingupm) 같은 오픈 소스 도구를 만들었지만 많은 개발자는 처음부터 환경을 구축하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-107">While Microsoft and the community have created open source tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="21c4a-108">다음 설명서에서는 MRTK 사용 여부에 관계없이 Mixed Reality 개발을 위한 프로젝트를 올바르게 설정하는 방법을 보여 드립니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="21c4a-109">변경해야 하는 설정은 프로젝트별 설정 및 장면별 설정의 두 가지 범주로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="21c4a-110">나중에 언제든지 MRTK를 가져올 수 있으므로 수동 경로를 먼저 진행하기 위한 페널티가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="21c4a-111">WMR 수동 설정을 선택하는 경우 변경해야 하는 설정은 프로젝트당 및 장면당 두 가지 범주로 세분화됩니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="21c4a-112">프로젝트별 설정</span><span class="sxs-lookup"><span data-stu-id="21c4a-112">Per-project settings</span></span>

<span data-ttu-id="21c4a-113">Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-3.png)

<span data-ttu-id="21c4a-115">HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="21c4a-116">**파일 > 빌드 설정...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="21c4a-117">플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="21c4a-118">**Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="21c4a-119">**Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="21c4a-120">**Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="21c4a-121">**UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="21c4a-122">디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-4.png)

<span data-ttu-id="21c4a-124">플랫폼을 설정하면 내보낼 때 2D 보기 대신 [몰입형 보기를](../../design/app-views.md) 만들도록 Unity에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="21c4a-125">XRSDK의 경우</span><span class="sxs-lookup"><span data-stu-id="21c4a-125">For XRSDK</span></span> 

1. <span data-ttu-id="21c4a-126">Unity 편집기에서 **프로젝트 설정 > 편집으로** 이동하고 **XR 플러그 인 관리를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="21c4a-127">**XR 플러그 인 관리 설치를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-127">Select **Install XR Plugin Management**</span></span>

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](images/wmr-config-img-5.png)

3. <span data-ttu-id="21c4a-129">**시작 시 XR 초기화를** 선택하고 **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="21c4a-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](images/wmr-config-img-7.png)

4. <span data-ttu-id="21c4a-131">**XR 플러그 인 관리 섹션을** 확장하고 **Univeral Windows 플랫폼 설정** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-131">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="21c4a-132">Unity 2020 이상에서는 **OpenXR을** 확인하거나 **를 Windows Mixed Reality** 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-132">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="21c4a-133">런타임 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-133">You can choose either runtime.</span></span>  <span data-ttu-id="21c4a-134">HoloLens 2 또는 HP Reverb G2용으로 특별히 개발하고 **OpenXR을** 사용해 보려는 경우 OpenXR 상자를 선택하고 이 자습서로 돌아가기 전에 [Unity용 Mixed Reality OpenXR 플러그 인 사용](openxr-getting-started.md) 가이드를 검토하여 이러한 디바이스에 대해 올바르게 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="21c4a-134">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="21c4a-135">Unity 2020 LTS부터 Microsoft는 OpenXR 개발을 수용하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-135">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="21c4a-136">이 경로로 마이그레이션할 때 Unity 2021.1에서는 Windows XR 플러그 인이 더 이상 사용되지 않으며 2021.2에서 제거되어 OpenXR이 유일하게 지원되는 경로가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-136">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="21c4a-137">자세한 내용은 Mixed Reality [OpenXR 플러그 인 사용을](openxr-getting-started.md)참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="21c4a-137">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="21c4a-138">**Windows Mixed Reality** 플러그 인을 선택하려는 경우 모든 확인란을 선택하고 **깊이 제출 모드를** **깊이 16비트로** 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-138">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Windows Mixed Reality 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="21c4a-140">레거시 XR의 경우</span><span class="sxs-lookup"><span data-stu-id="21c4a-140">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="21c4a-141">레거시 XR은 Unity 2019에서 더 이상 사용되지 않으며 Unity 2020에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-141">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="21c4a-142">빌드 **설정...에서 플레이어 설정...을** **엽니다. 창** 및 **XR 설정** 그룹 확장</span><span class="sxs-lookup"><span data-stu-id="21c4a-142">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="21c4a-143">**XR 설정** 섹션에서 **가상 현실 지원됨을** 선택하여 가상 현실 디바이스 목록을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-143">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="21c4a-144">**깊이 형식을** **16비트 깊이로** 설정하고 **깊이 버퍼 공유를** 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="21c4a-144">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="21c4a-145">**스테레오 렌더링 모드를** **단일 패스 인스턴스로** 설정</span><span class="sxs-lookup"><span data-stu-id="21c4a-145">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="21c4a-146">홀로그램 **Remoting을 사용하려면 WSA 홀로그램 Remoting 지원됨을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-146">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![플레이어 설정 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="21c4a-148">매니페스트 업데이트</span><span class="sxs-lookup"><span data-stu-id="21c4a-148">Updating the manifest</span></span>

<span data-ttu-id="21c4a-149">이제 앱에서 홀로그램 렌더링 및 공간 입력을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-149">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="21c4a-150">그러나 앱은 특정 기능을 활용하기 위해 매니페스트에서 적절한 기능을 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-150">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="21c4a-151">유니버설 Windows 플랫폼 > 게시 설정 > 기능에 **대한 플레이어 설정 > 설정으로** 가서 프로젝트 기능을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-151">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="21c4a-152">내보내는 모든 향후 프로젝트에 포함하려면 Unity에서 매니페스트 선언을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-152">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="21c4a-153">Mixed Reality 일반적으로 사용되는 Unity API를 사용하도록 설정하는 데 적용 가능한 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-153">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="21c4a-154">기능</span><span class="sxs-lookup"><span data-stu-id="21c4a-154">Capability</span></span>  |  <span data-ttu-id="21c4a-155">기능이 필요한 API</span><span class="sxs-lookup"><span data-stu-id="21c4a-155">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="21c4a-156">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="21c4a-156">SpatialPerception</span></span>  |  <span data-ttu-id="21c4a-157">SurfaceObserver(HoloLens의 [공간 매핑](../../design/spatial-mapping.md) 메시에 대한 액세스) &mdash; *헤드셋의 일반적인 공간 추적에 필요한 기능이 없습니다.*</span><span class="sxs-lookup"><span data-stu-id="21c4a-157">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="21c4a-158">웹캠</span><span class="sxs-lookup"><span data-stu-id="21c4a-158">WebCam</span></span>  |  <span data-ttu-id="21c4a-159">PhotoCapture 및 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="21c4a-159">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="21c4a-160">PicturesLibrary / VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="21c4a-160">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="21c4a-161">각각 PhotoCapture 또는 VideoCapture(캡처된 콘텐츠를 저장할 때)</span><span class="sxs-lookup"><span data-stu-id="21c4a-161">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="21c4a-162">마이크</span><span class="sxs-lookup"><span data-stu-id="21c4a-162">Microphone</span></span>  |  <span data-ttu-id="21c4a-163">VideoCapture(오디오 캡처 시), DictationRecognizer, GrammarRecognizer 및 KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="21c4a-163">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="21c4a-164">InternetClient</span><span class="sxs-lookup"><span data-stu-id="21c4a-164">InternetClient</span></span>  |  <span data-ttu-id="21c4a-165">DictationRecognizer(Unity Profiler 사용)</span><span class="sxs-lookup"><span data-stu-id="21c4a-165">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="21c4a-166">품질 설정</span><span class="sxs-lookup"><span data-stu-id="21c4a-166">Quality settings</span></span>

<span data-ttu-id="21c4a-167">HoloLens에는 모바일 클래스 GPU가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-167">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="21c4a-168">앱이 HoloLens를 대상으로 하는 경우 가장 빠른 성능을 위해 튜닝된 앱의 품질 설정으로 시작하여 전체 프레임 속도를 유지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-168">If your app is targeting HoloLens, you'll want to start off with the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate.</span></span>  <span data-ttu-id="21c4a-169">개발 과정에서 더 나아가면 품질 및 성능의 적절한 균형을 찾기 위해 품질 설정을 향상하는 것을 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-169">Once you have your are further along in your development you may consider upping the quality settings to find the right balance of quality and performance:</span></span> 

1. <span data-ttu-id="21c4a-170"> *\*프로젝트 설정 편집 > 품질 >** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-170">Select **Edit > Project Settings > Quality**</span></span> 
2. <span data-ttu-id="21c4a-171"> *\*Windows 스토어** 로고 아래의 *\*드롭다운을**   선택하고 매우  *\*낮음 을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-171">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="21c4a-172">Windows 스토어 열의 상자와 매우 낮은 행이 녹색이면 설정이 올바르게 적용된 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-172">You'll know the setting is applied correctly when the box in the Windows Store column and Very Low row is green</span></span> 
3. <span data-ttu-id="21c4a-173"> *\*그림자** 섹션에서 그림자   사용 안 *\*함을 선택합니다.**</span><span class="sxs-lookup"><span data-stu-id="21c4a-173">In the **Shadows** section, select **Disable Shadows**</span></span> 

<span data-ttu-id="21c4a-174">![품질 설정 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="21c4a-174">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="21c4a-175">*Unity 품질 설정*</span><span class="sxs-lookup"><span data-stu-id="21c4a-175">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="21c4a-176">장면별 설정</span><span class="sxs-lookup"><span data-stu-id="21c4a-176">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="21c4a-177">Unity 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="21c4a-177">Unity camera settings</span></span>

<span data-ttu-id="21c4a-178">**Virtual Reality Supported를** 선택하면 [Unity 카메라](camera-in-unity.md) 구성 요소가 머리 추적 [및 스테레오 범위 렌더링을 처리합니다.](../platform-capabilities-and-apis/rendering.md)</span><span class="sxs-lookup"><span data-stu-id="21c4a-178">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="21c4a-179">즉, Main Camera 개체를 사용자 지정 카메라로 바꿀 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-179">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="21c4a-180">앱이 특히 HoloLens를 대상으로 하는 경우 디바이스의 투명 디스플레이에 최적화하기 위해 몇 가지 설정을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-180">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="21c4a-181">이러한 설정을 사용하면 홀로그램 콘텐츠를 실제 세계에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-181">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="21c4a-182">**계층** 구조에서 **주 카메라를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-182">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="21c4a-183">**Inspector(검사기)** 패널에서 변환 **위치를** **0, 0, 0으로** 설정하여 사용자의 머리 위치가 Unity 세계 원본에서 시작되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-183">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="21c4a-184">**플래그 지우기를** **단색으로 변경합니다.**</span><span class="sxs-lookup"><span data-stu-id="21c4a-184">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="21c4a-185">**배경색을** **RGBA 0,0,0,0으로 변경합니다.**</span><span class="sxs-lookup"><span data-stu-id="21c4a-185">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="21c4a-186">HoloLens에서 검은색이 투명하게 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-186">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="21c4a-187">**클리핑 평면** 변경 - [HoloLens 권장](camera-in-unity.md#using-clipping-planes) 0.85(미터) 근처에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-187">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#using-clipping-planes) 0.85 (meters).</span></span>

<span data-ttu-id="21c4a-188">![Unity 편집기에서 열린 검사기 탭의 스크린샷](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="21c4a-188">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="21c4a-189">*Unity 카메라 설정*</span><span class="sxs-lookup"><span data-stu-id="21c4a-189">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21c4a-190">새 카메라를 삭제하고 만드는 경우 새 카메라에 **MainCamera** 태그가 지정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-190">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="21c4a-191">다음 단계</span><span class="sxs-lookup"><span data-stu-id="21c4a-191">Next steps</span></span>

<span data-ttu-id="21c4a-192">이제 프로젝트가 준비되면 Mixed Reality 환경 개발을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21c4a-192">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="21c4a-193">[핵심 구성 요소](unity-development-overview.md#2-core-building-blocks) 추가</span><span class="sxs-lookup"><span data-stu-id="21c4a-193">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="21c4a-194">사용 가능한 [플랫폼 기능 및 API](unity-development-overview.md#3-advanced-features) 확인</span><span class="sxs-lookup"><span data-stu-id="21c4a-194">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="21c4a-195">[앱을 배포하는](../platform-capabilities-and-apis/using-visual-studio.md#) 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="21c4a-195">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="21c4a-196">Mixed Reality [시뮬레이터](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 사용</span><span class="sxs-lookup"><span data-stu-id="21c4a-196">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="21c4a-197">참고 항목</span><span class="sxs-lookup"><span data-stu-id="21c4a-197">See also</span></span>
* [<span data-ttu-id="21c4a-198">도구 설치</span><span class="sxs-lookup"><span data-stu-id="21c4a-198">Install the tools</span></span>](../install-the-tools.md)