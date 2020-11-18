---
title: Unreal의 HoloLens 사진/비디오 카메라
description: Unreal에서 HoloLens 사진/비디오 카메라 사용 가이드
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, 카메라, PV 카메라, MRC
ms.openlocfilehash: 6302a64fcde2a16b6ae1cb570215629a3e6ea9e5
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573237"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="ceaa4-104">Unreal의 HoloLens 사진/비디오 카메라</span><span class="sxs-lookup"><span data-stu-id="ceaa4-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="ceaa4-105">개요</span><span class="sxs-lookup"><span data-stu-id="ceaa4-105">Overview</span></span>

<span data-ttu-id="ceaa4-106">HoloLens에는 MRC(혼합 현실 캡처)에서 사용하며 앱에서 실세계 시각적 개체에 액세스하는 데 사용하는 PV(사진/비디오) 카메라가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="ceaa4-107">홀로그램 원격 접속에서는 PV 카메라가 지원되지 않지만, HoloLens PV 카메라 기능을 시뮬레이션하기 위해 PC에 연결된 웹캠을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-107">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="ceaa4-108">MRC용 PV 카메라에서 렌더링</span><span class="sxs-lookup"><span data-stu-id="ceaa4-108">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="ceaa4-109">여기에는 **Unreal Engine 4.25** 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-109">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="ceaa4-110">시스템 및 사용자 지정 MRC 레코더는 몰입형 앱에서 렌더링한 홀로그램과 PV 카메라를 결합하여 혼합 현실 캡처를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-110">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="ceaa4-111">기본적으로 혼합 현실 캡처는 오른쪽 눈의 홀로그램 출력을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-111">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="ceaa4-112">몰입 형 앱이 [PV 카메라에서 렌더링](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)하도록 선택한 경우 해당 항목을 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-112">If an immersive app chooses to [render from the PV Camera](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="ceaa4-113">이를 통해 MRC 영상에서 실제 세계와 홀로그램의 매핑이 개선됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-113">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="ceaa4-114">PV 카메라에서 렌더링하도록 옵트인하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-114">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="ceaa4-115">**SetEnabledMixedRealityCamera** 및 **ResizeMixedRealityCamera** 호출</span><span class="sxs-lookup"><span data-stu-id="ceaa4-115">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="ceaa4-116">**크기 X** 및 **크기 Y** 값을 사용하여 비디오 크기를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-116">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![세 번째 카메라](../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="ceaa4-118">그러면 Unreal은 PV 카메라의 관점에서 렌더링하는 MRC의 요청을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-118">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="ceaa4-119">[혼합 현실 캡처](../../mixed-reality-capture.md)가 트리거된 경우에만 앱이 사진/비디오 카메라의 관점에서 렌더링하도록 요청됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-119">Only when [Mixed Reality Capture](../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="ceaa4-120">PV 카메라 사용</span><span class="sxs-lookup"><span data-stu-id="ceaa4-120">Using the PV Camera</span></span>

<span data-ttu-id="ceaa4-121">웹캠 질감을 게임에서 런타임에 검색할 수 있지만 편집기의 **편집 > 프로젝트 설정** 에서 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-121">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="ceaa4-122">**플랫폼 > HoloLens > 기능** 으로 이동하여 **웹캠** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-122">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="ceaa4-123">**StartCameraCapture** 함수를 사용하여 런타임에 웹캠을 사용하고 **StopCameraCapture** 함수를 사용하여 기록을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-123">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Camera 시작 중지](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="ceaa4-125">이미지 렌더링</span><span class="sxs-lookup"><span data-stu-id="ceaa4-125">Rendering an image</span></span>
<span data-ttu-id="ceaa4-126">카메라 이미지를 렌더링하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-126">To render the camera image:</span></span>
1. <span data-ttu-id="ceaa4-127">프로젝트의 재질을 기반으로 동적 재질 인스턴스를 만듭니다. 아래 스크린샷에서 이름이 **PVCamMat** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-127">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="ceaa4-128">동적 재질 인스턴스를 **재질 인스턴스 동적 개체 참조** 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-128">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="ceaa4-129">카메라 피드를 렌더링하는 장면의 개체 재질을 이 새로운 동적 재질 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-129">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="ceaa4-130">카메라 이미지를 재질에 바인딩하는 데 사용할 타이머를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-130">Start a timer that will be used to bind the camera image to the material.</span></span>

![카메라 렌더링](images/unreal-camera-render.PNG)

4. <span data-ttu-id="ceaa4-132">이 타이머에 대한 새로운 기능을 만들고(이 경우 **MaterialTimer**), **GetARCameraImage** 를 호출하여 웹캠에서 질감을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-132">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="ceaa4-133">이 질감이 유효한 경우 음영의 질감 매개 변수를 이 이미지로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-133">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="ceaa4-134">그렇지 않으면 재질 타이머를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-134">Otherwise, start the material timer again.</span></span>

![웹캠의 카메라 텍스처](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="ceaa4-136">재질에 색 항목에 바인딩된 **SetTextureParameterValue** 의 이름과 일치하는 매개 변수가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-136">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="ceaa4-137">매개 변수가 없으면 카메라 이미지를 제대로 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-137">Without this, the camera image can't be properly displayed.</span></span>

![카메라 텍스처](images/unreal-camera-material.PNG)

## <a name="next-development-checkpoint"></a><span data-ttu-id="ceaa4-139">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="ceaa4-139">Next Development Checkpoint</span></span>

<span data-ttu-id="ceaa4-140">앞에서 설명한 Unreal 개발 검사점 경험을 수행하는 경우 Mixed Reality 플랫폼 기능과 API를 탐색하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-140">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="ceaa4-141">여기에서 다음 항목을 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-141">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ceaa4-142">QR 코드</span><span class="sxs-lookup"><span data-stu-id="ceaa4-142">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="ceaa4-143">또는 디바이스나 에뮬레이터에서 앱 배포로 직접 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-143">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ceaa4-144">디바이스에 배포</span><span class="sxs-lookup"><span data-stu-id="ceaa4-144">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="ceaa4-145">언제든지 [Unreal 개발 검사점](unreal-development-overview.md#3-platform-capabilities-and-apis)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceaa4-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="ceaa4-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ceaa4-146">See also</span></span>
* [<span data-ttu-id="ceaa4-147">위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="ceaa4-147">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="ceaa4-148">개발자를 위한 혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="ceaa4-148">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
