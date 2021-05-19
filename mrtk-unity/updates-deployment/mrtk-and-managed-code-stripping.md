---
title: MRTK 및 관리 코드 제거
description: MRTK 및 Unity에서 코드 제거
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 09e5140fd9585c19eacac5ba937eaf4ea8f2a8ea
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143729"
---
# <a name="mrtk-and-unity-managed-code-stripping"></a><span data-ttu-id="4d0b6-104">MRTK 및 Unity 관리 코드 제거</span><span class="sxs-lookup"><span data-stu-id="4d0b6-104">MRTK and Unity managed code stripping</span></span>

<span data-ttu-id="4d0b6-105">Unity의 IL2CPP 스크립팅 백 엔드(Unity 2018.4에서 선택 사항, 2019 이상에 필요)를 사용하는 경우 [관리 코드 제거가](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4d0b6-105">When using Unity's IL2CPP scripting backend (optional in Unity 2018.4, required in 2019 and newer), [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) occurs.</span></span>
<span data-ttu-id="4d0b6-106">Unity의 링커는 이 프로세스를 수행하여 이진 크기를 줄이고 빌드 시간을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="4d0b6-106">Unity's linker performs this process to reduce binary size as well as to decrease build times.</span></span>

<span data-ttu-id="4d0b6-107">Mixed Reality 도구 키트는 파일을 사용하여 `link.xml` Unity의 링커가 MRTK 어셈블리를 처리하는 방법에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4d0b6-107">The Mixed Reality Toolkit uses a file, `link.xml`, to influence how Unity's linker processes MRTK assemblies.</span></span> <span data-ttu-id="4d0b6-108">[Unity 설명서에서](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)전체 설명된 이 파일은 사용법을 유추할 수 없는 경우(예: 리플렉션을 통해 사용) 코드를 유지하는 방법에 대한 지침을 링커에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4d0b6-108">This file, described in full in [Unity's documentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), provides the linker with instructions on how to preserve code when its usage cannot be inferred (ex: used via reflection).</span></span>

<span data-ttu-id="4d0b6-109">유연하고 사용자 지정 가능한 플랫폼인 MRTK는 파일이 없는 경우 가져올 때 `link.xml` 에 파일을 만듭니다. `Assets/MixedRealityToolkit.Generated`</span><span class="sxs-lookup"><span data-stu-id="4d0b6-109">As a flexible and customizable platform, MRTK creates the `link.xml` file in `Assets/MixedRealityToolkit.Generated` on import, if it is found to not exist.</span></span> <span data-ttu-id="4d0b6-110">기존 link.xml 파일을 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4d0b6-110">Pre-existing link.xml files are not overwritten.</span></span> <span data-ttu-id="4d0b6-111">및 를 `link.xml` 버전 제어에 추가하는 것이 `link.xml.meta` 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4d0b6-111">It is recommended that `link.xml` and `link.xml.meta` be added to version control.</span></span> <span data-ttu-id="4d0b6-112">개발자는 프로젝트의 요구 사항에 맞게 자유롭게 사용자 지정할 수 있어야 `Assets/MixedRealityToolkit.Generated/link.xml` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d0b6-112">Developers should feel free to customize `Assets/MixedRealityToolkit.Generated/link.xml` to meet the needs of the project.</span></span>

<span data-ttu-id="4d0b6-113">기본적으로 MRTK에서 만든 link.xml 파일은 다음 데이터에 표시된 어셈블리 전체를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="4d0b6-113">By default, the link.xml file created by MRTK preserves the entirety of the assemblies shown in the following data.</span></span>

``` xml
<linker> 
  <!-- 
    This link.xml file is provided to prevent MRTK code from being optimized away 
    during IL2CPP builds.More details on when this is needed and why this is needed 
    can be found here: https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5273 
    If your application doesn't use some specific services (for example, if teleportation system is 
    disabled in the profile), it is possible to remove their corresponding lines down 
    below(in the previous example, we would remove the TeleportSystem below). 
    It's recommended to start with this list and narrow down if you want to ensure 
    specific bits of code get optimized away. 
  --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.SDK" preserve="all"/> 
  <!-- Core systems --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.BoundarySystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.CameraSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.InputSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SceneSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.TeleportSystem" preserve="all"/> 
  <!-- Data providers --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.LeapMotion" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenVR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.UnityAR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.Shared" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK" preserve="all"/> 
  <!-- Extension services --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.HandPhysics" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.Tracking" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.SceneTransitionService" preserve="all"/> 
</linker>
```

<span data-ttu-id="4d0b6-114">link.xml 파일 형식에 대한 자세한 내용은 Unity 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d0b6-114">For more information on the link.xml file format, please refer to the Unity documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d0b6-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d0b6-115">See also</span></span>

- [<span data-ttu-id="4d0b6-116">Unity: 관리 코드 제거</span><span class="sxs-lookup"><span data-stu-id="4d0b6-116">Unity: Managed Code Stripping</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [<span data-ttu-id="4d0b6-117">Unity: XML 파일 연결</span><span class="sxs-lookup"><span data-stu-id="4d0b6-117">Unity: Link XML file</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
