---
title: 경계 시스템 개요
description: MRTK의 경계 시스템에 대한 방문 페이지
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 경계 시스템,
ms.openlocfilehash: fd70479e5183e9a7557de5c5a532cc87161be017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177079"
---
# <a name="boundary-system-overview"></a><span data-ttu-id="05960-104">경계 시스템 개요</span><span class="sxs-lookup"><span data-stu-id="05960-104">Boundary system overview</span></span>

<span data-ttu-id="05960-105">경계 시스템은 혼합 현실 애플리케이션에서 가상 현실 경계 구성 요소를 시각화하기 위한 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="05960-105">The Boundary system provides support for visualizing Virtual Reality boundary components in mixed reality applications.</span></span> <span data-ttu-id="05960-106">경계는 VR 헤드셋을 걸 때 사용자가 안전하게 이동할 수 있는 영역을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="05960-106">Boundaries define the area in which users can safely move around while wearing a VR headset.</span></span> <span data-ttu-id="05960-107">경계는 사용자가 VR 헤드셋을 걸 때 보이지 않는 장애물을 방지하는 데 도움이 되는 혼합 현실 환경의 중요한 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="05960-107">Boundaries are an important component of a mixed reality experience to help users avoid unseen obstacles while wearing a VR headset.</span></span>

<span data-ttu-id="05960-108">많은 Virtual Reality 플랫폼은 사용자 또는 컨트롤러가 경계에 가까워지면 가상 세계에 겹쳐진 흰색 윤곽선과 같은 자동 디스플레이를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="05960-108">Many Virtual Reality platforms provide an automatic display, for example a white outline superimposed on the virtual world as the user or their controller nears the boundary.</span></span> <span data-ttu-id="05960-109">Mixed Reality Toolkit 경계 시스템은 이 기능을 확장하여 추적된 영역의 개요, 평면 및 사용자에게 추가 정보를 제공하는 데 사용할 수 있는 기타 기능을 표시할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="05960-109">The Mixed Reality Toolkit's Boundary System extends this feature to enable the display of an outline of the tracked area, a floor plane and other features that can be used to provide additional information to users.</span></span>

## <a name="getting-started"></a><span data-ttu-id="05960-110">시작</span><span class="sxs-lookup"><span data-stu-id="05960-110">Getting started</span></span>

<span data-ttu-id="05960-111">경계에 대한 지원을 추가하려면 Mixed Reality Toolkit 두 가지 주요 구성 요소인 경계 시스템과 경계로 구성된 가상 현실 플랫폼이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="05960-111">Adding support for boundaries requires two key components of the Mixed Reality Toolkit: the Boundary System and a Virtual Reality platform configured with a boundary.</span></span>

