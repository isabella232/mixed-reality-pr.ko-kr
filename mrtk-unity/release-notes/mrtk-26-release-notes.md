---
title: MRTK 2.6 릴리스 정보
description: MRTK 버전 2.6에 대 한 릴리스 정보
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK,
ms.openlocfilehash: c172e5d071bba22626e9c35b2b4318f1ff779335
ms.sourcegitcommit: f7839221c9549e60a2c3ac2dbd39f07a6851dcd2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2021
ms.locfileid: "112562513"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a>Microsoft Mixed Reality Toolkit 2.6 릴리스 정보

> [!IMPORTANT]
> ARM64를 사용 하 여 Microsoft HoloLens 2 용으로 빌드된 응용 프로그램에 영향을 주는 알려진 컴파일러 문제가 있습니다. 이 문제는 Visual Studio 2019을 버전 16.8 이상으로 업데이트 하 여 해결할 수 있습니다. Visual Studio를 업데이트할 수 없는 경우에는 패키지를 가져와 `com.microsoft.mixedreality.toolkit.tools` 해결 방법을 적용 하십시오.

## <a name="whats-new-in-262"></a>2.6.2 critical의 새로운 기능

### <a name="corrects-parenting-of-the-spatial-mesh"></a>공간 메시의 부모로 수정 합니다.

혼합 현실 Playspace 개체가 이동 된 후 공간 메시가 제대로 배치 되지 않은 [문제](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) 를 수정 합니다 (예: 텔레포트를 통해).

## <a name="whats-new-in-261"></a>2.6.1의 새로운 기능

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a>HoloLens 2/UWP에서 실행 되지 않는 OpenXR 수정

UWP에서 MRTK의 OpenXR 지원이 실행 되지 못하도록 하는 회귀를 수정 합니다.

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a>도약 동작 ObjectManipulator 회전 안 함 수정

ObjectManipulator 스크립트에서 윤 움직임의 회전이 고려 되지 않은 회귀를 수정 합니다.

### <a name="sample-scene-updates"></a>샘플 장면 업데이트

는 Unity 플러그 인의 제공 된 상태를 올바르게 반영 하도록 장면 이해 샘플 장면을 업데이트 합니다. 는 가져오는 공간 인식 샘플 장면에 더 이상 종속 되지 않도록 샘플을 업데이트 합니다. 2.6.1으로 업데이트 하기 전에 가져온 장면 이해 및 공간 인식 샘플이 프로젝트에 있는 경우 충돌을 방지 하기 위해이를 삭제 해야 합니다. 이러한 샘플을 제거 하지 않은 경우 콘솔의 해당 샘플과 관련 된 충돌을 확인 하려면 두 샘플 (또는 폴더)을 제거한 `Assets/Samples/Mixed Reality Toolkit Examples` 다음 가져오기를 다시 시도 하세요.

대화 상자 예제 장면을 업데이트 하 여 현재 대화 상자 시나리오를 올바르게 설명 합니다.

## <a name="whats-new-in-260"></a>2.6.0의 새로운 기능

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a>OpenXR에 대 한 지원 추가

Unity의 OpenXR 미리 보기 패키지 및 Microsoft의 Mixed Reality OpenXR 패키지에 대 한 초기 지원이 추가 되었습니다. 자세한 내용은 [MRTK/XRSDK 시작 페이지](../configuration/getting-started-with-mrtk-and-xrsdk.md), [Unity의 포럼 게시물](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)또는 [Microsoft 설명서](/windows/mixed-reality/develop/unity/openxr-getting-started) 를 참조 하세요.

> [!IMPORTANT]
> Unity의 OpenXR는 Unity 2020.2 이상 에서만 지원 됩니다.
>
> 현재는 x64 및 ARM64 빌드에서만 지원 합니다.

### <a name="asset-swap-utility"></a>자산 교환 유틸리티

새 [자산 교환 유틸리티](../features/tools/asset-swap-utility.md)를 사용 하 여 Unity 장면에서 여러 자산을 교환 합니다.

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a>이제 MRTK로 지원 되는 HP 동작 컨트롤러

HP 반향 G2 용 컨트롤러는 이제 MRTK를 사용 하 여 기본적으로 작동 합니다.

### <a name="experimental-interactive-element--state-visualizer"></a>실험적 대화형 요소 + 상태 시각화 도우미

