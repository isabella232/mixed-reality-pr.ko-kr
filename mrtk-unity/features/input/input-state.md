---
title: 입력 상태
description: MRTK의 입력 상태에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, InputState,
ms.openlocfilehash: 4c1bd115c63e25decf73c082546e75b0f276a7ef
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145253"
---
# <a name="accessing-input-state-in-mrtk"></a>MRTK의 입력 상태에 액세스

입력 원본에 연결된 컨트롤러를 반복해서 MRTK의 모든 입력 상태를 직접 쿼리할 수 있습니다. 또한 MRTK는 눈, 손, 머리 및 모션 컨트롤러의 위치와 회전에 액세스하기 위한 편리한 방법을 제공합니다.

컨트롤러를 통해, 그리고 클래스를 사용하여 입력을 쿼리하는 예제는 InputDataExample 장면을 [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) 참조하세요.

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a>예: MRTK의 액세스 위치, 머리 회전, 손, 눈

MRTK의 [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) 클래스는 손 광선, 헤드 광선, 시선 응시 광선 및 모션 컨트롤러 광선에 액세스하기 위한 편리한 메서드를 제공합니다.

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

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a>예: 장면에서 활성 상태인 모든 6DOF 컨트롤러의 액세스 위치, 회전

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

## <a name="see-also"></a>참고 항목

- [InputEvents](input-events.md)
- [포인터](pointers.md)
- [HandTracking](hand-tracking.md)
