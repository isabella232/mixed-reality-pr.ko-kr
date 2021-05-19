---
title: 눈 보정
description: MRTK에서 사용자 아이 보정을 설정 하는 방법
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, EyeTracking, 보정,
ms.openlocfilehash: d7ae9885b77798b44b3d63bb7f92283658e05411
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144002"
---
# <a name="eye-calibration"></a><span data-ttu-id="0526a-104">눈 보정</span><span class="sxs-lookup"><span data-stu-id="0526a-104">Eye calibration</span></span>

![눈 보정 알림에서 스크린샷](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a><span data-ttu-id="0526a-106">개요</span><span class="sxs-lookup"><span data-stu-id="0526a-106">Overview</span></span>

<span data-ttu-id="0526a-107">눈동자 추적이 앱 경험의 기본 부분인 경우 사용자의 눈 보정이 유효한 지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-107">If eye tracking is a fundamental part of your app experience, one may wish to ensure that the user's eye calibration is valid.</span></span>
<span data-ttu-id="0526a-108">잘못 된 주된 이유는 사용자가 장치에 배치할 때 눈 추적 보정을 건너뛰도록 선택 했기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-108">The main reason for it to be invalid is that the user has chosen to skip the eye tracking calibration when putting on the device.</span></span>

<span data-ttu-id="0526a-109">이 페이지에서는 다음 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-109">This page covers the following:</span></span>

- <span data-ttu-id="0526a-110">사용자가 아이 보정 임을 검색 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-110">Describes how to detect that a user is eye calibrated</span></span>
- <span data-ttu-id="0526a-111">사용자에 게 시각 보정을 수행 하도록 지시 하는 사용자 알림을 트리거하는 방법에 대 한 샘플을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-111">Provides a sample for how to trigger a user notification to instruct the user to go through the eye calibration</span></span>
  - <span data-ttu-id="0526a-112">눈 보정이 올바르면 자동으로 알림 해제</span><span class="sxs-lookup"><span data-stu-id="0526a-112">Automatically dismiss notification if eye calibration becomes valid</span></span>
  - <span data-ttu-id="0526a-113">사용자가 보정 없이 계속 하도록 선택 하면 수동으로 알림 해제</span><span class="sxs-lookup"><span data-stu-id="0526a-113">Manually dismiss notification if user chooses to continue without calibration</span></span>

### <a name="how-to-detect-the-eye-calibration-state"></a><span data-ttu-id="0526a-114">눈 보정 상태를 검색 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0526a-114">How to detect the eye calibration state</span></span>

<span data-ttu-id="0526a-115">MRTK의 아이 추적 구성은 인터페이스를 통해 구성 됩니다 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) .</span><span class="sxs-lookup"><span data-stu-id="0526a-115">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span>

<span data-ttu-id="0526a-116">[CoreServices](eye-tracking-eye-gaze-provider.md) 를 사용 하면 런타임에 도구 키트에 등록 된 기본 응시 공급자 구현을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-116">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span> <span data-ttu-id="0526a-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` 는 `bool?` 눈 트래커의 정보를 아직 사용할 수 없는 경우 null 인을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` returns a `bool?` which is null if no information from the eye tracker is available yet.</span></span>
<span data-ttu-id="0526a-118">데이터가 수신 되 면 true 또는 false를 반환 하 여 사용자의 눈 추적 보정이 유효 하거나 유효 하지 않음을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-118">Once data has been received, it will either return true or false to indicate that the user's eye tracking calibration is valid or invalid.</span></span>

### <a name="sample-eye-calibration-notification---step-by-step"></a><span data-ttu-id="0526a-119">샘플 눈 보정 알림-단계별</span><span class="sxs-lookup"><span data-stu-id="0526a-119">Sample eye calibration notification - step-by-step</span></span>

1. <span data-ttu-id="0526a-120">MRTK 눈동자 추적 예제 패키지 열기 (자산/m a d/예제/데모/EyeTracking)</span><span class="sxs-lookup"><span data-stu-id="0526a-120">Open the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking)</span></span>

