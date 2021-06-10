---
title: 커서
description: 커서 또는 대상 벡터의 표시기는 사용자가 HoloLens가 의도에 대해 이해하는 내용을 이해할 수 있도록 지속적인 피드백을 제공합니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens(1세대), HoloLens 2, Mixed Reality, 커서, 대상 지정, 응시, 제스처, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 광선, 입력
ms.openlocfilehash: 829d7b3f766f848228946ee0a623f9f3013adca3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600382"
---
# <a name="cursors"></a>커서

![커서](images/UX_Hero_Cursor.jpg)

커서는 헤드셋에서 사용자가 현재 포커스가 지정된 시간에 있다고 생각하는 위치에 따라 지속적인 피드백을 제공합니다. 커서 피드백에는 입력에 응답하는 가상 환경의 영역, 홀로그램 또는 지점이 포함됩니다. 커서는 디바이스가 사용자의 주의를 이해하는 위치에 대한 디지털 표현이지만 사용자의 의도를 결정하는 것과는 다릅니다. 또한 커서 피드백을 통해 사용자는 예상할 시스템 응답을 알 수 있습니다. 피드백을 사용하여 디바이스에 의도를 전달하여 사용자 신뢰도를 높일 수 있습니다.

**커서에는 손가락, 광선** 및 **머리 응시의** 세 가지 종류가 있습니다. 이러한 포인팅 커서는 HoloLens, HoloLens 2 및 몰입형 헤드셋에서 다양한 입력 형식으로 작동합니다. 다음은 각 유형의 헤드셋 및 상호 작용 모델에 사용할 커서 유형에 대한 지침입니다. MRTK(Mixed Reality 도구 키트)에서는 올바른 포인팅 환경을 빌드하는 데 도움이 되는 끌어서 놓기 커서 모듈을 만들었습니다.

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
        <td>손가락 커서</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>광선 커서</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>머리 응시 커서</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>손가락 커서

손가락 커서는["손으로 직접 조작"](direct-manipulation.md)상호 작용 모드를 향상시키기 위해 HoloLens 2 사용할 수 있습니다. 손가락이 가리키는 위치를 더 잘 이해하기 위해 두 인덱스 손가락의 팁에 링을 연결했습니다. 링 크기는 손가락이 UI 화면에 근접한 것을 기반으로 하며, 손가락이 UI를 터치할 때 작은 점으로 축소됩니다. 손가락이 가까울수록 링이 작습니다. <br>

![손가락 커서](images/finger-cursor.png)<br>
**손가락 커서의 시각적 피드백 상태** 1: 링이 점으로 축소됩니다. 2: 링이 표면에 맞춥니다. 3: 링이 손가락 벡터에 수직입니다. 4: 링이 없습니다.

## <a name="ray-cursor"></a>광선 커서

광선 커서는 원거리 포인팅 광선의 끝에 연결되어 실습을 벗어나는 개체를 조작할 수 있습니다. 몰입형 헤드셋에서 광선은 모션 컨트롤러에서 꺼내고 점 커서로 끝납니다. HoloLens 2 이러한 모션 컨트롤러 광선의 멘탈 모델을 적용하고 손끝에서 시작되고 직접 조작에 사용되는 손가락 커서와 일치하는 링 모양의 커서로 끝나는 손 광선을 디자인했습니다. <br>
:::row:::
    :::column:::
        ![광선 커서 컨트롤러](images/ray-cursor-controller.png)<br>
        **모션 컨트롤러의 광선 커서**<br>
    :::column-end:::
    :::column:::
        ![광선 커서 손](images/ray-cursor-hand.png)<br>
        **손의 광선 커서**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a>머리 응시 커서

