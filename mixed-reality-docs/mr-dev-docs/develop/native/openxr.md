---
title: OpenXR
description: 이식 가능한 OpenXR API 표준을 사용 하 여 엔진을 빌드하고 Windows Mixed Reality 및 HoloLens 2 헤드셋에 배포 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, 로드맵, 확장, Khronos, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어
ms.openlocfilehash: 8374cda738cc5b257338728f7d777f546768e71b
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906839"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR는 <a href="https://www.khronos.org/" target="_blank">Khronos</a>의 오픈 로열티 없는 무료 API 표준으로, [혼합 현실 스펙트럼](../../discover/mixed-reality.md)에서 다양 한 장치에 대 한 기본 액세스를 포함 하는 엔진을 제공 합니다.

데스크톱의 Windows Mixed Reality 몰입형 헤드셋 또는 HoloLens 2에서 OpenXR을 사용하여 개발할 수 있습니다.  헤드셋에 액세스할 수 없는 경우 HoloLens 2 에뮬레이터 또는 Windows Mixed Reality 시뮬레이터를 대신 사용할 수 있습니다.

## <a name="why-openxr"></a>왜 OpenXR?

OpenXR를 사용 하 여 HoloLens 2와 같은 holographic 장치 및 데스크톱 Pc 용 Windows Mixed Reality 헤드셋과 같은 몰입 형 장치를 모두 대상으로 하는 엔진을 빌드할 수 있습니다. OpenXR를 사용 하면 다양 한 하드웨어 플랫폼에서 이식할 수 있는 코드를 작성할 수 있습니다.

OpenXR API는 로더를 사용 하 여 응용 프로그램을 헤드셋의 기본 플랫폼 지원에 직접 연결 합니다. 최종 사용자는 Windows Mixed Reality 또는 다른 헤드셋을 사용 하는지 여부에 상관 없이 최대 성능 및 최소 대기 시간을 얻을 수 있습니다.

## <a name="what-is-openxr"></a>OpenXR이란?

OpenXR API는 holographic 및 몰입 형 장치를 모두 대상으로 할 수 있는 엔진을 빌드하는 데 필요한 핵심 포즈 예측, 프레임 타이밍 및 공간 입력 기능을 제공 합니다.

OpenXR API에 대 한 자세한 내용은 OpenXR 1.0 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">사양</a>, <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API 참조</a>및 <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">빠른 참조 가이드</a>를 확인 하세요.  자세한 내용은 <a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 페이지</a>를 참조 하세요.

