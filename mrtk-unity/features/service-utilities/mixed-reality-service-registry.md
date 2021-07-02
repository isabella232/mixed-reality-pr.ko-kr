---
title: Mixed Reality 서비스 레지스트리
description: MixedRealityServiceRegistry 및 IMixedRealityServiceRegistrar에 대한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 061e4233d61de817b1aaed7faaa6d461427d6f07
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176699"
---
# <a name="mixed-reality-service-registry"></a><span data-ttu-id="0b585-104">Mixed Reality 서비스 레지스트리</span><span class="sxs-lookup"><span data-stu-id="0b585-104">Mixed Reality service registry</span></span>

<span data-ttu-id="0b585-105">Mixed Reality Toolkit 관련 작업을 수행하는 매우 유사한 두 가지 구성 요소인 MixedRealityServiceRegistry 및 IMixedRealityServiceRegistrar가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-105">The Mixed Reality Toolkit has two very similarly named components that perform related tasks: MixedRealityServiceRegistry and IMixedRealityServiceRegistrar.</span></span>

## <a name="mixedrealityserviceregistry"></a><span data-ttu-id="0b585-106">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="0b585-106">MixedRealityServiceRegistry</span></span>

<span data-ttu-id="0b585-107">[MixedRealityServiceRegistry는](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 등록된 각 서비스(핵심 시스템 및 확장 서비스)의 인스턴스를 포함하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-107">The [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) is the component that contains instances of each registered service (core systems and extension services).</span></span>

> [!NOTE]
> <span data-ttu-id="0b585-108">MixedRealityServiceRegistry에는 [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)를 포함하여 [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 인터페이스를 구현하는 개체의 인스턴스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-108">The MixedRealityServiceRegistry contains instances of objects that implement [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface, including [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span></span>
>
><span data-ttu-id="0b585-109">[IMixedRealityDataProvider(IMixedRealityService의](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 하위 클래스)를 구현하는 개체는 MixedRealityServiceRegistry에 명시적으로 등록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-109">Objects implementing the [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (a subclass of IMixedRealityService) are explicitly not registered in the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="0b585-110">이러한 개체는 개별 서비스(예: 공간 인식)에서 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-110">These objects are managed by the individual services (ex: Spatial Awareness).</span></span>

<span data-ttu-id="0b585-111">MixedRealityServiceRegistry는 정적 C# 클래스로 구현되며 애플리케이션 코드에서 서비스 인스턴스를 획득하는 데 사용하는 권장 패턴입니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-111">The MixedRealityServiceRegistry is implemented as a static C# class and is the recommended pattern to use to acquire service instances in application code.</span></span>

<span data-ttu-id="0b585-112">다음 조각에서는 IMixedRealityInputSystem 인스턴스를 획득하는 것을 보여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-112">The following snippet demonstrates acquiring an IMixedRealityInputSystem instance.</span></span>

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a><span data-ttu-id="0b585-113">IMixedRealityServiceRegistrar</span><span class="sxs-lookup"><span data-stu-id="0b585-113">IMixedRealityServiceRegistrar</span></span>

<span data-ttu-id="0b585-114">[IMixedRealityServiceRegistrar는](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 하나 이상의 서비스 등록을 관리하는 구성 요소에서 구현하는 기능을 정의하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-114">The [IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) is the interface that defines the functionality implemented by components that manage the registration of one or more services.</span></span> <span data-ttu-id="0b585-115">IMixedRealityServiceRegistrar을 구현하는 구성 요소는 MixedRealityServiceRegistry 내에서 데이터를 추가 및 제거하는 것을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-115">Components that implement IMixedRealityServiceRegistrar are responsible for adding and removing the data within the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="0b585-116">[MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 개체는 이러한 구성 요소 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-116">The [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object is one such component.</span></span>

<span data-ttu-id="0b585-117">다른 등록 기관은 MRTK/SDK/Experimental/Features 폴더에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-117">Other registrars can be found in the MRTK/SDK/Experimental/Features folder.</span></span> <span data-ttu-id="0b585-118">이러한 구성 요소는 애플리케이션에 단일 서비스(예: 공간 인식) 지원을 추가하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-118">These components can be used to add single service (ex: Spatial Awareness) support to an application.</span></span> <span data-ttu-id="0b585-119">이러한 단일 서비스 관리자는 아래에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-119">These single service managers are listed below.</span></span>

- [<span data-ttu-id="0b585-120">BoundarySystemManager</span><span class="sxs-lookup"><span data-stu-id="0b585-120">BoundarySystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [<span data-ttu-id="0b585-121">CameraSystemManager</span><span class="sxs-lookup"><span data-stu-id="0b585-121">CameraSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [<span data-ttu-id="0b585-122">DiagnosticsSystemManager</span><span class="sxs-lookup"><span data-stu-id="0b585-122">DiagnosticsSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [<span data-ttu-id="0b585-123">InputSystemManager</span><span class="sxs-lookup"><span data-stu-id="0b585-123">InputSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [<span data-ttu-id="0b585-124">SpatialAwarenessSystemManager</span><span class="sxs-lookup"><span data-stu-id="0b585-124">SpatialAwarenessSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [<span data-ttu-id="0b585-125">TeleportSystemManager</span><span class="sxs-lookup"><span data-stu-id="0b585-125">TeleportSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

<span data-ttu-id="0b585-126">InputSystemManager를 제외하고 위의 각 구성 요소는 단일 서비스 유형의 등록 및 상태를 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-126">Each of the above components, with the exception of the InputSystemManager, are responsible for managing the registration and status of a single service type.</span></span> <span data-ttu-id="0b585-127">InputSystem에는 InputSystemManager에서도 관리되는 몇 가지 추가 지원 서비스(예: FocusProvider)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-127">The InputSystem requires some additional support services (ex: FocusProvider) that are also managed by the InputSystemManager.</span></span>

<span data-ttu-id="0b585-128">일반적으로 IMixedRealityServiceRegistrar에 의해 정의된 메서드는 서비스 관리 구성 요소에 의해 내부적으로 호출되거나 추가 서비스 구성 요소가 올바르게 작동해야 하는 서비스에 의해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b585-128">In general, the methods defined by IMixedRealityServiceRegistrar are called internally by service management components or called by services that require additional service components to function correctly.</span></span> <span data-ttu-id="0b585-129">애플리케이션 코드는 일반적으로 이러한 메서드를 호출하지 않아야 합니다. 이렇게 하면 애플리케이션이 예측 불가능하게 동작할 수 있습니다(예: 캐시된 서비스 인스턴스가 무효화될 수 있음).</span><span class="sxs-lookup"><span data-stu-id="0b585-129">Application code should, generally, not call these methods as doing so may cause the application to behave unpredictably (ex: a cached service instance may become invalid).</span></span>

## <a name="see-also"></a><span data-ttu-id="0b585-130">참조</span><span class="sxs-lookup"><span data-stu-id="0b585-130">See also</span></span>

- [<span data-ttu-id="0b585-131">IMixedRealityServiceRegistrar API 설명서</span><span class="sxs-lookup"><span data-stu-id="0b585-131">IMixedRealityServiceRegistrar API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [<span data-ttu-id="0b585-132">MixedRealityServiceRegistry API 설명서</span><span class="sxs-lookup"><span data-stu-id="0b585-132">MixedRealityServiceRegistry API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
