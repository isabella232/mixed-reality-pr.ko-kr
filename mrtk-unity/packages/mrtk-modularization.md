---
title: MRTK 모듈화
description: MRTK의 구성 요소화에 대해 설명합니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 04b2e6155e591a918b95aed20961a0450afe5f43
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144427"
---
# <a name="mixed-reality-toolkit-componentization"></a><span data-ttu-id="7b109-104">Mixed Reality 도구 키트 구성 요소화</span><span class="sxs-lookup"><span data-stu-id="7b109-104">Mixed Reality Toolkit componentization</span></span>

<span data-ttu-id="7b109-105">Mixed Reality Toolkit v2의 새로운 기능 중 하나는 향상된 구성 요소화입니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-105">One of the great new features of Mixed Reality Toolkit v2 is improved componentization.</span></span> <span data-ttu-id="7b109-106">가능하면 개별 구성 요소는 기초의 핵심 계층을 제외한 모든 계층에서 격리됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-106">Wherever possible, individual components are isolated from all but the core layer of the foundation.</span></span>

## <a name="minimized-dependencies"></a><span data-ttu-id="7b109-107">최소화된 의존성</span><span class="sxs-lookup"><span data-stu-id="7b109-107">Minimized dependencies</span></span>

<span data-ttu-id="7b109-108">MRTK v2는 의도적으로 모듈식으로 개발되었으며 시스템 서비스 간의 의존성을 최소화하기 위해 개발되었습니다(예: 공간 인식).</span><span class="sxs-lookup"><span data-stu-id="7b109-108">MRTK v2 was intentionally developed to be modular and to minimize dependencies between system services (ex: spatial awareness).</span></span>

<span data-ttu-id="7b109-109">일부 시스템 서비스(예: 입력 및 원격 보고)의 특성으로 인해 적은 수의 dependencies가 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-109">Due to the nature of some system services (ex: input and teleportation), a small number of dependencies exist.</span></span>

<span data-ttu-id="7b109-110">서비스에는 하나 이상의 데이터 공급자 구성 요소가 필요하지만 서비스 사이에는 직접 링크가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-110">While it is expected that services will need one or more data provider components, there are no direct links between them.</span></span> <span data-ttu-id="7b109-111">SDK 기능(예: 사용자 인터페이스 구성 요소)에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-111">The same is true for SDK features (ex: User Interface components).</span></span>

## <a name="component-communication"></a><span data-ttu-id="7b109-112">구성 요소 통신</span><span class="sxs-lookup"><span data-stu-id="7b109-112">Component communication</span></span>

<span data-ttu-id="7b109-113">구성 요소 간에 직접 링크가 없도록 하기 위해 MRTK v2는 인터페이스를 활용하여 서비스, 데이터 공급자 및 애플리케이션 코드 간에 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-113">To ensure that there are no direct links between components, MRTK v2 utilizes interfaces to communicate between services, data providers and application code.</span></span> <span data-ttu-id="7b109-114">이러한 인터페이스는 에 정의되며 모든 통신은 Mixed Reality Toolkit 핵심 구성 요소를 통해 라우팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-114">These interfaces are defined in and all communication is routed through the Mixed Reality Toolkit core component.</span></span>

