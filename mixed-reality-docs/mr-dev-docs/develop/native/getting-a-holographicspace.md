---
title: HolographicSpace 받기
description: 혼합 현실 앱에서 홀로그램 렌더링 및 공간 입력에 HolographicSpace API를 사용하는 방법을 알아봅니다.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, 공간 입력, 렌더링, 스왑 체인, 홀로그램 프레임, 업데이트 루프, 게임 루프, 참조 프레임, 찾기 기능, 샘플 코드, 연습, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 986ccdc6e81d1ac7c7b401a427da548218a68eb0352a0057bf7d7aba3c1d6d6a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212171"
---
# <a name="getting-a-holographicspace"></a>HolographicSpace 받기

> [!NOTE]
> 이 문서는 레거시 WinRT 네이티브 API와 관련이 있습니다.  새 네이티브 앱 프로젝트의 경우 **[OpenXR API](openxr-getting-started.md)** 를 사용하는 것이 좋습니다.

<a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> 클래스는 홀로그램 세계에 대한 포털입니다. 몰입형 렌더링을 제어하고, 카메라 데이터를 제공하고, 공간 추론 API에 대한 액세스를 제공합니다. UWP 앱의 <a href="/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> 또는 Win32 앱의 HWND용으로 만듭니다.

## <a name="set-up-the-holographic-space"></a>홀로그램 공간 설정

홀로그램 공간 개체를 만드는 것은 Windows Mixed Reality 앱을 만드는 첫 번째 단계입니다. 기존 Windows 앱은 애플리케이션 보기의 핵심 창에 대해 생성된 Direct3D 스왑 체인으로 렌더링됩니다. 이 스왑 체인은 홀로그램 UI의 슬레이트에 표시됩니다. 애플리케이션이 2D 슬레이트가 아닌 홀로그램 보기를 만들려면 스왑 체인 대신 코어 창에 대한 홀로그램 공간을 만듭니다. 이 홀로그램 공간에서 만든 홀로그램 프레임을 표시하면 앱이 전체 화면 렌더링 모드로 전환됩니다.

[ *Holographic DirectX 11 앱(유니버설 Windows) 템플릿에서* 시작하는](creating-a-holographic-directx-project.md) **UWP 앱의** 경우 AppView.cpp의 **SetWindow** 메서드에서 다음 코드를 찾습니다.

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

