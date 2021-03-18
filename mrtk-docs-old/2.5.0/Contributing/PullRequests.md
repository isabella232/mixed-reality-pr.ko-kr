---
title: PullRequests
description: 끌어오기 요청과 관련된 세부 정보입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, PR,
ms.openlocfilehash: acdabed1b6fe35c3f16db9cf3221481c1715321c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101775059"
---
# <a name="pull-requests"></a>끌어오기 요청

## <a name="prerequisites"></a>필수 구성 요소

이전에 Microsoft 프로젝트에 기여하지 않은 경우 [기여 라이선스 계약](https://cla.microsoft.com/)에 서명하라는 메시지가 표시될 수 있습니다.
PR의 설명을 통해 귀하의 서명 가능 여부를 알 수 있습니다.

> [!IMPORTANT]
> Microsoft 직원이지만 [GitHub에서 Microsoft 조직](https://github.com/Microsoft)의 구성원이 아닌 경우, 끌어오기 요청을 시작하기 전에 [Microsoft의 오픈 소스](https://opensource.microsoft.com/)를 방문하여 corpnet에서 Microsoft 및 GitHub 계정을 연결하세요. 미리 수행해야 할 몇 가지 프로세스 항목이 있습니다.

## <a name="creating-a-pull-request"></a>끌어오기 요청 만들기

끌어오기 요청을 제출할 준비가 되면 [mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development) 분기를 대상으로 하는 [끌어오기 요청을 만듭니다](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/mrtk_development...mrtk_development?expand=1).

지침을 읽고 끌어오기 요청이 지침을 충족하는지 확인합니다.

* PR과 관련된 모든 문제/기능 요청 또는 작업을 참조해야 합니다.
* 끌어오기 요청에 PR과 관련된 파일/변경 내용만 포함되는지 확인합니다.
* 설명서가 최신 상태이고 포함되어 있는지 확인합니다. 모든 공용 필드에 댓글이 있는지 확인합니다.
* 새 기능을 추가하는 경우 기능의 유효성을 검사하기 위한 테스트가 포함되어 있는지 확인합니다([UnitTests](UnitTests.md) 참조).
* 버그를 수정하는 경우 테스트를 작성하여 버그 수정 사항을 확인합니다.

프로젝트 관리자가 변경 내용을 검토합니다. 3일(영업일 기준) 이내에 모든 변경 사항을 검토하는 것을 목표로 합니다. 리뷰 댓글을 처리하고 토픽 분기로 푸시한 다음, 검토할 새로운 항목이 있음을 알려주는 댓글을 게시하세요.

> [!NOTE]
> 프로젝트에 제출된 모든 PR은 [MRTK 코딩 표준 가이드](CodingGuidelines.md)에 따라 심사되므로 원활한 프로세스를 위해 PR을 제출하기 전에 이를 검토하세요.

## <a name="pull-request-guidelines"></a>끌어오기 요청 지침

이러한 지침은 [Google의 엔지니어링 사례](https://google.github.io/eng-practices/review/developer/small-cls.html)를 기반으로 합니다.

### <a name="keep-pull-requests-small"></a>끌어오기 요청 작게 유지

작은 PR은 더 빠르고 철저하게 검토되고 버그를 유발할 가능성이 적고 롤백하기 쉽고 병합하기가 더 쉽습니다.

끌어오기 요청은 엔지니어가 30분 이내에 검토할 수 있을 정도로 작아야 합니다. 한 가지만 해결하도록 변경을 최소화합니다. 큰 PR을 만들어야 하는 경우 로컬 분기 또는 MRTK의 기능 분기로 이동할 수 있도록 여러 PR로 분할합니다. 새 자산(예: fbx, obj 파일)을 추가하지 말고 기존 자산을 재사용하도록 합니다.

### <a name="tests-should-be-added-in-the-same-pr-as-your-fix--feature-except-for-emergencies"></a>테스트는 응급 상황을 제외하고 수정/기능과 동일한 PR에 추가해야 합니다.

테스트는 변경 사항이 기존 코드를 회귀하지 않도록 하는 가장 좋은 방법이지만, 끌어오기 요청을 제출할 때 테스트를 잊어버리기 쉽습니다. PR에 테스트가 들어가도록 요구하는 것이 테스트를 작성하는 좋은 방법입니다.

모든 기능 및 버그 수정에는 관련 테스트가 있어야 합니다. 테스트를 작성할 전문 지식이나 시간이 없는 경우 테스트를 작성할 문제를 만들고 **현재 반복 고려** 레이블로 표시합니다.

### <a name="documentation-should-be-added-in-the-same-pull-request-as-a-fix--feature"></a>수정/기능과 동일한 끌어오기 요청에 설명서를 추가해야 합니다.

대부분의 개발자는 기능 사용 방법을 알고 있는 경우 코드가 아닌 설명서를 먼저 봅니다. 설명서를 최신 상태로 유지하면 사용자가 MRTK를 훨씬 쉽게 사용하고 의존할 수 있습니다.  항목이 최신 상태로 일관되게 유지되도록 설명서는 항상 관련 끌어보기과 함께 번들로 제공되어야 합니다.

docfx 사이트에서 필드/메서드에 대한 설명을 생성할 수 있도록 모든 공용 필드, 메서드, 속성에 [삼중 슬래시 요약 설명](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html)이 있는지 확인합니다. 필요한 경우 Documentation 폴더에서 Markdown 파일을 업데이트합니다.

### <a name="pull-request-descriptions-should-clearly-and-completely-describe-changes"></a>끌어오기 요청 설명은 변경 사항을 명확하고 완전하게 설명해야 합니다.

검토자는 끌어오기 요청에 대한 명확하고 완전한 설명을 통해 검토 중인 내용을 이해할 수 있습니다.

UX가 포함된 기능을 추가하는 경우 변경하려는 기능의 이미지/gif를 추가합니다. [여기 좋은 예가 있습니다](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532). 또 다른 제안 사항은 [예를 들어 이 끌어오기 요청](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896)에서 이전 및 이후의 gif를 포함하는 것입니다. 화면을 캡처하여 gif를 생성하는 데 권장되는 도구는 [ScreenToGif](https://www.screentogif.com/)입니다.
