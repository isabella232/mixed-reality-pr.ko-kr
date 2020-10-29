---
title: Unreal에서 입력 응시
description: HoloLens 및 Unreal Engine에 대 한 응시 입력 설정 자습서
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, HoloLens 2, 눈 추적, 응시 입력, 헤드 탑재 된 디스플레이, Unreal engine
ms.openlocfilehash: 477fbdc9c7ddb3b4e890e62150651d9227d4c19e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684857"
---
# <a name="gaze-input"></a>응시 입력

## <a name="overview"></a>개요

[Windows Mixed Reality 플러그인](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) 은 응시 입력을 위한 기본 제공 함수를 제공 하지 않지만 HoloLens 2는 눈 추적을 지원 합니다. 실제 추적 기능은 Unreal의 **탑재 된 표시** 및 **눈 추적** api에서 제공 하며 다음을 포함 합니다.

- 디바이스 정보
- 추적 센서
- 방향 및 위치
- 창 클리핑
- 데이터 및 추적 정보를 응시 합니다.

모든 기능의 전체 목록은 실제 [헤드 탑재 된 표시](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) 및 [눈 추적](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) 설명서에서 확인할 수 있습니다.

Unreal Api 외에도 HoloLens 2에 대 한 눈에 잘 맞는 [상호 작용](../../design/eye-gaze-interaction.md) 에 대 한 설명서를 확인 하 고 [hololens 2의 눈 추적](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) 작동 방식을 확인 하세요.

> [!IMPORTANT]
> 아이 추적은 HoloLens 2 에서만 지원 됩니다.

## <a name="enabling-eye-tracking"></a>눈 추적 사용
Unreal의 Api를 사용 하려면 먼저 HoloLens 프로젝트 설정에서 응시 입력을 사용 하도록 설정 해야 합니다. 응용 프로그램이 시작 되 면 아래 스크린샷에 표시 된 동의 프롬프트가 표시 됩니다.

- **예** 를 선택 하 여 사용 권한을 설정 하 고 입력에 대 한 액세스 권한을 얻습니다. 언제 든 지이 설정을 변경 해야 하는 경우 **설정** 앱에서 찾을 수 있습니다.

![눈 입력 권한](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> Unreal의 HoloLens 눈동자 추적에는 stereoscopic 추적에 필요한 두 광선 (지원 되지 않음)이 아닌 단일 응시 광선이 있습니다.

이를 통해 모든 설정에서 HoloLens 2 앱에 응시 입력을 Unreal에 추가 하기 시작 해야 합니다. 입력 응시에 대 한 자세한 내용 및 혼합 현실의 사용자에 게 영향을 주는 방법에 대 한 자세한 내용은 아래 링크를 참조 하세요. 대화형 환경을 구축할 때이에 대해 생각해 야 합니다.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 실제 개발 검사점 경험을 수행 하는 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다. 여기에서 다음 구성 요소를 진행할 수 있습니다. 

> [!div class="nextstepaction"]
> [손 추적](unreal-hand-tracking.md)

또는 혼합 현실 플랫폼 기능 및 Api로 이동 합니다.

> [!div class="nextstepaction"]
> [HoloLens 카메라](unreal-hololens-camera.md)

언제 든 지 [실제 개발 검사점](unreal-development-overview.md#2-core-building-blocks) 으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참조
* [조정](../../calibration.md)
* [편안함](../../design/comfort.md)
* [응시 및 커밋](../../design/gaze-and-commit.md)
* [음성 입력 ](../../out-of-scope/voice-design.md)
