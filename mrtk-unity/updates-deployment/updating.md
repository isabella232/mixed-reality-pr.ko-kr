---
title: 업데이트
description: 낮은 버전의 MRTK에서 마이그레이션하는 방법에 대 한 설명서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 97f45328bc8f9b811e815da0240138790db699c6
ms.sourcegitcommit: 0b09536c16f6802acc120a973d720aec7e30f617
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2021
ms.locfileid: "107742239"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a><span data-ttu-id="26ef4-104">Microsoft Mixed Reality Toolkit 업데이트</span><span class="sxs-lookup"><span data-stu-id="26ef4-104">Updating the Microsoft Mixed Reality Toolkit</span></span>

- [<span data-ttu-id="26ef4-105">새 버전의 MRTK로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="26ef4-105">Upgrading to a new version of MRTK</span></span>](#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="26ef4-106">2.3.0 2.4.0</span><span class="sxs-lookup"><span data-stu-id="26ef4-106">2.3.0 to 2.4.0</span></span>](#updating-230-to-240)
- [<span data-ttu-id="26ef4-107">2.2.0 2.3.0</span><span class="sxs-lookup"><span data-stu-id="26ef4-107">2.2.0 to 2.3.0</span></span>](#updating-220-to-230)
- [<span data-ttu-id="26ef4-108">2.1.0 2.2.0</span><span class="sxs-lookup"><span data-stu-id="26ef4-108">2.1.0 to 2.2.0</span></span>](#updating-210-to-220)
- [<span data-ttu-id="26ef4-109">2.0.0 2.1.0</span><span class="sxs-lookup"><span data-stu-id="26ef4-109">2.0.0 to 2.1.0</span></span>](#updating-200-to-210)
- [<span data-ttu-id="26ef4-110">2.0.0에 대 한 RC2</span><span class="sxs-lookup"><span data-stu-id="26ef4-110">RC2 to 2.0.0</span></span>](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a><span data-ttu-id="26ef4-111">현재 버전 찾기</span><span class="sxs-lookup"><span data-stu-id="26ef4-111">Finding the current version</span></span> 

<span data-ttu-id="26ef4-112">현재 사용 중인 MRTK의 버전을 확인 하려면 다음 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="26ef4-112">Follow these instructions to figure out which version of the MRTK you're currently using:</span></span>

1. <span data-ttu-id="26ef4-113">Unity에서 MRTK 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="26ef4-113">Open your MRTK project in Unity</span></span>
2. <span data-ttu-id="26ef4-114">프로젝트 창에서 "MixedRealityToolkit" 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-114">Navigate to the "MixedRealityToolkit" folder in your Project window</span></span>
3. <span data-ttu-id="26ef4-115">"버전" 이라는 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-115">Open the file called "Version"</span></span>

<span data-ttu-id="26ef4-116">위의 파일과 폴더가 존재 하지 않는 경우 새 버전의 MRTK가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-116">If the file and folder above doesn't exist, you're on a newer version of the MRTK.</span></span> <span data-ttu-id="26ef4-117">이 경우 다음을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-117">In that case, try the following:</span></span>

1. <span data-ttu-id="26ef4-118">"Mixed Reality Toolkit Foundation" 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-118">Navigate to the "Mixed Reality Toolkit Foundation" folder</span></span>
2. <span data-ttu-id="26ef4-119">Unity의 미리 보기를 보거나 텍스트 편집기를 사용 하 여 열려면 "package.json"을 클릭 하세요.</span><span class="sxs-lookup"><span data-stu-id="26ef4-119">Click on the "package.json" to see a preview in Unity or open it with a text editor</span></span>
3. <span data-ttu-id="26ef4-120">"버전:" 이라는 단어를 사용 하 여 줄을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-120">Look for the line with the word "version:"</span></span> 

## <a name="upgrading-to-a-new-version-of-mrtk"></a><span data-ttu-id="26ef4-121">새 버전의 MRTK로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="26ef4-121">Upgrading to a new version of MRTK</span></span>

<span data-ttu-id="26ef4-122">*MRTK 업데이트를 가져온 후 [](../features/tools/migration-window.md)* 에는 더 이상 사용 되지 않는 구성 요소에서 자동으로 수정 하 고 업그레이드 하 여 주요 변경 내용을 조정 하는 방법으로 마이그레이션 도구를 실행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-122">*It is strongly recommended to run the [migration tool](../features/tools/migration-window.md) after getting the MRTK update* to auto-fix and upgrade from deprecated components and adjust to breaking changes.</span></span> <span data-ttu-id="26ef4-123">마이그레이션 도구는 **도구** 패키지의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-123">The migration tool is part of the **Tools** package.</span></span>

<span data-ttu-id="26ef4-124">아래 지침에서는 2.4.0 to 2.5.0 upgrade 경로에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-124">The instructions below describe the 2.4.0 to 2.5.0 upgrade path.</span></span> <span data-ttu-id="26ef4-125">프로젝트가 2.3.0 또는 이전 버전인 경우 버전 [간](#updating-230-to-240) 변경 내용을 참조 하 여 업그레이드 경로를 이해 하거나, 버전에 따라 업그레이드를 수행 하는 이전 [릴리스의 지침](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) 을 읽으십시오.</span><span class="sxs-lookup"><span data-stu-id="26ef4-125">If your project is on 2.3.0 or earlier, read on to the changes [between versions](#updating-230-to-240) to understand the upgrade path, or read the previous [release's instructions](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) to do a version-by-version upgrade.</span></span>

### <a name="mixed-reality-feature-tool"></a><span data-ttu-id="26ef4-126">Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="26ef4-126">Mixed Reality Feature Tool</span></span>
<span data-ttu-id="26ef4-127">MRTK를 최신 버전으로 업그레이드 하는 가장 쉬운 방법은 [혼합 현실 기능 도구](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 를 사용 하 여 최신 패키지를 다운로드 하 고 Unity 프로젝트에 직접 로드 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-127">The easiest way to upgrade MRTK to a newer version MRTK is by using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) to download the latest packages and load them directly to your Unity project.</span></span>

<span data-ttu-id="26ef4-128">이전에 프로젝트에서 Unity asset (. unitypackage) 파일을 사용한 경우에는 [다음 지침](#switching-from-unity-asset-files-to-mixed-reality-feature-tool)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="26ef4-128">If the project previously used Unity asset (.unitypackage) files, please see [these instructions](#switching-from-unity-asset-files-to-mixed-reality-feature-tool).</span></span> 

### <a name="unity-asset-unitypackage-files"></a><span data-ttu-id="26ef4-129">Unity 자산 (. unitypackage) 파일</span><span class="sxs-lookup"><span data-stu-id="26ef4-129">Unity asset (.unitypackage) files</span></span>

<span data-ttu-id="26ef4-130">다른 업그레이드 경로는 MRTK Unity 패키지를 수동으로 다운로드 하 여 프로젝트에 적용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-130">Another upgrade path is to manually download MRTK Unity packages and apply them to your project.</span></span> <span data-ttu-id="26ef4-131">다음 단계를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="26ef4-131">See the steps below,</span></span>

1. <span data-ttu-id="26ef4-132">업그레이드 단계의 어느 시점에서 든 모든 snags 적중 하는 경우 현재 프로젝트의 복사본을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-132">Save a copy of your current project, in case you hit any snags at any point in the upgrade steps.</span></span>
1. <span data-ttu-id="26ef4-133">Unity 닫기</span><span class="sxs-lookup"><span data-stu-id="26ef4-133">Close Unity</span></span>
1. <span data-ttu-id="26ef4-134">*자산* 폴더 내에서 다음 **mrtk** 폴더를 해당 .xml 파일과 함께 삭제 합니다. 프로젝트에 나열 된 모든 폴더가 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-134">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="26ef4-135">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="26ef4-135">MRTK/Core</span></span>
    - <span data-ttu-id="26ef4-136">MRTK/예제</span><span class="sxs-lookup"><span data-stu-id="26ef4-136">MRTK/Examples</span></span>
    - <span data-ttu-id="26ef4-137">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="26ef4-137">MRTK/Extensions</span></span>
    - <span data-ttu-id="26ef4-138">MRTK/공급자</span><span class="sxs-lookup"><span data-stu-id="26ef4-138">MRTK/Providers</span></span>
    - <span data-ttu-id="26ef4-139">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="26ef4-139">MRTK/SDK</span></span>
    - <span data-ttu-id="26ef4-140">MRTK/서비스</span><span class="sxs-lookup"><span data-stu-id="26ef4-140">MRTK/Services</span></span>
    - <span data-ttu-id="26ef4-141">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="26ef4-141">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="26ef4-142">MRTK 셰이더가 수정 된 경우 MRTK/StandardAssets 폴더를 삭제 하기 전에 로컬 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-142">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="26ef4-143">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="26ef4-143">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="26ef4-144">**MixedRealityToolkit** 폴더 또는 해당. i a 파일을 삭제 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="26ef4-144">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="26ef4-145">**라이브러리** 폴더를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-145">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="26ef4-146">Unity Collab와 같은 일부 Unity 도구는 구성 정보를 라이브러리 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-146">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="26ef4-147">이를 수행 하는 도구를 사용 하는 경우 먼저 라이브러리에서 도구의 데이터 폴더를 복사한 후 라이브러리를 다시 생성 한 후에 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-147">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="26ef4-148">Unity에서 프로젝트를 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-148">Re-open the project in Unity</span></span>
1. <span data-ttu-id="26ef4-149">새 unity 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="26ef4-149">Import the new unity packages</span></span>
    - <span data-ttu-id="26ef4-150">파운데이션- _이 패키지를 먼저 가져옵니다_ .</span><span class="sxs-lookup"><span data-stu-id="26ef4-150">Foundation - _Import this package first_</span></span>
    - <span data-ttu-id="26ef4-151">도구</span><span class="sxs-lookup"><span data-stu-id="26ef4-151">Tools</span></span>
    - <span data-ttu-id="26ef4-152">필드 확장할</span><span class="sxs-lookup"><span data-stu-id="26ef4-152">(Optional) Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="26ef4-153">추가 확장을 설치한 경우 다시 가져와야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-153">If additional extensions had been installed, they may need to be re-imported.</span></span>
    - <span data-ttu-id="26ef4-154">필드 예와</span><span class="sxs-lookup"><span data-stu-id="26ef4-154">(Optional) Examples</span></span>
1. <span data-ttu-id="26ef4-155">Unity를 닫고 **라이브러리** 폴더를 삭제 합니다 (아래 노트를 먼저 읽으십시오!).</span><span class="sxs-lookup"><span data-stu-id="26ef4-155">Close Unity and delete the **Library** folder (read the note below first!).</span></span> <span data-ttu-id="26ef4-156">이 단계는 Unity가 asset 데이터베이스를 새로 고치고 기존 사용자 지정 프로필을 조정 하도록 강제 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-156">This step is necessary to force Unity to refresh its asset database and reconcile existing custom profiles.</span></span>
1. <span data-ttu-id="26ef4-157">Unity를 시작 하 고 프로젝트의 각 장면에 대해</span><span class="sxs-lookup"><span data-stu-id="26ef4-157">Launch Unity, and for each scene in the project</span></span>
    - <span data-ttu-id="26ef4-158">계층에서 **MixedRealityToolkit** 및 **MixedRealityPlayspace**(있는 경우)를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-158">Delete **MixedRealityToolkit** and **MixedRealityPlayspace**, if present, from the hierarchy.</span></span> <span data-ttu-id="26ef4-159">그러면 주 카메라가 삭제 되지만 다음 단계에서는 다시 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-159">This will delete the main camera, but it will be re-created in the next step.</span></span> <span data-ttu-id="26ef4-160">기본 카메라의 속성을 수동으로 변경한 경우에는 새 카메라를 만든 후 수동으로 다시 적용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-160">If any properties of the main camera have been manually changed, these will have to be re-applied manually once the new camera is created.</span></span>
    - <span data-ttu-id="26ef4-161">**MixedRealityToolkit-> 선택 하 여 장면에 추가 및 구성**</span><span class="sxs-lookup"><span data-stu-id="26ef4-161">Select **MixedRealityToolkit -> Add to Scene and Configure**</span></span>
    - <span data-ttu-id="26ef4-162">**> MixedRealityToolkit 유틸리티-> 업데이트-> 컨트롤러 매핑 프로필** (한 번만 수행 해야 함)을 선택 합니다. 이렇게 하면 사용자 지정 된 입력 동작을 그대로 유지 하면서 업데이트 된 축 및 데이터를 사용 하 여 사용자 지정 컨트롤러 매핑 프로필을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-162">Select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (only needs to be done once)       - This will update any custom controller mapping profiles with updated axes and data, while leaving your custom-assigned input actions intact</span></span>
1. <span data-ttu-id="26ef4-163">[마이그레이션 도구](../features/tools/migration-window.md) 를 실행 하 고 *전체 프로젝트* 에서 도구를 실행 하 여 모든 코드가 최신 버전으로 업데이트 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-163">Run the [migration tool](../features/tools/migration-window.md) and run the tool on the *Full Project* to ensure that all of your code is updated to the latest.</span></span>
   <span data-ttu-id="26ef4-164">마이그레이션 창에는 각각 자체에서 실행 되어야 하는 여러 마이그레이션 처리기가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-164">The migration window contains a number of different migration handlers, which must each be run on their own.</span></span> <span data-ttu-id="26ef4-165">이 단계에는 다음이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-165">This step involves:</span></span>
   - <span data-ttu-id="26ef4-166">**마이그레이션 처리기 선택** 드롭다운에서 첫 번째 마이그레이션 처리기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-166">Select the first migration handler from the **Migration Handler Selection** dropdown.</span></span>
   - <span data-ttu-id="26ef4-167">"전체 프로젝트" 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-167">Click the "Full Project" button.</span></span>
   - <span data-ttu-id="26ef4-168">"마이그레이션을 위한 전체 프로젝트 추가" 단추를 클릭 합니다 .이 단추를 클릭 하면 마이그레이션할 개체에 대 한 전체 프로젝트를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-168">Click the "Add full project for migration" button (this will scan the entire project for objects to migrate).</span></span>
   - <span data-ttu-id="26ef4-169">Migrateable 개체가 발견 된 경우 사용 하도록 설정 해야 하는 "마이그레이션" 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-169">Click the "Migrate" button which should be enabled if any migrateable objects were found.</span></span>
   - <span data-ttu-id="26ef4-170">드롭다운 내의 각 마이그레이션 처리기에 대해 앞의 세 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-170">Repeat the previous three steps for each of the migration handlers within the dropdown.</span></span>
     <span data-ttu-id="26ef4-171">이후 릴리스에서이 마이그레이션 프로세스를 간소화 하기 위해 수행할 수 있는 작업을 설명 하는 [이 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="26ef4-171">(See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) which covers work that can be done to simplify this migration process in a future release)</span></span>

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a><span data-ttu-id="26ef4-172">Unity 자산 파일에서 혼합 현실 기능 도구로 전환</span><span class="sxs-lookup"><span data-stu-id="26ef4-172">Switching from Unity asset files to Mixed Reality Feature Tool</span></span>

<span data-ttu-id="26ef4-173">Unity 자산 파일에서 혼합 현실 기능 도구 패키지로 전환 하면 다음과 같은 여러 가지 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-173">Switching from Unity asset files to Mixed Reality Feature Tool packages brings a number of benefits:</span></span>

- <span data-ttu-id="26ef4-174">간편한 업데이트</span><span class="sxs-lookup"><span data-stu-id="26ef4-174">Easier updating</span></span>
- <span data-ttu-id="26ef4-175">컴파일 시간 단축</span><span class="sxs-lookup"><span data-stu-id="26ef4-175">Faster compile times</span></span>
- <span data-ttu-id="26ef4-176">Visual Studio 솔루션의 프로젝트 수 감소</span><span class="sxs-lookup"><span data-stu-id="26ef4-176">Fewer projects in the Visual Studio solution</span></span>

<span data-ttu-id="26ef4-177">혼합 현실 기능 도구를 사용 하도록 변경 하려면 일회성 수동 단계가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-177">Changing to using the Mixed Reality Feature Tool requires a one-time set of manual steps.</span></span>

1. <span data-ttu-id="26ef4-178">현재 프로젝트의 복사본을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-178">Save a copy of your current project.</span></span>
1. <span data-ttu-id="26ef4-179">Unity 닫기</span><span class="sxs-lookup"><span data-stu-id="26ef4-179">Close Unity</span></span>
1. <span data-ttu-id="26ef4-180">*자산* 폴더 내에서 다음 **mrtk** 폴더를 해당 .xml 파일과 함께 삭제 합니다. 프로젝트에 나열 된 모든 폴더가 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-180">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="26ef4-181">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="26ef4-181">MRTK/Core</span></span>
    - <span data-ttu-id="26ef4-182">MRTK/예제</span><span class="sxs-lookup"><span data-stu-id="26ef4-182">MRTK/Examples</span></span>
    - <span data-ttu-id="26ef4-183">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="26ef4-183">MRTK/Extensions</span></span>
    - <span data-ttu-id="26ef4-184">MRTK/공급자</span><span class="sxs-lookup"><span data-stu-id="26ef4-184">MRTK/Providers</span></span>
    - <span data-ttu-id="26ef4-185">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="26ef4-185">MRTK/SDK</span></span>
    - <span data-ttu-id="26ef4-186">MRTK/서비스</span><span class="sxs-lookup"><span data-stu-id="26ef4-186">MRTK/Services</span></span>
    - <span data-ttu-id="26ef4-187">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="26ef4-187">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="26ef4-188">MRTK 셰이더가 수정 된 경우 MRTK/StandardAssets 폴더를 삭제 하기 전에 로컬 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-188">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="26ef4-189">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="26ef4-189">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="26ef4-190">**MixedRealityToolkit** 폴더 또는 해당. i a 파일을 삭제 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="26ef4-190">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="26ef4-191">**라이브러리** 폴더를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-191">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="26ef4-192">Unity Collab와 같은 일부 Unity 도구는 구성 정보를 라이브러리 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-192">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="26ef4-193">이를 수행 하는 도구를 사용 하는 경우 먼저 라이브러리에서 도구의 데이터 폴더를 복사한 후 라이브러리를 다시 생성 한 후에 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-193">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="26ef4-194">Unity에서 프로젝트를 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-194">Re-open the project in Unity</span></span>

<span data-ttu-id="26ef4-195">이전 단계를 수행한 후 [혼합 현실 기능 도구](#mixed-reality-feature-tool) 를 실행 하 고 Mixed reality Toolkit의 원하는 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-195">Once the previous steps have been performed, run the [Mixed Reality Feature Tool](#mixed-reality-feature-tool) and import the desired version of the Mixed Reality Toolkit.</span></span>

## <a name="updating-230-to-240"></a><span data-ttu-id="26ef4-196">2.3.0를 2.4.0로 업데이트 하는 중</span><span class="sxs-lookup"><span data-stu-id="26ef4-196">Updating 2.3.0 to 2.4.0</span></span>

<span data-ttu-id="26ef4-197">[폴더 이름 바꾸기](#folder-renames-in-240) 
 [API 변경](#api-changes-in-240)</span><span class="sxs-lookup"><span data-stu-id="26ef4-197">[Folder renames](#folder-renames-in-240)
[API changes](#api-changes-in-240)</span></span>

### <a name="folder-renames-in-240"></a><span data-ttu-id="26ef4-198">2.4.0에서 폴더 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="26ef4-198">Folder renames in 2.4.0</span></span>

<span data-ttu-id="26ef4-199">MixedRealityToolkit 폴더의 이름이 변경 되 고 버전 2.4에서 공용 계층으로 이동 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-199">The MixedRealityToolkit folders have been renamed and moved into a common hierarchy in version 2.4.</span></span> <span data-ttu-id="26ef4-200">응용 프로그램에서 MRTK 리소스에 하드 코드 된 경로를 사용 하는 경우 다음 테이블에 따라 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-200">If an application uses hard coded paths to MRTK resources, they will need to be updated per the following table.</span></span>

| <span data-ttu-id="26ef4-201">이전 폴더</span><span class="sxs-lookup"><span data-stu-id="26ef4-201">Previous Folder</span></span> | <span data-ttu-id="26ef4-202">새 폴더</span><span class="sxs-lookup"><span data-stu-id="26ef4-202">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="26ef4-203">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="26ef4-203">MixedRealityToolkit</span></span> | <span data-ttu-id="26ef4-204">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="26ef4-204">MRTK/Core</span></span> |
| <span data-ttu-id="26ef4-205">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="26ef4-205">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="26ef4-206">MRTK/예제</span><span class="sxs-lookup"><span data-stu-id="26ef4-206">MRTK/Examples</span></span> |
| <span data-ttu-id="26ef4-207">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="26ef4-207">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="26ef4-208">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="26ef4-208">MRTK/Extensions</span></span> |
| <span data-ttu-id="26ef4-209">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="26ef4-209">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="26ef4-210">MRTK/공급자</span><span class="sxs-lookup"><span data-stu-id="26ef4-210">MRTK/Providers</span></span> |
| <span data-ttu-id="26ef4-211">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="26ef4-211">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="26ef4-212">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="26ef4-212">MRTK/SDK</span></span> |
| <span data-ttu-id="26ef4-213">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="26ef4-213">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="26ef4-214">MRTK/서비스</span><span class="sxs-lookup"><span data-stu-id="26ef4-214">MRTK/Services</span></span> |
| <span data-ttu-id="26ef4-215">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="26ef4-215">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="26ef4-216">MRTK/테스트</span><span class="sxs-lookup"><span data-stu-id="26ef4-216">MRTK/Tests</span></span> |
| <span data-ttu-id="26ef4-217">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="26ef4-217">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="26ef4-218">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="26ef4-218">MRTK/Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="26ef4-219">는 `MixedRealityToolkit.Generated` 고객이 생성 한 파일을 포함 하며 변경 되지 않은 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-219">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

### <a name="eye-gaze-setup-in-240"></a><span data-ttu-id="26ef4-220">2.4.0의 눈 응시 설정</span><span class="sxs-lookup"><span data-stu-id="26ef4-220">Eye gaze setup in 2.4.0</span></span>

<span data-ttu-id="26ef4-221">이 버전의 MRTK는 눈동자를 설정 하는 데 필요한 단계를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-221">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="26ef4-222">_' IsEyeTrackingEnabled '_ 확인란은 입력 포인터 프로필의 응시 설정에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-222">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="26ef4-223">이 확인란을 선택 하면 기본 head 기반 응시를 사용 하는 대신 눈에 맞는 응시를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-223">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="26ef4-224">이러한 변경 내용에 대 한 자세한 내용 및 눈 추적 설정에 대 한 전체 지침은 [눈 추적](../features/input/eye-tracking/eye-tracking-basic-setup.md) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="26ef4-224">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/input/eye-tracking/eye-tracking-basic-setup.md) article.</span></span>

### <a name="eye-gaze-pointer-behavior-in-240"></a><span data-ttu-id="26ef4-225">2.4.0의 아이 응시 포인터 동작</span><span class="sxs-lookup"><span data-stu-id="26ef4-225">Eye gaze pointer behavior in 2.4.0</span></span>

<span data-ttu-id="26ef4-226">아이 응시 기본 포인터 동작은 헤드 응시 기본 포인터 동작과 일치 하도록 수정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-226">The eye gaze default pointer behavior have been modified to match the head gaze default pointer behavior.</span></span> <span data-ttu-id="26ef4-227">손이 감지 되 면 눈에 주목 하는 포인터가 자동으로 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-227">An eye gaze pointer will automatically be suppressed once a hand is detected.</span></span> <span data-ttu-id="26ef4-228">"선택"을 말한 후 눈에 띄는 포인터가 다시 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-228">The eye gaze pointer will become visible again after saying "Select".</span></span>

<span data-ttu-id="26ef4-229">응시 및 직접에 대 한 자세한 내용은 [눈동자 및 실습](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) 문서에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-229">Details about gaze and hand setups can be found in the [eyes and hands](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) article.</span></span>

### <a name="api-changes-in-240"></a><span data-ttu-id="26ef4-230">2.4.0의 API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="26ef4-230">API changes in 2.4.0</span></span>

<span data-ttu-id="26ef4-231">**사용자 지정 컨트롤러 클래스**</span><span class="sxs-lookup"><span data-stu-id="26ef4-231">**Custom controller classes**</span></span>

<span data-ttu-id="26ef4-232">사용자 지정 컨트롤러 클래스는 이전에를 정의 해야 했습니다 `SetupDefaultInteractions(Handedness)` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-232">Custom controller classes previously had to define `SetupDefaultInteractions(Handedness)`.</span></span> <span data-ttu-id="26ef4-233">이 메서드는 사용 하는 매개 변수가 컨트롤러 클래스의 자체 사용과 중복 되기 때문에 2.4에서 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-233">This method has been made obsolete in 2.4, as the handedness parameter was redundant with the controller class' own handedness.</span></span> <span data-ttu-id="26ef4-234">새 메서드에 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-234">The new method has no parameters.</span></span> <span data-ttu-id="26ef4-235">또한 다 수의 컨트롤러 클래스는 동일한 방식으로 정의 `AssignControllerMappings(DefaultInteractions);` 되므로 () 전체 호출이로 리팩터링 되었으며 `BaseController` 필요 하지 않고 선택적인 재정의를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-235">Additionally, many controller classes defined this the same way (`AssignControllerMappings(DefaultInteractions);`), so the full call has been refactored down into `BaseController` and made an optional override instead of required.</span></span>

<span data-ttu-id="26ef4-236">**아이 응시 속성**</span><span class="sxs-lookup"><span data-stu-id="26ef4-236">**Eye Gaze properties**</span></span>

<span data-ttu-id="26ef4-237">`UseEyeTracking` `GazeProvider` 의 구현에서 속성이 `IMixedRealityEyeGazeProvider` 로 바뀌었습니다 `IsEyeTrackingEnabled` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-237">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="26ef4-238">이전에 수행한 경우</span><span class="sxs-lookup"><span data-stu-id="26ef4-238">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="26ef4-239">지금이 작업 수행 ...</span><span class="sxs-lookup"><span data-stu-id="26ef4-239">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="26ef4-240">**WindowsApiChecker 속성**</span><span class="sxs-lookup"><span data-stu-id="26ef4-240">**WindowsApiChecker properties**</span></span>

<span data-ttu-id="26ef4-241">다음 WindowsApiChecker 속성은 사용 되지 않는 것으로 표시 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-241">The following WindowsApiChecker properties have been marked as obsolete.</span></span> <span data-ttu-id="26ef4-242">`IsMethodAvailable`, 또는를 사용 하세요 `IsPropertyAvailable` `IsTypeAvailable` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-242">Please use `IsMethodAvailable`, `IsPropertyAvailable` or `IsTypeAvailable`.</span></span>

- <span data-ttu-id="26ef4-243">UniversalApiContractV8_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="26ef4-243">UniversalApiContractV8_IsAvailable</span></span>
- <span data-ttu-id="26ef4-244">UniversalApiContractV7_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="26ef4-244">UniversalApiContractV7_IsAvailable</span></span>
- <span data-ttu-id="26ef4-245">UniversalApiContractV6_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="26ef4-245">UniversalApiContractV6_IsAvailable</span></span>
- <span data-ttu-id="26ef4-246">UniversalApiContractV5_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="26ef4-246">UniversalApiContractV5_IsAvailable</span></span>
- <span data-ttu-id="26ef4-247">UniversalApiContractV4_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="26ef4-247">UniversalApiContractV4_IsAvailable</span></span>
- <span data-ttu-id="26ef4-248">UniversalApiContractV3_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="26ef4-248">UniversalApiContractV3_IsAvailable</span></span>

<span data-ttu-id="26ef4-249">이후 API 계약 버전의 WindowsApiChecker에는 속성을 추가할 계획이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-249">There are no plans to add properties to WindowsApiChecker for future API contract versions.</span></span>

<span data-ttu-id="26ef4-250">**GltfMeshPrimitiveAttributes 읽기 전용**</span><span class="sxs-lookup"><span data-stu-id="26ef4-250">**GltfMeshPrimitiveAttributes read-only**</span></span>

<span data-ttu-id="26ef4-251">설정 가능 하 게 하는 데 사용 되는, 이제는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-251">The gltf mesh primitive attributes used to be settable, they are now read-only.</span></span> <span data-ttu-id="26ef4-252">해당 값은 deserialize 될 때 한 번 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-252">Their values will be set once when deserialized.</span></span>

### <a name="custom-button-icon-migration"></a><span data-ttu-id="26ef4-253">사용자 지정 단추 아이콘 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="26ef4-253">Custom Button Icon Migration</span></span>

<span data-ttu-id="26ef4-254">이전 사용자 지정 단추 아이콘은 단추의 쿼드 렌더러에 새 재질을 할당 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-254">Previously custom button icons required assigning a new material to the button's quad renderer.</span></span> <span data-ttu-id="26ef4-255">이는 더 이상 필요 하지 않으며 사용자 지정 아이콘 질감을 IconSet 이동 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-255">This is no longer necessary and we recommend moving custom icon textures into an IconSet.</span></span> <span data-ttu-id="26ef4-256">기존 사용자 지정 자료 및 아이콘은 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-256">Existing custom materials and icons are preserved.</span></span> <span data-ttu-id="26ef4-257">그러나 업그레이드 될 때까지 최적화가 더 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-257">However they will be less optimal until upgraded.</span></span>
<span data-ttu-id="26ef4-258">프로젝트의 모든 단추에 대 한 자산을 새 권장 형식으로 업그레이드 하려면 ButtonConfigHelperMigrationHandler를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-258">To upgrade the assets on all buttons in the project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="26ef4-259">(혼합 현실 도구 키트-> 유틸리티-> 마이그레이션 창-> 마이그레이션 처리기 선택-> MixedReality)</span><span class="sxs-lookup"><span data-stu-id="26ef4-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

![업그레이드 창 대화 상자](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="26ef4-261">마이그레이션 중에 기본 아이콘 집합에 아이콘이 없으면 사용자 지정 아이콘 집합이 MixedRealityToolkit/CustomIconSets에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-261">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="26ef4-262">이 작업이 수행 되었음을 나타내는 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-262">A dialog will indicate that this has taken place.</span></span>

![사용자 지정 아이콘 알림](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a><span data-ttu-id="26ef4-264">2.2.0를 2.3.0로 업데이트 하는 중</span><span class="sxs-lookup"><span data-stu-id="26ef4-264">Updating 2.2.0 to 2.3.0</span></span>

- [<span data-ttu-id="26ef4-265">API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="26ef4-265">API changes</span></span>](#api-changes-in-230)

### <a name="api-changes-in-230"></a><span data-ttu-id="26ef4-266">2.3.0의 API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="26ef4-266">API changes in 2.3.0</span></span>

<span data-ttu-id="26ef4-267">**ControllerPoseSynchronizer**</span><span class="sxs-lookup"><span data-stu-id="26ef4-267">**ControllerPoseSynchronizer**</span></span>

<span data-ttu-id="26ef4-268">비공개 ControllerPoseSynchronizer 필드는 사용 되지 않는 것으로 표시 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-268">The private ControllerPoseSynchronizer.handedness field has been marked as obsolete.</span></span> <span data-ttu-id="26ef4-269">이는 필드가 클래스 외부에 표시 되지 않기 때문에 응용 프로그램에 대 한 영향을 최소화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-269">This should have minimal impact on applications as the field is not visible outside of its class.</span></span>

<span data-ttu-id="26ef4-270">Public ControllerPoseSynchronizer 속성의 setter가 제거 되었습니다 ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span><span class="sxs-lookup"><span data-stu-id="26ef4-270">The public ControllerPoseSynchronizer.Handedness property's setter has been removed ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span></span>

<span data-ttu-id="26ef4-271">**Unity 용 MSBuild**</span><span class="sxs-lookup"><span data-stu-id="26ef4-271">**MSBuild for Unity**</span></span>

<span data-ttu-id="26ef4-272">이 버전의 MRTK는 이전 릴리스 보다 최신 버전의 Unity 용 MSBuild를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-272">This version of MRTK uses a newer version of MSBuild for Unity than previous releases.</span></span> <span data-ttu-id="26ef4-273">프로젝트를 로드 하는 동안 Unity 패키지 관리자 매니페스트에 이전 버전이 나열 되어 있으면 Unity에 MSBuild 사용 옵션을 선택 하 여 구성 대화 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-273">During project load, if the older version is listed in the Unity Package Manger manifest, the configuration dialog will appear, with the Enable MSBuild for Unity option checked.</span></span> <span data-ttu-id="26ef4-274">를 적용 하면 업그레이드가 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-274">Applying will perform an upgrade.</span></span>

<span data-ttu-id="26ef4-275">**ScriptingUtilities**</span><span class="sxs-lookup"><span data-stu-id="26ef4-275">**ScriptingUtilities**</span></span>

<span data-ttu-id="26ef4-276">ScriptingUtilities 클래스는 사용 되지 않는 것으로 표시 되었으며 MixedReality 어셈블리에서 ScriptUtilities로 대체 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-276">The ScriptingUtilities class has been marked as obsolete and has been replaced by ScriptUtilities, in the Microsoft.MixedReality.Toolkit.Editor.Utilities assembly.</span></span> <span data-ttu-id="26ef4-277">새 클래스는 이전 동작을 구체화 하 고 스크립팅 정의 제거에 대 한 지원을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-277">The new class refines previous behavior and adds support for removing scripting definitions.</span></span>

<span data-ttu-id="26ef4-278">기존 코드는 버전 2.3.0에서 계속 작동 하지만 새 클래스로 업데이트 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-278">While existing code will continue to function in version 2.3.0, it is recommended to update to the new class.</span></span>

<span data-ttu-id="26ef4-279">**ShellHandRayPointer**</span><span class="sxs-lookup"><span data-stu-id="26ef4-279">**ShellHandRayPointer**</span></span>

<span data-ttu-id="26ef4-280">ShellHandRayPointer 클래스의 lineRendererSelected 및 lineRendererNoTarget 멤버는 각각 lineMaterialSelected 및 lineMaterialNoTarget로 대체 되었습니다 ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span><span class="sxs-lookup"><span data-stu-id="26ef4-280">The lineRendererSelected and lineRendererNoTarget members of the ShellHandRayPointer class have been replaced by lineMaterialSelected and lineMaterialNoTarget, respectively ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span></span>

<span data-ttu-id="26ef4-281">컴파일 오류를 해결 하려면 lineRendererSelected를 lineMaterialSelected 및/또는 lineRendererNoTarget와 lineMaterialNoTarget로 바꾸세요.</span><span class="sxs-lookup"><span data-stu-id="26ef4-281">Please replace lineRendererSelected with lineMaterialSelected and/or lineRendererNoTarget with lineMaterialNoTarget to resolve compile errors.</span></span>

<span data-ttu-id="26ef4-282">**공간 관찰자 StartupBehavior**</span><span class="sxs-lookup"><span data-stu-id="26ef4-282">**Spatial observer StartupBehavior**</span></span>

<span data-ttu-id="26ef4-283">이제 클래스를 기반으로 하는 공간 관찰자가 `BaseSpatialObserver` 다시 활성화 될 때 ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)) startupbehavior 값을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-283">Spatial observers built upon the `BaseSpatialObserver` class now honor the value of StartupBehavior when re-enabled ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span></span>

<span data-ttu-id="26ef4-284">이 픽스를 활용 하는 데 필요한 변경 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-284">No changes are required to take advantage of this fix.</span></span>

<span data-ttu-id="26ef4-285">**UX 컨트롤 prefabs가 보도를 사용 하도록 업데이트 되었습니다.**</span><span class="sxs-lookup"><span data-stu-id="26ef4-285">**UX control prefabs updated to use PressableButton**</span></span>

<span data-ttu-id="26ef4-286">다음 prefabs는 거의 상호 작용 ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))에 TouchHandler 대신 보도 Sablebutton 구성 요소를 사용 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-286">The following prefabs are now using the PressableButton component instead of TouchHandler for near interaction ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span></span>

- <span data-ttu-id="26ef4-287">애니메이션 단추</span><span class="sxs-lookup"><span data-stu-id="26ef4-287">AnimationButton</span></span>
- <span data-ttu-id="26ef4-288">단추</span><span class="sxs-lookup"><span data-stu-id="26ef4-288">Button</span></span>
- <span data-ttu-id="26ef4-289">ButtonHoloLens1</span><span class="sxs-lookup"><span data-stu-id="26ef4-289">ButtonHoloLens1</span></span>
- <span data-ttu-id="26ef4-290">ButtonHoloLens1Toggle</span><span class="sxs-lookup"><span data-stu-id="26ef4-290">ButtonHoloLens1Toggle</span></span>
- <span data-ttu-id="26ef4-291">CheckBox</span><span class="sxs-lookup"><span data-stu-id="26ef4-291">CheckBox</span></span>
- <span data-ttu-id="26ef4-292">RadialSet</span><span class="sxs-lookup"><span data-stu-id="26ef4-292">RadialSet</span></span>
- <span data-ttu-id="26ef4-293">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="26ef4-293">ToggleButton</span></span>
- <span data-ttu-id="26ef4-294">ToggleSwitch</span><span class="sxs-lookup"><span data-stu-id="26ef4-294">ToggleSwitch</span></span>
- <span data-ttu-id="26ef4-295">UnityUIButton</span><span class="sxs-lookup"><span data-stu-id="26ef4-295">UnityUIButton</span></span>
- <span data-ttu-id="26ef4-296">UnityUICheckboxButton</span><span class="sxs-lookup"><span data-stu-id="26ef4-296">UnityUICheckboxButton</span></span>
- <span data-ttu-id="26ef4-297">UnityUIRadialButton</span><span class="sxs-lookup"><span data-stu-id="26ef4-297">UnityUIRadialButton</span></span>
- <span data-ttu-id="26ef4-298">UnityUIToggleButton</span><span class="sxs-lookup"><span data-stu-id="26ef4-298">UnityUIToggleButton</span></span>

<span data-ttu-id="26ef4-299">이 변경으로 인해 응용 프로그램 코드를 업데이트 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-299">Application code may require updating due to this change.</span></span>

<span data-ttu-id="26ef4-300">**WindowsMixedRealityUtilities 네임 스페이스**</span><span class="sxs-lookup"><span data-stu-id="26ef4-300">**WindowsMixedRealityUtilities namespace**</span></span>

<span data-ttu-id="26ef4-301">WindowsMixedRealityUtilities의 네임 스페이스는 MixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989))로 변경 되었습니다 (영문).</span><span class="sxs-lookup"><span data-stu-id="26ef4-301">The namespace of WindowsMixedRealityUtilities changed from Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input to Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span></span>

<span data-ttu-id="26ef4-302">컴파일 오류를 해결 하려면 #using 문을 업데이트 하세요.</span><span class="sxs-lookup"><span data-stu-id="26ef4-302">Please update #using statements to resolve compile errors.</span></span>

## <a name="updating-210-to-220"></a><span data-ttu-id="26ef4-303">2.1.0를 2.2.0로 업데이트 하는 중</span><span class="sxs-lookup"><span data-stu-id="26ef4-303">Updating 2.1.0 to 2.2.0</span></span>

- [<span data-ttu-id="26ef4-304">API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="26ef4-304">API changes</span></span>](#api-changes-in-220)

### <a name="api-changes-in-220"></a><span data-ttu-id="26ef4-305">2.2.0의 API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="26ef4-305">API changes in 2.2.0</span></span>

<span data-ttu-id="26ef4-306">**IMixedRealityBoundarySystem**</span><span class="sxs-lookup"><span data-stu-id="26ef4-306">**IMixedRealityBoundarySystem.Contains**</span></span>

<span data-ttu-id="26ef4-307">이 메서드는 이전에 특정 Unity 정의 실험적 열거형에서 수행 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-307">This method previously took in a specific, Unity-defined experimental enum.</span></span> <span data-ttu-id="26ef4-308">이제 Unity 열거와 동일한 MRTK 정의 열거형을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-308">It now takes in an MRTK-defined enum that's identical to the Unity enum.</span></span> <span data-ttu-id="26ef4-309">이렇게 변경 하면 Unity의 이후 경계 Api에 대해 MRTK를 준비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-309">This change helps prepare the MRTK for Unity's future boundary APIs.</span></span>

<span data-ttu-id="26ef4-310">**MixedRealityServiceProfileAttribute**</span><span class="sxs-lookup"><span data-stu-id="26ef4-310">**MixedRealityServiceProfileAttribute**</span></span>

<span data-ttu-id="26ef4-311">프로필을 지 원하는 데 필요한 요구 사항을 더 잘 설명 하기 위해 MixedRealityServiceProfileAttribute은 제외 된 형식의 선택적 컬렉션을 추가 하도록 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-311">To better describe the requirements for supporting a profile, the MixedRealityServiceProfileAttribute has been updated to add an optional collection of excluded types.</span></span> <span data-ttu-id="26ef4-312">이 변경의 일부로 ServiceType 속성이 형식에서 형식 []으로 변경 되 고 이름이 RequiredTypes로 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-312">As part of this change, the ServiceType property has been changed from Type to Type[] and been renamed to RequiredTypes.</span></span>

<span data-ttu-id="26ef4-313">두 번째 속성인 ExcludedTypes도 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-313">A second property, ExcludedTypes has also been added.</span></span>

## <a name="updating-200-to-210"></a><span data-ttu-id="26ef4-314">2.0.0를 2.1.0로 업데이트 하는 중</span><span class="sxs-lookup"><span data-stu-id="26ef4-314">Updating 2.0.0 to 2.1.0</span></span>

- [<span data-ttu-id="26ef4-315">API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="26ef4-315">API changes</span></span>](#api-changes-in-210)
- [<span data-ttu-id="26ef4-316">프로필 변경</span><span class="sxs-lookup"><span data-stu-id="26ef4-316">Profile changes</span></span>](#profile-changes-in-210)

### <a name="api-changes-in-210"></a><span data-ttu-id="26ef4-317">2.1.0의 API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="26ef4-317">API changes in 2.1.0</span></span>

<span data-ttu-id="26ef4-318">**BaseNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="26ef4-318">**BaseNearInteractionTouchable**</span></span>

<span data-ttu-id="26ef4-319">`BaseNearInteractionTouchable`가 메서드를 가상으로 표시 하도록 수정 되었습니다 `OnValidate` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-319">The `BaseNearInteractionTouchable` has been modified to mark the `OnValidate` method as virtual.</span></span> <span data-ttu-id="26ef4-320">를 확장 하는 클래스 `BaseNearInteractionTouchable` (예: `NearInteractionTouchableUnityUI` )가이 변경 내용을 반영 하도록 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-320">Classes that extend `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI`) have been updated to reflect this change.</span></span>

<span data-ttu-id="26ef4-321">**ColliderNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="26ef4-321">**ColliderNearInteractionTouchable**</span></span>

<span data-ttu-id="26ef4-322">`ColliderNearInteractionTouchable` 클래스는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-322">The `ColliderNearInteractionTouchable` class has been deprecated.</span></span> <span data-ttu-id="26ef4-323">사용할 코드 참조를 업데이트 하십시오 `BaseNearInteractionTouchable` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-323">Please update code references to use `BaseNearInteractionTouchable`.</span></span>

<span data-ttu-id="26ef4-324">**IMixedRealityMouseDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="26ef4-324">**IMixedRealityMouseDeviceManager**</span></span>

<span data-ttu-id="26ef4-325">**_강화_**</span><span class="sxs-lookup"><span data-stu-id="26ef4-325">**_Added_**</span></span>

<span data-ttu-id="26ef4-326">`IMixedRealityMouseDeviceManager``CursorSpeed`및 속성을 추가 했습니다 `WheelSpeed` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-326">`IMixedRealityMouseDeviceManager` has been added `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="26ef4-327">이러한 속성을 사용 하면 응용 프로그램에서 커서 및 휠의 속도를 각각 조정 하는 승수 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-327">These properties allow applications to specify a multiplier value by which the speed of the cursor and wheel, respectively will be scaled.</span></span>

<span data-ttu-id="26ef4-328">이는 주요 변경 내용 이며 기존 마우스 장치 관리자 구현을 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-328">This is a breaking change and requires existing mouse device manager implementations to be modified .</span></span>

>[!NOTE]
><span data-ttu-id="26ef4-329">이 변경 내용은 이전 버전과 호환 되지 않습니다. 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="26ef4-329">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="26ef4-330">**_Mapi_**</span><span class="sxs-lookup"><span data-stu-id="26ef4-330">**_Deprecated_**</span></span>

<span data-ttu-id="26ef4-331">`MouseInputProfile`속성은 더 이상 사용 되지 않는 것으로 표시 되었으며 이후 버전의 Microsoft Mixed Reality Toolkit에서 제거 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-331">The `MouseInputProfile` property has been marked as obsolete and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="26ef4-332">응용 프로그램 코드에서이 속성을 더 이상 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-332">It is recommended that application code no longer use this property.</span></span>

<span data-ttu-id="26ef4-333">**상호 작용 가능**</span><span class="sxs-lookup"><span data-stu-id="26ef4-333">**Interactable**</span></span>

<span data-ttu-id="26ef4-334">다음 메서드 및 속성은 더 이상 사용 되지 않으며 Microsoft Mixed Reality Toolkit의 이후 버전에서 제거 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-334">The following methods and properties have been deprecated and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="26ef4-335">사용 되지 않는 특성에 포함 되 고 콘솔에 표시 되는 지침에 따라 응용 프로그램 코드를 업데이트 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-335">The recommendation is to update application code per the guidance contained in the Obsolete attribute and displayed in the console.</span></span>

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

<span data-ttu-id="26ef4-336">**NearInteractionTouchableSurface**</span><span class="sxs-lookup"><span data-stu-id="26ef4-336">**NearInteractionTouchableSurface**</span></span>

<span data-ttu-id="26ef4-337">`NearInteractionTouchableSurface`클래스가 추가 되었으며 이제 및의 기본 클래스로 사용 `NearInteractionTouchable` `NearInteractionTouchableUnityUI` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-337">The `NearInteractionTouchableSurface` class has been added and now serves as the base class for `NearInteractionTouchable` and `NearInteractionTouchableUnityUI`.</span></span>

### <a name="profile-changes-in-210"></a><span data-ttu-id="26ef4-338">2.1.0의 프로필 변경 내용</span><span class="sxs-lookup"><span data-stu-id="26ef4-338">Profile changes in 2.1.0</span></span>

<span data-ttu-id="26ef4-339">**수동 추적 프로필**</span><span class="sxs-lookup"><span data-stu-id="26ef4-339">**Hand tracking profile**</span></span>

<span data-ttu-id="26ef4-340">손 모양 메시 및 조인트 시각화에는 이제 별도의 편집기 및 플레이어 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-340">The hand mesh and joint visualizations now have a separate editor and player settings.</span></span> <span data-ttu-id="26ef4-341">이 시각화를로 설정할 수 있도록 손 추적 프로필이 업데이트 되었습니다. 아무 것도, 모든 편집기 또는 플레이어입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-341">The hand tracking profile has been updated to allow for setting these visualizations to; Nothing, Everything, Editor or Player.</span></span>

![수동 시각화 모드](../release-notes/images/HandTrackingVisualizationModes.png)

<span data-ttu-id="26ef4-343">사용자 지정 수동 추적 프로필은 버전 2.1.0에서 제대로 작동 하도록 업데이트 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-343">Custom hand tracking profiles may need to be updated to work correctly with version 2.1.0.</span></span>

>[!NOTE]
><span data-ttu-id="26ef4-344">이 변경 내용은 이전 버전과 호환 되지 않습니다. 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="26ef4-344">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="26ef4-345">**입력 시뮬레이션 프로필**</span><span class="sxs-lookup"><span data-stu-id="26ef4-345">**Input simulation profile**</span></span>

<span data-ttu-id="26ef4-346">입력 시뮬레이션 시스템이 업그레이드 되어 입력 시뮬레이션 프로필에서 몇 가지 설정이 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-346">The input simulation system has been upgraded, which changes a few settings in the input simulation profile.</span></span> <span data-ttu-id="26ef4-347">일부 변경 내용은 자동으로 마이그레이션되지 않으며, 사용자가 프로필의 기본값 사용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-347">Some changes can not be migrated automatically and users may find that profiles are using default values.</span></span>

1. <span data-ttu-id="26ef4-348">프로필의 모든 KeyCode 및 마우스 단추 바인딩은 `KeyBinding` 바인딩 형식 (키 또는 마우스) 뿐만 아니라 실제 바인딩 코드 (각각 KeyCode 또는 마우스 단추 번호)를 저장 하는 제네릭 구조체로 대체 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-348">All KeyCode and mouse button bindings in the profile have been replaced with a generic `KeyBinding` struct, which stores the type of binding (key or mouse) as well as the actual binding code (KeyCode or mouse button number respectively).</span></span> <span data-ttu-id="26ef4-349">구조체에는 통합 표시를 허용 하는 자체 inspector가 있으며, 큰 드롭다운 목록에서 선택 하는 대신 각 키를 눌러 키 바인딩을 신속 하 게 설정 하는 "자동 바인딩" 도구를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-349">The struct has its own inspector, which allows unified display and offers an "auto-bind" tool to quickly set key bindings by pressing the respective key instead of selecting from a huge dropdown list.</span></span>

    - <span data-ttu-id="26ef4-350">FastControlKey</span><span class="sxs-lookup"><span data-stu-id="26ef4-350">FastControlKey</span></span>
    - <span data-ttu-id="26ef4-351">ToggleLeftHandKey</span><span class="sxs-lookup"><span data-stu-id="26ef4-351">ToggleLeftHandKey</span></span>
    - <span data-ttu-id="26ef4-352">ToggleRightHandKey</span><span class="sxs-lookup"><span data-stu-id="26ef4-352">ToggleRightHandKey</span></span>
    - <span data-ttu-id="26ef4-353">LeftHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="26ef4-353">LeftHandManipulationKey</span></span>
    - <span data-ttu-id="26ef4-354">RightHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="26ef4-354">RightHandManipulationKey</span></span>

1. <span data-ttu-id="26ef4-355">`MouseLookToggle` 는 이전에 `MouseLookButton` 와 같이 열거형에 포함 되었지만 `InputSimulationMouseButton.Focused` 이제는 별도의 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-355">`MouseLookToggle` was previously included in the `MouseLookButton` enum as `InputSimulationMouseButton.Focused`, it is now a separate option.</span></span> <span data-ttu-id="26ef4-356">사용 하도록 설정 되 면 카메라는 단추를 놓은 후에도 esc 키를 누를 때까지 마우스를 계속 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-356">When enabled, the camera will keep rotating with the mouse after releasing the button, until the escape key is pressed.</span></span>
1. <span data-ttu-id="26ef4-357">`HandDepthMultiplier` 입력 시뮬레이션의 일부 변경 내용을 수용할 수 있도록 기본값은 0.1에서 0.03로 낮아졌습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-357">`HandDepthMultiplier` default value has been lowered from 0.1 to 0.03 to accommodate some changes to the input simulation.</span></span> <span data-ttu-id="26ef4-358">스크롤할 때 카메라가 너무 빨리 이동 하는 경우이 값을 낮추어 보세요.</span><span class="sxs-lookup"><span data-stu-id="26ef4-358">If the camera moves too fast when scrolling, try lowering this value.</span></span>
1. <span data-ttu-id="26ef4-359">회전 하는 데 사용할 키가 제거 되었습니다. 이제 직접 회전이 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-359">Keys for rotating hands have been removed, hand rotation is now controlled by the mouse as well.</span></span> <span data-ttu-id="26ef4-360">`HandRotateButton`왼쪽/오른쪽 조작 키 (LShift/Space)와 함께 (Ctrl)를 누르고 있으면 직접 회전이 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-360">Holding `HandRotateButton` (Ctrl) together with the left/right hand manipulation key (LShift/Space) will enable hand rotation.</span></span>
1. <span data-ttu-id="26ef4-361">새 축 "스핀"가 입력 축 목록에 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-361">A new axis "UpDown" has been introduced to the input axis list.</span></span> <span data-ttu-id="26ef4-362">이는 세로에서 카메라 이동 및 컨트롤러 트리거 단추 뿐만 아니라 Q/E 키에 대 한 기본값을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-362">This controls camera movement in the vertical and defaults to Q/E keys as well as the controller trigger buttons.</span></span>

<span data-ttu-id="26ef4-363">이러한 변경 내용에 대 한 자세한 내용은 [입력 시뮬레이션 서비스](../features/input-simulation/input-simulation-service.md) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="26ef4-363">For more information on these changes, please see the [input simulation service](../features/input-simulation/input-simulation-service.md) article.</span></span>

<span data-ttu-id="26ef4-364">**마우스 데이터 공급자 프로필**</span><span class="sxs-lookup"><span data-stu-id="26ef4-364">**Mouse data provider profile**</span></span>

<span data-ttu-id="26ef4-365">마우스 데이터 공급자 프로필이 새 및 속성을 노출 하도록 업데이트 되었습니다 `CursorSpeed` `WheelSpeed` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-365">The mouse data provider profile has been updated to expose the new `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="26ef4-366">기존 사용자 지정 프로필의 기본값은 자동으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-366">Existing custom profiles will automatically have default values provided.</span></span> <span data-ttu-id="26ef4-367">프로필을 저장 하면 이러한 새 값이 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-367">When the profile is saved, these new values will be persisted.</span></span>

<span data-ttu-id="26ef4-368">**컨트롤러 매핑 프로필**</span><span class="sxs-lookup"><span data-stu-id="26ef4-368">**Controller mapping profile**</span></span>

<span data-ttu-id="26ef4-369">일부 축 및 입력 유형은 2.1.0에서 업데이트 되었으며, 특히 OpenVR 플랫폼을 중심으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-369">Some axes and input types have been updated in 2.1.0, especially around the OpenVR platform.</span></span> <span data-ttu-id="26ef4-370">업그레이드할 때 **MixedRealityToolkit-> 유틸리티-> 업데이트-> 컨트롤러 매핑 프로필** 을 선택 하십시오.</span><span class="sxs-lookup"><span data-stu-id="26ef4-370">Please be sure to select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** when upgrading.</span></span> <span data-ttu-id="26ef4-371">이렇게 하면 사용자 지정 된 입력 동작을 그대로 유지 하면서 업데이트 된 축 및 데이터를 사용 하 여 사용자 지정 컨트롤러 매핑 프로필을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-371">This will update any custom Controller Mapping Profiles with the updated axes and data, while leaving your custom-assigned input actions intact.</span></span>

## <a name="updating-rc2-to-200"></a><span data-ttu-id="26ef4-372">2.0.0에 RC2 업데이트</span><span class="sxs-lookup"><span data-stu-id="26ef4-372">Updating RC2 to 2.0.0</span></span>

<span data-ttu-id="26ef4-373">Microsoft Mixed Reality Toolkit의 RC2 및 2.0.0 릴리스 사이에 기존 프로젝트에 영향을 줄 수 있는 변경 내용이 적용 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-373">Between the RC2 and 2.0.0 releases of the Microsoft Mixed Reality Toolkit, changes were made that may impact existing projects.</span></span> <span data-ttu-id="26ef4-374">이 문서에서는 이러한 변경 내용과 프로젝트를 2.0.0 릴리스에 업데이트 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-374">This document describes those changes and how to update projects to the 2.0.0 release.</span></span>

- [<span data-ttu-id="26ef4-375">API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="26ef4-375">API changes</span></span>](#api-changes-in-200)
- [<span data-ttu-id="26ef4-376">어셈블리 이름 변경</span><span class="sxs-lookup"><span data-stu-id="26ef4-376">Assembly name changes</span></span>](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a><span data-ttu-id="26ef4-377">2.0.0의 API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="26ef4-377">API changes in 2.0.0</span></span>

<span data-ttu-id="26ef4-378">R c 2의 릴리스 이후 기존 프로젝트를 중단할 수 있는 몇 가지 API 변경 내용이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-378">Since the release of RC2, there have been a number of API changes including some that may break existing projects.</span></span> <span data-ttu-id="26ef4-379">다음 섹션에서는 RC2 및 2.0.0 릴리스 간에 발생 한 변경 사항을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-379">The following sections describe the changes that have occurred between the RC2 and 2.0.0 releases.</span></span>

<span data-ttu-id="26ef4-380">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="26ef4-380">**MixedRealityToolkit**</span></span>

<span data-ttu-id="26ef4-381">MixedRealityToolkit 개체의 다음 공용 속성은 더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-381">The following public properties on the MixedRealityToolkit object have been deprecated.</span></span>

- <span data-ttu-id="26ef4-382">`RegisteredMixedRealityServices` 에는 더 이상 등록 된 확장 서비스 및 데이터 공급자의 컬렉션이 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-382">`RegisteredMixedRealityServices` no longer contains the collection of registered extensions services and data providers.</span></span>

<span data-ttu-id="26ef4-383">확장 서비스에 액세스 하려면를 사용 `MixedRealityServiceRegistry.TryGetService<T>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-383">To access extension services, use `MixedRealityServiceRegistry.TryGetService<T>`.</span></span> <span data-ttu-id="26ef4-384">데이터 공급자에 액세스 하려면 서비스 인스턴스를로 캐스팅 하 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 고를 사용 `GetDataProvider<T>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-384">To access data providers, cast the service instance to [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) and use `GetDataProvider<T>`.</span></span>

<span data-ttu-id="26ef4-385">다음의 사용 [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) 되지 않는 속성 대신 또는를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-385">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) or [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) instead for the following deprecated properties</span></span>

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

<span data-ttu-id="26ef4-386">**CoreServices**</span><span class="sxs-lookup"><span data-stu-id="26ef4-386">**CoreServices**</span></span>

<span data-ttu-id="26ef4-387">[`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices)클래스는 개체에 있는 정적 시스템 접근자 (예: BoundarySystem)를 대체 합니다 `MixedRealityToolkit` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-387">The [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) class is the replacement for the static system accessors (ex: BoundarySystem) found in the `MixedRealityToolkit` object.</span></span>

>[!IMPORTANT]
><span data-ttu-id="26ef4-388">`MixedRealityToolkit`시스템 접근자는 버전 2.0.0에서 더 이상 사용 되지 않으며 MRTK의 이후 릴리스에서 제거 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-388">The `MixedRealityToolkit` system accessors have been deprecated in version 2.0.0 and will be removed in a future release of the MRTK.</span></span>

<span data-ttu-id="26ef4-389">다음 코드 예제에서는 이전 패턴과 새 패턴을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-389">The following code example illustrates the old and the new pattern.</span></span>

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

<span data-ttu-id="26ef4-390">새 CoreSystem 클래스를 사용 하면 다른 서비스 등록자 (예: 실험적 서비스 관리자 중 하나)를 사용 하도록 응용 프로그램을 변경 하는 경우 응용 프로그램 코드를 업데이트할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-390">Using the new CoreSystem class will ensure that your application code will not need updating if you change the application to use a different service registrar (ex: one of the experimental service managers).</span></span>

<span data-ttu-id="26ef4-391">**IMixedRealityRaycastProvider**</span><span class="sxs-lookup"><span data-stu-id="26ef4-391">**IMixedRealityRaycastProvider**</span></span>

<span data-ttu-id="26ef4-392">IMixedRealityRaycastProvider 추가 하 여 입력 시스템 구성 프로필이 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-392">With the addition of the IMixedRealityRaycastProvider, the input system configuration profile was changed.</span></span> <span data-ttu-id="26ef4-393">사용자 지정 프로필이 있는 경우 응용 프로그램을 실행할 때 다음 이미지에 오류가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-393">If you have a custom profile, you may receive the errors in the following image when you run your application.</span></span>

![Raycast 공급자 1 선택](../release-notes/images/UnableToRegisterRaycastProvider.png)

<span data-ttu-id="26ef4-395">이러한 문제를 해결 하려면 입력 시스템 프로필에 IMixedRealityRaycastProvider 인스턴스를 추가 하세요.</span><span class="sxs-lookup"><span data-stu-id="26ef4-395">To fix these, please add an IMixedRealityRaycastProvider instance to your input system profile.</span></span>

![Raycast 공급자 2 선택](../release-notes/images/SelectRaycastProvider.png)

<span data-ttu-id="26ef4-397">**이벤트 시스템**</span><span class="sxs-lookup"><span data-stu-id="26ef4-397">**Event System**</span></span>

- <span data-ttu-id="26ef4-398">`IMixedRealityEventSystem`이전 API 메서드 `Register` 및는 `Unregister` 사용 되지 않는 것으로 표시 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-398">The `IMixedRealityEventSystem` old API methods `Register` and `Unregister` have been marked as obsolete.</span></span> <span data-ttu-id="26ef4-399">이전 버전과의 호환성을 위해 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-399">They are preserved for backwards compatibility.</span></span>
- <span data-ttu-id="26ef4-400">`InputSystemGlobalListener` 사용 되지 않는 것으로 표시 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-400">`InputSystemGlobalListener` has been marked as obsolete.</span></span> <span data-ttu-id="26ef4-401">해당 기능이 변경 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-401">Its functionality has not changed.</span></span>
- <span data-ttu-id="26ef4-402">`BaseInputHandler` 기본 클래스가에서로 변경 되었습니다 `InputSystemGlobalListener` `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-402">`BaseInputHandler` base class has been changed from `InputSystemGlobalListener` to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="26ef4-403">이는의 모든 하위 항목에 대 한 주요 변경 내용입니다 `BaseInputHandler` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-403">This is a breaking change for any descendants of `BaseInputHandler`.</span></span>

<span data-ttu-id="26ef4-404">**_변경 내용 뒤의 동기_**</span><span class="sxs-lookup"><span data-stu-id="26ef4-404">**_Motivation behind the change_**</span></span>

<span data-ttu-id="26ef4-405">이전 이벤트 시스템 API를 `Register` 통해 `Unregister` 런타임 시 여러 문제가 발생할 수 있습니다. 주는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-405">The old event system API `Register` and `Unregister` could potentially cause multiple issues in runtime, main being:</span></span>

- <span data-ttu-id="26ef4-406">구성 요소가 전역 이벤트를 등록 하는 경우 *모든* 형식의 전역 입력 이벤트를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-406">If a component registers for global events, it would receive global input events of *all* types.</span></span>
- <span data-ttu-id="26ef4-407">개체의 구성 요소 중 하나가 전역 입력 이벤트를 등록 하는 경우이 개체의 모든 구성 요소는 *모든* 형식의 전역 입력 이벤트를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-407">If one of the components on an object registers for global input events, all components on this object will receive global input events of *all* types.</span></span>
- <span data-ttu-id="26ef4-408">동일한 개체에 있는 두 구성 요소가 전역 이벤트에 등록 된 다음 런타임에 비활성화 되는 경우 두 번째 구성 요소는 글로벌 이벤트 수신을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-408">If two components on the same object register to global events, and then one is disabled in runtime, the second one stops receiving global events.</span></span>

<span data-ttu-id="26ef4-409">새 API `RegisterHandler` 및 `UnregisterHandler` :</span><span class="sxs-lookup"><span data-stu-id="26ef4-409">New API `RegisterHandler` and `UnregisterHandler`:</span></span>

- <span data-ttu-id="26ef4-410">지정 된 입력 이벤트를 전역적으로 수신 해야 하는 명확 하 고 세부적인 제어를 제공 하며,이를 중심으로 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-410">Provides an explicit and granular control over which input events should be listened to globally and which should be focused-based.</span></span>
- <span data-ttu-id="26ef4-411">동일한 개체의 여러 구성 요소가 전역 이벤트를 서로 독립적으로 수신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-411">Allows multiple components on the same object to listen to global events independently on each other.</span></span>

<span data-ttu-id="26ef4-412">**_마이그레이션 방법_**</span><span class="sxs-lookup"><span data-stu-id="26ef4-412">**_How to migrate_**</span></span>

- <span data-ttu-id="26ef4-413">`Register` / `Unregister` 이전에 API를 호출한 경우이 호출을 호출로 바꿉니다 `RegisterHandler` / `UnregisterHandler` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-413">If you have been calling `Register`/`Unregister` API directly before, replace these calls with calls to `RegisterHandler`/`UnregisterHandler`.</span></span> <span data-ttu-id="26ef4-414">제네릭 매개 변수로 구현 하는 처리기 인터페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-414">Use handler interfaces you implement as generic parameters.</span></span> <span data-ttu-id="26ef4-415">여러 인터페이스를 구현 하 고 여러 인터페이스에서 전역 입력 이벤트를 수신 하는 경우 `RegisterHandler` 여러 번 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-415">If you implement multiple interfaces, and several of them listen to global input events, call `RegisterHandler` multiple times.</span></span>
- <span data-ttu-id="26ef4-416">에서 상속 된 경우 `InputSystemGlobalListener` 상속을로 변경 `InputSystemGlobalHandlerListener` 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-416">If you have been inheriting from `InputSystemGlobalListener`, change inheritance to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="26ef4-417">`RegisterHandlers`및 `UnregisterHandlers` 추상 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-417">Implement `RegisterHandlers` and `UnregisterHandlers` abstract methods.</span></span> <span data-ttu-id="26ef4-418">구현 호출 `inputSystem.RegisterHandler` ()에서 `inputSystem.UnregisterHandler` 전역 이벤트를 수신 하려는 모든 처리기 인터페이스에 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-418">In the implementation call `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) to register on all handler interfaces you want to listen global events for.</span></span>
- <span data-ttu-id="26ef4-419">에서 상속 된 경우 `BaseInputHandler` `RegisterHandlers` 및 추상 메서드를 구현 `UnregisterHandlers` 합니다 .의 경우와 동일 `InputSystemGlobalListener` 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-419">If you have been inheriting from `BaseInputHandler`, implement `RegisterHandlers` and `UnregisterHandlers` abstract methods (same as for `InputSystemGlobalListener`).</span></span>

<span data-ttu-id="26ef4-420">**_마이그레이션의 예_**</span><span class="sxs-lookup"><span data-stu-id="26ef4-420">**_Examples of migration_**</span></span>

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

<span data-ttu-id="26ef4-421">**공간 인식**</span><span class="sxs-lookup"><span data-stu-id="26ef4-421">**Spatial Awareness**</span></span>

<span data-ttu-id="26ef4-422">IMixedRealitySpatialAwarenessSystem 및 IMixedRealitySpatialAwarenessObserver 인터페이스는 아래에 설명 된 대로 여러 가지 주요 변경 내용을 수행 했습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-422">The IMixedRealitySpatialAwarenessSystem and IMixedRealitySpatialAwarenessObserver interfaces have taken multiple breaking changes as described below.</span></span>

<span data-ttu-id="26ef4-423">**_변경_**</span><span class="sxs-lookup"><span data-stu-id="26ef4-423">**_Changes_**</span></span>

<span data-ttu-id="26ef4-424">다음 메서드는 사용에 대 한 더 나은 설명을 위해 이름이 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-424">The following method(s) have been renamed to better describe their usage.</span></span>

- <span data-ttu-id="26ef4-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` 의 `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` 사용법을 명확 하 게 하기 위해 이름이로 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` has been renamed to `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` to clarify its usage.</span></span>

<span data-ttu-id="26ef4-426">**_추가_**</span><span class="sxs-lookup"><span data-stu-id="26ef4-426">**_Additions_**</span></span>

<span data-ttu-id="26ef4-427">사용자 의견을 바탕으로 이전에 관찰 된 공간 인식 데이터를 쉽게 제거할 수 있는 지원이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-427">Based on customer feedback, support for easy removal of previously observed spatial awareness data has been added.</span></span>

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

<span data-ttu-id="26ef4-428">**해결기**</span><span class="sxs-lookup"><span data-stu-id="26ef4-428">**Solvers**</span></span>

<span data-ttu-id="26ef4-429">일부 해 찾기 구성 요소 및 SolverHandler manager 클래스는 다양 한 버그를 수정 하 고 보다 직관적인 사용을 위해 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-429">Some solver components and the SolverHandler manager class has changed to fix various bugs and for more intuitive usage.</span></span>

<span data-ttu-id="26ef4-430">**_SolverHandler_**</span><span class="sxs-lookup"><span data-stu-id="26ef4-430">**_SolverHandler_**</span></span>

- <span data-ttu-id="26ef4-431">클래스가 더 이상에서 확장 되지 않습니다. `ControllerFinder`</span><span class="sxs-lookup"><span data-stu-id="26ef4-431">Class no longer extends from `ControllerFinder`</span></span>
- <span data-ttu-id="26ef4-432">`TrackedObjectToReference` public 속성이 사용 되지 않으며로 이름이 변경 되었습니다. `TrackedTargetType`</span><span class="sxs-lookup"><span data-stu-id="26ef4-432">`TrackedObjectToReference` public property deprecated and has been renamed to `TrackedTargetType`</span></span>
- <span data-ttu-id="26ef4-433">`TrackedObjectType` 지지 left & right controller values입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-433">`TrackedObjectType` deprecates left & right controller values.</span></span> <span data-ttu-id="26ef4-434">대신 또는 값을 사용 하 `MotionController` `HandJoint` 고 새 속성을 업데이트 `TrackedHandedness` 하 여 추적을 왼쪽 또는 오른쪽 컨트롤러로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-434">Instead use `MotionController` or `HandJoint` values and update new `TrackedHandedness` property to limit tracking to left or right controller</span></span>

<span data-ttu-id="26ef4-435">**_를_**</span><span class="sxs-lookup"><span data-stu-id="26ef4-435">**_InBetween_**</span></span>

- <span data-ttu-id="26ef4-436">`TrackedObjectForSecondTransform` public 속성이 사용 되지 않으며로 이름이 변경 되었습니다. `SecondTrackedObjectType`</span><span class="sxs-lookup"><span data-stu-id="26ef4-436">`TrackedObjectForSecondTransform` public property deprecated and has been renamed to `SecondTrackedObjectType`</span></span>
- <span data-ttu-id="26ef4-437">`AttachSecondTransformToNewTrackedObject()` 는 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-437">`AttachSecondTransformToNewTrackedObject()` has been removed.</span></span> <span data-ttu-id="26ef4-438">해 찾기를 업데이트 하려면 공용 속성 (즉,</span><span class="sxs-lookup"><span data-stu-id="26ef4-438">To update the solver, modify the public properties (i.e</span></span> <span data-ttu-id="26ef4-439">`SecondTrackedObjectType`)</span><span class="sxs-lookup"><span data-stu-id="26ef4-439">`SecondTrackedObjectType`)</span></span>

<span data-ttu-id="26ef4-440">**_SurfaceMagnetism_**</span><span class="sxs-lookup"><span data-stu-id="26ef4-440">**_SurfaceMagnetism_**</span></span>

- <span data-ttu-id="26ef4-441">`MaxDistance` public 속성이 사용 되지 않으며로 이름이 변경 되었습니다. `MaxRaycastDistance`</span><span class="sxs-lookup"><span data-stu-id="26ef4-441">`MaxDistance` public property deprecated and has been renamed to `MaxRaycastDistance`</span></span>
- <span data-ttu-id="26ef4-442">`CloseDistance` public 속성이 사용 되지 않으며로 이름이 변경 되었습니다. `ClosestDistance`</span><span class="sxs-lookup"><span data-stu-id="26ef4-442">`CloseDistance` public property deprecated and has been renamed to `ClosestDistance`</span></span>
- <span data-ttu-id="26ef4-443">이제의 기본값 `RaycastDirectionMode` 은 `TrackedTargetForward` 추적 대상 변환 방향의 raycasts를 전달 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-443">Default value for `RaycastDirectionMode` is now `TrackedTargetForward` which raycasts in the direction of the tracked target transform forward</span></span>
- <span data-ttu-id="26ef4-444">`OrientationMode` 열거형 값 `Vertical` 및 `Full` 은 `TrackedTarget` 각각 및로 이름이 변경 되었습니다 `SurfaceNormal` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-444">`OrientationMode` enum values, `Vertical` and `Full`, have been renamed to `TrackedTarget` and `SurfaceNormal` respectively</span></span>
- <span data-ttu-id="26ef4-445">`KeepOrientationVertical` 연결 된 GameObject의 방향이 세로로 유지 되는지 여부를 제어 하기 위해 public 속성이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-445">`KeepOrientationVertical` public property has been added to control whether orientation of associated GameObject remains vertical</span></span>

<span data-ttu-id="26ef4-446">**단추**</span><span class="sxs-lookup"><span data-stu-id="26ef4-446">**Buttons**</span></span>

- <span data-ttu-id="26ef4-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 이제 `DistanceSpaceMode` 속성을 기본값으로 설정 했습니다 `Local` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) now has `DistanceSpaceMode` property set to `Local` as default.</span></span> <span data-ttu-id="26ef4-448">이를 통해 단추의 크기를 조정할 수 있습니다 (pressable).</span><span class="sxs-lookup"><span data-stu-id="26ef4-448">This allows buttons to be scaled while still be pressable</span></span>

<span data-ttu-id="26ef4-449">**자르기 구**</span><span class="sxs-lookup"><span data-stu-id="26ef4-449">**Clipping Sphere**</span></span>

<span data-ttu-id="26ef4-450">ClippingSphere 인터페이스가 ClippingBox 및 ClippingPlane에 있는 Api를 반영 하도록 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-450">The ClippingSphere interface has changed to mirror the APIs found in the ClippingBox and ClippingPlane.</span></span>

<span data-ttu-id="26ef4-451">ClippingSphere의 Radius 속성은 이제 변환 배율에 따라 암시적으로 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-451">The ClippingSphere's Radius property is now implicitly calculated based on the transform scale.</span></span> <span data-ttu-id="26ef4-452">개발자가 검사기에서 ClippingSphere의 반지름을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-452">Before developers would have to specify the radius of the ClippingSphere in the inspector.</span></span> <span data-ttu-id="26ef4-453">Radius를 변경 하려는 경우 일반적인 방법으로 변환의 변환 배율을 업데이트 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-453">If you want to change the radius, just update the transform scale of the transform as you normally would.</span></span>

<span data-ttu-id="26ef4-454">**NearInteractionTouchable 및 PokePointer**</span><span class="sxs-lookup"><span data-stu-id="26ef4-454">**NearInteractionTouchable and PokePointer**</span></span>

- <span data-ttu-id="26ef4-455">NearInteractionTouchable는 Unity UI 캔버스를 더 이상 접촉 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-455">NearInteractionTouchable does not handle Unity UI canvas touching any longer.</span></span> <span data-ttu-id="26ef4-456">NearInteractionTouchableUnityUI 클래스는 이제 Unity UI touchables에 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-456">The NearInteractionTouchableUnityUI class must be used for Unity UI touchables now.</span></span>
- <span data-ttu-id="26ef4-457">ColliderNearInteractionTouchable는 colliders을 기반으로 하는 touchables의 새로운 기본 클래스입니다. 즉, NearInteractionTouchableUnityUI을 제외한 모든 touchable입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-457">ColliderNearInteractionTouchable is the new base class for touchables based on colliders, i.e. every touchable except NearInteractionTouchableUnityUI.</span></span>
- <span data-ttu-id="26ef4-458">BaseNearInteractionTouchable 이동 되었으며 PokePointer로 이름이 변경 되었습니다. TouchableDistance이 거리 이며 PokePointer가 touchables와 상호 작용할 수 있는 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-458">BaseNearInteractionTouchable.DistFront has been moved and renamed to PokePointer.TouchableDistance This is the distance and which the PokePointer can interact with touchables.</span></span> <span data-ttu-id="26ef4-459">이전에는 각 touchable 자체의 최대 상호 작용 거리가 있지만 이제 PokePointer에 정의 되어 더 나은 최적화를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-459">Previously each touchable had its own maximum interaction distance, but now this is defined in the PokePointer which allows better optimization.</span></span>
- <span data-ttu-id="26ef4-460">BaseNearInteractionTouchable가 PokeThreshold로 이름이 변경 되었습니다. 그러면 PokeThreshold가 DebounceThreshold에 해당 하는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-460">BaseNearInteractionTouchable.DistBack has been renamed to PokeThreshold This makes it clear that PokeThreshold is the counterpart to DebounceThreshold.</span></span> <span data-ttu-id="26ef4-461">Touchable는 PokeThreshold가 교차 될 때 활성화 되 고 DebounceThreshold가 교차할 때 릴리스됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-461">A touchable is activated when the PokeThreshold is crossed, and released when DebounceThreshold is crossed.</span></span>

<span data-ttu-id="26ef4-462">**ReadOnlyAttribute**</span><span class="sxs-lookup"><span data-stu-id="26ef4-462">**ReadOnlyAttribute**</span></span>

<span data-ttu-id="26ef4-463">`Microsoft.MixedReality.Toolkit`네임 스페이스는, 및에 추가 되었습니다 `ReadOnlyAttribute` `BeginReadOnlyGroupAttribute` `EndReadOnlyGroupAttribute` .</span><span class="sxs-lookup"><span data-stu-id="26ef4-463">The `Microsoft.MixedReality.Toolkit` namespace has been added to `ReadOnlyAttribute`, `BeginReadOnlyGroupAttribute`, and `EndReadOnlyGroupAttribute`.</span></span>

<span data-ttu-id="26ef4-464">**Pointer클릭 처리기**</span><span class="sxs-lookup"><span data-stu-id="26ef4-464">**PointerClickHandler**</span></span>

<span data-ttu-id="26ef4-465">`PointerClickHandler` 클래스는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-465">The `PointerClickHandler` class has been deprecated.</span></span> <span data-ttu-id="26ef4-466">`PointerHandler`대신를 사용 해야 합니다 .이는 동일한 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-466">The `PointerHandler` should be used instead, it provides the same functionality.</span></span>

<span data-ttu-id="26ef4-467">**HoloLens clicker 지원**</span><span class="sxs-lookup"><span data-stu-id="26ef4-467">**HoloLens clicker support**</span></span>

<span data-ttu-id="26ef4-468">HoloLens clicker의 컨트롤러 매핑이 unhanded 되지 않도록 변경 되었습니다 [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) .</span><span class="sxs-lookup"><span data-stu-id="26ef4-468">The HoloLens clicker's controller mappings have changed from being an unhanded [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) to being an unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand).</span></span> <span data-ttu-id="26ef4-469">이를 고려 하 여 ControllerMapping 프로필을 처음 열 때 자동 업데이트 프로그램이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-469">To account for this, an automatic updater will run the first time you open your ControllerMapping profile.</span></span> <span data-ttu-id="26ef4-470">이 일회성 마이그레이션 단계를 트리거하기 위해 2.0.0로 업그레이드 한 후에는 한 번 이상 사용자 지정 프로필을 열어 보세요.</span><span class="sxs-lookup"><span data-stu-id="26ef4-470">Please open any custom profiles at least once after upgrading to 2.0.0 in order to trigger this one-time migration step.</span></span>

<span data-ttu-id="26ef4-471">**InteractableHighlight 표시**</span><span class="sxs-lookup"><span data-stu-id="26ef4-471">**InteractableHighlight**</span></span>

<span data-ttu-id="26ef4-472">`InteractableHighlight` 클래스는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-472">The `InteractableHighlight` class has been deprecated.</span></span> <span data-ttu-id="26ef4-473">`InteractableOnFocus`클래스 및 `FocusInteractableStates` 자산을 대신 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-473">The `InteractableOnFocus` class and `FocusInteractableStates` asset should be used instead.</span></span> <span data-ttu-id="26ef4-474">`Theme`에 대 한 새 자산을 만들려면 `InteractableOnFocus` 프로젝트 창을 마우스 오른쪽 단추로 클릭 하 고   >  *Mixed Reality Toolkit*  >  *Interactable*  >  *테마* 만들기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-474">To create a new `Theme` asset for the `InteractableOnFocus`, right click in the project window and select *Create* > *Mixed Reality Toolkit* > *Interactable* > *Theme*.</span></span>

<span data-ttu-id="26ef4-475">**HandInteractionPanZoom**</span><span class="sxs-lookup"><span data-stu-id="26ef4-475">**HandInteractionPanZoom**</span></span>

<span data-ttu-id="26ef4-476">`HandInteractionPanZoom` 입력 구성 요소가 아닌 UI 네임 스페이스로 이동 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-476">`HandInteractionPanZoom` has been moved to the UI namespace as it was not an input component.</span></span> <span data-ttu-id="26ef4-477">`HandPanEventData` 도이 네임 스페이스로 이동 되었으며 다른 UI 이벤트 데이터와 일치 하도록 간소화 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-477">`HandPanEventData` has also been moved into this namespace, and simplified to correspond with other UI event data.</span></span>

### <a name="assembly-name-changes-in-200"></a><span data-ttu-id="26ef4-478">2.0.0의 어셈블리 이름 변경</span><span class="sxs-lookup"><span data-stu-id="26ef4-478">Assembly name changes in 2.0.0</span></span>

<span data-ttu-id="26ef4-479">2.0.0 릴리스에서는 공식의 모든 공식 Reality Toolkit 어셈블리 이름 및 연결 된 어셈블리 정의 (. asmdef) 파일이 다음 패턴에 맞게 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-479">In The 2.0.0 release, all of the official Mixed Reality Toolkit assembly names and their associated assembly definition (.asmdef) files have been updated to fit the following pattern.</span></span>

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

<span data-ttu-id="26ef4-480">일부 경우에는 여러 어셈블리가 병합 되어 해당 콘텐츠의 더 나은 unity를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-480">In some instances, multiple assemblies have been merged to create better unity of their contents.</span></span> <span data-ttu-id="26ef4-481">프로젝트에서 사용자 지정. asmdef 파일을 사용 하는 경우 업데이트가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-481">If your project uses custom .asmdef files, they may require updating.</span></span>

<span data-ttu-id="26ef4-482">다음 표에서는 2.0.0 릴리스에 대 한 RC2 파일 이름을 매핑하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-482">The following tables describe how the RC2 .asmdef file names map to the 2.0.0 release.</span></span> <span data-ttu-id="26ef4-483">모든 어셈블리 이름은. asmdef 파일 이름과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-483">All assembly names match the .asmdef file name.</span></span>

<span data-ttu-id="26ef4-484">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="26ef4-484">**MixedRealityToolkit**</span></span>

| <span data-ttu-id="26ef4-485">RC2</span><span class="sxs-lookup"><span data-stu-id="26ef4-485">RC2</span></span> | <span data-ttu-id="26ef4-486">2.0.0</span><span class="sxs-lookup"><span data-stu-id="26ef4-486">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="26ef4-487">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="26ef4-487">MixedRealityToolkit.asmdef</span></span> | <span data-ttu-id="26ef4-488">MixedReality입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-488">Microsoft.MixedReality.Toolkit.asmdef</span></span> |
| <span data-ttu-id="26ef4-489">MixedRealityToolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="26ef4-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span></span> | <span data-ttu-id="26ef4-490">MixedReality. a s t. n a m e.</span><span class="sxs-lookup"><span data-stu-id="26ef4-490">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span></span> |
| <span data-ttu-id="26ef4-491">MixedRealityToolkit. c s t.</span><span class="sxs-lookup"><span data-stu-id="26ef4-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="26ef4-492">제거 됨, MixedReality를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-492">Removed, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="26ef4-493">MixedRealityToolkit. EditorClassExtensions (영문)</span><span class="sxs-lookup"><span data-stu-id="26ef4-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span></span> | <span data-ttu-id="26ef4-494">MixedReality. ClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="26ef4-494">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span></span>
| <span data-ttu-id="26ef4-495">MixedRealityToolkit를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-495">MixedRealityToolkit.Core.Inspectors.asmdef</span></span> | <span data-ttu-id="26ef4-496">MixedReality. m a t.</span><span class="sxs-lookup"><span data-stu-id="26ef4-496">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span></span> |
| <span data-ttu-id="26ef4-497">MixedRealityToolkit를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span></span> | <span data-ttu-id="26ef4-498">MixedReality. b a s e.</span><span class="sxs-lookup"><span data-stu-id="26ef4-498">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span></span> |
| <span data-ttu-id="26ef4-499">MixedRealityToolkit. UtilitiesAsync</span><span class="sxs-lookup"><span data-stu-id="26ef4-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span></span> | <span data-ttu-id="26ef4-500">MixedReality (영문).</span><span class="sxs-lookup"><span data-stu-id="26ef4-500">Microsoft.MixedReality.Toolkit.Async.asmdef</span></span> |
| <span data-ttu-id="26ef4-501">MixedRealityToolkit (영문).</span><span class="sxs-lookup"><span data-stu-id="26ef4-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="26ef4-502">MixedReality. a s t.</span><span class="sxs-lookup"><span data-stu-id="26ef4-502">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="26ef4-503">MixedRealityToolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="26ef4-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span></span> | <span data-ttu-id="26ef4-504">MixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="26ef4-504">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span></span> |
| <span data-ttu-id="26ef4-505">MixedRealityToolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="26ef4-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span></span> | <span data-ttu-id="26ef4-506">MixedReality. c s t. m a t.</span><span class="sxs-lookup"><span data-stu-id="26ef4-506">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span></span> |

<span data-ttu-id="26ef4-507">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="26ef4-507">**MixedRealityToolkit.Providers**</span></span>

| <span data-ttu-id="26ef4-508">RC2</span><span class="sxs-lookup"><span data-stu-id="26ef4-508">RC2</span></span> | <span data-ttu-id="26ef4-509">2.0.0</span><span class="sxs-lookup"><span data-stu-id="26ef4-509">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="26ef4-510">MixedRealityToolkit을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span></span> | <span data-ttu-id="26ef4-511">MixedReality. c s t. a s e.</span><span class="sxs-lookup"><span data-stu-id="26ef4-511">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span></span> |
| <span data-ttu-id="26ef4-512">MixedRealityToolkit. WindowsMixedReality.</span><span class="sxs-lookup"><span data-stu-id="26ef4-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span></span> | <span data-ttu-id="26ef4-513">MixedReality. WindowsMixedReality..</span><span class="sxs-lookup"><span data-stu-id="26ef4-513">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span></span> |
| <span data-ttu-id="26ef4-514">MixedRealityToolkit. WindowsVoiceInput.</span><span class="sxs-lookup"><span data-stu-id="26ef4-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span></span> | <span data-ttu-id="26ef4-515">MixedReality. WindowsVoiceInput..</span><span class="sxs-lookup"><span data-stu-id="26ef4-515">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span></span> |

<span data-ttu-id="26ef4-516">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="26ef4-516">**MixedRealityToolkit.Services**</span></span>

| <span data-ttu-id="26ef4-517">RC2</span><span class="sxs-lookup"><span data-stu-id="26ef4-517">RC2</span></span> | <span data-ttu-id="26ef4-518">2.0.0</span><span class="sxs-lookup"><span data-stu-id="26ef4-518">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="26ef4-519">MixedRealityToolkit. BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="26ef4-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span></span> | <span data-ttu-id="26ef4-520">MixedReality. BoundarySystem (영문)</span><span class="sxs-lookup"><span data-stu-id="26ef4-520">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span></span> |
| <span data-ttu-id="26ef4-521">MixedRealityToolkit. CameraSystem</span><span class="sxs-lookup"><span data-stu-id="26ef4-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span></span> | <span data-ttu-id="26ef4-522">MixedReality. CameraSystem (영문)</span><span class="sxs-lookup"><span data-stu-id="26ef4-522">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span></span> |
| <span data-ttu-id="26ef4-523">MixedRealityToolkit. DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="26ef4-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span></span> | <span data-ttu-id="26ef4-524">MixedReality. DiagnosticsSystem (영문)</span><span class="sxs-lookup"><span data-stu-id="26ef4-524">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span></span> |
| <span data-ttu-id="26ef4-525">MixedRealityToolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="26ef4-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span></span> | <span data-ttu-id="26ef4-526">MixedReality (영문). asmdef</span><span class="sxs-lookup"><span data-stu-id="26ef4-526">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span></span> |
| <span data-ttu-id="26ef4-527">MixedRealityToolkit. n a m e.</span><span class="sxs-lookup"><span data-stu-id="26ef4-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span></span> | <span data-ttu-id="26ef4-528">MixedReality. c o m a s.</span><span class="sxs-lookup"><span data-stu-id="26ef4-528">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span></span> |
| <span data-ttu-id="26ef4-529">MixedRealityToolkit. n a m e.</span><span class="sxs-lookup"><span data-stu-id="26ef4-529">MixedRealityToolkit.Services.InputSystem.asmdef</span></span> | <span data-ttu-id="26ef4-530">MixedReality. n a m e.</span><span class="sxs-lookup"><span data-stu-id="26ef4-530">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span></span> |
| <span data-ttu-id="26ef4-531">MixedRealityToolkit입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-531">MixedRealityToolkit.Services.Inspectors.asmdef</span></span> | <span data-ttu-id="26ef4-532">MixedReality. c o m. n a m e.</span><span class="sxs-lookup"><span data-stu-id="26ef4-532">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span></span> |
| <span data-ttu-id="26ef4-533">MixedRealityToolkit. SceneSystem</span><span class="sxs-lookup"><span data-stu-id="26ef4-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span></span> | <span data-ttu-id="26ef4-534">MixedReality. SceneSystem (영문)</span><span class="sxs-lookup"><span data-stu-id="26ef4-534">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span></span> |
| <span data-ttu-id="26ef4-535">MixedRealityToolkit. SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="26ef4-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span></span> | <span data-ttu-id="26ef4-536">MixedReality. SpatialAwarenessSystem (영문)</span><span class="sxs-lookup"><span data-stu-id="26ef4-536">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span></span> |
| <span data-ttu-id="26ef4-537">MixedRealityToolkit. TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="26ef4-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span></span> | <span data-ttu-id="26ef4-538">MixedReality. TeleportSystem (영문)</span><span class="sxs-lookup"><span data-stu-id="26ef4-538">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span></span> |

<span data-ttu-id="26ef4-539">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="26ef4-539">**MixedRealityToolkit.SDK**</span></span>

| <span data-ttu-id="26ef4-540">RC2</span><span class="sxs-lookup"><span data-stu-id="26ef4-540">RC2</span></span> | <span data-ttu-id="26ef4-541">2.0.0</span><span class="sxs-lookup"><span data-stu-id="26ef4-541">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="26ef4-542">MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="26ef4-542">MixedRealityToolkit.SDK.asmdef</span></span> | <span data-ttu-id="26ef4-543">MixedReality (영문).</span><span class="sxs-lookup"><span data-stu-id="26ef4-543">Microsoft.MixedReality.Toolkit.SDK.asmdef</span></span> |
| <span data-ttu-id="26ef4-544">MixedRealityToolkit입니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span></span> | <span data-ttu-id="26ef4-545">MixedReality. a s e.</span><span class="sxs-lookup"><span data-stu-id="26ef4-545">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span></span> |

<span data-ttu-id="26ef4-546">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="26ef4-546">**MixedRealityToolkit.Examples**</span></span>

| <span data-ttu-id="26ef4-547">RC2</span><span class="sxs-lookup"><span data-stu-id="26ef4-547">RC2</span></span> | <span data-ttu-id="26ef4-548">2.0.0</span><span class="sxs-lookup"><span data-stu-id="26ef4-548">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="26ef4-549">MixedRealityToolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="26ef4-549">MixedRealityToolkit.Examples.asmdef</span></span> | <span data-ttu-id="26ef4-550">MixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="26ef4-550">Microsoft.MixedReality.Toolkit.Examples.asmdef</span></span> |
| <span data-ttu-id="26ef4-551">MixedRealityToolkit를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="26ef4-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span></span> | <span data-ttu-id="26ef4-552">MixedReality. c. c. c.</span><span class="sxs-lookup"><span data-stu-id="26ef4-552">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span></span> |
| <span data-ttu-id="26ef4-553">MixedRealityToolkit.. m a t.</span><span class="sxs-lookup"><span data-stu-id="26ef4-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span></span> | <span data-ttu-id="26ef4-554">MixedReality.. m a t e.</span><span class="sxs-lookup"><span data-stu-id="26ef4-554">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span></span> |
| <span data-ttu-id="26ef4-555">MixedRealityToolkit. InspectorFields. asmdef</span><span class="sxs-lookup"><span data-stu-id="26ef4-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span></span> | <span data-ttu-id="26ef4-556">MixedReality. InspectorFields (영문)</span><span class="sxs-lookup"><span data-stu-id="26ef4-556">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span></span> |
| <span data-ttu-id="26ef4-557">MixedRealityToolkit. InspectorFields. m a t.</span><span class="sxs-lookup"><span data-stu-id="26ef4-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span></span> | <span data-ttu-id="26ef4-558">MixedReality. InspectorFields. m a t.</span><span class="sxs-lookup"><span data-stu-id="26ef4-558">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span></span> |
| <span data-ttu-id="26ef4-559">MixedRealityToolkit (영문). asmdef</span><span class="sxs-lookup"><span data-stu-id="26ef4-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span></span> | <span data-ttu-id="26ef4-560">MixedReality. a s t. a s t.</span><span class="sxs-lookup"><span data-stu-id="26ef4-560">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span></span> |