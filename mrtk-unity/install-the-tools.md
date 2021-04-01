---
title: 도구 설치
description: MRTK-Unity, 도구 설명서 페이지 설치
author: polar-kev
ms.author: kesemple
ms.date: 03/02/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, mixed reality toolkit, 설치, 최신 버전, 도구, 시작, 기본 사항, unity, visual studio, toolkit, 혼합 현실 헤드셋, windows Mixed Reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터
ms.openlocfilehash: 117b34ae858e789b1366ce5338e23b8f366377ae
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550563"
---
# <a name="install-the-tools"></a>도구 설치

Microsoft HoloLens 및 Windows Mixed Reality 몰입형(VR) 헤드셋을 위한 애플리케이션을 빌드하는 데 필요한 도구를 다운로드하세요. Windows Mixed Reality 개발을 위한 별도 SDK는 없으므로 Windows 10 SDK에서 Visual Studio를 사용합니다.

혼합 현실 디바이스가 없나요? [HoloLens 에뮬레이터](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)를 설치하면 HoloLens 없이도 혼합 현실 앱의 일부 기능을 테스트할 수 있습니다. [Windows Mixed Reality 시뮬레이터](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator)를 사용하여 몰입형 헤드셋을 위한 혼합 현실 앱을 테스트할 수도 있습니다.

이 페이지에서는 MRTK를 Unity와 함께 사용하는 데 필요한 도구를 설치하는 과정을 안내합니다. 다른 혼합 현실 개발 플랫폼을 살펴보는 데 관심이 있는 경우 [Mixed Reality 개발 소개](/windows/mixed-reality/develop/development?tabs=unity) 페이지를 참조하세요.

[Mixed Reality Toolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)의 입력 시뮬레이션을 사용하여 손 인식 및 시선 추적과 같은 다양한 유형의 입력 상호 작용을 테스트할 수 있습니다.

|팁: 이 페이지에 책갈피를 지정하고 정기적으로 확인하면서 혼합 현실 개발에 권장되는 각 도구를 최신 상태로 유지하세요.|
|---|

## <a name="installation-checklist"></a>설치 검사 목록

