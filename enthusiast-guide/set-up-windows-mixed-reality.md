---
title: Windows Mixed Reality 설정
description: Windows Mixed Reality 동작 컨트롤러, 음성 및 오디오를 설정 하 고 안전한 재생 공간에 대 한 공간 경계를 정의 하는 방법입니다.
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 시작, 설정, 동작 컨트롤러, 컨트롤러, 음성, 오디오, 장착 됨, 경계, 그래픽 드라이버, Microsoft Edge, chromium
ms.openlocfilehash: cd59fd34dd00edc98d209681cc1239895c36ada2
ms.sourcegitcommit: 55a6a0b481238e7a2e3278a51583b6bda0eb259a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434633"
---
# <a name="set-up-windows-mixed-reality"></a><span data-ttu-id="d0f65-104">Windows Mixed Reality 설정</span><span class="sxs-lookup"><span data-stu-id="d0f65-104">Set up Windows Mixed Reality</span></span>

## <a name="get-ready"></a><span data-ttu-id="d0f65-105">준비</span><span class="sxs-lookup"><span data-stu-id="d0f65-105">Get ready</span></span>

<span data-ttu-id="d0f65-106">Windows Mixed Reality를 실행 하려면 다음이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-106">To run Windows Mixed Reality, you'll need:</span></span>

