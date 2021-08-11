---
title: 시선 응시 및 유지(dwell)
description: 상호 작용 모델, 설계 지침 및 고유한 과제를 포함하여 시선 응시 및 유지(dwell) 입력 모델에 대한 개요를 시작합니다.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
ms.localizationpriority: high
keywords: 시선 추적, Mixed Reality, 입력, 시선 응시, 시선 타깃팅, HoloLens 2, 시선 기반 선택, 유지, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 디자인
ms.openlocfilehash: dfe74ee1fe304cc63bb0c547d01ebadeb0469b171caa806671887817c17f92ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201838"
---
# <a name="eye-gaze-and-dwell"></a>시선 응시 및 유지(dwell)

_"시선 응시 및 유지"_ 상호 작용 모델은 [시선 응시 및 커밋](gaze-and-commit.md) 상호 작용 모델의 특별한 경우입니다.
1. 대상을 확인합니다. 
2. 대상을 선택하려는 의도를 확인하기 위해 명시적인 보조 입력을 사용합니다. 선택하려는 대상을 계속 보기만 하면 됩니다.

## <a name="advantages-of-the-eye-gaze-and-dwell-interaction-model"></a>"시선 응시 및 유지" 상호 작용 모델의 장점 

손으로 작업 중이나 도구를 잡고 있으면 홀로그램과 상호 작용하는 데 손을 사용하지 못할 수 있습니다.
"시선 응시 및 유지" 또는 다른 말로 : _"바라보기(look and stare)"_ 는 홀로그램을 선택할 수 있는 핸즈프리 상호 작용 대안입니다. 이 방법을 사용하면 머리 또는 몸을 완전히 돌릴 수 없는 매우 제한된 사용자(예: 매우 제한된 작업 환경에 있음)도 홀로그램과 상호 작용할 수 있습니다.
사용자가 선택하고 싶은 대상을 계속 보기만 하면 프로세스를 나타내는 다른 유지(dwell) 피드백이 표시됩니다.

## <a name="challenges-of-the-eye-gaze-and-dwell-interaction-model"></a>"시선 응시 및 유지" 상호 작용 모델의 과제

일반적으로 유지(dwell) 기반 활성화는 음성 입력이나 손 입력을 모두 사용할 수 없는 경우에만 마지막 대체 수단으로 사용하는 것이 좋습니다. 이는 유지(dwell) 시간을 선택하는 것이 어려울 수 있기 때문입니다. 초보 사용자의 경우 유지(dwell) 시간이 길어도 괜찮지만 숙련된 사용자는 자신의 환경을 빠르고 효율적으로 탐색하려고 합니다. 따라서 유지(dwell) 시간을 사용자의 특정 요구에 맞게 조정하는 방법이 어려운 과제입니다.
유지(dwell) 시간이 너무 짧으면: 홀로그램이 항상 사용자의 시선 응시에 반응하기 때문에 사용자가 압도감을 느낄 수 있습니다. 유지(dwell) 시간이 너무 길면: 사용자가 대상을 오랫동안 계속보고 있어야 해서 환경이 너무 느리고 방해가 될 수 있습니다.

## <a name="design-recommendations"></a>디자인 권장 사항

유지(dwell) 피드백에 두 가지 상태 접근 방식을 사용하는 것이 좋습니다.
1. *시작 지연*: 사용자가 대상을 보기 시작할 때는 아무 일도 일어나지 않아야 합니다. 불편하고 대응하기 어려운 환경이 될 수 있기 때문입니다. 그 대신 사용자가 대상을 의도적으로 응시하는지 아니면 그냥 훑어보고 있는지를 감지하기 위한 타이머를 시작합니다.
지정된 근접성(사용자가 큰 대상을 주시하고 둘러본다는 의미)에서 시작 시간을 150-250ms 정도로 사용하는 것이 좋습니다.  
2. *유지(dwell) 시작 피드백:* 사용자가 대상을 의도적으로 보고 있는 것이 확인되면 유지(dwell) 피드백을 표시하여 유지(dwell) 활성화가 시작되고 있음을 사용자에게 알립니다. 
3. *지속적인 피드백:* 사용자가 대상을 계속 바라보는 동안, 연속 진행 표시기를 나타내서, 사용자가 목표를 계속 바라봐야 한다는 것을 알 수 있도록 합니다. 특히 시선 응시 입력의 경우, 큰 원이나 구 모양이 작은 모양으로 줄어드는 효과를 사용하여 _사용자의 시각적 관심을 끄는_ 것이 좋습니다. 최종 상태(작은 원)에 대한 지표를 표시하면, 유지(dwell)가 마무리될 때 사용자와 의사 소통하는 데 도움이 됩니다. 아래 그림은 예시입니다. 
4. *마무리:* 사용자가 대상을 계속 주시하는 경우(650-850 ms 정도 더 오래), 유지(dwell) 활성화를 완료하고 바라본 대상을 선택합니다.

![유지(dwell) 상태](images/eyes_dwellstate_recommendation.png)<br>

## <a name="see-also"></a>참고 항목

* [시선 추적](eye-tracking.md)
* [시선 응시 및 커밋](gaze-and-commit-eyes.md)
* [응시 및 커밋](gaze-and-commit.md)
* [응시 및 유지](gaze-and-dwell.md)
* [음성 입력 ](../out-of-scope/voice-design.md)
