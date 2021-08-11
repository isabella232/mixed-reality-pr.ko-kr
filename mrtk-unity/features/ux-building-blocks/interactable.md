---
title: 상호 작용 가능
description: MRTK의 상호 작용 가능한 스크립트 구성 요소에 대한 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Interactable, 이벤트,
ms.openlocfilehash: a0aee99d01ae59a8ebedc4d62a4b0aaf844a7afaa6961bbfd05238dd9d5b673d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206813"
---
# <a name="interactable"></a>상호 작용 가능

![상호 작용 가능](../images/interactable/InteractableExamples.png)

[`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable)구성 요소는 모든 개체를 입력에 쉽게 상호 *작용하고* 응답할 수 있도록 하는 올인원 컨테이너입니다. 상호 작용 가능은 터치, 손 광선, 음성 등을 비롯한 모든 유형의 입력에 대한 catch-all 역할을 하며 이러한 상호 작용을 [이벤트](#events) 및 [시각적 테마](visual-themes.md) 응답으로 유입합니다. 이 구성 요소는 단추를 만들고, 포커스가 있는 개체의 색을 변경하는 등의 쉬운 방법을 제공합니다.

## <a name="how-to-configure-interactable"></a>Interactable을 구성하는 방법

구성 요소는 구성의 세 가지 기본 섹션을 허용합니다.

1) [일반 입력 구성](#general-input-settings)
1) 여러 GameObject를 대상으로 하는 [시각적 테마](visual-themes.md)
1) [이벤트 처리기](#events)

### <a name="general-input-settings"></a>일반 입력 설정

![상호 작용 가능한 일반 설정](../images/interactable/InputFeatures_short.png)

**상태**

*상태는* 상호 작용 가능한 프로필 및 [시각적 테마](visual-themes.md)에 대한 상호 작용 단계(예: press 또는 observed)를 정의하는 [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 매개 변수입니다. [](#interactable-profiles)

DefaultInteractableStates(Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset)는 기본적으로 MRTK와 함께 제공되며 *상호 작용 가능한* 구성 요소의 기본 매개 변수입니다. 

![검사기에서 ScriptableObject 예제 상태](../images/interactable/DefaultInteractableStates.png)

*DefaultInteractableStates* 자산은 네 가지 상태를 포함하며 [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) 상태 모델 구현을 활용합니다.

* **기본값:** 아무 것도 발생하지 않습니다. 가장 격리된 기본 상태입니다.

* **포커스:** 개체가 가리키고 있습니다. 이 상태는 단일 상태이며 다른 상태는 현재 설정되지 않지만 기본 순위에서 제외됩니다.

* **누르기:** 개체가 가리키고 있고 단추 또는 손을 누르고 있습니다. Press state out은 Default 및 Focus의 순위를 지정합니다. 이 상태는 Physical Press로 대체(fallback)로 설정됩니다.

* **사용 안 함:** 단추는 대화형이 아니어야 하며 시각적 피드백은 어떤 이유로 이 단추를 현재 사용할 수 없는 경우 사용자에게 알릴 수 있습니다. 이론적으로 비활성 상태는 다른 모든 상태를 포함할 수 있지만 사용이 해제된 경우 사용 안 함 상태는 다른 모든 상태를 비활성 상태로 전환합니다.

비트 값(#)은 목록의 순서에 따라 상태에 할당됩니다.

> [!NOTE]
> 일반적으로 *상호 작용* 가능한 구성 요소를 만들 때 DefaultInteractableStates(Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset)를 활용하는 것이 좋습니다. 
>
> 그러나 테마를 구동하는 데 사용할 수 있는 17개의 상호 작용 가능한 상태는 있지만 일부는 다른 구성 요소에 의해 구동됩니다. 다음은 기본 제공 기능이 있는 목록입니다.
>
> * 방문: Interactable을 클릭했습니다.
> * 토글: 단추가 토글된 상태이거나 차원 인덱스가 홀수입니다.
> * 제스처: 손 또는 컨트롤러를 눌렀고 원래 위치에서 이동했습니다.
> * VoiceCommand: Interactable을 트리거하는 데 음성 명령이 사용되었습니다.
> * PhysicalTouch: 터치 입력이 현재 검색되어 를 사용하여 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 사용하도록 설정합니다.
> * 잡기: 손은 현재 개체의 범위에서 잡고 있으며 를 사용하여 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 사용하도록 설정합니다.

**사용**

Interactable을 사용할지 여부를 전환합니다. 이는 [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 코드의 에 해당합니다.

*Interactable의* enabled 속성은 GameObject/Component를 통해 구성된 enabled 속성(즉, SetActive 등). GameObject 또는 *Interactable* MonoBehaviour를 사용하지 않도록 설정하면 클래스의 모든 것이 입력, 시각적 테마, 이벤트 등을 포함하여 실행하지 않도록 설정됩니다. 을 통해 사용하지 [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 않도록 설정하면 대부분의 입력 처리가 비활성화되고 관련 입력 상태가 다시 설정됩니다. 그러나 클래스는 여전히 모든 프레임을 실행하고 무시되는 입력 이벤트를 수신합니다. 이는 시각적 테마를 통해 수행할 수 있는 Interactable을 비활성 상태로 표시하는 데 유용합니다. 일반적인 예로 필요한 모든 입력 필드가 완료될 때까지 기다리는 제출 단추가 있습니다.

**입력 작업**

*대화형* 구성 요소가 반응해야 하는 입력 구성 또는 컨트롤러 매핑 프로필에서 [입력 작업을](../input/input-actions.md) 선택합니다.

이 속성은 를 통해 코드에서 런타임에 구성할 수 [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) 있습니다.

**IsGlobal**

true이면 선택한 [입력 동작](../input/input-actions.md)에 대한 전역 입력 수신기로 구성 요소를 표시합니다. 기본 동작은 이 *Interactable* collider/GameObject로만 입력을 제한하는 false입니다.

이 속성은 를 통해 코드에서 런타임에 구성할 수 [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) 있습니다.

**음성 명령**

[음성 명령](../input/speech.md), MRTK 음성 명령 프로필에서 음성 상호 작용에 대 한 OnClick 이벤트를 트리거 합니다.

이 속성은 를 통해 코드에서 런타임에 구성할 수 [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) 있습니다.

**포커스 필요**

true이면 음성 명령은 포인터에서 포커스가 이미 있는 경우에만 *Interactable을* 활성화합니다. false이면 *Interactable이* 선택한 음성 명령에 대한 전역 수신기로 작동합니다. 여러 글로벌 음성 수신기가 장면에서 구성하기 어려울 수 있기 때문에 기본 동작은 true입니다.

이 속성은 를 통해 코드에서 런타임에 구성할 수 [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) 있습니다.

**선택 모드**

이 속성은 선택 논리를 정의합니다. *Interactable을* 클릭하면 다음 *차원* 수준으로 반복됩니다. *차원은* 순위와 유사하며 입력 외부의 상태(즉, 포커스, 누르기 등). 단추와 연결된 토글 상태 또는 기타 다중 순위 상태를 정의하는 데 유용합니다. 현재 차원 수준은 에 의해 `Interactable.DimensionIndex` 추적됩니다.

사용 가능한 선택 모드는 다음과 같습니다.

* **단추**  -  *차원* = 1, 간단하게 클릭할 수 *있는 Interactable*
* **토글**  -  *차원* = 2, *on* off 상태 간의 *상호 작용 가능한* 대체 / 
* **다차원**  -  *차원 >* = 3입니다. 클릭할 때마다 현재 차원 수준 + 1이 증가합니다. 목록 등에 단추 상태를 정의하는 데 유용합니다.

*상호 작용 가능을* 사용하면 *차원당* 여러 테마를 정의할 수도 있습니다. 예를 들어 *SelectionMode=Toggle인* 경우 *Interactable을* 선택 *취소하고* 구성 요소를 *선택할* 때 다른 테마를 적용할 수 있습니다.

현재 선택 모드는 를 통해 런타임에 쿼리할 수 [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) 있습니다. 런타임 시 모드 업데이트는 속성을 원하는 기능과 일치하도록 설정하여 달성할 수  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) 있습니다. 또한 *토글* 및 다차원 모드에 유용한 현재 *차원은* 를 통해 액세스할 수 [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) 있습니다.

### <a name="interactable-profiles"></a>상호 작용 가능한 프로필

*프로필은* GameObject와 [시각적 테마](visual-themes.md)간의 관계를 만드는 항목입니다. 프로필은 상태 변경이 발생할 때 테마에서 조작할 콘텐츠를 [정의합니다.](#general-input-settings)

테마는 재질과 매우 유사하게 작동합니다. 현재 상태에 따라 개체에 할당될 속성 목록을 포함하는 스크립팅 가능한 개체입니다. 테마도 다시 사용할 수 있으며 여러 상호 *작용 가능한* UX 개체에 할당할 수 있습니다.

**삭제할 때 다시 설정**

시각적 테마는 선택한 테마 엔진의 클래스 및 형식에 따라 대상 GameObject의 다양한 속성을 수정합니다. Interactable 구성 요소가 제거될 때 *Reset On Destroy가* true이면 구성 요소는 활성 테마에서 원래 값으로 수정된 모든 속성을 다시 설정합니다. 그렇지 않으면 제거될 때 Interactable 구성 요소는 수정된 속성을 그대로 둡니다. 이 후자의 경우 다른 외부 구성 요소에 의해 변경되지 않는 한 값의 마지막 상태가 유지됩니다. 기본값은 false입니다.

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a>이벤트

모든 *Interactable* 구성 요소에는 구성 요소를 선택하기만 하면 발생되는 *OnClick* 이벤트가 있습니다. 그러나 *Interactable은* *OnClick* 이외의 입력 이벤트를 검색하는 데 사용할 수 있습니다.

이벤트 *추가* 단추를 클릭하여 새 유형의 이벤트 수신기 정의를 추가합니다. 추가되면 원하는 이벤트 유형을 선택합니다.

![이벤트 예제](../images/interactable/Events.png))

다양한 유형의 입력에 응답하는 다양한 유형의 이벤트 수신기가 있습니다. MRTK는 다음과 같은 수신기 세트와 함께 제공합니다.

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

를 확장하는 새 클래스를 만들어 사용자 지정 수신기를 만들 수 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 있습니다.

![이벤트 설정/해제 예](../images/interactable/Event_toggle.png)

*설정/해제 이벤트 수신기의 예*

### <a name="interactable-receivers"></a>Interactable 수신기

 [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver)구성 요소는 원본 *Interactable* 구성 요소 외부에서 이벤트를 정의할 수 있도록 허용 합니다. *InteractableReceiver* 는 다른 *Interactable* 에서 발생 한 필터링 된 이벤트 유형을 수신 대기 합니다. *Interactable* 속성이 직접 할당 되지 않은 경우 *검색 범위* 속성은 *InteractableReceiver* 가 자체, 부모 또는 자식 GameObject 이벤트를 수신 대기 하는 방향을 정의 합니다.

[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) 비슷한 방식으로 작동 하지만 일치 하는 이벤트 목록에 대 한 것입니다.

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a>사용자 지정 이벤트 만들기

[시각적 테마](visual-themes.md#custom-theme-engines)와 마찬가지로 이벤트를 확장 하 여 상태 패턴을 검색 하거나 기능을 노출할 수 있습니다.

사용자 지정 이벤트는 다음과 같은 두 가지 주요 방법으로 만들 수 있습니다.

1) 클래스를 확장 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 하 여 이벤트 유형 드롭다운 목록에 표시 되는 사용자 지정 이벤트를 만듭니다. Unity 이벤트는 기본적으로 제공 되지만 추가 Unity 이벤트를 추가 하거나 Unity 이벤트를 숨기도록 이벤트를 설정할 수 있습니다. 이 기능을 사용 하면 디자이너가 프로젝트의 엔지니어와 함께 작업 하 여 디자이너가 편집기에서 설정할 수 있는 사용자 지정 이벤트를 만들 수 있습니다.

1) 클래스를 확장 [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) 하 여 *Interactable* 또는 다른 개체에 상주할 수 있는 완전히 사용자 지정 이벤트 구성 요소를 만듭니다. 에서는 [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) *Interactable* 를 참조 하 여 상태 변경을 검색 합니다.

#### <a name="example-of-extending-receiverbase"></a>확장 예제 `ReceiverBase`

[`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI)클래스는 *Interactable* 에 대 한 상태 정보를 표시 하 고 사용자 지정 이벤트 수신기를 만드는 방법의 예입니다.

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

