---
title: 문서 가이드
description: MRTK에 대 한 설명서 지침과 표준입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 37233141bd43f27db47935574bac7630b8bea8d7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121391"
---
# <a name="documentation-guidelines"></a>설명서 지침

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

이 문서에서는 MRTK (혼합 현실 도구 키트)에 대 한 설명서 지침과 표준에 대해 간략하게 설명 합니다. 이를 통해 문서 작성과 생성의 기술적 측면을 소개 하 고 일반적인 문제를 강조 표시 하 고 권장 되는 쓰기 스타일을 설명할 수 있습니다.

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

사용자가 클릭 해야 하는 메뉴 항목을 언급할 때 현재 규칙은 *프로젝트 > 파일 > > 리프 만들기* 입니다.

### <a name="links"></a>링크

가능한 한 많은 유용한 링크를 다른 페이지에 삽입 하 고 각 링크는 한 번만 삽입 합니다. 페이지가 페이지의 모든 링크를 클릭 하는 것으로 가정 하 고, 동일한 페이지가 20 번 열리는 경우 얼마나 방해가 될 수 있는지 생각해 보십시오.

문장에 포함 된 링크를 선호 합니다.

- 잘못 됨: 지침이 유용 합니다. 자세한 내용은 [이 챕터](../contributing/documentation-guide.md) 를 참조 하십시오.
- 양호: [지침이](documentation-guide.md) 유용 합니다.

외부 링크를 사용 하지 않으면 오래 된 링크를 사용 하지 않거나 저작권 콘텐츠를 포함할 수 있습니다.

링크를 추가 하는 경우 링크를 [참고](#see-also) 항목 섹션에도 표시 해야 하는지 여부를 고려 합니다. 마찬가지로, 새 페이지에 대 한 링크를 연결 된 페이지에 추가할지 여부를 확인 합니다.

### <a name="images--screenshots"></a>이미지/스크린샷

**스크린샷만 사용 합니다.** 설명서에서 이미지를 유지 관리 하는 작업은 많은 작업 이며 작은 UI를 변경 하면 더 많은 스크린샷을 사용할 수 있습니다. 다음 규칙을 통해 유지 관리 작업을 줄일 수 있습니다.

1. 텍스트에서 설명할 수 있는 항목에 대 한 스크린샷을 사용 하지 마세요. 특히 속성 이름 및 값을 표시 하는 목적 으로만 **속성 그리드를 스크린샷 하지 마십시오** .
2. 표시 되는 것과 관련이 없는 스크린 샷에는 항목을 포함 하지 마십시오. 예를 들어 렌더링 효과가 표시 되는 경우 뷰포트의 스크린 샷을 만들지만 그 주변의 UI는 제외 합니다. 일부 UI를 표시 하는 경우에는 중요 한 부분만 이미지에 있도록 창을 이동 합니다.
3. 스크린샷 UI를 포함 하는 경우 중요 한 부분만 표시 합니다. 예를 들어 도구 모음에서 단추에 대 한 정보를 표시 하는 경우 중요 한 도구 모음 단추를 표시 하는 작은 이미지를 만들지만 그 주변의 모든 항목은 제외 합니다.
4. 재현 하기 쉬운 이미지만 사용 합니다. 즉, 스크린 샷에 표식을 그리거나 강조 표시 하지 않습니다. 첫째,이를 어떻게 표시 해야 하는지는 일관 된 규칙이 없습니다. 둘째, 이러한 스크린샷을 재현 하는 것이 추가 작업입니다. 대신 텍스트에서 중요 한 부분을 설명 합니다. 이 규칙에 대 한 예외는 있지만 드물게 발생 합니다.
5. 애니메이션 GIF를 다시 만드는 것이 훨씬 더 많은 노력을 기울여야 합니다. 시간이 종료 될 때까지 다시 만들거나, 해당 시간을 소비 하지 않으려는 경우 사용자에 게이를 throw 해야 할 것으로 간주 합니다.
6. 아티클의 이미지 수를 낮게 유지 합니다. 일부 도구에는 모든 항목을 표시 하 고 나머지는 텍스트에 설명 하는 전체 스크린샷 하나를 만드는 것이 좋은 방법입니다. 이렇게 하면 필요한 경우 스크린샷을 쉽게 바꿀 수 있습니다.

다른 측면은 다음과 같습니다.

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
- [기능 소개 버전 및 종속성](#feature-introduction-version-and-dependencies)
- [Serialize 된 필드](#serialized-fields)
- [열거형 값](#enumeration-values)

이러한 코드는 유지 관리, 버그 수정 및 사용자 지정의 용이성을 허용 하기 위해 위에 설명 되어 있어야 합니다.

### <a name="class-struct-enum-summary-blocks"></a>클래스, 구조체, 열거형 요약 블록

클래스, 구조체 또는 열거형이 MRTK에 추가 되는 경우 해당 용도를 설명 해야 합니다. 이는 클래스 위에 있는 요약 블록의 형태를 사용 하는 것입니다.

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

클래스 수준 종속성이 있는 경우 요약 바로 아래에 설명 블록으로 문서화 되어야 합니다.

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

클래스, 구조체 또는 열거형에 대 한 요약 없이 제출 된 끌어오기 요청은 승인 되지 않습니다.

### <a name="property-method-event-summary-blocks"></a>속성, 메서드, 이벤트 요약 블록

속성, 메서드 및 이벤트 (PMEs) 및 필드는 코드 표시 여부 (public, private, protected 및 internal)에 관계 없이 요약 블록으로 문서화 됩니다. 설명서 생성 도구는 공용 및 보호 된 기능만 필터링 하 고 게시 하는 일을 담당 합니다.

참고: Unity 메서드에는 요약 블록이 필요 **하지 않습니다** (예: 해제, 시작, 업데이트).

끌어오기 요청을 승인 하려면 PME 설명서가 **필요** 합니다.

PME summary 블록의 일부로 매개 변수 및 반환 된 데이터의 의미와 목적이 필요 합니다.

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a>기능 소개 버전 및 종속성

API 요약 설명서의 일부로 기능이 도입 된 MRTK 버전 및 모든 종속성에 대 한 정보는 설명 블록에 설명 되어 있습니다.

종속성에는 확장 및/또는 플랫폼 종속성이 포함 되어야 합니다.

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

예를 들어:

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

성능 정보는 CPU 및/또는 GPU 사용량이 많은 구성 요소에 권장 되며, 끌어오기 요청 검토의 일부로 요청 될 **수 있습니다** . 모든 해당 성능 정보는 API **및** 개요 설명서에 포함 되어 있습니다.

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

[Visual Studio Code](https://code.visualstudio.com/) 은 MRTK 설명서의 일부인 markdown 파일을 편집 하는 데 유용한 도구입니다.

설명서를 작성할 때는 다음 두 가지 확장을 설치 하는 것도 좋습니다.

- Visual Studio Code 용 docs Markdown 확장-Alt + M을 사용 하 여 docs 제작 옵션 메뉴를 표시 합니다.

- 코드 맞춤법 검사기-철자가 잘못 된 단어에는 밑줄이 그어집니다. 철자가 잘못 된 단어를 마우스 오른쪽 단추로 클릭 하 여 변경 하거나 사전에 저장 합니다.

이러한 두 가지 모두 Microsoft 게시 된 문서 작성 팩에 패키지 됩니다.

## <a name="see-also"></a>참조 

* [예제 링크](https://www.google.com)