---
title: 헤드 게이즈(head-gaze) 및 드웰(dwell)
description: 일반적인 시나리오 및 디자인 원칙을 포함하여 헤드 응시 및 상주 입력 모델의 개요를 시작합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality, 응시, dwell, 상호 작용, 디자인, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, ux, 지침, 목록 보기
ms.openlocfilehash: e069b0815f69848b7632cb7b1b85d85f328441b7156ae22ffe097fedc3ed6fc1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223628"
---
# <a name="head-gaze-and-dwell"></a>헤드 게이즈(head-gaze) 및 드웰(dwell)

손에 도구와 파트가 있으면 제스처가 어렵거나 불가능할 수 있습니다. 제스처와 같은 음성 명령은 특정 상황(예: 과도하게 소리가 큰 상황)에서 불안정할 수 있습니다. 또한 음성을 사용하여 컴퓨터를 제어하는 것이 전체적으로 일반적이지는 않지만 보편화되고 있는 것은 확실합니다. 헤드 게이즈(head-gaze) 및 드웰(dwell)은 HoloLens에서 헤드업 및 핸즈프리 작업을 수행하기에 가장 친숙하고 마스터하기 편한 메커니즘을 제공합니다. 또한 헤드 게이즈(head-gaze) 및 드웰(dwell)은 운영 환경에서 소음 간섭이나 무음 제약과 상관없이 100% 안정적입니다.

## <a name="scenarios"></a>시나리오

헤드 응시 및 번들(dwell)은 사람의 손을 다른 작업으로 바빠지는 시나리오에서 유용합니다. 이 기능은 음성이 100% 안정적이지 않거나 환경 또는 소셜 제약으로 인해 사용할 수 없는 경우에도 유용합니다. HoloLens를 착용하고 자동차 엔진을 수리하는 동안 참조 정보를 오버레이하는 경우가 좋은 예입니다. 엔진 칸에 기대고 있는 몸을 지탱하거나 도구를 다루느라 손을 사용할 수 없습니다. 차고 공간에서는 연장이 계속 윙윙거리면서 소리를 내기 때문에 시끄러워서 음성 명령을 실행하기 어렵습니다. 헤드 응시 및 유지를 사용하면 HoloLens 사용하는 사용자가 워크플로를 중단하지 않고도 참조 자료를 자신 있게 탐색할 수 있습니다. 

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
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></td>
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

헤드 게이즈(head-gaze) 및 드웰(dwell)에는 직관적인 시각 피드백이 필요하지만 피드백이 너무 많으면 불안정한 상태를 유발할 수 있습니다. 피드백은 사용자가 대상으로 하는 대상을 파악하는 데 도움이 되지만 의도에 대해 자동으로 선택하지는 않습니다. 텍스트, 아이콘 및 레이블을 읽을 때 선택하기 전에 사용자에게 정보를 흡수할 시간을 제공해야 합니다.
    
**최적의 속도 구하기**
    
드웰(dwell) 상호 작용은 탐색의 영향력에 따라 타이머가 다를 수 있습니다. 사용 빈도가 높은 함수는 일반적으로 채우기 시간이 빠른 것이 유용하고 중대한 함수는 채우기 시간이 긴 것이 유용합니다. 채우기 효과를 사용하여 타이머를 표시하면, 채우기 색상의 애니메이션 곡선이 채우기 시간이 빠른 느낌에 긍정적인 영향을 줄 수 있습니다. 빠른/중간/느린 채우기 속도 재정의 중에서 사용자가 결정할 수 있도록 고려하는 것이 필요합니다.
    
**요요 효과 절대 금지**

yo-yo 효과는 콘텐츠 배치 및 헤드 응시/dwell 컨트롤이 강제로 사람들이 반복적으로 조회 및 아래로 이동하도록 할 때 발생하는 머리 이동 패턴입니다. 예를 들어 맨 아래에 헤드 응시 및 dwell 단추가 있는 목록 탐색은 루프를 유도합니다. 즉, 상주하는 것을 보고, 결과를 조회하고, 다운다운하여 감소하는 등의 루프를 유도합니다. 결과 패턴은 불안정하므로 앞뒤로 덜 필요한 중앙 집중식 위치에 탐색 컨트롤을 배치하는 것이 좋습니다. 효과에 따라 유실 단추를 배치하는 것이 편안하게 중요합니다.
초
<br>

---

## <a name="ux-guidelines-and-best-practices"></a>UX 지침 및 모범 사례

### <a name="target-sizes"></a>대상 크기

쉽게 액세스할 수 있도록 헤드 응시 및 유지(dwell) 대상은 편안하게 볼 수 있을 만큼 크고 지정된 시간 동안 대상에 헤드를 안정적으로 유지해야 합니다. 가장 편안한 환경을 구현하려면 최소 대상 크기인 2도를 권장합니다. 

### <a name="visual-feedback"></a>시각적 피드백

드웰(dwell) 타이머를 나타내기 위해 방사형 채우기를 사용하는 경우에는 단추 가운데에서 시작합니다. 일관된 응답이 서로 다른 단추의 모두 다른 방향보다는 덜 혼란스럽습니다. 

  * 방향 상호 작용(예: 위로/아래로/왼쪽/오른쪽 탐색 등)에 대해 이 규칙을 끊을 수 있습니다. 예를 들어, Microsoft Dynamics 365 가이드의 경우 예외적으로 다음/뒤로가 왼쪽에서 오른쪽으로 채워집니다.
  * 단추 전환과 같은 시나리오의 경우 외부에서 방사형 채우기를 반전하는 것이 좋습니다. 단추 누르기와 반대되는 느낌은 유지하기 좋은 시각 패턴입니다. 

