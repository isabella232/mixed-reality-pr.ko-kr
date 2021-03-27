---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636378"
---
# <a name="mrtk"></a>[<span data-ttu-id="f4e2c-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="f4e2c-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="f4e2c-102">Unity 용 MRTK의 [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 클래스를 사용 하 고 **대상 소수 자릿수** 를 **다음** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![MRTK 설정 창](../../images/mrtk-target-scale.png)

<span data-ttu-id="f4e2c-104">MRTK는 플레이 공간 및 카메라의 위치를 자동으로 처리 해야 하지만 두 번 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="f4e2c-106">**계층** 패널에서 **MixedRealityPlayspace** GameObject를 확장 하 고 **기본 카메라** 자식 개체를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="f4e2c-107">**검사기** 패널에서 **변형** 구성 요소를 찾고 **위치** 를 **(X: 0, Y: 0, Z: 0)** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="f4e2c-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="f4e2c-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="f4e2c-109">[Xrinputsubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)에서 추적 원본 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="f4e2c-110">하위 시스템을 가져온 후 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="f4e2c-111">Unity의 [Xrrig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)를 사용 하 여 작업 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![계층의 XR rig](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="f4e2c-113">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="f4e2c-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="f4e2c-114">**Windows 스토어 플레이어 설정** 의 **기타 설정** 섹션으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="f4e2c-115">**Windows Mixed Reality** 를 장치로 선택 합니다 .이는 이전 버전의 Unity에서 **windows Holographic** 으로 나열 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="f4e2c-116">**지원 되는 가상 현실** 선택</span><span class="sxs-lookup"><span data-stu-id="f4e2c-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="f4e2c-117">기본 카메라 개체는 자동으로 카메라로 태그를 지정 하므로 Unity는 모든 이동 및 이동을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="f4e2c-118">이러한 설정은 앱의 각 장면에서 카메라에 적용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="f4e2c-119">기본적으로 Unity에서 새 장면을 만들 때 카메라 구성 요소를 포함 하는 계층의 기본 카메라 GameObject가 포함 되지만, 아래에는 설정이 제대로 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="f4e2c-120">**네임 스페이스:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="f4e2c-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="f4e2c-121">**유형:** *xrdevice*</span><span class="sxs-lookup"><span data-stu-id="f4e2c-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="f4e2c-122">**방향 전용** 또는 통합 된 **환경을** 구축 하려면 Unity를 고정 된 추적 공간 형식으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="f4e2c-123">고정 된 추적 공간에서는 Unity의 세계 좌표 시스템을 설정 하 여 [고정 된 참조 프레임](../../../../design/coordinate-systems.md#spatial-coordinate-systems)을 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="f4e2c-124">고정 추적 모드에서 카메라의 기본 위치 바로 앞에 있는 편집기에 배치 된 콘텐츠 (앞으로-Z)는 앱이 시작 될 때 사용자 앞에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="f4e2c-125">**네임 스페이스:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="f4e2c-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="f4e2c-126">**형식:** *inputtracking*</span><span class="sxs-lookup"><span data-stu-id="f4e2c-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="f4e2c-127">360도 비디오 뷰어 (위치 헤드 업데이트에서 환상 효과를 ruin)와 같은 순수한 **방향 전용 환경** 에서는 XR를 설정할 수 있습니다 [. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) 을 true로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e2c-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="f4e2c-128">사용자가 나중에 연결 된 원본을 recenter 할 수 있도록 하는 **확장 된 환경의** 경우 XR를 호출할 수 있습니다 [. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 메서드:</span><span class="sxs-lookup"><span data-stu-id="f4e2c-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="f4e2c-129">통합 된 [환경을](../../../../design/coordinate-systems.md)구축 하는 경우 XR를 호출 하 여 사용자의 현재 헤드 위치에서 Unity의 세계 원본을 recenter 수 있습니다 **[. Recenter 메서드입니다.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)**</span><span class="sxs-lookup"><span data-stu-id="f4e2c-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>