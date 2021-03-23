---
title: Mixed Reality Feature Tool 구성
description: HoloLens 및 VR 개발용 MR Feature Tool에서 Mixed Reality Unity 패키지를 다운로드하고 설치하는 방법에 대해 알아봅니다.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "99244017"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="799b7-104">Mixed Reality Feature Tool 구성</span><span class="sxs-lookup"><span data-stu-id="799b7-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="799b7-105">Mixed Reality Feature Tool을 사용하는 경우 다음과 같은 세 가지 설정 범주에 액세스하여 원하는 대로 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="799b7-106">다운로드 설정</span><span class="sxs-lookup"><span data-stu-id="799b7-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="799b7-107">기능 설정</span><span class="sxs-lookup"><span data-stu-id="799b7-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="799b7-108">설정 가져오기</span><span class="sxs-lookup"><span data-stu-id="799b7-108">Import settings</span></span>](#import-settings)

![설정](images/FeatureToolSettings.png)

## <a name="download-settings"></a><span data-ttu-id="799b7-110">다운로드 설정</span><span class="sxs-lookup"><span data-stu-id="799b7-110">Download settings</span></span>

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="799b7-111">기존 패키지 파일 덮어쓰기</span><span class="sxs-lookup"><span data-stu-id="799b7-111">Overwrite existing package files</span></span>

<span data-ttu-id="799b7-112">이 설정을 사용하도록 설정하면 패키지 파일을 가져올 때마다 패키지 파일이 다운로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 
* <span data-ttu-id="799b7-113">**네트워크 대역폭 사용량을 줄이려면 이 옵션을 사용하지 않도록 설정하는 것이 좋습니다.**</span><span class="sxs-lookup"><span data-stu-id="799b7-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="799b7-114">기본적으로 이전에 가져온 기능 패키지 파일은 다시 다운로드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="799b7-115">패키지 캐시</span><span class="sxs-lookup"><span data-stu-id="799b7-115">Package cache</span></span>

<span data-ttu-id="799b7-116">기능 패키지가 다운로드되는 위치를 업데이트하려면 이 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="799b7-117">이 릴리스에서 이 설정은 **읽기 전용** 입니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="799b7-118">이후 릴리스에서는 이 설정을 구성할 수 있게 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="799b7-119">기능 설정</span><span class="sxs-lookup"><span data-stu-id="799b7-119">Feature settings</span></span>

### <a name="include-preview-releases"></a><span data-ttu-id="799b7-120">미리 보기 릴리스 포함</span><span class="sxs-lookup"><span data-stu-id="799b7-120">Include preview releases</span></span>

<span data-ttu-id="799b7-121">미리 보기 릴리스를 가져오려면 이 설정을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-121">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="799b7-122">기본적으로 미리 보기 릴리스는 Mixed Reality Feature Tool에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-122">By default, preview releases aren't shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="799b7-123">미리 보기 릴리스란 패키지 버전에 **"-preview"** 가 지정된 것을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-123">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

## <a name="import-settings"></a><span data-ttu-id="799b7-124">설정 가져오기</span><span class="sxs-lookup"><span data-stu-id="799b7-124">Import settings</span></span>

### <a name="replace-existing-package-files"></a><span data-ttu-id="799b7-125">기존 패키지 파일 바꾸기</span><span class="sxs-lookup"><span data-stu-id="799b7-125">Replace existing package files</span></span>

<span data-ttu-id="799b7-126">기본적으로 Mixed Reality Feature Tool은 가져올 패키지의 이전 복사본을 제거하여 파일 크기와 불필요한 계산을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-126">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 
* <span data-ttu-id="799b7-127">모든 버전을 유지하려면 이 설정을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-127">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="799b7-128">프로젝트 기준 가져오기 경로</span><span class="sxs-lookup"><span data-stu-id="799b7-128">Project relative import path</span></span>

<span data-ttu-id="799b7-129">가져올 때 기능 패키지가 복사되는 프로젝트 폴더 경로를 업데이트하려면 이 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-129">Change this setting to update project folder path where feature packages are copied on import.</span></span> 
* <span data-ttu-id="799b7-130">예를 들어 프로젝트 폴더가 **C:\GalaxyExplorer** 일 경우 정규화된 가져오기 경로는 **C:\GalaxyExplorer\Packages\MixedReality** 가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-130">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="799b7-131">이 릴리스에서 이 설정은 **읽기 전용** 입니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-131">This setting is **read-only** in this release.</span></span> <span data-ttu-id="799b7-132">이후 릴리스에서는 이 설정을 구성할 수 있게 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="799b7-132">Future releases may make this setting configurable.</span></span>

## <a name="see-also"></a><span data-ttu-id="799b7-133">참조</span><span class="sxs-lookup"><span data-stu-id="799b7-133">See also</span></span>

- [<span data-ttu-id="799b7-134">Mixed Reality Feature Tool 시작</span><span class="sxs-lookup"><span data-stu-id="799b7-134">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)