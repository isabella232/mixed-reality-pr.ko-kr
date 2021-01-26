---
title: 위치를 찾을 수 있는 카메라
description: HoloLens front camera 카메라, 작동 방식 및 개발자가 사용할 수 있는 프로필 및 해상도에 대 한 일반 정보입니다.
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: 카메라, hololens, 컬러 카메라, 전면, hololens 2, cv, 컴퓨터 비전, fiducial, 표식, qr 코드, qr, 사진, 비디오
ms.openlocfilehash: f34973fee56f9469632b320a62dd441ed32e5805
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810158"
---
# <a name="locatable-camera"></a><span data-ttu-id="f456d-104">위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="f456d-104">Locatable camera</span></span>

<span data-ttu-id="f456d-105">HoloLens는 장치 전면에 탑재 된 세계 카메라를 포함 하 여 앱이 사용자에 게 표시 되는 내용을 볼 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-105">HoloLens includes a world-facing camera mounted on the front of the device, which enables apps to see what the user sees.</span></span> <span data-ttu-id="f456d-106">개발자는 스마트폰, 노트북 또는 데스크톱에서 색 카메라를 사용할 때와 마찬가지로 카메라에 액세스 하 고 해당 카메라를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-106">Developers have access to and control of the camera, just as they would for color cameras on smartphones, portables, or desktops.</span></span> <span data-ttu-id="f456d-107">모바일 및 데스크톱에서 작동 하는 동일한 유니버설 windows [미디어 캡처](/uwp/api/Windows.Media.Capture.MediaCapture) 및 windows Media foundation Api는 HoloLens에서 작업 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-107">The same universal windows [media capture](/uwp/api/Windows.Media.Capture.MediaCapture) and windows media foundation APIs that work on mobile and desktop work on HoloLens.</span></span> <span data-ttu-id="f456d-108">Unity [는 이러한 Windows api](../unity/locatable-camera-in-unity.md) 를 HoloLens의 카메라 사용 기능을 추상화 하도록 래핑 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-108">Unity [has wrapped these windows APIs](../unity/locatable-camera-in-unity.md) to abstract camera usage features on HoloLens.</span></span> <span data-ttu-id="f456d-109">기능 작업에는 holograms를 사용 하거나 사용 하지 않고 일반 사진과 비디오를 촬영 하 고 카메라의 위치와 장면의 원근감을 찾는 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-109">Feature tasks include taking regular photos and videos (with or without holograms) and locating the camera's position in and perspective on the scene.</span></span>

## <a name="device-camera-information"></a><span data-ttu-id="f456d-110">장치 카메라 정보</span><span class="sxs-lookup"><span data-stu-id="f456d-110">Device camera information</span></span>

### <a name="hololens-first-generation"></a><span data-ttu-id="f456d-111">HoloLens (첫 번째 생성)</span><span class="sxs-lookup"><span data-stu-id="f456d-111">HoloLens (first-generation)</span></span>

* <span data-ttu-id="f456d-112">자동 흰색 잔액, 자동 노출 및 전체 이미지 처리 파이프라인이 있는 PV (focus photo/video) 카메라</span><span class="sxs-lookup"><span data-stu-id="f456d-112">Fixed focus photo/video (PV) camera with auto white balance, auto exposure, and full image-processing pipeline.</span></span>
* <span data-ttu-id="f456d-113">카메라가 활성화 될 때마다 전 세계의 개인 개인 정보 취급 LED가 켜 집니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-113">White Privacy LED facing the world will illuminate whenever the camera is active</span></span>
* <span data-ttu-id="f456d-114">카메라는 30, 24, 20, 15, 5fps의 다음 모드 (모든 모드에서 16:9 가로 세로 비율)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-114">The camera supports the following modes (all modes are 16:9 aspect ratio) at 30, 24, 20, 15, and 5 fps:</span></span>

  |  <span data-ttu-id="f456d-115">비디오</span><span class="sxs-lookup"><span data-stu-id="f456d-115">Video</span></span>  |  <span data-ttu-id="f456d-116">미리 보기</span><span class="sxs-lookup"><span data-stu-id="f456d-116">Preview</span></span>  |  <span data-ttu-id="f456d-117">실패할</span><span class="sxs-lookup"><span data-stu-id="f456d-117">Still</span></span>  |  <span data-ttu-id="f456d-118">뷰의 가로 필드 (H-FOV)</span><span class="sxs-lookup"><span data-stu-id="f456d-118">Horizontal Field of View (H-FOV)</span></span> |  <span data-ttu-id="f456d-119">권장 사용법</span><span class="sxs-lookup"><span data-stu-id="f456d-119">Suggested usage</span></span> | 
  |----------|----------|----------|----------|----------|
  |  <span data-ttu-id="f456d-120">1280x720</span><span class="sxs-lookup"><span data-stu-id="f456d-120">1280x720</span></span> |  <span data-ttu-id="f456d-121">1280x720</span><span class="sxs-lookup"><span data-stu-id="f456d-121">1280x720</span></span> |  <span data-ttu-id="f456d-122">1280x720</span><span class="sxs-lookup"><span data-stu-id="f456d-122">1280x720</span></span> |  <span data-ttu-id="f456d-123">45도</span><span class="sxs-lookup"><span data-stu-id="f456d-123">45 deg</span></span>  |  <span data-ttu-id="f456d-124">(비디오 안정화를 사용 하는 기본 모드)</span><span class="sxs-lookup"><span data-stu-id="f456d-124">(default mode with video stabilization)</span></span> | 
  |  <span data-ttu-id="f456d-125">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f456d-125">N/A</span></span> |  <span data-ttu-id="f456d-126">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f456d-126">N/A</span></span> |  <span data-ttu-id="f456d-127">2048x1152</span><span class="sxs-lookup"><span data-stu-id="f456d-127">2048x1152</span></span> |  <span data-ttu-id="f456d-128">67도</span><span class="sxs-lookup"><span data-stu-id="f456d-128">67 deg</span></span> |  <span data-ttu-id="f456d-129">가장 높은 해상도의 이미지</span><span class="sxs-lookup"><span data-stu-id="f456d-129">Highest resolution still image</span></span> | 
  |  <span data-ttu-id="f456d-130">1408x792</span><span class="sxs-lookup"><span data-stu-id="f456d-130">1408x792</span></span> |  <span data-ttu-id="f456d-131">1408x792</span><span class="sxs-lookup"><span data-stu-id="f456d-131">1408x792</span></span> |  <span data-ttu-id="f456d-132">1408x792</span><span class="sxs-lookup"><span data-stu-id="f456d-132">1408x792</span></span> |  <span data-ttu-id="f456d-133">48도</span><span class="sxs-lookup"><span data-stu-id="f456d-133">48 deg</span></span> |  <span data-ttu-id="f456d-134">비디오 안정화 전 Overscan (패딩) 해상도</span><span class="sxs-lookup"><span data-stu-id="f456d-134">Overscan (padding) resolution before video stabilization</span></span> | 
  |  <span data-ttu-id="f456d-135">1344x756</span><span class="sxs-lookup"><span data-stu-id="f456d-135">1344x756</span></span> |  <span data-ttu-id="f456d-136">1344x756</span><span class="sxs-lookup"><span data-stu-id="f456d-136">1344x756</span></span> |  <span data-ttu-id="f456d-137">1344x756</span><span class="sxs-lookup"><span data-stu-id="f456d-137">1344x756</span></span> |  <span data-ttu-id="f456d-138">67도</span><span class="sxs-lookup"><span data-stu-id="f456d-138">67 deg</span></span> |  <span data-ttu-id="f456d-139">Overscan를 사용 하는 넓은 FOV 비디오 모드</span><span class="sxs-lookup"><span data-stu-id="f456d-139">Large FOV video mode with overscan</span></span> | 
  |  <span data-ttu-id="f456d-140">896x504</span><span class="sxs-lookup"><span data-stu-id="f456d-140">896x504</span></span> |  <span data-ttu-id="f456d-141">896x504</span><span class="sxs-lookup"><span data-stu-id="f456d-141">896x504</span></span> |  <span data-ttu-id="f456d-142">896x504</span><span class="sxs-lookup"><span data-stu-id="f456d-142">896x504</span></span> |  <span data-ttu-id="f456d-143">48도</span><span class="sxs-lookup"><span data-stu-id="f456d-143">48 deg</span></span> |  <span data-ttu-id="f456d-144">이미지 처리 작업에 대 한 낮은 전원/저해상도 모드</span><span class="sxs-lookup"><span data-stu-id="f456d-144">Low power / Low-resolution mode for image-processing tasks</span></span> | 

