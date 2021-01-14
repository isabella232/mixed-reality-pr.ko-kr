---
title: 앱 품질 기준
description: 이 문서에서는 혼합 현실 앱의 품질에 영향을 주는 주요 요소에 대해 설명 합니다.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 앱 품질 기준, 혼합 현실, 혼합 현실 앱, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 8037b573f50ef1f1137a6c50913990fadf40e92e
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192681"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="d2d73-104">앱 품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-104">App quality criteria</span></span>

<span data-ttu-id="d2d73-105">이 문서에서는 혼합 현실 앱의 품질에 영향을 주는 주요 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="d2d73-106">각 요소에 대해 다음 정보가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-106">For each factor, the following information is provided</span></span>
* <span data-ttu-id="d2d73-107">개요 – 품질 요소와 중요 한 이유에 대 한 간단한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-107">Overview – a brief description of the quality factor and why it's important.</span></span>
* <span data-ttu-id="d2d73-108">장치 영향-영향을 받는 창 혼합 현실 장치의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-108">Device impact - which type of Window Mixed Reality device is affected.</span></span>
* <span data-ttu-id="d2d73-109">품질 기준 – 품질 요소를 평가 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="d2d73-110">방법 측정 – 문제를 측정 (또는 경험) 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="d2d73-111">권장 사항 – 더 나은 사용자 환경을 제공 하는 방법에 대 한 요약입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="d2d73-112">리소스-더 나은 앱 환경을 만드는 데 유용한 개발자 및 디자인 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="d2d73-113">프레임 율</span><span class="sxs-lookup"><span data-stu-id="d2d73-113">Frame rate</span></span>

<span data-ttu-id="d2d73-114">프레임 요금은 홀로그램 안정성 및 사용자 편안의 첫 번째 기둥입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="d2d73-115">권장 되는 목표 보다 낮은 프레임 속도로 holograms 표시 되 고 경험 believability에 부정적인 영향을 미치고 잠재적으로 눈 피로를 일으킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="d2d73-116">Windows Mixed Reality 몰입 형 헤드셋의 경험에 대 한 대상 프레임 요금은 지원 하는 Windows 혼합 현실 호환 Pc에 따라 60 Hz 또는 90 Hz입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets is either 60 Hz or 90 Hz depending on which Windows Mixed Reality Compatible PCs you're supporting.</span></span> <span data-ttu-id="d2d73-117">HoloLens의 경우 대상 프레임 률은 60 Hz입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-117">For HoloLens, the target frame rate is 60 Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d2d73-118">장치 영향</span><span class="sxs-lookup"><span data-stu-id="d2d73-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2d73-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d2d73-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2d73-121">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-121">✔️</span></span></td>
        <td><span data-ttu-id="d2d73-122">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d2d73-123">품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-123">Quality criteria</span></span>

|  <span data-ttu-id="d2d73-124">가장 좋음</span><span class="sxs-lookup"><span data-stu-id="d2d73-124">Best</span></span>  |  <span data-ttu-id="d2d73-125">평가</span><span class="sxs-lookup"><span data-stu-id="d2d73-125">Meets</span></span> |  <span data-ttu-id="d2d73-126">실패</span><span class="sxs-lookup"><span data-stu-id="d2d73-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="d2d73-127">앱이 대상 장치에 대 한 FPS (초당 프레임 수) 목표를 만족 하는 앱: HoloLens의 60 fps; 울트라 Pc의 90 fps; 기본 Pc의 경우 60 fps.</span><span class="sxs-lookup"><span data-stu-id="d2d73-127">The app consistently meets frames per second (FPS) goal for target device: 60 fps on HoloLens; 90 fps on Ultra PCs; and 60 fps on mainstream PCs.</span></span> | <span data-ttu-id="d2d73-128">앱은 코어 환경을 방해할 하지 않는 간헐적 프레임을 보유 하 고 있으며, FPS는 원하는 목표 보다 일관 되 게 유지 되지만 앱 환경을 방해 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-128">The app has intermittent frame drops not impeding the core experience, or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="d2d73-129">앱이 10 초 이내에 평균적으로 프레임 속도로 놓기가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-129">The app is experiencing a drop in frame rate on average every 10 seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="d2d73-130">측정 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-130">How to measure</span></span>

