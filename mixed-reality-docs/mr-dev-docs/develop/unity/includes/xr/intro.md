---
ms.openlocfilehash: d39f6032eaf9a59ca52a6e7ae9b8e4d227175738
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906947"
---
# <a name="openxr"></a>[<span data-ttu-id="5df0d-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="5df0d-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="5df0d-102">Mixed Reality OpenXR 플러그 인은 Unity 2020 LTS 이상에 대 한 **Microsoft의 권장 사항** 입니다.</span><span class="sxs-lookup"><span data-stu-id="5df0d-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="5df0d-103">향후에 새로운 기능이 개발 되 면 앞으로는 Mixed Reality OpenXR 플러그 인에만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5df0d-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="5df0d-104">Mixed Reality OpenXR 플러그 인은 Ar설계도 Emanager 및 ARRaycastManager 구현을 제공 하 여 AR 기반 4.0을 완벽 하 게 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="5df0d-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="5df0d-105">이를 통해 HoloLens 2와 ARCore/Arcore 휴대폰 및 태블릿에 걸쳐 있는 raycasting 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5df0d-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5df0d-106">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="5df0d-106">Prerequisites</span></span> 

* <span data-ttu-id="5df0d-107">[HoloLens 2 개발을 위한 최신 도구](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="5df0d-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="5df0d-108">최신 Unity 2020.3 LTS (2020.3.8 f1 이상 권장)</span><span class="sxs-lookup"><span data-stu-id="5df0d-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="5df0d-109">최소 버전</span><span class="sxs-lookup"><span data-stu-id="5df0d-109">Minimum versions</span></span>

<span data-ttu-id="5df0d-110">이 페이지의 지침에는 아래 나열 된 최신 최신 Unity 및 OpenXR 요구 사항이 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5df0d-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="5df0d-111">최신 Unity OpenXR 플러그 인 (1.2 이상 권장)</span><span class="sxs-lookup"><span data-stu-id="5df0d-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="5df0d-112">최신 Mixed Reality OpenXR 플러그 인 (버전 1.0.0 이상 권장)</span><span class="sxs-lookup"><span data-stu-id="5df0d-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="5df0d-113">**(선택 사항)** 최신 MRTK, (버전 2.7 이상 권장)</span><span class="sxs-lookup"><span data-stu-id="5df0d-113">**(Optional)** Latest MRTK, (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="5df0d-114">**(선택 사항)** 최신 유니버설 렌더링 파이프라인 패키지 (버전 10.5.1 이상 권장)</span><span class="sxs-lookup"><span data-stu-id="5df0d-114">**(Optional)** Latest Universal Render Pipeline package, (we recommend version 10.5.1 or later)</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="5df0d-115">Windows PC에서 VR 응용 프로그램을 작성 하는 경우 Mixed Reality OpenXR 플러그 인이 반드시 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="5df0d-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="5df0d-116">그러나 HP 반향 G2 컨트롤러에 대 한 컨트롤러 매핑을 사용자 지정 하거나 HoloLens 2와 VR 헤드셋 모두에서 작동 하는 앱을 빌드하는 경우에는 플러그 인을 설치 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5df0d-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="5df0d-117">Windows XR</span><span class="sxs-lookup"><span data-stu-id="5df0d-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="5df0d-118">Microsoft는 Unity 2020의 모든 새 프로젝트에 대해 Windows XR 플러그 인을 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5df0d-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="5df0d-119">그러나 Unity 2019을 사용 중이 고 ARCore/Arcore 장치와의 호환성을 위해 AR Foundation 2.0이 필요한 경우이 플러그 인이 해당 지원을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5df0d-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5df0d-120">Unity 2019에서이 플러그 인을 사용 하면 Azure 공간 앵커가 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5df0d-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="5df0d-121">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="5df0d-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="5df0d-122">Unity 2019 이전 버전을 사용 하는 경우에는 레거시 기본 제공 XR 지원을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5df0d-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="5df0d-123">Windows XR 플러그 인은 Unity 2019에서 작동 하지만 Azure 공간 앵커가 지원 되지 않기 때문에 권장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5df0d-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>