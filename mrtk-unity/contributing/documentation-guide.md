---
title: 설명서 가이드
description: MRTK에 대한 설명서 지침 및 표준입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: cc5572e65540fa40cb1b8db56afbdd0986c467b9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144797"
---
# <a name="documentation-guidelines"></a>설명서 지침

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

이 문서에서는 MRTK(Mixed Reality Toolkit)에 대한 설명서 지침 및 표준을 간략하게 설명합니다. 설명서 작성 및 생성의 기술적 측면을 소개하고, 일반적인 문제를 강조 표시하고, 권장되는 쓰기 스타일을 설명합니다.

페이지 자체는 예제로 사용되므로 의도한 스타일과 설명서의 가장 일반적인 태그 기능을 사용합니다.

- [원본](#source-documentation)
- [방법](#how-to-documentation)
- [디자인](#design-documentation)
- [성능 정보](#performance-notes)
- [주요 변경 내용](#breaking-changes)

---

## <a name="functionality-and-markup"></a>기능 및 태그

이 섹션에서는 자주 필요한 기능에 대해 설명합니다. 작동 방식을 확인하려면 페이지의 소스 코드를 확인합니다.

1. 번호가 매겨진 목록
   1. 3개 이상의 선행 공백이 있는 중첩 번호가 매겨진 목록
   1. 코드의 실제 숫자는 관련이 없습니다. 구문 분석 시 올바른 항목 번호 설정이 처리됩니다.

- 글머리 기호 목록
  - 중첩된 글머리 기호 목록
- 이중  \* 별표가 있는 굵은 텍스트 \*\*\*
- 밑수 또는 단일  별표가  \_ \_ \* 있는 italic text\*
- `highlighted as code`백쿼트를 사용하여 문장 내의 텍스트 \`\`
- 문서 페이지 [MRTK 설명서 지침에](documentation-guide.md) 대한 링크
- 페이지 [내의 앵커에 대한](#style)링크 앵커는 공백을 대시로 대체하고 소문자로 변환하여 구성됩니다.

코드 샘플의 경우 세 개의 백틱이 있는 블록을 사용하고 \` \` \` 구문 강조 표시를 위한 언어로 *csharp를* 지정합니다.

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

문장 내의 코드를 언급하는 경우 `use a single backtick`

### <a name="todos"></a>Todos

시간이 지남에 따라 이러한 TODO(예: 코드 TODO)가 누적되고 업데이트 방법 및 손실 이유에 대한 정보가 누적되는 경향이 있기 때문에 문서에서 TODO를 사용하지 마십시오.

TODO를 추가해야 하는 경우 다음 단계를 수행합니다.

1. TODO의 컨텍스트를 설명하는 새 문제를 Github에 제출하고 다른 참가자가 TODO를 이해하고 해결할 수 있는 충분한 배경을 제공합니다.
2. 문서의 할 일에서 문제 URL을 참조합니다.

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a>강조 표시된 섹션

판독기에서 특정 점을 강조 표시하려면 , 및 를 사용하여 *> [!NOTE]* *> [!WARNING]* 다음 스타일을 *> [!IMPORTANT]* 생성합니다. 일반적인 사항에 대한 참고 사항 및 특수 관련 사례에 대해서만 경고/중요 지점을 사용하는 것이 좋습니다.

> [!NOTE]
> 참고 예제

> [!WARNING]
> 경고의 예

> [!IMPORTANT]
> 중요한 주석의 예

## <a name="page-layout"></a>페이지 레이아웃

### <a name="introduction"></a>소개

주 챕터 제목 바로 뒤의 부분은 챕터의 내용을 간단히 소개하는 역할을 해야 합니다. 이 작업을 너무 오래 수행하지 말고, 하위 자막을 추가합니다. 이렇게 하면 섹션에 연결할 수 있으며 책갈피로 저장할 수 있습니다.

### <a name="main-body"></a>본문

나머지를 구조화하려면 2단계 및 3단계 재구성을 사용합니다.

**미니 섹션**

눈에 띄어야 하는 블록에 대해 굵은 텍스트 줄을 사용합니다. 어느 시점에서는 이를 4개 수준의 뉴스로 바꿀 수 있습니다.

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
4. 마찬가지로 ' 사용자 '를 방지 해 보세요. 예: "이 간단한 변경을 사용 하면 셰이더가 구성 가능 합니다." -> "셰이더를 적은 노력으로 구성할 수 있습니다."
5. 'sloppy phrases'를 사용하지 마십시오.
6. 지나치게 기대한 소리를 방지합니다. 아무것도 판매할 필요가 없습니다.
7. 마찬가지로 지나치게 크게 하지 마십시오. 느낌표는 거의 필요하지 않습니다.

### <a name="capitalization"></a>대문자 표시

- **제목에 문장 대/소문자를** 사용합니다. Ie. 첫 글자와 이름을 대문자로 지정합니다.
- 다른 모든 경우 일반 영어를 사용합니다. 즉, 해당 컨텍스트에서 특별한 의미를 가진 경우에도 **임의의 단어를 대문자로** 대문자로 지정하지 않습니다. 특정 단어를 강조 표시하기 위해 *italic text를* [선호합니다. 아래를 참조하세요.](#emphasis-and-highlighting)
- 링크가 문장에 포함되는 경우(기본 설정 방법) 표준 챕터 이름은 항상 대문자를 사용하므로 텍스트 내에서 임의의 대문자 표시가 없는 규칙을 위반합니다. 따라서 사용자 지정 링크 이름을 사용하여 대문자를 수정합니다. 예를 들어 경계 [컨트롤](../features/ux-building-blocks/bounds-control.md) 설명서에 대한 링크는 다음과 같습니다.
- Unity 와 같은 이름을 대문자로 *지정합니다.*
- Unity 편집기 를 작성할 때는 "editor"를 *대문자로* 하지 마십시오.

### <a name="emphasis-and-highlighting"></a>강조 및 강조 표시

단어를 강조 표시하거나 강조 표시하여 굵게 만들거나 굵게 만드는 두 가지 방법이 있습니다. 굵은 텍스트의 효과는 **굵은 텍스트가 돋보여지므로** 텍스트 조각을 건너뛰거나 페이지 위로 스크롤하는 동안 쉽게 알 수 있습니다. 굵게는 사람들이 기억해야 하는 문구를 강조 표시하기에 좋습니다. 그러나 일반적으로 방해가 되므로 **굵은 텍스트를 거의 사용하지** 않습니다.

일반적으로는 특별 한 의미가 있기 때문에 논리적으로 함께 속하거나 특정 용어를 강조 표시 하는 ' 그룹 ' 중 하나를 원합니다. 이러한 작업은 전체 텍스트를 제거할 필요가 없습니다. 기울임꼴 텍스트를 *간단한 방법* 으로 사용 하 여 항목을 강조 표시 합니다.

마찬가지로, 파일 이름, 경로 또는 메뉴 항목이 텍스트에서 언급 되는 경우에는이를 사용 하 여 논리적으로 그룹화 하는 것이 혼란을 주지 않도록 하는 것이 좋습니다.

일반적으로 **불필요 한 텍스트 강조 표시를 방지** 합니다. 특수 용어는 판독기를 인식 하기 위해 한 번 강조 표시 될 수 있으며, 더 이상 사용 되지 않고 distracts만 제공 되는 경우 텍스트 전체에서 강조 표시를 반복 하지 않습니다.

### <a name="mentioning-menu-entries"></a>메뉴 항목을 언급 합니다.

사용자가 클릭 해야 하는 메뉴 항목을 언급할 때 현재 규칙은 *프로젝트 > 파일 > > 리프 만들기* 입니다.

### <a name="links"></a>링크

가능한 한 많은 유용한 링크를 다른 페이지에 삽입 하 고 각 링크는 한 번만 삽입 합니다. 페이지가 페이지의 모든 링크를 클릭 하는 것으로 가정 하 고, 동일한 페이지가 20 번 열리는 경우 얼마나 방해가 될 수 있는지 생각해 보십시오.

문장에 포함 된 링크를 선호 합니다.

- 잘못 됨: 지침이 유용 합니다. 자세한 내용은 [이 챕터](../contributing/documentation-guide.md) 를 참조 하십시오.
- 양호: [지침이](documentation-guide.md) 유용 합니다.

외부 링크를 사용 하지 않으면 오래 된 링크를 사용 하지 않거나 저작권 콘텐츠를 포함할 수 있습니다.

링크를 추가 하는 경우 링크를 [참고](#see-also) 항목 섹션에도 표시 해야 하는지 여부를 고려 합니다. 마찬가지로, 새 페이지에 대 한 링크를 연결 된 페이지에 추가할지 여부를 확인 합니다.

### <a name="images--screenshots"></a>이미지/스크린샷

**스크린샷만 사용 합니다.** 설명서에서 이미지를 유지 관리 하는 작업은 많은 작업 이며 작은 UI를 변경 하면 더 많은 스크린샷을 사용할 수 있습니다. 다음 규칙은 유지 관리 노력을 줄입니다.

1. 텍스트로 설명할 수 있는 스크린샷은 사용하지 마십시오. 특히 속성 이름 및 값을 표시하기 위한 목적으로만 **속성 표를 스크린샷으로 표시하면 안됩니다.**
2. 스크린샷에 표시된 내용과 관련이 없는 내용을 포함하지 마십시오. 예를 들어 렌더링 효과가 표시되면 뷰포트의 스크린샷을 만들되 주위의 UI는 제외합니다. 일부 UI를 표시하고 해당 중요한 부분만 이미지에 있도록 창을 이동해 보세요.
3. 스크린샷 UI를 포함하는 경우 중요한 부분만 표시합니다. 예를 들어 도구 모음의 단추에 대해 말하는 경우 중요한 도구 모음 단추를 표시하는 작은 이미지를 만들지만 그 주위의 모든 것을 제외합니다.
4. 재현하기 쉬운 이미지만 사용합니다. 즉, 표식 또는 강조 표시를 스크린샷에 그리지 마십시오. 첫째, 이러한 규칙의 모양은 일관되지 않습니다. 둘째, 이러한 스크린샷을 재현하는 것은 추가적인 노력입니다. 대신 텍스트의 중요한 부분을 설명합니다. 이 규칙에는 예외가 있지만 드문 경우입니다.
5. 물론 애니메이션 GIF를 다시 만들기 위해 훨씬 더 많은 노력을 기울입니다. 시간이 끝날 때까지 다시 만들어야 하거나, 시간을 소비하지 않으려는 경우 사람들이 이 파일을 throw할 것으로 예상합니다.
6. 문서의 이미지 수를 낮게 유지합니다. 종종 모든 것을 보여 주는 일부 도구의 전체 스크린샷을 만들고 나머지를 텍스트로 설명하는 것이 좋습니다. 이렇게 하면 필요할 때 스크린샷을 쉽게 바꿀 수 있습니다.

몇 가지 다른 측면은 다음과 같습니다.

- 스크린샷 용 편집기 UI는 밝은 회색 테마 편집기를 사용 해야 합니다. 모든 사용자가 어두운 테마에 액세스할 수 있는 것은 아니므로 최대한 일관성 있게 유지 하는 것입니다.
- 기본 이미지 너비는 대부분의 모니터에 잘 표시 되므로 500 픽셀입니다. 너무 많이 해 서는 안 됩니다. 800 픽셀은 최대 너비 여야 합니다.
- UI의 스크린샷에 PNGs를 사용 합니다.
- 3D 뷰포트 스크린샷에 PNGs 또는 JPGs를 사용 합니다. 압축 비율 보다 품질을 선호 합니다.

### <a name="list-of-component-properties"></a>구성 요소 속성 목록

속성 목록을 문서화할 때 굵은 텍스트를 사용 하 여 속성 이름을 강조 표시 한 다음 줄 바꿈 및 일반 텍스트를 사용 하 여 설명 합니다. 하위 장이나 글머리 기호 요소 목록을 사용 하지 마십시오.

또한 모든 문장을 마침표를 사용 하 여 완료 해야 합니다.

## <a name="page-completion-checklist"></a>페이지 완료 검사 목록

1. 이 문서의 지침을 준수 하는지 확인 합니다.
1. 문서 구조를 찾아보고 다른 페이지의 [참고](#see-also) 항목 섹션에서 새 문서를 찾을 수 있는지 확인 합니다.
1. 사용할 수 있는 경우 항목 증명에 대 한 지식이 있는 사용자에 게 기술 정확성을 위해 페이지를 읽도록 합니다.
1. 스타일 및 서식 지정을 위해 페이지를 증명 하는 사람이 필요 합니다. 이는 토픽에 익숙하지 않을 수 있습니다. 또한 설명서의 이해를 이해 하는 방법에 대 한 피드백을 얻는 것이 좋습니다.

## <a name="source-documentation"></a>원본 설명서

API 설명서는 MRTK 원본 파일에서 자동으로 생성 됩니다. 이를 용이 하 게 하려면 소스 파일이 다음을 포함 해야 합니다.

- [클래스, 구조체, 열거형 요약 블록](#class-struct-enum-summary-blocks)
- [속성, 메서드, 이벤트 요약 블록](#property-method-event-summary-blocks)
- [기능 소개 버전 및 의존성](#feature-introduction-version-and-dependencies)
- [직렬화된 필드](#serialized-fields)
- [열거형 값](#enumeration-values)

위의 코드 외에도 유지 관리, 버그 수정 및 사용자 지정 용이성을 허용하도록 코드를 잘 주석으로 작성해야 합니다.

### <a name="class-struct-enum-summary-blocks"></a>클래스, 구조체, 열거형 요약 블록

클래스, 구조체 또는 열거형이 MRTK에 추가되는 경우 해당 용도를 설명해야 합니다. 이는 클래스 위의 요약 블록 형식을 취합니다.

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

### <a name="serialized-fields"></a>Serialize 된 필드

Unity의 tooltip 특성을 사용 하 여 검사기에서 스크립트의 필드에 대 한 런타임 설명서를 제공 하는 것이 좋습니다.

구성 옵션이 API 설명서에 포함 되도록 하기 위해 스크립트는 *최소한* 요약 블록에 도구 설명 내용을 포함 해야 합니다.

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a>열거형 값

및 열거형을 정의 하는 경우 코드 에서도 요약 블록을 사용 하 여 열거형 값의 의미를 문서화 해야 합니다. 설명 블록을 사용 하 여 추가 정보를 제공 하 여 이해를 향상할 수 있습니다.

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

혼합 현실 도구 키트의 많은 사용자는 API 설명서를 사용할 필요가 없습니다. 이러한 사용자는 미리 만들어진 재사용 가능한 prefabs 및 스크립트를 활용 하 여 환경을 만듭니다.

각 기능 영역에는 매우 높은 수준에서 설명 하는 하나 이상의 markdown (md) 파일이 포함 됩니다. 제공 됩니다. 지정 된 기능 영역의 크기 및/또는 복잡도에 따라 제공 된 기능별로 하나의 추가 파일이 필요할 수 있습니다.

기능이 추가 되거나 사용이 변경 되 면 개요 설명서를 제공 해야 합니다.

이 설명서의 일부로, 자습서를 비롯 한 방법 섹션을 참조 하 여 시작 하는 기능 또는 개념에 대 한 새로운 고객을 지원할 수 있습니다.

## <a name="design-documentation"></a>디자인 설명서

혼합 현실은 완전히 새로운 세계를 만들 수 있는 기회를 제공 합니다. 이 부분에는 MRTK에서 사용할 사용자 지정 자산을 만드는 작업이 포함 될 수 있습니다. 이를 가능한 한 고객에 게 무료로 제공 하기 위해 구성 요소는 아트 자산의 서식 또는 기타 요구 사항을 설명 하는 디자인 설명서를 제공 해야 합니다.

디자인 설명서가 유용할 수 있는 몇 가지 예는 다음과 같습니다.

- 커서 모델
- 공간 매핑 시각화
- 음향 효과 파일

이러한 유형의 설명서 **는 권장 되며** , 끌어오기 요청 검토의 일환으로 요청 될 수 **있습니다** .

이는 [MS Developer 사이트](/windows/mixed-reality/design) 의 디자인 권장 사항과 다를 수 있습니다.

## <a name="performance-notes"></a>성능 정보

일부 중요 한 기능은 성능 비용으로 제공 됩니다. 일반적으로이 코드는 구성 방법에 따라 크게 달라 집니다.

예를 들면 다음과 같습니다.

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

성능 정보는 CPU 및/또는 GPU 사용량이 많은 구성 요소에 권장 되며, 끌어오기 요청 검토의 일부로 요청 될 **수 있습니다** . 모든 해당 성능 정보는 API **및** 개요 설명서에 포함 되어 있습니다.

## <a name="breaking-changes"></a>주요 변경 내용

주요 변경 내용 설명서는 각 기능 영역의 개별 breaking-changes.md 연결 되는 최상위 수준 [파일로](../contributing/breaking-changes.md) 구성 되어 있습니다.

기능 영역 breaking-changes.md 파일은 지정 된 릴리스에 대해 알려진 모든 주요 변경 내용 목록과 **이전 릴리스의 주요** 변경 내용에 대 한 기록을 포함 합니다.

예를 들면 다음과 같습니다.

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

[Visual Studio Code](https://code.visualstudio.com/) 은 MRTK 설명서의 일부인 markdown 파일을 편집 하는 데 유용한 도구입니다.

설명서를 작성할 때는 다음 두 가지 확장을 설치 하는 것도 좋습니다.

- Visual Studio Code 용 docs Markdown 확장-Alt + M을 사용 하 여 docs 제작 옵션 메뉴를 표시 합니다.

- 코드 맞춤법 검사기-철자가 잘못 된 단어에는 밑줄이 그어집니다. 철자가 잘못 된 단어를 마우스 오른쪽 단추로 클릭 하 여 변경 하거나 사전에 저장 합니다.

이러한 두 가지 모두 Microsoft 게시 된 문서 작성 팩에 패키지 됩니다.

## <a name="see-also"></a>참고 항목 

* [예제 링크](https://www.google.com)