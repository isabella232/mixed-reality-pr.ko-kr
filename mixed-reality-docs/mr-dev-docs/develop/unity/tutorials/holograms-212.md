---
title: MR 입력 212-음성
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 수행 하 여 음성 개념에 대 한 세부 정보를 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, 아카데미, 자습서, 음성
ms.openlocfilehash: ed37ef6e0c26c3d2a0cd2d51e18d01a258b2fc78
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686417"
---
# <a name="mr-input-212-voice"></a><span data-ttu-id="28a02-104">MR 입력 212: 음성</span><span class="sxs-lookup"><span data-stu-id="28a02-104">MR Input 212: Voice</span></span>

>[!NOTE]
><span data-ttu-id="28a02-105">Mixed Reality 아카데미 자습서는 HoloLens(1세대) 및 Mixed Reality 몰입형 헤드셋을 염두에 두고 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="28a02-106">따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="28a02-107">이러한 자습서는 HoloLens 2에 사용되는 최신 도구 집합 또는 상호 작용으로 업데이트되지 **_않습니다_** .</span><span class="sxs-lookup"><span data-stu-id="28a02-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="28a02-108">대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="28a02-109">HoloLens 2에 대한 [새로운 자습서 시리즈](../../../mr-learning-base-01.md)가 게시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-109">[A new series of tutorials](../../../mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="28a02-110">[음성 입력](../../../design/voice-input.md) 은 holograms와 상호 작용 하는 또 다른 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-110">[Voice input](../../../design/voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="28a02-111">음성 명령은 매우 자연스럽 고 쉬운 방법으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-111">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="28a02-112">음성 명령은 다음과 같이 설계 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-112">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="28a02-113">Natural</span><span class="sxs-lookup"><span data-stu-id="28a02-113">Natural</span></span>
* <span data-ttu-id="28a02-114">쉽게 기억할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-114">Easy to remember</span></span>
* <span data-ttu-id="28a02-115">적절 한 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="28a02-115">Context appropriate</span></span>
* <span data-ttu-id="28a02-116">동일한 컨텍스트 내의 다른 옵션과 충분히 구분</span><span class="sxs-lookup"><span data-stu-id="28a02-116">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="28a02-117">[MR 기본 101](../../../develop/unity/tutorials/holograms-101.md)에서 KeywordRecognizer를 사용 하 여 간단한 음성 명령을 두 번 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-117">In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="28a02-118">MR 입력 212에서는 다음을 수행 하는 방법을 자세히 알아보고 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="28a02-118">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="28a02-119">HoloLens 음성 엔진에 최적화 된 음성 명령을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-119">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="28a02-120">사용자가 사용할 수 있는 음성 명령을 인식 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-120">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="28a02-121">사용자의 음성 명령이 들리는지 인정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-121">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="28a02-122">받아쓰기 인식기를 사용 하 여 사용자의 의견을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-122">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="28a02-123">문법 인식기를 사용 하 여 SRGS 또는 음성 인식 문법 사양 파일에 따라 명령을 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-123">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="28a02-124">이 과정에서는 [Mr 입력 210](holograms-210.md) 및 [mr 입력 211](holograms-211.md)에서 빌드된 모델 탐색기를 다시 방문 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-124">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="28a02-125">아래 각 장에 포함 된 비디오는 이전 버전의 Unity 및 혼합 현실 도구 키트를 사용 하 여 기록 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-125">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="28a02-126">단계별 지침은 정확 하 고 최신 상태 이지만 최신의 비디오에서 스크립트 및 시각적 개체를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-126">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="28a02-127">Posterity에 대 한 비디오는 포함 되어 있지만 적용 되는 개념은 그대로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-127">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="28a02-128">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="28a02-128">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="28a02-129">과정</span><span class="sxs-lookup"><span data-stu-id="28a02-129">Course</span></span></th><th style="width:150px"> <span data-ttu-id="28a02-130"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="28a02-130"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="28a02-131"><a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="28a02-131"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="28a02-132">MR 입력 212: 음성</span><span class="sxs-lookup"><span data-stu-id="28a02-132">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="28a02-133">✔️</span><span class="sxs-lookup"><span data-stu-id="28a02-133">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="28a02-134">✔️</span><span class="sxs-lookup"><span data-stu-id="28a02-134">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="28a02-135">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="28a02-135">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="28a02-136">전제 조건</span><span class="sxs-lookup"><span data-stu-id="28a02-136">Prerequisites</span></span>

* <span data-ttu-id="28a02-137">올바른 [도구로](../../../develop/install-the-tools.md)구성 된 WINDOWS 10 PC입니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-137">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="28a02-138">몇 가지 기본적인 c # 프로그래밍 기능.</span><span class="sxs-lookup"><span data-stu-id="28a02-138">Some basic C# programming ability.</span></span>
* <span data-ttu-id="28a02-139">[MR 기본 101](../../../develop/unity/tutorials/holograms-101.md)를 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-139">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="28a02-140">[MR 입력 210](holograms-210.md)을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-140">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="28a02-141">[MR 입력 211](holograms-211.md)을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-141">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="28a02-142">[개발용으로 구성 된](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)HoloLens 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-142">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="28a02-143">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="28a02-143">Project files</span></span>

* <span data-ttu-id="28a02-144">프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) 을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-144">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="28a02-145">Unity 2017.2 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-145">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="28a02-146">바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-146">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="28a02-147">다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-147">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="28a02-148">정오표 및 참고 사항</span><span class="sxs-lookup"><span data-stu-id="28a02-148">Errata and Notes</span></span>

