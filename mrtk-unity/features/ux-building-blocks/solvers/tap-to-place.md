---
title: 탭하여 배치
description: TapToPlace MRTK 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 탭하여 배치,
ms.openlocfilehash: 98408312ec2637dc3fa137e7d51cce1f37e816f9a21b703ec9216bf90251661f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198321"
---
# <a name="tap-to-place"></a>탭하여 배치

![TapToPlace](../../images/solver/tap-to-place/TapToPlaceIntroGif.gif)

탭하여 배치는 게임 개체를 표면에 배치하는 데 사용되는 원거리 상호 작용 구성 요소입니다. 이 구성 요소는 공간 메시에 개체를 배치하는 데 유용합니다. 탭하여 배치는 두 번의 클릭과 헤드 이동의 조합을 사용하여 개체를 배치합니다. 한 번 클릭하여 배치를 시작하고 헤드 이동으로 개체의 위치를 제어하고 한 번 클릭하여 장면에 개체를 배치합니다.

## <a name="using-tap-to-place"></a>탭하여 배치 사용

1. 장면 설정
    - 새 unity 장면 만들기
    - **Mixed Reality 도구 키트** > **장면에 추가 및 구성** 으로 이동하여 장면에 MRTK를 추가합니다.
    > [!NOTE]
    > 탭하여 배치에서는 MRTK 입력 시스템에서 구동하는 클릭을 사용하지만 클릭하지 않고 제어할 수도 있습니다. 아래에서 탭하여 배치 코드 구성 섹션을 참조하세요.
    - 장면에 큐브를 추가하고 배율을 0.2로 변경하고 위치를 (0, 0, 0.7)로 변경합니다.
