---
title: 6. 패키징 후 디바이스 또는 에뮬레이터에 배포
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그 인을 사용하여 체스 앱을 만드는 자습서 시리즈 6/6부
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 자습서, 시작, mrtk, uxt, UX Tools, 설명서, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 83d8068ca8ce73f23edb85cf9044db5409105380
ms.sourcegitcommit: 9a93c9e9b3b088da942ac4386813ecf263c2e324
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865398"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="0848b-104">6. 패키징 후 디바이스 또는 에뮬레이터에 배포</span><span class="sxs-lookup"><span data-stu-id="0848b-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="0848b-105">이전 자습서에서는 체스 말을 원래 위치로 다시 설정하는 간단한 단추를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-105">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="0848b-106">이 마지막 섹션에서는 HoloLens 2 또는 에뮬레이터에서 앱을 실행할 수 있게 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-106">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="0848b-107">HoloLens 2가 있는 경우 컴퓨터에서 스트리밍하거나 앱을 패키징하여 디바이스에서 직접 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-107">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="0848b-108">디바이스가 없는 경우 에뮬레이터에서 실행되도록 앱을 패키징합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-108">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="0848b-109">이 섹션을 마치면 재생할 수 있는 혼합 현실 앱이 배포되며 조작과 UI가 완성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-109">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="0848b-110">목표</span><span class="sxs-lookup"><span data-stu-id="0848b-110">Objectives</span></span>

* <span data-ttu-id="0848b-111">[디바이스 전용] 홀로그램 앱 원격 기능을 통해 HoloLens 2에 스트리밍</span><span class="sxs-lookup"><span data-stu-id="0848b-111">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="0848b-112">HoloLens 2 디바이스 또는 에뮬레이터에 앱 패키징 및 배포</span><span class="sxs-lookup"><span data-stu-id="0848b-112">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="0848b-113">[디바이스 전용] 스트리밍</span><span class="sxs-lookup"><span data-stu-id="0848b-113">[Device Only] Streaming</span></span>

<span data-ttu-id="0848b-114">[홀로그램 원격 접속](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting)은 채널을 전환하는 것이 아니라 PC나 독립 실행형 UWP 디바이스에서 HoloLens 2로 데이터를 스트리밍합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-114">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="0848b-115">원격 호스트 앱은 HoloLens로부터 입력 데이터 스트림을 받고 가상 몰입형 보기에서 콘텐츠를 렌더링하며 다시 Wi-Fi를 통해 콘텐츠 프레임을 HoloLens로 돌려 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-115">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="0848b-116">스트리밍을 통해 몰입형 보기를 기존 데스크톱 PC 소프트웨어에 추가할 수 있고 다른 시스템 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-116">Streaming lets you add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="0848b-117">체스 앱에 이 경로를 적용하려면 다음 몇 가지가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-117">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="0848b-118">Microsoft Store에서 HoloLens 2에 **홀로그램 원격 플레이어** 를 설치하고 앱을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-118">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="0848b-119">앱에 표시되는 IP 주소를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-119">Note your IP address displayed in the app.</span></span>
    * <span data-ttu-id="0848b-120">**편집 > 프로젝트 설정** 으로 차례로 이동하여 Windows **기본 RHI** 가 **기본값** 또는 **D3D11** 로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-120">Go to **Edit > Project Settings** and sure the Windows **Default RHI** is set to **Default** or **D3D11**:</span></span>

![기본 RHI](../images/unreal/performance-recommendations-img-09.png)

