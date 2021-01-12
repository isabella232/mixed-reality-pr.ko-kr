---
title: 관람자 보기
description: 외부 디바이스에서 홀로그램을 시각화하여 외부 디스플레이에 혼합 현실 환경을 표시하거나 기록합니다.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 관람자 보기, iPhone, iOS, iPad, OpenCV, 카메라, ARKit, HoloLens, Mixed Reality, Mixed Reality Toolkit, 데모, 레코드
ms.openlocfilehash: 1f61d2094ec2762ab22576d2eac85ed6bf81d5c7
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008613"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="7088b-104">HoloLens 및 HoloLens 2의 관람자 보기</span><span class="sxs-lookup"><span data-stu-id="7088b-104">Spectator View for HoloLens and HoloLens 2</span></span>

![표식](images/SpecViewPhoneHero.jpg)

<span data-ttu-id="7088b-106">HoloLens를 쓰고 있을 때는 HoloLens를 쓰고 있지 않은 다른 사람이 자신이 보는 것과 똑같은 경이로움을 경험할 수 없다는 사실을 잊기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="7088b-106">When you're wearing a HoloLens, it's easy to forget a person without one can't experience the same wonders you're seeing.</span></span> <span data-ttu-id="7088b-107">Spectator View를 사용하면 HoloLens 사용자가 보고 있는 것을 다른 사람도 2D 화면으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7088b-107">Spectator View lets others see what a HoloLens user sees on a 2D screen.</span></span> <span data-ttu-id="7088b-108">또한 모바일 디바이스를 사용하여 홀로그램을 HD로 녹화하고 비디오 카메라를 사용하여 홀로그램을 고화질로 녹화하는 것도 빠르고 경제적인 접근법입니다.</span><span class="sxs-lookup"><span data-stu-id="7088b-108">It's also a fast and affordable approach to recording holograms in HD with mobile devices and getting great quality recordings of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="7088b-109">주요 리소스</span><span class="sxs-lookup"><span data-stu-id="7088b-109">Key Resources</span></span>

