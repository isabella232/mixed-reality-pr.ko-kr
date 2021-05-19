---
title: 눈 추적 대상 선택
description: 아이 응시 데이터 및 아이 응시 특정 이벤트에 액세스 하 여 MRTK에서 대상을 선택 하는 방법
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, EyeTracking,
ms.openlocfilehash: 229903e01c597aefbb3fc29de8a49d79cbbd42d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144193"
---
# <a name="eye-supported-target-selection"></a><span data-ttu-id="7c92a-104">눈 지원 대상 선택</span><span class="sxs-lookup"><span data-stu-id="7c92a-104">Eye-supported target selection</span></span>

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="7c92a-106">이 페이지에서는 아이 응시 데이터에 액세스 하는 다양 한 옵션과 MRTK의 대상 선택에 대 한 눈에 맞는 특정 이벤트에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-106">This page discusses different options for accessing eye gaze data and eye gaze specific events to select targets in MRTK.</span></span> <span data-ttu-id="7c92a-107">시각 추적을 사용 하면 사용자가 _직접 추적_ 및 _음성 명령과_ 같은 추가 입력을 사용 하 여 원하는 항목에 대 한 정보를 조합 하 여 빠르고 간편 하 게 대상을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-107">Eye tracking allows for fast and effortless target selections using a combination of information about what a user is looking at with additional inputs such as _hand tracking_ and _voice commands_:</span></span>

- <span data-ttu-id="7c92a-108">_"Select"_ (기본 음성 명령) & 표시</span><span class="sxs-lookup"><span data-stu-id="7c92a-108">Look & Say _"Select"_ (default voice command)</span></span>
- <span data-ttu-id="7c92a-109">_"폭발_ " 또는 _"Pop"_ (사용자 지정 음성 명령) & 표시</span><span class="sxs-lookup"><span data-stu-id="7c92a-109">Look & Say _"Explode"_ or _"Pop"_ (custom voice commands)</span></span>
- <span data-ttu-id="7c92a-110">& Bluetooth 단추 찾기</span><span class="sxs-lookup"><span data-stu-id="7c92a-110">Look & Bluetooth button</span></span>
- <span data-ttu-id="7c92a-111">& 가까이 (즉, 사용자의 손을 잡고, 엄지 단추와 인덱스 손가락을 함께)</span><span class="sxs-lookup"><span data-stu-id="7c92a-111">Look & Pinch (i.e., hold up your hand in front of you and bring your thumb and index finger together)</span></span>
  - <span data-ttu-id="7c92a-112">이렇게 하려면 [광선을 사용 하지 않도록 설정 해야](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray) 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-112">Please note that for this to work, the [hand rays need to be disabled](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span></span>

<span data-ttu-id="7c92a-113">아이 응시를 사용 하 여 holographic 콘텐츠를 선택 하려면 다음과 같은 몇 가지 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-113">To select holographic content using eye gaze, there are several options:</span></span>

