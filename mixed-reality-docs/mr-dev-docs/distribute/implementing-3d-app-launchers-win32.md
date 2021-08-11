---
title: 3D 앱 시작 관리자(Win32 앱) 구현
description: 시작 메뉴 및 홈 환경용 Win32 VR 앱 및 게임용 3D 앱 시작 관리자 및 로고를 만드는 방법을 알아봅니다.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, 로고, 아이콘, 모델링, 시작 관리자, 3D 시작 관리자, 타일, 라이브 큐브, win32, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 매니페스트
ms.openlocfilehash: 60eb4f543f287e833033c8e1852e2a85c6040d3c76455aadaca4b37c0a632573
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198769"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>3D 앱 시작 관리자(Win32 앱) 구현

> [!NOTE]
> 이 기능은 최신 [Windows 참가자](https://insider.windows.com) 항공편(RS5), 빌드 17704 이상인 PC에서만 사용할 수 있습니다.

[Windows Mixed Reality 홈은](../discover/navigating-the-windows-mixed-reality-home.md) 애플리케이션을 시작하기 전에 사용자가 시작하는 시작점입니다. 기본적으로 헤드셋 외부에서 몰입형 Win32 VR 앱 및 게임을 시작해야 하며, Windows Mixed Reality 시작 메뉴 "모든 앱" 목록에 표시되지 않습니다. 이 문서의 지침에 따라 3D 앱 시작 관리자를 구현하는 경우 Windows Mixed Reality 시작 메뉴 및 홈 환경 내에서 몰입형 Win32 VR 환경을 시작할 수 있습니다.

이는 Steam 외부에 분산된 몰입형 Win32 VR 환경의 경우에만 해당됩니다. [Steam을 통해 배포된](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)VR 환경의 경우 기본 시작 관리자를 사용하여 자동으로 "모든 앱" 목록의 [Windows Mixed Reality 시작 메뉴 SteamVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) 제목이 표시되도록 최신 Windows Insider RS5 항공편과 함께 SteamVR Beta에 대한 Windows Mixed Reality 업데이트했습니다. 즉, 이 문서에서 설명하는 메서드는 SteamVR 제목에 필요하지 않으며, SteamVR 베타 기능에 대한 Windows Mixed Reality 재정의됩니다.

## <a name="3d-app-launcher-creation-process"></a>3D 앱 시작 관리자 만들기 프로세스

3D 앱 시작 관리자를 만드는 세 가지 단계가 있습니다.
1. [디자인 및 개념](3d-app-launcher-design-guidance.md)
2. [모델링 및 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 애플리케이션에 통합(이 문서)

애플리케이션의 시작 관리자로 사용할 3D 자산은 호환성을 보장하기 위해 Windows Mixed Reality 작성 지침을 사용하여 [작성해야](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 합니다. 이 제작 사양을 충족하지 못하는 자산은 Windows Mixed Reality 홈에 렌더링되지 않습니다.

## <a name="configuring-the-3d-launcher"></a>3D 시작 관리자 구성

Win32 애플리케이션은 3D 앱 시작 관리자를 만드는 경우 Windows Mixed Reality 시작 메뉴 "모든 앱" 목록에 표시됩니다. 이렇게 하려면 다음 단계를 수행하여 3D 앱 시작 관리자 참조하는 [Visual Elements Manifest](/previous-versions/windows/apps/dn393983(v=win.10)) XML 파일을 만듭니다.

1. **3D 앱 시작 관리자 자산 GLB 파일을** 만듭니다(모델링 [및 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)참조).
2. 애플리케이션에 대한 **[Visual Elements 매니페스트를](/previous-versions/windows/apps/dn393983(v=win.10))** 만듭니다.
    1. [아래 샘플로](#sample-visual-elements-manifest)시작할 수 있습니다.  자세한 내용은 전체 [Visual Elements 매니페스트](/previous-versions/windows/apps/dn393983(v=win.10)) 설명서를 참조하세요.
    2. 앱에 대한 PNG/JPG/GIF를 통해 **Square150x150Logo** 및 **Square70x70Logo를** 업데이트합니다.
        * Windows Mixed Reality 모든 앱 목록에서 앱의 2D 로고와 바탕 화면의 시작 메뉴에 사용됩니다.
        * 파일 경로는 Visual Elements 매니페스트가 포함된 폴더를 기반으로 하며,
        * 표준 메커니즘을 통해 앱에 대한 바탕 화면 시작 메뉴 아이콘을 제공해야 합니다. 실행 파일 또는 직접 만든 바로 가기에 있을 수 있습니다. 예를 들어 IShellLink::SetIconLocation을 통해 수행합니다.
        * *선택 사항:* MRT에서 다양한 해상도 배율 및 고대비 테마에 대해 여러 자산 크기를 제공하려는 경우 resources.pri 파일을 사용할 수 있습니다.
    3. 3D 앱 시작 관리자 대한 GLB를 가리키도록 **MixedRealityModel 경로를** 업데이트합니다.
    4. 실행 파일과 이름이 같은 파일을 ".VisualElementsManifest.xml" 확장명으로 저장하고 동일한 디렉터리에 저장합니다. 예를 들어 실행 파일 "contoso.exe"의 경우 함께 제공되는 XML 파일의 이름은 "contoso.visualelementsmanifest.xml"입니다.
3. **애플리케이션의 바로 가기를** 바탕 화면 Windows 시작 메뉴에 추가합니다. 예제 C++ 구현은 [아래 샘플을](#sample-app-launcher-shortcut-creation) 참조하세요. 
    * %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs(컴퓨터) 또는 %APPDATA%\Microsoft\Windows\Start Menu\Programs(사용자)에서 만듭니다.
    * 업데이트에서 시각적 요소 매니페스트 또는 이 매니페스트가 참조하는 자산을 변경하는 경우 업데이트 관리자 또는 설치 관리자가 바로 가기를 업데이트하여 매니페스트를 재분석하고 캐시된 자산을 업데이트해야 합니다.
4. *선택 사항:* 바탕 화면 바로 가기가 애플리케이션의 EXE를 직접 가리키지 않는 경우(예: "myapp://"과 같은 사용자 지정 프로토콜 처리기를 호출하는 경우) 시작 메뉴는 앱의 VisualElementsManifest.xml 파일을 자동으로 찾지 않습니다. 이 문제를 해결하려면 바로 가기에서 System.AppUserModel.VisualElementsManifestHintPath()를 사용하여 Visual Elements 매니페스트의 파일 경로를 지정해야 합니다. System.AppUserModel.ID 동일한 기술을 사용하여 바로 가기에서 설정할 수 있습니다. System.AppUserModel.ID 사용할 필요는 없지만 바로 가기를 사용하는 경우 애플리케이션의 명시적 애플리케이션 사용자 모델 ID와 일치하도록 할 수 있습니다.  C++ [샘플은](#sample-app-launcher-shortcut-creation) 아래 샘플 앱 시작 관리자 바로 가기 만들기 섹션을 참조하세요.

### <a name="sample-visual-elements-manifest"></a>샘플 시각적 요소 매니페스트

```xml
<Application xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a>샘플 앱 시작 관리자 바로 가기 만들기

아래 샘플 코드에서는 Visual Elements 매니페스트 XML 파일의 경로를 재정의하는 것을 포함하여 C++에서 바로 가기를 만드는 방법을 보여 드립니다. 재정의는 바로 가기가 매니페스트와 연결된 EXE를 직접 가리키지 않는 경우에만 필요합니다(예: 바로 가기는 "myapp://"과 같은 사용자 지정 프로토콜 처리기를 사용함).

#### <a name="sample-lnk-shortcut-creation-c"></a>샘플. LNK 바로 가기 만들기(C++)

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a>샘플. URL 시작 관리자 바로 가기 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a>추가 정보

* 3D 앱 시작 관리자를 포함하는 [혼합 현실 모델 샘플입니다.](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)
* [3D 앱 시작 관리자 디자인 지침](3d-app-launcher-design-guidance.md)
* [Windows Mixed Reality 홈에 사용할 3D 모델 만들기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [3D 앱 시작 관리자 구현(UWP 앱)](implementing-3d-app-launchers.md)
* [Windows Mixed Reality 홈 탐색](../discover/navigating-the-windows-mixed-reality-home.md)