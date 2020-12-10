---
ms.openlocfilehash: 9fdcbdfe115fa859081c28b768f9c213ac241d13
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002725"
---
# <a name="425"></a>[4.25](#tab/425)

`EWMRHandKeypoint`열거형은 손 모양의 뼈 계층을 설명 합니다. 청사진에 나열 된 각 손 keypoint을 찾을 수 있습니다.

![핸드 Keypoint BP](../images/hand-keypoint-bp.png)

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

[HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) 테이블에서 각 열거 사례의 숫자 값을 찾을 수 있습니다.

### <a name="supporting-hand-tracking"></a>수동 추적 지원

다음을 추가 하 여 청사진에서 수동 추적을 사용할 수 있습니다. **> Windows Mixed Reality** 에서 직접 추적을 **지원 합니다** .

![수동 추적 BP](../images/unreal/hand-tracking-bp.png)

이 함수 `true` 는 장치에서 직접 추적이 지원 되 고 `false` 수동 추적을 사용할 수 없는 경우를 반환 합니다.

![수동 추적 BP 지원](../images/unreal/supports-hand-tracking-bp.png)

C++:

`WindowsMixedRealityHandTrackingFunctionLibrary.h`를 포함합니다.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>손으로 추적 하는 중

**GetHandJointTransform** 를 사용 하 여 손으로 공간 데이터를 반환할 수 있습니다. 데이터는 모든 프레임을 업데이트 하지만 프레임 내에 있으면 반환 된 값이 캐시 됩니다. 성능상의 이유로이 함수에는 높은 논리를 포함 하지 않는 것이 좋습니다.

![핸드 조인트 변환 가져오기](../images/unreal/get-hand-joint-transform.png)

C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

다음은 GetHandJointTransform의 함수 매개 변수를 분석 한 것입니다.

*  사용자가 왼쪽 또는 오른쪽에 있을 수 있습니다.
* **Keypoint** – 바늘의 뼈입니다.
* **변환** – 뼈의 기본 좌표와 방향입니다. 다음 뼈의 밑수를 요청 하 여 뼈의 끝 부분에 대 한 변환 데이터를 가져올 수 있습니다. 특수 팁 뼈는 distal의 끝을 제공 합니다.
* * * Radius-뼈 밑의 반경입니다.
* * * 반환 값-뼈가이 프레임을 추적 하면 true이 고, 뼈가 추적 되지 않으면 false입니다.


# <a name="426"></a>[4.26](#tab/426)

계층은 열거형으로 설명 됩니다 `EHandKeypoint` .

![손 모양 keypoint bluprint 옵션 이미지](../images/hand-keypoint-bp.png)

**동작 컨트롤러 데이터 가져오기** 함수를 사용 하 여 사용자의 손으로 모든 데이터를 가져올 수 있습니다. 이 함수는 **Xrmotioncontrollerdata** 구조체를 반환 합니다. 다음은 XRMotionControllerData 구조를 구문 분석 하 여 직접 공동 배치 위치를 가져오고 각 조인트의 위치에서 디버그 좌표계를 그리는 샘플 청사진 스크립트입니다.

![채널 함수로 선 추적에 연결 된 get 응시 데이터 함수의 청사진](../images/unreal-hand-tracking-img-03.png)

구조가 유효 하 고 정확한 지 확인 하는 것이 중요 합니다. 그렇지 않으면 위치, 회전 및 반지름 배열에 대 한 액세스에서 정의 되지 않은 동작이 발생할 수 있습니다.
