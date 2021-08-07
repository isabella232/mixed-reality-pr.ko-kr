---
ms.openlocfilehash: 78296dd4e6667c34926c954774547b21a223c5f4b6635476c51046c7ca22cdc3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208406"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**네임 스페이스:** *MixedReality. Toolkit. WindowsMixedReality*<br>
**유형:** *WindowsMixedRealityUtilities*

MRTK는 **WindowsMixedRealityUtilities** 클래스를 통해 레거시 WSA 및 XR SDK에서 이미 마샬링된 형식을 제공 합니다.

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**네임 스페이스:** *unityengine. XR smr*<br>
**유형:** *WindowsMREnvironment*

Static **WindowsMREnvironment** 클래스는 여러 네이티브 포인터에 대 한 액세스를 제공 합니다.

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**네임 스페이스:** *UNITYENGINE. XR*<br>
**유형:** *xrdevice*

<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**Xrdevice**</a> 유형을 사용 하면 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> 메서드를 사용 하 여 기본 네이티브 개체에 액세스할 수 있습니다. GetNativePtr 반환 되는 항목은 플랫폼 마다 다릅니다. Windows Mixed Reality를 대상으로 지정 하는 유니버설 Windows 플랫폼에서 GetNativePtr는 다음 구조체로 포인터 (IntPtr)를 반환 합니다.

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

Marshal.sizeof와 marshal.ptrtostructure 메서드를 사용 하 여 HolographicFrameNativeData로 변환할 수 있습니다.

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr** 은 길이가 MaxNumberOfCameras와 같은 unmanagedtype.lpwstr ByValArray으로 마샬링되는 IntPtr의 배열입니다.*
