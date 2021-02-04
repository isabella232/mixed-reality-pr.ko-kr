---
title: 기능 검색 및 가져오기
description: 혼합 현실 기능을 알아보고 다운로드합니다.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: 4da6b6fdfc0205d4fa7fb5bf4ae9e48993d7c1e6
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244025"
---
# <a name="discovering-and-acquiring-features"></a><span data-ttu-id="f10f0-104">기능 검색 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="f10f0-104">Discovering and acquiring features</span></span>

<span data-ttu-id="f10f0-105">이 문서의 섹션에서는 Mixed Reality Feature Tool에서 기능 패키지를 찾는 방법을 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-105">The sections in this article outline how to find feature packages in the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="f10f0-106">특정 섹션에 대한 참조 정보가 필요한 경우 아래 스크린샷을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="f10f0-106">Refer to the screenshot below if you need a reference for a given section:</span></span>

![기능 검색](images/FeatureToolDiscovery.png)

## <a name="available-features"></a><span data-ttu-id="f10f0-108">사용 가능한 기능</span><span class="sxs-lookup"><span data-stu-id="f10f0-108">Available features</span></span>

### <a name="category"></a><span data-ttu-id="f10f0-109">범주</span><span class="sxs-lookup"><span data-stu-id="f10f0-109">Category</span></span>

<span data-ttu-id="f10f0-110">Mixed Reality Feature Tool은 원하는 항목을 쉽게 찾을 수 있도록 기능 범주 컬렉션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-110">The Mixed Reality Feature Tool displays a collection of feature categories to make it easy to find what you want.</span></span> <span data-ttu-id="f10f0-111">범주를 확장하면 사용 가능한 기능 컬렉션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-111">Expand any of the categories to display its collection of available features.</span></span>

> [!NOTE]
> <span data-ttu-id="f10f0-112">원하는 기능을 찾을 수 없다면 **기타 기능** 을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="f10f0-112">If you can't find the functionality you're looking for, check **Other features**.</span></span>

![기능 범주](images/FeatureCategory.png)

<span data-ttu-id="f10f0-114">위의 스크린샷에서 범주 헤더에 포함되는 속성을 왼쪽에서 오른쪽 방향으로 나열하면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-114">The category header in the above screenshot contains the following properties, from left to right:</span></span>

