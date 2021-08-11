---
title: 입력 상태
description: MRTK의 입력 상태에 대 한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, mrtk, inputstate,
ms.openlocfilehash: 7d5e008ae3e43d227b90a563dd74e65a89527bd7ddf1720e26577042ce0d545f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228363"
---
# <a name="accessing-input-state-in-mrtk"></a>MRTK의 입력 상태 액세스

입력 소스에 연결 된 컨트롤러를 반복 하 여 MRTK의 모든 입력 상태를 직접 쿼리할 수 있습니다. 또한 MRTK는 눈, 손, 헤드 및 동작 컨트롤러의 위치와 회전에 액세스 하기 위한 편리한 방법을 제공 합니다.

컨트롤러를 반복 하 고 클래스를 사용 하 여 입력을 쿼리 하는 예제는 InputDataExample 장면을 참조 하세요 [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) .

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a>예: 액세스 위치, 헤드, 손 방향 회전, MRTK의 눈

MRTK의 [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) 클래스는 손 모양, 헤드 광선, 눈 응시 레이 레이 및 모션 컨트롤러 광선에 액세스 하기 위한 편리한 메서드를 제공 합니다.

```c#
// Get the head ray
var headRay = InputRayUtils.GetHeadGazeRay();

// Get the right hand ray
Ray rightHandRay;
if(InputRayUtils.TryGetHandRay(Handedness.right, rightHandRay))
{
    // Right hand ray is available
}
else
{
    // Right hand ray is not available
}
```

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a>예: 액세스 위치, 장면에서 활성화 된 모든 6DOF 컨트롤러의 회전

```c#
foreach(var controller in CoreServices.InputSystem.DetectedControllers)
{
    // Interactions for a controller is the list of inputs that this controller exposes
    foreach(MixedRealityInteractionMapping inputMapping in controller.Interactions)
    {
        // 6DOF controllers support the "SpatialPointer" type (pointing direction)
        // or "GripPointer" type (direction of the 6DOF controller)
        if (inputMapping.InputType == DeviceInputType.SpatialPointer)
        {
            Debug.Log("spatial pointer PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial pointer RotationData: " + inputMapping.RotationData);
        }

        if (inputMapping.InputType == DeviceInputType.SpatialGrip)
        {
            Debug.Log("spatial grip PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial grip RotationData: " + inputMapping.RotationData);
        }
    }
}
```

## <a name="see-also"></a>추가 정보

- [InputEvents](input-events.md)
- [포인터](pointers.md)
- [수동 추적](hand-tracking.md)
