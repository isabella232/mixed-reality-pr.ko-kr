---
title: 상호 작용 가능한 개체
description: 혼합 현실 애플리케이션에서 이벤트를 트리거하고, 시각 신호를 제공하고, 개체와 상호 작용하는 방법을 알아봅니다.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality, 컨트롤, 상호 작용, 큐, ui, ux, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 오디오
ms.openlocfilehash: b25c25a6dd48bcc85a556787099734d147d18df2
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110213"
---
# <a name="interactable-object"></a>상호 작용 가능한 개체

![상호 작용 가능한 개체](images/UX_Hero_Interactable.jpg)

단추는 오랫동안 2D 추상 세계에서 이벤트를 트리거하는 데 사용된 메타포입니다. 3차원 혼합 현실 세계에서는 더 이상 이 추상화 세계로 제한할 필요가 없습니다. 이벤트를 트리거하는 **상호 작용 가능한 개체일** 수 있습니다. 상호 작용 가능한 개체는 테이블의 커피 잔에서 중간 계단의 풍선에 이르기까지 모든 것일 수 있습니다. 대화 UI와 같은 특정 상황에서는 여전히 기존 단추를 사용합니다. 단추의 시각적 표현은 컨텍스트에 따라 달라집니다.

<br>

---

## <a name="important-properties-of-the-interactable-object"></a>상호 작용 가능한 개체의 중요한 속성

### <a name="visual-cues"></a>시각 신호

시각 신호는 시각 인식 중에 눈에서 수신되고 시각적 시스템에서 처리되는 광원의 센서 신호입니다. 시각적 개체 시스템은 많은 종, 특히 인간에서 주로 적용되므로 시각 신호는 세계를 인식하는 방식에서 정보의 큰 소스입니다.

홀로그램 개체는 혼합 현실의 실제 환경과 혼합되므로 상호 작용할 수 있는 개체를 이해하기 어려울 수 있습니다. 사용자 환경의 상호 작용 가능한 개체의 경우 각 입력 상태에 대해 차별화된 시각적 신호를 제공하는 것이 중요합니다. 이렇게 하면 사용자가 상호 작용 가능한 환경의 일부를 이해하고 일관된 상호 작용 방법을 사용하여 사용자가 안심할 수 있습니다.

<br>

---

### <a name="far-interactions"></a>원거리 상호 작용

사용자가 응시, 손 광선 및 모션 컨트롤러의 광선과 상호 작용할 수 있는 개체의 경우 다음 세 가지 입력 상태에 대해 서로 다른 시각 신호를 갖는 것이 좋습니다.

:::row:::
    :::column:::
       ![기본 상태의 상호 작용 가능한 개체](images/interactibleobject-states-default.jpg)<br>
       **기본(관찰) 상태**<br>
        개체의 기본 유휴 상태입니다.
    커서가 개체에 없습니다. 손은 감지되지 않습니다.
    :::column-end:::
    :::column:::
       ![대상 및 가리키기 상태의 상호 작용 가능한 개체](images/interactibleobject-states-targeted.jpg)<br>
        **대상 지정(가리키기) 상태**<br>
        개체가 응시 커서, 손가락 근접 또는 모션 컨트롤러의 포인터를 대상으로 하는 경우
    커서가 개체에 있습니다. 손은 감지되고 준비됩니다.
    :::column-end:::
    :::column:::
       ![누른 상태의 상호 작용 가능한 개체](images/interactibleobject-states-pressed.jpg)<br>
       **누른 상태**<br>
        에어 탭 제스처를 통해 개체를 누르면 손가락으로 누르거나 모션 컨트롤러의 선택 단추를 누릅니다.
    커서가 개체에 있습니다. 손을 감지하고, 에어 탭합니다.
    :::column-end:::
:::row-end:::

<br>

---

강조 표시 또는 크기 조정과 같은 기술을 사용하여 사용자의 입력 상태에 대한 시각적 신호를 제공할 수 있습니다. 혼합 현실에서는 시작 메뉴 앱 바 단추를 통해 다양한 입력 상태를 시각화하는 예제를 찾을 수 있습니다. 

이러한 상태는 **홀로그램 단추** 에서 다음과 같이 표시됩니다.

:::row:::
    :::column:::
       ![기본 상태의 홀로그램 단추](images/MRTK_InteractableState-default.jpg)<br>
       **기본(관찰) 상태**<br>
    :::column-end:::
    :::column:::
       ![대상 및 가리키기 상태의 홀로그램 단추](images/MRTK_InteractableState-targeted.jpg)<br>
        **대상 지정(가리키기) 상태**<br>
    :::column-end:::
    :::column:::
       ![누른 상태의 홀로그램 단추](images/MRTK_InteractableState-pressed.jpg)<br>
       **누른 상태**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>가까운 상호 작용(직접) 

