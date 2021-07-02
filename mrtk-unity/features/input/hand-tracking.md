---
title: 손 추적
description: MRTK에서 HandTracking을 사용하는 방법에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 손 추적,
ms.openlocfilehash: 68e936cb4121027008f37aae72496fe59445b636
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176895"
---
# <a name="hand-tracking"></a><span data-ttu-id="4af11-104">손 추적</span><span class="sxs-lookup"><span data-stu-id="4af11-104">Hand tracking</span></span>

## <a name="hand-tracking-profile"></a><span data-ttu-id="4af11-105">손 추적 프로필</span><span class="sxs-lookup"><span data-stu-id="4af11-105">Hand tracking profile</span></span>

<span data-ttu-id="4af11-106">_손 추적 프로필은_ _입력 시스템 프로필_ 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-106">The _Hand Tracking profile_ is found under the _Input System profile_.</span></span> <span data-ttu-id="4af11-107">여기에는 손 표현을 사용자 지정하기 위한 설정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-107">It contains settings for customizing hand representation.</span></span>

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a><span data-ttu-id="4af11-108">공동 프리팹</span><span class="sxs-lookup"><span data-stu-id="4af11-108">Joint prefabs</span></span>

<span data-ttu-id="4af11-109">공동 프리팹은 간단한 프리팹을 사용하여 시각화됩니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-109">Joint prefabs are visualized using simple prefabs.</span></span> <span data-ttu-id="4af11-110">_손끝_ 및 _인덱스 손가락_ 조인은 매우 중요하며 자체 프리팹이 있지만 다른 모든 조인은 동일한 프리팹을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-110">The _Palm_ and _Index Finger_ joints are of special importance and have their own prefab, while all other joints share the same prefab.</span></span>

