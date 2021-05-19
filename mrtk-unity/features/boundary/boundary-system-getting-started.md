---
title: 경계 시스템 시작
description: MRTK의 경계 시스템에 대한 방문 페이지
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 경계 시스템,
ms.openlocfilehash: 2858b770fb49a44d1e2d704e8d3a81affe74d272
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144736"
---
# <a name="boundary-system"></a><span data-ttu-id="2daad-104">경계 시스템</span><span class="sxs-lookup"><span data-stu-id="2daad-104">Boundary system</span></span>

<span data-ttu-id="2daad-105">경계 시스템은 혼합 현실 애플리케이션에서 가상 현실 경계 구성 요소를 시각화하기 위한 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-105">The Boundary system provides support for visualizing Virtual Reality boundary components in mixed reality applications.</span></span> <span data-ttu-id="2daad-106">경계는 VR 헤드셋을 걸 때 사용자가 안전하게 이동할 수 있는 영역을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-106">Boundaries define the area in which users can safely move around while wearing a VR headset.</span></span> <span data-ttu-id="2daad-107">경계는 사용자가 VR 헤드셋을 걸 때 보이지 않는 장애물을 방지하는 데 도움이 되는 혼합 현실 환경의 중요한 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-107">Boundaries are an important component of a mixed reality experience to help users avoid unseen obstacles while wearing a VR headset.</span></span>

<span data-ttu-id="2daad-108">많은 Virtual Reality 플랫폼은 사용자 또는 컨트롤러가 경계에 가까워지면 가상 세계에 겹쳐진 흰색 윤곽선과 같은 자동 디스플레이를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-108">Many Virtual Reality platforms provide an automatic display, for example a white outline superimposed on the virtual world as the user or their controller nears the boundary.</span></span> <span data-ttu-id="2daad-109">Mixed Reality 도구 키트의 경계 시스템은 이 기능을 확장하여 추적된 영역의 개요, 평면 및 사용자에게 추가 정보를 제공하는 데 사용할 수 있는 기타 기능을 표시할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-109">The Mixed Reality Toolkit's Boundary System extends this feature to enable the display of an outline of the tracked area, a floor plane and other features that can be used to provide additional information to users.</span></span>

## <a name="getting-started"></a><span data-ttu-id="2daad-110">시작</span><span class="sxs-lookup"><span data-stu-id="2daad-110">Getting started</span></span>

<span data-ttu-id="2daad-111">경계 지원을 추가하려면 Mixed Reality Toolkit의 두 가지 주요 구성 요소인 경계 시스템과 경계로 구성된 가상 현실 플랫폼이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-111">Adding support for boundaries requires two key components of the Mixed Reality Toolkit: the Boundary System and a Virtual Reality platform configured with a boundary.</span></span>

