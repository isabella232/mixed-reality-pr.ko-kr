---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636366"
---
# <a name="mrtk"></a>[<span data-ttu-id="d6bc2-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="d6bc2-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="d6bc2-102">MRTK는 [카메라 시스템 프로필의 구성](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)에 따라 특정 카메라 설정을 자동으로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6bc2-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="d6bc2-103">**네임 스페이스:** *MixedReality. CameraSystem*</span><span class="sxs-lookup"><span data-stu-id="d6bc2-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="d6bc2-104">**유형:** *MixedRealityCameraSystem*</span><span class="sxs-lookup"><span data-stu-id="d6bc2-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="d6bc2-105">카메라의 opaqueness를 확인 하기 위해 MixedRealityCamera 시스템에는 [ `IsOpaque` 속성이](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque)있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bc2-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="d6bc2-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="d6bc2-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="d6bc2-107">**네임 스페이스:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="d6bc2-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="d6bc2-108">**유형:** *xrdisplaysubsystem*</span><span class="sxs-lookup"><span data-stu-id="d6bc2-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="d6bc2-109">스크립트 코드를 사용 하 여 적극적으로 실행 중인 [Xrdisplaysubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)에서 [displayopaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) 을 확인 하 여 헤드셋이 몰입 형 또는 holographic 인지 여부를 런타임에 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bc2-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="d6bc2-110">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="d6bc2-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="d6bc2-111">**네임 스페이스:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="d6bc2-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="d6bc2-112">**유형:** *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="d6bc2-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="d6bc2-113">스크립트 코드를 사용 하 여 [HolographicSettings](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)를 확인 하 여 헤드셋이 몰입 또는 holographic 인지 여부를 런타임에 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6bc2-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>