---
title: 기타 질문
description: 표준 소비자 지원 설명서를 벗어나는 추가 Windows 혼합 현실 문제 해결 팁입니다.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원, Windows Mixed Reality 제거, 지원 되는 언어
appliesto:
- Windows 10
ms.openlocfilehash: a49008cb7d6a51385cb0d4ece7dfae3018aefe88
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131867"
---
# <a name="other-questions"></a><span data-ttu-id="e8c59-104">기타 질문</span><span class="sxs-lookup"><span data-stu-id="e8c59-104">Other questions</span></span>

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a><span data-ttu-id="e8c59-105">내 그래픽 드라이버가 지원 되지 않습니다 (그래픽 드라이버 오류 오류가 발생 함).</span><span class="sxs-lookup"><span data-stu-id="e8c59-105">My graphics driver isn't supported (I'm getting graphics driver failure errors).</span></span>

<span data-ttu-id="e8c59-106">"Dxdiag"를 검색 하 고 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-106">Search for and run "dxdiag":</span></span>

1.  <span data-ttu-id="e8c59-107">결과가 "기본 렌더러" 이면 그래픽 드라이버가 설치 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-107">If the result is “Basic Renderer”, the graphics driver is not installed.</span></span> <span data-ttu-id="e8c59-108">이 문제를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="e8c59-108">To fix this:</span></span>
    * <span data-ttu-id="e8c59-109">**Device Manager > 작업 > 하드웨어 변경 내용 검색** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-109">Go to **Device Manager > Action > Scan for Hardware Changes** .</span></span>
    * <span data-ttu-id="e8c59-110">Windows 업데이트를 사용 하 여 드라이버를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-110">Use Windows Update to update the driver.</span></span>
    * <span data-ttu-id="e8c59-111">그래도 문제가 해결 되지 않으면 제조업체 웹 사이트로 이동 하 여 최신 드라이버 업데이트를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-111">If this doesn't fix the problem, go to the manufacturer’s website and install the latest driver update.</span></span> 
    * <span data-ttu-id="e8c59-112">GPU에 대 한 업데이트를 사용할 수 없는 경우 장치에서 WMR가 지원 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-112">If an update isn't available for your GPU, WMR may not be supported on your device.</span></span> <span data-ttu-id="e8c59-113">이 것으로 생각 되 면 [지원](https://support.microsoft.com)담당자에 게 문의 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8c59-113">If you think it should be, contact [support](https://support.microsoft.com).</span></span>
2.  <span data-ttu-id="e8c59-114">"WDDM 2.1" 이상 버전을 가져오는 경우 그래픽 드라이버가 설치 되지만 최신 버전이 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-114">If you get a “WDDM 2.1” or lower version, the graphics driver is installed but it might not be the latest version.</span></span> <span data-ttu-id="e8c59-115">최신 버전을 가져오려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-115">To get the latest version:</span></span>
    * <span data-ttu-id="e8c59-116">Windows 업데이트를 사용 하 여 드라이버를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-116">Use Windows Update to update the driver.</span></span>
    * <span data-ttu-id="e8c59-117">업데이트에서 문제가 해결 되지 않으면 제조업체 웹 사이트로 이동 하 여 최신 드라이버 업데이트를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-117">If that update doesn't fix the problem, go to the manufacturer’s website and install the latest driver update.</span></span> 
    * <span data-ttu-id="e8c59-118">GPU에 대 한 업데이트를 사용할 수 없는 경우 장치에서 WMR가 지원 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-118">If an update isn't available for your GPU, WMR may not be supported on your device.</span></span> <span data-ttu-id="e8c59-119">이 것으로 생각 되 면 [지원](https://support.microsoft.com)담당자에 게 문의 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8c59-119">If you think it should be, contact [support](https://support.microsoft.com).</span></span>

<span data-ttu-id="e8c59-120">Windows Mixed Reality 설치에서 그래픽 카드가 요구 사항을 충족 하지 않는 것으로 생각 하 고 있다고 생각 되는 경우 헤드셋이 올바른 카드에 꽂혀 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-120">If Windows Mixed Reality setup says your graphics card doesn’t meet the requirements and you think it does, make sure your headset is plugged into the correct card.</span></span>

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a><span data-ttu-id="e8c59-121">내 Samsung Odyssey 또는 Odyssey + 헤드셋 펌웨어 업데이트가 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-121">My Samsung Odyssey or Odyssey+ headset firmware update is stuck.</span></span>

<span data-ttu-id="e8c59-122">Samsung는 "Samsung HMD Odyssey Setup" 및 "Samsung HMD Odyssey + Setup" 장치 도우미 앱을 통해 제공 되는 헤드셋 펌웨어 업데이트를 소유 하 고 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-122">Samsung owns and publishes headset firmware updates delivered via their "Samsung HMD Odyssey Setup" and "Samsung HMD Odyssey+ Setup" device companion apps.</span></span> <span data-ttu-id="e8c59-123">Samsung 펌웨어 업데이트 문제에 대 한 자세한 내용 및 도움을 보려면 Samsung 고객 서비스에 문의 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8c59-123">For more details and for help with Samsung firmware update issues, please reach out to Samsung customer service.</span></span>

<span data-ttu-id="e8c59-124">펌웨어 업데이트 프로세스가 중단 되 고 5 분 이상 진행 되지 않은 경우:</span><span class="sxs-lookup"><span data-stu-id="e8c59-124">If the firmware update process is getting stuck, and there has been no progress for more than five minutes:</span></span>

* <span data-ttu-id="e8c59-125">다른 모든 USB 장치를 일시적으로 분리 하 고 펌웨어 업데이트를 다시 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-125">Unplug all of your other USB devices temporarily and retry the firmware update.</span></span>
* <span data-ttu-id="e8c59-126">Samsung 헤드셋을 PC의 다른 USB 3.0 포트에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-126">Connect your Samsung headset to a different USB 3.0 port on your PC.</span></span>
* <span data-ttu-id="e8c59-127">Gb의 AORUS App Center와 같은 펌웨어 업데이트를 방해할 수 있는 설치 된 소프트웨어를 사용 하지 않도록 설정 하거나 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-127">Disable and/or uninstall any software installed that may interfere with firmware updates, like Gigabyte's AORUS App Center.</span></span>
* <span data-ttu-id="e8c59-128">다른 PC를 사용 하 여 Samsung 헤드셋 펌웨어 업데이트를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-128">Use a different PC to perform the Samsung headset firmware update.</span></span>

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a><span data-ttu-id="e8c59-129">혼합 현실에서 내 PC 데스크톱에 액세스 어떻게 할까요??</span><span class="sxs-lookup"><span data-stu-id="e8c59-129">How do I access my PC desktop in mixed reality?</span></span>
<span data-ttu-id="e8c59-130">Windows의 헤드셋에서 데스크톱 앱을 시작 합니다. 단추를 클릭 하 여 **모든 앱 > 데스크톱 >** 혼합 현실에서 PC 데스크톱에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-130">Launch the Desktop app in the headset from **Windows Button > All apps > Desktop** to access your PC desktop in mixed reality.</span></span>

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a><span data-ttu-id="e8c59-131">혼합 현실에서 여러 모니터를 표시 하는 방법</span><span class="sxs-lookup"><span data-stu-id="e8c59-131">How can I see multiple monitors in Mixed Reality</span></span>

<span data-ttu-id="e8c59-132">기본적으로 데스크톱 앱은 자동으로 전환 하 여 포커스가 있는 모니터를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-132">By default, Desktop app automatically switches to display the monitor with focus.</span></span> <span data-ttu-id="e8c59-133">혼합 현실에서 모든 모니터를 보려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-133">If you want to see all of your monitors in mixed reality:</span></span>

* <span data-ttu-id="e8c59-134">앱의 왼쪽 위 모서리에 있는 모니터 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-134">Click the monitor icon on the top left corner of the app.</span></span>
* <span data-ttu-id="e8c59-135">"모니터 자동 전환"을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-135">Disable "Automatically Switch Monitor".</span></span>
* <span data-ttu-id="e8c59-136">보려는 모니터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-136">Pick the monitor you want to see.</span></span>
* <span data-ttu-id="e8c59-137">데스크톱 앱의 다른 인스턴스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-137">Launch another instance of the Desktop app.</span></span>
* <span data-ttu-id="e8c59-138">해당 인스턴스에 대해 보려는 모니터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-138">Pick the monitor you want to see on that instance.</span></span>
* <span data-ttu-id="e8c59-139">모든 실제 모니터에 대해 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-139">Repeat for all of your physical monitors.</span></span>
<span data-ttu-id="e8c59-140">혼합 현실를 다시 시작할 때마다 각 데스크톱 앱에 표시 하려면 모니터를 다시 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-140">Note that you will have to reselect the monitor to show on each Desktop app every time you restart mixed reality.</span></span>

## <a name="my-desktop-app-only-shows-a-black-screen"></a><span data-ttu-id="e8c59-141">내 데스크톱 앱에는 검은색 화면만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-141">My Desktop app only shows a black screen</span></span>

<span data-ttu-id="e8c59-142">PC에 Nvidia 하이브리드 GPU가 있는 경우이 문제는 통합 된 GPU가 아닌 개별 GPU에서 runtimebroker.exe를 실행 하는 Nvidia 장치에 의해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-142">If your PC has an Nvidia hybrid GPU, the issue may be caused by Nvidia device running the runtimebroker.exe on the discrete GPU instead of the integrated one.</span></span> <span data-ttu-id="e8c59-143">이 문제를 해결 하려면[어떻게 할까요? "새 프로그램에 대 한 Optimus 설정 만들기"의](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="e8c59-143">To fix this issue, follow these instructions under "[How do I create Optimus settings for a new program?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)"</span></span> <span data-ttu-id="e8c59-144">C:\windows\system32\runtimebroker.exe 추가 하 고 "통합 그래픽" 프로세서에서 강제로 실행 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-144">to add C:\windows\system32\runtimebroker.exe and force it to run on the "Integrated graphics" processor.</span></span> 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a><span data-ttu-id="e8c59-145">Windows Mixed Reality를 사용 하는 경우 내 Wi-Fi 느려집니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-145">My Wi-Fi slows down when I'm using Windows Mixed Reality.</span></span>

<span data-ttu-id="e8c59-146">2.4 g h z Wi-Fi 연결을 사용 하는 경우 동작 컨트롤러에서 Wi-fi 속도가 느려질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-146">If you're using a 2.4GHz Wi-Fi connection, your motion controllers might slow down your Wi-Fi.</span></span> <span data-ttu-id="e8c59-147">다음 작업 중 하나를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="e8c59-147">Try one of the following:</span></span>

* <span data-ttu-id="e8c59-148">사용할 수 있는 경우 5GHz Wi-Fi 연결로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-148">Switch to a 5GHz Wi-Fi connection, if one is available.</span></span> <span data-ttu-id="e8c59-149">[자세한 정보를 알아보세요](https://support.microsoft.com/help/4000461).</span><span class="sxs-lookup"><span data-stu-id="e8c59-149">[Learn more](https://support.microsoft.com/help/4000461).</span></span>
* <span data-ttu-id="e8c59-150">별도의 Bluetooth 어댑터를 사용 하 여 이동 컨트롤러를 PC에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-150">Use a separate Bluetooth adapter to connect your motion controllers to your PC.</span></span> <span data-ttu-id="e8c59-151">[권장 어댑터](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8c59-151">See [recommended adapters](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).</span></span>

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a><span data-ttu-id="e8c59-152">PC를 연결 하 고 요금을 청구 하는 메시지를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-152">I got a message that said to plug in and charge my PC.</span></span> <span data-ttu-id="e8c59-153">그 이유는</span><span class="sxs-lookup"><span data-stu-id="e8c59-153">Why?</span></span>

<span data-ttu-id="e8c59-154">노트북을 사용 하는 경우 Windows Mixed Reality는 PC가 완전히 충전 되 고 연결 된 경우에 가장 잘 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-154">If you're using a laptop, Windows Mixed Reality works best when the PC is both fully charged and plugged in.</span></span>

## <a name="what-is-the-experience-options-setting"></a><span data-ttu-id="e8c59-155">환경 옵션 설정은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="e8c59-155">What is the Experience options setting?</span></span>

<span data-ttu-id="e8c59-156">이 설정 ( **설정 > 혼합 현실 > 헤드셋 표시 > 환경 옵션** )을 사용 하면 Windows Mixed reality 성능 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-156">This setting ( **Settings > Mixed reality > Headset display > Experience options** ) allows you to change the Windows Mixed Reality performance settings.</span></span> <span data-ttu-id="e8c59-157">이를 통해 다양 한 콘텐츠를 통해 하드웨어 구성에 대 한 최상의 환경을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-157">This enables you to choose the best experience for your hardware configuration across a range of content.</span></span> <span data-ttu-id="e8c59-158">이러한 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-158">These are the options:</span></span>
* <span data-ttu-id="e8c59-159">자동: Windows Mixed Reality는 하드웨어 구성에 대 한 최상의 환경을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-159">Automatic: Windows Mixed Reality will determine the best experience for your hardware configuration.</span></span> <span data-ttu-id="e8c59-160">대부분의 사용자는이 옵션을 사용 하 여 시작 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-160">For most people, this is the best choice to start with.</span></span>
* <span data-ttu-id="e8c59-161">60Hz: 새로 고침 빈도를 60Hz로 설정 하 고 혼합 현실 포털에서 비디오 캡처 및 미리 보기와 같은 특정 기능을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-161">60Hz: Sets the refresh rate to 60Hz and turns off certain features, such as video capture and preview in Mixed Reality Portal.</span></span>
* <span data-ttu-id="e8c59-162">90Hz: 새로 고침 빈도를 90Hz로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-162">90Hz: Sets the refresh rate to 90Hz.</span></span>

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a><span data-ttu-id="e8c59-163">Windows Mixed Reality에서 지원 되는 언어</span><span class="sxs-lookup"><span data-stu-id="e8c59-163">What languages are supported in Windows Mixed Reality</span></span>

<span data-ttu-id="e8c59-164">Windows Mixed Reality는 다음 언어로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-164">Windows Mixed Reality is available in the following languages:</span></span>

* <span data-ttu-id="e8c59-165">중국어 간체(중국)</span><span class="sxs-lookup"><span data-stu-id="e8c59-165">Chinese Simplified (China)</span></span>
* <span data-ttu-id="e8c59-166">영어(오스트레일리아)</span><span class="sxs-lookup"><span data-stu-id="e8c59-166">English (Australia)</span></span>
* <span data-ttu-id="e8c59-167">영어(캐나다)</span><span class="sxs-lookup"><span data-stu-id="e8c59-167">English (Canada)</span></span>
* <span data-ttu-id="e8c59-168">영어(영국)</span><span class="sxs-lookup"><span data-stu-id="e8c59-168">English (Great Britain)</span></span>
* <span data-ttu-id="e8c59-169">영어(미국)</span><span class="sxs-lookup"><span data-stu-id="e8c59-169">English (United States)</span></span>
* <span data-ttu-id="e8c59-170">프랑스어(캐나다)</span><span class="sxs-lookup"><span data-stu-id="e8c59-170">French (Canada)</span></span>
* <span data-ttu-id="e8c59-171">프랑스어(프랑스)</span><span class="sxs-lookup"><span data-stu-id="e8c59-171">French (France)</span></span>
* <span data-ttu-id="e8c59-172">독일어(독일)</span><span class="sxs-lookup"><span data-stu-id="e8c59-172">German (Germany)</span></span>
* <span data-ttu-id="e8c59-173">이탈리아어(이탈리아)</span><span class="sxs-lookup"><span data-stu-id="e8c59-173">Italian (Italy)</span></span>
* <span data-ttu-id="e8c59-174">일본어(일본)</span><span class="sxs-lookup"><span data-stu-id="e8c59-174">Japanese (Japan)</span></span>
* <span data-ttu-id="e8c59-175">스페인어(멕시코)</span><span class="sxs-lookup"><span data-stu-id="e8c59-175">Spanish (Mexico)</span></span>
* <span data-ttu-id="e8c59-176">스페인어(스페인)</span><span class="sxs-lookup"><span data-stu-id="e8c59-176">Spanish (Spain)</span></span>

<span data-ttu-id="e8c59-177">PC가 다른 언어로 설정 되어 있지만 인터페이스가 영어 (미국)로 표시 되 고 음성 명령과 받아쓰기를 사용할 수 없는 경우 Windows Mixed Reality를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-177">You can use Windows Mixed Reality if your PC is set to a different language, but the interface will appear in English (United States), and speech commands and dictation won't be available.</span></span> <span data-ttu-id="e8c59-178">Windows Mixed Reality 화면 키보드는 영어 (미국)만 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-178">The Windows Mixed Reality onscreen keyboard is English (United States) only.</span></span> <span data-ttu-id="e8c59-179">텍스트를 다른 언어로 입력 하려면 PC에 연결 된 실제 키보드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-179">To enter text in another language, use a physical keyboard connected to your PC.</span></span> <span data-ttu-id="e8c59-180">위에 나열 된 지원 되는 Windows Mixed Reality 언어 중 하나에서 받아쓰기를 사용할 수도 있습니다. 화면 키보드에서 마이크를 선택 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-180">You can also use dictation in one of the supported Windows Mixed Reality languages listed above—just select microphone on the onscreen keyboard.</span></span>

<span data-ttu-id="e8c59-181">Windows Mixed Reality는 음성 명령 또는 받아쓰기 기능 없이도 다음 언어로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-181">Windows Mixed Reality is also available in the following languages without speech commands or dictation features:</span></span>
* <span data-ttu-id="e8c59-182">중국어 번체 (대만 및 홍콩)</span><span class="sxs-lookup"><span data-stu-id="e8c59-182">Chinese Traditional (Taiwan and Hong Kong)</span></span>
* <span data-ttu-id="e8c59-183">네덜란드어(네덜란드)</span><span class="sxs-lookup"><span data-stu-id="e8c59-183">Dutch (Netherlands)</span></span>
* <span data-ttu-id="e8c59-184">한국어(한국)</span><span class="sxs-lookup"><span data-stu-id="e8c59-184">Korean (Korea)</span></span>
* <span data-ttu-id="e8c59-185">러시아어(러시아)</span><span class="sxs-lookup"><span data-stu-id="e8c59-185">Russian (Russia)</span></span>

## <a name="i-have-questions-about-my-headset-hardware"></a><span data-ttu-id="e8c59-186">내 헤드셋 하드웨어에 대 한 질문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-186">I have questions about my headset hardware.</span></span>

<span data-ttu-id="e8c59-187">헤드셋에 대 한 자세한 내용은 제조업체에서 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8c59-187">For details about your headset, check with the manufacturer.</span></span> <span data-ttu-id="e8c59-188">상자에 제품 가이드가 있거나 제조업체의 웹 사이트를 사용해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-188">There may be a product guide in the box, or you can try the manufacturer’s website.</span></span>

## <a name="how-do-i-uninstall-windows-mixed-reality"></a><span data-ttu-id="e8c59-189">Windows Mixed Reality를 제거할 어떻게 할까요? 있나요?</span><span class="sxs-lookup"><span data-stu-id="e8c59-189">How do I uninstall Windows Mixed Reality?</span></span>

1. <span data-ttu-id="e8c59-190">PC에서 헤드셋의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-190">Disconnect your headset from your PC.</span></span>
2. <span data-ttu-id="e8c59-191">Windows Mixed Reality 포털을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-191">Close Windows Mixed Reality Portal.</span></span>
2. <span data-ttu-id="e8c59-192">**시작 > 설정 > 혼합 현실** 로 이동 하 고 "제거"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-192">Go to  **Start > Settings > Mixed Reality** and select "Uninstall".</span></span>

<span data-ttu-id="e8c59-193">헤드셋을 다시 사용할 준비가 되 면 플러그 인을 시작 하 고 Windows Mixed Reality 포털에서 설치를 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-193">When you're ready to start using your headset again, plug it in, and Windows Mixed Reality Portal will take you through setup.</span></span>

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a><span data-ttu-id="e8c59-194">"Windows Mixed Reality 제거를 완료할 수 없습니다." 라는 메시지가 나타났습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-194">I got a "We couldn't finish uninstalling Windows Mixed Reality" message.</span></span>

<span data-ttu-id="e8c59-195">사용자 환경에 대 한 정보를 포함 하 여 일부 파일은 컴퓨터에 남아 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-195">Some files, including information about your environment, might still be on your computer.</span></span> <span data-ttu-id="e8c59-196">나중에 Windows Mixed Reality를 다시 설치 하려는 경우 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-196">This can cause problems if you decide to reinstall Windows Mixed Reality later.</span></span> <span data-ttu-id="e8c59-197">레지스트리를 수정 하 고 Windows PowerShell을 사용 하 여 명령을 실행 하 여 PC에서 남아 있는 Windows 혼합 현실 정보를 수동으로 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-197">You can manually remove any remaining Windows Mixed Reality info from your PC by modifying the registry and using Windows PowerShell to run commands.</span></span> <span data-ttu-id="e8c59-198">_레지스트리를 잘못 수정 하면 심각한 문제가 발생할 수 있습니다. 이러한 단계를 신중 하 게 수행 해야 합니다. 추가 된 보호를 위해 수정 하기 전에 레지스트리를 백업 하 여 문제가는 때 복원할 수 있도록 합니다._</span><span class="sxs-lookup"><span data-stu-id="e8c59-198">_If you modify the registry incorrectly, serious problems might occur. Make sure to follow these steps carefully. For added protection, back up your registry before you modify it so you can restore it if a problem occurrs._</span></span> <span data-ttu-id="e8c59-199">자세한 내용은 [Windows에서 레지스트리를 백업 하 고 다시 작성 하는 방법](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8c59-199">For more information, see [How to back up and restory the registry in Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows).</span></span> 

<span data-ttu-id="e8c59-200">다음 명령을 사용 하 여 Windows mixed reality를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-200">To uninstall Windows mixed reality using these commands:</span></span>
1. <span data-ttu-id="e8c59-201">PC를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-201">Restart your PC.</span></span>
2. <span data-ttu-id="e8c59-202">**검색** 상자에 "regedit"를 입력 하 고 "예"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-202">In the **Search** box, type "regedit" and then select "Yes".</span></span>
3. <span data-ttu-id="e8c59-203">다음 레지스트리 값을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-203">Remove these registry values:</span></span>
   <ul>
    <li><span data-ttu-id="e8c59-204"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>하 고 "FirstRunSucceeded"를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-204"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, then delete "FirstRunSucceeded".</span></span></li> 
    <li><span data-ttu-id="e8c59-205"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>하 고 "PreferDesktopSpeaker" 및 "PreferDesktopMic"를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-205"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>, then delete "PreferDesktopSpeaker" and "PreferDesktopMic".</span></span></li> 
    <li><span data-ttu-id="e8c59-206"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>"DisableSpeechInput"를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-206"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>, then delete "DisableSpeechInput".</span></span> <span data-ttu-id="e8c59-207">참고: Windows Mixed Reality를 사용 하는 PC의 모든 사용자 계정에 대해 HHKEY_CURRENT_USER의 레지스트리 항목을 삭제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-207">Note: The registry items in HHKEY_CURRENT_USER must be deleted for every user account on the PC that has used Windows Mixed Reality.</span></span></li> 
    <li><span data-ttu-id="e8c59-208"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>"DeviceID" 및 "Mode"를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-208"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>, then delete "DeviceID" and "Mode".</span></span></li> 
    <li><span data-ttu-id="e8c59-209"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>하 고 "OnDeviceLearningCompleted"를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-209"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, then delete "OnDeviceLearningCompleted".</span></span></li> 
   </ul><span data-ttu-id="e8c59-210">
4. 다음 레지스트리 키를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-210">
4. Remove the following registry keys:</span></span> <ul>
   <li> <span data-ttu-id="e8c59-211"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span><span class="sxs-lookup"><span data-stu-id="e8c59-211"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span></span></li> 
   <li> <span data-ttu-id="e8c59-212"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span><span class="sxs-lookup"><span data-stu-id="e8c59-212"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span></span></li> 
   <li> <span data-ttu-id="e8c59-213"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></span><span class="sxs-lookup"><span data-stu-id="e8c59-213"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></span></span></li><br/></ul><span data-ttu-id="e8c59-214">
5. 레지스트리 편집기를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-214">
5. Close the Registry Editor.</span></span>
<span data-ttu-id="e8c59-215">6.**C:\Users\user name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \LocalState** 로 이동 하 고 "RoomBounds.json"을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-215">6. Go to **C:\Users\user name\AppData\Local\Packages\Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy\LocalState** and delete "RoomBounds.json".</span></span> <span data-ttu-id="e8c59-216">Windows Mixed Reality를 사용 하는 각 사용자에 대해이를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-216">Repeat this for each user who has used Windows Mixed Reality.</span></span>
<span data-ttu-id="e8c59-217">7. 관리자 cmd 프롬프트를 열고 **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-217">7. Open admin cmd prompt and go to **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** .</span></span> <span data-ttu-id="e8c59-218">"헤드 추적 데이터" 폴더의 내용을 삭제 합니다 (폴더 자체는 아님).</span><span class="sxs-lookup"><span data-stu-id="e8c59-218">Delete the contents of the "HeadTracking data" folder (but not the folder itself).</span></span>
<span data-ttu-id="e8c59-219">8. "검색 상자"에 "powershell"을 입력 하 고 "Windows PowerShell"을 마우스 오른쪽 단추로 클릭 한 다음 "관리자 권한으로 실행"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-219">8. Type "powershell" in the "Search box", right-click "Windows PowerShell", and then select "Run as administrator".</span></span>
<span data-ttu-id="e8c59-220">9. Windows PowerShell에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-220">9. In Windows PowerShell:</span></span> <ul>
   <li><span data-ttu-id="e8c59-221">명령 프롬프트에서 <b>Dism/Online/Get-Capabilities</b>을 복사 하 여 붙여 넣은 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-221">At the command prompt, copy and paste <b>Dism /online /Get-Capabilities</b>, then press Enter.</span></span></b></li> 
   <li><span data-ttu-id="e8c59-222">Holographic로 시작 하는 기능 Id를 복사 합니다 .이 항목이 없으면이 항목이 설치 되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-222">Copy the Capability Identity that begins with Analog.Holographic.Desktop (if it isn't there, that means this item isn't installed.</span></span> <span data-ttu-id="e8c59-223">이 경우에는 10 단계로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-223">In that case, skip to step 10 ).</span></span></li> 
   <li><span data-ttu-id="e8c59-224">다음 명령 프롬프트를 복사 하 여 붙여넣고 Enter 키를 누릅니다. <b>Dism/Online/Remove-Capability/CapabilityName: 마지막 단계에서 복사 된 기능 id</b></span><span class="sxs-lookup"><span data-stu-id="e8c59-224">Copy and paste the following command prompt, then press Enter: <b>Dism /online /Remove-Capability /CapabilityName:the Capability Identity copied in the last step</b></span></span></li>
   </ul><span data-ttu-id="e8c59-225">
10. PC를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8c59-225">
10. Restart your PC.</span></span>

