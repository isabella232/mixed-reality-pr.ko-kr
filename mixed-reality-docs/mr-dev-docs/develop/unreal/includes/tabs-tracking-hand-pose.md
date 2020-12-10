---
ms.openlocfilehash: 9fdcbdfe115fa859081c28b768f9c213ac241d13
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002725"
---
# <a name="425"></a>[<span data-ttu-id="5aa2a-101">4.25</span><span class="sxs-lookup"><span data-stu-id="5aa2a-101">4.25</span></span>](#tab/425)

<span data-ttu-id="5aa2a-102">`EWMRHandKeypoint`열거형은 손 모양의 뼈 계층을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-102">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="5aa2a-103">청사진에 나열 된 각 손 keypoint을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-103">You can find each hand keypoint listed in your Blueprints:</span></span>

![핸드 Keypoint BP](../images/hand-keypoint-bp.png)

<span data-ttu-id="5aa2a-105">전체 c + + 열거형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-105">The full C++ enum is listed below:</span></span>
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

<span data-ttu-id="5aa2a-106">[HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) 테이블에서 각 열거 사례의 숫자 값을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-106">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span>

### <a name="supporting-hand-tracking"></a><span data-ttu-id="5aa2a-107">수동 추적 지원</span><span class="sxs-lookup"><span data-stu-id="5aa2a-107">Supporting Hand Tracking</span></span>

<span data-ttu-id="5aa2a-108">다음을 추가 하 여 청사진에서 수동 추적을 사용할 수 있습니다. **> Windows Mixed Reality** 에서 직접 추적을 **지원 합니다** .</span><span class="sxs-lookup"><span data-stu-id="5aa2a-108">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![수동 추적 BP](../images/unreal/hand-tracking-bp.png)

<span data-ttu-id="5aa2a-110">이 함수 `true` 는 장치에서 직접 추적이 지원 되 고 `false` 수동 추적을 사용할 수 없는 경우를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-110">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![수동 추적 BP 지원](../images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="5aa2a-112">C++:</span><span class="sxs-lookup"><span data-stu-id="5aa2a-112">C++:</span></span>

<span data-ttu-id="5aa2a-113">`WindowsMixedRealityHandTrackingFunctionLibrary.h`를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-113">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="5aa2a-114">손으로 추적 하는 중</span><span class="sxs-lookup"><span data-stu-id="5aa2a-114">Getting Hand Tracking</span></span>

<span data-ttu-id="5aa2a-115">**GetHandJointTransform** 를 사용 하 여 손으로 공간 데이터를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-115">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="5aa2a-116">데이터는 모든 프레임을 업데이트 하지만 프레임 내에 있으면 반환 된 값이 캐시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-116">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="5aa2a-117">성능상의 이유로이 함수에는 높은 논리를 포함 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-117">It's not recommended to have heavy logic in this function for performance reasons.</span></span>

![핸드 조인트 변환 가져오기](../images/unreal/get-hand-joint-transform.png)

<span data-ttu-id="5aa2a-119">C++:</span><span class="sxs-lookup"><span data-stu-id="5aa2a-119">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="5aa2a-120">다음은 GetHandJointTransform의 함수 매개 변수를 분석 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-120">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="5aa2a-121"> 사용자가 왼쪽 또는 오른쪽에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-121">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="5aa2a-122">**Keypoint** – 바늘의 뼈입니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-122">**Keypoint** – the bone of the hand.</span></span>
* <span data-ttu-id="5aa2a-123">**변환** – 뼈의 기본 좌표와 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-123">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="5aa2a-124">다음 뼈의 밑수를 요청 하 여 뼈의 끝 부분에 대 한 변환 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-124">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="5aa2a-125">특수 팁 뼈는 distal의 끝을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-125">A special Tip bone gives end of distal.</span></span>
* <span data-ttu-id="5aa2a-126">\* \* Radius-뼈 밑의 반경입니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-126">\*\*Radius—radius of the base of the bone.</span></span>
* <span data-ttu-id="5aa2a-127">\* \* 반환 값-뼈가이 프레임을 추적 하면 true이 고, 뼈가 추적 되지 않으면 false입니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-127">\*\*Return Value—true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>


# <a name="426"></a>[<span data-ttu-id="5aa2a-128">4.26</span><span class="sxs-lookup"><span data-stu-id="5aa2a-128">4.26</span></span>](#tab/426)

<span data-ttu-id="5aa2a-129">계층은 열거형으로 설명 됩니다 `EHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="5aa2a-129">The hierarchy is described by `EHandKeypoint` enum:</span></span>

![손 모양 keypoint bluprint 옵션 이미지](../images/hand-keypoint-bp.png)

<span data-ttu-id="5aa2a-131">**동작 컨트롤러 데이터 가져오기** 함수를 사용 하 여 사용자의 손으로 모든 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-131">You can get all this data from a user’s hands using the **Get Motion Controller Data** function.</span></span> <span data-ttu-id="5aa2a-132">이 함수는 **Xrmotioncontrollerdata** 구조체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-132">That function returns an **XRMotionControllerData** structure.</span></span> <span data-ttu-id="5aa2a-133">다음은 XRMotionControllerData 구조를 구문 분석 하 여 직접 공동 배치 위치를 가져오고 각 조인트의 위치에서 디버그 좌표계를 그리는 샘플 청사진 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-133">Below is a sample Blueprint script that parses the XRMotionControllerData structure to get hand joint locations and draws a debug coordinate system at each joint’s location.</span></span>

![채널 함수로 선 추적에 연결 된 get 응시 데이터 함수의 청사진](../images/unreal-hand-tracking-img-03.png)

<span data-ttu-id="5aa2a-135">구조가 유효 하 고 정확한 지 확인 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-135">It's important to check if the structure is valid and that it's a hand.</span></span> <span data-ttu-id="5aa2a-136">그렇지 않으면 위치, 회전 및 반지름 배열에 대 한 액세스에서 정의 되지 않은 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5aa2a-136">Otherwise, you may get undefined behavior in access to positions, rotations, and radii arrays.</span></span>
