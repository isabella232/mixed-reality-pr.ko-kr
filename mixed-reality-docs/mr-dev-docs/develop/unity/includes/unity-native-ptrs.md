---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475080"
---
# <a name="mrtk"></a>[<span data-ttu-id="83554-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="83554-101">MRTK</span></span>](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a><span data-ttu-id="83554-102">WindowsMixedRealityUtilities</span><span class="sxs-lookup"><span data-stu-id="83554-102">WindowsMixedRealityUtilities</span></span>

<span data-ttu-id="83554-103">**네임 스페이스:** *MixedReality. WindowsMixedReality*</span><span class="sxs-lookup"><span data-stu-id="83554-103">**Namespace:** *Microsoft.MixedReality.Toolkit.WindowsMixedReality*</span></span><br>
<span data-ttu-id="83554-104">**유형:** *WindowsMixedRealityUtilities*</span><span class="sxs-lookup"><span data-stu-id="83554-104">**Type:** *WindowsMixedRealityUtilities*</span></span>

<span data-ttu-id="83554-105">MRTK는 **WindowsMixedRealityUtilities** 클래스를 통해 레거시 WSA 및 XR SDK에서 이미 마샬링된 형식을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="83554-105">MRTK provides already-marshalled types across both legacy WSA and XR SDK through the **WindowsMixedRealityUtilities** class.</span></span>

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[<span data-ttu-id="83554-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="83554-106">XR SDK</span></span>](#tab/xr)

## <a name="windowsmrenvironment"></a><span data-ttu-id="83554-107">WindowsMREnvironment</span><span class="sxs-lookup"><span data-stu-id="83554-107">WindowsMREnvironment</span></span>

<span data-ttu-id="83554-108">**네임 스페이스:** *unityengine. XR smr*</span><span class="sxs-lookup"><span data-stu-id="83554-108">**Namespace:** *UnityEngine.XR.WindowsMR*</span></span><br>
<span data-ttu-id="83554-109">**유형:** *WindowsMREnvironment*</span><span class="sxs-lookup"><span data-stu-id="83554-109">**Type:** *WindowsMREnvironment*</span></span>

<span data-ttu-id="83554-110">Static **WindowsMREnvironment** 클래스는 여러 네이티브 포인터에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="83554-110">The static **WindowsMREnvironment** class provides access to several native pointers.</span></span>

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="83554-111">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="83554-111">Legacy WSA</span></span>](#tab/wsa)

## <a name="xrdevice"></a><span data-ttu-id="83554-112">XRDevice</span><span class="sxs-lookup"><span data-stu-id="83554-112">XRDevice</span></span>

<span data-ttu-id="83554-113">**네임 스페이스:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="83554-113">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="83554-114">**유형:** *xrdevice*</span><span class="sxs-lookup"><span data-stu-id="83554-114">**Type:** *XRDevice*</span></span>

<span data-ttu-id="83554-115"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**Xrdevice**</a> 유형을 사용 하면 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> 메서드를 사용 하 여 기본 네이티브 개체에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83554-115">The <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="83554-116">GetNativePtr 반환 되는 항목은 플랫폼 마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="83554-116">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="83554-117">Windows Mixed Reality를 대상으로 하는 유니버설 Windows 플랫폼에서 GetNativePtr는 다음 구조에 대 한 포인터 (IntPtr)를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="83554-117">On the Universal Windows Platform when targeting Windows Mixed Reality, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span>

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

<span data-ttu-id="83554-118">Marshal.sizeof와 marshal.ptrtostructure 메서드를 사용 하 여 HolographicFrameNativeData로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83554-118">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

<span data-ttu-id="83554-119">***IHolographicCameraPtr** 은 길이가 MaxNumberOfCameras와 같은 unmanagedtype.lpwstr ByValArray으로 마샬링되는 IntPtr의 배열입니다.*</span><span class="sxs-lookup"><span data-stu-id="83554-119">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span>
