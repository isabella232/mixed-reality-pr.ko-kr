---
title: Unreal의 QR 코드
description: Unreal에서 QR 코드 사용 가이드
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 기능, 설명서, 가이드, 홀로그램, qr 코드, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 7e39e1d822f0aa623a83678beef24f2c98a18944
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609644"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="0fdb0-104">Unreal의 QR 코드</span><span class="sxs-lookup"><span data-stu-id="0fdb0-104">QR codes in Unreal</span></span>

<span data-ttu-id="0fdb0-105">HoloLens 2는 웹캠을 사용하여 세계 공간에서 QR 코드를 볼 수 있습니다. 즉, 각 코드의 실제 세계 위치에서 홀로그램으로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-105">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms at each code's real-world position.</span></span> <span data-ttu-id="0fdb0-106">HoloLens 2는 또한 공유 경험을 만들기 위해 여러 디바이스에서 동일한 위치에 홀로그램을 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-106">HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="0fdb0-107">애플리케이션에 QR 코드를 추가하기 위한 모범 사례를 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-107">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="0fdb0-108">자동 영역</span><span class="sxs-lookup"><span data-stu-id="0fdb0-108">Quiet zones</span></span>
- <span data-ttu-id="0fdb0-109">조명 및 배경</span><span class="sxs-lookup"><span data-stu-id="0fdb0-109">Lighting and backdrop</span></span>
- <span data-ttu-id="0fdb0-110">크기, 거리 및 각도 위치</span><span class="sxs-lookup"><span data-stu-id="0fdb0-110">Size, distance, and angular position</span></span>

<span data-ttu-id="0fdb0-111">QR 코드가 앱에 배치될 때 [환경 고려 사항](../../environment-considerations-for-hololens.md)에 특히 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-111">Pay special attention to the [environment considerations](../../environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="0fdb0-112">이러한 각각의 토픽에 대한 자세한 정보와 필요한 NuGet 패키지를 다운로드하는 방법에 대한 지침은 주 [QR 코드 추적](../platform-capabilities-and-apis/qr-code-tracking.md) 설명서에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-112">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

> [!CAUTION]
> <span data-ttu-id="0fdb0-113">QR 코드는 HoloLens에서 기본적으로 추적할 수 있는 유일한 이미지 유형입니다. Unreal의 **UARTrackedImage** 모듈은 HoloLens에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-113">QR codes are the only type of images that can be tracked by HoloLens out of the box - Unreal's **UARTrackedImage** module isn't supported on HoloLens.</span></span> <span data-ttu-id="0fdb0-114">사용자 지정 이미지를 추적해야 하는 경우에는 타사 이미지 인식 라이브러리를 사용하여 디바이스의 [웹캠](unreal-hololens-camera.md)에 액세스한 후 이미지를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-114">If you need to track custom images, you can access the device's [webcam](unreal-hololens-camera.md) and process images using a third party image recognition library.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="0fdb0-115">QR 검색 사용</span><span class="sxs-lookup"><span data-stu-id="0fdb0-115">Enabling QR detection</span></span>
<span data-ttu-id="0fdb0-116">HoloLens 2는 웹캠을 사용하여 QR 코드를 확인해야 하므로 프로젝트 설정에서 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-116">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="0fdb0-117">**편집 > 프로젝트 설정** 을 열고 **플랫폼** 섹션까지 아래로 스크롤한 다음, **HoloLens** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-117">Open **Edit > Project Settings**, scroll to the **Platforms** section, and select **HoloLens**.</span></span>
    + <span data-ttu-id="0fdb0-118">**기능** 섹션을 확장하고 **웹캠** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-118">Expand the **Capabilities** section and check **Webcam**.</span></span>  
- <span data-ttu-id="0fdb0-119">또한 [ARSessionConfig 자산](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)을 추가하여 QR 코드 추적을 옵트인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-119">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a><span data-ttu-id="0fdb0-120">추적된 QR 코드 설정</span><span class="sxs-lookup"><span data-stu-id="0fdb0-120">Setting up a tracked QR code</span></span>

