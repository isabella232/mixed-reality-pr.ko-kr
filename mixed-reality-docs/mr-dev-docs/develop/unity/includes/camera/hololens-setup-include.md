---
ms.openlocfilehash: 6e751f5376110ddc6ae92c75b4182fba8240a356
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748489"
---
# <a name="mrtk"></a>[<span data-ttu-id="ff9ed-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="ff9ed-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="ff9ed-102">이 단계별 [자습서](../../tutorials/mr-learning-base-01.md) 에 따라 Unity 프로젝트에서 Mixed Reality Toolkit을 추가 하 고 자동으로 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-102">Follow this [step-by-step tutorial](../../tutorials/mr-learning-base-01.md) to add and automatically configure Mixed Reality Toolkit in your Unity project.</span></span> <span data-ttu-id="ff9ed-103">또한 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 클래스에서 Unity를 사용 하 여 직접 작업 하 고 **대상 규모** 를 **세계** 로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-103">It's also possible to work directly with the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **World**:</span></span>

![MRTK 설정 창](../../images/mrtk-target-scale.png)

<span data-ttu-id="ff9ed-105">MRTK는 플레이 공간 및 카메라의 위치를 자동으로 처리 해야 하지만 두 번 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-105">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="ff9ed-107">**계층** 패널에서 **MixedRealityPlayspace** GameObject를 확장 하 고 **기본 카메라** 자식 개체를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-107">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="ff9ed-108">**검사기** 패널에서 **변형** 구성 요소를 찾고 **위치** 를 **(X: 0, Y: 0, Z: 0)** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-108">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="ff9ed-109">XR SDK</span><span class="sxs-lookup"><span data-stu-id="ff9ed-109">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="ff9ed-110">[Xrinputsubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)에서 추적 원본 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-110">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="ff9ed-111">하위 시스템을 가져온 후 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-111">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

<span data-ttu-id="ff9ed-112">HoloLens 응용 프로그램에 대해 앵커 및 Arsession/Arsession에서 더 잘 작동 하는 [Arsession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) 을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-112">You can use [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) for HoloLens applications, which works better with anchors and ARKit/ARCore.</span></span>

![계층의 AR 세션](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> <span data-ttu-id="ff9ed-114">AR 세션 및 관련 기능에는 AR Foundation이 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-114">AR Session and related features need AR Foundation installed.</span></span>

<span data-ttu-id="ff9ed-115">ARSession을 사용 하지 않고 카메라 변경 내용을 수동으로 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-115">It's also possible to apply the camera changes manually without using ARSession:</span></span>

1. <span data-ttu-id="ff9ed-116">**계층** 패널에서 **주 카메라** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-116">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="ff9ed-117">**검사기** 패널에서 **변형** 구성 요소를 찾고 **위치** 를 **(X: 0, Y: 0, Z: 0)** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-117">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="ff9ed-118">![Unity의 검사기 창에 있는 카메라](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="ff9ed-118">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="ff9ed-119">*Unity의 검사기 창에 있는 카메라*</span><span class="sxs-lookup"><span data-stu-id="ff9ed-119">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="ff9ed-120">**기본 카메라** 에 **TrackedPoseDriver** 추가</span><span class="sxs-lookup"><span data-stu-id="ff9ed-120">Add a **TrackedPoseDriver** to the **Main Camera**</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="ff9ed-121">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="ff9ed-121">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="ff9ed-122">**계층** 패널에서 **주 카메라** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-122">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="ff9ed-123">**검사기** 패널에서 **변형** 구성 요소를 찾고 **위치** 를 **(X: 0, Y: 0, Z: 0)** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-123">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="ff9ed-124">![Unity의 검사기 창에 있는 카메라](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="ff9ed-124">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="ff9ed-125">*Unity의 검사기 창에 있는 카메라*</span><span class="sxs-lookup"><span data-stu-id="ff9ed-125">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="ff9ed-126">**Windows 스토어 플레이어 설정** 의 **기타 설정** 섹션으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-126">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
1. <span data-ttu-id="ff9ed-127">**Windows Mixed Reality** 를 장치로 선택 합니다 .이는 이전 버전의 Unity에서 **windows Holographic** 으로 나열 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-127">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
1. <span data-ttu-id="ff9ed-128">**지원 되는 가상 현실** 선택</span><span class="sxs-lookup"><span data-stu-id="ff9ed-128">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="ff9ed-129">기본 카메라 개체는 자동으로 카메라로 태그를 지정 하므로 Unity는 모든 이동 및 이동을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-129">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="ff9ed-130">이러한 설정은 앱의 각 장면에서 카메라에 적용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-130">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="ff9ed-131">기본적으로 Unity에서 새 장면을 만들 때 카메라 구성 요소를 포함 하는 계층의 기본 카메라 GameObject 포함 되지만 설정이 제대로 적용 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9ed-131">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but may not have the settings properly applied.</span></span>