1. <span data-ttu-id="2daad-112">경계 시스템 [사용](#enable-boundary-system)</span><span class="sxs-lookup"><span data-stu-id="2daad-112">[Enable](#enable-boundary-system) the boundary system</span></span>
2. <span data-ttu-id="2daad-113">경계 시각화 [구성](#configure-boundary-visualization)</span><span class="sxs-lookup"><span data-stu-id="2daad-113">[Configure](#configure-boundary-visualization) the boundary visualization</span></span>
3. <span data-ttu-id="2daad-114">구성된 경계를 사용하여 VR 플랫폼 [빌드 및 배포](#build-and-deploy)</span><span class="sxs-lookup"><span data-stu-id="2daad-114">[Build and deploy](#build-and-deploy) to a VR platform with a configured boundary</span></span>

## <a name="enable-boundary-system"></a><span data-ttu-id="2daad-115">경계 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="2daad-115">Enable boundary system</span></span>

<span data-ttu-id="2daad-116">경계 시스템은 MixedRealityToolkit 개체(또는 다른 [서비스 등록 기관](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 구성 요소)에 의해 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-116">The Boundary System is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="2daad-117">다음 단계에서는 MixedRealityToolkit 개체의 사용을 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-117">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="2daad-118">다른 서비스 등록 기관에 필요한 단계는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-118">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="2daad-119">장면 계층 구조에서 MixedRealityToolkit 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-119">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="2daad-121">검사기 패널을 경계 시스템 섹션으로 이동하고 사용을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-121">Navigate the Inspector panel to the Boundary System section and check Enable</span></span>

    ![경계 시스템 사용](../images/boundary/MRTKConfig_Boundary.png)

1. <span data-ttu-id="2daad-123">경계 시스템 구현을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-123">Select the Boundary System implementation.</span></span> <span data-ttu-id="2daad-124">MRTK에서 제공 하는 기본 클래스 구현은 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="2daad-124">The default class implementation provided by the MRTK is the [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

    ![경계 시스템 구현 선택](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="2daad-126">모든 경계 시스템 구현에서는 [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="2daad-126">All Boundary System implementation must extend the [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span></span>

## <a name="configure-boundary-visualization"></a><span data-ttu-id="2daad-127">경계 시각화 구성</span><span class="sxs-lookup"><span data-stu-id="2daad-127">Configure boundary visualization</span></span>

<span data-ttu-id="2daad-128">[경계 시스템은 구성 프로필을 사용](configuring-boundary-visualization.md) 하 여 표시할 경계 구성 요소를 지정 하 고 모양을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-128">The [Boundary System uses a configuration profile](configuring-boundary-visualization.md) to specify which boundary components are to be displayed and to configure their appearance.</span></span>

![경계 시각화 옵션](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> <span data-ttu-id="2daad-130">기본 프로필의 사용자 `DefaultMixedRealityBoundaryVisualizationProfile` (자산/m a s k/SDK/프로필)에는 바닥 평면, 재생 영역 및 추적 된 영역을 표시 하도록 경계 시스템이 미리 구성 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-130">Users of the default profile, `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) will have the boundary system pre-configured to display a floor plane, the play area and the tracked area.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="2daad-131">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="2daad-131">Build and deploy</span></span>

<span data-ttu-id="2daad-132">경계 시스템이 원하는 시각화 옵션을 사용 하 여 구성 되 면 프로젝트를 대상 플랫폼에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-132">Once the boundary system is configured with the desired visualization options, the project can be built deployed to the target platform.</span></span>

> [!NOTE]
> <span data-ttu-id="2daad-133">Unity 재생 모드에서는 구성 된 경계의 편집기에서 시각화를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-133">Unity Play Mode enables in-editor visualization of the configured boundary.</span></span> <span data-ttu-id="2daad-134">이 기능을 사용 하면 빌드 및 배포 단계를 요구 하지 않고 신속 하 게 개발 하 고 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-134">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="2daad-135">대상 하드웨어 및 플랫폼에서 실행 되는 응용 프로그램의 빌드 및 배포 버전을 사용 하 여 최종 승인 테스트를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-135">Be sure to do final acceptance testing using an built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="accessing-boundary-system-via-code"></a><span data-ttu-id="2daad-136">코드를 통해 경계 시스템 액세스</span><span class="sxs-lookup"><span data-stu-id="2daad-136">Accessing boundary system via code</span></span>

<span data-ttu-id="2daad-137">사용 하도록 설정 되 고 구성 된 경우 CoreServices 정적 도우미 클래스를 통해 경계 시스템에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-137">If enabled and configured, the Boundary System can be accessed via the CoreServices static helper class.</span></span> <span data-ttu-id="2daad-138">그런 다음 참조를 사용 하 여 경계 매개 변수를 동적으로 변경 하 고 시스템에서 관리 하는 관련 Gameobject에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2daad-138">The reference can then be used to dynamically change the Boundary parameters and access related GameObjects managed by the system.</span></span>

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a><span data-ttu-id="2daad-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2daad-139">See also</span></span>

- [<span data-ttu-id="2daad-140">경계 API 설명서</span><span class="sxs-lookup"><span data-stu-id="2daad-140">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="2daad-141">경계 시각화 구성</span><span class="sxs-lookup"><span data-stu-id="2daad-141">Configuring the Boundary Visualization</span></span>](configuring-boundary-visualization.md)
