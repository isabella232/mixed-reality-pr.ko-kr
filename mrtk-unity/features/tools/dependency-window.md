---
title: 종속성 창
description: MRTK의 종속성 기간 사용에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: fd17db3f365d8bd97b8cd9c43a6111e2b82a61fe
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647029"
---
# <a name="dependency-window"></a><span data-ttu-id="2adcd-104">종속성 창</span><span class="sxs-lookup"><span data-stu-id="2adcd-104">Dependency window</span></span>

<span data-ttu-id="2adcd-105">Unity에서는 어떤 자산이 사용되고 있는지, 어떤 자산이 참조되고 있는지를 익히는 것이 어려운 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="2adcd-105">In Unity, it is often difficult to gleam which assets are being used, and what is referencing them.</span></span> <span data-ttu-id="2adcd-106">"장면에서 참조 찾기" 옵션은 현재 장면에만 관심이 있을 때 잘 작동하지만 전체 Unity 프로젝트는 어떤가요?</span><span class="sxs-lookup"><span data-stu-id="2adcd-106">The "Find References in Scene" option works great when you are only concerned with the current scene, but what about your entire Unity project?</span></span> <span data-ttu-id="2adcd-107">이 경우 **종속성** 창(자산/MRTK/도구/DependencyWindow)이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2adcd-107">This is where the **Dependency Window** (Assets/MRTK/Tools/DependencyWindow) can be useful.</span></span>

<span data-ttu-id="2adcd-108">종속성 창에는 자산이 서로 참조하고 종속하는 방식이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2adcd-108">The Dependency Window displays how assets reference and depend on each other.</span></span> <span data-ttu-id="2adcd-109">프로젝트 YAML 파일 내에서 GUID를 구문 분석하여 Dependencies를 계산합니다(참고: 스크립트-스크립트 의존성 고려 안 함).</span><span class="sxs-lookup"><span data-stu-id="2adcd-109">Dependencies are calculated by parsing guids within project YAML files (note, script to script dependencies are not considered).</span></span>

## <a name="usage"></a><span data-ttu-id="2adcd-110">사용</span><span class="sxs-lookup"><span data-stu-id="2adcd-110">Usage</span></span>

<span data-ttu-id="2adcd-111">창을 열려면 **Mixed Reality**  >  **도구 키트**  >  **유틸리티**  >  **종속성 창을** 선택하면 창이 열리고 프로젝트의 종속성 그래프 빌드가 자동으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="2adcd-111">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Dependency Window** which will open the window and automatically begin building your project's dependency graph.</span></span> <span data-ttu-id="2adcd-112">종속성 그래프가 빌드되면 프로젝트 탭에서 자산을 선택하여 종속성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2adcd-112">Once the dependency graph is built, you can select assets in the project tab to inspect their dependencies.</span></span>

![종속성 창](../images/dependency-window/MRTK_Dependency_Window.png)

<span data-ttu-id="2adcd-114">창에는 현재 선택한 자산이 의존하는 자산 목록과 해당 자산에 의존하는 자산의 계층적 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2adcd-114">The window displays a list of assets that the currently selected asset depends on, and a hierarchical list of assets that depend on it.</span></span> <span data-ttu-id="2adcd-115">현재 선택한 자산에 종속되지 않는 경우 프로젝트에서 삭제하는 것을 고려할 수 있습니다(일부 자산은 Shader.Find()와 같은 API를 통해 프로그래밍 방식으로 로드되고 종속성 추적기에서 포착되지 않을 수 있음).</span><span class="sxs-lookup"><span data-stu-id="2adcd-115">If nothing depends on the currently selected asset, you can consider deleting it from your project (note that some assets are loaded programmatically via APIs like Shader.Find() and may not be caught by the dependency tracker).</span></span>

<span data-ttu-id="2adcd-116">창에는 다른 자산에서 참조하지 않고 삭제로 간주될 수 있는 모든 자산의 목록만 표시될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2adcd-116">The window can also display just a list of all assets which are not referenced by any other assets and could be considered for deletion:</span></span>

![유추되지 않은 자산을 표시하는 종속성 창](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> <span data-ttu-id="2adcd-118">종속성 창을 사용하는 동안 자산을 수정, 추가 또는 제거하는 경우 가장 "최신" 결과에 대한 종속성 그래프를 새로 고치는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2adcd-118">If assets are modified, added, or removed while the dependency window is in use, it is advised to refresh the dependency graph for the most "up to date" results.</span></span>
