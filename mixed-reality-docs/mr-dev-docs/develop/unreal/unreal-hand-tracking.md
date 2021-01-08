---
title: Unreal의 직접 추적
description: Unreal mixed reality 앱에서 직접 추적 입력, 포즈, 손 모양 및 라이브 링크 애니메이션을 사용 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, 직접 추적, Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed reality, 개발, 기능, 설명서, 가이드, holograms, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: e482c93233348325736d2c224788e9174c1f3b67
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010163"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="9f0ad-104">Unreal의 직접 추적</span><span class="sxs-lookup"><span data-stu-id="9f0ad-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="9f0ad-105">손으로 추적 시스템은 사용자의 palms와 손가락을 입력으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="9f0ad-106">모든 손가락의 위치 및 회전에 대 한 데이터, 전체 palm 및 핸드 제스처를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> <span data-ttu-id="9f0ad-107">Unreal 4.26부터 수동 추적은 Unreal HeadMountedDisplay 플러그 인을 기반으로 하며 모든 XR 플랫폼과 장치에서 공통 API를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-107">Starting in Unreal 4.26, hand tracking is based on the Unreal HeadMountedDisplay plugin and uses a common API across all XR platforms and devices.</span></span> <span data-ttu-id="9f0ad-108">기능은 Windows Mixed Reality 및 OpenXR 시스템 모두에서 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-108">Functionality is the same for both Windows Mixed Reality and OpenXR systems.</span></span>

## <a name="hand-pose"></a><span data-ttu-id="9f0ad-109">직접 포즈</span><span class="sxs-lookup"><span data-stu-id="9f0ad-109">Hand pose</span></span>

<span data-ttu-id="9f0ad-110">직접 사용 하면 사용자의 손으로, 손가락을 입력으로 사용 하 여 청사진과 c + +에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-110">Hand pose lets you track and use the hands and fingers of your users as input, which can be accessed in both Blueprints and C++.</span></span> <span data-ttu-id="9f0ad-111">Unreal API는 틱이 Unreal 엔진과 동기화 된 좌표계로 데이터를 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

