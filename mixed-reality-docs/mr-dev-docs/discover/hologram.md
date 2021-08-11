---
title: 홀로그램이란?
description: HoloLens를 사용 하면 전 세계에 표시 되는 조명 및 소리로 인 한 3 차원 holograms을 보고 상호 작용할 수 있습니다.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, holograms, 디자인, 상호 작용, 혼합 현실 헤드셋, Windows mixed reality 헤드셋, 확대 된 현실
ms.openlocfilehash: e028fe6180bded26263fa47feb5acefc94570222e43f10fe85db5adf90307844
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202118"
---
# <a name="what-is-a-hologram"></a>홀로그램이란?

HoloLens를 사용 하면 실제 개체와 같이 전 세계에 표시 되는 조명 및 소리로 구성 된 개체인 **holograms** 를 볼 수 있습니다. 홀로그램스는 [응시](../design/gaze-and-commit.md), [제스처](../design/gaze-and-commit.md#composite-gestures)및 [음성 명령](../design/voice-input.md)에 응답할 수 있습니다. 사용자를 중심으로 [실제 서피스와](../design/spatial-mapping.md) 상호 작용할 수도 있습니다. 홀로그램스은 전 세계의 일부인 디지털 개체입니다.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

## <a name="device-support"></a>디바이스 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>홀로그램</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a>홀로그램은 가볍고 소리로 구성 됩니다.

### <a name="light"></a>밝음

HoloLens [렌더링](../develop/platform-capabilities-and-apis/rendering.md) 되는 holograms는 사용자의 눈에 직접 holographic 프레임에 나타납니다. 빛을 전 세계에 추가 하는 홀로그램스 표시의 빛과 주변 세계의 빛이 모두 표시 되는 것을 의미 합니다. HoloLens는 조명을 추가 하는 덧셈 표시를 사용 하므로 검정 색이 투명 하 게 렌더링 됩니다. 

홀로그램스는 모양과 동작이 매우 다를 수 있습니다. 일부는 현실적인 및 반도체 이며, 다른 일부는 cartoonish 및 ethereal입니다. Holograms를 사용 하 여 사용자 환경에서 기능을 강조 표시 하거나 앱의 사용자 인터페이스에서이를 요소로 사용할 수 있습니다.

![홀로그램를 손으로 조작](images/hologram-hands-940px.jpg)

### <a name="sound"></a>소리

사용자 환경의 특정 장소에서 가져온 [소리](../design/spatial-sound.md)를 생성할 수도 홀로그램스. HoloLens에서 소리는 귀 바로 위에 있는 두 개의 스피커에서 제공 됩니다. Holographic 표시 하는 것과 동일 하 게, 스피커가 추가 되어 사용자 환경의 소리를 차단 하지 않고 새 소리를 도입 합니다.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>홀로그램을 사용자와 함께 전 세계 또는 태그에 배치할 수 있습니다.

홀로그램의 고정 위치가 있는 경우 전 세계의 해당 지점에 정확 하 게 [배치할](../design/coordinate-systems.md) 수 있습니다. 연습을 진행할 때 홀로그램은 실제 개체와 마찬가지로 전 세계에 따라 고정 된 상태로 표시 됩니다. [공간 앵커](../design/coordinate-systems.md#spatial-anchors) 를 사용 하 여 개체를 고정 하는 경우에는 나중에 다시 돌아올 때 시스템의 위치를 기억할 수 있습니다.

![소매 공간에서 Microsoft Dynamics 365 레이아웃을 사용 하는 두 남자](images/HLS19_retailLayoutHologram_001-940px.jpg)

대신 일부 holograms 사용자를 따릅니다. 사용자에 따라 자신을 배치 합니다. 사용자를 사용 하 여 홀로그램을 가져온 다음 다른 방에 들어온 후 벽에 놓을 수 있습니다.

**모범 사례**

* 일부 시나리오에서는 holograms가 쉽게 검색 가능 하거나 환경 전체에서 볼 때 표시 되어야 합니다. 이러한 종류의 위치에는 두 가지 상위 수준 방법이 있습니다. **표시-잠김** 및 **본문 잠김** 을 호출 해 보겠습니다.
   * 디스플레이 **잠금** 콘텐츠가 디스플레이 장치에 잠깁니다. 이러한 유형의 콘텐츠는 여러 사용자가 불편 하 게 하 고 "흔들기" 하려는 경우를 비롯 하 여 여러 가지 이유로 인해 복잡 합니다. 일반적으로 디자이너는 표시 잠금 콘텐츠를 방지 하는 것이 더 좋습니다.
   * **본문에서 잠긴** 콘텐츠는 훨씬 더 많은 기능을 제공할 수 있습니다. 본문 잠금은 3D 공간에서 사용자의 본문 또는 응시 벡터에 홀로그램을 표시 하는 경우입니다. 많은 경험을 통해 홀로그램은 사용자의 응시를 따르는 본문 잠금 동작을 채택 했습니다. 그러면 사용자가 해당 본문을 회전 하 고 홀로그램을 잃지 않고 공간을 이동할 수 있습니다. 지연 시간을 통합 하면 홀로그램 이동이 보다 자연스럽 게 느껴질 수 있습니다. 예를 들어 Windows Holographic OS의 일부 핵심 UI는 사용자가 헤드를 끄는 동안 gentle, 탄력적와 유사한 지연 시간에 사용자의 응시를 따르는 본문 잠금 변형을 사용 합니다.
* 일반적으로 헤드에서 약 1-2 미터 떨어진 편안 하 게 볼 때 홀로그램을 준비 합니다.
* 요소를 holographic 프레임에서 계속 사용 해야 하는 경우에는 요소를 드리프트 할 수 있으며, 사용자가 관점을 변경할 때 콘텐츠를 디스플레이의 한 쪽으로 이동 하는 것이 좋습니다. 자세한 내용은 [billboarding 및 태그 동반](../design/billboarding-and-tag-along.md) artilce를 참조 하세요.

**최적 영역에 holograms 두기-1.25 m에서 5 m 사이**

두 미터는 가장 최적의 보기 거리입니다. 1 측정기 보다 더 가까운 환경에서 성능이 저하 되기 시작 합니다. 1 미터 미만의 거리에서 holograms 정기적으로 이동 하는 것은 고정 holograms 보다 문제가 될 가능성이 높습니다. 콘텐츠를 너무 가까이 전환 하거나 페이드 아웃 하는 것이 좋습니다. 이렇게 하면 사용자가 불쾌 시청 환경으로 사용 하지 않아도 됩니다.

![사용자의 holograms를 배치 하는 데 가장 적합 한 거리입니다.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>홀로그램은 사용자 및 전 세계와 상호 작용 합니다.

홀로그램스는 빛과 소리를 위한 것이 아닙니다. 또한 전 세계의 활성 부분입니다. 홀로그램 및 제스처를 응시 하 고 홀로그램에서 팔 로우를 시작할 수 있습니다. 음성 명령을 제공 하 고 홀로그램은 회신할 수 있습니다.

![Microsoft HoloLens 2를 사용 하 여 바람 팜 개발 프로젝트에서 공동 작업을 하는 정부 유틸리티 작업자 그룹](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

홀로그램스 다른 곳에서 가능 하지 않은 개인 상호 작용을 사용 하도록 설정 합니다. HoloLens은 세계 어디에 있는지를 알 수 있기 때문에 holographic 문자는 눈에 직접 확인 하 고 대화를 시작할 수 있습니다.

홀로그램도 주변과 상호 작용할 수 있습니다. 예를 들어 테이블 위에 holographic 바운스 구슬을 삽입할 수 있습니다. 그런 다음 [공중 탭](../design/gaze-and-commit.md#composite-gestures)을 사용 하 여 구슬 바운스를 시청 하 고 테이블에 도달할 때 소리를 만듭니다.

홀로그램스 실제 개체에 의해 폐색 될 수도 있습니다. 예를 들어, holographic 문자는 외부의 도어를 살펴보고 벽 뒤에 있을 수 있습니다.

**Holograms와 실제 세계를 통합 하기 위한 팁**

* Gravitational 규칙에 맞춰 holograms 더 쉽게 이익은 수 있습니다. 예: holographic & dog를 공간에 부동으로 두지 않고 테이블의 vase에 배치 합니다.
* 대부분의 디자이너는 홀로그램을 보유 하 고 있는 표면에 "네거티브 그림자"를 만들어 더 이익은 holograms를 통합할 수 있는 것을 발견 했습니다. 홀로그램 주위에서 부드러운 광선을 만든 다음 광선에서 "그림자"를 빼서이를 수행 합니다. 소프트 광선은 실제 세계의 빛과 통합 됩니다. 섀도는 환경에서 홀로그램을 접지 하는 데 사용 됩니다.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a>홀로그램은 <br>다음을 수행할 수 있습니다.<br>
        Holographic 개발자는 2D 화면 및 전 세계의 창의적인 기능을 활용할 수 있습니다.<br><br>
        빌드 *를* 선택 하세요.
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![거실에서 Holographic 허수](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>다음 검색 검사점

사용자는이를 통해 설명 된 [검색](get-started-with-mr.md) 경험을 살펴보고 혼합 현실의 기본 사항을 살펴보세요. 이제 다음 기본 항목으로 계속 진행할 수 있습니다. 

> [!div class="nextstepaction"]
> [디자인 프로세스 확장](case-study-expanding-the-design-process-for-mixed-reality.md)