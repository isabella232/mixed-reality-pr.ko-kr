---
title: MR 및 Azure 302b - Custom Vision
description: 이 과정을 완료 하 여 machine learning 모델을 학습 한 다음 학습 된 모델을 사용 하 여 혼합 현실 응용 프로그램 내에서 유사한 개체를 인식 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 사용자 지정 비전, hololens, 모던, vr, Windows 10, Visual Studio
ms.openlocfilehash: d40dc1cf23ee8040406047eaddd7ee3b70365199
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679552"
---
# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="b2d3f-104">MR 및 Azure 302b: Custom Vision</span><span class="sxs-lookup"><span data-stu-id="b2d3f-104">MR and Azure 302b: Custom vision</span></span>

<br>

>[!NOTE]
><span data-ttu-id="b2d3f-105">Mixed Reality 아카데미 자습서는 HoloLens(1세대) 및 Mixed Reality 몰입형 헤드셋을 염두에 두고 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b2d3f-106">따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b2d3f-107">이러한 자습서는 HoloLens 2에 사용되는 최신 도구 집합 또는 상호 작용으로 업데이트되지 **_않습니다_**.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b2d3f-108">대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b2d3f-109">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b2d3f-110">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>


<span data-ttu-id="b2d3f-111">이 과정에서는 혼합 현실 응용 프로그램에서 Azure Custom Vision 기능을 사용 하 여 제공 된 이미지 내에서 사용자 지정 시각적 콘텐츠를 인식 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="b2d3f-112">이 서비스를 사용 하면 개체 이미지를 사용 하 여 기계 학습 모델을 학습 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="b2d3f-113">그러면 학습 된 모델을 사용 하 여 Microsoft HoloLens의 카메라 캡처 또는 모던 (VR 용 PC) 헤드셋에 연결 된 카메라에 의해 제공 되는 것과 유사한 개체를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![과정 결과](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="b2d3f-115">Azure Custom Vision는 개발자가 사용자 지정 이미지 분류자를 빌드할 수 있게 해 주는 Microsoft 인지 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="b2d3f-116">이러한 분류자는 새 이미지와 함께 사용 하 여 새 이미지 내의 개체를 인식 하거나 분류할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="b2d3f-117">이 서비스는 간단 하 고 사용 하기 쉬운 온라인 포털을 제공 하 여 프로세스를 간소화 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="b2d3f-118">자세한 내용은 [Azure Custom Vision Service 페이지](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="b2d3f-119">이 과정을 완료 하면 다음과 같은 두 가지 모드로 작업할 수 있는 혼합 현실 응용 프로그램이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="b2d3f-120">**분석 모드**: 이미지를 업로드 하 고, 태그를 만들고, 서비스를 학습 하 여 다른 개체 (이 경우 마우스 및 키보드)를 인식할 수 있도록 하 여 Custom Vision Service를 수동으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="b2d3f-121">그런 다음 카메라를 사용 하 여 이미지를 캡처하는 HoloLens 앱을 만들고 실제 세계에서 해당 개체를 인식 해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="b2d3f-122">**학습 모드**: 앱에서 "학습 모드"를 사용 하는 코드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="b2d3f-123">학습 모드에서는 HoloLens 카메라를 사용 하 여 이미지를 캡처하고, 캡처한 이미지를 서비스에 업로드 하 고, 사용자 지정 비전 모델을 학습할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="b2d3f-124">이 과정을 통해 Custom Vision Service에서 Unity 기반 샘플 응용 프로그램으로 결과를 가져오는 방법을 배울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="b2d3f-125">빌드할 수 있는 사용자 지정 응용 프로그램에 이러한 개념을 적용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="b2d3f-126">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="b2d3f-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b2d3f-127">과정</span><span class="sxs-lookup"><span data-stu-id="b2d3f-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b2d3f-128"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b2d3f-128"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b2d3f-129"><a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="b2d3f-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="b2d3f-130">MR 및 Azure 302b: Custom Vision</span><span class="sxs-lookup"><span data-stu-id="b2d3f-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="b2d3f-131">✔️</span><span class="sxs-lookup"><span data-stu-id="b2d3f-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="b2d3f-132">✔️</span><span class="sxs-lookup"><span data-stu-id="b2d3f-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="b2d3f-133">이 과정에서 주로 HoloLens에 초점을 맞춘 반면,이 과정에서 배운 내용을 Windows Mixed Reality 모던 (VR) 헤드셋에도 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="b2d3f-134">모던 (VR) 헤드셋은 액세스할 수 있는 카메라를 포함 하지 않으므로 PC에 연결 된 외부 카메라가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="b2d3f-135">이 과정을 진행 하면서 모던 (VR) 헤드셋을 지원 하기 위해 사용 해야 하는 변경 내용에 대 한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b2d3f-136">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b2d3f-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b2d3f-137">이 자습서는 Unity 및 c #에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="b2d3f-138">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (7 월 2018)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="b2d3f-139">[도구 설치](../../install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-139">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="b2d3f-140">이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="b2d3f-141">모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC</span><span class="sxs-lookup"><span data-stu-id="b2d3f-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="b2d3f-142">개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="b2d3f-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b2d3f-143">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="b2d3f-143">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b2d3f-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="b2d3f-144">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b2d3f-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b2d3f-145">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="b2d3f-146">개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](../../../discover/immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](../../../hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="b2d3f-146">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](../../../hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="b2d3f-147">PC에 연결 된 카메라 (몰입 형 헤드셋 개발용)</span><span class="sxs-lookup"><span data-stu-id="b2d3f-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="b2d3f-148">Azure 설정 및 Custom Vision API 검색을 위한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="b2d3f-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="b2d3f-149">Custom Vision Service에서 인식 하고자 하는 각 개체에 대해 5 개 이상의 이미지 (10 개 이상 권장)를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="b2d3f-150">원할 경우 [이 과정에서 이미 제공 된 이미지 (컴퓨터 마우스 및 키보드) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="b2d3f-151">시작하기 전 확인 사항</span><span class="sxs-lookup"><span data-stu-id="b2d3f-151">Before you start</span></span>

1.  <span data-ttu-id="b2d3f-152">이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="b2d3f-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="b2d3f-153">HoloLens를 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="b2d3f-154">HoloLens를 설정 하는 데 지원이 필요한 경우 [hololens 설정 문서를 방문](https://docs.microsoft.com/hololens/hololens-setup)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="b2d3f-155">새 HoloLens 앱 개발을 시작할 때 보정 및 센서 조정을 수행 하는 것이 좋습니다 (경우에 따라 각 사용자에 대해 해당 작업을 수행 하는 데 도움이 될 수 있음).</span><span class="sxs-lookup"><span data-stu-id="b2d3f-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="b2d3f-156">보정에 대 한 도움말을 보려면 [HoloLens 보정 문서에](../../../calibration.md#hololens-2)대 한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](../../../calibration.md#hololens-2).</span></span>

<span data-ttu-id="b2d3f-157">센서 조정에 대 한 도움말을 보려면 [HoloLens 센서 조정 문서에 대 한 링크를](../../../sensor-tuning.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](../../../sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="b2d3f-158">1 장-Custom Vision Service 포털</span><span class="sxs-lookup"><span data-stu-id="b2d3f-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="b2d3f-159">Azure에서 *Custom Vision Service* 을 사용 하려면 응용 프로그램에서 사용할 수 있도록 서비스 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="b2d3f-160">먼저 [ *Custom Vision Service* 기본 페이지로 이동](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="b2d3f-161">**시작** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-161">Click on the **Get Started** button.</span></span>

    ![Custom Vision Service 시작](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="b2d3f-163">*Custom Vision Service* 포털에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-163">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![포털에 로그인](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="b2d3f-165">아직 Azure 계정이 없는 경우 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-165">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="b2d3f-166">교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-166">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="b2d3f-167">처음으로 로그인 한 후에는 *서비스 사용 약관* 패널이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-167">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="b2d3f-168">확인란을 클릭 하 여 약관에 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-168">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="b2d3f-169">그런 다음 **동의 함** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-169">Then click on **I agree**.</span></span>

    ![서비스 약관](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="b2d3f-171">조건에 동의한 경우 포털의 *프로젝트* 섹션으로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-171">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="b2d3f-172">**새 프로젝트** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-172">Click on **New Project**.</span></span>

    ![새 프로젝트 만들기](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="b2d3f-174">탭이 오른쪽에 표시 되 고 프로젝트의 일부 필드를 지정 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-174">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="b2d3f-175">프로젝트의 *이름을* 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-175">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="b2d3f-176">프로젝트에 대 한 *설명을* 삽입 합니다 (*선택 사항*).</span><span class="sxs-lookup"><span data-stu-id="b2d3f-176">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="b2d3f-177">리소스 그룹을 선택 하거나 새 *리소스 그룹* 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-177">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="b2d3f-178">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-178">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="b2d3f-179">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 과정)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-179">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="b2d3f-180">*프로젝트 형식을* **분류** 로 설정</span><span class="sxs-lookup"><span data-stu-id="b2d3f-180">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="b2d3f-181">*도메인* 을 **일반** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-181">Set the *Domains* as **General**.</span></span>

        ![도메인 설정](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="b2d3f-183">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-183">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="b2d3f-184">작업이 완료 되 면 **프로젝트 만들기** 를 클릭 하면 Custom Vision Service 프로젝트 페이지로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-184">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="b2d3f-185">2 장-Custom Vision 프로젝트 학습</span><span class="sxs-lookup"><span data-stu-id="b2d3f-185">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="b2d3f-186">Custom Vision 포털에서 기본 목표는 이미지의 특정 개체를 인식할 수 있도록 프로젝트를 학습 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-186">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="b2d3f-187">응용 프로그램에서 인식 하는 각 개체에 대해 10 개 이상의 이미지가 필요 하지만 10 개 이상 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-187">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="b2d3f-188">[이 과정에서 제공 되는 이미지 (컴퓨터 마우스 및 키보드)를 사용할 수](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-188">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="b2d3f-189">Custom Vision Service 프로젝트를 학습 하려면:</span><span class="sxs-lookup"><span data-stu-id="b2d3f-189">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="b2d3f-190">태그 옆에 있는 단추를 클릭 **+** **합니다.**</span><span class="sxs-lookup"><span data-stu-id="b2d3f-190">Click on the **+** button next to **Tags.**</span></span>

    ![새 태그 추가](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="b2d3f-192">인식할 개체의 **이름을** 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-192">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="b2d3f-193">**Save** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-193">Click on **Save**.</span></span>

    ![개체 이름 추가 및 저장](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="b2d3f-195">**태그가** 추가 된 것을 확인할 수 있습니다 (표시 되기 위해 페이지를 다시 로드 해야 할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="b2d3f-195">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="b2d3f-196">확인란이 아직 선택 되어 있지 않은 경우 새 태그 옆에 있는 확인란을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-196">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![새 태그 사용](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="b2d3f-198">페이지의 가운데에 있는 **이미지 추가** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-198">Click on **Add Images** in the center of the page.</span></span>

    ![이미지 추가](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="b2d3f-200">**로컬 파일 찾아보기** 를 클릭 하 고, 업로드할 이미지를 검색 한 다음 선택 하 고 최소 5 (5)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-200">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="b2d3f-201">이러한 모든 이미지에는 학습 중인 개체가 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-201">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="b2d3f-202">한 번에 여러 이미지를 선택 하 여 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-202">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="b2d3f-203">탭에서 이미지를 볼 수 있는 경우 **내 태그** 상자에서 적절 한 태그를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-203">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![태그 선택](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="b2d3f-205">**파일 업로드** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-205">Click on **Upload files**.</span></span> <span data-ttu-id="b2d3f-206">파일이 업로드 되기 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-206">The files will begin uploading.</span></span> <span data-ttu-id="b2d3f-207">업로드를 확인 한 후 **완료** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-207">Once you have confirmation of the upload, click **Done**.</span></span>

    ![파일 업로드](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="b2d3f-209">같은 프로세스를 반복 하 여 **키보드** 라는 새 **태그** 를 만들고 적절 한 사진을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-209">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="b2d3f-210">새 태그를 만든 후 *마우스* 를 **선택 취소** 하 여 *이미지 추가* 창을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-210">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="b2d3f-211">두 태그를 모두 설정 했으면 **학습** 을 클릭 하 고 첫 번째 학습 반복이 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-211">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![학습 반복 사용](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="b2d3f-213">빌드된 후에는 기본 및 **예측 URL** **만들기** 라는 두 개의 단추를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-213">Once it's built, you'll be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="b2d3f-214">먼저 **기본 설정** 을 클릭 한 다음 **예측 URL** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-214">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![기본 및 예측 URL 만들기](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="b2d3f-216">이에서 제공 하는 끝점 URL은 모든 *반복* 이 기본값으로 표시 된 것으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-216">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="b2d3f-217">따라서 나중에 새 *반복* 을 만들고 기본값으로 업데이트할 경우에는 코드를 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-217">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="b2d3f-218">*예측 url* 을 클릭 한 후에는 *메모장* 을 열고, 코드에서 나중에 필요할 때 검색할 수 있도록 **url** 및 **예측 키** 를 복사 하 여 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-218">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![URL 및 Prediction-Key 복사 및 붙여넣기](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="b2d3f-220">화면 오른쪽 위에 있는 **코그** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-220">Click on the **Cog** at the top right of the screen.</span></span>

    ![코그 아이콘을 클릭 하 여 설정을 엽니다.](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="b2d3f-222">**학습 키** 를 복사 하 여 나중에 사용할 수 있도록 *메모장* 에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-222">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![학습 키 복사](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="b2d3f-224">또한 **프로젝트 Id** 를 복사 하 고 나중에 사용할 수 있도록 *메모장* 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-224">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![프로젝트 id 복사](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="b2d3f-226">3 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="b2d3f-226">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="b2d3f-227">다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-227">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="b2d3f-228">*Unity* 를 열고 **새로 만들기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-228">Open *Unity* and click **New**.</span></span>

    ![새 Unity 프로젝트 만들기](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="b2d3f-230">이제 Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-230">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="b2d3f-231">**AzureCustomVision을 삽입 합니다.**</span><span class="sxs-lookup"><span data-stu-id="b2d3f-231">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="b2d3f-232">프로젝트 템플릿이 **3d** 로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-232">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="b2d3f-233">위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-233">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="b2d3f-234">그런 다음 **프로젝트 만들기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-234">Then, click **Create project**.</span></span>

    ![프로젝트 설정 구성](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="b2d3f-236">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio** 로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-236">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="b2d3f-237">**Edit*  >  *기본 설정* 편집* 으로 이동한 다음 새 창에서 **외부 도구** 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-237">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="b2d3f-238">**외부 스크립트 편집기** 를 **Visual Studio 2017** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-238">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="b2d3f-239">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-239">Close the **Preferences** window.</span></span>

    ![외부 도구 구성](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="b2d3f-241">그런 다음 **파일 > 빌드 설정** 으로 이동 하 고 **유니버설 Windows 플랫폼** 을 선택한 후 **플랫폼 전환** 단추를 클릭 하 여 선택 항목을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-241">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![<span data-ttu-id="b2d3f-242">빌드 설정 구성</span><span class="sxs-lookup"><span data-stu-id="b2d3f-242">Configure build settings</span></span> ](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="b2d3f-243">아직 **파일 > 빌드 설정을** 사용 하 고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-243">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="b2d3f-244">**대상 장치가** **HoloLens** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="b2d3f-244">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="b2d3f-245">모던 헤드셋의 경우 **대상 장치** 를 *모든 장치로* 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-245">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="b2d3f-246">**빌드 형식이** **D3D** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-246">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="b2d3f-247">**SDK** 가 **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="b2d3f-247">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="b2d3f-248">**Visual Studio 버전이** **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="b2d3f-248">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="b2d3f-249">**빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="b2d3f-249">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="b2d3f-250">장면을 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-250">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="b2d3f-251">이렇게 하려면 열려 있는 **장면 추가** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-251">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="b2d3f-252">저장 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-252">A save window will appear.</span></span>

            ![빌드 목록에 열린 장면 추가](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="b2d3f-254">이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을** 로 지정한 다음</span><span class="sxs-lookup"><span data-stu-id="b2d3f-254">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![새 장면 폴더 만들기](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="b2d3f-256">새로 만든 **장면** 폴더를 연 다음 *파일 이름:* 텍스트 필드에 **CustomVisionScene** 를 입력 하 고 **저장** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-256">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![새 장면 파일 이름](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="b2d3f-258">Unity 프로젝트와 연결 되어 있어야 하므로 *자산* 폴더 내에 unity 장면을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-258">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="b2d3f-259">배경 폴더 (및 기타 유사한 폴더)를 만드는 것은 Unity 프로젝트를 구조화 하는 일반적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-259">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="b2d3f-260">*빌드 설정* 의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-260">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![기본 빌드 설정](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="b2d3f-262">*빌드 설정* 창에서 **플레이어 설정** 단추를 클릭 하면 *검사기* 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-262">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="b2d3f-263">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-263">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="b2d3f-264">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-264">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="b2d3f-265">**Scripting Runtime 버전** 은 **실험적 (.Net 4.6 이와 동일)** 이어야 하며,이 경우 편집기를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-265">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="b2d3f-266">**Scripting 백엔드** 는 **.net** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-266">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="b2d3f-267">**API 호환성 수준은** **.net 4.6** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-267">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![API compantiblity 설정](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="b2d3f-269">**게시 설정** 탭의 **기능** 아래에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-269">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="b2d3f-270">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="b2d3f-270">**InternetClient**</span></span>

        2.  <span data-ttu-id="b2d3f-271">**웹캠**</span><span class="sxs-lookup"><span data-stu-id="b2d3f-271">**Webcam**</span></span>

        3. <span data-ttu-id="b2d3f-272">**마이크**</span><span class="sxs-lookup"><span data-stu-id="b2d3f-272">**Microphone**</span></span>

        ![게시 설정 구성](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="b2d3f-274">패널의 아래쪽에서 **XR 설정** ( **게시 설정** 아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-274">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![XR 설정 구성](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="b2d3f-276">*빌드 설정* 으로 돌아가기 *Unity C \# 프로젝트가* 더 이상 회색으로 표시 되지 않습니다 .이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-276">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="b2d3f-277">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-277">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="b2d3f-278">장면 및 프로젝트를 저장 합니다 (**파일 > 장면/파일 저장 > 프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="b2d3f-278">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="b2d3f-279">4 장-Unity에서 Newtonsoft.json DLL 가져오기</span><span class="sxs-lookup"><span data-stu-id="b2d3f-279">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b2d3f-280">이 과정의 *Unity 설정* 구성 요소를 건너뛰고 계속 해 서 코드를 계속 사용 하려면이 [302b. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)를 다운로드 하 여 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 [6 장](#chapter-6---create-the-customvisionanalyser-class)에서 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-280">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="b2d3f-281">이 과정에서는 **newtonsoft.json** 라이브러리를 사용 해야 합니다 .이 라이브러리는 자산에 DLL로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-281">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="b2d3f-282">이 라이브러리를 포함 하는 패키지는 [이 링크에서 다운로드할 수 있습니다](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="b2d3f-282">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="b2d3f-283">Newtonsoft.json 라이브러리를 프로젝트로 가져오려면이 과정에서 제공 되는 Unity 패키지를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-283">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="b2d3f-284">**자산*  >  *가져오기* *패키지*  >  *사용자 지정* *패키지** 메뉴 옵션을 사용 하 여 *unitypackage* 을 Unity에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-284">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="b2d3f-285">표시 되는 **Unity 패키지 가져오기** 상자에서 **플러그 인** 을 포함 하 여 모든 항목을 선택 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-285">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![모든 패키지 항목 가져오기](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="b2d3f-287">**가져오기** 단추를 클릭 하 여 프로젝트에 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-287">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="b2d3f-288">프로젝트 뷰에서 **플러그** 인의 **newtonsoft.json** 폴더로 이동 하 고 *플러그 인에서Newtonsoft.Js* 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-288">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![Newtonsoft.json 플러그 인 선택](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="b2d3f-290">*플러그 인에 대 한Newtonsoft.Js* 선택 된 상태에서 **모든 플랫폼이** 선택 **취소** 되어 있는지 확인 하 고 **WSAPlayer** 도 **선택 취소** 한 다음 **적용** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-290">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="b2d3f-291">이는 파일이 올바르게 구성 되었는지 확인 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-291">This is just to confirm that the files are configured correctly.</span></span>

    ![Newtonsoft.json 플러그 인 구성](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="b2d3f-293">이러한 플러그 인을 표시 하면 Unity 편집기 에서만 사용 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-293">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="b2d3f-294">WSA 폴더에는 프로젝트를 Unity에서 내보낸 후에 사용 되는 다른 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-294">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="b2d3f-295">다음으로 **newtonsoft.json** 폴더 내에서 **WSA** 폴더를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-295">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="b2d3f-296">방금 구성한 파일의 복사본이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-296">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="b2d3f-297">파일을 선택 하 고 검사기에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-297">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="b2d3f-298">**모든 플랫폼이** **선택 취소** 되어 있음</span><span class="sxs-lookup"><span data-stu-id="b2d3f-298">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="b2d3f-299">**only** **WSAPlayer** 만 **선택** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-299">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="b2d3f-300">**Dont 프로세스** 를 **선택 했습니다** .</span><span class="sxs-lookup"><span data-stu-id="b2d3f-300">**Dont process** is **checked**</span></span>

    ![Newtonsoft.json 플러그 인 플랫폼 설정 구성](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="b2d3f-302">5 장-카메라 설정</span><span class="sxs-lookup"><span data-stu-id="b2d3f-302">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="b2d3f-303">계층 패널에서 *기본 카메라* 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-303">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="b2d3f-304">선택한 후에는 *검사기 패널* 에서 *주 카메라* 의 모든 구성 요소를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-304">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="b2d3f-305">*카메라* 개체의 이름을 **주 카메라로** 지정 해야 합니다 (철자 확인).</span><span class="sxs-lookup"><span data-stu-id="b2d3f-305">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="b2d3f-306">기본 카메라 **태그** 는 **maincamera** 로 설정 되어야 합니다 (철자 확인).</span><span class="sxs-lookup"><span data-stu-id="b2d3f-306">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="b2d3f-307">**변환 위치가** **0, 0, 0** 으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-307">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="b2d3f-308">**Clear 플래그** 를 **단색** 으로 설정 합니다. 몰입 형 헤드셋의 경우이를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-308">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="b2d3f-309">카메라 구성 요소의 **배경색** 을 **검은색, 알파 0 (16 진수 코드: #00000000)** 으로 설정 합니다 (몰입 형 헤드셋의 경우 무시).</span><span class="sxs-lookup"><span data-stu-id="b2d3f-309">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![카메라 구성 요소 속성 구성](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="b2d3f-311">6 장-CustomVisionAnalyser 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b2d3f-311">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="b2d3f-312">이 시점에서 일부 코드를 작성할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-312">At this point you are ready to write some code.</span></span>

<span data-ttu-id="b2d3f-313">*CustomVisionAnalyser* 클래스로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-313">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="b2d3f-314">아래에 표시 된 코드에서 **Custom Vision Service** 호출은 **Custom Vision REST API** 를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-314">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="b2d3f-315">이를 사용 하 여이 API를 구현 하 고 사용 하는 방법을 확인할 수 있습니다 (사용자가 직접 비슷한 항목을 구현 하는 방법을 이해 하는 데 유용).</span><span class="sxs-lookup"><span data-stu-id="b2d3f-315">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="b2d3f-316">Microsoft는 서비스를 호출 하는 데 사용할 수 있는 **CUSTOM VISION SERVICE SDK** 를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-316">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="b2d3f-317">자세한 내용은 [CUSTOM VISION SERVICE SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-317">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="b2d3f-318">이 클래스는 다음을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-318">This class is responsible for:</span></span>

-   <span data-ttu-id="b2d3f-319">캡처된 최신 이미지를 바이트 배열로 로드 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-319">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="b2d3f-320">분석을 위해 바이트 배열을 Azure *Custom Vision Service* 인스턴스로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-320">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="b2d3f-321">JSON 문자열로 응답을 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-321">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="b2d3f-322">응답을 deserialize 하 고 결과 *예측* 을 *SceneOrganiser* 클래스에 전달 하 여 응답이 표시 되는 방법을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-322">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="b2d3f-323">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b2d3f-323">To create this class:</span></span>

1.  <span data-ttu-id="b2d3f-324">*프로젝트 패널* 에 있는 *자산 폴더* 를 마우스 오른쪽 단추로 클릭 한 다음 **> 폴더 만들기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-324">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="b2d3f-325">폴더 **스크립트** 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-325">Call the folder **Scripts**.</span></span>

    ![스크립트 폴더 만들기](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="b2d3f-327">위에서 만든 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-327">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="b2d3f-328">폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **Create**,  >  **C \# 스크립트** 만들기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-328">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b2d3f-329">스크립트 이름을 *CustomVisionAnalyser* 로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-329">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="b2d3f-330">새 *CustomVisionAnalyser* 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-330">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="b2d3f-331">다음과 일치 하도록 파일 위쪽에서 네임 스페이스를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-331">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="b2d3f-332">*CustomVisionAnalyser* 클래스에서 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-332">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="b2d3f-333">**예측 키** 를 **predictionKey** 변수에 삽입 하 고 **예측 끝점** 을 **predictionEndpoint** 변수에 삽입 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-333">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="b2d3f-334">이 과정의 앞부분에서 *메모장* 에 복사 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-334">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="b2d3f-335">이제 initialize **()** 에 대 한 코드를 추가 하 여 인스턴스 변수를 초기화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-335">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="b2d3f-336">**Start ()** 및 **Update ()** 메서드를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-336">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="b2d3f-337">그런 다음 *ImageCapture* 클래스에서 캡처된 이미지의 분석 결과를 가져오는 코 루틴 (아래 정적 **GetImageAsByteArray ()** 메서드 포함)를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-337">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b2d3f-338">**AnalyseImageCapture** 코 루틴에는 아직 만들지 않은 *SceneOrganiser* 클래스에 대 한 호출이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-338">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="b2d3f-339">따라서 **해당 줄을 현재 주석으로 처리** 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-339">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  <span data-ttu-id="b2d3f-340">**Unity** 로 반환 하기 전에 **Visual Studio** 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-340">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="b2d3f-341">7 장-CustomVisionObjects 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b2d3f-341">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="b2d3f-342">지금 만들 클래스는 *CustomVisionObjects* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-342">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="b2d3f-343">이 스크립트에는 다른 클래스에서 *Custom Vision Service* 에 대 한 호출을 serialize 및 deserialize 하는 데 사용 하는 여러 개체가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-343">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="b2d3f-344">아래 JSON 구조가 [*Custom Vision 예측 v 2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)에서 작동 하도록 설정 되었으므로 Custom Vision Service에서 제공 하는 끝점을 기록해 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-344">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="b2d3f-345">다른 버전이 있는 경우 아래 구조를 업데이트 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-345">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="b2d3f-346">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b2d3f-346">To create this class:</span></span>

1.  <span data-ttu-id="b2d3f-347">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **Create**  >  **C \# 스크립트** 만들기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-347">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b2d3f-348">*CustomVisionObjects* 스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-348">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="b2d3f-349">새 **CustomVisionObjects** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-349">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="b2d3f-350">파일의 맨 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-350">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="b2d3f-351">*CustomVisionObjects* 클래스 내에서 **Start ()** 및 **Update ()** 메서드를 삭제 합니다. 이 클래스는 이제 비어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-351">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="b2d3f-352">*CustomVisionObjects* 클래스 **외부** 에 다음 클래스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-352">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="b2d3f-353">이러한 개체는 *newtonsoft.json* 라이브러리에서 응답 데이터를 serialize 및 deserialize 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-353">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="b2d3f-354">8 장-VoiceRecognizer 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b2d3f-354">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="b2d3f-355">이 클래스는 사용자의 음성 입력을 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-355">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="b2d3f-356">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b2d3f-356">To create this class:</span></span>

1.  <span data-ttu-id="b2d3f-357">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **Create**  >  **C \# 스크립트** 만들기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-357">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b2d3f-358">*VoiceRecognizer* 스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-358">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="b2d3f-359">새 **VoiceRecognizer** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-359">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="b2d3f-360">*VoiceRecognizer* 클래스 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-360">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="b2d3f-361">그런 다음 *VoiceRecognizer* 클래스 내에서 *Start ()* 메서드 위의 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-361">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="b2d3f-362">사용 가능한 **()** 및 **Start ()** 메서드를 추가 합니다. 후자는 이미지에 태그를 연결할 때 인식할 사용자 *키워드* 를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-362">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="b2d3f-363">**Update ()** 메서드를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-363">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="b2d3f-364">음성 입력이 인식 될 때마다 호출 되는 다음 처리기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-364">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="b2d3f-365">**Unity** 로 반환 하기 전에 **Visual Studio** 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-365">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="b2d3f-366">오류가 발생 하는 것 처럼 보일 수 있는 코드에 대해 걱정 하지 마세요. 추가 클래스를 곧 제공 하면이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-366">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="b2d3f-367">9 장-CustomVisionTrainer 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b2d3f-367">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="b2d3f-368">이 클래스는 일련의 웹 호출을 연결 하 여 *Custom Vision Service* 를 학습 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-368">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="b2d3f-369">각 호출은 코드 바로 위에 자세히 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-369">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="b2d3f-370">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b2d3f-370">To create this class:</span></span>

1.  <span data-ttu-id="b2d3f-371">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **Create**  >  **C \# 스크립트** 만들기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-371">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b2d3f-372">*CustomVisionTrainer* 스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-372">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="b2d3f-373">새 *CustomVisionTrainer* 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-373">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="b2d3f-374">*CustomVisionTrainer* 클래스 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-374">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="b2d3f-375">그런 다음 *CustomVisionTrainer* 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-375">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="b2d3f-376">여기에 사용 된 학습 URL은 *Custom Vision 교육 1.2* 설명서에 제공 되며 구조는 다음과 같습니다. https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="b2d3f-376">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="b2d3f-377">자세한 내용은 [*Custom Vision 학습 v 1.2 참조 API를 참조*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)하세요.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-377">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="b2d3f-378">**CustomVisionObjects** 클래스 내에서 사용 되는 JSON 구조가 [*Custom Vision 학습 v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)와 함께 작동 하도록 설정 되었으므로 Custom Vision Service에서 학습 모드를 제공 하는 끝점을 기록해 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-378">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="b2d3f-379">다른 버전이 있는 경우 *개체* 구조를 업데이트 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-379">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="b2d3f-380">앞에서 설명한 대로 **서비스 키** (학습 키) 값 및 **프로젝트 Id** 값을 추가 했는지 확인 합니다. 이러한 값은 [과정의 앞부분에서 (2 장, 10 단계부터) 포털에서 수집한](#chapter-2---training-your-custom-vision-project)값입니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-380">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-project).</span></span>

5.  <span data-ttu-id="b2d3f-381">다음 **Start ()** 및 **활성 ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-381">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="b2d3f-382">이러한 메서드는 초기화 시 호출 되며 UI를 설정 하는 호출을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-382">Those methods are called on initialization and contain the call to set up the UI:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="b2d3f-383">**Update ()** 메서드를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-383">Delete the **Update()** method.</span></span> <span data-ttu-id="b2d3f-384">이 클래스에는이 클래스가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-384">This class will not need it.</span></span>

7.  <span data-ttu-id="b2d3f-385">**RequestTagSelection ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-385">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="b2d3f-386">이 메서드는 이미지를 캡처하고 장치에 저장 한 후에는이 메서드를 학습 하기 위해 *Custom Vision Service* 에 제출할 준비가 되었을 때 가장 먼저 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-386">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="b2d3f-387">이 메서드는 학습 UI에서 사용자가 캡처된 이미지에 태그를 지정할 때 사용할 수 있는 키워드 집합을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-387">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="b2d3f-388">또한 *VoiceRecognizer* 클래스에서 음성 입력을 위해 사용자에 게 수신 대기를 시작 하도록 경고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-388">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="b2d3f-389">**Verifytag ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-389">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="b2d3f-390">이 메서드는 **VoiceRecognizer** 클래스에서 인식 하는 음성 입력을 받고 유효성을 확인 한 다음 학습 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-390">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="b2d3f-391">**Submitimagefortraining ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-391">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="b2d3f-392">이 메서드는 Custom Vision Service 교육 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-392">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="b2d3f-393">첫 번째 단계는 사용자의 확인 된 음성 입력과 연결 된 서비스에서 **태그 Id** 를 검색 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-393">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="b2d3f-394">**태그 Id** 는 이미지와 함께 업로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-394">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="b2d3f-395">**TrainCustomVisionProject ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-395">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="b2d3f-396">이미지를 제출 하 고 태그를 지정 하면이 메서드가 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-396">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="b2d3f-397">서비스에 제출 된 모든 이전 이미지와 방금 업로드 한 이미지를 사용 하 여 학습 되는 새 반복을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-397">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="b2d3f-398">교육이 완료 되 면이 메서드는 새로 생성 된 **반복** 을 **기본값으로** 설정 하는 메서드를 호출 하 여 분석에 사용 하는 끝점이 최신 학습 된 반복 임을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-398">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="b2d3f-399">**SetDefaultIteration ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-399">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="b2d3f-400">이 메서드는 이전에 만들어지고 학습 된 반복을 *기본값으로* 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-400">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="b2d3f-401">완료 되 면이 메서드는 서비스에서 기존 반복을 삭제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-401">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="b2d3f-402">이 과정을 작성할 당시에는 서비스에서 동시에 사용할 수 있는 최대 10 개 반복의 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-402">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="b2d3f-403">**DeletePreviousIteration ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-403">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="b2d3f-404">이 메서드는 이전의 기본이 아닌 반복을 찾아 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-404">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="b2d3f-405">이 클래스에서 추가 하는 마지막 메서드는 웹 호출에서 바이트 배열로 캡처된 이미지를 변환 하는 데 사용 되는 **GetImageAsByteArray ()** 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-405">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. <span data-ttu-id="b2d3f-406">**Unity** 로 반환 하기 전에 **Visual Studio** 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-406">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="b2d3f-407">10 장-SceneOrganiser 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b2d3f-407">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="b2d3f-408">이 클래스는 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-408">This class will:</span></span>

-   <span data-ttu-id="b2d3f-409">기본 카메라에 연결할 **커서** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-409">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="b2d3f-410">서비스에서 실제 개체를 인식할 때 표시 되는 **레이블** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-410">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="b2d3f-411">적절 한 구성 요소를 연결 하 여 기본 카메라를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-411">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="b2d3f-412">**분석 모드** 의 경우 기본 카메라의 위치를 기준으로 적절 한 세계 공간에서 런타임에 레이블을 생성 하 고 Custom Vision Service에서 받은 데이터를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-412">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="b2d3f-413">**학습 모드인** 경우 학습 프로세스의 다양 한 단계를 표시 하는 UI를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-413">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="b2d3f-414">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b2d3f-414">To create this class:</span></span>

1.  <span data-ttu-id="b2d3f-415">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **Create**  >  **C \# 스크립트** 만들기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-415">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b2d3f-416">스크립트 이름을 *SceneOrganiser* 로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-416">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="b2d3f-417">새 *SceneOrganiser* 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-417">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="b2d3f-418">네임 스페이스는 하나만 필요 하며 *SceneOrganiser* 클래스 위에서 다른 네임 스페이스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-418">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="b2d3f-419">그런 다음 *SceneOrganiser* 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-419">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="b2d3f-420">**Start ()** 및 **Update ()** 메서드를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-420">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="b2d3f-421">변수 바로 아래에서 해제 **()** 메서드를 추가 하 여 클래스를 초기화 하 고 장면을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-421">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="b2d3f-422">이제 주 카메라 커서를 만들고 배치 하는 **CreateCameraCursor ()** 메서드를 추가 하 고 **CreateLabel ()** 메서드를 추가 하 여 **분석 레이블** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-422">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="b2d3f-423">**SetCameraStatus ()** 메서드를 추가 합니다 .이 메서드는 카메라 상태를 제공 하는 텍스트 메시에 사용할 메시지를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-423">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="b2d3f-424">**PlaceAnalysisLabel ()** 및 **SetTagsToLastLabel ()** 메서드를 추가 합니다 .이 메서드는 Custom Vision Service에서 장면으로 데이터를 생성 하 고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-424">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="b2d3f-425">마지막으로, 응용 프로그램이 학습 모드일 때 학습 프로세스의 여러 단계를 표시 하는 UI를 생성 하는 **CreateTrainingUI ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-425">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="b2d3f-426">또한이 메서드는 카메라 상태 개체를 만들 asha 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-426">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="b2d3f-427">**Unity** 로 반환 하기 전에 **Visual Studio** 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-427">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b2d3f-428">계속 하기 전에 **CustomVisionAnalyser** 클래스를 열고 **AnalyseLastImageCaptured ()** 메서드 내에서 다음 줄의 *주석 처리를 제거* 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-428">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="b2d3f-429">11 장-ImageCapture 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b2d3f-429">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="b2d3f-430">만들려는 다음 클래스는 *ImageCapture* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-430">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="b2d3f-431">이 클래스는 다음을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-431">This class is responsible for:</span></span>

-   <span data-ttu-id="b2d3f-432">HoloLens 카메라를 사용 하 여 이미지를 캡처하고 *앱* 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-432">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="b2d3f-433">사용자 로부터 탭 제스처를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-433">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="b2d3f-434">응용 프로그램을 *분석* 모드에서 실행할지 아니면 *학습* 모드로 실행할지를 결정 하는 *열거형* 값을 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-434">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="b2d3f-435">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b2d3f-435">To create this class:</span></span>

1.  <span data-ttu-id="b2d3f-436">이전에 만든 **스크립트** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-436">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="b2d3f-437">폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **> C \# 스크립트 만들기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-437">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="b2d3f-438">스크립트 이름을 *ImageCapture* 로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-438">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="b2d3f-439">새 **ImageCapture** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-439">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="b2d3f-440">파일의 맨 위에 있는 네임 스페이스를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-440">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="b2d3f-441">그런 다음 *ImageCapture* 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-441">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="b2d3f-442">이제 **활성 ()** 및 **Start ()** 메서드에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-442">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="b2d3f-443">탭 제스처가 발생할 때 호출 되는 처리기를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-443">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="b2d3f-444">*분석* 모드에서 **TapHandler** 메서드는 사진 캡처 루프를 시작 하거나 중지 하는 스위치 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-444">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="b2d3f-445">*학습* 모드에서는 카메라에서 이미지를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-445">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="b2d3f-446">커서가 녹색이 면 카메라에서 이미지를 사용할 수 있음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-446">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="b2d3f-447">커서가 빨간색 이면 카메라가 사용 중임을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-447">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="b2d3f-448">응용 프로그램이 이미지 캡처 프로세스를 시작 하 고 이미지를 저장 하는 데 사용 하는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-448">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  <span data-ttu-id="b2d3f-449">사진이 캡처되고 분석 준비가 될 때 호출 되는 처리기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-449">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="b2d3f-450">그런 다음 코드가 설정 된 모드에 따라 결과를 *CustomVisionAnalyser* 또는 *CustomVisionTrainer* 에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-450">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="b2d3f-451">**Unity** 로 반환 하기 전에 **Visual Studio** 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-451">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="b2d3f-452">모든 스크립트가 완료 되었으므로 Unity 편집기로 돌아가서 **scripts** 폴더의 **SceneOrganiser** 클래스를 클릭 하 여 *계층 패널* 의 **기본 카메라** 개체로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-452">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="b2d3f-453">12 장-빌드하기 전</span><span class="sxs-lookup"><span data-stu-id="b2d3f-453">Chapter 12 - Before building</span></span>

<span data-ttu-id="b2d3f-454">응용 프로그램에 대 한 철저 한 테스트를 수행 하려면 HoloLens에 테스트용으로 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-454">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="b2d3f-455">이렇게 하려면 먼저 다음을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-455">Before you do, ensure that:</span></span>

- <span data-ttu-id="b2d3f-456">[2 장](#chapter-2---training-your-custom-vision-project) 에서 설명한 모든 설정이 올바르게 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-456">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="b2d3f-457">**주 카메라** 검사기 패널의 모든 필드가 제대로 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-457">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="b2d3f-458">**SceneOrganiser** 스크립트는 **주 카메라** 개체에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-458">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="b2d3f-459">**예측 키** 를 **predictionKey** 변수에 삽입 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-459">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="b2d3f-460">**예측 끝점** 을 **predictionEndpoint** 변수에 삽입 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-460">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="b2d3f-461">*CustomVisionTrainer* 클래스의 **TrainingKey** 변수에 **학습 키** 를 삽입 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-461">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="b2d3f-462">*CustomVisionTrainer* 클래스의 **PROJECTID** 변수에 **프로젝트 ID** 를 삽입 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-462">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="b2d3f-463">13 장-응용 프로그램 빌드 및 테스트용으로 로드</span><span class="sxs-lookup"><span data-stu-id="b2d3f-463">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="b2d3f-464">*빌드* 프로세스를 시작 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-464">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="b2d3f-465">**파일 > 빌드 설정** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-465">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="b2d3f-466">Tick **Unity C \# 프로젝트**.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-466">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="b2d3f-467">**빌드** 를 클릭한 다음</span><span class="sxs-lookup"><span data-stu-id="b2d3f-467">Click **Build**.</span></span> <span data-ttu-id="b2d3f-468">Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 **파일 탐색기** 창을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-468">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="b2d3f-469">이제 해당 폴더를 만들고 이름을 **App** 으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-469">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="b2d3f-470">그런 다음 **앱** 폴더를 선택 하 고 **폴더 선택** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-470">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="b2d3f-471">Unity는 **응용** 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-471">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="b2d3f-472">Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)</span><span class="sxs-lookup"><span data-stu-id="b2d3f-472">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="b2d3f-473">HoloLens에 배포 하려면:</span><span class="sxs-lookup"><span data-stu-id="b2d3f-473">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="b2d3f-474">HoloLens의 IP 주소 (원격 배포의 경우)가 필요 하 고 HoloLens가 **개발자 모드** 에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-474">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="b2d3f-475">가상 하드 디스크 파일에 대한 중요 정보를 제공하려면</span><span class="sxs-lookup"><span data-stu-id="b2d3f-475">To do this:</span></span>

    1.  <span data-ttu-id="b2d3f-476">HoloLens를 입고 하는 동안 **설정을** 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-476">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="b2d3f-477">**네트워크 & 인터넷**  >  **wi-fi**  >  **고급 옵션** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-477">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="b2d3f-478">**IPv4** 주소를 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-478">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="b2d3f-479">그런 다음 **설정** 으로 다시 이동한 다음 개발자를 위한 **& 보안을 업데이트** 합니다.  >  **For Developers**</span><span class="sxs-lookup"><span data-stu-id="b2d3f-479">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="b2d3f-480">**에서 개발자 모드를** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-480">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="b2d3f-481">새 Unity 빌드 ( **앱** 폴더)로 이동 하 여 **Visual Studio** 에서 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-481">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="b2d3f-482">*솔루션 구성* 에서 **디버그** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-482">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="b2d3f-483">*솔루션 플랫폼* 에서 **X86, 원격 컴퓨터** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-483">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="b2d3f-484">원격 장치의 **IP 주소** (이 경우에는 HoloLens)를 삽입 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-484">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![IP 주소 설정](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="b2d3f-486">**빌드** 메뉴로 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 HoloLens로 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-486">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="b2d3f-487">이제 앱이 HoloLens에 설치 된 앱 목록에 표시 되어 시작할 준비가 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="b2d3f-487">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="b2d3f-488">모던 헤드셋에 배포 하려면 **솔루션 플랫폼** 을 *로컬 컴퓨터* 로 설정 하 고 **구성을** *디버그* 로 설정 하 고 *x 86* 을 **플랫폼** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-488">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="b2d3f-489">그런 다음 **빌드** 메뉴 항목을 사용 하 여 *솔루션 배포* 를 선택 하 여 로컬 컴퓨터에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-489">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="b2d3f-490">응용 프로그램을 사용 하려면:</span><span class="sxs-lookup"><span data-stu-id="b2d3f-490">To use the application:</span></span>

<span data-ttu-id="b2d3f-491">*학습* 모드와 *예측* 모드 간에 앱 기능을 전환 하려면 ImageCapture 클래스 내에 있는 *ImageCapture* **()** 메서드에 있는 **appmode** 변수를 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-491">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="b2d3f-492">또는</span><span class="sxs-lookup"><span data-stu-id="b2d3f-492">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="b2d3f-493">*학습* 모드:</span><span class="sxs-lookup"><span data-stu-id="b2d3f-493">In *Training* mode:</span></span>

- <span data-ttu-id="b2d3f-494">**마우스** 또는 **키보드** 를 확인 하 고 **탭 제스처** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-494">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="b2d3f-495">그런 다음 태그를 제공 하 라는 텍스트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-495">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="b2d3f-496">**마우스** 또는 **키보드** 를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-496">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="b2d3f-497">*예측* 모드에서:</span><span class="sxs-lookup"><span data-stu-id="b2d3f-497">In *Prediction* mode:</span></span>

- <span data-ttu-id="b2d3f-498">개체를 확인 하 고 **탭 제스처** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-498">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="b2d3f-499">확률이 가장 높은 개체 (정규화 됨)를 제공 하는 텍스트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-499">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="b2d3f-500">14 장-Custom Vision 모델 평가 및 개선</span><span class="sxs-lookup"><span data-stu-id="b2d3f-500">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="b2d3f-501">서비스를 보다 정확 하 게 만들려면 예측에 사용 되는 모델을 계속 학습 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-501">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="b2d3f-502">이 작업은 *학습* 및 *예측* 모드 모두에서 새로운 응용 프로그램을 사용 하 여 수행 되며, 후자는이 장에서 설명 하는 포털을 방문 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-502">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="b2d3f-503">모델을 지속적으로 개선 하기 위해 포털을 여러 번 다시 방문할 준비를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-503">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="b2d3f-504">Azure Custom Vision 포털에 다시 이동 하 여 프로젝트에 있는 경우 페이지의 상단 가운데에서 *예측* 탭을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-504">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![예측 탭 선택](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="b2d3f-506">응용 프로그램이 실행 되는 동안 서비스에 전송 된 모든 이미지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-506">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="b2d3f-507">이미지를 마우스로 가리키면 해당 이미지에 대해 수행 된 예측이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-507">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![예측 이미지 목록](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="b2d3f-509">이미지 중 하나를 선택 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-509">Select one of your images to open it.</span></span> <span data-ttu-id="b2d3f-510">열린 후에는 해당 이미지에 대 한 예측이 오른쪽에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-510">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="b2d3f-511">예측이 올바르고이 이미지를 서비스의 학습 모델에 추가 하려는 경우 *내 태그* 입력 상자를 클릭 하 고 연결 하려는 태그를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-511">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="b2d3f-512">작업이 완료 되 면 오른쪽 아래에 있는 *저장 및 닫기* 단추를 클릭 하 고 다음 이미지를 계속 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-512">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![열 이미지 선택](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="b2d3f-514">이미지 그리드로 돌아가서 태그를 추가 하 고 저장 한 이미지를 제거할 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-514">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="b2d3f-515">태그가 지정 된 항목이 없는 것으로 생각 되는 이미지를 찾은 경우 해당 이미지에서 틱을 클릭 하 고 (여러 이미지에 대해이 작업을 수행할 수 있음) 그리드 페이지의 오른쪽 위 모퉁이에서 *삭제* 를 클릭 하 여 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-515">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="b2d3f-516">다음에 나오는 팝업에서 *예, 삭제* 또는 *아니요* 를 클릭 하 여 삭제를 확인 하거나 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-516">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![이미지 삭제](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="b2d3f-518">계속할 준비가 되 면 오른쪽 위에 있는 녹색 *학습* 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-518">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="b2d3f-519">서비스 모델은 제공 된 모든 이미지를 사용 하 여 학습 됩니다 (더 정확 하 게 함).</span><span class="sxs-lookup"><span data-stu-id="b2d3f-519">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="b2d3f-520">학습을 완료 한 후에는 *기본 설정* 단추를 한 번 더 클릭 하 여 *예측 URL* 에서 서비스의 최신 반복을 계속 사용할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-520">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="b2d3f-521">![학습 서비스 모델 시작 ](images/AzureLabs-Lab302b-39.png) ![ 기본 옵션 만들기 옵션을 선택 합니다.](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="b2d3f-521">![Start training service model](images/AzureLabs-Lab302b-39.png) ![Select make default option](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="b2d3f-522">완료 된 Custom Vision API 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="b2d3f-522">Your finished Custom Vision API application</span></span>

<span data-ttu-id="b2d3f-523">축 하 합니다. Azure Custom Vision API를 활용 하 여 실제 개체를 인식 하 고, 서비스 모델을 학습 하 고, 표시 되는 내용에 대 한 확신을 표시 하는 혼합 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-523">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![완료 된 프로젝트 예제](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="b2d3f-525">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="b2d3f-525">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="b2d3f-526">연습 1</span><span class="sxs-lookup"><span data-stu-id="b2d3f-526">Exercise 1</span></span>

<span data-ttu-id="b2d3f-527">**Custom Vision Service** 를 학습 하 여 더 많은 개체를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-527">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="b2d3f-528">연습 2</span><span class="sxs-lookup"><span data-stu-id="b2d3f-528">Exercise 2</span></span>

<span data-ttu-id="b2d3f-529">학습 한 내용을 확장 하는 방법으로 다음 연습을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-529">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="b2d3f-530">개체가 인식 될 때 소리를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2d3f-530">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="b2d3f-531">연습 3</span><span class="sxs-lookup"><span data-stu-id="b2d3f-531">Exercise 3</span></span>

<span data-ttu-id="b2d3f-532">API를 사용 하 여 응용 프로그램이 분석 하는 것과 동일한 이미지를 사용 하 여 서비스를 다시 학습 하므로 서비스를 보다 정확 하 게 만들 수 있습니다 (예측 및 학습을 동시에 수행).</span><span class="sxs-lookup"><span data-stu-id="b2d3f-532">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
