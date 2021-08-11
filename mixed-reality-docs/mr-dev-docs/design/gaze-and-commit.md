---
title: 응시 및 커밋
description: 두 가지 유형의 응시(머리 응시 및 시선 응시)와 다양한 유형의 커밋을 포함하여 응시 및 커밋 입력 모델에 대해 알아봅니다.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality, 응시, 응시 대상 지정, 상호 작용, 디자인, 시선 추적, 헤드 추적, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 98f2ac9d26fc02c969520fff9083152b77bf66a2f864d5fdb15b1ee781d5d7cb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201898"
---
# <a name="gaze-and-commit"></a>응시 및 커밋

_응시 및 커밋은_ 마우스를 사용하여 컴퓨터와 상호 작용하는 방식과 밀접하게 관련된 기본 입력 모델입니다. _지점 & 클릭합니다._ 이 페이지에서는 두 가지 유형의 응시 입력(헤드 및 시선 응시)과 다양한 유형의 커밋 작업을 소개합니다. _응시 및 커밋은_ 간접 조작을 통해 원거리 입력 모델로 간주됩니다. 연결할 수 없는 홀로그램 콘텐츠와 상호 작용하는 데 가장 적합합니다.

혼합 현실 헤드셋은 사용자의 머리 위치와 방향을 사용하여 헤드 방향 벡터를 결정할 수 있습니다. 응시는 사용자의 눈 사이를 직접 가리키는 직선으로 간주합니다. 이것은 사용자가 보고 있는 위치에 대한 대략적인 근사치입니다. 애플리케이션은 이 광선을 가상 또는 실제 개체와 교차하고 해당 위치에 커서를 그려 사용자가 대상으로 하는 대상을 알 수 있습니다.

헤드 게이즈 외에도 HoloLens 2 같은 일부 혼합 현실 헤드셋에는 시선 응시 벡터를 생성하는 시선 추적 시스템이 포함되어 있습니다. 이를 통해 사용자가 보는 위치를 세밀하게 측정할 수 있습니다. 두 경우 모두 응시는 사용자의 의도에 대한 중요한 신호를 나타냅니다. 시스템이 사용자의 의도한 작업을 해석하고 예측할수록 사용자 만족도와 성능이 향상됩니다.

다음은 혼합 현실 개발자가 머리 응시 또는 시선 응시를 활용할 수 있는 방법에 대한 몇 가지 예입니다.
* 앱은 장면의 홀로그램과 응시를 교차하여 사용자의 주의가 어디에 있는지 확인할 수 있습니다(시선 응시를 사용하여 더 정확함).
* 앱은 사용자의 응시에 따라 제스처 및 컨트롤러 누를 수 있으며, 이를 통해 사용자는 홀로그램을 원활하게 선택, 활성화, 잡기, 스크롤 또는 상호 작용할 수 있습니다.
* 앱을 통해 사용자는 응시 광선과 공간 매핑 메시를 교차하여 실제 화면에 홀로그램을 배치할 수 있습니다.
* 앱은 사용자가 중요한 개체의 방향을 보고 있지 않을 때를 알 수 있으며, 이로 인해 앱이 시각적 및 오디오 신호를 제공하여 해당 개체로 전환할 수 있습니다.

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
        <td><strong>입력 모델</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>헤드 게이즈(head-gaze) 및 커밋</td>
        <td>✔️ 권장</td>
        <td>✔️ 권장(세 번째 선택 - <a href="interaction-fundamentals.md">다른 옵션 보기</a>)</td>
        <td>➕ 대체 옵션</td>
    </tr>
         <tr>
        <td>시선 응시 및 커밋</td>
        <td>❌ 사용할 수 없습니다.</td>
        <td>✔️ 권장(세 번째 선택 - <a href="interaction-fundamentals.md">다른 옵션 보기</a>)</td>
        <td>❌ 사용할 수 없습니다.</td>
    </tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>머리 및 눈 추적 디자인 개념 데모

