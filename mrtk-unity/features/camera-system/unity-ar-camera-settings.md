---
title: Unity AR 카메라 설정
description: MRTK에서 AR 카메라를 사용하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, AR 카메라,
ms.openlocfilehash: e1c032805bc4b733cfcc51e1ceac5096c73715cf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121201"
---
# <a name="unity-ar-camera-settings-provider"></a><span data-ttu-id="c03d0-104">Unity AR 카메라 설정 공급자</span><span class="sxs-lookup"><span data-stu-id="c03d0-104">Unity AR camera settings provider</span></span>

<span data-ttu-id="c03d0-105">Unity AR 카메라 설정 공급자는 Android 및 iOS 디바이스에서 혼합 현실 애플리케이션을 실행할 수 있도록 하는 실험적 MRTK 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-105">The Unity AR camera settings provider is an experimental MRTK component that enables mixed reality applications to run on Android and iOS devices.</span></span>

## <a name="unity-ar-camera-settings-provider-options"></a><span data-ttu-id="c03d0-106">Unity AR 카메라 설정 공급자 옵션</span><span class="sxs-lookup"><span data-stu-id="c03d0-106">Unity AR camera settings provider options</span></span>

![Unity AR 카메라 설정 구성](../images/camera-system/UnityArSettingsConfiguration.png)

<span data-ttu-id="c03d0-108">장면에 공급자를 추가하는 방법에 대한 가이드: [iOS 및 Android용 MRTK를 구성하는 방법](../../supported-devices/using-ar-foundation.md)</span><span class="sxs-lookup"><span data-stu-id="c03d0-108">For a guide on how to add the provider to your scene: [How to configure MRTK for iOS and Android](../../supported-devices/using-ar-foundation.md)</span></span>

### <a name="tracking-settings"></a><span data-ttu-id="c03d0-109">추적 설정</span><span class="sxs-lookup"><span data-stu-id="c03d0-109">Tracking settings</span></span>

<span data-ttu-id="c03d0-110">Unity AR 카메라 설정 공급자는 추적이 수행되는 방식에 대한 구성 옵션을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-110">The Unity AR camera settings provider allows configuration options for how tracking is performed.</span></span> <span data-ttu-id="c03d0-111">이러한 설정은 Unity AR 카메라 설정 공급자 구현에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-111">These settings are specific to the Unity AR camera settings provider implementation.</span></span>

<span data-ttu-id="c03d0-112">**자세 소스**</span><span class="sxs-lookup"><span data-stu-id="c03d0-112">**Pose Source**</span></span>

<span data-ttu-id="c03d0-113">자세 소스는 사용 가능한 유형의 증강 현실 추적 자세를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-113">The pose source defines the available types of augmented reality tracking poses.</span></span> <span data-ttu-id="c03d0-114">일반적으로 이러한 값은 애플리케이션이 실행되는 디바이스의 구성 요소에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-114">In general, these values map to a component of the device on which the application is running.</span></span>

<span data-ttu-id="c03d0-115">사용 가능한 옵션은 다음 표에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-115">The available options are described in the following table.</span></span>

| <span data-ttu-id="c03d0-116">옵션</span><span class="sxs-lookup"><span data-stu-id="c03d0-116">Option</span></span> | <span data-ttu-id="c03d0-117">Description</span><span class="sxs-lookup"><span data-stu-id="c03d0-117">Description</span></span> |
| --- | --- |
| <span data-ttu-id="c03d0-118">Center</span><span class="sxs-lookup"><span data-stu-id="c03d0-118">Center</span></span> | <span data-ttu-id="c03d0-119">헤드 탑재 디바이스의 중심 눈입니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-119">The center eye of a head mounted device.</span></span> |
| <span data-ttu-id="c03d0-120">색 카메라</span><span class="sxs-lookup"><span data-stu-id="c03d0-120">Color Camera</span></span> | <span data-ttu-id="c03d0-121">모바일 디바이스의 색 카메라입니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-121">The color camera of a mobile device.</span></span> |
| <span data-ttu-id="c03d0-122">Head</span><span class="sxs-lookup"><span data-stu-id="c03d0-122">Head</span></span> | <span data-ttu-id="c03d0-123">헤드 탑재 디바이스의 헤드 눈이며, 보통 중심 눈 위에 약간 위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-123">The head eye of a head mounted device, often slightly above the center eye.</span></span> |
| <span data-ttu-id="c03d0-124">왼쪽 눈</span><span class="sxs-lookup"><span data-stu-id="c03d0-124">Left Eye</span></span> | <span data-ttu-id="c03d0-125">헤드 탑재 디바이스의 왼쪽 눈입니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-125">The left eye of a head mounted device.</span></span> |
| <span data-ttu-id="c03d0-126">왼쪽 자세</span><span class="sxs-lookup"><span data-stu-id="c03d0-126">Left Pose</span></span> | <span data-ttu-id="c03d0-127">왼쪽 컨트롤러의 자세입니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-127">The left hand controller pose.</span></span> |
| <span data-ttu-id="c03d0-128">오른쪽 눈</span><span class="sxs-lookup"><span data-stu-id="c03d0-128">Right Eye</span></span> | <span data-ttu-id="c03d0-129">헤드 탑재 디바이스의 오른쪽 눈입니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-129">The right eye of a head mounted device.</span></span> |
| <span data-ttu-id="c03d0-130">오른쪽 자세</span><span class="sxs-lookup"><span data-stu-id="c03d0-130">Right Pose</span></span> | <span data-ttu-id="c03d0-131">오른쪽 컨트롤러의 자세입니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-131">The right hand controller pose.</span></span> |