### <a name="hololens-2"></a><span data-ttu-id="f456d-145">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f456d-145">HoloLens 2</span></span>

* <span data-ttu-id="f456d-146">자동 흰색 잔액, 자동 노출 및 전체 이미지 처리 파이프라인이 있는 PV (자동 포커스 사진/비디오) 카메라</span><span class="sxs-lookup"><span data-stu-id="f456d-146">Auto-focus photo/video (PV) camera with auto white balance, auto exposure, and full image-processing pipeline.</span></span>
* <span data-ttu-id="f456d-147">카메라가 활성화 될 때마다 전 세계의 개인 개인 정보 취급 LED가 켜 집니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-147">White Privacy LED facing the world will illuminate whenever the camera is active.</span></span>
* <span data-ttu-id="f456d-148">HoloLens 2는 다른 카메라 프로필을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-148">HoloLens 2 supports different camera profiles.</span></span> <span data-ttu-id="f456d-149">[카메라 기능을 검색 하 고 선택](/windows/uwp/audio-video-camera/camera-profiles)하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-149">Learn how to [discover and select camera capabilities](/windows/uwp/audio-video-camera/camera-profiles).</span></span>
* <span data-ttu-id="f456d-150">카메라는 다음 프로필 및 해상도를 지원 합니다 (모든 비디오 모드는 16:9 가로 세로 비율).</span><span class="sxs-lookup"><span data-stu-id="f456d-150">The camera supports the following profiles and resolutions (all video modes are 16:9 aspect ratio):</span></span>
  
  | <span data-ttu-id="f456d-151">프로필</span><span class="sxs-lookup"><span data-stu-id="f456d-151">Profile</span></span>                                         | <span data-ttu-id="f456d-152">비디오</span><span class="sxs-lookup"><span data-stu-id="f456d-152">Video</span></span>     | <span data-ttu-id="f456d-153">미리 보기</span><span class="sxs-lookup"><span data-stu-id="f456d-153">Preview</span></span>   | <span data-ttu-id="f456d-154">실패할</span><span class="sxs-lookup"><span data-stu-id="f456d-154">Still</span></span>     | <span data-ttu-id="f456d-155">프레임 속도</span><span class="sxs-lookup"><span data-stu-id="f456d-155">Frame rates</span></span> | <span data-ttu-id="f456d-156">뷰의 가로 필드 (H-FOV)</span><span class="sxs-lookup"><span data-stu-id="f456d-156">Horizontal Field of View (H-FOV)</span></span> | <span data-ttu-id="f456d-157">권장 사용법</span><span class="sxs-lookup"><span data-stu-id="f456d-157">Suggested usage</span></span>                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | <span data-ttu-id="f456d-158">레거시, 0 BalancedVideoAndPhoto, 100</span><span class="sxs-lookup"><span data-stu-id="f456d-158">Legacy,0  BalancedVideoAndPhoto,100</span></span>             | <span data-ttu-id="f456d-159">2272x1278</span><span class="sxs-lookup"><span data-stu-id="f456d-159">2272x1278</span></span> | <span data-ttu-id="f456d-160">2272x1278</span><span class="sxs-lookup"><span data-stu-id="f456d-160">2272x1278</span></span> |           | <span data-ttu-id="f456d-161">15.30</span><span class="sxs-lookup"><span data-stu-id="f456d-161">15.30</span></span>       | <span data-ttu-id="f456d-162">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-162">64.69</span></span>                            | <span data-ttu-id="f456d-163">고품질 비디오 녹화</span><span class="sxs-lookup"><span data-stu-id="f456d-163">High-quality video recording</span></span>                |
  | <span data-ttu-id="f456d-164">레거시, 0 BalancedVideoAndPhoto, 100</span><span class="sxs-lookup"><span data-stu-id="f456d-164">Legacy,0  BalancedVideoAndPhoto,100</span></span>             | <span data-ttu-id="f456d-165">896x504</span><span class="sxs-lookup"><span data-stu-id="f456d-165">896x504</span></span>   | <span data-ttu-id="f456d-166">896x504</span><span class="sxs-lookup"><span data-stu-id="f456d-166">896x504</span></span>   |           | <span data-ttu-id="f456d-167">15.30</span><span class="sxs-lookup"><span data-stu-id="f456d-167">15.30</span></span>       | <span data-ttu-id="f456d-168">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-168">64.69</span></span>                            | <span data-ttu-id="f456d-169">고품질 사진 캡처에 대 한 미리 보기 스트림</span><span class="sxs-lookup"><span data-stu-id="f456d-169">Preview stream for high-quality photo capture</span></span> |
  | <span data-ttu-id="f456d-170">레거시, 0 BalancedVideoAndPhoto, 100</span><span class="sxs-lookup"><span data-stu-id="f456d-170">Legacy,0  BalancedVideoAndPhoto,100</span></span>             |           |           | <span data-ttu-id="f456d-171">3904x2196</span><span class="sxs-lookup"><span data-stu-id="f456d-171">3904x2196</span></span> |             | <span data-ttu-id="f456d-172">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-172">64.69</span></span>                            | <span data-ttu-id="f456d-173">고품질 사진 캡처</span><span class="sxs-lookup"><span data-stu-id="f456d-173">High-quality photo capture</span></span>                  |
  | <span data-ttu-id="f456d-174">BalancedVideoAndPhoto, 120</span><span class="sxs-lookup"><span data-stu-id="f456d-174">BalancedVideoAndPhoto, 120</span></span>                       | <span data-ttu-id="f456d-175">1952x1100</span><span class="sxs-lookup"><span data-stu-id="f456d-175">1952x1100</span></span> | <span data-ttu-id="f456d-176">1952x1100</span><span class="sxs-lookup"><span data-stu-id="f456d-176">1952x1100</span></span> | <span data-ttu-id="f456d-177">1952x1100</span><span class="sxs-lookup"><span data-stu-id="f456d-177">1952x1100</span></span> | <span data-ttu-id="f456d-178">15.30</span><span class="sxs-lookup"><span data-stu-id="f456d-178">15.30</span></span>       | <span data-ttu-id="f456d-179">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-179">64.69</span></span>                            | <span data-ttu-id="f456d-180">긴 기간 시나리오</span><span class="sxs-lookup"><span data-stu-id="f456d-180">Long duration scenarios</span></span>                     |
  | <span data-ttu-id="f456d-181">BalancedVideoAndPhoto, 120</span><span class="sxs-lookup"><span data-stu-id="f456d-181">BalancedVideoAndPhoto, 120</span></span>                       | <span data-ttu-id="f456d-182">1504x846</span><span class="sxs-lookup"><span data-stu-id="f456d-182">1504x846</span></span>  | <span data-ttu-id="f456d-183">1504x846</span><span class="sxs-lookup"><span data-stu-id="f456d-183">1504x846</span></span>  |           | <span data-ttu-id="f456d-184">15.30</span><span class="sxs-lookup"><span data-stu-id="f456d-184">15.30</span></span>       | <span data-ttu-id="f456d-185">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-185">64.69</span></span>                            | <span data-ttu-id="f456d-186">긴 기간 시나리오</span><span class="sxs-lookup"><span data-stu-id="f456d-186">Long duration scenarios</span></span>                     |
  | <span data-ttu-id="f456d-187">비디오 회의, 100</span><span class="sxs-lookup"><span data-stu-id="f456d-187">VideoConferencing,100</span></span>                           | <span data-ttu-id="f456d-188">1952x1100</span><span class="sxs-lookup"><span data-stu-id="f456d-188">1952x1100</span></span> | <span data-ttu-id="f456d-189">1952x1100</span><span class="sxs-lookup"><span data-stu-id="f456d-189">1952x1100</span></span> | <span data-ttu-id="f456d-190">1952x1100</span><span class="sxs-lookup"><span data-stu-id="f456d-190">1952x1100</span></span> | <span data-ttu-id="f456d-191">15, 30, 60</span><span class="sxs-lookup"><span data-stu-id="f456d-191">15,30,60</span></span>    | <span data-ttu-id="f456d-192">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-192">64.69</span></span>                            | <span data-ttu-id="f456d-193">비디오 회의, 긴 기간 시나리오</span><span class="sxs-lookup"><span data-stu-id="f456d-193">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="f456d-194">비디오 회의, 100</span><span class="sxs-lookup"><span data-stu-id="f456d-194">Videoconferencing,100</span></span>                           | <span data-ttu-id="f456d-195">1504x846</span><span class="sxs-lookup"><span data-stu-id="f456d-195">1504x846</span></span>  | <span data-ttu-id="f456d-196">1504x846</span><span class="sxs-lookup"><span data-stu-id="f456d-196">1504x846</span></span>  |           | <span data-ttu-id="f456d-197">5, 15, 30, 60</span><span class="sxs-lookup"><span data-stu-id="f456d-197">5,15,30,60</span></span>  | <span data-ttu-id="f456d-198">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-198">64.69</span></span>                            | <span data-ttu-id="f456d-199">비디오 회의, 긴 기간 시나리오</span><span class="sxs-lookup"><span data-stu-id="f456d-199">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="f456d-200">비디오 회의, 100 BalancedVideoAndPhoto, 120</span><span class="sxs-lookup"><span data-stu-id="f456d-200">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="f456d-201">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="f456d-201">1920x1080</span></span> | <span data-ttu-id="f456d-202">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="f456d-202">1920x1080</span></span> | <span data-ttu-id="f456d-203">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="f456d-203">1920x1080</span></span> | <span data-ttu-id="f456d-204">15, 30</span><span class="sxs-lookup"><span data-stu-id="f456d-204">15,30</span></span>       | <span data-ttu-id="f456d-205">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-205">64.69</span></span>                            | <span data-ttu-id="f456d-206">비디오 회의, 긴 기간 시나리오</span><span class="sxs-lookup"><span data-stu-id="f456d-206">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="f456d-207">비디오 회의, 100 BalancedVideoAndPhoto, 120</span><span class="sxs-lookup"><span data-stu-id="f456d-207">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="f456d-208">1280x720</span><span class="sxs-lookup"><span data-stu-id="f456d-208">1280x720</span></span>  | <span data-ttu-id="f456d-209">1280x720</span><span class="sxs-lookup"><span data-stu-id="f456d-209">1280x720</span></span>  | <span data-ttu-id="f456d-210">1280x720</span><span class="sxs-lookup"><span data-stu-id="f456d-210">1280x720</span></span>  | <span data-ttu-id="f456d-211">15, 30</span><span class="sxs-lookup"><span data-stu-id="f456d-211">15,30</span></span>       | <span data-ttu-id="f456d-212">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-212">64.69</span></span>                            | <span data-ttu-id="f456d-213">비디오 회의, 긴 기간 시나리오</span><span class="sxs-lookup"><span data-stu-id="f456d-213">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="f456d-214">비디오 회의, 100 BalancedVideoAndPhoto, 120</span><span class="sxs-lookup"><span data-stu-id="f456d-214">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="f456d-215">1128x636</span><span class="sxs-lookup"><span data-stu-id="f456d-215">1128x636</span></span>  |           |           | <span data-ttu-id="f456d-216">15, 30</span><span class="sxs-lookup"><span data-stu-id="f456d-216">15,30</span></span>       | <span data-ttu-id="f456d-217">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-217">64.69</span></span>                            | <span data-ttu-id="f456d-218">비디오 회의, 긴 기간 시나리오</span><span class="sxs-lookup"><span data-stu-id="f456d-218">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="f456d-219">비디오 회의, 100 BalancedVideoAndPhoto, 120</span><span class="sxs-lookup"><span data-stu-id="f456d-219">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="f456d-220">960 x 540</span><span class="sxs-lookup"><span data-stu-id="f456d-220">960x540</span></span>   |           |           | <span data-ttu-id="f456d-221">15, 30</span><span class="sxs-lookup"><span data-stu-id="f456d-221">15,30</span></span>       | <span data-ttu-id="f456d-222">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-222">64.69</span></span>                            | <span data-ttu-id="f456d-223">비디오 회의, 긴 기간 시나리오</span><span class="sxs-lookup"><span data-stu-id="f456d-223">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="f456d-224">비디오 회의, 100 BalancedVideoAndPhoto, 120</span><span class="sxs-lookup"><span data-stu-id="f456d-224">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="f456d-225">760x428</span><span class="sxs-lookup"><span data-stu-id="f456d-225">760x428</span></span>   |           |           | <span data-ttu-id="f456d-226">15, 30</span><span class="sxs-lookup"><span data-stu-id="f456d-226">15,30</span></span>       | <span data-ttu-id="f456d-227">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-227">64.69</span></span>                            | <span data-ttu-id="f456d-228">비디오 회의, 긴 기간 시나리오</span><span class="sxs-lookup"><span data-stu-id="f456d-228">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="f456d-229">비디오 회의, 100 BalancedVideoAndPhoto, 120</span><span class="sxs-lookup"><span data-stu-id="f456d-229">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="f456d-230">640x360</span><span class="sxs-lookup"><span data-stu-id="f456d-230">640x360</span></span>   |           |           | <span data-ttu-id="f456d-231">15, 30</span><span class="sxs-lookup"><span data-stu-id="f456d-231">15,30</span></span>       | <span data-ttu-id="f456d-232">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-232">64.69</span></span>                            | <span data-ttu-id="f456d-233">비디오 회의, 긴 기간 시나리오</span><span class="sxs-lookup"><span data-stu-id="f456d-233">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="f456d-234">비디오 회의, 100 BalancedVideoAndPhoto, 120</span><span class="sxs-lookup"><span data-stu-id="f456d-234">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="f456d-235">500x282</span><span class="sxs-lookup"><span data-stu-id="f456d-235">500x282</span></span>   |           |           | <span data-ttu-id="f456d-236">15, 30</span><span class="sxs-lookup"><span data-stu-id="f456d-236">15,30</span></span>       | <span data-ttu-id="f456d-237">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-237">64.69</span></span>                            | <span data-ttu-id="f456d-238">비디오 회의, 긴 기간 시나리오</span><span class="sxs-lookup"><span data-stu-id="f456d-238">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="f456d-239">비디오 회의, 100 BalancedVideoAndPhoto, 120</span><span class="sxs-lookup"><span data-stu-id="f456d-239">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="f456d-240">424x240</span><span class="sxs-lookup"><span data-stu-id="f456d-240">424x240</span></span>   |           |           | <span data-ttu-id="f456d-241">15, 30</span><span class="sxs-lookup"><span data-stu-id="f456d-241">15,30</span></span>       | <span data-ttu-id="f456d-242">64.69</span><span class="sxs-lookup"><span data-stu-id="f456d-242">64.69</span></span>                            | <span data-ttu-id="f456d-243">비디오 회의, 긴 기간 시나리오</span><span class="sxs-lookup"><span data-stu-id="f456d-243">Video conferencing, long duration scenarios</span></span> |

