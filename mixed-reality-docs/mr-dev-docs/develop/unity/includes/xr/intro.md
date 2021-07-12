---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603719"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Mixed Reality OpenXR 플러그 인은 **Unity 2020 LTS** 이상에 대한 **Microsoft의 권장 사항입니다.** 향후 새로운 기능이 개발되면 향후 Mixed Reality OpenXR 플러그 인에만 포함됩니다.

Mixed Reality OpenXR 플러그 인은 ARPlaneManager 및 ARRaycastManager 구현을 제공하여 AR Foundation 4.0을 완벽하게 지원합니다. 이렇게 하면 HoloLens 2 및 ARCore/ARKit 휴대폰 및 태블릿에 걸쳐 있는 광선 캐스팅 코드를 작성할 수 있습니다.

### <a name="prerequisites"></a>필수 구성 요소 

* [HoloLens 2 개발을 위한](../../../install-the-tools.md?tabs=unity#installation-checklist) 최신 도구
* 최신 Unity 2020.3 LTS: 버전 2020.3.8f1 이상

### <a name="recommended-package-versions"></a>권장 패키지 버전

이 페이지의 지침에서는 HoloLens 2 또는 Windows Mixed Reality 앱을 배포하는 데 필요한 핵심 Unity OpenXR 패키지를 설정합니다.

* Unity OpenXR 플러그 인: 버전 1.2 이상
* Mixed Reality OpenXR 플러그 인: 버전 1.0.0 이상

프로젝트에서 다음 패키지를 사용하는 경우 아래에 나열된 최소 버전 이상을 사용해야 합니다.

* MRTK: 버전 2.7.2 이상
* AR Foundation: 버전 4.1.1 이상
* URP(유니버설 렌더링 파이프라인): 버전 10.5.1 이상
* Azure Spatial Anchors: 버전 2.10 이상
* Azure Remote Rendering: 버전 1.0.15 이상

> [!NOTE]
> Windows PC에서 VR 애플리케이션을 빌드하는 경우 Mixed Reality OpenXR 플러그 인이 꼭 필요한 것은 아닙니다. 그러나 HP Reverb G2 컨트롤러에 대한 입력 바인딩을 설정하거나 HoloLens 2 헤드셋과 VR 헤드셋 모두에서 작동하는 앱을 빌드하는 경우 플러그 인을 설치해야 합니다.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

Unity 2020의 새 프로젝트에는 Windows XR 플러그 인을 사용하지 않는 것이 좋습니다.  대신 Mixed Reality OpenXR 플러그 인을 사용해야 합니다.

그러나 Unity 2019를 사용하고 있고 ARCore/ARKit 디바이스와의 호환성을 위해 AR Foundation 2.0이 필요한 경우 이 플러그 인을 통해 해당 지원을 사용할 수 있습니다.

> [!IMPORTANT]
> Unity 2019에서 이 플러그 인을 사용하는 것은 Azure Spatial Anchors 호환되지 않습니다.

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

**Unity 2019** 이하를 사용 중인 경우 레거시 기본 **제공 XR 지원을** 사용하는 것이 좋습니다.

Windows XR 플러그 인은 Unity 2019에서 작동하지만 이 플러그 인은 Unity 2019의 Azure Spatial Anchors 호환되지 않으므로 권장되지 않습니다.

새 프로젝트를 시작하는 경우 [대신 Unity 2020을 설치하고](../../choosing-unity-version.md) Mixed Reality OpenXR 플러그 인을 사용하는 것이 좋습니다.