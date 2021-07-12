---
title: Unity 버전 및 XR 플러그 인 선택
description: HoloLens 응용 프로그램 개발에 대 한 최신 Unity 및 XR 플러그 인 권장 사항을 최신으로 유지 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603684"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="43b64-104">Unity 버전 및 XR 플러그 인 선택</span><span class="sxs-lookup"><span data-stu-id="43b64-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="43b64-105">현재 혼합 현실 개발용으로 **최신 Mixed Reality OpenXR 플러그 인 Unity 2020.3 LTS를 설치 하는 것이 좋습니다** . 또한 다른 Unity 구성으로 앱을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="43b64-106">Unity 2020.3 LTS (권장)</span><span class="sxs-lookup"><span data-stu-id="43b64-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="43b64-107">HoloLens 2 및 Windows Mixed Reality 개발에 대 한 Microsoft의 현재 권장 unity 구성은 **최신 Mixed Reality OpenXR 플러그 인을 사용 하는 Unity 2020.3 lts** 입니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="43b64-108">이전 2020.3 빌드의 알려진 성능 문제를 방지 하려면 Unity 패치 릴리스 2020.3.8 f1 이상을 사용 **해야 합니다** .</span><span class="sxs-lookup"><span data-stu-id="43b64-108">You **must** use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43b64-109">Unity 2020은 HoloLens (첫 번째 gen)를 대상으로 하는 것을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="43b64-110">이러한 헤드셋은 unity 2019 LTS의 전체 수명 주기에 대 한 레거시 기본 제공 XR를 사용 하는 **[unity 2019 lts](#unity-20194-lts)** 에서 중부 2022를 통해 계속 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="43b64-111">Unity를 설치 하 고 관리 하는 가장 좋은 방법은 **Unity 허브** 를 통하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-111">The best way to install and manage Unity is through the **Unity Hub**:</span></span>

1. <span data-ttu-id="43b64-112"><a href="https://unity3d.com/get-unity/download" target="_blank">**Unity 허브**</a>를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-112">Install <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>.</span></span>
2. <span data-ttu-id="43b64-113">**설치** 탭을 선택 하 고 **추가** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-113">Select the **Installs** tab and choose **Add**.</span></span>
3. <span data-ttu-id="43b64-114">**Unity 2020.3 LTS** 를 선택 하 고 **다음** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-114">Select **Unity 2020.3 LTS** and click **Next**.</span></span>

![Unity 허브 설치 새 버전](images/unity-hub-img-01.png)

4. <span data-ttu-id="43b64-116">**' 플랫폼 '** 아래에서 다음 구성 요소를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-116">Check the following components under **'Platforms'**:</span></span>
    * <span data-ttu-id="43b64-117">**유니버설 Windows 플랫폼 빌드 지원**</span><span class="sxs-lookup"><span data-stu-id="43b64-117">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="43b64-118">**Windows 빌드 지원(IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="43b64-118">**Windows Build Support (IL2CPP)**</span></span>

![Unity 유니버설 Windows 플랫폼 빌드 지원 옵션](../images/Unity_Install_Option_UWP.png)

5. <span data-ttu-id="43b64-120">이러한 옵션을 사용 하지 않고 Unity를 이전에 설치한 경우 Unity 허브의 **' 모듈 추가 '** 메뉴를 통해 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-120">If you previously installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity Windows 빌드 지원 옵션](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="43b64-122">Unity 2020.3을 설치한 후에는 Mixed Reality OpenXR 플러그 인을 사용 하 여 프로젝트를 만들거나 기존 프로젝트를 업그레이드 하기 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-122">Once you have Unity 2020.3 installed, get started creating a project or upgrading an existing project using the Mixed Reality OpenXR plugin:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="43b64-123">OpenXR 플러그 인을 사용 하 여 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="43b64-123">Set up your project with the OpenXR plugin</span></span>](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="43b64-124">모든 새 프로젝트에 OpenXR를 사용 하는 것이 좋지만 Unity 2020.3 lts는 [Windows XR 플러그 인](xr-project-setup.md?tabs=windowsxr)도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](xr-project-setup.md?tabs=windowsxr).</span></span> <span data-ttu-id="43b64-125">이 플러그 인은 AR 기반 4.0 지원과 같은 새로운 기능을 받지 않지만 완전히 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-125">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="43b64-126">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="43b64-126">Unity 2019.4 LTS</span></span>

<span data-ttu-id="43b64-127">Unity 2019을 사용 해야 하는 경우 **unity 2019 LTS와 레거시 기본 제공 XR** 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-127">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="43b64-128">Unity 2019.4 LTS에서 레거시 기본 제공 XR를 시작 하려면 여기를 클릭 하세요.</span><span class="sxs-lookup"><span data-stu-id="43b64-128">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="43b64-129">레거시 기본 제공 XR를 사용 하 여 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="43b64-129">Set up your project with Legacy Built-in XR</span></span>](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="43b64-130">Unity는 Unity 2019에서 레거시 기본 제공 XR 지원을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-130">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="43b64-131">Unity 2019는 새로운 XR 플러그 인 프레임 워크를 제공 하지만 Microsoft는 현재 Azure 공간 앵커가 AR Foundation 2와의 호환성 때문에 Unity 2019에서 해당 경로를 제안 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-131">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="43b64-132">Unity 2020에서 Azure 공간 앵커는 XR 플러그 인 프레임 워크 내에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-132">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="43b64-133">HoloLens (첫 번째 gen) 용 앱을 개발 하는 경우, 이러한 헤드셋은 unity 2019 lts의 전체 수명 주기에 대 한 레거시 기본 제공 XR를 사용 하 여 2019 lts를 2022 통해 lts에서 계속 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-133">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20212"></a><span data-ttu-id="43b64-134">Unity 2021.2</span><span class="sxs-lookup"><span data-stu-id="43b64-134">Unity 2021.2</span></span>

<span data-ttu-id="43b64-135">초기 **Unity 2021.2** 빌드를 시도 하는 경우 [**Mixed Reality OpenXR 플러그**](xr-project-setup.md?tabs=openxr)인을 시작 하세요.</span><span class="sxs-lookup"><span data-stu-id="43b64-135">If you are trying out early **Unity 2021.2** builds, get started with the [**Mixed Reality OpenXR plugin**](xr-project-setup.md?tabs=openxr).</span></span> <span data-ttu-id="43b64-136">OpenXR 플러그 인은 Windows XR 플러그 인을 지 원하는 최종 unity 버전이 unity 2021.1 이기 때문에 unity 2021.2 이상에서 혼합 현실 개발의 유일한 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-136">The OpenXR plugin is the only path for mixed reality development in Unity 2021.2 and later, as the final Unity version to support the Windows XR plugin was Unity 2021.1.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="43b64-137">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="43b64-137">Unity 2018.4 LTS</span></span>

<span data-ttu-id="43b64-138">Unity 2018.4 LTS가 Unity의 2 년 Long-Term 지원 기간 끝에 도달 하 여 프로젝트를 계속 실행 하지만 Unity에서 업데이트를 더 이상 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-138">Unity 2018.4 LTS has reached the end of Unity's two-year Long-Term Support window and is no longer receiving updates from Unity, although your projects will continue to run.</span></span>

<span data-ttu-id="43b64-139">Unity 2018 프로젝트가 있는 경우 Unity 2020.3 LTS 및 Mixed Reality OpenXR 플러그 인으로의 마이그레이션을 계획 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="43b64-139">If you have a Unity 2018 project, you should consider planning for a migration forward to Unity 2020.3 LTS and the Mixed Reality OpenXR plugin.</span></span>