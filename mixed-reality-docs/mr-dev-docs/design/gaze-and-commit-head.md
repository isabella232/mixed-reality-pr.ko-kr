---
title: 헤드 게이즈(head-gaze) 및 커밋
description: 대상 크기 조정, 배치 및 안정화를 포함하여 헤드 응시 및 커밋 입력 모델을 시작합니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, 응시, 응시 대상 지정, 상호 작용, 디자인, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 대상, 포커스, 다듬기
ms.openlocfilehash: 641e403df23b2559429ca80aa06f384c4845ee347518adca2cfde1b3dbe874dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223666"
---
# <a name="head-gaze-and-commit"></a>헤드 게이즈(head-gaze) 및 커밋

_헤드 응시 및 커밋은_ 사용자의 머리 방향으로 개체를 대상으로 지정하는 응시 [및 커밋](gaze-and-commit.md) 입력 모델의 특별한 경우입니다. 손 제스처 에어 탭 또는 "선택" 음성 명령과 같은 보조 입력을 통해 대상에서 동작할 수 있습니다. 

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
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></td>
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

## <a name="head-and-eye-tracking-design-concepts-demo"></a>머리 및 눈 추적 디자인 개념 데모

실제 머리 및 눈 추적 디자인 개념을 보려면 아래의 **홀로그램 디자인 - 머리 추적 및 눈 추적** 동영상 데모를 확인합니다. 완료되면 계속해서 특정 주제에 대해 자세히 알아봅니다.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*이 동영상은 "홀로그램 디자인" HoloLens 2 앱에서 가져온 것입니다. [여기](https://aka.ms/dhapp)에서 전체 환경을 다운로드하여 즐겨 보세요.*

## <a name="target-sizing-and-feedback"></a>대상 크기 조정 및 피드백

헤드 응시 벡터는 미세 대상 지정에 사용할 수 있도록 반복적으로 표시되었지만, 더 큰 대상을 획득하는 총 대상 지정에 가장 적합한 경우가 많습니다. 1도~1.5도의 최소 대상 크기는 대부분의 시나리오에서 성공적인 사용자 작업을 허용하지만, 3도의 대상은 더 빠른 속도를 허용하는 경우가 많습니다. 사용자가 대상으로 하는 크기는 3D 요소의 경우에도 사실상 2D 영역입니다. 어떤 프로젝션을 향하든 대상으로 지정할 수 있는 영역이어야 합니다. 요소가 "활성"(사용자가 대상으로 지정함)이라는 중요한 신호를 제공하는 것이 유용합니다. 여기에는 표시되는 "가리키기" 효과, 오디오 강조 표시 또는 클릭과 같은 처리 또는 요소와 커서의 명확한 맞춤이 포함될 수 있습니다.

![2m 거리에서 최적 대상 크기](images/gazetargeting-size-1000px.jpg)<br>
*2미터 거리에 있는 최적 대상 크기*

<br>

![응시 대상 개체를 강조 표시한 예](images/gazetargeting-highlighting-940px.jpg)<br>
*응시 대상 개체를 강조 표시한 예*

## <a name="target-placement"></a>대상 배치

사용자는 보기 필드에서 너무 높거나 낮은 UI 요소를 찾지 못하는 경우가 많습니다. 대부분의 주의는 주로 눈 수준인 주요 포커스 주위의 영역에서 끝납니다. 대부분의 대상을 눈 높이 주변의 적당한 구간에 두면 도움이 됩니다. 사용자가 언제든지 상대적으로 작은 시각적 영역에 집중하는 경향이 있는 경우(시각의 주의력 원줄은 약 10도임) UI 요소를 개념적으로 관련된 정도로 그룹화하면 사용자가 영역을 응시할 때 항목에서 항목으로의 주의를 묶는 동작을 사용할 수 있습니다. UI를 디자인할 때는 HoloLens와 몰입형 헤드셋의 시야가 크게 달라질 수 있다는 점을 감안해야 합니다.

![Galaxy Explorer에서 응시 타기팅하기 편리하게 그룹화된 UI 요소의 예](images/gazetargeting-grouping-1000px.jpg)<br>
*Galaxy Explorer에서 응시 타기팅하기 편리하게 그룹화된 UI 요소의 예*

## <a name="improving-targeting-behaviors"></a>타기팅 동작 개선

대상을 지정하려는 사용자의 의도를 확인하거나 근사치를 지정할 수 있는 경우 올바르게 대상으로 지정된 것처럼 거의 누락된 상호 작용 시도를 수락하는 것이 유용할 수 있습니다. 혼합 현실 환경으로 통합할 수 있는 몇 가지 성공적인 방법은 다음과 같습니다.

### <a name="head-gaze-stabilization-gravity-wells"></a>헤드 게이즈(head-gaze) 안정화("중력 우물")

이 설정은 대부분 또는 항상 켜져 있어야 합니다. 이 기술은 보고 말하는 동작으로 인해 사용자가 이동할 수 있는 자연스러운 머리 및 목 지터를 제거합니다.

### <a name="closest-link-algorithms"></a>가장 가까운 링크 알고리즘

이러한 알고리즘은 스파스 대화형 콘텐츠가 있는 영역에서 가장 잘 작동합니다. 사용자가 상호 작용하려는 대상을 확인할 가능성이 높은 경우 일정 수준의 의도를 가정하여 대상 지정 능력을 보완할 수 있습니다.

### <a name="backdating-and-postdating-actions"></a>작업 백업 및 게시

이 메커니즘은 속도가 필요한 작업에 유용합니다. 사용자가 일련의 대상 지정 및 활성화를 빠르게 진행하는 경우 의도를 가정하는 것이 유용합니다. 또한 탭 전이나 약간 후에 사용자가 포커스에 있던 대상에 대해 누락된 단계를 수행하도록 허용하는 것도 유용합니다(이전/이후 50ms는 초기 테스트에서 효과적임).

### <a name="smoothing"></a>다듬기

이 메커니즘은 자연스러운 머리 이동 특성으로 인해 약간의 지터와 지터를 줄이는 이동 경로 지정에 유용합니다. 패스 동작을 다듬을 때 시간이 지남에 따라가 아니라 이동의 크기와 거리에 따라 다듬습니다.

### <a name="magnetism"></a>자성

이 메커니즘은 가장 일반적인 버전의 가장 가까운 링크 알고리즘으로 간주할 수 있습니다. 즉, 대화형 레이아웃에 대한 지식을 사용하여 사용자 의도에 더 잘 접근하여 사용자가 대상에 접근할 수 있기 때문에 대상에 커서를 그리거나 적중 상자를 눈에 띄게 늘리거나 적중함만 늘릴 수 있습니다. 이는 작은 대상에 대해 강력할 수 있습니다.

### <a name="focus-stickiness"></a>포커스 고착

포커스를 부여할 주변 대화형 요소를 결정할 때 포커스 고정은 현재 포커스가 있는 요소에 편차를 제공합니다. 이렇게 하면 자연 소음이 있는 두 요소 사이의 중간점에서 부동 소수점에서 부동 소수점 전환 동작을 줄일 수 있습니다.

## <a name="see-also"></a>추가 정보

* [시선 기반 상호 작용](eye-gaze-interaction.md)
* [응시 및 유지](gaze-and-dwell.md)
* [손 - 직접 조작](direct-manipulation.md)
* [손 - 제스처](gaze-and-commit.md#composite-gestures)
* [손 - 가리키고 커밋](point-and-commit.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [음성 입력 ](voice-input.md)