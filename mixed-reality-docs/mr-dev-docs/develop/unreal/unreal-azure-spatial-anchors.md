---
title: Unreal의 Azure Spatial Anchors
description: Unreal 엔진에서 Azure Spatial Anchors 만들기에 대한 개요입니다.
author: hferrone
ms.author: jacksonf
ms.date: 07/01/2020
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, azure development, spatial anchors, 혼합 현실, 개발, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 홀로그램, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 4714957c3ddab188a776c86f839208759c9d20de
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609744"
---
# <a name="azure-spatial-anchors-in-unreal"></a><span data-ttu-id="f8f6e-104">Unreal의 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="f8f6e-104">Azure Spatial Anchors in Unreal</span></span>

<span data-ttu-id="f8f6e-105">Azure Spatial Anchors는 Microsoft Mixed Reality 서비스이며, 증강 현실 디바이스를 사용하여 실제 세계에서 앵커 위치를 검색, 공유 및 유지하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-105">Azure Spatial Anchors is a Microsoft Mixed Reality service, allowing augmented reality devices to discover, share, and persist anchor points in the physical world.</span></span> <span data-ttu-id="f8f6e-106">아래 설명서는 Azure Spatial Anchors 서비스를 Unreal 프로젝트에 통합하는 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-106">Documentation below provides instructions for integrating the Azure Spatial Anchors service into an Unreal project.</span></span> <span data-ttu-id="f8f6e-107">자세한 내용은 [Azure Spatial Anchors 서비스](https://azure.microsoft.com/services/spatial-anchors/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-107">If you're looking for more information, check out the [Azure Spatial Anchors service](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

> [!NOTE]
> <span data-ttu-id="f8f6e-108">이제 Unreal Engine 4.26은 iOS 또는 Android를 대상으로 하는 개발자를 위해 ARKit 및 ARCore 지원을 위한 플러그 인을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-108">Unreal Engine 4.26 now has plugins for ARKit and ARCore support if you're targeting iOS or Android.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8f6e-109">로컬 앵커는 디바이스에 저장되는 반면, Azure Spatial Anchors는 클라우드에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="f8f6e-110">앵커를 로컬로 디바이스에 저장하려는 경우, 해당 프로세스를 안내하는 [로컬 Spatial Anchors](unreal-spatial-anchors.md) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-110">If you're looking to store your anchors locally on a device, we have a [Local Spatial Anchors](unreal-spatial-anchors.md) document that can walk you through the process.</span></span> <span data-ttu-id="f8f6e-111">로컬 및 Azure 앵커는 동일한 프로젝트에서 충돌 없이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f8f6e-112">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="f8f6e-112">Prerequisites</span></span>

<span data-ttu-id="f8f6e-113">이 가이드를 완료하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-113">To complete this guide, make sure you have:</span></span>

- <span data-ttu-id="f8f6e-114">[Unreal 버전 4.25](https://www.unrealengine.com/get-now) 이상 설치</span><span class="sxs-lookup"><span data-stu-id="f8f6e-114">Installed [Unreal version 4.25](https://www.unrealengine.com/get-now) or later</span></span>
- <span data-ttu-id="f8f6e-115">Unreal에 [HoloLens 2 프로젝트](tutorials/unreal-uxt-ch1.md) 설정</span><span class="sxs-lookup"><span data-stu-id="f8f6e-115">A [HoloLens 2 project](tutorials/unreal-uxt-ch1.md) setup in Unreal</span></span> 
- <span data-ttu-id="f8f6e-116">[Azure Spatial Anchors 개요](https://docs.microsoft.com/azure/spatial-anchors/overview) 꼼꼼히 읽기</span><span class="sxs-lookup"><span data-stu-id="f8f6e-116">Read through the [Azure Spatial Anchors overview](https://docs.microsoft.com/azure/spatial-anchors/overview)</span></span>
- <span data-ttu-id="f8f6e-117">C++ 및 Unreal에 대한 기본 지식</span><span class="sxs-lookup"><span data-stu-id="f8f6e-117">Basic knowledge on C++ and Unreal</span></span>

## <a name="getting-azure-spatial-anchors-account-info"></a><span data-ttu-id="f8f6e-118">Azure Spatial Anchors 계정 정보 얻기</span><span class="sxs-lookup"><span data-stu-id="f8f6e-118">Getting Azure Spatial Anchors account info</span></span>

<span data-ttu-id="f8f6e-119">프로젝트에서 Azure Spatial Anchors를 사용하기 전에 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-119">Before using Azure Spatial Anchors in your project, you need to:</span></span>
* <span data-ttu-id="f8f6e-120">[Spatial Anchors 리소스를 만들고](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) 아래 나열된 계정 필드를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-120">[Create a spatial anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) and copy the account fields listed below.</span></span> <span data-ttu-id="f8f6e-121">다음 값은 애플리케이션의 계정으로 사용자를 인증하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-121">These values are used to authenticate users with your application's account:</span></span>
    * <span data-ttu-id="f8f6e-122">**계정 ID**</span><span class="sxs-lookup"><span data-stu-id="f8f6e-122">**Account ID**</span></span>
    * <span data-ttu-id="f8f6e-123">**계정 키**</span><span class="sxs-lookup"><span data-stu-id="f8f6e-123">**Account Key**</span></span>

<span data-ttu-id="f8f6e-124">자세한 내용은 [Azure Spatial Anchors 인증](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) 문서를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-124">Check out the [Azure Spatial Anchors authentication](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) docs for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="f8f6e-125">Unreal 4.25의 Azure Spatial Anchors는 Azure AD 인증 토큰을 지원하지 않지만 이후 릴리스에서는 이 기능에 대한 지원이 제공될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-125">Azure Spatial Anchors in Unreal 4.25 does not support Azure AD authentication tokens, but support for this functionality will be coming in a later release.</span></span>

## <a name="adding-azure-spatial-anchors-plugins"></a><span data-ttu-id="f8f6e-126">Azure Spatial Anchors 플러그 인 추가</span><span class="sxs-lookup"><span data-stu-id="f8f6e-126">Adding Azure Spatial Anchors plugins</span></span>

<span data-ttu-id="f8f6e-127">다음을 수행하여 Unreal 에디터에서 Azure Spatial Anchors 플러그 인을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-127">Enable the Azure Spatial Anchors plugins in the Unreal editor by:</span></span>
1. <span data-ttu-id="f8f6e-128">**편집 > 플러그 인** 을 클릭하고 **AzureSpatialAnchors** 및 **AzureSpatialAnchorsForWMR** 을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-128">Clicking **Edit > Plugins** and searching for **AzureSpatialAnchors** and **AzureSpatialAnchorsForWMR**.</span></span>
2. <span data-ttu-id="f8f6e-129">두 플러그 인의 **사용** 확인란을 선택하여 애플리케이션에서 Azure Spatial Anchors 청사진 라이브러리에 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-129">Select the **Enabled** checkbox in both plugins to allow access to the Azure Spatial Anchors blueprint libraries in your application.</span></span>

![Unreal 편집기의 Spatial Anchors 플러그 인의 스크린샷](images/asa-unreal/unreal-spatial-anchors-img-01.png)

<span data-ttu-id="f8f6e-131">완료되면 Unreal 편집기를 다시 시작하여 플러그 인 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-131">Once that's done, restart the Unreal Editor for the plugin changes to take effect.</span></span> <span data-ttu-id="f8f6e-132">이제 프로젝트에서 Azure Spatial Anchors를 사용할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-132">The project is now ready to use Azure Spatial Anchors.</span></span>

## <a name="starting-a-spatial-anchors-session"></a><span data-ttu-id="f8f6e-133">Spatial Anchors 세션 시작</span><span class="sxs-lookup"><span data-stu-id="f8f6e-133">Starting a Spatial Anchors session</span></span>

<span data-ttu-id="f8f6e-134">Azure Spatial Anchors 세션을 사용하면 클라이언트 애플리케이션에서 Azure Spatial Anchors 서비스와 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-134">An Azure Spatial Anchors session allows client applications to communicate with the Azure Spatial Anchors service.</span></span> <span data-ttu-id="f8f6e-135">Azure Spatial Anchors를 만들고 유지하고 공유하려면 Azure Spatial Anchors 세션을 만들고 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-135">You'll need to create and start an Azure Spatial Anchors session to create, persist, and share Azure Spatial Anchors:</span></span>

1. <span data-ttu-id="f8f6e-136">애플리케이션에서 사용 중인 Pawn에 대한 청사진을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-136">Open the blueprint for the Pawn you're using in the application.</span></span>
2. <span data-ttu-id="f8f6e-137">**계정 ID** 와 **계정 키** 에 대한 두 문자열 변수를 추가한 다음, Azure Spatial Anchors 계정에서 해당 값을 할당하여 세션을 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-137">Add two string variables for the **Account ID** and **Account Key**, then assign the corresponding values from your Azure Spatial Anchors account to authenticate the session.</span></span>

![azure spatial anchors 계정 id, 키 및 변수 유형이 강조 표시된 세부 정보 패널의 스크린샷](images/asa-unreal/unreal-spatial-anchors-img-02.png)

<span data-ttu-id="f8f6e-139">다음을 수행하여 Azure Spatial Anchors 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-139">Start an Azure Spatial Anchors session by:</span></span>
1. <span data-ttu-id="f8f6e-140">HoloLens 애플리케이션에서 **AR 세션** 을 실행 중인지 확인합니다. AR 세션이 실행될 때까지 Azure Spatial Anchors 세션을 시작할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-140">Checking that an **AR Session** is running in the HoloLens application, as the Azure Spatial Anchors session can't start until an AR Session is running.</span></span> <span data-ttu-id="f8f6e-141">설정되어 있지 않으면 [AR 세션 자산을 만듭니다](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="f8f6e-141">If you don't have one setup, [create an AR Session asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>
2. <span data-ttu-id="f8f6e-142">**Azure Spatial Anchors 세션 시작** 사용자 지정 이벤트를 추가하고 아래 스크린샷에 표시된 대로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-142">Adding the **Start Azure Spatial Anchors Session** custom event and configure it as shown in the screenshot below.</span></span>
    * <span data-ttu-id="f8f6e-143">세션을 만들면 기본적으로 세션이 시작되지 않으므로 Azure Spatial Anchors 서비스를 사용하여 인증할 세션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-143">Creating a session doesn't start the session by default, which allows you to configure the session for authentication with the Azure Spatial Anchors service.</span></span>

![starting azure spatial anchors 세션 사용자 지정 이벤트의 청사진](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. <span data-ttu-id="f8f6e-145">**계정 ID** 및 **계정 키** 를 제공하도록 Azure Spatial Anchors 세션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-145">Configure the Azure Spatial Anchors session to provide the **Account ID** and **Account Key**.</span></span>

![계정 ID 및 키가 추가된 config 세션 함수의 청사진](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. <span data-ttu-id="f8f6e-147">애플리케이션이 Azure Spatial Anchors를 만들고 찾을 수 있도록 Azure Spatial Anchors 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-147">Start the Azure Spatial Anchors session, allowing the application to create and locate Azure Spatial Anchors.</span></span>

![azure spatial anchors 세션 시작 함수의 청사진](images/asa-unreal/unreal-spatial-anchors-img-05.png)

<span data-ttu-id="f8f6e-149">서비스를 더 이상 사용하지 않는 경우 이벤트 그래프 청사진에서 Azure Spatial Anchors 리소스를 정리하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-149">It's good practice to clean up Azure Spatial Anchors resources in your Event Graph blueprint when you're no longer using the service:</span></span>

1. <span data-ttu-id="f8f6e-150">Azure Spatial Anchors 세션을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-150">Stop the Azure Spatial Anchors session.</span></span> <span data-ttu-id="f8f6e-151">세션은 더 이상 실행되지 않지만 연결된 리소스가 Azure Spatial Anchors 플러그 인에 여전히 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-151">The session will no longer be running, but its associated resources will still exist in the Azure Spatial Anchors plugin.</span></span>

![stop azure spatial anchors 세션 사용자 지정 이벤트 및 stop 세션 함수의 청사진](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. <span data-ttu-id="f8f6e-153">Azure Spatial Anchors 세션을 제거하여 Azure Spatial Anchors 플러그 인에 여전히 알려져 있는 Azure Spatial Anchors 세션 리소스를 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-153">Destroy the Azure Spatial Anchors session to clean up any Azure Spatial Anchors session resources still known to the Azure Spatial Anchors plugin.</span></span>

![destroy 세션 함수의 청사진](images/asa-unreal/unreal-spatial-anchors-img-07.png)

<span data-ttu-id="f8f6e-155">이벤트 그래프 청사진은 아래 스크린샷과 같은 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-155">Your Event Graph blueprint should look like the screenshot below:</span></span>

![azure spatial anchor 세션 설정의 전체 이벤트 그래프의 청사진](images/asa-unreal/unreal-spatial-anchors-img-08.png)

## <a name="creating-an-anchor"></a><span data-ttu-id="f8f6e-157">앵커 만들기</span><span class="sxs-lookup"><span data-stu-id="f8f6e-157">Creating an anchor</span></span>

<span data-ttu-id="f8f6e-158">Azure Spatial Anchor는 증강 현실 애플리케이션 공간에서 실제 세계 포즈를 나타내며, 증강 현실 콘텐츠를 실제 위치에 고정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-158">An Azure Spatial Anchor represents a physical world pose in the augmented reality application space, which locks augmented reality content to physical locations.</span></span> <span data-ttu-id="f8f6e-159">Azure Spatial Anchors는 여러 사용자가 서로 공유할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-159">Azure Spatial Anchors can also be shared among different users.</span></span> <span data-ttu-id="f8f6e-160">이러한 공유를 통해 다른 디바이스에서 그려진 증강 현실 콘텐츠를 실제 세계에서 동일한 위치에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-160">This sharing allows augmented reality content drawn on different devices to be positioned in the same location in the physical world.</span></span> 

<span data-ttu-id="f8f6e-161">새 Azure Spatial Anchor를 만들려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-161">To create a new Azure Spatial Anchor:</span></span>
1. <span data-ttu-id="f8f6e-162">Azure Spatial Anchors 세션이 실행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-162">Check that an Azure Spatial Anchors session is running.</span></span> <span data-ttu-id="f8f6e-163">Azure Spatial Anchors 세션이 실행되고 있지 않으면 애플리케이션에서 Azure Spatial Anchor를 만들거나 유지할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-163">The application can't create or persist an Azure Spatial Anchor when no Azure Spatial Anchors session is running.</span></span>

![create azure spatial anchors 사용자 지정 이벤트의 청사진](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. <span data-ttu-id="f8f6e-165">위치를 유지해야 하는 Unreal **[장면 구성 요소](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** 를 만들거나 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-165">Create or obtain an Unreal **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** that should have its location persisted.</span></span> 
    * <span data-ttu-id="f8f6e-166">아래 이미지에서는 **앵커가 필요한 장면 구성 요소** 라는 구성 요소가 변수로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-166">In the below image, the **Scene Component Needing Anchor** component is used as a variable.</span></span> <span data-ttu-id="f8f6e-167">Unreal 장면 구성 요소는 [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) 및 Azure Spatial Anchor에 대해 애플리케이션 월드 변환을 설정하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-167">An Unreal Scene Component is needed to establish an application world transform for an [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) and Azure Spatial Anchor.</span></span>

![장면 구성 요소가 포함된 create azure spatial anchors 사용자 지정 이벤트의 청사진](images/asa-unreal/unreal-spatial-anchors-img-10.png)

<span data-ttu-id="f8f6e-169">Unreal 장면 구성 요소에 대한 Azure Spatial Anchor를 생성하고 저장하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-169">To construct and save an Azure Spatial Anchor for an Unreal Scene Component:</span></span>
1. <span data-ttu-id="f8f6e-170">Unreal 장면 구성 요소에 대한 [Pin 구성 요소](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html)를 호출하고 장면 구성 요소의 **월드 변환** 을 AR Pin에 사용되는 월드 변환으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-170">Call the [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) for the Unreal Scene Component and specify the Scene Component's **World Transform** as the World Transform used for the AR Pin.</span></span>
    * <span data-ttu-id="f8f6e-171">Unreal은 Azure Spatial Anchor를 만드는 데 사용되는 AR Pin을 사용하여 애플리케이션 공간에서 AR 포인트를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-171">Unreal tracks AR points in the application space using AR Pins, which are used to create an Azure Spatial Anchor.</span></span> <span data-ttu-id="f8f6e-172">Unreal에서 AR Pin은 HoloLens의 SpatialAnchor와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-172">In Unreal, an AR Pin is analogous to a SpatialAnchor on HoloLens.</span></span>

![핀 구성 요소 함수에 연결된 장면 구성 요소의 청사진](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. <span data-ttu-id="f8f6e-174">새로 만든 AR Pin을 사용하여 **Create Cloud Anchor**(클라우드 앵커 만들기)를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-174">Call **Create Cloud Anchor** using the newly created AR Pin.</span></span>
    * <span data-ttu-id="f8f6e-175">Create Cloud Anchor(클라우드 앵커 만들기)는 Azure Spatial Anchor 서비스가 아닌 로컬에 Azure Spatial Anchor를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-175">Create Cloud Anchor creates an Azure Spatial Anchor locally but not in the Azure Spatial Anchor service.</span></span> <span data-ttu-id="f8f6e-176">Azure Spatial Anchor의 매개 변수(예: 만료 날짜)는 서비스를 사용하여 Azure Spatial Anchor를 만들기 전에 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-176">Parameters for the Azure Spatial Anchor, such as an expiration date, can be set before creating the Azure Spatial Anchor with the service.</span></span>

![ARPin을 반환하는 클라우드 앵커 함수 만들기에 연결된 핀 구성 요소 함수의 청사진](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. <span data-ttu-id="f8f6e-178">Azure Spatial Anchor 만료를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-178">Set the Azure Spatial Anchor expiration.</span></span> <span data-ttu-id="f8f6e-179">이 함수의 Lifetime 매개 변수를 사용하면 개발자가 서비스에서 앵커를 유지해야 하는 시간을 초 단위로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-179">This function's Lifetime parameter allows the developer to specify in seconds how long the anchor should be maintained by the service.</span></span>
    * <span data-ttu-id="f8f6e-180">예를 들어, 일주일의 만료 시간 값은 60초 x 60분 x 24시간 x 7일 = 604,800초입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-180">For example, a week long expiration would take a value of 60 seconds x 60 minutes x 24 hours x seven days = 604,800 seconds.</span></span>

![수명 값이 604,800초로 설정된 만료 함수 설정에 연결된 클라우드 앵커의 청사진](images/asa-unreal/unreal-spatial-anchors-img-13.png)

<span data-ttu-id="f8f6e-182">앵커 매개 변수를 설정한 후에 저장할 준비가 된 것으로 앵커를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-182">After setting anchor parameters, declare the anchor as ready to save.</span></span> <span data-ttu-id="f8f6e-183">아래 예제에서는 새로 만든 Azure Spatial Anchor가 저장이 필요한 Azure Spatial Anchors 세트에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-183">In the example below, the newly created Azure Spatial Anchor is added to a set of Azure Spatial Anchors needing saving.</span></span> <span data-ttu-id="f8f6e-184">이 세트는 Pawn 청사진에 대한 변수로 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-184">This set is declared as a variable for the Pawn blueprint.</span></span>

![설정된 변수에 저장할 준비가 된 앵커의 청사진](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a><span data-ttu-id="f8f6e-186">앵커 저장</span><span class="sxs-lookup"><span data-stu-id="f8f6e-186">Saving an Anchor</span></span>

<span data-ttu-id="f8f6e-187">매개 변수를 사용하여 Azure Spatial Anchor를 구성한 후 **Save Cloud Anchor**(클라우드 앵커 저장)를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-187">After configuring the Azure Spatial Anchor with your parameters, call **Save Cloud Anchor**.</span></span> <span data-ttu-id="f8f6e-188">Save Cloud Anchor(클라우드 앵커 저장)는 Azure Spatial Anchors 서비스에 대한 앵커를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-188">Save Cloud Anchor declares the anchor to the Azure Spatial Anchors service.</span></span> <span data-ttu-id="f8f6e-189">Save Cloud Anchor(클라우드 앵커 저장) 호출이 성공하면 Azure Spatial Anchor 서비스의 다른 사용자가 Azure Spatial Anchor를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-189">When the call to Save Cloud Anchor succeeds, the Azure Spatial Anchor is available to other users of the Azure Spatial Anchor service.</span></span>  

![호출되는 save cloud anchor 함수의 청사진](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> <span data-ttu-id="f8f6e-191">Save Cloud Anchor(클라우드 앵커 저장)는 비동기 함수이며 게임 스레드 이벤트(예: **EventTick**)에서만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-191">Save Cloud Anchor is an asynchronous function and can only be called on a game thread event such as **EventTick**.</span></span> <span data-ttu-id="f8f6e-192">Save Cloud Anchor(클라우드 앵커 저장)는 사용자 지정 청사진 함수에 사용 가능한 청사진 함수로 나타나지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-192">Save Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="f8f6e-193">하지만 Pawn 이벤트 그래프 청사진 편집기에서는 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-193">However, it should be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="f8f6e-194">아래 예에서 Azure Spatial Anchor는 입력 이벤트 콜백 중에 세트에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-194">In the example below, the Azure Spatial Anchor is stored in a set during an input event callback.</span></span> <span data-ttu-id="f8f6e-195">그런 다음, EventTick에 앵커가 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-195">The anchor is then saved on the EventTick.</span></span> <span data-ttu-id="f8f6e-196">Azure Spatial Anchor를 저장하려면 Azure Spatial Anchors 세션에서 생성한 공간 데이터의 양에 따라 여러 번 시도가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-196">Saving an Azure Spatial Anchor may take multiple attempts depending on the amount of spatial data that your Azure Spatial Anchors session has created.</span></span> <span data-ttu-id="f8f6e-197">그래서 Save 호출이 성공했는지 여부를 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-197">That's why it's a good idea to check whether the save call succeeded.</span></span>

<span data-ttu-id="f8f6e-198">앵커가 저장되지 않은 경우 아직 저장이 필요한 앵커 세트에 다시 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-198">If the anchor doesn't save, readd it to the set of anchors still needing to be saved.</span></span> <span data-ttu-id="f8f6e-199">향후 EventTicks는 앵커가 성공적으로 저장될 때까지 저장을 계속 시도할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-199">Future EventTicks will keep trying to save the anchor until it's successfully stored.</span></span>

![설정된 변수에 다시 저장되는 저장되지 않은 앵커의 청사진](images/asa-unreal/unreal-spatial-anchors-img-16.png)

<span data-ttu-id="f8f6e-201">앵커가 저장되면 ARPin의 변환이 앱에 콘텐츠를 배치하기 위한 참조 변환 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-201">Once the anchor saves, the AR Pins' transform acts as a reference transform for placing content in your app.</span></span> <span data-ttu-id="f8f6e-202">다른 사용자가 이 앵커를 감지하고 AR 콘텐츠를 실제 세계의 여러 디바이스에 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-202">Other users can detect this anchor and align AR content for different devices in the physical world.</span></span>

## <a name="deleting-an-anchor"></a><span data-ttu-id="f8f6e-203">앵커 삭제</span><span class="sxs-lookup"><span data-stu-id="f8f6e-203">Deleting an Anchor</span></span>

<span data-ttu-id="f8f6e-204">**Delete Cloud Anchor**(클라우드 앵커 삭제)를 호출하여 Azure Spatial Anchor 서비스에서 앵커를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-204">You can delete anchors from the Azure Spatial Anchor service by calling **Delete Cloud Anchor**.</span></span>

![호출되는 delete cloud anchor 함수의 청사진](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> <span data-ttu-id="f8f6e-206">Delete Cloud Anchor(클라우드 앵커 삭제)는 잠재 함수이며 게임 스레드 이벤트(예: EventTick)에서만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-206">Delete Cloud Anchor is a latent function and can only be called on a game thread event, such as EventTick.</span></span> <span data-ttu-id="f8f6e-207">Delete Cloud Anchor(클라우드 앵커 삭제)는 사용자 지정 청사진 함수에는 사용 가능한 청사진 함수로 나타나지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-207">Delete Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="f8f6e-208">하지만 Pawn 이벤트 그래프 청사진 편집기에서는 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-208">It should however be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="f8f6e-209">아래 예제에서는 사용자 지정 입력 이벤트에서 앵커에 삭제 플래그가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-209">In the example below, the anchor is flagged for deletion on a custom input event.</span></span> <span data-ttu-id="f8f6e-210">그런 다음 EventTick에서 삭제를 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-210">The deletion is then attempted on the EventTick.</span></span> <span data-ttu-id="f8f6e-211">앵커 삭제가 실패하면 삭제 플래그가 지정된 앵커 세트에 Azure Spatial Anchor를 추가하고 나중에 EventTicks에서 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-211">If the anchor deletion fails, add the Azure Spatial Anchor to the set of anchors flagged for deletion and tries again on later EventTicks.</span></span>

<span data-ttu-id="f8f6e-212">이제 이벤트 그래프 청사진은 아래 스크린샷과 같은 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-212">Your Event Graph blueprint should now look like the screenshot below:</span></span>

![클라우드 앵커 처리를 위한 전체 이벤트 그래프의 청사진](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a><span data-ttu-id="f8f6e-214">기존 앵커 찾기</span><span class="sxs-lookup"><span data-stu-id="f8f6e-214">Locating pre-existing anchors</span></span>

<span data-ttu-id="f8f6e-215">Azure Spatial Anchors 서비스를 사용하는 피어가 기존 앵커를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-215">Existing anchors can be created by peers with the Azure Spatial Anchors service:</span></span>

1. <span data-ttu-id="f8f6e-216">감지할 앵커에 대한 Azure Spatial Anchor 식별자를 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-216">Obtain an Azure Spatial Anchor identifier for the anchor that you would like to detect.</span></span>
    * <span data-ttu-id="f8f6e-217">앵커 식별자는 이전 Azure Spatial Anchors 세션에서 동일한 디바이스로 만든 앵커에 대해 확보할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-217">An anchor identifier can be obtained for an anchor created by the same device in a previous Azure Spatial Anchors session.</span></span> <span data-ttu-id="f8f6e-218">Azure Spatial Anchors 서비스와 상호 작용하는 피어 디바이스에서 만들고 공유할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-218">It can also be created and shared by peer devices interacting with the Azure Spatial Anchors service.</span></span>

![get azure cloud 식별자 함수가 포함된 store azure spatial anchor 식별자 사용자 지정 이벤트의 청사진](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. <span data-ttu-id="f8f6e-220">**AzureSpatialAnchorsEvent** 구성 요소를 Pawn 청사진에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-220">Add an **AzureSpatialAnchorsEvent** component to your Pawn blueprint.</span></span>
    * <span data-ttu-id="f8f6e-221">이 구성 요소를 사용하면 다양한 Azure Spatial Anchors 이벤트(예: Azure Spatial Anchors가 있을 때 호출되는 이벤트)를 구독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-221">This component allows you to subscribe to various Azure Spatial Anchors events, such as events called when Azure Spatial Anchors are located.</span></span>

![구성 요소 및 세부 정보 패널이 열려 있는 청사진 편집기에서 열린 BP_Pawn의 스크린샷](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. <span data-ttu-id="f8f6e-223">**AzureSpatialAnchorsEvent** 구성 요소에 대한 **ASAAnchor Located 대리자** 를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-223">Subscribe to the **ASAAnchor Located Delegate** for the **AzureSpatialAnchorsEvent** component.</span></span>
    * <span data-ttu-id="f8f6e-224">대리자는 Azure Spatial Anchors 계정과 연결된 새 앵커가 배치되는 경우 해당 애플리케이션에 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-224">The delegate lets the application know when new anchors associated with the Azure Spatial Anchors account have been located.</span></span>
    * <span data-ttu-id="f8f6e-225">이벤트 콜백을 사용하면 Azure Spatial Anchors 세션을 사용하여 피어가 만든 Azure Spatial Anchors에는 기본적으로 AR Pin이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-225">With the event callback, Azure Spatial Anchors created by peers using the Azure Spatial Anchors session won't have AR Pins created by default.</span></span> <span data-ttu-id="f8f6e-226">감지된 Azure Spatial Anchor에 대한 AR Pin을 만들려면 개발자가 **Create ARPin Around Azure Cloud Spatial Anchor**(Azure Cloud Spatial Anchor에 대한 ARPin 만들기)를 호출하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-226">To create an AR Pin for the detected Azure Spatial Anchor, developers can call **Create ARPin Around Azure Cloud Spatial Anchor**.</span></span>

![ASAAnchor 위치 대리자에 연결된 재생 시작 이벤트의 청사진](images/asa-unreal/unreal-spatial-anchors-img-20.png)

<span data-ttu-id="f8f6e-228">Azure Spatial Anchor 서비스를 사용하여 피어에서 만든 Azure Spatial Anchors를 찾기 위해 애플리케이션은 **Azure Spatial Anchors Watcher** 를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-228">To locate Azure Spatial Anchors created by peers using the Azure Spatial Anchor service, the application will have to create an **Azure Spatial Anchors Watcher**:</span></span>
1. <span data-ttu-id="f8f6e-229">Azure Spatial Anchors 세션이 실행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-229">Check that an Azure Spatial Anchors session is running.</span></span>
2. <span data-ttu-id="f8f6e-230">**AzureSpatialAnchorsLocateCriteria** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-230">Create an **AzureSpatialAnchorsLocateCriteria**.</span></span>
    * <span data-ttu-id="f8f6e-231">다양한 위치 매개 변수(예: 사용자와의 거리 또는 다른 앵커와의 거리)를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-231">You can specify various location parameters like distance from the user or distance from another anchor.</span></span>
3. <span data-ttu-id="f8f6e-232">**AzureSpatialAnchorsLocateCritieria** 에서 찾고 있는 Azure Spatial Anchor 식별자를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-232">Declare the Azure Spatial Anchor identifier you're looking for in the **AzureSpatialAnchorsLocateCritieria**.</span></span>
4. <span data-ttu-id="f8f6e-233">**Create Watcher**(감시자 만들기)를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-233">Call **Create Watcher**.</span></span>

![start azure spatial anchors watcher 사용자 지정 이벤트의 청사진](images/asa-unreal/unreal-spatial-anchors-img-21.png)

<span data-ttu-id="f8f6e-235">이제 애플리케이션이 Azure Spatial Anchors 서비스에 알려진 Azure Spatial Anchors를 찾기 시작합니다. 따라서, 피어에서 만든 Azure Spatial Anchors를 사용자가 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-235">The application now begins looking for Azure Spatial Anchors known to the Azure Spatial Anchors service, meaning that users can locate Azure Spatial Anchors created by their peers.</span></span>

<span data-ttu-id="f8f6e-236">Azure Spatial Anchor를 찾은 후 **Stop Watcher**(감시자 중지)를 호출하여 Azure Spatial Anchors Watcher를 중지하고 감시자 리소스를 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-236">After locating the Azure Spatial Anchor, call **Stop Watcher** to stop the Azure Spatial Anchors Watcher and clean up watcher resources.</span></span>

![호출되는 stop watcher 함수의 청사진](images/asa-unreal/unreal-spatial-anchors-img-22.png)

<span data-ttu-id="f8f6e-238">마지막 이벤트 그래프 청사진은 아래 스크린샷과 같은 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-238">Your final Event Graph blueprint should now look like the screenshot below:</span></span>

![앵커 대리자 이벤트 처리를 위한 전체 이벤트 그래프의 청사진](images/asa-unreal/unreal-spatial-anchors-img-23.png)

## <a name="next-development-checkpoint"></a><span data-ttu-id="f8f6e-240">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="f8f6e-240">Next Development Checkpoint</span></span>

<span data-ttu-id="f8f6e-241">앞에서 설명한 Unreal 개발 과정을 따르고 있다면 현재 MRTK 핵심 구성 요소를 살펴보는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-241">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="f8f6e-242">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-242">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="f8f6e-243">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="f8f6e-243">Spatial mapping</span></span>](unreal-spatial-mapping.md)

<span data-ttu-id="f8f6e-244">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-244">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f8f6e-245">HoloLens 카메라</span><span class="sxs-lookup"><span data-stu-id="f8f6e-245">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="f8f6e-246">언제든지 [Unreal 개발 검사점](unreal-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8f6e-246">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="next-steps"></a><span data-ttu-id="f8f6e-247">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f8f6e-247">Next steps</span></span>
* [<span data-ttu-id="f8f6e-248">로컬 Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="f8f6e-248">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="f8f6e-249">Spatial Anchors 설명서</span><span class="sxs-lookup"><span data-stu-id="f8f6e-249">Spatial Anchors documentation</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)
* [<span data-ttu-id="f8f6e-250">Spatial Anchor 기능</span><span class="sxs-lookup"><span data-stu-id="f8f6e-250">Spatial Anchor features</span></span>](https://azure.microsoft.com/services/spatial-anchors/#features)
* [<span data-ttu-id="f8f6e-251">효과적인 앵커 환경 지침</span><span class="sxs-lookup"><span data-stu-id="f8f6e-251">Effective anchor experience guidelines</span></span>](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)