---
title: HoloLens 용 Unity를 사용 하는 WinRT Api
description: Leanr의 Unity 혼합 현실 프로젝트에서 WinRT Api 및 Windows 네임 스페이스를 활용 하는 방법을 설명 합니다.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, windows mixed reality, API, 연습, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 혼합 현실 Api
ms.openlocfilehash: 2116f0025449fdf127998e605f87de456e9bdaf9
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583556"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>HoloLens 용 Unity를 사용 하는 WinRT Api

이 페이지에서는 HoloLens 용 Unity 프로젝트에서 WinRT Api를 활용 하는 방법을 설명 합니다.

## <a name="mixed-reality-apis"></a>혼합 현실 Api

Windows SDK의 혼합 현실 하위 집합은 전처리기 지시문이 없는 프로젝트에서 사용할 수 있는 .NET Standard 2.0 호환 프로젝션에서 사용할 수 있게 되었습니다. 대부분의 Windows Api 인식 및 Windows 네임 스페이스는 포함 되며 나중에 추가 Api를 포함 하도록 확장할 수 있습니다. 투영 된 Api는 편집기에서 실행 되는 동안 사용할 수 있으며이를 통해 [재생 모드](//windows/mixed-reality/unity-play-mode)를 사용할 수 있습니다. 이 프로젝션을 사용 하려면 프로젝트를 다음과 같이 수정 합니다.

1) [Unity 용 nuget](https://github.com/GlitchEnzo/NuGetForUnity)을 사용 하 여 [MixedReality DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) nuget 패키지에 대 한 참조를 추가 합니다.
2) `Windows`다음을 사용 하 여 네임 스페이스에 대 한 참조 접두사 `Microsoft.` :
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Native pointer 캐스트를 다음으로 바꿉니다 `FromNativePtr` .
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>조건부로 WinRT API 호출 포함

전처리기 지시문을 사용 하 여 유니버설 Windows 플랫폼 및 Xbox One 플랫폼에 대해 빌드된 Unity 프로젝트에서 WinRT Api를 사용할 수도 있습니다. WinRT Api를 대상으로 하는 Unity 스크립트에서 작성 하는 모든 코드는 해당 빌드에 대해서만 조건부로 포함 되어야 합니다. 

Unity의 두 단계를 통해이 작업을 수행할 수 있습니다.
1) 플레이어 설정에서 API 호환성 수준을 **.net 4.6** 또는 **.NET Standard 2.0** 으로 설정 해야 합니다.
    - **편집**  >  **프로젝트 설정**  >  **플레이어**  >  **구성**  >  **Api 호환성 수준이** **.net 4.6** 또는 **.NET Standard 2.0**
2) 전처리기 지시문 **ENABLE_WINMD_SUPPORT** 은 WinRT 활용 코드를 통해 래핑해야 합니다.

다음 코드 조각은 [c # 스크립트의 WINRT API 유니버설 Windows 플랫폼](https://docs.unity3d.com/Manual/windowsstore-scripts.html)에 대 한 Unity 수동 페이지에서 가져온 것입니다. 이 예에서 광고 ID는 반환 되지만 UWP 및 Xbox One 빌드에만 해당 됩니다.

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Unity c # 프로젝트에서 스크립트 편집

Unity 편집기에서 스크립트를 두 번 클릭 하면 기본적으로 편집기 프로젝트에서 스크립트가 시작 됩니다. Visual Studio 프로젝트가 Windows 런타임를 참조 하지 않으므로 WinRT Api를 알 수 없는 것으로 표시 됩니다. **ENABLE_WINMD_SUPPORT** 지시문은 정의 되지 않으며, UWP Visual Studio 솔루션에 프로젝트를 빌드할 때까지 *#if* 래핑된 코드는 무시 됩니다.

## <a name="see-also"></a>참고 항목
* [Unity Visual Studio 솔루션 내보내기 및 빌드](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows 런타임 지원 Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)