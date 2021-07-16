---
title: 디바이스에 대한 메시 관찰자 구성
description: MRTK에서 첫 번째 공간 메시 관찰자를 구성하는 방법
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: aba49e88d4fc555a88fe42e4b09858f1d2453ddc
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281937"
---
# <a name="configuring-mesh-observers-for-device"></a><span data-ttu-id="1d7ab-104">디바이스에 대한 메시 관찰자 구성</span><span class="sxs-lookup"><span data-stu-id="1d7ab-104">Configuring mesh observers for device</span></span>

<span data-ttu-id="1d7ab-105">이 가이드에서는 Windows Mixed Reality 플랫폼을 지원하는 MRTK에서 첫 번째 공간 메시 관찰자를 구성하는 과정을 안내합니다(즉,</span><span class="sxs-lookup"><span data-stu-id="1d7ab-105">This guide will walk through configuring the out-of-box Spatial Mesh Observer in MRTK which supports the Windows Mixed Reality platform (i.e</span></span> <span data-ttu-id="1d7ab-106">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="1d7ab-106">HoloLens).</span></span> <span data-ttu-id="1d7ab-107">Mixed Reality Toolkit 제공되는 기본 구현은 [WindowsMixedRealitySpatialMeshObserver 클래스입니다.](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="1d7ab-107">The default implementation provided by the Mixed Reality Toolkit is the [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span> <span data-ttu-id="1d7ab-108">그러나 이 문서의 많은 속성은 다른 사용자 지정 관찰자 구현 에 [적용됩니다.](create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="1d7ab-108">Many of the properties in this article though apply for other [custom Observer implementations](create-data-provider.md).</span></span>

## <a name="profile-settings"></a><span data-ttu-id="1d7ab-109">프로필 설정</span><span class="sxs-lookup"><span data-stu-id="1d7ab-109">Profile settings</span></span>

<span data-ttu-id="1d7ab-110">[공간 인식 시스템에](spatial-awareness-getting-started.md)대한 공간 메시 관찰자 프로필을 구성할 때 다음 두 항목을 먼저 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-110">The following two items must be defined first when configuring a Spatial Mesh Observer profile for the [Spatial Awareness system](spatial-awareness-getting-started.md).</span></span>

1. <span data-ttu-id="1d7ab-111">구체적인 관찰자 형식 구현</span><span class="sxs-lookup"><span data-stu-id="1d7ab-111">The concrete observer type implementation</span></span>
1. <span data-ttu-id="1d7ab-112">이 관찰자를 실행할 수 있는 지원되는 플랫폼 목록</span><span class="sxs-lookup"><span data-stu-id="1d7ab-112">list of supported platform(s) to run this observer</span></span>

> [!NOTE]
> <span data-ttu-id="1d7ab-113">모든 관찰자는 [IMixedRealitySpatialAwarenessObserver 인터페이스를](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 확장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-113">All observers must extend the [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Mesh Observer 일반 설정 플랫폼 유형](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a><span data-ttu-id="1d7ab-115">일반 설정</span><span class="sxs-lookup"><span data-stu-id="1d7ab-115">General settings</span></span>

![Mesh Observer 일반 설정 Genral 설정](../images/spatial-awareness/MeshObserverGeneralSettings.png)

<span data-ttu-id="1d7ab-117">**시작 동작**</span><span class="sxs-lookup"><span data-stu-id="1d7ab-117">**Startup Behavior**</span></span>

<span data-ttu-id="1d7ab-118">시작 동작은 관찰자가 처음 인스턴스화될 때 실행을 시작할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-118">The startup behavior specifies whether the observer will begin running when first instantiated.</span></span> <span data-ttu-id="1d7ab-119">다음은 두 가지 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-119">The two options are:</span></span>

* <span data-ttu-id="1d7ab-120">*자동 시작* - 관찰자가 초기화 후 작업을 시작하는 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-120">*Auto Start* - The default value whereby the observer will begin operation after initialization</span></span>
* <span data-ttu-id="1d7ab-121">*수동 시작* - 관찰자가 시작하도록 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-121">*Manual Start* - The Observer will wait to be directed to start</span></span>

<span data-ttu-id="1d7ab-122">수동 *시작* 를 사용하는 경우 [코드를 통해 런타임에](usage-guide.md#starting-and-stopping-mesh-observation)다시 시작하고 일시 중단해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-122">If using *Manual Start*, one must [resume and suspend them at runtime via code](usage-guide.md#starting-and-stopping-mesh-observation).</span></span>

<span data-ttu-id="1d7ab-123">**업데이트 간격**</span><span class="sxs-lookup"><span data-stu-id="1d7ab-123">**Update Interval**</span></span>

<span data-ttu-id="1d7ab-124">공간 메시 데이터를 업데이트하기 위한 플랫폼 요청 사이의 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-124">The time, in seconds, between requests to the platform to update spatial mesh data.</span></span> <span data-ttu-id="1d7ab-125">일반적인 값은 0.1 및 5.0초 범위에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-125">Typical values fall in the range of 0.1 and 5.0 seconds.</span></span>

<span data-ttu-id="1d7ab-126">**고정 관찰자인가요?**</span><span class="sxs-lookup"><span data-stu-id="1d7ab-126">**Is Stationary Observer**</span></span>

<span data-ttu-id="1d7ab-127">관찰자가 고정된 상태를 유지할지 아니면 사용자와 함께 이동하고 업데이트할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-127">Indicates whether or not the observer is to remain stationary or to move and update with the user.</span></span> <span data-ttu-id="1d7ab-128">true이면 *관찰 익스텐트에서* 정의된 볼륨이 있는 *관찰자 도형은* 시작 시 원본에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-128">If true, the *Observer Shape* with volume defined by *Observation Extents* will remain at the origin on startup.</span></span> <span data-ttu-id="1d7ab-129">false이면 관찰자 공간은 사용자의 머리 뒤에 도형의 원점이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-129">If false, the Observer space will follow the user's head as the shape's origin.</span></span>

<span data-ttu-id="1d7ab-130">고정 관찰자, *관찰자 도형*\* 및 *관찰 익스텐트* 속성에 정의된 대로 관찰자 공간 외부의 물리적 영역에 대해 *계산된* 메시 데이터는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-130">There will be no mesh data calculated for any physical area outside of the Observer space as defined by these properties: *Is Stationary Observer*, \*Observer Shape\*\*, and *Observation Extents*.</span></span>

<span data-ttu-id="1d7ab-131">**관찰자 도형**</span><span class="sxs-lookup"><span data-stu-id="1d7ab-131">**Observer Shape**</span></span>

<span data-ttu-id="1d7ab-132">관찰자 모양은 메시 관찰자가 메시를 관찰할 때 사용할 볼륨의 유형을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-132">The observer shape defines the type of volume that the mesh observer will use when observing meshes.</span></span> <span data-ttu-id="1d7ab-133">지원되는 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-133">The supported options are:</span></span>

* <span data-ttu-id="1d7ab-134">*축 맞춤 큐브* - 애플리케이션 시작 시 결정된 대로 세계 좌표계의 축에 맞춰 유지되는 사각형 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-134">*Axis Aligned Cube* - Rectangular shape that stays aligned with the axes of the world coordinate system, as determined at application startup.</span></span>
* <span data-ttu-id="1d7ab-135">*사용자 맞춤 큐브* - 사용자 로컬 좌표계에 맞게 회전하는 사각형 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-135">*User Aligned Cube* - Rectangular shape that rotates to align with the users local coordinate system.</span></span>
* <span data-ttu-id="1d7ab-136">*구* - 세계 우주 원점의 중심이 있는 구형 볼륨입니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-136">*Sphere* - A spherical volume with a center at the world space origin.</span></span> <span data-ttu-id="1d7ab-137">*관찰 익스텐트* 속성의 X 값은 구의 반지름으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-137">The X value of the *Observation Extents* property will be used as the radius of the sphere.</span></span>

<span data-ttu-id="1d7ab-138">**관찰 익스텐트**</span><span class="sxs-lookup"><span data-stu-id="1d7ab-138">**Observation Extents**</span></span>

<span data-ttu-id="1d7ab-139">관찰 익스텐트 는 메시가 관찰될 관찰 지점으로부터의 거리를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-139">The observation extents define the distance from the observation point that meshes will be observed.</span></span>

### <a name="physics-settings"></a><span data-ttu-id="1d7ab-140">물리학 설정</span><span class="sxs-lookup"><span data-stu-id="1d7ab-140">Physics settings</span></span>

![Mesh Observer Physics 설정](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

<span data-ttu-id="1d7ab-142">**물리학 계층**</span><span class="sxs-lookup"><span data-stu-id="1d7ab-142">**Physics Layer**</span></span>

<span data-ttu-id="1d7ab-143">Unity 물리학 및 RayCast 시스템과 상호 작용하기 위해 공간 메시 개체를 배치할 물리학 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-143">The physics layer on which spatial mesh objects will be placed in order to interact with the Unity Physics and RayCast systems.</span></span>

> [!NOTE]
> <span data-ttu-id="1d7ab-144">Mixed Reality Toolkit 공간 인식 관찰자가 사용할 *계층 31을* 기본적으로 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-144">The Mixed Reality Toolkit reserves *layer 31* by default for use by Spatial Awareness observers.</span></span>

<span data-ttu-id="1d7ab-145">**정규 다시 계산**</span><span class="sxs-lookup"><span data-stu-id="1d7ab-145">**Recalculate Normals**</span></span>

<span data-ttu-id="1d7ab-146">메시 관찰자가 관찰 후 메시의 법선 다시 계산 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-146">Specifies whether or not the mesh observer will recalculate the normals of the mesh following observation.</span></span> <span data-ttu-id="1d7ab-147">이 설정은 애플리케이션이 메시와 함께 반환하지 않는 플랫폼에서 유효한 일반 데이터가 포함된 메시를 수신하도록 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-147">This setting is available to ensure applications receive meshes that contain valid normals data on platforms that do not return them with meshes.</span></span>

### <a name="level-of-detail-settings"></a><span data-ttu-id="1d7ab-148">세부 정보 설정 수준</span><span class="sxs-lookup"><span data-stu-id="1d7ab-148">Level of detail settings</span></span>

![메시 관찰자 세부 정보 수준 설정](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

<span data-ttu-id="1d7ab-150">**세부 정보 수준**</span><span class="sxs-lookup"><span data-stu-id="1d7ab-150">**Level of Detail**</span></span>

<span data-ttu-id="1d7ab-151">공간 메시 데이터의 LOD(세부 정보 수준)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-151">Specifies the level of detail (LOD) of the spatial mesh data.</span></span> <span data-ttu-id="1d7ab-152">현재 정의된 값은 거친 값, 미세 및 사용자 지정입니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-152">Currently defined values are Coarse, Fine and Custom.</span></span>

* <span data-ttu-id="1d7ab-153">*거친* - 애플리케이션 성능에 더 작은 영향을 미치며 탐색/평면 찾기에 매우 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-153">*Coarse* - Places a smaller impact on application performance and is an excellent choice for navigation/plane finding.</span></span>

* <span data-ttu-id="1d7ab-154">*중간* - 분산 설정은 환경의 큰 기능, 바닥 및 벽뿐만 아니라 폐색 세부 정보를 지속적으로 검사하는 환경에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-154">*Medium* - Balanced setting often useful for experiences that continually scan the environment for both large features, floors and walls, as well as occlusion details.</span></span>

* <span data-ttu-id="1d7ab-155">*미세* - 일반적으로 애플리케이션 성능에 더 높은 영향을 미치며 폐색 메시에 적합한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-155">*Fine* - Generally exacts a higher impact on application performance and is a great option for occlusion meshes.</span></span>

* <span data-ttu-id="1d7ab-156">*사용자 지정* - 애플리케이션에서 *삼각형/입방형 미터* 속성을 지정해야 하며 애플리케이션이 공간 메시 관찰자의 정확도와 성능 영향을 조정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-156">*Custom* - Requires the application to specify the *Triangles / Cubic Meter* property and allows applications to tune the accuracy vs. performance impact of the spatial mesh observer.</span></span>

> [!NOTE]
> <span data-ttu-id="1d7ab-157">모든 *삼각형/입방 미터* 값이 모든 플랫폼에서 보장되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-157">It is not guaranteed that all *Triangles/Cubic Meter* values are honored by all platforms.</span></span> <span data-ttu-id="1d7ab-158">사용자 지정 LOD를 사용하는 경우 실험 및 프로파일링이 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-158">Experimentation and profiling is highly recommended when using a custom LOD.</span></span>

<span data-ttu-id="1d7ab-159">**입방 미터당 삼각형**</span><span class="sxs-lookup"><span data-stu-id="1d7ab-159">**Triangles per Cubic Meter**</span></span>

<span data-ttu-id="1d7ab-160">**세부 정보 수준** 속성에 사용자 *지정* 설정을 사용할 때 유효하며 공간 메시의 삼각형 밀도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-160">Valid when using the *Custom* setting for the **Level of Detail** property and specifies the triangle density for the spatial mesh.</span></span>

### <a name="display-settings"></a><span data-ttu-id="1d7ab-161">디스플레이 설정</span><span class="sxs-lookup"><span data-stu-id="1d7ab-161">Display settings</span></span>

![메시 관찰자 표시 설정](../images/spatial-awareness/MeshObserverDisplaySettings.png)

<span data-ttu-id="1d7ab-163">**표시 옵션**</span><span class="sxs-lookup"><span data-stu-id="1d7ab-163">**Display Option**</span></span>

<span data-ttu-id="1d7ab-164">관찰자가 공간 메시를 표시하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-164">Specifies how spatial meshes are to be displayed by the observer.</span></span> <span data-ttu-id="1d7ab-165">지원되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-165">Supported values are:</span></span>

* <span data-ttu-id="1d7ab-166">*없음* - 관찰자가 메시를 렌더링하지 않음</span><span class="sxs-lookup"><span data-stu-id="1d7ab-166">*None* - Observer will not render the mesh</span></span>
* <span data-ttu-id="1d7ab-167">*표시* - 메시 데이터는 표시되는 *재질을* 사용하여 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-167">*Visible* - Mesh data will be visible using the *Visible Material*</span></span>
* <span data-ttu-id="1d7ab-168">*폐색* - 메시 데이터는 폐색 재질을 사용하여 장면의 항목을 *폐색합니다.*</span><span class="sxs-lookup"><span data-stu-id="1d7ab-168">*Occlusion* - Mesh data will be occlude items in scene using the *Occlusion Material*</span></span>

![공간 인식 시스템 구현 선택](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

<span data-ttu-id="1d7ab-170">공간 관찰자는 [코드를 통해 런타임에 다시 시작/일시 중단될](usage-guide.md#starting-and-stopping-mesh-observation) 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-170">Spatial Observers can be [resumed/suspended at runtime via code.](usage-guide.md#starting-and-stopping-mesh-observation)</span></span>

> [!WARNING]
> <span data-ttu-id="1d7ab-171">*표시 옵션을* *없음으로* 설정해도 관찰자의 실행이 **중지되지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-171">Setting *Display Option* to *None* does **NOT** stop the observer from running.</span></span> <span data-ttu-id="1d7ab-172">모든 관찰자를 중지하려는 경우 애플리케이션은 를 통해 모든 관찰자를 일시 중단해야 합니다. [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span><span class="sxs-lookup"><span data-stu-id="1d7ab-172">If you wish to stop all observers, applications will need to suspend all observers via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span></span>

<span data-ttu-id="1d7ab-173">**표시되는 재질**</span><span class="sxs-lookup"><span data-stu-id="1d7ab-173">**Visible Material**</span></span>

<span data-ttu-id="1d7ab-174">공간 메시를 시각화할 때 사용할 재질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-174">Indicates the material to be used when visualizing the spatial mesh.</span></span>

<span data-ttu-id="1d7ab-175">**폐색 재질**</span><span class="sxs-lookup"><span data-stu-id="1d7ab-175">**Occlusion Material**</span></span>

<span data-ttu-id="1d7ab-176">공간 메시가 홀로그램을 가리도록 하는 데 사용할 재질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1d7ab-176">Indicates the material to be used to cause the spatial mesh to occlude holograms.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d7ab-177">참조</span><span class="sxs-lookup"><span data-stu-id="1d7ab-177">See also</span></span>

* [<span data-ttu-id="1d7ab-178">공간 인식 시스템</span><span class="sxs-lookup"><span data-stu-id="1d7ab-178">Spatial Awareness System</span></span>](spatial-awareness-getting-started.md)
* [<span data-ttu-id="1d7ab-179">코드를 통해 공간 인식 시스템 구성</span><span class="sxs-lookup"><span data-stu-id="1d7ab-179">Configuring Spatial Awareness system via Code</span></span>](usage-guide.md)
* [<span data-ttu-id="1d7ab-180">IMixedRealitySpatialAwarenessObserver API 설명서</span><span class="sxs-lookup"><span data-stu-id="1d7ab-180">IMixedRealitySpatialAwarenessObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [<span data-ttu-id="1d7ab-181">IMixedRealitySpatialAwarenessMeshObserver API 설명서</span><span class="sxs-lookup"><span data-stu-id="1d7ab-181">IMixedRealitySpatialAwarenessMeshObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [<span data-ttu-id="1d7ab-182">BaseSpatialObserver API 설명서</span><span class="sxs-lookup"><span data-stu-id="1d7ab-182">BaseSpatialObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
