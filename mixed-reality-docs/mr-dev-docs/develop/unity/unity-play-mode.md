---
title: Unity 플레이 모드
description: Unity 편집기에서 재생 모드를 사용하여 앱을 배포하지 않고 디바이스에서 애플리케이션 변경 내용을 미리 보는 방법을 알아봅니다.
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Remoting, 홀로그램 Remoting, 홀로그램 Remoting 플레이어, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, Unity 재생 모드
ms.openlocfilehash: 35f80b0c217adfd5c5d14799dc882d5c504925aa
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333424"
---
# <a name="unity-play-mode"></a>Unity 플레이 모드

Unity 프로젝트에서 작업하는 빠른 방법은 PC의 Unity 편집기에서 로컬로 앱을 실행하는 "재생 모드"를 사용하는 것입니다. Unity는 Holographic Remoting을 사용하여 실제 HoloLens 디바이스에서 콘텐츠를 미리 볼 수 있는 빠른 방법을 제공합니다. 재생 모드는 개발 PC에 연결된 Windows Mixed Reality 헤드셋과 함께 사용할 수도 있습니다.

## <a name="holographic-remoting-setup"></a>홀로그램 Remoting 설정

1. 먼저 HoloLens 2 Microsoft Store [Holographic Remoting Player 앱을 설치해야](https://www.microsoft.com/store/productId/9NBLGGH4SV40) 합니다.
2. HoloLens 2 Holographic Remoting Player 앱을 실행하면 연결할 버전 번호 및 IP 주소가 표시됩니다.
    * OpenXR 플러그 인을 사용하려면 v2.4 이상

    ![HoloLens에서 실행 중인 홀로그램 Remoting Player의 스크린샷](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Unity 편집기 재생 모드의 홀로그램 Remoting

Visual Studio 프로젝트에서 UWP Unity 프로젝트를 빌드한 다음 HoloLens 2 디바이스에 패키징하고 배포하는 데 시간이 걸릴 수 있습니다. 한 가지 해결 방법은 홀로그램 편집기 Remoting 기능을 사용하도록 설정하여 "재생" 모드를 사용하여 C# 스크립트를 네트워크를 통해 HoloLens 2 디바이스로 직접 디버그할 수 있도록 하는 것입니다. 이 시나리오에서는 UWP 패키지를 빌드하고 원격 디바이스에 배포하는 오버헤드를 방지합니다.

1. [홀로그램 Remoting 설정의](#holographic-remoting-setup) 단계를 수행합니다.
2. **OpenXR Editor Remoting을 > Windows > XR을 엽니다.**

    ![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-02.png)

3. 홀로그램 Remoting 앱에서 얻는 IP 주소를 입력하고 **편집기 Remoting 사용을** 선택합니다.

    ![기능이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-03.png)

이제 "재생" 단추를 클릭하여 HoloLens의 Holographic Remoting 앱에서 Unity 앱을 재생할 수 있습니다. [Visual Studio를 Unity에 연결](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) 하 여 재생 모드에서 c # 스크립트를 디버그할 수도 있습니다.

> [!NOTE]
> 버전 0.1.0에서 Holographic Remoting 런타임은 앵커를 지원 하지 않으며 ARAnchorManager 기능은 원격 작업을 통해 작동 하지 않습니다.  이 기능은 이후 릴리스에서 제공 될 예정입니다.

## <a name="unity-play-mode-with-holographic-remoting"></a>Holographic 원격을 사용 하는 Unity 재생 모드

Holographic Remoting을 사용 하면 PC의 Unity 편집기에서 실행 되는 동안 HoloLens에서 앱을 경험해 볼 수 있습니다. 응시, 제스처, 음성 및 공간 매핑 입력은 HoloLens에서 PC로 전송 됩니다. 그러면 렌더링 된 프레임이 HoloLens로 다시 전송 됩니다. 이 방법은 전체 프로젝트를 빌드하고 배포 하지 않고도 신속 하 게 앱을 디버그할 수 있는 좋은 방법입니다.
1. HoloLens에서 **Microsoft Store** 로 이동 하 여 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 앱을 설치 합니다.
2. HoloLens에서 **Holographic Remoting Player** 앱을 시작 합니다.
3. Unity에서 **창** 메뉴로 이동 하 여 **XR** 하위 메뉴를 확장 하 고 **Holographic 에뮬레이션** 을 선택 합니다.
4. **에뮬레이션 모드** 를 **원격에서 장치로** 설정 합니다.
5. **원격 컴퓨터** 의 경우 HOLOLENS의 IP 주소를 입력 합니다.
6. **연결** 을 선택합니다. **연결 상태가** **연결 됨** 으로 변경 되 고 HoloLens에서 화면이 비어 있는 것을 볼 수 있습니다.
7. 재생 모드를 시작 하 고 HoloLens에서 앱을 경험 하려면 **재생** 단추를 선택 합니다.

Holographic Remoting을 사용 하려면 고속 PC와 Wi-Fi 연결이 필요 합니다. 자세한 내용은 [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) 설명서에서 확인할 수 있습니다.

최상의 결과를 위해 앱이 [포커스 지점을](focus-point-in-unity.md)적절히 설정 하는지 확인 합니다. 이렇게 하면 Holographic는 무선 연결의 대기 시간에 맞게 장면을 최적으로 조정 하는 데 도움이 됩니다.

## <a name="see-also"></a>참고 항목
* [홀로그램 원격 플레이어](../platform-capabilities-and-apis/holographic-remoting-player.md)
