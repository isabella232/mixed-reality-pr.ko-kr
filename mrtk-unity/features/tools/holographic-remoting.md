---
title: 홀로그램 원격 접속
description: 설명서 Holographic 원격 작업 MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 637f68e5ad5f360aea4b5c0603a682d61d152a89
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144587"
---
# <a name="holographic-remoting"></a><span data-ttu-id="d131b-104">홀로그램 원격 접속</span><span class="sxs-lookup"><span data-stu-id="d131b-104">Holographic Remoting</span></span>

<span data-ttu-id="d131b-105">Holographic 원격 스트림은 Wi-Fi 또는 USB 케이블 연결을 사용 하 여 PC에서 Microsoft HoloLens로 콘텐츠를 실시간으로 Holographic 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="d131b-106">이 기능은 혼합 현실 응용 프로그램을 개발할 때 개발자의 생산성을 크게 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="d131b-107">아래에 언급 된 XR SDK는 unity [2019.3 이상에서 unity의 새로운 XR 파이프라인](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="d131b-108">MRTK와 함께 XR SDK를 사용 하는 방법에 대 한 자세한 내용은 [여기](../../configuration/getting-started-with-mrtk-and-xrsdk.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d131b-108">See [here](../../configuration/getting-started-with-mrtk-and-xrsdk.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="d131b-109">레거시 XR는 unity 2018에 포함 된 기존 XR 파이프라인을 참조 하 고 unity 2019.3에서 사용 되지 않으며 Unity 2020에서 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="d131b-110">초기 설정</span><span class="sxs-lookup"><span data-stu-id="d131b-110">Initial setup</span></span>

<span data-ttu-id="d131b-111">HoloLens를 원격으로 사용할 수 있도록 설정 하려면 프로젝트가 최신 원격 구성 요소를 사용 하 고 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="d131b-112">**패키지 관리자 > 창** 열기</span><span class="sxs-lookup"><span data-stu-id="d131b-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="d131b-113">레거시 XR를 사용 하는 경우: **Windows Mixed Reality** 패키지의 최신 버전이 설치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="d131b-114">XR SDK를 사용 하는 경우: 최신 버전의 **WINDOWS XR 플러그 인** 패키지가 설치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="d131b-115">Microsoft Store를 통해 HoloLens에서 최신 Holographic 원격 응용 프로그램이 설치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="d131b-116">프로젝트에서 사용 되는 파이프라인에 따라 [레거시 XR 설치 지침](#legacy-xr-setup-instructions) 또는 [XR SDK 설치 지침](#xr-sdk-setup-instructions) 을 계속 진행 하세요.</span><span class="sxs-lookup"><span data-stu-id="d131b-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="d131b-117">레거시 XR 설치 지침</span><span class="sxs-lookup"><span data-stu-id="d131b-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="d131b-118">아래 지침은 HoloLens 2를 사용 하는 원격에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="d131b-119">HoloLens (첫 번째 Gen)로 원격 작업을 수행 하는 경우 [wi-fi를 사용 하 여 hololens에 연결](#connecting-to-the-hololens-with-wi-fi)로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="d131b-120">HoloLens 2를 사용 하는 경우 원격에 대 한 지원 및 시각 추적 데이터가 MRTK에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="d131b-121">이러한 기능을 사용 하려면 [프로젝트에 DotNetWinRT 가져오기](#import-dotnetwinrt-into-the-project)에 설명 된 단계를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="d131b-121">To enable these features, please follow the steps documented in [Import DotNetWinRT into the project](#import-dotnetwinrt-into-the-project).</span></span>

<span data-ttu-id="d131b-122">가져온 후 다음 단계는 **혼합 현실 도구 키트**  >  **유틸리티**  >  **Windows mixed Reality**  >  **검사 구성** 을 선택 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-122">Once imported, the next step is to select **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="d131b-123">이 단계에서는 DotNetWinRT 종속성을 사용 하도록 설정 하는 스크립팅 정의를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-123">This step adds a scripting define that enables the DotNetWinRT dependency.</span></span>

> [!NOTE]
> <span data-ttu-id="d131b-124">Unity 2019.4 이상 버전을 사용 하는 경우에는 확인 구성 유틸리티를 실행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-124">When using Unity 2019.4 and newer, it is not necessary to run the Check Configuration utility.</span></span>

<span data-ttu-id="d131b-125">손 조인트 및 시선 추적 추적을 사용하도록 설정하려면 Unity 패키지 가져오기 및 관련 **섹션을 통해 HoloLens 2 Remoting 디버깅의** 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-125">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="d131b-126">Unity 패키지 가져오기를 통해 HoloLens 2 Remoting 디버깅</span><span class="sxs-lookup"><span data-stu-id="d131b-126">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="d131b-127">HoloLens 2 손 조인트와 시선 추적이 remoting을 통해 작동하지 않는 경우 몇 가지 일반적인 잠재적 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-127">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="d131b-128">검사해야 하는 순서대로 아래에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-128">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="d131b-129">이러한 문제는 **Unity 2019.3** 이상에서 실행할 때 특히 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-129">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="import-dotnetwinrt-into-the-project"></a><span data-ttu-id="d131b-130">DotNetWinRT를 프로젝트로 가져오기</span><span class="sxs-lookup"><span data-stu-id="d131b-130">Import DotNetWinRT into the project</span></span>

1. <span data-ttu-id="d131b-131">Mixed Reality [기능 도구](https://aka.ms/MRFeatureTool) 다운로드</span><span class="sxs-lookup"><span data-stu-id="d131b-131">Download the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)</span></span>

1. <span data-ttu-id="d131b-132">기능 **검색** 보기에서 *winRT 프로젝션 Mixed Reality 선택합니다.*</span><span class="sxs-lookup"><span data-stu-id="d131b-132">In the **Discover features** view, select *Mixed Reality WinRT Projections*</span></span>

    ![DotNetWinRT 패키지 선택](../images/tools/remoting/SelectDotNetWinRT.png)

1. <span data-ttu-id="d131b-134">**기능 가져오기를** 클릭하고 패키지를 계속 [가져옵니다.](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages)</span><span class="sxs-lookup"><span data-stu-id="d131b-134">Click **Get Features** and continue to [import the package](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="d131b-135">플레이어 설정에 기록된 DOTNETWINRT_PRESENT 정의</span><span class="sxs-lookup"><span data-stu-id="d131b-135">DOTNETWINRT_PRESENT define written into player settings</span></span>

> [!NOTE]
> <span data-ttu-id="d131b-136">Unity 2019.4 이상에서 사용하는 경우 DOTNETWINRT_PRESENT 정의는 Unity 플레이어 설정이 아닌 적절한 .asmdef 파일 내에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-136">When using Unity 2019.4 and newer, the DOTNETWINRT_PRESENT define is contained within the appropriate .asmdef files and not the Unity Player Settings.</span></span> <span data-ttu-id="d131b-137">구성 확인 단계는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-137">The Check Configuration step is not required.</span></span>

<span data-ttu-id="d131b-138">MRTK 버전 2.5.0부터는 성능상의 이유로 이 #define 더 이상 자동으로 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-138">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="d131b-139">이 플래그를 사용하려면 **Mixed Reality 도구 키트**  >  **유틸리티** Windows Mixed Reality 구성 확인 메뉴  >  항목을  >   사용하세요.</span><span class="sxs-lookup"><span data-stu-id="d131b-139">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="d131b-140">구성 확인 항목에 확인이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-140">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="d131b-141">정의가 설정되었는지 확인하려면 Unity 플레이어 설정으로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="d131b-141">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="d131b-142">해당 위치에서 UWP 탭 아래의 다른 설정에서 스크립팅 기호 정의를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-142">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="d131b-143">DOTNETWINRT_PRESENT 해당 목록에 올바르게 작성되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-143">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="d131b-144">이 경우 이 단계가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-144">If that's there, this step succeeded.</span></span>

![DotNetWinRT 표시](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="d131b-146">HoloLens 2 별 원격 지원 제거</span><span class="sxs-lookup"><span data-stu-id="d131b-146">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="d131b-147">DotNetWinRT 어댑터가 있기 때문에 충돌이 발생 하거나 다른 문제가 발생 하는 경우 [도움말 리소스 중 하나](../../index.md#getting-help)를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="d131b-147">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../index.md#getting-help).</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="d131b-148">XR SDK 설치 지침</span><span class="sxs-lookup"><span data-stu-id="d131b-148">XR SDK setup instructions</span></span>

<span data-ttu-id="d131b-149">[MRTK 및 XR SDK 시작 페이지의 Windows Mixed Reality 설치 지침](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) 에 따라 편집기 내 HoloLens 원격 기능에 필요한 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-149">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="d131b-150">Wi-Fi를 사용 하 여 HoloLens에 연결</span><span class="sxs-lookup"><span data-stu-id="d131b-150">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="d131b-151">프로젝트가 구성 되 면 HoloLens에 대 한 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-151">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="d131b-152">**파일 > 빌드 설정** 에서 프로젝트 빌드 형식이로 설정 되어 있는지 확인 **유니버설 Windows 플랫폼**</span><span class="sxs-lookup"><span data-stu-id="d131b-152">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="d131b-153">HoloLens에서 **Holographic 원격** 응용 프로그램을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-153">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="d131b-154">Unity에서 **Window > XR > Holographic 에뮬레이션 (레거시 XR를 사용 하는 경우)/WINDOWS XR 플러그 인 원격 (XR SDK를 사용 하는 경우)** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-154">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![Holographic 에뮬레이션 시작](../images/tools/remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="d131b-156">**에뮬레이션 모드** 를 **원격에서 장치로** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-156">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![에뮬레이션 모드 설정](../images/tools/remoting/SelectEmulationMode.png)

1. <span data-ttu-id="d131b-158">(**_레거시 XR에만 적용_** 됨) **장치 버전** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-158">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![장치 버전 선택](../images/tools/remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="d131b-160">Holographic Remoting Player 응용 프로그램에서 표시 하는 IP 주소를 사용 하 여 **원격 컴퓨터** 필드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-160">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![IP 주소 입력](../images/tools/remoting/EnterIPAddress.png)

1. <span data-ttu-id="d131b-162">**연결** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-162">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="d131b-163">연결할 수 없는 경우 HoloLens 2가 PC에 연결 되어 있지 않은지 확인 하 고 Unity를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-163">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="d131b-164">USB 케이블로 HoloLens에 연결</span><span class="sxs-lookup"><span data-stu-id="d131b-164">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="d131b-165">USB 케이블 연결을 사용 하면 렌더링 품질과 안정성이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-165">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="d131b-166">USB 케이블 연결을 사용하려면 HoloLens 설정의 Wi-Fi HoloLens에서 연결을 끊고 홀로그램 Remoting Player 앱을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-166">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="d131b-167">169로 시작하는 IP 주소가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-167">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="d131b-168">Unity의 홀로그램 에뮬레이션 설정에서 이 IP 주소를 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-168">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="d131b-169">USB 케이블의 IP 주소가 식별되면 HoloLens를 다시 Wi-Fi 연결해도 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-169">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="d131b-170">Remoting 세션 시작</span><span class="sxs-lookup"><span data-stu-id="d131b-170">Starting a remoting session</span></span>

<span data-ttu-id="d131b-171">Unity가 HoloLens에 연결된 경우 편집기에서 재생 모드를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-171">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="d131b-172">세션이 완료되면 재생 모드를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-172">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="d131b-173">일부 Unity 버전에서는 Remoting 세션 중에 편집기가 재생 모드로 들어가면 중단되는 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-173">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="d131b-174">프로젝트가 로드될 때 홀로그램 창이 열려 있으면 이 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-174">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="d131b-175">이 문제가 발생하지 않도록 하려면 Unity를 종료하기 전에 항상 홀로그램 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d131b-175">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="d131b-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d131b-176">See also</span></span>

- [<span data-ttu-id="d131b-177">홀로그램 Remoting 문제 해결 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="d131b-177">Holographic Remoting troubleshooting and limitations</span></span>](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="d131b-178">Microsoft Holographic Remoting 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="d131b-178">Microsoft Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)