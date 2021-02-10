---
title: Mixed Reality Feature Tool 시작
description: HoloLens 및 VR 개발용 MR Feature Tool의 기본 사항에 대해 알아봅니다.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: 0aad81ddd625467dd9159232d590b1a4bf68d06b
ms.sourcegitcommit: d9f87635c87627adba7db37834e4627c149f9a28
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99570256"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="9d76a-104">Mixed Reality Feature Tool 시작</span><span class="sxs-lookup"><span data-stu-id="9d76a-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Mixed Reality Feature Tool 배너 이미지](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="9d76a-106">Mixed Reality Feature Tool은 현재 Unity에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="9d76a-107">Unreal에서 개발 중인 경우 [도구 설치](../install-the-tools.md) 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d76a-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="9d76a-108">Mixed Reality Feature Tool은 개발자가 혼합형 현실 기능 패키지를 검색 및 업데이트하고 Unity 프로젝트에 추가하는 데 사용되는 새로운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="9d76a-109">이름 또는 범주로 패키지를 검색하고, 종속성을 확인하고, 가져오기 전에 프로젝트 매니페스트 파일에 대한 제안된 변경 내용도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="9d76a-110">이전에 매니페스트 파일을 사용한 적이 없다면 모든 프로젝트 패키지를 포함하는 JSON 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="9d76a-111">원하는 패키지의 유효성을 검사하면 Mixed Reality Feature Tool에서 사용자가 선택한 프로젝트로 해당 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="9d76a-112">시스템 요구 사항</span><span class="sxs-lookup"><span data-stu-id="9d76a-112">System requirements</span></span>

<span data-ttu-id="9d76a-113">Mixed Reality Feature Tool을 실행하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="9d76a-114">.NET 5.0 런타임</span><span class="sxs-lookup"><span data-stu-id="9d76a-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="9d76a-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="9d76a-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="9d76a-116">Mixed Reality Feature Tool은 현재 Windows에서만 실행되지만 MacOS 지원이 곧 제공될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="9d76a-117">다운로드</span><span class="sxs-lookup"><span data-stu-id="9d76a-117">Download</span></span> 

<span data-ttu-id="9d76a-118">환경을 설정한 후 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="9d76a-119">Microsoft 다운로드 센터에서 [최신 버전의 Mixed Reality Feature Tool을 다운로드합니다](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="9d76a-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="9d76a-120">다운로드가 완료되면 파일의 압축을 풀고 바탕 화면에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="9d76a-121">더 빠른 액세스를 위해 실행 파일에 대한 바로 가기를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-121">We recommend creating a shortcut to the executable file for faster access</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="9d76a-122">1. 시작</span><span class="sxs-lookup"><span data-stu-id="9d76a-122">1. Getting started</span></span>

<span data-ttu-id="9d76a-123">실행 파일에서 Mixed Reality Feature Tool을 시작합니다. 처음 시작하는 경우 시작 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-123">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![시작](images/FeatureToolStart.png)

<span data-ttu-id="9d76a-125">시작 페이지에서 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-125">From the start page, you can:</span></span>

* <span data-ttu-id="9d76a-126">**기어 아이콘** 단추를 사용하여 도구 설정 [구성](configuring-feature-tool.md)</span><span class="sxs-lookup"><span data-stu-id="9d76a-126">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="9d76a-127">**물음표** 단추를 사용하여 기본 웹 브라우저를 시작하고 설명서 표시</span><span class="sxs-lookup"><span data-stu-id="9d76a-127">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="9d76a-128">**Start(시작)** 를 선택하여 기능 패키지 검색 시작</span><span class="sxs-lookup"><span data-stu-id="9d76a-128">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="9d76a-129">2. 기능 패키지 검색 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="9d76a-129">2. Discovering and acquiring feature packages</span></span>

<span data-ttu-id="9d76a-130">시작을 누르면 바로 기능 패키지 카탈로그가 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-130">The feature package catalog is retrieved as soon as you press Start.</span></span> <span data-ttu-id="9d76a-131">기능이 범주별로 그룹화되어 있어 필요한 기능을 더 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-131">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="9d76a-132">예를 들어 **Mixed Reality Toolkit** 범주에는 선택할 수 있는 몇 가지 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-132">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![검색 및 가져오기](images/FeatureToolDiscovery.png)

<span data-ttu-id="9d76a-134">원하는 항목을 선택했으면 **Get features(기능 가져오기)** 를 선택하여 카탈로그에서 필요한 패키지를 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-134">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="9d76a-135">자세한 내용은 [기능 검색 및 가져오기](discovering-features.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d76a-135">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="3-importing-feature-packages"></a><span data-ttu-id="9d76a-136">3. 기능 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="9d76a-136">3. Importing feature packages</span></span>

<span data-ttu-id="9d76a-137">가져오기가 완료되면 전체 패키지 집합이 필수 종속성 목록과 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-137">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="9d76a-138">기능 또는 패키지 선택 항목을 변경해야 한다면 이때 변경하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-138">If you need to change any feature or package selections, this is the time:</span></span>

![패키지 가져오기](images/FeatureToolImport.png)

<span data-ttu-id="9d76a-140">**Validate(유효성 검사)** 단추를 사용하여 Unity 프로젝트에서 선택한 기능을 성공적으로 가져올 수 있는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-140">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="9d76a-141">유효성 검사가 완료되면 성공 메시지 또는 식별된 문제 목록이 포함된 팝업 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-141">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="9d76a-142">또한 가져오기 전에 대상 Unity 프로젝트의 위치를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-142">You also need to set the location of the target Unity project before you import.</span></span> <span data-ttu-id="9d76a-143">프로젝트 경로 필드의 왼쪽에 있는 **줄임표** 단추를 사용하여 찾아보세요.</span><span class="sxs-lookup"><span data-stu-id="9d76a-143">Use the **ellipsis** button to the left of the project path field to browse.</span></span> <span data-ttu-id="9d76a-144">파일 시스템 탐색이 완료되면 대상 Unity 프로젝트를 포함하는 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-144">When you're done navigating your file system, open the folder containing your target Unity project.</span></span>

> [!NOTE]
> <span data-ttu-id="9d76a-145">Unity 프로젝트 폴더를 검색할 때 표시되는 대화 상자에는 파일 이름에 '_'가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-145">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="9d76a-146">파일 이름에 대한 값이 있어야 폴더를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-146">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="9d76a-147">**Import(가져오기)** 를 선택하여 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-147">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="9d76a-148">**Import(가져오기)** 단추를 클릭한 후에도 문제가 계속되면 단순 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-148">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="9d76a-149">아니요를 클릭하고 **Validate(유효성 검사)** 단추를 사용하여 문제를 확인하고 해결하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-149">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="9d76a-150">자세한 내용은 [기능 가져오기](importing-features.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d76a-150">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="4-reviewing-and-approving-project-changes"></a><span data-ttu-id="9d76a-151">4. 프로젝트 변경 내용 검토 및 승인</span><span class="sxs-lookup"><span data-stu-id="9d76a-151">4. Reviewing and approving project changes</span></span>

<span data-ttu-id="9d76a-152">최종 단계는 매니페스트 및 프로젝트 파일에 대한 제안된 변경 내용을 검토하고 승인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-152">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="9d76a-153">매니페스트에 대한 제안된 변경 내용이 왼쪽에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-153">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="9d76a-154">프로젝트에 추가할 파일은 오른쪽에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-154">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="9d76a-155">**Compare(비교)** 단추를 사용하여 현재 매니페스트 및 제안된 변경 내용을 나란히 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-155">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![권한 부여](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="9d76a-157">자세한 내용은 [프로젝트 수정 내용 검토 및 승인](reviewing-changes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d76a-157">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="5-project-updated"></a><span data-ttu-id="9d76a-158">5. 프로젝트 업데이트</span><span class="sxs-lookup"><span data-stu-id="9d76a-158">5. Project updated</span></span>

<span data-ttu-id="9d76a-159">제안된 변경 내용이 승인되면 선택된 혼합 현실 기능을 참조하도록 대상 Unity 프로젝트가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-159">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features:</span></span>

![프로젝트 업데이트](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="9d76a-161">Unity 프로젝트의 **Packages(패키지)** 폴더에는 이제 기능 패키지 파일과 함께 **MixedReality** 하위 폴더가 있으며, 매니페스트에는 적절한 참조가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-161">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="9d76a-162">Unity로 돌아가서 선택된 새 기능이 로드될 때까지 기다린 후 빌드를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9d76a-162">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="9d76a-163">참조</span><span class="sxs-lookup"><span data-stu-id="9d76a-163">See also</span></span>

- [<span data-ttu-id="9d76a-164">기능 도구 구성</span><span class="sxs-lookup"><span data-stu-id="9d76a-164">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="9d76a-165">검색 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="9d76a-165">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="9d76a-166">기능 패키지 세부 정보 보기</span><span class="sxs-lookup"><span data-stu-id="9d76a-166">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="9d76a-167">선택한 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="9d76a-167">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="9d76a-168">프로젝트 수정 내용 검토 및 승인</span><span class="sxs-lookup"><span data-stu-id="9d76a-168">Reviewing and approving project modifications</span></span>](reviewing-changes.md)
