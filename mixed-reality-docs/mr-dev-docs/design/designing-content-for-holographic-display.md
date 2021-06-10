---
title: Holographic 디스플레이용 콘텐츠 디자인
description: HoloLens 디바이스의 홀로그램 디스플레이에 대한 디자인 지침 및 모범 사례에 대해 알아봅니다.
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI 디자인, 홀로그램 디스플레이, 콘텐츠 디자인, 어두운 테마, 밝은 테마, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 디자인, 픽셀
ms.openlocfilehash: 2c68acb5478bfbd438c8bbb9dd2f8d9686bcefc5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600322"
---
# <a name="designing-content-for-holographic-display"></a>Holographic 디스플레이용 콘텐츠 디자인

![Ulnar 측면 손 위치](images/UX_Hero_DarkTheme.jpg)

홀로그램 디스플레이에 대한 콘텐츠를 디자인할 때 최상의 환경을 달성하기 위해 고려해야 하는 몇 가지 요소가 있습니다. 아래에 몇 가지 권장 사항이 나와 있으며 [색, 광원 및 재질](color-light-and-materials.md) 페이지에서 홀로그램 디스플레이의 특징에 대해 자세히 알아볼 수 있습니다.

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>큰 표면에서 밝은 색의 문제 

HoloLens 경험 연구 및 테스트에 따라 디스플레이의 큰 영역에서 밝은 색을 사용하면 다음과 같은 몇 가지 문제가 발생할 수 있음을 발견했습니다. 

**눈의 안과** 

홀로그램 표시는 가감기이므로 밝은 색의 홀로그램은 더 많은 광원을 사용합니다. 디스플레이의 큰 영역에 있는 밝고 단색으로 인해 사용자의 시선이 쉽게 발생할 수 있습니다. 

**손 폐색** 

밝은 색은 개체와 직접 상호 작용할 때 사용자가 손을 보기 어렵게 만듭니다. 사용자는 손을 볼 수 없으므로 손/손가락과 대상 표면 사이의 깊이/거리를 인식하기가 어려워집니다. 손가락 커서는 이 문제를 보정하는 데 도움이 되지만 밝은 흰색 표면에서는 여전히 어려울 수 있습니다. 

![색 및 손 폐색 ](images/color_handocclusion.jpg)
 *밝은 색 콘텐츠 백플레이트에서 손을 보기 어렵습니다.*

**색 균일성**

홀로그램 디스플레이의 특성으로 인해 디스플레이의 큰 밝은 영역은 blotlot이 될 수 있습니다. 어두운 색 구성표를 사용하면 이 문제를 최소화할 수 있습니다. 

## <a name="design-guidelines-for-color-choices"></a>색 선택에 대한 디자인 지침

**UI 배경에 어두운 색 사용**

어두운 색 구성표를 사용하면 눈의 집중을 최소화하고 직접 손 조작에 대한 신뢰도를 높일 수 있습니다. 

![콘텐츠 배경에 사용되는 어두운 색의 예 콘텐츠 ](images/color_dark_examples.jpg)
 *배경에 사용되는 어두운 색의 예*

**세미볼트 또는 굵은 글꼴 두께 사용**

HoloLens를 사용하면 환경이 멋진 고해상도 텍스트를 표시할 수 있습니다. 그러나 세로 스트로크가 작은 글꼴 크기로 지터링할 수 있으므로 밝게 또는 반광과 같은 씬 글꼴 두께를 방지하는 것이 좋습니다. 

![굵게 또는 반굵은 글꼴 두께(위쪽 패널)는 가독성을 ](images/color_font_examples.jpg)
 *향상시키거나 굵게 또는 반굵게 글꼴 두께(위쪽 패널)를 개선하여 가독성을 향상시킵니다.*

**MRTK의 HolographicBackplate 재질 사용**

HolographicBackplate 재질은 HoloLens 셸의 여러 UI 패널에 적용됩니다. 해당 기능 중 하나는 패널에 따라 위치를 이동할 때 사용자에게 표시되는 재정의 효과입니다. 백플래트 색은 미리 정의된 스펙트럼에서 약간 이동하며, 콘텐츠 가독성을 방해하지 않고 매력적인 동적 시각적 효과를 만듭니다. 이러한 미묘한 색 변화로 사소한 색 불규칙도를 보정할 수도 있습니다. 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>투명 또는 반투명 UI 백플래트 문제 

