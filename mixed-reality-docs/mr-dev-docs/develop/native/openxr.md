---
title: OpenXR
description: 이식 가능한 OpenXR API 표준을 사용하여 엔진을 빌드하고 Windows Mixed Reality 및 HoloLens 2 헤드셋에 배포합니다.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, 로드맵, 확장, 크론오스, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어
ms.openlocfilehash: 98b75f8b6059e6537d4cb4a10ecf8d057ad19a07
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110711542"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR은 <a href="https://www.khronos.org/" target="_blank">Khronos의</a>개방형 무료 API 표준으로, [혼합 현실 스펙트럼에서](../../discover/mixed-reality.md)다양한 디바이스에 대한 기본 액세스를 엔진에 제공합니다.

데스크톱의 Windows Mixed Reality 몰입형 헤드셋 또는 HoloLens 2에서 OpenXR을 사용하여 개발할 수 있습니다.  헤드셋에 액세스할 수 없는 경우 HoloLens 2 에뮬레이터 또는 Windows Mixed Reality 시뮬레이터를 대신 사용할 수 있습니다.

## <a name="why-openxr"></a>OpenXR을 왜 할까요?

OpenXR을 사용하면 HoloLens 2 같은 홀로그램 디바이스와 데스크톱 PC용 Windows Mixed Reality 헤드셋과 같은 몰입형 디바이스를 모두 대상으로 하는 엔진을 빌드할 수 있습니다. OpenXR을 사용하면 코드를 한 번 작성한 다음, 광범위한 하드웨어 플랫폼에서 이식할 수 있습니다.

OpenXR API는 로더를 사용하여 헤드셋의 네이티브 플랫폼 지원에 애플리케이션을 직접 연결합니다. 최종 사용자는 Windows Mixed Reality 또는 다른 헤드셋을 사용하든 관계없이 최대 성능과 최소 대기 시간을 얻습니다.

## <a name="what-is-openxr"></a>OpenXR이란?

OpenXR API는 홀로그램 및 몰입형 디바이스를 모두 대상으로 할 수 있는 엔진을 빌드하는 데 필요한 핵심 자세 예측, 프레임 타이밍 및 공간 입력 기능을 제공합니다.

OpenXR API에 대해 알아보려면 OpenXR 1.0 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">사양,</a> <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API 참조</a>및 <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">빠른 참조 가이드</a>를 확인하세요.  자세한 내용은 <a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 페이지 를 참조하세요.</a>

