---
title: Visual Studio를 사용하여 배포 및 디버깅
description: Visual Studio를 사용하여 HoloLens 및 Windows Mixed Reality용 앱을 빌드, 디버그 및 배포하는 방법을 알아봅니다.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, Mixed Reality, 디버그, 배포
ms.openlocfilehash: 43abf7b512d6b01695e2c953df821a608359918c461614e3f94710b57f241db0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221139"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Visual Studio를 사용하여 배포 및 디버깅

혼합 현실 앱을 개발할 때 DirectX와 Unity 중 무엇을 사용하든 관계없이 Visual Studio는 디버깅 및 배포에 적합한 도구입니다. 이 섹션에서는 다음을 수행하는 방법을 알아봅니다.
* Visual Studio를 통해 애플리케이션을 HoloLens 또는 Windows Mixed Reality 몰입형 헤드셋에 배포합니다.
* Visual Studio에 기본 제공된 HoloLens 에뮬레이터를 사용합니다.
* 혼합 현실 앱을 디버그합니다.

## <a name="prerequisites"></a>필수 구성 요소

1. 설치 지침은 [도구 설치](../../develop/install-the-tools.md#installation-checklist)를 참조하세요.
2. Visual Studio에서 새 유니버설 Windows 앱 프로젝트를 만듭니다.  HoloLens(1세대)의 경우 Visual Studio 2017 이상을 사용합니다.  HoloLens 2의 경우 Visual Studio 2019 16.2 이상을 사용합니다. C# 및 C++가 지원됩니다. (또는 지침에 따라 [Unity에서 앱을 만듭니다](../../develop/unity/tutorials/holograms-100.md).)

## <a name="enabling-developer-mode"></a>개발자 모드 사용

먼저 디바이스에서 **개발자 모드** 를 사용하도록 설정합니다. 그러면 Visual Studio에서 해당 디바이스에 연결할 수 있습니다.

### <a name="hololens"></a>HoloLens

1. HoloLens를 켜고 디바이스에 배치합니다.
2. [시작 제스처](../../design/system-gesture.md)를 사용하여 주 메뉴를 시작합니다.
3. **설정** 타일을 선택하여 환경에서 앱을 시작합니다.
4. **업데이트** 메뉴 항목을 선택합니다.
5. **개발자용** 메뉴 항목을 선택합니다.
6. **개발자 기능 사용** 을 사용하도록 설정하여 Visual Studio에서 HoloLens로 앱을 배포합니다. 디바이스에서 Windows Holographic 버전 21H1 이상을 실행하는 경우 **디바이스 검색** 도 사용하도록 설정합니다.
7. 옵션: 아래로 스크롤하고 **장치 포털** 도 사용하도록 설정하면 웹 브라우저에서 HoloLens의 [Windows 장치 포털](using-the-windows-device-portal.md)에 연결할 수 있습니다.

### <a name="windows-pc"></a>Windows PC

PC에 연결된 Windows Mixed Reality 헤드셋을 사용하는 경우 PC에서 **개발자 모드** 를 사용하도록 설정해야 합니다.
1. **설정** 으로 이동합니다.
2. **업데이트 및 보안** 을 선택합니다.
3. **개발자용** 을 선택합니다.
4. **개발자 모드** 를 사용하도록 설정하고, 선택한 설정에 대한 고지 사항을 읽은 다음, 예를 선택하여 변경 내용을 적용합니다.

## <a name="deploying-a-hololens-app-over-wi-fi"></a>Wi-Fi를 통해 HoloLens 앱 배포 

다음 속성을 사용하여 Visual Studio 프로젝트를 구성합니다.

1. 앱 컴파일 옵션 선택
    * Unity 프로젝트의 경우 **릴리스** 또는 **마스터** 를 선택합니다. 
    * 다른 모든 프로젝트의 경우 **릴리스** 를 선택합니다.

> [!NOTE]
> [Visual Studio 솔루션 내보내기 및 빌드](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)에서 각 컴파일 옵션에 대한 완전한 정의를 찾을 수 있습니다.

2. 디바이스에 따라 빌드 구성 선택

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. 배포 대상 드롭다운 메뉴에서 **원격 머신** 을 선택합니다.

![Visual Studio의 원격 머신 배포 대상](images/remotemachinesetting_arm64.png)

다음으로 원격 연결을 설정해야 합니다. C++ 및 JavaScript 프로젝트의 경우 **프로젝트 > 속성 > 구성 속성 > 디버깅** 으로 차례로 이동합니다. C# 프로젝트에서 작업하는 경우 대화 상자가 자동으로 나타납니다.

> [!NOTE]
> 원격 연결 대화 상자가 C# 프로젝트에 나타나지 않으면 **속성 > 디버그** 에서 수동으로 열 수 있습니다.

1. **주소** 또는 **머신 이름** 필드에서 디바이스의 IP 주소를 입력합니다. 
    * **설정 > 네트워크 및 인터넷 > 고급 옵션** 아래에서 HoloLens의 IP 주소를 찾을 수 있습니다.
    * 자동 감지 기능에 의존하지 않고 항상 수동으로 IP 주소를 입력하는 것이 좋습니다.

2. **인증 모드** 를 **유니버설(암호화되지 않은 프로토콜)** 로 설정

  ![Visual Studio의 원격 연결 대화 상자](images/remotedeploy.png)

3. 필요에 따라 앱 빌드, 배포 및 디버그
    * **디버그 > 디버깅 시작** 을 차례로 선택하여 앱을 배포하고, 디버깅을 시작합니다.
    * **빌드 > 배포** 를 선택하여 디버깅하지 않고 빌드 및 배포합니다.

![Visual Studio에서 디버깅 없이 시작](images/deploywithdebugging.png)

4. PC에서 앱을 HoloLens에 처음 배포하는 경우 PIN을 입력하라는 메시지가 표시됩니다. 아래의 **디바이스 페어링** 지침을 따릅니다.

## <a name="deploying-a-hololens-app-over-usb"></a>USB를 통해 HoloLens 앱 배포 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. 앱 컴파일 옵션 선택
    * Unity 프로젝트의 경우 **릴리스** 또는 **마스터** 를 선택합니다. 
    * 다른 모든 프로젝트의 경우 **릴리스** 를 선택합니다.

> [!NOTE]
> [Visual Studio 솔루션 내보내기 및 빌드](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)에서 각 컴파일 옵션에 대한 완전한 정의를 찾을 수 있습니다.

2. 디바이스에 따라 빌드 구성 선택

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. 배포 대상 드롭다운 메뉴에서 **디바이스** 를 선택합니다.

![Visual Studio에서 디바이스 배포](images/buildsettingsusbdeploy_arm64.png)

4. 필요에 따라 앱 빌드, 배포 및 디버그
    * **디버그 > 디버깅 시작** 을 차례로 선택하여 앱을 배포하고, 디버깅을 시작합니다.
    * **빌드 > 배포** 를 선택하여 디버깅하지 않고 빌드 및 배포합니다.

![Visual Studio에서 디버깅 없이 시작](images/deploywithdebugging.png)</br>

5. PC에서 앱을 HoloLens에 처음 배포하는 경우 PIN을 입력하라는 메시지가 표시됩니다. 아래의 **디바이스 페어링** 지침을 따릅니다.

> [!NOTE]
> USB를 통한 앱 배포에 상당한 지연 시간이 발생하는 경우 이전 섹션의 [원격 머신 지침](#deploying-a-hololens-app-over-wi-fi)를 사용하는 것이 좋습니다.

## <a name="deploying-an-app-to-the-hololens-emulator"></a>HoloLens 에뮬레이터에 앱 배포

1. **[HoloLens 2 또는 HoloLens(1세대) 에뮬레이터를 설치](../install-the-tools.md#installation-checklist)** 했는지 확인합니다.
2. 디바이스에 따라 빌드 구성 및 에뮬레이터 선택

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. 필요에 따라 앱 빌드, 배포 및 디버그
    * **디버그 > 디버깅 시작** 을 선택하여 앱을 배포하고 디버깅을 시작합니다.
    * **빌드 > 배포** 를 선택하여 디버깅하지 않고 빌드 및 배포합니다.

![Visual Studio에서 디버깅 없이 시작](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a>로컬 PC에 VR 앱 배포 

PC 또는 [Mixed Reality 시뮬레이터](using-the-windows-mixed-reality-simulator.md)에 연결되는 Windows Mixed Reality 몰입형 헤드셋을 사용하려면 다음을 수행합니다.
1. 앱에 대해 **x86** 또는 **x64** 빌드 구성을 선택합니다.
2. 배포 대상 드롭다운 메뉴에서 **로컬 머신** 을 선택합니다.
3. 필요에 따라 앱 빌드, 배포 및 디버그
    * **디버그 > 디버깅 시작** 을 차례로 선택하여 앱을 배포하고, 디버깅을 시작합니다.
    * **빌드 > 배포** 를 선택하여 디버깅하지 않고 빌드 및 배포합니다.

## <a name="pairing-your-device"></a>디바이스 페어링

앱을 Visual Studio에서 HoloLens로 처음 배포하는 경우 PIN을 입력하라는 메시지가 표시됩니다. HoloLens에서 설정 앱을 실행하여 PIN을 생성하고, **업데이트 > 개발자용** 으로 차례로 이동하여 **페어링** 을 탭합니다. HoloLens에 표시되는 PIN을 Visual Studio에 입력합니다. 페어링이 완료되면 HoloLens에서 **완료** 를 탭하여 대화 상자를 해제합니다. 이 PC는 이제 HoloLens와 페어링되어 앱을 자동으로 배포할 수 있습니다. 앱을 HoloLens에 배포하는 데 사용되는 모든 PC에 대해 이러한 단계를 반복하세요.

페어링된 모든 컴퓨터에서 HoloLens를 언페어링하려면 다음을 수행합니다.
* **설정** 앱을 시작하고, **업데이트 > 개발자용** 으로 이동하고, **지우기** 를 탭합니다.

## <a name="graphics-debugger-for-hololens-1st-gen"></a>HoloLens(1세대)용 그래픽 디버거

Visual Studio 그래픽 진단 도구는 홀로그램 앱을 작성하고 최적화하는 경우에 유용합니다. 자세한 내용은 [MSDN의 Visual Studio 그래픽 진단](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics)을 참조하세요.

**그래픽 디버거를 시작하려면**
1. 위의 지침에 따라 디바이스 또는 에뮬레이터를 대상으로 지정합니다.
2. **디버그 > 그래픽 > 진단 시작** 으로 차례로 이동합니다.
3. HoloLens를 사용하여 진단을 처음 시작하는 경우 "액세스 거부" 오류가 발생할 수 있습니다. 업데이트된 권한이 적용되도록 HoloLens를 다시 부팅하여 다시 시도하세요.

## <a name="profiling"></a>프로파일링

Visual Studio 프로파일링 도구를 사용하면 앱의 성능 및 리소스 사용을 분석할 수 있습니다. 여기에는 CPU, 메모리, 그래픽 및 네트워크 사용을 최적화하는 도구가 포함됩니다. 자세한 내용은 [MSDN의 디버깅하지 않고 진단 도구 실행](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools)을 참조하세요.

**HoloLens를 사용하여 프로파일링 도구를 시작하려면**
1. 위의 지침에 따라 디바이스 또는 에뮬레이터를 대상으로 지정합니다.
2. **디버그 > 디버깅하지 않고 진단 도구 시작...** 으로 차례로 이동합니다.
3. 사용하려는 도구를 선택합니다.
4. **시작** 을 선택합니다.
5. HoloLens를 사용하여 디버그 없이 진단을 처음 시작하는 경우 "액세스 거부" 오류가 발생할 수 있습니다. 업데이트된 권한이 적용되도록 HoloLens를 다시 부팅하여 다시 시도하세요.

## <a name="debugging-an-installed-or-running-app"></a>설치되었거나 실행 중인 앱 디버깅

Visual Studio를 사용하여 Visual Studio 프로젝트에서 배포하지 않고 설치된 유니버설 Windows 앱을 디버그할 수 있습니다. 이는 설치된 앱 패키지를 디버그하거나 이미 실행 중인 앱을 디버그하려는 경우에 유용합니다.
1. **디버그 -> 기타 디버그 대상 -> 설치된 앱 패키지 디버그** 로 차례로 이동합니다.
2. HoloLens의 경우 **원격 머신** 대상을 선택하고, 몰입형 헤드셋의 경우 **로컬 머신** 대상을 선택합니다.
3. 디바이스의 **IP 주소** 를 입력합니다.
4. **유니버설** 인증 모드를 선택합니다.
5. 창에 실행 중인 앱과 비활성 앱이 모두 표시됩니다. 디버그하려는 앱을 선택합니다.
6. 디버그할 코드 형식(관리, 네이티브, 혼합)을 선택합니다.
7. **연결** 또는 **시작** 을 선택합니다.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unity 개발 검사점 경험을 수행하는 경우 배포 단계를 진행하고 있는 것입니다. 여기에서 다음 항목으로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [HoloLens 에뮬레이터에 배포](using-the-hololens-emulator.md)

또는 고급 서비스 추가로 바로 이동합니다.

> [!div class="nextstepaction"]
> [고급 서비스](../../develop/unity/unity-development-overview.md#5-adding-services)

언제든지 [Unity 개발 검사점](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목
* [도구 설치](../install-the-tools.md)
* [HoloLens 에뮬레이터 사용](using-the-hololens-emulator.md)
* [UWP(유니버설 Windows 플랫폼) 앱 배포 및 디버깅](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [디바이스를 개발에 사용하도록 설정](/windows/uwp/get-started/enable-your-device-for-development)
