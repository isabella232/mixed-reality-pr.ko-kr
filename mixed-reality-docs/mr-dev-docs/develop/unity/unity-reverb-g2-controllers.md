---
title: Unity의 HP 반향 G2 컨트롤러
description: SteamVR 및 Windows Mixed Reality Unity 응용 프로그램에서 새로운 HP 반향 G2 컨트롤러를 설정 하 고 사용 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, 반향, 반향 G2, HP 반향 G2, 혼합 현실, 개발, 동작 컨트롤러, 사용자 입력, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 기능, holograms, 게임 개발
ms.openlocfilehash: fa9b80076d65978ae1602fc4f9519d7e11c651b5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583575"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="9ba9f-104">Unity의 HP 반향 G2 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="9ba9f-104">HP Reverb G2 Controllers in Unity</span></span>

<span data-ttu-id="9ba9f-105">HP 모션 컨트롤러는 새로운 유형의 Windows Mixed Reality 컨트롤러 이며, 사용 가능한 입력 집합이 약간 다른 모든 동일한 추적 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-105">HP Motion controllers are a brand new type of Windows Mixed Reality controllers: all the same tracking technology with a slightly different set of available inputs:</span></span> 

* <span data-ttu-id="9ba9f-106">터치 패드는 오른쪽 컨트롤러에 대 한 A와 B 라는 두 개의 단추로 대체 되었으며, 왼쪽 컨트롤러의 경우 X 및 Y입니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-106">Touchpad has been replaced by two buttons: A and B for the right controller, and X and Y for the left controller.</span></span> 
* <span data-ttu-id="9ba9f-107">이제 눌린 상태와 누르지 않음 상태를 포함 하는 단추 대신 0.0과 1.0 사이의 값 스트림을 게시 하는 트리거입니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-107">Grasp is now a trigger that publishes a stream of values between 0.0 and 1.0 instead of a button with Pressed and Not Pressed states.</span></span> 

<span data-ttu-id="9ba9f-108">새 입력은 기존 Windows 및 Unity Api를 통해 액세스할 수 없으므로 전용 **MixedReality** 가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-108">Since the new inputs aren't accessible through existing Windows and Unity APIs, you need the dedicated **Microsoft.MixedReality.Input** UPM Package.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="9ba9f-109">**이 패키지의 클래스는 기존 Windows 및 Unity Api를 대체 하지 않지만이를 보완 합니다.**</span><span class="sxs-lookup"><span data-stu-id="9ba9f-109">**Classes in this package do not replace existing Windows and Unity APIs but complement them.**</span></span> <span data-ttu-id="9ba9f-110">클래식 Windows Mixed Reality 컨트롤러와 HP 동작 컨트롤러에서 일반적으로 사용할 수 있는 기능은 기존 Api를 사용 하 여 동일한 코드 경로를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-110">Features commonly available to both classic Windows Mixed Reality controllers and HP Motion Controllers are accessible through the same code path using existing APIs.</span></span> <span data-ttu-id="9ba9f-111">새 입력만 추가 MixedReality 패키지를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-111">Only the new inputs require the use of the additional Microsoft.MixedReality.Input package.</span></span> 

## <a name="hp-motion-controller-overview"></a><span data-ttu-id="9ba9f-112">HP 모션 컨트롤러 개요</span><span class="sxs-lookup"><span data-stu-id="9ba9f-112">HP Motion Controller overview</span></span>

<span data-ttu-id="9ba9f-113">*MixedReality* 은 동작 컨트롤러를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-113">*Microsoft.MixedReality.Input.MotionController* represents a motion controller.</span></span> <span data-ttu-id="9ba9f-114">각 *Motioncontroller* 인스턴스에는 *XR가 있습니다. WSA. InteractionSource* 피어-사용, 공급 업체 id, 제품 id 및 버전을 사용 하 여 상관 관계를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-114">Each *MotionController* instance has an *XR.WSA.Input.InteractionSource* peer, which can be correlated using handedness, vendor ID, product ID, and version.</span></span> 

