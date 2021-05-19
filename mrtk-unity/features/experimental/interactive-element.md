---
title: 대화형 요소
description: InteractiveElement MRTK 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 대화형 요소, Interactable
ms.openlocfilehash: 65f518c53414d68d3a9d2093cb427140cc65560b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144760"
---
# <a name="interactive-element-experimental"></a><span data-ttu-id="aafda-104">Interactive 요소 [실험적]</span><span class="sxs-lookup"><span data-stu-id="aafda-104">Interactive Element [Experimental]</span></span>

<span data-ttu-id="aafda-105">MRTK 입력 시스템에 대 한 단순화 된 중앙 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-105">A simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="aafda-106">상태 관리 방법, 이벤트 관리 및 핵심 상호 작용 상태의 상태 설정 논리가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-106">Contains state management methods, event management and the state setting logic for Core Interaction States.</span></span>

<span data-ttu-id="aafda-107">Interactive 요소는 unity 2019.3: [Serialize 참조](https://docs.unity3d.com/ScriptReference/SerializeReference.html)의 새로운 기능을 활용 하므로 unity 2019.3에서 지원 되는 실험적 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-107">Interactive Element is an experimental feature supported in Unity 2019.3 and up as it utilizes a capability new to Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span></span>

### <a name="interactive-element-inspector"></a><span data-ttu-id="aafda-108">대화형 요소 검사기</span><span class="sxs-lookup"><span data-stu-id="aafda-108">Interactive Element Inspector</span></span>

<span data-ttu-id="aafda-109">재생 모드에서 대화형 요소 검사기는 현재 상태가 활성 상태 인지 여부를 나타내는 시각적 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-109">During play mode, the Interactive Element inspector provides visual feedback that indicates whether or not the current state is active.</span></span> <span data-ttu-id="aafda-110">활성 상태 이면 사이안 색으로 강조 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-110">If a state is active, it will be highlighted with a cyan color.</span></span>  <span data-ttu-id="aafda-111">상태가 활성이 아니면 색은 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-111">If the state is not active, the color is not changed.</span></span> <span data-ttu-id="aafda-112">검사기의 상태 옆에 있는 숫자는 상태 값입니다. 상태가 활성 이면 값은 1이 고, 상태가 활성이 아니면 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-112">The numbers next to the states in the inspector are the state values, if the state is active then the value is 1, if the state is not active the value is 0.</span></span>

![가상 손을 상호 작용 하는 대화형 요소](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a><span data-ttu-id="aafda-114">코어 상태</span><span class="sxs-lookup"><span data-stu-id="aafda-114">Core States</span></span>

<span data-ttu-id="aafda-115">Interactive 요소는 핵심 상태를 포함 하 고 [사용자 지정 상태](#custom-states)를 추가할 수 있도록 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-115">Interactive Element contains core states and supports the addition of [custom states](#custom-states).</span></span>  <span data-ttu-id="aafda-116">핵심 상태는에 정의 된 상태 설정 논리가 이미 있는 상태입니다 `BaseInteractiveElement` .</span><span class="sxs-lookup"><span data-stu-id="aafda-116">A core state is one that already has the state setting logic defined in `BaseInteractiveElement`.</span></span> <span data-ttu-id="aafda-117">다음은 현재 입력 기반 코어 상태의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-117">The following is a list of the current input-driven core states:</span></span> 

### <a name="current-core-states"></a><span data-ttu-id="aafda-118">현재 코어 상태</span><span class="sxs-lookup"><span data-stu-id="aafda-118">Current Core States</span></span>

- [<span data-ttu-id="aafda-119">기본</span><span class="sxs-lookup"><span data-stu-id="aafda-119">Default</span></span>](#default-state) 

<span data-ttu-id="aafda-120">근거리 및 원거리 상호 작용 핵심 상태:</span><span class="sxs-lookup"><span data-stu-id="aafda-120">Near and Far Interaction Core States:</span></span>
- [<span data-ttu-id="aafda-121">포커스</span><span class="sxs-lookup"><span data-stu-id="aafda-121">Focus</span></span>](#focus-state) 

<span data-ttu-id="aafda-122">거의 상호 작용 코어 상태:</span><span class="sxs-lookup"><span data-stu-id="aafda-122">Near Interaction Core States:</span></span>

- [<span data-ttu-id="aafda-123">가까이에 집중</span><span class="sxs-lookup"><span data-stu-id="aafda-123">Focus Near</span></span>](#focus-near-state)
- [<span data-ttu-id="aafda-124">터치</span><span class="sxs-lookup"><span data-stu-id="aafda-124">Touch</span></span>](#touch-state)

<span data-ttu-id="aafda-125">Far 상호 작용 코어 상태:</span><span class="sxs-lookup"><span data-stu-id="aafda-125">Far Interaction Core States:</span></span>
- [<span data-ttu-id="aafda-126">지금 포커스</span><span class="sxs-lookup"><span data-stu-id="aafda-126">Focus Far</span></span>](#focus-far-state)
- [<span data-ttu-id="aafda-127">지금 선택</span><span class="sxs-lookup"><span data-stu-id="aafda-127">Select Far</span></span>](#select-far-state)

<span data-ttu-id="aafda-128">기타 핵심 상태:</span><span class="sxs-lookup"><span data-stu-id="aafda-128">Other Core States:</span></span>
- [<span data-ttu-id="aafda-129">클릭됨</span><span class="sxs-lookup"><span data-stu-id="aafda-129">Clicked</span></span>](#clicked-state)
- [<span data-ttu-id="aafda-130">설정 및 해제</span><span class="sxs-lookup"><span data-stu-id="aafda-130">Toggle On and Toggle Off</span></span>](#toggle-on-and-toggle-off-state)
- [<span data-ttu-id="aafda-131">Speech 키워드</span><span class="sxs-lookup"><span data-stu-id="aafda-131">Speech Keyword</span></span>](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a><span data-ttu-id="aafda-132">Inspector를 통해 핵심 상태를 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="aafda-132">How to Add a Core State via Inspector</span></span>

1. <span data-ttu-id="aafda-133">대화형 요소에 대 한 검사기에서 **코어 상태 추가** 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-133">Navigate to **Add Core State** in the inspector for Interactive Element.</span></span>

    ![검사기를 통해 핵심 상태 추가](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. <span data-ttu-id="aafda-135">**상태 선택** 단추를 선택 하 여 추가할 핵심 상태를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-135">Select the **Select State** button to choose the core state to add.</span></span> <span data-ttu-id="aafda-136">메뉴의 상태는 상호 작용 유형별로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-136">The states in the menu are sorted by interaction type.</span></span>

    ![상태가 선택 된 검사기를 통해 코어 상태 추가](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. <span data-ttu-id="aafda-138">이벤트 구성 foldout을 열고 상태와 연결 된 이벤트와 속성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-138">Open the Event Configuration foldout to view the events and properties associated with the state.</span></span>

    ![이벤트 구성을 사용 하 여 검사기를 통해 핵심 상태 추가](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a><span data-ttu-id="aafda-140">스크립트를 통해 핵심 상태를 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="aafda-140">How to Add a Core State via Script</span></span>

<span data-ttu-id="aafda-141">메서드를 사용 `AddNewState(stateName)` 하 여 코어 상태를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-141">Use the `AddNewState(stateName)` method to add a core state.</span></span> <span data-ttu-id="aafda-142">사용 가능한 핵심 상태 이름 목록은 열거형을 사용 합니다 `CoreInteractionState` .</span><span class="sxs-lookup"><span data-stu-id="aafda-142">For a list of the available core state names, use the `CoreInteractionState` enum.</span></span>

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a><span data-ttu-id="aafda-143">상태 내부 구조</span><span class="sxs-lookup"><span data-stu-id="aafda-143">States Internal Structure</span></span> 

<span data-ttu-id="aafda-144">대화형 요소의 상태는 형식입니다 `InteractionState` .</span><span class="sxs-lookup"><span data-stu-id="aafda-144">The states in Interactive Element are of type `InteractionState`.</span></span>  <span data-ttu-id="aafda-145">에는 `InteractionState` 다음 속성이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-145">An `InteractionState` contains the following properties:</span></span>

- <span data-ttu-id="aafda-146">**이름:** 상태의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-146">**Name**: The name of the state.</span></span>
- <span data-ttu-id="aafda-147">**값:** 상태 값입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-147">**Value**: The state value.</span></span>  <span data-ttu-id="aafda-148">상태가 켜진 경우 상태 값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-148">If the state is on, the state value is 1.</span></span> <span data-ttu-id="aafda-149">상태가 꺼져 있으면 상태 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-149">If the state is off, the state value is 0.</span></span>
- <span data-ttu-id="aafda-150">**활성:** 상태가 현재 활성 상태인지 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-150">**Active**: Whether or not the state is currently active.</span></span> <span data-ttu-id="aafda-151">활성 속성의 값은 상태가 켜지면 true이고, 상태가 해제되어 있으면 false입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-151">The value for the Active property is true when the state is on, false if the state is off.</span></span> 
- <span data-ttu-id="aafda-152">**상호 작용 유형:** 상태의 상호 작용 형식은 상태가 의도된 상호 작용의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-152">**Interaction Type**: The Interaction Type of a state is the type of interaction a state is intended for.</span></span> 
  - <span data-ttu-id="aafda-153">`None`: 어떤 형식의 입력 상호 작용도 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-153">`None`: Does not support any form of input interaction.</span></span>
  - <span data-ttu-id="aafda-154">`Near`: 근접 상호 작용 지원.</span><span class="sxs-lookup"><span data-stu-id="aafda-154">`Near`: Near interaction support.</span></span> <span data-ttu-id="aafda-155">입력은 굴절된 손에서 다른 게임 개체와 직접 연결되는 경우( 즉, 굴절된 손의 위치가 세계 공간에서 게임 개체의 위치와 가까운 경우) 근거리 상호 작용으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-155">Input is considered near interaction when an articulated hand has direct contact with another game object, i.e. the position the articulated hand is close to the position of the game object in world space.</span></span>
  - <span data-ttu-id="aafda-156">`Far`: 원거리 상호 작용 지원.</span><span class="sxs-lookup"><span data-stu-id="aafda-156">`Far`: Far interaction support.</span></span> <span data-ttu-id="aafda-157">입력은 게임 개체와의 직접 연락이 필요하지 않은 경우 원거리 상호 작용으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-157">Input is considered far interaction when direct contact with the game object is not required.</span></span> <span data-ttu-id="aafda-158">예를 들어 컨트롤러 광선 또는 응시를 통한 입력은 원거리 상호 작용 입력으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-158">For example, input via controller ray or gaze is considered far interaction input.</span></span>
  - <span data-ttu-id="aafda-159">`NearAndFar`: 가까운 상호 작용 및 원거리 상호 작용 지원을 모두 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-159">`NearAndFar`: Encompasses both near and far interaction support.</span></span> 
  - <span data-ttu-id="aafda-160">`Other`: 포인터 독립적 상호 작용 지원.</span><span class="sxs-lookup"><span data-stu-id="aafda-160">`Other`: Pointer independent interaction support.</span></span>
- <span data-ttu-id="aafda-161">**이벤트 구성:** 상태에 대한 이벤트 구성은 직렬화된 이벤트 프로필 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-161">**Event Configuration**: The event configuration for a state is the serialized events profile entry point.</span></span> 

<span data-ttu-id="aafda-162">이러한 모든 속성은 Interactive 요소에 포함된 에서 내부적으로 `State Manager` 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-162">All of these properties are set internally in the `State Manager` contained in Interactive Element.</span></span> <span data-ttu-id="aafda-163">상태를 수정하려면 다음 도우미 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-163">For modification of states use the following helper methods:</span></span>

<span data-ttu-id="aafda-164">**상태 설정 도우미 메서드**</span><span class="sxs-lookup"><span data-stu-id="aafda-164">**State Setting Helper Methods**</span></span>

```c# 
// Get the InteractionState
interactiveElement.GetState("StateName");

// Set a state value to 1/on
interactiveElement.SetStateOn("StateName");

// Set a state value to 0/off
interactiveElement.SetStateOff("StateName");

// Check if a state is present in the state list
interactiveElement.IsStatePresent("StateName");

// Check whether or not a state is active
interactiveElement.IsStateActive("StateName");

// Add a new state to the state list
interactiveElement.AddNewState("StateName");

// Remove a state from the state list
interactiveElement.RemoveState("StateName");
```

<span data-ttu-id="aafda-165">상태의 이벤트 구성을 얻는 것은 상태 자체에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-165">Getting the event configuration of a state is specific to the state itself.</span></span> <span data-ttu-id="aafda-166">각 코어 상태에는 각 핵심 상태를 설명 하는 섹션 아래에 설명 된 특정 이벤트 구성 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-166">Each core state has a specific event configuration type which is outlined below under the sections describing each core state.</span></span>

<span data-ttu-id="aafda-167">다음은 상태 이벤트 구성을 가져오는 일반적인 예입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-167">Here is a generalized example of getting a state's event configuration:</span></span>

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a><span data-ttu-id="aafda-168">기본 상태</span><span class="sxs-lookup"><span data-stu-id="aafda-168">Default State</span></span>

<span data-ttu-id="aafda-169">기본 상태는 항상 대화형 요소에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-169">The Default state is always present on an Interactive Element.</span></span>  <span data-ttu-id="aafda-170">이 상태는 다른 모든 상태가 활성 상태가 아닌 경우에만 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-170">This state will be active only when all other states are not active.</span></span>  <span data-ttu-id="aafda-171">다른 상태가 활성 상태가 되 면 기본 상태는 내부적으로 off로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-171">If any other state becomes active, then the Default state will be set to off internally.</span></span> 

<span data-ttu-id="aafda-172">대화형 요소는 상태 목록에 있는 기본 및 포커스 상태를 사용 하 여 초기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-172">An Interactive Element is initialized with the Default and Focus states present in the state list.</span></span> <span data-ttu-id="aafda-173">기본 상태는 항상 상태 목록에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-173">The Default state always needs to be present in the state list.</span></span> 

#### <a name="getting-default-state-events"></a><span data-ttu-id="aafda-174">기본 상태 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="aafda-174">Getting Default State Events</span></span>

<span data-ttu-id="aafda-175">기본 상태에 대 한 이벤트 구성 유형입니다. `StateEvents`</span><span class="sxs-lookup"><span data-stu-id="aafda-175">Event configuration type for the Default State: `StateEvents`</span></span>

```c#
StateEvents defaultEvents = interactiveElement.GetStateEvents<StateEvents>("Default");

defaultEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State On");
});

defaultEvents.OnStateOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State Off");
});
```

### <a name="focus-state"></a><span data-ttu-id="aafda-176">포커스 상태</span><span class="sxs-lookup"><span data-stu-id="aafda-176">Focus State</span></span>

<span data-ttu-id="aafda-177">포커스 상태는 커서와 동등한 혼합 현실로 간주할 수 있는 근거리 및 원거리 상호 작용 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-177">The Focus state is a near and far interaction state that can be thought of as the mixed reality equivalent to hover.</span></span> <span data-ttu-id="aafda-178">포커스 상태에 대 한 근거리 및 원거리 상호 작용 사이의 구별 요소는 현재 활성 포인터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-178">The distinguishing factor between near and far interaction for the Focus state is the current active pointer type.</span></span>  <span data-ttu-id="aafda-179">포커스 상태에 대 한 포인터 형식이 Poke 포인터인 경우 상호 작용은 거의 상호 작용 하는 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-179">If the pointer type for the Focus state is the Poke Pointer, then the interaction is considered near interaction.</span></span>  <span data-ttu-id="aafda-180">기본 포인터가 Poke 포인터가 아닌 경우 상호 작용으로 인 한 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-180">If the primary pointer is not the Poke Pointer, then the interaction is considered far interaction.</span></span> <span data-ttu-id="aafda-181">포커스 상태는 기본적으로 대화형 요소에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-181">The Focus state is present in Interactive Element by default.</span></span>

<span data-ttu-id="aafda-182">**포커스 상태 동작** 
 ![ 가상 손 상호 작용을 사용 하는 포커스 상태](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="aafda-182">**Focus State Behavior**
![Focus state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span></span> 

<span data-ttu-id="aafda-183">**포커스 상태 검사기** 
 ![ Inpsector의 포커스 상태](../images/interactive-element/InEditor/FocusStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="aafda-183">**Focus State Inspector**
![Focus state in the Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span></span>

#### <a name="getting-focus-state-events&quot;></a><span data-ttu-id=&quot;aafda-184&quot;>포커스 상태 이벤트 가져오기</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-184&quot;>Getting Focus State Events</span></span>

<span data-ttu-id=&quot;aafda-185&quot;>포커스 상태의 이벤트 구성 유형입니다. `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-185&quot;>Event configuration type for the Focus State: `FocusEvents`</span></span>

```c#
FocusEvents focusEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;Focus");

focusEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus On");
});

focusEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus Off");
});
```

#### <a name="focus-near-vs-focus-far-behavior"></a><span data-ttu-id="aafda-186">가까이에 포커스를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-186">Focus Near vs Focus Far Behavior</span></span> 

![가상 손 상호 작용을 통해 가까운 정도의 포커스](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a><span data-ttu-id="aafda-188">포커스 근 상태</span><span class="sxs-lookup"><span data-stu-id="aafda-188">Focus Near State</span></span>

<span data-ttu-id="aafda-189">포커스 이벤트가 발생할 때 포커스 근사 상태가 설정되고 주 포인터가 Near 상호 작용을 나타내는 표시인 표시인 경우 Focus Near 상태가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-189">The Focus Near state is set when a focus event is raised and the primary pointer is the Poke pointer, an indication of near interaction.</span></span> 

<span data-ttu-id="aafda-190">**포커스 근 상태 동작** 
 ![ 가상 손 상호 작용을 통해 상태 가까이에 포커스](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="aafda-190">**Focus Near State Behavior**
![Focus near state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span></span> 

<span data-ttu-id="aafda-191">**상태 검사기** 
 ![ 근처 포커스 검사기에서 구성 요소 근처에 포커스](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="aafda-191">**Focus Near State Inspector**
![Focus near component in the Inspector](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span></span>

#### <a name="getting-focusnear-state-events&quot;></a><span data-ttu-id=&quot;aafda-192&quot;>FocusNear 상태 이벤트 받기</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-192&quot;>Getting FocusNear State Events</span></span>

<span data-ttu-id=&quot;aafda-193&quot;>FocusNear 상태에 대한 이벤트 구성 유형: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-193&quot;>Event configuration type for the FocusNear State: `FocusEvents`</span></span>

```c#
FocusEvents focusNearEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusNear");

focusNearEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus On");
});

focusNearEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus Off");
});
```

### <a name="focus-far-state"></a><span data-ttu-id="aafda-194">포커스 원거리 상태</span><span class="sxs-lookup"><span data-stu-id="aafda-194">Focus Far State</span></span>

<span data-ttu-id="aafda-195">포커스 원거리 상태는 기본 포인터가 Pointer 포인터가 아닌 경우 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-195">The Focus Far state is set when the primary pointer is not the Poke pointer.</span></span>  <span data-ttu-id="aafda-196">예를 들어 기본 컨트롤러 광선 포인터 및 GGV(응시, 제스처, 음성) 포인터는 원거리 상호 작용 포인터로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-196">For example, the default controller ray pointer and the GGV (Gaze, Gesture, Voice) pointer are considered far interaction pointers.</span></span>

<span data-ttu-id="aafda-197">**포커스 원거리 상태 동작** 
 ![ 가상 손 조작을 통해 멀리 떨어진 포커스 상태](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="aafda-197">**Focus Far State Behavior**
![Focus state far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span></span>

<span data-ttu-id="aafda-198">**포커스 원거리 상태 검사기** 
 ![ 검사기에서 멀리 떨어진 포커스 구성 요소](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="aafda-198">**Focus Far State Inspector**
![Focus far component in the Inspector](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span></span>

#### <a name="getting-focus-far-state-events&quot;></a><span data-ttu-id=&quot;aafda-199&quot;>포커스 원거리 상태 이벤트 얻기</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-199&quot;>Getting Focus Far State Events</span></span>

<span data-ttu-id=&quot;aafda-200&quot;>FocusFar 상태에 대한 이벤트 구성 유형: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-200&quot;>Event configuration type for the FocusFar State: `FocusEvents`</span></span>

```c#
FocusEvents focusFarEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusFar");

focusFarEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus On");
});

focusFarEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus Off");
});
```

### <a name="touch-state"></a><span data-ttu-id="aafda-201">터치 상태</span><span class="sxs-lookup"><span data-stu-id="aafda-201">Touch State</span></span>

<span data-ttu-id="aafda-202">터치 상태는 굴절된 손에서 개체를 직접 터치할 때 설정되는 거의 상호 작용 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-202">The Touch state is a near interaction state that is set when an articulated hand touches the object directly.</span></span>  <span data-ttu-id="aafda-203">직접 터치는 굴절된 손의 인덱스 손가락이 개체의 세계 위치에 매우 가까이 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-203">A direct touch means that the articulated hand's index finger is very close to the world position of the object.</span></span> <span data-ttu-id="aafda-204">기본적으로 Touch `NearInteractionTouchableVolume` 상태가 상태 목록에 추가되면 구성 요소가 개체에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-204">By default, a `NearInteractionTouchableVolume` component is attached to the object if the Touch state is added to the the state list.</span></span>  <span data-ttu-id="aafda-205">터치 이벤트를  `NearInteractionTouchableVolume` 검색하려면 또는 `NearInteractionTouchable` 구성 요소가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-205">The presence of a  `NearInteractionTouchableVolume` or `NearInteractionTouchable` component is required for detecting Touch events.</span></span>  <span data-ttu-id="aafda-206">와 의 차이점은 `NearInteractionTouchableVolume` `NearInteractionTouchable` 는 `NearInteractionTouchableVolume` 개체의 충돌체를 기반으로 터치를 `NearInteractionTouchable` 감지하고 평면의 정의된 영역 내에서 터치를 감지한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-206">The difference between `NearInteractionTouchableVolume` and `NearInteractionTouchable` is that `NearInteractionTouchableVolume` detects a touch based on the collider of the object and `NearInteractionTouchable`detects touch within a defined area of a plane.</span></span>

<span data-ttu-id="aafda-207">**터치 상태 동작** 
 ![ 가상 손 조작을 통해 터치 상태](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="aafda-207">**Touch State Behavior**
![Touch state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span></span>

<span data-ttu-id="aafda-208">**터치 상태 검사기** 
 ![ 검사기에서 터치 상태 구성 요소](../images/interactive-element/InEditor/TouchStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="aafda-208">**Touch State Inspector**
![Touch state component in the Inspector](../images/interactive-element/InEditor/TouchStateInspector.png)</span></span>

#### <a name="getting-touch-state-events&quot;></a><span data-ttu-id=&quot;aafda-209&quot;>터치 상태 이벤트 받기</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-209&quot;>Getting Touch State Events</span></span>

<span data-ttu-id=&quot;aafda-210&quot;>터치 상태에 대한 이벤트 구성 유형: `TouchEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-210&quot;>Event configuration type for the Touch State: `TouchEvents`</span></span>

```c#
TouchEvents touchEvents = interactiveElement.GetStateEvents<TouchEvents>(&quot;Touch");

touchEvents.OnTouchStarted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Started");
});

touchEvents.OnTouchCompleted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Completed");
});

touchEvents.OnTouchUpdated.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Updated");
});
```

### <a name="select-far-state"></a><span data-ttu-id="aafda-211">원거리 상태 선택</span><span class="sxs-lookup"><span data-stu-id="aafda-211">Select Far State</span></span>

<span data-ttu-id="aafda-212">원거리 선택 상태가 `IMixedRealityPointerHandler` 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-212">The Select Far state is the `IMixedRealityPointerHandler` surfaced.</span></span>  <span data-ttu-id="aafda-213">이 상태는 원거리 상호 작용 클릭(에어 탭)을 감지하고 기본 컨트롤러 광선 포인터 또는 GGV 포인터와 같은 원거리 상호 작용 포인터를 사용하는 원거리 상호 작용 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-213">This state is a far interaction state that detects far interaction click (air-tap) and holds through the use of far interaction pointers such as the default controller ray pointer or the GGV pointer.</span></span>  <span data-ttu-id="aafda-214">원거리 선택 상태에는 라는 이벤트 구성 폴딩 아래에 옵션이 `Global` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-214">The Select Far state has an option under the event configuration foldout named `Global`.</span></span> <span data-ttu-id="aafda-215">`Global`가 true이면 `IMixedRealityPointerHandler` 이 전역 입력 처리기로 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-215">If `Global` is true, then the `IMixedRealityPointerHandler` is registered as a global input handler.</span></span>  <span data-ttu-id="aafda-216">처리기가 전역으로 등록된 경우 입력 시스템 이벤트를 트리거하기 위해 개체에 집중할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-216">Focus on an object is not required to trigger input system events if a handler is registered as global.</span></span>  <span data-ttu-id="aafda-217">예를 들어 사용자가 포커스에 있는 개체에 관계없이 에어 탭/선택 제스처가 수행될 때마다 알고 싶은 경우 `Global` 를 true로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-217">For example, if a user wants to know anytime the air-tap/select gesture is performed regardless of the object in focus, set `Global` to true.</span></span> 

<span data-ttu-id="aafda-218">**원거리 상태 동작** 
 ![ 선택 가상 손 조작을 통해 멀리 선택](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="aafda-218">**Select Far State Behavior**
![Select far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span></span>

<span data-ttu-id="aafda-219">**원거리 상태 검사기** 
 ![ 선택 검사기에서 원거리 구성 요소 선택](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="aafda-219">**Select Far State Inspector**
![Select far component in the Inspector](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span></span>

#### <a name="getting-select-far-state-events&quot;></a><span data-ttu-id=&quot;aafda-220&quot;>원거리 상태 이벤트 선택</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-220&quot;>Getting Select Far State Events</span></span>

<span data-ttu-id=&quot;aafda-221&quot;>SelectFar 상태에 대한 이벤트 구성 유형: `SelectFarEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-221&quot;>Event configuration type for the SelectFar State: `SelectFarEvents`</span></span>

```c#
SelectFarEvents selectFarEvents = interactiveElement.GetStateEvents<SelectFarEvents>(&quot;SelectFar");

selectFarEvents.OnSelectUp.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Up");
});

selectFarEvents.OnSelectDown.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Down");
});

selectFarEvents.OnSelectHold.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Hold");
});

selectFarEvents.OnSelectClicked.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Clicked");
});
```

### <a name="clicked-state"></a><span data-ttu-id="aafda-222">클릭된 상태</span><span class="sxs-lookup"><span data-stu-id="aafda-222">Clicked State</span></span>

<span data-ttu-id="aafda-223">클릭 상태는 기본적으로 원거리 상호 작용 클릭(원거리 상태 선택)에 의해 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-223">The Clicked state is triggered by a far interaction click (Select Far state) by default.</span></span>  <span data-ttu-id="aafda-224">이 상태는 내부적으로 켜기로 전환되고 OnClicked 이벤트를 호출한 다음 즉시 꺼져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-224">This state is internally switched to on, invokes the OnClicked event and then is immediately switched to off.</span></span> 

> [!NOTE]
> <span data-ttu-id="aafda-225">상태 활동을 기반으로 하는 검사기에서 시각적 피드백이 켜진 후 즉시 꺼져 있으므로 Clicked 상태에 대한 시각적 피드백이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-225">The visual feedback in the inspector based on state activity is not present for the Clicked state because it is switched on and then off immediately.</span></span> 

<span data-ttu-id="aafda-226">**클릭된 상태 동작** 
 ![ 가상 손 상호 작용을 통해 클릭된 상태](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="aafda-226">**Clicked State Behavior**
![Clicked state with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span></span>

<span data-ttu-id="aafda-227">**상태 검사기 클릭** 
 ![ 검사기에서 state component를 클릭 합니다.](../images/interactive-element/InEditor/ClickedStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="aafda-227">**Clicked State Inspector**
![Click state component in the Inspector](../images/interactive-element/InEditor/ClickedStateInspector.png)</span></span>

<span data-ttu-id="aafda-228">**Near 및 Far 클릭 상태 예제**</span><span class="sxs-lookup"><span data-stu-id="aafda-228">**Near and Far Clicked State Example**</span></span>  
<span data-ttu-id="aafda-229">메서드를 사용 하 여 추가 진입점을 통해 클릭 된 상태를 트리거할 수 있습니다 `interactiveElement.TriggerClickedState()` .</span><span class="sxs-lookup"><span data-stu-id="aafda-229">The clicked state can be triggered through additional entry points using the `interactiveElement.TriggerClickedState()` method.</span></span>  <span data-ttu-id="aafda-230">예를 들어, 사용자가 개체에 대 한 클릭을 트리거하는 근접 한 상호 작용 터치를 원하는 경우 `TriggerClickedState()` 터치 상태의 수신기로 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-230">For example, if a user wants a near interaction touch to trigger a click on an object as well, then they would add the `TriggerClickedState()` method as a listener in the touch state.</span></span>   

![가상 핸드 상호 작용이 있는 Near 및 far 상태](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a><span data-ttu-id=&quot;aafda-232&quot;>클릭 상태 이벤트 가져오기</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-232&quot;>Getting Clicked State Events</span></span>

<span data-ttu-id=&quot;aafda-233&quot;>클릭 한 상태의 이벤트 구성 유형입니다. `ClickedEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-233&quot;>Event configuration type for the Clicked State: `ClickedEvents`</span></span>

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a><span data-ttu-id="aafda-234">설정/해제 상태 설정/해제</span><span class="sxs-lookup"><span data-stu-id="aafda-234">Toggle On and Toggle Off state</span></span>

<span data-ttu-id="aafda-235">토글 설정 및 설정/해제 상태는 쌍 이며 토글 동작에 대해 둘 다 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-235">The Toggle On and Toggle Off states are a pair and both need to be present for toggle behavior.</span></span>  <span data-ttu-id="aafda-236">기본적으로 토글 설정 및 설정/해제 상태는 먼 트 클릭 (Far 상태 선택)을 통해 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-236">By default, the Toggle On and Toggle Off states are triggered through a far interaction click (Select Far state).</span></span>  <span data-ttu-id="aafda-237">기본적으로 설정/해제 상태는 시작 시 활성 상태 이므로 설정/해제는 off로 초기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-237">By default, the Toggle Off state is active on start, meaning that the toggle will be initialized to off.</span></span>  <span data-ttu-id="aafda-238">사용자가 시작 시 활성화 상태를 설정 하려면 설정/해제 상태가 true로 설정 되어 있어야 합니다 `IsSelectedOnStart` .</span><span class="sxs-lookup"><span data-stu-id="aafda-238">If a user wants the Toggle On state to be active on start, then in the Toggle On state set `IsSelectedOnStart` to true.</span></span>

<span data-ttu-id="aafda-239">**상태 동작** 
 ![ ToggleOn 및 토글 가상 손 상호 작용을 사용 하 여 설정 및 해제](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="aafda-239">**ToggleOn and Toggle Off State Behavior**
![Toggle on and off with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span></span>

<span data-ttu-id="aafda-240">**상태 검사자** 
 ![ ToggleOn 및 토글 검사기에서 구성 요소 설정/해제](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="aafda-240">**ToggleOn and Toggle Off State Inspector**
![Toggle component in the Inspector](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span></span>

<span data-ttu-id="aafda-241">**Near 및 Far 전환 상태 예**</span><span class="sxs-lookup"><span data-stu-id="aafda-241">**Near and Far Toggle States Example**</span></span>  
<span data-ttu-id="aafda-242">클릭 상태와 마찬가지로 설정/해제 상태 설정에는 메서드를 사용 하 여 여러 진입점이 있을 수 있습니다 `interactiveElement.SetToggleStates()` .</span><span class="sxs-lookup"><span data-stu-id="aafda-242">Similar to the Clicked state, toggle state setting can have multiple entry points using the `interactiveElement.SetToggleStates()` method.</span></span> <span data-ttu-id="aafda-243">예를 들어, 사용자가 토글 상태를 설정 하기 위해 추가 진입점으로 터치 하려는 경우 `SetToggleStates()` 터치 상태의 이벤트 중 하나에 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-243">For example, if a user wants touch as an additional entry point to set the toggle states, then they add the `SetToggleStates()` method to one of the events in the Touch state.</span></span> 

![근거리 및 원거리 전환 (가상 핸드 상호 작용)](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a><span data-ttu-id=&quot;aafda-245&quot;>설정/해제 상태 이벤트 설정 및 해제</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-245&quot;>Getting Toggle On and Toggle Off State Events</span></span>

<span data-ttu-id=&quot;aafda-246&quot;>ToggleOn 상태에 대 한 이벤트 구성 유형입니다. `ToggleOnEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-246&quot;>Event configuration type for the ToggleOn State: `ToggleOnEvents`</span></span>  
<span data-ttu-id=&quot;aafda-247&quot;>ToggleOff 상태에 대한 이벤트 구성 유형: `ToggleOffEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-247&quot;>Event configuration type for the ToggleOff State: `ToggleOffEvents`</span></span>

```c#
// Toggle On Events
ToggleOnEvents toggleOnEvent = interactiveElement.GetStateEvents<ToggleOnEvents>(&quot;ToggleOn");

toggleOnEvent.OnToggleOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled On");
});

// Toggle Off Events
ToggleOffEvents toggleOffEvent = interactiveElement.GetStateEvents<ToggleOffEvents>("ToggleOff");

toggleOffEvent.OnToggleOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled Off");
});
```

### <a name="speech-keyword-state"></a><span data-ttu-id="aafda-248">음성 키워드 상태</span><span class="sxs-lookup"><span data-stu-id="aafda-248">Speech Keyword State</span></span>

<span data-ttu-id="aafda-249">Speech 키워드 상태는 Mixed Reality Speech Profile에 정의된 키워드를 수신 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-249">The Speech Keyword state listens for the keywords defined in the Mixed Reality Speech Profile.</span></span> <span data-ttu-id="aafda-250">모든 새 키워드는 런타임 전에 음성 명령 프로필에 등록해야 합니다(아래 단계).</span><span class="sxs-lookup"><span data-stu-id="aafda-250">Any new keyword MUST be registered in the speech command profile prior to runtime (steps below).</span></span> 

<span data-ttu-id="aafda-251">**음성 키워드 상태 동작** 
 ![ 가상 상호 작용이 있는 음성 키워드](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="aafda-251">**Speech Keyword State Behavior**
![Speech keyword with virtual interaction](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span></span>

<span data-ttu-id="aafda-252">**Speech 키워드 상태 검사기** 
 ![ 검사기에서 음성 키워드 구성 요소](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="aafda-252">**Speech Keyword State Inspector**
![Speech keyword component in the Inspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span></span>

> [!NOTE]
> <span data-ttu-id="aafda-253">Speech Keyword 상태는 위의 gif에서 F5 키를 눌러 편집기에서 트리거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-253">The Speech Keyword state was triggered in editor by pressing the F5 key in the gif above.</span></span> <span data-ttu-id="aafda-254">음성에 대한 편집기 테스트에서 설정은 아래 단계에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-254">Setting up in editor testing for speech is outlined the steps below.</span></span> 

#### <a name="how-to-register-a-speech-commandkeyword"></a><span data-ttu-id="aafda-255">음성 명령/키워드를 등록하는 방법</span><span class="sxs-lookup"><span data-stu-id="aafda-255">How to Register a Speech Command/Keyword</span></span>

1. <span data-ttu-id="aafda-256">**MixedRealityToolkit** 게임 개체 선택</span><span class="sxs-lookup"><span data-stu-id="aafda-256">Select the **MixedRealityToolkit** game object</span></span>

1. <span data-ttu-id="aafda-257">현재 프로필 **복사 및 사용자 지정을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-257">Select **Copy and Customize** the current profile</span></span>

1. <span data-ttu-id="aafda-258">입력 섹션으로 이동하고 **복제를** 선택하여 입력 프로필을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-258">Navigate to the Input section and select **Clone** to enable modification of the Input profile</span></span>

1. <span data-ttu-id="aafda-259">입력 프로필의 Speech 섹션에 Scroll down 음성 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="aafda-259">Scroll down to the Speech section in the Input profile and clone the Speech Profile</span></span>

    ![MRTK 게임 개체의 음성 키워드 프로필](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. <span data-ttu-id="aafda-261">새 음성 명령 추가를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-261">Select Add a New Speech Command</span></span>

    ![MRTK 프로필에 새 음성 키워드 추가](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. <span data-ttu-id="aafda-263">new 키워드를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-263">Enter the new keyword.</span></span> <span data-ttu-id="aafda-264">선택 사항: 편집기에서 테스트할 수 있도록 KeyCode를 F5(또는 다른 KeyCode)로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-264">Optional: Change the KeyCode to F5 (or another KeyCode) to allow for testing in editor.</span></span> 

    ![MRTK 프로필에서 음성 키워드 구성](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. <span data-ttu-id="aafda-266">Interactive Element Speech 키워드 상태 검사기로 돌아가기 **키워드 추가를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-266">Go back to the Interactive Element Speech Keyword state inspector and select **Add Keyword**</span></span> 

    ![대화형 요소 구성 요소에 키워드 추가](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![키워드 유효성 검사 및 등록](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. <span data-ttu-id="aafda-269">음성 프로필에 방금 등록 된 새 키워드를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-269">Enter the new keyword that was just registered in the Speech Profile</span></span>

    ![새 speech 키워드 입력](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


<span data-ttu-id="aafda-271">편집기에서 Speech 키워드 상태를 테스트 하려면 6 단계 (F5)에 정의 된 KeyCode를 눌러 speech 키워드 인식 이벤트를 시뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-271">To test the Speech Keyword state in editor, press the KeyCode that was defined in step 6 (F5) to simulate the speech keyword recognized event.</span></span>

#### <a name="getting-speech-keyword-state-events"></a><span data-ttu-id="aafda-272">음성 키워드 상태 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="aafda-272">Getting Speech Keyword State Events</span></span>

<span data-ttu-id="aafda-273">SpeechKeyword 상태에 대 한 이벤트 구성 유형입니다. `SpeechKeywordEvents`</span><span class="sxs-lookup"><span data-stu-id="aafda-273">Event configuration type for the SpeechKeyword State: `SpeechKeywordEvents`</span></span>

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>("SpeechKeyword");

speechKeywordEvents.OnAnySpeechKeywordRecognized.AddListener((speechEventData) =>
{
    Debug.Log($"{speechEventData.Command.Keyword} recognized");
});

// Get the "Change" Keyword event specifically
KeywordEvent keywordEvent = speechKeywordEvents.Keywords.Find((keyword) => keyword.Keyword == "Change");

keywordEvent.OnKeywordRecognized.AddListener(() =>
{ 
    Debug.Log("Change Keyword Recognized"); 
});
```

## <a name="custom-states"></a><span data-ttu-id="aafda-274">사용자 지정 상태</span><span class="sxs-lookup"><span data-stu-id="aafda-274">Custom States</span></span>

### <a name="how-to-create-a-custom-state-via-inspector"></a><span data-ttu-id="aafda-275">Inspector를 통해 사용자 지정 상태를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="aafda-275">How to Create a Custom State via Inspector</span></span> 

<span data-ttu-id="aafda-276">Inspector를 통해 만든 사용자 지정 상태는 기본 상태 이벤트 구성으로 초기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-276">The custom state created via inspector will be initialized with the default state event configuration.</span></span> <span data-ttu-id="aafda-277">사용자 지정 상태에 대 한 기본 이벤트 구성은 형식이 `StateEvents` 며 OnStateOn 및 OnStateOff 이벤트를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-277">The default event configuration for a custom state is of type `StateEvents` and contains the OnStateOn and OnStateOff events.</span></span>

1. <span data-ttu-id="aafda-278">대화형 요소에 대 한 검사기에서 **사용자 지정 상태 만들기** 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-278">Navigate to **Create Custom State** in the inspector for Interactive Element.</span></span>
    
    ![사용자 지정 상태 만들기](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. <span data-ttu-id="aafda-280">새 상태의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-280">Enter the name of the new state.</span></span> <span data-ttu-id="aafda-281">이 이름은 고유 해야 하며 기존 코어 상태와 같을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-281">This name must be unique and cannot be the same as the existing core states.</span></span> 
    
    ![새 사용자 지정 상태의 이름 입력](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. <span data-ttu-id="aafda-283">상태 목록에 추가할 **상태 이름 설정** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-283">Select **Set State Name** to add to the state list.</span></span>
    
    ![상태 목록에 사용자 지정 상태 추가](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   <span data-ttu-id="aafda-285">이 사용자 지정 상태는 `StateEvents` 및 이벤트를 포함 하는 기본 이벤트 구성으로 초기화 됩니다 `OnStateOn` `OnStateOff` .</span><span class="sxs-lookup"><span data-stu-id="aafda-285">This custom state is initialized with the default `StateEvents` event configuration which contains the `OnStateOn` and `OnStateOff` events.</span></span> <span data-ttu-id="aafda-286">새 상태에 대 한 사용자 지정 이벤트 구성을 만들려면 사용자 지정 [이벤트 구성을 사용 하 여 사용자 지정 상태 만들기](#creating-a-custom-state-with-a-custom-event-configuration)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aafda-286">To create a custom event configuration for a new state see: [Creating a Custom State with a Custom Event Configuration](#creating-a-custom-state-with-a-custom-event-configuration).</span></span>
    
    ![대화형 요소 구성 요소에 표시된 새 상태](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a><span data-ttu-id=&quot;aafda-288&quot;>스크립트를 통해 사용자 지정 상태를 만드는 방법</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;aafda-288&quot;>How to Create a Custom State via Script</span></span>

```c#
interactiveElement.AddNewState(&quot;MyNewState");

// A new state by default is initialized with a the default StateEvents configuration which contains the 
// OnStateOn and OnStateOff events

StateEvents myNewStateEvents = interactiveElement.GetStateEvents<StateEvents>("MyNewState");

myNewStateEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"MyNewState is On");
});

```

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a><span data-ttu-id="aafda-289">사용자 지정 이벤트 구성을 통해 사용자 지정 상태 만들기</span><span class="sxs-lookup"><span data-stu-id="aafda-289">Creating a Custom State with a Custom Event Configuration</span></span> 

<span data-ttu-id="aafda-290">**키보드라는** 사용자 지정 상태에 대한 예제 파일은 MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-290">Example files for a custom state named **Keyboard** are located here: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span></span>

<span data-ttu-id="aafda-291">다음 단계에서는 사용자 지정 상태 이벤트 구성 및 수신기 파일을 만드는 기존 예제를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-291">The following steps walk through an existing example of creating a custom state event configuration and receiver files.</span></span>

1. <span data-ttu-id="aafda-292">상태 이름을 생각해 보세요.</span><span class="sxs-lookup"><span data-stu-id="aafda-292">Think of a state name.</span></span>  <span data-ttu-id="aafda-293">이 이름은 고유해야 하며 기존 핵심 상태와 같을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-293">This name must be unique and cannot be the same as the existing core states.</span></span> <span data-ttu-id="aafda-294">이 예제에서는 상태 이름이 **키보드** 로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-294">For the purposes of this example, the state name is going to be **Keyboard**.</span></span>

1. <span data-ttu-id="aafda-295">state name + "Receiver" 및 state name + "Events"라는 두 개의 .cs 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-295">Create two .cs files named state name + "Receiver" and state name + "Events".</span></span> <span data-ttu-id="aafda-296">이러한 파일의 이름 지정은 내부적으로 고려되며 상태 이름 + 이벤트/수신자 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-296">The naming of these files are taken into consideration internally and must follow the state name + Event/Receiver convention.</span></span> 

    ![키보드 상태 스크립트](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. <span data-ttu-id="aafda-298">파일 내용에 대한 자세한 내용은 KeyboardEvents.cs 및 KeyboardReceiver.cs 파일을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aafda-298">See the KeyboardEvents.cs and KeyboardReceiver.cs files for more details on file contents.</span></span> <span data-ttu-id="aafda-299">새 이벤트 구성 클래스는 에서 상속해야 `BaseInteractionEventConfiguration` 하며 새 이벤트 수신기 클래스는 에서 상속해야 `BaseEventReceiver` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-299">New event configuration classes must inherit from `BaseInteractionEventConfiguration` and new event receiver classes must inherit from `BaseEventReceiver`.</span></span>  <span data-ttu-id="aafda-300">키보드 상태에 대한 상태 설정의 예는 `CustomStateSettingExample.cs` 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-300">Examples on state setting for the Keyboard state are located in the `CustomStateSettingExample.cs` file.</span></span> 

1. <span data-ttu-id="aafda-301">상태 이름을 사용하여 대화형 요소에 상태를 추가합니다. 이벤트 구성 및 이벤트 수신기 파일이 있는 경우 상태 이름이 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-301">Add the state to Interactive Element using the state name, the state name will be recognized if event configuration and event receiver files exist.</span></span>  <span data-ttu-id="aafda-302">사용자 지정 이벤트 구성 파일의 속성은 검사기에서 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-302">The properties in the custom event configuration file should appear in the inspector.</span></span>

    <span data-ttu-id="aafda-303">![대화형 요소에 사용자 지정 상태 추가 ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ 대화형 요소에서 인식되는 사용자 지정 상태](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span><span class="sxs-lookup"><span data-stu-id="aafda-303">![Adding custom state to interactive element](../images/interactive-element/InEditor/AddKeyboardState.png) ![Custom state recognized in the interactive element](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span></span>


1. <span data-ttu-id="aafda-304">이벤트 구성 및 이벤트 수신기 파일의 더 많은 예제는 다음 경로의 파일을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aafda-304">For more examples of event configuration and event receiver files see the files at these paths:</span></span>    
- <span data-ttu-id="aafda-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span><span class="sxs-lookup"><span data-stu-id="aafda-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span></span>
- <span data-ttu-id="aafda-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span><span class="sxs-lookup"><span data-stu-id="aafda-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span></span>

## <a name="example-scene"></a><span data-ttu-id="aafda-307">장면 예</span><span class="sxs-lookup"><span data-stu-id="aafda-307">Example Scene</span></span> 

<span data-ttu-id="aafda-308">대화형 요소 + 상태 시각화 도우미에 대 한 예제 장면이 여기에 있습니다. MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span><span class="sxs-lookup"><span data-stu-id="aafda-308">The example scene for Interactive Element + State Visualizer is located here: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span></span>

![대화형 요소 및 상태 시각화 도우미가 있는 예제 장면](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a><span data-ttu-id="aafda-310">Compressable 단추</span><span class="sxs-lookup"><span data-stu-id="aafda-310">Compressable Button</span></span>

<span data-ttu-id="aafda-311">예제 장면에는 및 라는 prefabs 포함 되어 있습니다 `CompressableButton` `CompressableButtonToggle` . 이러한 Prefabs는 `PressableButtonHoloLens2` 대화형 요소와 상태 시각화 도우미를 사용 하 여 생성 된 단추의 동작을 미러링합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-311">The example scene contains prefabs named `CompressableButton` and `CompressableButtonToggle`, these prefabs mirror the behavior of the `PressableButtonHoloLens2` buttons, that are constructed using Interactive Element and the State Visualizer.</span></span> <span data-ttu-id="aafda-312">`CompressableButton`구성 요소는 현재 `PressableButton`  +  `PressableButtonHoloLens2` `BaseInteractiveElement` 기본 클래스로의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-312">The `CompressableButton` component is currently a combination of `PressableButton` + `PressableButtonHoloLens2` with `BaseInteractiveElement`as a base class.</span></span> 

## <a name="state-visualizer-experimental"></a><span data-ttu-id="aafda-313">상태 시각화 도우미 [실험적]</span><span class="sxs-lookup"><span data-stu-id="aafda-313">State Visualizer [Experimental]</span></span>

<span data-ttu-id="aafda-314">상태 시각화 도우미 구성 요소는 연결 된 대화형 요소 구성 요소에 정의 된 상태에 따라 개체에 애니메이션을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-314">The State Visualizer component adds animations to an object based on the states defined in a linked Interactive Element component.</span></span> <span data-ttu-id="aafda-315">이 구성 요소는 애니메이션 자산을 만들고, MixedRealityToolkit 폴더에 배치 하 고, 대상 게임 개체에 애니메이션 효과 속성을 추가 하 여 간소화 된 애니메이션 키프레임 설정을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-315">This component creates animation assets, places them in the MixedRealityToolkit.Generated folder and enables simplified animation keyframe setting through adding Animatable properties to a target game object.</span></span> <span data-ttu-id="aafda-316">상태 간에 애니메이션 전환을 사용 하도록 설정 하기 위해 애니메이터 컨트롤러 자산이 만들어지고 기본 상태 시스템이 연결 된 매개 변수 및 모든 상태 전환으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-316">To enable animation transitions between states, an Animator Controller asset is created and a default state machine is generated with associated parameters and any state transitions.</span></span>  <span data-ttu-id="aafda-317">상태 시스템은 Unity의 애니메이터 창에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-317">The state machine can be viewed in Unity's Animator window.</span></span>

### <a name="state-visualizer-and-unity-animation-system"></a><span data-ttu-id="aafda-318">상태 시각화 도우미 및 Unity 애니메이션 시스템</span><span class="sxs-lookup"><span data-stu-id="aafda-318">State Visualizer and Unity Animation System</span></span>

<span data-ttu-id="aafda-319">상태 시각화 도우미는 현재 Unity 애니메이션 시스템을 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-319">The State Visualizer currently leverages the Unity Animation System.</span></span> 

<span data-ttu-id="aafda-320">상태 시각화 도우미의 **새 애니메이션 클립 생성** 단추를 누르면 새 애니메이션 클립 자산이 대화형 요소의 상태 이름에 따라 생성 되 고 MixedRealityToolkit 폴더에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-320">When the **Generate New Animation Clips** button in the State Visualizer is pressed, new animation clip assets are generated based on the state names in Interactive Element and are placed in the MixedRealityToolkit.Generated folder.</span></span> <span data-ttu-id="aafda-321">각 상태 컨테이너의 애니메이션 클립 속성은 연결 된 애니메이션 클립으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-321">The Animation Clip property in each state container is set to the associated animation clip.</span></span>

![상태 시각화 요소의 애니메이션 클립](../images/interactive-element/StateVisualizer/AnimationClips.png)

<span data-ttu-id="aafda-323">애니메이션 클립 간의 부드러운 전환을 관리 하기 위해 [애니메이터 상태 컴퓨터](https://docs.unity3d.com/Manual/AnimationOverview.html) 도 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-323">An [Animator State Machine](https://docs.unity3d.com/Manual/AnimationOverview.html) is also generated to manage smooth transitions between animation clips.</span></span>  <span data-ttu-id="aafda-324">기본적으로 상태 시스템은 [모든](https://docs.unity3d.com/Manual/class-State.html) 상태를 사용 하 여 대화형 요소의 모든 상태 간 전환을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-324">By default, the state machine utilizes the [Any State](https://docs.unity3d.com/Manual/class-State.html) to allow transitions between any state in Interactive Element.</span></span> 

<span data-ttu-id="aafda-325">[Animator에서 트리거되는 상태 시각화 도우미도](https://docs.unity3d.com/Manual/AnimationParameters.html) 각 상태에 대해 생성되며, 트리거 매개 변수는 상태 시각화 도우미에서 애니메이션을 트리거하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-325">[State visualizers triggered in the animator](https://docs.unity3d.com/Manual/AnimationParameters.html) are also generated for each state, the trigger parameters are used in the State Visualizer to trigger an animation.</span></span>

![Unity 상태 시스템](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a><span data-ttu-id="aafda-327">런타임 제한 사항</span><span class="sxs-lookup"><span data-stu-id="aafda-327">Runtime Limitations</span></span> 

<span data-ttu-id="aafda-328">상태 시각화 도우미는 검사기를 통해 개체에 추가해야 하며 스크립트를 통해 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-328">The State Visualizer must be added to an object via the Inspector and cannot be added via script.</span></span>  <span data-ttu-id="aafda-329">AnimatorStateMachine/AnimationController를 수정하는 속성은 앱을 빌드할 때 제거되는 편집기 네임스페이스( `UnityEditor.Animations` )에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-329">The properties that modify the AnimatorStateMachine/AnimationController are contained in an editor namespace (`UnityEditor.Animations`) which get removed when the app is built.</span></span>

## <a name="how-to-use-the-state-visualizer"></a><span data-ttu-id="aafda-330">상태 시각화 도우미를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="aafda-330">How to use the State Visualizer</span></span>

1. <span data-ttu-id="aafda-331">큐브 만들기</span><span class="sxs-lookup"><span data-stu-id="aafda-331">Create a Cube</span></span>
1. <span data-ttu-id="aafda-332">대화형 요소 연결</span><span class="sxs-lookup"><span data-stu-id="aafda-332">Attach Interactive Element</span></span>
1. <span data-ttu-id="aafda-333">연결 상태 시각화 도우미</span><span class="sxs-lookup"><span data-stu-id="aafda-333">Attach State Visualizer</span></span>
1. <span data-ttu-id="aafda-334">**새 애니메이션 클립 생성 선택**</span><span class="sxs-lookup"><span data-stu-id="aafda-334">Select **Generate New Animation Clips**</span></span>

    ![새 애니메이션 클립 생성](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![시각화 도우미 및 대화형 요소 구성 요소에서 생성된 애니메이션 클립 표시](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. <span data-ttu-id="aafda-337">포커스 상태 컨테이너에서 **대상 추가를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-337">In the Focus state container, select **Add Target**</span></span>

    ![상태 시각화 도우미 대상 추가](../images/interactive-element/StateVisualizer/AddTarget.png)

1. <span data-ttu-id="aafda-339">현재 게임 개체를 대상 필드로 끌기</span><span class="sxs-lookup"><span data-stu-id="aafda-339">Drag the current game object to the target field</span></span> 

    ![상태 시각화 도우미 대상 설정](../images/interactive-element/StateVisualizer/SetTarget.png)

1. <span data-ttu-id="aafda-341">큐브 애니메이션 가능 속성 폴딩 열기</span><span class="sxs-lookup"><span data-stu-id="aafda-341">Open the Cube Animatable Properties foldout</span></span>
1. <span data-ttu-id="aafda-342">애니메이션 가능 속성 드롭다운 메뉴를 선택하고 **색을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-342">Select the Animatable property drop down menu and select **Color**</span></span>

    ![상태 시각화 도우미 색 설정](../images/interactive-element/StateVisualizer/SetColor.png)

1. <span data-ttu-id="aafda-344">**색 애니메이션 가능 속성 추가를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-344">Select **Add the Color Animatable Property**</span></span>

    ![시각화 도우미 색 애니메이션 가능 속성 선택](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. <span data-ttu-id="aafda-346">색 선택</span><span class="sxs-lookup"><span data-stu-id="aafda-346">Choose a Color</span></span> 

    ![색상환에서 시각화 도우미 색 선택](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. <span data-ttu-id="aafda-348">재생을 누르고 전환 색 변경을 관찰 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-348">Press play and observe the transitional color change</span></span>

    ![가상 손 상호 작용을 사용 하 여 색 변경 예제 전환](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a><span data-ttu-id="aafda-350">애니메이션 효과 속성</span><span class="sxs-lookup"><span data-stu-id="aafda-350">Animatable Properties</span></span>

<span data-ttu-id="aafda-351">애니메이션 효과 속성의 주요 목적은 애니메이션 클립 키 프레임 설정을 간소화 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-351">The primary purpose of the Animatable Properties is to simplify animation clip keyframe setting.</span></span>  <span data-ttu-id="aafda-352">사용자가 Unity 애니메이션 시스템에 친숙 하 고 생성 된 애니메이션 클립에서 키 프레임을 직접 설정 하는 것을 선호 하는 경우 애니메이션 효과 속성을 대상 개체에 추가 하 고 Unity의 애니메이션 창 (Windows > 애니메이션 > 애니메이션)에서 클립을 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-352">If a user is familiar with the Unity Animation System and would prefer to directly set keyframes on the generated animation clips, then they can simply not add Animatable properties to a target object and open the clip in Unity's Animation window (Windows > Animation > Animation).</span></span> 

<span data-ttu-id="aafda-353">애니메이션에 애니메이션 효과 속성을 사용 하는 경우 곡선 형식은 EaseInOut로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-353">If using the Animatable properties for animation, the curve type is set to EaseInOut.</span></span>

<span data-ttu-id="aafda-354">**현재 애니메이션 효과 속성:**</span><span class="sxs-lookup"><span data-stu-id="aafda-354">**Current Animatable Properties:**</span></span>
- [<span data-ttu-id="aafda-355">크기 조정 오프셋</span><span class="sxs-lookup"><span data-stu-id="aafda-355">Scale Offset</span></span>](#scale-offset)
- [<span data-ttu-id="aafda-356">위치 오프셋</span><span class="sxs-lookup"><span data-stu-id="aafda-356">Position Offset</span></span>](#position-offset)
- [<span data-ttu-id="aafda-357">색상</span><span class="sxs-lookup"><span data-stu-id="aafda-357">Color</span></span>](#color)
- [<span data-ttu-id="aafda-358">셰이더 색</span><span class="sxs-lookup"><span data-stu-id="aafda-358">Shader Color</span></span>](#shader-color)
- [<span data-ttu-id="aafda-359">셰이더 Float</span><span class="sxs-lookup"><span data-stu-id="aafda-359">Shader Float</span></span>](#shader-float)
- [<span data-ttu-id="aafda-360">셰이더 벡터</span><span class="sxs-lookup"><span data-stu-id="aafda-360">Shader Vector</span></span>](#shader-vector)

### <a name="scale-offset"></a><span data-ttu-id="aafda-361">크기 조정 오프셋</span><span class="sxs-lookup"><span data-stu-id="aafda-361">Scale Offset</span></span>

<span data-ttu-id="aafda-362">눈금 오프셋 애니메이션 효과 속성은 개체의 현재 소수 자릿수를 사용 하 여 정의 된 오프셋을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-362">The Scale Offset Animatable property takes the current scale of the object and adds the defined offset.</span></span>

![가상 손 상호 작용을 사용 하는 크기 조정 오프셋](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a><span data-ttu-id="aafda-364">위치 오프셋</span><span class="sxs-lookup"><span data-stu-id="aafda-364">Position Offset</span></span>

<span data-ttu-id="aafda-365">Position Offset 애니메이션 효과 속성은 개체의 현재 위치를 사용 하 여 정의 된 오프셋을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-365">The Position Offset Animatable property takes the current position of the object and adds the defined offset.</span></span>

![가상 손 상호 작용을 사용 하는 위치 오프셋](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a><span data-ttu-id="aafda-367">색</span><span class="sxs-lookup"><span data-stu-id="aafda-367">Color</span></span>

<span data-ttu-id="aafda-368">색 애니메이션 효과 속성은 재질에 기본 색 속성이 있는 경우 재질의 기본 색을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-368">The Color Animatable property represents the main color of a material if the material has a main color property.</span></span> <span data-ttu-id="aafda-369">이 속성은 속성에 애니메이션을 적용 `material._Color` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-369">This property animates the `material._Color` property.</span></span>

![가상 손 상호 작용으로 색 변경 포커스](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a><span data-ttu-id="aafda-371">셰이더 색</span><span class="sxs-lookup"><span data-stu-id="aafda-371">Shader Color</span></span>

<span data-ttu-id="aafda-372">셰이더 색 애니메이션 효과 속성은 Color 형식의 셰이더 속성을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-372">The Shader Color Animatable property refers to a shader property of type color.</span></span> <span data-ttu-id="aafda-373">모든 셰이더 속성에는 속성 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-373">A property name is required for all shader properties.</span></span> <span data-ttu-id="aafda-374">아래 gif는 주 재질 색이 아닌 Fill_Color 라는 셰이더 색 속성에 애니메이션을 적용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-374">The gif below demonstrates animating a shader color property named Fill_Color that is not the main material color.</span></span>  <span data-ttu-id="aafda-375">재질 검사기에서 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-375">Observe the changing values in the material inspector.</span></span>

![가상 손을 상호 작용 하는 음영 색](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a><span data-ttu-id="aafda-377">셰이더 Float</span><span class="sxs-lookup"><span data-stu-id="aafda-377">Shader Float</span></span>

<span data-ttu-id="aafda-378">Shader Float 애니메이션 효과 속성은 Float 형식의 셰이더 속성을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-378">The Shader Float Animatable property refers to a shader property of type float.</span></span> <span data-ttu-id="aafda-379">모든 셰이더 속성에는 속성 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-379">A property name is required for all shader properties.</span></span> <span data-ttu-id="aafda-380">아래 gif에서 금속성 속성에 대 한 재질 검사기의 변경 값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-380">In the gif below, observe the changing values in the material inspector for the Metallic property.</span></span> 

![가상 손을 상호 작용 하는 셰이더 float](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a><span data-ttu-id="aafda-382">셰이더 벡터</span><span class="sxs-lookup"><span data-stu-id="aafda-382">Shader Vector</span></span>

<span data-ttu-id="aafda-383">셰이더 Vector 애니메이션 효과 속성은 System.numerics.vector3 및 system.numerics.vector4 형식의 셰이더 속성을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-383">The Shader Vector Animatable property refers to a shader property of type Vector4.</span></span> <span data-ttu-id="aafda-384">모든 셰이더 속성에는 속성 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-384">A property name is required for all shader properties.</span></span> <span data-ttu-id="aafda-385">아래 gif에서 바둑판식 배열 (Main Tex_ST) 속성에 대 한 재질 검사기의 변경 값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-385">In the gif below, observe the changing values in the material inspector for the Tiling (Main Tex_ST) property.</span></span> 

![가상 손 상호 작용이 있는 셰이더 벡터](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a><span data-ttu-id="aafda-387">애니메이션 효과 셰이더 속성 이름을 찾는 방법</span><span class="sxs-lookup"><span data-stu-id="aafda-387">How to Find Animatable Shader Property Names</span></span>

1. <span data-ttu-id="aafda-388">창 > 애니메이션 > 애니메이션으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-388">Navigate to Window > Animation > Animation</span></span>
1. <span data-ttu-id="aafda-389">상태 시각화 도우미가 있는 개체가 계층 구조에서 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-389">Ensure that the object with the State Visualizer is selected in the hierarchy</span></span>
1. <span data-ttu-id="aafda-390">애니메이션 창에서 애니메이션 클립 선택</span><span class="sxs-lookup"><span data-stu-id="aafda-390">Select any animation clip in the Animation window</span></span>
1. <span data-ttu-id="aafda-391">**속성 추가를** 선택하고 Mesh 렌더러 폴딩을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-391">Select **Add Property**, open the Mesh Renderer foldout</span></span> 

    ![Animator 창에 애니메이션 속성 추가](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. <span data-ttu-id="aafda-393">이 목록에는 모든 Animatable 속성 이름의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafda-393">This list contains the names of all the Animatable property names</span></span> 

    ![Animator 창의 메시 렌더러 애니메이션 속성](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a><span data-ttu-id="aafda-395">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aafda-395">See also</span></span>

- [<span data-ttu-id="aafda-396">**단추**</span><span class="sxs-lookup"><span data-stu-id="aafda-396">**Buttons**</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="aafda-397">**범위 제어**</span><span class="sxs-lookup"><span data-stu-id="aafda-397">**Bounds Control**</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="aafda-398">**Grid 개체 컬렉션**</span><span class="sxs-lookup"><span data-stu-id="aafda-398">**Grid Object Collection**</span></span>](../ux-building-blocks/object-collection.md)
- [<span data-ttu-id="aafda-399">**RadialView Solver**</span><span class="sxs-lookup"><span data-stu-id="aafda-399">**RadialView Solver**</span></span>](../ux-building-blocks/solvers/solver.md)
