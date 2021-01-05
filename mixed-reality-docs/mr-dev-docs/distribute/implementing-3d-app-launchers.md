---
title: 3D 앱 시작 관리자(UWP 앱) 구현
description: HoloLens 및 모던 (VR) 헤드셋 모두에서 Windows Mixed Reality UWP 앱 및 게임 (Microsoft Store을 통해 배포)에 대 한 3D 앱 다운로드 및 로고를 만드는 방법입니다.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, 로고, 아이콘, 모델링, 시작 관리자, 3D 시작 관리자, 타일, 라이브 큐브, 딥 링크, secondarytile, 보조 타일, UWP, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, XML, 경계 상자, unity
ms.openlocfilehash: 38f0932f20e3660c91b87de7bcb9d66799d9a51a
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757500"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="b3431-104">3D 앱 시작 관리자(UWP 앱) 구현</span><span class="sxs-lookup"><span data-stu-id="b3431-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="b3431-105">이 기능은 몰입 형 헤드셋에 대해 RS3 (2017) 크리에이터 업데이트의 일부로 추가 되었으며 Windows 10 4 월 2018 업데이트를 사용 하 여 HoloLens에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="b3431-106">응용 프로그램이 10.0.16299의 버전을 대상으로 하는 Windows SDK의 버전을 대상으로 하는 작업을 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="b3431-107">[여기](https://developer.microsoft.com/windows/downloads/windows-10-sdk)에서 최신 Windows SDK를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="b3431-108">[Windows Mixed Reality 홈](../discover/navigating-the-windows-mixed-reality-home.md) 은 사용자가 응용 프로그램을 시작 하기 전에 수행 하는 시작 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-108">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="b3431-109">Windows Mixed Reality 용 UWP 응용 프로그램을 만들 때 기본적으로 앱은 앱 로고를 사용 하 여 2D 슬레이트 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="b3431-110">Windows Mixed Reality 환경을 개발 하는 경우 응용 프로그램의 기본 2D 시작 관리자를 재정의 하도록 3D 시작 관리자를 선택적으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="b3431-111">일반적으로 Windows Mixed Reality 홈에서 사용자를 제외 하는 몰입 형 응용 프로그램을 시작 하려면 3D 시작을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home.</span></span> <span data-ttu-id="b3431-112">앱이 현재 활성화 된 경우 기본 2D 시작 관리자가 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-112">The default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="b3431-113">[3d 딥 링크 (secondaryTile)](#3d-deep-links-secondarytiles) 를 2d UWP 앱 내 콘텐츠의 3d 시작 관리자로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-113">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="b3431-114">3D 앱 시작 관리자 만들기 프로세스</span><span class="sxs-lookup"><span data-stu-id="b3431-114">3D app launcher creation process</span></span>

<span data-ttu-id="b3431-115">3D 앱 시작 관리자를 만드는 세 가지 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-115">There are three steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="b3431-116">디자인 및 concepting</span><span class="sxs-lookup"><span data-stu-id="b3431-116">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="b3431-117">모델링 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="b3431-117">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="b3431-118">응용 프로그램에 통합 (이 문서)</span><span class="sxs-lookup"><span data-stu-id="b3431-118">Integrating it into your application (this article)</span></span>

<span data-ttu-id="b3431-119">응용 프로그램에 대 한 관리자로 사용할 3D 자산은 호환성을 보장 하기 위해 [Windows Mixed Reality 제작 지침](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 을 사용 하 여 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-119">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="b3431-120">이 제작 사양을 충족 하지 못하는 자산은 Windows Mixed Reality 홈에서 렌더링 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-120">Assets that fail to meet this authoring specification won't be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="b3431-121">3D 시작 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="b3431-121">Configuring the 3D launcher</span></span>

<span data-ttu-id="b3431-122">Visual Studio에서 새 프로젝트를 만들면 앱의 이름과 로고가 표시 되는 간단한 기본 타일이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-122">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="b3431-123">이 2D 표현을 사용자 지정 3D 모델로 바꾸려면 "MixedRealityModel" 요소를 기본 타일 정의의 일부로 포함 하도록 응용 프로그램의 응용 프로그램 매니페스트를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-123">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="b3431-124">2D 시작 관리자로 되돌리려면 매니페스트에서 MixedRealityModel 정의를 제거 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-124">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="b3431-125">XML</span><span class="sxs-lookup"><span data-stu-id="b3431-125">XML</span></span>

<span data-ttu-id="b3431-126">먼저 현재 프로젝트에서 앱 패키지 매니페스트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-126">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="b3431-127">기본적으로 매니페스트는 appxmanifest.xml로 이름이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-127">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="b3431-128">Visual Studio를 사용 하는 경우 솔루션 뷰어에서 매니페스트를 마우스 오른쪽 단추로 클릭 하 고 **소스 보기** 를 선택 하 여 편집을 위해 xml을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-128">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="b3431-129">매니페스트 위쪽에서 uap5 스키마를 추가 하 고이를 무시할 수 있는 네임 스페이스로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-129">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="b3431-130">다음으로 응용 프로그램의 기본 타일에서 "MixedRealityModel"를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-130">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

<span data-ttu-id="b3431-131">MixedRealityModel 요소는 응용 프로그램 패키지에 저장 된 3D 자산을 가리키는 파일 경로를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-131">The MixedRealityModel element accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="b3431-132">현재는 .bb 파일 형식을 사용 하 여 전달 되 고 [Windows Mixed Reality 3d 자산 제작 지침](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 에 따라 작성 된 3d 모델만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-132">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="b3431-133">자산은 앱 패키지에 저장 되어야 하 고 애니메이션은 현재 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-133">Assets must be stored in the app package and animation isn't currently supported.</span></span> <span data-ttu-id="b3431-134">"Path" 매개 변수를 비워 두면 Windows에서 3D 시작 관리자 대신 2D 슬레이트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-134">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="b3431-135">**참고:** 응용 프로그램을 빌드하고 실행 하기 전에 빌드 설정에서 .bb 자산을 "콘텐츠"로 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-135">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="b3431-136">![솔루션 탐색기에서. a s b를 선택 하 고 속성 섹션을 사용 하 여 빌드 설정에서 "콘텐츠"로 표시 합니다.](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="b3431-136">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="b3431-137">*솔루션 탐색기에서. a s b를 선택 하 고 속성 섹션을 사용 하 여 빌드 설정에서 "콘텐츠"로 표시 합니다.*</span><span class="sxs-lookup"><span data-stu-id="b3431-137">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="b3431-138">경계 상자</span><span class="sxs-lookup"><span data-stu-id="b3431-138">Bounding box</span></span>

<span data-ttu-id="b3431-139">경계 상자는 개체 주위에 추가 버퍼 영역을 선택적으로 추가 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-139">A bounding box can be used to optionally add an extra buffer region around the object.</span></span> <span data-ttu-id="b3431-140">경계 상자는 중심점 및 범위를 사용 하 여 지정 됩니다 .이 범위는 경계 상자 중심에서 각 축의 가장자리 까지의 거리를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-140">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="b3431-141">경계 상자의 단위는 1 단위 = 1 미터에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-141">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="b3431-142">경계 상자를 제공 하지 않으면 개체의 메시에 자동으로 조정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-142">If a bounding box isn't provided, then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="b3431-143">제공 된 경계 상자가 모델 보다 작으면 망상에 맞게 크기가 조정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-143">If the provided bounding box is smaller than the model, then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="b3431-144">경계 상자 특성에 대 한 지원은 Windows RS4 update와 함께 MixedRealityModel 요소에 대 한 속성으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-144">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="b3431-145">응용 프로그램 매니페스트 맨 위에 있는 경계 상자를 먼저 정의 하려면 uap6 스키마를 추가 하 고이를 무시할 수 있는 네임 스페이스로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-145">To define a bounding box first at the top of the app manifest add the uap6 schema and include it as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="b3431-146">그런 다음 MixedRealityModel에서 SpatialBoundingBox 속성을 설정 하 여 경계 상자를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-146">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="b3431-147">Unity 사용</span><span class="sxs-lookup"><span data-stu-id="b3431-147">Using Unity</span></span>

<span data-ttu-id="b3431-148">Unity를 사용 하는 경우 응용 프로그램 매니페스트를 편집 하려면 먼저 Visual Studio에서 프로젝트를 빌드하고 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-148">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="b3431-149">Unity에서 새 Visual Studio 솔루션을 빌드 및 배포 하는 경우 매니페스트에서 3D 시작 관리자를 다시 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-149">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="b3431-150">3D 딥 링크 (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="b3431-150">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="b3431-151">이 기능은 모던 용 2017 RS3 (RS4) 헤드셋의 일부로 추가 되었으며 HoloLens 용 (4 월 2018 업데이트)의 일부로 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-151">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="b3431-152">응용 프로그램이 10.0.16299 on 모던 (VR) 헤드셋 및 10.0.17125의 버전을 대상으로 하는 Windows SDK 버전을 대상으로 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-152">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="b3431-153">[여기](https://developer.microsoft.com/windows/downloads/windows-10-sdk)에서 최신 Windows SDK를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-153">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="b3431-154">3D 딥 링크 (secondaryTiles)는 2D UWP 앱 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-154">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="b3431-155">그러나 Windows Mixed Reality 홈에서 전용 앱을 시작 하는 [3d 앱 시작 관리자](implementing-3d-app-launchers.md) 를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-155">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="b3431-156">Windows 시작 메뉴의 2d [보조 타일과](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) 마찬가지로, 응용 프로그램의 3d 모델을 [windows mixed reality 홈](../discover/navigating-the-windows-mixed-reality-home.md) 에 포함 하는 기능을 추가 하 여 windows mixed reality에 2d 응용 프로그램을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-156">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="b3431-157">예를 들어 360 ° photo viewer 앱에 직접 연결 되는 360 ° 인화지를 만들거나, 사용자가 저자에 대 한 세부 정보 페이지를 여는 자산 컬렉션에서 3D 콘텐츠를 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-157">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="b3431-158">3D 콘텐츠를 사용 하 여 2D 응용 프로그램의 기능을 확장 하는 몇 가지 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-158">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="b3431-159">3D "secondaryTile" 만들기</span><span class="sxs-lookup"><span data-stu-id="b3431-159">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="b3431-160">만들 때 혼합 현실 모델을 정의 하 여 "secondaryTiles"을 사용 하 여 응용 프로그램의 3D 콘텐츠를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-160">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="b3431-161">혼합 현실 모델은 앱 패키지에서 3D 자산을 참조 하 고 필요에 따라 경계 상자를 정의 하 여 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-161">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="b3431-162">단독 보기 내에서 "secondaryTiles" 만들기는 현재 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-162">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a><span data-ttu-id="b3431-163">경계 상자</span><span class="sxs-lookup"><span data-stu-id="b3431-163">Bounding box</span></span>

<span data-ttu-id="b3431-164">경계 상자는 개체 주위에 추가 버퍼 영역을 추가 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-164">A bounding box can be used to add an extra buffer region around the object.</span></span> <span data-ttu-id="b3431-165">경계 상자는 중심점 및 범위를 사용 하 여 지정 됩니다 .이 범위는 경계 상자 중심에서 각 축의 가장자리 까지의 거리를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-165">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="b3431-166">경계 상자의 단위는 1 단위 = 1 미터에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-166">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="b3431-167">경계 상자를 제공 하지 않으면 개체의 메시에 자동으로 조정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-167">If a bounding box isn't provided, one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="b3431-168">제공 된 경계 상자가 모델 보다 작으면 망상에 맞게 크기가 조정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-168">If the provided bounding box is smaller than the model, it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="b3431-169">활성화 동작</span><span class="sxs-lookup"><span data-stu-id="b3431-169">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="b3431-170">이 기능은 Windows RS4 업데이트를 통해 지원 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-170">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="b3431-171">이 기능을 사용 하려는 경우 응용 프로그램이 10.0.17125 이상 Windows SDK 버전을 대상으로 하 고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-171">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="b3431-172">3D secondaryTile의 활성화 동작을 정의 하 여 사용자가 선택할 때 반응 하는 방식을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-172">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="b3431-173">이는 순수 하 게 정보를 제공 하거나 장식 하는 혼합 현실 홈에 3D 개체를 저장 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-173">This can be used to place 3D objects in the Mixed Reality home that are purely informative or decorative.</span></span> <span data-ttu-id="b3431-174">다음 활성화 동작 유형이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-174">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="b3431-175">기본값: 사용자가 3D secondaryTile을 선택 하면 앱이 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-175">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="b3431-176">없음: 사용자가 3D secondaryTile을 선택 하면 아무 작업도 수행 되지 않으며 앱이 활성화 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-176">None: When the user selects the 3D secondaryTile nothing happens and the app isn't activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="b3431-177">기존 "secondaryTile" 가져오기 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="b3431-177">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="b3431-178">개발자는 이전에 지정한 속성을 포함 하 여 기존 보조 타일의 목록을 다시 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-178">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="b3431-179">값을 변경한 다음 UpdateAsync ()를 호출 하 여 속성을 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-179">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="b3431-180">사용자가 Windows Mixed Reality에 있는지 확인 하는 중</span><span class="sxs-lookup"><span data-stu-id="b3431-180">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="b3431-181">3D 딥 링크 (secondaryTiles)는 보기가 Windows Mixed Reality 헤드셋에 표시 되는 동안에만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-181">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="b3431-182">Windows Mixed Reality 헤드셋에 보기가 표시 되지 않는 경우 진입점을 숨기 거 나 오류 메시지를 표시 하 여이를 정상적으로 처리 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-182">When your view isn't being presented in a Windows Mixed Reality headset, we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="b3431-183">[IsCurrentViewPresentedOnHolographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)를 쿼리하여이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-183">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="b3431-184">타일 알림</span><span class="sxs-lookup"><span data-stu-id="b3431-184">Tile notifications</span></span>

<span data-ttu-id="b3431-185">타일 알림은 현재 3D 자산과 함께 업데이트를 전송 하는 것을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-185">Tile notifications don't currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="b3431-186">즉, 개발자가 다음을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-186">This means that developers can't do the following:</span></span>

* <span data-ttu-id="b3431-187">푸시 알림</span><span class="sxs-lookup"><span data-stu-id="b3431-187">Push Notifications</span></span>
* <span data-ttu-id="b3431-188">정기적 폴링</span><span class="sxs-lookup"><span data-stu-id="b3431-188">Periodic Polling</span></span>
* <span data-ttu-id="b3431-189">예약 된 알림</span><span class="sxs-lookup"><span data-stu-id="b3431-189">Scheduled Notifications</span></span>

<span data-ttu-id="b3431-190">다른 타일 기능 및 특성과 2D 타일에 사용 되는 방법에 대 한 자세한 내용은 [UWP 앱에 대 한 타일 설명서](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b3431-190">For more information on the other tiles features and attributes and how they're used for 2D tiles, see the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3431-191">추가 정보</span><span class="sxs-lookup"><span data-stu-id="b3431-191">See also</span></span>

* <span data-ttu-id="b3431-192">3D 앱 시작 관리자를 포함 하는 [혼합 현실 모델 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) 입니다.</span><span class="sxs-lookup"><span data-stu-id="b3431-192">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="b3431-193">3D 앱 시작 관리자 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="b3431-193">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="b3431-194">Windows Mixed Reality 홈에서 사용할 3D 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="b3431-194">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="b3431-195">3D 앱 응용 프로그램 구현 (Win32 앱)</span><span class="sxs-lookup"><span data-stu-id="b3431-195">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="b3431-196">Windows Mixed Reality 홈 탐색</span><span class="sxs-lookup"><span data-stu-id="b3431-196">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
