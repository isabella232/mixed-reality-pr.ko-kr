---
title: Visual Studio를 사용하여 배포 및 디버깅
description: Visual Studio를 사용하여 HoloLens 및 Windows Mixed Reality용 앱을 빌드, 디버그 및 배포하는 방법을 알아봅니다.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, Mixed Reality, 디버그, 배포
ms.openlocfilehash: 2ab89311163a48ee3c14511446a1498ce883a232
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496098"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="0e55e-104">Visual Studio를 사용하여 배포 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="0e55e-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="0e55e-105">혼합 현실 앱을 개발할 때 DirectX와 Unity 중 무엇을 사용하든 관계없이 Visual Studio는 디버깅 및 배포에 적합한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="0e55e-106">이 섹션에서는 다음을 수행하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="0e55e-107">Visual Studio를 통해 애플리케이션을 HoloLens 또는 Windows Mixed Reality 몰입형 헤드셋에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="0e55e-108">Visual Studio에 기본 제공된 HoloLens 에뮬레이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="0e55e-109">혼합 현실 앱을 디버그합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0e55e-110">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0e55e-110">Prerequisites</span></span>

1. <span data-ttu-id="0e55e-111">설치 지침은 [도구 설치](../../develop/install-the-tools.md#installation-checklist)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e55e-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="0e55e-112">Visual Studio에서 새 유니버설 Windows 앱 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="0e55e-113">HoloLens(1세대)의 경우 Visual Studio 2017 이상을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="0e55e-114">HoloLens 2의 경우 Visual Studio 2019 16.2 이상을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="0e55e-115">C# 및 C++가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-115">C# and C++ are supported.</span></span> <span data-ttu-id="0e55e-116">(또는 지침에 따라 [Unity에서 앱을 만듭니다](../../develop/unity/tutorials/holograms-100.md).)</span><span class="sxs-lookup"><span data-stu-id="0e55e-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="0e55e-117">개발자 모드 사용</span><span class="sxs-lookup"><span data-stu-id="0e55e-117">Enabling Developer Mode</span></span>

<span data-ttu-id="0e55e-118">먼저 디바이스에서 **개발자 모드** 를 사용하도록 설정합니다. 그러면 Visual Studio에서 해당 디바이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="0e55e-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="0e55e-119">HoloLens</span></span>

1. <span data-ttu-id="0e55e-120">HoloLens를 켜고 디바이스에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="0e55e-121">[시작 제스처](../../design/system-gesture.md)를 사용하여 주 메뉴를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="0e55e-122">**설정** 타일을 선택하여 환경에서 앱을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="0e55e-123">**업데이트** 메뉴 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="0e55e-124">**개발자용** 메뉴 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="0e55e-125">**개발자 모드** 를 사용하여 Visual Studio에서 HoloLens로 앱을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-125">Enable **Developer Mode** to deploy apps from Visual Studio to your HoloLens.</span></span>
7. <span data-ttu-id="0e55e-126">옵션: 아래로 스크롤하고 **장치 포털** 도 사용하도록 설정하면 웹 브라우저에서 HoloLens의 [Windows 장치 포털](using-the-windows-device-portal.md)에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-126">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="0e55e-127">Windows PC</span><span class="sxs-lookup"><span data-stu-id="0e55e-127">Windows PC</span></span>

<span data-ttu-id="0e55e-128">PC에 연결된 Windows Mixed Reality 헤드셋을 사용하는 경우 PC에서 **개발자 모드** 를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-128">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="0e55e-129">**설정** 으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-129">Go to **Settings**</span></span>
2. <span data-ttu-id="0e55e-130">**업데이트 및 보안** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-130">Select **Update and Security**</span></span>
3. <span data-ttu-id="0e55e-131">**개발자용** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-131">Select **For developers**</span></span>
4. <span data-ttu-id="0e55e-132">**개발자 모드** 를 사용하도록 설정하고, 선택한 설정에 대한 고지 사항을 읽은 다음, 예를 선택하여 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-132">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="0e55e-133">Wi-Fi를 통해 HoloLens 앱 배포</span><span class="sxs-lookup"><span data-stu-id="0e55e-133">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="0e55e-134">다음 속성을 사용하여 Visual Studio 프로젝트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-134">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="0e55e-135">앱 컴파일 옵션 선택</span><span class="sxs-lookup"><span data-stu-id="0e55e-135">Select your apps compilation options</span></span>
    * <span data-ttu-id="0e55e-136">Unity 프로젝트의 경우 **릴리스** 또는 **마스터** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-136">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="0e55e-137">다른 모든 프로젝트의 경우 **릴리스** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-137">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="0e55e-138">[Visual Studio 솔루션 내보내기 및 빌드](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)에서 각 컴파일 옵션에 대한 완전한 정의를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-138">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="0e55e-139">디바이스에 따라 빌드 구성 선택</span><span class="sxs-lookup"><span data-stu-id="0e55e-139">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="0e55e-140">배포 대상 드롭다운 메뉴에서 **원격 머신** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-140">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Visual Studio의 원격 머신 배포 대상](images/remotemachinesetting_arm64.png)

