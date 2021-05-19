---
title: 시선 추적 시선 공급자
description: MRTK의 시선 응시 공급자에 대한 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, EyeTracking, EyeGaze,
ms.openlocfilehash: ef50a55d52a5dad9f424c8af8139565e02542b6c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144027"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a>Unity 스크립트에서 시선 추적 데이터에 액세스

이 문서에서는 MRTK 장면에서 시선 추적을 설정하는 방법을 이해하고 있다고 가정합니다(시선 [추적을 사용하기 위한 기본 MRTK 설정](eye-tracking-basic-setup.md)참조).
MonoBehaviour 스크립트에서 시선 추적 데이터에 액세스하는 것은 쉽습니다. *CoreServices.InputSystem.EyeGazeProvider* 를 사용하면됩니다.

## <a name="imixedrealityeyegazeprovider"></a>IMixedRealityEyeGazeProvider

MRTK의 시선 추적 구성은 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) 인터페이스를 통해 구성됩니다. [CoreServices.InputSystem.EyeGazeProvider를](eye-tracking-eye-gaze-provider.md) 사용하면 런타임에 도구 키트에 등록된 기본 응시 공급자 구현이 제공됩니다.
의 유용한 `EyeGazeProvider` 속성은 아래에 설명되어 있습니다.

- **IsEyeTrackingEnabled:** 사용자가 응시에 시선 추적을 사용하도록 선택한 경우 True입니다.

- **IsEyeCalibrationValid:** 사용자의 시선 추적 보정이 유효한지 여부를 나타냅니다.
값이 시선 추적 시스템에서 데이터를 아직 받지 못한 경우 'null'을 반환합니다.
사용자가 시선 추적 보정을 건너뛰므로 유효하지 않을 수 있습니다.

- **IsEyeTrackingEnabledAndValid:** 현재 시선 추적 데이터가 응시에 사용되었는지 여부를 나타냅니다.

- **IsEyeTrackingDataValid:** 시선 추적 데이터를 사용할 수 있는 경우 True입니다.
시간 제한 초과(사용자에게 깜박임) 또는 추적 하드웨어 또는 사용 권한 부족으로 인해 사용할 수 없을 수 있습니다.
사용자의 [시선 보정](eye-tracking-is-user-calibrated.md) 여부를 감지하고 적절한 알림을 표시하는 방법을 설명하는 누락된 눈 보정 알림 샘플을 확인하세요.

- **GazeOrigin:** 응시 광선의 원점입니다.
'IsEyeGazeValid'가 false인 경우 *헤드* 게이즈 원점이 반환됩니다.

- **GazeDirection**: 응시 레이의 방향입니다.
' IsEyeGazeValid '가 false 인 경우 *헤드* 응시 방향을 반환 합니다.

- **HitInfo**, **HitPosition**, **HitNormal** 등: 현재 대상의 gazed에 대 한 정보입니다.
이 false 인 경우에는 `IsEyeGazeValid` 사용자의 *헤드* 응시를 기반으로 합니다.

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a>CoreServices를 사용 하는 예제. EyeGazeProvider

[FollowEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze)의 예제는 다음과 같습니다.

- 사용자가 보고 있는 홀로그램의 위치를 가져옵니다.

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- 사용자가 현재 찾고 있는 고정 거리에서 시각적 자산 표시:

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a>참고 항목

- [MRTK 눈 추적 개요](eye-tracking-main.md)
- [MRTK 눈동자 추적 설정](eye-tracking-basic-setup.md)
- [MRTK 눈동자 추적 보정](eye-tracking-is-user-calibrated.md)
- [HoloLens 2 눈동자 추적 설명서](/windows/mixed-reality/eye-tracking)