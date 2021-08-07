---
title: 손 추적
description: MRTK에서 수동 추적을 사용 하는 방법에 대 한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 직접 추적
ms.openlocfilehash: f9d3b6b0f83a513b849aa27d464595ec8543bc30b64314c9a6e341cd6cb3a519
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189499"
---
# <a name="hand-tracking"></a>손 추적

## <a name="hand-tracking-profile"></a>수동 추적 프로필

_직접 추적 프로필_ 은 _입력 시스템 프로필_ 아래에 있습니다. 직접 표시를 사용자 지정 하는 설정이 포함 되어 있습니다.

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a>조인트 prefabs

조인트 prefabs는 simple prefabs를 사용 하 여 시각화 됩니다. _야자나무_ 및 _인덱스 손가락_ 의 조인트는 특별 한 중요 한 것 이며, 다른 모든 조인트는 동일한 prefab을 prefab 합니다.

기본적으로 손 모양 prefabs는 간단한 기 하 도형 기본 형식입니다. 원하는 경우 대체할 수 있습니다. Prefab가 전혀 지정 되지 않은 경우 빈 [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) 가 대신 만들어집니다.

> [!WARNING]
> 조인트 개체는 모든 프레임에서 변환 되 고 상당한 성능 비용이 발생할 수 있으므로, 조인트 prefabs에서 복잡 한 스크립트나 비용이 많이 드는 렌더링은 사용 하지 마세요.

기본 직접 조인트 표현 |  공동 레이블
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a>손 모양 메시 prefab

손 모양 메시는 직접 추적 장치에서 완전히 정의 된 메시 데이터를 제공 하는 경우에 사용 됩니다. Prefab의 메시 렌더링할는 장치의 데이터로 대체 되므로 큐브와 같은 더미 메시로 충분 합니다. Prefab의 재질은 손 모양에 사용 됩니다.

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

수동 메시 표시는 성능에 큰 영향을 줄 수 있습니다. 따라서 **직접 메시 시각화 사용** 옵션을 선택 취소 하 여 완전히 사용 하지 않도록 설정할 수 있습니다.

## <a name="hand-visualization-settings"></a>수동 시각화 설정

손 모양 메쉬 및 손 모양 연결점은 각각 *손 모양 시각화 모드* 설정 및 *직접 접합 시각화 모드* 를 통해 설정 하거나 해제할 수 있습니다. 이러한 설정은 응용 프로그램 모드에 따라 다릅니다. 즉, 편집기에서 (예를 들어 편집기 내 시뮬레이션을 사용 하 여 조인트를 표시 하는 경우), 장치에 배포할 때 (플레이어 빌드에서) 동일한 기능이 해제 되어 있는 동안 일부 기능을 켤 수 있습니다.

일반적으로 편집기에서 직접 공동 시각화를 설정 하는 것이 좋습니다. 즉, 편집기 내 시뮬레이션에서 손 조인트가 있는 위치를 표시 하 고, 손 모양 맞추기 및 손 모양 메쉬 시각화를 모두 플레이어에서 끌 수 있습니다 (성능 저하가 발생 하기 때문).

## <a name="scripting"></a>스크립팅

각 개별 핸드 조인트에 대해 입력 시스템에서 위치 및 회전이 요청 될 수 있습니다 [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

또는 시스템에서 조인트를 따르는 [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) 에 대 한 액세스를 허용 합니다. 이는 다른 GameObject에서 조인트를 지속적으로 추적 해야 하는 경우에 유용할 수 있습니다.

사용 가능한 조인트는 열거형에 나열 됩니다 [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) .

> [!NOTE]
> 직접 추적이 손실 된 경우에는 조인트 개체가 제거 됩니다. 오류를 방지 하기 위해 조인트 개체를 사용 하는 모든 스크립트가 사례를 정상적으로 처리 하는지 확인 합니다 `null` .

### <a name="accessing-a-given-hand-controller"></a>지정 된 손 컨트롤러에 액세스

특정 손 컨트롤러 (예: 입력 이벤트를 처리할 때)를 사용 하는 경우가 많습니다. 이 경우 인터페이스를 사용 하 여 장치에서 직접 공동 데이터를 요청할 수 있습니다 [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) .

#### <a name="polling-joint-pose-from-controller"></a>컨트롤러에서 조인트 포즈 폴링

[`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*)이 함수는 `false` 어떤 이유로 요청 된 조인트를 사용할 수 없는 경우를 반환 합니다. 이 경우 결과 포즈는이 됩니다 [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .

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

#### <a name="joint-transform-from-hand-visualizer"></a>손 모양 시각화 도우미의 조인트 변형

[컨트롤러 시각화 도우미](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer)에서 조인트 개체를 요청할 수 있습니다.

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

### <a name="simplified-joint-data-access"></a>단순화 된 공동 데이터 액세스

특정 컨트롤러가 지정 되지 않은 경우에는 직접 연결 데이터에 편리 하 게 액세스할 수 있도록 유틸리티 클래스가 제공 됩니다. 이러한 함수는 현재 추적 된 첫 번째 사용 가능한 장치에서 공동 데이터를 요청 합니다.

#### <a name="polling-joint-pose-from-handjointutils"></a>HandJointUtils에서 조인트 포즈 폴링

[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) 는 첫 번째 활성 장치를 쿼리 하는 정적 클래스입니다.

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a>직접 조인트 서비스에서의 조인트 변형

[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) 추적 조인트에 대 한 영구 [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) 집합을 유지 합니다.

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a>직접 추적 이벤트

컨트롤러에서 직접 데이터를 폴링하는 것이 바람직하지 않은 경우에도 입력 시스템에서 이벤트를 제공 합니다.

#### <a name="joint-events"></a>조인트 이벤트

[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) 조인트 위치의 업데이트를 처리 합니다.

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

#### <a name="mesh-events"></a>메시 이벤트

[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) 트레일러 모양 망상의 변경 내용을 처리 합니다.

손 메시는 기본적으로 사용 하도록 설정 되어 있지 않습니다.

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

## <a name="known-issues"></a>알려진 문제

### <a name="net-native"></a>.NET 네이티브

현재 .NET 백 엔드를 사용 하는 마스터 빌드와 관련 된 알려진 문제가 있습니다. .NET 네이티브에서 포인터는를 `IInspectable` 사용 하 여 네이티브에서 관리 코드로 마샬링할 수 없습니다 `Marshal.GetObjectForIUnknown` . MRTK는이를 사용 하 여 `SpatialCoordinateSystem` 플랫폼에서 직접 및 눈 데이터를 수신 하기 위해를 가져옵니다.

이 문제에 대 한 해결 방법으로, [네이티브 혼합 현실 Toolkit](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround)리포지토리에 DLL 원본을 제공 했습니다. 추가 정보의 지침에 따라 결과 이진 파일을 Unity 자산의 플러그 인 폴더에 복사 하세요. 그러면 MRTK에 제공 된 WindowsMixedRealityUtilities 스크립트에서 해결 방법을 확인 합니다.

사용자 고유의 DLL을 만들거나이 해결 방법을 기존 DLL에 포함 하려는 경우 해결 방법의 핵심은 다음과 같습니다.

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

그리고 c # Unity 코드에서 사용 됩니다.

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