### <a name="progressive-disclosure"></a>점진적 공개

점진적인 공개란 상호 작용의 각 단계에 해당하는 세부 정보만 표시하는 것을 의미합니다. dwell의 경우, 즉, 목록 컨트롤과 같이 강조 표시 시 dwell 대상이 표시됩니다.

 ### <a name="oversized-targets"></a>너무 큰 대상

드웰(dwell) 지역은 Microsoft Dynamics 365 가이드의 뒤로 단추처럼, 사용하기 쉽도록 비활성 아이콘보다 클 수 있습니다.

### <a name="prevent-flickering-with-delayed-feedback"></a>피드백 지연으로 인한 깜박임 방지

다른 사람이 드웰(dwell) 대상을 지나칠 때 깜박이지 않도록, 시각 피드백을 시작하기 전에 짧은 지연을 사용합니다.
* 자주 상호 작용하는 단추의 경우 애플리케이션이 반응적으로 느낄 수 있도록 지연을 짧게 유지합니다.
* 자주 조작하지 않는 단추의 경우 인터페이스가 twitchy인 것을 방지하기 위해 더 긴 지연이 적절할 수 있습니다.

<br>

---

## <a name="ui-patterns"></a>UI 패턴

### <a name="high-frequency-buttons"></a>높은 빈도 단추

:::row:::
    :::column:::
        빈도가 높은 단추는 애플리케이션 전체에서 일반적으로 사용되는 단추입니다. Microsoft Dynamics 365 가이드의 다음 및 뒤로 단추가 좋은 예입니다.<br>
        <br>
        **권장 사항**<br>
  * 빈도가 높은 단추는 크고 헤드 응시를 통해 더 쉽게 적중해야 합니다.
  * 인체 공학적 부담을 방지하려면 눈 높이를 가깝게 유지합니다.<br>
        <br>
*이미지: Microsoft Dynamics 365 Guides 다음 단추*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 Guides 다음 단추](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>낮은 빈도 단추

빈도가 낮은 단추는 애플리케이션 전체에서 정기적으로 상호 작용하지 않는 단추입니다. 설정 메뉴에 액세스하는 단추 또는 모든 작업을 지우는 단추가 좋은 예입니다.

* 이러한 단추는 우발적인 활성화를 피하기 위해 빈번한 헤드 게이즈(head-gaze) 경로에서 멀리 두는 것이 좋습니다. 

<br>

---

### <a name="confirmations"></a>확인

:::row:::
    :::column:::
        비용을 청구하거나, 작업을 삭제하거나, 긴 프로세스를 시작하는 등 작업에 상당한 영향을 주는 경우 사람이 단추를 선택해야 했는지 확인하는 것이 유용합니다.<br>
        <br>
        **권장 사항**<br>
  * 주요 단추의 선택을 강조 표시합니다.
  * 선택 강조 표시와 동시에 드웰(dwell) 대상을 나타냅니다.
  * 보조 단추의 경우 헤드 게이즈(head-gaze) 시 드웰(dwell) 대상을 드러납니다.<br>
        <br>
*이미지: Microsoft Dynamics 365 Guides 확인 대화 상자*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 Guides 확인 대화 상자](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>토글 단추

토글 단추를 사용하려면 다소 미묘한 논리가 제대로 작동해야 합니다. 토글 단추를 켜고 활성화하면 단추를 종료한 다음 돌아가서 dwell 논리를 다시 시작해야 합니다. 토글 가능한 단추에는 명확한 활성 및 비활성 상태가 있어야 합니다. 

<br>

---

### <a name="list-views"></a>목록 보기

:::row:::
    :::column:::
        목록 보기는 헤드 응시 및 유동 입력에 대한 특정 과제를 제공합니다. 사용자는 유지(dwell) 대상을 중심으로 팁토를 해야 하는 것처럼 콘텐츠를 스캔할 수 있습니다.<br>
        <br>
**권장 사항**<br>
  * 헤드 게이즈(head-gaze)가 특정 주체(dwell) 대상에 있지 않으면 헤드-헤드-헤드(head-gaze)가 시작되지 않는 한 전체 행이 강조 표시되게 합니다.
  * 시각적 노이즈를 줄이기 위해 행이 강조 표시된 경우에만 dwell 대상을 표시합니다.
  * 유지(dwell) 대상의 위치와 명확하고 일관되어야 합니다.
  * 반복적인 UI를 방지하기 위해 모든 유동 대상을 한 번에 표시하지 마세요.
  * UX 친숙도를 설정하기 위해 가능한 한 자주 동일한 패턴을 다시 사용하십시오.<br>
        <br>
*이미지: Microsoft Dynamics 365 Guides 목록*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 Guides 목록](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>추가 정보

* [응시 및 커밋](gaze-and-commit.md)
* [손 - 직접 조작](direct-manipulation.md)
* [손 - 제스처](gaze-and-commit.md#composite-gestures)
* [손 - 가리키고 커밋](point-and-commit.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [음성 입력 ](voice-input.md)