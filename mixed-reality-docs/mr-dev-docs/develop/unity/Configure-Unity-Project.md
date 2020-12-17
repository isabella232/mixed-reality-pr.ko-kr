---
title: MRTK를 사용 하지 않고 프로젝트 구성
description: Windows Mixed Reality 용 Unity 프로젝트를 구성 하는 방법에 대 한 지침
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, mixed reality, 개발, 시작, 새 프로젝트, Windows Mixed Reality, UWP, XR, 성능
ms.openlocfilehash: 1337001e8cc5c280c5789acbc8f10f40bca9b763
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613392"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="c2c32-104">MRTK를 사용 하지 않고 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="c2c32-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="c2c32-105">Windows Mixed Reality (WMR)는 Windows 10 운영 체제의 일부로 도입 된 Microsoft 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="c2c32-106">WMR 플랫폼을 사용 하면 holographic 및 VR 디스플레이 장치에서 디지털 콘텐츠를 렌더링 하는 응용 프로그램을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="c2c32-107">Microsoft 및 커뮤니티에서는 WMR 환경을 자동으로 설정 하는 [mrtk (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 와 같은 활용 도구를 만들었으므로 많은 개발자 들이 처음부터 환경을 구축 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="c2c32-108">다음 설명서에서는 MRTK를 사용 하는지 여부에 관계 없이 혼합 현실 개발용으로 프로젝트를 올바르게 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="c2c32-109">변경 해야 하는 설정은 프로젝트 당 설정 및 장면 별 설정의 두 가지 범주로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="c2c32-110">나중에 언제 든 지 MRTK를 가져올 수 있으므로 수동 경로를 먼저 이동 하는 데는 아무런 영향이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="c2c32-111">WMR 수동 설치를 선택 하는 경우 변경 해야 하는 설정은 프로젝트별 및 장면의 두 가지 범주로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="c2c32-112">프로젝트별 설정</span><span class="sxs-lookup"><span data-stu-id="c2c32-112">Per-project settings</span></span>

<span data-ttu-id="c2c32-113">데스크톱 VR를 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택 된 PC 독립 실행형 플랫폼을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![PC, Mac & 독립 실행형 플랫폼이 강조 표시 된 unity 편집기에서 열리는 빌드 설정 창의 스크린샷](images/wmr-config-img-3.png)

<span data-ttu-id="c2c32-115">HoloLens 2를 대상으로 하는 경우 유니버설 Windows 플랫폼로 전환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="c2c32-116">**파일 > 빌드 설정** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="c2c32-117">플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="c2c32-118">**아키텍처** 를 **ARM 64** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="c2c32-119">**대상 장치** 를 **HoloLens** 로 설정</span><span class="sxs-lookup"><span data-stu-id="c2c32-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="c2c32-120">**빌드 유형을** **D3D** 로 설정</span><span class="sxs-lookup"><span data-stu-id="c2c32-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="c2c32-121">**UWP SDK** 를 **최신 설치** 로 설정</span><span class="sxs-lookup"><span data-stu-id="c2c32-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="c2c32-122">디버그에 알려진 성능 문제가 있으므로 **빌드 구성을** **릴리스로** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![유니버설 Windows 플랫폼 강조 표시 된 unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-4.png)

<span data-ttu-id="c2c32-124">플랫폼을 설정한 후에는 내보낼 때 Unity에서 2D 보기 대신 [몰입 형 보기](../../design/app-views.md) 를 만들도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="c2c32-125">XRSDK의 경우</span><span class="sxs-lookup"><span data-stu-id="c2c32-125">For XRSDK</span></span> 

1. <span data-ttu-id="c2c32-126">Unity 편집기에서 **편집 > 프로젝트 설정** 으로 이동 하 고 **XR 플러그 인 관리** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="c2c32-127">**XR 플러그 인 관리 설치** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-127">Select **Install XR Plugin Management**</span></span>

![XR 플러그 인 관리가 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-5.png)

3. <span data-ttu-id="c2c32-129">시작 및 **Windows Mixed Reality** **에서 XR 초기화를** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![XR 플러그 인 관리가 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-7.png)

4. <span data-ttu-id="c2c32-131">**XR 플러그 인 관리** 섹션을 확장 하 고 **Windows Mixed Reality** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-131">Expand the **XR Plug-in Management** section and select **Windows Mixed Reality**</span></span>
5. <span data-ttu-id="c2c32-132">모든 상자를 선택 하 고 **깊이 전송 모드** 를 **깊이 16 비트로** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-132">Check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Windows Mixed Reality 섹션이 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="c2c32-134">레거시 XR의 경우</span><span class="sxs-lookup"><span data-stu-id="c2c32-134">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="c2c32-135">레거시 XR는 Unity 2019에서 더 이상 사용 되지 않으며 Unity 2020에서 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-135">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="c2c32-136">빌드 설정에서 **플레이어 설정** ...을 엽니다. \*\*\*\* **XR 설정** 그룹을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-136">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="c2c32-137">**XR 설정** 섹션에서 가상 현실 **지원 됨** 을 선택 하 여 가상 현실 장치 목록을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-137">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="c2c32-138">**깊이 형식을** **16 비트 깊이로** 설정 하 고 **깊이 버퍼 공유** 를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-138">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="c2c32-139">**단일 패스 인스턴스로** **스테레오 렌더링 모드** 설정</span><span class="sxs-lookup"><span data-stu-id="c2c32-139">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="c2c32-140">Holographic 원격 기능을 사용 하려는 경우에는 **WSA Holographic Remoting 지원** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-140">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![플레이어 설정 섹션이 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="c2c32-142">매니페스트를 업데이트 하는 중</span><span class="sxs-lookup"><span data-stu-id="c2c32-142">Updating the manifest</span></span>

<span data-ttu-id="c2c32-143">이제 앱이 holographic 렌더링 및 공간 입력을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-143">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="c2c32-144">그러나 특정 기능을 활용 하려면 앱이 해당 매니페스트에 적절 한 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-144">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="c2c32-145">**플레이어 설정 > 설정 유니버설 Windows 플랫폼 > 게시 설정 > 기능** 으로 이동 하 여 프로젝트 기능을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-145">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="c2c32-146">내보낸 이후 모든 프로젝트에 포함 하기 위해 Unity에서 매니페스트 선언을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-146">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="c2c32-147">혼합 현실에 일반적으로 사용 되는 Unity Api를 사용 하는 데 적용 되는 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-147">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="c2c32-148">기능</span><span class="sxs-lookup"><span data-stu-id="c2c32-148">Capability</span></span>  |  <span data-ttu-id="c2c32-149">기능을 필요로 하는 Api</span><span class="sxs-lookup"><span data-stu-id="c2c32-149">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="c2c32-150">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="c2c32-150">SpatialPerception</span></span>  |  <span data-ttu-id="c2c32-151">SurfaceObserver (HoloLens의 [공간 매핑](../../design/spatial-mapping.md) 메시에 대 한 액세스) &mdash; *헤드셋의 일반 공간 추적에 필요한 기능이 없습니다* .</span><span class="sxs-lookup"><span data-stu-id="c2c32-151">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="c2c32-152">웹캠</span><span class="sxs-lookup"><span data-stu-id="c2c32-152">WebCam</span></span>  |  <span data-ttu-id="c2c32-153">사진 캡처 및 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="c2c32-153">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="c2c32-154">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="c2c32-154">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="c2c32-155">각각 사진 캡처 또는 VideoCapture (캡처된 콘텐츠를 저장 하는 경우)</span><span class="sxs-lookup"><span data-stu-id="c2c32-155">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="c2c32-156">마이크</span><span class="sxs-lookup"><span data-stu-id="c2c32-156">Microphone</span></span>  |  <span data-ttu-id="c2c32-157">VideoCapture (오디오 캡처 시), DictationRecognizer, GrammarRecognizer 및 KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="c2c32-157">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="c2c32-158">InternetClient</span><span class="sxs-lookup"><span data-stu-id="c2c32-158">InternetClient</span></span>  |  <span data-ttu-id="c2c32-159">DictationRecognizer (및 Unity 프로파일러를 사용 하려면)</span><span class="sxs-lookup"><span data-stu-id="c2c32-159">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="c2c32-160">품질 설정</span><span class="sxs-lookup"><span data-stu-id="c2c32-160">Quality settings</span></span>

<span data-ttu-id="c2c32-161">HoloLens에는 모바일 클래스 GPU가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-161">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="c2c32-162">앱이 HoloLens를 대상으로 하는 경우 앱의 품질 설정이 전체 프레임 속도를 유지 하기 위해 가장 빠른 성능을 위해 조정 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-162">If your app is targeting HoloLens, you'll want the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate:</span></span>

1. <span data-ttu-id="c2c32-163">**편집 > 프로젝트 설정 > 품질** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-163">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="c2c32-164">**Windows 스토어** 로고 아래의 **드롭다운** 을 선택 하 고 **매우 낮음** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-164">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="c2c32-165">Windows 스토어 열의 상자와 **매우 낮은** 행이 녹색 인 경우 설정이 올바르게 적용 됨을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-165">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green</span></span>
3. <span data-ttu-id="c2c32-166">**그림자** 섹션에서 **그림자 사용 안 함** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-166">In the **Shadows** section, select **Disable Shadows**</span></span>

<span data-ttu-id="c2c32-167">![품질 설정 섹션이 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="c2c32-167">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="c2c32-168">*Unity 품질 설정*</span><span class="sxs-lookup"><span data-stu-id="c2c32-168">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="c2c32-169">장면 별 설정</span><span class="sxs-lookup"><span data-stu-id="c2c32-169">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="c2c32-170">Unity 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="c2c32-170">Unity camera settings</span></span>

<span data-ttu-id="c2c32-171">**가상 현실을 지원 됨** 을 선택 하면 [Unity 카메라](camera-in-unity.md) 구성 요소가 [헤드 추적 및 stereoscopic 렌더링](../platform-capabilities-and-apis/rendering.md)을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-171">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="c2c32-172">즉, 기본 카메라 개체를 사용자 지정 카메라로 바꿀 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-172">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="c2c32-173">앱이 특별히 HoloLens를 대상으로 하는 경우에는 장치의 투명 디스플레이를 최적화 하기 위해 몇 가지 설정을 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-173">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="c2c32-174">이러한 설정을 통해 holographic 콘텐츠를 실제 세계에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-174">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="c2c32-175">**계층** 에서 **기본 카메라** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-175">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="c2c32-176">**검사기** 패널에서 변환 **위치** 를 **0, 0, 0** 으로 설정 하 여 사용자의 헤드 위치가 Unity 세계 원점에서 시작 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-176">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="c2c32-177">**Clear 플래그** 를 **Solid 색** 으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-177">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="c2c32-178">**배경색** 을 **RGBA 0, 0**, 0, 0으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-178">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="c2c32-179">검은색은 HoloLens에서 투명 하 게 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-179">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="c2c32-180">**클립 평면** 을 [HoloLens 권장](camera-in-unity.md#clip-planes) 0.85 (미터) 근처로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-180">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="c2c32-181">![Unity 편집기에서 열리는 검사기 탭의 스크린샷](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="c2c32-181">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="c2c32-182">*Unity 카메라 설정*</span><span class="sxs-lookup"><span data-stu-id="c2c32-182">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c2c32-183">새 카메라를 삭제 하 고 만드는 경우 새 카메라에 **maincamera** 로 태그가 지정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-183">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c2c32-184">다음 단계</span><span class="sxs-lookup"><span data-stu-id="c2c32-184">Next steps</span></span>

<span data-ttu-id="c2c32-185">이제 프로젝트가 준비 되었으므로 혼합 현실 환경 개발을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c32-185">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="c2c32-186">[핵심 구성 요소](unity-development-overview.md#2-core-building-blocks) 추가</span><span class="sxs-lookup"><span data-stu-id="c2c32-186">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="c2c32-187">사용 가능한 [플랫폼 기능 및 api](unity-development-overview.md#3-platform-capabilities-and-apis) 확인</span><span class="sxs-lookup"><span data-stu-id="c2c32-187">Check out available [platform capabilities and APIs](unity-development-overview.md#3-platform-capabilities-and-apis)</span></span>
* <span data-ttu-id="c2c32-188">[앱을 배포](../platform-capabilities-and-apis/using-visual-studio.md#deploying-an-app-to-your-local-pc---immersive-headset) 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="c2c32-188">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#deploying-an-app-to-your-local-pc---immersive-headset)</span></span>
* <span data-ttu-id="c2c32-189">[혼합 현실 시뮬레이터](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 사용</span><span class="sxs-lookup"><span data-stu-id="c2c32-189">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="c2c32-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2c32-190">See also</span></span>
* [<span data-ttu-id="c2c32-191">도구 설치</span><span class="sxs-lookup"><span data-stu-id="c2c32-191">Install the tools</span></span>](../install-the-tools.md)