---
title: Unreal의 직접 추적
description: Unreal에서 수동 추적을 사용 하는 방법을 설명 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, 직접 추적, Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed reality, 개발, 기능, 설명서, 가이드, holograms, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 4c66e2353c1e881c05541fd0fe9eafa553ea5c23
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609714"
---
# <a name="hand-tracking-in-unreal"></a>Unreal의 직접 추적

손으로 추적 시스템은 사용자의 palms와 손가락을 입력으로 사용 합니다. 모든 손가락의 위치 및 회전에 대 한 데이터, 전체 palm 및 핸드 제스처를 사용할 수 있습니다. 

## <a name="hand-pose"></a>직접 포즈

손으로 사용자를 추적 하 고 입력으로 사용할 수 있습니다. 청사진과 c + +에서 추적 데이터에 액세스할 수 있습니다. 더 자세한 기술 정보는 Unreal의 [Windows](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) 에서 볼 수 있습니다. Unreal API는 틱이 Unreal 엔진과 동기화 된 좌표계로 데이터를 전송 합니다.

### <a name="understanding-the-bone-hierarchy"></a>뼈 계층 구조 이해

`EWMRHandKeypoint`열거형은 손 모양의 뼈 계층을 설명 합니다. 청사진에 나열 된 각 손 keypoint을 찾을 수 있습니다.

![핸드 Keypoint BP](images/hand-keypoint-bp.png)

전체 c + + 열거형은 다음과 같습니다.
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

[HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) 테이블에서 각 열거 사례의 숫자 값을 찾을 수 있습니다. Enum 사례와 일치 하는 전체 포즈 레이아웃은 아래 이미지에 나와 있습니다.

