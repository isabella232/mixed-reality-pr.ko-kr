---
title: 홀로그램 원격 접속
description: 문서 홀로그램 Remoting MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 196bbb7027389ea75ddc577e4efc397ca779d550
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647178"
---
# <a name="holographic-remoting"></a>홀로그램 원격 접속

홀로그램 Remoting은 Wi-Fi 또는 USB 케이블 연결을 사용하여 PC에서 Microsoft HoloLens 홀로그램 콘텐츠를 실시간으로 스트림합니다. 이 기능은 혼합 현실 애플리케이션을 개발할 때 개발자 생산성을 크게 높일 수 있습니다.

아래에 언급된 XR SDK는 Unity [2019.3 이상에서 Unity의 새 XR 파이프라인을](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)나타냅니다. MRTK와 함께 XR SDK를 사용하는 방법은 [여기를](../../configuration/getting-started-with-mrtk-and-xrsdk.md) 참조하세요. 레거시 XR은 Unity 2018에 포함되고 Unity 2019.3에서 더 이상 사용되지 않고 Unity 2020에서 제거된 기존 XR 파이프라인을 나타냅니다.

## <a name="initial-setup"></a>초기 설정

HoloLens에 대한 Remoting을 사용하도록 설정하려면 프로젝트에서 최신 Remoting 구성 요소를 사용하고 있는지 확인해야 합니다.

1. **창 열기 > 패키지 관리자**
    - 레거시 XR을 사용하는 경우: 최신 버전의 **Windows Mixed Reality** 패키지가 설치되어 있는지 확인합니다.
    - XR SDK를 사용하는 경우: 최신 버전의 **Windows XR 플러그 인** 패키지가 설치되어 있는지 확인합니다.
1. Microsoft Store 통해 HoloLens에 최신 Holographic Remoting 애플리케이션이 설치되어 있는지 확인합니다.

