---
title: Unreal의 음성 입력
description: HoloLens 2 장치에 대 한 Unreal mixed reality 앱에서 음성 입력, 음성 매핑 및 인식을 설정 하 고 사용 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, Unreal, Unreal Engine 4, UE4, HoloLens 2, 음성, 음성 입력, 음성 인식, 혼합 현실, 개발, 기능, 설명서, 가이드, holograms, 게임 개발, 혼합 현실 헤드셋, windows Mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 466b41c522e95f9fe3d618ad221dde8ccd925634
ms.sourcegitcommit: a688bf0f1b796e4860f8252e852be79053937088
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205838"
---
# <a name="voice-input-in-unreal"></a>Unreal의 음성 입력

Unreal의 음성 입력을 사용 하면 핸드 제스처를 사용 하지 않고도 홀로그램과 상호 작용할 수 있으며 HoloLens 2만 지원 됩니다. HoloLens 2의 음성 입력은 다른 모든 유니버설 Windows 앱의 음성을 지 원하는 동일한 엔진에서 제공 되지만, Unreal은 더 제한적인 엔진을 사용 하 여 음성 입력을 처리 합니다. 이는 다음 섹션에서 설명 하는, Unreal의 음성 입력 기능을 미리 정의 된 음성 매핑으로 제한 합니다. 

## <a name="enabling-speech-recognition"></a>음성 인식 사용

Windows Mixed Reality 플러그 인을 사용 하는 경우 음성 입력에 특별 한 Windows Mixed Reality Api가 필요 하지 않습니다. 기존 Unreal Engine 4 [입력](https://docs.unrealengine.com/Gameplay/Input/index.html) 매핑 API를 기반으로 합니다. OpenXR를 사용 하는 경우 [Microsoft OpenXR 플러그 인](https://github.com/microsoft/Microsoft-OpenXR-Unreal)을 추가로 설치 해야 합니다. 

HoloLens에서 음성 인식을 사용 하도록 설정 하려면:
1. **프로젝트 설정 > 플랫폼 > HoloLens > 기능** 을 선택 하 고 **마이크** 를 사용 하도록 설정 합니다. 
2. 설정에서 음성 인식을 사용 하도록 설정 **> 개인 정보 > 음성** 을 선택 하 고 **영어** 를 선택 합니다.

> [!NOTE]
> 음성 인식은 항상 **설정** 앱에서 구성 된 Windows 표시 언어로 작동 합니다. 또한 최상의 서비스 품질을 위해 **온라인 음성 인식을** 사용 하도록 설정 하는 것이 좋습니다.

![Windows 음성 인식 설정](images/unreal/speech-recognition-settings.png)

3. 응용 프로그램에서 마이크를 사용 하도록 설정 하려는 경우 먼저 ask를 시작 하면 대화 상자가 표시 됩니다. **예** 를 선택 하면 앱에서 음성 입력이 시작 됩니다.

## <a name="adding-speech-mappings"></a>음성 매핑 추가

음성 입력을 사용 하는 경우 음성 작업을 작업에 연결 하는 것은 중요 한 단계입니다. 이러한 매핑은 사용자가 말할 수 있는 음성 키워드에 대해 앱을 모니터링 한 다음 연결 된 작업을 실행 합니다. 다음과 같은 방법으로 음성 매핑을 찾을 수 있습니다.
1. **편집 > 프로젝트 설정** 을 선택 하 고 **엔진** 섹션으로 스크롤한 다음 **입력** 을 클릭 합니다.

점프 명령에 대 한 새 음성 매핑을 추가 하려면:
1. **+** **배열 요소** 옆의 아이콘을 선택 하 고 다음 값을 입력 합니다.
    * **작업 이름** 에 대 한 **jumpWord**
    * **Speech 키워드** 에 대 한 **점프**

> [!NOTE]
> 모든 영어 단어 또는 짧은 문장을 키워드로 사용할 수 있습니다. 

![UE4 엔진 입력 설정](images/unreal/engine-input.png)

음성 매핑은 작업 또는 축 매핑과 같은 입력 구성 요소나 이벤트 그래프의 청사진 노드로 사용할 수 있습니다. 예를 들어, 단어를 음성으로 연결 하는 경우에 따라 두 개의 다른 로그를 출력 하도록 점프 명령을 연결할 수 있습니다.

1. 청사진을 두 번 클릭 하 여 **이벤트 그래프** 에서 엽니다.
2. **마우스 오른쪽 단추를 클릭** 하 고 음성 매핑의 **작업 이름** (이 경우 **jumpWord**)을 검색 한 다음 **Enter 키** 를 눌러 그래프에 **입력 동작** 노드를 추가 합니다.
3. 아래 이미지에 나와 있는 것 처럼 **누름** 핀을 끌어 **문자열 노드에 인쇄** 합니다. **릴리스된** pin은 비워 둘 수 있으며, 음성 매핑에 대해서는 아무 것도 실행 되지 않습니다.
 
![음성에 대 한 간단한 작업](images/unreal/voice-input-img-03.png)

4. 앱을 재생 하 고, **이동** 이라는 단어를 표시 하 고, 콘솔에서 로그를 출력 합니다.

모든 설정에 따라 HoloLens 앱에 음성 입력을 추가 하기 시작 해야 합니다. 아래 링크에서 음성 및 상호 작용에 대 한 자세한 내용을 확인 하 고 사용자를 위해 만드는 환경에 대해 생각해 볼 수 있습니다.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 실제 개발 경험을 수행 하는 경우 다음 작업은 혼합 현실 플랫폼 기능과 Api를 탐색 하는 것입니다. 

> [!div class="nextstepaction"]
> [HoloLens 카메라](unreal-hololens-camera.md)

언제든지 [Unreal 개발 검사점](unreal-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목
* [음성 입력](../../design/voice-input.md)
* [응시 및 커밋](../../design/gaze-and-commit.md)
* [Instinctual 상호 작용](../../design/interaction-fundamentals.md)

