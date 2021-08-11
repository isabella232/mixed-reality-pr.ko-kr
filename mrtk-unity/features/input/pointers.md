---
title: 포인터
description: MRTK의 포인터에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 포인터,
ms.openlocfilehash: 9fec02e7866aaf867c7145491bfd84f727e039cdd7a4323ace9c65f74e49480a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191018"
---
# <a name="pointers"></a>포인터

![포인터](../images/pointers/MRTK_Pointer_Main.png)

이 문서에서는 [포인터 아키텍처와](../../architecture/controllers-pointers-and-focus.md) 비교하여 실제로 포인터 입력을 구성하고 응답하는 방법을 설명합니다.

포인터는 새 컨트롤러가 검색될 때 런타임에 자동으로 인스턴스화됩니다. 컨트롤러에 두 개 이상의 포인터를 연결할 수 있습니다. 예를 들어 기본 포인터 프로필을 사용하여 Windows Mixed Reality 컨트롤러는 표준 선택 및 원격 보고에 대한 선과 매개변 포인터를 모두 얻습니다.

## <a name="pointer-configuration"></a>포인터 구성

포인터는 를 통해 MRTK에서 입력 시스템의 일부로 [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile) 구성됩니다. 이 유형의 프로필은 [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) MRTK 구성 검사기의 에 할당됩니다. 포인터 프로필은 커서, 런타임에 사용할 수 있는 포인터 유형 및 해당 포인터가 서로 통신하여 활성 상태인지 결정하는 방법을 결정합니다.

- *포인팅 익스텐트* - 포인터가 GameObject와 상호 작용할 수 있는 최대 거리를 정의합니다.

- *포인팅 광선 캐스트 계층 마스크* - 지정된 포인터가 상호 작용할 수 있는 가능한 GameObject 및 시도할 상호 작용 순서를 결정하는 LayerMasks의 우선 순위가 지정된 배열입니다. 이는 포인터가 다른 장면 개체 앞에 먼저 UI 요소와 상호 작용하도록 하는 데 유용할 수 있습니다.
![포인터 프로필 예제](../images/input/pointers/PointerProfile.PNG)

### <a name="pointer-options-configuration"></a>포인터 옵션 구성

기본 MRTK 포인터 프로필 구성에는 다음 포인터 클래스 및 연결된 프리팹이 기본적으로 포함됩니다. 런타임 시 시스템에서 사용할 수 있는 포인터 목록은 포인터 프로필의 *포인터 옵션* 아래에 정의됩니다. 개발자는 이 목록을 활용하여 기존 포인터를 다시 구성하거나, 새 포인터를 추가하거나, 포인터를 삭제할 수 있습니다.

![포인터 옵션 프로필 예제](../images/input/pointers/PointerOptionsProfile.PNG)

각 포인터 항목은 다음 데이터 집합으로 정의됩니다.

- *컨트롤러 유형* - 포인터가 유효한 컨트롤러 집합입니다.
  - 예를 *들어,* 은(는) 손가락으로 개체를 "poking"하는 역할을 하며, 기본적으로 은(는) 굴절형 손 컨트롤러 유형만 지원하는 것으로 표시됩니다. 포인터는 컨트롤러를 사용할 수 있게 될 때만 인스턴스화되며, 특히 *컨트롤러 형식은* 이 포인터 프리팹을 만들 수 있는 컨트롤러를 정의합니다.

- *손수* - 특정 손(왼쪽/오른쪽)에 대해서만 포인터를 인스턴스화할 수 있습니다.

> [!NOTE]
> 포인터 항목의 *Handedness* 속성을 *None으로* 설정하면 해당 포인터를 목록에서 제거하는 대신 시스템에서 효과적으로 비활성화됩니다.

- *포인터 프리팹* - 지정된 컨트롤러 유형과 일치하는 컨트롤러 및 전달이 추적되기 시작하면 이 프리팹 자산이 인스턴스화됩니다.