HoloLens 2 전체 기능 집합을 대상으로 지정하려면 OpenXR 1.0 코어 외의 추가 기능(예: 굴절된 손 추적, 시선 추적, 공간 매핑 및 공간 앵커)을 사용할 수 있는 공급업체 간 및 공급업체별 OpenXR 확장도 사용합니다. 자세한 내용은 올해 말 출시될 확장에 대한 아래 [로드맵 섹션을](#roadmap) 참조하세요.

OpenXR 자체는 혼합 현실 엔진이 아닙니다.  대신 OpenXR을 사용하면 Unity 및 Unreal과 같은 엔진이 이식 가능한 코드를 한 번 작성할 수 있으며, 이 코드는 해당 플랫폼을 빌드한 공급업체와 관계없이 사용자의 홀로그램 또는 몰입형 디바이스의 네이티브 플랫폼 기능에 액세스할 수 있습니다.

## <a name="roadmap"></a>로드맵

OpenXR 사양은 런타임 구현자가 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">기본 OpenXR 1.0 사양</a>에 정의된 [핵심 기능](#what-is-openxr) 외에 추가 기능을 노출할 수 있도록 하는 확장 메커니즘을 정의합니다.

OpenXR 확장에는 세 가지 종류가 있습니다.
* **공급업체 확장(예: `MSFT` ):** 하드웨어 또는 소프트웨어 기능에서 공급업체별 혁신을 지원합니다.  모든 런타임 공급업체는 언제든지 공급업체 확장을 도입하고 배송할 수 있습니다.
  * **실험적 공급업체 확장(예: `MSFT_preview` ):** 피드백을 수집하기 위해 미리 보기 중인 실험적 공급업체 확장입니다.  `MSFT_preview` 확장은 개발자 디바이스 전용이며 실제 확장이 배송될 때 제거됩니다.  이를 실험하려면 개발자 [디바이스에서 미리 보기 확장을 사용하도록 설정할](openxr-getting-started.md#using-preview-extensions)수 있습니다.
* **공급업체 간 `EXT` 확장:** 여러 회사에서 정의하고 구현하는 공급업체 간 확장입니다.  관심 있는 회사 그룹은 언제든지 EXT 확장을 도입할 수 있습니다.
* **공식 `KHR` 확장:** 핵심 사양 릴리스의 일부로 공식 Khronos 확장이 공개되었습니다.  KHR 확장에는 핵심 사양 자체와 동일한 라이선스가 적용됩니다.

Windows Mixed Reality OpenXR 런타임은 `MSFT` `EXT` OpenXR 애플리케이션에 전체 HoloLens 2 기능을 제공하는 및 확장 집합을 지원합니다.

| 기능 영역 | 확장 가용성 |
|--------------|------------------------|
| 시스템 + 세션 | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [참조 공간(보기, 로컬, 스테이지)](../../design/coordinate-systems.md) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| 뷰 구성(모노, 스테레오) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [스왑 체인](../platform-capabilities-and-apis/rendering.md)  +  [프레임 타이밍](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| 컴퍼지션 계층<br />(프로젝션, 쿼드) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [입력 및 맵](../../design/interaction-fundamentals.md) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Direct3D 11 통합 | **공식 `KHR` 확장 릴리스:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Direct3D 12 통합 | **공식 `KHR` 확장 릴리스:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [무제한 참조 <br /> 공간(세계적 규모 환경)](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` 확장이 릴리스됨:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Spatial Anchors](../../design/spatial-anchors.md) | **`MSFT` 확장이 릴리스됨:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [손 <br /> 조작(그립/목표 자세, 에어 탭, 잡기)](../../design/hands-and-tools.md)<p>*HoloLens 2 전용*</p> | **`MSFT` 확장이 릴리스됨:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [손 굴절 + 손 메시](../../design/hands-and-tools.md)<p>*HoloLens 2 전용*</p> | <p>**`EXT` 런타임 102에서 릴리스된 확장:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` 런타임 102에서 릴리스된 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [응시](../../design/eye-tracking.md)<p>*HoloLens 2 전용*</p> | **`EXT` 확장이 릴리스됨:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| 다른 HoloLens SDK와의 Interop<br />(예: [QR](../platform-capabilities-and-apis/qr-code-tracking.md))<p>*HoloLens 2 전용*</p> | <p>**`MSFT` 런타임 102에서 릴리스된 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` 런타임 105의 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_perception_anchor_interop">XR_MSFT_perception_anchor_interop</a></code></p> |
| [<br />혼합 현실 캡처(PV 카메라에서 세 번째 렌더링)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*HoloLens 2 전용*</p> | **`MSFT` 런타임 102에서 릴리스된 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| UWP CoreWindow API와의 Interop<br />(예: 키보드/마우스의 경우) | **`MSFT` 런타임 103에서 릴리스된 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| 모션 컨트롤러 상호 작용 프로필<br />(Samsung Odyssey 및 HP Reverb G2) | **`MSFT` 런타임 103에서 릴리스된 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [모션 컨트롤러 렌더링 모델](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` 런타임 104에서 릴리스된 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [장면 이해(평면, 메시)](../../design/scene-understanding.md)<p>*HoloLens 2 전용*</p> | <p>**런타임 102 현재:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code>Scene [Understanding SDK와](../platform-capabilities-and-apis/scene-understanding-sdk.md) 함께 사용</p><p>**`MSFT` 미리 [보기 런타임 105의](openxr-getting-started.md#using-preview-extensions)확장:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_scene_understanding_preview2">XR_MSFT_scene_understanding_preview2</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_scene_understanding_serialization_preview">XR_MSFT_scene_understanding_serialization_preview</a></code></p> |
| [컴퍼지션 계층 다시 프로젝션 <br /> 모드(자동 평면 또는 방향 전용 다시 프로젝션)](../platform-capabilities-and-apis/hologram-stability.md#reprojection) | **`MSFT` 미리 [보기 런타임 105의](openxr-getting-started.md#using-preview-extensions)확장:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_composition_layer_reprojection_preview">XR_MSFT_composition_layer_reprojection_preview</a></code> |
| 기타 공급업체 간 확장 | <p>**공식 `KHR` 확장 릴리스:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_color_scale_bias" target="_blank">XR_KHR_composition_layer_color_scale_bias</a></code><p>**`EXT` 확장이 릴리스됨:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

이러한 확장 중 일부는 공급업체별 확장으로 시작될 수 있지만 `MSFT` Microsoft 및 기타 OpenXR 런타임 공급업체는 이러한 기능 영역의 많은 부분에 대해 공급업체 간 또는 확장을 설계하기 위해 함께 작업하고 `EXT` `KHR` 있습니다. 공급업체 간 확장을 사용하면 핵심 사양과 마찬가지로 런타임 공급업체에서 이러한 기능에 대해 작성하는 코드를 이식할 수 있습니다.

## <a name="getting-started-with-openxr"></a>OpenXR 시작

![혼합 현실 헤드셋을 쓴 사용자가 재생 중인 Minecraft의 스크린샷](images/openxr-minecraft.jpg)

*Minecraft의 새로운 RenderDragon 엔진은 OpenXR을 사용하여 데스크톱 VR 지원을 구축했습니다.*

Microsoft는 Unity 및 Epic Games와 협력하여 혼합 현실의 미래를 열기 위해 HoloLens 2 뿐만 아니라 [HP의 새로운 Reverb G2 헤드셋을](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)비롯한 전체 PC VR 전체에 걸쳐 열려 있습니다.  OpenXR은 Minecraft 및 Microsoft Flight Simulator와 같은 현재 출시되는 주요 타이틀에 대해 공급업체 간 VR 지원을 제공합니다.  HoloLens(1세대)용 개발에 대한 자세한 내용은 릴리스 정보 를 [참조하세요.](/hololens/hololens1-release-notes)

Unity, Unreal Engine 또는 자체 엔진에서 OpenXR을 시작하는 방법을 알아보려면 다음을 읽어보세요.

### <a name="openxr-in-unity"></a>Unity의 OpenXR

현재 HoloLens 2, HoloLens(1세대) 및 Windows Mixed Reality 헤드셋에 지원되는 Unity 개발 경로는 기존 WinRT API 백 엔드가 있는 **Unity 2019 LTS입니다.**  Unity를 통해 [OpenXR로](../unity/openxr-getting-started.md)이동할 수 있습니다. Unity 2019 앱에서 새 HP Reverb G2 컨트롤러를 대상으로 하는 경우 [HP Reverb G2 입력 문서를 참조하세요.](../unity/unity-reverb-g2-controllers.md)

Unity **2020 LTS부터** Unity는 HoloLens 2 및 Windows Mixed Reality 헤드셋을 지원하는 [OpenXR 백 엔드를 제공합니다.](https://forum.unity.com/threads/unitys-plans-for-openxr.993225/)  여기에는 손/시선 추적, 공간 앵커 및 HP Reverb G2 컨트롤러를 포함하여 [HoloLens 2 및 Windows Mixed Reality 헤드셋의 전체 기능을](#roadmap)조명하는 OpenXR 확장에 대한 지원이 포함됩니다.  MRTK-Unity [MRTK 2.7을](../unity/tutorials/mr-learning-base-02.md?tabs=openxr#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)통해 OpenXR을 지원합니다.  HoloLens 2 대한 Unity 2020 LTS 지원의 현재 상태에 대한 자세한 내용은 [Unity 버전 선택을 참조하세요.](../unity/choosing-unity-version.md)

Unity **2021부터** OpenXR은 HoloLens 2 및 Windows Mixed Reality 헤드셋을 대상으로 하는 데 유일하게 지원되는 Unity 백 엔드가 됩니다.

### <a name="openxr-in-unreal-engine"></a>Unreal Engine의 OpenXR

**Unreal Engine 4.23부터** WinRT(Windows Mixed Reality) 플러그 인을 통해 HoloLens 2 및 Windows Mixed Reality 헤드셋을 완전히 지원할 수 있습니다.

Unreal Engine 4.23은 OpenXR 1.0에 대한 미리 보기 지원을 출시한 최초의 주요 게임 엔진 릴리스이기도 합니다.  이제 **Unreal Engine 4.26에서는 Unreal Engine의** 기본 제공 OpenXR 지원을 통해 HoloLens 2, Windows Mixed Reality 및 기타 데스크톱 VR 헤드셋에 대한 지원을 사용할 수 있습니다.  Unreal Engine 4.26은 [Microsoft의 OpenXR 확장 플러그 인도](https://github.com/microsoft/Microsoft-OpenXR-Unreal)지원하여 손 상호 작용 및 HP Reverb G2 컨트롤러 지원을 지원하여 [HoloLens 2 및 Windows Mixed Reality 헤드셋의 전체 기능 집합을 조명합니다.](#roadmap)  Unreal Engine 4.26은 현재 [에픽 게임 시작 관리자에서](https://www.unrealengine.com/download/creators)사용할 수 있으며, MRTK-Unreal 지원은 4월 말에 제공될 예정입니다.


### <a name="openxr-for-native-development"></a>네이티브 개발을 위한 OpenXR

데스크톱의 Windows Mixed Reality 몰입형 헤드셋 또는 HoloLens 2에서 OpenXR을 사용하여 개발할 수 있습니다.  헤드셋에 액세스할 수 없는 경우 HoloLens 2 에뮬레이터 또는 Windows Mixed Reality 시뮬레이터를 대신 사용할 수 있습니다.

HoloLens 2 또는 몰입형 Windows Mixed Reality 헤드셋용 OpenXR 애플리케이션 개발을 시작하려면 [OpenXR 개발을 시작하는 방법을](openxr-getting-started.md)참조하세요.

OpenXR API의 모든 주요 구성 요소를 둘러보고 현재 OpenXR을 사용하는 실제 애플리케이션의 예제를 확인하려면 다음 60분 연습 비디오를 확인하세요.

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>참조

* <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR에 대한 자세한 정보</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 사양</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 참조</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 빠른 참조 가이드</a>