---
title: Unreal에서 프로젝트 업그레이드
description: Unreal 프로젝트의 버전 업그레이드 단계 및 사용되지 않는 API에 대한 개요입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 설명서, 가이드, 기능, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 이식, 업그레이드
ms.openlocfilehash: efad783ee199ed42c7355917a180855b3ec4f11b
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355766"
---
# <a name="upgrading-projects-in-unreal"></a><span data-ttu-id="361c2-104">Unreal에서 프로젝트 업그레이드</span><span class="sxs-lookup"><span data-stu-id="361c2-104">Upgrading projects in Unreal</span></span>

<span data-ttu-id="361c2-105">새 버전의 Unreal로 업데이트할 때 청사진을 컴파일하거나 프로젝트를 패키징하면 사용되지 않는 함수가 경고로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-105">When updating to a new version of Unreal, deprecated functions will show up as warnings when compiling the blueprint or packaging the project.</span></span>  <span data-ttu-id="361c2-106">기존 함수를 대체하는 새 함수가 추가되면 기존 함수는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-106">Functions are deprecated when a new function has been added that should be used instead.</span></span> 

## <a name="426-upgrades"></a><span data-ttu-id="361c2-107">4.26 업그레이드</span><span class="sxs-lookup"><span data-stu-id="361c2-107">4.26 upgrades</span></span>
 
<span data-ttu-id="361c2-108">4\.26에서는 공통 인터페이스를 추가하고 애플리케이션 코드 플랫폼의 제약을 받지 않도록 모든 AR 및 VR 플랫폼이 리팩터링되었습니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-108">In 4.26, all AR and VR platforms have been refactored to add common interfaces and keep application code platform agnostic.</span></span>  <span data-ttu-id="361c2-109">이 리팩터링 때문에 4.26으로 업데이트되는 HoloLens 프로젝트에서 평소보다 많은 경고가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-109">Because of this refactor, HoloLens projects updating to 4.26 may see more warnings than usual.</span></span>  <span data-ttu-id="361c2-110">프로젝트를 다른 플랫폼으로 보다 쉽게 이식할 수 있도록 새 API로 업데이트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-110">Updating to the new APIs is recommended so the project can be more easily ported to other platforms.</span></span>

<span data-ttu-id="361c2-111">더 이상 사용되지 않는 함수와 대신 사용되는 함수를 알려주는 경고 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-111">Warning messages will show which function has been deprecated and indicate what function to use instead.</span></span>  <span data-ttu-id="361c2-112">사용되지 않는 모든 함수는 이 릴리스에서는 계속 작동하지만 이후 릴리스에서는 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-112">All deprecated functions will continue to work for this release but may not work in future releases.</span></span>  <span data-ttu-id="361c2-113">뿐만 아니라 사용되지 않는 함수는 청사진에서 함수를 검색할 때 더 이상 나열되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-113">Deprecated functions will also no longer be listed when searching for functions in a blueprint.</span></span>

