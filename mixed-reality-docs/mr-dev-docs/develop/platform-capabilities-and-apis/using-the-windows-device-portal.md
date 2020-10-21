---
title: Windows 장치 포털 사용
description: HoloLens용 Windows 장치 포털을 사용하면 Wi-Fi 또는 USB를 통해 원격으로 디바이스를 구성하고 관리할 수 있습니다. Device Portal은 PC의 웹 브라우저에서 연결 가능한 HoloLens에 있는 웹 서버입니다. 장치 포털에는 HoloLens를 관리하고 앱을 디버깅 및 최적화하는 데 도움이 되는 많은 도구가 포함되어 있습니다.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Windows 장치 포털, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 98030e55736d423d1fb84d2b965f6ed40246d8f4
ms.sourcegitcommit: 9c88703a832fb8ca8476e808499d06239ea5d2cd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92011484"
---
# <a name="using-the-windows-device-portal"></a><span data-ttu-id="372ca-106">Windows 장치 포털 사용</span><span class="sxs-lookup"><span data-stu-id="372ca-106">Using the Windows Device Portal</span></span>

<table>
<tr>
<th><span data-ttu-id="372ca-107">기능</span><span class="sxs-lookup"><span data-stu-id="372ca-107">Feature</span></span></th><th style="width:150px"><span data-ttu-id="372ca-108"><a href="../../hololens-hardware-details.md">HoloLens(1세대)</a></span><span class="sxs-lookup"><span data-stu-id="372ca-108"><a href="../../hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="372ca-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="372ca-109">HoloLens 2</span></span></th><th style="width:150px">
</tr><tr>
<td> <span data-ttu-id="372ca-110">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="372ca-110">Windows Device Portal</span></span></td><td style="text-align: center;"> <span data-ttu-id="372ca-111">✔️</span><span class="sxs-lookup"><span data-stu-id="372ca-111">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="372ca-112">✔️</span><span class="sxs-lookup"><span data-stu-id="372ca-112">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

<span data-ttu-id="372ca-113">HoloLens용 Windows 장치 포털을 사용하면 Wi-Fi 또는 USB를 통해 원격으로 디바이스를 구성하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-113">The Windows Device Portal for HoloLens lets you configure and manage your device remotely over Wi-Fi or USB.</span></span> <span data-ttu-id="372ca-114">Device Portal은 PC의 웹 브라우저에서 연결 가능한 HoloLens에 있는 웹 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-114">The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.</span></span> <span data-ttu-id="372ca-115">장치 포털에는 HoloLens를 관리하고 앱을 디버깅 및 최적화하는 데 도움이 되는 많은 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-115">The Device Portal includes many tools that will help you manage your HoloLens and debug and optimize your apps.</span></span>

<span data-ttu-id="372ca-116">이 설명서에서는 HoloLens용 Windows 장치 포털을 중점적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-116">This documentation is specifically about the Windows Device Portal for HoloLens.</span></span> <span data-ttu-id="372ca-117">Windows Mixed Reality를 포함한 데스크톱용 Windows 장치 포털을 사용하려면 [Windows 장치 포털 개요](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="372ca-117">To use the Windows Device portal for desktop (including for Windows Mixed Reality), see [Windows Device Portal overview](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

## <a name="setting-up-hololens-to-use-windows-device-portal"></a><span data-ttu-id="372ca-118">Windows 장치 포털을 사용하도록 HoloLens 설정</span><span class="sxs-lookup"><span data-stu-id="372ca-118">Setting up HoloLens to use Windows Device Portal</span></span>

