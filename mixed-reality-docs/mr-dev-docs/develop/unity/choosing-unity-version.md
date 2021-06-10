---
title: Unity 버전 및 XR 플러그 인 선택
description: HoloLens 응용 프로그램 개발에 대 한 최신 Unity 및 XR 플러그 인 권장 사항을 최신으로 유지 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: da171db41e508fe556d8645b23f12f6f437446a1
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908236"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Unity 버전 및 XR 플러그 인 선택

현재 **Unity 2019.4 LTS를 설치 하 고 혼합 현실 개발용으로 레거시 기본 제공 XR를 사용 하는 것이 좋습니다** . 다른 Unity 구성으로 앱을 빌드할 수도 있습니다.

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (권장)

Microsoft의 최신 권장 Unity 구성-HoloLens 2 및 Windows Mixed Reality 개발은 **레거시 기본 제공 XR 지원을 사용 하는 Unity 2019.4 LTS** 입니다.

Unity를 설치 하 고 관리 하는 가장 좋은 방법은 <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity 허브]</a>를 통하는 것입니다. 설치 된 경우 Unity 허브를 엽니다.

1. **설치** 탭을 선택 하 고 **추가** 를 선택 합니다.
2. Unity 2019.4 LTS를 선택 하 고 **다음** 을 클릭 합니다.

![Unity 허브 설치할 새 버전](images/unity-hub-img-01.png)

3. **' 플랫폼 '** 아래에서 다음 구성 요소를 확인 합니다.
    * **유니버설 Windows 플랫폼 빌드 지원** 
    * **Windows 빌드 지원(IL2CPP)**

![Unity 유니버설 Windows 플랫폼 빌드 지원 옵션](../images/Unity_Install_Option_UWP.png)

4. 이러한 옵션 없이 Unity를 설치한 경우 Unity 허브의 **' 모듈 추가 '** 메뉴를 통해 unity를 추가할 수 있습니다.

![Unity Windows 빌드 지원 옵션](../images/Unity_Install_Option_UWP2.png)

Unity 2019.4 LTS에서 레거시 기본 제공 XR를 시작 하려면 여기를 클릭 하세요.

> [!div class="nextstepaction"]
> [레거시 기본 제공 XR 설정](legacy-xr-support.md)

> [!NOTE]
> Unity는 Unity 2019에서 레거시 기본 제공 XR 지원을 사용 하지 않습니다.  Unity 2019는 새로운 XR 플러그 인 프레임 워크를 제공 하지만 Microsoft는 현재 Azure 공간 앵커가 AR Foundation 2와의 호환성 때문에 Unity 2019에서 해당 경로를 제안 하지 않습니다.  Unity 2020에서 Azure 공간 앵커는 XR 플러그 인 프레임 워크 내에서 지원 됩니다.

HoloLens 용 앱을 개발 하는 경우 (첫 번째 gen), 이러한 헤드셋은 unity 2019 LTS의 전체 수명 주기에 대 한 레거시 기본 제공 XR를 사용 하 여 2019 LTS를 2022 통해 계속 지원 됩니다.

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

**Unity 2020.3 LTS** 를 사용 하는 경우 **windows XR 플러그 인** 을 사용 하 여 HoloLens 2 및 Windows Mixed Reality 응용 프로그램을 개발할 수 있습니다.

그러나 HoloLens 안정성 및 HoloLens 2의 기타 기능에 영향을 주는 알려진 문제는 다음과 같습니다. 

* 유니버설 Windows 플랫폼 빌드 대상을 사용 하는 Holographic app remoting 응용 프로그램이 작동 하지 않습니다.
* Unity graphics jobs 시스템은 HoloLens 프로젝트와 호환 되지 않는 경우에도 기본적으로 켜져 있습니다.

지금 Unity 2020에서 새 프로젝트를 시작 하도록 선택 하는 경우 앱을 출시 하기 전에 업데이트 된 Unity 빌드 및 Windows XR 플러그 인 빌드에 대 한 향후 몇 개월을 수행 해야 합니다.  이렇게 하면 사용자가 홀로그램의 적절 한 안정성을 경험 하 게 됩니다.

> [!div class="nextstepaction"]
> [Windows XR 플러그 인 사용](windows-xr-plugin.md)

### <a name="using-openxr"></a>OpenXR 사용

Unity 2020.3 LTS는 **혼합 현실 OpenXR** 플러그 인에 대 한 공개 미리 보기도 지원 합니다.

Mixed Reality OpenXR 플러그 인은 Ar설계도 Emanager 및 ARRaycastManager 구현을 제공 하 여 AR 기반 4.0을 완벽 하 게 지원 합니다. 그러면 HoloLens 2와 ARCore/Arcore 휴대폰 및 태블릿 범위에 도달할 때 적중 테스트 코드를 작성할 수 있습니다. 

올해 후반에 OpenXR 플러그 인을 사용 하는 **unity 2020.3 LTS** 는 권장 unity 구성이 되며 unity의 이후 HoloLens 2 기능은이 플러그 인을 통해서만 노출 됩니다.

> [!div class="nextstepaction"]
> [OpenXR 플러그 인 사용](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021.1

초기 **Unity 2021.1** 빌드를 시도 하는 경우 Windows XR 플러그 인이 더 이상 사용 되지 않으므로 **OpenXR 플러그 인** 으로 이동 해야 합니다.  Unity 2021.2부터 Windows XR 플러그 인이 더 이상 지원 되지 않으므로 OpenXR 플러그 인은 혼합 현실 개발의 유일한 경로입니다.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Unity 2018.4 LTS를 사용 하는 프로젝트가 이미 있는 경우 Unity 엔진은 릴리스 후 2 년 동안 계속 지원 됩니다.  Unity 2018 LTS는 2021의 스프링에서 서비스 종료에 도달 합니다.