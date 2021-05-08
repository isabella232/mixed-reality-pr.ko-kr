---
title: HowToAddNearInteractivity
description: MRTK의 거의 상호 작용에 대 한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 거의 상호 작용,
ms.openlocfilehash: fc6fbb33e5a8e9aa6930f56f292f8ded51c53ff0
ms.sourcegitcommit: 0c717ed0043c7a65e2caf1452eb0f49059cdf154
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108644849"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a>MRTK에서 근접 한 상호 작용을 추가 하는 방법

거의 상호 작용은 접촉 및 가져와 형태로 제공 됩니다. 터치 및 잡기 이벤트는 각각 [Pokepointer](pointers.md#pokepointer) 및 [SpherePointer](pointers.md#spherepointer)에서 포인터 이벤트로 발생 합니다.

특정 GameObject에 대 한 터치 및/또는 입력 이벤트를 수신 대기 하려면 세 가지 주요 단계가 필요 합니다.

1. 관련 포인터가 기본 [Mrtk 구성 프로필](../../configuration/mixed-reality-configuration-guide.md)에 등록 되었는지 확인 합니다.
1. 원하는 GameObject에 적절 한 [잡기](#add-grab-interactions) 또는 [터치](#add-touch-interactions) 스크립트 구성 요소가 있는지 확인 합니다 [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .
1. 원하는 GameObject에 연결 된 스크립트에 대 한 입력 처리기 인터페이스를 구현 하 여 [잡기](#grab-code-example) 또는 [터치](#touch-code-example) 이벤트를 수신 대기 합니다.

## <a name="add-grab-interactions"></a>잡기 상호 작용 추가

1. [SpherePointer](pointers.md#spherepointer) 가 *Mrtk 포인터 프로필* 에 등록 되었는지 확인 합니다.

    기본 MRTK 프로필과 기본 HoloLens 2 프로필에는 이미 *SpherePointer* 이 포함 되어 있습니다. Mrtk 구성 프로필을 선택 하 고 **입력**  >  **포인터**  >  **포인터 옵션** 으로 이동 하 여 SpherePointer이 생성 되는지 확인할 수 있습니다. 기본 `GrabPointer` prefab (자산/m a s v k/SDK/Features/UX/Prefabs/포인터)는 *컨트롤러 유형의* *트레일러* 식으로 나열 되어야 합니다. 사용자 지정 prefab는 클래스를 구현 하는 동안 활용할 수 있습니다 [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) .

    ![잡기 포인터 프로필 예](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    기본 잡기 포인터는 기본 Hololens 2 인터페이스와 일치 하는 잡기 지점을 기준으로 원뿔의 인접 개체를 쿼리 합니다.

    ![원추형 잡기 포인터](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. Grabbable 해야 하는 GameObject에는 및 collider를 추가 합니다 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) .

    GameObject 계층이 grabbable 계층에 있는지 확인 합니다. 기본적으로 *공간 인식을* 제외한 모든 계층은 Grabbable *Raycasts를 무시* 합니다. *GrabPointer* Prefab에서 *잡기 계층 마스크* 를 검사 하 여 grabbable 된 레이어를 확인 합니다.

1. GameObject 또는 해당 상위 항목 중 하나에서 인터페이스를 구현 하는 스크립트 구성 요소를 추가 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) 합니다. 를 사용 하는 개체의 상위 항목은 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 포인터 이벤트도 받을 수 있습니다.

### <a name="grab-code-example"></a>잡기 코드 예제

다음은 이벤트가 터치 또는 잡기 인 경우 인쇄 되는 스크립트입니다. 관련 *IMixedRealityPointerHandler* interface 함수에서을 통해 해당 이벤트를 트리거하는 포인터의 형식을 확인할 수 있습니다 [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) . 포인터가 *SpherePointer* 인 경우 상호 작용은 잡기입니다.

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

## <a name="add-touch-interactions"></a>터치 상호 작용 추가

UnityUI 요소에 터치 상호 작용을 추가 하는 프로세스는 바닐라 3D Gameobject와 다릅니다. Unity ui 구성 요소를 사용 하도록 설정 하려면 다음 섹션인 *UNITY ui* 로 건너뛸 수 있습니다.

그러나 **두** 유형의 UX 요소 모두에 대해 *mrtk 포인터 프로필* 에 [pokepointer](pointers.md#pokepointer) 가 등록 되어 있는지 확인 합니다.

기본 MRTK 프로필과 기본 HoloLens 2 프로필은 이미 *Pokepointer* 를 포함 하 고 있습니다. Mrtk 구성 프로필을 선택 하 고 **입력**  >  **포인터**  >  **포인터 옵션** 으로 이동 하 여 pokepointer가 생성 되는지 확인할 수 있습니다. 기본 `PokePointer` (asset/MRTK/SDK/Features/UX/Prefabs/포인터) prefab는 *컨트롤러 유형의* *트레일러* 표시와 함께 나열 되어야 합니다. 사용자 지정 prefab는 클래스를 구현 하는 동안 활용할 수 있습니다 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) .

![Poke 포인터 프로필 예](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>3D Gameobject

3d 개체에 단일 touchable 평면이 포함 되어야 하는지 아니면 전체 collider를 기반으로 하 여 touchable 되어야 하는 경우에 따라 3D Gameobject에 터치 상호 작용을 추가 하는 두 가지 방법이 있습니다.
첫 번째 방법은 BoxColliders를 사용 하는 개체에 대 한 것 이며,이는 collider의 단일 면만 터치 이벤트에 대응 하는 것을 요구 합니다. 다른 하나는 collider를 기반으로 하는 모든 방향에서 touchable 해야 하는 개체에 대 한 것입니다.

### <a name="single-face-touch"></a>단일 얼굴 터치

이는 단일 얼굴을 touchable 해야 하는 경우에 유용 합니다. 이 옵션은 game 개체가 BoxCollider를가지고 있다고 가정 합니다. 비 BoxCollider 개체와 함께 사용할 수 있습니다 .이 경우 ' 경계 ' 및 ' 로컬 센터 ' 속성을 수동으로 설정 하 여 touchable 평면을 구성 합니다 (즉, 범위는 0이 아닌 값으로 설정 해야 함).

1. Touchable GameObject에서 BoxCollider 및 [ `NearInteractionTouchable` ] (f: NearInteractionTouchable) 구성 요소를 추가 합니다.

    1. 아래 구성 요소 스크립트에서 [] (f: MixedReality) 인터페이스를 사용 하 *는 경우에* 는 **이벤트를 Receive** 로 설정 `IMixedRealityTouchHandler` 합니다.

    1. **범위 수정** 및 **수정 센터** 를 클릭 합니다.

    ![NearInteractionTouchable 설정](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. 해당 개체 또는 해당 상위 항목 중 하나에서를 구현 하는 스크립트 구성 요소를 추가 합니다. [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   인터페이스입니다. [] (F: MixedReality NearInteractionTouchable)를 사용 하는 개체의 상위 항목 `NearInteractionTouchable` 은 포인터 이벤트도 받을 수 있습니다.

> [!NOTE]
> *NearInteractionTouchable* GameObject가 선택 된 편집기 장면 보기에서 흰색 윤곽선 사각형 및 화살표를 확인 합니다. 화살표는 touchable의 "front"를 가리킵니다. Collidable는 해당 방향 에서만 touchable 됩니다. 모든 방향에서 collider touchable을 만들려면 [임의 collider touch](#arbitrary-collider-touch)에 대 한 섹션을 참조 하세요.
> ![NearInteractionTouchable Gizmo 그리려면 ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>임의 collider touch

이는 게임 개체가 전체 collider 얼굴을 따라 touchable 해야 하는 경우에 유용 합니다. 예를 들어 SphereCollider를 사용 하 여 개체에 대 한 터치 상호 작용을 사용 하도록 설정 하는 데 사용할 수 있습니다. 여기서 전체 collider는 touchable 해야 합니다.

1. Touchable 해야 하는 GameObject에서 collider 및 a [ `NearInteractionTouchableVolume` ] (f: MixedReality) 구성 요소를 추가 합니다.

    1. 아래 구성 요소 스크립트에서 [] (f: MixedReality) 인터페이스를 사용 하 *는 경우에* 는 **이벤트를 Receive** 로 설정 `IMixedRealityTouchHandler` 합니다.

1. 해당 개체 또는 해당 상위 항목 중 하나에서를 구현 하는 스크립트 구성 요소를 추가 합니다. [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   인터페이스입니다. [] (F: MixedReality NearInteractionTouchable)를 사용 하는 개체의 상위 항목 `NearInteractionTouchable` 은 포인터 이벤트도 받을 수 있습니다.

### <a name="unity-ui"></a>Unity UI

1. 장면에 [Unityui 캔버스가](https://docs.unity3d.com/Manual/UICanvas.html) 있는지 추가/확인 합니다.

1. Touchable GameObject에서 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 구성 요소를 추가 합니다.  

    1. 아래 구성 요소 스크립트에서 인터페이스를 사용 하 *는 경우에* 는 **이벤트를 수신** 으로 설정 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 합니다.

1. 해당 개체 또는 해당 상위 항목 중 하나에서 인터페이스를 구현 하는 스크립트 구성 요소를 추가 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 합니다. 를 사용 하는 개체의 상위 항목은 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 포인터 이벤트도 받을 수 있습니다.

> [!IMPORTANT]
> 개체가 겹치는 캔버스 개체에 있는 경우 예상 대로 동작 하지 않을 수 있습니다. 일관 된 동작을 보장 하기 위해 장면에서 캔버스 개체를 겹치지 않도록 합니다.

> [!IMPORTANT]
> `NearInteractionTouchable`스크립트 구성 요소에서 속성 *이벤트를 수신 하려면* *포인터* 와 *터치* 라는 두 가지 옵션을 사용할 수 있습니다. 인터페이스  를 사용 하 고  [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)  [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 입력 이벤트를 응답/처리 하는 구성 요소 스크립트에서 인터페이스를 사용 하는 경우 터치로 설정 하려면 이벤트를 Receive로 설정 합니다.

#### <a name="touch-code-example"></a>터치 코드 예제

아래 코드는 변형 구성 요소를 사용 하 여 GameObject에 연결 하 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 고 터치식 입력 이벤트에 응답할 수 있는 MonoBehaviour를 보여 줍니다.

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

## <a name="near-interaction-script-examples"></a>거의 상호 작용 스크립트 예제

### <a name="touch-events"></a>터치 이벤트

이 예에서는 큐브를 만들고, touchable 하 고, 터치 시 색을 변경 합니다.

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

아래 예제에서는 GameObject를 끌기 가능 하 게 만드는 방법을 보여 줍니다. 게임 개체에 collider가 있는 것으로 가정 합니다.

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

## <a name="see-also"></a>참고 항목

* [입력 개요](overview.md)
* [포인터](pointers.md)
* [입력 이벤트](input-events.md)
