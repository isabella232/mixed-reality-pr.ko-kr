---
ms.openlocfilehash: 3bffb5db8f4a36d04c2b408c939cbd2010a7def7
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748459"
---
# <a name="mrtk"></a>[<span data-ttu-id="6b94b-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="6b94b-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="6b94b-102">Unity용 MRTK의 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 클래스를 사용하고 **대상 눈금을** **Seated로** 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-102">Use the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![MRTK 설정 창](../../images/mrtk-target-scale.png)

<span data-ttu-id="6b94b-104">MRTK는 재생 영역 및 카메라의 위치를 자동으로 처리해야 하지만 다음을 다시 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK 플레이스페이스](../../images/mrtk-playspace.png)

1. <span data-ttu-id="6b94b-106">**Hierarchy** 패널에서 **MixedRealityPlayspace** GameObject를 확장하고 **Main Camera** 자식 개체를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="6b94b-107">**검사기** 패널에서 **변환** 구성 요소를 찾아 **위치를** **(X: 0, Y: 0, Z: 0)으로** 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="6b94b-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="6b94b-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="6b94b-109">[XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)에서 추적 원본 모드를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="6b94b-110">하위 시스템을 가져온 후 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="6b94b-111">Unity의 [XRig 를 작업합니다.](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)</span><span class="sxs-lookup"><span data-stu-id="6b94b-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![계층 구조의 XR 조작](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="6b94b-113">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="6b94b-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="6b94b-114">Windows 스토어 플레이어 **설정의 기타 설정** **섹션으로** 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="6b94b-115">이전 버전의 Unity에서 **Windows Holographic으로** 나열될 수 있는 디바이스로 **Windows Mixed Reality** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="6b94b-116">**가상 현실 지원 선택**</span><span class="sxs-lookup"><span data-stu-id="6b94b-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="6b94b-117">Main Camera 개체는 자동으로 카메라로 태그가 지정되므로 Unity는 모든 이동 및 변환을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="6b94b-118">이러한 설정은 앱의 각 장면에서 카메라에 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="6b94b-119">기본적으로 Unity에서 새 장면을 만들 때 카메라 구성 요소를 포함하지만 아래 설정이 제대로 적용되지 않은 주 카메라 GameObject가 계층 구조에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="6b94b-120">**네임스페이스:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="6b94b-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="6b94b-121">**유형:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="6b94b-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="6b94b-122">**방향 전용** 또는 **좌표 크기 조정 환경을** 빌드하려면 Unity를 고정 추적 공간 형식으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="6b94b-123">고정 추적 공간은 Unity의 세계 좌표계를 설정하여 [고정 참조 프레임을](../../../../design/coordinate-systems.md#spatial-coordinate-systems)추적합니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="6b94b-124">고정 추적 모드에서는 앱이 시작되면 카메라의 기본 위치 바로 앞에 배치된 콘텐츠(정방향은 -Z)가 사용자 앞에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b94b-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="6b94b-125">**네임스페이스:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="6b94b-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="6b94b-126">**형식:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="6b94b-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="6b94b-127">360도 비디오 뷰어와 같은 순수 **방향 전용 환경의** 경우(위치 헤드 업데이트로 인해 현상이 악화되는 경우) XR을 설정할 수 [있습니다. InputTracking.disablePositionalTracking을](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) true로:</span><span class="sxs-lookup"><span data-stu-id="6b94b-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="6b94b-128">**사용자용 크기 조정 환경의** 경우 사용자가 나중에 착석 원점이 될 수 있도록 XR을 호출할 수 [있습니다. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 메서드:</span><span class="sxs-lookup"><span data-stu-id="6b94b-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="6b94b-129">[착석 규모 환경을](../../../../design/coordinate-systems.md)빌드하는 경우 XR을 호출하여 사용자의 현재 헤드 위치에서 Unity의 권역을 더 최근에 만들 수 **[있습니다. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 메서드.</span><span class="sxs-lookup"><span data-stu-id="6b94b-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>