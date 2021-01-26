---
title: Holographic Remoting 원격 앱 작성 (OpenXR)
description: OpenXR를 사용 하 여 원격 컴퓨터에서 렌더링 된 원격 콘텐츠를 Holographic 원격 앱으로 HoloLens 2로 스트리밍하는 방법에 대해 알아봅니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, 원격, Holographic 원격, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, NuGet
ms.openlocfilehash: c5ba1b5c309b5d0ddd3bd46f0730f28c946d3c3f
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810083"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a><span data-ttu-id="756d1-104">OpenXR API를 사용 하 여 Holographic Remoting 원격 앱 작성</span><span class="sxs-lookup"><span data-stu-id="756d1-104">Writing a Holographic Remoting remote app using the OpenXR API</span></span>

>[!IMPORTANT]
><span data-ttu-id="756d1-105">이 문서에서는 [OPENXR API](../native/openxr.md)를 사용 하 여 HoloLens 2 및 Windows Mixed Reality 헤드셋 용 원격 응용 프로그램을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-105">This document describes the creation of a remote application for HoloLens 2 and Windows Mixed Reality headsets using the [OpenXR API](../native/openxr.md).</span></span> <span data-ttu-id="756d1-106">HoloLens 용 원격 응용 프로그램 **(첫 번째 gen)** 은 NuGet 패키지 **버전 1.x를 사용** 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-106">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="756d1-107">즉, HoloLens 2 용으로 작성 된 원격 응용 프로그램은 HoloLens 1과 호환 되지 않으며 그 반대의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-107">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="756d1-108">HoloLens 1에 대 한 설명서는 [여기](add-holographic-remoting.md)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-108">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="756d1-109">Holographic 원격 앱은 원격으로 렌더링 된 콘텐츠를 HoloLens 2 및 Windows Mixed Reality 모던 헤드셋으로 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-109">Holographic Remoting apps can stream remotely rendered content to HoloLens 2 and Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="756d1-110">더 많은 시스템 리소스에 액세스 하 고 기존 데스크톱 PC 소프트웨어에 원격 [몰입 형 보기](../../design/app-views.md) 를 통합할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-110">You can also access more system resources and integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="756d1-111">원격 앱은 HoloLens 2에서 입력 데이터 스트림을 받고, 가상 몰입 형 보기에서 콘텐츠를 렌더링 하 고, 콘텐츠 프레임을 HoloLens 2로 다시 스트리밍합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-111">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="756d1-112">연결은 표준 Wi-fi를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="756d1-113">Holographic Remoting은 NuGet 패킷을 통해 데스크톱 또는 UWP 앱에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-113">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="756d1-114">연결을 처리 하 고 몰입 형 보기에서 렌더링 하는 추가 코드가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-114">Additional code is required which handles the connection and renders in an immersive view.</span></span> <span data-ttu-id="756d1-115">일반적인 원격 연결의 경우 대기 시간은 50 밀리초로 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-115">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="756d1-116">플레이어 앱은 실시간으로 대기 시간을 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-116">The player app can report the latency in real time.</span></span>

<span data-ttu-id="756d1-117">이 페이지 및 작업 프로젝트의 모든 코드는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-117">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="756d1-118">필수 조건</span><span class="sxs-lookup"><span data-stu-id="756d1-118">Prerequisites</span></span>

<span data-ttu-id="756d1-119">좋은 출발점은 작업 OpenXR 기반 데스크톱 또는 UWP 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-119">A good starting point is a working OpenXR based Desktop or UWP app.</span></span> <span data-ttu-id="756d1-120">자세한 내용은 [OpenXR 시작](../native/openxr-getting-started.md)하기를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="756d1-120">For details see [Getting started with OpenXR](../native/openxr-getting-started.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="756d1-121">Holographic 원격을 사용 하는 모든 앱은 [다중 스레드 아파트](/windows/win32/com/multithreaded-apartments)를 사용 하도록 작성 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-121">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="756d1-122">[단일 스레드 아파트](/windows/win32/com/single-threaded-apartments) 를 사용 하는 것은 지원 되지만, 재생 하는 동안 일지 성능이 저하 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-122">The use of a [single-threaded apartment](/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="756d1-123">C + +/WinRT [winrt:: init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 사용 하는 경우 다중 스레드 아파트는 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-123">When using C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="756d1-124">Holographic 원격 NuGet 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="756d1-124">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="756d1-125">Visual Studio에서 프로젝트에 NuGet 패키지를 추가 하려면 다음 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-125">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="756d1-126">Visual Studio에서 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-126">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="756d1-127">프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **NuGet 패키지 관리 ...** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-127">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="756d1-128">표시 되는 패널에서 **찾아보기** 를 선택한 다음 "Holographic Remoting"을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-128">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="756d1-129">**Holographic** 를 선택 하 고 최신 **2.x 버전을** 선택 하 고 **설치** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-129">Select **Microsoft.Holographic.Remoting.OpenXr**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="756d1-130">**미리 보기** 대화 상자가 표시 되 면 **확인** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-130">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="756d1-131">사용권 계약 대화 상자가 표시 되 면 **동의** 함을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-131">Select **I Accept** when the license agreement dialog pops up.</span></span>
7. <span data-ttu-id="756d1-132">다음 NuGet 패키지에 대해 3 ~ 6 단계를 반복 합니다. OpenXR, OpenXR</span><span class="sxs-lookup"><span data-stu-id="756d1-132">Repeat the steps 3 to 6 for the following NuGet Packages: OpenXR.Headers, OpenXR.Loader</span></span>

