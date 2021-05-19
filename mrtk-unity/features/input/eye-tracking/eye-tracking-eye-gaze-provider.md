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
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a><span data-ttu-id="ef69f-104">Unity 스크립트에서 시선 추적 데이터에 액세스</span><span class="sxs-lookup"><span data-stu-id="ef69f-104">Accessing eye tracking data in your Unity script</span></span>

<span data-ttu-id="ef69f-105">이 문서에서는 MRTK 장면에서 시선 추적을 설정하는 방법을 이해하고 있다고 가정합니다(시선 [추적을 사용하기 위한 기본 MRTK 설정](eye-tracking-basic-setup.md)참조).</span><span class="sxs-lookup"><span data-stu-id="ef69f-105">This article assumes one has understanding for setting up eye tracking in an MRTK scene (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)).</span></span>
<span data-ttu-id="ef69f-106">MonoBehaviour 스크립트에서 시선 추적 데이터에 액세스하는 것은 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-106">Accessing eye tracking data in a MonoBehaviour script is easy!</span></span> <span data-ttu-id="ef69f-107">*CoreServices.InputSystem.EyeGazeProvider* 를 사용하면됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-107">Simply use *CoreServices.InputSystem.EyeGazeProvider*.</span></span>

## <a name="imixedrealityeyegazeprovider"></a><span data-ttu-id="ef69f-108">IMixedRealityEyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="ef69f-108">IMixedRealityEyeGazeProvider</span></span>

<span data-ttu-id="ef69f-109">MRTK의 시선 추적 구성은 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) 인터페이스를 통해 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-109">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span> <span data-ttu-id="ef69f-110">[CoreServices.InputSystem.EyeGazeProvider를](eye-tracking-eye-gaze-provider.md) 사용하면 런타임에 도구 키트에 등록된 기본 응시 공급자 구현이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-110">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span>
<span data-ttu-id="ef69f-111">의 유용한 `EyeGazeProvider` 속성은 아래에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-111">Useful properties of the `EyeGazeProvider` is outlined below.</span></span>

- <span data-ttu-id="ef69f-112">**IsEyeTrackingEnabled:** 사용자가 응시에 시선 추적을 사용하도록 선택한 경우 True입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-112">**IsEyeTrackingEnabled**: True if user has selected to use eye tracking for gaze.</span></span>

- <span data-ttu-id="ef69f-113">**IsEyeCalibrationValid:** 사용자의 시선 추적 보정이 유효한지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-113">**IsEyeCalibrationValid**: Indicates whether the user's eye tracking calibration is valid or not.</span></span>
<span data-ttu-id="ef69f-114">값이 시선 추적 시스템에서 데이터를 아직 받지 못한 경우 'null'을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-114">It returns 'null', if the value has not yet received data from the eye tracking system.</span></span>
<span data-ttu-id="ef69f-115">사용자가 시선 추적 보정을 건너뛰므로 유효하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-115">It may be invalid, because the user skipped the eye tracking calibration.</span></span>

- <span data-ttu-id="ef69f-116">**IsEyeTrackingEnabledAndValid:** 현재 시선 추적 데이터가 응시에 사용되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-116">**IsEyeTrackingEnabledAndValid**: Indicates whether the current eye tracking data is currently been used for gaze.</span></span>

- <span data-ttu-id="ef69f-117">**IsEyeTrackingDataValid:** 시선 추적 데이터를 사용할 수 있는 경우 True입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-117">**IsEyeTrackingDataValid**: True if eye tracking data is available.</span></span>
<span data-ttu-id="ef69f-118">시간 제한 초과(사용자에게 깜박임) 또는 추적 하드웨어 또는 사용 권한 부족으로 인해 사용할 수 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-118">It may be unavailable due to exceeded timeout (should be robust to the user blinking though) or lack of tracking hardware or permissions.</span></span>
<span data-ttu-id="ef69f-119">사용자의 [시선 보정](eye-tracking-is-user-calibrated.md) 여부를 감지하고 적절한 알림을 표시하는 방법을 설명하는 누락된 눈 보정 알림 샘플을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="ef69f-119">Check out our [Missing eye calibration notification sample](eye-tracking-is-user-calibrated.md) that explains how to detect whether a user is eye calibrated and to show an appropriate notification.</span></span>

- <span data-ttu-id="ef69f-120">**GazeOrigin:** 응시 광선의 원점입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-120">**GazeOrigin**: Origin of the gaze ray.</span></span>
<span data-ttu-id="ef69f-121">'IsEyeGazeValid'가 false인 경우 *헤드* 게이즈 원점이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-121">Please note that this will return the *head* gaze origin if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="ef69f-122">**GazeDirection**: 응시 레이의 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-122">**GazeDirection**: Direction of the gaze ray.</span></span>
<span data-ttu-id="ef69f-123">' IsEyeGazeValid '가 false 인 경우 *헤드* 응시 방향을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-123">This will return the *head* gaze direction if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="ef69f-124">**HitInfo**, **HitPosition**, **HitNormal** 등: 현재 대상의 gazed에 대 한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-124">**HitInfo**, **HitPosition**, **HitNormal**, etc.: Information about the currently gazed at target.</span></span>
<span data-ttu-id="ef69f-125">이 false 인 경우에는 `IsEyeGazeValid` 사용자의 *헤드* 응시를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-125">Again, if `IsEyeGazeValid` is false, this will be based on the user's *head* gaze.</span></span>

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a><span data-ttu-id="ef69f-126">CoreServices를 사용 하는 예제. EyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="ef69f-126">Examples for using CoreServices.InputSystem.EyeGazeProvider</span></span>

<span data-ttu-id="ef69f-127">[FollowEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze)의 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-127">Here is an example from the [FollowEyeGaze.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span></span>

- <span data-ttu-id="ef69f-128">사용자가 보고 있는 홀로그램의 위치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef69f-128">Get the point of a hologram that the user is looking at:</span></span>

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- <span data-ttu-id="ef69f-129">사용자가 현재 찾고 있는 고정 거리에서 시각적 자산 표시:</span><span class="sxs-lookup"><span data-stu-id="ef69f-129">Showing a visual asset at a fixed distance from where the user is currently looking:</span></span>

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a><span data-ttu-id="ef69f-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef69f-130">See also</span></span>

- [<span data-ttu-id="ef69f-131">MRTK 눈 추적 개요</span><span class="sxs-lookup"><span data-stu-id="ef69f-131">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="ef69f-132">MRTK 눈동자 추적 설정</span><span class="sxs-lookup"><span data-stu-id="ef69f-132">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="ef69f-133">MRTK 눈동자 추적 보정</span><span class="sxs-lookup"><span data-stu-id="ef69f-133">MRTK Eye Tracking Calibration</span></span>](eye-tracking-is-user-calibrated.md)
- [<span data-ttu-id="ef69f-134">HoloLens 2 눈동자 추적 설명서</span><span class="sxs-lookup"><span data-stu-id="ef69f-134">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)