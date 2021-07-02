---
title: 이전 버전에서 업데이트
description: MRTK의 하위 버전에서 마이그레이션에 대한 설명서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 5a914d6408d346dac0bf6c683f401564e875f4d8
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175105"
---
# <a name="updating-from-earlier-versions"></a><span data-ttu-id="9e037-104">이전 버전에서 업데이트</span><span class="sxs-lookup"><span data-stu-id="9e037-104">Updating from earlier versions</span></span>

- [<span data-ttu-id="9e037-105">새 버전의 MRTK로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="9e037-105">Upgrading to a new version of MRTK</span></span>](#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="9e037-106">2.3.0 ~ 2.4.0</span><span class="sxs-lookup"><span data-stu-id="9e037-106">2.3.0 to 2.4.0</span></span>](#updating-230-to-240)
- [<span data-ttu-id="9e037-107">2.2.0 ~ 2.3.0</span><span class="sxs-lookup"><span data-stu-id="9e037-107">2.2.0 to 2.3.0</span></span>](#updating-220-to-230)
- [<span data-ttu-id="9e037-108">2.1.0 ~ 2.2.0</span><span class="sxs-lookup"><span data-stu-id="9e037-108">2.1.0 to 2.2.0</span></span>](#updating-210-to-220)
- [<span data-ttu-id="9e037-109">2.0.0 ~ 2.1.0</span><span class="sxs-lookup"><span data-stu-id="9e037-109">2.0.0 to 2.1.0</span></span>](#updating-200-to-210)
- [<span data-ttu-id="9e037-110">RC2에서 2.0.0으로</span><span class="sxs-lookup"><span data-stu-id="9e037-110">RC2 to 2.0.0</span></span>](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a><span data-ttu-id="9e037-111">현재 버전 찾기</span><span class="sxs-lookup"><span data-stu-id="9e037-111">Finding the current version</span></span> 

<span data-ttu-id="9e037-112">다음 지침에 따라 현재 사용 중인 MRTK 버전을 파악합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-112">Follow these instructions to figure out which version of the MRTK you're currently using:</span></span>

1. <span data-ttu-id="9e037-113">Unity에서 MRTK 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="9e037-113">Open your MRTK project in Unity</span></span>
2. <span data-ttu-id="9e037-114">Project 창에서 "MixedRealityToolkit" 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-114">Navigate to the "MixedRealityToolkit" folder in your Project window</span></span>
3. <span data-ttu-id="9e037-115">"Version"이라는 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-115">Open the file called "Version"</span></span>

<span data-ttu-id="9e037-116">위의 파일 및 폴더가 없으면 최신 버전의 MRTK에 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-116">If the file and folder above doesn't exist, you're on a newer version of the MRTK.</span></span> <span data-ttu-id="9e037-117">이 경우 다음을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-117">In that case, try the following:</span></span>

1. <span data-ttu-id="9e037-118">"Mixed Reality Toolkit Foundation" 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-118">Navigate to the "Mixed Reality Toolkit Foundation" folder</span></span>
2. <span data-ttu-id="9e037-119">"package.js켜기"를 클릭하여 Unity에서 미리 보기를 보거나 텍스트 편집기를 사용하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-119">Click on the "package.json" to see a preview in Unity or open it with a text editor</span></span>
3. <span data-ttu-id="9e037-120">"version:"이라는 단어가 있는 줄을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-120">Look for the line with the word "version:"</span></span> 

## <a name="upgrading-to-a-new-version-of-mrtk"></a><span data-ttu-id="9e037-121">새 버전의 MRTK로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="9e037-121">Upgrading to a new version of MRTK</span></span>

<span data-ttu-id="9e037-122">*MRTK 업데이트를 받은 후 [마이그레이션 도구를](../features/tools/migration-window.md) 실행하여* 사용되지 않은 구성 요소에서 자동 수정 및 업그레이드하고 주요 변경 내용에 맞게 조정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-122">*It is strongly recommended to run the [migration tool](../features/tools/migration-window.md) after getting the MRTK update* to auto-fix and upgrade from deprecated components and adjust to breaking changes.</span></span> <span data-ttu-id="9e037-123">마이그레이션 도구는 **도구** 패키지의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-123">The migration tool is part of the **Tools** package.</span></span>

<span data-ttu-id="9e037-124">아래 지침에서는 2.4.0에서 2.5.0으로 업그레이드 경로를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-124">The instructions below describe the 2.4.0 to 2.5.0 upgrade path.</span></span> <span data-ttu-id="9e037-125">프로젝트가 2.3.0 이하인 경우 [버전 간](#updating-230-to-240) 변경 내용을 읽어 업그레이드 경로를 이해하거나 이전 [릴리스의 지침을](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) 읽어 버전별 업그레이드를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-125">If your project is on 2.3.0 or earlier, read on to the changes [between versions](#updating-230-to-240) to understand the upgrade path, or read the previous [release's instructions](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) to do a version-by-version upgrade.</span></span>

### <a name="mixed-reality-feature-tool"></a><span data-ttu-id="9e037-126">Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="9e037-126">Mixed Reality Feature Tool</span></span>
<span data-ttu-id="9e037-127">MRTK를 최신 버전 MRTK로 업그레이드하는 가장 쉬운 방법은 [Mixed Reality 기능 도구를](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 사용하여 최신 패키지를 다운로드하고 Unity 프로젝트에 직접 로드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-127">The easiest way to upgrade MRTK to a newer version MRTK is by using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) to download the latest packages and load them directly to your Unity project.</span></span>

<span data-ttu-id="9e037-128">프로젝트에서 이전에 Unity 자산(.unitypackage) 파일을 사용한 경우 [다음 지침을 참조하세요.](#switching-from-unity-asset-files-to-mixed-reality-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="9e037-128">If the project previously used Unity asset (.unitypackage) files, please see [these instructions](#switching-from-unity-asset-files-to-mixed-reality-feature-tool).</span></span> 

### <a name="unity-asset-unitypackage-files"></a><span data-ttu-id="9e037-129">Unity 자산(.unitypackage) 파일</span><span class="sxs-lookup"><span data-stu-id="9e037-129">Unity asset (.unitypackage) files</span></span>

<span data-ttu-id="9e037-130">또 다른 업그레이드 경로는 MRTK Unity 패키지를 수동으로 다운로드하여 프로젝트에 적용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-130">Another upgrade path is to manually download MRTK Unity packages and apply them to your project.</span></span> <span data-ttu-id="9e037-131">아래 단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e037-131">See the steps below,</span></span>

1. <span data-ttu-id="9e037-132">업그레이드 단계의 어느 지점에서나 스네그를 적중하는 경우 현재 프로젝트의 복사본을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-132">Save a copy of your current project, in case you hit any snags at any point in the upgrade steps.</span></span>
1. <span data-ttu-id="9e037-133">Unity 닫기</span><span class="sxs-lookup"><span data-stu-id="9e037-133">Close Unity</span></span>
1. <span data-ttu-id="9e037-134">*Assets* 폴더 내에서 .meta 파일과 함께 다음 **MRTK** 폴더를 삭제합니다(프로젝트에 나열된 폴더가 모두 없을 수 있음).</span><span class="sxs-lookup"><span data-stu-id="9e037-134">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="9e037-135">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="9e037-135">MRTK/Core</span></span>
    - <span data-ttu-id="9e037-136">MRTK/예제</span><span class="sxs-lookup"><span data-stu-id="9e037-136">MRTK/Examples</span></span>
    - <span data-ttu-id="9e037-137">MRTK/확장</span><span class="sxs-lookup"><span data-stu-id="9e037-137">MRTK/Extensions</span></span>
    - <span data-ttu-id="9e037-138">MRTK/공급자</span><span class="sxs-lookup"><span data-stu-id="9e037-138">MRTK/Providers</span></span>
    - <span data-ttu-id="9e037-139">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="9e037-139">MRTK/SDK</span></span>
    - <span data-ttu-id="9e037-140">MRTK/서비스</span><span class="sxs-lookup"><span data-stu-id="9e037-140">MRTK/Services</span></span>
    - <span data-ttu-id="9e037-141">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="9e037-141">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="9e037-142">MRTK 셰이더를 수정한 경우 MRTK/StandardAssets 폴더를 삭제하기 전에 로컬 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-142">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="9e037-143">MRTK/도구</span><span class="sxs-lookup"><span data-stu-id="9e037-143">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="9e037-144">**MixedRealityToolkit.Generated** 폴더 또는 해당 .meta 파일을 삭제하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="9e037-144">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="9e037-145">**라이브러리** 폴더 삭제</span><span class="sxs-lookup"><span data-stu-id="9e037-145">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="9e037-146">Unity Collab과 같은 일부 Unity 도구는 라이브러리 폴더에 구성 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-146">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="9e037-147">이 작업을 수행하는 도구를 사용하는 경우 먼저 삭제하기 전에 라이브러리에서 도구의 데이터 폴더를 복사한 다음 라이브러리를 다시 생성한 후 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-147">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="9e037-148">Unity에서 프로젝트 다시 열기</span><span class="sxs-lookup"><span data-stu-id="9e037-148">Re-open the project in Unity</span></span>
1. <span data-ttu-id="9e037-149">새 Unity 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="9e037-149">Import the new unity packages</span></span>
    - <span data-ttu-id="9e037-150">Foundation - _이 패키지를 먼저 가져오기_</span><span class="sxs-lookup"><span data-stu-id="9e037-150">Foundation - _Import this package first_</span></span>
    - <span data-ttu-id="9e037-151">도구</span><span class="sxs-lookup"><span data-stu-id="9e037-151">Tools</span></span>
    - <span data-ttu-id="9e037-152">(선택 사항) 확장</span><span class="sxs-lookup"><span data-stu-id="9e037-152">(Optional) Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="9e037-153">추가 확장이 설치된 경우 다시 가져와야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-153">If additional extensions had been installed, they may need to be re-imported.</span></span>
    - <span data-ttu-id="9e037-154">(선택 사항) 예제</span><span class="sxs-lookup"><span data-stu-id="9e037-154">(Optional) Examples</span></span>
1. <span data-ttu-id="9e037-155">Unity를 닫고 **Library** 폴더를 삭제합니다(아래 참고를 먼저 읽어보세요!).</span><span class="sxs-lookup"><span data-stu-id="9e037-155">Close Unity and delete the **Library** folder (read the note below first!).</span></span> <span data-ttu-id="9e037-156">이 단계는 Unity에서 자산 데이터베이스를 새로 고치고 기존 사용자 지정 프로필을 조정하도록 강제하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-156">This step is necessary to force Unity to refresh its asset database and reconcile existing custom profiles.</span></span>
1. <span data-ttu-id="9e037-157">Unity를 시작하고 프로젝트의 각 장면에 대해</span><span class="sxs-lookup"><span data-stu-id="9e037-157">Launch Unity, and for each scene in the project</span></span>
    - <span data-ttu-id="9e037-158">계층에서 **MixedRealityToolkit** 및 **MixedRealityPlayspace(있는 경우)를** 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-158">Delete **MixedRealityToolkit** and **MixedRealityPlayspace**, if present, from the hierarchy.</span></span> <span data-ttu-id="9e037-159">그러면 기본 카메라가 삭제되지만 다음 단계에서 다시 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-159">This will delete the main camera, but it will be re-created in the next step.</span></span> <span data-ttu-id="9e037-160">주 카메라의 속성을 수동으로 변경한 경우 새 카메라가 만들어지면 수동으로 다시 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-160">If any properties of the main camera have been manually changed, these will have to be re-applied manually once the new camera is created.</span></span>
    - <span data-ttu-id="9e037-161">**MixedRealityToolkit -> 장면에 추가 및 구성을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-161">Select **MixedRealityToolkit -> Add to Scene and Configure**</span></span>
    - <span data-ttu-id="9e037-162">**MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles(한** 번만 수행) 선택 - 사용자 지정 할당 입력 작업을 그대로 유지하면서 업데이트된 축 및 데이터로 사용자 지정 컨트롤러 매핑 프로필을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-162">Select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (only needs to be done once)       - This will update any custom controller mapping profiles with updated axes and data, while leaving your custom-assigned input actions intact</span></span>
1. <span data-ttu-id="9e037-163">마이그레이션 [도구를](../features/tools/migration-window.md) 실행하고 *전체 Project* 도구를 실행하여 모든 코드가 최신 코드로 업데이트되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-163">Run the [migration tool](../features/tools/migration-window.md) and run the tool on the *Full Project* to ensure that all of your code is updated to the latest.</span></span>
   <span data-ttu-id="9e037-164">마이그레이션 창에는 각각 자체 실행해야 하는 다양한 마이그레이션 처리기가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-164">The migration window contains a number of different migration handlers, which must each be run on their own.</span></span> <span data-ttu-id="9e037-165">이 단계에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-165">This step involves:</span></span>
   - <span data-ttu-id="9e037-166">마이그레이션 처리기 선택 드롭다운에서 첫 번째 **마이그레이션 처리기를 선택합니다.**</span><span class="sxs-lookup"><span data-stu-id="9e037-166">Select the first migration handler from the **Migration Handler Selection** dropdown.</span></span>
   - <span data-ttu-id="9e037-167">"전체 Project" 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-167">Click the "Full Project" button.</span></span>
   - <span data-ttu-id="9e037-168">"마이그레이션할 전체 프로젝트 추가" 단추를 클릭합니다(마이그레이션할 개체에 대한 전체 프로젝트를 검색함).</span><span class="sxs-lookup"><span data-stu-id="9e037-168">Click the "Add full project for migration" button (this will scan the entire project for objects to migrate).</span></span>
   - <span data-ttu-id="9e037-169">마이그레이션 가능한 개체가 있는 경우 사용하도록 설정해야 하는 "마이그레이션" 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-169">Click the "Migrate" button which should be enabled if any migrateable objects were found.</span></span>
   - <span data-ttu-id="9e037-170">드롭다운 내의 각 마이그레이션 처리기에 대해 이전 세 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-170">Repeat the previous three steps for each of the migration handlers within the dropdown.</span></span>
     <span data-ttu-id="9e037-171">(향후 릴리스에서 이 마이그레이션 프로세스를 간소화하기 위해 수행할 수 있는 작업을 다루는 이 [문제를](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) 참조하세요.)</span><span class="sxs-lookup"><span data-stu-id="9e037-171">(See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) which covers work that can be done to simplify this migration process in a future release)</span></span>

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a><span data-ttu-id="9e037-172">Unity 자산 파일에서 Mixed Reality 기능 도구로 전환</span><span class="sxs-lookup"><span data-stu-id="9e037-172">Switching from Unity asset files to Mixed Reality Feature Tool</span></span>

<span data-ttu-id="9e037-173">Unity 자산 파일에서 Mixed Reality 기능 도구 패키지로 전환하면 다음과 같은 여러 가지 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-173">Switching from Unity asset files to Mixed Reality Feature Tool packages brings a number of benefits:</span></span>

- <span data-ttu-id="9e037-174">보다 쉽게 업데이트</span><span class="sxs-lookup"><span data-stu-id="9e037-174">Easier updating</span></span>
- <span data-ttu-id="9e037-175">컴파일 시간 단축</span><span class="sxs-lookup"><span data-stu-id="9e037-175">Faster compile times</span></span>
- <span data-ttu-id="9e037-176">Visual Studio 솔루션의 프로젝트 감소</span><span class="sxs-lookup"><span data-stu-id="9e037-176">Fewer projects in the Visual Studio solution</span></span>

<span data-ttu-id="9e037-177">를 Mixed Reality 기능 도구 사용으로 변경하려면 일회성 수동 단계 집합이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-177">Changing to using the Mixed Reality Feature Tool requires a one-time set of manual steps.</span></span>

1. <span data-ttu-id="9e037-178">현재 프로젝트의 복사본을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-178">Save a copy of your current project.</span></span>
1. <span data-ttu-id="9e037-179">Unity 닫기</span><span class="sxs-lookup"><span data-stu-id="9e037-179">Close Unity</span></span>
1. <span data-ttu-id="9e037-180">*Assets* 폴더 내에서 .meta 파일과 함께 다음 **MRTK** 폴더를 삭제합니다(프로젝트에 나열된 폴더가 모두 없을 수 있음).</span><span class="sxs-lookup"><span data-stu-id="9e037-180">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="9e037-181">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="9e037-181">MRTK/Core</span></span>
    - <span data-ttu-id="9e037-182">MRTK/예제</span><span class="sxs-lookup"><span data-stu-id="9e037-182">MRTK/Examples</span></span>
    - <span data-ttu-id="9e037-183">MRTK/확장</span><span class="sxs-lookup"><span data-stu-id="9e037-183">MRTK/Extensions</span></span>
    - <span data-ttu-id="9e037-184">MRTK/공급자</span><span class="sxs-lookup"><span data-stu-id="9e037-184">MRTK/Providers</span></span>
    - <span data-ttu-id="9e037-185">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="9e037-185">MRTK/SDK</span></span>
    - <span data-ttu-id="9e037-186">MRTK/서비스</span><span class="sxs-lookup"><span data-stu-id="9e037-186">MRTK/Services</span></span>
    - <span data-ttu-id="9e037-187">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="9e037-187">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="9e037-188">MRTK 셰이더를 수정한 경우 MRTK/StandardAssets 폴더를 삭제하기 전에 로컬 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-188">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="9e037-189">MRTK/도구</span><span class="sxs-lookup"><span data-stu-id="9e037-189">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="9e037-190">**MixedRealityToolkit.Generated** 폴더 또는 해당 .meta 파일을 삭제하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="9e037-190">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="9e037-191">**라이브러리** 폴더 삭제</span><span class="sxs-lookup"><span data-stu-id="9e037-191">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="9e037-192">Unity Collab과 같은 일부 Unity 도구는 라이브러리 폴더에 구성 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-192">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="9e037-193">이 작업을 수행하는 도구를 사용하는 경우 먼저 삭제하기 전에 라이브러리에서 도구의 데이터 폴더를 복사한 다음 라이브러리를 다시 생성한 후 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-193">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="9e037-194">Unity에서 프로젝트 다시 열기</span><span class="sxs-lookup"><span data-stu-id="9e037-194">Re-open the project in Unity</span></span>

<span data-ttu-id="9e037-195">이전 단계가 수행되면 [Mixed Reality 기능 도구를](#mixed-reality-feature-tool) 실행하고 원하는 버전의 Mixed Reality Toolkit 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-195">Once the previous steps have been performed, run the [Mixed Reality Feature Tool](#mixed-reality-feature-tool) and import the desired version of the Mixed Reality Toolkit.</span></span>

## <a name="updating-230-to-240"></a><span data-ttu-id="9e037-196">2.3.0에서 2.4.0으로 업데이트</span><span class="sxs-lookup"><span data-stu-id="9e037-196">Updating 2.3.0 to 2.4.0</span></span>

<span data-ttu-id="9e037-197">[폴더 이름 바꾸기](#folder-renames-in-240) 
 [API 변경 내용](#api-changes-in-240)</span><span class="sxs-lookup"><span data-stu-id="9e037-197">[Folder renames](#folder-renames-in-240)
[API changes](#api-changes-in-240)</span></span>

### <a name="folder-renames-in-240"></a><span data-ttu-id="9e037-198">2.4.0에서 폴더 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="9e037-198">Folder renames in 2.4.0</span></span>

<span data-ttu-id="9e037-199">MixedRealityToolkit 폴더의 이름이 변경되고 버전 2.4의 공통 계층 구조로 이동되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-199">The MixedRealityToolkit folders have been renamed and moved into a common hierarchy in version 2.4.</span></span> <span data-ttu-id="9e037-200">애플리케이션이 MRTK 리소스에 하드 코딩된 경로를 사용하는 경우 다음 표에 따라 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-200">If an application uses hard coded paths to MRTK resources, they will need to be updated per the following table.</span></span>

| <span data-ttu-id="9e037-201">이전 폴더</span><span class="sxs-lookup"><span data-stu-id="9e037-201">Previous Folder</span></span> | <span data-ttu-id="9e037-202">새 폴더</span><span class="sxs-lookup"><span data-stu-id="9e037-202">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="9e037-203">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="9e037-203">MixedRealityToolkit</span></span> | <span data-ttu-id="9e037-204">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="9e037-204">MRTK/Core</span></span> |
| <span data-ttu-id="9e037-205">MixedRealityToolkit.Examples</span><span class="sxs-lookup"><span data-stu-id="9e037-205">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="9e037-206">MRTK/예제</span><span class="sxs-lookup"><span data-stu-id="9e037-206">MRTK/Examples</span></span> |
| <span data-ttu-id="9e037-207">MixedRealityToolkit.Extensions</span><span class="sxs-lookup"><span data-stu-id="9e037-207">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="9e037-208">MRTK/확장</span><span class="sxs-lookup"><span data-stu-id="9e037-208">MRTK/Extensions</span></span> |
| <span data-ttu-id="9e037-209">MixedRealityToolkit.Providers</span><span class="sxs-lookup"><span data-stu-id="9e037-209">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="9e037-210">MRTK/공급자</span><span class="sxs-lookup"><span data-stu-id="9e037-210">MRTK/Providers</span></span> |
| <span data-ttu-id="9e037-211">MixedRealityToolkit.SDK</span><span class="sxs-lookup"><span data-stu-id="9e037-211">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="9e037-212">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="9e037-212">MRTK/SDK</span></span> |
| <span data-ttu-id="9e037-213">MixedRealityToolkit.Services</span><span class="sxs-lookup"><span data-stu-id="9e037-213">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="9e037-214">MRTK/서비스</span><span class="sxs-lookup"><span data-stu-id="9e037-214">MRTK/Services</span></span> |
| <span data-ttu-id="9e037-215">MixedRealityToolkit.Tests</span><span class="sxs-lookup"><span data-stu-id="9e037-215">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="9e037-216">MRTK/테스트</span><span class="sxs-lookup"><span data-stu-id="9e037-216">MRTK/Tests</span></span> |
| <span data-ttu-id="9e037-217">MixedRealityToolkit.Tools</span><span class="sxs-lookup"><span data-stu-id="9e037-217">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="9e037-218">MRTK/도구</span><span class="sxs-lookup"><span data-stu-id="9e037-218">MRTK/Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="9e037-219">에는 `MixedRealityToolkit.Generated` 고객이 생성한 파일이 포함되어 있으며 변경되지 않은 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-219">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

### <a name="eye-gaze-setup-in-240"></a><span data-ttu-id="9e037-220">2.4.0의 시선 응시 설정</span><span class="sxs-lookup"><span data-stu-id="9e037-220">Eye gaze setup in 2.4.0</span></span>

<span data-ttu-id="9e037-221">이 버전의 MRTK는 시선 응시 설정에 필요한 단계를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-221">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="9e037-222">_'IsEyeTrackingEnabled'_ 확인란은 입력 포인터 프로필의 응시 설정에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-222">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="9e037-223">이 확인란을 선택하면 시선 기반 응시가 활성화된 다음, 기본 머리 기반 응시가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-223">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="9e037-224">이러한 변경 내용 및 시선 추적 설정에 대한 전체 지침에 대한 자세한 내용은 [시선 추적](../features/input/eye-tracking/eye-tracking-basic-setup.md) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e037-224">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/input/eye-tracking/eye-tracking-basic-setup.md) article.</span></span>

### <a name="eye-gaze-pointer-behavior-in-240"></a><span data-ttu-id="9e037-225">2.4.0의 시선 응시 포인터 동작</span><span class="sxs-lookup"><span data-stu-id="9e037-225">Eye gaze pointer behavior in 2.4.0</span></span>

<span data-ttu-id="9e037-226">시선 응시 기본 포인터 동작이 머리 응시 기본 포인터 동작과 일치하도록 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-226">The eye gaze default pointer behavior have been modified to match the head gaze default pointer behavior.</span></span> <span data-ttu-id="9e037-227">시선 응시 포인터는 손을 감지하면 자동으로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-227">An eye gaze pointer will automatically be suppressed once a hand is detected.</span></span> <span data-ttu-id="9e037-228">"선택"이라고 말하면 시선 응시 포인터가 다시 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-228">The eye gaze pointer will become visible again after saying "Select".</span></span>

<span data-ttu-id="9e037-229">응시 및 손 설정에 대한 세부 정보는 [눈과 손](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) 문서에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-229">Details about gaze and hand setups can be found in the [eyes and hands](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) article.</span></span>

### <a name="api-changes-in-240"></a><span data-ttu-id="9e037-230">2.4.0의 API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="9e037-230">API changes in 2.4.0</span></span>

<span data-ttu-id="9e037-231">**사용자 지정 컨트롤러 클래스**</span><span class="sxs-lookup"><span data-stu-id="9e037-231">**Custom controller classes**</span></span>

<span data-ttu-id="9e037-232">사용자 지정 컨트롤러 클래스는 이전에 를 정의해야 `SetupDefaultInteractions(Handedness)` 했습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-232">Custom controller classes previously had to define `SetupDefaultInteractions(Handedness)`.</span></span> <span data-ttu-id="9e037-233">이 메서드는 2.4에서 사용되지 않습니다. 2.4에서는 손수 매개 변수가 컨트롤러 클래스의 고유 전달과 중복되었기 때문에 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-233">This method has been made obsolete in 2.4, as the handedness parameter was redundant with the controller class' own handedness.</span></span> <span data-ttu-id="9e037-234">새 메서드에 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-234">The new method has no parameters.</span></span> <span data-ttu-id="9e037-235">또한 많은 컨트롤러 클래스가 동일한 `AssignControllerMappings(DefaultInteractions);` 방식()으로 정의되었으므로 전체 호출이 로 리팩터화되어 `BaseController` 필요 대신 선택적 재정의를 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-235">Additionally, many controller classes defined this the same way (`AssignControllerMappings(DefaultInteractions);`), so the full call has been refactored down into `BaseController` and made an optional override instead of required.</span></span>

<span data-ttu-id="9e037-236">**시선 응시 속성**</span><span class="sxs-lookup"><span data-stu-id="9e037-236">**Eye Gaze properties**</span></span>

<span data-ttu-id="9e037-237">`UseEyeTracking`구현의 속성 `GazeProvider` 이름이 로 `IMixedRealityEyeGazeProvider` `IsEyeTrackingEnabled` 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-237">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="9e037-238">이전에 이 작업을 한 경우...</span><span class="sxs-lookup"><span data-stu-id="9e037-238">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="9e037-239">지금 이 작업을 수행합니다...</span><span class="sxs-lookup"><span data-stu-id="9e037-239">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="9e037-240">**WindowsApiChecker 속성**</span><span class="sxs-lookup"><span data-stu-id="9e037-240">**WindowsApiChecker properties**</span></span>

<span data-ttu-id="9e037-241">다음 WindowsApiChecker 속성은 사용되지 않는 것으로 표시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-241">The following WindowsApiChecker properties have been marked as obsolete.</span></span> <span data-ttu-id="9e037-242">또는 `IsMethodAvailable` 을 `IsPropertyAvailable` `IsTypeAvailable` 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="9e037-242">Please use `IsMethodAvailable`, `IsPropertyAvailable` or `IsTypeAvailable`.</span></span>

- <span data-ttu-id="9e037-243">UniversalApiContractV8_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="9e037-243">UniversalApiContractV8_IsAvailable</span></span>
- <span data-ttu-id="9e037-244">UniversalApiContractV7_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="9e037-244">UniversalApiContractV7_IsAvailable</span></span>
- <span data-ttu-id="9e037-245">UniversalApiContractV6_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="9e037-245">UniversalApiContractV6_IsAvailable</span></span>
- <span data-ttu-id="9e037-246">UniversalApiContractV5_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="9e037-246">UniversalApiContractV5_IsAvailable</span></span>
- <span data-ttu-id="9e037-247">UniversalApiContractV4_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="9e037-247">UniversalApiContractV4_IsAvailable</span></span>
- <span data-ttu-id="9e037-248">UniversalApiContractV3_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="9e037-248">UniversalApiContractV3_IsAvailable</span></span>

<span data-ttu-id="9e037-249">향후 API 계약 버전에 대해 WindowsApiChecker에 속성을 추가할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-249">There are no plans to add properties to WindowsApiChecker for future API contract versions.</span></span>

<span data-ttu-id="9e037-250">**GltfMeshPrimitiveAttributes 읽기 전용**</span><span class="sxs-lookup"><span data-stu-id="9e037-250">**GltfMeshPrimitiveAttributes read-only**</span></span>

<span data-ttu-id="9e037-251">설정 가능한 데 사용된 gltf 메시 기본 특성은 이제 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-251">The gltf mesh primitive attributes used to be settable, they are now read-only.</span></span> <span data-ttu-id="9e037-252">해당 값은 deserialized될 때 한 번 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-252">Their values will be set once when deserialized.</span></span>

### <a name="custom-button-icon-migration"></a><span data-ttu-id="9e037-253">사용자 지정 단추 아이콘 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="9e037-253">Custom Button Icon Migration</span></span>

<span data-ttu-id="9e037-254">이전에는 사용자 지정 단추 아이콘을 사용하여 단추의 쿼드 렌더러에 새 재질을 할당해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-254">Previously custom button icons required assigning a new material to the button's quad renderer.</span></span> <span data-ttu-id="9e037-255">더 이상 필요하지 않으며 사용자 지정 아이콘 질감을 IconSet으로 이동하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-255">This is no longer necessary and we recommend moving custom icon textures into an IconSet.</span></span> <span data-ttu-id="9e037-256">기존 사용자 지정 재질 및 아이콘이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-256">Existing custom materials and icons are preserved.</span></span> <span data-ttu-id="9e037-257">그러나 업그레이드할 때까지는 최적 상태가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-257">However they will be less optimal until upgraded.</span></span>
<span data-ttu-id="9e037-258">프로젝트의 모든 단추에 있는 자산을 새 권장 형식으로 업그레이드하려면 ButtonConfigHelperMigrationHandler를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-258">To upgrade the assets on all buttons in the project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="9e037-259">(Mixed Reality Toolkit -> 유틸리티 -> 마이그레이션 창 -> 마이그레이션 처리기 선택 -> Microsoft.MixedReality. Toolkit. Utilities.ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="9e037-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

![업그레이드 창 대화](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="9e037-261">마이그레이션 중에 설정된 기본 아이콘에 아이콘이 없으면 MixedRealityToolkit.Generated/CustomIconSets에 사용자 지정 아이콘 집합이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-261">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="9e037-262">대화 상자는 이 작업을 수행했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-262">A dialog will indicate that this has taken place.</span></span>

![사용자 지정 아이콘 알림](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a><span data-ttu-id="9e037-264">2.2.0에서 2.3.0으로 업데이트</span><span class="sxs-lookup"><span data-stu-id="9e037-264">Updating 2.2.0 to 2.3.0</span></span>

- [<span data-ttu-id="9e037-265">API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="9e037-265">API changes</span></span>](#api-changes-in-230)

### <a name="api-changes-in-230"></a><span data-ttu-id="9e037-266">2.3.0의 API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="9e037-266">API changes in 2.3.0</span></span>

<span data-ttu-id="9e037-267">**ControllerPoseSynchronizer**</span><span class="sxs-lookup"><span data-stu-id="9e037-267">**ControllerPoseSynchronizer**</span></span>

<span data-ttu-id="9e037-268">프라이빗 ControllerPoseSynchronizer.handedness 필드는 사용되지 않는 것으로 표시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-268">The private ControllerPoseSynchronizer.handedness field has been marked as obsolete.</span></span> <span data-ttu-id="9e037-269">필드가 클래스 외부에 표시되지 않기 때문에 애플리케이션에 미치는 영향을 최소화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-269">This should have minimal impact on applications as the field is not visible outside of its class.</span></span>

<span data-ttu-id="9e037-270">공용 ControllerPoseSynchronizer.Handedness 속성의 setter가 제거되었습니다([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span><span class="sxs-lookup"><span data-stu-id="9e037-270">The public ControllerPoseSynchronizer.Handedness property's setter has been removed ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span></span>

<span data-ttu-id="9e037-271">**Unity용 MSBuild**</span><span class="sxs-lookup"><span data-stu-id="9e037-271">**MSBuild for Unity**</span></span>

<span data-ttu-id="9e037-272">이 버전의 MRTK는 이전 릴리스보다 최신 버전의 Unity용 MSBuild 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-272">This version of MRTK uses a newer version of MSBuild for Unity than previous releases.</span></span> <span data-ttu-id="9e037-273">프로젝트를 로드하는 동안 이전 버전이 Unity 패키지 관리자 매니페스트에 나열되면 Unity에 MSBuild 사용 옵션이 선택된 구성 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-273">During project load, if the older version is listed in the Unity Package Manger manifest, the configuration dialog will appear, with the Enable MSBuild for Unity option checked.</span></span> <span data-ttu-id="9e037-274">를 적용하면 업그레이드가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-274">Applying will perform an upgrade.</span></span>

<span data-ttu-id="9e037-275">**ScriptingUtilities**</span><span class="sxs-lookup"><span data-stu-id="9e037-275">**ScriptingUtilities**</span></span>

<span data-ttu-id="9e037-276">ScriptingUtilities 클래스는 사용되지 않는 것으로 표시되었으며 Microsoft.MixedReality에서 ScriptUtilities로 대체되었습니다. Toolkit. Editor.Utilities 어셈블리.</span><span class="sxs-lookup"><span data-stu-id="9e037-276">The ScriptingUtilities class has been marked as obsolete and has been replaced by ScriptUtilities, in the Microsoft.MixedReality.Toolkit.Editor.Utilities assembly.</span></span> <span data-ttu-id="9e037-277">새 클래스는 이전 동작을 구체화하고 스크립팅 정의 제거에 대한 지원을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-277">The new class refines previous behavior and adds support for removing scripting definitions.</span></span>

<span data-ttu-id="9e037-278">기존 코드는 버전 2.3.0에서 계속 작동하지만 새 클래스로 업데이트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-278">While existing code will continue to function in version 2.3.0, it is recommended to update to the new class.</span></span>

<span data-ttu-id="9e037-279">**ShellHandRayPointer**</span><span class="sxs-lookup"><span data-stu-id="9e037-279">**ShellHandRayPointer**</span></span>

<span data-ttu-id="9e037-280">ShellHandRayPointer 클래스의 lineRendererSelected 및 lineRendererNoTarget 멤버가 각각 lineMaterialSelected 및 lineMaterialNoTarget(#6863 )으로 대체되었습니다.[](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)</span><span class="sxs-lookup"><span data-stu-id="9e037-280">The lineRendererSelected and lineRendererNoTarget members of the ShellHandRayPointer class have been replaced by lineMaterialSelected and lineMaterialNoTarget, respectively ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span></span>

<span data-ttu-id="9e037-281">lineRendererSelected 및/또는 lineRendererNoTarget을 lineMaterialNoTarget으로 바꾸어 컴파일 오류를 해결하세요.</span><span class="sxs-lookup"><span data-stu-id="9e037-281">Please replace lineRendererSelected with lineMaterialSelected and/or lineRendererNoTarget with lineMaterialNoTarget to resolve compile errors.</span></span>

<span data-ttu-id="9e037-282">**공간 관찰자 StartupBehavior**</span><span class="sxs-lookup"><span data-stu-id="9e037-282">**Spatial observer StartupBehavior**</span></span>

<span data-ttu-id="9e037-283">클래스를 기반으로 구축된 공간 `BaseSpatialObserver` 관찰자는 이제 다시 사용하도록 설정할 때 StartupBehavior의 값을 적용합니다([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span><span class="sxs-lookup"><span data-stu-id="9e037-283">Spatial observers built upon the `BaseSpatialObserver` class now honor the value of StartupBehavior when re-enabled ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span></span>

<span data-ttu-id="9e037-284">이 수정 사항을 활용하기 위해 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-284">No changes are required to take advantage of this fix.</span></span>

<span data-ttu-id="9e037-285">**PressableButton을 사용하도록 업데이트된 UX 컨트롤 프리팹**</span><span class="sxs-lookup"><span data-stu-id="9e037-285">**UX control prefabs updated to use PressableButton**</span></span>

<span data-ttu-id="9e037-286">다음 프리팹은 이제 근거리 상호 작용을 위해 TouchHandler 대신 PressableButton 구성 요소를 사용하고 있습니다([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070)).</span><span class="sxs-lookup"><span data-stu-id="9e037-286">The following prefabs are now using the PressableButton component instead of TouchHandler for near interaction ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span></span>

- <span data-ttu-id="9e037-287">AnimationButton</span><span class="sxs-lookup"><span data-stu-id="9e037-287">AnimationButton</span></span>
- <span data-ttu-id="9e037-288">단추</span><span class="sxs-lookup"><span data-stu-id="9e037-288">Button</span></span>
- <span data-ttu-id="9e037-289">ButtonHoloLens1</span><span class="sxs-lookup"><span data-stu-id="9e037-289">ButtonHoloLens1</span></span>
- <span data-ttu-id="9e037-290">ButtonHoloLens1Toggle</span><span class="sxs-lookup"><span data-stu-id="9e037-290">ButtonHoloLens1Toggle</span></span>
- <span data-ttu-id="9e037-291">CheckBox</span><span class="sxs-lookup"><span data-stu-id="9e037-291">CheckBox</span></span>
- <span data-ttu-id="9e037-292">RadialSet</span><span class="sxs-lookup"><span data-stu-id="9e037-292">RadialSet</span></span>
- <span data-ttu-id="9e037-293">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="9e037-293">ToggleButton</span></span>
- <span data-ttu-id="9e037-294">ToggleSwitch</span><span class="sxs-lookup"><span data-stu-id="9e037-294">ToggleSwitch</span></span>
- <span data-ttu-id="9e037-295">UnityUIButton</span><span class="sxs-lookup"><span data-stu-id="9e037-295">UnityUIButton</span></span>
- <span data-ttu-id="9e037-296">UnityUICheckboxButton</span><span class="sxs-lookup"><span data-stu-id="9e037-296">UnityUICheckboxButton</span></span>
- <span data-ttu-id="9e037-297">UnityUIRadialButton</span><span class="sxs-lookup"><span data-stu-id="9e037-297">UnityUIRadialButton</span></span>
- <span data-ttu-id="9e037-298">UnityUIToggleButton</span><span class="sxs-lookup"><span data-stu-id="9e037-298">UnityUIToggleButton</span></span>

<span data-ttu-id="9e037-299">이 변경으로 인해 애플리케이션 코드를 업데이트해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-299">Application code may require updating due to this change.</span></span>

<span data-ttu-id="9e037-300">**WindowsMixedRealityUtilities 네임스페이스**</span><span class="sxs-lookup"><span data-stu-id="9e037-300">**WindowsMixedRealityUtilities namespace**</span></span>

<span data-ttu-id="9e037-301">WindowsMixedRealityUtilities의 네임스페이스가 Microsoft.MixedReality에서 변경되었습니다. Toolkit. Microsoft.MixedReality에 대한 WindowsMixedReality.Input. Toolkit. WindowsMixedReality([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span><span class="sxs-lookup"><span data-stu-id="9e037-301">The namespace of WindowsMixedRealityUtilities changed from Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input to Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span></span>

<span data-ttu-id="9e037-302">컴파일 오류를 해결하려면 #using 문을 업데이트하세요.</span><span class="sxs-lookup"><span data-stu-id="9e037-302">Please update #using statements to resolve compile errors.</span></span>

## <a name="updating-210-to-220"></a><span data-ttu-id="9e037-303">2.1.0에서 2.2.0으로 업데이트</span><span class="sxs-lookup"><span data-stu-id="9e037-303">Updating 2.1.0 to 2.2.0</span></span>

- [<span data-ttu-id="9e037-304">API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="9e037-304">API changes</span></span>](#api-changes-in-220)

### <a name="api-changes-in-220"></a><span data-ttu-id="9e037-305">2.2.0의 API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="9e037-305">API changes in 2.2.0</span></span>

<span data-ttu-id="9e037-306">**IMixedRealityBoundarySystem.Contains**</span><span class="sxs-lookup"><span data-stu-id="9e037-306">**IMixedRealityBoundarySystem.Contains**</span></span>

<span data-ttu-id="9e037-307">이 메서드는 이전에 Unity에서 정의한 특정 실험적 열거형을 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-307">This method previously took in a specific, Unity-defined experimental enum.</span></span> <span data-ttu-id="9e037-308">이제 Unity 열거형과 동일한 MRTK 정의 열거형을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-308">It now takes in an MRTK-defined enum that's identical to the Unity enum.</span></span> <span data-ttu-id="9e037-309">이 변경은 Unity의 향후 경계 API에 대한 MRTK를 준비하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-309">This change helps prepare the MRTK for Unity's future boundary APIs.</span></span>

<span data-ttu-id="9e037-310">**MixedRealityServiceProfileAttribute**</span><span class="sxs-lookup"><span data-stu-id="9e037-310">**MixedRealityServiceProfileAttribute**</span></span>

<span data-ttu-id="9e037-311">프로필 지원 요구 사항을 더 잘 설명하기 위해 MixedRealityServiceProfileAttribute가 업데이트되어 제외된 형식의 선택적 컬렉션을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-311">To better describe the requirements for supporting a profile, the MixedRealityServiceProfileAttribute has been updated to add an optional collection of excluded types.</span></span> <span data-ttu-id="9e037-312">이 변경의 일부로 ServiceType 속성이 Type에서 Type[]으로 변경되고 RequiredTypes로 이름이 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-312">As part of this change, the ServiceType property has been changed from Type to Type[] and been renamed to RequiredTypes.</span></span>

<span data-ttu-id="9e037-313">두 번째 속성인 ExcludedTypes도 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-313">A second property, ExcludedTypes has also been added.</span></span>

## <a name="updating-200-to-210"></a><span data-ttu-id="9e037-314">2.0.0에서 2.1.0으로 업데이트</span><span class="sxs-lookup"><span data-stu-id="9e037-314">Updating 2.0.0 to 2.1.0</span></span>

- [<span data-ttu-id="9e037-315">API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="9e037-315">API changes</span></span>](#api-changes-in-210)
- [<span data-ttu-id="9e037-316">프로필 변경 내용</span><span class="sxs-lookup"><span data-stu-id="9e037-316">Profile changes</span></span>](#profile-changes-in-210)

### <a name="api-changes-in-210"></a><span data-ttu-id="9e037-317">2.1.0의 API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="9e037-317">API changes in 2.1.0</span></span>

<span data-ttu-id="9e037-318">**BaseNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="9e037-318">**BaseNearInteractionTouchable**</span></span>

<span data-ttu-id="9e037-319">`BaseNearInteractionTouchable`메서드를 가상으로 표시하도록 가 `OnValidate` 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-319">The `BaseNearInteractionTouchable` has been modified to mark the `OnValidate` method as virtual.</span></span> <span data-ttu-id="9e037-320">(예: `BaseNearInteractionTouchable` )를 확장하는 `NearInteractionTouchableUnityUI` 클래스가 이 변경 사항을 반영하도록 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-320">Classes that extend `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI`) have been updated to reflect this change.</span></span>

<span data-ttu-id="9e037-321">**ColliderNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="9e037-321">**ColliderNearInteractionTouchable**</span></span>

<span data-ttu-id="9e037-322">`ColliderNearInteractionTouchable` 클래스는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-322">The `ColliderNearInteractionTouchable` class has been deprecated.</span></span> <span data-ttu-id="9e037-323">를 사용하도록 코드 참조를 `BaseNearInteractionTouchable` 업데이트하세요.</span><span class="sxs-lookup"><span data-stu-id="9e037-323">Please update code references to use `BaseNearInteractionTouchable`.</span></span>

<span data-ttu-id="9e037-324">**IMixedRealityMouseDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="9e037-324">**IMixedRealityMouseDeviceManager**</span></span>

<span data-ttu-id="9e037-325">**_추가됨_**</span><span class="sxs-lookup"><span data-stu-id="9e037-325">**_Added_**</span></span>

<span data-ttu-id="9e037-326">`IMixedRealityMouseDeviceManager``CursorSpeed`및 `WheelSpeed` 속성이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-326">`IMixedRealityMouseDeviceManager` has been added `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="9e037-327">이러한 속성을 사용하면 애플리케이션에서 커서와 휠의 속도를 각각 조정하는 승수 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-327">These properties allow applications to specify a multiplier value by which the speed of the cursor and wheel, respectively will be scaled.</span></span>

<span data-ttu-id="9e037-328">이는 주요 변경이며 기존 마우스 디바이스 관리자 구현을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-328">This is a breaking change and requires existing mouse device manager implementations to be modified .</span></span>

>[!NOTE]
><span data-ttu-id="9e037-329">이 변경 내용은 버전 2.0.0과 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-329">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="9e037-330">**_사용되지 않음_**</span><span class="sxs-lookup"><span data-stu-id="9e037-330">**_Deprecated_**</span></span>

<span data-ttu-id="9e037-331">`MouseInputProfile`속성은 사용되지 않는 것으로 표시되었으며 이후 버전의 Microsoft Mixed Reality Toolkit 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-331">The `MouseInputProfile` property has been marked as obsolete and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="9e037-332">애플리케이션 코드는 더 이상이 속성을 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-332">It is recommended that application code no longer use this property.</span></span>

<span data-ttu-id="9e037-333">**상호 작용 가능**</span><span class="sxs-lookup"><span data-stu-id="9e037-333">**Interactable**</span></span>

<span data-ttu-id="9e037-334">다음 메서드 및 속성은 더 이상 사용되지 않으며 이후 버전의 Microsoft Mixed Reality Toolkit 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-334">The following methods and properties have been deprecated and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="9e037-335">권장 사항은 사용되지 않는 특성에 포함되고 콘솔에 표시되는 지침에 따라 애플리케이션 코드를 업데이트하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-335">The recommendation is to update application code per the guidance contained in the Obsolete attribute and displayed in the console.</span></span>

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

<span data-ttu-id="9e037-336">**NearInteractionTouchableSurface**</span><span class="sxs-lookup"><span data-stu-id="9e037-336">**NearInteractionTouchableSurface**</span></span>

<span data-ttu-id="9e037-337">`NearInteractionTouchableSurface`클래스가 추가되었으며 이제 및 의 기본 클래스로 `NearInteractionTouchable` `NearInteractionTouchableUnityUI` 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-337">The `NearInteractionTouchableSurface` class has been added and now serves as the base class for `NearInteractionTouchable` and `NearInteractionTouchableUnityUI`.</span></span>

### <a name="profile-changes-in-210"></a><span data-ttu-id="9e037-338">2.1.0의 프로필 변경 내용</span><span class="sxs-lookup"><span data-stu-id="9e037-338">Profile changes in 2.1.0</span></span>

<span data-ttu-id="9e037-339">**손 추적 프로필**</span><span class="sxs-lookup"><span data-stu-id="9e037-339">**Hand tracking profile**</span></span>

<span data-ttu-id="9e037-340">손 메시 및 공동 시각화에는 이제 별도의 편집기와 플레이어 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-340">The hand mesh and joint visualizations now have a separate editor and player settings.</span></span> <span data-ttu-id="9e037-341">이러한 시각화를 로 설정하도록 손 추적 프로필이 업데이트되었습니다. Nothing, Everything, Editor 또는 Player.</span><span class="sxs-lookup"><span data-stu-id="9e037-341">The hand tracking profile has been updated to allow for setting these visualizations to; Nothing, Everything, Editor or Player.</span></span>

![손 시각화 모드](../release-notes/images/HandTrackingVisualizationModes.png)

<span data-ttu-id="9e037-343">사용자 지정 손 추적 프로필은 버전 2.1.0에서 올바르게 작동하도록 업데이트해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-343">Custom hand tracking profiles may need to be updated to work correctly with version 2.1.0.</span></span>

>[!NOTE]
><span data-ttu-id="9e037-344">이 변경 내용은 버전 2.0.0과 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-344">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="9e037-345">**입력 시뮬레이션 프로필**</span><span class="sxs-lookup"><span data-stu-id="9e037-345">**Input simulation profile**</span></span>

<span data-ttu-id="9e037-346">입력 시뮬레이션 시스템이 업그레이드되어 입력 시뮬레이션 프로필의 몇 가지 설정이 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-346">The input simulation system has been upgraded, which changes a few settings in the input simulation profile.</span></span> <span data-ttu-id="9e037-347">일부 변경 내용은 자동으로 마이그레이션할 수 없으며 사용자는 프로필이 기본값을 사용하고 있음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-347">Some changes can not be migrated automatically and users may find that profiles are using default values.</span></span>

1. <span data-ttu-id="9e037-348">프로필의 모든 KeyCode 및 마우스 단추 바인딩은 `KeyBinding` 바인딩 형식(키 또는 마우스)과 실제 바인딩 코드(각각 KeyCode 또는 마우스 단추 번호)를 저장하는 제네릭 구조체로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-348">All KeyCode and mouse button bindings in the profile have been replaced with a generic `KeyBinding` struct, which stores the type of binding (key or mouse) as well as the actual binding code (KeyCode or mouse button number respectively).</span></span> <span data-ttu-id="9e037-349">구조체에는 통합된 표시를 허용하고 큰 드롭다운 목록에서 선택하는 대신 해당 키를 눌러 키 바인딩을 신속하게 설정하는 "자동 바인딩" 도구를 제공하는 자체 검사기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-349">The struct has its own inspector, which allows unified display and offers an "auto-bind" tool to quickly set key bindings by pressing the respective key instead of selecting from a huge dropdown list.</span></span>

    - <span data-ttu-id="9e037-350">FastControlKey</span><span class="sxs-lookup"><span data-stu-id="9e037-350">FastControlKey</span></span>
    - <span data-ttu-id="9e037-351">ToggleLeftHandKey</span><span class="sxs-lookup"><span data-stu-id="9e037-351">ToggleLeftHandKey</span></span>
    - <span data-ttu-id="9e037-352">ToggleRightHandKey</span><span class="sxs-lookup"><span data-stu-id="9e037-352">ToggleRightHandKey</span></span>
    - <span data-ttu-id="9e037-353">LeftHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="9e037-353">LeftHandManipulationKey</span></span>
    - <span data-ttu-id="9e037-354">RightHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="9e037-354">RightHandManipulationKey</span></span>

1. <span data-ttu-id="9e037-355">`MouseLookToggle` 은 이전에 `MouseLookButton` 열거형에 로 `InputSimulationMouseButton.Focused` 포함되었으므로 이제는 별도의 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-355">`MouseLookToggle` was previously included in the `MouseLookButton` enum as `InputSimulationMouseButton.Focused`, it is now a separate option.</span></span> <span data-ttu-id="9e037-356">사용하도록 설정하면 단추를 해제한 후 이스케이프 키를 누를 때까지 카메라가 마우스로 계속 회전합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-356">When enabled, the camera will keep rotating with the mouse after releasing the button, until the escape key is pressed.</span></span>
1. <span data-ttu-id="9e037-357">`HandDepthMultiplier` 입력 시뮬레이션에 대한 일부 변경 내용을 수용하기 위해 기본값이 0.1에서 0.03으로 감소되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-357">`HandDepthMultiplier` default value has been lowered from 0.1 to 0.03 to accommodate some changes to the input simulation.</span></span> <span data-ttu-id="9e037-358">스크롤할 때 카메라가 너무 빨리 이동하면 이 값을 낮추어 보세요.</span><span class="sxs-lookup"><span data-stu-id="9e037-358">If the camera moves too fast when scrolling, try lowering this value.</span></span>
1. <span data-ttu-id="9e037-359">손을 회전하기 위한 키가 제거되었으며, 이제 마우스를 통해 손 회전도 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-359">Keys for rotating hands have been removed, hand rotation is now controlled by the mouse as well.</span></span> <span data-ttu-id="9e037-360">`HandRotateButton`왼쪽/오른쪽 조작 키(LShift/Space)와 함께 (Ctrl)을 보유하면 손 회전이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-360">Holding `HandRotateButton` (Ctrl) together with the left/right hand manipulation key (LShift/Space) will enable hand rotation.</span></span>
1. <span data-ttu-id="9e037-361">새 축 "UpDown"이 입력 축 목록에 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-361">A new axis "UpDown" has been introduced to the input axis list.</span></span> <span data-ttu-id="9e037-362">이렇게 하면 세로로 카메라의 이동이 제어되고, 기본적으로 Q/E 키와 컨트롤러 트리거 단추가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-362">This controls camera movement in the vertical and defaults to Q/E keys as well as the controller trigger buttons.</span></span>

<span data-ttu-id="9e037-363">이러한 변경 내용에 대한 자세한 내용은 [입력 시뮬레이션 서비스](../features/input-simulation/input-simulation-service.md) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e037-363">For more information on these changes, please see the [input simulation service](../features/input-simulation/input-simulation-service.md) article.</span></span>

<span data-ttu-id="9e037-364">**마우스 데이터 공급자 프로필**</span><span class="sxs-lookup"><span data-stu-id="9e037-364">**Mouse data provider profile**</span></span>

<span data-ttu-id="9e037-365">새 및 속성을 노출하도록 마우스 데이터 공급자 프로필이 `CursorSpeed` `WheelSpeed` 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-365">The mouse data provider profile has been updated to expose the new `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="9e037-366">기존 사용자 지정 프로필에는 자동으로 기본값이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-366">Existing custom profiles will automatically have default values provided.</span></span> <span data-ttu-id="9e037-367">프로필이 저장되면 이러한 새 값이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-367">When the profile is saved, these new values will be persisted.</span></span>

<span data-ttu-id="9e037-368">**컨트롤러 매핑 프로필**</span><span class="sxs-lookup"><span data-stu-id="9e037-368">**Controller mapping profile**</span></span>

<span data-ttu-id="9e037-369">일부 축 및 입력 형식은 2.1.0, 특히 OpenVR 플랫폼과 관련하여 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-369">Some axes and input types have been updated in 2.1.0, especially around the OpenVR platform.</span></span> <span data-ttu-id="9e037-370">업그레이드할 때 **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles를** 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-370">Please be sure to select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** when upgrading.</span></span> <span data-ttu-id="9e037-371">이렇게 하면 사용자 지정 할당 입력 작업을 그대로 유지하면서 사용자 지정 컨트롤러 매핑 프로필이 업데이트된 축 및 데이터로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-371">This will update any custom Controller Mapping Profiles with the updated axes and data, while leaving your custom-assigned input actions intact.</span></span>

## <a name="updating-rc2-to-200"></a><span data-ttu-id="9e037-372">RC2를 2.0.0으로 업데이트</span><span class="sxs-lookup"><span data-stu-id="9e037-372">Updating RC2 to 2.0.0</span></span>

<span data-ttu-id="9e037-373">Microsoft Mixed Reality Toolkit RC2 및 2.0.0 릴리스 사이에 기존 프로젝트에 영향을 미칠 수 있는 변경 내용이 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-373">Between the RC2 and 2.0.0 releases of the Microsoft Mixed Reality Toolkit, changes were made that may impact existing projects.</span></span> <span data-ttu-id="9e037-374">이 문서에서는 이러한 변경 내용과 프로젝트를 2.0.0 릴리스로 업데이트하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-374">This document describes those changes and how to update projects to the 2.0.0 release.</span></span>

- [<span data-ttu-id="9e037-375">API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="9e037-375">API changes</span></span>](#api-changes-in-200)
- [<span data-ttu-id="9e037-376">어셈블리 이름 변경</span><span class="sxs-lookup"><span data-stu-id="9e037-376">Assembly name changes</span></span>](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a><span data-ttu-id="9e037-377">2.0.0의 API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="9e037-377">API changes in 2.0.0</span></span>

<span data-ttu-id="9e037-378">RC2 릴리스 이후 기존 프로젝트를 중단시키는 일부 API를 포함하여 많은 API 변경이 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-378">Since the release of RC2, there have been a number of API changes including some that may break existing projects.</span></span> <span data-ttu-id="9e037-379">다음 섹션에서는 RC2 및 2.0.0 릴리스 간에 발생한 변경 내용에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-379">The following sections describe the changes that have occurred between the RC2 and 2.0.0 releases.</span></span>

<span data-ttu-id="9e037-380">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="9e037-380">**MixedRealityToolkit**</span></span>

<span data-ttu-id="9e037-381">MixedRealityToolkit 개체의 다음 공용 속성은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-381">The following public properties on the MixedRealityToolkit object have been deprecated.</span></span>

- <span data-ttu-id="9e037-382">`RegisteredMixedRealityServices` 에 등록된 확장 서비스 및 데이터 공급자의 컬렉션이 더 이상 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-382">`RegisteredMixedRealityServices` no longer contains the collection of registered extensions services and data providers.</span></span>

<span data-ttu-id="9e037-383">확장 서비스에 액세스하려면 를 `MixedRealityServiceRegistry.TryGetService<T>` 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-383">To access extension services, use `MixedRealityServiceRegistry.TryGetService<T>`.</span></span> <span data-ttu-id="9e037-384">데이터 공급자에 액세스하려면 서비스 인스턴스를 로 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 캐스팅하고 `GetDataProvider<T>` 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-384">To access data providers, cast the service instance to [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) and use `GetDataProvider<T>`.</span></span>

<span data-ttu-id="9e037-385">다음 사용되지 않은 속성에 대해 [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 또는 를 대신 사용합니다. [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices)</span><span class="sxs-lookup"><span data-stu-id="9e037-385">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) or [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) instead for the following deprecated properties</span></span>

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

<span data-ttu-id="9e037-386">**CoreServices**</span><span class="sxs-lookup"><span data-stu-id="9e037-386">**CoreServices**</span></span>

<span data-ttu-id="9e037-387">[`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices)클래스는 개체에 있는 정적 시스템 접근자(예: BoundarySystem)를 `MixedRealityToolkit` 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-387">The [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) class is the replacement for the static system accessors (ex: BoundarySystem) found in the `MixedRealityToolkit` object.</span></span>

>[!IMPORTANT]
><span data-ttu-id="9e037-388">`MixedRealityToolkit`시스템 접근자는 버전 2.0.0에서 더 이상 사용되지 않으며 MRTK의 이후 릴리스에서 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-388">The `MixedRealityToolkit` system accessors have been deprecated in version 2.0.0 and will be removed in a future release of the MRTK.</span></span>

<span data-ttu-id="9e037-389">다음 코드 예제에서는 이전 및 새 패턴을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-389">The following code example illustrates the old and the new pattern.</span></span>

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

<span data-ttu-id="9e037-390">새 CoreSystem 클래스를 사용하면 다른 서비스 등록 기관(예: 실험적 서비스 관리자 중 하나)을 사용하도록 애플리케이션을 변경하는 경우 애플리케이션 코드를 업데이트할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-390">Using the new CoreSystem class will ensure that your application code will not need updating if you change the application to use a different service registrar (ex: one of the experimental service managers).</span></span>

<span data-ttu-id="9e037-391">**IMixedRealityRaycastProvider**</span><span class="sxs-lookup"><span data-stu-id="9e037-391">**IMixedRealityRaycastProvider**</span></span>

<span data-ttu-id="9e037-392">IMixedRealityRaycastProvider가 추가되면서 입력 시스템 구성 프로필이 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-392">With the addition of the IMixedRealityRaycastProvider, the input system configuration profile was changed.</span></span> <span data-ttu-id="9e037-393">사용자 지정 프로필이 있는 경우 애플리케이션을 실행할 때 다음 이미지에 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-393">If you have a custom profile, you may receive the errors in the following image when you run your application.</span></span>

![Raycast 공급자 1 선택](../release-notes/images/UnableToRegisterRaycastProvider.png)

<span data-ttu-id="9e037-395">이 문제를 해결하려면 IMixedRealityRaycastProvider 인스턴스를 입력 시스템 프로필에 추가하세요.</span><span class="sxs-lookup"><span data-stu-id="9e037-395">To fix these, please add an IMixedRealityRaycastProvider instance to your input system profile.</span></span>

![Raycast 공급자 2 선택](../release-notes/images/SelectRaycastProvider.png)

<span data-ttu-id="9e037-397">**이벤트 시스템**</span><span class="sxs-lookup"><span data-stu-id="9e037-397">**Event System**</span></span>

- <span data-ttu-id="9e037-398">`IMixedRealityEventSystem`이전 API 메서드 `Register` 및 는 사용되지 않는 것으로 `Unregister` 표시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-398">The `IMixedRealityEventSystem` old API methods `Register` and `Unregister` have been marked as obsolete.</span></span> <span data-ttu-id="9e037-399">이전 버전과의 호환성을 위해 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-399">They are preserved for backwards compatibility.</span></span>
- <span data-ttu-id="9e037-400">`InputSystemGlobalListener` 가 사용되지 않는 것으로 표시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-400">`InputSystemGlobalListener` has been marked as obsolete.</span></span> <span data-ttu-id="9e037-401">해당 기능은 변경되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-401">Its functionality has not changed.</span></span>
- <span data-ttu-id="9e037-402">`BaseInputHandler` 기본 클래스가 에서 로 `InputSystemGlobalListener` `InputSystemGlobalHandlerListener` 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-402">`BaseInputHandler` base class has been changed from `InputSystemGlobalListener` to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="9e037-403">이는 의 하위 항목에 대한 주요 `BaseInputHandler` 변경입니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-403">This is a breaking change for any descendants of `BaseInputHandler`.</span></span>

<span data-ttu-id="9e037-404">**_변경의 동기 부여_**</span><span class="sxs-lookup"><span data-stu-id="9e037-404">**_Motivation behind the change_**</span></span>

<span data-ttu-id="9e037-405">이전 이벤트 시스템 `Register` API로 `Unregister` 인해 런타임에 여러 문제가 발생할 수 있습니다. 주요 원인은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-405">The old event system API `Register` and `Unregister` could potentially cause multiple issues in runtime, main being:</span></span>

- <span data-ttu-id="9e037-406">구성 요소가 전역 이벤트에 등록하는 경우 *모든* 형식의 전역 입력 이벤트를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-406">If a component registers for global events, it would receive global input events of *all* types.</span></span>
- <span data-ttu-id="9e037-407">개체의 구성 요소 중 하나가 전역 입력 이벤트를 등록하는 경우 이 개체의 모든 구성 요소는 *모든* 형식의 전역 입력 이벤트를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-407">If one of the components on an object registers for global input events, all components on this object will receive global input events of *all* types.</span></span>
- <span data-ttu-id="9e037-408">동일한 개체의 두 구성 요소가 전역 이벤트에 등록되고 한 구성 요소가 런타임에서 비활성화된 경우 두 번째 구성 요소는 전역 이벤트 수신을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-408">If two components on the same object register to global events, and then one is disabled in runtime, the second one stops receiving global events.</span></span>

<span data-ttu-id="9e037-409">새 API `RegisterHandler` 및 `UnregisterHandler` :</span><span class="sxs-lookup"><span data-stu-id="9e037-409">New API `RegisterHandler` and `UnregisterHandler`:</span></span>

- <span data-ttu-id="9e037-410">전역적으로 수신 대기해야 하는 입력 이벤트와 포커스를 기반으로 해야 하는 입력 이벤트에 대한 명시적 및 세부적인 제어를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-410">Provides an explicit and granular control over which input events should be listened to globally and which should be focused-based.</span></span>
- <span data-ttu-id="9e037-411">동일한 개체의 여러 구성 요소가 서로 독립적으로 전역 이벤트를 수신 대기할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-411">Allows multiple components on the same object to listen to global events independently on each other.</span></span>

<span data-ttu-id="9e037-412">**_마이그레이션 방법_**</span><span class="sxs-lookup"><span data-stu-id="9e037-412">**_How to migrate_**</span></span>

- <span data-ttu-id="9e037-413">이전에 API를 호출한 경우 `Register` / `Unregister` 이러한 호출을 에 대한 호출로 `RegisterHandler` / `UnregisterHandler` 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-413">If you have been calling `Register`/`Unregister` API directly before, replace these calls with calls to `RegisterHandler`/`UnregisterHandler`.</span></span> <span data-ttu-id="9e037-414">제네릭 매개 변수로 구현하는 처리기 인터페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-414">Use handler interfaces you implement as generic parameters.</span></span> <span data-ttu-id="9e037-415">여러 인터페이스를 구현하고 그 중 여러 인터페이스가 전역 입력 이벤트를 수신 대기하는 경우 를 `RegisterHandler` 여러 번 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-415">If you implement multiple interfaces, and several of them listen to global input events, call `RegisterHandler` multiple times.</span></span>
- <span data-ttu-id="9e037-416">에서 상속한 경우 `InputSystemGlobalListener` 상속을 로 `InputSystemGlobalHandlerListener` 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-416">If you have been inheriting from `InputSystemGlobalListener`, change inheritance to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="9e037-417">`RegisterHandlers`메서드를 구현하고 `UnregisterHandlers` 추상화합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-417">Implement `RegisterHandlers` and `UnregisterHandlers` abstract methods.</span></span> <span data-ttu-id="9e037-418">구현 `inputSystem.RegisterHandler` 호출에서 ( `inputSystem.UnregisterHandler` ) 전역 이벤트를 수신 대기 하려는 모든 처리기 인터페이스에 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-418">In the implementation call `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) to register on all handler interfaces you want to listen global events for.</span></span>
- <span data-ttu-id="9e037-419">에서 상속된 경우 `BaseInputHandler` 및 `RegisterHandlers` `UnregisterHandlers` 추상 메서드를 구현합니다(의 경우와 `InputSystemGlobalListener` 동일).</span><span class="sxs-lookup"><span data-stu-id="9e037-419">If you have been inheriting from `BaseInputHandler`, implement `RegisterHandlers` and `UnregisterHandlers` abstract methods (same as for `InputSystemGlobalListener`).</span></span>

<span data-ttu-id="9e037-420">**_마이그레이션 예제_**</span><span class="sxs-lookup"><span data-stu-id="9e037-420">**_Examples of migration_**</span></span>

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

<span data-ttu-id="9e037-421">**공간 인식**</span><span class="sxs-lookup"><span data-stu-id="9e037-421">**Spatial Awareness**</span></span>

<span data-ttu-id="9e037-422">IMixedRealitySpatialAwarenessSystem 및 IMixedRealitySpatialAwarenessObserver 인터페이스는 아래에 설명된 대로 여러 가지 주요 변경 내용을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-422">The IMixedRealitySpatialAwarenessSystem and IMixedRealitySpatialAwarenessObserver interfaces have taken multiple breaking changes as described below.</span></span>

<span data-ttu-id="9e037-423">**_변경_**</span><span class="sxs-lookup"><span data-stu-id="9e037-423">**_Changes_**</span></span>

<span data-ttu-id="9e037-424">사용법을 더 잘 설명하기 위해 다음 메서드의 이름이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-424">The following method(s) have been renamed to better describe their usage.</span></span>

- <span data-ttu-id="9e037-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` 은 사용을 명확히 하기 위해 로 이름이 `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` has been renamed to `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` to clarify its usage.</span></span>

<span data-ttu-id="9e037-426">**_추가_**</span><span class="sxs-lookup"><span data-stu-id="9e037-426">**_Additions_**</span></span>

<span data-ttu-id="9e037-427">고객 피드백에 따라 이전에 관찰된 공간 인식 데이터를 쉽게 제거할 수 있는 지원이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-427">Based on customer feedback, support for easy removal of previously observed spatial awareness data has been added.</span></span>

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

<span data-ttu-id="9e037-428">**해결기**</span><span class="sxs-lookup"><span data-stu-id="9e037-428">**Solvers**</span></span>

<span data-ttu-id="9e037-429">일부 해결기 구성 요소 및 SolverHandler 관리자 클래스는 다양한 버그를 수정하고 보다 직관적인 사용을 위해 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-429">Some solver components and the SolverHandler manager class has changed to fix various bugs and for more intuitive usage.</span></span>

<span data-ttu-id="9e037-430">**_SolverHandler_**</span><span class="sxs-lookup"><span data-stu-id="9e037-430">**_SolverHandler_**</span></span>

- <span data-ttu-id="9e037-431">클래스는 더 이상 에서 확장되지 않습니다. `ControllerFinder`</span><span class="sxs-lookup"><span data-stu-id="9e037-431">Class no longer extends from `ControllerFinder`</span></span>
- <span data-ttu-id="9e037-432">`TrackedObjectToReference` public 속성은 더 이상 사용되지 않으며 이름이 로 바뀌었습니다. `TrackedTargetType`</span><span class="sxs-lookup"><span data-stu-id="9e037-432">`TrackedObjectToReference` public property deprecated and has been renamed to `TrackedTargetType`</span></span>
- <span data-ttu-id="9e037-433">`TrackedObjectType` 는 왼쪽 & 오른쪽 컨트롤러 값을 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-433">`TrackedObjectType` deprecates left & right controller values.</span></span> <span data-ttu-id="9e037-434">대신 또는 값을 사용하고 `MotionController` `HandJoint` 새 속성을 `TrackedHandedness` 업데이트하여 추적을 왼쪽 또는 오른쪽 컨트롤러로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-434">Instead use `MotionController` or `HandJoint` values and update new `TrackedHandedness` property to limit tracking to left or right controller</span></span>

<span data-ttu-id="9e037-435">**_Inbetween_**</span><span class="sxs-lookup"><span data-stu-id="9e037-435">**_InBetween_**</span></span>

- <span data-ttu-id="9e037-436">`TrackedObjectForSecondTransform` public 속성은 더 이상 사용되지 않으며 이름이 로 바뀌었습니다. `SecondTrackedObjectType`</span><span class="sxs-lookup"><span data-stu-id="9e037-436">`TrackedObjectForSecondTransform` public property deprecated and has been renamed to `SecondTrackedObjectType`</span></span>
- <span data-ttu-id="9e037-437">`AttachSecondTransformToNewTrackedObject()` 는 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-437">`AttachSecondTransformToNewTrackedObject()` has been removed.</span></span> <span data-ttu-id="9e037-438">해결기를 업데이트하려면 공용 속성(즉,</span><span class="sxs-lookup"><span data-stu-id="9e037-438">To update the solver, modify the public properties (i.e</span></span> <span data-ttu-id="9e037-439">`SecondTrackedObjectType`)</span><span class="sxs-lookup"><span data-stu-id="9e037-439">`SecondTrackedObjectType`)</span></span>

<span data-ttu-id="9e037-440">**_SurfaceM_**</span><span class="sxs-lookup"><span data-stu-id="9e037-440">**_SurfaceMagnetism_**</span></span>

- <span data-ttu-id="9e037-441">`MaxDistance` public 속성은 더 이상 사용되지 않으며 이름이 로 바뀌었습니다. `MaxRaycastDistance`</span><span class="sxs-lookup"><span data-stu-id="9e037-441">`MaxDistance` public property deprecated and has been renamed to `MaxRaycastDistance`</span></span>
- <span data-ttu-id="9e037-442">`CloseDistance` public 속성은 더 이상 사용되지 않으며 이름이 로 바뀌었습니다. `ClosestDistance`</span><span class="sxs-lookup"><span data-stu-id="9e037-442">`CloseDistance` public property deprecated and has been renamed to `ClosestDistance`</span></span>
- <span data-ttu-id="9e037-443">`RaycastDirectionMode`의 기본값은 이제 `TrackedTargetForward` 추적된 대상 변환의 방향으로 광선 캐스트를 변환하는 입니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-443">Default value for `RaycastDirectionMode` is now `TrackedTargetForward` which raycasts in the direction of the tracked target transform forward</span></span>
- <span data-ttu-id="9e037-444">`OrientationMode`열거형 값 `Vertical` 및 의 이름이 각각 및 로 `Full` 변경되었습니다. `TrackedTarget` `SurfaceNormal`</span><span class="sxs-lookup"><span data-stu-id="9e037-444">`OrientationMode` enum values, `Vertical` and `Full`, have been renamed to `TrackedTarget` and `SurfaceNormal` respectively</span></span>
- <span data-ttu-id="9e037-445">`KeepOrientationVertical` 연결된 GameObject의 방향이 세로로 유지되는지 여부를 제어하기 위해 public 속성이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-445">`KeepOrientationVertical` public property has been added to control whether orientation of associated GameObject remains vertical</span></span>

<span data-ttu-id="9e037-446">**단추**</span><span class="sxs-lookup"><span data-stu-id="9e037-446">**Buttons**</span></span>

- <span data-ttu-id="9e037-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 이제 `DistanceSpaceMode` 속성이 `Local` 기본값으로 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) now has `DistanceSpaceMode` property set to `Local` as default.</span></span> <span data-ttu-id="9e037-448">이렇게 하면 계속 누를 수 있는 동안 단추의 크기를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-448">This allows buttons to be scaled while still be pressable</span></span>

<span data-ttu-id="9e037-449">**클리핑 구**</span><span class="sxs-lookup"><span data-stu-id="9e037-449">**Clipping Sphere**</span></span>

<span data-ttu-id="9e037-450">ClippingSphere 인터페이스가 ClippingBox 및 ClippingPlane에 있는 API를 미러하도록 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-450">The ClippingSphere interface has changed to mirror the APIs found in the ClippingBox and ClippingPlane.</span></span>

<span data-ttu-id="9e037-451">이제 ClippingSphere의 Radius 속성이 변환 배율에 따라 암시적으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-451">The ClippingSphere's Radius property is now implicitly calculated based on the transform scale.</span></span> <span data-ttu-id="9e037-452">개발자는 검사기에서 ClippingSphere의 반지름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-452">Before developers would have to specify the radius of the ClippingSphere in the inspector.</span></span> <span data-ttu-id="9e037-453">반경을 변경하려면 변환의 변환 배율만 정상적으로 업데이트하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-453">If you want to change the radius, just update the transform scale of the transform as you normally would.</span></span>

<span data-ttu-id="9e037-454">**NearInteractionTouchable 및인스턴스**</span><span class="sxs-lookup"><span data-stu-id="9e037-454">**NearInteractionTouchable and PokePointer**</span></span>

- <span data-ttu-id="9e037-455">NearInteractionTouchable은 더 이상 터치하는 Unity UI 캔버스를 처리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-455">NearInteractionTouchable does not handle Unity UI canvas touching any longer.</span></span> <span data-ttu-id="9e037-456">이제 Unity UI 터치 가능에 NearInteractionTouchableUnityUI 클래스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-456">The NearInteractionTouchableUnityUI class must be used for Unity UI touchables now.</span></span>
- <span data-ttu-id="9e037-457">ColliderNearInteractionTouchable은 충돌체를 기반으로 하는 터치 가능한 새 기본 클래스입니다. 즉, NearInteractionTouchableUnityUI를 제외한 모든 터치 가능 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-457">ColliderNearInteractionTouchable is the new base class for touchables based on colliders, i.e. every touchable except NearInteractionTouchableUnityUI.</span></span>
- <span data-ttu-id="9e037-458">BaseNearInteractionTouchable.DistFront가 이동되고 Rename이 표시되어,이 거리이며, 이 거리이며, 이 거리와는 다른 TouchAble과 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-458">BaseNearInteractionTouchable.DistFront has been moved and renamed to PokePointer.TouchableDistance This is the distance and which the PokePointer can interact with touchables.</span></span> <span data-ttu-id="9e037-459">이전에는 각 터치 가능 개체의 최대 상호 작용 거리가 있었지만, 이제는 최적화를 향상할 수 있도록 하여 을(를) 에 정의했습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-459">Previously each touchable had its own maximum interaction distance, but now this is defined in the PokePointer which allows better optimization.</span></span>
- <span data-ttu-id="9e037-460">BaseNearInteractionTouchable.DistBack의 이름이Resreshold로 바뀌었습니다. 이렇게 하면 사용자 표시가 DebounceThreshold에 해당한다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-460">BaseNearInteractionTouchable.DistBack has been renamed to PokeThreshold This makes it clear that PokeThreshold is the counterpart to DebounceThreshold.</span></span> <span data-ttu-id="9e037-461">Touchable은Resreshold가 교차될 때 활성화되고 DebounceThreshold가 교차될 때 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-461">A touchable is activated when the PokeThreshold is crossed, and released when DebounceThreshold is crossed.</span></span>

<span data-ttu-id="9e037-462">**ReadOnlyAttribute**</span><span class="sxs-lookup"><span data-stu-id="9e037-462">**ReadOnlyAttribute**</span></span>

<span data-ttu-id="9e037-463">`Microsoft.MixedReality.Toolkit`네임스페이스가 , 및 에 `ReadOnlyAttribute` 추가되었습니다. `BeginReadOnlyGroupAttribute` `EndReadOnlyGroupAttribute`</span><span class="sxs-lookup"><span data-stu-id="9e037-463">The `Microsoft.MixedReality.Toolkit` namespace has been added to `ReadOnlyAttribute`, `BeginReadOnlyGroupAttribute`, and `EndReadOnlyGroupAttribute`.</span></span>

<span data-ttu-id="9e037-464">**PointerClickHandler**</span><span class="sxs-lookup"><span data-stu-id="9e037-464">**PointerClickHandler**</span></span>

<span data-ttu-id="9e037-465">`PointerClickHandler` 클래스는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-465">The `PointerClickHandler` class has been deprecated.</span></span> <span data-ttu-id="9e037-466">`PointerHandler`대신 을 사용해야 하며, 동일한 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-466">The `PointerHandler` should be used instead, it provides the same functionality.</span></span>

<span data-ttu-id="9e037-467">**HoloLens 클릭하여 지원**</span><span class="sxs-lookup"><span data-stu-id="9e037-467">**HoloLens clicker support**</span></span>

<span data-ttu-id="9e037-468">HoloLens 클릭하여 컨트롤러 매핑이 처리되지 않은 에서 처리되지 않은 로 [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-468">The HoloLens clicker's controller mappings have changed from being an unhanded [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) to being an unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand).</span></span> <span data-ttu-id="9e037-469">이를 고려하기 위해 ControllerMapping 프로필을 처음 열 때 자동 업데이트 관리자가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-469">To account for this, an automatic updater will run the first time you open your ControllerMapping profile.</span></span> <span data-ttu-id="9e037-470">이 일회성 마이그레이션 단계를 트리거하려면 2.0.0으로 업그레이드한 후 사용자 지정 프로필을 한 번 이상 여세요.</span><span class="sxs-lookup"><span data-stu-id="9e037-470">Please open any custom profiles at least once after upgrading to 2.0.0 in order to trigger this one-time migration step.</span></span>

<span data-ttu-id="9e037-471">**InteractableHighlight**</span><span class="sxs-lookup"><span data-stu-id="9e037-471">**InteractableHighlight**</span></span>

<span data-ttu-id="9e037-472">`InteractableHighlight` 클래스는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-472">The `InteractableHighlight` class has been deprecated.</span></span> <span data-ttu-id="9e037-473">`InteractableOnFocus` `FocusInteractableStates` 클래스와 자산을 대신 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-473">The `InteractableOnFocus` class and `FocusInteractableStates` asset should be used instead.</span></span> <span data-ttu-id="9e037-474">에 대한 새 자산을 만들려면 `Theme` 프로젝트 창을 마우스 오른쪽 `InteractableOnFocus` 단추로 클릭하고 상호 작용 가능한 테마 Mixed Reality Toolkit   >    >    >  *만들기를* 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-474">To create a new `Theme` asset for the `InteractableOnFocus`, right click in the project window and select *Create* > *Mixed Reality Toolkit* > *Interactable* > *Theme*.</span></span>

<span data-ttu-id="9e037-475">**HandInteractionPanZoom**</span><span class="sxs-lookup"><span data-stu-id="9e037-475">**HandInteractionPanZoom**</span></span>

<span data-ttu-id="9e037-476">`HandInteractionPanZoom` 은 입력 구성 요소가 아니어도 UI 네임스페이스로 이동되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-476">`HandInteractionPanZoom` has been moved to the UI namespace as it was not an input component.</span></span> <span data-ttu-id="9e037-477">`HandPanEventData` 도 이 네임스페이스로 이동되었으며 다른 UI 이벤트 데이터와 일치하도록 간소화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-477">`HandPanEventData` has also been moved into this namespace, and simplified to correspond with other UI event data.</span></span>

### <a name="assembly-name-changes-in-200"></a><span data-ttu-id="9e037-478">2.0.0에서 어셈블리 이름 변경</span><span class="sxs-lookup"><span data-stu-id="9e037-478">Assembly name changes in 2.0.0</span></span>

<span data-ttu-id="9e037-479">2.0.0 릴리스에서는 모든 공식 Mixed Reality Toolkit 어셈블리 이름과 관련 어셈블리 정의(.asmdef) 파일이 다음 패턴에 맞게 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-479">In The 2.0.0 release, all of the official Mixed Reality Toolkit assembly names and their associated assembly definition (.asmdef) files have been updated to fit the following pattern.</span></span>

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

<span data-ttu-id="9e037-480">일부 경우에는 콘텐츠의 더 나은 통합을 만들기 위해 여러 어셈블리가 병합되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-480">In some instances, multiple assemblies have been merged to create better unity of their contents.</span></span> <span data-ttu-id="9e037-481">프로젝트에서 사용자 지정 .asmdef 파일을 사용하는 경우 업데이트가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-481">If your project uses custom .asmdef files, they may require updating.</span></span>

<span data-ttu-id="9e037-482">다음 표에서는 RC2 .asmdef 파일 이름이 2.0.0 릴리스에 매핑하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-482">The following tables describe how the RC2 .asmdef file names map to the 2.0.0 release.</span></span> <span data-ttu-id="9e037-483">모든 어셈블리 이름은 .asmdef 파일 이름과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="9e037-483">All assembly names match the .asmdef file name.</span></span>

<span data-ttu-id="9e037-484">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="9e037-484">**MixedRealityToolkit**</span></span>

| <span data-ttu-id="9e037-485">RC2</span><span class="sxs-lookup"><span data-stu-id="9e037-485">RC2</span></span> | <span data-ttu-id="9e037-486">2.0.0</span><span class="sxs-lookup"><span data-stu-id="9e037-486">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="9e037-487">MixedRealityToolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-487">MixedRealityToolkit.asmdef</span></span> | <span data-ttu-id="9e037-488">Microsoft.MixedReality. Toolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-488">Microsoft.MixedReality.Toolkit.asmdef</span></span> |
| <span data-ttu-id="9e037-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span></span> | <span data-ttu-id="9e037-490">Microsoft.MixedReality. Toolkit. Editor.BuildAndDeploy.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-490">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span></span> |
| <span data-ttu-id="9e037-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="9e037-492">제거된 경우 Microsoft.MixedReality를 사용합니다. Toolkit. Editor.Utilities.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-492">Removed, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="9e037-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span></span> | <span data-ttu-id="9e037-494">Microsoft.MixedReality. Toolkit. Editor.ClassExtensions.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-494">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span></span>
| <span data-ttu-id="9e037-495">MixedRealityToolkit.Core.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-495">MixedRealityToolkit.Core.Inspectors.asmdef</span></span> | <span data-ttu-id="9e037-496">Microsoft.MixedReality. Toolkit. Editor.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-496">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span></span> |
| <span data-ttu-id="9e037-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span></span> | <span data-ttu-id="9e037-498">Microsoft.MixedReality. Toolkit. Editor.ServiceInspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-498">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span></span> |
| <span data-ttu-id="9e037-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span></span> | <span data-ttu-id="9e037-500">Microsoft.MixedReality. Toolkit. Async.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-500">Microsoft.MixedReality.Toolkit.Async.asmdef</span></span> |
| <span data-ttu-id="9e037-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="9e037-502">Microsoft.MixedReality. Toolkit. Editor.Utilities.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-502">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="9e037-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span></span> | <span data-ttu-id="9e037-504">Microsoft.MixedReality. Toolkit. Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-504">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span></span> |
| <span data-ttu-id="9e037-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span></span> | <span data-ttu-id="9e037-506">Microsoft.MixedReality. Toolkit. Gltf.Importers.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-506">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span></span> |

<span data-ttu-id="9e037-507">**MixedRealityToolkit.Providers**</span><span class="sxs-lookup"><span data-stu-id="9e037-507">**MixedRealityToolkit.Providers**</span></span>

| <span data-ttu-id="9e037-508">RC2</span><span class="sxs-lookup"><span data-stu-id="9e037-508">RC2</span></span> | <span data-ttu-id="9e037-509">2.0.0</span><span class="sxs-lookup"><span data-stu-id="9e037-509">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="9e037-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span></span> | <span data-ttu-id="9e037-511">Microsoft.MixedReality. Toolkit. Providers.OpenVR.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-511">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span></span> |
| <span data-ttu-id="9e037-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span></span> | <span data-ttu-id="9e037-513">Microsoft.MixedReality. Toolkit. Providers.WindowsMixedReality.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-513">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span></span> |
| <span data-ttu-id="9e037-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span></span> | <span data-ttu-id="9e037-515">Microsoft.MixedReality. Toolkit. Providers.WindowsVoiceInput.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-515">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span></span> |

<span data-ttu-id="9e037-516">**MixedRealityToolkit.Services**</span><span class="sxs-lookup"><span data-stu-id="9e037-516">**MixedRealityToolkit.Services**</span></span>

| <span data-ttu-id="9e037-517">RC2</span><span class="sxs-lookup"><span data-stu-id="9e037-517">RC2</span></span> | <span data-ttu-id="9e037-518">2.0.0</span><span class="sxs-lookup"><span data-stu-id="9e037-518">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="9e037-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span></span> | <span data-ttu-id="9e037-520">Microsoft.MixedReality. Toolkit. Services.BoundarySystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-520">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span></span> |
| <span data-ttu-id="9e037-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span></span> | <span data-ttu-id="9e037-522">Microsoft.MixedReality. Toolkit. Services.CameraSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-522">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span></span> |
| <span data-ttu-id="9e037-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span></span> | <span data-ttu-id="9e037-524">Microsoft.MixedReality. Toolkit. Services.DiagnosticsSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-524">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span></span> |
| <span data-ttu-id="9e037-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span></span> | <span data-ttu-id="9e037-526">Microsoft.MixedReality. Toolkit. Services.InputSimulation.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-526">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span></span> |
| <span data-ttu-id="9e037-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span></span> | <span data-ttu-id="9e037-528">Microsoft.MixedReality. Toolkit. Services.InputSimulation.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-528">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span></span> |
| <span data-ttu-id="9e037-529">MixedRealityToolkit.Services.InputSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-529">MixedRealityToolkit.Services.InputSystem.asmdef</span></span> | <span data-ttu-id="9e037-530">Microsoft.MixedReality. Toolkit. Services.InputSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-530">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span></span> |
| <span data-ttu-id="9e037-531">MixedRealityToolkit.Services.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-531">MixedRealityToolkit.Services.Inspectors.asmdef</span></span> | <span data-ttu-id="9e037-532">Microsoft.MixedReality. Toolkit. Services.InputSystem.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-532">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span></span> |
| <span data-ttu-id="9e037-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span></span> | <span data-ttu-id="9e037-534">Microsoft.MixedReality. Toolkit. Services.SceneSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-534">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span></span> |
| <span data-ttu-id="9e037-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span></span> | <span data-ttu-id="9e037-536">Microsoft.MixedReality. Toolkit. Services.SpatialAwarenessSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-536">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span></span> |
| <span data-ttu-id="9e037-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span></span> | <span data-ttu-id="9e037-538">Microsoft.MixedReality. Toolkit. Services.TeleportSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-538">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span></span> |

<span data-ttu-id="9e037-539">**MixedRealityToolkit.SDK**</span><span class="sxs-lookup"><span data-stu-id="9e037-539">**MixedRealityToolkit.SDK**</span></span>

| <span data-ttu-id="9e037-540">RC2</span><span class="sxs-lookup"><span data-stu-id="9e037-540">RC2</span></span> | <span data-ttu-id="9e037-541">2.0.0</span><span class="sxs-lookup"><span data-stu-id="9e037-541">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="9e037-542">MixedRealityToolkit.SDK.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-542">MixedRealityToolkit.SDK.asmdef</span></span> | <span data-ttu-id="9e037-543">Microsoft.MixedReality. Toolkit. SDK.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-543">Microsoft.MixedReality.Toolkit.SDK.asmdef</span></span> |
| <span data-ttu-id="9e037-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span></span> | <span data-ttu-id="9e037-545">Microsoft.MixedReality. Toolkit. Sdk. Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-545">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span></span> |

<span data-ttu-id="9e037-546">**MixedRealityToolkit.Examples**</span><span class="sxs-lookup"><span data-stu-id="9e037-546">**MixedRealityToolkit.Examples**</span></span>

| <span data-ttu-id="9e037-547">RC2</span><span class="sxs-lookup"><span data-stu-id="9e037-547">RC2</span></span> | <span data-ttu-id="9e037-548">2.0.0</span><span class="sxs-lookup"><span data-stu-id="9e037-548">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="9e037-549">MixedRealityToolkit.Examples.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-549">MixedRealityToolkit.Examples.asmdef</span></span> | <span data-ttu-id="9e037-550">Microsoft.MixedReality. Toolkit. Examples.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-550">Microsoft.MixedReality.Toolkit.Examples.asmdef</span></span> |
| <span data-ttu-id="9e037-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span></span> | <span data-ttu-id="9e037-552">Microsoft.MixedReality. Toolkit. Demos.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-552">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span></span> |
| <span data-ttu-id="9e037-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span></span> | <span data-ttu-id="9e037-554">Microsoft.MixedReality. Toolkit. Demos.StandardShader.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-554">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span></span> |
| <span data-ttu-id="9e037-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span></span> | <span data-ttu-id="9e037-556">Microsoft.MixedReality. Toolkit. Demos.InspectorFields.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-556">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span></span> |
| <span data-ttu-id="9e037-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span></span> | <span data-ttu-id="9e037-558">Microsoft.MixedReality. Toolkit. Demos.InspectorFields.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-558">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span></span> |
| <span data-ttu-id="9e037-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span></span> | <span data-ttu-id="9e037-560">Microsoft.MixedReality. Toolkit. Demos.UX.Interactables.asmdef</span><span class="sxs-lookup"><span data-stu-id="9e037-560">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span></span> |
