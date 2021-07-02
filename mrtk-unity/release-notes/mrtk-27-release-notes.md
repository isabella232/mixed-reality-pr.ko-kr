---
title: MRTK 2.7 릴리스 정보
description: MRTK 버전 2.7에 대한 릴리스 정보
author: RogPodge
ms.author: roliu
ms.date: 06/16/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, XRSDK, Legacy XR, Leap Motion, Ultraleap, OpenXR
ms.localizationpriority: high
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 8f6c68c067df735761dd9c162c71fd85f1f3e132
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906979"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Microsoft Mixed Reality Toolkit 2.7 릴리스 정보

## <a name="whats-new-in-272"></a>2\.7.2의 새로운 기능

### <a name="fixed-a-upm-package-dependency-issue"></a>UPM 패키지 종속성 문제 수정

종속성이 올바르게 설정되지 않은 MRTK 2.7.1 UPM 패키지에 문제가 있습니다. 이 문제로 인해 Mixed Reality Feature Tool이 MRTK 2.7.1 패키지를 제대로 가져오지 못했습니다. 이 문제는 이제 2.7.2에서 해결되었습니다. 이 버전에서는 2.7.1에 비해 코드 변경이 없습니다.


## <a name="whats-new-in-271"></a>2\.7.1의 새로운 기능

### <a name="show-version"></a>버전 표시

이제 `Mixed Reality` > `Toolkit` 메뉴에는 프로젝트에서 사용 중인 MRTK 버전을 확인하기 위해 Mixed Reality Toolkit Foundation 패키지를 검사하는 `Show version...` 항목이 포함됩니다.

![버전 메뉴 표시](images/ShowVersionMenu.png)

![MRTK 버전 대화 상자](images/VersionDialog.png)

