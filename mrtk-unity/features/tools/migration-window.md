---
title: 마이그레이션 창
description: MRTK에서 업데이트로 마이그레이션하는 방법에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: a6e268dd28be2a3d485f937ec5b5ce6b1f29851f
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647120"
---
# <a name="migration-window"></a><span data-ttu-id="5ea56-104">마이그레이션 기간</span><span class="sxs-lookup"><span data-stu-id="5ea56-104">Migration window</span></span>

<span data-ttu-id="5ea56-105">MRTK가 변경되면 일부 구성 요소가 더 이상 사용되지 않을 수 있으며 교체가 도입될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-105">As the MRTK undergoes changes, some components might get deprecated and replacements will get introduced.</span></span>
<span data-ttu-id="5ea56-106">마이그레이션 기간은 사용자가 사용되지 않는 구성 요소의 하위 집합을 새 대체 항목으로 자동으로 마이그레이션하는 데 도움이 되는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-106">The migration window is a tool that helps users to automatically migrate a subset of those deprecated components to the new replacements.</span></span>

![마이그레이션 기간](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a><span data-ttu-id="5ea56-108">사용</span><span class="sxs-lookup"><span data-stu-id="5ea56-108">Usage</span></span>

<span data-ttu-id="5ea56-109">창을 열려면 **도구 키트** 유틸리티 마이그레이션 창 Mixed Reality  >    >    >  선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-109">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Migration Window**.</span></span> <span data-ttu-id="5ea56-110">마이그레이션 창이 열리면 마이그레이션 처리기의 구성 요소별 구현을 선택하여 선택 모드 탐색 탭을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-110">Once the migration window is open, the selection mode navigation tabs can be enabled by choosing the component specific implementation of the migration handler.</span></span>  

![마이그레이션 선택 모드](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a><span data-ttu-id="5ea56-112">개체 모드</span><span class="sxs-lookup"><span data-stu-id="5ea56-112">Object mode</span></span>

<span data-ttu-id="5ea56-113">개체 탭을 선택하면 사용자가 마이그레이션할 프로젝트 폴더에서 현재 열려 있는 장면 또는 프리팹에서 Game 개체를 끌어서 놓을 수 있는 필드 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-113">Selecting the objects tab enables the object Field to where the user can drag and drop any Game objects from the currently open scene or prefabs from the project folder to be migrated.</span></span>
<span data-ttu-id="5ea56-114">나열된 개체의 오른쪽에 표시되는 *제거(-)* 단추를 누르면 선택 목록에서 개체가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-114">Pressing the remove *(-)* button displayed at the right side of the listed object removes the object from the selection list.</span></span>

<span data-ttu-id="5ea56-115">원하는 모든 개체가 목록에 있으면 *마이그레이션* 단추를 누르면 선택한 마이그레이션 처리기 구현에 필요한 변경 내용이 구현과 일치하는 선택 항목의 모든 구성 요소에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-115">Once all the desired objects are in the list, pressing the *Migrate* button will apply the changes required by the chosen migration handler implementation to all components in the selection that match the implementation.</span></span>

![선택 마이그레이션](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a><span data-ttu-id="5ea56-117">장면 모드</span><span class="sxs-lookup"><span data-stu-id="5ea56-117">Scene mode</span></span>

<span data-ttu-id="5ea56-118">사용자가 마이그레이션할 개체가 포함된 장면 자산을 끌어서 놓을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-118">Allows user to drag and drop scene assets containing objects to be migrated.</span></span>

![마이그레이션 장면 선택](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a><span data-ttu-id="5ea56-120">프로젝트 모드</span><span class="sxs-lookup"><span data-stu-id="5ea56-120">Project mode</span></span>

<span data-ttu-id="5ea56-121">*마이그레이션* 단추를 누르면 프로젝트의 모든 프리팹 및 장면에 대한 마이그레이션 처리기 구현의 대상이 지정된 구성 요소가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ea56-121">Pressing the *Migrate* button will update the component targeted by the migration handler implementation for all prefabs and scenes in the project.</span></span>

![전체 프로젝트 마이그레이션](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a><span data-ttu-id="5ea56-123">참조</span><span class="sxs-lookup"><span data-stu-id="5ea56-123">See also</span></span>

- [<span data-ttu-id="5ea56-124">이전 버전에서 업데이트</span><span class="sxs-lookup"><span data-stu-id="5ea56-124">Updating from earlier versions</span></span>](../../updates-deployment/updating.md)
- [<span data-ttu-id="5ea56-125">Microsoft Mixed Reality Toolkit 릴리스</span><span class="sxs-lookup"><span data-stu-id="5ea56-125">Microsoft Mixed Reality Toolkit releases</span></span>](../../release-notes/mrtk-26-release-notes.md)
- [<span data-ttu-id="5ea56-126">MRTK 로드맵</span><span class="sxs-lookup"><span data-stu-id="5ea56-126">MRTK roadmap</span></span>](../../roadmap.md)
