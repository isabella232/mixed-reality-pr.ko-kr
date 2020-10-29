---
title: Unreal에서 입력 응시
description: HoloLens 및 Unreal Engine에 대 한 응시 입력 설정 자습서
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, HoloLens 2, 눈 추적, 응시 입력, 헤드 탑재 된 디스플레이, Unreal engine
ms.openlocfilehash: 477fbdc9c7ddb3b4e890e62150651d9227d4c19e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684857"
---
# <a name="gaze-input"></a><span data-ttu-id="9bd29-104">응시 입력</span><span class="sxs-lookup"><span data-stu-id="9bd29-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="9bd29-105">개요</span><span class="sxs-lookup"><span data-stu-id="9bd29-105">Overview</span></span>

<span data-ttu-id="9bd29-106">[Windows Mixed Reality 플러그인](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) 은 응시 입력을 위한 기본 제공 함수를 제공 하지 않지만 HoloLens 2는 눈 추적을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="9bd29-107">실제 추적 기능은 Unreal의 **탑재 된 표시** 및 **눈 추적** api에서 제공 하며 다음을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="9bd29-108">디바이스 정보</span><span class="sxs-lookup"><span data-stu-id="9bd29-108">Device information</span></span>
- <span data-ttu-id="9bd29-109">추적 센서</span><span class="sxs-lookup"><span data-stu-id="9bd29-109">Tracking sensors</span></span>
- <span data-ttu-id="9bd29-110">방향 및 위치</span><span class="sxs-lookup"><span data-stu-id="9bd29-110">Orientation and position</span></span>
- <span data-ttu-id="9bd29-111">창 클리핑</span><span class="sxs-lookup"><span data-stu-id="9bd29-111">Clipping panes</span></span>
- <span data-ttu-id="9bd29-112">데이터 및 추적 정보를 응시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-112">Gaze data and tracking information</span></span>

<span data-ttu-id="9bd29-113">모든 기능의 전체 목록은 실제 [헤드 탑재 된 표시](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) 및 [눈 추적](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) 설명서에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="9bd29-114">Unreal Api 외에도 HoloLens 2에 대 한 눈에 잘 맞는 [상호 작용](../../design/eye-gaze-interaction.md) 에 대 한 설명서를 확인 하 고 [hololens 2의 눈 추적](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) 작동 방식을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="9bd29-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](../../design/eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9bd29-115">아이 추적은 HoloLens 2 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="9bd29-116">눈 추적 사용</span><span class="sxs-lookup"><span data-stu-id="9bd29-116">Enabling eye tracking</span></span>
<span data-ttu-id="9bd29-117">Unreal의 Api를 사용 하려면 먼저 HoloLens 프로젝트 설정에서 응시 입력을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="9bd29-118">응용 프로그램이 시작 되 면 아래 스크린샷에 표시 된 동의 프롬프트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="9bd29-119">**예** 를 선택 하 여 사용 권한을 설정 하 고 입력에 대 한 액세스 권한을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="9bd29-120">언제 든 지이 설정을 변경 해야 하는 경우 **설정** 앱에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![눈 입력 권한](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="9bd29-122">Unreal의 HoloLens 눈동자 추적에는 stereoscopic 추적에 필요한 두 광선 (지원 되지 않음)이 아닌 단일 응시 광선이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="9bd29-123">이를 통해 모든 설정에서 HoloLens 2 앱에 응시 입력을 Unreal에 추가 하기 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="9bd29-124">입력 응시에 대 한 자세한 내용 및 혼합 현실의 사용자에 게 영향을 주는 방법에 대 한 자세한 내용은 아래 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9bd29-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="9bd29-125">대화형 환경을 구축할 때이에 대해 생각해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="9bd29-126">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="9bd29-126">Next Development Checkpoint</span></span>

<span data-ttu-id="9bd29-127">앞에서 설명한 실제 개발 검사점 경험을 수행 하는 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-127">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="9bd29-128">여기에서 다음 구성 요소를 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-128">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="9bd29-129">손 추적</span><span class="sxs-lookup"><span data-stu-id="9bd29-129">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="9bd29-130">또는 혼합 현실 플랫폼 기능 및 Api로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-130">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9bd29-131">HoloLens 카메라</span><span class="sxs-lookup"><span data-stu-id="9bd29-131">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="9bd29-132">언제 든 지 [실제 개발 검사점](unreal-development-overview.md#2-core-building-blocks) 으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bd29-132">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bd29-133">참조</span><span class="sxs-lookup"><span data-stu-id="9bd29-133">See also</span></span>
* [<span data-ttu-id="9bd29-134">조정</span><span class="sxs-lookup"><span data-stu-id="9bd29-134">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="9bd29-135">편안함</span><span class="sxs-lookup"><span data-stu-id="9bd29-135">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="9bd29-136">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="9bd29-136">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="9bd29-137">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="9bd29-137">Voice input</span></span>](../../out-of-scope/voice-design.md)
