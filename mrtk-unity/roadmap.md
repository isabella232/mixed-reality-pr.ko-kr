---
title: 로드맵
description: MRTK의 로드맵을 설명하는 설명서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 7385d516e986c1602ad59e2825aa6d1262504727
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175587"
---
# <a name="roadmap"></a><span data-ttu-id="29e68-104">로드맵</span><span class="sxs-lookup"><span data-stu-id="29e68-104">Roadmap</span></span>

<span data-ttu-id="29e68-105">이 문서에서는 Mixed Reality Toolkit 로드맵을 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-105">This document outlines the roadmap of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="29e68-106">다음은 개발 중인 작업을 반영하고 대상 날짜는 예상치를 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-106">Please note that the following reflects work that is in development and target dates reflect estimates.</span></span>

## <a name="current-release"></a><span data-ttu-id="29e68-107">현재 릴리스</span><span class="sxs-lookup"><span data-stu-id="29e68-107">Current release</span></span>

<span data-ttu-id="29e68-108">Microsoft Mixed Reality Toolkit v2.6</span><span class="sxs-lookup"><span data-stu-id="29e68-108">Microsoft Mixed Reality Toolkit v2.6</span></span>

## <a name="upcoming-releases"></a><span data-ttu-id="29e68-109">예정된 릴리스</span><span class="sxs-lookup"><span data-stu-id="29e68-109">Upcoming releases</span></span>

