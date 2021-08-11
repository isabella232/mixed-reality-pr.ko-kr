---
title: 홀로그램 DirectX 프로젝트 만들기
description: Windows Mixed Reality 앱 템플릿을 기반으로 새 holographic DirectX 앱을 만드는 방법에 대해 알아봅니다.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, holographic 앱, 새 앱, UWP 앱, 템플릿 앱, holograms, 새 프로젝트, 연습, 다운로드, 샘플 코드, 혼합 현실 헤드셋, Windows mixed Reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 7de7d73ec1e5fd8abde6d4822c86628e090fdf0cf89769fc9ef21311ff1aff15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200176"
---
# <a name="creating-a-holographic-directx-project"></a>홀로그램 DirectX 프로젝트 만들기

> [!NOTE]
> 이 문서는 레거시 WinRT 네이티브 Api와 관련이 있습니다.  새 네이티브 앱 프로젝트의 경우 **[OPENXR API](openxr-getting-started.md)** 를 사용 하는 것이 좋습니다.

HoloLens에 대해 만든 holographic 앱은 <a href="/windows/uwp/get-started/universal-application-platform-guide" target="_blank">UWP (유니버설 Windows 플랫폼) 앱</a>이 됩니다.  데스크톱 Windows Mixed Reality 헤드셋을 대상으로 하는 경우 UWP 앱 또는 Win32 앱을 만들 수 있습니다.

DirectX 11 holographic UWP 앱 템플릿은 DirectX 11 UWP 앱 템플릿과 매우 유사 합니다. 템플릿에는 프로그램 루프, Direct3D 장치 및 컨텍스트를 관리 하는 **DeviceResources** 클래스, 간소화 된 콘텐츠 렌더러 클래스가 포함 됩니다. 다른 UWP 앱과 마찬가지로 <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>도 있습니다.

그러나 혼합 현실 앱에는 일반적인 Direct3D UWP 앱에 없는 몇 가지 추가 기능이 있습니다. Windows Mixed Reality 앱 템플릿은 다음을 수행할 수 있습니다.
* Holographic 카메라와 연결 된 Direct3D 장치 리소스를 처리 합니다.
* 시스템에서 카메라 백 버퍼를 검색 합니다. Direct3D12의 경우 holographic 백 버퍼 리소스를 만들고 리소스 수명을 관리 합니다.
* [응시](../../design/gaze-and-commit.md) 입력을 처리 하 고 [제스처](../../design/gaze-and-commit.md#composite-gestures)를 인식 합니다.
* 전체 화면 스테레오 렌더링 모드로 전환 합니다.

## <a name="how-do-i-get-started"></a>시작하려면 어떻게 해야 하나요?

Visual Studio 2019 및 Windows Mixed Reality 앱 템플릿을 다운로드 하는 방법에 대 한 지침에 따라 먼저 [도구를 설치](../install-the-tools.md)합니다. 혼합 현실 앱 템플릿은 Visual Studio marketplace에서 [웹 다운로드](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)로 사용 하거나 Visual Studio UI를 통해 확장으로 설치 하 여 사용할 수 있습니다.

이제 DirectX 11 Windows Mixed Reality 앱을 만들 준비가 되었습니다. 샘플 콘텐츠를 제거 하려면 *pch* 에서 **DRAW_SAMPLE_CONTENT** 전처리기 지시문을 주석으로 처리 합니다.

## <a name="creating-a-uwp-project"></a>UWP 프로젝트 만들기

도구를 설치 하면] (. /install-the-tools.md) holographic DirectX UWP 프로젝트를 만들 수 있습니다.

