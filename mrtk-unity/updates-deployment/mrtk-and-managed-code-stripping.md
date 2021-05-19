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
# <a name="mrtk-and-unity-managed-code-stripping"></a>MRTK 및 Unity 관리 코드 제거

Unity의 IL2CPP 스크립팅 백 엔드(Unity 2018.4에서 선택 사항, 2019 이상에 필요)를 사용하는 경우 [관리 코드 제거가](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) 발생합니다.
Unity의 링커는 이 프로세스를 수행하여 이진 크기를 줄이고 빌드 시간을 줄입니다.

Mixed Reality 도구 키트는 파일을 사용하여 `link.xml` Unity의 링커가 MRTK 어셈블리를 처리하는 방법에 영향을 줍니다. [Unity 설명서에서](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)전체 설명된 이 파일은 사용법을 유추할 수 없는 경우(예: 리플렉션을 통해 사용) 코드를 유지하는 방법에 대한 지침을 링커에 제공합니다.

유연하고 사용자 지정 가능한 플랫폼인 MRTK는 파일이 없는 경우 가져올 때 `link.xml` 에 파일을 만듭니다. `Assets/MixedRealityToolkit.Generated` 기존 link.xml 파일을 덮어쓰지 않습니다. 및 를 `link.xml` 버전 제어에 추가하는 것이 `link.xml.meta` 좋습니다. 개발자는 프로젝트의 요구 사항에 맞게 자유롭게 사용자 지정할 수 있어야 `Assets/MixedRealityToolkit.Generated/link.xml` 합니다.

기본적으로 MRTK에서 만든 link.xml 파일은 다음 데이터에 표시된 어셈블리 전체를 유지합니다.

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

link.xml 파일 형식에 대한 자세한 내용은 Unity 설명서를 참조하세요.

## <a name="see-also"></a>참고 항목

- [Unity: 관리 코드 제거](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [Unity: XML 파일 연결](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
