---
title: 공간 인식 메시 관찰자 구성
description: MRTK에서 기본 공간 메시 관찰자를 구성 하는 방법
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 0d71a32d76624698e78b8123f427ddefc08f3d0b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144960"
---
# <a name="configuring-mesh-observers-for-device"></a><span data-ttu-id="a8a65-104">장치에 대 한 메시 관찰자 구성</span><span class="sxs-lookup"><span data-stu-id="a8a65-104">Configuring mesh observers for device</span></span>

<span data-ttu-id="a8a65-105">이 가이드에서는 Windows 혼합 현실 플랫폼 (예:)을 지 원하는 MRTK에서 기본 공간 메시 관찰자를 구성 하는 과정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-105">This guide will walk through configuring the out-of-box Spatial Mesh Observer in MRTK which supports the Windows Mixed Reality platform (i.e</span></span> <span data-ttu-id="a8a65-106">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="a8a65-106">HoloLens).</span></span> <span data-ttu-id="a8a65-107">Mixed Reality Toolkit에서 제공 되는 기본 구현은 [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-107">The default implementation provided by the Mixed Reality Toolkit is the [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span> <span data-ttu-id="a8a65-108">그러나이 문서의 많은 속성은 다른 [사용자 지정 관찰자 구현](create-data-provider.md)에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-108">Many of the properties in this article though apply for other [custom Observer implementations](create-data-provider.md).</span></span>

## <a name="profile-settings"></a><span data-ttu-id="a8a65-109">프로필 설정</span><span class="sxs-lookup"><span data-stu-id="a8a65-109">Profile settings</span></span>

<span data-ttu-id="a8a65-110">[공간 인식 시스템](spatial-awareness-getting-started.md)에 대해 공간 메시 관찰자 프로필을 구성할 때 먼저 다음 두 항목을 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-110">The following two items must be defined first when configuring a Spatial Mesh Observer profile for the [Spatial Awareness system](spatial-awareness-getting-started.md).</span></span>

1. <span data-ttu-id="a8a65-111">구체적인 관찰자 형식 구현</span><span class="sxs-lookup"><span data-stu-id="a8a65-111">The concrete observer type implementation</span></span>
1. <span data-ttu-id="a8a65-112">이 관찰자를 실행 하는 데 지원 되는 플랫폼 목록</span><span class="sxs-lookup"><span data-stu-id="a8a65-112">list of supported platform(s) to run this observer</span></span>

> [!NOTE]
> <span data-ttu-id="a8a65-113">모든 관찰자가 [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 인터페이스를 확장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-113">All observers must extend the [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![메시 관찰자 일반 설정 플랫폼 형식](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a><span data-ttu-id="a8a65-115">일반 설정</span><span class="sxs-lookup"><span data-stu-id="a8a65-115">General settings</span></span>

![메시 관찰자 일반 설정 Genral 설정](../images/spatial-awareness/MeshObserverGeneralSettings.png)

<span data-ttu-id="a8a65-117">**시작 동작**</span><span class="sxs-lookup"><span data-stu-id="a8a65-117">**Startup Behavior**</span></span>

<span data-ttu-id="a8a65-118">시작 동작은 관찰자가 처음 인스턴스화될 때 실행을 시작할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-118">The startup behavior specifies whether the observer will begin running when first instantiated.</span></span> <span data-ttu-id="a8a65-119">다음은 두 가지 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-119">The two options are:</span></span>

* <span data-ttu-id="a8a65-120">*자동 시작* -초기화 후 관찰자가 작업을 시작 하는 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-120">*Auto Start* - The default value whereby the observer will begin operation after initialization</span></span>
* <span data-ttu-id="a8a65-121">*수동 시작* -관찰자가 시작 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-121">*Manual Start* - The Observer will wait to be directed to start</span></span>

<span data-ttu-id="a8a65-122">*수동 시작* 을 사용 하는 경우 [코드를 통해 런타임 시 다시 시작 하 고 일시 중단](usage-guide.md#starting-and-stopping-mesh-observation)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-122">If using *Manual Start*, one must [resume and suspend them at runtime via code](usage-guide.md#starting-and-stopping-mesh-observation).</span></span>

<span data-ttu-id="a8a65-123">**업데이트 간격**</span><span class="sxs-lookup"><span data-stu-id="a8a65-123">**Update Interval**</span></span>

<span data-ttu-id="a8a65-124">플랫폼에서 공간 메시 데이터를 업데이트 하는 요청 사이의 시간 (초)입니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-124">The time, in seconds, between requests to the platform to update spatial mesh data.</span></span> <span data-ttu-id="a8a65-125">일반적인 값의 범위는 0.1에서 5.0 초 사이입니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-125">Typical values fall in the range of 0.1 and 5.0 seconds.</span></span>

<span data-ttu-id="a8a65-126">**고정 관찰자인가요?**</span><span class="sxs-lookup"><span data-stu-id="a8a65-126">**Is Stationary Observer**</span></span>

<span data-ttu-id="a8a65-127">관찰자가 고정된 상태를 유지할지 아니면 사용자와 함께 이동하고 업데이트할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-127">Indicates whether or not the observer is to remain stationary or to move and update with the user.</span></span> <span data-ttu-id="a8a65-128">true이면 *관찰 익스텐트에서* 정의된 볼륨이 있는 *관찰자 도형은* 시작 시 원본에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-128">If true, the *Observer Shape* with volume defined by *Observation Extents* will remain at the origin on startup.</span></span> <span data-ttu-id="a8a65-129">false이면 관찰자 공간은 사용자의 머리 뒤에 도형의 원점이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-129">If false, the Observer space will follow the user's head as the shape's origin.</span></span>

<span data-ttu-id="a8a65-130">고정 관찰자, *관찰자 도형*\* 및 *관찰 익스텐트* 속성에 정의된 대로 관찰자 공간 외부의 물리적 영역에 대해 *계산된* 메시 데이터는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-130">There will be no mesh data calculated for any physical area outside of the Observer space as defined by these properties: *Is Stationary Observer*, \*Observer Shape\*\*, and *Observation Extents*.</span></span>

<span data-ttu-id="a8a65-131">**관찰자 셰이프**</span><span class="sxs-lookup"><span data-stu-id="a8a65-131">**Observer Shape**</span></span>

<span data-ttu-id="a8a65-132">관찰자 모양은 메시 관찰자가 메시를 관찰할 때 사용할 볼륨의 유형을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-132">The observer shape defines the type of volume that the mesh observer will use when observing meshes.</span></span> <span data-ttu-id="a8a65-133">지원되는 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-133">The supported options are:</span></span>

* <span data-ttu-id="a8a65-134">*축 맞춤 큐브* - 애플리케이션 시작 시 결정된 대로 세계 좌표계의 축에 맞춰 유지되는 사각형 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-134">*Axis Aligned Cube* - Rectangular shape that stays aligned with the axes of the world coordinate system, as determined at application startup.</span></span>
* <span data-ttu-id="a8a65-135">*사용자 맞춤 큐브* - 사용자 로컬 좌표계에 맞게 회전하는 사각형 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-135">*User Aligned Cube* - Rectangular shape that rotates to align with the users local coordinate system.</span></span>
* <span data-ttu-id="a8a65-136">*구* - 세계 공간 원점의 중심이 있는 구형 볼륨입니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-136">*Sphere* - A spherical volume with a center at the world space origin.</span></span> <span data-ttu-id="a8a65-137">*관찰 익스텐트* 속성의 X 값은 구의 반지름으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-137">The X value of the *Observation Extents* property will be used as the radius of the sphere.</span></span>

<span data-ttu-id="a8a65-138">**관찰 익스텐트**</span><span class="sxs-lookup"><span data-stu-id="a8a65-138">**Observation Extents**</span></span>

<span data-ttu-id="a8a65-139">관찰 익스텐트 는 메시가 관찰될 관찰 지점으로부터의 거리를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-139">The observation extents define the distance from the observation point that meshes will be observed.</span></span>

### <a name="physics-settings"></a><span data-ttu-id="a8a65-140">물리학 설정</span><span class="sxs-lookup"><span data-stu-id="a8a65-140">Physics settings</span></span>

![Mesh Observer Physics 설정](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

<span data-ttu-id="a8a65-142">**물리학 계층**</span><span class="sxs-lookup"><span data-stu-id="a8a65-142">**Physics Layer**</span></span>

<span data-ttu-id="a8a65-143">Unity 물리학 및 RayCast 시스템과 상호 작용하기 위해 공간 메시 개체를 배치할 물리학 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-143">The physics layer on which spatial mesh objects will be placed in order to interact with the Unity Physics and RayCast systems.</span></span>

> [!NOTE]
> <span data-ttu-id="a8a65-144">Mixed Reality 도구 키트는 공간 인식 관찰자가 사용할 *계층 31을* 기본적으로 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-144">The Mixed Reality Toolkit reserves *layer 31* by default for use by Spatial Awareness observers.</span></span>

<span data-ttu-id="a8a65-145">**정규 다시 계산**</span><span class="sxs-lookup"><span data-stu-id="a8a65-145">**Recalculate Normals**</span></span>

<span data-ttu-id="a8a65-146">메시 관찰자가 관찰 후 망상의 법선을 다시 계산할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-146">Specifies whether or not the mesh observer will recalculate the normals of the mesh following observation.</span></span> <span data-ttu-id="a8a65-147">이 설정은 응용 프로그램이 메시를 사용 하 여 반환 하지 않는 플랫폼에서 유효한 법선 데이터를 포함 하는 메시를 받도록 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-147">This setting is available to ensure applications receive meshes that contain valid normals data on platforms that do not return them with meshes.</span></span>

### <a name="level-of-detail-settings"></a><span data-ttu-id="a8a65-148">세부 정보 설정 수준</span><span class="sxs-lookup"><span data-stu-id="a8a65-148">Level of detail settings</span></span>

![메시 관찰자 수준 세부 설정](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

<span data-ttu-id="a8a65-150">**세부 정보 수준**</span><span class="sxs-lookup"><span data-stu-id="a8a65-150">**Level of Detail**</span></span>

<span data-ttu-id="a8a65-151">공간 메시 데이터의 세부 수준 (LOD)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-151">Specifies the level of detail (LOD) of the spatial mesh data.</span></span> <span data-ttu-id="a8a65-152">현재 정의 된 값은 거칠게, 세밀 하 고 사용자 지정입니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-152">Currently defined values are Coarse, Fine and Custom.</span></span>

* <span data-ttu-id="a8a65-153">*거칠게* 는 응용 프로그램 성능에 미치는 영향을 최소화 하 고 탐색/평면 검색에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-153">*Coarse* - Places a smaller impact on application performance and is an excellent choice for navigation/plane finding.</span></span>

* <span data-ttu-id="a8a65-154">*중간 규모* 의 설정은 폐색 세부 정보 뿐만 아니라 규모가 뛰어난 기능, 층 및 벽 모두를 지속적으로 검색 하는 환경에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-154">*Medium* - Balanced setting often useful for experiences that continually scan the environment for both large features, floors and walls, as well as occlusion details.</span></span>

* <span data-ttu-id="a8a65-155">*자세히* -일반적으로 응용 프로그램 성능에 더 큰 영향을 폐색 메시를 위한 유용한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-155">*Fine* - Generally exacts a higher impact on application performance and is a great option for occlusion meshes.</span></span>

* <span data-ttu-id="a8a65-156">*사용자 지정* -응용 프로그램에서 *삼각형/입방 측정기* 속성을 지정 하 고, 응용 프로그램에서 공간 메시 관찰자의 정확도와 성능 영향을 조정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-156">*Custom* - Requires the application to specify the *Triangles / Cubic Meter* property and allows applications to tune the accuracy vs. performance impact of the spatial mesh observer.</span></span>

> [!NOTE]
> <span data-ttu-id="a8a65-157">모든 플랫폼에서 모든 *삼각형/입방 미터* 값을 허용 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-157">It is not guaranteed that all *Triangles/Cubic Meter* values are honored by all platforms.</span></span> <span data-ttu-id="a8a65-158">사용자 지정 LOD를 사용 하는 경우 실험 및 프로 파일링은 매우 권장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-158">Experimentation and profiling is highly recommended when using a custom LOD.</span></span>

<span data-ttu-id="a8a65-159">**입방 미터 당 삼각형**</span><span class="sxs-lookup"><span data-stu-id="a8a65-159">**Triangles per Cubic Meter**</span></span>

<span data-ttu-id="a8a65-160">**Detail 속성 수준** 에 대 한 *사용자 지정* 설정을 사용 하는 경우 유효 하 고 공간 메시의 삼각형 밀도를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-160">Valid when using the *Custom* setting for the **Level of Detail** property and specifies the triangle density for the spatial mesh.</span></span>

### <a name="display-settings"></a><span data-ttu-id="a8a65-161">디스플레이 설정</span><span class="sxs-lookup"><span data-stu-id="a8a65-161">Display settings</span></span>

![메시 관찰자 표시 설정](../images/spatial-awareness/MeshObserverDisplaySettings.png)

<span data-ttu-id="a8a65-163">**표시 옵션**</span><span class="sxs-lookup"><span data-stu-id="a8a65-163">**Display Option**</span></span>

<span data-ttu-id="a8a65-164">관찰자가 공간 메시를 표시 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-164">Specifies how spatial meshes are to be displayed by the observer.</span></span> <span data-ttu-id="a8a65-165">지원되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-165">Supported values are:</span></span>

* <span data-ttu-id="a8a65-166">*없음* -관찰자가 메시를 렌더링 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-166">*None* - Observer will not render the mesh</span></span>
* <span data-ttu-id="a8a65-167">*가시-* 표시 되는 *재질* 을 사용 하 여 메시 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-167">*Visible* - Mesh data will be visible using the *Visible Material*</span></span>
* <span data-ttu-id="a8a65-168">*폐색* - 메시 데이터는 폐색 재질을 사용하여 장면의 항목을 *폐색합니다.*</span><span class="sxs-lookup"><span data-stu-id="a8a65-168">*Occlusion* - Mesh data will be occlude items in scene using the *Occlusion Material*</span></span>

![공간 인식 시스템 구현 선택](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

<span data-ttu-id="a8a65-170">공간 관찰자는 [코드를 통해 런타임에 다시 시작/일시 중단될](usage-guide.md#starting-and-stopping-mesh-observation) 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-170">Spatial Observers can be [resumed/suspended at runtime via code.](usage-guide.md#starting-and-stopping-mesh-observation)</span></span>

> [!WARNING]
> <span data-ttu-id="a8a65-171">*표시 옵션을* *없음으로* 설정해도 관찰자의 실행이 **중지되지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-171">Setting *Display Option* to *None* does **NOT** stop the observer from running.</span></span> <span data-ttu-id="a8a65-172">모든 관찰자를 중지하려는 경우 애플리케이션은 를 통해 모든 관찰자를 일시 중단해야 합니다. [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span><span class="sxs-lookup"><span data-stu-id="a8a65-172">If you wish to stop all observers, applications will need to suspend all observers via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span></span>

<span data-ttu-id="a8a65-173">**표시되는 재질**</span><span class="sxs-lookup"><span data-stu-id="a8a65-173">**Visible Material**</span></span>

<span data-ttu-id="a8a65-174">공간 메시를 시각화할 때 사용할 재질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-174">Indicates the material to be used when visualizing the spatial mesh.</span></span>

<span data-ttu-id="a8a65-175">**폐색 재질**</span><span class="sxs-lookup"><span data-stu-id="a8a65-175">**Occlusion Material**</span></span>

<span data-ttu-id="a8a65-176">공간 메시가 홀로그램을 가리는 데 사용할 재질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8a65-176">Indicates the material to be used to cause the spatial mesh to occlude holograms.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8a65-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8a65-177">See also</span></span>

* [<span data-ttu-id="a8a65-178">공간 인식 시스템</span><span class="sxs-lookup"><span data-stu-id="a8a65-178">Spatial Awareness System</span></span>](spatial-awareness-getting-started.md)
* [<span data-ttu-id="a8a65-179">코드를 통해 공간 인식 시스템 구성</span><span class="sxs-lookup"><span data-stu-id="a8a65-179">Configuring Spatial Awareness system via Code</span></span>](usage-guide.md)
* [<span data-ttu-id="a8a65-180">IMixedRealitySpatialAwarenessObserver API 설명서</span><span class="sxs-lookup"><span data-stu-id="a8a65-180">IMixedRealitySpatialAwarenessObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [<span data-ttu-id="a8a65-181">IMixedRealitySpatialAwarenessMeshObserver API 설명서</span><span class="sxs-lookup"><span data-stu-id="a8a65-181">IMixedRealitySpatialAwarenessMeshObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [<span data-ttu-id="a8a65-182">BaseSpatialObserver API 설명서</span><span class="sxs-lookup"><span data-stu-id="a8a65-182">BaseSpatialObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