![직접 기초](../native/images/hand-skeleton.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a><span data-ttu-id="9f0ad-113">손 모양 링크 애니메이션</span><span class="sxs-lookup"><span data-stu-id="9f0ad-113">Hand Live Link Animation</span></span>

<span data-ttu-id="9f0ad-114">손 포즈는 [라이브 링크 플러그 인](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)을 사용 하 여 애니메이션에 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-114">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="9f0ad-115">Windows Mixed Reality 및 라이브 링크 플러그 인을 사용 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="9f0ad-115">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span>
1. <span data-ttu-id="9f0ad-116">**창 > 라이브 링크** 를 선택 하 여 라이브 링크 편집기 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-116">Select **Window > Live Link** to open the Live Link editor window.</span></span>
2. <span data-ttu-id="9f0ad-117">**원본** 선택 및 **Windows Mixed Reality 추적 원본** 사용</span><span class="sxs-lookup"><span data-stu-id="9f0ad-117">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![라이브 링크 소스](images/unreal/live-link-source.png)

<span data-ttu-id="9f0ad-119">소스를 사용 하도록 설정 하 고 애니메이션 자산을 연 후에는 **장면 미리 보기** 탭에서 **애니메이션** 섹션을 확장 하 여 추가 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-119">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![라이브 링크 애니메이션](images/unreal/live-link-animation.png)

<span data-ttu-id="9f0ad-121">손 모양 애니메이션 계층은에서와 동일 합니다 `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="9f0ad-121">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="9f0ad-122">**WindowsMixedRealityHandTrackingLiveLinkRemapAsset** 를 사용 하 여 애니메이션의 대상을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-122">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![라이브 링크 애니메이션 2](images/unreal/live-link-animation2.png)

<span data-ttu-id="9f0ad-124">편집기에서 서브클래싱 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-124">It can also be subclassed in the editor:</span></span>

![라이브 링크 다시 매핑](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a><span data-ttu-id="9f0ad-126">손 모양 메시</span><span class="sxs-lookup"><span data-stu-id="9f0ad-126">Hand Mesh</span></span>

### <a name="hand-mesh-as-a-tracked-geometry"></a><span data-ttu-id="9f0ad-127">추적 되는 기 하 도형으로 직접 메시</span><span class="sxs-lookup"><span data-stu-id="9f0ad-127">Hand Mesh as a Tracked Geometry</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f0ad-128">OpenXR에서 추적 되는 기 하 도형으로 손 모양의 메시를 가져오려면 **활성화 된 추적 기 하 도형** 으로 **설정 된 손 모양 사용** 을 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-128">Getting hand meshes as a tracked geometry in OpenXR requires you to call **Set Use Hand Mesh** with **Enabled Tracking Geometry**.</span></span>

<span data-ttu-id="9f0ad-129">해당 모드를 사용 하도록 설정 하려면 설정 된 **추적 기 하 도형을** 사용 하 여 **핸드 메시 사용** 을 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-129">To enable that mode you should call **Set Use Hand Mesh** with **Enabled Tracking Geometry**:</span></span>

![설정에 연결 된 이벤트 시작 재생의 청사진 활성화 된 추적 기 하 도형 모드를 사용 하 여 설정 된 손 모양 메시 함수 사용](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> <span data-ttu-id="9f0ad-131">두 모드를 동시에 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-131">It’s not possible for both modes to be enabled at the same time.</span></span> <span data-ttu-id="9f0ad-132">하나를 사용 하도록 설정 하면 다른 하나는 자동으로 사용 하지 않도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-132">If you enable one, the other is automatically disabled.</span></span>

### <a name="accessing-hand-mesh-data"></a><span data-ttu-id="9f0ad-133">손 모양 메시 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="9f0ad-133">Accessing Hand Mesh Data</span></span>

![손 모양 메시](images/unreal/hand-mesh.png)

<span data-ttu-id="9f0ad-135">직접 메시 데이터에 액세스 하려면 먼저 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-135">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="9f0ad-136">**Arsessionconfig** 자산을 선택 하 고 **AR 설정-> 월드 매핑** 설정을 확장 하 고 **추적 된 기 하 도형에서 메시 데이터 생성** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-136">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span>

<span data-ttu-id="9f0ad-137">기본 메시 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-137">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="9f0ad-138">폐색에 대 한 메시 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="9f0ad-138">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="9f0ad-139">메시 데이터의 충돌 생성</span><span class="sxs-lookup"><span data-stu-id="9f0ad-139">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="9f0ad-140">메시 데이터의 Nav 메시 생성</span><span class="sxs-lookup"><span data-stu-id="9f0ad-140">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="9f0ad-141">와이어 프레임으로 메시 데이터 렌더링 – 생성 된 메시를 표시 하는 디버그 매개 변수</span><span class="sxs-lookup"><span data-stu-id="9f0ad-141">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="9f0ad-142">이러한 매개 변수 값은 공간 매핑 메시 및 손 모양 메시 기본값으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-142">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="9f0ad-143">모든 망상의 청사진 또는 코드에서 언제 든 지 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-143">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="9f0ad-144">C + + API 참조</span><span class="sxs-lookup"><span data-stu-id="9f0ad-144">C++ API Reference</span></span>
<span data-ttu-id="9f0ad-145">`EEARObjectClassification`를 사용 하 여 모든 추적 가능 개체에서 손 모양 값을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-145">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

<span data-ttu-id="9f0ad-146">다음 대리자는 시스템에서 손 메시를 포함 하 여 추적 가능 개체를 검색할 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-146">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span>

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

<span data-ttu-id="9f0ad-147">대리자 처리기가 아래 함수 시그니처를 따르는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-147">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="9f0ad-148">다음을 통해 메시 데이터에 액세스할 수 있습니다  `UARTrackedGeometry::GetUnderlyingMesh` .</span><span class="sxs-lookup"><span data-stu-id="9f0ad-148">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a><span data-ttu-id="9f0ad-149">청사진 API 참조</span><span class="sxs-lookup"><span data-stu-id="9f0ad-149">Blueprint API Reference</span></span>

<span data-ttu-id="9f0ad-150">청사진에서 손 모양 망을 사용 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-150">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="9f0ad-151">청사진 행위자에 **ARTrackableNotify** 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="9f0ad-151">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![ARTrackable 알림](images/unreal/ar-trackable-notify.png)

2. <span data-ttu-id="9f0ad-153">**세부 정보** 패널로 이동 하 여 **이벤트** 섹션을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-153">Go to the **Details** panel and expand the **Events** section.</span></span>

![ARTrackable 알림 2](images/unreal/ar-trackable-notify2.png)

3. <span data-ttu-id="9f0ad-155">이벤트 그래프의 다음 노드로 추적 된 Geometry 추가/업데이트/제거를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-155">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![ARTrackable 알림](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a><span data-ttu-id="9f0ad-157">OpenXR의 핸드 메시 시각화</span><span class="sxs-lookup"><span data-stu-id="9f0ad-157">Hand Mesh visualization in OpenXR</span></span>

<span data-ttu-id="9f0ad-158">손 메시를 시각화 하는 권장 방법은 [Microsoft OpenXR 플러그 인과](https://github.com/microsoft/Microsoft-OpenXR-Unreal)함께 대규모의 XRVisualization 플러그 인을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-158">The recommended way to visualize hand mesh is to use Epic’s XRVisualization plugin together with the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span> 

<span data-ttu-id="9f0ad-159">그런 다음 청사진 편집기에서 사용 하도록 설정 된 **XRVisualization** 를 매개 변수로 사용 하 여 [Microsoft OpenXR 플러그 인](https://github.com/microsoft/Microsoft-OpenXR-Unreal) 에서 **Set use 손 메시** 함수를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-159">Then in the blueprint editor, you should use **Set Use Hand Mesh** function from the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) with **Enabled XRVisualization** as a parameter:</span></span>

![설정에 연결 된 이벤트 시작 재생의 청사진 사용 하도록 설정 된 손 모양 메시 함수를 사용 하는 xrvisualization 모드](images/unreal-hand-tracking-img-05.png)

<span data-ttu-id="9f0ad-161">렌더링 프로세스를 관리 하려면 XRVisualization에서 **렌더링 동작 컨트롤러** 를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-161">To manage the rendering process, you should use **Render Motion Controller** from XRVisualization:</span></span>

![렌더링 동작 컨트롤러 함수에 연결 된 get 모션 컨트롤러 데이터 함수의 청사진](images/unreal-hand-tracking-img-06.png)

<span data-ttu-id="9f0ad-163">결과:</span><span class="sxs-lookup"><span data-stu-id="9f0ad-163">The result:</span></span>

![실제 인간 오버레이할의 디지털 핸드 이미지 이미지](images/unreal-hand-tracking-img-07.png) 

<span data-ttu-id="9f0ad-165">사용자 지정 셰이더를 사용 하 여 손을 메시를 그리는 등 더 복잡 한 작업이 필요한 경우 메시를 추적 된 기 하 도형으로 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-165">If you need anything more complicated, such as drawing a hand mesh with a custom shader, you need to get the meshes as a tracked geometry.</span></span> 

## <a name="hand-rays"></a><span data-ttu-id="9f0ad-166">손 광선</span><span class="sxs-lookup"><span data-stu-id="9f0ad-166">Hand rays</span></span>

<span data-ttu-id="9f0ad-167">개체를 가져오거나 단추를 누르는 것과 같은 닫기 작업에 대해 작업을 수행 하는 것이 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-167">Getting hand pose works for close interactions like grabbing objects or pressing buttons.</span></span> <span data-ttu-id="9f0ad-168">그러나 사용자에 게 멀리 떨어져 있는 holograms 작업 해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-168">However, sometimes you need to work with holograms that are far away from your users.</span></span> <span data-ttu-id="9f0ad-169">이는 c + + 및 청사진 모두를 가리키는 장치로 사용할 수 있는 직접 광선을 사용 하 여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-169">This can be accomplished with hand rays, which can be used as pointing devices in both C++ and Blueprints.</span></span> <span data-ttu-id="9f0ad-170">손 모양에서 먼 점으로 광선을 그릴 수 있으며, Unreal 레이 추적에서 몇 가지 도움을 받을 수 있습니다. 그렇지 않은 경우에는 연결 되지 않은 홀로그램을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-170">You can draw a ray from your hand to a far point and, with some help from Unreal ray tracing, select a hologram that would otherwise be out of reach.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="9f0ad-171">모든 함수 결과는 프레임 마다 변경 되므로 모두 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-171">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="9f0ad-172">Pure 및 비 순수형 또는 호출 가능 함수에 대 한 자세한 내용은 [함수](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)에 대 한 청사진 사용자 guid를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-172">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a><span data-ttu-id="9f0ad-173">제스처</span><span class="sxs-lookup"><span data-stu-id="9f0ad-173">Gestures</span></span>

<span data-ttu-id="9f0ad-174">HoloLens 2는 공간 제스처를 추적 합니다. 즉, 이러한 제스처를 입력으로 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-174">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="9f0ad-175">제스처 추적은 구독 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-175">Gesture tracking is based on a subscription model.</span></span> <span data-ttu-id="9f0ad-176">"제스처 구성" 함수를 사용 하 여 추적 하려는 제스처를 장치에 알려야 합니다.  제스처에 대 한 자세한 내용은 [HoloLens 2 기본 사용](https://docs.microsoft.com/hololens/hololens2-basic-usage) 문서에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-176">You should use the “Configure Gestures” function to tell the device which gestures you want to track.  You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="9f0ad-177">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="9f0ad-177">Next Development Checkpoint</span></span>

<span data-ttu-id="9f0ad-178">앞에서 설명한 Unreal 개발 과정을 따르고 있다면 현재 MRTK 핵심 구성 요소를 살펴보는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-178">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="9f0ad-179">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-179">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f0ad-180">로컬 Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="9f0ad-180">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="9f0ad-181">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-181">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f0ad-182">HoloLens 카메라</span><span class="sxs-lookup"><span data-stu-id="9f0ad-182">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="9f0ad-183">언제든지 [Unreal 개발 검사점](unreal-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f0ad-183">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