<span data-ttu-id="c03d0-132">자세 원본의 기본값은 휴대폰 또는 태블릿과 같은 모바일 디바이스에서 투명하게 표시할 수 있도록 **색 카메라** 입니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-132">The default value for pose source is **Color Camera**, to enable a transparent display on mobile devices, such as a phone or tablet.</span></span>

<span data-ttu-id="c03d0-133">**추적 유형**</span><span class="sxs-lookup"><span data-stu-id="c03d0-133">**Tracking Type**</span></span>

<span data-ttu-id="c03d0-134">추적 유형은 추적에 사용할 자세 부분을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-134">The tracking type defines the portion(s) of the pose that will be used for tracking.</span></span>

<span data-ttu-id="c03d0-135">사용 가능한 옵션은 다음 표에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-135">The available options are described in the following table.</span></span>

| <span data-ttu-id="c03d0-136">옵션</span><span class="sxs-lookup"><span data-stu-id="c03d0-136">Option</span></span> | <span data-ttu-id="c03d0-137">Description</span><span class="sxs-lookup"><span data-stu-id="c03d0-137">Description</span></span> |
| --- | --- |
| <span data-ttu-id="c03d0-138">위치</span><span class="sxs-lookup"><span data-stu-id="c03d0-138">Position</span></span> | <span data-ttu-id="c03d0-139">디바이스의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-139">The position of the device.</span></span> |
| <span data-ttu-id="c03d0-140">회전</span><span class="sxs-lookup"><span data-stu-id="c03d0-140">Rotation</span></span> | <span data-ttu-id="c03d0-141">디바이스의 회전입니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-141">The rotation of the device.</span></span> |
| <span data-ttu-id="c03d0-142">회전 및 위치</span><span class="sxs-lookup"><span data-stu-id="c03d0-142">Rotation And Position</span></span> | <span data-ttu-id="c03d0-143">디바이스의 위치 및 회전입니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-143">The position and rotation of the device.</span></span> |

<span data-ttu-id="c03d0-144">추적 형식의 기본값은 **회전 및 위치** 이며, 가장 풍부한 추적 환경을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-144">The default value for tracking type is **Rotation And Position**, to enable the richest tracking experience.</span></span>

<span data-ttu-id="c03d0-145">**업데이트 유형**</span><span class="sxs-lookup"><span data-stu-id="c03d0-145">**Update Type**</span></span>

<span data-ttu-id="c03d0-146">업데이트 유형은 프레임 처리 중에 자세 데이터가 샘플링되는 지점을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-146">The update type defines at what points, during frame processing, the pose data will be sampled.</span></span>

<span data-ttu-id="c03d0-147">사용 가능한 옵션은 다음 표에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-147">The available options are described in the following table.</span></span>

| <span data-ttu-id="c03d0-148">옵션</span><span class="sxs-lookup"><span data-stu-id="c03d0-148">Option</span></span> | <span data-ttu-id="c03d0-149">Description</span><span class="sxs-lookup"><span data-stu-id="c03d0-149">Description</span></span> |
| --- | --- |
| <span data-ttu-id="c03d0-150">렌더링 전</span><span class="sxs-lookup"><span data-stu-id="c03d0-150">Before Render</span></span> | <span data-ttu-id="c03d0-151">렌더링 직전에.</span><span class="sxs-lookup"><span data-stu-id="c03d0-151">Just before rendering.</span></span> |
| <span data-ttu-id="c03d0-152">업데이트</span><span class="sxs-lookup"><span data-stu-id="c03d0-152">Update</span></span> | <span data-ttu-id="c03d0-153">프레임의 업데이트 단계 중.</span><span class="sxs-lookup"><span data-stu-id="c03d0-153">During the update phase of the frame.</span></span> |
| <span data-ttu-id="c03d0-154">렌더링 전 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="c03d0-154">Update And Before Render</span></span> | <span data-ttu-id="c03d0-155">업데이트 단계 중 및 렌더링 직전에</span><span class="sxs-lookup"><span data-stu-id="c03d0-155">During the update phase and just before rendering.</span></span> |

<span data-ttu-id="c03d0-156">추적 형식의 기본값은 **업데이트 및 렌더링 전** 으로, 가장 낮은 추적 대기 시간을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c03d0-156">The default value for tracking type is **Update And Before Render**, to enable the lowest tracking latency.</span></span>

## <a name="see-also"></a><span data-ttu-id="c03d0-157">참조</span><span class="sxs-lookup"><span data-stu-id="c03d0-157">See also</span></span>

- [<span data-ttu-id="c03d0-158">카메라 시스템 개요</span><span class="sxs-lookup"><span data-stu-id="c03d0-158">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="c03d0-159">카메라 설정 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="c03d0-159">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
