---
title: Azure Spatial Anchors 저장, 검색 및 공유
description: 이 과정을 완료하여 혼합 현실 애플리케이션에서 Azure Spatial Anchors를 저장, 검색, 공유하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, 앱 세션
ms.localizationpriority: high
ms.openlocfilehash: 4a435702e87dc34ed96d5493a67905b8ab372a38
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403354"
---
# <a name="3-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="aee45-104">3. Azure Spatial Anchors 저장, 검색 및 공유</span><span class="sxs-lookup"><span data-stu-id="aee45-104">3. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="aee45-105">이 자습서에서는 앵커 ID를 HoloLens 2의 스토리지에 저장하여 여러 앱 세션에서 Azure Spatial Anchors를 저장하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-105">In this tutorial, you will learn how to save Azure Spatial Anchors across multiple app sessions by saving the anchor ID to the HoloLens 2's storage.</span></span> <span data-ttu-id="aee45-106">또한 다중 디바이스 앵커 맞춤을 위해 이 앵커 ID를 다른 디바이스와 공유하는 방법에 대해서도 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-106">You will also learn how to share this anchor ID to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="aee45-107">목표</span><span class="sxs-lookup"><span data-stu-id="aee45-107">Objectives</span></span>

* <span data-ttu-id="aee45-108">여러 앱 세션 간에 공간 맞춤을 달성하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-108">Learn how to achieve spatial alignment across multiple app sessions.</span></span>
* <span data-ttu-id="aee45-109">여러 디바이스 간의 공간 맞춤을 구현하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-109">Learn how to achieve spatial alignment between multiple devices.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="aee45-110">장면 준비</span><span class="sxs-lookup"><span data-stu-id="aee45-110">Preparing the scene</span></span>

<span data-ttu-id="aee45-111">Hierarchy 창에서 **ButtonParent** 개체를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-111">In the Hierarchy window, expand the **ButtonParent** object.</span></span> <span data-ttu-id="aee45-112">**마지막 네 개의 자식 단추** 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-112">Select the **last four child button** objects.</span></span> <span data-ttu-id="aee45-113">Inspector 창에서 이름 필드 옆에 있는 확인란을 **선택** 하여 모든 개체를 활성화하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-113">In the Inspector window, **check** the checkbox next to the name field to make all the objects active.</span></span>

![이전에 비활성화된 단추 개체가 선택되고 활성화된 Unity](images/mr-learning-asa/asa-03-section1-step1-1.png)

<span data-ttu-id="aee45-115">Hierarchy 창에서 **ButtonParent** 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-115">In the Hierarchy window, select the **ButtonParent** objects.</span></span> <span data-ttu-id="aee45-116">그런 다음, Inspector 창에서 **GridObjectCollection** 구성 요소를 찾고 **컬렉션 업데이트** 단추를 클릭하여 모든 **ButtonParent** 개체의 자식 개체 위치를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-116">Then in the Inspector window, locate the **GridObjectCollection** component and click the **Update Collection** button to update the position of all the **ButtonParent** object's child objects.</span></span>

![GridObjectCollection 구성 요소가 업데이트된 Unity](images/mr-learning-asa/asa-03-section1-step1-2.png)

## <a name="persisting-azure-spatial-anchors-between-app-sessions"></a><span data-ttu-id="aee45-118">앱 세션 간에 Azure Spatial Anchors 유지</span><span class="sxs-lookup"><span data-stu-id="aee45-118">Persisting Azure Spatial Anchors between app sessions</span></span>

<span data-ttu-id="aee45-119">이 섹션에서는 Azure Anchor ID를 HoloLens 로컬 디스크로 저장하고 가져오는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-119">In this section, you will learn how to save and retrieve the Azure Anchor ID to and from the HoloLens' local disk.</span></span> <span data-ttu-id="aee45-120">이렇게 하면 서로 다른 앱 세션 간에 동일한 앵커 ID에 대한 Azure를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-120">This will allow you to query Azure for the same anchor ID between different app sessions.</span></span> <span data-ttu-id="aee45-121">이를 통해 앵커된 holograms가 이전 앱 세션과 동일한 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-121">It will enable the anchored holograms to be positioned at the same location as in the previous app session.</span></span>

