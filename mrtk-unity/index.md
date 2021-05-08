---
title: MRTK-Unity 개발자 설명서
description: Unity용 Mixed Reality Toolkit에 대해 알아보세요.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: cb8b95cf9e563e8a277fa0d4b253639a763f5ad5
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489303"
---
# <a name="what-is-the-mixed-reality-toolkit"></a><span data-ttu-id="51db2-104">Mixed Reality Toolkit이란 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="51db2-104">What is the Mixed Reality Toolkit</span></span>

![Mixed Reality Toolkit](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="51db2-106">MRTK-Unity는 Unity에서 플랫폼 간 MR 앱 개발을 가속화하는 데 사용되는 구성 요소 및 기능 집합을 제공하는 Microsoft 기반 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-106">MRTK-Unity is a Microsoft-driven project that provides a set of components and features, used to accelerate cross-platform MR app development in Unity.</span></span> <span data-ttu-id="51db2-107">일부 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-107">Here are some of its functions:</span></span>

* <span data-ttu-id="51db2-108">**공간 상호 작용 및 UI를 위한 플랫폼 간 입력 시스템 및 구성 요소** 를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-108">Provides the **cross-platform input system and building blocks for spatial interactions and UI**.</span></span>
* <span data-ttu-id="51db2-109">변경 내용을 즉시 볼 수 있는 편집기 내 시뮬레이션을 통해 **프로토타입을 신속하게 제작** 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-109">Enables **rapid prototyping** via in-editor simulation that allows you to see changes immediately.</span></span>
* <span data-ttu-id="51db2-110">**확장 가능한 프레임워크** 로서 작동해 개발자에게 핵심 구성 요소를 교환하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-110">Operates as an **extensible framework** that provides developers the ability to swap out core components.</span></span>
* <span data-ttu-id="51db2-111">**다양한 플랫폼을 지원합니다**.</span><span class="sxs-lookup"><span data-stu-id="51db2-111">**Supports a wide range of platforms**:</span></span>

| <span data-ttu-id="51db2-112">플랫폼</span><span class="sxs-lookup"><span data-stu-id="51db2-112">Platform</span></span> | <span data-ttu-id="51db2-113">지원되는 디바이스</span><span class="sxs-lookup"><span data-stu-id="51db2-113">Supported Devices</span></span> |
|---|---|
| <span data-ttu-id="51db2-114">OpenXR(Unity 2020.2 이상)</span><span class="sxs-lookup"><span data-stu-id="51db2-114">OpenXR (Unity 2020.2 or newer)</span></span> | <span data-ttu-id="51db2-115">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="51db2-115">Microsoft HoloLens 2</span></span> <br> <span data-ttu-id="51db2-116">Windows Mixed Reality 헤드셋</span><span class="sxs-lookup"><span data-stu-id="51db2-116">Windows Mixed Reality headsets</span></span> |
| <span data-ttu-id="51db2-117">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="51db2-117">Windows Mixed Reality</span></span> | <span data-ttu-id="51db2-118">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="51db2-118">Microsoft HoloLens</span></span> <br> <span data-ttu-id="51db2-119">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="51db2-119">Microsoft HoloLens 2</span></span> <br> <span data-ttu-id="51db2-120">Windows Mixed Reality 헤드셋</span><span class="sxs-lookup"><span data-stu-id="51db2-120">Windows Mixed Reality headsets</span></span>  |
| <span data-ttu-id="51db2-121">Oculus(Unity 2019.3 이상)</span><span class="sxs-lookup"><span data-stu-id="51db2-121">Oculus (Unity 2019.3 or newer)</span></span> | <span data-ttu-id="51db2-122">Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="51db2-122">Oculus Quest</span></span> |
| <span data-ttu-id="51db2-123">OpenVR</span><span class="sxs-lookup"><span data-stu-id="51db2-123">OpenVR</span></span> |  <span data-ttu-id="51db2-124">Windows Mixed Reality 헤드셋</span><span class="sxs-lookup"><span data-stu-id="51db2-124">Windows Mixed Reality headsets</span></span> <br> <span data-ttu-id="51db2-125">HTC Vive</span><span class="sxs-lookup"><span data-stu-id="51db2-125">HTC Vive</span></span> <br> <span data-ttu-id="51db2-126">Oculus Rift</span><span class="sxs-lookup"><span data-stu-id="51db2-126">Oculus Rift</span></span> |
| <span data-ttu-id="51db2-127">Ultraleap Hand Tracking</span><span class="sxs-lookup"><span data-stu-id="51db2-127">Ultraleap Hand Tracking</span></span> | <span data-ttu-id="51db2-128">Ultraleap Leap 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="51db2-128">Ultraleap Leap Motion controller</span></span> |
| <span data-ttu-id="51db2-129">모바일</span><span class="sxs-lookup"><span data-stu-id="51db2-129">Mobile</span></span> | <span data-ttu-id="51db2-130">iOS 및 Android</span><span class="sxs-lookup"><span data-stu-id="51db2-130">iOS and Android</span></span> |

## <a name="getting-started-with-mrtk"></a><span data-ttu-id="51db2-131">MRTK 시작</span><span class="sxs-lookup"><span data-stu-id="51db2-131">Getting started with MRTK</span></span>

<span data-ttu-id="51db2-132">Unity에서 MRTK 또는 Mixed Reality 개발을 처음 사용하는 경우 디바이스 또는 에뮬레이터에 MRTK 예제 허브 샘플 애플리케이션을 설치하고 탐색하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-132">If you're new to MRTK or Mixed Reality development in Unity, we recommend installing and exploring the MRTK Examples Hub sample application on your device or emulator.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="51db2-133">MRTK 예제 허브 앱 다운로드</span><span class="sxs-lookup"><span data-stu-id="51db2-133">Download the MRTK Examples Hub app</span></span>](running-examples-hub.md)

<span data-ttu-id="51db2-134">Mixed Reality 및 MRTK가 제공하는 기능을 파악했다면 필요한 도구를 설치하고 초급 HoloLens 2 자습서 시리즈를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-134">Once you've got the hang of what Mixed Reality and MRTK has to offer, install the necessary tools and follow our beginner level HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="51db2-135">도구 설치</span><span class="sxs-lookup"><span data-stu-id="51db2-135">Install the tools</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools?tabs=unity)

> [!div class="nextstepaction"]
> [<span data-ttu-id="51db2-136">HoloLens 2 자습서 시리즈</span><span class="sxs-lookup"><span data-stu-id="51db2-136">HoloLens 2 Tutorial Series</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

<span data-ttu-id="51db2-137">작동 원리를 자세히 알고 싶으신가요?</span><span class="sxs-lookup"><span data-stu-id="51db2-137">Want to see what's going on under the hood?</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="51db2-138">GitHub에서 MRTK 살펴보기</span><span class="sxs-lookup"><span data-stu-id="51db2-138">Explore MRTK on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a><span data-ttu-id="51db2-139">설명서</span><span class="sxs-lookup"><span data-stu-id="51db2-139">Documentation</span></span>

| <span data-ttu-id="51db2-140">[![릴리스 정보](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-140">[![Release notes](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span></span><br/>[<span data-ttu-id="51db2-141">릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="51db2-141">Release Notes</span></span>](release-notes/mrtk-26-release-notes.md)| <span data-ttu-id="51db2-142">[![MRTK 개요](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-142">[![MRTK Overview](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span></span><br/>[<span data-ttu-id="51db2-143">MRTK 개요</span><span class="sxs-lookup"><span data-stu-id="51db2-143">MRTK Overview</span></span>](architecture/overview.md)|<span data-ttu-id="51db2-144">[![API 참조](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span><span class="sxs-lookup"><span data-stu-id="51db2-144">[![API Reference](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span></span><br/>[<span data-ttu-id="51db2-145">API 참조</span><span class="sxs-lookup"><span data-stu-id="51db2-145">API Reference</span></span>](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a><span data-ttu-id="51db2-146">빌드 상태</span><span class="sxs-lookup"><span data-stu-id="51db2-146">Build status</span></span>

| <span data-ttu-id="51db2-147">Branch</span><span class="sxs-lookup"><span data-stu-id="51db2-147">Branch</span></span> | <span data-ttu-id="51db2-148">CI 상태</span><span class="sxs-lookup"><span data-stu-id="51db2-148">CI Status</span></span> | <span data-ttu-id="51db2-149">문서 상태</span><span class="sxs-lookup"><span data-stu-id="51db2-149">Docs Status</span></span> |
|---|---|---|
| `main` |<span data-ttu-id="51db2-150">[![CI 상태](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span><span class="sxs-lookup"><span data-stu-id="51db2-150">[![CI Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span></span>|<span data-ttu-id="51db2-151">[![문서 상태](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span><span class="sxs-lookup"><span data-stu-id="51db2-151">[![Docs Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span></span>

## <a name="feature-areas"></a><span data-ttu-id="51db2-152">기능 영역</span><span class="sxs-lookup"><span data-stu-id="51db2-152">Feature areas</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="51db2-153">[![입력 시스템](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-153">[![Input System](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="51db2-154">**[입력 시스템](features/input/overview.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-154">**[Input System](features/input/overview.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-155">[![손 추적(HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-155">[![Hand Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="51db2-156">**[손 추적 <br> (HoloLens 2)](features/input/hand-tracking.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-156">**[Hand Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-157">[![시선 추적(HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-157">[![Eye Tracking (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span></span><br>
        <span data-ttu-id="51db2-158">**[시선 추적 <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-158">**[Eye Tracking <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-159">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-159">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span></span><br>
        <span data-ttu-id="51db2-160">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-160">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="51db2-161">[![손 추적(Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-161">[![Hand Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span></span><br>
        <span data-ttu-id="51db2-162">**[손 추적 <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-162">**[Hand Tracking <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-163">[![UI 컨트롤](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="51db2-163">[![UI Controls](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span></span><br>
        <span data-ttu-id="51db2-164">**[UI 컨트롤](#ux-building-blocks)**</span><span class="sxs-lookup"><span data-stu-id="51db2-164">**[UI Controls](#ux-building-blocks)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-165">[![해결기](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-165">[![Solvers](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span></span><br>
        <span data-ttu-id="51db2-166">**[해결기](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-166">**[Solvers](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-167">[![다중 장면 관리자](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-167">[![Multi-Scene Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="51db2-168">**[다중 장면<br/> 관리자](features/scene-system/scene-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-168">**[Multi-Scene<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="51db2-169">[![공간 인식](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-169">[![Spatial Awareness](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span></span><br>
        <span data-ttu-id="51db2-170">**[공간<br/> 인식](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-170">**[Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-171">[![진단 도구](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-171">[![Diagnostic Tool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="51db2-172">**[진단 <br/> 도구](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-172">**[Diagnostic <br/> Tool](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-173">[![MRTK 표준 셰이더 보기](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span><span class="sxs-lookup"><span data-stu-id="51db2-173">[![MRTK Standard Shader View](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span></span><br>
        <span data-ttu-id="51db2-174">**[MRTK 표준 셰이더 예제 보기](features/rendering/mrtk-standard-shader.md?q=shader)**</span><span class="sxs-lookup"><span data-stu-id="51db2-174">**[MRTK Standard Shader Example View](features/rendering/mrtk-standard-shader.md?q=shader)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-175">[![음성 및 받아쓰기](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-175">[![Speech & Dictation](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="51db2-176">**[음성](features/input/speech.md)<br/> & [받아쓰기](features/input/dictation.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-176">**[Speech](features/input/speech.md)<br/> & [Dictation](features/input/dictation.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="51db2-177">[![경계 시스템](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-177">[![Boundary System](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span></span><br>
        <span data-ttu-id="51db2-178">**[경계 <br/>시스템](features/boundary/boundary-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-178">**[Boundary <br/>System](features/boundary/boundary-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-179">[![편집기 내 시뮬레이션](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-179">[![In-Editor Simulation](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="51db2-180">**[편집기 내 <br/> 시뮬레이션](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-180">**[In-Editor <br/> Simulation](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-181">[![실험적 기능](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-181">[![Experimental Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span></span><br>
        <span data-ttu-id="51db2-182">**[실험적<br/> 기능](contributing/experimental-features.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-182">**[Experimental <br/> Features](contributing/experimental-features.md)**</span></span><br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a><span data-ttu-id="51db2-183">UX 구성 요소</span><span class="sxs-lookup"><span data-stu-id="51db2-183">UX building blocks</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="51db2-184">[![단추](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[단추](features/ux-building-blocks/button.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-184">[![Button](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Button](features/ux-building-blocks/button.md)**</span></span><br>
        <span data-ttu-id="51db2-185">HoloLens 2의 연결된 손을 포함한 다양한 입력 방법을 지원하는 단추 컨트롤</span><span class="sxs-lookup"><span data-stu-id="51db2-185">A button control which supports various input methods, including HoloLens 2's articulated hand</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-186">[![경계 컨트롤](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[경계 컨트롤](features/ux-building-blocks/bounds-control.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-186">[![Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds Control](features/ux-building-blocks/bounds-control.md)**</span></span><br>
        <span data-ttu-id="51db2-187">3D 공간에서 개체 조작을 위한 표준 UI</span><span class="sxs-lookup"><span data-stu-id="51db2-187">Standard UI for manipulating objects in 3D space</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-188">[![개체 조작자](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[개체 조작자](features/ux-building-blocks/object-manipulator.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-188">[![Object Manipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Object Manipulator](features/ux-building-blocks/object-manipulator.md)**</span></span><br>
        <span data-ttu-id="51db2-189">한 손 또는 양손을 사용하여 개체를 조작하기 위한 스크립트</span><span class="sxs-lookup"><span data-stu-id="51db2-189">Script for manipulating objects with one or two hands</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="51db2-190">[![슬레이트](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[슬레이트](features/ux-building-blocks/slate.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-190">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span></span><br>
        <span data-ttu-id="51db2-191">연결된 손 입력을 사용한 스크롤을 지원하는 2D 스타일 평면</span><span class="sxs-lookup"><span data-stu-id="51db2-191">2D style plane which supports scrolling with articulated hand input</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-192">[![시스템 키보드](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[시스템 키보드](features/ux-building-blocks/system-keyboard.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-192">[![System Keyboard](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[System Keyboard](features/ux-building-blocks/system-keyboard.md)**</span></span><br>
        <span data-ttu-id="51db2-193">Unity에서 시스템 키보드를 사용하는 예제 스크립트</span><span class="sxs-lookup"><span data-stu-id="51db2-193">Example script of using the system keyboard in Unity</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-194">[![상호 작용 가능](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[상호 작용 가능](features/ux-building-blocks/interactable.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-194">[![Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**</span></span><br>
        <span data-ttu-id="51db2-195">시각적 상태 및 테마 지원으로 개체를 상호 작용 가능하게 만드는 스크립트</span><span class="sxs-lookup"><span data-stu-id="51db2-195">A script for making objects interactable with visual states and theme support</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="51db2-196">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-196">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
        <span data-ttu-id="51db2-197">태그 동반, 신체 고정, 일정한 뷰 크기 및 표면 자성과 같은 다양한 개체 위치 지정 동작</span><span class="sxs-lookup"><span data-stu-id="51db2-197">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-198">[![개체 컬렉션](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[개체 컬렉션](features/ux-building-blocks/object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-198">[![Object Collection](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Object Collection](features/ux-building-blocks/object-collection.md)**</span></span><br>
        <span data-ttu-id="51db2-199">3차원 모양의 개체 배열을 배치하는 스크립트</span><span class="sxs-lookup"><span data-stu-id="51db2-199">Script for laying out an array of objects in a three-dimensional shape</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-200">[![도구 설명](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[도구 설명](features/ux-building-blocks/tooltip.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-200">[![Tooltip](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Tooltip](features/ux-building-blocks/tooltip.md)**</span></span><br>
        <span data-ttu-id="51db2-201">모션 컨트롤러 및 개체에 레이블을 지정하는 데 사용할 수 있는 유연한 앵커/피벗 시스템을 포함하는 주석 UI</span><span class="sxs-lookup"><span data-stu-id="51db2-201">Annotation UI with a flexible anchor/pivot system, which can be used for labeling motion controllers and objects</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="51db2-202">[![슬라이더](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[슬라이더](features/ux-building-blocks/sliders.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-202">[![Slider](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Slider](features/ux-building-blocks/sliders.md)**</span></span><br>
        <span data-ttu-id="51db2-203">직접 손 추적 상호 작용을 지원하는 값 조정을 위한 슬라이더 UI</span><span class="sxs-lookup"><span data-stu-id="51db2-203">Slider UI for adjusting values supporting direct hand tracking interaction</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-204">[![MRTK 표준 셰이더](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK 표준 셰이더](features/rendering/mrtk-standard-shader.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-204">[![MRTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**</span></span><br>
        <span data-ttu-id="51db2-205">MRTK의 표준 셰이더는 성능으로 다양한 Fluent Design 요소를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-205">MRTK's Standard shader supports various Fluent design elements with performance</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-206">[![손 메뉴](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[손 메뉴](features/ux-building-blocks/hand-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-206">[![Hand Menu](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Hand Menu](features/ux-building-blocks/hand-menu.md)**</span></span><br>
        <span data-ttu-id="51db2-207">손 제약 조건 해결기를 사용하는 빠른 액세스용 손 잠금 UI</span><span class="sxs-lookup"><span data-stu-id="51db2-207">Hand-locked UI for quick access, using the Hand Constraint Solver</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="51db2-208">[![앱 바](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[앱 바](features/ux-building-blocks/app-bar.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-208">[![App Bar](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App Bar](features/ux-building-blocks/app-bar.md)**</span></span><br>
        <span data-ttu-id="51db2-209">경계 컨트롤의 수동 활성화를 위한 UI</span><span class="sxs-lookup"><span data-stu-id="51db2-209">UI for Bounds Control's manual activation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-210">[![포인터](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[포인터](features/input/pointers.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-210">[![Pointers](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointers](features/input/pointers.md)**</span></span><br>
        <span data-ttu-id="51db2-211">다양한 종류의 포인터에 대해 알아보기</span><span class="sxs-lookup"><span data-stu-id="51db2-211">Learn about various types of pointers</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-212">[![손끝 시각화](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[손끝 시각화](features/ux-building-blocks/fingertip-visualization.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-212">[![Fingertip Visualization](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip Visualization](features/ux-building-blocks/fingertip-visualization.md)**</span></span><br>
        <span data-ttu-id="51db2-213">직접 상호 작용에 대한 신뢰도를 향상시키는 손끝의 시각적 어포던스</span><span class="sxs-lookup"><span data-stu-id="51db2-213">Visual affordance on the fingertip which improves the confidence for the direct interaction</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="51db2-214">[![Near 메뉴](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near 메뉴](features/ux-building-blocks/near-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-214">[![Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near Menu](features/ux-building-blocks/near-menu.md)**</span></span><br>
        <span data-ttu-id="51db2-215">근거리 상호 작용을 위한 부동 메뉴 UI</span><span class="sxs-lookup"><span data-stu-id="51db2-215">Floating menu UI for the near interactions</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-216">[![공간 인식 시작](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[공간 인식 보기](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-216">[![Spatial Awareness Getting started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial Awareness View](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
        <span data-ttu-id="51db2-217">홀로그램 개체가 물리적 환경과 상호 작용하게 만들기</span><span class="sxs-lookup"><span data-stu-id="51db2-217">Make your holographic objects interact with the physical environments</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-218">[![음성 명령](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[음성 명령](features/input/speech.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-218">[![Voice Command](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Voice Command](features/input/speech.md)**</span></span><br>
        <span data-ttu-id="51db2-219">음성 입력 통합을 위한 스크립트 및 예제</span><span class="sxs-lookup"><span data-stu-id="51db2-219">Scripts and examples for integrating speech input</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="51db2-220">[![진행률 표시기](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[진행률 표시기](features/ux-building-blocks/progress-indicator.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-220">[![Progress Indicator](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Progress Indicator](features/ux-building-blocks/progress-indicator.md)**</span></span><br>
        <span data-ttu-id="51db2-221">데이터 프로세스 또는 작업을 알려주기 위한 시각적 표시기</span><span class="sxs-lookup"><span data-stu-id="51db2-221">Visual indicator for communicating data process or operation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-222">[![대화 상자](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[대화 상자](features/ux-building-blocks/dialog.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-222">[![Dialog](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialog](features/ux-building-blocks/dialog.md)**</span></span><br>
        <span data-ttu-id="51db2-223">사용자의 확인 또는 승인을 요청하는 UI</span><span class="sxs-lookup"><span data-stu-id="51db2-223">UI for asking for user's confirmation or acknowledgement</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-224">[![손 코치](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[손 코치](features/ux-building-blocks/hand-coach.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-224">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span></span><br>
        <span data-ttu-id="51db2-225">제스처가 학습되지 않은 경우 사용자 안내를 지원하는 구성 요소</span><span class="sxs-lookup"><span data-stu-id="51db2-225">Component that helps guide the user when the gesture has not been taught</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="51db2-226">[![직접 물리학 서비스](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[직접 물리학 서비스 [실험용]](features/experimental/hand-physics-service.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-226">[![Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Hand Physics Service [Experimental]](features/experimental/hand-physics-service.md)**</span></span><br>
        <span data-ttu-id="51db2-227">직접 물리학 서비스는 강체 충돌 이벤트 및 연결된 손과의 상호 작용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-227">The hand physics service enables rigid body collision events and interactions with articulated hands</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-228">[![스크롤 컬렉션](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[스크롤 컬렉션](features/ux-building-blocks/scrolling-object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-228">[![Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling Collection](features/ux-building-blocks/scrolling-object-collection.md)**</span></span><br>
        <span data-ttu-id="51db2-229">3D 개체를 기본적으로 스크롤하는 개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="51db2-229">An Object Collection that natively scrolls 3D objects</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-230">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [실험용]](features/experimental/dock.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-230">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimental]](features/experimental/dock.md)**</span></span><br>
        <span data-ttu-id="51db2-231">Dock를 사용하면 미리 결정된 위치 안팎으로 개체를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-231">The Dock allows objects to be moved in and out of predetermined positions</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="51db2-232">[![시선 추적: 대상 선택](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[시선 추적: 대상 선택](features/input/eye-tracking/eye-tracking-target-selection.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-232">[![Eye Tracking: Target Selection](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eye Tracking: Target Selection](features/input/eye-tracking/eye-tracking-target-selection.md)**</span></span><br>
        <span data-ttu-id="51db2-233">시선, 음성 및 손 입력을 결합하여 장면 전체의 홀로그램을 빠르고 간편하게 선택</span><span class="sxs-lookup"><span data-stu-id="51db2-233">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-234">[![시선 추적: 탐색](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[시선 추적: 탐색](features/input/eye-tracking/eye-tracking-navigation.md)**</span><span class="sxs-lookup"><span data-stu-id="51db2-234">[![Eye Tracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eye Tracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span></span><br>
        <span data-ttu-id="51db2-235">표시되는 내용에 따라 텍스트를 자동으로 스크롤하거나 포커스가 있는 콘텐츠를 확대하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="51db2-235">Learn how to auto-scroll text or fluently zoom into focused content based on what you are looking at</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="51db2-236">[![시선 추적: 열 지도](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[시선 추적: 열 지도](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span><span class="sxs-lookup"><span data-stu-id="51db2-236">[![Eye Tracking: Heat Map](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eye Tracking: Heat Map](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span></span><br>
        <span data-ttu-id="51db2-237">사용자가 앱에서 본 내용을 로깅, 로드 및 시각화하는 예제</span><span class="sxs-lookup"><span data-stu-id="51db2-237">Examples for logging, loading and visualizing what users have been looking at in your app</span></span>
    :::column-end:::
:::row-end:::

## <a name="tools"></a><span data-ttu-id="51db2-238">도구</span><span class="sxs-lookup"><span data-stu-id="51db2-238">Tools</span></span>

|  <span data-ttu-id="51db2-239">[![최적화 창](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [최적화 창](features/tools/optimize-window.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-239">[![Optimize Window](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimize Window](features/tools/optimize-window.md)</span></span> | <span data-ttu-id="51db2-240">[![종속성 창](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [종속성 창](features/tools/dependency-window.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-240">[![Dependency Window](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Dependency Window](features/tools/dependency-window.md)</span></span> | ![빌드 창](features/images/MRTK_Icon_BuildWindow.png) <span data-ttu-id="51db2-242">빌드 창</span><span class="sxs-lookup"><span data-stu-id="51db2-242">Build Window</span></span> | <span data-ttu-id="51db2-243">[![입력 기록](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [입력 기록](features/input-simulation/input-animation-recording.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-243">[![Input recording](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Input recording](features/input-simulation/input-animation-recording.md)</span></span> |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="51db2-244">성능 최적화를 위해 Mixed Reality 프로젝트의 구성 자동화</span><span class="sxs-lookup"><span data-stu-id="51db2-244">Automate configuration of Mixed Reality projects for performance optimizations</span></span> | <span data-ttu-id="51db2-245">자산 간 종속성 분석 및 사용되지 않는 자산 식별</span><span class="sxs-lookup"><span data-stu-id="51db2-245">Analyze dependencies between assets and identify unused assets</span></span> |  <span data-ttu-id="51db2-246">Mixed Reality 애플리케이션을 위한 엔드투엔드 빌드 프로세스 구성 및 실행</span><span class="sxs-lookup"><span data-stu-id="51db2-246">Configure and execute an end-to-end build process for Mixed Reality applications</span></span> | <span data-ttu-id="51db2-247">편집기에서 머리 이동 및 손 추적 데이터 기록 및 재생</span><span class="sxs-lookup"><span data-stu-id="51db2-247">Record and playback head movement and hand tracking data in editor</span></span> |

## <a name="example-scenes"></a><span data-ttu-id="51db2-248">예제 장면</span><span class="sxs-lookup"><span data-stu-id="51db2-248">Example scenes</span></span>

<span data-ttu-id="51db2-249">[이 예제 장면](features/example-scenes/hand-interaction-examples.md)에서 MRTK의 다양한 상호 작용 유형과 UI 컨트롤을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-249">Explore MRTK's various types of interactions and UI controls in [this example scene](features/example-scenes/hand-interaction-examples.md).</span></span>

<span data-ttu-id="51db2-250">[![예제 장면 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-250">[![Example Scene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="mrtk-examples-hub"></a><span data-ttu-id="51db2-251">MRTK 예제 허브</span><span class="sxs-lookup"><span data-stu-id="51db2-251">MRTK examples hub</span></span>

<span data-ttu-id="51db2-252">MRTK 예제 허브를 사용하여 MRTK에서 다양한 예제 장면을 사용해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-252">With the MRTK Examples Hub, you can try various example scenes in MRTK.</span></span>
<span data-ttu-id="51db2-253">[MR Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)에서 "Mixed Reality Toolkit 예제" 패키지를 선택하여 HoloLens(x86), HoloLens 2(ARM) 및 Windows Mixed Reality 몰입형 헤드셋(x64)용으로 미리 작성된 앱 패키지를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-253">You can download pre-built app packages for HoloLens(x86), HoloLens 2(ARM), and Windows Mixed Reality immersive headsets(x64) by selecting the "Mixed Reality Toolkit Examples" package in the [MR Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span></span> <span data-ttu-id="51db2-254">[Windows 장치 포털을 사용하여 HoloLens(1세대)에 앱을 설치](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-254">Make sure to [use the Windows Device Portal to install apps on HoloLens (1st gen)](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span></span> <span data-ttu-id="51db2-255">HoloLens 2에서 [Microsoft Store 앱을 통해 MRTK 예제 허브](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4)를 다운로드하고 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-255">On HoloLens 2, you can download and install [MRTK Examples Hub through the Microsoft Store app](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span></span>

<span data-ttu-id="51db2-256">MRTK의 장면 시스템과 장면 전환 서비스를 사용하여 다중 장면 허브를 만드는 방법에 대한 자세한 내용은 [예제 허브 추가 정보 페이지](features/example-scenes/example-hub.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-256">See [Examples Hub README page](features/example-scenes/example-hub.md) to learn about the details on creating a multi-scene hub with MRTK's scene system and scene transition service.</span></span>

<span data-ttu-id="51db2-257">[![예제 장면 허브](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="51db2-257">[![Example Scene Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="sample-apps-made-with-mrtk"></a><span data-ttu-id="51db2-258">MRTK를 사용하여 만든 샘플 앱</span><span class="sxs-lookup"><span data-stu-id="51db2-258">Sample apps made with MRTK</span></span>

| <span data-ttu-id="51db2-259">[![원소의 주기율표](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="51db2-259">[![Periodic Table of the Elements](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span>| <span data-ttu-id="51db2-260">[![갤럭시 익스플로러](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="51db2-260">[![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span></span>| <span data-ttu-id="51db2-261">[![Surfaces 샘플 앱](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span><span class="sxs-lookup"><span data-stu-id="51db2-261">[![Surfaces sample app](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="51db2-262">[원소의 주기율표](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)는 MRTK의 입력 시스템 및 구성 요소를 사용하여 HoloLens 및 몰입형 헤드셋을 위한 앱 환경을 만드는 방법을 보여주는 오픈 소스 샘플 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-262">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) is an open-source sample app which demonstrates how to use MRTK's input system and building blocks to create an app experience for HoloLens and Immersive headsets.</span></span> <span data-ttu-id="51db2-263">포팅 사례 읽기: [MRTK v2를 사용하는 HoloLens 2에 원소의 주기율표 앱 가져오기](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="51db2-263">Read the porting story: [Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span> |<span data-ttu-id="51db2-264">[갤럭시 익스플로러](https://github.com/Microsoft/GalaxyExplorer)는 HoloLens '아이디어 공유' 캠페인의 일환으로 2016년 3월에 처음 개발된 오픈 소스 샘플 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-264">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app that was originally developed in March 2016 as part of the HoloLens 'Share Your Idea' campaign.</span></span> <span data-ttu-id="51db2-265">갤럭시 익스플로러는 MRTK v2를 사용하는 HoloLens 2를 위한 새 기능으로 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-265">Galaxy Explorer has been updated with new features for HoloLens 2, using MRTK v2.</span></span> <span data-ttu-id="51db2-266">사례 읽기: [HoloLens 2용 갤럭시 익스플로러 제작](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="51db2-266">Read the story: [The Making of Galaxy Explorer for HoloLens 2](/windows/mixed-reality/galaxy-explorer-update)</span></span> |<span data-ttu-id="51db2-267">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)는 HoloLens 2용 오픈 소스 샘플 앱으로, 시각적 개체, 오디오, 완전히 연결된 손 추적으로 촉감을 만드는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-267">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) is an open-source sample app for HoloLens 2 which explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span> <span data-ttu-id="51db2-268">자세한 디자인 및 개발 사례는 Microsoft 혼합 현실 개발자의 날 세션 [Surfaces 앱을 통한 학습](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-268">Check out Microsoft MR Dev Days session [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) for the detailed design and development story.</span></span> |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a><span data-ttu-id="51db2-269">2020 혼합 현실 개발자의 날의 세션 동영상</span><span class="sxs-lookup"><span data-stu-id="51db2-269">Session videos from Mixed Reality Dev Days 2020</span></span>

| <span data-ttu-id="51db2-270">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="51db2-270">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>| <span data-ttu-id="51db2-271">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span><span class="sxs-lookup"><span data-stu-id="51db2-271">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>| <span data-ttu-id="51db2-272">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span><span class="sxs-lookup"><span data-stu-id="51db2-272">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="51db2-273">간단한 MRTK 앱을 만드는 방법을 처음부터 끝까지 설명하는 자습서입니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-273">Tutorial on how to create a simple MRTK app from start to finish.</span></span> <span data-ttu-id="51db2-274">상호 작용 개념 및 MRTK의 다중 플랫폼 기능에 대해 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-274">Learn about interaction concepts and MRTK’s multi-platform capabilities.</span></span> | <span data-ttu-id="51db2-275">멋진 혼합 현실 환경을 빌드하는 데 도움이 되는 MRTK의 UX 구성 요소에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-275">Deep dive on the MRTK’s UX building blocks that help you build beautiful mixed reality experiences.</span></span> | <span data-ttu-id="51db2-276">MRTK 및 외부의 성능 도구에 대한 소개와 MRTK 표준 셰이더에 대한 개요입니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-276">An introduction to performance tools, both in MRTK and external, as well as an overview of the MRTK Standard Shader.</span></span> |

<span data-ttu-id="51db2-277">더 많은 세션 동영상을 살펴보려면 [혼합 현실 개발자의 날](/windows/mixed-reality/mr-dev-days-sessions)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-277">See [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) to explore more session videos.</span></span>

## <a name="engage-with-the-community"></a><span data-ttu-id="51db2-278">커뮤니티에 참여</span><span class="sxs-lookup"><span data-stu-id="51db2-278">Engage with the community</span></span>

* <span data-ttu-id="51db2-279">[Slack](https://holodevelopers.slack.com/)에서 MRTK에 대한 대화에 참여하세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-279">Join the conversation around MRTK on [Slack](https://holodevelopers.slack.com/).</span></span> <span data-ttu-id="51db2-280">[자동 초대 발신자](https://holodevelopersslack.azurewebsites.net/)를 통해 Slack 커뮤니티에 가입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-280">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

* <span data-ttu-id="51db2-281">**MRTK** 태그를 사용하여 [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk)에서 MRTK를 사용하는 방법에 관해 질문하세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-281">Ask questions about using MRTK on [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) using the **MRTK** tag.</span></span>

* <span data-ttu-id="51db2-282">MRTK 코드에서 문제가 발생한 경우 [알려진 문제](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)를 검색하거나 [새 문제](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)를 제기합니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-282">Search for [known issues](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) or file a [new issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) if you find something broken in MRTK code.</span></span>

* <span data-ttu-id="51db2-283">MRTK에 기여하는 방법에 대한 질문이 있는 경우 Slack의 [혼합 현실 도구 키트](https://holodevelopers.slack.com/messages/C2H4HT858) 채널로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-283">For questions about contributing to MRTK, go to the [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) channel on slack.</span></span>

<span data-ttu-id="51db2-284">이 프로젝트는 [Microsoft 오픈 소스 준수 사항](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-284">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="51db2-285">자세한 내용은 [준수 사항 FAQ](https://opensource.microsoft.com/codeofconduct/faq/)를 참조하고, 추가 질문이나 의견이 있는 경우에는 [opencode@microsoft.com](mailto:opencode@microsoft.com)으로 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-285">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a><span data-ttu-id="51db2-286">혼합 현실 개발자 센터의 유용한 리소스</span><span class="sxs-lookup"><span data-stu-id="51db2-286">Useful resources on the Mixed Reality Dev Center</span></span>

| <span data-ttu-id="51db2-287">![검색](features/images/mrdevcenter/icon-discover.png) [검색](/windows/mixed-reality/)</span><span class="sxs-lookup"><span data-stu-id="51db2-287">![Discover](features/images/mrdevcenter/icon-discover.png) [Discover](/windows/mixed-reality/)</span></span>| <span data-ttu-id="51db2-288">![디자인](features/images/mrdevcenter/icon-design.png) [디자인](/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="51db2-288">![Design](features/images/mrdevcenter/icon-design.png) [Design](/windows/mixed-reality/design)</span></span>| <span data-ttu-id="51db2-289">![개발](features/images/mrdevcenter/icon-develop.png) [개발](/windows/mixed-reality/development)</span><span class="sxs-lookup"><span data-stu-id="51db2-289">![Develop](features/images/mrdevcenter/icon-develop.png) [Develop](/windows/mixed-reality/development)</span></span>| <span data-ttu-id="51db2-290">![배포)](features/images/mrdevcenter/icon-distribute.png) [배포](/windows/mixed-reality/implementing-3d-app-launchers)</span><span class="sxs-lookup"><span data-stu-id="51db2-290">![Distribute)](features/images/mrdevcenter/icon-distribute.png) [Distribute](/windows/mixed-reality/implementing-3d-app-launchers)</span></span>|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| <span data-ttu-id="51db2-291">HoloLens 및 몰입형 헤드셋(VR)을 위한 혼합 현실 환경을 빌드하는 방법을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-291">Learn to build mixed reality experiences for HoloLens and immersive headsets (VR).</span></span>          | <span data-ttu-id="51db2-292">디자인 가이드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-292">Get design guides.</span></span> <span data-ttu-id="51db2-293">사용자 인터페이스를 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-293">Build user interface.</span></span> <span data-ttu-id="51db2-294">상호 작용 및 입력을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-294">Learn interactions and input.</span></span>     | <span data-ttu-id="51db2-295">개발 가이드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-295">Get development guides.</span></span> <span data-ttu-id="51db2-296">기술을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-296">Learn the technology.</span></span> <span data-ttu-id="51db2-297">과학을 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-297">Understand the science.</span></span>       | <span data-ttu-id="51db2-298">다른 사용자에게 앱을 제공할 수 있도록 준비하고 3D 시작 관리자를 만드는 방안을 고려해 보세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-298">Get your app ready for others and consider creating a 3D launcher.</span></span> |

## <a name="useful-resources-on-azure"></a><span data-ttu-id="51db2-299">Azure에 대한 유용한 리소스</span><span class="sxs-lookup"><span data-stu-id="51db2-299">Useful resources on Azure</span></span>

| <span data-ttu-id="51db2-300">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span><span class="sxs-lookup"><span data-stu-id="51db2-300">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span></span><br> [<span data-ttu-id="51db2-301">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="51db2-301">Spatial Anchors</span></span>](/azure/spatial-anchors/)| <span data-ttu-id="51db2-302">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="51db2-302">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](/azure/cognitive-services/speech-service/)</span></span>| <span data-ttu-id="51db2-303">![비전 서비스](features/images/mrdevcenter/icon-azurevisionservices.png) [비전 서비스](/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="51db2-303">![Vision Services](features/images/mrdevcenter/icon-azurevisionservices.png) [Vision Services](/azure/cognitive-services/computer-vision/)</span></span>|
| :------------------------| :--------------------- | :---------------------- |
| <span data-ttu-id="51db2-304">Spatial Anchors는 시간이 지나도 디바이스에서 위치를 유지하는 개체를 사용하여 Mixed Reality 환경을 만들 수 있는 플랫폼 간 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-304">Spatial Anchors is a cross-platform service that allows you to create Mixed Reality experiences using objects that persist their location across devices over time.</span></span>| <span data-ttu-id="51db2-305">음성을 텍스트로 변환, 화자 인식, 음성 번역 등의 Azure 기반 음성 기능을 검색하고 애플리케이션에 통합하세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-305">Discover and integrate Azure powered speech capabilities like speech to text, speaker recognition or speech translation into your application.</span></span>| <span data-ttu-id="51db2-306">컴퓨터 비전, 얼굴 감지, 감정 인식, 비디오 인덱서 등의 비전 서비스를 사용하여 이미지 또는 비디오 콘텐츠를 식별하고 분석하세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-306">Identify and analyze your image or video content using Vision Services like computer vision, face detection, emotion recognition or video indexer.</span></span> |

## <a name="how-to-contribute"></a><span data-ttu-id="51db2-307">참가 방법</span><span class="sxs-lookup"><span data-stu-id="51db2-307">How to contribute</span></span>

<span data-ttu-id="51db2-308">[기여](contributing/contributing.md)에서 MRTK에 기여할 수 있는 방법을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-308">Learn how you can contribute to MRTK at [Contributing](contributing/contributing.md).</span></span>

## <a name="getting-help"></a><span data-ttu-id="51db2-309">도움말 보기</span><span class="sxs-lookup"><span data-stu-id="51db2-309">Getting help</span></span>

<span data-ttu-id="51db2-310">MRTK로 인한 문제가 발생했거나 작업을 수행하는 방법에 대한 질문이 있는 경우 다음과 같은 몇 가지 리소스를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-310">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="51db2-311">버그 보고서의 경우 GitHub 리포지토리에서 [문제를 제기](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose)하세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-311">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="51db2-312">질문이 있는 경우 [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) 또는 Slack의 [혼합 현실 도구 키트 채널](https://holodevelopers.slack.com/messages/C2H4HT858)에 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="51db2-312">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="51db2-313">[자동 초대 발신자](https://holodevelopersslack.azurewebsites.net/)를 통해 Slack 커뮤니티에 가입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51db2-313">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>