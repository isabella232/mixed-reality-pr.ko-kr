---
title: Windows 장치 포털 사용
description: Windows 장치 포털을 사용하여 Wi-Fi 또는 USB를 통해 원격으로 디바이스를 구성하고 관리하는 방법에 대해 알아봅니다.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Windows 장치 포털, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: d772175683208ac0e3ed4b3163ca561da416c1cf
ms.sourcegitcommit: 593e8f80297ac0b5eccb2488d3f333885eab9adf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112919814"
---
# <a name="using-the-windows-device-portal"></a><span data-ttu-id="8f67e-104">Windows 장치 포털 사용</span><span class="sxs-lookup"><span data-stu-id="8f67e-104">Using the Windows Device Portal</span></span>

<table>
<tr>
<th><span data-ttu-id="8f67e-105">기능</span><span class="sxs-lookup"><span data-stu-id="8f67e-105">Feature</span></span></th><th style="width:150px"><span data-ttu-id="8f67e-106"><a href="/hololens/hololens1-hardware">HoloLens(1세대)</a></span><span class="sxs-lookup"><span data-stu-id="8f67e-106"><a href="/hololens/hololens1-hardware">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="8f67e-107">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8f67e-107">HoloLens 2</span></span></th><th style="width:150px">
</tr><tr>
<td> <span data-ttu-id="8f67e-108">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="8f67e-108">Windows Device Portal</span></span></td><td style="text-align: center;"> <span data-ttu-id="8f67e-109">✔️</span><span class="sxs-lookup"><span data-stu-id="8f67e-109">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8f67e-110">✔️</span><span class="sxs-lookup"><span data-stu-id="8f67e-110">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

<span data-ttu-id="8f67e-111">HoloLens용 Windows 장치 포털을 사용하면 Wi-Fi 또는 USB를 통해 원격으로 디바이스를 구성하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-111">The Windows Device Portal for HoloLens lets you configure and manage your device remotely over Wi-Fi or USB.</span></span> <span data-ttu-id="8f67e-112">Device Portal은 PC의 웹 브라우저에서 연결 가능한 HoloLens에 있는 웹 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-112">The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.</span></span> <span data-ttu-id="8f67e-113">장치 포털에는 HoloLens를 관리하고 앱을 디버깅 및 최적화하는 데 도움이 되는 많은 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-113">The Device Portal includes many tools that will help you manage your HoloLens and debug and optimize your apps.</span></span>

<span data-ttu-id="8f67e-114">이 설명서에서는 HoloLens용 Windows 장치 포털을 중점적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-114">This documentation is specifically about the Windows Device Portal for HoloLens.</span></span> <span data-ttu-id="8f67e-115">Windows Mixed Reality를 포함한 데스크톱용 Windows 장치 포털을 사용하려면 [Windows 장치 포털 개요](/windows/uwp/debug-test-perf/device-portal)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8f67e-115">To use the Windows Device portal for desktop (including for Windows Mixed Reality), see [Windows Device Portal overview](/windows/uwp/debug-test-perf/device-portal)</span></span>

## <a name="setting-up-hololens-to-use-windows-device-portal"></a><span data-ttu-id="8f67e-116">Windows 장치 포털을 사용하도록 HoloLens 설정</span><span class="sxs-lookup"><span data-stu-id="8f67e-116">Setting up HoloLens to use Windows Device Portal</span></span>

