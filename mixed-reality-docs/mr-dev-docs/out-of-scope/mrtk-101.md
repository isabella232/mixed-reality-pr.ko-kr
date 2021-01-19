---
title: MRTK 101 - 일반적인 공간 상호 작용 사용
description: HoloLens 2, HoloLens, Windows Mixed Reality 및 Open VR을 위한 기본 상호 작용에 Mixed Reality Toolkit Unity를 사용하는 방법입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, 디자인, 샘플 앱, 컨트롤, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.localizationpriority: high
ms.openlocfilehash: 8b9af843dc059ef4d50aa5508356c7aeed968a4e
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98248149"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="d70c8-104">MRTK 101: 일반적인 공간 상호 작용에 Mixed Reality Toolkit Unity를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="d70c8-106">MRTK를 사용하여 혼합 현실에서 가장 널리 사용되는 일반적인 상호 작용 패턴을 구현하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="d70c8-107">Unity 편집기에서 입력 상호 작용을 시뮬레이션하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="d70c8-108">개체를 잡고 움직이는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-108">How to grab and move an object?</span></span>
- <span data-ttu-id="d70c8-109">개체 크기를 조정하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-109">How to resize an object?</span></span>
- <span data-ttu-id="d70c8-110">정밀도를 사용하여 개체를 이동하거나 회전하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="d70c8-111">개체에서 입력 이벤트에 응답하도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="d70c8-112">시각적 피드백을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-112">How to add visual feedback?</span></span>
- <span data-ttu-id="d70c8-113">오디오 피드백을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-113">How to add audio feedback?</span></span>
- <span data-ttu-id="d70c8-114">HoloLens 2 스타일 단추 프리팹을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="d70c8-115">개체에서 사용자를 따르도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-115">How to make an object follow you?</span></span>
- <span data-ttu-id="d70c8-116">개체에서 사용자를 향하도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="d70c8-117">이 문서는 [MRTK v2.5.1 릴리스](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)의 변경 내용을 반영하도록 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="d70c8-118">이 페이지의 모든 콘텐츠는 Unity 편집기에서 MRTK의 입력 시뮬레이션을 사용하여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="d70c8-119">아직 설치하지 않은 경우 [MRTK 설치 가이드(GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)에 따라 최신 버전의 MRTK를 설치하세요.</span><span class="sxs-lookup"><span data-stu-id="d70c8-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="d70c8-120">Unity 편집기에서 입력 상호 작용을 시뮬레이션하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-120">How to simulate input interactions in Unity editor?</span></span>

<span data-ttu-id="d70c8-121">MRTK는 편집기 내 입력 시뮬레이션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="d70c8-122">Unity의 재생 단추를 클릭하여 장면을 실행한 후 다음 키를 사용하여 입력을 시뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-122">Run your scene by clicking Unity's play button, then use the following keys to simulate input:</span></span>
- <span data-ttu-id="d70c8-123">W, A, S, D 키를 눌러 카메라를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-123">Press W, A, S, D keys to move the camera.</span></span>
- <span data-ttu-id="d70c8-124">마우스 오른쪽 단추를 누른 채 마우스를 움직여 주위를 둘러봅니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-124">Hold the right mouse button and move the mouse to look around.</span></span>
- <span data-ttu-id="d70c8-125">스페이스 바(오른손) 또는 왼쪽 Shift 키(왼손)를 눌러 시뮬레이션된 손을 불러옵니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-125">Press Space bar(Right hand) or left Shift key(Left hand) to bring up the simulated hands</span></span>
- <span data-ttu-id="d70c8-126">보기에서 시뮬레이션된 손을 유지하려면 T 또는 Y 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-126">Press T or Y keys to keep simulated hands in view</span></span>
- <span data-ttu-id="d70c8-127">Q 또는 E(수평) / R 또는 F(수직)를 눌러 시뮬레이션된 손을 회전합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-127">Press Q or E(horizontal) / R or F(vertical) to rotate simulated hands</span></span>

<span data-ttu-id="d70c8-128">[MRTK 문서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)에서 입력 시뮬레이션에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-128">You can learn more about Input Simulation in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span></span>

## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="d70c8-129">개체를 잡고 움직이는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-129">How to grab and move an object?</span></span>

<span data-ttu-id="d70c8-130">**ObjectManipulator.cs** 및 **NearInteractionGrabbable.cs** 스크립트를 첨부하여 개체를 잡을 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-130">Attach the **ObjectManipulator.cs** and **NearInteractionGrabbable.cs** scripts to make an object grabbable.</span></span> <span data-ttu-id="d70c8-131">ObjectManipulator는 근거리 및 원거리 상호 작용을 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-131">ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="d70c8-132">HoloLens 2의 관절 있는 손 추적 입력(근거리), 손 광선(원거리), 모션 컨트롤러의 빔(원거리), HoloLens 응시 커서 및 에어 탭(원거리)을 사용하여 개체를 잡고 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-132">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), and HoloLens gaze cursor and air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="d70c8-133">개체 크기를 조정하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-133">How to resize an object?</span></span>
<span data-ttu-id="d70c8-134">**ObjectManipulator.cs** 는 양손 크기 조정/회전을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-134">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="d70c8-135">스크립트는 HoloLens 2의 관절 있는 손 입력, HoloLens 1의 응시 + 제스처 입력, Windows Mixed Reality 몰입형 헤드셋의 모션 컨트롤러 입력과 같은 다양한 입력 유형에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-135">The script works with various input types, such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="d70c8-136">MRTK 설명서에서 Object Manipulator에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="d70c8-136">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="d70c8-137">정밀도를 사용하여 개체를 이동하거나 회전하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-137">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="d70c8-138">개체의 크기를 조정하고 회전하는 인터페이스인 경계 상자를 사용하는 개체에 **BoundsControl.cs** 를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-138">Assign **BoundsControl.cs** to an object to use Bounding Box, which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="d70c8-139">기본적으로 HoloLens 1 스타일 파란색 핸들 및 선이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-139">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="d70c8-140">HoloLens 2 스타일 근접 기반 애니메이션 핸들을 사용하려면 프리팹과 재질을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-140">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="d70c8-141">MRTK 설명서에서 경계 컨트롤에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="d70c8-141">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="d70c8-142">개체에서 입력 이벤트에 응답하도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-142">How to make an object respond to input events?</span></span>
<span data-ttu-id="d70c8-143">**PointerHandler.cs** 를 개체에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-143">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="d70c8-144">검사기에서 OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() 이벤트를 사용할 수 있습니다. 스크립트에서 이러한 이벤트를 사용하려면 **IMixedRealityPointerHandler** 를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-144">In the inspector, you can use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="d70c8-145">MRTK 설명서에서 입력 시스템에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="d70c8-145">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="d70c8-146">시각적 피드백을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-146">How to add visual feedback?</span></span>
<span data-ttu-id="d70c8-147">**Interactable.cs** 를 개체에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-147">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="d70c8-148">검사기에서 대상 개체를 추가하고 새 테마를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-148">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="d70c8-149">Interactable의 테마 프로필을 사용하면 시각적 피드백을 사용 가능한 모든 입력 상호 작용 상태에 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-149">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="d70c8-150">Interactable은 상호 작용 상태에 따라 셰이더의 속성을 제어할 수 있는 셰이더 테마를 포함하여 다양한 유형의 테마를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-150">Interactable provides various types of themes including the shader theme, which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="d70c8-151">MRTK 설명서에서 Interactable에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="d70c8-151">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="d70c8-152">시각적 피드백에 대한 또 다른 중요한 구성 요소는 **MRTK 표준 셰이더** 입니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-152">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="d70c8-153">MRTK 표준 셰이더를 사용하면 시각적 피드백 효과(예: 호버 조명, 근접 조명)를 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-153">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="d70c8-154">MRTK 표준 셰이더는 Unity 표준 셰이더보다 적은 계산을 수행하므로 성능이 뛰어난 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-154">Since MRTK Standard shader performs less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="d70c8-155">새 재질을 만들고, 'Mixed Reality Toolkit > 표준' 셰이더를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-155">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="d70c8-156">또는 MRTK 표준 셰이더를 사용하는 기존 재질 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-156">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="d70c8-157">MRTK 문서에서 MRTK 표준 셰이더에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="d70c8-157">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="d70c8-158">오디오 피드백을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-158">How to add audio feedback?</span></span>
<span data-ttu-id="d70c8-159">**AudioSource** 를 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-159">Add **AudioSource** to an object.</span></span> <span data-ttu-id="d70c8-160">그런 다음, 입력 이벤트를 공개하는 스크립트(예: Interactable.cs 또는 PointerHandler.cs)에서 AudioSource가 있는 개체를 이벤트에 할당하고, **AudioSource.PlayOneShot()** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-160">Then, in the scripts that expose input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="d70c8-161">오디오 클립을 사용하거나 MRTK의 오디오 자산 중에서 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-161">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="d70c8-162">HoloLens 2 스타일 단추 프리팹을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-162">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="d70c8-163">MRTK는 근접 조명, 압축 상자, 사용자의 신뢰도를 높이는 단추 표면의 잔물결 효과와 같은 시각적 피드백을 포함하여 다양한 유형의 HoloLens 2의 셸(OS) 스타일 단추를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-163">MRTK provides various types of HoloLens 2's shell (OS) style buttons, including visual feedback like proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="d70c8-164">**HoloLens 2 스타일의 누를 수 있는 단추 프리팹** 중 하나를 장면에 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-164">Drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="d70c8-165">프리팹은 위에서 소개한 Interactable.cs를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-165">The prefab uses Interactable.cs introduced above.</span></span> <span data-ttu-id="d70c8-166">Interactable의 OnClick()과 같은 공개된 이벤트를 사용하여 작업을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-166">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="d70c8-167">MRTK 설명서에서 Button 프리팹에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="d70c8-167">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="d70c8-168">개체에서 사용자를 따르도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-168">How to make an object follow you?</span></span>
<span data-ttu-id="d70c8-169">**RadialView.cs** 또는 **Follow.cs** 스크립트를 개체에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-169">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="d70c8-170">3D 공간에서 다양한 유형의 개체 위치 지정을 구현할 수 있는 Solver 스크립트 시리즈의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-170">It's part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="d70c8-171">**SolverHandler.cs** 가 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-171">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="d70c8-172">다음은 HoloLens 셸의 [시작] 메뉴와 마찬가지로 '지연 팔로우(lazy follow)' tag-along 동작을 구현하기 위한 RadialView 구성의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-172">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="d70c8-173">최소/최대 거리 및 최소/최대 보기 각도를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-173">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="d70c8-174">아래 예에서는 개체의 위치를 15° 이내에서 0.4-0.8m 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-174">The example below shows positioning the object between 0.4 m and 0.8-m range within 15°.</span></span> <span data-ttu-id="d70c8-175">위치를 더 빠르거나 더 느리게 업데이트하려면 선형 보간 시간(Lerp Time) 값을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-175">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="d70c8-176">MRTK 설명서에서 Solver에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="d70c8-176">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="d70c8-177">개체에서 사용자를 향하도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="d70c8-177">How to make an object face you?</span></span>
<span data-ttu-id="d70c8-178">**Billboard.cs** 스크립트를 개체에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-178">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="d70c8-179">사용자가 어디에 있든 항상 사용자를 향합니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-179">It will always face you, whatever your position.</span></span> <span data-ttu-id="d70c8-180">피벗 축 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70c8-180">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="d70c8-181">놀라운 혼합 현실 환경을 만들 준비가 되었나요?</span><span class="sxs-lookup"><span data-stu-id="d70c8-181">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="d70c8-182">아래 페이지를 방문하여 MRTK와 혼합 현실에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="d70c8-182">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="d70c8-183">작성자 정보</span><span class="sxs-lookup"><span data-stu-id="d70c8-183">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="d70c8-184"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="d70c8-184"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="d70c8-185">UX 디자이너 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="d70c8-185">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="d70c8-186">참조</span><span class="sxs-lookup"><span data-stu-id="d70c8-186">See also</span></span>
* [<span data-ttu-id="d70c8-187">MRTK 설치 가이드(GitHub)</span><span class="sxs-lookup"><span data-stu-id="d70c8-187">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="d70c8-188">MRTK(Mixed Reality Toolkit)-Unity GitHub</span><span class="sxs-lookup"><span data-stu-id="d70c8-188">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="d70c8-189">MRTK 설명서 포털(GitHub)</span><span class="sxs-lookup"><span data-stu-id="d70c8-189">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="d70c8-190">HoloToolkit에서 MRTK로 포팅 지침</span><span class="sxs-lookup"><span data-stu-id="d70c8-190">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
