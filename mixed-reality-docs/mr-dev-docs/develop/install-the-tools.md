---
title: 도구 설치
description: 최신 버전의 Unity, Visual Studio 및 도구를 사용하여 HoloLens 및 VR 개발에 권장되는 도구를 여기에서 시작합니다.
author: thetuvix
ms.author: alexturn
ms.date: 09/15/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: ff365d7d772410a2cd752072a878c37dae1d9b19
ms.sourcegitcommit: 7dad5bde71d429bb23c72a4074e60b6668a7f091
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2021
ms.locfileid: "127857486"
---
# <a name="install-the-tools"></a>도구 설치

Microsoft HoloLens 및 Windows Mixed Reality 몰입형(VR) 헤드셋을 위한 애플리케이션을 빌드하는 데 필요한 도구를 다운로드하세요. Windows Mixed Reality 개발을 위한 별도 SDK는 없으므로 Windows 10 SDK에서 Visual Studio를 사용합니다.

혼합 현실 디바이스가 없나요? [HoloLens 에뮬레이터](platform-capabilities-and-apis/using-the-hololens-emulator.md)를 설치하면 HoloLens 없이도 혼합 현실 앱의 일부 기능을 테스트할 수 있습니다. [Windows Mixed Reality 시뮬레이터](platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)를 사용하여 몰입형 헤드셋을 위한 혼합 현실 앱을 테스트할 수도 있습니다.

혼합 현실 앱 만들기를 시작하는 가장 쉬운 방법은 Unity 또는 Unreal 게임 엔진을 설치하는 것입니다. 그러나 사용자 지정 엔진을 사용하려는 경우에는 DirectX에 대해 빌드할 수도 있습니다.

