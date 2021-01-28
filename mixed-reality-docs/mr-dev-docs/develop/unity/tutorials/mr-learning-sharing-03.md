---
title: 여러 사용자 연결
description: 이 과정을 완료하여 HoloLens 2 혼합 현실 애플리케이션에서 여러 사용자를 연결하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, 다중 사용자 기능, Photon, MRTK, mixed reality toolkit, UWP, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: 0c6bf0871836ad7aae9c3906b2042f97ae003ebf
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699067"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="bb76e-104">3. 여러 사용자 연결</span><span class="sxs-lookup"><span data-stu-id="bb76e-104">3. Connecting multiple users</span></span>

<span data-ttu-id="bb76e-105">이 자습서에서는 라이브 공유 환경의 일부로 여러 사용자를 연결하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-105">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="bb76e-106">자습서를 마치면 여러 디바이스에서 앱을 실행하여 각 사용자가 다른 사용자의 아바타가 움직이는 것을 실시간으로 보게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-106">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="bb76e-107">목표</span><span class="sxs-lookup"><span data-stu-id="bb76e-107">Objectives</span></span>

* <span data-ttu-id="bb76e-108">공유 환경에서 여러 사용자를 연결하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="bb76e-108">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="bb76e-109">장면 준비</span><span class="sxs-lookup"><span data-stu-id="bb76e-109">Preparing the scene</span></span>

<span data-ttu-id="bb76e-110">이 섹션에서는 자습서 프리팹 중 일부를 추가하여 장면을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-110">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="bb76e-111">Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** 폴더로 이동한 다음, 다음과 같은 프리팹을 클릭하고 Hierarchy 창으로 끌어서 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-111">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="bb76e-112">**NetworkLobby** 프리팹</span><span class="sxs-lookup"><span data-stu-id="bb76e-112">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="bb76e-113">**SharedPlayground** 프리팹</span><span class="sxs-lookup"><span data-stu-id="bb76e-113">**SharedPlayground** prefab</span></span>

