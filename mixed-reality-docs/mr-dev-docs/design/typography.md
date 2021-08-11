---
title: 입력 체계
description: 혼합 현실 앱 환경의 정보를 제공하기 위한 중요한 요소로 텍스트를 디자인하고 구현하는 방법을 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 스타일, 글꼴, 입력 체계, ui, ux, 텍스트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens
ms.openlocfilehash: 7df2386f3478c0b0b79d198a3342bc9a9a061f6e5a305baedcd91be9c2f09f04
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200324"
---
# <a name="typography"></a>입력 체계

![HoloLens 입력 체계 예제](images/typography-cover.png)<br>


텍스트는 앱 환경의 정보를 제공하는 데 중요한 요소입니다. 2D 화면의 입력 체계처럼 목표는 명확하고 읽기 쉬운 것입니다. 혼합 현실의 3차원 측면을 통해 텍스트 및 전반적인 사용자 경험에 훨씬 더 큰 영향을 줄 수 있습니다.

3D의 형식에 대해 설명하면 대용량 3D 텍스트가 돌출된 것으로 생각하는 경향이 있습니다. 일부 로고 형식 디자인과 일부 다른 제한된 애플리케이션을 제외하고, 돌출된 텍스트는 텍스트의 가독성을 저하하는 경향이 있습니다. 3D에 대한 환경을 디자인하는 경우에도 읽기 쉽고 읽기 쉽기 때문에 형식에 2D를 사용합니다.

