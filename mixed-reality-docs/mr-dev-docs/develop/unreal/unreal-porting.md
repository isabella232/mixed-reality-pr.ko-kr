---
title: Unreal에서 프로젝트 업그레이드
description: Unreal 프로젝트의 버전 업그레이드 단계, API 변경 및 사용 중단을 최신 상태로 유지하세요.
author: hferrone
ms.author: jacksonf
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 설명서, 가이드, 기능, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 이식, 업그레이드
ms.openlocfilehash: 27fb726bc0ca9c51b4e7b68ad28b76f89312262e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010053"
---
# <a name="upgrading-projects-in-unreal"></a><span data-ttu-id="3d1ea-104">Unreal에서 프로젝트 업그레이드</span><span class="sxs-lookup"><span data-stu-id="3d1ea-104">Upgrading projects in Unreal</span></span>

<span data-ttu-id="3d1ea-105">새 버전의 Unreal로 업데이트할 때 청사진을 컴파일하거나 프로젝트를 패키징하면 사용되지 않는 함수가 경고로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-105">When updating to a new version of Unreal, deprecated functions show up as warnings when compiling blueprints or packaging the project.</span></span>  <span data-ttu-id="3d1ea-106">기존 함수를 대체하는 새 함수가 추가되면 기존 함수는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-106">Functions are deprecated when a new function has been added that should be used instead.</span></span> 

## <a name="426-upgrades"></a><span data-ttu-id="3d1ea-107">4.26 업그레이드</span><span class="sxs-lookup"><span data-stu-id="3d1ea-107">4.26 upgrades</span></span>
 
<span data-ttu-id="3d1ea-108">4\.26에서는 공통 인터페이스를 추가하고 애플리케이션 코드 플랫폼의 제약을 받지 않도록 모든 AR 및 VR 플랫폼이 리팩터링되었기 때문에 평소보다 더 많은 경고가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-108">In 4.26, all AR and VR platforms have been refactored to add common interfaces and keep application code platform agnostic, so you may see more warnings than usual.</span></span>  <span data-ttu-id="3d1ea-109">프로젝트를 다른 플랫폼으로 보다 쉽게 이식할 수 있도록 새 API로 업데이트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-109">Updating to the new APIs is recommended so the project can be more easily ported to other platforms.</span></span>

<span data-ttu-id="3d1ea-110">더 이상 사용되지 않는 함수와 대신 사용되는 함수를 알려주는 경고 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-110">Warning messages will show which function has been deprecated and indicate what function to use instead.</span></span>  <span data-ttu-id="3d1ea-111">사용되지 않는 모든 함수는 이 릴리스에서는 계속 작동하지만 이후 릴리스에서는 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-111">All deprecated functions will continue to work for this release but may not work in future releases.</span></span>  <span data-ttu-id="3d1ea-112">뿐만 아니라 사용되지 않는 함수는 청사진에서 함수를 검색할 때 더 이상 나열되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-112">Deprecated functions will also no longer be listed when searching for functions in a blueprint.</span></span>