* <span data-ttu-id="28a02-149">코드에서 중단점을 적중 하려면 Visual Studio의 도구->옵션->디버깅에서 "내 코드만 사용"을 사용 하지 않도록 설정 ( *선택 취소* ) 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-149">"Enable Just My Code" needs to be disabled ( *unchecked* ) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="28a02-150">Unity 설치</span><span class="sxs-lookup"><span data-stu-id="28a02-150">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="28a02-151">Instructions</span><span class="sxs-lookup"><span data-stu-id="28a02-151">Instructions</span></span>

1. <span data-ttu-id="28a02-152">Unity를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-152">Start Unity.</span></span>
2. <span data-ttu-id="28a02-153">**열기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-153">Select **Open** .</span></span>
3. <span data-ttu-id="28a02-154">이전에 보관 하지 않은 **HolographicAcademy-Holograms-212-Voice** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-154">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="28a02-155">**Starting** / **모델 탐색기** 시작 폴더를 찾아 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-155">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="28a02-156">**폴더 선택** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-156">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="28a02-157">**프로젝트** 패널에서 **장면** 폴더를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-157">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="28a02-158">**모델 탐색기** 장면을 두 번 클릭 하 여 Unity에서 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-158">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="28a02-159">빌딩</span><span class="sxs-lookup"><span data-stu-id="28a02-159">Building</span></span>

1. <span data-ttu-id="28a02-160">Unity에서 **파일 > 빌드 설정** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-160">In Unity, select **File > Build Settings** .</span></span>
2. <span data-ttu-id="28a02-161">백그라운드에서 장면 **/모델 탐색기** 가 **백그라운드** 에서 표시 되지 않는 경우 **열린 장면 추가** 를 클릭 하 여 장면을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-161">If **Scenes/ModelExplorer** is not listed in **Scenes In Build** , click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="28a02-162">특별히 HoloLens를 개발 하는 경우 **대상 장치** 를 **hololens** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-162">If you're specifically developing for HoloLens, set **Target device** to **HoloLens** .</span></span> <span data-ttu-id="28a02-163">그렇지 않으면 **모든 장치** 에 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-163">Otherwise, leave it on **Any device** .</span></span>
4. <span data-ttu-id="28a02-164">**빌드 형식이** **D3D** 로 설정 되 고 **sdk** 가 **최신 버전** 으로 설정 되어 있는지 확인 합니다 (sdk 16299 이상 이어야 함).</span><span class="sxs-lookup"><span data-stu-id="28a02-164">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="28a02-165">**빌드** 를 클릭한 다음</span><span class="sxs-lookup"><span data-stu-id="28a02-165">Click **Build** .</span></span>
6. <span data-ttu-id="28a02-166">"App" 이라는 **새 폴더** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-166">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="28a02-167">단일 **앱** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-167">Single click the **App** folder.</span></span>
8. <span data-ttu-id="28a02-168">**폴더 선택** 을 클릭 하면 Unity에서 Visual Studio 용 프로젝트 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-168">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="28a02-169">Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-169">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="28a02-170">**앱** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-170">Open the **App** folder.</span></span>
2. <span data-ttu-id="28a02-171">**모델 탐색기 Visual Studio 솔루션** 을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-171">Open the **ModelExplorer Visual Studio Solution** .</span></span>

