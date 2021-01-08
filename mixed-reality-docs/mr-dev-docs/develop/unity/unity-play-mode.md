---
title: Unity 플레이 모드
description: Unity 편집기에서 Play 모드를 사용 하 여 앱을 배포 하지 않고 장치에서 응용 프로그램 변경 내용을 미리 보는 방법에 대해 알아봅니다.
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, remoting, holographic remoting, holographic 원격 플레이어, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity 재생 모드
ms.openlocfilehash: 9f6c2cafd08fca8a5d60f3fcf5832ee74762e173
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009843"
---
# <a name="unity-play-mode"></a><span data-ttu-id="8f677-104">Unity 플레이 모드</span><span class="sxs-lookup"><span data-stu-id="8f677-104">Unity Play Mode</span></span>

<span data-ttu-id="8f677-105">Unity 프로젝트에서 작업 하는 빠른 방법은 PC의 Unity 편집기에서 로컬로 앱을 실행 하는 "재생 모드"를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="8f677-106">Unity는 Holographic 원격 기능을 사용 하 여 실제 HoloLens 장치에서 콘텐츠를 빠르게 미리 볼 수 있는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="8f677-107">재생 모드는 개발 PC에 연결 된 Windows Mixed Reality 헤드셋과 함께 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="8f677-108">Holographic 원격을 사용 하는 Unity 재생 모드</span><span class="sxs-lookup"><span data-stu-id="8f677-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="8f677-109">Holographic Remoting을 사용 하면 PC의 Unity 편집기에서 실행 되는 동안 HoloLens에서 앱을 경험해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-109">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="8f677-110">응시, 제스처, 음성 및 공간 매핑 입력은 HoloLens에서 PC로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="8f677-111">그러면 렌더링 된 프레임이 HoloLens로 다시 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="8f677-112">이 방법은 전체 프로젝트를 빌드하고 배포 하지 않고도 신속 하 게 앱을 디버그할 수 있는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="8f677-113">HoloLens에서 **Microsoft Store** 로 이동 하 여 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 앱을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="8f677-114">HoloLens에서 **Holographic Remoting Player** 앱을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="8f677-115">Unity에서 **창** 메뉴로 이동 하 여 **XR** 하위 메뉴를 확장 하 고 **Holographic 에뮬레이션** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-115">In Unity, go to the **Window** menu, expand the **XR** submenu, and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="8f677-116">**에뮬레이션 모드** 를 **원격에서 장치로** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="8f677-117">**원격 컴퓨터** 의 경우 HOLOLENS의 IP 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="8f677-118">**연결** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-118">Select **Connect**.</span></span> <span data-ttu-id="8f677-119">**연결 상태가** **연결 됨** 으로 변경 되 고 HoloLens에서 화면이 비어 있는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="8f677-120">재생 모드를 시작 하 고 HoloLens에서 앱을 경험 하려면 **재생** 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-120">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="8f677-121">Holographic Remoting을 사용 하려면 고속 PC와 Wi-Fi 연결이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="8f677-122">자세한 내용은 [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) 설명서에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-122">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="8f677-123">최상의 결과를 위해 앱이 [포커스 지점을](focus-point-in-unity.md)적절히 설정 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="8f677-124">이렇게 하면 Holographic는 무선 연결의 대기 시간에 맞게 장면을 최적으로 조정 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f677-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f677-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f677-125">See Also</span></span>
* [<span data-ttu-id="8f677-126">홀로그램 원격 플레이어</span><span class="sxs-lookup"><span data-stu-id="8f677-126">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
