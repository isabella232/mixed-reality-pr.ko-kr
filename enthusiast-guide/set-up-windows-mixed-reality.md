---
title: Windows Mixed Reality 설정
description: Windows Mixed Reality 동작 컨트롤러, 음성 및 오디오를 설정 하 고 안전한 재생 공간에 대 한 공간 경계를 정의 하는 방법입니다.
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 시작, 설정, 동작 컨트롤러, 컨트롤러, 음성, 오디오, 장착 됨, 경계, 그래픽 드라이버, Microsoft Edge, chromium
ms.openlocfilehash: 8cd313651665fe2e50deb21e2ba2434883dc873a
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725944"
---
# <a name="set-up-windows-mixed-reality"></a><span data-ttu-id="c35d4-104">Windows Mixed Reality 설정</span><span class="sxs-lookup"><span data-stu-id="c35d4-104">Set up Windows Mixed Reality</span></span>

## <a name="get-ready"></a><span data-ttu-id="c35d4-105">준비</span><span class="sxs-lookup"><span data-stu-id="c35d4-105">Get ready</span></span>

<span data-ttu-id="c35d4-106">Windows Mixed Reality를 실행 하려면 다음이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-106">To run Windows Mixed Reality, you'll need:</span></span>

* <span data-ttu-id="c35d4-107">호환 되는 혼합 현실 모던 헤드셋.</span><span class="sxs-lookup"><span data-stu-id="c35d4-107">A compatible mixed reality immersive headset.</span></span> [<span data-ttu-id="c35d4-108">자세한 정보</span><span class="sxs-lookup"><span data-stu-id="c35d4-108">Learn more</span></span>](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)
* <span data-ttu-id="c35d4-109">[Windows Mixed Reality READY PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 와 헤드셋에 대 한 올바른 포트</span><span class="sxs-lookup"><span data-stu-id="c35d4-109">A [Windows Mixed Reality-ready PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) with the correct ports for your headset</span></span>
* <span data-ttu-id="c35d4-110">동작 [컨트롤러](controllers-in-wmr.md), Xbox 컨트롤러 또는 마우스 및 키보드</span><span class="sxs-lookup"><span data-stu-id="c35d4-110">Motion [controllers](controllers-in-wmr.md), an Xbox controller, or a mouse and keyboard</span></span>
* <span data-ttu-id="c35d4-111">마이크가 있는 헤드폰 (헤드셋에서 기본 제공 되지 않는 경우)</span><span class="sxs-lookup"><span data-stu-id="c35d4-111">Headphones with a mic (if your headset doesn't have them built in)</span></span>
* <span data-ttu-id="c35d4-112">열려 있는 많은 공간</span><span class="sxs-lookup"><span data-stu-id="c35d4-112">A large, open space</span></span>

## <a name="get-set"></a><span data-ttu-id="c35d4-113">집합 가져오기</span><span class="sxs-lookup"><span data-stu-id="c35d4-113">Get set</span></span>

<span data-ttu-id="c35d4-114">공간을 준비 합니다 (오버 헤드 공간 포함).</span><span class="sxs-lookup"><span data-stu-id="c35d4-114">Prepare your space (including your overhead space).</span></span> <span data-ttu-id="c35d4-115">사용할 영역에 장애물, 위험 또는 손상 된 항목이 없는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-115">Make sure there are no obstacles, hazards, or fragile items in the area you’ll be using.</span></span> <span data-ttu-id="c35d4-116">계단의 위쪽 이나 더 낮은 천장 팬에서 설정 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="c35d4-116">Don’t set up at the top of a staircase or under an extra-low ceiling fan.</span></span> <span data-ttu-id="c35d4-117">영역에서 모든 거 나 장애물을 제거 하 고 모든 헤드셋 사용자가 안전 지침을 읽고 이해 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-117">Remove any breakables or obstacles from the area and make sure that all headset users read and understand the safety guidelines.</span></span>

<span data-ttu-id="c35d4-118">공간이 준비 되 면 헤드셋에 연결 하지만 아직 배치 하지 마십시오. 먼저 PC에서 일부 설치를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-118">Once your space is ready, plug in your  headset, but don't put it on yet—first we'll need to do some setup on your PC.</span></span> <span data-ttu-id="c35d4-119">PC 검사를 실행 하 고, 일부 소프트웨어를 다운로드 하 고, 컨트롤러를 연결 하 고, 장애물을 방지 하는 데 도움이 되는 [경계](boundary-questions.md) 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-119">We’ll run a PC check, download some software, connect your controllers, and create a [boundary](boundary-questions.md) to help you avoid obstacles.</span></span>

<span data-ttu-id="c35d4-120">그런 다음 재미 있는 부분을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-120">Then comes the fun part—put on your headset and enter the mixed world.</span></span> <span data-ttu-id="c35d4-121">Cortana는 둘러보기를 제공 하기 위해 대기 중입니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-121">Cortana will be waiting to give you a tour.</span></span> <span data-ttu-id="c35d4-122">즐거운 시간 보내세요!</span><span class="sxs-lookup"><span data-stu-id="c35d4-122">Have fun!</span></span>

## <a name="go"></a><span data-ttu-id="c35d4-123">지금</span><span class="sxs-lookup"><span data-stu-id="c35d4-123">Go!</span></span>

<span data-ttu-id="c35d4-124">공간이 준비 되 면 헤드셋에 연결 하지만 아직 배치 하지 마십시오. 먼저 PC에서 일부 설치를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-124">Once your space is ready, plug in your  headset, but don't put it on yet—first we'll need to do some setup on your PC.</span></span> <span data-ttu-id="c35d4-125">PC 검사를 실행 하 고, 일부 소프트웨어를 다운로드 하 고, 컨트롤러를 연결 하 고, 장애물을 방지 하는 데 도움이 되는 [경계](boundary-questions.md) 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-125">We’ll run a PC check, download some software, connect your controllers, and create a [boundary](boundary-questions.md) to help you avoid obstacles.</span></span>

<span data-ttu-id="c35d4-126">그런 다음 재미 있는 부분을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-126">Then comes the fun part—put on your headset and enter the mixed world.</span></span> <span data-ttu-id="c35d4-127">Cortana는 둘러보기를 제공 하기 위해 대기 중입니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-127">Cortana will be waiting to give you a tour.</span></span> <span data-ttu-id="c35d4-128">즐거운 시간 보내세요!</span><span class="sxs-lookup"><span data-stu-id="c35d4-128">Have fun!</span></span>

## <a name="get-familiar-with-your-motion-controllers"></a><span data-ttu-id="c35d4-129">동작 컨트롤러에 대해 알아보기</span><span class="sxs-lookup"><span data-stu-id="c35d4-129">Get familiar with your motion controllers</span></span>

<span data-ttu-id="c35d4-130">헤드셋에 기본 제공 된 라디오가 있는 경우 헤드셋과 함께 제공 되는 컨트롤러는 팩터리에서 페어링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-130">If your headset has a built-in radio, the controllers that come with your headset are paired to it in the factory.</span></span> <span data-ttu-id="c35d4-131">새 컨트롤러와 헤드셋을 처음 켜면 이미 페어링 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-131">When you first turn on your new controllers and headset, they'll already be paired.</span></span>

<span data-ttu-id="c35d4-132">기본 제공 라디오 없이 헤드셋을 사용 하는 경우 PC에 연결 하 여 동작 컨트롤러를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-132">If you have a headset without a built-in radio, you'll have to set up your motion controllers by pairing them to your PC.</span></span> <span data-ttu-id="c35d4-133">2018 이후 제조 된 대부분의 헤드셋에는 기본 제공 라디오가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-133">Most headsets manufactured after 2018 have built-in radio.</span></span>

<span data-ttu-id="c35d4-134">Xbox 게임 패드 또는 키보드와 마우스를 사용 하려는 경우에는 컨트롤러를 페어링 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-134">You don’t need to pair your controllers if you're only planning to use an Xbox gamepad or keyboard and mouse.</span></span>  <span data-ttu-id="c35d4-135">컨트롤러를 사용 하려는 경우에는 컨트롤러를 페어링 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-135">If you ever plan to use controllers, you should pair them.</span></span>

<span data-ttu-id="c35d4-136">**참고**: Windows Mixed Reality 동작 컨트롤러에는 Bluetooth 4.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-136">**Note**: Windows Mixed Reality motion controllers require Bluetooth 4.0.</span></span> <span data-ttu-id="c35d4-137">PC에 기본 제공 된 Bluetooth가 없는 경우에는 Bluetooth 4.0을 지 원하는 USB Bluetooth 어댑터를 연결 하 여 동작 컨트롤러를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-137">If your PC doesn't have built-in Bluetooth, you'll need to plug in a USB Bluetooth adapter that supports Bluetooth 4.0 to enable your motion controllers.</span></span> <span data-ttu-id="c35d4-138">헤드셋에서 기본 제공 라디오를 사용 하는 데에는 Bluetooth 어댑터가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-138">You don’t need a Bluetooth adapter to use the built-in radio in your headset.</span></span>

![동작 컨트롤러에 대해 알아보기](images/get_to_know_controllers.png)

<span data-ttu-id="c35d4-140">동작 컨트롤러를 쌍으로 연결 해야 하는 경우 [Windows Mixed Reality의 컨트롤러](controllers-in-wmr.md) 문서를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-140">If you need to pair your motion controllers, review [controllers in Windows Mixed Reality](controllers-in-wmr.md) article.</span></span>

## <a name="set-up-your-room-boundary"></a><span data-ttu-id="c35d4-141">대화방 경계 설정</span><span class="sxs-lookup"><span data-stu-id="c35d4-141">Set up your room boundary</span></span>

<span data-ttu-id="c35d4-142">방 규모 또는 책상 크기 조정 환경을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-142">Choose a room scale or desk scale experience:</span></span>

<span data-ttu-id="c35d4-143">**옵션 1: 모든 환경 (공간 규모가 라고도 함)에 대해 설정** 하면 대화방을 탐색할 수 있으며, 가장 몰입가 혼합 된 현실 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-143">**Option 1: Set me up for all experiences (also known as room scale)** will allow you to walk around the room and is the most immersive mixed reality experience.</span></span> <span data-ttu-id="c35d4-144">혼합 현실에 대해 최소 5 피트 x 7 피트 (1.5 미터 x 2 미터)의 공간을 선택 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-144">We recommend you at clear at least five foot x seven foot (1.5 meters x 2 meters) of space for mixed reality.</span></span>

<span data-ttu-id="c35d4-145">**옵션 2: 사용자의 책상에서 작동 하는 (책상 크기 조정 라고도 함) 환경에 대해 설정** 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-145">**Option 2: Set me up for seated and standing (also known as desk scale)** experience will work at your desk.</span></span> <span data-ttu-id="c35d4-146">공간이 크지 않은 경우 좋은 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-146">It's a good option if your space isn't large.</span></span> <span data-ttu-id="c35d4-147">또한 경계 없이 헤드셋을 사용 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-147">It also means that you'll be using your headset without a boundary.</span></span> <span data-ttu-id="c35d4-148">물리적 장애물을 방지 하는 데 도움이 되는 경계를 갖지 않으므로 한 곳에 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-148">You'll need to stay in one place, as you'll have no boundary to help you avoid physical obstacles.</span></span> <span data-ttu-id="c35d4-149">일부 앱 및 게임은 경계 환경으로 설계 되지 않으므로 의도 한 대로 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-149">Some apps and games aren't designed to be a boundary experience, so they might not work as intended.</span></span>

![설정 선택](images/1050px-chooseasetup.png)

### <a name="if-you-choose-set-me-up-for-all-experiences"></a><span data-ttu-id="c35d4-151">"모든 환경에 대해 설정"을 선택 하는 경우</span><span class="sxs-lookup"><span data-stu-id="c35d4-151">If you choose "Set me up for all experiences"</span></span>

<span data-ttu-id="c35d4-152">곧 이동 하 고 상호 작용할 수 있는 가상 세계가 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-152">Soon, your room will become a virtual world where you can walk around and interact!</span></span> <span data-ttu-id="c35d4-153">혼합 현실 실행을 위해 공간의 일부 공간을 확보 하 고 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-153">Stand up and clear some space in your room for running mixed reality.</span></span> <span data-ttu-id="c35d4-154">혼합 현실에서 최소 5 피트 x 7 피트 또는 1.5 미터 x 2 미터의 공간을 선택 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-154">We recommend you at clear at least five foot x seven foot, or 1.5 meters x 2 meters, of space for mixed reality.</span></span>

![공간이 명확 한지 확인 합니다.](images/1050px-createaboundary.png)

<span data-ttu-id="c35d4-156">공간이 명확 한지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-156">Make sure your space is clear.</span></span>

![헤드셋 가운데 맞춤](images/1050px-createaboundary-2.png)

<span data-ttu-id="c35d4-158">헤드셋을 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-158">Center your headset.</span></span>

![경계 추적](images/1050px-createaboundary-3.png)

<span data-ttu-id="c35d4-160">경계를 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-160">Trace your boundary.</span></span>

![PC를 지속적으로 유지](images/1050px-createaboundary-4.png)

<span data-ttu-id="c35d4-162">헤드셋을 PC가 가리키는 상태로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-162">Keep your headset pointed toward your PC.</span></span>

![경계는 다음과 같습니다.](images/1050px-createaboundary-5.png)

<span data-ttu-id="c35d4-164">경계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-164">Here's your boundary.</span></span>

### <a name="if-you-choose-set-me-up-for-seated-and-standing"></a><span data-ttu-id="c35d4-165">"시작 및 고정에 대해 설정"을 선택 하는 경우</span><span class="sxs-lookup"><span data-stu-id="c35d4-165">If you choose "Set me up for seated and standing"</span></span>

<span data-ttu-id="c35d4-166">이 옵션을 선택 하는 경우에는 추가 단계가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-166">There are no extra steps required if you choose this option.</span></span>

## <a name="what-is-the-maximum-size-of-the-boundary"></a><span data-ttu-id="c35d4-167">경계의 최대 크기는 얼마 인가요?</span><span class="sxs-lookup"><span data-stu-id="c35d4-167">What is the maximum size of the boundary?</span></span>

<span data-ttu-id="c35d4-168">Windows Mixed Reality에서 지원 되는 최대 경계 크기는 중앙에서 18x18ft (5.7 x 5.7 m) 또는 13 ft (4 m) 반경입니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-168">The maximum supported boundary size in Windows Mixed Reality is a 18x18ft (5.7x5.7m) or 13 ft (4 m) radius from the center.</span></span> <span data-ttu-id="c35d4-169">경계 크기는 앵커 지점과 경계의 안정성을 위해 이동할 수 있는 앵커 지점의 거리에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-169">The boundary size depends on the anchor point and how far from the anchor point you can move before you risk the stability of the boundary.</span></span>  <span data-ttu-id="c35d4-170">Windows Mixed Reality는 단계 추상화를 기반으로 하며, 단계는에서 이동 하는 공간입니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-170">Windows Mixed Reality is built on a stage abstraction, the stage being the space you move around in.</span></span> <span data-ttu-id="c35d4-171">해당 단계는 거의 모든 앱에서 가정 하는 단일 앵커에 종속 됩니다 .이는 Vive와 Oculus가 단일 좌표계로 작동 하는 방식입니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-171">That stage depends on a single anchor, which nearly every app also assumes – it’s how Vive and Oculus work too with their single coordinate system.</span></span>  <span data-ttu-id="c35d4-172">이는 내부 추적을 사용 하는 경우에 중요 합니다 .이는 앵커 지점에서 더 멀리 이동할 때 헤드셋 추적이 안정적으로 경계를 유지할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-172">This is important because with inside-out tracking, as you move further away from an anchor point the headset tracking is reliable at keeping the boundary stable.</span></span>  <span data-ttu-id="c35d4-173">경계는 물리적 장애물을 방지 하기 위해 고안 된 것 이며,이는 이동 하는 중심에서 더 많은 문제를 해결 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-173">Where the boundary is intended to help avoid physical obstacles, it becomes more of a problem the further out from the center you go.</span></span>  <span data-ttu-id="c35d4-174">최대 경계 크기를 결정 하는 두 가지 요인이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-174">Two factors went into the decision on maximum boundary size.</span></span> <span data-ttu-id="c35d4-175">Windows Mixed Reality 헤드셋이 경계와 헤드셋 케이블의 길이에 가장 적합 한 공간 크기 조정 환경을 제공할 수 있는 최대 거리 (대부분의 Windows Mixed Reality 헤드셋은 10 피트 (3 m)).</span><span class="sxs-lookup"><span data-stu-id="c35d4-175">The maximum distance at which Windows Mixed Reality headsets could provide the best room scale experience with a boundary and the length of the headset cable, which for most Windows Mixed Reality headsets are 10 ft (3 m).</span></span>

## <a name="set-up-speech"></a><span data-ttu-id="c35d4-176">음성 설정</span><span class="sxs-lookup"><span data-stu-id="c35d4-176">Set up speech</span></span>

<span data-ttu-id="c35d4-177">혼합 현실에서 Cortana 명령을 사용 하도록 설정할 수 있습니다. 그러면 음성 명령을 사용 하 여 앱을 텔레포트 하 고 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-177">You can enable Cortana commands in mixed reality, which lets you use speech commands to teleport and open apps.</span></span> <span data-ttu-id="c35d4-178">이러한 작업에 대 한 자세한 내용은 [혼합 현실 정보](learn-mixed-reality.md) 챕터를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c35d4-178">You'll learn more about these actions in the [Learn Mixed Reality](learn-mixed-reality.md) chapter.</span></span>

![혼합 현실에서 음성 사용이 더 좋습니다.](images/1050px-betterwithspeech.png)

## <a name="set-up-your-audio-headset"></a><span data-ttu-id="c35d4-180">오디오 헤드셋 설정</span><span class="sxs-lookup"><span data-stu-id="c35d4-180">Set up your audio headset</span></span>

<span data-ttu-id="c35d4-181">Ic AKG 헤드폰 및 이중 마이크 배열을 사용 하 여 Samsung HMD Odyssey를 구매한 경우를 제외 하 고 마이크와 헤드폰을 모두 사용 하 여 오디오 헤드셋을 받고 헤드셋의 3.5-mm 오디오 잭에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-181">Unless you purchased a Samsung HMD Odyssey with integrated AKG headphones and dual microphone array, you need to get an audio headset with both microphone and headphones and plug that into your headset's 3.5-mm audio jack.</span></span> <span data-ttu-id="c35d4-182">헤드셋의 3.5-mm 오디오 잭이 헤드셋의 아래쪽에 있거나 헤드셋 모델에 따라 헤드셋 센터에 연결 된 짧은 오디오 케이블의 끝에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-182">The 3.5-mm audio jack for your headset is located on the underside of the headset visor or at the end of a short audio cable attached to the headset visor, depending on the headset model.</span></span>

## <a name="adjusting-your-headsets-display-settings"></a><span data-ttu-id="c35d4-183">헤드셋의 디스플레이 설정 조정</span><span class="sxs-lookup"><span data-stu-id="c35d4-183">Adjusting your headset's display settings</span></span>

<span data-ttu-id="c35d4-184">Windows Mixed Reality는 PC의 하드웨어 구성에 따라 품질 및 성능의 균형을 유지 하는 표시 설정을 자동으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-184">Windows Mixed Reality automatically chooses display settings that balance quality and performance, based on your PC's hardware configuration.</span></span> <span data-ttu-id="c35d4-185">이러한 설정을 조정 하려면 **설정 > 혼합 현실 > 헤드셋 표시** 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-185">To adjust these settings, go to **Settings > Mixed Reality > Headset display**.</span></span>

### <a name="visuals"></a><span data-ttu-id="c35d4-186">시각적 개체</span><span class="sxs-lookup"><span data-stu-id="c35d4-186">Visuals</span></span>

<span data-ttu-id="c35d4-187">이 설정은 Mixed reality 홈의 시각적 품질을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-187">This setting controls the visual quality of your Mixed reality home.</span></span> <span data-ttu-id="c35d4-188">기본값은 "Automatic"입니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-188">The default is "Automatic".</span></span>

### <a name="resolution"></a><span data-ttu-id="c35d4-189">해결 방법</span><span class="sxs-lookup"><span data-stu-id="c35d4-189">Resolution</span></span>

<span data-ttu-id="c35d4-190">헤드셋의 기본 해상도는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-190">Your headset's native resolution is shown here.</span></span>

<span data-ttu-id="c35d4-191">고해상도 디스플레이를 사용 하 여 헤드셋을 PC에 연결 하는 경우 (예: 4320x2160이 표시 된 헤드셋) 혼합 현실 디스플레이 해상도를 조정 하는 설정이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-191">If you connect a headset with higher resolution displays to your PC, for example headsets with 4320x2160 displays, you'll see a setting to adjust the Mixed reality display resolution.</span></span>

* <span data-ttu-id="c35d4-192">이 설정은 Windows Mixed Reality 컴퍼지션 스택에 대해 기본적으로 렌더링 (예: 4320x2160) 할 수 있는 옵션을 제공 하거나, 컴퍼지션 스택이 더 낮은 해상도 및 upscale (예: 2880x1440에서 렌더링 하 고, upscale에서 4320x2160으로 렌더링)를 렌더링 하는 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-192">This setting provides the option for the Windows Mixed Reality composition stack to render natively (for example, at 4320x2160), or to have the composition stack render at a lower resolution and upscale (for example, render at 2880x1440 and upscale to 4320x2160).</span></span>
* <span data-ttu-id="c35d4-193">기본 설정은 헤드셋에서 가능한 최상의 시각적 품질을 제공 하기 위해 기본적으로 렌더링 하는 것입니다 (예: **4320 x 2160 (최고 품질)** 옵션).</span><span class="sxs-lookup"><span data-stu-id="c35d4-193">The default setting is to render natively (for example, the **4320 x 2160 (best quality)** option) to provide the best visual quality possible from your headset.</span></span>
* <span data-ttu-id="c35d4-194">다음과 같은 경우 **자동 upscaling (최상의 성능)** 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-194">Use the **Automatic upscaling (best performance)** option if:</span></span>
    * <span data-ttu-id="c35d4-195">PC가 해상도가 높은 헤드셋의 최소 그래픽 하드웨어 요구 사항을 충족 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-195">Your PC doesn't meet the minimum graphics hardware requirements for your headset with higher resolution displays</span></span>
    * <span data-ttu-id="c35d4-196">그래픽 성능 문제가 발생 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-196">You're seeing graphics performance issues</span></span>

<span data-ttu-id="c35d4-197">이 설정은 Windows 10, 버전 1903 이상에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-197">This setting is available on Windows 10, version 1903, or newer.</span></span>

### <a name="calibration"></a><span data-ttu-id="c35d4-198">보정</span><span class="sxs-lookup"><span data-stu-id="c35d4-198">Calibration</span></span>

<span data-ttu-id="c35d4-199">이 설정은 software IPD support가 포함 된 헤드셋의 IPD 보정을 조정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-199">This setting is to adjust the IPD calibration for headsets with software IPD support.</span></span>

### <a name="experience-options"></a><span data-ttu-id="c35d4-200">환경 옵션</span><span class="sxs-lookup"><span data-stu-id="c35d4-200">Experience options</span></span>

<span data-ttu-id="c35d4-201">이 고급 설정은 기본 헤드셋 디스플레이 새로 고침 빈도 환경을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-201">This advanced setting overrides the default headset display refresh rate experience.</span></span>

* <span data-ttu-id="c35d4-202">**자동 (기본값)**: PC의 하드웨어 구성에 따라 60 hz 또는 90-hz 환경을 자동으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-202">**Automatic (default)**: Automatically select the 60 Hz or 90-Hz experience based on your PC's hardware configuration.</span></span>
* <span data-ttu-id="c35d4-203">**60 Hz**</span><span class="sxs-lookup"><span data-stu-id="c35d4-203">**60 Hz**</span></span>
* <span data-ttu-id="c35d4-204">**90 Hz**</span><span class="sxs-lookup"><span data-stu-id="c35d4-204">**90 Hz**</span></span>

>[!Note]
><span data-ttu-id="c35d4-205">HP 반향 G2 헤드셋을 처음 설정 하는 경우 최상의 환경을 보장 하기 위해 환경이 90 Hz로 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-205">When first setting up HP Reverb G2 headset the experience will be changed to 90Hz to ensure the .best experience.</span></span>  <span data-ttu-id="c35d4-206">필요한 경우이를 다시 자동으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-206">If needed you can change this back to Automatic.</span></span>

### <a name="input-switching"></a><span data-ttu-id="c35d4-207">입력 전환</span><span class="sxs-lookup"><span data-stu-id="c35d4-207">Input switching</span></span>

<span data-ttu-id="c35d4-208">이 설정은 헤드셋의 현재 상태 센서에 대 한 응답으로 Windows Mixed Reality의 동작을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-208">This setting controls the behavior of Windows Mixed Reality in response to your headset's presence sensor:</span></span>

* <span data-ttu-id="c35d4-209">**헤드셋 상태 센서를 사용 하 여 자동으로 전환** (기본값): 헤드셋을 작성할 때마다 windows에서 자동으로 입력 (키보드, 마우스 ...)을 Windows Mixed Reality에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-209">**Automatically switch using headset presence sensor** (default): Windows will automatically direct input (keyboard, mouse...) to Windows Mixed Reality whenever you're wearing your headset.</span></span> <span data-ttu-id="c35d4-210">언제 든 지 Win + Y를 사용 하 여이를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-210">You can override this at any time with Win + Y.</span></span>
* <span data-ttu-id="c35d4-211">**Windows 로고 키 + Y를 사용 하 여 수동 전환**: windows는 헤드셋을 입고 있는 시기를 검색 하기 위해 헤드셋 상태 센서를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-211">**Manually switch using Windows logo key + Y**: Windows won't use the headset presence sensor to detect when you're wearing your headset.</span></span> <span data-ttu-id="c35d4-212">PC 데스크톱과 Windows Mixed Reality 간에 입력을 전환 하려면 Win + Y를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-212">You'll need to use Win + Y to switch your input between your PC desktop and Windows Mixed Reality.</span></span>

<span data-ttu-id="c35d4-213">이 설정은 Windows 10, 버전 1903 이상에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-213">This setting is available on Windows 10, version 1903, or newer.</span></span>

## <a name="installing-microsoft-edge"></a><span data-ttu-id="c35d4-214">Microsoft Edge 설치</span><span class="sxs-lookup"><span data-stu-id="c35d4-214">Installing Microsoft Edge</span></span> 

<span data-ttu-id="c35d4-215">Windows Mixed Reality 홈에서 새로운 Chromium 기반 Microsoft Edge를 사용 하려면 windows Mixed Reality 홈의 Win32 응용 프로그램 (예: 새 Microsoft Edge)에 대 한 기본 지원을 위해 Windows 10 버전 1903 이상으로 업그레이드 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-215">To use the new Chromium-based Microsoft Edge in Windows Mixed Reality home, upgrade to Windows 10 Version 1903 or later for native support of Win32 applications (like the new Microsoft Edge) in Windows Mixed Reality home.</span></span> <span data-ttu-id="c35d4-216">Windows 업데이트를 확인 하거나 [최신 버전의 Windows 10을 수동으로 설치](https://www.microsoft.com/software-download/windows10)합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-216">Check Windows Update or [manually install the latest version of Windows 10](https://www.microsoft.com/software-download/windows10).</span></span>

>[!IMPORTANT]
><span data-ttu-id="c35d4-217">새 Microsoft Edge는 VR 헤드셋을 위한 몰입 형 웹 환경을 만들기 위한 새로운 표준인 WebXR 지원으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-217">The new Microsoft Edge launches with support for WebXR, the new standard for creating immersive web experiences for VR headsets.</span></span> <span data-ttu-id="c35d4-218">새 Microsoft Edge를 설치 하는 경우 더 이상 Microsoft Edge에서 WebVR 환경을 재생할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-218">You will no longer be able to play WebVR experiences in Microsoft Edge if you install the new Microsoft Edge.</span></span>

### <a name="issues-with-the-new-microsoft-edge-in-windows-mixed-reality"></a><span data-ttu-id="c35d4-219">Windows Mixed Reality의 새로운 Microsoft Edge에 대 한 문제</span><span class="sxs-lookup"><span data-stu-id="c35d4-219">Issues with the new Microsoft Edge in Windows Mixed Reality</span></span>

<span data-ttu-id="c35d4-220">**2020-01 누적 업데이트에서 해결 된 Windows 10 버전 1903 이상 버전에서 해결 된 알려진 문제**</span><span class="sxs-lookup"><span data-stu-id="c35d4-220">**Known issues resolved by the 2020-01 Cumulative update for Windows 10 Version 1903 (or later)**</span></span>

- <span data-ttu-id="c35d4-221">새 Microsoft Edge를 포함 하 여 모든 Win32 앱을 시작 하면 헤드셋 디스플레이가 잠깐 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-221">Launching any Win32 app, including the new Microsoft Edge, causes the headset display to briefly freeze.</span></span>
- <span data-ttu-id="c35d4-222">Windows Mixed Reality 시작 메뉴에서 Microsoft Edge 타일이 사라집니다. "클래식 앱" 폴더에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-222">The Microsoft Edge tile disappears from the Windows Mixed Reality Start menu (you can find it in the “Classic apps” folder).</span></span>
- <span data-ttu-id="c35d4-223">이전 Microsoft Edge의 Windows는 여전히 혼합 현실 홈을 중심으로 하지만 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-223">Windows from the previous Microsoft Edge are still placed around the mixed reality home, but cannot be used.</span></span> <span data-ttu-id="c35d4-224">이러한 창을 활성화 하려고 하면 데스크톱 앱에서 Edge가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-224">Attempting to activate those windows launches Edge in the Desktop app.</span></span>
- <span data-ttu-id="c35d4-225">Mixed reality 홈에서 하이퍼링크를 선택 하면 혼합 현실 홈 대신 바탕 화면에서 웹 브라우저가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-225">Selecting a hyperlink in the mixed reality home launches a web browser on the desktop instead of the mixed reality home.</span></span>
- <span data-ttu-id="c35d4-226">WebVR 전시 앱은 WebVR 더 이상 지원 되지 않더라도 혼합 현실 홈에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-226">The WebVR Showcase app is present in the mixed reality home, despite WebVR no longer being supported.</span></span>
- <span data-ttu-id="c35d4-227">키보드 시작 및 시각적 개체에 대 한 일반적인 개선 사항</span><span class="sxs-lookup"><span data-stu-id="c35d4-227">General improvements to keyboard launch and visuals.</span></span>

<span data-ttu-id="c35d4-228">**추가 알려진 문제**</span><span class="sxs-lookup"><span data-stu-id="c35d4-228">**Additional known issues**</span></span>

- <span data-ttu-id="c35d4-229">Windows Mixed Reality에서 열린 웹 사이트는 혼합 현실 포털이 닫히면 Microsoft Edge windows가 혼합 현실 홈에 배치 된 위치에 그대로 유지 되는 경우 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-229">Websites open in Windows Mixed Reality will be lost when Mixed Reality Portal closes, though the Microsoft Edge windows will remain where they were placed in the mixed reality home.</span></span>
- <span data-ttu-id="c35d4-230">Microsoft Edge 창의 오디오는 spatialized 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-230">Audio from Microsoft Edge windows isn't spatialized.</span></span>
- <span data-ttu-id="c35d4-231">360 Viewer 확장 버전 2.3.8에서 수정 됨: Windows Mixed Reality에서 YouTube의 360 비디오를 열면 비디오가 헤드셋에서 왜곡 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-231">Fixed in 360 Viewer extension version 2.3.8: Opening a 360 video from YouTube in Windows Mixed Reality may result in the video being distorted in the headset.</span></span> <span data-ttu-id="c35d4-232">Edge를 다시 시작 하면이 문제를 해결 하기 위해 360 뷰어 확장이 업데이트 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-232">Restarting Edge should invisibly update the 360 Viewer extension to resolve this issue.</span></span> <span data-ttu-id="c35d4-233">`edge://system/`주소 표시줄에를 입력 하 고 "확장" 옆의 "확장" 단추를 선택 하 여 어떤 확장 버전이 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-233">You can confirm which version of the extension you have by entering `edge://system/` in the address bar and selecting the "Expand" button next to "extensions."</span></span>
- <span data-ttu-id="c35d4-234">Windows Mixed Reality 세션 중에는 **설정 > 시스템 > 디스플레이** 에서 일반 물리적 모니터로 가상 모니터가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-234">During Windows Mixed Reality sessions, virtual monitors will appear as generic physical monitors in **Settings > System > Display**.</span></span>

## <a name="launching-mixed-reality-after-the-first-time"></a><span data-ttu-id="c35d4-235">처음으로 혼합 된 현실 시작</span><span class="sxs-lookup"><span data-stu-id="c35d4-235">Launching mixed reality after the first time</span></span>

<span data-ttu-id="c35d4-236">혼합 현실를 두 번째로 입력 하는 것은 PC에 연결 되어 있는 동안 헤드셋을 다시 배치 하는 것 만큼 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-236">Entering mixed reality a second time is as easy as putting the headset back on while it's connected to your PC.</span></span> <span data-ttu-id="c35d4-237">시작 메뉴에서 열어 혼합 현실 포털 응용 프로그램을 수동으로 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-237">You can also launch the Mixed Reality Portal application manually by opening it from the Start menu.</span></span> <span data-ttu-id="c35d4-238">입력 및 오디오는 설정 하면 헤드셋으로 자동으로 라우팅하거나 키보드에서 **Windows + Y** 를 눌러 수동으로 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c35d4-238">Input and audio will route automatically to the headset when you put it on, or you can trigger this manually by pressing **Windows + Y** on your keyboard.</span></span>

## <a name="see-also"></a><span data-ttu-id="c35d4-239">추가 정보</span><span class="sxs-lookup"><span data-stu-id="c35d4-239">See also</span></span>

* [<span data-ttu-id="c35d4-240">커뮤니티에 질문하기</span><span class="sxs-lookup"><span data-stu-id="c35d4-240">Ask the community</span></span>](https://answers.microsoft.com)
* [<span data-ttu-id="c35d4-241">지원 문의</span><span class="sxs-lookup"><span data-stu-id="c35d4-241">Contact us for support</span></span>](https://support.microsoft.com/contactus/)
* [<span data-ttu-id="c35d4-242">설치 문제 해결</span><span class="sxs-lookup"><span data-stu-id="c35d4-242">Troubleshooting installation</span></span>](installation_errors.md)
* [<span data-ttu-id="c35d4-243">설치 문제 해결</span><span class="sxs-lookup"><span data-stu-id="c35d4-243">Troubleshooting setup</span></span>](wmr-setup-faq.md)
* [<span data-ttu-id="c35d4-244">Mixed Reality 학습</span><span class="sxs-lookup"><span data-stu-id="c35d4-244">Learn Mixed Reality</span></span>](learn-mixed-reality.md)
* [<span data-ttu-id="c35d4-245">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="c35d4-245">Motion controllers</span></span>](controllers-in-wmr.md)
* [<span data-ttu-id="c35d4-246">내부에서 외부로 추적의 작동 방식</span><span class="sxs-lookup"><span data-stu-id="c35d4-246">How inside-out tracking works</span></span>](tracking-system.md)
