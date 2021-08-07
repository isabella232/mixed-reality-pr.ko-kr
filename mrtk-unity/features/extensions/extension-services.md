---
title: 확장 서비스
description: MRTK의 확장된 기능에 대한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 0f9f30bb7d2d44cef828b79bc916d933a6355dbb1068b09e73317d1c977ef45a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186999"
---
# <a name="extension-services"></a>확장 서비스

확장 서비스는 Mixed Reality Toolkit 기능을 확장하는 구성 요소입니다. 이러한 서비스는 MRTK 또는 다른 당사자가 제공할 수 있습니다.

## <a name="creating-an-extension-service"></a>확장 서비스 만들기

확장 서비스를 만드는 가장 효율적인 방법은 [확장 서비스 만들기 마법사](../tools/extension-service-creation-wizard.md)를 사용하는 것입니다.
확장 서비스 만들기 마법사를 시작하려면 **Mixed Reality Toolkit > 유틸리티 > 확장 서비스 만들기를** 선택합니다.

![확장 서비스 만들기 마법사](../images/extension-wizard/ExtensionServiceCreationWizard.png)

마법사는 서비스 구성 요소 만들기를 자동화하고 적절한 인터페이스 상속을 보장합니다.

![확장 서비스 만들기 마법사에서 만든 구성 요소](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> MRTK 버전 2.0.0에서는 확장 서비스 마법사에서 서비스 검사자 및 서비스 프로필을 생성해야 하는 문제가 있습니다. 자세한 내용은 문제 [5654를](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) 참조하세요.

마법사가 완료되면 서비스 기능을 구현할 수 있습니다.

## <a name="registering-an-extension-service"></a>확장 서비스 등록

애플리케이션에서 액세스할 수 있도록 새 확장 서비스를 Mixed Reality Toolkit 등록해야 합니다.

확장 서비스 만들기 마법사를 사용하여 서비스를 등록할 수 있습니다.

![확장 서비스 만들기 마법사 등록](../images/extension-wizard/ExtensionServiceWizardRegister.png)

Mixed Reality Toolkit 구성 검사기를 사용하여 서비스를 수동으로 등록할 수도 있습니다.

![수동 확장 서비스 등록](../images/profiles/RegisterExtensionService.png)

확장 서비스에서 프로필을 사용하는 경우 검사기에서 프로필을 지정했는지 확인하세요.

![구성된 확장 서비스](../images/profiles/ConfiguredExtensionService.png)

구성 요소 이름 및 우선 순위를 조정할 수도 있습니다.

## <a name="accessing-an-extension-service"></a>확장 서비스 액세스

아래 예제와 같이 를 사용하여 코드에서 확장 서비스에 [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 액세스합니다.

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a>참고 항목

- [시스템, 확장 서비스 및 데이터 공급자](../../architecture/systems-extensions-providers.md)
- [확장 서비스 만들기 마법사](../tools/extension-service-creation-wizard.md)
- [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