<span data-ttu-id="aee45-122">Hierarchy 창에서 **ButtonParent** 개체를 확장하고 **SaveAzureAnchorIdToDisk** 및 **GetAzureAnchorIdFromDisk** 라는 두 개의 단추를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-122">In the Hierarchy window, expand the **ButtonParent** object and locate the two buttons named **SaveAzureAnchorIdToDisk** and **GetAzureAnchorIdFromDisk**:</span></span>

![SaveAzureAnchorIdToDisk 및 GetAzureAnchorIdFromDisk 단추 개체가 선택된 Unity](images/mr-learning-asa/asa-03-section2-step1-1.png)

<span data-ttu-id="aee45-124">이전 자습서의 [장면을 작동하도록 단추 구성](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) 지침과 동일한 단계를 수행하여 두 개의 단추 각각에 **Interactable(스크립트)** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-124">Follow the same steps as in the [configuring the buttons to operate the scene](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="aee45-125">**SaveAzureAnchorIdToDisk** 단추 개체에 대해 AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** 함수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-125">For the **SaveAzureAnchorIdToDisk** button object, assign the AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** function.</span></span>
* <span data-ttu-id="aee45-126">**GetAzureAnchorIdFromDisk** 단추 개체에 대해 AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** 함수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-126">For the **GetAzureAnchorIdFromDisk** button object, assign the AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** function.</span></span>

<span data-ttu-id="aee45-127">업데이트된 앱을 HoloLens에 빌드하는 경우 이제 Azure Anchor ID를 저장하여 앱 세션 간에 Azure Spatial Anchors를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-127">If you build the updated app to your HoloLens, you can now persist Azure Spatial Anchors between app sessions by saving the Azure Anchor ID.</span></span> <span data-ttu-id="aee45-128">이를 테스트하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-128">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="aee45-129">Rover 탐색기를 원하는 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-129">Move the Rover Explorer to the desired location</span></span>
2. <span data-ttu-id="aee45-130">Azure 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-130">Start Azure Session</span></span>
3. <span data-ttu-id="aee45-131">Azure Anchor를 만듭니다(앵커를 Rover 탐색기의 위치에 만듦).</span><span class="sxs-lookup"><span data-stu-id="aee45-131">Create Azure Anchor (creates anchors at the location of the Rover Explorer)</span></span>
4. <span data-ttu-id="aee45-132">Azure 앵커 ID를 디스크에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-132">Save Azure Anchor ID to Disk</span></span>
5. <span data-ttu-id="aee45-133">앱을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-133">Restart the app</span></span>
6. <span data-ttu-id="aee45-134">디스크에서 Azure 앵커를 가져옵니다(방금 저장한 앵커 ID를 로드함).</span><span class="sxs-lookup"><span data-stu-id="aee45-134">Get Azure Anchor from Disk (loads the anchor ID you just saved)</span></span>
7. <span data-ttu-id="aee45-135">Azure 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-135">Start Azure Session</span></span>
8. <span data-ttu-id="aee45-136">Azure 앵커를 찾습니다(Rover 탐색기를 3단계의 위치에 배치함).</span><span class="sxs-lookup"><span data-stu-id="aee45-136">Find Azure Anchor (positions the Rover Explorer at the location from step 3)</span></span>