<span data-ttu-id="28a02-172">HoloLens에 배포 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="28a02-172">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="28a02-173">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86** 으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-173">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86** .</span></span>
2. <span data-ttu-id="28a02-174">로컬 컴퓨터 단추 옆에 있는 드롭다운 화살표를 클릭 하 고 **원격 컴퓨터** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-174">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine** .</span></span>
3. <span data-ttu-id="28a02-175">**HoloLens 장치 IP 주소** 를 입력 하 고 인증 모드를 **유니버설 (암호화 되지 않은 프로토콜)** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-175">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)** .</span></span> <span data-ttu-id="28a02-176">**선택** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-176">Click **Select** .</span></span> <span data-ttu-id="28a02-177">장치 IP 주소를 모르는 경우 **네트워크 & 인터넷 > 고급 옵션 > 설정** 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28a02-177">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** .</span></span>
4. <span data-ttu-id="28a02-178">상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5** 를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-178">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5** .</span></span> <span data-ttu-id="28a02-179">처음으로 장치에 배포 하는 경우에는 [Visual Studio와 쌍](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)으로 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-179">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="28a02-180">앱이 배포 되 면 **선택 제스처로** **fitbox** 를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-180">When the app has deployed, dismiss the **Fitbox** with a **select gesture** .</span></span>

<span data-ttu-id="28a02-181">모던 헤드셋에 배포 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="28a02-181">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="28a02-182">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 x **64** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64** .</span></span>
2. <span data-ttu-id="28a02-183">배포 대상이 **로컬 컴퓨터** 로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-183">Make sure the deployment target is set to **Local Machine** .</span></span>
3. <span data-ttu-id="28a02-184">상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5** 를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-184">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5** .</span></span>
4. <span data-ttu-id="28a02-185">앱이 배포 되 면 동작 컨트롤러에서 트리거를 당겨 **Fitbox** 를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-185">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="28a02-186">Visual Studio 오류 패널에 몇 가지 빨간색 오류가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-186">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="28a02-187">무시 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-187">It is safe to ignore them.</span></span> <span data-ttu-id="28a02-188">출력 패널로 전환 하 여 실제 빌드 진행률을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-188">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="28a02-189">출력 패널에 오류가 발생 하면 문제를 해결 해야 합니다 (대부분 스크립트에서 실수로 인해 발생 하는 경우).</span><span class="sxs-lookup"><span data-stu-id="28a02-189">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="28a02-190">1 장-인식</span><span class="sxs-lookup"><span data-stu-id="28a02-190">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="28a02-191">목표</span><span class="sxs-lookup"><span data-stu-id="28a02-191">Objectives</span></span>

* <span data-ttu-id="28a02-192">음성 명령 디자인의 **일과 및 Dos** 에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-192">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="28a02-193">**KeywordRecognizer** 를 사용 하 여 응시 기반 음성 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-193">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="28a02-194">사용자가 커서 **피드백** 을 사용 하 여 음성 명령을 인식 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-194">Make users aware of voice commands using cursor **feedback** .</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="28a02-195">음성 명령 디자인</span><span class="sxs-lookup"><span data-stu-id="28a02-195">Voice Command Design</span></span>

<span data-ttu-id="28a02-196">이 장에서는 음성 명령을 디자인 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-196">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="28a02-197">음성 명령을 만들 때:</span><span class="sxs-lookup"><span data-stu-id="28a02-197">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="28a02-198">DO</span><span class="sxs-lookup"><span data-stu-id="28a02-198">DO</span></span>

