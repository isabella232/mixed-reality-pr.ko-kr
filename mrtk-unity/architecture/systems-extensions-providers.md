---
title: 시스템 확장 공급자
description: MRTK 확장 및 데이터 공급자
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 시스템 확장
ms.openlocfilehash: add1f443edb687edfc387a316d83443779e079f9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143506"
---
# <a name="systems-extension-services-and-data-providers"></a><span data-ttu-id="54cc0-104">시스템, 확장 서비스 및 데이터 공급자</span><span class="sxs-lookup"><span data-stu-id="54cc0-104">Systems, extension services and data providers</span></span>

<span data-ttu-id="54cc0-105">혼합 현실 도구 키트에서 많은 기능이 서비스 형태로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-105">In the Mixed Reality Toolkit, many of the features are delivered in the form of services.</span></span> <span data-ttu-id="54cc0-106">서비스는 시스템, 확장 서비스 및 데이터 공급자의 세 가지 기본 범주로 그룹화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-106">Services are grouped into three primary categories: systems, extension services and data providers.</span></span>

## <a name="systems"></a><span data-ttu-id="54cc0-107">시스템</span><span class="sxs-lookup"><span data-stu-id="54cc0-107">Systems</span></span>

<span data-ttu-id="54cc0-108">시스템은 혼합 현실 도구 키트의 핵심 기능을 제공 하는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-108">Systems are services that provide the core functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="54cc0-109">모든 시스템은 인터페이스의 구현 [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 입니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-109">All systems are implementations of the [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span></span>

- [<span data-ttu-id="54cc0-110">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="54cc0-110">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="54cc0-111">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="54cc0-111">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md)
- [<span data-ttu-id="54cc0-112">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="54cc0-112">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md)
- [<span data-ttu-id="54cc0-113">InputSystem</span><span class="sxs-lookup"><span data-stu-id="54cc0-113">InputSystem</span></span>](../features/input/overview.md)
- [<span data-ttu-id="54cc0-114">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="54cc0-114">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md)
- [<span data-ttu-id="54cc0-115">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="54cc0-115">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="54cc0-116">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="54cc0-116">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md)

<span data-ttu-id="54cc0-117">나열 된 각 시스템은 MixedRealityToolkit 구성 요소의 구성 [프로필](../features/profiles/profiles.md)에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-117">Each of the listed systems are surfaced in the MixedRealityToolkit component's configuration [profile](../features/profiles/profiles.md).</span></span>

## <a name="extensions"></a><span data-ttu-id="54cc0-118">확장</span><span class="sxs-lookup"><span data-stu-id="54cc0-118">Extensions</span></span>

<span data-ttu-id="54cc0-119">확장 서비스는 혼합 현실 도구 키트의 기능을 확장 하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-119">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="54cc0-120">모든 확장 서비스는 인터페이스를 구현 하도록 지정 해야 합니다 [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) .</span><span class="sxs-lookup"><span data-stu-id="54cc0-120">All extension services must specify that they implement the [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span></span>

<span data-ttu-id="54cc0-121">확장 서비스를 만드는 방법에 대 한 자세한 내용은 [확장 서비스](../features/extensions/extension-services.md) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54cc0-121">For information on creating extension services, please reference the [Extension services](../features/extensions/extension-services.md) article.</span></span>

<span data-ttu-id="54cc0-122">MRTK에 액세스할 수 있게 하려면 MixedRealityToolkit 구성 요소 구성 프로필의 Extensions 섹션을 사용 하 여 확장 서비스를 등록 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-122">To be accessible to the MRTK, extension services are registered and configured using the Extensions section of the MixedRealityToolkit component's configuration profile.</span></span>

![확장 서비스 구성](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a><span data-ttu-id="54cc0-124">데이터 공급자</span><span class="sxs-lookup"><span data-stu-id="54cc0-124">Data providers</span></span>

<span data-ttu-id="54cc0-125">데이터 공급자는 이름별로 Mixed Reality Toolkit 서비스에 데이터를 제공하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-125">Data providers are components that, per their name, provide data to a Mixed Reality Toolkit service.</span></span> <span data-ttu-id="54cc0-126">모든 데이터 공급자는 인터페이스를 구현한다고 지정해야 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-126">All data providers must specify that they implement the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="54cc0-127">모든 서비스에 데이터 공급자가 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-127">Not all services will require data providers.</span></span> <span data-ttu-id="54cc0-128">Mixed Reality 도구 키트 시스템 중에서 입력 및 공간 인식 시스템은 데이터 공급자를 활용하는 유일한 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-128">Of the Mixed Reality Toolkit's systems, the Input and Spatial Awareness systems are the only services to utilize data providers.</span></span>

<span data-ttu-id="54cc0-129">특정 MRTK 서비스에 액세스할 수 있도록 데이터 공급자는 서비스의 구성 프로필에 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-129">To be accessible to the specific MRTK service, data providers are registered in the service's configuration profile.</span></span>

<span data-ttu-id="54cc0-130">애플리케이션 코드는 인터페이스를 통해 데이터 공급자에 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-130">Application code accesses data providers via the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span></span> <span data-ttu-id="54cc0-131">액세스를 간소화하기 위해 도우미 클래스를 통해 데이터 공급자를 검색할 수도 `CoreServices` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-131">To simplify access, data providers can also be retrieved via the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> <span data-ttu-id="54cc0-132">`IMixedRealityDataProvider`는 에서 상속되지만 데이터 `IMixedRealityService` 공급자는 에 등록되지 `MixedRealityServiceRegistry` 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-132">Although `IMixedRealityDataProvider` inherits from `IMixedRealityService`, data providers are not registered with the `MixedRealityServiceRegistry`.</span></span> <span data-ttu-id="54cc0-133">데이터 공급자에 액세스하려면 애플리케이션 코드가 등록된 서비스 인스턴스(예: 입력 시스템)를 쿼리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-133">To access data providers, application code must query the service instance for which they were registered (ex: input system).</span></span>

### <a name="input"></a><span data-ttu-id="54cc0-134">입력</span><span class="sxs-lookup"><span data-stu-id="54cc0-134">Input</span></span>

<span data-ttu-id="54cc0-135">MRTK 입력 시스템은 를 구현하는 데이터 공급자만 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-135">The MRTK input system utilizes only data providers that implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager).</span></span>

![입력 시스템 데이터 공급자](../features/images/input/RegisteredServiceProviders.PNG)

<span data-ttu-id="54cc0-137">다음 예제에서는 입력 시뮬레이션 공급자에 액세스하고 SmoothEyeTracking 속성을 토글하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-137">The following example demonstrates accessing the input simulation provider and toggle the SmoothEyeTracking property.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess = CoreServices.InputSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IInputSimulationService inputSimulation =
        dataProviderAccess.GetDataProvider<IInputSimulationService>();

    if (inputSimulation != null)
    {
        inputSimulation.SmoothEyeTracking = !inputSimulation.SmoothEyeTracking;
    }
}
```

<span data-ttu-id="54cc0-138">핵심 입력 시스템에 대한 데이터 공급자 액세스는 도우미 클래스를 사용하여 간소화할 수도 `CoreServices` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-138">Accessing a data provider for the core input system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="54cc0-139">입력 시스템은 애플리케이션이 실행되는 플랫폼에 대해 지원되는 데이터 공급자만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-139">The input system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="54cc0-140">MRTK 입력 시스템에 대한 데이터 공급자 작성에 대한 자세한 내용은 [입력 시스템 데이터 공급자 만들기를](../features/input/create-data-provider.md)참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54cc0-140">For information on writing a data provider for the MRTK input system, please see [creating an input system data provider](../features/input/create-data-provider.md).</span></span>

### <a name="spatial-awareness"></a><span data-ttu-id="54cc0-141">공간 인식</span><span class="sxs-lookup"><span data-stu-id="54cc0-141">Spatial awareness</span></span>

<span data-ttu-id="54cc0-142">MRTK 공간 인식 시스템은 인터페이스를 구현하는 데이터 공급자만 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-142">The MRTK spatial awareness system utilizes only data providers that implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![공간 인식 시스템 데이터 공급자](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

<span data-ttu-id="54cc0-144">다음 예제에서는 등록된 공간 메시 데이터 공급자에 액세스하고 메시의 표시 유형 변경에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-144">The following example demonstrates accessing the registered spatial mesh data providers and changing the visibility of the meshes.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess =
    CoreServices.SpatialAwarenessSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IReadOnlyList<IMixedRealitySpatialAwarenessMeshObserver> observers =
        dataProviderAccess.GetDataProviders<IMixedRealitySpatialAwarenessMeshObserver>();

    foreach (IMixedRealitySpatialAwarenessMeshObserver observer in observers)
    {
        // Set the mesh to use the occlusion material
        observer.DisplayOption = SpatialMeshDisplayOptions.Occlusion;
    }
}
```

<span data-ttu-id="54cc0-145">핵심 공간 인식 시스템에 대한 데이터 공급자 액세스는 도우미 클래스를 사용하여 간소화할 수도 `CoreServices` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-145">Accessing a data provider for the core spatial awareness system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="54cc0-146">공간 인식 시스템은 애플리케이션이 실행되는 플랫폼에 대해 지원되는 데이터 공급자만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="54cc0-146">The spatial awareness system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="54cc0-147">MRTK 공간 인식 시스템에 대한 데이터 공급자 작성에 대한 자세한 내용은 [공간 인식 시스템 데이터 공급자 만들기를](../features/spatial-awareness/create-data-provider.md)참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54cc0-147">For information on writing a data provider for the MRTK spatial awareness system, please see [creating a spatial awareness system data provider](../features/spatial-awareness/create-data-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54cc0-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54cc0-148">See also</span></span>

- [<span data-ttu-id="54cc0-149">확장 서비스</span><span class="sxs-lookup"><span data-stu-id="54cc0-149">Extension services</span></span>](../features/extensions/extension-services.md)
- [<span data-ttu-id="54cc0-150">입력 시스템 데이터 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="54cc0-150">Creating an input system data provider</span></span>](../features/input/create-data-provider.md)
- [<span data-ttu-id="54cc0-151">공간 인식 시스템 데이터 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="54cc0-151">Creating a spatial awareness system system data provider</span></span>](../features/spatial-awareness/create-data-provider.md)
- [<span data-ttu-id="54cc0-152">IMixedRealityService 인터페이스</span><span class="sxs-lookup"><span data-stu-id="54cc0-152">IMixedRealityService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [<span data-ttu-id="54cc0-153">IMixedRealityDataProvider 인터페이스</span><span class="sxs-lookup"><span data-stu-id="54cc0-153">IMixedRealityDataProvider interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="54cc0-154">IMixedRealityExtensionService 인터페이스</span><span class="sxs-lookup"><span data-stu-id="54cc0-154">IMixedRealityExtensionService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
