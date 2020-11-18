---
title: Holographic 디스플레이용 콘텐츠 디자인
description: Holographic 표시에 대 한 디자인 지침 및 모범 사례
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI 디자인, holographic 표시, 콘텐츠 디자인, 어두운 테마, 밝은 테마, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, 혼합 현실 도구 키트, 디자인, 픽셀
ms.openlocfilehash: ea3fbda7aff80f0878521deb433c88b16abeab19
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702639"
---
# <a name="designing-content-for-holographic-display"></a>Holographic 디스플레이용 콘텐츠 디자인

![Ulnar 사이드 위치](images/UX_Hero_DarkTheme.jpg)

Holographic에 대 한 콘텐츠를 디자인할 때 최상의 환경을 달성 하기 위해 고려해 야 하는 몇 가지 요소가 있습니다. 아래 권장 사항 중 일부를 나열 하 고 [색, 조명 및 자료](color-light-and-materials.md) 페이지에서 holographic 디스플레이의 특징에 대해 자세히 알아볼 수 있습니다.

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>넓은 표면에서 밝은 색을 사용 하는 문제 
다양 한 유형의 HoloLens 환경에서 사용자 연구 및 테스트에 따라 디스플레이의 많은 부분에서 밝은 색을 사용 하면 몇 가지 문제가 발생할 수 있습니다. 

**아이 피로** 

Holographic display는 가감 되므로 밝은 색은 더 밝은 색을 사용 하 여 holograms를 표시 합니다. 밝은 영역에서 단색을 사용 하면 사용자에 게 눈에 피로 쉽게 나타날 수 있습니다. 

**손 폐색** 

밝은 색을 사용 하면 개체와 직접 상호 작용할 때 사용자가 손을 볼 수 있습니다. 사용자가 손을 볼 수 없기 때문에 손 모양/손가락 간의 깊이/거리를 대상 화면으로 인식 하기가 어려워집니다. 손가락 커서는이 문제를 보정 하는 데 도움이 되지만 밝은 흰색 표면에서는 여전히 어려울 수 있습니다. 

![색 및 손 폐색는 ](images/color_handocclusion.jpg)
 *밝은 색이 지정 된 콘텐츠 backplate에서 손 모양 보기*

**색 균일성**

Holographic 디스플레이의 특징으로 인해 디스플레이의 밝은 영역이 blotchy 될 수 있습니다. 짙은 색 구성표를 사용 하면이 문제를 최소화할 수 있습니다. 

## <a name="design-guidelines"></a>디자인 지침

**UI 배경에 짙은 색 사용**

진한 색 구성표를 사용 하 여 눈 피로 최소화 하 고 직접 상호 작용에 대 한 신뢰도를 높일 수 있습니다. 

![](images/color_dark_examples.jpg)
*콘텐츠 배경에 사용 되는 짙은 색의* 예제 어두운 UI 예제

**Semibold 또는 굵은 글꼴 두께 사용**

HoloLens를 사용 하면 경험을 통해 멋진 고해상도 텍스트를 표시할 수 있습니다. 그러나 세로 스트로크가 작은 글꼴 크기로 지터 될 수 있으므로 밝은 글꼴 가중치 (예: 밝은 글꼴 또는 반투명)를 사용 하지 않는 것이 좋습니다. 

![진한 UI 예 ](images/color_font_examples.jpg)
 *굵게 또는 반 굵은 글꼴 두께 (위쪽 패널)는 가독성을 향상 시킵니다* .

**MRTK의 HolographicBackplate 재질 사용**

HolographicBackplate 재질은 HoloLens 셸에서 여러 UI 패널에 적용 됩니다. 이러한 기능 중 하나는 패널을 기준으로 위치를 이동할 때 사용자에 게 표시 되는 iridescence 효과입니다. 배경 플레이트 색은 미리 정의 된 스펙트럼에서 조금씩 이동 하 여 콘텐츠 가독성을 방해 하지 않고 뛰어난 동적 시각적 효과를 만듭니다. 이러한 미세한 이동 색은 보조 색 탐지할을 보정 하는 데도 사용 됩니다. 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>투명 또는 반투명 UI 백 판금 관련 챌린지 
![투명 한 UI 예제 ](images/color_transparent_examples.jpg)
 *투명 한 ui 백 판의 예*

