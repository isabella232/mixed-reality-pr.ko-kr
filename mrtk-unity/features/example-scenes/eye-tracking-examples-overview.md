---
title: 시선 추적 예제 개요
description: MRTK에서 시선 추적을 빌드하는 예제
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, EyeTracking,
ms.openlocfilehash: b5fd3ee35e54c54f2f6b21dc1ce53625c68f65b4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144682"
---
# <a name="eye-tracking-examples"></a><span data-ttu-id="dad1c-104">시선 추적 예제</span><span class="sxs-lookup"><span data-stu-id="dad1c-104">Eye tracking examples</span></span>

<span data-ttu-id="dad1c-105">이 항목에서는 MRTK 시선 추적 예제(Assets/MRTK/Examples/Demos/EyeTracking)를 기반으로 하여 MRTK에서 시선 추적을 빠르게 시작하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-105">This topic describes how to quickly get started with eye tracking in MRTK by building on MRTK eye tracking examples (Assets/MRTK/Examples/Demos/EyeTracking).</span></span>
<span data-ttu-id="dad1c-106">이러한 샘플을 통해 새로운 입력 기능인 **시선 추적!**</span><span class="sxs-lookup"><span data-stu-id="dad1c-106">These samples let you experience one of our new magical input capabilities: **Eye tracking**!</span></span>
<span data-ttu-id="dad1c-107">데모에는 암시적 시선 기반 활성화에서 **음성** 및 **손** 입력으로 보고 있는 내용에 대한 정보를 원활하게 결합하는 방법에 이르기까지 다양한 사용 사례가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-107">The demo includes various use cases, ranging from implicit eye-based activations to how to seamlessly combine information about what you are looking at with **voice** and **hand** input.</span></span>
<span data-ttu-id="dad1c-108">이렇게 하면 사용자는 대상을 보고 _'선택'이라고_ 말하거나 손 제스처를 수행하여 홀로그램 콘텐츠를 빠르고 쉽게 선택하고 보기 전체로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-108">This enables users to quickly and effortlessly select and move holographic content across their view simply by looking at a target and saying _'Select'_ or performing a hand gesture.</span></span>
<span data-ttu-id="dad1c-109">데모에는 슬레이트에 있는 텍스트 및 이미지의 시선 응시 지향 스크롤, 이동 및 확대/축소 예제도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-109">The demos also include an example for eye-gaze-directed scroll, pan and zoom of text and images on a slate.</span></span>
<span data-ttu-id="dad1c-110">마지막으로, 2D 슬레이트에서 사용자의 시각적 주의를 기록하고 시각화하는 예제가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-110">Finally, an example is provided for recording and visualizing the user's visual attention on a 2D slate.</span></span>
<span data-ttu-id="dad1c-111">다음 섹션에서는 MRTK 시선 추적 예제 패키지(Assets/MRTK/Examples/Demos/EyeTracking)에 포함된 각 샘플에 대한 자세한 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-111">In the following section, you will find more details on what each of the different samples in the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking) includes:</span></span>

