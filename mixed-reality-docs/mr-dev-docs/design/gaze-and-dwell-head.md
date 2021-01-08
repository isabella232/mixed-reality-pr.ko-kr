---
title: 헤드 게이즈(head-gaze) 및 드웰(dwell)
description: 일반적인 시나리오 및 디자인 원칙을 포함 하 여 헤드 응시 및 지속 입력 모델의 개요를 시작 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: 혼합 현실, 응시, 지속, 상호 작용, 디자인, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, 혼합 현실 도구 키트, ux, 지침, 목록 뷰
ms.openlocfilehash: 2bfd984a466c1ccd3913e889ca57663800f46380
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007083"
---
# <a name="head-gaze-and-dwell"></a>헤드 게이즈(head-gaze) 및 드웰(dwell)

손에 도구와 파트가 있으면 제스처가 어렵거나 불가능할 수 있습니다. 제스처와 같은 음성 명령은 특정 상황(예: 과도하게 소리가 큰 상황)에서 불안정할 수 있습니다. 또한 음성을 사용하여 컴퓨터를 제어하는 것이 전체적으로 일반적이지는 않지만 보편화되고 있는 것은 확실합니다. 헤드 게이즈(head-gaze) 및 드웰(dwell)은 HoloLens에서 헤드업 및 핸즈프리 작업을 수행하기에 가장 친숙하고 마스터하기 편한 메커니즘을 제공합니다. 또한 헤드 게이즈(head-gaze) 및 드웰(dwell)은 운영 환경에서 소음 간섭이나 무음 제약과 상관없이 100% 안정적입니다.

## <a name="scenarios"></a>시나리오

헤드-응시 및 유지는 사용자가 다른 작업을 사용 하는 시나리오에서 유용 합니다. 이 기능은 음성이 100% 안정적이 아니거나 환경 또는 소셜 제약 조건으로 인해 사용할 수 있는 경우에도 유용 합니다. HoloLens를 착용하고 자동차 엔진을 수리하는 동안 참조 정보를 오버레이하는 경우가 좋은 예입니다. 엔진 칸에 기대고 있는 몸을 지탱하거나 도구를 다루느라 손을 사용할 수 없습니다. 차고 공간에서는 연장이 계속 윙윙거리면서 소리를 내기 때문에 시끄러워서 음성 명령을 실행하기 어렵습니다. 헤드-응시 및 유지를 통해 HoloLens를 사용 하는 사람은 자신의 워크플로를 중단 하지 않고 자신 들이 참조 자료를 안전 하 게 탐색할 수 있습니다. 

## <a name="device-support"></a>디바이스 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>입력 모델</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>헤드 게이즈(head-gaze) 및 드웰(dwell)</td>
        <td>✔️ 권장</td>
        <td>✔️ 권장</td>
        <td>✔️ 권장</td>
    </tr>
</table>


## <a name="design-principles"></a>디자인 원칙

**“과도한 응시” 방지**

헤드 게이즈(head-gaze) 및 드웰(dwell)에는 직관적인 시각 피드백이 필요하지만 피드백이 너무 많으면 불안정한 상태를 유발할 수 있습니다. 사용자 의견을 통해 사용자에 게 대상에 대 한 정보를 알려 주지만 자신의 의도에 대해 자동 선택을 하지 않습니다. 텍스트, 아이콘 및 레이블을 읽을 때를 선택 하기 전에 사용자에 게 정보를 입력할 수 있는 시간을 제공 해야 합니다.
    
**최적의 속도 구하기**
    
드웰(dwell) 상호 작용은 탐색의 영향력에 따라 타이머가 다를 수 있습니다. 사용 빈도가 높은 함수는 일반적으로 채우기 시간이 빠른 것이 유용하고 중대한 함수는 채우기 시간이 긴 것이 유용합니다. 채우기 효과를 사용하여 타이머를 표시하면, 채우기 색상의 애니메이션 곡선이 채우기 시간이 빠른 느낌에 긍정적인 영향을 줄 수 있습니다. 빠른/중간/느린 채우기 속도 재정의 중에서 사용자가 결정할 수 있도록 고려하는 것이 필요합니다.
    
**요요 효과 절대 금지**

Yo – yo 효과는 콘텐츠 배치 및 헤드-응시 컨트롤이 반복적으로 조회를 수행 하는 경우 발생 하는 불쾌 한 헤드 이동 패턴입니다. 예를 들어 목록의 맨 아래에 있는 헤드-응시 및 유지 단추를 사용 하 여 탐색을 시작 하 고, 결과를 조회 하 고, 유지 하는 등의 작업을 반복 합니다. 결과적으로 발생 하는 패턴은 불편 하므로, 더 작은 앞뒤로 필요로 하는 중앙 위치에 탐색 컨트롤을 배치 하는 것이 좋습니다. 효과를 바탕으로 지속 단추를 배치 하는 것은 편안 하 게 중요 합니다.
초
<br>

---

## <a name="ux-guidelines-and-best-practices"></a>UX 지침 및 모범 사례

### <a name="target-sizes"></a>대상 크기

쉽게 액세스할 수 있도록 헤드 응시 및 유지 대상은 편안 하 게 볼 수 있을 만큼 충분히 커야 하며 지정 된 시간 동안 대상에서 한 개의 헤드를 보유 하 고 있습니다. 가장 편안한 환경을 구현 하기 위해 최소 대상 크기인 2도를 권장 합니다. 

### <a name="visual-feedback"></a>시각적 피드백

