---
title: 혼합 현실 구성 가이드
description: Unity에 MRTK를 구성 하는 방법에 대 한 설명서입니다.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK,
ms.openlocfilehash: b714e01a0969b88a4ca7a3a5047bc5d61516e3f3
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345146"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a>Mixed Reality Toolkit 프로필 구성 가이드

![MRTK 로고](../features/images/MRTK_Logo_Rev.png)

혼합 현실 도구 키트는 가능한 한 도구 키트를 관리 하는 데 필요한 많은 구성 (진정한 런타임 "사물" 제외)을 중앙 집중식으로 관리 합니다.

이 가이드는 도구 키트에 대해 현재 사용할 수 있는 각 구성 프로필 화면에 대 한 간단한 연습입니다.

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a>기본 Mixed Reality Toolkit 구성 프로필

장면의 *MixedRealityToolkit* GameObject에 연결 된 기본 구성 프로필은 프로젝트의 도구 키트에 대 한 기본 진입점을 제공 합니다.

> [!NOTE]
> 혼합 현실 도구 키트는 기본 구성 화면을 "잠금" 하 여 프로젝트에 대 한 공통 시작 지점이 항상 있는지 확인 하 고 프로젝트가 진화 함에 따라 사용자 고유의 설정을 정의 하기 시작 하는 것이 좋습니다. MRTK 구성은 재생 모드에서 편집할 수 없습니다.

