---
ms.openlocfilehash: fb8b5b509ef83e2a4f9d978dbf0faebbf3e0be1d10d6697f16cfb9366d7a2edb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187511"
---
# <a name="426"></a>[4.26](#tab/426)

손 광선에 대한 데이터를 얻으려면 이전 섹션의 동작 컨트롤러 데이터 얻기 함수를 사용해야 합니다. 반환된 구조체에는 손 광선을 만드는 데 사용할 수 있는 두 개의 매개 변수인 **Aim Position** 및 **Aim Rotation이 포함됩니다.** 이러한 매개 변수는 사용자의 광선이 지시하는 광선을 형성합니다. 이를 받아서 가리키는 홀로그램을 찾아야 합니다.

다음은 손 광선이 위젯에 적중하는지 여부를 결정하고 사용자 지정 적중 결과를 설정하는 예제입니다.

![get motion controller data 함수의 청사진](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[4.25](#tab/425)

청사진에서 손 광선을 사용하려면 **Windows Mixed Reality HMD에서** 작업을 검색합니다.

![손 광선 BP](../images/unreal/hand-rays-bp.png)

C++에서 액세스하려면 호출 코드 파일의 맨 위에 를 `WindowsMixedRealityFunctionLibrary.h` 포함합니다.

### <a name="enum"></a>열거형

또한 청사진에서 사용할 수 있는 **EHMDInputControllerButtons** 아래의 입력 사례에 액세스할 수 있습니다.

![입력 컨트롤러 단추](../images/unreal/input-controller-buttons.png)

C++에서 액세스하려면 `EHMDInputControllerButtons` 열거형 클래스를 사용합니다.
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

다음은 적용 가능한 두 열거형 사례에 대한 분석입니다.

* **Select** - 사용자가 트리거한 Select 이벤트입니다.
    * HoloLens 2 에어 탭, 응시 및 커밋을 통해 또는 [음성 입력이](../unreal-voice-input.md) 활성화된 "선택"이라고 말하여 트리거됩니다.
* **파악** - 사용자가 트리거한 손아귀 이벤트입니다.
    * 홀로그램에서 사용자의 손가락을 닫아 HoloLens 2 트리거됩니다.

아래와 같은 열거형을 통해 C++에서 손 메시의 추적 상태에 액세스할 수 `EHMDTrackingStatus` 있습니다.

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

다음은 적용 가능한 두 열거형 사례에 대한 분석입니다.

* **NotTracked** –- 손을 볼 수 없습니다.
* **추적** –- 손은 완전히 추적됩니다.

### <a name="struct"></a>구조체

PointerPoseInfo 구조체는 다음 손 데이터에 대한 정보를 제공할 수 있습니다.

* **원점** – 손의 원점
* **방향** – 손 방향
* **Up** – 손의 up 벡터
* **방향** – 방향 쿼터니언
* **추적 상태** – 현재 추적 상태

아래와 같이 Blueprints를 통해 PointerPoseInfo 구조체에 액세스할 수 있습니다.

![포인터 자세 정보 BP](../images/unreal/pointer-pose-info-bp.png)

또는 C++를 통해 다음을 수행합니다.

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

아래에 나열된 모든 함수는 모든 프레임에서 호출할 수 있으며, 이를 통해 연속 모니터링이 가능합니다.

1. **포인터 자세 정보 얻기는** 현재 프레임의 손 광선 방향에 대한 전체 정보를 반환합니다.

청사진:

![포인터 자세 정보 얻기](../images/unreal/get-pointer-pose-info.png)

C++:
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Is Handed는** 현재 프레임에서 손을 잡으면 true를 반환합니다.

청사진:

![은(는) BP를 이해합니다.](../images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. **Select Pressed는** 사용자가 현재 프레임에서 선택을 트리거한 경우 true를 반환합니다.

청사진:

![눌린 BP 선택](../images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. **Is Button Clicked는** 현재 프레임에서 이벤트 또는 단추가 트리거되면 true를 반환합니다.

청사진:

![단추 클릭 BP](../images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **컨트롤러 추적 상태 얻기는** 현재 프레임에서 추적 상태를 반환합니다.

청사진:

![컨트롤러 추적 상태 BP를 얻습니다.](../images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```