<span data-ttu-id="4af11-111">기본적으로 손 결합 프리팹은 간단한 기하학적 기본 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-111">By default the hand joint prefabs are simple geometric primitives.</span></span> <span data-ttu-id="4af11-112">원하는 경우 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-112">These can be replaced if desired.</span></span> <span data-ttu-id="4af11-113">프리팹을 전혀 지정하지 않으면 빈 [GameObjects가](https://docs.unity3d.com/ScriptReference/GameObject.html) 대신 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-113">If no prefab is specified at all, empty [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) are created instead.</span></span>

> [!WARNING]
> <span data-ttu-id="4af11-114">조인 개체는 모든 프레임에서 변환되고 상당한 성능 비용이 들 수 있기 때문에 복잡한 스크립트를 사용하거나 공동 프리팹에서 비용이 많이 드는 렌더링을 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="4af11-114">Avoid using complex scripts or expensive rendering in joint prefabs, since joint objects are transformed on every frame and can have significant performance cost!</span></span>

<span data-ttu-id="4af11-115">기본 손 공동 표현</span><span class="sxs-lookup"><span data-stu-id="4af11-115">Default Hand Joint Representation</span></span> |  <span data-ttu-id="4af11-116">공동 레이블</span><span class="sxs-lookup"><span data-stu-id="4af11-116">Joint Labels</span></span>
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a><span data-ttu-id="4af11-117">손 메시 프리팹</span><span class="sxs-lookup"><span data-stu-id="4af11-117">Hand mesh prefab</span></span>

<span data-ttu-id="4af11-118">손 메시는 손 추적 디바이스에서 완전히 정의된 메시 데이터를 제공하는 경우에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-118">The hand mesh is used if fully defined mesh data is provided by the hand tracking device.</span></span> <span data-ttu-id="4af11-119">프리팹에서 렌더링 가능한 메시는 디바이스의 데이터로 대체되므로 큐브와 같은 더미 메시로 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-119">The mesh renderable in the prefab is replaced by data from the device, so a dummy mesh such as a cube is sufficient.</span></span> <span data-ttu-id="4af11-120">프리팹의 재질은 손 메시에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-120">The material of the prefab is used for the hand mesh.</span></span>

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

<span data-ttu-id="4af11-121">손 메시 표시는 성능에 상당한 영향을 줄 수 있습니다. 이러한 이유로 **손 메시 시각화 사용** 옵션을 선택 취소하여 완전히 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-121">Hand mesh display can have a noticeable performance impact, for this reason it can be disabled entirely by unchecking **Enable Hand Mesh Visualization** option.</span></span>

## <a name="hand-visualization-settings"></a><span data-ttu-id="4af11-122">손 시각화 설정</span><span class="sxs-lookup"><span data-stu-id="4af11-122">Hand visualization settings</span></span>

<span data-ttu-id="4af11-123">손 메시 및 손 조인트 시각화는 각각 손 메시 시각화 모드 설정 및 손 공동 *시각화 모드를* 통해 해제하거나 끌 수 *있습니다.*</span><span class="sxs-lookup"><span data-stu-id="4af11-123">The hand mesh and hand joint visualizations can be turned off or on via the *Hand Mesh Visualization Modes* setting and *Hand Joint Visualization Modes* respectively.</span></span> <span data-ttu-id="4af11-124">이러한 설정은 애플리케이션 모드에 따라 다릅니다. 즉, 디바이스에 배포할 때(플레이어 빌드에서) 동일한 기능을 해제하면서 편집기에서 일부 기능을 켤 수 있습니다(예: 편집기 내 시뮬레이션과의 조인 확인).</span><span class="sxs-lookup"><span data-stu-id="4af11-124">These settings are application-mode specific, meaning it is possible to turn on some features while in editor (to see joints with in-editor simulation, for example) while having the same features turned off when deployed to device (in player builds).</span></span>

<span data-ttu-id="4af11-125">일반적으로 편집기에서 손 조인트 시각화를 켜고(편집기 내 시뮬레이션에서 손 조인트의 위치를 표시함) 플레이어에서 손 조인트 시각화와 손 메시 시각화를 모두 해제하는 것이 좋습니다(성능 저하가 발생하므로).</span><span class="sxs-lookup"><span data-stu-id="4af11-125">Note that it's generally recommended to have hand joint visualization turned on in editor (so that in-editor simulation will show where the hand joints are), and to have both hand joint visualization and hand mesh visualization turned off in player (because they incur a performance hit).</span></span>

## <a name="scripting"></a><span data-ttu-id="4af11-126">스크립팅</span><span class="sxs-lookup"><span data-stu-id="4af11-126">Scripting</span></span>

<span data-ttu-id="4af11-127">위치 및 회전으로 각 개별 손 조인에 대 한 입력 시스템에서 요청할 수 있습니다 [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-127">Position and rotation can be requested from the input system for each individual hand joint as a [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="4af11-128">또는 시스템에서 조인트 뒤에 있는 [GameObject에](https://docs.unity3d.com/ScriptReference/GameObject.html) 대한 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-128">Alternatively the system allows access to [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) that follow the joints.</span></span> <span data-ttu-id="4af11-129">이는 다른 GameObject가 공동을 지속적으로 추적해야 하는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-129">This can be useful if another GameObject should track a joint continuously.</span></span>

<span data-ttu-id="4af11-130">사용 가능한 조인은 [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) 열거형에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-130">Available joints are listed in the [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enum.</span></span>

> [!NOTE]
> <span data-ttu-id="4af11-131">손 추적이 손실되면 공동 개체가 소멸됩니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-131">Joint object are destroyed when hand tracking is lost!</span></span> <span data-ttu-id="4af11-132">오류를 방지하기 위해 공동 개체를 사용하는 모든 스크립트가 `null` 대/소문자를 정상적으로 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-132">Make sure that any scripts using the joint object handle the `null` case gracefully to avoid errors!</span></span>

### <a name="accessing-a-given-hand-controller"></a><span data-ttu-id="4af11-133">지정된 손 컨트롤러 액세스</span><span class="sxs-lookup"><span data-stu-id="4af11-133">Accessing a given hand controller</span></span>

<span data-ttu-id="4af11-134">입력 이벤트를 처리할 때와 같은 특정 손 컨트롤러를 사용할 수 있는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-134">A specific hand controller is often available, e.g. when handling input events.</span></span> <span data-ttu-id="4af11-135">이 경우 인터페이스를 사용하여 디바이스에서 직접 공동 데이터를 요청할 수 [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-135">In this case the joint data can be requested directly from the device, using the [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.</span></span>

#### <a name="polling-joint-pose-from-controller"></a><span data-ttu-id="4af11-136">컨트롤러에서 공동 자세 폴링</span><span class="sxs-lookup"><span data-stu-id="4af11-136">Polling joint pose from controller</span></span>

<span data-ttu-id="4af11-137">[`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) `false` 어떤 이유로 요청된 조인을 사용할 수 없는 경우 함수는 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-137">The [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) function returns `false` if the requested joint is not available for some reason.</span></span> <span data-ttu-id="4af11-138">이 경우 결과 자세는 [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) 입니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-138">In that case the resulting pose will be [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var hand = eventData.Controller as IMixedRealityHand;
  if (hand != null)
  {
    if (hand.TryGetJoint(TrackedHandJoint.IndexTip, out MixedRealityPose jointPose)
    {
      // ...
    }
  }
}
```

#### <a name="joint-transform-from-hand-visualizer"></a><span data-ttu-id="4af11-139">손 시각화 도우미에서의 공동 변환</span><span class="sxs-lookup"><span data-stu-id="4af11-139">Joint transform from hand visualizer</span></span>

<span data-ttu-id="4af11-140">[컨트롤러 시각화 도우미](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer)에서 공동 개체를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-140">Joint objects can be requested from the [controller visualizer](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var handVisualizer = eventData.Controller.Visualizer as IMixedRealityHandVisualizer;
  if (handVisualizer != null)
  {
    if (handVisualizer.TryGetJointTransform(TrackedHandJoint.IndexTip, out Transform jointTransform)
    {
      // ...
    }
  }
}
```

### <a name="simplified-joint-data-access"></a><span data-ttu-id="4af11-141">간소화된 공동 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="4af11-141">Simplified joint data access</span></span>

<span data-ttu-id="4af11-142">특정 컨트롤러가 지정되지 않은 경우 손 공동 데이터에 편리하게 액세스할 수 있도록 유틸리티 클래스가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-142">If no specific controller is given then utility classes are provided for convenient access to hand joint data.</span></span> <span data-ttu-id="4af11-143">이러한 함수는 현재 추적된 첫 번째 사용 가능한 손 디바이스에서 공동 데이터를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-143">These functions request joint data from the first available hand device currently tracked.</span></span>

#### <a name="polling-joint-pose-from-handjointutils"></a><span data-ttu-id="4af11-144">HandJointUtils에서 공동 자세 폴링</span><span class="sxs-lookup"><span data-stu-id="4af11-144">Polling joint pose from HandJointUtils</span></span>

<span data-ttu-id="4af11-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) 는 첫 번째 활성 손 디바이스를 쿼리하는 정적 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) is a static class that queries the first active hand device.</span></span>

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a><span data-ttu-id="4af11-146">손 공동 서비스에서의 공동 변환</span><span class="sxs-lookup"><span data-stu-id="4af11-146">Joint transform from hand joint service</span></span>

<span data-ttu-id="4af11-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) 는 조인트 추적을 위해 [GameObjects의](https://docs.unity3d.com/ScriptReference/GameObject.html) 영구 집합을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) keeps a persistent set of [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) for tracking joints.</span></span>

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a><span data-ttu-id="4af11-148">손 추적 이벤트</span><span class="sxs-lookup"><span data-stu-id="4af11-148">Hand tracking events</span></span>

<span data-ttu-id="4af11-149">컨트롤러에서 직접 데이터를 폴링하는 것이 바람직하지 않은 경우 입력 시스템은 이벤트도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-149">The input system provides events as well, if polling data from controllers directly is not desirable.</span></span>

#### <a name="joint-events"></a><span data-ttu-id="4af11-150">공동 이벤트</span><span class="sxs-lookup"><span data-stu-id="4af11-150">Joint events</span></span>

<span data-ttu-id="4af11-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) 는 공동 위치의 업데이트를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) handles updates of joint positions.</span></span>

```c#
public class MyHandJointEventHandler : IMixedRealityHandJointHandler
{
    public Handedness myHandedness;

    void IMixedRealityHandJointHandler.OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            if (eventData.InputData.TryGetValue(TrackedHandJoint.IndexTip, out MixedRealityPose pose))
            {
                // ...
            }
        }
    }
}
```

#### <a name="mesh-events"></a><span data-ttu-id="4af11-152">메시 이벤트</span><span class="sxs-lookup"><span data-stu-id="4af11-152">Mesh events</span></span>

<span data-ttu-id="4af11-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) 는 굴절된 손 메시의 변경 내용을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) handles changes of the articulated hand mesh.</span></span>

<span data-ttu-id="4af11-154">손 메시는 기본적으로 사용하도록 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-154">Note that hand meshes are not enabled by default.</span></span>

```c#
public class MyHandMeshEventHandler : IMixedRealityHandMeshHandler
{
    public Handedness myHandedness;
    public Mesh myMesh;

    public void OnHandMeshUpdated(InputEventData<HandMeshInfo> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            myMesh.vertices = eventData.InputData.vertices;
            myMesh.normals = eventData.InputData.normals;
            myMesh.triangles = eventData.InputData.triangles;

            if (eventData.InputData.uvs != null && eventData.InputData.uvs.Length > 0)
            {
                myMesh.uv = eventData.InputData.uvs;
            }

            // ...
        }
    }
}
```

## <a name="known-issues"></a><span data-ttu-id="4af11-155">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="4af11-155">Known issues</span></span>

### <a name="net-native"></a><span data-ttu-id="4af11-156">.NET 네이티브</span><span class="sxs-lookup"><span data-stu-id="4af11-156">.NET Native</span></span>

<span data-ttu-id="4af11-157">현재 .NET 백 엔드를 사용하는 마스터 빌드에는 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-157">There is currently a known issue with Master builds using the .NET backend.</span></span> <span data-ttu-id="4af11-158">.NET 네이티브 를 사용하여 `IInspectable` 네이티브 코드에서 관리 코드로 포인터를 마샬링할 수 `Marshal.GetObjectForIUnknown` 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-158">In .NET Native, `IInspectable` pointers cannot be marshaled from native to managed code using `Marshal.GetObjectForIUnknown`.</span></span> <span data-ttu-id="4af11-159">MRTK는 플랫폼에서 손 및 시선 데이터를 받기 위해 이를 사용하여 를 `SpatialCoordinateSystem` 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-159">The MRTK uses this to obtain the `SpatialCoordinateSystem` in order to receive hand and eye data from the platform.</span></span>

<span data-ttu-id="4af11-160">이 문제에 대한 해결 방법으로 [네이티브 Mixed Reality Toolkit 리포지점](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround)에서 DLL 원본을 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-160">We've provided DLL source as a workaround for this issue, in [the native Mixed Reality Toolkit repo](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span></span> <span data-ttu-id="4af11-161">README의 지침에 따라 결과 이진 파일을 Unity 자산의 플러그 인 폴더에 복사하세요.</span><span class="sxs-lookup"><span data-stu-id="4af11-161">Please follow the instructions in the README there and copy the resulting binaries into a Plugins folder in your Unity assets.</span></span> <span data-ttu-id="4af11-162">그런 다음 MRTK에 제공된 WindowsMixedRealityUtilities 스크립트가 해결 방법을 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-162">After that, the WindowsMixedRealityUtilities script provided in the MRTK will resolve the workaround for you.</span></span>

<span data-ttu-id="4af11-163">고유한 DLL을 만들거나 기존 DLL에 이 해결 방법을 포함하려는 경우 해결 방법의 핵심은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-163">If you want to create your own DLL or include this workaround in an existing one, the core of the workaround is:</span></span>

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

<span data-ttu-id="4af11-164">그리고 C# Unity 코드에서 다음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4af11-164">And its use in your C# Unity code:</span></span>

```c#
[DllImport("DotNetNativeWorkaround.dll", EntryPoint = "MarshalIInspectable")]
private static extern void GetSpatialCoordinateSystem(IntPtr nativePtr, out SpatialCoordinateSystem coordinateSystem);

private static SpatialCoordinateSystem GetSpatialCoordinateSystem(IntPtr nativePtr)
{
    try
    {
        GetSpatialCoordinateSystem(nativePtr, out SpatialCoordinateSystem coordinateSystem);
        return coordinateSystem;
    }
    catch
    {
        UnityEngine.Debug.LogError("Call to the DotNetNativeWorkaround plug-in failed. The plug-in is required for correct behavior when using .NET Native compilation");
        return Marshal.GetObjectForIUnknown(nativePtr) as SpatialCoordinateSystem;
    }
}
```
