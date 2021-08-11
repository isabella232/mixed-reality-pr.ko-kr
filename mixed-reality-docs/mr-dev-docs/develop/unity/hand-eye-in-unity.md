---
title: Unity에서의 트레일러 및 눈 추적
description: Unity, 핸드 제스처 및 동작 컨트롤러의 응시에서 작업을 수행 하는 두 가지 주요 방법에 대해 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 제스처, 동작 컨트롤러, unity, 응시, 입력, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, 혼합 현실 Toolkit
ms.openlocfilehash: 005b817574e6d3600b9c43e443432203418b58a2258e2938614cc549ab7539c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223839"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Unity에서의 트레일러 및 눈 추적

HoloLens 2에는 여러 가지 새롭고 흥미로운 기능 (예: 트레일러 식 및 눈 추적)이 도입 되었습니다.

Unity에서 새로운 기능을 활용 하는 가장 쉬운 방법은 MRTK를 통하는 것입니다. 또한 시작 하는 데 도움이 되는 몇 가지 예제 장면이 있습니다.

* [MRTK에서 트레일러 식 시작](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
* [MRTK에서 눈 추적 시작](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>MRTK에서 실습, 눈동자 및 기타 항목을 지 원하는 빌딩 블록

MRTK v2는 개발을 가속화 하는 데 도움이 되는 UI 컨트롤 및 구성 요소 집합을 제공 합니다.

|  [![단추](images/MRTK_Button_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) [단추](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) | [ ![ 경계 상자](images/MRTK_BoundingBox_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) [경계 상자](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) | [ ![ 조작 처리기](images/MRTK_Manipulation_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) [조작 처리기](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) |
|:--- | :--- | :--- |
| HoloLens2's를 포함 하는 다양 한 입력 메서드를 지 원하는 button 컨트롤입니다. | 3D 공간에서 개체 조작을 위한 표준 UI | 한 손 또는 양손을 사용하여 개체를 조작하기 위한 스크립트 |
|  [![슬레이트](images/MRTK_Slate_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) [슬레이트](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) | [![시스템 키보드](images/MRTK_SystemKeyboard_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) [시스템 키보드](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) | [![상호 작용 가능](images/InteractableExamples.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) [상호 작용 가능](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) |
| 트레일러 식 입력으로 스크롤을 지 원하는 2D 스타일 평면 | Unity에서 시스템 키보드를 사용하는 예제 스크립트  | 시각적 상태 및 테마 지원으로 개체를 상호 작용 가능하게 만드는 스크립트 |
|  [![Solver](images/MRTK_Solver_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) [Solver](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) | [![개체 컬렉션](images/MRTK_ObjectCollection_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) [개체 컬렉션](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) | [![도구 설명](images/MRTK_Tooltip_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) [도구 설명](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) |
| 태그 동반, 본문 잠금, 상수 보기 크기 및 표면 자기와 같은 다양 한 개체 위치 지정 동작 | 3 차원 모양의 개체 배열을 레이아웃 하는 스크립트 | 동작 컨트롤러 및 개체에 레이블을 지정 하는 데 사용할 수 있는 유연한 앵커/피벗 시스템을 포함 하는 주석 UI입니다. |
|  [![앱 바](images/MRTK_AppBar_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) [앱 바](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) | [![포인터](images/MRTK_Pointer_Main.png)](/windows/mixed-reality/mrtk-unity/features/input/pointers) [포인터](/windows/mixed-reality/mrtk-unity/features/input/pointers) | [![손끝 시각화](images/MRTK_FingertipVisualization_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) [손끝 시각화](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) |
| 경계 상자의 수동 활성화를 위한 UI | 다양한 종류의 포인터에 대해 알아보기 | 직접 상호 작용에 대 한 신뢰도를 향상 시키는 fingertip의 시각적 affordance |
|  [![시선 추적: 대상 선택](images/mrtk_et_targetselect.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) [시선 추적: 대상 선택](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) | [![시선 추적: 탐색](images/mrtk_et_navigation.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) [시선 추적: 탐색](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) |
| 눈, 음성 및 손 입력을 결합 하 여 장면 전체의 holograms을 빠르고 간편 하 게 선택 | 표시 되는 내용에 따라 텍스트를 자동으로 스크롤하거나 중요 한 콘텐츠를 확대 하는 방법에 대해 알아봅니다.| 사용자의 앱에서 보고 있는 사용자를 기록, 로드 및 시각화 하는 예제 |

## <a name="example-scenes"></a>예제 장면

[이 예제 장면](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)에서 MRTK의 다양한 상호 작용 유형과 UI 컨트롤을 살펴봅니다.

Mixed Reality의 다른 예제 장면을 [GitHub Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) **자산/MixedRealityToolkit/데모** 폴더 아래에서 찾을 수 있습니다.

[![장면 예](images/MRTK_Examples.png)](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [공간 매핑](spatial-mapping-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목

* [시선 기반 상호 작용](../../design/eye-gaze-interaction.md)
* [HoloLens 2의 시선 추적](../../design/eye-tracking.md)
* [응시 및 커밋](../../design/gaze-and-commit.md)
* [손 - 직접 조작](../../design/direct-manipulation.md)
* [손 - 제스처](../../design/gaze-and-commit.md#composite-gestures)
* [손 - 가리키고 커밋](../../design/point-and-commit.md)
* [Instinctual 상호 작용](../../design/interaction-fundamentals.md)
* [모션 컨트롤러](../../design/motion-controllers.md)
* [UnityEngine. XR](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR 추적](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)