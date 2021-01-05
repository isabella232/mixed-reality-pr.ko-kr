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
ms.openlocfilehash: afb559937c2bde06d3c74c1c572aefec50502884
ms.sourcegitcommit: 9a93c9e9b3b088da942ac4386813ecf263c2e324
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865438"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a><span data-ttu-id="e8ebb-105">Mixed Reality 열성적인 가이드에 기여</span><span class="sxs-lookup"><span data-stu-id="e8ebb-105">Contributing to the Mixed Reality Enthusiast Guide</span></span>

<span data-ttu-id="e8ebb-106">열성적인 가이드에 관심을 가져 주셔서 감사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-106">Thank you for your interest in the Enthusiast Guide.</span></span> <span data-ttu-id="e8ebb-107">문서 개선을 위해 사용자 의견, 편집, 추가 및 도움을 주셔서 감사 합니다. 이 페이지에는 영향을 주는 기본 단계와 지침이 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-107">We appreciate your feedback, edits, additions and help with improving our docs. This page covers the basic steps and guidelines for contributing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8ebb-108">docs.microsoft.com에 참여하는 모든 리포지토리는 [Microsoft 오픈 소스 준수 사항](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-108">All repositories that publish to docs.microsoft.com have adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span> <span data-ttu-id="e8ebb-109">자세한 내용은 [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/)(준수 사항 FAQ)를 참조하거나 [opencode@microsoft.com](mailto:opencode@microsoft.com)에 질문 또는 의견을 알려주세요.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-109">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any questions or comments.</span></span><br>
>
> <span data-ttu-id="e8ebb-110">공용 리포지토리의 설명서 및 코드 예제에 대한 사소한 수정 또는 확인 내용은 [docs.microsoft.com 사용 약관](https://docs.microsoft.com/legal/termsofuse)에서 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-110">Minor corrections or clarifications to documentation and code examples in public repositories are covered by the [docs.microsoft.com Terms of Use](https://docs.microsoft.com/legal/termsofuse).</span></span> <span data-ttu-id="e8ebb-111">새롭거나 중요한 변경 내용으로 인해 끌어오기 요청에서 Microsoft 직원이 아닌 경우 온라인 CLA(참가 사용권 계약)을 제출하도록 요청하는 주석이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-111">New or significant changes will generate a comment in the pull request asking you to submit an online Contribution License Agreement (CLA) if you are not an employee of Microsoft.</span></span> <span data-ttu-id="e8ebb-112">온라인 양식 작성을 먼저 완료해야 Microsoft에서 끌어오기 요청을 수락할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-112">We need you to complete the online form before we can accept your pull request.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="e8ebb-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e8ebb-113">Before you start</span></span>

<span data-ttu-id="e8ebb-114">아직 없는 경우 [GitHub 계정을 만들어야](https://github.com/join)합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-114">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="e8ebb-115">Microsoft 직원 인 경우 microsoft [오픈 소스 포털](https://repos.opensource.microsoft.com/)의 microsoft 별칭에 GitHub 계정을 연결 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-115">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="e8ebb-116">**"Microsoft"** 및 **"MicrosoftDocs"** 조직에 참여 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-116">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations.</span></span>

<span data-ttu-id="e8ebb-117">GitHub 계정을 설정할 때 다음과 같은 보안 예방 조치를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-117">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="e8ebb-118">[Github 계정에 대 한 강력한 암호](https://github.com/settings/admin)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-118">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="e8ebb-119">[2 단계 인증](https://github.com/settings/two_factor_authentication/configure)을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-119">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="e8ebb-120">[복구 코드](https://github.com/settings/auth/recovery-codes) 를 안전한 장소에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-120">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="e8ebb-121">[공개 프로필 설정을](https://github.com/settings/profile)업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-121">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="e8ebb-122">사용자의 이름을 설정 하 고 *전자 메일 주소를 표시 하지 않도록* *공용 전자 메일* 을 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-122">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="e8ebb-123">사용자가 참여 하는 문서 페이지에 미리 보기가 표시 되기 때문에 프로필 사진을 업로드 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-123">We recommend you upload a profile picture because a thumbnail is shown on docs pages you contribute to.</span></span>
- <span data-ttu-id="e8ebb-124">명령줄을 사용할 계획인 경우 [Windows 용 Git 자격 증명 관리자](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)를 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-124">If you plan to use the command line, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest).</span></span> <span data-ttu-id="e8ebb-125">이렇게 하면 기여를 할 때마다 암호를 입력할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-125">That way, you won't have to enter your password every time you make a contribution.</span></span>

<span data-ttu-id="e8ebb-126">게시 시스템은 GitHub에 연결 되므로 이러한 단계가 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-126">The publishing system is tied to GitHub, so these steps are important.</span></span> <span data-ttu-id="e8ebb-127">GitHub 별칭을 사용 하 여 각 아티클에 대 한 작성자 또는 참가자로 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-127">You'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="how-to-make-a-change"></a><span data-ttu-id="e8ebb-128">변경을 수행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="e8ebb-128">How to make a change</span></span>

| <span data-ttu-id="e8ebb-129">문서 변경을 제안하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-129">To suggest a change to the docs, follow these steps:</span></span> | <span data-ttu-id="e8ebb-130">스크린샷</span><span class="sxs-lookup"><span data-stu-id="e8ebb-130">Screenshots</span></span> |
| :------------------- | :--------: |
| <span data-ttu-id="e8ebb-131">1. Docs.microsoft.com 페이지를 표시 하는 경우 페이지 오른쪽 위에 있는 **편집** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-131">1. If you're viewing a Docs.microsoft.com page, click the **Edit** button in the upper right of the page.</span></span>  <span data-ttu-id="e8ebb-132">그러면 [GitHub 리포지토리](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide)의 해당 Markdown 소스 파일로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-132">You will be redirected to the corresponding Markdown source file in the [GitHub repository](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide).</span></span> | ![편집 단추](images/edit_button.jpg) |
| <span data-ttu-id="e8ebb-134">2. 아직 GitHub 계정이 없는 경우 오른쪽 위에서 **등록** 을 클릭 하 고 새 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-134">2. If you don't already have a GitHub account, click **Sign Up** in the upper right and create a new account.</span></span> | ![등록 단추](images/signup-for-github-button.png)|
| <span data-ttu-id="e8ebb-136">3. 해당 하는 GitHub 페이지가 열리면 편집 (연필 아이콘)을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-136">3. On the corresponding GitHub page that opens, click Edit (the pencil icon).</span></span> | ![연필 단추](images/pencil_button.jpg)|
| <span data-ttu-id="e8ebb-138">4. 파일 편집 창에서 [파일 메타 데이터를 업데이트](#updating-metadata) 하 고 Markdown language를 사용 하 여 콘텐츠를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-138">4. In the Edit file pane, [update the files metadata](#updating-metadata) and use Markdown language to change the content.</span></span> <span data-ttu-id="e8ebb-139">([Markdown를 작성 하는 방법](https://help.github.com/articles/basic-writing-and-formatting-syntax/))</span><span class="sxs-lookup"><span data-stu-id="e8ebb-139">([How to write markdown.](https://help.github.com/articles/basic-writing-and-formatting-syntax/))</span></span>| ![파일 편집](images/edit-in-github.png)|
| <span data-ttu-id="e8ebb-141">5. 변경 내용 미리 보기를 클릭 하 여 서식이 예상 대로 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-141">5. Click Preview changes to verify the formatting looks as expected.</span></span> | ![변경 내용 미리 보기](images/edit-in-github.png)|
| <span data-ttu-id="e8ebb-143">6. 완료 되 면 페이지 아래쪽으로 스크롤하고 "파일 변경 내용 제안"을 클릭 하면 변경 내용을 확인할 수 있는 "변경 내용 비교" 페이지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-143">6. When you're done, scroll to the bottom of the page and click "Propose file change", you will be presented with a "Comparing changes" page, allowing you to verify your changes.</span></span> <span data-ttu-id="e8ebb-144">그런 다음 "끌어오기 요청 만들기" 단추를 클릭 하 여 변경 내용을 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-144">Then click the "Create pull request" button to submit your changes.</span></span> <span data-ttu-id="e8ebb-145">이 시점에서 작업이 마무리됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-145">At this point you are finished!</span></span> | ![변경 제안](images/propose.jpg)|

<span data-ttu-id="e8ebb-147">끌어오기 요청을 통해 변경 내용을 전송 하면 설명서 팀의 구성원에 의해 검토 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-147">After you submit changes (via a pull request), they will be reviewed by a member of the documentation team.</span></span> <span data-ttu-id="e8ebb-148">요청이 수락 되 면 업데이트가에 게시 됩니다 [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide) .</span><span class="sxs-lookup"><span data-stu-id="e8ebb-148">If your request is accepted, updates are published to [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide).</span></span>

<span data-ttu-id="e8ebb-149">\* 내부 검토 전용의 경우 변경 내용을 볼 수 있습니다 [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) .</span><span class="sxs-lookup"><span data-stu-id="e8ebb-149">\*For internal review only, you can see your changes at [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master).</span></span>

### <a name="updating-metadata"></a><span data-ttu-id="e8ebb-150">메타 데이터 업데이트</span><span class="sxs-lookup"><span data-stu-id="e8ebb-150">Updating Metadata</span></span>

<span data-ttu-id="e8ebb-151">각 문서의 맨 위에 있는 메타 데이터를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-151">Update metadata at the top of each article:</span></span>
   * <span data-ttu-id="e8ebb-152">**제목**: 문서를 볼 때 브라우저 탭에 표시 되는 페이지 제목입니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-152">**title**: Page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="e8ebb-153">페이지 제목은 SEO 및 인덱싱에 사용 되므로 필요한 경우를 제외 하 고는 제목을 변경 하지 않습니다. 단, 설명서를 공개 하기 전에는이 작업이 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-153">Page titles are used for SEO and indexing, so don't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="e8ebb-154">**설명**: SEO 및 검색을 향상 시키는 아티클의 콘텐츠에 대 한 간단한 설명을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-154">**description**: Write a brief description of the article's content, which boosts SEO and discovery.</span></span>
   * <span data-ttu-id="e8ebb-155">**작성자**: 페이지의 기본 소유자 인 경우 여기에 GitHub 별칭을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-155">**author**: If you're the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="e8ebb-156">**ms author**: 페이지의 기본 소유자 인 경우 여기에 Microsoft 별칭을 추가 @microsoft.com 합니다 (별칭만 필요 없음).</span><span class="sxs-lookup"><span data-stu-id="e8ebb-156">**ms.author**: If you're the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="e8ebb-157">**ms. 날짜**: 페이지에 주요 콘텐츠를 추가 하는 경우에는 날짜를 업데이트 하지만 설명, 서식, 문법 또는 철자와 같은 픽스는 업데이트 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-157">**ms.date**: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="e8ebb-158">**키워드**: SEO의 키워드 지원 (검색 엔진 최적화).</span><span class="sxs-lookup"><span data-stu-id="e8ebb-158">**keywords**: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="e8ebb-159">사용자의 문서와 관련 된 키워드를 쉼표와 공백으로 구분 하 고 목록에서 마지막 키워드 뒤에 문장 부호는 추가 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-159">Add keywords, separated by a comma and a space, that are specific to your article, but no punctuation after the last keyword in your list.</span></span> <span data-ttu-id="e8ebb-160">모든 문서에 적용 되는 전역 키워드는 다른 곳에서 관리 되므로 추가할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-160">You don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 

### <a name="renaming-or-deleting-an-existing-article"></a><span data-ttu-id="e8ebb-161">기존 아티클 이름 바꾸기 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="e8ebb-161">Renaming or deleting an existing article</span></span>

<span data-ttu-id="e8ebb-162">변경 시 기존 아티클의 이름을 바꾸거나 삭제 하는 경우에는 리디렉션을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-162">If your change will rename or delete an existing article, be sure to add a redirect.</span></span> <span data-ttu-id="e8ebb-163">이렇게 하면 기존 문서에 대 한 링크를 가진 모든 사용자가 올바른 위치가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-163">That way, anyone with a link to the existing article will still end up in the right place.</span></span> <span data-ttu-id="e8ebb-164">리디렉션은 리포지토리의 루트에 있는 파일의 .openpublishing.redirection.js에 의해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-164">Redirects are managed by the .openpublishing.redirection.json file in the root of the repo.</span></span>

<span data-ttu-id="e8ebb-165">.openpublishing.redirection.js에 대 한 리디렉션을 추가 하려면 배열에 항목을 추가 합니다 `redirections` .</span><span class="sxs-lookup"><span data-stu-id="e8ebb-165">To add a redirect to .openpublishing.redirection.json, add an entry to the `redirections` array:</span></span>

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/enthusiast-guide/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- <span data-ttu-id="e8ebb-166">는 `source_path` 제거 하는 이전 아티클의 상대 저장소 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-166">The `source_path` is the relative repository path to the old article that you're removing.</span></span> <span data-ttu-id="e8ebb-167">경로는로 시작 `mixed-reality-docs/enthusiast-guide` 하 고로 끝나야 `.md` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-167">Be sure the path starts with `mixed-reality-docs/enthusiast-guide` and ends with `.md`.</span></span>
- <span data-ttu-id="e8ebb-168">는 `redirect_url` 이전 문서에서 새 아티클에 대 한 상대 공용 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-168">The `redirect_url` is the relative public URL from the old article to the new article.</span></span> <span data-ttu-id="e8ebb-169">이 URL은  `mixed-reality-docs/enthusiast-guide` `.md` 리포지토리 경로가 아니라 공용 url을 참조 하므로이 url에 또는가 포함 되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-169">Be sure that this URL **doesn't** contain `mixed-reality-docs/enthusiast-guide` or `.md`, as it refers to the public URL and not the repository path.</span></span> <span data-ttu-id="e8ebb-170">를 사용 하 여 새 문서 내의 섹션에 연결할 `#section` 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-170">Linking to a section within the new article using `#section` is allowed.</span></span> <span data-ttu-id="e8ebb-171">필요한 경우 여기서 다른 사이트에 대 한 절대 경로를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-171">You can also use an absolute path to another site here, if necessary.</span></span>
- <span data-ttu-id="e8ebb-172">`redirect_document_id` 이전 파일의 문서 ID를 유지할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-172">`redirect_document_id` indicates whether you would like to keep the document ID from the previous file.</span></span> <span data-ttu-id="e8ebb-173">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-173">The default is `false`.</span></span> <span data-ttu-id="e8ebb-174">`true`리디렉션된 아티클의 특성 값을 유지 하려는 경우에 사용 합니다 `ms.documentid` .</span><span class="sxs-lookup"><span data-stu-id="e8ebb-174">Use `true` if you want to preserve the `ms.documentid` attribute value from the redirected article.</span></span> <span data-ttu-id="e8ebb-175">문서 ID를 유지 하는 경우 페이지 보기 및 순위와 같은 데이터가 대상 문서에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-175">If you preserve the document ID, data, such as page views and rankings, will be transferred to the target article.</span></span> <span data-ttu-id="e8ebb-176">리디렉션이 주로 이름 바꾸기 인 경우에는이 작업을 수행 하 고, 동일한 콘텐츠 중 일부만 포함 하는 다른 문서에 대 한 포인터는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-176">Do this if the redirect is primarily a rename, and not a pointer to different article that only covers some of the same content.</span></span>

<span data-ttu-id="e8ebb-177">리디렉션을 추가 하는 경우에도 이전 파일을 삭제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-177">If you add a redirect, be sure to delete the old file as well.</span></span>

### <a name="creating-a-new-article"></a><span data-ttu-id="e8ebb-178">새 문서 만들기</span><span class="sxs-lookup"><span data-stu-id="e8ebb-178">Creating a new article</span></span>

<span data-ttu-id="e8ebb-179">웹 브라우저에서 GitHub를 통해 설명서 리포지토리에서 *새 문서를 만들려면* 다음 워크플로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-179">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="e8ebb-180">오른쪽 위에 있는 **포크** 단추를 사용 하 여 MicrosoftDocs/mixed-reality/tree/docs/열성적인 ' 마스터 ' 분기에서 포크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-180">Create a fork off the MicrosoftDocs/mixed-reality/tree/docs/enthusiast-guide 'master' branch (using the **Fork** button in the top right).</span></span>

   ![마스터 분기를 포크 합니다.](images/forkbranch.png)
2. <span data-ttu-id="e8ebb-182">"Mixed-reality/열성적인" 폴더의 오른쪽 위에서 **새 파일 만들기** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-182">In the "mixed-reality/enthusiast-guide" folder, select **Create new file** in the top right.</span></span>
3. <span data-ttu-id="e8ebb-183">문서에 대 한 페이지 이름 (공백 대신 하이픈을 사용 하 고 구두점 또는 아포스트로피를 사용 하지 않음)을 만든 후 ".ma"를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-183">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![새 페이지의 이름을로 합니다.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="e8ebb-185">"Mixed reality-docs/열성적인" 폴더 내에서 새 문서를 만들었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-185">Make sure you create the new article from within the "mixed-reality-docs/enthusiast" folder.</span></span> <span data-ttu-id="e8ebb-186">새 파일 이름 줄에서 "/mixed-reality-docs/enthusiast-guide"를 확인 하 여이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-186">You can confirm this by checking for "/mixed-reality-docs/enthusiast-guide" in the new file name line.</span></span>

4. <span data-ttu-id="e8ebb-187">새 페이지 위쪽에 다음 메타 데이터 블록을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-187">At the top of your new page, add the following metadata block:</span></span>

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. <span data-ttu-id="e8ebb-188">[위의 섹션](#updating-metadata)에 설명 된 지침에 따라 관련 메타 데이터 필드를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-188">Fill in the relevant metadata fields per the instructions in the [section above](#updating-metadata).</span></span>
6. <span data-ttu-id="e8ebb-189">[Markdown 기본 사항을](#markdown-basics)사용 하 여 문서 콘텐츠를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-189">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="e8ebb-190">`## See also`문서의 맨 아래에 있는 섹션을 다른 관련 문서에 대 한 링크와 함께 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-190">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="e8ebb-191">완료 되 면 **새 파일 커밋** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-191">When finished, select **Commit new file**.</span></span>
9. <span data-ttu-id="e8ebb-192">**새 끌어오기 요청** 을 선택 하 고 포크의 ' 마스터 ' 분기를 MicrosoftDocs/mixed-열성적인/' master '에 병합 합니다. 화살표가 올바른 방법을 가리키고 있는지 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-192">Select **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality/enthusiast-guide 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![포크에서 MicrosoftDocs/mixed-reality/열성적인로 끌어오기 요청 만들기](images/pr_to_master.PNG)

## <a name="working-with-branches"></a><span data-ttu-id="e8ebb-194">분기 작업</span><span class="sxs-lookup"><span data-stu-id="e8ebb-194">Working with Branches</span></span>

<span data-ttu-id="e8ebb-195">[Mixed Reality 열성적인 가이드 GitHub 리포지토리](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) 는 두 개의 기본 부모 분기 인 [Master](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master)를 활용 합니다. Master,이 콘텐츠는 [스테이징 사이트](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)에서 검토 하 고 라이브 [사이트](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide)에 표시 되는 콘텐츠를 [실시간](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live)으로 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-195">The [Mixed Reality Enthusiast Guide GitHub repository](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) utilizes two main parent branches: [Master](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master), this content can be reviewed on the [staging site](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide), and [Live](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live), for content appearing on the [live site](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide).</span></span>

<span data-ttu-id="e8ebb-196">기여를 만들 때 **마스터** 분기에 끌어오기 요청 (PR)을 제출 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-196">When making contributions, please submit your Pull Request (PR) to the **Master** branch.</span></span> <span data-ttu-id="e8ebb-197">이 분기는 스테이징 사이트에서 볼 수 있으며 실시간으로 게시할 준비가 완료된 기고문만 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-197">This branch can be viewed on the staging site and should only contain contributions that are ready to be published live.</span></span> <span data-ttu-id="e8ebb-198">스테이징 사이트에서 선택 하 고 볼 수 있는 고유한 분기 이름으로 분기를 만들고 제출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-198">You may also create and submit a branch with your own unique branch name which can be selected and viewed in the staging site.</span></span> <span data-ttu-id="e8ebb-199">**라이브** 분기는 콘텐츠 관리자만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-199">(The **Live** branch is only allowed for use by the content administrators.)</span></span>

## <a name="markdown-basics"></a><span data-ttu-id="e8ebb-200">Markdown 기본 사항</span><span class="sxs-lookup"><span data-stu-id="e8ebb-200">Markdown basics</span></span>

<span data-ttu-id="e8ebb-201">다음 리소스는 Markdown 언어를 사용 하 여 문서를 편집 하는 방법을 배우는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-201">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="e8ebb-202">Markdown 기본 사항</span><span class="sxs-lookup"><span data-stu-id="e8ebb-202">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="e8ebb-203">한눈에 Markdown 참조 포스터</span><span class="sxs-lookup"><span data-stu-id="e8ebb-203">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="e8ebb-204">Docs.microsoft.com에 대 한 Markdown 쓰기에 대 한 추가 리소스</span><span class="sxs-lookup"><span data-stu-id="e8ebb-204">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="e8ebb-205">테이블 추가</span><span class="sxs-lookup"><span data-stu-id="e8ebb-205">Adding tables</span></span>

<span data-ttu-id="e8ebb-206">스타일 docs.microsoft.com 스타일을 지정 하는 방식 때문에 인라인 CSS를 시도 하더라도 테두리나 사용자 지정 스타일은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-206">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="e8ebb-207">짧은 시간 동안 작동 하는 것 처럼 보이지만 결국 플랫폼은 테이블에서 스타일을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-207">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="e8ebb-208">따라서 미리 계획 하 고 테이블을 단순하게 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-208">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="e8ebb-209">[Markdown 테이블을 쉽게 만들 수 있는 사이트는 다음과 같습니다](https://www.tablesgenerator.com/markdown_tables).</span><span class="sxs-lookup"><span data-stu-id="e8ebb-209">[Here’s a site that makes Markdown tables easy](https://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="e8ebb-210">[Visual Studio Code에 대 한 Docs Markdown 확장](https://docs.microsoft.com/teamblog/docs-extension) 은 [Visual Studio Code (아래 참조)](#using-visual-studio-code) 를 사용 하 여 문서를 편집 하는 경우에도 테이블을 쉽게 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-210">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="e8ebb-211">이미지 추가</span><span class="sxs-lookup"><span data-stu-id="e8ebb-211">Adding images</span></span>

<span data-ttu-id="e8ebb-212">리포지토리의 "mixed reality-docs/images" 폴더에 이미지를 업로드 한 다음 문서에서 적절 하 게 참조 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-212">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="e8ebb-213">이미지가 자동으로 전체 크기로 표시 됩니다. 즉, 큰 이미지는 문서의 전체 너비를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-213">Images will automatically show up at full-size, which means large images will fill the entire width of the article.</span></span> <span data-ttu-id="e8ebb-214">이미지를 업로드 하기 전에 미리 크기를 조정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-214">We recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="e8ebb-215">권장 되는 너비는 600 픽셀에서 700 픽셀 사이 이지만, 조밀한 스크린샷 또는 스크린 샷의 분수 인 경우 크기를 조정 하거나 축소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-215">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e8ebb-216">병합 하기 전에 분기 리포지토리에만 이미지를 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-216">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="e8ebb-217">따라서 문서에 이미지를 추가 하려면 먼저 [Visual Studio Code를 사용](#using-visual-studio-code) 하 여 포크의 "images" 폴더에 이미지를 추가 하거나 웹 브라우저에서 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-217">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="e8ebb-218">MicrosoftDocs/mixed reality 리포지토리를 분기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-218">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="e8ebb-219">포크에서 문서를 편집 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-219">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="e8ebb-220">문서에서 참조 하는 이미지를 포크의 "mixed reality-docs/images" 폴더에 업로드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-220">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="e8ebb-221">분기를 MicrosoftDocs/mixed-현실 ' master ' 분기에 병합 하는 **끌어오기 요청** 을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-221">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="e8ebb-222">사용자 고유의 분기 리포지토리를 설정 하는 방법을 알아보려면 [새 문서 만들기](#creating-a-new-article)에 대 한 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-222">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="e8ebb-223">작업 미리 보기</span><span class="sxs-lookup"><span data-stu-id="e8ebb-223">Previewing your work</span></span>

<span data-ttu-id="e8ebb-224">웹 브라우저를 통해 GitHub에서 편집 하는 동안 페이지 맨 위에 있는 **미리 보기** 탭을 선택 하 여 커밋 전 작업을 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-224">While editing in GitHub via a web browser, you can select the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="e8ebb-225">review.docs.microsoft.com의 변경 내용 미리 보기는 Microsoft 직원 에게만 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-225">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="e8ebb-226">Microsoft 직원: 기여를 ' 마스터 ' 분기에 병합 한 후에는에서 공개 되기 전에 콘텐츠를 검토할 수 있습니다 https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master .</span><span class="sxs-lookup"><span data-stu-id="e8ebb-226">Microsoft employees: once your contributions have been merged into the 'master' branch, you can review the content before it goes public at https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master.</span></span> <span data-ttu-id="e8ebb-227">왼쪽 열에 있는 목차를 사용 하 여 문서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-227">Find your article using the table of contents in the left column.</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="e8ebb-228">브라우저에서 편집 및 데스크톱 클라이언트를 사용 하 여 편집</span><span class="sxs-lookup"><span data-stu-id="e8ebb-228">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="e8ebb-229">브라우저에서 편집은 빠른 변경을 수행 하는 가장 쉬운 방법 이지만 다음과 같은 몇 가지 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-229">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="e8ebb-230">맞춤법 검사를 받을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-230">You don't get spell-check.</span></span>
- <span data-ttu-id="e8ebb-231">다른 문서에 대 한 스마트 링크를 얻을 수 없습니다 (문서의 파일 이름을 직접 입력 해야 함).</span><span class="sxs-lookup"><span data-stu-id="e8ebb-231">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="e8ebb-232">이미지를 업로드 하 고 참조 하는 것이 더 나을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-232">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="e8ebb-233">이러한 문제를 해결 하는 것이 아닌 경우에는 도움이 될 때 도움이 되는 몇 가지 [유용한 확장과](#useful-extensions) 함께 [Visual Studio Code](https://code.visualstudio.com/) 와 같은 데스크톱 클라이언트를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-233">If you'd rather not deal with these issues, use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) when contributing.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="e8ebb-234">Visual Studio Code 사용</span><span class="sxs-lookup"><span data-stu-id="e8ebb-234">Using Visual Studio Code</span></span>

<span data-ttu-id="e8ebb-235">[위에](#editing-in-the-browser-vs-editing-with-a-desktop-client)나열 된 이유 때문에 웹 브라우저가 아닌 데스크톱 클라이언트를 사용 하 여 문서를 편집 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-235">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="e8ebb-236">[Visual Studio Code](https://code.visualstudio.com/)를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-236">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="e8ebb-237">설치 프로그램</span><span class="sxs-lookup"><span data-stu-id="e8ebb-237">Setup</span></span>

<span data-ttu-id="e8ebb-238">이 리포지토리를 사용 하도록 Visual Studio Code를 구성 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-238">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="e8ebb-239">웹 브라우저에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-239">In a web browser:</span></span>
    1. <span data-ttu-id="e8ebb-240">[PC 용 Git를](https://git-scm.com/downloads)설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-240">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="e8ebb-241">[Visual Studio Code](https://code.visualstudio.com/)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-241">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="e8ebb-242">[분기 MicrosoftDocs/mixed-현실](#creating-a-new-article) . 아직 없는 경우.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-242">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="e8ebb-243">포크에서 **복제 또는 다운로드** 를 선택 하 고 URL을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-243">In your fork, select **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="e8ebb-244">Visual Studio Code에서 포크의 로컬 클론을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-244">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="e8ebb-245">**보기** 메뉴에서 **명령 팔레트** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-245">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="e8ebb-246">"Git: Clone"을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-246">Type "Git: Clone."</span></span>
    3. <span data-ttu-id="e8ebb-247">복사한 URL을 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-247">Paste the URL you copied.</span></span>
    4. <span data-ttu-id="e8ebb-248">PC에서 클론을 저장할 위치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-248">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="e8ebb-249">팝업에서 **리포지토리 열기** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-249">Select **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="e8ebb-250">문서 편집</span><span class="sxs-lookup"><span data-stu-id="e8ebb-250">Editing documentation</span></span>

<span data-ttu-id="e8ebb-251">Visual Studio Code를 사용 하 여 설명서를 변경 하려면 다음 워크플로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-251">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="e8ebb-252">Visual Studio Code 사용 하는 경우에는 문서 [편집](#how-to-make-a-change) 및 [만들기](#creating-a-new-article) 에 대 한 모든 지침과 위에서 [Markdown 편집의 기본](#markdown-basics)사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-252">All the guidance for [editing](#how-to-make-a-change) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="e8ebb-253">복제 된 분기가 공식 리포지토리를 사용 하 여 최신 상태 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-253">Make sure your cloned fork is up to date with the official repo.</span></span>
   1. <span data-ttu-id="e8ebb-254">웹 브라우저에서 끌어오기 요청을 만들어 MicrosoftDocs/mixed reality의 다른 참가자의 최근 변경 내용을 포크에 동기화 합니다. 화살표가 올바른 방법을 가리키고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-254">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![MicrosoftDocs/mixed-현실에서 포크로 변경 내용 동기화](images/sync_repos.PNG)
   2. <span data-ttu-id="e8ebb-256">Visual Studio Code에서 동기화 단추를 선택 하 여 새로 업데이트 된 포크를 로컬 클론에 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-256">In Visual Studio Code, select the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![동기화 단추 이미지를 클릭 합니다.](images/sync_clone.png)
2. <span data-ttu-id="e8ebb-258">Visual Studio Code를 사용 하 여 복제 된 리포지토리에서 문서를 만들거나 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-258">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="e8ebb-259">하나 이상의 문서 (필요한 경우 "images" 폴더에 이미지 추가)를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-259">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="e8ebb-260">**탐색기** 에서 변경 내용을 **저장** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-260">**Save** changes in **Explorer**.</span></span>
      
      ![탐색기에서 "모두 저장"을 선택 합니다.](images/explorer_save.png)
   3. <span data-ttu-id="e8ebb-262">**소스 제어** 의 모든 변경 내용 **커밋** (메시지가 표시 되 면 쓰기 커밋 메시지).</span><span class="sxs-lookup"><span data-stu-id="e8ebb-262">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![소스 제어에서 "모두 커밋"을 선택 합니다.](images/source_control_commit.png)
   4. <span data-ttu-id="e8ebb-264">**동기화** 단추를 선택 하 여 변경 내용을 원본으로 다시 동기화 합니다 (GitHub의 포크).</span><span class="sxs-lookup"><span data-stu-id="e8ebb-264">Select the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![동기화 단추를 클릭 합니다.](images/sync_back.png)
3. <span data-ttu-id="e8ebb-266">웹 브라우저에서 끌어오기 요청을 만들어 분기의 새 변경 내용을 MicrosoftDocs/mixed-현실 ' master '로 다시 동기화 합니다. 화살표가 올바른 방법을 가리키고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-266">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![포크에서 MicrosoftDocs/mixed reality로 끌어오기 요청 만들기](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="e8ebb-268">유용한 확장</span><span class="sxs-lookup"><span data-stu-id="e8ebb-268">Useful extensions</span></span>

<span data-ttu-id="e8ebb-269">문서를 편집할 때 다음과 같은 Visual Studio Code 확장을 유용 하 게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-269">The following Visual Studio Code extensions are useful when editing documentation:</span></span>

- <span data-ttu-id="e8ebb-270">[Visual Studio Code 용 Docs Markdown 확장](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - **Alt + M** 을 사용 하 여 다음과 같은 docs 제작 옵션 메뉴를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-270">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="e8ebb-271">업로드 한 이미지를 검색 하 고 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-271">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="e8ebb-272">목록과 같이 목록, 테이블 및 문서 특정 호출 등의 서식을 추가 `>[!NOTE]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-272">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="e8ebb-273">내부 링크와 책갈피를 검색 하 고 참조 합니다 (페이지 내의 특정 섹션에 대 한 링크).</span><span class="sxs-lookup"><span data-stu-id="e8ebb-273">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="e8ebb-274">서식 지정 오류가 강조 표시 됩니다. 자세한 내용은 오류를 마우스로 가리키십시오.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-274">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="e8ebb-275">[코드 맞춤법 검사기](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -철자가 잘못 된 단어에는 밑줄이 그어집니다. 철자가 잘못 된 단어를 마우스 오른쪽 단추로 클릭 하 여 변경 하거나 사전에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-275">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a><span data-ttu-id="e8ebb-276">문제를 사용 하 여 Windows Mixed Reality 열성적인 가이드에 대 한 피드백 제공</span><span class="sxs-lookup"><span data-stu-id="e8ebb-276">Using issues to provide feedback on Windows Mixed Reality Enthusiast Guide</span></span>

<span data-ttu-id="e8ebb-277">사용자 의견을 제공 하거나 문제를 해결 하기 위해 실제 문서 페이지를 직접 수정 하는 대신 [문제](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) 를 해결 하 고 콘텐츠 소유자는 적시에 문제를 해결 하는 데 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-277">To provide feedback, or point out a problem, rather than directly modifying actual documentation pages, [create an issue](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) and the content owners will do their best to address the issue in a timely fashion.</span></span>

<span data-ttu-id="e8ebb-278">특정 페이지와 관련 된 문제를 생성 하는 경우 토픽 제목 및 URL을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-278">Be sure to include the topic title and the URL if you are creating an issue regarding a specific page.</span></span>

<span data-ttu-id="e8ebb-279">이 콘텐츠를 지원 해 주셔서 감사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-279">Thank you for supporting this content!</span></span>
