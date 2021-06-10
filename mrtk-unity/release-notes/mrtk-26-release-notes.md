---
title: MRTK 2.6 릴리스 정보
description: MRTK 버전 2.6의 릴리스 정보
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 4ac82f7e07135e840886fef810844ff00ef1ac1e
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647187"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a><span data-ttu-id="44376-104">Microsoft Mixed Reality Toolkit 2.6 릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="44376-104">Microsoft Mixed Reality Toolkit 2.6 Release Notes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="44376-105">ARM64를 사용하여 Microsoft HoloLens 2용으로 빌드된 애플리케이션에 영향을 주는 알려진 컴파일러 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-105">There is a known compiler issue that impacts applications built for Microsoft HoloLens 2 using ARM64.</span></span> <span data-ttu-id="44376-106">이 문제는 Visual Studio 2019를 버전 16.8 이상으로 업데이트하여 해결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-106">This issue is fixed by updating Visual Studio 2019 to version 16.8 or later.</span></span> <span data-ttu-id="44376-107">Visual Studio 업데이트할 수 없는 경우 패키지를 `com.microsoft.mixedreality.toolkit.tools` 가져와서 해결 방법을 적용하세요.</span><span class="sxs-lookup"><span data-stu-id="44376-107">If you are unable to update Visual Studio, please import the `com.microsoft.mixedreality.toolkit.tools` package to apply a workaround.</span></span>

## <a name="whats-new-in-262"></a><span data-ttu-id="44376-108">2.6.2의 새로운 내용</span><span class="sxs-lookup"><span data-stu-id="44376-108">What's new in 2.6.2</span></span>

### <a name="corrects-parenting-of-the-spatial-mesh"></a><span data-ttu-id="44376-109">공간 메시의 부모링을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-109">Corrects parenting of the spatial mesh</span></span>

<span data-ttu-id="44376-110">Mixed Reality Playspace 개체가 이동된 후 공간 메시가 제대로 배치되지 않는 [문제를](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) 해결합니다(예: 원격 포트를 통해).</span><span class="sxs-lookup"><span data-stu-id="44376-110">Fixes the [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) where spatial meshes were not being properly located after the Mixed Reality Playspace object was moved (ex: via a teleport).</span></span>

## <a name="whats-new-in-261"></a><span data-ttu-id="44376-111">2.6.1의 새로운 내용</span><span class="sxs-lookup"><span data-stu-id="44376-111">What's new in 2.6.1</span></span>

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a><span data-ttu-id="44376-112">HoloLens 2/UWP에서 실행되지 않는 OpenXR 수정</span><span class="sxs-lookup"><span data-stu-id="44376-112">Fixes OpenXR not running on HoloLens 2 / UWP</span></span>

<span data-ttu-id="44376-113">MRTK의 OpenXR 지원이 UWP에서 실행되지 않도록 하는 회귀를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-113">Fixes a regression that prevented MRTK's OpenXR support from running on UWP.</span></span>

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a><span data-ttu-id="44376-114">Leap Motion ObjectManipulator가 회전하지 않는 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-114">Fixes Leap Motion ObjectManipulator not rotating</span></span>

<span data-ttu-id="44376-115">ObjectManipulator 스크립트에서 Leap Motion 손의 회전을 고려하지 않은 회귀를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-115">Fixes a regression where a Leap Motion hand's rotation was not taken into account by the ObjectManipulator script.</span></span>

### <a name="sample-scene-updates"></a><span data-ttu-id="44376-116">샘플 장면 업데이트</span><span class="sxs-lookup"><span data-stu-id="44376-116">Sample scene updates</span></span>

