---
title: UnityArCameraSettings
description: MRTK에서 AR 카메라를 사용하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, AR 카메라,
ms.openlocfilehash: 15aacae4cb543a3a94660ef1ab057ad0febcb715
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850419"
---
# <a name="unity-ar-camera-settings-provider"></a><span data-ttu-id="ef217-104">Unity AR 카메라 설정 공급자</span><span class="sxs-lookup"><span data-stu-id="ef217-104">Unity AR camera settings provider</span></span>

<span data-ttu-id="ef217-105">Unity AR 카메라 설정 공급자는 Android 및 iOS 디바이스에서 혼합 현실 애플리케이션을 실행할 수 있도록 하는 실험적 MRTK 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-105">The Unity AR camera settings provider is an experimental MRTK component that enables mixed reality applications to run on Android and iOS devices.</span></span>

## <a name="unity-ar-camera-settings-provider-options"></a><span data-ttu-id="ef217-106">Unity AR 카메라 설정 공급자 옵션</span><span class="sxs-lookup"><span data-stu-id="ef217-106">Unity AR camera settings provider options</span></span>

![Unity AR 카메라 설정 구성](../images/camera-system/UnityArSettingsConfiguration.png)

<span data-ttu-id="ef217-108">장면에 공급자를 추가하는 방법에 대한 가이드: [iOS 및 Android용 MRTK를 구성하는 방법](../../supported-devices/using-ar-foundation.md)</span><span class="sxs-lookup"><span data-stu-id="ef217-108">For a guide on how to add the provider to your scene: [How to configure MRTK for iOS and Android](../../supported-devices/using-ar-foundation.md)</span></span>

### <a name="tracking-settings"></a><span data-ttu-id="ef217-109">추적 설정</span><span class="sxs-lookup"><span data-stu-id="ef217-109">Tracking settings</span></span>

<span data-ttu-id="ef217-110">Unity AR 카메라 설정 공급자는 추적을 수행하는 방법에 대한 구성 옵션을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-110">The Unity AR camera settings provider allows configuration options for how tracking is performed.</span></span> <span data-ttu-id="ef217-111">이러한 설정은 Unity AR 카메라 설정 공급자 구현에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-111">These settings are specific to the Unity AR camera settings provider implementation.</span></span>

<span data-ttu-id="ef217-112">**자세 소스**</span><span class="sxs-lookup"><span data-stu-id="ef217-112">**Pose Source**</span></span>

<span data-ttu-id="ef217-113">자세 소스는 사용 가능한 유형의 증강 현실 추적 자세를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-113">The pose source defines the available types of augmented reality tracking poses.</span></span> <span data-ttu-id="ef217-114">일반적으로 이러한 값은 애플리케이션이 실행되는 디바이스의 구성 요소에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-114">In general, these values map to a component of the device on which the application is running.</span></span>

<span data-ttu-id="ef217-115">사용 가능한 옵션은 다음 표에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-115">The available options are described in the following table.</span></span>

| <span data-ttu-id="ef217-116">옵션</span><span class="sxs-lookup"><span data-stu-id="ef217-116">Option</span></span> | <span data-ttu-id="ef217-117">Description</span><span class="sxs-lookup"><span data-stu-id="ef217-117">Description</span></span> |
| --- | --- |
| <span data-ttu-id="ef217-118">Center</span><span class="sxs-lookup"><span data-stu-id="ef217-118">Center</span></span> | <span data-ttu-id="ef217-119">헤드 탑재 디바이스의 중심 눈입니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-119">The center eye of a head mounted device.</span></span> |
| <span data-ttu-id="ef217-120">색 카메라</span><span class="sxs-lookup"><span data-stu-id="ef217-120">Color Camera</span></span> | <span data-ttu-id="ef217-121">모바일 디바이스의 색 카메라입니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-121">The color camera of a mobile device.</span></span> |
| <span data-ttu-id="ef217-122">Head</span><span class="sxs-lookup"><span data-stu-id="ef217-122">Head</span></span> | <span data-ttu-id="ef217-123">헤드 탑재 디바이스의 머리 눈은 보통 가운데 눈 위에 약간 늘고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-123">The head eye of a head mounted device, often slightly above the center eye.</span></span> |
| <span data-ttu-id="ef217-124">왼쪽 눈</span><span class="sxs-lookup"><span data-stu-id="ef217-124">Left Eye</span></span> | <span data-ttu-id="ef217-125">헤드 탑재 장치의 왼쪽 눈입니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-125">The left eye of a head mounted device.</span></span> |
| <span data-ttu-id="ef217-126">왼쪽 포즈</span><span class="sxs-lookup"><span data-stu-id="ef217-126">Left Pose</span></span> | <span data-ttu-id="ef217-127">왼쪽 컨트롤러는입니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-127">The left hand controller pose.</span></span> |
| <span data-ttu-id="ef217-128">올바른 눈</span><span class="sxs-lookup"><span data-stu-id="ef217-128">Right Eye</span></span> | <span data-ttu-id="ef217-129">헤드 탑재 장치의 올바른 눈입니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-129">The right eye of a head mounted device.</span></span> |
| <span data-ttu-id="ef217-130">올바른 포즈</span><span class="sxs-lookup"><span data-stu-id="ef217-130">Right Pose</span></span> | <span data-ttu-id="ef217-131">오른쪽 컨트롤러는이를 야기 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-131">The right hand controller pose.</span></span> |

