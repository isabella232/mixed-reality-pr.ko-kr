---
title: Unity의 HP Reverb G2 컨트롤러
description: SteamVR 및 Windows Mixed Reality Unity 응용 프로그램에서 새로운 HP 반향 G2 컨트롤러를 설정 하 고 사용 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, 반향, 반향 G2, HP 반향 G2, 혼합 현실, 개발, 동작 컨트롤러, 사용자 입력, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 기능, holograms, 게임 개발
ms.openlocfilehash: 4e561cb1e46fe487f1b25ed526f0adeafc2de6c525835ffe3b1871d7516b233e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215626"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>Unity의 HP Reverb G2 컨트롤러

HP 모션 컨트롤러는 새로운 유형의 Windows Mixed Reality 컨트롤러 이며, 약간 다른 사용 가능한 입력 집합을 사용 하는 동일한 추적 기술입니다. 

* 터치 패드는 오른쪽 컨트롤러에 대 한 A와 B 라는 두 개의 단추로 대체 되었으며, 왼쪽 컨트롤러의 경우 X 및 Y입니다. 
* 이제 눌린 상태와 누르지 않음 상태를 포함 하는 단추 대신 0.0과 1.0 사이의 값 스트림을 게시 하는 트리거입니다. 

기존 Windows 및 Unity api를 통해 새 입력에 액세스할 수 없으므로 전용 **MixedReality** UPM 패키지가 필요 합니다. 

> [!IMPORTANT]
> **이 패키지의 클래스는 기존 Windows 및 Unity api를 대체 하지는 않지만이를 보완 합니다.** 클래식 Windows Mixed Reality 컨트롤러 및 HP 동작 컨트롤러에서 일반적으로 사용할 수 있는 기능은 기존 api를 사용 하 여 동일한 코드 경로를 통해 액세스할 수 있습니다. 새 입력만 추가 MixedReality 패키지를 사용 해야 합니다. 

## <a name="hp-motion-controller-overview"></a>HP 모션 컨트롤러 개요

*MixedReality* 은 동작 컨트롤러를 나타냅니다. 각 *Motioncontroller* 인스턴스에는 *XR가 있습니다. WSA. InteractionSource* 피어-사용, 공급 업체 id, 제품 id 및 버전을 사용 하 여 상관 관계를 지정할 수 있습니다. 

*InteractionManager* events를 사용 하 여 새 *InteractionSource* 인스턴스를 검색 하는 것과 마찬가지로 *motioncontroller감시자* 를 만들고 해당 이벤트를 구독 하 여 motioncontroller 인스턴스를 사용할 수 있습니다. MotionController의 메서드 및 속성은 해당 단추, 트리거, 2D 축 및 엄지 스틱을 포함 하 여 컨트롤러에서 지원 되는 입력을 설명 합니다. 또한 MotionController 클래스는 *Motioncontroller판독값* 클래스를 통해 입력 상태에 액세스 하는 메서드를 노출 합니다. MotionControllerReading 클래스는 지정 된 시간에 컨트롤러 상태의 스냅숏을 나타냅니다. 

## <a name="installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool"></a>Mixed Reality 기능 도구를 사용 하 여 MixedReality 설치

새 Mixed Reality 기능 도구 응용 프로그램을 사용 하 여 MixedReality 플러그 인을 설치 합니다. [설치 및 사용 지침](welcome-to-mr-feature-tool.md) 을 따르고 mixed reality Toolkit 범주에서 **혼합 현실 입력** 패키지를 선택 합니다.

![혼합 현실 기능이 강조 표시 된 혼합 현실 기능 도구 패키지 창](images/feature-tool-mrinput.png)

## <a name="using-microsoftmixedrealityinput"></a>MixedReality 사용 

### <a name="input-values"></a>입력 값

MotionController는 두 종류의 입력을 노출할 수 있습니다. 

* 단추와 트리거 상태는 얼마나 누르는 지를 나타내는 0.0에서 1.0 사이의 고유한 부동 소수점 값으로 표현 됩니다.
    * 트리거에서 0.0 (완전히 릴리스된)에서 1.0 (완전히 누름) 사이의 연속 값을 반환할 수 있는 동안에는 0.0 (누르지 않은 경우) 또는 1.0 (누른 경우)만 반환할 수 있습니다. 
