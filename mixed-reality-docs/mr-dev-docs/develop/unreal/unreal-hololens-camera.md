---
title: Unreal의 HoloLens 사진/비디오 카메라
description: Unreal에서 혼합 현실 캡처 및 개체 위치에 HoloLens 사진 및 비디오 카메라를 사용하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 기능, 설명서, 가이드, 홀로그램, 카메라, PV 카메라, MRC, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 6f1301e0daeb44521dfb4e93a915d49d9aea8443
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98247766"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="0944c-104">Unreal의 HoloLens 사진/비디오 카메라</span><span class="sxs-lookup"><span data-stu-id="0944c-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="0944c-105">HoloLens 바이저에는 MRC(혼합 현실 캡처)에 사용 가능하고 카메라 프레임의 픽셀 좌표로 Unreal 세계 공간의 개체를 찾는 데 사용할 수 있는 PV(사진/비디오) 카메라가 달려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0944c-105">The HoloLens has a Photo/Video (PV) Camera on the visor that can be used for both Mixed Reality Capture (MRC) and locating objects in Unreal world space from pixel coordinates in the camera frame.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0944c-106">홀로그램 원격 접속에서는 PV 카메라가 지원되지 않지만, HoloLens PV 카메라 기능을 시뮬레이션하기 위해 PC에 연결된 웹캠을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0944c-106">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

[!INCLUDE[](includes/tabs-pv-camera.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="0944c-107">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="0944c-107">Next Development Checkpoint</span></span>

<span data-ttu-id="0944c-108">앞에서 설명한 Unreal 개발 과정을 따르고 있다면 현재 Mixed Reality 플랫폼 기능 및 API를 살펴보는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="0944c-108">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="0944c-109">여기에서 다음 항목으로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0944c-109">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0944c-110">QR 코드</span><span class="sxs-lookup"><span data-stu-id="0944c-110">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="0944c-111">또는 디바이스나 에뮬레이터에서 앱 배포로 직접 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0944c-111">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0944c-112">디바이스에 배포</span><span class="sxs-lookup"><span data-stu-id="0944c-112">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="0944c-113">언제든지 [Unreal 개발 검사점](unreal-development-overview.md#3-advanced-features)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0944c-113">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="0944c-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0944c-114">See also</span></span>

* [<span data-ttu-id="0944c-115">위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="0944c-115">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="0944c-116">개발자를 위한 혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="0944c-116">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