HoloLens 2 개체와 상호 작용할 수 있는 굴절형 손 추적 입력을 지원합니다. 능동적 피드백과 완벽한 깊이 인식이 없으면 개체에서 얼마나 멀리 떨어져 있는지 또는 터치하고 있는지 여부를 알기 어려울 수 있습니다. 개체의 상태, 특히 해당 개체를 기반으로 하는 손의 상태를 전달하기에 충분한 시각적 신호를 제공하는 것이 중요합니다.

시각적 피드백을 사용하여 다음 상태를 전달합니다.
* **기본값(관찰)**: 개체의 기본 유휴 상태입니다.
* **마우스로 가리키기:** 손을 홀로그램 근처에 있을 때 홀로그램을 대상으로 하는 손을 전달하도록 시각적 개체를 변경합니다. 
* **거리 및 상호 작용 지점:** 손에서 홀로그램에 접근하면 피드백이 디자인되어 프로젝션된 상호 작용 지점과 손가락이 얼마나 멀리 떨어져 있는지를 알 수 있습니다.
* **연락처 시작:** 터치가 발생했음을 전달하도록 시각적 개체(밝게, 색)를 변경합니다.
* **이해:** 개체를 파악할 때 시각적 개체(밝게, 색) 변경
* **연락처 종료:** 터치가 종료되면 시각적 개체(밝게, 색) 변경

<br>

---

:::row:::
    :::column:::
        ![가리키기(원거리)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **가리키기(원거리)**<br>
        손의 근접성을 기준으로 강조 표시
    :::column-end:::
    :::column:::
        ![가리키기(가까이)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **가리키기(가까이)**<br>
        손까지의 거리를 기준으로 크기 변경을 강조 표시합니다.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![터치/누르기](images/640px-interactibleobject-states-near-press.jpg)<br>
        **터치/누르기**<br>
        시각적 개체 및 오디오 피드백.
    :::column-end:::
    :::column:::
        ![파악](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **파악**<br>
        시각적 개체 및 오디오 피드백.
    :::column-end:::
:::row-end:::

<br>

<br>

---

[HoloLens 2 단추는](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) 다양한 입력 상호 작용 상태를 시각화하는 방법의 예입니다.

:::row:::
    :::column:::
        ![기본값](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **기본값**<br>
    :::column-end:::
    :::column:::
        ![가리키기](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **가리키기**<br>
        근접 기반 조명 효과를 공개합니다.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![터치](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **터치**<br>
        잔물결 효과를 표시합니다.
    :::column-end:::
    :::column:::
        ![작업 방법](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **눌러**<br>
        앞면판을 이동합니다.
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>HoloLens 2 "링" 시각 신호<br>
        HoloLens 2 사용자의 깊이 인식에 도움이 될 수 있는 추가 시각 신호가 있습니다. 손끝이 개체에 가까워지면 손끝 근처의 링이 나타나고 축소됩니다. 링은 누른 상태에 도달하면 결국 점으로 수렴됩니다. 이 시각적 어패던스는 사용자가 개체에서 얼마나 멀리 떨어져 있는지 이해하는 데 도움이 됩니다.<br>
        <br>
        *비디오 루프: 경계 상자에 대한 근접성을 기반으로 하는 시각적 피드백의 예*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![손 근접도에 대한 시각적 피드백](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>오디오 큐

직접 손 상호 작용을 위해 적절한 오디오 피드백은 사용자 환경을 크게 향상시킬 수 있습니다. 오디오 피드백을 사용하여 다음 신호를 전달합니다.
* **연락처 시작: 터치가** 시작될 때 소리 재생
* **연락처 끝:** 터치 엔드에서 소리 재생
* **잡기 시작: 잡기가** 시작될 때 소리를 재생합니다.
* **잡기 끝: 잡기가** 끝날 때 소리를 재생합니다.

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>음성 명령<br>
        상호 작용 가능한 개체의 경우 대체 상호 작용 옵션을 지원하는 것이 중요합니다. 기본적으로 상호 작용 가능한 모든 개체에 [대해 음성 명령을](../out-of-scope/voice-design.md) 지원하는 것이 좋습니다. 검색 가능성을 개선하기 위해 가리키기 상태 중에 도구 설명도 제공할 수 있습니다.<br>
        <br>
        *이미지: 음성 명령에 대한 도구 설명*
    :::column-end:::
        :::column:::
       ![음성 명령](images/640px-interactibleobject-voicecommand.png)<br>
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

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity용 MRTK(Mixed Reality Toolkit)의 상호 작용 가능한 개체

**[MRTK에서](https://github.com/Microsoft/MixedRealityToolkit-Unity)** [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) 스크립트를 사용하여 개체가 다양한 유형의 입력 상호 작용 상태에 응답하도록 할 수 있습니다. 색, 크기, 재질 및 셰이더와 같은 개체 속성을 제어하여 시각적 상태를 정의할 수 있는 다양한 유형의 테마를 지원합니다.

* [상호 작용 가능](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [손 상호 작용 예제 장면](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

MixedRealityToolkit의 표준 셰이더에서는 시각적 및 오디오 큐를 만드는 데 도움이 되는 **근접 광원과** 같은 다양한 옵션을 제공합니다.

* [MRTK 표준 세이더](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a>참조

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