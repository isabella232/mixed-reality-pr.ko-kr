---
title: Azure Custom Vision 통합
description: 이 과정을 완료하여 HoloLens 2 혼합 현실 애플리케이션 내에서 Azure Custom Vision을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, hololens 2, azure custom vision, azure cognitive services, azure cloud services, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 7624ed28c337f3621a29f15f1ab3b0e98aeb89db
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224236"
---
# <a name="3-integrating-azure-custom-vision"></a><span data-ttu-id="2a7b5-104">3. Azure Custom Vision 통합</span><span class="sxs-lookup"><span data-stu-id="2a7b5-104">3. Integrating Azure Custom Vision</span></span>

<span data-ttu-id="2a7b5-105">이 자습서에서는 **Azure Custom Vision** 을 사용하는 방법을 알아봅니다. 사진 세트를 업로드하여 *추적된 개체* 와 연결하고 **Custom Vision** 서비스에 업로드하여 학습 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-105">In this tutorial, you will learn how to use **Azure Custom Vision**.You will upload a set of photos to associate it with a *Tracked Object*, upload them to the **Custom Vision** service and start the training process.</span></span> <span data-ttu-id="2a7b5-106">그런 다음, 이 서비스를 사용하여 웹캠 피드에서 사진을 캡처하여 *추적된 개체* 를 감지합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-106">Then you will use the service to detect the *Tracked Object* by capturing photos from the webcam feed.</span></span>

## <a name="objectives"></a><span data-ttu-id="2a7b5-107">목표</span><span class="sxs-lookup"><span data-stu-id="2a7b5-107">Objectives</span></span>

* <span data-ttu-id="2a7b5-108">Azure Custom Vision에 대한 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="2a7b5-108">Learn the basics about Azure Custom Vision</span></span>
* <span data-ttu-id="2a7b5-109">이 프로젝트에서 Custom Vision을 사용하도록 장면을 설정하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="2a7b5-109">Learn how to setup the scene to use Custom Vision in this project</span></span>
* <span data-ttu-id="2a7b5-110">이미지 업로드, 학습 및 감지를 통합하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="2a7b5-110">Learn how to integrate upload, train and detect images</span></span>

## <a name="understanding-azure-custom-vision"></a><span data-ttu-id="2a7b5-111">Azure Custom Vision 이해</span><span class="sxs-lookup"><span data-stu-id="2a7b5-111">Understanding Azure Custom Vision</span></span>

<span data-ttu-id="2a7b5-112">**Azure Custom Vision** 은 **Cognitive Services** 제품군에 속하며 이미지 분류자를 학습시키는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-112">**Azure Custom Vision** is part of the **Cognitive Services** family and is used to train image classifiers.</span></span> <span data-ttu-id="2a7b5-113">이미지 분류자는 학습된 모델을 사용하여 일치하는 태그를 적용하는 AI 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-113">The image classifier is an AI service that uses the trained model to apply matching tags.</span></span> <span data-ttu-id="2a7b5-114">이 분류 기능은 애플리케이션이 *추적된 개체* 를 감지하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-114">This classification feature will be used by our application to detect *Tracked Objects*.</span></span>

<span data-ttu-id="2a7b5-115">[Azure Custom Vision](/azure/cognitive-services/custom-vision-service/home)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-115">Learn more about [Azure Custom Vision](/azure/cognitive-services/custom-vision-service/home).</span></span>

## <a name="preparing-azure-custom-vision"></a><span data-ttu-id="2a7b5-116">Azure Custom Vision 준비</span><span class="sxs-lookup"><span data-stu-id="2a7b5-116">Preparing Azure Custom Vision</span></span>

<span data-ttu-id="2a7b5-117">시작하려면 그 전에 사용자 지정 비전 프로젝트를 만들어야 하며, 가장 빠른 방법은 웹 포털을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-117">Before you can start, you have to create a custom vision project, the fastest way is by using the web portal.</span></span>

<span data-ttu-id="2a7b5-118">이 [빠른 시작 자습서](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images)를 *이미지 업로드 및 태그 지정* 섹션까지 수행하여 계정과 프로젝트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-118">Follow this [quickstart tutorial](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) to setup your account and project until section *Upload and tag images*.</span></span>

> [!WARNING]
> <span data-ttu-id="2a7b5-119">모델을 학습시키려면 태그당 태그 2개 및 이미지 5개 이상이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-119">To train a model you need to have at least 2 tags and 5 images per tag.</span></span> <span data-ttu-id="2a7b5-120">이 애플리케이션을 사용하려면 이미지가 5개 이상인 태그를 하나 이상 만들어야 합니다. 그래야 나중에 학습 과정에서 실패하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-120">To use this application you should at least create one tag with 5 images, so that the training process later won't fail.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="2a7b5-121">장면 준비</span><span class="sxs-lookup"><span data-stu-id="2a7b5-121">Preparing the scene</span></span>

<span data-ttu-id="2a7b5-122">프로젝트 창에서 **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-122">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![ObjectDetectionManager 프리팹의 경로를 보여주는 Project(프로젝트) 창이 있는 Unity](images/mr-learning-azure/tutorial3-section4-step1-1.png)