>[!NOTE]
><span data-ttu-id="756d1-133">HoloLens 1을 대상으로 하는 개발자에 게는 NuGet 패키지의 버전 **1. x. x** 를 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-133">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="756d1-134">자세한 내용은 [Holographic 원격 추가 (HoloLens (첫 번째 gen))](add-holographic-remoting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="756d1-134">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="select-the-holographic-remoting-openxr-runtime"></a><span data-ttu-id="756d1-135">Holographic Remoting OpenXR runtime을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-135">Select the Holographic Remoting OpenXR runtime</span></span>

<span data-ttu-id="756d1-136">원격 앱에서 수행 해야 하는 첫 번째 단계는 OpenXr NuGet 패키지의 일부인 Holographic Remoting OpenXR runtime을 선택 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-136">The first step you need to do in your remote app is to select the Holographic Remoting OpenXR runtime, which is part of the Microsoft.Holographic.Remoting.OpenXr NuGet package.</span></span> <span data-ttu-id="756d1-137">이렇게 하려면 ```XR_RUNTIME_JSON``` 환경 변수를 앱 내 파일의 RemotingXR.js경로에 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-137">You can do this by setting the ```XR_RUNTIME_JSON``` environment variable to the path of the RemotingXR.json file within your app.</span></span> <span data-ttu-id="756d1-138">이 환경 변수는 OpenXR 로더가 시스템 기본 OpenXR 런타임을 사용 하지 않고 대신 Holographic Remoting OpenXR 런타임으로 리디렉션하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-138">This environment variable is used by the OpenXR loader to not use the system default OpenXR runtime but instead redirect to the Holographic Remoting OpenXR runtime.</span></span> <span data-ttu-id="756d1-139">Holographic OpenXr NuGet 패키지를 사용 하는 경우 파일의 RemotingXR.js출력 폴더로 컴파일하는 동안 자동으로 복사 됩니다. 일반적으로 OpenXR 런타임 선택은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-139">When using the Microsoft.Holographic.Remoting.OpenXr NuGet package the RemotingXR.json file is automatically copied during compilation to the output folder, the OpenXR runtime selection typically looks as follows.</span></span>

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a><span data-ttu-id="756d1-140">Holographic Remoting 확장을 사용 하 여 XrInstance 만들기</span><span class="sxs-lookup"><span data-stu-id="756d1-140">Create XrInstance with Holographic Remoting Extension</span></span>

<span data-ttu-id="756d1-141">일반적인 OpenXR 앱이 수행 해야 하는 첫 번째 단계는 OpenXR extensions를 선택 하 고 XrInstance를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-141">The first step a typical OpenXR app is supposed to do is to select OpenXR extensions and create an XrInstance.</span></span> <span data-ttu-id="756d1-142">OpenXR core 사양은 remoting 특정 API를 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-142">The OpenXR core specification doesn't provide any remoting specific API.</span></span> <span data-ttu-id="756d1-143">이러한 이유로 Holographic Remoting은 이라는 고유한 OpenXR 확장을 도입 ```XR_MSFT_holographic_remoting``` 했습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-143">For that reason Holographic Remoting introduces its own OpenXR extension named ```XR_MSFT_holographic_remoting```.</span></span> <span data-ttu-id="756d1-144">XrCreateInstance를 호출할 때 ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` XrInstanceCreateInfo에 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-144">Ensure that when you call xrCreateInstance the ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` is included in the XrInstanceCreateInfo.</span></span>

