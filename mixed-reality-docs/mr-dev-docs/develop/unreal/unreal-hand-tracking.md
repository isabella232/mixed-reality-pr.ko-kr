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
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="7622e-104">Unreal의 직접 추적</span><span class="sxs-lookup"><span data-stu-id="7622e-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="7622e-105">손으로 추적 시스템은 사용자의 palms와 손가락을 입력으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="7622e-106">모든 손가락의 위치 및 회전에 대 한 데이터, 전체 palm 및 핸드 제스처를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="7622e-107">직접 포즈</span><span class="sxs-lookup"><span data-stu-id="7622e-107">Hand Pose</span></span>

<span data-ttu-id="7622e-108">손으로 사용자를 추적 하 고 입력으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-108">Hand pose lets you track and use the hands and fingers of your users as input.</span></span> <span data-ttu-id="7622e-109">청사진과 c + +에서 추적 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-109">You can access tracking data both in Blueprints and C++.</span></span> <span data-ttu-id="7622e-110">더 자세한 기술 정보는 Unreal의 [Windows](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) 에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-110">You can find more technical details in Unreal's [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API.</span></span> <span data-ttu-id="7622e-111">Unreal API는 틱이 Unreal 엔진과 동기화 된 좌표계로 데이터를 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

### <a name="understanding-the-bone-hierarchy"></a><span data-ttu-id="7622e-112">뼈 계층 구조 이해</span><span class="sxs-lookup"><span data-stu-id="7622e-112">Understanding the bone hierarchy</span></span>

<span data-ttu-id="7622e-113">`EWMRHandKeypoint`열거형은 손 모양의 뼈 계층을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-113">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="7622e-114">청사진에 나열 된 각 손 keypoint을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-114">You can find each hand keypoint listed in your Blueprints:</span></span>

![핸드 Keypoint BP](images/hand-keypoint-bp.png)

<span data-ttu-id="7622e-116">전체 c + + 열거형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-116">The full C++ enum is listed below:</span></span>
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

<span data-ttu-id="7622e-117">[HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) 테이블에서 각 열거 사례의 숫자 값을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-117">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span> <span data-ttu-id="7622e-118">Enum 사례와 일치 하는 전체 포즈 레이아웃은 아래 이미지에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-118">The entire hand pose layout with matching enum cases is shown in the image below:</span></span>

