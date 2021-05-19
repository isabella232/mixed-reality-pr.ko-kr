---
title: 마이그레이션 창
description: MRTK의 업데이트로 마이그레이션하는 방법에 대 한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 8e03848097c313a518f638de591f692ab71f0985
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143875"
---
# <a name="migration-window"></a><span data-ttu-id="cf6c2-104">마이그레이션 기간</span><span class="sxs-lookup"><span data-stu-id="cf6c2-104">Migration window</span></span>

<span data-ttu-id="cf6c2-105">MRTK가 변경 되 면 일부 구성 요소가 더 이상 사용 되지 않을 수 있으며 대체가 도입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf6c2-105">As the MRTK undergoes changes, some components might get deprecated and replacements will get introduced.</span></span>
<span data-ttu-id="cf6c2-106">마이그레이션 창은 사용자가 더 이상 사용 되지 않는 구성 요소의 하위 집합을 새 대체 항목으로 자동으로 마이그레이션하는 데 도움이 되는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="cf6c2-106">The migration window is a tool that helps users to automatically migrate a subset of those deprecated components to the new replacements.</span></span>

![마이그레이션 기간](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a><span data-ttu-id="cf6c2-108">사용량</span><span class="sxs-lookup"><span data-stu-id="cf6c2-108">Usage</span></span>

<span data-ttu-id="cf6c2-109">창을 열려면 *Mixed Reality Toolkit*  >  *유틸리티*  >  *마이그레이션 창* 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf6c2-109">To open the window, select *Mixed Reality Toolkit* > *Utilities* > *Migration Window*.</span></span> <span data-ttu-id="cf6c2-110">마이그레이션 창이 열리면 마이그레이션 처리기의 구성 요소별 구현을 선택 하 여 선택 모드 탐색 탭을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf6c2-110">Once the migration window is open, the selection mode navigation tabs can be enabled by choosing the component specific implementation of the migration handler.</span></span>  

![마이그레이션 선택 모드](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a><span data-ttu-id="cf6c2-112">개체 모드</span><span class="sxs-lookup"><span data-stu-id="cf6c2-112">Object mode</span></span>

<span data-ttu-id="cf6c2-113">개체 탭을 선택 하면 개체 필드에서 사용자가 현재 열려 있는 장면 또는 prefabs 프로젝트 폴더에 있는 게임 개체를 끌어서 놓을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf6c2-113">Selecting the objects tab enables the object Field to where the user can drag and drop any Game objects from the currently open scene or prefabs from the project folder to be migrated.</span></span>
<span data-ttu-id="cf6c2-114">나열 된 개체의 오른쪽에 표시 된 제거 *(-)* 단추를 누르면 선택 목록에서 해당 개체가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf6c2-114">Pressing the remove *(-)* button displayed at the right side of the listed object removes the object from the selection list.</span></span>

<span data-ttu-id="cf6c2-115">원하는 모든 개체가 목록에 있으면 *마이그레이션* 단추를 누르면 선택한 마이그레이션 처리기 구현에 필요한 변경 내용이 구현에 일치 하는 선택 항목의 모든 구성 요소에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf6c2-115">Once all the desired objects are in the list, pressing the *Migrate* button will apply the changes required by the chosen migration handler implementation to all components in the selection that match the implementation.</span></span>

![선택 마이그레이션](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a><span data-ttu-id="cf6c2-117">장면 모드</span><span class="sxs-lookup"><span data-stu-id="cf6c2-117">Scene mode</span></span>

<span data-ttu-id="cf6c2-118">사용자가 마이그레이션할 개체가 포함 된 장면 자산을 끌어서 놓을 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf6c2-118">Allows user to drag and drop scene assets containing objects to be migrated.</span></span>

![마이그레이션에 대 한 장면 선택](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a><span data-ttu-id="cf6c2-120">프로젝트 모드</span><span class="sxs-lookup"><span data-stu-id="cf6c2-120">Project mode</span></span>

<span data-ttu-id="cf6c2-121">*마이그레이션 단추를* 누르면 마이그레이션 처리기 구현에서 대상으로 지정 된 구성 요소가 프로젝트의 모든 prefabs 및 장면에 대해 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf6c2-121">Pressing the *Migrate* button will update the component targeted by the migration handler implementation for all prefabs and scenes in the project.</span></span>

![전체 프로젝트 마이그레이션](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a><span data-ttu-id="cf6c2-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf6c2-123">See also</span></span>

- [<span data-ttu-id="cf6c2-124">이전 버전에서 업데이트</span><span class="sxs-lookup"><span data-stu-id="cf6c2-124">Updating from earlier versions</span></span>](../../updates-deployment/updating.md)
- [<span data-ttu-id="cf6c2-125">Microsoft Mixed Reality Toolkit 릴리스</span><span class="sxs-lookup"><span data-stu-id="cf6c2-125">Microsoft Mixed Reality Toolkit releases</span></span>](../../release-notes/mrtk-26-release-notes.md)
- [<span data-ttu-id="cf6c2-126">MRTK 로드맵</span><span class="sxs-lookup"><span data-stu-id="cf6c2-126">MRTK roadmap</span></span>](../../roadmap.md)
