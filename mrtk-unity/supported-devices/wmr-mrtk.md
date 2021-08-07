---
title: HoloLens 및 WMR 헤드셋에 배포
description: 다양한 디바이스에 앱을 빌드하고 배포하기 위한 설명서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, Visual Studio
ms.openlocfilehash: 622c7ca4b9c527630b5677fe377d1d3108bdfe08c9dc616bfd4d3256b83b9ab0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209480"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a>HoloLens 및 WMR 헤드셋에 배포

mrtk를 사용 하 여 빌드된 응용 프로그램을 windows 장치, UWP (유니버설 Windows Platform) 및 독립 실행형 플랫폼에 배포 하는 방법에는 두 가지가 있습니다. HoloLens 1 또는 HoloLens 2 용으로 빌드된 응용 프로그램은 uwp를 대상으로 하지만, WMR 헤드셋 용으로 빌드된 응용 프로그램은 uwp 또는 독립 실행형을 대상으로 할 수 있습니다.

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a>HoloLens 1, HoloLens 2 및 UWP (WMR 헤드셋)에서 mrtk 빌드 및 배포

UWP ( **HoloLens 1** 및 **HoloLens 2** )에 대 한 빌드 및 배포 방법에 대 한 지침은 [응용 프로그램을 장치에 빌드](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)에서 찾을 수 있습니다. 이러한 단계를 통해 **WMR 헤드셋** 에 배포할 수도 있습니다.

> [!NOTE]
> Visual Studio에서 장치에 응용 프로그램을 배포 하는 경우 장치에 따라 Visual Studio 약간 다르게 구성 해야 합니다. 구성은 다음과 같습니다.
>
>| 플랫폼 | 구성 | 아키텍처 | 대상 |
|---|---|---|---|
| HoloLens 2 | 릴리스 또는 마스터 | ARM64 | 디바이스 |
| HoloLens 1 | 릴리스 또는 마스터 | x86 | 디바이스 |
| WMR 헤드셋 | 릴리스 또는 마스터 | X64 | 로컬 컴퓨터 |

**팁:** HoloLens 1, HoloLens 2 또는 WMR에 대해 빌드할 때 빌드 설정 "대상 SDK 버전" 및 "최소 플랫폼 버전"은 아래 그림에 나와 있는 것 처럼 보입니다.

![빌드 창](../features/images/getting-started/BuildWindow.png)

기타 설정은 다를 수 있습니다(예를 들어, 빌드 구성/아키텍처/빌드 유형 및 다른 설정은 Visual Studio 솔루션 내에서 항상 변경할 수 있음).

"대상 SDK 버전" 드롭다운에 "10.0.18362.0" 옵션이 포함되어 있는지 확인합니다. 이 항목이 없으면 [최신 Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)를 설치해야 합니다.

### <a name="unity-20192020-and-hololens"></a>Unity 2019/2020 및 HoloLens

HoloLens 앱이 장치에서 2d 패널로 표시 되는 경우 UWP 앱을 배포 하기 전에 Unity에서 다음 설정이 구성 되었는지 확인 합니다.

레거시 기본 제공 XR 지원 (Unity 2019에만 해당)을 사용 하는 경우:

1. 편집 > 프로젝트 설정, 플레이어로 이동합니다.
1. UWP 탭의 **XR 설정** 에서 **가상 현실 지원** 이 활성화되어 있고 **Windows Mixed Reality** SDK가 SDK에 추가되었는지 확인합니다.
1. Visual Studio에서 빌드 및 배포

OpenXR 또는 Windows XR 플러그 인을 사용 하는 경우:

1. [XRSDK 시작](../configuration/getting-started-with-mrtk-and-xrsdk.md)에 있는 단계를 따릅니다.
1. 구성 프로필이 **DefaultXRSDKConfigurationProfile** 인지 확인합니다.
1. **편집 > 프로젝트 설정, XR-Plugin 관리** 로 이동하여 **Windows Mixed Reality** 를 사용하는지 확인합니다.
1. Visual Studio에서 빌드 및 배포

>[!IMPORTANT]
> Unity 2019.3.x를 사용하는 경우 Visual Studio의 빌드 아키텍처로 **ARM64** 를 선택하고 **ARM** 은 선택하지 않습니다. Unity 2019.3.x의 기본 Unity 설정을 사용하면 Unity 버그로 인해 ARM이 선택된 경우 Unity 앱은 HoloLens에 배포하지 않습니다.
>
> ARM 아키텍처가 필요한 경우 **편집 > 프로젝트 설정, 플레이어** 로 이동하고 **기타 설정** 메뉴에서 **그래픽 작업** 을 사용하지 않도록 설정합니다. **그래픽 작업** 을 사용하지 않도록 설정하면 앱이 Unity 2019.3.x용 ARM 빌드 아키텍처를 사용하여 배포할 수는 있지만 ARM64가 권장됩니다.
>
> 이 문제는 Unity 2019.4 및 Unity 2020.3에서 해결 되었습니다.

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a>WMR 헤드셋에 MRTK 빌드 및 배포 (독립 실행형)

WMR 헤드셋에서 MRTK의 독립 실행형 빌드를 사용할 수 있습니다. WMR 헤드셋에 대한 독립 실행형 빌드를 사용하려면 다음과 같은 추가 단계가 필요합니다.

> [!NOTE]
> Unity의 XR SDK는 또한 독립 실행형 빌드에서 기본 WMR을 지원하지만 SteamVR 또는 WMR 플러그인은 필요하지 않습니다. 이러한 단계는 Unity의 레거시 XR에 필요합니다.

1. [Steam](https://store.steampowered.com/about/)을 설치합니다.
1. [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)을 설치합니다.
1. [WMR 플러그 인](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)을 설치합니다.

### <a name="how-to-use-wmr-plugin"></a>WMR 플러그 인을 사용하는 방법

1. Steam를 열고 Windows Mixed Reality 플러그 인을 검색합니다.
    - WMR 플러그 인을 시작하기 전에 SteamVR이 닫혀 있는지 확인합니다. WMR 플러그 인을 시작하면 SteamVR도 시작됩니다.
    - WMR 헤드셋이 연결되어 있는지 확인합니다.

    ![WMR 플러그 인 검색](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. SteamVR 플러그 인용 Windows Mixed Reality의 경우 **시작** 을 선택합니다.

    ![WMR 플러그 인](../features/images/build-deploy/WMR/WMRPlugin.png)

    - SteamVR 및 WMR 플러그 인이 시작되고 WMR 헤드셋에 대한 새 추적 상태 창이 표시됩니다.
    - 자세한 내용은 [Windows Mixed Reality Steam 설명서](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)를 참조하세요.

        ![WMR 시작 모양](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. Unity에서 MRTK 장면이 열린 상태에서 **파일 > 빌드 설정** 으로 이동합니다.

1. 장면 빌드
    - **열린 장면 추가** 를 선택합니다.
    - 플랫폼이 **독립 실행형** 인지 확인합니다.
    - **빌드** 를 선택합니다.
    - 파일 탐색기에서 새 빌드의 위치를 선택합니다.

    ![독립 실행형에 대한 빌드 설정](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. 새 Unity 실행 파일이 생성되며, 앱을 시작하려면 파일 탐색기에서 Unity 실행 파일을 선택합니다.

    ![파일 탐색기 Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>참고 항목

- [Android 및 iOS 지원](using-ar-foundation.md)
- [Leap Motion 지원](leap-motion-mrtk.md)
- [플랫폼 기능 검색](detecting-platform-capabilities.md)
