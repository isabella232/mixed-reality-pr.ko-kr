---
title: 상호 작용 가능
description: MRTK의 Interactable 스크립트 구성 요소에 대 한 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Interactable, 이벤트,
ms.openlocfilehash: f141a394ec9395e0a27cc964caeb66654fb6fe08
ms.sourcegitcommit: 47c402dc8e588817ce60229bf019170fa36f3045
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107581565"
---
# <a name="interactable"></a><span data-ttu-id="cd9e5-104">상호 작용 가능</span><span class="sxs-lookup"><span data-stu-id="cd9e5-104">Interactable</span></span>

![상호 작용 가능](../images/interactable/InteractableExamples.png)

<span data-ttu-id="cd9e5-106">[`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable)이 구성 요소는 모든 개체를 쉽게 *interactable* 하 고 입력에 응답할 수 있도록 하는 일대다 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-106">The [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) component is an all-in-one container to make any object easily *interactable* and responsive to input.</span></span> <span data-ttu-id="cd9e5-107">Interactable는 터치, 손 광선, 음성 등을 비롯 한 모든 유형의 입력에 대해 모두 catch 역할을 하며 이러한 상호 작용을 [이벤트](#events) 및 [시각적 테마](visual-themes.md) 응답으로 깔때기 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-107">Interactable acts as a catch-all for all types of input including touch, hand rays, speech etc and funnel these interactions into [events](#events) and [visual theme](visual-themes.md) responses.</span></span> <span data-ttu-id="cd9e5-108">이 구성 요소를 사용 하면 단추를 만들고 포커스를 가진 개체의 색을 변경 하는 등의 작업을 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-108">This component provides an easy way to make buttons, change color on objects with focus, and more.</span></span>

## <a name="how-to-configure-interactable"></a><span data-ttu-id="cd9e5-109">Interactable를 구성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="cd9e5-109">How to configure Interactable</span></span>

<span data-ttu-id="cd9e5-110">구성 요소는 구성의 세 가지 주요 섹션을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-110">The component allows for three primary sections of configuration:</span></span>

1) [<span data-ttu-id="cd9e5-111">일반 입력 구성</span><span class="sxs-lookup"><span data-stu-id="cd9e5-111">General input configuration</span></span>](#general-input-settings)
1) <span data-ttu-id="cd9e5-112">여러 Gameobject를 대상으로 하는 [시각적 테마](visual-themes.md)</span><span class="sxs-lookup"><span data-stu-id="cd9e5-112">[Visual Themes](visual-themes.md) targeted against multiple GameObjects</span></span>
1) [<span data-ttu-id="cd9e5-113">이벤트 처리기</span><span class="sxs-lookup"><span data-stu-id="cd9e5-113">Event handlers</span></span>](#events)

### <a name="general-input-settings"></a><span data-ttu-id="cd9e5-114">일반 입력 설정</span><span class="sxs-lookup"><span data-stu-id="cd9e5-114">General input settings</span></span>

![일반 Interactable 설정](../images/interactable/InputFeatures_short.png)

<span data-ttu-id="cd9e5-116">**상태**</span><span class="sxs-lookup"><span data-stu-id="cd9e5-116">**States**</span></span>

<span data-ttu-id="cd9e5-117">*상태* 는 [Interactable 프로필과](#interactable-profiles) [시각적 테마](visual-themes.md)에 대해 press와 같은 상호 작용 단계를 정의 하는 [스크립트가 tabletableobject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-117">*States* is a [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) parameter that defines the interactions phases, like press or observed, for [Interactable Profiles](#interactable-profiles) and [Visual Themes](visual-themes.md).</span></span>

<span data-ttu-id="cd9e5-118">**Defaultinteractablestates** (ASSET/MRTK/SDK/FEATURES/UX/Interactable/States/defaultInteractable)는 MRTK와 함께 제공 되며  구성 요소의 기본 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-118">The **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) ships with MRTK out-of-box and is the default parameter for *Interactable* components.</span></span>

![Inspector의 상태 스크립트가 아닌 개체 예제](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="cd9e5-120">*Defaultinteractablestates* 자산은 네 가지 상태를 포함 하며 [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) 상태 모델 구현을 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-120">The *DefaultInteractableStates* asset contains four states and utilizes the [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) state model implementation.</span></span>

* <span data-ttu-id="cd9e5-121">**기본값**: 아무것도 발생 하지 않습니다 .이는 가장 격리 된 기본 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-121">**Default**: Nothing is happening, this is the most isolated base state.</span></span>

* <span data-ttu-id="cd9e5-122">**Focus**: 개체가 가리키고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-122">**Focus**: The object is being pointed at.</span></span> <span data-ttu-id="cd9e5-123">이는 단일 상태 이며, 현재 다른 상태는 설정 되지 않지만 순위 기본값을 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-123">This is a single state, no other states are currently set, but it will out rank Default.</span></span>

* <span data-ttu-id="cd9e5-124">**키를 누르면** 개체가 가리키고 단추를 누르면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-124">**Press**: The object is being pointed at and a button or hand is pressing.</span></span> <span data-ttu-id="cd9e5-125">누르기 상태 아웃은 기본 및 포커스의 순위를 매깁니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-125">The Press state out ranks Default and Focus.</span></span> <span data-ttu-id="cd9e5-126">이 상태는 또한 물리적 인쇄기로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-126">This state will also get set as a fallback to Physical Press.</span></span>

* <span data-ttu-id="cd9e5-127">**사용 안 함**: 단추가 대화형이 아니어야 하며, 어떤 이유로 든이 단추를 사용할 수 없는 경우 사용자에 게 알려 주는 시각적 피드백이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-127">**Disabled**: The button should not be interactive and visual feedback will let the user know if for some reason this button is not usable at this time.</span></span> <span data-ttu-id="cd9e5-128">이론적으로 사용 하지 않도록 설정 된 상태는 다른 모든 상태를 포함할 수 있지만 사용 하도록 설정 된 경우 사용 안 함 상태는 다른 모든 상태를가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-128">In theory, the disabled state could contain all other states, but when Enabled is turned off, the Disabled state trumps all other states.</span></span>

<span data-ttu-id="cd9e5-129">비트 값 (#)은 목록에 있는 순서에 따라 상태에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-129">A bit value (#) is assigned to the state depending on the order in the list.</span></span>

> [!NOTE]
> <span data-ttu-id="cd9e5-130">*Interactable* 구성 요소를 만들 때 **Defaultinteractablestates** (asset/MRTK/SDK/Features/UX/Interactable/States/defaultinteractablestates)를 활용 하는 것이 일반적으로 권장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-130">It is generally recommended to utilize the **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) when creating *Interactable* components.</span></span>
>
> <span data-ttu-id="cd9e5-131">그러나 테마를 구동 하는 데 사용할 수 있는 17 개의 Interactable 상태를 사용할 수 있지만 일부는 다른 구성 요소에서 구동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-131">However, there are 17 Interactable states available that can be used to drive themes, though some are meant to be driven by other components.</span></span> <span data-ttu-id="cd9e5-132">다음은 기본 제공 기능을 사용 하는 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-132">Here is a list of those with built-in functionality.</span></span>
>
> * <span data-ttu-id="cd9e5-133">방문 됨: Interactable를 클릭 했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-133">Visited: the Interactable has been clicked.</span></span>
> * <span data-ttu-id="cd9e5-134">전환 됨: 단추가 전환 된 상태 이거나 차원 인덱스가 홀수입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-134">Toggled: The button is in a toggled state or Dimension index is an odd number.</span></span>
> * <span data-ttu-id="cd9e5-135">제스처: 손 또는 컨트롤러를 눌렀다 원래 위치에서 이동 했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-135">Gesture: The hand or controller was pressed and has moved from the original position.</span></span>
> * <span data-ttu-id="cd9e5-136">VoiceCommand: 음성 명령이 Interactable를 트리거하는 데 사용 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-136">VoiceCommand: A speech command was used to trigger the Interactable.</span></span>
> * <span data-ttu-id="cd9e5-137">실제 터치: 터치 입력이 현재 검색 되 고를 사용 하도록 설정 하는 데 사용 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-137">PhysicalTouch: A touch input is currently detected, use [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) to enable.</span></span>
> * <span data-ttu-id="cd9e5-138">잡기: 현재는 개체의 경계를 대상으로 하는 데를 사용 합니다. [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)</span><span class="sxs-lookup"><span data-stu-id="cd9e5-138">Grab: A hand is currently grabbing in the bounds of the object, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) to enable</span></span>

<span data-ttu-id="cd9e5-139">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="cd9e5-139">**Enabled**</span></span>

<span data-ttu-id="cd9e5-140">Interactable를 사용 하도록 설정할지 여부를 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-140">Toggles whether an Interactable will start enabled or not.</span></span> <span data-ttu-id="cd9e5-141">이는 [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 코드의에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-141">This corresponds to the [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) in code.</span></span>

<span data-ttu-id="cd9e5-142">*Interactable의* Enabled 속성이 GameObject/Component를 통해 구성 된 enabled 속성과 다릅니다 (즉,</span><span class="sxs-lookup"><span data-stu-id="cd9e5-142">An *Interactable's* enabled property is different than the enabled property configured via GameObject/Component (i.e</span></span> <span data-ttu-id="cd9e5-143">SetActive 등).</span><span class="sxs-lookup"><span data-stu-id="cd9e5-143">SetActive etc).</span></span> <span data-ttu-id="cd9e5-144">GameObject 또는 *Interactable* MonoBehaviour를 사용 하지 않도록 설정 하면 입력, 시각적 테마, 이벤트 등을 포함 하 여 클래스의 모든 항목을 실행할 수 없습니다. Via를 사용 하지 않도록 설정 하면 [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 대부분의 입력 처리를 사용할 수 없으며 관련 된 입력 상태를 다시 설정</span><span class="sxs-lookup"><span data-stu-id="cd9e5-144">Disabling the GameObject or *Interactable* MonoBehaviour will disable everything in the class from running including input, visual themes, events, etc. Disabling via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) will disable most input handling, resetting related input states.</span></span> <span data-ttu-id="cd9e5-145">그러나 클래스는 모든 프레임을 계속 실행 하 고 무시 되는 입력 이벤트를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-145">However, the class will still run every frame and receive input events which will be ignored.</span></span> <span data-ttu-id="cd9e5-146">이는 시각적 테마를 통해 수행할 수 있는 비활성 상태로 Interactable를 표시 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-146">This is useful for displaying the Interactable in a disabled state which can be done via Visual Themes.</span></span> <span data-ttu-id="cd9e5-147">이에 대 한 일반적인 예는 모든 필수 입력 필드가 완료 되기를 기다리는 제출 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-147">A typical example of this would be a submit button waiting for all the required input fields to be completed.</span></span>

<span data-ttu-id="cd9e5-148">**입력 작업**</span><span class="sxs-lookup"><span data-stu-id="cd9e5-148">**Input Actions**</span></span>

<span data-ttu-id="cd9e5-149">*Interactable* 구성 요소가 응답 해야 하는 입력 구성 또는 컨트롤러 매핑 프로필에서 [입력 작업](../input/input-actions.md) 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-149">Select the [input action](../input/input-actions.md) from the input configuration or controller mapping profile that the *Interactable* component should react to.</span></span>

<span data-ttu-id="cd9e5-150">이 속성은 런타임에를 통해 코드에서 구성할 수 있습니다 [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .</span><span class="sxs-lookup"><span data-stu-id="cd9e5-150">This property can be configured at runtime in code via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction).</span></span>

<span data-ttu-id="cd9e5-151">**IsGlobal**</span><span class="sxs-lookup"><span data-stu-id="cd9e5-151">**IsGlobal**</span></span>

<span data-ttu-id="cd9e5-152">True 이면 구성 요소가 선택한 [입력 동작](../input/input-actions.md)에 대 한 전역 입력 수신기로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-152">If true, this will mark the component as a global input listener for the selected [input action](../input/input-actions.md).</span></span> <span data-ttu-id="cd9e5-153">기본 동작은 false 이며,이 *Interactable* Collider/GameObject만 입력이 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-153">Default behavior is false which will restrict input to only this *Interactable* collider/GameObject.</span></span>

<span data-ttu-id="cd9e5-154">이 속성은 런타임에를 통해 코드에서 구성할 수 있습니다 [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) .</span><span class="sxs-lookup"><span data-stu-id="cd9e5-154">This property can be configured at runtime in code via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal).</span></span>

<span data-ttu-id="cd9e5-155">**Speech 명령**</span><span class="sxs-lookup"><span data-stu-id="cd9e5-155">**Speech Command**</span></span>

<span data-ttu-id="cd9e5-156">음성 상호 작용에 대 한 OnClick 이벤트를 트리거하는 MRTK Speech Commands 프로필의 [음성 명령](../input/speech.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-156">[Speech command](../input/speech.md), from the MRTK Speech Commands Profile, to trigger an OnClick event for voice interaction.</span></span>

<span data-ttu-id="cd9e5-157">이 속성은 런타임에를 통해 코드에서 구성할 수 있습니다 [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) .</span><span class="sxs-lookup"><span data-stu-id="cd9e5-157">This property can be configured at runtime in code via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand).</span></span>

<span data-ttu-id="cd9e5-158">**포커스 필요**</span><span class="sxs-lookup"><span data-stu-id="cd9e5-158">**Requires Focus**</span></span>

<span data-ttu-id="cd9e5-159">True 이면 음성 명령은 포인터의 포커스가 이미 있는 경우에만 *Interactable* 를 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-159">If true, the voice command will only activate the *Interactable* if and only if it already has focus from a pointer.</span></span> <span data-ttu-id="cd9e5-160">False 이면 *Interactable* 가 선택한 음성 명령의 전역 수신기 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-160">If false, then the *Interactable* will act as a global listener for the selected voice command.</span></span> <span data-ttu-id="cd9e5-161">여러 전역 음성 수신기를 장면에서 구성 하기 어려울 수 있으므로 기본 동작은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-161">The default behavior is true, as multiple global speech listeners can be difficult to organize in a scene.</span></span>

<span data-ttu-id="cd9e5-162">이 속성은 런타임에를 통해 코드에서 구성할 수 있습니다 [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) .</span><span class="sxs-lookup"><span data-stu-id="cd9e5-162">This property can be configured at runtime in code via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus).</span></span>

<span data-ttu-id="cd9e5-163">**선택 모드**</span><span class="sxs-lookup"><span data-stu-id="cd9e5-163">**Selection Mode**</span></span>

<span data-ttu-id="cd9e5-164">이 속성은 선택 논리를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-164">This property defines the selection logic.</span></span> <span data-ttu-id="cd9e5-165">*Interactable* 을 클릭 하면 다음 *차원* 수준으로 반복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-165">When an *Interactable* is clicked, it iterates into a next *Dimension* level.</span></span> <span data-ttu-id="cd9e5-166">*차원은* 순위와 비슷하며 입력 외부의 상태를 정의 합니다 (즉,</span><span class="sxs-lookup"><span data-stu-id="cd9e5-166">*Dimensions* is similar to rank and defines a state outside of inputs (i.e</span></span> <span data-ttu-id="cd9e5-167">포커스, 누르기 등).</span><span class="sxs-lookup"><span data-stu-id="cd9e5-167">focus, press etc).</span></span> <span data-ttu-id="cd9e5-168">이는 단추와 연결 된 다른 다중 순위 상태 또는 설정/해제 상태를 정의 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-168">They are useful for defining Toggle states or other multi-rank states associated with a button.</span></span> <span data-ttu-id="cd9e5-169">현재 차원 수준은에 의해 추적 됩니다 `Interactable.DimensionIndex` .</span><span class="sxs-lookup"><span data-stu-id="cd9e5-169">The current Dimension level is tracked by `Interactable.DimensionIndex`.</span></span>

<span data-ttu-id="cd9e5-170">사용 가능한 선택 모드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-170">The selection modes available are:</span></span>

* <span data-ttu-id="cd9e5-171">**단추**  -  *차원* = 1, 클릭 가능한 단순 *Interactable*</span><span class="sxs-lookup"><span data-stu-id="cd9e5-171">**Button** - *Dimensions* = 1, simple clickable *Interactable*</span></span>
* <span data-ttu-id="cd9e5-172">**토글**  -  *차원* = 2, *Interactable* *에서* / *꺼짐* 상태 사이 대체</span><span class="sxs-lookup"><span data-stu-id="cd9e5-172">**Toggle** - *Dimensions* = 2, *Interactable* alternates between *on*/*off* state</span></span>
* <span data-ttu-id="cd9e5-173">**다중 차원**  -  *차원* >= 3, 클릭 마다 현재 차원 수준 + 1이 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-173">**Multi-dimension** - *Dimensions* >= 3, every click increases the current dimension level + 1.</span></span> <span data-ttu-id="cd9e5-174">목록에 대 한 단추 상태 등을 정의 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-174">Useful for defining a button state to a list, etc.</span></span>

<span data-ttu-id="cd9e5-175">*Interactable* 를 사용 하면 *차원* 마다 여러 테마를 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-175">*Interactable* also allows for multiple Themes to be defined per *Dimension*.</span></span> <span data-ttu-id="cd9e5-176">예를 들어 *SelectionMode = Toggle* 인 경우 *Interactable* 가 선택 *취소* 되 면 하나의 테마가 적용 되 고 구성 요소가 *선택* 되 면 다른 테마가 적용 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-176">For example when *SelectionMode=Toggle*, one theme may be applied when the *Interactable* is *deselected* and another theme applied when the component is *selected*.</span></span>

<span data-ttu-id="cd9e5-177">를 통해 런타임에 현재 선택 모드를 쿼리할 수 있습니다 [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) .</span><span class="sxs-lookup"><span data-stu-id="cd9e5-177">The current Selection Mode can be queried at runtime via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode).</span></span> <span data-ttu-id="cd9e5-178">런타임에 모드를 업데이트 하는 것은  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) 원하는 기능과 일치 하도록 속성을 설정 하 여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-178">Updating the mode at runtime can be achieved by setting the  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) property to match the desired functionality.</span></span> <span data-ttu-id="cd9e5-179">또한 *설정/해제* 및 *다중 차원* 모드에 유용한 현재 차원은를 통해 액세스할 수 있습니다 [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) .</span><span class="sxs-lookup"><span data-stu-id="cd9e5-179">Furthermore, the current dimension, useful for *Toggle* and *Multi-Dimension* modes, can be accessed via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension).</span></span>

### <a name="interactable-profiles"></a><span data-ttu-id="cd9e5-180">Interactable 프로필</span><span class="sxs-lookup"><span data-stu-id="cd9e5-180">Interactable profiles</span></span>

<span data-ttu-id="cd9e5-181">*프로필* 은 GameObject [시각적 테마](visual-themes.md)간의 관계를 만드는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-181">*Profiles* are items that create a relationship between a GameObject and a [Visual Theme](visual-themes.md).</span></span> <span data-ttu-id="cd9e5-182">프로필은 [상태 변경이 발생할](#general-input-settings)때 테마에 의해 조작 되는 콘텐츠를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-182">The profile defines what content will be manipulated by a theme when a [state change occurs](#general-input-settings).</span></span>

<span data-ttu-id="cd9e5-183">테마는 자료와 유사 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-183">Themes work a lot like materials.</span></span> <span data-ttu-id="cd9e5-184">현재 상태에 따라 개체에 할당 되는 속성 목록을 포함 하는 스크립트 가능한 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-184">They are scriptable objects that contain a list of properties that will be assigned to an object based on the current state.</span></span> <span data-ttu-id="cd9e5-185">테마도 다시 사용할 수 있으며 여러 *Interactable* UX 개체에서 할당 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-185">Themes are also re-usable and can be assigned across multiple *Interactable* UX objects.</span></span>

<span data-ttu-id="cd9e5-186">**제거 시 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="cd9e5-186">**Reset On Destroy**</span></span>

<span data-ttu-id="cd9e5-187">시각적 테마는 선택한 테마 엔진의 클래스 및 형식에 따라 대상 GameObject의 다양 한 속성을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-187">Visual themes modify various properties on a targeted GameObject, dependent on the class and type of theme engine selected.</span></span> <span data-ttu-id="cd9e5-188">Interactable 구성 요소가 제거 될 때 *Reset에서 Reset* 이 true 이면 구성 요소가 모든 수정 된 속성을 활성 테마에서 원래 값으로 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-188">If *Reset On Destroy* is true when the Interactable component is destroyed, the component will reset all modified properties from active themes to their original values.</span></span> <span data-ttu-id="cd9e5-189">그렇지 않으면 제거 될 때 Interactable 구성 요소가 수정 된 속성을 그대로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-189">Otherwise, when destroyed, the Interactable component will leave any modified properties as-is.</span></span> <span data-ttu-id="cd9e5-190">이 두 번째 경우에는 다른 외부 구성 요소에 의해 변경 되지 않는 한 값의 마지막 상태가 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-190">In this latter case, the last state of values will persist unless altered by another external component.</span></span> <span data-ttu-id="cd9e5-191">기본값은 false입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-191">The default is false.</span></span>

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a><span data-ttu-id="cd9e5-192">이벤트</span><span class="sxs-lookup"><span data-stu-id="cd9e5-192">Events</span></span>

<span data-ttu-id="cd9e5-193">모든 *Interactable* 구성 요소에는 구성 요소를 간단히 선택할 때 발생 하는 *OnClick* 이벤트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-193">Every *Interactable* component has an *OnClick* event that fires when the component is simply selected.</span></span> <span data-ttu-id="cd9e5-194">그러나 *Interactable* 는 단순히 *OnClick* 이 아닌 입력 이벤트를 검색 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-194">However, *Interactable* can be used to detect input events other than just *OnClick*.</span></span>

<span data-ttu-id="cd9e5-195">이벤트 *추가* 단추를 클릭 하 여 새 유형의 이벤트 수신기 정의를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-195">Click the *Add Event* button to add a new type of Event Receiver definition.</span></span> <span data-ttu-id="cd9e5-196">추가 되 면 원하는 이벤트 유형을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-196">Once added, select the type of Event desired.</span></span>

![이벤트 예제](../images/interactable/Events.png)<span data-ttu-id="cd9e5-198">)</span><span class="sxs-lookup"><span data-stu-id="cd9e5-198">)</span></span>

<span data-ttu-id="cd9e5-199">여러 유형의 입력에 응답 하는 다양 한 유형의 이벤트 수신기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-199">There are different types of event receivers to respond to different types of input.</span></span> <span data-ttu-id="cd9e5-200">MRTK는 기본 제공 되는 다음 수신기 집합과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-200">MRTK ships with the following set of receivers out-of-box.</span></span>

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

<span data-ttu-id="cd9e5-201">를 확장 하는 새 클래스를 만들어 사용자 지정 수신기를 만들 수 있습니다 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) .</span><span class="sxs-lookup"><span data-stu-id="cd9e5-201">A custom receiver can be created by making a new class that extends [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase).</span></span>

![이벤트 설정/해제 예](../images/interactable/Event_toggle.png)

<span data-ttu-id="cd9e5-203">*설정/해제 이벤트 수신기의 예*</span><span class="sxs-lookup"><span data-stu-id="cd9e5-203">*Example of a Toggle Event Receiver*</span></span>

### <a name="interactable-receivers"></a><span data-ttu-id="cd9e5-204">Interactable 수신기</span><span class="sxs-lookup"><span data-stu-id="cd9e5-204">Interactable receivers</span></span>

 <span data-ttu-id="cd9e5-205">[`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver)구성 요소는 원본 *Interactable* 구성 요소 외부에서 이벤트를 정의할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-205">The [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) component allows for events to be defined outside of the source *Interactable* component.</span></span> <span data-ttu-id="cd9e5-206">*InteractableReceiver* 는 다른 *Interactable* 에서 발생 한 필터링 된 이벤트 유형을 수신 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-206">The *InteractableReceiver* will listen for a filtered event type fired by another *Interactable*.</span></span> <span data-ttu-id="cd9e5-207">*Interactable* 속성이 직접 할당 되지 않은 경우 *검색 범위* 속성은 *InteractableReceiver* 가 자체, 부모 또는 자식 GameObject 이벤트를 수신 대기 하는 방향을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-207">If the *Interactable* property is not directly assigned, then the *Search Scope* property defines the direction the *InteractableReceiver* listens for events which is either on itself, in a parent, or in a child GameObject.</span></span>

