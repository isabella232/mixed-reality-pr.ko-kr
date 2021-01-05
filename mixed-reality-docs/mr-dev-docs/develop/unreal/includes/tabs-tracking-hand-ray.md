---
ms.openlocfilehash: 18ccbf3e28eaa2f61157bd9585d633c987e9af48
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717884"
---
# <a name="426"></a>[4.26](#tab/426)

핸드 광선의 데이터를 가져오려면 이전 섹션에서 동작 컨트롤러 데이터 가져오기 함수를 사용 해야 합니다. 반환 된 구조체에는 바늘을 만드는 데 사용할 수 있는 두 개의 매개 변수 ( **목표 위치** 및 **표적 회전**)가 포함 되어 있습니다. 이러한 매개 변수는 엘보우로 향하는 광선을 형성 합니다. 이를 수행 하 고가 가리키는 홀로그램을 찾아야 합니다.

다음은 광선이 위젯에 적중 되는지 여부를 결정 하 고 사용자 지정 적중 결과를 설정 하는 예입니다.

![Get 모션 컨트롤러 데이터 함수의 청사진](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[4.25](#tab/425)

청사진에서 손 광선을 사용 하려면 **Windows Mixed REALITY HMD** 에서 작업을 검색 합니다.

![핸드 광선 BP](../images/unreal/hand-rays-bp.png)

C + +에서 액세스 하려면 `WindowsMixedRealityFunctionLibrary.h` 호출 하는 코드 파일의 맨 위에를 포함 합니다.

### <a name="enum"></a>열거형

또한 청사진에서 사용할 수 있는 **EHMDInputControllerButtons** 아래의 입력 사례에 액세스할 수 있습니다.

![입력 컨트롤러 단추](../images/unreal/input-controller-buttons.png)

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
    * 비행기 탭, 응시 및 커밋에 의해 또는 [음성 입력](../unreal-voice-input.md) 을 사용 하도록 설정 된 "선택"을 말하는 경우 HoloLens 2에서 트리거됩니다.
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

![포인터 포즈 정보 BP](../images/unreal/pointer-pose-info-bp.png)

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

![포인터 포즈 정보 가져오기](../images/unreal/get-pointer-pose-info.png)

C++:
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Grasped** 는 현재 프레임의 Grasped 경우 true를 반환 합니다.

청사진

![Grasped BP](../images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. **Select 누르면** 사용자가 현재 프레임에서 select를 트리거한 경우 true를 반환 합니다.

청사진

![선택 프레스 BP](../images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. **이 단추를 클릭** 하면 현재 프레임에서 이벤트 또는 단추가 트리거되는 경우 true가 반환 됩니다.

청사진

![단추 클릭을 클릭 합니다.](../images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **컨트롤러 추적 상태 가져오기** 는 현재 프레임에서 추적 상태를 반환 합니다.

청사진

![컨트롤러 추적 상태 BP 가져오기](../images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```