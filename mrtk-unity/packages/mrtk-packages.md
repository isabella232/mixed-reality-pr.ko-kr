---
title: MRTK 패키지
description: 혼합 현실 하드웨어 및 플랫폼을 지 원하는 MRTK의 패키지입니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, Unity 패키지 관리자
ms.openlocfilehash: 3c2a11dd4036a78ccb96aa2c640ef8324181c1e0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176499"
---
# <a name="mrtk-packages"></a>MRTK 패키지

mixed reality Toolkit (mrtk)는 혼합 현실 하드웨어 및 플랫폼에 대 한 지원을 제공 하 여 플랫폼 간 혼합 현실 응용 프로그램 개발을 가능 하 게 하는 패키지 모음입니다.

mrtk는 [asset](#asset-packages) (. unitypackage) 패키지와 [Unity 패키지 관리자](#unity-package-manager)를 통해 사용할 수 있습니다.

## <a name="asset-packages"></a>자산 패키지

MRTK 자산 (. unitypackage)은 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)에서 다운로드할 수 있습니다.

자산 패키지를 사용 하는 몇 가지 이점은 다음과 같습니다.

- Unity 2018.4 이상에서 사용 가능
- MRTK를 쉽게 변경할 수 있습니다.
  - MRTK가 자산 폴더에 있습니다.

다음은 몇 가지 문제입니다.

- MRTK는 프로젝트의 자산 폴더의 일부 이며,
  - 대규모 프로젝트
  - 컴파일 시간 느림
- 종속성 관리 안 함
  - 고객은 패키지 종속성을 수동으로 해결 해야 합니다.
- 수동 업데이트 프로세스
  - 여러 단계
  - 대량 (3000 개 이상 파일) 소스 제어 업데이트
  - MRTK에 대 한 변경 내용이 손실 될 위험
- 예제 패키지를 가져오는 것은 일반적으로 모든 예제를 포함 합니다.

사용 가능한 패키지는 다음과 같습니다.