머리 응시 커서는 머리의 위치와 회전을 사용하여 가리킨 보이지 않는 머리 응시 벡터의 끝에 연결되는 점입니다. 작업을 실행하기 위해 이 포인팅 커서는 에어 탭, 음성 명령, 대기 및 단추 누르기와 같은 다양한 커밋 입력과 쌍을 이루어 드립니다. HoloLens 2 머리 응시는 에어 탭과 원거리 손 광선 간의 상호 작용 충돌이 있기 때문에 에어 탭이 아닌 커밋 입력과 가장 잘 쌍을 이루게 됩니다. <br>
:::row:::
    :::column:::
        ![머리 응시 커서 손](images/head-gaze-cursor-hand.png)<br>
        **손 제스처를 가진 머리 응시 커서**<br>
    :::column-end:::
    :::column:::
        ![머리 응시 커서 음성](images/head-gaze-cursor-voice.png)<br>
        **음성 명령을 통해 머리 응시 커서**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a>커서 사용자 지정 권장 사항

커서 피드백 동작 및 모양을 사용자 지정하려는 경우 몇 가지 디자인 권장 사항은 다음과 같습니다.

### <a name="cursor-scale"></a>커서 배율

* 커서는 사용 가능한 대상보다 크지 않아야 하며, 사용자가 콘텐츠를 쉽게 조작하고 볼 수 있도록 합니다.
* 만든 경험에 따라 사용자가 둘러 볼 때 커서 크기를 조정하는 것도 중요한 고려 사항입니다. 예를 들어 사용자가 환경을 더 자세히 살펴보고 커서가 너무 작아서 손실되지 않아야 합니다.
* 커서의 크기를 조정하는 경우 크기가 조정됨에 따라 소프트 애니메이션을 적용하여 유기적인 느낌을 주는 것이 좋습니다.
* 콘텐츠를 방해하지 않습니다. 홀로그램은 환경을 기억하기 쉽게 만들고 커서를 제거하면 안 됩니다.

### <a name="directionless-cursor-shape"></a>방향 없는 커서 모양

* 오른쪽 커서 모양은 하나도 없지만 torus와 같은 방향 없는 도형을 사용하는 것이 좋습니다. 어떤 방향(예: 기존 화살표 커서)을 가리키는 커서는 사용자가 항상 그런 방식으로 보이도록 혼동할 수 있습니다.
* 커서를 사용하여 상호 작용 명령을 사용자에게 전달하는 경우는 예외입니다. 예를 들어 Mixed Reality OS에서 홀로그램 크기를 조정하는 경우 커서에는 홀로그램 크기를 조정하기 위해 손을 이동하는 방법을 사용자에게 지시하는 화살표가 일시적으로 포함됩니다.

### <a name="look-and-feel"></a>모양과 느낌

* 도넛형 또는 torus 모양의 커서는 많은 애플리케이션에서 작동합니다.
* 만드는 환경을 가장 잘 나타내는 색과 모양을 선택합니다.
* 커서는 색 [구분이](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)특히 쉽습니다.
* 불투명도가 균형이 조정된 작은 커서는 시각적 계층 구조를 분산하지 않고 정보를 제공합니다.
* 커서 뒤에 그림자 또는 강조 표시를 사용하면 콘텐츠를 방해하고 당면한 작업에 방해가 될 수 있기 때문에 인식할 수 있어야 합니다.
* 커서는 앱의 표면에 맞춰지고 곱해야 합니다. 사용자는 시스템에서 보고 있는 위치를 볼 수 있을 뿐만 아니라 시스템이 주변을 알고 있다는 느낌을 갖게 됩니다. 예를 들어 Mixed Reality OS의 커서는 사용자의 세계 표면에 맞춰져 사용자가 홀로그램을 직접 보고 있지 않더라도 세계를 인식할 수 있습니다.
* 커서를 사용자에게 가까이 있을 때 대화형 요소에 자기적으로 잠그면 사용자가 선택 작업을 사용할 때 해당 요소와 상호 작용할 수 있다는 확신을 높일 수 있습니다.

### <a name="visual-cues"></a>시각 신호

