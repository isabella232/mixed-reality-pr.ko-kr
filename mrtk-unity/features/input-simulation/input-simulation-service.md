---
title: 입력 시뮬레이션 서비스
description: MRTK의 입력 시뮬레이션 서비스에 대한 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 66b79c14bbd0ea8c188aba684b9bd1034de31bf9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176965"
---
# <a name="input-simulation-service"></a><span data-ttu-id="6a7fe-104">입력 시뮬레이션 서비스</span><span class="sxs-lookup"><span data-stu-id="6a7fe-104">Input simulation service</span></span>

![MRTK 입력 시뮬레이션](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

<span data-ttu-id="6a7fe-106">MRTK의 입력 시뮬레이션을 사용하면 디바이스를 빌드하고 배포하지 않고도 Unity 편집기에서 다양한 유형의 상호 작용을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-106">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="6a7fe-107">이렇게 하면 디자인 및 개발 프로세스에서 아이디어를 빠르게 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-107">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="6a7fe-108">키보드와 마우스 조합을 사용하여 시뮬레이션된 입력을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-108">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="6a7fe-109">입력 시뮬레이션 서비스는 Unity 편집기에서 사용할 수 없는 디바이스 및 플랫폼의 동작을 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-109">The Input Simulation Service emulates the behavior of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="6a7fe-110">다음은 이러한 서비스의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-110">Examples include:</span></span>

* <span data-ttu-id="6a7fe-111">HoloLens 또는 VR 디바이스 헤드 추적</span><span class="sxs-lookup"><span data-stu-id="6a7fe-111">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="6a7fe-112">손 제스처 HoloLens</span><span class="sxs-lookup"><span data-stu-id="6a7fe-112">HoloLens hand gestures</span></span>
* <span data-ttu-id="6a7fe-113">HoloLens 2 손 추적</span><span class="sxs-lookup"><span data-stu-id="6a7fe-113">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="6a7fe-114">시선 추적 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="6a7fe-114">HoloLens 2 eye tracking</span></span>
* <span data-ttu-id="6a7fe-115">VR 디바이스 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="6a7fe-115">VR device controllers</span></span>

> [!WARNING]
> <span data-ttu-id="6a7fe-116">Unity의 XR 홀로그램 에뮬레이션 > 에뮬레이션 모드 = "편집기에서 시뮬레이트"를 사용하는 경우에는 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-116">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="6a7fe-117">Unity의 편집기 내 시뮬레이션은 MRTK의 입력 시뮬레이션에서 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-117">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="6a7fe-118">MRTK 입력 시뮬레이션 서비스를 사용하려면 XR 홀로그램 에뮬레이션을 에뮬레이션 모드 = *"없음"으로* 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-118">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="how-to-use-mrtk-input-simulation"></a><span data-ttu-id="6a7fe-119">MRTK 입력 시뮬레이션을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="6a7fe-119">How to use MRTK Input simulation</span></span> 

<span data-ttu-id="6a7fe-120">입력 시뮬레이션은 MRTK와 함께 제공된 프로필에서 기본적으로 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-120">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span> <span data-ttu-id="6a7fe-121">**재생 단추를** 클릭하면 입력 시뮬레이션이 지원된 장면을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-121">You can simply click **Play** button to run the scene with input simulation support.</span></span>

* <span data-ttu-id="6a7fe-122">**W, A, S, D, Q, E** 키를 눌러 카메라를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-122">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="6a7fe-123">마우스 **오른쪽 단추를** 누른 다음 마우스를 이동하여 주변을 둘러볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-123">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="6a7fe-124">시뮬레이션된 손을 가져오려면 **스페이스바(오른쪽)** 또는 **왼쪽 시프트 키(왼쪽)를** 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-124">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="6a7fe-125">시뮬레이션된 손을 보기에 유지하려면 **T** 또는 **Y** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-125">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="6a7fe-126">시뮬레이션된 손을 회전하려면 **Ctrl 키를** 누른 채 마우스를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-126">To rotate simulated hands, press and hold **Ctrl key** and move mouse</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a><span data-ttu-id="6a7fe-127">편집기 입력 시뮬레이션 치트 시트에서</span><span class="sxs-lookup"><span data-stu-id="6a7fe-127">In editor input simulation cheat sheet</span></span>

<span data-ttu-id="6a7fe-128">HandInteractionExamples 장면에서 **왼쪽 Ctrl+ H를** 눌러 입력 시뮬레이션 컨트롤이 있는 치트 시트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-128">Press **Left Ctrl + H** in the HandInteractionExamples scene to bring up a cheat sheet with Input simulation controls.</span></span>

> ![MRTK 입력 시뮬레이션 치트 시트](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="6a7fe-130">입력 시뮬레이션 서비스 사용</span><span class="sxs-lookup"><span data-stu-id="6a7fe-130">Enabling the input simulation service</span></span>

<span data-ttu-id="6a7fe-131">입력 시스템 데이터 공급자 구성에서 입력 시뮬레이션 서비스를 다음으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-131">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="6a7fe-132">**형식은** *Microsoft.MixedReality.Toolkit. Input > InputSimulationService*.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-132">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="6a7fe-133">서비스에서 키보드 및 마우스 입력을 사용하므로 **기본적으로 지원되는 플랫폼에는** 모든 *편집기* 플랫폼이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-133">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="6a7fe-134">원하는 대상을 포함하도록 **지원되는** 플랫폼 속성을 변경하여 독립 실행형과 같은 다른 플랫폼 엔드포인트에서 입력 시뮬레이션 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-134">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a><span data-ttu-id="6a7fe-135">카메라 컨트롤</span><span class="sxs-lookup"><span data-stu-id="6a7fe-135">Camera control</span></span>

<span data-ttu-id="6a7fe-136">헤드 이동은 입력 시뮬레이션 서비스에서 에뮬레이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-136">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="6a7fe-137">카메라 회전</span><span class="sxs-lookup"><span data-stu-id="6a7fe-137">Rotating the camera</span></span>

1. <span data-ttu-id="6a7fe-138">뷰포트 편집기 창을 마우스로 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-138">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="6a7fe-139">*단추 누른 것이 작동하지 않는 경우 입력 포커스를 지정하려면 창을 클릭해야 할 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="6a7fe-139">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="6a7fe-140">마우스 모양 **단추를** 길게 누릅니다(기본값: 마우스 오른쪽 단추).</span><span class="sxs-lookup"><span data-stu-id="6a7fe-140">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="6a7fe-141">뷰포트 창에서 마우스를 이동하여 카메라를 회전합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-141">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="6a7fe-142">스크롤 휠을 사용하여 카메라를 보기 방향으로 굴려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-142">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="6a7fe-143">입력 시뮬레이션 프로필에서 **마우스 모양 속도** 설정을 변경하여 카메라 회전 속도를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-143">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="6a7fe-144">또는 **Look Horizontal** Look / **Vertical** 축을 사용하여 카메라를 회전합니다(기본값: 게임 컨트롤러 오른쪽 엄지스틱).</span><span class="sxs-lookup"><span data-stu-id="6a7fe-144">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="6a7fe-145">카메라 이동</span><span class="sxs-lookup"><span data-stu-id="6a7fe-145">Moving the camera</span></span>

<span data-ttu-id="6a7fe-146">가로  / **이동 세로로 이동** 축을 사용하여 카메라를 이동합니다(기본값: WASD 키 또는 게임 컨트롤러 왼쪽 엄지스틱).</span><span class="sxs-lookup"><span data-stu-id="6a7fe-146">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="6a7fe-147">카메라 위치 및 회전 각도는 도구 창에서도 명시적으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-147">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="6a7fe-148">다시 설정 단추를 사용하여 카메라를 기본값으로 **다시 설정할** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-148">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a><span data-ttu-id="6a7fe-149">컨트롤러 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="6a7fe-149">Controller simulation</span></span>

<span data-ttu-id="6a7fe-150">입력 시뮬레이션은 에뮬레이트된 컨트롤러 디바이스(즉, 모션 컨트롤러 및 손)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-150">The input simulation supports emulated controller devices (i.e. motion controllers and hands).</span></span> <span data-ttu-id="6a7fe-151">이러한 가상 컨트롤러는 단추 또는 잡기 가능한 개체와 같은 일반 컨트롤러를 지원하는 모든 개체와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-151">These virtual controllers can interact with any object that supports regular controllers, such as buttons or grabbable objects.</span></span>

### <a name="controller-simulation-mode"></a><span data-ttu-id="6a7fe-152">컨트롤러 시뮬레이션 모드</span><span class="sxs-lookup"><span data-stu-id="6a7fe-152">Controller simulation mode</span></span>

<span data-ttu-id="6a7fe-153">입력 [시뮬레이션 도구 창에서](#input-simulation-tools-window) **기본 컨트롤러 시뮬레이션 모드** 설정은 세 개의 고유한 입력 모델 간에 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-153">In the [input simulation tools window](#input-simulation-tools-window) the **Default Controller Simulation Mode** setting switches between three distinct input models.</span></span> <span data-ttu-id="6a7fe-154">이 기본 모드는 입력 시뮬레이션 프로필에서도 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-154">This default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="6a7fe-155">*굴절형 손:* 공동 위치 데이터를 통해 완전히 굴절된 손 디바이스를 시뮬레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-155">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="6a7fe-156">HoloLens 2 상호 작용 모델을 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-156">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="6a7fe-157">손의 정확한 위치를 기반으로 하거나 터치를 사용하는 상호 작용은 이 모드에서 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-157">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="6a7fe-158">*손 제스처:* 에어 탭 및 기본 제스처를 통해 간소화된 손 모델을 시뮬레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-158">*Hand Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="6a7fe-159">HoloLens [상호 작용 모델을](/windows/mixed-reality/gestures)에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-159">Emulates [HoloLens interaction model](/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="6a7fe-160">포커스는 응시 포인터를 사용하여 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-160">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="6a7fe-161">*에어 탭* 제스처는 단추와 상호 작용하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-161">The *Air Tap* gesture is used to interact with buttons.</span></span>

* <span data-ttu-id="6a7fe-162">*모션 컨트롤러:* VR 헤드셋과 함께 사용되는 모션 컨트롤러를 시뮬레이션합니다. 이 동작은 명사형 손과의 원거리 상호 작용과 유사하게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-162">*Motion Controller*: Simulates a motion controller used with VR headsets that works similarly to far interactions with Articulated Hands.</span></span>

   <span data-ttu-id="6a7fe-163">컨트롤러 상호 작용 모델을 통해 VR 헤드셋을 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-163">Emulates VR headset with controllers interaction model.</span></span>

   <span data-ttu-id="6a7fe-164">트리거, 잡기 및 메뉴 키는 키보드 및 마우스 입력을 통해 시뮬레이션됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-164">The trigger, grab and menu keys are simulated via keyboard and mouse input.</span></span>

### <a name="simulating-controller-movement"></a><span data-ttu-id="6a7fe-165">컨트롤러 이동 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="6a7fe-165">Simulating controller movement</span></span>

<span data-ttu-id="6a7fe-166">**왼쪽/오른쪽 컨트롤러 조작** 키(기본값: 왼쪽 컨트롤러의 *경우 왼쪽 시프트,* 오른쪽 컨트롤러의 경우 *공간)를* 길게 눌러 두 컨트롤러 중 하나를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-166">Press and hold the **Left/Right Controller Manipulation Key** (default: *Left Shift* for left controller and *Space* for right controller) to gain control of either controller.</span></span> <span data-ttu-id="6a7fe-167">조작 키를 누르는 동안 컨트롤러가 뷰포트에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-167">While the manipulation key is pressed, the controller will appear in the viewport.</span></span> <span data-ttu-id="6a7fe-168">조작 키가 해제되면 컨트롤러는 짧은 **컨트롤러 숨기기 시간 제한** 이후에 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-168">Once the manipulation key is released, the controllers will disappear after a short **Controller Hide Timeout**.</span></span>

<span data-ttu-id="6a7fe-169">[입력 시뮬레이션 도구 창에서](#input-simulation-tools-window) 카메라를 기준으로 컨트롤러를 설정/고정하거나 **왼쪽/오른쪽 컨트롤러 키** 전환(기본값: 왼쪽의 경우 *T,* 오른쪽의 *경우 Y)을* 눌러 컨트롤러를 설정/고정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-169">Controllers can be toggled on and frozen relative to the camera in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Controller Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="6a7fe-170">토글 키를 다시 눌러 컨트롤러를 다시 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-170">Press the toggle key again to hide the controllers again.</span></span> <span data-ttu-id="6a7fe-171">컨트롤러를 조작하려면 **왼쪽/오른쪽 컨트롤러 조작 키를** 보유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-171">To manipulate the controllers, the **Left/Right Controller Manipulation Key** needs to be held.</span></span> <span data-ttu-id="6a7fe-172">**왼쪽/오른쪽 컨트롤러 조작 키를** 두 번 탭하면 컨트롤러를 켜고 끌 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-172">Double tapping the **Left/Right Controller Manipulation Key** can also toggle the controllers on/off.</span></span>

<span data-ttu-id="6a7fe-173">마우스 이동은 보기 평면에서 컨트롤러를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-173">Mouse movement will move the controller in the view plane.</span></span> <span data-ttu-id="6a7fe-174">**컨트롤러는 마우스 휠** 을 사용하여 카메라로 더 이동하거나 더 가깝게 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-174">Controllers can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="6a7fe-175">마우스를 사용하여 컨트롤러를 회전하려면 **왼쪽/오른쪽 컨트롤러 조작 키(왼쪽** *시프트* 또는 *공간)와* 컨트롤러 회전  단추(기본값: *왼쪽 Ctrl* 단추)를 모두 누른 다음 마우스를 이동하여 컨트롤러를 회전합니다. </span><span class="sxs-lookup"><span data-stu-id="6a7fe-175">To rotate controllers using the mouse, hold both the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*) *and* the **Controller Rotate Button** (default: *Left Ctrl* button) and then move the mouse to rotate the controller.</span></span> <span data-ttu-id="6a7fe-176">컨트롤러 회전 속도는 입력 시뮬레이션 프로필에서 **마우스 컨트롤러 회전 속도** 설정을 변경하여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-176">Controller rotation speed can be configured by changing the **Mouse Controller Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="6a7fe-177">손을 기본값으로 다시 설정하는 것을 포함하여 [입력 시뮬레이션 도구 창에서](#input-simulation-tools-window)모든 손 배치를 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-177">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="6a7fe-178">추가 프로필 설정</span><span class="sxs-lookup"><span data-stu-id="6a7fe-178">Additional profile settings</span></span>

* <span data-ttu-id="6a7fe-179">**컨트롤러 깊이 승수는** 마우스 스크롤 휠 깊이 이동의 민감도를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-179">**Controller Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="6a7fe-180">숫자가 클수록 컨트롤러 확대/축소 속도가 빨라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-180">A larger number will speed up controller zoom.</span></span>
* <span data-ttu-id="6a7fe-181">**기본 컨트롤러 거리는** 카메라에서 컨트롤러의 초기 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-181">**Default Controller Distance** is the initial distance of controllers from the camera.</span></span> <span data-ttu-id="6a7fe-182">**다시 설정** 단추 컨트롤러를 클릭하면 컨트롤러도 이 거리에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-182">Clicking the **Reset** button controllers will also place controllers at this distance.</span></span>
* <span data-ttu-id="6a7fe-183">**컨트롤러 지터 양은** 컨트롤러에 임의 동작을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-183">**Controller Jitter Amount** adds random motion to controllers.</span></span> <span data-ttu-id="6a7fe-184">이 기능은 디바이스에서 부정확한 컨트롤러 추적을 시뮬레이션하고 노이즈 입력에서 상호 작용이 제대로 작동하는지 확인하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-184">This feature can be used to simulate inaccurate controller tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a><span data-ttu-id="6a7fe-185">손 제스처</span><span class="sxs-lookup"><span data-stu-id="6a7fe-185">Hand gestures</span></span>

<span data-ttu-id="6a7fe-186">손가락 모으기, 잡기, poking 등과 같은 손 제스처도 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-186">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="6a7fe-187">**왼쪽/오른쪽 컨트롤러 조작 키(왼쪽** *시프트* 또는 *공간)를* 사용하여 손 컨트롤 사용</span><span class="sxs-lookup"><span data-stu-id="6a7fe-187">Enable hand control using the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>

2. <span data-ttu-id="6a7fe-188">조작하는 동안 마우스 단추를 길게 눌러 손 제스처를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-188">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="6a7fe-189">각 마우스 단추를 매핑하여 *왼쪽/가운데/오른쪽 마우스 손* 제스처 설정을 사용하여 손 모양을 다른 제스처로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-189">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="6a7fe-190">*기본 손 제스처는* 단추를 누르지 않은 경우 손 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-190">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="6a7fe-191">*손가락 모으기* 제스처는 이 시점에서 "선택" 작업을 수행하는 유일한 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-191">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="6a7fe-192">일회용 조작</span><span class="sxs-lookup"><span data-stu-id="6a7fe-192">One-hand manipulation</span></span>

1. <span data-ttu-id="6a7fe-193">**왼쪽/오른쪽 컨트롤러 조작 키(왼쪽** *시프트* 또는 *공백)를* 길게 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-193">Press and hold **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="6a7fe-194">개체를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-194">Point at object</span></span>
3. <span data-ttu-id="6a7fe-195">마우스 단추를 눌러 손가락 모으기</span><span class="sxs-lookup"><span data-stu-id="6a7fe-195">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="6a7fe-196">마우스를 사용하여 개체 이동</span><span class="sxs-lookup"><span data-stu-id="6a7fe-196">Use your mouse to move the object</span></span>
5. <span data-ttu-id="6a7fe-197">마우스 단추를 놓아 상호 작용 중지</span><span class="sxs-lookup"><span data-stu-id="6a7fe-197">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a><span data-ttu-id="6a7fe-198">양손 조작</span><span class="sxs-lookup"><span data-stu-id="6a7fe-198">Two-hand manipulation</span></span>

<span data-ttu-id="6a7fe-199">두 손으로 동시에 개체를 조작하는 경우 영구 손 모드를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-199">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="6a7fe-200">토글 키(*T/Y*)를 눌러 두 손을 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-200">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="6a7fe-201">한 번에 한 손으로 조작:</span><span class="sxs-lookup"><span data-stu-id="6a7fe-201">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="6a7fe-202">오른쪽을 제어 하기 위한 **공간** 보유</span><span class="sxs-lookup"><span data-stu-id="6a7fe-202">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="6a7fe-203">개체를 가져올 위치로 손 모양 이동</span><span class="sxs-lookup"><span data-stu-id="6a7fe-203">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="6a7fe-204">**마우스 왼쪽 단추** 를 클릭 하 여 *손가락* 제스처를 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-204">Press the **left mouse button** to activate the *Pinch* gesture.</span></span>
    1. <span data-ttu-id="6a7fe-205">오른쪽의 제어를 중지 하는 **공간** 을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-205">Release **Space** to stop controlling the right hand.</span></span> <span data-ttu-id="6a7fe-206">이 손을 고정 하 고 더 이상 조작 되지 않으므로 *손가락* 을 끄는 제스처로 잠깁니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-206">The hand will be frozen in place and be locked into the *Pinch* gesture since it is no longer being manipulated.</span></span>
1. <span data-ttu-id="6a7fe-207">또 다른 위치에서 동일한 개체를 사용 하 여 프로세스를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-207">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="6a7fe-208">이제 두 손을 모두 동일한 개체를 잡기 때문에 두 항목 중 하나를 이동 하 여 두 번의 조작을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-208">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="6a7fe-209">GGV (응시, 제스처 및 음성) 상호 작용</span><span class="sxs-lookup"><span data-stu-id="6a7fe-209">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="6a7fe-210">기본적으로 GGV 상호 작용은-편집기에서 사용 하도록 설정 되지만, 장면에는 구분 되지 않는 손으로 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-210">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="6a7fe-211">카메라를 회전 하 여 응시 커서가 interactable 개체 (마우스 오른쪽 단추)를 가리키도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-211">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="6a7fe-212">**마우스 왼쪽 단추** 를 클릭 하 여 상호 작용</span><span class="sxs-lookup"><span data-stu-id="6a7fe-212">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="6a7fe-213">카메라를 다시 회전 하 여 개체를 조작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-213">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="6a7fe-214">입력 시뮬레이션 프로필 내에서 *직접 사용 가능 입력 사용* 옵션을 설정/해제 하 여이 옵션을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-214">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="6a7fe-215">또한 시뮬레이션 된 손을 GGV 상호 작용에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-215">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="6a7fe-216">**손으로 시뮬레이션 모드** 를 [입력 시뮬레이션 프로필](#enabling-the-input-simulation-service) 의 *제스처로* 전환 하 여 GGV 시뮬레이션 사용</span><span class="sxs-lookup"><span data-stu-id="6a7fe-216">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="6a7fe-217">카메라를 회전 하 여 응시 커서가 interactable 개체 (마우스 오른쪽 단추)를 가리키도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-217">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="6a7fe-218">오른쪽을 제어 하기 위한 **공간** 보유</span><span class="sxs-lookup"><span data-stu-id="6a7fe-218">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="6a7fe-219">**마우스 왼쪽 단추** 를 클릭 하 여 상호 작용</span><span class="sxs-lookup"><span data-stu-id="6a7fe-219">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="6a7fe-220">마우스를 사용 하 여 개체 이동</span><span class="sxs-lookup"><span data-stu-id="6a7fe-220">Use your mouse to move the object</span></span>
1. <span data-ttu-id="6a7fe-221">마우스 단추를 놓으면 상호 작용 중지</span><span class="sxs-lookup"><span data-stu-id="6a7fe-221">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a><span data-ttu-id="6a7fe-222">텔레포트 이벤트 발생</span><span class="sxs-lookup"><span data-stu-id="6a7fe-222">Raising Teleport Events</span></span>

<span data-ttu-id="6a7fe-223">입력 시뮬레이션에서 텔레포트 이벤트를 발생 시키려면 입력 시뮬레이션 프로필에서 손 제스처 설정 구성 하 고 다른 하나는 텔레포트 **종료** 제스처를 수행 하는 동안 **텔레포트 시작** 제스처를 수행 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-223">To raise the teleport event in input simulation, configure the Hand Gesture Settings in the Input Simulation Profile so that one performs the **Teleport Start** Gesture while the other performs the **Teleport End** Gesture.</span></span> <span data-ttu-id="6a7fe-224">텔레포트 **시작** 제스처는 텔레포트 포인터를 표시 하 고, **텔레포트 End** gesure은 텔레포트 작업을 완료 하 고 사용자를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-224">The **Teleport Start** gesture will bring up the Teleport Pointer, while the **Teleport End** gesure will complete the teleport action and move the user.</span></span>

<span data-ttu-id="6a7fe-225">결과 텔레포트의 y 위치는 y 축을 따라 카메라의 변위에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-225">The y-position of your resulting teleport is dependent on the camera's displacement along the y-axis.</span></span> <span data-ttu-id="6a7fe-226">편집기에서이는 기본적으로 0 이므로 **Q** 및 **E** 키를 사용 하 여 적절 한 높이로 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-226">In editor, this is 0 by default, so use the **Q** and **E** keys to adjust it to the appropriate height.</span></span>

![입력 시뮬레이션 텔레포트 설정](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a><span data-ttu-id="6a7fe-228">동작 컨트롤러 상호 작용</span><span class="sxs-lookup"><span data-stu-id="6a7fe-228">Motion controller interaction</span></span>

<span data-ttu-id="6a7fe-229">시뮬레이션 된 동작 컨트롤러는 동일한 방식으로 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-229">The simulated motion controllers can be manipulated the same way articulated hands are.</span></span> <span data-ttu-id="6a7fe-230">상호 작용 모델은 트리거, 잡기 및 메뉴 키가 각각 *왼쪽 마우스 단추*, *G* 및 *M* 키에 매핑되는 동안 트레일러 식의 먼 상호 작용과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-230">The interaction model is similar to far interaction of articulated hand while the trigger, grab and menu keys are mapped to *left mouse button*, *G* and *M* key respectively.</span></span>

### <a name="eye-tracking"></a><span data-ttu-id="6a7fe-231">시선 추적</span><span class="sxs-lookup"><span data-stu-id="6a7fe-231">Eye tracking</span></span>

<span data-ttu-id="6a7fe-232">[입력 시뮬레이션 프로필](#enabling-the-input-simulation-service)에서 **눈 위치 시뮬레이트** 옵션을 선택 하 여 [눈동자 추적 시뮬레이션](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) 을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-232">[Eye tracking simulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="6a7fe-233">이는 GGV 또는 모션 컨트롤러 스타일 상호 작용에 사용 하면 안 됩니다. 따라서 **기본 컨트롤러 시뮬레이션 모드가** *트레일러* 식으로 설정 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-233">This should not be used with GGV or motion controller style interactions (so ensure that **Default Controller Simulation Mode** is set to *Articulated Hand*).</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="6a7fe-234">입력 시뮬레이션 도구 창</span><span class="sxs-lookup"><span data-stu-id="6a7fe-234">Input simulation tools window</span></span>

<span data-ttu-id="6a7fe-235">**혼합 현실**  >  **Toolkit**  >  **유틸리티**  >  **입력 시뮬레이션** 메뉴에서 입력 시뮬레이션 도구 창을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-235">Enable the input simulation tools window from the  **Mixed Reality** > **Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="6a7fe-236">이 창에서는 재생 모드 동안 입력 시뮬레이션의 상태에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-236">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons-optional"></a><span data-ttu-id="6a7fe-237">뷰포트 단추 (선택 사항)</span><span class="sxs-lookup"><span data-stu-id="6a7fe-237">Viewport buttons (optional)</span></span>

<span data-ttu-id="6a7fe-238">기본 수동 배치를 제어 하는 편집기 내 단추의 prefab은 **표시기 prefab** 의 입력 시뮬레이션 프로필에 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-238">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="6a7fe-239">이 유틸리티는 선택적 유틸리티 이며 [입력 시뮬레이션 도구 창](#input-simulation-tools-window)에서 동일한 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-239">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="6a7fe-240">뷰포트 표시기는 현재 Unity UI 상호 작용을 방해할 수 있으므로 기본적으로 사용 하지 않도록 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-240">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="6a7fe-241">문제 [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-241">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="6a7fe-242">을 사용 하도록 설정 하려면 InputSimulationIndicators prefab를 **표시기 prefab** 에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-242">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="6a7fe-243">손 아이콘은 시뮬레이트된 바늘의 상태를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-243">Hand icons show the state of the simulated hands:</span></span>

* ![추적 되지 않은 손 모양 아이콘](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="6a7fe-245&quot;>이는 추적 되지 않습니다.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;6a7fe-245&quot;>The hand is not tracking.</span></span> <span data-ttu-id=&quot;6a7fe-246&quot;>손으로 활성화 하려면 클릭 합니다.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;6a7fe-246&quot;>Click to enable the hand.</span></span>
* <span data-ttu-id=&quot;6a7fe-247&quot;>![추적 된 손 아이콘](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png &quot;추적 된 손 아이콘") 이 손을 추적 하지만 사용자가 제어 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-247">![Tracked hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="6a7fe-248">손을 숨기려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-248">Click to hide the hand.</span></span>
* <span data-ttu-id="6a7fe-249">![제어 된 손 모양 아이콘](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "제어 된 손 모양 아이콘") 사용자가 직접 추적 하 고 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-249">![Controlled hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="6a7fe-250">손을 숨기려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-250">Click to hide the hand.</span></span>
* <span data-ttu-id="6a7fe-251">![손 모양 다시 설정 아이콘](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "손 모양 다시 설정 아이콘") 손 모양을 기본 위치로 다시 설정 하려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-251">![Reset hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>


## <a name="see-also"></a><span data-ttu-id="6a7fe-252">참조</span><span class="sxs-lookup"><span data-stu-id="6a7fe-252">See also</span></span>

* <span data-ttu-id="6a7fe-253">[입력 시스템 프로필](../input/input-providers.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="6a7fe-253">[Input System profile](../input/input-providers.md).</span></span>