![MRTK 구성 프로필](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

혼합 현실 도구 키트의 모든 "기본" 프로필은 asset/MRTK/SDK/Profiles 폴더의 SDK 프로젝트에서 찾을 수 있습니다.

> [!IMPORTANT]
> DefaultHoloLens2ConfigurationProfile는 HoloLens 2에 최적화 되어 있습니다. 자세한 내용은 [프로필](../features/profiles/profiles.md) 을 참조 하세요.

기본 Mixed Reality Toolkit 구성 프로필을 열면 검사기에 다음 화면이 표시 됩니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

장면에서 MixedRealityToolkit 없이 MixedRealityToolkitConfigurationProfile 자산을 선택 하는 경우 MRTK에서 자동으로 장면을 설정 하도록 할 것인지 묻는 메시지가 표시 됩니다. 이 옵션은 선택 사항 이지만 모든 구성 화면에 액세스 하려면 장면에 활성 MixedRealityToolkit 개체가 있어야 합니다.

프로젝트에 대 한 현재 활성 런타임 구성을 저장 합니다.

여기에서 다음을 포함 하 여 MRTK에 대 한 모든 구성 프로필을 탐색할 수 있습니다.

- [Mixed Reality Toolkit 프로필 구성 가이드](#mixed-reality-toolkit-profile-configuration-guide)
  - [기본 Mixed Reality Toolkit 구성 프로필](#the-main-mixed-reality-toolkit-configuration-profile)
  - [환경 설정](#experience-settings)
  - [카메라 설정](#camera-settings)
  - [입력 시스템 설정](#input-system-settings)
  - [경계 시각화 설정](#boundary-visualization-settings)
  - [Teleportation 시스템 선택](#teleportation-system-selection)
  - [공간 인식 설정](#spatial-awareness-settings)
  - [진단 설정](#diagnostics-settings)
  - [시스템 설정 장면](#scene-system-settings)
  - [추가 서비스 설정](#additional-services-settings)
  - [입력 작업 설정](#input-actions-settings)
  - [입력 작업 규칙](#input-actions-rules)
  - [포인터 구성](#pointer-configuration)
  - [제스처 구성](#gestures-configuration)
  - [음성 명령](#speech-commands)
  - [컨트롤러 매핑 구성](#controller-mapping-configuration)
  - [컨트롤러 시각화 설정](#controller-visualization-settings)
  - [편집기 유틸리티](#editor-utilities)
    - [서비스 검사기](#service-inspectors)
    - [깊이 버퍼 렌더러](#depth-buffer-renderer)
  - [런타임에 프로필 변경](#changing-profiles-at-runtime)
    - [이전 MRTK 초기화 프로필 스위치](#pre-mrtk-initialization-profile-switch)
    - [활성 프로필 스위치](#active-profile-switch)
  - [참고 항목](#see-also)

이러한 구성 프로필은 아래 관련 섹션에서 자세히 설명 합니다.

---
<a name="experience"></a>

## <a name="experience-settings"></a>환경 설정

기본 Mixed Reality 도구 키트 구성 페이지에 있는이 설정은 프로젝트에 대 한 [혼합 현실 환경 규모](/windows/mixed-reality/coordinate-systems-in-unity) 의 기본 작업을 정의 합니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a>카메라 설정

카메라 설정은 혼합 현실 프로젝트에 대해 카메라를 설정 하는 방법을 정의 하 여 일반 클리핑, 품질 및 투명도 설정을 정의 합니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a>입력 시스템 설정

Mixed Reality 프로젝트는 기본적으로 선택 되는 프로젝트에 대 한 모든 입력 이벤트를 라우팅하기 위한 강력 하 고 잘 학습 된 입력 시스템을 제공 합니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

MRTK에서 제공 하는 입력 시스템 뒤에는 여러 다른 시스템이 있으며,이를 통해 다중 플랫폼/혼합 현실 프레임 워크의 복잡성을 추상화 하는 데 필요한 복잡 한 비-weavings를 구동 하 고 관리할 수 있습니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

각 개별 프로필은 아래에 자세히 설명 되어 있습니다.

- 포커스 설정
- [입력 작업 설정](#input-actions-settings)
- [입력 작업 규칙](#input-actions-rules)
- [포인터 구성](#pointer-configuration)
- [제스처 구성](#gestures-configuration)
- [음성 명령](#speech-commands)
- [컨트롤러 매핑 구성](#controller-mapping-configuration)
- [컨트롤러 시각화 설정](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a>경계 시각화 설정

경계 시스템은 기본 플랫폼 경계/보호자 시스템에서 보고 하는 인식 된 경계를 변환 합니다. 경계 시각화 도우미 구성은 사용자의 위치를 기준으로 장면 내에 기록 된 경계를 자동으로 표시 하는 기능을 제공 합니다. 경계는 사용자의 장면 내 teleports 위치에 따라 반응 하거나 업데이트 합니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a>Teleportation 시스템 선택

Mixed Reality 프로젝트는 기본적으로 선택 되는 프로젝트에서 Teleportation 이벤트를 관리 하기 위한 완전 한 기능을 갖춘 Teleportation 시스템을 제공 합니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a>공간 인식 설정

혼합 현실 프로젝트는 기본적으로 선택 되는 프로젝트에서 공간 검색 시스템을 사용 하기 위해 다시 작성 된 공간 인식 시스템을 제공 합니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

혼합 현실 도구 키트 공간 인식 구성을 사용 하면 응용 프로그램이 시작 될 때 자동으로 실행 되는 경우 자동으로 실행 되는 방식으로 또는 보기의 필드에 대 한 익스텐트를 설정 하는 방식으로 시스템 시작 방식을 조정할 수 있습니다.

또한 메시 및 surface 설정을 구성 하 여 프로젝트에서 사용자의 환경을 이해 하는 방법을 사용자 지정할 수 있습니다.

검색 된 환경을 제공할 수 있는 장치에만 적용 됩니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a>진단 설정

MRTK의 선택적 이지만 매우 유용한 기능은 플러그 인 진단 기능입니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

진단 프로필은 화면에서 디스플레이 패널을 사용/사용 하지 않도록 설정 하는 편리한 켜기/끄기 스위치를 포함 하 여 프로젝트가 실행 되는 동안 모니터링 하는 몇 가지 간단한 시스템을 제공 합니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a>시스템 설정 장면

MRTK는 복잡 한 추가 장면 로드/언로드를 관리 하는 데 도움이 되는 선택적 서비스를 제공 합니다. 장면 시스템이 프로젝트에 적합 한지 여부를 결정 하려면 [장면 시스템 시작 가이드를 참조 하세요.](../features/scene-system/scene-system-getting-started.md)

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a>추가 서비스 설정

Mixed Reality Toolkit의 고급 영역 중 하나는 프레임 워크에 "서비스"를 등록 하는 데 사용할 수 있는 [서비스 로케이터 패턴](https://en.wikipedia.org/wiki/Service_locator_pattern) 구현입니다. 이를 통해 프레임 워크를 새로운 기능/시스템으로 쉽게 확장할 수 있습니다. 또한 프로젝트에서 이러한 기능을 활용 하 여 고유한 런타임 구성 요소를 등록할 수 있습니다.

등록 된 서비스에서는 MonoBehaviour 또는 clunky singleton 패턴을 구현 하는 오버 헤드와 비용 없이 모든 Unity 이벤트의 모든 이점을 누릴 수 있습니다. 이를 통해 포그라운드 및 백그라운드 프로세스를 실행 하는 데 필요한 장면 오버 헤드가 없는 순수 c # 구성 요소 (예: 시스템, 런타임 게임 논리 또는 거의 모든 항목)를 사용할 수 있습니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a>입력 작업 설정

입력 작업은 런타임 프로젝트의 모든 물리적 상호 작용 및 입력을 추상화 하는 방법을 제공 합니다. 모든 실제 입력 (컨트롤러/직접/마우스/등)은 런타임 프로젝트에서 사용 하기 위한 논리적 입력 동작으로 변환 됩니다. 이렇게 하면 입력이 제공 되는 위치와 관계 없이 프로젝트에서 이러한 작업을 내부적으로 "할 일" 또는 "상호 작용"으로 구현 합니다.

새 입력 작업을 만들려면 "새 작업 추가" 단추를 클릭 하 고 표시 되는 내용에 대 한 텍스트 이름을 입력 하면 됩니다. 그런 다음 동작을 전달할 축 (데이터 유형)만 선택 해야 합니다. 또는 실제 컨트롤러의 경우에는 다음과 같이 연결 될 수 있는 물리적 입력 유형을 선택 해야 합니다.

| 축 제약 조건 | 데이터 형식 | 설명 | 예제 사용 |
| :--- | :--- | :--- | :--- |
| 없음 | 데이터 없음 | 빈 동작 또는 이벤트에 사용 됩니다. | 이벤트 트리거 |
| Raw (예약 됨) | object | 나중에 사용하도록 예약되어 있습니다. | N/A |
| 디지털 | bool | 형식 데이터의 부울 켜기 또는 끄기 | 컨트롤러 단추 |
| 단일 축 | float | 단정밀도 데이터 값 | 범위가 있는 입력(예: 트리거) |
| 이중 축 | Vector2 | 여러 축에 대한 이중 float 형식 날짜 | Dpad 또는 Thumbstick |
| Dof 위치 3개 | Vector3 | float 축이 3개인 의 위치 형식 데이터 | 3D 위치 스타일만 컨트롤러 |
| Dof 회전 3개 | 쿼터니언 | float 축이 4개인 회전 전용 입력 | 3도 스타일 컨트롤러(예: Oculus Go 컨트롤러) |
| Six Dof | Mixed Reality 자세(Vector3, Quaternion) | Vector3 및 Quaternion 구성 요소가 모두 있는 위치 및 회전 스타일 입력 | 모션 컨트롤러 또는 포인터 |

입력 작업을 활용하는 이벤트는 실제 컨트롤러로 제한되지 않으며, 프로젝트 내에서 계속 활용하여 런타임 효과가 새 작업을 생성하도록 할 수 있습니다.

> [!NOTE]
> 입력 작업은 런타임에 편집할 수 없는 몇 가지 구성 요소 중 하나이며 디자인 타임 구성에만 해당합니다. 각 작업에 대해 생성된 ID에 대한 프레임워크(및 프로젝트) 종속성으로 인해 프로젝트가 실행되는 동안에는 이 프로필을 교환해서는 안 됩니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a>입력 작업 규칙

입력 작업 규칙은 의 한 입력 동작에 대해 발생된 이벤트를 해당 데이터 값에 따라 다른 작업으로 자동으로 변환하는 방법을 제공합니다. 프레임워크 내에서 원활하게 관리되며 성능 비용이 발생하지 않습니다.

예를 들어 의 DPad에서 단일 이중 축 입력 이벤트를 해당하는 4개 "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" 작업(아래 이미지에 표시)으로 변환합니다.

사용자 고유의 코드에서 이 작업을 수행할 수도 있습니다. 그러나 이것이 매우 일반적인 패턴인 것을 볼 때 프레임워크는 이 작업을 "기본 제공"하는 메커니즘을 제공합니다.

입력 작업 사용 가능한 입력 축에 대해 규칙을 구성할 수 있습니다. 그러나 한 축 형식의 입력 동작을 동일한 축 형식의 다른 입력 동작으로 변환할 수 있습니다. 이중 축 동작을 다른 이중 축 작업에 매핑할 수 있지만 디지털 또는 없음 작업에는 매핑할 수 없습니다.

![입력 작업 규칙 프로필](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a>포인터 구성

포인터는 입력 디바이스에서 장면의 대화형 활동을 구동하는 데 사용되며, 장면의 모든 개체(충돌체가 연결되어 있거나 UI 구성 요소)를 사용하여 방향과 적중 테스트를 모두 제공합니다. 포인터는 기본적으로 컨트롤러, 헤드셋(응시/포커스) 및 마우스/터치 입력에 대해 자동으로 구성됩니다.

Mixed Reality Toolkit에서 제공하는 여러 줄 구성 요소 중 하나를 사용하거나 MRTK IMixedRealityPointer 인터페이스를 구현하는 경우 직접 포인터를 사용하여 활성 장면 내에서 포인터를 시각화할 수도 있습니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- 포인팅 익스텐트: 응시를 비롯한 모든 포인터에 대한 전역 포인팅 익스텐트 결정
- 포인팅 광선 캐스트 계층 마스크: 광선 캐스팅할 레이어 포인터를 결정합니다.
- 디버그 그리기 포인팅 광선: 광선 캐스팅에 사용되는 광선을 시각화하기 위한 디버그 도우미입니다.
- 그리기 포인팅 광선 색 디버그: 시각화에 사용할 색 집합입니다.
- 응시 커서 프리팹: 모든 장면에 대한 전역 응시 커서를 쉽게 지정할 수 있습니다.

필요한 경우 응시에 대한 특정 값을 재정의하기 위해 응시 공급자로 빠르게 이동할 수 있는 추가 도우미 단추가 있습니다.

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a>제스처 구성

제스처는 다양한 SDK(예: HoloLens)에서 제공하는 다양한 "제스처" 입력 메서드에 입력 작업을 할당할 수 있도록 하는 시스템별 구현입니다.

> [!NOTE]
> 현재 제스처 구현은 HoloLens 전용이며 나중에 도구 키트에 추가될 때(아직 날짜 없음) 다른 시스템에 대해 향상될 예정입니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a>음성 명령

제스처와 마찬가지로 일부 런타임 플랫폼은 Unity 프로젝트에서 수신할 수 있는 명령을 생성하는 기능과 함께 지능형 "Speech to Text" 기능도 제공합니다. 이 구성 프로필을 사용하면 다음을 구성할 수 있습니다.

1. 일반 설정 - 자동 시작 또는 수동 시작으로 설정된 "시작 동작"은 입력 시스템 시작 시 KeywordRecognizer를 초기화할지 또는 프로젝트에서 KeywordRecognizer를 초기화할 시기를 결정하도록 할지를 결정합니다. "인식 신뢰도 수준"은 Unity의 [KeywordRecognizer API를](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) 초기화하는 데 사용됩니다.
2. 음성 명령 - "단어"를 등록하고 프로젝트에서 받을 수 있는 입력 작업으로 변환합니다. 필요한 경우 키보드 작업에 연결할 수도 있습니다.

> [!IMPORTANT]
> 시스템은 현재 Windows 10 플랫폼에서 실행하는 경우에만 음성을 지원합니다(예: HoloLens 및 Windows 10 Desktop). 향후 MRTK에 추가될 때(아직 날짜 없음) 다른 시스템에 대해 향상될 예정입니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a>컨트롤러 매핑 구성

Mixed Reality 도구 키트의 핵심 구성 화면 중 하나는 프로젝트에서 활용할 수 있는 다양한 유형의 컨트롤러를 구성하고 매핑하는 기능입니다.

아래 구성 화면에서는 도구 키트에서 현재 인식되는 컨트롤러를 구성할 수 있습니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

MRTK는 다음 컨트롤러/시스템에 대한 기본 구성을 제공합니다.

- 마우스(3D 공간 마우스 지원 포함)
- 터치 스크린
- Xbox 컨트롤러
- Windows Mixed Reality 컨트롤러
- HoloLens 제스처
- HTC Vive wand 컨트롤러
- Oculus Touch 컨트롤러
- Oculus 원격 컨트롤러
- 일반 OpenVR 디바이스(고급 사용자만 해당)

미리 빌드된 컨트롤러 시스템의 이미지를 클릭하면 모든 해당 입력에 대해 단일 입력 작업을 구성할 수 있습니다. 예를 들어 아래의 Oculus Touch 컨트롤러 구성 화면을 참조하세요.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

위에서 식별되지 않은 다른 OpenVR 또는 Unity 입력 컨트롤러를 구성하기 위한 고급 화면도 있습니다.

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a>컨트롤러 시각화 설정

컨트롤러 매핑 외에도, 컨트롤러가 장면 내에서 제공되는 방식을 사용자 지정하기 위해 별도의 구성 프로필이 제공됩니다.

"전역"(특정 손으로 컨트롤러의 모든 인스턴스) 또는 개별 컨트롤러 유형/손에서 구성할 수 있습니다.

MRTK는 Windows Mixed Reality 및 OpenVR에 대한 네이티브 SDK 컨트롤러 모델도 지원합니다. 이러한 구성은 장면에 GameObjects로 로드되고 플랫폼의 컨트롤러 추적을 사용하여 배치됩니다.

장면의 컨트롤러 표현이 실제 컨트롤러 위치에서 오프셋되어야 하는 경우 컨트롤러 모델의 프리팹에 대해 해당 오프셋을 설정하기만 하면 됩니다(예: 오프셋 위치로 컨트롤러 프리팹의 변환 위치 설정).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a>편집기 유틸리티

다음 유틸리티는 편집기에서만 작동하며 개발 생산성을 향상시키는 데 유용합니다.

![MRTK 편집기 구성 유틸리티](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a>서비스 검사기

서비스 검사기는 활성 서비스를 나타내는 장면 내 개체를 생성하는 편집기 전용 기능입니다. 이러한 개체를 선택하면 설명서 링크, 편집기 시각화 제어 및 서비스 상태에 대한 인사이트를 제공하는 검사기가 표시됩니다.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

구성 프로필의 *편집기 설정에서* *서비스 검사기 사용을* 확인하여 서비스 검사자를 사용하도록 설정할 수 있습니다.

### <a name="depth-buffer-renderer"></a>깊이 버퍼 렌더러

일부 혼합 현실 플랫폼과 깊이 버퍼를 공유하면 [홀로그램 안정화가](../performance/hologram-stabilization.md)향상될 수 있습니다. 예를 들어 Windows Mixed Reality 플랫폼은 프레임을 렌더링하는 데 걸리는 시간 동안 미묘한 머리 이동을 고려하도록 픽셀당 렌더링된 장면을 수정할 수 있습니다. 그러나 이러한 기술을 사용하려면 정확한 데이터가 있는 깊이 버퍼가 필요하므로 기하 도형이 사용자로부터 얼마나 멀리 떨어져 있는지 알 수 있습니다.

장면에서 필요한 모든 데이터를 깊이 버퍼에 렌더링하도록 하기 위해 개발자는 구성 프로필의 *편집기 설정에서* *렌더링 깊이 버퍼* 기능을 전환할 수 있습니다. 그러면 현재 깊이 버퍼가 적용되고 후처리 효과인 를 주 카메라에 적용하여 장면 보기에 색으로 [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) 렌더링됩니다.

![렌더링 깊이 버퍼 유틸리티 ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>장면의 파란색 실린더에는 ZWrite가 꺼진 재질이 있으므로 깊이 데이터가 기록되지 않습니다.</sup>

## <a name="changing-profiles-at-runtime"></a>런타임 시 프로필 변경

런타임에 프로필을 업데이트할 수 있으며 일반적으로 다음과 같은 두 가지 시나리오와 시간이 있습니다.

1. **MRTK 초기화 프로필 전환 전:** 시작 시 MRTK가 초기화되고 프로필이 활성화되기 전에 아직 사용되지 않는 프로필을 대체하여 디바이스 기능에 따라 다른 기능을 사용하거나 사용하지 않도록 설정합니다. 예를 들어 환경이 공간 매핑 하드웨어가 없는 VR에서 실행되는 경우 공간 매핑 구성 요소를 사용하도록 설정하는 것이 타의가 아닐 수 있습니다.
1. **활성 프로필 전환:** 시작 후 MRTK가 초기화되고 프로필이 활성화된 후 현재 사용 중인 프로필을 교환하여 특정 기능의 동작 방식을 변경합니다. 예를 들어 원거리 포인터를 완전히 제거하려는 애플리케이션의 특정 하위 환경이 있을 수 있습니다.

### <a name="pre-mrtk-initialization-profile-switch"></a>이전 MRTK 초기화 프로필 스위치

이는 MRTK 초기화 전에 실행 되는 MonoBehaviour (예:)를 연결 하 여 수행할 수 있습니다. 스크립트 (예: 호출)는 스크립트 `SetProfileBeforeInitialization` `MixedRealityToolkit` [실행 순서 설정을](https://docs.unity3d.com/Manual/class-MonoManager.html)설정 하 여 수행할 수 있는 스크립트 보다 먼저 실행 해야 합니다.

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

"ProfileToUse" 대신 특정 플랫폼에 적용 되는 임의의 프로필 집합을 포함할 수 있습니다 (예: HoloLens 1의 경우 하나, VR의 경우 하나, HoloLens 2의 경우 하나). 로드할 프로필을 파악 하기 위해 다양 한 표시기 (예: https://docs.unity3d.com/ScriptReference/SystemInfo.html 또는 카메라가 불투명/투명 한지 여부)를 사용할 수 있습니다.

### <a name="active-profile-switch"></a>활성 프로필 스위치

이를 위해서는 `MixedRealityToolkit.Instance.ActiveProfile` 활성 프로필을 대체 하는 새 프로필로 속성을 설정 합니다.

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

참고 런타임 중에 설정 하는 경우 `ActiveProfile` 현재 실행 중인 서비스의 삭제는 모든 서비스의 마지막 behaviour () 이후에 발생 하며, 새 프로필과 연결 된 서비스의 인스턴스화 및 초기화는 모든 서비스의 첫 번째 업데이트 () 이전에 발생 합니다.

이 프로세스 중에는 눈에 띄는 응용 프로그램 hesitation 발생할 수 있습니다. 또한 스크립트 보다 우선 순위가 높은 모든 스크립트는 `MixedRealityToolkit` 새 프로필이 제대로 설정 되기 전에 해당 업데이트를 입력할 수 있습니다. 스크립트 우선 순위에 대 한 자세한 내용은 [스크립트 실행 순서 설정](https://docs.unity3d.com/Manual/class-MonoManager.html) 을 참조 하세요.

프로필 전환 프로세스에서 기존 UI 카메라는 변경 되지 않은 상태로 유지 되 고, canvas를 필요로 하는 Unity UI 구성 요소가 스위치 후에도 계속 작동 하도록 보장 합니다.

## <a name="see-also"></a>참조

- [홀로그램 안정화](../performance/hologram-stabilization.md)