* 엄지 스틱 상태는 X 및 Y 구성 요소가-1.0 ~ 1.0 사이인 Vector2.x으로 표현 됩니다. 

*Motioncontroller. Get보도 Sableinput ()* 을 사용 하 여 누름 값 (단추 및 트리거)을 반환 하는 입력 목록을 반환 하거나, *GetXYInputs ()* 메서드를 사용 하 여 2 축 값을 반환 하는 입력의 목록을 반환할 수 있습니다. 

MotionControllerReading 인스턴스는 지정 된 시간에 컨트롤러의 상태를 나타냅니다. 

* *Get보도 Sedvalue ()* 는 단추 또는 트리거의 상태를 검색 합니다. 
* *GetXYValue ()* 는 엄지 스틱 상태를 검색 합니다. 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a>MotionController 인스턴스 및 해당 상태 컬렉션을 유지 관리 하는 캐시 만들기 

먼저 MotionControllerWatcher를 인스턴스화하고 *Motioncontrollerwatcher* 및 *Motioncontrollerwatcher* 된 이벤트에 대 한 처리기를 등록 하 여 사용 가능한 motioncontroller 인스턴스의 캐시를 유지 합니다. 이 캐시는 다음 코드에서 보여 주는 것 처럼 GameObject에 연결 된 MonoBehavior 합니다.

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    /// <summary> 
    /// Internal helper class which associates a Motion Controller 
    /// and its known state 
    /// </summary> 
    private class MotionControllerState 
    { 
        /// <summary> 
        /// Construction 
        /// </summary> 
        /// <param name="mc">motion controller</param>` 
        public MotionControllerState(MotionController mc) 
        { 
            this.MotionController = mc; 
        } 

        /// <summary> 
        /// Motion Controller that the state represents 
        /// </summary> 
        public MotionController MotionController { get; private set; } 
        … 
    } 

    private MotionControllerWatcher _watcher; 
    private Dictionary<Handedness, MotionControllerState> 
        _controllers = new Dictionary<Handedness, MotionControllerState>(); 

    /// <summary> 
    /// Starts monitoring controller's connections and disconnections 
    /// </summary> 
    public void Start() 
    { 
        _watcher = new MotionControllerWatcher(); 
        _watcher.MotionControllerAdded += _watcher_MotionControllerAdded; 
        _watcher.MotionControllerRemoved += _watcher_MotionControllerRemoved; 
        var nowait = _watcher.StartAsync(); 
    } 

    /// <summary> 
    /// Stops monitoring controller's connections and disconnections 
    /// </summary> 
    public void Stop() 
    { 
        if (_watcher != null) 
        { 
            _watcher.MotionControllerAdded -= _watcher_MotionControllerAdded; 
            _watcher.MotionControllerRemoved -= _watcher_MotionControllerRemoved; 
            _watcher.Stop(); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been removed from the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerRemoved(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers.Remove(e.Handedness); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been added to the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerAdded(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers[e.Handedness] = new MotionControllerState(e); 
        } 
    } 
} 
```

### <a name="reading-new-inputs-by-polling"></a>폴링을 통해 새 입력 읽기 

MonoBehavior 클래스의 *Update* 메서드를 실행 하는 동안 *TryGetReadingAtTime* 를 통해 알려진 각 컨트롤러의 현재 상태를 읽을 수 있습니다. *현재 날짜/시간* 을 타임 스탬프 매개 변수로 전달 하 여 컨트롤러의 최신 상태를 읽을 수 있도록 하려고 합니다. 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 

    private class MotionControllerState 
    {
        … 

        /// <summary> 
        /// Update the current state of the motion controller 
        /// </summary> 
        /// <param name="when">time of the reading</param> 
        public void Update(DateTime when) 
        { 
            this.CurrentReading = this.MotionController.TryGetReadingAtTime(when); 
        } 

        /// <summary> 
        /// Last reading from the controller 
        /// </summary> 
        public MotionControllerReading CurrentReading { get; private set; } 
    } 

    /// <summary> 
    /// Updates the input states of the known motion controllers 
    /// </summary> 
    public void Update() 
    { 
        var now = DateTime.Now; 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

컨트롤러를 사용 하 여 현재 입력 값을 가져올 수 있습니다. 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 
    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(Handedness handedness, ControllerInput input) 
    { 
        MotionControllerReading currentReading = null; 

        lock (_controllers) 
        { 
            if (_controllers.TryGetValue(handedness, out MotionControllerState mc)) 
            { 
                currentReading = mc.CurrentReading; 
            } 
        } 

        return (currentReading == null) ? 0.0f : currentReading.GetPressedValue(input); 
    } 

    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(UnityEngine.XR.WSA.Input.InteractionSourceHandedness handedness, ControllerInput input) 
    { 
        return GetValue(Convert(handedness), input); 
    } 

    /// <summary> 
    /// Returns a boolean indicating whether a controller input such as button or trigger is pressed 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>true if pressed, false if not pressed</returns> 
    public bool IsPressed(Handedness handedness, ControllerInput input) 
    { 
        return GetValue(handedness, input) >= PressedThreshold; 
    } 
} 
```

예를 들어 InteractionSource의 아날로그 값을 읽으려면 다음을 수행 합니다. 

```csharp
/// Read the analog grasp value of all connected interaction sources 
void Update() 
{ 
    … 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    foreach (var sourceState in InteractionManager.GetCurrentReading()) 
    { 
        float graspValue = stateCache.GetValue(sourceState.source.handedness, 
            Microsoft.MixedReality.Input.ControllerInput.Grasp);
        … 
    }
} 
```

### <a name="generating-events-from-the-new-inputs"></a>새 입력에서 이벤트 생성 

프레임당 한 번 컨트롤러의 상태를 폴링하는 대신 모든 상태 변경을 이벤트로 처리할 수 있습니다 .이 옵션을 사용 하면 프레임 보다 빨리 지속 되는 작업을 처리할 수 있습니다. 이 접근 방식이 작동 하려면 동작 컨트롤러의 캐시가 마지막 프레임 이후 컨트롤러에서 게시 한 모든 상태를 처리 해야 합니다 .이 작업은 MotionController에서 검색 된 마지막 MotionControllerReading의 타임 스탬프를 저장 하 고 *motioncontroller. TryGetReadingAfterTime ()* 를 호출 하 여 수행할 수 있습니다. 

```csharp
private class MotionControllerState 
{ 
    … 
    /// <summary> 
    /// Returns an array representng buttons which are pressed 
    /// </summary> 
    /// <param name="reading">motion controller reading</param> 
    /// <returns>array of booleans</returns> 
    private bool[] GetPressed(MotionControllerReading reading) 
    { 
        if (reading == null) 
        { 
            return null; 
        } 
        else 
        { 
            bool[] ret = new bool[this.pressableInputs.Length]; 
            for (int i = 0; i < pressableInputs.Length; ++i) 
            { 
                ret[i] = reading.GetPressedValue(pressableInputs[i]) >= PressedThreshold; 
            } 

            return ret; 
        } 
    } 

    /// <summary> 
    /// Get the next available state of the motion controller 
    /// </summary> 
    /// <param name="lastReading">previous reading</param> 
    /// <param name="newReading">new reading</param> 
    /// <returns>true is a new reading was available</returns> 
    private bool GetNextReading(MotionControllerReading lastReading, out MotionControllerReading newReading) 
    { 
        if (lastReading == null) 
        { 
            // Get the first state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterSystemRelativeTime(TimeSpan.FromSeconds(0.0)); 
        } 
        else 
        { 
            // Get the next state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterTime(lastReading.InputTime); 
        } 

        return newReading != null; 
    } 

    /// <summary> 
    /// Processes all the new states published by the controller since the last call 
    /// </summary> 
    public IEnumerable<MotionControllerEventArgs> GetNextEvents() 
    {
        MotionControllerReading lastReading = this.CurrentReading; 
        bool[] lastPressed = GetPressed(lastReading); 
        MotionControllerReading newReading; 
        bool[] newPressed; 

        while (GetNextReading(lastReading, out newReading)) 
        { 
            newPressed = GetPressed(newReading); 

            // If we have two readings, compare and generate events 
            if (lastPressed != null) 
            { 
                for (int i = 0; i < pressableInputs.Length; ++i) 
                { 
                    if (newPressed[i] != lastPressed[i]) 
                    { 
                        yield return new MotionControllerEventArgs(this.MotionController.Handedness, newPressed[i], this.pressableInputs[i], newReading.InputTime); 
                    } 
                } 
            } 

            lastPressed = newPressed; 
            lastReading = newReading; 
        } 

        // No more reading 
        this.CurrentReading = lastReading; 
    } 
} 
```

캐시 내부 클래스를 업데이트 했으므로 MonoBehavior 클래스는 눌려진 두 이벤트를 노출 하 고, 해당 Update () 메서드에서이를 발생 시킬 수 있습니다. 

```csharp
/// <summary> 
/// Event argument class for InputPressed and InputReleased events 
/// </summary> 
public class MotionControllerEventArgs : EventArgs 
{ 
    public MotionControllerEventArgs(Handedness handedness, bool isPressed, rollerInput input, DateTime inputTime) 
    { 
        this.Handedness = handedness; 
        this.Input = input; 
        this.InputTime = inputTime; 
        this.IsPressed = isPressed; 
    } 

    /// <summary> 
    /// Handedness of the controller raising the event 
    /// </summary> 
    public Handedness Handedness { get; private set; } 

    /// <summary> 
    /// Button pressed or released 
    /// </summary> 
    public ControllerInput Input { get; private set; } 

    /// <summary> 
    /// Time of the event 
    /// </summary> 
    public DateTime InputTime { get; private set; } 

    /// <summary> 
    /// true if button is pressed, false otherwise 
    /// </summary> 
    public bool IsPressed { get; private set; } 
} 

/// <summary> 
/// Event raised when a button is pressed 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputPressed; 

/// <summary> 
/// Event raised when a button is released 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputReleased; 

/// <summary> 
/// Updates the input states of the known motion controllers 
/// </summary> 
public void Update() 
{ 
    // If some event handler has been registered, we need to process all states  
    // since the last update, to avoid missing a quick press / release 
    if ((InputPressed != null) || (InputReleased != null)) 
    { 
        List<MotionControllerEventArgs> events = new <MotionControllerEventArgs>(); 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                events.AddRange(controller.Value.GetNextEvents()); 
            } 
        } 
 
        // Sort the events by time 
        events.Sort((e1, e2) => DateTime.Compare(e1.InputTime, e2.InputTime)); 

        foreach (MotionControllerEventArgs evt in events) 
        { 
            if (evt.IsPressed && (InputPressed != null)) 
            { 
                InputPressed(this, evt); 
            } 
            else if (!evt.IsPressed && (InputReleased != null)) 
            { 
                InputReleased(this, evt); 
            } 
        } 
    } 
    else 
    { 
        // As we do not predict button presses and the timestamp of the next e is in the future 
        // DateTime.Now is correct in this context as it will return the latest e of controllers 
        // which is the best we have at the moment for the frame. 
        var now = DateTime.Now; 
        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

위의 코드 예제에서 구조를 사용 하면 이벤트를 훨씬 더 쉽게 등록할 수 있습니다. 

```csharp
public InteractionSourceHandedness handedness; 
public Microsoft.MixedReality.Input.ControllerInput redButton;

// Start of the Mono Behavior: register handlers for events from cache 
void Start() 
{ 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    stateCache.InputPressed += stateCache_InputPressed; 
    stateCache.InputReleased += stateCache_InputReleased; 
    … 
} 

// Called when a button is released 
private void stateCache_InputReleased(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 

// Called when a button is pressed 
private void stateCache_InputPressed(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 
```

## <a name="see-also"></a>참고 항목

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](../porting-apps/porting-guides.md?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](../porting-apps/porting-guides.md?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->