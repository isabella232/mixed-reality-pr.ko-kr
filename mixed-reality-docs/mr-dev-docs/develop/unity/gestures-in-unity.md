---
title: Unity의 제스처
description: XR 및 일반 단추 및 축 Api를 사용 하 여 손으로 입력 하는 손으로 Unity에서 작업을 수행 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 제스처, unity, 응시, 입력, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 523f05f9b3dd05a140bb40168b654a2dc0b00bb5
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299718"
---
# <a name="gestures-in-unity"></a><span data-ttu-id="8d0fb-104">Unity의 제스처</span><span class="sxs-lookup"><span data-stu-id="8d0fb-104">Gestures in Unity</span></span>

<span data-ttu-id="8d0fb-105">HoloLens의 [손으로](../../design/gaze-and-commit.md#composite-gestures) 는 [Unity](gaze-in-unity.md)에서 작업을 수행 하는 두 가지 주요 방법, 그리고 HOLOLENS 및 몰입 형 HMD의 [동작 컨트롤러](../../design/motion-controllers.md) 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="8d0fb-106">Unity에서 동일한 Api를 통해 두 공간 입력 원본에 대 한 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="8d0fb-107">Unity는 Windows Mixed Reality의 공간 입력 데이터에 액세스 하는 두 가지 기본 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="8d0fb-108">일반적인 *입력. GetButton/Input. Getbutton* api는 여러 Unity XR sdk에서 작동 하는 반면, Windows Mixed Reality와 관련 된 *InteractionManager/GestureRecognizer* api는 전체 공간 입력 데이터 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="8d0fb-109">상위 수준 복합 제스처 Api (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="8d0fb-109">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="8d0fb-110">**네임 스페이스:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="8d0fb-110">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="8d0fb-111">**유형**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="8d0fb-111">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="8d0fb-112">앱은 공간 입력 소스, 탭, 유지, 조작 및 탐색 제스처에 대 한 상위 수준 복합 제스처를 인식할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-112">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation, and Navigation gestures.</span></span> <span data-ttu-id="8d0fb-113">GestureRecognizer를 사용 하 여 [직접](../../design/gaze-and-commit.md#composite-gestures) 및 [동작 컨트롤러](../../design/motion-controllers.md) 에서 이러한 복합 제스처를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-113">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="8d0fb-114">GestureRecognizer의 각 제스처 이벤트는 입력에 대 한 SourceKind와 이벤트 시점의 대상 헤드 광선을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-114">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="8d0fb-115">일부 이벤트는 추가 컨텍스트별 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-115">Some events provide additional context-specific information.</span></span>

<span data-ttu-id="8d0fb-116">제스처 인식기를 사용 하 여 제스처를 캡처하는 데 필요한 몇 가지 단계만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-116">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="8d0fb-117">새 제스처 인식기 만들기</span><span class="sxs-lookup"><span data-stu-id="8d0fb-117">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="8d0fb-118">감시할 제스처 지정</span><span class="sxs-lookup"><span data-stu-id="8d0fb-118">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="8d0fb-119">이러한 제스처에 대 한 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="8d0fb-119">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="8d0fb-120">제스처 캡처 시작</span><span class="sxs-lookup"><span data-stu-id="8d0fb-120">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="8d0fb-121">새 제스처 인식기 만들기</span><span class="sxs-lookup"><span data-stu-id="8d0fb-121">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="8d0fb-122">*GestureRecognizer* 를 사용 하려면 *GestureRecognizer* 를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-122">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="8d0fb-123">감시할 제스처 지정</span><span class="sxs-lookup"><span data-stu-id="8d0fb-123">Specify which gestures to watch for</span></span>

<span data-ttu-id="8d0fb-124">*SetRecognizableGestures ()* 를 통해 관심 있는 제스처를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-124">Specify which gestures you're interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="8d0fb-125">이러한 제스처에 대 한 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="8d0fb-125">Subscribe to events for those gestures</span></span>

<span data-ttu-id="8d0fb-126">관심이 있는 제스처에 대 한 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-126">Subscribe to events for the gestures you're interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="8d0fb-127">탐색 및 조작 제스처는 *GestureRecognizer* 의 인스턴스에서 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-127">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="8d0fb-128">제스처 캡처 시작</span><span class="sxs-lookup"><span data-stu-id="8d0fb-128">Start capturing gestures</span></span>

<span data-ttu-id="8d0fb-129">기본적으로 *GestureRecognizer* 는 *Startcapturinggestures ()* 를 호출할 때까지 입력을 모니터링 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-129">By default, a *GestureRecognizer* doesn't monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="8d0fb-130">*Stopcapturinggestures ()* 가 처리 된 프레임 보다 먼저 입력이 수행 되 면 *Stopcap의 ing제스처 ()* 가 호출 된 후에 제스처 이벤트가 생성 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-130">It's possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="8d0fb-131">*GestureRecognizer* 는 제스처가 실제로 발생 한 이전 프레임의 설정 또는 해제 여부를 기억할 것 이므로이 프레임의 응시 대상에 따라 제스처 모니터링을 시작 하 고 중지 하는 것은 안정적입니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-131">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it's reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="8d0fb-132">제스처 캡처 중지</span><span class="sxs-lookup"><span data-stu-id="8d0fb-132">Stop capturing gestures</span></span>

<span data-ttu-id="8d0fb-133">제스처 인식을 중지 하려면:</span><span class="sxs-lookup"><span data-stu-id="8d0fb-133">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="8d0fb-134">제스처 인식기 제거</span><span class="sxs-lookup"><span data-stu-id="8d0fb-134">Removing a gesture recognizer</span></span>

<span data-ttu-id="8d0fb-135">*GestureRecognizer* 개체를 삭제 하기 전에 구독 이벤트의 구독을 취소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-135">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="8d0fb-136">Unity에서 동작 컨트롤러 모델 렌더링</span><span class="sxs-lookup"><span data-stu-id="8d0fb-136">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="8d0fb-137">![동작 컨트롤러 모델 및 teleportation](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="8d0fb-137">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="8d0fb-138">*동작 컨트롤러 모델 및 teleportation*</span><span class="sxs-lookup"><span data-stu-id="8d0fb-138">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="8d0fb-139">응용 프로그램에서 사용자가 보유 하 고 있는 실제 컨트롤러와 일치 하는 동작 컨트롤러를 렌더링 하려면 [혼합 현실 도구 키트](https://github.com/Microsoft/MixedRealityToolkit-Unity/)에서 **motioncontroller prefab** 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-139">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="8d0fb-140">이 prefab는 시스템의 설치 된 동작 컨트롤러 드라이버에서 런타임에 올바른 인 글 Tf 모델을 동적으로 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-140">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="8d0fb-141">편집기에서 수동으로 가져오는 대신 이러한 모델을 동적으로 로드 하는 것이 중요 합니다. 따라서 앱은 사용자에 게 있을 수 있는 현재 및 미래의 모든 컨트롤러에 대해 물리적으로 정확한 3D 모델을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-141">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="8d0fb-142">[시작](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 지침에 따라 Mixed Reality Toolkit를 다운로드 하 여 Unity 프로젝트에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-142">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="8d0fb-143">시작 단계의 일부로 카메라를 *MixedRealityCameraParent* prefab로 대체 한 경우에는 계속 진행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-143">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="8d0fb-144">이 prefab에는 동작 컨트롤러 렌더링이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-144">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="8d0fb-145">그렇지 않으면 프로젝트 창에서 장면에 asset */HoloToolkit/Input/Prefabs/MotionControllers. prefab* 를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-145">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="8d0fb-146">사용자가 장면 내에서 teleports 때 카메라를 이동 하는 데 사용 하는 모든 부모 개체의 자식으로 해당 prefab을 추가 하 여 컨트롤러를 사용자와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-146">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="8d0fb-147">앱이 teleporting를 포함 하지 않는 경우 장면의 루트에 prefab를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-147">If your app doesn't involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="8d0fb-148">개체 throw</span><span class="sxs-lookup"><span data-stu-id="8d0fb-148">Throwing objects</span></span>

<span data-ttu-id="8d0fb-149">가상 현실에서 개체를 throw 하는 것은 처음에 보이는 것 보다 더 어려운 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-149">Throwing objects in virtual reality is a harder problem than it may at first seem.</span></span> <span data-ttu-id="8d0fb-150">대부분의 물리적 기반 상호 작용의 경우와 마찬가지로 게임에서 throw 되는 것이 예기치 않은 방식으로 작동 하는 경우에는 즉시 명확 하 고 집중 교육 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-150">As with most physically based interactions, when throwing in game acts in an unexpected way, it's immediately obvious and breaks immersion.</span></span> <span data-ttu-id="8d0fb-151">실제로 올바른 throw 동작을 나타내는 방법에 대해 자세히 살펴보고, 플랫폼 업데이트를 통해 사용할 수 있는 몇 가지 지침을 제공 하 여 사용자와 공유 하 고 싶습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-151">We've spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="8d0fb-152">[여기](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)에서 throw를 구현 하는 방법에 대 한 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-152">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="8d0fb-153">이 샘플은 다음 네 가지 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-153">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="8d0fb-154">**위치 대신 컨트롤러의 *속도* 를 사용** 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-154">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="8d0fb-155">11 월 Windows 업데이트에서는 [' ' 근사치 ' ' 위치 추적 상태](../../design/motion-controllers.md#controller-tracking-state)에 있는 경우 동작이 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-155">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="8d0fb-156">이 상태에서 컨트롤러에 대 한 속도 정보는 높은 정확도를 기대 하는 동안에도 계속 보고 됩니다 .이는 일반적으로 위치가 높은 정확도를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-156">When in this state, velocity information about the controller will continue to be reported for as long as we believe its high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="8d0fb-157">**컨트롤러의 *각도 속도* 를 통합** 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-157">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="8d0fb-158">이 논리는 `throwing.cs` `GetThrownObjectVelAngVel` 위에 링크 된 패키지 내의 정적 메서드에 있는 파일에 모두 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-158">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="8d0fb-159">각도 속도가 conserved throw 된 개체는 throw 시점에 있었던 것과 동일한 각도의 속도를 유지 해야 합니다. `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="8d0fb-159">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="8d0fb-160">Throw 된 개체의 질량 중심은 그립 포즈의 원점에 있지 않을 수 있으므로 사용자 참조 프레임의 컨트롤러와 다른 속도를 가질 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-160">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity than that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="8d0fb-161">이러한 방식으로 제공 되는 개체 속도의 부분은 컨트롤러 원본 주위에서 throw 된 개체의 질량 중심의 순간 탄젠트 속도입니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-161">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="8d0fb-162">이 탄젠트 속도는 컨트롤러 원본 및 throw 된 개체의 질량 중심 사이의 거리를 나타내는 벡터와 컨트롤러의 각도 속도 간 곱입니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-162">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="8d0fb-163">Throw 된 개체의 총 속도는 컨트롤러의 속도와 이러한 탄젠트 속도의 합입니다. `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="8d0fb-163">The total velocity of the thrown object is the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="8d0fb-164">**속도를 적용 하는 *시간* 에 대 한 주의를** 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-164">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="8d0fb-165">단추를 누르면 해당 이벤트에 대해 Bluetooth를 통해 운영 체제로 버블링 하는 데 최대 20 밀리초까지 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-165">When a button is pressed, it can take up to 20 ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="8d0fb-166">이는 컨트롤러 상태 변경을 누른 상태에서 누르지 않음으로 또는 다른 방법으로 변경 하는 것을 폴링하는 경우 발생 하는 컨트롤러의 상태에 대 한 이러한 변경 내용에 대 한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-166">This means that if you poll for a controller state change from pressed to not pressed or the other way around, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="8d0fb-167">또한 폴링 API에 의해 표시 되는 컨트롤러는 프레임이 표시 될 때, 향후 20 밀리초를 초과할 수 있는 포즈를 반영 하는 것으로 예상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-167">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more than 20 ms in the future.</span></span> <span data-ttu-id="8d0fb-168">이는 보류 중인 개체를 *렌더링* 하는 데 유용 하지만, 사용자가 throw를 릴리스한 순간의 궤적을 계산할 때 개체를 *대상으로 지정* 하는 데 시간이 복합어.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-168">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released the throw.</span></span> <span data-ttu-id="8d0fb-169">다행히 11 월 업데이트를 사용 하는 경우 *InteractionSourcePressed* 또는 *InteractionSourceReleased* 와 같은 Unity 이벤트가 전송 되 면이 상태에는 단추를 눌렀다 놓았을 때의 기록 포즈 데이터가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-169">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was pressed or released.</span></span>  <span data-ttu-id="8d0fb-170">을 throw 하는 동안 가장 정확한 컨트롤러 렌더링과 컨트롤러를 대상으로 하려면 적절 한 폴링 및 이벤트를 올바르게 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-170">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="8d0fb-171">각 프레임을 렌더링 하는 **컨트롤러** 의 경우 응용 프로그램은 현재 프레임의 photon 시간에 대해 앞으로 예측 되는 컨트롤러에서 컨트롤러의 *GameObject* 위치를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-171">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="8d0fb-172">Unity 폴링 Api (예: XR)에서이 데이터를 가져옵니다 *[. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 또는 *[XR. WSA. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-172">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="8d0fb-173">Press 또는 릴리스부터 **컨트롤러를 대상** 으로 하는 경우 앱은 해당 누르기 또는 릴리스 이벤트에 대 한 기록 컨트롤러의 포즈를 기준으로 궤적을 ray로 계산 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-173">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="8d0fb-174">*[InteractionManager InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* 와 같은 Unity 이벤트 api에서이 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-174">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="8d0fb-175">**그립 포즈를 사용** 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-175">**Use the grip pose**.</span></span> <span data-ttu-id="8d0fb-176">각도 속도와 속도는 포인터가 아닌 그립 포즈를 기준으로 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-176">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="8d0fb-177">Throw는 향후 Windows 업데이트를 사용 하 여 계속 개선 되며 여기에서 자세한 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-177">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk"></a><span data-ttu-id="8d0fb-178">MRTK의 제스처 및 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="8d0fb-178">Gesture and Motion Controllers in MRTK</span></span>

<span data-ttu-id="8d0fb-179">입력 관리자에서 제스처 및 동작 컨트롤러에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-179">You can access gesture and motion controller from the input Manager.</span></span>

* [<span data-ttu-id="8d0fb-180">MRTK의 제스처</span><span class="sxs-lookup"><span data-stu-id="8d0fb-180">Gesture in MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [<span data-ttu-id="8d0fb-181">MRTK의 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="8d0fb-181">Motion Controller in MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="8d0fb-182">안내 따르기</span><span class="sxs-lookup"><span data-stu-id="8d0fb-182">Follow along with tutorials</span></span>

<span data-ttu-id="8d0fb-183">보다 자세한 사용자 지정 예제가 포함 된 단계별 자습서는 혼합 현실 아카데미에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-183">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="8d0fb-184">MR 입력 211: 제스처</span><span class="sxs-lookup"><span data-stu-id="8d0fb-184">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="8d0fb-185">MR 입력 213: 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="8d0fb-185">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="8d0fb-186">[![MR 입력 213-동작 컨트롤러](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="8d0fb-186">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="8d0fb-187">*MR 입력 213-동작 컨트롤러*</span><span class="sxs-lookup"><span data-stu-id="8d0fb-187">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="8d0fb-188">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="8d0fb-188">Next Development Checkpoint</span></span>

<span data-ttu-id="8d0fb-189">앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-189">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="8d0fb-190">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-190">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8d0fb-191">손 및 시선 추적</span><span class="sxs-lookup"><span data-stu-id="8d0fb-191">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="8d0fb-192">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-192">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8d0fb-193">공유 환경</span><span class="sxs-lookup"><span data-stu-id="8d0fb-193">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="8d0fb-194">언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0fb-194">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d0fb-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8d0fb-195">See also</span></span>

* [<span data-ttu-id="8d0fb-196">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="8d0fb-196">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="8d0fb-197">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="8d0fb-197">Motion controllers</span></span>](../../design/motion-controllers.md)