>[!TIP]
><span data-ttu-id="756d1-145">기본적으로 앱의 렌더링 된 콘텐츠는 HoloLens 2 또는 Windows Mixed Reality 헤드셋에서 실행 되는 Holographic Remoting 플레이어로만 스트리밍됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-145">By default the rendered content of your app is only streamed to the Holographic Remoting player either running on a HoloLens 2 or on a Windows Mixed Reality headsets.</span></span> <span data-ttu-id="756d1-146">또한 원격 PC에서 렌더링 된 콘텐츠를 표시 하기 위해 예를 들어 창의 스왑 체인을 통해 Holographic Remoting은 이라는 두 번째 OpenXR 확장을 제공 ```XR_MSFT_holographic_remoting_frame_mirroring``` 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-146">To also display the rendered content on the remote PC, via a swap-chain of a window for instance, Holographic Remoting provides a second OpenXR extension named ```XR_MSFT_holographic_remoting_frame_mirroring```.</span></span> <span data-ttu-id="756d1-147">해당 기능을 사용 하려는 경우에도를 사용 하 여이 확장을 사용 하도록 설정 해야 ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-147">Ensure to also enable this extension using ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` in case you want to use that functionality.</span></span>

>[!IMPORTANT]
><span data-ttu-id="756d1-148">Holographic Remoting OpenXR extension API에 대 한 자세한 내용은 [Holographic remoting 샘플 github 리포지토리에서](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)찾을 수 있는 [사양을](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="756d1-148">To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="connect-to-the-device"></a><span data-ttu-id="756d1-149">장치에 연결</span><span class="sxs-lookup"><span data-stu-id="756d1-149">Connect to the device</span></span>

<span data-ttu-id="756d1-150">원격 앱이 XrInstance를 만들고 xrGetSystem을 통해 XrSystemId를 쿼리하면 플레이어 장치에 대 한 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-150">After your remote app has created the XrInstance and queried the XrSystemId via xrGetSystem a connection to the player device can be established.</span></span>

>[!WARNING]
> <span data-ttu-id="756d1-151">Holographic Remoting OpenXR 런타임은 연결이 설정 된 후에 보기 구성 또는 환경 blend 모드와 같은 장치별 데이터를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-151">The Holographic Remoting OpenXR runtime is only able to provide device specific data such as view configurations or environment blend modes after a connection has been established.</span></span> <span data-ttu-id="756d1-152">```xrEnumerateViewConfigurations```,,, ```xrEnumerateViewConfigurationViews``` ```xrGetViewConfigurationProperties``` ```xrEnumerateEnvironmentBlendModes``` 및 ```xrGetSystemProperties``` 는 모두 연결 되기 전에 HoloLens 2에서 실행 되는 플레이어에 연결 하는 경우 일반적으로 얻을 수 있는 값과 일치 하는 기본값을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-152">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews```, ```xrGetViewConfigurationProperties```, ```xrEnumerateEnvironmentBlendModes```, and ```xrGetSystemProperties``` will give you default values, matching what you would typically get if you connect to a player running on a HoloLens 2, before being fully connected.</span></span>
<span data-ttu-id="756d1-153">연결이 설정 되기 전에는 이러한 메서드를 호출 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-153">It is strongly recommended to not call these methods before a connection has been established.</span></span> <span data-ttu-id="756d1-154">이러한 메서드는 XrSession을 성공적으로 만들고 세션 상태가 XR_SESSION_STATE_READY 이상인 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-154">The suggestion is used these methods after the XrSession has been successfully created and the session state is at least XR_SESSION_STATE_READY.</span></span>

<span data-ttu-id="756d1-155">다음을 통해 최대 비트 전송률, 오디오 사용, 비디오 코덱 또는 깊이 버퍼 스트림 확인과 같은 일반 속성을 구성할 수 있습니다 ```xrRemotingSetContextPropertiesMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="756d1-155">General properties such as max bitrate, audio enabled, video codec, or depth buffer stream resolution can be configured via ```xrRemotingSetContextPropertiesMSFT``` as follows.</span></span>

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

<span data-ttu-id="756d1-156">연결은 두 가지 방법 중 하나로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-156">The connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="756d1-157">원격 앱은 장치에서 실행 중인 플레이어에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-157">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="756d1-158">장치에서 실행 되는 플레이어가 원격 앱에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-158">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="756d1-159">원격 앱에서 플레이어 장치로의 연결을 설정 하려면 ```xrRemotingConnectMSFT``` 구조를 통해 호스트 이름 및 포트를 지정 하는 메서드를 호출 합니다  ```XrRemotingConnectInfoMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="756d1-159">To establish a connection from the remote app to the player device call the ```xrRemotingConnectMSFT``` method specifying the hostname and port via the  ```XrRemotingConnectInfoMSFT``` structure.</span></span> <span data-ttu-id="756d1-160">Holographic Remoting 플레이어에서 사용 하는 포트는 **8265** 입니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-160">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

<span data-ttu-id="756d1-161">원격 앱에서 들어오는 연결을 수신 하는 작업은 메서드를 호출 하 여 수행할 수 있습니다 ```xrRemotingListenMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="756d1-161">Listening for incoming connections on the remote app can be done by calling the ```xrRemotingListenMSFT``` method.</span></span> <span data-ttu-id="756d1-162">핸드셰이크 포트와 전송 포트는 모두 구조를 통해 지정할 수 있습니다 ```XrRemotingListenInfoMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="756d1-162">Both the handshake port and transport port can be specified via the ```XrRemotingListenInfoMSFT``` structure.</span></span> <span data-ttu-id="756d1-163">핸드셰이크 포트는 초기 핸드셰이크에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-163">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="756d1-164">그러면 전송 포트를 통해 데이터가 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-164">The data is then sent over the transport port.</span></span> <span data-ttu-id="756d1-165">기본적으로 **8265** 및 **8266** 이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-165">By default **8265** and **8266** are used.</span></span>

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

<span data-ttu-id="756d1-166">또는를 호출할 때 연결 상태를 해제 해야 ```xrRemotingConnectMSFT``` 합니다 ```xrRemotingListenMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="756d1-166">The connection state must be disconnected when you call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT```.</span></span> <span data-ttu-id="756d1-167">XrInstance를 만들고를 통해 XrSystemId에 대해 쿼리 한 후 언제 든 지 연결 상태를 가져올 수 있습니다 ```xrRemotingGetConnectionStateMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="756d1-167">You can get the connection state at any point after you have created an XrInstance and queried for the XrSystemId via ```xrRemotingGetConnectionStateMSFT```.</span></span>

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

<span data-ttu-id="756d1-168">사용 가능한 연결 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-168">Available connection states are:</span></span>
- <span data-ttu-id="756d1-169">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="756d1-169">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span></span>
- <span data-ttu-id="756d1-170">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span><span class="sxs-lookup"><span data-stu-id="756d1-170">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span></span>
- <span data-ttu-id="756d1-171">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="756d1-171">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span></span>

>[!IMPORTANT]
> <span data-ttu-id="756d1-172">```xrRemotingConnectMSFT``````xrRemotingListenMSFT```xrCreateSession를 통해 XrSession을 만들기 전에 또는를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-172">```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` must be called before trying to create a XrSession via xrCreateSession.</span></span> <span data-ttu-id="756d1-173">연결 상태가 인 동안 XrSession을 만들려고 하면 ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` 세션 생성은 성공 하지만 세션 상태는 즉시 XR_SESSION_STATE_LOSS_PENDING로 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-173">If you try to create a XrSession while the connection state is ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session creation will succeed but the session state will immediately transition to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="756d1-174">Holographic Remoting의 구현은 ```xrCreateSession``` 연결 설정 대기를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-174">Holographic Remoting's implementation of ```xrCreateSession``` supports waiting for a connection to be established.</span></span> <span data-ttu-id="756d1-175">```xrRemotingConnectMSFT```를 호출 하거나 ```xrRemotingListenMSFT``` 바로 다음에 호출 하 여 연결이 설정 될 때까지 차단 하 고 대기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-175">You can call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` immediately followed by a call to, which will block and wait for a connection to be established.</span></span> <span data-ttu-id="756d1-176">제한 시간은 10 초로 고정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-176">The timeout is fixed to 10 seconds.</span></span> <span data-ttu-id="756d1-177">이 시간 내에 연결을 설정할 수 있는 경우 XrSession 만들기가 성공 하 고 세션 상태가 XR_SESSION_STATE_READY로 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-177">If a connection can be established within this time the XrSession creation will succeed and the session state will transition to XR_SESSION_STATE_READY.</span></span> <span data-ttu-id="756d1-178">연결을 설정할 수 없는 경우에도 세션 만들기는 성공 하지만 즉시 XR_SESSION_STATE_LOSS_PENDING로 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-178">In case no connection can be established the session creation also succeeds but immediately transitions to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="756d1-179">일반적으로 연결 상태는 XrSession 상태와 두 가지입니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-179">In general, the connection state is couple with the XrSession state.</span></span> <span data-ttu-id="756d1-180">연결 상태에 대 한 변경 내용은 세션 상태에도 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-180">Any change to the connection state also affects the session state.</span></span> <span data-ttu-id="756d1-181">예를 들어 연결 상태가에서 `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` 로 전환 되 면 ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` 세션 상태가 XR_SESSION_STATE_LOSS_PENDING로 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-181">For instance, if the connection state switches from `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` to ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session state will transition to XR_SESSION_STATE_LOSS_PENDING as well.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="756d1-182">원격 특정 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="756d1-182">Handling Remoting specific events</span></span>

<span data-ttu-id="756d1-183">Holographic Remoting OpenXR runtime은 연결 상태를 모니터링 하는 데 중요 한 세 개의 이벤트를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-183">The Holographic Remoting OpenXR runtime exposes three events, which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="756d1-184">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: 장치에 대 한 연결이 성공적으로 설정 된 경우에 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-184">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Triggered when a connection to the device has been successfully established.</span></span>
2) <span data-ttu-id="756d1-185">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: 설정 된 연결이 닫히거나 연결을 설정할 수 없는 경우에 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-185">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Triggered if an established connection is closed or a connection couldn't be established.</span></span>
3) <span data-ttu-id="756d1-186">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: 들어오는 연결을 수신 하는 작업이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-186">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: When listening for incoming connections starts.</span></span>

