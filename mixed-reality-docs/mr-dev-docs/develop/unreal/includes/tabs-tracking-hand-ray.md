---
ms.openlocfilehash: 18ccbf3e28eaa2f61157bd9585d633c987e9af48
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717884"
---
# <a name="426"></a>[<span data-ttu-id="3a13a-101">4.26</span><span class="sxs-lookup"><span data-stu-id="3a13a-101">4.26</span></span>](#tab/426)

<span data-ttu-id="3a13a-102">핸드 광선의 데이터를 가져오려면 이전 섹션에서 동작 컨트롤러 데이터 가져오기 함수를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-102">To get the data for the hand rays, you should use the Get Motion Controller Data function from the previous section.</span></span> <span data-ttu-id="3a13a-103">반환 된 구조체에는 바늘을 만드는 데 사용할 수 있는 두 개의 매개 변수 ( **목표 위치** 및 **표적 회전**)가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-103">The returned structure contains two parameters you can use to create a hand ray – **Aim Position** and **Aim Rotation**.</span></span> <span data-ttu-id="3a13a-104">이러한 매개 변수는 엘보우로 향하는 광선을 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-104">These parameters form a ray directed by your elbow.</span></span> <span data-ttu-id="3a13a-105">이를 수행 하 고가 가리키는 홀로그램을 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-105">You should take them and find a hologram being pointed by.</span></span>

<span data-ttu-id="3a13a-106">다음은 광선이 위젯에 적중 되는지 여부를 결정 하 고 사용자 지정 적중 결과를 설정 하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-106">Below is an example of determining whether a hand ray hits a Widget and setting a custom hit result:</span></span>

