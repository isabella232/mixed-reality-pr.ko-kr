---
title: 손 및 모션 컨트롤러
description: 가상와 물리적 간의 경계를 제거할 수 있는 직접 및 동작 컨트롤러 상호 작용 모델에 대해 알아봅니다.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 혼합 현실, 손, 움직임 컨트롤러, 상호 작용, 디자인, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: e931e5ec11548d9aab0d1dd7f8921dbc7554abab
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702159"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="e599b-104">손 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="e599b-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="e599b-105">시나리오</span><span class="sxs-lookup"><span data-stu-id="e599b-105">Scenarios</span></span>
<span data-ttu-id="e599b-106">[상호 작용 개요](interaction-fundamentals.md)를 읽은 후이 상호 작용 모델을 채택 하도록 선택 하는 경우 사용자가 holographic와 상호 작용 하는 데 두 개의 손을 사용 하도록 요구 하는 응용 프로그램을 개발 하 고 있음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="e599b-106">If you choose to adopt this interaction model after reading the [interaction overview](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="e599b-107">응용 프로그램은 가상과 물리적 간의 경계를 제거 하는 목표를 달성 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e599b-107">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="e599b-108">몇 가지 특정 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e599b-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="e599b-109">정보 근로자에게 콘텐츠를 표시하고 제어하는 UI 어포던스가 있는 2D 가상 화면 제공</span><span class="sxs-lookup"><span data-stu-id="e599b-109">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="e599b-110">팩터리 어셈블리 줄에 대 한 첫 번째 줄 작업자 자습서 및 가이드 제공</span><span class="sxs-lookup"><span data-stu-id="e599b-110">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="e599b-111">의료 전문가 지원 및 교육을 위한 전문 도구 개발</span><span class="sxs-lookup"><span data-stu-id="e599b-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="e599b-112">3D 가상 개체를 사용하여 실제 세계를 꾸미거나 두 번째 세계 만들기</span><span class="sxs-lookup"><span data-stu-id="e599b-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="e599b-113">실제 세계를 배경으로 사용하여 위치 기반 서비스 및 게임 만들기</span><span class="sxs-lookup"><span data-stu-id="e599b-113">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="e599b-114">손 및 동작 컨트롤러 소프트웨어나</span><span class="sxs-lookup"><span data-stu-id="e599b-114">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e599b-115">[![수동으로 직접 조작](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="e599b-115">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="e599b-116">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="e599b-116">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="e599b-117">이는 사용자가 직접 holograms를 터치 하 고 조작할 수 있는 손을 활용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e599b-117">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="e599b-118">일상의 경험을 활용 하 고 적절 한 시각적 affordances 제공 함으로써 사용자는 실제 개체를 조작 하는 동일한 방법을 사용 하 여 가상 항목과 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e599b-118">By leveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e599b-119">[![수동으로 가리키고 커밋](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="e599b-119">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="e599b-120">수동으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="e599b-120">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="e599b-121">이를 통해 사용자는 거리가 holograms 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e599b-121">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="e599b-122">사용자가 주변 환경을 최대한 활용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e599b-122">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="e599b-123">사용자는 어디 든 지 holograms를 배치할 수 있으며 모든 거리에서 계속 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e599b-123">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="e599b-124">2D 및 3D holograms을 제어 하 고 조작 하기 위한 멘 탈 모델 및 제스처는 직접 조작의 경우와 매우 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e599b-124">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e599b-125">[![모션 컨트롤러](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="e599b-125">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="e599b-126">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="e599b-126">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="e599b-127">동작 컨트롤러는 하나 또는 두 손을 모두 사용 하는 동시에 다 수의 거리에서 정확한 상호 작용을 제공 하 여 사용자의 물리적 기능을 확장 하는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="e599b-127">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="e599b-128">이러한 하드웨어 액세서리는 널리 사용 되는 다양 한 상호 작용에 대 한 바로 가기를 제공 하 고 다양 한 작업에 대 한 tactile 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e599b-128">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="e599b-129">현재 동작 컨트롤러는 WMR (Windows Mixed Reality) 시나리오 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e599b-129">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="e599b-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e599b-130">See also</span></span>
* [<span data-ttu-id="e599b-131">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="e599b-131">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e599b-132">헤드 게이즈 및 유지</span><span class="sxs-lookup"><span data-stu-id="e599b-132">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="e599b-133">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="e599b-133">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e599b-134">수동으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="e599b-134">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="e599b-135">핸즈프리</span><span class="sxs-lookup"><span data-stu-id="e599b-135">Hands-free</span></span>](hands-free.md)
