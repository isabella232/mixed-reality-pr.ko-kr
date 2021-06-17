---
title: 경계 상자 및 앱 바
description: 앱 바는 홀로그램 경계의 아래쪽 가장자리에 표시되는 일련의 단추를 포함하는 개체 수준 메뉴입니다.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, 앱 바, 경계 상자, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5c437b303ec5462179a1ddf43687aa1653419b08
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110094"
---
# <a name="bounding-box-and-app-bar"></a>경계 상자 및 앱 바
![경계는 Mixed Reality 개체 조작을 위한 표준 인터페이스입니다.](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>경계 상자란?

경계는 Mixed Reality 개체 조작을 위한 표준 인터페이스입니다. 이 기능은 사용자에게 개체가 현재 조정 가능한 시각적 신호를 제공합니다. HoloLens 2 경계 상자는 직접 손 조작과 함께 작동하며 사용자의 손가락 근접에 응답합니다. 사용자가 개체와의 거리를 인식하는 데 도움이 되는 시각적 피드백을 보여줍니다.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>개체 크기 조정<br>
        경계 상자의 모서리는 개체의 크기를 조정하는 데 사용할 수 있음을 사용자에게 알려줍니다. 핸들은 배율 조정을 위해 널리 이해된 패턴을 따릅니다. 이 시각 신호는 조정 모드 외부에서 표시되지 않더라도 개체의 전체 영역을 사용자에게 표시합니다. 이 기능이 없으면 다른 개체 또는 표면에 스냅된 개체가 주위에 공백이 있어서는 안 되는 것처럼 동작하는 것처럼 보일 수 있습니다.<br>
        <br>
        *비디오 루프: 경계 상자를 통해 개체 크기 조정*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![경계 상자를 통해 개체 크기를 조정하는 HoloLens의 관점](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>개체 회전<br>
        경계 상자의 가장자리에 있는 세로 사각형 어조도 회전 표시기입니다. 이렇게 하면 사용자가 배치된 홀로그램을 더 세부적으로 조정할 수 있습니다. 조정하고 크기를 조정할 수 있을 뿐만 아니라 이제도 회전할 수 있습니다.<br>
        <br>
        *비디오 루프: 경계 상자를 통해 개체 회전*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![경계 상자를 통해 개체를 회전하는 HoloLens 지점 보기](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>HoloLens 2 손 근접도에 대한 시각적 피드백<br>
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

**Unity 앱 개발의 경우 [Mixed Reality Toolkit-Unity의 경계 상자를 참조하세요.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**

<br>

---

## <a name="what-is-the-app-bar"></a>앱 표시줄이란?

앱 바는 홀로그램 경계의 아래쪽 가장자리에 표시되는 일련의 단추를 포함하는 개체 수준 메뉴입니다. 이 패턴은 일반적으로 사용자가 홀로그램을 제거하고 조정할 수 있도록 하는 데 사용됩니다. 앱 바는 주로 사용자 환경에서 배치된 개체를 관리하는 방법으로 설계되었습니다. 경계 상자와 결합된 사용자는 혼합 현실에서 개체가 지향되는 위치와 방법을 완전히 제어할 수 있습니다.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>앱 표시줄이 사용자를 따릅니다.<br>
        이 패턴은 세계에서 잠긴 개체와 함께 사용되므로 사용자가 개체를 이동할 때 앱 표시줄은 항상 사용자와 가장 가까운 개체 쪽에 표시됩니다. 기술적으로는 그렇지 않지만 이 기능은 효과적으로 동일한 결과를 달성합니다. 사용자 환경의 다른 위치에서 사용할 수 있는 기능을 차단하거나 차단할 수 없도록 합니다. <br>
        <br>
        *비디오 루프: 홀로그램을 둘러보면 앱 바가 다음과 같이 진행됩니다.*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![홀로그램을 둘러 들이고 있습니다. 앱 표시줄은 다음과 같습니다.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity용 MRTK(Mixed Reality Toolkit)의 경계 상자
**[MRTK는](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 경계 상자 및 앱 표시줄에 대한 스크립트와 프리팹을 제공합니다. BoundingBox.cs 스크립트를 개체에 할당하여 경계 상자를 추가할 수 있습니다.

* [MRTK - 경계 상자](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


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