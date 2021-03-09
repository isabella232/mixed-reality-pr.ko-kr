---
title: Unity의 혼합 현실 기본 개체
description: XR 네임 스페이스를 사용 하 여 Unity에서 기본 Holographic 네이티브 개체에 액세스 하는 방법에 대해 알아봅니다.
author: vladkol
ms.author: vladkol
ms.date: 02/25/2021
ms.topic: article
keywords: unity, mixed reality, 네이티브, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr, mixed reality 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: c202c698fe55bcd3215850579166ebcb8d4b8910
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475079"
---
# <a name="mixed-reality-native-interop-in-unity"></a>Unity의 혼합 현실 네이티브 interop

모든 혼합 현실 앱은 카메라 데이터를 수신 하 고 프레임을 렌더링 하기 시작 하기 전에 [HolographicSpace를 가져옵니다](../native/getting-a-holographicspace.md) . Unity에서 엔진은 Holographic 개체를 처리 하 고 내부적으로 렌더링 루프의 일부로 업데이트 하는 단계를 처리 합니다.

그러나 고급 시나리오에서는 <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> 및 current <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>와 같은 기본 네이티브 개체에 대 한 액세스 권한을 얻어야 할 수 있습니다.

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a>네이티브 포인터 역마샬링

`IntPtr`위의 방법 중 하나에서를 가져온 후 (MRTK에는 필요 하지 않음) 다음 코드 조각을 사용 하 여 관리 되는 개체로 마샬링합니다.

[MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)를 사용 하는 경우 메서드를 사용 하 여 네이티브 포인터에서 관리 되는 개체를 생성할 수 있습니다. `FromNativePtr()`

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

그렇지 않으면를 사용 하 여 `Marshal.GetObjectForIUnknown()` 원하는 형식으로 캐스팅 합니다.

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a>좌표계 간 변환

Unity는 왼손 좌표계를 사용 하는 반면 Windows 인식 Api는 오른손 좌표계를 사용 합니다. 이러한 두 가지 규칙을 변환 하기 위해 다음 도우미를 사용할 수 있습니다.

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(q.X, q.Y, -q.Z, -q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(q.x, q.y, -q.z, -q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a>HolographicFrame 네이티브 데이터 사용

> [!NOTE]
> HolographicFrameNativeData을 통해 수신 되는 네이티브 개체의 상태를 변경 하면 예기치 않은 동작 및 렌더링 아티팩트가 발생할 수 있습니다. 특히 Unity에서 동일한 상태를 갖는 이유가 있을 수 있습니다.  예를 들어 HolographicFrame를 호출 하면 안 됩니다. UpdateCurrentPrediction를 호출 하면 안 됩니다. 그렇지 않으면 Unity가 해당 프레임으로 렌더링 하는 포즈 예측이 Windows에서 기대 하는 포즈와 동기화 되지 않아 [홀로그램 안정성이](../platform-capabilities-and-apis/hologram-stability.md)감소 합니다.

렌더링 또는 디버깅을 위해 네이티브 인터페이스에 액세스 해야 하는 경우 네이티브 플러그 인 또는 c # 코드에서 HolographicFrameNativeData의 데이터를 사용 합니다.

HolographicFrameNativeData를 사용 하 여 XR SDK 확장을 사용 하 여 photon time에 대 한 현재 프레임의 예측을 가져오는 방법의 예는 다음과 같습니다.

```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if ENABLE_WINMD_SUPPORT
    IntPtr holographicFramePtr = UnityEngine.XR.WindowsMR.WindowsMREnvironment.CurrentHolographicRenderFrame;

    if (holographicFramePtr != IntPtr.Zero)
    {
        var holographicFrame = Marshal.GetObjectForIUnknown(holographicFramePtr) as Windows.Graphics.Holographic.HolographicFrame;
        frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
        return true;
    }
#endif

    frameDateTime = DateTime.MinValue;
    return false;
}
```

## <a name="see-also"></a>참고 항목

* [HoloLens용 Unity 앱에서 Windows 네임스페이스 사용](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [DirectX의 렌더링](../native/rendering-in-directx.md)