![인터페이스를 통해 공간 인식 시스템 사용](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a><span data-ttu-id="7b109-116">MRTK 가져오기 공간 최소화</span><span class="sxs-lookup"><span data-stu-id="7b109-116">Minimizing MRTK import footprint</span></span>

<span data-ttu-id="7b109-117">현재 MRTK는 단일 기본 패키지로 가져옵니다(완전히 선택적 패키지인 예제 패키지의 존재는 잠시 무시).</span><span class="sxs-lookup"><span data-stu-id="7b109-117">At this moment, the MRTK is imported as a single foundation package (ignoring for a moment the existence of the examples package, which is a completely optional package).</span></span> <span data-ttu-id="7b109-118">가져온 파일을 수동으로 축소하여 이 공간을 줄일 수 있지만, 잘 정의된 가이드가 없는 매우 수동적인 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-118">It is possible to make this footprint smaller by manually cutting down on the files imported, though this is a highly manual process which doesn't have a well-defined guide.</span></span>

<span data-ttu-id="7b109-119">Foundation 패키지를 가져오는 동안 임의의 항목을 선택 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-119">It is possible to uncheck arbitrary items during the import of the Foundation package.</span></span> <span data-ttu-id="7b109-120">그러나 기능이 중단될 수 있기 때문에 개발 초기 단계에서는 이 작업을 수행하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-120">However, it's not recommended to do this at an early stage in development as it might break functionality.</span></span> <span data-ttu-id="7b109-121">앱의 최종 기능 집합을 파악한 후에는 다음 폴더에서 필요 없는 공급자 및 서비스를 정리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-121">After having figured out the final feature set of an app, pruning unneeded providers and services can be done on the following folders:</span></span>

- <span data-ttu-id="7b109-122">MRTK/서비스</span><span class="sxs-lookup"><span data-stu-id="7b109-122">MRTK/Services</span></span>
- <span data-ttu-id="7b109-123">MRTK/공급자</span><span class="sxs-lookup"><span data-stu-id="7b109-123">MRTK/Providers</span></span>
- <span data-ttu-id="7b109-124">MRTK/SDK/기능</span><span class="sxs-lookup"><span data-stu-id="7b109-124">MRTK/SDK/Features</span></span>

> [!NOTE]
> <span data-ttu-id="7b109-125">MRTK v2. x에는 asset/MRTK/Core 폴더의 콘텐츠가 **_필요_** 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-125">MRTK v2.x **_requires_** the contents of the Assets/MRTK/Core folder.</span></span>

## <a name="upcoming-features"></a><span data-ttu-id="7b109-126">예정된 기능</span><span class="sxs-lookup"><span data-stu-id="7b109-126">Upcoming features</span></span>

### <a name="application-architecture"></a><span data-ttu-id="7b109-127">애플리케이션 아키텍처</span><span class="sxs-lookup"><span data-stu-id="7b109-127">Application architecture</span></span>

<span data-ttu-id="7b109-128">MRTK는 다음과 같은 다양 한 아키텍처를 사용 하 여 응용 프로그램을 빌드할 수 있도록 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-128">The MRTK will have support to enable applications to be built with a variety of architectures, including:</span></span>

- [<span data-ttu-id="7b109-129">MixedRealityToolkit 서비스 로케이터</span><span class="sxs-lookup"><span data-stu-id="7b109-129">MixedRealityToolkit service locator</span></span>](#mixedrealitytoolkit-service-locator)
- [<span data-ttu-id="7b109-130">개별 서비스</span><span class="sxs-lookup"><span data-stu-id="7b109-130">Individual services</span></span>](#individual-service-components)
- [<span data-ttu-id="7b109-131">사용자 지정 서비스 로케이터</span><span class="sxs-lookup"><span data-stu-id="7b109-131">Custom service locator</span></span>](#custom-service-locator)
- [<span data-ttu-id="7b109-132">하이브리드 아키텍처</span><span class="sxs-lookup"><span data-stu-id="7b109-132">Hybrid architecture</span></span>](#hybrid-architecture)

<span data-ttu-id="7b109-133">응용 프로그램 아키텍처를 선택할 때는 디자인 유연성과 응용 프로그램 성능을 고려 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-133">When selecting an application architecture, it is important to consider design flexibility and application performance.</span></span> <span data-ttu-id="7b109-134">여기에 설명 된 아키텍처는 모든 응용 프로그램에 적합 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-134">The architectures described here are not expected to be suitable for every application.</span></span>

#### <a name="mixedrealitytoolkit-service-locator"></a><span data-ttu-id="7b109-135">MixedRealityToolkit 서비스 로케이터</span><span class="sxs-lookup"><span data-stu-id="7b109-135">MixedRealityToolkit service locator</span></span>

<span data-ttu-id="7b109-136">MRTK는 기본 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 서비스 로케이터 구성 요소를 사용 하도록 응용 프로그램 장면을 설정 하 고 자동으로 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-136">The MRTK enables (and automatically configures) application scenes to use the default [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator component.</span></span> <span data-ttu-id="7b109-137">이 구성 요소에는 구성 검사기를 통해 MRTK 시스템 및 데이터 공급자를 구성 하 고 구성 요소 lifespans 및 핵심 동작을 관리 하는 지원이 포함 됩니다 (예: 업데이트할 경우).</span><span class="sxs-lookup"><span data-stu-id="7b109-137">This component includes support for configuring MRTK systems and data providers via configuration inspectors and manages component lifespans and core behaviors (ex: when to update).</span></span>

<span data-ttu-id="7b109-138">프로젝트에서 사용 되는지 여부에 관계 없이 모든 시스템이 핵심 구성 검사자에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-138">All systems are represented in the core configuration inspector, regardless of whether or not they are present or enabled in the project.</span></span> <span data-ttu-id="7b109-139">자세한 내용은 [Mixed Reality 구성 가이드](../configuration/mixed-reality-configuration-guide.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7b109-139">Please see the [Mixed Reality Configuration Guide](../configuration/mixed-reality-configuration-guide.md) for more information.</span></span>

#### <a name="individual-service-components"></a><span data-ttu-id="7b109-140">개별 서비스 구성 요소</span><span class="sxs-lookup"><span data-stu-id="7b109-140">Individual service components</span></span>

<span data-ttu-id="7b109-141">일부 개발자는 개별 서비스 구성 요소를 응용 프로그램 장면 계층 구조에 포함 하려는 것으로 표시 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-141">Some developers have expressed a desire to include individual service components into the application scene hierarchy.</span></span> <span data-ttu-id="7b109-142">이 사용을 가능 하 게 하려면 사용자 지정 등록 기관에 서비스를 캡슐화 하거나 자체 등록/자동 관리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-142">To enable this usage, services will either need to be encapsulated in a custom registrar or be self-registering / self-managing.</span></span>

<span data-ttu-id="7b109-143">자체 등록 서비스는 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 응용 프로그램 코드가 레지스트리를 통해 서비스 인스턴스를 검색할 수 있도록를 구현 하 고 자체를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-143">A self-registering service would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) and register itself so that application code could discover the service instance via a registry.</span></span>

<span data-ttu-id="7b109-144">자동 관리 서비스는 장면 계층 구조에서 singleton 개체로 구현 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-144">A self-managing service could be implemented as a singleton object in the scene hierarchy.</span></span> <span data-ttu-id="7b109-145">이 개체는 애플리케이션 코드가 서비스 기능에 직접 액세스하는 데 사용할 수 있는 및 인스턴스 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-145">This object would provide and instance property which application code could use to directly access service functionality.</span></span>

#### <a name="custom-service-locator"></a><span data-ttu-id="7b109-146">사용자 지정 서비스 로케이터</span><span class="sxs-lookup"><span data-stu-id="7b109-146">Custom service locator</span></span>

<span data-ttu-id="7b109-147">일부 개발자는 사용자 지정 서비스 로케이터 구성 요소를 만드는 기능을 요청했습니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-147">Some developers have requested the ability to create a custom service locator component.</span></span> <span data-ttu-id="7b109-148">사용자 지정 서비스 로케이터는 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 인터페이스를 구현하고 활성 서비스의 수명 주기 및 핵심 동작을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-148">Custom service locators would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface and manage the life cycle and core behaviors of active services.</span></span>

#### <a name="hybrid-architecture"></a><span data-ttu-id="7b109-149">하이브리드 아키텍처</span><span class="sxs-lookup"><span data-stu-id="7b109-149">Hybrid architecture</span></span>

<span data-ttu-id="7b109-150">MRTK는 개발자가 필요에 따라 또는 원하는 대로 이전 접근 방식을 결합할 수 있는 하이브리드 아키텍처를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-150">The MRTK will support a hybrid architecture in which developers can combine the previous approaches as needed or desired.</span></span> <span data-ttu-id="7b109-151">예를 들어 개발자는 서비스 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 로케이터로 시작하고 자체 등록 서비스를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-151">For example, a developer could start with the [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator and add a self-registering service.</span></span>

> [!NOTE]
> <span data-ttu-id="7b109-152">하이브리드 아키텍처를 선택할 때는 작업 중복(예: 여러 구성 요소에서 컨트롤러 데이터 획득)을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b109-152">When opting for a hybrid architecture, it is important to be mindful of any duplication of work (ex: acquiring controller data from multiple components).</span></span>
