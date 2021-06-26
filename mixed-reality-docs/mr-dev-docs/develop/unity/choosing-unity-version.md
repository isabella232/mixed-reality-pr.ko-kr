---
title: Unity 버전 및 XR 플러그 인 선택
description: HoloLens 애플리케이션 개발을 위한 최신 Unity 및 XR 플러그 인 권장 사항을 최신 상태로 유지합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, mixed reality 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: 646a0ec3b3b332b038509cba39caa085c1590c1a
ms.sourcegitcommit: 593e8f80297ac0b5eccb2488d3f333885eab9adf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112921430"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Unity 버전 및 XR 플러그 인 선택

현재 Mixed Reality 개발을 위해 **최신 Mixed Reality OpenXR 플러그 인이 있는 Unity 2020.3 LTS를 설치하는 것이 좋지만** 다른 Unity 구성으로 앱을 빌드할 수도 있습니다.

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS(권장)

HoloLens 2 및 Windows Mixed Reality 개발을 위한 Microsoft의 현재 권장 Unity 구성은 **최신 Mixed Reality OpenXR 플러그 인이 있는 Unity 2020.3 LTS입니다.** 이전 2020.3 빌드에서 알려진 성능 문제를 방지하려면 Unity 패치 릴리스 2020.3.8f1 이상 버전을 사용해야 합니다.

> [!IMPORTANT]
> Unity 2020은 HoloLens(1세대)를 대상으로 하는 것을 지원하지 않습니다. 이러한 헤드셋은 **[Unity 2019 LTS의](#unity-20194-lts)** 전체 수명 주기에서 2022년 중간까지 레거시 기본 제공 XR이 있는 Unity 2019 LTS에서 계속 지원됩니다.
>
> [!NOTE]
> 일부 패키지는 Unity 2020 LTS의 혼합 현실 프로젝트와 아직 호환되지 않습니다.
> 
> * URP(유니버설 렌더링 파이프라인) 10.5.0 이상에는 HoloLens 2 디바이스에서 알려진 성능 문제가 있습니다. _(다음 URP 릴리스에서 수정됨)_
> * Azure Remote Rendering Unity 2020을 지원하는 업데이트된 릴리스를 아직 제공하지 않았습니다.
>
> Unity 프로젝트에서 유니버설 렌더링 파이프라인 또는 Azure Remote Rendering 사용하는 경우 업데이트된 패키지를 사용할 수 있을 때까지 프로젝트를 Unity 2020으로 업그레이드하는 것을 보류하는 것이 좋습니다.

Unity를 설치하고 관리할 때 가장 좋은 방법은 <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>를 사용하는 것입니다. 설치되면 Unity Hub를 엽니다.

1. 설치 **탭을** 선택하고 **추가를** 선택합니다.
2. Unity 2020.3 LTS를 선택하고 **다음을** 클릭합니다.

![Unity 허브 새 버전 설치](images/unity-hub-img-01.png)

3. **'플랫폼'에서** 다음 구성 요소를 확인합니다.
    * **유니버설 Windows 플랫폼 빌드 지원**
    * **Windows 빌드 지원(IL2CPP)**

![Unity 유니버설 Windows 플랫폼 빌드 지원 옵션](../images/Unity_Install_Option_UWP.png)

4. 이러한 옵션 없이 Unity를 설치한 경우 Unity Hub의 **'모듈 추가'** 메뉴를 통해 추가할 수 있습니다.

![Unity Windows 빌드 지원 옵션](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [OpenXR 플러그 인 사용](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> 모든 새 프로젝트에 OpenXR을 사용하는 것이 좋습니다. Unity 2020.3 LTS는 [Windows XR 플러그 인](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)도 지원합니다. 이 플러그 인은 AR Foundation 4.0 지원과 같은 새로운 기능을 받지 못하지만 완전히 지원됩니다.

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

Unity 2019를 사용해야 하는 경우 **레거시 기본 제공 XR 에서 Unity 2019 LTS를** 사용할 수 있습니다. Unity 2019.4 LTS에서 레거시 기본 제공 XR을 시작하려면 다음을 클릭합니다.

> [!div class="nextstepaction"]
> [레거시 기본 제공 XR 설정](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> Unity는 Unity 2019부터 레거시 기본 제공 XR 지원이 더 이상 사용되지 않습니다.  Unity 2019는 새로운 XR 플러그 인 프레임워크를 제공하지만, Azure Spatial Anchors AR Foundation 2와의 비호환성으로 인해 Microsoft는 현재 Unity 2019에서 해당 경로를 권장하지 않습니다.  Unity 2020에서 Azure Spatial Anchors XR 플러그 인 프레임워크 내에서 지원됩니다.

HoloLens(1세대)용 앱을 개발하는 경우 이러한 헤드셋은 Unity 2019 LTS의 전체 수명 주기 동안 Unity 2019 LTS에서 레거시 기본 제공 XR이 있는 Unity 2022 LTS에서 계속 지원됩니다.

## <a name="unity-20211"></a>Unity 2021.1

초기 **Unity 2021.1** 빌드를 시도하는 경우 Windows **XR 플러그 인이** 더 이상 사용되지 않으면 OpenXR 플러그 인 로 이동해야 합니다.  Unity 2021.2부터는 Windows XR 플러그 인이 더 이상 지원되지 않아 OpenXR 플러그 인이 Mixed Reality 개발을 위한 유일한 경로가 됩니다.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Unity 2018.4 LTS를 사용하는 프로젝트가 이미 있는 경우 Unity 엔진은 릴리스 후 2년 동안 계속 지원됩니다.  Unity 2018 LTS는 2021년 봄 서비스 종료에 도달합니다.