<span data-ttu-id="cd9e5-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) 비슷한 방식으로 작동 하지만 일치 하는 이벤트 목록에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) acts in a similar fashion but for a list of matching events.</span></span>

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a><span data-ttu-id="cd9e5-209">사용자 지정 이벤트 만들기</span><span class="sxs-lookup"><span data-stu-id="cd9e5-209">Create custom events</span></span>

<span data-ttu-id="cd9e5-210">[시각적 테마](visual-themes.md#custom-theme-engines)와 마찬가지로 이벤트를 확장 하 여 상태 패턴을 검색 하거나 기능을 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-210">Like [Visual Themes](visual-themes.md#custom-theme-engines), events can be extended to detect any state pattern or to expose functionality.</span></span>

<span data-ttu-id="cd9e5-211">사용자 지정 이벤트는 다음과 같은 두 가지 주요 방법으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-211">Custom events can be created in two main ways:</span></span>

1) <span data-ttu-id="cd9e5-212">클래스를 확장 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 하 여 이벤트 유형 드롭다운 목록에 표시 되는 사용자 지정 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-212">Extend the [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) class to create a custom event that will show up in the dropdown list of event types.</span></span> <span data-ttu-id="cd9e5-213">Unity 이벤트는 기본적으로 제공 되지만 추가 Unity 이벤트를 추가 하거나 Unity 이벤트를 숨기도록 이벤트를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-213">A Unity event is provided by default, but additional Unity events can be added or the event can be set to hide Unity events.</span></span> <span data-ttu-id="cd9e5-214">이 기능을 사용 하면 디자이너가 프로젝트의 엔지니어와 함께 작업 하 여 디자이너가 편집기에서 설정할 수 있는 사용자 지정 이벤트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-214">This functionality allows a designer to work with an engineer on a project to create a custom event that the designer can setup in the editor.</span></span>

