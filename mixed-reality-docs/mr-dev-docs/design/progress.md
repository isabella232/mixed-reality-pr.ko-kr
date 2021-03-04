---
title: 진행률 표시
description: 진행률 컨트롤이 혼합 현실 앱에서 장기 실행 작업이 진행 되 고 있음을 사용자에 게 피드백을 제공 하는 방법을 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 컨트롤, ui, ux, 진행률 표시기, 혼합 현실 헤드셋, windows Mixed Reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f323559c9a50a6f01636f0aba0bddc93b547125b
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759849"
---
# <a name="progress-indicator"></a>진행률 표시기

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

진행률 컨트롤은 장기 실행 작업이 진행 중임을 피드백을 제공 합니다. 진행률 표시기가 표시 되 면 사용자는 대기 시간을 볼 수 있으며 앱과 상호 작용할 수 없습니다.

<br>

---

## <a name="types-of-progress"></a>진행률 유형

발생 한 상황에 대 한 사용자 정보를 제공 하는 것이 중요 합니다. 혼합 현실에서는 앱이 좋은 시각적 피드백을가지고 있지 않은 경우 물리적 환경이 나 개체에 의해 사용자가 쉽게 무시 수 있습니다. 데이터를 로드 하거나 장면을 업데이트 하는 경우와 같이 몇 초 정도 걸리는 경우 시각적 표시기를 표시 하는 것이 좋습니다. 작업이 진행 중인 사용자를 표시 하는 두 가지 옵션은 **진행률 표시줄이** 나 **진행 링** 입니다.

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>진행률 표시줄<br>
        진행률 표시줄에는 태스크의 완료율이 표시 됩니다. 기간이 알려진 작업 (활성화 상태의) 중에 사용 해야 하지만, 해당 진행률이 사용자의 앱 상호 작용을 차단 하지 않아야 합니다.<br>
        <br>
        *이미지: HoloLens의 진행률 표시줄 예*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens의 진행률 표시줄 예](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>진행률 링<br>
        진행률 링은 확정 되지 않은 상태 이며 작업이 완료 될 때까지 사용자 상호 작용이 차단 될 때 사용 해야 합니다.<br>
        <br>
        *이미지: HoloLens의 진행 링 예*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 장치의 진행 링 예](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>사용자 지정 개체의 진행률<br>
        사용자 지정 2D/3D 개체를 사용 하 여 진행률 컨트롤을 사용자 지정 하 여 앱의 개성 및 브랜드 id에 추가할 수 있습니다.<br>
        <br>
        *이미지: HoloLens의 사용자 지정 메시 예제를 사용 하 여 진행*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens의 사용자 지정 메시 예제로 진행](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>모범 사례

* 사용자가 자신의 헤드를 빈 공간으로 쉽게 이동 하 고 컨텍스트를 손실할 수 있으므로 [billboarding 또는 태그](billboarding-and-tag-along.md) 를 진행률 표시와 긴밀 하 게 구분 합니다. 사용자가 아무것도 확인할 수 없는 경우 앱이 손상 된 것 처럼 보일 수 있습니다. Billboarding 및 태그 동반은 Progress prefab에 기본 제공 됩니다.
* 항상 사용자에 게 발생 하는 상황에 대 한 상태 정보를 제공 하는 것이 좋습니다. 진행률 prefab 상태를 제공 하기 위한 Windows 표준 링 유형 진행률을 비롯 한 다양 한 비주얼 스타일을 제공 합니다. 응용 프로그램의 브랜드에 맞게 진행률 스타일을 조정 하려는 경우 애니메이션으로 사용자 지정 메시를 사용할 수도 있습니다.

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 용 MRTK (Mixed Reality Toolkit)의 진행률 표시기

* [MRTK-진행률 표시기 prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK-장면 전환 서비스](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/extensions/scene-transition-service.md)


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