<span data-ttu-id="44376-117">Unity 플러그 인의 제공된 상태를 올바르게 반영하도록 장면 이해 샘플 장면을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-117">Updates the scene understanding sample scene to correctly reflect the shipped state of the Unity plugin.</span></span> <span data-ttu-id="44376-118">또한 가져오는 공간 인식 샘플 장면에 더 이상 종속되지 않도록 샘플을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-118">Also updates the sample to no longer have a dependency on the spatial awareness sample scene being imported.</span></span> <span data-ttu-id="44376-119">2.6.1로 업데이트하기 전에 가져온 장면 이해 및 공간 인식 샘플이 가능한 충돌을 방지하기 위해 프로젝트에 있는 경우 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-119">Before updating to 2.6.1 you should delete the imported scene understanding and spatial awareness samples if they are present in your project to avoid possible conflicts.</span></span> <span data-ttu-id="44376-120">이러한 샘플을 제거하지 않고 콘솔의 샘플과 관련된 충돌이 표시되는 경우 샘플(또는 `Assets/Samples/Mixed Reality Toolkit Examples` 폴더)을 모두 제거한 다음 다시 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="44376-120">If you did not remove those samples and do see conflicts related to those in the console, please remove both samples (or the `Assets/Samples/Mixed Reality Toolkit Examples` folder) and then try importing again.</span></span>

<span data-ttu-id="44376-121">대화 예제 장면을 업데이트하여 현재 대화 시나리오를 올바르게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-121">Updates the dialog example scene to correctly describe the current dialog scenarios.</span></span>

## <a name="whats-new-in-260"></a><span data-ttu-id="44376-122">2.6.0의 새로운 내용</span><span class="sxs-lookup"><span data-stu-id="44376-122">What's new in 2.6.0</span></span>
<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a><span data-ttu-id="44376-123">OpenXR에 대한 지원 추가</span><span class="sxs-lookup"><span data-stu-id="44376-123">Add support for OpenXR</span></span>

<span data-ttu-id="44376-124">Unity의 OpenXR 미리 보기 패키지 및 Microsoft의 Mixed Reality OpenXR 패키지에 대한 초기 지원이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-124">Initial support for Unity's OpenXR preview package and Microsoft's Mixed Reality OpenXR package has been added.</span></span> <span data-ttu-id="44376-125">자세한 내용은 [MRTK/XRSDK 시작 페이지,](../configuration/getting-started-with-mrtk-and-xrsdk.md) [Unity의 포럼 게시물](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)또는 [Microsoft 설명서를 참조하세요.](/windows/mixed-reality/develop/unity/openxr-getting-started)</span><span class="sxs-lookup"><span data-stu-id="44376-125">See [the MRTK/XRSDK getting started page](../configuration/getting-started-with-mrtk-and-xrsdk.md), [Unity's forum post](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/), or [Microsoft's documentation](/windows/mixed-reality/develop/unity/openxr-getting-started) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="44376-126">Unity의 OpenXR은 Unity 2020.2 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="44376-126">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="44376-127">현재 x64 및 ARM64 빌드만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-127">Currently, it also only supports x64 and ARM64 builds.</span></span>

### <a name="asset-swap-utility"></a><span data-ttu-id="44376-128">자산 교환 유틸리티</span><span class="sxs-lookup"><span data-stu-id="44376-128">Asset swap utility</span></span>

<span data-ttu-id="44376-129">Unity 장면의 여러 자산을 새 [Asset Swap 유틸리티](../features/tools/asset-swap-utility.md)로 교환합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-129">Swap multiple assets in a Unity scene with the new [Asset Swap utility](../features/tools/asset-swap-utility.md).</span></span>

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a><span data-ttu-id="44376-130">이제 MRTK에서 HP 모션 컨트롤러 지원</span><span class="sxs-lookup"><span data-stu-id="44376-130">HP Motion Controllers now supported with MRTK</span></span>

<span data-ttu-id="44376-131">HP Reverb G2용 컨트롤러는 이제 MRTK에서 기본적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-131">Controllers for the HP Reverb G2 now work natively with MRTK.</span></span>

### <a name="experimental-interactive-element--state-visualizer"></a><span data-ttu-id="44376-132">실험적 대화형 요소 + 상태 시각화 도우미</span><span class="sxs-lookup"><span data-stu-id="44376-132">Experimental Interactive Element + State Visualizer</span></span>