<span data-ttu-id="0e55e-142">다음으로 원격 연결을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-142">Next, you need to set your remote connection.</span></span> <span data-ttu-id="0e55e-143">C++ 및 JavaScript 프로젝트의 경우 **프로젝트 > 속성 > 구성 속성 > 디버깅** 으로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-143">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="0e55e-144">C# 프로젝트에서 작업하는 경우 대화 상자가 자동으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-144">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="0e55e-145">원격 연결 대화 상자가 C# 프로젝트에 나타나지 않으면 **속성 > 디버그** 에서 수동으로 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-145">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="0e55e-146">**주소** 또는 **머신 이름** 필드에서 디바이스의 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-146">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="0e55e-147">**설정 > 네트워크 및 인터넷 > 고급 옵션** 아래에서 HoloLens의 IP 주소를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-147">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="0e55e-148">자동 감지 기능에 의존하지 않고 항상 수동으로 IP 주소를 입력하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-148">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="0e55e-149">**인증 모드** 를 **유니버설(암호화되지 않은 프로토콜)** 로 설정</span><span class="sxs-lookup"><span data-stu-id="0e55e-149">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Visual Studio의 원격 연결 대화 상자](images/remotedeploy.png)

3. <span data-ttu-id="0e55e-151">필요에 따라 앱 빌드, 배포 및 디버그</span><span class="sxs-lookup"><span data-stu-id="0e55e-151">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="0e55e-152">**디버그 > 디버깅 시작** 을 차례로 선택하여 앱을 배포하고, 디버깅을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-152">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="0e55e-153">**빌드 > 배포** 를 선택하여 디버깅하지 않고 빌드 및 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-153">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Visual Studio에서 디버깅 없이 시작](images/deploywithdebugging.png)

4. <span data-ttu-id="0e55e-155">PC에서 앱을 HoloLens에 처음 배포하는 경우 PIN을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-155">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="0e55e-156">아래의 **디바이스 페어링** 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-156">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="0e55e-157">USB를 통해 HoloLens 앱 배포</span><span class="sxs-lookup"><span data-stu-id="0e55e-157">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="0e55e-158">앱 컴파일 옵션 선택</span><span class="sxs-lookup"><span data-stu-id="0e55e-158">Select your apps compilation options</span></span>
    * <span data-ttu-id="0e55e-159">Unity 프로젝트의 경우 **릴리스** 또는 **마스터** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-159">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="0e55e-160">다른 모든 프로젝트의 경우 **릴리스** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-160">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="0e55e-161">[Visual Studio 솔루션 내보내기 및 빌드](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)에서 각 컴파일 옵션에 대한 완전한 정의를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-161">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="0e55e-162">디바이스에 따라 빌드 구성 선택</span><span class="sxs-lookup"><span data-stu-id="0e55e-162">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="0e55e-163">배포 대상 드롭다운 메뉴에서 **디바이스** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-163">Select **Device** in the deployment target drop-down menu</span></span>

