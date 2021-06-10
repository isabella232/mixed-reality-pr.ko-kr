---
title: Unity의 굴절형 손 및 시선 추적
description: Unity에서 응시에 대한 작업을 취하는 두 가지 주요 방법인 손 제스처 및 모션 컨트롤러에 대해 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 제스처, 모션 컨트롤러, unity, 응시, 입력, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: ff4c4b064e11e0cad45f4b0c1aaa90c61eda51d7
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600662"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Unity의 굴절형 손 및 시선 추적

HoloLens 2 굴절형 손 및 시선 추적과 같은 새롭고 흥미로운 기능을 도입했습니다.

Unity에서 새로운 기능을 활용하는 가장 쉬운 방법은 MRTK를 통하는 것입니다. 시작하는 데 도움이 되는 몇 가지 예제 장면도 있습니다.

* [MRTK에서 조인된 손 시작](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
* [MRTK에서 시선 추적 시작](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>MRTK에서 손, 눈 및 기타를 지원하는 구성 요소

MRTK v2는 개발을 가속화하는 데 도움이 되는 UI 컨트롤 및 구성 요소 집합을 제공합니다.

|  [![단추](images/MRTK_Button_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) [단추](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) | [ ![ 경계 상자](images/MRTK_BoundingBox_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) [경계 상자](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) | [ ![ 조작 처리기](images/MRTK_Manipulation_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) [조작 처리기](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) |
|:--- | :--- | :--- |
| HoloLens2의 굴절된 손을 비롯한 다양한 입력 메서드를 지원하는 단추 컨트롤 | 3D 공간에서 개체 조작을 위한 표준 UI | 한 손 또는 양손을 사용하여 개체를 조작하기 위한 스크립트 |
|  [![슬레이트](images/MRTK_Slate_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) [슬레이트](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) | [![시스템 키보드](images/MRTK_SystemKeyboard_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) [시스템 키보드](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) | [![상호 작용 가능](images/InteractableExamples.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) [상호 작용 가능](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) |
| 2D 스타일 평면 - 굴절형 손 입력을 사용하여 스크롤을 지원합니다. | Unity에서 시스템 키보드를 사용하는 예제 스크립트  | 시각적 상태 및 테마 지원으로 개체를 상호 작용 가능하게 만드는 스크립트 |
|  [![Solver](images/MRTK_Solver_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) [Solver](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) | [![개체 컬렉션](images/MRTK_ObjectCollection_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) [개체 컬렉션](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) | [![도구 설명](images/MRTK_Tooltip_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) [도구 설명](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) |
| 태그 따라, 본문 잠금, 상수 뷰 크기 및 표면 자성과 같은 다양한 개체 위치 지정 동작 | 3차원 모양으로 개체 배열을 레이아웃하는 스크립트 | 모션 컨트롤러 및 개체의 레이블을 지정하는 데 사용할 수 있는 유연한 앵커/피벗 시스템을 사용하는 주석 UI입니다. |
|  [![앱 바](images/MRTK_AppBar_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) [앱 바](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) | [![포인터](images/MRTK_Pointer_Main.png)](/windows/mixed-reality/mrtk-unity/features/input/pointers) [포인터](/windows/mixed-reality/mrtk-unity/features/input/pointers) | [![손끝 시각화](images/MRTK_FingertipVisualization_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) [손끝 시각화](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) |
| 경계 상자의 수동 활성화를 위한 UI | 다양한 종류의 포인터에 대해 알아보기 | 직접 상호 작용에 대한 신뢰도를 향상시키는 손끝의 시각적 어포던스 |
|  [![시선 추적: 대상 선택](images/mrtk_et_targetselect.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) [시선 추적: 대상 선택](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) | [![시선 추적: 탐색](images/mrtk_et_navigation.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) [시선 추적: 탐색](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) | [![시선 추적: 열 지도](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) [시선 추적: 열 지도](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| 눈, 음성 및 손 입력을 결합하여 장면 전체에서 홀로그램을 빠르고 쉽게 선택합니다. | 텍스트를 자동으로 스크롤하거나 보고 있는 내용에 따라 포커스가 있는 콘텐츠를 확대하는 방법을 알아봅니다.| 앱에서 사용자가 보고 있는 내용을 로깅, 로드 및 시각화하는 예제 |

## <a name="example-scenes"></a>예제 장면

[이 예제 장면](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)에서 MRTK의 다양한 상호 작용 유형과 UI 컨트롤을 살펴봅니다.

**Assets/MixedRealityToolkit.Examples/Demos** 폴더의 [Mixed Reality Toolkit GitHub에서](https://github.com/Microsoft/MixedRealityToolkit-Unity) 다른 예제 장면을 찾을 수 있습니다.

[![예제 장면](images/MRTK_Examples.png)](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unity 개발 여정을 수행하는 경우 MRTK 핵심 구성 요소 탐색을 진행하는 중입니다. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [공간 매핑](spatial-mapping-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참조

* [시선 기반 상호 작용](../../design/eye-gaze-interaction.md)
* [HoloLens 2의 시선 추적](../../design/eye-tracking.md)
* [응시 및 커밋](../../design/gaze-and-commit.md)
* [손 - 직접 조작](../../design/direct-manipulation.md)
* [손 - 제스처](../../design/gaze-and-commit.md#composite-gestures)
* [손 - 가리키고 커밋](../../design/point-and-commit.md)
* [Instinctual 상호 작용](../../design/interaction-fundamentals.md)
* [모션 컨트롤러](../../design/motion-controllers.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)