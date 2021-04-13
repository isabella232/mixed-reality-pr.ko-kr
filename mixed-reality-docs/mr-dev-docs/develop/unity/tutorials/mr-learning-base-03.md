---
title: 시작 자습서 - 3. MRTK 프로필 구성
description: 이 과정에서는 MRTK(Mixed Reality Toolkit) 프로필을 구성하는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, 공간 인식
ms.localizationpriority: high
ms.openlocfilehash: f6c17dc361846808ec10f1d94932e3089072e642
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300458"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="9bb60-105">3. MRTK 프로필 구성</span><span class="sxs-lookup"><span data-stu-id="9bb60-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="9bb60-106">개요</span><span class="sxs-lookup"><span data-stu-id="9bb60-106">Overview</span></span>

<span data-ttu-id="9bb60-107">이 자습서에서는 MRTK 프로필을 사용자 지정하고 구성하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="9bb60-108"><a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK 프로필</a>은 MRTK 시스템 및 기능을 초기화하는 방법에 대한 구성 정보를 구성하는 중첩된 프로필 트리입니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-108">The <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="9bb60-109">최상위 프로필인 Configuration Profile에는 각 기본 코어 시스템에 대한 중첩 프로필이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="9bb60-110">각 중첩 프로필은 해당 시스템의 동작을 구성하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="9bb60-111">이 예제에서는 공간 메시 관찰자의 설정을 변경하여 공간 인식 메시를 숨기는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="9bb60-112">그러나 MRTK 프로필의 설정 또는 값을 사용자 지정할 때 이러한 원칙을 그대로 적용해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="9bb60-113">[이전 자습서](mr-learning-base-02.md#congratulations)에서 HoloLens 2에 프로젝트를 배포할 때처럼 <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">공간 인식</a> 메시는 환경의 기하 도형을 나타내는 메시 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="9bb60-114">처음에 볼 때는 유용하지만, 시각적 산만함과 이 기능을 사용할 때의 추가 성능 저하를 피하기 위해 일반적으로 꺼져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="9bb60-115">목표</span><span class="sxs-lookup"><span data-stu-id="9bb60-115">Objectives</span></span>

* <span data-ttu-id="9bb60-116">MRTK 프로필을 사용자 지정 및 구성하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="9bb60-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="9bb60-117">공간 인식 메시 숨기기</span><span class="sxs-lookup"><span data-stu-id="9bb60-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="9bb60-118">공간 인식 표시 옵션 변경</span><span class="sxs-lookup"><span data-stu-id="9bb60-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="9bb60-119">공간 인식 메시를 숨기기 위해 수행하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="9bb60-120">기본 구성 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="9bb60-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="9bb60-121">공간 인식 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="9bb60-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="9bb60-122">기본 공간 인식 시스템 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="9bb60-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="9bb60-123">기본 공간 인식 메시 관찰자 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="9bb60-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="9bb60-124">공간 인식 메시의 표시 유형 변경</span><span class="sxs-lookup"><span data-stu-id="9bb60-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="9bb60-125">기본적으로 MRTK 프로필은 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="9bb60-126">이러한 기본 프로필 템플릿을 편집하려면 먼저 복제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="9bb60-127">중첩된 여러 프로필 레이어가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="9bb60-128">따라서 하나 이상의 설정을 구성할 때 여러 프로필을 복제하여 편집하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a><span data-ttu-id="9bb60-129">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-129">Congratulations</span></span>

<span data-ttu-id="9bb60-130">이 자습서에서는 MRTK 프로필 및 설정을 복제, 사용자 지정 및 구성하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb60-130">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9bb60-131">다음 자습서: 4. 장면에서 개체 위치 지정</span><span class="sxs-lookup"><span data-stu-id="9bb60-131">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)