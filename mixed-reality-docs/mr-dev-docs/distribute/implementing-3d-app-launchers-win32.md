---
title: 3D 앱 시작 관리자(Win32 앱) 구현
description: 시작 메뉴 및 홈 환경에 대해 Win32 VR 앱 및 게임에 대 한 3D 앱 시작 및 로고를 만드는 방법에 대해 알아봅니다.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, 로고, 아이콘, 모델링, 시작 관리자, 3D 시작 관리자, 타일, 라이브 큐브, win32, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 매니페스트
ms.openlocfilehash: 63b07664cb09f51e6d0588fdc50d141ad8985093
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009672"
---
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="0c62f-104">3D 앱 시작 관리자(Win32 앱) 구현</span><span class="sxs-lookup"><span data-stu-id="0c62f-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="0c62f-105">이 기능은 최신 [Windows 참가자](https://insider.windows.com) 항공편 (RS5), 빌드 17704 이상 버전을 실행 하는 pc 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="0c62f-106">[Windows Mixed Reality 홈](../discover/navigating-the-windows-mixed-reality-home.md) 은 사용자가 응용 프로그램을 시작 하기 전에 수행 하는 시작 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-106">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="0c62f-107">기본적으로 헤드셋 외부에서 모던 Win32 VR 앱과 게임을 시작 해야 하며 Windows Mixed Reality 시작 메뉴의 "모든 앱" 목록에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-107">By default, you need to launch immersive Win32 VR apps and games from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="0c62f-108">이 문서의 지침에 따라 3D 앱 시작 관리자를 구현 하는 경우 Windows Mixed Reality 시작 메뉴 및 홈 환경에서 몰입 형 Win32 VR 환경을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-108">If you follow the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="0c62f-109">이는 스트림 외부에 배포 되는 모던 Win32 VR 환경에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-109">This is only true for immersive Win32 VR experiences distributed outside of Steam.</span></span> <span data-ttu-id="0c62f-110">[스트림를 통해 배포](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)되는 VR 환경의 경우 [SteamVR Beta에 대 한 windows mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) 를 최신 windows 참가자 RS5 항공편과 함께 업데이트 하 여 기본 시작 관리자를 사용 하 여 자동으로 "모든 앱" 목록의 windows mixed Reality 시작 메뉴에 SteamVR 제목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-110">For VR experiences [distributed through Steam](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="0c62f-111">즉,이 문서에서 설명 하는 메서드는 SteamVR 제목에는 필요 하지 않으며 SteamVR Beta 기능을 위해 Windows Mixed Reality에 의해 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="0c62f-112">3D 앱 시작 관리자 만들기 프로세스</span><span class="sxs-lookup"><span data-stu-id="0c62f-112">3D app launcher creation process</span></span>

<span data-ttu-id="0c62f-113">3D 앱 시작 관리자를 만드는 세 가지 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-113">There are three steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="0c62f-114">디자인 및 concepting</span><span class="sxs-lookup"><span data-stu-id="0c62f-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="0c62f-115">모델링 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="0c62f-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="0c62f-116">응용 프로그램에 통합 (이 문서)</span><span class="sxs-lookup"><span data-stu-id="0c62f-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="0c62f-117">응용 프로그램에 대 한 관리자로 사용할 3D 자산은 호환성을 보장 하기 위해 [Windows Mixed Reality 제작 지침](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 을 사용 하 여 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="0c62f-118">이 제작 사양을 충족 하지 못하는 자산은 Windows Mixed Reality 홈에서 렌더링 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-118">Assets that fail to meet this authoring specification won't be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="0c62f-119">3D 시작 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="0c62f-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="0c62f-120">Win32 응용 프로그램은 3D 앱 시작 관리자를 만드는 경우 Windows Mixed Reality 시작 메뉴의 "모든 앱" 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="0c62f-121">이렇게 하려면 다음 단계를 수행 하 여 3D 앱 시작 관리자를 참조 하는 [시각적 요소 매니페스트](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="0c62f-122">**3D 앱 시작 관리자 자산 및 파일** 만들기 ( [모델링 및 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)참조)</span><span class="sxs-lookup"><span data-stu-id="0c62f-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="0c62f-123">응용 프로그램에 대 한 **[시각적 요소 매니페스트](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="0c62f-124">[아래 샘플](#sample-visual-elements-manifest)에서 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="0c62f-125">자세한 내용은 전체 [시각적 요소 매니페스트](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0c62f-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="0c62f-126">**Square150x150Logo** 및 **Square70x70Logo** 를 앱에 대 한 PNG/JPG/GIF로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="0c62f-127">이러한 응용 프로그램은 Windows Mixed Reality의 모든 앱 목록과 데스크톱의 시작 메뉴에서 앱의 2D 로고에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="0c62f-128">파일 경로는 시각적 요소 매니페스트를 포함 하는 폴더를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-128">The file path is based on the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="0c62f-129">표준 메커니즘을 통해 앱에 대 한 바탕 화면 시작 메뉴 아이콘을 계속 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="0c62f-130">이 파일은 실행 파일 또는 사용자가 만드는 바로 가기에서 직접 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-130">This can either be directly in the executable or in the shortcut you create.</span></span> <span data-ttu-id="0c62f-131">예: IShellLink:: SetIconLocation을 통해.</span><span class="sxs-lookup"><span data-stu-id="0c62f-131">For example, via IShellLink::SetIconLocation.</span></span>
        * <span data-ttu-id="0c62f-132">*선택 사항:* MRT.LOG에서 다양 한 해상도 크기 조정 및 고대비 테마에 대 한 여러 자산 크기를 제공 하려는 경우에는 리소스 .pri 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-132">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="0c62f-133">3D 앱 시작 관리자에 대 한 지 수 b를 가리키도록 **MixedRealityModel 경로** 를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-133">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="0c62f-134">".VisualElementsManifest.xml" 확장명을 사용 하 여 실행 파일과 이름이 같은 파일을 저장 하 고 동일한 디렉터리에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-134">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="0c62f-135">예를 들어 실행 파일 "contoso.exe"의 경우 함께 제공 된 XML 파일의 이름은 "contoso.visualelementsmanifest.xml"입니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-135">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="0c62f-136">응용 프로그램의 **바로 가기를** 바탕 화면 Windows 시작 메뉴에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-136">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="0c62f-137">예제 c + + 구현은 [아래 샘플](#sample-app-launcher-shortcut-creation) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0c62f-137">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="0c62f-138">%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) 또는%APPDATA%\Microsoft\Windows\Start Menu\Programs (사용자)에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-138">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="0c62f-139">업데이트에서 시각적 요소 매니페스트 또는이를 참조 하는 자산을 변경 하는 경우 매니페스트가 다시 구문 분석 캐시 된 자산이 업데이트 되도록 업데이트 프로그램 또는 설치 관리자에서 바로 가기를 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-139">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="0c62f-140">*선택 사항:* 바탕 화면 바로 가기가 응용 프로그램의 EXE를 직접 가리키지 않는 경우 (예: "myapp://"와 같은 사용자 지정 프로토콜 처리기를 호출 하는 경우) 시작 메뉴에서 앱의 VisualElementsManifest.xml 파일을 자동으로 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-140">*Optional:* If your desktop shortcut doesn't point directly to your application’s EXE (for example, if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="0c62f-141">이 문제를 해결 하려면 바로 가기에서 VisualElementsManifestHintPath ()를 사용 하 여 시각적 요소 매니페스트의 파일 경로를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-141">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="0c62f-142">System.AppUserModel.ID와 동일한 기법을 사용 하 여 바로 가기에서 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-142">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="0c62f-143">System.AppUserModel.ID를 사용할 필요는 없지만 응용 프로그램의 명시적인 응용 프로그램 사용자 모델 ID (사용 되는 경우)와 일치 하는 바로 가기가 있으면이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-143">You aren't required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="0c62f-144">C + + 샘플은 아래의 [샘플 앱 시작 관리자 바로 가기 생성](#sample-app-launcher-shortcut-creation) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0c62f-144">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="0c62f-145">샘플 시각적 요소 매니페스트</span><span class="sxs-lookup"><span data-stu-id="0c62f-145">Sample Visual Elements Manifest</span></span>

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

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="0c62f-146">샘플 앱 시작 관리자 바로 가기 만들기</span><span class="sxs-lookup"><span data-stu-id="0c62f-146">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="0c62f-147">아래 샘플 코드에서는 시각적 요소 매니페스트 XML 파일에 대 한 경로 재정의를 비롯 하 여 c + +에서 바로 가기를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-147">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="0c62f-148">이 재정의는 바로 가기가 매니페스트와 연결 된 EXE를 직접 가리키지 않는 경우에만 필요 합니다. 예를 들어 바로 가기에서 "myapp://"와 같은 사용자 지정 프로토콜 처리기를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-148">Note the override is only required in cases where your shortcut doesn't point directly to the EXE associated with the manifest (for example, your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="0c62f-149">샘플이. .LNK 바로 가기 만들기 (c + +)</span><span class="sxs-lookup"><span data-stu-id="0c62f-149">Sample .LNK shortcut creation (C++)</span></span>

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

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="0c62f-150">샘플이. URL 시작 관리자 바로 가기</span><span class="sxs-lookup"><span data-stu-id="0c62f-150">Sample .URL launcher shortcut</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="0c62f-151">참조</span><span class="sxs-lookup"><span data-stu-id="0c62f-151">See also</span></span>

* <span data-ttu-id="0c62f-152">3D 앱 시작 관리자를 포함 하는 [혼합 현실 모델 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) 입니다.</span><span class="sxs-lookup"><span data-stu-id="0c62f-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="0c62f-153">3D 앱 시작 관리자 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="0c62f-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="0c62f-154">Windows Mixed Reality 홈에서 사용할 3D 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="0c62f-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="0c62f-155">3D 앱 응용 프로그램 구현 (UWP 앱)</span><span class="sxs-lookup"><span data-stu-id="0c62f-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="0c62f-156">Windows Mixed Reality 홈 탐색</span><span class="sxs-lookup"><span data-stu-id="0c62f-156">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
