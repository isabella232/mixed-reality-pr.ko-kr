---
title: Maquette 정보
description: Maquette 및 해당 기능에 대해 소개 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, 프로토타입, 혼합 현실, 가상 현실, VR, MR, 피드백, 피드백 허브, 버그
ms.openlocfilehash: fbc2aee7472a26e508937fa1dedfdac08fadfa10
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935623"
---
# <a name="about-maquette"></a><span data-ttu-id="c1ef5-104">Maquette 정보</span><span class="sxs-lookup"><span data-stu-id="c1ef5-104">About Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="c1ef5-105">![로고 ](../images/MaquetteIcon.png) MaquetteScript 소개</span><span class="sxs-lookup"><span data-stu-id="c1ef5-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Introduction</span></span>

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
<span data-ttu-id="c1ef5-106">Maquette는 표준 ECMA 5.1 Javascript를 통합 하 여 VSCode 내에서 편집 및 실행할 수 있는 Maquette 장면 및 개체의 상호 작용에 대 한 투자를 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef5-106">Maquette integrates standard ECMA 5.1 Javascript to enable investment of interactivity in Maquette scenes and objects which can be edited and executed from within VSCode.</span></span> <span data-ttu-id="c1ef5-107">개체의 속성은 스크립트 내에서 읽기 및 설정, 호출 된 개체 메서드, 개체 및 시스템 이벤트 필드 지정 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef5-107">Properties of objects are exposed for reading and setting from within script, object methods called, and object and system events fielded.</span></span> <span data-ttu-id="c1ef5-108">스크립트는 스크립트를 통해 액세스할 수 있는 시스템 개체를 통해 Maquette 자체와 상호 작용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef5-108">Script can also interact with Maquette itself via system objects accessible via script.</span></span> <span data-ttu-id="c1ef5-109">사용자가 조작할 수 있는 다양 한 UI 컨트롤은 시스템의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef5-109">Various UI controls that the user can interact with are part of the system.</span></span> <span data-ttu-id="c1ef5-110">Maquette에서 작성 하거나 스크립트 내에서 만들고 관리할 때 이러한 내용을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef5-110">These can be added when authoring in Maquette or created and managed from within script.</span></span> <span data-ttu-id="c1ef5-111">이러한 요소 (데이터 입력, 클릭 등)를 포함 하는 사용자 상호 작용 이벤트는 스크립트에 이벤트로도 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef5-111">User interaction events with these elements (data entry, clicks, etc) are also exposed to script as events.</span></span> <span data-ttu-id="c1ef5-112">이러한 추가 기능을 사용 하면 실험에서 데이터 시각화로, 혼합 현실 사용자 시나리오를 탐색 하 여 AR 또는 VR의 완벽 한 환경으로 간단 하 고 복잡 한 장면을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef5-112">With these additions, simple to complex scenes can be built, from experiments to data visualization to explorations of Mixed Reality user scenarios to fully realized experiences in AR or VR.</span></span>

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
<span data-ttu-id="c1ef5-113">60 second'ish 비디오</span><span class="sxs-lookup"><span data-stu-id="c1ef5-113">60 second'ish video</span></span>
* <span data-ttu-id="c1ef5-114">항목 제목 카드</span><span class="sxs-lookup"><span data-stu-id="c1ef5-114">Entry Title Card</span></span>
  * <span data-ttu-id="c1ef5-115">Maquette에서 대화형 혼합 현실 콘텐츠 만들기</span><span class="sxs-lookup"><span data-stu-id="c1ef5-115">Creation of Interactive Mixed Reality Content in Maquette</span></span>
  * <span data-ttu-id="c1ef5-116">스크립팅/대화형 작업/u i s 시스템</span><span class="sxs-lookup"><span data-stu-id="c1ef5-116">Scripting/Interactivity/UI System</span></span>
* <span data-ttu-id="c1ef5-117">팀 또는 비디오 캡션에 오신 것을 .VO.MSECND.NET?</span><span class="sxs-lookup"><span data-stu-id="c1ef5-117">VO welcome by team or video captions?</span></span>  <span data-ttu-id="c1ef5-118">방법과</span><span class="sxs-lookup"><span data-stu-id="c1ef5-118">explaining:</span></span>
  * <span data-ttu-id="c1ef5-119">대화형 MR 콘텐츠 생성을 위한 스크립팅의 이유</span><span class="sxs-lookup"><span data-stu-id="c1ef5-119">reasoning behind scripting to enable creation of interactive MR content</span></span>
  * <span data-ttu-id="c1ef5-120">매우 광범위 한 브러시 스트로크에서 사용할 수 있는 방법에 터치</span><span class="sxs-lookup"><span data-stu-id="c1ef5-120">touch on how it can be used in very broad brush strokes</span></span>