![직접 기초](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a>수동 추적 지원

다음을 추가 하 여 청사진에서 수동 추적을 사용할 수 있습니다. **> Windows Mixed Reality** 에서 직접 추적을 **지원 합니다** .

![수동 추적 BP](images/unreal/hand-tracking-bp.png)

이 함수 `true` 는 장치에서 직접 추적이 지원 되 고 `false` 수동 추적을 사용할 수 없는 경우를 반환 합니다.

![수동 추적 BP 지원](images/unreal/supports-hand-tracking-bp.png)

C++: 

`WindowsMixedRealityHandTrackingFunctionLibrary.h`를 포함합니다.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>손으로 추적 하는 중

**GetHandJointTransform** 를 사용 하 여 손으로 공간 데이터를 반환할 수 있습니다. 데이터는 모든 프레임을 업데이트 하지만 프레임 내에 있으면 반환 된 값이 캐시 됩니다. 성능상의 이유로이 함수에는 높은 논리를 포함 하지 않는 것이 좋습니다. 

![핸드 조인트 변환 가져오기](images/unreal/get-hand-joint-transform.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

다음은 GetHandJointTransform의 함수 매개 변수를 분석 한 것입니다.

* **Hand** 사용자가 왼쪽 또는 오른쪽에 있을 수 있습니다.
* **Keypoint** – 바늘의 뼈입니다. 
* **변환** – 뼈의 기본 좌표와 방향입니다. 다음 뼈의 밑수를 요청 하 여 뼈의 끝 부분에 대 한 변환 데이터를 가져올 수 있습니다. 특수 팁 뼈는 distal의 끝을 제공 합니다. 
* **Radius** -뼈 밑의 반경입니다.
* **반환 값** -뼈가이 프레임을 추적 하면 true이 고, 뼈가 추적 되지 않으면 false입니다.

## <a name="hand-live-link-animation"></a>손 모양 링크 애니메이션

손 포즈는 [라이브 링크 플러그 인](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)을 사용 하 여 애니메이션에 노출 됩니다.

Windows Mixed Reality 및 라이브 링크 플러그 인을 사용 하는 경우: 
1. **창 > 라이브 링크** 를 선택 하 여 라이브 링크 편집기 창을 엽니다. 
2. **원본** 선택 및 **Windows Mixed Reality 추적 원본** 사용

![라이브 링크 소스](images/unreal/live-link-source.png)
 
소스를 사용 하도록 설정 하 고 애니메이션 자산을 연 후에는 **장면 미리 보기** 탭에서 **애니메이션** 섹션을 확장 하 여 추가 옵션을 표시 합니다.

![라이브 링크 애니메이션](images/unreal/live-link-animation.png)
 
손 모양 애니메이션 계층은에서와 동일 합니다 `EWMRHandKeypoint` . **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** 를 사용 하 여 애니메이션의 대상을 지정할 수 있습니다.

![라이브 링크 애니메이션 2](images/unreal/live-link-animation2.png)
 
편집기에서 서브클래싱 될 수도 있습니다.

![라이브 링크 다시 매핑](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a>손 모양 메시 데이터 액세스

![손 모양 메시](images/unreal/hand-mesh.png)

직접 메시 데이터에 액세스 하려면 먼저 다음을 수행 해야 합니다.
- **Arsessionconfig** 자산을 선택 하 고 **AR 설정-> 월드 매핑** 설정을 확장 하 고 **추적 된 기 하 도형에서 메시 데이터 생성** 을 선택 합니다. 

기본 메시 매개 변수는 다음과 같습니다.

1.  폐색에 대 한 메시 데이터 사용
2.  메시 데이터의 충돌 생성
3.  메시 데이터의 Nav 메시 생성
4.  와이어 프레임으로 메시 데이터 렌더링 – 생성 된 메시를 표시 하는 디버그 매개 변수

이러한 매개 변수 값은 공간 매핑 메시 및 손 모양 메시 기본값으로 사용 됩니다. 모든 망상의 청사진 또는 코드에서 언제 든 지 변경할 수 있습니다.

### <a name="c-api-reference"></a>C + + API 참조 
`EEARObjectClassification`를 사용 하 여 모든 추적 가능 개체에서 손 모양 값을 찾을 수 있습니다.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

다음 대리자는 시스템에서 손 메시를 포함 하 여 추적 가능 개체를 검색할 때 호출 됩니다. 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

대리자 처리기가 아래 함수 시그니처를 따르는지 확인 합니다.

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

다음을 통해 메시 데이터에 액세스할 수 있습니다  `UARTrackedGeometry::GetUnderlyingMesh` .

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a>청사진 API 참조

청사진에서 손 모양 망을 사용 하려면 다음을 수행 합니다.
1. 청사진 행위자에 **ARTrackableNotify** 구성 요소 추가

![ARTrackable 알림](images/unreal/ar-trackable-notify.png)
 
2. **세부 정보** 패널로 이동 하 여 **이벤트** 섹션을 확장 합니다. 

![ARTrackable 알림 2](images/unreal/ar-trackable-notify2.png)
 
3. 이벤트 그래프의 다음 노드로 추적 된 Geometry 추가/업데이트/제거를 덮어씁니다.

![ARTrackable 알림](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>손 광선

[SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API를 노출 하는 c + + 및 청사진에서 직접 광선을 포인팅 장치로 사용할 수 있습니다.

> [!IMPORTANT]
> 모든 함수 결과는 프레임 마다 변경 되므로 모두 호출할 수 있습니다. Pure 및 비 순수형 또는 호출 가능 함수에 대 한 자세한 내용은 [함수](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)에 대 한 청사진 사용자 guid를 참조 하세요.

청사진에서 손 광선을 사용 하려면 **Windows Mixed REALITY HMD** 에서 작업을 검색 합니다.

![핸드 광선 BP](images/unreal/hand-rays-bp.png)
 
C + +에서 액세스 하려면 `WindowsMixedRealityFunctionLibrary.h` 호출 하는 코드 파일의 맨 위에를 포함 합니다.

### <a name="enum"></a>열거형

또한 청사진에서 사용할 수 있는 **EHMDInputControllerButtons** 아래의 입력 사례에 액세스할 수 있습니다.

![입력 컨트롤러 단추](images/unreal/input-controller-buttons.png)

C + +에서 액세스의 경우 `EHMDInputControllerButtons` enum 클래스를 사용 합니다.
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

다음은 적용 가능한 두 가지 열거 사례를 분석 한 것입니다.

* **Select** -사용자가 트리거된 select 이벤트입니다. 
    * 비행기 탭, 응시 및 커밋에 의해 또는 [음성 입력](unreal-voice-input.md) 을 사용 하도록 설정 된 "선택"을 말하는 경우 HoloLens 2에서 트리거됩니다. 
* 사용자가 트리거 **이벤트를 트리거** 했습니다. 
    * 홀로그램에서 사용자 손가락을 닫아 HoloLens 2에서 트리거됩니다. 

아래에 표시 된 열거형을 통해 c + +에서 손 모양에 대 한 추적 상태에 액세스할 수 있습니다 `EHMDTrackingStatus` .

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

다음은 적용 가능한 두 가지 열거 사례를 분석 한 것입니다.

* **Nottracked** – 손 모양이 표시 되지 않습니다.
* **추적** –이 손을 완전히 추적 합니다.

### <a name="struct"></a>구조체

PointerPoseInfo 구조체는 다음 데이터에 대 한 정보를 제공할 수 있습니다.

* **원점** – 손 모양
* **방향** – 손 방향
* **Up** – 손 모양 벡터
* **방향** – 4 원수 
* **상태 추적** -현재 추적 상태

아래와 같이 청사진을 통해 PointerPoseInfo 구조체에 액세스할 수 있습니다.

![포인터 포즈 정보 BP](images/unreal/pointer-pose-info-bp.png)

또는 c + +:

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a>Functions

아래에 나열 된 모든 함수는 연속 모니터링을 허용 하는 모든 프레임에서 호출 될 수 있습니다. 

1. **포인터 포즈 정보 가져오기** 현재 프레임의 손 모양에 대 한 전체 정보를 반환 합니다. 

청사진

![포인터 포즈 정보 가져오기](images/unreal/get-pointer-pose-info.png)

C++: 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Grasped** 는 현재 프레임의 Grasped 경우 true를 반환 합니다.

청사진

![Grasped BP](images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. **Select 누르면** 사용자가 현재 프레임에서 select를 트리거한 경우 true를 반환 합니다.

청사진

![선택 프레스 BP](images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. **이 단추를 클릭** 하면 현재 프레임에서 이벤트 또는 단추가 트리거되는 경우 true가 반환 됩니다.

청사진

![단추 클릭을 클릭 합니다.](images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **컨트롤러 추적 상태 가져오기** 는 현재 프레임에서 추적 상태를 반환 합니다.

청사진

![컨트롤러 추적 상태 BP 가져오기](images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a>제스처

HoloLens 2는 공간 제스처를 추적 합니다. 즉, 이러한 제스처를 입력으로 캡처할 수 있습니다. 제스처에 대 한 자세한 내용은 [HoloLens 2 기본 사용](https://docs.microsoft.com/hololens/hololens2-basic-usage) 문서에 나와 있습니다.

**Windows Mixed Reality 공간 입력** 및 호출 하는 `WindowsMixedRealitySpatialInputFunctionLibrary.h` 코드 파일에를 추가 하 여 c + + 함수에서 청사진 함수를 찾을 수 있습니다.

![캡처 제스처](images/unreal/capture-gestures.png)

### <a name="enum"></a>열거형
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
청사진 

![제스처 형식](images/unreal/gesture-type.png)

C++:
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>함수
함수를 사용 하 여 제스처 캡처를 사용 하거나 사용 하지 않도록 설정할 수 있습니다 `CaptureGestures` . 활성화 된 제스처가 입력 이벤트를 발생 시키면이 함수는 `true` 제스처 캡처가 성공한 경우를 반환 하 고 오류가 발생 하면를 반환 합니다 `false` .

청사진

![제스처 BP 캡처](images/unreal/capture-gestures-bp.png)

C++:
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

청사진 및 c + +: 주요 이벤트에서 찾을 수 있는 주요 이벤트는 다음과 같습니다. ![](images/unreal/key-events.png)

![주요 이벤트 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 실제 개발 경험을 수행 하는 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다. 여기에서 다음 구성 요소를 계속 진행할 수 있습니다. 

> [!div class="nextstepaction"]
> [로컬 Spatial Anchors](unreal-spatial-anchors.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [HoloLens 카메라](unreal-hololens-camera.md)

언제든지 [Unreal 개발 검사점](unreal-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.