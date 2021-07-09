---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392616"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="512cc-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="512cc-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-switching-build-platform"></a><span data-ttu-id="512cc-102">1. 빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="512cc-102">1. Switching Build Platform</span></span>

<span data-ttu-id="512cc-103">Unity 메뉴에서 파일 > 빌드 설정을 차례로 선택하여 빌드 설정 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-103">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="512cc-104">빌드 설정 창에서 **PC, Mac & Linux 독립 실행형** 플랫폼을 선택하고 **플랫폼 전환** 단추를 클릭하여 빌드 플랫폼을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-104">In the Build Settings window, select **PC, Mac & Linux Standalone** Platform and click the **Switch Platform** button to change the Build Platform:</span></span>

![빌드 플랫폼 전환](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

<span data-ttu-id="512cc-106">Unity에서 플랫폼 전환을 완료하면 x 아이콘을 클릭하여 빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-106">When Unity has finished switching the platform, click the x icon to close the Build Settings window.</span></span>

### <a name="2-set-the-project-settings"></a><span data-ttu-id="512cc-107">2. 프로젝트 설정 지정</span><span class="sxs-lookup"><span data-stu-id="512cc-107">2. Set the project settings</span></span>

<span data-ttu-id="512cc-108">Unity 메뉴에서 **편집** > **프로젝트 설정** > **XR 플러그 인 관리** 를 선택하고 Windows 독립 실행형 탭에 있는지 확인하고 **OpenXR**  및 **Windows Mixed Reality 기능 세트** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-108">In the Unity menu, select **Edit** > **Project Settings** > **XR Plug-in Management** ensure that you are in Windows Standalone tab and check the **OpenXR** and **Windows Mixed Reality feature set** checkbox.</span></span>

![OpenXR 및 Windows Mixed Reality 기능 세트 사용 설정](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

<span data-ttu-id="512cc-110">프로젝트 설정 창에서 **OpenXR** 을 선택하고 Windows 독립 실행형 탭에 있는지 확인하고 **깊이 제출 모드** 를 없음에서 **깊이 16비트** 로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-110">In Project Settings window, select **OpenXR** and ensure that you are in Windows Standalone tab and change the **Depth submission mode** from None to **Depth 16 Bit**.</span></span>

<span data-ttu-id="512cc-111">상호 작용 프로필 탭에서 + 기호를 클릭하여 **시선 응시 상호 작용 프로필** 및 **Microsoft 손 상호 작용 프로필** 을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-111">In interaction profiles tab add **Eye Gaze Interaction Profile** and **Microsoft Hand Interaction Profile** by clicking on the + symbol.</span></span>

![시선 응시 상호 작용 프로필 및 Microsoft 손 상호 작용 프로필 추가](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

<span data-ttu-id="512cc-113">**Open XR 기능 그룹** > **모든 기능** > **Holographic 앱 원격** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-113">Under **Open XR feature groups** > **All features** > check the **Holographic App Remoting** checkbox.</span></span>

![Holographic 앱 원격 사용 설정](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

<span data-ttu-id="512cc-115">그런 다음 **Windows Mixed Reality** 확인란을 선택하고 Windows Mixed Reality 그룹에서 **Holographic 앱 원격** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-115">next select the **Windows Mixed Reality**  check box and under Windows Mixed Reality group select the  **Holographic App Remoting** checkbox.</span></span>

![Windows Mixed Reality Holographic 앱 원격 사용 설정](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a><span data-ttu-id="512cc-117">3. Unity 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="512cc-117">3. Build the Unity Project</span></span>

<span data-ttu-id="512cc-118">Unity 메뉴에서 파일 > 빌드 설정을 차례로 선택하여 빌드 설정 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-118">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="512cc-119">Build Settings(빌드 설정) 창에서 \***Add Open Scenes** _ 단추를 클릭하여 현재 장면을 Scenes(장면)에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-119">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="512cc-120">빌드 목록에서 _ *빌드*\* 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-120">In the Build list, then click the _ *Build*\* button:</span></span>

![장면이 추가된 Unity Build Settings 창](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

<span data-ttu-id="512cc-122">빌드를 저장할 적절한 위치를 선택합니다(예: Documents\MixedRealityLearning).</span><span class="sxs-lookup"><span data-stu-id="512cc-122">choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="512cc-123">새 폴더를 만들고 적절한 이름(예: PCHolographicRemoting)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-123">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="512cc-124">그런 다음, ***폴더 선택*** 단추를 클릭하여 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-124">Then click the ***Select Folder*** button to start the build process:</span></span>

![Select Folder 프롬프트 창이 있는 Unity Build Settings 창](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

<span data-ttu-id="512cc-126">Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-126">Wait for Unity to finish the build process.</span></span>

![진행 중인 Unity 빌드 프로세스](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

<span data-ttu-id="512cc-128">실행 파일을 두 번 클릭하여 PC에서 PC Holographic 원격 애플리케이션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-128">double click on the Executable file to open the PC Holographic Remoting Application in your PC.</span></span>

> [!NOTE]
> <span data-ttu-id="512cc-129">UWP로 빌드된 PC 앱용 Holographic 원격의 일부 알려진 문제로 인해 PC 앱을 OpenXR용 Windows 독립 실행형으로 빌드하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-129">Due to some known issues in Holographic Remoting for PC app Built as UWP we are Building the PC App as Windows Standalone for OpenXR.</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="512cc-130">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="512cc-130">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-set-the-player-settings"></a><span data-ttu-id="512cc-131">1. 플레이어 설정 지정</span><span class="sxs-lookup"><span data-stu-id="512cc-131">1. Set the player settings</span></span>

<span data-ttu-id="512cc-132">**XR 설정** 섹션에서 **WSA 홀로그램 원격 지원** 확인란을 선택하고 홀로그램 원격을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-132">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![WSA 홀로그램 원격 지원이 사용되도록 설정된 Unity XR 설정 창](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="512cc-134">2. Unity 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="512cc-134">2. Build the Unity Project</span></span>

<span data-ttu-id="512cc-135">Unity 메뉴에서 파일 > 빌드 설정을 차례로 선택하여 빌드 설정 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-135">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="512cc-136">Build Settings(빌드 설정) 창에서 \***Add Open Scenes** _ 단추를 클릭하여 현재 장면을 Scenes(장면)에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-136">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="512cc-137">Build 목록에서 _ \*_Build 단추_\*\*를 클릭하여 유니버설 Windows 플랫폼 빌드 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-137">In the Build list, then click the _ *_Build button_*\* to open the Build Universal Windows Platform window:</span></span>

![장면이 추가된 Unity Build Settings 창](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="512cc-139">빌드 유니버설 Windows 플랫폼 창에서 빌드를 저장할 적합한 위치(예: Documents\MixedRealityLearning)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-139">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="512cc-140">새 폴더를 만들고 적절한 이름(예: PCHolographicRemoting)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-140">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="512cc-141">그런 다음, ***폴더 선택*** 단추를 클릭하여 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-141">Then click the ***Select Folder*** button to start the build process:</span></span>

![Select Folder 프롬프트 창이 있는 Unity Build Settings 창](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="512cc-143">Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-143">Wait for Unity to finish the build process.</span></span>

![진행 중인 Unity 빌드 프로세스](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="512cc-145">3. 애플리케이션 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="512cc-145">3. Build and deploy the application</span></span>

<span data-ttu-id="512cc-146">빌드 프로세스가 완료되면 Unity에서 빌드를 저장한 위치를 열라는 메시지를 Windows 파일 탐색기에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-146">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="512cc-147">폴더 내부를 탐색하고 .sln 파일을 두 번 클릭하여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-147">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![새로 만든 Visual Studio 솔루션이 선택된 Windows 탐색기](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="512cc-149">Visual Studio에서 새 구성 요소를 설치하라는 메시지가 표시되면 도구 설치 설명서에서 지정한 대로 모든 필수 구성 요소가 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-149">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="512cc-150">릴리스 구성, x64 아키텍처 및 로컬 머신을 대상으로 선택하여 PC에 대해 Visual Studio를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-150">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![로컬 컴퓨터에 대해 구성된 Visual Studio](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="512cc-152">***로컬 머신*** 이라고 표시된 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-152">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="512cc-153">애플리케이션을 빌드하고 PC에 배포하기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-153">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="512cc-154">애플리케이션은 기본적으로 PC에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="512cc-154">The application will be installed in your PC by default.</span></span>