![Create Named ARPin 함수의 청사진](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a><span data-ttu-id="3d1ea-114">4.25 사용 중단</span><span class="sxs-lookup"><span data-stu-id="3d1ea-114">4.25 deprecations</span></span>

| <span data-ttu-id="3d1ea-115">더 이상 사용되지 않는 함수</span><span class="sxs-lookup"><span data-stu-id="3d1ea-115">Deprecated function</span></span> | <span data-ttu-id="3d1ea-116">새 함수</span><span class="sxs-lookup"><span data-stu-id="3d1ea-116">New function</span></span> |
| --- | --- |
| <span data-ttu-id="3d1ea-117">CreateNamedARPin</span><span class="sxs-lookup"><span data-stu-id="3d1ea-117">CreateNamedARPin</span></span> | ![Pin Component 함수의 청사진](images/unreal-porting-img-02.png) |
| <span data-ttu-id="3d1ea-119">LoadWMRAnchorStoreARPins</span><span class="sxs-lookup"><span data-stu-id="3d1ea-119">LoadWMRAnchorStoreARPins</span></span> | ![Load ARPins from Local Store 함수의 청사진](images/unreal-porting-img-03.png) |
| <span data-ttu-id="3d1ea-121">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span><span class="sxs-lookup"><span data-stu-id="3d1ea-121">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span></span> | ![Save ARPin to Local Store 함수의 청사진](images/unreal-porting-img-04.png) |
| <span data-ttu-id="3d1ea-123">RemoveARPinFromWMRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="3d1ea-123">RemoveARPinFromWMRAnchorStore</span></span> | ![Remove ARPin from Local Store 함수의 청사진](images/unreal-porting-img-05.png) |
| <span data-ttu-id="3d1ea-125">SetEnabledMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="3d1ea-125">SetEnabledMixedRealityCamera</span></span> | ![Set Enabled XRCamera 함수의 청사진](images/unreal-porting-img-06.png) |
| <span data-ttu-id="3d1ea-127">ResizeMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="3d1ea-127">ResizeMixedRealityCamera</span></span> | ![Resize XRCamera 함수의 청사진](images/unreal-porting-img-07.png) |
| <span data-ttu-id="3d1ea-129">StartCameraCapture</span><span class="sxs-lookup"><span data-stu-id="3d1ea-129">StartCameraCapture</span></span> | ![카메라 캡처를 시작하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-08.png) |
| <span data-ttu-id="3d1ea-131">StopCameraCapture</span><span class="sxs-lookup"><span data-stu-id="3d1ea-131">StopCameraCapture</span></span> | ![카메라 캡처를 중지하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-09.png) |
| <span data-ttu-id="3d1ea-133">StartQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="3d1ea-133">StartQRCodeCapture</span></span> | ![QR 코드 캡처를 시작하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-10.png) |
| <span data-ttu-id="3d1ea-135">StopQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="3d1ea-135">StopQRCodeCapture</span></span> | ![QR 코드 캡처를 중지하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-11.png) |
| <span data-ttu-id="3d1ea-137">4\.25에서는 공간 매핑이 자동으로 시작되었지만 4.26에서는 직접 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-137">Spatial mapping previously automatically started in 4.25, but now needs to be toggled in 4.26.</span></span> | ![공간 매핑을 사용하도록 설정하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-12.png) |
| <span data-ttu-id="3d1ea-139">ShowKeyboard</span><span class="sxs-lookup"><span data-stu-id="3d1ea-139">ShowKeyboard</span></span> | <span data-ttu-id="3d1ea-140">포커스가 텍스트 위젯으로 이동하면 키보드가 자동으로 표시되기 때문에 4.26에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-140">Removed in 4.26 since the keyboard automatically shows when a text widget is focused on.</span></span> |
| <span data-ttu-id="3d1ea-141">HideKeyboard</span><span class="sxs-lookup"><span data-stu-id="3d1ea-141">HideKeyboard</span></span> | <span data-ttu-id="3d1ea-142">텍스트 위젯의 포커스가 다른 곳으로 이동하면 키보드가 자동으로 표시되기 때문에 4.26에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-142">Removed in 4.26 since the keyboard will automatically hide when a text widget is unfocused.</span></span> |
| <span data-ttu-id="3d1ea-143">SupportsHandTracking</span><span class="sxs-lookup"><span data-stu-id="3d1ea-143">SupportsHandTracking</span></span> | ![Supports Hand Tracking 속성의 청사진](images/unreal-porting-img-13.png) |
| <span data-ttu-id="3d1ea-145">IsDisplayOpaque</span><span class="sxs-lookup"><span data-stu-id="3d1ea-145">IsDisplayOpaque</span></span> | ![IsDisplayOpaque 속성의 청사진](images/unreal-porting-img-14.png) |
| <span data-ttu-id="3d1ea-147">GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus</span><span class="sxs-lookup"><span data-stu-id="3d1ea-147">GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus</span></span> | ![Get Motion Controller Data 함수의 청사진](images/unreal-porting-img-15.png) |
| <span data-ttu-id="3d1ea-149">GetVersionString</span><span class="sxs-lookup"><span data-stu-id="3d1ea-149">GetVersionString</span></span> | ![Get Version String 함수의 청사진](images/unreal-porting-img-16.png) |
| <span data-ttu-id="3d1ea-151">IsTrackingAvailable</span><span class="sxs-lookup"><span data-stu-id="3d1ea-151">IsTrackingAvailable</span></span> | ![IsTrackingAvailable 속성의 청사진](images/unreal-porting-img-17.png) |
| <span data-ttu-id="3d1ea-153">IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed</span><span class="sxs-lookup"><span data-stu-id="3d1ea-153">IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed</span></span> | <span data-ttu-id="3d1ea-154">Unreal의 입력 작업 시스템을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-154">Use Unreal’s input action system.</span></span> |
| <span data-ttu-id="3d1ea-155">SetFocusPointForFrame</span><span class="sxs-lookup"><span data-stu-id="3d1ea-155">SetFocusPointForFrame</span></span> | <span data-ttu-id="3d1ea-156">4.26에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-156">Removed in 4.26.</span></span>  <span data-ttu-id="3d1ea-157">이전에는 원격 접속 시 리프로젝션에 사용되었지만, 지금은 깊이 리프로젝션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-157">Previously used for reprojection when remoting, which now supports depth reprojection.</span></span> |

## <a name="426-changes"></a><span data-ttu-id="3d1ea-158">4.26 변경 사항</span><span class="sxs-lookup"><span data-stu-id="3d1ea-158">4.26 changes</span></span>

<span data-ttu-id="3d1ea-159">중요한 변경 사항은 Windows Mixed Reality 플러그 인을 시작하려면 **편집 > 프로젝트 설정 > 프로젝트 > 설명 > 설정** 에서 **VR에서 시작** 이 필수라는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-159">The significant change is that **Start in VR** from **Edit > Project Settings > Project > Description > Settings** is mandatory for starting Windows Mixed Reality plugin.</span></span> <span data-ttu-id="3d1ea-160">해당 매개 변수를 사용하지 않으면 디바이스에 홀로그램이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d1ea-160">Without that parameter, you will not see your holograms on the device.</span></span>