| 도구 | 참고 |
|---------|---------|
| ![Windows 로고](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**(수동 설치 링크)</a><br><br>PC의 운영 체제가 혼합 현실 애플리케이션을 빌드하는 플랫폼과 일치하도록 최신 버전의 Windows 10을 설치합니다.  | **Windows 10 설치** <br> 설정의 Windows 업데이트를 통해 또는 설치 미디어를 만들어(왼쪽 열의 링크 사용) 최신 버전의 Windows 10을 설치할 수 있습니다. <br><br>각 릴리스의 Windows 10에서 사용할 수 있는 최신 혼합 현실 기능에 대한 내용은 [현재 릴리스 정보](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)를 참조하세요. 설정 > 업데이트 및 보안 > 개발자용에서 **PC의 개발자 모드를 사용하도록 설정** 합니다. <br><br> **엔터프라이즈 및 회사 관리용 PC에 대한 참고 사항**<br>조직의 IT 부서에서 PC를 관리하는 경우 업데이트하려면 해당 부서에 문의해야 할 수도 있습니다. <br><br> **Windows용 'N' 버전**<br> Windows Mixed Reality 몰입형(VR) 헤드셋은 'N' 버전의 Windows에서 지원되지 않습니다. |
| ![Visual Studio 로고 이미지](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019(16.8 이상)** (설치 링크)</a> <br><br>Windows 등을 위한 전기능 IDE(통합 개발 환경)입니다. Visual Studio를 사용하여 코드를 작성하고, 디버그하고, 테스트하고, 배포합니다. | **Visual Studio 2019 설치** <br> 다음 워크로드를 설치합니다. <br><br>*● C++를 사용한 데스크톱 개발*<br>*● UWP(유니버설 Windows 플랫폼) 개발*<br><br>HoloLens 앱을 개발하려는 경우 UWP 워크로드 내에서 다음과 같은 선택적 구성 요소를 확인해야 합니다.<br><br>*● USB 디바이스 연결*<br><br>**● Unity에 대한 참고 사항:**<br>특정 목적을 위해 최신 버전의 Unity(비 LTS)를 설치하려는 경우가 아니면 Unity 워크로드를 Visual Studio 설치의 일부로 설치하지 *말고*, 대신 아래 설명된 것처럼 **Unity 2019 LTS** 스트림을 설치하는 것이 좋습니다.<br><br>**알려진 문제**<br>Visual Studio 2019 버전 16.0의 혼합 현실 앱 디버깅에는 몇 가지 알려진 이슈가 있습니다.  **Visual Studio 2019 버전 16.8 이상** 으로 업데이트하세요. |
| ![Windows 로고](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK(10.0.18362.0)** (수동 설치 링크)</a> <br><br>HoloLens 2에서 Windows 10 앱을 빌드하기 위한 최신 헤더와 라이브러리, 메타데이터, 도구를 제공합니다. | **HoloLens 2 앱을 빌드하려면 Windows SDK 빌드 18362 이상을 설치해야 합니다.**<br> <br> 데스크톱 Windows Mixed Reality 헤드셋 또는 HoloLens(1세대)용 애플리케이션만 개발하는 경우에는 Visual Studio 2019에서 설치된 Windows SDK를 사용할 수 있습니다. |
| ![Visual Studio 로고](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2154784" target="_blank">**HoloLens 2 에뮬레이터(Windows Holographic 버전 20H2, 2021년 2월 업데이트)** (설치 링크: 10.0.19041.1134)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens(1세대) 에뮬레이터**(설치 링크: 10.0.17763.134)</a> <br><br>이 에뮬레이터를 사용하면 실제 HoloLens 없이도 HoloLens 가상 머신 이미지에서 애플리케이션을 실행할 수 있습니다.<br> <br> | 에뮬레이터 시작 방법에 대한 자세한 내용은 [HoloLens 에뮬레이터 사용](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)을 참조하세요.<br> <br> 에뮬레이터 설치를 성공적으로 수행하려면 **시스템에서 Hyper-V를 지원해야 합니다**. 자세한 내용은 아래 시스템 요구 사항 섹션을 참조하세요. <br> <br> **HoloLens(1세대) 에뮬레이터에 대한 참고 사항** <br>. Visual Studio 2019를 사용하여 HoloLens(1세대) 에뮬레이터를 설치하는 경우 VS 템플릿을 선택 취소하고 [Visual Studio Marketplace에서 설치해야 합니다](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="unity"></a>Unity

Windows 10, Visual Studio, Windows 10 SDK가 준비되었으면 빌드할 엔진으로 Unity를 사용하겠습니다.

### <a name="1-download-the-latest-version"></a>1. 최신 버전 다운로드

새 프로젝트를 시작할 때 사용하기 가장 좋은 버전은 [Unity LTS(장기 지원)](https://unity3d.com/unity/qa/lts-releases) 스트림이며, 이것을 최신 개정판으로 업데이트하여 안정적인 최신 수정 프로그램을 선택하는 것이 좋습니다.

* 현재 권장 사항은 [Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)를 사용하는 것입니다. Unity 2018.4 LTS도 지원됩니다.
* MRTK와 함께 [Mixed Reality OpenXR](/windows/mixed-reality/develop/unity/openxr-getting-started) 미리 보기 기능을 사용하려는 경우 Unity 2020.2 이상이 필요합니다.
* 특정 이유로 인해 다른 Unity 버전을 사용해야 하는 경우 Unity는 서로 다른 버전을 함께 설치하도록 지원합니다.

### <a name="2-install-the-mixed-reality-feature-tool"></a>2. Mixed Reality Feature Tool 설치

[Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)은 개발자가 혼합형 현실 기능 패키지를 검색하고 Unity 프로젝트에 추가하는 데 사용되는 새로운 방법입니다.

이름 또는 범주로 패키지를 검색하고, 종속성을 확인하고, 가져오기 전에 프로젝트 매니페스트 파일에 대한 제안된 변경 내용도 볼 수 있습니다. 원하는 패키지의 유효성을 검사하면 Mixed Reality Feature Tool에서 사용자가 선택한 Unity 프로젝트로 해당 패키지를 다운로드합니다.

#### <a name="importing-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit 가져오기

[설치 및 사용 지침](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#system-requirements)을 따르고 Mixed Reality Toolkit Foundation 패키지를 선택하여 Mixed Reality Toolkit 패키지를 다운로드할 수 있습니다.

Github에서 MRTK 패키지를 수동으로 다운로드하려면 [Mixed Reality Toolkit-Unity(GitHub)](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)의 릴리스 페이지를 방문하세요.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Mixed Reality 개발용 PC 설정

Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다. 또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다. 일부 도구는 이전 운영 체제에서 지원되지 않습니다.

| 참고: HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다. 필요에 따라 아래 요구 사항을 충족해야 합니다. |
|---|

#### <a name="for-hololens-development"></a>HoloLens 개발

HoloLens 개발을 위해 개발 PC를 설정할 때 [Unity](https://docs.unity3d.com/Manual/system-requirements.html) 및 Visual Studio 둘 다에 대한 시스템 요구 사항을 충족하는지 확인합니다. HoloLens 디바이스에서 앱을 실행하려면 [Windows 장치 포털 설치 지침](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#setting-up-hololens-to-use-windows-device-portal)을 따라야 합니다. [HoloLens 에뮬레이터](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.

HoloLens 에뮬레이터를 시작하려면 [HoloLens 에뮬레이터 사용](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)을 참조하세요.

HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.

### <a name="hololens-troubleshooting"></a>HoloLens 문제 해결

개발자 모드 설정은 회색으로 표시됩니다.

디바이스에서 개발자 모드를 사용하는 데 문제가 발생하면 [디바이스 소유자](/hololens/security-adminless-os)가 아닐 수 있습니다. 다중 사용자 모드에서 디바이스를 먼저 사용하는 사용자가 디바이스 소유자입니다. 이후 사용자는 개발자 모드 또는 기타 구성 변경을 사용하는 데 필요한 권한이 없습니다. 하지만 [HoloLens 보안 설명서](/hololens/hololens2-compliance)에 자세히 설명된 Autopilot 환경의 첫 번째 사용자가 디바이스 소유자가 아닐 수 있는 예외가 있습니다.

가능한 솔루션은 다음과 같습니다.

* 디바이스를 다른 사용자나 개발자에게 전달하기 전에 디바이스 소유자가 개발자 모드를 켜도록 합니다.
* IT/MDM 관리자가 특정 디바이스 또는 개발자 디바이스 그룹에 대해 [CSP 정책 ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)을 사용하도록 제안합니다.
이 정책은 [프로비전 패키지](/hololens/hololens-provisioning) 또는 [HoloLens 디바이스용 MDM](/hololens/hololens-mdm-configure)을 통해 설정할 수 있습니다.
* [ARC(Advanced Recovery Companion)](/hololens/hololens-recovery) 사용

| 참고: 디바이스 관리에 대한 자세한 내용은 HoloLens 디바이스 관리 개요에서 확인할 수 있습니다.|
|---|

USB를 통해 배포할 수 없습니다.

USB를 통해 애플리케이션을 직접 배포할 수 없는 경우 위에 나열된 모든 설치 요구 사항을 충족했는지 확인하고 [단계별 자습서](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02#building-your-application-to-your-hololens-2)를 따르세요.

몰입형 (VR) 헤드셋 요구 사항

| 참고: 다음 지침은 몰입형(VR) 헤드셋 개발 PC에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.|
|---|

| 경고: 이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 소비자 PC 사양을 나타내는 [최소 PC 하드웨어 호환성 지침](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.|
|---|

몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.

현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.

. | 최소 | 권장
--- |--- |---
프로세서 | 노트북: Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 데스크톱: Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 또는 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어| 데스크톱: Intel Desktop i7 6세대(6코어) 또는 AMD Ryzen 5 1600(6코어, 12스레드) GPU | 노트북: NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU 데스크톱: NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU | 데스크톱: NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU
GPU 드라이버 WDDM 버전 | WDDM 2.2 드라이버
열 디자인 전원 | 15W 이상
그래픽 디스플레이 포트 | 헤드셋용 가용 그래픽 디스플레이 포트 1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)
디스플레이 해상도 | 해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상
메모리 | 8GB RAM 이상 | 16GB RAM 이상
스토리지 | >10GB의 추가 사용 가능 공간
USB 포트 | 헤드셋용 가용 USB 포트 1개(USB 3.0 A형) 참고: USB은 최소 900mA를 제공해야 합니다.
Bluetooth | Bluetooth 4.0(액세서리 연결용)

## <a name="next-development-checkpoint"></a>다음 개발 검사점

이제 도구를 설치했으므로 MRTK HoloLens 2 자습서 시리즈를 따를 것을 권장합니다.
> [!div class="nextstepaction"]
> [HoloLens 2 자습서 시리즈](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)