1) <span data-ttu-id="cd9e5-215">클래스를 확장 [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) 하 여 *Interactable* 또는 다른 개체에 상주할 수 있는 완전히 사용자 지정 이벤트 구성 요소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-215">Extend the [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) class to create a completely custom event component that can reside on the *Interactable* or another object.</span></span> <span data-ttu-id="cd9e5-216">에서는 [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) *Interactable* 를 참조 하 여 상태 변경을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-216">The [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) will reference the *Interactable* to detect state changes.</span></span>

#### <a name="example-of-extending-receiverbase"></a><span data-ttu-id="cd9e5-217">확장 예제 `ReceiverBase`</span><span class="sxs-lookup"><span data-stu-id="cd9e5-217">Example of extending `ReceiverBase`</span></span>

<span data-ttu-id="cd9e5-218">[`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI)클래스는 *Interactable* 에 대 한 상태 정보를 표시 하 고 사용자 지정 이벤트 수신기를 만드는 방법의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-218">The [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) class displays status information about an *Interactable* and is an example of how to create a custom Event Receiver.</span></span>

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

<span data-ttu-id="cd9e5-219">다음 메서드는 사용자 지정 이벤트 수신기를 만들 때 재정의/구현 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-219">The following methods are useful to override/implement when creating a custom Event Receiver.</span></span> <span data-ttu-id="cd9e5-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 는 상태 패턴/전환을 검색 하는 데 사용할 수 있는 추상 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) is an abstract method that can be used to detect state patterns/transitions.</span></span> <span data-ttu-id="cd9e5-221">또한 [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 및 메서드는 [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) *Interactable* 가 선택 된 경우 사용자 지정 이벤트 논리를 만드는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-221">Furthermore, the [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) and [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) methods are useful for creating custom event logic when the *Interactable* is selected.</span></span>

```c#
public override void OnUpdate(InteractableStates state, Interactable source)
{
    if (state.CurrentState() != lastState)
    {
        // the state has changed, do something new
        lastState = state.CurrentState();
        ...
    }
}

public virtual void OnVoiceCommand(InteractableStates state, Interactable source,
                                    string command, int index = 0, int length = 1)
{
    base.OnVoiceCommand(state, source, command, index, length);
    // voice command called, perform some action
}  

public virtual void OnClick(InteractableStates state,
                            Interactable source,
                            IMixedRealityPointer pointer = null)
{
    base.OnClick(state, source);
    // click called, perform some action
}
```

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a><span data-ttu-id="cd9e5-222">검사기에 사용자 지정 이벤트 수신기 필드 표시</span><span class="sxs-lookup"><span data-stu-id="cd9e5-222">Displaying custom event receiver fields in the inspector</span></span>

<span data-ttu-id="cd9e5-223">*ReceiverBase* 스크립트 [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) 는 특성을 사용 하 여 검사기에서 사용자 지정 속성을 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-223">*ReceiverBase* scripts use [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) attributes to expose custom properties in the inspector.</span></span> <span data-ttu-id="cd9e5-224">다음은 도구 설명 및 레이블 정보가 있는 사용자 지정 속성인 Vector3의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-224">Here's an example of Vector3, a custom property with tooltip and label information.</span></span> <span data-ttu-id="cd9e5-225">*Interactable* GameObject를 선택 하 고 연결 된 *이벤트 수신기* 유형을 추가한 경우이 속성은 검사기에서 구성할 수 있는 것으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-225">This property will show up as configurable in the inspector when an *Interactable* GameObject is selected and has the associated *Event Receiver* type added.</span></span>

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a><span data-ttu-id="cd9e5-226">Interactable 사용 방법</span><span class="sxs-lookup"><span data-stu-id="cd9e5-226">How to use Interactable</span></span>

### <a name="building-a-simple-button"></a><span data-ttu-id="cd9e5-227">간단한 단추 작성</span><span class="sxs-lookup"><span data-stu-id="cd9e5-227">Building a simple button</span></span>

<span data-ttu-id="cd9e5-228">입력 이벤트를 수신 하도록 구성 된 GameObject에 *Interactable* 구성 요소를 추가 하 여 간단한 단추를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-228">One can create a simple button by adding the *Interactable* component to a GameObject that is configured to receive input events.</span></span> <span data-ttu-id="cd9e5-229">이 클래스에는 collider가 있거나 입력을 받기 위해 자식에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-229">It can have a collider on it or on a child to receive input.</span></span> <span data-ttu-id="cd9e5-230">Unity UI 기반 Gameobject에서 *Interactable* 를 사용 하는 경우 캔버스 GameObject 아래에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-230">If using *Interactable* with a Unity UI based GameObjects, it should be under the Canvas GameObject.</span></span>

<span data-ttu-id="cd9e5-231">새 프로필을 만들고 GameObject 자체를 할당 하 고 새 테마를 만들어 단추를 한 단계 더 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-231">Take the button one step further, by creating a new profile, assigning the GameObject itself and creating a new theme.</span></span> <span data-ttu-id="cd9e5-232">또한 *OnClick* 이벤트를 사용 하 여 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-232">Furthermore, use the *OnClick* event to make something happen.</span></span>

> [!NOTE]
> <span data-ttu-id="cd9e5-233">[단추 pressable](button.md) 를 설정 하려면 [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 구성 요소가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-233">Making a [button pressable](button.md) requires the [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) component.</span></span> <span data-ttu-id="cd9e5-234">또한 [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) *Interactable* 구성 요소에 이벤트를 누르기 위해 구성 요소가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-234">Additionally, the [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) component is needed to funnel press events to the *Interactable* component.</span></span>

### <a name="creating-toggle-and-multi-dimension-buttons"></a><span data-ttu-id="cd9e5-235">설정/해제 및 다중 차원 단추 만들기</span><span class="sxs-lookup"><span data-stu-id="cd9e5-235">Creating toggle and multi-dimension buttons</span></span>

#### <a name="toggle-button"></a><span data-ttu-id="cd9e5-236">토글 단추</span><span class="sxs-lookup"><span data-stu-id="cd9e5-236">Toggle button</span></span>

<span data-ttu-id="cd9e5-237">단추를 사용 하지 않도록 설정 하려면 [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) 필드를 형식으로 변경 `Toggle` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-237">To make a button Toggle-able, change the [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) field to type `Toggle`.</span></span> <span data-ttu-id="cd9e5-238">*프로필* 섹션에는 *Interactable* 가 설정 되어 있을 때 사용 되는 각 프로필에 대 한 새 전환 된 테마가 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-238">In the *Profiles* section, a new toggled theme is added for each profile that is used when the *Interactable* is toggled on.</span></span>

<span data-ttu-id="cd9e5-239">[`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes)가 Toggle로 설정 된 동안에는 *IsToggled* 확인란을 사용 하 여 런타임 초기화 시 컨트롤의 기본값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-239">While the [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) is set to Toggle, the *IsToggled* check box can be used to set the default value of the control at runtime initialization.</span></span>

