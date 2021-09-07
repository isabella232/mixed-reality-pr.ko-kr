---
title: 단추
description: 혼합 현실의 기본 구성 요소 중 하나인 단추를 사용하여 즉각적인 작업을 트리거하는 방법을 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Mixed Reality, 컨트롤, 상호 작용, ui, ux, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 단추
ms.openlocfilehash: 4b3a9bda852c7a83ee603c3f2340d44f4be89f4d
ms.sourcegitcommit: 4f1697b11e5638db9bbd0bd7a671d846d54c6389
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2021
ms.locfileid: "122682978"
---
# <a name="button"></a>단추

![단추](images/UX_Hero_Button.jpg)

단추는 혼합 현실에서 가장 기본적이고 중요한 UI 요소 중 하나입니다. 이를 통해 사용자는 즉각적인 작업을 트리거할 수 있습니다. 혼합 현실에는 물리적 피드백이 없으므로 사용자의 상호 작용 신뢰도를 높이기에 충분한 시각적 및 오디오 피드백을 제공하는 것이 중요합니다. 

HoloLens 2 단추 디자인에서는 많은 디자인 반복, 프로토타이핑 및 사용자 연구 연구를 기반으로 하여 빈 공간에서 사용자의 깊이 인식 및 상호 작용에 도움이 되는 여러 시각적 어포던스 및 오디오 신호를 통합했습니다. 

## <a name="visual-affordances"></a>시각적 어세서

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWJHgW]


:::row:::
    :::column:::
       ![근접 광원 효과가 표시된 단추](images/UX_Button_Affordance_ProximityLight.jpg)<br>
       **근접 조명**<br>
    :::column-end:::
    :::column:::
       ![포커스 강조 효과와 함께 선택된 단추](images/UX_Button_Affordance_FocusHighlight.jpg)<br>
        **포커스 강조 표시**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![압축 압축 효과가 표시된 단추를 누르고 있습니다.](images/UX_Button_Affordance_Compression.jpg)<br>
       **압축 압축**<br>
    :::column-end:::
    :::column:::
       ![트리거 펄스 효과가 표시된 단추를 누르고 있습니다.](images/UX_Button_Affordance_Pulse.jpg)<br>
        **트리거의 펄스**<br>
    :::column-end:::
:::row-end:::

<br>

## <a name="audio-cues"></a>오디오 큐

적절한 오디오 피드백은 사용자 환경을 크게 향상시킬 수 있습니다. HoloLens 2 단추는 다음 신호를 전달하는 오디오 피드백을 제공합니다.
* **연락처 시작: 터치가 시작될** 때 소리 재생(가까운 상호 작용)
* **연락처 끝:** 터치 엔드에서 소리 재생(근거리 상호 작용)
* **손가락 모으기 시작:** 손가락 모으기 선택에서 소리 재생(응시 또는 광선과의 원거리 상호 작용)
* **손가락 모으기 끝:** 손가락 모으기 릴리스에서 소리 재생(응시 또는 광선과의 원거리 상호 작용)

<br>

---

:::row:::
    :::column:::
        ## <a name="voice-commandingbr"></a>음성 명령<br>
        혼합 현실의 단추의 경우 대체 상호 작용 옵션을 지원하는 것이 중요합니다. 기본적으로 모든 단추에 음성 명령을 지원하는 것이 좋습니다. HoloLens 2 단추 디자인에서는 가리키기 상태 동안 도구 설명이 제공 되어 검색 가능성을 향상 시킵니다.
    :::column-end:::
        :::column:::
       ![음성 입력 ](images/UX_Hero_VoiceCommand.jpg)<br>
        *이미지: 음성 명령에 대한 도구 설명*
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a>크기 조정 권장 사항

