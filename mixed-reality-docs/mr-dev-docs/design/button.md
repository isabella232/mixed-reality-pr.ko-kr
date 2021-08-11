---
title: 단추
description: 혼합 현실 기본 구성 요소 중 하나인 단추를 사용 하 여 즉각적인 작업을 트리거하는 방법에 대해 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 혼합 현실, 컨트롤, 상호 작용, ui, ux, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, mrtk, 혼합 현실 Toolkit, 단추
ms.openlocfilehash: 602d5b8784c97676e29574e4a5b0ffb7b240f07c2c43bbe68e0f8bc49db9dd1f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219324"
---
# <a name="button"></a>단추

![단추](images/UX_Hero_Button.jpg)

사용자는 단추를 사용 하 여 혼합 현실 환경에서 즉각적인 작업을 트리거할 수 있습니다. HoloLens 2에서 단추에는 사용자와의 상호 작용 신뢰도를 높이는 데 도움이 되는 시각적 신호 및 affordances 있습니다. 

:::row:::
    :::column:::
       ![근접 조명 효과가 표시 된 단추](images/UX_Button_Affordance_ProximityLight.jpg)<br>
       **근접 조명**<br>
    :::column-end:::
    :::column:::
       ![포커스 강조 표시 효과가 표시 된 단추 선택](images/UX_Button_Affordance_FocusHighlight.jpg)<br>
        **포커스 강조 표시**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![압축 케이지 효과를 표시 하 여 단추 누름](images/UX_Button_Affordance_Compression.jpg)<br>
       **케이지 압축**<br>
    :::column-end:::
    :::column:::
       ![트리거 펄스 효과가 표시 된 단추를 누르는 중임](images/UX_Button_Affordance_Pulse.jpg)<br>
        **펄스 on 트리거**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a>Unity 용 mrtk (Mixed Reality Toolkit)의 단추
**[Unity 용 mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 HoloLens 2 및 HoloLens (첫 번째 gen)의 셸 스타일 단추를 비롯 한 다양 한 유형의 단추 prefabs을 제공 합니다. HoloLens 2 단추 prefab에는 사용자 신뢰도를 개선 하는 데 도움이 되는 몇 가지 상세 affordances 있습니다.

* 근접 기반 강조 표시
* 전면 케이지 압축
* 트리거의 펄스 효과입니다.

* 자세한 지침 및 사용자 지정 예제를 보려면 [Mrtk 단추](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) 를 확인 하세요.

<br>

---

## <a name="see-also"></a>추가 정보

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