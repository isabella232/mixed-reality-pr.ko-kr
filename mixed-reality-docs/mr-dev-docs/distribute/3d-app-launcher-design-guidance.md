---
title: 3D 앱 시작 관리자 디자인 지침
description: 3D 앱 시작 관리자는 사용자의 혼합 현실 주택에서 앱을 시작하도록 선택할 수 있는 "물리적" 개체입니다.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 3D 앱 시작 관리자, 몰입형 헤드셋, 라이브 큐브, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, UWP, Win32, 조명, 색
ms.openlocfilehash: 2d93930d63b251aa91d77c96b4d5250baba54c51de50388f690b3588b1580761
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188529"
---
# <a name="3d-app-launcher-design-guidance"></a>3D 앱 시작 관리자 디자인 지침

Windows Mixed Reality 몰입형(VR) 헤드셋을 누르면 Windows Mixed Reality 홈으로 들어갑니다. 집 은 산과 물로 둘러싸인 작은 집으로 시각화되지만 다른 환경을 선택하고 고유한 를 [만들 수도 있습니다.](../design/add-custom-home-environments.md) 홈 공간 내에서 사용자는 원하는 방식으로 관심 있는 3D 개체 및 앱을 자유롭게 정렬하고 구성할 수 있습니다. **3D 앱 시작** 관리자는 사용자의 혼합 현실 주택에서 앱을 시작하도록 선택할 수 있는 "물리적" 개체입니다.