<span data-ttu-id="756d1-187">이러한 이벤트는 큐에 배치 되며 원격 앱은 질서 via를 사용 하 여 큐에서 읽어야 합니다 ```xrPollEvent``` .</span><span class="sxs-lookup"><span data-stu-id="756d1-187">These events are placed in a queue and your remote app must read from the queue with regularity via ```xrPollEvent```.</span></span>

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="756d1-188">스트리밍 콘텐츠를 로컬로 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-188">Preview streamed content locally</span></span>

<span data-ttu-id="756d1-189">장치에 전송 된 원격 앱에 동일한 콘텐츠를 표시 하려면 ```XR_MSFT_holographic_remoting_frame_mirroring``` 확장을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-189">To display the same content in the remote app that is sent to the device the ```XR_MSFT_holographic_remoting_frame_mirroring``` extension can be used.</span></span> <span data-ttu-id="756d1-190">이 확장을 사용 하면 ```XrRemotingFrameMirrorImageInfoMSFT``` 다음과 같이 Xr프레임 끝 정보에 연결 되지 않은를 사용 하 여 xrEndFrame에 질감을 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-190">With this extension, you can submit a texture to xrEndFrame by using the ```XrRemotingFrameMirrorImageInfoMSFT``` that isn't chained to the XrFrameEndInfo as follows.</span></span>

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

