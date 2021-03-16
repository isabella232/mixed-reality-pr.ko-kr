---
title: MRTK-Unity 개발자 설명서
description: Unity용 Mixed Reality Toolkit에 대해 알아보세요.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: a774a5c08cb2d8bbaeebeca19cec366504efba58
ms.sourcegitcommit: 5c81c19905b26818882e49679bd71f5dd7bc6d3b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103202818"
---
# <a name="what-is-the-mixed-reality-toolkit"></a><span data-ttu-id="2148d-104">Mixed Reality Toolkit이란 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="2148d-104">What is the Mixed Reality Toolkit</span></span>

![Mixed Reality Toolkit](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="2148d-106">MRTK-Unity는 Unity에서 플랫폼 간 MR 앱 개발을 가속화하는 데 사용되는 구성 요소 및 기능 집합을 제공하는 Microsoft 기반 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-106">MRTK-Unity is a Microsoft-driven project that provides a set of components and features, used to accelerate cross-platform MR app development in Unity.</span></span> <span data-ttu-id="2148d-107">일부 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-107">Here are some of its functions:</span></span>

* <span data-ttu-id="2148d-108">**공간 상호 작용 및 UI를 위한 플랫폼 간 입력 시스템 및 구성 요소** 를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-108">Provides the **cross-platform input system and building blocks for spatial interactions and UI**.</span></span>
* <span data-ttu-id="2148d-109">변경 내용을 즉시 볼 수 있는 편집기 내 시뮬레이션을 통해 **프로토타입을 신속하게 제작** 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-109">Enables **rapid prototyping** via in-editor simulation that allows you to see changes immediately.</span></span>
* <span data-ttu-id="2148d-110">**확장 가능한 프레임워크** 로서 작동해 개발자에게 핵심 구성 요소를 교환하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-110">Operates as an **extensible framework** that provides developers the ability to swap out core components.</span></span>
* <span data-ttu-id="2148d-111">다음을 포함한 **다양한 플랫폼을 지원** 합니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-111">**Supports a wide range of platforms**, including</span></span>
  * <span data-ttu-id="2148d-112">OpenXR(Unity 2020.2 이상)</span><span class="sxs-lookup"><span data-stu-id="2148d-112">OpenXR (Unity 2020.2 or newer)</span></span>
    * <span data-ttu-id="2148d-113">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2148d-113">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="2148d-114">Windows Mixed Reality 헤드셋</span><span class="sxs-lookup"><span data-stu-id="2148d-114">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="2148d-115">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2148d-115">Windows Mixed Reality</span></span>
    * <span data-ttu-id="2148d-116">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="2148d-116">Microsoft HoloLens</span></span>
    * <span data-ttu-id="2148d-117">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2148d-117">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="2148d-118">Windows Mixed Reality 헤드셋</span><span class="sxs-lookup"><span data-stu-id="2148d-118">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="2148d-119">Oculus(Unity 2019.3 이상)</span><span class="sxs-lookup"><span data-stu-id="2148d-119">Oculus (Unity 2019.3 or newer)</span></span>
    * <span data-ttu-id="2148d-120">Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="2148d-120">Oculus Quest</span></span>
  * <span data-ttu-id="2148d-121">OpenVR</span><span class="sxs-lookup"><span data-stu-id="2148d-121">OpenVR</span></span>
    * <span data-ttu-id="2148d-122">Windows Mixed Reality 헤드셋</span><span class="sxs-lookup"><span data-stu-id="2148d-122">Windows Mixed Reality headsets</span></span>
    * <span data-ttu-id="2148d-123">HTC Vive</span><span class="sxs-lookup"><span data-stu-id="2148d-123">HTC Vive</span></span>
    * <span data-ttu-id="2148d-124">Oculus Rift</span><span class="sxs-lookup"><span data-stu-id="2148d-124">Oculus Rift</span></span>
  * <span data-ttu-id="2148d-125">Ultraleap Hand Tracking</span><span class="sxs-lookup"><span data-stu-id="2148d-125">Ultraleap Hand Tracking</span></span>
  * <span data-ttu-id="2148d-126">iOS, Android 같은 모바일 디바이스</span><span class="sxs-lookup"><span data-stu-id="2148d-126">Mobile devices such as iOS and Android</span></span>

## <a name="getting-started-with-mrtk"></a><span data-ttu-id="2148d-127">MRTK 시작</span><span class="sxs-lookup"><span data-stu-id="2148d-127">Getting started with MRTK</span></span>

<span data-ttu-id="2148d-128">Unity에서 MRTK 또는 Mixed Reality 개발이 처음인 경우 필요한 도구를 설치한 다음, HoloLens 2 자습서 시리즈를 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-128">If you're new to MRTK or Mixed Reality development in Unity, we recommend you install the necessary tools and then follow the HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2148d-129">도구 설치</span><span class="sxs-lookup"><span data-stu-id="2148d-129">Install the Tools</span></span>](install-the-tools.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="2148d-130">HoloLens 2 자습서 시리즈</span><span class="sxs-lookup"><span data-stu-id="2148d-130">HoloLens 2 Tutorial Series</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

<span data-ttu-id="2148d-131">작동 원리를 자세히 알고 싶으신가요?</span><span class="sxs-lookup"><span data-stu-id="2148d-131">Want to see what's going on under the hood?</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="2148d-132">GitHub에서 MRTK 살펴보기</span><span class="sxs-lookup"><span data-stu-id="2148d-132">Explore MRTK on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a><span data-ttu-id="2148d-133">설명서</span><span class="sxs-lookup"><span data-stu-id="2148d-133">Documentation</span></span>

| <span data-ttu-id="2148d-134">[![릴리스 정보](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-134">[![Release notes](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span></span><br/>[<span data-ttu-id="2148d-135">릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="2148d-135">Release Notes</span></span>](release-notes/mrtk-26-release-notes.md)| <span data-ttu-id="2148d-136">[![MRTK 개요](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-136">[![MRTK Overview](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span></span><br/>[<span data-ttu-id="2148d-137">MRTK 개요</span><span class="sxs-lookup"><span data-stu-id="2148d-137">MRTK Overview</span></span>](architecture/overview.md)|<span data-ttu-id="2148d-138">[![API 참조](features/images/MRTK_Icon_APIReference.png)](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)</span><span class="sxs-lookup"><span data-stu-id="2148d-138">[![API Reference](features/images/MRTK_Icon_APIReference.png)](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)</span></span><br/>[<span data-ttu-id="2148d-139">API 참조</span><span class="sxs-lookup"><span data-stu-id="2148d-139">API Reference</span></span>](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a><span data-ttu-id="2148d-140">빌드 상태</span><span class="sxs-lookup"><span data-stu-id="2148d-140">Build status</span></span>

| <span data-ttu-id="2148d-141">Branch</span><span class="sxs-lookup"><span data-stu-id="2148d-141">Branch</span></span> | <span data-ttu-id="2148d-142">CI 상태</span><span class="sxs-lookup"><span data-stu-id="2148d-142">CI Status</span></span> | <span data-ttu-id="2148d-143">문서 상태</span><span class="sxs-lookup"><span data-stu-id="2148d-143">Docs Status</span></span> |
|---|---|---|
| `mrtk_development` |<span data-ttu-id="2148d-144">[![CI 상태](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span><span class="sxs-lookup"><span data-stu-id="2148d-144">[![CI Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span></span>|<span data-ttu-id="2148d-145">[![문서 상태](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span><span class="sxs-lookup"><span data-stu-id="2148d-145">[![Docs Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span></span>

## <a name="feature-areas"></a><span data-ttu-id="2148d-146">기능 영역</span><span class="sxs-lookup"><span data-stu-id="2148d-146">Feature areas</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="2148d-147">[![입력 시스템](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-147">[![Input System](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="2148d-148">**[입력 시스템](features/input/overview.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-148">**[Input System](features/input/overview.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-149">[![손 추적(HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-149">[![Hand Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="2148d-150">**[손 추적 <br> (HoloLens 2)](features/input/hand-tracking.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-150">**[Hand Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-151">[![시선 추적(HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-151">[![Eye Tracking (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span></span><br>
        <span data-ttu-id="2148d-152">**[시선 추적 <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-152">**[Eye Tracking <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-153">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-153">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span></span><br>
        <span data-ttu-id="2148d-154">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-154">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2148d-155">[![손 추적(Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-155">[![Hand Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span></span><br>
        <span data-ttu-id="2148d-156">**[손 추적 <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-156">**[Hand Tracking <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-157">[![UI 컨트롤](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="2148d-157">[![UI Controls](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span></span><br>
        <span data-ttu-id="2148d-158">**[UI 컨트롤](#ux-building-blocks)**</span><span class="sxs-lookup"><span data-stu-id="2148d-158">**[UI Controls](#ux-building-blocks)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-159">[![해결기](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-159">[![Solvers](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span></span><br>
        <span data-ttu-id="2148d-160">**[해결기](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-160">**[Solvers](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-161">[![다중 장면 관리자](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-161">[![Multi-Scene Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="2148d-162">**[다중 장면<br/> 관리자](features/scene-system/scene-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-162">**[Multi-Scene<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2148d-163">[![공간 인식](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-163">[![Spatial Awareness](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span></span><br>
        <span data-ttu-id="2148d-164">**[공간<br/> 인식](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-164">**[Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-165">[![진단 도구](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-165">[![Diagnostic Tool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="2148d-166">**[진단 <br/> 도구](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-166">**[Diagnostic <br/> Tool](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-167">[![MRTK 표준 셰이더 보기](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span><span class="sxs-lookup"><span data-stu-id="2148d-167">[![MRTK Standard Shader View](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span></span><br>
        <span data-ttu-id="2148d-168">**[MRTK 표준 셰이더 예제 보기](features/rendering/mrtk-standard-shader.md?q=shader)**</span><span class="sxs-lookup"><span data-stu-id="2148d-168">**[MRTK Standard Shader Example View](features/rendering/mrtk-standard-shader.md?q=shader)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-169">[![음성 및 받아쓰기](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-169">[![Speech & Dictation](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="2148d-170">**[음성](features/input/speech.md)<br/> & [받아쓰기](features/input/dictation.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-170">**[Speech](features/input/speech.md)<br/> & [Dictation](features/input/dictation.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2148d-171">[![경계 시스템](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-171">[![Boundary System](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span></span><br>
        <span data-ttu-id="2148d-172">**[경계 <br/>시스템](features/boundary/boundary-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-172">**[Boundary <br/>System](features/boundary/boundary-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-173">[![편집기 내 시뮬레이션](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-173">[![In-Editor Simulation](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="2148d-174">**[편집기 내 <br/> 시뮬레이션](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-174">**[In-Editor <br/> Simulation](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-175">[![실험적 기능](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-175">[![Experimental Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span></span><br>
        <span data-ttu-id="2148d-176">**[실험적<br/> 기능](contributing/experimental-features.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-176">**[Experimental <br/> Features](contributing/experimental-features.md)**</span></span><br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a><span data-ttu-id="2148d-177">UX 구성 요소</span><span class="sxs-lookup"><span data-stu-id="2148d-177">UX building blocks</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="2148d-178">[![단추](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[단추](features/ux-building-blocks/button.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-178">[![Button](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Button](features/ux-building-blocks/button.md)**</span></span><br>
        <span data-ttu-id="2148d-179">HoloLens 2의 연결된 손을 포함한 다양한 입력 방법을 지원하는 단추 컨트롤</span><span class="sxs-lookup"><span data-stu-id="2148d-179">A button control which supports various input methods, including HoloLens 2's articulated hand</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-180">[![경계 컨트롤](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[경계 컨트롤](features/ux-building-blocks/bounds-control.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-180">[![Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds Control](features/ux-building-blocks/bounds-control.md)**</span></span><br>
        <span data-ttu-id="2148d-181">3D 공간에서 개체 조작을 위한 표준 UI</span><span class="sxs-lookup"><span data-stu-id="2148d-181">Standard UI for manipulating objects in 3D space</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-182">[![개체 조작자](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[개체 조작자](features/ux-building-blocks/object-manipulator.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-182">[![Object Manipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Object Manipulator](features/ux-building-blocks/object-manipulator.md)**</span></span><br>
        <span data-ttu-id="2148d-183">한 손 또는 양손을 사용하여 개체를 조작하기 위한 스크립트</span><span class="sxs-lookup"><span data-stu-id="2148d-183">Script for manipulating objects with one or two hands</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2148d-184">[![슬레이트](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[슬레이트](features/ux-building-blocks/slate.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-184">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span></span><br>
        <span data-ttu-id="2148d-185">연결된 손 입력을 사용한 스크롤을 지원하는 2D 스타일 평면</span><span class="sxs-lookup"><span data-stu-id="2148d-185">2D style plane which supports scrolling with articulated hand input</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-186">[![시스템 키보드](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[시스템 키보드](features/ux-building-blocks/system-keyboard.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-186">[![System Keyboard](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[System Keyboard](features/ux-building-blocks/system-keyboard.md)**</span></span><br>
        <span data-ttu-id="2148d-187">Unity에서 시스템 키보드를 사용하는 예제 스크립트</span><span class="sxs-lookup"><span data-stu-id="2148d-187">Example script of using the system keyboard in Unity</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-188">[![상호 작용 가능](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[상호 작용 가능](features/ux-building-blocks/interactable.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-188">[![Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**</span></span><br>
        <span data-ttu-id="2148d-189">시각적 상태 및 테마 지원으로 개체를 상호 작용 가능하게 만드는 스크립트</span><span class="sxs-lookup"><span data-stu-id="2148d-189">A script for making objects interactable with visual states and theme support</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2148d-190">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-190">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
        <span data-ttu-id="2148d-191">태그 동반, 신체 고정, 일정한 뷰 크기 및 표면 자성과 같은 다양한 개체 위치 지정 동작</span><span class="sxs-lookup"><span data-stu-id="2148d-191">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-192">[![개체 컬렉션](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[개체 컬렉션](features/ux-building-blocks/object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-192">[![Object Collection](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Object Collection](features/ux-building-blocks/object-collection.md)**</span></span><br>
        <span data-ttu-id="2148d-193">3차원 모양의 개체 배열을 배치하는 스크립트</span><span class="sxs-lookup"><span data-stu-id="2148d-193">Script for laying out an array of objects in a three-dimensional shape</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-194">[![도구 설명](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[도구 설명](features/ux-building-blocks/tooltip.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-194">[![Tooltip](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Tooltip](features/ux-building-blocks/tooltip.md)**</span></span><br>
        <span data-ttu-id="2148d-195">모션 컨트롤러 및 개체에 레이블을 지정하는 데 사용할 수 있는 유연한 앵커/피벗 시스템을 포함하는 주석 UI</span><span class="sxs-lookup"><span data-stu-id="2148d-195">Annotation UI with a flexible anchor/pivot system, which can be used for labeling motion controllers and objects</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2148d-196">[![슬라이더](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[슬라이더](features/ux-building-blocks/sliders.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-196">[![Slider](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Slider](features/ux-building-blocks/sliders.md)**</span></span><br>
        <span data-ttu-id="2148d-197">직접 손 추적 상호 작용을 지원하는 값 조정을 위한 슬라이더 UI</span><span class="sxs-lookup"><span data-stu-id="2148d-197">Slider UI for adjusting values supporting direct hand tracking interaction</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-198">[![MRTK 표준 셰이더](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK 표준 셰이더](features/rendering/mrtk-standard-shader.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-198">[![MRTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**</span></span><br>
        <span data-ttu-id="2148d-199">MRTK의 표준 셰이더는 성능으로 다양한 Fluent Design 요소를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-199">MRTK's Standard shader supports various Fluent design elements with performance</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-200">[![손 메뉴](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[손 메뉴](features/ux-building-blocks/hand-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-200">[![Hand Menu](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Hand Menu](features/ux-building-blocks/hand-menu.md)**</span></span><br>
        <span data-ttu-id="2148d-201">손 제약 조건 해결기를 사용하는 빠른 액세스용 손 잠금 UI</span><span class="sxs-lookup"><span data-stu-id="2148d-201">Hand-locked UI for quick access, using the Hand Constraint Solver</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2148d-202">[![앱 바](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[앱 바](features/ux-building-blocks/app-bar.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-202">[![App Bar](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App Bar](features/ux-building-blocks/app-bar.md)**</span></span><br>
        <span data-ttu-id="2148d-203">경계 컨트롤의 수동 활성화를 위한 UI</span><span class="sxs-lookup"><span data-stu-id="2148d-203">UI for Bounds Control's manual activation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-204">[![포인터](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[포인터](features/input/pointers.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-204">[![Pointers](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointers](features/input/pointers.md)**</span></span><br>
        <span data-ttu-id="2148d-205">다양한 종류의 포인터에 대해 알아보기</span><span class="sxs-lookup"><span data-stu-id="2148d-205">Learn about various types of pointers</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-206">[![손끝 시각화](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[손끝 시각화](features/ux-building-blocks/fingertip-visualization.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-206">[![Fingertip Visualization](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip Visualization](features/ux-building-blocks/fingertip-visualization.md)**</span></span><br>
        <span data-ttu-id="2148d-207">직접 상호 작용에 대한 신뢰도를 향상시키는 손끝의 시각적 어포던스</span><span class="sxs-lookup"><span data-stu-id="2148d-207">Visual affordance on the fingertip which improves the confidence for the direct interaction</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2148d-208">[![Near 메뉴](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near 메뉴](features/ux-building-blocks/near-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-208">[![Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near Menu](features/ux-building-blocks/near-menu.md)**</span></span><br>
        <span data-ttu-id="2148d-209">근거리 상호 작용을 위한 부동 메뉴 UI</span><span class="sxs-lookup"><span data-stu-id="2148d-209">Floating menu UI for the near interactions</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-210">[![공간 인식 시작](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[공간 인식 보기](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-210">[![Spatial Awareness Getting started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial Awareness View](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
        <span data-ttu-id="2148d-211">홀로그램 개체가 물리적 환경과 상호 작용하게 만들기</span><span class="sxs-lookup"><span data-stu-id="2148d-211">Make your holographic objects interact with the physical environments</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-212">[![음성 명령](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[음성 명령](features/input/speech.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-212">[![Voice Command](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Voice Command](features/input/speech.md)**</span></span><br>
        <span data-ttu-id="2148d-213">음성 입력 통합을 위한 스크립트 및 예제</span><span class="sxs-lookup"><span data-stu-id="2148d-213">Scripts and examples for integrating speech input</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2148d-214">[![진행률 표시기](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[진행률 표시기](features/ux-building-blocks/progress-indicator.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-214">[![Progress Indicator](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Progress Indicator](features/ux-building-blocks/progress-indicator.md)**</span></span><br>
        <span data-ttu-id="2148d-215">데이터 프로세스 또는 작업을 알려주기 위한 시각적 표시기</span><span class="sxs-lookup"><span data-stu-id="2148d-215">Visual indicator for communicating data process or operation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-216">[![대화 상자](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[대화 상자](features/ux-building-blocks/dialog.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-216">[![Dialog](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialog](features/ux-building-blocks/dialog.md)**</span></span><br>
        <span data-ttu-id="2148d-217">사용자의 확인 또는 승인을 요청하는 UI</span><span class="sxs-lookup"><span data-stu-id="2148d-217">UI for asking for user's confirmation or acknowledgement</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-218">[![손 코치](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[손 코치](features/ux-building-blocks/hand-coach.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-218">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span></span><br>
        <span data-ttu-id="2148d-219">제스처가 학습되지 않은 경우 사용자 안내를 지원하는 구성 요소</span><span class="sxs-lookup"><span data-stu-id="2148d-219">Component that helps guide the user when the gesture has not been taught</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2148d-220">[![직접 물리학 서비스](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[직접 물리학 서비스 [실험용]](features/experimental/hand-physics-service.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-220">[![Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Hand Physics Service [Experimental]](features/experimental/hand-physics-service.md)**</span></span><br>
        <span data-ttu-id="2148d-221">직접 물리학 서비스는 강체 충돌 이벤트 및 연결된 손과의 상호 작용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-221">The hand physics service enables rigid body collision events and interactions with articulated hands</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-222">[![스크롤 컬렉션](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[스크롤 컬렉션](features/ux-building-blocks/scrolling-object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-222">[![Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling Collection](features/ux-building-blocks/scrolling-object-collection.md)**</span></span><br>
        <span data-ttu-id="2148d-223">3D 개체를 기본적으로 스크롤하는 개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="2148d-223">An Object Collection that natively scrolls 3D objects</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-224">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [실험용]](features/experimental/dock.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-224">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimental]](features/experimental/dock.md)**</span></span><br>
        <span data-ttu-id="2148d-225">Dock를 사용하면 미리 결정된 위치 안팎으로 개체를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-225">The Dock allows objects to be moved in and out of predetermined positions</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="2148d-226">[![시선 추적: 대상 선택](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[시선 추적: 대상 선택](features/input/eye-tracking/eye-tracking-target-selection.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-226">[![Eye Tracking: Target Selection](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eye Tracking: Target Selection](features/input/eye-tracking/eye-tracking-target-selection.md)**</span></span><br>
        <span data-ttu-id="2148d-227">시선, 음성 및 손 입력을 결합하여 장면 전체의 홀로그램을 빠르고 간편하게 선택</span><span class="sxs-lookup"><span data-stu-id="2148d-227">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-228">[![시선 추적: 탐색](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[시선 추적: 탐색](features/input/eye-tracking/eye-tracking-navigation.md)**</span><span class="sxs-lookup"><span data-stu-id="2148d-228">[![Eye Tracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eye Tracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span></span><br>
        <span data-ttu-id="2148d-229">표시되는 내용에 따라 텍스트를 자동으로 스크롤하거나 포커스가 있는 콘텐츠를 확대하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="2148d-229">Learn how to auto-scroll text or fluently zoom into focused content based on what you are looking at</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2148d-230">[![시선 추적: 열 지도](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[시선 추적: 열 지도](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span><span class="sxs-lookup"><span data-stu-id="2148d-230">[![Eye Tracking: Heat Map](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eye Tracking: Heat Map](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span></span><br>
        <span data-ttu-id="2148d-231">사용자가 앱에서 본 내용을 로깅, 로드 및 시각화하는 예제</span><span class="sxs-lookup"><span data-stu-id="2148d-231">Examples for logging, loading and visualizing what users have been looking at in your app</span></span>
    :::column-end:::
:::row-end:::

## <a name="tools"></a><span data-ttu-id="2148d-232">도구</span><span class="sxs-lookup"><span data-stu-id="2148d-232">Tools</span></span>

|  <span data-ttu-id="2148d-233">[![최적화 창](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [최적화 창](features/tools/optimize-window.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-233">[![Optimize Window](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimize Window](features/tools/optimize-window.md)</span></span> | <span data-ttu-id="2148d-234">[![종속성 창](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [종속성 창](features/tools/dependency-window.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-234">[![Dependency Window](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Dependency Window](features/tools/dependency-window.md)</span></span> | ![빌드 창](features/images/MRTK_Icon_BuildWindow.png) <span data-ttu-id="2148d-236">빌드 창</span><span class="sxs-lookup"><span data-stu-id="2148d-236">Build Window</span></span> | <span data-ttu-id="2148d-237">[![입력 기록](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [입력 기록](features/input-simulation/input-animation-recording.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-237">[![Input recording](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Input recording](features/input-simulation/input-animation-recording.md)</span></span> |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="2148d-238">성능 최적화를 위해 Mixed Reality 프로젝트의 구성 자동화</span><span class="sxs-lookup"><span data-stu-id="2148d-238">Automate configuration of Mixed Reality projects for performance optimizations</span></span> | <span data-ttu-id="2148d-239">자산 간 종속성 분석 및 사용되지 않는 자산 식별</span><span class="sxs-lookup"><span data-stu-id="2148d-239">Analyze dependencies between assets and identify unused assets</span></span> |  <span data-ttu-id="2148d-240">Mixed Reality 애플리케이션을 위한 엔드투엔드 빌드 프로세스 구성 및 실행</span><span class="sxs-lookup"><span data-stu-id="2148d-240">Configure and execute an end-to-end build process for Mixed Reality applications</span></span> | <span data-ttu-id="2148d-241">편집기에서 머리 이동 및 손 추적 데이터 기록 및 재생</span><span class="sxs-lookup"><span data-stu-id="2148d-241">Record and playback head movement and hand tracking data in editor</span></span> |

## <a name="example-scenes"></a><span data-ttu-id="2148d-242">예제 장면</span><span class="sxs-lookup"><span data-stu-id="2148d-242">Example scenes</span></span>

<span data-ttu-id="2148d-243">[이 예제 장면](features/example-scenes/hand-interaction-examples.md)에서 MRTK의 다양한 상호 작용 유형과 UI 컨트롤을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-243">Explore MRTK's various types of interactions and UI controls in [this example scene](features/example-scenes/hand-interaction-examples.md).</span></span>

<span data-ttu-id="2148d-244">[![예제 장면 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-244">[![Example Scene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="mrtk-examples-hub"></a><span data-ttu-id="2148d-245">MRTK 예제 허브</span><span class="sxs-lookup"><span data-stu-id="2148d-245">MRTK examples hub</span></span>

<span data-ttu-id="2148d-246">MRTK 예제 허브를 사용하여 MRTK에서 다양한 예제 장면을 사용해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-246">With the MRTK Examples Hub, you can try various example scenes in MRTK.</span></span>
<span data-ttu-id="2148d-247">[MR Feature Tool](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)에서 "Mixed Reality Toolkit 예제" 패키지를 선택하여 HoloLens(x86), HoloLens 2(ARM) 및 Windows Mixed Reality 몰입형 헤드셋(x64)용으로 미리 작성된 앱 패키지를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-247">You can download pre-built app packages for HoloLens(x86), HoloLens 2(ARM), and Windows Mixed Reality immersive headsets(x64) by selecting the "Mixed Reality Toolkit Examples" package in the [MR Feature Tool](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span></span> <span data-ttu-id="2148d-248">[Windows 장치 포털을 사용하여 HoloLens(1세대)에 앱을 설치](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-248">Make sure to [use the Windows Device Portal to install apps on HoloLens (1st gen)](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span></span> <span data-ttu-id="2148d-249">HoloLens 2에서 [Microsoft Store 앱을 통해 MRTK 예제 허브](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4)를 다운로드하고 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-249">On HoloLens 2, you can download and install [MRTK Examples Hub through the Microsoft Store app](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span></span>

<span data-ttu-id="2148d-250">MRTK의 장면 시스템과 장면 전환 서비스를 사용하여 다중 장면 허브를 만드는 방법에 대한 자세한 내용은 [예제 허브 추가 정보 페이지](features/example-scenes/example-hub.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-250">See [Examples Hub README page](features/example-scenes/example-hub.md) to learn about the details on creating a multi-scene hub with MRTK's scene system and scene transition service.</span></span>

<span data-ttu-id="2148d-251">[![예제 장면 허브](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="2148d-251">[![Example Scene Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="sample-apps-made-with-mrtk"></a><span data-ttu-id="2148d-252">MRTK를 사용하여 만든 샘플 앱</span><span class="sxs-lookup"><span data-stu-id="2148d-252">Sample apps made with MRTK</span></span>

| <span data-ttu-id="2148d-253">[![원소의 주기율표](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="2148d-253">[![Periodic Table of the Elements](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span>| <span data-ttu-id="2148d-254">[![갤럭시 익스플로러](features/images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="2148d-254">[![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span></span>| <span data-ttu-id="2148d-255">[![Surfaces 샘플 앱](features/images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/sampleapp-surfaces)</span><span class="sxs-lookup"><span data-stu-id="2148d-255">[![Surfaces sample app](features/images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/sampleapp-surfaces)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="2148d-256">[원소의 주기율표](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)는 MRTK의 입력 시스템 및 구성 요소를 사용하여 HoloLens 및 몰입형 헤드셋을 위한 앱 환경을 만드는 방법을 보여주는 오픈 소스 샘플 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-256">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) is an open-source sample app which demonstrates how to use MRTK's input system and building blocks to create an app experience for HoloLens and Immersive headsets.</span></span> <span data-ttu-id="2148d-257">포팅 사례 읽기: [MRTK v2를 사용하는 HoloLens 2에 원소의 주기율표 앱 가져오기](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="2148d-257">Read the porting story: [Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span> |<span data-ttu-id="2148d-258">[갤럭시 익스플로러](https://github.com/Microsoft/GalaxyExplorer)는 HoloLens '아이디어 공유' 캠페인의 일환으로 2016년 3월에 처음 개발된 오픈 소스 샘플 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-258">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app that was originally developed in March 2016 as part of the HoloLens 'Share Your Idea' campaign.</span></span> <span data-ttu-id="2148d-259">갤럭시 익스플로러는 MRTK v2를 사용하는 HoloLens 2를 위한 새 기능으로 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-259">Galaxy Explorer has been updated with new features for HoloLens 2, using MRTK v2.</span></span> <span data-ttu-id="2148d-260">사례 읽기: [HoloLens 2용 갤럭시 익스플로러 제작](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="2148d-260">Read the story: [The Making of Galaxy Explorer for HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)</span></span> |<span data-ttu-id="2148d-261">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)는 HoloLens 2용 오픈 소스 샘플 앱으로, 시각적 개체, 오디오, 완전히 연결된 손 추적으로 촉감을 만드는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-261">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) is an open-source sample app for HoloLens 2 which explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span> <span data-ttu-id="2148d-262">자세한 디자인 및 개발 사례는 Microsoft 혼합 현실 개발자의 날 세션 [Surfaces 앱을 통한 학습](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-262">Check out Microsoft MR Dev Days session [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) for the detailed design and development story.</span></span> |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a><span data-ttu-id="2148d-263">2020 혼합 현실 개발자의 날의 세션 동영상</span><span class="sxs-lookup"><span data-stu-id="2148d-263">Session videos from Mixed Reality Dev Days 2020</span></span>

| <span data-ttu-id="2148d-264">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="2148d-264">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>| <span data-ttu-id="2148d-265">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span><span class="sxs-lookup"><span data-stu-id="2148d-265">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>| <span data-ttu-id="2148d-266">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span><span class="sxs-lookup"><span data-stu-id="2148d-266">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="2148d-267">간단한 MRTK 앱을 만드는 방법을 처음부터 끝까지 설명하는 자습서입니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-267">Tutorial on how to create a simple MRTK app from start to finish.</span></span> <span data-ttu-id="2148d-268">상호 작용 개념 및 MRTK의 다중 플랫폼 기능에 대해 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-268">Learn about interaction concepts and MRTK’s multi-platform capabilities.</span></span> | <span data-ttu-id="2148d-269">멋진 혼합 현실 환경을 빌드하는 데 도움이 되는 MRTK의 UX 구성 요소에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-269">Deep dive on the MRTK’s UX building blocks that help you build beautiful mixed reality experiences.</span></span> | <span data-ttu-id="2148d-270">MRTK 및 외부의 성능 도구에 대한 소개와 MRTK 표준 셰이더에 대한 개요입니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-270">An introduction to performance tools, both in MRTK and external, as well as an overview of the MRTK Standard Shader.</span></span> |

<span data-ttu-id="2148d-271">더 많은 세션 동영상을 살펴보려면 [혼합 현실 개발자의 날](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-271">See [Mixed Reality Dev Days](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) to explore more session videos.</span></span>

## <a name="engage-with-the-community"></a><span data-ttu-id="2148d-272">커뮤니티에 참여</span><span class="sxs-lookup"><span data-stu-id="2148d-272">Engage with the community</span></span>

* <span data-ttu-id="2148d-273">[Slack](https://holodevelopers.slack.com/)에서 MRTK에 대한 대화에 참여하세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-273">Join the conversation around MRTK on [Slack](https://holodevelopers.slack.com/).</span></span> <span data-ttu-id="2148d-274">[자동 초대 발신자](https://holodevelopersslack.azurewebsites.net/)를 통해 Slack 커뮤니티에 가입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-274">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

* <span data-ttu-id="2148d-275">**MRTK** 태그를 사용하여 [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk)에서 MRTK를 사용하는 방법에 관해 질문하세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-275">Ask questions about using MRTK on [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) using the **MRTK** tag.</span></span>

* <span data-ttu-id="2148d-276">MRTK 코드에서 문제가 발생한 경우 [알려진 문제](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)를 검색하거나 [새 문제](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)를 제기합니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-276">Search for [known issues](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) or file a [new issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) if you find something broken in MRTK code.</span></span>

* <span data-ttu-id="2148d-277">MRTK에 기여하는 방법에 대한 질문이 있는 경우 Slack의 [혼합 현실 도구 키트](https://holodevelopers.slack.com/messages/C2H4HT858) 채널로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-277">For questions about contributing to MRTK, go to the [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) channel on slack.</span></span>

<span data-ttu-id="2148d-278">이 프로젝트는 [Microsoft 오픈 소스 준수 사항](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-278">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="2148d-279">자세한 내용은 [준수 사항 FAQ](https://opensource.microsoft.com/codeofconduct/faq/)를 참조하고, 추가 질문이나 의견이 있는 경우에는 [opencode@microsoft.com](mailto:opencode@microsoft.com)으로 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-279">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a><span data-ttu-id="2148d-280">혼합 현실 개발자 센터의 유용한 리소스</span><span class="sxs-lookup"><span data-stu-id="2148d-280">Useful resources on the Mixed Reality Dev Center</span></span>

| <span data-ttu-id="2148d-281">![검색](features/images/mrdevcenter/icon-discover.png) [검색](https://docs.microsoft.com/windows/mixed-reality/)</span><span class="sxs-lookup"><span data-stu-id="2148d-281">![Discover](features/images/mrdevcenter/icon-discover.png) [Discover](https://docs.microsoft.com/windows/mixed-reality/)</span></span>| <span data-ttu-id="2148d-282">![디자인](features/images/mrdevcenter/icon-design.png) [디자인](https://docs.microsoft.com/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="2148d-282">![Design](features/images/mrdevcenter/icon-design.png) [Design](https://docs.microsoft.com/windows/mixed-reality/design)</span></span>| <span data-ttu-id="2148d-283">![개발](features/images/mrdevcenter/icon-develop.png) [개발](https://docs.microsoft.com/windows/mixed-reality/development)</span><span class="sxs-lookup"><span data-stu-id="2148d-283">![Develop](features/images/mrdevcenter/icon-develop.png) [Develop](https://docs.microsoft.com/windows/mixed-reality/development)</span></span>| <span data-ttu-id="2148d-284">![배포)](features/images/mrdevcenter/icon-distribute.png) [배포](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)</span><span class="sxs-lookup"><span data-stu-id="2148d-284">![Distribute)](features/images/mrdevcenter/icon-distribute.png) [Distribute](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)</span></span>|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| <span data-ttu-id="2148d-285">HoloLens 및 몰입형 헤드셋(VR)을 위한 혼합 현실 환경을 빌드하는 방법을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-285">Learn to build mixed reality experiences for HoloLens and immersive headsets (VR).</span></span>          | <span data-ttu-id="2148d-286">디자인 가이드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-286">Get design guides.</span></span> <span data-ttu-id="2148d-287">사용자 인터페이스를 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-287">Build user interface.</span></span> <span data-ttu-id="2148d-288">상호 작용 및 입력을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-288">Learn interactions and input.</span></span>     | <span data-ttu-id="2148d-289">개발 가이드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-289">Get development guides.</span></span> <span data-ttu-id="2148d-290">기술을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-290">Learn the technology.</span></span> <span data-ttu-id="2148d-291">과학을 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-291">Understand the science.</span></span>       | <span data-ttu-id="2148d-292">다른 사용자에게 앱을 제공할 수 있도록 준비하고 3D 시작 관리자를 만드는 방안을 고려해 보세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-292">Get your app ready for others and consider creating a 3D launcher.</span></span> |

## <a name="useful-resources-on-azure"></a><span data-ttu-id="2148d-293">Azure에 대한 유용한 리소스</span><span class="sxs-lookup"><span data-stu-id="2148d-293">Useful resources on Azure</span></span>

| <span data-ttu-id="2148d-294">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span><span class="sxs-lookup"><span data-stu-id="2148d-294">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span></span><br> [<span data-ttu-id="2148d-295">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="2148d-295">Spatial Anchors</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)| <span data-ttu-id="2148d-296">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](https://docs.microsoft.com/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="2148d-296">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](https://docs.microsoft.com/azure/cognitive-services/speech-service/)</span></span>| <span data-ttu-id="2148d-297">![비전 서비스](features/images/mrdevcenter/icon-azurevisionservices.png) [비전 서비스](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="2148d-297">![Vision Services](features/images/mrdevcenter/icon-azurevisionservices.png) [Vision Services](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)</span></span>|
| :------------------------| :--------------------- | :---------------------- |
| <span data-ttu-id="2148d-298">Spatial Anchors는 시간이 지나도 디바이스에서 위치를 유지하는 개체를 사용하여 Mixed Reality 환경을 만들 수 있는 플랫폼 간 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-298">Spatial Anchors is a cross-platform service that allows you to create Mixed Reality experiences using objects that persist their location across devices over time.</span></span>| <span data-ttu-id="2148d-299">음성을 텍스트로 변환, 화자 인식, 음성 번역 등의 Azure 기반 음성 기능을 검색하고 애플리케이션에 통합하세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-299">Discover and integrate Azure powered speech capabilities like speech to text, speaker recognition or speech translation into your application.</span></span>| <span data-ttu-id="2148d-300">컴퓨터 비전, 얼굴 감지, 감정 인식, 비디오 인덱서 등의 비전 서비스를 사용하여 이미지 또는 비디오 콘텐츠를 식별하고 분석하세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-300">Identify and analyze your image or video content using Vision Services like computer vision, face detection, emotion recognition or video indexer.</span></span> |

## <a name="how-to-contribute"></a><span data-ttu-id="2148d-301">참가 방법</span><span class="sxs-lookup"><span data-stu-id="2148d-301">How to contribute</span></span>

<span data-ttu-id="2148d-302">[기여](contributing/contributing.md)에서 MRTK에 기여할 수 있는 방법을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-302">Learn how you can contribute to MRTK at [Contributing](contributing/contributing.md).</span></span>

## <a name="getting-help"></a><span data-ttu-id="2148d-303">도움말 보기</span><span class="sxs-lookup"><span data-stu-id="2148d-303">Getting help</span></span>

<span data-ttu-id="2148d-304">MRTK로 인한 문제가 발생했거나 작업을 수행하는 방법에 대한 질문이 있는 경우 다음과 같은 몇 가지 리소스를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-304">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="2148d-305">버그 보고서의 경우 GitHub 리포지토리에서 [문제를 제기](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose)하세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-305">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="2148d-306">질문이 있는 경우 [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) 또는 Slack의 [혼합 현실 도구 키트 채널](https://holodevelopers.slack.com/messages/C2H4HT858)에 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="2148d-306">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="2148d-307">[자동 초대 발신자](https://holodevelopersslack.azurewebsites.net/)를 통해 Slack 커뮤니티에 가입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2148d-307">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>