![예: Floaty Bird 3D 앱 시작 관리자](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Floaty Bird 3D 앱 시작 관리자 예제(가상의 앱)*

## <a name="3d-app-launcher-creation-process"></a>3D 앱 시작 관리자 만들기 프로세스

3D 앱 시작 관리자를 만드는 3단계는 다음과 같습니다.

1. 디자인 및 개념(이 문서)
2. [모델링 및 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 애플리케이션에 통합:
    * [UWP 앱](implementing-3d-app-launchers.md)
    * [Win32 앱](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>설계 개념

### <a name="fantastic-yet-familiar"></a>친숙하면서도 친숙합니다.

앱 시작 관리자가 있는 Windows Mixed Reality 환경은 친숙한 부분인 능동적/sci-fi입니다. 가장 적합한 시작 관리자가 이 세계의 규칙을 따릅니다. 앱에서 친숙하고 대표적인 개체를 사용하지만 실제 현실의 규칙 중 일부를 익히는 방법을 생각해 보세요. 매직이 발생합니다.

### <a name="intuitive"></a>직관적인

앱 시작 관리자를 살펴보면 앱을 시작하는 목적이 분명해야 하며 혼동을 일으키면 안 됩니다. 예를 들어 시작 관리자가 앱의 명백한 대표이기 때문에 클리프 하우스 혼동하지 않도록 해야 합니다. 앱 시작 관리자가 터치/선택하도록 사람을 초대해야 합니다.

![예제: Fresh Note 3D 앱 시작 관리자](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Fresh Note 3D 앱 시작 관리자 예제(가상의 앱)*

### <a name="home-scale"></a>홈 규모

3D 앱 시작 관리자가 클리프 하우스 있으며 해당 기본 크기는 공간의 다른 "물리적" 개체와 함께 사용해야 합니다. 집 공장 또는 일부 주택 옆에 시작 관리자를 배치하는 경우 집처럼 크기가 넓은 집처럼 느낄 수 있습니다. 좋은 시작점은 30 입방형 cm의 모양을 확인하는 것이지만, 사용자가 원한다면 확장하거나 축소할 수 있습니다.

### <a name="own-able"></a>자체 가능

앱 시작 관리자가 사람이 자신의 공간에 가지고 싶어 하는 개체처럼 느낄 수 있습니다. 이러한 항목으로 가상으로 자신을 둘러볼 수 있으므로 시작 관리자는 사용자가 찾아서 가까이 두기에 충분히 바람직하다고 생각한 것 같은 느낌을 주어야 합니다.

![예: Astro Warp 3D 앱 시작 관리자](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Astro Warp 3D 앱 시작 관리자 예제(가상의 앱)*

### <a name="recognizable"></a>인식할

3D 앱 시작 관리자가 "앱의 브랜드"를 보는 사람에게 즉시 표현해야 합니다. 앱에 별표 문자 또는 특히 식별 가능한 개체가 있는 경우 이를 디자인의 중요한 부분으로 사용하는 것이 좋습니다. 혼합 현실 세계에서 개체는 단순히 로고만 하는 것보다 사용자로부터 더 많은 관심을 끌어들입니다. 인식할 수 있는 개체는 브랜드와 빠르고 명확하게 통신합니다.

### <a name="volumetric"></a>체적

앱은 단순히 로고를 평면에 놓고 하루에 호출하는 것 이상의 것을 좋아합니다. 시작 관리자는 사용자 공간에서 흥미로운 3D 물리적 개체처럼 느낄 수 있습니다. 좋은 방법은 앱이 Macy's 1일차에 풍선이 있다고 상상해보는 것입니다. 사람들이 거리를 따라 내려와서 정말 무엇을 할 수 있을까요?라고 스스로에게 물어보세요. 모든 보기 각도에서 어떤 모양이 좋을까요?

:::row:::
    :::column:::
        ![로고 전용 ](images/20171016-140436-mixedreality-640px.jpg) *로고만*
    :::column-end:::
    :::column:::
        ![문자로 더 잘 ](images/20171016-140557-mixedreality-640px.jpg) *인식 가능 문자로 인식 가능*
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![평면 접근 방식은 놀라울 정도로 평면적인 느낌을 ](images/20171016-155101-mixedreality-640px.jpg) *줍니다. 평면적인 느낌을 줍니다.*
    :::column-end:::
    :::column:::
        ![볼륨 접근 방식은 앱을 더 잘 보여 줍니다. ](images/20171016-161407-mixedreality-640px.jpg) *Volumetric 접근 방식은 앱을 더 잘 보여 줍니다.*
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a>좋은 3D 모델에 대한 팁

* 앱 시작 관리자에 대한 차원을 계획할 때는 대략 30cm 큐브에 대해 를 곱합니다. 따라서 1:1:1 크기 비율입니다.
* 모델은 10,000개 미만의 다각형이어야 합니다. [삼각형 개수 및 세부 정보 수준(LOD)에 대해 자세히 알아보기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* 몰입형 헤드셋에서 테스트합니다.
* 가능한 경우 모델의 기하 도형에 세부 정보를 빌드합니다. 자세한 내용은 질감에 의존하지 마세요.
* "물 닫힌" 닫힌 기하 도형을 빌드합니다. 모델링되지 않은 구멍이 없습니다.
* 개체에서 자연 재질을 사용합니다. Imagine 실제 세계에서 만들 수 있습니다.
* 모델이 서로 다른 거리와 크기로 잘 읽혀 있는지 확인합니다.
* 모델을 사용할 준비가 되면 자산 [내보내기 지침 을 참조하세요.](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)

![질감에 미묘한 세부 정보가 있는 모델](images/20171013-143334-mixedreality-640px.jpg)<br>
*질감에 미묘한 세부 정보가 있는 모델*

### <a name="what-to-avoid"></a>피해야 할 사항

* 고대비 세부 정보 또는 작고 사용량이 많은 패턴과 질감을 사용하지 마세요.
* 씬 기하 도형을 사용하지 마세요. 멀리서 잘 작동하지 않으며 별칭이 잘못된 것입니다.
* 모델의 일부가 1:1:1 크기 비율을 초과하여 확장되지 않도록 합니다. 크기 조정 문제가 발생합니다.

![고대비, 사용량이 적은 패턴 방지](images/20171013-143603-mixedreality-640px.jpg)<br>
*고대비, 작고 사용량이 많은 패턴 방지*

## <a name="how-to-handle-type"></a>형식을 처리하는 방법

* 형식은 앱 시작 관리자의 약 1/3 이상을 차지하는 것이 좋습니다. 형식은 시작 관리자가 실제로 시작 관리자라는 아이디어를 사람들에게 제공하는 주요 것이므로 상당한 경우 좋습니다.
* 형식을 매우 광범위하게 만들지 않도록 하세요. 앱 시작 관리자 핵심 차원의 범위 내에서 유지합니다(더 많거나 적음).
* 플랫 형식은 작동할 수 있지만 특정 각도 및 특정 환경에서 보기 어려울 수 있습니다. 이 작업을 돕기 위해 이 개체를 실선 개체로 배치하거나 그 뒤에 배치하는 것이 좋습니다.
* 형식에 차원을 추가하면 3D에서 멋진 느낌을 줍니다. 형식의 측면을 다른 어두운 색으로 음영 처리하면 가독성에 도움이 될 수 있습니다.

:::row:::
    :::column:::
        ![배경이 없는 평면 형식은 특정 각도에서 보기 어려울 수 있으며 특정 환경에서는 ](images/flattype-640px.png) *배경이 없는 플랫 형식은 특정 각도 및 특정 환경에서 보기 어려울 수 있습니다.*
    :::column-end:::
    :::column:::
        ![기본 제공 배경이 있는 형식은 잘 작동할 수 ](images/flattypeandbkg-640px.png) *있습니다. 기본 제공 배경이 있는 형식은 잘 작동할 수 있습니다.*
    :::column-end:::
    :::column:::
        ![면의 음영을 처리하면 돌출된 ](images/20171016-160221-mixedreality-640px.jpg) *형식이 잘 작동할 수 있습니다.*
    :::column-end:::
:::row-end:::

**작동하는 형식 색**

* 흰색
* 검정
* 밝은 반포도 색

![작동하는 색을 입력합니다.](images/20171016-112111-mixedreality-640px.jpg)<br>
*작동하는 형식 색*

### <a name="colors-to-avoid"></a>방지할 색

문제를 일으키는 형식 색은 다음과 같습니다.

* 중간 톤
* 회색
* 과도하게 채도된 색 또는 디스포일된 색

![문제를 일으키는 형식 색입니다.](images/20171016-112246-mixedreality-640px.jpg)<br>
*문제를 일으키는 형식 색*

## <a name="lighting"></a>조명

앱 시작 관리자의 조명은 클리프 하우스 환경에서 제공됩니다. 조명과 그림자 모두에서 잘 보이도록 집 안의 여러 곳에서 시작 관리자를 테스트해야 합니다. 좋은 점은 이 문서의 다른 디자인 지침을 따른 경우 시작 관리자의 모양이 클리프 하우스 대부분의 조명에 적합해야 한다는 것입니다.

환경의 다양한 조명에서 시작 관리자가 어떻게 보이는지 테스트할 수 있는 좋은 위치는 Studio, Media Room, 집 바깥쪽 및 백도어(자가 있는 구체적인 영역)입니다. 또 다른 좋은 테스트는 반조와 반 그림자에 배치하고 어떻게 표시되는지 확인하는 것입니다.

![시작 관리자가 밝은 그림자와 그림자 모두에서 잘 보이는지 확인합니다.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*시작 관리자가 밝은 그림자와 그림자 모두에서 양호한지 확인합니다.*

## <a name="texturing"></a>텍스처링

### <a name="authoring-your-textures"></a>질감 작성

3D 앱 시작 관리자의 끝 형식은 PBR(물리적 기반 렌더링) 파이프라인을 사용하여 만들어지는 .glb 파일입니다. 이 프로세스는 까다로운 프로세스일 수 있습니다. 이제 기술 전문가를 고용해보는 것이 좋습니다( 아직 하지 않은 경우). DIY-er라는 미식적인 경우 [PBR 용어를 연구하고 학습하는](https://wiki.polycount.com/wiki/PBR) 데 시간을 할애하고 시작하기 전에 어떤 일이 발생하는지 알아보면 일반적인 실수를 방지하는 데 도움이 됩니다. 

![예제: Fresh Note 앱](images/pbr-freshnote1-640px-500px.png)<br>
*Fresh Note 3D 앱 시작 관리자 예제(가상의 앱)*

### <a name="recommended-authoring-tool"></a>권장 제작 도구

최종 파일을 작성하려면 [을](https://www.allegorithmic.com/products/substance-painter) 사용하는 것이 좋습니다. 여기서는 을 통해 을 작성할 수 [있습니다.](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)

(또는 이러한 항목 중 하나에 대해 더 잘 알고 있는 경우 [3D-경우에 따라 3D-경우에](https://3dcoat.com/home/)따라 [3D-경우에](https://quixel.se/suite2/)따라 Suite 2 또는 [Marmoset Toolbag이](https://www.marmoset.co/toolbag/) 작동합니다.)

### <a name="best-practices"></a>모범 사례

* 앱 시작 관리자 개체가 PBR용으로 작성된 경우 클리프 하우스 환경에 맞게 간단하게 변환할 수 있어야 합니다.
* 셰이더에는 Metal/Roughness 작업 흐름이 있습니다. Unreal PBR 셰이더가 가까운 팩시밀리입니다.
* 질감을 내보낼 때 [권장되는 질감 크기를](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) 염두에 두어야 합니다.
* 실시간 조명을 위해 개체를 빌드해야 합니다. 즉, 다음을 의미합니다.
  * 섀도 피하거나 그림자를 그렸습니다.
  * 질감에서 베이킹된 조명 방지
  * PBR 재질 제작 패키지 중 하나를 사용하여 셰이더에 대해 생성된 올바른 맵을 얻습니다.

## <a name="see-also"></a>참고 항목

* [혼합 현실 홈 사용할 3D 모델 만들기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [3D 앱 시작 관리자(UWP 앱) 구현](implementing-3d-app-launchers.md)
* [3D 앱 시작 관리자(Win32 앱) 구현](implementing-3d-app-launchers-win32.md)