HoloLens 형식은 가감 색 시스템을 기반으로 조명을 사용하여 홀로그램으로 생성됩니다. 다른 홀로그램과 마찬가지로 형식은 모든 각도에서 세계를 잠그고 관찰할 수 있는 실제 환경에 배치할 수 있습니다. 형식과 환경 간의 [시차](https://en.wikipedia.org/wiki/Parallax) 효과도 환경에 깊이를 더합니다.

## <a name="typography-in-mixed-reality"></a>혼합 현실의 입력 체계

혼합 현실의 입력 체계 규칙은 다른 곳과 다르지 않습니다. 실제 세계와 가상 세계의 텍스트는 읽을 수 있고 읽을 수 있어야 합니다. 텍스트는 벽 위에 있거나 실제 개체에 중첩될 수 있습니다. 디지털 사용자 인터페이스와 함께 부동일 수 있습니다. 컨텍스트에 관계없이 읽기 및 인식에 동일한 입력 체계 규칙을 적용합니다.

### <a name="create-clear-hierarchy"></a>명확한 계층 구조 만들기

다양한 형식 크기 및 가중치를 사용하여 대비 및 계층 구조를 빌드합니다. 형식 램프를 정의하고 앱 환경 전체에서 이를 수행하면 일관된 정보 계층 구조를 갖춘 뛰어난 사용자 환경을 제공할 수 있습니다.

![유형 램프 예제](images/typography-ramp-1000px.jpg)<br>
*형식 램프를 정의하고 앱 환경 전체에서 따릅니다.*

### <a name="limit-your-fonts"></a>글꼴 제한

단일 컨텍스트에서 두 개 이상의 다른 글꼴 패밀리를 사용하지 마십시오. 글꼴이 너무 많으면 환경의 일관성과 일관성이 끊어지고 정보를 사용하는 것이 더 어려워집니다. HoloLens 정보가 물리적 환경 위에 오버레이되므로 너무 많은 글꼴 스타일을 사용하면 환경이 저하됩니다. 맑은 고딕 모든 Microsoft 디지털 디자인의 글꼴입니다. Windows Mixed Reality 셸에서 일관되게 사용됩니다. Windows 디자인 도구 키트 페이지에서 맑은 고딕 글꼴 파일을 [다운로드할](/windows/uwp/design-downloads/)수 있습니다.

[맑은 고딕 서체에 대한 자세한 정보](/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>씬 글꼴 두께 방지

씬 세로 스트로크가 진동하고 가독성이 저하되므로 42pt 미만의 형식 크기에는 밝은 글꼴 또는 반광 글꼴 두께를 사용하지 마십시오. 스트로크 두께가 충분한 최신 글꼴이 잘 작동합니다. 예를 들어 Helvetica 및 Arial은 일반 또는 굵은 두께를 사용하여 HoloLens 읽을 수 있습니다.

### <a name="color"></a>색

HoloLens 홀로그램은 가감 광원 시스템으로 생성되므로 흰색 텍스트는 매우 읽기 쉬운 것입니다. 시작 메뉴 및 앱 표시줄에서 흰색 텍스트의 예를 찾을 수 있습니다. HoloLens 백플레이스 없이는 흰색 텍스트가 잘 작동하지만 복잡한 물리적 배경 때문에 형식을 읽기 어려울 수 있습니다. 어둡거나 색이 있는 뒷판에 흰색 텍스트를 사용하여 사용자의 포커스를 개선하고 물리적 배경에서 방해를 최소화하는 것이 좋습니다.

<br>


![어둡거나 색이 있는 뒷판에 흰색 텍스트를 사용하는 것이 좋습니다. ](images/typography-whiteonblack2-1000px.jpg)
 *어둡거나 색이 있는 뒷판에 있는 흰색 텍스트의 예입니다.*
<br>

어두운 텍스트를 사용하려면 밝은 뒤로판을 사용하여 읽을 수 있도록 해야 합니다. 가감 색 시스템에서 검은색은 투명하게 표시됩니다. 즉, 색이 있는 뒷판이 없으면 검은색 텍스트가 표시되지 않습니다.

:::row:::
    :::column:::
        ![흰색 텍스트의 흰색과 검은색의 예](images/typography-whiteonblack.png)<br>
        *흰색 텍스트의 흰색과 검은색의 예*<br>
    :::column-end:::
    :::column:::
        ![시스템 앱의 검은색 텍스트 예 - 스토어 및 설정](images/640px-typography-blackonwhite.jpg)<br>
        *시스템 앱의 검은색 텍스트 예 - 스토어 및 설정*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>권장되는 글꼴 크기

예상할 수 있듯이 PC 또는 태블릿 디바이스에서 사용하는 형식 크기(일반적으로 12~32pt 사이)는 2미터의 거리만큼 작게 보입니다. 각 글꼴의 특성에 따라 달라지지만 일반적으로 권장되는 최소 보기 각도와 가독성을 위한 글꼴 높이는 사용자 연구 연구를 기반으로 약 0.35°-0.4°/12.21-13.97mm입니다. [Unity의 텍스트](../develop/unity/text-in-unity.md) 페이지에 도입된 배율 비율은 약 35-40pt입니다. 

0.45m(45cm)에서 가까운 상호 작용의 경우 읽을 수 있는 최소 글꼴의 보기 각도와 높이는 0.4°-0.5° / 3.14–3.9mm입니다. [Unity의 텍스트](../develop/unity/text-in-unity.md)에 도입된 배율 비율은 약 9~12pt입니다.

![근거리 및 원거리 상호 작용 범위 ](images/typography-distance-1000px.jpg)
 *근거리 및 원거리 상호 작용 범위의 콘텐츠*

### <a name="the-minimum-legible-font-size"></a>읽을 수 있는 최소 글꼴 크기

| 거리 | 시야각 | 텍스트 높이 | 글꼴 크기** |
|---------|---------|---------|---------|
| 45cm(직접 조작 거리) | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2m | 0.35°-0.4° | 12.21–13.97mm | 34.63-39.58pt |

### <a name="the-comfortably-legible-font-size"></a>읽을 수 있는 편안하게 읽을 수 있는 글꼴 크기

| 거리 | 시야각 | 텍스트 높이 | 글꼴 크기** |
|---------|---------|---------|---------|
| 45cm(직접 조작 거리) | 0.65°-0.8° | 5.1-6.3mm | 14.47-17.8pt |
| 2m | 0.6°-0.75° | 20.9-26.2mm | 59.4-74.2 pt |


맑은 고딕(Windows 기본 글꼴)는 대부분의 경우 잘 작동합니다. 씬 세로 스트로크가 진동하고 가독성이 저하되므로 작은 크기의 밝은 글꼴 또는 반조 글꼴 패밀리를 사용하지 마십시오. 스트로크 두께가 충분한 최신 글꼴이 잘 작동합니다. 예를 들어 Helvetica 및 Arial은 일반 또는 굵은 가중치로 HoloLens 읽을 수 있습니다.

**Unity의 텍스트 크기 계산에 대한 자세한 내용은 Unity의 [텍스트를 참조하세요.](../develop/unity/text-in-unity.md)**

![보기 각도 ](images/Text_In_Unity_ViewingAngle.jpg)
 *보기 거리, 각도 및 텍스트 높이*

<br>

---

## <a name="resources"></a>리소스

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[Segoe 글꼴](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    (Zip 파일)<br>
    ### <a name="hololens-fontbr"></a>[HoloLens 글꼴](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    (Zip 파일)<br>
    <br>
    *이미지: HoloLens 글꼴은 Windows Mixed Reality 사용되는 기호 문자 모양을 제공합니다.*
    :::column-end:::
        :::column:::
        ![HoloLens 글꼴은 에 사용되는 기호 문자 모양을 제공합니다Windows Mixed Reality](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a>추가 정보

* [Unity의 텍스트](../develop/unity/text-in-unity.md)
* [색, 광원 및 재질](./color-light-and-materials.md)