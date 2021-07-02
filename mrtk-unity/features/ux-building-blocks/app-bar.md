---
title: 앱 바
description: MRTK의 앱 바에 대 한 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 앱 바,
ms.openlocfilehash: 3c8633d91b2c26f8bdc774a98b2cb48ffb276720
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175695"
---
# <a name="app-bar"></a><span data-ttu-id="5b290-104">앱 바</span><span class="sxs-lookup"><span data-stu-id="5b290-104">App bar</span></span>

![앱 바](../images/app-bar/MRTK_AppBar_Main.png)

<span data-ttu-id="5b290-106">앱 바는 [경계 제어](bounds-control.md) 스크립트와 함께 사용 되는 UI 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5b290-106">App bar is a UI component that is used together with the [bounds control](bounds-control.md) script.</span></span> <span data-ttu-id="5b290-107">컨트롤을 조작 하기 위해 개체에 button 컨트롤을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b290-107">It adds button controls to an object with the intent to manipulate it.</span></span> <span data-ttu-id="5b290-108">' 조정 ' 단추를 사용 하 여 개체에 대 한 경계 컨트롤 인터페이스를 활성화/비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b290-108">Using the 'Adjust' button, the bounds control interface for an object can be de- / activated.</span></span> <span data-ttu-id="5b290-109">"제거" 단추는 장면에서 개체를 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b290-109">The "Remove" button should remove the object from the scene.</span></span>

## <a name="how-to-use-app-bar"></a><span data-ttu-id="5b290-110">앱 바를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="5b290-110">How to use app bar</span></span>

<span data-ttu-id="5b290-111">`AppBar`장면 계층에 (asset/MRTK/SDK/Features/UX/Prefabs/AppBar/appbar. prefab)를 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="5b290-111">Drag and drop `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) into the scene hierarchy.</span></span> <span data-ttu-id="5b290-112">구성 요소의 검사기 패널에서 범위 컨트롤을 포함 하는 개체를 *대상 경계 상자로* 할당 하 여 앱 바를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b290-112">In the inspector panel of the component, assign any object with a bounds control as the *Target Bounding Box* to add the app bar to it.</span></span>

<span data-ttu-id="5b290-113">**중요:** 대상 개체에 대 한 범위 제어 활성화 옵션은 ' 수동으로 활성화 ' 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b290-113">**Important:** The bounds control activation option for the target object should be 'Activate Manually'.</span></span>

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
