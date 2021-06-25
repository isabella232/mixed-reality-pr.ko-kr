---
ms.openlocfilehash: d39f6032eaf9a59ca52a6e7ae9b8e4d227175738
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906947"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Mixed Reality OpenXR 플러그 인은 Unity 2020 LTS 이상에 대 한 **Microsoft의 권장 사항** 입니다. 향후에 새로운 기능이 개발 되 면 앞으로는 Mixed Reality OpenXR 플러그 인에만 포함 됩니다.

Mixed Reality OpenXR 플러그 인은 Ar설계도 Emanager 및 ARRaycastManager 구현을 제공 하 여 AR 기반 4.0을 완벽 하 게 지원 합니다. 이를 통해 HoloLens 2와 ARCore/Arcore 휴대폰 및 태블릿에 걸쳐 있는 raycasting 코드를 작성할 수 있습니다.

### <a name="prerequisites"></a>필수 구성 요소 

* [HoloLens 2 개발을 위한 최신 도구](../../../install-the-tools.md?tabs=unity#installation-checklist)
* 최신 Unity 2020.3 LTS (2020.3.8 f1 이상 권장)

### <a name="minimum-versions"></a>최소 버전

이 페이지의 지침에는 아래 나열 된 최신 최신 Unity 및 OpenXR 요구 사항이 설정 되어 있습니다.

* 최신 Unity OpenXR 플러그 인 (1.2 이상 권장)
* 최신 Mixed Reality OpenXR 플러그 인 (버전 1.0.0 이상 권장)
* **(선택 사항)** 최신 MRTK, (버전 2.7 이상 권장)
* **(선택 사항)** 최신 유니버설 렌더링 파이프라인 패키지 (버전 10.5.1 이상 권장)

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> Windows PC에서 VR 응용 프로그램을 작성 하는 경우 Mixed Reality OpenXR 플러그 인이 반드시 필요한 것은 아닙니다. 그러나 HP 반향 G2 컨트롤러에 대 한 컨트롤러 매핑을 사용자 지정 하거나 HoloLens 2와 VR 헤드셋 모두에서 작동 하는 앱을 빌드하는 경우에는 플러그 인을 설치 하는 것이 좋습니다.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Microsoft는 Unity 2020의 모든 새 프로젝트에 대해 Windows XR 플러그 인을 사용 하지 않는 것이 좋습니다.

그러나 Unity 2019을 사용 중이 고 ARCore/Arcore 장치와의 호환성을 위해 AR Foundation 2.0이 필요한 경우이 플러그 인이 해당 지원을 사용 하도록 설정 합니다.

> [!IMPORTANT]
> Unity 2019에서이 플러그 인을 사용 하면 Azure 공간 앵커가 지원 되지 않습니다. 

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

Unity 2019 이전 버전을 사용 하는 경우에는 레거시 기본 제공 XR 지원을 사용 하는 것이 좋습니다. Windows XR 플러그 인은 Unity 2019에서 작동 하지만 Azure 공간 앵커가 지원 되지 않기 때문에 권장 되지 않습니다.