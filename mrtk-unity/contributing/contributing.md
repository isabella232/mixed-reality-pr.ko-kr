---
title: MRTK에 기여
description: 혼합 현실에 기여 하는 방법 Toolkit
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 버그 보고서
ms.openlocfilehash: b79f69cbb6dea1201c88d9fd1a354967ce40735e
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282047"
---
# <a name="contributing-to-mrtk"></a>MRTK에 기여

혼합 현실 Toolkit (mrtk)는 커뮤니티의 기여를 시작 합니다. 모든 변경 내용이 작거나 클 경우 [Mrtk 코딩 표준을](coding-guidelines.md)준수 해야 하므로 변경 내용을 검토 하는 동안 지연을 방지 하기 위해 개발 하는 동안이에 대해 잘 알고 있어야 합니다.

질문이 있는 경우 [에는 여유 시간에 대 한 혼합 현실 도구 키트 채널](https://holodevelopers.slack.com/messages/C2H4HT858)을 확인 하세요.
[자동 초대 발신자](https://holodevelopersslack.azurewebsites.net/)를 통해 Slack 커뮤니티에 가입할 수 있습니다.

## <a name="submission-process"></a>제출 프로세스

개발자가 [새 문제를 만들기](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)시작 하는 Toolkit 혼합 현실에 기여할 수 있도록 여러 경로를 제공 합니다.

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

여기에서 다음 파일을 사용할 수 있습니다.

- **버그 보고서** -혼합 현실 Toolkit 구성 요소 중 하나를 사용 하는 기능 문제
- **설명서 문제** -혼합 현실 Toolkit [설명서](https://microsoft.github.io/MixedRealityToolkit-Unity) 에 문제가 있습니다.
- **기능 요청** -새 Mixed Reality Toolkit 기능에 대 한 제안

## <a name="proposing-feature-requests"></a>기능 요청 제안

새 Mixed Reality Toolkit 기능을 요청 하는 경우 해결 해야 하는 고객 혜택/문제를 문서화 하는 것이 중요 합니다. 제출 되 면 기능 요청을 검토 하 고 GitHub에 대해 설명 합니다. 여러 고객에 게 유용한 작업을 보장 하기 위해 각 기능 제안의 토론을 열고 건설적인 하는 것이 좋습니다.

기능을 다시 사용 하지 않아도 되는 것을 방지 하기 위해 일반적으로이 기능을 개발 하는 동안에는이 기능을 시작 하지 않는 것이 좋습니다. 커뮤니티 검토 프로세스에서 제안 된 구현이 크게 변경 되어야 할 수 있는 하나 이상의 문제를 발견 하는 경우가 많습니다.

> [!NOTE]
> 백로그에 이미 존재 하는 항목에 대 한 작업을 수행 하려는 경우 해당 작업 항목을 제안으로 사용할 수 있습니다. 작업을 완료 하는 작업을 유지 관리자 알리는 작업에 대해서도 설명 해야 합니다.

## <a name="contribution-process"></a>기여 프로세스

시작 하려면 다음 단계를 수행 하면 됩니다.

1. 리포지토리를 포크합니다. 페이지의 오른쪽 위에 있는 "포크" 단추를 클릭 하 고 흐름을 따릅니다.
1. 분기에 분기 ( [주](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) 분기의 외부 분기)를 만들어 제출할 준비가 될 때까지 변경 내용을 보다 쉽게 격리할 수 있도록 합니다. 릴리스 안정화 기간 동안 버그를 수정 하려면 최신 분기를 찾으십시오 `prerelease/*` . 새 기능은 항상로 전환 되어야 합니다 `main` .

Git 워크플로를 처음 접하는 경우 [Github에서이 소개를 확인 하세요](https://guides.github.com/activities/hello-world/).

버그 수정 또는 기능을 추가할 때 다음 단계를 수행 합니다.

1. 버그 수정 또는 기능을 구현 합니다. MRTK를 빌드하고 배포 하는 방법에 대 한 지침은 [Hololens 및 WMR 장치에 배포 하](../supported-devices/wmr-mrtk.md)는 것입니다. [코딩 지침](../contributing/coding-guidelines.md)을 따라야 합니다.
1. 기능을 추가 하는 경우 기능을 보여 주는 예제 장면을 추가 합니다.
1. 실험적 기능을 추가 하는 경우 테스트 및 설명서를 작성할 필요가 없습니다. 대신 [실험적 기능 지침](../contributing/experimental-features.md)을 따릅니다.
1. 버그 수정/기능을 확인 하는 테스트를 추가 합니다. 테스트 작성 및 실행에 대 한 지침은 단위 [테스트](../contributing/unit-tests.md)에 있습니다.
1. 코드 및 기능이 [설명서 지침](../contributing/documentation-guide.md)에 설명 된 대로 설명 되어 있는지 확인 합니다.
1. 코드가 모든 플랫폼에서 의도 한 대로 작동 하는지 확인 합니다. 지원 되는 플랫폼 목록은 [릴리스 정보](../release-notes/mrtk-26-release-notes.md) 를 참조 하세요. UWP 프로젝트 Windows 경우 코드는 [wack 규격](https://developer.microsoft.com/windows/develop/app-certification-kit)이어야 합니다. 이렇게 하려면 Visual Studio 솔루션을 생성 하 고 프로젝트를 마우스 오른쪽 단추로 클릭 합니다. **저장소**  >  **앱 패키지를 만듭니다**. 프롬프트에 따라 WACK 테스트를 실행 합니다. 모두 성공 했는지 확인 합니다.
1. 끌어오기 요청을 만들 때 [끌어오기 요청](../contributing/pull-requests.md) 에 대 한 지침을 따릅니다.
