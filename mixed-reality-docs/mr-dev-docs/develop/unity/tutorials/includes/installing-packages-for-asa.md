---
ms.openlocfilehash: 0a89ef77bee7eff83d4599c46ffd2681c99b2165
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175574"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="33af5-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="33af5-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="33af5-102">Unity 메뉴에서 **창** > **패키지 관리자** 를 선택하여 패키지 관리자 창을 연 다음 **AR Foundation** > **4.1.7** 버전이 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="33af5-102">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then verify that **AR Foundation** > **4.1.7** version is installed.</span></span>

![AR Foundation이 선택된 Unity Package Manager](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="33af5-104">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="33af5-104">Importing the tutorial assets</span></span>

<span data-ttu-id="33af5-105">AzurespatialAnchors SDK V2.10을 프로젝트에 추가합니다. 패키지를 추가하려면 이 [자습서](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="33af5-105">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="33af5-106">다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.</span><span class="sxs-lookup"><span data-stu-id="33af5-106">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="33af5-107">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="33af5-107">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="33af5-108">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="33af5-108">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

<span data-ttu-id="33af5-109">자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33af5-109">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![자습서 자산을 가져온 후의 Unity 계층 구조, 장면 및 프로젝트 창](../images/mr-learning-asa/asa-02-section3-step1-2-OpenXR.png)

> [!TIP]
> <span data-ttu-id="33af5-111">Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면  [자습서 자산 가져오기](../mr-learning-base-04.md#importing-the-tutorial-assets)  지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33af5-111">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="unity-2020--windows-xr-plugin"></a>[<span data-ttu-id="33af5-112">Unity 2020 + Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="33af5-112">Unity 2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="33af5-113">Unity 메뉴에서 **창** > **패키지 관리자** 를 차례로 선택하여 패키지 관리자 창을 연 다음, **AR Foundation > 4.0.12** 버전을 선택하고, **설치** 단추를 클릭하여 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="33af5-113">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 4.0.12** version and click the **Install** button to install the package:</span></span>

![AR Foundation이 선택된 Unity Package Manager](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="33af5-115">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="33af5-115">Importing the tutorial assets</span></span>

<span data-ttu-id="33af5-116">AzurespatialAnchors SDK V2.10을 프로젝트에 추가합니다. 패키지를 추가하려면 이 [자습서](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="33af5-116">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="33af5-117">다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.</span><span class="sxs-lookup"><span data-stu-id="33af5-117">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="33af5-118">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="33af5-118">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="33af5-119">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="33af5-119">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

<span data-ttu-id="33af5-120">자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33af5-120">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![자습서 자산을 가져온 후의 Unity 계층 구조, 장면 및 프로젝트 창](../images/mr-learning-asa/asa-02-section3-step1-2-XRSDK.PNG)

> [!TIP]
> <span data-ttu-id="33af5-122">Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면  [자습서 자산 가져오기](../mr-learning-base-04.md#importing-the-tutorial-assets)  지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33af5-122">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="33af5-123">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="33af5-123">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="33af5-124">Unity 메뉴에서 **창** > **패키지 관리자** 를 차례로 선택하여 패키지 관리자 창을 연 다음, **AR Foundation > 3.1.3** 버전을 선택하고, **설치** 단추를 클릭하여 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="33af5-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 3.1.3** version and click the **Install** button to install the package:</span></span>

![AR Foundation이 선택된 Unity Package Manager](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="33af5-126">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="33af5-126">Importing the tutorial assets</span></span>

<span data-ttu-id="33af5-127">AzurespatialAnchors SDK V2.7.2를 Unity 프로젝트에 추가합니다. 패키지를 추가하려면 이 [자습서](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="33af5-127">Add AzurespatialAnchors SDK V2.7.2 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="33af5-128">다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.</span><span class="sxs-lookup"><span data-stu-id="33af5-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="33af5-129">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="33af5-129">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="33af5-130">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="33af5-130">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage)

<span data-ttu-id="33af5-131">자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33af5-131">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![자습서 자산을 가져온 후의 Unity 계층 구조, 장면 및 프로젝트 창](../images/mr-learning-asa/asa-02-section3-step1-2-Legacy.png)

> [!NOTE]
> <span data-ttu-id="33af5-133">더 이상 사용되지 않는 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)'과 관련된 CS0618 경고가 표시되는 경우 이러한 경고를 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33af5-133">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' is obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="33af5-134">Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면  [자습서 자산 가져오기](../mr-learning-base-04.md#importing-the-tutorial-assets)  지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33af5-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>
