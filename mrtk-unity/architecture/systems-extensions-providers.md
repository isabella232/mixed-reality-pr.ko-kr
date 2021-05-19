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
# <a name="systems-extension-services-and-data-providers"></a>시스템, 확장 서비스 및 데이터 공급자

혼합 현실 도구 키트에서 많은 기능이 서비스 형태로 제공 됩니다. 서비스는 시스템, 확장 서비스 및 데이터 공급자의 세 가지 기본 범주로 그룹화 됩니다.

## <a name="systems"></a>시스템

시스템은 혼합 현실 도구 키트의 핵심 기능을 제공 하는 서비스입니다. 모든 시스템은 인터페이스의 구현 [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 입니다.

- [BoundarySystem](../features/boundary/boundary-system-getting-started.md)
- [CameraSystem](../features/camera-system/camera-system-overview.md)
- [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md)
- [InputSystem](../features/input/overview.md)
- [SceneSystem](../features/scene-system/scene-system-getting-started.md)
- [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [TeleportSystem](../features/teleport-system/teleport-system.md)

나열 된 각 시스템은 MixedRealityToolkit 구성 요소의 구성 [프로필](../features/profiles/profiles.md)에 표시 됩니다.

## <a name="extensions"></a>확장

확장 서비스는 혼합 현실 도구 키트의 기능을 확장 하는 구성 요소입니다. 모든 확장 서비스는 인터페이스를 구현 하도록 지정 해야 합니다 [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) .

확장 서비스를 만드는 방법에 대 한 자세한 내용은 [확장 서비스](../features/extensions/extension-services.md) 문서를 참조 하세요.

MRTK에 액세스할 수 있게 하려면 MixedRealityToolkit 구성 요소 구성 프로필의 Extensions 섹션을 사용 하 여 확장 서비스를 등록 하 고 구성 합니다.

![확장 서비스 구성](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a>데이터 공급자

데이터 공급자는 이름별로 Mixed Reality Toolkit 서비스에 데이터를 제공하는 구성 요소입니다. 모든 데이터 공급자는 인터페이스를 구현한다고 지정해야 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 합니다.

> [!NOTE]
> 모든 서비스에 데이터 공급자가 필요한 것은 아닙니다. Mixed Reality 도구 키트 시스템 중에서 입력 및 공간 인식 시스템은 데이터 공급자를 활용하는 유일한 서비스입니다.

특정 MRTK 서비스에 액세스할 수 있도록 데이터 공급자는 서비스의 구성 프로필에 등록됩니다.

애플리케이션 코드는 인터페이스를 통해 데이터 공급자에 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 액세스합니다. 액세스를 간소화하기 위해 도우미 클래스를 통해 데이터 공급자를 검색할 수도 `CoreServices` 있습니다.

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> `IMixedRealityDataProvider`는 에서 상속되지만 데이터 `IMixedRealityService` 공급자는 에 등록되지 `MixedRealityServiceRegistry` 않습니다. 데이터 공급자에 액세스하려면 애플리케이션 코드가 등록된 서비스 인스턴스(예: 입력 시스템)를 쿼리해야 합니다.

### <a name="input"></a>입력

MRTK 입력 시스템은 를 구현하는 데이터 공급자만 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 활용합니다.

![입력 시스템 데이터 공급자](../features/images/input/RegisteredServiceProviders.PNG)

다음 예제에서는 입력 시뮬레이션 공급자에 액세스하고 SmoothEyeTracking 속성을 토글하는 방법을 보여 줍니다.

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

핵심 입력 시스템에 대한 데이터 공급자 액세스는 도우미 클래스를 사용하여 간소화할 수도 `CoreServices` 있습니다.

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> 입력 시스템은 애플리케이션이 실행되는 플랫폼에 대해 지원되는 데이터 공급자만 반환합니다.

MRTK 입력 시스템에 대한 데이터 공급자 작성에 대한 자세한 내용은 [입력 시스템 데이터 공급자 만들기를](../features/input/create-data-provider.md)참조하세요.

### <a name="spatial-awareness"></a>공간 인식

MRTK 공간 인식 시스템은 인터페이스를 구현하는 데이터 공급자만 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 활용합니다.

![공간 인식 시스템 데이터 공급자](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

다음 예제에서는 등록된 공간 메시 데이터 공급자에 액세스하고 메시의 표시 유형 변경에 대해 설명합니다.

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

핵심 공간 인식 시스템에 대한 데이터 공급자 액세스는 도우미 클래스를 사용하여 간소화할 수도 `CoreServices` 있습니다.

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> 공간 인식 시스템은 애플리케이션이 실행되는 플랫폼에 대해 지원되는 데이터 공급자만 반환합니다.

MRTK 공간 인식 시스템에 대한 데이터 공급자 작성에 대한 자세한 내용은 [공간 인식 시스템 데이터 공급자 만들기를](../features/spatial-awareness/create-data-provider.md)참조하세요.

## <a name="see-also"></a>참고 항목

- [확장 서비스](../features/extensions/extension-services.md)
- [입력 시스템 데이터 공급자 만들기](../features/input/create-data-provider.md)
- [공간 인식 시스템 데이터 공급자 만들기](../features/spatial-awareness/create-data-provider.md)
- [IMixedRealityService 인터페이스](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [IMixedRealityDataProvider 인터페이스](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [IMixedRealityExtensionService 인터페이스](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
