---
title: Unity for HoloLens WinRT API
description: HoloLens 위해 Unity 혼합 현실 프로젝트에서 WinRT API 및 Windows 네임스페이스를 사용하는 방법을 간결하게 파악합니다.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, windows mixed reality, API, 연습, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, Mixed Reality API
ms.openlocfilehash: 158c28d9186269108442226bbfcfc90a3c235a71336fdab9dbf9eadc21a309a1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215609"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>Unity for HoloLens WinRT API

이 페이지에서는 HoloLens 위해 Unity 프로젝트에서 WinRT API를 사용하는 방법을 설명합니다.

## <a name="mixed-reality-apis"></a>Mixed Reality API

Windows SDK의 Mixed Reality 포커스가 있는 하위 집합은 전처리기 지시문 없이 프로젝트에서 사용할 수 있는 .NET Standard 2.0 호환 프로젝션에서 사용할 수 있습니다. Windows 대부분의 API. 인식 및 Windows. Ui. Input.Spatial 네임스페이스가 포함되며 나중에 추가 API를 포함하도록 확장할 수 있습니다. 프로젝스된 API는 편집기에서 실행하는 동안 사용할 수 있으며, 이를 통해 [재생 모드](/windows/mixed-reality/unity-play-mode)를 사용할 수 있습니다. 이 프로젝션을 사용하려면 프로젝트를 다음과 같이 수정합니다.

1) Microsoft.Windows 대한 참조를 [추가합니다. MixedReality.DotNetWinRT는](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) [Unity용](https://github.com/GlitchEnzo/NuGetForUnity)NuGet 사용하여 패키지를 NuGet.
2) 를 사용하여 `Windows` 네임스페이스에 대한 접두사 `Microsoft.` 참조:
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) 네이티브 포인터 캐스트를 로 대체합니다. `FromNativePtr`
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>조건부로 WinRT API 호출 포함

또한 전처리기 지시문을 사용하여 유니버설 Windows 플랫폼 및 Xbox One 플랫폼용으로 빌드된 Unity 프로젝트에서 WinRT API를 사용할 수도 있습니다. WinRT API를 대상으로 하는 Unity 스크립트에서 작성하는 모든 코드는 해당 빌드에 대해서만 조건부로 포함되어야 합니다. 

이 작업은 Unity에서 다음 두 단계를 통해 수행할 수 있습니다.
1) 플레이어 설정에서 API 호환성 수준을 **.NET 4.6** 또는 **.NET Standard 2.0으로** 설정해야 합니다.
    - **편집**  >  **Project 설정**  >  **플레이어**  >  **구성**  >  **.NET 4.6** 또는 **.NET Standard 2.0으로의** API 호환성 수준 
2) 전처리기 지시문 **ENABLE_WINMD_SUPPORT** WinRT에서 활용하는 코드를 래핑해야 합니다.

다음 코드 조각은 [유니버설 Windows 플랫폼: C# 스크립트의 WinRT API에](https://docs.unity3d.com/Manual/windowsstore-scripts.html)대한 Unity 수동 페이지에 있습니다. 이 예제에서는 광고 ID가 반환되지만 UWP 및 Xbox One 빌드에서만 반환됩니다.

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Unity C# 프로젝트에서 스크립트 편집

Unity 편집기에서 스크립트를 두 번 클릭하면 기본적으로 편집기 프로젝트에서 스크립트가 시작됩니다. Visual Studio 프로젝트에서 Windows 런타임을 참조하지 않으므로 WinRT API는 알 수 없는 것처럼 보입니다. **ENABLE_WINMD_SUPPORT** 지시문은 정의되지 않으며 *프로젝트를* UWP Visual Studio 솔루션으로 빌드할 때까지 #if 래핑된 코드가 무시됩니다.

## <a name="see-also"></a>추가 정보
* [Unity Visual Studio 솔루션 내보내기 및 빌드](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows 런타임 지원 Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)