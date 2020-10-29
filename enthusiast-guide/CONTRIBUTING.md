---
title: 영향을 주는 지침
description: Windows Mixed Reality 열성적인 가이드에 기여 하기 위한 기본 단계 및 지침을 알아보세요. 사용자 의견, 편집, 추가 및 도움을 주셔서 감사 합니다.
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 사용자 의견, 피드백 허브, 버그
appliesto:
- Windows 10
ms.openlocfilehash: 78f1a66ea6e853e55b8020747abea22a1dc686e5
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684441"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>Mixed Reality 열성적인 가이드에 기여

열성적인 가이드에 관심을 가져 주셔서 감사 합니다. 문서 개선을 위해 사용자 의견, 편집, 추가 및 도움을 주셔서 감사 합니다. 이 페이지에는 영향을 주는 기본 단계와 지침이 설명 되어 있습니다.

> [!IMPORTANT]
> docs.microsoft.com에 참여하는 모든 리포지토리는 [Microsoft 오픈 소스 준수 사항](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다. 자세한 내용은 [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/)(준수 사항 FAQ)를 참조하거나 [opencode@microsoft.com](mailto:opencode@microsoft.com)에 질문 또는 의견을 알려주세요.<br>
>
> 공용 리포지토리의 설명서 및 코드 예제에 대한 사소한 수정 또는 확인 내용은 [docs.microsoft.com 사용 약관](https://docs.microsoft.com/legal/termsofuse)에서 다룹니다. 새롭거나 중요한 변경 내용으로 인해 끌어오기 요청에서 Microsoft 직원이 아닌 경우 온라인 CLA(참가 사용권 계약)을 제출하도록 요청하는 주석이 생성됩니다. 온라인 양식 작성을 먼저 완료해야 Microsoft에서 끌어오기 요청을 수락할 수 있습니다.

## <a name="how-to-make-a-change"></a>변경을 수행 하는 방법

| 문서 변경을 제안하려면 다음 단계를 수행합니다. | 스크린샷 |
| :------------------- | :--------: |
| 1. Docs.microsoft.com 페이지를 표시 하는 경우 페이지 오른쪽 위에 있는 **편집** 단추를 클릭 합니다.  그러면 [GitHub 리포지토리](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide)의 해당 Markdown 소스 파일로 리디렉션됩니다. | ![편집 단추](images/edit_button.jpg) |
| 2. 아직 GitHub 계정이 없는 경우 오른쪽 위에서 **등록** 을 클릭 하 고 새 계정을 만듭니다. | ![등록 단추](images/signup-for-github-button.png)|
| 3. 해당 하는 GitHub 페이지가 열리면 편집 (연필 아이콘)을 클릭 합니다. | ![연필 단추](images/pencil_button.jpg)|
| 4. 파일 편집 창에서 Markdown 언어를 사용 하 여 콘텐츠를 변경 합니다. ([Markdown를 작성 하는 방법](https://help.github.com/articles/basic-writing-and-formatting-syntax/))| ![파일 편집](images/edit-in-github.png)|
| 5. 변경 내용 미리 보기를 클릭 하 여 서식이 예상 대로 표시 되는지 확인 합니다. | ![변경 내용 미리 보기](images/edit-in-github.png)|
| 6. 완료 되 면 페이지 아래쪽으로 스크롤하고 "파일 변경 내용 제안"을 클릭 하면 변경 내용을 확인할 수 있는 "변경 내용 비교" 페이지가 표시 됩니다. 그런 다음 "끌어오기 요청 만들기" 단추를 클릭 하 여 변경 내용을 제출 합니다. 이 시점에서 작업이 마무리됩니다. | ![변경 제안](images/propose.jpg)|

끌어오기 요청을 통해 변경 내용을 전송 하면 설명서 팀의 구성원에 의해 검토 됩니다. 요청이 수락 되 면 업데이트가에 게시 됩니다 [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide) .

* 내부 검토 전용의 경우 변경 내용을 볼 수 있습니다 [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) .

## <a name="working-with-branches"></a>분기 작업

[Mixed Reality 열성적인 가이드 GitHub 리포지토리](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) 는 두 개의 기본 부모 분기 인 [Master](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master)를 활용 합니다. Master,이 콘텐츠는 [스테이징 사이트](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)에서 검토 하 고 라이브 [사이트](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide)에 표시 되는 콘텐츠를 [실시간](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live)으로 확인할 수 있습니다.

기여를 만들 때 **마스터** 분기에 끌어오기 요청 (PR)을 제출 하세요. 이 분기는 스테이징 사이트에서 볼 수 있으며 실시간으로 게시할 준비가 완료된 기고문만 포함해야 합니다. 스테이징 사이트에서 선택 하 고 볼 수 있는 고유한 분기 이름으로 분기를 만들고 제출할 수도 있습니다. **라이브** 분기는 콘텐츠 관리자만 사용할 수 있습니다.

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>문제를 사용 하 여 Windows Mixed Reality 열성적인 가이드에 대 한 피드백 제공

사용자 의견을 제공 하거나 문제를 해결 하기 위해 실제 문서 페이지를 직접 수정 하는 대신 [문제](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) 를 해결 하 고 콘텐츠 소유자는 적시에 문제를 해결 하는 데 가장 적합 합니다.

특정 페이지와 관련 된 문제를 생성 하는 경우 토픽 제목 및 URL을 포함 해야 합니다.

이 콘텐츠를 지원 해 주셔서 감사 합니다.