<span data-ttu-id="2a7b5-124">여기에서 프리팹 **ObjectDetectionManager** 를 장면 계층 구조로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-124">From there drag the prefab **ObjectDetectionManager** into the scene Hierarchy.</span></span>

![Inspector(검사기)에 표시된 ObjectDetectionManager 스크립트 구성 요소 구성 필드가 있는 Unity](images/mr-learning-azure/tutorial3-section4-step1-2.png)

<span data-ttu-id="2a7b5-126">Hierarchy(계층 구조) 창에서 **ObjectDetectionManager** 개체를 찾아서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-126">In the Hierarchy window locate the **ObjectDetectionManager** object and select it.</span></span>
<span data-ttu-id="2a7b5-127">**ObjectDetectionManager** 프리팹에는 **ObjectDetectionManager(스크립트)** 구성 요소가 포함되어 있으며 Inspector(인스펙터) 창에서 볼 수 있듯이 Azure 설정 및 프로젝트 설정에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-127">The **ObjectDetectionManager** prefab contains the **ObjectDetectionManager (script)** component and as you can see from the Inspector window it depends on Azure settings and Project settings.</span></span>

## <a name="retrieving-azure-api-resource-credentials"></a><span data-ttu-id="2a7b5-128">Azure API 리소스 자격 증명 검색</span><span class="sxs-lookup"><span data-stu-id="2a7b5-128">Retrieving Azure api resource credentials</span></span>

<span data-ttu-id="2a7b5-129">**ObjectDetectionManager(스크립트)** 설정에 필요한 자격 증명은 Azure Portal 및 Custom Vision 포털에서 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-129">The necessary credentials for the **ObjectDetectionManager (script)** settings can be retrieve from the Azure Portal and the custom vision portal.</span></span>

### <a name="retrieving-azure-settings-credentials"></a><span data-ttu-id="2a7b5-130">Azure 설정 자격 증명 검색</span><span class="sxs-lookup"><span data-stu-id="2a7b5-130">Retrieving Azure Settings credentials</span></span>

<span data-ttu-id="2a7b5-131">이 자습서의 *장면 준비* 섹션에서 만든 **Cognitive Services** 유형의 Custom Vision 리소스를 찾아서 이동합니다(Custom Vision 리소스 이름을 선택하고 *-Prediction* 선택).</span><span class="sxs-lookup"><span data-stu-id="2a7b5-131">Find and locate the custom vision resource of type **Cognitive Services** you have created in the *Preparing the scene* section of this tutorial (select custom vision resources name followed by *-Prediction* ).</span></span> <span data-ttu-id="2a7b5-132">여기서 *개요* 또는 *키 및 엔드포인트* 를 클릭하여 필요한 자격 증명을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-132">There click on *Overview* or *Keys and Endpoint* to retrieve the necessary credentials.</span></span>

### <a name="retrieving-project-settings-credentials"></a><span data-ttu-id="2a7b5-133">프로젝트 설정 자격 증명 검색</span><span class="sxs-lookup"><span data-stu-id="2a7b5-133">Retrieving Project Settings credentials</span></span>

