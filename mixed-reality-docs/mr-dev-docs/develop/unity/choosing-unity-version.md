---
title: Unity 버전 및 XR 플러그 인 선택
description: HoloLens 응용 프로그램 개발에 대 한 최신 Unity 및 XR 플러그 인 권장 사항을 최신으로 유지 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 05/27/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: 1f658c0e69091ce0aaeb37b7f427e57f060c3fb2
ms.sourcegitcommit: 62e5909b837c9c7ecedd040164f2308868db4723
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2021
ms.locfileid: "111741925"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Unity 버전 및 XR 플러그 인 선택

현재 혼합 현실 개발용으로 **최신 Mixed Reality OpenXR 플러그 인 Unity 2020.3 LTS를 설치 하는 것이 좋습니다** . 또한 다른 Unity 구성으로 앱을 빌드할 수 있습니다.

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (권장)

Microsoft의 최신 권장 Unity 구성-HoloLens 2 및 Windows Mixed Reality 개발은 **최신 Mixed Reality OpenXR 플러그 인 unity 2020.3 LTS** 입니다.

> [!IMPORTANT]
> Unity 2020은 HoloLens (첫 번째 gen)를 대상으로 지정 하는 기능을 지원 하지 않습니다. 이러한 헤드셋은 unity 2019 LTS의 전체 수명 주기에 대 한 레거시 기본 제공 XR를 사용 하는 **[unity 2019 lts](#unity-20194-lts)** 에서 중부 2022를 통해 계속 지원 됩니다.

Mixed Reality OpenXR 플러그 인은 Ar설계도 Emanager 및 ARRaycastManager 구현을 제공 하 여 AR 기반 4.0을 완벽 하 게 지원 합니다. 그러면 HoloLens 2와 ARCore/Arcore 휴대폰 및 태블릿 범위에 도달할 때 적중 테스트 코드를 작성할 수 있습니다.

Unity를 설치하고 관리할 때 가장 좋은 방법은 <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>를 사용하는 것입니다. 설치 된 경우 Unity 허브를 엽니다.

1. **설치** 탭을 선택 하 고 **추가** 를 선택 합니다.
2. Unity 2020.3 LTS를 선택 하 고 **다음** 을 클릭 합니다.

![Unity 허브 설치할 새 버전](images/unity-hub-img-01.png)

3. **' 플랫폼 '** 아래에서 다음 구성 요소를 확인 합니다.
    * **유니버설 Windows 플랫폼 빌드 지원**
    * **Windows 빌드 지원(IL2CPP)**

![Unity 유니버설 Windows 플랫폼 빌드 지원 옵션](../images/Unity_Install_Option_UWP.png)

4. 이러한 옵션 없이 Unity를 설치한 경우 Unity 허브의 **' 모듈 추가 '** 메뉴를 통해 unity를 추가할 수 있습니다.

![Unity Windows 빌드 지원 옵션](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [OpenXR 플러그 인 사용](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> 모든 새 프로젝트에 OpenXR를 사용 하는 것이 좋지만 Unity 2020.3 LTS는 **[WINDOWS XR 플러그 인](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)** 도 지원 합니다. 홀로그램 안정성 및 HoloLens 2의 기타 기능에 영향을 주는 알려진 문제는 다음과 같습니다.
>
> * 유니버설 Windows 플랫폼 빌드 대상을 사용 하는 Holographic app remoting 응용 프로그램이 작동 하지 않습니다.
> * Unity graphics jobs 시스템은 HoloLens 프로젝트와 호환 되지 않는 경우에도 기본적으로 켜져 있습니다.

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

Unity 2019을 사용 해야 하는 경우 **unity 2019 LTS와 레거시 기본 제공 XR** 를 사용할 수 있습니다. Unity 2019.4 LTS에서 레거시 기본 제공 XR를 시작 하려면 여기를 클릭 하세요.

> [!div class="nextstepaction"]
> [레거시 기본 제공 XR 설정](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> Unity는 Unity 2019에서 레거시 기본 제공 XR 지원을 사용 하지 않습니다.  Unity 2019는 새로운 XR 플러그 인 프레임 워크를 제공 하지만 Microsoft는 현재 Azure 공간 앵커가 AR Foundation 2와의 호환성 때문에 Unity 2019에서 해당 경로를 제안 하지 않습니다.  Unity 2020에서 Azure 공간 앵커는 XR 플러그 인 프레임 워크 내에서 지원 됩니다.

HoloLens 용 앱을 개발 하는 경우 (첫 번째 gen), 이러한 헤드셋은 unity 2019 LTS의 전체 수명 주기에 대 한 레거시 기본 제공 XR를 사용 하 여 2019 LTS를 2022 통해 계속 지원 됩니다.

## <a name="unity-20211"></a>Unity 2021.1

초기 **Unity 2021.1** 빌드를 시도 하는 경우 Windows XR 플러그 인이 더 이상 사용 되지 않으므로 **OpenXR 플러그 인** 으로 이동 해야 합니다.  Unity 2021.2부터 Windows XR 플러그 인이 더 이상 지원 되지 않으므로 OpenXR 플러그 인은 혼합 현실 개발의 유일한 경로입니다.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Unity 2018.4 LTS를 사용 하는 프로젝트가 이미 있는 경우 Unity 엔진은 릴리스 후 2 년 동안 계속 지원 됩니다.  Unity 2018 LTS는 2021의 스프링에서 서비스 종료에 도달 합니다.