![시선 추적 장면 목록](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

<span data-ttu-id="dad1c-113">다음 섹션은 개별 시선 추적 데모 장면에 대한 간략한 개요입니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-113">The following section is a quick overview of what the individual eye tracking demo scenes are about.</span></span>
<span data-ttu-id="dad1c-114">MRTK 시선 추적 데모 장면이 [가감적으로 로드되며,](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)아래에서 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-114">The MRTK eye tracking demo scenes are [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), which we will explain below how to set up.</span></span>

## <a name="overview-of-the-eye-tracking-demo-samples"></a><span data-ttu-id="dad1c-115">시선 추적 데모 샘플 개요</span><span class="sxs-lookup"><span data-stu-id="dad1c-115">Overview of the eye tracking demo samples</span></span>

### <a name="eye-supported-target-selection"></a>[<span data-ttu-id="dad1c-116">**시선 지원 대상 선택**</span><span class="sxs-lookup"><span data-stu-id="dad1c-116">**Eye-Supported Target Selection**</span></span>](../input/eye-tracking/eye-tracking-target-selection.md)

<span data-ttu-id="dad1c-117">이 자습서에서는 시선 응시 데이터에 쉽게 액세스하여 대상을 선택하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-117">This tutorial showcases the ease of accessing eye gaze data to select targets.</span></span>
<span data-ttu-id="dad1c-118">대상에 집중한다는 확신을 사용자에게 제공하기 위한 미묘한 피드백과 강력한 피드백의 예가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-118">It includes an example for subtle yet powerful feedback to provide the user with the confidence that a target is focused without being overwhelming.</span></span>
<span data-ttu-id="dad1c-119">또한 읽은 후 자동으로 사라지는 스마트 알림의 간단한 예가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-119">In addition, there is a simple example of smart notifications that automatically disappear after being read.</span></span>

<span data-ttu-id="dad1c-120">**요약:** 눈, 음성 및 손 입력의 조합을 사용하여 빠르고 간편한 대상 선택</span><span class="sxs-lookup"><span data-stu-id="dad1c-120">**Summary**: Fast and effortless target selections using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-navigation"></a>[<span data-ttu-id="dad1c-121">**눈에 잘 지 원하는 탐색**</span><span class="sxs-lookup"><span data-stu-id="dad1c-121">**Eye-Supported Navigation**</span></span>](../input/eye-tracking/eye-tracking-navigation.md)

<span data-ttu-id="dad1c-122">멀리 떨어져 있는 표시 또는 전자 판독기에서 몇 가지 정보를 읽고 표시 된 텍스트의 끝에 도달 하면 텍스트가 자동으로 이동 하 여 더 많은 콘텐츠를 표시 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-122">Imagine that you are reading some information on a distant display or your e-reader and when you reach the end of the displayed text, the text automatically scrolls up to reveal more content.</span></span>
<span data-ttu-id="dad1c-123">또는 원하는 위치로 직접 확대/축소 하는 방법에 대해 magically?</span><span class="sxs-lookup"><span data-stu-id="dad1c-123">Or how about magically zooming directly toward where you were looking at?</span></span>
<span data-ttu-id="dad1c-124">이 자습서에서는 눈에 전시 탐색에 대 한 몇 가지 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-124">These are some of the examples showcased in this tutorial regarding eye-supported navigation.</span></span>
<span data-ttu-id="dad1c-125">또한 현재 포커스에 따라 자동으로 회전 하도록 하 여 3D holograms의 수동 회전을 위한 예제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-125">In addition, there is an example for hands-free rotation of 3D holograms by making them automatically rotate based on your current focus.</span></span>

<span data-ttu-id="dad1c-126">**요약**: 눈동자, 음성 및 직접 입력의 조합을 사용 하 여 스크롤, 이동, 확대/축소, 3d 회전</span><span class="sxs-lookup"><span data-stu-id="dad1c-126">**Summary**: Scroll, pan, zoom, 3D rotation using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-positioning"></a>[<span data-ttu-id="dad1c-127">**눈 지원 위치**</span><span class="sxs-lookup"><span data-stu-id="dad1c-127">**Eye-Supported Positioning**</span></span>](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

<span data-ttu-id="dad1c-128">이 자습서에서는 이전 1980의 MIT 미디어 랩에서 눈에 잘 [맞는](https://youtu.be/CbIn8p4_4CQ) 음성 입력을 사용 하 여 연구 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-128">This tutorial shows an input scenario called [Put-That-There](https://youtu.be/CbIn8p4_4CQ) dating back to research from the MIT Media Lab in the early 1980's with eye, hand and voice input.</span></span>
<span data-ttu-id="dad1c-129">아이디어는 빠르게 목표를 선택 하 고 위치를 지정 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-129">The idea is simple: Benefit from your eyes for fast target selection and positioning.</span></span>
<span data-ttu-id="dad1c-130">홀로그램을 살펴보고 _' 배치 '_ 라고 표시 하 고, 배치 하려는 위치를 확인 하 고 _' 거기! '_ 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-130">Simply look at a hologram and say _'put this'_, look over where you want to place it and say _'there!'_.</span></span>
<span data-ttu-id="dad1c-131">홀로그램을 보다 정확 하 게 배치 하기 위해 직접, 음성 또는 컨트롤러에서 추가 입력을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-131">For more precisely positioning your hologram, you can use additional input from your hands, voice or controllers.</span></span>

<span data-ttu-id="dad1c-132">**요약**: 눈동자, 음성 및 직접 입력 (*끌어서 놓기*)을 사용 하 여 holograms을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-132">**Summary**: Positioning holograms using eyes, voice and hand input (*drag-and-drop*).</span></span> <span data-ttu-id="dad1c-133">눈 + 바늘을 사용 하는 눈에 잘 지는 슬라이더.</span><span class="sxs-lookup"><span data-stu-id="dad1c-133">Eye-supported sliders using eyes + hands.</span></span>

### <a name="visualization-of-visual-attention"></a><span data-ttu-id="dad1c-134">**시각적 주의 시각화**</span><span class="sxs-lookup"><span data-stu-id="dad1c-134">**Visualization of visual attention**</span></span>

<span data-ttu-id="dad1c-135">사용자의 모습을 기반으로 하는 데이터는 디자인의 유용성을 평가 하 고 효율적인 작업 스트림의 문제를 식별 하는 매우 강력한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-135">Data based on where users look makes an immensely powerful tool to assess usability of a design and to identify problems in efficient work streams.</span></span>
<span data-ttu-id="dad1c-136">이 자습서에서는 다양 한 눈 추적 시각화 및 여러 가지 요구 사항을 충족 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-136">This tutorial discusses different eye tracking visualizations and how they fit different needs.</span></span>
<span data-ttu-id="dad1c-137">눈 추적 데이터를 기록 하 고 로드 하기 위한 기본 예제와 이러한 데이터를 시각화 하는 방법에 대 한 예제를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-137">We provide basic examples for logging and loading eye tracking data and examples for how to visualize them.</span></span>

<span data-ttu-id="dad1c-138">**요약**: 슬레이트의 2 차원 주의 맵 (열 지도)</span><span class="sxs-lookup"><span data-stu-id="dad1c-138">**Summary**: Two-dimensional attention map (heatmaps) on slates.</span></span> <span data-ttu-id="dad1c-139">눈 추적 데이터를 재생 하 &를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-139">Recording & replaying eye tracking data.</span></span>

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a><span data-ttu-id="dad1c-140">MRTK 눈동자 추적 샘플 설정</span><span class="sxs-lookup"><span data-stu-id="dad1c-140">Setting up the MRTK eye tracking samples</span></span>

### <a name="prerequisites"></a><span data-ttu-id="dad1c-141">필수 조건</span><span class="sxs-lookup"><span data-stu-id="dad1c-141">Prerequisites</span></span>

<span data-ttu-id="dad1c-142">장치에서 눈 추적 샘플을 사용 하려면 패키지의 Appxmanifest.xml에 "응시 입력" 기능을 사용 하 여 빌드된 샘플 앱 패키지와 HoloLens 2가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-142">Note that using the eye tracking samples on device requires a HoloLens 2 and a sample app package that is built with the "Gaze Input" capability on the package's AppXManifest.</span></span>

<span data-ttu-id="dad1c-143">장치에서 이러한 눈 추적 샘플을 사용 하려면 Visual Studio에서 앱을 빌드하기 전에 [다음 단계](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) 를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-143">In order to use these eye tracking samples on device, make sure to follow [these steps](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) prior to building the app in Visual Studio.</span></span>

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a><span data-ttu-id="dad1c-144">1. Load EyeTrackingDemo-00-RootScene 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-144">1. Load EyeTrackingDemo-00-RootScene.unity</span></span>

<span data-ttu-id="dad1c-145">*EyeTrackingDemo-00-RootScene* 은 모든 코어 MRTK 구성 요소가 포함 된 기본 (_루트_) 장면입니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-145">The *EyeTrackingDemo-00-RootScene* is the base (_root_) scene that has all the core MRTK components included.</span></span>
<span data-ttu-id="dad1c-146">이는 먼저 로드 해야 하며, 눈 추적 데모를 실행 하는 장면입니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-146">This is the scene that you need to load first and from which you will run the eye tracking demos.</span></span>
<span data-ttu-id="dad1c-147">[추가로 업데이트할지 로드](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)되는 다양 한 눈 추적 샘플 간을 쉽게 전환할 수 있는 그래픽 장면 메뉴를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-147">It features a graphical scene menu that allows you to easily switch between the different eye tracking samples which will be [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).</span></span>

![눈 추적 샘플의 장면 메뉴](../images/eye-tracking/mrtk_et_scenemenu.jpg)

<span data-ttu-id="dad1c-149">루트 장면에는 MRTK 구성 된 프로필 및 장면 카메라와 같이 추가로 업데이트할지 로드 된 장면에서 지속 되는 몇 가지 핵심 구성 요소가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-149">The root scene includes a few core components that will persist across the additively loaded scenes, such as the MRTK configured profiles and scene camera.</span></span>
<span data-ttu-id="dad1c-150">_MixedRealityBasicSceneSetup_ (아래 스크린샷 참조)에는 시작 시 참조 된 장면을 자동으로 로드 하는 스크립트가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-150">The _MixedRealityBasicSceneSetup_ (see screenshot below) includes a script that will automatically load the referenced scene on startup.</span></span>
<span data-ttu-id="dad1c-151">기본적으로 _EyeTrackingDemo는 선택 사항_ 입니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-151">By default, this is _EyeTrackingDemo-02-TargetSelection_.</span></span>  

![OnLoadStartScene 스크립트의 예](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a><span data-ttu-id="dad1c-153">2. 빌드 메뉴에 장면 추가</span><span class="sxs-lookup"><span data-stu-id="dad1c-153">2. Adding scenes to the build menu</span></span>

<span data-ttu-id="dad1c-154">런타임 중에 추가 장면을 로드 하려면 빌드 _설정-빌드 메뉴의 > 장면_ 에 이러한 장면을 먼저 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-154">To load additive scenes during runtime, you must add these scenes to your _Build Settings -> Scenes in Build_ menu first.</span></span>
<span data-ttu-id="dad1c-155">루트 장면이 목록의 첫 번째 장면으로 표시 되는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-155">It is important that the root scene is shown as the first scene in the list:</span></span>

![빌드 설정 시각 추적 샘플에 대 한 장면 메뉴](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a><span data-ttu-id="dad1c-157">3. Unity 편집기에서 눈 추적 샘플 재생</span><span class="sxs-lookup"><span data-stu-id="dad1c-157">3. Play the eye tracking samples in the Unity editor</span></span>

<span data-ttu-id="dad1c-158">빌드 설정에 시각 추적 장면을 추가 하 고 _EyeTrackingDemo-00-rootscene_ 로드 한 후에는 마지막으로 확인할 수 있는 항목은 _MixedRealityBasicSceneSetup_ GameObject에 연결 된 _' onloadstartscene '_ 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-158">After adding the eye tracking scenes to the Build Settings and loading the _EyeTrackingDemo-00-RootScene_, there is one last thing you may want to check: Is the _'OnLoadStartScene'_ script that is attached to the _MixedRealityBasicSceneSetup_ GameObject enabled?</span></span> <span data-ttu-id="dad1c-159">이는 루트 장면에서 가장 먼저 로드할 데모 장면을 알 수 있도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-159">This is to let the root scene know which demo scene to load first.</span></span>

![OnLoad_StartScene 스크립트의 예](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

<span data-ttu-id="dad1c-161">시작합시다!</span><span class="sxs-lookup"><span data-stu-id="dad1c-161">Let's roll!</span></span> <span data-ttu-id="dad1c-162">_"Play"_!</span><span class="sxs-lookup"><span data-stu-id="dad1c-162">Hit _"Play"_!</span></span>
<span data-ttu-id="dad1c-163">여러 gem이 표시되고 장면 메뉴가 맨 위에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-163">You should see several gems appear and the scene menu at the top.</span></span>

![ET 대상 선택 장면의 샘플 스크린샷](../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="dad1c-165">또한 게임 보기의 가운데에 작은 반투명 원을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-165">You should also notice a small semitransparent circle at the center of your game view.</span></span>
<span data-ttu-id="dad1c-166">시뮬레이션된 _시선 응시의_ 표시기(커서) 역할을 합니다. 마우스 _오른쪽 단추를_ 누르고 마우스를 이동하여 위치를 변경하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-166">This acts as an indicator (cursor) of your _simulated eye gaze_: Simply press down the _right mouse button_ and move the mouse to change its position.</span></span>
<span data-ttu-id="dad1c-167">커서가 gem 위로 마우스를 가져가면 현재 본 gem의 가운데에 맞춰지는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-167">When the cursor is hovering over the gems, you will notice that it will snap to the center of the currently viewed gem.</span></span>
<span data-ttu-id="dad1c-168">이는 대상을 _"살펴볼"_ 때 이벤트가 예상대로 트리거되는지 테스트하는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-168">This is a great way to test if events are triggered as expected when _"looking"_ at a target.</span></span>
<span data-ttu-id="dad1c-169">마우스 컨트롤을 통한 _시뮬레이션된 시선 응시는_ 빠르고 의도하지 않은 시선 이동에 비해 다소 좋지 않은 보완입니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-169">Be aware that the _simulated eye gaze_ via mouse control is a rather poor supplement to our rapid and unintentional eye movements.</span></span>
<span data-ttu-id="dad1c-170">그러나 HoloLens 2 디바이스에 배포하여 디자인을 계속 진행하기 전에 기본 기능을 테스트하는 데 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-170">However, it is great for testing the basic functionality before iterating on the design by deploying it to the HoloLens 2 device.</span></span>
<span data-ttu-id="dad1c-171">시선 추적 샘플 장면으로 돌아가기: gem은 보고 있는 동안 회전하며 , 및 ...를 "보고"하여 소멸될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-171">Returning to our eye tracking sample scene: The gem rotates as long as being looked at and can be destroyed by "looking" at it and ...</span></span>

- <span data-ttu-id="dad1c-172">Enter 키를 누릅니다("select"라고 말하는 시뮬레이션) </span><span class="sxs-lookup"><span data-stu-id="dad1c-172">Pressing _Enter_ (which simulates saying "select")</span></span>
- <span data-ttu-id="dad1c-173">마이크에 _"select"라고_ 말</span><span class="sxs-lookup"><span data-stu-id="dad1c-173">Saying _"select"_ into your microphone</span></span>
- <span data-ttu-id="dad1c-174">_Space를_ 눌러 시뮬레이션된 손 입력을 표시하는 동안 마우스 왼쪽 단추를 클릭하여 시뮬레이션된 손가락 모으기를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-174">While pressing _Space_ to show the simulated hand input, click the left mouse button to perform a simulated pinch</span></span>

<span data-ttu-id="dad1c-175">[**시선 지원 대상 선택**](../input/eye-tracking/eye-tracking-target-selection.md) 자습서에서 이러한 상호 작용을 달성할 수 있는 방법을 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-175">We describe in more detail how you can achieve these interactions in our [**Eye-Supported Target Selection**](../input/eye-tracking/eye-tracking-target-selection.md) tutorial.</span></span>

<span data-ttu-id="dad1c-176">장면의 위쪽 메뉴 모음까지 커서를 이동하면 현재 마우스로 가리킨 항목이 부분적으로 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-176">When moving the cursor up to the top menu bar in the scene, you will notice that the currently hovered item will highlight subtly.</span></span>
<span data-ttu-id="dad1c-177">위에서 설명한 커밋 방법 중 하나를 사용하여 현재 강조 표시된 항목을 선택할 수 있습니다(예: Enter 키를 _누른_ 경우).</span><span class="sxs-lookup"><span data-stu-id="dad1c-177">You can select the currently highlighted item by using one of the above described commit methods (e.g., pressing _Enter_).</span></span>
<span data-ttu-id="dad1c-178">이렇게 하면 다양한 시선 추적 샘플 장면 간에 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-178">This way you can switch between the different eye tracking sample scenes.</span></span>

### <a name="4-how-to-test-specific-sub-scenes"></a><span data-ttu-id="dad1c-179">4. 특정 하위 장면을 테스트하는 방법</span><span class="sxs-lookup"><span data-stu-id="dad1c-179">4. How to test specific sub scenes</span></span>

<span data-ttu-id="dad1c-180">특정 시나리오에서 작업하는 경우 매번 장면 메뉴를 거치지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-180">When working on a specific scenario, you may not want to go through the scene menu every time.</span></span>
<span data-ttu-id="dad1c-181">대신 _재생_ 단추를 누를 때 현재 작업 중인 장면에서 직접 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-181">Instead, you may want to start directly from the scene that you are currently working on when pressing the _Play_ button.</span></span>
<span data-ttu-id="dad1c-182">문제없습니다!</span><span class="sxs-lookup"><span data-stu-id="dad1c-182">No problem!</span></span> <span data-ttu-id="dad1c-183">수행할 수 있는 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-183">Here is what you can do:</span></span>

1. <span data-ttu-id="dad1c-184">_루트_ 장면 로드</span><span class="sxs-lookup"><span data-stu-id="dad1c-184">Load the _root_ scene</span></span>
2. <span data-ttu-id="dad1c-185">_루트_ 장면에서 _' Onloadstartscene '_ 스크립트를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-185">In the _root_ scene, disable the _'OnLoadStartScene'_ script</span></span>
3. <span data-ttu-id="dad1c-186">아래 스크린샷에 표시 된 것 처럼 아래에 설명 된 시각 추적 테스트 장면 중 하나 (또는 다른 장면)를 _계층_ 뷰에 _끌어_ 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-186">_Drag and drop_ one of the eye tracking test scenes that are described below (or any other scene) into your _Hierarchy_ view as shown in the screenshot below.</span></span>

    ![추가 장면의 예](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. <span data-ttu-id="dad1c-188">_Play_ 누르기</span><span class="sxs-lookup"><span data-stu-id="dad1c-188">Press _Play_</span></span>

<span data-ttu-id="dad1c-189">이와 같은 하위 장면을 로드 하는 것은 영구적이 지 않습니다. 즉, 앱을 HoloLens 2 장치에 배포 하는 경우 루트 장면이 로드 됩니다 (빌드 설정의 맨 위에 표시 된다고 가정).</span><span class="sxs-lookup"><span data-stu-id="dad1c-189">Please note that loading the sub scene like this is not persistent: This means that if you deploy your app to the HoloLens 2 device, it will only load the root scene (assuming it appears at the top of your Build Settings).</span></span>
<span data-ttu-id="dad1c-190">또한 프로젝트를 다른 사용자와 공유 하는 경우에는 하위 장면이 자동으로 로드 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dad1c-190">Also, when you share your project with others, the sub scenes are not automatically loaded.</span></span>

---

<span data-ttu-id="dad1c-191">이제 MRTK 눈 추적 예제 장면을 작업 하는 방법을 배웠으므로 이제 눈에 holograms를 선택 하는 방법에 대 한 자세한 내용을 계속 살펴보겠습니다. [눈에 잘 지 원하는 대상 선택](../input/eye-tracking/eye-tracking-target-selection.md)</span><span class="sxs-lookup"><span data-stu-id="dad1c-191">Now that you know how to get the MRTK eye tracking example scenes to work, let's continue with diving deeper into how to select holograms with your eyes: [Eye-supported target selection](../input/eye-tracking/eye-tracking-target-selection.md).</span></span>

---
[<span data-ttu-id="dad1c-192">"MixedRealityToolkit의 눈동자 추적"으로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="dad1c-192">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](../input/eye-tracking/eye-tracking-Main.md)
