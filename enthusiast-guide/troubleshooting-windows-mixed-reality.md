---
title: Windows Mixed Reality 문제 해결
description: 표준 소비자 지원 설명서를 벗어나는 Windows Mixed Reality 문제 해결을 최신 상태로 유지 합니다.
ms.topic: article
ms.author: rajhawar
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원
ms.openlocfilehash: b347145e73c3e3f96d9a387edbfdb6dc0360b094
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196648"
---
# <a name="troubleshooting-in-windows-mixed-reality"></a><span data-ttu-id="5adbc-104">Windows Mixed Reality의 문제 해결</span><span class="sxs-lookup"><span data-stu-id="5adbc-104">Troubleshooting in Windows Mixed Reality</span></span>

![문제 해결 헤더 로고](images/1050px-Mixedrealityportal.png)

<span data-ttu-id="5adbc-106">모던 하드웨어에서 문제가 발생 하는 경우 일반적인 문제 영역을 진단 하 고 자세한 도움말은 다음 문서를 참조 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5adbc-106">If you run into trouble with your immersive hardware, it's important to diagnose the general issue area and then refer to the following articles for more detailed help.</span></span>

<span data-ttu-id="5adbc-107">여기에서 다음 옵션에 대 한 지원 옵션을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5adbc-107">Here you will find the support options for the following options ensuring you are directed to the right information with least hassle.</span></span> <span data-ttu-id="5adbc-108">또한 다음과 같은 커뮤니티 리소스와 셀프 서비스 콘텐츠 옵션도 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="5adbc-108">We also cover community resources and self-service content options for you to explore:</span></span>

>[!Note]
><span data-ttu-id="5adbc-109">새로 릴리스된 HP 반향 G2 헤드셋 및 컨트롤러를 사용할 때 모든 항목에 대 한 [전용 FAQ 페이지](reverbG2-faq.yml) 를 컴파일 했습니다.</span><span class="sxs-lookup"><span data-stu-id="5adbc-109">In honor of the newly released HP Reverb G2 headset and controllers, we've compiled a [dedicated FAQ page](reverbG2-faq.yml) for all things G2.</span></span> <span data-ttu-id="5adbc-110">이 문서에서는 연결 문제 및 이미지 명확성에서 동작 컨트롤러 문제 및 혼합 현실 실행과 관련 한 모든 사항을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="5adbc-110">This article covers everything from connection problems and image clarity to motion controllers issues and running Mixed Reality.</span></span>

