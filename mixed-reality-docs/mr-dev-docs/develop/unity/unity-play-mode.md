---
title: 홀로그램 원격으로 작업 미리 보기
description: 재생 모드에서 Holographic 원격을 사용 하 여 앱을 배포 하지 않고 장치에서 응용 프로그램 변경 내용을 미리 봅니다.
author: keveleigh
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: unity, remoting, holographic remoting, holographic remoting player, HoloLens, mixed reality 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity 재생 모드
ms.openlocfilehash: cd9dca9d1ddf17b78e8c317fa3a58093c9b5837de379510148c6e645b31120ca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226235"
---
# <a name="preview-your-work-with-holographic-remoting"></a>홀로그램 원격으로 작업 미리 보기

Holographic 원격을 사용 하 여 실시간으로 HoloLens 2 Holographic 콘텐츠를 스트리밍할 수 있습니다. 이 방법은 전체 프로젝트를 빌드하고 배포 하지 않고도 신속 하 게 앱을 디버그할 수 있는 좋은 방법입니다. 

Unity 프로젝트에서 작업 하는 빠른 방법은 PC의 Unity 편집기에서 로컬로 앱을 실행 하는 "재생 모드"를 사용 하는 것입니다. Unity는 Holographic 원격을 사용 하 여 실제 HoloLens 장치에서 콘텐츠를 빠르게 미리 볼 수 있도록 합니다. 재생 모드는 개발 PC에 연결 된 Windows Mixed Reality 헤드셋에도 사용할 수 있습니다.

## <a name="holographic-remoting-setup"></a>Holographic 원격 설치

1. 먼저 HoloLens 2 Microsoft Store에서 [Holographic Remoting Player 앱을 설치](https://www.microsoft.com/store/productId/9NBLGGH4SV40) 해야 합니다.
2. HoloLens 2에서 Holographic Remoting Player 앱을 실행 하면 연결할 버전 번호와 IP 주소가 표시 됩니다.
    * OpenXR 플러그 인을 사용 하려면 v 2.4 이상이 필요 합니다.

    ![HoloLens에서 실행 되는 Holographic 원격 플레이어의 스크린샷](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>Holographic 원격을 사용 하는 Unity 재생 모드

Holographic Remoting을 사용 하면 PC의 Unity 편집기에서 실행 되는 동안 HoloLens에서 앱을 경험할 수 있습니다. 응시, 제스처, 음성 및 공간 매핑 입력은 HoloLens에서 PC로 전송 됩니다. 렌더링 된 프레임은 HoloLens으로 다시 전송 됩니다. 이 방법은 전체 프로젝트를 빌드하고 배포 하지 않고도 신속 하 게 앱을 디버그할 수 있는 좋은 방법입니다.

[!INCLUDE[](includes/unity-play-mode.md)]

Holographic Remoting을 사용 하려면 고속 PC와 Wi-Fi 연결이 필요 합니다. 자세한 내용은 [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) 설명서에서 확인할 수 있습니다.

최상의 결과를 위해 앱이 [포커스 지점을](focus-point-in-unity.md)적절히 설정 하는지 확인 합니다. 이렇게 하면 Holographic는 무선 연결의 대기 시간에 맞게 장면을 최적으로 조정 하는 데 도움이 됩니다.

## <a name="see-also"></a>참고 항목

* [홀로그램 원격 플레이어](../platform-capabilities-and-apis/holographic-remoting-player.md)