- <span data-ttu-id="f10f0-115">확장 및 축소 단추</span><span class="sxs-lookup"><span data-stu-id="f10f0-115">Expand and collapse button</span></span>
- <span data-ttu-id="f10f0-116">범주 이름(예: Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="f10f0-116">Category name (ex: Mixed Reality Toolkit)</span></span>
- <span data-ttu-id="f10f0-117">선택한 기능 수</span><span class="sxs-lookup"><span data-stu-id="f10f0-117">Count of selected features</span></span>
- <span data-ttu-id="f10f0-118">사용 가능한 기능 수</span><span class="sxs-lookup"><span data-stu-id="f10f0-118">Count of available features</span></span>

### <a name="feature"></a><span data-ttu-id="f10f0-119">기능</span><span class="sxs-lookup"><span data-stu-id="f10f0-119">Feature</span></span>

![기능 항목](images/FeatureEntry.png)

<span data-ttu-id="f10f0-121">기능은 해당 범주에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-121">Features are listed in their appropriate category.</span></span> <span data-ttu-id="f10f0-122">위의 스크린샷에서 기능 항목에 포함되는 요소를 왼쪽에서 오른쪽 방향으로 나열하면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-122">From left to right in the above screenshot, feature entries contain:</span></span>

- <span data-ttu-id="f10f0-123">선택 확인란</span><span class="sxs-lookup"><span data-stu-id="f10f0-123">Selection check box</span></span>
- <span data-ttu-id="f10f0-124">기능 이름(예: Mixed Reality Toolkit Foundation)</span><span class="sxs-lookup"><span data-stu-id="f10f0-124">Feature name (ex: Mixed Reality Toolkit Foundation)</span></span>
- <span data-ttu-id="f10f0-125">사용 가능한 버전 목록</span><span class="sxs-lookup"><span data-stu-id="f10f0-125">List of available versions</span></span>
- <span data-ttu-id="f10f0-126">[기능 패키지 세부 정보](viewing-package-details.md)에 대한 링크</span><span class="sxs-lookup"><span data-stu-id="f10f0-126">Link to the [feature package details](viewing-package-details.md)</span></span>

## <a name="refresh-the-feature-catalog"></a><span data-ttu-id="f10f0-127">기능 카탈로그 새로 고침</span><span class="sxs-lookup"><span data-stu-id="f10f0-127">Refresh the feature catalog</span></span>

<span data-ttu-id="f10f0-128">새 기능 및 업데이트된 기능을 확인하려면 새로 고침을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-128">To check for new and updated features, click the refresh</span></span> ![새로 고침 단추](images/RefreshButton.png) <span data-ttu-id="f10f0-130">단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-130">button.</span></span> <span data-ttu-id="f10f0-131">그러면 카탈로그 사이트에 연결되고 최신 정보가 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-131">This will connect to the catalog site and retrieve the latest information.</span></span>
* <span data-ttu-id="f10f0-132">카탈로그를 읽으면 마지막 업데이트 날짜 및 시간이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-132">Once the catalog has been read, the date and time of the last update will be displayed.</span></span>

## <a name="select-features"></a><span data-ttu-id="f10f0-133">기능 선택</span><span class="sxs-lookup"><span data-stu-id="f10f0-133">Select features</span></span>

<span data-ttu-id="f10f0-134">범주를 확장하고, 버전을 선택하고, 확인란을 클릭하여 기능을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-134">Features are selected by expanding a category, selecting a version, and clicking the check box:</span></span>

![선택한 기능](images/SelectedFeatures.png)

<span data-ttu-id="f10f0-136">하나 이상의 기능이 선택된 각 범주가 업데이트되고 개수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-136">Each category with one or more selected features will update to display the count.</span></span>

## <a name="acquiring-features"></a><span data-ttu-id="f10f0-137">기능 가져오기</span><span class="sxs-lookup"><span data-stu-id="f10f0-137">Acquiring features</span></span>

<span data-ttu-id="f10f0-138">기능을 선택한 후 **Get features(기능 가져오기)** 를 선택하면 선택한 기능 패키지 파일의 다운로드가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-138">Once you've chosen your features, select **Get features** to start downloading the selected feature package files.</span></span>

> [!NOTE]
> <span data-ttu-id="f10f0-139">기본적으로 이전에 가져온 기능 패키지 파일은 다시 다운로드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-139">By default, previously acquired feature package files won't be re-downloaded.</span></span> <span data-ttu-id="f10f0-140">이 동작을 변경하려면 [기능 도구 구성](configuring-feature-tool.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f10f0-140">To change this behavior please see [configuring the feature tool](configuring-feature-tool.md).</span></span>

<span data-ttu-id="f10f0-141">다운로드가 완료되면 Mixed Reality Feature Tool이 [기능 가져오기](importing-features.md) 단계로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-141">Once downloading is complete, the Mixed Reality Feature Tool will move to the [importing features](importing-features.md) step.</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="f10f0-142">이전 단계로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="f10f0-142">Going back to the previous step</span></span>

<span data-ttu-id="f10f0-143">**Discover features(기능 검색)** 에서 Mixed Reality Feature Tool을 사용하여 처음으로 다시 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-143">From **Discover features**, the Mixed Reality Feature Tool allows for navigating back to the beginning.</span></span> <span data-ttu-id="f10f0-144">**Go back(돌아가기)** 을 선택하여 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f10f0-144">Select **Go back** to start again.</span></span>

## <a name="see-also"></a><span data-ttu-id="f10f0-145">참조</span><span class="sxs-lookup"><span data-stu-id="f10f0-145">See also</span></span>

- [<span data-ttu-id="f10f0-146">Mixed Reality Feature Tool 시작</span><span class="sxs-lookup"><span data-stu-id="f10f0-146">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="f10f0-147">기능 도구 구성</span><span class="sxs-lookup"><span data-stu-id="f10f0-147">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="f10f0-148">기능 패키지 세부 정보 보기</span><span class="sxs-lookup"><span data-stu-id="f10f0-148">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="f10f0-149">선택한 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="f10f0-149">Importing selected packages</span></span>](importing-features.md)
