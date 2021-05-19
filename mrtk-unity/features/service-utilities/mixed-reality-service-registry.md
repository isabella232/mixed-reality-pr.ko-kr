---
title: Mixed Reality 서비스 레지스트리 및 IMixedRealityServiceRegistrar
description: MixedRealityServiceRegistry 및 IMixedRealityServiceRegistrar에 대한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 09b20537824af42d241b6c33496cedcb4f530bc7
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145235"
---
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a><span data-ttu-id="1effe-104">MixedRealityServiceRegistry 및 IMixedRealityServiceRegistrar란?</span><span class="sxs-lookup"><span data-stu-id="1effe-104">What are the MixedRealityServiceRegistry and IMixedRealityServiceRegistrar?</span></span>

<span data-ttu-id="1effe-105">Mixed Reality Toolkit에는 관련 작업을 수행하는 매우 유사한 두 가지 구성 요소인 MixedRealityServiceRegistry 및 IMixedRealityServiceRegistrar가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-105">The Mixed Reality Toolkit has two very similarly named components that perform related tasks: MixedRealityServiceRegistry and IMixedRealityServiceRegistrar.</span></span>

## <a name="mixedrealityserviceregistry"></a><span data-ttu-id="1effe-106">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="1effe-106">MixedRealityServiceRegistry</span></span>

<span data-ttu-id="1effe-107">[MixedRealityServiceRegistry는](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 등록된 각 서비스(핵심 시스템 및 확장 서비스)의 인스턴스를 포함하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-107">The [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) is the component that contains instances of each registered service (core systems and extension services).</span></span>

> [!NOTE]
> <span data-ttu-id="1effe-108">MixedRealityServiceRegistry에는 [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)를 포함하여 [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 인터페이스를 구현하는 개체의 인스턴스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-108">The MixedRealityServiceRegistry contains instances of objects that implement [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface, including [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span></span>
>
><span data-ttu-id="1effe-109">[IMixedRealityDataProvider(IMixedRealityService의](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 하위 클래스)를 구현하는 개체는 MixedRealityServiceRegistry에 명시적으로 등록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-109">Objects implementing the [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (a subclass of IMixedRealityService) are explicitly not registered in the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="1effe-110">이러한 개체는 개별 서비스(예: 공간 인식)에서 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-110">These objects are managed by the individual services (ex: Spatial Awareness).</span></span>

<span data-ttu-id="1effe-111">MixedRealityServiceRegistry는 정적 C# 클래스로 구현되며 애플리케이션 코드에서 서비스 인스턴스를 획득하는 데 사용하는 권장 패턴입니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-111">The MixedRealityServiceRegistry is implemented as a static C# class and is the recommended pattern to use to acquire service instances in application code.</span></span>

<span data-ttu-id="1effe-112">다음 조각에서는 IMixedRealityInputSystem 인스턴스를 획득하는 것을 보여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-112">The following snippet demonstrates acquiring an IMixedRealityInputSystem instance.</span></span>

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a><span data-ttu-id="1effe-113">IMixedRealityServiceRegistrar</span><span class="sxs-lookup"><span data-stu-id="1effe-113">IMixedRealityServiceRegistrar</span></span>

<span data-ttu-id="1effe-114">[IMixedRealityServiceRegistrar는](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 하나 이상의 서비스 등록을 관리하는 구성 요소에서 구현하는 기능을 정의하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-114">The [IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) is the interface that defines the functionality implemented by components that manage the registration of one or more services.</span></span> <span data-ttu-id="1effe-115">IMixedRealityServiceRegistrar을 구현하는 구성 요소는 MixedRealityServiceRegistry 내에서 데이터를 추가 및 제거하는 것을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-115">Components that implement IMixedRealityServiceRegistrar are responsible for adding and removing the data within the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="1effe-116">[MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 개체는 이러한 구성 요소 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-116">The [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object is one such component.</span></span>

<span data-ttu-id="1effe-117">다른 등록 기관은 MRTK/SDK/Experimental/Features 폴더에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-117">Other registrars can be found in the MRTK/SDK/Experimental/Features folder.</span></span> <span data-ttu-id="1effe-118">이러한 구성 요소는 애플리케이션에 단일 서비스(예: 공간 인식) 지원을 추가하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-118">These components can be used to add single service (ex: Spatial Awareness) support to an application.</span></span> <span data-ttu-id="1effe-119">이러한 단일 서비스 관리자는 아래에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-119">These single service managers are listed below.</span></span>

- [<span data-ttu-id="1effe-120">BoundarySystemManager</span><span class="sxs-lookup"><span data-stu-id="1effe-120">BoundarySystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [<span data-ttu-id="1effe-121">CameraSystemManager</span><span class="sxs-lookup"><span data-stu-id="1effe-121">CameraSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [<span data-ttu-id="1effe-122">DiagnosticsSystemManager</span><span class="sxs-lookup"><span data-stu-id="1effe-122">DiagnosticsSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [<span data-ttu-id="1effe-123">InputSystemManager</span><span class="sxs-lookup"><span data-stu-id="1effe-123">InputSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [<span data-ttu-id="1effe-124">SpatialAwarenessSystemManager</span><span class="sxs-lookup"><span data-stu-id="1effe-124">SpatialAwarenessSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [<span data-ttu-id="1effe-125">TeleportSystemManager</span><span class="sxs-lookup"><span data-stu-id="1effe-125">TeleportSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

<span data-ttu-id="1effe-126">InputSystemManager를 제외한 위의 각 구성 요소는 단일 서비스 유형의 등록 및 상태를 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-126">Each of the above components, with the exception of the InputSystemManager, are responsible for managing the registration and status of a single service type.</span></span> <span data-ttu-id="1effe-127">InputSystem에는 InputSystemManager에서도 관리되는 몇 가지 추가 지원 서비스(예: FocusProvider)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-127">The InputSystem requires some additional support services (ex: FocusProvider) that are also managed by the InputSystemManager.</span></span>

<span data-ttu-id="1effe-128">일반적으로 IMixedRealityServiceRegistrar에 의해 정의된 메서드는 서비스 관리 구성 요소에 의해 내부적으로 호출되거나 추가 서비스 구성 요소가 올바르게 작동해야 하는 서비스에 의해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="1effe-128">In general, the methods defined by IMixedRealityServiceRegistrar are called internally by service management components or called by services that require additional service components to function correctly.</span></span> <span data-ttu-id="1effe-129">애플리케이션 코드는 일반적으로 이러한 메서드를 호출하지 않아야 합니다. 이렇게 하면 애플리케이션이 예기치 않게 동작할 수 있습니다(예: 캐시된 서비스 인스턴스가 잘못될 수 있음).</span><span class="sxs-lookup"><span data-stu-id="1effe-129">Application code should, generally, not call these methods as doing so may cause the application to behave unpredictably (ex: a cached service instance may become invalid).</span></span>

## <a name="see-also"></a><span data-ttu-id="1effe-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1effe-130">See also</span></span>

- [<span data-ttu-id="1effe-131">IMixedRealityServiceRegistrar API 설명서</span><span class="sxs-lookup"><span data-stu-id="1effe-131">IMixedRealityServiceRegistrar API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [<span data-ttu-id="1effe-132">MixedRealityServiceRegistry API 설명서</span><span class="sxs-lookup"><span data-stu-id="1effe-132">MixedRealityServiceRegistry API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