<span data-ttu-id="756d1-191">위의 예제에서는 DX11를 사용 하 여 xrEndFrame에 대 한 호출 바로 뒤에 창을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-191">The example above uses a DX11 swap-chain texture and presents the window immediately after the call to xrEndFrame.</span></span> <span data-ttu-id="756d1-192">사용량은 스왑 체인 질감으로 제한 되지 않으며 추가 GPU 동기화가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-192">The usage isn't restricted to swap-chain textures and no additional GPU synchronization is required.</span></span> <span data-ttu-id="756d1-193">사용 및 제약 조건에 대 한 자세한 내용은 [확장 사양을](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring)확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="756d1-193">For details on usage and constraints check out the [extension specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span></span>
<span data-ttu-id="756d1-194">원격 앱에서 DX12를 사용 하는 경우 XrRemotingFrameMirrorImageD3D11MSFT 대신 XrRemotingFrameMirrorImageD3D12MSFT를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="756d1-194">If your remote app is using DX12 use XrRemotingFrameMirrorImageD3D12MSFT instead of XrRemotingFrameMirrorImageD3D11MSFT.</span></span>

## <a name="see-also"></a><span data-ttu-id="756d1-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="756d1-195">See Also</span></span>
* [<span data-ttu-id="756d1-196">사용자 지정 홀로그램 원격 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="756d1-196">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="756d1-197">홀로그램 원격을 사용하여 보안 연결 설정</span><span class="sxs-lookup"><span data-stu-id="756d1-197">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="756d1-198">Holographic 원격 문제 해결 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="756d1-198">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="756d1-199">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="756d1-199">Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="756d1-200">Microsoft 개인정보처리방침</span><span class="sxs-lookup"><span data-stu-id="756d1-200">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)