1. <span data-ttu-id="8f67e-117">HoloLens의 전원을 켜고 디바이스에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-117">Power on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="8f67e-118">[시작 제스처](/hololens/hololens2-basic-usage#start-gesture)(HoloLens 2) 또는 [블룸](/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)(HoloLens 1세대)을 사용하여 주 메뉴를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-118">Use the [Start gesture](/hololens/hololens2-basic-usage#start-gesture) for HoloLens2 or [Bloom](/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) on HoloLens (1st Gen) to launch the main menu.</span></span> 
3. <span data-ttu-id="8f67e-119">**설정** 타일을 응시하고 [에어 탭](/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) 제스처(HoloLens 1세대)를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-119">Gaze at the **Settings** tile and do an [air-tap](/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) gesture on HoloLens (1st Gen).</span></span> <span data-ttu-id="8f67e-120">또한 HoloLens 2에서는 [설정 타일을 터치하거나 손 광선을 사용](/hololens/hololens2-basic-usage)하는 방식으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-120">You can also select it on HoloLens 2 by [touching it or using a Hand ray](/hololens/hololens2-basic-usage).</span></span> 
4. <span data-ttu-id="8f67e-121">**업데이트** 메뉴 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-121">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="8f67e-122">**개발자용** 메뉴 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-122">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="8f67e-123">**개발자 모드** 를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-123">Enable **Developer Mode**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f67e-124">관리자가 아닌 다중 사용자인 경우 개발자 모드를 시작할 수 있는 기능이 회색으로 표시될 수 있습니다. **[디바이스에 대한 관리자](/hololens/security-adminless-os)** 인지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="8f67e-124">If you're in multi-user and not an admin, the ability to enter Developer Mode may be grayed out. Please ensure that you are an **[admin on the device](/hololens/security-adminless-os)**.</span></span>

7. <span data-ttu-id="8f67e-125">[아래로 스크롤](../../design/gaze-and-commit.md#composite-gestures)하여 **장치 포털** 을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-125">[Scroll down](../../design/gaze-and-commit.md#composite-gestures) and enable **Device Portal**.</span></span>
8. <span data-ttu-id="8f67e-126">USB 또는 Wi-Fi를 통해 이 HoloLens에 앱을 배포할 수 있도록 Windows 장치 포털을 설정하려면 **페어링** 을 선택하여 [페어링 PIN을 생성](using-visual-studio.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-126">If you're setting up Windows Device Portal so you can deploy apps to this HoloLens over USB or Wi-Fi, select **Pair** to [generate a pairing PIN](using-visual-studio.md).</span></span> <span data-ttu-id="8f67e-127">첫 번째 배포 시에는 Visual Studio에 PIN을 입력할 때까지 PIN 팝업에서 설정 앱을 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-127">Leave the Settings app at the PIN popup until you enter the PIN into Visual Studio during your first deployment.</span></span>

![Windows Holographic 설정 앱에서 개발자 모드 사용](images/using-windows-portal-img-01.jpg)

## <a name="connecting-over-wi-fi"></a><span data-ttu-id="8f67e-129">Wi-Fi를 통한 연결</span><span class="sxs-lookup"><span data-stu-id="8f67e-129">Connecting over Wi-Fi</span></span>

1. <span data-ttu-id="8f67e-130">[HoloLens를 Wi-Fi에 연결합니다](/hololens/hololens-network).</span><span class="sxs-lookup"><span data-stu-id="8f67e-130">[Connect your HoloLens to Wi-Fi](/hololens/hololens-network).</span></span>
2. <span data-ttu-id="8f67e-131">다음 중 하나를 수행하여 디바이스의 IP 주소를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-131">Look up your device's IP address by either:</span></span>
  * <span data-ttu-id="8f67e-132">**설정 > 네트워크 및 인터넷 > Wi-Fi > 고급 옵션** 으로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-132">Going to **Settings > Network & Internet > Wi-Fi > Advanced Options**.</span></span>
  * <span data-ttu-id="8f67e-133">**설정 > 네트워크 및 인터넷** 으로 차례로 이동하고, **하드웨어 속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-133">Going to **Settings > Network & Internet** and selecting **Hardware properties**.</span></span>
  * <span data-ttu-id="8f67e-134">"내 IP 주소는 무엇인가요?"</span><span class="sxs-lookup"><span data-stu-id="8f67e-134">Using the "What's my IP address?"</span></span> <span data-ttu-id="8f67e-135">음성 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-135">voice command.</span></span>

![HoloLens 2 설정](images/using-windows-portal-img-02.jpg)

3. <span data-ttu-id="8f67e-137">PC의 웹 브라우저에서 https://<YOUR_HOLOLENS_IP_ADDRESS>로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-137">From a web browser on your PC, go to https://<YOUR_HOLOLENS_IP_ADDRESS></span></span>
   * <span data-ttu-id="8f67e-138">브라우저에 다음 메시지가 표시됩니다. 장치 포털에 발급된 인증서는 테스트 인증서이므로 "이 웹 사이트의 보안 인증서에 문제가 있습니다."라는 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-138">The browser will display the following message: "There's a problem with this website's security certificate" because the certificate, which is issued to the Device Portal is a test certificate.</span></span> <span data-ttu-id="8f67e-139">지금은 이 인증서 오류를 무시하고 계속 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-139">You can ignore this certificate error for now and continue.</span></span>

## <a name="connecting-over-usb"></a><span data-ttu-id="8f67e-140">USB를 통한 연결</span><span class="sxs-lookup"><span data-stu-id="8f67e-140">Connecting over USB</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f67e-141">새 브라우저 표준에서는 포트 10080을 사용해야 하므로 이에 따라 IpOverUsb는 더 이상 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-141">IpOverUsb is no longer recommended per new browser standards as it requires the use of port 10080.</span></span> <span data-ttu-id="8f67e-142">IpOverUsb를 계속 사용하려면 Visual Studio 설치 중에 기본적으로 선택되지 않는 'USB 디바이스 연결' 상자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-142">If you still wish to use IpOverUsb, check the 'USB Device Connectivity' box during Visual Studio installation, which isn't checked by default.</span></span> <span data-ttu-id="8f67e-143">대신 HoloLens 2에서 기본적으로 지원되는 UsbNcm으로 연결하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-143">Instead, we recommend connecting with UsbNcm, which is supported by default on HoloLens 2.</span></span> <span data-ttu-id="8f67e-144">HoloLens 1을 사용하는 경우 WiFi를 사용하여 PC에 연결하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-144">If you are using a HoloLens 1, we recommend connecting to your PC using WiFi.</span></span>

1. <span data-ttu-id="8f67e-145">HoloLens 2에서 Windows Holographic 버전 21H1 이상을 실행하는 경우 설정 앱에서 '개발자용'으로 이동하여 '디바이스 검색'이 켜져 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-145">If your HoloLens 2 is running Windows Holographic version 21H1 or higher, go to 'For developers' in the Settings app and make sure that 'Device discovery' is toggled ON.</span></span> 
2. <span data-ttu-id="8f67e-146">USB-C 케이블을 사용하여 HoloLens 2를 PC에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-146">Connect your HoloLens 2 to your PC with a USB-C cable.</span></span>
3. <span data-ttu-id="8f67e-147">UsbNcm IP를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-147">Find your UsbNcm IP.</span></span> <span data-ttu-id="8f67e-148">이 작업은 몇 가지 방법을 통해 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-148">There are a few ways to do this:</span></span>
  * <span data-ttu-id="8f67e-149">디바이스의 설정 앱에서(이 방법은 '디바이스 검색'이 켜진 상태에서 Windows Holographic 버전 21H1 이상을 실행하는 HoloLenses에서만 작동합니다.)</span><span class="sxs-lookup"><span data-stu-id="8f67e-149">In the Settings app on the device (This method only works for HoloLenses running Windows Holographic version 21H1 or higher, with 'Device discovery' toggled ON.)</span></span>
    1. <span data-ttu-id="8f67e-150">디바이스의 설정 앱으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-150">Go into the Settings app on the device.</span></span>
    2. <span data-ttu-id="8f67e-151">"업데이트 및 보안" > "개발자용"으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-151">Go to "Update & Security" > "For developers."</span></span> <span data-ttu-id="8f67e-152">이것은 디바이스 포털을 사용하도록 설정한 것과 동일한 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-152">This is the same place you enabled Device Portal.</span></span>
    3. <span data-ttu-id="8f67e-153">페이지 하단에서 **이더넷** IP 주소를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-153">At the bottom of the page, copy your **Ethernet** IP address.</span></span> <span data-ttu-id="8f67e-154">UsbNcm IP입니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-154">This is your UsbNcm IP.</span></span> 
    <span data-ttu-id="8f67e-155">![HoloLens 2 설정 - UsbNcm IP](images/deviceportal_usbncm_ipaddress.jpg)</span><span class="sxs-lookup"><span data-stu-id="8f67e-155">![HoloLens 2 settings - UsbNcm IP](images/deviceportal_usbncm_ipaddress.jpg)</span></span>

  * <span data-ttu-id="8f67e-156">디바이스 포털에서</span><span class="sxs-lookup"><span data-stu-id="8f67e-156">In Device Portal</span></span> 
    1. <span data-ttu-id="8f67e-157">디바이스에서 HoloLens의 WiFi 주소를 사용하여 디바이스 포털을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-157">On your device, open Device Portal using your HoloLens' WiFi address.</span></span> <span data-ttu-id="8f67e-158">HoloLens의 WiFi 주소를 모르는 경우 "내 IP 주소는 무엇인가요?"라는 음성 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-158">If you don't know your HoloLens' WiFi address, you can use the voice command "What's my IP address?"</span></span>
    2. <span data-ttu-id="8f67e-159">시스템 > 네트워킹으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-159">Go to System > Networking</span></span>
    3. <span data-ttu-id="8f67e-160">"IP 구성" 패널의 페이지 맨 오른쪽에서 "설명: UsbNcm 기능"으로 시작하는 섹션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-160">On the far right side of the page in the "IP Configuration" panel, locate the section that starts with "Description: UsbNcm Function."</span></span>
    4. <span data-ttu-id="8f67e-161">UsbNcm IP는 "IPv4 주소" 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-161">Your UsbNcm IP is the "IPv4 address" line.</span></span> <span data-ttu-id="8f67e-162">주소를 복사하거나 주소를 클릭하기만 하면 됩니다. 이는 UsbNcm IP를 사용하여 디바이스 포털을 다시 여는 하이퍼링크입니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-162">You can copy the address or just click on the address - it is a hyperlink which will reopen Device Portal using the UsbNcm IP.</span></span>
  
  * <span data-ttu-id="8f67e-163">명령 프롬프트에서</span><span class="sxs-lookup"><span data-stu-id="8f67e-163">In a command prompt</span></span>
    1. <span data-ttu-id="8f67e-164">명령 프롬프트에서 Windows 10 SDK가 설치된 bin\<SDK version>\x86 폴더(예: C:\Program Files (x86)\Windows Kits\10\bin\10.0.19041.0\x86)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-164">In any command prompt, navigate to the bin\<SDK version>\x86 folder where your Windows 10 SDK is installed, such as C:\Program Files (x86)\Windows Kits\10\bin\10.0.19041.0\x86.</span></span>
    2. <span data-ttu-id="8f67e-165">"winappdeploycmd devices"를 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-165">Type "winappdeploycmd devices" and press Enter.</span></span>
    3. <span data-ttu-id="8f67e-166">출력에서 모델/이름 열이 HOLOLENS-xxxxxx와 같은 HoloLens 디바이스 이름인 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-166">In the output, look for the entry where the Model/Name column is your HoloLens device name, such as HOLOLENS-xxxxxx.</span></span> <span data-ttu-id="8f67e-167">UsbNcm IP는 이 줄의 시작 부분에 있으며 169.254.x.x 형식의 자동 개인 IP 주소가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-167">The UsbNcm IP is at the start of this line and will be an Automatic Private IP address in the form of 169.254.x.x.</span></span> <span data-ttu-id="8f67e-168">이 주소를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-168">Copy this address.</span></span> 
 
4. <span data-ttu-id="8f67e-169">UsbNcm IP를 복사한 경우 PC의 웹 브라우저에서 https://와 UsbNcm IP를 차례로 입력한 후 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-169">If you copied your UsbNcm IP, from a web browser on your PC go to https:// followed by your UsbNcm IP.</span></span>

### <a name="moving-files-over-usb"></a><span data-ttu-id="8f67e-170">USB를 통해 파일 이동</span><span class="sxs-lookup"><span data-stu-id="8f67e-170">Moving files over USB</span></span>

<span data-ttu-id="8f67e-171">추가 설정 없이 파일을 PC에서 HoloLens로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-171">You can move files from your PC to your HoloLens without any additional setup.</span></span>
1. <span data-ttu-id="8f67e-172">USB 코드를 사용하여 PC를 HoloLens에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-172">Connect your PC to your HoloLens with a USB cord</span></span>
2. <span data-ttu-id="8f67e-173">데스크톱에서 파일을 **PC\\[Your_HoloLens_Device_Name]\Internal Storage** 로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-173">Drag your files into **PC\\[Your_HoloLens_Device_Name]\Internal Storage** on your desktop</span></span>
3. <span data-ttu-id="8f67e-174">**시작 메뉴** 를 열고, HoloLens에서 **모든 앱 > 파일 탐색기** 를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-174">Open the **Start Menu** and select **All apps > File Explorer** on your HoloLens</span></span>

> [!NOTE]
> <span data-ttu-id="8f67e-175">"최근에 사용한 파일"에서 벗어나서 파일을 찾으려면 패널 왼쪽에서 **이 디바이스** 를 선택해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-175">You may need to select **This device** on the left side of the panel to navigate away from "Recently used" to locate your files.</span></span> 

## <a name="connecting-to-an-emulator"></a><span data-ttu-id="8f67e-176">에뮬레이터에 연결</span><span class="sxs-lookup"><span data-stu-id="8f67e-176">Connecting to an emulator</span></span>

<span data-ttu-id="8f67e-177">에뮬레이터로 장치 포털을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-177">You can also use the Device Portal with your emulator.</span></span> <span data-ttu-id="8f67e-178">장치 포털에 연결하려면 [도구 모음](using-the-hololens-emulator.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-178">To connect to the Device Portal, use the [toolbar](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="8f67e-179">다음 아이콘을 선택합니다. ![장치 포털 열기 아이콘](images/emulator-deviceportal.png) **장치 포털 열기**: 에뮬레이터에서 HoloLens OS용 Windows 디바이스 포털을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-179">Select this icon: ![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

## <a name="creating-a-username-and-password"></a><span data-ttu-id="8f67e-180">사용자 이름 및 암호 만들기</span><span class="sxs-lookup"><span data-stu-id="8f67e-180">Creating a Username and Password</span></span>

<span data-ttu-id="8f67e-181">![Windows 장치 포털에 대한 액세스 설정](images/windows-device-portal-credentials-reset-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-181">![Set up access to Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)</span></span><br>
<span data-ttu-id="8f67e-182">*Windows 장치 포털에 대한 액세스 설정*</span><span class="sxs-lookup"><span data-stu-id="8f67e-182">*Set up access to Windows Device Portal*</span></span>

<span data-ttu-id="8f67e-183">HoloLens에서 장치 포털에 처음 연결하면 사용자 이름 및 암호를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-183">The first time you connect to the Device Portal on your HoloLens, you'll need to create a username and password.</span></span>
1. <span data-ttu-id="8f67e-184">PC의 웹 브라우저에서 HoloLens의 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-184">In a web browser on your PC, enter the IP address of the HoloLens.</span></span> <span data-ttu-id="8f67e-185">액세스 설정 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-185">The Setup access page opens.</span></span>
2. <span data-ttu-id="8f67e-186">**핀 요청** 을 선택하거나 탭하고 HoloLens 디스플레이를 확인하여 생성된 PIN을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-186">Select or tap **Request pin** and look at the HoloLens display to get the generated PIN.</span></span>
3. <span data-ttu-id="8f67e-187">**디바이스에 표시된 PIN** 텍스트 상자에 PIN을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-187">Enter the PIN in the **PIN displayed on your device** textbox.</span></span>
4. <span data-ttu-id="8f67e-188">장치 포털 연결에 사용할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-188">Enter the user name you'll use to connect to the Device Portal.</span></span> <span data-ttu-id="8f67e-189">MSA(Microsoft 계정) 이름 또는 도메인 이름일 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-189">It doesn't need to be a Microsoft Account (MSA) name or a domain name.</span></span>
5. <span data-ttu-id="8f67e-190">암호를 입력하고 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-190">Enter a password and confirm it.</span></span> <span data-ttu-id="8f67e-191">암호는 7자 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-191">The password must be at least seven characters in length.</span></span> <span data-ttu-id="8f67e-192">MSA 또는 도메인 암호일 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-192">It doesn't need to be an MSA or domain password.</span></span>
6. <span data-ttu-id="8f67e-193">**연결** 을 클릭하여 HoloLens의 Windows 장치 포털에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-193">Click **Pair** to connect to Windows Device Portal on the HoloLens.</span></span>

<span data-ttu-id="8f67e-194">이 사용자 이름 또는 암호를 변경하려는 경우 언제든지 https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm으로 이동하여 디바이스 보안 페이지를 방문하면 이 프로세스를 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-194">If you wish to change this username or password at any time, you can repeat this process by visiting the device security page by  navigating to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.</span></span>

## <a name="security-certificate"></a><span data-ttu-id="8f67e-195">보안 인증서</span><span class="sxs-lookup"><span data-stu-id="8f67e-195">Security certificate</span></span>

<span data-ttu-id="8f67e-196">브라우저에 "인증서 오류"가 표시되는 경우 디바이스와 트러스트 관계를 만들어 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-196">If you see a "certificate error" in your browser, you can fix it by creating a trust relationship with the device.</span></span>

<span data-ttu-id="8f67e-197">각 HoloLens는 해당 SSL 연결에 대한 자체 서명된 인증서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-197">Each HoloLens generates a self-signed certificate for its SSL connection.</span></span> <span data-ttu-id="8f67e-198">기본적으로 이 인증서는 PC의 웹 브라우저에서 신뢰하지 않아 "인증서 오류"가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-198">By default, this certificate is not trusted by your PC's web browser and you may get a "certificate error".</span></span> <span data-ttu-id="8f67e-199">신뢰하는 Wi-Fi 네트워크 또는 USB를 통해 HoloLens에서 이 인증서를 다운로드하고 PC에서 신뢰할 수 있도록 만들어 안전하게 디바이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-199">You can securely connect to your device by downloading this certificate from your HoloLens over USB or a Wi-Fi network you trust and trusting it on your PC.</span></span>
1. <span data-ttu-id="8f67e-200">**보안된 네트워크(신뢰하는 Wi-Fi 네트워크 또는 USB)에 있는지 확인합니다.**</span><span class="sxs-lookup"><span data-stu-id="8f67e-200">**Make sure you are on a secure network (USB or a Wi-Fi network you trust).**</span></span>
2. <span data-ttu-id="8f67e-201">장치 포털의 "보안" 페이지에서 이 디바이스의 인증서를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-201">Download this device's certificate from the "Security" page on the Device Portal.</span></span>
   * <span data-ttu-id="8f67e-202"> https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-202">Navigate to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span></span>
   * <span data-ttu-id="8f67e-203">시스템 > 기본 설정에 대한 노드를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-203">Open the node for System > Preferences.</span></span> 
   * <span data-ttu-id="8f67e-204">"디바이스 보안"이 나올 때까지 아래로 스크롤하고 "이 디바이스의 인증서 다운로드" 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-204">Scroll down to Device Security, select the "Download this device's certificate" button.</span></span>
3. <span data-ttu-id="8f67e-205">PC의 "신뢰할 수 있는 루트 인증 기관" 저장소에 인증서를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-205">Install the certificate in the "Trusted Root Certification Authorities" store on your PC.</span></span>
   * <span data-ttu-id="8f67e-206">Windows 메뉴에서 컴퓨터 인증서 관리를 입력하고 애플릿을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-206">From the Windows menu, type: Manage Computer Certificates and start the applet.</span></span>
   * <span data-ttu-id="8f67e-207">**신뢰할 수 있는 루트 인증 기관** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-207">Expand the **Trusted Root Certification Authority** folder.</span></span>
   * <span data-ttu-id="8f67e-208">**인증서** 폴더를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-208">Select the **Certificates** folder.</span></span>
   * <span data-ttu-id="8f67e-209">작업 메뉴에서 모든 작업 > 가져오기...를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-209">From the Action menu, select: All Tasks > Import...</span></span>
   * <span data-ttu-id="8f67e-210">장치 포털에서 다운로드한 인증서 파일을 사용하여 인증서 가져오기 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-210">Complete the Certificate Import Wizard, using the certificate file you downloaded from the Device Portal.</span></span>
4. <span data-ttu-id="8f67e-211">브라우저를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-211">Restart the browser.</span></span>

>[!NOTE]
> <span data-ttu-id="8f67e-212">이 인증서는 디바이스에서만 신뢰할 수 있으며, 디바이스가 플래시되면 사용자가 프로세스를 다시 진행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-212">This certificate will only be trusted for the device and the user will have to go through the process again if the device is flashed.</span></span>

## <a name="sideloading-applications"></a><span data-ttu-id="8f67e-213">테스트용 로드 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="8f67e-213">Sideloading applications</span></span>

### <a name="installing-a-certificate"></a><span data-ttu-id="8f67e-214">인증서 설치</span><span class="sxs-lookup"><span data-stu-id="8f67e-214">Installing a certificate</span></span>

1. <span data-ttu-id="8f67e-215">Windows 장치 포털에서 **앱** 관리자 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-215">In Windows Device Portal, navigate to the **Apps** manager page</span></span>
2. <span data-ttu-id="8f67e-216">앱 배포 섹션에서 **인증서 설치** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-216">In the Deploy apps section, select **Install Certificate**</span></span>
3. <span data-ttu-id="8f67e-217">앱 패키지 서명에 사용되는 인증서 파일(.cer) 선택에서 파일 선택을 선택하고 테스트용으로 로드하려는 앱 패키지와 연결된 인증서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-217">Under Select certificate file (.cer) used to sign an app package, select Choose File and browse to the certificate associated with the app package that you want to sideload</span></span>
4. <span data-ttu-id="8f67e-218">**설치** 를 선택하여 설치를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-218">Select **Install** to start the installation</span></span>

![Windows 장치 포털에서 열린 앱 관리자 페이지의 스크린샷](images/sideloading-1.png)

### <a name="installing-an-app"></a><span data-ttu-id="8f67e-220">앱 설치</span><span class="sxs-lookup"><span data-stu-id="8f67e-220">Installing an app</span></span>

> [!NOTE]
> <span data-ttu-id="8f67e-221">장치 포털을 통해 앱을 설치하려면 인증서로 서명해야 합니다. 앱을 설치하기 전에 이 인증서를 디바이스에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-221">In order for an app to install successfully via Device Portal it must be signed by a certificate, this certificate must be installed to the device prior to attempting to install the app.</span></span> <span data-ttu-id="8f67e-222">지침은 [이전 섹션](#installing-a-certificate)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8f67e-222">See the [previous section](#installing-a-certificate) for instructions.</span></span>

1. <span data-ttu-id="8f67e-223">[Visual Studio에서 앱 패키지를 만들면](using-visual-studio.md) 생성된 파일에서 원격으로 디바이스에 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-223">When you've [created an app package from Visual Studio](using-visual-studio.md), you can remotely install it onto your device from the generated files:</span></span>

![앱 패키지 파일 콘텐츠의 스크린샷](images/sideloading-2.png)

2. <span data-ttu-id="8f67e-225">Windows 장치 포털에서 **앱** 관리자 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-225">In Windows Device Portal, navigate to the **Apps** manager page</span></span>
3. <span data-ttu-id="8f67e-226">앱 **배포** 섹션에서 **로컬 스토리지** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-226">In the **Deploy** apps section, select **Local Storage**</span></span>
4. <span data-ttu-id="8f67e-227">애플리케이션 패키지 선택에서 파일 선택을 선택하고 테스트용으로 로드하려는 앱 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-227">Under Select the application package, select Choose File and browse to the app package that you want to sideload</span></span>
5. <span data-ttu-id="8f67e-228">앱 설치와 함께 선택적 또는 프레임워크 패키지를 설치하려는 경우 해당 확인란을 선택하고 **다음** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-228">Check the respective boxes if you want to install optional or framework packages along with the app installation and select **Next**:</span></span>

![로컬 스토리지 탭이 강조 표시된 Windows 장치 포털에서 열린 앱 관리자 페이지의 스크린샷](images/sideloading-3.png)

6. <span data-ttu-id="8f67e-230">**설치** 를 선택하여 설치를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-230">Select **Install** to start the installation</span></span>
 
![성공적으로 설치된 Windows 장치 포털에서 열린 앱 관리자 페이지의 스크린샷](images/sideloading-4.png) 

<span data-ttu-id="8f67e-232">설치가 완료되면 HoloLens의 **모든 앱** 페이지로 돌아가서 새로 설치된 애플리케이션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-232">Once the installation is complete, go back to the **All apps** page on your HoloLens and launch your newly installed application!</span></span>

## <a name="device-portal-pages"></a><span data-ttu-id="8f67e-233">장치 포털 페이지</span><span class="sxs-lookup"><span data-stu-id="8f67e-233">Device Portal Pages</span></span>

### <a name="home"></a><span data-ttu-id="8f67e-234">홈</span><span class="sxs-lookup"><span data-stu-id="8f67e-234">Home</span></span>

<span data-ttu-id="8f67e-235">![Microsoft HoloLens에 대한 Windows 장치 포털의 홈 페이지](images/using-windows-portal-img-04.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-235">![Windows Device Portal home page on Microsoft HoloLens](images/using-windows-portal-img-04.png)</span></span><br>
<span data-ttu-id="8f67e-236">*Microsoft HoloLens에 대한 Windows 장치 포털의 홈 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-236">*Windows Device Portal home page on Microsoft HoloLens*</span></span>

<span data-ttu-id="8f67e-237">홈페이지에서 장치 포털 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-237">Your Device Portal session starts at the Home page.</span></span> <span data-ttu-id="8f67e-238">홈페이지의 왼쪽 탐색 모음에서 다른 페이지에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-238">Access other pages from the navigation bar along the left side of the home page.</span></span>

<span data-ttu-id="8f67e-239">페이지 맨 위에 있는 도구 모음에서 자주 사용하는 상태 및 기능에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-239">The toolbar at the top of the page provides access to commonly used status and features.</span></span>
* <span data-ttu-id="8f67e-240">**온라인**: 디바이스가 Wi-Fi에 연결되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-240">**Online**: Indicates whether the device is connected to Wi-Fi.</span></span>
* <span data-ttu-id="8f67e-241">**종료**: 디바이스를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-241">**Shutdown**: Turns off the device.</span></span>
* <span data-ttu-id="8f67e-242">**다시 시작**: 디바이스를 하드 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-242">**Restart**: Cycles power on the device.</span></span>
* <span data-ttu-id="8f67e-243">**보안**: 디바이스 보안 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-243">**Security**: Opens the Device Security page.</span></span>
* <span data-ttu-id="8f67e-244">**냉각**: 디바이스의 온도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-244">**Cool**: Indicates the temperature of the device.</span></span>
* <span data-ttu-id="8f67e-245">**A/C**: 디바이스가 연결되어 있고 충전 중인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-245">**A/C**: Indicates whether the device is plugged in and charging.</span></span>
* <span data-ttu-id="8f67e-246">**도움말**: REST 인터페이스 설명서 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-246">**Help**: Opens the REST interface documentation page.</span></span>

<span data-ttu-id="8f67e-247">홈페이지에는 다음 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-247">The home page shows the following info:</span></span>
* <span data-ttu-id="8f67e-248">**디바이스 상태:** 디바이스의 상태를 모니터링하고 중요한 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-248">**Device Status:** monitors the health of your device and reports critical errors.</span></span>
* <span data-ttu-id="8f67e-249">**Windows 정보:** HoloLens 이름과 현재 설치된 Windows 버전을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-249">**Windows information:** shows the name of the HoloLens and the currently installed version of Windows.</span></span>
* <span data-ttu-id="8f67e-250">**기본 설정** 섹션에는 다음 설정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-250">**Preferences** section contains the following settings:</span></span>
   * <span data-ttu-id="8f67e-251">**IPD**: 앞을 똑바로 바라볼 때 사용자의 동공 중심 사이의 거리인 IPD(동공 간 거리)를 밀리미터 단위로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-251">**IPD**: Sets the interpupillary distance (IPD) - the distance, in millimeters, between the center of the user's pupils when looking straight ahead.</span></span> <span data-ttu-id="8f67e-252">설정은 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-252">The setting takes effect immediately.</span></span> <span data-ttu-id="8f67e-253">기본값은 디바이스를 설정할 때 자동으로 계산되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-253">The default value was calculated automatically when you set up your device.</span></span>
   * <span data-ttu-id="8f67e-254">**디바이스 이름**: HoloLens에 이름을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-254">**Device name**: Assign a name to the HoloLens.</span></span> <span data-ttu-id="8f67e-255">이 값을 변경 후에는 디바이스를 다시 부팅해야 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-255">eboot the device after changing this value for it to take effect.</span></span> <span data-ttu-id="8f67e-256">**저장** 을 클릭한 후 디바이스를 즉시 다시 부팅할 것인지 또는 나중에 다시 부팅할 것인지를 묻는 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-256">After clicking **Save**, a dialog will ask if you want to reboot the device immediately or reboot later.</span></span>
   * <span data-ttu-id="8f67e-257">**절전 설정**: 디바이스가 전원에 연결된 경우 및 배터리에 연결된 경우에 각각 절전 모드로 전환되기 전에 대기할 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-257">**Sleep settings**: Sets the length of time to wait before the device goes to sleep when it's plugged in and when it's on battery.</span></span>

### <a name="3d-view"></a><span data-ttu-id="8f67e-258">3D 뷰</span><span class="sxs-lookup"><span data-stu-id="8f67e-258">3D View</span></span>

<span data-ttu-id="8f67e-259">![Microsoft HoloLens에 대한 Windows 장치 포털의 3D 뷰 페이지](images/using-windows-portal-img-05.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-259">![3D View page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-05.png)</span></span><br>
<span data-ttu-id="8f67e-260">*Microsoft HoloLens에 대한 Windows 장치 포털의 3D 뷰 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-260">*3D View page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="8f67e-261">3D 뷰 페이지를 사용하여 HoloLens가 사용자의 주변을 해석하는 방법을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-261">Use the 3D View page to see how HoloLens interprets your surroundings.</span></span> <span data-ttu-id="8f67e-262">마우스를 사용하여 뷰를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-262">Navigate the view by using the mouse:</span></span>
* <span data-ttu-id="8f67e-263">회전: 왼쪽 단추 클릭 + 마우스</span><span class="sxs-lookup"><span data-stu-id="8f67e-263">Rotate: left click + mouse;</span></span>
* <span data-ttu-id="8f67e-264">이동: 오른쪽 단추 클릭 + 마우스</span><span class="sxs-lookup"><span data-stu-id="8f67e-264">Pan: right click + mouse;</span></span>
* <span data-ttu-id="8f67e-265">확대/축소: 마우스 스크롤</span><span class="sxs-lookup"><span data-stu-id="8f67e-265">Zoom: mouse scroll.</span></span>
* <span data-ttu-id="8f67e-266">**추적 옵션**</span><span class="sxs-lookup"><span data-stu-id="8f67e-266">**Tracking options**</span></span>
   * <span data-ttu-id="8f67e-267">**강제 시각적 추적** 을 선택하여 연속 시각적 추적을 켭니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-267">Turn on continuous visual tracking by checking **Force visual tracking**.</span></span> 
   * <span data-ttu-id="8f67e-268">**일시 중지** 는 시각적 추적을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-268">**Pause** stops visual tracking.</span></span>
* <span data-ttu-id="8f67e-269">**보기 옵션**: 3D 뷰의 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-269">**View options**: Set options on the 3D view:</span></span>
  * <span data-ttu-id="8f67e-270">**추적**: 시각적 추적이 활성 상태인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-270">**Tracking**: Indicates whether visual tracking is active.</span></span>
  * <span data-ttu-id="8f67e-271">**바닥 표시**: 체크무늬 바닥 평면을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-271">**Show floor**: Displays a checkered floor plane.</span></span>
  * <span data-ttu-id="8f67e-272">**절두체 표시**: 절두체 보기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-272">**Show frustum**: Displays the view frustum.</span></span>
  * <span data-ttu-id="8f67e-273">**보정 평면 표시**: HoloLens가 동작을 안정화하는 데 사용하는 평면을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-273">**Show stabilization plane**: Displays the plane that HoloLens uses for stabilizing motion.</span></span>
  * <span data-ttu-id="8f67e-274">**메시 표시**: 사용자의 주변을 나타내는 공간 매핑 메시를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-274">**Show mesh**: Displays the spatial mapping mesh that represents your surroundings.</span></span>
  * <span data-ttu-id="8f67e-275">**공간 앵커 표시**: 활성 앱의 공간 앵커를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-275">**Show spatial anchors**: Displays spatial anchors for the active app.</span></span> <span data-ttu-id="8f67e-276">업데이트 단추를 선택하여 앵커를 가져오고 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-276">Select the Update button to get and refresh the anchors.</span></span>
  * <span data-ttu-id="8f67e-277">**자세한 정보 표시**: 실시간으로 바뀌는 손 위치, 머리 회전 사원수 및 디바이스 원점 벡터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-277">**Show details**: Displays hand positions, head rotation quaternions, and the device origin vector as they change in real time.</span></span>
  * <span data-ttu-id="8f67e-278">**전체 화면 단추**: 3D 뷰를 전체 화면 모드로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-278">**Full screen button**: Shows the 3D View in full screen mode.</span></span> <span data-ttu-id="8f67e-279">전체 화면 보기를 종료하려면 ESC 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-279">Press ESC to exit full screen view.</span></span>
* <span data-ttu-id="8f67e-280">**표면 재구성**: **업데이트** 를 클릭 또는 탭하여 디바이스에서 최신 공간 매핑 메시를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-280">**Surface reconstruction**: Select or tap **Update** to display the latest spatial mapping mesh from the device.</span></span> <span data-ttu-id="8f67e-281">전체 단계를 완료하는 데 시간이 최대 몇 초 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-281">A full pass may take some time to complete (up to a few seconds).</span></span> <span data-ttu-id="8f67e-282">메시는 3D 뷰에서 자동으로 업데이트되지 않으며 디바이스에서 수동으로 **업데이트** 를 선택해야만 최신 메시를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-282">The mesh doesn't update automatically in the 3D view, and you must manually select **Update** to get the latest mesh from the device.</span></span> <span data-ttu-id="8f67e-283">**저장** 을 선택하여 현재 공간 매핑 메시를 PC에 obj 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-283">Select **Save** to save the current spatial mapping mesh as an obj file on your PC.</span></span>
* <span data-ttu-id="8f67e-284">**공간 앵커**: 업데이트를 선택하여 활성 앱의 공간 앵커를 표시하거나 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-284">**Spatial anchors**: Select Update to display or update the spatial anchors for the active app.</span></span>

### <a name="map-manager"></a><span data-ttu-id="8f67e-285">맵 관리자</span><span class="sxs-lookup"><span data-stu-id="8f67e-285">Map Manager</span></span>

<span data-ttu-id="8f67e-286">맵 관리자를 사용하면 디바이스 간에 맵을 공유하여 위치 기반 엔터테인먼트 고객에 대한 공유 환경을 설정하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-286">Map Manager allows you to share maps across devices, which can be used to set up shared experiences for Location-Based Entertainment customers.</span></span> <span data-ttu-id="8f67e-287">이 도구를 사용하여 시스템 맵 및 앵커를 가져오고 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-287">The tool allows you to import and export system maps and anchors.</span></span>  

<span data-ttu-id="8f67e-288">맵 관리자에 액세스하려면 장치 포털에 로그인하고, **Mixed Reality -> 맵 관리자** 를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-288">To access the Map Manager, log into the Device Portal and select **Mixed Reality -> Map Manager**:</span></span> 

<span data-ttu-id="8f67e-289">![Windows 장치 포털의 맵 관리자 페이지](images/using-windows-portal-img-06.png)
*Microsoft HoloLens에 있는 Windows 장치 포털의 맵 관리자 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-289">![Map manager page in Windows Device Portal](images/using-windows-portal-img-06.png)
*Map Manager page in Windows Device Portal on Microsoft HoloLens*</span></span>

#### <a name="exporting-and-importing-maps"></a><span data-ttu-id="8f67e-290">맵 내보내기 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="8f67e-290">Exporting and importing maps</span></span>

<span data-ttu-id="8f67e-291">맵을 내보내려면 **시스템 맵 및 앵커 내보내기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-291">To export maps, select **Export System Map & Anchors**.</span></span> <span data-ttu-id="8f67e-292">이 경우 시간이 좀 걸릴 수 있으므로 맵을 내보내는 동안 30~60초 동안 기다리도록 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-292">This could take a while so be prepared to wait for 30-60 seconds while the map is exported.</span></span> <span data-ttu-id="8f67e-293">완료되면 브라우저에서 파일이 다운로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-293">Once it’s complete, the file will be downloaded in your browser.</span></span>  

<span data-ttu-id="8f67e-294">맵과 앵커를 가져오려면 **맵 파일 업로드** 및 **앵커 파일 업로드** 를 각각 선택하고, 이미 내보낸 맵 또는 앵커 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-294">To import maps and anchors, select **Upload a map file** and **Upload an anchor file** respectively and select a map or anchor file that you've already exported.</span></span> <span data-ttu-id="8f67e-295">업로드된 맵 또는 앵커 파일은 다른 HoloLens 디바이스에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-295">The uploaded map or anchor file can come from any other HoloLens device.</span></span> 

> [!NOTE]
> <span data-ttu-id="8f67e-296">HoloLens에서는 공간 매핑 데이터베이스를 가져오고 내보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-296">On HoloLens, it's also possible to import and export the spatial mapping data base.</span></span> <span data-ttu-id="8f67e-297">그러나 이 데이터베이스는 HoloLens 이외의 디바이스에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-297">However, this doesn't work on non-HoloLens devices.</span></span>  


### <a name="mixed-reality-capture"></a><span data-ttu-id="8f67e-298">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="8f67e-298">Mixed Reality Capture</span></span>

<span data-ttu-id="8f67e-299">![Microsoft HoloLens에 대한 Windows 장치 포털의 혼합 현실 캡처 페이지](images/using-windows-portal-img-07.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-299">![Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-07.png)</span></span><br>
<span data-ttu-id="8f67e-300">*Microsoft HoloLens에 대한 Windows 장치 포털의 혼합 현실 캡처 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-300">*Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="8f67e-301">혼합 현실 캡처 페이지를 사용하여 HoloLens에서 미디어 스트림을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-301">Use the Mixed Reality Capture page to save media streams from the HoloLens.</span></span>
* <span data-ttu-id="8f67e-302">**캡처 설정**: 다음 설정을 확인하여 캡처할 미디어 스트림을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-302">**Capture Settings**: Control the media streams that are captured by checking the following settings:</span></span>
  * <span data-ttu-id="8f67e-303">**홀로그램**: 비디오 스트림에서 홀로그램 콘텐츠를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-303">**Holograms**: Captures the holographic content in the video stream.</span></span> <span data-ttu-id="8f67e-304">홀로그램은 스테레오가 아닌 모노로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-304">Holograms are rendered in mono, not stereo.</span></span>
  * <span data-ttu-id="8f67e-305">**PV 카메라**: 사진/비디오 카메라에서 비디오 스트림을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-305">**PV camera**: Captures the video stream from the photo/video camera.</span></span>
  * <span data-ttu-id="8f67e-306">**마이크 오디오**: 마이크 배열에서 오디오를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-306">**Mic Audio**: Captures audio from the microphone array.</span></span>
  * <span data-ttu-id="8f67e-307">**앱 오디오**: 현재 실행 중인 앱에서 오디오를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-307">**App Audio**: Captures audio from the currently running app.</span></span>
  * <span data-ttu-id="8f67e-308">**카메라에서 렌더링**: [실행 중인 앱에서 지원](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)할 경우 캡처본을 사진/비디오 카메라 관점이 되도록 조정합니다(HoloLens 2만 해당).</span><span class="sxs-lookup"><span data-stu-id="8f67e-308">**Render from Camera**: Aligns the capture to be from the perspective of the photo/video camera, if [supported by the running app](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (HoloLens 2 only).</span></span>
  * <span data-ttu-id="8f67e-309">**실시간 미리 보기 품질**: 실시간 미리 보기의 화면 해상도, 프레임 속도 및 스트리밍 속도를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-309">**Live preview quality**: Select the screen resolution, frame rate, and streaming rate for the live preview.</span></span>
* <span data-ttu-id="8f67e-310">**오디오 설정**(HoloLens 2만 해당):</span><span class="sxs-lookup"><span data-stu-id="8f67e-310">**Audio Settings** (HoloLens 2 only):</span></span>
  * <span data-ttu-id="8f67e-311">**오디오 미디어 범주**: 마이크를 처리할 때 사용되는 범주를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-311">**Audio Media Category**: Select the category is used when processing the microphone.</span></span> <span data-ttu-id="8f67e-312">**기본** 에는 일부 환경이 포함되지만 **통신** 은 백그라운드 노이즈 취소를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-312">**Default**  will include some of the environment, while **Communications** applies background noise cancellation.</span></span>
  * <span data-ttu-id="8f67e-313">**앱 오디오 게인**: 앱 오디오의 볼륨에 적용되는 게인입니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-313">**App Audio Gain**: The gain applied to app audio's volume.</span></span>
  * <span data-ttu-id="8f67e-314">**마이크 오디오 게인**: 마이크 오디오의 볼륨에 적용되는 게인입니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-314">**Mic Audio Gain**: The gain applied to mic audio's volume.</span></span>
* <span data-ttu-id="8f67e-315">**사진 및 비디오 설정**(HoloLens 2, 버전 2004 이상):</span><span class="sxs-lookup"><span data-stu-id="8f67e-315">**Photo and Video Settings** (HoloLens 2, version 2004 or later):</span></span>
  * <span data-ttu-id="8f67e-316">**캡처 프로필**: 사진과 비디오를 촬영할 때 사용할 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-316">**Capture Profile**: Select the profile used when taking photos and videos.</span></span> <span data-ttu-id="8f67e-317">프로필은 사용할 수 있는 해상도와 프레임 비율을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-317">The profile determines which resolutions and frame-rates are available.</span></span>
  * <span data-ttu-id="8f67e-318">**사진 해상도**: 사진을 촬영하는 해상도입니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-318">**Photo Resolution**: The resolution the photo will be taken with.</span></span>
  * <span data-ttu-id="8f67e-319">**비디오 해상도 및 프레임 비율**: 촬영하는 비디오의 해상도와 프레임 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-319">**Video Resolution and Frame-rate**: The resolution and frame-rate the video will be taken with.</span></span>
  * <span data-ttu-id="8f67e-320">**비디오 안정화 버퍼**: 비디오를 촬영할 때 사용되는 버퍼 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-320">**Video Stabilization Buffer**: The buffer size used when taking a video.</span></span> <span data-ttu-id="8f67e-321">값이 클수록 빠른 움직임에 맞게 보정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-321">The higher the value, the better it can compensate for quick movements.</span></span>
* <span data-ttu-id="8f67e-322">**실시간 미리 보기** 단추를 선택하거나 탭하여 캡처 스트림을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-322">Select or tap the **Live preview** button to show the capture stream.</span></span> <span data-ttu-id="8f67e-323">**실시간 미리 보기 중지** 는 캡처 스트림을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-323">**Stop live preview** stops the capture stream.</span></span>
* <span data-ttu-id="8f67e-324">**녹화** 를 선택하거나 탭하여 지정된 설정을 사용해 혼합 현실 스트림의 녹화를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-324">Select or tap **Record** to start recording the mixed-reality stream, using the specified settings.</span></span> <span data-ttu-id="8f67e-325">**녹화 정지** 는 녹화를 끝내고 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-325">**Stop recording** ends the recording and saves it.</span></span>
* <span data-ttu-id="8f67e-326">**사진 촬영** 을 선택하거나 탭하여 캡처 스트림에서 정지 이미지를 촬영합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-326">Select or tap **Take photo** to take a still image from the capture stream.</span></span>
* <span data-ttu-id="8f67e-327">**기본 설정 복원** 을 선택하거나 탭하여 오디오, 사진 및 비디오 설정에 기본 설정을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-327">Select or tap **Restore Default Settings** to restore the default settings for audio, photo, and video settings.</span></span>
* <span data-ttu-id="8f67e-328">**비디오 및 사진**: 디바이스에서 촬영한 비디오 및 사진 캡처 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-328">**Videos and photos**: Shows a list of video and photo captures taken on the device.</span></span>

<span data-ttu-id="8f67e-329">이 페이지의 모든 설정은 Windows 장치 포털을 사용하여 만든 캡처에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-329">All settings on this page apply to captures taken using Windows Device Portal.</span></span> <span data-ttu-id="8f67e-330">일부 설정은 시작 메뉴, 하드웨어 단추, 글로벌 음성 명령, Miracast 및 사용자 지정 MRC 레코더를 비롯한 시스템 MRC에 추가로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-330">Some additionally apply to System MRC, including start menu, hardware buttons, global voice commands, Miracast, and custom MRC Recorders.</span></span>

|  <span data-ttu-id="8f67e-331">설정</span><span class="sxs-lookup"><span data-stu-id="8f67e-331">Setting</span></span>  |  <span data-ttu-id="8f67e-332">시스템 MRC에 적용</span><span class="sxs-lookup"><span data-stu-id="8f67e-332">Applies to System MRC</span></span>  |  <span data-ttu-id="8f67e-333">사용자 지정 MRC 레코더에 적용</span><span class="sxs-lookup"><span data-stu-id="8f67e-333">Applies to Custom MRC Recorders</span></span> |
|----------|----------|----------|
|  <span data-ttu-id="8f67e-334">홀로그램</span><span class="sxs-lookup"><span data-stu-id="8f67e-334">Holograms</span></span>  |  <span data-ttu-id="8f67e-335">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-335">No</span></span>  |  <span data-ttu-id="8f67e-336">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-336">No</span></span> |
|  <span data-ttu-id="8f67e-337">PV 카메라</span><span class="sxs-lookup"><span data-stu-id="8f67e-337">PV camera</span></span>  |  <span data-ttu-id="8f67e-338">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-338">No</span></span>  |  <span data-ttu-id="8f67e-339">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-339">No</span></span> |
|  <span data-ttu-id="8f67e-340">마이크 오디오</span><span class="sxs-lookup"><span data-stu-id="8f67e-340">Mic Audio</span></span>  |  <span data-ttu-id="8f67e-341">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-341">No</span></span>  |  <span data-ttu-id="8f67e-342">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-342">No</span></span> |
|  <span data-ttu-id="8f67e-343">앱 오디오</span><span class="sxs-lookup"><span data-stu-id="8f67e-343">App Audio</span></span>  |  <span data-ttu-id="8f67e-344">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-344">No</span></span>  |  <span data-ttu-id="8f67e-345">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-345">No</span></span> |
|  <span data-ttu-id="8f67e-346">카메라에서 렌더링</span><span class="sxs-lookup"><span data-stu-id="8f67e-346">Render from Camera</span></span>  |  <span data-ttu-id="8f67e-347">예</span><span class="sxs-lookup"><span data-stu-id="8f67e-347">Yes</span></span>    |  <span data-ttu-id="8f67e-348">예(재정의할 수 있음)</span><span class="sxs-lookup"><span data-stu-id="8f67e-348">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="8f67e-349">실시간 미리 보기 품질</span><span class="sxs-lookup"><span data-stu-id="8f67e-349">Live preview quality</span></span>  |  <span data-ttu-id="8f67e-350">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-350">No</span></span>  |  <span data-ttu-id="8f67e-351">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-351">No</span></span> |
|  <span data-ttu-id="8f67e-352">오디오 미디어 범주</span><span class="sxs-lookup"><span data-stu-id="8f67e-352">Audio Media Category</span></span>  |  <span data-ttu-id="8f67e-353">예</span><span class="sxs-lookup"><span data-stu-id="8f67e-353">Yes</span></span>  |  <span data-ttu-id="8f67e-354">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-354">No</span></span> |
|  <span data-ttu-id="8f67e-355">앱 오디오 게인</span><span class="sxs-lookup"><span data-stu-id="8f67e-355">App Audio Gain</span></span>  |  <span data-ttu-id="8f67e-356">예</span><span class="sxs-lookup"><span data-stu-id="8f67e-356">Yes</span></span>  |  <span data-ttu-id="8f67e-357">예(재정의할 수 있음)</span><span class="sxs-lookup"><span data-stu-id="8f67e-357">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="8f67e-358">마이크 오디오 게인</span><span class="sxs-lookup"><span data-stu-id="8f67e-358">Mic Audio Gain</span></span>  |  <span data-ttu-id="8f67e-359">예</span><span class="sxs-lookup"><span data-stu-id="8f67e-359">Yes</span></span>  |  <span data-ttu-id="8f67e-360">예(재정의할 수 있음)</span><span class="sxs-lookup"><span data-stu-id="8f67e-360">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="8f67e-361">캡처 프로필</span><span class="sxs-lookup"><span data-stu-id="8f67e-361">Capture Profile</span></span>  |  <span data-ttu-id="8f67e-362">예</span><span class="sxs-lookup"><span data-stu-id="8f67e-362">Yes</span></span>  |  <span data-ttu-id="8f67e-363">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-363">No</span></span> |
|  <span data-ttu-id="8f67e-364">사진 해상도</span><span class="sxs-lookup"><span data-stu-id="8f67e-364">Photo Resolution</span></span>  |  <span data-ttu-id="8f67e-365">예</span><span class="sxs-lookup"><span data-stu-id="8f67e-365">Yes</span></span>  |  <span data-ttu-id="8f67e-366">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-366">No</span></span> |
|  <span data-ttu-id="8f67e-367">비디오 해상도 및 프레임 비율</span><span class="sxs-lookup"><span data-stu-id="8f67e-367">Video Resolution and Frame-rate</span></span>  |  <span data-ttu-id="8f67e-368">예</span><span class="sxs-lookup"><span data-stu-id="8f67e-368">Yes</span></span>  |  <span data-ttu-id="8f67e-369">아니요</span><span class="sxs-lookup"><span data-stu-id="8f67e-369">No</span></span> |
|  <span data-ttu-id="8f67e-370">비디오 안정화 버퍼</span><span class="sxs-lookup"><span data-stu-id="8f67e-370">Video Stabilization Buffer</span></span>  |  <span data-ttu-id="8f67e-371">예</span><span class="sxs-lookup"><span data-stu-id="8f67e-371">Yes</span></span>  |  <span data-ttu-id="8f67e-372">예(재정의할 수 있음)</span><span class="sxs-lookup"><span data-stu-id="8f67e-372">Yes (can be overridden)</span></span> |

> [!NOTE]
> <span data-ttu-id="8f67e-373">[동시 MRC에 대한 제한 사항](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-373">There are [limitations to simultaneous MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span></span>
> * <span data-ttu-id="8f67e-374">Windows 장치 포털이 비디오를 녹화하는 동안 앱에서 사진/비디오 카메라에 액세스하려고 하면 비디오 녹화가 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-374">If an app tries to access the photo/video camera while Windows Device Portal is recording a video, the video recording will stop.</span></span>
>   * <span data-ttu-id="8f67e-375">앱이 SharedReadOnly 모드를 사용하여 사진/비디오 카메라에 액세스하는 경우 HoloLens 2는 비디오 녹화를 중지하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-375">HoloLens 2 will not stop recording video if the app accesses the photo/video camera with SharedReadOnly mode.</span></span>
> * <span data-ttu-id="8f67e-376">앱이 현재 사진/비디오 카메라를 사용하는 경우 Windows 장치 포털에서 사진을 촬영하거나 비디오를 녹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-376">If an app is actively using the photo/video camera, Windows Device Portal is able to take a photo or record a video.</span></span>
> * <span data-ttu-id="8f67e-377">라이브 스트리밍:</span><span class="sxs-lookup"><span data-stu-id="8f67e-377">Live streaming:</span></span>
>   * <span data-ttu-id="8f67e-378">HoloLens(1세대)는 Windows 장치 포털에서 라이브 스트리밍 중에 앱이 사진/비디오 카메라에 액세스하지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-378">HoloLens (1st gen) prevents an app from accessing the photo/video camera while live streaming from Windows Device Portal.</span></span>
>   * <span data-ttu-id="8f67e-379">HoloLens(1세대)는 앱이 현재 사진/비디오 카메라를 사용하는 경우 라이브 스트리밍에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-379">HoloLens (1st gen) will fail to live stream if an app is actively using the photo/video camera.</span></span>
>   * <span data-ttu-id="8f67e-380">HoloLens 2는 앱이 ExclusiveControl 모드에서 사진/비디오 카메라에 액세스하려고 하면 라이브 스트리밍을 자동으로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-380">HoloLens 2 automatically stops live streaming when an app tries to access the photo/video camera in ExclusiveControl mode.</span></span>
>   * <span data-ttu-id="8f67e-381">HoloLens 2는 앱이 현재 PV 카메라를 사용 중인 경우 라이브 스트림을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-381">HoloLens 2 is able to start a live stream while an app is actively using the PV camera.</span></span>

### <a name="performance-tracing"></a><span data-ttu-id="8f67e-382">성능 추적</span><span class="sxs-lookup"><span data-stu-id="8f67e-382">Performance Tracing</span></span>

<span data-ttu-id="8f67e-383">![Microsoft HoloLens에 대한 Windows 장치 포털의 성능 추적 페이지](images/using-windows-portal-img-08.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-383">![Performance Tracing page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-08.png)</span></span><br>
<span data-ttu-id="8f67e-384">*Microsoft HoloLens에 대한 Windows 장치 포털의 성능 추적 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-384">*Performance Tracing page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="8f67e-385">HoloLens에서 [WPR(Windows Performance Recorder)](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448205(v=win.10)) 추적을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-385">Capture [Windows Performance Recorder](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448205(v=win.10)) (WPR) traces from your HoloLens.</span></span>
* <span data-ttu-id="8f67e-386">**사용 가능한 프로필**: 드롭다운 목록에서 WPR 프로필을 선택하고 **시작** 을 선택하거나 탭하여 추적을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-386">**Available profiles**: Select the WPR profile from the dropdown, and select or tap **Start** to start tracing.</span></span>
* <span data-ttu-id="8f67e-387">**사용자 지정 프로필**: PC에서 WPR 프로필을 선택하려면 **찾아보기** 를 선택하거나 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-387">**Custom profiles**: Select or tap **Browse** to choose a WPR profile from your PC.</span></span> <span data-ttu-id="8f67e-388">추적을 시작하려면 **업로드 및 시작** 을 선택하거나 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-388">Select or tap **Upload and start** to start tracing.</span></span>

<span data-ttu-id="8f67e-389">추적을 중지하려면 중지 링크를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-389">To stop the trace, select the stop link.</span></span> <span data-ttu-id="8f67e-390">추적 파일이 다운로드를 완료할 때까지 이 페이지에 계속 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-390">Stay on this page until the trace file has completed downloading.</span></span>

<span data-ttu-id="8f67e-391">캡처된 ETL 파일은 [Windows Performance Analyzer](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448170(v=win.10))에서 분석을 위해 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-391">Captured ETL files can be opened for analysis in [Windows Performance Analyzer](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448170(v=win.10)).</span></span>

### <a name="processes"></a><span data-ttu-id="8f67e-392">프로세스</span><span class="sxs-lookup"><span data-stu-id="8f67e-392">Processes</span></span>

<span data-ttu-id="8f67e-393">![Microsoft HoloLens에 대한 Windows 장치 포털의 프로세스 페이지](images/using-windows-portal-img-09.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-393">![Processes page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-09.png)</span></span><br>
<span data-ttu-id="8f67e-394">*Microsoft HoloLens에 대한 Windows 장치 포털의 프로세스 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-394">*Processes page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="8f67e-395">현재 실행 중인 프로세스에 대한 세부 정보를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-395">Shows details about currently running processes.</span></span> <span data-ttu-id="8f67e-396">앱 및 시스템 프로세스 모두 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-396">This includes both apps and system processes.</span></span>

### <a name="system-performance"></a><span data-ttu-id="8f67e-397">시스템 성능</span><span class="sxs-lookup"><span data-stu-id="8f67e-397">System Performance</span></span>

<span data-ttu-id="8f67e-398">![Microsoft HoloLens에 대한 Windows 장치 포털의 시스템 성능 페이지](images/using-windows-portal-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-398">![System Performance page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-10.png)</span></span><br>
<span data-ttu-id="8f67e-399">*Microsoft HoloLens에 대한 Windows 장치 포털의 시스템 성능 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-399">*System Performance page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="8f67e-400">전력 사용량, 프레임 속도 및 CPU 로드와 같은 시스템 진단 정보를 실시간 그래프로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-400">Shows real-time graphs of system diagnostic info, like power usage, frame rate, and CPU load.</span></span>

<span data-ttu-id="8f67e-401">사용 가능한 메트릭은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-401">These are the available metrics:</span></span>
* <span data-ttu-id="8f67e-402">**SoC 전원**: 순간 시스템 온칩 전력 사용률 1분 평균</span><span class="sxs-lookup"><span data-stu-id="8f67e-402">**SoC power**: Instantaneous system-on-chip power usage, averaged over one minute</span></span>
* <span data-ttu-id="8f67e-403">**시스템 전원**: 순간 시스템 전력 사용률 1분 평균</span><span class="sxs-lookup"><span data-stu-id="8f67e-403">**System power**: Instantaneous system power usage, averaged over one minute</span></span>
* <span data-ttu-id="8f67e-404">**프레임 속도**: 초당 프레임, 초당 누락 VBlank 및 연속 누락 VBlank</span><span class="sxs-lookup"><span data-stu-id="8f67e-404">**Frame rate**: Frames per second, missed VBlanks per second, and consecutive missed VBlanks</span></span>
* <span data-ttu-id="8f67e-405">**GPU**: GPU 엔진 사용률(사용 가능한 총 전원 대비 백분율)</span><span class="sxs-lookup"><span data-stu-id="8f67e-405">**GPU**: GPU engine usage, percent of total available</span></span>
* <span data-ttu-id="8f67e-406">**CPU**: 사용 가능한 총 전원 대비 백분율</span><span class="sxs-lookup"><span data-stu-id="8f67e-406">**CPU**: percent of total available</span></span>
* <span data-ttu-id="8f67e-407">**I/O**: 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="8f67e-407">**I/O**: Reads and writes</span></span>
* <span data-ttu-id="8f67e-408">**네트워크**: 수신 및 전송</span><span class="sxs-lookup"><span data-stu-id="8f67e-408">**Network**: Received and sent</span></span>
* <span data-ttu-id="8f67e-409">**메모리**: 전체, 사용 중, 약정, 페이징 및 비페이징 메모리</span><span class="sxs-lookup"><span data-stu-id="8f67e-409">**Memory**: Total, in use, committed, paged, and non-paged</span></span>

### <a name="apps"></a><span data-ttu-id="8f67e-410">앱</span><span class="sxs-lookup"><span data-stu-id="8f67e-410">Apps</span></span>

<span data-ttu-id="8f67e-411">![Microsoft HoloLens에 대한 Windows 장치 포털의 앱 페이지](images/using-windows-portal-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-411">![Apps page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-11.png)</span></span><br>
<span data-ttu-id="8f67e-412">*Microsoft HoloLens에 대한 Windows 장치 포털의 앱 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-412">*Apps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="8f67e-413">HoloLens에 설치된 앱을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-413">Manages the apps that are installed on the HoloLens.</span></span>
* <span data-ttu-id="8f67e-414">**설치된 앱**: 앱을 제거하고 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-414">**Installed apps**: Remove and start apps.</span></span>
* <span data-ttu-id="8f67e-415">**실행 중인 앱**: 현재 실행 중인 앱을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-415">**Running apps**: Lists apps that are running currently.</span></span>
* <span data-ttu-id="8f67e-416">**앱 설치**: 컴퓨터/네트워크 폴더에서 설치할 앱 패키지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-416">**Install app**: Select app packages for installation from a folder on your computer/network.</span></span>
* <span data-ttu-id="8f67e-417">**종속성**: 설치하려는 앱에 대한 종속성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-417">**Dependency**: Add dependencies for the app you're going to install.</span></span>
* <span data-ttu-id="8f67e-418">**배포**: 선택한 앱 + 종속성을 HoloLens에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-418">**Deploy**: Deploy the selected app + dependencies to the HoloLens.</span></span>

### <a name="app-crash-dumps"></a><span data-ttu-id="8f67e-419">앱 크래시 덤프</span><span class="sxs-lookup"><span data-stu-id="8f67e-419">App Crash Dumps</span></span>

<span data-ttu-id="8f67e-420">![Microsoft HoloLens에 대한 Windows 장치 포털의 앱 크래시 덤프 페이지](images/using-windows-portal-img-12.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-420">![App Crash Dumps page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-12.png)</span></span><br>
<span data-ttu-id="8f67e-421">*Microsoft HoloLens에 대한 Windows 장치 포털의 앱 크래시 덤프 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-421">*App Crash Dumps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="8f67e-422">이 페이지에서는 테스트용으로 로드된 앱에 대한 크래시 덤프를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-422">This page allows you to collect crash dumps for your side-loaded apps.</span></span> <span data-ttu-id="8f67e-423">크래시 덤프를 수집하려는 각 앱에 대해 **크래시 덤프 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-423">Check the **Crash Dumps Enabled** checkbox for each app for which you want to collect crash dumps.</span></span> <span data-ttu-id="8f67e-424">이 페이지로 돌아와서 크래시 덤프를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-424">Return to this page to collect crash dumps.</span></span> <span data-ttu-id="8f67e-425">덤프 파일은 [디버깅을 위해 Visual Studio에서 열릴 수 있습니다](/previous-versions/visualstudio/visual-studio-2015/debugger/using-dump-files).</span><span class="sxs-lookup"><span data-stu-id="8f67e-425">Dump files can be [opened in Visual Studio for debugging](/previous-versions/visualstudio/visual-studio-2015/debugger/using-dump-files).</span></span>

### <a name="file-explorer"></a><span data-ttu-id="8f67e-426">파일 탐색기</span><span class="sxs-lookup"><span data-stu-id="8f67e-426">File Explorer</span></span>

<span data-ttu-id="8f67e-427">![Microsoft HoloLens에 대한 Windows 장치 포털의 파일 탐색기 페이지](images/using-windows-portal-img-13.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-427">![File Explorer page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-13.png)</span></span><br>
<span data-ttu-id="8f67e-428">*Microsoft HoloLens에 대한 Windows 장치 포털의 파일 탐색기 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-428">*File Explorer page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="8f67e-429">파일 탐색기를 사용하여 파일을 찾아보고, 업로드하고, 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-429">Use the file explorer to browse, upload, and download files.</span></span> <span data-ttu-id="8f67e-430">문서 폴더, 그림 폴더 및 Visual Studio 또는 장치 포털에서 배포한 앱에 대한 로컬 스토리지 폴더의 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-430">You can work with files in the Documents folder, Pictures folder, and in the local storage folders for apps that you deployed from Visual Studio or the Device Portal.</span></span>

### <a name="kiosk-mode"></a><span data-ttu-id="8f67e-431">키오스크 모드</span><span class="sxs-lookup"><span data-stu-id="8f67e-431">Kiosk Mode</span></span>

>[!NOTE]
><span data-ttu-id="8f67e-432">키오스크 모드는 [Microsoft HoloLens Commercial Suite](/hololens/hololens-commercial-features)에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-432">Kiosk mode is only available with the [Microsoft HoloLens Commercial Suite](/hololens/hololens-commercial-features).</span></span>

![Microsoft HoloLens에 있는 Windows 장치 포털의 키오스크 모드 페이지](images/using-windows-portal-img-14.png)

<span data-ttu-id="8f67e-434">Windows 장치 포털을 통해 키오스크 모드를 사용하도록 설정하는 방법에 대한 최신 지침은 Windows IT 전문가 센터의 [키오스크 모드로 HoloLens 설정 ](/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) 문서를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="8f67e-434">Check the [Set up HoloLens in kiosk mode](/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) article in Windows IT Pro Center for up-to-date instructions on enabling kiosk mode via Windows Device Portal.</span></span>

### <a name="logging"></a><span data-ttu-id="8f67e-435">로깅</span><span class="sxs-lookup"><span data-stu-id="8f67e-435">Logging</span></span>

<span data-ttu-id="8f67e-436">![Microsoft HoloLens에 대한 Windows 장치 포털의 로깅 페이지](images/using-windows-portal-img-15.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-436">![Logging page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-15.png)</span></span><br>
<span data-ttu-id="8f67e-437">*Microsoft HoloLens에 대한 Windows 장치 포털의 로깅 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-437">*Logging page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="8f67e-438">HoloLens에서 실시간 ETW(Windows용 이벤트 추적)를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-438">Manages real-time Event Tracing for Windows (ETW) on the HoloLens.</span></span>

<span data-ttu-id="8f67e-439">**이벤트 목록** 만 표시하려면 **공급자 숨기기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-439">Check **Hide providers** to show the **Events** list only.</span></span>
* <span data-ttu-id="8f67e-440">**등록된 공급자**: ETW 공급자와 추적 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-440">**Registered providers**: Select the ETW provider and the tracing level.</span></span> <span data-ttu-id="8f67e-441">추적 수준은 다음 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-441">Tracing level is one of these values:</span></span>
   1. <span data-ttu-id="8f67e-442">비정상적인 끝내기 또는 종료</span><span class="sxs-lookup"><span data-stu-id="8f67e-442">Abnormal exit or termination</span></span>
   2. <span data-ttu-id="8f67e-443">심각한 오류</span><span class="sxs-lookup"><span data-stu-id="8f67e-443">Severe errors</span></span>
   3. <span data-ttu-id="8f67e-444">경고</span><span class="sxs-lookup"><span data-stu-id="8f67e-444">Warnings</span></span>
   4. <span data-ttu-id="8f67e-445">오류가 아닌 경고</span><span class="sxs-lookup"><span data-stu-id="8f67e-445">Non-error warnings</span></span>

<span data-ttu-id="8f67e-446">추적을 시작하려면 **사용** 을 선택하거나 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-446">Select or tap **Enable** to start tracing.</span></span> <span data-ttu-id="8f67e-447">공급자가 **활성화된 공급자** 드롭다운에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-447">The provider is added to the **Enabled Providers** dropdown.</span></span>
* <span data-ttu-id="8f67e-448">**사용자 지정 공급자**: 사용자 지정 ETW 공급자와 추적 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-448">**Custom providers**: Select a custom ETW provider and the tracing level.</span></span> <span data-ttu-id="8f67e-449">공급자를 GUID로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-449">Identify the provider by its GUID.</span></span> <span data-ttu-id="8f67e-450">GUID에 대괄호를 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="8f67e-450">Don't include brackets in the GUID.</span></span>
* <span data-ttu-id="8f67e-451">**활성화된 공급자**: 활성화된 공급자를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-451">**Enabled providers**: Lists the enabled providers.</span></span> <span data-ttu-id="8f67e-452">추적을 중지하려면 드롭다운에서 공급자를 선택하고 **사용 안 함** 을 클릭 또는 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-452">Select a provider from the dropdown and click or tap **Disable** to stop tracing.</span></span> <span data-ttu-id="8f67e-453">모든 추적을 일시 중단하려면 **모두 중지** 를 클릭 또는 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-453">Click or tap **Stop all** to suspend all tracing.</span></span>
* <span data-ttu-id="8f67e-454">**공급자 기록**: 현재 세션 중 활성화된 ETW 공급자를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-454">**Providers history**: Shows the ETW providers that were enabled during the current session.</span></span> <span data-ttu-id="8f67e-455">비활성화된 공급자를 활성화하려면 **사용** 을 클릭 또는 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-455">Click or tap **Enable** to activate a provider that was disabled.</span></span> <span data-ttu-id="8f67e-456">기록을 지우려면 **지우기** 를 클릭 또는 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-456">Click or tap **Clear** to clear the history.</span></span>
* <span data-ttu-id="8f67e-457">**이벤트**: 선택된 공급자의 ETW 이벤트를 표 형식으로 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-457">**Events**: Lists ETW events from the selected providers in table format.</span></span> <span data-ttu-id="8f67e-458">이 표는 실시간으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-458">This table is updated in real time.</span></span> <span data-ttu-id="8f67e-459">모든 ETW 이벤트를 표에서 삭제하려면 표 아래에 있는 **지우기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-459">Beneath the table, click the **Clear** button to delete all ETW events from the table.</span></span> <span data-ttu-id="8f67e-460">이렇게 해도 공급자는 비활성화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-460">This doesn't disable any providers.</span></span> <span data-ttu-id="8f67e-461">**파일로 저장** 을 클릭하여 현재 수집된 ETW 이벤트를 CSV 파일에 로컬로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-461">You can click **Save to file** to export the currently collected ETW events to a CSV file locally.</span></span>
* <span data-ttu-id="8f67e-462">**필터**: 수집된 ETW 이벤트를 ID, 키워드, 수준, 공급자 이름, 작업 이름 또는 텍스트로 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-462">**Filters**: Allow you to filter the ETW events collected by ID, Keyword, Level, Provider Name, Task Name, or Text.</span></span> <span data-ttu-id="8f67e-463">여러 조건을 함께 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-463">You can combine several criteria together:</span></span>
   1. <span data-ttu-id="8f67e-464">동일한 속성에 적용되는 조건의 경우 이러한 조건 중 하나라도 만족하는 이벤트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-464">For criteria applying to the same property, events that can satisfy any one of these criteria are shown.</span></span>
   2. <span data-ttu-id="8f67e-465">다른 속성에 적용되는 조건의 경우 이벤트가 모든 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-465">For criteria applying to a different property, events must satisfy all of the criteria</span></span>

<span data-ttu-id="8f67e-466">예를 들어 *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')* 기준을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-466">For example, you can specify the criteria *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span></span>

### <a name="simulation"></a><span data-ttu-id="8f67e-467">Simulation</span><span class="sxs-lookup"><span data-stu-id="8f67e-467">Simulation</span></span>

<span data-ttu-id="8f67e-468">![Microsoft HoloLens에 대한 Windows 장치 포털의 시뮬레이션 페이지](images/using-windows-portal-img-16.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-468">![Simulation page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-16.png)</span></span><br>
<span data-ttu-id="8f67e-469">*Microsoft HoloLens에 대한 Windows 장치 포털의 시뮬레이션 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-469">*Simulation page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="8f67e-470">테스트를 위해 입력 데이터를 기록 및 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-470">Allows you to record and play back input data for testing.</span></span>
* <span data-ttu-id="8f67e-471">**공간 캡처**: 사용자의 주변에 대한 공간 매핑 메시를 포함하는 시뮬레이트된 공간 파일을 다운로드하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-471">**Capture room**: Used to download a simulated room file that contains the spatial mapping mesh for the user's surroundings.</span></span> <span data-ttu-id="8f67e-472">공간의 이름을 지정한 다음, **캡처** 를 클릭하여 PC에 .xef 파일로 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-472">Name the room and then click **Capture** to save the data as an .xef file on your PC.</span></span> <span data-ttu-id="8f67e-473">이 공간 파일을 HoloLens 에뮬레이터에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-473">This room file can be loaded into the HoloLens emulator.</span></span>
* <span data-ttu-id="8f67e-474">**녹화**: 녹화할 스트림을 선택하고 녹화본의 이름을 지정하고 **녹화** 를 클릭 또는 탭하여 녹화를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-474">**Recording**: Check the streams to record, name the recording, and click or tap **Record** to start recoding.</span></span> <span data-ttu-id="8f67e-475">HoloLens를 사용하여 작업을 수행한 다음, **중지** 를 클릭하여 PC에 .xef 파일로 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-475">Perform actions with your HoloLens and then click **Stop** to save the data as an .xef file on your PC.</span></span> <span data-ttu-id="8f67e-476">이 파일을 HoloLens 에뮬레이터 또는 디바이스에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-476">This file can be loaded on the HoloLens emulator or device.</span></span>
  >[!NOTE]
  ><span data-ttu-id="8f67e-477">녹음 기능은 현재 HoloLens 1세대에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-477">The Recording feature is currently only available on the HoloLens 1st gen.</span></span> <span data-ttu-id="8f67e-478">HoloLens 2에서는 아직 녹음이 지원되지 않지만 기존 녹음의 재생은 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-478">Recording is not yet supported on HoloLens 2, but Playback of existing recordings is supported.</span></span>
* <span data-ttu-id="8f67e-479">**재생**: **녹화본 업로드** 를 클릭 또는 탭하여 PC에서 xef 파일을 선택하고 HoloLens에 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-479">**Playback**: Click or tap **Upload recording** to select a xef file from your PC and send the data to the HoloLens.</span></span>
* <span data-ttu-id="8f67e-480">**제어 모드**: 드롭다운 목록에서 **기본** 또는 **시뮬레이션** 을 선택하고 **설정** 단추를 클릭 또는 탭하여 HoloLens의 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-480">**Control mode**: Select **Default** or **Simulation** from the dropdown, and click or tap the **Set** button to select the mode on the HoloLens.</span></span> <span data-ttu-id="8f67e-481">"시뮬레이션"을 선택하면 HoloLens의 실제 센서를 사용할 수 없고 대신 업로드한 시뮬레이트된 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-481">Choosing "Simulation" disables the real sensors on your HoloLens and uses uploaded simulated data instead.</span></span> <span data-ttu-id="8f67e-482">"시뮬레이션"으로 전환하면 HoloLens가 "기본"으로 다시 전환될 때까지 실제 사용자에게 응답하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-482">If you switch to "Simulation", your HoloLens won't respond to the real user until you switch back to "Default".</span></span>

### <a name="networking"></a><span data-ttu-id="8f67e-483">네트워킹</span><span class="sxs-lookup"><span data-stu-id="8f67e-483">Networking</span></span>

<span data-ttu-id="8f67e-484">![Microsoft HoloLens에 대한 Windows 장치 포털의 네트워킹 페이지](images/using-windows-portal-img-17.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-484">![Networking page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-17.png)</span></span><br>
<span data-ttu-id="8f67e-485">*Microsoft HoloLens에 대한 Windows 장치 포털의 네트워킹 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-485">*Networking page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="8f67e-486">HoloLens에서 Wi-Fi 연결을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-486">Manages Wi-Fi connections on the HoloLens.</span></span>
* <span data-ttu-id="8f67e-487">**WiFi 어댑터**: 드롭다운 컨트롤을 사용하여 Wi-Fi 어댑터 및 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-487">**WiFi adapters**: Select a Wi-Fi adapter and profile by using the dropdown controls.</span></span> <span data-ttu-id="8f67e-488">**연결** 을 클릭하거나 탭하여 선택한 어댑터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-488">Click or tap **Connect** to use the selected adapter.</span></span>
* <span data-ttu-id="8f67e-489">**사용 가능한 네트워크**: HoloLens가 연결할 수 있는 Wi-Fi 네트워크를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-489">**Available networks**: Lists the Wi-Fi networks that the HoloLens can connect to.</span></span> <span data-ttu-id="8f67e-490">목록을 업데이트하려면 **새로 고침** 을 클릭하거나 탭합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-490">Click or tap **Refresh** to update the list.</span></span>
* <span data-ttu-id="8f67e-491">**IP 구성**: 네트워크 연결의 IP 주소 및 기타 세부 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-491">**IP configuration**: Shows the IP address and other details of the network connection.</span></span>

### <a name="virtual-input"></a><span data-ttu-id="8f67e-492">가상 입력</span><span class="sxs-lookup"><span data-stu-id="8f67e-492">Virtual Input</span></span>

<span data-ttu-id="8f67e-493">![Microsoft HoloLens에 대한 Windows 장치 포털의 가상 입력 페이지](images/using-windows-portal-img-18.png)</span><span class="sxs-lookup"><span data-stu-id="8f67e-493">![Virtual Input page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-18.png)</span></span><br>
<span data-ttu-id="8f67e-494">*Microsoft HoloLens에 대한 Windows 장치 포털의 가상 입력 페이지*</span><span class="sxs-lookup"><span data-stu-id="8f67e-494">*Virtual Input page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="8f67e-495">원격 컴퓨터에서 HoloLens에 키보드 입력을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-495">Sends keyboard input from the remote machine to the HoloLens.</span></span>

<span data-ttu-id="8f67e-496">**가상 키보드** 아래 영역을 클릭 또는 탭하여 HoloLens에 키 입력 전송을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-496">Click or tap the region under **Virtual keyboard** to enable sending keystrokes to the HoloLens.</span></span> <span data-ttu-id="8f67e-497">**입력 텍스트** 텍스트 상자에 입력하고 **보내기** 를 클릭 또는 탭하여 활성 앱에 키 입력을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-497">Type in the **Input text** textbox and click or tap **Send** to send the keystrokes to the active app.</span></span>

## <a name="device-portal-rest-apis"></a><span data-ttu-id="8f67e-498">장치 포털 REST API</span><span class="sxs-lookup"><span data-stu-id="8f67e-498">Device Portal REST APIs</span></span>

<span data-ttu-id="8f67e-499">장치 포털의 모든 작업은 데이터에 액세스하고 디바이스를 프로그래밍 방식으로 제어할 때 선택적으로 사용할 수 있는 [REST API](device-portal-api-reference.md)를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-499">Everything in the device portal is built on top of [REST APIs](device-portal-api-reference.md) that you can optionally use to access the data and control your device programmatically.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="8f67e-500">문제 해결</span><span class="sxs-lookup"><span data-stu-id="8f67e-500">Troubleshooting</span></span>

### <a name="how-to-fix-the-its-lonely-here-message"></a><span data-ttu-id="8f67e-501">"It's lonely here(비어 있습니다)" 메시지를 수정하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f67e-501">How to fix the "It's lonely here" message</span></span>

> [!NOTE]
> <span data-ttu-id="8f67e-502">HoloLens 2에서 HoloLens(1세대)로 이동하면 HoloLens(1세대)에서 사용하기 전에 HoloLens 2에서 사용할 경우 페이지가 비어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-502">Going from a HoloLens 2 to HoloLens (1st gen) may cause the pages to become lonely if used on the HoloLens 2 prior to use on the HoloLens (1st gen).</span></span>

![장치 포털 페이지의 It's lonely here(비어 있습니다)](images/using-windows-portal-img-19.png)

1. <span data-ttu-id="8f67e-504">왼쪽 위 메뉴에서 **레이아웃 다시 설정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-504">Select **Reset layout** from the top-left Menu:</span></span>

![장치 포털 메뉴에서 레이아웃 다시 설정 선택](images/using-windows-portal-img-20.png)

2. <span data-ttu-id="8f67e-506">**작업 영역 다시 설정** 머리글 아래에서 **레이아웃 다시 설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-506">Click **Reset layout** under the **Reset workspace** heading.</span></span> <span data-ttu-id="8f67e-507">포털 페이지는 자동으로 콘텐츠를 새로 고치고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f67e-507">The portal page will automatically refresh and display your content.</span></span>

![작업 영역 다시 설정 페이지에서 레이아웃 다시 설정 선택](images/using-windows-portal-img-21.png)
