---
title: 시작 제스처
description: 시작 제스처를 사용하여 HoloLens 시작 메뉴를 호출하고 몰입형 헤드셋을 Windows Mixed Reality 방법을 알아봅니다.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Mixed Reality, 제스처, 상호 작용, 디자인, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 간
ms.openlocfilehash: f3ad9309c7232f20a25060b1d98d7374272ceea00f24be18d7263b8ec7002fb3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213743"
---
# <a name="start-gesture"></a>시작 제스처

시작 제스처는 시작 메뉴를 호출하는 데 사용되는 손 제스처입니다. 키보드의 Windows 키, Xbox 컨트롤러의 Xbox 단추 또는 몰입형 헤드셋 모션 컨트롤러의 Windows 단추를 누르는 것과 같습니다. 상호 작용을 디자인할 때 충돌을 방지하기 위해 각 Mixed Reality 디바이스에서 예약된 시스템 제스처에 특히 주의해야 합니다.

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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>Bloom</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>눌리기 단추</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>시선 응시 및 손만 쌓기 손가락 모으기</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Bloom

HoloLens(1세대)의 시작 메뉴를 불러 오도록 "피감"을 디자인했습니다. 이 메뉴는 꽃 꽃들을 모방하는 기호 제스처입니다. 확실히 발이 있는 상호 작용, 사용하기 쉽고 빠르게 회수하는 것이 고유합니다. 제스처를 사용하려면 손끝과 손끝을 함께 누른 다음 손가락을 펼쳐 손을 엽니다.

:::row:::
    :::column:::
        ![개감 닫기](images/bloom-close.png)<br>
        **1단계: 손끝으로 손끝 위로**<br>
    :::column-end:::
    :::column:::
        ![개나리 열기](images/bloom-open.png)<br>
        **2단계: 손끝이 분산된 손끝 위로**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>시작 제스처

HoloLens 2 사용자가 더 직관적인 가상 버피 단추로 개화 제스처를 대체했습니다. 사용자에게 단추를 표시하면 직관적으로 단추를 눌렀다가 다른 손으로 누를 수 있습니다.

:::row:::
    :::column:::
        ![준비 완료된 단추를 눌라 주세요.](images/wrist-button-ready.png)<br>
        **1단계: 손아라운 단추를 표시하기 위한 손만 모양**<br>
    :::column-end:::
    :::column:::
        ![압정 단추 누르기](images/wrist-button-press.png)<br>
        **2단계: 단추 누르기**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a>한 손 시작 제스처

> [!IMPORTANT]
> 한 손 시작 제스처를 사용하려면 다음을 수행합니다.
>
> 1. 2019년 11월 업데이트(빌드 18363.1039) 이상으로 업데이트해야 합니다.
> 1. 시선 추적이 올바르게 작동하려면 장치에서 눈을 보정해야 합니다. 시작 아이콘을 볼 때 아이콘 주변에 회전하는 점이 보이지 않으면 장치에서 눈이 보정되지 않은 것입니다.

한 손으로만 시작 제스처를 사용할 수도 있습니다. 손만을 향하여 손을 내밀고 내부 속의 **시작 아이콘을** 보세요. **아이콘을 주시하면서** 엄지손가락과 집게손가락을 함께 모읍니다.<br>
:::row:::
    :::column:::
        ![준비 완료된 단추를 눌라 주세요.](images/wrist-button-ready.png)<br>
        **1단계: 손아라운 단추를 표시하기 위한 손만 모양**<br>
    :::column-end:::
    :::column:::
        ![섞기 단추 손가락 모으기](images/wrist-button-pinch.png)<br>
        **2단계: 단추를 응시한 다음, 손가락 모으기**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>추가 정보

* [Instinctual 상호 작용](interaction-fundamentals.md)
* [시선 응시](eye-tracking.md)
* [음성 입력 ](voice-input.md)