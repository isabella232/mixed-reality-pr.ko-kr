---
title: 홀로그램이란?
description: HoloLens 사용하면 주변 세계에 나타나는 3차원 홀로그램, 광원 및 소리로 구성된 개체를 보고 상호 작용할 수 있습니다.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 홀로그램, 디자인, 상호 작용, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 증강 현실이란?
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634334"
---
# <a name="what-is-a-hologram"></a>홀로그램이란?

HoloLens 사용하면 실제 개체처럼 주변 세계에 나타나는 광원과 소리로 구성된 개체인 **홀로그램을** 볼 수 있습니다. 홀로그램스 [응시,](../design/gaze-and-commit.md) [제스처](../design/gaze-and-commit.md#composite-gestures)및 음성 명령에 응답할 수 [있습니다.](../design/voice-input.md) 주위의 실제 [표면과](../design/spatial-mapping.md) 상호 작용할 수도 있습니다. 홀로그램스 전 세계의 일부인 디지털 개체입니다.

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

## <a name="a-hologram-is-made-of-light-and-sound"></a>홀로그램은 광원과 소리로 구성됩니다.

### <a name="light"></a>밝음

HoloLens [렌더링되는](../develop/platform-capabilities-and-apis/rendering.md) 홀로그램은 홀로그램 프레임에서 사용자의 눈 바로 앞에 나타납니다. 홀로그램스 세계에 조명을 추가합니다. 즉, 디스플레이의 광원과 주변 세계의 광원을 모두 볼 수 있습니다. HoloLens 조명을 추가하는 가감 표시를 사용하므로 검은색이 투명하게 렌더링됩니다. 

홀로그램스 모양과 동작이 매우 다를 수 있습니다. 일부는 현실적이고 견고하며, 다른 일부는 설사하고 은밀합니다. 홀로그램을 사용하여 사용자 환경의 기능을 강조 표시하거나 앱의 사용자 인터페이스에서 요소로 사용할 수 있습니다.

![홀로그램을 조작하는 손](images/hologram-hands-940px.jpg)

### <a name="sound"></a>소리

홀로그램스 환경의 특정 위치에서 제공되는 것처럼 보이는 [소리를](../design/spatial-sound.md)생성할 수도 있습니다. HoloLens 소리는 음면 바로 위에 있는 두 개의 스피커에서 제공됩니다. 홀로그램 디스플레이와 마찬가지로, 화자는 가감성이 있으며 사용자 환경에서 소리를 차단하지 않고 새로운 소리를 도입합니다.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>홀로그램을 세계에 배치하거나 태그를 함께 배치할 수 있습니다.

홀로그램의 고정 위치가 있는 경우 전 세계의 해당 지점에 정확하게 [배치할](../design/coordinate-systems.md) 수 있습니다. 진행하면서 홀로그램은 실제 개체처럼 주변 세계에 따라 고정된 것처럼 나타납니다. [공간 앵커를](../design/coordinate-systems.md#spatial-anchors) 사용하여 개체를 고정하는 경우 나중에 다시 돌아올 때 시스템에서 개체를 남겨둔 위치도 기억할 수 있습니다.

![소매 공간에서 Microsoft Dynamics 365 레이아웃을 사용하는 두 명의 남성](images/HLS19_retailLayoutHologram_001-940px.jpg)

일부 홀로그램은 사용자를 대신 따릅니다. 사용자에 따라 자신을 배치합니다. 홀로그램을 가져온 다음, 다른 방으로 들어가면 벽 위에 놓도록 선택할 수 있습니다.

**모범 사례**

* 일부 시나리오에서는 홀로그램을 환경 전체에서 쉽게 검색하거나 볼 수 있다고 요구합니다. 이러한 종류의 위치에는 두 가지 높은 수준의 접근 방식이 있습니다. 표시 잠금 및 **본문이** **잠긴** 를 호출해 보겠습니다.
   * **디스플레이 잠금** 콘텐츠가 디스플레이 디바이스에 잠겨 있습니다. 이러한 유형의 콘텐츠는 여러 가지 이유로 인해 까다로운데, 여기에는 많은 사용자가 불편하게 만들고 "흔든다"고 하는 "불연연한 느낌"이 포함됩니다. 일반적으로 디자이너는 디스플레이 잠금 콘텐츠를 방지하는 것이 더 낫습니다.
   * **본문이 잠긴** 콘텐츠는 훨씬 더 용인할 수 있습니다. 본문 잠금은 3D 공간에서 홀로그램을 사용자의 본문 또는 응시 벡터에 테더링하는 경우입니다. 많은 경험에서 홀로그램이 사용자의 응시를 따르는 신체 잠금 동작을 채택하여 사용자가 홀로그램을 손실하지 않고도 자신의 신체를 회전하고 공간을 이동할 수 있습니다. 지연을 통합하면 홀로그램 이동이 더 자연스럽게 느낄 수 있습니다. 예를 들어 Windows Holographic OS의 일부 핵심 UI는 사용자가 머리가 바뀌는 동안 탄력적인 탄력적 지연으로 사용자의 응시를 따르는 신체 잠금의 변형을 사용합니다.
* 홀로그램을 일반적으로 머리에서 약 1-2미터 떨어진 보기 거리에 배치합니다.
* 요소가 홀로그램 프레임에 지속적으로 있어야 하는 경우 드리프트할 수 있도록 허용하거나, 사용자가 보기를 변경할 때 콘텐츠를 디스플레이의 한 쪽으로 이동하는 것이 좋습니다. 자세한 내용은 스트리밍 [및 태그 따라](../design/billboarding-and-tag-along.md) 아티실을 참조하세요.

**최적의 영역에 홀로그램 배치 - 1.25m에서 5m 사이**

2미터는 가장 최적의 보기 거리입니다. 1미터에 가까워지면 환경이 저하됩니다. 1미터 미만의 거리에 있는 경우 정기적으로 깊이 이동하는 홀로그램은 고정 홀로그램보다 문제가 될 가능성이 높습니다. 콘텐츠가 너무 가까워지면 콘텐츠를 정상적으로 클리핑하거나 페이드 아웃하는 것이 좋습니다. 따라서 사용자가 보기가 너무 빠릅니다.

![사용자로부터 홀로그램을 배치하기 위한 최적의 거리입니다.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>홀로그램은 사용자 및 사용자 세계와 상호 작용합니다.

홀로그램스 조명과 소리에만 국한되지 않습니다. 또한 전 세계에서 활동적인 부분입니다. 홀로그램과 제스처를 손으로 응시하면 홀로그램이 따라오기 시작할 수 있습니다. 음성 명령을 제공하면 홀로그램이 응답할 수 있습니다.

![Microsoft HoloLens 2를 사용하여 풍력 발전 단지 개발 프로젝트에서 공동 작업하는 정부 유틸리티 작업자 그룹](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

홀로그램스 다른 곳에서는 불가능한 개인 상호 작용을 사용하도록 설정합니다. HoloLens 세계 어디에 있는지 알고 있기 때문에 홀로그램 문자는 눈에서 직접 보고 대화를 시작할 수 있습니다.

홀로그램은 주변 환경과 상호 작용할 수도 있습니다. 예를 들어 홀로그램 바운드 볼을 테이블 위에 배치할 수 있습니다. 그런 [다음, 에어 탭을](../design/gaze-and-commit.md#composite-gestures)통해 공이 바운드되는 것을 보고 테이블에 적중될 때 소리를 내립니다.

홀로그램스 실제 개체에 의해 폐색될 수도 있습니다. 예를 들어 홀로그램 문자는 문과 벽 뒤에서 보이지 않는 것을 볼 수 있습니다.

**홀로그램과 실제 세계를 통합하기 위한 팁**

* 초대형 규칙에 맞게 조정하면 홀로그램을 더 쉽게 관련시키고 더 안정적으로 만들 수 있습니다. 예: 홀로그램 개를 공간에 부동하지 않고 테이블에 꽃병을 & 지면에 홀로그램 개를 놓습니다.
* 많은 디자이너는 홀로그램이 있는 표면에 "음의 그림자"를 만들어 더 신뢰할 수 있는 홀로그램을 통합할 수 있음을 발견했습니다. 홀로그램 주위에 부드러운 후광을 만든 다음, 광선에서 "그림자"를 빼서 이 작업을 수행합니다. 소프트 후광은 실제 세계의 광원과 통합됩니다. 그림자는 환경에서 홀로그램을 접지하는 데 사용됩니다.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a>홀로그램이란? <br>다음을 기대할 수 있습니다.<br>
        홀로그램 개발자는 2D 화면과 주변 세계로 독창함을 끊을 수 있는 능력을 갖습니다.<br><br>
        무엇을 *빌드하시겠습니까?*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![회의실의 홀로그램 허수 세계](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>다음 검색 검사점

앞에서 설명한 [검색 여정을](get-started-with-mr.md) 진행하면서 Mixed Reality 기본 사항들을 탐색하고 있습니다. 이제 다음 기본 항목으로 계속 진행할 수 있습니다. 

> [!div class="nextstepaction"]
> [디자인 프로세스 확장](case-study-expanding-the-design-process-for-mixed-reality.md)