![Create Named ARPin 함수의 청사진](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a><span data-ttu-id="361c2-115">4.25 사용 중단</span><span class="sxs-lookup"><span data-stu-id="361c2-115">4.25 deprecations</span></span>

| <span data-ttu-id="361c2-116">더 이상 사용되지 않는 함수</span><span class="sxs-lookup"><span data-stu-id="361c2-116">Deprecated function</span></span> | <span data-ttu-id="361c2-117">새 함수</span><span class="sxs-lookup"><span data-stu-id="361c2-117">New function</span></span> |
| --- | --- |
| <span data-ttu-id="361c2-118">CreateNamedARPin</span><span class="sxs-lookup"><span data-stu-id="361c2-118">CreateNamedARPin</span></span> | ![Pin Component 함수의 청사진](images/unreal-porting-img-02.png) |
| <span data-ttu-id="361c2-120">LoadWMRAnchorStoreARPins</span><span class="sxs-lookup"><span data-stu-id="361c2-120">LoadWMRAnchorStoreARPins</span></span> | ![Load ARPins from Local Store 함수의 청사진](images/unreal-porting-img-03.png) |
| <span data-ttu-id="361c2-122">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span><span class="sxs-lookup"><span data-stu-id="361c2-122">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span></span> | ![Save ARPin to Local Store 함수의 청사진](images/unreal-porting-img-04.png) |
| <span data-ttu-id="361c2-124">RemoveARPinFromWMRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="361c2-124">RemoveARPinFromWMRAnchorStore</span></span> | ![Remove ARPin from Local Store 함수의 청사진](images/unreal-porting-img-05.png) |
| <span data-ttu-id="361c2-126">SetEnabledMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="361c2-126">SetEnabledMixedRealityCamera</span></span> | ![Set Enabled XRCamera 함수의 청사진](images/unreal-porting-img-06.png) |
| <span data-ttu-id="361c2-128">ResizeMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="361c2-128">ResizeMixedRealityCamera</span></span> | ![Resize XRCamera 함수의 청사진](images/unreal-porting-img-07.png) |
| <span data-ttu-id="361c2-130">StartCameraCapture</span><span class="sxs-lookup"><span data-stu-id="361c2-130">StartCameraCapture</span></span> | ![카메라 캡처를 시작하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-08.png) |
| <span data-ttu-id="361c2-132">StopCameraCapture</span><span class="sxs-lookup"><span data-stu-id="361c2-132">StopCameraCapture</span></span> | ![카메라 캡처를 중지하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-09.png) |
| <span data-ttu-id="361c2-134">StartQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="361c2-134">StartQRCodeCapture</span></span> | ![QR 코드 캡처를 시작하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-10.png) |
| <span data-ttu-id="361c2-136">StopQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="361c2-136">StopQRCodeCapture</span></span> | ![QR 코드 캡처를 중지하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-11.png) |
| <span data-ttu-id="361c2-138">4\.25에서는 공간 매핑이 자동으로 시작되었지만 4.26에서는 직접 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-138">Spatial mapping previously automatically started in 4.25, but now needs to be toggled in 4.26.</span></span> | ![공간 매핑을 사용하도록 설정하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-12.png) |
| <span data-ttu-id="361c2-140">ShowKeyboard</span><span class="sxs-lookup"><span data-stu-id="361c2-140">ShowKeyboard</span></span> | <span data-ttu-id="361c2-141">포커스가 텍스트 위젯으로 이동하면 키보드가 자동으로 표시되기 때문에 4.26에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-141">Removed in 4.26 since the keyboard automatically shows when a text widget is focused on.</span></span> |
| <span data-ttu-id="361c2-142">HideKeyboard</span><span class="sxs-lookup"><span data-stu-id="361c2-142">HideKeyboard</span></span> | <span data-ttu-id="361c2-143">텍스트 위젯의 포커스가 다른 곳으로 이동하면 키보드가 자동으로 표시되기 때문에 4.26에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-143">Removed in 4.26 since the keyboard will automatically hide when a text widget is unfocused.</span></span> |
| <span data-ttu-id="361c2-144">SupportsHandTracking</span><span class="sxs-lookup"><span data-stu-id="361c2-144">SupportsHandTracking</span></span> | ![Supports Hand Tracking 속성의 청사진](images/unreal-porting-img-13.png) |
| <span data-ttu-id="361c2-146">IsDisplayOpaque</span><span class="sxs-lookup"><span data-stu-id="361c2-146">IsDisplayOpaque</span></span> | ![IsDisplayOpaque 속성의 청사진](images/unreal-porting-img-14.png) |
| <span data-ttu-id="361c2-148">GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus</span><span class="sxs-lookup"><span data-stu-id="361c2-148">GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus</span></span> | ![Get Motion Controller Data 함수의 청사진](images/unreal-porting-img-15.png) |
| <span data-ttu-id="361c2-150">GetVersionString</span><span class="sxs-lookup"><span data-stu-id="361c2-150">GetVersionString</span></span> | ![Get Version String 함수의 청사진](images/unreal-porting-img-16.png) |
| <span data-ttu-id="361c2-152">IsTrackingAvailable</span><span class="sxs-lookup"><span data-stu-id="361c2-152">IsTrackingAvailable</span></span> | ![IsTrackingAvailable 속성의 청사진](images/unreal-porting-img-17.png) |
| <span data-ttu-id="361c2-154">IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed</span><span class="sxs-lookup"><span data-stu-id="361c2-154">IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed</span></span> | <span data-ttu-id="361c2-155">Unreal의 입력 작업 시스템을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-155">Use Unreal’s input action system.</span></span> |
| <span data-ttu-id="361c2-156">SetFocusPointForFrame</span><span class="sxs-lookup"><span data-stu-id="361c2-156">SetFocusPointForFrame</span></span> | <span data-ttu-id="361c2-157">4\.26에서는 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-157">Removed in 4.26.</span></span>  <span data-ttu-id="361c2-158">이전에는 원격 기능에서 리프로젝션에 사용되었지만, 지금은 깊이 리프로젝션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="361c2-158">Previously this was used for reprojection when remoting, which now supports depth reprojection.</span></span> |