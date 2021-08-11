---
title: 대화형 요소
description: InteractiveElement MRTK 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Interactive 요소, Interactable
ms.openlocfilehash: 6d8f36c4780844e991eb32943645402503fab8340c6843dbb607f1c11033d912
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220605"
---
# <a name="interactive-element-experimental"></a>Interactive 요소 [실험적]

MRTK 입력 시스템에 대한 간소화된 중앙 집중식 진입점입니다. 핵심 상호 작용 상태에 대한 상태 관리 메서드, 이벤트 관리 및 상태 설정 논리를 포함합니다.

Interactive Element는 Unity 2019.3에 새로 추가된 기능인 [Serialize Reference를](https://docs.unity3d.com/ScriptReference/SerializeReference.html)활용하기 때문에 Unity 2019.3 이상에서 지원되는 실험적 기능입니다.

### <a name="interactive-element-inspector"></a>Interactive 요소 검사기

재생 모드 중에 Interactive 요소 검사기는 현재 상태가 활성 상태인지 여부를 나타내는 시각적 피드백을 제공합니다. 상태가 활성 상태이면 진한색으로 강조 표시됩니다.  상태가 활성 상태가 아닌 경우 색이 변경되지 않습니다. 검사기에서 상태 옆에 있는 숫자는 상태 값입니다. 상태가 활성 상태이면 값은 1이고, 상태가 활성 상태가 아닌 경우 값은 0입니다.

![가상 손 상호 작용이 있는 대화형 요소](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a>핵심 상태

Interactive 요소는 핵심 상태를 포함하며 [사용자 지정 상태](#custom-states)추가를 지원합니다.  핵심 상태는 에 정의된 상태 설정 논리가 이미 있는 `BaseInteractiveElement` 상태입니다. 다음은 현재 입력 기반 코어 상태의 목록입니다. 

### <a name="current-core-states"></a>현재 핵심 상태

- [기본값](#default-state) 

근 및 원거리 상호 작용 핵심 상태:
- [포커스](#focus-state) 

근 상호 작용 핵심 상태:

- [포커스 가까이](#focus-near-state)
- [터치](#touch-state)

원거리 상호 작용 핵심 상태:
- [멀리 포커스](#focus-far-state)
- [멀리 선택](#select-far-state)

기타 핵심 상태:
- [클릭됨](#clicked-state)
- [켜기 및 토글 끄기](#toggle-on-and-toggle-off-state)
- [음성 키워드](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a>검사기를 통해 코어 상태를 추가하는 방법

1. Interactive 요소에 대한 검사기에서 **코어 상태 추가로** 이동합니다.

    ![검사기에서 핵심 상태 추가](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. 상태 **선택** 단추를 선택하여 추가할 코어 상태를 선택합니다. 메뉴의 상태는 상호 작용 유형별로 정렬됩니다.

    ![상태가 선택된 검사기 를 통해 코어 상태 추가](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. 이벤트 구성 폴딩을 열어 상태와 연결된 이벤트 및 속성을 확인합니다.

    ![이벤트 구성을 통해 검사기 통해 코어 상태 추가](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a>스크립트를 통해 코어 상태를 추가하는 방법

메서드를 사용하여 `AddNewState(stateName)` 코어 상태를 추가합니다. 사용 가능한 코어 상태 이름 목록은 `CoreInteractionState` 열거형을 사용합니다.

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a>상태 내부 구조 

Interactive 요소의 상태는 `InteractionState` 형식입니다.  `InteractionState`에는 다음 속성이 포함됩니다.

- **이름:** 상태의 이름입니다.
- **값:** 상태 값입니다.  상태가 켜진 경우 상태 값은 1입니다. 상태가 꺼져 있으면 상태 값은 0입니다.
- **활성:** 상태가 현재 활성 상태인지 여부입니다. 활성 속성의 값은 상태가 켜진 경우 true이고, 상태가 해제되어 있으면 false입니다. 
- **상호 작용 형식:** 상태의 상호 작용 형식은 상태가 의도된 상호 작용 유형입니다. 
  - `None`: 어떤 형식의 입력 상호 작용도 지원하지 않습니다.
  - `Near`: 근접 상호 작용 지원. 입력은 굴절된 손이 다른 게임 개체와 직접 연결되는 경우( 즉, 굴절된 손의 위치가 세계 공간에서 게임 개체의 위치와 가까운 경우) 근거리 상호 작용으로 간주됩니다.
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

상태의 이벤트 구성을 얻는 것은 상태 자체에 따라 다릅니다. 각 코어 상태에는 각 코어 상태를 설명하는 섹션 아래에 설명된 특정 이벤트 구성 유형이 있습니다.

다음은 상태의 이벤트 구성을 얻는 일반화된 예제입니다.

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a>기본 상태

기본 상태는 항상 대화형 요소에 있습니다.  이 상태는 다른 모든 상태가 활성 상태가 아닌 경우에만 활성화됩니다.  다른 상태가 활성화되면 기본 상태가 내부적으로 off로 설정됩니다. 

대화형 요소는 상태 목록에 있는 기본 및 포커스 상태로 초기화됩니다. 기본 상태는 항상 상태 목록에 있어야 합니다. 

#### <a name="getting-default-state-events"></a>기본 상태 이벤트 받기

기본 상태에 대한 이벤트 구성 유형: `StateEvents`

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

포커스 상태는 가리키기와 동일한 혼합 현실로 간주될 수 있는 근사하고 먼 상호 작용 상태입니다. 포커스 상태에 대한 근사 상호 작용과 원거리 상호 작용 간의 구분 요소는 현재 활성 포인터 형식입니다.  Focus 상태의 포인터 형식이 Pointer Pointer이면 상호 작용이 가까운 상호 작용으로 간주됩니다.  기본 포인터가 Pointer 포인터가 아닌 경우 상호 작용은 원거리 상호 작용으로 간주됩니다. Focus 상태는 기본적으로 Interactive Element에 있습니다.

**포커스 상태 동작** 
 ![ 가상 손 상호 작용을 통해 포커스 상태](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif) 

**포커스 상태 검사기** 
 ![ Inpsector의 포커스 상태](../images/interactive-element/InEditor/FocusStateInspector.png)

#### <a name="getting-focus-state-events&quot;></a>포커스 상태 이벤트 받기

포커스 상태에 대한 이벤트 구성 유형: `FocusEvents`

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

#### <a name="focus-near-vs-focus-far-behavior"></a>포커스 가까이 및 포커스 원거리 동작 

![가상 손 상호 작용을 통해 가까운 정도의 포커스](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a>포커스 근 상태

Focus Near 상태는 포커스 이벤트가 발생할 때 설정되고 기본 포인터는 근사 상호 작용을 나타내는 은(는) Pointer 포인터입니다. 

**상태 근처 포커스 동작** 
 ![ 가상 손 상호 작용을 통해 상태 가까이에 포커스](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif) 

**포커스 근 상태 검사기** 
 ![ 검사기에서 구성 요소 근처에 포커스](../images/interactive-element/InEditor/FocusNearStateInspector.png)

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
 ![ 가상 손 상호 작용을 통해 멀리 떨어진 포커스 상태](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)

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

터치 상태는 근접 하 게 개체를 직접 접촉 하는 경우에 설정 되는 근접 한 상호 작용 상태입니다.  직접 터치는 트레일러의 인덱스 손가락이 개체의 세계 위치와 매우 근접해 있음을 의미 합니다. `NearInteractionTouchableVolume`터치 상태가 상태 목록에 추가 되는 경우 기본적으로 구성 요소는 개체에 연결 됩니다.  `NearInteractionTouchableVolume` `NearInteractionTouchable` 터치 이벤트를 검색 하려면 또는 구성 요소가 있어야 합니다.  와의 차이점 `NearInteractionTouchableVolume` 은 `NearInteractionTouchable` `NearInteractionTouchableVolume` 개체의 collider을 기반으로 터치를 검색 하 고 `NearInteractionTouchable` 평면의 정의 된 영역 내에서 터치를 검색 한다는 것입니다.

**터치 상태 동작** 
 ![ 가상 손 상호 작용이 포함 된 터치 상태](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)

**터치 상태 검사기** 
 ![ 검사기의 Touch state 구성 요소](../images/interactive-element/InEditor/TouchStateInspector.png)

#### <a name="getting-touch-state-events&quot;></a>터치 상태 이벤트 가져오기

터치 상태의 이벤트 구성 유형입니다. `TouchEvents`

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

### <a name="select-far-state"></a>Far 상태 선택

Select Far 상태는 표시 되는 `IMixedRealityPointerHandler` 입니다.  이 상태는 멀리 떨어져 있는 클릭 (공중 탭)을 검색 하 고 기본 컨트롤러 광선 포인터 또는 GGV 포인터와 같은 원거리 상호 작용 포인터를 사용 하 여 유지 하는 원거리 상호 작용 상태입니다.  Select Far 상태에는 이벤트 구성 foldout 이라는 옵션이 `Global` 있습니다. `Global`이 true 이면가 `IMixedRealityPointerHandler` 전역 입력 처리기로 등록 됩니다.  처리기가 global로 등록 된 경우에는 개체에 포커스를 두고 입력 시스템 이벤트를 트리거할 필요가 없습니다.  예를 들어, 사용자가 포커스에 있는 개체에 관계 없이 공중 탭/선택 제스처를 수행 해야 하는 경우를 `Global` true로 설정 합니다. 

**Far 상태 동작 선택** 
 ![ 가상 핸드 상호 작용을 사용 하 여 지금 선택](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)

**Far 상태 검사기 선택** 
 ![ 검사기에서 far 구성 요소 선택](../images/interactive-element/InEditor/SelectFarStateInspector.png)

#### <a name="getting-select-far-state-events&quot;></a>선택 Far 상태 이벤트 가져오기

SelectFar 상태의 이벤트 구성 유형입니다. `SelectFarEvents`

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

### <a name="clicked-state"></a>클릭 한 상태

클릭 된 상태는 멀리 떨어져 있는 클릭 (Far 상태 선택)에 의해 트리거됩니다.  이 상태는 내부적으로 on으로 전환 되 고, OnClicked 이벤트를 호출 하 고, 즉시 off로 전환 됩니다. 

> [!NOTE]
> 상태 작업을 기반으로 하는 검사기의 시각적 피드백은 전환 된 후 즉시 해제 되기 때문에 클릭 된 상태에 대해 존재 하지 않습니다. 

**클릭 상태 동작** 
 ![ 가상 손 상호 작용을 사용 하 여 클릭 한 상태](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)

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
ToggleOff 상태에 대 한 이벤트 구성 유형입니다. `ToggleOffEvents`

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

### <a name="speech-keyword-state"></a>Speech 키워드 상태

Speech 키워드 상태는 Mixed Reality Speech 프로필에 정의 된 키워드를 수신 대기 합니다. 새 키워드는 런타임 이전에 음성 명령 프로필에 등록 되어야 합니다 (아래 단계 참조). 

**Speech 키워드 상태 동작** 
 ![ 가상 상호 작용이 있는 Speech 키워드](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)

**Speech 키워드 상태 검사기** 
 ![ 검사기의 Speech 키워드 구성 요소](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)

> [!NOTE]
> 위의 gif에서 F5 키를 눌러 편집기에서 Speech 키워드 상태를 트리거 했습니다. 편집기에서 음성에 대 한 테스트를 설정 하는 단계는 아래에 설명 되어 있습니다. 

#### <a name="how-to-register-a-speech-commandkeyword"></a>음성 명령/키워드를 등록 하는 방법

1. **MixedRealityToolkit** game 개체를 선택 합니다.

1. 현재 프로필 **복사 및 사용자 지정을** 선택 합니다.

1. 입력 섹션으로 이동 하 고 **복제** 를 선택 하 여 입력 프로필을 수정할 수 있도록 합니다.

1. 입력 프로필에서 음성 섹션으로 스크롤하고 음성 프로필을 복제 합니다.

    ![MRTK game 개체의 Speech 키워드 프로필](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. 새 음성 명령 추가를 선택 합니다.

    ![MRTK 프로필에 새 speech 키워드 추가](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. New 키워드를 입력 합니다. 선택 사항: 편집기에서 테스트를 허용 하도록 KeyCode을 F5 또는 다른 KeyCode로 변경 합니다. 

    ![MRTK 프로필에서 speech 키워드 구성](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. 대화형 요소 음성 키워드 상태 검사기로 돌아가서 **키워드 추가** 를 선택 합니다. 

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
    
    ![대화형 요소 구성 요소에 표시 되는 새 상태](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


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

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a>사용자 지정 이벤트 구성을 사용 하 여 사용자 지정 상태 만들기 

**키보드** 라는 사용자 지정 상태에 대 한 예제 파일은 다음 위치에 있습니다. MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample

다음 단계에서는 사용자 지정 상태 이벤트 구성 및 수신자 파일을 만드는 기존 예제를 안내 합니다.

1. 상태 이름을 생각 합니다.  이 이름은 고유 해야 하며 기존 코어 상태와 같을 수 없습니다. 이 예제에서는 상태 이름이 **키보드** 로 이동 합니다.

1. 상태 이름 + "수신자"와 상태 이름 + "이벤트" 라는 두 개의 .cs 파일을 만듭니다. 이러한 파일의 이름은 내부적으로 고려 되며 상태 이름 + 이벤트/수신자 규칙을 따라야 합니다. 

    ![키보드 상태 스크립트](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. 파일 내용에 대 한 자세한 내용은 KeyboardEvents 및 KeyboardReceiver 파일을 참조 하세요. 새 이벤트 구성 클래스는에서 상속 해야 `BaseInteractionEventConfiguration` 하며, 새 이벤트 수신기 클래스는에서 상속 해야 합니다 `BaseEventReceiver` .  키보드 상태에 대 한 상태 설정 예제는 파일에 있습니다 `CustomStateSettingExample.cs` . 

1. 상태 이름을 사용하여 대화형 요소에 상태를 추가합니다. 이벤트 구성 및 이벤트 수신기 파일이 있는 경우 상태 이름이 인식됩니다.  사용자 지정 이벤트 구성 파일의 속성은 검사기에서 나타나야 합니다.

    ![대화형 요소에 사용자 지정 상태 추가 ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ 대화형 요소에서 인식되는 사용자 지정 상태](../images/interactive-element/InEditor/SetKeyboardStateName.png)


1. 이벤트 구성 및 이벤트 수신기 파일의 더 많은 예제는 다음 경로의 파일을 참조하세요.    
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers

## <a name="example-scene"></a>예제 장면 

Interactive Element + State 시각화 도우미에 대한 예제 장면의 위치는 MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity입니다.

![대화형 요소 및 상태 시각화 도우미가 있는 예제 장면](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a>압축 가능 단추

예제 장면에는 및 라는 프리팹이 포함되어 `CompressableButton` `CompressableButtonToggle` 있으며, 이러한 `PressableButtonHoloLens2` 프리팹은 대화형 요소 및 상태 시각화 도우미를 사용하여 구성된 단추의 동작을 미러합니다. 구성 요소는 현재 와 `CompressableButton` 를 `PressableButton`  +  `PressableButtonHoloLens2` 기본 `BaseInteractiveElement` 클래스로 조합한 것입니다. 

## <a name="state-visualizer-experimental"></a>상태 시각화 도우미 [실험적]

상태 시각화 도우미 구성 요소는 연결된 Interactive Element 구성 요소에 정의된 상태에 따라 개체에 애니메이션을 추가합니다. 이 구성 요소는 애니메이션 자산을 만들고 MixedRealityToolkit.Generated 폴더에 배치하며, 애니메이션 가능 속성을 대상 게임 개체에 추가하여 간소화된 애니메이션 키 프레임 설정을 사용하도록 설정합니다. 상태 간에 애니메이션 전환을 사용하도록 설정하기 위해 Animator 컨트롤러 자산이 생성되고 연결된 매개 변수 및 상태 전환을 사용하여 기본 상태 머신이 생성됩니다.  상태 시스템은 Unity의 Animator 창에서 볼 수 있습니다.

### <a name="state-visualizer-and-unity-animation-system"></a>상태 시각화 도우미 및 Unity 애니메이션 시스템

상태 시각화 도우미는 현재 Unity 애니메이션 시스템을 활용합니다. 

상태 시각화 도우미에서 **새 애니메이션 클립 생성** 단추를 누르면 대화형 요소의 상태 이름에 따라 새 애니메이션 클립 자산이 생성되고 MixedRealityToolkit.Generated 폴더에 배치됩니다. 각 상태 컨테이너의 애니메이션 클립 속성은 연결된 애니메이션 클립으로 설정됩니다.

![상태 시각화 도우미 구성 요소의 애니메이션 클립](../images/interactive-element/StateVisualizer/AnimationClips.png)

애니메이션 클립 간의 원활한 전환을 관리하기 위해 [Animator State Machine도](https://docs.unity3d.com/Manual/AnimationOverview.html) 생성됩니다.  기본적으로 상태 시스템은 [Any State를](https://docs.unity3d.com/Manual/class-State.html) 활용하여 Interactive Element의 모든 상태 간 전환을 허용합니다. 

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

    ![색 휠에서 시각화 도우미 색 선택](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. 재생을 누르고 전환 색 변경 관찰

    ![가상 손 상호 작용을 통해 전환 색 변경 예제](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a>애니메이션 가능 속성

애니메이션 가능 속성의 주요 목적은 애니메이션 클립 키 프레임 설정을 간소화하는 것입니다.  사용자가 Unity 애니메이션 시스템에 익숙하고 생성된 애니메이션 클립에서 키 프레임을 직접 설정하려는 경우 대상 개체에 애니메이션 가능 속성을 추가하고 Unity의 애니메이션 창에서 클립을 열 수 없습니다(애니메이션 > 애니메이션 Windows >). 

애니메이션에 애니메이션 가능 속성을 사용하는 경우 곡선 형식은 EaseInOut으로 설정됩니다.

**현재 애니메이션 가능 속성:**
- [배율 오프셋](#scale-offset)
- [위치 오프셋](#position-offset)
- [색상](#color)
- [셰이더 색](#shader-color)
- [셰이더 Float](#shader-float)
- [셰이더 벡터](#shader-vector)

### <a name="scale-offset"></a>배율 오프셋

Scale Offset Animatable 속성은 개체의 현재 배율과 정의된 오프셋을 추가합니다.

![가상 손 조작을 통해 오프셋 크기 조정](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a>위치 오프셋

위치 오프셋 애니메이션 가능 속성은 개체의 현재 위치를 가져와서 정의된 오프셋을 추가합니다.

![가상 손 상호 작용을 통해 위치 오프셋](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a>색

색 애니메이션 가능 속성은 재질에 주 색 속성이 있는 경우 재질의 주 색을 나타냅니다. 이 속성 애니메이션을 `material._Color` 속성입니다.

![가상 손 조작을 통해 포커스 색 변경](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a>셰이더 색

셰이더 색 애니메이션 가능 속성은 색 형식의 셰이더 속성을 나타냅니다. 모든 셰이더 속성에는 속성 이름이 필요합니다. 아래 gif는 주 재질 색이 아닌 Fill_Color 라는 셰이더 색 속성에 애니메이션을 적용하는 것을 보여줍니다.  재질 검사기에서 변경되는 값을 관찰합니다.

![가상 손 조작을 통해 음영 색](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a>셰이더 Float

셰이더 Float Animatable 속성은 float 형식의 셰이더 속성을 참조합니다. 모든 셰이더 속성에는 속성 이름이 필요합니다. 아래 gif에서 Material Inspector의 값 변경 내용을 확인합니다. 

![가상 손 상호 작용을 통해 셰이더 float](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a>셰이더 벡터

셰이더 벡터 애니메이션 가능 속성은 Vector4 형식의 셰이더 속성을 참조합니다. 모든 셰이더 속성에는 속성 이름이 필요합니다. 아래 gif에서 Tiling(Main Tex_ST) 속성에 대한 재질 검사기에서 변경되는 값을 확인합니다. 

![가상 손 상호 작용이 있는 셰이더 벡터](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a>애니메이션 가능한 셰이더 속성 이름을 찾는 방법

1. 창 > 애니메이션 > 애니메이션으로 이동합니다.
1. 상태 시각화 도우미가 있는 개체가 계층 구조에서 선택되어 있는지 확인합니다.
1. 애니메이션 창에서 애니메이션 클립 선택
1. **속성 추가를** 선택하고 Mesh 렌더러 폴딩을 엽니다. 

    ![Animator 창에 애니메이션 속성 추가](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. 이 목록에는 모든 Animatable 속성 이름의 이름이 포함됩니다. 

    ![Animator 창의 메시 렌더러 애니메이션 속성](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a>추가 정보

- [**단추**](../ux-building-blocks/button.md)
- [**경계 컨트롤**](../ux-building-blocks/bounds-control.md)
- [**Grid 개체 컬렉션**](../ux-building-blocks/object-collection.md)
- [**RadialView Solver**](../ux-building-blocks/solvers/solver.md)
