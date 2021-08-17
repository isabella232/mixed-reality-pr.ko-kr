---
title: 홀로그램 Remoting 및 재생 모드를 통해 앱 미리 보기 및 디버그
description: 홀로그램 Remoting 및 재생 모드를 사용하여 앱 미리 보기 및 디버그
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 증강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작, 홀로그램 원격, 데스크톱, 미리 보기, 디버그
ms.openlocfilehash: fe15d55037f09c47fe1e8a1dd996d0c69480f7b2
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203847"
---
# <a name="preview-and-debug-your-app-using-holographic-remoting-and-play-mode"></a>홀로그램 Remoting 및 재생 모드를 사용하여 앱 미리 보기 및 디버그

이 문서에서는 홀로그램 Remoting에 대한 다음 사용 사례를 설명합니다. 

- **개발 프로세스 중에 앱을 미리 보고 디버그하려고** 합니다. 재생 모드에서 PC의 Unity 편집기에서 로컬로 앱을 실행하고 환경을 HoloLens 스트리밍할 수 있습니다. 이렇게 하면 전체 프로젝트를 빌드하고 배포하지 않고도 앱을 신속하게 디버그할 수 있습니다. 이 유형의 앱을 _홀로그램 Remoting 재생 모드 미리 보기 앱이라고_ 합니다. HoloLens 입력(응시, 제스처, 음성 및 공간 매핑)은 PC로 전송되며, 여기서 콘텐츠는 가상 몰입형 보기로 렌더링됩니다. 그러면 렌더링된 프레임이 HoloLens 전송됩니다. 

홀로그램 Remoting에 대한 자세한 내용은 [홀로그램 Remoting 개요를 참조하세요.](../platform-capabilities-and-apis/holographic-remoting-overview.md)

PC의 리소스가 HoloLens 온보드 리소스에 의존하는 대신 앱에 [전원을 공급하려는](use-pc-resources.md) 경우에도 Holographic Remoting을 사용할 수 있습니다.

## <a name="set-up-holographic-remoting"></a>홀로그램 Remoting 설정

홀로그램 Remoting을 사용하려면 HoloLens Microsoft Store [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) 앱을 설치해야 합니다. 아래에 설명된 대로 앱을 다운로드하고 실행하면 연결할 버전 번호와 IP 주소가 표시됩니다. **OpenXR 플러그 인 을 사용하려면 v2.4 이상 이 필요합니다.**

홀로그램 Remoting에는 빠른 PC 및 Wi-Fi 연결이 필요합니다. 자세한 내용은 위에 링크된 홀로그램 Remoting Player 문서에서 찾을 수 있습니다.

![HoloLens 실행 중인 홀로그램 Remoting Player의 스크린샷](images/openxr-features-img-01.png)

[!INCLUDE[](includes/unity-play-mode.md)]

## <a name="see-also"></a>참고 항목
* [홀로그램 원격 플레이어](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [자습서: PC 홀로그램 Remoting 시작](tutorials/mr-learning-pc-holographic-remoting-01.md)
* [자습서: 홀로그램 Remoting PC 애플리케이션 만들기](tutorials/mr-learning-pc-holographic-remoting-02.md)
