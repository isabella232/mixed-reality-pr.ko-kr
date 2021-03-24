---
title: BuildAndDeploy
description: 다양한 디바이스에 앱을 빌드하고 배포하기 위한 설명서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Visual Studio, Android, IOS
ms.openlocfilehash: 3256296c1fd13ad051d2c75805c49ec555e8977d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686465"
---
# <a name="building-and-deploying-mrtk"></a>MRTK 빌드 및 배포

디바이스에서 앱을 독립 실행형 앱(HoloLens, Android, iOS 등)으로 실행하려면 Unity 프로젝트에서 빌드 및 배포 단계를 실행해야 합니다. MRTK를 사용하는 앱을 빌드하고 배포하는 것은 다른 Unity 앱을 빌드하고 배포하는 것과 같습니다. MRTK 관련 지침은 없습니다. HoloLens용 Unity 앱을 빌드하고 배포하는 방법에 대한 자세한 단계를 보려면 아래를 참조하세요.  [빌드 게시](https://docs.unity3d.com/Manual/PublishingBuilds.html)에서 다른 플랫폼용 빌드에 대해 자세히 알아보세요.

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a>HoloLens 1 및 HoloLens 2(UWP)에 MRTK 빌드 및 배포

HoloLens 1 및 HoloLens 2(UWP)를 빌드하고 배포하는 방법에 대한 지침은 [디바이스에 애플리케이션 빌드](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)에서 찾을 수 있습니다.

**팁:** WMR, HoloLens 1 또는 HoloLens 2를 빌드할 때에는 빌드 설정 "대상 SDK 버전" 및 "최소 플랫폼 버전"은 아래 그림과 같이 표시되는 것이 좋습니다.

![빌드 창](../features/images/getting-started/BuildWindow.png)

기타 설정은 다를 수 있습니다(예를 들어, 빌드 구성/아키텍처/빌드 유형 및 다른 설정은 Visual Studio 솔루션 내에서 항상 변경할 수 있음).

"대상 SDK 버전" 드롭다운에 "10.0.18362.0" 옵션이 포함되어 있는지 확인합니다. 이 항목이 없으면 [최신 Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)를 설치해야 합니다.

### <a name="unity-20193-and-hololens"></a>Unity 2019.3 및 HoloLens

HoloLens 앱이 디바이스에서 2D 패널로 표시되는 경우 UWP 앱을 배포하기 전에 Unity 2019.3.x에서 다음 설정이 구성되었는지 확인합니다.

레거시 XR을 사용하는 경우:

1. 편집 > 프로젝트 설정, 플레이어로 이동합니다.
1. UWP 탭의 **XR 설정** 에서 **가상 현실 지원** 이 활성화되어 있고 **Windows Mixed Reality** SDK가 SDK에 추가되었는지 확인합니다.
1. Visual Studio에서 빌드 및 배포

XR-Plugin을 사용하는 경우:

1. [XRSDK 시작](../configuration/GettingStartedWithMRTKAndXRSDK.md)에 있는 단계를 따릅니다.
1. 구성 프로필이 **DefaultXRSDKConfigurationProfile** 인지 확인합니다.
1. **편집 > 프로젝트 설정, XR-Plugin 관리** 로 이동하여 **Windows Mixed Reality** 를 사용하는지 확인합니다.
1. Visual Studio에서 빌드 및 배포

>[!IMPORTANT]
> Unity 2019.3.x를 사용하는 경우 Visual Studio의 빌드 아키텍처로 **ARM64** 를 선택하고 **ARM** 은 선택하지 않습니다. Unity 2019.3.x의 기본 Unity 설정을 사용하면 Unity 버그로 인해 ARM이 선택된 경우 Unity 앱은 HoloLens에 배포하지 않습니다. 이는 [Unity의 문제 추적기](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)에서 추적할 수 있습니다.
>
> ARM 아키텍처가 필요한 경우 **편집 > 프로젝트 설정, 플레이어** 로 이동하고 **기타 설정** 메뉴에서 **그래픽 작업** 을 사용하지 않도록 설정합니다. **그래픽 작업** 을 사용하지 않도록 설정하면 앱이 Unity 2019.3.x용 ARM 빌드 아키텍처를 사용하여 배포할 수는 있지만 ARM64가 권장됩니다.

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a>Windows Mixed Reality 헤드셋에 MRTK 빌드 및 배포

WMR(Windows Mixed Reality) 헤드셋을 UWP(유니버설 Windows 플랫폼) 및 독립 실행형 빌드에 사용할 수 있습니다.  WMR 헤드셋에 대한 독립 실행형 빌드를 사용하려면 다음과 같은 추가 단계가 필요합니다.

> [!NOTE]
> Unity의 XR SDK는 또한 독립 실행형 빌드에서 기본 WMR을 지원하지만 SteamVR 또는 WMR 플러그인은 필요하지 않습니다. 이러한 단계는 Unity의 레거시 XR에 필요합니다.

1. [Steam](https://store.steampowered.com/about/)을 설치합니다.
1. [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)을 설치합니다.
1. [WMR 플러그 인](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)을 설치합니다.

### <a name="how-to-use-wmr-plugin"></a>WMR 플러그 인을 사용하는 방법

1. Steam를 열고 Windows Mixed Reality 플러그 인을 검색합니다.
    - WMR 플러그 인을 시작하기 전에 SteamVR이 닫혀 있는지 확인합니다. WMR 플러그 인을 시작하면 SteamVR도 시작됩니다.
    - WMR 헤드셋이 연결되어 있는지 확인합니다.

    ![WMR 플러그 인 검색](../features/images/build-deploy/wmr/SteamSearchWMRPlugin.png)

1. SteamVR 플러그 인용 Windows Mixed Reality의 경우 **시작** 을 선택합니다.

    ![WMR 플러그 인](../features/images/build-deploy/wmr/WMRPlugin.png)

    - SteamVR 및 WMR 플러그 인이 시작되고 WMR 헤드셋에 대한 새 추적 상태 창이 표시됩니다.
    - 자세한 내용은 [Windows Mixed Reality Steam 설명서](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)를 참조하세요.

        ![WMR 시작 모양](../features/images/build-deploy/wmr/WMRPluginActive.png)

1. Unity에서 MRTK 장면이 열린 상태에서 **파일 > 빌드 설정** 으로 이동합니다.

1. 장면 빌드
    - **열린 장면 추가** 를 선택합니다.
    - 플랫폼이 **독립 실행형** 인지 확인합니다.
    - **빌드** 를 선택합니다.
    - 파일 탐색기에서 새 빌드의 위치를 선택합니다.

    ![독립 실행형에 대한 빌드 설정](../features/images/build-deploy/wmr/BuildSettingsStandaloneUnity.png)

1. 새 Unity 실행 파일이 생성되며, 앱을 시작하려면 파일 탐색기에서 Unity 실행 파일을 선택합니다.

    ![파일 탐색기 Unity](../features/images/build-deploy/wmr/FileExplorerUnityExe.png)

## <a name="see-also"></a>참고 항목

- [Android 및 iOS 지원](../features/cross-platform/UsingARFoundation.md)
- [Leap Motion 지원](../features/cross-platform/LeapMotionMRTK.md)
- [플랫폼 기능 검색](../features/cross-platform/DetectingPlatformCapabilities.md)
