---
title: 사례 연구 - 3 HoloStudio UI 및 상호 작용 디자인 학습
description: HoloStudio UI 및 상호 작용 디자인 학습
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio, Windows Mixed Reality
ms.openlocfilehash: 1b384a10d3fe53cf7e69c2e8437904040322dc213d9473d9ae9abf272c08ec5e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195872"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>사례 연구 - 3 HoloStudio UI 및 상호 작용 디자인 학습

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) HoloLens 첫 번째 Microsoft 앱 중 하나입니다. 따라서 3D UI 및 상호 작용 디자인에 대한 새로운 모범 사례를 만들어야 했습니다. 많은 사용자 테스트, 프로토타이핑, 시행착오를 통해 이 작업을 진행했습니다.

모든 사람이 이러한 유형의 연구를 수행할 수 있는 리소스를 가지고 있지는 않다는 것을 알고 있으므로 Holographic Designer인 여하우가 UI 및 HoloLens 앱의 상호 작용 디자인에 대한 HoloStudio 개발 중에 배운 세 가지 사항을 공유했습니다.

## <a name="watch-the-video"></a>비디오 보기

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>문제 #1: 사람들이 생성을 이동하고 싶지 않았습니다.

원래는 실제 세계에서 찾을 수 있는 것처럼 HoloStudio 워크벤치를 사각형으로 디자인했습니다. 문제는 사람들이 데스크에 있거나 컴퓨터 앞에서 작업할 때 가만히 있으라고 알려주는 경험의 수명을 갖기 때문에 워크벤치를 이동하고 모든 측면에서 3D 생성을 탐색하지 않는다는 것입니다.

![의 워크벤치 사각형 디자인은 사용자가 이동하면서 모든 측면에서 생성되는 것을 볼 수 HoloStudio.](images/rectangular-workbench-500px.jpg)

워크벤치를 반올림할 수 있는 인사이트를 확보했으므로 여러분이 서 있어야 하는 "전면" 또는 명확한 위치가 없었습니다. 이를 테스트할 때 사람들이 갑자기 주변을 이동하고 자신의 생성을 탐색하기 시작했습니다.

![순환 워크벤치 디자인은 사용자가 생성을 진행하도록 권장했습니다.](images/circular-workbench-500px.jpg)

**습득한 지식**

항상 사용자에게 익숙한 것에 대해 생각해야 합니다. 물리적 공간을 활용하는 것은 HoloLens 멋진 기능이며 다른 디바이스로는 수행할 수 없는 일입니다.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>문제 #2: 모달 대화 상자가 홀로그램 프레임에서 벗어나는 경우가 있습니다.

경우에 따라 사용자가 앱에서 주의가 필요한 것과 다른 방향을 보고 있을 수 있습니다. PC에서 대화 상자를 팝업할 수 있지만, 3D 환경의 다른 사람의 얼굴에서 이 작업을 수행하면 대화 상자가 방해가 되는 것처럼 보일 수 있습니다. 메시지를 읽는 데 필요하지만, 메시지를 읽지 못하게 하는 것이 직관적입니다. 이 반응들은 게임을 하는 경우 좋지만, 작업을 위해 설계된 도구에서는 이상적이지 않습니다.

몇 가지 다른 사항을 시도한 후 마지막으로 대화에 "사고 거품형" 시스템을 사용하기로 했고, 사용자가 애플리케이션에서 주의가 필요한 위치를 따라갈 수 있는 텐드릴을 추가했습니다. 또한 사용자가 이동 위치를 알 수 있도록 방향성을 암시하는 tendrils 펄스를 만들었습니다.

!["Thought Bubble" 시스템에는 방향성을 제공하여 앱에서 사용자의 주의가 필요한 위치로 안내하는 펄스 텐드릴이 포함되었습니다.](images/thought-bubble-500px.jpg)

**습득한 지식**

3D에서는 사용자에게 주의해야 하는 사항에 대해 경고하는 것이 훨씬 더 어렵습니다. [공간 소리,](../design/spatial-sound.md)광원 또는 사고 거품과 같은 주의 주의를 기울이면 사용자가 필요한 위치로 이어질 수 있습니다.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>문제 #3: 경우에 따라 UI가 다른 홀로그램에 의해 차단될 수 있습니다.

사용자가 홀로그램 및 연결된 UI 컨트롤과 상호 작용하려고 하지만 다른 홀로그램이 앞에 있기 때문에 보기에서 차단되는 경우가 있습니다. HoloStudio 개발하는 동안 이에 대한 해결 방법을 제시하기 위해 시행착오를 사용했습니다.

![홀로그램과 연결된 UI 컨트롤은 홀로그램과 사용자 사이에 다른 홀로그램이 있는 경우 차단될 수 HoloLens.](images/ui-blocked-500px.jpg)

차단할 수 없도록 사용자에게 더 가깝게 UI 컨트롤을 이동하려고 했지만, 사용자가 멀리 떨어져 있는 홀로그램을 동시에 보는 동안 가까운 컨트롤을 보는 것이 불편하다는 것을 알게 됩니다. 그러나 가장 가까운 홀로그램 앞에 있는 컨트롤을 사용자에게 이동한 경우 영향을 주어야 하는 홀로그램에서 분리된 것처럼 보입니다.

결국 UI 컨트롤을 고스팅하고 연결된 홀로그램과 사용자로부터 동일한 거리에 배치하여 둘 다 연결되어 있다고 느낄 수 있습니다. 이렇게 하면 가려져 있더라도 사용자가 컨트롤과 상호 작용할 수 있습니다.

![해결 방법: 컨트롤과의 상호 작용을 허용하고 영향을 주는 홀로그램에 연결된 느낌을 주는 UI 컨트롤을 고스트했습니다.](images/ghosting-ui-500px.jpg)

**습득한 지식**

사용자는 차단된 경우에도 UI 컨트롤에 쉽게 액세스할 수 있어야 하므로 홀로그램이 실제 위치에 관계없이 작업을 완료할 수 있도록 하는 방법을 알아내야 합니다.

## <a name="about-the-author"></a>작성자 정보

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>2018년 3월 20일</b><br>수석 Holographic Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>추가 정보
* [Instinctual 상호 작용](../design/interaction-fundamentals.md)
