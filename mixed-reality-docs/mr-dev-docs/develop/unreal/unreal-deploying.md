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
ms.openlocfilehash: e811bc1b82aa40e658f9c855b65446483dd8bef2
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609434"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="5cc15-104">Unreal의 디바이스에 배포</span><span class="sxs-lookup"><span data-stu-id="5cc15-104">Deploy to device in Unreal</span></span>

<span data-ttu-id="5cc15-105">다음 두 가지 방법으로 HoloLens 2에 Unreal 응용 프로그램을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-105">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="5cc15-106">Unreal 편집기에서 직접</span><span class="sxs-lookup"><span data-stu-id="5cc15-106">Directly from the Unreal editor</span></span>
* <span data-ttu-id="5cc15-107">장치 포털을 통해 업로드 된 패키지</span><span class="sxs-lookup"><span data-stu-id="5cc15-107">As a package uploaded via the device portal</span></span>

<span data-ttu-id="5cc15-108">두 옵션 모두 개발용으로 [장치 포털](../platform-capabilities-and-apis/using-the-windows-device-portal.md) 을 사용 하도록 HoloLens를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-108">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="5cc15-109">Unreal 편집기에서 장치에 배포</span><span class="sxs-lookup"><span data-stu-id="5cc15-109">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="5cc15-110">**시작** 단추 옆에 있는 드롭다운 화살표를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-110">Select the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="5cc15-111">처음에는 HoloLens 장치 옵션이 회색으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-111">Initially, the HoloLens device option will be grayed out.</span></span>

![시작 드롭다운 옵션](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="5cc15-113">**Device Manager** 를 열고 HoloLens는 장치 목록에 자동으로 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-113">Open the **Device Manager** and note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="5cc15-114">나열 되지 **않은 장치 추가** 섹션을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-114">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="5cc15-115">**플랫폼** 으로 **HoloLens** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-115">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="5cc15-116">장치의 IP 주소와 포트 정보를 콜론으로 구분 하 여 장치 식별자로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-116">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="5cc15-117">예를 들면 "127.0.0.1:10080" (USB를 통해 연결 된 경우)입니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-117">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="5cc15-118">장치 포털 사용자 이름 및 암호 자격 증명을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-118">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="5cc15-119">**추가** 를 누르고 장치 관리자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-119">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="5cc15-120">잘못 된 주소 또는 사용자 자격 증명과 같은 오류가 발생 하는 경우 메시지가 출력 로그에 인쇄 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-120">If there's an error, such as wrong address or user credentials, a message will print to the Output Log.</span></span>

![나열 되지 않은 장치 추가](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="5cc15-122">**시작** 단추 옆에 있는 드롭다운 화살표를 다시 선택 합니다. 이번에는 방금 추가한 HoloLens 장치가 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-122">Select the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="5cc15-123">Hololens에 빌드 및 배포할 HoloLens 장치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-123">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="5cc15-124">장치를 빌드하기 위해 셰이더를 다시 컴파일하는 작업이 포함 될 수 있습니다 (특히 첫 번째 실행의 경우) .이는 다소 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-124">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="5cc15-125">앱이 실행 될 때까지 장치가 절전 모드로 전환 되지 않도록 합니다 (앱을 사용 해야 할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="5cc15-125">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="5cc15-126">그렇지 않으면 셰이더 컴파일이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-126">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="5cc15-127">장치 포털을 통해 장치에 배포</span><span class="sxs-lookup"><span data-stu-id="5cc15-127">Deploying to device via device portal</span></span>

<span data-ttu-id="5cc15-128">앱 패키징 및 배포에 대 한 자세한 지침은 [Unreal tutorial 시리즈](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-128">You can find detailed instructions on packaging and deploying an app in the [Unreal tutorial series](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="5cc15-129">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="5cc15-129">Next Development Checkpoint</span></span>

<span data-ttu-id="5cc15-130">앞에서 설명한 실제 개발 경험을 수행 하는 경우 배포 단계를 진행 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-130">If you're following the Unreal development journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="5cc15-131">여기에서 고급 서비스를 계속 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-131">From here, you can continue to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5cc15-132">고급 서비스</span><span class="sxs-lookup"><span data-stu-id="5cc15-132">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="5cc15-133">언제든지 [Unreal 개발 검사점](unreal-development-overview.md#4-streaming-and-deploying-to-a-device)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cc15-133">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) at any time.</span></span>