> [!NOTE]
> <span data-ttu-id="f456d-244">고객은 [혼합 현실 캡처](/hololens/holographic-photos-and-videos) 를 활용 하 여 holograms 및 비디오 안정화를 포함 하는 앱의 비디오 또는 사진을 찍을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-244">Customers can leverage [mixed reality capture](/hololens/holographic-photos-and-videos) to take videos or photos of your app, which include holograms and video stabilization.</span></span>
>
><span data-ttu-id="f456d-245">개발자는 응용 프로그램을 만들 때 고객이 콘텐츠를 캡처할 때 최대한 적절 하 게 보이도록 하려는 경우 고려해 야 할 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-245">As a developer, there are considerations you should take into account when creating your app if you want it to look as good as possible when a customer captures content.</span></span> <span data-ttu-id="f456d-246">앱 내에서 직접 혼합 현실 캡처를 사용 하도록 설정 (및 사용자 지정) 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-246">You can also enable (and customize) mixed reality capture from directly within your app.</span></span> <span data-ttu-id="f456d-247">[개발자를 위한 혼합 현실 캡처에서](mixed-reality-capture-for-developers.md)자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="f456d-247">Learn more at [mixed reality capture for developers](mixed-reality-capture-for-developers.md).</span></span>

## <a name="locating-the-device-camera-in-the-world"></a><span data-ttu-id="f456d-248">전 세계에서 장치 카메라 찾기</span><span class="sxs-lookup"><span data-stu-id="f456d-248">Locating the Device Camera in the World</span></span>