> [!NOTE]
> <span data-ttu-id="aee45-137">앱을 완전히 다시 시작하려면 몰입형 앱 보기를 종료한 후, 혼합 현실 홈의 앱 창을 닫고 [시작] 메뉴에서 앱을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-137">To fully restart the app, after exiting the immersive app view, the app window in the mixed reality home needs to be closed before relaunching it from the Start menu.</span></span> <span data-ttu-id="aee45-138">자세한 내용은 [HoloLens에서 앱 사용](/hololens/holographic-home#using-apps-on-hololens) 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aee45-138">For additional details, you can refer to the [Using apps on HoloLens](/hololens/holographic-home#using-apps-on-hololens) documentation.</span></span>

## <a name="sharing-azure-spatial-anchors-between-devices"></a><span data-ttu-id="aee45-139">디바이스 간에 Azure Spatial Anchors 공유</span><span class="sxs-lookup"><span data-stu-id="aee45-139">Sharing Azure Spatial Anchors between devices</span></span>

<span data-ttu-id="aee45-140">이 섹션에서는 여러 디바이스 간에 Azure 앵커 ID를 공유하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-140">In this section, you will learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="aee45-141">이렇게 하면 여러 디바이스에서 동일한 앵커 ID를 Azure에 쿼리하여 고정된 홀로그램을 공간적으로 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-141">This will allow multiple devices to query Azure for the same anchor ID, allowing the anchored holograms to be spatially aligned.</span></span> <span data-ttu-id="aee45-142">공간 맞춤, 즉 여러 디바이스 간에 동일한 실제 위치에서 동일한 홀로그램을 보는 것은 HoloLens 2에서 로컬 공유 환경의 핵심입니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-142">Spatial alignment, i.e., seeing the same holograms in the same physical location between multiple devices, is key to local shared experiences in the HoloLens 2.</span></span>

<span data-ttu-id="aee45-143">[다중 사용자 기능 자습서](mr-learning-sharing-02.md) 시리즈에서 설명하는 방법을 포함하여 디바이스 간에 Azure 앵커 ID를 전송하는 여러 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-143">There are many ways to transfer Azure Anchor IDs between devices, including methods outlined in the [Multi-user capabilities tutorials](mr-learning-sharing-02.md) series.</span></span> <span data-ttu-id="aee45-144">이 예에서는 간단한 웹 서비스를 사용하여 디바이스 간에 앵커 ID를 업로드하고 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-144">In this example, you will use a simple web service to upload and download anchor IDs between devices.</span></span>

<span data-ttu-id="aee45-145">Hierarchy 창에서 **ButtonParent** 개체를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-145">In the Hierarchy window, expand the **ButtonParent** object.</span></span>   <span data-ttu-id="aee45-146">**ShareAzureAnchorIdToNetwork** 및 **GetAzureAnchorIdFromNetwork** 라는 두 단추를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-146">Locate the two buttons named **ShareAzureAnchorIdToNetwork** and **GetAzureAnchorIdFromNetwork**:</span></span>

![ShareAzureAnchorIdToNetwork 및 GetAzureAnchorIdFromNetwork 단추 개체가 선택된 Unity](images/mr-learning-asa/asa-03-section3-step1-1.png)

<span data-ttu-id="aee45-148">이전 자습서의 [장면을 작동하도록 단추 구성](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) 지침과 동일한 단계를 수행하여 두 개의 단추 각각에 **Interactable(스크립트)** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-148">Follow the same steps as in the [configuring the buttons to operate the scene](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="aee45-149">**ShareAzureAnchorIdToNetwork** 개체에 대해 AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** 함수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-149">For the **ShareAzureAnchorIdToNetwork** object, assign the AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** function.</span></span>
* <span data-ttu-id="aee45-150">**GetAzureAnchorIdFromNetwork** 개체에 대해 AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** 함수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-150">For the **GetAzureAnchorIdFromNetwork** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** function.</span></span>

<span data-ttu-id="aee45-151">업데이트된 앱을 두 개의 HoloLens 디바이스에 빌드하는 경우 이제 Azure 앵커 ID를 공유하여 공간을 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-151">If you build the updated app to two HoloLens devices, you can now achieve spatial alignment by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="aee45-152">이를 테스트하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-152">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="aee45-153">HoloLens 디바이스 1: Rover 탐색기를 원하는 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-153">On HoloLens device 1: Move the Rover Explorer to the desired location.</span></span>
2. <span data-ttu-id="aee45-154">HoloLens 디바이스 1: Azure 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-154">On HoloLens device 1: Start Azure Session.</span></span>
3. <span data-ttu-id="aee45-155">HoloLens 디바이스 1: Azure Anchor를 만듭니다(앵커를 Rover 탐색기의 위치에 만듦).</span><span class="sxs-lookup"><span data-stu-id="aee45-155">On HoloLens device 1: Create Azure Anchor (creates anchors at the location of the Rover Explorer).</span></span>
4. <span data-ttu-id="aee45-156">HoloLens 디바이스 1: Azure 앵커 ID를 네트워크에 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-156">On HoloLens device 1: Share Azure Anchor ID to Network.</span></span>
5. <span data-ttu-id="aee45-157">HoloLens 디바이스 2: 앱을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-157">On HoloLens device 2: Start the app.</span></span>
6. <span data-ttu-id="aee45-158">HoloLens 디바이스 2: 네트워크에서 공유 앵커 ID를 가져옵니다(HoloLens 디바이스 1에서 방금 공유한 앵커 ID를 가져옴).</span><span class="sxs-lookup"><span data-stu-id="aee45-158">On HoloLens device 2: Get Shared Anchor ID from Network (fetches the anchor ID just shared from HoloLens device 1).</span></span>
7. <span data-ttu-id="aee45-159">HoloLens 디바이스 2: Azure 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-159">On HoloLens device 2: Start Azure Session.</span></span>
8. <span data-ttu-id="aee45-160">HoloLens 디바이스 2: Azure Anchor를 찾습니다(Rover 탐색기를 3단계의 위치에 배치함).</span><span class="sxs-lookup"><span data-stu-id="aee45-160">On HoloLens device 2: Find Azure Anchor (positions the Rover Explorer at the location from step 3).</span></span>

> [!TIP]
> <span data-ttu-id="aee45-161">하나의 HoloLens만 있는 경우에도 두 번째 HoloLens 디바이스를 사용하는 대신 앱을 다시 시작하여 기능을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-161">If you only have one HoloLens, you can still test the functionality by restarting the app instead of using a second HoloLens device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="aee45-162">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-162">Congratulations</span></span>

<span data-ttu-id="aee45-163">이 자습서에서는 Azure Spatial Anchor ID를 HoloLens의 로컬 디스크에 저장하여 앱 세션과 앱 다시 시작 간에 Azure Spatial Anchors를 유지하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-163">In this tutorial, you learned how to persist Azure Spatial Anchors between app sessions and app restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens.</span></span> <span data-ttu-id="aee45-164">또한 기본 다중 사용자, 정적 홀로그램 공유 환경을 위해 여러 디바이스 간에 Azure Spatial Anchors를 공유하는 방법도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-164">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="aee45-165">다음 자습서에서는 사용자에게 실시간 피드백을 제공하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-165">In the next tutorial, you will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="aee45-166">이 피드백에는 앵커 만들기, 환경 이해 품질 및 Azure 세션 상태에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-166">This feedback will include information about Anchor creation, the quality of environment understanding, and the Azure session's state.</span></span> <span data-ttu-id="aee45-167">피드백을 사용하지 않는 경우 사용자는 앵커가 Azure에 성공적으로 업로드되었는지 여부, 환경의 품질이 앵커를 만드는 데 충분한지 여부 또는 현재 상태를 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aee45-167">Without feedback, users may not know whether an anchor has successfully been uploaded to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aee45-168">다음 자습서: 4. Azure Spatial Anchor 피드백 표시</span><span class="sxs-lookup"><span data-stu-id="aee45-168">Next Tutorial: 4. Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
