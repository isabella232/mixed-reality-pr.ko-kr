---
title: Holographic 원격 기능 개요
description: Holographic Remoting이 무엇 인지와 개발 프로세스에 어떤 도움이 될 수 있는지에 대해 알아봅니다.
author: hferrone
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, mrtk, mixed reality Toolkit, 확대 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작, holographic 원격, 데스크톱, 미리 보기
ms.openlocfilehash: 52b69f942797b1f0a6a9bcc5276a49d4d2cebba5
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184604"
---
# <a name="holographic-remoting-overview"></a>Holographic 원격 기능 개요

Holographic 원격을 사용 하 여 실시간으로 HoloLens Holographic 콘텐츠를 스트리밍할 수 있습니다. 이에 대 한 두 가지 주요 용도와 차이점을 이해 하는 것이 중요 합니다.

1. (Unity 또는 Unreal): **개발 프로세스 중에 앱을 미리 보고 디버그할** 수 있습니다. 앱을 재생 모드에서 PC의 Unity 편집기에서 로컬로 실행 하 고 HoloLens 환경을 스트리밍할 수 있습니다. 이렇게 하면 전체 프로젝트를 빌드하고 배포 하지 않고도 앱을 신속 하 게 디버그할 수 있습니다. 이 유형의 앱을 _Holographic Remoting Play Mode Preview 앱_ 이라고 합니다.

    - [Unity에서 앱 미리 보기 및 디버깅에 대 한 자세한 정보](../unity/preview-and-debug-your-app.md)

    - [Unreal에서 앱 미리 보기 및 디버그에 대해 자세히 알아보기](../unreal/unreal-streaming.md)

1. (Unity, unreal 또는 c + +): **HoloLens 온보드 리소스를 활용 하는 대신 PC의 리소스가 앱을 구동 하도록 하려는 경우**: Holographic 원격 기능을 포함 하는 앱을 만들고 빌드할 수 있습니다. 사용자가 HoloLens에서 앱을 실행 하지만 앱이 실제로 pc에서 실행 되므로 pc에서 더 강력한 리소스를 활용할 수 있습니다. 앱에 고해상도 자산 또는 모델이 있고 프레임 율이 저하 되지 않도록 하려는 경우에 특히 유용할 수 있습니다. 이 유형의 앱을 _Holographic Remoting 원격 앱_ 이라고 합니다.

    - [Unity에서 PC 리소스를 사용 하는 방법에 대 한 자세한 정보](../unity/use-pc-resources.md)

    - [실시간에서 PC 리소스 사용에 대 한 자세한 정보](../unreal/unreal-streaming.md)

    - [Windows Mixed Reality api를 사용 하 여 Holographic Remoting 원격 앱 작성 (c + +)](holographic-remoting-create-remote-wmr.md)

    - [OpenXR Api를 사용 하 여 Holographic Remoting 원격 앱 작성 (c + +)](holographic-remoting-create-remote-openxr.md)

두 경우 모두 HoloLens (응시, 제스처, 음성 및 공간 매핑)의 입력이 PC로 전송 되 고 콘텐츠는 가상 몰입 형 보기에서 렌더링 된 다음 렌더링 된 프레임이 HoloLens 전송 됩니다. 

## <a name="see-also"></a>참고 항목

* [홀로그램 원격 플레이어](holographic-remoting-player.md)
* [자습서: PC Holographic 원격 작업 시작](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [자습서: Holographic Remoting PC 응용 프로그램 만들기](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
