---
title: 색, 광원 및 재질
description: 혼합 현실용 콘텐츠를 디자인하려면 모든 시각적 자산에 대한 색, 조명 및 재질을 신중하게 고려해야 합니다.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 색, 조명, 재질, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 50789faa44e6786c0d9fd0b146daa84f459df451bedc52f06073e742ea8064a0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219868"
---
# <a name="color-light-and-materials"></a>색, 광원 및 재질

![색, 광원 및 재질](images/RemoteRendering.jpg)

혼합 현실용 콘텐츠를 디자인하려면 모든 가상 자산에 대한 색, 조명 및 재질을 신중하게 고려해야 합니다. 미적 목적에는 조명과 재질을 사용하여 몰입형 환경의 어조를 설정하는 것이 포함될 수 있지만, 기능적 목적에는 색을 사용하여 사용자에게 임박한 작업을 경고하는 것이 포함될 수 있습니다. 이러한 각 결정은 환경의 대상 디바이스에 대한 기회 및 제약 조건에 따라 측정되어야 합니다.

다음은 몰입형 헤드셋과 홀로그램 헤드셋 모두에서 자산을 렌더링하는 데 관련된 지침입니다. 이러한 항목 중 대부분은 다른 기술 영역과 밀접하게 연결되어 있으며 관련 주제 목록은 이 문서의 끝에 있는 [참고](color-light-and-materials.md#see-also) 항목 섹션에서 찾을 수 있습니다.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>몰입형 디바이스 및 홀로그램 디바이스에서 렌더링

몰입형 헤드셋에서 렌더링된 콘텐츠는 홀로그램 헤드셋에서 렌더링된 콘텐츠와 비교할 때 시각적으로 다르게 표시됩니다. 몰입형 헤드셋은 일반적으로 2D 화면에서 예상한 대로 콘텐츠를 렌더링하지만, HoloLens 같은 홀로그램 헤드셋은 색 순차적이고, see-through RGB 디스플레이를 사용하여 홀로그램을 렌더링합니다.

항상 홀로그램 헤드셋에서 홀로그램 환경을 테스트하는 데 시간이 소요됩니다. 홀로그램 디바이스용으로 특별히 빌드된 경우에도 콘텐츠의 모양은 보조 모니터, 스냅샷 및 표시줄 보기에서 볼 수 있듯이 다릅니다. 디바이스를 사용하여 환경을 둘러보고, 홀로그램의 조명을 테스트하고, 콘텐츠가 렌더링하는 방식을 모든 면(위 및 아래)에서 관찰해야 합니다. 디바이스에서 다양한 밝기 설정으로 테스트해야 합니다. 모든 사용자가 가정된 기본값과 다양한 조명 조건 집합을 공유할 가능성은 거의 없습니다.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>홀로그램 디바이스에서 렌더링의 기본 사항

* **홀로그램 디바이스에는 가감 디스플레이가** 있습니다. 홀로그램스 실제 세계의 광원에 조명을 추가하여 만들어집니다. 흰색은 밝게 표시되고 검은색은 투명하게 표시됩니다.

* **색에 미치는 영향은 사용자 환경에 따라 다릅니다.** 사용자의실에는 다양한 조명 조건이 있습니다. 명확성을 위해 적절한 수준의 대비를 사용하여 콘텐츠를 만듭니다.

* **동적 조명 방지** – 홀로그램 경험에서 균일하게 조명되는 홀로그램스 가장 효율적입니다. 고급 동적 조명을 사용하면 모바일 디바이스의 기능을 초과할 가능성이 높습니다. 동적 조명이 필요한 경우 Mixed Reality Toolkit 표준 [셰이더](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)를 사용하는 것이 좋습니다. 

## <a name="designing-with-color"></a>색으로 디자인

가감 표시의 특성으로 인해 특정 색이 홀로그램 디스플레이에서 다르게 나타날 수 있습니다. 일부 색은 조명 환경에서 팝되지만 다른 색은 영향이 적은 것으로 표시됩니다. 웜 색이 전경색으로 점프하는 동안 쿨 색은 배경으로 기울어지는 경향이 있습니다. 경험에서 색을 탐색할 때 다음 요소를 고려합니다.

* **밝은 색 렌더링** - 흰색이 밝게 표시되며 드물게 사용해야 합니다. 대부분의 경우 R 235 G 235 B 235와 같은 흰색 값을 고려합니다. 밝은 영역이 크면 사용자 불편이 발생할 수 있습니다. UI 창의 백플레이트의 경우 어두운 색을 사용하는 것이 좋습니다.

* **어두운 색 렌더링** - 가감 표시의 특성으로 인해 어두운 색이 투명하게 표시됩니다. 실선 검은색 개체는 실제 세계와 다르지 않습니다. 아래 알파 채널을 참조하세요. "검정" 모양을 제공하려면 16,16,16과 같은 매우 진한 회색 RGB 값을 사용해 보세요.

* **색 균일성** - 일반적으로 홀로그램은 배경에 관계없이 색 균일성을 유지할 수 있도록 충분히 밝게 렌더링됩니다. 큰 영역은 blotlot이 될 수 있습니다. 밝은 단색의 큰 영역을 사용하지 않습니다.

* **영역** - HoloLens Adobe RGB와 개념적으로 유사한 "넓은 색 영역"의 이점을 누릴 수 있습니다. 따라서 일부 색은 디바이스에서 다양한 품질과 표현을 표시할 수 있습니다.

* **감마** - 렌더링된 이미지의 밝기와 대비는 몰입형 디바이스와 홀로그램 디바이스에 따라 달라집니다. 이러한 디바이스 차이는 색과 그림자의 어두운 영역을 더하거나 덜 밝게 만드는 것처럼 보입니다.

* **색 구분** - "색 구분" 또는 "색 구분"이라고도 하는 색 구분은 사용자가 눈으로 개체를 추적할 때 홀로그램 이동(커서 포함)에서 가장 일반적으로 발생합니다.

## <a name="technical-considerations"></a>기술 고려 사항

* **별칭 -** 홀로그램 기하 도형의 가장자리가 실제 세계를 충족하는 별칭, 가변 또는 "계단 단계"를 고려해야 합니다. 질감을 높은 세부 정보로 사용하면 이 효과를 가져올 수 있습니다. 질감을 매핑하고 필터링을 사용하도록 설정해야 합니다. 홀로그램의 가장자리를 흐리게 하거나 개체 주위에 검은색 가장자리 테두리를 만드는 질감을 추가하는 것이 좋습니다. 가능한 경우 씬 기하 도형을 사용하지 않습니다.

* **알파 채널** - 홀로그램을 렌더링하지 않는 모든 부분에 대해 완전히 투명하도록 알파 채널을 지워야 합니다. 알파를 정의되지 않은 상태로 두면 디바이스에서 이미지/비디오를 찍을 때 또는 [표시자 보기'를 사용하여 시각적 아티팩트로 연결됩니다.

* **질감 질감 -** 광원은 홀로그램 디스플레이에서 가감되므로 의도한 시각적 효과를 생성하지 않는 경우가 많으므로 밝은 단색의 큰 영역을 방지하는 것이 가장 좋습니다.

## <a name="design-guidelines-for-holographic-display"></a>홀로그램 디스플레이에 대한 디자인 지침

![색 및 손 폐색](images/color_handocclusion.jpg)

홀로그램 디스플레이에 대한 콘텐츠를 디자인할 때 최상의 환경을 달성하는 것을 고려해야 하는 몇 가지 요소가 있습니다. 지침 및 권장 사항은 [홀로그램 표시를 위한 콘텐츠 디자인을](designing-content-for-holographic-display.md) 참조하세요.

## <a name="storytelling-with-light-and-color"></a>밝은 색으로 스토리텔링

밝은 색과 색은 홀로그램이 사용자 환경에서 더 자연스럽게 표시되도록 하고 사용자에게 지침과 도움을 제공하는 데 도움이 될 수 있습니다. 홀로그램 환경의 경우 조명 및 색을 탐색할 때 다음 요소를 고려합니다.

:::row:::
    :::column:::
* **Vignetting** - 재질을 어둡게 하는 'vignette' 효과는 사용자가 보기 필드의 가운데에 주의를 기울이는 데 도움이 될 수 있습니다. 이 효과는 사용자의 응시 벡터에서 반경의 홀로그램 재질을 어둡게 합니다. 이는 사용자가 오블리크 또는 눈금 각도에서 홀로그램을 볼 때도 효과적입니다.

* **강조** - 색, 밝기 및 조명을 대조하여 개체 또는 상호 작용 지점에 주의를 기울입니다. 스토리텔링의 조명 방법에 대한 자세한 내용은 [픽셀 단원 - 컴퓨터 그래픽에 대한 조명 접근 방식을 참조하세요.](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)<br>
        <br>
        *이미지: 색을 사용하여 조각의 장면에 표시된 요소를 스토리텔링하는 데 중점을 [둡니다.](https://www.microsoft.com/p/fragments/9nblggh5ggm8)*
    :::column-end:::
        :::column:::
        ![색을 사용하여 조각의 장면에 표시된 스토리텔링 요소에 중점을 둡니다.](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a>재질

:::row:::
    :::column:::
재질은 사실적인 홀로그램을 만드는 데 중요한 요소입니다. 적절한 시각적 특성을 제공하여 실제 환경과 잘 혼합할 수 있는 매력적인 홀로그램 개체를 만들 수 있습니다. 재질은 다양한 유형의 사용자 입력 상호 작용에 대한 시각적 피드백을 제공하는 데도 중요합니다.  

[MRTK는](https://github.com/Microsoft/MixedRealityToolkit-Unity) 시각적 피드백에 사용할 수 있는 다양한 시각적 효과 옵션이 있는 MRTK 표준 셰이더를 제공합니다. 예를 들어 사용자의 손가락이 개체의 표면에 접근하면 '근접 광원' 속성을 사용하여 조명 효과를 제공할 수 있습니다. [MRTK 표준 셰이더에](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) 대해 자세히 알아보기
    :::column-end:::
        :::column:::
    *비디오 루프: 경계 상자에* 
     ![ 근접한 시각적 피드백의 예 손 근접도에 대한 시각적 피드백](images/HoloLens2_Proximity.gif)

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a>추가 정보
* [Holographic 디스플레이용 콘텐츠 디자인](designing-content-for-holographic-display.md)
* [색 구분](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [홀로그램](../discover/hologram.md)
* [Microsoft 디자인 언어 - 색](https://www.microsoft.com/design/color)
* [유니버설 Windows 플랫폼 - 색](/windows/uwp/style/color)