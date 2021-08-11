---
title: MRTK 2.5 릴리스 정보
description: MRTK 버전 2.5에 대 한 릴리스 정보
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk,
ms.openlocfilehash: 7d3e158bc7e4b0125f264aa9abc8f369a6e825562266891b0528066d8b8b9b71
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198130"
---
# <a name="microsoft-mixed-reality-toolkit-25-release-notes"></a>Microsoft Mixed Reality Toolkit 2.5 릴리스 정보

> [!IMPORTANT]
> ARM64를 사용 하 여 Microsoft HoloLens 2 용으로 빌드된 응용 프로그램에 영향을 주는 알려진 컴파일러 문제가 있습니다. 이 문제는 2019 Visual Studio 버전 16.8 이상으로 업데이트 하 여 해결할 수 있습니다. Visual Studio를 업데이트할 수 없는 경우에는 패키지를 가져와 `com.microsoft.mixedreality.toolkit.tools` 해결 방법을 적용 하십시오.

## <a name="whats-new-in-254"></a>2.5.4의 새로운 기능

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a>UPM를 사용할 때 Oculus 통합으로 버그를 수정 합니다.

UPM를 사용 하는 경우 OculusXRSDKDeviceManagerProfile는 [시작 시 항상 prefabs로 설정](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160)되어 있지 않습니다. 이 릴리스는 시작 시 prefabs의 작업 집합을 가리키도록 장치 관리자를 구성 합니다.

### <a name="fixes-an-issue-with-openxr-via-upm"></a>UPM를 통한 OpenXR 문제 해결

OpenXR 공급자가 기본적으로 link.xml에 추가 되지 않아 Unity의 패키지 관리자를 통해 OpenXR 및 mrtk를 사용할 때 새 프로젝트가 장치에서 실행 되지 않는 문제를 해결 합니다. 업그레이드 된 기존 프로젝트는이를 수동으로 추가 해야 합니다.

## <a name="whats-new-in-253"></a>2.5.3의 새로운 기능

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a>2.5.2에 도입 된 Oculus를 사용 하 여 회귀를 수정 합니다.

2.5.2 [에는 Oculus SDK를 통합할 때 빌드 문제가](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083)도입 되었습니다. 이 릴리스는 해당 문제를 되돌립니다.

## <a name="whats-new-in-252"></a>2.5.2의 새로운 기능

### <a name="add-support-for-openxr"></a>OpenXR에 대 한 지원 추가

Unity의 OpenXR 미리 보기 패키지 및 Microsoft의 Mixed Reality OpenXR 패키지에 대 한 초기 지원이 추가 되었습니다. 자세한 내용은 [MRTK/XRSDK 시작 페이지](../configuration/getting-started-with-mrtk-and-xrsdk.md), [Unity의 포럼 게시물](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)또는 [Microsoft 설명서](/windows/mixed-reality/develop/unity/openxr-getting-started) 를 참조 하세요.

> [!IMPORTANT]
> Unity의 OpenXR는 Unity 2020.3 이상 에서만 지원 됩니다.
> 또한 x64, ARM 및 ARM64 빌드를 지원 합니다.

### <a name="boundary-visualization-errors-fixed"></a>경계 시각화 오류 수정 됨

바닥 또는 벽과 같은 경계 시각화는 이제 경계 프로필에 따라 적절 하 게 구성 되 고 런타임에 표시 됩니다.

### <a name="msbuild-for-unity-support"></a>Unity 지원 MSBuild

unity의 [새 패키지 지침](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)에 맞게 2.5.2 릴리스의 MSBuild에 대 한 지원이 제거 되었습니다.

## <a name="whats-new-in-251"></a>2.5.1의 새로운 기능

### <a name="package-dependency-errors-fixed"></a>패키지 종속성 오류가 수정 되었습니다.

이 릴리스는 잘못 된 패키지 간 파일 종속성을 수정 합니다 (예: 표준 자산의 파일은 더 이상 Foundation의 파일을 잘못 참조 함). 버전 2.5.1 텍스트 메시 Pro에 대 한 명시적 종속성도 추가 합니다.

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a>자산/MRTK/셰이더에 복사 되는 표준 자산 패키지 셰이더

