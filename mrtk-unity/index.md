---
title: MRTK-Unity 개발자 설명서
description: Unity용 Mixed Reality Toolkit에 대해 알아보세요.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: ecd12cb6fbed305f1a2532f0b55a6d0441df43fa537c63d9919ae9bc91a675c0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204825"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit이란 무엇인가요?

![Mixed Reality Toolkit](features/images/Logo_MRTK_Unity_Banner.png)

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyXHW]

MRTK-Unity는 Unity에서 플랫폼 간 MR 앱 개발을 가속화하는 데 사용되는 구성 요소 및 기능 집합을 제공하는 Microsoft 기반 프로젝트입니다. 일부 기능은 다음과 같습니다.

* **공간 상호 작용 및 UI를 위한 플랫폼 간 입력 시스템 및 구성 요소** 를 제공합니다.
* 변경 내용을 즉시 볼 수 있는 편집기 내 시뮬레이션을 통해 **프로토타입을 신속하게 제작** 할 수 있습니다.
* **확장 가능한 프레임워크** 로서 작동해 개발자에게 핵심 구성 요소를 교환하는 기능을 제공합니다.
* **다양한 플랫폼을 지원합니다**.

::: moniker range=">= mrtkunity-2021-05"
| 플랫폼 | 지원되는 디바이스 |
|---|---|
| OpenXR(Unity 2020.3.8+) | Microsoft HoloLens 2 <br> Windows Mixed Reality 헤드셋 |
| Windows Mixed Reality | Microsoft HoloLens <br> Microsoft HoloLens 2 <br> Windows Mixed Reality 헤드셋  |
| Oculus(Unity 2019.3 이상) | Oculus Quest |
| OpenVR |  Windows Mixed Reality 헤드셋 <br> HTC Vive <br> Oculus Rift |
| Ultraleap Hand Tracking | Ultraleap Leap 모션 컨트롤러 |
| 모바일 | iOS 및 Android |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| 플랫폼 | 지원되는 디바이스 |
|---|---|
| OpenXR(MRTK 2.6, Unity 2020.3.8+에서 미리 보기) | Microsoft HoloLens 2 <br> Windows Mixed Reality 헤드셋 |
| Windows Mixed Reality | Microsoft HoloLens <br> Microsoft HoloLens 2 <br> Windows Mixed Reality 헤드셋  |
| Oculus(Unity 2019.3 이상) | Oculus Quest |
| OpenVR |  Windows Mixed Reality 헤드셋 <br> HTC Vive <br> Oculus Rift |
| Ultraleap Hand Tracking | Ultraleap Leap 모션 컨트롤러 |
| 모바일 | iOS 및 Android |
::: moniker-end

## <a name="getting-started-with-mrtk"></a>MRTK 시작

Unity에서 MRTK 또는 Mixed Reality 개발을 처음 사용하는 경우 디바이스 또는 [에뮬레이터](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)에 MRTK 예제 허브 샘플 애플리케이션을 설치하고 탐색하는 것이 좋습니다. 

> [!div class="nextstepaction"]
> [MRTK 예제 허브 앱 다운로드](running-examples-hub.md)

Mixed Reality 및 MRTK가 제공하는 기능을 파악했다면 필요한 도구를 설치하고 초급 HoloLens 2 자습서 시리즈를 따르세요.

> [!div class="nextstepaction"]
> [도구 설치](/windows/mixed-reality/develop/install-the-tools?tabs=unity)