<span data-ttu-id="f456d-249">HoloLens에서 사진과 비디오를 사용 하는 경우 캡처된 프레임은 세계 카메라의 위치와 카메라의 렌즈 모델을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-249">When HoloLens takes photos and videos, the captured frames include the location of the camera in the world and the lens model of the camera.</span></span> <span data-ttu-id="f456d-250">이를 통해 응용 프로그램은 확대 된 이미징 시나리오에 대 한 실제 환경에서 카메라의 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-250">This allows applications to reason about the position of the camera in the real world for augmented imaging scenarios.</span></span> <span data-ttu-id="f456d-251">개발자는 선호 하는 이미지 처리 또는 사용자 지정 컴퓨터 비전 라이브러리를 사용 하 여 자신의 시나리오를 창의적 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-251">Developers can creatively roll their own scenarios using their favorite image processing or custom computer vision libraries.</span></span>

<span data-ttu-id="f456d-252">HoloLens 설명서의 다른 곳에서 "카메라"는 "가상 게임 카메라" (앱에서 렌더링 하는 것과 같은)를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-252">"Camera" elsewhere in HoloLens documentation may refer to the "virtual game camera" (the frustum the app renders to).</span></span> <span data-ttu-id="f456d-253">달리 지정 되지 않은 경우이 페이지의 "카메라"는 실제 RGB 색 카메라를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-253">Unless denoted otherwise, "camera" on this page refers to the real-world RGB color camera.</span></span>