1. <span data-ttu-id="05960-112">경계 시스템 [사용](#enable-boundary-system)</span><span class="sxs-lookup"><span data-stu-id="05960-112">[Enable](#enable-boundary-system) the boundary system</span></span>
2. <span data-ttu-id="05960-113">경계 시각화 [구성](#configure-boundary-visualization)</span><span class="sxs-lookup"><span data-stu-id="05960-113">[Configure](#configure-boundary-visualization) the boundary visualization</span></span>
3. <span data-ttu-id="05960-114">구성된 경계를 사용하여 VR 플랫폼 [빌드 및 배포](#build-and-deploy)</span><span class="sxs-lookup"><span data-stu-id="05960-114">[Build and deploy](#build-and-deploy) to a VR platform with a configured boundary</span></span>

## <a name="enable-boundary-system"></a><span data-ttu-id="05960-115">경계 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="05960-115">Enable boundary system</span></span>

<span data-ttu-id="05960-116">경계 시스템은 MixedRealityToolkit 개체(또는 다른 [서비스 등록 기관](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 구성 요소)에 의해 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="05960-116">The Boundary System is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="05960-117">다음 단계에서는 MixedRealityToolkit 개체의 사용을 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="05960-117">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="05960-118">다른 서비스 등록 기관에 필요한 단계는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05960-118">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="05960-119">장면 계층 구조에서 MixedRealityToolkit 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05960-119">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="05960-121">검사기 패널을 경계 시스템 섹션으로 이동하고 사용을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05960-121">Navigate the Inspector panel to the Boundary System section and check Enable</span></span>

    ![경계 시스템 사용](../images/boundary/MRTKConfig_Boundary.png)

1. <span data-ttu-id="05960-123">경계 시스템 구현을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05960-123">Select the Boundary System implementation.</span></span> <span data-ttu-id="05960-124">MRTK에서 제공하는 기본 클래스 구현은 입니다. [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="05960-124">The default class implementation provided by the MRTK is the [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

    ![경계 시스템 구현 선택](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="05960-126">모든 경계 시스템 구현은 다음을 확장해야 합니다. [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="05960-126">All Boundary System implementation must extend the [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span></span>

## <a name="configure-boundary-visualization"></a><span data-ttu-id="05960-127">경계 시각화 구성</span><span class="sxs-lookup"><span data-stu-id="05960-127">Configure boundary visualization</span></span>

<span data-ttu-id="05960-128">[경계 시스템은 구성 프로필을 사용하여](configuring-boundary-visualization.md) 표시할 경계 구성 요소를 지정하고 모양을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="05960-128">The [Boundary System uses a configuration profile](configuring-boundary-visualization.md) to specify which boundary components are to be displayed and to configure their appearance.</span></span>

![경계 시각화 옵션](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> <span data-ttu-id="05960-130">기본 `DefaultMixedRealityBoundaryVisualizationProfile` 프로필(자산/MRTK/SDK/프로필)의 사용자는 평면, 재생 영역 및 추적된 영역을 표시하도록 미리 구성된 경계 시스템을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05960-130">Users of the default profile, `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) will have the boundary system pre-configured to display a floor plane, the play area and the tracked area.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="05960-131">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="05960-131">Build and deploy</span></span>

<span data-ttu-id="05960-132">경계 시스템이 원하는 시각화 옵션으로 구성되면 프로젝트를 대상 플랫폼에 배포하여 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05960-132">Once the boundary system is configured with the desired visualization options, the project can be built deployed to the target platform.</span></span>

> [!NOTE]
> <span data-ttu-id="05960-133">Unity 재생 모드를 사용하면 구성된 경계를 편집기 내 시각화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05960-133">Unity Play Mode enables in-editor visualization of the configured boundary.</span></span> <span data-ttu-id="05960-134">이 기능을 사용하면 빌드 및 배포 단계 없이도 신속한 개발 및 테스트를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05960-134">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="05960-135">대상 하드웨어 및 플랫폼에서 실행되는 애플리케이션의 빌드 및 배포 버전을 사용하여 최종 승인 테스트를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05960-135">Be sure to do final acceptance testing using an built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="accessing-boundary-system-via-code"></a><span data-ttu-id="05960-136">코드를 통해 경계 시스템에 액세스</span><span class="sxs-lookup"><span data-stu-id="05960-136">Accessing boundary system via code</span></span>

<span data-ttu-id="05960-137">사용하도록 설정되고 구성된 경우 CoreServices 정적 도우미 클래스를 통해 경계 시스템에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05960-137">If enabled and configured, the Boundary System can be accessed via the CoreServices static helper class.</span></span> <span data-ttu-id="05960-138">그런 다음 참조를 사용하여 경계 매개 변수를 동적으로 변경하고 시스템에서 관리하는 관련 GameObjects에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05960-138">The reference can then be used to dynamically change the Boundary parameters and access related GameObjects managed by the system.</span></span>

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a><span data-ttu-id="05960-139">참조</span><span class="sxs-lookup"><span data-stu-id="05960-139">See also</span></span>

- [<span data-ttu-id="05960-140">경계 API 설명서</span><span class="sxs-lookup"><span data-stu-id="05960-140">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="05960-141">경계 시각화 구성</span><span class="sxs-lookup"><span data-stu-id="05960-141">Configuring the Boundary Visualization</span></span>](configuring-boundary-visualization.md)