<span data-ttu-id="cd9e5-240">*Canselect* 를 사용 하면 *Interactable* 가 *off* 로 *설정* 된 상태로 전환 되 고 *canselect* 는 역함수를 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-240">*CanSelect* means the *Interactable* can go from *off* to *on* while the *CanDeselect* means the inverse.</span></span>

![프로필 설정/해제 시각적 테마 예제](../images/interactable/Profile_toggle.png)

<span data-ttu-id="cd9e5-242">개발자는 [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 및 인터페이스를 활용 [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 하 여 코드를 통해 *Interactable* 의 설정/해제 상태를 가져오거나 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-242">Developers can utilize the [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) and [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces to get/set the toggle state of an *Interactable* via code.</span></span>

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a><span data-ttu-id="cd9e5-243">단추 컬렉션 설정/해제</span><span class="sxs-lookup"><span data-stu-id="cd9e5-243">Toggle button collection</span></span>

<span data-ttu-id="cd9e5-244">일반적으로는 지정 된 시간 (방사형 집합 또는 라디오 단추)이 라고도 하는 토글 단추 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-244">It is common to have a list of toggle buttons where only one can be active at any given time, also known as a radial set or radio buttons etc.</span></span>

<span data-ttu-id="cd9e5-245">[`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection)구성 요소를 사용 하 여이 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-245">Use the [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) component to enable this functionality.</span></span> <span data-ttu-id="cd9e5-246">이 컨트롤은 지정 된 시간에 하나의 *Interactable* 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-246">This control ensures only one *Interactable* is toggled on at any given time.</span></span> <span data-ttu-id="cd9e5-247">*RadialSet* (asset/MRTK/SDK/FEATURES/UX/Interactable/Prefabs/RadialSet)도 기본 제공 되는 좋은 출발점입니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-247">The *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) is also a great starting point out-of-box.</span></span>

<span data-ttu-id="cd9e5-248">사용자 지정 방사형 단추 그룹을 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-248">To create a custom radial button group:</span></span>

1) <span data-ttu-id="cd9e5-249">여러 *Interactable* gameobject/단추 만들기</span><span class="sxs-lookup"><span data-stu-id="cd9e5-249">Create multiple *Interactable* GameObjects/buttons</span></span>
1) <span data-ttu-id="cd9e5-250">각 *Interactable* 를 *SelectionMode* = Toggle, Canselect = true 및 *canselect* = false로 설정 합니다. </span><span class="sxs-lookup"><span data-stu-id="cd9e5-250">Set each *Interactable* with *SelectionMode* = Toggle, *CanSelect* = true, and *CanDeselect* = false</span></span>
1) <span data-ttu-id="cd9e5-251">모든 상호 작용을 통해 빈 부모 GameObject *을 만들고* *InteractableToggleCollection* 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-251">Create an empty parent GameObject over all the *Interactables* and add the *InteractableToggleCollection* component</span></span>
1) <span data-ttu-id="cd9e5-252">*InteractableToggleCollection* 의 *ToggleList* 에 모든 상호 작용을 *추가 합니다.*</span><span class="sxs-lookup"><span data-stu-id="cd9e5-252">Add all *Interactables* to the *ToggleList* on the *InteractableToggleCollection*</span></span>
1) <span data-ttu-id="cd9e5-253">*InteractableToggleCollection CurrentIndex* 속성을 설정 하 여 시작 시 기본적으로 선택 되는 단추를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-253">Set the *InteractableToggleCollection.CurrentIndex* property to determine which button is selected by default at start</span></span>

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a><span data-ttu-id="cd9e5-254">다차원 단추</span><span class="sxs-lookup"><span data-stu-id="cd9e5-254">Multi-dimensional button</span></span>

<span data-ttu-id="cd9e5-255">다중 차원 선택 모드는 연속 단추를 만드는 데 사용 되거나 3 개 이상의 단계를 포함 하는 단추를 사용 하 여 속도를 제어 합니다. 예를 들어 고속 (1x), 고속 (2x) 또는 가장 빠름 (3:3)</span><span class="sxs-lookup"><span data-stu-id="cd9e5-255">Multi-Dimension selection mode is used to create sequential buttons, or a button that has more than two steps, like controlling speed with three values, Fast (1x), Faster (2x) or Fastest (3x).</span></span>

<span data-ttu-id="cd9e5-256">차원을 숫자 값으로 사용 하는 경우 각 단계에 다른 테마를 사용 하 여 각 속도 설정에 대 한 단추의 텍스트 레이블 또는 질감을 제어 하기 위해 최대 9 개의 테마를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-256">With dimensions being a numeric value, up to 9 themes can be added to control the text label or texture of the button for each speed setting, using a different theme for each of step.</span></span>

<span data-ttu-id="cd9e5-257">모든 click 이벤트는 값에 `DimensionIndex` 도달할 때까지 런타임에 1로 이동 합니다 `Dimensions` .</span><span class="sxs-lookup"><span data-stu-id="cd9e5-257">Every click event will advance the `DimensionIndex` by 1 at runtime until the `Dimensions` value is reached.</span></span> <span data-ttu-id="cd9e5-258">그러면 주기가 0으로 다시 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-258">Then the cycle will reset to 0.</span></span>

![다차원 프로필 예](../images/interactable/Profile_multiDimensions.png)

<span data-ttu-id="cd9e5-260">개발자는를 평가 [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 하 여 현재 활성 상태인 차원을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-260">Developers can assess the [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) to determine which dimension is currently active.</span></span>

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a><span data-ttu-id="cd9e5-261">런타임에 Interactable 만들기</span><span class="sxs-lookup"><span data-stu-id="cd9e5-261">Create Interactable at runtime</span></span>

<span data-ttu-id="cd9e5-262">*Interactable* 은 런타임에 모든 GameObject에 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-262">*Interactable* can be easily added to any GameObject at runtime.</span></span> <span data-ttu-id="cd9e5-263">다음 예제에서는 [시각적 테마](visual-themes.md)를 사용 하 여 프로필을 할당 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-263">The following example demonstrates how to assign a profile with a [visual theme](visual-themes.md).</span></span>

```c#
var interactableObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
var interactable = interactableObject.AddComponent<Interactable>();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

interactable.Profiles = new List<InteractableProfileItem>()
{
    new InteractableProfileItem()
    {
        Themes = new List<Theme>()
        {
            Interactable.GetDefaultThemeAsset(new List<ThemeDefinition>() { newThemeType })
        },
        Target = interactableObject,
    },
};

// Force the Interactable to be clicked
interactable.TriggerOnClick()
```

### <a name="interactable-events-via-code"></a><span data-ttu-id="cd9e5-264">코드를 통해 이벤트 Interactable</span><span class="sxs-lookup"><span data-stu-id="cd9e5-264">Interactable events via code</span></span>

<span data-ttu-id="cd9e5-265">다음 예제를 사용 하 여 코드를 통해 기본 이벤트에 작업을 추가할 수 있습니다 [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) .</span><span class="sxs-lookup"><span data-stu-id="cd9e5-265">One can add an action to the base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) event via code with the following example.</span></span>

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

<span data-ttu-id="cd9e5-266">함수를 사용 [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 하 여 런타임에 동적으로 이벤트 수신기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-266">Use the [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) function to add event receivers dynamically at runtime.</span></span>

<span data-ttu-id="cd9e5-267">아래 예제 코드는 포커스 enter/exit를 수신 하는 [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)를 추가 하는 방법을 보여 줍니다. 또한 이벤트 인스턴스가 발생할 때 수행할 작업 코드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-267">The example code below demonstrates how to add an [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for focus enter/exit, and furthermore define action code to perform when the event instances fire.</span></span>

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

<span data-ttu-id="cd9e5-268">아래 예제 코드에서는 [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)를 추가 하는 방법을 보여 줍니다 .이는 토글 가능 상호 중단에 대 한 선택/선택 취소 상태 전환을 *수신 하 고*, 또한 이벤트 인스턴스가 발생할 때 수행할 작업 코드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd9e5-268">The example code below demonstrates how to add an [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for selected/deselected state transitions on toggle-able *Interactables*, and furthermore defines action code to perform when the event instances fire.</span></span>

```c#
public static void AddToggleEvents(Interactable interactable)
{
    var toggleReceiver = interactable.AddReceiver<InteractableOnToggleReceiver>();

    // Make the interactable have toggle capability, from code.
    // In the gui editor it's much easier
    interactable.Dimensions = 2;
    interactable.CanSelect = true;
    interactable.CanDeselect  = true;

    toggleReceiver.OnSelect.AddListener(() => Debug.Log("Toggle selected"));
    toggleReceiver.OnDeselect.AddListener(() => Debug.Log("Toggle un-selected"));
}
```

## <a name="see-also"></a><span data-ttu-id="cd9e5-269">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd9e5-269">See also</span></span>

* [<span data-ttu-id="cd9e5-270">시각적 개체 테마</span><span class="sxs-lookup"><span data-stu-id="cd9e5-270">Visual Themes</span></span>](visual-themes.md)
* [<span data-ttu-id="cd9e5-271">입력 작업</span><span class="sxs-lookup"><span data-stu-id="cd9e5-271">Input Actions</span></span>](../input/input-actions.md)
* [<span data-ttu-id="cd9e5-272">음성 명령</span><span class="sxs-lookup"><span data-stu-id="cd9e5-272">Speech Commands</span></span>](../input/speech.md)
* [<span data-ttu-id="cd9e5-273">단추</span><span class="sxs-lookup"><span data-stu-id="cd9e5-273">Buttons</span></span>](button.md)
* [<span data-ttu-id="cd9e5-274">MRTK 표준 세이더</span><span class="sxs-lookup"><span data-stu-id="cd9e5-274">MRTK Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)
