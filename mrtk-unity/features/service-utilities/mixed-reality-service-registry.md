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
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a>MixedRealityServiceRegistry 및 IMixedRealityServiceRegistrar란?

Mixed Reality Toolkit에는 관련 작업을 수행하는 매우 유사한 두 가지 구성 요소인 MixedRealityServiceRegistry 및 IMixedRealityServiceRegistrar가 있습니다.

## <a name="mixedrealityserviceregistry"></a>MixedRealityServiceRegistry

[MixedRealityServiceRegistry는](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 등록된 각 서비스(핵심 시스템 및 확장 서비스)의 인스턴스를 포함하는 구성 요소입니다.

> [!NOTE]
> MixedRealityServiceRegistry에는 [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)를 포함하여 [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 인터페이스를 구현하는 개체의 인스턴스가 포함되어 있습니다.
>
>[IMixedRealityDataProvider(IMixedRealityService의](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 하위 클래스)를 구현하는 개체는 MixedRealityServiceRegistry에 명시적으로 등록되지 않습니다. 이러한 개체는 개별 서비스(예: 공간 인식)에서 관리됩니다.

MixedRealityServiceRegistry는 정적 C# 클래스로 구현되며 애플리케이션 코드에서 서비스 인스턴스를 획득하는 데 사용하는 권장 패턴입니다.

다음 조각에서는 IMixedRealityInputSystem 인스턴스를 획득하는 것을 보여 있습니다.

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a>IMixedRealityServiceRegistrar

[IMixedRealityServiceRegistrar는](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 하나 이상의 서비스 등록을 관리하는 구성 요소에서 구현하는 기능을 정의하는 인터페이스입니다. IMixedRealityServiceRegistrar을 구현하는 구성 요소는 MixedRealityServiceRegistry 내에서 데이터를 추가 및 제거하는 것을 담당합니다. [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 개체는 이러한 구성 요소 중 하나입니다.

다른 등록 기관은 MRTK/SDK/Experimental/Features 폴더에서 찾을 수 있습니다. 이러한 구성 요소는 애플리케이션에 단일 서비스(예: 공간 인식) 지원을 추가하는 데 사용할 수 있습니다. 이러한 단일 서비스 관리자는 아래에 나열되어 있습니다.

- [BoundarySystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [CameraSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [DiagnosticsSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [InputSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [SpatialAwarenessSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [TeleportSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

InputSystemManager를 제외한 위의 각 구성 요소는 단일 서비스 유형의 등록 및 상태를 관리해야 합니다. InputSystem에는 InputSystemManager에서도 관리되는 몇 가지 추가 지원 서비스(예: FocusProvider)가 필요합니다.

일반적으로 IMixedRealityServiceRegistrar에 의해 정의된 메서드는 서비스 관리 구성 요소에 의해 내부적으로 호출되거나 추가 서비스 구성 요소가 올바르게 작동해야 하는 서비스에 의해 호출됩니다. 애플리케이션 코드는 일반적으로 이러한 메서드를 호출하지 않아야 합니다. 이렇게 하면 애플리케이션이 예기치 않게 동작할 수 있습니다(예: 캐시된 서비스 인스턴스가 잘못될 수 있음).

## <a name="see-also"></a>참고 항목

- [IMixedRealityServiceRegistrar API 설명서](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [MixedRealityServiceRegistry API 설명서](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