* <span data-ttu-id="d2d73-131">실시간 프레임 속도 그래프는 [Windows 장치 포털](using-the-windows-device-portal.md#system-performance) 의 "시스템 성능"에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="d2d73-132">개발 디버깅을 위해 앱에 프레임 주기 진단 카운터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="d2d73-133">샘플 카운터에 대 한 리소스를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2d73-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="d2d73-134">앱이 실행 되는 동안 한 쪽에서 쪽으로 이동 하 여 프레임 속도로 떨어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="d2d73-135">홀로그램에 예기치 않은 떨림 이동이 표시 되 면 프레임 속도가 낮거나 안정성 평면이 원인일 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d2d73-136">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d2d73-136">Recommendations</span></span>

* <span data-ttu-id="d2d73-137">개발 작업을 시작할 때 프레임 속도 카운터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="d2d73-138">프레임 속도로 놓기가 발생 하는 변경 내용을 평가 하 고 성능 버그로 적절 하 게 해결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="d2d73-139">리소스</span><span class="sxs-lookup"><span data-stu-id="d2d73-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d2d73-140">설명서</span><span class="sxs-lookup"><span data-stu-id="d2d73-140">Documentation</span></span>

* [<span data-ttu-id="d2d73-141">혼합 현실 성능 이해</span><span class="sxs-lookup"><span data-stu-id="d2d73-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="d2d73-142">홀로그램 안정성 및 프레임 속도</span><span class="sxs-lookup"><span data-stu-id="d2d73-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="d2d73-143">Asset performance 예산</span><span class="sxs-lookup"><span data-stu-id="d2d73-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="d2d73-144">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="d2d73-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d2d73-145">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="d2d73-145">Tools and tutorials</span></span>

* [<span data-ttu-id="d2d73-146">혼합 현실 도구 키트, FPS 카운터 표시</span><span class="sxs-lookup"><span data-stu-id="d2d73-146">Mixed Reality Toolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="d2d73-147">혼합 현실 도구 키트, 셰이더</span><span class="sxs-lookup"><span data-stu-id="d2d73-147">Mixed Reality Toolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="d2d73-148">외부 참조</span><span class="sxs-lookup"><span data-stu-id="d2d73-148">External references</span></span>

* [<span data-ttu-id="d2d73-149">Unity, 모바일 응용 프로그램 최적화</span><span class="sxs-lookup"><span data-stu-id="d2d73-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="d2d73-150">홀로그램 안정성</span><span class="sxs-lookup"><span data-stu-id="d2d73-150">Hologram stability</span></span>

<span data-ttu-id="d2d73-151">안정적인 holograms는 앱의 유용성 및 believability을 높이고 사용자에 게 더 편안한 보기 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="d2d73-152">홀로그램 안정성의 품질은 좋은 앱 개발과 장치에서 환경을 이해 (추적) 하는 기능으로 인해 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="d2d73-153">프레임 요금은 안정성의 첫 번째 기둥 이지만 다음을 비롯 한 다른 요인이 안정성에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="d2d73-154">안정화 평면 사용</span><span class="sxs-lookup"><span data-stu-id="d2d73-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="d2d73-155">공간 앵커에 대 한 거리</span><span class="sxs-lookup"><span data-stu-id="d2d73-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="d2d73-156">추적</span><span class="sxs-lookup"><span data-stu-id="d2d73-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="d2d73-157">장치 영향</span><span class="sxs-lookup"><span data-stu-id="d2d73-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2d73-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d2d73-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2d73-160">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d2d73-161">품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-161">Quality criteria</span></span>

|  <span data-ttu-id="d2d73-162">가장 좋음</span><span class="sxs-lookup"><span data-stu-id="d2d73-162">Best</span></span>  |  <span data-ttu-id="d2d73-163">평가</span><span class="sxs-lookup"><span data-stu-id="d2d73-163">Meets</span></span> |  <span data-ttu-id="d2d73-164">실패</span><span class="sxs-lookup"><span data-stu-id="d2d73-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d2d73-165">Holograms 지속적으로 안정적으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="d2d73-166">보조 콘텐츠에 예기치 않은 이동이 표시 됩니다. 예기치 않은 이동은 전체 앱 환경을 방해 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-166">Secondary content shows unexpected movement; or unexpected movement doesn't impede overall app experience.</span></span> | <span data-ttu-id="d2d73-167">프레임의 기본 콘텐츠에 예기치 않은 이동이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-167">Primary content in frame shows unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="d2d73-168">측정 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-168">How to measure</span></span>

<span data-ttu-id="d2d73-169">장치를 입고 하 고 환경을 확인 하는 동안 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="d2d73-170">한쪽에서 쪽으로 헤드를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-170">Move your head from side to side.</span></span> <span data-ttu-id="d2d73-171">Holograms가 예기치 않은 움직임을 표시 하는 경우 프레임 속도가 낮거나 초점면에 대 한 안정성 평면의 부적절 한 맞춤이 원인일 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-171">If the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="d2d73-172">Holograms 및 환경을 중심으로 이동 하 여 스윔 및 jumpiness와 같은 동작을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="d2d73-173">이 유형의 동작은 장치에서 환경을 추적 하지 않거나 공간 앵커에 대 한 거리를 발생 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="d2d73-174">프레임에 큰 holograms 여러 개 있는 경우 다양 한 수준에서 홀로그램 동작을 관찰 하 여 헤드 위치를 측면에서 쪽으로 이동 합니다. shakiness가 표시 되 면 안정화 평면으로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d2d73-175">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d2d73-175">Recommendations</span></span>

* <span data-ttu-id="d2d73-176">개발 작업을 시작할 때 프레임 속도 카운터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-176">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="d2d73-177">안정화 평면을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="d2d73-178">항상 앵커의 3 미터 내에 고정 된 holograms을 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="d2d73-179">환경이 적절 한 추적을 위해 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-179">Make sure your environment is set up for proper tracking.</span></span>
* <span data-ttu-id="d2d73-180">프레임 내에서 다양 한 초점면 수준에서 holograms을 방지 하기 위해 환경을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="d2d73-181">리소스</span><span class="sxs-lookup"><span data-stu-id="d2d73-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d2d73-182">설명서</span><span class="sxs-lookup"><span data-stu-id="d2d73-182">Documentation</span></span>

* [<span data-ttu-id="d2d73-183">홀로그램 안정성 및 프레임 속도</span><span class="sxs-lookup"><span data-stu-id="d2d73-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="d2d73-184">사례 연구, 안정화 평면 사용</span><span class="sxs-lookup"><span data-stu-id="d2d73-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="d2d73-185">혼합 현실 성능 이해</span><span class="sxs-lookup"><span data-stu-id="d2d73-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="d2d73-186">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="d2d73-186">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="d2d73-187">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="d2d73-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="d2d73-188">추적 오류 처리</span><span class="sxs-lookup"><span data-stu-id="d2d73-188">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="d2d73-189">고정 참조 프레임</span><span class="sxs-lookup"><span data-stu-id="d2d73-189">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d2d73-190">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="d2d73-190">Tools and tutorials</span></span>

* [<span data-ttu-id="d2d73-191">MR 부록 키트, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="d2d73-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="d2d73-192">실제 표면의 Holograms 위치</span><span class="sxs-lookup"><span data-stu-id="d2d73-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="d2d73-193">물리적 개체가 있는 holograms의 잘못 된 맞춤 (서로 관련 된 경우)은 holograms와 실제 세계의 비 합집합을 명확 하 게 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) are a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="d2d73-194">배치의 정확도는 시나리오의 요구 사항에 상대적 이어야 합니다. 예를 들어 일반 표면 배치에서는 공간 맵을 사용할 수 있지만 더 정확한 배치에서는 표식 및 보정을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d2d73-195">장치 영향</span><span class="sxs-lookup"><span data-stu-id="d2d73-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2d73-196"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-196"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d2d73-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2d73-198">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-198">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d2d73-199">품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-199">Quality criteria</span></span>

|  <span data-ttu-id="d2d73-200">가장 좋음</span><span class="sxs-lookup"><span data-stu-id="d2d73-200">Best</span></span>  |  <span data-ttu-id="d2d73-201">평가</span><span class="sxs-lookup"><span data-stu-id="d2d73-201">Meets</span></span> |  <span data-ttu-id="d2d73-202">실패</span><span class="sxs-lookup"><span data-stu-id="d2d73-202">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="d2d73-203">Holograms는 일반적으로 센티미터에서 인치 범위의 표면에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-203">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="d2d73-204">더 많은 정확성이 필요한 경우 앱은 앱 사양 내에서 공동 작업을 위한 효율적인 수단을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-204">If you need more accuracy, the app should provide an efficient means for collaboration within the app spec.</span></span> | <span data-ttu-id="d2d73-205">해당 없음</span><span class="sxs-lookup"><span data-stu-id="d2d73-205">NA</span></span> | <span data-ttu-id="d2d73-206">Holograms 화면 평면을 분리 하거나 화면에서 부동 상태로 표시 하 여 실제 대상 개체와 정렬 되지 않은 상태로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-206">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="d2d73-207">정확도가 필요한 경우 Holograms는 시나리오의 근접 사양을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-207">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d2d73-208">측정 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-208">How to measure</span></span>

* <span data-ttu-id="d2d73-209">공간 맵에 배치 된 Holograms는 화면 위 또는 아래에 크게 부동으로 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-209">Holograms that are placed on spatial map shouldn't appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="d2d73-210">정확한 배치가 필요한 Holograms에는 시나리오 요구 사항에 맞는 일종의 표식 및 보정 시스템이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-210">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d2d73-211">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d2d73-211">Recommendations</span></span>

* <span data-ttu-id="d2d73-212">공간 맵은 전체 자릿수가 필요 하지 않은 경우 화면에 개체를 배치 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-212">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="d2d73-213">최상의 정밀도를 위해 마커 또는 포스터를 사용 하 여 최종 보정에 대 한 holograms 및 Xbox 컨트롤러 (또는 일부 수동 맞춤 메커니즘)를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-213">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="d2d73-214">매우 큰 holograms을 논리적 부분으로 분리 하 고 각 부분을 표면에 정렬 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-214">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="d2d73-215">IPD (interpupillary distance)를 잘못 설정 하면 홀로그램 맞춤에도 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-215">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="d2d73-216">항상 사용자의 IPD으로 HoloLens를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-216">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="d2d73-217">리소스</span><span class="sxs-lookup"><span data-stu-id="d2d73-217">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d2d73-218">설명서</span><span class="sxs-lookup"><span data-stu-id="d2d73-218">Documentation</span></span>

* [<span data-ttu-id="d2d73-219">공간 매핑 배치</span><span class="sxs-lookup"><span data-stu-id="d2d73-219">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="d2d73-220">대화방 스캔 프로세스</span><span class="sxs-lookup"><span data-stu-id="d2d73-220">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="d2d73-221">공간 앵커 모범 사례</span><span class="sxs-lookup"><span data-stu-id="d2d73-221">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="d2d73-222">추적 오류 처리</span><span class="sxs-lookup"><span data-stu-id="d2d73-222">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="d2d73-223">Unity의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="d2d73-223">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="d2d73-224">Vuforia 개발 개요</span><span class="sxs-lookup"><span data-stu-id="d2d73-224">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d2d73-225">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="d2d73-225">Tools and tutorials</span></span>

* [<span data-ttu-id="d2d73-226">MR 도구 키트, 공간 매핑 라이브러리</span><span class="sxs-lookup"><span data-stu-id="d2d73-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="d2d73-227">MR 부록 키트, 포스터 보정 샘플</span><span class="sxs-lookup"><span data-stu-id="d2d73-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="d2d73-228">MR 부록 키트, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="d2d73-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="d2d73-229">외부 참조</span><span class="sxs-lookup"><span data-stu-id="d2d73-229">External references</span></span>

* [<span data-ttu-id="d2d73-230">Lowes 사례 연구, 전체 자릿수 맞춤</span><span class="sxs-lookup"><span data-stu-id="d2d73-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="d2d73-231">편안 하 게 영역 보기</span><span class="sxs-lookup"><span data-stu-id="d2d73-231">Viewing zone of comfort</span></span>

<span data-ttu-id="d2d73-232">앱 개발자는 다양 한 깊이에서 콘텐츠 및 holograms를 배치 하 여 사용자의 눈이 수렴 하는 위치를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="d2d73-233">Hololens를 입고 하는 사용자는 사용자 로부터 약 2.0 m 거리 만큼 떨어진 곳에서 화면을 고정 하 여 일반 이미지를 유지 하기 위해 항상 2.0 m에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-233">Users wearing HoloLens will always accommodate to 2.0 m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0 m away from the user.</span></span> <span data-ttu-id="d2d73-234">콘텐츠 깊이가 잘못 되 면 visual discomfort 또는 피로이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d2d73-235">장치 영향</span><span class="sxs-lookup"><span data-stu-id="d2d73-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2d73-236"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-236"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d2d73-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2d73-238">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d2d73-239">품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="d2d73-240">가장 좋음</span><span class="sxs-lookup"><span data-stu-id="d2d73-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="d2d73-241">2 m에 콘텐츠를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-241">Place content at 2 m.</span></span></li><li><span data-ttu-id="d2d73-242">Holograms를 2 m에 배치할 수 없고 수렴 및 범위 간 충돌을 피할 수 없는 경우 홀로그램 배치를 위한 최적의 영역은 1.25 m에서 5 m 사이입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-242">When holograms cannot be placed at 2 m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25 m and 5 m.</span></span></li><li><span data-ttu-id="d2d73-243">모든 경우에서 디자이너는 콘텐츠 크기 및 기본 배치 매개 변수를 조정 하는 것과 같이 사용자가 1 + m 자리를 상호 작용할 수 있도록 콘텐츠를 구조화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="d2d73-244">시나리오에 필요 하지 않는 한 클리핑 평면은 1 m부터 페이드 아웃 하 여 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-244">Unless not required by the scenario, a clipping plane should be implement with fade out starting at 1 m.</span></span></li><li><span data-ttu-id="d2d73-245">가장 작은 홀로그램을 더 자세히 관찰 해야 하는 경우에는 콘텐츠가 50 cm 보다 가까이 있지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-245">In cases where closer observation of a motionless hologram is required, the content shouldn't be closer than 50 cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="d2d73-246">평가</span><span class="sxs-lookup"><span data-stu-id="d2d73-246">Meets</span></span></td><td> <span data-ttu-id="d2d73-247">콘텐츠는 보기 및 동작 지침 내에 있지만 클리핑 평면을 부적절 하 게 사용 하거나 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d2d73-248">실패</span><span class="sxs-lookup"><span data-stu-id="d2d73-248">Fail</span></span> </td><td> <span data-ttu-id="d2d73-249">콘텐츠가 너무 가까이 표시 됩니다 (일반적으로 &lt; 1.25 m, 또는 &lt; holograms를 더 자세히 관찰 해야 하는 고정 된의 경우 50 cm).</span><span class="sxs-lookup"><span data-stu-id="d2d73-249">Content is presented too close (typically &lt;1.25 m, or &lt;50 cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="d2d73-250">측정 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-250">How to measure</span></span>

* <span data-ttu-id="d2d73-251">콘텐츠는 일반적으로 2 m 이상 이지만 1.25 보다 작거나 5 m 보다 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-251">Content should typically be 2 m away, but no closer than 1.25 or further than 5 m.</span></span>
* <span data-ttu-id="d2d73-252">몇 가지 예외를 제외 하 고, HoloLens 클리핑 렌더링 거리는 1 m에서 시작 하는 콘텐츠 페이드 아웃을 사용 하 여 85CM으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-252">With few exceptions, the HoloLens clipping render distance should be set to 85CM with fade out of content starting at 1 m.</span></span> <span data-ttu-id="d2d73-253">내용에 접근 하 고 클리핑 평면 효과를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="d2d73-254">고정 콘텐츠는 50 cm을 초과 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-254">Stationary content should not be closer than 50 cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d2d73-255">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d2d73-255">Recommendations</span></span>

* <span data-ttu-id="d2d73-256">2 m의 최적 보기 거리에 대 한 콘텐츠를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-256">Design content for the optimal viewing distance of 2 m.</span></span>
* <span data-ttu-id="d2d73-257">1 m에서 시작 하 여 콘텐츠의 페이드 아웃을 사용 하 여 클리핑 렌더링 거리를 85 cm으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-257">Set the clipping render distance to 85 cm with fade out of content starting at 1 m.</span></span>
* <span data-ttu-id="d2d73-258">자세히 보기를 필요로 하는 고정 된 holograms의 경우에는 클리핑 평면이 30 cm 보다 가까이 있지 않아야 하 고 페이드 아웃은 클리핑 평면에서 10 cm 이상 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30 cm and fade out should start at least 10 cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="d2d73-259">리소스</span><span class="sxs-lookup"><span data-stu-id="d2d73-259">Resources</span></span>

* [<span data-ttu-id="d2d73-260">렌더링 거리</span><span class="sxs-lookup"><span data-stu-id="d2d73-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="d2d73-261">Unity의 포커스 포인트</span><span class="sxs-lookup"><span data-stu-id="d2d73-261">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="d2d73-262">규모 실험</span><span class="sxs-lookup"><span data-stu-id="d2d73-262">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="d2d73-263">텍스트, 권장 글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="d2d73-263">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="d2d73-264">깊이 전환</span><span class="sxs-lookup"><span data-stu-id="d2d73-264">Depth switching</span></span>

<span data-ttu-id="d2d73-265">편안 하 게 발생 하는 문제 영역을 확인 하는 것에 관계 없이 사용자가 근거리 및 far 초점면 (holograms 및 실제 콘텐츠 포함) 사이에서 자주 또는 빠르게 전환 하는 요구는 oculomotor 피로 및 일반 discomfort으로 이어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d2d73-266">장치 영향</span><span class="sxs-lookup"><span data-stu-id="d2d73-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2d73-267"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-267"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d2d73-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2d73-269">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-269">✔️</span></span></td>
        <td><span data-ttu-id="d2d73-270">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d2d73-271">품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-271">Quality criteria</span></span>

|  <span data-ttu-id="d2d73-272">가장 좋음</span><span class="sxs-lookup"><span data-stu-id="d2d73-272">Best</span></span>  |  <span data-ttu-id="d2d73-273">평가</span><span class="sxs-lookup"><span data-stu-id="d2d73-273">Meets</span></span> |  <span data-ttu-id="d2d73-274">실패</span><span class="sxs-lookup"><span data-stu-id="d2d73-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d2d73-275">사용자가 자연스럽 게 refocus 하지 않는 제한 된 또는 자연 스러운 수준 전환.</span><span class="sxs-lookup"><span data-stu-id="d2d73-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="d2d73-276">갑작스러운 깊이 전환이는 핵심 이며 앱 환경 또는 예기치 않은 실제 콘텐츠로 인 한 급격 한 깊이 전환으로 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="d2d73-277">일관 된 깊이 전환 또는 앱 환경에 대 한 필수 또는 핵심이 아닌 급격 한 깊이 전환.</span><span class="sxs-lookup"><span data-stu-id="d2d73-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d2d73-278">측정 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-278">How to measure</span></span>

* <span data-ttu-id="d2d73-279">앱에서 사용자가 일관 되 게, 또는 갑자기 깊이 포커스를 변경 해야 하는 경우 깊이 전환 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d2d73-280">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d2d73-280">Recommendations</span></span>

* <span data-ttu-id="d2d73-281">일관 된 초점 평면에서 기본 콘텐츠를 유지 하 고 안정화 평면이 초점면와 일치 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="d2d73-282">그러면 oculomotor 피로 및 예기치 않은 홀로그램 이동이 완화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="d2d73-283">리소스</span><span class="sxs-lookup"><span data-stu-id="d2d73-283">Resources</span></span>

* [<span data-ttu-id="d2d73-284">렌더링 거리</span><span class="sxs-lookup"><span data-stu-id="d2d73-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="d2d73-285">Unity의 포커스 포인트</span><span class="sxs-lookup"><span data-stu-id="d2d73-285">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="d2d73-286">공간 음향 사용</span><span class="sxs-lookup"><span data-stu-id="d2d73-286">Use of spatial sound</span></span>

<span data-ttu-id="d2d73-287">Windows Mixed Reality에서 오디오 엔진은 방향, 거리 및 환경 시뮬레이션을 사용 하 여 3D 소리를 시뮬레이션 하 여 혼합 현실 환경의 aural 구성 요소를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="d2d73-288">개발자는 응용 프로그램에서 공간 소리를 사용 하 여 사용자를 중심으로 3 차원 공간 (구)의 소리를 convincingly 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3-dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="d2d73-289">이러한 소리는 실제 물리적 개체 또는 사용자 환경에서 혼합 현실 holograms에서 가져온 것 처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="d2d73-290">공간 사운드는 혼합 현실 응용 프로그램에서 집중 교육, 접근성 및 UX 디자인을 위한 강력한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d2d73-291">장치 영향</span><span class="sxs-lookup"><span data-stu-id="d2d73-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2d73-292"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-292"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d2d73-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2d73-294">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-294">✔️</span></span></td>
        <td><span data-ttu-id="d2d73-295">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d2d73-296">품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-296">Quality criteria</span></span>

|  <span data-ttu-id="d2d73-297">가장 좋음</span><span class="sxs-lookup"><span data-stu-id="d2d73-297">Best</span></span>  |  <span data-ttu-id="d2d73-298">평가</span><span class="sxs-lookup"><span data-stu-id="d2d73-298">Meets</span></span> |  <span data-ttu-id="d2d73-299">실패</span><span class="sxs-lookup"><span data-stu-id="d2d73-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d2d73-300">소리는 논리적으로 spatialized UX는 소리를 적절 하 게 사용 하 여 개체 검색 및 사용자 피드백을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="d2d73-301">소리는 자연스럽 고 개체와 관련이 있으며 시나리오 전체에서 정규화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="d2d73-302">공간 오디오는 believability에 적합 하 게 사용 되지만 사용자 의견 및 검색 기능을 지원 하기 위한 수단으로는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="d2d73-303">소리는 예상 대로 spatialized 되지 않으며 UX 내에서 사용자를 지원 하기 위해 소리가 부족할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="d2d73-304">또는 공간 오디오는 시나리오 디자인에서 고려 되지 않았거나 사용 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d2d73-305">측정 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-305">How to measure</span></span>

* <span data-ttu-id="d2d73-306">일반적으로 관련 소리는 대상 holograms에서 내보내야 합니다 (예: holographic dog에서 오는 짖 소리).</span><span class="sxs-lookup"><span data-stu-id="d2d73-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="d2d73-307">사용자에 게 holographic 프레임 외부의 작업을 인식 하거나 피드백을 제공할 수 있도록 UX 전체에서 사운드 신호를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d2d73-308">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d2d73-308">Recommendations</span></span>

* <span data-ttu-id="d2d73-309">공간 오디오를 사용 하 여 개체 검색 및 사용자 인터페이스를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="d2d73-310">실제 소리는 합성 또는 비 자연 음향 보다 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="d2d73-311">대부분의 소리는 spatialized 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="d2d73-312">보이지 않는 송신기를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="d2d73-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="d2d73-313">공간 마스킹을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="d2d73-314">모든 소리를 표준화 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="d2d73-315">리소스</span><span class="sxs-lookup"><span data-stu-id="d2d73-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d2d73-316">설명서</span><span class="sxs-lookup"><span data-stu-id="d2d73-316">Documentation</span></span>

* [<span data-ttu-id="d2d73-317">공간 음향</span><span class="sxs-lookup"><span data-stu-id="d2d73-317">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="d2d73-318">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="d2d73-318">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="d2d73-319">Unity의 공간 음향</span><span class="sxs-lookup"><span data-stu-id="d2d73-319">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="d2d73-320">사례 연구, HoloTour에 대 한 공간 음향</span><span class="sxs-lookup"><span data-stu-id="d2d73-320">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="d2d73-321">사례 연구, RoboRaid에서 공간 소리 사용</span><span class="sxs-lookup"><span data-stu-id="d2d73-321">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d2d73-322">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="d2d73-322">Tools and tutorials</span></span>

* [<span data-ttu-id="d2d73-323">혼합 현실 도구 키트-공간 오디오</span><span class="sxs-lookup"><span data-stu-id="d2d73-323">Mixed Reality Toolkit - Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="d2d73-324">FOV (holographic frame) 경계에 집중</span><span class="sxs-lookup"><span data-stu-id="d2d73-324">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="d2d73-325">잘 디자인 된 사용자 환경은 사용자를 중심으로 확장 되는 가상 환경의 유용한 컨텍스트를 만들고 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-325">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="d2d73-326">FOV 경계의 효과를 완화 하는 것은 콘텐츠 크기 조정 및 컨텍스트, 공간 오디오, 지침 시스템 및 사용자 위치의 사용에 대 한 자세한 디자인을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-326">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="d2d73-327">이 작업을 수행 하는 경우 사용자는 편안 하 게 앱 환경을 사용 하는 동안 FOV 경계에 의해 손상 된 것을 느낄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-327">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d2d73-328">장치 영향</span><span class="sxs-lookup"><span data-stu-id="d2d73-328">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2d73-329"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-329"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d2d73-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2d73-331">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-331">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d2d73-332">품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-332">Quality criteria</span></span>

|  <span data-ttu-id="d2d73-333">가장 좋음</span><span class="sxs-lookup"><span data-stu-id="d2d73-333">Best</span></span>  |  <span data-ttu-id="d2d73-334">평가</span><span class="sxs-lookup"><span data-stu-id="d2d73-334">Meets</span></span> |  <span data-ttu-id="d2d73-335">실패</span><span class="sxs-lookup"><span data-stu-id="d2d73-335">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d2d73-336">사용자는 컨텍스트를 손실 하지 않으며 보기는 편안 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-336">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="d2d73-337">대량 개체에 대 한 컨텍스트 지원이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-337">Context assistance is provided for large objects.</span></span> <span data-ttu-id="d2d73-338">프레임 외부 개체에 대 한 검색 가능성 및 보기 지침이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-338">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="d2d73-339">일반적으로 holograms의 동작 디자인과 크기는 편안 하 게 볼 수 있는 환경에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-339">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="d2d73-340">사용자는 컨텍스트를 손실 하지 않지만 제한 된 상황에서는 추가 목 모션이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-340">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="d2d73-341">제한 된 상황에서 크기 조정으로 인해 holograms는 수직 또는 수평 프레임을 중단 하 여 holograms를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-341">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="d2d73-342">Holograms를 보려면 컨텍스트를 손실 하 고/또는 일관성 있는 목 모션이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-342">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="d2d73-343">큰 holographic 개체에 대 한 컨텍스트 지침이 없습니다. 검색 지침이 없는 프레임 외부에서 개체를 이동 하는 것이 불가능 하거나, 긴 holograms를 보려면 일반적인 목 모션이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-343">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d2d73-344">측정 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-344">How to measure</span></span>

* <span data-ttu-id="d2d73-345">(규모가 큼) 홀로그램의 컨텍스트가 손실 되거나 경계에서 잘릴 수 있으므로 인식 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-345">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="d2d73-346">Holograms의 위치는 holographic 프레임에서 빠르게 이동 하는 관심 있는 감독 또는 콘텐츠가 부족 하기 때문에 찾기가 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-346">Locations of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="d2d73-347">시나리오를 수행 하려면 일반적인 및 반복적인 위쪽 및 아래쪽 헤드 동작을 수행 하 여 홀로그램을 피로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-347">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d2d73-348">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d2d73-348">Recommendations</span></span>

* <span data-ttu-id="d2d73-349">FOV에 맞는 작은 개체를 사용 하 여 환경을 시작한 다음 시각적 신호를 사용 하 여 더 큰 버전으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-349">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="d2d73-350">공간 오디오 및 주의 감독을 사용 하면 사용자가 FOV 외부에 있는 콘텐츠를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-350">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="d2d73-351">가능 하면 FOV를 수직으로 자르는 holograms을 피합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-351">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="d2d73-352">최상의 보기 위치를 위해 사용자에 게 앱 내 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-352">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="d2d73-353">리소스</span><span class="sxs-lookup"><span data-stu-id="d2d73-353">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d2d73-354">설명서</span><span class="sxs-lookup"><span data-stu-id="d2d73-354">Documentation</span></span>

* [<span data-ttu-id="d2d73-355">홀로그램 프레임</span><span class="sxs-lookup"><span data-stu-id="d2d73-355">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="d2d73-356">사례 연구, HoloStudio UI 및 상호 작용 디자인 학습</span><span class="sxs-lookup"><span data-stu-id="d2d73-356">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="d2d73-357">개체 및 환경의 크기 조정</span><span class="sxs-lookup"><span data-stu-id="d2d73-357">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="d2d73-358">커서, 시각적 신호</span><span class="sxs-lookup"><span data-stu-id="d2d73-358">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="d2d73-359">외부 참조</span><span class="sxs-lookup"><span data-stu-id="d2d73-359">External references</span></span>

* [<span data-ttu-id="d2d73-360">FOV에 대 한 많은 ado</span><span class="sxs-lookup"><span data-stu-id="d2d73-360">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="d2d73-361">사용자 위치에 반응 하는 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="d2d73-361">Content reacts to user position</span></span>

<span data-ttu-id="d2d73-362">Holograms은 "실제" 개체와 거의 동일한 방식으로 사용자의 위치에 대응 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-362">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="d2d73-363">주목할 만한 디자인 고려 사항은 사용자의 위치를 고정 하 고 사용자의 동작에 맞게 조정할 수 있는 UI 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-363">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="d2d73-364">사용자 위치에 맞게 올바르게 조정 되는 앱을 디자인 하면 더 이익은 환경을 만들고 더 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-364">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d2d73-365">장치 영향</span><span class="sxs-lookup"><span data-stu-id="d2d73-365">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2d73-366"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-366"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d2d73-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2d73-368">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-368">✔️</span></span></td>
        <td><span data-ttu-id="d2d73-369">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-369">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d2d73-370">품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-370">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="d2d73-371">가장 좋음</span><span class="sxs-lookup"><span data-stu-id="d2d73-371">Best</span></span> </td><td> <span data-ttu-id="d2d73-372">사용자가 필요한 사용자 이동 범위 내에서 사용자가 자연스럽 게 콘텐츠와 상호 작용할 수 있도록 콘텐츠와 UI가 사용자 위치에 맞게 조정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-372">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d2d73-373">평가</span><span class="sxs-lookup"><span data-stu-id="d2d73-373">Meets</span></span> </td><td> <span data-ttu-id="d2d73-374">UI는 사용자 위치에 맞게 조정 되지만 사용자의 위치를 조정 해야 하는 주요 콘텐츠 보기를 방해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-374">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d2d73-375">실패</span><span class="sxs-lookup"><span data-stu-id="d2d73-375">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="d2d73-376">UI 요소는 이동 하는 동안 손실 되거나 잠기므로 사용자가 컨트롤로 반환 (또는 찾기) 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-376">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="d2d73-377">UI 요소는 기본 콘텐츠 보기를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-377">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="d2d73-378">UI 이동은 특히 <a href="../../design/billboarding-and-tag-along.md">태그 동반</a> ui 요소를 사용 하 여 거리 및 모멘텀을 보기 위해 최적화 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-378">UI movement isn't optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="d2d73-379">측정 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-379">How to measure</span></span>

* <span data-ttu-id="d2d73-380">모든 측정값은 시나리오의 적절 한 범위 내에서 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-380">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="d2d73-381">사용자 이동이 다를 수 있지만 응용 프로그램을 실행 하는 데는 극단적인 사용자 이동이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-381">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="d2d73-382">UI 요소의 경우 사용자 이동에 관계 없이 관련 컨트롤을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-382">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="d2d73-383">예를 들어 사용자가 확대/축소를 사용 하 여 3D 맵을 보고 탐색 하는 경우 위치에 관계 없이 사용자가 확대/축소 컨트롤을 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-383">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d2d73-384">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d2d73-384">Recommendations</span></span>

* <span data-ttu-id="d2d73-385">사용자가 카메라 이며 이동을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-385">The user is the camera and they control the movement.</span></span> <span data-ttu-id="d2d73-386">드라이브를 사용 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-386">Let them drive.</span></span>
* <span data-ttu-id="d2d73-387">다른 방법으로는 사용자가 이동 하는 경우에는 전 세계에 잠그거나 가려져 없는 텍스트 및 menuing 시스템에 대해 billboarding을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-387">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="d2d73-388">사용자가 앞에 있는 내용을 볼 수 있도록 허용 하면서 사용자를 따라야 하는 콘텐츠에 태그를 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-388">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="d2d73-389">리소스</span><span class="sxs-lookup"><span data-stu-id="d2d73-389">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d2d73-390">설명서</span><span class="sxs-lookup"><span data-stu-id="d2d73-390">Documentation</span></span>

* [<span data-ttu-id="d2d73-391">상호 작용 디자인</span><span class="sxs-lookup"><span data-stu-id="d2d73-391">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="d2d73-392">색, 광원 및 재질</span><span class="sxs-lookup"><span data-stu-id="d2d73-392">Color, light, and material</span></span>](../../color,-light-and-materials.md)
* [<span data-ttu-id="d2d73-393">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="d2d73-393">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="d2d73-394">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="d2d73-394">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="d2d73-395">자체 모션 및 사용자 보행</span><span class="sxs-lookup"><span data-stu-id="d2d73-395">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="d2d73-396">입력 상호 작용 명확성</span><span class="sxs-lookup"><span data-stu-id="d2d73-396">Input interaction clarity</span></span>

<span data-ttu-id="d2d73-397">입력 상호 작용의 명확성은 앱의 유용성에 매우 중요 하며, 입력 일관성, approachability, 상호 작용 메서드의 검색 기능을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-397">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="d2d73-398">사용자는 재설정 없이 플랫폼 전체의 공통 상호 작용을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-398">User can use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="d2d73-399">앱에 사용자 지정 입력이 있는 경우 명확 하 게 통신 하 고 설명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-399">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d2d73-400">장치 영향</span><span class="sxs-lookup"><span data-stu-id="d2d73-400">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2d73-401"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-401"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d2d73-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2d73-403">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-403">✔️</span></span></td>
        <td><span data-ttu-id="d2d73-404">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-404">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d2d73-405">품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-405">Quality criteria</span></span>

|  <span data-ttu-id="d2d73-406">가장 좋음</span><span class="sxs-lookup"><span data-stu-id="d2d73-406">Best</span></span>  |  <span data-ttu-id="d2d73-407">평가</span><span class="sxs-lookup"><span data-stu-id="d2d73-407">Meets</span></span> |  <span data-ttu-id="d2d73-408">실패</span><span class="sxs-lookup"><span data-stu-id="d2d73-408">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d2d73-409">입력 상호 작용 방법은 Windows Mixed Reality 제공 [지침](../../design/interaction-fundamentals.md)과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-409">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="d2d73-410">표준 상호 작용을 사용 하는 대신 표준 입력을 사용 하 여 모든 사용자 지정 입력을 중복 해서는 안 되며, 사용자에 게 명확 하 게 전달 하 여 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-410">Any custom input shouldn't be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="d2d73-411">가장 좋지만 사용자 지정 입력은 표준 입력 방법으로 중복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-411">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="d2d73-412">사용자는 여전히 앱 환경을 통해 목표와 진행 상황을 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-412">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="d2d73-413">입력 방법 또는 단추 매핑을 이해 하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-413">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="d2d73-414">입력은 과도 하 게 사용자 지정 되므로 표준 입력을 지원 하지 않거나 지침이 없거나 피로 및 편안 하 게 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-414">Input is heavily customized, doesn't support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d2d73-415">측정 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-415">How to measure</span></span>

* <span data-ttu-id="d2d73-416">앱은 일관 된 [표준 입력 메서드를 사용 합니다.](../../design/interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="d2d73-416">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="d2d73-417">앱에 사용자 지정 입력이 있는 경우 다음을 통해 명확 하 게 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-417">If the app has custom input, it's clearly communicated through:</span></span>
* <span data-ttu-id="d2d73-418">첫 실행 환경</span><span class="sxs-lookup"><span data-stu-id="d2d73-418">First-run experience</span></span>
* <span data-ttu-id="d2d73-419">소개 화면</span><span class="sxs-lookup"><span data-stu-id="d2d73-419">Introductory screens</span></span>
* <span data-ttu-id="d2d73-420">도구 설명</span><span class="sxs-lookup"><span data-stu-id="d2d73-420">Tooltips</span></span>
* <span data-ttu-id="d2d73-421">핸드 코치</span><span class="sxs-lookup"><span data-stu-id="d2d73-421">Hand coach</span></span>
* <span data-ttu-id="d2d73-422">도움말 섹션</span><span class="sxs-lookup"><span data-stu-id="d2d73-422">Help section</span></span>
* <span data-ttu-id="d2d73-423">음성</span><span class="sxs-lookup"><span data-stu-id="d2d73-423">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="d2d73-424">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d2d73-424">Recommendations</span></span>

* <span data-ttu-id="d2d73-425">가능 하면 표준 입력 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-425">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="d2d73-426">비표준 입력 방법에 대 한 데모, 자습서 및 도구 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-426">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="d2d73-427">응용 프로그램 전체에서 일관 된 상호 작용 모델을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-427">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="d2d73-428">리소스</span><span class="sxs-lookup"><span data-stu-id="d2d73-428">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d2d73-429">설명서</span><span class="sxs-lookup"><span data-stu-id="d2d73-429">Documentation</span></span>

* [<span data-ttu-id="d2d73-430">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="d2d73-430">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="d2d73-431">Interactable 개체</span><span class="sxs-lookup"><span data-stu-id="d2d73-431">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="d2d73-432">헤드 게이즈 및 유지</span><span class="sxs-lookup"><span data-stu-id="d2d73-432">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="d2d73-433">커서</span><span class="sxs-lookup"><span data-stu-id="d2d73-433">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="d2d73-434">편안 함 및 응시</span><span class="sxs-lookup"><span data-stu-id="d2d73-434">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="d2d73-435">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="d2d73-435">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="d2d73-436">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="d2d73-436">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="d2d73-437">Unity 입력 포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="d2d73-437">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="d2d73-438">Unity의 키보드 입력</span><span class="sxs-lookup"><span data-stu-id="d2d73-438">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="d2d73-439">Unity의 응시</span><span class="sxs-lookup"><span data-stu-id="d2d73-439">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="d2d73-440">Unity의 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="d2d73-440">Motion controllers in Unity</span></span>](../unity/motion-controllers-in-unity.md)
* [<span data-ttu-id="d2d73-441">Unity의 제스처</span><span class="sxs-lookup"><span data-stu-id="d2d73-441">Gestures in Unity</span></span>](../unity/gestures-in-unity.md)
* [<span data-ttu-id="d2d73-442">Unity의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="d2d73-442">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="d2d73-443">DirectX의 키보드, 마우스 및 컨트롤러 입력</span><span class="sxs-lookup"><span data-stu-id="d2d73-443">Keyboard, mouse, and controller input in DirectX</span></span>](../../keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="d2d73-444">DirectX의 헤드 및 눈 응시</span><span class="sxs-lookup"><span data-stu-id="d2d73-444">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="d2d73-445">DirectX의 헤드 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="d2d73-445">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="d2d73-446">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="d2d73-446">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d2d73-447">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="d2d73-447">Tools and tutorials</span></span>

* [<span data-ttu-id="d2d73-448">사례 연구: 더 많은 개인 컴퓨팅</span><span class="sxs-lookup"><span data-stu-id="d2d73-448">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="d2d73-449">캐스트 연구: HoloStudio UI 및 상호 작용 디자인 학습</span><span class="sxs-lookup"><span data-stu-id="d2d73-449">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="d2d73-450">샘플 앱: 요소의 주기적 테이블</span><span class="sxs-lookup"><span data-stu-id="d2d73-450">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="d2d73-451">샘플 앱: 음력 모듈</span><span class="sxs-lookup"><span data-stu-id="d2d73-451">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="d2d73-452">Interactable 개체</span><span class="sxs-lookup"><span data-stu-id="d2d73-452">Interactable objects</span></span>

<span data-ttu-id="d2d73-453">단추는 긴 2D 추상 세계에서 이벤트를 트리거하는 데 사용 되는 비유입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-453">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="d2d73-454">3 차원 혼합 현실 세계에서는 이러한 추상화의 목표로 더 이상 국한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-454">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="d2d73-455">모든 항목은 이벤트를 트리거하는 Interactable 개체 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-455">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="d2d73-456">Interactable 개체는 테이블의 커피에서 공기의 풍선 부동으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-456">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="d2d73-457">Interactable 개체는 폼에 관계 없이 시각적 및 오디오 큐를 통해 사용자가 명확 하 게 인식할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-457">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d2d73-458">장치 영향</span><span class="sxs-lookup"><span data-stu-id="d2d73-458">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2d73-459"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-459"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d2d73-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2d73-461">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-461">✔️</span></span></td>
        <td><span data-ttu-id="d2d73-462">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-462">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d2d73-463">품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-463">Quality criteria</span></span>

|  <span data-ttu-id="d2d73-464">가장 좋음</span><span class="sxs-lookup"><span data-stu-id="d2d73-464">Best</span></span>  |  <span data-ttu-id="d2d73-465">평가</span><span class="sxs-lookup"><span data-stu-id="d2d73-465">Meets</span></span> |  <span data-ttu-id="d2d73-466">실패</span><span class="sxs-lookup"><span data-stu-id="d2d73-466">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d2d73-467">폼에 관계 없이 interactable 개체는 유휴 상태, 대상 지정 및 선택 됨의 세 가지 상태에서 시각적 및 오디오 큐를 통해 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-467">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="d2d73-468">"이 항목을 참조 하세요." 라는 것은 전체 환경에서 명확 하 고 일관 되 게 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-468">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="d2d73-469">개체를 확장 하 고 배포 하 여 오류를 자유롭게 대상으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-469">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="d2d73-470">사용자는 오디오 또는 시각적 피드백을 통해 interactable로 개체를 인식할 수 있으며 개체를 대상으로 하 고 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-470">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="d2d73-471">시각적 개체 또는 오디오 신호를 제공 하지 않으면 사용자가 interactable 개체를 인식할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-471">Given no visual or audio cues, user can't recognize an interactable object.</span></span> <span data-ttu-id="d2d73-472">개체 확장 또는 개체 간 거리 때문에 오류가 발생 하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-472">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d2d73-473">측정 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-473">How to measure</span></span>

* <span data-ttu-id="d2d73-474">Interactable 개체는 ' Interactable '로 인식할 수 있습니다. 단추, 메뉴 및 앱 별 콘텐츠를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-474">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app-specific content.</span></span> <span data-ttu-id="d2d73-475">이에 대 한 규칙은 interactable 개체를 대상으로 지정할 때 시각 및 오디오 큐가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-475">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d2d73-476">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d2d73-476">Recommendations</span></span>

* <span data-ttu-id="d2d73-477">시각적 개체와 오디오 피드백을 사용 하 여 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-477">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="d2d73-478">각 입력 상태 (유휴 상태, 대상 지정, 선택 됨)에 대해 시각적 피드백을 구분 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-478">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="d2d73-479">Interactable 개체의 크기를 조정 하 고 오류를 자유롭게 대상으로 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-479">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="d2d73-480">그룹화 된 interactable 개체 (예: 메뉴 모음 또는 목록)에는 대상 지정을 위한 적절 한 간격이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-480">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="d2d73-481">음성 명령을 지 원하는 단추 및 메뉴는 명령 키워드 ("참조)에 대 한 텍스트 레이블을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-481">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="d2d73-482">리소스</span><span class="sxs-lookup"><span data-stu-id="d2d73-482">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d2d73-483">설명서</span><span class="sxs-lookup"><span data-stu-id="d2d73-483">Documentation</span></span>

* [<span data-ttu-id="d2d73-484">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="d2d73-484">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="d2d73-485">Unity의 텍스트</span><span class="sxs-lookup"><span data-stu-id="d2d73-485">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="d2d73-486">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="d2d73-486">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="d2d73-487">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="d2d73-487">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d2d73-488">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="d2d73-488">Tools and tutorials</span></span>

* [<span data-ttu-id="d2d73-489">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="d2d73-489">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="d2d73-490">대화방 스캔</span><span class="sxs-lookup"><span data-stu-id="d2d73-490">Room scanning</span></span>

<span data-ttu-id="d2d73-491">공간 매핑 데이터를 필요로 하는 앱은 사용자가 장치를 활성화 하 여 환경을 탐색 하는 동안 시간 및 세션 간에이 데이터를 자동으로 수집 하는 장치에 의존 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-491">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="d2d73-492">이 데이터의 완성도와 품질은 사용자가 수행한 탐색 크기, 탐색 이후 경과 된 시간, 장치에서 영역을 스캔 한 후 가구 및 문과 같은 개체가 이동 했는지 여부를 포함 하는 다양 한 요인에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-492">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="d2d73-493">많은 앱은 사용자가 공간 맵의 완전성 및 품질을 개선 하기 위해 추가 단계를 수행 해야 하는지 여부를 판단 하기 위해 경험을 시작할 때 공간 매핑 데이터를 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-493">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="d2d73-494">사용자가 환경을 검색 해야 하는 경우 검사 하는 동안 지침이 제공 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-494">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d2d73-495">장치 영향</span><span class="sxs-lookup"><span data-stu-id="d2d73-495">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2d73-496"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-496"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d2d73-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2d73-498">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-498">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d2d73-499">품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-499">Quality criteria</span></span>

|  <span data-ttu-id="d2d73-500">가장 좋음</span><span class="sxs-lookup"><span data-stu-id="d2d73-500">Best</span></span>  |  <span data-ttu-id="d2d73-501">평가</span><span class="sxs-lookup"><span data-stu-id="d2d73-501">Meets</span></span> |  <span data-ttu-id="d2d73-502">실패</span><span class="sxs-lookup"><span data-stu-id="d2d73-502">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d2d73-503">사용자 검사가 진행 중 이라고 알려주는 공간 메시의 시각화입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-503">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="d2d73-504">사용자가 수행할 작업과 검사가 시작 및 중지 되는 시기를 명확 하 게 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-504">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="d2d73-505">공간 메시의 시각화가 제공 되지만 사용자가 수행할 작업을 명확 하 게 알지 못할 수 있으며 진행 정보는 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-505">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="d2d73-506">메시의 시각화가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-506">No visualization of mesh.</span></span> <span data-ttu-id="d2d73-507">찾을 위치와 관련 하 여 사용자에 게 제공 되는 지침 정보가 없습니다. 검색을 시작/중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-507">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="d2d73-508">측정 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-508">How to measure</span></span>

* <span data-ttu-id="d2d73-509">필요한 방 스캔 중에는 찾을 위치와 검사를 시작 및 중지 하는 시기를 나타내는 시각적 개체와 오디오 지침이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-509">During a required room scan, visual and audio guidance are provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d2d73-510">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d2d73-510">Recommendations</span></span>

* <span data-ttu-id="d2d73-511">사용자가 환경에 포함 해야 하는 총 볼륨의 크기를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-511">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="d2d73-512">검사가 시작 되 면 통신 하 고 진행률 표시기와 같은 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-512">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="d2d73-513">검색 중에 메시의 시각화를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-513">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="d2d73-514">사용자가 대화방을 보고 이동할 수 있도록 시각적 및 오디오 신호를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-514">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="d2d73-515">데이터를 개선 하기 위해 이동할 위치를 사용자에 게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-515">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="d2d73-516">필요한 검색 품질을 얻기 위해 수행 해야 하는 작업을 사용자에 게 알리는 것이 가장 좋을 수 있습니다. 예를 들어 천장, 가구를 찾는 등의 작업을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-516">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="d2d73-517">리소스</span><span class="sxs-lookup"><span data-stu-id="d2d73-517">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d2d73-518">설명서</span><span class="sxs-lookup"><span data-stu-id="d2d73-518">Documentation</span></span>

* [<span data-ttu-id="d2d73-519">실내 스캔 시각화</span><span class="sxs-lookup"><span data-stu-id="d2d73-519">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="d2d73-520">사례 연구: HoloLens의 공간 매핑 기능 확장</span><span class="sxs-lookup"><span data-stu-id="d2d73-520">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="d2d73-521">사례 연구: HoloTour에 대 한 공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="d2d73-521">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="d2d73-522">사례 연구: 조각에서 몰입 형 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="d2d73-522">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d2d73-523">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="d2d73-523">Tools and tutorials</span></span>

* [<span data-ttu-id="d2d73-524">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="d2d73-524">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="d2d73-525">방향 표시기</span><span class="sxs-lookup"><span data-stu-id="d2d73-525">Directional indicators</span></span>

<span data-ttu-id="d2d73-526">혼합 현실 앱에서 콘텐츠는 실제 개체에서 뷰 또는 폐색의 필드 밖에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-526">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="d2d73-527">잘 디자인 된 앱을 사용 하면 사용자가 보이지 않는 콘텐츠를 더 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-527">A well-designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="d2d73-528">방향성 표시기는 사용자에 게 중요 한 콘텐츠를 경고 하 고 사용자의 위치를 기준으로 콘텐츠에 대 한 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-528">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="d2d73-529">보이지 않는 콘텐츠에 대 한 지침은 소리 송신기, 방향 화살표 또는 직접 시각적 표시의 형태로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-529">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d2d73-530">장치 영향</span><span class="sxs-lookup"><span data-stu-id="d2d73-530">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2d73-531"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-531"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d2d73-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2d73-533">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-533">✔️</span></span></td>
        <td><span data-ttu-id="d2d73-534">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-534">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d2d73-535">품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-535">Quality criteria</span></span>

|  <span data-ttu-id="d2d73-536">가장 좋음</span><span class="sxs-lookup"><span data-stu-id="d2d73-536">Best</span></span>  |  <span data-ttu-id="d2d73-537">평가</span><span class="sxs-lookup"><span data-stu-id="d2d73-537">Meets</span></span> |  <span data-ttu-id="d2d73-538">실패</span><span class="sxs-lookup"><span data-stu-id="d2d73-538">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d2d73-539">시각적 개체와 오디오 큐는 사용자에 게 보기 필드 외부의 관련 콘텐츠를 직접 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-539">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="d2d73-540">콘텐츠의 일반적인 방향을 사용자에 게 가리키는 화살표 또는 표시기입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-540">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="d2d73-541">관련 콘텐츠가 보기 필드의 외부에 있으며 사용자에 게 잘못 된 위치나 위치 지침이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-541">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d2d73-542">측정 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-542">How to measure</span></span>

* <span data-ttu-id="d2d73-543">보기의 사용자 필드 외부에 있는 관련 콘텐츠는 시각적 개체 및/또는 오디오 신호를 통해 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-543">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d2d73-544">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d2d73-544">Recommendations</span></span>

* <span data-ttu-id="d2d73-545">관련 콘텐츠가 사용자의 보기 필드 외부에 있는 경우 방향 표시기와 오디오 신호를 사용 하 여 사용자에 게 콘텐츠를 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-545">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="d2d73-546">대부분의 경우에는 방향 화살표 보다 직접 시각적 개체 가이드가 선호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-546">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="d2d73-547">방향 표시기는 커서에 내장 되어서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-547">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="d2d73-548">리소스</span><span class="sxs-lookup"><span data-stu-id="d2d73-548">Resources</span></span>

* [<span data-ttu-id="d2d73-549">홀로그램 프레임</span><span class="sxs-lookup"><span data-stu-id="d2d73-549">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="d2d73-550">데이터 로드</span><span class="sxs-lookup"><span data-stu-id="d2d73-550">Data loading</span></span>

<span data-ttu-id="d2d73-551">진행률 컨트롤은 긴 작업을 진행 중인 사용자에게 피드백을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-551">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="d2d73-552">진행률 표시기가 표시 될 때 사용자가 앱과 상호 작용할 수 없고 대기 시간이 얼마나 길어질 수도 있음을 의미할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-552">It can mean that the user can't interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d2d73-553">장치 영향</span><span class="sxs-lookup"><span data-stu-id="d2d73-553">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2d73-554"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-554"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d2d73-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2d73-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2d73-556">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-556">✔️</span></span></td>
        <td><span data-ttu-id="d2d73-557">✔️</span><span class="sxs-lookup"><span data-stu-id="d2d73-557">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d2d73-558">품질 기준</span><span class="sxs-lookup"><span data-stu-id="d2d73-558">Quality criteria</span></span>

|  <span data-ttu-id="d2d73-559">가장 좋음</span><span class="sxs-lookup"><span data-stu-id="d2d73-559">Best</span></span>  |  <span data-ttu-id="d2d73-560">평가</span><span class="sxs-lookup"><span data-stu-id="d2d73-560">Meets</span></span> |  <span data-ttu-id="d2d73-561">실패</span><span class="sxs-lookup"><span data-stu-id="d2d73-561">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d2d73-562">데이터를 로드 또는 처리 하는 동안 진행률이 표시 되는 진행률 표시줄 또는 링 형식의 애니메이션 시각적 표시기입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-562">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="d2d73-563">시각적 표시기는 대기 시간에 대 한 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-563">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="d2d73-564">사용자에 게 데이터 로드가 진행 중 이라는 알림이 표시 되지만 대기 시간을 나타내는 것은 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-564">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="d2d73-565">5 초 보다 오래 걸리는 태스크에 대 한 데이터 로드 또는 프로세스 표시기가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-565">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="d2d73-566">측정 방법</span><span class="sxs-lookup"><span data-stu-id="d2d73-566">How to measure</span></span>

* <span data-ttu-id="d2d73-567">데이터를 로드 하는 동안 5 초 넘게 비어 있는 상태가 없는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-567">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d2d73-568">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d2d73-568">Recommendations</span></span>

* <span data-ttu-id="d2d73-569">사용자가이 앱을 중단 또는 충돌 하도록 할 수 있는 경우 진행 상황을 보여 주는 데이터 로드 애니메이터를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-569">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="d2d73-570">적절 한 엄지 단추는 5 초 넘게 걸릴 수 있는 ' 로드 ' 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="d2d73-570">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="d2d73-571">리소스</span><span class="sxs-lookup"><span data-stu-id="d2d73-571">Resources</span></span>

* [<span data-ttu-id="d2d73-572">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="d2d73-572">Displaying progress</span></span>](../../design/progress.md)