1. <span data-ttu-id="372ca-119">HoloLens의 전원을 켜고 디바이스에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-119">Power on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="372ca-120">[시작 제스처](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture)(HoloLens 2) 또는 [블룸](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)(HoloLens 1세대)으로 주 메뉴를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-120">Perform the [Start gesture](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) for HoloLens2 or [Bloom](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) on HoloLens (1st Gen) to launch the main menu.</span></span> 
3. <span data-ttu-id="372ca-121">**설정** 타일을 응시하고 HoloLens 1세대에서 [에어 탭](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) 제스처를 수행하거나 HoloLens 2에서 [터치하거나 손 광선을 사용](https://docs.microsoft.com/hololens/hololens2-basic-usage)하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-121">Gaze at the **Settings** tile and perform the [air-tap](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) gesture on HoloLens (1st Gen) or select it on HoloLens 2 by [touching it or using a Hand ray](https://docs.microsoft.com/hololens/hololens2-basic-usage).</span></span> 
4. <span data-ttu-id="372ca-122">**업데이트** 메뉴 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-122">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="372ca-123">**개발자용** 메뉴 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-123">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="372ca-124">**개발자 모드**를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-124">Enable **Developer Mode**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="372ca-125">관리자가 아닌 다중 사용자인 경우 개발자 모드를 시작할 수 있는 기능이 회색으로 표시될 수 있습니다. **[디바이스에 대한 관리자](https://docs.microsoft.com/hololens/security-adminless-os)** 인지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="372ca-125">If you're in multi-user and not an admin, the ability to enter Developer Mode may be grayed out. Please ensure that you are an **[admin on the device](https://docs.microsoft.com/hololens/security-adminless-os)**.</span></span>

7. <span data-ttu-id="372ca-126">[아래로 스크롤](../../design/gaze-and-commit.md#composite-gestures)하여 **장치 포털**을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-126">[Scroll down](../../design/gaze-and-commit.md#composite-gestures) and enable **Device Portal**.</span></span>
8. <span data-ttu-id="372ca-127">USB 또는 Wi-Fi를 통해 이 HoloLens에 앱을 배포할 수 있도록 Windows 장치 포털을 설정하려면 **연결**을 클릭하여 [연결 PIN을 생성](using-visual-studio.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-127">If you are setting up Windows Device Portal so you can deploy apps to this HoloLens over USB or Wi-Fi, click **Pair** to [generate a pairing PIN](using-visual-studio.md).</span></span> <span data-ttu-id="372ca-128">첫 번째 배포 시에는 Visual Studio에 PIN을 입력할 때까지 PIN 팝업에서 설정 앱을 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-128">Leave the Settings app at the PIN popup until you enter the PIN into Visual Studio during your first deployment.</span></span>

![Windows Holographic 설정 앱에서 개발자 모드 사용](images/using-windows-portal-img-01.jpg)

## <a name="connecting-over-wi-fi"></a><span data-ttu-id="372ca-130">Wi-Fi를 통한 연결</span><span class="sxs-lookup"><span data-stu-id="372ca-130">Connecting over Wi-Fi</span></span>

1. <span data-ttu-id="372ca-131">[HoloLens를 Wi-Fi에 연결합니다](../../connecting-to-wi-fi-on-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="372ca-131">[Connect your HoloLens to Wi-Fi](../../connecting-to-wi-fi-on-hololens.md).</span></span>
2. <span data-ttu-id="372ca-132">다음 중 하나를 수행하여 디바이스의 IP 주소를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-132">Look up your device's IP address by either:</span></span>
   * <span data-ttu-id="372ca-133">**설정 > 네트워크 및 인터넷 > Wi-Fi > 고급 옵션**으로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-133">Going to **Settings > Network & Internet > Wi-Fi > Advanced Options**.</span></span>
   * <span data-ttu-id="372ca-134">**설정 > 네트워크 및 인터넷**으로 차례로 이동하고, **하드웨어 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-134">Going to **Settings > Network & Internet** and selecting **Hardware properties**.</span></span>

![HoloLens 2 설정](images/using-windows-portal-img-02.jpg)

3. <span data-ttu-id="372ca-136">PC의 웹 브라우저에서 https://<YOUR_HOLOLENS_IP_ADDRESS>로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-136">From a web browser on your PC, go to https://<YOUR_HOLOLENS_IP_ADDRESS></span></span>
   * <span data-ttu-id="372ca-137">브라우저에 다음 메시지가 표시됩니다. "이 웹 사이트의 보안 인증서에 문제가 있습니다."</span><span class="sxs-lookup"><span data-stu-id="372ca-137">The browser will display the following message: "There's a problem with this website's security certificate".</span></span> <span data-ttu-id="372ca-138">이 오류는 디바이스 포털에 발행된 인증서가 테스트 인증서이기 때문에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-138">This happens because the certificate which is issued to the Device Portal is a test certificate.</span></span> <span data-ttu-id="372ca-139">지금은 이 인증서 오류를 무시하고 계속 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-139">You can ignore this certificate error for now and proceed.</span></span>

## <a name="connecting-over-usb"></a><span data-ttu-id="372ca-140">USB를 통한 연결</span><span class="sxs-lookup"><span data-stu-id="372ca-140">Connecting over USB</span></span>

1. <span data-ttu-id="372ca-141">[도구](../install-the-tools.md)를 설치하여 USB 연결을 사용하도록 설정하기 위해 Windows 10 개발자 도구가 설치된 Visual Studio가 PC에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-141">[Install the tools](../install-the-tools.md) to make sure you have Visual Studio with the Windows 10 developer tools installed on your PC to enable USB connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="372ca-142">USB 연결과 관련된 문제가 있으면 USB 디바이스 연결 선택적 구성 요소가 **[Visual Studio 도구 패키지](../install-the-tools.md#installation-checklist)** 의 일부로 설치되어 있는지 다시 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="372ca-142">If you're having issues with USB connectivity double check that the USB Device Connectivity optional component is installed as part of your **[Visual Studio tool package](../install-the-tools.md#installation-checklist)**.</span></span>

2. <span data-ttu-id="372ca-143">마이크로 USB 케이블(HoloLens 1세대) 또는 USB-C(HoloLens 2)를 사용하여 HoloLens를 PC에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-143">Connect your HoloLens to your PC with a micro-USB cable for HoloLens (1st Gen) or USB-C for HoloLens 2.</span></span>
3. <span data-ttu-id="372ca-144">PC의 웹 브라우저에서 [https://127.0.0.1:10080](https://127.0.0.1:10080)으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-144">From a web browser on your PC, go to [https://127.0.0.1:10080](https://127.0.0.1:10080).</span></span>

### <a name="moving-files-over-usb"></a><span data-ttu-id="372ca-145">USB를 통해 파일 이동</span><span class="sxs-lookup"><span data-stu-id="372ca-145">Moving files over USB</span></span>

<span data-ttu-id="372ca-146">추가 설정 없이 파일을 PC에서 HoloLens로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-146">You can move files from your PC to your HoloLens without any additional setup.</span></span>
1. <span data-ttu-id="372ca-147">USB 코드를 사용하여 PC를 HoloLens에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-147">Connect your PC to your HoloLens with a USB cord</span></span>
2. <span data-ttu-id="372ca-148">데스크톱에서 파일을 **PC\\[Your_HoloLens_Device_Name]\Internal Storage**로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-148">Drag your files into **PC\\[Your_HoloLens_Device_Name]\Internal Storage** on your desktop</span></span>
3. <span data-ttu-id="372ca-149">**시작 메뉴**를 열고, HoloLens에서 **모든 앱 > 파일 탐색기**를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-149">Open the **Start Menu** and select **All apps > File Explorer** on your HoloLens</span></span>

> [!NOTE]
> <span data-ttu-id="372ca-150">"최근에 사용한 파일"에서 벗어나서 파일을 찾으려면 패널 왼쪽에서 **이 디바이스**를 선택해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-150">You may need to select **This device** on the left side of the panel to navigate away from "Recently used" to locate your files.</span></span> 

## <a name="connecting-to-an-emulator"></a><span data-ttu-id="372ca-151">에뮬레이터에 연결</span><span class="sxs-lookup"><span data-stu-id="372ca-151">Connecting to an emulator</span></span>

<span data-ttu-id="372ca-152">에뮬레이터로 디바이스 포털을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-152">You can also use the Device Portal with your emulator.</span></span> <span data-ttu-id="372ca-153">장치 포털에 연결하려면 [도구 모음](using-the-hololens-emulator.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-153">To connect to the Device Portal, use the [toolbar](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="372ca-154">다음 아이콘을 클릭합니다. ![장치 포털 열기 아이콘](images/emulator-deviceportal.png) **장치 포털 열기**: 에뮬레이터에서 HoloLens OS용 Windows 디바이스 포털을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-154">Click on this icon: ![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

## <a name="creating-a-username-and-password"></a><span data-ttu-id="372ca-155">사용자 이름 및 암호 만들기</span><span class="sxs-lookup"><span data-stu-id="372ca-155">Creating a Username and Password</span></span>

<span data-ttu-id="372ca-156">![Windows 장치 포털에 대한 액세스 설정](images/windows-device-portal-credentials-reset-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-156">![Set up access to Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)</span></span><br>
<span data-ttu-id="372ca-157">*Windows 장치 포털에 대한 액세스 설정*</span><span class="sxs-lookup"><span data-stu-id="372ca-157">*Set up access to Windows Device Portal*</span></span>

<span data-ttu-id="372ca-158">HoloLens에서 디바이스 포털에 처음 연결하면 사용자 이름 및 암호를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-158">The first time you connect to the Device Portal on your HoloLens, you will need to create a username and password.</span></span>
1. <span data-ttu-id="372ca-159">PC의 웹 브라우저에서 HoloLens의 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-159">In a web browser on your PC, enter the IP address of the HoloLens.</span></span> <span data-ttu-id="372ca-160">액세스 설정 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-160">The Set up access page opens.</span></span>
2. <span data-ttu-id="372ca-161">**PIN 요청**을 클릭 또는 탭하고 HoloLens 디스플레이를 확인하여 생성된 PIN을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-161">Click or tap **Request pin** and look at the HoloLens display to get the generated PIN.</span></span>
3. <span data-ttu-id="372ca-162">**디바이스에 표시된 PIN** 텍스트 상자에 PIN을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-162">Enter the PIN in the **PIN displayed on your device** textbox.</span></span>
4. <span data-ttu-id="372ca-163">디바이스 포털 연결에 사용할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-163">Enter the user name you will use to connect to the Device Portal.</span></span> <span data-ttu-id="372ca-164">MSA(Microsoft 계정) 이름 또는 도메인 이름일 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-164">It doesn't need to be a Microsoft Account (MSA) name or a domain name.</span></span>
5. <span data-ttu-id="372ca-165">암호를 입력하고 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-165">Enter a password and confirm it.</span></span> <span data-ttu-id="372ca-166">암호는 7자 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-166">The password must be at least seven characters in length.</span></span> <span data-ttu-id="372ca-167">MSA 또는 도메인 암호일 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-167">It doesn't need to be an MSA or domain password.</span></span>
6. <span data-ttu-id="372ca-168">**연결**을 클릭하여 HoloLens의 Windows 장치 포털에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-168">Click **Pair** to connect to Windows Device Portal on the HoloLens.</span></span>

<span data-ttu-id="372ca-169">이 사용자 이름 또는 암호를 변경하려는 경우 언제든지 https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm으로 이동하여 디바이스 보안 페이지를 방문하면 이 프로세스를 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-169">If you wish to change this username or password at any time, you can repeat this process by visiting the device security page by  navigating to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.</span></span>

## <a name="security-certificate"></a><span data-ttu-id="372ca-170">보안 인증서</span><span class="sxs-lookup"><span data-stu-id="372ca-170">Security certificate</span></span>

<span data-ttu-id="372ca-171">브라우저에 "인증서 오류"가 표시되는 경우 디바이스와 트러스트 관계를 만들어 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-171">If you see a "certificate error" in your browser, you can fix it by creating a trust relationship with the device.</span></span>

<span data-ttu-id="372ca-172">각 HoloLens는 해당 SSL 연결에 대한 고유의 자체 서명된 인증서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-172">Each HoloLens generates a unique self-signed certificate for its SSL connection.</span></span> <span data-ttu-id="372ca-173">기본적으로 이 인증서는 PC의 웹 브라우저에서 신뢰하지 않아 "인증서 오류"가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-173">By default, this certificate is not trusted by your PC's web browser and you may get a "certificate error".</span></span> <span data-ttu-id="372ca-174">신뢰하는 Wi-Fi 네트워크 또는 USB를 통해 HoloLens에서 이 인증서를 다운로드하고 PC에서 신뢰할 수 있도록 만들어 안전하게 디바이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-174">By downloading this certificate from your HoloLens (over USB or a Wi-Fi network you trust) and trusting it on your PC, you can securely connect to your device.</span></span>
1. <span data-ttu-id="372ca-175">**보안된 네트워크(신뢰하는 Wi-Fi 네트워크 또는 USB)에 있는지 확인합니다.**</span><span class="sxs-lookup"><span data-stu-id="372ca-175">**Make sure you are on a secure network (USB or a Wi-Fi network you trust).**</span></span>
2. <span data-ttu-id="372ca-176">장치 포털의 "보안" 페이지에서 이 디바이스의 인증서를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-176">Download this device's certificate from the "Security" page on the Device Portal.</span></span>
   * <span data-ttu-id="372ca-177">https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-177">Navigate to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span></span>
   * <span data-ttu-id="372ca-178">시스템 > 기본 설정에 대한 노드를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-178">Open the node for System > Preferences.</span></span> 
   * <span data-ttu-id="372ca-179">"디바이스 보안"이 나올 때까지 아래로 스크롤하고 "이 디바이스의 인증서 다운로드" 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-179">Scroll down to Device Security, click the "Download this device's certificate" button.</span></span>
3. <span data-ttu-id="372ca-180">PC의 "신뢰할 수 있는 루트 인증 기관" 저장소에 인증서를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-180">Install the certificate in the "Trusted Root Certification Authorities" store on your PC.</span></span>
   * <span data-ttu-id="372ca-181">Windows 메뉴에서 컴퓨터 인증서 관리를 입력하고 애플릿을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-181">From the Windows menu, type: Manage Computer Certificates and start the applet.</span></span>
   * <span data-ttu-id="372ca-182">**신뢰할 수 있는 루트 인증 기관** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-182">Expand the **Trusted Root Certification Authority** folder.</span></span>
   * <span data-ttu-id="372ca-183">**인증서** 폴더를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-183">Click the **Certificates** folder.</span></span>
   * <span data-ttu-id="372ca-184">작업 메뉴에서 모든 작업 > 가져오기...를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-184">From the Action menu, select: All Tasks > Import...</span></span>
   * <span data-ttu-id="372ca-185">디바이스 포털에서 다운로드한 인증서 파일을 사용하여 인증서 가져오기 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-185">Complete the Certificate Import Wizard, using the certificate file you downloaded from the Device Portal.</span></span>
4. <span data-ttu-id="372ca-186">브라우저를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-186">Restart the browser.</span></span>

>[!NOTE]
> <span data-ttu-id="372ca-187">이 인증서는 디바이스에서만 신뢰할 수 있으며, 디바이스가 플래시되면 사용자가 프로세스를 다시 진행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-187">This certificate will only be trusted for the device and the user will have to go through the process again if the device is flashed.</span></span>


## <a name="device-portal-pages"></a><span data-ttu-id="372ca-188">디바이스 포털 페이지</span><span class="sxs-lookup"><span data-stu-id="372ca-188">Device Portal Pages</span></span>

### <a name="home"></a><span data-ttu-id="372ca-189">홈</span><span class="sxs-lookup"><span data-stu-id="372ca-189">Home</span></span>

<span data-ttu-id="372ca-190">![Microsoft HoloLens에 대한 Windows 장치 포털의 홈 페이지](images/using-windows-portal-img-04.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-190">![Windows Device Portal home page on Microsoft HoloLens](images/using-windows-portal-img-04.png)</span></span><br>
<span data-ttu-id="372ca-191">*Microsoft HoloLens에 대한 Windows 장치 포털의 홈 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-191">*Windows Device Portal home page on Microsoft HoloLens*</span></span>

<span data-ttu-id="372ca-192">홈페이지에서 디바이스 포털 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-192">Your Device Portal session starts at the Home page.</span></span> <span data-ttu-id="372ca-193">홈페이지의 왼쪽 탐색 모음에서 다른 페이지에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-193">Access other pages from the navigation bar along the left side of the home page.</span></span>

<span data-ttu-id="372ca-194">페이지 맨 위에 있는 도구 모음에서 자주 사용하는 상태 및 기능에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-194">The toolbar at the top of the page provides access to commonly used status and features.</span></span>
* <span data-ttu-id="372ca-195">**온라인**: 디바이스가 Wi-Fi에 연결되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-195">**Online**: Indicates whether the device is connected to Wi-Fi.</span></span>
* <span data-ttu-id="372ca-196">**종료**: 디바이스를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-196">**Shutdown**: Turns off the device.</span></span>
* <span data-ttu-id="372ca-197">**다시 시작**: 디바이스를 하드 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-197">**Restart**: Cycles power on the device.</span></span>
* <span data-ttu-id="372ca-198">**보안**: 디바이스 보안 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-198">**Security**: Opens the Device Security page.</span></span>
* <span data-ttu-id="372ca-199">**냉각**: 디바이스의 온도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-199">**Cool**: Indicates the temperature of the device.</span></span>
* <span data-ttu-id="372ca-200">**A/C**: 디바이스가 연결되어 있고 충전 중인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-200">**A/C**: Indicates whether the device is plugged in and charging.</span></span>
* <span data-ttu-id="372ca-201">**도움말**: REST 인터페이스 설명서 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-201">**Help**: Opens the REST interface documentation page.</span></span>

<span data-ttu-id="372ca-202">홈페이지에는 다음 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-202">The home page shows the following info:</span></span>
* <span data-ttu-id="372ca-203">**디바이스 상태:** 디바이스의 상태를 모니터링하고 중요한 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-203">**Device Status:** monitors the health of your device and reports critical errors.</span></span>
* <span data-ttu-id="372ca-204">**Windows 정보:** HoloLens 이름과 현재 설치된 Windows 버전을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-204">**Windows information:** shows the name of the HoloLens and the currently installed version of Windows.</span></span>
* <span data-ttu-id="372ca-205">**기본 설정** 섹션에는 다음 설정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-205">**Preferences** section contains the following settings:</span></span>
   * <span data-ttu-id="372ca-206">**IPD**: 앞을 똑바로 바라볼 때 사용자의 동공 중심 사이의 거리인 IPD(동공 간 거리)를 밀리미터 단위로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-206">**IPD**: Sets the interpupillary distance (IPD), which is the distance, in millimeters, between the center of the user's pupils when looking straight ahead.</span></span> <span data-ttu-id="372ca-207">설정은 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-207">The setting takes effect immediately.</span></span> <span data-ttu-id="372ca-208">기본값은 디바이스를 설정할 때 자동으로 계산되었습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-208">The default value was calculated automatically when you set up your device.</span></span>
   * <span data-ttu-id="372ca-209">**디바이스 이름**: HoloLens에 이름을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-209">**Device name**: Assign a name to the HoloLens.</span></span> <span data-ttu-id="372ca-210">이 값을 변경 후에는 디바이스를 다시 부팅해야 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-210">You must reboot the device after changing this value for it to take effect.</span></span> <span data-ttu-id="372ca-211">**저장**을 클릭한 후 디바이스를 즉시 다시 부팅할 것인지 또는 나중에 다시 부팅할 것인지를 묻는 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-211">After clicking **Save**, a dialog will ask if you want to reboot the device immediately or reboot later.</span></span>
   * <span data-ttu-id="372ca-212">**절전 설정**: 디바이스가 전원에 연결된 경우 및 배터리에 연결된 경우에 각각 절전 모드로 전환되기 전에 대기할 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-212">**Sleep settings**: Sets the length of time to wait before the device goes to sleep when it's plugged in and when it's on battery.</span></span>

### <a name="3d-view"></a><span data-ttu-id="372ca-213">3D 뷰</span><span class="sxs-lookup"><span data-stu-id="372ca-213">3D View</span></span>

<span data-ttu-id="372ca-214">![Microsoft HoloLens에 대한 Windows 장치 포털의 3D 뷰 페이지](images/using-windows-portal-img-05.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-214">![3D View page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-05.png)</span></span><br>
<span data-ttu-id="372ca-215">*Microsoft HoloLens에 대한 Windows 장치 포털의 3D 뷰 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-215">*3D View page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="372ca-216">3D 뷰 페이지를 사용하여 HoloLens가 사용자의 주변을 해석하는 방법을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-216">Use the 3D View page to see how HoloLens interprets your surroundings.</span></span> <span data-ttu-id="372ca-217">마우스를 사용하여 뷰를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-217">Navigate the view by using the mouse:</span></span>
* <span data-ttu-id="372ca-218">회전: 왼쪽 단추 클릭 + 마우스</span><span class="sxs-lookup"><span data-stu-id="372ca-218">Rotate: left click + mouse;</span></span>
* <span data-ttu-id="372ca-219">이동: 오른쪽 단추 클릭 + 마우스</span><span class="sxs-lookup"><span data-stu-id="372ca-219">Pan: right click + mouse;</span></span>
* <span data-ttu-id="372ca-220">확대/축소: 마우스 스크롤</span><span class="sxs-lookup"><span data-stu-id="372ca-220">Zoom: mouse scroll.</span></span>
* <span data-ttu-id="372ca-221">**추적 옵션**</span><span class="sxs-lookup"><span data-stu-id="372ca-221">**Tracking options**</span></span>
   * <span data-ttu-id="372ca-222">**강제 시각적 추적**을 선택하여 연속 시각적 추적을 켭니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-222">Turn on continuous visual tracking by checking **Force visual tracking**.</span></span> 
   * <span data-ttu-id="372ca-223">**일시 중지**는 시각적 추적을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-223">**Pause** stops visual tracking.</span></span>
* <span data-ttu-id="372ca-224">**보기 옵션**: 3D 뷰의 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-224">**View options**: Set options on the 3D view:</span></span>
  * <span data-ttu-id="372ca-225">**추적**: 시각적 추적이 활성 상태인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-225">**Tracking**: Indicates whether visual tracking is active.</span></span>
  * <span data-ttu-id="372ca-226">**바닥 표시**: 체크무늬 바닥 평면을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-226">**Show floor**: Displays a checkered floor plane.</span></span>
  * <span data-ttu-id="372ca-227">**절두체 표시**: 절두체 보기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-227">**Show frustum**: Displays the view frustum.</span></span>
  * <span data-ttu-id="372ca-228">**보정 평면 표시**: HoloLens가 동작을 안정화하는 데 사용하는 평면을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-228">**Show stabilization plane**: Displays the plane that HoloLens uses for stabilizing motion.</span></span>
  * <span data-ttu-id="372ca-229">**메시 표시**: 사용자의 주변을 나타내는 공간 매핑 메시를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-229">**Show mesh**: Displays the spatial mapping mesh that represents your surroundings.</span></span>
  * <span data-ttu-id="372ca-230">**공간 앵커 표시**: 활성 앱의 공간 앵커를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-230">**Show spatial anchors**: Displays spatial anchors for the active app.</span></span> <span data-ttu-id="372ca-231">업데이트 단추를 클릭하여 앵커를 가져오고 새로 고쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-231">You must click the Update button to get and refresh the anchors.</span></span>
  * <span data-ttu-id="372ca-232">**자세한 정보 표시**: 실시간으로 바뀌는 손 위치, 머리 회전 사원수 및 디바이스 원점 벡터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-232">**Show details**: Displays hand positions, head rotation quaternions, and the device origin vector as they change in real time.</span></span>
  * <span data-ttu-id="372ca-233">**전체 화면 단추**: 3D 뷰를 전체 화면 모드로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-233">**Full screen button**: Shows the 3D View in full screen mode.</span></span> <span data-ttu-id="372ca-234">전체 화면 보기를 종료하려면 ESC 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-234">Press ESC to exit full screen view.</span></span>
* <span data-ttu-id="372ca-235">**표면 재구성**: **업데이트**를 클릭 또는 탭하여 디바이스에서 최신 공간 매핑 메시를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-235">**Surface reconstruction**: Click or tap **Update** to display the latest spatial mapping mesh from the device.</span></span> <span data-ttu-id="372ca-236">전체 단계를 완료하는 데 시간이 최대 몇 초 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-236">A full pass may take some time to complete (up to a few seconds).</span></span> <span data-ttu-id="372ca-237">메시는 3D 뷰에서 자동으로 업데이트되지 않으며, 디바이스에서 수동으로 **업데이트**를 클릭해야만 최신 메시를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-237">The mesh does not update automatically in the 3D view, and you must manually click **Update** to get the latest mesh from the device.</span></span> <span data-ttu-id="372ca-238">**저장**을 클릭하여 현재 공간 매핑 메시를 PC에서 obj 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-238">Click **Save** to save the current spatial mapping mesh as an obj file on your PC.</span></span>
* <span data-ttu-id="372ca-239">**공간 앵커**: 업데이트를 클릭하여 활성 앱의 공간 앵커를 표시하거나 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-239">**Spatial anchors**: Click Update to display or update the spatial anchors for the active app.</span></span>

### <a name="map-manager"></a><span data-ttu-id="372ca-240">맵 관리자</span><span class="sxs-lookup"><span data-stu-id="372ca-240">Map Manager</span></span>

<span data-ttu-id="372ca-241">맵 관리자를 사용하면 디바이스 간에 맵을 공유할 수 있으며, 위치 기반 엔터테인먼트 고객에 대한 공유 환경을 설정하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-241">Map Manager allows you to share maps across devices, which can be used to setup shared experiences for Location Based Entertainment customers.</span></span> <span data-ttu-id="372ca-242">이 도구를 사용하여 시스템 맵 및 앵커를 가져오고 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-242">The tool allows you to import and export system maps and anchors.</span></span>  

<span data-ttu-id="372ca-243">맵 관리자에 액세스하려면 장치 포털에 로그인하고, **Mixed Reality -> 맵 관리자**를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-243">To access the Map Manager, log into the Device Portal and select **Mixed Reality -> Map Manager**:</span></span> 

<span data-ttu-id="372ca-244">![Windows 장치 포털의 맵 관리자 페이지](images/using-windows-portal-img-06.png)
*Microsoft HoloLens에 있는 Windows 장치 포털의 맵 관리자 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-244">![Map manager page in Windows Device Portal](images/using-windows-portal-img-06.png)
*Map Manager page in Windows Device Portal on Microsoft HoloLens*</span></span>

#### <a name="exporting-and-importing-maps"></a><span data-ttu-id="372ca-245">맵 내보내기 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="372ca-245">Exporting and importing maps</span></span>

<span data-ttu-id="372ca-246">맵을 내보내려면 **시스템 맵 및 앵커 내보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-246">To export maps, click **Export System Map & Anchors**.</span></span> <span data-ttu-id="372ca-247">이 경우 시간이 좀 걸릴 수 있으므로 맵을 내보내는 동안 30~60초 동안 기다리도록 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-247">This could take a while so be prepared to wait for 30-60 seconds while the map is exported.</span></span> <span data-ttu-id="372ca-248">완료되면 브라우저에서 파일이 다운로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-248">Once it’s complete, the file will be downloaded in your browser.</span></span>  

<span data-ttu-id="372ca-249">맵과 앵커를 가져오려면 **맵 파일 업로드** 및 **앵커 파일 업로드**를 각각 클릭하고, 이미 내보낸 맵 또는 앵커 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-249">To import maps and anchors, click **Upload a map file** and **Upload an anchor file** respectively and select a map or anchor file that you've already exported.</span></span> <span data-ttu-id="372ca-250">업로드된 맵 또는 앵커 파일은 사용자 또는 다른 HoloLens 디바이스에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-250">The uploaded map or anchor file can come from your or any other HoloLens device.</span></span> 

> [!NOTE]
> <span data-ttu-id="372ca-251">HoloLens에서는 공간 매핑 데이터베이스를 가져오고 내보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-251">On HoloLens, it's also possible to import and export the spatial mapping data base.</span></span> <span data-ttu-id="372ca-252">그러나 이 데이터베이스는 HoloLens 이외의 디바이스에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-252">However, this doesn't work on non-HoloLens devices.</span></span>  


### <a name="mixed-reality-capture"></a><span data-ttu-id="372ca-253">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="372ca-253">Mixed Reality Capture</span></span>

<span data-ttu-id="372ca-254">![Microsoft HoloLens에 대한 Windows 장치 포털의 혼합 현실 캡처 페이지](images/using-windows-portal-img-07.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-254">![Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-07.png)</span></span><br>
<span data-ttu-id="372ca-255">*Microsoft HoloLens에 대한 Windows 장치 포털의 혼합 현실 캡처 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-255">*Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="372ca-256">혼합 현실 캡처 페이지를 사용하여 HoloLens에서 미디어 스트림을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-256">Use the Mixed Reality Capture page to save media streams from the HoloLens.</span></span>
* <span data-ttu-id="372ca-257">**캡처 설정**: 다음 설정을 확인하여 캡처할 미디어 스트림을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-257">**Capture Settings**: Control the media streams that are captured by checking the following settings:</span></span>
  * <span data-ttu-id="372ca-258">**홀로그램**: 비디오 스트림에서 홀로그램 콘텐츠를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-258">**Holograms**: Captures the holographic content in the video stream.</span></span> <span data-ttu-id="372ca-259">홀로그램은 스테레오가 아닌 모노로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-259">Holograms are rendered in mono, not stereo.</span></span>
  * <span data-ttu-id="372ca-260">**PV 카메라**: 사진/비디오 카메라에서 비디오 스트림을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-260">**PV camera**: Captures the video stream from the photo/video camera.</span></span>
  * <span data-ttu-id="372ca-261">**마이크 오디오**: 마이크 배열에서 오디오를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-261">**Mic Audio**: Captures audio from the microphone array.</span></span>
  * <span data-ttu-id="372ca-262">**앱 오디오**: 현재 실행 중인 앱에서 오디오를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-262">**App Audio**: Captures audio from the currently running app.</span></span>
  * <span data-ttu-id="372ca-263">**카메라에서 렌더링**: [실행 중인 앱에서 지원](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)할 경우 캡처본을 사진/비디오 카메라 관점이 되도록 조정합니다(HoloLens 2만 해당).</span><span class="sxs-lookup"><span data-stu-id="372ca-263">**Render from Camera**: Aligns the capture to be from the perspective of the photo/video camera, if [supported by the running app](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (HoloLens 2 only).</span></span>
  * <span data-ttu-id="372ca-264">**실시간 미리 보기 품질**: 실시간 미리 보기의 화면 해상도, 프레임 속도 및 스트리밍 속도를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-264">**Live preview quality**: Select the screen resolution, frame rate, and streaming rate for the live preview.</span></span>
* <span data-ttu-id="372ca-265">**오디오 설정**(HoloLens 2만 해당):</span><span class="sxs-lookup"><span data-stu-id="372ca-265">**Audio Settings** (HoloLens 2 only):</span></span>
  * <span data-ttu-id="372ca-266">**오디오 미디어 범주**: 마이크를 처리할 때 사용되는 범주를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-266">**Audio Media Category**: Select the category is used when processing the microphone.</span></span> <span data-ttu-id="372ca-267">**기본**에는 일부 환경이 포함되지만 **통신**은 백그라운드 노이즈 취소를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-267">**Default**  will include some of the environment whereas **Communications** applies background noise cancellation.</span></span>
  * <span data-ttu-id="372ca-268">**앱 오디오 게인**: 앱 오디오의 볼륨에 적용되는 게인입니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-268">**App Audio Gain**: The gain applied to app audio's volume.</span></span>
  * <span data-ttu-id="372ca-269">**마이크 오디오 게인**: 마이크 오디오의 볼륨에 적용되는 게인입니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-269">**Mic Audio Gain**: The gain applied to mic audio's volume.</span></span>
* <span data-ttu-id="372ca-270">**사진 및 비디오 설정**(HoloLens 2, 버전 2004 이상):</span><span class="sxs-lookup"><span data-stu-id="372ca-270">**Photo and Video Settings** (HoloLens 2, version 2004 or later):</span></span>
  * <span data-ttu-id="372ca-271">**캡처 프로필**: 사진과 비디오를 촬영할 때 사용할 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-271">**Capture Profile**: Select the profile used when taking photos and videos.</span></span> <span data-ttu-id="372ca-272">프로필은 사용할 수 있는 해상도와 프레임 비율을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-272">The profile determines which resolutions and frame-rates are available.</span></span>
  * <span data-ttu-id="372ca-273">**사진 해상도**: 사진을 촬영하는 해상도입니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-273">**Photo Resolution**: The resolution the photo will be taken with.</span></span>
  * <span data-ttu-id="372ca-274">**비디오 해상도 및 프레임 비율**: 촬영하는 비디오의 해상도와 프레임 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-274">**Video Resolution and Frame-rate**: The resolution and frame-rate the video will be taken with.</span></span>
  * <span data-ttu-id="372ca-275">**비디오 안정화 버퍼**: 비디오를 촬영할 때 사용되는 버퍼 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-275">**Video Stabilization Buffer**: The buffer size used when taking a video.</span></span> <span data-ttu-id="372ca-276">값이 클수록 빠른 움직임에 맞게 보정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-276">The higher the value, the better it can compensate for quick movements.</span></span>
* <span data-ttu-id="372ca-277">**실시간 미리 보기** 단추를 클릭 또는 탭하여 캡처 스트림을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-277">Click or tap the **Live preview** button to show the capture stream.</span></span> <span data-ttu-id="372ca-278">**실시간 미리 보기 중지**는 캡처 스트림을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-278">**Stop live preview** stops the capture stream.</span></span>
* <span data-ttu-id="372ca-279">**녹화**를 클릭 또는 탭하여 지정된 설정을 사용해 혼합 현실 스트림의 녹화를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-279">Click or tap **Record** to start recording the mixed-reality stream, using the specified settings.</span></span> <span data-ttu-id="372ca-280">**녹화 정지**는 녹화를 끝내고 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-280">**Stop recording** ends the recording and saves it.</span></span>
* <span data-ttu-id="372ca-281">**사진 촬영**을 클릭 또는 탭하여 캡처 스트림에서 정지 이미지를 촬영합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-281">Click or tap **Take photo** to take a still image from the capture stream.</span></span>
* <span data-ttu-id="372ca-282">**기본 설정 복원**을 클릭하거나 탭하여 오디오, 사진 및 비디오 설정에 기본 설정을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-282">Click or tap **Restore Default Settings** to restore the default settings for audio, photo, and video settings.</span></span>
* <span data-ttu-id="372ca-283">**비디오 및 사진**: 디바이스에서 촬영한 비디오 및 사진 캡처 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-283">**Videos and photos**: Shows a list of video and photo captures taken on the device.</span></span>

<span data-ttu-id="372ca-284">이 페이지의 모든 설정은 Windows 장치 포털을 사용하는 캡처에 적용되지만 일부는 추가적으로 시스템 MRC(시작 메뉴, 하드웨어 단추, 글로벌 음성 명령, Miracast) 및 사용자 지정 MRC 레코더에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-284">All settings on this page apply to captures taken using Windows Device Portal, but some additionally apply to System MRC (start menu, hardware buttons, global voice commands, Miracast) and to custom MRC Recorders.</span></span>

|  <span data-ttu-id="372ca-285">설정</span><span class="sxs-lookup"><span data-stu-id="372ca-285">Setting</span></span>  |  <span data-ttu-id="372ca-286">시스템 MRC에 적용</span><span class="sxs-lookup"><span data-stu-id="372ca-286">Applies to System MRC</span></span>  |  <span data-ttu-id="372ca-287">사용자 지정 MRC 레코더에 적용</span><span class="sxs-lookup"><span data-stu-id="372ca-287">Applies to Custom MRC Recorders</span></span> |
|----------|----------|----------|
|  <span data-ttu-id="372ca-288">홀로그램</span><span class="sxs-lookup"><span data-stu-id="372ca-288">Holograms</span></span>  |  <span data-ttu-id="372ca-289">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-289">No</span></span>  |  <span data-ttu-id="372ca-290">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-290">No</span></span> |
|  <span data-ttu-id="372ca-291">PV 카메라</span><span class="sxs-lookup"><span data-stu-id="372ca-291">PV camera</span></span>  |  <span data-ttu-id="372ca-292">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-292">No</span></span>  |  <span data-ttu-id="372ca-293">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-293">No</span></span> |
|  <span data-ttu-id="372ca-294">마이크 오디오</span><span class="sxs-lookup"><span data-stu-id="372ca-294">Mic Audio</span></span>  |  <span data-ttu-id="372ca-295">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-295">No</span></span>  |  <span data-ttu-id="372ca-296">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-296">No</span></span> |
|  <span data-ttu-id="372ca-297">앱 오디오</span><span class="sxs-lookup"><span data-stu-id="372ca-297">App Audio</span></span>  |  <span data-ttu-id="372ca-298">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-298">No</span></span>  |  <span data-ttu-id="372ca-299">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-299">No</span></span> |
|  <span data-ttu-id="372ca-300">카메라에서 렌더링</span><span class="sxs-lookup"><span data-stu-id="372ca-300">Render from Camera</span></span>  |  <span data-ttu-id="372ca-301">예</span><span class="sxs-lookup"><span data-stu-id="372ca-301">Yes</span></span>    |  <span data-ttu-id="372ca-302">예(재정의할 수 있음)</span><span class="sxs-lookup"><span data-stu-id="372ca-302">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="372ca-303">실시간 미리 보기 품질</span><span class="sxs-lookup"><span data-stu-id="372ca-303">Live preview quality</span></span>  |  <span data-ttu-id="372ca-304">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-304">No</span></span>  |  <span data-ttu-id="372ca-305">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-305">No</span></span> |
|  <span data-ttu-id="372ca-306">오디오 미디어 범주</span><span class="sxs-lookup"><span data-stu-id="372ca-306">Audio Media Category</span></span>  |  <span data-ttu-id="372ca-307">예</span><span class="sxs-lookup"><span data-stu-id="372ca-307">Yes</span></span>  |  <span data-ttu-id="372ca-308">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-308">No</span></span> |
|  <span data-ttu-id="372ca-309">앱 오디오 게인</span><span class="sxs-lookup"><span data-stu-id="372ca-309">App Audio Gain</span></span>  |  <span data-ttu-id="372ca-310">예</span><span class="sxs-lookup"><span data-stu-id="372ca-310">Yes</span></span>  |  <span data-ttu-id="372ca-311">예(재정의할 수 있음)</span><span class="sxs-lookup"><span data-stu-id="372ca-311">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="372ca-312">마이크 오디오 게인</span><span class="sxs-lookup"><span data-stu-id="372ca-312">Mic Audio Gain</span></span>  |  <span data-ttu-id="372ca-313">예</span><span class="sxs-lookup"><span data-stu-id="372ca-313">Yes</span></span>  |  <span data-ttu-id="372ca-314">예(재정의할 수 있음)</span><span class="sxs-lookup"><span data-stu-id="372ca-314">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="372ca-315">캡처 프로필</span><span class="sxs-lookup"><span data-stu-id="372ca-315">Capture Profile</span></span>  |  <span data-ttu-id="372ca-316">예</span><span class="sxs-lookup"><span data-stu-id="372ca-316">Yes</span></span>  |  <span data-ttu-id="372ca-317">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-317">No</span></span> |
|  <span data-ttu-id="372ca-318">사진 해상도</span><span class="sxs-lookup"><span data-stu-id="372ca-318">Photo Resolution</span></span>  |  <span data-ttu-id="372ca-319">예</span><span class="sxs-lookup"><span data-stu-id="372ca-319">Yes</span></span>  |  <span data-ttu-id="372ca-320">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-320">No</span></span> |
|  <span data-ttu-id="372ca-321">비디오 해상도 및 프레임 비율</span><span class="sxs-lookup"><span data-stu-id="372ca-321">Video Resolution and Frame-rate</span></span>  |  <span data-ttu-id="372ca-322">예</span><span class="sxs-lookup"><span data-stu-id="372ca-322">Yes</span></span>  |  <span data-ttu-id="372ca-323">아니요</span><span class="sxs-lookup"><span data-stu-id="372ca-323">No</span></span> |
|  <span data-ttu-id="372ca-324">비디오 안정화 버퍼</span><span class="sxs-lookup"><span data-stu-id="372ca-324">Video Stabilization Buffer</span></span>  |  <span data-ttu-id="372ca-325">예</span><span class="sxs-lookup"><span data-stu-id="372ca-325">Yes</span></span>  |  <span data-ttu-id="372ca-326">예(재정의할 수 있음)</span><span class="sxs-lookup"><span data-stu-id="372ca-326">Yes (can be overridden)</span></span> |

> [!NOTE]
> <span data-ttu-id="372ca-327">[동시 MRC에 대한 제한 사항](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-327">There are [limitations to simultaneous MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span></span>
> * <span data-ttu-id="372ca-328">Windows 장치 포털이 비디오를 녹화하는 동안 앱에서 사진/비디오 카메라에 액세스하려고 하면 비디오 녹화가 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-328">If an app tries to access the photo/video camera while Windows Device Portal is recording a video, the video recording will stop.</span></span>
>   * <span data-ttu-id="372ca-329">앱이 SharedReadOnly 모드를 사용하여 사진/비디오 카메라에 액세스하는 경우 HoloLens 2는 비디오 녹화를 중지하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-329">HoloLens 2 will not stop recording video if the app accesses the photo/video camera with SharedReadOnly mode.</span></span>
> * <span data-ttu-id="372ca-330">앱이 현재 사진/비디오 카메라를 사용하는 경우 Windows 장치 포털에서 사진을 촬영하거나 비디오를 녹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-330">If an app is actively using the photo/video camera, Windows Device Portal is able to take a photo or record a video.</span></span>
> * <span data-ttu-id="372ca-331">라이브 스트리밍:</span><span class="sxs-lookup"><span data-stu-id="372ca-331">Live streaming:</span></span>
>   * <span data-ttu-id="372ca-332">HoloLens(1세대)는 Windows 장치 포털에서 라이브 스트리밍 중에 앱이 사진/비디오 카메라에 액세스하지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-332">HoloLens (1st gen) prevents an app from accessing the photo/video camera while live streaming from Windows Device Portal.</span></span>
>   * <span data-ttu-id="372ca-333">HoloLens(1세대)는 앱이 현재 사진/비디오 카메라를 사용하는 경우 라이브 스트리밍에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-333">HoloLens (1st gen) will fail to live stream if an app is actively using the photo/video camera.</span></span>
>   * <span data-ttu-id="372ca-334">HoloLens 2는 앱이 ExclusiveControl 모드에서 사진/비디오 카메라에 액세스하려고 하면 라이브 스트리밍을 자동으로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-334">HoloLens 2 automatically stops live streaming when an app tries to access the photo/video camera in ExclusiveControl mode.</span></span>
>   * <span data-ttu-id="372ca-335">HoloLens 2는 앱이 현재 PV 카메라를 사용 중인 경우 라이브 스트림을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-335">HoloLens 2 is able to start a live stream while an app is actively using the PV camera.</span></span>

### <a name="performance-tracing"></a><span data-ttu-id="372ca-336">성능 추적</span><span class="sxs-lookup"><span data-stu-id="372ca-336">Performance Tracing</span></span>

<span data-ttu-id="372ca-337">![Microsoft HoloLens에 대한 Windows 장치 포털의 성능 추적 페이지](images/using-windows-portal-img-08.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-337">![Performance Tracing page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-08.png)</span></span><br>
<span data-ttu-id="372ca-338">*Microsoft HoloLens에 대한 Windows 장치 포털의 성능 추적 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-338">*Performance Tracing page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="372ca-339">HoloLens에서 [WPR(Windows Performance Recorder)](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) 추적을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-339">Capture [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) traces from your HoloLens.</span></span>
* <span data-ttu-id="372ca-340">**사용 가능한 프로필**: 드롭다운 목록에서 WPR 프로필을 선택하고 **시작**을 클릭 또는 탭하여 추적을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-340">**Available profiles**: Select the WPR profile from the dropdown, and click or tap **Start** to start tracing.</span></span>
* <span data-ttu-id="372ca-341">**사용자 지정 프로필**: PC에서 WPR 프로필을 선택하려면 **찾아보기**를 클릭 또는 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-341">**Custom profiles**: Click or tap **Browse** to choose a WPR profile from your PC.</span></span> <span data-ttu-id="372ca-342">추적을 시작하려면 **업로드 및 시작**을 클릭 또는 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-342">Click or tap **Upload and start** to start tracing.</span></span>

<span data-ttu-id="372ca-343">추적을 중지하려면 중지 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-343">To stop the trace, click the stop link.</span></span> <span data-ttu-id="372ca-344">추적 파일이 다운로드를 완료할 때까지 이 페이지에 계속 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-344">Stay on this page until the trace file has completed downloading.</span></span>

<span data-ttu-id="372ca-345">캡처된 ETL 파일은 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx)에서 분석을 위해 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-345">Captured ETL files can be opened for analysis in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).</span></span>

### <a name="processes"></a><span data-ttu-id="372ca-346">프로세스</span><span class="sxs-lookup"><span data-stu-id="372ca-346">Processes</span></span>

<span data-ttu-id="372ca-347">![Microsoft HoloLens에 대한 Windows 장치 포털의 프로세스 페이지](images/using-windows-portal-img-09.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-347">![Processes page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-09.png)</span></span><br>
<span data-ttu-id="372ca-348">*Microsoft HoloLens에 대한 Windows 장치 포털의 프로세스 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-348">*Processes page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="372ca-349">현재 실행 중인 프로세스에 대한 세부 정보를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-349">Shows details about currently running processes.</span></span> <span data-ttu-id="372ca-350">앱 및 시스템 프로세스 모두 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-350">This includes both apps and system processes.</span></span>

### <a name="system-performance"></a><span data-ttu-id="372ca-351">시스템 성능</span><span class="sxs-lookup"><span data-stu-id="372ca-351">System Performance</span></span>

<span data-ttu-id="372ca-352">![Microsoft HoloLens에 대한 Windows 장치 포털의 시스템 성능 페이지](images/using-windows-portal-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-352">![System Performance page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-10.png)</span></span><br>
<span data-ttu-id="372ca-353">*Microsoft HoloLens에 대한 Windows 장치 포털의 시스템 성능 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-353">*System Performance page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="372ca-354">전력 사용량, 프레임 속도 및 CPU 로드와 같은 시스템 진단 정보를 실시간 그래프로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-354">Shows real-time graphs of system diagnostic info, like power usage, frame rate, and CPU load.</span></span>

<span data-ttu-id="372ca-355">사용 가능한 메트릭은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-355">These are the available metrics:</span></span>
* <span data-ttu-id="372ca-356">**SoC 전원**: 1분 평균 순간 시스템 온칩 전력 사용률</span><span class="sxs-lookup"><span data-stu-id="372ca-356">**SoC power**: Instantaneous system-on-chip power utilization, averaged over one minute</span></span>
* <span data-ttu-id="372ca-357">**시스템 전원**: 1분 평균 순간 시스템 전력 사용률</span><span class="sxs-lookup"><span data-stu-id="372ca-357">**System power**: Instantaneous system power utilization, averaged over one minute</span></span>
* <span data-ttu-id="372ca-358">**프레임 속도**: 초당 프레임, 초당 누락 VBlank 및 연속 누락 VBlank</span><span class="sxs-lookup"><span data-stu-id="372ca-358">**Frame rate**: Frames per second, missed VBlanks per second, and consecutive missed VBlanks</span></span>
* <span data-ttu-id="372ca-359">**GPU**: GPU 엔진 사용률(사용 가능한 총 전원 대비 백분율)</span><span class="sxs-lookup"><span data-stu-id="372ca-359">**GPU**: GPU engine utilization, percent of total available</span></span>
* <span data-ttu-id="372ca-360">**CPU**: 사용 가능한 총 전원 대비 백분율</span><span class="sxs-lookup"><span data-stu-id="372ca-360">**CPU**: percent of total available</span></span>
* <span data-ttu-id="372ca-361">**I/O**: 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="372ca-361">**I/O**: Reads and writes</span></span>
* <span data-ttu-id="372ca-362">**네트워크**: 수신 및 전송</span><span class="sxs-lookup"><span data-stu-id="372ca-362">**Network**: Received and sent</span></span>
* <span data-ttu-id="372ca-363">**메모리**: 전체, 사용 중, 약정, 페이징 및 비페이징 메모리</span><span class="sxs-lookup"><span data-stu-id="372ca-363">**Memory**: Total, in use, committed, paged, and non-paged</span></span>

### <a name="apps"></a><span data-ttu-id="372ca-364">앱</span><span class="sxs-lookup"><span data-stu-id="372ca-364">Apps</span></span>

<span data-ttu-id="372ca-365">![Microsoft HoloLens에 대한 Windows 장치 포털의 앱 페이지](images/using-windows-portal-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-365">![Apps page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-11.png)</span></span><br>
<span data-ttu-id="372ca-366">*Microsoft HoloLens에 대한 Windows 장치 포털의 앱 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-366">*Apps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="372ca-367">HoloLens에 설치된 앱을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-367">Manages the apps that are installed on the HoloLens.</span></span>
* <span data-ttu-id="372ca-368">**설치된 앱**: 앱을 제거하고 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-368">**Installed apps**: Remove and start apps.</span></span>
* <span data-ttu-id="372ca-369">**실행 중인 앱**: 현재 실행 중인 앱을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-369">**Running apps**: Lists apps that are running currently.</span></span>
* <span data-ttu-id="372ca-370">**앱 설치**: 컴퓨터/네트워크 폴더에서 설치할 앱 패키지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-370">**Install app**: Select app packages for installation from a folder on your computer/network.</span></span>
* <span data-ttu-id="372ca-371">**종속성**: 설치하려는 앱에 대한 종속성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-371">**Dependency**: Add dependencies for the app you are going to install.</span></span>
* <span data-ttu-id="372ca-372">**배포**: 선택한 앱 + 종속성을 HoloLens에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-372">**Deploy**: Deploy the selected app + dependencies to the HoloLens.</span></span>

### <a name="app-crash-dumps"></a><span data-ttu-id="372ca-373">앱 크래시 덤프</span><span class="sxs-lookup"><span data-stu-id="372ca-373">App Crash Dumps</span></span>

<span data-ttu-id="372ca-374">![Microsoft HoloLens에 대한 Windows 장치 포털의 앱 크래시 덤프 페이지](images/using-windows-portal-img-12.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-374">![App Crash Dumps page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-12.png)</span></span><br>
<span data-ttu-id="372ca-375">*Microsoft HoloLens에 대한 Windows 장치 포털의 앱 크래시 덤프 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-375">*App Crash Dumps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="372ca-376">이 페이지에서는 테스트용으로 로드된 앱에 대한 크래시 덤프를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-376">This page allows you to collect crash dumps for your side-loaded apps.</span></span> <span data-ttu-id="372ca-377">크래시 덤프를 수집하려는 각 앱에 대해 **크래시 덤프 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-377">Check the **Crash Dumps Enabled** checkbox for each app for which you want to collect crash dumps.</span></span> <span data-ttu-id="372ca-378">이 페이지로 돌아와서 크래시 덤프를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-378">Return to this page to collect crash dumps.</span></span> <span data-ttu-id="372ca-379">덤프 파일은 [디버깅을 위해 Visual Studio에서 열릴 수 있습니다](https://msdn.microsoft.com/library/d5zhxt22.aspx).</span><span class="sxs-lookup"><span data-stu-id="372ca-379">Dump files can be [opened in Visual Studio for debugging](https://msdn.microsoft.com/library/d5zhxt22.aspx).</span></span>

### <a name="file-explorer"></a><span data-ttu-id="372ca-380">파일 탐색기</span><span class="sxs-lookup"><span data-stu-id="372ca-380">File Explorer</span></span>

<span data-ttu-id="372ca-381">![Microsoft HoloLens에 대한 Windows 장치 포털의 파일 탐색기 페이지](images/using-windows-portal-img-13.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-381">![File Explorer page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-13.png)</span></span><br>
<span data-ttu-id="372ca-382">*Microsoft HoloLens에 대한 Windows 장치 포털의 파일 탐색기 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-382">*File Explorer page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="372ca-383">파일 탐색기를 사용하여 파일을 찾아보고, 업로드하고, 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-383">Use the file explorer to browse, upload, and download files.</span></span> <span data-ttu-id="372ca-384">문서 폴더, 그림 폴더 및 Visual Studio 또는 장치 포털에서 배포한 앱에 대한 로컬 스토리지 폴더의 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-384">You can work with files in the Documents folder, Pictures folder, and in the local storage folders for apps that you deployed from Visual Studio or the Device Portal.</span></span>

### <a name="kiosk-mode"></a><span data-ttu-id="372ca-385">키오스크 모드</span><span class="sxs-lookup"><span data-stu-id="372ca-385">Kiosk Mode</span></span>

>[!NOTE]
><span data-ttu-id="372ca-386">키오스크 모드는 [Microsoft HoloLens Commercial Suite](../../commercial-features.md)에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-386">Kiosk mode is only available with the [Microsoft HoloLens Commercial Suite](../../commercial-features.md).</span></span>

![Microsoft HoloLens에 있는 Windows 장치 포털의 키오스크 모드 페이지](images/using-windows-portal-img-14.png)

<span data-ttu-id="372ca-388">Windows 장치 포털을 통해 키오스크 모드를 사용하도록 설정하는 방법에 대한 최신 지침은 Windows IT 전문가 센터의 [키오스크 모드로 HoloLens 설정 ](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) 문서를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="372ca-388">Check the [Set up HoloLens in kiosk mode](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) article in Windows IT Pro Center for up-to-date instructions on enabling kiosk mode via Windows Device Portal.</span></span>

### <a name="logging"></a><span data-ttu-id="372ca-389">로깅</span><span class="sxs-lookup"><span data-stu-id="372ca-389">Logging</span></span>

<span data-ttu-id="372ca-390">![Microsoft HoloLens에 대한 Windows 장치 포털의 로깅 페이지](images/using-windows-portal-img-15.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-390">![Logging page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-15.png)</span></span><br>
<span data-ttu-id="372ca-391">*Microsoft HoloLens에 대한 Windows 장치 포털의 로깅 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-391">*Logging page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="372ca-392">HoloLens에서 실시간 ETW(Windows용 이벤트 추적)를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-392">Manages realtime Event Tracing for Windows (ETW) on the HoloLens.</span></span>

<span data-ttu-id="372ca-393">**이벤트 목록**만 표시하려면 **공급자 숨기기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-393">Check **Hide providers** to show the **Events** list only.</span></span>
* <span data-ttu-id="372ca-394">**등록된 공급자**: ETW 공급자와 추적 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-394">**Registered providers**: Select the ETW provider and the tracing level.</span></span> <span data-ttu-id="372ca-395">추적 수준은 다음 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-395">Tracing level is one of these values:</span></span>
   1. <span data-ttu-id="372ca-396">비정상적인 끝내기 또는 종료</span><span class="sxs-lookup"><span data-stu-id="372ca-396">Abnormal exit or termination</span></span>
   2. <span data-ttu-id="372ca-397">심각한 오류</span><span class="sxs-lookup"><span data-stu-id="372ca-397">Severe errors</span></span>
   3. <span data-ttu-id="372ca-398">경고</span><span class="sxs-lookup"><span data-stu-id="372ca-398">Warnings</span></span>
   4. <span data-ttu-id="372ca-399">오류가 아닌 경고</span><span class="sxs-lookup"><span data-stu-id="372ca-399">Non-error warnings</span></span>

<span data-ttu-id="372ca-400">추적을 시작하려면 **사용**을 클릭 또는 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-400">Click or tap **Enable** to start tracing.</span></span> <span data-ttu-id="372ca-401">공급자가 **활성화된 공급자** 드롭다운에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-401">The provider is added to the **Enabled Providers** dropdown.</span></span>
* <span data-ttu-id="372ca-402">**사용자 지정 공급자**: 사용자 지정 ETW 공급자와 추적 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-402">**Custom providers**: Select a custom ETW provider and the tracing level.</span></span> <span data-ttu-id="372ca-403">공급자를 GUID로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-403">Identify the provider by its GUID.</span></span> <span data-ttu-id="372ca-404">GUID에 대괄호를 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="372ca-404">Don't include brackets in the GUID.</span></span>
* <span data-ttu-id="372ca-405">**활성화된 공급자**: 활성화된 공급자를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-405">**Enabled providers**: Lists the enabled providers.</span></span> <span data-ttu-id="372ca-406">추적을 중지하려면 드롭다운에서 공급자를 선택하고 **사용 안 함**을 클릭 또는 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-406">Select a provider from the dropdown and click or tap **Disable** to stop tracing.</span></span> <span data-ttu-id="372ca-407">모든 추적을 일시 중단하려면 **모두 중지**를 클릭 또는 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-407">Click or tap **Stop all** to suspend all tracing.</span></span>
* <span data-ttu-id="372ca-408">**공급자 기록**: 현재 세션 중 활성화된 ETW 공급자를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-408">**Providers history**: Shows the ETW providers that were enabled during the current session.</span></span> <span data-ttu-id="372ca-409">비활성화된 공급자를 활성화하려면 **사용**을 클릭 또는 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-409">Click or tap **Enable** to activate a provider that was disabled.</span></span> <span data-ttu-id="372ca-410">기록을 지우려면 **지우기**를 클릭 또는 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-410">Click or tap **Clear** to clear the history.</span></span>
* <span data-ttu-id="372ca-411">**이벤트**: 선택된 공급자의 ETW 이벤트를 표 형식으로 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-411">**Events**: Lists ETW events from the selected providers in table format.</span></span> <span data-ttu-id="372ca-412">이 표는 실시간으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-412">This table is updated in real time.</span></span> <span data-ttu-id="372ca-413">모든 ETW 이벤트를 표에서 삭제하려면 표 아래에 있는 **지우기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-413">Beneath the table, click the **Clear** button to delete all ETW events from the table.</span></span> <span data-ttu-id="372ca-414">이렇게 해도 공급자는 비활성화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-414">This does not disable any providers.</span></span> <span data-ttu-id="372ca-415">**파일로 저장**을 클릭하여 현재 수집된 ETW 이벤트를 CSV 파일에 로컬로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-415">You can click **Save to file** to export the currently collected ETW events to a CSV file locally.</span></span>
* <span data-ttu-id="372ca-416">**필터**: 수집된 ETW 이벤트를 ID, 키워드, 수준, 공급자 이름, 작업 이름 또는 텍스트로 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-416">**Filters**: Allow you to filter the ETW events collected by ID, Keyword, Level, Provider Name, Task Name, or Text.</span></span> <span data-ttu-id="372ca-417">여러 조건을 함께 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-417">You can combine several criteria together:</span></span>
   1. <span data-ttu-id="372ca-418">동일한 속성에 적용되는 조건의 경우 이러한 조건 중 하나라도 만족하는 이벤트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-418">For criteria applying to the same property, events that can satisfy any one of these criteria are shown.</span></span>
   2. <span data-ttu-id="372ca-419">다른 속성에 적용되는 조건의 경우 이벤트가 모든 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-419">For criteria applying to a different property, events must satisfy all of the criteria</span></span>

<span data-ttu-id="372ca-420">예를 들어 *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')* 기준을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-420">For example, you can specify the criteria *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span></span>

### <a name="simulation"></a><span data-ttu-id="372ca-421">Simulation</span><span class="sxs-lookup"><span data-stu-id="372ca-421">Simulation</span></span>

<span data-ttu-id="372ca-422">![Microsoft HoloLens에 대한 Windows 장치 포털의 시뮬레이션 페이지](images/using-windows-portal-img-16.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-422">![Simulation page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-16.png)</span></span><br>
<span data-ttu-id="372ca-423">*Microsoft HoloLens에 대한 Windows 장치 포털의 시뮬레이션 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-423">*Simulation page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="372ca-424">테스트를 위해 입력 데이터를 기록 및 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-424">Allows you to record and play back input data for testing.</span></span>
* <span data-ttu-id="372ca-425">**공간 캡처**: 사용자의 주변에 대한 공간 매핑 메시를 포함하는 시뮬레이트된 공간 파일을 다운로드하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-425">**Capture room**: Used to download a simulated room file that contains the spatial mapping mesh for the user's surroundings.</span></span> <span data-ttu-id="372ca-426">공간의 이름을 지정한 다음, **캡처**를 클릭하여 PC에 .xef 파일로 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-426">Name the room and then click **Capture** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="372ca-427">이 공간 파일을 HoloLens 에뮬레이터에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-427">This room file can be loaded into the HoloLens emulator.</span></span>
* <span data-ttu-id="372ca-428">**녹화**: 녹화할 스트림을 선택하고 녹화본의 이름을 지정하고 **녹화**를 클릭 또는 탭하여 녹화를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-428">**Recording**: Check the streams to record, name the recording, and click or tap **Record** to start recoding.</span></span> <span data-ttu-id="372ca-429">HoloLens를 사용하여 작업을 수행한 다음, **중지**를 클릭하여 PC에 .xef 파일로 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-429">Perform actions with your HoloLens and then click **Stop** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="372ca-430">이 파일을 HoloLens 에뮬레이터 또는 디바이스에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-430">This file can be loaded on the HoloLens emulator or device.</span></span>
* <span data-ttu-id="372ca-431">**재생**: **녹화본 업로드**를 클릭 또는 탭하여 PC에서 xef 파일을 선택하고 HoloLens에 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-431">**Playback**: Click or tap **Upload recording** to select a xef file from your PC and send the data to the HoloLens.</span></span>
* <span data-ttu-id="372ca-432">**제어 모드**: 드롭다운 목록에서 **기본** 또는 **시뮬레이션**을 선택하고 **설정** 단추를 클릭 또는 탭하여 HoloLens의 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-432">**Control mode**: Select **Default** or **Simulation** from the dropdown, and click or tap the **Set** button to select the mode on the HoloLens.</span></span> <span data-ttu-id="372ca-433">"시뮬레이션"을 선택하면 HoloLens의 실제 센서를 사용할 수 없고 대신 업로드한 시뮬레이트된 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-433">Choosing "Simulation" disables the real sensors on your HoloLens and uses uploaded simulated data instead.</span></span> <span data-ttu-id="372ca-434">"시뮬레이션"으로 전환하면 HoloLens가 "기본"으로 다시 전환될 때까지 실제 사용자에게 응답하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-434">If you switch to "Simulation", your HoloLens will not respond to the real user until you switch back to "Default".</span></span>

### <a name="networking"></a><span data-ttu-id="372ca-435">네트워킹</span><span class="sxs-lookup"><span data-stu-id="372ca-435">Networking</span></span>

<span data-ttu-id="372ca-436">![Microsoft HoloLens에 대한 Windows 장치 포털의 네트워킹 페이지](images/using-windows-portal-img-17.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-436">![Networking page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-17.png)</span></span><br>
<span data-ttu-id="372ca-437">*Microsoft HoloLens에 대한 Windows 장치 포털의 네트워킹 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-437">*Networking page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="372ca-438">HoloLens에서 Wi-Fi 연결을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-438">Manages Wi-Fi connections on the HoloLens.</span></span>
* <span data-ttu-id="372ca-439">**WiFi 어댑터**: 드롭다운 컨트롤을 사용하여 Wi-Fi 어댑터 및 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-439">**WiFi adapters**: Select a Wi-Fi adapter and profile by using the dropdown controls.</span></span> <span data-ttu-id="372ca-440">**연결**을 클릭하거나 탭하여 선택한 어댑터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-440">Click or tap **Connect** to use the selected adapter.</span></span>
* <span data-ttu-id="372ca-441">**사용 가능한 네트워크**: HoloLens가 연결할 수 있는 Wi-Fi 네트워크를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-441">**Available networks**: Lists the Wi-Fi networks that the HoloLens can connect to.</span></span> <span data-ttu-id="372ca-442">목록을 업데이트하려면 **새로 고침**을 클릭하거나 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-442">Click or tap **Refresh** to update the list.</span></span>
* <span data-ttu-id="372ca-443">**IP 구성**: 네트워크 연결의 IP 주소 및 기타 세부 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-443">**IP configuration**: Shows the IP address and other details of the network connection.</span></span>

### <a name="virtual-input"></a><span data-ttu-id="372ca-444">가상 입력</span><span class="sxs-lookup"><span data-stu-id="372ca-444">Virtual Input</span></span>

<span data-ttu-id="372ca-445">![Microsoft HoloLens에 대한 Windows 장치 포털의 가상 입력 페이지](images/using-windows-portal-img-18.png)</span><span class="sxs-lookup"><span data-stu-id="372ca-445">![Virtual Input page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-18.png)</span></span><br>
<span data-ttu-id="372ca-446">*Microsoft HoloLens에 대한 Windows 장치 포털의 가상 입력 페이지*</span><span class="sxs-lookup"><span data-stu-id="372ca-446">*Virtual Input page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="372ca-447">원격 컴퓨터에서 HoloLens에 키보드 입력을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-447">Sends keyboard input from the remote machine to the HoloLens.</span></span>

<span data-ttu-id="372ca-448">**가상 키보드** 아래 영역을 클릭 또는 탭하여 HoloLens에 키 입력 전송을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-448">Click or tap the region under **Virtual keyboard** to enable sending keystrokes to the HoloLens.</span></span> <span data-ttu-id="372ca-449">**입력 텍스트** 텍스트 상자에 입력하고 **보내기**를 클릭 또는 탭하여 활성 앱에 키 입력을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-449">Type in the **Input text** textbox and click or tap **Send** to send the keystrokes to the active app.</span></span>

## <a name="device-portal-rest-apis"></a><span data-ttu-id="372ca-450">장치 포털 REST API</span><span class="sxs-lookup"><span data-stu-id="372ca-450">Device Portal REST API's</span></span>

<span data-ttu-id="372ca-451">장치 포털의 모든 작업은 데이터에 액세스하고 디바이스를 프로그래밍 방식으로 제어할 때 선택적으로 사용할 수 있는 [REST API](device-portal-api-reference.md)를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-451">Everything in the device portal is built on top of [REST API's](device-portal-api-reference.md) that you can optionally use to access the data and control your device programmatically.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="372ca-452">문제 해결</span><span class="sxs-lookup"><span data-stu-id="372ca-452">Troubleshooting</span></span>

### <a name="how-to-fix-the-its-lonely-here-message"></a><span data-ttu-id="372ca-453">"It's lonely here(비어 있습니다)" 메시지를 수정하는 방법</span><span class="sxs-lookup"><span data-stu-id="372ca-453">How to fix the "It's lonely here" message</span></span>

> [!NOTE]
> <span data-ttu-id="372ca-454">HoloLens 2에서 HoloLens(1세대)로 이동하면 HoloLens(1세대)에서 사용하기 전에 HoloLens 2에서 사용할 경우 페이지가 비어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-454">Going from a HoloLens 2 to HoloLens (1st gen) may cause the pages to become lonely if used on the HoloLens 2 prior to use on the HoloLens (1st gen).</span></span>

![장치 포털 페이지의 It's lonely here(비어 있습니다)](images/using-windows-portal-img-19.png)

1. <span data-ttu-id="372ca-456">왼쪽 위 메뉴에서 **레이아웃 다시 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-456">Select **Reset layout** from the top-left Menu:</span></span>

![장치 포털 메뉴에서 레이아웃 다시 설정 선택](images/using-windows-portal-img-20.png)

2. <span data-ttu-id="372ca-458">**작업 영역 다시 설정** 머리글 아래에서 **레이아웃 다시 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-458">Click **Reset layout** under the **Reset workspace** heading.</span></span> <span data-ttu-id="372ca-459">포털 페이지는 자동으로 콘텐츠를 새로 고치고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="372ca-459">The portal page will automatically refresh and display your content.</span></span>

![작업 영역 다시 설정 페이지에서 레이아웃 다시 설정 선택](images/using-windows-portal-img-21.png)
