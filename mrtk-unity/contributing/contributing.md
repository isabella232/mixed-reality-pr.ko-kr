---
title: 참여
description: Mixed Reality 도구 키트에 기여하는 방법
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 버그 보고서,
ms.openlocfilehash: 525e704ae2f09580c8c19ca7e8a25dad4aed2647
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489263"
---
# <a name="contributing"></a>참여

MRTK(Mixed Reality 도구 키트)는 커뮤니티의 기여를 환영합니다. 모든 변경 내용은 작거나 크고 [MRTK 코딩 표준을](coding-guidelines.md)준수해야 하므로 변경 내용을 검토할 때 지연을 방지하기 위해 개발하는 동안 이러한 사항을 잘 알고 있어야 합니다.

질문이 있는 경우 [Slack의 mixed-reality-toolkit 채널에](https://holodevelopers.slack.com/messages/C2H4HT858)문의하세요.
[자동 초대 발신자](https://holodevelopersslack.azurewebsites.net/)를 통해 Slack 커뮤니티에 가입할 수 있습니다.

## <a name="submission-process"></a>제출 프로세스

개발자가 [새 문제](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)만들기부터 시작하여 Mixed Reality 도구 키트에 기여할 수 있는 여러 경로를 제공합니다.

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

여기에서 다음을 제출합니다.

- **버그 보고서** - Mixed Reality 도구 키트 구성 요소 중 하나의 기능 문제
- **설명서 문제** - Mixed Reality Toolkit [설명서](https://microsoft.github.io/MixedRealityToolkit-Unity) 관련 문제
- **기능 요청** - 새 Mixed Reality 도구 키트 기능에 대한 제안

## <a name="proposing-feature-requests"></a>기능 요청 제안

새로운 Mixed Reality Toolkit 기능을 요청할 때 해결해야 할 고객 혜택/문제를 문서화하는 것이 중요합니다. 제출되면 GitHub에서 기능 요청을 검토하고 논의합니다. 각 기능 제안에 대해 개방적이고 간략하게 논의하여 대규모 고객 세그먼트에 작업이 도움이 되도록 하는 것이 좋습니다.

기능을 다시 작업할 필요가 없도록 하려면 일반적으로 검토 단계에서 기능 개발을 시작하지 않는 것이 좋습니다. 커뮤니티 검토 프로세스에서 제안된 구현에서 중요한 변경이 필요할 수 있는 하나 이상의 문제를 발견할 수 있는 경우가 많습니다.

> [!NOTE]
> 백로그에 이미 존재하는 항목에 대해 작업하려는 경우 해당 작업 항목을 제안으로 사용할 수 있습니다. 또한 완료를 위해 작업 중임을 유지 관리자에게 알리는 작업에 대해서도 주석을 달 수 있습니다.

## <a name="contribution-process"></a>기여 프로세스

시작하려면 다음 단계를 수행하면됩니다.

1. 리포지토리를 포크 합니다. 페이지의 오른쪽 위에 있는 "포크" 단추를 클릭 하 고 흐름을 따릅니다.
1. 분기에 분기 ( [주](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) 분기의 외부 분기)를 만들어 제출할 준비가 될 때까지 변경 내용을 보다 쉽게 격리할 수 있도록 합니다. 릴리스 안정화 기간 동안 버그를 수정 하려면 최신 분기를 찾으십시오 `prerelease/*` . 새 기능은 항상로 전환 되어야 합니다 `main` .

Git 워크플로를 처음 접하는 경우 [Github에서이 소개를 확인 하세요](https://guides.github.com/activities/hello-world/).

버그 수정 또는 기능을 추가할 때 다음 단계를 수행 합니다.

1. 버그 수정 또는 기능을 구현 합니다. MRTK를 빌드하고 배포 하는 방법에 대 한 지침은 [Buildanddeploy](../updates-deployment/build-and-deploy.md)에 있습니다. [코딩 지침](../contributing/coding-guidelines.md)을 따라야 합니다.
1. 기능을 추가 하는 경우 기능을 보여 주는 예제 장면을 추가 합니다.
1. 실험적 기능을 추가 하는 경우 테스트 및 설명서를 작성할 필요가 없습니다. 대신 [실험적 기능 지침](../contributing/experimental-features.md)을 따릅니다.
1. 버그 수정/기능을 확인 하는 테스트를 추가 합니다. 테스트 작성 및 실행에 대 한 지침은 단위 [테스트](../contributing/unit-tests.md)에 있습니다.
1. 코드 및 기능이 [설명서 지침](../contributing/documentation-guide.md)에 설명 된 대로 설명 되어 있는지 확인 합니다.
1. 코드가 모든 플랫폼에서 의도 한 대로 작동 하는지 확인 합니다. 지원 되는 플랫폼 목록은 [릴리스 정보](../release-notes/mrtk-26-release-notes.md) 를 참조 하세요. Windows UWP 프로젝트의 경우 코드는 [Wack 규격](https://developer.microsoft.com/windows/develop/app-certification-kit)이어야 합니다. 이렇게 하려면 Visual Studio 솔루션을 생성 하 고 프로젝트를 마우스 오른쪽 단추로 클릭 합니다. **저장소**  >  **앱 패키지를 만듭니다**. 프롬프트에 따라 WACK 테스트를 실행합니다. 모두 성공했는지 확인합니다.
1. 끌어오기 요청을 만들 때 [끌어오기 요청의](../contributing/pull-requests.md) 지침을 따릅니다.