<span data-ttu-id="44376-133">Interactive Element는 MRTK 입력 시스템에 대한 간소화된 중앙 집중식 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="44376-133">Interactive Element is a simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="44376-134">여기에는 상태 관리 메서드, 이벤트 관리 및 핵심 상호 작용 상태에 대한 상태 설정 논리가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="44376-134">It contains state management methods, event management and the state setting logic for Core Interaction States.</span></span> <span data-ttu-id="44376-135">자세한 내용은 [Interactive 요소 설명서를 참조하세요.](../features/experimental/interactive-element.md)</span><span class="sxs-lookup"><span data-stu-id="44376-135">For more information see [Interactive Element Documentation](../features/experimental/interactive-element.md).</span></span>

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

<span data-ttu-id="44376-137">상태 시각화 도우미는 Interactive 요소에 의존하는 애니메이션 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="44376-137">The State Visualizer is an animation component that depends on Interactive Element.</span></span>  <span data-ttu-id="44376-138">이 구성 요소는 애니메이션 클립을 만들고, 키 프레임을 설정하고, Animator 상태 컴퓨터를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-138">This component creates Animation Clips, sets keyframes and generates an Animator State Machine.</span></span> <span data-ttu-id="44376-139">자세한 내용은 [상태 시각화 도우미 설명서를 참조하세요.](../features/experimental/interactive-element.md#state-visualizer-experimental)</span><span class="sxs-lookup"><span data-stu-id="44376-139">For more information see [State Visualizer Documentation](../features/experimental/interactive-element.md#state-visualizer-experimental)</span></span>

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a><span data-ttu-id="44376-141">이제 모든 플랫폼에서 원격 포트 제스처를 통해 원격 보고가 지원됨</span><span class="sxs-lookup"><span data-stu-id="44376-141">Teleportation with the teleport gesture now supported on all platforms</span></span>