* <span data-ttu-id="d0f65-107">호환 되는 혼합 현실 모던 헤드셋.</span><span class="sxs-lookup"><span data-stu-id="d0f65-107">A compatible mixed reality immersive headset.</span></span> [<span data-ttu-id="d0f65-108">자세한 정보</span><span class="sxs-lookup"><span data-stu-id="d0f65-108">Learn more</span></span>](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)
* <span data-ttu-id="d0f65-109">[Windows Mixed Reality READY PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 와 헤드셋에 대 한 올바른 포트</span><span class="sxs-lookup"><span data-stu-id="d0f65-109">A [Windows Mixed Reality-ready PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) with the correct ports for your headset</span></span>
* <span data-ttu-id="d0f65-110">동작 [컨트롤러](controllers-in-wmr.md), Xbox 컨트롤러 또는 마우스 및 키보드</span><span class="sxs-lookup"><span data-stu-id="d0f65-110">Motion [controllers](controllers-in-wmr.md), an Xbox controller, or a mouse and keyboard</span></span>
* <span data-ttu-id="d0f65-111">마이크가 있는 헤드폰 (헤드셋에서 기본 제공 되지 않는 경우)</span><span class="sxs-lookup"><span data-stu-id="d0f65-111">Headphones with a mic (if your headset doesn't have them built in)</span></span>
* <span data-ttu-id="d0f65-112">열려 있는 많은 공간</span><span class="sxs-lookup"><span data-stu-id="d0f65-112">A large, open space</span></span>

## <a name="get-set"></a><span data-ttu-id="d0f65-113">집합 가져오기</span><span class="sxs-lookup"><span data-stu-id="d0f65-113">Get set</span></span>

<span data-ttu-id="d0f65-114">공간을 준비 합니다 (오버 헤드 공간 포함).</span><span class="sxs-lookup"><span data-stu-id="d0f65-114">Prepare your space (including your overhead space).</span></span> <span data-ttu-id="d0f65-115">사용할 영역에 장애물, 위험 또는 손상 된 항목이 없는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-115">Make sure there are no obstacles, hazards, or fragile items in the area you’ll be using.</span></span> <span data-ttu-id="d0f65-116">계단의 위쪽 이나 더 낮은 천장 팬에서 설정 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="d0f65-116">Don’t set up at the top of a staircase or under an extra-low ceiling fan.</span></span> <span data-ttu-id="d0f65-117">영역에서 트 및 장애물을 제거 하 고, 사용자와 헤드셋을 사용 하는 모든 사용자가 [안전 지침](https://support.microsoft.com/help/4039969)을 읽고 이해 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-117">Remove breakables and obstacles from the area, and make sure that you and anyone who uses your headset reads and understands the [safety guidelines](https://support.microsoft.com/help/4039969).</span></span>

## <a name="go"></a><span data-ttu-id="d0f65-118">지금</span><span class="sxs-lookup"><span data-stu-id="d0f65-118">Go!</span></span>

<span data-ttu-id="d0f65-119">공간이 준비 되 면 헤드셋에 연결 하지만 아직 배치 하지 마세요. 먼저 PC에서 일부 설정을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-119">Once your space is ready, plug in your  headset, but don't put it on quite yet—first we'll need to do some setup on your PC.</span></span> <span data-ttu-id="d0f65-120">PC 검사를 실행 하 고, 일부 소프트웨어를 다운로드 하 고, 컨트롤러를 연결 하 고, 장애물을 방지 하는 데 도움이 되는 [경계](boundary-questions.md) 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-120">We’ll run a PC check, download some software, connect your controllers, and create a [boundary](boundary-questions.md) to help you avoid obstacles.</span></span>

<span data-ttu-id="d0f65-121">그런 다음 재미 있는 부분을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-121">Then comes the fun part—put on your headset and enter the mixed world.</span></span> <span data-ttu-id="d0f65-122">Cortana는 둘러보기를 제공 하기 위해 대기 중입니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-122">Cortana will be waiting to give you a tour.</span></span> <span data-ttu-id="d0f65-123">즐거운 시간 보내세요!</span><span class="sxs-lookup"><span data-stu-id="d0f65-123">Have fun!</span></span>

## <a name="get-familiar-with-your-motion-controllers"></a><span data-ttu-id="d0f65-124">동작 컨트롤러에 대해 알아보기</span><span class="sxs-lookup"><span data-stu-id="d0f65-124">Get familiar with your motion controllers</span></span>

<span data-ttu-id="d0f65-125">헤드셋에 기본 제공 된 라디오가 있는 경우 헤드셋과 함께 제공 되는 컨트롤러는 팩터리에서 페어링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-125">If your headset has a built-in radio, the controllers that come with your headset are paired to it in the factory.</span></span> <span data-ttu-id="d0f65-126">새 컨트롤러와 헤드셋을 처음 켜면 이미 페어링 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-126">When you first turn on your new controllers and headset, they will already be paired.</span></span>

<span data-ttu-id="d0f65-127">기본 제공 되는 라디오가 없는 헤드셋이 있는 경우 플레이어를 PC에 연결 하 여 동작 컨트롤러를 설정 해야 합니다 (2018 이후 제조 된 대부분의 헤드셋은 기본 제공 라디오).</span><span class="sxs-lookup"><span data-stu-id="d0f65-127">If you have a headset without a built-in radio, you will have to set up your motion controllers by pairing them to your PC (most headsets manufactured after 2018 have built-in radio).</span></span>

<span data-ttu-id="d0f65-128">Xbox 게임 패드 또는 키보드와 마우스를 사용 하려는 경우에는 컨트롤러를 페어링 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-128">If you are only planning to use an Xbox gamepad or keyboard and mouse, you don’t need to pair your controllers.</span></span>  <span data-ttu-id="d0f65-129">컨트롤러를 사용 하려는 경우에는 해당 컨트롤러를 페어링 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-129">If you ever plan to use controllers, you should probably pair them.</span></span>

<span data-ttu-id="d0f65-130">**참고**: Windows Mixed Reality 동작 컨트롤러에는 Bluetooth 4.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-130">**Note**: Windows Mixed Reality motion controllers require Bluetooth 4.0.</span></span> <span data-ttu-id="d0f65-131">PC에 기본 제공 된 Bluetooth가 없는 경우에는 Bluetooth 4.0을 지 원하는 USB Bluetooth 어댑터를 연결 하 여 동작 컨트롤러를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-131">If your PC doesn't have built-in Bluetooth, you will need to plug in a USB Bluetooth adapter that supports Bluetooth 4.0 to enable your motion controllers.</span></span> <span data-ttu-id="d0f65-132">헤드셋에서 기본 제공 라디오를 사용 하는 경우 Bluetooth 어댑터가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-132">If you are using the built-in radio in your headset you don’t need a Bluetooth adapter.</span></span>

![동작 컨트롤러에 대해 알아보기](images/get_to_know_controllers.png)

<span data-ttu-id="d0f65-134">동작 컨트롤러를 쌍으로 연결 해야 하는 경우 [Windows Mixed Reality의 컨트롤러](controllers-in-wmr.md) 문서를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-134">If you need to pair your motion controllers, review [controllers in Windows Mixed Reality](controllers-in-wmr.md) article.</span></span>

## <a name="set-up-your-room-boundary"></a><span data-ttu-id="d0f65-135">대화방 경계 설정</span><span class="sxs-lookup"><span data-stu-id="d0f65-135">Set up your room boundary</span></span>

<span data-ttu-id="d0f65-136">방 규모 또는 책상 크기 조정 환경을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-136">Choose a room scale or desk scale experience:</span></span>

<span data-ttu-id="d0f65-137">**옵션 1: 모든 환경 (공간 규모가 라고도 함)에 대해 설정** 하면 대화방을 탐색할 수 있으며, 가장 몰입가 혼합 된 현실 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-137">**Option 1: Set me up for all experiences (also known as room scale)** will allow you to walk around the room and is the most immersive mixed reality experience.</span></span> <span data-ttu-id="d0f65-138">혼합 현실에 대해 최소 5 피트 x 7 피트 (1.5 미터 x 2 미터)의 공간을 확보 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-138">We recommend you at clear at least 5 foot x 7 foot (1.5 meters x 2 meters) of space for mixed reality.</span></span>

<span data-ttu-id="d0f65-139">**옵션 2: 사용자의 책상에서 작동 하는 (책상 크기 조정 라고도 함) 환경에 대해 설정** 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-139">**Option 2: Set me up for seated and standing (also known as desk scale)** experience will work at your desk.</span></span> <span data-ttu-id="d0f65-140">공간에 공간이 많지 않은 경우 좋은 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-140">It's a good option if you don't have a lot of room in your space.</span></span> <span data-ttu-id="d0f65-141">또한 경계 없이 헤드셋을 사용 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-141">It also means that you will be using your headset without a boundary.</span></span> <span data-ttu-id="d0f65-142">물리적 장애물을 방지 하는 데 도움이 되는 경계를 갖지 않으므로 한 곳에 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-142">You'll need to stay in one place, as you'll have no boundary to help you avoid physical obstacles.</span></span> <span data-ttu-id="d0f65-143">또한 일부 앱 및 게임은 경계와 함께 사용 되도록 설계 될 수 있으므로 의도 한 대로 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-143">Also, some apps and games may be designed to be used with a boundary, so they might not work as intended.</span></span>

![설정 선택](images/1050px-chooseasetup.png)

### <a name="if-you-choose-set-me-up-for-all-experiences"></a><span data-ttu-id="d0f65-145">"모든 환경에 대해 설정"을 선택 하는 경우</span><span class="sxs-lookup"><span data-stu-id="d0f65-145">If you choose "Set me up for all experiences"</span></span>

<span data-ttu-id="d0f65-146">곧 이동 하 고 상호 작용할 수 있는 가상 세계가 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-146">Soon, your room will become a virtual world where you can walk around and interact!</span></span> <span data-ttu-id="d0f65-147">혼합 현실 실행을 위해 공간에서 일부 공간을 확보 하 고 선택 취소 합니다 (예: 일부 바닥 공간을 지우고 위치를 대화방의 쪽으로 이동).</span><span class="sxs-lookup"><span data-stu-id="d0f65-147">Stand up and clear some space in your room for running mixed reality (e.g. clear some floor space and move your chair to the side of the room).</span></span> <span data-ttu-id="d0f65-148">혼합 현실에 대해 최소 5 피트 x 7 피트 (1.5 미터 x 2 미터)의 공간을 확보 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-148">We recommend you at clear at least 5 foot x 7 foot (1.5 meters x 2 meters) of space for mixed reality.</span></span>

![공간이 명확 한지 확인 합니다.](images/1050px-createaboundary.png)

<span data-ttu-id="d0f65-150">공간이 명확 한지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-150">Make sure your space is clear.</span></span>

![헤드셋 가운데 맞춤](images/1050px-createaboundary-2.png)

<span data-ttu-id="d0f65-152">헤드셋을 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-152">Center your headset.</span></span>

![경계 추적](images/1050px-createaboundary-3.png)

<span data-ttu-id="d0f65-154">경계를 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-154">Trace your boundary.</span></span>

![PC를 지속적으로 유지](images/1050px-createaboundary-4.png)

<span data-ttu-id="d0f65-156">헤드셋을 PC가 가리키는 상태로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-156">Keep your headset pointed toward your PC.</span></span>

![경계는 다음과 같습니다.](images/1050px-createaboundary-5.png)

<span data-ttu-id="d0f65-158">경계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-158">Here's your boundary.</span></span>

### <a name="if-you-choose-set-me-up-for-seated-and-standing"></a><span data-ttu-id="d0f65-159">"시작 및 고정에 대해 설정"을 선택 하는 경우</span><span class="sxs-lookup"><span data-stu-id="d0f65-159">If you choose "Set me up for seated and standing"</span></span>

<span data-ttu-id="d0f65-160">이 옵션을 선택 하는 경우 추가 단계를 수행 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-160">There are no additional steps required if you choose this option.</span></span>

## <a name="what-is-the-maximum-size-of-the-boundary"></a><span data-ttu-id="d0f65-161">경계의 최대 크기는 얼마 인가요?</span><span class="sxs-lookup"><span data-stu-id="d0f65-161">What is the maximum size of the boundary?</span></span>

<span data-ttu-id="d0f65-162">Windows Mixed Reality에서 현재 지원 되는 최대 경계 크기는 18x18ft (5.7 x 5.7 m) 또는 중앙의 13ft (4m) 반경입니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-162">The currently supported maximum boundary size in Windows Mixed Reality is 18x18ft (5.7x5.7m) or 13ft (4m) radius from the center.</span></span>  <span data-ttu-id="d0f65-163">경계 크기는 앵커 지점과 경계의 안정성을 위해 이동할 수 있는 앵커 지점 으로부터의 거리에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-163">The boundary size is dependent on the anchor point and how far from the anchor point you can move before you risk the stability of the boundary.</span></span>  <span data-ttu-id="d0f65-164">Windows Mixed Reality는 플랫폼의 단계 추상화를 기반으로 하며, 단계는에서 이동 하는 공간을 기반으로 하며,이 단계는 단일 앵커 (거의 모든 앱은 단일 좌표계를 포함 함)에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-164">Windows Mixed Reality is built on a stage abstraction in the platform, the stage being the space you move around in, and that stage depends on a single anchor (which nearly every app also assumes – it’s how Vive and Oculus work too, as they only have a single coordinate system).</span></span>  <span data-ttu-id="d0f65-165">이는 내부 추적을 사용 하는 것이 중요 한 이유는 앵커 지점에서 더 멀리 이동할 때 헤드셋 추적이 안정적으로 경계를 유지 하는 것 이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-165">The reason that this is important is that with inside-out tracking, as you move further away from an anchor point the headset tracking is reliable at keeping the boundary stable.</span></span>  <span data-ttu-id="d0f65-166">경계는 물리적 장애물을 방지 하기 위해 고안 된 것 이며,이는 이동 하는 중심에서 더 많은 문제를 해결 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-166">Where the boundary is intended to help avoid physical obstacles, it becomes more and more of a problem the further out from the center you go.</span></span>  <span data-ttu-id="d0f65-167">최대 경계 크기를 결정 하는 두 가지 요인이 있습니다. Windows Mixed Reality 헤드셋이 경계와 헤드셋 케이블의 길이에 가장 적합 한 공간 크기 조정 환경을 제공할 수 있는 최대 거리 (대부분의 Windows Mixed Reality 헤드셋은 10ft (3m)).</span><span class="sxs-lookup"><span data-stu-id="d0f65-167">Two factors went into the decision on maximum boundary size; the maximum distance at which Windows Mixed Reality headsets could provide the best room scale experience with a boundary and the length of the headset cable, which for most Windows Mixed Reality headsets is 10ft (3m).</span></span>

## <a name="set-up-speech"></a><span data-ttu-id="d0f65-168">음성 설정</span><span class="sxs-lookup"><span data-stu-id="d0f65-168">Set up speech</span></span>

<span data-ttu-id="d0f65-169">혼합 현실 내에서 Cortana 명령을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-169">You can enable Cortana commands inside of mixed reality.</span></span> <span data-ttu-id="d0f65-170">이렇게 하면 혼합 현실 내에서 음성 명령을 사용 하 여 텔레포트 하 고 앱을 열고 다른 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-170">This allows you to use speech commands inside of mixed reality to teleport, open apps, and do other things.</span></span> <span data-ttu-id="d0f65-171">이에 대 한 자세한 내용은 [Mixed Reality 배우기](learn-mixed-reality.md) 장에서 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="d0f65-171">You'll learn more about this in the [Learn Mixed Reality](learn-mixed-reality.md) chapter.</span></span>

![혼합 현실에서 음성 사용이 더 좋습니다.](images/1050px-betterwithspeech.png)

## <a name="set-up-your-audio-headset"></a><span data-ttu-id="d0f65-173">오디오 헤드셋 설정</span><span class="sxs-lookup"><span data-stu-id="d0f65-173">Set up your audio headset</span></span>

<span data-ttu-id="d0f65-174">Samsung HMD Odyssey (통합 AKG 헤드폰 및 통합 된 이중 마이크 배열 포함)를 구입 하지 않은 경우 마이크와 헤드폰이 모두 있는 오디오 헤드셋을 가져와 헤드셋의 3.5 mm 오디오 잭에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-174">Unless you purchased a Samsung HMD Odyssey (which has integrated AKG headphones and an integrated dual microphone array), you will need to get an audio headset (that has both microphone and headphones) and plug that into your headset's 3.5mm audio jack.</span></span> <span data-ttu-id="d0f65-175">헤드셋 용 3.5 m a x 오디오는 헤드셋 모델에 따라 헤드셋 센터의 아래쪽에 있거나 헤드셋 센터에서 들어오는 짧은 오디오 케이블의 끝에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-175">The 3.5mm audio jack for your headset will - depending on the headset model - be located either on the underside of the headset visor or at the end of a short audio cable coming out of the headset visor.</span></span>

## <a name="adjusting-your-headsets-display-settings"></a><span data-ttu-id="d0f65-176">헤드셋의 디스플레이 설정 조정</span><span class="sxs-lookup"><span data-stu-id="d0f65-176">Adjusting your headset's display settings</span></span>

<span data-ttu-id="d0f65-177">Windows Mixed Reality는 PC의 하드웨어 구성에 따라 품질 및 성능의 균형을 유지 하는 표시 설정을 자동으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-177">Windows Mixed Reality automatically chooses display settings that balance quality and performance, based on your PC's hardware configuration.</span></span> <span data-ttu-id="d0f65-178">이러한 설정을 조정 하려면 **설정 > 혼합 현실 > 헤드셋 표시**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-178">To adjust these settings, go to **Settings > Mixed Reality > Headset display**.</span></span>

### <a name="visuals"></a><span data-ttu-id="d0f65-179">시각적 개체</span><span class="sxs-lookup"><span data-stu-id="d0f65-179">Visuals</span></span>

<span data-ttu-id="d0f65-180">이 설정은 Mixed reality 홈의 시각적 품질을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-180">This setting controls the visual quality of your Mixed reality home.</span></span> <span data-ttu-id="d0f65-181">기본값은 "Automatic"입니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-181">The default is "Automatic".</span></span>

### <a name="resolution"></a><span data-ttu-id="d0f65-182">해결 방법</span><span class="sxs-lookup"><span data-stu-id="d0f65-182">Resolution</span></span>

<span data-ttu-id="d0f65-183">헤드셋의 기본 해상도는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-183">Your headset's native resolution is shown here.</span></span>

<span data-ttu-id="d0f65-184">고해상도 디스플레이를 사용 하는 헤드셋 (예: 4320x2160이 표시 된 헤드셋)을 PC에 연결 하는 경우 혼합 현실 디스플레이 해상도를 조정 하는 설정이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-184">If you connect a headset with higher resolution displays (for example, headsets with 4320x2160 displays) to your PC, you'll see a setting to adjust the Mixed reality display resolution.</span></span>

* <span data-ttu-id="d0f65-185">이 설정은 Windows Mixed Reality 컴퍼지션 스택에 대해 기본적으로 렌더링 (예: 4320x2160) 할 수 있는 옵션을 제공 하거나, 컴퍼지션 스택이 더 낮은 해상도 및 upscale (예: 2880x1440에서 렌더링 하 고, upscale에서 4320x2160으로 렌더링)를 렌더링 하는 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-185">This setting provides the option for the Windows Mixed Reality composition stack to render natively (for example, at 4320x2160), or to have the composition stack render at a lower resolution and upscale (for example, render at 2880x1440 and upscale to 4320x2160).</span></span>
* <span data-ttu-id="d0f65-186">기본 설정은 헤드셋에서 가능한 최상의 시각적 품질을 제공 하기 위해 기본적으로 렌더링 하는 것입니다 (예: **4320 x 2160 (최고 품질)** 옵션).</span><span class="sxs-lookup"><span data-stu-id="d0f65-186">The default setting is to render natively (for example, the **4320 x 2160 (best quality)** option) to provide the best visual quality possible from your headset.</span></span>
* <span data-ttu-id="d0f65-187">PC가 해상도가 더 높은 헤드셋의 최소 그래픽 하드웨어 요구 사항을 충족 하지 않는 경우 및/또는 그래픽 성능 문제가 발생 하는 경우 **자동 upscaling 조정 (최상의 성능)** 옵션을 선택 하 여 사용해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-187">If your PC does not meet the minimum graphics hardware requirements for your headset with higher resolution displays, and/or if you're seeing graphics performance issues, you could try using selecting the **Automatic upscaling (best performance)** option.</span></span>

<span data-ttu-id="d0f65-188">이 설정은 Windows 10, 버전 1903 이상에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-188">This setting is available on Windows 10, version 1903, or newer.</span></span>

### <a name="calibration"></a><span data-ttu-id="d0f65-189">보정</span><span class="sxs-lookup"><span data-stu-id="d0f65-189">Calibration</span></span>

<span data-ttu-id="d0f65-190">이 설정은 software IPD support가 포함 된 헤드셋의 IPD 보정을 조정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-190">This setting is to adjust the IPD calibration for headsets with software IPD support.</span></span>

### <a name="experience-options"></a><span data-ttu-id="d0f65-191">환경 옵션</span><span class="sxs-lookup"><span data-stu-id="d0f65-191">Experience options</span></span>

<span data-ttu-id="d0f65-192">이 고급 설정은 기본 헤드셋 디스플레이 새로 고침 빈도 환경을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-192">This advanced setting overrides the default headset display refresh rate experience.</span></span>

* <span data-ttu-id="d0f65-193">**자동 (기본값)**: PC의 하드웨어 구성에 따라 60Hz 또는 90hz 환경을 자동으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-193">**Automatic (default)**: Automatically select the 60Hz or 90Hz experience based on your PC's hardware configuration.</span></span>
* <span data-ttu-id="d0f65-194">**60Hz**</span><span class="sxs-lookup"><span data-stu-id="d0f65-194">**60Hz**</span></span>
* <span data-ttu-id="d0f65-195">**90Hz**</span><span class="sxs-lookup"><span data-stu-id="d0f65-195">**90Hz**</span></span>

>[!Note]
><span data-ttu-id="d0f65-196">HP 반향 G2 헤드셋을 처음 설정 하는 경우 최상의 환경을 보장 하기 위해 환경이 90 Hz로 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-196">When first setting up HP Reverb G2 headset the experience will be changed to 90Hz to ensure the .best experience.</span></span>  <span data-ttu-id="d0f65-197">필요한 경우이를 다시 자동으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-197">If needed you can change this back to Automatic.</span></span>

### <a name="input-switching"></a><span data-ttu-id="d0f65-198">입력 전환</span><span class="sxs-lookup"><span data-stu-id="d0f65-198">Input switching</span></span>

<span data-ttu-id="d0f65-199">이 설정은 헤드셋의 현재 상태 센서에 대 한 응답으로 Windows Mixed Reality의 동작을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-199">This setting controls the behavior of Windows Mixed Reality in response to your headset's presence sensor:</span></span>

* <span data-ttu-id="d0f65-200">**헤드셋 상태 센서를 사용 하 여 자동으로 전환** (기본값): 헤드셋을 작성할 때마다 windows에서 자동으로 입력 (키보드, 마우스 ...)을 Windows Mixed Reality에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-200">**Automatically switch using headset presence sensor** (default): Windows will automatically direct input (keyboard, mouse...) to Windows Mixed Reality whenever you're wearing your headset.</span></span> <span data-ttu-id="d0f65-201">언제 든 지 Win + Y를 사용 하 여이를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-201">You can override this at anytime with Win + Y.</span></span>
* <span data-ttu-id="d0f65-202">**Windows 로고 키 + Y를 사용 하 여 수동 전환**: windows는 헤드셋을 입고 있는 시점을 검색 하기 위해 헤드셋 상태 센서를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-202">**Manually switch using Windows logo key + Y**: Windows will not use the headset presence sensor to detect when you're wearing your headset.</span></span> <span data-ttu-id="d0f65-203">PC 데스크톱과 Windows Mixed Reality 간에 입력을 전환 하려면 Win + Y를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-203">You'll need to use Win + Y to switch your input between your PC desktop and Windows Mixed Reality.</span></span>

<span data-ttu-id="d0f65-204">이 설정은 Windows 10, 버전 1903 이상에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-204">This setting is available on Windows 10, version 1903, or newer.</span></span>

## <a name="installing-microsoft-edge"></a><span data-ttu-id="d0f65-205">Microsoft Edge 설치</span><span class="sxs-lookup"><span data-stu-id="d0f65-205">Installing Microsoft Edge</span></span> 

<span data-ttu-id="d0f65-206">Windows Mixed Reality 홈에서 새로운 Chromium 기반 Microsoft Edge를 사용 하려면 windows Mixed Reality 홈의 Win32 응용 프로그램 (예: 새 Microsoft Edge)에 대 한 기본 지원을 위해 Windows 10 버전 1903 이상으로 업그레이드 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-206">To use the new Chromium-based Microsoft Edge in Windows Mixed Reality home, upgrade to Windows 10 Version 1903 or later for native support of Win32 applications (like the new Microsoft Edge) in Windows Mixed Reality home.</span></span> <span data-ttu-id="d0f65-207">Windows 업데이트를 확인 하거나 [최신 버전의 Windows 10을 수동으로 설치](https://www.microsoft.com/software-download/windows10)합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-207">Check Windows Update or [manually install the latest version of Windows 10](https://www.microsoft.com/software-download/windows10).</span></span>

>[!IMPORTANT]
><span data-ttu-id="d0f65-208">새 Microsoft Edge는 VR 헤드셋을 위한 몰입 형 웹 환경을 만들기 위한 새로운 표준인 WebXR 지원으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-208">The new Microsoft Edge launches with support for WebXR, the new standard for creating immersive web experiences for VR headsets.</span></span> <span data-ttu-id="d0f65-209">새 Microsoft Edge를 설치 하는 경우 더 이상 Microsoft Edge에서 WebVR 환경을 재생할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-209">You will no longer be able to play WebVR experiences in Microsoft Edge if you install the new Microsoft Edge.</span></span>

### <a name="issues-with-the-new-microsoft-edge-in-windows-mixed-reality"></a><span data-ttu-id="d0f65-210">Windows Mixed Reality의 새로운 Microsoft Edge에 대 한 문제</span><span class="sxs-lookup"><span data-stu-id="d0f65-210">Issues with the new Microsoft Edge in Windows Mixed Reality</span></span>

<span data-ttu-id="d0f65-211">**2020-01 누적 업데이트에서 해결 된 Windows 10 버전 1903 이상 버전에서 해결 된 알려진 문제**</span><span class="sxs-lookup"><span data-stu-id="d0f65-211">**Known issues resolved by the 2020-01 Cumulative update for Windows 10 Version 1903 (or later)**</span></span>

- <span data-ttu-id="d0f65-212">새 Microsoft Edge를 포함 하 여 모든 Win32 앱을 시작 하면 헤드셋 디스플레이가 잠깐 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-212">Launching any Win32 app, including the new Microsoft Edge, causes the headset display to briefly freeze.</span></span>
- <span data-ttu-id="d0f65-213">Windows Mixed Reality 시작 메뉴에서 Microsoft Edge 타일이 사라집니다. "클래식 앱" 폴더에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-213">The Microsoft Edge tile disappears from the Windows Mixed Reality Start menu (you can find it in the “Classic apps” folder).</span></span>
- <span data-ttu-id="d0f65-214">이전 Microsoft Edge의 Windows는 여전히 혼합 현실 홈을 중심으로 하지만 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-214">Windows from the previous Microsoft Edge are still placed around the mixed reality home, but cannot be used.</span></span> <span data-ttu-id="d0f65-215">이러한 창을 활성화 하려고 하면 데스크톱 앱 내에서 가장자리가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-215">Attempting to activate those windows launches Edge inside of the Desktop app.</span></span>
- <span data-ttu-id="d0f65-216">Mixed reality 홈에서 하이퍼링크를 선택 하면 혼합 현실 홈 대신 바탕 화면에서 웹 브라우저가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-216">Selecting a hyperlink in the mixed reality home launches a web browser on the desktop instead of the mixed reality home.</span></span>
- <span data-ttu-id="d0f65-217">WebVR 전시 앱은 WebVR 더 이상 지원 되지 않더라도 혼합 현실 홈에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-217">The WebVR Showcase app is present in the mixed reality home, despite WebVR no longer being supported.</span></span>
- <span data-ttu-id="d0f65-218">키보드 시작 및 시각적 개체에 대 한 일반적인 개선 사항</span><span class="sxs-lookup"><span data-stu-id="d0f65-218">General improvements to keyboard launch and visuals.</span></span>

<span data-ttu-id="d0f65-219">**추가 알려진 문제**</span><span class="sxs-lookup"><span data-stu-id="d0f65-219">**Additional known issues**</span></span>

- <span data-ttu-id="d0f65-220">Windows Mixed Reality에서 열린 웹 사이트는 혼합 현실 포털이 닫히면 Microsoft Edge windows가 혼합 현실 홈에 배치 된 위치에 그대로 유지 되는 경우 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-220">Websites open in Windows Mixed Reality will be lost when Mixed Reality Portal closes, though the Microsoft Edge windows will remain where they were placed in the mixed reality home.</span></span>
- <span data-ttu-id="d0f65-221">Microsoft Edge 창의 오디오는 spatialized 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-221">Audio from Microsoft Edge windows is not spatialized.</span></span>
- <span data-ttu-id="d0f65-222">360 Viewer 확장 버전 2.3.8에서 수정 됨: Windows Mixed Reality에서 YouTube의 360 비디오를 열면 비디오가 헤드셋에서 왜곡 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-222">Fixed in 360 Viewer extension version 2.3.8: Opening a 360 video from YouTube in Windows Mixed Reality may result in the video being distorted in the headset.</span></span> <span data-ttu-id="d0f65-223">Edge를 다시 시작 하면이 문제를 해결 하기 위해 360 뷰어 확장이 업데이트 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-223">Restarting Edge should invisibly update the 360 Viewer extension to resolve this issue.</span></span> <span data-ttu-id="d0f65-224">`edge://system/`주소 표시줄에를 입력 하 고 "확장" 옆의 "확장" 단추를 선택 하 여 어떤 확장 버전이 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-224">You can confirm which version of the extension you have by entering `edge://system/` in the address bar and selecting the "Expand" button next to "extensions."</span></span>
- <span data-ttu-id="d0f65-225">Windows Mixed Reality 세션 중에는 **설정 > 시스템 > 디스플레이**에서 일반 물리적 모니터로 가상 모니터가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-225">During Windows Mixed Reality sessions, virtual monitors will appear as generic physical monitors in **Settings > System > Display**.</span></span>

## <a name="launching-mixed-reality-after-the-first-time"></a><span data-ttu-id="d0f65-226">처음으로 혼합 된 현실 시작</span><span class="sxs-lookup"><span data-stu-id="d0f65-226">Launching mixed reality after the first time</span></span>

<span data-ttu-id="d0f65-227">혼합 현실를 두 번째로 입력 하는 것은 PC에 연결 되어 있는 동안 헤드셋을 다시 배치 하는 것 만큼 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-227">Entering mixed reality a second time is as easy as putting the headset back on while its connected to your PC.</span></span> <span data-ttu-id="d0f65-228">시작 메뉴에서 열어 혼합 현실 포털 응용 프로그램을 수동으로 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-228">You can also launch the Mixed Reality Portal application manually by opening it from the Start menu.</span></span> <span data-ttu-id="d0f65-229">입력 및 오디오는 설정 하면 헤드셋으로 자동으로 라우팅하거나 키보드에서 **Windows + Y** 를 눌러 수동으로 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0f65-229">Input and audio will route automatically to the headset when you put it on, or you can trigger this manually by pressing **Windows + Y** on your keyboard.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0f65-230">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0f65-230">See also</span></span>

* [<span data-ttu-id="d0f65-231">커뮤니티에 질문하기</span><span class="sxs-lookup"><span data-stu-id="d0f65-231">Ask the community</span></span>](https://answers.microsoft.com)
* [<span data-ttu-id="d0f65-232">지원 문의</span><span class="sxs-lookup"><span data-stu-id="d0f65-232">Contact us for support</span></span>](https://support.microsoft.com/contactus/)
* [<span data-ttu-id="d0f65-233">설치 문제 해결</span><span class="sxs-lookup"><span data-stu-id="d0f65-233">Troubleshooting installation</span></span>](installation_errors.md)
* [<span data-ttu-id="d0f65-234">설치 문제 해결</span><span class="sxs-lookup"><span data-stu-id="d0f65-234">Troubleshooting setup</span></span>](set-up-questions.md)
* [<span data-ttu-id="d0f65-235">Mixed Reality 학습</span><span class="sxs-lookup"><span data-stu-id="d0f65-235">Learn Mixed Reality</span></span>](learn-mixed-reality.md)
* [<span data-ttu-id="d0f65-236">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="d0f65-236">Motion controllers</span></span>](controllers-in-wmr.md)
* [<span data-ttu-id="d0f65-237">내부에서 외부로 추적의 작동 방식</span><span class="sxs-lookup"><span data-stu-id="d0f65-237">How inside-out tracking works</span></span>](tracking-system.md)
