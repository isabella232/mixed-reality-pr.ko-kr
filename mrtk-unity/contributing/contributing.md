---
title: MRTK에 기여
description: Mixed Reality Toolkit에 기여 하는 방법
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 버그 보고서
ms.openlocfilehash: 8132c39a2bac7ae0926f125a6362e411100c8406
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144518"
---
# <a name="contributing"></a><span data-ttu-id="c0b3a-104">참여</span><span class="sxs-lookup"><span data-stu-id="c0b3a-104">Contributing</span></span>

<span data-ttu-id="c0b3a-105">MRTK (Mixed Reality Toolkit)는 커뮤니티의 기여를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-105">The Mixed Reality Toolkit (MRTK) welcomes contributions from the community.</span></span> <span data-ttu-id="c0b3a-106">모든 변경 내용이 작거나 클 경우 [Mrtk 코딩 표준을](coding-guidelines.md)준수 해야 하므로 변경 내용을 검토 하는 동안 지연을 방지 하기 위해 개발 하는 동안이에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-106">All changes be they small or large, need to adhere to the [MRTK coding standards](coding-guidelines.md), so please ensure you are familiar with these while developing to avoid delays when the change is being reviewed.</span></span>

<span data-ttu-id="c0b3a-107">질문이 있는 경우 [에는 여유 시간에 대 한 혼합 현실 도구 키트 채널](https://holodevelopers.slack.com/messages/C2H4HT858)을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-107">If you have any questions, please reach out on the [mixed-reality-toolkit channel on Slack](https://holodevelopers.slack.com/messages/C2H4HT858).</span></span>
<span data-ttu-id="c0b3a-108">[자동 초대 발신자](https://holodevelopersslack.azurewebsites.net/)를 통해 Slack 커뮤니티에 가입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-108">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

## <a name="submission-process"></a><span data-ttu-id="c0b3a-109">제출 프로세스</span><span class="sxs-lookup"><span data-stu-id="c0b3a-109">Submission process</span></span>

<span data-ttu-id="c0b3a-110">개발자가 [새 문제를 만들기](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)시작 하 여 혼합 현실 도구 키트에 기여할 수 있도록 여러 경로를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-110">We provide several paths to enable developers to contribute to the Mixed Reality Toolkit, all starting with [creating a new Issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose).</span></span>

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

<span data-ttu-id="c0b3a-111">여기에서 다음 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-111">From here you file:</span></span>

- <span data-ttu-id="c0b3a-112">혼합 현실 도구 키트 구성 요소 중 하나를 사용 하 여 **버그 보고서** -기능 문제</span><span class="sxs-lookup"><span data-stu-id="c0b3a-112">**Bug report** - Functionality issue with one of the Mixed Reality Toolkit components</span></span>
- <span data-ttu-id="c0b3a-113">**설명서 문제** -Mixed Reality Toolkit [설명서](https://microsoft.github.io/MixedRealityToolkit-Unity) 의 문제</span><span class="sxs-lookup"><span data-stu-id="c0b3a-113">**Documentation issue** - Issue with the Mixed Reality Toolkit [documentation](https://microsoft.github.io/MixedRealityToolkit-Unity)</span></span>
- <span data-ttu-id="c0b3a-114">**기능 요청** -새 Mixed Reality Toolkit 기능에 대 한 제안</span><span class="sxs-lookup"><span data-stu-id="c0b3a-114">**Feature request** - Proposal for a new Mixed Reality Toolkit feature</span></span>

## <a name="proposing-feature-requests"></a><span data-ttu-id="c0b3a-115">기능 요청 제안</span><span class="sxs-lookup"><span data-stu-id="c0b3a-115">Proposing feature requests</span></span>

<span data-ttu-id="c0b3a-116">새 Mixed Reality Toolkit 기능을 요청 하는 경우 해결 해야 하는 고객 혜택/문제를 문서화 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-116">When requesting a new Mixed Reality Toolkit feature, it is important to document the customer benefit / problem to be solved.</span></span> <span data-ttu-id="c0b3a-117">제출 되 면 기능 요청을 검토 하 고 GitHub에서 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-117">Once submitted, a feature request will be reviewed and discussed on GitHub.</span></span> <span data-ttu-id="c0b3a-118">여러 고객에 게 유용한 작업을 보장 하기 위해 각 기능 제안의 토론을 열고 건설적인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-118">We encourage open and constructive discussion of each feature proposal to ensure that the work is beneficial to a large segment of customers.</span></span>

<span data-ttu-id="c0b3a-119">기능을 다시 사용 하지 않아도 되는 것을 방지 하기 위해 일반적으로이 기능을 개발 하는 동안에는이 기능을 시작 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-119">To avoid needing to rework the feature, it is generally recommended that development of the feature does not begin during the review phase.</span></span> <span data-ttu-id="c0b3a-120">커뮤니티 검토 프로세스에서 제안 된 구현이 크게 변경 되어야 할 수 있는 하나 이상의 문제를 발견 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-120">Many times, the community review process uncovers one or more issues that may require significant changes in the proposed implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="c0b3a-121">백로그에 이미 존재 하는 항목에 대 한 작업을 수행 하려는 경우 해당 작업 항목을 제안으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-121">If you wish to work on something that already exists on our backlog, you can use that work item as your proposal.</span></span> <span data-ttu-id="c0b3a-122">작업을 완료 하는 작업을 유지 관리자 알리는 작업에 대해서도 설명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-122">Be sure to also comment on the task notifying maintainers that you're working towards completing it.</span></span>

## <a name="contribution-process"></a><span data-ttu-id="c0b3a-123">기여 프로세스</span><span class="sxs-lookup"><span data-stu-id="c0b3a-123">Contribution process</span></span>

<span data-ttu-id="c0b3a-124">시작하려면 다음 단계를 수행하면됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-124">To get started, simply follow these steps:</span></span>

1. <span data-ttu-id="c0b3a-125">리포지토리를 포크합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-125">Fork the repository.</span></span> <span data-ttu-id="c0b3a-126">페이지 오른쪽 위에 있는 "포크" 단추를 클릭하고 흐름을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-126">Click on the "Fork" button on the top right of the page and follow the flow.</span></span>
1. <span data-ttu-id="c0b3a-127">주 분기에서 분기를 만들어 제출할 [](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) 준비가 될 때까지 변경 내용을 쉽게 격리할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-127">Create a branch in your fork (off of the [main](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) branch) to make it easier to isolate any changes until ready for submission.</span></span> <span data-ttu-id="c0b3a-128">릴리스 안정화 기간 동안 버그 수정은 최신 `prerelease/*` 분기를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-128">For bug fixes during a release stabilization period, look for the latest `prerelease/*` branch.</span></span> <span data-ttu-id="c0b3a-129">새 기능은 항상 로 이동해야 `main` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-129">New features should always go into `main`.</span></span>

<span data-ttu-id="c0b3a-130">Git 워크플로를 접하는 경우 [Github에서 이 소개를 확인하세요.](https://guides.github.com/activities/hello-world/)</span><span class="sxs-lookup"><span data-stu-id="c0b3a-130">If you are new to to the Git workflow, [check out this introduction from Github](https://guides.github.com/activities/hello-world/).</span></span>

<span data-ttu-id="c0b3a-131">버그 수정 또는 기능을 추가할 때 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-131">When adding a bug fix or feature, follow these steps:</span></span>

1. <span data-ttu-id="c0b3a-132">버그 수정 또는 기능을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-132">Implement the bug fix or feature.</span></span> <span data-ttu-id="c0b3a-133">MRTK를 빌드하고 배포하기 위한 지침은 [Hololens 및 WMR 디바이스에 배포에](../supported-devices/wmr-mrtk.md)있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-133">Instructions for building and deploying MRTK are at [Deploying to Hololens and WMR devices](../supported-devices/wmr-mrtk.md).</span></span> <span data-ttu-id="c0b3a-134">코딩 지침 을 따라야 [합니다.](../contributing/coding-guidelines.md)</span><span class="sxs-lookup"><span data-stu-id="c0b3a-134">Remember to follow the [Coding Guidelines](../contributing/coding-guidelines.md).</span></span>
1. <span data-ttu-id="c0b3a-135">기능을 추가하는 경우 기능을 보여 주는 예제 장면도 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-135">If adding a feature, also add an example scene that demonstrates the feature.</span></span>
1. <span data-ttu-id="c0b3a-136">실험적 기능을 추가하는 경우 테스트 및 설명서를 작성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-136">If adding an experimental feature, then writing tests and documentation are not necessary.</span></span> <span data-ttu-id="c0b3a-137">대신 [실험적 기능 지침](../contributing/experimental-features.md)을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-137">Instead, follow [experimental feature guidelines](../contributing/experimental-features.md).</span></span>
1. <span data-ttu-id="c0b3a-138">버그 수정/기능을 확인하는 테스트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-138">Add tests to verify the bug fix / feature.</span></span> <span data-ttu-id="c0b3a-139">테스트 작성 및 실행에 대한 지침은 [UnitTests](../contributing/unit-tests.md)에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-139">Instructions for writing and running tests are at [UnitTests](../contributing/unit-tests.md).</span></span>
1. <span data-ttu-id="c0b3a-140">코드 및 기능이 설명서 지침 에 설명된 대로 문서화되어 있는지 [확인합니다.](../contributing/documentation-guide.md)</span><span class="sxs-lookup"><span data-stu-id="c0b3a-140">Ensure the code and feature(s) are documented as described in the [Documentation Guidelines](../contributing/documentation-guide.md).</span></span>
1. <span data-ttu-id="c0b3a-141">코드가 모든 플랫폼에서 의도한 대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-141">Ensure the code works as intended on all platforms.</span></span> <span data-ttu-id="c0b3a-142">지원되는 플랫폼 목록은 [릴리스 정보](../release-notes/mrtk-26-release-notes.md) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-142">Please see [Release notes](../release-notes/mrtk-26-release-notes.md) for the list of supported platforms.</span></span> <span data-ttu-id="c0b3a-143">Windows UWP 프로젝트의 경우 코드는 [WACK 규격](https://developer.microsoft.com/windows/develop/app-certification-kit)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-143">For Windows UWP projects, code must be [WACK compliant](https://developer.microsoft.com/windows/develop/app-certification-kit).</span></span> <span data-ttu-id="c0b3a-144">이렇게 하려면 Visual Studio 솔루션을 생성하고 프로젝트를 마우스 오른쪽 단추로 클릭합니다. **Store**  >  **앱 패키지를 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="c0b3a-144">To do this, generate a Visual Studio solution, right click on project; **Store** > **Create App Packages**.</span></span> <span data-ttu-id="c0b3a-145">프롬프트에 따라 WACK 테스트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-145">Follow the prompts and run WACK tests.</span></span> <span data-ttu-id="c0b3a-146">모두 성공 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-146">Make sure they all succeed.</span></span>
1. <span data-ttu-id="c0b3a-147">끌어오기 요청을 만들 때 [끌어오기 요청](../contributing/pull-requests.md) 에 대 한 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c0b3a-147">Follow the instructions at [Pull Requests](../contributing/pull-requests.md) when making a pull request.</span></span>
