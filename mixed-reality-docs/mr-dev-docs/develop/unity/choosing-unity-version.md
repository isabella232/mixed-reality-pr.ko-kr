---
title: Unity 버전 및 XR 플러그 인 선택
description: HoloLens 애플리케이션 개발을 위한 최신 Unity 및 XR 플러그 인 권장 사항을 최신 상태로 유지합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, mixed reality 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: 11f930f014ff579db1f8845d52b7a2d65dd85d6b
ms.sourcegitcommit: 4ea9ba1ca1cde426b016111c4176a4b0a9c17553
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113080700"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="ed8ab-104">Unity 버전 및 XR 플러그 인 선택</span><span class="sxs-lookup"><span data-stu-id="ed8ab-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="ed8ab-105">현재 Mixed Reality 개발을 위해 **최신 Mixed Reality OpenXR 플러그 인이 있는 Unity 2020.3 LTS를 설치하는 것이 좋지만** 다른 Unity 구성으로 앱을 빌드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="ed8ab-106">Unity 2020.3 LTS(권장)</span><span class="sxs-lookup"><span data-stu-id="ed8ab-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="ed8ab-107">HoloLens 2 및 Windows Mixed Reality 개발을 위한 Microsoft의 현재 권장 Unity 구성은 **최신 Mixed Reality OpenXR 플러그 인이 있는 Unity 2020.3 LTS입니다.**</span><span class="sxs-lookup"><span data-stu-id="ed8ab-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="ed8ab-108">이전 2020.3 빌드에서 알려진 성능 문제를 방지하려면 Unity 패치 릴리스 2020.3.8f1 이상 버전을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-108">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed8ab-109">Unity 2020은 HoloLens(1세대)를 대상으로 하는 것을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="ed8ab-110">이러한 헤드셋은 **[Unity 2019 LTS의](#unity-20194-lts)** 전체 수명 주기에서 2022년 중간까지 레거시 기본 제공 XR이 있는 Unity 2019 LTS에서 계속 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>
>
> [!NOTE]
> <span data-ttu-id="ed8ab-111">Azure Remote Rendering Unity 2020을 지원하는 업데이트된 릴리스를 아직 제공하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-111">Azure Remote Rendering has not yet shipped an updated release supporting Unity 2020.</span></span>
>
> <span data-ttu-id="ed8ab-112">Unity 프로젝트에서 Azure Remote Rendering 사용하는 경우 업데이트된 패키지를 사용할 수 있을 때까지 프로젝트를 Unity 2020으로 업그레이드하는 것을 보류하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-112">If your Unity project uses Azure Remote Rendering, we recommend holding off on upgrading your project to Unity 2020 until an updated package is available.</span></span>

<span data-ttu-id="ed8ab-113">Unity를 설치하고 관리할 때 가장 좋은 방법은 <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-113">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="ed8ab-114">설치되면 Unity Hub를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-114">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="ed8ab-115">설치 **탭을** 선택하고 **추가를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-115">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="ed8ab-116">Unity 2020.3 LTS를 선택하고 **다음을** 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-116">Select Unity 2020.3 LTS and click **Next**</span></span>

![Unity 허브 새 버전 설치](images/unity-hub-img-01.png)

3. <span data-ttu-id="ed8ab-118">**'플랫폼'에서** 다음 구성 요소를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-118">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="ed8ab-119">**유니버설 Windows 플랫폼 빌드 지원**</span><span class="sxs-lookup"><span data-stu-id="ed8ab-119">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="ed8ab-120">**Windows 빌드 지원(IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="ed8ab-120">**Windows Build Support (IL2CPP)**</span></span>

![Unity 유니버설 Windows 플랫폼 빌드 지원 옵션](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="ed8ab-122">이러한 옵션 없이 Unity를 설치한 경우 Unity Hub의 **'모듈 추가'** 메뉴를 통해 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-122">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity Windows 빌드 지원 옵션](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="ed8ab-124">OpenXR 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="ed8ab-124">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="ed8ab-125">모든 새 프로젝트에 OpenXR을 사용하는 것이 좋습니다. Unity 2020.3 LTS는 [Windows XR 플러그 인](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-125">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span></span> <span data-ttu-id="ed8ab-126">이 플러그 인은 AR Foundation 4.0 지원과 같은 새로운 기능을 받지 못하지만 완전히 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-126">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="ed8ab-127">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="ed8ab-127">Unity 2019.4 LTS</span></span>

<span data-ttu-id="ed8ab-128">Unity 2019를 사용해야 하는 경우 **레거시 기본 제공 XR 에서 Unity 2019 LTS를** 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-128">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="ed8ab-129">Unity 2019.4 LTS에서 레거시 기본 제공 XR을 시작하려면 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-129">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ed8ab-130">레거시 기본 제공 XR 설정</span><span class="sxs-lookup"><span data-stu-id="ed8ab-130">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="ed8ab-131">Unity는 Unity 2019부터 레거시 기본 제공 XR 지원이 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-131">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="ed8ab-132">Unity 2019는 새로운 XR 플러그 인 프레임워크를 제공하지만, Azure Spatial Anchors AR Foundation 2와의 비호환성으로 인해 Microsoft는 현재 Unity 2019에서 해당 경로를 권장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-132">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="ed8ab-133">Unity 2020에서 Azure Spatial Anchors XR 플러그 인 프레임워크 내에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-133">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="ed8ab-134">HoloLens(1세대)용 앱을 개발하는 경우 이러한 헤드셋은 Unity 2019 LTS의 전체 수명 주기 동안 Unity 2019 LTS에서 레거시 기본 제공 XR이 있는 Unity 2022 LTS에서 계속 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-134">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="ed8ab-135">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="ed8ab-135">Unity 2021.1</span></span>

<span data-ttu-id="ed8ab-136">초기 **Unity 2021.1** 빌드를 시도하는 경우 Windows **XR 플러그 인이** 더 이상 사용되지 않으면 OpenXR 플러그 인 로 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-136">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="ed8ab-137">Unity 2021.2부터는 Windows XR 플러그 인이 더 이상 지원되지 않아 OpenXR 플러그 인이 Mixed Reality 개발을 위한 유일한 경로가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-137">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="ed8ab-138">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="ed8ab-138">Unity 2018.4 LTS</span></span>

<span data-ttu-id="ed8ab-139">Unity 2018.4 LTS를 사용하는 프로젝트가 이미 있는 경우 Unity 엔진은 릴리스 후 2년 동안 계속 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-139">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="ed8ab-140">Unity 2018 LTS는 2021년 봄 서비스 종료에 도달합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8ab-140">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
