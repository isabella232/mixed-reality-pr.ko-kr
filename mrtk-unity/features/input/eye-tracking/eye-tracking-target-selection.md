---
title: 시선 추적 대상 선택
description: 시선 응시 데이터 및 시선 응시 특정 이벤트에 액세스하여 MRTK에서 대상을 선택하는 방법
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, EyeTracking,
ms.openlocfilehash: aab2f35259db183f4f3edb4fffc2b3e7a066bccf9c69e492c90ee193388b8b7a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189603"
---
# <a name="eye-supported-target-selection"></a>시선 지원 대상 선택

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

이 페이지에서는 MRTK에서 대상을 선택하기 위해 시선 응시 데이터 및 시선 응시 특정 이벤트에 액세스하기 위한 다양한 옵션을 설명합니다. 시선 추적을 사용하면 _손 추적_ 및 음성 명령과 같은 추가 입력을 통해 사용자가 보고 있는 내용에 대한 정보를 조합하여 빠르고 간편하게 대상을 선택할 수 _있습니다._

- _"Select"(기본_ 음성 명령)라고 & 찾습니다.
- "분해" 또는 _"팝"(사용자_ 지정 음성 명령)을 & 찾습니다. 
- & Bluetooth 단추 보기
- 손가락 모으기를 &(즉, 손을 내밀고 엄지 단추와 인덱스 손가락을 함께 가져 오십시오.)
  - 이렇게 하려면 손 광선을 사용하지 않도록 [설정해야 합니다.](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)

시선 응시를 사용하여 홀로그램 콘텐츠를 선택하려면 몇 가지 옵션이 있습니다.

