---
ms.openlocfilehash: fa21b1a5c3c89cf3c1c63c7ed8ebbdc3d8547661443853987ee3713e50c50e5c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187505"
---
# <a name="426"></a>[4.26](#tab/426)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

![제스처 함수를 구성하기 위해 연결된 이벤트 시작 재생의 청사진](../images/unreal-hand-tracking-img-09.png)

그런 다음, 다음 이벤트를 구독하는 코드를 추가해야 합니다.

![Windows 공간 입력 홀드, 탭 및 왼쪽 조작 제스처의 청사진 ](../images/unreal/key-events.png)
 ![ 세부 정보 패널에서 공간 입력 탭 제스처 옵션 Windows 스크린샷](../images/unreal/key-events2.png)

### <a name="openxr"></a>OpenXR

OpenXR에서 제스처 이벤트는 입력 파이프라인을 통해 추적됩니다. 손 조작을 사용하면 디바이스가 탭 및 유지 제스처를 자동으로 인식할 수 있지만 다른 제스처는 인식할 수 없습니다. OpenXRMsftHandInteraction Select 및 그립 매핑으로 이름이 지정됩니다. 구독을 사용하도록 설정할 필요가 없습니다. 다음과 같이 Project 설정/엔진/입력에서 이벤트를 선언해야 합니다.

![OpenXR 작업 매핑의 스크린샷](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[4.25](#tab/425)

에서 공간 **입력 Windows Mixed Reality** Blueprint 함수를 찾을 수 있으며, 호출 코드 파일에 를 추가하여 C++ 함수를 찾을 `WindowsMixedRealitySpatialInputFunctionLibrary.h` 수 있습니다.

![캡처 제스처](../images/unreal/capture-gestures.png)

### <a name="enum"></a>열거형
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
청사진:

![제스처 유형](../images/unreal/gesture-type.png)

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
함수를 사용하여 제스처 캡처를 사용하거나 사용하지 않도록 설정할 수 `CaptureGestures` 있습니다. 활성화된 제스처가 입력 이벤트를 발생시킬 때 `true` 함수는 제스처 캡처가 성공하면 를 반환하고 `false` 오류가 있으면 를 반환합니다.

청사진:

![캡처 제스처 BP](../images/unreal/capture-gestures-bp.png)

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

다음은 청사진 및 C++: 키 이벤트에서 찾을 수 있는 ![ 주요 이벤트입니다.](../images/unreal/key-events.png)

![주요 이벤트 2](../images/unreal/key-events2.png)
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