<span data-ttu-id="2a7b5-134">[Custom Vision](https://www.customvision.ai/projects) 대시보드에서 이 자습서용으로 만든 프로젝트를 열고 페이지 오른쪽 위 모서리 기어 아이콘을 클릭하여 설정 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-134">In the [custom vision](https://www.customvision.ai/projects) dashboard, open the project you have created for this tutorial and click on the top right corner of the page on the gear icon to open the settings page.</span></span> <span data-ttu-id="2a7b5-135">오른쪽 *리소스* 섹션에서 필요한 자격 증명을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-135">Here on the right hand *Resources* section you will find the necessary credentials.</span></span>

<span data-ttu-id="2a7b5-136">**ObjectDetectionManager(스크립트)** 가 올바르게 설정되었으면 장면 계층 구조에서 **SceneController** 개체를 찾아서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-136">Now with the **ObjectDetectionManager (script)** setup correctly, find the **SceneController** object in your scene Hierarchy and select it.</span></span>

![Inspector(검사기)에 표시된 SceneController 스크립트 구성 요소 구성 필드가 있는 Unity](images/mr-learning-azure/tutorial3-section4-step1-3.png)

<span data-ttu-id="2a7b5-138">**SceneController** 구성 요소의 *Object Detection Manager*(개체 감지 관리자) 필드가 비어 있는 것이 보이면 **ObjectDetectionManager** 를 계층 구조에서 이 필드로 끌어오고 장면을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-138">You see *Object Detection Manager* field in the **SceneController** component is empty, drag the **ObjectDetectionManager** from the Hierarchy into that field and save the scene.</span></span>

![SceneController 스크립트 구성 요소가 구성된 Unity](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a><span data-ttu-id="2a7b5-140">이미지 가져오기 및 업로드</span><span class="sxs-lookup"><span data-stu-id="2a7b5-140">Take and upload images</span></span>

<span data-ttu-id="2a7b5-141">장면을 실행하고 **Set Object**(개체 설정)를 클릭한 후 [이전 단원](mr-learning-azure-02.md)에서 만든 **추적된 개체** 중 하나의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-141">Run the scene and click on **Set Object**, type in the name for one of the **Tracked Objects** you have created in the [previous lesson](mr-learning-azure-02.md).</span></span> <span data-ttu-id="2a7b5-142">이제 **Object Card**(개체 카드) 아래쪽에서 있는 **Computer Vision** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-142">Now click on **Computer Vision** button you can find at the bottom of the **Object Card**.</span></span>

<span data-ttu-id="2a7b5-143">새 창이 열리면 이미지 인식을 위해 모델을 학습시키기 위한 사진을 6장 찍어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-143">A new window will open where you have to take six photos to train the model for image recognition.</span></span> <span data-ttu-id="2a7b5-144">**Camera** 단추를 클릭하고 추적할 개체를 보면서 AirTap을 수행하는 동작을 6번 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-144">Click on the **Camera** button and perform an AirTap when you look on the object you like to track, do this six times.</span></span>

> [!TIP]
> <span data-ttu-id="2a7b5-145">모델 학습을 향상시키려면 각 이미지를 서로 다른 각도와 조명 조건에서 찍습니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-145">To improve the model training try to take each image from different angles and lighting conditions.</span></span>

<span data-ttu-id="2a7b5-146">이미지가 충분해지면 **Train**(학습) 단추를 클릭하여 클라우드에서 모델 학습 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-146">Once you have enough images click on the **Train** button to start the model training process in the cloud.</span></span> <span data-ttu-id="2a7b5-147">학습을 활성화하면 모든 이미지가 업로드되고 학습이 시작되며, 최대 1분 이상 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-147">Activating the training will upload all images and then start the training, this can take up to a minute or more.</span></span> <span data-ttu-id="2a7b5-148">메뉴 안의 메시지는 현재 진행 상황을 나타내며 완료가 나타나면 애플리케이션을 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-148">A message inside the menu indicates the current progress and once it indicates the completion you can stop the application</span></span>

> [!TIP]
> <span data-ttu-id="2a7b5-149">**ObjectDetectionManager(스크립트)** 는 찍힌 이미지를 Custom Vision 서비스에 직접 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-149">The **ObjectDetectionManager (script)** directly uploads taken images into the Custom Vision service.</span></span> <span data-ttu-id="2a7b5-150">대안으로, Custom Vision API는 이미지 URL을 허용하며, 연습으로 **ObjectDetectionManager(script)** 를 수정하여 이미지를 Blob 스토리지에 대신 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-150">As an alternative the custom vision API accepts URLs to the images, as an exercise you can modify the **ObjectDetectionManager (script)** to upload the images to a Blob storage instead.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="2a7b5-151">개체 감지</span><span class="sxs-lookup"><span data-stu-id="2a7b5-151">Detect objects</span></span>

<span data-ttu-id="2a7b5-152">이제 학습된 모델을 테스트에 추가하고, 애플리케이션을 실행하고, 주 메뉴에서 **검색 개체** 를 클릭하고 해당 **추적된 개체** 의 이름을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-152">You can now put the trained model to the test, run the application and from the *main menu* click on **Search Object** and type the name of the **Tracked Object** in question.</span></span> <span data-ttu-id="2a7b5-153">**Object Card**(개체 카드)가 표시되면 **Custom Vision** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-153">The **Object Card** will appear and click on the **Custom Vision** button.</span></span> <span data-ttu-id="2a7b5-154">여기에서 **ObjectDetectionManager** 는 카메라의 배경에서 이미지를 캡처하기 시작하고 진행률이 메뉴에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-154">From here the **ObjectDetectionManager** will start taking image captures in the background from the camera and the progress will be indicated on the menu.</span></span> <span data-ttu-id="2a7b5-155">모델을 학습시키는 데 사용한 개체로 카메라를 향하게 하면 잠시 후에 개체를 감지하는 것이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-155">Point the camera to the object you used to train the model and you will see that after a short while it will detect the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2a7b5-156">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-156">Congratulations</span></span>

<span data-ttu-id="2a7b5-157">이 자습서에서는 Azure Custom Vision을 사용하여 이미지를 학습시키고 분류 서비스를 사용하여 연결된 **추적된 개체** 와 일치하는 이미지를 감지하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-157">In this tutorial you learned how Azure Custom Vision can be used to train images and use the classification service to detect images that match the associated **Tracked Object**.</span></span>

<span data-ttu-id="2a7b5-158">다음 자습서에서는 Azure Spatial Anchors를 사용하여 추적된 개체를 물질계의 위치에 링크하는 방법과 사용자를 추적된 개체에 링크된 위치로 안내하는 화살표를 표시하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="2a7b5-158">In the next tutorial you will learn how to use Azure Spatial Anchors to link a *Tracked Object* with a location in the physical world and how to display an arrow that will guide the user back to the Tracked Object's linked location.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2a7b5-159">다음 자습서: 4. Azure Spatial Anchors 통합</span><span class="sxs-lookup"><span data-stu-id="2a7b5-159">Next tutorial: 4. Integrating Azure Spatial Anchors</span></span>](mr-learning-azure-04.md)