> [!NOTE]
> MRTK가 [GitHub 리포지토리](https://aka.ms/mrtk)에서 복제된 경우 버전 정보가 설정되지 않습니다.
>
> ![버전을 확인할 수 없음](images/CannotDetermineVersion.png)

### <a name="authors-list"></a>작성자 목록

MRTK 2.7.1부터 작성자 목록 파일이 Mixed Reality Toolkit Foundation 패키지에 포함됩니다.

### <a name="integrated-openxr-project-setup-into-the-configurator-setup-flow"></a>OpenXR 프로젝트 설정을 Configurator 설정 흐름에 통합

MRTK 2.7.1부터는 Mixed Reality OpenXR 플러그 인 사용자에게 MRTK로 플러그 인을 설정하는 방법에 대한 지침이 제공됩니다. HoloLens 2를 대상으로 하는 사용자가 권장 설정을 자동으로 적용할 수 있는 옵션이 있습니다.

![OpenXR 설치 지침이 포함된 Configurator 창](images/configuratorMROpenXR.png)

### <a name="notable-bugfixes-and-changes"></a>주목할 만한 버그 수정 및 변경 내용

- XR SDK 파이프라인에서 Unity Joystick Manager가 지원됨으로 표시 [#9954](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9954), [#9994](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9994)
- null 오류를 방지하기 위해 상호 작용 가능한 검사기 코드에 검사를 추가 [#9943](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9943)
- 펄스 셰이더 예제 장면에 OpenXR 메시 공급자 추가 [#9902 ](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9902)
- 손 물리학 프로필을 예제 장면으로 복원 [#9915](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9915)
- HandConstraint* 스크립트에 대한 일부 정리 [#9935](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9935)
- 프로필 만들기 및 복제에 영향을 주는 일부 버그 수정 [#9982](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9982)


## <a name="whats-new-in-270"></a>2\.7.0의 새로운 기능

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>OpenXR이 이제 MRTK에서 공식적으로 지원됩니다.

새로운 OpenXR 플러그 인이 점점 더 발전하면서 MRTK가 이제 공식적으로 OpenXR을 지원합니다. 이전 릴리스와 비교하여 OpenXR을 사용하여 프로젝트에 다음과 같은 기능을 추가했습니다.

- [시스템 제공 모션 컨트롤러 모델 지원](#support-for-the-system-provided-motion-controller-model-on-openxr)
- WinMR 제스처(선택, 유지, 조작 및 탐색) 지원 [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)
- [컨트롤러 햅틱 지원](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [HoloLens 2에서 관절형 손 메시 지원](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- HoloLens 2에서 공간 매핑 지원 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567), [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- HoloLens 2에서 장면 이해 지원 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

OpenXR을 통해 HoloLens 2 또는 Windows Mixed Reality 헤드셋을 대상으로 하는 경우 [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)을 통해 **Mixed Reality OpenXR 플러그 인 버전 0.9.5 이상** 을 설치/업데이트해야 합니다. 그렇지 않으면 위의 개선 사항 중 일부가 누락될 수 있습니다.

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>Legacy XR 및 XR SDK 데이터 공급자는 이제 동일한 프로필 내에서 사용할 수 있습니다.

데이터 공급자는 이제 적절한 파이프라인을 선택한 경우에만 로드되므로 Legacy XR 및 XR SDK 데이터 공급자가 동일한 프로필 내에서 공존할 수 있습니다. 이를 수용하기 위해 Legacy XR 및 XR SDK 데이터 공급자는 이제 프로필 보기 내의 여러 탭 아래에 구성되어 사용자가 대상 XR 파이프라인에 대한 올바른 프로필을 가지고 있는지 확인할 수 있습니다.

![이제 Legacy 및 XR SDK 데이터 공급자를 단일 프로필로 통합할 수 있습니다.](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

이를 수용하기 위해 이제 null 데이터 공급자가 더 이상 로드되지 않고 프로필 검사기에 표시되지 않습니다. 사용자는 **편집-> 프로젝트 설정-> Mixed Reality Toolkit** 에서 `Show null data providers in the profile inspector`를 전환하여 누락된 데이터 공급자가 있는 예기치 않은 동작을 디버깅할 수 있습니다.

![Null 데이터 공급자는 이제 기본적으로 숨겨져 있습니다.](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
![프로필 검사기에서 null 데이터 공급자 표시 설정/해제](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>환경 설정 및 관련 Mixed Reality Scene Content 동작 추가

이제 사용자는 [환경 설정](../features/experience-settings/experience-settings.md)을 구성하여 MRTK가 대상 환경에 따라 [Mixed Reality Scene Content](../features/experience-settings/scene-content.md)를 적절하게 표시할 수 있습니다.

사용자의 이전 환경 스케일링 설정이 새 환경 설정 프로필과 일치하지 않으면 검사기에서 수정하라는 메시지가 표시됩니다.

![환경 스케일링 마이그레이션](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>새로 디자인된 Configurator는 이제 설정 프로세스를 통해 사용자를 안내합니다.

새로운 MRTK Configurator는 XR 개발 및 MRTK와 함께 사용하기 위해 프로젝트를 적절하게 구성하기 위한 단계별 지침을 사용자에게 제공합니다. 여기에는 XR 파이프라인 선택, 플랫폼별 플러그 인 가져오기, TextMeshPro 가져오기, 예제(UPM 사용 시) 및 기타 이전에 포함된 프로젝트 권장 설정이 포함됩니다.

![파이프라인 목록을 표시하는 Configurator](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>등급이 지정된 텔레포트 핫스팟

새 [텔레포트 핫스팟 구성 요소](../features/teleport-system/teleport-hotspot.md)는 등급이 지정되었습니다. GameObject에 텔레포트 핫스팟을 추가하여 사용자가 해당 위치로 텔레포트할 때 특정 위치와 방향에 있도록 할 수 있습니다.

![텔레포트 핫스팟 예](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>등급이 지정된 유지

유지 기능과 예는 이제 실험 등급이 지정되었습니다. 볼륨 HoloLens 2 스타일 단추의 새로운 예가 샘플 장면에 포함되어 있습니다.

![유지 영웅](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>Leap Motion Unity Module 버전 4.6.0, 4.7.0, 4.7.1 및 4.8.0에 대한 지원 추가

최신 버전의 [Leap Motion Unity 모듈](https://developer.leapmotion.com/unity)에 대한 지원이 이제 MRTK 2.7.0과 호환됩니다. 자세한 내용은 [Leap Motion에 대한 MRTK 구성 방법](../supported-devices/leap-motion-mrtk.md)을 참조하세요.

새로운 LeapMotionOrientationExample 장면에 기여해 주신 @jackyangzzh에게 감사드립니다!

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>대상 지정 음성 이벤트가 발생하면 더 이상 응시 포인터로 제한되지 않음

이전에는 대상 지정 음성 이벤트는 응시 포인터를 사용하여 포커스가 있는 개체에서만 발생할 수 있었습니다. 이제 개체가 포인터에 의해 포커스가 맞춰지면 음성 이벤트를 받을 수 있습니다.

![원거리 포인터를 사용한 음성 이벤트](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>HTK에서 MRTK로 TextToSpeech 포팅

이제 [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer)를 사용하여 UWP 플랫폼의 텍스트에서 음성을 생성할 수 있도록 MRTK에서 인기 있는 TextToSpeech 스크립트를 사용할 수 있습니다. 또한 기능을 보여주기 위해 샘플 장면을 추가했습니다.

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>OpenXR에서 시스템 제공 모션 컨트롤러 모델 지원

OpenXR에서 시스템 제공 모션 컨트롤러 모델에 대해 편집기 내 및 런타임 시 지원이 추가되었습니다.

![두 모션 컨트롤러 모델이 표시된 편집기 창](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>OpenXR에서 HoloLens 2 관절형 손 메시 지원

![MRTK 예제 장면에서 디바이스 내에서 실행되는 손 메시](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>레거시 WMR, Windows XR 플러그 인 및 OpenXR에서 컨트롤러 햅틱 지원

레거시 WMR, Windows XR 플러그 인 및 OpenXR에서 컨트롤러 햅틱 지원이 추가되었습니다. [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Windows XR 플러그 인에서 시선 추적 지원

Windows XR 플러그 인 최소 버전 2.7.0(Unity 2019), 4.4.2(Unity 2020) 및 5.2.2(Unity 2021)를 사용할 때 시선 응시에 대한 지원이 추가되었습니다. [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>주목할 만한 버그 수정 및 변경 내용

- 손가락 모으기 감지가 더 부드러워졌습니다. 이제 실수로 손가락 모으기 제스처가 드롭되는 현상이 줄어들었습니다. [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- 개체 조작자 구성 요소가 있는 오브젝트는 이제 플래그가 설정될 때 속도를 일관되게 유지합니다. [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- 이제 Back-strafing이 바닥을 확인하여 카메라가 환경에 삽입될 수 있는 상황이나 사용자가 빈 공간 위에 떠 있는 상황을 방지합니다. [#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject는 이제 가상 속성이 되어 스피어 또는 포크 포인터를 확장할 때 더욱 유연해졌습니다. [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- 단추는 이제 사용 가능한 음성 명령을 나타낼 때 적절한 키워드를 표시합니다. [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Oculus 컨트롤러는 이제 자체 독립형 비주얼라이저를 사용하여 MRTK 시각화가 Oculus 통합 패키지의 시각화와 충돌하지 않도록 합니다. [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- 키보드 관련 스크립트가 최신 Unity 버전(2019.4.25+ 및 2020.3.2+)의 동작에 맞게 변경되었습니다. 릴리스 당시에도 HoloLens에 영향을 미치는 자동 완성 버그와 TMP 입력 필드 버그(둘 다 MRTK 외부에 있음)가 있습니다. 자세한 내용은 [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) 및 [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724)를 참조하세요.
- 스크롤 개체 컬렉션의 성능이 향상되었습니다. 또한 컬렉션 내의 GameObject가 중복될 때 재질이 손실되는 문제도 해결되었습니다. [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- 장면 이해 데모 스크립트에서 특정 종류의 관찰된 모든 장면 개체를 검색하도록 `GetSceneObjectsOfType` 기능을 추가했습니다. [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- 명령줄 빌드 도구에서는 `sceneList` 또는 `sceneListFile` 플래그(플래그가 있는 경우)로 지정된 장면만 빌드에 포함됩니다. [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- 빌드 도구에는 `msbuild`(기본 옵션)를 사용하는 대신 `nuget.exe`에 대한 경로를 지정하고 이 경로를 사용하여 패키지 복원을 수행하는 새 옵션이 있습니다. [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- Windows XR 플러그 인을 사용하면 손 관절이 부실해지고 손 메시가 이중으로 발생하는 문제가 해결되었습니다. [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- Windows XR 플러그 인의 자동 원격 기능을 사용하여 입력 및 상호 작용이 누락되는 문제가 해결되었습니다. [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- BuildDeployWindow가 Windows SDK 경로에 대해 잘못된 reg 키를 쿼리하는 문제가 해결되었습니다. [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- MRTK의 glTF 가져오기 도구는 이제 선택 사항입니다. glTF 가져오기 도구가 여러 개 있는 경우 사용자 지정 스크립팅 정의 기호에 `MRTK_GLTF_IMPORTER_OFF`를 추가하여 MRTK를 사용하지 않도록 설정할 수 있습니다. [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- OpenVR의 Knuckles 컨트롤러가 제대로 감지되지 않는 문제가 해결되었습니다. [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- 손 메시를 시각화할 때 프레임당 할당 수를 줄입니다. [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- MRTK 예제 패키지(Unity 패키지 관리자에서)를 실행하는 메뉴 항목을 추가하여 샘플을 더 쉽게 가져올 수 있습니다. [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- Unity 2020.3을 사용할 때 로드 시간 경고 수가 줄어들었습니다.
- 빌드 창 기능 문서 추가: [페이지 방문](../features/tools/build-window.md)

## <a name="known-issues"></a>알려진 문제

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>오디오 데모에 asmdef 파일(UPM 패키지)이 없습니다.

Mixed Reality Feature Tool을 통해 MRTK를 가져올 때 Unity 패키지 관리자 UI를 사용하여 샘플과 데모가 프로젝트에 추가됩니다. 오디오 데모를 가져온 후 `WindowsMicrophoneStreamDemo.unity` 장면이 제대로 작동하지 않습니다. 이는 샘플에 대한 .asmdef 파일이 누락된 결과입니다.

이 [문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908)를 해결하려면 다음 단계를 수행하세요.

- Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...]/MRTK.Examples.asmdef를 "Assets/Samples/Mixed Reality Toolkit Examples" 폴더에 복사합니다.
- 복사한 파일의 이름을 Examples로 바꿉니다.
- Examples 파일을 엽니다.
- 이름 상자에서 내용을 Examples로 대체합니다.
- 적용을 클릭합니다.
- 빌드 및 배포

이 문제는 향후 MRTK 릴리스에서 해결될 예정입니다.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>MRTK 빌드 창이 Unity 2020.3에서 무기한 "자산 가져오기" 대화 상자를 트리거합니다.

Unity 2020.3의 MRTK 빌드 창에는 UWP 빌드를 성공적으로 수행한 후 "자산 가져오기" 대화 상자가 완료되지 않는 [문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723)가 알려져 있습니다. 이 문제는 Unity와 협력하여 조사 중입니다.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Unity 2020의 Text Mesh Pro 캔버스 렌더러 경고

Unity 2020을 사용하는 동안 대부분의 MRTK 예제 장면에 다음 경고가 기록됩니다.

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

캔버스 렌더러 경고가 [TextMeshPro 버전 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3)에 추가되었습니다. 이러한 경고는 MRTK의 예제 장면에 영향을 미치지 않으며 콘솔에서 지울 수 있습니다. 자세한 내용은 [문제 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811)을 참조하세요.