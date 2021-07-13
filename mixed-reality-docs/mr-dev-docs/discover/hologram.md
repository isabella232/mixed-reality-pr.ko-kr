---
title: 홀로그램이란?
description: HoloLens 사용하면 주변 세계에 나타나는 3차원 홀로그램, 광원 및 소리로 구성된 개체를 보고 상호 작용할 수 있습니다.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 홀로그램, 디자인, 상호 작용, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 증강 현실이란?
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634334"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="f9f21-104">홀로그램이란?</span><span class="sxs-lookup"><span data-stu-id="f9f21-104">What is a hologram?</span></span>

<span data-ttu-id="f9f21-105">HoloLens 사용하면 실제 개체처럼 주변 세계에 나타나는 광원과 소리로 구성된 개체인 **홀로그램을** 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-105">HoloLens lets you view **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="f9f21-106">홀로그램스 [응시,](../design/gaze-and-commit.md) [제스처](../design/gaze-and-commit.md#composite-gestures)및 음성 명령에 응답할 수 [있습니다.](../design/voice-input.md)</span><span class="sxs-lookup"><span data-stu-id="f9f21-106">Holograms can respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="f9f21-107">주위의 실제 [표면과](../design/spatial-mapping.md) 상호 작용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="f9f21-108">홀로그램스 전 세계의 일부인 디지털 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-108">Holograms are digital objects that are part of your world.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

## <a name="device-support"></a><span data-ttu-id="f9f21-109">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="f9f21-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f9f21-110"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="f9f21-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f9f21-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="f9f21-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="f9f21-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="f9f21-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="f9f21-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="f9f21-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f9f21-114">홀로그램</span><span class="sxs-lookup"><span data-stu-id="f9f21-114">Holograms</span></span></td>
        <td><span data-ttu-id="f9f21-115">✔️</span><span class="sxs-lookup"><span data-stu-id="f9f21-115">✔️</span></span></td>
        <td><span data-ttu-id="f9f21-116">✔️</span><span class="sxs-lookup"><span data-stu-id="f9f21-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="f9f21-117">홀로그램은 광원과 소리로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-117">A hologram is made of light and sound</span></span>

### <a name="light"></a><span data-ttu-id="f9f21-118">밝음</span><span class="sxs-lookup"><span data-stu-id="f9f21-118">Light</span></span>

<span data-ttu-id="f9f21-119">HoloLens [렌더링되는](../develop/platform-capabilities-and-apis/rendering.md) 홀로그램은 홀로그램 프레임에서 사용자의 눈 바로 앞에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-119">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of users' eyes.</span></span> <span data-ttu-id="f9f21-120">홀로그램스 세계에 조명을 추가합니다. 즉, 디스플레이의 광원과 주변 세계의 광원을 모두 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-120">Holograms add light to your world, which means that you see both the light from the display and the light from your surrounding world.</span></span> <span data-ttu-id="f9f21-121">HoloLens 조명을 추가하는 가감 표시를 사용하므로 검은색이 투명하게 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-121">Since HoloLens uses an additive display that adds light, the black color will be rendered transparent.</span></span> 

<span data-ttu-id="f9f21-122">홀로그램스 모양과 동작이 매우 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-122">Holograms can have very different appearances and behaviors.</span></span> <span data-ttu-id="f9f21-123">일부는 현실적이고 견고하며, 다른 일부는 설사하고 은밀합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="f9f21-124">홀로그램을 사용하여 사용자 환경의 기능을 강조 표시하거나 앱의 사용자 인터페이스에서 요소로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-124">You can use holograms to highlight features in your environment or use them as elements in your app's user interface.</span></span>

![홀로그램을 조작하는 손](images/hologram-hands-940px.jpg)

### <a name="sound"></a><span data-ttu-id="f9f21-126">소리</span><span class="sxs-lookup"><span data-stu-id="f9f21-126">Sound</span></span>

