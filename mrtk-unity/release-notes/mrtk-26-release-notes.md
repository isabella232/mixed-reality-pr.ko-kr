---
title: MRTK 2.6 릴리스 정보
description: MRTK 버전 2.6의 릴리스 정보
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 4ac82f7e07135e840886fef810844ff00ef1ac1e
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647187"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a>Microsoft Mixed Reality Toolkit 2.6 릴리스 정보

> [!IMPORTANT]
> ARM64를 사용하여 Microsoft HoloLens 2용으로 빌드된 애플리케이션에 영향을 주는 알려진 컴파일러 문제가 있습니다. 이 문제는 Visual Studio 2019를 버전 16.8 이상으로 업데이트하여 해결되었습니다. Visual Studio 업데이트할 수 없는 경우 패키지를 `com.microsoft.mixedreality.toolkit.tools` 가져와서 해결 방법을 적용하세요.

## <a name="whats-new-in-262"></a>2.6.2의 새로운 내용

### <a name="corrects-parenting-of-the-spatial-mesh"></a>공간 메시의 부모링을 수정합니다.

Mixed Reality Playspace 개체가 이동된 후 공간 메시가 제대로 배치되지 않는 [문제를](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) 해결합니다(예: 원격 포트를 통해).

## <a name="whats-new-in-261"></a>2.6.1의 새로운 내용

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a>HoloLens 2/UWP에서 실행되지 않는 OpenXR 수정

MRTK의 OpenXR 지원이 UWP에서 실행되지 않도록 하는 회귀를 수정합니다.

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a>Leap Motion ObjectManipulator가 회전하지 않는 문제를 해결합니다.

ObjectManipulator 스크립트에서 Leap Motion 손의 회전을 고려하지 않은 회귀를 수정합니다.

### <a name="sample-scene-updates"></a>샘플 장면 업데이트

Unity 플러그 인의 제공된 상태를 올바르게 반영하도록 장면 이해 샘플 장면을 업데이트합니다. 또한 가져오는 공간 인식 샘플 장면에 더 이상 종속되지 않도록 샘플을 업데이트합니다. 2.6.1로 업데이트하기 전에 가져온 장면 이해 및 공간 인식 샘플이 가능한 충돌을 방지하기 위해 프로젝트에 있는 경우 삭제해야 합니다. 이러한 샘플을 제거하지 않고 콘솔의 샘플과 관련된 충돌이 표시되는 경우 샘플(또는 `Assets/Samples/Mixed Reality Toolkit Examples` 폴더)을 모두 제거한 다음 다시 가져옵니다.

대화 예제 장면을 업데이트하여 현재 대화 시나리오를 올바르게 설명합니다.

## <a name="whats-new-in-260"></a>2.6.0의 새로운 내용
<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a>OpenXR에 대한 지원 추가

Unity의 OpenXR 미리 보기 패키지 및 Microsoft의 Mixed Reality OpenXR 패키지에 대한 초기 지원이 추가되었습니다. 자세한 내용은 [MRTK/XRSDK 시작 페이지,](../configuration/getting-started-with-mrtk-and-xrsdk.md) [Unity의 포럼 게시물](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)또는 [Microsoft 설명서를 참조하세요.](/windows/mixed-reality/develop/unity/openxr-getting-started)

> [!IMPORTANT]
> Unity의 OpenXR은 Unity 2020.2 이상에서만 지원됩니다.
>
> 현재 x64 및 ARM64 빌드만 지원합니다.

### <a name="asset-swap-utility"></a>자산 교환 유틸리티

Unity 장면의 여러 자산을 새 [Asset Swap 유틸리티](../features/tools/asset-swap-utility.md)로 교환합니다.

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a>이제 MRTK에서 HP 모션 컨트롤러 지원

HP Reverb G2용 컨트롤러는 이제 MRTK에서 기본적으로 작동합니다.