<span data-ttu-id="9ba9f-115">*InteractionManager* events를 사용 하 여 새 *InteractionSource* 인스턴스를 검색 하는 것과 마찬가지로 *motioncontroller감시자* 를 만들고 해당 이벤트를 구독 하 여 motioncontroller 인스턴스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-115">You can grab MotionController instances by creating a *MotionControllerWatcher* and subscribing to its events, similar to using *InteractionManager* events to discover new *InteractionSource* instances.</span></span> <span data-ttu-id="9ba9f-116">MotionController의 메서드 및 속성은 해당 단추, 트리거, 2D 축 및 엄지 스틱을 포함 하 여 컨트롤러에서 지원 되는 입력을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-116">The MotionController’s methods and properties describe the inputs supported by the controller, including its buttons, triggers, 2D axis, and thumbstick.</span></span> <span data-ttu-id="9ba9f-117">또한 MotionController 클래스는 *Motioncontroller판독값* 클래스를 통해 입력 상태에 액세스 하는 메서드를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-117">The MotionController class also exposes methods for accessing input states through the *MotionControllerReading* class.</span></span> <span data-ttu-id="9ba9f-118">MotionControllerReading 클래스는 지정 된 시간에 컨트롤러 상태의 스냅숏을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-118">The MotionControllerReading class represents a snapshot of the controller’s state at a given time.</span></span> 

## <a name="installing-microsoftmixedrealityinput-using-the-unity-package-manager"></a><span data-ttu-id="9ba9f-119">Unity 패키지 관리자를 사용 하 여 MixedReality 설치</span><span class="sxs-lookup"><span data-stu-id="9ba9f-119">Installing Microsoft.MixedReality.Input using the Unity Package Manager</span></span> 

<span data-ttu-id="9ba9f-120">Unity 패키지 관리자는 [매니페스트 파일](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.js)을 사용 하 여 설치할 패키지와 설치할 수 있는 레지스트리 (서버)를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-120">The Unity Package Manager uses a [manifest file](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.json) to determine which packages to install and the registries (servers) they can be installed from.</span></span> <span data-ttu-id="9ba9f-121">MixedReality 패키지를 사용 하려면 먼저 혼합 현실 구성 요소 서버를 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-121">Before you can use the Microsoft.MixedReality.Input package, you'll need to register the Mixed Reality component server.</span></span>

### <a name="registering-the-mixed-reality-component-server"></a><span data-ttu-id="9ba9f-122">Mixed Reality 구성 요소 서버 등록</span><span class="sxs-lookup"><span data-stu-id="9ba9f-122">Registering the Mixed Reality component server</span></span> 

<span data-ttu-id="9ba9f-123">혼합 현실 입력 패키지를 사용 하는 각 프로젝트에 대해 패키지 폴더에 있는 파일의 manifest.js에는 혼합 현실 범위 레지스트리가 추가 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-123">For each project that will be using the Mixed Reality Input package, the manifest.json file (in the Packages folder) needs the Mixed Reality scoped registry added.</span></span> <span data-ttu-id="9ba9f-124">혼합 현실 지원에 대 한 manifest.js를 적절히 수정 하려면:</span><span class="sxs-lookup"><span data-stu-id="9ba9f-124">To properly modify manifest.json to support Mixed Reality:</span></span> 
    1. <span data-ttu-id="9ba9f-125"><projectRoot>Visual Studio Code와 같은 텍스트 편집기에서/Packages/manifest.js를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-125">Open <projectRoot>/Packages/manifest.json in a text editor, such as Visual Studio Code.</span></span> 
    2. <span data-ttu-id="9ba9f-126">매니페스트 파일의 맨 위에서 혼합 현실 서버를 범위가 지정 된 레지스트리 섹션에 추가 하 고 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-126">At the top of the manifest file, add the Mixed Reality server to the scoped registry section and save the file.</span></span> 
    
