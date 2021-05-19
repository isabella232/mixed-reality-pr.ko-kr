---
title: 입력 시뮬레이션 서비스
description: MRTK의 입력 시뮬레이션 서비스에 대한 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 81e7dcab7e0f349d05521f93d75bba6927761fd1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145090"
---
# <a name="input-simulation-service"></a><span data-ttu-id="41b3a-104">입력 시뮬레이션 서비스</span><span class="sxs-lookup"><span data-stu-id="41b3a-104">Input simulation service</span></span>

<span data-ttu-id="41b3a-105">입력 시뮬레이션 서비스는 Unity 편집기에서 사용할 수 없는 디바이스 및 플랫폼의 동작을 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-105">The Input Simulation Service emulates the behavior of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="41b3a-106">다음은 이러한 템플릿의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-106">Examples include:</span></span>

* <span data-ttu-id="41b3a-107">HoloLens 또는 VR 디바이스 헤드 추적</span><span class="sxs-lookup"><span data-stu-id="41b3a-107">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="41b3a-108">HoloLens 손 제스처</span><span class="sxs-lookup"><span data-stu-id="41b3a-108">HoloLens hand gestures</span></span>
* <span data-ttu-id="41b3a-109">HoloLens 2 전달된 손 추적</span><span class="sxs-lookup"><span data-stu-id="41b3a-109">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="41b3a-110">시선 추적 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="41b3a-110">HoloLens 2 eye tracking</span></span>
* <span data-ttu-id="41b3a-111">VR 디바이스 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="41b3a-111">VR device controllers</span></span>

<span data-ttu-id="41b3a-112">사용자는 기존 키보드와 마우스 조합을 사용하여 런타임에 시뮬레이션된 디바이스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-112">Users can use a conventional keyboard and mouse combination to control simulated devices at runtime.</span></span> <span data-ttu-id="41b3a-113">이 방법을 사용하면 먼저 디바이스에 배포하지 않고 Unity 편집기에서 상호 작용을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-113">This approach allows testing of interactions in the Unity editor without first deploying to a device.</span></span>

> [!WARNING]
> <span data-ttu-id="41b3a-114">Unity의 XR 홀로그램 에뮬레이션 > 에뮬레이션 모드 = "편집기에서 시뮬레이트"를 사용하는 경우에는 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-114">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="41b3a-115">Unity의 편집기 내 시뮬레이션은 MRTK의 입력 시뮬레이션에서 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-115">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="41b3a-116">MRTK 입력 시뮬레이션 서비스를 사용하려면 XR 홀로그램 에뮬레이션을 에뮬레이션 모드 = *"없음"으로* 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-116">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="41b3a-117">입력 시뮬레이션 서비스 사용</span><span class="sxs-lookup"><span data-stu-id="41b3a-117">Enabling the input simulation service</span></span>

<span data-ttu-id="41b3a-118">입력 시뮬레이션은 MRTK와 함께 제공된 프로필에서 기본적으로 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-118">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span>

<span data-ttu-id="41b3a-119">입력 시스템 데이터 공급자 구성에서 입력 시뮬레이션 서비스를 다음으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-119">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="41b3a-120">**형식은** *Microsoft.MixedReality.Toolkit.Input > InputSimulationService* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-120">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="41b3a-121">서비스에서 키보드 및 마우스 입력을 사용하므로 **기본적으로 지원되는 플랫폼에는** 모든 *편집기* 플랫폼이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-121">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="41b3a-122">원하는 대상을 포함하도록 **지원되는** 플랫폼 속성을 변경하여 독립 실행형과 같은 다른 플랫폼 엔드포인트에서 입력 시뮬레이션 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-122">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <span data-ttu-id="41b3a-123">![입력 시뮬레이션 지원 플랫폼](../images/input-simulation/InputSimulationSupportedPlatforms.gif)</span><span class="sxs-lookup"><span data-stu-id="41b3a-123">![Input Simulation Supported Platforms](../images/input-simulation/InputSimulationSupportedPlatforms.gif)</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="41b3a-124">입력 시뮬레이션 도구 창</span><span class="sxs-lookup"><span data-stu-id="41b3a-124">Input simulation tools window</span></span>

