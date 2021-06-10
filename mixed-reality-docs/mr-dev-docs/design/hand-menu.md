---
title: 손 메뉴
description: 손 메뉴를 사용하면 자주 사용되는 함수에 대해 직접 연결된 UI를 빠르게 가져올 수 있습니다.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 손, 메뉴, 단추, 빠른 액세스, 레이아웃, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f007ada2d7a594f141d30a3619d4d80ac74621d8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600332"
---
# <a name="hand-menu"></a>손 메뉴

![Ulnar 측면 손 위치](images/UX_Hero_HandMenu.jpg)

손 메뉴는 HoloLens 2 가장 고유한 UX 패턴 중 하나입니다. 이를 통해 직접 연결된 UI를 신속하게 가져올 수 있습니다. 언제든지 액세스할 수 있고 쉽게 표시하고 숨길 수 있기 때문에 빠른 작업에 적합합니다.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

아래 목록에서 손 메뉴를 사용하기 위한 권장 모범 사례를 찾을 수 있습니다. [MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)에서 손 메뉴를 보여주는 예제 장면도 찾을 수 있습니다.

<br>

---

## <a name="best-practices"></a>모범 사례

**단추 수를 작게 유지** 

손으로 잠긴 메뉴와 눈 사이의 근접한 거리와 사용자가 언제든지 상대적으로 작은 시각적 영역에 집중하는 경향이 있기 때문에(시각의 주의력 원통은 약 10도임) 단추 수를 작게 유지하는 것이 좋습니다. 탐색에 따라 세 개의 단추가 있는 하나의 열은 사용자가 FOV의 가운데로 손을 이동하는 경우에도 모든 콘텐츠를 FOV(보기 필드) 내에 유지하여 잘 작동합니다. 

**빠른 작업에 손 메뉴 사용** 

Arm을 발생시키고 위치를 유지 관리하면 손쉽게 암이 화를 일으킬 수 있습니다. 짧은 상호 작용이 필요한 메뉴에 대해 손으로 잠긴 메서드를 사용합니다. 메뉴가 복잡하고 상호 작용 시간이 길어야 하는 경우 세계 잠금 또는 본문 잠금을 대신 사용하는 것이 좋습니다. 

**단추/패널 각도**

메뉴는 머리의 반대쪽 위를 향해야 합니다. 이렇게 하면 자연스러운 손 이동이 반대쪽 손으로 메뉴와 상호 작용할 수 있으며 단추를 터치할 때 불편하거나 머리가 눌려지는 위치를 방지할 수 있습니다. 

**한 손 또는 손 없는 작업을 지원하는 것이 좋습니다.**

사용자의 손을 항상 사용할 수 있다고 가정하지 마세요. 한 손 또는 양손을 사용할 수 없는 경우 광범위한 컨텍스트를 고려하고 이러한 상황에 맞게 디자인 계정을 지정해야 합니다. 한 손 메뉴를 지원하려면 손을 대칭 놓을 때 메뉴 배치를 손 잠금에서 세계 잠금으로 전환해 볼 수 있습니다(손 아래로 이동합니다). 핸즈프리 시나리오의 경우 음성 명령을 사용하여 손 메뉴를 호출하는 것이 좋습니다.

**집 근처에 단추를 추가하지 않습니다(시스템 홈 단추).**

손 메뉴 단추가 홈 단추에 너무 가까이 배치되면 손 메뉴와 상호 작용하는 동안 실수로 트리거할 수 있습니다.

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>크고 복잡한 UI 컨트롤이 있는 손 메뉴

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
직접 연결된 메뉴에서 단추 또는 UI 컨트롤의 수를 제한하는 것이 좋습니다. 이는 많은 수의 UI 요소와 확장된 상호 작용으로 인해 암겨질 수 있기 때문입니다. 사용자 경험에 큰 메뉴가 필요한 경우 사용자가 메뉴를 쉽게 잠글 수 있는 방법을 제공합니다. 권장되는 한 가지 방법은 손을 떨어지거나 사용자와 떨어져 있을 때 메뉴를 세계 잠금으로 잠그는 것입니다. 두 번째 방법은 사용자가 다른 손으로 메뉴를 직접 잡도록 하는 것입니다. 사용자가 메뉴를 놓으면 메뉴가 세계 잠금으로 설정됩니다. 이러한 방식으로 사용자는 오랜 시간 동안 편리하고 자신 있게 다양한 UI 요소와 상호 작용할 수 있습니다. 

메뉴가 세계로 잠겨 있는 경우 메뉴를 이동하는 방법을 제공하고 더 이상 필요하지 않은 경우 메뉴를 닫아야 합니다. 메뉴의 측면 또는 위쪽에 핸들을 제공하여 메뉴를 이동 가능하게 만듭니다. 메뉴를 닫을 수 있도록 닫기 단추를 추가합니다. 사용자 손을 사용할 때 메뉴가 다시 연결되도록 허용합니다. 또한 잘못된 활성화를 방지하기 위해 사용자가 손을 응시하도록 요구하는 것이 좋습니다(아래 참조).

**유용성 문제를 보여 주는 큰 메뉴**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**손 놓기에서 세계 잠겨 있는 메뉴**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**수동 잡기 & 메뉴를 세계 잠금으로 끌어오기**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a>잘못된 활성화를 방지하는 방법

