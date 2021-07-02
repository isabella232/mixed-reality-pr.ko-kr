---
title: 제스처
description: MRTK의 제스처 및 해당 이벤트에 대한 Docummentation
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 제스처,
ms.openlocfilehash: 7bbc97ab5e23a69356d523c463aa37c013d70337
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176880"
---
# <a name="gestures"></a><span data-ttu-id="4964c-104">제스처</span><span class="sxs-lookup"><span data-stu-id="4964c-104">Gestures</span></span>

<span data-ttu-id="4964c-105">제스처는 사람의 손을 기반으로 하는 입력 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-105">Gestures are input events based on human hands.</span></span> <span data-ttu-id="4964c-106">MRTK에서 제스처 입력 이벤트를 발생시키는 디바이스에는 두 가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-106">There are two types of devices that raise gesture input events in MRTK:</span></span>

- <span data-ttu-id="4964c-107">HoloLens 같은 디바이스를 Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4964c-107">Windows Mixed Reality devices such as HoloLens.</span></span> <span data-ttu-id="4964c-108">이는 손가락 모으기 동작("에어 탭") 및 탭 및 유지 제스처에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-108">This describes pinching motions ("Air Tap") and tap-and-hold gestures.</span></span>

  <span data-ttu-id="4964c-109">HoloLens 제스처에 대한 자세한 내용은 [Windows Mixed Reality 제스처 설명서를 참조하세요.](/windows/mixed-reality/gestures)</span><span class="sxs-lookup"><span data-stu-id="4964c-109">For more information on HoloLens gestures see the [Windows Mixed Reality Gestures documentation](/windows/mixed-reality/gestures).</span></span>

  <span data-ttu-id="4964c-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)[는 Unity XR을 래핑합니다. Wsa. Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) - HoloLens 디바이스에서 Unity의 제스처 이벤트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) wraps the [Unity XR.WSA.Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) to consume Unity's gesture events from HoloLens devices.</span></span>

- <span data-ttu-id="4964c-111">터치 스크린 디바이스.</span><span class="sxs-lookup"><span data-stu-id="4964c-111">Touch screen devices.</span></span>

  <span data-ttu-id="4964c-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) 는 물리적 터치 스크린을 지원하는 [Unity Touch 클래스를](https://docs.unity3d.com/ScriptReference/Touch.html) 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) wraps the [Unity Touch class](https://docs.unity3d.com/ScriptReference/Touch.html) that supports physical touch screens.</span></span>

<span data-ttu-id="4964c-113">이러한 두 입력 소스는 _모두 제스처 설정_ 프로필을 사용하여 Unity의 Touch 및 제스처 이벤트를 각각 MRTK의 입력 작업 으로 [변환합니다.](input-actions.md)</span><span class="sxs-lookup"><span data-stu-id="4964c-113">Both of these input sources use the _Gesture Settings_ profile to translate Unity's Touch and Gesture events respectively into MRTK's [Input Actions](input-actions.md).</span></span> <span data-ttu-id="4964c-114">이 프로필은 입력 _시스템 설정_ 프로필에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-114">This profile can be found under the _Input System Settings_ profile.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a><span data-ttu-id="4964c-115">제스처 이벤트</span><span class="sxs-lookup"><span data-stu-id="4964c-115">Gesture events</span></span>

<span data-ttu-id="4964c-116">제스처 이벤트는 제스처 처리기 인터페이스 또는 (이벤트 처리기 표 참조) 중 하나를 구현하여 [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) [수신됩니다.](input-events.md)</span><span class="sxs-lookup"><span data-stu-id="4964c-116">Gesture events are received by implementing one of the gesture handler interfaces: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) or [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (see table of [event handlers](input-events.md)).</span></span>

<span data-ttu-id="4964c-117">제스처 이벤트 처리기의 예제 구현은 [예제 장면](#example-scene) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4964c-117">See [Example Scene](#example-scene) for an example implementation of a gesture event handler.</span></span>

<span data-ttu-id="4964c-118">제네릭 버전을 구현할 때 *OnGestureCompleted* 및 *OnGestureUpdated* 이벤트는 다음 형식의 형식화된 데이터를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-118">When implementing the generic version, the *OnGestureCompleted* and *OnGestureUpdated* events can receive typed data of the following types:</span></span>

- <span data-ttu-id="4964c-119">`Vector2` - 2D 위치 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-119">`Vector2` - 2D position gesture.</span></span> <span data-ttu-id="4964c-120">를 알리기 위해 터치 스크린에서 [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-120">Produced by touch screens to inform of their [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html).</span></span>
- <span data-ttu-id="4964c-121">`Vector3` - 3D 위치 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-121">`Vector3` - 3D position gesture.</span></span> <span data-ttu-id="4964c-122">HoloLens 생성하여 다음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-122">Produced by HoloLens to inform of:</span></span>
  - <span data-ttu-id="4964c-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) 조작 이벤트의</span><span class="sxs-lookup"><span data-stu-id="4964c-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) of a manipulation event</span></span>
  - <span data-ttu-id="4964c-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) 탐색 이벤트의</span><span class="sxs-lookup"><span data-stu-id="4964c-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) of a navigation event</span></span>