컨트롤러와 연결된 여러 포인터가 있을 수 있습니다. 예를 들어 `DefaultHoloLens2InputSystemProfile` (Assets/MRTK/SDK/Profiles/HoloLens2/)에서 연결된 손 컨트롤러는 *,GrabPointer* 및 *DefaultControllerPointer(즉,* 손 광선).

> [!NOTE]
> MRTK는 *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers에 포인터 프리팹 집합을* 제공합니다. 새 사용자 지정 프리팹은 *Assets/MRTK/SDK/Features/UX/Scripts/Pointers* 또는 를 구현하는 다른 스크립트의 포인터 스크립트 중 하나를 포함하는 한 빌드할 수 [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer) 있습니다.

### <a name="default-pointer-classes"></a>기본 포인터 클래스

다음 클래스는 위에서 설명한 기본 *MRTK 포인터 프로필에서* 사용할 수 있고 정의된 기본 MRTK 포인터입니다. *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers* 아래에 제공된 각 포인터 프리팹에는 연결된 포인터 구성 요소 중 하나가 포함됩니다.

![MRTK 기본 포인터](../images/input/pointers/MRTK_Pointers.png)

#### <a name="far-pointers"></a>원거리 포인터

##### [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer)

 기본 포인터 클래스인 *LinePointer는* 포인터 방향으로 입력 소스(즉, 컨트롤러)에서 선을 그리고 이 방향으로 단일 광선 캐스트를 지원합니다. 일반적으로 및 원격 포트 포인터와 같은 자식 [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 클래스는 주로 공통 기능을 제공하는 이 클래스 대신 인스턴스화되고 활용됩니다(또한 원격 이동이 종료되는 위치를 나타내는 선을 그립니다).

Oculus, Vive 및 Windows Mixed Reality 같은 모션 컨트롤러의 경우 회전이 컨트롤러의 회전과 일치합니다. HoloLens 2 굴절형 손과 같은 다른 컨트롤러의 경우 회전은 시스템에서 제공하는 손의 포인팅 자세와 일치합니다.

<img src="../images/pointers/MRTK_Pointers_Line.png" width="400" alt="MRTK Pointer Line">

##### [`CurvePointer`](xref:Microsoft.MixedReality.Toolkit.Input.CurvePointer)

*CurvePointer는* 곡선을 따라 다단계 광선 캐스트를 허용하여 *LinePointer* 클래스를 확장합니다. 이 기본 포인터 클래스는 선이 일관되게 포아볼라로 변하는 원격 보고 포인터와 같은 곡선 인스턴스에 유용합니다.

##### [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer)

에서 확장되는 *ShellHandRayPointer의* [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer) 구현은 *MRTK 포인터 프로필* 의 기본값으로 사용됩니다. *DefaultControllerPointer* 프리팹은 [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 클래스를 구현합니다.

##### [`GGVPointer`](xref:Microsoft.MixedReality.Toolkit.Input.GGVPointer)

*GGV(응시/제스처/음성)* 포인터라고도 하는 GGVPointer는 주로 응시 및 에어 탭 또는 응시 및 음성 선택 상호 작용을 통해 HoloLens 1 스타일 모양과 탭 상호 작용을 제공합니다. GGV 포인터의 위치와 방향은 헤드의 위치와 회전에 의해 구동됩니다.

##### [`TouchPointer`](xref:Microsoft.MixedReality.Toolkit.Input.TouchPointer)

*TouchPointer는* Unity Touch 입력(즉, 터치 스크린)을 사용합니다. 화면을 터치하는 동작이 카메라에서 장면의 잠재적으로 먼 위치로 광선을 캐스팅하기 때문에 이러한 동작은 '원거리 상호 작용'입니다.

##### [`MousePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer)

*MousePointer는* 원거리 상호 작용이 아니라 터치 대신 마우스에 대한 세계 광선 캐스팅에 화면을 제공합니다.

![마우스 포인터](../images/pointers/MRTK_MousePointer.png)

> [!NOTE]
> 마우스 지원은 MRTK에서 기본적으로 사용할 수 없지만 MRTK 입력 프로필에 형식의 새 *입력 Data Provider* 추가하고 를 [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) 데이터 공급자에 할당하여 사용하도록 설정할 수 [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) 있습니다.

#### <a name="near-pointers"></a>Near 포인터

##### [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)

*[을](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* 사용하여 "근거리 상호 작용 터치 가능"을 지원하는 게임 개체와 상호 작용합니다. 연결된 스크립트가 있는 GameObject입니다. [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) UnityUI의 경우 이 포인터는 NearInteractionTouchableUnityUI를 찾습니다.  이 SpherePointer는 SphereCast를 사용하여 가장 가까운 터치 가능한 요소를 확인하고 누를 수 있는 단추와 같은 요소의 전원을 켜는 데 사용됩니다.

 구성 요소를 사용하여 GameObject를 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 구성할 때는 단추 앞이나 터치 가능해야 하는 다른 개체를 가리키도록 *localForward* 매개 변수를 구성해야 합니다. 또한 터치 가능 개체의 *경계가* 터치 가능한 개체의 범위와 일치하는지 확인합니다.

유용한 포인터 포인터 속성:

- *TouchableDistance:* 터치 가능한 표면과 상호 작용할 수 있는 최대 거리
- *시각적 개체:* 손가락 끝 시각적 개체(기본적으로 손가락의 링)를 렌더링하는 데 사용되는 게임 개체입니다.
- *선:* 손끝에서 활성 입력 표면으로 그리는 선택적 선입니다.
- *계층 마스크* - 포인터가 상호 작용할 수 있는 가능한 GameObject 및 시도할 상호 작용 순서를 결정하는 LayerMasks의 우선 순위가 지정되는 배열입니다. GameObject에는 `NearInteractionTouchable` pointer 포인터와 상호 작용하기 위한 구성 요소도 있어야 합니다.

<img src="../images/pointers/MRTK_PokePointer.png" width="400" alt="Poke Pointer">

##### [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)

*[SpherePointer는](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* [UnityEngine.Physics.OverlapSphere를](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html) 사용하여 상호 작용에 가장 가까운 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 개체를 식별합니다. 이 개체는 와 같은 "잡기 가능한" 입력에 `ManipulationHandler` 유용합니다. [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) / [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 기능 쌍과 마찬가지로, Sphere 포인터와 상호 작용하려면 게임 개체에 스크립트인 구성 요소가 포함되어야 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 합니다.

<img src="../images/pointers/MRTK_GrabPointer.jpg" width="400" alt="Grab Pointer">

유용한 Sphere 포인터 속성:

- *구 캐스트 반경:* 잡기 가능한 개체를 쿼리하는 데 사용되는 구의 반지름입니다.
- *근거리 개체 여백:* 개체가 포인터 근처에 있는지 검색하기 위해 쿼리할 구 캐스트 반경 위쪽의 거리입니다. 총 근 개체 감지 반경은 구 캐스트 반지름 + 근 개체 여백입니다.
- *근사 개체 섹터 각도:* 주변 개체를 쿼리하기 위한 포인터의 앞으로 축을 중심으로 하는 각도입니다. 쿼리 `IsNearObject` 함수를 원추형처럼 만듭니다. Hololens 2 동작과 일치하도록 기본적으로 66도로 설정됩니다.

![정방향 개체에 대해서만 쿼리하도록 수정된 구 포인터](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

- *Near Object Smoothing Factor:* Near Object 검색을 위한 다듬기 요소입니다. 개체가 근거리 개체 반경에서 검색되면 쿼리된 반지름이 근거리 개체 반경 *(1 + 근거리 개체 다듬기 비율)이 되어 민감도를 줄이고 개체가 검색 범위를 벗어나기 어렵게 만듭니다.
- *잡기 레이어 마스크* - 포인터가 상호 작용할 수 있는 가능한 GameObject 및 시도할 상호 작용 순서를 결정하는 우선 순위가 지정되는 LayerMask 배열입니다. GameObject에는 `NearInteractionGrabbable` SpherePointer와 상호 작용하는 도 있어야 합니다.
    > [!NOTE]
    > 공간 인식 계층은 MRTK에서 제공하는 기본 GrabPointer 프리팹에서 사용하지 않도록 설정됩니다. 이렇게 하면 공간 메시를 사용하여 구 겹치는 쿼리를 수행할 때 성능에 미치는 영향을 줄일 수 있습니다. GrabPointer 프리팹을 수정하여 이를 사용하도록 설정할 수 있습니다.
- *FOV에 없는 충돌체 무시* - 포인터 근처에 있을 수 있지만 실제로는 시각적 개체 FOV에 없는 충돌체를 무시할지 여부입니다.
이렇게 하면 실수로 잡기를 방지할 수 있으며, 잡기 가능에 가까울 수 있지만 볼 수 없는 경우 손 광선을 켤 수 있습니다. *Visual FOV는* 성능상의 이유로 일반적인 frustum 대신 원추형을 통해 정의됩니다. 이 원추는 반경이 반자 표시 높이(또는 세로 FOV)와 동일한 카메라의 frustum과 같이 가운데에 맞춰지고 방향을 지정합니다.

<img src="../images/input/pointers/SpherePointer_VisualFOV.png" width="200" alt="Sphere Pointer">

#### <a name="teleport-pointers"></a>Teleport 포인터

- [`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) 는 작업이 수행될 때 원격 포트 요청을 발생합니다(즉, 사용자를 이동하려면 원격 포트 단추를 눌렀습니다.)
- [`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) 는 작업이 수행될 때 원격 포트 요청을 발생합니다(즉, 사용자를 이동하기 위해 포라볼릭 선 raycast를 사용하여 원격 포트 단추를 눌렀습니다.

<img src="../images/pointers/MRTK_Pointers_Parabolic.png" width="400" alt="Pointer Parabolic">

## <a name="pointer-support-for-mixed-reality-platforms"></a>혼합 현실 플랫폼에 대한 포인터 지원

다음 표에서는 MRTK의 공통 플랫폼에 일반적으로 사용되는 포인터 형식에 대해 자세히 설명합니다. 참고: 이러한 플랫폼에 다른 포인터 형식을 추가할 수 있습니다. 예를 들어 Vr에 Sphere 포인터 또는 Sphere 포인터를 추가할 수 있습니다. 또한 게임 패드가 있는 VR 디바이스는 GGV 포인터를 사용할 수 있습니다.

|       포인터              | OpenVR  | Windows Mixed Reality | HoloLens 1 | HoloLens 2 |
|---------------------|---------|-----------------------|------------|------------|
| ShellHandRayPointer | Valid   | Valid                 |            | Valid      |
| TeleportPointer     | Valid   | Valid                 |            |            |
| GGVPointer          |         |                       | Valid      |            |
| SpherePointer       |         |                       |            | Valid      |
| PokePointer         |         |                       |            | Valid      |

## <a name="pointer-interactions-via-code"></a>코드를 통한 포인터 상호 작용

### <a name="pointer-event-interfaces"></a>포인터 이벤트 인터페이스

다음 인터페이스 중 하나 이상을 구현 하 고를 사용 하 여 GameObject에 할당 된 MonoBehaviours는 `Collider` 연결 된 인터페이스에서 정의 된 대로 포인터 상호 작용 이벤트를 수신 합니다.

| 이벤트 | Description | Handler |
| --- | --- | --- |
| 포커스 변경/포커스가 변경 되기 전에 | 포커스가 손실 되는 게임 개체와 포인터가 포커스를 변경할 때마다 발생 합니다. | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) |
포커스 입력/종료 | 첫 번째 포인터가 포커스를 벗어나면 마지막 포인터가 포커스를 잃을 때 포커스를 얻는 게임 개체에서 발생 합니다. | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler)
포인터 아래로/아래로/위로/클릭 | 보고서 포인터를 끌어서 놓으면 발생 합니다. | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)
터치 시작/업데이트 됨/완료 됨 | 터치 활동을 보고 하는 것과 같은 터치 인식 포인터에 의해 발생 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 합니다. | [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)

> [!NOTE]
> [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) 및는 발생 하는 [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) 개체에서 처리 되어야 합니다. 포커스 이벤트를 전역적으로 받을 수 있지만 다른 입력 이벤트와 달리 전역 이벤트 처리기는 포커스를 기준으로 이벤트 수신을 차단 하지 않습니다 (이벤트는 전역 처리기와 포커스의 해당 개체에서 수신 됨).

#### <a name="pointer-input-events-in-action"></a>작업 중인 포인터 입력 이벤트

포인터 입력 이벤트는 [일반 입력 이벤트](input-events.md#input-events-in-action)와 비슷한 방식으로 MRTK 입력 시스템에서 인식 되 고 처리 됩니다. 포인터 입력 이벤트는 입력 이벤트를 발생 시킨 포인터 뿐만 아니라 전역 입력 처리기에의 한 GameObject만 처리 됩니다. 일반 입력 이벤트는 모든 활성 포인터에 대해 Gameobject에 의해 처리 됩니다.

1. MRTK 입력 시스템에서 입력 이벤트를 인식 했습니다.
1. MRTK 입력 시스템은 등록 된 모든 전역 입력 처리기에 입력 이벤트에 대 한 관련 인터페이스 함수를 발생 시킵니다.
1. 입력 시스템은 이벤트를 발생 시킨 포인터에 대해 포커스가 있는 GameObject를 결정 합니다.
    1. 입력 시스템은 [Unity의 이벤트 시스템](https://docs.unity3d.com/Manual/EventSystem.html) 을 활용 하 여 포커스가 있는 GameObject에서 일치 하는 모든 구성 요소에 대해 관련 인터페이스 함수를 실행 합니다.
    1. 어떤 지점에서 든 입력 이벤트가 사용 된 것으로 [표시](input-events.md#how-to-stop-input-events)되 면 프로세스가 종료 되 고 추가 gameobject가 콜백을 수신할 수 없습니다.
        - 예: 인터페이스를 구현 하는 구성 요소는 [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) GameObject의 이득을 검색 하거나 포커스를 잃을 수 있습니다.
        - 참고: 현재 GameObject에서 원하는 인터페이스와 일치 하는 구성 요소가 없는 경우 Unity 이벤트 시스템은 부모 GameObject를 검색 하기 위해 버블링 됩니다.
1. 전역 입력 처리기를 등록 하지 않고 일치 하는 구성 요소/인터페이스를 사용 하 여 GameObject를 찾을 수 없는 경우 입력 시스템은 각 대체 등록 된 입력 처리기를 호출 합니다.

#### <a name="example"></a>예제

다음은 포인터가 포커스를 하거나 포커스를 벗어나거나 포인터가 개체를 선택할 때 연결 된 렌더러의 색을 변경 하는 예제 스크립트입니다.

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    private Color color_IdleState = Color.cyan;
    private Color color_OnHover = Color.white;
    private Color color_OnSelect = Color.blue;
    private Material material;

    private void Awake()
    {
        material = GetComponent<Renderer>().material;
    }

    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }

    void IMixedRealityPointerHandler.OnPointerDown(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerDragged(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
    {
        material.color = color_OnSelect;
    }
}
```

### <a name="query-pointers"></a>쿼리 포인터

사용 가능한 입력 소스를 반복 하 여 현재 활성화 된 모든 포인터를 수집할 수 있습니다 (즉, 연결 된 포인터를 검색 하는 데 사용할 수 있는 컨트롤러 및 입력

```c#
var pointers = new HashSet<IMixedRealityPointer>();

// Find all valid pointers
foreach (var inputSource in CoreServices.InputSystem.DetectedInputSources)
{
    foreach (var pointer in inputSource.Pointers)
    {
        if (pointer.IsInteractionEnabled && !pointers.Contains(pointer))
        {
            pointers.Add(pointer);
        }
    }
}
```

#### <a name="primary-pointer"></a>기본 포인터

개발자는 포커스의 기본 포인터가 변경 될 때 알림을 받도록 FocusProviders PrimaryPointerChanged 이벤트를 구독할 수 있습니다. 이는 사용자가 현재 응시를 통해 장면 또는 손 모양 또는 다른 입력 소스와 상호 작용 하 고 있는지 확인 하는 데 매우 유용할 수 있습니다.

```c#
private void OnEnable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.SubscribeToPrimaryPointerChanged(OnPrimaryPointerChanged, true);
}

private void OnPrimaryPointerChanged(IMixedRealityPointer oldPointer, IMixedRealityPointer newPointer)
{
    ...
}

private void OnDisable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.UnsubscribeFromPrimaryPointerChanged(OnPrimaryPointerChanged);

    // This flushes out the current primary pointer
    OnPrimaryPointerChanged(null, null);
}
```

`PrimaryPointerExample`(자산/m a RTK/예제/데모/입력/장면/PrimaryPointer) 장면에서는 이벤트에 대해를 사용 하 여 [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) 새 기본 포인터에 응답 하는 방법을 보여 줍니다.

<img src="../images/pointers/PrimaryPointerExample.png" style="max-width:100%;" alt="Primary Pointer Example">

### <a name="pointer-result"></a>포인터 결과

포인터 속성에는 [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) 포커스가 있는 개체를 확인 하는 데 사용 되는 장면 쿼리의 현재 결과가 포함 됩니다. 동작 컨트롤러에 대해 기본적으로 생성 된 것과 같은 raycast 포인터의 경우, 입력 및 손 광선의 위치와 정상적인 위치를 포함 합니다.

```c#
private void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
{
    var result = eventData.Pointer.Result;
    var spawnPosition = result.Details.Point;
    var spawnRotation = Quaternion.LookRotation(result.Details.Normal);
    Instantiate(MyPrefab, spawnPosition, spawnRotation);
}
```

`PointerResultExample`장면 (asset/MRTK/example/데모가/Input/장면이/PointerResult/PointerResultExample)은 포인터를 사용 하 여 [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) 적중 위치에서 개체를 생성 하는 방법을 보여 줍니다.

<img src="../images/input/PointerResultExample.png" style="max-width:100%;" alt="Pointer Result">

### <a name="disable-pointers"></a>포인터 사용 안 함

포인터를 사용 하거나 사용 하지 않도록 설정 하려면 (예: 손 모양 사용 안 함)를 [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 통해 지정 된 포인터 형식에 대해를 설정 [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) 합니다.

```c#
// Disable the hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Disable hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);

// Disable the gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOff);

// Set the behavior to match HoloLens 1
// Note, if on HoloLens 2, you must configure your pointer profile to make the GGV pointer show up for articulated hands.
public void SetHoloLens1()
{
    PointerUtils.SetPokePointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGrabPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGGVBehavior(PointerBehavior.Default);
}
```

[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) 더 많은 예제는 및를 참조 하세요.

## <a name="pointer-interactions-via-editor"></a>편집기를 통한 포인터 상호 작용

에서 처리 하는 포인터 이벤트의 경우 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) mrtk는 구성 요소의 형태로 더 편리 하 [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) 게 사용할 수 있으므로 Unity 이벤트를 통해 포인터 이벤트를 직접 처리할 수 있습니다.

<img src="../images/pointers/PointerHandler.png" style="max-width:100%;" alt="Pointer Handler">

## <a name="pointer-extent"></a>포인터 익스텐트

Far 포인터에는이를 사용 하 여 장면의 다른 개체와 상호 작용 하는 정도를 제한 하는 설정이 있습니다.
기본적으로이 값은 10 미터로 설정 됩니다. 이 값은 HoloLens 셸의 동작과 일관 되 게 유지 되도록 선택 되었습니다.

`DefaultControllerPointer`Prefab의 구성 요소 필드를 업데이트 하 여 변경할 수 있습니다 [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) .

*포인터 익스텐트* -포인터가 상호 작용 하는 최대 거리를 제어 합니다.

*기본 포인터 익스텐트* -포인터가 무엇이 든 상호 작용 하지 않을 때 렌더링 되는 포인터 광선/선의 길이를 제어 합니다.

## <a name="see-also"></a>추가 정보

- [포인터 아키텍처](../../architecture/controllers-pointers-and-focus.md)
- [입력 이벤트](input-events.md)