[<span data-ttu-id="7c92a-114">**1. 기본 포커스 포인터를 사용 합니다.**</span><span class="sxs-lookup"><span data-stu-id="7c92a-114">**1. Use the primary focus pointer:**</span></span>](#1-use-generic-focus-and-pointer-handlers)

<span data-ttu-id="7c92a-115">이는 우선 순위가 지정 된 커서로 인식 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-115">This can be understood as your prioritized cursor.</span></span>
<span data-ttu-id="7c92a-116">기본적으로 손을 볼 수 있는 경우에는 손 광선입니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-116">By default, if the hands are in view, then this would be hand rays.</span></span>
<span data-ttu-id="7c92a-117">뷰가 표시 되지 않는 경우 우선 순위가 지정 된 포인터가 헤드 또는 눈에 응시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-117">If no hands are in view, then the prioritized pointer would be head or eye gaze.</span></span>
<span data-ttu-id="7c92a-118">따라서 핸드 광선을 사용 하는 경우 현재 디자인 헤드 또는 눈에 맞는 응시를 커서 입력으로 표시 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-118">Thus, please note that based on the current design head or eye gaze is suppressed as a cursor input if hand rays are used.</span></span>

<span data-ttu-id="7c92a-119">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-119">For example:</span></span>

<span data-ttu-id="7c92a-120">사용자가 먼 holographic 단추를 선택 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-120">A user wants to select a distant holographic button.</span></span>
<span data-ttu-id="7c92a-121">개발자는 다양 한 상황에서 사용자가이 작업을 수행할 수 있도록 하는 유연한 솔루션을 제공 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-121">As a developer, you want to provide a flexible solution that allows the user to achieve this tasks in various conditions:</span></span>

- <span data-ttu-id="7c92a-122">단추를 탐색 하 고 poke.</span><span class="sxs-lookup"><span data-stu-id="7c92a-122">Walk up to the button and poke it</span></span>
- <span data-ttu-id="7c92a-123">멀리서 보고 "select"라고 말합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-123">Look at it from a distance and say "select"</span></span>
- <span data-ttu-id="7c92a-124">손 광선을 사용하여 단추를 대상으로 지정하고 손가락 모으기를 수행하는 경우 가장 유연한 솔루션은 현재 우선 순위가 지정된 기본 포커스 포인터가 이벤트를 트리거할 때마다 알려주기 때문에 기본 포커스 처리기를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-124">Target the button using a hand ray and performing a pinch In this case, the most flexible solution is to use the primary focus handler as it will notify you whenever the currently prioritized primary focus pointer triggers an event.</span></span> <span data-ttu-id="7c92a-125">손 광선을 사용하는 경우 손을 보는 즉시 머리 또는 시선 응시 포커스 포인터가 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-125">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c92a-126">손 광선을 사용하는 경우 손을 보는 즉시 머리 또는 시선 응시 포커스 포인터가 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-126">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span> <span data-ttu-id="7c92a-127">[ _'모양 및 손가락 모으기'_ 상호 작용을 지원하려면 손 광선 을 사용하지 않도록 설정해야 합니다.](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span><span class="sxs-lookup"><span data-stu-id="7c92a-127">If you want to support a [_'look and pinch'_ interaction, you need to disable the hand ray](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray).</span></span> <span data-ttu-id="7c92a-128">시선 추적 샘플 장면에서 눈 + 손 동작을 사용하여 보다 풍부한 상호 작용을 보여줄 수 있도록 손 광선을 사용하지 않도록 설정했습니다( 예: [시선 지원 위치).](eye-tracking-eyes-and-hands.md)</span><span class="sxs-lookup"><span data-stu-id="7c92a-128">In our eye tracking sample scenes, we have disabled the hand ray to allow for showcasing richer interactions using eyes + hand motions - see for example [Eye-Supported Positioning](eye-tracking-eyes-and-hands.md).</span></span>

[<span data-ttu-id="7c92a-129">**2. 시선 포커스와 손 광선을 동시에 사용합니다.**</span><span class="sxs-lookup"><span data-stu-id="7c92a-129">**2. Use both eye focus and hand rays at the same time:**</span></span>](#2-independent-eye-gaze-specific-eyetrackingtarget)

<span data-ttu-id="7c92a-130">특정 이벤트를 트리거하고 여러 원거리 상호 작용 기술을 동시에 사용할 수 있는 포커스 포인터 유형을 보다 구체적으로 지정하려는 경우가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-130">There might be instances where you want to be more specific which type of focus pointers can trigger certain events and allow for simultaneously using multiple far interaction techniques.</span></span>

<span data-ttu-id="7c92a-131">예를 들어 앱에서 사용자는 원거리 광선을 사용하여 홀로그램 기계 설치를 조작할 수 있습니다. 예를 들어 멀리 떨어진 홀로그램 엔진 부품을 잡고 붙들고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-131">For example: In your app, a user can use far hand rays to manipulate some holographic mechanical setup - e.g., grab and hold some distant holographic engine parts and hold them in place.</span></span> <span data-ttu-id="7c92a-132">이렇게 하는 동안 사용자는 몇 가지 지침을 수행하고 일부 확인란을 표시하여 진행 상황을 기록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-132">While doing so, the user has to go through a number of instructions and record her/his progress by marking off some check boxes.</span></span> <span data-ttu-id="7c92a-133">사용자가 손을 _사용 중이지 않은_ 경우 확인란을 터치하거나 손 광선을 사용하여 선택하는 것이 직관적입니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-133">If the user has her/his hands _not busy_, it would be instinctual to simply touch the check box or select it using a hand ray.</span></span> <span data-ttu-id="7c92a-134">그러나 일부 홀로그램 엔진 부품을 배치하는 경우처럼 사용자가 손을 사용 중인 경우 사용자가 시선 응시를 사용하여 지침을 원활하게 스크롤하고 단순히 확인란을 보고 "확인란을 확인하세요!"라고 말할 수 있도록 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-134">However, if the user has her/his hands busy, as in our case holding some holographic engine parts in place, you want to enable the user to seamlessly scroll through the instructions using their eye gaze and to simply look at a check box and say "check it!".</span></span>

<span data-ttu-id="7c92a-135">이를 사용하려면 핵심 MRTK FocusHandlers와 독립적이며 아래에서 자세히 설명될 시선별 EyeTrackingTarget 스크립트를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-135">To enable this, you need to use eye-specific EyeTrackingTarget script that is independent from the core MRTK FocusHandlers and will be discussed further below.</span></span>

## <a name="1-use-generic-focus-and-pointer-handlers"></a><span data-ttu-id="7c92a-136">1. 제네릭 포커스 및 포인터 처리기 사용</span><span class="sxs-lookup"><span data-stu-id="7c92a-136">1. Use generic focus and pointer handlers</span></span>

<span data-ttu-id="7c92a-137">눈동자 추적이 올바르게 설정 된 경우 ( [눈 추적을 사용 하려면 기본 MRTK 설정](eye-tracking-basic-setup.md)참조) 사용자가 눈동자를 사용 하 여 holograms를 선택할 수 있도록 하는 것은 다른 포커스 입력 (예: 헤드 응시 또는 손 모양)의 경우와 동일 합니다. 이는 사용자의 요구 사항에 따라 MRTK 입력 포인터 프로필에서 주 포커스 형식을 정의 하 여 코드를 그대로 유지 하면서 holograms와 상호 작용 하는 유연한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-137">If eye tracking is set up correctly (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)), enabling users to select holograms using their eyes is the same as for any other focus input (e.g., head gaze or hand ray).This provides the great advantage of a flexible way to interact with your holograms by defining the main focus type in your MRTK Input Pointer Profile depending on your user's needs, while leaving your code untouched.</span></span> <span data-ttu-id="7c92a-138">이를 통해 코드 줄을 변경 하지 않고 head 또는 눈동자를 전환할 수 있으며, 원거리 상호 작용을 위해 손 광선을 눈 대상으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-138">This allows for switching between head or eye gaze without changing a line of code or replace hand rays with eye targeting for far interactions.</span></span>

### <a name="focusing-on-a-hologram"></a><span data-ttu-id="7c92a-139">홀로그램에 집중</span><span class="sxs-lookup"><span data-stu-id="7c92a-139">Focusing on a hologram</span></span>

<span data-ttu-id="7c92a-140">홀로그램의 초점을 감지 하려면 두 인터페이스 멤버 ( _OnFocusEnter_ 및 _OnFocusExit_)를 제공 하는 _' IMixedRealityFocusHandler '_ 인터페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-140">To detect when a hologram is focused, use the _'IMixedRealityFocusHandler'_ interface that provides you with two interface members: _OnFocusEnter_ and _OnFocusExit_.</span></span>

<span data-ttu-id="7c92a-141">다음은 색을 확인할 때 홀로그램의 색을 변경 하는 데 사용할 수 있는 간단한 예제입니다 [.](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap)</span><span class="sxs-lookup"><span data-stu-id="7c92a-141">Here is a simple example from [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) to change a hologram's color when being looked at.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a><span data-ttu-id="7c92a-142">포커스가 있는 홀로그램 선택</span><span class="sxs-lookup"><span data-stu-id="7c92a-142">Selecting a focused hologram</span></span>

<span data-ttu-id="7c92a-143">포커스가 있는 홀로그램을 선택 하려면 _Pointerhandler_ 를 사용 하 여 입력 이벤트를 수신 하 여 선택 항목을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-143">To select a focused hologram, use _PointerHandler_ to listen for input events to confirm a selection.</span></span>
<span data-ttu-id="7c92a-144">예를 들어 _IMixedRealityPointerHandler_ 를 추가 하면 단순 포인터 입력에 반응 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-144">For example, adding the _IMixedRealityPointerHandler_ will make them react to simple pointer input.</span></span>
<span data-ttu-id="7c92a-145">_IMixedRealityPointerHandler_ 인터페이스를 사용 하려면 다음 세 가지 인터페이스 멤버를 구현 해야 합니다. _Onpointerup_, _Onpointerup_ 및 _onpointerup_ 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-145">The _IMixedRealityPointerHandler_ interface requires implementing the following three interface members: _OnPointerUp_, _OnPointerDown_, and _OnPointerClicked_.</span></span>

<span data-ttu-id="7c92a-146">아래 예제에서는이를 확인 하 고 집기를 확인 하거나 "선택" 하 여 홀로그램의 색을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-146">In the example below, we change the color of a hologram by looking at it and pinching or saying "select".</span></span>
<span data-ttu-id="7c92a-147">이벤트를 트리거하는 데 필요한 작업은 `eventData.MixedRealityInputAction == selectAction` Unity 편집기에서의 유형을 설정할 수 있는 방법으로 정의 됩니다 `selectAction` (기본적으로 "선택" 동작).</span><span class="sxs-lookup"><span data-stu-id="7c92a-147">The required action to trigger the event is defined by `eventData.MixedRealityInputAction == selectAction` whereby we can set the type of `selectAction` in the Unity Editor - by default it's the "Select" action.</span></span> <span data-ttu-id="7c92a-148">_Mrtk_ 프로필 [](../input-actions.md)  ->  _입력_  ->  _입력 작업_ 을 통해 mrtk 프로필에서 사용 가능한 MixedRealityInputActions 유형을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-148">The types of available [MixedRealityInputActions](../input-actions.md) can be configured in the MRTK Profile via _MRTK Configuration Profile_ -> _Input_ -> _Input Actions_.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a><span data-ttu-id="7c92a-149">아이-응시 별 BaseEyeFocusHandler</span><span class="sxs-lookup"><span data-stu-id="7c92a-149">Eye-gaze-specific BaseEyeFocusHandler</span></span>

<span data-ttu-id="7c92a-150">아이 응시가 다른 포인터 입력과 매우 다를 수 있다는 것을 고려할 때, _눈_ 에 잘 대응 하 고 현재 기본 입력 포인터인 경우 포커스 입력에만 반응 하는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-150">Given that eye gaze can be very different to other pointer inputs, you may want to make sure to only react to the focus input if it is _eye gaze_ and it is currently the primary input pointer.</span></span>
<span data-ttu-id="7c92a-151">이러한 목적을 위해에서 파생 되는 [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) 시각 추적과 관련 된를 사용 [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-151">For this purpose, you would use the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) which is specific to eye tracking and which derives from the [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler).</span></span>
<span data-ttu-id="7c92a-152">앞에서 설명한 것 처럼 눈동자 응시 대상이 현재 기본 포인터 입력 인 경우에만 트리거됩니다 (즉, 손을 광선 활성).</span><span class="sxs-lookup"><span data-stu-id="7c92a-152">As mentioned before, it will only trigger if eye gaze targeting is currently the primary pointer input (i.e., no hand ray is active).</span></span> <span data-ttu-id="7c92a-153">자세한 내용은 [눈동자 및 손 모양 제스처를 지 원하는 방법](eye-tracking-eyes-and-hands.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7c92a-153">For more information, see [How to support eye gaze + hand gestures](eye-tracking-eyes-and-hands.md).</span></span>

<span data-ttu-id="7c92a-154">다음은의 예제입니다 `EyeTrackingDemo-03-Navigation` (자산/m RTK/예제/데모/EyeTracking/장면).</span><span class="sxs-lookup"><span data-stu-id="7c92a-154">Here is an example from `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).</span></span>
<span data-ttu-id="7c92a-155">이 데모에는 표시 되는 개체의 부분에 따라 설정 되는 두 개의 3D holograms 있습니다. 사용자가 홀로그램의 왼쪽에 표시 되 면 해당 부분은 사용자를 향하는 앞으로 천천히 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-155">In this demo, there are two 3D holograms that will turn depending on which part of the object is looked at: If the user looks at the left side of the hologram, then that part will slowly move towards the front facing the user.</span></span>
<span data-ttu-id="7c92a-156">오른쪽이 보이는 경우 해당 부분은 앞쪽으로 천천히 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-156">If the right side is looked at, then that part will slowly move to the front.</span></span>
<span data-ttu-id="7c92a-157">이 동작은 항상 활성화 하 고 싶지 않을 수 있는 동작이 며, 손 모양 또는 헤드 응시에 의해 실수로 트리거되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-157">This is a behavior that you may not want to have active at all times and also something that you may not want to accidentally trigger by a hand ray or head gaze.</span></span>
<span data-ttu-id="7c92a-158">가 [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) 연결 되 면 GameObject를 검토 하는 동안 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-158">Having the [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) attached, a GameObject will rotate while being looked at.</span></span>

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

<span data-ttu-id="7c92a-159">에서 사용 가능한 이벤트의 전체 목록은 API 설명서를 [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7c92a-159">Check the API documentation for a complete list of available events of the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler):</span></span>

- <span data-ttu-id="7c92a-160">**OnEyeFocusStart:** 이 대상의 collider와 교차 하는 모양 응시를 *시작* 하면 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-160">**OnEyeFocusStart:** Triggered once the eye gaze ray *starts* intersecting with this target's collider.</span></span>
- <span data-ttu-id="7c92a-161">**OnEyeFocusStay:** 아이 응시 광선이이 대상의 collider와 교차 *하는 동안* 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-161">**OnEyeFocusStay:** Triggered *while* the eye gaze ray is intersecting with this target's collider.</span></span>
- <span data-ttu-id="7c92a-162">**OnEyeFocusStop:** 이 대상의 collider와 교차 하는 눈동자를 *중지* 한 후에 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-162">**OnEyeFocusStop:** Triggered once the eye gaze ray *stops* intersecting with this target's collider.</span></span>
- <span data-ttu-id="7c92a-163">**OnEyeFocusDwell:** 지정 된 시간 동안 눈동자 응시 광선이이 대상의 collider와 교차 한 후에 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-163">**OnEyeFocusDwell:** Triggered once the eye gaze ray has intersected with this target's collider for a specified amount of time.</span></span>

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a><span data-ttu-id="7c92a-164">2. 독립적인 눈에 EyeTrackingTarget</span><span class="sxs-lookup"><span data-stu-id="7c92a-164">2. Independent eye-gaze-specific EyeTrackingTarget</span></span>

<span data-ttu-id="7c92a-165">마지막으로 스크립트를 통해 눈에 잘 맞는 입력을 다른 포커스 포인터와 완전히 독립적으로 처리할 수 있는 솔루션을 제공 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-165">Finally, we provide you with a solution that let's you treat eye-based input completely independent from other focus pointers via the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span></span>

<span data-ttu-id="7c92a-166">이는 다음과 같은 세 가지 _이점이_ 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-166">This has three _advantages_:</span></span>

- <span data-ttu-id="7c92a-167">홀로그램은 사용자의 눈 응시에만 반응 하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-167">You can make sure that the hologram is only reacting to the user's eye gaze.</span></span>
- <span data-ttu-id="7c92a-168">이는 현재 활성 기본 입력과는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-168">This is independent from the currently active primary input.</span></span> <span data-ttu-id="7c92a-169">따라서 여러 입력을 한 번에 처리할 수 있습니다. 예를 들어 빠른 시각 대상을 직접 제스처와 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-169">Hence, you can process multiple inputs at once - for example, combining fast eye targeting with hand gestures.</span></span>
- <span data-ttu-id="7c92a-170">Unity 편집기 또는 코드를 통해 기존 동작을 빠르고 편리 하 게 처리 하 고 다시 사용할 수 있도록 여러 Unity 이벤트가 이미 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-170">Several Unity events have already been set up to make it fast and convenient to handle and reuse existing behaviors from within the Unity Editor or via code.</span></span>

<span data-ttu-id="7c92a-171">또한 다음과 같은 몇 가지 _단점이 있습니다._</span><span class="sxs-lookup"><span data-stu-id="7c92a-171">There are also some _disadvantages:_</span></span>

- <span data-ttu-id="7c92a-172">별도의 입력을 개별적으로 처리 하는 데 더 많은 노력이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-172">More effort to handle separate inputs individually.</span></span>
- <span data-ttu-id="7c92a-173">세련 되지 않은 성능 저하: 대상만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-173">No elegant degradation: It only supports eye targeting.</span></span> <span data-ttu-id="7c92a-174">눈 추적이 작동 하지 않는 경우 약간의 추가 대체가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-174">If eye tracking is not working, you require some additional fallback.</span></span>

<span data-ttu-id="7c92a-175">_BaseFocusHandler_ 와 마찬가지로 _EyeTrackingTarget_ 는 unity 편집기 (아래 예제 참조)를 통해 또는 코드에서 _AddListener ()_ 를 사용 하 여 편리 하 게 수신할 수 있는 몇 가지 눈에 맞는 unity 이벤트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-175">Similar to the _BaseFocusHandler_, the _EyeTrackingTarget_ comes ready with several eye-gaze-specific Unity events that you can conveniently listen to either via the Unity Editor (see example below) or by using _AddListener()_ in code:</span></span>

- <span data-ttu-id="7c92a-176">OnLookAtStart()</span><span class="sxs-lookup"><span data-stu-id="7c92a-176">OnLookAtStart()</span></span>
- <span data-ttu-id="7c92a-177">WhileLookingAtTarget()</span><span class="sxs-lookup"><span data-stu-id="7c92a-177">WhileLookingAtTarget()</span></span>
- <span data-ttu-id="7c92a-178">OnLookAway()</span><span class="sxs-lookup"><span data-stu-id="7c92a-178">OnLookAway()</span></span>
- <span data-ttu-id="7c92a-179">OnDwell ()</span><span class="sxs-lookup"><span data-stu-id="7c92a-179">OnDwell()</span></span>
- <span data-ttu-id="7c92a-180">OnSelected ()</span><span class="sxs-lookup"><span data-stu-id="7c92a-180">OnSelected()</span></span>

<span data-ttu-id="7c92a-181">다음에서는 _EyeTrackingTarget_ 를 사용 하는 방법에 대 한 몇 가지 예제를 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-181">In the following, we walk you through a few examples for how to use _EyeTrackingTarget_.</span></span>

### <a name="example-1-eye-supported-smart-notifications"></a><span data-ttu-id="7c92a-182">예제 #1: 눈동자 지원 스마트 알림</span><span class="sxs-lookup"><span data-stu-id="7c92a-182">Example #1: Eye-supported smart notifications</span></span>

<span data-ttu-id="7c92a-183">`EyeTrackingDemo-02-TargetSelection`(Asset/MRTK/example/데모/EyeTracking/장면)에서 눈동자 응시에 반응 하는 _' 스마트 attentive 알림 '_ 의 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-183">In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes), you can find an example for _'smart attentive notifications'_ that react to your eye gaze.</span></span>
<span data-ttu-id="7c92a-184">이러한 상자는 장면에 배치할 수 있는 3D 텍스트 상자 이며 쉽게 읽을 수 있도록 사용자를 매끄럽게 확대 하 고 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-184">These are 3D text boxes that can be placed in the scene and that will smoothly enlarge and turn toward the user when being looked at to ease legibility.</span></span> <span data-ttu-id="7c92a-185">사용자가 알림을 읽는 동안 정보가 선명 하 고 명확 하 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-185">While the user is reading the notification, the information keeps getting displayed crisp and clear.</span></span> <span data-ttu-id="7c92a-186">이 정보를 읽고 알림에서 벗어나면 알림이 자동으로 해제 되 고 페이드 아웃 됩니다. 이를 위해 다음과 같은 몇 가지 일반적인 동작 스크립트가 눈 추적에 국한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-186">After reading it and looking away from the notification, the notification will automatically be dismissed and fades out. To achieve all this, there are a few generic behavior scripts that are not specific to eye tracking at all, such as:</span></span>

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

<span data-ttu-id="7c92a-187">이 방법의 장점은 여러 이벤트에서 동일한 스크립트를 다시 사용할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-187">The advantage of this approach is that the same scripts can be reused by various events.</span></span> <span data-ttu-id="7c92a-188">예를 들어, 홀로그램은 음성 명령을 기반으로 하거나 가상 단추를 누른 후 사용자의 연결을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-188">For example, a hologram may start facing the user based on a voice commands or after pressing a virtual button.</span></span> <span data-ttu-id="7c92a-189">이러한 이벤트를 트리거하려면 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) GameObject에 연결된 스크립트에서 실행해야 하는 메서드를 참조하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-189">To trigger these events, you can simply reference the methods that should be executed in the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script that is attached to your GameObject.</span></span>

<span data-ttu-id="7c92a-190">_'스마트 들여쓰기 알림'의_ 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-190">For the example of the _'smart attentive notifications'_, the following happens:</span></span>

- <span data-ttu-id="7c92a-191">**OnLookAtStart()**: 알림이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-191">**OnLookAtStart()**: The notification starts to...</span></span>
  - <span data-ttu-id="7c92a-192">*FaceUser.Engage:* ... 사용자 쪽으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-192">*FaceUser.Engage:* ... turn toward the user.</span></span>
  - <span data-ttu-id="7c92a-193">*ChangeSize.Engage:* ... _크기(지정된 최대 배율까지)_ 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-193">*ChangeSize.Engage:* ... increase in size _(up to a specified maximum scale)_.</span></span>
  - <span data-ttu-id="7c92a-194">*BlendOut.Engage:* ... 가 더 혼합되기 _시작합니다(더 미묘한 유휴 상태에 있는 후)._</span><span class="sxs-lookup"><span data-stu-id="7c92a-194">*BlendOut.Engage:* ... starts to blend in more _(after being at a more subtle idle state)_.</span></span>  

- <span data-ttu-id="7c92a-195">**OnDwell()**: 알림이 충분히 조회되었다는 것을 _BlendOut_ 스크립트에 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-195">**OnDwell()**: Informs the _BlendOut_ script that the notification has been looked at sufficiently.</span></span>

- <span data-ttu-id="7c92a-196">**OnLookAway()**: 알림이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-196">**OnLookAway()**: The notification starts to...</span></span>
  - <span data-ttu-id="7c92a-197">*FaceUser.Disengage:* ... 를 원래 방향으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-197">*FaceUser.Disengage:* ... turn back to its original orientation.</span></span>
  - <span data-ttu-id="7c92a-198">*ChangeSize.Disengage:* ... 원래 크기로 다시 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-198">*ChangeSize.Disengage:* ... decrease back to its original size.</span></span>
  - <span data-ttu-id="7c92a-199">*BlendOut.Disengage:* ... 혼합 시작 - _OnDwell()이_ 트리거된 경우 완전히 혼합되어 제거되고, 그렇지 않으면 유휴 상태로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-199">*BlendOut.Disengage:* ... starts to blend out - If _OnDwell()_ was triggered, blend out completely and destroy, otherwise back to its idle state.</span></span>

<span data-ttu-id="7c92a-200">**디자인 고려 사항:** 여기서는 사용자의 시선 응시에 너무 빠르게 반응하여 불편을 유발하지 않도록 이러한 동작의 속도를 신중하게 조정하는 것이 이 환경의 핵심입니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-200">**Design consideration:** The key to an enjoyable experience here is to carefully tune the speed of any of these behaviors to avoid causing discomfort by reacting to the user’s eye gaze too quickly all the time.</span></span>
<span data-ttu-id="7c92a-201">그렇지 않으면 매우 부담스울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-201">Otherwise this can quickly feel extremely overwhelming.</span></span>

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a><span data-ttu-id="7c92a-202">예제 #2: 홀로그램 gem이 보고 있을 때 느리게 회전합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-202">Example #2: Holographic gem rotates slowly when looking at it</span></span>

<span data-ttu-id="7c92a-203">예제 #1 마찬가지로, 볼 때 일정한 방향과 일정한 속도로 느린 회전을 하는 홀로그램 `EyeTrackingDemo-02-TargetSelection` gem(Assets/MRTK/Examples/Demos/EyeTracking/Scenes) 장면에 대한 호버 피드백을 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-203">Similar to Example #1, we can easily create a hover feedback for our holographic gems in `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) scene that will slowly rotate in a constant direction and at a constant speed (in contrast to the rotation example from above) when being looked at.</span></span> <span data-ttu-id="7c92a-204">_EyeTrackingTarget의_ _WhileLookingAtTarget()_ 이벤트에서 홀로그램 gem의 회전을 트리거하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-204">All you need is to trigger the rotation of the holographic gem from the _EyeTrackingTarget_'s _WhileLookingAtTarget()_ event.</span></span> <span data-ttu-id="7c92a-205">다음은 몇 가지 세부 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-205">Here are a few more details:</span></span>

1. <span data-ttu-id="7c92a-206">연결된 GameObject를 회전하는 public 함수를 포함하는 제네릭 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-206">Create a generic script that includes a public function to rotate the GameObject it is attached to.</span></span> <span data-ttu-id="7c92a-207">다음은 Unity 편집기에서 회전 방향과 속도를 조정할 수 있는 RotateWithConstSpeedDir의 예입니다 _._</span><span class="sxs-lookup"><span data-stu-id="7c92a-207">Below is an example from _RotateWithConstSpeedDir.cs_ where we can tweak the rotation direction and speed from the Unity Editor.</span></span>

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. <span data-ttu-id="7c92a-208">스크립트를 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 대상 GameObject에 추가 하 고 아래 스크린샷에 표시 된 것 처럼 UnityEvent 트리거에서 _RotateTarget ()_ 함수를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-208">Add the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to your target GameObject and reference the _RotateTarget()_ function in the UnityEvent trigger as shown the screenshot below:</span></span>

    ![EyeTrackingTarget 샘플](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a><span data-ttu-id="7c92a-210">예제 #3: 이러한 보석 즉, _다중 모달 눈동자-응시 지원 대상 선택_</span><span class="sxs-lookup"><span data-stu-id="7c92a-210">Example #3: Pop those gems aka _multi-modal eye-gaze-supported target selection_</span></span>

<span data-ttu-id="7c92a-211">이전 예제에서는 대상이 무엇 인지 여부와이에 대 한 응답을 트리거하는 방법을 쉽게 감지 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-211">In the previous example, we have shown how easy it is to detect whether a target is looked at and how to trigger a reaction to that.</span></span> <span data-ttu-id="7c92a-212">다음으로에서 _Onselected ()_ 이벤트를 사용 하 여 보석을 폭발 하 게 합니다 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) .</span><span class="sxs-lookup"><span data-stu-id="7c92a-212">Next, let's make the gems explode using the _OnSelected()_ event from the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget).</span></span> <span data-ttu-id="7c92a-213">흥미로운 부분은 선택이 트리거되는 *방법* 입니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-213">The interesting part is *how* the selection is triggered.</span></span> <span data-ttu-id="7c92a-214">를 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 사용 하면 여러 가지 방법으로 선택 항목을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-214">The [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) allows for quickly assigning different ways to invoke a selection:</span></span>

- <span data-ttu-id="7c92a-215">핸드 _제스처_: ' 선택 작업 '을 ' select '로 설정 하면 기본 손 모양 제스처를 사용 하 여 선택 항목을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-215">_Pinch gesture_: Setting the 'Select Action' to 'Select' uses the default hand gesture to trigger the selection.</span></span>
<span data-ttu-id="7c92a-216">즉, 사용자가 손 모양 및 손가락을 함께 사용 하 여 선택 영역을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-216">This means that the user can simply raise their hand and pinch their thumb and index finger together to confirm the selection.</span></span>

- <span data-ttu-id="7c92a-217">_"Select"_: 홀로그램을 선택 하려면 " _선택_ " 이라는 기본 음성 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-217">Say _"Select"_: Use the default voice command _"Select"_ for selecting a hologram.</span></span>

- <span data-ttu-id="7c92a-218">_"폭발"_ 또는 _"Pop"_: 사용자 지정 음성 명령을 사용 하려면 다음 두 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-218">Say _"Explode"_ or _"Pop"_: To use custom voice commands, you need to follow two steps:</span></span>
    1. <span data-ttu-id="7c92a-219">사용자 지정 작업 (예: _"DestroyTarget"_ ) 설정</span><span class="sxs-lookup"><span data-stu-id="7c92a-219">Set up a custom action such as _"DestroyTarget"_</span></span>
        - <span data-ttu-id="7c92a-220">_Mrtk-> 입력 > 입력 작업_ 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-220">Navigate to _MRTK -> Input -> Input Actions_</span></span>
        - <span data-ttu-id="7c92a-221">"새 작업 추가"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-221">Click "Add a new action"</span></span>

    2. <span data-ttu-id="7c92a-222">_"폭발"_ 또는 _"Pop"_ 와 같이이 작업을 트리거하는 음성 명령을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-222">Set up the voice commands that trigger this action such as _"Explode"_ or _"Pop"_</span></span>
        - <span data-ttu-id="7c92a-223">_Mrtk-> 입력-> Speech_ 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-223">Navigate to _MRTK -> Input -> Speech_</span></span>
        - <span data-ttu-id="7c92a-224">"새 음성 명령 추가"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-224">Click "Add a new speech command"</span></span>
            - <span data-ttu-id="7c92a-225">방금 만든 작업 연결</span><span class="sxs-lookup"><span data-stu-id="7c92a-225">Associate the action you just created</span></span>
            - <span data-ttu-id="7c92a-226">단추 누르기를 통해 작업을 트리거할 수 있도록 _KeyCode_ 을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-226">Assign a _KeyCode_ to allow for triggering the action via a button press</span></span>

![음성 명령 EyeTrackingTarget 샘플](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

<span data-ttu-id="7c92a-228">gem을 선택하면 소리가 나고 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-228">When a gem is selected it will explode, making a sound and disappear.</span></span> <span data-ttu-id="7c92a-229">스크립트에서 [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-229">This is handled by the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span></span> <span data-ttu-id="7c92a-230">다음과 같은 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-230">You have two options:</span></span>

- <span data-ttu-id="7c92a-231">**Unity 편집기에서 다음을 수행합니다.** 각 gem 템플릿에 연결된 스크립트를 Unity 편집기의 OnSelected() Unity 이벤트에 연결하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-231">**In the Unity Editor:** You could simply link the script that is attached to each of our gem templates to the OnSelected() Unity event in the Unity Editor.</span></span>
- <span data-ttu-id="7c92a-232">**코드에서:** GameObjects를 끌어서 놓지 않으려면 이벤트 수신기를 스크립트에 직접 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-232">**In code:** If you don't want to drag and drop GameObjects around, you can also simply add a event listener directly to your script.</span></span>  
<span data-ttu-id="7c92a-233">스크립트에서 수행된 방법의 예제는 다음과 같습니다. [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect)</span><span class="sxs-lookup"><span data-stu-id="7c92a-233">Here's an example from how we did it in the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span></span>

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a><span data-ttu-id="7c92a-234">예제 #4: 손 광선과 시선 응시 입력을 함께 사용</span><span class="sxs-lookup"><span data-stu-id="7c92a-234">Example #4: Use hand rays and eye gaze input together</span></span>

<span data-ttu-id="7c92a-235">손 광선은 머리 및 시선 응시 대상보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-235">Hand rays take priority over head and eye gaze targeting.</span></span> <span data-ttu-id="7c92a-236">즉, 손 광선을 사용하는 경우 손을 볼 때 손 광선이 기본 포인터 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-236">This means, if hand rays are enabled, the moment the hands come into view, the hand ray will act as the primary pointer.</span></span>
<span data-ttu-id="7c92a-237">그러나 사용자가 특정 홀로그램을 보고 있는지 여부를 감지하면서 손 광선을 사용하려는 상황이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-237">However, there might be situations in which you want to use hand rays while still detecting whether a user is looking at a certain hologram.</span></span> <span data-ttu-id="7c92a-238">아주 쉽습니다!</span><span class="sxs-lookup"><span data-stu-id="7c92a-238">Easy!</span></span> <span data-ttu-id="7c92a-239">기본적으로 다음 두 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-239">Essentially you require two steps:</span></span>

<span data-ttu-id="7c92a-240">**1. 손 광선 사용:** 손 광선을 사용하도록 설정하려면 _Mixed Reality Toolkit -> 입력 -> 포인터로_ 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-240">**1. Enable the hand ray:** To enable the hand ray, go to _Mixed Reality Toolkit -> Input -> Pointers_.</span></span>
<span data-ttu-id="7c92a-241">모든 시선 추적 데모 장면에 대해 Mixed Reality 도구 키트가 한 번 구성된 _EyeTrackingDemo-00-RootScene에_ _EyeTrackingDemoPointerProfile이_ 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-241">In the _EyeTrackingDemo-00-RootScene_ where the Mixed Reality Toolkit is configured once for all of the eye tracking demo scenes, you should see the _EyeTrackingDemoPointerProfile_.</span></span>
<span data-ttu-id="7c92a-242">새 _입력 프로필을_ 처음부터 만들거나 현재 시선 추적 프로필을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-242">You can either create a new _Input Profile_ from scratch or adapt the current eye tracking one:</span></span>

- <span data-ttu-id="7c92a-243">**처음부터:** _포인터_ 탭의 상황에 맞는 메뉴에서 _DefaultMixedRealityInputPointerProfile을_ 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-243">**From scratch:** In the _Pointers_ tab, select the _DefaultMixedRealityInputPointerProfile_ from the context menu.</span></span>
<span data-ttu-id="7c92a-244">손 광선이 이미 활성화된 기본 포인터 프로필입니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-244">This is the default pointer profile that already has the hand ray enabled!</span></span>
<span data-ttu-id="7c92a-245">기본 커서(불투명 흰색 점)를 변경하려면 프로필을 복제하고 사용자 지정 포인터 프로필을 만들기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-245">To change the default cursor (an opaque white dot), simply clone the profile and create your own custom pointer profile.</span></span>
<span data-ttu-id="7c92a-246">그런 _다음, DefaultCursor를_ 응시 커서 프리팹 _아래의 EyeGazeCursor로_ 바꿉니다. </span><span class="sxs-lookup"><span data-stu-id="7c92a-246">Then replace _DefaultCursor_ with _EyeGazeCursor_ under _Gaze Cursor Prefab_.</span></span>  
- <span data-ttu-id="7c92a-247">**기존 _EyeTrackingDemoPointerProfile_ 기반:** _EyeTrackingDemoPointerProfile을_ 두 번 클릭하고 포인터 옵션 아래에 다음 항목을 _추가합니다._</span><span class="sxs-lookup"><span data-stu-id="7c92a-247">**Based on the existing _EyeTrackingDemoPointerProfile_:** Double-click the _EyeTrackingDemoPointerProfile_ and add the following entry under _Pointer Options_:</span></span>
  - <span data-ttu-id="7c92a-248">**컨트롤러 유형:** ' 트레일러 식 ', ' Windows Mixed Reality '</span><span class="sxs-lookup"><span data-stu-id="7c92a-248">**Controller Type:** 'Articulated Hand', 'Windows Mixed Reality'</span></span>
  - <span data-ttu-id="7c92a-249">**손:** 일부</span><span class="sxs-lookup"><span data-stu-id="7c92a-249">**Handedness:** Any</span></span>
  - <span data-ttu-id="7c92a-250">**포인터 Prefab:** DefaultControllerPointer</span><span class="sxs-lookup"><span data-stu-id="7c92a-250">**Pointer Prefab:** DefaultControllerPointer</span></span>

<span data-ttu-id="7c92a-251">**2. 홀로그램이** 확인 된 것을 검색 합니다. [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 위에서 설명한 대로 스크립트를 사용 하 여 홀로그램을 확인 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-251">**2. Detect that a hologram is looked at:** Use the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to enable detecting that a hologram is looked at as described above.</span></span> <span data-ttu-id="7c92a-252">또한 `FollowEyeGaze` 핸드 광선 사용 여부에 관계 없이 눈에 볼 수 있는 홀로그램 (예: 커서)을 보여 주는 샘플 스크립트를 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-252">You can also take a look at the `FollowEyeGaze` sample script for inspiration as this is showing a hologram following your eye gaze (e.g., a cursor) whether hand rays are enabled or not.</span></span>

<span data-ttu-id="7c92a-253">이제 눈 추적 데모 장면을 시작할 때 손으로 그린 빛이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-253">Now, when you start the eye tracking demo scenes, you should see a ray coming from your hands.</span></span>
<span data-ttu-id="7c92a-254">예를 들어 눈 추적 대상 선택 데모에서 반투명 원은 계속 눈에 보이는 응시를 사용 하 고 있으며, 보석은 어디에 있든, 아니면 위쪽 장면 메뉴 단추를 사용 하 여 기본 입력 포인터를 대신 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c92a-254">For example, in the eye tracking target selection demo, the semi-transparent circle is still following your eye gaze and the gems respond to whether they are looked at or not, while the top scene menu buttons use the primary input pointer (your hands) instead.</span></span>

---
[<span data-ttu-id="7c92a-255">"MixedRealityToolkit의 눈동자 추적"으로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="7c92a-255">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
