---
title: MRTK 및 관리 코드 제거
description: MRTK 및 Unity에서 코드 제거
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 8b8e0f4488a6e955e599084c0b59d8c80f553a78
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176293"
---
# <a name="mrtk-and-managed-code-stripping"></a>MRTK 및 관리 코드 제거

Unity의 IL2CPP scripting 백 엔드를 사용 하는 경우 (Unity 2018.4에서 선택 사항, 2019 이상에서 필요) [관리 코드](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) 제거를 수행 합니다.
Unity의 링커는이 프로세스를 수행 하 여 이진 크기를 줄이고 빌드 시간을 줄입니다.

혼합 현실 Toolkit는 파일을 사용 하 여 `link.xml` Unity의 링커가 mrtk 어셈블리를 처리 하는 방식에 영향을 줍니다. [Unity 설명서](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)에서 전체에 설명 된이 파일은 해당 사용을 유추할 수 없을 때 코드를 유지 하는 방법에 대 한 지침을 링커에 제공 합니다 (예: 리플렉션을 통해 사용).

유연 하 고 사용자 지정이 가능한 플랫폼인 MRTK는 `link.xml` `Assets/MixedRealityToolkit.Generated` 가져올 때 (존재 하지 않는 경우)에 파일을 만듭니다. 기존 link.xml 파일은 덮어쓰지 않습니다. 를 `link.xml` `link.xml.meta` 버전 제어에 추가 하는 것이 좋습니다. 개발자는 `Assets/MixedRealityToolkit.Generated/link.xml` 프로젝트의 요구 사항을 충족 하기 위해 자유롭게 사용자 지정 해야 합니다.

기본적으로 MRTK에서 만든 link.xml 파일은 다음 데이터에 표시 된 어셈블리 전체를 유지 합니다.

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

link.xml 파일 형식에 대 한 자세한 내용은 Unity 설명서를 참조 하세요.

## <a name="see-also"></a>참조

- [Unity: 관리 코드 제거](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [Unity: XML 파일 연결](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
