---
title: 설명서 지침
description: MRTK에 대 한 설명서 지침과 표준입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: aa583876d4ca9e115d4ea4507638eebab838207230693cb7c24b781d8f0b020b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210726"
---
# <a name="documentation-guidelines"></a>설명서 지침

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

이 문서에서는 mrtk (Mixed Reality Toolkit)에 대 한 설명서 지침과 표준에 대해 간략하게 설명 합니다. 이를 통해 문서 작성과 생성의 기술적 측면을 소개 하 고 일반적인 문제를 강조 표시 하 고 권장 되는 쓰기 스타일을 설명할 수 있습니다.

페이지 자체는 예제로 제공 되므로 설명서의 원하는 스타일과 가장 일반적인 태그 기능을 사용 합니다.

- [원본](#source-documentation)
- [방법](#how-to-documentation)
- [디자인](#design-documentation)
- [성능 정보](#performance-notes)
- [주요 변경 내용](#breaking-changes)

---

## <a name="functionality-and-markup"></a>기능 및 태그

이 섹션에서는 자주 필요한 기능에 대해 설명 합니다. 작동 방식을 확인 하려면 페이지의 소스 코드를 확인 합니다.

1. 번호 매기기 목록
   1. 3 개 이상의 공백이 포함 된 중첩 된 번호 매기기 목록
   1. 코드의 실제 숫자는 관련이 없습니다. 구문 분석은 올바른 항목 번호를 설정 하는 데 사용 됩니다.

- 글머리 기호 점 목록
  - 중첩 된 글머리 기호 점 목록
-  \* \* 이중 별표가 있는 굵게 텍스트\*\*
-   \_ 밑줄 \_ 또는 \* 단일 별표가 포함 된 기울임꼴 텍스트\*
- `highlighted as code` \` 큰따옴표를 사용 하는 문장 내 텍스트\`
- 문서 페이지에 대 한 링크 [Mrtk 설명서 지침](documentation-guide.md)
- [페이지 내의 앵커](#style)에 대 한 링크입니다. 앵커는 공백을 대시로 바꾸고 소문자로 변환 하 여 형성 됩니다.

코드 샘플의 경우 세 개의 백 틱이 있는 블록을 사용 \` \` \` 하 고 구문 강조를 위한 언어로 *csharp* 을 지정 합니다.

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

문장 내에서 코드를 언급 하는 경우 `use a single backtick`

### <a name="todos"></a>Todo

시간이 지남에 따라, 이러한 TODOs (예: 코드 TODOs)를 누적 하 고 업데이트 하는 방법에 대 한 정보 및 업데이트 하는 방법에 대 한 정보를 문서에서 사용 하지 마세요.

TODO를 반드시 추가 해야 하는 경우 다음 단계를 수행 합니다.

1. TODO의 컨텍스트를 설명 하는 Github에서 새로운 문제를 해결 하 고 다른 참가자가 이해할 수 있는 충분 한 배경 지식을 제공 하 고 TODO를 해결할 수 있습니다.
2. 문서에서 todo의 issue URL을 참조 합니다.

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a>강조 표시 된 섹션

판독기의 특정 요소를 강조 표시 하려면, *> [!NOTE]* 및를 사용 *> [!WARNING]* 하 여 *> [!IMPORTANT]* 다음 스타일을 생성 합니다. 특별 한 관련 사례에 대해서만 일반 요소 및 경고/중요 점에 대해 메모를 사용 하는 것이 좋습니다.

> [!NOTE]
> 메모 예

> [!WARNING]
> 경고의 예

> [!IMPORTANT]
> 중요 한 주석의 예

## <a name="page-layout"></a>페이지 레이아웃

### <a name="introduction"></a>소개

주 챕터 제목 바로 뒤의 부분은 챕터에 대 한 간략 한 소개로 제공 되어야 합니다. 이 작업을 너무 오래 하지 말고 하위 헤드라인을 추가 합니다. 이러한 섹션을 섹션에 연결할 수 있으며 책갈피로 저장할 수 있습니다.

### <a name="main-body"></a>주 본문

2 수준 및 3 단계 헤드라인을 사용 하 여 나머지를 구성 합니다.

**미니 섹션**

해제 해야 하는 블록에 굵은 텍스트 줄을 사용 합니다. 이는 특정 시점에 4 단계 헤드라인으로 바꿀 수 있습니다.

### <a name="see-also-section"></a>' 참고 항목 ' 섹션

대부분의 페이지 *는 라는 챕터* 로 끝나야 합니다. 이 장에서는이 항목과 관련 된 페이지에 대 한 링크를 가리키는 글머리 기호 목록 일 뿐입니다. 이러한 링크는 페이지 텍스트 내에 해당 하는 경우에도 나타날 수 있지만 반드시 필요한 것은 아닙니다. 마찬가지로 페이지 텍스트에는 주 항목과 관련이 없는 페이지에 대 한 링크가 포함 되어 있을 수 있습니다. *참고* 항목 목록에 포함 되지 않아야 합니다. 링크를 선택 하는 방법에 대 한 예제는 [이 페이지의 '](#see-also) ' 참고 ' 단원을 참조 하세요.

## <a name="table-of-contents-toc"></a>목차 (TOC)

Toc 파일은 MRTK github.io 설명서에서 탐색 모음을 생성 하는 데 사용 됩니다.
새 문서 파일이 추가 될 때마다 문서 폴더의 toc. yml 파일 중 하나에 해당 파일에 대 한 항목이 있는지 확인 합니다. Toc 파일에 나열 된 문서만 개발자 문서 탐색에 표시 됩니다. 문서 폴더의 모든 하위 폴더에 대 한 toc 파일이 있을 수 있습니다 .이 파일은 기존 toc 파일에 연결 하 여 탐색의 해당 부분에 하위 섹션으로 추가할 수 있습니다.

## <a name="style"></a>스타일

### <a name="writing-style"></a>쓰기 스타일

일반적인 경험: **전문 전문가** 에 게 해보세요. 이는 일반적으로 ' 대화형 톤 '을 방지 하는 것을 의미 합니다. 또한 hyperbole 및 sensationalism을 방지 합니다.

1. 지나치게 재미 않게 해보세요.
2. ' I '를 쓰지 않음
3. ' Microsoft '를 사용 하지 마세요. 이는 일반적으로 ' MRTK '를 대신 사용 하 여 쉽게 rephrased 수 있습니다. 예: "이 기능을 지원 합니다."-> "MRTK는이 기능을 지원 합니다." 또는 "다음 기능이 지원 됩니다."
4. 마찬가지로 ' 사용자 '를 방지 해 보세요. 예: "이 간단한 변경을 사용 하면 셰이더가 구성 가능 합니다." -> "셰이더는 약간의 노력으로 구성할 수 있습니다."
5. ' 찾아낼 문구 '를 사용 하지 마세요.
6. 지나치게 많이 발생 하는 것을 방지 하기 위해 어떤 것도 판매할 필요가 없습니다.
7. 마찬가지로 지나치게 극적이 되지 않도록 합니다. 느낌표는 거의 필요 하지 않습니다.

### <a name="capitalization"></a>대문자 표시

- **헤드라인의 경우 문장의 첫 글자를** 사용 합니다. Ie. 첫 번째 문자 및 이름을 대문자로 표시 하지만 다른는 그렇지 않습니다.
- 다른 모든 항목에 일반 영어를 사용 합니다. 즉, 해당 컨텍스트에서 특별 한 의미를 보유 하더라도 **임의의 단어를 대문자로 표기 하지 않습니다**. 특정 단어를 강조 표시 하기 위해 *기울임꼴 텍스트* 를 선호 합니다. [아래를 참조](#emphasis-and-highlighting)하십시오.
- 링크를 문장 (선호 하는 방법)에 포함 하는 경우 표준 장 이름에는 항상 대문자를 사용 하 여 텍스트 내에서 임의의 대/소문자 구분 규칙이 손상 되지 않도록 합니다. 따라서 사용자 지정 링크 이름을 사용 하 여 대문자 표시를 수정 합니다. 예를 들어, 다음은 [경계 컨트롤](../features/ux-building-blocks/bounds-control.md) 설명서에 대 한 링크입니다.
- *Unity* 와 같은 이름을 대문자로 표기 합니다.
- *Unity 편집기* 를 작성할 때 "편집기"를 대문자로 표기 하지 마십시오.

### <a name="emphasis-and-highlighting"></a>강조 및 강조 표시

단어를 강조 표시 하거나 강조 표시 하는 두 가지 방법으로 굵게 하거나 기울임꼴로 만들 수 있습니다. 굵은 텍스트의 효과는 굵은 텍스트가 **표시** 되는 것 이므로 텍스트의 일부를 skimming 하거나 페이지를 스크롤 하는 동안 쉽게 확인할 수 있습니다. 굵게는 사용자가 기억할 구를 강조 표시 하는 데 유용 합니다. 그러나 일반적으로는 **자주 사용 되지 않으므로 굵은 텍스트를 사용** 합니다.

일반적으로는 특별 한 의미가 있기 때문에 논리적으로 함께 속하거나 특정 용어를 강조 표시 하는 ' 그룹 ' 중 하나를 원합니다. 이러한 작업은 전체 텍스트를 제거할 필요가 없습니다. 기울임꼴 텍스트를 *간단한 방법* 으로 사용 하 여 항목을 강조 표시 합니다.

마찬가지로, 파일 이름, 경로 또는 메뉴 항목이 텍스트에서 언급 되는 경우에는이를 사용 하 여 논리적으로 그룹화 하는 것이 혼란을 주지 않도록 하는 것이 좋습니다.

일반적으로 **불필요 한 텍스트 강조 표시를 방지** 합니다. 특수 용어는 판독기를 인식 하기 위해 한 번 강조 표시 될 수 있으며, 더 이상 사용 되지 않고 distracts만 제공 되는 경우 텍스트 전체에서 강조 표시를 반복 하지 않습니다.

### <a name="mentioning-menu-entries"></a>메뉴 항목을 언급 합니다.

사용자가 클릭 해야 하는 메뉴 항목을 언급할 때 현재 규칙은 *Project > 파일 > > 리프 만들기* 입니다.

### <a name="links"></a>링크

다른 페이지에 가능한 한 많은 유용한 링크를 삽입하지만 각 링크는 한 번만 삽입합니다. 독자가 페이지의 모든 링크를 클릭한다고 가정하고, 동일한 페이지가 20번 열리는 경우 얼마나 불편할지 생각해 보세요.

문장에 포함된 링크를 선호합니다.

- BAD: 지침이 유용합니다. 자세한 내용은 [이 장을](../contributing/documentation-guide.md) 참조하세요.
- GOOD: [지침이](documentation-guide.md) 유용합니다.

외부 링크를 사용하지 마십시오. 오래된 링크가 되거나 저작권이 있는 콘텐츠가 포함될 수 있습니다.

링크를 추가할 때 참고 항목 섹션에도 링크가 나열되는지 여부를 [고려합니다.](#see-also) 마찬가지로 새 페이지에 대한 링크를 링크된 페이지에 추가해야 하는지 여부를 확인합니다.

### <a name="images--screenshots"></a>이미지/스크린샷

**스크린샷을 드물게 사용합니다.** 설명서에서 이미지를 유지 관리하는 것은 많은 작업이며, 작은 UI를 변경하면 많은 스크린샷이 오래 될 수 있습니다. 다음 규칙은 유지 관리 노력을 줄입니다.

1. 텍스트로 설명할 수 있는 스크린샷은 사용하지 마십시오. 특히 속성 이름 및 값을 표시하기 위한 목적으로만 **속성 표를 스크린샷으로 표시하면 안됩니다.**
2. 스크린샷에 표시된 내용과 관련이 없는 내용을 포함하지 마십시오. 예를 들어 렌더링 효과가 표시되면 뷰포트의 스크린샷을 만들되 주위의 UI는 제외합니다. 일부 UI를 표시하고 해당 중요한 부분만 이미지에 있도록 창을 이동해 보세요.
3. 스크린샷 UI를 포함하는 경우 중요한 부분만 표시합니다. 예를 들어 도구 모음의 단추에 대해 말하는 경우 중요한 도구 모음 단추를 표시하는 작은 이미지를 만들지만 그 주위의 모든 것을 제외합니다.
4. 재현하기 쉬운 이미지만 사용합니다. 즉, 표식 또는 강조 표시를 스크린샷에 그리지 마십시오. 첫째, 이러한 규칙의 모양은 일관되지 않습니다. 둘째, 이러한 스크린샷을 재현하는 것은 추가적인 노력입니다. 대신 텍스트의 중요한 부분을 설명합니다. 이 규칙에는 예외가 있지만 드문 경우입니다.
5. 물론 애니메이션 GIF를 다시 만들기 위해 훨씬 더 많은 노력을 기울입니다. 시간이 끝날 때까지 다시 만들어야 하거나, 시간을 소비하지 않으려는 경우 사람들이 이 파일을 throw할 것으로 예상합니다.
6. 문서의 이미지 수를 낮게 유지합니다. 종종 모든 것을 보여 주는 일부 도구의 전체 스크린샷을 만들고 나머지를 텍스트로 설명하는 것이 좋습니다. 이렇게 하면 필요할 때 스크린샷을 쉽게 바꿀 수 있습니다.

몇 가지 다른 측면은 다음과 같습니다.

- 스크린샷에 대한 편집기 UI는 모든 사용자가 어두운 테마에 액세스할 수 있는 것은 아니고 가능한 일관성을 유지하려고 하기 때문에 밝은 회색 테마 편집기를 사용해야 합니다.
- 기본 이미지 너비는 500픽셀이며 대부분의 모니터에 잘 표시됩니다. 너무 많이 벗어나지 않도록 합니다. 너비가 800픽셀이어야 합니다.
- UI의 스크린샷에 PNG를 사용합니다.
- 3D 뷰포트 스크린샷에는 PNG 또는 JPG를 사용합니다. 압축 비율보다 품질을 선호합니다.

### <a name="list-of-component-properties"></a>구성 요소 속성 목록

속성 목록을 문서화할 때는 굵은 텍스트를 사용하여 속성 이름을 강조 표시한 다음 줄 나누기와 일반 텍스트를 사용하여 설명합니다. 하위 장 또는 글머리 기호 목록을 사용하지 마십시오.

또한 마침표로 모든 문장을 완료해야 합니다.

## <a name="page-completion-checklist"></a>페이지 완성 검사 목록

1. 이 문서의 지침이 준수되었는지 확인합니다.
1. 문서 구조를 찾아보고 다른 페이지의 참고 섹션 아래에서 새 문서를 언급할 수 있는지 [확인합니다.](#see-also)
1. 사용 가능한 경우 기술 정확성에 대한 페이지를 증명하여 읽어주는 토픽에 대한 지식이 있는 사람이 있어야 합니다.
1. 누군가가 스타일 및 서식 지정을 위해 페이지를 증명하여 읽게 합니다. 이 항목에 익숙하지 않은 사람이 있을 수 있으며, 설명서의 이해 정도에 대한 피드백을 받는 것도 좋습니다.

## <a name="source-documentation"></a>원본 설명서

API 설명서는 MRTK 원본 파일에서 자동으로 생성됩니다. 이를 용이하게 하려면 원본 파일에 다음이 포함되어야 합니다.

- [클래스, 구조체, 열거형 요약 블록](#class-struct-enum-summary-blocks)
- [속성, 메서드, 이벤트 요약 블록](#property-method-event-summary-blocks)
- [기능 소개 버전 및 의존성](#feature-introduction-version-and-dependencies)
- [직렬화된 필드](#serialized-fields)
- [열거형 값](#enumeration-values)

위의 코드 외에도 유지 관리, 버그 수정 및 사용자 지정 용이성을 허용하도록 코드를 잘 주석으로 작성해야 합니다.

### <a name="class-struct-enum-summary-blocks"></a>클래스, 구조체, 열거형 요약 블록

클래스, 구조체 또는 열거형이 MRTK에 추가되는 경우 해당 용도를 설명해야 합니다. 이는 클래스 위에 요약 블록의 형식을 취합니다.

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

클래스 수준 dependencies가 있는 경우 요약 바로 아래의 설명 블록에 문서화되어야 합니다.

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

클래스, 구조체 또는 열거형에 대한 요약 없이 제출된 끌어오기 요청은 승인되지 않습니다.

### <a name="property-method-event-summary-blocks"></a>속성, 메서드, 이벤트 요약 블록

속성, 메서드 및 이벤트(PMEs) 및 필드는 코드 표시 유형(퍼블릭, 프라이빗, 보호 및 내부)에 관계없이 요약 블록으로 문서화되어야 합니다. 설명서 생성 도구는 퍼블릭 및 보호된 기능만 필터링하고 게시합니다.

참고: Unity 메서드에는  요약 블록이 필요하지 않습니다(예: 각성, 시작, 업데이트).

끌어오기 요청을 승인하려면 PME 설명서가 **필요합니다.**

PME 요약 블록의 일부로 매개 변수 및 반환된 데이터의 의미와 목적이 필요합니다.

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a>기능 소개 버전 및 의존성

API 요약 설명서의 일부로 기능이 도입된 MRTK 버전 및 모든 의존성 관련 정보를 설명 블록에 문서화해야 합니다.

종속성 확장 및/또는 플랫폼 종속성 포함 되어야 합니다.

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a>직렬화된 필드

Unity의 도구 설명 특성을 사용하여 검사기에서 스크립트의 필드에 대한 런타임 설명서를 제공하는 것이 좋습니다.

구성 옵션이 API 설명서에 포함되도록 스크립트는 적어도 도구 설명 콘텐츠를 요약 블록에 *포함해야* 합니다.

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a>열거형 값

및 열거형을 정의할 때 코드는 요약 블록을 사용하여 열거형 값의 의미도 문서화해야 합니다. 설명 블록은 필요에 따라 이해를 향상시키기 위해 추가 세부 정보를 제공하는 데 사용할 수 있습니다.

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a>방법 설명서

Mixed Reality Toolkit 많은 사용자가 API 설명서를 사용하지 않아도 될 수 있습니다. 이러한 사용자는 미리 만들어진 재사용 가능한 프리팹 및 스크립트를 활용하여 환경을 만듭니다.

각 기능 영역에는 제공된 내용에 대해 상당히 높은 수준에서 설명하는 하나 이상의 markdown(.md) 파일이 포함됩니다. 지정된 기능 영역의 크기 및/또는 복잡성에 따라 제공된 기능당 최대 하나씩 추가 파일이 필요할 수 있습니다.

기능이 추가되거나 사용량이 변경되면 개요 설명서를 제공해야 합니다.

이 설명서의 일부로 일러스트레이션을 비롯한 방법 섹션을 제공하여 시작의 기능 또는 개념을 접하는 고객을 지원해야 합니다.

## <a name="design-documentation"></a>디자인 설명서

Mixed Reality 완전히 새로운 세계를 만들 수 있는 기회를 제공합니다. 이 작업의 일부로 MRTK와 함께 사용할 사용자 지정 자산을 만들 수 있습니다. 고객이 최대한 마찰을 없도록 하려면 구성 요소에서 아트 자산에 대한 서식 또는 기타 요구 사항을 설명하는 디자인 설명서를 제공해야 합니다.

디자인 설명서가 유용할 수 있는 몇 가지 예는 다음과 같습니다.

- 커서 모델
- 공간 매핑 시각화
- 음향 효과 파일

이 유형의 설명서는 **권장되며** 끌어오기 요청 검토의 일부로 요청될 **수 있습니다.**

[이는 MS 개발자 사이트의](/windows/mixed-reality/design) 디자인 권장 사항과 다를 수도 있습니다.

## <a name="performance-notes"></a>성능 정보

몇 가지 중요한 기능은 성능 비용이 듭니다. 이 코드는 구성 방법에 따라 매우 달라지는 경우가 많습니다.

예를 들어:

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

성능 참고는 CPU 및/또는 GPU가 많은 구성 요소에 권장되며 끌어오기 요청 검토의 일부로 요청될 **수 있습니다.** 모든 해당 성능 정보는 API **및** 개요 설명서에 포함 되어 있습니다.

## <a name="breaking-changes"></a>주요 변경 내용

주요 변경 내용 설명서는 각 기능 영역의 개별 breaking-changes.md 연결 되는 최상위 수준 [파일로](../contributing/breaking-changes.md) 구성 되어 있습니다.

기능 영역 breaking-changes.md 파일은 지정 된 릴리스에 대해 알려진 모든 주요 변경 내용 목록과 **이전 릴리스의 주요** 변경 내용에 대 한 기록을 포함 합니다.

예를 들어:

```md
Spatial sound breaking changes

2018.07.2
* Spatialization of the imaginary effect is now required.
* Management of randomized AudioClip files requires an entropy value in the manager node.

2018.07.1
No known breaking changes

2018.07.0
...
```

기능 수준 breaking-changes.md 파일에 포함 된 정보는 각각의 새 MRTK 릴리스에 대 한 릴리스 정보로 집계 됩니다.

변경의 일부인 주요 변경 내용은 끌어오기 요청의 일부로 문서화 되어야 **합니다** .

## <a name="tools-for-editing-markdown"></a>MarkDown 편집 도구

[Visual Studio Code](https://code.visualstudio.com/) 은 mrtk 설명서의 일부인 markdown 파일을 편집 하는 데 유용한 도구입니다.

설명서를 작성할 때는 다음 두 가지 확장을 설치 하는 것도 좋습니다.

- Visual Studio Code 용 docs Markdown 확장-Alt + M을 사용 하 여 docs 제작 옵션 메뉴를 표시 합니다.

- 코드 맞춤법 검사기-철자가 잘못 된 단어에는 밑줄이 그어집니다. 철자가 잘못 된 단어를 마우스 오른쪽 단추로 클릭 하 여 변경 하거나 사전에 저장 합니다.

이러한 두 가지 모두 Microsoft 게시 된 문서 작성 팩에 패키지 됩니다.

## <a name="see-also"></a>추가 정보

- [설명서에 대 한 "참고 항목" 링크 예](https://www.microsoft.com)
