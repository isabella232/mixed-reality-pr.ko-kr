---
ms.openlocfilehash: ca3589364fb27c3f8087572113f09e48d30e087e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394577"
---
# <a name="openxr"></a>[<span data-ttu-id="ed547-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ed547-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="ed547-102">Mixed Reality OpenXR 플러그 인은 Unity 2020 LTS 이상에 대한 **Microsoft의 권장 사항입니다.**</span><span class="sxs-lookup"><span data-stu-id="ed547-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="ed547-103">향후 새로운 기능이 개발되면 향후 Mixed Reality OpenXR 플러그 인에만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed547-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="ed547-104">Mixed Reality OpenXR 플러그 인은 ARPlaneManager 및 ARRaycastManager 구현을 제공하여 AR Foundation 4.0을 완벽하게 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ed547-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="ed547-105">이렇게 하면 HoloLens 2 및 ARCore/ARKit 휴대폰 및 태블릿에 걸쳐 있는 광선 캐스팅 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed547-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ed547-106">필수 조건</span><span class="sxs-lookup"><span data-stu-id="ed547-106">Prerequisites</span></span> 

* <span data-ttu-id="ed547-107">[HoloLens 2 개발을 위한](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist) 최신 도구</span><span class="sxs-lookup"><span data-stu-id="ed547-107">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="ed547-108">최신 Unity 2020.3 LTS(2020.3.8f1 이상 권장)</span><span class="sxs-lookup"><span data-stu-id="ed547-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="ed547-109">최소 버전</span><span class="sxs-lookup"><span data-stu-id="ed547-109">Minimum versions</span></span>

<span data-ttu-id="ed547-110">이 페이지의 지침은 아래에 나열된 가장 최신의 가장 큰 Unity 및 OpenXR 요구 사항을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ed547-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="ed547-111">최신 Unity OpenXR 플러그 인(1.2 이상 권장)</span><span class="sxs-lookup"><span data-stu-id="ed547-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="ed547-112">최신 Mixed Reality OpenXR 플러그 인(버전 1.0.0 이상 권장)</span><span class="sxs-lookup"><span data-stu-id="ed547-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="ed547-113">**(선택 사항)** 최신 MRTK(버전 2.7 이상 권장)</span><span class="sxs-lookup"><span data-stu-id="ed547-113">**(Optional)** Latest MRTK, (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="ed547-114">**(선택 사항)** 최신 유니버설 렌더링 파이프라인 패키지(버전 10.5.1 이상 권장)</span><span class="sxs-lookup"><span data-stu-id="ed547-114">**(Optional)** Latest Universal Render Pipeline package, (we recommend version 10.5.1 or later)</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="ed547-115">Windows PC VR 애플리케이션을 빌드하는 경우 Mixed Reality OpenXR 플러그 인이 반드시 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="ed547-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="ed547-116">그러나 HP Reverb G2 컨트롤러에 대한 컨트롤러 매핑을 사용자 지정하거나 HoloLens 2 및 VR 헤드셋 둘 다에서 작동하는 앱을 빌드하는 경우 플러그 인을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed547-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="ed547-117">Windows XR</span><span class="sxs-lookup"><span data-stu-id="ed547-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="ed547-118">Microsoft는 Unity 2020의 새 프로젝트에 Windows XR 플러그 인을 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ed547-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="ed547-119">그러나 Unity 2019를 사용하고 있고 ARCore/ARKit 디바이스와의 호환성을 위해 AR Foundation 2.0이 필요한 경우 이 플러그 인을 통해 해당 지원을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed547-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed547-120">Unity 2019에서 이 플러그 인을 사용하면 Azure Spatial Anchors 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ed547-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="ed547-121">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="ed547-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="ed547-122">Unity 2019 이하를 사용 중인 경우 레거시 기본 제공 XR 지원을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ed547-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="ed547-123">Windows XR 플러그 인은 Unity 2019에서 작동하지만 Azure Spatial Anchors 지원되지 않으므로 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ed547-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>