[**1. 기본 포커스 포인터 사용:**](#1-use-generic-focus-and-pointer-handlers)

우선 순위가 있는 커서로 이해할 수 있습니다.
기본적으로 손을 볼 수 있는 경우 손 광선이 됩니다.
손을 볼 수 없는 경우 우선 순위가 있는 포인터는 머리 또는 시선 응시입니다.
따라서 현재 디자인 헤드 또는 시선 응시를 기반으로 손 광선이 사용되는 경우 커서 입력으로 표시되지 않습니다.

예를 들어:

사용자가 먼 홀로그램 단추를 선택하려고 합니다.
개발자는 사용자가 다양한 조건에서 이 작업을 수행할 수 있는 유연한 솔루션을 제공하려고 합니다.

- 단추까지 위로 들어와서 단추를 쌓습니다.
- 멀리서 보고 "select"라고 말합니다.
- 손 광선을 사용하여 단추를 대상으로 지정하고 손가락 모으기를 수행하는 경우 가장 유연한 솔루션은 현재 우선 순위가 지정된 기본 포커스 포인터가 이벤트를 트리거할 때마다 알려주기 때문에 기본 포커스 처리기를 사용하는 것입니다. 손 광선을 사용하는 경우 손을 보는 즉시 머리 또는 시선 응시 포커스 포인터가 비활성화됩니다.

> [!IMPORTANT]
> 손 광선을 사용하는 경우 손을 보는 즉시 머리 또는 시선 응시 포커스 포인터가 비활성화됩니다. [ _'모양 및 손가락 모으기'_ 상호 작용을 지원하려면 손 광선 을 사용하지 않도록 설정해야 합니다.](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray) 시선 추적 샘플 장면에서 눈 + 손 동작을 사용하여 보다 풍부한 상호 작용을 보여줄 수 있도록 손 광선을 사용하지 않도록 설정했습니다( 예: [시선 지원 위치).](eye-tracking-eyes-and-hands.md)

[**2. 시선 포커스와 손 광선을 동시에 사용합니다.**](#2-independent-eye-gaze-specific-eyetrackingtarget)

특정 이벤트를 트리거하고 여러 원거리 상호 작용 기술을 동시에 사용할 수 있는 포커스 포인터 유형을 보다 구체적으로 지정하려는 경우가 있을 수 있습니다.

예를 들어 앱에서 사용자는 원거리 광선을 사용하여 홀로그램 기계 설치를 조작할 수 있습니다. 예를 들어 멀리 떨어진 홀로그램 엔진 부품을 잡고 붙들고 있습니다. 이렇게 하는 동안 사용자는 몇 가지 지침을 수행하고 일부 확인란을 표시하여 진행 상황을 기록해야 합니다. 사용자가 손을 _사용 중이지 않은_ 경우 확인란을 터치하거나 손 광선을 사용하여 선택하는 것이 직관적입니다. 그러나 일부 홀로그램 엔진 부품을 배치하는 경우처럼 사용자가 손을 사용 중인 경우 사용자가 시선 응시를 사용하여 지침을 원활하게 스크롤하고 단순히 확인란을 보고 "확인란을 확인하세요!"라고 말할 수 있도록 하려고 합니다.

이를 사용하려면 핵심 MRTK FocusHandlers와 독립적이며 아래에서 자세히 설명될 시선별 EyeTrackingTarget 스크립트를 사용해야 합니다.

## <a name="1-use-generic-focus-and-pointer-handlers"></a>1. 제네릭 포커스 및 포인터 처리기 사용

시선 추적이 올바르게 설정된 [경우(시선 추적을 사용하도록 기본 MRTK 설정](eye-tracking-basic-setup.md)참조) 사용자가 눈으로 홀로그램을 선택할 수 있도록 하는 것은 다른 포커스 입력(예: 머리 응시 또는 손 광선)과 동일합니다. 이렇게 하면 코드를 그대로 유지하면서 사용자의 요구에 따라 MRTK 입력 포인터 프로필에서 기본 포커스 형식을 정의하여 홀로그램과 상호 작용하는 유연한 방법의 큰 이점을 제공합니다. 이렇게 하면 코드 줄을 변경하지 않고 머리 또는 시선 응시 사이를 전환하거나 손 광선을 원거리 상호 작용을 위한 시선 대상으로 바꿀 수 있습니다.

### <a name="focusing-on-a-hologram"></a>홀로그램에 집중

홀로그램에 초점을 맞춘 시기를 감지하려면 _OnFocusEnter_ 및 _OnFocusExit의_ 두 인터페이스 멤버를 제공하는 _'IMixedRealityFocusHandler'_ 인터페이스를 사용합니다.

다음은 볼 때 홀로그램의 색을 변경하는 [ColorTap.cs의](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) 간단한 예제입니다.

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

### <a name="selecting-a-focused-hologram"></a>포커스가 있는 홀로그램 선택

포커스가 있는 홀로그램을 선택하려면 _PointerHandler를_ 사용하여 입력 이벤트를 수신 대기하여 선택을 확인합니다.
예를 들어 _IMixedRealityPointerHandler를_ 추가하면 간단한 포인터 입력에 반응하게 됩니다.
_IMixedRealityPointerHandler_ 인터페이스를 사용하려면 _OnPointerUp, OnPointerDown_ 및 _OnPointerClicked_ 의 세 가지 인터페이스 멤버를 구현해야 합니다. 

아래 예제에서는 홀로그램을 보고 손가락 모으기 또는 "select"라고 말하여 홀로그램의 색을 변경합니다.
이벤트를 트리거하는 데 필요한 작업은 Unity 편집기에서 형식을 설정할 수 있는 에 의해 정의됩니다. `eventData.MixedRealityInputAction == selectAction` `selectAction` 기본적으로 "선택" 작업입니다. 사용 가능한 [MixedRealityInputActions](../input-actions.md) 형식은 MRTK 구성 프로필 입력 입력 작업을 통해 _MRTK 프로필에서_ 구성할 수  ->    ->  있습니다.

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

### <a name="eye-gaze-specific-baseeyefocushandler"></a>시선 응시 관련 BaseEyeFocusHandler

시선 응시는 다른 포인터 입력과 매우 다를 수 있기 때문에 _시선 응시이고_ 현재 기본 입력 포인터인 경우에만 포커스 입력에 반응해야 할 수 있습니다.
이를 위해 [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) 시선 추적과 관련되고 에서 파생되는 를 [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) 사용합니다.
앞에서 설명한 것처럼 시선 응시 대상 지정이 현재 기본 포인터 입력인 경우에만 트리거됩니다(즉, 손 광선이 활성 상태가 아닙니다). 자세한 내용은 [시선 응시 + 손 제스처를 지원하는 방법을 참조하세요.](eye-tracking-eyes-and-hands.md)

다음은 `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes)의 예제입니다.
이 데모에는 개체의 어떤 부분에 따라 설정되는 두 개의 3D 홀로그램이 있습니다. 사용자가 홀로그램의 왼쪽을 보면 해당 부분이 사용자를 향하는 전면으로 천천히 이동합니다.
오른쪽을 살펴보면 해당 부분이 천천히 앞으로 이동합니다.
이 동작은 항상 활성화하지 않으려는 동작이며 손 광선 또는 머리 응시로 실수로 트리거하지 않을 수도 있습니다.
를 [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) 연결하면 GameObject가 확인되는 동안 회전합니다.

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

API 설명서에서 의 사용 가능한 이벤트의 전체 목록을 [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) 확인합니다.

- **OnEyeFocusStart:** 시선 응시 광선이 이 대상의 충돌체와 교차하기 *시작하면* 트리거됩니다.
- **OnEyeFocusStay:** 시선 응시 광선이 이 대상의 충돌체와 교차하는 *동안* 트리거됩니다.
- **OnEyeFocusStop:** 시선 응시 광선이 이 대상의 충돌체와의 교차를 *중지하면* 트리거됩니다.
- **OnEyeFocusDwell:** 지정된 시간 동안 시선 응시 광선이 이 대상의 충돌체와 교차하면 트리거됩니다.

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a>2. 독립적인 시선 응시 관련 EyeTrackingTarget

마지막으로, 스크립트를 통해 다른 포커스 포인터와 완전히 독립적인 시선 기반 입력을 처리할 수 있는 솔루션을 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 제공합니다.

여기에는 다음과 같은 세 _가지 이점이 있습니다._

- 홀로그램이 사용자의 시선 응시에만 반응하는지 확인할 수 있습니다.
- 이는 현재 활성 상태인 기본 입력과는 독립적입니다. 따라서 빠른 시선 대상 지정과 손 제스처를 결합하는 등 여러 입력을 한 번에 처리할 수 있습니다.
- Unity 편집기 내에서 또는 코드를 통해 기존 동작을 빠르고 편리하게 처리하고 다시 사용할 수 있도록 여러 Unity 이벤트가 이미 설정되어 있습니다.

몇 가지 _단점도 있습니다._

- 개별 입력을 개별적으로 처리하는 데 더 많은 노력이 있습니다.
- 세련된 성능 저하 없음: 시선 대상 지정만 지원합니다. 시선 추적이 작동하지 않는 경우 몇 가지 추가 대체가 필요합니다.

_BaseFocusHandler와_ 마찬가지로 _EyeTrackingTarget은_ Unity 편집기(아래 예제 참조)를 통해 또는 코드에서 _AddListener()를_ 사용하여 편리하게 수신 대기할 수 있는 몇 가지 시선 응시 관련 Unity 이벤트와 함께 제공됩니다.

- OnLookAtStart()
- WhileLookingAtTarget()
- OnLookAway()
- OnDwell()
- OnSelected()

다음에서는 _EyeTrackingTarget_ 를 사용하는 방법에 대한 몇 가지 예제를 안내합니다.

### <a name="example-1-eye-supported-smart-notifications"></a>예제 #1: 시선 지원 스마트 알림

`EyeTrackingDemo-02-TargetSelection`(Assets/MRTK/Examples/Demos/EyeTracking/Scenes)에서 시선 응시에 반응하는 _'스마트 들여쓰기 알림'에_ 대한 예제를 찾을 수 있습니다.
이러한 텍스트 상자는 장면에 배치할 수 있으며 쉽게 읽을 수 있도록 살펴볼 때 원활하게 확대되고 사용자 쪽으로 전환되는 3D 텍스트 상자입니다. 사용자가 알림을 읽는 동안 정보가 선명하고 명확하게 표시됩니다. 알림을 읽고 알림에서 벗어나면 알림이 자동으로 해제되고 페이드 아웃됩니다. 이 모든 것을 달성하기 위해 다음과 같이 시선 추적에 특정되지 않은 몇 가지 일반적인 동작 스크립트가 있습니다.

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

이 방법의 장점은 동일한 스크립트를 다양한 이벤트에서 다시 사용할 수 있다는 것입니다. 예를 들어 홀로그램은 음성 명령에 따라 또는 가상 단추를 누른 후 사용자를 향하기 시작할 수 있습니다. 이러한 이벤트를 트리거하려면 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) GameObject에 연결된 스크립트에서 실행해야 하는 메서드를 참조하기만 하면 됩니다.

_'스마트 들여쓰기 알림'의 예는_ 다음과 같습니다.

- **OnLookAtStart()**: 알림이 시작됩니다.
  - *FaceUser.Engage:* ... 사용자 쪽으로 전환합니다.
  - *ChangeSize.Engage:* ... _크기(지정된 최대 배율까지)_ 증가합니다.
  - *BlendOut.Engage:* ... 가 더 혼합되기 _시작합니다(더 미묘한 유휴 상태에 있는 후)._  

- **OnDwell()**: 알림이 충분히 조회되었다는 것을 _BlendOut_ 스크립트에 알릴 수 있습니다.

- **OnLookAway()**: 알림이 시작됩니다.
  - *FaceUser.Disengage:* ... 를 원래 방향으로 되돌립니다.
  - *ChangeSize.Disengage:* ... 원래 크기로 다시 줄입니다.
  - *BlendOut.Disengage:* ... 혼합 시작 - _OnDwell()이_ 트리거된 경우 완전히 혼합되어 제거되고, 그렇지 않으면 유휴 상태로 돌아갑니다.

**디자인 고려 사항:** 여기서는 사용자의 시선 응시에 너무 빠르게 반응하여 불편을 유발하지 않도록 이러한 동작의 속도를 신중하게 조정하는 것이 흥미로운 경험입니다.
그렇지 않으면 매우 부담스울 수 있습니다.

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a>예제 #2: 홀로그램 gem이 보고 있을 때 느리게 회전합니다.

예제 #1 마찬가지로, 볼 때 일정한 방향과 일정한 속도로 느린 회전을 하는 홀로그램 `EyeTrackingDemo-02-TargetSelection` gem(Assets/MRTK/Examples/Demos/EyeTracking/Scenes) 장면에 대한 호버 피드백을 쉽게 만들 수 있습니다. _EyeTrackingTarget의_ _WhileLookingAtTarget()_ 이벤트에서 홀로그램 gem의 회전을 트리거하기만 하면 됩니다. 다음은 몇 가지 세부 정보입니다.

1. 연결된 GameObject를 회전하는 public 함수를 포함하는 제네릭 스크립트를 만듭니다. 다음은 Unity 편집기에서 회전 방향과 속도를 조정할 수 있는 _RotateWithConstSpeedDir.cs의_ 예제입니다.

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

1. 대상 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) GameObject에 스크립트를 추가하고 아래 스크린샷과 같이 UnityEvent 트리거에서 _RotateTarget()_ 함수를 참조합니다.

    ![EyeTrackingTarget 샘플](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a>예제 #3: 이러한 gem을 팝 _즉, 다중 모달 시선 응시 지원 대상 선택_

이전 예제에서는 대상을 보는지 여부를 검색하는 것이 얼마나 쉬운지와 이에 대한 대응을 트리거하는 방법을 보여 보았습니다. 다음으로, 의 _OnSelected()_ 이벤트를 사용하여 gems를 분해해 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 보겠습니다. 흥미로운 부분은 선택이 트리거되는 *방식입니다.* [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget)를 사용하면 선택 항목을 호출하는 다양한 방법을 신속하게 할당할 수 있습니다.

- _손가락 모으기 제스처:_'작업 선택'을 '선택'으로 설정하려면 기본 손 제스처를 사용하여 선택을 트리거합니다.
즉, 사용자는 손만 들어와 엄지 손가락과 인덱스 손가락을 모아 선택을 확인할 수 있습니다.

- _"Select"라고_ 말하세요. 홀로그램을 선택하려면 기본 음성 명령 _"Select"를_ 사용합니다.

- _"분해"_ 또는 _"팝"_ 말: 사용자 지정 음성 명령을 사용하려면 다음 두 단계를 수행해야 합니다.
    1. _"DestroyTarget"과_ 같은 사용자 지정 작업 설정
        - _MRTK -> 입력 -> 입력 작업으로 이동합니다._
        - "새 작업 추가"를 클릭합니다.

    2. _"분해" 또는 "팝"과_ 같이 이 작업을  트리거하는 음성 명령을 설정합니다.
        - _MRTK -> 입력 -> Speech로_ 이동합니다.
        - "새 음성 명령 추가"를 클릭합니다.
            - 방금 만든 작업 연결
            - 단추를 눌러 작업을 트리거할 수 있도록 _KeyCode_ 할당

![음성 명령 EyeTrackingTarget 샘플](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

gem을 선택하면 소리가 나고 사라집니다. 스크립트에서 [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) 처리됩니다. 다음과 같은 두 가지 옵션이 있습니다.

- **Unity 편집기에서 다음을 수행합니다.** 각 gem 템플릿에 연결된 스크립트를 Unity 편집기의 OnSelected() Unity 이벤트에 연결하기만 하면 됩니다.
- **코드에서:** GameObjects를 끌어서 놓지 않으려면 이벤트 수신기를 스크립트에 직접 추가할 수도 있습니다.  
스크립트에서 수행된 방법의 예제는 다음과 같습니다. [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect)

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

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a>예제 #4: 손 광선과 시선 응시 입력을 함께 사용

손 광선은 머리 및 시선 응시 대상보다 우선합니다. 즉, 손 광선을 사용하는 경우 손을 볼 때 손 광선이 기본 포인터 역할을 합니다.
그러나 사용자가 특정 홀로그램을 보고 있는지 여부를 감지하면서 손 광선을 사용하려는 상황이 있을 수 있습니다. 아주 쉽습니다! 기본적으로 다음 두 단계가 필요합니다.

**1. 손 광선 사용:** 손 광선을 사용하도록 설정하려면 _Mixed Reality Toolkit -> 입력 -> 포인터로_ 이동합니다.
모든 시선 추적 데모 장면에 대해 Mixed Reality Toolkit 한 번 구성된 _EyeTrackingDemo-00-RootScene에_ _EyeTrackingDemoPointerProfile이_ 표시됩니다.
새 _입력 프로필을_ 처음부터 만들거나 현재 시선 추적 프로필을 조정할 수 있습니다.

- **처음부터:** _포인터_ 탭의 상황에 맞는 메뉴에서 _DefaultMixedRealityInputPointerProfile을_ 선택합니다.
손 광선이 이미 활성화된 기본 포인터 프로필입니다.
기본 커서(불투명 흰색 점)를 변경하려면 프로필을 복제하고 사용자 지정 포인터 프로필을 만들기만 하면 됩니다.
그런 _다음, DefaultCursor를_ 응시 커서 프리팹 _아래의 EyeGazeCursor로_ 바꿉니다.   
- **기존 _EyeTrackingDemoPointerProfile_ 기반:** _EyeTrackingDemoPointerProfile을_ 두 번 클릭하고 포인터 옵션 아래에 다음 항목을 _추가합니다._
  - **컨트롤러 유형:** '조인된 손', 'Windows Mixed Reality'
  - **손수:** Any
  - **포인터 프리팹:** DefaultControllerPointer

**2. 홀로그램이 보이는지 검색:** 스크립트를 사용하여 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 위에서 설명한 대로 홀로그램이 보이는지 검색할 수 있습니다. `FollowEyeGaze`손 광선의 사용 여부에 관계없이 시선 응시(예: 커서)를 따라 홀로그램을 보여 주는 샘플 스크립트에서 영감을 받을 수도 있습니다.

이제 시선 추적 데모 장면을 시작하면 손에서 광선이 나오는 것을 볼 수 있습니다.
예를 들어 시선 추적 대상 선택 데모에서 반투명 원은 여전히 시선 응시를 따르고 있으며, gem은 응시 여부에 따라 응답하지만, 위쪽 장면 메뉴 단추는 기본 입력 포인터(손)를 대신 사용합니다.

---
["MixedRealityToolkit의 시선 추적"으로 돌아가기](eye-tracking-main.md)
