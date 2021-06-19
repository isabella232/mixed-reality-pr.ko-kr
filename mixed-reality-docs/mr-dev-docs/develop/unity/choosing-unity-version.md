---
title: Unity 버전 및 XR 플러그 인 선택
description: HoloLens 애플리케이션 개발을 위한 최신 Unity 및 XR 플러그 인 권장 사항을 최신 상태로 유지합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, mixed reality 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: 452692b1be98459cc242833149b1cfd91f0f4d4a
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394423"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="235b9-104">Unity 버전 및 XR 플러그 인 선택</span><span class="sxs-lookup"><span data-stu-id="235b9-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="235b9-105">현재 Unity **2019.4 LTS를 설치하고** Mixed Reality 개발을 위해 레거시 기본 제공 XR을 사용하는 것이 좋지만 다른 Unity 구성을 사용하여 앱을 빌드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="235b9-106">Unity 2019.4 LTS(권장)</span><span class="sxs-lookup"><span data-stu-id="235b9-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="235b9-107">HoloLens 2 및 Windows Mixed Reality 개발을 위한 Microsoft의 현재 권장 Unity 구성은 레거시 기본 제공 XR 지원을 **사용하는 Unity 2019.4 LTS입니다.**</span><span class="sxs-lookup"><span data-stu-id="235b9-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="235b9-108">Unity를 설치하고 관리하는 가장 좋은 방법은 <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>를 통하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="235b9-109">설치되면 Unity Hub를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="235b9-110">설치 **탭을** 선택하고 **추가를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="235b9-111">Unity 2019.4 LTS를 선택하고 **다음을** 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Unity 허브 새 버전 설치](images/unity-hub-img-2019.png)

3. <span data-ttu-id="235b9-113">**'플랫폼'에서** 다음 구성 요소를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="235b9-114">**유니버설 Windows 플랫폼 빌드 지원**</span><span class="sxs-lookup"><span data-stu-id="235b9-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="235b9-115">**Windows 빌드 지원(IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="235b9-115">**Windows Build Support (IL2CPP)**</span></span>

![Unity 유니버설 Windows 플랫폼 빌드 지원 옵션](images/Unity_Install_Option_UWP_2019.png)

4. <span data-ttu-id="235b9-117">이러한 옵션 없이 Unity를 설치한 경우 Unity Hub의 **'모듈 추가'** 메뉴를 통해 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity Windows 빌드 지원 옵션](images/Unity_Install_Option_UWP2_2019.png)

<span data-ttu-id="235b9-119">Unity 2019.4 LTS에서 레거시 기본 제공 XR을 시작하려면 다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="235b9-120">레거시 기본 제공 XR 설정</span><span class="sxs-lookup"><span data-stu-id="235b9-120">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="235b9-121">Unity는 Unity 2019부터 레거시 기본 제공 XR 지원이 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="235b9-122">Unity 2019는 새로운 XR 플러그 인 프레임워크를 제공하지만, Azure Spatial Anchors AR Foundation 2와의 비호환성으로 인해 Microsoft는 현재 Unity 2019에서 해당 경로를 권장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="235b9-123">Unity 2020에서 Azure Spatial Anchors XR 플러그 인 프레임워크 내에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="235b9-124">HoloLens(1세대)용 앱을 개발하는 경우 이러한 헤드셋은 Unity 2019 LTS의 전체 수명 주기 동안 Unity 2019 LTS에서 레거시 기본 제공 XR이 있는 Unity 2022 LTS에서 계속 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="235b9-125">Unity 2020.3 LTS</span><span class="sxs-lookup"><span data-stu-id="235b9-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="235b9-126">**Unity 2020.3 LTS를** 사용하는 경우 Microsoft의 현재 권장 사항은 **최신 Mixed Reality OpenXR 플러그 인** 입니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-126">If you’re using **Unity 2020.3 LTS**, Microsoft’s current recommendation is the latest **Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="235b9-127">이전 2020.3 빌드에서 알려진 성능 문제를 방지하려면 Unity 패치 릴리스 2020.3.8f1 이상 버전을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-127">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

<span data-ttu-id="235b9-128">Mixed Reality OpenXR 플러그 인은 ARPlaneManager 및 ARRaycastManager 구현을 제공하여 AR Foundation 4.0을 완벽하게 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-128">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="235b9-129">이렇게 하면 적중 테스트 코드를 한 번 작성한 다음, HoloLens 2 및 ARCore/ARKit 휴대폰 및 태블릿에 걸쳐 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-129">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

<span data-ttu-id="235b9-130">그러나 Unity 2020 LTS 프로젝트에 영향을 주는 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-130">However, there are known issues that affect Unity 2020 LTS projects:</span></span>

* <span data-ttu-id="235b9-131">URP(유니버설 렌더링 파이프라인) 10.5.0 이상은 HoloLens 2 디바이스에서 성능 저하가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-131">The Universal Rendering Pipeline (URP) 10.5.0 or older has performance penalties on HoloLens 2 devices.</span></span>

<span data-ttu-id="235b9-132">오늘 Unity 2020에서 새 프로젝트를 시작하도록 선택하는 경우 앱을 배송하기 전에 업데이트된 Unity 빌드 및 URP 패키지에 대한 후속 조치를 몇 주 동안 진행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-132">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming weeks for updated Unity builds and URP packages before shipping your app.</span></span>  <span data-ttu-id="235b9-133">이렇게 하면 사용자가 적절한 홀로그램 안정성을 경험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-133">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="235b9-134">OpenXR 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="235b9-134">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

## <a name="unity-20211"></a><span data-ttu-id="235b9-135">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="235b9-135">Unity 2021.1</span></span>

<span data-ttu-id="235b9-136">초기 **Unity 2021.1** 빌드를 시도하는 경우 Windows **XR 플러그 인이** 더 이상 사용되지 않으면 OpenXR 플러그 인 로 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-136">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="235b9-137">Unity 2021.2부터는 Windows XR 플러그 인이 더 이상 지원되지 않아 OpenXR 플러그 인이 Mixed Reality 개발을 위한 유일한 경로가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-137">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="235b9-138">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="235b9-138">Unity 2018.4 LTS</span></span>

<span data-ttu-id="235b9-139">Unity 2018.4 LTS를 사용하는 프로젝트가 이미 있는 경우 Unity 엔진은 릴리스 후 2년 동안 계속 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-139">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="235b9-140">Unity 2018 LTS는 2021년 봄 서비스 종료에 도달합니다.</span><span class="sxs-lookup"><span data-stu-id="235b9-140">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>