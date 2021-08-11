---
title: 홀로그램 Remoting 개요
description: 홀로그램 Remoting이 무엇이며 개발 프로세스에 어떤 도움이 될 수 있는지 알아봅니다.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 증강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작, 홀로그램 원격, 데스크톱, 미리 보기
ms.openlocfilehash: 1b20590429b7df209e805ed8e94de5a6010bdbb609edc10fc5854cd4df86f64c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217119"
---
# <a name="holographic-remoting-overview"></a>홀로그램 Remoting 개요

홀로그램 렌더링에 대한 지원을 PC 앱 또는 게임에 추가하면 앱에서 홀로그램 콘텐츠를 실시간으로 HoloLens 2 스트리밍할 수 있습니다. 전체 프로젝트를 빌드하고 배포하지 않고도 앱을 신속하게 디버그할 수 있는 좋은 방법입니다. 응시, 제스처, 음성 및 공간 매핑 입력은 HoloLens 2 PC로 전송되고, 콘텐츠는 PC의 더 큰 시스템 리소스를 사용하여 가상 몰입형 보기로 렌더링되고, 렌더링된 프레임은 HoloLens 2 다시 전송됩니다. 홀로그램 Remoting은 Windows Mixed Reality 몰입형 헤드셋에도 사용할 수 있습니다.

NuGet 패키지를 통해 데스크톱 또는 UWP 앱에 홀로그램 원격을 추가하고 표준 Wi-Fi를 사용하여 연결합니다. 연결을 처리하고 몰입형 보기에서 렌더링하는 추가 코드가 필요합니다. 일반적인 Remoting 연결의 대기 시간이 50ms입니다. 디바이스는 실시간으로 대기 시간을 보고할 수 있는 "플레이어" 앱을 사용하여 스트리밍된 콘텐츠를 표시합니다.

Unity 개발자인 경우 재생 모드의 Unity 편집기에서 앱을 실행하여 홀로그램 Remoting을 사용할 수도 있습니다.

## <a name="see-also"></a>참고 항목
* [홀로그램 원격 플레이어](holographic-remoting-player.md)
* [Windows Mixed Reality API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-wmr.md)
* [OpenXR API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-openxr.md)
* [자습서: PC 홀로그램 Remoting 시작](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [자습서: 홀로그램 Remoting PC 애플리케이션 만들기](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
