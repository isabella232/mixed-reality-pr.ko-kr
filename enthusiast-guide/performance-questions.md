---
title: 성능 FAQ
description: 표준 소비자 지원 설명서를 벗어나는 성능 Windows 혼합 현실 문제 해결.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원, 성능
appliesto:
- Windows 10
ms.openlocfilehash: d6b37f8f6c964222b90fff57f0ba994c14fcaeab
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131967"
---
# <a name="performance-faqs"></a><span data-ttu-id="c93ae-104">성능 FAQ</span><span class="sxs-lookup"><span data-stu-id="c93ae-104">Performance FAQs</span></span>

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60hz-or-90hz-framerate"></a><span data-ttu-id="c93ae-105">Windows Mixed Reality 헤드셋이 60Hz 또는 90Hz 프레임 속도에서 렌더링 되나요?</span><span class="sxs-lookup"><span data-stu-id="c93ae-105">Is my Windows Mixed Reality headset rendering at 60Hz or 90Hz framerate</span></span>

<span data-ttu-id="c93ae-106">HDMI 2.0 포트와 4 개 이상의 실제 코어가 있는 CPU가 포함 된 불연속 GPU를 사용 하는 경우에는 90 Hz를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-106">If you have a discrete GPU with HDMI 2.0 ports and a CPU with four or more physical cores, you should be getting 90 Hz.</span></span> <span data-ttu-id="c93ae-107">확인 하려면 **장치 포털 > 성능** 탭을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-107">To confirm, check the **Device Portal > Performance** tab.</span></span>