2.  <span data-ttu-id="0848b-122">Unreal 편집기로 돌아가서 **편집 > 프로젝트 설정** 으로 이동하고 **홀로그램 원격** 섹션에서 **원격 사용** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-122">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="0848b-123">편집기를 다시 시작한 다음, 디바이스 IP 주소(홀로그램 원격 플레이어 앱에 표시됨)를 입력한 다음, **연결** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-123">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="0848b-124">연결되면 **재생** 단추 오른쪽의 드롭다운 화살표를 클릭하여 **VR 미리 보기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-124">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="0848b-125">그러면 HoloLens 헤드셋으로 스트리밍되는 VR 미리 보기 창에 앱이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-125">The app will run in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="0848b-126">장치 포털을 통해 앱 패키징 및 배포</span><span class="sxs-lookup"><span data-stu-id="0848b-126">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="0848b-127">HoloLens용 Unreal 앱을 처음으로 패키징하는 경우 Epic Launcher에서 지원 파일을 다운로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-127">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="0848b-128">**편집기 기본 설정 > 일반 > 소스 코드 > 소스 코드 편집기** 로 이동하여 Visual Studio 2019가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-128">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="0848b-129">Epic Games 시작 관리자에서 **라이브러리** 탭으로 이동한 다음, **시작** 옆의 드롭다운 화살표를 선택하고 **옵션** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-129">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="0848b-130">**대상 플랫폼** 에서 **HoloLens 2** 를 선택하고 **적용** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-130">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="0848b-131">![프로젝트 설정에서 대상 플랫폼 변경](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="0848b-131">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="0848b-132">**편집 > 프로젝트 설정** 으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-132">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="0848b-133">**프로젝트 > 설명 > 정보 > 프로젝트 이름** 에서 프로젝트 이름을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-133">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="0848b-134">**프로젝트 > 설명 > 게시자 > 회사 고유 이름** 아래에서 **CN=YourCompanyName** 을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-134">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>
    * <span data-ttu-id="0848b-135">**프로젝트 > 설명 > 설정** 에서 **VR에서 시작** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-135">Select **Start in VR** under **Project > Description > Settings**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0848b-136">이러한 필드 중 하나를 비워 두면 3단계에서 새 인증서를 생성하려고 할 때 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-136">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0848b-137">게시자의 이름은 [LADPv3 고유 이름 형식](https://www.ietf.org/rfc/rfc2253.txt)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-137">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="0848b-138">패키지할 때 잘못된 형식의 게시자 이름으로 인해 "서명 키를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-138">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="0848b-139">앱에 디지털 서명할 수 없습니다."라는</span><span class="sxs-lookup"><span data-stu-id="0848b-139">The app could not be digitally signed."</span></span> <span data-ttu-id="0848b-140">오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-140">error upon packaging.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0848b-141">"VR에서 시작"을 선택하지 않으면 애플리케이션이 슬레이트에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-141">Not selecting "Start in VR" will lead your application trying to start in a slate</span></span>

![프로젝트 설정 - 설명](images/unreal-uxt/6-cn-new.PNG)

2.  <span data-ttu-id="0848b-143">**플랫폼 > HoloLens** 에서 **HoloLens 에뮬레이션에 대해 빌드** 및/또는 **HoloLens 디바이스에 대해 빌드** 를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-143">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="0848b-144">**서명 인증서** 옆의 **패키징** 섹션에서 **새로 생성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-144">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0848b-145">이미 생성된 인증서를 사용하는 경우 인증서의 게시자 이름은 애플리케이션의 게시자 이름과 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-145">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="0848b-146">그렇지 않으면 "서명 키를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-146">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="0848b-147">앱에 디지털 서명할 수 없습니다."라는</span><span class="sxs-lookup"><span data-stu-id="0848b-147">The app could not be digitally signed."</span></span> <span data-ttu-id="0848b-148">오류로 인해 path\filename 파일을 삭제하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-148">error.</span></span>

![프로젝트 설정 - 플랫폼 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="0848b-150">프라이빗 키 암호를 만들라는 메시지가 표시되면 테스트 목적으로 **없음** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-150">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![새 인증서 생성](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="0848b-152">**파일 > 패키지 프로젝트** 으로 이동하여 **HoloLens** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-152">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="0848b-153">새 폴더를 만들어 패키지를 저장하고 **폴더 선택** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-153">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="0848b-154">앱 패키징 후 [Windows 장치 포털](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)을 열고 **보기 > 앱** 으로 이동한 다음, **앱 배포** 섹션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-154">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="0848b-155">**찾아보기...** 를 클릭하고 **ChessApp.appxbundle** 파일로 이동한 다음, **열기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-155">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="0848b-156">처음 디바이스에 앱을 설치하는 경우 **프레임워크 패키지를 선택하도록 허용** 옆의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-156">Check the box next to **Allow me to select framework packages** if you're installing the app on your device for the first time.</span></span>
    * <span data-ttu-id="0848b-157">다음 대화 상자에서 적절한 **VCLibs** 및 **appx** 파일, 디바이스에 **arm64**, 에뮬레이터에 **x64** 를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-157">In the next dialogue, include the appropriate **VCLibs** and **appx** files, **arm64** for device and **x64** for emulator.</span></span> <span data-ttu-id="0848b-158">파일은 패키지를 저장한 폴더 안의 **HoloLens** 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-158">You can find the files under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="0848b-159">**설치** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-159">Click **Install**</span></span>
    * <span data-ttu-id="0848b-160">이제 **모든 앱** 으로 이동하고 새로 설치된 앱을 탭하여 실행하거나 **Windows Device Portal** 에서 직접 앱을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-160">You can now go to **All Apps** and tap the newly installed app to run it, or start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="0848b-161">축하합니다!</span><span class="sxs-lookup"><span data-stu-id="0848b-161">Congratulations!</span></span> <span data-ttu-id="0848b-162">HoloLens 혼합 현실 애플리케이션이 완료되어 진행할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-162">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="0848b-163">하지만 이것이 전부는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-163">However, you're not at the end of the road.</span></span> <span data-ttu-id="0848b-164">MRTK에는 공간 매핑, 응시, 음성 입력을 비롯하여 QR 코드에 이르기까지, 프로젝트에 추가할 수 있는 무수한 독립 실행형 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-164">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="0848b-165">이러한 기능에 대한 자세한 내용은 [Unreal 개발 개요](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-165">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="0848b-166">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="0848b-166">Next Development Checkpoint</span></span>

<span data-ttu-id="0848b-167">앞에서 설명한 Unreal 개발 과정을 따르고 있다면 현재 MRTK 핵심 구성 요소를 살펴보는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-167">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="0848b-168">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-168">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0848b-169">응시 입력</span><span class="sxs-lookup"><span data-stu-id="0848b-169">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="0848b-170">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-170">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0848b-171">HoloLens 카메라</span><span class="sxs-lookup"><span data-stu-id="0848b-171">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="0848b-172">언제든지 [Unreal 개발 검사점](../unreal-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0848b-172">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
