---
title: 손으로 가리키고 커밋
description: 혼합 현실 애플리케이션에서 제스처 지원을 위한 포인트 및 커밋 입력 모델의 기본 사항에 대해 알아봅니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 상호 작용, 디자인, HoloLens, 손, 원거리, 가리키고 커밋, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, 손 광선, 개체 조작, MRTK, Mixed Reality Toolkit, DoF
ms.openlocfilehash: 7cf3aa3dd77776fce00d45b0ec086bf1d2e8c06241fd4525276783c2abfd51d9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115194569"
---
# <a name="point-and-commit-with-hands"></a>손으로 가리키고 커밋

![커서](images/UX_Hero_HandRay.jpg)

손으로 가리키고 커밋은 멀리 떨어져 있는 2D 콘텐츠 및 3D 개체를 겨냥하고, 선택하고, 조작할 수 있는 입력 모델입니다. “원거리” 상호 작용 기법은 인간이 실제 세상과 자연스럽게 상호 작용하는 방식이 아니므로 혼합 현실에만 해당됩니다. 예를 들어, 슈퍼 영웅 영화인 *엑스맨* 에서 등장 인물 [매그니토](https://en.wikipedia.org/wiki/Magneto_(comics))는 멀리 떨어져 있는 물체를 손으로 조작할 수 있습니다. 이것은 사람이 실제로 할 수 있는 일이 아닙니다. HoloLens(AR)와 Mixed Reality(MR) 모두에서 실제 세계의 물리적 제약 조건을 없애기 위해 사용자에게 이러한 마법 같은 힘을 제공합니다. 재미있는 홀로그램 환경일 뿐만 아니라 사용자 상호 작용을 보다 효과적이고 효율적으로 만들어 줍니다.

## <a name="device-support"></a>디바이스 지원

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>입력 모델</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></td>
     <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
</tr>
<tr>
     <td>손으로 가리키고 커밋</td>
     <td>❌ 지원 안 됨</td>
     <td>✔️ 권장</td>
     <td>✔️ 권장</td>
</tr>
</table>


_"손으로 가리키고 커밋"_ 은 새로운 연결형 손 추적 시스템을 사용하는 새로운 기능 중 하나입니다. 이 입력 모델은 모션 컨트롤러를 사용한 몰입형 헤드셋의 기본 입력 모델이기도 합니다.

<br>

---

## <a name="hand-rays"></a>손 광선

HoloLens 2에서 사용자의 손바닥 중앙에서 나오는 손 레이를 만들었습니다. 이 레이는 손의 연장선으로 취급됩니다. 도넛 모양의 커서가 레이 끝에 연결되어 레이가 대상 개체와 교차하는 위치를 나타냅니다. 그런 다음, 커서가 닿는 개체는 손에서 제스처 명령을 받을 수 있습니다.

엄지손가락과 집게손가락을 통해 기본적인 제스처 명령이 트리거되면서 에어 탭 작업이 수행됩니다. 손 레이를 사용하여 가리키고 에어 탭을 사용하여 커밋함으로써, 사용자는 단추 또는 하이퍼링크를 활성화할 수 있습니다. 좀 더 복잡한 제스처의 경우, 떨어진 위치에서 웹 콘텐츠를 탐색하고 3D 개체를 조작할 수 있습니다. 손 레이의 시각적 디자인은 아래 설명된 것처럼 이러한 가리키고 커밋 상태에도 대응해야 합니다. 

:::row:::
    :::column:::
        ![손 광선 가리키기](images/hand-rays-pointing.jpg)<br>
        **가리키는 상태**<br>
        *가리키기* 상태에서 레이는 대시이고 커서는 도넛 모양입니다.
    :::column-end:::
    :::column:::
        ![손 광선 커밋](images/hand-rays-commit.jpg)<br>
        **커밋 상태**<br>
        *커밋* 상태에서 레이는 실선으로 바뀌고 커서는 점으로 축소됩니다.
    :::column-end:::
:::row-end:::

<br>

---

## <a name="transition-between-near-and-far"></a>근거리 및 원거리 간 전환

"집게손가락으로 가리키기"와 같은 특정 제스처를 사용하여 광선을 전달하는 대신 사용자의 손바닥 중앙에서 광선이 발사되도록 설계했습니다. 이러한 방식으로 손가락을 모아서 잡기 같은 더 섬세한 제스처를 위한 Five Fingers를 발표하고 예약했습니다. 이 디자인에서는 근거리 및 원거리 상호 작용 모두에 동일한 손 제스처를 사용하는 한 가지 심리 모델만 만듭니다. 즉, 다른 거리에 있는 개체를 조작하는 데 동일한 잡기 제스처를 사용할 수 있습니다. 레이 호출은 다음과 같이 자동으로 진행되며 근접성을 기준으로 합니다.

:::row:::
    :::column:::
        ![근거리 조작](images/transition-near-manipulation.jpg)<br>
        **근거리 조작**<br>
        개체가 팔을 뻗어 닿을 수 있는 거리(약 50cm) 안에 있는 경우 근거리 상호 작용을 위해 레이가 자동으로 해제됩니다.
    :::column-end:::
    :::column:::
        ![원거리 조작](images/transition-far-manipulation.jpg)<br>
        **원거리 조작**<br>
        개체가 50cm보다 더 멀리 떨어져 있으면 레이가 켜집니다. 이러한 전환은 원활하고 매끄럽게 진행되어야 합니다.
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>2D 슬레이트 상호 작용

2D 슬레이트는 웹 브라우저와 같은 2D 앱 콘텐츠를 호스트하는 홀로그램 컨테이너입니다. 2D 슬레이트와 먼 거리에서 상호 작용할 경우의 기본적인 개념은 손 광선을 사용하여 타깃팅하고 에어 탭을 사용하여 선택하는 것입니다. 손 레이로 타기팅한 후에는 에어 탭을 수행하여 하이퍼링크 또는 단추를 트리거할 수 있습니다. 한 손으로 “에어 탭하고 끌기”를 수행하여 슬레이트 콘텐츠를 위아래로 스크롤할 수 있습니다. 두 손으로 에어 탭을 수행하고 끄는 상대적 동작으로 슬레이트 콘텐츠를 확대 및 축소할 수 있습니다.

손 레이가 모서리와 가장자리를 직접 향하게 하면 가장 가까운 조작 어포던스가 표시됩니다. “잡기 및 끌기” 조작 어포던스에서 사용자는 모서리 어포던스를 통해 균일하게 크기를 조정하고, 가장자리 어포던스를 통해 슬레이트를 재배치할 수 있습니다. 2D 슬레이트의 맨 위에 있는 홀로바를 잡아서 끌면 전체 슬레이트를 이동할 수 있습니다.

:::row:::
    :::column:::
       ![2D 슬레이트 상호 작용 클릭](images/2d-slate-interaction-click.jpg)<br>
       **클릭**<br>
    :::column-end:::
    :::column:::
       ![2D 슬레이트 상호 작용 스크롤](images/2d-slate-interaction-scroll.jpg)<br>
        **스크롤**<br>
    :::column-end:::
    :::column:::
       ![2D 슬레이트 상호 작용 확대/축소](images/2d-slate-interaction-zoom.jpg)<br>
       **확대/축소**<br>
    :::column-end:::
:::row-end:::

<br>

**2D 슬레이트 조작의 경우**<br>

* 사용자는 모서리 또는 가장자리를 손 레이로 가리켜 가장 가까운 조작 어포던스를 표시합니다. 
* 사용자는 어포던스에 조작 제스처를 적용하여 모서리 어포던스를 통해 균일하게 크기를 조정하고, 가장자리 어포던스를 통해 슬레이트를 재배치할 수 있습니다. 
* 2D 슬레이트의 맨 위에 있는 홀로바에 조작 제스처를 적용하여 전체 슬레이트를 이동할 수 있습니다.<br>

<br>

---

## <a name="3d-object-manipulation"></a>3D 개체 조작

직접 조작에서 사용자는 어포던스 기반 조작 및 비어포던스 기반 조작의 두 가지 방법으로 3D 개체를 조작할 수 있습니다. 가리키기 및 커밋 모델에서 사용자는 손 광선을 통해 정확히 동일한 작업을 수행할 수 있습니다. 추가 학습이 필요하지 않습니다.<br>

### <a name="affordance-based-manipulation"></a>어포던스 기반 조작

사용자는 손 광선을 사용하여 경계 상자 및 조작 어포던스를 가리키고 표시합니다. 사용자는 경계 상자에 조작 제스처를 적용하여 전체 개체를 이동하고, 가장자리 어포던스를 적용하여 회전하고, 모서리 어포던스를 적용하여 균일하게 크기를 조정할 수 있습니다. <br>

:::row:::
    :::column:::
       ![3D 개체 조작 원거리 이동](images/3d-object-manipulation-far-move.jpg)<br>
       **이동**<br>
    :::column-end:::
    :::column:::
       ![3D 개체 조작 원거리 회전](images/3d-object-manipulation-far-rotate.jpg)<br>
        **회전**<br>
    :::column-end:::
    :::column:::
       ![3D 개체 조작 원거리 배율](images/3d-object-manipulation-far-scale.jpg)<br>
       **크기 조정**<br>
    :::column-end:::
:::row-end:::

### <a name="non-affordance-based-manipulation"></a>비어포던스 기반 조작

사용자가 직접 손 광선으로 가리켜 경계 상자를 표시한 다음, 조작 제스처를 직접 적용합니다. 한 손을 사용할 경우 개체의 변환 및 회전은 손의 동작 및 방향과 연결됩니다. 두 손을 사용할 경우 두 손의 상대적 동작에 따라 변환, 크기 조정 및 회전할 수 있습니다.<br>

<br>

---

## <a name="instinctual-gestures"></a>직관적 제스처

가리키고 커밋을 위한 직관적 제스처 개념은 [손을 사용한 직접 조작](direct-manipulation.md)의 개념과 유사합니다. 사용자가 3D 개체에 대해 수행해야 하는 제스처는 UI 어포던스의 디자인에 따라 유도됩니다. 예를 들어, 사용자는 다섯 손가락을 모두 사용해서 더 큰 개체를 잡을 수도 있지만, 작은 제어점이 사용자가 엄지손가락과 집게손가락을 모으도록 유도할 수 있습니다.

:::row:::
    :::column:::
       ![직관적 제스처 원거리 소형 개체](images/instinctual-gestures-far-smallobject.jpg)<br>
       **소형 개체**<br>
    :::column-end:::
    :::column:::
       ![직관적 제스처 원거리 중형 개체](images/instinctual-gestures-far-mediumobject.jpg)<br>
        **중형 개체**<br>
    :::column-end:::
    :::column:::
       ![직관적 제스처 원거리 대형 개체](images/instinctual-gestures-far-largeobject.jpg)<br>
       **대형 개체**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>손과 6 DoF 컨트롤러 간의 대칭 디자인 

Mixed Reality 포털(MRP)에 원거리 상호 작용을 위한 가리키고 커밋이라는 개념이 만들어지고 정의되었습니다. 이 시나리오에서 사용자가 몰입형 헤드셋을 쓰고 모션 컨트롤러를 통해 3D 개체와 상호 작용합니다. 모션 컨트롤러는 멀리 떨어진 개체를 가리키고 조작하기 위해 레이를 보냅니다. 다른 작업을 추가로 커밋하기 위한 단추가 컨트롤러에 제공됩니다. 광선의 상호 작용 모델을 적용하고 양손에 연결합니다. 이 대칭 디자인에서 MRP에 친숙한 사용자는 HoloLens 2를 사용할 때 먼 거리 가리키기 및 조작을 위해 다른 상호 작용 모델을 학습할 필요가 없으며, 그 반대의 경우도 마찬가지입니다.    

:::row:::
    :::column:::
        ![컨트롤러 사용 광선의 대칭 디자인](images/symmetric-design-for-rays-controllers.jpg)<br>
        **컨트롤러 광선**<br>
    :::column-end:::
    :::column:::
        ![손을 사용한 광선의 대칭 디자인](images/symmetric-design-for-rays-hands.jpg)<br>
        **손 광선**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity용 MRTK(Mixed Reality Toolkit)의 손 광선

기본적으로 MRTK는 셸의 시스템 손 광선과 동일한 시각적 상태의 손 광선 prefab([DefaultControllerPointer. prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers))를 제공합니다. MRTK 입력 프로필의 포인터 아래에 할당됩니다. 몰입형 헤드셋에서 동일한 광선이 모션 컨트롤러에 사용됩니다.

* [MRTK - 포인터 프로필](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [MRTK - 입력 시스템](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [MRTK - 포인터](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a>참고 항목

* [수동으로 직접 조작](direct-manipulation.md)
* [응시 및 커밋](gaze-and-commit.md)
* [손 - 직접 조작](direct-manipulation.md)
* [손 - 제스처](gaze-and-commit.md#composite-gestures)
* [Instinctual 상호 작용](interaction-fundamentals.md)