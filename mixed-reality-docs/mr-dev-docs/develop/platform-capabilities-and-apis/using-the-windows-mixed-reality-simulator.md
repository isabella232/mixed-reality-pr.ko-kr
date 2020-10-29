---
title: Windows Mixed Reality 시뮬레이션 사용
description: Windows Mixed reality 시뮬레이터를 사용 하면 Windows Mixed Reality 몰입 형 헤드셋 없이 PC에서 혼합 현실 앱을 테스트할 수 있습니다.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality, 시뮬레이터, 테스트
ms.openlocfilehash: 72ce82770f80b6c22837ac9484d88a4497d6b8f8
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683558"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="906b1-104">Windows Mixed Reality 시뮬레이션 사용</span><span class="sxs-lookup"><span data-stu-id="906b1-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="906b1-105">Windows Mixed reality 시뮬레이터를 사용 하면 Windows Mixed Reality 몰입 형 헤드셋 없이 PC에서 혼합 현실 앱을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="906b1-106">Windows 10 크리에이터 스 업데이트부터 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-106">It is available beginning with the Windows 10 Creators Update.</span></span> <span data-ttu-id="906b1-107">시뮬레이터는 가상 컴퓨터를 사용 하지 않지만 [HoloLens 에뮬레이터](using-the-hololens-emulator.md)와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-107">The simulator is similar to the [HoloLens Emulator](using-the-hololens-emulator.md), though the simulator does not use a virtual machine.</span></span> <span data-ttu-id="906b1-108">시뮬레이터에서 실행 되는 앱은 몰입 형 헤드셋을 사용 하는 경우와 마찬가지로 Windows 10 desktop 사용자 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-108">Apps running in the simulator run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="906b1-109">일반적으로 몰입 형 헤드셋에서 센서에 의해 읽혀집니다 사용자 및 환경 입력이 키보드, 마우스 또는 Xbox 컨트롤러를 사용 하 여 시뮬레이션 됩니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-109">The human and environmental input that would usually be read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="906b1-110">앱은 시뮬레이터에서 실행 되도록 수정할 필요가 없으며 몰입 형 헤드셋에서 실행 되지 않는 것을 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-110">Apps don't need to be modified to run in the simulator, and don't know that they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="906b1-111">Windows Mixed Reality 시뮬레이터 사용</span><span class="sxs-lookup"><span data-stu-id="906b1-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="906b1-112">개발자 모드를 설정에서 **사용 하도록** 설정-> 업데이트 및 보안-개발자를 위한 ></span><span class="sxs-lookup"><span data-stu-id="906b1-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="906b1-113">바탕 화면에서 **혼합 현실 포털** 시작</span><span class="sxs-lookup"><span data-stu-id="906b1-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="906b1-114">포털을 처음 시작 하는 경우 설정 환경을 진행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="906b1-115">**시작** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-115">Click **Get started**</span></span>
   2. <span data-ttu-id="906b1-116">동의 **함을 클릭 하** 여 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-116">Click **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="906b1-117">**시뮬레이션에 대 한 설정 (개발자의 경우)** 을 클릭 하 여 물리적 장치 없이 설치를 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-117">Click **Set up for simulation (for developers)** to proceed through setup without a physical device</span></span>
   4. <span data-ttu-id="906b1-118">**설정** 을 클릭 하 여 선택을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-118">Click **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="906b1-119">Mixed Reality 포털의 왼쪽에 있는 **개발자 용** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-119">Click the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="906b1-120">시뮬레이션 전환 전환 **켜기로 전환**</span><span class="sxs-lookup"><span data-stu-id="906b1-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="906b1-121">시뮬레이션을 사용 하도록 설정 하면 기본적으로 왼쪽 시뮬레이션 된 6-DOF controller가 설치 되 고 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-121">Enabling simulation installs and enables the left simulated 6-DOF controller by default.</span></span>  <span data-ttu-id="906b1-122">Windows 10에서 2019 업데이트를 설치 하기 전에 시뮬레이션 된 6 DOF 컨트롤러를 설치 하려면 관리자 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-122">Prior to the Windows 10 May 2019 update, installing a simulated 6-DOF controller requires administrator permissions.</span></span>  <span data-ttu-id="906b1-123">사용자 계정 컨트롤 대화 상자가 나타나면 동의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-123">You must accept the User Account Control dialog if one appears.</span></span>

<span data-ttu-id="906b1-124">이제 시뮬레이션을 사용 하 여 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-124">You should now be running with simulation!</span></span>

<span data-ttu-id="906b1-125">설정에서 개발자 모드를 사용 하지 않도록 설정 하려면 혼합 현실 포털의 **개발자 용** 섹션에서 시뮬레이션 토글 스위치를 먼저 **해제** 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-125">If you want to disable Developer mode in Settings, you should first turn the Simulation toggle switch to **Off** in the **For developers** section of the Mixed Reality Portal.</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="906b1-126">혼합 현실 시뮬레이터에 앱 배포</span><span class="sxs-lookup"><span data-stu-id="906b1-126">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="906b1-127">시뮬레이터는 가상 머신을 사용 하지 않고 로컬 PC에서 실행 되므로 디버그할 때 유니버설 Windows 앱을 **로컬 컴퓨터** 에 배포 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-127">Since the simulator runs on your local PC without a Virtual Machine, you can simply deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="906b1-128">기본 시뮬레이터 입력</span><span class="sxs-lookup"><span data-stu-id="906b1-128">Basic simulator input</span></span>