### <a name="using-unity"></a><span data-ttu-id="f456d-254">Unity 사용</span><span class="sxs-lookup"><span data-stu-id="f456d-254">Using Unity</span></span>

<span data-ttu-id="f456d-255">' CameraIntrinsics ' 및 ' CameraCoordinateSystem '에서 응용 프로그램/세계 좌표계로 이동 하려면 [Unity의 과정이 카메라](../unity/locatable-camera-in-unity.md) 문서에 있는 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="f456d-255">To go from the 'CameraIntrinsics' and 'CameraCoordinateSystem' to your application/world coordinate system, follow the instructions in the [Locatable camera in Unity](../unity/locatable-camera-in-unity.md) article.</span></span>  <span data-ttu-id="f456d-256">CameraToWorldMatrix는 PhotoCaptureFrame 클래스에서 자동으로 제공 되므로 아래에서 설명 하는 CameraCoordinateSystem 변환에 대해 걱정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-256">CameraToWorldMatrix is automatically provided by PhotoCaptureFrame class, and so you don't need to worry about the CameraCoordinateSystem transforms discussed below.</span></span>

### <a name="using-mediaframereference"></a><span data-ttu-id="f456d-257">MediaFrameReference 사용</span><span class="sxs-lookup"><span data-stu-id="f456d-257">Using MediaFrameReference</span></span>

<span data-ttu-id="f456d-258">이러한 지침은 you'r가 [MediaFrameReference](/uwp/api/windows.media.capture.frames.mediaframereference) 클래스를 사용 하 여 카메라에서 이미지 프레임을 읽는 경우에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-258">These instructions apply if you'r using the [MediaFrameReference](/uwp/api/windows.media.capture.frames.mediaframereference) class to read image frames from the camera.</span></span>