<span data-ttu-id="c93ae-108">참고: GPU에 HDMI 1.4 출력만 있는 경우 DisplayPort를 사용 [2.0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 하 여 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-108">Note: If your GPU only has a HDMI 1.4 output, you can use a DisplayPort to [HDMI 2.0 adapter](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) as a workaround.</span></span>

<span data-ttu-id="c93ae-109">참고: "헤드셋 디스플레이"의 시각적 품질 설정은 Windows Mixed Reality 홈 환경의 렌더링에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-109">Note: The visual quality settings in "Headset display" only affect the rendering of the Windows Mixed Reality home experience.</span></span>

## <a name="my-pc-is-running-slowly"></a><span data-ttu-id="c93ae-110">내 PC가 느리게 실행 되 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-110">My PC is running slowly</span></span>

<span data-ttu-id="c93ae-111">시스템은 여러 가지 이유로 인해 속도가 느릴 수 있으며 대부분의 경우이는 몇 초 동안만 지속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-111">The system may be slow for many reasons and in most cases this only last a few seconds.</span></span> <span data-ttu-id="c93ae-112">오랜 기간 동안이 문제가 발생 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="c93ae-112">If you experience this problem over long periods of time:</span></span>

1. <span data-ttu-id="c93ae-113">바탕 화면에서 사용 하지 않는 응용 프로그램을 모두 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-113">Close all unused application on the desktop.</span></span>
2. <span data-ttu-id="c93ae-114">랩톱이 전원에 연결 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-114">Ensure that your laptop is plugged into a power source.</span></span>
3. <span data-ttu-id="c93ae-115">PC가 준비 중이 아닌지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-115">Make sure that the PC is not warming up.</span></span>
4. <span data-ttu-id="c93ae-116">Windows Mixed Reality 홈의 시각적 품질을 낮춥니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-116">Lower the visual quality in your Windows Mixed Reality home.</span></span>
5. <span data-ttu-id="c93ae-117">PC에 최신 [그래픽 드라이버가](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-117">Ensure that you have the latest [graphics drivers](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) for your PC.</span></span>

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a><span data-ttu-id="c93ae-118">혼합 현실 환경을 실행할 때 PC가 준비 중입니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-118">My PC is warming up as I run the Mixed Reality experiences.</span></span> <span data-ttu-id="c93ae-119">쿨 어떻게 할까요? 유지</span><span class="sxs-lookup"><span data-stu-id="c93ae-119">How do I keep it cool</span></span>

1. <span data-ttu-id="c93ae-120">배터리가 청구 되 고 전원에 전원이 꽂혀 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-120">Check that the battery is charged and the power source is plugged in.</span></span>
2. <span data-ttu-id="c93ae-121">PC 팬이 차단 되지 않았는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-121">Make sure that the PC fans are not blocked.</span></span>
3. <span data-ttu-id="c93ae-122">비교적 쿨 환경에서 PC를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-122">Use the PC in a relatively cool environment.</span></span>
4. <span data-ttu-id="c93ae-123">PC를 가리키는 열 원본 (예: sun 또는 열 통풍구)이 없는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-123">Make sure there are no heat sources (for example, the sun or heat vents) pointed at the PC.</span></span>

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a><span data-ttu-id="c93ae-124">내 시각적 개체가 고르지 않거나, 느리게 로드 되거나, 양호 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-124">My visuals are choppy, load slowly, or don't look good</span></span>

* <span data-ttu-id="c93ae-125">헤드셋이 PC의 올바른 그래픽 카드에 꽂혀 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-125">Make sure your headset is plugged into the correct graphics card on your PC.</span></span> <span data-ttu-id="c93ae-126">일부 Pc에는 통합 및 분리 된 그래픽 카드가 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-126">Some PCs have both integrated and discrete graphics cards.</span></span> <span data-ttu-id="c93ae-127">일반적으로 불연속 카드는 최상의 성능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-127">The discrete card will generally provide the best performance.</span></span> <span data-ttu-id="c93ae-128">[PC 하드웨어에 대해 자세히 알아보세요](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="c93ae-128">[Learn more about PC hardware](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).</span></span>
* <span data-ttu-id="c93ae-129">바탕 화면에서 사용 하지 않는 응용 프로그램을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-129">Close unused applications on your desktop.</span></span>
* <span data-ttu-id="c93ae-130">헤드셋이 snugly에 맞게 조정 되었는지 확인 합니다 (아래로, 더 높거나 왼쪽 및 오른쪽으로 이동).</span><span class="sxs-lookup"><span data-stu-id="c93ae-130">Make sure your headset fits snugly (move it lower and higher, or left and right, to adjust).</span></span>
* <span data-ttu-id="c93ae-131">**설정 > 혼합 현실 > 헤드셋 디스플레이** 에서 헤드셋의 시각적 설정을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-131">Adjust your headset's visual settings in **Settings > Mixed reality > Headset display** .</span></span> <span data-ttu-id="c93ae-132">"시각적 품질"을 "자동"으로 설정 하면 PC에 대 한 혼합 현실 환경이 자동으로 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-132">When "Visual quality" is set to "Automatic", the mixed reality experience for your PC will be chosen automatically.</span></span> <span data-ttu-id="c93ae-133">시각적 세부 정보를 보려면 "시각적 품질"을 "높음"으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-133">For more visual detail, set "Visual quality" to "High".</span></span> <span data-ttu-id="c93ae-134">시각적 개체가 고르지 않으면 더 낮은 설정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-134">If your visuals are choppy, select a lower setting.</span></span>
* <span data-ttu-id="c93ae-135">헤드셋 보정 노브를 조정 하 여 lenses가 pupils (IPD) 사이에 올바른 거리로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-135">Adjust the headset calibration knob to make sure that the lenses are set to the correct distance between your pupils (called IPD).</span></span> <span data-ttu-id="c93ae-136">IPD를 모르는 경우 optometrist은 사용자를 위해 측정 하거나 IPD를 측정 하기 위해 설계 된 웹 사이트를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-136">If you don't know your IPD, an optometrist should be able to measure it for you, or use a website designed to measure IPD.</span></span> <span data-ttu-id="c93ae-137">헤드셋에 보정 노브가 없는 경우 **설정 > 혼합 현실 > 헤드셋 표시** 를 선택 하 고 "보정 제어"를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-137">If the headset doesn't have a calibration knob, select **Settings > Mixed reality > Headset display** and adjust the "Calibration control".</span></span>
* <span data-ttu-id="c93ae-138">USB-C를 사용 하거나 HDMI 어댑터에 DisplayPort를 사용 하는 경우 다른 것을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-138">If you’re using a USB-C or DisplayPort to HDMI adapter, try a different one.</span></span> <span data-ttu-id="c93ae-139">[권장 어댑터를](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c93ae-139">See [recommended adapters.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)</span></span>
* <span data-ttu-id="c93ae-140">PC의 그래픽 카드에 연결 될 수 있는 추가 모니터의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-140">Disconnect any extra monitors that may be connected to your PC’s graphics card.</span></span>
* <span data-ttu-id="c93ae-141">Windows 스토어에서 다른 혼합 현실 앱을 사용해 보세요. 일부 앱은 컴퓨터 설치에서 더 잘 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c93ae-141">Try some different mixed reality apps from the Windows Store — some may work better with your computer setup.</span></span>
