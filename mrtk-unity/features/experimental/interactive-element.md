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
# <a name="interactive-element-experimental"></a>Interactive 요소 [실험적]

MRTK 입력 시스템에 대 한 단순화 된 중앙 진입점입니다. 상태 관리 방법, 이벤트 관리 및 핵심 상호 작용 상태의 상태 설정 논리가 포함 됩니다.

Interactive 요소는 unity 2019.3: [Serialize 참조](https://docs.unity3d.com/ScriptReference/SerializeReference.html)의 새로운 기능을 활용 하므로 unity 2019.3에서 지원 되는 실험적 기능입니다.

### <a name="interactive-element-inspector"></a>대화형 요소 검사기

재생 모드에서 대화형 요소 검사기는 현재 상태가 활성 상태 인지 여부를 나타내는 시각적 피드백을 제공 합니다. 활성 상태 이면 사이안 색으로 강조 표시 됩니다.  상태가 활성이 아니면 색은 변경 되지 않습니다. 검사기의 상태 옆에 있는 숫자는 상태 값입니다. 상태가 활성 이면 값은 1이 고, 상태가 활성이 아니면 값은 0입니다.

![가상 손을 상호 작용 하는 대화형 요소](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a>코어 상태

Interactive 요소는 핵심 상태를 포함 하 고 [사용자 지정 상태](#custom-states)를 추가할 수 있도록 지원 합니다.  핵심 상태는에 정의 된 상태 설정 논리가 이미 있는 상태입니다 `BaseInteractiveElement` . 다음은 현재 입력 기반 코어 상태의 목록입니다. 

### <a name="current-core-states"></a>현재 코어 상태

- [기본](#default-state) 

근거리 및 원거리 상호 작용 핵심 상태:
- [포커스](#focus-state) 

거의 상호 작용 코어 상태:

- [가까이에 집중](#focus-near-state)
- [터치](#touch-state)

Far 상호 작용 코어 상태:
- [지금 포커스](#focus-far-state)
- [지금 선택](#select-far-state)

기타 핵심 상태:
- [클릭됨](#clicked-state)
- [설정 및 해제](#toggle-on-and-toggle-off-state)
- [Speech 키워드](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a>Inspector를 통해 핵심 상태를 추가 하는 방법

1. 대화형 요소에 대 한 검사기에서 **코어 상태 추가** 로 이동 합니다.

    ![검사기를 통해 핵심 상태 추가](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. **상태 선택** 단추를 선택 하 여 추가할 핵심 상태를 선택 합니다. 메뉴의 상태는 상호 작용 유형별로 정렬 됩니다.

    ![상태가 선택 된 검사기를 통해 코어 상태 추가](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. 이벤트 구성 foldout을 열고 상태와 연결 된 이벤트와 속성을 확인 합니다.

    ![이벤트 구성을 사용 하 여 검사기를 통해 핵심 상태 추가](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a>스크립트를 통해 핵심 상태를 추가 하는 방법

메서드를 사용 `AddNewState(stateName)` 하 여 코어 상태를 추가 합니다. 사용 가능한 핵심 상태 이름 목록은 열거형을 사용 합니다 `CoreInteractionState` .

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a>상태 내부 구조 

대화형 요소의 상태는 형식입니다 `InteractionState` .  에는 `InteractionState` 다음 속성이 포함 되어 있습니다.

- **이름:** 상태의 이름입니다.
- **값:** 상태 값입니다.  상태가 켜진 경우 상태 값은 1입니다. 상태가 꺼져 있으면 상태 값은 0입니다.
- **활성:** 상태가 현재 활성 상태인지 여부입니다. 활성 속성의 값은 상태가 켜지면 true이고, 상태가 해제되어 있으면 false입니다. 
- **상호 작용 유형:** 상태의 상호 작용 형식은 상태가 의도된 상호 작용의 형식입니다. 
  - `None`: 어떤 형식의 입력 상호 작용도 지원하지 않습니다.
  - `Near`: 근접 상호 작용 지원. 입력은 굴절된 손에서 다른 게임 개체와 직접 연결되는 경우( 즉, 굴절된 손의 위치가 세계 공간에서 게임 개체의 위치와 가까운 경우) 근거리 상호 작용으로 간주됩니다.
  - `Far`: 원거리 상호 작용 지원. 입력은 게임 개체와의 직접 연락이 필요하지 않은 경우 원거리 상호 작용으로 간주됩니다. 예를 들어 컨트롤러 광선 또는 응시를 통한 입력은 원거리 상호 작용 입력으로 간주됩니다.
  - `NearAndFar`: 가까운 상호 작용 및 원거리 상호 작용 지원을 모두 포함합니다. 
  - `Other`: 포인터 독립적 상호 작용 지원.
- **이벤트 구성:** 상태에 대한 이벤트 구성은 직렬화된 이벤트 프로필 진입점입니다. 

이러한 모든 속성은 Interactive 요소에 포함된 에서 내부적으로 `State Manager` 설정됩니다. 상태를 수정하려면 다음 도우미 메서드를 사용합니다.

**상태 설정 도우미 메서드**

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

상태의 이벤트 구성을 얻는 것은 상태 자체에 따라 다릅니다. 각 코어 상태에는 각 핵심 상태를 설명 하는 섹션 아래에 설명 된 특정 이벤트 구성 유형이 있습니다.

다음은 상태 이벤트 구성을 가져오는 일반적인 예입니다.

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a>기본 상태

기본 상태는 항상 대화형 요소에 표시 됩니다.  이 상태는 다른 모든 상태가 활성 상태가 아닌 경우에만 활성화 됩니다.  다른 상태가 활성 상태가 되 면 기본 상태는 내부적으로 off로 설정 됩니다. 

대화형 요소는 상태 목록에 있는 기본 및 포커스 상태를 사용 하 여 초기화 됩니다. 기본 상태는 항상 상태 목록에 있어야 합니다. 

#### <a name="getting-default-state-events"></a>기본 상태 이벤트 가져오기

기본 상태에 대 한 이벤트 구성 유형입니다. `StateEvents`

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

### <a name="focus-state"></a>포커스 상태

포커스 상태는 커서와 동등한 혼합 현실로 간주할 수 있는 근거리 및 원거리 상호 작용 상태입니다. 포커스 상태에 대 한 근거리 및 원거리 상호 작용 사이의 구별 요소는 현재 활성 포인터 형식입니다.  포커스 상태에 대 한 포인터 형식이 Poke 포인터인 경우 상호 작용은 거의 상호 작용 하는 것으로 간주 됩니다.  기본 포인터가 Poke 포인터가 아닌 경우 상호 작용으로 인 한 것으로 간주 됩니다. 포커스 상태는 기본적으로 대화형 요소에 표시 됩니다.

**포커스 상태 동작** 
 ![ 가상 손 상호 작용을 사용 하는 포커스 상태](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif) 

**포커스 상태 검사기** 
 ![ Inpsector의 포커스 상태](../images/interactive-element/InEditor/FocusStateInspector.png)

#### <a name="getting-focus-state-events&quot;></a>포커스 상태 이벤트 가져오기

포커스 상태의 이벤트 구성 유형입니다. `FocusEvents`

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

#### <a name="focus-near-vs-focus-far-behavior"></a>가까이에 포커스를 이동 합니다. 

![가상 손 상호 작용을 통해 가까운 정도의 포커스](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a>포커스 근 상태

포커스 이벤트가 발생할 때 포커스 근사 상태가 설정되고 주 포인터가 Near 상호 작용을 나타내는 표시인 표시인 경우 Focus Near 상태가 설정됩니다. 

**포커스 근 상태 동작** 
 ![ 가상 손 상호 작용을 통해 상태 가까이에 포커스](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif) 

**상태 검사기** 
 ![ 근처 포커스 검사기에서 구성 요소 근처에 포커스](../images/interactive-element/InEditor/FocusNearStateInspector.png)

#### <a name="getting-focusnear-state-events&quot;></a>FocusNear 상태 이벤트 받기

FocusNear 상태에 대한 이벤트 구성 유형: `FocusEvents`

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

### <a name="focus-far-state"></a>포커스 원거리 상태

포커스 원거리 상태는 기본 포인터가 Pointer 포인터가 아닌 경우 설정됩니다.  예를 들어 기본 컨트롤러 광선 포인터 및 GGV(응시, 제스처, 음성) 포인터는 원거리 상호 작용 포인터로 간주됩니다.

**포커스 원거리 상태 동작** 
 ![ 가상 손 조작을 통해 멀리 떨어진 포커스 상태](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)

**포커스 원거리 상태 검사기** 
 ![ 검사기에서 멀리 떨어진 포커스 구성 요소](../images/interactive-element/InEditor/FocusFarStateInspector.png)

#### <a name="getting-focus-far-state-events&quot;></a>포커스 원거리 상태 이벤트 얻기

FocusFar 상태에 대한 이벤트 구성 유형: `FocusEvents`

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

### <a name="touch-state"></a>터치 상태

터치 상태는 굴절된 손에서 개체를 직접 터치할 때 설정되는 거의 상호 작용 상태입니다.  직접 터치는 굴절된 손의 인덱스 손가락이 개체의 세계 위치에 매우 가까이 있음을 의미합니다. 기본적으로 Touch `NearInteractionTouchableVolume` 상태가 상태 목록에 추가되면 구성 요소가 개체에 연결됩니다.  터치 이벤트를  `NearInteractionTouchableVolume` 검색하려면 또는 `NearInteractionTouchable` 구성 요소가 필요합니다.  와 의 차이점은 `NearInteractionTouchableVolume` `NearInteractionTouchable` 는 `NearInteractionTouchableVolume` 개체의 충돌체를 기반으로 터치를 `NearInteractionTouchable` 감지하고 평면의 정의된 영역 내에서 터치를 감지한다는 것입니다.

**터치 상태 동작** 
 ![ 가상 손 조작을 통해 터치 상태](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)

**터치 상태 검사기** 
 ![ 검사기에서 터치 상태 구성 요소](../images/interactive-element/InEditor/TouchStateInspector.png)

#### <a name="getting-touch-state-events&quot;></a>터치 상태 이벤트 받기

터치 상태에 대한 이벤트 구성 유형: `TouchEvents`

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

### <a name="select-far-state"></a>원거리 상태 선택

원거리 선택 상태가 `IMixedRealityPointerHandler` 표시되어 있습니다.  이 상태는 원거리 상호 작용 클릭(에어 탭)을 감지하고 기본 컨트롤러 광선 포인터 또는 GGV 포인터와 같은 원거리 상호 작용 포인터를 사용하는 원거리 상호 작용 상태입니다.  원거리 선택 상태에는 라는 이벤트 구성 폴딩 아래에 옵션이 `Global` 있습니다. `Global`가 true이면 `IMixedRealityPointerHandler` 이 전역 입력 처리기로 등록됩니다.  처리기가 전역으로 등록된 경우 입력 시스템 이벤트를 트리거하기 위해 개체에 집중할 필요가 없습니다.  예를 들어 사용자가 포커스에 있는 개체에 관계없이 에어 탭/선택 제스처가 수행될 때마다 알고 싶은 경우 `Global` 를 true로 설정합니다. 

**원거리 상태 동작** 
 ![ 선택 가상 손 조작을 통해 멀리 선택](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)

**원거리 상태 검사기** 
 ![ 선택 검사기에서 원거리 구성 요소 선택](../images/interactive-element/InEditor/SelectFarStateInspector.png)

#### <a name="getting-select-far-state-events&quot;></a>원거리 상태 이벤트 선택

SelectFar 상태에 대한 이벤트 구성 유형: `SelectFarEvents`

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

### <a name="clicked-state"></a>클릭된 상태

클릭 상태는 기본적으로 원거리 상호 작용 클릭(원거리 상태 선택)에 의해 트리거됩니다.  이 상태는 내부적으로 켜기로 전환되고 OnClicked 이벤트를 호출한 다음 즉시 꺼져 있습니다. 

> [!NOTE]
> 상태 활동을 기반으로 하는 검사기에서 시각적 피드백이 켜진 후 즉시 꺼져 있으므로 Clicked 상태에 대한 시각적 피드백이 없습니다. 

**클릭된 상태 동작** 
 ![ 가상 손 상호 작용을 통해 클릭된 상태](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)

**상태 검사기 클릭** 
 ![ 검사기에서 state component를 클릭 합니다.](../images/interactive-element/InEditor/ClickedStateInspector.png)

**Near 및 Far 클릭 상태 예제**  
메서드를 사용 하 여 추가 진입점을 통해 클릭 된 상태를 트리거할 수 있습니다 `interactiveElement.TriggerClickedState()` .  예를 들어, 사용자가 개체에 대 한 클릭을 트리거하는 근접 한 상호 작용 터치를 원하는 경우 `TriggerClickedState()` 터치 상태의 수신기로 메서드를 추가 합니다.   

![가상 핸드 상호 작용이 있는 Near 및 far 상태](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a>클릭 상태 이벤트 가져오기

클릭 한 상태의 이벤트 구성 유형입니다. `ClickedEvents`

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a>설정/해제 상태 설정/해제

토글 설정 및 설정/해제 상태는 쌍 이며 토글 동작에 대해 둘 다 있어야 합니다.  기본적으로 토글 설정 및 설정/해제 상태는 먼 트 클릭 (Far 상태 선택)을 통해 트리거됩니다.  기본적으로 설정/해제 상태는 시작 시 활성 상태 이므로 설정/해제는 off로 초기화 됩니다.  사용자가 시작 시 활성화 상태를 설정 하려면 설정/해제 상태가 true로 설정 되어 있어야 합니다 `IsSelectedOnStart` .

**상태 동작** 
 ![ ToggleOn 및 토글 가상 손 상호 작용을 사용 하 여 설정 및 해제](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)

**상태 검사자** 
 ![ ToggleOn 및 토글 검사기에서 구성 요소 설정/해제](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)

**Near 및 Far 전환 상태 예**  
클릭 상태와 마찬가지로 설정/해제 상태 설정에는 메서드를 사용 하 여 여러 진입점이 있을 수 있습니다 `interactiveElement.SetToggleStates()` . 예를 들어, 사용자가 토글 상태를 설정 하기 위해 추가 진입점으로 터치 하려는 경우 `SetToggleStates()` 터치 상태의 이벤트 중 하나에 메서드를 추가 합니다. 

![근거리 및 원거리 전환 (가상 핸드 상호 작용)](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a>설정/해제 상태 이벤트 설정 및 해제

ToggleOn 상태에 대 한 이벤트 구성 유형입니다. `ToggleOnEvents`  
ToggleOff 상태에 대한 이벤트 구성 유형: `ToggleOffEvents`

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

### <a name="speech-keyword-state"></a>음성 키워드 상태

Speech 키워드 상태는 Mixed Reality Speech Profile에 정의된 키워드를 수신 대기합니다. 모든 새 키워드는 런타임 전에 음성 명령 프로필에 등록해야 합니다(아래 단계). 

**음성 키워드 상태 동작** 
 ![ 가상 상호 작용이 있는 음성 키워드](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)

**Speech 키워드 상태 검사기** 
 ![ 검사기에서 음성 키워드 구성 요소](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)

> [!NOTE]
> Speech Keyword 상태는 위의 gif에서 F5 키를 눌러 편집기에서 트리거되었습니다. 음성에 대한 편집기 테스트에서 설정은 아래 단계에 설명되어 있습니다. 

#### <a name="how-to-register-a-speech-commandkeyword"></a>음성 명령/키워드를 등록하는 방법

1. **MixedRealityToolkit** 게임 개체 선택

1. 현재 프로필 **복사 및 사용자 지정을** 선택합니다.

1. 입력 섹션으로 이동하고 **복제를** 선택하여 입력 프로필을 수정할 수 있습니다.

1. 입력 프로필의 Speech 섹션에 Scroll down 음성 프로필 복제

    ![MRTK 게임 개체의 음성 키워드 프로필](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. 새 음성 명령 추가를 선택합니다.

    ![MRTK 프로필에 새 음성 키워드 추가](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. new 키워드를 입력합니다. 선택 사항: 편집기에서 테스트할 수 있도록 KeyCode를 F5(또는 다른 KeyCode)로 변경합니다. 

    ![MRTK 프로필에서 음성 키워드 구성](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. Interactive Element Speech 키워드 상태 검사기로 돌아가기 **키워드 추가를** 선택합니다. 

    ![대화형 요소 구성 요소에 키워드 추가](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![키워드 유효성 검사 및 등록](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. 음성 프로필에 방금 등록 된 새 키워드를 입력 합니다.

    ![새 speech 키워드 입력](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


편집기에서 Speech 키워드 상태를 테스트 하려면 6 단계 (F5)에 정의 된 KeyCode를 눌러 speech 키워드 인식 이벤트를 시뮬레이트합니다.

#### <a name="getting-speech-keyword-state-events&quot;></a>음성 키워드 상태 이벤트 가져오기

SpeechKeyword 상태에 대 한 이벤트 구성 유형입니다. `SpeechKeywordEvents`

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>(&quot;SpeechKeyword");

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

## <a name="custom-states"></a>사용자 지정 상태

### <a name="how-to-create-a-custom-state-via-inspector"></a>Inspector를 통해 사용자 지정 상태를 만드는 방법 

Inspector를 통해 만든 사용자 지정 상태는 기본 상태 이벤트 구성으로 초기화 됩니다. 사용자 지정 상태에 대 한 기본 이벤트 구성은 형식이 `StateEvents` 며 OnStateOn 및 OnStateOff 이벤트를 포함 합니다.

1. 대화형 요소에 대 한 검사기에서 **사용자 지정 상태 만들기** 로 이동 합니다.
    
    ![사용자 지정 상태 만들기](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. 새 상태의 이름을 입력 합니다. 이 이름은 고유 해야 하며 기존 코어 상태와 같을 수 없습니다. 
    
    ![새 사용자 지정 상태의 이름 입력](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. 상태 목록에 추가할 **상태 이름 설정** 을 선택 합니다.
    
    ![상태 목록에 사용자 지정 상태 추가](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   이 사용자 지정 상태는 `StateEvents` 및 이벤트를 포함 하는 기본 이벤트 구성으로 초기화 됩니다 `OnStateOn` `OnStateOff` . 새 상태에 대 한 사용자 지정 이벤트 구성을 만들려면 사용자 지정 [이벤트 구성을 사용 하 여 사용자 지정 상태 만들기](#creating-a-custom-state-with-a-custom-event-configuration)를 참조 하세요.
    
    ![대화형 요소 구성 요소에 표시된 새 상태](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a>스크립트를 통해 사용자 지정 상태를 만드는 방법

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

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a>사용자 지정 이벤트 구성을 통해 사용자 지정 상태 만들기 

**키보드라는** 사용자 지정 상태에 대한 예제 파일은 MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample에 있습니다.

다음 단계에서는 사용자 지정 상태 이벤트 구성 및 수신기 파일을 만드는 기존 예제를 안내합니다.

1. 상태 이름을 생각해 보세요.  이 이름은 고유해야 하며 기존 핵심 상태와 같을 수 없습니다. 이 예제에서는 상태 이름이 **키보드** 로 지정됩니다.

1. state name + "Receiver" 및 state name + "Events"라는 두 개의 .cs 파일을 만듭니다. 이러한 파일의 이름 지정은 내부적으로 고려되며 상태 이름 + 이벤트/수신자 규칙을 따라야 합니다. 

    ![키보드 상태 스크립트](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. 파일 내용에 대한 자세한 내용은 KeyboardEvents.cs 및 KeyboardReceiver.cs 파일을 참조하세요. 새 이벤트 구성 클래스는 에서 상속해야 `BaseInteractionEventConfiguration` 하며 새 이벤트 수신기 클래스는 에서 상속해야 `BaseEventReceiver` 합니다.  키보드 상태에 대한 상태 설정의 예는 `CustomStateSettingExample.cs` 파일에 있습니다. 

1. 상태 이름을 사용하여 대화형 요소에 상태를 추가합니다. 이벤트 구성 및 이벤트 수신기 파일이 있는 경우 상태 이름이 인식됩니다.  사용자 지정 이벤트 구성 파일의 속성은 검사기에서 나타나야 합니다.

    ![대화형 요소에 사용자 지정 상태 추가 ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ 대화형 요소에서 인식되는 사용자 지정 상태](../images/interactive-element/InEditor/SetKeyboardStateName.png)


1. 이벤트 구성 및 이벤트 수신기 파일의 더 많은 예제는 다음 경로의 파일을 참조하세요.    
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers

## <a name="example-scene"></a>장면 예 

대화형 요소 + 상태 시각화 도우미에 대 한 예제 장면이 여기에 있습니다. MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity

![대화형 요소 및 상태 시각화 도우미가 있는 예제 장면](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a>Compressable 단추

예제 장면에는 및 라는 prefabs 포함 되어 있습니다 `CompressableButton` `CompressableButtonToggle` . 이러한 Prefabs는 `PressableButtonHoloLens2` 대화형 요소와 상태 시각화 도우미를 사용 하 여 생성 된 단추의 동작을 미러링합니다. `CompressableButton`구성 요소는 현재 `PressableButton`  +  `PressableButtonHoloLens2` `BaseInteractiveElement` 기본 클래스로의 조합입니다. 

## <a name="state-visualizer-experimental"></a>상태 시각화 도우미 [실험적]

상태 시각화 도우미 구성 요소는 연결 된 대화형 요소 구성 요소에 정의 된 상태에 따라 개체에 애니메이션을 추가 합니다. 이 구성 요소는 애니메이션 자산을 만들고, MixedRealityToolkit 폴더에 배치 하 고, 대상 게임 개체에 애니메이션 효과 속성을 추가 하 여 간소화 된 애니메이션 키프레임 설정을 사용 하도록 설정 합니다. 상태 간에 애니메이션 전환을 사용 하도록 설정 하기 위해 애니메이터 컨트롤러 자산이 만들어지고 기본 상태 시스템이 연결 된 매개 변수 및 모든 상태 전환으로 생성 됩니다.  상태 시스템은 Unity의 애니메이터 창에서 볼 수 있습니다.

### <a name="state-visualizer-and-unity-animation-system"></a>상태 시각화 도우미 및 Unity 애니메이션 시스템

상태 시각화 도우미는 현재 Unity 애니메이션 시스템을 활용 합니다. 

상태 시각화 도우미의 **새 애니메이션 클립 생성** 단추를 누르면 새 애니메이션 클립 자산이 대화형 요소의 상태 이름에 따라 생성 되 고 MixedRealityToolkit 폴더에 배치 됩니다. 각 상태 컨테이너의 애니메이션 클립 속성은 연결 된 애니메이션 클립으로 설정 됩니다.

![상태 시각화 요소의 애니메이션 클립](../images/interactive-element/StateVisualizer/AnimationClips.png)

애니메이션 클립 간의 부드러운 전환을 관리 하기 위해 [애니메이터 상태 컴퓨터](https://docs.unity3d.com/Manual/AnimationOverview.html) 도 생성 됩니다.  기본적으로 상태 시스템은 [모든](https://docs.unity3d.com/Manual/class-State.html) 상태를 사용 하 여 대화형 요소의 모든 상태 간 전환을 허용 합니다. 

[Animator에서 트리거되는 상태 시각화 도우미도](https://docs.unity3d.com/Manual/AnimationParameters.html) 각 상태에 대해 생성되며, 트리거 매개 변수는 상태 시각화 도우미에서 애니메이션을 트리거하는 데 사용됩니다.

![Unity 상태 시스템](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a>런타임 제한 사항 

상태 시각화 도우미는 검사기를 통해 개체에 추가해야 하며 스크립트를 통해 추가할 수 없습니다.  AnimatorStateMachine/AnimationController를 수정하는 속성은 앱을 빌드할 때 제거되는 편집기 네임스페이스( `UnityEditor.Animations` )에 포함됩니다.

## <a name="how-to-use-the-state-visualizer"></a>상태 시각화 도우미를 사용하는 방법

1. 큐브 만들기
1. 대화형 요소 연결
1. 연결 상태 시각화 도우미
1. **새 애니메이션 클립 생성 선택**

    ![새 애니메이션 클립 생성](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![시각화 도우미 및 대화형 요소 구성 요소에서 생성된 애니메이션 클립 표시](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. 포커스 상태 컨테이너에서 **대상 추가를** 선택합니다.

    ![상태 시각화 도우미 대상 추가](../images/interactive-element/StateVisualizer/AddTarget.png)

1. 현재 게임 개체를 대상 필드로 끌기 

    ![상태 시각화 도우미 대상 설정](../images/interactive-element/StateVisualizer/SetTarget.png)

1. 큐브 애니메이션 가능 속성 폴딩 열기
1. 애니메이션 가능 속성 드롭다운 메뉴를 선택하고 **색을** 선택합니다.

    ![상태 시각화 도우미 색 설정](../images/interactive-element/StateVisualizer/SetColor.png)

1. **색 애니메이션 가능 속성 추가를** 선택합니다.

    ![시각화 도우미 색 애니메이션 가능 속성 선택](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. 색 선택 

    ![색상환에서 시각화 도우미 색 선택](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. 재생을 누르고 전환 색 변경을 관찰 합니다.

    ![가상 손 상호 작용을 사용 하 여 색 변경 예제 전환](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a>애니메이션 효과 속성

애니메이션 효과 속성의 주요 목적은 애니메이션 클립 키 프레임 설정을 간소화 하는 것입니다.  사용자가 Unity 애니메이션 시스템에 친숙 하 고 생성 된 애니메이션 클립에서 키 프레임을 직접 설정 하는 것을 선호 하는 경우 애니메이션 효과 속성을 대상 개체에 추가 하 고 Unity의 애니메이션 창 (Windows > 애니메이션 > 애니메이션)에서 클립을 열 수 없습니다. 

애니메이션에 애니메이션 효과 속성을 사용 하는 경우 곡선 형식은 EaseInOut로 설정 됩니다.

**현재 애니메이션 효과 속성:**
- [크기 조정 오프셋](#scale-offset)
- [위치 오프셋](#position-offset)
- [색상](#color)
- [셰이더 색](#shader-color)
- [셰이더 Float](#shader-float)
- [셰이더 벡터](#shader-vector)

### <a name="scale-offset"></a>크기 조정 오프셋

눈금 오프셋 애니메이션 효과 속성은 개체의 현재 소수 자릿수를 사용 하 여 정의 된 오프셋을 추가 합니다.

![가상 손 상호 작용을 사용 하는 크기 조정 오프셋](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a>위치 오프셋

Position Offset 애니메이션 효과 속성은 개체의 현재 위치를 사용 하 여 정의 된 오프셋을 추가 합니다.

![가상 손 상호 작용을 사용 하는 위치 오프셋](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a>색

색 애니메이션 효과 속성은 재질에 기본 색 속성이 있는 경우 재질의 기본 색을 나타냅니다. 이 속성은 속성에 애니메이션을 적용 `material._Color` 합니다.

![가상 손 상호 작용으로 색 변경 포커스](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a>셰이더 색

셰이더 색 애니메이션 효과 속성은 Color 형식의 셰이더 속성을 참조 합니다. 모든 셰이더 속성에는 속성 이름이 필요 합니다. 아래 gif는 주 재질 색이 아닌 Fill_Color 라는 셰이더 색 속성에 애니메이션을 적용 하는 방법을 보여 줍니다.  재질 검사기에서 값을 변경 합니다.

![가상 손을 상호 작용 하는 음영 색](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a>셰이더 Float

Shader Float 애니메이션 효과 속성은 Float 형식의 셰이더 속성을 참조 합니다. 모든 셰이더 속성에는 속성 이름이 필요 합니다. 아래 gif에서 금속성 속성에 대 한 재질 검사기의 변경 값을 확인 합니다. 

![가상 손을 상호 작용 하는 셰이더 float](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a>셰이더 벡터

셰이더 Vector 애니메이션 효과 속성은 System.numerics.vector3 및 system.numerics.vector4 형식의 셰이더 속성을 참조 합니다. 모든 셰이더 속성에는 속성 이름이 필요 합니다. 아래 gif에서 바둑판식 배열 (Main Tex_ST) 속성에 대 한 재질 검사기의 변경 값을 확인 합니다. 

![가상 손 상호 작용이 있는 셰이더 벡터](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a>애니메이션 효과 셰이더 속성 이름을 찾는 방법

1. 창 > 애니메이션 > 애니메이션으로 이동합니다.
1. 상태 시각화 도우미가 있는 개체가 계층 구조에서 선택되어 있는지 확인합니다.
1. 애니메이션 창에서 애니메이션 클립 선택
1. **속성 추가를** 선택하고 Mesh 렌더러 폴딩을 엽니다. 

    ![Animator 창에 애니메이션 속성 추가](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. 이 목록에는 모든 Animatable 속성 이름의 이름이 포함됩니다. 

    ![Animator 창의 메시 렌더러 애니메이션 속성](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a>참고 항목

- [**단추**](../ux-building-blocks/button.md)
- [**범위 제어**](../ux-building-blocks/bounds-control.md)
- [**Grid 개체 컬렉션**](../ux-building-blocks/object-collection.md)
- [**RadialView Solver**](../ux-building-blocks/solvers/solver.md)