![Get 모션 컨트롤러 데이터 함수의 청사진](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[<span data-ttu-id="3a13a-108">4.25</span><span class="sxs-lookup"><span data-stu-id="3a13a-108">4.25</span></span>](#tab/425)

<span data-ttu-id="3a13a-109">청사진에서 손 광선을 사용 하려면 **Windows Mixed REALITY HMD** 에서 작업을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-109">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![핸드 광선 BP](../images/unreal/hand-rays-bp.png)

<span data-ttu-id="3a13a-111">C + +에서 액세스 하려면 `WindowsMixedRealityFunctionLibrary.h` 호출 하는 코드 파일의 맨 위에를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-111">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="3a13a-112">열거형</span><span class="sxs-lookup"><span data-stu-id="3a13a-112">Enum</span></span>

<span data-ttu-id="3a13a-113">또한 청사진에서 사용할 수 있는 **EHMDInputControllerButtons** 아래의 입력 사례에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-113">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![입력 컨트롤러 단추](../images/unreal/input-controller-buttons.png)

<span data-ttu-id="3a13a-115">C + +에서 액세스의 경우 `EHMDInputControllerButtons` enum 클래스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-115">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="3a13a-116">다음은 적용 가능한 두 가지 열거 사례를 분석 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-116">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="3a13a-117">**Select** -사용자가 트리거된 select 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-117">**Select** - User triggered Select event.</span></span>
    * <span data-ttu-id="3a13a-118">비행기 탭, 응시 및 커밋에 의해 또는 [음성 입력](../unreal-voice-input.md) 을 사용 하도록 설정 된 "선택"을 말하는 경우 HoloLens 2에서 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-118">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](../unreal-voice-input.md) enabled.</span></span>
* <span data-ttu-id="3a13a-119">사용자가 트리거 **이벤트를 트리거** 했습니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-119">**Grasp** - User triggered Grasp event.</span></span>
    * <span data-ttu-id="3a13a-120">홀로그램에서 사용자 손가락을 닫아 HoloLens 2에서 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-120">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span>

<span data-ttu-id="3a13a-121">아래에 표시 된 열거형을 통해 c + +에서 손 모양에 대 한 추적 상태에 액세스할 수 있습니다 `EHMDTrackingStatus` .</span><span class="sxs-lookup"><span data-stu-id="3a13a-121">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="3a13a-122">다음은 적용 가능한 두 가지 열거 사례를 분석 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-122">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="3a13a-123">**Nottracked** – 손 모양이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-123">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="3a13a-124">**추적** –이 손을 완전히 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-124">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="3a13a-125">구조체</span><span class="sxs-lookup"><span data-stu-id="3a13a-125">Struct</span></span>

<span data-ttu-id="3a13a-126">PointerPoseInfo 구조체는 다음 데이터에 대 한 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-126">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="3a13a-127">**원점** – 손 모양</span><span class="sxs-lookup"><span data-stu-id="3a13a-127">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="3a13a-128">**방향** – 손 방향</span><span class="sxs-lookup"><span data-stu-id="3a13a-128">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="3a13a-129">**Up** – 손 모양 벡터</span><span class="sxs-lookup"><span data-stu-id="3a13a-129">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="3a13a-130">**방향** – 4 원수</span><span class="sxs-lookup"><span data-stu-id="3a13a-130">**Orientation** – orientation quaternion</span></span>
* <span data-ttu-id="3a13a-131">**상태 추적** -현재 추적 상태</span><span class="sxs-lookup"><span data-stu-id="3a13a-131">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="3a13a-132">아래와 같이 청사진을 통해 PointerPoseInfo 구조체에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-132">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![포인터 포즈 정보 BP](../images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="3a13a-134">또는 c + +:</span><span class="sxs-lookup"><span data-stu-id="3a13a-134">Or with C++:</span></span>

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

### <a name="functions"></a><span data-ttu-id="3a13a-135">Functions</span><span class="sxs-lookup"><span data-stu-id="3a13a-135">Functions</span></span>

<span data-ttu-id="3a13a-136">아래에 나열 된 모든 함수는 연속 모니터링을 허용 하는 모든 프레임에서 호출 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-136">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span>

1. <span data-ttu-id="3a13a-137">**포인터 포즈 정보 가져오기** 현재 프레임의 손 모양에 대 한 전체 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-137">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span>

<span data-ttu-id="3a13a-138">청사진</span><span class="sxs-lookup"><span data-stu-id="3a13a-138">Blueprint:</span></span>

![포인터 포즈 정보 가져오기](../images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="3a13a-140">C++:</span><span class="sxs-lookup"><span data-stu-id="3a13a-140">C++:</span></span>
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="3a13a-141">**Grasped** 는 현재 프레임의 Grasped 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-141">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="3a13a-142">청사진</span><span class="sxs-lookup"><span data-stu-id="3a13a-142">Blueprint:</span></span>

![Grasped BP](../images/unreal/is-grasped-bp.png)

<span data-ttu-id="3a13a-144">C++:</span><span class="sxs-lookup"><span data-stu-id="3a13a-144">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. <span data-ttu-id="3a13a-145">**Select 누르면** 사용자가 현재 프레임에서 select를 트리거한 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-145">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="3a13a-146">청사진</span><span class="sxs-lookup"><span data-stu-id="3a13a-146">Blueprint:</span></span>

![선택 프레스 BP](../images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="3a13a-148">C++:</span><span class="sxs-lookup"><span data-stu-id="3a13a-148">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="3a13a-149">**이 단추를 클릭** 하면 현재 프레임에서 이벤트 또는 단추가 트리거되는 경우 true가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-149">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="3a13a-150">청사진</span><span class="sxs-lookup"><span data-stu-id="3a13a-150">Blueprint:</span></span>

![단추 클릭을 클릭 합니다.](../images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="3a13a-152">C++:</span><span class="sxs-lookup"><span data-stu-id="3a13a-152">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="3a13a-153">**컨트롤러 추적 상태 가져오기** 는 현재 프레임에서 추적 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a13a-153">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="3a13a-154">청사진</span><span class="sxs-lookup"><span data-stu-id="3a13a-154">Blueprint:</span></span>

![컨트롤러 추적 상태 BP 가져오기](../images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="3a13a-156">C++:</span><span class="sxs-lookup"><span data-stu-id="3a13a-156">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```