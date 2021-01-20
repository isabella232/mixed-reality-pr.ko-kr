---
title: 시작 제스처
description: 시작 제스처를 사용 하 여 HoloLens 및 Windows Mixed Reality 모던 헤드셋의 시작 메뉴를 호출 하는 방법에 대해 알아봅니다.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 혼합 현실, 제스처, 상호 작용, 디자인, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 블 룸
ms.openlocfilehash: d0f3bd81cab945a01a523806ebaf4546752d74c1
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583233"
---
# <a name="start-gesture"></a>시작 제스처

시작 제스처는 시작 메뉴를 호출 하는 데 사용 되는 손 제스처입니다. 이는 키보드에서 Windows 키를 누르는 것과 동일한 기능입니다. Xbox의 Xbox 버튼 또는 모던 헤드셋 동작 컨트롤러의 Windows 단추입니다. 상호 작용을 디자인할 때 충돌을 방지 하기 위해 각 혼합 현실 장치에서 예약 된 시스템 제스처에 특히 주의 해야 합니다.

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
        <td>손목 단추</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>아이 응시 및 야자수</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Bloom

"블 룸"는 모방 (꽃 벚꽃)의 기호화 된 제스처로 시작 메뉴를 HoloLens (첫 번째 gen)로 표시 하도록 설계 되었습니다. Footed 상호 작용, 사용 편의성 및 신속 하 게 회수할 수 있습니다. 제스처를 사용 하려면 야자나무를 함께 사용 하 여 손을 놓고 손가락을 확산 시켜 손을 여세요.

:::row:::
    :::column:::
        ![블 룸 닫기](images/bloom-close.png)<br>
        **1 단계: 쉽게 함께 팜 강화**<br>
    :::column-end:::
    :::column:::
        ![블 룸 열기](images/bloom-open.png)<br>
        **2 단계: 간편 하 게 확산 된 팜**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>시작 제스처

HoloLens 2에서는 블 룸 제스처를 사용자에 게 더 많은 instinctual 인 가상 손목 단추로 대체 했습니다. 사용자가 손목 단추를 표시 하 여 쉽게 접근 하 고 다른 손으로 누를 수 있습니다.

:::row:::
    :::column:::
        ![손목 단추 준비 완료](images/wrist-button-ready.png)<br>
        **1 단계: 손목 단추를 표시 합니다.**<br>
    :::column-end:::
    :::column:::
        ![손목 단추 누르기](images/wrist-button-press.png)<br>
        **2 단계: 손목 단추 누르기**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a>단방향 시작 제스처

> [!IMPORTANT]
> 한 번의 시작 제스처를 사용 하려면 다음을 수행 합니다.
>
> 1. 2019 년 11 월 업데이트 (빌드 18363.1039) 이상으로 업데이트 해야 합니다.
> 1. 눈동자 추적이 제대로 작동 하도록 장치에서 눈동자를 보정 해야 합니다. 표시 될 때 시작 아이콘 주위에 orbiting 점이 표시 되지 않는 경우 눈은 장치에서 보정 되지 않습니다.

한 번만 사용 하 여 시작 제스처를 사용할 수도 있습니다. 사용자를 향한 손을 잡고 내부 손목 **시작 아이콘** 을 살펴보세요. **아이콘을 눈에 유지 하면서** 엄지 단추와 인덱스 손가락을 함께 손가락으로 합니다.<br>
:::row:::
    :::column:::
        ![손목 단추 준비 완료](images/wrist-button-ready.png)<br>
        **1 단계: 손목 단추를 표시 합니다.**<br>
    :::column-end:::
    :::column:::
        ![손목 단추 손가락으로](images/wrist-button-pinch.png)<br>
        **2 단계: 단추를 누른 후 손가락으로 이동**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>참고 항목

* [Instinctual 상호 작용](interaction-fundamentals.md)
* [눈-응시](eye-tracking.md)
* [음성 입력 ](voice-input.md)