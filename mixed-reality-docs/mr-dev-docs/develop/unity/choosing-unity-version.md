---
title: Unity 버전 및 XR 플러그 인 선택
description: HoloLens 응용 프로그램 개발에 대 한 최신 Unity 및 XR 플러그 인 권장 사항을 최신으로 유지 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: f37dbdccf175a5cea9a647f0c14b90682b19dfb3
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906858"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="54a31-104">Unity 버전 및 XR 플러그 인 선택</span><span class="sxs-lookup"><span data-stu-id="54a31-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="54a31-105">현재 **Unity 2019.4 LTS를 설치 하 고 혼합 현실 개발용으로 레거시 기본 제공 XR를 사용 하는 것이 좋습니다** . 다른 Unity 구성으로 앱을 빌드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="54a31-106">Unity 2019.4 LTS (권장)</span><span class="sxs-lookup"><span data-stu-id="54a31-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="54a31-107">Microsoft의 최신 권장 Unity 구성-HoloLens 2 및 Windows Mixed Reality 개발은 **레거시 기본 제공 XR 지원을 사용 하는 Unity 2019.4 LTS** 입니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="54a31-108">Unity를 설치 하 고 관리 하는 가장 좋은 방법은 <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity 허브]</a>를 통하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="54a31-109">설치 된 경우 Unity 허브를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="54a31-110">**설치** 탭을 선택 하 고 **추가** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="54a31-111">Unity 2019.4 LTS를 선택 하 고 **다음** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Unity 허브 설치할 새 버전](images/unity-hub-img-2019.png)

3. <span data-ttu-id="54a31-113">**' 플랫폼 '** 아래에서 다음 구성 요소를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="54a31-114">**유니버설 Windows 플랫폼 빌드 지원**</span><span class="sxs-lookup"><span data-stu-id="54a31-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="54a31-115">**Windows 빌드 지원(IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="54a31-115">**Windows Build Support (IL2CPP)**</span></span>

![Unity 유니버설 Windows 플랫폼 빌드 지원 옵션](images/Unity_Install_Option_UWP_2019.png)

4. <span data-ttu-id="54a31-117">이러한 옵션 없이 Unity를 설치한 경우 Unity 허브의 **' 모듈 추가 '** 메뉴를 통해 unity를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity Windows 빌드 지원 옵션](images/Unity_Install_Option_UWP2_2019.png)

<span data-ttu-id="54a31-119">Unity 2019.4 LTS에서 레거시 기본 제공 XR를 시작 하려면 여기를 클릭 하세요.</span><span class="sxs-lookup"><span data-stu-id="54a31-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="54a31-120">레거시 기본 제공 XR 설정</span><span class="sxs-lookup"><span data-stu-id="54a31-120">Set up Legacy Built-in XR</span></span>](./xr-project-setup.md?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="54a31-121">Unity는 Unity 2019에서 레거시 기본 제공 XR 지원을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="54a31-122">Unity 2019는 새로운 XR 플러그 인 프레임 워크를 제공 하지만 Microsoft는 현재 Azure 공간 앵커가 AR Foundation 2와의 호환성 때문에 Unity 2019에서 해당 경로를 제안 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="54a31-123">Unity 2020에서 Azure 공간 앵커는 XR 플러그 인 프레임 워크 내에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="54a31-124">HoloLens 용 앱을 개발 하는 경우 (첫 번째 gen), 이러한 헤드셋은 unity 2019 LTS의 전체 수명 주기에 대 한 레거시 기본 제공 XR를 사용 하 여 2019 LTS를 2022 통해 계속 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="54a31-125">Unity 2020.3 LTS</span><span class="sxs-lookup"><span data-stu-id="54a31-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="54a31-126">**Unity 2020.3 LTS** 를 사용 하는 경우 Microsoft의 현재 권장 사항은 최신 **Mixed Reality OpenXR 플러그 인** 입니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-126">If you’re using **Unity 2020.3 LTS**, Microsoft’s current recommendation is the latest **Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="54a31-127">이전 2020.3 빌드의 알려진 성능 문제를 방지 하려면 Unity 패치 릴리스 2020.3.8 f1 이상을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-127">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

<span data-ttu-id="54a31-128">Mixed Reality OpenXR 플러그 인은 Ar설계도 Emanager 및 ARRaycastManager 구현을 제공 하 여 AR 기반 4.0을 완벽 하 게 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-128">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="54a31-129">그러면 HoloLens 2와 ARCore/Arcore 휴대폰 및 태블릿 범위에 도달할 때 적중 테스트 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-129">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

<span data-ttu-id="54a31-130">그러나 Unity 2020 LTS 프로젝트에 영향을 주는 알려진 문제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-130">However, there are known issues that affect Unity 2020 LTS projects:</span></span>

* <span data-ttu-id="54a31-131">URP (유니버설 렌더링 파이프라인) 10.5.0 또는 이전 버전은 HoloLens 2 장치에서 성능이 저하 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-131">The Universal Rendering Pipeline (URP) 10.5.0 or older has performance penalties on HoloLens 2 devices.</span></span>

<span data-ttu-id="54a31-132">지금 Unity 2020에서 새 프로젝트를 시작 하도록 선택 하는 경우 앱을 출시 하기 전에 업데이트 된 Unity 빌드 및 URP 패키지에 대 한 최신 주를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-132">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming weeks for updated Unity builds and URP packages before shipping your app.</span></span>  <span data-ttu-id="54a31-133">이렇게 하면 사용자가 홀로그램의 적절 한 안정성을 경험 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-133">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="54a31-134">OpenXR 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="54a31-134">Using the OpenXR plugin</span></span>](./xr-project-setup.md?tabs=openxr)

## <a name="unity-20211"></a><span data-ttu-id="54a31-135">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="54a31-135">Unity 2021.1</span></span>

<span data-ttu-id="54a31-136">초기 **Unity 2021.1** 빌드를 시도 하는 경우 Windows XR 플러그 인이 더 이상 사용 되지 않으므로 **OpenXR 플러그 인** 으로 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-136">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="54a31-137">Unity 2021.2부터 Windows XR 플러그 인이 더 이상 지원 되지 않으므로 OpenXR 플러그 인은 혼합 현실 개발의 유일한 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-137">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="54a31-138">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="54a31-138">Unity 2018.4 LTS</span></span>

<span data-ttu-id="54a31-139">Unity 2018.4 LTS를 사용 하는 프로젝트가 이미 있는 경우 Unity 엔진은 릴리스 후 2 년 동안 계속 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-139">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="54a31-140">Unity 2018 LTS는 2021의 스프링에서 서비스 종료에 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="54a31-140">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>