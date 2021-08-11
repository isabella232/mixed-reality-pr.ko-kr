---
title: 시선 추적 시선 공급자
description: MRTK의 아이 응시 공급자 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, mrtk, EyeTracking, EyeGaze,
ms.openlocfilehash: 9a62bdba0bc4bb2985e6c2ffc4e8e66a8f867681a5e51c9e5f235b29f3baaf50
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193195"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a>Unity 스크립트에서 눈 추적 데이터 액세스

이 문서에서는 MRTK 장면에서 눈 추적을 설정 하는 방법을 이해 하는 것으로 가정 합니다 ( [눈 추적을 사용 하려면 기본 MRTK 설정](eye-tracking-basic-setup.md)참조).
MonoBehaviour 스크립트에서 눈 추적 데이터에 쉽게 액세스할 수 있습니다. CoreServices를 사용 하면 됩니다. *EyeGazeProvider*.

## <a name="imixedrealityeyegazeprovider"></a>IMixedRealityEyeGazeProvider

MRTK의 아이 추적 구성은 인터페이스를 통해 구성 됩니다 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) . [CoreServices](eye-tracking-eye-gaze-provider.md) 를 사용 하면 런타임에 도구 키트에 등록 된 기본 응시 공급자 구현을 제공 합니다.
의 유용한 속성 `EyeGazeProvider` 은 아래에 설명 되어 있습니다.

- **IsEyeTrackingEnabled**: 사용자가 응시에 대해 눈동자 추적을 사용 하도록 선택한 경우 True입니다.

- **IsEyeCalibrationValid**: 사용자의 눈 추적 보정이 유효한 지 여부를 나타냅니다.
값이 눈 추적 시스템에서 데이터를 아직 받지 않은 경우 ' n u l l '을 반환 합니다.
사용자가 눈 추적 보정을 건너 뛰 었으 므로 잘못 된 것일 수 있습니다.

- **IsEyeTrackingEnabledAndValid**: 현재 눈동자 추적 데이터를 현재 응시에 사용 했는지 여부를 나타냅니다.

- **IsEyeTrackingDataValid**: 눈동자 추적 데이터를 사용할 수 있는 경우 True입니다.
제한 시간이 초과 되었거나 (사용자가 깜박이는 것을 강력 하 게 함) 하드웨어 또는 사용 권한이 추적 되지 않아서 사용할 수 없는 상태일 수 있습니다.
사용자가 아이 보정 인지 여부를 검색 하 고 적절 한 알림을 표시 하는 방법을 설명 하는 [누락 된 눈 보정 알림 샘플](eye-tracking-is-user-calibrated.md) 을 확인 하세요.

- **GazeOrigin**: 응시 레이의 원점입니다.
' IsEyeGazeValid '가 false 인 경우 *헤드* 응시 원본을 반환 합니다.

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

## <a name="see-also"></a>추가 정보

- [MRTK 눈 추적 개요](eye-tracking-main.md)
- [MRTK 눈동자 추적 설정](eye-tracking-basic-setup.md)
- [MRTK 눈동자 추적 보정](eye-tracking-is-user-calibrated.md)
- [HoloLens 2 아이 추적 설명서](/windows/mixed-reality/eye-tracking)