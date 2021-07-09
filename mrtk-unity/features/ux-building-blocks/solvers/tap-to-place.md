---
title: 탭하여 배치
description: TapToPlace MRTK 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 탭하여 배치,
ms.openlocfilehash: 1664509a08c2d589d22b71df580328f3f3655c61
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176400"
---
# <a name="tap-to-place"></a><span data-ttu-id="07453-104">탭하여 배치</span><span class="sxs-lookup"><span data-stu-id="07453-104">Tap to place</span></span>

![TapToPlace](../../images/solver/tap-to-place/TapToPlaceIntroGif.gif)

<span data-ttu-id="07453-106">탭하여 배치는 게임 개체를 표면에 배치하는 데 사용되는 원거리 상호 작용 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="07453-106">Tap to Place is a far interaction component that is used to place a game object on surface.</span></span> <span data-ttu-id="07453-107">이 구성 요소는 공간 메시에 개체를 배치하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-107">This component is useful for placing objects on a spatial mesh.</span></span> <span data-ttu-id="07453-108">탭하여 배치는 두 번의 클릭과 헤드 이동의 조합을 사용하여 개체를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-108">Tap to Place uses a combination of two clicks and head movement to place an object.</span></span> <span data-ttu-id="07453-109">한 번 클릭하여 배치를 시작하고 헤드 이동으로 개체의 위치를 제어하고 한 번 클릭하여 장면에 개체를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-109">A click to start the placement, head movement to control the position of the object and a click to place the object in the scene.</span></span>

## <a name="using-tap-to-place"></a><span data-ttu-id="07453-110">탭하여 배치 사용</span><span class="sxs-lookup"><span data-stu-id="07453-110">Using Tap to Place</span></span>

1. <span data-ttu-id="07453-111">장면 설정</span><span class="sxs-lookup"><span data-stu-id="07453-111">Set up the scene</span></span>
    - <span data-ttu-id="07453-112">새 unity 장면 만들기</span><span class="sxs-lookup"><span data-stu-id="07453-112">Create a new unity scene</span></span>
    - <span data-ttu-id="07453-113">**Mixed Reality 도구 키트** > **장면에 추가 및 구성** 으로 이동하여 장면에 MRTK를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-113">Add MRTK to the scene by navigating to the **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    > [!NOTE]
    > <span data-ttu-id="07453-114">탭하여 배치에서는 MRTK 입력 시스템에서 구동하는 클릭을 사용하지만 클릭하지 않고 제어할 수도 있습니다. 아래에서 탭하여 배치 코드 구성 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07453-114">Tap to Place uses clicks driven by the MRTK Input System but it can also be controlled without clicks, see the Tap To Place Code Configurability section below.</span></span>
    - <span data-ttu-id="07453-115">장면에 큐브를 추가하고 배율을 0.2로 변경하고 위치를 (0, 0, 0.7)로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-115">Add a cube to the scene and change the scale to 0.2 and change the position to (0, 0, 0.7).</span></span>