<span data-ttu-id="0fdb0-121">QR 코드는 Unreal의 AR 추적 기하 도형 시스템을 통해 추적 이미지로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-121">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="0fdb0-122">이 작업을 수행하려면 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-122">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="0fdb0-123">행위자 청사진을 만들고 **ARTrackableNotify** 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-123">Create an Actor Blueprint and add an **ARTrackableNotify** component:</span></span>

![QR AR 추적 가능 알림](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="0fdb0-125">**ARTrackableNotify** 를 선택하고 **세부 정보** 패널에서 **이벤트** 섹션을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-125">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel:</span></span>

![QR 이벤트](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="0fdb0-127">**추적 기하 도형 추가** 옆의 **+** 를 클릭하여 이벤트 그래프에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-127">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="0fdb0-128">[UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 구성 요소 API에서 이벤트의 전체 목록을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-128">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![추적된 기하 도형 추가 시 노드 추가](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a><span data-ttu-id="0fdb0-130">추적된 QR 코드 사용</span><span class="sxs-lookup"><span data-stu-id="0fdb0-130">Using a tracked QR code</span></span>
<span data-ttu-id="0fdb0-131">다음 이미지의 이벤트 그래프는 QR 코드의 가운데에 점을 렌더링하고 그 데이터를 출력하는 데 사용되는 **OnUpdateTrackedImage** 이벤트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-131">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

<span data-ttu-id="0fdb0-132">진행 상황은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-132">Here's what's going on:</span></span>
1. <span data-ttu-id="0fdb0-133">먼저 추적 이미지를 **ARTrackedQRCode** 에 캐스트하여 현재 업데이트된 이미지가 QR 코드인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-133">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="0fdb0-134">인코딩된 데이터는 **QRCode** 변수에서 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-134">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="0fdb0-135">**GetLocalToWorldTransform** 위치에서 QR 코드의 왼쪽 위를, **GetEstimateSize** 로 크기를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-135">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="0fdb0-136">코드에서 [QR 코드 좌표계를 가져올 수](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-136">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="0fdb0-137">고유 ID 찾기</span><span class="sxs-lookup"><span data-stu-id="0fdb0-137">Finding the unique ID</span></span>
<span data-ttu-id="0fdb0-138">모든 QR 코드에는 다음을 통해 찾을 수 있는 고유한 guid ID가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-138">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="0fdb0-139">**As ARTracked QRCode** 핀을 끌어서 놓고 검색하여 **고유 ID 가져오기**</span><span class="sxs-lookup"><span data-stu-id="0fdb0-139">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![QR Guid](images/unreal-qr-guid.PNG)

<span data-ttu-id="0fdb0-141">QR 코드를 사용하기 위해서는 뒤에서 많은 작업이 필요하므로 이것이 전부는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-141">There's a lot going on behind the scenes with QR codes, so you're not at the end of the road.</span></span> <span data-ttu-id="0fdb0-142">내부 작업을 더 상세히 설명하는 다음 링크를 확인해 보세요.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-142">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="0fdb0-143">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="0fdb0-143">Next Development Checkpoint</span></span>

<span data-ttu-id="0fdb0-144">앞에서 설명한 Unreal 개발 검사점 경험을 수행하는 경우 Mixed Reality 플랫폼 기능과 API를 탐색하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-144">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="0fdb0-145">여기에서 다음 항목을 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-145">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0fdb0-146">WinRT</span><span class="sxs-lookup"><span data-stu-id="0fdb0-146">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="0fdb0-147">또는 디바이스나 에뮬레이터에서 앱 배포로 직접 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-147">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0fdb0-148">디바이스에 배포</span><span class="sxs-lookup"><span data-stu-id="0fdb0-148">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="0fdb0-149">언제든지 [Unreal 개발 검사점](unreal-development-overview.md#3-platform-capabilities-and-apis)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fdb0-149">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fdb0-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fdb0-150">See also</span></span>
* [<span data-ttu-id="0fdb0-151">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="0fdb0-151">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="0fdb0-152">홀로그램</span><span class="sxs-lookup"><span data-stu-id="0fdb0-152">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="0fdb0-153">좌표계</span><span class="sxs-lookup"><span data-stu-id="0fdb0-153">Coordinate systems</span></span>](../../design/coordinate-systems.md)