- [Mfc](#foundation-package)
- [확장](#extensions-package)
- [도구](#tools-package)
- [테스트 유틸리티](#test-utilities-package)
- [예](#examples-package)

이러한 패키지는 GitHub의 [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) 분기에 있는 소스 코드를 통해 Microsoft에서 릴리스 및 지원 됩니다.

### <a name="foundation-package"></a>Foundation 패키지

혼합 현실 Toolkit Foundation은 응용 프로그램에서 혼합 현실 플랫폼 간에 일반적인 기능을 활용할 수 있도록 하는 코드 집합입니다.

<img src="../features/images/input/MRTK_Package_Foundation.png" width="350px" alt="Pakage foundation" style="display:block;">  
<sup>MRTK Foundation 패키지</sup>

MRTK Foundation 패키지에는 다음이 포함 되어 있습니다.

| 폴더 | 구성 요소 | Description |
| --- | --- | --- |
| MRTK/Core | | 인터페이스 및 형식 정의, 기본 클래스, 표준 셰이더. |
| MRTK/코어/공급자 | | 플랫폼 독립적 데이터 공급자 |
| | 훈련 | 직접 추적을 위한 기본 클래스 지원 및 서비스입니다. |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | 헤드 이동 및 핸드 추적 데이터 기록을 지원 합니다. |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | 수동 및 눈 입력의 편집기 내 시뮬레이션 지원. |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | 3D 모델을 데이터로 사용 하는 공간 인식 관찰자 |
| | UnityInput | Unity의 입력 API를 통해 구현 되는 일반적인 입력 장치 (조이스틱, 마우스 등). |
| MRTK/공급자 | | 플랫폼별 데이터 공급자 |
| | LeapMotion | UltraLeap Leap 동작 컨트롤러에 대 한 지원. |
| | OpenVR | OpenVR 장치 지원. |
| | Oculus | Quest와 같은 Oculus 장치 지원. |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) | 시험용 모바일 AR 장치에서 MRTK를 사용 하도록 설정 하는 카메라 설정 공급자입니다. |
| | WindowsMixedReality | Microsoft HoloLens 및 모던 헤드셋을 비롯 한 Windows Mixed Reality 장치 지원. |
| | Windows | Microsoft Windows 특정 api (예: 음성 및 받아쓰기)를 지원 합니다. |
| | XR SDK | 시험용 Unity 2019.3 이상에서 [unity의 NEW XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 를 지원 합니다. |
| MRTK/SDK | | |
| | 실험적 | 셰이더, 사용자 인터페이스 컨트롤 및 개별 시스템 관리자를 비롯 한 실험적 기능 |
| | 기능 | 기본 패키지를 기반으로 하는 기능입니다. |
| | 프로필 | Microsoft Mixed Reality의 기본 프로필 Toolkit 시스템 및 서비스입니다. |
| | StandardAssets | 일반적인 자산 모델, 질감, 재질 등 |
| MRTK/SceneSystemResources | | 장면 시스템에서 사용 하는 자산 및 리소스 |
| MRTK/서비스 | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | VR 경계 지원을 구현 하는 시스템입니다. |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | 카메라 구성 및 관리를 구현 하는 시스템입니다. |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | 응용 프로그램 진단에서 시스템을 구현 합니다 (예: 시각적 프로파일러). |
| | [InputSystem](../features/input/overview.md) | 사용자 입력에 대 한 액세스 및 처리 지원을 제공 하는 시스템입니다. |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | 다중 장면 응용 프로그램 지원을 제공 하는 시스템입니다. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | 사용자 환경을 인식 하기 위한 지원을 제공 하는 시스템입니다. |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | Teleporting에 대 한 지원을 제공 하는 시스템 (점프의 경험에 대 한 이동). |
| MRTK/StandardAssets | | MRTK 표준 셰이더, 기본 자료 및 혼합 현실 환경에 대 한 기타 표준 자산 |

### <a name="extensions-package"></a>확장 패키지

선택적 MixedRealityToolkit 패키지에는 Microsoft Mixed Reality Toolkit의 기능을 확장 하는 추가 서비스가 포함 되어 있습니다.

> [!NOTE]
> 확장 패키지에는 MixedRealityToolkit가 필요 합니다.

| 폴더 | 구성 요소 | Description |
| --- | --- | --- |
| MRTK/Extensions | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | 트레일러 지원을 추가 하는 서비스입니다. |
| | LostTrackingService | Microsoft HoloLens 장치에서 추적 손실의 처리를 간소화 하는 서비스입니다. |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | 부드러운 장면 전환 추가를 간소화 하는 서비스입니다. |

### <a name="tools-package"></a>도구 패키지

선택적 MixedRealityToolkit 패키지에는 Microsoft Mixed Reality Toolkit를 사용 하 여 혼합 현실 개발 환경을 개선 하는 유용한 도구가 포함 되어 있습니다.
이러한 도구는 Unity 편집기의 **Mixed Reality Toolkit > 유틸리티** 메뉴에 있습니다.

> [!NOTE]
> 도구 패키지에는 MixedRealityToolkit가 필요 합니다.

| 폴더 | 구성 요소 | Description |
| --- | --- | --- |
| MRTK/Tools | |
| | BuildWindow | UWP 응용 프로그램 빌드 및 배포 프로세스를 간소화 하는 데 도움이 되는 도구입니다. |
| | [DependencyWindow](../features/tools/dependency-window.md) | 프로젝트의 자산에 대 한 종속성 그래프를 만드는 도구입니다. |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | 확장 서비스를 만드는 데 도움이 되는 마법사입니다. |
| | [MigrationWindow](../features/tools/migration-window.md) | 사용 되지 않는 MRTK 구성 요소를 사용 하는 코드 업데이트에 도움이 되는 도구입니다.  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | Unity에서 최상의 성능을 위해 혼합 현실 프로젝트를 자동으로 구성 하는 데 도움이 되는 유틸리티입니다. |
| | ReserializeAssetsUtility | 특정 Unity 파일을 다시 serialize 하기 위한 지원을 제공 합니다. |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | 개발자가 하드웨어 컨트롤러에 대 한 Unity 매핑을 신속 하 게 결정할 수 있도록 하는 유틸리티입니다. |
| | ScreenshotUtility | Unity 편집기에서 응용 프로그램 이미지를 캡처할 수 있습니다. |
| | TextureCombinerWindow | 그래픽 질감을 결합 하는 유틸리티입니다. |
| | [도구 상자](../features/ux-building-blocks/toolbox.md) | MRTK UX 구성 요소를 쉽게 검색 하 고 사용할 수 있도록 하는 UI입니다. |

### <a name="test-utilities-package"></a>유틸리티 패키지 테스트

선택적 MixedRealityToolkit 패키지는 개발자가 [재생 모드 테스트](../contributing/unit-tests.md#play-mode-tests)를 쉽게 만들 수 있도록 하는 도우미 스크립트 모음입니다. 이러한 유틸리티는 MRTK 구성 요소를 만드는 개발자에 게 특히 유용 합니다.

| 폴더 | 구성 요소 | Description |
| --- | --- | --- |
| MRTK/테스트 | |
| | TestUtilities | 핸드 시뮬레이션 유틸리티를 포함 하 여 재생 모드 테스트 만들기를 간소화 하는 방법입니다. |

### <a name="examples-package"></a>예제 패키지

예제 패키지에는 기본 패키지의 기능을 실행 하는 데모, 샘플 스크립트 및 샘플 장면이 포함 되어 있습니다. 이 패키지에는 다양 한 형식의 직접 입력에 응답 하는 샘플 개체 (아래 그림)가 포함 되어 있습니다 ( [HandInteractionExample](../features/example-scenes/hand-interaction-examples.md) ).

![HandInteractionExample 장면](../features/images/MRTK_Examples.png)

이 패키지에는 [여기에 설명](../features/example-scenes/eye-tracking-examples-overview.md) 된 눈 추적 데모도 포함 되어 있습니다.

보다 일반적으로 MRTK의 모든 새 기능은 동일한 폴더 구조와 위치에 따라 예제 패키지에 해당 하는 예제를 포함 해야 합니다.

> [!NOTE]
> 예제 패키지에는 MixedRealityToolkit가 필요 합니다.

| 폴더 | 구성 요소 | Description |
| --- | --- | --- |
| MRTK/예제 | | |
| | 데모 | 하나 또는 두 개의 관련 기능을 보여 주는 간단한 장면 |
| | 실험적 | 실험적 기능을 보여 주는 데모 장면 |
| | StandardAssets | 여러 데모 장면에서 공유 하는 일반적인 자산입니다. |

## <a name="unity-package-manager"></a>Unity 패키지 관리자

unity 2019.4 이상 버전을 사용 하 여 생성 되는 환경에서는 [unity 패키지 관리자](https://docs.unity3d.com/Manual/Packages.html)를 통해 mrtk를 사용할 수 있습니다.

자산 패키지를 사용 하는 몇 가지 이점은 다음과 같습니다.

- 더 작은 프로젝트
  - 클리너 Visual Studio 솔루션
  - 체크 인할 파일 수 줄이기 (MRTK는 파일의 단순 참조 `Packages/manifest.json` )
- 컴파일 속도 향상
  - Unity는 빌드하는 동안 MRTK를 다시 컴파일할 필요가 없습니다.
- 종속성 확인
  - 종속성이 포함 된 패키지를 지정 하는 경우 필요한 MRTK 패키지가 자동으로 설치 됩니다.
- 새 MRTK 버전으로 쉽게 업데이트
  - 파일의 버전을 변경 합니다. `Packages/manifest.json`

다음은 몇 가지 문제입니다.

- MRTK는 변경할 수 없습니다.
  - 패키지 확인 중 제거 되지 않으면 변경할 수 없습니다.
- MRTK는 Unity 2018.4를 사용 하는 UPM 패키지를 지원 하지 않습니다.

### <a name="foundation-package"></a>Foundation 패키지

Foundation 패키지 ( `com.microsoft.mixedreality.toolkit.foundation` )는 혼합 현실 Toolkit의 기본을 형성 합니다.

| 폴더 | 구성 요소 | Description |
| --- | --- | --- |
| MRTK/Core | | 인터페이스 및 형식 정의, 기본 클래스, 표준 셰이더. |
| MRTK/코어/공급자 | | 플랫폼 독립적 데이터 공급자 |
| | 훈련 | 직접 추적을 위한 기본 클래스 지원 및 서비스입니다. |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | 헤드 이동 및 핸드 추적 데이터 기록을 지원 합니다. |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | 수동 및 눈 입력의 편집기 내 시뮬레이션 지원. |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | 3D 모델을 데이터로 사용 하는 공간 인식 관찰자 |
| | UnityInput | Unity의 입력 API를 통해 구현 되는 일반적인 입력 장치 (조이스틱, 마우스 등). |
| MRTK/공급자 | | 플랫폼별 데이터 공급자 |
| | LeapMotion | UltraLeap Leap 동작 컨트롤러에 대 한 지원. |
| | OpenVR | OpenVR 장치 지원. |
| | Oculus | Quest와 같은 Oculus 장치 지원. |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) | 시험용 모바일 AR 장치에서 MRTK를 사용 하도록 설정 하는 카메라 설정 공급자입니다. |
| | WindowsMixedReality | Microsoft HoloLens 및 모던 헤드셋을 비롯 한 Windows Mixed Reality 장치 지원. |
| | Windows | Microsoft Windows 특정 api (예: 음성 및 받아쓰기)를 지원 합니다. |
| | XR SDK | 시험용 Unity 2019.3 이상에서 [unity의 NEW XR framework](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 를 지원 합니다. |
| MRTK/SDK | | |
| | 실험적 | 셰이더, 사용자 인터페이스 컨트롤 및 개별 시스템 관리자를 비롯 한 실험적 기능 |
| | 기능 | 기본 패키지를 기반으로 하는 기능입니다. |
| | 프로필 | Microsoft Mixed Reality의 기본 프로필 Toolkit 시스템 및 서비스입니다. |
| | StandardAssets | 일반적인 자산 모델, 질감, 재질 등 |
| MRTK/서비스 | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | VR 경계 지원을 구현 하는 시스템입니다. |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | 카메라 구성 및 관리를 구현 하는 시스템입니다. |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | 응용 프로그램 진단에서 시스템을 구현 합니다 (예: 시각적 프로파일러). |
| | [InputSystem](../features/input/overview.md) | 사용자 입력에 대 한 액세스 및 처리 지원을 제공 하는 시스템입니다. |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | 다중 장면 응용 프로그램 지원을 제공 하는 시스템입니다. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | 사용자 환경을 인식 하기 위한 지원을 제공 하는 시스템입니다. |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | Teleporting에 대 한 지원을 제공 하는 시스템 (점프의 경험에 대 한 이동). |

종속성:

- 표준 자산 ( `com.microsoft.mixedreality.toolkit.standardassets` )

### <a name="standard-assets"></a>표준 자산

표준 자산 패키지 ( `com.microsoft.mixedreality.toolkit.standardassets)` 은 다음을 비롯 한 모든 혼합 현실 환경에 권장 되는 구성 요소 모음입니다.

- MRTK 표준 셰이더
- MRTK 표준 셰이더를 사용 하는 기본 자료
- 오디오 파일
- 글꼴
- 질감
- 아이콘

> [!Note]
> 어셈블리 정의를 기반으로 하는 주요 변경 내용을 방지 하기 위해 MRTK 표준 셰이더의 일부 기능을 제어 하는 데 사용 되는 스크립트는 표준 자산 패키지에 포함 되지 않습니다. 이러한 스크립트는 폴더의 foundation 패키지에서 찾을 수 있습니다 `MRTK/Core/Utilities/StandardShader` .

종속성: 없음

### <a name="extension-packages"></a>확장 패키지

선택적 확장 패키지 ( `com.microsoft.mixedreality.toolkit.extensions)` MRTK의 기능을 확장 하는 추가 구성 요소 포함)

| 폴더 | 구성 요소 | Description |
| --- | --- | --- |
| MRTK/Extensions | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | 트레일러 지원을 추가 하는 서비스입니다. |
| | LostTrackingService | Microsoft HoloLens 장치에서 추적 손실의 처리를 간소화 하는 서비스입니다. |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | 부드러운 장면 전환 추가를 간소화 하는 서비스입니다. |
| | 샘플 ~ | 샘플 장면 및 자산을 포함 하는 숨겨진 (Unity 편집기) 폴더입니다. |

예제 프로젝트를 포함 하는 패키지를 사용 하는 프로세스에 대 한 자세한 내용은 [Mixed Reality Toolkit 및 Unity 패키지 관리자](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) 문서에서 찾을 수 있습니다.

종속성:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="tools-package"></a>도구 패키지

선택적 도구 패키지 ( `com.microsoft.mixedreality.toolkit.tools)` 혼합 현실 환경 만들기에 유용한 도구 포함) 일반적으로 이러한 도구는 편집기 구성 요소 이며 해당 코드는 응용 프로그램의 일부로 제공 되지 않습니다.

| 폴더 | 구성 요소 | Description |
| --- | --- | --- |
| MRTK/Tools | |
| | BuildWindow | UWP 응용 프로그램 빌드 및 배포 프로세스를 간소화 하는 데 도움이 되는 도구입니다. |
| | [DependencyWindow](../features/tools/dependency-window.md) | 프로젝트의 자산에 대 한 종속성 그래프를 만드는 도구입니다. |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | 확장 서비스를 만드는 데 도움이 되는 마법사입니다. |
| | [MigrationWindow](../features/tools/migration-window.md) | 사용 되지 않는 MRTK 구성 요소를 사용 하는 코드 업데이트에 도움이 되는 도구입니다.  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | Unity에서 최상의 성능을 위해 혼합 현실 프로젝트를 자동으로 구성 하는 데 도움이 되는 유틸리티입니다. |
| | ReserializeAssetsUtility | 특정 Unity 파일을 다시 serialize 하기 위한 지원을 제공 합니다. |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | 개발자가 하드웨어 컨트롤러에 대 한 Unity 매핑을 신속 하 게 결정할 수 있도록 하는 유틸리티입니다. |
| | ScreenshotUtility | Unity 편집기에서 응용 프로그램 이미지를 캡처할 수 있습니다. |
| | TextureCombinerWindow | 그래픽 질감을 결합 하는 유틸리티입니다. |
| | [도구 상자](../features/ux-building-blocks/toolbox.md) | MRTK UX 구성 요소를 쉽게 검색 하 고 사용할 수 있도록 하는 UI입니다. |

종속성:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="test-utilities-package"></a>유틸리티 패키지 테스트

선택적 테스트 유틸리티 패키지 ()에는 `com.microsoft.mixedreality.toolkit.testutilities` 개발자가 재생 모드 테스트를 쉽게 만들 수 있도록 하는 도우미 스크립트 컬렉션이 포함 되어 있습니다. 이러한 유틸리티는 MRTK 구성 요소를 만드는 개발자에 게 특히 유용 합니다.

| 폴더 | 구성 요소 | Description |
| --- | --- | --- |
| MRTK/테스트 | |
| | TestUtilities | 손 시뮬레이션 유틸리티를 포함하여 재생 모드 테스트 만들기를 간소화하는 방법입니다. |

종속성:

- Foundation( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="examples-package"></a>예제 패키지

예제 패키지( `com.microsoft.mixedreality.toolkit.examples` )는 개발자가 관심 있는 예제만 가져올 수 있도록 구조화되어 있습니다.

예제 프로젝트가 포함된 패키지를 사용하는 프로세스에 대한 자세한 내용은 [Mixed Reality Toolkit 및 Unity 패키지 관리자](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) 문서에서 찾을 수 있습니다.

| 폴더 | 구성 요소 | Description |
| --- | --- | --- |
| MRTK/예제 | | |
| | 샘플~ | 샘플 장면 및 자산이 포함된 숨겨진(Unity 편집기) 폴더입니다. |
| | StandardAssets | 여러 데모 장면에서 공유하는 공통 자산입니다. |

종속성:

- Foundation( `com.microsoft.mixedreality.toolkit.foundation` )
- 확장 기능(`com.microsoft.mixedreality.toolkit.extensions`)

## <a name="see-also"></a>참조

- [아키텍처 개요](../architecture/overview.md)
- [시스템, 확장 서비스 및 데이터 공급자](../architecture/systems-extensions-providers.md)
- [Mixed Reality Toolkit 및 Unity 패키지 관리자](../configuration/usingupm.md)