손 메뉴를 트리거하는 이벤트로 손 업을 사용하는 경우 사용자가 의도적으로(통신 및 개체 조작을 위해) 손을 움직이기 때문에(가양성) 필요하지 않을 때 실수로 나타날 수 있습니다. 거짓 활성화를 줄이려면 손끝 이벤트 외에 손 메뉴를 호출하는 추가 단계를 추가합니다(예: 완전히 열린 손가락 또는 사용자가 의도적으로 손을 잡고 있음).

**플랫 팜 필요**

사용자가 환경 내에서 통신하는 동안 개체 또는 제스처를 조작할 때 발생할 수 있는 거짓 활성화를 방지할 수 있습니다. 

**응시 필요**

사용자가 시선 응시 또는 머리 응시를 사용하여 손을 응시하도록 요구하면 보조 활성화 단계(사용자의 편의를 위해 튜닝 가능한 거리 임계값 사용)로 주의를 집중해야 하기 때문에 잘못된 활성화를 방지할 수 있습니다.  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>손 메뉴 배치 모범 사례

인체 구조에서 ulnar 게는 ulna 게 근처에서 실행되는 게아입니다. ulna는 눈송이에서 가장 작은 손가락으로 늘이는 포아름에 있는 긴 웜입니다.

다음은 탐색을 기반으로 하는 두 가지 권장 배치입니다.

:::row:::
    :::column:::
        ![손 속의 Ulnar 측면 위치](images/UlnarSideHandMenu.gif)<br>
        **A. 집 안의 Ulnar**<br>
        손은 서로 겹치지 않으므로 이 위치는 안정적입니다. 이는 정확한 손 감지 및 추적에 중요합니다.
    :::column-end:::
    :::column:::
        ![Ulnar의 손 위 위치](images/UlnarAboveHandMenu.gif)<br>
        **B. 위의 Ulnar**<br>
        이 위치는 손 메뉴와 상호 작용하기 위해 손을 너무 많이 올리지 않아도 되므로 사용자에게 편리합니다. **13cm** 메뉴를 손만 위에 배치하고 ulnar 손무한 안에 단추를 맞추는 것이 좋습니다. [최적의 단추 크기에 대해 자세히 알아보기](interactable-object.md)<br>
        <br>
        기술적인 이유로 한 가지 필수 구현을 사용하여 이 위치를 권장합니다. 사용자의 반대쪽 손과 상호 작용에 가까워지면 개발자가 메뉴를 고정해야 합니다. 이렇게 하면 겹치는 손의 지터링을 방지하고 단추의 더 빠른 대상 지정을 허용합니다.<br>
        <br>
        HoloLens 2 카메라는 서로 분리된 경우 손을 정확하게 식별합니다. 손을 겹치면 손 메뉴가 앵커 위치에서 벗어날 수 있습니다.<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a>권장되지 않는 메뉴 위치

다양한 메뉴 레이아웃 및 위치로 사용자 조사를 완료했습니다. 다음 메뉴 위치는 **권장되지 않습니다.** 아래의 각 연구 단점을 찾습니다.

:::row:::
    :::column:::
        ![위쪽 암](images/AboveArm.gif)<br>
        **암 위**<br>
        1 - 손 추적을 유지하기가 어렵습니다.<br>
        2 - 자연스럽지 않은 위치로 인해 사용자의 불편을 유발합니다.
    :::column-end:::
    :::column:::
        ![위 손가락](images/AboveFingers.gif)<br>
        **위 손가락**<br>
        1 - 오랜 시간 동안 손을 내밀기 때문에 손의 아유<br>
        2 - 인덱스 및 가운데 손가락의 손 추적 문제
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![가운데 손대기 위](images/handCenter.gif)<br>
        **가운데 위 손살마**<br>
        1 - 손 겹침으로 인한 손 추적 문제<br>
        2 - 메뉴와 상호 작용하기 위해 오랫동안 손을 붙들고 있기 때문에 손의 기운
    :::column-end:::
    :::column:::
        ![위쪽 손가락 설명 ](images/TopFingerTip.gif) **위쪽 손끝**<br>
        1 - 손 추적 문제<br>
        2 - 정상 태세 위에 손을 붙들지 않도록 손의심<br>
        3 - 손가락 사이의 공간이 제한되어 실수로 다른 손가락으로 단추를 누르는 문제
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Arm의 뒷면](images/BackOfTheArm.gif)<br>
        **암(arm) 뒷면**<br>
        1 - 실수로 홈 단추를 트리거할 수 있습니다.<br>
        2 - 자연스럽거나 편안한 위치가 아닙니다.
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity용 MRTK(Mixed Reality Toolkit)의 손 메뉴

**[MRTK는](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 손 메뉴에 대한 스크립트 및 예제 장면을 제공합니다. HandConstraintPalmUp 해결기 스크립트를 사용하면 다양한 구성 가능한 옵션을 사용하여 개체를 손으로 연결할 수 있습니다. MRTK의 손 메뉴 예제에는 거짓 활성화를 방지하기 위한 평면 손만 및 응시 요구 사항과 같은 유용한 옵션이 포함됩니다.

* [손 메뉴 설명서](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [손 메뉴 예제 장면](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

MRTK 예제 허브 앱을 HoloLens 2 손 메뉴 예제를 사용해 볼 수 있습니다.

* [MRTK 예제 허브의 손 메뉴 장면](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

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