Interactive 요소는 MRTK 입력 시스템에 대 한 단순화 된 중앙 진입점입니다. 상태 관리 메서드, 이벤트 관리 및 핵심 상호 작용 상태에 대 한 상태 설정 논리가 포함 됩니다. 자세한 내용은 [대화형 요소 설명서](../features/experimental/interactive-element.md)를 참조 하세요.

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

상태 시각화 도우미는 대화형 요소에 의존 하는 애니메이션 구성 요소입니다. 이 구성 요소는 애니메이션 클립을 만들고, 키 프레임을 설정 하 고, 애니메이터 상태 시스템을 생성 합니다. 자세한 내용은 [상태 시각화 도우미 설명서](../features/experimental/interactive-element.md#state-visualizer-experimental) 를 참조 하세요.

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a>Teleportation 이제 모든 플랫폼에서 지원 되는 텔레포트 제스처가 있습니다.

사용자는 이제 텔레포트 제스처를 사용 하 여 모든 플랫폼에서 재생 공간 주위를 이동할 수 있습니다. 기본 구성을 사용 하 여 MR 장치의 컨트롤러를 텔레포트 하려면 엄지 스틱을 사용 합니다. 트레일러 식으로 텔레포트 하려면 인덱스 손가락을 curl 하 여 텔레포트를 완료 하 고 인덱스 및 엄지 단추를 사용 하 여 손을 향한 제스처를 만듭니다. 입력 시뮬레이션을 사용 하 여 텔레포트 하려면 업데이트 된 [입력 시뮬레이션 서비스 설명서](../features/input-simulation/input-simulation-service.md)를 참조 하세요.

![텔레포트 제스처](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a>현재 MRTK에서 실험적 공간 인식 관찰자로 제공 되는 장면 이해

[장면 이해](/windows/mixed-reality/scene-understanding) 의 실험적 지원은 MRTK 2.6에서 도입 되었습니다. 사용자는 HoloLens 2의 장면 이해 기능을 MRTK 기반 프로젝트의 공간 인식 관찰자로 통합할 수 있습니다. 자세한 내용은 [장면 이해 설명서](../features/spatial-awareness/scene-understanding.md) 를 참조 하세요.

> [!IMPORTANT]
> 장면 이해는 HoloLens 2 및 Unity 2019.4 이상 에서만 지원 됩니다.
>
> 이 기능에는 이제 [혼합 현실 기능 도구](https://aka.ms/MRFeatureTool)를 통해 사용할 수 있는 장면 이해 패키지가 필요 합니다.
> Mixed Reality 기능 도구를 사용 하거나 UPM를 통해 다른 방법으로 가져오는 경우 종속성 문제로 인해 실험적-SceneUnderstanding 샘플을 가져오기 전에 SpatialAwareness 샘플을 가져오세요. 자세한 내용은 [이 GitHub 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 를 참조 하세요.

![장면 이해](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a>런타임 프로필 전환 지원

이제 MRTK를 사용 하면 MRTK 인스턴스를 초기화 하기 전에 (즉, 이전 MRTK 초기화 프로필 스위치) 프로필을 전환할 수 있으며 프로필이 활성 상태인 경우 (즉, 활성 프로필 스위치) 사용 됩니다. 이전 스위치를 사용 하 여 하드웨어의 기능을 기반으로 하는 구성 요소를 선택 하 고, 후자를 사용 하 여 사용자가 응용 프로그램의 하위 부분를 시작할 때 환경을 수정할 수 있습니다. 자세한 내용 및 코드 샘플은 [프로필 전환에](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) 대 한 설명서를 참조 하세요.

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a>방향 표시기 및 실험적에서 solvers 그라데이션 따르기

두 개의 새로운 solvers는 중요 한 MRTK에서 사용할 준비가 되었습니다.

![방향 표시기 해 찾기](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a>실험적에서 Coach 그라데이션

이제는 Coach 기능을 중요 한 MRTK에서 사용할 준비가 되었습니다.

![핸드 Coach 예제](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a>실험적의 대화 상자 컨트롤 그라데이션

이제 대화 상자 컨트롤을 중요 한 MRTK에서 사용할 준비가 되었습니다.

![대화 상자 컨트롤](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a>실험에서의 펄스 셰이더

펄스 셰이더 스크립트는 실험적에서의 그라데이션입니다. 자세한 내용은 [펄스 셰이더 설명서](../features/rendering/pulse-shader.md) 를 참조 하세요.

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a>입력 기록 서비스의 향상 된 기능

`InputRecordingService``InputPlaybackService`이제는 눈에 멋진 입력을 기록 하 고 재생할 수 있습니다. 기록은 파일 크기를 기록 하는 동안 기록 기간 동안 일관 된 프레임 속도를 보장 하도록 최적화 되었으며 절약 시간은 약 50%로 줄어듭니다. 이제 기록 파일의 저장 및 로드를 비동기적으로 수행할 수 있습니다. 이 MRTK 버전에서 기록의 파일 형식이 변경 되었습니다. 새 버전 1.1 사양에 대 한 자세한 내용은 [여기](../features/input-simulation/input-animation-file-format.md) 를 참조 하세요.

### <a name="reading-mode"></a>읽기 모드

HoloLens 2의 [읽기 모드](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) 에 대 한 지원이 추가 되었습니다. 읽기 모드를 통해 시스템의 뷰 필드가 줄어들지만 Unity의 출력 크기가 제거 됩니다. Unity에서 렌더링 되는 픽셀은 HoloLens 2의 예상 픽셀에 해당 합니다. 응용 프로그램 작성자는 여러 개인을 사용 하 여 테스트를 수행 하 여 앱에서 원하는 균형을 유지 해야 합니다.

![Windows Mixed Reality 읽기 모드](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a>UWP에서 3D 앱 서비스에 대 한 지원

UWP 용 [3d 앱 시작 관리자](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 를 설정 하는 기능을 추가 합니다. 이 설정은 MRTK 빌드 창과 MRTK 프로젝트 설정의 빌드 설정에서 모두 제공 됩니다. Unity에서 빌드하는 동안 프로젝트에 자동으로 기록 됩니다.

![빌드 설정](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a>주요 변경 내용

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a>가져온 개체의 특정 필드는 이제 대문자로 되어 있습니다.

Deserialization 관련 문제로 인해 가져온 잘못 된 개체의 일부 필드가 현재 대문자로 시작 됩니다. 영향을 받는 필드는 (새 이름),,,,,,,,, 등 `ComponentType` `Path` `Interpolation` `Target` `Type` `Mode` `MagFilter` `MinFilter` `WrapS` `WrapT` 입니다.

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a>입력 애니메이션 이진 파일에 업데이트 된 버전 1.1 형식이 있습니다.

및에서 사용 되는 입력 애니메이션 이진 파일에는 `InputRecordingService` `InputPlaybackService` 이제 이러한 두 서비스에 대 한 최적화를 사용 하도록 설정 하는 업데이트 된 파일 형식이 있습니다. 새 버전 1.1 사양에 대 한 자세한 내용은 [여기](../features/input-simulation/input-animation-file-format.md) 를 참조 하세요.

### <a name="msbuild-for-unity-support"></a>Unity 용 MSBuild 지원

Unity의 [새 패키지 지침](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)에 맞게 2.5.2 릴리스에서 MSBuild에 대 한 지원이 제거 되었습니다.

## <a name="known-issues"></a>알려진 문제

### <a name="openxr"></a>OpenXR

현재 Holographic Remoting 및 OpenXR에는 알려진 문제가 있으며,이는 손으로의 조인트를 일관 되 게 사용할 수 없습니다.
또한 눈 추적 샘플 장면은 현재 호환 되지 않습니다. 단, 눈 추적이 _작동 합니다_ .

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

현재 [독립 실행형 플랫폼을 대상으로 하는 경우에서 Oculus XR 플러그 인](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)을 사용 하는 알려진 문제가 있습니다. 업데이트에 대 한 Oculus 버그 추적기/포럼/릴리스 정보를 확인 하세요.

이 세 가지 오류 집합을 사용 하 여 버그를 표시 합니다.

![Oculus XR 플러그 인 오류](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI 및 TextMeshPro

최신 버전의 TextMeshPro (1.5.0 + 또는 2.1.1 +)에 대 한 알려진 문제는 드롭다운의 기본 글꼴 크기와 굵은 글꼴 문자 간격이 변경 된 것입니다.

![TMP 이미지](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

이 작업은 이전 버전의 TextMeshPro으로 다운 그레이드 하 여 해결할 수 있습니다. 자세한 내용은 [문제 #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) 를 참조 하세요.