* <span data-ttu-id="28a02-199">간결한 명령을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-199">Create concise commands.</span></span> <span data-ttu-id="28a02-200">*"현재 선택한 비디오 재생"* 을 사용 하지 않으려는 경우에는 해당 명령이 간결 하지 않으며 사용자가 쉽게 잊어버린 것입니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-200">You don't want to use *"Play the currently selected video"* , because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="28a02-201">대신 *"Play Video"* 를 사용 해야 합니다 .이는 간결 하 고 여러 음절을 포함 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-201">Instead, you should use: *"Play Video"* , because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="28a02-202">간단한 어휘를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-202">Use a simple vocabulary.</span></span> <span data-ttu-id="28a02-203">사용자가 쉽게 검색 하 고 기억할 수 있는 일반적인 단어와 구를 항상 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="28a02-203">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="28a02-204">예를 들어 응용 프로그램에 보기에서 표시 하거나 숨길 수 있는 note 개체가 있는 경우 "카드"는 거의 사용 되지 않는 용어 이므로 *"Show 카드"* 명령을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-204">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"* , because "placard" is a rarely used term.</span></span> <span data-ttu-id="28a02-205">대신 *"메모 표시"* 명령을 사용 하 여 응용 프로그램에 메모를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-205">Instead, you would use the command: *"Show Note"* , to reveal the note in your application.</span></span>
* <span data-ttu-id="28a02-206">일관 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-206">Be consistent.</span></span> <span data-ttu-id="28a02-207">음성 명령은 응용 프로그램 전체에서 일관 되 게 유지 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-207">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="28a02-208">응용 프로그램에 두 가지 장면이 있고 두 장면 모두에 응용 프로그램을 닫는 단추가 포함 되어 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-208">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="28a02-209">첫 번째 장면에서 *"Exit"* 명령을 사용 하 여 단추를 트리거하고 두 번째 장면에서 *"응용 프로그램 닫기"* 명령을 사용 하는 경우 사용자는 혼동을 발생 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-209">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"* , then the user is going to get very confused.</span></span> <span data-ttu-id="28a02-210">동일한 기능이 여러 장면에서 지속 되는 경우이를 트리거하기 위해 동일한 음성 명령을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-210">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="28a02-211">안 함</span><span class="sxs-lookup"><span data-stu-id="28a02-211">DON'T</span></span>

* <span data-ttu-id="28a02-212">단일 음절 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-212">Use single syllable commands.</span></span> <span data-ttu-id="28a02-213">예를 들어 비디오를 재생 하는 음성 명령을 만든 경우 간단한 명령 *"play"* 를 사용 하지 않는 것이 좋습니다 .이는 단일 음절 이며 시스템에서 쉽게 누락 될 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-213">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"* , as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="28a02-214">대신 *"Play Video"* 를 사용 해야 합니다 .이는 간결 하 고 여러 음절을 포함 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-214">Instead, you should use: *"Play Video"* , because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="28a02-215">시스템 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-215">Use system commands.</span></span> <span data-ttu-id="28a02-216">*"Select"* 명령은 현재 포커스가 있는 개체에 대 한 탭 이벤트를 트리거하기 위해 시스템에 예약 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-216">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="28a02-217">원하는 대로 작동 하지 않을 수 있으므로 키워드 또는 구에 *"Select"* 명령을 다시 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="28a02-217">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="28a02-218">예를 들어 응용 프로그램에서 큐브를 선택 하는 음성 명령이 *"Select cube"* 이지만 사용자가 명령을 재생 때 구를 확인 하는 경우 구가 대신 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-218">For example, if the voice command for selecting a cube in your application was *"Select cube"* , but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="28a02-219">비슷하게 앱 바 명령은 음성으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-219">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="28a02-220">CoreWindow 보기에서 다음 음성 명령을 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="28a02-220">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="28a02-221">뒤로 이동</span><span class="sxs-lookup"><span data-stu-id="28a02-221">Go Back</span></span>
    2. <span data-ttu-id="28a02-222">스크롤 도구</span><span class="sxs-lookup"><span data-stu-id="28a02-222">Scroll Tool</span></span>
    3. <span data-ttu-id="28a02-223">확대/축소 도구</span><span class="sxs-lookup"><span data-stu-id="28a02-223">Zoom Tool</span></span>
    4. <span data-ttu-id="28a02-224">끌기 도구</span><span class="sxs-lookup"><span data-stu-id="28a02-224">Drag Tool</span></span>
    5. <span data-ttu-id="28a02-225">Adjust</span><span class="sxs-lookup"><span data-stu-id="28a02-225">Adjust</span></span>
    6. <span data-ttu-id="28a02-226">제거</span><span class="sxs-lookup"><span data-stu-id="28a02-226">Remove</span></span>
* <span data-ttu-id="28a02-227">비슷한 소리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-227">Use similar sounds.</span></span> <span data-ttu-id="28a02-228">Rhyme 음성 명령을 사용 하지 않도록 하십시오.</span><span class="sxs-lookup"><span data-stu-id="28a02-228">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="28a02-229">*"저장소 표시"* 및 *"자세히 표시"* 를 지 원하는 쇼핑 응용 프로그램이 있는 경우 다른 명령 중 하나를 사용 하 고 있는 동안에는 명령 중 하나를 사용 하지 않도록 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-229">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="28a02-230">예를 들어 *"저장소 표시"* 단추를 사용 하 여 저장소를 연 후 *"자세히 표시"* 명령을 사용 하 여 검색을 할 수 있도록 저장소가 표시 될 때 해당 명령을 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-230">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="28a02-231">Instructions</span><span class="sxs-lookup"><span data-stu-id="28a02-231">Instructions</span></span>