* 환경이 단일 홀로그램에 초점을 맞춘 경우 커서는 홀로그램을 비울 때 해당 홀로그램에 맞춰서 마우스를 맞추고 모양을 변경해야 합니다. 이렇게 하면 홀로그램이 실행 가능하고 상호 작용할 수 있음을 사용자에게 전달할 수 있습니다.
* 애플리케이션에서 공간 매핑을 사용하는 경우 커서가 표시되는 모든 표면을 정렬하고 클리핑할 수 있습니다. 이를 통해 HoloLens와 애플리케이션에서 공간을 볼 수 있다는 피드백을 사용자에게 제공합니다. 이렇게 하면 홀로그램이 실제와 세계에 있다는 사실이 강화되고 실제와 가상 간의 격차를 해소할 수 있습니다.
* 보기에 홀로그램 또는 표면이 없을 때 커서가 수행해야 하는 작업을 파악합니다. 사용자 앞에 미리 결정된 거리에 배치하는 것이 한 가지 옵션입니다.

### <a name="possible-actions"></a>가능한 작업

* 커서는 크기 조정 또는 회전과 같이 홀로그램이 수행할 수 있는 가능한 작업을 전달하기 위해 다른 아이콘으로 나타낼 수 있습니다.
* 커서가 사용자에게 의미가 있는 경우에만 커서에 추가 정보를 추가합니다. 그렇지 않으면 사용자가 상태 변경을 알아차리지 못하거나 커서가 혼동될 수 있습니다.

### <a name="input-state"></a>입력 상태

* 커서를 사용하여 사용자의 입력 상태 또는 의도를 표시할 수 있습니다. 예를 들어 시스템에 손 상태가 표시되고 애플리케이션이 조치를 취할 준비가 되었다는 것을 사용자에게 알리는 아이콘을 표시할 수 있습니다.
* 커서를 사용하여 사용자에게 음성 명령이 잠시 색 변경을 통해 시스템에서 들은 것을 표시할 수도 있습니다.

* 다음 커서 상태는 다양한 방법으로 구현할 수 있습니다. 상태 시스템처럼 커서를 모델링하여 이러한 다양한 상태를 구현할 수 있습니다. 예를 들면 다음과 같습니다.
    * 유휴 상태는 기본 커서를 표시하는 위치입니다.
    * 준비 상태는 준비 위치에서 사용자의 손을 감지한 경우입니다.
    * 상호 작용 상태는 사용자가 특정 상호 작용을 수행하는 경우입니다.
    * 가능한 작업 상태 또는 가리키기 상태는 홀로그램에서 수행할 수 있는 가능한 작업을 전달 하는 경우입니다.

또한 다양 한 상태를 검색할 때 다양 한 아트 자산을 표시 하는 스킨 가능 방식으로 이러한 상태를 구현할 수 있습니다.

<br>

---

## <a name="going-cursor-free"></a>"커서를 사용 하지 않음"으로 이동

집중 교육의 의미는 환경의 주요 구성 요소이 고,에 대 한 상호 작용을 가리키는 경우 (응시 및 제스처를 통해) 뛰어난 정밀도가 필요 하지 않은 경우 커서를 사용 하지 않고 디자인 하는 것이 좋습니다. 시스템은 여전히 커서의 일반적인 요구 사항을 충족 해야 합니다. 사용자에 게 시스템의 포인팅에 대 한 지속적인 피드백을 제공 하 고 사용자가 시스템에 대 한 사용자를 전달 하도록 도움을 줍니다. 이는 다른 눈에 띄는 상태를 변경 하 여 달성할 수 있습니다.

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 용 MRTK (Mixed Reality Toolkit)의 커서

기본적으로 [Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity) 는 셸 시스템 커서와 동일한 시각적 상태를 가진 커서 Prefab ([defaultcursor. prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors))를 제공 합니다. MRTK 입력 프로필의 포인터 아래에 할당됩니다. 사용자 환경에 맞게이 커서를 바꾸거나 사용자 지정할 수 있습니다. 아이 추적 입력 환경에서 MRTK는 혼란을 최소화 하기 위해 미묘한 시각적 개체를 포함 하는 EyeGazeCursor를 제공 합니다.

* [MRTK - 포인터 프로필](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [MRTK - 입력 시스템](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [MRTK - 포인터](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a>참고 항목

* [제스처](gaze-and-commit.md#composite-gestures)
* [헤드 게이즈 및 커밋](gaze-and-commit.md)