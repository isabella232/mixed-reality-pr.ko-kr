---
ms.openlocfilehash: 5f990569ae4052377cba717b5526bb8ba51b8016
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636385"
---
# <a name="mrtk"></a>[<span data-ttu-id="f95dc-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="f95dc-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="f95dc-102">[MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 클래스를 사용 하 여 Unity에서 MRTK를 사용 하 고 **대상 크기** 를 방 **또는 서** 로 설정 합니다. </span><span class="sxs-lookup"><span data-stu-id="f95dc-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to either **Room** or **Standing**:</span></span>

![MRTK 설정 창](../../images/mrtk-target-scale.png)

<span data-ttu-id="f95dc-104">MRTK는 플레이 공간 및 카메라의 위치를 자동으로 처리 해야 하지만 두 번 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="f95dc-106">**계층** 패널에서 **MixedRealityPlayspace** GameObject를 확장 하 고 **기본 카메라** 자식 개체를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="f95dc-107">**검사기** 패널에서 **변형** 구성 요소를 찾고 **위치** 를 **(X: 0, Y: 0, Z: 0)** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="f95dc-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="f95dc-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="f95dc-109">[Xrinputsubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)에서 추적 원본 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="f95dc-110">하위 시스템을 가져온 후 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

<span data-ttu-id="f95dc-111">Unity의 [Xrrig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)를 사용 하 여 작업 합니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![계층의 XR rig](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="f95dc-113">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="f95dc-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="f95dc-114">**Windows 스토어 플레이어 설정** 의 **기타 설정** 섹션으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="f95dc-115">**Windows Mixed Reality** 를 장치로 선택 합니다 .이는 이전 버전의 Unity에서 **windows Holographic** 으로 나열 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="f95dc-116">**지원 되는 가상 현실** 선택</span><span class="sxs-lookup"><span data-stu-id="f95dc-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="f95dc-117">기본 카메라 개체는 자동으로 카메라로 태그를 지정 하므로 Unity는 모든 이동 및 이동을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="f95dc-118">이러한 설정은 앱의 각 장면에서 카메라에 적용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="f95dc-119">기본적으로 Unity에서 새 장면을 만들 때 카메라 구성 요소를 포함 하는 계층의 기본 카메라 GameObject가 포함 되지만, 아래에는 설정이 제대로 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="f95dc-120">**네임 스페이스:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="f95dc-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="f95dc-121">**유형:** *xrdevice*</span><span class="sxs-lookup"><span data-stu-id="f95dc-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="f95dc-122">**대규모 또는** **공간 규모의 경험** 을 위해 바닥을 기준으로 콘텐츠를 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-122">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="f95dc-123">사용자의 층을 사용 하는 이유는 사용자의 정의 된 최고 수준 원점 및 선택적 대화방 경계를 나타내는 **[공간 단계](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** 를 처음 실행 하는 동안 설정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-123">You reason about the user's floor using the **[spatial stage](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="f95dc-124">Unity가 최고 좌표계로 작동 하는지 확인 하기 위해 RoomScale 추적 공간 유형을 사용 하 여 Unity를 설정 하 고 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-124">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

* <span data-ttu-id="f95dc-125">SetTrackingSpaceType가 true를 반환 하는 경우 Unity는 세계 좌표계를 정상적으로 전환 하 여 [참조의 스테이지 프레임](../../../../design/coordinate-systems.md#spatial-coordinate-systems)을 추적 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-125">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="f95dc-126">SetTrackingSpaceType가 false를 반환 하는 경우 Unity는 사용자의 환경에서 바닥을 설정 하지 않았기 때문에 참조의 스테이지 프레임으로 전환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-126">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="f95dc-127">False 반환 값은 일반적이 지 않지만 다른 방에 단계를 설정 하 고 사용자가 새 단계를 설정 하지 않은 상태에서 현재 대화방으로 장치를 이동 하는 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-127">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="f95dc-128">앱이 RoomScale 추적 공간 유형을 성공적으로 설정 하면 y = 0 평면에 배치 된 콘텐츠가 바닥에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f95dc-128">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="f95dc-129">0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 구현</span><span class="sxs-lookup"><span data-stu-id="f95dc-129">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>