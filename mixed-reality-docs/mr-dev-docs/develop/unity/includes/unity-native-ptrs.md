---
ms.openlocfilehash: c3775dc73f41b822c233d8fc4ec62459e789b89f
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122263404"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**네임스페이스:** *Microsoft.MixedReality.Toolkit. WindowsMixedReality*<br>
**유형:** *WindowsMixedRealityUtilities*

MRTK는 **WindowsMixedRealityUtilities** 클래스를 통해 레거시 WSA 및 XR SDK에서 이미 마샬링된 형식을 제공합니다.

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="windows-xr-plugin"></a>[Windows XR 플러그 인](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**네임스페이스:** *UnityEngine.XR.WindowsMR*<br>
**유형:** *WindowsMREnvironment*

정적 **WindowsMREnvironment** 클래스는 여러 네이티브 포인터에 대한 액세스를 제공합니다.

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**네임스페이스:** *UnityEngine.XR*<br>
**유형:** *XRDevice*

<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> 형식을 사용하면 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> 메서드를 사용하여 기본 네이티브 개체에 액세스할 수 있습니다. GetNativePtr에서 반환하는 내용은 플랫폼마다 다릅니다. 유니버설 Windows 플랫폼에서 Windows Mixed Reality 대상으로 지정할 때 XRDevice.GetNativePtr은 포인터(IntPtr)를 다음 구조로 반환합니다.

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame
    public IntPtr IHolographicCameraPtr; // Windows::Graphics::Holographic::IHolographicCamera
}
```

Marshal.PtrToStructure 메서드를 사용하여 HolographicFrameNativeData로 변환할 수 있습니다.

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr은 길이가** MaxNumberOfCameras와 같은 UnmanagedType.ByValArray로 마샬링된 IntPtr의 배열입니다.*
