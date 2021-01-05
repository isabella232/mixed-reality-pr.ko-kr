---
title: 헤드 게이즈(head-gaze) 및 커밋
description: 헤드-응시 및 커밋 입력 모델의 개요입니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: 혼합 현실, 응시, 응시 대상 지정, 상호 작용, 디자인, 혼합 현실 헤드셋, windows mixed Reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, 혼합 현실 도구 키트, 대상, 포커스, 다듬기
ms.openlocfilehash: cc12c349704a63c5b95c9eede91d0486f56787a2
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847883"
---
# <a name="head-gaze-and-commit"></a>헤드 게이즈(head-gaze) 및 커밋

_헤드-응시 및 커밋은_ 사용자의 방향으로 개체를 대상으로 지정 하는 [응시 및 커밋](gaze-and-commit.md) 입력 모델의 특별 한 경우입니다. 손 제스처 air 탭 또는 "선택" 음성 명령과 같은 보조 입력을 사용 하 여 대상에서 작업을 수행할 수 있습니다. 

## <a name="device-support"></a>디바이스 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>입력 모델</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>헤드 게이즈(head-gaze) 및 커밋</td>
        <td>✔️ 권장</td>
        <td>✔️ 권장(세 번째 선택 - <a href="interaction-fundamentals.md">다른 옵션 보기</a>)</td>
        <td>➕ 대체 옵션</td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a>대상 크기 조정 및 피드백

헤드 응시 벡터는 세밀 하 게 대상 지정에 사용할 수 있도록 반복적으로 표시 되었지만 큰 대상을 확보 하는 데 가장 적합 한 경우가 많습니다. 최소 대상 크기인 1 ~ 1.5도를 사용 하면 대부분의 시나리오에서 성공적인 사용자 작업을 허용 하지만, 3도의 대상은 속도가 더 높을 수 있습니다. 사용자가 대상으로 하는 크기는 3D 요소에도 효과적으로 사용할 수 있는 2D 영역입니다. 어떤 프로젝션이 가능 영역 이어야 합니다. 요소가 "활성" (사용자가 대상으로 하는) 인 두드러진 몇 가지 큐를 제공 하는 것이 유용 합니다. 여기에는 표시 되는 "가리키기" 효과, 오디오 하이라이트 또는 클릭 또는 요소와 커서의 처리가 같은 내용이 포함 될 수 있습니다.

![2m 거리에서 최적 대상 크기](images/gazetargeting-size-1000px.jpg)<br>
*2 미터 거리의 최적 대상 크기*

<br>

![응시 대상 개체를 강조 표시한 예](images/gazetargeting-highlighting-940px.jpg)<br>
*응시 대상 개체를 강조 표시한 예*

## <a name="target-placement"></a>대상 배치

사용자는 종종 보기의 필드에 너무 많거나 낮은 UI 요소를 찾지 못할 수 있습니다. 대부분의 주의가 가장 중요 한 영역에서 가장 중요 한 부분을 차지 합니다. 대부분의 대상을 눈 높이 주변의 적당한 구간에 두면 도움이 됩니다. 사용자가 언제 든 지 상대적으로 작은 시각적 영역에 초점을 맞출 수 있는 경향이 있으므로 (attentional의 비전 원뿔 약 10도), 사용자가 응시를 영역 전체로 이동할 때 UI 요소를 개념적으로 관련 된 수준까지 그룹화 할 수 있습니다. UI를 디자인할 때는 HoloLens와 몰입형 헤드셋의 시야가 크게 달라질 수 있다는 점을 감안해야 합니다.

![Galaxy Explorer에서 응시 타기팅하기 편리하게 그룹화된 UI 요소의 예](images/gazetargeting-grouping-1000px.jpg)<br>
*Galaxy Explorer에서 응시 타기팅하기 편리하게 그룹화된 UI 요소의 예*

## <a name="improving-targeting-behaviors"></a>타기팅 동작 개선

특정 항목을 대상으로 지정 하는 사용자 의도를 결정 하거나 긴밀 하 게 사용할 수 있는 경우, 정확히 대상으로 지정 된 것 처럼 거의 누락 된 상호 작용 시도를 허용 하면 도움이 될 수 있습니다 다음은 혼합 현실 환경에서 통합할 수 있는 성공적인 몇 가지 방법입니다.

### <a name="head-gaze-stabilization-gravity-wells"></a>헤드 게이즈(head-gaze) 안정화("중력 우물")

이는 대부분의 시간 동안 설정 해야 합니다. 이 기술은 사용자가 이동 및 말하기 동작으로 인해 이동 하는 것과 같은 자연 스런 head 및 목 jitter을 제거 합니다.

### <a name="closest-link-algorithms"></a>가장 가까운 링크 알고리즘

이러한 알고리즘은 스파스 대화형 콘텐츠가 있는 영역에서 가장 잘 작동 합니다. 사용자가 상호 작용 하려고 했던 항목을 결정할 수 있을 확률이 높은 경우 특정 수준의 의도를 가정 하 여 대상 기능을 보완할 수 있습니다.

### <a name="backdating-and-postdating-actions"></a>배경 및 postdating 작업

이 메커니즘은 속도가 필요한 작업에 유용합니다. 사용자가 고속 대상 지정 및 활성화 연습을 통해 이동 하는 경우 몇 가지 의도를 가정 하는 것이 유용 합니다. 또한 사용자가 탭을 약간 전후에 초점을 맞춘 대상에 대 한 작업을 수행 하는 데 유용 합니다 (초기 테스트에서 50 밀리초 이전/후에 적용 됨).

### <a name="smoothing"></a>다듬기

이 메커니즘은 자연 스러운 헤드 이동 특성으로 인해 pathing 이동 하 여 약간의 지터와 wobbles를 줄이는 데 유용 합니다. Pathing 동작을 매끄럽게 하는 경우 시간이 지남에 따라 부드러운 이동의 크기와 거리를 매끄럽게 합니다.

### <a name="magnetism"></a>자성

이 메커니즘은 가장 근접 한 링크 알고리즘의 보다 일반적인 버전으로 간주할 수 있습니다. 즉, 사용자가 대화형 레이아웃에 대 한 몇 가지 정보를 사용 하 여 사용자 의도를 보다 효과적으로 활용할 수 있으므로 대상에 커서를 그리거나 단순히 hitboxes를 늘릴 수 있습니다. 이는 작은 대상에 대해 강력 할 수 있습니다.

### <a name="focus-stickiness"></a>포커스 고착

에서 제공 하는 근처 대화형 요소를 결정 하는 경우 포커스에 포커스를 지정 하면 현재 포커스가 있는 요소에 대 한 바이어스가 제공 됩니다. 이렇게 하면 자연 노이즈가 있는 두 요소 간의 중간점에서 부동 상태에 있는 경우 비정상적인 포커스 전환 동작을 줄일 수 있습니다.

## <a name="see-also"></a>추가 정보

* [시선 기반 상호 작용](eye-gaze-interaction.md)
* [응시 및 유지](gaze-and-dwell.md)
* [손 - 직접 조작](direct-manipulation.md)
* [손 - 제스처](gaze-and-commit.md#composite-gestures)
* [손 - 가리키고 커밋](point-and-commit.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [음성 입력 ](voice-input.md)