- [<span data-ttu-id="5adbc-111">커뮤니티 도움말 옵션 가져오기</span><span class="sxs-lookup"><span data-stu-id="5adbc-111">Get your community help options</span></span>](#community-help-options)
- [<span data-ttu-id="5adbc-112">자체 도움말 옵션 가져오기</span><span class="sxs-lookup"><span data-stu-id="5adbc-112">Get your self help options</span></span>](#troubleshooting-topics)

## <a name="community-help-options"></a><span data-ttu-id="5adbc-113">커뮤니티 도움말 옵션</span><span class="sxs-lookup"><span data-stu-id="5adbc-113">Community help options</span></span>

<span data-ttu-id="5adbc-114">커뮤니티 개발자를 위한 개발자 질문에 대 한 답변은 Stack Overflow 또는 Reddit에서 질문 하세요.</span><span class="sxs-lookup"><span data-stu-id="5adbc-114">For answers on your developer questions from the community developer ecosystem, ask your question on Stack Overflow or Reddit.</span></span>

### <a name="post-a-question-on-reddit"></a><span data-ttu-id="5adbc-115">Reddit에 질문을 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5adbc-115">Post a question on Reddit</span></span>
<div class='icon is-large'>
    <img alt='Reddit' src='https://docs.microsoft.com/media/logos/logo_reddit.svg'>
</div><br/>

- [<span data-ttu-id="5adbc-116">Reddit의 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="5adbc-116">Windows Mixed Reality on Reddit</span></span>](https://www.reddit.com/r/WindowsMR/)

### <a name="post-a-question-on-stack-overflow"></a><span data-ttu-id="5adbc-117">Stack Overflow에 질문 게시</span><span class="sxs-lookup"><span data-stu-id="5adbc-117">Post a question on Stack Overflow</span></span>
<div class='icon is-large'>
    <img alt='Stack Overflow' src='https://docs.microsoft.com/media/logos/logo_stackoverflow.svg'>
</div><br/>

- [<span data-ttu-id="5adbc-118">Stack Overflow의 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="5adbc-118">Windows Mixed Reality on Stack Overflow</span></span>](https://stackoverflow.com/questions/tagged/windows-mixed-reality)

## <a name="troubleshooting-topics"></a><span data-ttu-id="5adbc-119">문제 해결 항목</span><span class="sxs-lookup"><span data-stu-id="5adbc-119">Troubleshooting topics</span></span>

<span data-ttu-id="5adbc-120">모던 하드웨어에서 문제가 발생 하는 경우 일반적인 문제 영역을 진단 하 고 자세한 도움말은 다음 문서를 참조 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5adbc-120">When you run into trouble with your immersive hardware, it's important to diagnose the general issue area and then refer to the following articles for more detailed help.</span></span> 

### <a name="installation-and-setup-issues"></a><span data-ttu-id="5adbc-121">설치 및 설정 문제</span><span class="sxs-lookup"><span data-stu-id="5adbc-121">Installation and setup issues</span></span>

<span data-ttu-id="5adbc-122">설치, Windows Mixed Reality 실행, 설치 오류, 최소 PC 요구 사항 또는 관리자 권한과 관련된 문제는 다음 두 가지 FAQ를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="5adbc-122">For issues with installation, running Windows Mixed Reality, setup errors, minimum PC requirements, or admin permissions, check out these two FAQs:</span></span>

- [<span data-ttu-id="5adbc-123">설치 오류</span><span class="sxs-lookup"><span data-stu-id="5adbc-123">Installation errors</span></span>](installation_errors.md)
- [<span data-ttu-id="5adbc-124">실시간 문제 설정</span><span class="sxs-lookup"><span data-stu-id="5adbc-124">Setup realted issues</span></span>](wmr-setup-faq.yml)

### <a name="hardware-issues"></a><span data-ttu-id="5adbc-125">하드웨어 문제</span><span class="sxs-lookup"><span data-stu-id="5adbc-125">Hardware issues</span></span>

<span data-ttu-id="5adbc-126">실제 헤드셋 디바이스, 케이블 연결, 연결 오류, Mixed Reality 포털 시작 및 검은색 또는 빈 헤드셋 디스플레이와 관련한 문제는 다음 문서를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="5adbc-126">For problems with your physical headset device, cable connections, connection errors, launching the Mixed Reality Portal, and black or blank headset displays, check out the following articles:</span></span>

- [<span data-ttu-id="5adbc-127">헤드셋 연결</span><span class="sxs-lookup"><span data-stu-id="5adbc-127">Headset connectivity</span></span>](headset-connectivity.md)
- [<span data-ttu-id="5adbc-128">헤드셋 표시</span><span class="sxs-lookup"><span data-stu-id="5adbc-128">Headset display</span></span>](headset-display.md)
- [<span data-ttu-id="5adbc-129">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="5adbc-129">Motion controllers</span></span>](motion-controller-problems.md)

### <a name="core-experience-issues"></a><span data-ttu-id="5adbc-130">핵심 환경 문제</span><span class="sxs-lookup"><span data-stu-id="5adbc-130">Core experience issues</span></span>

<span data-ttu-id="5adbc-131">경계를 만들거나, 소리를 들거나, 소리를 들이지 않거나, Bluetooth 오디오 또는 헤드셋 추적과 관련된 문제가 발생하는 경우 다음 FAQ를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="5adbc-131">If you're experiencing issues with creating boundaries, hearing or not hearing sound, Bluetooth audio, or headset tracking, check out the following FAQs:</span></span>

- [<span data-ttu-id="5adbc-132">경계에 대한 도움말</span><span class="sxs-lookup"><span data-stu-id="5adbc-132">Help with boundaries</span></span>](boundary-questions.md)
- [<span data-ttu-id="5adbc-133">가장 일반적인 음성 및 오디오 문제에 대한 Suppprt</span><span class="sxs-lookup"><span data-stu-id="5adbc-133">Suppprt for most common speech and audio issues</span></span>](speech-and-audio.md)
- [<span data-ttu-id="5adbc-134">추적 시스템</span><span class="sxs-lookup"><span data-stu-id="5adbc-134">Tracking system</span></span>](tracking.md)

### <a name="vr-experience-issues"></a><span data-ttu-id="5adbc-135">VR 환경 문제</span><span class="sxs-lookup"><span data-stu-id="5adbc-135">VR experience issues</span></span>

<span data-ttu-id="5adbc-136">SteamVR 게임, Windows 개발자 모드 설치 또는 브라우저에서 WebVR 콘텐츠 보기에 문제가 있는 경우 아래 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5adbc-136">If you're having issues with SteamVR games, installing Windows Developer Mode, or viewing WebVR content in a browser, the articles below are the place to be:</span></span>

- [<span data-ttu-id="5adbc-137">SteamVR 지원</span><span class="sxs-lookup"><span data-stu-id="5adbc-137">Support with SteamVR</span></span>](steamvr-questions.md)
- [<span data-ttu-id="5adbc-138">WebVR 지원</span><span class="sxs-lookup"><span data-stu-id="5adbc-138">Support with WebVR</span></span>](webvr-questions.md)

### <a name="performance-issues-and-immersice-hardware-related-issues"></a><span data-ttu-id="5adbc-139">성능 문제 및 몰입형 하드웨어 관련 문제</span><span class="sxs-lookup"><span data-stu-id="5adbc-139">Performance issues and immersice hardware related issues</span></span>

<span data-ttu-id="5adbc-140">PC가 느리게 실행되거나, 너무 웜이 있거나, 시각적 개체가 너무 많으면 다음을 설명했습니다.</span><span class="sxs-lookup"><span data-stu-id="5adbc-140">If you're PC is running slow, getting too warm under the hood, or just experiencing choppy visuals, we've got you covered:</span></span>

- [<span data-ttu-id="5adbc-141">일반적인 성능 관련 문제</span><span class="sxs-lookup"><span data-stu-id="5adbc-141">General performance related issues</span></span>](performance-questions.md)
- [<span data-ttu-id="5adbc-142">몰입형 하드웨어 관련 문제</span><span class="sxs-lookup"><span data-stu-id="5adbc-142">Immersive hardware related issues</span></span>](other-questions.md)
