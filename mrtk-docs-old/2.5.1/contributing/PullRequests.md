---
title: PullRequests
description: 끌어오기 요청과 관련된 세부 정보입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, PR,
ms.openlocfilehash: 31db19154adbf7016aec609e7baca8c4fa3eda48
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690820"
---
# <a name="pull-requests"></a><span data-ttu-id="ce6b7-104">끌어오기 요청</span><span class="sxs-lookup"><span data-stu-id="ce6b7-104">Pull requests</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ce6b7-105">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="ce6b7-105">Prerequisites</span></span>

<span data-ttu-id="ce6b7-106">이전에 Microsoft 프로젝트에 기여하지 않은 경우 [기여 라이선스 계약](https://cla.microsoft.com/)에 서명하라는 메시지가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-106">If you haven't contributed to a Microsoft project before, you may be asked to sign a [contribution license agreement](https://cla.microsoft.com/).</span></span>
<span data-ttu-id="ce6b7-107">PR의 설명을 통해 귀하의 서명 가능 여부를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-107">A comment in the PR will let you know if you do.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ce6b7-108">Microsoft 직원이지만 [GitHub에서 Microsoft 조직](https://github.com/Microsoft)의 구성원이 아닌 경우, 끌어오기 요청을 시작하기 전에 [Microsoft의 오픈 소스](https://opensource.microsoft.com/)를 방문하여 corpnet에서 Microsoft 및 GitHub 계정을 연결하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-108">If you are a Microsoft employee and are not a member of the [Microsoft organization on GitHub](https://github.com/Microsoft), please link your Microsoft and GitHub accounts on corpnet by visiting [Open Source at Microsoft](https://opensource.microsoft.com/) before you start your pull request.</span></span> <span data-ttu-id="ce6b7-109">미리 수행해야 할 몇 가지 프로세스 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-109">There's some process stuff you'll need to do ahead of time.</span></span>

## <a name="creating-a-pull-request"></a><span data-ttu-id="ce6b7-110">끌어오기 요청 만들기</span><span class="sxs-lookup"><span data-stu-id="ce6b7-110">Creating a pull request</span></span>

<span data-ttu-id="ce6b7-111">끌어오기 요청을 제출할 준비가 되면 [mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development) 분기를 대상으로 하는 [끌어오기 요청을 만듭니다](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/mrtk_development...mrtk_development?expand=1).</span><span class="sxs-lookup"><span data-stu-id="ce6b7-111">When you are ready to submit a pull request, [create a pull request](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/mrtk_development...mrtk_development?expand=1) targeting the [mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development) branch.</span></span>

<span data-ttu-id="ce6b7-112">지침을 읽고 끌어오기 요청이 지침을 충족하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-112">Read the guidelines and ensure your pull request meets the guidelines.</span></span>

* <span data-ttu-id="ce6b7-113">PR과 관련된 모든 문제/기능 요청 또는 작업을 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-113">Make sure to reference any Issue / Feature Request or Task the PR relates to.</span></span>
* <span data-ttu-id="ce6b7-114">끌어오기 요청에 PR과 관련된 파일/변경 내용만 포함되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-114">Check the pull request contains only files / changes related to the PR.</span></span>
* <span data-ttu-id="ce6b7-115">설명서가 최신 상태이고 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-115">Check documentation is up to date and included.</span></span> <span data-ttu-id="ce6b7-116">모든 공용 필드에 댓글이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-116">Check all public fields have comments.</span></span>
* <span data-ttu-id="ce6b7-117">새 기능을 추가하는 경우 기능의 유효성을 검사하기 위한 테스트가 포함되어 있는지 확인합니다([UnitTests](UnitTests.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="ce6b7-117">If adding a new feature, check that tests are included to validate the feature (see [UnitTests](UnitTests.md)).</span></span>
* <span data-ttu-id="ce6b7-118">버그를 수정하는 경우 테스트를 작성하여 버그 수정 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-118">If fixing a bug, write a test to verify the bug fix.</span></span>

<span data-ttu-id="ce6b7-119">프로젝트 관리자가 변경 내용을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-119">The project maintainers will review your changes.</span></span> <span data-ttu-id="ce6b7-120">3일(영업일 기준) 이내에 모든 변경 사항을 검토하는 것을 목표로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-120">We aim to review all changes within three business days.</span></span> <span data-ttu-id="ce6b7-121">리뷰 댓글을 처리하고 토픽 분기로 푸시한 다음, 검토할 새로운 항목이 있음을 알려주는 댓글을 게시하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-121">Please address any review comments, push to your topic branch, and post a comment letting us know that there's new stuff to review.</span></span>

> [!NOTE]
> <span data-ttu-id="ce6b7-122">프로젝트에 제출된 모든 PR은 [MRTK 코딩 표준 가이드](CodingGuidelines.md)에 따라 심사되므로 원활한 프로세스를 위해 PR을 제출하기 전에 이를 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-122">All PR's submitted to the project will also be vetted according to the [MRTK coding standards guide](CodingGuidelines.md), so please review these before submitting your PR to ensure a smooth process.</span></span>

## <a name="pull-request-guidelines"></a><span data-ttu-id="ce6b7-123">끌어오기 요청 지침</span><span class="sxs-lookup"><span data-stu-id="ce6b7-123">Pull request guidelines</span></span>

<span data-ttu-id="ce6b7-124">이러한 지침은 [Google의 엔지니어링 사례](https://google.github.io/eng-practices/review/developer/small-cls.html)를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-124">These guidelines are based off of the [Google's engineering practices](https://google.github.io/eng-practices/review/developer/small-cls.html).</span></span>

### <a name="keep-pull-requests-small"></a><span data-ttu-id="ce6b7-125">끌어오기 요청 작게 유지</span><span class="sxs-lookup"><span data-stu-id="ce6b7-125">Keep pull requests small</span></span>

<span data-ttu-id="ce6b7-126">작은 PR은 더 빠르고 철저하게 검토되고 버그를 유발할 가능성이 적고 롤백하기 쉽고 병합하기가 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-126">Smaller PRs are reviewed more quickly and thoroughly, are less likely to introduce bugs, easier to roll back, and easier to merge.</span></span>

<span data-ttu-id="ce6b7-127">끌어오기 요청은 엔지니어가 30분 이내에 검토할 수 있을 정도로 작아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-127">Pull requests should be small enough that an engineer could review it in under 30 minutes.</span></span> <span data-ttu-id="ce6b7-128">한 가지만 해결하도록 변경을 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-128">Try to make a minimal change that addresses just one thing.</span></span> <span data-ttu-id="ce6b7-129">큰 PR을 만들어야 하는 경우 로컬 분기 또는 MRTK의 기능 분기로 이동할 수 있도록 여러 PR로 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-129">If you must create a large PR, split it into several PRs that go into either your local branch, or a feature branch of MRTK.</span></span> <span data-ttu-id="ce6b7-130">새 자산(예: fbx, obj 파일)을 추가하지 말고 기존 자산을 재사용하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-130">Avoid adding new assets (e.g. fbx, obj files) and instead aim to re-use existing assets.</span></span>

### <a name="tests-should-be-added-in-the-same-pr-as-your-fix--feature-except-for-emergencies"></a><span data-ttu-id="ce6b7-131">테스트는 응급 상황을 제외하고 수정/기능과 동일한 PR에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-131">Tests should be added in the same PR as your fix / feature, except for emergencies</span></span>

<span data-ttu-id="ce6b7-132">테스트는 변경 사항이 기존 코드를 회귀하지 않도록 하는 가장 좋은 방법이지만, 끌어오기 요청을 제출할 때 테스트를 잊어버리기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-132">Tests are the best way to ensure changes do not regress existing code, but it is also easy to forget about tests when submitting pull requests.</span></span> <span data-ttu-id="ce6b7-133">PR에 테스트가 들어가도록 요구하는 것이 테스트를 작성하는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-133">Requiring that they go in with your PR are a great way to ensure that tests get written.</span></span>

<span data-ttu-id="ce6b7-134">모든 기능 및 버그 수정에는 관련 테스트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-134">Every feature and bug fix should have tests associated with it.</span></span> <span data-ttu-id="ce6b7-135">테스트를 작성할 전문 지식이나 시간이 없는 경우 테스트를 작성할 문제를 만들고 **현재 반복 고려** 레이블로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-135">If you do not have the expertise or time to write a test, create an issue to write the tests, and mark them with label **Consider for Current Iteration**.</span></span>

### <a name="documentation-should-be-added-in-the-same-pull-request-as-a-fix--feature"></a><span data-ttu-id="ce6b7-136">수정/기능과 동일한 끌어오기 요청에 설명서를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-136">Documentation should be added in the same pull request as a fix / feature</span></span>

<span data-ttu-id="ce6b7-137">대부분의 개발자는 기능 사용 방법을 알고 있는 경우 코드가 아닌 설명서를 먼저 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-137">Most developers look first at documentation, not code, when understanding how to use a feature.</span></span> <span data-ttu-id="ce6b7-138">설명서를 최신 상태로 유지하면 사용자가 MRTK를 훨씬 쉽게 사용하고 의존할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-138">Ensuring documentation is up to date makes it much easier for people to consume and rely MRTK.</span></span>  <span data-ttu-id="ce6b7-139">항목이 최신 상태로 일관되게 유지되도록 설명서는 항상 관련 끌어보기과 함께 번들로 제공되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-139">Documentation should always be bundled with the related pull to ensure items remain up-to-date and consistent.</span></span>

<span data-ttu-id="ce6b7-140">docfx 사이트에서 필드/메서드에 대한 설명을 생성할 수 있도록 모든 공용 필드, 메서드, 속성에 [삼중 슬래시 요약 설명](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html)이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-140">Ensure every public field, method, property has [triple slash summary comments](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html) so our docfx site can generate descriptions for fields / methods.</span></span> <span data-ttu-id="ce6b7-141">필요한 경우 Documentation 폴더에서 Markdown 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-141">If needed, update markdown files in Documentation folder.</span></span>

### <a name="pull-request-descriptions-should-clearly-and-completely-describe-changes"></a><span data-ttu-id="ce6b7-142">끌어오기 요청 설명은 변경 사항을 명확하고 완전하게 설명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-142">Pull request descriptions should clearly and completely describe changes</span></span>

<span data-ttu-id="ce6b7-143">검토자는 끌어오기 요청에 대한 명확하고 완전한 설명을 통해 검토 중인 내용을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-143">Clear and complete descriptions of pull requests ensure reviewers understand what they are reviewing.</span></span>

<span data-ttu-id="ce6b7-144">UX가 포함된 기능을 추가하는 경우 변경하려는 기능의 이미지/gif를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-144">If adding features that contain UX, add an image / gif of the feature you are changing.</span></span> <span data-ttu-id="ce6b7-145">[여기 좋은 예가 있습니다](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532).</span><span class="sxs-lookup"><span data-stu-id="ce6b7-145">[Here is a good example](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532).</span></span> <span data-ttu-id="ce6b7-146">또 다른 제안 사항은 [예를 들어 이 끌어오기 요청](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896)에서 이전 및 이후의 gif를 포함하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-146">Another suggestion is to have a gif of Before and After, [for example in this pull request](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896).</span></span> <span data-ttu-id="ce6b7-147">화면을 캡처하여 gif를 생성하는 데 권장되는 도구는 [ScreenToGif](https://www.screentogif.com/)입니다.</span><span class="sxs-lookup"><span data-stu-id="ce6b7-147">A tool we recommend for generating gifs from screen captures is [ScreenToGif](https://www.screentogif.com/).</span></span>