<span data-ttu-id="44376-142">이제 사용자는 원격 이동 제스처를 사용하여 모든 플랫폼에서 재생 공간을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-142">Users can now use the teleport gesture to move around their play space across all platforms.</span></span> <span data-ttu-id="44376-143">기본 구성을 사용하여 MR 디바이스에서 컨트롤러와 원격 통신하려면 엄지스틱을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-143">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="44376-144">굴절된 손으로 원격 이동하려면 손끝이 인덱스 및 엄지 손가락으로 바깥쪽을 향하도록 제스처를 만들고, 인덱스 손가락으로 말려서 원격 통신을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-144">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="44376-145">입력 시뮬레이션을 사용하여 원격 전송하려면 업데이트된 [입력 시뮬레이션 서비스 설명서를](../features/input-simulation/input-simulation-service.md)참조하세요.</span><span class="sxs-lookup"><span data-stu-id="44376-145">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../features/input-simulation/input-simulation-service.md).</span></span>

  ![원격 이동 제스처](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a><span data-ttu-id="44376-147">이제 MRTK에서 실험적 공간 인식 관찰자로 장면 이해 사용 가능</span><span class="sxs-lookup"><span data-stu-id="44376-147">Scene Understanding now available in MRTK as an experimental spatial awareness observer</span></span>

<span data-ttu-id="44376-148">[Scene Understanding의](/windows/mixed-reality/scene-understanding) 실험적 지원은 MRTK 2.6에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-148">Experimental support of [Scene Understanding](/windows/mixed-reality/scene-understanding) is introduced in MRTK 2.6.</span></span> <span data-ttu-id="44376-149">사용자는 MRTK 기반 프로젝트에서 공간 인식 관찰자로 HoloLens 2 장면 이해 기능을 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-149">Users can incorporate the scene understanding capabilities of HoloLens 2 as a spatial awareness observer in MRTK based projects.</span></span> <span data-ttu-id="44376-150">자세한 내용은 [Scene Understanding 설명서를](../features/spatial-awareness/scene-understanding.md) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="44376-150">Please read the [Scene Understanding documentation](../features/spatial-awareness/scene-understanding.md) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="44376-151">Scene Understanding은 HoloLens 2 및 Unity 2019.4 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="44376-151">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>
>
> <span data-ttu-id="44376-152">이 기능을 사용하려면 [이제 Mixed Reality 기능 도구를](https://aka.ms/MRFeatureTool)통해 사용할 수 있는 Scene Understanding 패키지가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-152">This feature requires the Scene Understanding package, which is now available via the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>
> <span data-ttu-id="44376-153">Mixed Reality 기능 도구를 사용하거나 UPM을 통해 가져오는 경우 종속성 문제로 인한 실험적 - 장면해결 샘플을 가져오기 전에 Demos - SpatialAwareness 샘플을 가져오세요.</span><span class="sxs-lookup"><span data-stu-id="44376-153">When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="44376-154">자세한 내용은 [이 GitHub 문제를](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="44376-154">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

  ![장면 이해](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a><span data-ttu-id="44376-156">런타임 프로필 전환 지원</span><span class="sxs-lookup"><span data-stu-id="44376-156">Runtime profile switching support</span></span>

<span data-ttu-id="44376-157">MRTK는 이제 MRTK 인스턴스를 초기화하기 전(예: MRTK 초기화 프로필 전환 전) 및 프로필이 활성 사용 중이 된 후(즉, 활성 프로필 스위치) 모두에 프로필 전환을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-157">MRTK now allows profile switching both before the initialization of the MRTK instance (i.e. Pre MRTK initialization profile switch) and after a profile has been in active use (i.e. Active profile switch).</span></span> <span data-ttu-id="44376-158">이전 스위치는 하드웨어의 기능에 따라 선택 구성 요소를 사용하도록 설정하는 데 사용할 수 있으며, 후자는 사용자가 애플리케이션의 하위 부분을 입력할 때 환경을 수정하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-158">The former switch can be used to enable select components based on capabilities of the hardware, while the latter can be used to modify experience as the user enters a subpart of the application.</span></span> <span data-ttu-id="44376-159">자세한 내용 및 코드 [샘플은 프로필 전환에](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) 대한 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="44376-159">Please read the [documentation on profile switching](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) for more information and code samples.</span></span>

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a><span data-ttu-id="44376-160">실험에서 퇴사한 방향 표시기 및 팔로우 해결기</span><span class="sxs-lookup"><span data-stu-id="44376-160">Directional indicator and follow solvers graduated from experimental</span></span>

<span data-ttu-id="44376-161">두 개의 새 해결기를 주선 MRTK와 함께 사용할 준비가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-161">Two new solvers are ready for use with mainline MRTK.</span></span>

  ![방향 표시기 해결기](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a><span data-ttu-id="44376-163">손 감독과 실험적 승부</span><span class="sxs-lookup"><span data-stu-id="44376-163">Hand Coach graduated from experimental</span></span>

<span data-ttu-id="44376-164">이제 손 감독 기능이 주선 MRTK와 함께 사용할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-164">The Hand Coach feature is now ready for use with mainline MRTK.</span></span>
  <span data-ttu-id="44376-165">![손 감독 예제](/windows/mixed-reality/design/images/handcoach/airtap.gif)</span><span class="sxs-lookup"><span data-stu-id="44376-165">![Hand Coach Example](/windows/mixed-reality/design/images/handcoach/airtap.gif)</span></span>

### <a name="dialog-controls-graduated-from-experimental"></a><span data-ttu-id="44376-166">실험적 대화 상자 컨트롤</span><span class="sxs-lookup"><span data-stu-id="44376-166">Dialog controls graduated from experimental</span></span>

<span data-ttu-id="44376-167">이제 대화 상자 컨트롤을 주선 MRTK와 함께 사용할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-167">Dialog controls are now ready for use with mainline MRTK.</span></span>

  ![대화 상자 컨트롤](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a><span data-ttu-id="44376-169">실험적에서 펄스 셰이더가 분리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-169">Pulse shader graduated from experimental</span></span>

<span data-ttu-id="44376-170">펄스 셰이더 스크립트는 실험적 스크립트에서 제외되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-170">The Pulse shader scripts have graduated from experimental.</span></span> <span data-ttu-id="44376-171">자세한 내용은 [펄스 셰이더 설명서를 참조하세요.](../features/rendering/pulse-shader.md)</span><span class="sxs-lookup"><span data-stu-id="44376-171">For more information see: [Pulse Shader Documentation](../features/rendering/pulse-shader.md)</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a><span data-ttu-id="44376-173">입력 기록 서비스 개선</span><span class="sxs-lookup"><span data-stu-id="44376-173">Input Recording Service improvements</span></span>

<span data-ttu-id="44376-174">`InputRecordingService` 이제 및 `InputPlaybackService` 는 시선 응시 입력을 기록하고 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-174">`InputRecordingService` and `InputPlaybackService` can now record and play back eye gaze input.</span></span> <span data-ttu-id="44376-175">기록 파일 크기 및 저장 시간도 약 50% 줄이면서 기록 기간 동안 일관된 프레임 속도 보장을 위해 녹화가 최적화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-175">Recording has been optimized to ensure a consistent framerate throughout the recording period while recording file size and save time are also reduced by about 50%.</span></span> <span data-ttu-id="44376-176">이제 기록 파일의 저장 및 로드를 비동기적으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-176">Saving and loading of recording files can now be performed asynchronously.</span></span> <span data-ttu-id="44376-177">이 MRTK 버전에서 기록의 파일 형식이 변경되었습니다. 새 버전 1.1 사양에 대한 자세한 내용은 [여기를](../features/input-simulation/input-animation-file-format.md) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="44376-177">Note the file format of the recording has changed in this MRTK version, please see [here](../features/input-simulation/input-animation-file-format.md) for more information on the new version 1.1 specifications.</span></span>

### <a name="reading-mode"></a><span data-ttu-id="44376-178">읽기 모드</span><span class="sxs-lookup"><span data-stu-id="44376-178">Reading mode</span></span>

<span data-ttu-id="44376-179">HoloLens 2 [읽기 모드에](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) 대한 지원이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-179">Added support for [reading mode](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) on HoloLens 2.</span></span> <span data-ttu-id="44376-180">읽기 모드는 시스템의 보기 필드를 줄이지만 Unity 출력의 크기 조정은 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-180">Reading mode reduces the system's field of view but eliminates a scaling of Unity's output.</span></span> <span data-ttu-id="44376-181">Unity에서 렌더링된 픽셀은 HoloLens 2 프로젝션된 픽셀에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-181">A pixel rendered by Unity will correspond to a projected pixel on HoloLens 2.</span></span> <span data-ttu-id="44376-182">애플리케이션 작성자는 여러 개인과 함께 테스트를 수행하여 앱에서 이 절충이 절충되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-182">Application authors should do tests with multiple individuals to be sure this is a tradeoff they want in their app.</span></span>

  ![Windows Mixed Reality 읽기 모드](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a><span data-ttu-id="44376-184">UWP에서 3D 앱 시작 관리자 지원</span><span class="sxs-lookup"><span data-stu-id="44376-184">Support for 3D app launchers on UWP</span></span>

<span data-ttu-id="44376-185">UWP용 [3D 앱 시작 관리자를](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 설정하는 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-185">Adds the ability to set a [3D app launcher](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for UWP.</span></span> <span data-ttu-id="44376-186">이 설정은 MRTK 빌드 창과 MRTK 프로젝트 설정의 빌드 설정에서 모두 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="44376-186">This setting is exposed both in the MRTK Build Window and the MRTK Project Settings, under Build Settings.</span></span> <span data-ttu-id="44376-187">Unity에서 빌드하는 동안 프로젝트에 자동으로 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="44376-187">It's automatically written into the project during the build in Unity.</span></span>

  ![빌드 설정](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a><span data-ttu-id="44376-189">주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="44376-189">Breaking changes</span></span>

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a><span data-ttu-id="44376-190">가져온 GLTF 개체의 특정 필드가 이제 대문자로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44376-190">Certain fields of imported GLTF objects are now capitalized</span></span>

<span data-ttu-id="44376-191">deserialization 관련 문제로 인해 가져온 GLTF 개체의 일부 필드가 이제 대문자로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-191">Due to deserialization related issues some fields of imported GLTF objects are now starting with capital letters.</span></span> <span data-ttu-id="44376-192">영향을 받는 필드는 (새 이름에 있음): `ComponentType` , , , , , , , , , `Path` , `Interpolation` `Target` `Type` `Mode` `MagFilter` `MinFilter` `WrapS` `WrapT` 입니다.</span><span class="sxs-lookup"><span data-stu-id="44376-192">The affected fields are (in their new names): `ComponentType`, `Path`, `Interpolation`, `Target`, `Type`, `Mode`, `MagFilter`, `MinFilter`, `WrapS`, `WrapT`.</span></span>

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a><span data-ttu-id="44376-193">입력 애니메이션 이진 파일의 버전 1.1 형식이 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-193">Input animation binary file has an updated version 1.1 format</span></span>

<span data-ttu-id="44376-194">및 에서 사용하는 입력 애니메이션 이진 `InputRecordingService` `InputPlaybackService` 파일에는 이제 이러한 두 서비스에 대한 최적화를 사용할 수 있도록 업데이트된 파일 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-194">Input animation binary file, used by `InputRecordingService` and `InputPlaybackService`, now has an updated file format to enable the optimizations made to those two services.</span></span> <span data-ttu-id="44376-195">새 버전 1.1 사양에 대한 자세한 내용은 [여기를](../features/input-simulation/input-animation-file-format.md) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="44376-195">Please see [here](../features/input-simulation/input-animation-file-format.md) for more information on the new version 1.1 specifications.</span></span>

### <a name="msbuild-for-unity-support"></a><span data-ttu-id="44376-196">Unity용 MSBuild 지원</span><span class="sxs-lookup"><span data-stu-id="44376-196">MSBuild for Unity support</span></span>

<span data-ttu-id="44376-197">Unity용 MSBuild에 대한 지원은 [Unity의 새 패키지 지침](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)에 맞게 2.5.2 릴리스부터 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-197">Support for MSBuild for Unity has been removed as of the 2.5.2 release, to align with [Unity's new package guidance](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span></span>

## <a name="known-issues"></a><span data-ttu-id="44376-198">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="44376-198">Known issues</span></span>

### <a name="openxr"></a><span data-ttu-id="44376-199">OpenXR</span><span class="sxs-lookup"><span data-stu-id="44376-199">OpenXR</span></span>

<span data-ttu-id="44376-200">현재 홀로그램 Remoting 및 OpenXR에는 손합을 일관되게 사용할 수 없는 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-200">There's currently a known issue with Holographic Remoting and OpenXR, where hand joints aren't consistently available.</span></span>
<span data-ttu-id="44376-201">또한 눈 추적 샘플 장면은 현재 호환 되지 않습니다. 단, 눈 추적이 *작동 합니다* .</span><span class="sxs-lookup"><span data-stu-id="44376-201">Additionally, the eye tracking sample scenes aren't currently compatible, though eye tracking *does* work.</span></span>

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a><span data-ttu-id="44376-202">일부 혼합 현실 도구 키트 표준 셰이더 기능에는 기본 패키지가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-202">Some Mixed Reality Toolkit Standard Shader features require the Foundation package</span></span>

<span data-ttu-id="44376-203">Unity 패키지 관리자를 통해 가져올 때 MRTK 표준 셰이더 유틸리티 스크립트 (예: HoverLight)는 표준 자산 패키지의 셰이더와 함께 배치 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-203">When imported via the Unity Package Manager, the MRTK Standard Shader utilities scripts (ex: HoverLight.cs) are not co-located with the shader in the Standard Assets package.</span></span> <span data-ttu-id="44376-204">이 기능에 액세스 하려면 응용 프로그램에 기반 패키지를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-204">To access this functionality, applications will require the Foundation package to be imported.</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="44376-205">CameraCache는 종료 시 새 카메라를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-205">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="44376-206">일부 상황에서 (예: Unity 편집기에서 LeapMotion 공급자를 사용 하는 경우) CameraCache가 종료 시 MainCamera를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-206">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="44376-207">자세한 내용은 [이 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="44376-207">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="44376-208">Unity 패키지 관리자를 통해 예제를 가져오는 경우 System.io.filenotfoundexception</span><span class="sxs-lookup"><span data-stu-id="44376-208">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="44376-209">프로젝트 경로의 길이에 따라 Unity 패키지 관리자를 통해 예제를 가져오면 Unity 콘솔에서 System.io.filenotfoundexception 메시지가 생성 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-209">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="44376-210">이 오류의 원인은 MAX_PATH (256 자) 보다 긴 "누락 된" 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="44376-210">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="44376-211">해결 하려면 프로젝트 경로의 길이를 줄이십시오.</span><span class="sxs-lookup"><span data-stu-id="44376-211">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="44376-212">Spatializer가 지정 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-212">No spatializer was specified.</span></span> <span data-ttu-id="44376-213">응용 프로그램에서 공간 소리를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-213">The application will not support Spatial Sound</span></span>

<span data-ttu-id="44376-214">오디오 spatializer 구성 되지 않은 경우 "No spatializer가 지정 되었습니다." 경고가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44376-214">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="44376-215">XR 패키지를 설치 하지 않은 경우에 이러한 문제가 발생할 수 있습니다. Unity는 이러한 패키지에 spatializers를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-215">This can occur if no XR package is installed, as Unity includes spatializers in these packages.</span></span>

<span data-ttu-id="44376-216">이 문제를 해결 하려면 다음을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="44376-216">To resolve, please ensure that:</span></span>

- <span data-ttu-id="44376-217">**창**  >  **패키지 관리자** 에 XR 패키지가 하나 이상 설치 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-217">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="44376-218">**Mixed Reality Toolkit**  >  **유틸리티**  >  **Unity 프로젝트를 구성** 하 고 **오디오 Spatializer** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-218">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![오디오 Spatializer 선택](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="44376-220">NullReferenceException: 개체 참조가 개체의 인스턴스로 설정 되지 않았습니다 (SceneTransitionService.Initialize).</span><span class="sxs-lookup"><span data-stu-id="44376-220">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="44376-221">경우에 따라를 열면 `EyeTrackingDemo-00-RootScene` SceneTransitionService 클래스의 Initialize 메서드에서 NullReferenceException이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-221">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="44376-222">이 오류는 장면 전환 서비스의 구성 프로필이 설정 되어 있지 않기 때문에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-222">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="44376-223">해결 하려면 다음 단계를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="44376-223">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="44376-224">`MixedRealityToolkit`계층의 개체로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-224">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="44376-225">검사기 창에서 다음을 선택 합니다. `Extensions`</span><span class="sxs-lookup"><span data-stu-id="44376-225">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="44376-226">확장 되지 않은 경우 확장 합니다. `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="44376-226">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="44376-227">의 값을 `Configuration Profile` **MRTKExamplesHubSceneTransitionServiceProfile** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-227">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

![장면 전환 프로필 수정](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a><span data-ttu-id="44376-229">Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="44376-229">Oculus Quest</span></span>

<span data-ttu-id="44376-230">현재 [독립 실행형 플랫폼을 대상으로 하는 경우에서 Oculus XR 플러그 인](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)을 사용 하는 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-230">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span>  <span data-ttu-id="44376-231">업데이트에 대 한 Oculus 버그 추적기/포럼/릴리스 정보를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="44376-231">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="44376-232">이 세 가지 오류 집합을 사용 하 여 버그를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="44376-232">The bug is signified with this set of 3 errors:</span></span>

![Oculus XR 플러그 인 오류](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="44376-234">UnityUI 및 TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="44376-234">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="44376-235">최신 버전의 TextMeshPro (1.5.0 + 또는 2.1.1 +)에 대 한 알려진 문제는 드롭다운의 기본 글꼴 크기와 굵은 글꼴 문자 간격이 변경 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="44376-235">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![TMP 이미지](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="44376-237">이 작업은 이전 버전의 TextMeshPro으로 다운 그레이드 하 여 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44376-237">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="44376-238">자세한 내용은 [문제 #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="44376-238">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>