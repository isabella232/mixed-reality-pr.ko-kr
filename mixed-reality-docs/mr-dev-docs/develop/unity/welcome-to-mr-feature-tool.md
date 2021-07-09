---
title: Mixed Reality Feature Tool 시작
description: HoloLens 및 VR 개발용 MR Feature Tool의 기본 사항에 대해 알아봅니다.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: 4e822f2dda2a314ce06bc394a4d92b1aa6953af3
ms.sourcegitcommit: 943489923c69c3a28bc152f1cb516dcdcea2880a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111772416"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="3a3e4-104">Mixed Reality Feature Tool 시작</span><span class="sxs-lookup"><span data-stu-id="3a3e4-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Mixed Reality Feature Tool 배너 이미지](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="3a3e4-106">Mixed Reality Feature Tool은 현재 Unity에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="3a3e4-107">Unreal에서 개발 중인 경우 [도구 설치](../install-the-tools.md) 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="3a3e4-108">Mixed Reality Feature Tool은 개발자가 혼합형 현실 기능 패키지를 검색 및 업데이트하고 Unity 프로젝트에 추가하는 데 사용되는 새로운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="3a3e4-109">이름 또는 범주로 패키지를 검색하고, 종속성을 확인하고, 가져오기 전에 프로젝트 매니페스트 파일에 대한 제안된 변경 내용도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="3a3e4-110">이전에 매니페스트 파일을 사용한 적이 없다면 모든 프로젝트 패키지를 포함하는 JSON 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="3a3e4-111">원하는 패키지의 유효성을 검사하면 Mixed Reality Feature Tool에서 사용자가 선택한 프로젝트로 해당 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="3a3e4-112">시스템 요구 사항</span><span class="sxs-lookup"><span data-stu-id="3a3e4-112">System requirements</span></span>

<span data-ttu-id="3a3e4-113">Mixed Reality Feature Tool을 실행하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="3a3e4-114">.NET 5.0 런타임</span><span class="sxs-lookup"><span data-stu-id="3a3e4-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="3a3e4-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="3a3e4-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="3a3e4-116">Mixed Reality Feature Tool은 현재 Windows에서만 실행되지만 MacOS 지원이 곧 제공될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="3a3e4-117">다운로드</span><span class="sxs-lookup"><span data-stu-id="3a3e4-117">Download</span></span>

<span data-ttu-id="3a3e4-118">환경을 설정한 후 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="3a3e4-119">Microsoft 다운로드 센터에서 [최신 버전의 Mixed Reality Feature Tool을 다운로드합니다](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="3a3e4-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="3a3e4-120">다운로드가 완료되면 파일의 압축을 풀고 바탕 화면에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="3a3e4-121">더 빠른 액세스를 위해 실행 파일에 대한 바로 가기를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-121">We recommend creating a shortcut to the executable file for faster access</span></span>

> [!NOTE]
> <span data-ttu-id="3a3e4-122">Unity 패키지 관리자를 처음 사용하는 경우 [UPM 지침](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager)을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-122">If you're new to using the Unity Package Manager, follow our [UPM instructions](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span></span>

## <a name="changes-in-this-release"></a><span data-ttu-id="3a3e4-123">이 릴리스의 변경 내용:</span><span class="sxs-lookup"><span data-stu-id="3a3e4-123">Changes in this release</span></span>

<span data-ttu-id="3a3e4-124">버전 1.0.2103 베타에는 다음 수정 사항이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-124">Version 1.0.2103 Beta includes the following fixes:</span></span>

* <span data-ttu-id="3a3e4-125">다운로드 오류 검색 기능이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-125">Improvements to download error detection.</span></span>
* <span data-ttu-id="3a3e4-126">올바르게 업데이트되도록 하기 위해 매니페스트를 작성하는 방법에 대한 업데이트입니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-126">Updates on how manifests are written to avoid failure to update correctly.</span></span>
* <span data-ttu-id="3a3e4-127">이스케이프가 프로젝트 매니페스트의 파일 경로에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-127">Escpaing has been removed from file paths in the project manifest.</span></span>

<span data-ttu-id="3a3e4-128">이 릴리스에는 다음과 같은 기능이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-128">The following features have been added in this release:</span></span>

* <span data-ttu-id="3a3e4-129">기능 카탈로그가 이제 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-129">The feature catalog is now cached.</span></span> <span data-ttu-id="3a3e4-130">새 기능 및 업데이트를 확인하려면 검색에서 새로 고침 단추를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-130">To check for new features and updates, please use the refresh button in Discovery.</span></span>
* <span data-ttu-id="3a3e4-131">가져오기 단계에서 검색 이전으로 프로젝트 선택을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-131">Move project selection from the Import step to before Discovery.</span></span>
* <span data-ttu-id="3a3e4-132">사용 가능한 패키지는 프로젝트의 지정된 Unity 버전을 기준으로 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-132">Available packages are filtered by the project's specified Unity version.</span></span>
* <span data-ttu-id="3a3e4-133">이제 검색 뷰에 현재 설치된 패키지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-133">The discovery view now displays currently installed packages.</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="3a3e4-134">1. 시작</span><span class="sxs-lookup"><span data-stu-id="3a3e4-134">1. Getting started</span></span>

<span data-ttu-id="3a3e4-135">실행 파일에서 Mixed Reality Feature Tool을 시작합니다. 처음 시작하는 경우 시작 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-135">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![시작](images/FeatureToolStart.png)

<span data-ttu-id="3a3e4-137">시작 페이지에서 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-137">From the start page, you can:</span></span>

* <span data-ttu-id="3a3e4-138">**기어 아이콘** 단추를 사용하여 도구 설정 [구성](configuring-feature-tool.md)</span><span class="sxs-lookup"><span data-stu-id="3a3e4-138">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="3a3e4-139">**물음표** 단추를 사용하여 기본 웹 브라우저를 시작하고 설명서 표시</span><span class="sxs-lookup"><span data-stu-id="3a3e4-139">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="3a3e4-140">**Start(시작)** 를 선택하여 기능 패키지 검색 시작</span><span class="sxs-lookup"><span data-stu-id="3a3e4-140">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-selecting-your-unity-project"></a><span data-ttu-id="3a3e4-141">2. Unity 프로젝트 선택</span><span class="sxs-lookup"><span data-stu-id="3a3e4-141">2. Selecting your Unity project</span></span>

<span data-ttu-id="3a3e4-142">발견된 모든 기능이 Unity의 프로젝트 버전에서 지원되는지 확인하려면 첫 번째 단계는 프로젝트 경로 필드 오른쪽에 있는 **줄임표** 단추를 사용하여 Mixed Reality Feature Tool을 프로젝트로 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-142">To ensure that all discovered features are supported on your project's version of Unity, the fist step is to point the Mixed Reality Feature Tool to your project using the **ellipsis** button (to the right of the project path field).</span></span>

![Unity 프로젝트 선택](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> <span data-ttu-id="3a3e4-144">Unity 프로젝트 폴더를 검색할 때 표시되는 대화 상자에는 파일 이름에 '_'가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="3a3e4-145">파일 이름에 대한 값이 있어야 폴더를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="3a3e4-146">프로젝트의 폴더를 찾았으면 열기 단추를 클릭하여 Mixed Reality Feature Tool로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-146">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3a3e4-147">Mixed Reality Feature Tool은 유효성 검사를 수행하여 Unity 프로젝트 폴더로 지정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-147">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="3a3e4-148">폴더에는 `Assets`, `Packages` 및 `Project Settings` 폴더가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-148">The folder must contain `Assets`, `Packages` and `Project Settings` folders.</span></span>

## <a name="3-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="3a3e4-149">3. 기능 패키지 검색 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="3a3e4-149">3. Discovering and acquiring feature packages</span></span>

> [!NOTE]
> <span data-ttu-id="3a3e4-150">이제 버전 1.0.2103 베타에서 서버에 액세스할 때마다 기능 카탈로그 콘텐츠를 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-150">Version 1.0.2103 Beta now caches the feature catalog contents whenever the server is accessed.</span></span> <span data-ttu-id="3a3e4-151">이러한 변경을 통해 절대 최신 데이터를 표시하는 대신 사용 가능한 기능에 빠르게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-151">This change enables fast access to available features, at the expense of displaying the absolute latest data.</span></span> <span data-ttu-id="3a3e4-152">카탈로그를 업데이트하려면 **새로 고침** 단추를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-152">To update the catalog, please use the **Refresh** button.</span></span>

<span data-ttu-id="3a3e4-153">기능이 범주별로 그룹화되어 있어 필요한 기능을 더 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-153">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="3a3e4-154">예를 들어 **Mixed Reality Toolkit** 범주에는 선택할 수 있는 몇 가지 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-154">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![검색 및 가져오기](images/FeatureToolDiscovery.png)

<span data-ttu-id="3a3e4-156">Mixed Reality Feature Tool은 이전에 가져온 기능을 인식하는 경우 각각에 의해 알림 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-156">When the Mixed Reality Feature Tool recognizes previously imported feature(s), it displays a notification message by each.</span></span>

![가져온 기능 알림](images/feature-tool-imported-note.png)


<span data-ttu-id="3a3e4-158">원하는 항목을 선택했으면 **Get features(기능 가져오기)** 를 선택하여 카탈로그에서 필요한 패키지를 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-158">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="3a3e4-159">자세한 내용은 [기능 검색 및 가져오기](discovering-features.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-159">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="4-importing-feature-packages"></a><span data-ttu-id="3a3e4-160">4. 기능 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="3a3e4-160">4. Importing feature packages</span></span>

<span data-ttu-id="3a3e4-161">가져오기가 완료되면 전체 패키지 집합이 필수 종속성 목록과 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-161">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="3a3e4-162">기능 또는 패키지 선택 항목을 변경해야 한다면 이때 변경하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-162">If you need to change any feature or package selections, this is the time:</span></span>

![패키지 가져오기](images/FeatureToolImport.png)

<span data-ttu-id="3a3e4-164">**Validate(유효성 검사)** 단추를 사용하여 Unity 프로젝트에서 선택한 기능을 성공적으로 가져올 수 있는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-164">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="3a3e4-165">유효성 검사가 완료되면 성공 메시지 또는 식별된 문제 목록이 포함된 팝업 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-165">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="3a3e4-166">**Import(가져오기)** 를 선택하여 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-166">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="3a3e4-167">**Import(가져오기)** 단추를 클릭한 후에도 문제가 계속되면 단순 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-167">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="3a3e4-168">아니요를 클릭하고 **Validate(유효성 검사)** 단추를 사용하여 문제를 확인하고 해결하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-168">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="3a3e4-169">자세한 내용은 [기능 가져오기](importing-features.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-169">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="5-reviewing-and-approving-project-changes"></a><span data-ttu-id="3a3e4-170">5. 프로젝트 변경 내용 검토 및 승인</span><span class="sxs-lookup"><span data-stu-id="3a3e4-170">5. Reviewing and approving project changes</span></span>

<span data-ttu-id="3a3e4-171">최종 단계는 매니페스트 및 프로젝트 파일에 대한 제안된 변경 내용을 검토하고 승인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-171">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="3a3e4-172">매니페스트에 대한 제안된 변경 내용이 왼쪽에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-172">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="3a3e4-173">프로젝트에 추가할 파일은 오른쪽에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-173">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="3a3e4-174">**Compare(비교)** 단추를 사용하여 현재 매니페스트 및 제안된 변경 내용을 나란히 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-174">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![권한 부여](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="3a3e4-176">자세한 내용은 [프로젝트 수정 내용 검토 및 승인](reviewing-changes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-176">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="6-project-updated"></a><span data-ttu-id="3a3e4-177">6. 프로젝트 업데이트</span><span class="sxs-lookup"><span data-stu-id="3a3e4-177">6. Project updated</span></span>

<span data-ttu-id="3a3e4-178">제안된 변경 내용이 승인되면 선택된 Mixed Reality 기능을 참조하도록 대상 Unity 프로젝트가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-178">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features.</span></span>

![프로젝트 업데이트](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="3a3e4-180">Unity 프로젝트의 **Packages(패키지)** 폴더에는 이제 기능 패키지 파일과 함께 **MixedReality** 하위 폴더가 있으며, 매니페스트에는 적절한 참조가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-180">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="3a3e4-181">Unity로 돌아가서 선택된 새 기능이 로드될 때까지 기다린 후 빌드를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3e4-181">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="3a3e4-182">참조</span><span class="sxs-lookup"><span data-stu-id="3a3e4-182">See also</span></span>

- [<span data-ttu-id="3a3e4-183">기능 도구 구성</span><span class="sxs-lookup"><span data-stu-id="3a3e4-183">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="3a3e4-184">검색 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="3a3e4-184">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="3a3e4-185">기능 패키지 세부 정보 보기</span><span class="sxs-lookup"><span data-stu-id="3a3e4-185">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="3a3e4-186">선택한 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="3a3e4-186">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="3a3e4-187">프로젝트 수정 내용 검토 및 승인</span><span class="sxs-lookup"><span data-stu-id="3a3e4-187">Reviewing and approving project modifications</span></span>](reviewing-changes.md)