1. <span data-ttu-id="07453-116">충돌체를 사용하여 게임 개체에 [탭하여 배치](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) 연결</span><span class="sxs-lookup"><span data-stu-id="07453-116">Attach [Tap to Place](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) to a game object with a collider</span></span>

    ![TapToPlaceInspector](../../images/solver/tap-to-place/TapToPlaceInspector2.png)

    - <span data-ttu-id="07453-118">탭하여 배치 구성 요소가 추가되면 솔버 처리기도 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="07453-118">When the Tap to Place component is added, a Solver Handler will also be attached.</span></span> <span data-ttu-id="07453-119">탭하여 배치는 솔버 처리기가 필요한 [솔버](solver.md) 클래스에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="07453-119">Tap to Place derives from the [Solver](solver.md) class which requires a Solver Handler.</span></span> <span data-ttu-id="07453-120">탭하여 배치 개체의 위치는 솔버 처리기 내에서 `TrackedTargetType`을 기준으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="07453-120">The position of a Tap to Place object is calculated relative to the `TrackedTargetType` within the Solver Handler.</span></span> <span data-ttu-id="07453-121">기본적으로 헤드는 `TrackedTargetType`입니다. 즉, 헤드가 움직일 때 개체는 따라갑니다(선택된 경우).</span><span class="sxs-lookup"><span data-stu-id="07453-121">By default the Head is the `TrackedTargetType`, i.e. when the head moves, the object follows if it is selected.</span></span>  <span data-ttu-id="07453-122">`TrackedTargetType`은 개체가 컨트롤러를 따르는 컨트롤러 광선으로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07453-122">The `TrackedTargetType` can also be set to Controller Ray which has the object follow the controller.</span></span> <span data-ttu-id="07453-123">탭하여 배치 검사기의 첫 번째 속성 그룹은 [공통 솔버 속성](solver.md#common-solver-properties)입니다.</span><span class="sxs-lookup"><span data-stu-id="07453-123">The first group of properties in the Tap to Place inspector are the [Common Solver Properties](solver.md#common-solver-properties).</span></span>  
    > [!IMPORTANT]
    > <span data-ttu-id="07453-124">탭하여 배치는 독립 실행형 솔버이며 다른 솔버와 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07453-124">Tap to Place is a stand alone Solver and cannot be chained with other Solvers.</span></span> <span data-ttu-id="07453-125">배치되는 동안 개체의 위치를 업데이트하는 데 SolverHandler.UpdateSolvers가 사용되기 때문에 연결될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07453-125">It cannot be chained because SolverHandler.UpdateSolvers is used to update the object's position while it is being placed.</span></span>
    - <span data-ttu-id="07453-126">탭하여 배치 속성:</span><span class="sxs-lookup"><span data-stu-id="07453-126">Tap to Place Properties:</span></span>
        - <span data-ttu-id="07453-127">`Auto Start`: true이면 탭하여 배치 솔버가 배치할 게임 개체의 위치를 제어하기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-127">`Auto Start`: If true, the Tap to Place solver will start out controlling the position of the game object to be placed.</span></span> <span data-ttu-id="07453-128">개체는 TrackedTargetType(헤드 또는 컨트롤러 광선)을 따라 즉시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="07453-128">The object will immediately start following the TrackedTargetType (Head or Controller Ray).</span></span> <span data-ttu-id="07453-129">효과를 적용하기 위해 Start()를 호출하기 전에 이 값을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-129">This value must be modified before Start() is invoked in order to have any effect.</span></span>
        - <span data-ttu-id="07453-130">`Default Placement Distance`: 개체가 SolverHandler의 TrackedTargetType 전방에 상대적으로 배치된 기본 거리(미터)입니다.</span><span class="sxs-lookup"><span data-stu-id="07453-130">`Default Placement Distance`: The default distance (in meters) an object will be placed relative to the TrackedTargetType forward in the SolverHandler.</span></span> <span data-ttu-id="07453-131">광선 투사에서 표면에 비추지 않는 경우 게임 개체가 기본 배치 거리에 놓입니다.</span><span class="sxs-lookup"><span data-stu-id="07453-131">The game object will be placed at the default placement distance if a surface is not hit by the raycast.</span></span>
        - <span data-ttu-id="07453-132">`Max Raycast Distance`: 'TrackedTargetType' 원점을 기준으로 하는 광선 투사의 최대 거리(미터)입니다.</span><span class="sxs-lookup"><span data-stu-id="07453-132">`Max Raycast Distance`: The max distance (meters) for the raycast based on the 'TrackedTargetType' origin.</span></span> <span data-ttu-id="07453-133">이 광선 투사는 선택한 개체를 배치할 표면을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="07453-133">This raycast looks for a surface to place a selected object.</span></span>
        - <span data-ttu-id="07453-134">`UseDefaultSurfaceNormalOffset`: 이 속성은 기본적으로 true이며 배치되는 개체가 표면에 정렬되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-134">`UseDefaultSurfaceNormalOffset`: This property is true by default, it ensures the object being placed is aligned on a surface.</span></span> <span data-ttu-id="07453-135">이 속성이 true이면 `SurfaceNormalOffset` 속성에 지정된 값 대신 기본 표면 법선 오프셋이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07453-135">If this property is true, the default surface normal offset will be applied instead of any value specified for the `SurfaceNormalOffset` property.</span></span> <span data-ttu-id="07453-136">false이면 `SurfaceNormalOffset`의 값이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07453-136">If false, the value for `SurfaceNormalOffset` will be applied.</span></span> <span data-ttu-id="07453-137">기본 표면 법선 오프셋은 z축을 따르는 충돌체의 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="07453-137">The default surface normal offset is the collider's extents along the z axis.</span></span>
        - <span data-ttu-id="07453-138">`Surface Normal Offset`: 광선 투사가 표면에 비추는 경우 배치할 게임 개체의 중심과 표면 법선을 따르는 표면 사이의 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="07453-138">`Surface Normal Offset`: The distance between the center of the game object to place and a surface along the surface normal, if the raycast hits a surface.</span></span> <span data-ttu-id="07453-139">이 속성은 `UseDefaultSurfaceNormalOffset`이 false인 경우에만 개체에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07453-139">This property is only applied to an object if `UseDefaultSurfaceNormalOffset` is false.</span></span>
        - <span data-ttu-id="07453-140">`Keep Orientation Vertical`: true인 경우 배치할 게임 개체가 Vector3.up과 일직선으로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="07453-140">`Keep Orientation Vertical`: If true, the game object to place will remain upright and in line with Vector3.up.</span></span>
        - <span data-ttu-id="07453-141">`Rotate According to Surface`: false이면 배치할 게임 개체가 표면 비추기에 따라 회전을 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07453-141">`Rotate According to Surface`: If false, the game object to place will not change its rotation according to the surface hit.</span></span>  <span data-ttu-id="07453-142">개체는 IsBeingPlaced가 true인 동안 카메라를 향하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07453-142">The object will remain facing the camera while IsBeingPlaced is true.</span></span>
        - <span data-ttu-id="07453-143">`Magnetic Surfaces`: 가장 높은 우선 순위에서 가장 낮은 우선 순위로 실행할 LayerMask 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="07453-143">`Magnetic Surfaces`: An array of LayerMasks to execute from highest to lowest priority.</span></span> <span data-ttu-id="07453-144">광선 투사 비추기를 제공하기 위한 첫 번째 계층 마스크는 위치 계산에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07453-144">First layer mask to provide a raycast hit will be used for position calculations.</span></span>
        - <span data-ttu-id="07453-145">`Debug Enabled`: true이면 Unity 편집기에서 광선 투사 비추기의 법선이 노란색으로 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="07453-145">`Debug Enabled`: If true and in the Unity Editor, the normal of the raycast hit will be drawn in yellow.</span></span> <span data-ttu-id="07453-146">개체가 현재 방향으로 설정된 이유를 시각적으로 설명하는 표면 비추기의 법선을 그리기 때문에 `RotateAccordingToSurface`가 true일 때 디버그를 사용하도록 설정하면 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-146">Debug enabled is useful when `RotateAccordingToSurface` is true because it draws the normal of the surface hit which visually explains why the object is set at its current orientation.</span></span>
        - <span data-ttu-id="07453-147">`On Placing Started`:이 이벤트는 배치할 게임 개체가 선택될 때 한 번 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="07453-147">`On Placing Started`: This event is triggered once when the game object to place is selected.</span></span>
        - <span data-ttu-id="07453-148">`On Placing Stopped`:이 이벤트는 배치할 게임 개체가 선택 해제되어 배치될 때 한 번 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="07453-148">`On Placing Stopped`: This event is triggered once when the game object to place is unselected, placed.</span></span>