다음 메서드는 사용자 지정 이벤트 수신기를 만들 때 재정의/구현 하는 데 유용 합니다. [`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 는 상태 패턴/전환을 검색 하는 데 사용할 수 있는 추상 메서드입니다. 또한 [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 및 메서드는 [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) *Interactable* 가 선택 된 경우 사용자 지정 이벤트 논리를 만드는 데 유용 합니다.

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

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a>검사기에 사용자 지정 이벤트 수신기 필드 표시

*ReceiverBase* 스크립트 [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) 는 특성을 사용 하 여 검사기에서 사용자 지정 속성을 노출 합니다. 다음은 도구 설명 및 레이블 정보가 있는 사용자 지정 속성인 Vector3의 예입니다. *Interactable* GameObject를 선택 하 고 연결 된 *이벤트 수신기* 유형을 추가한 경우이 속성은 검사기에서 구성할 수 있는 것으로 표시 됩니다.

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a>Interactable 사용 방법

### <a name="building-a-simple-button"></a>간단한 단추 작성

입력 이벤트를 수신 하도록 구성 된 GameObject에 *Interactable* 구성 요소를 추가 하 여 간단한 단추를 만들 수 있습니다. 이 클래스에는 collider가 있거나 입력을 받기 위해 자식에 있을 수 있습니다. Unity UI 기반 Gameobject에서 *Interactable* 를 사용 하는 경우 캔버스 GameObject 아래에 있어야 합니다.

새 프로필을 만들고 GameObject 자체를 할당 하 고 새 테마를 만들어 단추를 한 단계 더 수행 합니다. 또한 *OnClick* 이벤트를 사용 하 여 작업을 수행 합니다.

> [!NOTE]
> [단추 pressable](button.md) 를 설정 하려면 [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 구성 요소가 필요 합니다. 또한 [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) *Interactable* 구성 요소에 이벤트를 누르기 위해 구성 요소가 필요 합니다.

### <a name="creating-toggle-and-multi-dimension-buttons"></a>설정/해제 및 다중 차원 단추 만들기

#### <a name="toggle-button"></a>토글 단추

단추를 사용 하지 않도록 설정 하려면 [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) 필드를 형식으로 변경 `Toggle` 합니다. *프로필* 섹션에는 *Interactable* 가 설정 되어 있을 때 사용 되는 각 프로필에 대 한 새 전환 된 테마가 추가 됩니다.

[`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes)가 Toggle로 설정 된 동안에는 *IsToggled* 확인란을 사용 하 여 런타임 초기화 시 컨트롤의 기본값을 설정할 수 있습니다.

