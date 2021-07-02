---
title: 시스템, 확장 서비스 및 데이터 공급자
description: MRTK 확장 및 데이터 공급자
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 시스템 확장
ms.openlocfilehash: 668df40cec9b9443b37f63d80fcf8a1ca2e0bcbc
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177418"
---
# <a name="systems-extension-services-and-data-providers"></a><span data-ttu-id="52193-104">시스템, 확장 서비스 및 데이터 공급자</span><span class="sxs-lookup"><span data-stu-id="52193-104">Systems, extension services, and data providers</span></span>

<span data-ttu-id="52193-105">혼합 현실 Toolkit에서 대부분의 기능은 서비스 형태로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52193-105">In the Mixed Reality Toolkit, many of the features are delivered in the form of services.</span></span> <span data-ttu-id="52193-106">서비스는 시스템, 확장 서비스 및 데이터 공급자의 세 가지 기본 범주로 그룹화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52193-106">Services are grouped into three primary categories: systems, extension services and data providers.</span></span>

## <a name="systems"></a><span data-ttu-id="52193-107">시스템</span><span class="sxs-lookup"><span data-stu-id="52193-107">Systems</span></span>

<span data-ttu-id="52193-108">시스템은 혼합 현실 Toolkit의 핵심 기능을 제공 하는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="52193-108">Systems are services that provide the core functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="52193-109">모든 시스템은 인터페이스의 구현 [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 입니다.</span><span class="sxs-lookup"><span data-stu-id="52193-109">All systems are implementations of the [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span></span>

- [<span data-ttu-id="52193-110">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="52193-110">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="52193-111">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="52193-111">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md)
- [<span data-ttu-id="52193-112">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="52193-112">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md)
- [<span data-ttu-id="52193-113">InputSystem</span><span class="sxs-lookup"><span data-stu-id="52193-113">InputSystem</span></span>](../features/input/overview.md)
- [<span data-ttu-id="52193-114">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="52193-114">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md)
- [<span data-ttu-id="52193-115">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="52193-115">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="52193-116">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="52193-116">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md)

<span data-ttu-id="52193-117">나열 된 각 시스템은 MixedRealityToolkit 구성 요소의 구성 [프로필](../features/profiles/profiles.md)에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52193-117">Each of the listed systems are surfaced in the MixedRealityToolkit component's configuration [profile](../features/profiles/profiles.md).</span></span>

## <a name="extensions"></a><span data-ttu-id="52193-118">확장</span><span class="sxs-lookup"><span data-stu-id="52193-118">Extensions</span></span>

<span data-ttu-id="52193-119">확장 서비스는 혼합 현실 Toolkit의 기능을 확장 하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="52193-119">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="52193-120">모든 확장 서비스는 인터페이스를 구현 하도록 지정 해야 합니다 [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) .</span><span class="sxs-lookup"><span data-stu-id="52193-120">All extension services must specify that they implement the [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span></span>

<span data-ttu-id="52193-121">확장 서비스를 만드는 방법에 대 한 자세한 내용은 [확장 서비스](../features/extensions/extension-services.md) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52193-121">For information on creating extension services, please reference the [Extension services](../features/extensions/extension-services.md) article.</span></span>

<span data-ttu-id="52193-122">MRTK에 액세스할 수 있게 하려면 MixedRealityToolkit 구성 요소 구성 프로필의 Extensions 섹션을 사용 하 여 확장 서비스를 등록 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="52193-122">To be accessible to the MRTK, extension services are registered and configured using the Extensions section of the MixedRealityToolkit component's configuration profile.</span></span>

![확장 서비스 구성](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a><span data-ttu-id="52193-124">데이터 공급자</span><span class="sxs-lookup"><span data-stu-id="52193-124">Data providers</span></span>

<span data-ttu-id="52193-125">데이터 공급자는 이름에 따라 혼합 현실 Toolkit 서비스에 데이터를 제공 하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="52193-125">Data providers are components that, per their name, provide data to a Mixed Reality Toolkit service.</span></span> <span data-ttu-id="52193-126">모든 데이터 공급자는 인터페이스를 구현 하도록 지정 해야 합니다 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) .</span><span class="sxs-lookup"><span data-stu-id="52193-126">All data providers must specify that they implement the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="52193-127">일부 서비스의 경우 데이터 공급자가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52193-127">Not all services will require data providers.</span></span> <span data-ttu-id="52193-128">혼합 현실 Toolkit의 시스템에서 데이터 공급자를 활용 하는 데는 입력 및 공간 인식 시스템이 유일 하 게 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="52193-128">Of the Mixed Reality Toolkit's systems, the Input and Spatial Awareness systems are the only services to utilize data providers.</span></span>

<span data-ttu-id="52193-129">특정 MRTK 서비스에 액세스할 수 있도록 데이터 공급자는 서비스의 구성 프로필에 등록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52193-129">To be accessible to the specific MRTK service, data providers are registered in the service's configuration profile.</span></span>

<span data-ttu-id="52193-130">응용 프로그램 코드는 인터페이스를 통해 데이터 공급자에 액세스 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 합니다.</span><span class="sxs-lookup"><span data-stu-id="52193-130">Application code accesses data providers via the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span></span> <span data-ttu-id="52193-131">액세스를 간소화 하기 위해 도우미 클래스를 통해 데이터 공급자를 검색할 수도 있습니다 `CoreServices` .</span><span class="sxs-lookup"><span data-stu-id="52193-131">To simplify access, data providers can also be retrieved via the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> <span data-ttu-id="52193-132">`IMixedRealityDataProvider`는에서 상속 하지만 `IMixedRealityService` 데이터 공급자는에 등록 되지 않습니다 `MixedRealityServiceRegistry` .</span><span class="sxs-lookup"><span data-stu-id="52193-132">Although `IMixedRealityDataProvider` inherits from `IMixedRealityService`, data providers are not registered with the `MixedRealityServiceRegistry`.</span></span> <span data-ttu-id="52193-133">데이터 공급자에 액세스 하려면 응용 프로그램 코드가 등록 된 서비스 인스턴스 (예: 입력 시스템)를 쿼리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52193-133">To access data providers, application code must query the service instance for which they were registered (ex: input system).</span></span>

### <a name="input"></a><span data-ttu-id="52193-134">입력</span><span class="sxs-lookup"><span data-stu-id="52193-134">Input</span></span>

<span data-ttu-id="52193-135">MRTK 입력 시스템은을 구현 하는 데이터 공급자만 활용 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 합니다.</span><span class="sxs-lookup"><span data-stu-id="52193-135">The MRTK input system utilizes only data providers that implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager).</span></span>

![입력 시스템 데이터 공급자](../features/images/input/RegisteredServiceProviders.PNG)

<span data-ttu-id="52193-137">다음 예제에서는 입력 시뮬레이션 공급자에 액세스 하 고 SmoothEyeTracking 속성을 설정/해제 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52193-137">The following example demonstrates accessing the input simulation provider and toggle the SmoothEyeTracking property.</span></span>

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

<span data-ttu-id="52193-138">도우미 클래스를 사용 하 여 핵심 입력 시스템용 데이터 공급자에 액세스할 수도 있습니다 `CoreServices` .</span><span class="sxs-lookup"><span data-stu-id="52193-138">Accessing a data provider for the core input system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="52193-139">입력 시스템은 응용 프로그램이 실행 되는 플랫폼에 대해 지원 되는 데이터 공급자만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="52193-139">The input system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="52193-140">MRTK 입력 시스템용 데이터 공급자를 작성 하는 방법에 대 한 자세한 내용은 [입력 시스템 데이터 공급자 만들기](../features/input/create-data-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52193-140">For information on writing a data provider for the MRTK input system, please see [creating an input system data provider](../features/input/create-data-provider.md).</span></span>

### <a name="spatial-awareness"></a><span data-ttu-id="52193-141">공간 인식</span><span class="sxs-lookup"><span data-stu-id="52193-141">Spatial awareness</span></span>

<span data-ttu-id="52193-142">MRTK 공간 인식 시스템은 인터페이스를 구현 하는 데이터 공급자만 활용 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 합니다.</span><span class="sxs-lookup"><span data-stu-id="52193-142">The MRTK spatial awareness system utilizes only data providers that implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![공간 인식 시스템 데이터 공급자](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

<span data-ttu-id="52193-144">다음 예제에서는 등록 된 공간 메시 데이터 공급자에 액세스 하 고 메시의 표시 유형을 변경 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52193-144">The following example demonstrates accessing the registered spatial mesh data providers and changing the visibility of the meshes.</span></span>

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

<span data-ttu-id="52193-145">도우미 클래스를 사용 하 여 핵심 공간 인식 시스템용 데이터 공급자에 액세스할 수도 있습니다 `CoreServices` .</span><span class="sxs-lookup"><span data-stu-id="52193-145">Accessing a data provider for the core spatial awareness system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="52193-146">공간 인식 시스템은 응용 프로그램이 실행 되는 플랫폼에 대해 지원 되는 데이터 공급자만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="52193-146">The spatial awareness system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="52193-147">MRTK 공간 인식 시스템용 데이터 공급자를 작성 하는 방법에 대 한 자세한 내용은 [공간 인식 시스템 데이터 공급자 만들기](../features/spatial-awareness/create-data-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52193-147">For information on writing a data provider for the MRTK spatial awareness system, please see [creating a spatial awareness system data provider](../features/spatial-awareness/create-data-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="52193-148">참조</span><span class="sxs-lookup"><span data-stu-id="52193-148">See also</span></span>

- [<span data-ttu-id="52193-149">확장 서비스</span><span class="sxs-lookup"><span data-stu-id="52193-149">Extension services</span></span>](../features/extensions/extension-services.md)
- [<span data-ttu-id="52193-150">입력 시스템 데이터 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="52193-150">Creating an input system data provider</span></span>](../features/input/create-data-provider.md)
- [<span data-ttu-id="52193-151">공간 인식 시스템 시스템 데이터 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="52193-151">Creating a spatial awareness system system data provider</span></span>](../features/spatial-awareness/create-data-provider.md)
- [<span data-ttu-id="52193-152">IMixedRealityService 인터페이스</span><span class="sxs-lookup"><span data-stu-id="52193-152">IMixedRealityService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [<span data-ttu-id="52193-153">IMixedRealityDataProvider 인터페이스</span><span class="sxs-lookup"><span data-stu-id="52193-153">IMixedRealityDataProvider interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="52193-154">IMixedRealityExtensionService 인터페이스</span><span class="sxs-lookup"><span data-stu-id="52193-154">IMixedRealityExtensionService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