- <span data-ttu-id="4964c-125">`Quaternion` - 3D 회전 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-125">`Quaternion` - 3D rotation gesture.</span></span> <span data-ttu-id="4964c-126">사용자 지정 입력 소스에 사용할 수 있지만 현재 기존 입력 소스에서 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-126">Available to custom input sources but not currently produced by any of the existing ones.</span></span>
- <span data-ttu-id="4964c-127">`MixedRealityPose` - 결합된 3D 위치/회전 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-127">`MixedRealityPose` - Combined 3D position/rotation gesture.</span></span> <span data-ttu-id="4964c-128">사용자 지정 입력 소스에 사용할 수 있지만 현재 기존 입력 소스에서 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-128">Available to custom input sources but not currently produced by any of the existing ones.</span></span>

## <a name="order-of-events"></a><span data-ttu-id="4964c-129">이벤트 순서</span><span class="sxs-lookup"><span data-stu-id="4964c-129">Order of events</span></span>

<span data-ttu-id="4964c-130">사용자 입력에 따라 다음과 같은 두 가지 주요 이벤트 체인이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-130">There are two principal chains of events, depending on user input:</span></span>

- <span data-ttu-id="4964c-131">"Hold":</span><span class="sxs-lookup"><span data-stu-id="4964c-131">"Hold":</span></span>
    1. <span data-ttu-id="4964c-132">길게 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-132">Hold tap:</span></span>
        - <span data-ttu-id="4964c-133">_조작_ 시작</span><span class="sxs-lookup"><span data-stu-id="4964c-133">start _Manipulation_</span></span>
    1. <span data-ttu-id="4964c-134">[HoldStartDuration 을 탭합니다.](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)</span><span class="sxs-lookup"><span data-stu-id="4964c-134">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="4964c-135">_보류_ 시작</span><span class="sxs-lookup"><span data-stu-id="4964c-135">start _Hold_</span></span>
    1. <span data-ttu-id="4964c-136">릴리스 탭:</span><span class="sxs-lookup"><span data-stu-id="4964c-136">Release tap:</span></span>
        - <span data-ttu-id="4964c-137">_완료 보류_</span><span class="sxs-lookup"><span data-stu-id="4964c-137">complete _Hold_</span></span>
        - <span data-ttu-id="4964c-138">완전한 _조작_</span><span class="sxs-lookup"><span data-stu-id="4964c-138">complete _Manipulation_</span></span>

- <span data-ttu-id="4964c-139">"이동":</span><span class="sxs-lookup"><span data-stu-id="4964c-139">"Move":</span></span>
    1. <span data-ttu-id="4964c-140">길게 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-140">Hold tap:</span></span>
        - <span data-ttu-id="4964c-141">_조작_ 시작</span><span class="sxs-lookup"><span data-stu-id="4964c-141">start _Manipulation_</span></span>
    1. <span data-ttu-id="4964c-142">[HoldStartDuration 을 탭합니다.](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)</span><span class="sxs-lookup"><span data-stu-id="4964c-142">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="4964c-143">_보류_ 시작</span><span class="sxs-lookup"><span data-stu-id="4964c-143">start _Hold_</span></span>
    1. <span data-ttu-id="4964c-144">[NavigationStartThreshold를](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)넘어 손을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-144">Move hand beyond [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span></span>
        - <span data-ttu-id="4964c-145">_보류_ 취소</span><span class="sxs-lookup"><span data-stu-id="4964c-145">cancel _Hold_</span></span>
        - <span data-ttu-id="4964c-146">_탐색_ 시작</span><span class="sxs-lookup"><span data-stu-id="4964c-146">start _Navigation_</span></span>
    1. <span data-ttu-id="4964c-147">릴리스 탭:</span><span class="sxs-lookup"><span data-stu-id="4964c-147">Release tap:</span></span>
        - <span data-ttu-id="4964c-148">완전한 _조작_</span><span class="sxs-lookup"><span data-stu-id="4964c-148">complete _Manipulation_</span></span>
        - <span data-ttu-id="4964c-149">_탐색_ 완료</span><span class="sxs-lookup"><span data-stu-id="4964c-149">complete _Navigation_</span></span>

## <a name="example-scene"></a><span data-ttu-id="4964c-150">예제 장면</span><span class="sxs-lookup"><span data-stu-id="4964c-150">Example scene</span></span>

<span data-ttu-id="4964c-151">HandInteractionGestureEventsExample(Assets/MRTK/Examples/Demos/HandTracking/Scenes) 장면에서 Result 포인터를 사용하여 적중 위치에서 개체를 생성하는 방법을 보여줍니다. </span><span class="sxs-lookup"><span data-stu-id="4964c-151">The **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) scene shows how to use the pointer Result to spawn an object at the hit location.</span></span>

<span data-ttu-id="4964c-152">`GestureTester`(Assets/MRTK/Examples/Demos/HandTracking/Script) 스크립트는 GameObjects를 통해 제스처 이벤트를 시각화하는 예제 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-152">The `GestureTester` (Assets/MRTK/Examples/Demos/HandTracking/Script) script is an example implementation to visualize gesture events via GameObjects.</span></span> <span data-ttu-id="4964c-153">처리기 함수는 표시기 개체의 색을 변경하고 장면의 텍스트 개체에 마지막으로 기록된 이벤트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4964c-153">The handler functions change the color of indicator objects and display the last recorded event in text objects in the scene.</span></span>