![Visual Studio에서 디바이스 배포](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="0e55e-165">필요에 따라 앱 빌드, 배포 및 디버그</span><span class="sxs-lookup"><span data-stu-id="0e55e-165">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="0e55e-166">**디버그 > 디버깅 시작** 을 선택하여 앱을 배포하고 디버깅을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-166">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="0e55e-167">**빌드 > 배포** 를 선택하여 디버깅하지 않고 빌드 및 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-167">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Visual Studio에서 디버깅 없이 시작](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="0e55e-169">PC에서 앱을 HoloLens에 처음 배포하는 경우 PIN을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-169">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="0e55e-170">아래의 **디바이스 페어링** 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-170">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="0e55e-171">USB를 통한 앱 배포에 상당한 지연 시간이 발생하는 경우 이전 섹션의 [원격 머신 지침](#deploying-a-hololens-app-over-wi-fi)를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-171">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="0e55e-172">HoloLens 에뮬레이터에 앱 배포</span><span class="sxs-lookup"><span data-stu-id="0e55e-172">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="0e55e-173">**[HoloLens 2 또는 HoloLens(1세대) 에뮬레이터를 설치](../install-the-tools.md#installation-checklist)** 했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-173">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="0e55e-174">디바이스에 따라 빌드 구성 및 에뮬레이터 선택</span><span class="sxs-lookup"><span data-stu-id="0e55e-174">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="0e55e-175">필요에 따라 앱 빌드, 배포 및 디버그</span><span class="sxs-lookup"><span data-stu-id="0e55e-175">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="0e55e-176">**디버그 > 디버깅 시작** 을 선택하여 앱을 배포하고 디버깅을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-176">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="0e55e-177">**빌드 > 배포** 를 선택하여 디버깅하지 않고 빌드 및 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-177">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![Visual Studio에서 디버깅 없이 시작](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="0e55e-179">로컬 PC에 VR 앱 배포</span><span class="sxs-lookup"><span data-stu-id="0e55e-179">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="0e55e-180">PC 또는 [Mixed Reality 시뮬레이터](using-the-windows-mixed-reality-simulator.md)에 연결되는 Windows Mixed Reality 몰입형 헤드셋을 사용하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-180">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="0e55e-181">앱에 대해 **x86** 또는 **x64** 빌드 구성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-181">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="0e55e-182">배포 대상 드롭다운 메뉴에서 **로컬 머신** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-182">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="0e55e-183">필요에 따라 앱 빌드, 배포 및 디버그</span><span class="sxs-lookup"><span data-stu-id="0e55e-183">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="0e55e-184">**디버그 > 디버깅 시작** 을 차례로 선택하여 앱을 배포하고, 디버깅을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-184">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="0e55e-185">**빌드 > 배포** 를 선택하여 디버깅하지 않고 빌드 및 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-185">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="0e55e-186">디바이스 페어링</span><span class="sxs-lookup"><span data-stu-id="0e55e-186">Pairing your device</span></span>

<span data-ttu-id="0e55e-187">앱을 Visual Studio에서 HoloLens로 처음 배포하는 경우 PIN을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-187">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="0e55e-188">HoloLens에서 설정 앱을 실행하여 PIN을 생성하고, **업데이트 > 개발자용** 으로 차례로 이동하여 **페어링** 을 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-188">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="0e55e-189">HoloLens에 표시되는 PIN을 Visual Studio에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-189">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="0e55e-190">페어링이 완료되면 HoloLens에서 **완료** 를 탭하여 대화 상자를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-190">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="0e55e-191">이 PC는 이제 HoloLens와 페어링되어 앱을 자동으로 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-191">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="0e55e-192">앱을 HoloLens에 배포하는 데 사용되는 모든 PC에 대해 이러한 단계를 반복하세요.</span><span class="sxs-lookup"><span data-stu-id="0e55e-192">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="0e55e-193">페어링된 모든 컴퓨터에서 HoloLens를 언페어링하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-193">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="0e55e-194">**설정** 앱을 시작하고, **업데이트 > 개발자용** 으로 이동하고, **지우기** 를 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-194">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="0e55e-195">HoloLens(1세대)용 그래픽 디버거</span><span class="sxs-lookup"><span data-stu-id="0e55e-195">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="0e55e-196">Visual Studio 그래픽 진단 도구는 홀로그램 앱을 작성하고 최적화하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-196">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="0e55e-197">자세한 내용은 [MSDN의 Visual Studio 그래픽 진단](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e55e-197">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="0e55e-198">**그래픽 디버거를 시작하려면**</span><span class="sxs-lookup"><span data-stu-id="0e55e-198">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="0e55e-199">위의 지침에 따라 디바이스 또는 에뮬레이터를 대상으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-199">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="0e55e-200">**디버그 > 그래픽 > 진단 시작** 으로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-200">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="0e55e-201">HoloLens를 사용하여 진단을 처음 시작하는 경우 "액세스 거부" 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-201">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="0e55e-202">업데이트된 권한이 적용되도록 HoloLens를 다시 부팅하여 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="0e55e-202">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="0e55e-203">프로파일링</span><span class="sxs-lookup"><span data-stu-id="0e55e-203">Profiling</span></span>

<span data-ttu-id="0e55e-204">Visual Studio 프로파일링 도구를 사용하면 앱의 성능 및 리소스 사용을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-204">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="0e55e-205">여기에는 CPU, 메모리, 그래픽 및 네트워크 사용을 최적화하는 도구가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-205">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="0e55e-206">자세한 내용은 [MSDN의 디버깅하지 않고 진단 도구 실행](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e55e-206">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="0e55e-207">**HoloLens를 사용하여 프로파일링 도구를 시작하려면**</span><span class="sxs-lookup"><span data-stu-id="0e55e-207">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="0e55e-208">위의 지침에 따라 디바이스 또는 에뮬레이터를 대상으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-208">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="0e55e-209">**디버그 > 디버깅하지 않고 진단 도구 시작...** 으로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-209">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="0e55e-210">사용하려는 도구를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-210">Select the tools you want to use</span></span>
4. <span data-ttu-id="0e55e-211">**시작** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-211">Select **Start**</span></span>
5. <span data-ttu-id="0e55e-212">HoloLens를 사용하여 디버그 없이 진단을 처음 시작하는 경우 "액세스 거부" 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-212">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="0e55e-213">업데이트된 권한이 적용되도록 HoloLens를 다시 부팅하여 다시 시도하세요.</span><span class="sxs-lookup"><span data-stu-id="0e55e-213">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="0e55e-214">설치되었거나 실행 중인 앱 디버깅</span><span class="sxs-lookup"><span data-stu-id="0e55e-214">Debugging an installed or running app</span></span>

<span data-ttu-id="0e55e-215">Visual Studio를 사용하여 Visual Studio 프로젝트에서 배포하지 않고 설치된 유니버설 Windows 앱을 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-215">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="0e55e-216">이는 설치된 앱 패키지를 디버그하거나 이미 실행 중인 앱을 디버그하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-216">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="0e55e-217">**디버그 -> 기타 디버그 대상 -> 설치된 앱 패키지 디버그** 로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-217">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="0e55e-218">HoloLens의 경우 **원격 머신** 대상을 선택하고, 몰입형 헤드셋의 경우 **로컬 머신** 대상을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-218">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="0e55e-219">디바이스의 **IP 주소** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-219">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="0e55e-220">**유니버설** 인증 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-220">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="0e55e-221">창에 실행 중인 앱과 비활성 앱이 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-221">The window shows both running and inactive apps.</span></span> <span data-ttu-id="0e55e-222">디버그하려는 앱을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-222">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="0e55e-223">디버그할 코드 형식(관리, 네이티브, 혼합)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-223">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="0e55e-224">**연결** 또는 **시작** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-224">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="0e55e-225">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="0e55e-225">Next Development Checkpoint</span></span>

<span data-ttu-id="0e55e-226">앞에서 설명한 Unity 개발 검사점 경험을 수행하는 경우 배포 단계를 진행하고 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-226">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="0e55e-227">여기에서 다음 항목으로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-227">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e55e-228">HoloLens 에뮬레이터에 배포</span><span class="sxs-lookup"><span data-stu-id="0e55e-228">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="0e55e-229">또는 고급 서비스 추가로 바로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-229">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e55e-230">고급 서비스</span><span class="sxs-lookup"><span data-stu-id="0e55e-230">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="0e55e-231">언제든지 [Unity 개발 검사점](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e55e-231">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e55e-232">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e55e-232">See also</span></span>
* [<span data-ttu-id="0e55e-233">도구 설치</span><span class="sxs-lookup"><span data-stu-id="0e55e-233">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="0e55e-234">HoloLens 에뮬레이터 사용</span><span class="sxs-lookup"><span data-stu-id="0e55e-234">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="0e55e-235">UWP(유니버설 Windows 플랫폼) 앱 배포 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="0e55e-235">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="0e55e-236">디바이스를 개발에 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="0e55e-236">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)