| <span data-ttu-id="29e68-110">제품</span><span class="sxs-lookup"><span data-stu-id="29e68-110">Product</span></span> | <span data-ttu-id="29e68-111">Description</span><span class="sxs-lookup"><span data-stu-id="29e68-111">Description</span></span> | <span data-ttu-id="29e68-112">타임라인</span><span class="sxs-lookup"><span data-stu-id="29e68-112">Timeline</span></span> | <span data-ttu-id="29e68-113">Project 보드</span><span class="sxs-lookup"><span data-stu-id="29e68-113">Project board</span></span> |
| --- | --- | --- | --- |
| [<span data-ttu-id="29e68-114">MRTK V2.7</span><span class="sxs-lookup"><span data-stu-id="29e68-114">MRTK V2.7</span></span>](#270) | <span data-ttu-id="29e68-115">MRTK의 다음 반복</span><span class="sxs-lookup"><span data-stu-id="29e68-115">Next iteration of MRTK</span></span> | <span data-ttu-id="29e68-116">2021년 5월</span><span class="sxs-lookup"><span data-stu-id="29e68-116">May 2021</span></span> | https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14 |

<span data-ttu-id="29e68-117">릴리스는 테마(예: 큰 기능 영역)를 중심으로 하며 약 8~12주마다 발생하도록 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-117">Releases are centered around themes (ex: large feature areas) and are scheduled to occur approximately every 8-12 weeks.</span></span>

<span data-ttu-id="29e68-118">백로그 항목을 포함한 릴리스 세부 정보는 [GitHub 마일스톤 페이지에서](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones)찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-118">Release details, including backlog items, can be found on the [GitHub milestone pages](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones).</span></span> <span data-ttu-id="29e68-119">열려 있는 문제의 전체 집합은 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)에서 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-119">The complete set of open issues can also be found on [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a><span data-ttu-id="29e68-120">MRTK(Mixed Reality Toolkit) 로드맵</span><span class="sxs-lookup"><span data-stu-id="29e68-120">Mixed Reality Toolkit (MRTK) roadmap</span></span>

<span data-ttu-id="29e68-121">이 Mixed Reality Toolkit 의도적으로 MR/AR/VR/XR 플랫폼 간을 위해 빌드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-121">The Mixed Reality Toolkit is built to be cross MR/AR/VR/XR platform by design.</span></span> <span data-ttu-id="29e68-122">도구 키트는 현재 Unity 2019.4.x 및 Unity 2018.4.x를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-122">The toolkit currently supports Unity 2019.4.x and Unity 2018.4.x.</span></span>

> <span data-ttu-id="29e68-123">Unity에서 LTS(장기 지원) 제품을 릴리스하면 Mixed Reality Toolkit LTS 릴리스로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-123">When Unity releases an LTS (Long Term Support) product, the Mixed Reality Toolkit will update to the LTS release.</span></span> <span data-ttu-id="29e68-124">Mixed Reality Toolkit Unity의 최신 비 베타(예: 2020.1) 기술 분기 버전에서 실행되지만 공식적으로 지원되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-124">Although the Mixed Reality Toolkit runs on the latest non-beta (ex: 2020.1) tech branch version of Unity, it is not officially supported.</span></span>

### <a name="270"></a><span data-ttu-id="29e68-125">2.7.0</span><span class="sxs-lookup"><span data-stu-id="29e68-125">2.7.0</span></span>

<span data-ttu-id="29e68-126">현재 2.7.0 릴리스를 계획하고 있으며 곧 더 많은 업데이트가 제공될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-126">We are currently planning the 2.7.0 release and will have more updates for you soon!</span></span>
<span data-ttu-id="29e68-127">릴리스의 최신 상태는 [마일스톤 페이지](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14)를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="29e68-127">For the latest status of the release, please visit the [milestone page](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).</span></span>

<span data-ttu-id="29e68-128">상태: 계획</span><span class="sxs-lookup"><span data-stu-id="29e68-128">Status: Planning</span></span>

<span data-ttu-id="29e68-129">대상 타임라인: 2021년 5월</span><span class="sxs-lookup"><span data-stu-id="29e68-129">Target Timeline: May 2021</span></span>

<span data-ttu-id="29e68-130">테마:</span><span class="sxs-lookup"><span data-stu-id="29e68-130">Themes:</span></span>

- <span data-ttu-id="29e68-131">안정성</span><span class="sxs-lookup"><span data-stu-id="29e68-131">Stability</span></span> 
- <span data-ttu-id="29e68-132">플랫폼 확장: OpenXR</span><span class="sxs-lookup"><span data-stu-id="29e68-132">Platform Expansion: OpenXR</span></span>
- <span data-ttu-id="29e68-133">사용자 환경</span><span class="sxs-lookup"><span data-stu-id="29e68-133">User Experience</span></span>
- <span data-ttu-id="29e68-134">개발자 교육</span><span class="sxs-lookup"><span data-stu-id="29e68-134">Developer Education</span></span>
- <span data-ttu-id="29e68-135">패키징</span><span class="sxs-lookup"><span data-stu-id="29e68-135">Packaging</span></span>

<span data-ttu-id="29e68-136">**안정성**</span><span class="sxs-lookup"><span data-stu-id="29e68-136">**Stability**</span></span>

<span data-ttu-id="29e68-137">품질 및 안정성은 이 릴리스와 모든 Microsoft Mixed Reality Toolkit 릴리스의 최우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-137">Quality and stability are the top priority for this and all Microsoft Mixed Reality Toolkit releases.</span></span> <span data-ttu-id="29e68-138">MRTK 구성 요소의 안정성에 영향을 주는 고객 및 파트너 문제의 우선 순위를 계속 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-138">We will continue to prioritize customer and partner issues that impact the stability of MRTK components.</span></span>

<span data-ttu-id="29e68-139">**플랫폼 확장: OpenXR**</span><span class="sxs-lookup"><span data-stu-id="29e68-139">**Platform Expansion: OpenXR**</span></span>

<span data-ttu-id="29e68-140">MRTK 팀은 [OpenXR을](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672)통해 혼합 현실의 개방형 미래를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-140">The MRTK team supports the open future of mixed reality through [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672).</span></span> <span data-ttu-id="29e68-141">OpenXR에 대한 지원은 현재 개발 중이며 초기 미리 보기 지원은 MRTK 2.5.2에서 릴리스되었습니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-141">Support for OpenXR is currently under development, with initial preview support released in MRTK 2.5.2.</span></span>

<span data-ttu-id="29e68-142">**사용자 환경**</span><span class="sxs-lookup"><span data-stu-id="29e68-142">**User Experience**</span></span>

<span data-ttu-id="29e68-143">MRTK에 대한 피드백을 수신 대기하고 있으며 다음을 위한 계획이 계속 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-143">We're listening to your feedback about MRTK and have continued plans for:</span></span>

- <span data-ttu-id="29e68-144">버그 수정</span><span class="sxs-lookup"><span data-stu-id="29e68-144">Bug fixes</span></span>
- <span data-ttu-id="29e68-145">MRTK UX 컨트롤을 더 쉽게 이해할 수 있도록 만들기</span><span class="sxs-lookup"><span data-stu-id="29e68-145">Making MRTK UX controls easier to understand</span></span>
- <span data-ttu-id="29e68-146">HoloLens 셸 패리티</span><span class="sxs-lookup"><span data-stu-id="29e68-146">HoloLens Shell parity</span></span>
- <span data-ttu-id="29e68-147">기능이 회귀되지 않는지 확인하기 위한 테스트</span><span class="sxs-lookup"><span data-stu-id="29e68-147">Tests to ensure features do not regress</span></span>

<span data-ttu-id="29e68-148">**개발자 교육**</span><span class="sxs-lookup"><span data-stu-id="29e68-148">**Developer Education**</span></span>

<span data-ttu-id="29e68-149">개발자 설명서를 Github에서 새 문서 플랫폼으로 마이그레이션했습니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-149">We've migrated our developer documentation from Github to a new docs platform!</span></span> <span data-ttu-id="29e68-150">개발자 설명서 환경을 계속 개선할 수 있도록 여러분의 의견을 듣고 싶습니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-150">We want to hear your feedback so we can continue to improve our developer documentation experience.</span></span>
<span data-ttu-id="29e68-151">현재 MIXED REALITY 문서의 다른 섹션에 있는 [MRTK 자습서가](/windows/mixed-reality/develop/unity/tutorials) 있습니다. MRTK 설명서의 나머지 부분과 함께 이러한 자습서를 실시간으로 마이그레이션할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-151">We currently have [MRTK tutorials](/windows/mixed-reality/develop/unity/tutorials) that live in a different section of Mixed Reality docs. We will be migrating these tutorials to live with the rest of the MRTK documentation.</span></span> 

<span data-ttu-id="29e68-152">**패키징**</span><span class="sxs-lookup"><span data-stu-id="29e68-152">**Packaging**</span></span>

<span data-ttu-id="29e68-153">[Mixed Reality 기능 도구는](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 개발자가 Mixed Reality 기능 패키지를 검색, 업데이트 및 Unity 프로젝트에 추가할 수 있는 새로운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-153">The [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="29e68-154">이름 또는 범주로 패키지를 검색하고, 종속성을 확인하고, 가져오기 전에 프로젝트 매니페스트 파일에 대한 제안된 변경 내용도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-154">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="29e68-155">기능 요청 및 버그에 응답할 때 Mixed Reality 기능 도구를 업데이트하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-155">We intend to make updates to the Mixed Reality Feature Tool as we respond to feature requests and bugs.</span></span>

## <a name="backlog"></a><span data-ttu-id="29e68-156">백로그</span><span class="sxs-lookup"><span data-stu-id="29e68-156">Backlog</span></span>

<span data-ttu-id="29e68-157">다음 목록에서는 MRTK 팀이 추진하려는 주요 투자 중 일부를 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="29e68-157">The following list highlights some of the key investments the MRTK team intends to pursue.</span></span>

- <span data-ttu-id="29e68-158">플랫폼 확장</span><span class="sxs-lookup"><span data-stu-id="29e68-158">Platform expansion</span></span>
- <span data-ttu-id="29e68-159">확장성</span><span class="sxs-lookup"><span data-stu-id="29e68-159">Extensibility</span></span>
- <span data-ttu-id="29e68-160">모듈화</span><span class="sxs-lookup"><span data-stu-id="29e68-160">Modularity</span></span>
- <span data-ttu-id="29e68-161">접근성 기능</span><span class="sxs-lookup"><span data-stu-id="29e68-161">Accessibility features</span></span>
- <span data-ttu-id="29e68-162">세계화 기능 향상</span><span class="sxs-lookup"><span data-stu-id="29e68-162">Globalization enhancements</span></span>
- <span data-ttu-id="29e68-163">클라우드 서비스 지원</span><span class="sxs-lookup"><span data-stu-id="29e68-163">Cloud service support</span></span>
- <span data-ttu-id="29e68-164">도구</span><span class="sxs-lookup"><span data-stu-id="29e68-164">Tools</span></span>
