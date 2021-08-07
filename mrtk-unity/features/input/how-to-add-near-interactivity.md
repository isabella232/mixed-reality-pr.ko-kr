---
title: 근접 대화형 작업을 추가하는 방법
description: MRTK의 근거리 상호 작용에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 근사 상호 작용,
ms.openlocfilehash: 174623ebf340e800848c15e22dc2299aaf997b484a1329d67c28540acd79515a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212599"
---
# <a name="how-to-add-near-interactivity"></a>근접 대화형 작업을 추가하는 방법

가까운 상호 작용은 터치와 잡기의 형태로 제공됩니다. 터치 및 잡기 이벤트는 각각 [SpherePointer](pointers.md#pokepointer) 및 [SpherePointer에](pointers.md#spherepointer)의해 포인터 이벤트로 발생합니다.

특정 GameObject에서 터치 및/또는 입력 이벤트를 수신 대기하려면 세 가지 주요 단계가 필요합니다.

1. 관련 포인터가 기본 [MRTK 구성 프로필](../../configuration/mixed-reality-configuration-guide.md)에 등록되어 있는지 확인합니다.
1. 원하는 GameObject에 적절한 [잡기](#add-grab-interactions) 또는 [터치](#add-touch-interactions) 스크립트 구성 요소 및 가 있는지 [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) 확인합니다.
1. 연결된 스크립트에서 원하는 GameObject에 대한 입력 처리기 인터페이스를 구현하여 [잡기](#grab-code-example) 또는 [터치](#touch-code-example) 이벤트를 수신 대기합니다.

## <a name="add-grab-interactions"></a>잡기 상호 작용 추가

1. [SpherePointer가](pointers.md#spherepointer) *MRTK 포인터 프로필* 에 등록되어 있는지 확인합니다.

    기본 MRTK 프로필 및 기본 HoloLens 2 프로필에는 *이미 SpherePointer 가* 포함되어 있습니다. MRTK 구성 프로필을 선택하고 **입력** 포인터 포인터 옵션 으로 이동하여 SpherePointer가 생성될지 확인할 수  >    >  **있습니다.** 기본 `GrabPointer` 프리팹(Assets/MRTK/SDK/Features/UX/Prefabs/Pointers)은 *컨트롤러 형식의* *굴절형 와* 함께 나열되어야 합니다. 사용자 지정 프리팹은 클래스를 구현하는 한 활용할 수 [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) 있습니다.

    ![Grab 포인터 프로필 예제](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    기본 잡기 포인터는 기본 Hololens 2 인터페이스와 일치하도록 잡기 지점 주위의 원두에 있는 주변 개체를 쿼리합니다.

    ![원통형 잡기 포인터](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. 잡기 가능해야 하는 GameObject에서 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) , 충돌체를 추가합니다.

    GameObject의 계층이 잡기 가능한 계층에 있는지 확인합니다. 기본적으로 *공간 인식* 및 Raycast 무시를 제외한 모든 계층은 잡기가 *가능합니다.* *GrabPointer* 프리팹에서 잡기 계층 마스크를 검사하여 잡기 가능한 *레이어를 확인합니다.*

1. GameObject 또는 해당 상위 항목 중 하나에서 인터페이스를 구현하는 스크립트 구성 요소를 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) 추가합니다. 를 가진 개체의 모든 상위 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 항목은 포인터 이벤트도 받을 수 있습니다.

### <a name="grab-code-example"></a>코드 잡기 예제

다음은 이벤트가 터치 또는 잡기인 경우 인쇄되는 스크립트입니다. 관련 *IMixedRealityPointerHandler* 인터페이스 함수에서 을 통해 해당 이벤트를 트리거하는 포인터 형식을 확인할 수 [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) 있습니다. 포인터가 *SpherePointer* 이면 상호 작용은 잡기입니다.

```c#
public class PrintPointerEvents : MonoBehaviour, IMixedRealityPointerHandler
{
    public void OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.Pointer is SpherePointer)
        {
            Debug.Log($"Grab start from {eventData.Pointer.PointerName}");
        }
        if (eventData.Pointer is PokePointer)
        {
            Debug.Log($"Touch start from {eventData.Pointer.PointerName}");
        }
    }

    public void OnPointerClicked(MixedRealityPointerEventData eventData) {}
    public void OnPointerDragged(MixedRealityPointerEventData eventData) {}
    public void OnPointerUp(MixedRealityPointerEventData eventData) {}
}
```

## <a name="add-touch-interactions"></a>터치 조작 추가

UnityUI 요소에 터치 상호 작용을 추가하는 프로세스는 vanilla 3D GameObjects와 다릅니다. Unity UI 구성 요소를 사용하도록 설정하려면 *Unity UI* 섹션으로 건너뛸 수 있습니다.

**그러나 두** 가지 유형의 UX 요소 모두에 대해, *MrTK 포인터 프로필* 에 [UxPointer가](pointers.md#pokepointer) 등록되어 있는지 확인합니다.

기본 MRTK 프로필 및 기본 HoloLens 2 프로필은 이미 *을* 포함합니다. MRTK 구성 프로필을 선택하고 **입력** 포인터 포인터 옵션 으로 이동하여 사용자  >  **지정자가** 생성될지 확인할 수  >  **있습니다.** `PokePointer`기본(Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) 프리팹은 *컨트롤러 형식의* *조인된 손* 으로 나열되어야 합니다. 사용자 지정 프리팹은 클래스를 구현하는 한 활용할 수 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 있습니다.

![3차원 포인터 프로필 예제](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>3D GameObjects

3D 개체에 터치 가능한 평면이 하나만 있어야 하는지 또는 전체 충돌체를 기반으로 터치 가능해야 하는지에 따라 3D GameObject에 터치 상호 작용을 추가하는 두 가지 방법이 있습니다.
첫 번째 방법은 일반적으로 BoxColliders가 있는 개체에 있으며, 여기서 충돌체의 단일 얼굴만 터치 이벤트에 반응하도록 합니다. 다른 하나는 충돌체를 기반으로 모든 방향에서 터치할 수 있어야 하는 개체에 대한 것입니다.

### <a name="single-face-touch"></a>단일 얼굴 터치

이 방법은 하나의 얼굴만 터치할 수 있어야 하는 상황을 활성화하는 데 유용합니다. 이 옵션은 게임 개체에 BoxCollider가 있다고 가정합니다. BoxCollider가 아닌 개체와 함께 사용할 수 있습니다. 이 경우 '경계' 및 '로컬 센터' 속성을 수동으로 설정하여 터치 가능한 평면을 구성합니다(즉, 경계를 0이 아닌 값으로 설정해야 합니다).

1. 터치 가능해야 하는 GameObject에서 BoxCollider 및 [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit 추가합니다. Input.NearInteractionTouchable) 구성 요소입니다.

    1. [ ] (xref:Microsoft.MixedReality.Toolkit 사용하는 경우 이벤트를 *Touch로* **수신으로** `IMixedRealityTouchHandler` 설정합니다. 아래 구성 요소 스크립트의 Input.IMixedRealityTouchHandler) 인터페이스입니다.

    1. **범위 수정** 및 **센터 수정을** 클릭합니다.

    ![NearInteractionTouchable 설정](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. 해당 개체 또는 상위 항목 중 하나에서 를 구현하는 스크립트 구성 요소를 추가합니다. [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   인터페이스입니다. [ `NearInteractionTouchable` ](xref:Microsoft.MixedReality.Toolkit 개체의 모든 상위 항목입니다. Input.NearInteractionTouchable)은 포인터 이벤트도 받을 수 있습니다.

> [!NOTE]
> *NearInteractionTouchable* GameObject가 선택된 편집기 장면 보기에서 흰색 윤곽선 사각형과 화살표를 확인합니다. 화살표는 터치 가능한 의 "전면"을 가리킵니다. 충돌 가능 은 해당 방향에서만 터치할 수 있습니다. 모든 방향에서 충돌자를 터치할 수 있도록 하려면 [임의 충돌자 터치에 대한 섹션을 참조하세요.](#arbitrary-collider-touch)
> ![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>임의 충돌자 터치

이는 전체 충돌체 얼굴을 따라 게임 개체를 터치할 수 있어야 하는 상황을 활성화하는 데 유용합니다. 예를 들어 전체 충돌체를 터치할 수 있어야 하는 SphereCollider를 사용하여 개체에 대한 터치 상호 작용을 사용하도록 설정하는 데 사용할 수 있습니다.

1. 터치 가능해야 하는 GameObject에서 충돌체 및 [ `NearInteractionTouchableVolume` ](xref:Microsoft.MixedReality.Toolkit 추가합니다. Input.NearInteractionTouchableVolume) 구성 요소입니다.

    1. [ ] (xref:Microsoft.MixedReality.Toolkit 사용하는 경우 이벤트를 *Touch로* **수신으로** `IMixedRealityTouchHandler` 설정합니다. 아래 구성 요소 스크립트의 Input.IMixedRealityTouchHandler) 인터페이스입니다.

1. 해당 개체 또는 상위 항목 중 하나에서 를 구현하는 스크립트 구성 요소를 추가합니다. [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   인터페이스입니다. [ `NearInteractionTouchable` ](xref:Microsoft.MixedReality.Toolkit 개체의 모든 상위 항목입니다. Input.NearInteractionTouchable)은 포인터 이벤트도 받을 수 있습니다.

### <a name="unity-ui"></a>Unity UI

1. 장면에 [UnityUI 캔버스가](https://docs.unity3d.com/Manual/UICanvas.html) 있는지 추가/확인합니다.

1. 터치 가능해야 하는 GameObject에서 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 구성 요소를 추가합니다.  

    1. 아래 구성 요소 스크립트에서 인터페이스를 사용하는 경우 **이벤트를 Receive** to *Touch로* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 설정합니다.

1. 해당 개체 또는 해당 상위 항목 중 하나에서 인터페이스를 구현하는 스크립트 구성 요소를 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 추가합니다. 를 가진 개체의 모든 상위 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 항목은 포인터 이벤트도 받을 수 있습니다.

> [!IMPORTANT]
> 개체가 겹치는 캔버스 개체에 있는 경우 예상대로 동작하지 않을 수 있습니다. 일관된 동작을 보장하려면 장면에서 캔버스 개체를 겹치지 마세요.

> [!IMPORTANT]
> 스크립트 `NearInteractionTouchable` 구성 요소에서 *Events to Receive* 속성에는 *Pointer* 및 *Touch의* 두 가지 옵션이 있습니다. 인터페이스를 사용하는 경우 이벤트를 *포인터로* *수신으로* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) 설정하고 입력 이벤트를 응답/처리하는 구성 요소 스크립트에서 인터페이스를 사용하는 경우 *Touch로* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 설정합니다.

#### <a name="touch-code-example"></a>터치 코드 예제

아래 코드에서는 변형 구성 요소를 사용하여 GameObject에 연결하고 터치 입력 이벤트에 응답할 수 있는 MonoBehaviour를 보여 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 드립니다.

```c#
public class TouchEventsExample : MonoBehaviour, IMixedRealityTouchHandler
{
    public void OnTouchStarted(HandTrackingInputEventData eventData)
    {
        string ptrName = eventData.Pointer.PointerName;
        Debug.Log($"Touch started from {ptrName}");
    }
    public void OnTouchCompleted(HandTrackingInputEventData eventData) {}
    public void OnTouchUpdated(HandTrackingInputEventData eventData) { }
}
```

## <a name="near-interaction-script-examples"></a>근 상호 작용 스크립트 예제

### <a name="touch-events"></a>터치 이벤트

이 예제에서는 큐브를 만들고, 큐브를 터치 가능하게 만들고, 터치 시 색을 변경합니다.

```c#
public static void MakeChangeColorOnTouch(GameObject target)
{
    // Add and configure the touchable
    var touchable = target.AddComponent<NearInteractionTouchableVolume>();
    touchable.EventsToReceive = TouchableEventType.Pointer;

    var material = target.GetComponent<Renderer>().material;
    // Change color on pointer down and up
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) => material.color = Color.green);
    pointerHandler.OnPointerUp.AddListener((e) => material.color = Color.magenta);
}
```

### <a name="grab-events"></a>이벤트 잡기

아래 예제에서는 GameObject를 끌 수 있도록 하는 방법을 보여 주세요. 게임 개체에 충돌체가 있다고 가정합니다.

```c#
public static void MakeNearDraggable(GameObject target)
{
    // Instantiate and add grabbable
    target.AddComponent<NearInteractionGrabbable>();

    // Add ability to drag by re-parenting to pointer object on pointer down
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = ((SpherePointer)(e.Pointer)).transform;
        }
    });
    pointerHandler.OnPointerUp.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = null;
        }
    });
}
```

## <a name="useful-apis"></a>유용한 API

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a>추가 정보

* [입력 개요](overview.md)
* [포인터](pointers.md)
* [입력 이벤트](input-events.md)