![직접 기초](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a><span data-ttu-id="7622e-120">수동 추적 지원</span><span class="sxs-lookup"><span data-stu-id="7622e-120">Supporting Hand Tracking</span></span>

<span data-ttu-id="7622e-121">다음을 추가 하 여 청사진에서 수동 추적을 사용할 수 있습니다. **> Windows Mixed Reality** 에서 직접 추적을 **지원 합니다** .</span><span class="sxs-lookup"><span data-stu-id="7622e-121">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![수동 추적 BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="7622e-123">이 함수 `true` 는 장치에서 직접 추적이 지원 되 고 `false` 수동 추적을 사용할 수 없는 경우를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-123">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![수동 추적 BP 지원](images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="7622e-125">C++:</span><span class="sxs-lookup"><span data-stu-id="7622e-125">C++:</span></span> 

<span data-ttu-id="7622e-126">`WindowsMixedRealityHandTrackingFunctionLibrary.h`를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-126">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="7622e-127">손으로 추적 하는 중</span><span class="sxs-lookup"><span data-stu-id="7622e-127">Getting Hand Tracking</span></span>

<span data-ttu-id="7622e-128">**GetHandJointTransform** 를 사용 하 여 손으로 공간 데이터를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-128">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="7622e-129">데이터는 모든 프레임을 업데이트 하지만 프레임 내에 있으면 반환 된 값이 캐시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-129">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="7622e-130">성능상의 이유로이 함수에는 높은 논리를 포함 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-130">It's not recommended to have heavy logic in this function for performance reasons.</span></span> 

![핸드 조인트 변환 가져오기](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="7622e-132">C++:</span><span class="sxs-lookup"><span data-stu-id="7622e-132">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="7622e-133">다음은 GetHandJointTransform의 함수 매개 변수를 분석 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-133">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="7622e-134">**Hand** 사용자가 왼쪽 또는 오른쪽에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-134">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="7622e-135">**Keypoint** – 바늘의 뼈입니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-135">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="7622e-136">**변환** – 뼈의 기본 좌표와 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-136">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="7622e-137">다음 뼈의 밑수를 요청 하 여 뼈의 끝 부분에 대 한 변환 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-137">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="7622e-138">특수 팁 뼈는 distal의 끝을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-138">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="7622e-139">**Radius** -뼈 밑의 반경입니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-139">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="7622e-140">**반환 값** -뼈가이 프레임을 추적 하면 true이 고, 뼈가 추적 되지 않으면 false입니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-140">**Return Value** — true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="7622e-141">손 모양 링크 애니메이션</span><span class="sxs-lookup"><span data-stu-id="7622e-141">Hand Live Link Animation</span></span>

<span data-ttu-id="7622e-142">손 포즈는 [라이브 링크 플러그 인](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)을 사용 하 여 애니메이션에 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-142">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="7622e-143">Windows Mixed Reality 및 라이브 링크 플러그 인을 사용 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="7622e-143">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span> 
1. <span data-ttu-id="7622e-144">**창 > 라이브 링크** 를 선택 하 여 라이브 링크 편집기 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-144">Select **Window > Live Link** to open the Live Link editor window.</span></span> 
2. <span data-ttu-id="7622e-145">**원본** 선택 및 **Windows Mixed Reality 추적 원본** 사용</span><span class="sxs-lookup"><span data-stu-id="7622e-145">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![라이브 링크 소스](images/unreal/live-link-source.png)
 
<span data-ttu-id="7622e-147">소스를 사용 하도록 설정 하 고 애니메이션 자산을 연 후에는 **장면 미리 보기** 탭에서 **애니메이션** 섹션을 확장 하 여 추가 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-147">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![라이브 링크 애니메이션](images/unreal/live-link-animation.png)
 
<span data-ttu-id="7622e-149">손 모양 애니메이션 계층은에서와 동일 합니다 `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="7622e-149">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="7622e-150">**WindowsMixedRealityHandTrackingLiveLinkRemapAsset** 를 사용 하 여 애니메이션의 대상을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-150">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![라이브 링크 애니메이션 2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="7622e-152">편집기에서 서브클래싱 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-152">It can also be subclassed in the editor:</span></span>

![라이브 링크 다시 매핑](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a><span data-ttu-id="7622e-154">손 모양 메시 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="7622e-154">Accessing Hand Mesh Data</span></span>

![손 모양 메시](images/unreal/hand-mesh.png)

<span data-ttu-id="7622e-156">직접 메시 데이터에 액세스 하려면 먼저 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-156">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="7622e-157">**Arsessionconfig** 자산을 선택 하 고 **AR 설정-> 월드 매핑** 설정을 확장 하 고 **추적 된 기 하 도형에서 메시 데이터 생성** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-157">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span> 

<span data-ttu-id="7622e-158">기본 메시 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-158">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="7622e-159">폐색에 대 한 메시 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="7622e-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="7622e-160">메시 데이터의 충돌 생성</span><span class="sxs-lookup"><span data-stu-id="7622e-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="7622e-161">메시 데이터의 Nav 메시 생성</span><span class="sxs-lookup"><span data-stu-id="7622e-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="7622e-162">와이어 프레임으로 메시 데이터 렌더링 – 생성 된 메시를 표시 하는 디버그 매개 변수</span><span class="sxs-lookup"><span data-stu-id="7622e-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="7622e-163">이러한 매개 변수 값은 공간 매핑 메시 및 손 모양 메시 기본값으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-163">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="7622e-164">모든 망상의 청사진 또는 코드에서 언제 든 지 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-164">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="7622e-165">C + + API 참조</span><span class="sxs-lookup"><span data-stu-id="7622e-165">C++ API Reference</span></span> 
<span data-ttu-id="7622e-166">`EEARObjectClassification`를 사용 하 여 모든 추적 가능 개체에서 손 모양 값을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-166">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

<span data-ttu-id="7622e-167">다음 대리자는 시스템에서 손 메시를 포함 하 여 추적 가능 개체를 검색할 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-167">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 

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

<span data-ttu-id="7622e-168">대리자 처리기가 아래 함수 시그니처를 따르는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-168">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="7622e-169">다음을 통해 메시 데이터에 액세스할 수 있습니다  `UARTrackedGeometry::GetUnderlyingMesh` .</span><span class="sxs-lookup"><span data-stu-id="7622e-169">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a><span data-ttu-id="7622e-170">청사진 API 참조</span><span class="sxs-lookup"><span data-stu-id="7622e-170">Blueprint API Reference</span></span>

<span data-ttu-id="7622e-171">청사진에서 손 모양 망을 사용 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-171">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="7622e-172">청사진 행위자에 **ARTrackableNotify** 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="7622e-172">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![ARTrackable 알림](images/unreal/ar-trackable-notify.png)
 
2. <span data-ttu-id="7622e-174">**세부 정보** 패널로 이동 하 여 **이벤트** 섹션을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-174">Go to the **Details** panel and expand the **Events** section.</span></span> 

![ARTrackable 알림 2](images/unreal/ar-trackable-notify2.png)
 
3. <span data-ttu-id="7622e-176">이벤트 그래프의 다음 노드로 추적 된 Geometry 추가/업데이트/제거를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-176">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![ARTrackable 알림](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="7622e-178">손 광선</span><span class="sxs-lookup"><span data-stu-id="7622e-178">Hand Rays</span></span>

<span data-ttu-id="7622e-179">[SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API를 노출 하는 c + + 및 청사진에서 직접 광선을 포인팅 장치로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-179">You can use a hand ray as a pointing device in both C++ and Blueprints, which exposes the [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7622e-180">모든 함수 결과는 프레임 마다 변경 되므로 모두 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-180">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="7622e-181">Pure 및 비 순수형 또는 호출 가능 함수에 대 한 자세한 내용은 [함수](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)에 대 한 청사진 사용자 guid를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7622e-181">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

<span data-ttu-id="7622e-182">청사진에서 손 광선을 사용 하려면 **Windows Mixed REALITY HMD** 에서 작업을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-182">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![핸드 광선 BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="7622e-184">C + +에서 액세스 하려면 `WindowsMixedRealityFunctionLibrary.h` 호출 하는 코드 파일의 맨 위에를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-184">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="7622e-185">열거형</span><span class="sxs-lookup"><span data-stu-id="7622e-185">Enum</span></span>

<span data-ttu-id="7622e-186">또한 청사진에서 사용할 수 있는 **EHMDInputControllerButtons** 아래의 입력 사례에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-186">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![입력 컨트롤러 단추](images/unreal/input-controller-buttons.png)

<span data-ttu-id="7622e-188">C + +에서 액세스의 경우 `EHMDInputControllerButtons` enum 클래스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-188">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="7622e-189">다음은 적용 가능한 두 가지 열거 사례를 분석 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-189">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="7622e-190">**Select** -사용자가 트리거된 select 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-190">**Select** - User triggered Select event.</span></span> 
    * <span data-ttu-id="7622e-191">비행기 탭, 응시 및 커밋에 의해 또는 [음성 입력](unreal-voice-input.md) 을 사용 하도록 설정 된 "선택"을 말하는 경우 HoloLens 2에서 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-191">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](unreal-voice-input.md) enabled.</span></span> 
* <span data-ttu-id="7622e-192">사용자가 트리거 **이벤트를 트리거** 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-192">**Grasp** - User triggered Grasp event.</span></span> 
    * <span data-ttu-id="7622e-193">홀로그램에서 사용자 손가락을 닫아 HoloLens 2에서 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-193">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 

<span data-ttu-id="7622e-194">아래에 표시 된 열거형을 통해 c + +에서 손 모양에 대 한 추적 상태에 액세스할 수 있습니다 `EHMDTrackingStatus` .</span><span class="sxs-lookup"><span data-stu-id="7622e-194">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="7622e-195">다음은 적용 가능한 두 가지 열거 사례를 분석 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-195">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="7622e-196">**Nottracked** – 손 모양이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-196">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="7622e-197">**추적** –이 손을 완전히 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-197">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="7622e-198">구조체</span><span class="sxs-lookup"><span data-stu-id="7622e-198">Struct</span></span>

<span data-ttu-id="7622e-199">PointerPoseInfo 구조체는 다음 데이터에 대 한 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-199">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="7622e-200">**원점** – 손 모양</span><span class="sxs-lookup"><span data-stu-id="7622e-200">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="7622e-201">**방향** – 손 방향</span><span class="sxs-lookup"><span data-stu-id="7622e-201">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="7622e-202">**Up** – 손 모양 벡터</span><span class="sxs-lookup"><span data-stu-id="7622e-202">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="7622e-203">**방향** – 4 원수</span><span class="sxs-lookup"><span data-stu-id="7622e-203">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="7622e-204">**상태 추적** -현재 추적 상태</span><span class="sxs-lookup"><span data-stu-id="7622e-204">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="7622e-205">아래와 같이 청사진을 통해 PointerPoseInfo 구조체에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-205">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![포인터 포즈 정보 BP](images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="7622e-207">또는 c + +:</span><span class="sxs-lookup"><span data-stu-id="7622e-207">Or with C++:</span></span>

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

### <a name="functions"></a><span data-ttu-id="7622e-208">Functions</span><span class="sxs-lookup"><span data-stu-id="7622e-208">Functions</span></span>

<span data-ttu-id="7622e-209">아래에 나열 된 모든 함수는 연속 모니터링을 허용 하는 모든 프레임에서 호출 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-209">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span> 

1. <span data-ttu-id="7622e-210">**포인터 포즈 정보 가져오기** 현재 프레임의 손 모양에 대 한 전체 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-210">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span> 

<span data-ttu-id="7622e-211">청사진</span><span class="sxs-lookup"><span data-stu-id="7622e-211">Blueprint:</span></span>

![포인터 포즈 정보 가져오기](images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="7622e-213">C++:</span><span class="sxs-lookup"><span data-stu-id="7622e-213">C++:</span></span> 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="7622e-214">**Grasped** 는 현재 프레임의 Grasped 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-214">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="7622e-215">청사진</span><span class="sxs-lookup"><span data-stu-id="7622e-215">Blueprint:</span></span>

![Grasped BP](images/unreal/is-grasped-bp.png)

<span data-ttu-id="7622e-217">C++:</span><span class="sxs-lookup"><span data-stu-id="7622e-217">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. <span data-ttu-id="7622e-218">**Select 누르면** 사용자가 현재 프레임에서 select를 트리거한 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-218">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="7622e-219">청사진</span><span class="sxs-lookup"><span data-stu-id="7622e-219">Blueprint:</span></span>

![선택 프레스 BP](images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="7622e-221">C++:</span><span class="sxs-lookup"><span data-stu-id="7622e-221">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="7622e-222">**이 단추를 클릭** 하면 현재 프레임에서 이벤트 또는 단추가 트리거되는 경우 true가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-222">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="7622e-223">청사진</span><span class="sxs-lookup"><span data-stu-id="7622e-223">Blueprint:</span></span>

![단추 클릭을 클릭 합니다.](images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="7622e-225">C++:</span><span class="sxs-lookup"><span data-stu-id="7622e-225">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="7622e-226">**컨트롤러 추적 상태 가져오기** 는 현재 프레임에서 추적 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-226">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="7622e-227">청사진</span><span class="sxs-lookup"><span data-stu-id="7622e-227">Blueprint:</span></span>

![컨트롤러 추적 상태 BP 가져오기](images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="7622e-229">C++:</span><span class="sxs-lookup"><span data-stu-id="7622e-229">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a><span data-ttu-id="7622e-230">제스처</span><span class="sxs-lookup"><span data-stu-id="7622e-230">Gestures</span></span>

<span data-ttu-id="7622e-231">HoloLens 2는 공간 제스처를 추적 합니다. 즉, 이러한 제스처를 입력으로 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-231">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="7622e-232">제스처에 대 한 자세한 내용은 [HoloLens 2 기본 사용](https://docs.microsoft.com/hololens/hololens2-basic-usage) 문서에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-232">You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

<span data-ttu-id="7622e-233">**Windows Mixed Reality 공간 입력** 및 호출 하는 `WindowsMixedRealitySpatialInputFunctionLibrary.h` 코드 파일에를 추가 하 여 c + + 함수에서 청사진 함수를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-233">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![캡처 제스처](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="7622e-235">열거형</span><span class="sxs-lookup"><span data-stu-id="7622e-235">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="7622e-236">청사진</span><span class="sxs-lookup"><span data-stu-id="7622e-236">Blueprint:</span></span> 

![제스처 형식](images/unreal/gesture-type.png)

<span data-ttu-id="7622e-238">C++:</span><span class="sxs-lookup"><span data-stu-id="7622e-238">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="7622e-239">함수</span><span class="sxs-lookup"><span data-stu-id="7622e-239">Function</span></span>
<span data-ttu-id="7622e-240">함수를 사용 하 여 제스처 캡처를 사용 하거나 사용 하지 않도록 설정할 수 있습니다 `CaptureGestures` .</span><span class="sxs-lookup"><span data-stu-id="7622e-240">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="7622e-241">활성화 된 제스처가 입력 이벤트를 발생 시키면이 함수는 `true` 제스처 캡처가 성공한 경우를 반환 하 고 오류가 발생 하면를 반환 합니다 `false` .</span><span class="sxs-lookup"><span data-stu-id="7622e-241">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="7622e-242">청사진</span><span class="sxs-lookup"><span data-stu-id="7622e-242">Blueprint:</span></span>

![제스처 BP 캡처](images/unreal/capture-gestures-bp.png)

<span data-ttu-id="7622e-244">C++:</span><span class="sxs-lookup"><span data-stu-id="7622e-244">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

<span data-ttu-id="7622e-245">청사진 및 c + +: 주요 이벤트에서 찾을 수 있는 주요 이벤트는 다음과 같습니다. ![](images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="7622e-245">The following are key events, which you can find in Blueprints and C++: ![Key Events](images/unreal/key-events.png)</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="7622e-247">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="7622e-247">Next Development Checkpoint</span></span>

<span data-ttu-id="7622e-248">앞에서 설명한 실제 개발 경험을 수행 하는 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-248">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="7622e-249">여기에서 다음 구성 요소를 계속 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-249">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="7622e-250">로컬 Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="7622e-250">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="7622e-251">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-251">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7622e-252">HoloLens 카메라</span><span class="sxs-lookup"><span data-stu-id="7622e-252">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="7622e-253">언제든지 [Unreal 개발 검사점](unreal-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7622e-253">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>