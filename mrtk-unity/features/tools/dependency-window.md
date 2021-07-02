---
title: 종속성 창
description: MRTK의 종속성 창 사용에 대 한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 590476add6904f76081630c4416184bea9f694ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176660"
---
# <a name="dependency-window"></a><span data-ttu-id="f803b-104">종속성 창</span><span class="sxs-lookup"><span data-stu-id="f803b-104">Dependency window</span></span>

<span data-ttu-id="f803b-105">Unity에서 사용 되는 자산 및 참조 하는 항목을 gleam 하는 것이 어려운 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f803b-105">In Unity, it is often difficult to gleam which assets are being used, and what is referencing them.</span></span> <span data-ttu-id="f803b-106">"장면에서 참조 찾기" 옵션은 현재 장면에만 관심이 있는 경우와 전체 Unity 프로젝트에 대 한 내용에 대해 잘 작동 하나요?</span><span class="sxs-lookup"><span data-stu-id="f803b-106">The "Find References in Scene" option works great when you are only concerned with the current scene, but what about your entire Unity project?</span></span> <span data-ttu-id="f803b-107">여기에서 **종속성 창** (asset/MRTK/Tools/DependencyWindow)이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f803b-107">This is where the **Dependency Window** (Assets/MRTK/Tools/DependencyWindow) can be useful.</span></span>

<span data-ttu-id="f803b-108">종속성 창에는 자산이 서로를 참조 하 고 종속 되는 방식이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f803b-108">The Dependency Window displays how assets reference and depend on each other.</span></span> <span data-ttu-id="f803b-109">종속성은 project YAML 파일 내의 guid를 구문 분석 하 여 계산 됩니다 (참고, 스크립트 종속성에 대 한 스크립트는 고려 되지 않음).</span><span class="sxs-lookup"><span data-stu-id="f803b-109">Dependencies are calculated by parsing guids within project YAML files (note, script to script dependencies are not considered).</span></span>

## <a name="usage"></a><span data-ttu-id="f803b-110">사용</span><span class="sxs-lookup"><span data-stu-id="f803b-110">Usage</span></span>

<span data-ttu-id="f803b-111">창을 열려면 **Mixed Reality**  >  **Toolkit**  >  **유틸리티**  >  **종속성 창** 을 선택 합니다. 그러면 창이 열리고 프로젝트의 종속성 그래프를 자동으로 빌드하기 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f803b-111">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Dependency Window** which will open the window and automatically begin building your project's dependency graph.</span></span> <span data-ttu-id="f803b-112">종속성 그래프가 작성 되 면 프로젝트 탭에서 자산을 선택 하 여 해당 종속성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f803b-112">Once the dependency graph is built, you can select assets in the project tab to inspect their dependencies.</span></span>

![종속성 창](../images/dependency-window/MRTK_Dependency_Window.png)

<span data-ttu-id="f803b-114">창에는 현재 선택 된 자산이 종속 된 자산 목록과 해당 자산이 종속 된 자산의 계층적 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f803b-114">The window displays a list of assets that the currently selected asset depends on, and a hierarchical list of assets that depend on it.</span></span> <span data-ttu-id="f803b-115">현재 선택 된 자산에 종속 되지 않는 경우 프로젝트에서 삭제 하는 것을 고려할 수 있습니다. 일부 자산은 셰이더와 같은 Api를 통해 프로그래밍 방식으로 로드 됩니다. Find ()는 종속성 추적기에 의해 catch 되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f803b-115">If nothing depends on the currently selected asset, you can consider deleting it from your project (note that some assets are loaded programmatically via APIs like Shader.Find() and may not be caught by the dependency tracker).</span></span>

<span data-ttu-id="f803b-116">이 창에는 다른 자산에서 참조 하지 않으며 삭제로 간주할 수 있는 모든 자산 목록만 표시 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f803b-116">The window can also display just a list of all assets which are not referenced by any other assets and could be considered for deletion:</span></span>

![참조 되지 않은 자산을 보여 주는 종속성 창](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> <span data-ttu-id="f803b-118">종속성 창이 사용 되는 동안 자산을 수정, 추가 또는 제거 하는 경우 가장 "최신" 결과에 대 한 종속성 그래프를 새로 고치는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f803b-118">If assets are modified, added, or removed while the dependency window is in use, it is advised to refresh the dependency graph for the most "up to date" results.</span></span>