> [!div class="nextstepaction"]
> [HoloLens 2 자습서 시리즈](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

작동 원리를 자세히 알고 싶으신가요?
> [!div class="nextstepaction"]
> [GitHub에서 MRTK 살펴보기](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a>설명서

| [![릴리스 정보](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-27-release-notes.md)<br/>[릴리스 정보](release-notes/mrtk-26-release-notes.md)| [![MRTK 개요](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)<br/>[MRTK 개요](architecture/overview.md)|[![API 참조](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)<br/>[API 참조](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a>빌드 상태

| Branch | CI 상태 | 문서 상태 |
|---|---|---|
| `main` |[![CI 상태](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![문서 상태](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

## <a name="feature-areas"></a>기능 영역

:::row:::
    :::column:::
       [![입력 시스템](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)<br>
        **[입력 시스템](features/input/overview.md)**<br>
    :::column-end:::
    :::column:::
        [![손 추적(HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)<br>
        **[손 추적 <br> (HoloLens 2)](features/input/hand-tracking.md)**<br>
    :::column-end:::
    :::column:::
        [![시선 추적(HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)<br>
        **[시선 추적 <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**<br>
    :::column-end:::
    :::column:::
        [![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)<br>
        **[Profiles](configuration/mixed-reality-configuration-guide.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![손 추적(Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](supported-devices/leap-motion-mrtk.md)<br>
        **[손 추적 <br/> (Ultraleap)](supported-devices/leap-motion-mrtk.md)**<br>
    :::column-end:::
    :::column:::
        [![UI 컨트롤](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)<br>
        **[UI 컨트롤](#ux-building-blocks)**<br>
    :::column-end:::
    :::column:::
        [![해결기](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)<br>
        **[해결기](features/ux-building-blocks/solvers/solver.md)**<br>
    :::column-end:::
    :::column:::
        [![다중 장면 관리자](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[다중 장면<br/> 관리자](features/scene-system/scene-system-getting-started.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![공간 인식](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)<br>
        **[공간<br/> 인식](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![진단 도구](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[진단 <br/> 도구](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![MRTK 표준 셰이더 보기](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)<br>
        **[MRTK 표준 셰이더 예제 보기](features/rendering/mrtk-standard-shader.md?q=shader)**<br>
    :::column-end:::
    :::column:::
        [![음성 및 받아쓰기](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[음성](features/input/speech.md)<br/> & [받아쓰기](features/input/dictation.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![경계 시스템](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)<br>
        **[경계 <br/>시스템](features/boundary/boundary-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![편집기 내 시뮬레이션](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[편집기 내 <br/> 시뮬레이션](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![실험적 기능](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)<br>
        **[실험적<br/> 기능](contributing/experimental-features.md)**<br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a>UX 구성 요소

:::row:::
    :::column:::
       [![단추](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[단추](features/ux-building-blocks/button.md)**<br>
        HoloLens 2의 연결된 손을 포함한 다양한 입력 방법을 지원하는 단추 컨트롤
    :::column-end:::
    :::column:::
        [![경계 컨트롤](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[경계 컨트롤](features/ux-building-blocks/bounds-control.md)**<br>
        3D 공간에서 개체 조작을 위한 표준 UI
    :::column-end:::
    :::column:::
        [![개체 조작자](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[개체 조작자](features/ux-building-blocks/object-manipulator.md)**<br>
        한 손 또는 양손을 사용하여 개체를 조작하기 위한 스크립트
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![슬레이트](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[슬레이트](features/ux-building-blocks/slate.md)**<br>
        연결된 손 입력을 사용한 스크롤을 지원하는 2D 스타일 평면
    :::column-end:::
    :::column:::
        [![시스템 키보드](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[시스템 키보드](features/ux-building-blocks/system-keyboard.md)**<br>
        Unity에서 시스템 키보드를 사용하는 예제 스크립트
    :::column-end:::
    :::column:::
        [![상호 작용 가능](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[상호 작용 가능](features/ux-building-blocks/interactable.md)**<br>
        시각적 상태 및 테마 지원으로 개체를 상호 작용 가능하게 만드는 스크립트
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**<br>
        태그 동반, 신체 고정, 일정한 뷰 크기 및 표면 자성과 같은 다양한 개체 위치 지정 동작
    :::column-end:::
    :::column:::
        [![개체 컬렉션](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[개체 컬렉션](features/ux-building-blocks/object-collection.md)**<br>
        3차원 모양의 개체 배열을 배치하는 스크립트
    :::column-end:::
    :::column:::
        [![도구 설명](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[도구 설명](features/ux-building-blocks/tooltip.md)**<br>
        모션 컨트롤러 및 개체에 레이블을 지정하는 데 사용할 수 있는 유연한 앵커/피벗 시스템을 포함하는 주석 UI
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![슬라이더](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[슬라이더](features/ux-building-blocks/sliders.md)**<br>
        직접 손 추적 상호 작용을 지원하는 값 조정을 위한 슬라이더 UI
    :::column-end:::
    :::column:::
        [![MRTK 표준 셰이더](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK 표준 셰이더](features/rendering/mrtk-standard-shader.md)**<br>
        MRTK의 표준 셰이더는 성능으로 다양한 Fluent Design 요소를 지원합니다.
    :::column-end:::
    :::column:::
        [![손 메뉴](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[손 메뉴](features/ux-building-blocks/hand-menu.md)**<br>
        손 제약 조건 해결기를 사용하는 빠른 액세스용 손 잠금 UI
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![앱 바](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[앱 바](features/ux-building-blocks/app-bar.md)**<br>
        경계 컨트롤의 수동 활성화를 위한 UI
    :::column-end:::
    :::column:::
        [![포인터](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[포인터](features/input/pointers.md)**<br>
        다양한 종류의 포인터에 대해 알아보기
    :::column-end:::
    :::column:::
        [![손끝 시각화](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[손끝 시각화](features/ux-building-blocks/fingertip-visualization.md)**<br>
        직접 상호 작용에 대한 신뢰도를 향상시키는 손끝의 시각적 어포던스
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Near 메뉴](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near 메뉴](features/ux-building-blocks/near-menu.md)**<br>
        근거리 상호 작용을 위한 부동 메뉴 UI
    :::column-end:::
    :::column:::
        [![공간 인식 시작](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[공간 인식 보기](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
        홀로그램 개체가 물리적 환경과 상호 작용하게 만들기
    :::column-end:::
    :::column:::
        [![음성 명령](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[음성 명령](features/input/speech.md)**<br>
        음성 입력 통합을 위한 스크립트 및 예제
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![진행률 표시기](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[진행률 표시기](features/ux-building-blocks/progress-indicator.md)**<br>
        데이터 프로세스 또는 작업을 알려주기 위한 시각적 표시기
    :::column-end:::
    :::column:::
        [![대화 상자](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[대화 상자](features/ux-building-blocks/dialog.md)**<br>
        사용자의 확인 또는 승인을 요청하는 UI
    :::column-end:::
    :::column:::
        [![손 코치](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[손 코치](features/ux-building-blocks/hand-coach.md)**<br>
        제스처가 학습되지 않은 경우 사용자 안내를 지원하는 구성 요소
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![직접 물리학 서비스](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/extensions/hand-physics-service.md) **[직접 물리학 서비스 [실험용]](features/extensions/hand-physics-service.md)**<br>
        직접 물리학 서비스는 강체 충돌 이벤트 및 연결된 손과의 상호 작용을 지원합니다.
    :::column-end:::
    :::column:::
        [![스크롤 컬렉션](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[스크롤 컬렉션](features/ux-building-blocks/scrolling-object-collection.md)**<br>
        3D 개체를 기본적으로 스크롤하는 개체 컬렉션
    :::column-end:::
    :::column:::
        [![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [실험용]](features/experimental/dock.md)**<br>
        Dock를 사용하면 미리 결정된 위치 안팎으로 개체를 이동할 수 있습니다.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![시선 추적: 대상 선택](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[시선 추적: 대상 선택](features/input/eye-tracking/eye-tracking-target-selection.md)**<br>
        시선, 음성 및 손 입력을 결합하여 장면 전체의 홀로그램을 빠르고 간편하게 선택
    :::column-end:::
    :::column:::
        [![시선 추적: 탐색](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[시선 추적: 탐색](features/input/eye-tracking/eye-tracking-navigation.md)**<br>
        표시되는 내용에 따라 텍스트를 자동으로 스크롤하거나 포커스가 있는 콘텐츠를 확대하는 방법 알아보기
    :::column-end:::
    :::column:::
        [![시선 추적: 열 지도](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[시선 추적: 열 지도](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**<br>
        사용자가 앱에서 본 내용을 로깅, 로드 및 시각화하는 예제
    :::column-end:::
:::row-end:::

## <a name="tools"></a>도구

|  [![최적화 창](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [최적화 창](features/tools/optimize-window.md) | [![종속성 창](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [종속성 창](features/tools/dependency-window.md) | [![빌드 창](features/images/MRTK_Icon_BuildWindow.png)](features/tools/build-window.md)[빌드 창](features/tools/build-window.md) | [![입력 기록](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [입력 기록](features/input-simulation/input-animation-recording.md) |
|:--- | :--- | :--- | :--- |
| 성능 최적화를 위해 Mixed Reality 프로젝트의 구성 자동화 | 자산 간 종속성 분석 및 사용되지 않는 자산 식별 |  Mixed Reality 애플리케이션을 위한 엔드투엔드 빌드 프로세스 구성 및 실행 | 편집기에서 머리 이동 및 손 추적 데이터 기록 및 재생 |

## <a name="example-scenes"></a>예제 장면

MRTK는 MRTK의 기능을 사용하는 방법을 보여주는 예제 장면을 제공합니다. 자산/MRTK/Examples/Demos 폴더에서 예제 장면을 찾을 수 있습니다. 예제 장면을 획득하고 실행하는 방법을 알아보려면 [예제 장면](running-example-scenes.md) 페이지를 읽어보세요. [손 상호 작용 예제 장면](features/example-scenes/hand-interaction-examples.md)은 상호 작용 및 UI를 위한 MRTK의 구성 요소를 경험할 수 있는 좋은 장소입니다.

[![예제 장면 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="mrtk-examples-hub"></a>MRTK 예제 허브

MRTK 예제 허브를 사용하면 각 장면을 빌드하고 배포하지 않고도 MRTK에서 다양한 예제 장면을 시도할 수 있습니다.
[MR Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)에서 "Mixed Reality Toolkit 예제" 패키지를 선택하여 HoloLens(x86), HoloLens 2(ARM) 및 Windows Mixed Reality 몰입형 헤드셋(x64)용으로 미리 작성된 앱 패키지를 다운로드할 수 있습니다. [Windows 장치 포털을 사용하여 HoloLens(1세대)에 앱을 설치](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)해야 합니다. HoloLens 2에서 [Microsoft Store 앱을 통해 MRTK 예제 허브](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4)를 다운로드하고 설치할 수 있습니다.

MRTK의 장면 시스템과 장면 전환 서비스를 사용하여 다중 장면 허브를 만드는 방법에 대한 자세한 내용은 [예제 허브 추가 정보 페이지](features/example-scenes/example-hub.md)를 참조하세요.

[![예제 장면 허브](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="sample-apps-made-with-mrtk"></a>MRTK를 사용하여 만든 샘플 앱

| [![원소의 주기율표](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![갤럭시 익스플로러](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)| [![Surfaces 샘플 앱](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)|
|:--- | :--- | :--- |
| [원소의 주기율표](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)는 MRTK의 입력 시스템 및 구성 요소를 사용하여 HoloLens 및 몰입형 헤드셋을 위한 앱 환경을 만드는 방법을 보여주는 오픈 소스 샘플 앱입니다. 포팅 사례 읽기: [MRTK v2를 사용하는 HoloLens 2에 원소의 주기율표 앱 가져오기](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158) |[갤럭시 익스플로러](https://github.com/Microsoft/GalaxyExplorer)는 HoloLens '아이디어 공유' 캠페인의 일환으로 2016년 3월에 처음 개발된 오픈 소스 샘플 앱입니다. 갤럭시 익스플로러는 MRTK v2를 사용하는 HoloLens 2를 위한 새 기능으로 업데이트되었습니다. 사례 읽기: [HoloLens 2용 갤럭시 익스플로러 제작](/windows/mixed-reality/galaxy-explorer-update) |[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)는 HoloLens 2용 오픈 소스 샘플 앱으로, 시각적 개체, 오디오, 완전히 연결된 손 추적으로 촉감을 만드는 방법을 살펴봅니다. 자세한 디자인 및 개발 사례는 Microsoft 혼합 현실 개발자의 날 세션 [Surfaces 앱을 통한 학습](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)을 확인하세요. |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>2020 혼합 현실 개발자의 날의 세션 동영상

| [![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| 간단한 MRTK 앱을 만드는 방법을 처음부터 끝까지 설명하는 자습서입니다. 상호 작용 개념 및 MRTK의 다중 플랫폼 기능에 대해 알아보세요. | 멋진 혼합 현실 환경을 빌드하는 데 도움이 되는 MRTK의 UX 구성 요소에 대해 자세히 알아보세요. | MRTK 및 외부의 성능 도구에 대한 소개와 MRTK 표준 셰이더에 대한 개요입니다. |

더 많은 세션 동영상을 살펴보려면 [혼합 현실 개발자의 날](/windows/mixed-reality/mr-dev-days-sessions)을 참조하세요.

## <a name="engage-with-the-community"></a>커뮤니티에 참여

* [Slack](https://holodevelopers.slack.com/)에서 MRTK에 대한 대화에 참여하세요. [자동 초대 발신자](https://holodevelopersslack.azurewebsites.net/)를 통해 Slack 커뮤니티에 가입할 수 있습니다.

* **MRTK** 태그를 사용하여 [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk)에서 MRTK를 사용하는 방법에 관해 질문하세요.

* MRTK 코드에서 문제가 발생한 경우 [알려진 문제](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)를 검색하거나 [새 문제](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)를 제기합니다.

* MRTK에 기여하는 방법에 대한 질문이 있는 경우 Slack의 [혼합 현실 도구 키트](https://holodevelopers.slack.com/messages/C2H4HT858) 채널로 이동하세요.

이 프로젝트는 [Microsoft 오픈 소스 준수 사항](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다.
자세한 내용은 [준수 사항 FAQ](https://opensource.microsoft.com/codeofconduct/faq/)를 참조하고, 추가 질문이나 의견이 있는 경우에는 [opencode@microsoft.com](mailto:opencode@microsoft.com)으로 문의하세요.

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>혼합 현실 개발자 센터의 유용한 리소스

| ![검색](features/images/mrdevcenter/icon-discover.png) [검색](/windows/mixed-reality/)| ![디자인](features/images/mrdevcenter/icon-design.png) [디자인](/windows/mixed-reality/design)| ![개발](features/images/mrdevcenter/icon-develop.png) [개발](/windows/mixed-reality/development)| ![배포)](features/images/mrdevcenter/icon-distribute.png) [배포](/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| HoloLens 및 몰입형 헤드셋(VR)을 위한 혼합 현실 환경을 빌드하는 방법을 알아보세요.          | 디자인 가이드를 가져옵니다. 사용자 인터페이스를 구축합니다. 상호 작용 및 입력을 알아봅니다.     | 개발 가이드를 가져옵니다. 기술을 알아봅니다. 과학을 이해합니다.       | 다른 사용자에게 앱을 제공할 수 있도록 준비하고 3D 시작 관리자를 만드는 방안을 고려해 보세요. |

## <a name="useful-resources-on-azure"></a>Azure에 대한 유용한 리소스

| ![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)<br> [Spatial Anchors](/azure/spatial-anchors/)| ![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](/azure/cognitive-services/speech-service/)| ![비전 서비스](features/images/mrdevcenter/icon-azurevisionservices.png) [비전 서비스](/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| Spatial Anchors는 시간이 지나도 디바이스에서 위치를 유지하는 개체를 사용하여 Mixed Reality 환경을 만들 수 있는 플랫폼 간 서비스입니다.| 음성을 텍스트로 변환, 화자 인식, 음성 번역 등의 Azure 기반 음성 기능을 검색하고 애플리케이션에 통합하세요.| 컴퓨터 비전, 얼굴 감지, 감정 인식, 비디오 인덱서 등의 비전 서비스를 사용하여 이미지 또는 비디오 콘텐츠를 식별하고 분석하세요. |

## <a name="how-to-contribute"></a>참가 방법

[기여](contributing/contributing.md)에서 MRTK에 기여할 수 있는 방법을 알아보세요.

## <a name="getting-help"></a>도움말 보기

MRTK로 인한 문제가 발생했거나 작업을 수행하는 방법에 대한 질문이 있는 경우 다음과 같은 몇 가지 리소스를 활용할 수 있습니다.

* 버그 보고서의 경우 GitHub 리포지토리에서 [문제를 제기](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose)하세요.
* 질문이 있는 경우 [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) 또는 Slack의 [혼합 현실 도구 키트 채널](https://holodevelopers.slack.com/messages/C2H4HT858)에 문의하세요. [자동 초대 발신자](https://holodevelopersslack.azurewebsites.net/)를 통해 Slack 커뮤니티에 가입할 수 있습니다.