실제 머리 및 눈 추적 디자인 개념을 보려면 아래의 **홀로그램 디자인 - 머리 추적 및 눈 추적** 동영상 데모를 확인합니다. 완료되면 계속해서 특정 주제에 대해 자세히 알아봅니다.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*이 동영상은 "홀로그램 디자인" HoloLens 2 앱에서 가져온 것입니다. [여기](https://aka.ms/dhapp)에서 전체 환경을 다운로드하여 즐겨 보세요.*

## <a name="gaze"></a>응시

### <a name="eye--or-head-gaze"></a>시선 또는 머리 응시?
"시선 응시 및 커밋" 또는 "헤드 응시 및 커밋" 입력 모델을 사용해야 하는지 여부에 대한 질문에 직면하는 경우 몇 가지 고려 사항이 있습니다. 몰입형 헤드셋 또는 HoloLens(1세대)용으로 개발하는 경우 헤드 게이즈(head-gaze) 및 커밋을 선택하는 것이 간단합니다. HoloLens 2 위해 개발하는 경우 선택이 좀 더 어려워집니다. 각각에 제공되는 장점과 과제를 이해하는 것이 중요합니다.
머리 응시와 시선 응시 대상 지정을 대조하기 위해 아래 표에서 몇 가지 광범위한 장점과 단점을 컴파일했습니다. 이 방법은 완전하지 않으며 혼합 현실의 시선 응시 대상 지정에 대해 자세히 알아보는 것이 좋습니다.
* [HoloLens 2 시선 추적:](eye-tracking.md)일부 개발자 지침을 포함하여 HoloLens 2 대한 새로운 시선 추적 기능의 일반적인 소개입니다. 
* [시선 응시 상호 작용:](eye-gaze-interaction.md)시선 추적을 입력으로 사용하려는 경우 디자인 고려 사항 및 권장 사항입니다.

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>시선 응시 대상 지정</strong></td>
        <td><strong>헤드 게이즈(head-gaze) 타기팅</strong></td>
    </tr>
    <tr>
        <td>빠른!</td>
        <td>느린</td>
    </tr>
    <tr>
        <td>낮은 노력(거의 모든 신체 이동 필요)</td>
        <td>균등할 수 있습니다. - 가능한 불편(예: 목의 가중치)</td>
    </tr>
    <tr>
        <td>커서가 필요하지 않지만 미묘한 피드백이 권장됩니다.</td>
        <td>커서를 표시해야 합니다.</td>
    </tr>
    <tr>
        <td>부드러운 시선 이동 없음 - 예를 들어 그리기에는 좋지 않습니다.</td>
        <td>보다 제어되고 명시적</td>
    </tr>
    <tr>
        <td>작은 대상(예: 작은 단추 또는 웹 링크)의 경우 어렵습니다.</td>
        <td>신뢰할 수 있는! 대체(fallback)가 좋습니다!</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

응시 및 커밋 입력 모델에 헤드 응시 또는 시선 응시를 사용하든 간에 각각 서로 다른 디자인 제약 조건 집합이 제공됩니다. 이러한 내용은 [시선 응시 및 커밋 및](gaze-and-commit-eyes.md) 헤드 응시 및 [커밋](gaze-and-commit-head.md) 문서에서 별도로 다룹니다.

<br>

---

### <a name="cursor"></a>커서

:::row:::
    :::column:::
        머리 응시의 경우 대부분의 앱은 [커서](cursors.md) 또는 기타 감사/시각적 표시를 사용하여 상호 작용하려는 내용에 대한 사용자의 확신을 제공해야 합니다. 일반적으로 머리 응시 광선이 홀로그램 또는 실제 표면일 수 있는 개체와 먼저 교차하는 세계에 이 커서를 배치합니다.<br>
        <br>
        시선 응시의 경우 일반적으로 커서를 *표시하지 않는* 것이 좋습니다. 이 경우 사용자의 방해가 되고 불편해질 수 있습니다. 대신 시각적 대상을 조금만 강조 표시하거나, 눈가 커서를 사용하여 사용자가 상호 작용하려는 대상에 대한 확신을 제공합니다. 자세한 내용은 HoloLens 2 대한 [시선 기반 입력에 대한 디자인 지침을](eye-tracking.md) 확인하세요.
    :::column-end:::
        :::column:::
       ![응시를 표시하는 예제 시각적 커서](images/cursor.jpg)<br>
       *이미지: 응시를 표시하는 예제 시각적 커서*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>Commit
대상을 _응시하는_ 다양한 방법에 대해 이야기한 후 응시 및 _커밋의 커밋_ 부분에 대해 좀 더 알아보겠습니다. 
개체 또는 UI 요소를 대상으로 지정한 후 사용자는 보조 입력을 사용하여 상호 작용하거나 클릭할 수 있습니다. 이를 입력 모델의 커밋 단계라고 합니다. 

지원되는 커밋 메서드는 다음과 같습니다.
- 에어 탭 손 제스처(즉, 앞에서 손을 들어와서 인덱스 손가락과 엄지 손가락을 모으세요).
- _"select"_ 또는 대상 음성 명령 중 하나를 말합니다.
- [HoloLens 클릭하여](/hololens/hololens1-clicker) 단일 단추 누르기
- Xbox 게임 패드에서 'A' 단추 누르기
- Xbox 적응형 컨트롤러에서 'A' 단추 누르기

### <a name="gaze-and-air-tap-gesture"></a>응시 및 에어 탭 제스처
에어 탭은 손을 똑바로 세워서 탭하는 동작입니다. 에어 탭을 사용하려면 준비 위치로 인덱스 손가락을 들어 올립니다. 그런 다음 엄지 손가락으로 손가락 모으기를 하고, 인덱스 손가락을 다시 올려 놓습니다. HoloLens(1세대)에서는 에어 탭이 가장 일반적인 보조 입력입니다.


:::row:::
    :::column:::
       ![준비 위치의 손가락](images/readyandpress-ready.jpg)<br>
       **준비 위치의 손가락**<br>
    :::column-end:::
    :::column:::
       ![아래로 손가락을 눌러 탭하거나 클릭합니다.](images/readyandpress-press.jpg)<br>
        **아래로 손가락을 눌러 탭하거나 클릭합니다.**<br>
    :::column-end:::
:::row-end:::


HoloLens 2 에어 탭도 사용할 수 있습니다. 원래 버전에서 완화되었습니다. 이제 손을 맞고 가만히 있는 한 거의 모든 종류의 손가락 모으기가 지원됩니다. 이렇게 하면 사용자가 제스처를 더 쉽게 학습하고 사용할 수 있습니다. 이 새 에어 탭은 동일한 API를 통해 이전 API를 대체하므로 기존 애플리케이션은 HoloLens 2 위해 다시 컴파일한 후 자동으로 새 동작을 갖습니다.

<br>

---

### <a name="gaze-and-select-voice-command&quot;></a>응시 및 &quot;선택&quot; 음성 명령
음성 명령은 혼합 현실의 주요 상호 작용 방법 중 하나입니다. 시스템을 제어하는 강력한 핸즈프리 메커니즘을 제공합니다. 다음과 같은 다양한 유형의 음성 상호 작용 모델이 있습니다.

- 클릭 동작 또는 커밋을 보조 입력으로 사용하는 일반 &quot;Select&quot; 명령입니다.
- 개체 명령(예: &quot;닫기&quot; 또는 &quot;더 크게 만들기")은 작업을 보조 입력으로 수행하고 커밋합니다.
- 전역 명령 (예: "시작으로 이동")은 대상이 필요 하지 않습니다.
- Cortana와 같은 대화 사용자 인터페이스 또는 엔터티는 AI 자연어 기능을 포함 합니다.
- 사용자 지정 음성 명령

세부 정보 및 사용 가능한 음성 명령의 포괄적인 목록과 사용 방법에 대 한 자세한 내용은 [음성 명령](../out-of-scope/voice-design.md) 지침을 확인 하세요.

<br>

---


### <a name="gaze-and-hololens-clicker"></a>Clicker 및 HoloLens 응시

:::row:::
    :::column:::
        HoloLens Clicker는 HoloLens 용으로 특별히 구축 된 첫 번째 주변 장치입니다. HoloLens (첫 번째 gen) 개발 버전에 포함 되어 있습니다. HoloLens Clicker를 사용 하면 사용자가 최소한의 손 동작을 클릭 하 고 보조 입력으로 커밋할 수 있습니다. HoloLens Clicker는 BTLE (Bluetooth 낮은 에너지)를 사용 하 여 HoloLens (첫 번째 gen) 또는 HoloLens 2에 연결 합니다.<br>
        <br>
        [장치를 페어링 하는 방법에 대 한 자세한 내용 및 지침](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *이미지: HoloLens Clicker*
    :::column-end:::
        :::column:::
       ![HoloLens 클리커](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>응시 및 Xbox 무선 컨트롤러

:::row:::
    :::column:::
        Xbox 무선 컨트롤러는 ' A ' 단추를 사용 하 여 클릭 actuation를 보조 입력으로 수행 합니다. 장치는 시스템을 탐색 하 고 제어 하는 데 도움이 되는 기본 작업 집합에 매핑됩니다. 컨트롤러를 사용자 지정 하려면 Xbox 액세서리 응용 프로그램을 사용 하 여 Xbox 무선 컨트롤러를 구성 합니다.<br>
        <br>
        [Xbox 컨트롤러와 PC를 페어링 하는 방법](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *이미지: Xbox 무선 컨트롤러*
    :::column-end:::
        :::column:::
       ![Xbox 무선 컨트롤러](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>응시 및 Xbox 적응 컨트롤러
주로 모바일 기능이 제한 된 게이머의 요구 사항을 충족 하기 위해 설계 된 Xbox 적응 컨트롤러는 혼합 현실에 더 쉽게 액세스할 수 있도록 지 원하는 장치에 대 한 통합 허브입니다.

Xbox 적응 컨트롤러는 ' A ' 단추를 사용 하 여 클릭 actuation를 보조 입력으로 수행 합니다. 장치는 시스템을 탐색 하 고 제어 하는 데 도움이 되는 기본 작업 집합에 매핑됩니다. 컨트롤러를 사용자 지정 하려면 Xbox 액세서리 응용 프로그램을 사용 하 여 Xbox 적응 컨트롤러를 구성 합니다.

![Xbox 적응형 컨트롤러](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox 적응형 컨트롤러*

스위치, 단추, 탈것, 조이스틱 등의 외부 장치를 커넥트 하 여 고유한 사용자 지정 컨트롤러 환경을 만듭니다. 단추, 엄지 스틱 및 트리거 입력은 3.5-mm 잭 및 USB 포트를 통해 연결 된 보조 장치를 사용 하 여 제어 됩니다.

![Xbox 적응형 컨트롤러 포트](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox 적응형 컨트롤러 포트*

[디바이스 페어링 지침](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Xbox 사이트의 더 많은 정보</a>

<br>

---

## <a name="composite-gestures"></a>복합 제스처

### <a name="air-tap"></a>에어 탭
공기 탭 제스처와 아래 다른 제스처는 특정 탭에만 반응 합니다. 메뉴 또는와 같은 다른 탭을 검색 하려면 응용 프로그램에서 위의 두 키 구성 요소 제스처 섹션에 설명 된 하위 수준 상호 작용을 직접 사용 해야 합니다.

### <a name="tap-and-hold"></a>길게 누르기
홀드(hold)는 에어 탭의 아래쪽 손가락 위치를 유지하는 것입니다. 공기 탭 및 유지의 조합을 사용 하면 개체를 활성화 하는 대신 개체를 선택 하거나 상황에 맞는 메뉴를 표시 하는 것과 같이 개체를 선택 하는 것과 같이 arm 이동과 결합 하 여 보다 복잡 한 "클릭 및 끌기" 상호 작용을 수행할 수 있습니다.
이러한 제스처를 설계할 때 사용자가 확장 제스처 중에 손 postures을 완화 수 있으므로 주의 해야 합니다.

### <a name="manipulation"></a>조작
사용자의 손을 이동 하 여 홀로그램에서 1:1에 반응할 수 있도록 하려면 조작 제스처를 사용 하 여 홀로그램을 이동, 크기 조정 또는 회전할 수 있습니다. 이러한 1:1 움직임을 사용하는 한 가지 방식은 실제로 선을 긋거나 그릴 수 있도록 하는 것입니다.
조작 제스처에 대한 초기 타기팅은 응시 또는 포인팅을 통해 수행해야 합니다. 탭 하 여 보류가 시작 되 면 개체 조작이 직접 이동 하 여 처리 됩니다. 그러면 사용자가를 조작 하는 동안 살펴볼 수 있습니다.

### <a name="navigation"></a>탐색
탐색 제스처는 가상 조이스틱처럼 작동하며 방사형 메뉴와 같은 UI 위젯을 탐색하는 데 사용할 수 있습니다. 길게 눌러서 제스처를 시작한 후 초기에 누른 부분을 중심으로 정규화된 3D 큐브 안에서 손을 움직입니다. 값이-1에서 1 사이의 X, Y 또는 Z 축을 따라 이동 하 고 0을 시작 점으로 이동할 수 있습니다.
탐색은 속도 기반 연속 스크롤 또는 확대/축소 제스처를 빌드하는 데 사용할 수 있으며, 마우스 가운데 단추를 클릭한 다음, 마우스를 위아래로 움직여서 2D UI를 스크롤하는 것과 유사합니다.

레일을 사용한 탐색은 특정 임계값에 도달할 때까지 특정 축의 움직임을 인식 하는 기능을 나타냅니다. 이는 응용 프로그램이 X, Y 축의 탐색 제스처를 인식 하도록 구성 되어 있지만 레일을 사용 하 여 X 축도 지정 하는 경우와 같이 개발자가 응용 프로그램에서 둘 이상의 축으로 이동 하는 경우에만 유용 합니다. 이 경우 Y 축에서 직접 이동이 발생 하는 경우 시스템은 x 축에서 허수 레일 (가이드) 내에 유지 되는 동안 X 축에서 직접 이동 하는 것을 인식 합니다.

2D 앱에서는 사용자가 세로 탐색 제스처를 사용하여 앱 내에서 스크롤, 확대/축소 또는 끌기를 수행할 수 있습니다. 그러면 앱에 가상 손가락 터치가 삽입되어 같은 유형의 터치 제스처가 시뮬레이션됩니다. 사용자는 단추를 선택 하거나 ' <스크롤/끌기/확대/축소> 도구 '를 사용 하 여 응용 프로그램 위에 있는 막대의 도구 사이를 전환 하 여 수행할 작업을 선택할 수 있습니다.

[복합 제스처에 대한 추가 정보](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>제스처 인식기

제스처 인식 기능을 사용 하는 경우의 한 가지 장점 중 하나는 현재 대상 홀로그램에서 수락할 수 있는 제스처에 대해서만 제스처 인식기를 구성할 수 있다는 것입니다. 플랫폼은 지원 되는 특정 제스처를 구분 하기 위해 필요에 따라 명확성을 갖습니다. 이러한 방식으로, 살짝 누르기를 지 원하는 홀로그램은 press와 release 사이에 모든 시간을 허용할 수 있는 반면, 탭 및 유지를 모두 지 원하는 홀로그램은 대기 시간 임계값 후에 탭을 보류 중으로 승격할 수 있습니다.

## <a name="hand-recognition"></a>손 인식
HoloLens는 디바이스에 보이는 한쪽 또는 양쪽 손의 위치를 추적하여 손 제스처를 인식합니다. HoloLens는 손이 준비 상태(집게손가락을 올리고 손등을 마주보고 있는 상태)이거나 눌린 상태(집게손가락을 내리고 손등을 마주보고 있는 상태)일 때 손을 봅니다. 손이 다른 포즈에 있으면 HoloLens은 무시 됩니다.
HoloLens에서 검색 되는 각 면에 대해 방향과 눌린 상태 없이 위치에 액세스할 수 있습니다. 손이 제스처 프레임의 가장자리에 가까워지면, 방향 벡터가 제공됩니다. 이것을 사용자에게 표시하면, HoloLens에게 보이는 위치로 손을 다시 이동하려면 손을 어떻게 움직여야 하는지를 사용자가 알 수 있습니다.

## <a name="gesture-frame"></a>제스처 프레임
HoloLens에 대 한 제스처의 경우 제스처는 제스처 프레임 내에 있어야 합니다. 제스처는 제스처-감지 카메라에서 적절 하 게 볼 수 있습니다. 사용자는 작업 성공 및 자신에 게 편안 하 게 사용할 수 있도록이 영역에 대 한 교육을 받아야 합니다. 대부분의 사용자는 처음에는 HoloLens를 통해 제스처 프레임이 보기 내에 있어야 하 고 상호 작용 하는 데 사용할 수 있는 상태를 유지 한다고 가정 합니다. HoloLens Clicker를 사용 하는 경우에는 제스처 프레임 내에서 손을 사용할 필요가 없습니다.

특히 연속 제스처의 경우 holographic 개체를 이동 하는 경우, 예를 들어 의도 하지 않은 결과를 손실 하는 경우 중간 제스처를 사용 하 여 사용자가 제스처 프레임 외부로 손을 이동할 위험이 있습니다.

다음 세 가지 사항을 고려해야 합니다.

- 제스처 프레임의 존재 및 근사치 범위에 대 한 사용자 교육입니다. HoloLens 설치 하는 동안이를 배울 수 있습니다.

- 응용 프로그램 내의 제스처 프레임 경계에 도달 하거나 해당 제스처가 원치 않는 결과로 이어질 수 있는 수준까지 사용자에 게 알립니다. Research는 이러한 알림 시스템의 주요 품질을 보여 줍니다. HoloLens shell은 경계가 교차 하는 방향을 나타내는 중앙 커서에 이러한 유형의 알림 (시각적 개체)에 대 한 좋은 예를 제공 합니다.

- 제스처 프레임 경계를 벗어난 결과는 최소화되어야 합니다. 일반적으로이는 제스처의 결과가 경계에서 중지 되 고 반전 되지 않음을 의미 합니다. 예를 들어 사용자가 실내에서 일부 holographic 개체를 이동 하는 경우 제스처 프레임이 위반 되 면 이동이 중지 되 고 시작 지점으로 반환 되지 않습니다. 사용자에 게 몇 가지 문제가 발생할 수 있지만, 경계를 보다 신속 하 게 이해 하 고 매번 원하는 작업을 다시 시작 하지 않아도 됩니다.



## <a name="see-also"></a>추가 정보
* [시선 기반 상호 작용](eye-gaze-interaction.md)
* [HoloLens 2의 시선 추적](eye-tracking.md)
* [응시 및 유지](gaze-and-dwell.md)
* [손 - 직접 조작](direct-manipulation.md)
* [손 - 제스처](gaze-and-commit.md#composite-gestures)
* [손 - 가리키고 커밋](point-and-commit.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [음성 입력 ](voice-input.md)