* <span data-ttu-id="c1ef5-121">Scripting vingette의 동작</span><span class="sxs-lookup"><span data-stu-id="c1ef5-121">Scripting vingette’s in action</span></span>
  * <span data-ttu-id="c1ef5-122">작성 대화 상자</span><span class="sxs-lookup"><span data-stu-id="c1ef5-122">Composing dialog box</span></span>
  * <span data-ttu-id="c1ef5-123">개요에서 앱 빌드 (요리 앱 데모)</span><span class="sxs-lookup"><span data-stu-id="c1ef5-123">Building app from outline (cooking app demo)</span></span>
  * <span data-ttu-id="c1ef5-124">Photogrammetry 모델에서 작성</span><span class="sxs-lookup"><span data-stu-id="c1ef5-124">Composing in photogrammetry model</span></span>
  * <span data-ttu-id="c1ef5-125">문제 해결 가이드와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="c1ef5-125">Interacting with troubleshooting guide</span></span>
  * <span data-ttu-id="c1ef5-126">VSCode의 디버깅 스크립팅 화면 보기</span><span class="sxs-lookup"><span data-stu-id="c1ef5-126">Screen view of debugging scripting in VSCode</span></span>
  * <span data-ttu-id="c1ef5-127">장면에서 개체의 스크립트에 대 한 액세스 권한 얻기</span><span class="sxs-lookup"><span data-stu-id="c1ef5-127">Getting access to script from an object in scene</span></span>
  * <span data-ttu-id="c1ef5-128">등 ...</span><span class="sxs-lookup"><span data-stu-id="c1ef5-128">Etc...</span></span>
* <span data-ttu-id="c1ef5-129">끝에 요약 제목 카드</span><span class="sxs-lookup"><span data-stu-id="c1ef5-129">Summary Title card at end</span></span>
  * <span data-ttu-id="c1ef5-130">Maquette에 연결</span><span class="sxs-lookup"><span data-stu-id="c1ef5-130">Link to Maquette</span></span>
  * <span data-ttu-id="c1ef5-131">스크립팅을 시작 하는 위치</span><span class="sxs-lookup"><span data-stu-id="c1ef5-131">Where to go to get started with scripting</span></span>
  * <span data-ttu-id="c1ef5-132">공지/상태/커뮤니티</span><span class="sxs-lookup"><span data-stu-id="c1ef5-132">Announcements/status/community</span></span>
  * <span data-ttu-id="c1ef5-133">수행할 수 있는 작업을 확인 하세요. (?)</span><span class="sxs-lookup"><span data-stu-id="c1ef5-133">Look forward to seeing what you can do/submissions(?)</span></span>
  * <span data-ttu-id="c1ef5-134">사용자 의견 및 사용자가 더 나은 기능을 제공 하는 방법</span><span class="sxs-lookup"><span data-stu-id="c1ef5-134">Feedback and how we can serve you better</span></span>

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [<span data-ttu-id="c1ef5-135">시작</span><span class="sxs-lookup"><span data-stu-id="c1ef5-135">Getting Started</span></span>](installation.md)
* [<span data-ttu-id="c1ef5-136">예제 및 샘플 앱</span><span class="sxs-lookup"><span data-stu-id="c1ef5-136">Examples and Sample Apps</span></span>](../samples/overview.md)
* [<span data-ttu-id="c1ef5-137">지원</span><span class="sxs-lookup"><span data-stu-id="c1ef5-137">Support</span></span>](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a><span data-ttu-id="c1ef5-138">피드백 보내기</span><span class="sxs-lookup"><span data-stu-id="c1ef5-138">Send us feedback</span></span>

<span data-ttu-id="c1ef5-139">경험 및 결과에 대해 귀를 기울이고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef5-139">We look forward to hearing about your experiences and results.</span></span> <span data-ttu-id="c1ef5-140">피드백, 제안 및 버그 보고서가 항상 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1ef5-140">Feedback, suggestions and bug reports always welcome!</span></span>
<span data-ttu-id="c1ef5-141">링크를 <></span><span class="sxs-lookup"><span data-stu-id="c1ef5-141"><Link?></span></span>