![투명한 UI 예제 투명 ](images/color_transparent_examples.jpg)
 *UI 백플레이트 예*

**시각적 복잡성 및 접근성**

홀로그램 개체는 실제 환경과 혼합되므로 투명 또는 반투명 창의 콘텐츠 또는 UI 가독성이 저하될 수 있습니다. 또한 투명 홀로그램 개체가 서로 위에 오버레이되는 경우 혼동되는 깊이로 인해 사용자가 상호 작용하기 어려울 수 있습니다.

**성능**

투명 또는 반투명 개체가 올바르게 렌더링하려면 백그라운드에 있는 개체와 정렬하고 혼합해야 합니다. 투명 개체 정렬에는 CPU 비용이 적고 혼합 시 상당한 GPU 비용이 듭니다. GPU가 z 선별(즉, 선별)을 통해 숨겨진 표면 제거를 수행할 수 없기 때문입니다. 깊이 테스트). 숨겨진 표면 제거를 허용하지 않을 경우 최종 렌더링된 픽셀에 필요한 작업 수가 증가합니다. 이로 인해 더 많은 압력 채우기 속도 제약 조건이 적용됩니다.

**깊이 LSR 기술의 홀로그램 안정성 문제**

홀로그램 다시 프로젝션 또는 홀로그램 안정성을 개선하기 위해 애플리케이션은 렌더링된 모든 프레임에 대해 깊이 버퍼를 시스템에 제출할 수 있습니다. 다시 프로젝션에 깊이 버퍼를 사용하는 경우 렌더링된 모든 픽셀에 해당하는 깊이의 깊이 버퍼를 작성해야 합니다. 깊이 값이 있는 모든 픽셀에는 색 값도 있어야 합니다. 위의 지침을 따르지 않으면 유효한 깊이 정보가 없는 렌더링된 이미지의 영역이 종종 파동과 같은 왜곡으로 표시되는 아티팩트 생성 방식으로 다시 프로젝션될 수 있습니다.


## <a name="design-guidelines-for-transparent-elements"></a>투명 요소에 대한 디자인 지침

**불투명 UI 배경 사용**

기본적으로 투명 또는 반투명 개체는 적절한 혼합을 허용하기 위해 깊이를 작성하지 않습니다. 이 문제를 완화하는 방법은 불투명 개체 사용, 불투명 개체(예: 불투명 백플래트 앞에 반투명 단추) 가까이 표시, 반투명 개체가 깊이를 쓰도록 강제 적용(모든 시나리오에 적용되지 않음) 또는 프레임 끝에 깊이 값만 기여하는 프록시 개체 렌더링 등이 있습니다.

MRTK-Unity 내의 솔루션: /windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity  

단색 및 불투명 백플레이트를 사용하여 가독성 및 상호 작용 신뢰도를 보호할 수 있습니다.

**영향을 받는 픽셀 수 최소화**

프로젝트에서 투명 개체를 사용해야 하는 경우 영향을 받는 픽셀 수를 최소화합니다. 예를 들어 개체가 가감 효과와 같은 특정 조건에서만 표시되는 경우 가감 색을 검은색으로 설정하는 대신 완전히 보이지 않을 때 개체를 사용하지 않도록 설정합니다. 알파 마스크가 있는 쿼드를 사용하여 만든 간단한 2D 도형의 경우 불투명 셰이더를 사용하여 셰이프의 메시 표현을 대신 만드는 것이 좋습니다. 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity용 MRTK(Mixed Reality Toolkit)의 어두운 UI 예제

**[MRTK는](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 어두운 색 구성표를 기반으로 하는 많은 UI 구성표 예제를 제공합니다.

* [Near 메뉴](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
* [대화 상자](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)
* [손 메뉴](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="see-also"></a>참조

* [색, 광원 및 재질](color-light-and-materials.md)
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