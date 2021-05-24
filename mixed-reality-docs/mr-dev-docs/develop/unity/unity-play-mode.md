---
title: Unity 플레이 모드
description: Unity 편집기에서 재생 모드를 사용하여 앱을 배포하지 않고 디바이스에서 애플리케이션 변경 내용을 미리 보는 방법을 알아봅니다.
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Remoting, 홀로그램 Remoting, 홀로그램 Remoting 플레이어, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, Unity 재생 모드
ms.openlocfilehash: 35f80b0c217adfd5c5d14799dc882d5c504925aa
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333424"
---
# <a name="unity-play-mode"></a><span data-ttu-id="f8e31-104">Unity 플레이 모드</span><span class="sxs-lookup"><span data-stu-id="f8e31-104">Unity Play Mode</span></span>

<span data-ttu-id="f8e31-105">Unity 프로젝트에서 작업하는 빠른 방법은 PC의 Unity 편집기에서 로컬로 앱을 실행하는 "재생 모드"를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="f8e31-106">Unity는 Holographic Remoting을 사용하여 실제 HoloLens 디바이스에서 콘텐츠를 미리 볼 수 있는 빠른 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="f8e31-107">재생 모드는 개발 PC에 연결된 Windows Mixed Reality 헤드셋과 함께 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="f8e31-108">홀로그램 Remoting 설정</span><span class="sxs-lookup"><span data-stu-id="f8e31-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="f8e31-109">먼저 HoloLens 2 Microsoft Store [Holographic Remoting Player 앱을 설치해야](https://www.microsoft.com/store/productId/9NBLGGH4SV40) 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="f8e31-110">HoloLens 2 Holographic Remoting Player 앱을 실행하면 연결할 버전 번호 및 IP 주소가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="f8e31-111">OpenXR 플러그 인을 사용하려면 v2.4 이상</span><span class="sxs-lookup"><span data-stu-id="f8e31-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens에서 실행 중인 홀로그램 Remoting Player의 스크린샷](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="f8e31-113">Unity 편집기 재생 모드의 홀로그램 Remoting</span><span class="sxs-lookup"><span data-stu-id="f8e31-113">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="f8e31-114">Visual Studio 프로젝트에서 UWP Unity 프로젝트를 빌드한 다음 HoloLens 2 디바이스에 패키징하고 배포하는 데 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-114">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="f8e31-115">한 가지 해결 방법은 홀로그램 편집기 Remoting 기능을 사용하도록 설정하여 "재생" 모드를 사용하여 C# 스크립트를 네트워크를 통해 HoloLens 2 디바이스로 직접 디버그할 수 있도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-115">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="f8e31-116">이 시나리오에서는 UWP 패키지를 빌드하고 원격 디바이스에 배포하는 오버헤드를 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-116">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="f8e31-117">[홀로그램 Remoting 설정의](#holographic-remoting-setup) 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-117">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="f8e31-118">**OpenXR Editor Remoting을 > Windows > XR을 엽니다.**</span><span class="sxs-lookup"><span data-stu-id="f8e31-118">Open **Windows > XR > OpenXR Editor Remoting**:</span></span>

    ![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-02.png)

3. <span data-ttu-id="f8e31-120">홀로그램 Remoting 앱에서 얻는 IP 주소를 입력하고 **편집기 Remoting 사용을** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-120">Input the IP address you get from the Holographic Remoting app, and select **Enable Editor Remoting**</span></span>

    ![기능이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-03.png)

<span data-ttu-id="f8e31-122">이제 "재생" 단추를 클릭하여 HoloLens의 Holographic Remoting 앱에서 Unity 앱을 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-122">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="f8e31-123">[Visual Studio를 Unity에 연결](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) 하 여 재생 모드에서 c # 스크립트를 디버그할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-123">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="f8e31-124">버전 0.1.0에서 Holographic Remoting 런타임은 앵커를 지원 하지 않으며 ARAnchorManager 기능은 원격 작업을 통해 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-124">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="f8e31-125">이 기능은 이후 릴리스에서 제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-125">This feature is coming in future releases.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="f8e31-126">Holographic 원격을 사용 하는 Unity 재생 모드</span><span class="sxs-lookup"><span data-stu-id="f8e31-126">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="f8e31-127">Holographic Remoting을 사용 하면 PC의 Unity 편집기에서 실행 되는 동안 HoloLens에서 앱을 경험해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-127">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="f8e31-128">응시, 제스처, 음성 및 공간 매핑 입력은 HoloLens에서 PC로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-128">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="f8e31-129">그러면 렌더링 된 프레임이 HoloLens로 다시 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-129">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="f8e31-130">이 방법은 전체 프로젝트를 빌드하고 배포 하지 않고도 신속 하 게 앱을 디버그할 수 있는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-130">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="f8e31-131">HoloLens에서 **Microsoft Store** 로 이동 하 여 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 앱을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-131">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="f8e31-132">HoloLens에서 **Holographic Remoting Player** 앱을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-132">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="f8e31-133">Unity에서 **창** 메뉴로 이동 하 여 **XR** 하위 메뉴를 확장 하 고 **Holographic 에뮬레이션** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-133">In Unity, go to the **Window** menu, expand the **XR** submenu, and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="f8e31-134">**에뮬레이션 모드** 를 **원격에서 장치로** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-134">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="f8e31-135">**원격 컴퓨터** 의 경우 HOLOLENS의 IP 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-135">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="f8e31-136">**연결** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-136">Select **Connect**.</span></span> <span data-ttu-id="f8e31-137">**연결 상태가** **연결 됨** 으로 변경 되 고 HoloLens에서 화면이 비어 있는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-137">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="f8e31-138">재생 모드를 시작 하 고 HoloLens에서 앱을 경험 하려면 **재생** 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-138">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="f8e31-139">Holographic Remoting을 사용 하려면 고속 PC와 Wi-Fi 연결이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-139">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="f8e31-140">자세한 내용은 [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) 설명서에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-140">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="f8e31-141">최상의 결과를 위해 앱이 [포커스 지점을](focus-point-in-unity.md)적절히 설정 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-141">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="f8e31-142">이렇게 하면 Holographic는 무선 연결의 대기 시간에 맞게 장면을 최적으로 조정 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8e31-142">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8e31-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f8e31-143">See Also</span></span>
* [<span data-ttu-id="f8e31-144">홀로그램 원격 플레이어</span><span class="sxs-lookup"><span data-stu-id="f8e31-144">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