*Canselect* 를 사용 하면 *Interactable* 가 *off* 로 *설정* 된 상태로 전환 되 고 *canselect* 는 역함수를 의미 합니다.

![프로필 설정/해제 시각적 테마 예제](../images/interactable/Profile_toggle.png)

개발자는 [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 및 인터페이스를 활용 [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 하 여 코드를 통해 *Interactable* 의 설정/해제 상태를 가져오거나 설정할 수 있습니다.

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a>단추 컬렉션 설정/해제

일반적으로는 지정 된 시간 (방사형 집합 또는 라디오 단추)이 라고도 하는 토글 단추 목록이 있습니다.

[`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection)구성 요소를 사용 하 여이 기능을 사용 하도록 설정 합니다. 이 컨트롤은 지정 된 시간에 하나의 *Interactable* 설정 되어 있는지 확인 합니다. *RadialSet* (asset/MRTK/SDK/FEATURES/UX/Interactable/Prefabs/RadialSet)도 기본 제공 되는 좋은 출발점입니다.

사용자 지정 방사형 단추 그룹을 만들려면 다음을 수행 합니다.

1) 여러 *Interactable* gameobject/단추 만들기
1) 각 *Interactable* 를 *SelectionMode* = Toggle, Canselect = true 및 *canselect* = false로 설정 합니다. 
1) 모든 상호 작용을 통해 빈 부모 GameObject *을 만들고* *InteractableToggleCollection* 구성 요소를 추가 합니다.
1) *InteractableToggleCollection* 의 *ToggleList* 에 모든 상호 작용을 *추가 합니다.*
1) *InteractableToggleCollection CurrentIndex* 속성을 설정 하 여 시작 시 기본적으로 선택 되는 단추를 결정 합니다.

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a>다차원 단추

다중 차원 선택 모드는 연속 단추를 만드는 데 사용 되거나 3 개 이상의 단계를 포함 하는 단추를 사용 하 여 속도를 제어 합니다. 예를 들어 고속 (1x), 고속 (2x) 또는 가장 빠름 (3:3)

차원을 숫자 값으로 사용 하는 경우 각 단계에 다른 테마를 사용 하 여 각 속도 설정에 대 한 단추의 텍스트 레이블 또는 질감을 제어 하기 위해 최대 9 개의 테마를 추가할 수 있습니다.

모든 click 이벤트는 값에 `DimensionIndex` 도달할 때까지 런타임에 1로 이동 합니다 `Dimensions` . 그러면 주기가 0으로 다시 설정 됩니다.

![다차원 프로필 예](../images/interactable/Profile_multiDimensions.png)

개발자는를 평가 [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 하 여 현재 활성 상태인 차원을 확인할 수 있습니다.

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a>런타임에 Interactable 만들기

*Interactable* 은 런타임에 모든 GameObject에 쉽게 추가할 수 있습니다. 다음 예제에서는 [시각적 테마](visual-themes.md)를 사용 하 여 프로필을 할당 하는 방법을 보여 줍니다.

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

### <a name="interactable-events-via-code"></a>코드를 통해 이벤트 Interactable

다음 예제를 사용 하 여 코드를 통해 기본 이벤트에 작업을 추가할 수 있습니다 [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) .

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

함수를 사용 [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 하 여 런타임에 동적으로 이벤트 수신기를 추가 합니다.

아래 예제 코드는 포커스 enter/exit를 수신 하는 [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)를 추가 하는 방법을 보여 줍니다. 또한 이벤트 인스턴스가 발생할 때 수행할 작업 코드를 정의 합니다.

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

아래 예제 코드에서는 [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)를 추가 하는 방법을 보여 줍니다 .이는 토글 가능 상호 중단에 대 한 선택/선택 취소 상태 전환을 *수신 하 고*, 또한 이벤트 인스턴스가 발생할 때 수행할 작업 코드를 정의 합니다.

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

## <a name="see-also"></a>추가 정보

* [시각적 테마](visual-themes.md)
* [입력 작업](../input/input-actions.md)
* [음성 명령](../input/speech.md)
* [단추](button.md)
* [MRTK 표준 셰이더](../rendering/MRTK-standard-shader.md)
