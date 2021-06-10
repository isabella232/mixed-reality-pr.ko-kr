---
title: 진행률 표시
description: 진행률 컨트롤이 혼합 현실 앱에서 장기 실행 작업이 진행 중이라는 피드백을 사용자에게 제공하는 방법을 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 컨트롤, ui, ux, 진행률 표시기, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 01f032efb887ecfc6f8d66683fb954cd0574a4f3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600552"
---
# <a name="progress-indicator"></a>진행률 표시기

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

진행률 컨트롤은 장기 실행 작업이 진행 중이라는 피드백을 제공합니다. 진행률 표시기가 표시되면 사용자는 대기 시간을 볼 수 있으며 앱과 상호 작용할 수 없습니다.

<br>

---

## <a name="types-of-progress"></a>진행률 유형

어떤 일이 발생하는지에 대한 정보를 사용자에게 제공하는 것이 중요합니다. 혼합 현실에서 앱에 좋은 시각적 피드백이 없는 경우 실제 환경 또는 개체에 의해 사용자에게 쉽게 방해가 될 수 있습니다. 데이터가 로드되거나 장면이 업데이트되는 경우와 같이 몇 초 정도 걸리는 경우 시각적 표시기를 표시하는 것이 좋습니다. 사용자에게 작업이 진행 중임을 표시하는 두 가지 옵션인 **진행률 표시줄** 또는 **진행률 링이** 있습니다.

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>진행률 표시줄<br>
        진행률 표시줄에 작업의 완료 백분율이 표시됩니다. 해당 기간이 알려져 있지만(결정) 작업 중에 사용되어야 하지만 진행률로 인해 앱과의 사용자 상호 작용이 차단되지 않아야 합니다.<br>
        <br>
        *이미지: HoloLens의 진행률 표시줄 예제*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens의 진행률 표시줄 예제](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>진행률 링<br>
        진행률 링에는 확정되지 않은 상태만 있으며 작업이 완료될 때까지 사용자 상호 작용이 차단될 때 사용해야 합니다.<br>
        <br>
        *이미지: HoloLens의 진행률 링 예제*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 디바이스의 진행률 링 예제](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>사용자 지정 개체 진행률<br>
        사용자 고유의 사용자 지정 2D/3D 개체를 사용하여 Progress 컨트롤을 사용자 지정하여 앱의 개성 및 브랜드 ID에 추가할 수 있습니다.<br>
        <br>
        *이미지: HoloLens의 사용자 지정 메시 예제 진행률*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens에서 사용자 지정 메시 예제 진행률](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>모범 사례

* 사용자가 쉽게 헤드를 빈 공간으로 이동하고 컨텍스트를 잃을 수 있기 때문에 진행률 표시에 밀집하거나 [태그를](billboarding-and-tag-along.md) 붙입니다. 사용자가 아무것도 볼 수 없는 경우 앱이 충돌하는 것처럼 보일 수 있습니다. 스트리밍 및 태그는 진행률 프리팹에 기본 제공되어 있습니다.
* 사용자에게 발생하는 상황에 대한 상태 정보를 항상 제공하는 것이 좋습니다. 진행률 프리팹은 상태 제공을 위한 Windows 표준 링 형식 진행률 등 다양한 비주얼 스타일을 제공합니다. 진행률 스타일을 앱 브랜드에 맞추려면 애니메이션과 함께 사용자 지정 메시를 사용할 수도 있습니다.

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity용 MRTK(Mixed Reality Toolkit)의 진행률 표시기

* [MRTK - 진행률 표시기 프리팹](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK - 장면 전환 서비스](/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


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