---
title: MRTK 2.7 릴리스 정보
description: MRTK 버전 2.7의 릴리스 정보
author: RogPodge
ms.author: roliu
ms.date: 05/27/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, XRSDK, 레거시 XR, Leap 동작, Ultraleap
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 92c8705c70a2a6c1e25f1ed6b1f87eac1e5726e0
ms.sourcegitcommit: 11d5d7c3fdd59c1ebcfca34dbb6d84c05b481e5f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111897406"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Microsoft Mixed Reality Toolkit 2.7 릴리스 정보

## <a name="whats-new-in-270"></a>합니다의 새로운 기능

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>OpenXR는 이제 MRTK에서 공식적으로 지원 됩니다.

새 OpenXR 플러그 인이 점점 더 발전 하 고 있으므로 이제 공식적으로 OpenXR을 지원 합니다. 이전 릴리스와 비교할 때 OpenXR를 사용 하 여 프로젝트에 다음 기능을 추가 했습니다.

- [시스템 제공 동작 컨트롤러 모델에 대 한 지원](#support-for-the-system-provided-motion-controller-model-on-openxr)
- WinMR 제스처 (선택, 유지, 조작 및 탐색) 지원 [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)
- [컨트롤러 haptics 지원](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [HoloLens 2의 트레일러 메시 지원 2](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567)의 공간 매핑 지원 [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- HoloLens 2에 대 한 장면 이해 지원 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>이제 동일한 프로필 내에서 레거시 XR 및 XR SDK 데이터 공급자를 사용할 수 있습니다.

이제 데이터 공급자는 적절 한 파이프라인이 선택 된 경우에만 로드 되므로 레거시 XR 및 XR SDK 데이터 공급자가 동일한 프로필 내에 공존할 수 있습니다. 이를 수용 하기 위해 레거시 XR 및 XR SDK 데이터 공급자는 이제 프로필 보기 내의 서로 다른 탭으로 구성 되어 사용자가 대상 XR 파이프라인에 대 한 올바른 프로필을 갖고 있는지 여부를 확인할 수 있도록 지원 합니다.

![이제 레거시 및 XR SDK 데이터 공급자를 단일 프로필로 통합 할 수 있습니다.](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

이를 수용 하기 위해 이제 null 데이터 공급자가 더 이상 로드 되지 않고 프로필 검사자에 표시 됩니다. 사용자는 `Show null data providers in the profile inspector` **편집 > 프로젝트 설정-> Mixed Reality Toolkit** 에서 전환 하 여 누락 된 데이터 공급자가 있는 예기치 않은 동작을 디버그할 수 있습니다.

![Null 데이터 공급자는 이제 기본적으로 숨겨져 있습니다. ](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
 ![ 프로필 검사자에서 null 데이터 공급자 표시 설정/해제](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>환경 설정 및 연결 된 혼합 현실 장면 콘텐츠 동작을 추가 했습니다.

사용자는 이제 [환경 설정을](../features/experience-settings/experience-settings.md)구성할 수 있습니다. 그러면 MRTK가 대상 환경에 따라 [혼합 된 현실 장면 콘텐츠](../features/experience-settings/scene-content.md) 를 적절 하 게 표시할 수 있습니다.

사용자의 이전 환경 크기 조정 설정이 새 환경 설정 프로필과 일치 하지 않는 경우 검사기에서 수정 하 라는 메시지가 표시 됩니다.

![환경 규모 마이그레이션](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>이제 다시 디자인 된 Configurator가 설치 프로세스를 안내 합니다.

새 MRTK configurator는 XR 개발을 위한 프로젝트를 적절 하 게 구성 하 고 MRTK와 함께 사용 하기 위한 단계별 지침을 제공 합니다. XR 파이프라인을 선택 하 고, 플랫폼별 플러그인을 가져오고, TextMeshPro을 가져오고, 예제 (UPM를 사용 하는 경우)를 표시 하 고, 기타 이전에 포함 된 프로젝트에 대 한 권장 설정을 다룹니다.

![파이프라인 목록을 표시 하는 Configurator](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>로 텔레포트 핫스폿

새 [텔레포트 핫스팟 구성 요소가](../features/teleport-system/teleport-hotspot.md) 그라데이션 되었습니다. GameObject에 텔레포트 핫스팟을 추가 하 여 해당 위치로 텔레포트 할 때 사용자가 특정 위치 및 방향에 있는지 확인할 수 있습니다.

![텔레포트 핫스팟 예](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>그라데이션 유지

지속 기능 및 예제는 이제 실험적에서 진행 됩니다. 대규모 HoloLens 2 스타일 단추의 새로운 예는 샘플 장면에 포함 되어 있습니다.

![지속 주인공](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>도약 동작 Unity 모듈 버전 4.6.0, 4.7.0, 4.7.1 및 4.8.0에 대 한 지원이 추가 되었습니다.

최신 버전의 [Leap 동작 Unity 모듈](https://developer.leapmotion.com/unity) 에 대 한 지원은 이제 MRTK 합니다와 호환 됩니다.  자세한 내용은 [Leap 동작에 대해 MRTK를 구성 하는 방법을](../supported-devices/leap-motion-mrtk.md) 참조 하세요.

@jackyangzzh새 LeapMotionOrientationExample 장면에 참여 해 주셔서 감사 합니다.

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>대상 음성 이벤트가 발생 하면 더 이상 응시 포인터로 제한 되지 않습니다.

이전에는 대상 음성 이벤트는 응시 포인터를 사용 하 여 포커스가 있는 개체 에서만 발생할 수 있었습니다. 이제 개체는 포인터에 포커스가 있는 경우 음성 이벤트를 받을 수 있습니다.

![Far 포인터가 있는 음성 이벤트](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>HTK에서 MRTK로 이식 되는 TextToSpeech

이제 MRTK에서 beloved TextToSpeech 스크립트를 사용 하 여를 사용 하 여 UWP 플랫폼에서 텍스트의 음성을 생성할 수 있습니다 [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) . 또한 기능을 보여 주기 위해 샘플 장면을 추가 했습니다.

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>OpenXR에서 시스템 제공 동작 컨트롤러 모델에 대 한 지원

OpenXR에서 시스템 제공 동작 컨트롤러 모델에 대 한 지원 (편집기 및 런타임)이 모두 추가 되었습니다.

![두 개의 동작 컨트롤러 모델을 보여 주는 편집기 창](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>OpenXR에 대 한 HoloLens 2의 트레일러 메시 지원

![MRTK 예제 장면에서 장치에서 실행 되는 핸드 메시](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>레거시 WMR, Windows XR 플러그 인 및 OpenXR에서의 컨트롤러 haptics 지원

레거시 WMR, Windows XR 플러그 인 및 OpenXR에서 컨트롤러 haptics에 대 한 지원이 추가 되었습니다. [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Windows XR 플러그 인에 대 한 아이 추적 지원

Windows XR 플러그 인 최소 버전 합니다 (Unity 2019), 4.4.2 (Unity 2020) 및 5.2.2 (Unity 2021)를 사용 하는 경우 눈동자 응시에 대 한 지원이 추가 되었습니다. [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>주목할 만한 수정 및 변경 내용

- 더 부드럽게 검색 했습니다. 이제 실수로 손가락을 삭제 하는 것이 더 어려워집니다. [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- 이제 개체 조작자 구성 요소가 있는 개체는 플래그가 설정 되 면 릴리스에 대 한 속도를 일관 되 게 유지 합니다. [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- 이제 strafing가 바닥을 확인 하 여 카메라가 환경에 클리핑할 수 있는 상황이 나 사용자가 빈 공간을 마우스 포인터로 이동 하는 상황을 방지 합니다. [#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject는 이제 가상 속성으로, 구 또는 poke 포인터를 확장할 때 더 많은 유연성을 허용 합니다. [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- 이제 단추를 사용 하 여 사용 가능한 음성 명령을 표시할 때 적절 한 키워드를 표시 합니다. [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- 이제 oculus 컨트롤러는 자체의 독립 실행형 시각화 도우미를 사용 하 여 충돌 방지에서 Oculus 통합 패키지의 시각화를 사용 하 여 MRTK 시각화를 방지 합니다. [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- 최신 Unity 버전 (2019.4.25 + & 2020.3.2 +)의 동작과 맞추기 위해 키보드 관련 스크립트가 변경 되었습니다. 릴리스를 기반으로 자동 완성 버그와 TMP 입력 필드 버그 (둘 다 MRTK가 외부에 있습니다)가 HoloLens에 영향을 줍니다. 자세한 내용은 [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) 및 [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724)를 참조 하세요.
- 스크롤 개체 컬렉션의 성능이 개선 되었습니다. 또한 중복 된 경우에는 컬렉션 내에서 GameObject를 발생 시키는 문제를 해결 했습니다. [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- 장면 이해 데모 스크립트에서 함수를 추가 `GetSceneObjectsOfType` 하 여 특정 종류의 관찰 된 모든 장면 개체를 검색 합니다. [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- 명령줄 빌드 도구에서 `sceneList` 또는 `sceneListFile` 플래그 (플래그가 있는 경우)로 지정 된 장면이 빌드에 포함 됩니다. [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- 빌드 도구에는 `nuget.exe` `msbuild` (기본 옵션)를 사용 하는 대신 경로를 지정 하 고 패키지 복원을 수행 하는 데 사용할 수 있는 새로운 옵션이 있습니다. [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- Windows XR 플러그 인을 사용 하는 경우 부실 손을 조인트 하 고 두 배가 되는 문제가 해결 되었습니다. [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- Windows XR 플러그 인의 자동 원격 기능을 사용 하 여 입력 및 상호 작용이 누락 되는 문제를 해결 했습니다. [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- BuildDeployWindow에서 Windows SDK 경로에 대해 잘못 된 레지스트리 키를 쿼리해야 하는 문제를 해결 했습니다. [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- MRTK의 글 어 가져오기는 이제 선택 사항입니다. 여러 글 어 가져오기가 있으면 `MRTK_GLTF_IMPORTER_OFF` 사용자 지정 스크립팅 기호 정의에 추가 하 여 MRTK를 사용 하지 않도록 설정할 수 있습니다. [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- OpenVR의 Knuckles 컨트롤러가 제대로 검색 되지 않는 문제가 해결 되었습니다. [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- 손 메쉬를 시각화할 때 프레임당 할당 수를 줄입니다 [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- 예제를 쉽게 가져올 수 있도록 MRTK 예제 패키지 (Unity 패키지 관리자)를 시작 하는 메뉴 항목이 추가 되었습니다 [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- Unity 2020.3를 사용 하는 경우 로드 시간 경고 수가 줄어듭니다.
- 추가 된 빌드 창 기능 설명서: [페이지 방문](/windows/mixed-reality/mrtk-unity/features/tools/build-window)

## <a name="known-issues"></a>알려진 문제

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>오디오 데모에 asmdef 파일(UPM 패키지)이 없습니다.

Mixed Reality 기능 도구를 통해 MRTK를 가져올 때 Unity 패키지 관리자 UI를 사용하여 샘플 및 데모가 프로젝트에 추가됩니다. 오디오 데모를 가져온 후 `WindowsMicrophoneStreamDemo.unity` 장면이 제대로 작동하지 않습니다. 이는 샘플에 대한 .asmdef 파일이 누락된 결과입니다.

이 [문제를](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908)해결하려면 다음 단계를 수행하세요.

- 라이브러리/PackageCache/com.microsoft.mixedreality.toolkit.examples@ 복사[...] /MRTK. "Assets/Samples/Mixed Reality Toolkit Examples" 폴더에 대한 Examples.asmdef
- 복사한 파일의 이름을 예제로 바꿉니다.
- Examples 파일 열기
- 이름 상자에서 내용을 예제로 대체합니다.
- 적용을 클릭합니다.
- 빌드 및 배포

이 문제는 향후 MRTK 릴리스에서 해결될 예정입니다.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>UNITY 2020.3에서 MRTK 빌드 창이 무기한 "자산 가져오기" 대화 상자를 트리거합니다.

Unity 2020.3의 MRTK 빌드 창에는 UWP 빌드를 성공적으로 수행한 후 "자산 가져오기" 대화 상자가 완료되지 않는 알려진 [문제가](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) 있습니다. 이 문제는 Unity와 협력하여 조사되고 있습니다.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Unity 2020의 Text Mesh Pro Canvas 렌더러 경고

Unity 2020을 사용하는 동안 대부분의 MRTK 예제 장면에 다음 경고가 기록됩니다.

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

Canvas 렌더러 경고가 [TextMeshPro 버전 3.0.3에](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3)추가되었습니다.  이러한 경고는 MRTK의 예제 장면에 영향을 미치지 않으며 콘솔에서 지울 수 있습니다. 자세한 내용은 [문제 9811을](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) 참조하세요.
