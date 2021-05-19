---
title: HTK에서 MRTK로 이식 가이드
description: HoloLens Toolkit(HTK)에서 MRTK(Mixed Reality Toolkit)로 마이그레이션
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, HTK,
ms.openlocfilehash: fbcb2863c894a4e4c1529e19112b33712f69e99f
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143765"
---
# <a name="porting-guide"></a>포팅 가이드

HoloLens Toolkit(HTK)에서 MRTK(Mixed Reality Toolkit)로 마이그레이션하는 데 도움이 되는 가이드입니다.

## <a name="controller-and-hand-input"></a>컨트롤러 및 손 입력

### <a name="setup-and-configuration"></a>설정 및 구성

|         메서드                  | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 유형                      | 관련된 경우 입력 형식 정보가 있는 단추에 대한 특정 이벤트입니다. | 이벤트를 통해 전달되는 동작/제스처 기반 입력입니다. |
| 설치 프로그램                     | 장면에 InputManager를 배치합니다. | [구성 프로필에서](../configuration/mixed-reality-configuration-guide.md) 입력 시스템을 사용하도록 설정하고 구체적인 입력 시스템 유형을 지정합니다. |
| 구성             | 장면의 각 개별 스크립트에 대해 검사기에서 구성됩니다. | 아래에 나열된 Mixed Reality 입력 시스템 프로필 및 관련 프로필을 통해 구성됩니다. |

관련 프로필:

* Mixed Reality 컨트롤러 매핑 프로필
* Mixed Reality 컨트롤러 시각화 프로필
* Mixed Reality 제스처 프로필
* Mixed Reality 입력 작업 프로필
* Mixed Reality 입력 작업 규칙 프로필
* 포인터 프로필 Mixed Reality

[응시 공급자](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider) 설정은 장면의 주 카메라 개체에서 수정 됩니다.

플랫폼 지원 구성 요소 (예: Windows Mixed Reality 장치 관리자)를 해당 서비스의 데이터 공급자에 추가 해야 합니다.

### <a name="interface-and-event-mappings"></a>인터페이스 및 이벤트 매핑

일부 이벤트는 더 이상 고유한 이벤트를 포함 하지 않으며 이제 [MixedRealityInputAction](../features/input/input-actions.md)을 포함 합니다. 이러한 작업은 입력 작업 프로필에 지정 되며 컨트롤러 매핑 프로필의 특정 컨트롤러 및 플랫폼에 매핑됩니다. 같은 이벤트 `OnInputDown` 는 이제 MixedRealityInputAction 형식을 확인 해야 합니다.

관련 입력 시스템:

* [입력 개요](../features/input/overview.md)
* [입력 이벤트](../features/input/input-events.md)
* [입력 포인터](../features/input/pointers.md)