프로젝트에서 사용되는 파이프라인에 따라 [레거시 XR 설치 지침](#legacy-xr-setup-instructions) 또는 [XR SDK 설치 지침을](#xr-sdk-setup-instructions) 계속 진행하세요.

## <a name="legacy-xr-setup-instructions"></a>레거시 XR 설치 지침

아래 지침은 HoloLens 2 있는 remoting에만 적용됩니다. HoloLens(1세대)에서만 Remoting을 수행하는 경우 [Wi-Fi를 사용하여 HoloLens에 연결로](#connecting-to-the-hololens-with-wi-fi)건너뜁니다.

HoloLens 2 사용하는 경우 MRTK에 remoting에 대한 설명된 손 및 시선 추적 데이터에 대한 지원이 추가되었습니다. 이러한 기능을 사용하도록 설정하려면 [DotNetWinRT를 프로젝트로 가져오기에](#import-dotnetwinrt-into-the-project)설명된 단계를 따르세요.

가져온 후 다음 단계는 Mixed Reality   >  **도구 키트** 유틸리티 Windows Mixed Reality 구성 확인을 선택하는  >    >    >  것입니다. 이 단계에서는 DotNetWinRT 종속성을 사용하도록 설정하는 스크립팅 정의를 추가합니다.

> [!NOTE]
> Unity 2019.4 이상에서는 Check Configuration 유틸리티를 실행할 필요가 없습니다.

손 조인트 및 시선 추적 추적을 사용하도록 설정하려면 Unity 패키지 가져오기 및 관련 **섹션을 통해 HoloLens 2 Remoting 디버깅의** 단계를 따릅니다.

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>Unity 패키지 가져오기를 통해 HoloLens 2 Remoting 디버깅

HoloLens 2 손 조인트와 시선 추적이 remoting을 통해 작동하지 않는 경우 몇 가지 일반적인 문제가 있습니다. 검사해야 하는 순서대로 아래에 나열되어 있습니다.

이러한 문제는 **Unity 2019.3** 이상에서 실행할 때 특히 관련이 있습니다.

#### <a name="import-dotnetwinrt-into-the-project"></a>DotNetWinRT를 프로젝트로 가져오기

1. Mixed Reality [기능 도구](https://aka.ms/MRFeatureTool) 다운로드

1. 기능 **검색** 보기에서 *winRT 프로젝션 Mixed Reality 선택합니다.*

    ![DotNetWinRT 패키지 선택](../images/tools/remoting/SelectDotNetWinRT.png)

1. **기능 가져오기를** 클릭하고 패키지를 계속 [가져옵니다.](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages)

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>플레이어 설정에 기록된 DOTNETWINRT_PRESENT 정의

> [!NOTE]
> Unity 2019.4 이상에서 사용하는 경우 DOTNETWINRT_PRESENT 정의는 Unity 플레이어 설정이 아닌 적절한 .asmdef 파일 내에 포함됩니다. 구성 확인 단계는 필요하지 않습니다.

MRTK 버전 2.5.0부터는 성능상의 이유로 이 #define 더 이상 자동으로 설정되지 않습니다. 이 플래그를 사용하려면 **Mixed Reality 도구 키트**  >  **유틸리티** Windows Mixed Reality 구성 확인 메뉴  >  항목을  >   사용하세요.

> [!Note]
> 구성 확인 항목에 확인이 표시되지 않습니다. 정의가 설정되었는지 확인하려면 Unity 플레이어 설정으로 이동하세요. 해당 위치에서 UWP 탭 아래의 다른 설정에서 스크립팅 기호 정의를 확인합니다. DOTNETWINRT_PRESENT 해당 목록에 올바르게 작성되었는지 확인합니다. 이 경우 이 단계가 성공했습니다.

![DotNetWinRT 현재](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a>HoloLens 2 특정 Remoting 지원 제거

DotNetWinRT 어댑터의 존재로 인해 충돌 또는 기타 문제가 발생하면 [도움말 리소스 중 하나에 문의하세요.](../../index.md#getting-help)

## <a name="xr-sdk-setup-instructions"></a>XR SDK 설정 지침

[MRTK 및 XR SDK 시작 페이지의 Windows Mixed Reality 설정 지침을](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) 따르고 편집기에서 HoloLens Remoting에 필요한 단계를 수행해야 합니다.

## <a name="connecting-to-the-hololens-with-wi-fi"></a>Wi-Fi 사용하여 HoloLens에 연결

프로젝트가 구성되면 HoloLens에 대한 연결을 설정할 수 있습니다.

1. **파일 > 빌드 설정** 에서 프로젝트 빌드 형식이 **유니버설 Windows 플랫폼**
1. HoloLens에서 **홀로그램 Remoting 애플리케이션을** 시작합니다.
1. Unity에서 **Windows > XR > Holographic Emulation(레거시 XR을 사용하는 경우) /Windows XR 플러그 인 Remoting(XR SDK를 사용하는 경우)을** 선택합니다.

    ![홀로그램 에뮬레이션 시작](../images/tools/remoting/StartHolographicEmulation.png)

1. **에뮬레이션 모드를** **원격으로 디바이스 로** 설정합니다.

    ![에뮬레이션 모드 설정](../images/tools/remoting/SelectEmulationMode.png)

1. (**_레거시 XR에만 적용)_** 디바이스 **버전** 을 선택합니다.

    ![디바이스 버전 선택](../images/tools/remoting/SelectDeviceVersion.png)

1. 홀로그램 원격 플레이어 애플리케이션에서 표시하는 IP 주소를 사용하여 **원격 머신** 필드를 설정합니다.

    ![IP 주소 입력](../images/tools/remoting/EnterIPAddress.png)

1. **연결** 을 클릭합니다.

> [!NOTE]
> 연결할 수 없는 경우 HoloLens 2 PC에 연결되어 있지 않은지 확인하고 Unity를 다시 시작합니다.

## <a name="connecting-to-the-hololens-with-usb-cable"></a>USB 케이블을 사용하여 HoloLens에 연결

USB 케이블 연결을 통해 렌더링 품질과 안정성이 향상됩니다. USB 케이블 연결을 사용하려면 HoloLens 설정의 Wi-Fi HoloLens에서 연결을 끊고 홀로그램 Remoting Player 앱을 시작합니다. 169로 시작하는 IP 주소가 표시됩니다. Unity의 홀로그램 에뮬레이션 설정에서 이 IP 주소를 사용하여 연결합니다. USB 케이블의 IP 주소가 식별되면 HoloLens를 다시 Wi-Fi 연결해도 안전합니다.

## <a name="starting-a-remoting-session"></a>Remoting 세션 시작

Unity가 HoloLens에 연결된 경우 편집기에서 재생 모드를 입력합니다.

세션이 완료되면 재생 모드를 종료합니다.

> [!NOTE]
> 일부 Unity 버전에서는 Remoting 세션 중에 편집기가 재생 모드로 들어가면 중단되는 알려진 문제가 있습니다. 프로젝트가 로드될 때 홀로그램 창이 열려 있으면 이 문제가 발생할 수 있습니다. 이 문제가 발생하지 않도록 하려면 Unity를 종료하기 전에 항상 홀로그램 대화 상자를 닫습니다.

## <a name="see-also"></a>참조

- [홀로그램 Remoting 문제 해결 및 제한 사항](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Microsoft Holographic Remoting 소프트웨어 사용 조건](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)