UPM를 통해 표준 자산 패키지를 설치 하는 경우 셰이더가 자산/m a s v k/셰이더 폴더로 복사 되어 더 이상 변경할 수 없게 됩니다. 이를 통해 다음에 프로젝트가 로드 될 때 레거시 동작을 되돌리는 URP (유니버설 렌더링 파이프라인)에 대해 업데이트 된 셰이더 문제가 해결 됩니다.

### <a name="fixed-teleport-cursor-sticking-to-hands"></a>손에 고정 된 텔레포트 커서

이 릴리스에서는 텔레포트 대상 커서가 시각적 개체에 집중 될 수 있는 [문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) 를 해결 합니다.

## <a name="whats-new-in-250"></a>2.5.0의 새로운 기능

### <a name="unity-package-manager-upm-support"></a>UPM (Unity 패키지 관리자) 지원

이제 Unity 패키지 관리자를 사용 하 여 혼합 현실 Toolkit를 관리할 수 있습니다.

![MRTK Foundation UPM 패키지](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> MRTK UPM 패키지를 가져오는 데 필요한 몇 가지 수동 단계가 있습니다. 자세한 내용은 [혼합 현실 Toolkit 및 Unity 패키지 관리자](../configuration/usingupm.md) 를 검토 하세요.

### <a name="oculus-quest-xr-sdk-support"></a>Oculus Quest XR SDK 지원

이제 MRTK는 기본 XR SDK 파이프라인을 사용 하 여 Oculus Quest 헤드셋 및 컨트롤러 실행을 지원 합니다. [Eric Provencher의](https://twitter.com/prvncher) MRTK-Quest에서 작업 하는 경우에도 [Oculus Integration Unity 패키지](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 에서 수동 추적을 지원 합니다.

새 파이프라인을 사용 하 여 Oculus 퀘스트에서 장치를 배포 하는 방법에 대 한 지침은 [Oculus Quest 설치 가이드](../supported-devices/oculus-quest-mrtk.md) 를 참조 하세요.

### <a name="scrolling-object-collection"></a>스크롤 개체 컬렉션

MRTK UX 구성 요소는 실험적 기능에서 업그레이드 되었으며 colliders가 연결 되지 않은 개체에 대 한 지원이 추가 된 다양 한 크기의 3D 콘텐츠를 레이아웃 더 자유롭게 제공 합니다. 또한 콘텐츠 마스킹을 사용 하지 않도록 설정 하는 새로운 옵션이 추가 되어 프로토타입을 더 쉽게 만들 수 있습니다.

자세한 내용은 [스크롤 개체 컬렉션](../features/ux-building-blocks/scrolling-object-collection.md) 을 참조 하세요.

![스크롤 개체 컬렉션](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a>텔레포트 포인터 애니메이션, 처리 및 소리 개선

이제 텔레포트 포인터가 애니메이션 및 오디오 피드백을 개선 했습니다. 또한 주변 표면에서 멀리 떨어진 표면으로 전환할 때 더 부드럽게 처리 되도록 텔레포트 포인터의 처리를 개선 했습니다.

### <a name="input-simulation-cheat-sheet"></a>입력 시뮬레이션 참고 자료 시트

이제 HandInteractionExamples 장면에는 입력 시뮬레이션에 대 한 도움말 페이지를 표시 하는 구성 가능한 바로 가기가 있습니다.

![입력 시뮬레이션 참고 자료 시트](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a>입력 시뮬레이션 눈동자 마우스로 응시

사용자는 이제 시각 추적을 시뮬레이션 하기 위해 마우스를 사용할 수 있습니다. `Eye Simulation Mode`입력 시뮬레이션 프로필의 필드를 확인 하 고 마우스로 설정 합니다. 이전 필드를 대체 `Simulate Eye Position` 합니다.

![아이 응시 마우스](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a>편집기 재생 모드의 입력 시뮬레이션 동작 컨트롤러

이제 사용자는 편집자 재생 모드와 마찬가지로 동작 컨트롤러를 시뮬레이션할 수 있습니다. 트리거, 잡기 및 메뉴 단추가 현재 지원 됩니다.

### <a name="conical-grab-pointer"></a>원추형 잡기 포인터

이제 구가 아닌 잡기에서 원뿔을 사용 하 여 근처 개체를 쿼리하도록 잡기 포인터를 구성할 수 있습니다. 이는 원뿔을 사용 하 여 인접 개체를 쿼리 하는 기본 HoloLens 2 인터페이스의 동작과 매우 유사 합니다. 또한 새를 사용 하도록 DefaultHoloLens2InputSystemProfile 조정 되었습니다 `ConicalGrabPointer` .

![원추형 잡기 포인터](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a>TestUtilities 패키지

이제 패키지 (MixedReality. Toolkit가 있습니다. 2.5.0. unitypackage)-MRTK에서 종단 간 테스트를 만드는 데 사용 하는 PlayMode 및 Testutilities 테스트 인프라를 포함 합니다. 이 인프라는 MRTK 팀 자체에 매우 유용 하 게 사용 되었으며 소비자가이를 사용 하 여 자체 프로젝트에 테스트 검사를 추가 하는 것이 좋습니다.

다음 코드에서는 테스트 손을 만들고, 특정 위치에 표시 하 고, 이동 하 고, 옆으로 여는 방법을 보여 줍니다.

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

이러한 TestUtilities를 사용 하 여 테스트를 작성 하는 방법에 대 한 지침은 [테스트 작성](../contributing/unit-tests.md#writing-tests)에 대 한이 섹션을 참조 하세요.

이 인프라를 사용 하는 기존 테스트에 대 한 예제는 MRTK의 [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)를 참조 하세요.

### <a name="support-for-the-leap-motion-451-unity-modules"></a>도약 동작 4.5.1 Unity 모듈 지원

도약 동작 Unity 모듈 버전 4.5.1에 대 한 지원이 추가 되었으며 4.4.0 자산에 대 한 지원이 제거 되었습니다. 현재 지원 되는 Leap 동작 Unity 모듈의 버전은 4.5.0 및 4.5.1입니다.

초기 Leap 동작 통합에 대 한 추가 단계도 있습니다. 자세한 내용은 [MRTK에서 Leap 동작 손 추적을 구성 하는 방법](../supported-devices/leap-motion-mrtk.md) 을 참조 하세요.

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a>공간 인식 메시 관찰자는 자료의 사용자 지정을 더 잘 처리 합니다.

이 릴리스에서 `Windows Mixed Reality Spatial Mesh Observer` 및 `Generic XR SDK Spatial Mesh Observer` 구성 요소는 시각적 재질 처리를 개선 했습니다. 이전에는 관찰자에 의해 메쉬가 업데이트 된 후에도 재질은 유지 됩니다 .이는 이전에 프로필에 구성 된 대로 기본 VisibleMaterial 다시 설정 되었습니다.

이렇게 하면 개발자가 메시 자료를 변경 하 고 변경 내용을 예기치 않게 덮어쓸 수 있습니다.

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a>MixedRealityToolkit 폴더에 생성 된 Link.xml

Unity 패키지 관리자 MRTK가 도입 되면서 이제 MRTK가 없는 `link.xml` 경우 폴더에 파일을 씁니다 `Assets/MixedRealityToolkit.Generated` . 이 파일을 추가 하는 것이 좋습니다 .이 파일을 소스 제어에 추가 하는 것이 좋습니다 `link.xml.meta` . Link.xml은 Unity 링커의 [관리 코드](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) 제거 기능에 영향을 주는 데 사용 됩니다.

MRTK link.xml 파일에 대 한 자세한 내용은 [mrtk 및 관리 코드](../updates-deployment/mrtk-and-managed-code-stripping.md) 제거 문서에서 찾을 수 있습니다.

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a>Unity 2019.3 +: MRTK 구성 대화 상자에서 더 이상 레거시 XR 지원 사용을 시도 하지 않습니다.

Unity의 XR 플랫폼을 사용 하는 경우 충돌을 방지 하기 위해 레거시 XR 지원을 사용 하도록 설정 하는 옵션이 MRTK 구성 대화 상자에서 제거 되었습니다. XR를 사용 하는 경우에는 Unity 2019에서 **편집**  >  **Project 설정**  >
 **Player**  >  **XR 설정**  >  **가상 현실 지원** 을 사용 하 여 레거시 지원을 사용 하도록 설정할 수 있습니다.

### <a name="reduction-in-initializeonload-overhead"></a>InitializeOnLoad 오버 헤드 감소

여기서는 작업을 수행 하 여 InitializeOnLoad 처리기에서 실행 되는 작업의 양을 줄이고 내부 루프 개발 속도를 향상 시킬 수 있습니다. InitializeOnLoad 처리기는 스크립트가 컴파일될 때마다 재생 모드를 시작 하기 전에 실행 되 고 편집기 시작 에서도 실행 됩니다. 이러한 처리기는 이제 훨씬 더 낮은 사례에서 실행 되므로 일반적인 Unity 응답성이 향상 됩니다.

일부 경우에는 다음을 수행 해야 하는 단점이 있습니다.

- 추가 통합 단계에 대 한 [도약 동작 손 추적 구성](../supported-devices/leap-motion-mrtk.md) 을 참조 하세요.
- ARFoundation을 사용 하는 사용자에 게는 시작 단계에 추가 수동 단계가 있습니다.
  새 단계는 [Arfoundation](../supported-devices/using-ar-foundation.md#install-required-packages) 을 참조 하세요.
- HoloLens 2에서 [레거시 XR 파이프라인](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) 을 사용 하 여 Holographic Remoting을 사용 하는 사용자에 게는 이제 [수동 단계](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) 를 수행 해야 합니다.

### <a name="bounds-control-graduated"></a>범위 컨트롤 그라데이션

![경계 컨트롤](../features/images/bounds-control/MRTK_BoundsControl_Main.png)

[범위 제어](../features/ux-building-blocks/bounds-control.md) 는 실험적에서 비롯 되며 다양 한 새로운 기능 및 많은 버그 수정이 제공 됩니다.
이 업데이트의 주요 목록은 다음과 같습니다.

- 속성이 구성으로 분할 되어 범위 제어를 쉽게 설정할 수 있습니다.
- 스크립트 가능한 개체를 통해 구성을 공유할 수 있습니다.
- 모든 속성/스크립트 가능한 속성은 런타임 구성 가능
- 범위 제어 rig는 속성 변경에 더 이상 다시 만들어지지 않습니다.
- 번역 핸들 지원
- 제약 조건 관리자를 통한 전체 제약 조건 지원
- 탄력적 시스템 통합 (실험적)

이전 경계 상자는 이제 사용 되지 않으며, 경계 상자를 사용 하는 기존 게임 개체는 마이그레이션 도구나 [경계 상자 검사기](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control)를 [사용 하 여 업그레이드할](../features/tools/migration-window.md) 수 있습니다.

### <a name="constraint-manager-component"></a>제약 조건 관리자 구성 요소

이제 제약 조건을 새 [제약 조건 관리자 구성 요소](../features/ux-building-blocks/constraint-manager.md)를 통해 경계 컨트롤과 개체 조작자 모두에서 사용할 수 있습니다. 두 구성 요소는 기본적으로 제약 조건 관리자를 만들고 연결 된 제약 조건을 자동으로 처리 합니다.

또한 자동 동작 제약 조건 관리자는 사용자가 처리 해야 하는 제약 조건을 결정할 수 있는 수동 모드와 함께 제공 됩니다.
이러한 이유로 속성 검사자에서 제약 조건을 표시 하는 방법이 약간 변경 되었습니다.

<img src="../features/images/constraint-manager/ManualSelection.png" width="600" alt="Inspector view showing manual constraint manager selection">

구성 요소에 적용 되는 제약 조건은 이제 제약 조건 관리자 구성 요소에 목록으로 표시 되는 반면 제약 조건 관리자 ( [범위 제어](../features/ux-building-blocks/bounds-control.md#constraint-system) 또는 [개체 조작자](../features/ux-building-blocks/object-manipulator.md#constraint-manager))를 사용 하는 구성 요소는 이제 선택한 제약 조건 관리자 및 모드 (자동 또는 수동)를 표시 합니다.
자세한 내용은 문서에서 [제약 조건 관리자](../features/ux-building-blocks/constraint-manager.md) 섹션을 참조 하세요.

### <a name="hololens-2-button-material-update"></a>HoloLens 2 단추 재질 업데이트

mrc에서 검정 색을 제거 하는 HoloLens 2 단추의 전면 케이지 자료를 업데이트 했습니다.

![HoloLens 2 단추 재질 업데이트](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a>설명 패널 업데이트, 이동 가능한 예제 장면

설명 패널을 업데이트 했습니다. (SceneDescriptionPanelRev prefab) 새 디자인은 사용자가 전체 장면을 조정/이동 하는 데 사용할 수 있는 grabbable 위쪽 막대를 제공 합니다.

![설명 패널 업데이트](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a>공간 메시 시각화-공기를 탭 하 여 펄스

HoloLens 2의 셸 동작과 일치 하도록 공간 메시의 업데이트 된 펄스 셰이더 예제입니다.

![공기를 통한 펄스-탭](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system-experimental"></a>탄력적 시스템 (실험적)

![탄력적 System2](../features/images/elastics/Elastics_Main.gif)

MRTK는 이제 다양 한 확장 가능 하 고 유연한 서브 클래스가 포함 된 [탄력적 시뮬레이션 시스템과](../features/experimental/elastic-system.md) 함께 제공 됩니다. 4 차원 4 차원 스프링, 3 차원 볼륨 스프링 및 간단한 선형 스프링 시스템에 대 한 바인딩을 제공 합니다.

현재 [탄력적 manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) 를 지 원하는 다음 MRTK 구성 요소는 탄력적 기능을 활용할 수 있습니다.

- [경계 컨트롤](../features/ux-building-blocks/bounds-control.md#elastics-experimental)
- [개체 조작자](../features/ux-building-blocks/object-manipulator.md#elastics-experimental)

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Expanding an elastic menu">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Grabbing an elastic coffee cup">

### <a name="joystick-experimental"></a>조이스틱 (실험적)

많은 대상 개체를 제어할 수 있는 조이스틱 인터페이스의 예입니다.

![조이스틱이](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a>색 선택 (실험적)

런타임에 개체의 재질 색을 쉽게 변경할 수 있게 해 주는 실험적 컨트롤입니다.

![색 선택 컨트롤의 세 가지 다른 방법](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)

![색 선택 컨트롤의 네 가지 다른 방법](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

## <a name="breaking-changes"></a>주요 변경 내용

### <a name="assembly-definition-files-changes"></a>어셈블리 정의 파일 변경

일부 asmdef 파일이 변경 되 고 이제 Unity 2018.4.13 f1 이상만 지원 됩니다. 이전 버전의 Unity에서 MRTK 2.5로 업데이트 하는 경우 컴파일 오류가 표시 됩니다. 이 문제는 `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` 프로젝트 창에서로 이동 하 고 검사기에서 누락 된 참조를 제거 하 여 해결할 수 있습니다. 및를 사용 하 여 이러한 단계를 반복 `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` 합니다. 참고 Unity 2019로 업그레이드할 때 이러한 세 asmdef 파일을 원래 (수정 되지 않은)로 바꿔서 변경 내용을 되돌려야 합니다.

### <a name="imixedrealitypointermediator"></a>IMixedRealityPointerMediator

이 인터페이스는 새 함수를 포함 하도록 업데이트 되었습니다.

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

DefaultPointerMediator를 서브 클래스 하지 않는 사용자 지정 포인터 mediator 있는 경우이 새 함수를 구현 해야 합니다. 이 추가 된 이유에 대 한 배경 정보는 [이 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) 를 참조 하세요. 이는 IPointerPreferences 설정을 사용 하는 생성자가 있는지 여부에 따라 암시적으로 수행 되는 것이 아니라 포인터 기본 설정이 mediator에 명시적으로 전달 되도록 하기 위해 추가 되었습니다.

### <a name="rest--device-portal-api"></a>Rest/장치 포털 API

`UseSSL`정적 속성이에서로 이동 했습니다 `Rest` `DevicePortal` .

이전에 수행한 경우

```csharp
Rest.UseSSL = true
```

지금이 작업 수행 ...

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a>Link.xml

이전에 응용 프로그램에서 mrtk의 NuGet 배포를 사용 하는 경우 `link.xml` 파일이 Foundation 패키지에서 제거 되었습니다. 코드 보존 규칙을 복원 하려면 Unity에서 프로젝트를 한 번 열면 `link.xml` 에서 기본 파일이 생성 됩니다 `Assets/MixedRealityToolkit.Generated` . 이 파일 (및 `link.xml.meta` )을 소스 제어에 추가 하는 것이 좋습니다.

### <a name="transform-constraint-changes"></a>변환 제약 조건 변경

TargetTransform 속성이 제약 조건 시스템에서 사용 되지 않으므로 사용 되지 않는 것으로 표시 되었습니다. 제약 조건 논리는 Initialize 및 Apply 메서드에 전달 된 변환을 기반으로 합니다. 이 속성을 사용 하는 파생 사용자 제약 조건은 동일한 동작을 얻기 위해 제약 조건 구성 요소의 변환을 저장 하 여 해당 구현에서 TargetTransform을 캐시할 수 있습니다.

저장 된 초기 세계 포즈 `worldPoseOnManipulationStart` 데이터 형식이 조작 된 개체의 로컬 크기 조정 값을 포함 하는 MixedRealityPose에서 MixedRealityTransform로 변경 되었습니다. 이 변경으로 초기 크기 조정 값을 더 이상 별도로 캐시 하지 않아도 됩니다.

### <a name="new-property-in-imixedrealitydictationsystem"></a>IMixedRealityDictationSystem의 새 속성

새 속성이 `AudioClip` IMixedRealityDictationSystem 인터페이스에 추가 되었습니다. `AudioClip`속성을 사용 하면 현재 받아쓰기 세션과 연결 된 오디오 클립에 액세스할 수 있습니다. 사용자는 인터페이스를 구현 하는 스크립트에서 속성을 구현 해야 합니다.

### <a name="service-facades-turn-down"></a>서비스 외관 해제

2.5에서 서비스 외관 중단 됩니다. 이 기능은 원래 MRTK의 서비스를 나타내는 가짜-장면 Gameobject를 만들어 MRTK 프로필을 더 쉽게 구성할 수 있도록 추가 되었습니다. 장기 실행에서는 가짜 게임 개체를 만들어 동기화 된 상태로 유지 하는 것을 방지 하려고 합니다 (데이터 동기화 및 "진위 원본" 문제는 크기를 조정 하 고 어렵습니다 어렵습니다.).

2.5에서 프로젝트 업그레이드를 원활 하 게 수행 하기 위해 서비스 외관 처리기가 유지 됩니다. 프로젝트에 존재 하는 모든 외관은 2.5에서 열린 장면이 자동으로 고정 되도록 서비스 외관 처리기에 의해 삭제 됩니다.

서비스 외관 기능과 관련 된 나머지 코드는 이후 릴리스에서 제거 될 예정입니다.

### <a name="addition-of-motion-controller-to-input-simulation-service"></a>입력 시뮬레이션 서비스에 동작 컨트롤러 추가

이제 동작 컨트롤러 시뮬레이션이 기존 손 시뮬레이션을 따라 편집기 재생 모드로 제공 됩니다. 이러한 변경을 가능 하 게 하기 위해 이제 많은 최신 함수/필드/속성이 더 이상 사용 되지 않는 것으로 표시 되 `InputSimulationService.cs` 고 `MixedRealityInputSimulationProfile.cs` 가장 중요 한 변경 내용을 가져옵니다. 관련 코드의 논리 및 동작은 주로 동일 하 게 유지 되며 대부분의 오래 된 함수 등은 참조를 "직접"으로 대체 하는 것과 관련이 있습니다. 예를 들어에서로의 일반적인 용어 "controller"입니다. `DefaultHandSimulationMode` `DefaultControllerSimulationMode` 새 이름을 가져오는 것 외에도 특정 새 함수의 반환 형식이 이름/동작 변경 내용에 맞게 업데이트 됩니다. 예를 들어 `GetControllerDevice` 원래는 `GetHandDevice` 대신를 반환 `BaseController` 합니다 `SimulatedHand` .

`IInputSimulationService` 에는 이제 새 속성과가 있습니다 `MotionControllerDataLeft` `MotionControllerDataRight` . `MixedRealityInputSimulationProfile` 에는 이제 특정 동작 컨트롤러 단추의 키보드 매핑에 대 한 새 필드가 포함 됩니다.

## <a name="known-issues"></a>알려진 문제

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache는 종료 시 새 카메라를 만들 수 있습니다.

일부 상황에서 (예: Unity 편집기에서 LeapMotion 공급자를 사용 하는 경우) CameraCache가 종료 시 MainCamera를 다시 만들 수 있습니다. 자세한 내용은 [이 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 를 참조 하세요.

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>Unity를 통해 예제를 가져오는 경우 system.io.filenotfoundexception 패키지 관리자

프로젝트 경로의 길이에 따라 unity 패키지 관리자를 통해 예제를 가져오는 경우 unity 콘솔에서 system.io.filenotfoundexception 메시지가 생성 될 수 있습니다. 이 오류의 원인은 MAX_PATH (256 자) 보다 긴 "누락 된" 파일의 경로입니다. 해결 하려면 프로젝트 경로의 길이를 줄이십시오.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Spatializer가 지정 되지 않았습니다. 응용 프로그램에서 공간 소리를 지원 하지 않습니다.

오디오 spatializer 구성 되지 않은 경우 "No spatializer가 지정 되었습니다." 경고가 표시 됩니다. XR 패키지를 설치 하지 않은 경우에 이러한 문제가 발생할 수 있습니다. Unity는 이러한 패키지에 spatializers를 포함 합니다.

이 문제를 해결 하려면 다음을 확인 하세요.

- **창**  >  하나 이상의 XR 패키지가 설치 **패키지 관리자**
- **혼합 현실 Toolkit**  >  **유틸리티**  >  **Unity Project 구성** 하 고 **오디오 Spatializer** 선택

  ![오디오 Spatializer 선택](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: 개체 참조가 개체의 인스턴스로 설정 되지 않았습니다 (SceneTransitionService.Initialize).

경우에 따라를 열면 `EyeTrackingDemo-00-RootScene` SceneTransitionService 클래스의 Initialize 메서드에서 NullReferenceException이 발생할 수 있습니다.
이 오류는 장면 전환 서비스의 구성 프로필이 설정 되어 있지 않기 때문에 발생 합니다. 해결 하려면 다음 단계를 사용 하세요.

- `MixedRealityToolkit`계층의 개체로 이동 합니다.
- 검사기 창에서 다음을 선택 합니다. `Extensions`
- 확장 되지 않은 경우 확장 합니다. `Scene Transition Service`
- 의 값을 `Configuration Profile` **MRTKExamplesHubSceneTransitionServiceProfile** 로 설정 합니다.

![장면 전환 수정](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus Quest

현재 [독립 실행형 플랫폼을 대상으로 하는 경우에서 Oculus XR 플러그 인](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)을 사용 하는 알려진 문제가 있습니다. 업데이트에 대 한 Oculus 버그 추적기/포럼/릴리스 정보를 확인 하세요.

이 세 가지 오류 집합을 사용 하 여 버그를 표시 합니다.

![Oculus XR 플러그 인 오류](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI 및 TextMeshPro

최신 버전의 TextMeshPro (1.5.0 + 또는 2.1.1 +)에 대 한 알려진 문제는 드롭다운의 기본 글꼴 크기와 굵은 글꼴 문자 간격이 변경 된 것입니다.

![TMP 이미지](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

이 작업은 이전 버전의 TextMeshPro으로 다운 그레이드 하 여 해결할 수 있습니다. 자세한 내용은 [문제 #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) 를 참조 하세요.
