---
title: 기능 가져오기
description: HoloLens 및 VR 개발용 MR Feature Tool에서 기능을 가져오고 설치하는 방법에 대해 알아봅니다.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: 0d9139835b9eb4e3e5ce3d1f378c56a4724bfa55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230827"
---
# <a name="importing-features"></a><span data-ttu-id="34140-104">기능 가져오기</span><span class="sxs-lookup"><span data-stu-id="34140-104">Importing features</span></span>

<span data-ttu-id="34140-105">기능이 다운로드되면 검토하고 Unity 프로젝트로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34140-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="34140-106">이 단계에서는 애플리케이션 창이 다음 이미지와 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="34140-106">At this step, your application window should look like the following image:</span></span>

![기능 가져오기](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="34140-108">Features list</span><span class="sxs-lookup"><span data-stu-id="34140-108">Features list</span></span>

<span data-ttu-id="34140-109">**Features(기능)** 목록에는 검색 중에 선택된 패키지 컬렉션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34140-109">The **Features** list contains the collection of packages selected during discovery.</span></span> <span data-ttu-id="34140-110">가져오기 전에 각 기능을 선택하거나 선택 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34140-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="34140-111">패키지 세부 정보는 아래와 같은 **Details(세부 정보)** 링크를 사용하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34140-111">Package details can be viewed using the **Details** link shown below</span></span>

![Features list](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="34140-113">필수 종속성 목록</span><span class="sxs-lookup"><span data-stu-id="34140-113">Required dependencies list</span></span>

<span data-ttu-id="34140-114">**필수 종속성** 목록에는 하나 이상의 선택된 기능이 작동하는 데 필요한 패키지가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34140-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="34140-115">이 목록에는 종속성의 종속성도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="34140-115">This list will also contain dependencies of dependencies.</span></span> <span data-ttu-id="34140-116">가져오기 전에 각 종속성을 선택하거나 선택 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34140-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="34140-117">패키지 세부 정보는 아래와 같은 **Details(세부 정보)** 링크를 사용하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34140-117">Package details can be viewed using the **Details** link shown below</span></span>

![종속성 목록](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="34140-119">필수 종속성을 선택 취소하면 Unity에서 프로젝트를 로드할 때 종속성이 하나 이상 누락되었다는 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="34140-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="34140-120">이러한 기능은 프로젝트에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34140-120">These features won't be usable in the project.</span></span>

## <a name="validating-selections"></a><span data-ttu-id="34140-121">선택 항목 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="34140-121">Validating selections</span></span>

<span data-ttu-id="34140-122">기능을 가져오기 전에 선택한 기능의 유효성을 검사하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="34140-122">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="34140-123">이 단계에서는 성공적인 프로젝트 개발에 방해가 될 수 있는 모든 문제를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="34140-123">This step will raise any issues that are likely to impede successful project development.</span></span>

![유효성 검사 문제](images/ValidationIssues.png)

<span data-ttu-id="34140-125">Mixed Reality Feature Tool은 두 가지 자동 문제 해결 방법(다음 섹션에서 설명) 및 문제를 수동으로 취소하고 해결하는 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="34140-125">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="34140-126">종속성 사용</span><span class="sxs-lookup"><span data-stu-id="34140-126">Enable dependencies</span></span>

<span data-ttu-id="34140-127">**종속성 사용** 단추를 클릭하면 누락된 종속성이 자동으로 다시 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="34140-127">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="34140-128">이는 명시적으로 선택된 종속성(**기능** 목록에 표시됨)과 선택한 기능의 요구 사항에 따라 암시적으로 선택된 종속성에 대해 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="34140-128">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="34140-129">기능 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="34140-129">Disable features</span></span>

<span data-ttu-id="34140-130">**기능 사용 안 함** 을 선택하면 선택되지 않은 하나 이상의 종속성에 종속된 모든 기능이 자동으로 선택 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="34140-130">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="34140-131">이는 암시적으로 선택된 종속성 패키지 및 명시적으로 선택한 기능에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="34140-131">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="34140-132">가져오기</span><span class="sxs-lookup"><span data-stu-id="34140-132">Importing</span></span>

<span data-ttu-id="34140-133">**가져오기** 를 선택하여 선택한 기능을 추가하고 [최종 승인](reviewing-changes.md) 후 대상 프로젝트를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="34140-133">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34140-134">가져오는 동안 유효성 검사 문제가 계속되면 경고 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="34140-134">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="34140-135">[아니요]를 선택하고 **유효성 검사** 를 클릭하여 표시된 문제를 해결하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="34140-135">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![유효성 검사 문제 계속](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="34140-137">이전 단계로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="34140-137">Going back to the previous step</span></span>

<span data-ttu-id="34140-138">**기능 가져오기** 에서 Mixed Reality Feature Tool을 사용하여 [탐색](discovering-features.md)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34140-138">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="34140-139">**돌아가기** 를 선택하여 다른 기능 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="34140-139">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="34140-140">참조</span><span class="sxs-lookup"><span data-stu-id="34140-140">See also</span></span>

- [<span data-ttu-id="34140-141">Mixed Reality Feature Tool 시작</span><span class="sxs-lookup"><span data-stu-id="34140-141">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="34140-142">검색 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="34140-142">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="34140-143">기능 패키지 세부 정보 보기</span><span class="sxs-lookup"><span data-stu-id="34140-143">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="34140-144">프로젝트 수정 내용 검토 및 승인</span><span class="sxs-lookup"><span data-stu-id="34140-144">Reviewing and approving project modifications</span></span>](reviewing-changes.md)