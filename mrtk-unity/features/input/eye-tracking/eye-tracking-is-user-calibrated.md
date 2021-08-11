---
title: 눈 보정
description: MRTK에서 사용자 아이 보정을 설정 하는 방법
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, EyeTracking, 보정,
ms.openlocfilehash: 02b173bbc7a6bf410d3521b37660f292b8e3340de6b1a98007fdbc200f26bc49
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199774"
---
# <a name="eye-calibration"></a>눈 보정

![눈 보정 알림에서 스크린샷](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a>개요

눈동자 추적이 앱 경험의 기본 부분인 경우 사용자의 눈 보정이 유효한 지 확인 하는 것이 좋습니다.
잘못 된 주된 이유는 사용자가 장치에 배치할 때 눈 추적 보정을 건너뛰도록 선택 했기 때문입니다.

이 페이지에서는 다음 내용을 다룹니다.

- 사용자가 아이 보정 임을 검색 하는 방법을 설명 합니다.
- 사용자에 게 시각 보정을 수행 하도록 지시 하는 사용자 알림을 트리거하는 방법에 대 한 샘플을 제공 합니다.
  - 눈 보정이 올바르면 자동으로 알림 해제
  - 사용자가 보정 없이 계속 하도록 선택 하면 수동으로 알림 해제

### <a name="how-to-detect-the-eye-calibration-state"></a>눈 보정 상태를 검색 하는 방법

MRTK의 아이 추적 구성은 인터페이스를 통해 구성 됩니다 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) .

[CoreServices](eye-tracking-eye-gaze-provider.md) 를 사용 하면 런타임에 도구 키트에 등록 된 기본 응시 공급자 구현을 제공 합니다. `IMixedRealityEyeGazeProvider.IsEyeGazeValid` 는 `bool?` 눈 트래커의 정보를 아직 사용할 수 없는 경우 null 인을 반환 합니다.
데이터가 수신 되 면 true 또는 false를 반환 하 여 사용자의 눈 추적 보정이 유효 하거나 유효 하지 않음을 표시 합니다.

### <a name="sample-eye-calibration-notification---step-by-step"></a>샘플 눈 보정 알림-단계별

1. MRTK 눈동자 추적 예제 패키지 열기 (자산/m a d/예제/데모/EyeTracking)

2. Load _EyeTrackingDemo-00-rootscene. unity_ 장면

3. _EyeCalibrationChecker_ 확인:
   - 이 장면에는 현재 사용자가 *_EyeCalibrationChecker_ game 개체* 에서 보정 되는지 여부를 검색 하는 샘플이 이미 있습니다.
단순히 몇 개의 텍스트 메시를 부모로 하 고 알림을 혼합 하 고 추가 하기 위한 몇 가지 추가 트리거를 포함 합니다. 여기에는 정품 인증에 대 한 크기 및 불투명도가 천천히 늘어납니다.
알림이 해제 되 면 천천히 크기가 줄어들고 페이드 아웃 됩니다.

   - *_EyeCalibrationChecker_ game 개체* 에 연결 되는 [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) 스크립트는 두 Unity 이벤트를 노출 합니다.
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - 이러한 이벤트는 보정 상태가 변경 되는 경우에만 트리거됩니다. 따라서 사용자가 알림을 해제 하도록 선택 하면 알림이 다시 표시 되지 않습니다.
      - 앱이 다시 시작 됩니다.
      - 유효한 사용자가 검색 된 후 새 uncalibrated 사용자가 장치를에 배치 했습니다.

   - 애니메이션 및 이벤트가 올바르게 트리거되는지 여부를 테스트 하기 위해 EyeCalibrationChecker 스크립트는 플래그를 소유 합니다 `bool editorTestUserIsCalibrated` . 예를 들어 Unity 편집기에서 실행 되는 경우 다음을 테스트할 수 있습니다.
      1. 보정 상태가 true에서 false로 변경 되 면 알림이 자동으로 표시 되는지 여부
      1. 상태가 false에서 true로 변경 되 면 자동으로 알림을 해제 하는지 여부를 지정 합니다.

```c#
    private bool? prevCalibrationStatus = null;
    ...

   void Update()
   {
      // Get the latest calibration state from the EyeGazeProvider
      bool? calibrationStatus = CoreServices.InputSystem?.EyeGazeProvider?.IsEyeCalibrationValid;

      ...

      if (calibrationStatus != null)
      {
         if (prevCalibrationStatus != calibrationStatus)
         {
            if (calibrationStatus == false)
            {
               OnNoEyeCalibrationDetected.Invoke();
            }
         else
         {
            OnEyeCalibrationDetected.Invoke();
         }

         prevCalibrationStatus = calibrationStatus;
      }
   }
```

## <a name="see-also"></a>추가 정보

- [MRTK 눈 추적 개요](eye-tracking-main.md)
- [MRTK 눈동자 추적 설정](eye-tracking-basic-setup.md)
- [코드를 통한 MRTK 눈동자 추적](eye-tracking-eye-gaze-provider.md)
- [HoloLens 2 아이 추적 설명서](/windows/mixed-reality/eye-tracking)
