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
# <a name="documentation-guidelines"></a><span data-ttu-id="f72b6-104">설명서 지침</span><span class="sxs-lookup"><span data-stu-id="f72b6-104">Documentation guidelines</span></span>

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

<span data-ttu-id="f72b6-105">이 문서에서는 MRTK(Mixed Reality Toolkit)에 대한 설명서 지침 및 표준을 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-105">This document outlines the documentation guidelines and standards for the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="f72b6-106">설명서 작성 및 생성의 기술적 측면을 소개하고, 일반적인 문제를 강조 표시하고, 권장되는 쓰기 스타일을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-106">This provides an introduction to technical aspects of documentation writing and generation, to highlight common pitfalls, and to describe the recommended writing style.</span></span>

<span data-ttu-id="f72b6-107">페이지 자체는 예제로 사용되므로 의도한 스타일과 설명서의 가장 일반적인 태그 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-107">The page itself is supposed to serve as an example, therefore it uses the intended style and the most common markup features of the documentation.</span></span>

- [<span data-ttu-id="f72b6-108">원본</span><span class="sxs-lookup"><span data-stu-id="f72b6-108">Source</span></span>](#source-documentation)
- [<span data-ttu-id="f72b6-109">방법</span><span class="sxs-lookup"><span data-stu-id="f72b6-109">How-to</span></span>](#how-to-documentation)
- [<span data-ttu-id="f72b6-110">디자인</span><span class="sxs-lookup"><span data-stu-id="f72b6-110">Design</span></span>](#design-documentation)
- [<span data-ttu-id="f72b6-111">성능 정보</span><span class="sxs-lookup"><span data-stu-id="f72b6-111">Performance notes</span></span>](#performance-notes)
- [<span data-ttu-id="f72b6-112">주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="f72b6-112">Breaking changes</span></span>](#breaking-changes)

---

## <a name="functionality-and-markup"></a><span data-ttu-id="f72b6-113">기능 및 태그</span><span class="sxs-lookup"><span data-stu-id="f72b6-113">Functionality and markup</span></span>

<span data-ttu-id="f72b6-114">이 섹션에서는 자주 필요한 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-114">This section describes frequently needed features.</span></span> <span data-ttu-id="f72b6-115">작동 방식을 확인하려면 페이지의 소스 코드를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-115">To see how they work, look at the source code of the page.</span></span>

1. <span data-ttu-id="f72b6-116">번호가 매겨진 목록</span><span class="sxs-lookup"><span data-stu-id="f72b6-116">Numbered lists</span></span>
   1. <span data-ttu-id="f72b6-117">3개 이상의 선행 공백이 있는 중첩 번호가 매겨진 목록</span><span class="sxs-lookup"><span data-stu-id="f72b6-117">Nested numbered lists with at least 3 leading blank spaces</span></span>
   1. <span data-ttu-id="f72b6-118">코드의 실제 숫자는 관련이 없습니다. 구문 분석 시 올바른 항목 번호 설정이 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-118">The actual number in code is irrelevant; parsing will take care of setting the correct item number.</span></span>

- <span data-ttu-id="f72b6-119">글머리 기호 목록</span><span class="sxs-lookup"><span data-stu-id="f72b6-119">Bullet point lists</span></span>
  - <span data-ttu-id="f72b6-120">중첩된 글머리 기호 목록</span><span class="sxs-lookup"><span data-stu-id="f72b6-120">Nested bullet point lists</span></span>
- <span data-ttu-id="f72b6-121">이중  \* 별표가 있는 굵은 텍스트 \*\*\*</span><span class="sxs-lookup"><span data-stu-id="f72b6-121">Text in **bold** with \*\*double asterisk\*\*</span></span>
- <span data-ttu-id="f72b6-122">밑수 또는 단일  별표가  \_ \_ \* 있는 italic text\*</span><span class="sxs-lookup"><span data-stu-id="f72b6-122">_italic_ *text* with \_underscore\_ or \*single asterisk\*</span></span>
- <span data-ttu-id="f72b6-123">`highlighted as code`백쿼트를 사용하여 문장 내의 텍스트 \`\`</span><span class="sxs-lookup"><span data-stu-id="f72b6-123">Text `highlighted as code` within a sentence \`using backquotes\`</span></span>
- <span data-ttu-id="f72b6-124">문서 페이지 [MRTK 설명서 지침에](documentation-guide.md) 대한 링크</span><span class="sxs-lookup"><span data-stu-id="f72b6-124">Links to docs pages [MRTK documentation guidelines](documentation-guide.md)</span></span>
- <span data-ttu-id="f72b6-125">페이지 [내의 앵커에 대한](#style)링크 앵커는 공백을 대시로 대체하고 소문자로 변환하여 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-125">Links to [anchors within a page](#style); anchors are formed by replacing spaces with dashes, and converting to lowercase</span></span>

<span data-ttu-id="f72b6-126">코드 샘플의 경우 세 개의 백틱이 있는 블록을 사용하고 \` \` \` 구문 강조 표시를 위한 언어로 *csharp를* 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-126">For code samples we use the blocks with three backticks \`\`\` and specify *csharp* as the language for syntax highlighting:</span></span>

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

<span data-ttu-id="f72b6-127">문장 내의 코드를 언급하는 경우 `use a single backtick`</span><span class="sxs-lookup"><span data-stu-id="f72b6-127">When mentioning code within a sentence `use a single backtick`.</span></span>

### <a name="todos"></a><span data-ttu-id="f72b6-128">Todos</span><span class="sxs-lookup"><span data-stu-id="f72b6-128">TODOs</span></span>

<span data-ttu-id="f72b6-129">시간이 지남에 따라 이러한 TODO(예: 코드 TODO)가 누적되고 업데이트 방법 및 손실 이유에 대한 정보가 누적되는 경향이 있기 때문에 문서에서 TODO를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f72b6-129">Avoid using TODOs in docs, as over time these TODOs (like code TODOs) tend to accumulate and information about how they should be updated and why gets lost.</span></span>

<span data-ttu-id="f72b6-130">TODO를 추가해야 하는 경우 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-130">If it is absolutely necessary to add a TODO, follow these steps:</span></span>

1. <span data-ttu-id="f72b6-131">TODO의 컨텍스트를 설명하는 새 문제를 Github에 제출하고 다른 참가자가 TODO를 이해하고 해결할 수 있는 충분한 배경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-131">File a new issue on Github describing the context behind the TODO, and provide enough background that another contributor would be able to understand and then address the TODO.</span></span>
2. <span data-ttu-id="f72b6-132">문서의 할 일에서 문제 URL을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-132">Reference the issue URL in the todo in the docs.</span></span>

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a><span data-ttu-id="f72b6-133">강조 표시된 섹션</span><span class="sxs-lookup"><span data-stu-id="f72b6-133">Highlighted sections</span></span>

<span data-ttu-id="f72b6-134">판독기에서 특정 점을 강조 표시하려면 , 및 를 사용하여 *> [!NOTE]* *> [!WARNING]* 다음 스타일을 *> [!IMPORTANT]* 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-134">To highlight specific points to the reader, use *> [!NOTE]* , *> [!WARNING]* , and *> [!IMPORTANT]* to produce the following styles.</span></span> <span data-ttu-id="f72b6-135">일반적인 사항에 대한 참고 사항 및 특수 관련 사례에 대해서만 경고/중요 지점을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-135">It is recommended to use notes for general points and warning/important points only for special relevant cases.</span></span>

> [!NOTE]
> <span data-ttu-id="f72b6-136">참고 예제</span><span class="sxs-lookup"><span data-stu-id="f72b6-136">Example of a note</span></span>

> [!WARNING]
> <span data-ttu-id="f72b6-137">경고의 예</span><span class="sxs-lookup"><span data-stu-id="f72b6-137">Example of a warning</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f72b6-138">중요한 주석의 예</span><span class="sxs-lookup"><span data-stu-id="f72b6-138">Example of an important comment</span></span>

## <a name="page-layout"></a><span data-ttu-id="f72b6-139">페이지 레이아웃</span><span class="sxs-lookup"><span data-stu-id="f72b6-139">Page layout</span></span>

### <a name="introduction"></a><span data-ttu-id="f72b6-140">소개</span><span class="sxs-lookup"><span data-stu-id="f72b6-140">Introduction</span></span>

<span data-ttu-id="f72b6-141">주 챕터 제목 바로 뒤의 부분은 챕터의 내용을 간단히 소개하는 역할을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-141">The part right after the main chapter title should serve as a short introduction what the chapter is about.</span></span> <span data-ttu-id="f72b6-142">이 작업을 너무 오래 수행하지 말고, 하위 자막을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-142">Do not make this too long, instead add sub headlines.</span></span> <span data-ttu-id="f72b6-143">이렇게 하면 섹션에 연결할 수 있으며 책갈피로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-143">These allow to link to sections and can be saved as bookmarks.</span></span>

### <a name="main-body"></a><span data-ttu-id="f72b6-144">본문</span><span class="sxs-lookup"><span data-stu-id="f72b6-144">Main body</span></span>

<span data-ttu-id="f72b6-145">나머지를 구조화하려면 2단계 및 3단계 재구성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-145">Use two-level and three-level headlines to structure the rest.</span></span>

<span data-ttu-id="f72b6-146">**미니 섹션**</span><span class="sxs-lookup"><span data-stu-id="f72b6-146">**Mini Sections**</span></span>

<span data-ttu-id="f72b6-147">눈에 띄어야 하는 블록에 대해 굵은 텍스트 줄을 사용합니다. 어느 시점에서는 이를 4개 수준의 뉴스로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-147">Use a bold line of text for blocks that should stand out. We might replace this by four-level headlines at some point.</span></span>

### <a name="see-also-section"></a><span data-ttu-id="f72b6-148">' 참고 항목 ' 섹션</span><span class="sxs-lookup"><span data-stu-id="f72b6-148">'See also' section</span></span>

<span data-ttu-id="f72b6-149">대부분의 페이지 *는 라는 챕터* 로 끝나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-149">Most pages should end with a chapter called *See also*.</span></span> <span data-ttu-id="f72b6-150">이 장에서는이 항목과 관련 된 페이지에 대 한 링크를 가리키는 글머리 기호 목록 일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-150">This chapter is simply a bullet pointed list of links to pages related to this topic.</span></span> <span data-ttu-id="f72b6-151">이러한 링크는 페이지 텍스트 내에 해당 하는 경우에도 나타날 수 있지만 반드시 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-151">These links may also appear within the page text where appropriate, but this is not required.</span></span> <span data-ttu-id="f72b6-152">마찬가지로 페이지 텍스트에는 주 항목과 관련이 없는 페이지에 대 한 링크가 포함 되어 있을 수 있습니다. *참고* 항목 목록에 포함 되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-152">Similarly, the page text may contain links to pages that are not related to the main topic, these should not be included in the *See also* list.</span></span> <span data-ttu-id="f72b6-153">링크를 선택 하는 방법에 대 한 예제는 [이 페이지의 '](#see-also) ' 참고 ' 단원을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f72b6-153">See [this page's ''See also'' chapter](#see-also) as an example for the choice of links.</span></span>

## <a name="table-of-contents-toc"></a><span data-ttu-id="f72b6-154">목차 (TOC)</span><span class="sxs-lookup"><span data-stu-id="f72b6-154">Table of Contents (TOC)</span></span>

<span data-ttu-id="f72b6-155">Toc 파일은 MRTK github.io 설명서에서 탐색 모음을 생성 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-155">Toc files are used for generating the navigation bars in the MRTK github.io documentation.</span></span>
<span data-ttu-id="f72b6-156">새 문서 파일이 추가 될 때마다 문서 폴더의 toc. yml 파일 중 하나에 해당 파일에 대 한 항목이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-156">Whenever a new documentation file is added, make sure that there's an entry for that file in one of the toc.yml files of the documentation folder.</span></span> <span data-ttu-id="f72b6-157">Toc 파일에 나열 된 문서만 개발자 문서 탐색에 표시 됩니다. 문서 폴더의 모든 하위 폴더에 대 한 toc 파일이 있을 수 있습니다 .이 파일은 기존 toc 파일에 연결 하 여 탐색의 해당 부분에 하위 섹션으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-157">Only articles listed in the toc files will show up in the navigation of the developer docs. There can be a toc file for every subfolder in the documentation folder which can be linked into any existing toc file to add it as a subsection to the corresponding part of the navigation.</span></span>

## <a name="style"></a><span data-ttu-id="f72b6-158">스타일</span><span class="sxs-lookup"><span data-stu-id="f72b6-158">Style</span></span>

### <a name="writing-style"></a><span data-ttu-id="f72b6-159">쓰기 스타일</span><span class="sxs-lookup"><span data-stu-id="f72b6-159">Writing style</span></span>

<span data-ttu-id="f72b6-160">일반적인 경험: **전문 전문가** 에 게 해보세요.</span><span class="sxs-lookup"><span data-stu-id="f72b6-160">General rule of thumb: Try to **sound professional**.</span></span> <span data-ttu-id="f72b6-161">이는 일반적으로 ' 대화형 톤 '을 방지 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-161">That usually means to avoid a 'conversational tone'.</span></span> <span data-ttu-id="f72b6-162">또한 hyperbole 및 sensationalism을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-162">Also try to avoid hyperbole and sensationalism.</span></span>

1. <span data-ttu-id="f72b6-163">지나치게 재미 않게 해보세요.</span><span class="sxs-lookup"><span data-stu-id="f72b6-163">Don't try to be (overly) funny.</span></span>
2. <span data-ttu-id="f72b6-164">' I '를 쓰지 않음</span><span class="sxs-lookup"><span data-stu-id="f72b6-164">Never write 'I'</span></span>
3. <span data-ttu-id="f72b6-165">' Microsoft '를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="f72b6-165">Avoid 'we'.</span></span> <span data-ttu-id="f72b6-166">이는 일반적으로 ' MRTK '를 대신 사용 하 여 쉽게 rephrased 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-166">This can usually be rephrased easily, using 'MRTK' instead.</span></span> <span data-ttu-id="f72b6-167">예: "이 기능을 지원 합니다."-> "MRTK는이 기능을 지원 합니다." 또는 "다음 기능이 지원 됩니다."</span><span class="sxs-lookup"><span data-stu-id="f72b6-167">Example: "we support this feature" -> "MRTK supports this feature" or "the following features are supported ...".</span></span>
4. <span data-ttu-id="f72b6-168">마찬가지로 ' 사용자 '를 방지 해 보세요.</span><span class="sxs-lookup"><span data-stu-id="f72b6-168">Similarly, try to avoid 'you'.</span></span> <span data-ttu-id="f72b6-169">예: "이 간단한 변경을 사용 하면 셰이더가 구성 가능 합니다."</span><span class="sxs-lookup"><span data-stu-id="f72b6-169">Example: "With this simple change your shader becomes configurable!"</span></span> <span data-ttu-id="f72b6-170">-> "셰이더를 적은 노력으로 구성할 수 있습니다."</span><span class="sxs-lookup"><span data-stu-id="f72b6-170">-> "Shaders can be made configurable with little effort."</span></span>
5. <span data-ttu-id="f72b6-171">'sloppy phrases'를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f72b6-171">Do not use 'sloppy phrases'.</span></span>
6. <span data-ttu-id="f72b6-172">지나치게 기대한 소리를 방지합니다. 아무것도 판매할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-172">Avoid sounding overly excited, we do not need to sell anything.</span></span>
7. <span data-ttu-id="f72b6-173">마찬가지로 지나치게 크게 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f72b6-173">Similarly, avoid being overly dramatic.</span></span> <span data-ttu-id="f72b6-174">느낌표는 거의 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-174">Exclamation marks are rarely needed.</span></span>

### <a name="capitalization"></a><span data-ttu-id="f72b6-175">대문자 표시</span><span class="sxs-lookup"><span data-stu-id="f72b6-175">Capitalization</span></span>

- <span data-ttu-id="f72b6-176">**제목에 문장 대/소문자를** 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-176">Use **Sentence case for headlines**.</span></span> <span data-ttu-id="f72b6-177">Ie.</span><span class="sxs-lookup"><span data-stu-id="f72b6-177">Ie.</span></span> <span data-ttu-id="f72b6-178">첫 글자와 이름을 대문자로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-178">capitalize the first letter and names, but nothing else.</span></span>
- <span data-ttu-id="f72b6-179">다른 모든 경우 일반 영어를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-179">Use regular English for everything else.</span></span> <span data-ttu-id="f72b6-180">즉, 해당 컨텍스트에서 특별한 의미를 가진 경우에도 **임의의 단어를 대문자로** 대문자로 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-180">That means **do not capitalize arbitrary words**, even if they hold a special meaning in that context.</span></span> <span data-ttu-id="f72b6-181">특정 단어를 강조 표시하기 위해 *italic text를* [선호합니다. 아래를 참조하세요.](#emphasis-and-highlighting)</span><span class="sxs-lookup"><span data-stu-id="f72b6-181">Prefer *italic text* for highlighting certain words, [see below](#emphasis-and-highlighting).</span></span>
- <span data-ttu-id="f72b6-182">링크가 문장에 포함되는 경우(기본 설정 방법) 표준 챕터 이름은 항상 대문자를 사용하므로 텍스트 내에서 임의의 대문자 표시가 없는 규칙을 위반합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-182">When a link is embedded in a sentence (which is the preferred method), the standard chapter name always uses capital letters, thus breaking the rule of no arbitrary capitalization inside text.</span></span> <span data-ttu-id="f72b6-183">따라서 사용자 지정 링크 이름을 사용하여 대문자를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-183">Therefore use a custom link name to fix the capitalization.</span></span> <span data-ttu-id="f72b6-184">예를 들어 경계 [컨트롤](../features/ux-building-blocks/bounds-control.md) 설명서에 대한 링크는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-184">As an example, here is a link to the [bounds control](../features/ux-building-blocks/bounds-control.md) documentation.</span></span>
- <span data-ttu-id="f72b6-185">Unity 와 같은 이름을 대문자로 *지정합니다.*</span><span class="sxs-lookup"><span data-stu-id="f72b6-185">Do capitalize names, such as *Unity*.</span></span>
- <span data-ttu-id="f72b6-186">Unity 편집기 를 작성할 때는 "editor"를 *대문자로* 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f72b6-186">Do NOT capitalize "editor" when writing *Unity editor*.</span></span>

### <a name="emphasis-and-highlighting"></a><span data-ttu-id="f72b6-187">강조 및 강조 표시</span><span class="sxs-lookup"><span data-stu-id="f72b6-187">Emphasis and highlighting</span></span>

<span data-ttu-id="f72b6-188">단어를 강조 표시하거나 강조 표시하여 굵게 만들거나 굵게 만드는 두 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-188">There are two ways to emphasize or highlight words, making them bold or making them italic.</span></span> <span data-ttu-id="f72b6-189">굵은 텍스트의 효과는 **굵은 텍스트가 돋보여지므로** 텍스트 조각을 건너뛰거나 페이지 위로 스크롤하는 동안 쉽게 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-189">The effect of bold text is that **bold text sticks out** and therefore can easily be noticed while skimming a piece of text or even just scrolling over a page.</span></span> <span data-ttu-id="f72b6-190">굵게는 사람들이 기억해야 하는 문구를 강조 표시하기에 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-190">Bold is great to highlight phrases that people should remember.</span></span> <span data-ttu-id="f72b6-191">그러나 일반적으로 방해가 되므로 **굵은 텍스트를 거의 사용하지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-191">However, **use bold text rarely**, because it is generally distracting.</span></span>

<span data-ttu-id="f72b6-192">일반적으로는 특별 한 의미가 있기 때문에 논리적으로 함께 속하거나 특정 용어를 강조 표시 하는 ' 그룹 ' 중 하나를 원합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-192">Often one wants to either 'group' something that belongs logically together or highlight a specific term, because it has a special meaning.</span></span> <span data-ttu-id="f72b6-193">이러한 작업은 전체 텍스트를 제거할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-193">Such things do not need to stand out of the overall text.</span></span> <span data-ttu-id="f72b6-194">기울임꼴 텍스트를 *간단한 방법* 으로 사용 하 여 항목을 강조 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-194">Use italic text as a *lightweight method* to highlight something.</span></span>

<span data-ttu-id="f72b6-195">마찬가지로, 파일 이름, 경로 또는 메뉴 항목이 텍스트에서 언급 되는 경우에는이를 사용 하 여 논리적으로 그룹화 하는 것이 혼란을 주지 않도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-195">Similarly, when a filename, a path or a menu-entry is mentioned in text, prefer to make it italic to logically group it, without being distracting.</span></span>

<span data-ttu-id="f72b6-196">일반적으로 **불필요 한 텍스트 강조 표시를 방지** 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-196">In general, try to **avoid unnecessary text highlighting**.</span></span> <span data-ttu-id="f72b6-197">특수 용어는 판독기를 인식 하기 위해 한 번 강조 표시 될 수 있으며, 더 이상 사용 되지 않고 distracts만 제공 되는 경우 텍스트 전체에서 강조 표시를 반복 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-197">Special terms can be highlighted once to make the reader aware, do not repeat such highlighting throughout the text, when it serves no purpose anymore and only distracts.</span></span>

### <a name="mentioning-menu-entries"></a><span data-ttu-id="f72b6-198">메뉴 항목을 언급 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-198">Mentioning menu entries</span></span>

<span data-ttu-id="f72b6-199">사용자가 클릭 해야 하는 메뉴 항목을 언급할 때 현재 규칙은 *프로젝트 > 파일 > > 리프 만들기* 입니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-199">When mentioning a menu entry that a user should click, the current convention is: *Project > Files > Create > Leaf*</span></span>

### <a name="links"></a><span data-ttu-id="f72b6-200">링크</span><span class="sxs-lookup"><span data-stu-id="f72b6-200">Links</span></span>

<span data-ttu-id="f72b6-201">가능한 한 많은 유용한 링크를 다른 페이지에 삽입 하 고 각 링크는 한 번만 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-201">Insert as many useful links to other pages as possible, but each link only once.</span></span> <span data-ttu-id="f72b6-202">페이지가 페이지의 모든 링크를 클릭 하는 것으로 가정 하 고, 동일한 페이지가 20 번 열리는 경우 얼마나 방해가 될 수 있는지 생각해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="f72b6-202">Assume a reader clicks on every link in the page, and think about how annoying it would be, if the same page opens 20 times.</span></span>

<span data-ttu-id="f72b6-203">문장에 포함 된 링크를 선호 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-203">Prefer links embedded in a sentence:</span></span>

- <span data-ttu-id="f72b6-204">잘못 됨: 지침이 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-204">BAD: Guidelines are useful.</span></span> <span data-ttu-id="f72b6-205">자세한 내용은 [이 챕터](../contributing/documentation-guide.md) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f72b6-205">See [this chapter](../contributing/documentation-guide.md) for details.</span></span>
- <span data-ttu-id="f72b6-206">양호: [지침이](documentation-guide.md) 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-206">GOOD: [Guidelines](documentation-guide.md) are useful.</span></span>

<span data-ttu-id="f72b6-207">외부 링크를 사용 하지 않으면 오래 된 링크를 사용 하지 않거나 저작권 콘텐츠를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-207">Avoid external links, they can become outdated or contain copyrighted content.</span></span>

<span data-ttu-id="f72b6-208">링크를 추가 하는 경우 링크를 [참고](#see-also) 항목 섹션에도 표시 해야 하는지 여부를 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-208">When adding a link, consider whether it should also be listed in the [See also](#see-also) section.</span></span> <span data-ttu-id="f72b6-209">마찬가지로, 새 페이지에 대 한 링크를 연결 된 페이지에 추가할지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-209">Similarly, check whether a link to the new page should be added to the linked-to page.</span></span>

### <a name="images--screenshots"></a><span data-ttu-id="f72b6-210">이미지/스크린샷</span><span class="sxs-lookup"><span data-stu-id="f72b6-210">Images / screenshots</span></span>

<span data-ttu-id="f72b6-211">**스크린샷만 사용 합니다.**</span><span class="sxs-lookup"><span data-stu-id="f72b6-211">**Use screenshots sparingly.**</span></span> <span data-ttu-id="f72b6-212">설명서에서 이미지를 유지 관리 하는 작업은 많은 작업 이며 작은 UI를 변경 하면 더 많은 스크린샷을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-212">Maintaining images in documentation is a lot of work, small UI changes can make a lot of screenshots outdated.</span></span> <span data-ttu-id="f72b6-213">다음 규칙은 유지 관리 노력을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-213">The following rules will reduce maintenance effort:</span></span>

1. <span data-ttu-id="f72b6-214">텍스트로 설명할 수 있는 스크린샷은 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f72b6-214">Do not use screenshots for things that can be described in text.</span></span> <span data-ttu-id="f72b6-215">특히 속성 이름 및 값을 표시하기 위한 목적으로만 **속성 표를 스크린샷으로 표시하면 안됩니다.**</span><span class="sxs-lookup"><span data-stu-id="f72b6-215">Especially, **never screenshot a property grid** for the sole purpose of showing property names and values.</span></span>
2. <span data-ttu-id="f72b6-216">스크린샷에 표시된 내용과 관련이 없는 내용을 포함하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f72b6-216">Do not include things in a screenshot that are irrelevant to what is shown.</span></span> <span data-ttu-id="f72b6-217">예를 들어 렌더링 효과가 표시되면 뷰포트의 스크린샷을 만들되 주위의 UI는 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-217">For instance, when a rendering effect is shown, make a screenshot of the viewport, but exclude any UI around it.</span></span> <span data-ttu-id="f72b6-218">일부 UI를 표시하고 해당 중요한 부분만 이미지에 있도록 창을 이동해 보세요.</span><span class="sxs-lookup"><span data-stu-id="f72b6-218">Showing some UI, try to move windows around such that only that important part is in the image.</span></span>
3. <span data-ttu-id="f72b6-219">스크린샷 UI를 포함하는 경우 중요한 부분만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-219">When including screenshot UI, only show the important parts.</span></span> <span data-ttu-id="f72b6-220">예를 들어 도구 모음의 단추에 대해 말하는 경우 중요한 도구 모음 단추를 표시하는 작은 이미지를 만들지만 그 주위의 모든 것을 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-220">For example, when talking about buttons in a toolbar, make a small image that shows the important toolbar buttons, but exclude everything around it.</span></span>
4. <span data-ttu-id="f72b6-221">재현하기 쉬운 이미지만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-221">Only use images that are easy to reproduce.</span></span> <span data-ttu-id="f72b6-222">즉, 표식 또는 강조 표시를 스크린샷에 그리지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f72b6-222">That means do not paint markers or highlights into screenshots.</span></span> <span data-ttu-id="f72b6-223">첫째, 이러한 규칙의 모양은 일관되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-223">First, there are no consistent rules how these should look, anyway.</span></span> <span data-ttu-id="f72b6-224">둘째, 이러한 스크린샷을 재현하는 것은 추가적인 노력입니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-224">Second, reproducing such a screenshot is additional effort.</span></span> <span data-ttu-id="f72b6-225">대신 텍스트의 중요한 부분을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-225">Instead, describe the important parts in text.</span></span> <span data-ttu-id="f72b6-226">이 규칙에는 예외가 있지만 드문 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-226">There are exceptions to this rule, but they are rare.</span></span>
5. <span data-ttu-id="f72b6-227">물론 애니메이션 GIF를 다시 만들기 위해 훨씬 더 많은 노력을 기울입니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-227">Obviously, it is much more effort to recreate an animated GIF.</span></span> <span data-ttu-id="f72b6-228">시간이 끝날 때까지 다시 만들어야 하거나, 시간을 소비하지 않으려는 경우 사람들이 이 파일을 throw할 것으로 예상합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-228">Expect to be responsible to recreate it until the end of time, or expect people to throw it out, if they don't want to spend that time.</span></span>
6. <span data-ttu-id="f72b6-229">문서의 이미지 수를 낮게 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-229">Keep the number of images in an article low.</span></span> <span data-ttu-id="f72b6-230">종종 모든 것을 보여 주는 일부 도구의 전체 스크린샷을 만들고 나머지를 텍스트로 설명하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-230">Often a good method is to make one overall screenshot of some tool, that shows everything, and then describe the rest in text.</span></span> <span data-ttu-id="f72b6-231">이렇게 하면 필요할 때 스크린샷을 쉽게 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-231">This makes it easy to replace the screenshot when necessary.</span></span>

<span data-ttu-id="f72b6-232">몇 가지 다른 측면은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-232">Some other aspects:</span></span>

- <span data-ttu-id="f72b6-233">스크린샷 용 편집기 UI는 밝은 회색 테마 편집기를 사용 해야 합니다. 모든 사용자가 어두운 테마에 액세스할 수 있는 것은 아니므로 최대한 일관성 있게 유지 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-233">The editor UI for screenshots should use light gray theme editor as not all users have access to the dark theme and we'd like to keep things as consistent as possible.</span></span>
- <span data-ttu-id="f72b6-234">기본 이미지 너비는 대부분의 모니터에 잘 표시 되므로 500 픽셀입니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-234">Default image width is 500 pixels, as this displays well on most monitors.</span></span> <span data-ttu-id="f72b6-235">너무 많이 해 서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-235">Try not to deviate too much from it.</span></span> <span data-ttu-id="f72b6-236">800 픽셀은 최대 너비 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-236">800 pixels width should be the maximum.</span></span>
- <span data-ttu-id="f72b6-237">UI의 스크린샷에 PNGs를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-237">Use PNGs for screenshots of UI.</span></span>
- <span data-ttu-id="f72b6-238">3D 뷰포트 스크린샷에 PNGs 또는 JPGs를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-238">Use PNGs or JPGs for 3D viewport screenshots.</span></span> <span data-ttu-id="f72b6-239">압축 비율 보다 품질을 선호 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-239">Prefer quality over compression ratio.</span></span>

### <a name="list-of-component-properties"></a><span data-ttu-id="f72b6-240">구성 요소 속성 목록</span><span class="sxs-lookup"><span data-stu-id="f72b6-240">List of component properties</span></span>

<span data-ttu-id="f72b6-241">속성 목록을 문서화할 때 굵은 텍스트를 사용 하 여 속성 이름을 강조 표시 한 다음 줄 바꿈 및 일반 텍스트를 사용 하 여 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-241">When documenting a list of properties, use bold text to highlight the property name, then line breaks and regular text to describe them.</span></span> <span data-ttu-id="f72b6-242">하위 장이나 글머리 기호 요소 목록을 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f72b6-242">Do not use sub-chapters or bullet point lists.</span></span>

<span data-ttu-id="f72b6-243">또한 모든 문장을 마침표를 사용 하 여 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-243">Also, don't forget to finish all sentences with a period.</span></span>

## <a name="page-completion-checklist"></a><span data-ttu-id="f72b6-244">페이지 완료 검사 목록</span><span class="sxs-lookup"><span data-stu-id="f72b6-244">Page completion checklist</span></span>

1. <span data-ttu-id="f72b6-245">이 문서의 지침을 준수 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-245">Ensure that this document's guidelines were followed.</span></span>
1. <span data-ttu-id="f72b6-246">문서 구조를 찾아보고 다른 페이지의 [참고](#see-also) 항목 섹션에서 새 문서를 찾을 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-246">Browse the document structure and see if the new document could be mentioned under the [See also](#see-also) section of other pages.</span></span>
1. <span data-ttu-id="f72b6-247">사용할 수 있는 경우 항목 증명에 대 한 지식이 있는 사용자에 게 기술 정확성을 위해 페이지를 읽도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-247">If available, have someone with knowledge of the topic proof-read the page for technical correctness.</span></span>
1. <span data-ttu-id="f72b6-248">스타일 및 서식 지정을 위해 페이지를 증명 하는 사람이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-248">Have someone proof-read the page for style and formatting.</span></span> <span data-ttu-id="f72b6-249">이는 토픽에 익숙하지 않을 수 있습니다. 또한 설명서의 이해를 이해 하는 방법에 대 한 피드백을 얻는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-249">This can be someone unfamiliar with the topic, which is also a good idea to get feedback about how understandable the documentation is.</span></span>

## <a name="source-documentation"></a><span data-ttu-id="f72b6-250">원본 설명서</span><span class="sxs-lookup"><span data-stu-id="f72b6-250">Source documentation</span></span>

<span data-ttu-id="f72b6-251">API 설명서는 MRTK 원본 파일에서 자동으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-251">API documentation will be generated automatically from the MRTK source files.</span></span> <span data-ttu-id="f72b6-252">이를 용이 하 게 하려면 소스 파일이 다음을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-252">To facilitate this, source files are required to contain the following:</span></span>

- [<span data-ttu-id="f72b6-253">클래스, 구조체, 열거형 요약 블록</span><span class="sxs-lookup"><span data-stu-id="f72b6-253">Class, struct, enum summary blocks</span></span>](#class-struct-enum-summary-blocks)
- [<span data-ttu-id="f72b6-254">속성, 메서드, 이벤트 요약 블록</span><span class="sxs-lookup"><span data-stu-id="f72b6-254">Property, method, event summary blocks</span></span>](#property-method-event-summary-blocks)
- [<span data-ttu-id="f72b6-255">기능 소개 버전 및 의존성</span><span class="sxs-lookup"><span data-stu-id="f72b6-255">Feature introduction version and dependencies</span></span>](#feature-introduction-version-and-dependencies)
- [<span data-ttu-id="f72b6-256">직렬화된 필드</span><span class="sxs-lookup"><span data-stu-id="f72b6-256">Serialized fields</span></span>](#serialized-fields)
- [<span data-ttu-id="f72b6-257">열거형 값</span><span class="sxs-lookup"><span data-stu-id="f72b6-257">Enumeration values</span></span>](#enumeration-values)

<span data-ttu-id="f72b6-258">위의 코드 외에도 유지 관리, 버그 수정 및 사용자 지정 용이성을 허용하도록 코드를 잘 주석으로 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-258">In addition to the above, the code should be well commented to allow for maintenance, bug fixes and ease of customization.</span></span>

### <a name="class-struct-enum-summary-blocks"></a><span data-ttu-id="f72b6-259">클래스, 구조체, 열거형 요약 블록</span><span class="sxs-lookup"><span data-stu-id="f72b6-259">Class, struct, enum summary blocks</span></span>

<span data-ttu-id="f72b6-260">클래스, 구조체 또는 열거형이 MRTK에 추가되는 경우 해당 용도를 설명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-260">If a class, struct or enum is being added to the MRTK, its purpose must be described.</span></span> <span data-ttu-id="f72b6-261">이는 클래스 위의 요약 블록 형식을 취합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-261">This is to take the form of a summary block above the class.</span></span>

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

<span data-ttu-id="f72b6-262">클래스 수준 dependencies가 있는 경우 요약 바로 아래의 설명 블록에 문서화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-262">If there are any class level dependencies, they should be documented in a remarks block, immediately below the summary.</span></span>

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

<span data-ttu-id="f72b6-263">클래스, 구조체 또는 열거형에 대한 요약 없이 제출된 끌어오기 요청은 승인되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-263">Pull Requests submitted without summaries for classes, structures or enums will not be approved.</span></span>

### <a name="property-method-event-summary-blocks"></a><span data-ttu-id="f72b6-264">속성, 메서드, 이벤트 요약 블록</span><span class="sxs-lookup"><span data-stu-id="f72b6-264">Property, method, event summary blocks</span></span>

<span data-ttu-id="f72b6-265">속성, 메서드 및 이벤트(PMEs) 및 필드는 코드 표시 유형(퍼블릭, 프라이빗, 보호 및 내부)에 관계없이 요약 블록으로 문서화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-265">Properties, methods and events (PMEs) as well as fields are to be documented with summary blocks, regardless of code visibility (public, private, protected and internal).</span></span> <span data-ttu-id="f72b6-266">설명서 생성 도구는 퍼블릭 및 보호된 기능만 필터링하고 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-266">The documentation generation tool is responsible for filtering out and publishing only the public and protected features.</span></span>

<span data-ttu-id="f72b6-267">참고: Unity 메서드에는  요약 블록이 필요하지 않습니다(예: 각성, 시작, 업데이트).</span><span class="sxs-lookup"><span data-stu-id="f72b6-267">NOTE: A summary block is **not** required for Unity methods (ex: Awake, Start, Update).</span></span>

<span data-ttu-id="f72b6-268">끌어오기 요청을 승인하려면 PME 설명서가 **필요합니다.**</span><span class="sxs-lookup"><span data-stu-id="f72b6-268">PME documentation is **required** for a pull request to be approved.</span></span>

<span data-ttu-id="f72b6-269">PME 요약 블록의 일부로 매개 변수 및 반환된 데이터의 의미와 목적이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-269">As part of a PME summary block, the meaning and purpose of parameters and returned data is required.</span></span>

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a><span data-ttu-id="f72b6-270">기능 소개 버전 및 의존성</span><span class="sxs-lookup"><span data-stu-id="f72b6-270">Feature introduction version and dependencies</span></span>

<span data-ttu-id="f72b6-271">API 요약 설명서의 일부로 기능이 도입된 MRTK 버전 및 모든 의존성 관련 정보를 설명 블록에 문서화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-271">As part of the API summary documentation, information regarding the MRTK version in which the feature was introduced and any dependencies should be documented in a remarks block.</span></span>

<span data-ttu-id="f72b6-272">종속성 확장 및/또는 플랫폼 종속성 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-272">Dependencies should include extension and/or platform dependencies.</span></span>

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a><span data-ttu-id="f72b6-273">Serialize 된 필드</span><span class="sxs-lookup"><span data-stu-id="f72b6-273">Serialized fields</span></span>

<span data-ttu-id="f72b6-274">Unity의 tooltip 특성을 사용 하 여 검사기에서 스크립트의 필드에 대 한 런타임 설명서를 제공 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-274">It is a good practice to use Unity's tooltip attribute to provide runtime documentation for a script's fields in the inspector.</span></span>

<span data-ttu-id="f72b6-275">구성 옵션이 API 설명서에 포함 되도록 하기 위해 스크립트는 *최소한* 요약 블록에 도구 설명 내용을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-275">So that configuration options are included in the API documentation, scripts are required to include *at least* the tooltip contents in a summary block.</span></span>

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a><span data-ttu-id="f72b6-276">열거형 값</span><span class="sxs-lookup"><span data-stu-id="f72b6-276">Enumeration values</span></span>

<span data-ttu-id="f72b6-277">및 열거형을 정의 하는 경우 코드 에서도 요약 블록을 사용 하 여 열거형 값의 의미를 문서화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-277">When defining and enumeration, code must also document the meaning of the enum values using a summary block.</span></span> <span data-ttu-id="f72b6-278">설명 블록을 사용 하 여 추가 정보를 제공 하 여 이해를 향상할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-278">Remarks blocks can optionally be used to provide additional details to enhance understanding.</span></span>

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a><span data-ttu-id="f72b6-279">방법 설명서</span><span class="sxs-lookup"><span data-stu-id="f72b6-279">How-to documentation</span></span>

<span data-ttu-id="f72b6-280">혼합 현실 도구 키트의 많은 사용자는 API 설명서를 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-280">Many users of the Mixed Reality Toolkit may not need to use the API documentation.</span></span> <span data-ttu-id="f72b6-281">이러한 사용자는 미리 만들어진 재사용 가능한 prefabs 및 스크립트를 활용 하 여 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-281">These users will take advantage of our pre-made, reusable prefabs and scripts to create their experiences.</span></span>

<span data-ttu-id="f72b6-282">각 기능 영역에는 매우 높은 수준에서 설명 하는 하나 이상의 markdown (md) 파일이 포함 됩니다. 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-282">Each feature area will contain one or more markdown (.md) files that describe at a fairly high level, what is provided.</span></span> <span data-ttu-id="f72b6-283">지정 된 기능 영역의 크기 및/또는 복잡도에 따라 제공 된 기능별로 하나의 추가 파일이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-283">Depending on the size and/or complexity of a given feature area, there may be a need for additional files, up to one per feature provided.</span></span>

<span data-ttu-id="f72b6-284">기능이 추가 되거나 사용이 변경 되 면 개요 설명서를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-284">When a feature is added (or the usage is changed), overview documentation must be provided.</span></span>

<span data-ttu-id="f72b6-285">이 설명서의 일부로, 자습서를 비롯 한 방법 섹션을 참조 하 여 시작 하는 기능 또는 개념에 대 한 새로운 고객을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-285">As part of this documentation, how-to sections, including illustrations, should be provided to assist customers new to a feature or concept in getting started.</span></span>

## <a name="design-documentation"></a><span data-ttu-id="f72b6-286">디자인 설명서</span><span class="sxs-lookup"><span data-stu-id="f72b6-286">Design documentation</span></span>

<span data-ttu-id="f72b6-287">혼합 현실은 완전히 새로운 세계를 만들 수 있는 기회를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-287">Mixed Reality provides an opportunity to create entirely new worlds.</span></span> <span data-ttu-id="f72b6-288">이 부분에는 MRTK에서 사용할 사용자 지정 자산을 만드는 작업이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-288">Part of this is likely to involve the creation of custom assets for use with the MRTK.</span></span> <span data-ttu-id="f72b6-289">이를 가능한 한 고객에 게 무료로 제공 하기 위해 구성 요소는 아트 자산의 서식 또는 기타 요구 사항을 설명 하는 디자인 설명서를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-289">To make this as friction free as possible for customers, components should provide design documentation describing any formatting or other requirements for art assets.</span></span>

<span data-ttu-id="f72b6-290">디자인 설명서가 유용할 수 있는 몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-290">Some examples where design documentation can be helpful:</span></span>

- <span data-ttu-id="f72b6-291">커서 모델</span><span class="sxs-lookup"><span data-stu-id="f72b6-291">Cursor models</span></span>
- <span data-ttu-id="f72b6-292">공간 매핑 시각화</span><span class="sxs-lookup"><span data-stu-id="f72b6-292">Spatial mapping visualizations</span></span>
- <span data-ttu-id="f72b6-293">음향 효과 파일</span><span class="sxs-lookup"><span data-stu-id="f72b6-293">Sound effect files</span></span>

<span data-ttu-id="f72b6-294">이러한 유형의 설명서 **는 권장 되며** , 끌어오기 요청 검토의 일환으로 요청 될 수 **있습니다** .</span><span class="sxs-lookup"><span data-stu-id="f72b6-294">This type of documentation is **strongly** recommended, and **may** be requested as part of a pull request review.</span></span>

<span data-ttu-id="f72b6-295">이는 [MS Developer 사이트](/windows/mixed-reality/design) 의 디자인 권장 사항과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-295">This may or may not be different from the design recommendation on the [MS Developer site](/windows/mixed-reality/design)</span></span>

## <a name="performance-notes"></a><span data-ttu-id="f72b6-296">성능 정보</span><span class="sxs-lookup"><span data-stu-id="f72b6-296">Performance notes</span></span>

<span data-ttu-id="f72b6-297">일부 중요 한 기능은 성능 비용으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-297">Some important features come at a performance cost.</span></span> <span data-ttu-id="f72b6-298">일반적으로이 코드는 구성 방법에 따라 크게 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-298">Often this code will very depending how they are configured.</span></span>

<span data-ttu-id="f72b6-299">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-299">For example:</span></span>

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

<span data-ttu-id="f72b6-300">성능 정보는 CPU 및/또는 GPU 사용량이 많은 구성 요소에 권장 되며, 끌어오기 요청 검토의 일부로 요청 될 **수 있습니다** .</span><span class="sxs-lookup"><span data-stu-id="f72b6-300">Performance notes are recommended for CPU and/or GPU heavy components and **may** be requested as part of a pull request review.</span></span> <span data-ttu-id="f72b6-301">모든 해당 성능 정보는 API **및** 개요 설명서에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-301">Any applicable performance notes are to be included in API **and** overview documentation.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="f72b6-302">주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="f72b6-302">Breaking changes</span></span>

<span data-ttu-id="f72b6-303">주요 변경 내용 설명서는 각 기능 영역의 개별 breaking-changes.md 연결 되는 최상위 수준 [파일로](../contributing/breaking-changes.md) 구성 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-303">Breaking changes documentation is to consist of a top level [file](../contributing/breaking-changes.md) which links to each feature area's individual breaking-changes.md.</span></span>

<span data-ttu-id="f72b6-304">기능 영역 breaking-changes.md 파일은 지정 된 릴리스에 대해 알려진 모든 주요 변경 내용 목록과 **이전 릴리스의 주요** 변경 내용에 대 한 기록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-304">The feature area breaking-changes.md files are to contain the list of all known breaking changes for a given release **as well as** the history of breaking changes from past releases.</span></span>

<span data-ttu-id="f72b6-305">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-305">For example:</span></span>

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

<span data-ttu-id="f72b6-306">기능 수준 breaking-changes.md 파일에 포함 된 정보는 각각의 새 MRTK 릴리스에 대 한 릴리스 정보로 집계 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-306">The information contained within the feature level breaking-changes.md files will be aggregated to the release notes for each new MRTK release.</span></span>

<span data-ttu-id="f72b6-307">변경의 일부인 주요 변경 내용은 끌어오기 요청의 일부로 문서화 되어야 **합니다** .</span><span class="sxs-lookup"><span data-stu-id="f72b6-307">Any breaking changes that are part of a change **must** be documented as part of a Pull Request.</span></span>

## <a name="tools-for-editing-markdown"></a><span data-ttu-id="f72b6-308">MarkDown 편집 도구</span><span class="sxs-lookup"><span data-stu-id="f72b6-308">Tools for editing MarkDown</span></span>

<span data-ttu-id="f72b6-309">[Visual Studio Code](https://code.visualstudio.com/) 은 MRTK 설명서의 일부인 markdown 파일을 편집 하는 데 유용한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-309">[Visual Studio Code](https://code.visualstudio.com/) is a great tool for editing markdown files that are part of MRTK's documentation.</span></span>

<span data-ttu-id="f72b6-310">설명서를 작성할 때는 다음 두 가지 확장을 설치 하는 것도 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-310">When writing documentation, installing the following two extensions is also highly recommended:</span></span>

- <span data-ttu-id="f72b6-311">Visual Studio Code 용 docs Markdown 확장-Alt + M을 사용 하 여 docs 제작 옵션 메뉴를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-311">Docs Markdown Extension for Visual Studio Code - Use Alt+M to bring up a menu of docs authoring options.</span></span>

- <span data-ttu-id="f72b6-312">코드 맞춤법 검사기-철자가 잘못 된 단어에는 밑줄이 그어집니다. 철자가 잘못 된 단어를 마우스 오른쪽 단추로 클릭 하 여 변경 하거나 사전에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-312">Code Spell Checker - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>

<span data-ttu-id="f72b6-313">이러한 두 가지 모두 Microsoft 게시 된 문서 작성 팩에 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f72b6-313">Both of these come packaged in the Microsoft published Docs Authoring Pack.</span></span>

## <a name="see-also"></a><span data-ttu-id="f72b6-314">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f72b6-314">See also</span></span> 

* [<span data-ttu-id="f72b6-315">예제 링크</span><span class="sxs-lookup"><span data-stu-id="f72b6-315">Example link</span></span>](https://www.google.com)