Unity를 사용하는 경우 [Mixed Reality Toolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)의 입력 시뮬레이션을 사용하여 손 인식 및 시선 추적 입력과 같은 다양한 유형의 입력 상호 작용을 테스트할 수 있습니다. Unreal 프로젝트의 경우 [UX Tools 플러그 인](https://github.com/microsoft/MixedReality-UXTools-Unreal)을 사용하여 공통 입력 상호 작용 및 사용자 환경 기능을 테스트합니다.

>[!TIP]
>이 페이지에 책갈피를 지정하고 정기적으로 확인하면서 혼합 현실 개발에 권장되는 각 도구를 최신 상태로 유지하세요.

<br>

## <a name="installation-checklist"></a>설치 검사 목록

| 도구 | 참고 |
|---------|---------|
| ![Windows 로고](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**(수동 설치 링크)</a><br><br>PC의 운영 체제가 혼합 현실 애플리케이션을 빌드하는 플랫폼과 일치하도록 최신 버전의 Windows 10을 설치합니다.  | **Windows 10 설치** <br> 설정의 Windows 업데이트를 통해 또는 설치 미디어를 만들어(왼쪽 열의 링크 사용) 최신 버전의 Windows 10을 설치할 수 있습니다. <br><br>각 릴리스의 Windows 10에서 사용할 수 있는 최신 혼합 현실 기능에 대한 내용은 [현재 릴리스 정보](/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md)를 참조하세요. 설정 > 업데이트 및 보안 > 개발자용에서 **PC의 개발자 모드를 사용하도록 설정** 합니다. <br><br> **엔터프라이즈 및 회사 관리용 PC에 대한 참고 사항**<br>조직의 IT 부서에서 PC를 관리하는 경우 업데이트하려면 해당 부서에 문의해야 할 수도 있습니다. <br><br> **Windows용 'N' 버전**<br> Windows Mixed Reality 몰입형(VR) 헤드셋은 'N' 버전의 Windows에서 지원되지 않습니다. |
| ![Visual Studio 로고 이미지](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019(16.8 이상)** (설치 링크)</a> <br><br>Windows 등을 위한 전기능 IDE(통합 개발 환경)입니다. Visual Studio를 사용하여 코드를 작성하고, 디버그하고, 테스트하고, 배포합니다. | **Visual Studio 2019 설치** <br> 다음 워크로드를 설치합니다. <br><br>*● C++를 사용한 데스크톱 개발*<br>*● UWP(유니버설 Windows 플랫폼) 개발*<br>*● Unity를 사용한 게임 개발(**Unity를 사용하려는 경우**)*<br><br>UWP 워크로드 내에서 **다음 구성 요소가 설치에 포함되어 있는지 확인합니다.**<br><br>*● Windows 10 SDK 버전 10.0.19041.0 또는 10.0.18362.0*<br>*● USB 디바이스 연결(USB를 통해 HoloLens에 배포/디버그하는 데 필요)*<br>*● C++(v142) 유니버설 Windows 플랫폼 도구(Unity 사용 시 필요)*<br><br>**HoloLens(1세대) 및 데스크톱 Windows Mixed Reality 헤드셋에 대한 참고 사항**<br>데스크톱 Windows Mixed Reality 헤드셋 또는 HoloLens(1세대)용 애플리케이션만 개발하는 경우에는 Visual Studio 2017을 사용하고 이를 통해 설치된 Windows SDK를 사용할 수 있습니다.<br><br>**알려진 문제**<br>Visual Studio 2019 버전 16.0의 혼합 현실 앱 디버깅에는 몇 가지 알려진 이슈가 있습니다.  **Visual Studio 2019 버전 16.8 이상** 으로 업데이트하세요. |
| ![Visual Studio 로고](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2172762" target="_blank">**HoloLens 2 에뮬레이터(Windows Holographic 버전 21H1, 2021년 9월 업데이트)** (설치 링크: 10.0.20348.1010)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens(1세대) 에뮬레이터**(설치 링크: 10.0.17763.134)</a> <br><br>이 선택적 에뮬레이터를 사용하면 실제 HoloLens 없이도 HoloLens 가상 머신 이미지에서 애플리케이션을 실행할 수 있습니다.<br> <br> | 선택적 에뮬레이터 시작 방법에 대한 자세한 내용은 [HoloLens 에뮬레이터 사용](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md)을 참조하세요.<br> <br> 에뮬레이터 설치를 성공적으로 수행하려면 **시스템에서 Hyper-V를 지원해야 합니다**. 자세한 내용은 아래 시스템 요구 사항 섹션을 참조하세요. <br> <br> **HoloLens(1세대) 에뮬레이터에 대한 참고 사항** <br>  설치를 성공적으로 완료하려면 Visual Studio 2017이 필요합니다. Visual Studio 2019를 사용하여 HoloLens(1세대) 에뮬레이터를 설치하는 경우 VS 템플릿을 선택 취소하고 [Visual Studio Marketplace에서 설치해야 합니다](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="install-your-engine-of-choice"></a>원하는 엔진 설치

이제 Windows 10, Visual Studio 및 Windows 10 SDK를 사용할 준비가 되었으므로 원하는 엔진을 설치하고 설정하겠습니다.

> [!div class="nextstepaction"]
> [엔진 선택](choosing-an-engine.md)

## <a name="troubleshooting"></a>문제 해결

### <a name="setting-developer-mode-is-grayed-out"></a>개발자 모드 설정은 회색으로 표시됩니다.

디바이스에서 개발자 모드를 사용하는 데 문제가 발생하면 [디바이스 소유자](/hololens/security-adminless-os)가 아닐 수 있습니다. 다중 사용자 모드에서 디바이스를 먼저 사용하는 사용자가 디바이스 소유자입니다. 이후 사용자는 개발자 모드 또는 기타 구성 변경을 사용하는 데 필요한 권한이 없습니다. 하지만 [HoloLens 보안 설명서](/hololens/security-adminless-os#device-owner)에 자세히 설명된 Autopilot 환경의 첫 번째 사용자가 디바이스 소유자가 아닐 수 있는 예외가 있습니다.

가능한 솔루션은 다음과 같습니다.

* 디바이스를 다른 사용자나 개발자에게 전달하기 전에 디바이스 소유자가 개발자 모드를 켜도록 합니다.
* IT/MDM 관리자가 특정 디바이스 또는 개발자 디바이스 그룹에 대해 CSP [정책 ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)를 사용하도록 제안합니다.
    * 이 정책은 [프로비전 패키지](/hololens/hololens-provisioning) 또는 [HoloLens 디바이스용 MDM](/hololens/hololens-mdm-configure)을 통해 설정할 수 있습니다.
* [ARC(Advanced Recovery Companion)](/hololens/hololens-recovery) 사용

> [!NOTE]
> 디바이스 관리에 대한 자세한 내용은 **[HoloLens 디바이스 관리](/hololens/hololens-csp-policy-overview)** 개요에서 확인할 수 있습니다.

#### <a name="i-cant-deploy-over-usb"></a>USB를 통해 배포할 수 없습니다.

USB를 통해 애플리케이션을 직접 배포할 수 없는 경우 위에 나열된 모든 설치 요구 사항을 충족했는지 확인하고 [단계별 자습서](unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)를 따르세요.