HoloLens 2의 전체 기능 집합을 대상으로 지정 하기 위해, OpenXR 1.0 코어 이외의 추가 기능 (예: OpenXR)을 사용 하도록 설정 하는 공급 업체 및 공급 업체별 확장을 사용 합니다. 자세한 내용은 올해 후반에 나오는 확장에서 아래의 [로드맵 섹션](#roadmap) 을 참조 하세요.

OpenXR는 혼합 현실 엔진이 아닙니다.  대신, OpenXR를 사용 하 여 Unity와 같은 엔진에서 이식 가능한 코드를 작성 한 후에는 해당 플랫폼을 기반으로 하는 사용자의 holographic 또는 모던 장치의 기본 플랫폼 기능에 액세스할 수 있습니다.

## <a name="roadmap"></a>로드맵

OpenXR 사양은 런타임 구현자가 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">기본 OpenXR 1.0 사양</a>에 정의 된 [핵심 기능](#what-is-openxr) 외에 추가 기능을 노출할 수 있도록 하는 확장 메커니즘을 정의 합니다.

OpenXR 확장에는 세 가지 종류가 있습니다.
* **공급 업체 확장 (예 `MSFT` :):** 하드웨어 또는 소프트웨어 기능에서 공급 업체별 혁신을 사용 하도록 설정 합니다.  모든 런타임 공급 업체는 언제 든 지 공급 업체 확장을 소개 하 고 제공할 수 있습니다.
  * **실험적 공급 업체 확장 (예 `MSFT_preview` :):** 피드백을 수집 하기 위해 미리 보는 실험적 공급 업체 확장입니다.  `MSFT_preview` 확장은 개발자 장치에만 해당 되며, 실제 확장이 제공 될 때 제거 됩니다.  실험을 위해 [개발자 장치에서 미리 보기 확장을 사용 하도록 설정할](openxr-getting-started.md#using-preview-extensions)수 있습니다.
* **교차 공급 업체 `EXT` 확장:** 여러 회사에서 정의 하 고 구현 하는 공급 업체 확장 프로그램입니다.  관심이 있는 회사 그룹은 언제 든 지 내선 내선 번호를 도입할 수 있습니다.
* **공식 `KHR` 확장:** 공식 Khronos 확장 비준 핵심 사양 릴리스의 일부로 구성 됩니다.  KHR 확장은 코어 사양 자체와 동일한 라이선스로 적용 됩니다.

Windows Mixed Reality OpenXR 런타임은 `MSFT` `EXT` HoloLens 2 기능의 전체 집합을 OpenXR 응용 프로그램으로 가져오는 및 확장 집합을 지원 합니다.

| 기능 영역 | 확장 가용성 |
|--------------|------------------------|
| 시스템 + 세션 | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [참조 공간 (보기, 로컬, 단계)](../../design/coordinate-systems.md) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| 구성 보기 (mono, 스테레오) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Swapchains](../platform-capabilities-and-apis/rendering.md)  +  [프레임 타이밍](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| 컴포지션 계층<br />(프로젝션, 쿼드) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Input 및 haptics](../../design/interaction-fundamentals.md) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Direct3D 11 통합 | **정식 `KHR` 확장 릴리스:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Direct3D 12 통합 | **정식 `KHR` 확장 릴리스:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [바인딩되지 않은 참조 공간 <br /> (세계 규모가 뛰어난 환경)](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` 확장 릴리스:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Spatial Anchors](../../design/spatial-anchors.md) | **`MSFT` 확장 릴리스:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [손으로 조작 <br /> (그립/aim 포즈, 공중 탭, 방법)](../../design/hands-and-tools.md)<p>*HoloLens 2만*</p> | **`MSFT` 확장 릴리스:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [손 모양 articulation + 손 모양](../../design/hands-and-tools.md)<p>*HoloLens 2만*</p> | <p>**`EXT` 런타임 102에서 릴리스된 확장:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` 런타임 102에서 릴리스된 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [응시](../../design/eye-tracking.md)<p>*HoloLens 2만*</p> | **`EXT` 확장 릴리스:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| 다른 HoloLens Sdk와의 상호 운용성<br />(예: [QR](../platform-capabilities-and-apis/qr-code-tracking.md))<p>*HoloLens 2만*</p> | <p>**`MSFT` 런타임 102에서 릴리스된 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` 런타임 105의 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_perception_anchor_interop">XR_MSFT_perception_anchor_interop</a></code></p> |
| [혼합 현실 캡처 <br /> (PV 카메라의 세 번째 렌더링)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*HoloLens 2만*</p> | **`MSFT` 런타임 102에서 릴리스된 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| UWP CoreWindow API와의 상호 운용성<br />(예를 들어 키보드/마우스의 경우) | **`MSFT` 런타임 103에서 릴리스된 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| 동작 컨트롤러 상호 작용 프로필<br />(Samsung Odyssey 및 HP 반향 G2) | **`MSFT` 런타임 103에서 릴리스된 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [동작 컨트롤러 렌더링 모델](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` 런타임 104에서 릴리스된 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [장면 이해 (평면, 메시)](../../design/scene-understanding.md)<p>*HoloLens 2만*</p> | <p>**런타임 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> [장면 이해 SDK](../platform-capabilities-and-apis/scene-understanding-sdk.md) 를 사용 하 여 사용</p><p>**`MSFT`[preview 런타임 105](openxr-getting-started.md#using-preview-extensions)의 확장:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_scene_understanding_preview2">XR_MSFT_scene_understanding_preview2</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_scene_understanding_serialization_preview">XR_MSFT_scene_understanding_serialization_preview</a></code></p> |
| [컴퍼지션 계층 reprojection 모드 <br /> (자동 평면 또는 방향-다시 프로젝션 전용)](../platform-capabilities-and-apis/hologram-stability.md#reprojection) | **`MSFT`[preview 런타임 105](openxr-getting-started.md#using-preview-extensions)의 확장:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_composition_layer_reprojection_preview">XR_MSFT_composition_layer_reprojection_preview</a></code> |
| 기타 교차 공급 업체 확장 | <p>**정식 `KHR` 확장 릴리스:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_color_scale_bias" target="_blank">XR_KHR_composition_layer_color_scale_bias</a></code><p>**`EXT` 릴리스된 확장:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

이러한 확장 중 일부는 공급 업체별 확장으로 시작 될 수 있지만 `MSFT` , Microsoft 및 기타 OpenXR runtime 공급 업체는 `EXT` `KHR` 이러한 기능 영역에 대 한 교차 공급 업체 또는 확장을 설계 하기 위해 함께 작업 하 고 있습니다. 공급 업체 간 확장은 핵심 사양과 마찬가지로 런타임 공급 업체에서 이식 가능한 해당 기능에 대해 작성 하는 코드를 만듭니다.

## <a name="getting-started-with-openxr"></a>OpenXR 시작

![혼합 현실 헤드셋을 입고 사용자가 재생 중인 Minecraft의 스크린샷](images/openxr-minecraft.jpg)

*Minecraft 's new RenderDragon 엔진은 OpenXR를 사용 하 여 데스크톱 VR 지원을 구축 했습니다.*

Microsoft는 전 [세계의 새로운 반향 G2 헤드셋](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)을 비롯 한 모든 범위의 PC VR 전체에서 (HoloLens 2 뿐만 아니라), 혼합 현실의 미래를 개방 하도록 Unity 및 대규모 사용자 스토리 게임을 사용 했습니다.  OpenXR는 현재 Minecraft 및 Microsoft 비행 시뮬레이터 등의 주요 타이틀 배송에 대 한 공급 업체의 VR 지원 기능을 제공 합니다.  HoloLens (첫 번째 gen)를 개발 하는 방법에 대 한 자세한 내용은 [릴리스 정보](/hololens/hololens1-release-notes)를 참조 하세요.

Unity, Unreal Engine 또는 사용자 고유의 엔진에서 OpenXR를 시작 하는 방법을 알아보려면을 읽어 보세요.

### <a name="openxr-in-unity"></a>Unity의 OpenXR

현재 HoloLens 2, HoloLens (첫 번째 gen) 및 Windows Mixed Reality 헤드셋에 대해 지원 되는 Unity 개발 경로는 기존 WinRT API 백 엔드와 함께 **unity 2019 LTS** 입니다.  Unity를 사용 하 [여 OpenXR](../unity/xr-project-setup.md)로 이동할 수 있습니다. Unity 2019 앱에서 새로운 HP 반향 G2 컨트롤러를 대상으로 하는 경우 [Hp 반향 g2 입력 문서](../unity/unity-reverb-g2-controllers.md)를 참조 하세요.

**Unity 2020 LTS** 부터 Unity는 HoloLens 2 및 Windows Mixed Reality 헤드셋을 지 원하는 [OpenXR 백 엔드를 제공](https://forum.unity.com/threads/unitys-plans-for-openxr.993225/) 합니다.  여기에는 핸드 경/눈 추적, 공간 앵커 및 HP 반향 G2 컨트롤러를 포함 하 여 [HoloLens 2 및 Windows Mixed Reality 헤드셋의 전체 기능](#roadmap)을 강화 하는 OpenXR 확장에 대 한 지원이 포함 됩니다.  MRTK-Unity는 [Mrtk 2.7](../unity/tutorials/mr-learning-base-02.md?tabs=openxr#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)OpenXR을 지원 합니다.  HoloLens의 현재 상태에 대 한 2020 LTS 지원 HoloLens 2에 대 한 자세한 내용은 [unity 버전 선택](../unity/choosing-unity-version.md)을 참조 하세요.

**Unity 2021** 부터 OpenXR는 HoloLens 2 및 Windows Mixed Reality 헤드셋을 대상으로 하는 지원 되는 유일한 Unity 백 엔드가 되도록 졸업을 합니다.

### <a name="openxr-in-unreal-engine"></a>Unreal Engine의 OpenXR

**Unreal Engine 4.23** 부터 Windows mixed Reality (WinRT) 플러그 인을 통해 HoloLens 2 및 Windows mixed reality 헤드셋을 완벽 하 게 지원할 수 있습니다.

Unreal Engine 4.23은 OpenXR 1.0에 대 한 미리 보기 지원을 제공 하는 최초의 주요 게임 엔진 릴리스입니다.  이제 **Unreal engine 4.26** 에서 HoloLens 2, Windows Mixed Reality 및 기타 데스크톱 VR 헤드셋은 Unreal engine의 기본 제공 OpenXR 지원을 통해 제공 됩니다.  Unreal Engine 4.26은 [Microsoft의 OpenXR 확장 플러그 인](https://github.com/microsoft/Microsoft-OpenXR-Unreal)도 지원 하며, 직접 상호 작용 및 HP 반향 G2 컨트롤러 지원을 사용 하도록 설정 하 여 [HoloLens 2 및 Windows Mixed Reality 헤드셋의 전체 기능 집합](#roadmap)을 제공 합니다.  현재 사용 하지 않는 unreal Engine 4.26은 현재 4 월에 MRTK-Unreal 지원을 포함 하 여 [대규모 사용자 스토리 게임 시작 관리자](https://www.unrealengine.com/download/creators)에서 사용할 수 있습니다.


### <a name="openxr-for-native-development"></a>OpenXR for native development

데스크톱의 Windows Mixed Reality 몰입형 헤드셋 또는 HoloLens 2에서 OpenXR을 사용하여 개발할 수 있습니다.  헤드셋에 액세스할 수 없는 경우 HoloLens 2 에뮬레이터 또는 Windows Mixed Reality 시뮬레이터를 대신 사용할 수 있습니다.

HoloLens 2 또는 몰입 형 Windows Mixed Reality 헤드셋 용 OpenXR 응용 프로그램 개발을 시작 하려면 [OpenXR 개발을 시작 하는 방법](openxr-getting-started.md)을 참조 하세요.

지금 OpenXR를 사용 하는 실제 응용 프로그램의 예제와 함께 OpenXR API의 모든 주요 구성 요소에 대 한 둘러보기는이 60 분 연습 비디오를 확인 하세요.

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>참조

* <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR에 대 한 자세한 정보</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 사양</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 참조</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 빠른 참조 가이드</a>