드웰(dwell) 타이머를 나타내기 위해 방사형 채우기를 사용하는 경우에는 단추 가운데에서 시작합니다. 일관된 응답이 서로 다른 단추의 모두 다른 방향보다는 덜 혼란스럽습니다. 

  * 이 규칙은 방향 상호 작용 (예: nav up/down/left/right 등)의 경우 손상 될 수 있습니다. 예를 들어, Microsoft Dynamics 365 가이드의 경우 예외적으로 다음/뒤로가 왼쪽에서 오른쪽으로 채워집니다.
  * 단추를 설정/해제 하는 등의 경우에는 바깥쪽에서 방사형 채우기를 반전 하는 것이 좋습니다. 단추 누르기와 반대되는 느낌은 유지하기 좋은 시각 패턴입니다. 

### <a name="progressive-disclosure"></a>점진적 공개

점진적인 공개란 상호 작용의 각 단계에 해당하는 세부 정보만 표시하는 것을 의미합니다. 유지의 경우 유지 대상이 강조 표시에서 표시 됩니다 (예: 목록 컨트롤).

 ### <a name="oversized-targets"></a>너무 큰 대상

드웰(dwell) 지역은 Microsoft Dynamics 365 가이드의 뒤로 단추처럼, 사용하기 쉽도록 비활성 아이콘보다 클 수 있습니다.

### <a name="prevent-flickering-with-delayed-feedback"></a>피드백 지연으로 인한 깜박임 방지

다른 사람이 드웰(dwell) 대상을 지나칠 때 깜박이지 않도록, 시각 피드백을 시작하기 전에 짧은 지연을 사용합니다.
* 자주 상호 작용 하는 단추의 경우 응용 프로그램이 반응 하지 않도록 짧은 지연 시간을 유지 합니다.
* 자주 상호 작용 하는 단추의 경우 twitchy 인터페이스를 방지 하는 데 시간이 더 오래 걸릴 수 있습니다.

<br>

---

## <a name="ui-patterns"></a>UI 패턴

### <a name="high-frequency-buttons"></a>높은 빈도 단추

:::row:::
    :::column:::
        높은 빈도 단추는 응용 프로그램 전체에서 일반적으로 사용 되는 단추입니다. Microsoft Dynamics 365 가이드의 다음 및 뒤로 단추가 좋은 예입니다.<br>
        <br>
        **권장 사항**<br>
  * 높은 빈도 단추가 크고, head-응시로 더 쉽게 적중 됩니다.
  * 인체 공학 덕분을 방지 하려면 눈에 가까운 높이를 유지 하세요.<br>
        <br>
*이미지: Microsoft Dynamics 365 가이드 다음 단추*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 가이드 다음 단추](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>낮은 빈도 단추

빈도가 낮은 단추는 응용 프로그램 전체에서 정기적으로 상호 작용 하지 않는 단추입니다. 설정 메뉴에 액세스하는 단추 또는 모든 작업을 지우는 단추가 좋은 예입니다.

* 이러한 단추는 우발적인 활성화를 피하기 위해 빈번한 헤드 게이즈(head-gaze) 경로에서 멀리 두는 것이 좋습니다. 

<br>

---

### <a name="confirmations"></a>확인

:::row:::
    :::column:::
        작업의 요금 청구, 작업 삭제 또는 긴 프로세스 시작과 같은 심각한 영향을 주는 경우 개인이 단추를 선택 하는 것을 확인 하는 것이 유용 합니다.<br>
        <br>
        **권장 사항**<br>
  * 주요 단추의 선택을 강조 표시합니다.
  * 선택 강조 표시와 동시에 드웰(dwell) 대상을 나타냅니다.
  * 보조 단추의 경우 헤드 게이즈(head-gaze) 시 드웰(dwell) 대상을 드러납니다.<br>
        <br>
*이미지: Microsoft Dynamics 365 가이드 확인 대화 상자*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 가이드 확인 대화 상자](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>토글 단추

토글 단추를 사용하려면 다소 미묘한 논리가 제대로 작동해야 합니다. 설정/해제 단추를 활성화 하 고 활성화 하는 경우 단추를 종료 하 고를 반환 하 여 유지 논리를 다시 시작 해야 합니다. 가능한 단추가 활성 상태와 비활성 상태를 명확 하 게 유지 하는 것이 중요 합니다. 

<br>

---

### <a name="list-views"></a>목록 보기

:::row:::
    :::column:::
        목록 뷰는 헤드-응시 및 지속 입력에 대 한 특정 챌린지를 제공 합니다. 사용자는 유지 목표를 tiptoe 해야 하는 것과 같은 느낌 없이 콘텐츠를 스캔할 수 있습니다.<br>
        <br>
**권장 사항**<br>
  * 헤드 gazed 때 전체 행을 강조 표시 하 되, head-응시가 특정 유지 목표에 있지 않으면 유지를 시작 하지 않습니다.
  * 시각적 노이즈를 줄이기 위해 행이 강조 표시 된 경우에만 유지 대상을 표시 합니다.
  * 유지 대상의 위치와 명확 하 게 일치 해야 합니다.
  * 반복적인 UI를 방지 하기 위해 모든 유지 대상을 한 번에 표시 하지 않습니다.
  * 가능한 한 자주 같은 패턴을 재사용 하 여 UX를 파악 합니다.<br>
        <br>
*이미지: Microsoft Dynamics 365 가이드 목록*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 가이드 목록](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>참조

* [응시 및 커밋](gaze-and-commit.md)
* [손 - 직접 조작](direct-manipulation.md)
* [손 - 제스처](gaze-and-commit.md#composite-gestures)
* [손 - 가리키고 커밋](point-and-commit.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [음성 입력 ](voice-input.md)
