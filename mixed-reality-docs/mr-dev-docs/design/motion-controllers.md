---
title: 모션 컨트롤러
description: 응용 프로그램에서 혼합 현실 동작 컨트롤러를 사용 하 여 입력 상호 작용을 설정 하 고 쌍을 설정 하는 방법에 대해 알아봅니다.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof 컨트롤러, 동작 컨트롤러, 페어링, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, 스크롤, 그립, 상태
ms.openlocfilehash: 367c9d9e0179c82af05af3fded9341ff7960d19e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583665"
---
# <a name="motion-controllers"></a><span data-ttu-id="a8c47-104">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="a8c47-104">Motion controllers</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="a8c47-105">동작 컨트롤러는 사용자가 혼합 현실에서 작업을 수행할 수 있게 해 주는 [하드웨어 액세서리](../discover/hardware-accessories.md) 입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-105">Motion controllers are [hardware accessories](../discover/hardware-accessories.md) that allow users to take action in mixed reality.</span></span> <span data-ttu-id="a8c47-106">[제스처](gaze-and-commit.md#composite-gestures) 를 통한 동작 컨트롤러의 이점은 컨트롤러의 공간이 정확 하 여 디지털 개체와의 세분화 된 상호 작용을 가능 하 게 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-106">An advantage of motion controllers over [gestures](gaze-and-commit.md#composite-gestures) is that the controllers have a precise position in space, allowing for fine grained interaction with digital objects.</span></span> <span data-ttu-id="a8c47-107">Windows Mixed Reality 모던 헤드셋의 경우, 동작 컨트롤러는 사용자가 전 세계에서 작업을 수행 하는 기본 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-107">For Windows Mixed Reality immersive headsets, motion controllers are the primary way that users will take action in their world.</span></span><br>
        <br>
        <span data-ttu-id="a8c47-108">*이미지: Windows Mixed Reality 동작 컨트롤러*</span><span class="sxs-lookup"><span data-stu-id="a8c47-108">*Image: A Windows Mixed Reality motion controller*</span></span>
    :::column-end:::
        :::column:::
       ![Windows Mixed Reality 동작 컨트롤러](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="device-support"></a><span data-ttu-id="a8c47-110">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="a8c47-110">Device support</span></span>

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="a8c47-111"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="a8c47-111"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="a8c47-112"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a8c47-112"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="a8c47-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a8c47-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="a8c47-114"><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="a8c47-114"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="a8c47-115">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="a8c47-115">Motion controllers</span></span></td>
     <td>❌</td>
     <td>❌</td>
     <td><span data-ttu-id="a8c47-116">✔️</span><span class="sxs-lookup"><span data-stu-id="a8c47-116">✔️</span></span></td>
</tr>
</table>

## <a name="hardware-details"></a><span data-ttu-id="a8c47-117">하드웨어 세부 정보</span><span class="sxs-lookup"><span data-stu-id="a8c47-117">Hardware details</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="a8c47-118">Windows Mixed Reality 동작 컨트롤러는 몰입 형 헤드셋의 센서를 사용 하 여 뷰 필드에서 정확 하 고 응답성이 뛰어난 이동 추적을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-118">Windows Mixed Reality motion controllers offer precise and responsive movement tracking in your field of view using the sensors in the immersive headset.</span></span> <span data-ttu-id="a8c47-119">공간의 벽에는 하드웨어를 설치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-119">There's no need to install hardware on the walls in your space.</span></span> <span data-ttu-id="a8c47-120">이러한 동작 컨트롤러는 Windows Mixed Reality 모던 헤드셋과 동일한 설정 및 이식성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-120">These motion controllers will offer the same ease of setup and portability as Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="a8c47-121">이 명절을 통해 이러한 컨트롤러를 출시 하 고 판매할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-121">Our device partners plan to market and sell these controllers on retail shelves this holiday.</span></span>

<span data-ttu-id="a8c47-122">![컨트롤러에 대 한 자세한 내용을 확인 하세요.](images/controllerimage-750px.png)</span><span class="sxs-lookup"><span data-stu-id="a8c47-122">![Get to know your controller](images/controllerimage-750px.png)</span></span><br>
<span data-ttu-id="a8c47-123">*컨트롤러에 대 한 자세한 내용을 확인 하세요.*</span><span class="sxs-lookup"><span data-stu-id="a8c47-123">*Get to know your controller*</span></span>

<span data-ttu-id="a8c47-124">**요소**</span><span class="sxs-lookup"><span data-stu-id="a8c47-124">**Features:**</span></span>
* <span data-ttu-id="a8c47-125">광학 추적</span><span class="sxs-lookup"><span data-stu-id="a8c47-125">Optical tracking</span></span>
* <span data-ttu-id="a8c47-126">트리거</span><span class="sxs-lookup"><span data-stu-id="a8c47-126">Trigger</span></span>
* <span data-ttu-id="a8c47-127">잡기 단추</span><span class="sxs-lookup"><span data-stu-id="a8c47-127">Grab button</span></span>
* <span data-ttu-id="a8c47-128">사용해</span><span class="sxs-lookup"><span data-stu-id="a8c47-128">Thumbstick</span></span>
* <span data-ttu-id="a8c47-129">터치 패드</span><span class="sxs-lookup"><span data-stu-id="a8c47-129">Touchpad</span></span>

## <a name="setup"></a><span data-ttu-id="a8c47-130">설치 프로그램</span><span class="sxs-lookup"><span data-stu-id="a8c47-130">Setup</span></span>

### <a name="before-you-begin"></a><span data-ttu-id="a8c47-131">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a8c47-131">Before you begin</span></span>

<span data-ttu-id="a8c47-132">**다음이 필요합니다:**</span><span class="sxs-lookup"><span data-stu-id="a8c47-132">**You'll need:**</span></span>
* <span data-ttu-id="a8c47-133">두 개의 동작 컨트롤러 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-133">A set of two motion controllers.</span></span>
* <span data-ttu-id="a8c47-134">AA 배터리가 4 개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-134">Four AA batteries.</span></span>
* <span data-ttu-id="a8c47-135">Bluetooth 4.0을 지 원하는 PC입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-135">A PC with Bluetooth 4.0 support.</span></span>

<span data-ttu-id="a8c47-136">**Windows, Unity 및 드라이버 업데이트 확인**</span><span class="sxs-lookup"><span data-stu-id="a8c47-136">**Check for Windows, Unity, and driver updates**</span></span>
* <span data-ttu-id="a8c47-137">혼합 현실 개발을 위해 기본 버전의 Windows, Unity 등의 [도구를 설치](../develop/install-the-tools.md) 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c47-137">Visit [Install the tools](../develop/install-the-tools.md) for the preferred versions of Windows, Unity, and so on, for mixed reality development.</span></span>
* <span data-ttu-id="a8c47-138">최신 [헤드셋 및 동작 컨트롤러 드라이버가](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-138">Make sure you have the most up-to-date [headset and motion controller drivers](/windows/mixed-reality/enthusiast-guide/mixed-reality-software).</span></span>

### <a name="pairing-controllers"></a><span data-ttu-id="a8c47-139">페어링 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="a8c47-139">Pairing controllers</span></span>

<span data-ttu-id="a8c47-140">다른 Bluetooth 장치와 마찬가지로 Windows 설정을 사용 하 여 호스트 PC와 동작 컨트롤러를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-140">Motion controllers can be bonded with host PC using Windows settings like any other Bluetooth device.</span></span>

1. <span data-ttu-id="a8c47-141">두 개의 AA 배터리를 컨트롤러 후면에 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-141">Insert two AA batteries into the back of the controller.</span></span> <span data-ttu-id="a8c47-142">지금은 배터리 덮개를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-142">Leave the battery cover off for now.</span></span>
2. <span data-ttu-id="a8c47-143">기본 제공 Bluetooth 라디오 대신 외부 USB Bluetooth 어댑터를 사용 하는 경우 계속 하기 전에 [bluetooth 모범 사례](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) 를 검토 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c47-143">If you're using an external USB Bluetooth Adapter instead of a built-in Bluetooth radio, review the [Bluetooth best practices](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) before proceeding.</span></span> <span data-ttu-id="a8c47-144">기본 제공 라디오를 사용 하는 데스크톱 구성의 경우 안테나가 연결 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-144">For desktop configuration with built-in radio, ensure antenna is connected.</span></span>
3. <span data-ttu-id="a8c47-145">**Windows 설정**  ->  **장치** 열기  ->  **bluetooth 또는 기타 장치**  ->  **bluetooth** 를 추가 하 고 "동작 컨트롤러 – 오른쪽" 및 "동작 컨트롤러-왼쪽"의 이전 인스턴스를 모두 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-145">Open **Windows Settings** -> **Devices** -> **Add Bluetooth or other device** -> **Bluetooth** and remove any earlier instances of “Motion controller – Right” and “Motion controller – Left”.</span></span> <span data-ttu-id="a8c47-146">목록의 맨 아래에 있는 기타 장치 범주도 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-146">Check also Other devices category at the bottom of the list.</span></span>
4. <span data-ttu-id="a8c47-147">**Bluetooth 또는 다른 장치 추가** 를 선택 하 고 bluetooth 장치 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-147">Select **Add Bluetooth or other device** and see it starting to discover Bluetooth devices.</span></span>
5. <span data-ttu-id="a8c47-148">컨트롤러의 Windows 단추를 길게 눌러 컨트롤러를 켜고 buzzes 면 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-148">Press and hold the controller's Windows button to turn on the controller, release once it buzzes.</span></span>
6. <span data-ttu-id="a8c47-149">Led가 펄스를 시작할 때까지 페어링 단추 (배터리 구획의 탭)를 길게 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-149">Press and hold the pairing button (tab in the battery compartment) until the LEDs begin pulsing.</span></span>

:::row:::
    :::column:::
7. <span data-ttu-id="a8c47-150">목록의 맨 아래에 "동작 컨트롤러-왼쪽" 또는 "동작 컨트롤러 오른쪽"이 표시 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-150">Wait "Motion controller - Left" or "Motion controller - Right" to appear to the bottom of the list.</span></span> <span data-ttu-id="a8c47-151">페어링 하려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-151">Select to pair.</span></span> <span data-ttu-id="a8c47-152">컨트롤러는 연결 될 때 한 번 진동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-152">Controller will vibrate once when connected.</span></span><br>
        <br>
        <span data-ttu-id="a8c47-153">*이미지: 페어링 하려면 "동작 컨트롤러"를 선택 합니다. 인스턴스가 여러 개 있는 경우 목록의 맨 아래에서 하나를 선택 합니다.*</span><span class="sxs-lookup"><span data-stu-id="a8c47-153">*Image: Select "Motion controller" to pair; if there are multiple instances, select one from the bottom of the list*</span></span>
    :::column-end:::
        :::column:::
       ![여러 인스턴스가 목록의 아래쪽에 표시 되는 항목을 선택 하는 경우 연결할 동작 컨트롤러를 선택 합니다.](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. <span data-ttu-id="a8c47-155">컨트롤러가 Bluetooth 설정의 **"마우스, 키보드, & 펜" 범주** 아래에 **연결** 됨으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-155">You'll see the controller appear in the Bluetooth settings under **“Mouse, keyboard, & pen” category** as **Connected**.</span></span> <span data-ttu-id="a8c47-156">이 시점에서 펌웨어 업데이트를 가져올 수 있습니다. [다음 섹션](motion-controllers.md#updating-controller-firmware)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c47-156">At this point, you may get a firmware update – see [next section](motion-controllers.md#updating-controller-firmware).</span></span>
9. <span data-ttu-id="a8c47-157">배터리 덮개를 다시 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-157">Reattach battery cover.</span></span>
10. <span data-ttu-id="a8c47-158">두 번째 컨트롤러에 대해 1-9 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-158">Repeat steps 1-9 for the second controller.</span></span>

<br>

:::row:::
    :::column:::
        <span data-ttu-id="a8c47-159">두 컨트롤러를 성공적으로 연결한 후 설정은 **"마우스, 키보드, & 펜" 범주** 에서 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-159">After successfully pairing both controllers, your settings should look like the following, under **“Mouse, keyboard, & pen” category**</span></span> <br>
        <br>
        <span data-ttu-id="a8c47-160">*이미지: 연결 된 동작 컨트롤러*</span><span class="sxs-lookup"><span data-stu-id="a8c47-160">*Image: Motion controllers connected*</span></span>
    :::column-end:::
        :::column:::
       ![연결 된 동작 컨트롤러](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

<span data-ttu-id="a8c47-162">페어링 후 컨트롤러가 꺼져 있으면 해당 상태는 페어링된 것으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-162">If the controllers are turned off after pairing, their status will show up as Paired.</span></span> <span data-ttu-id="a8c47-163">컨트롤러가 "기타 장치" 범주에서 영구적으로 연결 된 경우에는 페어링이 부분적 으로만 완료 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-163">For controllers permanently under the “Other devices” category, pairing may have only partially completed.</span></span> <span data-ttu-id="a8c47-164">이 경우 페어링 단계를 다시 실행 하 여 컨트롤러 기능을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-164">In this case, run the pairing steps again to get controller functional.</span></span>

### <a name="updating-controller-firmware"></a><span data-ttu-id="a8c47-165">컨트롤러 펌웨어 업데이트</span><span class="sxs-lookup"><span data-stu-id="a8c47-165">Updating controller firmware</span></span>

* <span data-ttu-id="a8c47-166">새 컨트롤러 펌웨어를 사용할 수 있는 상태에서 모던 헤드셋을 PC에 연결 하는 경우 다음에 전원을 켤 때 해당 펌웨어가 자동으로 이동 컨트롤러로 푸시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-166">If an immersive headset is connected to your PC with new controller firmware is available, the firmware will be pushed to your motion controllers automatically the next time you turn them on.</span></span> <span data-ttu-id="a8c47-167">컨트롤러 펌웨어 업데이트는 원형 동작에서 비추는 LED 사분면 패턴으로 표시 되며 1-2 분이 소요 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-167">Controller firmware updates are indicated by a pattern of illuminating LED quadrants in a circular motion, and take 1-2 minutes.</span></span>


:::row:::
    :::column:::
* <span data-ttu-id="a8c47-168">펌웨어 업데이트가 완료 되 면 컨트롤러를 다시 부팅 하 고 다시 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-168">After the firmware update completes, the controllers will reboot and reconnect.</span></span> <span data-ttu-id="a8c47-169">이제 두 컨트롤러를 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-169">Both controllers should be connected now.</span></span> <br>
        <br>
        <span data-ttu-id="a8c47-170">*이미지: Bluetooth 설정에서 연결 된 컨트롤러*</span><span class="sxs-lookup"><span data-stu-id="a8c47-170">*Image: Controllers connected in Bluetooth settings*</span></span>
    :::column-end:::
        :::column:::
       ![연결 된 컨트롤러](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* <span data-ttu-id="a8c47-172">컨트롤러가 제대로 작동 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-172">Verify your controllers work properly:</span></span>
    1. <span data-ttu-id="a8c47-173">**혼합 현실 포털** 을 시작 하 고 혼합 현실 홈을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-173">Launch **Mixed Reality Portal** and enter your Mixed Reality Home.</span></span>
    2. <span data-ttu-id="a8c47-174">컨트롤러를 이동 하 고 추적, 테스트 단추를 확인 하 고 [teleportation](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 작동 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-174">Move your controllers and verify tracking, test buttons, and verify [teleportation](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) works.</span></span> <span data-ttu-id="a8c47-175">그렇지 않으면 [동작 컨트롤러 문제 해결](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c47-175">If they don't, then check out [motion controller troubleshooting](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers).</span></span>

## <a name="gazing-and-pointing"></a><span data-ttu-id="a8c47-176">Gazing 및 가리키기</span><span class="sxs-lookup"><span data-stu-id="a8c47-176">Gazing and pointing</span></span>

<span data-ttu-id="a8c47-177">Windows Mixed Reality는 상호 작용을 위한 두 가지 주요 모델을 지원 합니다. **응시 및 커밋** 및 **커밋**:</span><span class="sxs-lookup"><span data-stu-id="a8c47-177">Windows Mixed Reality supports two key models for interaction; **gaze and commit** and **point and commit**:</span></span>
* <span data-ttu-id="a8c47-178">사용자는 **응시 및 커밋을** 사용 하 여 사용자가 자신의 [응시](gaze-and-commit.md)를 사용 하 여 개체를 대상으로 지정한 다음 손으로 직접 탭, 게임 패드, clicker 또는 음성으로 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-178">With **gaze and commit**, users target an object with their [gaze](gaze-and-commit.md), and then select objects with hand air-taps, a gamepad, a clicker, or their voice.</span></span>
* <span data-ttu-id="a8c47-179">**지점 및 커밋을** 사용 하 여 사용자는 대상 개체에서 포인팅 가능 동작 컨트롤러를 목표로 한 다음 컨트롤러의 트리거를 사용 하 여 개체를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-179">With **point and commit**, a user can aim a pointing-capable motion controller at the target object and then select objects with the controller's trigger.</span></span>

<span data-ttu-id="a8c47-180">동작 컨트롤러를 가리키는 기능을 지 원하는 앱은 가능한 경우에도 사용자에 게 사용 하는 입력 장치에 대 한 선택 항목을 제공 하는 응시 기반 상호 작용을 가능 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-180">Apps that support pointing with motion controllers should also enable gaze-driven interactions where possible, to give users a choice in what input devices they use.</span></span>

### <a name="managing-recoil-when-pointing"></a><span data-ttu-id="a8c47-181">가리킬 때 recoil 관리</span><span class="sxs-lookup"><span data-stu-id="a8c47-181">Managing recoil when pointing</span></span>

<span data-ttu-id="a8c47-182">동작 컨트롤러를 사용 하 여 지점 및 커밋을 수행 하는 경우 사용자는 해당 트리거를 끌어와 컨트롤러를 사용 하 여 대상 지정 하 고 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-182">When using motion controllers to point and commit, your users will use the controller to target and interact by pulling its trigger.</span></span> <span data-ttu-id="a8c47-183">트리거 vigorously를 끌어오는 사용자는 의도 한 대로 트리거 끌어오기의 끝에서 컨트롤러의 상위 수준으로 끝날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-183">Users who pull the trigger vigorously may end up aiming the controller higher at the end of their trigger pull than they'd intended.</span></span>

<span data-ttu-id="a8c47-184">사용자가 트리거를 끌어올 때 발생할 수 있는 이러한 recoil를 관리 하기 위해 트리거의 아날로그 축 값이 0.0 이상으로 증가 하는 경우 앱에서 대상 광선을 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-184">To manage any such recoil that may occur when users pull the trigger, your app can snap its targeting ray when the trigger's analog axis value rises above 0.0.</span></span> <span data-ttu-id="a8c47-185">그런 다음 짧은 시간 내에 최종 키가 발생 하는 한, 나중에 트리거 값이 1.0에 도달 하면 몇 개 프레임을 대상으로 하는 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-185">You can then take action using that targeting ray a few frames later once the trigger value reaches 1.0, as long as the final press occurs within a short time window.</span></span> <span data-ttu-id="a8c47-186">상위 수준 [복합 탭 제스처](gaze-and-commit.md#composite-gestures)를 사용 하는 경우 Windows에서이 대상 지정 광선 캡처 및 시간 초과를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-186">When using the higher-level [composite Tap gesture](gaze-and-commit.md#composite-gestures), Windows will manage this targeting ray capture and timeout for you.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="a8c47-187">그립 포즈 및 포인팅 포즈</span><span class="sxs-lookup"><span data-stu-id="a8c47-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="a8c47-188">Windows Mixed Reality는 다양 한 폼 팩터에서 동작 컨트롤러를 지원 하며, 각 컨트롤러의 디자인이 사용자의 손 위치와 앱이 컨트롤러를 렌더링할 때 사용 해야 하는 자연 스러운 "전달" 방향 간의 관계에 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-188">Windows Mixed Reality supports motion controllers in different form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="a8c47-189">이러한 컨트롤러를 더 잘 나타내기 위해 각 상호 작용 소스에 대해 조사할 수 있는 두 가지 종류의 포즈가 있습니다. **그립** 및 **포인터는 포즈** 를 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-189">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source; the **grip pose** and the **pointer pose**.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="a8c47-190">그립 포즈</span><span class="sxs-lookup"><span data-stu-id="a8c47-190">Grip pose</span></span>

<span data-ttu-id="a8c47-191">**그립 포즈** 는 HoloLens에서 감지한 손바닥의 위치 또는 동작 컨트롤러를 보유 하는 야자나무를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-191">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="a8c47-192">몰입 형 헤드셋에서 그립 포즈는 사용자 **의 손을** 만들거나 **사용자의 손으로 보유 한 개체**(예: 소드 또는 포)를 렌더링 하는 데 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-192">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="a8c47-193">동작 컨트롤러에 대해 Windows에서 제공 하는 **렌더링할 모델** 은 동작 컨트롤러를 시각화할 때에도 그립 포즈를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-193">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="a8c47-194">그립 포즈는 구체적으로 다음과 같이 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-194">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="a8c47-195">**그립 위치**: 컨트롤러를 자연스럽 게 유지 하는 경우 왼쪽 또는 오른쪽으로 조정 하 여 그립 내 위치를 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-195">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="a8c47-196">Windows Mixed Reality 동작 컨트롤러에서이 위치는 일반적으로 보통 클릭 단추와 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-196">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="a8c47-197">**그립 방향 오른쪽 축**: 손 모양 5 손가락으로 구성 된 평면을 완전히 열 때 palm (왼쪽 palm, 오른쪽 팜)에 있는 광선</span><span class="sxs-lookup"><span data-stu-id="a8c47-197">The **grip orientation's Right axis**: When you completely open your hand to form a flat five-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="a8c47-198">**그립 방향 전방 축: 핸들** 을 부분적으로 (컨트롤러를 보유 하는 것 처럼) 닫는 경우 비 엄지 손가락으로 형성 된 튜브를 통해 "전달" 하는 광선이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-198">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="a8c47-199">**그립 방향 up 축**: 오른쪽 및 전방 정의에 의해 암시 된 위쪽 축입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-199">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="a8c47-200">포인터 포즈</span><span class="sxs-lookup"><span data-stu-id="a8c47-200">Pointer pose</span></span>

<span data-ttu-id="a8c47-201">**포인터 포즈** 는 컨트롤러의 팁을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-201">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="a8c47-202">시스템에서 제공 하는 포인터 포즈는 **컨트롤러 모델 자체를 렌더링** 하는 경우 raycast를 사용 하는 데 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-202">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="a8c47-203">컨트롤러 대신 다른 가상 개체 (예: 가상 사용자)를 렌더링 하는 경우 앱 정의 된 포 모델의 배럴을 따라 이동 하는 광선과 같이 해당 가상 개체에 가장 자연 스러운 광선을 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-203">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="a8c47-204">사용자는 가상 개체를 볼 수 있고 실제 컨트롤러는 볼 수 없으므로 가상 개체를 가리키면 앱을 사용 하는 것이 더 자연스럽 게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-204">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="a8c47-205">컨트롤러 추적 상태</span><span class="sxs-lookup"><span data-stu-id="a8c47-205">Controller tracking state</span></span>

<span data-ttu-id="a8c47-206">헤드셋 처럼 Windows Mixed Reality 동작 컨트롤러를 사용 하려면 외부 추적 센서를 설정 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-206">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="a8c47-207">대신, 컨트롤러는 헤드셋 자체의 센서에 의해 추적 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-207">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="a8c47-208">사용자가 컨트롤러를 헤드셋의 뷰 필드에서 밖으로 이동 하는 경우 대부분의 경우 Windows는 컨트롤러 위치를 계속 유추 하 고 앱에 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-208">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="a8c47-209">컨트롤러에서 충분히 긴 시각적 추적을 분실 한 경우 컨트롤러의 위치는 대략적인 정확도 위치로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-209">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="a8c47-210">이 시점에서 시스템은 컨트롤러를 사용자에 게 본문 잠금을 설정 하 고, 이동 하는 동안 사용자의 위치를 추적 하 고, 내부 방향 센서를 사용 하 여 컨트롤러의 실제 방향을 계속 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-210">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="a8c47-211">컨트롤러를 사용 하 여 UI 요소를 가리키고 활성화 하는 많은 앱이 정상적으로 작동 하 고, 사용자가 모르게 정확한 정확도를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-211">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="a8c47-212">명시적 추적 상태에 대 한 추론</span><span class="sxs-lookup"><span data-stu-id="a8c47-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="a8c47-213">추적 상태에 따라 위치를 다르게 처리 하려는 앱은 더 나아가 컨트롤러의 상태에 대 한 속성 (예: SourceLossRisk 및 PositionAccuracy)을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as SourceLossRisk and PositionAccuracy:</span></span>

<table>
<tr>
<th> <span data-ttu-id="a8c47-214">상태 추적</span><span class="sxs-lookup"><span data-stu-id="a8c47-214">Tracking state</span></span> </th><th> <span data-ttu-id="a8c47-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="a8c47-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="a8c47-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="a8c47-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="a8c47-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="a8c47-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="a8c47-218"><b>높은 정확도</b> </span><span class="sxs-lookup"><span data-stu-id="a8c47-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="a8c47-219">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="a8c47-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a8c47-220">높은</span><span class="sxs-lookup"><span data-stu-id="a8c47-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a8c47-221">true</span><span class="sxs-lookup"><span data-stu-id="a8c47-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a8c47-222"><b>높은 정확도 (손실 위험)</b> </span><span class="sxs-lookup"><span data-stu-id="a8c47-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a8c47-223">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="a8c47-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a8c47-224">높은</span><span class="sxs-lookup"><span data-stu-id="a8c47-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a8c47-225">true</span><span class="sxs-lookup"><span data-stu-id="a8c47-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a8c47-226"><b>대략적인 정확도</b> </span><span class="sxs-lookup"><span data-stu-id="a8c47-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a8c47-227">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="a8c47-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a8c47-228">근사치</span><span class="sxs-lookup"><span data-stu-id="a8c47-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a8c47-229">true</span><span class="sxs-lookup"><span data-stu-id="a8c47-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a8c47-230"><b>위치 없음</b> </span><span class="sxs-lookup"><span data-stu-id="a8c47-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a8c47-231">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="a8c47-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a8c47-232">근사치</span><span class="sxs-lookup"><span data-stu-id="a8c47-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a8c47-233">false</span><span class="sxs-lookup"><span data-stu-id="a8c47-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="a8c47-234">이러한 동작 컨트롤러 추적 상태는 다음과 같이 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="a8c47-235">**높은 정확도:** 동작 컨트롤러는 헤드셋의 보기 필드 내에 있지만 일반적으로 시각적 추적에 따라 정확도가 높은 위치를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="a8c47-236">일시적으로 보기의 필드를 벗어나거나 헤드셋 센서에서 일시적으로 가려진 이동 컨트롤러 (예: 사용자의 경우)는 컨트롤러 자체의 관성 추적에 따라 짧은 시간 동안 계속 해 서 정확도가 높은 포즈를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-236">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (for example, by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="a8c47-237">**높은 정확도 (손실 위험):** 사용자가 이동 컨트롤러를 헤드셋의 보기 필드 가장자리를 지나서 이동할 때 헤드셋은 곧 컨트롤러의 위치를 시각적으로 추적할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="a8c47-238">앱은 **SourceLossRisk** reach 1.0을 확인 하 여 컨트롤러가이 FOV 경계에 도달한 경우를 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="a8c47-239">이 시점에서 앱은 고품질 포즈의 안정적인 스트림을 필요로 하는 컨트롤러 제스처를 일시 중지 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-239">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="a8c47-240">**대략적인 정확도:** 컨트롤러에서 충분히 긴 시각적 추적을 분실 한 경우 컨트롤러의 위치는 대략적인 정확도 위치로 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="a8c47-241">이 시점에서 시스템은 컨트롤러를 사용자에 게 본문 잠금을 설정 하 고, 이동 하는 동안 사용자의 위치를 추적 하 고, 내부 방향 센서를 사용 하 여 컨트롤러의 실제 방향을 계속 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="a8c47-242">컨트롤러를 사용 하 여 UI 요소를 가리키고 활성화 하는 많은 앱이 정상적으로 작동 하 고, 사용자가 모르게 정확한 정확도를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="a8c47-243">입력 요구 사항이 많은 앱은 사용자에 게이 시간 동안 오프 화면 대상에 대 한 hitbox을 제공 하는 등의 방법으로 **positionaccuracy** 속성을 검사 하 여 정확도가 **높은** **정확도부터 정확도까지** 이러한 삭제를 합리적으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="a8c47-244">**위치 없음:** 컨트롤러는 오랜 시간 동안 정확한 정확도로 작동할 수 있지만, 경우에 따라 본문 잠금 위치가 중요 하지 않은 경우에도 시스템에서 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="a8c47-245">예를 들어 설정 된 컨트롤러가 시각적으로 관찰 되지 않았거나 사용자가 다른 사용자가 선택 하는 컨트롤러를 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-245">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="a8c47-246">이러한 시간에 시스템은 앱에 어떤 위치도 제공 하지 않으며 **TryGetPosition** 는 false를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-246">At those times, the system won't provide any position to the app, and **TryGetPosition** will return false.</span></span>

## <a name="interactions-low-level-spatial-input"></a><span data-ttu-id="a8c47-247">상호 작용: 하위 수준 공간 입력</span><span class="sxs-lookup"><span data-stu-id="a8c47-247">Interactions: Low-level spatial input</span></span>

<span data-ttu-id="a8c47-248">손으로 이동 하 고 **이동 하는** 컨트롤러의 핵심 상호 작용은 **선택**, **메뉴**, 방법, **터치 패드**, **엄지 스틱** 및 **홈** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-248">The core interactions across hands and motion controllers are **Select**, **Menu**, **Grasp**, **Touchpad**, **Thumbstick**, and **Home**.</span></span>
* <span data-ttu-id="a8c47-249">Press를 선택 하 고 릴리스를 차례로 선택 하 여 홀로그램을 활성화 하는 기본 상호 작용을 **선택** 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-249">**Select** is the primary interaction to activate a hologram, consisting of a press followed by a release.</span></span> <span data-ttu-id="a8c47-250">동작 컨트롤러의 경우 컨트롤러의 트리거를 사용 하 여 Select 누르기를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-250">For motion controllers, you perform a Select press using the controller's trigger.</span></span> <span data-ttu-id="a8c47-251">Select를 수행 하는 다른 방법은 [음성 명령](voice-input.md) "Select"를 말하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-251">Other ways to perform a Select are by speaking the [voice command](voice-input.md) "Select".</span></span> <span data-ttu-id="a8c47-252">모든 앱 내에서 동일한 select 상호 작용을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-252">The same select interaction can be used within any app.</span></span> <span data-ttu-id="a8c47-253">Select를 마우스 클릭에 해당 하는 것으로 간주 합니다. 한 번 알아보고 모든 앱에 적용 되는 범용 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-253">Think of Select as the equivalent of a mouse click; a universal action that you learn once and then apply across all your apps.</span></span>
* <span data-ttu-id="a8c47-254">**메뉴** 는 상황에 맞는 메뉴를 끌어오거나 다른 보조 작업을 수행 하는 데 사용 되는 개체의 동작에 대 한 보조 상호 작용입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-254">**Menu** is the secondary interaction for acting on an object, used to pull up a context menu or take some other secondary action.</span></span> <span data-ttu-id="a8c47-255">동작 컨트롤러를 사용 하면 컨트롤러의 *메뉴* 단추를 사용 하 여 메뉴 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-255">With motion controllers, you can take a menu action using the controller's *menu* button.</span></span> <span data-ttu-id="a8c47-256">(즉, 햄버거 "메뉴" 아이콘이 있는 단추)</span><span class="sxs-lookup"><span data-stu-id="a8c47-256">(that is, the button with the hamburger "menu" icon on it)</span></span>
* <span data-ttu-id="a8c47-257">사용자가 직접 개체에 대 한 작업을 수행 하 여 조작 하는 방법을 **이해** 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-257">**Grasp** is how users can directly take action on objects at their hand to manipulate them.</span></span> <span data-ttu-id="a8c47-258">동작 컨트롤러를 사용 하 여 펀치를 긴밀 하 게 배치 하 여 동작을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-258">With motion controllers, you can do a grasp action by squeezing your fist tightly.</span></span> <span data-ttu-id="a8c47-259">동작 컨트롤러는 잡기 단추, 팜 트리거 또는 기타 센서를 사용 하 여 감지기를 감지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-259">A motion controller may detect a Grasp with a grab button, palm trigger, or other sensor.</span></span>
* <span data-ttu-id="a8c47-260">**터치 패드** 를 통해 사용자는 동작 컨트롤러의 터치 패드 화면에 있는 두 차원의 작업을 조정 하 여 터치 패드에서 다운을 클릭 하 여 작업을 커밋할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-260">**Touchpad** allows the user to adjust an action in two dimensions along the surface of a motion controller's touchpad, committing the action by clicking down on the touchpad.</span></span> <span data-ttu-id="a8c47-261">터치 패드는 누름 상태, 작업 상태 및 정규화 된 XY 좌표를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-261">Touchpads provide a pressed state, touched state, and normalized XY coordinates.</span></span> <span data-ttu-id="a8c47-262">원형 터치 패드 범위에서 X 및 Y의 범위는-1에서 1 사이 이며 중심은 (0, 0)입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-262">X and Y range from -1 to 1 across the range of the circular touchpad, with a center at (0, 0).</span></span> <span data-ttu-id="a8c47-263">X의 경우-1은 왼쪽에 있고 1은 오른쪽에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-263">For X, -1 is on the left and 1 is on the right.</span></span> <span data-ttu-id="a8c47-264">Y의 경우-1은 아래쪽에 있고 1은 맨 위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-264">For Y, -1 is on the bottom and 1 is on the top.</span></span>
* <span data-ttu-id="a8c47-265">**엄지 스틱** 을 사용 하면 동작 컨트롤러의 엄지 스틱을 원형 범위 내에서 이동 하 고 엄지 스틱에서 아래로 클릭 하 여 작업을 커밋하는 방식으로 두 차원의 작업을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-265">**Thumbstick** allows the user to adjust an action in two dimensions by moving a motion controller's thumbstick within its circular range, committing the action by clicking down on the thumbstick.</span></span> <span data-ttu-id="a8c47-266">또한 Thumbsticks는 눌러진 상태와 정규화 된 XY 좌표를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-266">Thumbsticks also provide a pressed state and normalized XY coordinates.</span></span> <span data-ttu-id="a8c47-267">원형 터치 패드 범위에서 X 및 Y의 범위는-1에서 1 사이 이며 중심은 (0, 0)입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-267">X and Y range from -1 to 1 across the range of the circular touchpad, with a center at (0, 0).</span></span> <span data-ttu-id="a8c47-268">X의 경우-1은 왼쪽에 있고 1은 오른쪽에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-268">For X, -1 is on the left and 1 is on the right.</span></span> <span data-ttu-id="a8c47-269">Y의 경우-1은 아래쪽에 있고 1은 맨 위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-269">For Y, -1 is on the bottom and 1 is on the top.</span></span>
* <span data-ttu-id="a8c47-270">**Home** 은 시작 메뉴로 다시 이동 하는 데 사용 되는 특수 시스템 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-270">**Home** is a special system action that is used to go back to the Start Menu.</span></span> <span data-ttu-id="a8c47-271">키보드에서 Windows 키를 누르거나 Xbox 컨트롤러의 Xbox 단추를 누르는 것과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-271">It's similar to pressing the Windows key on a keyboard or the Xbox button on an Xbox controller.</span></span> <span data-ttu-id="a8c47-272">동작 컨트롤러에서 Windows 단추를 눌러 홈으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-272">You can go Home by pressing the Windows button on a motion controller.</span></span> <span data-ttu-id="a8c47-273">언제 든 지 "안녕 코타 나 이동 홈"을 안내 하는 것으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-273">Note, you can always return to Start by saying "Hey Cortana, Go Home".</span></span> <span data-ttu-id="a8c47-274">앱은 시스템에 의해 처리 되기 때문에 특별 한 방식으로 홈 작업에 대응할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-274">Apps can't react specifically to Home actions, as these are handled by the system.</span></span>

## <a name="composite-gestures-high-level-spatial-input"></a><span data-ttu-id="a8c47-275">복합 제스처: 상위 수준 공간 입력</span><span class="sxs-lookup"><span data-stu-id="a8c47-275">Composite gestures: High-level spatial input</span></span>

<span data-ttu-id="a8c47-276">[핸드 제스처](gaze-and-commit.md#composite-gestures) 와 동작 컨트롤러를 시간에 따라 추적 하 여 상위 수준 **[복합 제스처](gaze-and-commit.md#composite-gestures)** 의 공통 집합을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-276">Both [hand gestures](gaze-and-commit.md#composite-gestures) and motion controllers can be tracked over time to detect a common set of high-level **[composite gestures](gaze-and-commit.md#composite-gestures)**.</span></span> <span data-ttu-id="a8c47-277">이를 통해 앱은 사용자가 직접 또는 컨트롤러를 사용 하 든 관계 없이 상위 수준 **탭**, **보유**, **조작** 및 **탐색** 제스처를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-277">This enables your app to detect high-level **tap**, **hold**, **manipulation** and **navigation** gestures, whether users end up using hands or controllers.</span></span>

## <a name="rendering-the-motion-controller-model"></a><span data-ttu-id="a8c47-278">동작 컨트롤러 모델 렌더링</span><span class="sxs-lookup"><span data-stu-id="a8c47-278">Rendering the motion controller model</span></span>

<span data-ttu-id="a8c47-279">**3d 컨트롤러 모델** Windows에서는 현재 시스템에서 활성 상태인 각 동작 컨트롤러의 렌더링할 모델을 앱에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-279">**3D controller models** Windows makes available to apps a renderable model of each motion controller currently active in the system.</span></span> <span data-ttu-id="a8c47-280">앱이 시스템 제공 컨트롤러 모델을 런타임에 동적으로 로드 하 고이를 표시 하는 방식으로 앱이 이후 컨트롤러 디자인과 호환 되는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-280">By having your app dynamically load and articulate these system-provided controller models at runtime, you can ensure your app is forward-compatible to any future controller designs.</span></span>

<span data-ttu-id="a8c47-281">모델의 원점은 실제 세계의이 지점에 맞춰 정렬 되므로 컨트롤러의 **그립 포즈** 에서 모든 렌더링할 모델을 렌더링 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-281">We recommend rendering all renderable models at the **grip pose** of the controller, as the origin of the model is aligned with this point in the physical world.</span></span> <span data-ttu-id="a8c47-282">컨트롤러 모델을 렌더링 하는 경우에는 해당 컨트롤러의 물리적 디자인을 고려 하 여 사용자가 의도적으로 가리키는 광선을 나타내는 **포인터 포즈** 에서 장면으로의 장면을 raycast 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-282">If you're rendering controller models, you may then wish to raycast into your scene from the **pointer pose**, which represents the ray along which users will naturally expect to point, given that controller's physical design.</span></span>

<span data-ttu-id="a8c47-283">Unity에서 동적으로 컨트롤러 모델을 로드 하는 방법에 대 한 자세한 내용은 [unity에서 동작 컨트롤러 모델 렌더링](../develop/unity/gestures-in-unity.md#rendering-the-motion-controller-model-in-unity) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c47-283">For more information about how to load controller models dynamically in Unity, see the [Rendering the motion controller model in Unity](../develop/unity/gestures-in-unity.md#rendering-the-motion-controller-model-in-unity) section.</span></span>

<span data-ttu-id="a8c47-284">**2d 컨트롤러 선 아트** 앱 내 컨트롤러 모델 자체에 앱 컨트롤러의 팁과 명령을 연결 하는 것이 좋지만 일부 개발자는 플랫 "자습서" 또는 "방법" UI에서 동작 컨트롤러의 2D 선 아트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-284">**2D controller line art** While we recommend attaching in-app controller tips and commands to the in-app controller models themselves, some developers may want to use 2D line art representations of the motion controllers in flat "tutorial" or "how-to" UI.</span></span> <span data-ttu-id="a8c47-285">이러한 개발자에 게는 다음의 검은색과 흰색 모두에서 .png 동작 컨트롤러 라인 아트 파일을 사용할 수 있습니다 (저장 하려면 마우스 오른쪽 단추 클릭).</span><span class="sxs-lookup"><span data-stu-id="a8c47-285">For those developers, we've made .png motion controller line art files available in both black and white below (right-click to save).</span></span>

![동작 컨트롤러의 미리 보기 라인 아트](images/motioncontrollers-black-preview-300px.png)

[<span data-ttu-id="a8c47-287">' ' ' 흰색 ' ' '의 전체 해상도 동작 컨트롤러 라인 아트</span><span class="sxs-lookup"><span data-stu-id="a8c47-287">Full-resolution motion controllers line art in '''white'''</span></span>](images/motioncontrollers-white.png)
 
[<span data-ttu-id="a8c47-288">' ' ' Black ' ' '의 전체 해상도 동작 컨트롤러 라인 아트</span><span class="sxs-lookup"><span data-stu-id="a8c47-288">Full-resolution motion controllers line art in '''black'''</span></span>](images/motioncontrollers-black.png)

## <a name="faq"></a><span data-ttu-id="a8c47-289">FAQ</span><span class="sxs-lookup"><span data-stu-id="a8c47-289">FAQ</span></span>

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a><span data-ttu-id="a8c47-290">여러 Pc에 동작 컨트롤러를 페어링 할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="a8c47-290">Can I pair motion controllers to multiple PCs?</span></span>

<span data-ttu-id="a8c47-291">동작 컨트롤러는 단일 PC와의 페어링을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-291">Motion controllers support pairing with a single PC.</span></span> <span data-ttu-id="a8c47-292">컨트롤러를 페어링 하려면 [동작 컨트롤러 설정](motion-controllers.md#setup) 에 대 한 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="a8c47-292">Follow instructions on [motion controller setup](motion-controllers.md#setup) to pair your controllers.</span></span>

### <a name="how-do-i-update-motion-controller-firmware"></a><span data-ttu-id="a8c47-293">동작 컨트롤러 펌웨어를 업데이트 어떻게 할까요??</span><span class="sxs-lookup"><span data-stu-id="a8c47-293">How do I update motion controller firmware?</span></span>

<span data-ttu-id="a8c47-294">동작 컨트롤러 펌웨어는 헤드셋 드라이버의 일부 이며 필요한 경우 연결 시 자동으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-294">Motion controller firmware is part of the headset driver and will be updated automatically on connection, if necessary.</span></span> <span data-ttu-id="a8c47-295">펌웨어 업데이트는 일반적으로 Bluetooth 송수신 장치 및 링크 품질에 따라 1-2 분이 소요 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-295">Firmware updates typically take 1-2 minutes depending on Bluetooth radio and link quality.</span></span> <span data-ttu-id="a8c47-296">드문 경우 지만 컨트롤러 펌웨어 업데이트에는 최대 10 분이 걸릴 수 있으며,이로 인해 Bluetooth 연결 또는 라디오 간섭을 일으킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-296">In rare cases, controller firmware updates may take up to 10 minutes, which can indicate poor Bluetooth connectivity or radio interference.</span></span> <span data-ttu-id="a8c47-297">연결 문제를 해결 하려면 [열성적인 가이드의 Bluetooth 모범 사례](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c47-297">See [Bluetooth best practices in the Enthusiast Guide](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) to troubleshoot connectivity issues.</span></span> <span data-ttu-id="a8c47-298">펌웨어 업데이트 후 컨트롤러는 다시 부팅 되 고 호스트 PC에 다시 연결 됩니다. (Led가 추적을 위해 밝게 표시 될 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="a8c47-298">After a firmware update, controllers will reboot and reconnect to the host PC (you may notice the LEDs go bright for tracking).</span></span> <span data-ttu-id="a8c47-299">펌웨어 업데이트가 중단 된 경우 (예: 컨트롤러에 전원이 들어오지 않음) 다음에 컨트롤러 전원을 켤 때 다시 시도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-299">If a firmware update is interrupted (for example, the controllers lose power), it will be attempted again the next time the controllers are powered on.</span></span>

### <a name="how-i-can-check-battery-level"></a><span data-ttu-id="a8c47-300">배터리 수준을 확인할 수 있는 방법은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="a8c47-300">How I can check battery level?</span></span>

<span data-ttu-id="a8c47-301">[Windows Mixed Reality 홈](../discover/navigating-the-windows-mixed-reality-home.md)에서 컨트롤러를 사용 하 여 가상 모델의 뒷면에 있는 배터리 수준을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-301">In the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md), you can turn your controller over to see its battery level on the reverse side of the virtual model.</span></span> <span data-ttu-id="a8c47-302">물리적 배터리 수준 표시기는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-302">There's no physical battery level indicator.</span></span>

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a><span data-ttu-id="a8c47-303">헤드셋 없이 이러한 컨트롤러를 사용할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="a8c47-303">Can you use these controllers without a headset?</span></span> <span data-ttu-id="a8c47-304">조이스틱/트리거/등의 입력만 있으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-304">Just for the joystick/trigger/etc input?</span></span>

<span data-ttu-id="a8c47-305">유니버설 Windows 응용 프로그램에는 적합 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-305">Not for Universal Windows Applications.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="a8c47-306">문제 해결</span><span class="sxs-lookup"><span data-stu-id="a8c47-306">Troubleshooting</span></span>

<span data-ttu-id="a8c47-307">열성적인 가이드의 [동작 컨트롤러 문제 해결](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c47-307">See [motion controller troubleshooting](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) in the Enthusiast Guide.</span></span>

## <a name="filing-motion-controller-feedbackbugs"></a><span data-ttu-id="a8c47-308">동작 컨트롤러 피드백/버그 파일링</span><span class="sxs-lookup"><span data-stu-id="a8c47-308">Filing motion controller feedback/bugs</span></span>

<span data-ttu-id="a8c47-309">"혼합 현실-> 입력" 범주를 사용 하 여 피드백 허브에 [피드백을 제공](/hololens/hololens-feedback) 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c47-309">[Give us feedback](/hololens/hololens-feedback) in Feedback Hub, using the "Mixed Reality -> Input" category.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8c47-310">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8c47-310">See also</span></span>

* [<span data-ttu-id="a8c47-311">Unity의 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="a8c47-311">Motion controllers in Unity</span></span>](../develop/unity/motion-controllers-in-unity.md)
* [<span data-ttu-id="a8c47-312">DirectX의 헤드 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="a8c47-312">Hands and motion controllers in DirectX</span></span>](../develop/native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="a8c47-313">제스처</span><span class="sxs-lookup"><span data-stu-id="a8c47-313">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="a8c47-314">열성적인 's Guide: Windows Mixed Reality 홈</span><span class="sxs-lookup"><span data-stu-id="a8c47-314">Enthusiast's Guide: Your Windows Mixed Reality home</span></span>](/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [<span data-ttu-id="a8c47-315">열성적인 's Guide: Windows Mixed Reality에서 게임 & 앱 사용</span><span class="sxs-lookup"><span data-stu-id="a8c47-315">Enthusiast's Guide: Using games & apps in Windows Mixed Reality</span></span>](/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [<span data-ttu-id="a8c47-316">내부에서 외부로 추적의 작동 방식</span><span class="sxs-lookup"><span data-stu-id="a8c47-316">How inside-out tracking works</span></span>](/windows/mixed-reality/enthusiast-guide/tracking-system)