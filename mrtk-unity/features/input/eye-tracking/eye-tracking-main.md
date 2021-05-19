---
title: 시선 추적
description: MRTK의 눈 추적 방문 페이지
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, EyeTracking,
ms.openlocfilehash: 2ee19cab7a7e8ec954f7694c8f06c836d5510644
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144014"
---
# <a name="eye-tracking-in-the-mixed-reality-toolkit"></a><span data-ttu-id="541da-104">Mixed Reality Toolkit의 눈동자 추적</span><span class="sxs-lookup"><span data-stu-id="541da-104">Eye tracking in the Mixed Reality Toolkit</span></span>

![MRTK의 아이 추적](../../images/eye-tracking/mrtk_et_compilation.png)

<span data-ttu-id="541da-106">_HoloLens 2_ 는 새롭고 강력한 새 입력을 제공 합니다. 눈 추적!</span><span class="sxs-lookup"><span data-stu-id="541da-106">_HoloLens 2_ offers an exciting and powerful new input: Eye tracking!</span></span>
<span data-ttu-id="541da-107">아이 추적을 사용 하면 사용자의 보기에서 빠르고 쉽게 holograms를 사용 하 고 사용자의 의도를 파악 하 여 시스템을 더 효율적으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="541da-107">Eye tracking enables users to quickly and effortlessly engage with holograms across their view and can make your system smarter by better identifying a user's intention.</span></span> <span data-ttu-id="541da-108">혼합 현실에서 눈 추적을 위한 강력한 응용 프로그램 및 디자인 지침에 대해 설명 하는 것과 같은 자세한 내용은 HoloLens에 대 한 Microsoft의 Mixed Reality [설명서](/windows/mixed-reality/eye-tracking) 를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="541da-108">Check out Microsoft's Mixed Reality [documentation on eye tracking on HoloLens 2](/windows/mixed-reality/eye-tracking) for more details, such as explaining powerful applications and design guidelines for eye tracking in mixed reality.</span></span>

<span data-ttu-id="541da-109">눈동자 추적의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="541da-109">New to eye tracking?</span></span> <span data-ttu-id="541da-110">문제없습니다!</span><span class="sxs-lookup"><span data-stu-id="541da-110">No problem!</span></span> <span data-ttu-id="541da-111">[혼합 현실 도구 키트](https://github.com/Microsoft/MixedRealityToolkit-Unity)에서 시작 하는 데 도움이 되는 다양 한 비디오, 자습서 및 샘플이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="541da-111">There are a number of videos, tutorials and samples to get you started in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)!</span></span>
<span data-ttu-id="541da-112">먼저 눈에 잘 맞는 상호 작용에 대 한 모범 사례를 보여 주는 몇 가지 기존 눈 추적 샘플을 살펴보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="541da-112">It is recommended to start by exploring some of the existing eye tracking samples that demonstrate best practices for eye-based interactions.</span></span> <span data-ttu-id="541da-113">그런 다음 이러한 샘플을 사용 하 여 사용자와 관련이 있는 파트를 앱으로 끌어올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="541da-113">You can then use these samples to pull the parts that seem relevant to you into your app.</span></span> <span data-ttu-id="541da-114">마지막으로, 앱에서 눈 추적 작업을 수행 하기 위해 핵심 구성 요소를 사용 하 여 새 장면을 설정 하는 방법에 대해서도 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="541da-114">Finally, we also describe how to set up a fresh scene with the core components to get eye tracking working in your app.</span></span>

1. [<span data-ttu-id="541da-115">MRTK 눈동자 추적 샘플</span><span class="sxs-lookup"><span data-stu-id="541da-115">MRTK eye tracking samples</span></span>](../../example-scenes/eye-tracking-examples-overview.md)

2. [<span data-ttu-id="541da-116">MRTK 눈동자 추적 설정</span><span class="sxs-lookup"><span data-stu-id="541da-116">MRTK eye tracking setup</span></span>](eye-tracking-basic-setup.md)

3. [<span data-ttu-id="541da-117">코드를 통해 눈 추적 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="541da-117">Accessing eye tracking data via Code</span></span>](eye-tracking-eye-gaze-provider.md)

4. [<span data-ttu-id="541da-118">장치에서 눈 추적 보정의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="541da-118">Validate eye tracking calibration on device</span></span>](eye-tracking-is-user-calibrated.md)

## <a name="see-also"></a><span data-ttu-id="541da-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="541da-119">See also</span></span>

- [<span data-ttu-id="541da-120">MRTK 눈동자 추적 설정</span><span class="sxs-lookup"><span data-stu-id="541da-120">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="541da-121">코드를 통한 MRTK 눈동자 추적</span><span class="sxs-lookup"><span data-stu-id="541da-121">MRTK Eye Tracking via Code</span></span>](eye-tracking-eye-gaze-provider.md)
- [<span data-ttu-id="541da-122">MRTK 눈동자 추적 보정</span><span class="sxs-lookup"><span data-stu-id="541da-122">MRTK Eye Tracking Calibration</span></span>](eye-tracking-is-user-calibrated.md)
- [<span data-ttu-id="541da-123">HoloLens 2 눈동자 추적 설명서</span><span class="sxs-lookup"><span data-stu-id="541da-123">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)