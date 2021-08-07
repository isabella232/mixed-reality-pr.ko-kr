---
title: Unity 버전 및 XR 플러그 인 선택
description: HoloLens 응용 프로그램 개발에 대 한 최신 Unity 및 XR 플러그 인 권장 사항을 최신으로 유지 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: 7d22ccee301345352ae384f8b237415f925bbd254e0923197130caf48540c171
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210890"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>Unity 버전 및 XR 플러그 인 선택

현재 혼합 현실 개발용으로 **최신 Mixed Reality OpenXR 플러그 인 Unity 2020.3 LTS를 설치 하는 것이 좋습니다** . 또한 다른 Unity 구성으로 앱을 빌드할 수 있습니다.

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (권장)

HoloLens 2 및 Windows Mixed Reality 개발에 대 한 Microsoft의 현재 권장 unity 구성은 **최신 Mixed Reality OpenXR 플러그 인을 사용 하는 Unity 2020.3 lts** 입니다. 이전 2020.3 빌드의 알려진 성능 문제를 방지 하려면 Unity 패치 릴리스 2020.3.8 f1 이상을 사용 **해야 합니다** .

> [!IMPORTANT]
> Unity 2020은 HoloLens (첫 번째 gen)를 대상으로 하는 것을 지원 하지 않습니다. 이러한 헤드셋은 unity 2019 LTS의 전체 수명 주기에 대 한 레거시 기본 제공 XR를 사용 하는 **[unity 2019 lts](#unity-20194-lts)** 에서 중부 2022를 통해 계속 지원 됩니다.

Unity를 설치 하 고 관리 하는 가장 좋은 방법은 **Unity 허브** 를 통하는 것입니다.

1. <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity 허브**</a>를 설치 합니다.
2. **설치** 탭을 선택 하 고 **추가** 를 선택 합니다.
3. **Unity 2020.3 LTS** 를 선택 하 고 **다음** 을 클릭 합니다.

![Unity 허브 설치 새 버전](images/unity-hub-img-01.png)

4. **' 플랫폼 '** 아래에서 다음 구성 요소를 확인 합니다.
    * **유니버설 Windows 플랫폼 빌드 지원**
    * **Windows 빌드 지원(IL2CPP)**

![Unity 유니버설 Windows 플랫폼 빌드 지원 옵션](../images/Unity_Install_Option_UWP.png)

5. 이러한 옵션을 사용 하지 않고 Unity를 이전에 설치한 경우 Unity 허브의 **' 모듈 추가 '** 메뉴를 통해 추가할 수 있습니다.

![Unity Windows 빌드 지원 옵션](../images/Unity_Install_Option_UWP2.png)

Unity 2020.3을 설치한 후에는 Mixed Reality OpenXR 플러그 인을 사용 하 여 프로젝트를 만들거나 기존 프로젝트를 업그레이드 하기 시작 합니다.

> [!div class="nextstepaction"]
> [OpenXR 플러그 인을 사용 하 여 프로젝트 설정](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> 모든 새 프로젝트에 OpenXR를 사용 하는 것이 좋지만 Unity 2020.3 lts는 [Windows XR 플러그 인](xr-project-setup.md?tabs=windowsxr)도 지원 합니다. 이 플러그 인은 AR 기반 4.0 지원과 같은 새로운 기능을 받지 않지만 완전히 지원 됩니다.

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

Unity 2019을 사용 해야 하는 경우 **unity 2019 LTS와 레거시 기본 제공 XR** 를 사용할 수 있습니다. Unity 2019.4 LTS에서 레거시 기본 제공 XR를 시작 하려면 여기를 클릭 하세요.

> [!div class="nextstepaction"]
> [레거시 기본 제공 XR를 사용 하 여 프로젝트 설정](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> Unity는 Unity 2019에서 레거시 기본 제공 XR 지원을 사용 하지 않습니다.  Unity 2019는 새로운 XR 플러그 인 프레임 워크를 제공 하지만 Microsoft는 현재 Azure 공간 앵커가 AR Foundation 2와의 호환성 때문에 Unity 2019에서 해당 경로를 제안 하지 않습니다.  Unity 2020에서 Azure 공간 앵커는 XR 플러그 인 프레임 워크 내에서 지원 됩니다.

HoloLens (첫 번째 gen) 용 앱을 개발 하는 경우, 이러한 헤드셋은 unity 2019 lts의 전체 수명 주기에 대 한 레거시 기본 제공 XR를 사용 하 여 2019 lts를 2022 통해 lts에서 계속 지원 됩니다.

## <a name="unity-20212"></a>Unity 2021.2

초기 **Unity 2021.2** 빌드를 시도 하는 경우 [**Mixed Reality OpenXR 플러그**](xr-project-setup.md?tabs=openxr)인을 시작 하세요. OpenXR 플러그 인은 Windows XR 플러그 인을 지 원하는 최종 unity 버전이 unity 2021.1 이기 때문에 unity 2021.2 이상에서 혼합 현실 개발의 유일한 경로입니다.

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Unity 2018.4 LTS가 Unity의 2 년 Long-Term 지원 기간 끝에 도달 하 여 프로젝트를 계속 실행 하지만 Unity에서 업데이트를 더 이상 받지 않습니다.

Unity 2018 프로젝트가 있는 경우 Unity 2020.3 LTS 및 Mixed Reality OpenXR 플러그 인으로의 마이그레이션을 계획 하는 것이 좋습니다.