* [<span data-ttu-id="7088b-110">**GitHub의 관람자 보기**</span><span class="sxs-lookup"><span data-stu-id="7088b-110">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="7088b-111">**관람자 보기 설명서**</span><span class="sxs-lookup"><span data-stu-id="7088b-111">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="7088b-112">**관람자 보기 샘플**</span><span class="sxs-lookup"><span data-stu-id="7088b-112">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="7088b-113">사용 사례</span><span class="sxs-lookup"><span data-stu-id="7088b-113">Use Cases</span></span>

* <span data-ttu-id="7088b-114">iPhone 또는 Android 디바이스를 사용하여 혼합 현실 환경을 녹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7088b-114">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="7088b-115">Full HD로 녹화하고 홀로그램과 그림자에 앤티앨리어싱을 적용하면 홀로그램 동영상을 경제적이고 빠르게 녹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7088b-115">Record in full HD and apply anti-aliasing to holograms and shadow for a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="7088b-116">라이브 혼합 현실 환경을 지연 없이 iPhone 또는 iPad에서 Apple TV로 직접 스트림합니다!</span><span class="sxs-lookup"><span data-stu-id="7088b-116">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="7088b-117">게스트와 경험을 공유합니다. 비 HoloLens 사용자가 휴대폰 또는 태블릿에서 홀로그램을 직접 경험할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7088b-117">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="7088b-118">현재 기능</span><span class="sxs-lookup"><span data-stu-id="7088b-118">Current Features</span></span>

* <span data-ttu-id="7088b-119">홀로그램의 공간 동기화를 통해 모든 사용자가 똑같은 장소에서 홀로그램을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7088b-119">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="7088b-120">iOS(ARKit 사용 디바이스) 및 Android(ARCore 사용 디바이스)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7088b-120">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="7088b-121">여러 iOS 게스트가 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7088b-121">Multiple iOS guests.</span></span>
<span data-ttu-id="7088b-122">비디오 + 홀로그램 + 주변 소리 + 홀로그램 소리를 녹화합니다.</span><span class="sxs-lookup"><span data-stu-id="7088b-122">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="7088b-123">비디오를 저장하거나, 이메일로 보내거나, 다른 지원 앱과 공유할 수 있도록 시트를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="7088b-123">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="7088b-124">![표식](images/SpecViewPhoneDemo.jpg)
![표식](images/hololensspectatorview-500px.jpg) ![표식](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="7088b-124">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="7088b-125">다음 표에는 다양한 관람자 보기 기능 및 해당 특성이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7088b-125">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="7088b-126">비디오 녹화 요구 사항에 가장 적합한 옵션을 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="7088b-126">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="7088b-127">기능</span><span class="sxs-lookup"><span data-stu-id="7088b-127">Functionality</span></span>                                | <span data-ttu-id="7088b-128">모바일</span><span class="sxs-lookup"><span data-stu-id="7088b-128">Mobile</span></span>                  |                    <span data-ttu-id="7088b-129">비디오 카메라</span><span class="sxs-lookup"><span data-stu-id="7088b-129">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="7088b-130">HD 품질</span><span class="sxs-lookup"><span data-stu-id="7088b-130">HD quality</span></span>                           |         <span data-ttu-id="7088b-131">Full HD</span><span class="sxs-lookup"><span data-stu-id="7088b-131">Full HD</span></span>         |        <span data-ttu-id="7088b-132">전문 품질 촬영(비디오 카메라)</span><span class="sxs-lookup"><span data-stu-id="7088b-132">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="7088b-133">간편한 카메라 이동</span><span class="sxs-lookup"><span data-stu-id="7088b-133">Easy camera movement</span></span>                 |            <span data-ttu-id="7088b-134">✔</span><span class="sxs-lookup"><span data-stu-id="7088b-134">✔</span></span>            |                      <span data-ttu-id="7088b-135">✔</span><span class="sxs-lookup"><span data-stu-id="7088b-135">✔</span></span>                      |
| <span data-ttu-id="7088b-136">3인칭 보기</span><span class="sxs-lookup"><span data-stu-id="7088b-136">Third-person view</span></span>                    |            <span data-ttu-id="7088b-137">✔</span><span class="sxs-lookup"><span data-stu-id="7088b-137">✔</span></span>            |                      <span data-ttu-id="7088b-138">✔</span><span class="sxs-lookup"><span data-stu-id="7088b-138">✔</span></span>                      |
| <span data-ttu-id="7088b-139">화면으로 스트리밍 가능</span><span class="sxs-lookup"><span data-stu-id="7088b-139">Can be streamed to screens</span></span>           |            <span data-ttu-id="7088b-140">✔</span><span class="sxs-lookup"><span data-stu-id="7088b-140">✔</span></span>            |                      <span data-ttu-id="7088b-141">✔</span><span class="sxs-lookup"><span data-stu-id="7088b-141">✔</span></span>                      |
| <span data-ttu-id="7088b-142">이식 가능</span><span class="sxs-lookup"><span data-stu-id="7088b-142">Portable</span></span>                             |            <span data-ttu-id="7088b-143">✔</span><span class="sxs-lookup"><span data-stu-id="7088b-143">✔</span></span>            |                                             |
| <span data-ttu-id="7088b-144">무선</span><span class="sxs-lookup"><span data-stu-id="7088b-144">Wireless</span></span>                             |            <span data-ttu-id="7088b-145">✔</span><span class="sxs-lookup"><span data-stu-id="7088b-145">✔</span></span>            |                                             |
| <span data-ttu-id="7088b-146">추가 필수 하드웨어</span><span class="sxs-lookup"><span data-stu-id="7088b-146">Additional required hardware</span></span>         |     <span data-ttu-id="7088b-147">Android 휴대폰, iPhone</span><span class="sxs-lookup"><span data-stu-id="7088b-147">Android phone, iPhone</span></span>    | <span data-ttu-id="7088b-148">HoloLens + 의장품 + 삼각대 + 비디오 카메라 + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="7088b-148">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="7088b-149">하드웨어 투자</span><span class="sxs-lookup"><span data-stu-id="7088b-149">Hardware investment</span></span>                  |           <span data-ttu-id="7088b-150">낮음</span><span class="sxs-lookup"><span data-stu-id="7088b-150">Low</span></span>            |                     <span data-ttu-id="7088b-151">높음</span><span class="sxs-lookup"><span data-stu-id="7088b-151">High</span></span>                    |
| <span data-ttu-id="7088b-152">플랫폼 간</span><span class="sxs-lookup"><span data-stu-id="7088b-152">Cross-platform</span></span>                       |           <span data-ttu-id="7088b-153">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="7088b-153">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="7088b-154">동기화된 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="7088b-154">Synchronized content</span></span>                 |            <span data-ttu-id="7088b-155">✔</span><span class="sxs-lookup"><span data-stu-id="7088b-155">✔</span></span>            |                      <span data-ttu-id="7088b-156">✔</span><span class="sxs-lookup"><span data-stu-id="7088b-156">✔</span></span>                      |
| <span data-ttu-id="7088b-157">런타임 설치 기간</span><span class="sxs-lookup"><span data-stu-id="7088b-157">Runtime setup duration</span></span>               |         <span data-ttu-id="7088b-158">인스턴트</span><span class="sxs-lookup"><span data-stu-id="7088b-158">Instant</span></span>          |                     <span data-ttu-id="7088b-159">느림</span><span class="sxs-lookup"><span data-stu-id="7088b-159">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="7088b-160">참조</span><span class="sxs-lookup"><span data-stu-id="7088b-160">See also</span></span>

* [<span data-ttu-id="7088b-161">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="7088b-161">Mixed reality capture</span></span>](../../mixed-reality-capture.md) 
* [<span data-ttu-id="7088b-162">개발자를 위한 혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="7088b-162">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="7088b-163">혼합 현실의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="7088b-163">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