<span data-ttu-id="906b1-129">시뮬레이터 제어는 일반적인 3D 비디오 게임과 [HoloLens 에뮬레이터](using-the-hololens-emulator.md)와 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-129">Controlling the simulator is very similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="906b1-130">키보드, 마우스 또는 Xbox 컨트롤러를 사용하여 사용할 수 있는 입력 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-130">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="906b1-131">몰입 형 헤드셋을 입고 하는 시뮬레이션 된 사용자의 작업을 전달 하 여 시뮬레이터를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-131">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="906b1-132">작업은 시뮬레이트된 사용자를 이동 하 고 몰입 형 헤드셋에서와 같이 응답 하는 앱과 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-132">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="906b1-133">**앞으로, 뒤로, 왼쪽 및 오른쪽으로 걷기** - 키보드의 W, A, S 및 D 키 또는 Xbox 컨트롤러의 왼쪽 스틱을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-133">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="906b1-134">마우스 **오른쪽 단추** 를 클릭 하 고 마우스를 끌거나, 키보드의 화살표 키 또는 Xbox 컨트롤러의 오른쪽 스틱을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-134">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="906b1-135">**작업 단추 컨트롤러에서 키를 누릅니다** . 마우스 오른쪽 단추로 마우스를 클릭 하거나 키보드에서 enter 키를 누르거나 Xbox 컨트롤러에서 A 단추를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-135">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="906b1-136">**홈 단추 컨트롤러에서 키를 누릅니다** . 키보드에서 Windows 키나 F2 키를 누르거나 Xbox 컨트롤러에서 B 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-136">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="906b1-137">**스크롤을 위한 컨트롤러 이동** -Alt 키를 누른 상태에서 마우스 오른쪽 단추를 누른 상태에서 마우스를 위아래로 끌거나 Xbox 컨트롤러에서 오른쪽 트리거와 단추를 누르고 오른쪽 스틱을 위아래로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-137">**Controller movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="906b1-138">추적 된 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="906b1-138">Tracked controllers</span></span>

<span data-ttu-id="906b1-139">혼합 현실 시뮬레이터는 최대 2 개의 직접 보관 된 동작 컨트롤러를 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-139">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="906b1-140">혼합 현실 포털에서 토글 스위치를 사용 하 여 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-140">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="906b1-141">시뮬레이트된 각 컨트롤러에는 다음이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-141">Each simulated controller has:</span></span>
* <span data-ttu-id="906b1-142">공간에서의 위치 및 방향</span><span class="sxs-lookup"><span data-stu-id="906b1-142">Position and orientation in space</span></span>
* <span data-ttu-id="906b1-143">홈 단추</span><span class="sxs-lookup"><span data-stu-id="906b1-143">Home button</span></span>
* <span data-ttu-id="906b1-144">메뉴 버튼</span><span class="sxs-lookup"><span data-stu-id="906b1-144">Menu button</span></span>
* <span data-ttu-id="906b1-145">그립 단추</span><span class="sxs-lookup"><span data-stu-id="906b1-145">Grip button</span></span>
* <span data-ttu-id="906b1-146">터치 패드</span><span class="sxs-lookup"><span data-stu-id="906b1-146">Touchpad</span></span>
* <span data-ttu-id="906b1-147">사용해</span><span class="sxs-lookup"><span data-stu-id="906b1-147">Thumbstick</span></span>
* <span data-ttu-id="906b1-148">배터리 수준</span><span class="sxs-lookup"><span data-stu-id="906b1-148">Battery level</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="906b1-149">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="906b1-149">Next Development Checkpoint</span></span>

<span data-ttu-id="906b1-150">앞서 소개한 Unity 개발 검사점 경험을 수행 하는 경우 배포 단계를 진행 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-150">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="906b1-151">여기에서 다음 [항목](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) 으로 이동 하거나 고급 서비스 추가로 바로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="906b1-151">From here, you can proceed to the next [topic](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) or jump directly to adding advanced services.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="906b1-152">고급 서비스</span><span class="sxs-lookup"><span data-stu-id="906b1-152">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a><span data-ttu-id="906b1-153">참조</span><span class="sxs-lookup"><span data-stu-id="906b1-153">See also</span></span>
* [<span data-ttu-id="906b1-154">HoloLens 에뮬레이터 사용</span><span class="sxs-lookup"><span data-stu-id="906b1-154">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="906b1-155">고급 혼합 현실 시뮬레이터 입력</span><span class="sxs-lookup"><span data-stu-id="906b1-155">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="906b1-156">Unity의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="906b1-156">Spatial mapping in Unity</span></span>](../../develop/unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="906b1-157">DirectX의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="906b1-157">Spatial mapping in DirectX</span></span>](../../develop/native/spatial-mapping-in-directx.md)