![새로 추가한 NetworkLobby 및 SharedPlayground 프리팹이 선택된 Unity](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="bb76e-115">Project 창에서 **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** 폴더로 이동한 다음, 다음과 같은 프리팹을 클릭하고 Hierarchy 창으로 끌어서 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-115">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="bb76e-116">**DebugWindow** 프리팹</span><span class="sxs-lookup"><span data-stu-id="bb76e-116">**DebugWindow** prefab</span></span>

![새로 추가한 DebugWindow 프리팹이 선택된 Unity](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="bb76e-118">사용자 프리팹 만들기</span><span class="sxs-lookup"><span data-stu-id="bb76e-118">Creating the user prefab</span></span>

<span data-ttu-id="bb76e-119">이 섹션에서는 공유 환경의 사용자를 나타내는 데 사용할 프리팹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-119">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="bb76e-120">1. 사용자 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="bb76e-120">1. Create and configure the user</span></span>

<span data-ttu-id="bb76e-121">Hierarchy 창에서 빈 영역을 마우스 오른쪽 단추로 클릭하고 **Create Empty** 를 선택하여 빈 개체를 장면에 추가하고 개체의 이름을 **PhotonUser** 로 지정하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-121">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="bb76e-122">변환 **위치** 는 X = 0, Y = 0, Z = 0으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-122">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![새로 만든 PhotonUser 개체가 선택된 Unity](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="bb76e-124">Hierarchy 창에서 **PhotonUser** 개체를 선택한 다음, Inspector 창에서 **구성 요소 추가** 단추를 사용하여 **Photon User (Script)** 구성 요소를 PhotonUser 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-124">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![Photon User 구성 요소가 추가된 Unity](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="bb76e-126">Inspector 창에서 **Add Component** 단추를 사용하여 **Generic Net Sync (Script)** 구성 요소를 PhotonUser 개체에 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-126">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="bb76e-127">**Is User** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-127">Check the **Is User** checkbox</span></span>

![Generic Net Sync 구성 요소가 추가되고 구성된 Unity](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="bb76e-129">Inspector 창에서 **Add Component** 단추를 사용하여 **Photon View (Script)** 구성 요소를 PhotonUser 개체에 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-129">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="bb76e-130">**Observed Components(관찰된 구성 요소)** 필드에 **Generic Net Sync(Script)(일반 네트워크 동기화(스크립트))** 구성 요소가 할당되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-130">Ensure that the **Observed Components** field is assigned with the **Generic Net Sync (Script)** component</span></span>

![Photon View 구성 요소가 추가되고 구성된 Unity](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="bb76e-132">2. 아바타 만들기</span><span class="sxs-lookup"><span data-stu-id="bb76e-132">2. Create the avatar</span></span>

<span data-ttu-id="bb76e-133">Project 창에서 **Assets(자산)**  > **MRTK** > **StandardAssets** > **Materials(자료)** 폴더로 이동하여 MRTK 자료를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-133">In the Project window, navigate to the **Assets** > **MRTK** > **StandardAssets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="bb76e-134">그런 다음, Hierarchy 창에서 **PhotonUser** 개체를 마우스 오른쪽 단추로 클릭하고 **3D Object** > **Sphere** 를 선택하여 PhotonUser 개체의 자식으로 구형 개체를 만들어서 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-134">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="bb76e-135">변환 **Position** 은 X = 0, Y = 0, Z = 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-135">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="bb76e-136">변환 **Scale** 을 적절한 크기(예: X = 0.15, Y = 0.15, Z = 0.15)로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-136">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="bb76e-137">MeshRenderer > Materials > **Element 0** 필드에 **MRTK_Standard_White** 자료를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-137">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![새로 만들고 구성한 아바타 구가 있는 Unity](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="bb76e-139">3. 프리팹 만들기</span><span class="sxs-lookup"><span data-stu-id="bb76e-139">3. Create the prefab</span></span>

<span data-ttu-id="bb76e-140">Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-140">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![Resource 폴더가 선택된 Unity 프로젝트 창](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="bb76e-142">Resources 폴더를 선택한 상태에서 **PhotonUser** 개체를 Hierarchy 창에서 **Resources** 폴더로 **클릭하고 끌어서** PhotonUser 개체를 프리펩으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-142">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![새로 만든 PhotonUser 프리팹이 선택된 Unity](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="bb76e-144">Hierarchy 창에서 **PhotonUser** 개체를 마우스 오른쪽 단추로 클릭하고 **Delete** 를 선택하여 장면에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-144">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![새로 만든 PhotonUser 프리팹이 장면에서 제거된 Unity](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="bb76e-146">사용자 프리팹을 인스턴스화하도록 PUN 구성</span><span class="sxs-lookup"><span data-stu-id="bb76e-146">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="bb76e-147">이 섹션에서는 이전 섹션에서 만든 PhotonUser 프리펩을 사용하도록 프로젝트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-147">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="bb76e-148">Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-148">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="bb76e-149">Hierarchy 창에서 **NetworkLobby** 개체를 펼쳐서 **NetworkRoom** 자식 개체를 선택한 다음, Inspector 창에서 **Photon Room (Script)** 구성 요소를 찾아서 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-149">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="bb76e-150">**Photon User Prefab** 필드에 Resources 폴더의 **PhotonUser** 프리팹을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-150">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![Photon Room 구성 요소가 부분적으로 구성된 Unity](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="bb76e-152">여러 사용자 환경 체험</span><span class="sxs-lookup"><span data-stu-id="bb76e-152">Trying the experience with multiple users</span></span>

<span data-ttu-id="bb76e-153">Unity 프로젝트를 빌드하고 HoloLens에 배포했으면 Unity로 돌아가서 HoloLens에서 앱이 실행되는 동안 게임 모드로 들어갑니다. 머리(HoloLens)를 움직이면 HoloLens 사용자 아바타가 움직이는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-153">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![네트워크 사용자를 사용하여 Unity를 보여주는 애니메이션](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="bb76e-155">Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb76e-155">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="bb76e-156">앱에서 Photon에 연결해야 하므로 컴퓨터/디바이스가 인터넷에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-156">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="bb76e-157">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-157">Congratulations</span></span>

<span data-ttu-id="bb76e-158">여러 사용자가 동일한 환경에 연결하여 서로의 움직임을 볼 수 있도록 프로젝트를 구성하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-158">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="bb76e-159">다음 자습서에서는 개체의 움직임도 여러 디바이스에서 공유되도록 기능을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="bb76e-159">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bb76e-160">다음 자습서: 4. 여러 사용자와 개체 이동 공유</span><span class="sxs-lookup"><span data-stu-id="bb76e-160">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