<span data-ttu-id="ef217-132">포즈 원본의 기본값은 휴대폰 이나 태블릿과 같은 모바일 장치에서 투명 한 디스플레이를 사용 하도록 설정 하기 위한 **컬러 카메라** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-132">The default value for pose source is **Color Camera**, to enable a transparent display on mobile devices, such as a phone or tablet.</span></span>

<span data-ttu-id="ef217-133">**추적 유형**</span><span class="sxs-lookup"><span data-stu-id="ef217-133">**Tracking Type**</span></span>

<span data-ttu-id="ef217-134">추적 유형은 추적에 사용 되는 포즈의 부분을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-134">The tracking type defines the portion(s) of the pose that will be used for tracking.</span></span>

<span data-ttu-id="ef217-135">다음 표에서는 사용 가능한 옵션에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-135">The available options are described in the following table.</span></span>

| <span data-ttu-id="ef217-136">옵션</span><span class="sxs-lookup"><span data-stu-id="ef217-136">Option</span></span> | <span data-ttu-id="ef217-137">Description</span><span class="sxs-lookup"><span data-stu-id="ef217-137">Description</span></span> |
| --- | --- |
| <span data-ttu-id="ef217-138">위치</span><span class="sxs-lookup"><span data-stu-id="ef217-138">Position</span></span> | <span data-ttu-id="ef217-139">장치의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-139">The position of the device.</span></span> |
| <span data-ttu-id="ef217-140">회전</span><span class="sxs-lookup"><span data-stu-id="ef217-140">Rotation</span></span> | <span data-ttu-id="ef217-141">장치의 회전입니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-141">The rotation of the device.</span></span> |
| <span data-ttu-id="ef217-142">회전 및 위치</span><span class="sxs-lookup"><span data-stu-id="ef217-142">Rotation And Position</span></span> | <span data-ttu-id="ef217-143">장치의 위치 및 회전입니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-143">The position and rotation of the device.</span></span> |

<span data-ttu-id="ef217-144">가장 다양 한 추적 환경을 사용 하도록 설정 하려면 추적 유형의 기본값은 **회전 및 위치** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-144">The default value for tracking type is **Rotation And Position**, to enable the richest tracking experience.</span></span>

<span data-ttu-id="ef217-145">**업데이트 유형**</span><span class="sxs-lookup"><span data-stu-id="ef217-145">**Update Type**</span></span>

<span data-ttu-id="ef217-146">업데이트 유형은 프레임 처리 중에 포즈 데이터가 샘플링 되는 시점을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-146">The update type defines at what points, during frame processing, the pose data will be sampled.</span></span>

<span data-ttu-id="ef217-147">다음 표에서는 사용 가능한 옵션에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-147">The available options are described in the following table.</span></span>

| <span data-ttu-id="ef217-148">옵션</span><span class="sxs-lookup"><span data-stu-id="ef217-148">Option</span></span> | <span data-ttu-id="ef217-149">Description</span><span class="sxs-lookup"><span data-stu-id="ef217-149">Description</span></span> |
| --- | --- |
| <span data-ttu-id="ef217-150">렌더링 전</span><span class="sxs-lookup"><span data-stu-id="ef217-150">Before Render</span></span> | <span data-ttu-id="ef217-151">렌더링 직전.</span><span class="sxs-lookup"><span data-stu-id="ef217-151">Just before rendering.</span></span> |
| <span data-ttu-id="ef217-152">업데이트</span><span class="sxs-lookup"><span data-stu-id="ef217-152">Update</span></span> | <span data-ttu-id="ef217-153">프레임의 업데이트 단계 중.</span><span class="sxs-lookup"><span data-stu-id="ef217-153">During the update phase of the frame.</span></span> |
| <span data-ttu-id="ef217-154">렌더링 전 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="ef217-154">Update And Before Render</span></span> | <span data-ttu-id="ef217-155">업데이트 단계 중 및 렌더링 직전에</span><span class="sxs-lookup"><span data-stu-id="ef217-155">During the update phase and just before rendering.</span></span> |

<span data-ttu-id="ef217-156">추적 형식의 기본값은 **업데이트 및 렌더링 전** 으로, 가장 낮은 추적 대기 시간을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef217-156">The default value for tracking type is **Update And Before Render**, to enable the lowest tracking latency.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef217-157">추가 정보</span><span class="sxs-lookup"><span data-stu-id="ef217-157">See also</span></span>

- [<span data-ttu-id="ef217-158">카메라 시스템 개요</span><span class="sxs-lookup"><span data-stu-id="ef217-158">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="ef217-159">카메라 설정 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="ef217-159">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