1. 충돌체를 사용하여 게임 개체에 [탭하여 배치](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) 연결

    ![TapToPlaceInspector](../../images/solver/tap-to-place/TapToPlaceInspector2.png)

    - 탭하여 배치 구성 요소가 추가되면 솔버 처리기도 연결됩니다. 탭하여 배치는 솔버 처리기가 필요한 [솔버](solver.md) 클래스에서 파생됩니다. 탭하여 배치 개체의 위치는 솔버 처리기 내에서 `TrackedTargetType`을 기준으로 계산됩니다. 기본적으로 헤드는 `TrackedTargetType`입니다. 즉, 헤드가 움직일 때 개체는 따라갑니다(선택된 경우).  `TrackedTargetType`은 개체가 컨트롤러를 따르는 컨트롤러 광선으로 설정할 수도 있습니다. 탭하여 배치 검사기의 첫 번째 속성 그룹은 [공통 솔버 속성](solver.md#common-solver-properties)입니다.  
    > [!IMPORTANT]
    > 탭하여 배치는 독립 실행형 솔버이며 다른 솔버와 연결할 수 없습니다. 배치되는 동안 개체의 위치를 업데이트하는 데 SolverHandler.UpdateSolvers가 사용되기 때문에 연결될 수 없습니다.
    - 탭하여 배치 속성:
        - `Auto Start`: true이면 탭하여 배치 솔버가 배치할 게임 개체의 위치를 제어하기 시작합니다. 개체는 TrackedTargetType(헤드 또는 컨트롤러 광선)을 따라 즉시 시작됩니다. 효과를 적용하기 위해 Start()를 호출하기 전에 이 값을 수정해야 합니다.
        - `Default Placement Distance`: 개체가 SolverHandler의 TrackedTargetType 전방에 상대적으로 배치된 기본 거리(미터)입니다. 광선 투사에서 표면에 비추지 않는 경우 게임 개체가 기본 배치 거리에 놓입니다.
        - `Max Raycast Distance`: 'TrackedTargetType' 원점을 기준으로 하는 광선 투사의 최대 거리(미터)입니다. 이 광선 투사는 선택한 개체를 배치할 표면을 찾습니다.
        - `UseDefaultSurfaceNormalOffset`: 이 속성은 기본적으로 true이며 배치되는 개체가 표면에 정렬되도록 합니다. 이 속성이 true이면 `SurfaceNormalOffset` 속성에 지정된 값 대신 기본 표면 법선 오프셋이 적용됩니다. false이면 `SurfaceNormalOffset`의 값이 적용됩니다. 기본 표면 법선 오프셋은 z축을 따르는 충돌체의 범위입니다.
        - `Surface Normal Offset`: 광선 투사가 표면에 비추는 경우 배치할 게임 개체의 중심과 표면 법선을 따르는 표면 사이의 거리입니다. 이 속성은 `UseDefaultSurfaceNormalOffset`이 false인 경우에만 개체에 적용됩니다.
        - `Keep Orientation Vertical`: true인 경우 배치할 게임 개체가 Vector3.up과 일직선으로 유지됩니다.
        - `Rotate According to Surface`: false이면 배치할 게임 개체가 표면 비추기에 따라 회전을 변경하지 않습니다.  개체는 IsBeingPlaced가 true인 동안 카메라를 향하고 있습니다.
        - `Magnetic Surfaces`: 가장 높은 우선 순위에서 가장 낮은 우선 순위로 실행할 LayerMask 배열입니다. 광선 투사 비추기를 제공하기 위한 첫 번째 계층 마스크는 위치 계산에 사용됩니다.
        - `Debug Enabled`: true이면 Unity 편집기에서 광선 투사 비추기의 법선이 노란색으로 그려집니다. 개체가 현재 방향으로 설정된 이유를 시각적으로 설명하는 표면 비추기의 법선을 그리기 때문에 `RotateAccordingToSurface`가 true일 때 디버그를 사용하도록 설정하면 유용합니다.
        - `On Placing Started`:이 이벤트는 배치할 게임 개체가 선택될 때 한 번 트리거됩니다.
        - `On Placing Stopped`:이 이벤트는 배치할 게임 개체가 선택 해제되어 배치될 때 한 번 트리거됩니다.

1. 편집기에서 탭하여 배치 동작 테스트
    - 재생을 누르고 스페이스바를 길게 눌러 입력 시뮬레이션 손을 표시합니다.
    - 큐브에 초점이 맞춰질 때까지 손을 이동하고 마우스 왼쪽 단추로 클릭하여 입력 시뮬레이션 손으로 클릭을 시뮬레이션합니다.
        - 충돌체가 장면에 없으면 개체는 정의된 `Default Placement Distance`에서 `TrackedTargetType`을 따릅니다.
    - 개체는 선택 후 `TrackedTargetType`의 이동을 따릅니다. 편집기에서 헤드 이동을 시뮬레이션하려면 WASD 키를 누릅니다. 마우스 오른쪽 단추를 클릭한 상태에서 헤드 회전을 변경합니다.
    - 개체 배치를 중지하려면 다시 클릭합니다.  배치 중지 클릭을 위해 개체에 초점을 맞출 필요는 없습니다. 초점은 배치 프로세스를 시작하는 초기 클릭에만 필요합니다.

    `TrackedTargetType`: 헤드(기본값) |  `TrackedTargetType`: 컨트롤러 광선
    :-------------------------:|:-------------------------:
    ![탭하여 배치 입력 시뮬레이션 헤드 컨트롤 광선](../../images/solver/tap-to-place/TapToPlaceInputSimulationHead.gif)  |  ![탭하여 배치 입력 시뮬레이션 컨트롤러 광선 2](../../images/solver/tap-to-place/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a>탭하여 배치 코드 구성

탭하여 배치 개체 선택 타이밍은 클릭 이벤트를 요구하는 대신 `StartPlacement()` 및 `StopPlacement()`를 통해 제어할 수도 있습니다. 이 기능은 테스트를 작성하는 데 유용하며 MRTK 입력 시스템을 사용하지 않고 편집기에 개체를 배치하는 대체 방법을 제공합니다.

1. 빈 게임 개체 만들기
1. 다음 스크립트 예를 만들어 빈 게임 개체에 연결합니다.

    ```c#
    using UnityEngine;
    using Microsoft.MixedReality.Toolkit.Utilities.Solvers;

    public class TapToPlaceInputExample : MonoBehaviour
    {
        private GameObject cube;
        private TapToPlace tapToPlace;

        void Start()
        {
            cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
            cube.transform.localScale = Vector3.one * 0.2f;
            cube.transform.position = Vector3.forward * 0.7f;

            tapToPlace = cube.AddComponent<TapToPlace>();
        }

        void Update()
        {
            if (Input.GetKeyDown(KeyCode.U))
            {
                tapToPlace.StartPlacement();
            }
            if (Input.GetKeyDown(KeyCode.I))
            {
                tapToPlace.StopPlacement();
            }
        }
    }
    ```

1. 재생 모드에서 *U 키* 를 눌러 큐브 배치를 시작합니다.
1. 배치를 중지하려면 *I 키* 를 누릅니다.

## <a name="tap-to-place-example-scene"></a>탭하여 배치 장면 예

탭하여 배치 장면 예는 각각 서로 다른 구성이 있는 4개의 배치 가능 개체로 구성되어 있습니다. 장면 예에는 계층 구조에서 기본적으로 사용하지 않도록 설정된 표면 배치 동작을 보여 주는 벽이 포함되어 있습니다. 장면 예는 [릴리스 페이지](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)에 있는 Microsoft.MixedReality.Toolkit.Unity.Examples Unity 패키지에서 찾을 수 있습니다. 장면 위치는 *MRTK.Examples/Demos/Solvers/Scenes/TapToPlaceExample.unity* 입니다.

![탭하여 배치 예](../../images/solver/tap-to-place/TapToPlaceExampleScene.gif)

## <a name="see-also"></a>참조

- [해결기](solver.md)
- [공간 인식](../../spatial-awareness/spatial-awareness-getting-started.md)
- [입력 시뮬레이션](../../input-simulation/input-simulation-service.md)
- [손 추적](../../input/hand-tracking.md)
- [응시](../../input/gaze.md)
