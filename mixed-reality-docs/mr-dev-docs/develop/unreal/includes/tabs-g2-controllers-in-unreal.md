---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638735"
---
# <a name="all-platforms"></a>[<span data-ttu-id="fd2b5-101">모든 플랫폼</span><span class="sxs-lookup"><span data-stu-id="fd2b5-101">All platforms</span></span>](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a><span data-ttu-id="fd2b5-102">HP 동작 컨트롤러 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="fd2b5-102">Enabling HP Motion Controller Plugin</span></span> 

<span data-ttu-id="fd2b5-103">상호 작용 프로필 및 컨트롤러 매핑은 HP 동작 컨트롤러 플러그 인에 있습니다 .이 플러그 인은 컨트롤러 매핑을 사용 하지 않도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd2b5-103">The interaction profile and controller mappings are in the HP Motion Controller plugin, which must be enabled to expose the controller mappings to Unreal’s input system.</span></span>

![OpenXRHPController 플러그 인 사용](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[<span data-ttu-id="fd2b5-105">SteamVR</span><span class="sxs-lookup"><span data-stu-id="fd2b5-105">SteamVR</span></span>](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a><span data-ttu-id="fd2b5-106">시작 및 HMDPluginPriority 구성</span><span class="sxs-lookup"><span data-stu-id="fd2b5-106">Configuring Startup and HMDPluginPriority</span></span>

<span data-ttu-id="fd2b5-107">SteamVR를 사용 하는 Unreal의 입력에는 몇 가지 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd2b5-107">Input in Unreal using SteamVR has a few differences.</span></span>  <span data-ttu-id="fd2b5-108">프로젝트를 설정할 때 먼저 vr를 추가 하 여 SteamVR의 새 입력 시스템을 사용 하는지 확인 **합니다. SteamVR. EnableVRInput = 1** 을 **엔진/Config/ConsoleVariables.ini** 의 **시작** 섹션으로 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd2b5-108">When setting up the project, first ensure it is using SteamVR’s new input system by adding **vr.SteamVR.EnableVRInput=1** to the **Startup** section in **Engine/Config/ConsoleVariables.ini** .</span></span>  <span data-ttu-id="fd2b5-109">이 ini는 프로젝트 디렉터리가 아닌 엔진 설치 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd2b5-109">This ini is found in the engine install directory, not the project directory.</span></span>

![시작 구성 업데이트](../images/reverb-g2-img-07.png)

<span data-ttu-id="fd2b5-111">HP 동작 컨트롤러 플러그 인은 OpenXR를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd2b5-111">The HP Motion Controller plugin will enable OpenXR.</span></span>  <span data-ttu-id="fd2b5-112">OpenXR를 사용 하지 않는 경우 ConsoleVariables.ini와 동일한 디렉터리에서 BaseEngine.ini SteamVR의 HMDPluginPriority를 편집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd2b5-112">If you're not using OpenXR, you will need to edit the HMDPluginPriority of SteamVR in BaseEngine.ini in the same directory as ConsoleVariables.ini.</span></span>  <span data-ttu-id="fd2b5-113">SteamVR 값을 OpenXRHMD 값 보다 크게 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd2b5-113">Change the SteamVR value to be greater than the OpenXRHMD value.</span></span>

![HMDPluginPriority 구성을 업데이트 하는 중](../images/reverb-g2-img-08.png)


