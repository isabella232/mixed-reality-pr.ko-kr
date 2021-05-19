---
title: 입력 이벤트
description: MRTK의 InputEvents에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 이벤트,
ms.openlocfilehash: 450c6dbbed8fc9bbb1a648b7a22f0de66747cbaf
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145228"
---
# <a name="input-events"></a>입력 이벤트

아래 목록에서는 사용자 지정 MonoBehaviour 구성 요소에서 구현할 수 있는 모든 입력 이벤트 인터페이스를 간략하게 설명합니다. 이러한 인터페이스는 MRTK 입력 시스템에서 호출하여 사용자 입력 상호 작용에 따라 사용자 지정 앱 논리를 처리합니다. [포인터 입력 이벤트는](pointers.md#pointer-event-interfaces) 아래 표준 입력 이벤트 유형과 약간 다르게 처리됩니다.

> [!IMPORTANT]
> 기본적으로 스크립트는 포커스에 있는 GameObject의 포인터 또는 부모에 의해 포커스가 있는 GameObject인 경우에만 입력 이벤트를 받습니다.

| Handler | 이벤트 | Description |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | 소스 검색/손실 | 입력 소스가 감지/손실될 때(예: 굴절된 손을 감지하거나 추적하지 못했을 때) 발생합니다. |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | 소스 자세가 변경되었습니다. | 소스에서 발생된 자세 변경 내용입니다. 소스 자세는 입력 소스의 일반적인 자세를 나타냅니다. 6개의 DOF 컨트롤러에서 그립 또는 포인터 자세와 같은 특정 자세는 를 통해 얻을 수 `IMixedRealityInputHandler<MixedRealityPose>` 있습니다. |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | 입력 아래로/위로 | 단추와 같은 이진 입력의 변경 내용에서 발생합니다. |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 입력이 변경되었습니다. | 지정된 형식의 입력이 변경될 때 발생합니다. **T는** 다음 값을 사용할 수 있습니다. <br/> - *float(예:* 아날로그 트리거 반환)<br/> - *Vector2(예:* 게임 패드 엄지스틱 방향을 반환함) <br/> - *Vector3* (예: 추적 된 장치의 위치 반환) <br/> - *4 원수* (예: 추적 된 장치의 방향 반환)<br/> - [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (예: 완전히 추적 된 장치 반환) |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | 음성 키워드가 인식 되었습니다. | *음성 명령 프로필* 에 구성 된 키워드 중 하나를 인식 했을 때 발생 합니다. |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | 받아쓰기<br/> Hypothesis <br/> 결과 <br/> 완료 <br/> Error | 받아쓰기 시스템에서 받아쓰기 세션의 결과를 보고 하는 데 발생 합니다. |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | 제스처 이벤트 위치: <br/> 시작됨 <br/> 업데이트됨 <br/> Completed <br/> 취소됨 | 제스처 검색에 발생 합니다. |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | 제스처 업데이트 됨/완료 됨 | 지정 된 형식의 추가 데이터를 포함 하는 제스처를 검색할 때 발생 합니다. **T** 의 가능한 값에 대 한 자세한 내용은 [**제스처 이벤트**](gestures.md#gesture-events) 를 참조 하세요. |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | 직접 조인트 업데이트 | 직접 조인트가 업데이트 되 면 해당 컨트롤러에 의해 발생 합니다. |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | 손 메쉬 업데이트 됨 | 손 메쉬가 업데이트 될 때이를 트레일러 컨트롤러에서 발생 시킵니다. |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | 작업 시작 됨/종료 됨 | 작업에 매핑되는 입력에 대 한 작업 시작 및 종료를 나타내려면을 발생 시킵니다. |

## <a name="input-events-in-action"></a>입력 이벤트의 작동

스크립트 수준에서 입력 이벤트는 위의 표에 표시 된 이벤트 처리기 인터페이스 중 하나를 구현 하 여 사용 될 수 있습니다. 사용자 상호 작용을 통해 입력 이벤트가 발생 하는 경우 다음 작업이 수행 됩니다.

1. MRTK 입력 시스템은 입력 이벤트가 발생했음을 인식합니다.
1. MRTK 입력 시스템은 등록된 모든 전역 입력 처리기에 입력 이벤트의 관련 인터페이스 [함수를 발생합니다.](#register-for-global-input-events)
1. 입력 시스템에 등록된 모든 활성 포인터:
    1. 입력 시스템은 현재 포인터에 포커스가 있는 GameObject를 결정합니다.
    1. 입력 시스템은 [Unity의 이벤트 시스템을](https://docs.unity3d.com/Manual/EventSystem.html) 활용하여 포커스가 있는 GameObject에서 일치하는 모든 구성 요소에 대한 관련 인터페이스 함수를 시작합니다.
    1. 입력 이벤트가 [사용된 것으로 표시된](#how-to-stop-input-events)경우 프로세스가 종료되고 더 이상 GameObjects에서 콜백을 수신하지 않습니다.
        - 예제: 인터페이스를 구현하는 구성 요소는 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 음성 명령이 인식될 때 검색됩니다.
        - 참고: Unity 이벤트 시스템은 현재 GameObject에서 원하는 인터페이스와 일치하는 구성 요소가 없으면 부모 GameObject를 검색하기 위해 버블 업됩니다.
1. 전역 입력 처리기가 등록되지 않고 일치하는 구성 요소/인터페이스가 있는 GameObject가 없는 경우 입력 시스템은 등록된 각 대체 입력 처리기를 호출합니다.

> [!NOTE]
> [포인터 입력 이벤트는](pointers.md#pointer-event-interfaces) 위에 나열된 입력 이벤트 인터페이스와 약간 다른 방식으로 처리됩니다. 특히 포인터 입력 이벤트는 입력 이벤트를 발생시킨 포인터와 모든 전역 입력 처리기에 의해 포커스가 있는 GameObject에 의해서만 처리됩니다. 일반 입력 이벤트는 모든 활성 포인터에 대한 포커스에서 GameObjects에 의해 처리됩니다.

### <a name="input-event-interface-example"></a>입력 이벤트 인터페이스 예제

아래 코드에서는 인터페이스를 사용하는 것을 보여 주는 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 코드입니다. 사용자가 이 클래스를 사용하는 GameObject에 집중하는 동안 "더 작음" 또는 "더 큰" 단어를 `ShowHideSpeechHandler` 말하면 GameObject는 자체의 크기를 절반 또는 두 배만큼 조정합니다.

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
> [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 입력 이벤트를 사용하려면 원하는 키워드가 [MRTK Speech Commands Profile](speech.md)에 미리 등록되어 있어야 합니다.

## <a name="register-for-global-input-events"></a>전역 입력 이벤트 등록

전역 입력 이벤트를 수신 하는 구성 요소를 만들려면 무시는 어떤 GameObject가 포커스에 있을 수 있는지를 확인 하 고 구성 요소는 입력 시스템에 자신을 등록 해야 합니다. 등록 되 면이 MonoBehaviour의 모든 인스턴스는 현재 포커스가 있는 모든 GameObject 및 기타 전역 등록 수신기와 함께 입력 이벤트를 수신 합니다.

입력 이벤트를 [사용으로 표시](#how-to-stop-input-events)한 경우에는 전역으로 등록 된 처리기도 모든 콜백을 수신 합니다. 그러나 포커스가 없는 Gameobject는 이벤트를 수신 합니다.

### <a name="global-input-registration-example"></a>전역 입력 등록 예

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

## <a name="register-for-fallback-input-events"></a>대체 입력 이벤트 등록

대체 (Fallback) 입력 처리기는 등록 된 전역 입력 처리기와 비슷하지만 입력 이벤트 처리의 마지막 수단으로 취급 됩니다. 전역 입력 처리기를 찾을 수 없고 포커스에 Gameobject 없는 경우에만 대체 입력 처리기가 활용 됩니다.

### <a name="fallback-input-handler-example"></a>대체 입력 처리기 예

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

## <a name="how-to-stop-input-events"></a>입력 이벤트를 중지 하는 방법

모든 입력 이벤트 인터페이스는 [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) 인터페이스의 각 함수에 대 한 매개 변수로 데이터 개체를 제공 합니다. 이 이벤트 데이터 개체는 Unity 자체에서 확장 [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) 됩니다.

[설명 된 대로](#input-events-in-action)실행을 통해 입력 이벤트가 전파 되지 않도록 하려면 구성 요소가를 호출 하 여 [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) 이벤트를 사용 된 것으로 표시할 수 있습니다. 이렇게 하면 전역 입력 처리기를 제외 하 고 현재 입력 이벤트를 수신 하는 다른 Gameobject이 중지 됩니다.

> [!NOTE]
> 메서드를 호출 하는 구성 요소는 `Use()` 다른 gameobject를 수신 하지 못하게 합니다. 그러나 현재 GameObject의 다른 구성 요소는 여전히 입력 이벤트를 수신 하 고 관련 된 인터페이스 함수를 발생 시킵니다.

## <a name="see-also"></a>참고 항목

- [포인터](pointers.md)
- [Speech](speech.md)
- [입력 상태](input-state.md)