<span data-ttu-id="41b3a-125">**혼합 현실 도구 키트**  >  **유틸리티**  >  **입력 시뮬레이션** 메뉴에서 입력 시뮬레이션 도구 창을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-125">Enable the input simulation tools window from the  **Mixed Reality Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="41b3a-126">이 창에서는 재생 모드 동안 입력 시뮬레이션의 상태에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-126">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons"></a><span data-ttu-id="41b3a-127">뷰포트 단추</span><span class="sxs-lookup"><span data-stu-id="41b3a-127">Viewport buttons</span></span>

<span data-ttu-id="41b3a-128">기본 수동 배치를 제어 하는 편집기 내 단추의 prefab은 **표시기 prefab** 의 입력 시뮬레이션 프로필에 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-128">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="41b3a-129">이 유틸리티는 선택적 유틸리티 이며 [입력 시뮬레이션 도구 창](#input-simulation-tools-window)에서 동일한 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-129">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="41b3a-130">뷰포트 표시기는 현재 Unity UI 상호 작용을 방해할 수 있으므로 기본적으로 사용 하지 않도록 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-130">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="41b3a-131">문제 [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41b3a-131">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="41b3a-132">을 사용 하도록 설정 하려면 InputSimulationIndicators prefab를 **표시기 prefab** 에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-132">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="41b3a-133">손 아이콘은 시뮬레이트된 바늘의 상태를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-133">Hand icons show the state of the simulated hands:</span></span>