Visual Studio 2019에서 새 프로젝트를 만들려면 다음을 수행 합니다.
1. **Visual Studio** 를 시작 합니다.
2. 오른쪽의 **시작** 섹션에서 **새 프로젝트 만들기** 를 선택 합니다.
3. **새 프로젝트 만들기** 대화 상자의 드롭다운 메뉴에서 **c + +**, **Windows Mixed Reality** 및 **UWP** 를 선택 합니다.
4. **Holographic DirectX 11 앱 (Universal Windows) (c + +/winrt)** 을 선택 합니다.
   ![Visual Studio 2019에서 Holographic DirectX 11 c + +/winrt UWP 앱 프로젝트 템플릿의 스크린샷](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *Visual Studio 2019의 Holographic DirectX 11 c + +/winrt UWP 앱 프로젝트 템플릿*
   >[!IMPORTANT]
   >프로젝트 템플릿의 이름에 "(c + +/WinRT)"가 포함 되어 있어야 합니다.  그렇지 않으면 이전 버전의 holographic 프로젝트 템플릿이 설치 되어 있는 것입니다.  최신 프로젝트 템플릿을 가져오려면 Visual Studio 2019에 대 한 확장으로 [설치](../install-the-tools.md) 합니다.
5. **새로 만들기** 를 선택합니다.
5. **Project 이름** 및 **위치** 텍스트 상자를 입력 하 고 **만들기** 를 선택 하거나 탭 합니다. Holographic app 프로젝트가 생성 됩니다.
6. HoloLens 2만을 대상으로 하는 개발의 경우 **대상 버전** 및 **최소 버전이** **Windows 10 버전 1903** 으로 설정 되어 있는지 확인 합니다.  HoloLens (첫 번째 gen) 또는 데스크톱 Windows Mixed Reality 헤드셋도 대상으로 지정 하는 경우 **최소 버전** 을 **Windows 10, 버전 1809** 로 설정할 수 있습니다. HoloLens 2의 새 기능을 사용 하는 경우 코드에서 일부 <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">버전 적응 검사가</a> 필요 합니다.
   ![Windows 10, 버전 1903을 대상으로 설정 하 고 최소 버전으로 설정 하는 스크린샷](images/new-uwp-project.png)<br>
   ***Windows 10, 버전 1903을** 대상 및 최소 버전으로 설정*
   >[!IMPORTANT]
   >**Windows 10, 버전 1903** 가 표시 되지 않으면 최신 Windows 10 SDK가 설치 되어 있지 않은 것입니다.  이 옵션을 표시 하려면 <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">Windows 10 SDK 버전 10.0.18362.0 이상을 설치</a>합니다.

Visual Studio 2017에서 새 프로젝트를 만들려면 다음을 수행 합니다.
1. **Visual Studio** 를 시작 합니다.
2. **파일** 메뉴에서 **새로 만들기** 를 가리킨 다음 상황에 맞는 메뉴에서 **Project** 를 선택 합니다. **새 프로젝트** 대화 상자가 열립니다.
3. 왼쪽에서 **설치** 를 확장 하 고 **Visual C++** 언어 노드를 확장 합니다.
4. **Windows Universal > Holographic** 노드로 이동 하 고 **Holographic DirectX 11 App (Universal Windows) (c + +/winrt)** 을 선택 합니다.
   ![Visual Studio 2017에서 Holographic DirectX 11 c + +/winrt UWP 앱 프로젝트 템플릿의 스크린샷](images/holographic-directx-app-cpp-new-project.png)<br>
   *Visual Studio 2017의 Holographic DirectX 11 c + +/winrt UWP 앱 프로젝트 템플릿*
   >[!IMPORTANT]
   >프로젝트 템플릿의 이름에 "(c + +/WinRT)"가 포함 되어 있어야 합니다.  그렇지 않으면 이전 버전의 holographic 프로젝트 템플릿이 설치 되어 있는 것입니다.  최신 프로젝트 템플릿을 가져오려면 Visual Studio 2017에 대 한 확장으로 [설치](../install-the-tools.md) 합니다.
5. **이름** 및 **위치** 텍스트 상자를 입력 하 고 **확인** 을 선택 하거나 탭 합니다. Holographic app 프로젝트가 생성 됩니다.
6. HoloLens 2만을 대상으로 하는 개발의 경우 **대상 버전** 및 **최소 버전이** **Windows 10 버전 1903** 으로 설정 되어 있는지 확인 합니다.  HoloLens (첫 번째 gen) 또는 데스크톱 Windows Mixed Reality 헤드셋도 대상으로 지정 하는 경우 **최소 버전** 을 **Windows 10, 버전 1809** 로 설정할 수 있습니다. HoloLens 2의 새 기능을 사용 하는 경우 코드에서 일부 <a href="/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">버전 적응 검사가</a> 필요 합니다.
   ![Windows 10, 버전 1903을 대상으로 설정 하 고 최소 버전으로 설정 하는 스크린샷](images/new-uwp-project.png)<br>
   ***Windows 10, 버전 1903을** 대상 및 최소 버전으로 설정*
   >[!IMPORTANT]
   >**Windows 10, 버전 1903** 가 표시 되지 않으면 최신 Windows 10 SDK가 설치 되어 있지 않은 것입니다.  이 옵션을 표시 하려면 <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">Windows 10 SDK 버전 10.0.18362.0 이상을 설치</a>합니다.

템플릿은 표준 규격 c + + 17 컴파일러를 지 원하는 Windows 런타임 api의 c + + 17 언어 <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">프로젝션을 사용 하</a>여 프로젝트를 생성 합니다.  이 프로젝트에서는 사용자 로부터 2 미터 배치 된 전 세계 잠긴 큐브를 만드는 방법을 보여 줍니다. 사용자는 컨트롤러의 단추를 [클릭 하거나 눌러](../../design/gaze-and-commit.md#composite-gestures) 사용자의 [응시](../../design/gaze-and-commit.md)에 지정 된 다른 위치에 큐브를 배치할 수 있습니다. 이 프로젝트를 수정 하 여 혼합 현실 앱을 만들 수 있습니다.

SharpDX를 기반으로 하는 **Visual c #** holographic 프로젝트 템플릿을 사용 하 여 새 프로젝트를 만들 수도 있습니다.  holographic c # 프로젝트가 Windows holographic 앱 템플릿에서 시작 되지 않은 경우 Windows Mixed Reality c # 템플릿 프로젝트에서 fxcompile 파일을 복사한 후 .csproj 파일에 가져와서 프로젝트에 추가 하는 HLSL 파일을 컴파일해야 합니다. Direct3D 12 템플릿은 Visual Studio에 대 한 Windows Mixed Reality 앱 템플릿 확장에도 제공 됩니다.

[Visual Studio 사용 하 여](../platform-capabilities-and-apis/using-visual-studio.md) 샘플을 빌드 및 배포 하는 방법에 대 한 정보를 검토 하 고 HoloLens, 몰입 형 장치가 연결 된 PC 또는 에뮬레이터를 검토 합니다.

아래 지침의 나머지 부분에서는 c + +를 사용 하 여 앱을 빌드하는 것으로 가정 합니다.

### <a name="uwp-app-entry-point"></a>UWP 앱 진입점

Holographic UWP 앱은 AppView .cpp의 **Wwinmain** 함수에서 시작 합니다. **Wwinmain** 함수는 앱의 <a href="/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> 를 만들고이를 사용 하 여 <a href="/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> 를 시작 합니다.

**Appview .cpp** 에서:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

이 시점부터 appview 클래스는 Windows 기본 입력 이벤트, CoreWindow 이벤트 및 메시지와의 상호 작용을 처리 합니다. 또한 앱에서 사용 하는 HolographicSpace를 만듭니다.

## <a name="creating-a-win32-project"></a>Win32 프로젝트 만들기

Win32 holographic 프로젝트 빌드를 시작 하는 가장 쉬운 방법은 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *basichologram* win32 샘플</a>을 조정 하는 것입니다.

이 Win32 샘플은 표준 규격 c + + 17 컴파일러를 지 원하는 Windows 런타임 api의 c + + 17 언어 프로젝션 인 <a href="/windows/uwp/cpp-and-winrt-apis/" target="_blank">c +</a>+ 17을 사용 합니다.  이 프로젝트에서는 사용자 로부터 2 미터 배치 된 전 세계 잠긴 큐브를 만드는 방법을 보여 줍니다. 사용자는 컨트롤러의 단추를 눌러 사용자의 [응시](../../design/gaze-and-commit.md)에 지정 된 다른 위치에 큐브를 배치할 수 있습니다. 이 프로젝트를 수정 하 여 혼합 현실 앱을 만들 수 있습니다.

### <a name="win32-app-entry-point"></a>Win32 앱 진입점

Holographic Win32 앱은 AppMain .cpp의 **Wwinmain** 함수에서 시작 합니다. **Wwinmain** 함수는 응용 프로그램의 HWND를 만들고 메시지 루프를 시작 합니다.

**Appmain .cpp** 에서:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

이 시점부터 AppMain 클래스는 기본 창 메시지와의 상호 작용을 처리 합니다. 또한 앱에서 사용 하는 HolographicSpace를 만듭니다.

## <a name="render-holographic-content"></a>Holographic 내용 렌더링

프로젝트의 **Content** 폴더에는 [holographic 공간](getting-a-holographicspace.md)에 holograms를 렌더링 하기 위한 클래스가 포함 되어 있습니다. 템플릿의 기본 홀로그램은 사용자 로부터 2 미터 떨어진 회전 하는 큐브입니다. 이 큐브 그리기는 다음과 같은 주요 메서드를 포함 하는 **SpinningCubeRenderer** 에서 구현 됩니다.

|  방법  |  설명 | 
|----------|----------|
|  `CreateDeviceDependentResources` |  셰이더를 로드 하 고 큐브 메시를 만듭니다. | 
|  `PositionHologram` |  제공 된 <a href="/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>에 지정 된 위치에 홀로그램을 배치 합니다. | 
|  `Update` |  큐브를 회전 하 고 모델 매트릭스를 설정 합니다. | 
|  `Render` |  꼭 짓 점 및 픽셀 셰이더를 사용 하 여 프레임을 렌더링 합니다. | 

**셰이더** 하위 폴더에는 네 가지 기본 셰이더 구현이 있습니다.

|  셰이더  |  설명 | 
|----------|----------|
|  `GeometryShader.hlsl` |  기 하 도형을 수정 되지 않은 상태로 유지 하는 통과입니다. | 
|  `PixelShader.hlsl` |  색 데이터를 통과 합니다. 색 데이터는 래스터화 단계에서 보간된 후 픽셀에 할당 됩니다. | 
|  `VertexShader.hlsl` |  GPU에서 꼭 짓 점 처리를 수행 하기 위한 간단한 셰이더입니다. | 
|  `VPRTVertexShader.hlsl` |  GPU에서 꼭 짓 점 처리를 수행 하는 간단한 셰이더가 Windows Mixed Reality 스테레오 렌더링에 최적화 되어 있습니다. | 

`VertexShaderShared.hlsl` 와 사이에 공유 되는 공통 코드 `VertexShader.hlsl` 를 포함 `VPRTVertexShader.hlsl` 합니다.

참고: Direct3D 12 앱 템플릿에는도 포함 됩니다 `ViewInstancingVertexShader.hlsl` . 이 변형은 D3D12 선택적 기능을 사용 하 여 스테레오 이미지를 보다 효율적으로 렌더링 합니다.

셰이더는 프로젝트가 빌드되고 **SpinningCubeRenderer:: CreateDeviceDependentResources** 메서드에 로드 될 때 컴파일됩니다.

## <a name="interact-with-your-holograms"></a>Holograms와 상호 작용

사용자 입력은 <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> 인스턴스를 가져오고 <a href="/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">sourcepressed</a> 이벤트를 구독 하는 **SpatialInputHandler** 클래스에서 처리 됩니다. 그러면 공기 탭 제스처와 기타 공간 입력 이벤트를 검색할 수 있습니다.

## <a name="update-holographic-content"></a>Holographic 콘텐츠 업데이트

혼합 현실 앱은 기본적으로의 **업데이트** 메서드에서 구현 되는 게임 루프에서 업데이트 됩니다 `AppMain.cpp` . **Update** 메서드는 회전 큐브와 같은 장면 개체를 업데이트 하 고 최신 뷰 및 프로젝션 매트릭스를 가져오고 스왑 체인을 표시 하는 데 사용 되는 <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 개체를 반환 합니다.

의 **Render** 메서드는 `AppMain.cpp` 현재 앱 및 공간 위치 지정 상태에 따라 <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 을 사용 하 여 각 holographic 카메라에 현재 프레임을 렌더링 합니다.

## <a name="notes"></a>참고

이제 Windows Mixed Reality 앱 템플릿에서 스펙터 완화 플래그가 설정 된 (/Qspectre) 컴파일을 지원 합니다. 스펙터 완화가 사용 하도록 설정 된 구성을 컴파일하기 전에 스펙터-완화 된 버전의 Microsoft Visual C++ (MSVC) 런타임 라이브러리를 설치 해야 합니다. 스펙터-완화 된 c + + 라이브러리를 설치 하려면 Visual Studio 설치 관리자를 시작 하 고 **수정** 을 선택 합니다. **개별 구성 요소로** 이동 하 여 "스펙터"를 검색 합니다. 스펙터로 완화 된 코드를 컴파일하는 데 필요한 MSVC 버전 및 대상 플랫폼에 해당 하는 상자를 선택 하 고 **수정** 을 클릭 하 여 설치를 시작 합니다.

## <a name="see-also"></a>추가 정보
* [HolographicSpace 받기](getting-a-holographicspace.md)
* <a href="/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [DirectX의 렌더링](rendering-in-directx.md)
* [Visual Studio를 사용하여 앱 배포 및 디버깅](../platform-capabilities-and-apis/using-visual-studio.md)
* [HoloLens 에뮬레이터 사용](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [홀로그램 DirectX 앱에서 XAML 사용](../platform-capabilities-and-apis/using-xaml-with-holographic-directx-apps.md)