* <span data-ttu-id="28a02-232">Unity의 **계층** 패널에서 검색 도구를 사용 하 여 **holoComm_screen_mesh** 개체를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-232">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="28a02-233">**HoloComm_screen_mesh** 개체를 두 번 클릭 하 여 **화면** 에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-233">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene** .</span></span> <span data-ttu-id="28a02-234">음성 명령에 응답 하는 astronaut의 조사식입니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-234">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="28a02-235">**검사기** 패널에서 **음성 입력 원본 (스크립트)** 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-235">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="28a02-236">**키워드** 섹션을 확장 하 여 지원 되는 음성 명령: **Communicator 열기** 를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-236">Expand the **Keywords** section to see the supported voice command: **Open Communicator** .</span></span>
* <span data-ttu-id="28a02-237">오른쪽의 코그를 클릭 한 다음 **스크립트 편집** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-237">Click the cog to the right side, then select **Edit Script** .</span></span>
* <span data-ttu-id="28a02-238">**SpeechInputSource.cs** 를 탐색 하 여 **KeywordRecognizer** 를 사용 하 여 음성 명령을 추가 하는 방법을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-238">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="28a02-239">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="28a02-239">Build and Deploy</span></span>

* <span data-ttu-id="28a02-240">Unity에서 **파일 > 빌드 설정을** 사용 하 여 응용 프로그램을 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-240">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="28a02-241">**앱** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-241">Open the **App** folder.</span></span>
* <span data-ttu-id="28a02-242">**모델 탐색기 Visual Studio 솔루션** 을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-242">Open the **ModelExplorer Visual Studio Solution** .</span></span>