* ![추적 되지 않은 손 모양 아이콘](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="41b3a-135&quot;>이는 추적 되지 않습니다.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;41b3a-135&quot;>The hand is not tracking.</span></span> <span data-ttu-id=&quot;41b3a-136&quot;>손으로 활성화 하려면 클릭 합니다.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;41b3a-136&quot;>Click to enable the hand.</span></span>
* <span data-ttu-id=&quot;41b3a-137&quot;>![추적 된 손 아이콘](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png &quot;추적된 손 아이콘") 이 손을 추적 하지만 사용자가 제어 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-137">![Tracked hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="41b3a-138">손을 숨기려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-138">Click to hide the hand.</span></span>
* <span data-ttu-id="41b3a-139">![제어 된 손 모양 아이콘](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "제어 된 손 모양 아이콘") 사용자가 직접 추적 하 고 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-139">![Controlled hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="41b3a-140">손을 숨기려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-140">Click to hide the hand.</span></span>
* <span data-ttu-id="41b3a-141">![손 모양 다시 설정 아이콘](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "손 모양 다시 설정 아이콘") 손 모양을 기본 위치로 다시 설정 하려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-141">![Reset hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>

## <a name="in-editor-input-simulation-cheat-sheet"></a><span data-ttu-id="41b3a-142">편집기 입력 시뮬레이션 참고 자료 시트</span><span class="sxs-lookup"><span data-stu-id="41b3a-142">In editor input simulation cheat sheet</span></span>

<span data-ttu-id="41b3a-143">HandInteractionExamples 장면에서 왼쪽 Ctrl+ H를 눌러 입력 시뮬레이션 컨트롤이 있는 치트 시트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-143">Press Left Ctrl + H in the HandInteractionExamples scene to bring up a cheat sheet with Input simulation controls.</span></span>

![입력 시뮬레이션 치트 시트](https://user-images.githubusercontent.com/39840334/86066480-13637f00-ba27-11ea-8814-d222d548f684.gif)

## <a name="camera-control"></a><span data-ttu-id="41b3a-145">카메라 컨트롤</span><span class="sxs-lookup"><span data-stu-id="41b3a-145">Camera control</span></span>

<span data-ttu-id="41b3a-146">헤드 이동은 입력 시뮬레이션 서비스에서 에뮬레이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-146">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="41b3a-147">카메라 회전</span><span class="sxs-lookup"><span data-stu-id="41b3a-147">Rotating the camera</span></span>

1. <span data-ttu-id="41b3a-148">뷰포트 편집기 창을 마우스로 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-148">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="41b3a-149">*단추 누른 것이 작동하지 않는 경우 창을 클릭하여 입력 포커스를 지정해야 할 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="41b3a-149">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="41b3a-150">마우스 모양 **단추를** 길게 누릅니다(기본값: 마우스 오른쪽 단추).</span><span class="sxs-lookup"><span data-stu-id="41b3a-150">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="41b3a-151">뷰포트 창에서 마우스를 이동하여 카메라를 회전합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-151">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="41b3a-152">스크롤 휠을 사용하여 카메라를 보기 방향으로 굴려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-152">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="41b3a-153">입력 시뮬레이션 프로필에서 **마우스 모양 속도** 설정을 변경하여 카메라 회전 속도를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-153">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="41b3a-154">또는 **Look Horizontal** Look / **Vertical** 축을 사용하여 카메라를 회전합니다(기본값: 게임 컨트롤러 오른쪽 엄지스틱).</span><span class="sxs-lookup"><span data-stu-id="41b3a-154">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="41b3a-155">카메라 이동</span><span class="sxs-lookup"><span data-stu-id="41b3a-155">Moving the camera</span></span>

<span data-ttu-id="41b3a-156">가로  / **이동 세로로 이동** 축을 사용하여 카메라를 이동합니다(기본값: WASD 키 또는 게임 컨트롤러 왼쪽 엄지스틱).</span><span class="sxs-lookup"><span data-stu-id="41b3a-156">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="41b3a-157">카메라 위치 및 회전 각도는 도구 창에서도 명시적으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-157">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="41b3a-158">다시 설정 단추를 사용하여 카메라를 기본값으로 **다시 설정할** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-158">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a><span data-ttu-id="41b3a-159">컨트롤러 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="41b3a-159">Controller simulation</span></span>

<span data-ttu-id="41b3a-160">입력 시뮬레이션은 에뮬레이트된 컨트롤러 디바이스(즉, 모션 컨트롤러 및 손)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-160">The input simulation supports emulated controller devices (i.e. motion controllers and hands).</span></span> <span data-ttu-id="41b3a-161">이러한 가상 컨트롤러는 단추 또는 잡기 가능한 개체와 같은 일반 컨트롤러를 지원하는 모든 개체와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-161">These virtual controllers can interact with any object that supports regular controllers, such as buttons or grabbable objects.</span></span>

### <a name="controller-simulation-mode"></a><span data-ttu-id="41b3a-162">컨트롤러 시뮬레이션 모드</span><span class="sxs-lookup"><span data-stu-id="41b3a-162">Controller simulation mode</span></span>

<span data-ttu-id="41b3a-163">입력 [시뮬레이션 도구 창에서](#input-simulation-tools-window) **기본 컨트롤러 시뮬레이션 모드** 설정은 세 개의 고유한 입력 모델 간에 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-163">In the [input simulation tools window](#input-simulation-tools-window) the **Default Controller Simulation Mode** setting switches between three distinct input models.</span></span> <span data-ttu-id="41b3a-164">이 기본 모드는 입력 시뮬레이션 프로필 에서도 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-164">This default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="41b3a-165">*트레일러* 식: 공동 배치 데이터를 사용 하 여 완전히 모든 문자 모양 장치를 시뮬레이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-165">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="41b3a-166">HoloLens 2 상호 작용 모델을 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-166">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="41b3a-167">손 모양 또는 터치 사용의 정확한 위치를 기반으로 하는 상호 작용은이 모드에서 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-167">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="41b3a-168">*핸드 제스처*: 공중 탭 및 기본 제스처를 사용 하 여 단순한 손 모양 모델을 시뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-168">*Hand Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="41b3a-169">[HoloLens 상호 작용 모델](/windows/mixed-reality/gestures)을 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-169">Emulates [HoloLens interaction model](/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="41b3a-170">포커스는 응시 포인터를 사용 하 여 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-170">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="41b3a-171">*공기 탭* 제스처는 단추와 상호 작용 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-171">The *Air Tap* gesture is used to interact with buttons.</span></span>

* <span data-ttu-id="41b3a-172">*동작 컨트롤러*: 가장 먼 트 바늘과 유사 하 게 상호 작용 하는 것과 유사 하 게 작동 하는 VR 헤드셋에서 사용 되는 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="41b3a-172">*Motion Controller*: Simulates a motion controller used with VR headsets that works similarly to far interactions with Articulated Hands.</span></span>

   <span data-ttu-id="41b3a-173">컨트롤러 상호 작용 모델을 사용 하 여 VR 헤드셋을 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-173">Emulates VR headset with controllers interaction model.</span></span>

   <span data-ttu-id="41b3a-174">트리거, 잡기 및 메뉴 키는 키보드 및 마우스 입력을 통해 시뮬레이션 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-174">The trigger, grab and menu keys are simulated via keyboard and mouse input.</span></span>

### <a name="simulating-controller-movement"></a><span data-ttu-id="41b3a-175">컨트롤러 이동 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="41b3a-175">Simulating controller movement</span></span>

<span data-ttu-id="41b3a-176">**왼쪽/오른쪽 컨트롤러 조작 키** (기본값: 왼쪽 컨트롤러의 경우 왼쪽 *시프트* 및 오른쪽 컨트롤러에 대 한 *공간* )를 누르고 있으면 두 컨트롤러를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-176">Press and hold the **Left/Right Controller Manipulation Key** (default: *Left Shift* for left controller and *Space* for right controller) to gain control of either controller.</span></span> <span data-ttu-id="41b3a-177">조작 키를 누르면 컨트롤러가 뷰포트에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-177">While the manipulation key is pressed, the controller will appear in the viewport.</span></span> <span data-ttu-id="41b3a-178">조작 키가 해제 되 면 짧은 **컨트롤러 숨기기 제한 시간** 후에 컨트롤러가 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-178">Once the manipulation key is released, the controllers will disappear after a short **Controller Hide Timeout**.</span></span>

<span data-ttu-id="41b3a-179">[입력 시뮬레이션 도구 창](#input-simulation-tools-window) 에서 카메라를 기준으로 컨트롤러를 설정 및 고정 하거나, **왼쪽/오른쪽 컨트롤러 키** (기본값: *T* 의 경우 왼쪽, 오른쪽에는 *Y* )를 눌러 컨트롤러를 설정 하 고 고정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-179">Controllers can be toggled on and frozen relative to the camera in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Controller Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="41b3a-180">컨트롤러를 다시 숨기려면 토글 키를 다시 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-180">Press the toggle key again to hide the controllers again.</span></span> <span data-ttu-id="41b3a-181">컨트롤러를 조작 하려면 **왼쪽/오른쪽 컨트롤러 조작 키** 를 보유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-181">To manipulate the controllers, the **Left/Right Controller Manipulation Key** needs to be held.</span></span> <span data-ttu-id="41b3a-182">**왼쪽/오른쪽 컨트롤러 조작 키** 를 두 번 누르면 컨트롤러를 설정/해제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-182">Double tapping the **Left/Right Controller Manipulation Key** can also toggle the controllers on/off.</span></span>

<span data-ttu-id="41b3a-183">마우스를 움직이면 뷰 평면에서 컨트롤러가 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-183">Mouse movement will move the controller in the view plane.</span></span> <span data-ttu-id="41b3a-184">컨트롤러는 **마우스 휠** 을 사용하여 카메라로 더 이동하거나 더 가깝게 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-184">Controllers can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="41b3a-185">마우스를 사용하여 컨트롤러를 회전하려면 **왼쪽/오른쪽 컨트롤러 조작 키(왼쪽** *시프트* 또는 *공간)와* 컨트롤러 회전  단추(기본값: *왼쪽 Ctrl* 단추)를 모두 누른 다음 마우스를 이동하여 컨트롤러를 회전합니다. </span><span class="sxs-lookup"><span data-stu-id="41b3a-185">To rotate controllers using the mouse, hold both the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*) *and* the **Controller Rotate Button** (default: *Left Ctrl* button) and then move the mouse to rotate the controller.</span></span> <span data-ttu-id="41b3a-186">컨트롤러 회전 속도는 입력 시뮬레이션 프로필에서 **마우스 컨트롤러 회전 속도** 설정을 변경하여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-186">Controller rotation speed can be configured by changing the **Mouse Controller Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="41b3a-187">손을 기본값으로 다시 설정하는 것을 포함하여 [입력 시뮬레이션 도구 창에서](#input-simulation-tools-window)모든 손 배치를 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-187">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="41b3a-188">추가 프로필 설정</span><span class="sxs-lookup"><span data-stu-id="41b3a-188">Additional profile settings</span></span>

* <span data-ttu-id="41b3a-189">**컨트롤러 깊이 승수는** 마우스 스크롤 휠 깊이 이동의 민감도를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-189">**Controller Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="41b3a-190">숫자가 클수록 컨트롤러 확대/축소 속도가 빨라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-190">A larger number will speed up controller zoom.</span></span>
* <span data-ttu-id="41b3a-191">**기본 컨트롤러 거리는** 카메라에서 컨트롤러의 초기 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-191">**Default Controller Distance** is the initial distance of controllers from the camera.</span></span> <span data-ttu-id="41b3a-192">**다시 설정** 단추 컨트롤러를 클릭하면 컨트롤러도 이 거리에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-192">Clicking the **Reset** button controllers will also place controllers at this distance.</span></span>
* <span data-ttu-id="41b3a-193">**컨트롤러 지터 양은** 컨트롤러에 임의 동작을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-193">**Controller Jitter Amount** adds random motion to controllers.</span></span> <span data-ttu-id="41b3a-194">이 기능은 디바이스에서 부정확한 컨트롤러 추적을 시뮬레이션하고 노이즈 입력에서 상호 작용이 제대로 작동하는지 확인하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-194">This feature can be used to simulate inaccurate controller tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a><span data-ttu-id="41b3a-195">손 제스처</span><span class="sxs-lookup"><span data-stu-id="41b3a-195">Hand gestures</span></span>

<span data-ttu-id="41b3a-196">손가락 모으기, 잡기, poking 등과 같은 손 제스처도 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-196">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="41b3a-197">**왼쪽/오른쪽 컨트롤러 조작 키(왼쪽** *시프트* 또는 *공간)를* 사용하여 손 컨트롤을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-197">Enable hand control using the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>

2. <span data-ttu-id="41b3a-198">조작하는 동안 마우스 단추를 길게 눌러 손 제스처를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-198">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="41b3a-199">각 마우스 단추를 매핑하여 *왼쪽/가운데/오른쪽 마우스 손* 제스처 설정을 사용하여 손 모양을 다른 제스처로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-199">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="41b3a-200">*기본 손 제스처는* 단추를 누르지 않은 경우 손 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-200">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="41b3a-201">*손가락 모으기* 제스처는 이 시점에서 "선택" 작업을 수행하는 유일한 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-201">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="41b3a-202">일회용 조작</span><span class="sxs-lookup"><span data-stu-id="41b3a-202">One-hand manipulation</span></span>

1. <span data-ttu-id="41b3a-203">**왼쪽/오른쪽 컨트롤러 조작 키(왼쪽** *시프트* 또는 *공간)를* 길게 누르고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-203">Press and hold **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="41b3a-204">개체를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-204">Point at object</span></span>
3. <span data-ttu-id="41b3a-205">마우스 단추를 옆으로 유지</span><span class="sxs-lookup"><span data-stu-id="41b3a-205">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="41b3a-206">마우스를 사용 하 여 개체 이동</span><span class="sxs-lookup"><span data-stu-id="41b3a-206">Use your mouse to move the object</span></span>
5. <span data-ttu-id="41b3a-207">마우스 단추를 놓으면 상호 작용 중지</span><span class="sxs-lookup"><span data-stu-id="41b3a-207">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a><span data-ttu-id="41b3a-208">두 손을 조작</span><span class="sxs-lookup"><span data-stu-id="41b3a-208">Two-hand manipulation</span></span>

<span data-ttu-id="41b3a-209">두 손을 동시에 사용 하 여 개체를 조작 하는 경우에는 영구 수동 모드를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-209">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="41b3a-210">토글 키 (*T/Y*)를 눌러 두 손을 모두 설정/해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-210">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="41b3a-211">한 번에 한 손으로 조작:</span><span class="sxs-lookup"><span data-stu-id="41b3a-211">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="41b3a-212">오른쪽을 제어 하기 위한 **공간** 보유</span><span class="sxs-lookup"><span data-stu-id="41b3a-212">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="41b3a-213">개체를 가져올 위치로 손 모양 이동</span><span class="sxs-lookup"><span data-stu-id="41b3a-213">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="41b3a-214">**마우스 왼쪽 단추** 를 클릭 하 여 *손가락* 제스처를 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-214">Press the **left mouse button** to activate the *Pinch* gesture.</span></span>
    1. <span data-ttu-id="41b3a-215">오른쪽의 제어를 중지 하는 **공간** 을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-215">Release **Space** to stop controlling the right hand.</span></span> <span data-ttu-id="41b3a-216">이 손을 고정 하 고 더 이상 조작 되지 않으므로 *손가락* 을 끄는 제스처로 잠깁니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-216">The hand will be frozen in place and be locked into the *Pinch* gesture since it is no longer being manipulated.</span></span>
1. <span data-ttu-id="41b3a-217">또 다른 위치에서 동일한 개체를 사용 하 여 프로세스를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-217">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="41b3a-218">이제 두 손을 모두 동일한 개체를 잡기 때문에 두 항목 중 하나를 이동 하 여 두 번의 조작을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-218">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="41b3a-219">GGV (응시, 제스처 및 음성) 상호 작용</span><span class="sxs-lookup"><span data-stu-id="41b3a-219">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="41b3a-220">기본적으로 GGV 상호 작용은-편집기에서 사용 하도록 설정 되지만, 장면에는 구분 되지 않는 손으로 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-220">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="41b3a-221">카메라를 회전 하 여 응시 커서가 interactable 개체 (마우스 오른쪽 단추)를 가리키도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-221">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="41b3a-222">**마우스 왼쪽 단추** 를 클릭 하 여 상호 작용</span><span class="sxs-lookup"><span data-stu-id="41b3a-222">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="41b3a-223">카메라를 다시 회전 하 여 개체를 조작 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-223">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="41b3a-224">입력 시뮬레이션 프로필 내에서 *직접 사용 가능 입력 사용* 옵션을 설정/해제 하 여이 옵션을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-224">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="41b3a-225">또한 GGV 상호 작용에 시뮬레이션된 손을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-225">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="41b3a-226">입력 시뮬레이션 [프로필에서](#enabling-the-input-simulation-service) **손 시뮬레이션 모드를** *제스처로* 전환하여 GGV 시뮬레이션 사용</span><span class="sxs-lookup"><span data-stu-id="41b3a-226">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="41b3a-227">카메라를 회전하여 상호 작용 가능한 개체(마우스 오른쪽 단추)에서 응시 커서를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-227">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="41b3a-228">**오른쪽을** 제어할 공간을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-228">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="41b3a-229">**마우스 왼쪽 단추를** 클릭하고 누른 채 상호 작용</span><span class="sxs-lookup"><span data-stu-id="41b3a-229">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="41b3a-230">마우스를 사용하여 개체 이동</span><span class="sxs-lookup"><span data-stu-id="41b3a-230">Use your mouse to move the object</span></span>
1. <span data-ttu-id="41b3a-231">마우스 단추를 놓아 상호 작용 중지</span><span class="sxs-lookup"><span data-stu-id="41b3a-231">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a><span data-ttu-id="41b3a-232">Teleport 이벤트 발생</span><span class="sxs-lookup"><span data-stu-id="41b3a-232">Raising Teleport Events</span></span>

<span data-ttu-id="41b3a-233">입력 시뮬레이션에서 teleport 이벤트를 발생하려면 입력 시뮬레이션 프로필에서 손 제스처 설정을 구성하여 한 사람이 **Teleport 시작** 제스처를 수행하고 다른 하나는 **원격 포트 끝** 제스처를 수행하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-233">To raise the teleport event in input simulation, configure the Hand Gesture Settings in the Input Simulation Profile so that one performs the **Teleport Start** Gesture while the other performs the **Teleport End** Gesture.</span></span> <span data-ttu-id="41b3a-234">**Teleport 시작** 제스처는 Teleport 포인터를 가져오고, **Teleport End** 제스처는 teleport 작업을 완료하고 사용자를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-234">The **Teleport Start** gesture will bring up the Teleport Pointer, while the **Teleport End** gesure will complete the teleport action and move the user.</span></span>

<span data-ttu-id="41b3a-235">결과 원격포트의 y 위치는 y축을 따라 카메라의 치환에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-235">The y-position of your resulting teleport is dependent on the camera's displacement along the y-axis.</span></span> <span data-ttu-id="41b3a-236">편집기에서는 기본적으로 0이므로 **Q** 및 **E** 키를 사용하여 적절한 높이로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-236">In editor, this is 0 by default, so use the **Q** and **E** keys to adjust it to the appropriate height.</span></span>

![입력 시뮬레이션 원격 포트 설정](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a><span data-ttu-id="41b3a-238">모션 컨트롤러 상호 작용</span><span class="sxs-lookup"><span data-stu-id="41b3a-238">Motion controller interaction</span></span>

<span data-ttu-id="41b3a-239">시뮬레이션된 모션 컨트롤러는 굴절된 손과 동일한 방식으로 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-239">The simulated motion controllers can be manipulated the same way articulated hands are.</span></span> <span data-ttu-id="41b3a-240">상호 작용 모델은 트리거, 잡기 및 메뉴 키가 각각 *왼쪽 마우스 단추*, *G* 및 *M* 키에 매핑되는 동안의 원거리 손 상호 작용과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-240">The interaction model is similar to far interaction of articulated hand while the trigger, grab and menu keys are mapped to *left mouse button*, *G* and *M* key respectively.</span></span>

### <a name="eye-tracking"></a><span data-ttu-id="41b3a-241">시선 추적</span><span class="sxs-lookup"><span data-stu-id="41b3a-241">Eye tracking</span></span>

<span data-ttu-id="41b3a-242">[입력 시뮬레이션](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) 프로필 에서 **시선 위치 시뮬레이션** 옵션을 확인하여 시선 추적 [시뮬레이션을](#enabling-the-input-simulation-service)사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-242">[Eye tracking simulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="41b3a-243">GGV 또는 모션 컨트롤러 스타일 상호 작용과 함께 사용하면 안 됩니다(따라서 **기본 컨트롤러 시뮬레이션 모드가** *조인된 손으로* 설정되어 있는지 확인).</span><span class="sxs-lookup"><span data-stu-id="41b3a-243">This should not be used with GGV or motion controller style interactions (so ensure that **Default Controller Simulation Mode** is set to *Articulated Hand*).</span></span>

## <a name="see-also"></a><span data-ttu-id="41b3a-244">참고 항목</span><span class="sxs-lookup"><span data-stu-id="41b3a-244">See also</span></span>

* <span data-ttu-id="41b3a-245">[입력 시스템 프로필](../input/input-providers.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="41b3a-245">[Input System profile](../input/input-providers.md).</span></span>