2. <span data-ttu-id="0526a-121">Load _EyeTrackingDemo-00-rootscene. unity_ 장면</span><span class="sxs-lookup"><span data-stu-id="0526a-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span></span>

3. <span data-ttu-id="0526a-122">_EyeCalibrationChecker_ 확인:</span><span class="sxs-lookup"><span data-stu-id="0526a-122">Check out _EyeCalibrationChecker_:</span></span>
   - <span data-ttu-id="0526a-123">이 장면에는 현재 사용자가 *_EyeCalibrationChecker_ 게임 개체* 에서 보정되었는지 여부를 감지하는 샘플이 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-123">In this scene, we have already a sample for detecting whether the current user is calibrated under the *_EyeCalibrationChecker_ game object*.</span></span>
<span data-ttu-id="0526a-124">단순히 몇 가지 텍스트 메시의 부모이며 알림을 혼합하기 위한 몇 가지 추가 트리거가 있습니다. 여기에는 정품 인증 시 크기 및 불투명도를 느리게 늘리는 것이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-124">It simply parents a few text meshes and has some additional triggers for blending the notification in and out. This includes slowly increasing its size and opacity on activation.</span></span>
<span data-ttu-id="0526a-125">알림이 해제되면 크기가 느려지고 페이드 아웃됩니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-125">Once the notification is dismissed, it will slowly decrease its size and fade out.</span></span>

   - <span data-ttu-id="0526a-126">*_EyeCalibrationChecker_ 게임 개체에* 연결된 은 두 개의 Unity 이벤트를 노출하는 [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-126">Attached to the *_EyeCalibrationChecker_ game object* is the [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) script which exposes two Unity Events:</span></span>
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - <span data-ttu-id="0526a-127">이러한 이벤트는 보정 상태가 변경될 때만 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-127">These events will only trigger if the calibration status changes.</span></span> <span data-ttu-id="0526a-128">따라서 사용자가 알림을 해제하도록 선택하면 알림이 다시 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-128">Hence, if a user chooses to dismiss the notification, the notification will not show up again until</span></span>
      - <span data-ttu-id="0526a-129">앱이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-129">The app gets restarted</span></span>
      - <span data-ttu-id="0526a-130">유효한 사용자가 검색된 다음, 계산되지 않은 새 사용자가 디바이스를 켜고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-130">A valid user has been detected and then a new uncalibrated user has put the device on</span></span>

   - <span data-ttu-id="0526a-131">애니메이션 및 이벤트가 올바르게 트리거되는지 여부를 테스트하기 위해 EyeCalibrationChecker 스크립트에는 `bool editorTestUserIsCalibrated` 플래그가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-131">For testing whether the animations and events are triggered correctly, the EyeCalibrationChecker script possesses a `bool editorTestUserIsCalibrated` flag.</span></span> <span data-ttu-id="0526a-132">예를 들어 Unity 편집기에서 실행하는 경우 다음을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-132">For example, when running in the Unity Editor, one can test:</span></span>
      1. <span data-ttu-id="0526a-133">보정 상태가 true에서 false로 변경되면 알림이 자동으로 팝업되는지 여부</span><span class="sxs-lookup"><span data-stu-id="0526a-133">Whether the notification automatically pops up once the calibration status changes from true to false</span></span>
      1. <span data-ttu-id="0526a-134">상태가 false에서 true로 변경되면 알림을 다시 자동으로 해제할지 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="0526a-134">Whether it automatically dismisses the notification again once the status changes from false to true.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0526a-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0526a-135">See also</span></span>

- [<span data-ttu-id="0526a-136">MRTK 시선 추적 개요</span><span class="sxs-lookup"><span data-stu-id="0526a-136">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="0526a-137">MRTK 시선 추적 설정</span><span class="sxs-lookup"><span data-stu-id="0526a-137">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="0526a-138">코드를 통한 MRTK 시선 추적</span><span class="sxs-lookup"><span data-stu-id="0526a-138">MRTK Eye Tracking via Code</span></span>](eye-tracking-eye-gaze-provider.md)
- [<span data-ttu-id="0526a-139">HoloLens 2 시선 추적 설명서</span><span class="sxs-lookup"><span data-stu-id="0526a-139">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)