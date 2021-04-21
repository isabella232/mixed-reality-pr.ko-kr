---
title: Mixed Reality Feature Tool 구성
description: HoloLens 및 VR 개발용 MR Feature Tool에서 Mixed Reality Unity 패키지를 다운로드하고 설치하는 방법에 대해 알아봅니다.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731952"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="3335e-104">Mixed Reality Feature Tool 구성</span><span class="sxs-lookup"><span data-stu-id="3335e-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="3335e-105">Mixed Reality Feature Tool을 사용하는 경우 다음과 같은 세 가지 설정 범주에 액세스하여 원하는 대로 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="3335e-106">다운로드 설정</span><span class="sxs-lookup"><span data-stu-id="3335e-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="3335e-107">기능 설정</span><span class="sxs-lookup"><span data-stu-id="3335e-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="3335e-108">설정 가져오기</span><span class="sxs-lookup"><span data-stu-id="3335e-108">Import settings</span></span>](#import-settings)

## <a name="download-settings"></a><span data-ttu-id="3335e-109">다운로드 설정</span><span class="sxs-lookup"><span data-stu-id="3335e-109">Download settings</span></span>

![다운로드 설정](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="3335e-111">기존 패키지 파일 덮어쓰기</span><span class="sxs-lookup"><span data-stu-id="3335e-111">Overwrite existing package files</span></span>

<span data-ttu-id="3335e-112">이 설정을 사용하도록 설정하면 패키지 파일을 가져올 때마다 패키지 파일이 다운로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 

* <span data-ttu-id="3335e-113">**네트워크 대역폭 사용량을 줄이려면 이 옵션을 사용하지 않도록 설정하는 것이 좋습니다.**</span><span class="sxs-lookup"><span data-stu-id="3335e-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="3335e-114">기본적으로 이전에 가져온 기능 패키지 파일은 다시 다운로드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="3335e-115">패키지 캐시</span><span class="sxs-lookup"><span data-stu-id="3335e-115">Package cache</span></span>

<span data-ttu-id="3335e-116">기능 패키지가 다운로드되는 위치를 업데이트하려면 이 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="3335e-117">이 릴리스에서 이 설정은 **읽기 전용** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="3335e-118">이후 릴리스에서는 이 설정을 구성할 수 있게 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="3335e-119">기능 설정</span><span class="sxs-lookup"><span data-stu-id="3335e-119">Feature settings</span></span>

![기능 설정](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a><span data-ttu-id="3335e-121">미리 보기 릴리스 표시</span><span class="sxs-lookup"><span data-stu-id="3335e-121">Show preview releases</span></span>

<span data-ttu-id="3335e-122">미리 보기 릴리스를 가져오려면 이 설정을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-122">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="3335e-123">기본적으로 미리 보기 릴리스는 Mixed Reality Feature Tool에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-123">By default, preview releases are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="3335e-124">미리 보기 릴리스란 패키지 버전에 **"-preview"** 가 지정된 것을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-124">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

### <a name="show-early-access-program-features"></a><span data-ttu-id="3335e-125">조기 액세스 프로그램 기능 표시</span><span class="sxs-lookup"><span data-stu-id="3335e-125">Show early access program features</span></span>

<span data-ttu-id="3335e-126">등록된 조기 액세스 프로그램 릴리스에서 기능을 가져오려면 이 설정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-126">Enable this setting to acquire features from registered early access programs releases.</span></span>

* <span data-ttu-id="3335e-127">기본적으로 조기 액세스 기능은 Mixed Reality 기능 도구에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-127">By default, early access features are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="3335e-128">`Show preview releases`없이 `Show early access program features`를 사용하면 조기 액세스 패키지가 검색에 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-128">Enabling `Show early access program features` without `Show preview releases` may result in eary access packages not appearing in Discovery.</span></span>

## <a name="import-settings"></a><span data-ttu-id="3335e-129">설정 가져오기</span><span class="sxs-lookup"><span data-stu-id="3335e-129">Import settings</span></span>

![설정 가져오기](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a><span data-ttu-id="3335e-131">기존 패키지 파일 바꾸기</span><span class="sxs-lookup"><span data-stu-id="3335e-131">Replace existing package files</span></span>

<span data-ttu-id="3335e-132">기본적으로 Mixed Reality Feature Tool은 가져올 패키지의 이전 복사본을 제거하여 파일 크기와 불필요한 계산을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-132">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 

* <span data-ttu-id="3335e-133">모든 버전을 유지하려면 이 설정을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-133">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="3335e-134">프로젝트 기준 가져오기 경로</span><span class="sxs-lookup"><span data-stu-id="3335e-134">Project relative import path</span></span>

<span data-ttu-id="3335e-135">가져올 때 기능 패키지가 복사되는 프로젝트 폴더 경로를 업데이트하려면 이 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-135">Change this setting to update project folder path where feature packages are copied on import.</span></span> 

* <span data-ttu-id="3335e-136">예를 들어 프로젝트 폴더가 **C:\GalaxyExplorer** 일 경우 정규화된 가져오기 경로는 **C:\GalaxyExplorer\Packages\MixedReality** 가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-136">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="3335e-137">이 릴리스에서 이 설정은 **읽기 전용** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-137">This setting is **read-only** in this release.</span></span> <span data-ttu-id="3335e-138">이후 릴리스에서는 이 설정을 구성할 수 있게 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-138">Future releases may make this setting configurable.</span></span>

## <a name="early-access-settings"></a><span data-ttu-id="3335e-139">조기 액세스 설정</span><span class="sxs-lookup"><span data-stu-id="3335e-139">Early Access settings</span></span>

![조기 액세스 설정](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a><span data-ttu-id="3335e-141">조기 액세스 프로그램을 제거하기 전에 확인 요청</span><span class="sxs-lookup"><span data-stu-id="3335e-141">Ask for confirmation before removing an early access program</span></span>

<span data-ttu-id="3335e-142">이 설정은 조기 액세스 프로그램을 제거할 때마다 프롬프트를 표시할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-142">This setting determines if a prompt will be displayed each time an early access program is removed.</span></span>

### <a name="my-previews"></a><span data-ttu-id="3335e-143">내 미리 보기</span><span class="sxs-lookup"><span data-stu-id="3335e-143">My previews</span></span>

<span data-ttu-id="3335e-144">등록된 조기 액세스 프로그램 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-144">The list of registered early access programs.</span></span> <span data-ttu-id="3335e-145">`Add`, `Edit` 및 `Remove`를 사용하여 등록된 프로그램 컬렉션을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-145">Use the `Add`, `Edit` and `Remove` to manage the collection of registered programs.</span></span>

## <a name="diagnostic-settings"></a><span data-ttu-id="3335e-146">진단 설정</span><span class="sxs-lookup"><span data-stu-id="3335e-146">Diagnostic settings</span></span>

![진단 설정](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a><span data-ttu-id="3335e-148">로그 파일</span><span class="sxs-lookup"><span data-stu-id="3335e-148">Log file</span></span>

<span data-ttu-id="3335e-149">진단 로그 파일의 경로를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3335e-149">Displays the path to the diagnostic log file.</span></span>

## <a name="see-also"></a><span data-ttu-id="3335e-150">참조</span><span class="sxs-lookup"><span data-stu-id="3335e-150">See also</span></span>

- [<span data-ttu-id="3335e-151">Mixed Reality Feature Tool 시작</span><span class="sxs-lookup"><span data-stu-id="3335e-151">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)