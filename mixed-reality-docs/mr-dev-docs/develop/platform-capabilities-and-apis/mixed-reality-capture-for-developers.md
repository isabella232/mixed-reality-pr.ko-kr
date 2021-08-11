---
title: 개발자를 위한 혼합 현실 캡처
description: 개발자를 위한 혼합 현실 캡처를 사용, 사용 및 렌더링 하기 위한 모범 사례에 대해 알아봅니다.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc, 사진, 비디오, 캡처, 카메라
ms.openlocfilehash: af585cd212ba8f2ddc3ea812c1fff2a5da8603bff0e77d8fc2ad794486821685
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192104"
---
# <a name="mixed-reality-capture-for-developers"></a>개발자를 위한 혼합 현실 캡처

> [!NOTE]
> HoloLens 2에 대 한 새 MRC 기능에 대 한 지침은 아래의 [PV 카메라에서 렌더링](#render-from-the-pv-camera-opt-in) 을 참조 하세요.

언제 든 지 [혼합 현실 캡처](/hololens/holographic-photos-and-videos) (mrc) 사진 또는 비디오를 사용할 수 있지만 응용 프로그램을 개발할 때는 몇 가지 사항을 염두에 두어야 합니다. 여기에는 MRC 시각적 품질에 대 한 모범 사례와 Mrc가 캡처될 때 시스템 변경 내용에 대 한 응답성이 포함 됩니다.

또한 개발자는 혼합 현실 캡처 및 삽입을 앱에 원활 하 게 통합할 수 있습니다.

mrc on HoloLens (처음 생성)은 720p까지 비디오와 사진을 지원 하 고, mrc HoloLens 2의 mrc는 최대 1080p까지 비디오를 지원 하 고 최대 4k 해상도의 사진을 지원 합니다.

## <a name="the-importance-of-quality-mrc"></a>품질 MRC의 중요도

Microsoft Store 페이지의 혼합 현실 스크린샷 또는 소셜 네트워크에서 콘텐츠 캡처를 공유 하는 다른 사용자의 경우, 혼합 현실 미디어 캡처는 사용자가 앱에 처음으로 노출 하는 경우가 많습니다. MRC를 사용 하 여 앱을 시연 하 고, 사용자를 교육 하 고, 혼합 세계 상호 작용을 공유 하 고, 사용자 연구 및 문제를 해결할 수 있습니다.

## <a name="how-mrc-impacts-your-app"></a>MRC가 앱에 미치는 영향

### <a name="enabling-mrc-in-your-app"></a>앱에서 MRC 사용

기본적으로 앱은 사용자가 혼합 된 현실 캡처를 수행할 수 있도록 하기 위해 아무것도 수행할 필요가 없습니다.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>앱에서 MRC에 대 한 향상 된 맞춤 사용

기본적으로 혼합 현실 캡처는 올바른 눈동자의 holographic 출력을 photo/video (PV) 카메라와 결합 합니다. 이러한 두 소스는 현재 실행 중인 몰입 형 앱에 의해 설정 된 포커스 지점을 사용 하 여 결합 됩니다.

즉, PV 카메라와 오른쪽 디스플레이 사이의 물리적인 거리가 holograms 면 포커스 평면 외부의이 정렬 되지 않습니다.

#### <a name="set-the-focus-point"></a>포커스 지점 설정

모던 앱 (HoloLens)은 안정화 평면을 원하는 곳의 [포커스 지점을](../unity/focus-point-in-unity.md) 설정 해야 합니다. 이렇게 하면 헤드셋과 혼합 현실 캡처 모두에서 최상의 맞춤을 보장 합니다.

포커스 지점이 설정 되지 않은 경우 안정화 평면의 기본값은 2 미터입니다.

#### <a name="render-from-the-pv-camera-opt-in"></a>PV 카메라에서 렌더링 (옵트인)

HoloLens 2는 혼합 현실 캡처가 실행 되는 동안에는 몰입 형 앱 **에서 렌더링** 하는 데 사용할 수 있는 기능을 추가 합니다. 앱이 추가 렌더링을 올바르게 지원 하도록 하려면 앱에서이 기능을 옵트인 해야 합니다.

PV 카메라의 렌더링은 기본 MRC 환경에 비해 다음과 같은 향상 된 기능을 제공 합니다.
* 홀로그램 맞춤은 실제 환경에 대 한 맞춤 이며 거의 상호 작용을 위한 손을 모든 거리에서 정확 하 게 지정 해야 합니다. 기본 MRC에서 볼 수 있는 것 처럼 포커스 지점이 아닌 거리에 오프셋을 두지 않습니다.
* V RC 출력에 대 한 holograms를 렌더링 하는 데 사용 되지 않으므로 헤드셋의 올바른 눈이 손상 되지 않습니다.

PV 카메라에서 렌더링을 사용 하도록 설정 하는 세 가지 단계가 있습니다.
1. PhotoVideoCamera HolographicViewConfiguration 사용
2. 추가 HolographicCamera render를 처리 합니다.
3. 이 추가 HolographicCamera에서 셰이더 및 코드가 올바르게 렌더링 되는지 확인 합니다.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a>DirectX에서 PhotoVideoCamera HolographicViewConfiguration 사용

PV 카메라에서 렌더링을 옵트인 (opt in) 하려면 앱에서 PhotoVideoCamera의 [HolographicViewConfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)을 사용 하도록 설정 하기만 하면 됩니다.
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>DirectX에서 추가 HolographicCamera render를 처리 합니다.

앱이 PV 카메라에서 렌더링 하도록 옵트인 (opt in) 하 고 혼합 현실 캡처를 시작 하면 다음을 수행 합니다.
1. HolographicSpace의 CameraAdded 이벤트가 발생 합니다. 지금은 앱에서 카메라를 처리할 수 없는 경우이 이벤트가 지연 될 수 있습니다.
2. 이벤트가 처리 되지 않은 상태로 완료 되 면 HolographicCamera는 다음 HolographicFrame의 Ad지연과 카메라 목록에 표시 됩니다.

혼합 현실 캡처가 중지 될 때 (또는 혼합 현실 캡처가 실행 되는 동안 앱에서 보기 구성을 사용 하지 않도록 설정 하는 경우) HolographicCamera는 다음 HolographicFrame의 RemovedCameras 목록에 표시 되 고 HolographicSpace의 CameraRemoved 이벤트가 발생 합니다.

HolographicCamera에는 카메라가 속한 구성을 식별 하는 데 도움이 되는 [Viewconfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) 속성이 추가 되었습니다.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a>Unity에서 PhotoVideoCamera HolographicViewConfiguration 사용

> [!NOTE]
> Unity 2018를 사용 하는 경우 **unity 2018.4.13 f1** 이상이 필요 합니다. Unity 2019을 사용 하는 경우 **unity 2019.4** 이상이 필요 합니다.

[혼합 현실 Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)사용 하는 경우 pv 카메라에서 렌더링을 옵트인 (opt in) 하려면 [Windows Mixed Reality 카메라 설정](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings) 공급자를 사용 하도록 설정 하 고 **pv 카메라에서 렌더링** 을 선택 합니다.

혼합 현실 Toolkit를 사용 하지 않는 경우 DirectX에 대해 위에서 설명한 대로 구성 요소를 사용 하 여 [수동으로 옵트인 (opt in)](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) 할 수 있습니다.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Unity에서 추가 HolographicCamera render를 처리 합니다.

Unity에서 자동으로 수행 됩니다.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a>Unreal에서 PhotoVideoCamera HolographicViewConfiguration 사용

> [!NOTE]
> 여기에는 **Unreal Engine 4.25** 이상이 필요합니다.

PV 카메라에서 렌더링하도록 옵트인하려면 다음을 수행합니다.

1. **SetEnabledMixedRealityCamera** 및 **ResizeMixedRealityCamera** 호출
    * **크기 X** 및 **크기 Y** 값을 사용하여 비디오 크기를 설정합니다.

![세 번째 카메라](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a>Unreal에서 추가 HolographicCamera 렌더링 처리

이 작업은 자동으로 수행 됩니다.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>셰이더 및 코드에서 추가 카메라 지원 확인

혼합 현실 캡처를 실행 하 고 비정상적인 맞춤, 누락 된 콘텐츠 또는 성능 문제를 확인 합니다. 셰이더 및 코드를 적절 하 게 업데이트 합니다.

추가 카메라에 대 한 렌더링을 지원 하지 않는 특정 장면이 있는 경우 PhotoVideoCamera의 HolographicViewConfiguration을 사용 하지 않도록 설정할 수 있습니다.

### <a name="disabling-mrc-in-your-app"></a>앱에서 MRC를 사용 하지 않도록 설정

#### <a name="2d-app"></a>2D 앱

혼합 현실 캡처가를 실행 하는 경우 2D 앱은 시각적 콘텐츠를 가립니다 선택할 수 있습니다.
* [DXGI_PRESENT_RESTRICT_TO_OUTPUT](/windows/desktop/direct3ddxgi/dxgi-present) 플래그로 제공
* [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) 플래그를 사용 하 여 앱의 스왑 체인 만들기
* Windows 10 2019년 5월 업데이트를 사용 하 여 applicationview의 [IsScreenCaptureEnabled](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) 을 설정 합니다.

#### <a name="immersive-app"></a>몰입 형 앱

몰입 형 앱은 다음과 같은 방법으로 혼합 현실 캡처에서 해당 시각적 콘텐츠를 제외 하도록 선택할 수 있습니다.
* HolographicCameraRenderingParameter의 [IsContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) 을 설정 하 여 연결 된 프레임에 대 한 혼합 현실 캡처 사용 안 함
* 연결 된 holographic 카메라에 대해 혼합 현실 캡처를 사용 하지 않도록 HolographicCamera의 [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) 설정

#### <a name="password-keyboard"></a>암호 키보드

Windows 10 2019년 5월 업데이트를 사용 하면 암호나 pin 키보드를 볼 때 시각적 콘텐츠가 혼합 현실 캡처에서 자동으로 제외 됩니다.

### <a name="knowing-when-mrc-is-active"></a>MRC가 활성 상태인 경우 파악

앱에서 [appcapture](/uwp/api/Windows.Media.Capture.AppCapture) 클래스를 사용 하 여 시스템 혼합 현실 캡처가 실행 되는 시기 (오디오 또는 비디오)를 알 수 있습니다.

>[!NOTE]
>AppCapture의 [GetForCurrentView](/uwp/api/windows.media.capture.appcapture.getforcurrentview) API는 장치에서 혼합 현실 캡처를 사용할 수 없는 경우 null을 반환할 수 있습니다. 앱이 일시 중단 될 때 CapturingChanged 이벤트의 등록을 취소 하는 것도 중요 합니다. 그렇지 않으면 MRC가 차단 된 상태가 될 수 있습니다.

### <a name="best-practices-hololens-specific"></a>모범 사례 (HoloLens 관련)

MRC는 추가 개발 작업 없이 작동할 것으로 예상 되지만, 최상의 혼합 현실 캡처 환경을 제공할 때 알아두어야 할 몇 가지 사항이 있습니다.

**MRC는 홀로그램의 알파 채널을 사용 하 여 [카메라](locatable-camera.md) 이미지와 혼합 합니다.**

가장 중요 한 단계는 불투명 검정을 지우지 않고 앱이 투명 검정을 선택 취소 하 고 있는지 확인 하는 것입니다. Unity에서는 기본적으로 MixedRealityToolkit을 사용 하 여이 작업을 수행 합니다. 비 Unity에서 개발 하는 경우 한 줄의 변경 작업을 수행 해야 할 수 있습니다.

앱이 투명 검정을 지우지 않는 경우 MRC에 표시 될 수 있는 아티팩트는 다음과 같습니다.

**예제 실패**: 콘텐츠 주위의 검은색 가장자리 (투명 검정으로 지우지 못함)

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failure to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**예제 실패**: 홀로그램의 전체 배경 장면이 검은색으로 표시 됩니다. 배경 알파 값을 1로 설정 하면 검은색 배경이 발생 합니다.

![배경 알파 값을 1로 설정 하면 검은색 배경이 발생 합니다.](images/clearopaqueblack-300px.png)

**예상 결과**: 실제 세계와 제대로 혼합 된 홀로그램스 표시 됩니다 (투명 검정으로 지우는 경우 예상 결과).

![투명 검정으로 지우는 경우 예상 결과](images/cleartransparentblack-300px.png)

**솔루션**:
* 알파 값이 0 인 불투명 검정으로 표시 되는 모든 콘텐츠를 변경 합니다.
* 앱이 투명 검정으로 선택 취소 되어 있는지 확인 합니다.
* Unity는 기본적으로 MixedRealityToolkit를 사용 하 여 자동으로 제거 되지만 Unity가 아닌 앱 인 경우에는 ID3D11DeiceContext:: ClearRenderTargetView ()와 함께 사용 되는 색을 수정 해야 합니다. 불투명 검정 (0, 0, 0, 1)이 아닌 투명 한 검정 (0, 0, 0, 0)을 지울 수 있도록 하려고 합니다.

원하는 경우 이제 자산의 알파 값을 조정할 수 있지만 일반적으로 필요 하지 않습니다. 대부분의 경우에는 MRCs가 적절 하 게 보입니다. MRC는 미리 곱한 알파를 가정 합니다. 알파 값은 MRC 캡처에만 영향을 줍니다.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>HOLOLENS MRC를 사용하도록 설정하면 예상되는 일

다음은 달리 명시되지 않는 한 HoloLens(1세대) 및 HoloLens 2 모두에 적용됩니다.

* 시스템은 애플리케이션을 30Hz 렌더링으로 제한합니다. 이렇게 하면 앱이 일정한 예산 예약을 유지할 필요가 없고 MRC 비디오 레코드 프레임 속도 30fps와도 일치하도록 MRC가 실행되도록 몇 가지 헤드룸이 생성됩니다.
* MRC를 기록/스트리밍할 때 디바이스 오른쪽에 있는 홀로그램 콘텐츠가 "스파크라인"으로 표시될 수 있습니다. 텍스트를 읽기가 더 어려워지고 홀로그램 가장자리가 더 가변적으로 나타날 수 있습니다(이 손상 방지를 **HoloLens 2** 세 번째 카메라 렌더링에 옵트인(opt in)).
* MRC 사진 및 비디오는 애플리케이션이 사용하도록 설정한 경우 애플리케이션의 [포커스 지점을](../unity/focus-point-in-unity.md) 준수하므로 홀로그램이 정확하게 배치되도록 할 수 있습니다. 비디오의 경우 포커스 지점 깊이가 크게 변경될 경우 홀로그램이 느리게 드리프트되는 것처럼 보일 수 있도록 포커스 지점이 다듬어집니다. 포커스 지점과 다른 깊이의 홀로그램스 실제 세계의 오프셋으로 나타날 수 있습니다(포커스 지점이 2미터로 설정되어 있지만 홀로그램이 1미터에 배치되는 아래 예제 참조).

![2미터의 홀로그램스 전 세계에 완벽하게 등록되어 표시됩니다. 가까운 거리 또는 먼 거리에 홀로그램스 약간 오프셋될 수 있습니다.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>앱 내에서 MRC 기능 통합

혼합 현실 앱은 앱 내에서 MRC 사진 또는 비디오 캡처를 시작할 수 있으며, 캡처된 콘텐츠는 디바이스의 "카메라 롤"에 저장되지 않고 앱에서 사용할 수 있습니다. 사용자 지정 MRC 레코더를 만들거나 기본 제공 카메라 캡처 UI를 활용할 수 있습니다. 

### <a name="mrc-with-built-in-camera-ui"></a>기본 제공 카메라 UI가 있는 MRC

개발자는 카메라 *[캡처 UI API를](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 사용하여 몇 줄의 코드만으로 사용자가 캡처한 혼합 현실 사진 또는 비디오를 얻을 수 있습니다.

이 API는 사용자가 사진 또는 비디오를 촬영할 수 있는 기본 제공 MRC 카메라 UI를 시작하고 결과 캡처를 앱에 반환합니다. 스트림을 캡처하기 위해 사용자 지정 카메라 UI 또는 하위 수준 액세스를 추가해야 하는 경우 사용자 지정 혼합 현실 캡처 레코더를 만들 수 있습니다.

### <a name="creating-a-custom-mrc-recorder"></a>사용자 지정 MRC 레코더 만들기

사용자는 항상 시스템 MRC 캡처 서비스를 사용하여 사진 또는 비디오를 트리거할 수 있지만, 애플리케이션은 MRC와 마찬가지로 카메라 스트림에 홀로그램을 포함하는 사용자 지정 카메라 앱을 빌드할 수 있습니다. 이렇게 하면 애플리케이션이 사용자 입력에서 캡처를 시작하거나, 사용자 지정 기록 UI를 빌드하거나, MRC 설정을 사용자 지정하여 몇 가지 예제를 지정할 수 있습니다.

**HoloStudio MRC 효과를 사용하여 사용자 지정 MRC 카메라를 추가합니다.**

![HoloStudio MRC 효과를 사용하여 사용자 지정 MRC 카메라를 추가합니다.](images/cameraiconholostudio-300px.jpg)

Unity 애플리케이션에 대 [한 Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) 표시 해야 합니다 홀로그램을 사용 하도록 설정 하는 속성입니다.

다른 애플리케이션은 Windows 미디어 [캡처 API를](/uwp/api/Windows.Media.Capture.MediaCapture) 사용하여 카메라를 제어하고 MRC 비디오 및 오디오 효과를 추가하여 가상 홀로그램 및 애플리케이션 오디오를 정지 및 비디오에 포함함으로써 이 작업을 수행할 수 있습니다.

애플리케이션에는 효과를 추가하는 두 가지 옵션이 있습니다.
* 이전 API: [Windows. Media.Capture.MediaCapture.AddEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* 새 Microsoft 권장 API(개체를 반환하여 동적 속성을 조작할 수 있도록): [Windows. Media.Capture.MediaCapture.AddVideoEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [Windows. Media.Capture.MediaCapture.AddAudioEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) - 앱이 [IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) 및 [IAudioEffectDefinition](/uwp/api/windows.media.effects.iaudioeffectdefinition)의 자체 구현을 만들어야 합니다. 예제는 [MRC 샘플 앱을](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture) 참조하세요.

>[!NOTE]
> Windows. Media.MixedRealityCapture 네임스페이스는 Visual Studio 인식할 수 없지만 문자열은 여전히 유효합니다.

MRC 비디오 효과(**Windows. Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  속성 이름  |  형식  |  기본값  |  Description |
|----------|----------|----------|----------|
|  StreamType  |  UINT32([MediaStreamType](/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1(VideoRecord)  |  이 효과가 사용되는 캡처 스트림을 설명합니다. 오디오를 사용할 수 없습니다. |
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  비디오 캡처에서 홀로그램을 사용하거나 사용하지 않도록 설정하는 플래그입니다. |
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  홀로그램 캡처 중에 화면에 기록 표시기를 사용하거나 사용하지 않도록 설정하는 플래그입니다. |
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  HoloLens 추적기에서 구동하는 비디오 안정화를 사용하거나 사용하지 않도록 설정하는 플래그입니다. |
|  VideoStabilizationBufferLength  |  Uint32  |  0  |  비디오 안정화에 사용되는 기록 프레임의 개수를 설정합니다. 0은 0 대기 시간이고 성능 및 성능 측면에서 거의 "무료"입니다. 최고 품질의 경우 대기 시간 및 메모리가 15프레임인 경우 15를 권장합니다. |
|  GlobalOpacityCoefficient  |  float  |  0.9(HoloLens) 1.0(몰입형 헤드셋)  |  홀로그램의 전역 불투명도 계수를 0.0(완전 투명)에서 1.0(완전 불투명)으로 설정합니다. |
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  보호된 콘텐츠를 표시하는 2d UWP 앱이 있는 경우 빈 프레임 반환을 사용하거나 사용하지 않도록 설정하는 플래그입니다. 이 플래그가 false이고 2d UWP 앱이 보호된 콘텐츠를 표시하는 경우 2d UWP 앱은 헤드셋과 혼합 현실 캡처 모두에서 보호된 콘텐츠 질감으로 대체됩니다. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  홀로그램 카메라의 숨겨진 영역 메시 및 인접 콘텐츠를 표시하거나 사용하지 않도록 설정하는 플래그입니다. |
| OutputSize | 크기 | 0, 0 | 비디오 안정화를 위해 자른 후 원하는 출력 크기를 설정합니다. 0 또는 잘못된 출력 크기를 지정하면 기본 자르기 크기가 선택됩니다. |
| PreferredHologramPerspective | Uint32 | Windows 장치 포털 **카메라에서 렌더링** 설정 | 캡처해야 하는 홀로그램 카메라 보기 구성을 나타내는 데 사용되는 열거형: 0(표시)은 앱이 사진/비디오 카메라에서 렌더링하도록 요청하지 않는다는 것을 의미하며, 1(PhotoVideoCamera)은 앱이 사진/비디오 카메라에서 렌더링하도록 요청합니다(앱이 지원하는 경우). 에서만 지원 HoloLens 2 |

>[!NOTE]
> 혼합 현실 캡처 [페이지로](using-the-windows-device-portal.md#mixed-reality-capture) 가서 **카메라에서 렌더링** 을 선택 취소하여 Windows 장치 포털 **PreferredHologramPerspective의** 기본값을 변경할 수 있습니다. 설정의 기본값은 **1(PhotoVideoCamera)이지만** **0(표시) 으로** 설정하려면 선택 취소할 수 있습니다.
>
> **PreferredHologramPerspective의** 기본값은 **2020년 6월** 업데이트(Windows Holographic, 버전 2004 빌드 19041.1106 및 Holographic 버전 1903 빌드 18362.1064 Windows 이전의 0(표시)이었습니다.

MRC 오디오 효과(**Windows. Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

| 속성 이름 | 형식 | 기본값 | Description |
|----------|----------|----------|----------|
| MixerMode | Uint32 | 2(마이크 및 시스템 오디오) | 사용해야 하는 오디오 원본을 나타내는 데 사용되는 열거형: 0(마이크 오디오만), 1(시스템 오디오만), 2(마이크 및 시스템 오디오) |
| LoopbackGain | float | Windows 장치 포털 **앱 오디오 게인** 설정 | 시스템 오디오 볼륨에 적용할 게인입니다. 범위는 0.0에서 5.0까지입니다. 에서만 지원 HoloLens 2 |
| MicrophoneGain | float | Windows 장치 포털의 **마이크 오디오 게인** 설정 | 마이크 볼륨에 적용 됩니다. 범위는 0.0에서 5.0 사이입니다. HoloLens 2 에서만 지원 됨 |

>[!NOTE]
> [혼합 현실 캡처 페이지로](using-the-windows-device-portal.md#mixed-reality-capture) 이동 하 고 해당 설정 옆에 있는 슬라이더를 조정 하 여 Windows 장치 포털에서 **LoopbackGain** 또는 **MicrophoneGain** 의 기본값을 변경할 수 있습니다. 두 설정의 기본값은 모두 **1.0** 이지만 **0.0** 에서 **5.0** 사이의 값으로 설정할 수 있습니다.
>
> Windows Device Portal을 사용 하 여 기본 획득 값을 구성 하는 것은 6 월 2020 업데이트 (Windows Holographic, 버전 2004 빌드 19041.1106 및 Windows Holographic, 버전 1903 build 18362.1064)를 사용 하 여 추가 되었습니다.

### <a name="simultaneous-mrc-limitations"></a>동시 MRC 제한 사항

여러 앱에서 MRC에 동시에 액세스 하는 경우 특정 제한 사항을 알고 있어야 합니다.

#### <a name="photovideo-camera-access"></a>사진/비디오 카메라 액세스

HoloLens 1에서는 프로세스가 비디오를 기록 하거나 사진을 촬영 하는 동안 mrc가 사진을 캡처하거나 비디오를 캡처할 수 없습니다. 그 반대의 경우도 마찬가지입니다. MRC가 실행 중인 경우 응용 프로그램이 카메라에 액세스 하지 못합니다. 

HoloLens 2를 사용 하 여 카메라에 대 한 액세스를 공유할 수 있습니다. 해상도 또는 프레임 속도로 직접 제어 하지 않아도 되는 경우 Sharedmode를 사용 하는 [Sharedmode 속성](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) 을 사용 하 여 MediaCapture를 초기화할 수 있습니다.  

##### <a name="built-in-mrc-photovideo-camera-access"></a>기본 제공 MRC 사진/비디오 카메라 액세스

Windows 10에 기본 제공 되는 mrc 기능 (Cortana, 시작 메뉴, 하드웨어 바로 가기, Miracast, Windows 장치 포털):

* 기본적으로 ExclusiveControl를 사용 하 여 실행 됩니다.

그러나 공유 모드에서 작동 하도록 MRC 하위 시스템에 대 한 지원이 추가 되었습니다. 

* 앱이 photo/video 카메라에 대 한 ExclusiveControl 액세스를 요청 하는 경우 기본 제공 MRC는 앱의 요청이 성공 하도록 photo/video 카메라를 사용 하 여 자동으로 중지 됩니다. 
* 앱이 ExclusiveControl 된 상태에서 기본 제공 MRC를 시작 하면 기본 제공 MRC가 SharedReadOnly 모드에서 실행 됩니다. 

이 공유 모드 기능에는 다음과 같은 제한 사항이 있습니다.

* Cortana, 하드웨어 바로 가기 또는 시작 메뉴를 통한 사진: Windows 10 4 월 2018 업데이트 (이상)를 사용 해야 합니다.
* Cortana, 하드웨어 바로 가기 또는 시작 메뉴를 통한 비디오: Windows 10 4 월 2018 업데이트 (이상)를 사용 해야 합니다.
* Miracast를 통한 mrc 스트리밍: Windows 10 2018년 10월 업데이트 이상이 필요 합니다.
* Windows 장치 포털을 통해 또는 HoloLens 도우미 앱을 통해 mrc 스트리밍: HoloLens 2 필요

>[!NOTE]
> 다른 앱에서 photo/video 카메라를 사용 하는 경우 기본 제공 MRC 카메라 UI의 해상도 및 프레임 비율이 일반 값에서 감소할 수 있습니다.

#### <a name="mrc-access-for-developers"></a>개발자를 위한 MRC 액세스

MRC를 사용 하는 경우 항상 카메라에 대 한 단독 제어를 요청 하는 것이 좋습니다. 이렇게 하면 위에 나열 된 제한 사항을 알고 있는 한 응용 프로그램이 카메라의 설정에 대 한 모든 권한을 가집니다. 

* [초기화 설정을](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041) 사용 하 여 미디어 캡처 개체 만들기
* [SharingMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) 속성을 **exclusive** 로 설정 합니다.

> [!CAUTION]
> 계속 하기 전에 [SharingMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) 주의 사항을 주의 깊게 읽어야 합니다.

* 원하는 방식으로 카메라 설정
* 앱을 시작 하 고, 시작 API로 비디오 프레임을 캡처한 다음, MRC를 사용 하도록 설정 합니다.

> [!CAUTION]
> 앱을 시작 하기 전에 MRC를 시작 하면 기능이 예상 대로 작동 하는 것을 보장할 수 없습니다.

[Holographic face 추적 샘플](/samples/microsoft/windows-universal-samples/holographicfacetracking)에서 위의 프로세스에 대 한 전체 샘플을 찾을 수 있습니다.

> [!NOTE]
> 4 월 2018 업데이트 Windows 10 하기 전에는 앱의 사용자 지정 mrc 레코더를 시스템 mrc와 함께 사용할 수 없습니다 (사진 캡처, 비디오 캡처 또는 Windows 장치 포털에서 스트리밍).

## <a name="see-also"></a>참조

* [혼합 현실 캡처](/hololens/holographic-photos-and-videos)
* [Spectator View](spectator-view.md)
* [Unity 개발 개요](../unity/unity-development-overview.md)
* [Unreal 개발 개요](../unreal/unreal-development-overview.md)
