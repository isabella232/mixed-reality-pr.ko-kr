---
title: 입력 이벤트
description: MRTK의 InputEvents에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 이벤트,
ms.openlocfilehash: c8871aa575e2aa4507e9dbbdcc8bdf0fc0604633
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176785"
---
# <a name="input-events"></a><span data-ttu-id="d4699-104">입력 이벤트</span><span class="sxs-lookup"><span data-stu-id="d4699-104">Input events</span></span>

<span data-ttu-id="d4699-105">아래 목록에서는 사용자 지정 MonoBehaviour 구성 요소에서 구현할 수 있는 모든 입력 이벤트 인터페이스를 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-105">The list below outlines all available input event interfaces to be implemented by a custom MonoBehaviour component.</span></span> <span data-ttu-id="d4699-106">이러한 인터페이스는 사용자 입력 상호 작용에 따라 사용자 지정 앱 논리를 처리하기 위해 MRTK 입력 시스템에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-106">These interfaces will be called by the MRTK input system to handle custom app logic based on user input interactions.</span></span> <span data-ttu-id="d4699-107">[포인터 입력 이벤트는](pointers.md#pointer-event-interfaces) 아래 표준 입력 이벤트 유형과 약간 다르게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-107">[Pointer input events](pointers.md#pointer-event-interfaces) are handled slightly differently than the standard input event types below.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4699-108">기본적으로 스크립트는 포커스에 있는 GameObject의 포인터 또는 부모에 의해 포커스가 있는 GameObject인 경우에만 입력 이벤트를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-108">By default, a script will receive input events only if it is the GameObject in focus by a pointer or parent of a GameObject in focus.</span></span>

| <span data-ttu-id="d4699-109">Handler</span><span class="sxs-lookup"><span data-stu-id="d4699-109">Handler</span></span> | <span data-ttu-id="d4699-110">이벤트</span><span class="sxs-lookup"><span data-stu-id="d4699-110">Events</span></span> | <span data-ttu-id="d4699-111">Description</span><span class="sxs-lookup"><span data-stu-id="d4699-111">Description</span></span> |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | <span data-ttu-id="d4699-112">원본 검색/손실</span><span class="sxs-lookup"><span data-stu-id="d4699-112">Source Detected / Lost</span></span> | <span data-ttu-id="d4699-113">입력 소스가 감지/손실될 때(예: 굴절된 손을 감지하거나 추적하지 못했을 때) 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-113">Raised when an input source is detected/lost, like when an articulated hand is detected or lost track of.</span></span> |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | <span data-ttu-id="d4699-114">소스 자세가 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-114">Source Pose Changed</span></span> | <span data-ttu-id="d4699-115">소스에서 발생된 자세 변경 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-115">Raised on source pose changes.</span></span> <span data-ttu-id="d4699-116">소스 자세는 입력 소스의 일반적인 자세를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-116">The source pose represents the general pose of the input source.</span></span> <span data-ttu-id="d4699-117">6개의 DOF 컨트롤러에서 그립 또는 포인터 자세와 같은 특정 자세는 를 통해 얻을 수 `IMixedRealityInputHandler<MixedRealityPose>` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-117">Specific poses, like the grip or pointer pose in a six DOF controller, can be obtained via `IMixedRealityInputHandler<MixedRealityPose>`.</span></span> |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | <span data-ttu-id="d4699-118">입력 아래로/위로</span><span class="sxs-lookup"><span data-stu-id="d4699-118">Input Down / Up</span></span> | <span data-ttu-id="d4699-119">단추와 같은 이진 입력의 변경 내용에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-119">Raised on changes to binary inputs like buttons.</span></span> |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | <span data-ttu-id="d4699-120">입력이 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-120">Input Changed</span></span> | <span data-ttu-id="d4699-121">지정된 형식의 입력이 변경될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-121">Raised on changes to inputs of the given type.</span></span> <span data-ttu-id="d4699-122">**T는** 다음 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-122">**T** can take the following values:</span></span> <br/> <span data-ttu-id="d4699-123">- *float(예:* 아날로그 트리거 반환)</span><span class="sxs-lookup"><span data-stu-id="d4699-123">- *float* (e.g returns analog trigger)</span></span><br/> <span data-ttu-id="d4699-124">- *Vector2(예:* 게임 패드 엄지스틱 방향을 반환함)</span><span class="sxs-lookup"><span data-stu-id="d4699-124">- *Vector2* (e.g returns gamepad thumbstick direction)</span></span> <br/> <span data-ttu-id="d4699-125">- *Vector3(예:* 추적된 디바이스의 위치 반환)</span><span class="sxs-lookup"><span data-stu-id="d4699-125">- *Vector3* (e.g return position of tracked device)</span></span> <br/> <span data-ttu-id="d4699-126">- *쿼터니언(예:* 추적된 디바이스의 방향을 반환함)</span><span class="sxs-lookup"><span data-stu-id="d4699-126">- *Quaternion* (e.g returns orientation of tracked device)</span></span><br/> <span data-ttu-id="d4699-127">- [MixedRealityPose(예:](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 완전히 추적된 디바이스 반환)</span><span class="sxs-lookup"><span data-stu-id="d4699-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (e.g. returns fully tracked device)</span></span> |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | <span data-ttu-id="d4699-128">음성 키워드 인식</span><span class="sxs-lookup"><span data-stu-id="d4699-128">Speech Keyword Recognized</span></span> | <span data-ttu-id="d4699-129">Speech Commands Profile 에 구성된 키워드 중 하나를 인식할 때 *발생합니다.*</span><span class="sxs-lookup"><span data-stu-id="d4699-129">Raised on recognition of one of the keywords configured in the *Speech Commands Profile*.</span></span> |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | <span data-ttu-id="d4699-130">받아쓰기</span><span class="sxs-lookup"><span data-stu-id="d4699-130">Dictation</span></span><br/> <span data-ttu-id="d4699-131">Hypothesis</span><span class="sxs-lookup"><span data-stu-id="d4699-131">Hypothesis</span></span> <br/> <span data-ttu-id="d4699-132">결과</span><span class="sxs-lookup"><span data-stu-id="d4699-132">Result</span></span> <br/> <span data-ttu-id="d4699-133">완료</span><span class="sxs-lookup"><span data-stu-id="d4699-133">Complete</span></span> <br/> <span data-ttu-id="d4699-134">오류</span><span class="sxs-lookup"><span data-stu-id="d4699-134">Error</span></span> | <span data-ttu-id="d4699-135">받아쓰기 세션의 결과를 보고하기 위해 받아쓰기 시스템에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-135">Raised by dictation systems to report the results of a dictation session.</span></span> |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | <span data-ttu-id="d4699-136">제스처 이벤트:</span><span class="sxs-lookup"><span data-stu-id="d4699-136">Gesture events on:</span></span> <br/> <span data-ttu-id="d4699-137">시작됨</span><span class="sxs-lookup"><span data-stu-id="d4699-137">Started</span></span> <br/> <span data-ttu-id="d4699-138">업데이트됨</span><span class="sxs-lookup"><span data-stu-id="d4699-138">Updated</span></span> <br/> <span data-ttu-id="d4699-139">완료됨</span><span class="sxs-lookup"><span data-stu-id="d4699-139">Completed</span></span> <br/> <span data-ttu-id="d4699-140">취소됨</span><span class="sxs-lookup"><span data-stu-id="d4699-140">Canceled</span></span> | <span data-ttu-id="d4699-141">제스처 감지에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-141">Raised on gesture detection.</span></span> |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | <span data-ttu-id="d4699-142">제스처 업데이트/완료됨</span><span class="sxs-lookup"><span data-stu-id="d4699-142">Gesture Updated / Completed</span></span> | <span data-ttu-id="d4699-143">지정된 형식의 추가 데이터를 포함하는 제스처를 검색할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-143">Raised on detection of gestures containing additional data of the given type.</span></span> <span data-ttu-id="d4699-144">**T** 의 가능한 값에 대한 자세한 내용은 [**제스처 이벤트를**](gestures.md#gesture-events) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4699-144">See [**gesture events**](gestures.md#gesture-events) for details on possible values for **T**.</span></span> |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | <span data-ttu-id="d4699-145">손 조인트 업데이트됨</span><span class="sxs-lookup"><span data-stu-id="d4699-145">Hand Joints Updated</span></span> | <span data-ttu-id="d4699-146">손 조인트 업데이트 시 굴절된 손 컨트롤러에 의해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-146">Raised by articulated hand controllers when hand joints are updated.</span></span> |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | <span data-ttu-id="d4699-147">손 메시 업데이트됨</span><span class="sxs-lookup"><span data-stu-id="d4699-147">Hand Mesh Updated</span></span> | <span data-ttu-id="d4699-148">손 메시가 업데이트될 때 굴절된 손 컨트롤러에 의해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-148">Raised by articulated hand controllers when a hand mesh is updated.</span></span> |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | <span data-ttu-id="d4699-149">작업 시작/종료</span><span class="sxs-lookup"><span data-stu-id="d4699-149">Action Started / Ended</span></span> | <span data-ttu-id="d4699-150">작업에 매핑된 입력에 대한 작업 시작 및 종료를 나타내려면 를 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-150">Raise to indicate action start and end for inputs mapped to actions.</span></span> |

## <a name="input-events-in-action"></a><span data-ttu-id="d4699-151">실행 중 입력 이벤트</span><span class="sxs-lookup"><span data-stu-id="d4699-151">Input events in action</span></span>

<span data-ttu-id="d4699-152">스크립트 수준에서 입력 이벤트는 위의 표에 표시된 이벤트 처리기 인터페이스 중 하나를 구현하여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-152">At the script level, input events can be consumed by implementing one of the event handler interfaces shown in the table above.</span></span> <span data-ttu-id="d4699-153">사용자 상호 작용을 통해 입력 이벤트가 발생하면 다음이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-153">When an input event fires via a user interaction, the following takes place:</span></span>

1. <span data-ttu-id="d4699-154">MRTK 입력 시스템은 입력 이벤트가 발생했음을 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-154">The MRTK input system recognizes that an input event has occurred.</span></span>
1. <span data-ttu-id="d4699-155">MRTK 입력 시스템은 등록된 모든 전역 입력 처리기에 입력 이벤트의 관련 인터페이스 [함수를 발생합니다.](#register-for-global-input-events)</span><span class="sxs-lookup"><span data-stu-id="d4699-155">The MRTK input system fires the relevant interface function of the input event to all [registered global input handlers](#register-for-global-input-events)</span></span>
1. <span data-ttu-id="d4699-156">입력 시스템에 등록된 모든 활성 포인터:</span><span class="sxs-lookup"><span data-stu-id="d4699-156">For every active pointer registered with the input system:</span></span>
    1. <span data-ttu-id="d4699-157">입력 시스템은 현재 포인터에 포커스가 있는 GameObject를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-157">The input system determines which GameObject is in focus for the current pointer.</span></span>
    1. <span data-ttu-id="d4699-158">입력 시스템은 [Unity의 이벤트 시스템을](https://docs.unity3d.com/Manual/EventSystem.html) 활용하여 포커스가 있는 GameObject에서 일치하는 모든 구성 요소에 대한 관련 인터페이스 함수를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-158">The input system utilizes [Unity's event system](https://docs.unity3d.com/Manual/EventSystem.html) to fire the relevant interface function for all matching components on the focused GameObject.</span></span>
    1. <span data-ttu-id="d4699-159">입력 이벤트가 [사용된 것으로 표시된](#how-to-stop-input-events)경우 프로세스가 종료되고 더 이상 GameObjects에서 콜백을 수신하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-159">If at any point an input event has been [marked as used](#how-to-stop-input-events), the process will end and no further GameObjects will receive callbacks.</span></span>
        - <span data-ttu-id="d4699-160">예제: 인터페이스를 구현하는 구성 요소는 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 음성 명령이 인식될 때 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-160">Example: Components implementing the interface [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) will be searched for when a speech command is recognized.</span></span>
        - <span data-ttu-id="d4699-161">참고: Unity 이벤트 시스템은 현재 GameObject에서 원하는 인터페이스와 일치하는 구성 요소가 없으면 부모 GameObject를 검색하기 위해 버블 업됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-161">Note: The Unity event system will bubble up to search the parent GameObject if no components matching the desired interface are found on the current GameObject.</span></span>
1. <span data-ttu-id="d4699-162">전역 입력 처리기가 등록되지 않고 일치하는 구성 요소/인터페이스가 있는 GameObject가 없는 경우 입력 시스템은 등록된 각 대체 입력 처리기를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-162">If no global input handlers are registered and no GameObject is found with a matching component/interface, then the input system will call each fallback registered input handler</span></span>

> [!NOTE]
> <span data-ttu-id="d4699-163">[포인터 입력 이벤트는](pointers.md#pointer-event-interfaces) 위에 나열된 입력 이벤트 인터페이스와 약간 다른 방식으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-163">[Pointer input events](pointers.md#pointer-event-interfaces) are handled in a slightly different manner than the input event interfaces listed above.</span></span> <span data-ttu-id="d4699-164">특히 포인터 입력 이벤트는 입력 이벤트를 발생시킨 포인터와 모든 전역 입력 처리기에 의해 포커스가 있는 GameObject에 의해서만 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-164">In particular, pointer input events are handled only by the GameObject in focus by the pointer that fired the input event - as well as any global input handlers.</span></span> <span data-ttu-id="d4699-165">일반 입력 이벤트는 모든 활성 포인터에 대한 포커스에서 GameObjects에 의해 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-165">Regular input events are handled by GameObjects in focus for all active pointers.</span></span>

### <a name="input-event-interface-example"></a><span data-ttu-id="d4699-166">입력 이벤트 인터페이스 예제</span><span class="sxs-lookup"><span data-stu-id="d4699-166">Input event interface example</span></span>

<span data-ttu-id="d4699-167">아래 코드에서는 인터페이스를 사용하는 것을 보여 주는 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-167">The code below demonstrates use of the [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface.</span></span> <span data-ttu-id="d4699-168">사용자가 이 클래스를 사용하는 GameObject에 집중하는 동안 "더 작음" 또는 "더 큰" 단어를 `ShowHideSpeechHandler` 말하면 GameObject는 자체의 크기를 절반 또는 두 배만큼 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-168">When the user says the words "smaller" or "bigger" while focusing on a GameObject with this `ShowHideSpeechHandler` class, the GameObject will scale itself by half or twice as much.</span></span>

```c#
public class ShowHideSpeechHandler : MonoBehaviour, IMixedRealitySpeechHandler
{
    ...

    void IMixedRealitySpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.Command.Keyword == "smaller")
        {
            transform.localScale *= 0.5f;
        }
        else if (eventData.Command.Keyword == "bigger")
        {
            transform.localScale *= 2.0f;
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="d4699-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 입력 이벤트를 사용하려면 원하는 키워드가 [MRTK Speech Commands Profile](speech.md)에 미리 등록되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) input events require that the desired keywords are pre-registered in the [MRTK Speech Commands Profile](speech.md).</span></span>

## <a name="register-for-global-input-events"></a><span data-ttu-id="d4699-170">전역 입력 이벤트 등록</span><span class="sxs-lookup"><span data-stu-id="d4699-170">Register for global input events</span></span>

<span data-ttu-id="d4699-171">GameObject가 포커스에 있을 수 있는 것을 무시하고 전역 입력 이벤트를 수신 대기하는 구성 요소를 만들려면 구성 요소가 입력 시스템에 등록되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-171">To create a component that listens for global input events, disregarding what GameObject may be in focus, a component must register itself with the Input System.</span></span> <span data-ttu-id="d4699-172">등록되면 이 MonoBehaviour의 모든 인스턴스는 현재 포커스가 있는 GameObject 및 기타 전역 등록 수신기와 함께 입력 이벤트를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-172">Once registered, any instances of this MonoBehaviour will receive input events along with any GameObject(s) currently in focus and other global registered listeners.</span></span>

<span data-ttu-id="d4699-173">입력 이벤트가 사용된 [것으로 표시된](#how-to-stop-input-events)경우 전역 등록된 처리기는 여전히 콜백을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-173">If an input event has been [marked as used](#how-to-stop-input-events), global registered handlers will still all receive callbacks.</span></span> <span data-ttu-id="d4699-174">그러나 포커스가 있는 GameObjects는 이벤트를 수신하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-174">However, no focused GameObjects will receive the event.</span></span>

### <a name="global-input-registration-example"></a><span data-ttu-id="d4699-175">전역 입력 등록 예제</span><span class="sxs-lookup"><span data-stu-id="d4699-175">Global input registration example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler, // Handle source detected and lost
    IMixedRealityHandJointHandler // handle joint position updates for hands
{
    private void OnEnable()
    {
        // Instruct Input System that we would like to receive all input events of type
        // IMixedRealitySourceStateHandler and IMixedRealityHandJointHandler
        CoreServices.InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        // This component is being destroyed
        // Instruct the Input System to disregard us for input event handling
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source detected: " + hand.ControllerHandedness);
        }
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source lost: " + hand.ControllerHandedness);
        }
    }

    public void OnHandJointsUpdated(
                InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        MixedRealityPose palmPose;
        if (eventData.InputData.TryGetValue(TrackedHandJoint.Palm, out palmPose))
        {
            Debug.Log("Hand Joint Palm Updated: " + palmPose.Position);
        }
    }
}
```

## <a name="register-for-fallback-input-events"></a><span data-ttu-id="d4699-176">대체 입력 이벤트 등록</span><span class="sxs-lookup"><span data-stu-id="d4699-176">Register for fallback input events</span></span>

<span data-ttu-id="d4699-177">대체 입력 처리기는 등록된 전역 입력 처리기와 유사하지만 입력 이벤트 처리의 마지막 수단으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-177">Fallback input handlers are similar to registered global input handlers but are treated as a last resort for input event handling.</span></span> <span data-ttu-id="d4699-178">전역 입력 처리기가 없고 GameObject가 포커스에 없는 경우에만 대체 입력 처리기가 활용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-178">Only if no global input handlers were found and no GameObjects are in focus will fallback input handlers be leveraged.</span></span>

### <a name="fallback-input-handler-example"></a><span data-ttu-id="d4699-179">대체 입력 처리기 예제</span><span class="sxs-lookup"><span data-stu-id="d4699-179">Fallback input handler example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler // Handle source detected and lost
{
    private void OnEnable()
    {
        CoreServices.InputSystem?.PushFallbackInputHandler(this);
    }

    private void OnDisable()
    {
        CoreServices.InputSystem?.PopFallbackInputHandler();
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        ...
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        ...
    }
}
```

## <a name="how-to-stop-input-events"></a><span data-ttu-id="d4699-180">입력 이벤트를 중지하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4699-180">How to stop input events</span></span>

<span data-ttu-id="d4699-181">모든 입력 이벤트 인터페이스는 [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) 인터페이스의 각 함수에 대한 매개 변수로 데이터 개체를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-181">Every input event interface provides a [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) data object as a parameter to each function on the interface.</span></span> <span data-ttu-id="d4699-182">이 이벤트 데이터 개체는 Unity의 자체 에서 [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-182">This event data object extends from Unity's own [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html).</span></span>

<span data-ttu-id="d4699-183">[설명된 대로](#input-events-in-action)입력 이벤트가 실행을 통해 전파되는 것을 중지하기 위해 구성 요소는 를 [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) 호출하여 이벤트를 사용된 것으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-183">In order to stop an input event from propagating through its execution [as outlined](#input-events-in-action), a component can call [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) to mark the event as used.</span></span> <span data-ttu-id="d4699-184">이렇게 하면 전역 입력 처리기를 제외하고 다른 모든 GameObject가 현재 입력 이벤트를 받지 못하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-184">This will stop any other GameObjects from receiving the current input event, with the exception of global input handlers.</span></span>

> [!NOTE]
> <span data-ttu-id="d4699-185">메서드를 호출하는 구성 요소는 `Use()` 다른 GameObjects에서 수신을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-185">A component that calls the `Use()` method will stop other GameObjects from receiving it.</span></span> <span data-ttu-id="d4699-186">그러나 현재 GameObject의 다른 구성 요소는 여전히 입력 이벤트를 수신하고 관련된 인터페이스 함수를 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4699-186">However, other components on the current GameObject will still receive the input event and fire any related interface functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4699-187">참조</span><span class="sxs-lookup"><span data-stu-id="d4699-187">See also</span></span>

- [<span data-ttu-id="d4699-188">포인터</span><span class="sxs-lookup"><span data-stu-id="d4699-188">Pointers</span></span>](pointers.md)
- [<span data-ttu-id="d4699-189">Speech</span><span class="sxs-lookup"><span data-stu-id="d4699-189">Speech</span></span>](speech.md)
- [<span data-ttu-id="d4699-190">입력 상태</span><span class="sxs-lookup"><span data-stu-id="d4699-190">Input State</span></span>](input-state.md)
