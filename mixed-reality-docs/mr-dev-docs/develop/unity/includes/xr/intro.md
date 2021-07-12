---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603719"
---
# <a name="openxr"></a>[<span data-ttu-id="b2f3f-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b2f3f-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="b2f3f-102">Mixed Reality OpenXR 플러그 인은 **Unity 2020 LTS** 이상에 대한 **Microsoft의 권장 사항입니다.**</span><span class="sxs-lookup"><span data-stu-id="b2f3f-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for **Unity 2020 LTS** or later.</span></span> <span data-ttu-id="b2f3f-103">향후 새로운 기능이 개발되면 향후 Mixed Reality OpenXR 플러그 인에만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="b2f3f-104">Mixed Reality OpenXR 플러그 인은 ARPlaneManager 및 ARRaycastManager 구현을 제공하여 AR Foundation 4.0을 완벽하게 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="b2f3f-105">이렇게 하면 HoloLens 2 및 ARCore/ARKit 휴대폰 및 태블릿에 걸쳐 있는 광선 캐스팅 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="b2f3f-106">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="b2f3f-106">Prerequisites</span></span> 

* <span data-ttu-id="b2f3f-107">[HoloLens 2 개발을 위한](../../../install-the-tools.md?tabs=unity#installation-checklist) 최신 도구</span><span class="sxs-lookup"><span data-stu-id="b2f3f-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="b2f3f-108">최신 Unity 2020.3 LTS: 버전 2020.3.8f1 이상</span><span class="sxs-lookup"><span data-stu-id="b2f3f-108">Latest Unity 2020.3 LTS: version 2020.3.8f1 or later</span></span>

### <a name="recommended-package-versions"></a><span data-ttu-id="b2f3f-109">권장 패키지 버전</span><span class="sxs-lookup"><span data-stu-id="b2f3f-109">Recommended package versions</span></span>

<span data-ttu-id="b2f3f-110">이 페이지의 지침에서는 HoloLens 2 또는 Windows Mixed Reality 앱을 배포하는 데 필요한 핵심 Unity OpenXR 패키지를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-110">The instructions in this page will set you up with the core Unity OpenXR packages required to deploy HoloLens 2 or Windows Mixed Reality apps:</span></span>

* <span data-ttu-id="b2f3f-111">Unity OpenXR 플러그 인: 버전 1.2 이상</span><span class="sxs-lookup"><span data-stu-id="b2f3f-111">Unity OpenXR plugin: version 1.2 or later</span></span>
* <span data-ttu-id="b2f3f-112">Mixed Reality OpenXR 플러그 인: 버전 1.0.0 이상</span><span class="sxs-lookup"><span data-stu-id="b2f3f-112">Mixed Reality OpenXR plugin: version 1.0.0 or later</span></span>

<span data-ttu-id="b2f3f-113">프로젝트에서 다음 패키지를 사용하는 경우 아래에 나열된 최소 버전 이상을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-113">If you use the following packages in your project, you will need to ensure that you use at least the minimum versions listed below:</span></span>

* <span data-ttu-id="b2f3f-114">MRTK: 버전 2.7.2 이상</span><span class="sxs-lookup"><span data-stu-id="b2f3f-114">MRTK: version 2.7.2 or later</span></span>
* <span data-ttu-id="b2f3f-115">AR Foundation: 버전 4.1.1 이상</span><span class="sxs-lookup"><span data-stu-id="b2f3f-115">AR Foundation: version 4.1.1 or later</span></span>
* <span data-ttu-id="b2f3f-116">URP(유니버설 렌더링 파이프라인): 버전 10.5.1 이상</span><span class="sxs-lookup"><span data-stu-id="b2f3f-116">Universal Render Pipeline (URP): version 10.5.1 or later</span></span>
* <span data-ttu-id="b2f3f-117">Azure Spatial Anchors: 버전 2.10 이상</span><span class="sxs-lookup"><span data-stu-id="b2f3f-117">Azure Spatial Anchors: version 2.10 or later</span></span>
* <span data-ttu-id="b2f3f-118">Azure Remote Rendering: 버전 1.0.15 이상</span><span class="sxs-lookup"><span data-stu-id="b2f3f-118">Azure Remote Rendering: version 1.0.15 or later</span></span>

> [!NOTE]
> <span data-ttu-id="b2f3f-119">Windows PC에서 VR 애플리케이션을 빌드하는 경우 Mixed Reality OpenXR 플러그 인이 꼭 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-119">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not strictly required.</span></span> <span data-ttu-id="b2f3f-120">그러나 HP Reverb G2 컨트롤러에 대한 입력 바인딩을 설정하거나 HoloLens 2 헤드셋과 VR 헤드셋 모두에서 작동하는 앱을 빌드하는 경우 플러그 인을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-120">However, you'll want to install the plugin if you're setting up input bindings for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="b2f3f-121">Windows Xr</span><span class="sxs-lookup"><span data-stu-id="b2f3f-121">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="b2f3f-122">Unity 2020의 새 프로젝트에는 Windows XR 플러그 인을 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-122">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>  <span data-ttu-id="b2f3f-123">대신 Mixed Reality OpenXR 플러그 인을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-123">Instead, you should use the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="b2f3f-124">그러나 Unity 2019를 사용하고 있고 ARCore/ARKit 디바이스와의 호환성을 위해 AR Foundation 2.0이 필요한 경우 이 플러그 인을 통해 해당 지원을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-124">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b2f3f-125">Unity 2019에서 이 플러그 인을 사용하는 것은 Azure Spatial Anchors 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-125">Using this plugin in Unity 2019 is not compatible with Azure Spatial Anchors.</span></span>

# <a name="legacy-xr"></a>[<span data-ttu-id="b2f3f-126">Legacy XR</span><span class="sxs-lookup"><span data-stu-id="b2f3f-126">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="b2f3f-127">**Unity 2019** 이하를 사용 중인 경우 레거시 기본 **제공 XR 지원을** 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-127">If you're still on **Unity 2019** or earlier, Microsoft recommends using the **Legacy Built-in XR support**.</span></span>

<span data-ttu-id="b2f3f-128">Windows XR 플러그 인은 Unity 2019에서 작동하지만 이 플러그 인은 Unity 2019의 Azure Spatial Anchors 호환되지 않으므로 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-128">While the Windows XR plugin is functional on Unity 2019, it's not recommended because this plugin is not compatible with Azure Spatial Anchors on Unity 2019.</span></span>

<span data-ttu-id="b2f3f-129">새 프로젝트를 시작하는 경우 [대신 Unity 2020을 설치하고](../../choosing-unity-version.md) Mixed Reality OpenXR 플러그 인을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b2f3f-129">If you're starting a new project, we recommend [installing Unity 2020 instead](../../choosing-unity-version.md) and using the Mixed Reality OpenXR plugin.</span></span>