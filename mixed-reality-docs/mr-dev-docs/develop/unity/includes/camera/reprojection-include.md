---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636361"
---
# <a name="mrtk"></a>[<span data-ttu-id="f34a3-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="f34a3-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="f34a3-102">MRTK에는 현재 reprojection 모드에 대 한 도우미가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f34a3-102">MRTK doesn't currently have helpers for the reprojection mode.</span></span> <span data-ttu-id="f34a3-103">자세한 내용은 다른 탭 중 하나를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f34a3-103">Please see one of the other tabs for more information.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="f34a3-104">XR SDK</span><span class="sxs-lookup"><span data-stu-id="f34a3-104">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="f34a3-105">Reprojection 모드는 reprojectionMode을 적절 한 값으로 설정 하 여 구성할 수 있습니다 [.](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html)</span><span class="sxs-lookup"><span data-stu-id="f34a3-105">The reprojection mode is configurable by setting [XRDisplaySubsystem.reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="f34a3-106">예를 들어 엄격 본문에서 잠긴 콘텐츠 (예: 360도 비디오 콘텐츠)를 사용 하 여 [방향 전용 환경을](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) 빌드하는 경우 [ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html)로 설정 하 여 reprojection 모드를 방향 으로만 명시적으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f34a3-106">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [ReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="f34a3-107">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="f34a3-107">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="f34a3-108">Reprojection 모드는 ReprojectionMode를 적절 한 값으로 설정 하 여 구성할 수 있습니다 [.](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html)</span><span class="sxs-lookup"><span data-stu-id="f34a3-108">The reprojection mode is configurable by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="f34a3-109">예를 들어 엄격 본문에서 잠긴 콘텐츠 (예: 360도 비디오 콘텐츠)를 사용 하 여 [방향 전용 환경을](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) 빌드하는 경우 [HolographicReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)로 설정 하 여 reprojection 모드를 방향 으로만 명시적으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f34a3-109">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>