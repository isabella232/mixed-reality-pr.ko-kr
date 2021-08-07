---
title: 빌보딩 및 태그얼롱
description: 혼합 현실 애플리케이션에서 항상 사용자를 상대하도록 지향하는 개체를 사용하는 방법을 알아봅니다.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 스트링, 태그 따라, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 7ffcbe1d3401601e92eb1ac81dfd84f2af9e8e79eeea809b01a1e943a85f0db9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214180"
---
# <a name="billboarding-and-tag-along"></a>빌보딩 및 태그얼롱

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>가장이란?

복습은 혼합 현실의 개체에 적용할 수 있는 동작 개념입니다. 싱이 있는 개체는 항상 사용자를 향하도록 방향을 정합니다. 텍스트 및 메뉴 시스템은 일반적인 사용 사례로, 사용자의 환경에 배치된 정적 개체(세계 잠금)는 사용자가 이동할 때 가려지거나 읽을 수 없게 됩니다.

래핑이 활성화된 개체는 사용자 환경에서 자유롭게 회전할 수 있습니다. 디자인 고려 사항에 따라 단일 축으로 제한될 수도 있습니다. 다른 개체에 너무 가까이 배치되거나 HoloLens 스캔된 표면이 너무 닫히면 비추는 개체가 자신을 잘라내거나 폐색할 수 있습니다. 이를 방지하려면 축에서 회전할 때 개체가 생성할 수 있는 총 공간을 생각해야 합니다.

<br>

---
## <a name="what-is-a-tag-along"></a>태그가란?

태그는 홀로그램에 추가할 수 있는 동작 개념입니다. 태그 따라 개체는 사용자가 편안하게 상호 작용할 수 있는 범위에 유지하려고 합니다.

![HoloLens 핀 패널은 태그가 따라 동작하는 방식의 좋은 예입니다.](images/tagalong-1000px.jpg)<br>
*HoloLens 시작 메뉴 태그 따라 동작의 좋은 예입니다.*

태그 따라 개체에는 동작 방식을 미세 조정할 수 있는 매개 변수가 있습니다. 사용자가 환경을 이동하는 동안 콘텐츠는 사용자의 시야 안이나 외부에 있을 수 있습니다. 이동하면 콘텐츠가 보기의 가장자리 쪽으로 밀어 사용자의 주변을 유지하려고 합니다. 사용자가 이동하는 빈도에 따라 콘텐츠가 일시적으로 보기에서 벗어날 수 있습니다. 사용자가 태그 따라 개체를 응시할 때 더 완벽하게 표시됩니다. 콘텐츠는 항상 "한눈에 보기"라고 생각하므로 사용자는 콘텐츠의 방향을 절대 잊어버리지 않습니다.

추가 매개 변수는 태그와 함께 개체가 밴드에 의해 사용자의 헤드에 연결된 느낌을 줄 수 있습니다. 가속 또는 감속을 강화하면 개체에 가중치가 부여되어 물리적으로 더 많은 느낌을 줍니다. 이 봄 동작은 태그가 작동하는 방식에 대한 정확한 멘탈 모델을 작성하는 데 도움이 되는 어패던스입니다. 오디오는 사용자가 태그 따라 모드에서 개체가 있는 경우에 대한 다른 신호를 제공하는 데 도움이 됩니다. 오디오는 이동 속도를 강화해야 합니다. 빠른 헤드 턴이 더 눈에 띄는 음향 효과를 제공해야 하는 반면, 자연스러운 속도로 복습하는 경우 오디오 효과가 최소화되거나 영향을 미치지 않아야 합니다.

실제로 헤드 잠금된 콘텐츠와 마찬가지로 태그를 따라 이동한 개체는 사용자의 보기에서 너무 많이 이동하거나 너무 많이 움직이면 답할 수 있습니다. 사용자가 주변을 둘러본 후 빠르게 중지하면 해당 감지는 중지되었다고 알려줍니다. 이들의 균형은 머리의 회전이 중지되고 비전이 전 세계의 회전을 중지한다는 것을 알립니다. 그러나 사용자가 중지되었을 때 태그가 계속 이동하면 인식이 혼동될 수 있습니다.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity용 MRTK(Mixed Reality Toolkit)의 스트리밍 및 태그
**[MRTK는](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 스트링 및 태그 따라 동작에 대한 스크립트를 제공합니다. Object.cs 스크립트를 개체에 할당하여 동작을 추가하고 개체가 항상 사용자를 향하도록 합니다. 태그 따라 동작을 추가하려면 RadialView.cs 스크립트를 사용합니다. lerping time, distance 및 degree와 같은 다양한 옵션을 조정할 수 있습니다.

* [MRTK - 방사형 뷰 해결기](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [MRTK - 스크립트](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a>추가 정보

* [커서](cursors.md)
* [손 광선](point-and-commit.md)
* [Button](button.md)
* [상호 작용 가능한 개체](interactable-object.md)
* [경계 상자 및 앱 바](app-bar-and-bounding-box.md)
* [조작](direct-manipulation.md)
* [손 메뉴](hand-menu.md)
* [Near 메뉴](near-menu.md)
* [개체 컬렉션](object-collection.md)
* [음성 명령](voice-input.md)
* [키보드](keyboard.md)
* [Tooltip](tooltip.md)
* [슬레이트](slate.md)
* [슬라이더](slider.md)
* [셰이더](shader.md)
* [빌보딩 및 태그얼롱](billboarding-and-tag-along.md)
* [진행률 표시](progress.md)
* [표면 자성](surface-magnetism.md)