1. <span data-ttu-id="07453-149">편집기에서 탭하여 배치 동작 테스트</span><span class="sxs-lookup"><span data-stu-id="07453-149">Testing Tap to Place behavior in editor</span></span>
    - <span data-ttu-id="07453-150">재생을 누르고 스페이스바를 길게 눌러 입력 시뮬레이션 손을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-150">Press play and hold the space bar to show an input simulation hand.</span></span>
    - <span data-ttu-id="07453-151">큐브에 초점이 맞춰질 때까지 손을 이동하고 마우스 왼쪽 단추로 클릭하여 입력 시뮬레이션 손으로 클릭을 시뮬레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-151">Move the hand until the cube is in focus and simulate a click with the input simulation hand by clicking with the left mouse.</span></span>
        - <span data-ttu-id="07453-152">충돌체가 장면에 없으면 개체는 정의된 `Default Placement Distance`에서 `TrackedTargetType`을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="07453-152">If colliders are not present in the scene, the object will follow the `TrackedTargetType` at the defined `Default Placement Distance`.</span></span>
    - <span data-ttu-id="07453-153">개체는 선택 후 `TrackedTargetType`의 이동을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="07453-153">The object will follow the movement of the `TrackedTargetType` after selection.</span></span> <span data-ttu-id="07453-154">편집기에서 헤드 이동을 시뮬레이션하려면 WASD 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="07453-154">To simulate head movement in editor, press the WASD keys.</span></span> <span data-ttu-id="07453-155">마우스 오른쪽 단추를 클릭한 상태에서 헤드 회전을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-155">Change head rotation by clicking and holding the right mouse.</span></span>
    - <span data-ttu-id="07453-156">개체 배치를 중지하려면 다시 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-156">To stop placing the object, click again.</span></span>  <span data-ttu-id="07453-157">배치 중지 클릭을 위해 개체에 초점을 맞출 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07453-157">The object does not need to be in focus for the stop placement click.</span></span> <span data-ttu-id="07453-158">초점은 배치 프로세스를 시작하는 초기 클릭에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-158">Focus is only required for the initial click that starts the placement process.</span></span>

    <span data-ttu-id="07453-159">`TrackedTargetType`: 헤드(기본값)</span><span class="sxs-lookup"><span data-stu-id="07453-159">`TrackedTargetType`: Head (Default)</span></span> |  <span data-ttu-id="07453-160">`TrackedTargetType`: 컨트롤러 광선</span><span class="sxs-lookup"><span data-stu-id="07453-160">`TrackedTargetType`: Controller Ray</span></span>
    :-------------------------:|:-------------------------:
    ![탭하여 배치 입력 시뮬레이션 헤드 컨트롤 광선](../../images/solver/tap-to-place/TapToPlaceInputSimulationHead.gif)  |  ![탭하여 배치 입력 시뮬레이션 컨트롤러 광선 2](../../images/solver/tap-to-place/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a><span data-ttu-id="07453-163">탭하여 배치 코드 구성</span><span class="sxs-lookup"><span data-stu-id="07453-163">Tap to Place Code Configurability</span></span>

<span data-ttu-id="07453-164">탭하여 배치 개체 선택 타이밍은 클릭 이벤트를 요구하는 대신 `StartPlacement()` 및 `StopPlacement()`를 통해 제어할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07453-164">Tap to Place object selection timing can also be controlled via `StartPlacement()` and `StopPlacement()` instead of requiring a click event.</span></span> <span data-ttu-id="07453-165">이 기능은 테스트를 작성하는 데 유용하며 MRTK 입력 시스템을 사용하지 않고 편집기에 개체를 배치하는 대체 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-165">This capability is useful for writing tests and provides an alternative method to place an object in editor without using the MRTK Input System.</span></span>

1. <span data-ttu-id="07453-166">빈 게임 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="07453-166">Create an empty game object</span></span>
1. <span data-ttu-id="07453-167">다음 스크립트 예를 만들어 빈 게임 개체에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-167">Create and attach the following example script to the empty game object</span></span>

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

1. <span data-ttu-id="07453-168">재생 모드에서 *U 키* 를 눌러 큐브 배치를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="07453-168">In play mode, press the *U key* to start placing the cube</span></span>
1. <span data-ttu-id="07453-169">배치를 중지하려면 *I 키* 를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="07453-169">Press the *I key* to stop the placement</span></span>

## <a name="tap-to-place-example-scene"></a><span data-ttu-id="07453-170">탭하여 배치 장면 예</span><span class="sxs-lookup"><span data-stu-id="07453-170">Tap to Place Example Scene</span></span>

<span data-ttu-id="07453-171">탭하여 배치 장면 예는 각각 서로 다른 구성이 있는 4개의 배치 가능 개체로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07453-171">The Tap to Place example scene consists of 4 placeable objects, each with a different configuration.</span></span> <span data-ttu-id="07453-172">장면 예에는 계층 구조에서 기본적으로 사용하지 않도록 설정된 표면 배치 동작을 보여 주는 벽이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07453-172">The example scene contains walls to show the surface placement behavior that are disabled by default in the hierarchy.</span></span> <span data-ttu-id="07453-173">장면 예는 [릴리스 페이지](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)에 있는 Microsoft.MixedReality.Toolkit.Unity.Examples Unity 패키지에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07453-173">The example scene can be found in the Microsoft.MixedReality.Toolkit.Unity.Examples unity package found on the [Release Page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="07453-174">장면 위치는 *MRTK.Examples/Demos/Solvers/Scenes/TapToPlaceExample.unity* 입니다.</span><span class="sxs-lookup"><span data-stu-id="07453-174">The scene location is: *MRTK.Examples/Demos/Solvers/Scenes/TapToPlaceExample.unity*</span></span>

![탭하여 배치 예](../../images/solver/tap-to-place/TapToPlaceExampleScene.gif)

## <a name="see-also"></a><span data-ttu-id="07453-176">참조</span><span class="sxs-lookup"><span data-stu-id="07453-176">See also</span></span>

- [<span data-ttu-id="07453-177">해결기</span><span class="sxs-lookup"><span data-stu-id="07453-177">Solvers</span></span>](solver.md)
- [<span data-ttu-id="07453-178">공간 인식</span><span class="sxs-lookup"><span data-stu-id="07453-178">Spatial Awareness</span></span>](../../spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="07453-179">입력 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="07453-179">Input Simulation</span></span>](../../input-simulation/input-simulation-service.md)
- [<span data-ttu-id="07453-180">손 추적</span><span class="sxs-lookup"><span data-stu-id="07453-180">Hand Tracking</span></span>](../../input/hand-tracking.md)
- [<span data-ttu-id="07453-181">응시</span><span class="sxs-lookup"><span data-stu-id="07453-181">Gaze</span></span>](../../input/gaze.md)
