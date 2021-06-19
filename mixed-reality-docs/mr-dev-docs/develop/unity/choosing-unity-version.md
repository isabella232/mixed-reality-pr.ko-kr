---
title: Unity 버전 및 XR 플러그 인 선택
description: HoloLens 애플리케이션 개발을 위한 최신 Unity 및 XR 플러그 인 권장 사항을 최신 상태로 유지합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, mixed reality 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: 452692b1be98459cc242833149b1cfd91f0f4d4a
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394423"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Unity 버전 및 XR 플러그 인 선택

현재 Unity **2019.4 LTS를 설치하고** Mixed Reality 개발을 위해 레거시 기본 제공 XR을 사용하는 것이 좋지만 다른 Unity 구성을 사용하여 앱을 빌드할 수도 있습니다.

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS(권장)

HoloLens 2 및 Windows Mixed Reality 개발을 위한 Microsoft의 현재 권장 Unity 구성은 레거시 기본 제공 XR 지원을 **사용하는 Unity 2019.4 LTS입니다.**

Unity를 설치하고 관리하는 가장 좋은 방법은 <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>를 통하는 것입니다. 설치되면 Unity Hub를 엽니다.

1. 설치 **탭을** 선택하고 **추가를** 선택합니다.
2. Unity 2019.4 LTS를 선택하고 **다음을** 클릭합니다.

![Unity 허브 새 버전 설치](images/unity-hub-img-2019.png)

3. **'플랫폼'에서** 다음 구성 요소를 확인합니다.
    * **유니버설 Windows 플랫폼 빌드 지원** 
    * **Windows 빌드 지원(IL2CPP)**

![Unity 유니버설 Windows 플랫폼 빌드 지원 옵션](images/Unity_Install_Option_UWP_2019.png)

4. 이러한 옵션 없이 Unity를 설치한 경우 Unity Hub의 **'모듈 추가'** 메뉴를 통해 추가할 수 있습니다.

![Unity Windows 빌드 지원 옵션](images/Unity_Install_Option_UWP2_2019.png)

Unity 2019.4 LTS에서 레거시 기본 제공 XR을 시작하려면 다음을 클릭합니다.

> [!div class="nextstepaction"]
> [레거시 기본 제공 XR 설정](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> Unity는 Unity 2019부터 레거시 기본 제공 XR 지원이 더 이상 사용되지 않습니다.  Unity 2019는 새로운 XR 플러그 인 프레임워크를 제공하지만, Azure Spatial Anchors AR Foundation 2와의 비호환성으로 인해 Microsoft는 현재 Unity 2019에서 해당 경로를 권장하지 않습니다.  Unity 2020에서 Azure Spatial Anchors XR 플러그 인 프레임워크 내에서 지원됩니다.

HoloLens(1세대)용 앱을 개발하는 경우 이러한 헤드셋은 Unity 2019 LTS의 전체 수명 주기 동안 Unity 2019 LTS에서 레거시 기본 제공 XR이 있는 Unity 2022 LTS에서 계속 지원됩니다.

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

**Unity 2020.3 LTS를** 사용하는 경우 Microsoft의 현재 권장 사항은 **최신 Mixed Reality OpenXR 플러그 인** 입니다. 이전 2020.3 빌드에서 알려진 성능 문제를 방지하려면 Unity 패치 릴리스 2020.3.8f1 이상 버전을 사용해야 합니다.

Mixed Reality OpenXR 플러그 인은 ARPlaneManager 및 ARRaycastManager 구현을 제공하여 AR Foundation 4.0을 완벽하게 지원합니다. 이렇게 하면 적중 테스트 코드를 한 번 작성한 다음, HoloLens 2 및 ARCore/ARKit 휴대폰 및 태블릿에 걸쳐 작성할 수 있습니다.

그러나 Unity 2020 LTS 프로젝트에 영향을 주는 알려진 문제가 있습니다.

* URP(유니버설 렌더링 파이프라인) 10.5.0 이상은 HoloLens 2 디바이스에서 성능 저하가 있습니다.

오늘 Unity 2020에서 새 프로젝트를 시작하도록 선택하는 경우 앱을 배송하기 전에 업데이트된 Unity 빌드 및 URP 패키지에 대한 후속 조치를 몇 주 동안 진행해야 합니다.  이렇게 하면 사용자가 적절한 홀로그램 안정성을 경험할 수 있습니다.

> [!div class="nextstepaction"]
> [OpenXR 플러그 인 사용](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

## <a name="unity-20211"></a>Unity 2021.1

초기 **Unity 2021.1** 빌드를 시도하는 경우 Windows **XR 플러그 인이** 더 이상 사용되지 않으면 OpenXR 플러그 인 로 이동해야 합니다.  Unity 2021.2부터는 Windows XR 플러그 인이 더 이상 지원되지 않아 OpenXR 플러그 인이 Mixed Reality 개발을 위한 유일한 경로가 됩니다.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Unity 2018.4 LTS를 사용하는 프로젝트가 이미 있는 경우 Unity 엔진은 릴리스 후 2년 동안 계속 지원됩니다.  Unity 2018 LTS는 2021년 봄 서비스 종료에 도달합니다.