| HTK 2017 |  MRTK v2  | 작업 매핑 |
|----------|-----------|----------------|
| `IControllerInputHandler` | [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 터치 패드 또는 엄지 스틱에 매핑됨 |
| `IControllerTouchpadHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | 터치 패드로 매핑됨 |
| `IFocusable` | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) | |
| `IGamePadHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IHoldHandler` | [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | 제스처 프로필에 포함 되도록 매핑됨 |
| `IInputClickHandler` | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) |
| `IInputHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | 컨트롤러의 단추 또는 직접 탭으로 매핑됨 |
| `IManipulationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | 제스처 프로필의 조작에 매핑됨 |
| `INavigationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | 제스처 프로필의 탐색에 매핑됨 |
| `IPointerSpecificFocusable` | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) | |
| `ISelectHandler` | [`IMixedRealityInputHandler<float>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 트리거 위치로 매핑됨 |
| `ISourcePositionHandler` | [`IMixedRealityInputHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) 또는 [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 포인터 위치 또는 그립 위치에 매핑됨 |
| `ISourceRotationHandler` | [`IMixedRealityInputHandler<Quaternion>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) 또는 [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 포인터 위치 또는 그립 위치에 매핑됨 |
| `ISourceStateHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IXboxControllerHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) 및 [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 다양한 컨트롤러 단추 및 엄지스틱에 매핑 |

## <a name="camera"></a>카메라

|        메서드                    | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 설치 프로그램                     | MainCamera를 삭제하고 MixedRealityCameraParent / MixedRealityCamera / HoloLensCamera 프리팹을 장면에 **추가하거나** Mixed Reality Toolkit > 구성 > Mixed Reality 장면 설정 적용 메뉴 항목을 사용합니다. | Mixed Reality Toolkit > 장면에 추가 및 구성...을 통해 MixedRealityPlayspace에서 부모가 된 MainCamera |
| 구성             | 프리팹 인스턴스에서 수행되는 카메라 설정 구성입니다. | [혼합 현실 카메라 프로필](xref:Microsoft.MixedReality.Toolkit.MixedRealityCameraProfile)에 구성된 카메라 설정입니다. |

## <a name="speech"></a>음성

### <a name="keyword-recognition"></a>키워드 인식

|         메서드                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 설치 프로그램                     | 장면에 SpeechInputSource를 추가합니다. | 키워드 서비스(예: Windows Speech Input Manager)를 입력 시스템의 데이터 공급자에 추가해야 합니다. |
| 구성             | 인식된 키워드는 SpeechInputSource의 검사기에서 구성됩니다. | 키워드는 Mixed Reality Speech Commands Profile 에서 [구성됩니다.](../features/input/speech.md) |
| 이벤트 처리기            | `ISpeechHandler` | [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

### <a name="dictation"></a>받아쓰기

|         메서드                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 설치 프로그램                     | 장면에 DictationInputManager를 추가합니다. | 받아쓰기 지원을 사용하려면 서비스(예: Windows 받아쓰기 입력 관리자)를 입력 시스템의 데이터 공급자에 추가해야 합니다. |
| 이벤트 처리기            | `IDictationHandler` | `IMixedRealityDictationHandler`[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

## <a name="spatial-awareness--mapping"></a>공간 인식/매핑

### <a name="mesh"></a>메시

|         메서드                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 설치 프로그램                     | 장면에 SpatialMapping prefab를 추가 합니다. | 구성 프로필에서 공간 인식 시스템을 사용 하도록 설정 하 고 공간 인식 시스템의 데이터 공급자에 공간 관찰자 (예: Windows Mixed Reality 공간 메시 관찰자)를 추가 합니다. |
| 구성             | 검사기에서 장면 인스턴스를 구성 합니다. | 각 공간 관찰자 프로필에 대 한 설정을 구성 합니다. |

### <a name="planes"></a>평면

|         메서드                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 설치 프로그램                     | 스크립트를 사용 `SurfaceMeshesToPlanes` 합니다. | 아직 구현되지 않았습니다. |

### <a name="spatial-understanding"></a>공간 이해

|       메서드                      | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 설치 프로그램                     | 장면에 SpatialUnderstanding prefab를 추가 합니다. | 아직 구현되지 않았습니다. |
| 구성             | 검사기에서 장면 인스턴스를 구성 합니다. | 아직 구현되지 않았습니다. |

## <a name="boundary"></a>경계

|         메서드                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 설치 프로그램                     | `BoundaryManager`장면에 스크립트를 추가 합니다. | 구성 프로필에서 경계 시스템을 사용 하도록 설정 합니다. |
| 구성             | 검사기에서 장면 인스턴스를 구성 합니다. | 경계 시각화 프로필에서 설정을 구성 합니다. |

## <a name="sharing"></a>공유

|             메서드               | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 설치 프로그램                     | 공유 서비스: 장면에 공유 프리팹을 추가합니다. UNet: SharingWithUNET 예제를 사용합니다. | 진행 중 |
| 구성             | 검사기에서 장면 인스턴스를 구성합니다. | 진행 중 |

## <a name="ux"></a>Ux

|         메서드                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 단추                     | [상호 작용 가능한 개체](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Button](../features/ux-building-blocks/Button.md) |
| 상호 작용 가능                     | [상호 작용 가능한 개체](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [상호 작용 가능](../features/ux-building-blocks/Interactable.md) |
| 경계 상자             | [경계 상자](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [경계 상자](../features/ux-building-blocks/bounding-box.md) |
| 앱 바             | [앱 바](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [앱 바](../features/ux-building-blocks/app-bar.md) |
| 한 손 조작(Grb 및 이동)   | [HandDraggable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/HandDraggable.cs) | [조작 처리기](../features/ux-building-blocks/manipulation-handler.md) |
| 두 손 조작(잡기/이동/회전/배율)             | [TwoHandManipulatable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/TwoHandManipulatable.cs) | [조작 처리기](../features/ux-building-blocks/manipulation-handler.md) |
| 키보드             | [키보드 프리팹]() | [시스템 키보드](../features/ux-building-blocks/system-keyboard.md) |
| Tooltip             | [도구 설명](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_TooltipExample.md) | [도구 설명](../features/ux-building-blocks/tooltip.md) |
| 개체 컬렉션             | [개체 컬렉션](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md) | [개체 컬렉션](../features/ux-building-blocks/object-collection.md) |
| Solver             | [Solver](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Readme/README_SolverSystem.md) | [Solver](../features/ux-building-blocks/solvers/solver.md) |

## <a name="utilities"></a>유틸리티

일부 유틸리티는 해 찾기 시스템에서 중복으로 조정 되었습니다. 필요한 스크립트가 없는 경우 문제를 파일에 입력 하십시오.

| HTK 2017 |  MRTK v2  |
|----------|-----------|
| 빌보드 | [`Billboard`](xref:Microsoft.MixedReality.Toolkit.UI.Billboard) |
| Tagalong | [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) 또는 [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) [해 찾기](../features/ux-building-blocks/solvers/Solver.md) |
| FixedAngularSize | [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)[해 찾기](../features/ux-building-blocks/solvers/solver.md) |
| FpsDisplay | [진단 시스템](../features/diagnostics/diagnostics-system-getting-started.md) (구성 프로필) |
| NearFade | [Mixed Reality Toolkit 표준 셰이더에](../features/rendering/mrtk-standard-shader.md) 기본 제공 |