### <a name="experimental-interactive-element--state-visualizer"></a>실험적 대화형 요소 + 상태 시각화 도우미

Interactive Element는 MRTK 입력 시스템에 대한 간소화된 중앙 집중식 진입점입니다. 여기에는 상태 관리 메서드, 이벤트 관리 및 핵심 상호 작용 상태에 대한 상태 설정 논리가 포함됩니다. 자세한 내용은 [Interactive 요소 설명서를 참조하세요.](../features/experimental/interactive-element.md)

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

상태 시각화 도우미는 Interactive 요소에 의존하는 애니메이션 구성 요소입니다.  이 구성 요소는 애니메이션 클립을 만들고, 키 프레임을 설정하고, Animator 상태 컴퓨터를 생성합니다. 자세한 내용은 [상태 시각화 도우미 설명서를 참조하세요.](../features/experimental/interactive-element.md#state-visualizer-experimental)

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a>이제 모든 플랫폼에서 원격 포트 제스처를 통해 원격 보고가 지원됨

이제 사용자는 원격 이동 제스처를 사용하여 모든 플랫폼에서 재생 공간을 이동할 수 있습니다. 기본 구성을 사용하여 MR 디바이스에서 컨트롤러와 원격 통신하려면 엄지스틱을 사용합니다. 굴절된 손으로 원격 이동하려면 손끝이 인덱스 및 엄지 손가락으로 바깥쪽을 향하도록 제스처를 만들고, 인덱스 손가락으로 말려서 원격 통신을 완료합니다. 입력 시뮬레이션을 사용하여 원격 전송하려면 업데이트된 [입력 시뮬레이션 서비스 설명서를](../features/input-simulation/input-simulation-service.md)참조하세요.

  ![원격 이동 제스처](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a>이제 MRTK에서 실험적 공간 인식 관찰자로 장면 이해 사용 가능

[Scene Understanding의](/windows/mixed-reality/scene-understanding) 실험적 지원은 MRTK 2.6에서 도입되었습니다. 사용자는 MRTK 기반 프로젝트에서 공간 인식 관찰자로 HoloLens 2 장면 이해 기능을 통합할 수 있습니다. 자세한 내용은 [Scene Understanding 설명서를](../features/spatial-awareness/scene-understanding.md) 참조하세요.

> [!IMPORTANT]
> Scene Understanding은 HoloLens 2 및 Unity 2019.4 이상에서만 지원됩니다.
>
> 이 기능을 사용하려면 [이제 Mixed Reality 기능 도구를](https://aka.ms/MRFeatureTool)통해 사용할 수 있는 Scene Understanding 패키지가 필요합니다.
> Mixed Reality 기능 도구를 사용하거나 UPM을 통해 가져오는 경우 종속성 문제로 인한 실험적 - 장면해결 샘플을 가져오기 전에 Demos - SpatialAwareness 샘플을 가져오세요. 자세한 내용은 [이 GitHub 문제를](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 참조하세요.

  ![장면 이해](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a>런타임 프로필 전환 지원

MRTK는 이제 MRTK 인스턴스를 초기화하기 전(예: MRTK 초기화 프로필 전환 전) 및 프로필이 활성 사용 중이 된 후(즉, 활성 프로필 스위치) 모두에 프로필 전환을 허용합니다. 이전 스위치는 하드웨어의 기능에 따라 선택 구성 요소를 사용하도록 설정하는 데 사용할 수 있으며, 후자는 사용자가 애플리케이션의 하위 부분을 입력할 때 환경을 수정하는 데 사용할 수 있습니다. 자세한 내용 및 코드 [샘플은 프로필 전환에](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) 대한 설명서를 참조하세요.

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a>실험에서 퇴사한 방향 표시기 및 팔로우 해결기

두 개의 새 해결기를 주선 MRTK와 함께 사용할 준비가 완료되었습니다.

  ![방향 표시기 해결기](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a>손 감독과 실험적 승부

이제 손 감독 기능이 주선 MRTK와 함께 사용할 준비가 되었습니다.
  ![손 감독 예제](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a>실험적 대화 상자 컨트롤

이제 대화 상자 컨트롤을 주선 MRTK와 함께 사용할 준비가 되었습니다.

  ![대화 상자 컨트롤](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a>실험적에서 펄스 셰이더가 분리되었습니다.

펄스 셰이더 스크립트는 실험적 스크립트에서 제외되었습니다. 자세한 내용은 [펄스 셰이더 설명서를 참조하세요.](../features/rendering/pulse-shader.md)

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a>입력 기록 서비스 개선

`InputRecordingService` 이제 및 `InputPlaybackService` 는 시선 응시 입력을 기록하고 재생할 수 있습니다. 기록 파일 크기 및 저장 시간도 약 50% 줄이면서 기록 기간 동안 일관된 프레임 속도 보장을 위해 녹화가 최적화되었습니다. 이제 기록 파일의 저장 및 로드를 비동기적으로 수행할 수 있습니다. 이 MRTK 버전에서 기록의 파일 형식이 변경되었습니다. 새 버전 1.1 사양에 대한 자세한 내용은 [여기를](../features/input-simulation/input-animation-file-format.md) 참조하세요.

### <a name="reading-mode"></a>읽기 모드

HoloLens 2 [읽기 모드에](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) 대한 지원이 추가되었습니다. 읽기 모드는 시스템의 보기 필드를 줄이지만 Unity 출력의 크기 조정은 제거합니다. Unity에서 렌더링된 픽셀은 HoloLens 2 프로젝션된 픽셀에 해당합니다. 애플리케이션 작성자는 여러 개인과 함께 테스트를 수행하여 앱에서 이 절충이 절충되었는지 확인해야 합니다.

  ![Windows Mixed Reality 읽기 모드](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a>UWP에서 3D 앱 시작 관리자 지원

UWP용 [3D 앱 시작 관리자를](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 설정하는 기능을 추가합니다. 이 설정은 MRTK 빌드 창과 MRTK 프로젝트 설정의 빌드 설정에서 모두 노출됩니다. Unity에서 빌드하는 동안 프로젝트에 자동으로 기록됩니다.

  ![빌드 설정](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a>주요 변경 내용

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a>가져온 GLTF 개체의 특정 필드가 이제 대문자로 표시됩니다.

deserialization 관련 문제로 인해 가져온 GLTF 개체의 일부 필드가 이제 대문자로 시작합니다. 영향을 받는 필드는 (새 이름에 있음): `ComponentType` , , , , , , , , , `Path` , `Interpolation` `Target` `Type` `Mode` `MagFilter` `MinFilter` `WrapS` `WrapT` 입니다.

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a>입력 애니메이션 이진 파일의 버전 1.1 형식이 업데이트되었습니다.

및 에서 사용하는 입력 애니메이션 이진 `InputRecordingService` `InputPlaybackService` 파일에는 이제 이러한 두 서비스에 대한 최적화를 사용할 수 있도록 업데이트된 파일 형식이 있습니다. 새 버전 1.1 사양에 대한 자세한 내용은 [여기를](../features/input-simulation/input-animation-file-format.md) 참조하세요.

### <a name="msbuild-for-unity-support"></a>Unity용 MSBuild 지원

Unity용 MSBuild에 대한 지원은 [Unity의 새 패키지 지침](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)에 맞게 2.5.2 릴리스부터 제거되었습니다.

## <a name="known-issues"></a>알려진 문제

### <a name="openxr"></a>OpenXR

현재 홀로그램 Remoting 및 OpenXR에는 손합을 일관되게 사용할 수 없는 알려진 문제가 있습니다.
또한 눈 추적 샘플 장면은 현재 호환 되지 않습니다. 단, 눈 추적이 *작동 합니다* .

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>일부 혼합 현실 도구 키트 표준 셰이더 기능에는 기본 패키지가 필요 합니다.

Unity 패키지 관리자를 통해 가져올 때 MRTK 표준 셰이더 유틸리티 스크립트 (예: HoverLight)는 표준 자산 패키지의 셰이더와 함께 배치 되지 않습니다. 이 기능에 액세스 하려면 응용 프로그램에 기반 패키지를 가져와야 합니다.

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache는 종료 시 새 카메라를 만들 수 있습니다.

일부 상황에서 (예: Unity 편집기에서 LeapMotion 공급자를 사용 하는 경우) CameraCache가 종료 시 MainCamera를 다시 만들 수 있습니다. 자세한 내용은 [이 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 를 참조 하세요.

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>Unity 패키지 관리자를 통해 예제를 가져오는 경우 System.io.filenotfoundexception

프로젝트 경로의 길이에 따라 Unity 패키지 관리자를 통해 예제를 가져오면 Unity 콘솔에서 System.io.filenotfoundexception 메시지가 생성 될 수 있습니다. 이 오류의 원인은 MAX_PATH (256 자) 보다 긴 "누락 된" 파일의 경로입니다. 해결 하려면 프로젝트 경로의 길이를 줄이십시오.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Spatializer가 지정 되지 않았습니다. 응용 프로그램에서 공간 소리를 지원 하지 않습니다.

오디오 spatializer 구성 되지 않은 경우 "No spatializer가 지정 되었습니다." 경고가 표시 됩니다. XR 패키지를 설치 하지 않은 경우에 이러한 문제가 발생할 수 있습니다. Unity는 이러한 패키지에 spatializers를 포함 합니다.

이 문제를 해결 하려면 다음을 확인 하세요.

- **창**  >  **패키지 관리자** 에 XR 패키지가 하나 이상 설치 되어 있습니다.
- **Mixed Reality Toolkit**  >  **유틸리티**  >  **Unity 프로젝트를 구성** 하 고 **오디오 Spatializer** 를 선택 합니다.

  ![오디오 Spatializer 선택](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: 개체 참조가 개체의 인스턴스로 설정 되지 않았습니다 (SceneTransitionService.Initialize).

경우에 따라를 열면 `EyeTrackingDemo-00-RootScene` SceneTransitionService 클래스의 Initialize 메서드에서 NullReferenceException이 발생할 수 있습니다.
이 오류는 장면 전환 서비스의 구성 프로필이 설정 되어 있지 않기 때문에 발생 합니다. 해결 하려면 다음 단계를 사용 하세요.

- `MixedRealityToolkit`계층의 개체로 이동 합니다.
- 검사기 창에서 다음을 선택 합니다. `Extensions`
- 확장 되지 않은 경우 확장 합니다. `Scene Transition Service`
- 의 값을 `Configuration Profile` **MRTKExamplesHubSceneTransitionServiceProfile** 로 설정 합니다.

![장면 전환 프로필 수정](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus Quest

현재 [독립 실행형 플랫폼을 대상으로 하는 경우에서 Oculus XR 플러그 인](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)을 사용 하는 알려진 문제가 있습니다.  업데이트에 대 한 Oculus 버그 추적기/포럼/릴리스 정보를 확인 하세요.

이 세 가지 오류 집합을 사용 하 여 버그를 표시 합니다.

![Oculus XR 플러그 인 오류](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI 및 TextMeshPro

최신 버전의 TextMeshPro (1.5.0 + 또는 2.1.1 +)에 대 한 알려진 문제는 드롭다운의 기본 글꼴 크기와 굵은 글꼴 문자 간격이 변경 된 것입니다.

![TMP 이미지](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

이 작업은 이전 버전의 TextMeshPro으로 다운 그레이드 하 여 해결할 수 있습니다. 자세한 내용은 [문제 #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) 를 참조 하세요.