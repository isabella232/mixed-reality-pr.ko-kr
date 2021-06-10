---
ms.openlocfilehash: 76f72ac81b677acabf98444f626b7a6b908c29fb
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748488"
---
# <a name="mrtk"></a>[<span data-ttu-id="143b4-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="143b4-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="143b4-102">MRTK는 카메라 시스템 프로필 의 [구성에](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)따라 특정 카메라 설정을 자동으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="143b4-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="143b4-103">**네임스페이스:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span><span class="sxs-lookup"><span data-stu-id="143b4-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="143b4-104">**형식:** *MixedRealityCameraSystem*</span><span class="sxs-lookup"><span data-stu-id="143b4-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="143b4-105">카메라의 불투명도를 확인하기 위해 MixedRealityCamera 시스템에는 [ `IsOpaque` 속성이](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque)있습니다.</span><span class="sxs-lookup"><span data-stu-id="143b4-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="143b4-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="143b4-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="143b4-107">**네임스페이스:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="143b4-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="143b4-108">**유형:** *XRDisplaySubsystem*</span><span class="sxs-lookup"><span data-stu-id="143b4-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="143b4-109">스크립트 코드를 사용하여 현재 실행 중인 [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)에서 [displayOpaque를](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) 확인하여 헤드셋이 몰입형인지 또는 홀로그램인지 런타임에 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="143b4-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="143b4-110">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="143b4-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="143b4-111">**네임스페이스:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="143b4-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="143b4-112">**유형:** *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="143b4-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="143b4-113">[HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)를 확인하여 런타임에 스크립트 코드를 사용하여 헤드셋이 몰입형인지 또는 홀로그램인지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="143b4-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>