**시각적 복잡성 및 접근성**

Holographic 개체는 물리적 환경과 혼합 되므로 투명 하거나 투명 한 창의 콘텐츠나 UI를 더 쉽게 읽을 수 있습니다. 또한 투명 한 개체 들이 서로 위에 중첩 된 경우에는 사용자가 혼동을 holographic 때문에 상호 작용 하기가 어려울 수 있습니다.

**성능**

투명 하거나 투명 한 개체가 올바르게 렌더링 되려면 해당 개체가 배경에 있는 개체와 정렬 되 고 혼합 되어야 합니다. 투명 개체의 정렬에는 CPU 비용이 적당 하 고, 혼합을 사용 하면 GPU에서 z 고르기 (즉, 수준 테스트). 숨겨진 표면 제거를 허용 하지 않으면 렌더링 되는 최종 픽셀에 대해 계산 해야 하는 작업 수가 늘어나고, 따라서 채우기 빈도 제약 조건에 더 많은 부담을 주게 됩니다.

**깊이 LSR 기술에서 홀로그램 안정성 문제**

Holographic reprojection 또는 홀로그램 안정성을 향상 시키기 위해 응용 프로그램은 렌더링 된 모든 프레임에 대 한 깊이 버퍼를 시스템에 제출할 수 있습니다. Reprojection에 깊이 버퍼를 사용 하는 경우 한 가지 규칙에 대해 렌더링 된 모든 색 픽셀에 대해 해당 하는 깊이 값을 깊이 버퍼에 써야 하 고 깊이 값이 있는 모든 픽셀에도 색 값이 있어야 한다는 것입니다. 위의 지침을 따르지 않으면 유효한 깊이 정보가 없는 렌더링 된 이미지 영역이 아티팩트를 생성 하는 방식으로 다시 프로젝션 될 수 있습니다 (종종 물결 모양의 왜곡으로 표시 됨).


## <a name="design-guidelines"></a>디자인 지침
**불투명 UI 배경 사용**

투명 하거나 투명 한 개체는 기본적으로 적절 하 게 혼합 되도록 깊이를 작성 하지 않습니다. 이러한 문제를 완화 하는 방법으로는 불투명 한 개체를 사용 하 여 투명 한 개체를 불투명 한 개체 (예: 불투명 한 판 앞의 반투명 단추)에 가깝게 표시 하거나 투명 한 개체를 투명 한 개체 (모든 시나리오에서는 적용 되지 않음)로 강제 적용 하거나 프레임 끝에 깊이 값을 적용 하는 프록시 개체를 렌더링 합니다.

MRTK-Unity의 솔루션: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity  

단색 및 불투명 백 판을 사용 하 여 가독성 및 상호 작용 신뢰도를 안전 하 게 보호할 수 있습니다.

**영향을 받는 픽셀 수 최소화**

프로젝트에서 투명 개체를 사용 해야 하는 경우 영향을 받는 픽셀 수를 최소화 하십시오. 예를 들어 특정 조건 에서만 개체가 표시 되는 경우 (예: 가산적 네온 효과) 개체를 완전히 표시 하지 않는 경우 (추가 색을 검정으로 설정 하는 대신) 개체를 사용 하지 않도록 설정 합니다. 알파 마스크를 사용 하 여 쿼드를 사용 하 여 만든 간단한 2D 모양의 경우 불투명 셰이더를 사용 하 여 모양의 망상 표시를 만드는 것이 좋습니다. 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 용 MRTK (Mixed Reality Toolkit)의 어두운 UI 예제
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 짙은 색 체계를 기반으로 다양 한 UI 빌딩 블록 예제를 제공 합니다.

* [메뉴 근처](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [대화 상자](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [손 모양 메뉴](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


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