[ *BasicHologram* Win32 샘플부터 Win32](creating-a-holographic-directx-project.md#creating-a-win32-project) **앱을** 빌드하는 경우 **App::CreateWindowAndHolographicSpace에서** HWND 예제를 살펴보세요. 그런 다음 연결된 <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>를 만들어 몰입형 HWND로 변환할 수 있습니다.

```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

UWP CoreWindow 또는 Win32 HWND에 대한 HolographicSpace를 얻은 후 HolographicSpace는 홀로그램 카메라를 처리하고, 좌표계를 만들고, 홀로그램 렌더링을 수행할 수 있습니다. 현재 홀로그램 공간은 DirectX 템플릿의 여러 위치에 사용됩니다.
* **DeviceResources** 클래스는 Direct3D 디바이스를 만들려면 HolographicSpace 개체에서 일부 정보를 얻어야 합니다. 홀로그램 디스플레이와 연결된 DXGI 어댑터 ID입니다. <a href="/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> 클래스는 앱의 Direct3D 11 디바이스를 사용하여 각 홀로그램 카메라의 백 버퍼와 같은 디바이스 기반 리소스를 만들고 관리합니다. 이 함수가 수행하는 작업을 자세히 알아보려면 DeviceResources.cpp에서 찾을 수 있습니다.
* **DeviceResources::InitializeUsingHolographicSpace** 함수는 LUID를 검색하여 어댑터를 가져오는 방법과 기본 어댑터가 지정되지 않은 경우 기본 어댑터를 선택하는 방법을 보여 있습니다.
* 앱의 기본 클래스는 업데이트 및 렌더링을 위해 **AppView::SetWindow** 또는 **App::CreateWindowAndHolographicSpace의 홀로그램** 공간을 사용합니다.

>[!NOTE]
>아래 섹션에서는 홀로그램 UWP 앱 템플릿에서 시작했다고 가정하는 **AppView::SetWindow와** 같은 템플릿의 함수 이름을 언급하지만 표시되는 코드 조각은 UWP 및 Win32 앱에 동일하게 적용됩니다.

다음으로, AppMain 클래스에서 **SetHolographicSpace가** 담당하는 설정 프로세스를 자세히 살펴보겠습니다.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>카메라 이벤트 구독, 카메라 리소스 만들기 및 제거

앱의 홀로그램 콘텐츠는 홀로그램 공간에 있으며 장면에 대한 다양한 관점을 나타내는 하나 이상의 홀로그램 카메라를 통해 표시됩니다. 이제 홀로그램 공간이 생겼으므로 홀로그램 카메라에 대한 데이터를 받을 수 있습니다.

앱은 해당 카메라와 관련된 리소스를 만들어 **CameraAdded** 이벤트에 응답해야 합니다. 이러한 리소스의 예로 백 버퍼 렌더링 대상 보기가 있습니다. 앱이 홀로그램 프레임을 생성하기 전에 **AppView::SetWindow에서** 호출되는 **DeviceResources::SetHolographicSpace** 함수에서 이 코드를 볼 수 있습니다.

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

또한 앱은 해당 카메라에 대해 만들어진 리소스를 해제하여 **CameraRemoved** 이벤트에 응답해야 합니다.

**DeviceResources::SetHolographicSpace에서:**

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

이벤트 처리기는 홀로그램 렌더링이 원활하게 진행되고 앱이 렌더링되도록 일부 작업을 완료해야 합니다. 자세한 내용은 코드 및 주석을 읽어보세요. 기본 클래스에서 **OnCameraAdded** 및 **OnCameraRemoved를** 찾아 **deviceResources에서** **m_cameraResources** 맵을 처리하는 방법을 이해할 수 있습니다.

지금은 AppMain 및 앱이 홀로그램 카메라에 대해 알 수 있도록 설정하는 데 중점을 두고 있습니다. 이 점을 염두에 두고 다음 두 가지 요구 사항을 기록해 두는 것이 중요합니다.

1. **CameraAdded** 이벤트 처리기의 경우 앱이 비동기적으로 작동하여 새 홀로그램 카메라에 대한 리소스 만들기 및 자산 로드를 완료할 수 있습니다. 이 작업을 완료하는 데 프레임이 두 개 이상 걸리는 앱은 지연을 요청하고 비동기적으로 로드한 후 지연을 완료해야 합니다. [PPL 작업을](/cpp/parallel/concrt/parallel-patterns-library-ppl) 사용하여 비동기 작업을 수행할 수 있습니다. 앱은 이벤트 처리기를 종료하거나 지연을 완료할 때 해당 카메라에 즉시 렌더링할 준비가 되었는지 확인해야 합니다. 이벤트 처리기를 종료하거나 지연을 완료하면 앱이 이제 해당 카메라가 포함된 홀로그램 프레임을 받을 준비가 되었다는 것을 시스템에 알릴 수 있습니다.

2. 앱이 **CameraRemoved** 이벤트를 받으면 백 버퍼에 대한 모든 참조를 해제하고 함수를 즉시 종료해야 합니다. 여기에는 렌더링 대상 뷰 및 [IDXGIResource](/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)에 대한 참조를 보유할 수 있는 기타 리소스가 포함됩니다. 또한 **앱은 CameraResources::ReleaseResourcesForBackBuffer에** 표시된 대로 백 버퍼가 렌더링 대상으로 연결되지 않았는지 확인해야 합니다. 속도를 높이기 위해 앱은 백 버퍼를 해제한 다음, 작업을 시작하여 카메라에 대한 다른 해체 작업을 비동기적으로 완료할 수 있습니다. 홀로그램 앱 템플릿에는 이 용도로 사용할 수 있는 PPL 작업이 포함되어 있습니다.

>[!NOTE]
>추가되거나 제거된 카메라가 프레임에 표시되는 시기를 확인하려면 **HolographicFrame** [AddedCameras](/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) 및 [RemovedCameras](/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) 속성을 사용합니다.

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>홀로그램 콘텐츠에 대한 참조 프레임 만들기

HolographicSpace에서 렌더링하려면 앱의 콘텐츠가 [공간 좌표계에](coordinate-systems-in-directx.md) 배치되어야 합니다. 시스템은 홀로그램에 대한 좌표계를 설정하는 데 사용할 수 있는 두 개의 기본 참조 프레임을 제공합니다.

Windows Holographic에는 두 가지 종류의 참조 프레임, 즉 디바이스에 연결된 참조 프레임과 디바이스가 사용자 환경을 통해 이동할 때 고정된 상태로 유지되는 참조 프레임이 있습니다. 홀로그램 앱 템플릿은 기본적으로 고정 참조 프레임을 사용합니다. 이는 세계에서 잠긴 홀로그램을 렌더링하는 가장 간단한 방법 중 하나입니다.

고정 참조 프레임은 디바이스의 현재 위치 근처에서 위치를 안정화하도록 설계되었습니다. 즉, 디바이스의 주변 공간에 대해 자세히 알아보면 디바이스에서 더 많은 좌표가 사용자 환경을 기준으로 약간 드리프트할 수 있습니다. 고정 참조 프레임을 만드는 방법에는 [공간 단계에서](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)좌표계를 획득하거나 기본 <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>를 사용하는 두 가지 방법이 있습니다. 몰입형 헤드셋용 Windows Mixed Reality 앱을 만드는 경우 [권장되는](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)시작점은 공간 단계 입니다. 공간 단계에서는 플레이어가 몰입형 헤드셋을 사용하는 기능에 대한 정보도 제공합니다. 여기서는 기본 <a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>를 사용하는 방법을 보여줍니다.

공간 로케이터는 Windows Mixed Reality 디바이스를 나타내며 디바이스의 동작을 추적하고 해당 위치를 기준으로 이해할 수 있는 좌표계를 제공합니다.

**AppMain::OnHolographicDisplayIsAvailableChanged에서:**

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

앱이 시작될 때 고정 참조 프레임을 한 번 만듭니다. 이는 앱이 시작될 때 원본이 디바이스의 위치에 배치된 세계 좌표계를 정의하는 경우와 유사합니다. 이 참조 프레임은 디바이스와 함께 이동하지 않습니다.

**AppMain::SetHolographicSpace에서:**

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

모든 참조 프레임은 사용자의 환경과 관련하여 y축이 "위로"를 가리킵니다. Windows "오른쪽" 좌표계를 사용하므로 –z 축의 방향은 참조 프레임을 만들 때 디바이스가 지향하는 "정방향" 방향과 일치합니다.

>[!NOTE]
>앱에 개별 홀로그램의 정확한 배치가 필요한 경우 <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor를</a> 사용하여 개별 홀로그램을 실제 세계의 위치에 고정합니다. 예를 들어 사용자가 특별한 관심 지점을 나타내는 경우 공간 앵커를 사용합니다. 앵커 위치는 드리프트되지 않지만 조정할 수 있습니다. 기본적으로 앵커가 조정되면 수정이 발생한 후 다음 여러 프레임에서 위치가 쉽게 배치됩니다. 애플리케이션에 따라 이 문제가 발생하는 경우 다른 방식으로 조정을 처리할 수 있습니다(예: 홀로그램이 보기가 아닐 때까지 지연). <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> 속성 및 <a href="/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> 이벤트는 이러한 사용자 지정을 사용하도록 설정합니다.

## <a name="respond-to-locatability-changed-events"></a>찾기 기능 변경 이벤트에 응답

세계로 잠긴 홀로그램을 렌더링하려면 디바이스가 세계에서 자신을 찾아야 합니다. 환경 조건으로 인해 항상 가능한 것은 아니며, 그럴 경우 사용자는 추적 중단에 대한 시각적 표시를 예상할 수 있습니다. 이 시각적 표시는 전 세계에 고정되지 않고 디바이스에 연결된 참조 프레임을 사용하여 렌더링해야 합니다.

어떤 이유로든 추적이 중단되면 앱에서 알림을 요청할 수 있습니다. LocatabilityChanged 이벤트에 등록하여 디바이스가 세계에서 자신을 찾는 기능이 변경되면 감지합니다. **AppMain::SetHolographicSpace에서:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

그런 다음, 이 이벤트를 사용하여 홀로그램을 전 세계에 고정 렌더링할 수 없는 경우를 확인합니다.

## <a name="see-also"></a>추가 정보
* [DirectX의 렌더링](rendering-in-directx.md)
* [DirectX의 좌표계](coordinate-systems-in-directx.md)