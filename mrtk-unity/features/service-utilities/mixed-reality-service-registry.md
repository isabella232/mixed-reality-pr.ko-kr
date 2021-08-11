---
title: Mixed Reality 서비스 레지스트리
description: MixedRealityServiceRegistry 및 IMixedRealityServiceRegistrar에 대 한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 16aea46890297dab209c13b6776a0a571b1e05bf5021a5795a33dc88366ee9b1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217437"
---
# <a name="mixed-reality-service-registry"></a>Mixed Reality 서비스 레지스트리

혼합 현실 Toolkit에는 관련 작업을 수행 하는 두 개의 매우 유사한 명명 된 구성 요소 (MixedRealityServiceRegistry 및 IMixedRealityServiceRegistrar)가 있습니다.

## <a name="mixedrealityserviceregistry"></a>MixedRealityServiceRegistry

[MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 는 등록 된 각 서비스 (핵심 시스템 및 확장 서비스)의 인스턴스를 포함 하는 구성 요소입니다.

> [!NOTE]
> MixedRealityServiceRegistry에는 [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)를 포함 하 여 [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 인터페이스를 구현 하는 개체의 인스턴스가 포함 되어 있습니다.
>
>[IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (IMixedRealityService의 서브 클래스)를 구현 하는 개체는 MixedRealityServiceRegistry에 명시적으로 등록 되지 않습니다. 이러한 개체는 개별 서비스에 의해 관리 됩니다 (예: 공간 인식).

MixedRealityServiceRegistry는 정적 c # 클래스로 구현 되며 응용 프로그램 코드에서 서비스 인스턴스를 획득 하는 데 사용 하는 권장 되는 패턴입니다.

다음 코드 조각에서는 IMixedRealityInputSystem 인스턴스를 가져오는 방법을 보여 줍니다.

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a>IMixedRealityServiceRegistrar

[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 는 하나 이상의 서비스 등록을 관리 하는 구성 요소에서 구현 하는 기능을 정의 하는 인터페이스입니다. IMixedRealityServiceRegistrar를 구현 하는 구성 요소는 MixedRealityServiceRegistry 내에서 데이터를 추가 하 고 제거 하는 일을 담당 합니다. [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 개체는 이러한 구성 요소 중 하나입니다.

다른 등록 기관는 MRTK/SDK/실험적/Features 폴더에서 찾을 수 있습니다. 이러한 구성 요소를 사용 하 여 단일 서비스 (예: 공간 인식)를 응용 프로그램에 추가할 수 있습니다. 이러한 단일 서비스 관리자는 다음과 같습니다.

- [BoundarySystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [CameraSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [DiagnosticsSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [InputSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [SpatialAwarenessSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [TeleportSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

InputSystemManager를 제외 하 고 위의 각 구성 요소는 단일 서비스 유형의 등록과 상태를 관리 하는 일을 담당 합니다. InputSystem에는 InputSystemManager에서 관리 하는 몇 가지 추가 지원 서비스 (예: FocusProvider)가 필요 합니다.

일반적으로 IMixedRealityServiceRegistrar에 의해 정의 된 메서드는 서비스 관리 구성 요소에서 내부적으로 호출 되거나 추가 서비스 구성 요소가 제대로 작동 해야 하는 서비스에 의해 호출 됩니다. 일반적으로 응용 프로그램 코드는 이러한 메서드를 호출 하지 않아야 합니다. 이렇게 하면 응용 프로그램이 예기치 않게 동작 하 게 될 수 있습니다 (예: 캐시 된 서비스 인스턴스가 유효 하지 않을 수 있음).

## <a name="see-also"></a>추가 정보

- [IMixedRealityServiceRegistrar API 설명서](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [MixedRealityServiceRegistry API 설명서](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