<pre>
{ 
  "scopedRegistries": [ 
    { 
      "name": "Microsoft Mixed Reality", 
      "url": "https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/", 
      "scopes": [ 
        "com.microsoft.mixedreality" 
      ] 
    } 
  ], 
</pre>

### <a name="adding-the-microsoftmixedrealityinput-package"></a><span data-ttu-id="9ba9f-127">MixedReality 패키지 추가</span><span class="sxs-lookup"><span data-stu-id="9ba9f-127">Adding the Microsoft.MixedReality.Input package</span></span> 

<span data-ttu-id="9ba9f-128"><projectRoot>텍스트 편집기에서 파일의/Packages/manifest.js종속성 섹션을 수정 하 여 mixedreality 패키지를 추가 하 고 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-128">Modify the dependencies section of the <projectRoot>/Packages/manifest.json file in the text editor to add com.microsoft.mixedreality.input package and save the file.</span></span> 

<pre>
  "dependencies": { 
    "com.microsoft.mixedreality.input": "0.9.2006", 
  }
</pre>

## <a name="using-microsoftmixedrealityinput"></a><span data-ttu-id="9ba9f-129">MixedReality 사용</span><span class="sxs-lookup"><span data-stu-id="9ba9f-129">Using Microsoft.MixedReality.Input</span></span> 

### <a name="input-values"></a><span data-ttu-id="9ba9f-130">입력 값</span><span class="sxs-lookup"><span data-stu-id="9ba9f-130">Input values</span></span>

<span data-ttu-id="9ba9f-131">MotionController는 두 종류의 입력을 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-131">A MotionController can expose two kinds of inputs:</span></span> 

* <span data-ttu-id="9ba9f-132">단추와 트리거 상태는 얼마나 누르는 지를 나타내는 0.0에서 1.0 사이의 고유한 부동 소수점 값으로 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-132">Buttons and trigger states are expressed by a unique float value between 0.0 and 1.0 that indicates how much they're pressed.</span></span>
    * <span data-ttu-id="9ba9f-133">트리거에서 0.0 (완전히 릴리스된)에서 1.0 (완전히 누름) 사이의 연속 값을 반환할 수 있는 동안에는 0.0 (누르지 않은 경우) 또는 1.0 (누른 경우)만 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-133">A button can only return 0.0 (when not pressed) or 1.0 (when pressed) while a trigger can return continuous values between 0.0 (fully released) to 1.0 (fully pressed).</span></span> 
* <span data-ttu-id="9ba9f-134">엄지 스틱 상태는 X 및 Y 구성 요소가-1.0 ~ 1.0 사이인 Vector2.x으로 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-134">Thumbstick state is expressed by a Vector2 whose X and Y components are between -1.0 and 1.0.</span></span> 

<span data-ttu-id="9ba9f-135">*Motioncontroller. Get보도 Sableinput ()* 을 사용 하 여 누름 값 (단추 및 트리거)을 반환 하는 입력 목록을 반환 하거나, *GetXYInputs ()* 메서드를 사용 하 여 2 축 값을 반환 하는 입력의 목록을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-135">You can use *MotionController.GetPressableInputs()* to return a list of inputs returning a pressed value (buttons and triggers) or the *MotionController.GetXYInputs()* method to return a list of inputs returning a 2-axis value.</span></span> 

<span data-ttu-id="9ba9f-136">MotionControllerReading 인스턴스는 지정 된 시간에 컨트롤러의 상태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-136">A MotionControllerReading instance represents the state of the controller at a given time:</span></span> 

* <span data-ttu-id="9ba9f-137">*Get보도 Sedvalue ()* 는 단추 또는 트리거의 상태를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-137">*GetPressedValue()* retrieves the state of a button or a trigger.</span></span> 
* <span data-ttu-id="9ba9f-138">*GetXYValue ()* 는 엄지 스틱 상태를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-138">*GetXYValue()* retrieves the state of a thumbstick.</span></span> 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a><span data-ttu-id="9ba9f-139">MotionController 인스턴스 및 해당 상태 컬렉션을 유지 관리 하는 캐시 만들기</span><span class="sxs-lookup"><span data-stu-id="9ba9f-139">Creating a cache to maintain a collection of MotionController instances and their states</span></span> 

<span data-ttu-id="9ba9f-140">먼저 MotionControllerWatcher를 인스턴스화하고 *Motioncontrollerwatcher* 및 *Motioncontrollerwatcher* 된 이벤트에 대 한 처리기를 등록 하 여 사용 가능한 motioncontroller 인스턴스의 캐시를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-140">Start by instantiating a MotionControllerWatcher and registering handlers for its *MotionControllerAdded* and *MotionControllerRemoved* events to keep a cache of available MotionController instances.</span></span> <span data-ttu-id="9ba9f-141">이 캐시는 다음 코드에서 보여 주는 것 처럼 GameObject에 연결 된 MonoBehavior 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-141">This cache should be a MonoBehavior attached to a GameObject as demonstrated in the following code:</span></span>

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

### <a name="reading-new-inputs-by-polling"></a><span data-ttu-id="9ba9f-142">폴링을 통해 새 입력 읽기</span><span class="sxs-lookup"><span data-stu-id="9ba9f-142">Reading new inputs by polling</span></span> 

<span data-ttu-id="9ba9f-143">MonoBehavior 클래스의 *Update* 메서드를 실행 하는 동안 *TryGetReadingAtTime* 를 통해 알려진 각 컨트롤러의 현재 상태를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-143">You can read the current state of each known controller through *MotionController.TryGetReadingAtTime* during the *Update* method of the MonoBehavior class.</span></span> <span data-ttu-id="9ba9f-144">*현재 날짜/시간* 을 타임 스탬프 매개 변수로 전달 하 여 컨트롤러의 최신 상태를 읽을 수 있도록 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-144">You want to pass *DateTime.Now* as the timestamp parameter to ensure that the latest state of the controller is read.</span></span> 

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

<span data-ttu-id="9ba9f-145">컨트롤러를 사용 하 여 현재 입력 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-145">You can grab the controllers current input value using the Handedness of the controller:</span></span> 

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

<span data-ttu-id="9ba9f-146">예를 들어 InteractionSource의 아날로그 값을 읽으려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-146">For example, to read the analog grasp value of an InteractionSource:</span></span> 

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

### <a name="generating-events-from-the-new-inputs"></a><span data-ttu-id="9ba9f-147">새 입력에서 이벤트 생성</span><span class="sxs-lookup"><span data-stu-id="9ba9f-147">Generating events from the new inputs</span></span> 

<span data-ttu-id="9ba9f-148">프레임당 한 번 컨트롤러의 상태를 폴링하는 대신 모든 상태 변경을 이벤트로 처리할 수 있습니다 .이 옵션을 사용 하면 프레임 보다 빨리 지속 되는 작업을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-148">Instead of polling for a controller's state once per frame, you have the option of handling all state changes as events, which lets you handle even the quickest actions lasting less than a frame.</span></span> <span data-ttu-id="9ba9f-149">이 접근 방식이 작동 하려면 동작 컨트롤러의 캐시가 마지막 프레임 이후 컨트롤러에서 게시 한 모든 상태를 처리 해야 합니다 .이 작업은 MotionController에서 검색 된 마지막 MotionControllerReading의 타임 스탬프를 저장 하 고 *motioncontroller. TryGetReadingAfterTime ()* 를 호출 하 여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-149">In order for this approach to work, the cache of motion controllers needs to process all states published by a controller since the last frame, which you can do by storing the timestamp of the last MotionControllerReading retrieved from a MotionController and calling *MotionController.TryGetReadingAfterTime()*:</span></span> 

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

<span data-ttu-id="9ba9f-150">캐시 내부 클래스를 업데이트 했으므로 MonoBehavior 클래스는 눌려진 두 이벤트를 노출 하 고, 해당 Update () 메서드에서이를 발생 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-150">Now that you've updated the cache internal classes, the MonoBehavior class can expose two events – Pressed and Released – and raise them from its Update() method:</span></span> 

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

<span data-ttu-id="9ba9f-151">위의 코드 예제에서 구조를 사용 하면 이벤트를 훨씬 더 쉽게 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba9f-151">The structure in the above code examples makes registering events much more readable:</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="9ba9f-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ba9f-152">See also</span></span>

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](../porting-apps/porting-guides.md?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](../porting-apps/porting-guides.md?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->