<span data-ttu-id="f456d-259">각 이미지 프레임 (사진 또는 비디오)에는 캡처 시점에 카메라를 기반으로 하는 [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 이 포함 되어 있으며,이는 [MediaFrameReference](/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)의 [CoordinateSystem](/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) 속성을 사용 하 여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-259">Each image frame (whether photo or video) includes a [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) rooted at the camera at the time of capture, which can be accessed using the [CoordinateSystem](/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) property of your [MediaFrameReference](/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference).</span></span> <span data-ttu-id="f456d-260">각 프레임에는 [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 속성에서 찾을 수 있는 카메라 렌즈 모델에 대 한 설명이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-260">Each frame contains a description of the camera lens model, which can be found in the [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) property.</span></span> <span data-ttu-id="f456d-261">이러한 변환은 함께 각 픽셀에 대해 픽셀을 생성 한 photons에서 가져온 경로를 나타내는 3D 공간의 광선을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-261">Together, these transforms define for each pixel a ray in 3D space representing the path taken by the photons that produced the pixel.</span></span> <span data-ttu-id="f456d-262">이러한 광선은 프레임의 좌표계에서 다른 좌표계 (예: [고정 참조 프레임](../../design/coordinate-systems.md#stationary-frame-of-reference))로 변환을 가져와서 앱의 다른 콘텐츠와 관련 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-262">These rays can be related to other content in the app by obtaining the transform from the frame's coordinate system to some other coordinate system (e.g. from a [stationary frame of reference](../../design/coordinate-systems.md#stationary-frame-of-reference)).</span></span> 

<span data-ttu-id="f456d-263">각 이미지 프레임은 다음을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-263">Each image frame provides the following:</span></span>
* <span data-ttu-id="f456d-264">픽셀 데이터 (RGB/NV12/JPEG/등 형식)</span><span class="sxs-lookup"><span data-stu-id="f456d-264">Pixel Data (in RGB/NV12/JPEG/etc. format)</span></span>
* <span data-ttu-id="f456d-265">캡처 위치의 [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem)</span><span class="sxs-lookup"><span data-stu-id="f456d-265">A [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) from the location of capture</span></span>
* <span data-ttu-id="f456d-266">카메라의 렌즈 모드가 포함 된 [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-266">A [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) class containing the lens mode of the camera</span></span>

<span data-ttu-id="f456d-267">[HolographicFaceTracking 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) 에서는 카메라의 좌표계와 사용자 고유의 응용 프로그램 좌표계 간에 변환을 쿼리 하는 매우 간단한 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-267">The [HolographicFaceTracking sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) shows the fairly straightforward way to query for the transform between the camera's coordinate system and your own application coordinate systems.</span></span>

### <a name="using-media-foundation"></a><span data-ttu-id="f456d-268">미디어 파운데이션 사용</span><span class="sxs-lookup"><span data-stu-id="f456d-268">Using Media Foundation</span></span>

<span data-ttu-id="f456d-269">카메라에서 이미지 프레임을 읽기 위해 미디어 파운데이션를 직접 사용 하는 경우 다음 샘플 코드에 표시 된 것 처럼 각 프레임의 [MFSampleExtension_CameraExtrinsics 특성](/windows/win32/medfound/mfsampleextension-cameraextrinsics) 및 [MFSampleExtension_PinholeCameraIntrinsics 특성](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) 을 사용 하 여 응용 프로그램의 다른 좌표계를 기준으로 카메라 프레임을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-269">If you are using Media Foundation directly to read image frames from the camera, you can use each frame's [MFSampleExtension_CameraExtrinsics attribute](/windows/win32/medfound/mfsampleextension-cameraextrinsics) and [MFSampleExtension_PinholeCameraIntrinsics attribute](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) to locate camera frames relative to your application's other coordinate systems, as shown in this sample code:</span></span>

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a><span data-ttu-id="f456d-270">왜곡 오류</span><span class="sxs-lookup"><span data-stu-id="f456d-270">Distortion Error</span></span>

<span data-ttu-id="f456d-271">HoloLens에서 비디오와 스틸 이미지 스트림은 응용 프로그램에서 프레임을 사용할 수 있게 되기 전에 시스템의 이미지 처리 파이프라인에서 undistorted 됩니다 (미리 보기 스트림에는 원래의 왜곡 된 프레임이 포함 됨).</span><span class="sxs-lookup"><span data-stu-id="f456d-271">On HoloLens, the video and still image streams are undistorted in the system's image-processing pipeline before the frames are made available to the application (the preview stream contains the original distorted frames).</span></span> <span data-ttu-id="f456d-272">CameraIntrinsics만 사용할 수 있으므로 응용 프로그램은 이미지 프레임이 완벽 한 pinhole 카메라를 나타낸다고 가정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-272">Because only the CameraIntrinsics are made available, applications must assume image frames represent a perfect pinhole camera.</span></span>

<span data-ttu-id="f456d-273">HoloLens (처음 생성)에서 이미지 프로세서의 왜곡 함수는 프레임 메타 데이터에서 CameraIntrinsics를 사용 하는 경우에도 최대 10 픽셀의 오류를 남길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-273">On HoloLens (first-generation), the undistortion function in the image processor may still leave an error of up to 10 pixels when using the CameraIntrinsics in the frame metadata.</span></span> <span data-ttu-id="f456d-274">많은 사용 사례에서이 오류가 발생 하지 않습니다. 예를 들어 holograms를 실제 포스터/표식에 맞추고, 예를 들어, 10-px 오프셋 (holograms의 경우 약 11mm <은 2 미터 떨어진 위치)을 확인할 경우이 왜곡 오류가 원인일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-274">In many use cases, this error won't matter, but if you're aligning holograms to real world posters/markers, for example, and you notice a <10-px offset (roughly 11 mm for holograms positioned 2 meters away), this distortion error could be the cause.</span></span> 

## <a name="locatable-camera-usage-scenarios"></a><span data-ttu-id="f456d-275">과정이 카메라 사용 시나리오</span><span class="sxs-lookup"><span data-stu-id="f456d-275">Locatable Camera Usage Scenarios</span></span>

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a><span data-ttu-id="f456d-276">캡처된 전 세계에 사진 또는 비디오 표시</span><span class="sxs-lookup"><span data-stu-id="f456d-276">Show a photo or video in the world where it was captured</span></span>

<span data-ttu-id="f456d-277">장치 카메라 프레임에는 이미지를 찍은 시간을 정확히 표시 하는 데 사용할 수 있는 "전 세계 카메라" 변환이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-277">The Device Camera frames come with a "Camera To World" transform, that can be used to show exactly where the device was when the image was taken.</span></span> <span data-ttu-id="f456d-278">예를 들어이 위치 (MultiplyPoint (Vector3))에 작은 holographic 아이콘을 배치 하 고 카메라가 연결 된 방향으로 약간의 화살표 (CameraToWorld (MultiplyVector))를 그릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-278">For example, you could position a small holographic icon at this location (CameraToWorld.MultiplyPoint(Vector3.zero)) and even draw a little arrow in the direction that the camera was facing (CameraToWorld.MultiplyVector(Vector3.forward)).</span></span>

### <a name="tag--pattern--poster--object-tracking"></a><span data-ttu-id="f456d-279">태그/패턴/포스터/개체 추적</span><span class="sxs-lookup"><span data-stu-id="f456d-279">Tag / Pattern / Poster / Object Tracking</span></span>

<span data-ttu-id="f456d-280">많은 혼합 현실 응용 프로그램에서는 인식할 수 있는 이미지 또는 시각적 패턴을 사용 하 여 공간에 추적 가능 점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-280">Many mixed reality applications use a recognizable image or visual pattern to create a trackable point in space.</span></span> <span data-ttu-id="f456d-281">그런 다음이 요소를 기준으로 개체를 렌더링 하거나 알려진 위치를 만드는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-281">This is then used to render objects relative to that point or create a known location.</span></span> <span data-ttu-id="f456d-282">HoloLens를 사용 하는 경우에는 fiducials로 태그가 지정 된 실제 세계 개체 (예: QR 코드가 포함 된 TV 모니터)를 찾고, holograms를 fiducials에 배치 하 고, Wi-fi를 통해 HoloLens와 통신 하도록 설정 된 태블릿과 같은 비 HoloLens 장치와 시각적으로 연결 하는 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-282">Some uses for HoloLens include finding a real world object tagged with fiducials (e.g. a TV monitor with a QR code), placing holograms over fiducials, and visually pairing with non-HoloLens devices like tablets that have been set up to communicate with HoloLens via Wi-Fi.</span></span>

<span data-ttu-id="f456d-283">시각적 패턴을 인식 하 고 응용 프로그램의 세계 공간에 개체를 저장 하는 몇 가지 항목이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-283">You'll need a few things to recognize a visual pattern and place an object in the applications world space:</span></span>
1. <span data-ttu-id="f456d-284">QR 코드, AR 태그, 얼굴 찾기, 원 추적기, OCR 등의 이미지 패턴 인식 도구 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-284">An image pattern recognition toolkit, such as QR code, AR tags, face finder, circle trackers, OCR etc.</span></span>
2. <span data-ttu-id="f456d-285">런타임에 이미지 프레임을 수집 하 여 인식 계층으로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-285">Collect image frames at runtime, and pass them to the recognition layer</span></span>
3. <span data-ttu-id="f456d-286">이미지 위치를 세계 위치 또는 세계 광선으로 다시 프로젝션 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-286">Unproject their image locations back into world positions, or likely world rays.</span></span> 
4. <span data-ttu-id="f456d-287">이러한 세계 위치에 가상 모델 배치</span><span class="sxs-lookup"><span data-stu-id="f456d-287">Position your virtual models over these world locations</span></span>

<span data-ttu-id="f456d-288">몇 가지 중요 한 이미지 처리 링크:</span><span class="sxs-lookup"><span data-stu-id="f456d-288">Some important image-processing links:</span></span>
* [<span data-ttu-id="f456d-289">OpenCV</span><span class="sxs-lookup"><span data-stu-id="f456d-289">OpenCV</span></span>](https://opencv.org/)
* [<span data-ttu-id="f456d-290">QR 태그</span><span class="sxs-lookup"><span data-stu-id="f456d-290">QR Tags</span></span>](https://en.wikipedia.org/wiki/QR_code)
* [<span data-ttu-id="f456d-291">FaceSDK</span><span class="sxs-lookup"><span data-stu-id="f456d-291">FaceSDK</span></span>](https://research.microsoft.com/projects/facesdk/)
* [<span data-ttu-id="f456d-292">Microsoft Translator</span><span class="sxs-lookup"><span data-stu-id="f456d-292">Microsoft Translator</span></span>](https://www.microsoft.com/translator/business)

<span data-ttu-id="f456d-293">특히 장기 실행 이미지 인식 알고리즘을 처리할 때는 대화형 응용 프로그램 프레임 률을 유지 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-293">Keeping an interactive application frame-rate is critical, especially when dealing with long-running image recognition algorithms.</span></span> <span data-ttu-id="f456d-294">이러한 이유로 일반적으로 다음과 같은 패턴을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-294">For this reason, we commonly use the following pattern:</span></span>
1. <span data-ttu-id="f456d-295">주 스레드: 카메라 개체를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-295">Main Thread: manages the camera object</span></span>
2. <span data-ttu-id="f456d-296">주 스레드: 새 프레임 (비동기)을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-296">Main Thread: requests new frames (async)</span></span>
3. <span data-ttu-id="f456d-297">주 스레드: 추적 스레드에 새 프레임 전달</span><span class="sxs-lookup"><span data-stu-id="f456d-297">Main Thread: pass new frames to tracking thread</span></span>
4. <span data-ttu-id="f456d-298">추적 스레드: 키 요소를 수집 하는 이미지를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-298">Tracking Thread: processes image to collect key points</span></span>
5. <span data-ttu-id="f456d-299">주 스레드: 찾은 키 지점과 일치 하도록 가상 모델을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-299">Main Thread: moves virtual model to match found key points</span></span>
6. <span data-ttu-id="f456d-300">주 스레드: 2 단계에서 반복</span><span class="sxs-lookup"><span data-stu-id="f456d-300">Main Thread: repeat from step 2</span></span>

<span data-ttu-id="f456d-301">일부 이미지 표식 시스템은 단일 픽셀 위치만 제공 합니다 (다른 사용자는이 섹션이 필요 하지 않은 전체 변환을 제공 함) .이는 가능한 위치의 광선과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-301">Some image marker systems only provide a single pixel location (others provide the full transform in which case this section won't be needed), which equates to a ray of possible locations.</span></span> <span data-ttu-id="f456d-302">단일 3d 위치로 이동 하려면 여러 광선을 활용 하 여 대략적인 교차를 기준으로 최종 결과를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-302">To get to a single 3d location, we can then leverage multiple rays and find the final result by their approximate intersection.</span></span> <span data-ttu-id="f456d-303">이 작업을 수행하려면 다음 작업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-303">To do this, you'll need to:</span></span>
1. <span data-ttu-id="f456d-304">여러 카메라 이미지를 수집 하는 루프 가져오기</span><span class="sxs-lookup"><span data-stu-id="f456d-304">Get a loop going collecting multiple camera images</span></span>
2. <span data-ttu-id="f456d-305">연결 된 기능 지점과 해당 세계 광선 찾기</span><span class="sxs-lookup"><span data-stu-id="f456d-305">Find the associated feature points, and their world rays</span></span>
3. <span data-ttu-id="f456d-306">여러 가지 세계 광선을 포함 하는 기능 사전이 있는 경우 다음 코드를 사용 하 여 이러한 광선의 교차를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-306">When you have a dictionary of features, each with multiple world rays, you can use the following code to solve for the intersection of those rays:</span></span>

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

<span data-ttu-id="f456d-307">두 개 이상의 추적 된 태그 위치가 지정 된 경우 사용자의 현재 시나리오에 맞게 모델링 된 장면을 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-307">Given two or more tracked tag locations, you can position a modeled scene to fit the user's current scenario.</span></span> <span data-ttu-id="f456d-308">중력을 가정할 수 없는 경우 세 가지 태그 위치가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-308">If you can't assume gravity, then you'll need three tag locations.</span></span> <span data-ttu-id="f456d-309">대부분의 경우 흰색 구는 실시간 추적 된 태그 위치를 나타내고 파란색 구는 모델링 된 태그 위치를 나타내는 색 구성표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-309">In many cases, we use a color scheme where white spheres represent real-time tracked tag locations, and blue spheres represent modeled tag locations.</span></span> <span data-ttu-id="f456d-310">이를 통해 사용자는 맞춤 품질을 시각적으로 측정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-310">This allows the user to visually gauge the alignment quality.</span></span> <span data-ttu-id="f456d-311">모든 응용 프로그램에서 다음 설정을 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-311">We assume the following setup in all our applications:</span></span>
* <span data-ttu-id="f456d-312">두 개 이상의 모델링 한 태그 위치</span><span class="sxs-lookup"><span data-stu-id="f456d-312">Two or more modeled tag locations</span></span>
* <span data-ttu-id="f456d-313">장면에 있는 하나의 ' 보정 공간 '은 태그의 부모입니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-313">One 'calibration space', which in the scene is the parent of the tags</span></span>
* <span data-ttu-id="f456d-314">카메라 기능 식별자</span><span class="sxs-lookup"><span data-stu-id="f456d-314">Camera feature identifier</span></span>
* <span data-ttu-id="f456d-315">동작-보정 공간을 이동 하 여 모델링 된 태그를 실시간 태그에 맞춰 정렬 합니다. 즉, 다른 연결에 상대적인 위치에 있으므로 모델링 된 마커 자체가 아니라 부모 공간을 이동 하는 것은 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f456d-315">Behavior, which moves the calibration space to align the modeled tags with the real-time tags (we're careful to move the parent space, not the modeled markers themselves, because other connect is positions relative to them).</span></span>

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a><span data-ttu-id="f456d-316">Led 또는 다른 인식기 라이브러리를 사용 하 여 태그가 지정 된 고정 또는 실제 개체/얼굴 이동 추적 또는 식별</span><span class="sxs-lookup"><span data-stu-id="f456d-316">Track or Identify Tagged Stationary or Moving real-world objects/faces using LEDs or other recognizer libraries</span></span>

<span data-ttu-id="f456d-317">예제:</span><span class="sxs-lookup"><span data-stu-id="f456d-317">Examples:</span></span>
* <span data-ttu-id="f456d-318">Led가 있는 산업 로봇 (또는 느린 개체 이동에 대 한 QR 코드)</span><span class="sxs-lookup"><span data-stu-id="f456d-318">Industrial robots with LEDs (or QR codes for slower moving objects)</span></span>
* <span data-ttu-id="f456d-319">대화방의 개체 식별 및 인식</span><span class="sxs-lookup"><span data-stu-id="f456d-319">Identify and recognize objects in the room</span></span>
* <span data-ttu-id="f456d-320">대화방에서 사람을 식별 하 고 인식 합니다 (예: 얼굴에 holographic 접점 카드 배치).</span><span class="sxs-lookup"><span data-stu-id="f456d-320">Identify and recognize people in the room, for example placing holographic contact cards over faces</span></span>

## <a name="see-also"></a><span data-ttu-id="f456d-321">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f456d-321">See also</span></span>
* [<span data-ttu-id="f456d-322">과정이 카메라 샘플</span><span class="sxs-lookup"><span data-stu-id="f456d-322">Locatable camera sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [<span data-ttu-id="f456d-323">Unity의 위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="f456d-323">Locatable camera in Unity</span></span>](../unity/locatable-camera-in-unity.md)
* [<span data-ttu-id="f456d-324">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="f456d-324">Mixed reality capture</span></span>](/hololens/holographic-photos-and-videos)
* [<span data-ttu-id="f456d-325">개발자를 위한 혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="f456d-325">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="f456d-326">미디어 캡처 소개</span><span class="sxs-lookup"><span data-stu-id="f456d-326">Media capture introduction</span></span>](/windows/uwp/audio-video-camera/)
* [<span data-ttu-id="f456d-327">Holographic face 추적 샘플</span><span class="sxs-lookup"><span data-stu-id="f456d-327">Holographic face tracking sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)