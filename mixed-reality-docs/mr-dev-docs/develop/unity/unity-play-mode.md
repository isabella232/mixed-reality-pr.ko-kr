---
title: Unity 플레이 모드
description: Unity 편집기에서 재생 모드를 사용하여 앱을 배포하지 않고 디바이스에서 애플리케이션 변경 내용을 미리 보는 방법을 알아봅니다.
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity, Remoting, 홀로그램 Remoting, 홀로그램 Remoting 플레이어, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, Unity 재생 모드
ms.openlocfilehash: b998233fda34beee0c98795a1efa2c86a53541ba
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392297"
---
# <a name="unity-play-mode"></a><span data-ttu-id="7b0c2-104">Unity 플레이 모드</span><span class="sxs-lookup"><span data-stu-id="7b0c2-104">Unity Play Mode</span></span>

<span data-ttu-id="7b0c2-105">Unity 프로젝트에서 작업하는 빠른 방법은 PC의 Unity 편집기에서 로컬로 앱을 실행하는 "재생 모드"를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7b0c2-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="7b0c2-106">Unity는 Holographic Remoting을 사용하여 실제 HoloLens 디바이스에서 콘텐츠를 미리 볼 수 있는 빠른 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7b0c2-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="7b0c2-107">재생 모드는 개발 PC에 연결된 Windows Mixed Reality 헤드셋과 함께 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b0c2-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="7b0c2-108">홀로그램 Remoting 설정</span><span class="sxs-lookup"><span data-stu-id="7b0c2-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="7b0c2-109">먼저 HoloLens 2 Microsoft Store [홀로그램 Remoting Player 앱을 설치해야](https://www.microsoft.com/store/productId/9NBLGGH4SV40) 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b0c2-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="7b0c2-110">HoloLens 2 Holographic Remoting Player 앱을 실행하면 연결할 버전 번호 및 IP 주소가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b0c2-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="7b0c2-111">OpenXR 플러그 인을 사용하려면 v2.4 이상</span><span class="sxs-lookup"><span data-stu-id="7b0c2-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens에서 실행 중인 홀로그램 Remoting Player의 스크린샷](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="7b0c2-113">홀로그램 Remoting을 통해 Unity 재생 모드</span><span class="sxs-lookup"><span data-stu-id="7b0c2-113">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="7b0c2-114">Holographic Remoting을 사용하면 PC의 Unity 편집기에서 실행되는 동안 HoloLens에서 앱을 경험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b0c2-114">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="7b0c2-115">응시, 제스처, 음성 및 공간 매핑 입력은 HoloLens에서 PC로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b0c2-115">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="7b0c2-116">그러면 렌더링된 프레임이 HoloLens로 다시 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b0c2-116">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="7b0c2-117">전체 프로젝트를 빌드하고 배포하지 않고도 앱을 신속하게 디버그할 수 있는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="7b0c2-117">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="7b0c2-118">홀로그램 Remoting에는 빠른 PC 및 Wi-Fi 연결이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7b0c2-118">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="7b0c2-119">자세한 내용은 [홀로그램 Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) 설명서에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b0c2-119">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="7b0c2-120">최상의 결과를 위해 앱이 [포커스 지점](focus-point-in-unity.md)를 제대로 설정했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7b0c2-120">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="7b0c2-121">이렇게 하면 홀로그램 Remoting이 무선 연결의 대기 시간을 가장 잘 조정하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b0c2-121">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b0c2-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b0c2-122">See Also</span></span>

* [<span data-ttu-id="7b0c2-123">홀로그램 원격 플레이어</span><span class="sxs-lookup"><span data-stu-id="7b0c2-123">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