상호 작용 가능한 모든 개체를 쉽게 터치할 수 있도록 하려면 상호 작용 가능한 가 사용자로부터의 거리를 기준으로 최소 크기를 충족하는지 확인하는 것이 좋습니다. 시각적 각도는 종종 시각적 호의 각도로 측정됩니다. 시각적 각도는 사용자의 눈과 개체 사이의 거리를 기반으로 하며 일정하게 유지되지만, 대상의 물리적 크기는 사용자와의 거리가 변경됨에 따라 변경됩니다. 사용자와의 거리를 기준으로 개체의 필요한 물리적 크기를 확인하려면 [이](https://elvers.us/perception/visualAngle/)와 같은 시각적 각도 계산기를 사용해 보세요.

다음은 상호 작용 가능한 콘텐츠의 최소 크기에 대한 권장 사항입니다.

### <a name="target-size-for-direct-hand-interaction"></a>직접 손 조작을 위한 대상 크기

| 거리 | 시야각 | 크기 |
|---------|---------|---------|
| 45cm  | 2°보다 작지 않습니다. | 1.6 x 1.6 cm |

![직접 손 조작을 위한 대상 크기](images/TargetSizingNear.jpg)<br>
*직접 손 조작을 위한 대상 크기*

<br>

### <a name="target-size-for-buttons"></a>단추의 대상 크기

직접 상호 작용을 위한 단추를 만들 때 아이콘과 일부 텍스트를 포함할 충분한 공간이 있는지 확인하기 위해 최소 크기가 3.2 x 3.2 cm보다 큰 것이 좋습니다.

| 거리 | 최소 크기 |
|---------|---------|
| 45cm  | 3.2 x 3.2 cm |

![단추의 대상 크기](images/TargetSizingButtons.png)<br>
*단추의 대상 크기*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>손 광선 또는 응시 상호 작용의 대상 크기
| 거리 | 시야각 | 크기 |
|---------|---------|---------|
| 2m  | 1°보다 작지 않습니다. | 3.5 x 3.5 cm |

![손 광선 또는 응시 상호 작용의 대상 크기](images/TargetSizingFar.jpg)<br>
*손 광선 또는 응시 상호 작용의 대상 크기*

<br>

---

## <a name="design-guidelines"></a>디자인 지침

### <a name="avoid-transparent-backplate"></a>투명한 백플레이트 방지
단추가 있는 메뉴 UI를 디자인할 때는 불투명 백플레이트 사용을 권장합니다. 투명 백플랫은 다음과 같은 이유로 권장되지 않습니다.
* 이벤트를 트리거하기 위해 단추를 얼마나 눌렀는지 이해하기 어렵기 때문에 상호 작용하기 어렵습니다.
* 복잡한 물리적 환경의 가독성 문제
* 투명 판을 통해 표시되는 홀로그램스 깊이 LSR 안정화 기술과 함께 사용할 때수명 효과 문제를 표시할 수 있습니다.

[홀로그램 디스플레이에 대한](designing-content-for-holographic-display.md) 색 선택 및 지침에 대한 자세한 내용은 홀로그램 디스플레이용 콘텐츠 디자인을 참조하세요.

![투명한 UI 예제 투명 ](images/color_transparent_examples.jpg)
 *UI 백플레이트 예*

<br>

### <a name="use-shared-backplate"></a>공유 백플레이트 사용
여러 단추의 경우 개별 단추의 백플레이트 대신 공유 백플레이트 를 사용하는 것이 좋습니다.

* 시각적 노이즈 및 복잡성 줄이기
* 그룹화 지우기  

![공유 백플레이트 ](images/Button_Design_SharedBackplate.png
)
 *예제 공유 UI 백플레이트 예*

<br>

---

## <a name="button-in-mrtk-mixed-reality-toolkit"></a>MRTK의 단추(Mixed Reality Toolkit)
**[Unity용 MRTK](/windows/mixed-reality/mrtk-unity/)** 및 **[Unreal용 MRTK는](/windows/mixed-reality/develop/unreal/unreal-mrtk-introduction)** HoloLens 2 스타일 단추를 포함하여 다양한 유형의 단추 프리팹을 제공합니다. HoloLens 2 단추 구성 요소에는 이 페이지에 소개된 모든 시각적 피드백 및 상호 작용 세부 정보가 포함되어 있습니다. 이를 사용하면 디자이너, 개발자, 연구원이 수행한 많은 디자인 반복 및 사용자 연구 결과를 활용할 수 있습니다.

자세한 지침 및 사용자 지정된 예제는 [MRTK - 단추를](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) 확인하세요.

<br>

---

## <a name="see-also"></a>참고 항목

* [커서](cursors.md)
* [손 광선](point-and-commit.md)
* [Button](button.md)
* [상호 작용 가능한 개체](interactable-object.md)
* [경계 상자 및 앱 바](app-bar-and-bounding-box.md)
* [조작](direct-manipulation.md)
* [손 메뉴](hand-menu.md)
* [Near 메뉴](near-menu.md)
* [개체 컬렉션](object-collection.md)
* [음성 명령](voice-input.md)
* [키보드](keyboard.md)
* [Tooltip](tooltip.md)
* [슬레이트](slate.md)
* [슬라이더](slider.md)
* [셰이더](shader.md)
* [빌보딩 및 태그얼롱](billboarding-and-tag-along.md)
* [진행률 표시](progress.md)
* [표면 자성](surface-magnetism.md)