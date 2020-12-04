---
title: Unreal의 디바이스에 배포
description: 장치를 장치에 배포 하는 방법에 대 한 가이드 2 개
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 장치에 배포, PC, 설명서, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
appliesto:
- HoloLens 2
ms.openlocfilehash: ef33e037d6ab6a69059c1452b71a428fe51836b9
ms.sourcegitcommit: d56e7dd6c917ddc4ead0792ebff21891921174b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564023"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="f99aa-104">Unreal의 디바이스에 배포</span><span class="sxs-lookup"><span data-stu-id="f99aa-104">Deploy to device in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="f99aa-105">개요</span><span class="sxs-lookup"><span data-stu-id="f99aa-105">Overview</span></span>
<span data-ttu-id="f99aa-106">다음 두 가지 방법으로 HoloLens 2에 Unreal 응용 프로그램을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-106">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="f99aa-107">Unreal 편집기에서 직접</span><span class="sxs-lookup"><span data-stu-id="f99aa-107">Directly from the Unreal editor</span></span>
* <span data-ttu-id="f99aa-108">장치 포털을 통해 업로드 된 패키지</span><span class="sxs-lookup"><span data-stu-id="f99aa-108">As a package uploaded via the device portal</span></span>

<span data-ttu-id="f99aa-109">두 옵션 모두 개발용으로 [장치 포털](../platform-capabilities-and-apis/using-the-windows-device-portal.md) 을 사용 하도록 HoloLens를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-109">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="f99aa-110">Unreal 편집기에서 장치에 배포</span><span class="sxs-lookup"><span data-stu-id="f99aa-110">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="f99aa-111">**시작** 단추 옆에 있는 드롭다운 화살표를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-111">Click the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="f99aa-112">처음에는 HoloLens 장치 옵션이 회색으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-112">Initially, the HoloLens device option will be grayed out.</span></span>

![시작 드롭다운 옵션](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="f99aa-114">**Device Manager** 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-114">Open the **Device Manager**.</span></span> <span data-ttu-id="f99aa-115">HoloLens는 장치 목록에 자동으로 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-115">Note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="f99aa-116">나열 되지 **않은 장치 추가** 섹션을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-116">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="f99aa-117">**플랫폼** 으로 **HoloLens** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-117">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="f99aa-118">장치의 IP 주소와 포트 정보를 콜론으로 구분 하 여 장치 식별자로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-118">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="f99aa-119">예를 들면 "127.0.0.1:10080" (USB를 통해 연결 된 경우)입니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-119">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="f99aa-120">장치 포털 사용자 이름 및 암호 자격 증명을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-120">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="f99aa-121">**추가** 를 누르고 장치 관리자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-121">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="f99aa-122">오류가 발생 하는 경우 (예: 잘못 된 주소, 사용자 이름 또는 암호) 출력 로그에 메시지가 인쇄 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-122">In the case of an error (such as wrong address, user name or password), a message will be printed to the Output Log.</span></span>

![나열 되지 않은 장치 추가](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="f99aa-124">**시작** 단추 옆에 있는 드롭다운 화살표를 다시 클릭 합니다. 이번에는 방금 추가한 HoloLens 장치가 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-124">Click the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="f99aa-125">Hololens에 빌드 및 배포할 HoloLens 장치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-125">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="f99aa-126">장치를 빌드하기 위해 셰이더를 다시 컴파일하는 작업이 포함 될 수 있습니다 (특히 첫 번째 실행의 경우) .이는 다소 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-126">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="f99aa-127">앱이 실행 될 때까지 장치가 절전 모드로 전환 되지 않도록 합니다 (앱을 사용 해야 할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="f99aa-127">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="f99aa-128">그렇지 않으면 셰이더 컴파일이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-128">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="f99aa-129">장치 포털을 통해 장치에 배포</span><span class="sxs-lookup"><span data-stu-id="f99aa-129">Deploying to device via device portal</span></span>

<span data-ttu-id="f99aa-130">[앱 패키징 및 배포](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) 에 대 한 자세한 지침은 unreal 자습서 시리즈 시작의 마지막 섹션에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-130">You can find detailed instructions on [packaging and deploying an app](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="f99aa-131">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="f99aa-131">Next Development Checkpoint</span></span>

<span data-ttu-id="f99aa-132">앞에서 설명한 실제 개발 검사점 경험을 수행 하는 경우 배포 단계를 진행 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-132">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="f99aa-133">여기에서 고급 서비스 추가를 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-133">From here, you can proceed to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f99aa-134">고급 서비스</span><span class="sxs-lookup"><span data-stu-id="f99aa-134">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="f99aa-135">언제든지 [Unreal 개발 검사점](unreal-development-overview.md#4-streaming-and-deploying-to-a-device)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f99aa-135">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) at any time.</span></span>
