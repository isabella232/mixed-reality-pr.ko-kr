---
title: Unity 플레이 모드
description: Unity 편집기에서 Play 모드를 사용 하 여 앱을 배포 하지 않고 장치에서 응용 프로그램 변경 내용을 미리 보는 방법에 대해 알아봅니다.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, remoting, holographic remoting, holographic 원격 플레이어, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity 재생 모드
ms.openlocfilehash: caa9d7bf11104ee168fda24fc369de490feb7817
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547098"
---
# <a name="unity-play-mode"></a><span data-ttu-id="5246d-104">Unity 플레이 모드</span><span class="sxs-lookup"><span data-stu-id="5246d-104">Unity Play Mode</span></span>

<span data-ttu-id="5246d-105">Unity 프로젝트에서 작업 하는 빠른 방법은 PC의 Unity 편집기에서 로컬로 앱을 실행 하는 "재생 모드"를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="5246d-106">Unity는 Holographic 원격 기능을 사용 하 여 실제 HoloLens 장치에서 콘텐츠를 빠르게 미리 볼 수 있는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="5246d-107">재생 모드는 개발 PC에 연결 된 Windows Mixed Reality 헤드셋과 함께 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="5246d-108">Holographic 원격 설치</span><span class="sxs-lookup"><span data-stu-id="5246d-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="5246d-109">먼저 HoloLens 2의 Microsoft Store에서 [Holographic Remoting Player 앱을 설치](https://www.microsoft.com/store/productId/9NBLGGH4SV40) 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="5246d-110">HoloLens 2에서 Holographic 원격 플레이어 앱을 실행 하면 연결할 버전 번호와 IP 주소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="5246d-111">OpenXR 플러그 인을 사용 하려면 v 2.4 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens에서 실행 중인 Holographic 원격 플레이어의 스크린샷](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="5246d-113">Unity 편집기 재생 모드의 Holographic 원격 기능</span><span class="sxs-lookup"><span data-stu-id="5246d-113">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="5246d-114">Visual Studio 프로젝트에서 UWP Unity 프로젝트를 빌드한 다음 패키지 하 여 HoloLens 2 장치에 배포 하는 데 다소 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-114">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="5246d-115">한 가지 해결 방법은 Holographic Editor 원격 기능을 사용 하도록 설정 하는 것입니다 .이 기능을 사용 하면 네트워크를 통해 HoloLens 2 장치에 직접 "재생" 모드를 사용 하 여 c # 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-115">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="5246d-116">이 시나리오에서는 UWP 패키지를 빌드하여 원격 장치에 배포 하는 오버 헤드를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-116">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="5246d-117">[Holographic 원격 설치](#holographic-remoting-setup) 의 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-117">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="5246d-118">**Windows > XR > OpenXR Editor 원격** 기능을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-118">Open **Windows > XR > OpenXR Editor Remoting**:</span></span>

    ![XR 플러그 인 관리가 강조 표시 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-02.png)

3. <span data-ttu-id="5246d-120">Holographic Remoting 앱에서 가져온 IP 주소를 입력 하 고 **편집기 원격 기능 사용** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-120">Input the IP address you get from the Holographic Remoting app, and select **Enable Editor Remoting**</span></span>

    ![기능이 강조 표시 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-features-img-03.png)

<span data-ttu-id="5246d-122">이제 "재생" 단추를 클릭 하 여 HoloLens의 Holographic Remoting 앱에 Unity 앱을 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-122">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="5246d-123">[Visual Studio를 Unity에 연결](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) 하 여 재생 모드에서 c # 스크립트를 디버그할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-123">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="5246d-124">버전 0.1.0에서 Holographic Remoting 런타임은 앵커를 지원 하지 않으며 ARAnchorManager 기능은 원격 작업을 통해 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-124">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="5246d-125">이 기능은 이후 릴리스에서 제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-125">This feature is coming in future releases.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="5246d-126">Holographic 원격을 사용 하는 Unity 재생 모드</span><span class="sxs-lookup"><span data-stu-id="5246d-126">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="5246d-127">Holographic Remoting을 사용 하면 PC의 Unity 편집기에서 실행 되는 동안 HoloLens에서 앱을 경험해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-127">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="5246d-128">응시, 제스처, 음성 및 공간 매핑 입력은 HoloLens에서 PC로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-128">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="5246d-129">그러면 렌더링 된 프레임이 HoloLens로 다시 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-129">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="5246d-130">이 방법은 전체 프로젝트를 빌드하고 배포 하지 않고도 신속 하 게 앱을 디버그할 수 있는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-130">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="5246d-131">Holographic Remoting을 사용 하려면 고속 PC와 Wi-Fi 연결이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-131">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="5246d-132">자세한 내용은 [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) 설명서에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-132">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="5246d-133">최상의 결과를 위해 앱이 [포커스 지점을](focus-point-in-unity.md)적절히 설정 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-133">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="5246d-134">이렇게 하면 Holographic는 무선 연결의 대기 시간에 맞게 장면을 최적으로 조정 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5246d-134">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="5246d-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5246d-135">See Also</span></span>

* [<span data-ttu-id="5246d-136">홀로그램 원격 플레이어</span><span class="sxs-lookup"><span data-stu-id="5246d-136">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