<span data-ttu-id="f9f21-127">홀로그램스 환경의 특정 위치에서 제공되는 것처럼 보이는 [소리를](../design/spatial-sound.md)생성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-127">Holograms can also produce [sounds](../design/spatial-sound.md), which appear to come from a specific place in your environment.</span></span> <span data-ttu-id="f9f21-128">HoloLens 소리는 음면 바로 위에 있는 두 개의 스피커에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-128">On HoloLens, sound comes from two speakers that are located directly above your ears.</span></span> <span data-ttu-id="f9f21-129">홀로그램 디스플레이와 마찬가지로, 화자는 가감성이 있으며 사용자 환경에서 소리를 차단하지 않고 새로운 소리를 도입합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-129">Same as the holographic displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="f9f21-130">홀로그램을 세계에 배치하거나 태그를 함께 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-130">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="f9f21-131">홀로그램의 고정 위치가 있는 경우 전 세계의 해당 지점에 정확하게 [배치할](../design/coordinate-systems.md) 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-131">When you have a fixed location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="f9f21-132">진행하면서 홀로그램은 실제 개체처럼 주변 세계에 따라 고정된 것처럼 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-132">As you walk around, the hologram appears stationary based on the world around you, just like a physical object.</span></span> <span data-ttu-id="f9f21-133">[공간 앵커를](../design/coordinate-systems.md#spatial-anchors) 사용하여 개체를 고정하는 경우 나중에 다시 돌아올 때 시스템에서 개체를 남겨둔 위치도 기억할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-133">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![소매 공간에서 Microsoft Dynamics 365 레이아웃을 사용하는 두 명의 남성](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="f9f21-135">일부 홀로그램은 사용자를 대신 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-135">Some holograms follow the user instead.</span></span> <span data-ttu-id="f9f21-136">사용자에 따라 자신을 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-136">They position themselves based on the user.</span></span> <span data-ttu-id="f9f21-137">홀로그램을 가져온 다음, 다른 방으로 들어가면 벽 위에 놓도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-137">You can choose to bring a hologram with you, and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="f9f21-138">**모범 사례**</span><span class="sxs-lookup"><span data-stu-id="f9f21-138">**Best practices**</span></span>

* <span data-ttu-id="f9f21-139">일부 시나리오에서는 홀로그램을 환경 전체에서 쉽게 검색하거나 볼 수 있다고 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-139">Some scenarios demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="f9f21-140">이러한 종류의 위치에는 두 가지 높은 수준의 접근 방식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-140">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="f9f21-141">표시 잠금 및 **본문이** **잠긴** 를 호출해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-141">Let's call them **display-locked** and **body-locked**.</span></span>
   * <span data-ttu-id="f9f21-142">**디스플레이 잠금** 콘텐츠가 디스플레이 디바이스에 잠겨 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-142">**Display-locked** content is locked to the display device.</span></span> <span data-ttu-id="f9f21-143">이러한 유형의 콘텐츠는 여러 가지 이유로 인해 까다로운데, 여기에는 많은 사용자가 불편하게 만들고 "흔든다"고 하는 "불연연한 느낌"이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-143">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="f9f21-144">일반적으로 디자이너는 디스플레이 잠금 콘텐츠를 방지하는 것이 더 낫습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-144">In general, designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="f9f21-145">**본문이 잠긴** 콘텐츠는 훨씬 더 용인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-145">**Body-locked** content can be far more forgiving.</span></span> <span data-ttu-id="f9f21-146">본문 잠금은 3D 공간에서 홀로그램을 사용자의 본문 또는 응시 벡터에 테더링하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-146">Body-locking is when you tether a hologram to the user's body or gaze vector in 3D space.</span></span> <span data-ttu-id="f9f21-147">많은 경험에서 홀로그램이 사용자의 응시를 따르는 신체 잠금 동작을 채택하여 사용자가 홀로그램을 손실하지 않고도 자신의 신체를 회전하고 공간을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-147">Many experiences have adopted a body-locking behavior where the hologram follows the user's gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="f9f21-148">지연을 통합하면 홀로그램 이동이 더 자연스럽게 느낄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-148">Incorporating a delay helps the hologram movements to feel more natural.</span></span> <span data-ttu-id="f9f21-149">예를 들어 Windows Holographic OS의 일부 핵심 UI는 사용자가 머리가 바뀌는 동안 탄력적인 탄력적 지연으로 사용자의 응시를 따르는 신체 잠금의 변형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-149">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="f9f21-150">홀로그램을 일반적으로 머리에서 약 1-2미터 떨어진 보기 거리에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-150">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="f9f21-151">요소가 홀로그램 프레임에 지속적으로 있어야 하는 경우 드리프트할 수 있도록 허용하거나, 사용자가 보기를 변경할 때 콘텐츠를 디스플레이의 한 쪽으로 이동하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-151">Allow elements to drift if they must be continually in the holographic frame, or consider moving your content to one side of the display when the user changes their point of view.</span></span> <span data-ttu-id="f9f21-152">자세한 내용은 스트리밍 [및 태그 따라](../design/billboarding-and-tag-along.md) 아티실을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9f21-152">For more information, see the [billboarding and tag-along](../design/billboarding-and-tag-along.md) artilce.</span></span>

<span data-ttu-id="f9f21-153">**최적의 영역에 홀로그램 배치 - 1.25m에서 5m 사이**</span><span class="sxs-lookup"><span data-stu-id="f9f21-153">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="f9f21-154">2미터는 가장 최적의 보기 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-154">Two meters is the most optimal viewing distance.</span></span> <span data-ttu-id="f9f21-155">1미터에 가까워지면 환경이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-155">The experience will start to degrade as you get closer than 1 meter.</span></span> <span data-ttu-id="f9f21-156">1미터 미만의 거리에 있는 경우 정기적으로 깊이 이동하는 홀로그램은 고정 홀로그램보다 문제가 될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-156">At distances less than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="f9f21-157">콘텐츠가 너무 가까워지면 콘텐츠를 정상적으로 클리핑하거나 페이드 아웃하는 것이 좋습니다. 따라서 사용자가 보기가 너무 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-157">Consider gracefully clipping or fading out your content when it gets too close, so you don't jar the user into an unpleasant viewing experience.</span></span>

![사용자로부터 홀로그램을 배치하기 위한 최적의 거리입니다.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="f9f21-159">홀로그램은 사용자 및 사용자 세계와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-159">A hologram interacts with you and your world</span></span>

<span data-ttu-id="f9f21-160">홀로그램스 조명과 소리에만 국한되지 않습니다. 또한 전 세계에서 활동적인 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-160">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="f9f21-161">홀로그램과 제스처를 손으로 응시하면 홀로그램이 따라오기 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-161">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="f9f21-162">음성 명령을 제공하면 홀로그램이 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-162">Give a voice command, and the hologram can reply.</span></span>

![Microsoft HoloLens 2를 사용하여 풍력 발전 단지 개발 프로젝트에서 공동 작업하는 정부 유틸리티 작업자 그룹](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="f9f21-164">홀로그램스 다른 곳에서는 불가능한 개인 상호 작용을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-164">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="f9f21-165">HoloLens 세계 어디에 있는지 알고 있기 때문에 홀로그램 문자는 눈에서 직접 보고 대화를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-165">Because the HoloLens knows where it is in the world, a holographic character can look at you directly in the eyes and start a conversation with you.</span></span>

<span data-ttu-id="f9f21-166">홀로그램은 주변 환경과 상호 작용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-166">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="f9f21-167">예를 들어 홀로그램 바운드 볼을 테이블 위에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-167">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="f9f21-168">그런 [다음, 에어 탭을](../design/gaze-and-commit.md#composite-gestures)통해 공이 바운드되는 것을 보고 테이블에 적중될 때 소리를 내립니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-168">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound as it hits the table.</span></span>

<span data-ttu-id="f9f21-169">홀로그램스 실제 개체에 의해 폐색될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-169">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="f9f21-170">예를 들어 홀로그램 문자는 문과 벽 뒤에서 보이지 않는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-170">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="f9f21-171">**홀로그램과 실제 세계를 통합하기 위한 팁**</span><span class="sxs-lookup"><span data-stu-id="f9f21-171">**Tips for integrating holograms and the real world**</span></span>

* <span data-ttu-id="f9f21-172">초대형 규칙에 맞게 조정하면 홀로그램을 더 쉽게 관련시키고 더 안정적으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-172">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="f9f21-173">예: 홀로그램 개를 공간에 부동하지 않고 테이블에 꽃병을 & 지면에 홀로그램 개를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-173">For example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="f9f21-174">많은 디자이너는 홀로그램이 있는 표면에 "음의 그림자"를 만들어 더 신뢰할 수 있는 홀로그램을 통합할 수 있음을 발견했습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-174">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="f9f21-175">홀로그램 주위에 부드러운 후광을 만든 다음, 광선에서 "그림자"를 빼서 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-175">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="f9f21-176">소프트 후광은 실제 세계의 광원과 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-176">The soft glow integrates with the light from the real world.</span></span> <span data-ttu-id="f9f21-177">그림자는 환경에서 홀로그램을 접지하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-177">The shadow is used to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a><span data-ttu-id="f9f21-178">홀로그램이란?</span><span class="sxs-lookup"><span data-stu-id="f9f21-178">A hologram is what</span></span> <br><span data-ttu-id="f9f21-179">다음을 기대할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-179">you can dream up</span></span><br>
        <span data-ttu-id="f9f21-180">홀로그램 개발자는 2D 화면과 주변 세계로 독창함을 끊을 수 있는 능력을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-180">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="f9f21-181">무엇을 *빌드하시겠습니까?*</span><span class="sxs-lookup"><span data-stu-id="f9f21-181">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="f9f21-182">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="f9f21-182">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="f9f21-183">![회의실의 홀로그램 허수 세계](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="f9f21-183">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="f9f21-184">다음 검색 검사점</span><span class="sxs-lookup"><span data-stu-id="f9f21-184">Next Discovery Checkpoint</span></span>

<span data-ttu-id="f9f21-185">앞에서 설명한 [검색 여정을](get-started-with-mr.md) 진행하면서 Mixed Reality 기본 사항들을 탐색하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-185">You're on the [discovery journey](get-started-with-mr.md) we've laid out, and exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="f9f21-186">이제 다음 기본 항목으로 계속 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9f21-186">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="f9f21-187">디자인 프로세스 확장</span><span class="sxs-lookup"><span data-stu-id="f9f21-187">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)