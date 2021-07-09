---
title: Azure Spatial Anchors 시작
description: 이 과정을 완료하여 혼합 현실 애플리케이션에서 Azure Spatial Anchors를 사용하여 개체를 고정하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: eddde9b827dcf2a2f054f48a50f38946e5d98533
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175567"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="771b4-104">2. Azure Spatial Anchors 시작</span><span class="sxs-lookup"><span data-stu-id="771b4-104">2. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="771b4-105">이 자습서에서는 Azure Spatial Anchors 세션을 시작 및 중지하고 단일 디바이스에서 Azure Spatial Anchors를 생성, 업로드 및 다운로드하는 데 필요한 여러 단계를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-105">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="771b4-106">목표</span><span class="sxs-lookup"><span data-stu-id="771b4-106">Objectives</span></span>

* <span data-ttu-id="771b4-107">HoloLens 2용 Azure Spatial Anchors를 사용하여 개발하는 방법에 대한 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="771b4-107">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="771b4-108">공간 앵커를 만들고 Azure에서 가져오는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="771b4-108">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="771b4-109">Unity 프로젝트 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="771b4-109">Creating and preparing the Unity project</span></span>

<span data-ttu-id="771b4-110">이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-110">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="771b4-111">먼저 [프로젝트 초기화 및 첫 번째 애플리케이션 배포](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-111">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="771b4-112">[Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정</span><span class="sxs-lookup"><span data-stu-id="771b4-112">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="771b4-113">빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="771b4-113">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="771b4-114">TextMeshPro 필수 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="771b4-114">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="771b4-115">Mixed Reality Toolkit 가져오기 및 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="771b4-115">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="771b4-116">[장면 만들기 및 구성](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) 및 장면에 적절한 이름(예: *AzureSpatialAnchors*) 지정</span><span class="sxs-lookup"><span data-stu-id="771b4-116">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="771b4-117">그런 다음, [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필이 **DefaultHoloLens2ConfigurationProfile** 인지 확인하고, 공간 인식 메시의 표시 옵션을 **Occlusion(폐색)** 으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-117">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile**  and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a><span data-ttu-id="771b4-118">내장 Unity 패키지 설치 및 자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="771b4-118">Installing inbuilt Unity packages and Importing the tutorial assets</span></span>

[!INCLUDE[](includes/installing-packages-for-asa.md)]

## <a name="preparing-the-scene"></a><span data-ttu-id="771b4-119">장면 준비</span><span class="sxs-lookup"><span data-stu-id="771b4-119">Preparing the scene</span></span>

<span data-ttu-id="771b4-120">이 섹션에서는 자습서 프리팹 중 일부를 추가하여 장면을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-120">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="771b4-121">프로젝트 창에서 **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** 폴더로 이동한 후 다음과 같은 프리팹을 클릭하고 Hierarchy(계층 구조) 창으로 끌어서 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="771b4-122">**ButtonParent** 프리팹</span><span class="sxs-lookup"><span data-stu-id="771b4-122">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="771b4-123">**DebugWindow** 프리팹</span><span class="sxs-lookup"><span data-stu-id="771b4-123">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="771b4-124">**Instructions** 프리팹</span><span class="sxs-lookup"><span data-stu-id="771b4-124">**Instructions** prefabs</span></span>
* <span data-ttu-id="771b4-125">**ParentAnchor** 프리팹</span><span class="sxs-lookup"><span data-stu-id="771b4-125">**ParentAnchor** prefabs</span></span>

![새로 추가한 프리팹이 선택된 Unity](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="771b4-127">장면에 큰 아이콘(예: 방해가 되는 큰 틀의 'T' 아이콘)이 표시되는 경우 위 이미지와 같이 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos를 끄기 위치로 전환</a>하여 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-127">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

<span data-ttu-id="771b4-128">계층 구조 창에서 **MixedRealityToolkit** 개체를 선택하고, 검사기 창에서 **구성 요소 추가** 단추를 사용하여 다음 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-128">Select **MixedRealityToolkit** object in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="771b4-129">AR 앵커 관리자(스크립트)</span><span class="sxs-lookup"><span data-stu-id="771b4-129">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="771b4-130">DisableDiagnosticsSystem(스크립트)</span><span class="sxs-lookup"><span data-stu-id="771b4-130">DisableDiagnosticsSystem (Script)</span></span>

![<span data-ttu-id="771b4-131">AR Anchor Manager 및 DisableDiagnosticsSystem 구성 요소가 추가된 Unity MixedRealityToolkit 개체</span><span class="sxs-lookup"><span data-stu-id="771b4-131">Unity MixedRealityToolkit object with AR Anchor Manager and DisableDiagnosticsSystem components added</span></span> ](images/mr-learning-asa/asa-02-section4-step1-2.PNG)

> [!WARNING]
> <span data-ttu-id="771b4-132">ASA v2.9.0 및 v2.10.0-preview.1에는 두 개의 추가 개체를 장면에 배치해야 하는 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-132">There is a known issue with ASA v2.9.0 and v2.10.0-preview.1 that requires two additional objects to be placed in the scene.</span></span> <span data-ttu-id="771b4-133">속성 창에서 **구성 요소 추가** 단추를 사용하여 AR Camera Manager(스크립트) 및 AR Session(스크립트)을 **MixedRealityToolkit** 개체에 추가하세요.</span><span class="sxs-lookup"><span data-stu-id="771b4-133">Please use the **Add Component** button in the inspector window to add an AR Camera Manager (Script) and an AR Session (Script) to the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="771b4-134">검사기 창에서 카메라 개체 옆에 있는 확인란을 선택 해제하여 AR Camera Manager(스크립트)를 추가하는 동안 자동으로 생성되는 카메라를 사용하지 않도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-134">Be sure to disable the Camera that is created automatically while adding the AR Camera Manager (Script) by unchecking the checkbox next to the Camera object in the inspector window.</span></span> <span data-ttu-id="771b4-135">이 문제는 ASA v2.10.0의 전체 릴리스에서 해결될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-135">This issue will be addressed in the full release of ASA v2.10.0.</span></span>
> 

> [!NOTE]
> <span data-ttu-id="771b4-136">AR Anchor Manager(스크립트) 구성 요소를 추가하면 AR Session Origin(스크립트) 구성 요소가 AR Anchor Manager(스크립트) 구성 요소에 필요하기 때문에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-136">When you add the AR Anchor Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Anchor Manager (Script) component.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="771b4-137">장면을 작동하도록 단추 구성</span><span class="sxs-lookup"><span data-stu-id="771b4-137">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="771b4-138">이 섹션에서는 스크립트를 장면에 추가하여 로컬 앵커와 Azure Spatial Anchors가 앱에서 동작하는 방식에 대한 기본 사항을 보여 주는 일련의 단추 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-138">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="771b4-139">Hierarchy(계층 구조) 창에서 **ButtonParent** 개체를 펼쳐서 **StartAzureSession** 라는 첫 번째 자식 개체를 선택하고 Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-139">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="771b4-140">**ParentAnchor** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="771b4-140">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="771b4-141">**No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **StartAzureSession ()** 을 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="771b4-141">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![StartAzureSession 단추 OnClick 이벤트가 구성된 Unity](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="771b4-143">Hierarchy(계층 구조) 창에서 **StopAzureSession** 이라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-143">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="771b4-144">**ParentAnchor** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="771b4-144">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="771b4-145">**No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **StopAzureSession ()** 을 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="771b4-145">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![StopAzureSession 단추 OnClick 이벤트가 구성된 Unity](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="771b4-147">Hierarchy(계층 구조) 창에서 **CreateAzureAnchor** 라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-147">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="771b4-148">**ParentAnchor** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="771b4-148">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="771b4-149">**No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **CreateAzureAnchor ()** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="771b4-149">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="771b4-150">**ParentAnchor** 개체를 빈 **None (Game Object)** 필드에 할당하여 CreateAzureAnchor () 함수의 인수로 만들기</span><span class="sxs-lookup"><span data-stu-id="771b4-150">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![CreateAzureAnchor 단추 OnClick 이벤트가 구성된 Unity](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="771b4-152">Hierarchy(계층 구조) 창에서 **RemoveLocalAnchor** 라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-152">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="771b4-153">**ParentAnchor** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="771b4-153">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="771b4-154">**No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **RemoveLocalAnchor ()** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="771b4-154">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="771b4-155">**ParentAnchor** 개체를 빈 **None (Game Object)** 필드에 할당하여 RemoveLocalAnchor () 함수의 인수로 만들기</span><span class="sxs-lookup"><span data-stu-id="771b4-155">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![RemoveLocalAnchor 단추 OnClick 이벤트가 구성된 Unity](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="771b4-157">Hierarchy(계층 구조) 창에서 **FindAzureAnchor** 라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-157">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="771b4-158">**ParentAnchor** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="771b4-158">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="771b4-159">**No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **FindAzureAnchor ()** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="771b4-159">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![FindAzureAnchor 단추 OnClick 이벤트가 구성된 Unity](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="771b4-161">Hierarchy(계층 구조) 창에서 **DeleteAzureAnchor** 라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-161">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="771b4-162">**ParentAnchor** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="771b4-162">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="771b4-163">**No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **DeleteAzureAnchor ()** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="771b4-163">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![DeleteAzureAnchor 단추 OnClick 이벤트가 구성된 Unity](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="771b4-165">Azure 리소스에 장면 연결</span><span class="sxs-lookup"><span data-stu-id="771b4-165">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="771b4-166">Hierarchy(계층 구조) 창에서 **ParentAnchor** 개체를 선택하고, Inspector(인스펙터) 창에서 **Spatial Anchor Manager(스크립트)** 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-166">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="771b4-167">이 자습서 시리즈에서 [필수 구성 요소](mr-learning-asa-01.md#prerequisites)의 일부로 생성된 Azure Spatial Anchors 계정의 자격 증명을 사용하여 **Credentials** 섹션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-167">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="771b4-168">**Spatial Anchors Account ID** 필드에 Azure Spatial Anchors 계정의 **계정 ID** 를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-168">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="771b4-169">**Spatial Anchors Account Key** 필드에 Azure Spatial Anchors 계정의 기본 또는 보조 **액세스 키** 를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-169">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="771b4-170">**Spatial Anchors Account 도메인** 필드에 Azure Spatial Anchors 계정의 **계정 도메인** 을 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-170">In the **Spatial Anchors Account Domain** field, paste the **Account Domain** from your Azure Spatial Anchors account</span></span>

![Spatial Anchor Manager가 구성된 Unity](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="771b4-172">Azure Spatial Anchors의 기본 동작 사용해 보기</span><span class="sxs-lookup"><span data-stu-id="771b4-172">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="771b4-173">Azure Spatial Anchors는 Unity에서 실행할 수 없으므로 Azure Spatial Anchors 기능을 테스트하려면 프로젝트를 빌드하고 디바이스에 앱을 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-173">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="771b4-174">Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="771b4-174">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="771b4-175">앱이 디바이스에서 실행되는 경우 Azure Spatial Anchor 자습서 지침 패널에 표시되는 화면의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-175">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="771b4-176">큐브를 다른 위치로 이동</span><span class="sxs-lookup"><span data-stu-id="771b4-176">Move the cube to a different location</span></span>
2. <span data-ttu-id="771b4-177">Azure 세션 시작</span><span class="sxs-lookup"><span data-stu-id="771b4-177">Start Azure Session</span></span>
3. <span data-ttu-id="771b4-178">Azure 앵커 만들기(큐브의 위치에 앵커 만들기)</span><span class="sxs-lookup"><span data-stu-id="771b4-178">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
4. <span data-ttu-id="771b4-179">Azure 세션 중지</span><span class="sxs-lookup"><span data-stu-id="771b4-179">Stop Azure Session</span></span>
5. <span data-ttu-id="771b4-180">로컬 앵커 제거(사용자가 큐브를 이동할 수 있도록 허용)</span><span class="sxs-lookup"><span data-stu-id="771b4-180">Remove Local Anchor (allows the user to move the cube)</span></span>
6. <span data-ttu-id="771b4-181">큐브를 다른 곳으로 이동</span><span class="sxs-lookup"><span data-stu-id="771b4-181">Move the cube somewhere else</span></span>
7. <span data-ttu-id="771b4-182">Azure 세션 시작</span><span class="sxs-lookup"><span data-stu-id="771b4-182">Start Azure Session</span></span>
8. <span data-ttu-id="771b4-183">Azure 앵커 찾기(큐브를 3단계의 위치에 배치)</span><span class="sxs-lookup"><span data-stu-id="771b4-183">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
9. <span data-ttu-id="771b4-184">Azure 앵커 삭제</span><span class="sxs-lookup"><span data-stu-id="771b4-184">Delete Azure Anchor</span></span>
10. <span data-ttu-id="771b4-185">Azure 세션 중지</span><span class="sxs-lookup"><span data-stu-id="771b4-185">Stop Azure session</span></span>

![Instructions 개체가 선택된 Unity](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="771b4-187">Azure Spatial Anchors는 인터넷을 사용하여 앵커 데이터를 저장하고 로드하므로 디바이스가 인터넷에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-187">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="771b4-188">환경 고정</span><span class="sxs-lookup"><span data-stu-id="771b4-188">Anchoring an experience</span></span>

<span data-ttu-id="771b4-189">이전 섹션에서는 Azure Spatial Anchors의 기본 사항을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-189">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="771b4-190">큐브를 사용하여 연결된 앵커가 있는 부모 게임 개체를 표현하고 시각화했습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-190">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="771b4-191">이 섹션에서는 전체 환경을 ParentAnchor 개체의 자식 항목으로 배치하여 이 환경을 고정시키는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-191">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="771b4-192">Hierarchy(계층 구조) 창에서 **ParentAnchor** 개체를 선택하고, Inspector(인스펙터) 창에서 **Transform** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-192">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="771b4-193">**X 배율** 을 1.1로 변경</span><span class="sxs-lookup"><span data-stu-id="771b4-193">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="771b4-194">**Z 배율** 을 1.1로 변경</span><span class="sxs-lookup"><span data-stu-id="771b4-194">Change **Scale Z** to 1.1</span></span>

![ParentAnchor 개체가 선택되고 배치되고 크기 조정된 Unity](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="771b4-196">프로젝트 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** 폴더로 이동한 다음, **RoverExplorer_Complete** 프래팹을 클릭하여 Hierarchy(계층 구조) 창으로 끌어서 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-196">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![새로 추가된 RoverExplorer_Complete 프리팹이 선택된 Unity](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="771b4-198">Hierarchy(계층 구조) 창에 RoverModule_Complete 개체가 아직 선택되어 있으면 **ParentAnchor** 개체로 끌어서 ParentAnchor 개체의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-198">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![RoverExplorer_Complete 개체가 ParentAnchor의 자식으로 설정된 Unity](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="771b4-200">이제 프로젝트를 다시 빌드하고 디바이스에 앱을 배포하는 경우, 크기 조정된 큐브를 이동하여 전체 Rover Explorer 환경을 재배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-200">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="771b4-201">위치 변경 개체(예: 이 자습서에 사용된 큐브) 사용, 환경 주위의 경계 컨트롤을 해제/설정하는 단추 사용, 위치 및 회전 gizmos 사용 등을 포함하여 환경 위치 변경을 위한 다양한 사용자 환경 흐름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-201">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounds control that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="771b4-202">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-202">Congratulations</span></span>

<span data-ttu-id="771b4-203">이 자습서에서는 Azure Spatial Anchors의 기본 사항을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-203">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="771b4-204">이 자습서에는 Azure Spatial Anchors 세션을 시작 및 중지하는 데 필요한 다양한 단계를 살펴볼 수 있는 몇 가지 단추를 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-204">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="771b4-205">이를 통해 단일 디바이스에서 Azure Spatial Anchors를 생성, 업로드 및 다운로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-205">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="771b4-206">다음 자습서에서는 앱이 다시 시작된 후에도 검색을 위해 Azure 앵커 ID를 HoloLens 2에 저장하는 방법 및 여러 디바이스 간에 앵커 ID를 전송하여 공간 맞춤을 구현하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="771b4-206">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="771b4-207">다음 자습서: 3. Azure Spatial Anchors 저장, 검색 및 공유</span><span class="sxs-lookup"><span data-stu-id="771b4-207">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