<span data-ttu-id="28a02-243">설정 하는 동안 Visual Studio에서이 프로젝트를 이미 빌드/배포한 경우 해당 인스턴스를 열고 메시지가 표시 되 면 다시 로드를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-243">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="28a02-244">Visual Studio에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5** 를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-244">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5** .</span></span>
* <span data-ttu-id="28a02-245">응용 프로그램을 HoloLens에 배포한 후에는 마우스를 [탭](../../../design/gaze-and-commit.md#composite-gestures) 제스처를 사용 하 여 맞춤 상자를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-245">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](../../../design/gaze-and-commit.md#composite-gestures) gesture.</span></span>
* <span data-ttu-id="28a02-246">Astronaut의 조사식을 응시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-246">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="28a02-247">Watch에 포커스가 있는 경우 커서가 마이크로로 변경 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-247">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="28a02-248">그러면 응용 프로그램이 음성 명령을 수신 대기 하는 것으로 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-248">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="28a02-249">도구 설명이 조사식에 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-249">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="28a02-250">그러면 사용자가 *"Communicator 열기"* 명령을 검색 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-250">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="28a02-251">Gazing 하는 동안 *"Communicator 열기"* 라고 communicator 패널을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-251">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="28a02-252">2 장-승인</span><span class="sxs-lookup"><span data-stu-id="28a02-252">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="28a02-253">목표</span><span class="sxs-lookup"><span data-stu-id="28a02-253">Objectives</span></span>

* <span data-ttu-id="28a02-254">마이크 입력을 사용 하 여 메시지를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-254">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="28a02-255">응용 프로그램이 자신의 음성을 수신 대기 하 고 있음을 사용자에 게 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-255">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="28a02-256">마이크에서 녹음할 앱에 대해 **마이크** 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-256">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="28a02-257">이러한 작업은 이미 MR 입력 212에 대해 수행 되지만 사용자 고유의 프로젝트에 대해서는이를 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-257">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="28a02-258">Unity 편집기에서 "편집 > 프로젝트 설정 > 플레이어"로 이동 하 여 플레이어 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-258">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="28a02-259">"유니버설 Windows 플랫폼" 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-259">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="28a02-260">"게시 설정 > 기능" 섹션에서 **마이크** 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-260">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="28a02-261">Instructions</span><span class="sxs-lookup"><span data-stu-id="28a02-261">Instructions</span></span>

* <span data-ttu-id="28a02-262">Unity의 **계층 구조** 패널에서 **holoComm_screen_mesh** 개체가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-262">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="28a02-263">**검사기** 패널에서 **Astronaut Watch (스크립트)** 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-263">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="28a02-264">**Communicator Prefab** 속성의 값으로 설정 된 작은 파란색 큐브를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-264">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="28a02-265">이제 **프로젝트** 패널에서 **Communicator** prefab에 포커스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-265">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="28a02-266">**프로젝트** 패널에서 **Communicator** prefab를 클릭 하 여 **검사기** 에서 해당 구성 요소를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-266">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector** .</span></span>
* <span data-ttu-id="28a02-267">**마이크 관리자 (스크립트)** 구성 요소를 살펴보면 사용자의 음성을 기록 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-267">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="28a02-268">**Communicator** 개체에는 **메시지 보내기** 명령에 응답 하기 위한 **음성 입력 처리기 (스크립트)** 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-268">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="28a02-269">**Communicator (스크립트)** 구성 요소를 확인 하 고 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-269">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="28a02-270">Communicator.cs는 communicator 장치에서 적절 한 단추 상태를 설정 하는 일을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-270">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="28a02-271">이렇게 하면 사용자가 메시지를 기록 하 고, 다시 재생 하 고, 메시지를 astronaut으로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-271">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="28a02-272">또한 애니메이션이 적용 된 웨이브 폼을 시작 하 고 중지 하 여 사용자에 게 음성이 들리는지를 승인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-272">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="28a02-273">**Communicator.cs** 에서 **Start** 메서드에서 다음 줄 (81 및 82)을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-273">In **Communicator.cs** , delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="28a02-274">그러면 communicator에서 ' 레코드 ' 단추가 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-274">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="28a02-275">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="28a02-275">Build and Deploy</span></span>

* <span data-ttu-id="28a02-276">Visual Studio에서 응용 프로그램을 다시 빌드하고 장치에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-276">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="28a02-277">Astronaut의 감시를 응시 하 고 communicator를 표시 하는 *"Open communicator"* 라고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-277">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="28a02-278">Astronaut에 대 한 구두 메시지 기록을 시작 하려면 **녹음** 단추 (마이크)를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-278">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="28a02-279">말하기를 시작 하 고 사용자에 게 음성이 들리는지 사용자에 게 피드백을 제공 하는 웨이브 애니메이션이 communicator에서 재생 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-279">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="28a02-280">**중지** 단추 (왼쪽 사각형)를 누르고 웨이브 애니메이션의 실행이 중지 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-280">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="28a02-281">**재생** 단추 (오른쪽 삼각형)를 눌러 기록 된 메시지를 재생 하 고 장치에서이를 듣습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-281">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="28a02-282">**중지** 단추 (오른쪽 사각형)를 눌러 기록 된 메시지의 재생을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-282">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="28a02-283">*"메시지 보내기"* 를 통해 communicator를 닫고 astronaut에서 ' message Received ' 응답을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-283">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="28a02-284">3 장-및 받아쓰기 인식기 이해</span><span class="sxs-lookup"><span data-stu-id="28a02-284">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="28a02-285">목표</span><span class="sxs-lookup"><span data-stu-id="28a02-285">Objectives</span></span>

* <span data-ttu-id="28a02-286">받아쓰기 인식기를 사용 하 여 사용자의 음성을 텍스트로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-286">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="28a02-287">Communicator에서 받아쓰기 인식기의 가설 및 최종 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-287">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="28a02-288">이 장에서는 받아쓰기 인식기를 사용 하 여 astronaut에 대 한 메시지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-288">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="28a02-289">받아쓰기 인식기를 사용 하는 경우 다음을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-289">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="28a02-290">받아쓰기 인식기가 작동 하려면 WiFi에 연결 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-290">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="28a02-291">시간 제한은 설정 된 시간 후에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-291">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="28a02-292">다음 두 가지 제한 시간을 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-292">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="28a02-293">인식기가 시작 되 고 처음 5 초 동안 오디오가 들리지 않으면 시간이 초과 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-293">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="28a02-294">인식기가 결과를 제공 했지만 20 초 동안 침묵 소음을 받은 경우 시간이 초과 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-294">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="28a02-295">한 번에 하나의 인식기 유형 (키워드 또는 받아쓰기)만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-295">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="28a02-296">마이크에서 녹음할 앱에 대해 **마이크** 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-296">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="28a02-297">이러한 작업은 이미 MR 입력 212에 대해 수행 되지만 사용자 고유의 프로젝트에 대해서는이를 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-297">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="28a02-298">Unity 편집기에서 "편집 > 프로젝트 설정 > 플레이어"로 이동 하 여 플레이어 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-298">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="28a02-299">"유니버설 Windows 플랫폼" 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-299">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="28a02-300">"게시 설정 > 기능" 섹션에서 **마이크** 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-300">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="28a02-301">Instructions</span><span class="sxs-lookup"><span data-stu-id="28a02-301">Instructions</span></span>

<span data-ttu-id="28a02-302">받아쓰기 인식기를 사용 하도록 **MicrophoneManager.cs** 를 편집 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-302">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="28a02-303">다음을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-303">This is what we'll add:</span></span>

1. <span data-ttu-id="28a02-304">**기록 단추** 를 누르면 **DictationRecognizer이 시작** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-304">When the **Record button** is pressed, we'll **start the DictationRecognizer** .</span></span>
2. <span data-ttu-id="28a02-305">DictationRecognizer가 이해 하는 사항의 **가설** 을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-305">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="28a02-306">DictationRecognizer가 이해 한 **결과** 를 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-306">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="28a02-307">DictationRecognizer에서 시간 제한을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-307">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="28a02-308">**중지 단추** 를 누르거나 mic 세션이 시간 초과 되 면 **DictationRecognizer를 중지** 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-308">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer** .</span></span>
6. <span data-ttu-id="28a02-309">**메시지 보내기** 명령을 수신 대기 하는 **KeywordRecognizer** 를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-309">Restart the **KeywordRecognizer** , which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="28a02-310">이제 시작하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-310">Let's get started.</span></span> <span data-ttu-id="28a02-311">**MicrophoneManager.cs** 에서 3. a에 대 한 모든 코딩 연습을 완료 하거나 아래에 있는 완성 된 코드를 복사 하 여 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-311">Complete all coding exercises for 3.a in **MicrophoneManager.cs** , or copy and paste the finished code found below:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="28a02-312">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="28a02-312">Build and Deploy</span></span>

* <span data-ttu-id="28a02-313">Visual Studio에서 다시 빌드하고 장치에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-313">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="28a02-314">공기 탭 제스처를 사용 하 여 맞춤 상자를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-314">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="28a02-315">Astronaut의 감시를 응시 하 고 *"Communicator Open"* 이라고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-315">Gaze at the astronaut's watch and say *"Open Communicator"* .</span></span>
* <span data-ttu-id="28a02-316">**녹음** 단추 (마이크)를 선택 하 여 메시지를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-316">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="28a02-317">말하기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-317">Start speaking.</span></span> <span data-ttu-id="28a02-318">**받아쓰기 인식기** 는 음성을 해석 하 고, communicator에 가설 텍스트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-318">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="28a02-319">메시지를 기록 하는 동안 *"메시지 보내기"* 를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="28a02-319">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="28a02-320">**받아쓰기 인식기** 가 여전히 활성 상태 이므로 **키워드 인식기** 가 응답 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-320">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="28a02-321">몇 초 동안 말하기를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-321">Stop speaking for a few seconds.</span></span> <span data-ttu-id="28a02-322">받아쓰기 인식기가 가설을 완료 하 고 최종 결과를 표시 하는 것을 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="28a02-322">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="28a02-323">읽어주기를 시작한 후 20 초 동안 일시 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-323">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="28a02-324">이렇게 하면 **받아쓰기 인식기** 가 시간 초과 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-324">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="28a02-325">위의 제한 시간이 지나면 **키워드 인식기** 가 다시 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-325">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="28a02-326">이제 communicator가 음성 명령에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-326">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="28a02-327">Astronaut에 메시지를 보내기 위한 *"메시지 보내기"* 라고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-327">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="28a02-328">4 장-문법 인식기</span><span class="sxs-lookup"><span data-stu-id="28a02-328">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="28a02-329">목표</span><span class="sxs-lookup"><span data-stu-id="28a02-329">Objectives</span></span>

* <span data-ttu-id="28a02-330">문법 인식기를 사용 하 여 SRGS 또는 음성 인식 문법 사양 파일에 따라 사용자 음성을 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-330">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="28a02-331">마이크에서 녹음할 앱에 대해 **마이크** 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-331">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="28a02-332">이러한 작업은 이미 MR 입력 212에 대해 수행 되지만 사용자 고유의 프로젝트에 대해서는이를 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-332">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="28a02-333">Unity 편집기에서 "편집 > 프로젝트 설정 > 플레이어"로 이동 하 여 플레이어 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-333">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="28a02-334">"유니버설 Windows 플랫폼" 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-334">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="28a02-335">"게시 설정 > 기능" 섹션에서 **마이크** 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-335">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="28a02-336">Instructions</span><span class="sxs-lookup"><span data-stu-id="28a02-336">Instructions</span></span>

1. <span data-ttu-id="28a02-337">**계층** 패널에서 **Jetpack_Center** 을 검색 하 고 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-337">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="28a02-338">**검사기** 패널에서 **Tagalong Action** 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-338">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="28a02-339">개체의 오른쪽에 있는 작은 원을 클릭 하 여 필드 **에 태그를 추가할 수** 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-339">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="28a02-340">팝업 창이 표시 되 면 **Srgstoolbox** 를 검색 하 고 목록에서 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-340">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="28a02-341">**Streamingassets** 폴더에서 **SRGSColor.xml** 파일을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-341">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
    1. <span data-ttu-id="28a02-342">SRGS 디자인 사양은 [여기](https://www.w3.org/TR/speech-grammar/)의 W3C 웹 사이트에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-342">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>

<span data-ttu-id="28a02-343">SRGS 파일에는 다음과 같은 세 가지 유형의 규칙이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-343">In our SRGS file, we have three types of rules:</span></span>

* <span data-ttu-id="28a02-344">12 색 목록에서 한 색을 표시할 수 있는 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-344">A rule which lets you say one color from a list of twelve colors.</span></span>
* <span data-ttu-id="28a02-345">색 규칙과 세 도형 중 하나를 조합 하 여 수신 대기 하는 세 가지 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-345">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
* <span data-ttu-id="28a02-346">3 가지 "color + shape" 규칙의 조합을 수신 하는 루트 규칙 colorChooser입니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-346">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="28a02-347">도형은 임의의 순서로 정렬 하 고 1부터 모두 세까지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-347">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="28a02-348">이 규칙은 초기 문법 태그에서 파일의 맨 위에 루트 규칙으로 지정 되므로에 대해 수신 됩니다 &lt; &gt; .</span><span class="sxs-lookup"><span data-stu-id="28a02-348">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="28a02-349">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="28a02-349">Build and Deploy</span></span>

* <span data-ttu-id="28a02-350">Unity에서 응용 프로그램을 다시 빌드한 다음, Visual Studio에서 빌드 및 배포 하 여 HoloLens에서 앱을 경험해 보세요.</span><span class="sxs-lookup"><span data-stu-id="28a02-350">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="28a02-351">공기 탭 제스처를 사용 하 여 맞춤 상자를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-351">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="28a02-352">Astronaut의 jetpack을 응시 하 고 공중 탭 제스처를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-352">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="28a02-353">말하기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-353">Start speaking.</span></span> <span data-ttu-id="28a02-354">**문법 인식기** 는 음성을 해석 하 고 인식에 따라 셰이프의 색을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-354">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="28a02-355">예제 명령은 "파란색 원, 노란색 사각형"입니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-355">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="28a02-356">다른 공기 탭 제스처를 수행 하 여 도구 상자를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-356">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="28a02-357">끝</span><span class="sxs-lookup"><span data-stu-id="28a02-357">The End</span></span>

<span data-ttu-id="28a02-358">축하합니다!</span><span class="sxs-lookup"><span data-stu-id="28a02-358">Congratulations!</span></span> <span data-ttu-id="28a02-359">이제 **MR 입력 212: Voice** 가 완료 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-359">You have now completed **MR Input 212: Voice** .</span></span>

* <span data-ttu-id="28a02-360">음성 명령의 Dos 및 일과을 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-360">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="28a02-361">사용자가 음성 명령을 인식 하도록 도구 설명을 사용 하는 방법을 살펴보았습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-361">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="28a02-362">사용자의 음성이 들리는지 확인 하는 데 사용 되는 다양 한 유형의 피드백이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-362">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="28a02-363">키워드 인식자와 받아쓰기 인식기 사이를 전환 하는 방법 및 이러한 두 기능이 음성을 이해 하 고 해석 하는 방법을 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-363">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="28a02-364">응용 프로그램에서 음성 인식을 위해 SRGS 파일 및 문법 인식기를 사용 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="28a02-364">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>