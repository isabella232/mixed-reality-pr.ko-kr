---
title: 관람자 보기
description: 외부 디바이스에서 홀로그램을 시각화하여 외부 디스플레이에 혼합 현실 환경을 표시하거나 기록합니다.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 관람자 보기, iPhone, iOS, iPad, OpenCV, 카메라, ARKit, HoloLens, Mixed Reality, Mixed Reality Toolkit, 데모, 레코드
ms.openlocfilehash: c344edea9b499bdff15d1d93e400b8be626a63b6
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530110"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="82caa-104">HoloLens 및 HoloLens 2의 관람자 보기</span><span class="sxs-lookup"><span data-stu-id="82caa-104">Spectator View for HoloLens and HoloLens 2</span></span>

![표식](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="82caa-106">개요</span><span class="sxs-lookup"><span data-stu-id="82caa-106">Overview</span></span>

<span data-ttu-id="82caa-107">HoloLens를 쓰고 있을 때는 HoloLens를 쓰고 있지 않은 다른 사람이 자신이 보는 것과 똑같은 경이로움을 경험할 수 없다는 사실을 잊기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="82caa-107">When you're wearing a HoloLens, it's easy to forget a person without one can't experience the same wonders you're seeing.</span></span> <span data-ttu-id="82caa-108">Spectator View를 사용하면 HoloLens 사용자가 보고 있는 것을 다른 사람도 2D 화면으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82caa-108">Spectator View lets others see what a HoloLens user sees on a 2D screen.</span></span> <span data-ttu-id="82caa-109">또한 모바일 디바이스를 사용하여 홀로그램을 HD로 녹화하고 비디오 카메라를 사용하여 홀로그램을 고화질로 녹화하는 것도 빠르고 경제적인 접근법입니다.</span><span class="sxs-lookup"><span data-stu-id="82caa-109">It's also a fast and affordable approach to recording holograms in HD with mobile devices and getting great quality recordings of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="82caa-110">주요 리소스</span><span class="sxs-lookup"><span data-stu-id="82caa-110">Key Resources</span></span>

* [<span data-ttu-id="82caa-111">**GitHub의 관람자 보기**</span><span class="sxs-lookup"><span data-stu-id="82caa-111">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="82caa-112">**관람자 보기 설명서**</span><span class="sxs-lookup"><span data-stu-id="82caa-112">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="82caa-113">**관람자 보기 샘플**</span><span class="sxs-lookup"><span data-stu-id="82caa-113">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="82caa-114">사용 사례</span><span class="sxs-lookup"><span data-stu-id="82caa-114">Use Cases</span></span>

* <span data-ttu-id="82caa-115">iPhone 또는 Android 디바이스를 사용하여 혼합 현실 환경을 녹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82caa-115">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="82caa-116">Full HD로 녹화하고 홀로그램과 그림자에 앤티앨리어싱을 적용하면 홀로그램 동영상을 경제적이고 빠르게 녹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82caa-116">Record in full HD and apply anti-aliasing to holograms and shadow for a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="82caa-117">라이브 혼합 현실 환경을 지연 없이 iPhone 또는 iPad에서 Apple TV로 직접 스트림합니다!</span><span class="sxs-lookup"><span data-stu-id="82caa-117">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="82caa-118">게스트와 경험을 공유합니다. 비 HoloLens 사용자가 휴대폰 또는 태블릿에서 홀로그램을 직접 경험할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="82caa-118">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="82caa-119">현재 기능</span><span class="sxs-lookup"><span data-stu-id="82caa-119">Current Features</span></span>

* <span data-ttu-id="82caa-120">홀로그램의 공간 동기화를 통해 모든 사용자가 똑같은 장소에서 홀로그램을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82caa-120">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="82caa-121">iOS(ARKit 사용 디바이스) 및 Android(ARCore 사용 디바이스)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="82caa-121">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="82caa-122">여러 iOS 게스트가 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82caa-122">Multiple iOS guests.</span></span>
<span data-ttu-id="82caa-123">비디오 + 홀로그램 + 주변 소리 + 홀로그램 소리를 녹화합니다.</span><span class="sxs-lookup"><span data-stu-id="82caa-123">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="82caa-124">비디오를 저장하거나, 이메일로 보내거나, 다른 지원 앱과 공유할 수 있도록 시트를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="82caa-124">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="82caa-125">![표식](images/SpecViewPhoneDemo.jpg)
![표식](images/hololensspectatorview-500px.jpg) ![표식](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="82caa-125">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="82caa-126">다음 표에는 다양한 관람자 보기 기능 및 해당 특성이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82caa-126">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="82caa-127">비디오 녹화 요구 사항에 가장 적합한 옵션을 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="82caa-127">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="82caa-128">기능</span><span class="sxs-lookup"><span data-stu-id="82caa-128">Functionality</span></span>                                | <span data-ttu-id="82caa-129">모바일</span><span class="sxs-lookup"><span data-stu-id="82caa-129">Mobile</span></span>                  |                    <span data-ttu-id="82caa-130">비디오 카메라</span><span class="sxs-lookup"><span data-stu-id="82caa-130">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="82caa-131">HD 품질</span><span class="sxs-lookup"><span data-stu-id="82caa-131">HD quality</span></span>                           |         <span data-ttu-id="82caa-132">Full HD</span><span class="sxs-lookup"><span data-stu-id="82caa-132">Full HD</span></span>         |        <span data-ttu-id="82caa-133">전문 품질 촬영(비디오 카메라)</span><span class="sxs-lookup"><span data-stu-id="82caa-133">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="82caa-134">간편한 카메라 이동</span><span class="sxs-lookup"><span data-stu-id="82caa-134">Easy camera movement</span></span>                 |            <span data-ttu-id="82caa-135">✔</span><span class="sxs-lookup"><span data-stu-id="82caa-135">✔</span></span>            |                      <span data-ttu-id="82caa-136">✔</span><span class="sxs-lookup"><span data-stu-id="82caa-136">✔</span></span>                      |
| <span data-ttu-id="82caa-137">3인칭 보기</span><span class="sxs-lookup"><span data-stu-id="82caa-137">Third-person view</span></span>                    |            <span data-ttu-id="82caa-138">✔</span><span class="sxs-lookup"><span data-stu-id="82caa-138">✔</span></span>            |                      <span data-ttu-id="82caa-139">✔</span><span class="sxs-lookup"><span data-stu-id="82caa-139">✔</span></span>                      |
| <span data-ttu-id="82caa-140">화면으로 스트리밍 가능</span><span class="sxs-lookup"><span data-stu-id="82caa-140">Can be streamed to screens</span></span>           |            <span data-ttu-id="82caa-141">✔</span><span class="sxs-lookup"><span data-stu-id="82caa-141">✔</span></span>            |                      <span data-ttu-id="82caa-142">✔</span><span class="sxs-lookup"><span data-stu-id="82caa-142">✔</span></span>                      |
| <span data-ttu-id="82caa-143">이식 가능</span><span class="sxs-lookup"><span data-stu-id="82caa-143">Portable</span></span>                             |            <span data-ttu-id="82caa-144">✔</span><span class="sxs-lookup"><span data-stu-id="82caa-144">✔</span></span>            |                                             |
| <span data-ttu-id="82caa-145">무선</span><span class="sxs-lookup"><span data-stu-id="82caa-145">Wireless</span></span>                             |            <span data-ttu-id="82caa-146">✔</span><span class="sxs-lookup"><span data-stu-id="82caa-146">✔</span></span>            |                                             |
| <span data-ttu-id="82caa-147">추가 필수 하드웨어</span><span class="sxs-lookup"><span data-stu-id="82caa-147">Additional required hardware</span></span>         |     <span data-ttu-id="82caa-148">Android 휴대폰, iPhone</span><span class="sxs-lookup"><span data-stu-id="82caa-148">Android phone, iPhone</span></span>    | <span data-ttu-id="82caa-149">HoloLens + 의장품 + 삼각대 + 비디오 카메라 + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="82caa-149">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="82caa-150">하드웨어 투자</span><span class="sxs-lookup"><span data-stu-id="82caa-150">Hardware investment</span></span>                  |           <span data-ttu-id="82caa-151">낮음</span><span class="sxs-lookup"><span data-stu-id="82caa-151">Low</span></span>            |                     <span data-ttu-id="82caa-152">높음</span><span class="sxs-lookup"><span data-stu-id="82caa-152">High</span></span>                    |
| <span data-ttu-id="82caa-153">플랫폼 간</span><span class="sxs-lookup"><span data-stu-id="82caa-153">Cross-platform</span></span>                       |           <span data-ttu-id="82caa-154">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="82caa-154">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="82caa-155">동기화된 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="82caa-155">Synchronized content</span></span>                 |            <span data-ttu-id="82caa-156">✔</span><span class="sxs-lookup"><span data-stu-id="82caa-156">✔</span></span>            |                      <span data-ttu-id="82caa-157">✔</span><span class="sxs-lookup"><span data-stu-id="82caa-157">✔</span></span>                      |
| <span data-ttu-id="82caa-158">런타임 설치 기간</span><span class="sxs-lookup"><span data-stu-id="82caa-158">Runtime setup duration</span></span>               |         <span data-ttu-id="82caa-159">인스턴트</span><span class="sxs-lookup"><span data-stu-id="82caa-159">Instant</span></span>          |                     <span data-ttu-id="82caa-160">느림</span><span class="sxs-lookup"><span data-stu-id="82caa-160">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="82caa-161">참조</span><span class="sxs-lookup"><span data-stu-id="82caa-161">See also</span></span>

* [<span data-ttu-id="82caa-162">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="82caa-162">Mixed reality capture</span></span>](../../mixed-reality-capture.md) 
* [<span data-ttu-id="82caa-163">개발자를 위한 혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="82caa-163">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="82caa-164">혼합 현실의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="82caa-164">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
