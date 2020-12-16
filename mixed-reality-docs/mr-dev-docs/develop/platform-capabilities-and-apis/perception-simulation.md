---
title: 인식 시뮬레이션
description: 인식 시뮬레이션 라이브러리를 사용 하 여 몰입 형 응용 프로그램의 시뮬레이션 된 입력을 자동화 하는 방법에 대 한 지침
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, 시뮬레이션, 테스트
ms.openlocfilehash: 64028c3a1ad58cecfebc93aee325b73c3a6a649a
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530401"
---
# <a name="perception-simulation"></a><span data-ttu-id="eb0b6-104">인식 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="eb0b6-104">Perception simulation</span></span>

<span data-ttu-id="eb0b6-105">앱에 대 한 자동화 된 테스트를 빌드 하시 겠어요?</span><span class="sxs-lookup"><span data-stu-id="eb0b6-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="eb0b6-106">테스트를 구성 요소 수준 단위 테스트 이상으로 전환 하 고 응용 프로그램을 종단 간에 실행 하 시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="eb0b6-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="eb0b6-107">인식 시뮬레이션은 원하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="eb0b6-108">인식 시뮬레이션 라이브러리는 테스트를 자동화할 수 있도록 사용자 및 세계 입력 데이터를 앱에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="eb0b6-109">예를 들어, 반복 가능한 특정 위치를 찾고 제스처 나 동작 컨트롤러를 사용 하는 사용자의 입력을 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then use a gesture or motion controller.</span></span>

<span data-ttu-id="eb0b6-110">인식 시뮬레이션은이를 실제 HoloLens, HoloLens 에뮬레이터 (최초의 gen), HoloLens 2 에뮬레이터 또는 혼합 현실 포털이 설치 된 PC와 같은 시뮬레이트된 입력을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (first gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="eb0b6-111">인식 시뮬레이션은 혼합 현실 장치에서 라이브 센서를 우회 하 고 장치에서 실행 되는 응용 프로그램에 시뮬레이트된 입력을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="eb0b6-112">응용 프로그램은 항상 사용 하는 것과 동일한 Api를 통해 이러한 입력 이벤트를 수신 하 고 실제 센서와 인식 시뮬레이션을 사용 하 여 실행 하는 방법에 대 한 차이점</span><span class="sxs-lookup"><span data-stu-id="eb0b6-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus Perception Simulation.</span></span> <span data-ttu-id="eb0b6-113">인식 시뮬레이션은 hololens 에뮬레이터에서 HoloLens 가상 컴퓨터에 시뮬레이트된 입력을 보내기 위해 사용 하는 것과 동일한 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="eb0b6-114">코드에서 시뮬레이션 사용을 시작 하려면 먼저 IPerceptionSimulationManager 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="eb0b6-115">해당 개체에서 헤드 위치, 손 모양 및 제스처를 포함 하 여 시뮬레이션 된 "휴먼"의 속성을 제어 하는 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span> <span data-ttu-id="eb0b6-116">동작 컨트롤러를 사용 하도록 설정 하 고 조작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-116">You can also enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="eb0b6-117">인식 시뮬레이션에 대 한 Visual Studio 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="eb0b6-117">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="eb0b6-118">개발 PC에 [HoloLens 에뮬레이터를 설치](../install-the-tools.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-118">[Install the HoloLens emulator](../install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="eb0b6-119">에뮬레이터는 인식 시뮬레이션에 사용 하는 라이브러리를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-119">The emulator includes the libraries you' use for Perception Simulation.</span></span>
2. <span data-ttu-id="eb0b6-120">새 Visual Studio c # 데스크톱 프로젝트를 만듭니다. 콘솔 프로젝트는 시작 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-120">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="eb0b6-121">프로젝트에 다음 이진 파일을 참조 (프로젝트 >추가 >참조 ...)로 추가 합니다. % ProgramFiles (x86)% \ Microsoft XDE \\ (버전) (예: HoloLens 2 에뮬레이터의 경우 **% ProgramFiles (x86)% \ microsoft xde \\ 10.0.18362.0** )에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-121">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="eb0b6-122">(참고: 이진 파일은 HoloLens 2 에뮬레이터의 일부 이지만 바탕 화면에서 Windows Mixed Reality에도 작동 합니다.) 은.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-122">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="eb0b6-123">인식 시뮬레이션에 대 한 PerceptionSimulationManager.Interop.dll 관리 c # 래퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-123">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="eb0b6-124">b.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-124">b.</span></span> <span data-ttu-id="eb0b6-125">PerceptionSimulationRest.dll-웹 소켓 통신 채널을 HoloLens 또는 에뮬레이터에 설정 하기 위한 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-125">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="eb0b6-126">c.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-126">c.</span></span> <span data-ttu-id="eb0b6-127">시뮬레이션을 위한 SimulationStream.Interop.dll 공유 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-127">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="eb0b6-128">프로젝트 a에 구현 이진 PerceptionSimulationManager.dll를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-128">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="eb0b6-129">먼저 프로젝트에 이진으로 추가 합니다 (기존 항목 >추가 >). 프로젝트 원본 폴더에 복사 하지 않도록 링크를 링크로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-129">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="eb0b6-130">![프로젝트에 PerceptionSimulationManager.dll을 링크 b로 추가 ](images/saveaslink.png) 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-130">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="eb0b6-131">그런 다음 빌드 시 출력 폴더에 복사 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-131">Then make sure that it gets copied to your output folder on build.</span></span> <span data-ttu-id="eb0b6-132">이는 이진의 속성 시트에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-132">This is in the property sheet for the binary.</span></span> <span data-ttu-id="eb0b6-133">![출력 디렉터리에 복사 PerceptionSimulationManager.dll 표시](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="eb0b6-133">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="eb0b6-134">활성 솔루션 플랫폼을 x 64로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-134">Set your active solution platform to x64.</span></span>  <span data-ttu-id="eb0b6-135">(아직 없는 경우 Configuration Manager를 사용 하 여 x 64에 대 한 플랫폼 항목을 만듭니다.)</span><span class="sxs-lookup"><span data-stu-id="eb0b6-135">(Use the Configuration Manager to create a Platform entry for x64 if one doesn't already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="eb0b6-136">IPerceptionSimulation Manager 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="eb0b6-136">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="eb0b6-137">시뮬레이션을 제어 하기 위해 IPerceptionSimulationManager 개체에서 검색 된 개체에 대 한 업데이트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-137">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="eb0b6-138">첫 번째 단계는 해당 개체를 가져와 대상 장치 또는 에뮬레이터에 연결 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-138">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="eb0b6-139">[도구 모음](using-the-hololens-emulator.md) 에서 장치 포털 단추를 클릭 하 여 에뮬레이터의 IP 주소를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-139">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="eb0b6-140">![장치 포털 열기 아이콘 ](images/emulator-deviceportal.png) **장치 포털**: 에뮬레이터에서 HoloLens OS에 대 한 Windows 장치 포털을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-140">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="eb0b6-141">Windows Mixed Reality의 경우 "업데이트 & 보안" 아래의 설정 앱에서 "장치 포털 사용"의 "연결 사용:" 섹션에 있는 "개발자 용" 섹션에서 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-141">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="eb0b6-142">IP 주소와 포트를 모두 기록해 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-142">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="eb0b6-143">먼저 RestSimulationStreamSink를 호출 하 여 RestSimulationStreamSink 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-143">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="eb0b6-144">Http 연결을 제어 하는 대상 장치 또는 에뮬레이터입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-144">This is the target device or emulator that you'll control over an http connection.</span></span> <span data-ttu-id="eb0b6-145">명령은 장치 또는 에뮬레이터에서 실행 되는 [Windows 장치 포털](using-the-windows-device-portal.md) 에 전달 되 고 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-145">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="eb0b6-146">개체를 만드는 데 필요한 네 가지 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-146">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="eb0b6-147">Uri uri-대상 장치의 IP 주소 (예: " https://123.123.123.123 " 또는 " https://123.123.123.123:50080 ")</span><span class="sxs-lookup"><span data-stu-id="eb0b6-147">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="eb0b6-148">시스템 .Net. NetworkCredential 자격 증명-대상 장치 또는 에뮬레이터의 [Windows 장치 포털](using-the-windows-device-portal.md) 에 연결 하기 위한 사용자 이름/암호입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-148">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="eb0b6-149">로컬 주소를 통해 에뮬레이터에 연결 하는 경우 (예:*168 ...* \*) 같은 PC에서 모든 자격 증명이 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-149">If you're connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="eb0b6-150">bool normal-보통 우선 순위의 경우 True, 낮은 우선 순위의 경우 false</span><span class="sxs-lookup"><span data-stu-id="eb0b6-150">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="eb0b6-151">일반적으로 테스트 시나리오의 경우이를 *true* 로 설정 하 여 테스트를 제어할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-151">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="eb0b6-152">에뮬레이터 및 Windows Mixed Reality 시뮬레이션에서는 우선 순위가 낮은 연결을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-152">The emulator and Windows Mixed Reality simulation use low-priority connections.</span></span>  <span data-ttu-id="eb0b6-153">또한 테스트에서 우선 순위가 낮은 연결을 사용 하는 경우 가장 최근에 설정 된 연결이 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-153">If your test also uses a low-priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="eb0b6-154">CancellationToken 토큰-비동기 작업을 취소 하는 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-154">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="eb0b6-155">둘째, IPerceptionSimulationManager를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-155">Second, you'll create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="eb0b6-156">시뮬레이션을 제어 하는 데 사용 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-156">This is the object you use to control simulation.</span></span> <span data-ttu-id="eb0b6-157">비동기 메서드에서도이 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-157">This must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="eb0b6-158">시뮬레이션 된 사용자 제어</span><span class="sxs-lookup"><span data-stu-id="eb0b6-158">Control the simulated Human</span></span>

<span data-ttu-id="eb0b6-159">IPerceptionSimulationManager에는 ISimulatedHuman 개체를 반환 하는 인적 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-159">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="eb0b6-160">시뮬레이션 된 사용자를 제어 하려면이 개체에 대 한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-160">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="eb0b6-161">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-161">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="eb0b6-162">기본 샘플 c # 콘솔 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="eb0b6-162">Basic Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="eb0b6-163">확장 된 샘플 c # 콘솔 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="eb0b6-163">Extended Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="eb0b6-164">6-DOF 컨트롤러에 대 한 참고 사항</span><span class="sxs-lookup"><span data-stu-id="eb0b6-164">Note on 6-DOF controllers</span></span>

<span data-ttu-id="eb0b6-165">시뮬레이션 된 6 DOF controller의 메서드에 대 한 속성을 호출 하기 전에 컨트롤러를 활성화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-165">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="eb0b6-166">이렇게 하지 않으면 예외가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-166">Not doing so will result in an exception.</span></span>  <span data-ttu-id="eb0b6-167">Windows 10 2019 년 5 월 업데이트부터 ISimulatedSixDofController 개체의 Status 속성을 SimulatedSixDofControllerStatus로 설정 하 여 시뮬레이션 된 6 DOF 컨트롤러를 설치 하 고 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-167">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="eb0b6-168">Windows 10 10 월 2018 업데이트 및 그 이전 버전에서는 \Windows\System32 폴더에 있는 PerceptionSimulationDevice 도구를 호출 하 여 시뮬레이션 된 6-DOF 컨트롤러를 별도로 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-168">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="eb0b6-169">이 도구의 사용법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-169">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="eb0b6-170">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-170">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="eb0b6-171">지원 되는 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-171">Supported actions are:</span></span>
* <span data-ttu-id="eb0b6-172">i = 설치</span><span class="sxs-lookup"><span data-stu-id="eb0b6-172">i = install</span></span>
* <span data-ttu-id="eb0b6-173">q = 쿼리</span><span class="sxs-lookup"><span data-stu-id="eb0b6-173">q = query</span></span>
* <span data-ttu-id="eb0b6-174">r = 제거</span><span class="sxs-lookup"><span data-stu-id="eb0b6-174">r = remove</span></span>

<span data-ttu-id="eb0b6-175">지원 되는 인스턴스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-175">Supported instances are:</span></span>
* <span data-ttu-id="eb0b6-176">1 = 왼쪽 6-DOF controller</span><span class="sxs-lookup"><span data-stu-id="eb0b6-176">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="eb0b6-177">2 = 오른쪽 6-DOF controller</span><span class="sxs-lookup"><span data-stu-id="eb0b6-177">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="eb0b6-178">프로세스의 종료 코드는 성공 (0이 아닌 반환 값) 또는 실패 (0이 아닌 반환 값)를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-178">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="eb0b6-179">' Q ' 작업을 사용 하 여 컨트롤러가 설치 되어 있는지 여부를 쿼리하려면 컨트롤러를 아직 설치 하지 않은 경우 반환 값은 0이 고, 컨트롤러가 설치 된 경우에는 (1)입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-179">When using the 'q' action to query whether a controller is installed, the return value will be zero (0) if the controller isn't already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="eb0b6-180">Windows 10 10 월 2018 업데이트 또는 그 이전 버전에서 컨트롤러를 제거 하는 경우 먼저 API를 통해 상태를 Off로 설정한 다음 PerceptionSimulationDevice 도구를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-180">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="eb0b6-181">이 도구는 관리자 권한으로 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-181">This tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="eb0b6-182">API 참조</span><span class="sxs-lookup"><span data-stu-id="eb0b6-182">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="eb0b6-183">PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="eb0b6-183">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="eb0b6-184">시뮬레이션 된 장치 유형을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-184">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="eb0b6-185">**PerceptionSimulation. SimulatedDeviceType**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-185">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="eb0b6-186">PerceptionSimulationManager에 대 한 기본값 인 가상의 참조 장치</span><span class="sxs-lookup"><span data-stu-id="eb0b6-186">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="eb0b6-187">PerceptionSimulation Ermode</span><span class="sxs-lookup"><span data-stu-id="eb0b6-187">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="eb0b6-188">헤드 추적 장치 모드를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-188">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="eb0b6-189">**PerceptionSimulation Ermode. 기본값**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-189">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="eb0b6-190">기본 헤드 추적입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-190">Default Head Tracking.</span></span> <span data-ttu-id="eb0b6-191">즉, 시스템에서 런타임 조건에 따라 가장 적합 한 헤드 추적 모드를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-191">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="eb0b6-192">**PerceptionSimulation입니다. 방향**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-192">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="eb0b6-193">방향 전용 헤드 추적입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-193">Orientation Only Head Tracking.</span></span> <span data-ttu-id="eb0b6-194">즉, 추적 된 위치는 신뢰할 수 없으며 헤드 위치에 종속 된 일부 기능을 사용 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-194">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="eb0b6-195">**PerceptionSimulation입니다. 위치**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-195">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="eb0b6-196">위치 헤드 추적.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-196">Positional Head Tracking.</span></span> <span data-ttu-id="eb0b6-197">즉, 추적 된 헤드 위치와 방향이 모두 안정적 임을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-197">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="eb0b6-198">PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="eb0b6-198">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="eb0b6-199">시뮬레이션 된 제스처를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-199">Describes a simulated gesture</span></span>

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

<span data-ttu-id="eb0b6-200">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-200">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="eb0b6-201">제스처를 표시 하는 데 사용 되는 센티널 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-201">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="eb0b6-202">**PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-202">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="eb0b6-203">손가락 누름 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-203">A finger pressed gesture.</span></span>

<span data-ttu-id="eb0b6-204">**PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-204">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="eb0b6-205">손가락이 해제 된 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-205">A finger released gesture.</span></span>

<span data-ttu-id="eb0b6-206">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-206">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="eb0b6-207">홈/시스템 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-207">The home/system gesture.</span></span>

<span data-ttu-id="eb0b6-208">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-208">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="eb0b6-209">최대 유효 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-209">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="eb0b6-210">PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="eb0b6-210">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="eb0b6-211">시뮬레이션 된 6 DOF controller의 가능한 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-211">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="eb0b6-212">**PerceptionSimulation. SimulatedSixDofControllerStatus**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-212">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="eb0b6-213">6-DOF 컨트롤러가 꺼져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-213">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="eb0b6-214">**PerceptionSimulation. SimulatedSixDofControllerStatus**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-214">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="eb0b6-215">6-DOF 컨트롤러를 켜고 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-215">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="eb0b6-216">**PerceptionSimulation. SimulatedSixDofControllerStatus**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-216">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="eb0b6-217">6-DOF 컨트롤러가 켜져 있지만 추적할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-217">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="eb0b6-218">PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="eb0b6-218">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="eb0b6-219">시뮬레이션 된 6 DOF 컨트롤러에서 지원 되는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-219">The supported buttons on a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

<span data-ttu-id="eb0b6-220">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-220">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="eb0b6-221">단추를 표시 하지 않는 데 사용 되는 센티널 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-221">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="eb0b6-222">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-222">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="eb0b6-223">홈 단추를 눌렀습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-223">The Home button is pressed.</span></span>

<span data-ttu-id="eb0b6-224">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-224">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="eb0b6-225">메뉴 단추가 눌러져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-225">The Menu button is pressed.</span></span>

<span data-ttu-id="eb0b6-226">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-226">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="eb0b6-227">그립 단추가 눌러져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-227">The Grip button is pressed.</span></span>

<span data-ttu-id="eb0b6-228">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-228">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="eb0b6-229">터치 패드가 눌러져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-229">The TouchPad is pressed.</span></span>

<span data-ttu-id="eb0b6-230">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-230">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="eb0b6-231">선택 단추가 눌러져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-231">The Select button is pressed.</span></span>

<span data-ttu-id="eb0b6-232">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-232">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="eb0b6-233">터치 패드가 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-233">The TouchPad is touched.</span></span>

<span data-ttu-id="eb0b6-234">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-234">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="eb0b6-235">엄지 스틱이 눌러져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-235">The Thumbstick is pressed.</span></span>

<span data-ttu-id="eb0b6-236">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-236">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="eb0b6-237">최대 유효 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-237">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="eb0b6-238">PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="eb0b6-238">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="eb0b6-239">시뮬레이션 된 눈동자의 보정 상태</span><span class="sxs-lookup"><span data-stu-id="eb0b6-239">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="eb0b6-240">**PerceptionSimulation. SimulatedEyesCalibrationState**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-240">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="eb0b6-241">눈동자 보정을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-241">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="eb0b6-242">**PerceptionSimulation. SimulatedEyesCalibrationState**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-242">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="eb0b6-243">눈이 보정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-243">The eyes have been calibrated.</span></span>  <span data-ttu-id="eb0b6-244">이것은 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-244">This is the default value.</span></span>

<span data-ttu-id="eb0b6-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configpostman**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="eb0b6-246">눈이 보정 되 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-246">The eyes are being calibrated.</span></span>

<span data-ttu-id="eb0b6-247">**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-247">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="eb0b6-248">눈동자를 보정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-248">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="eb0b6-249">PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="eb0b6-249">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="eb0b6-250">바늘의 조인트 추적 정확도입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-250">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="eb0b6-251">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-251">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="eb0b6-252">조인트는 추적 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-252">The joint isn't tracked.</span></span>

<span data-ttu-id="eb0b6-253">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-253">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="eb0b6-254">조인트 위치가 유추 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-254">The joint position is inferred.</span></span>

<span data-ttu-id="eb0b6-255">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-255">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="eb0b6-256">조인트는 완전히 추적 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-256">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="eb0b6-257">PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="eb0b6-257">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="eb0b6-258">바늘의 조인트 추적 정확도입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-258">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

<span data-ttu-id="eb0b6-259">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-259">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="eb0b6-260">손 모양 손가락 조인트는 닫힌 포즈를 반영 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-260">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="eb0b6-261">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-261">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="eb0b6-262">손 모양 손가락 조인트는 열린 포즈를 반영 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-262">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="eb0b6-263">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-263">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="eb0b6-264">손 모양 손가락 조인트는 포인팅 포즈를 반영 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-264">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="eb0b6-265">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-265">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="eb0b6-266">손 모양 손가락 조인트는 집기 포즈를 반영 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-266">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="eb0b6-267">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-267">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="eb0b6-268">SimulatedHandPose에 대 한 최대 유효 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-268">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="eb0b6-269">PerceptionSimulation.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-269">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="eb0b6-270">재생 상태를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-270">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="eb0b6-271">**PerceptionSimulation. 중지 됨**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-271">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="eb0b6-272">기록이 현재 중지 되었고 재생할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-272">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="eb0b6-273">**PerceptionSimulation. 재생 중**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-273">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="eb0b6-274">기록이 현재 재생 중입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-274">The recording is currently playing.</span></span>

<span data-ttu-id="eb0b6-275">**PerceptionSimulation. 일시 중지 됨**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-275">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="eb0b6-276">기록이 현재 일시 중지 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-276">The recording is currently paused.</span></span>

<span data-ttu-id="eb0b6-277">**PerceptionSimulation. 종료**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-277">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="eb0b6-278">기록이 끝에 도달 했습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-278">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="eb0b6-279">PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="eb0b6-279">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="eb0b6-280">3D 공간에서 점이 나 벡터를 설명할 수 있는 3 가지 구성 요소 벡터에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-280">Describes a three components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="eb0b6-281">**PerceptionSimulation. Vector3**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-281">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="eb0b6-282">벡터의 X 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-282">The X component of the vector.</span></span>

<span data-ttu-id="eb0b6-283">**PerceptionSimulation. Vector3**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-283">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="eb0b6-284">벡터의 Y 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-284">The Y component of the vector.</span></span>

<span data-ttu-id="eb0b6-285">**PerceptionSimulation. Vector3**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-285">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="eb0b6-286">벡터의 Z 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-286">The Z component of the vector.</span></span>

<span data-ttu-id="eb0b6-287">**PerceptionSimulation (System.web, system.web, System.web) (#ctor Vector3)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-287">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="eb0b6-288">새 Vector3를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-288">Construct a new Vector3.</span></span>

<span data-ttu-id="eb0b6-289">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-289">Parameters</span></span>
* <span data-ttu-id="eb0b6-290">x-벡터의 x 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-290">x - The x component of the vector.</span></span>
* <span data-ttu-id="eb0b6-291">y-벡터의 y 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-291">y - The y component of the vector.</span></span>
* <span data-ttu-id="eb0b6-292">z-벡터의 z 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-292">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="eb0b6-293">PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="eb0b6-293">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="eb0b6-294">3 가지 구성 요소 회전을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-294">Describes a three components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="eb0b6-295">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-295">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="eb0b6-296">X 축을 중심으로 하는 회전의 피치 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-296">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="eb0b6-297">**PerceptionSimulation. Rotation3. 요**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-297">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="eb0b6-298">Y 축을 중심으로 하는 회전의 요 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-298">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="eb0b6-299">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-299">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="eb0b6-300">Z 축을 중심으로 하는 회전의 롤 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-300">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="eb0b6-301">**PerceptionSimulation (System.web, system.web, System.web) (#ctor Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-301">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="eb0b6-302">새 Rotation3를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-302">Construct a new Rotation3.</span></span>

<span data-ttu-id="eb0b6-303">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-303">Parameters</span></span>
* <span data-ttu-id="eb0b6-304">피치-회전의 피치 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-304">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="eb0b6-305">요-회전의 요 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-305">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="eb0b6-306">roll-회전의 롤오버 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-306">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="eb0b6-307">PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="eb0b6-307">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="eb0b6-308">시뮬레이션 된 손으로의 조인트 구성에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-308">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="eb0b6-309">**PerceptionSimulation. SimulatedHandJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-309">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="eb0b6-310">조인트의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-310">The position of the joint.</span></span>

<span data-ttu-id="eb0b6-311">**PerceptionSimulation. SimulatedHandJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-311">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="eb0b6-312">조인트의 회전입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-312">The rotation of the joint.</span></span>

<span data-ttu-id="eb0b6-313">**PerceptionSimulation. SimulatedHandJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-313">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="eb0b6-314">조인트의 추적 정확도입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-314">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="eb0b6-315">PerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="eb0b6-315">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="eb0b6-316">카메라에서 일반적으로 사용 되는 것과 같은 뷰를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-316">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="eb0b6-317">**PerceptionSimulation. Near**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-317">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="eb0b6-318">가 수에 포함 된 최소 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-318">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="eb0b6-319">**PerceptionSimulation.**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-319">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="eb0b6-320">가 수에 포함 된 최대 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-320">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="eb0b6-321">**PerceptionSimulation. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-321">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="eb0b6-322">두 부분을 뺀 값의 가로 필드 (PI 보다 작음)입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-322">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="eb0b6-323">**PerceptionSimulation. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-323">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="eb0b6-324">뷰의 가로 필드와 세로 필드의 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-324">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="eb0b6-325">PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="eb0b6-325">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="eb0b6-326">시뮬레이션 된 헤드셋 디스플레이의 구성에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-326">Describes the configuration of the simulated headset's display.</span></span>

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

<span data-ttu-id="eb0b6-327">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-327">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="eb0b6-328">스테레오 렌더링의 용도에 대 한 헤드의 중심에서 왼쪽으로의 변환입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-328">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="eb0b6-329">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-329">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="eb0b6-330">스테레오 렌더링의 용도에 대 한 왼쪽 눈동자의 회전입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-330">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="eb0b6-331">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-331">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="eb0b6-332">스테레오 렌더링의 용도에 대 한 헤드의 중심에서 오른쪽으로의 변환입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-332">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="eb0b6-333">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-333">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="eb0b6-334">스테레오 렌더링의 용도에 대 한 올바른 눈동자의 회전입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-334">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="eb0b6-335">**PerceptionSimulation. SimulatedDisplayConfiguration. Ipd**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-335">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="eb0b6-336">스테레오 렌더링을 위해 시스템에서 보고 한 Ipd 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-336">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="eb0b6-337">**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-337">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="eb0b6-338">왼쪽 및 오른쪽에서 변형에 대해 제공 된 값을 유효한 것으로 간주 하 여 실행 중인 시스템에 적용할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-338">Whether the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="eb0b6-339">**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-339">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="eb0b6-340">Ipd에 제공 된 값을 유효한 것으로 간주 하 여 실행 중인 시스템에 적용할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-340">Whether the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="eb0b6-341">PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="eb0b6-341">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="eb0b6-342">장치를 제어 하는 데 사용 되는 패킷을 생성 하는 루트입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-342">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="eb0b6-343">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-343">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="eb0b6-344">시뮬레이션 된 사용자 및 시뮬레이션 된 전 세계를 해석 하는 시뮬레이션 된 장치 개체를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-344">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="eb0b6-345">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-345">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="eb0b6-346">시뮬레이션 된 사용자를 제어 하는 개체를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-346">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="eb0b6-347">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-347">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="eb0b6-348">시뮬레이션을 기본 상태로 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-348">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="eb0b6-349">PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="eb0b6-349">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="eb0b6-350">시뮬레이션 된 환경과 시뮬레이션 된 사용자를 해석 하는 장치를 설명 하는 인터페이스</span><span class="sxs-lookup"><span data-stu-id="eb0b6-350">Interface describing the device, which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="eb0b6-351">**PerceptionSimulation. ISimulatedDevice**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-351">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="eb0b6-352">시뮬레이션 된 장치에서 헤드 추적 장치를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-352">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="eb0b6-353">**PerceptionSimulation. ISimulatedDevice**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-353">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="eb0b6-354">시뮬레이션 된 장치에서 손 트래커를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-354">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="eb0b6-355">**PerceptionSimulation ISimulatedDevice. SetSimulatedDeviceType (PerceptionSimulation)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-355">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="eb0b6-356">제공 된 장치 유형과 일치 하도록 시뮬레이트된 장치의 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-356">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="eb0b6-357">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-357">Parameters</span></span>
* <span data-ttu-id="eb0b6-358">유형-시뮬레이션 된 장치의 새 유형</span><span class="sxs-lookup"><span data-stu-id="eb0b6-358">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="eb0b6-359">PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="eb0b6-359">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="eb0b6-360">ISimulatedDevice을 ISimulatedDevice2로 캐스팅 하 여 추가 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-360">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="eb0b6-361">**PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-361">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="eb0b6-362">시뮬레이션 된 사람이 헤드셋을 적극적으로 입고 있는지 여부를 검색 하거나 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-362">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="eb0b6-363">**PerceptionSimulation. ISimulatedDevice2 구성**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-363">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="eb0b6-364">시뮬레이션 된 디스플레이의 속성을 검색 하거나 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-364">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="eb0b6-365">PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="eb0b6-365">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="eb0b6-366">시뮬레이션 된 사람의 헤드를 추적 하는 시뮬레이션 된 장치의 부분을 설명 하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-366">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="eb0b6-367">**PerceptionSimulation. ISimulatedHeadTracker.**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-367">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="eb0b6-368">현재 헤드 추적 모드를 검색 하 고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-368">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="eb0b6-369">PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="eb0b6-369">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="eb0b6-370">시뮬레이션 된 사람의 손을 추적 하는 시뮬레이션 된 장치의 부분을 설명 하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-370">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

<span data-ttu-id="eb0b6-371">**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-371">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="eb0b6-372">전 세계와 관련 하 여 노드의 위치를 미터 단위로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-372">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="eb0b6-373">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-373">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="eb0b6-374">헤드의 중심을 기준으로 시뮬레이션 된 손 트래커의 위치를 검색 하 고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-374">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="eb0b6-375">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-375">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="eb0b6-376">시뮬레이션 된 손 추적기의 하향 피치를 검색 하 고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-376">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="eb0b6-377">**PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-377">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="eb0b6-378">시뮬레이션 된 손 추적기의 하 한을 무시 하는지 여부를 검색 하 고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-378">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="eb0b6-379">무시 하면 두 손을 항상 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-379">When ignored, both hands are always visible.</span></span> <span data-ttu-id="eb0b6-380">무시 되지 않는 경우 (기본값) 손을 트래커의 두 부분에 있는 경우에만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-380">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="eb0b6-381">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-381">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="eb0b6-382">손을 시뮬레이션 된 손 추적기에 표시할지 여부를 결정 하는 데 사용 되는 대/그와 같은 속성을 검색 하 고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-382">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="eb0b6-383">PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="eb0b6-383">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="eb0b6-384">시뮬레이션 된 사용자를 제어 하기 위한 최상위 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-384">Top-level interface for controlling the simulated human.</span></span>

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }s
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

<span data-ttu-id="eb0b6-385">**PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-385">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="eb0b6-386">전 세계와 관련 하 여 노드의 위치를 측정 하 고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-386">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="eb0b6-387">위치는 인간 피트의 중심에 있는 지점에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-387">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="eb0b6-388">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-388">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="eb0b6-389">시뮬레이션 된 사람이 직면 하는 방향을 검색 하 고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-389">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="eb0b6-390">0 라디안은 음의 Z 축을 아래로 내립니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-390">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="eb0b6-391">양의 라디안은 Y 축에 대해 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-391">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="eb0b6-392">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-392">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="eb0b6-393">시뮬레이션 된 인간의 높이를 미터 단위로 검색 하 고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-393">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="eb0b6-394">**PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-394">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="eb0b6-395">시뮬레이션 된 사람의 왼쪽을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-395">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="eb0b6-396">**PerceptionSimulation. ISimulatedHuman. RightHand**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-396">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="eb0b6-397">시뮬레이션 된 사람의 오른쪽을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-397">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="eb0b6-398">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-398">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="eb0b6-399">시뮬레이션 된 사람의 머리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-399">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="eb0b6-400">**PerceptionSimulation (ISimulatedHuman (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-400">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="eb0b6-401">현재 위치를 기준으로 시뮬레이션 된 사용자를 미터 단위로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-401">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="eb0b6-402">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-402">Parameters</span></span>
* <span data-ttu-id="eb0b6-403">translation-현재 위치를 기준으로 이동할 변환입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-403">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="eb0b6-404">**PerceptionSimulation. ISimulatedHuman (System.web)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-404">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="eb0b6-405">시뮬레이션 된 사용자를 현재 방향에 상대적으로 회전 하 여 Y 축에 대해 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-405">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="eb0b6-406">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-406">Parameters</span></span>
* <span data-ttu-id="eb0b6-407">radians-Y 축을 중심으로 회전할 양입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-407">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="eb0b6-408">PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="eb0b6-408">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="eb0b6-409">ISimulatedHuman을 ISimulatedHuman2로 캐스팅 하 여 추가 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-409">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="eb0b6-410">**PerceptionSimulation. ISimulatedHuman2**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-410">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="eb0b6-411">왼쪽 6-DOF 컨트롤러를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-411">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="eb0b6-412">**PerceptionSimulation. ISimulatedHuman2 컨트롤러**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-412">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="eb0b6-413">오른쪽 6-DOF controller를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-413">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="eb0b6-414">PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="eb0b6-414">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="eb0b6-415">시뮬레이션 된 사람의 손을 설명 하는 인터페이스</span><span class="sxs-lookup"><span data-stu-id="eb0b6-415">Interface describing a hand of the simulated human</span></span>

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

<span data-ttu-id="eb0b6-416">**PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-416">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="eb0b6-417">전 세계와 관련 하 여 노드의 위치를 미터 단위로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-417">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="eb0b6-418">**PerceptionSimulation. ISimulatedHand**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-418">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="eb0b6-419">미터 단위로 인간을 기준으로 시뮬레이션 된 손의 위치를 검색 하 고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-419">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="eb0b6-420">**PerceptionSimulation. ISimulatedHand**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-420">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="eb0b6-421">손이 현재 활성화 되어 있는지 여부를 검색 하 고 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-421">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="eb0b6-422">**PerceptionSimulation. ISimulatedHand**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-422">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="eb0b6-423">손이 현재 SimulatedDevice에 표시 되는지 (즉, 핸드 트래커에서 검색할 위치에 있는지)를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-423">Retrieve whether the hand is currently visible to the SimulatedDevice (that is, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="eb0b6-424">\**PerceptionSimulation. ISimulatedHand. Ensurevisible\**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-424">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="eb0b6-425">SimulatedDevice에 표시 되도록 손을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-425">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="eb0b6-426">**PerceptionSimulation (ISimulatedHand (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-426">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="eb0b6-427">현재 위치를 기준으로 시뮬레이션 된 손의 위치를 미터 단위로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-427">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="eb0b6-428">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-428">Parameters</span></span>
* <span data-ttu-id="eb0b6-429">번역-시뮬레이션 된 손을 변환할 양입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-429">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="eb0b6-430">**PerceptionSimulation ISimulatedHand. PerformGesture (PerceptionSimulation)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-430">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="eb0b6-431">시뮬레이션 된 손을 사용 하 여 제스처를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-431">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="eb0b6-432">손을 사용 하도록 설정 된 경우에만 시스템에서 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-432">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="eb0b6-433">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-433">Parameters</span></span>
* <span data-ttu-id="eb0b6-434">제스처-수행할 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-434">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="eb0b6-435">PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="eb0b6-435">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="eb0b6-436">ISimulatedHand을 ISimulatedHand2로 캐스팅 하 여 추가 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-436">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="eb0b6-437">**PerceptionSimulation. ISimulatedHand2**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-437">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="eb0b6-438">시뮬레이션 된 손 각도를 검색 하거나 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-438">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="eb0b6-439">양수 라디안은 축을 따라 볼 때 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-439">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="eb0b6-440">PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="eb0b6-440">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="eb0b6-441">ISimulatedHand을 ISimulatedHand3로 캐스팅 하 여 추가 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-441">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="eb0b6-442">**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-442">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="eb0b6-443">지정 된 조인트의 조인트 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-443">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="eb0b6-444">**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-444">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="eb0b6-445">지정 된 조인트의 조인트 구성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-445">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="eb0b6-446">**PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-446">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="eb0b6-447">애니메이션 효과를 주는 선택적 플래그를 사용 하 여 손 모양을 알려진 포즈로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-447">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="eb0b6-448">참고: 애니메이션 효과는 최종 조인트 구성을 즉시 반영 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-448">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="eb0b6-449">PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="eb0b6-449">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="eb0b6-450">시뮬레이션 된 사람의 머리를 설명 하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-450">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="eb0b6-451">**PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-451">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="eb0b6-452">전 세계와 관련 하 여 노드의 위치를 미터 단위로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-452">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="eb0b6-453">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-453">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="eb0b6-454">시뮬레이션 된 헤드의 회전을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-454">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="eb0b6-455">양수 라디안은 축을 따라 볼 때 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-455">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="eb0b6-456">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-456">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="eb0b6-457">시뮬레이션 된 헤드의 지름을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-457">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="eb0b6-458">이 값은 헤드의 중심 (회전 지점)을 결정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-458">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="eb0b6-459">**PerceptionSimulation. ISimulatedHead (PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-459">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="eb0b6-460">현재 회전을 기준으로 시뮬레이션 된 헤드를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-460">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="eb0b6-461">양수 라디안은 축을 따라 볼 때 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-461">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="eb0b6-462">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-462">Parameters</span></span>
* <span data-ttu-id="eb0b6-463">회전-회전할 양입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-463">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="eb0b6-464">PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="eb0b6-464">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="eb0b6-465">ISimulatedHead을 ISimulatedHead2로 캐스팅 하 여 추가 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-465">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="eb0b6-466">**PerceptionSimulation. ISimulatedHead2**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-466">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="eb0b6-467">시뮬레이션 된 사람의 눈동자를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-467">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="eb0b6-468">PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="eb0b6-468">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="eb0b6-469">시뮬레이션 된 사용자와 연결 된 6 DOF 컨트롤러를 설명 하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-469">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

<span data-ttu-id="eb0b6-470">**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="eb0b6-471">전 세계와 관련 하 여 노드의 위치를 미터 단위로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-471">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="eb0b6-472">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-472">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="eb0b6-473">컨트롤러의 현재 상태를 검색 하거나 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-473">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="eb0b6-474">이동, 회전 또는 누르기 단추에 대 한 호출이 성공 하기 전에 컨트롤러 상태를 Off 이외의 값으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-474">The controller status must be set to a value other than Off before any calls to move, rotate, or press buttons will succeed.</span></span>

<span data-ttu-id="eb0b6-475">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="eb0b6-476">사용자를 기준으로 시뮬레이션 된 컨트롤러의 위치를 미터 단위로 검색 하거나 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-476">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="eb0b6-477">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-477">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="eb0b6-478">시뮬레이션 된 컨트롤러의 방향을 검색 하거나 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-478">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="eb0b6-479">**PerceptionSimulation (ISimulatedSixDofController (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-479">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="eb0b6-480">현재 위치를 기준으로 시뮬레이트된 컨트롤러의 위치를 미터 단위로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-480">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="eb0b6-481">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-481">Parameters</span></span>
* <span data-ttu-id="eb0b6-482">번역-시뮬레이트된 컨트롤러를 변환할 양입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-482">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="eb0b6-483">**PerceptionSimulation. ISimulatedSixDofController (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-483">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="eb0b6-484">시뮬레이션 된 컨트롤러의 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-484">Press a button on the simulated controller.</span></span>  <span data-ttu-id="eb0b6-485">컨트롤러가 사용 하도록 설정 된 경우에만 시스템에서 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-485">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="eb0b6-486">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-486">Parameters</span></span>
* <span data-ttu-id="eb0b6-487">button-단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-487">button - The button to press.</span></span>

<span data-ttu-id="eb0b6-488">**PerceptionSimulation. ISimulatedSixDofController (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-488">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="eb0b6-489">시뮬레이션 된 컨트롤러에서 단추를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-489">Release a button on the simulated controller.</span></span>  <span data-ttu-id="eb0b6-490">컨트롤러가 사용 하도록 설정 된 경우에만 시스템에서 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-490">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="eb0b6-491">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-491">Parameters</span></span>
* <span data-ttu-id="eb0b6-492">button-해제할 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-492">button - The button to release.</span></span>

<span data-ttu-id="eb0b6-493">**PerceptionSimulation ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-493">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="eb0b6-494">시뮬레이션 된 컨트롤러의 터치 패드에서 시뮬레이션 된 손가락의 위치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-494">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="eb0b6-495">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-495">Parameters</span></span>
* <span data-ttu-id="eb0b6-496">x-손가락의 가로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-496">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="eb0b6-497">y-손가락의 세로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-497">y - The vertical position of the finger.</span></span>

<span data-ttu-id="eb0b6-498">**PerceptionSimulation ISimulatedSixDofController. SetTouchpadPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-498">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="eb0b6-499">시뮬레이션 된 컨트롤러의 터치 패드에서 시뮬레이션 된 손가락의 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-499">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="eb0b6-500">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-500">Parameters</span></span>
* <span data-ttu-id="eb0b6-501">x-손가락의 가로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-501">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="eb0b6-502">y-손가락의 세로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-502">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="eb0b6-503">PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="eb0b6-503">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="eb0b6-504">ISimulatedSixDofController를 ISimulatedSixDofController2로 캐스팅 하 여 추가 속성 및 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-504">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="eb0b6-505">**PerceptionSimulation ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-505">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="eb0b6-506">시뮬레이트된 컨트롤러에서 시뮬레이션 된 엄지 스틱의 위치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-506">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="eb0b6-507">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-507">Parameters</span></span>
* <span data-ttu-id="eb0b6-508">x-엄지 스틱의 가로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-508">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="eb0b6-509">y-엄지 스틱의 세로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-509">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="eb0b6-510">**PerceptionSimulation ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-510">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="eb0b6-511">시뮬레이트된 컨트롤러에서 시뮬레이션 된 엄지 스틱의 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-511">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="eb0b6-512">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-512">Parameters</span></span>
* <span data-ttu-id="eb0b6-513">x-엄지 스틱의 가로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-513">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="eb0b6-514">y-엄지 스틱의 세로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-514">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="eb0b6-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="eb0b6-516">시뮬레이트된 컨트롤러의 배터리 수준을 검색 하거나 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-516">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="eb0b6-517">값은 0.0 보다 크고 100.0 보다 작거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-517">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="eb0b6-518">PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="eb0b6-518">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="eb0b6-519">시뮬레이션 된 사람의 눈을 설명 하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-519">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="eb0b6-520">**PerceptionSimulation. ISimulatedEyes**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-520">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="eb0b6-521">시뮬레이션 된 눈동자의 회전을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-521">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="eb0b6-522">양수 라디안은 축을 따라 볼 때 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-522">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="eb0b6-523">**PerceptionSimulation. ISimulatedEyes (PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-523">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="eb0b6-524">현재 회전을 기준으로 시뮬레이션 된 눈동자를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-524">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="eb0b6-525">양수 라디안은 축을 따라 볼 때 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-525">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="eb0b6-526">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-526">Parameters</span></span>
* <span data-ttu-id="eb0b6-527">회전-회전할 양입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-527">rotation - The amount to rotate.</span></span>

<span data-ttu-id="eb0b6-528">**PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-528">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="eb0b6-529">시뮬레이션 된 눈동자의 보정 상태를 검색 하거나 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-529">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="eb0b6-530">**PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-530">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="eb0b6-531">전 세계와 관련 하 여 노드의 위치를 미터 단위로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-531">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="eb0b6-532">PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="eb0b6-532">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="eb0b6-533">재생을 위해 로드 된 단일 기록과 상호 작용 하기 위한 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-533">Interface for interacting with a single recording loaded for playback.</span></span>

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

<span data-ttu-id="eb0b6-534">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-534">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="eb0b6-535">기록의 데이터 형식 목록을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-535">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="eb0b6-536">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-536">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="eb0b6-537">기록의 현재 상태를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-537">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="eb0b6-538">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-538">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="eb0b6-539">재생을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-539">Start the playback.</span></span> <span data-ttu-id="eb0b6-540">기록이 일시 중지 된 경우 일시 중지 된 위치에서 재생이 다시 시작 됩니다. 중지 된 경우 재생이 시작 부분에서 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-540">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="eb0b6-541">이미를 재생 하는 경우이 호출은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-541">If already playing, this call is ignored.</span></span>

<span data-ttu-id="eb0b6-542">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-542">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="eb0b6-543">현재 위치에서 재생을 일시 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-543">Pauses the playback at its current location.</span></span> <span data-ttu-id="eb0b6-544">기록이 중지 되 면 호출은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-544">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="eb0b6-545">**PerceptionSimulation (ISimulationRecording).**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-545">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="eb0b6-546">지정 된 시간 (처음부터 100 나노초 간격으로)에 대 한 기록을 검색 하 고 해당 위치에서 일시 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-546">Seeks the recording to the specified time (in 100-nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="eb0b6-547">시간이 기록의 끝을 초과 하면 마지막 프레임에서 일시 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-547">If the time is beyond the end of the recording, it's paused at the last frame.</span></span>

<span data-ttu-id="eb0b6-548">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-548">Parameters</span></span>
* <span data-ttu-id="eb0b6-549">틱-검색 하는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-549">ticks - The time to which to seek.</span></span>

<span data-ttu-id="eb0b6-550">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-550">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="eb0b6-551">재생을 중지 하 고 위치를 시작 부분으로 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-551">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="eb0b6-552">PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="eb0b6-552">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="eb0b6-553">재생 하는 동안 상태 변경을 수신 하기 위한 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-553">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="eb0b6-554">**PerceptionSimulation. ISimulationRecordingCallback PlaybackStateChanged (PerceptionSimulation Backstate)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-554">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="eb0b6-555">ISimulationRecording의 재생 상태가 변경 될 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-555">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="eb0b6-556">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-556">Parameters</span></span>
* <span data-ttu-id="eb0b6-557">newState-기록의 새 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-557">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="eb0b6-558">PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="eb0b6-558">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="eb0b6-559">인식 시뮬레이션 개체를 만들기 위한 루트 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-559">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="eb0b6-560">**PerceptionSimulation PerceptionSimulationManager. CreatePerceptionSimulationManager (PerceptionSimulation)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-560">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="eb0b6-561">시뮬레이션 된 패킷을 생성 하 여 제공 된 싱크에 전달 하기 위해 개체에를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-561">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="eb0b6-562">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-562">Parameters</span></span>
* <span data-ttu-id="eb0b6-563">sink-생성 된 모든 패킷을 수신 하는 싱크입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-563">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="eb0b6-564">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb0b6-564">Return value</span></span>

<span data-ttu-id="eb0b6-565">만든 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-565">The created Manager.</span></span>

<span data-ttu-id="eb0b6-566">**PerceptionSimulation PerceptionSimulationManager. CreatePerceptionSimulationRecording (System.string)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-566">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="eb0b6-567">지정 된 경로에 있는 파일에 수신 된 모든 패킷을 저장 하는 싱크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-567">Create a sink, which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="eb0b6-568">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-568">Parameters</span></span>
* <span data-ttu-id="eb0b6-569">path-만들 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-569">path - The path of the file to create.</span></span>

<span data-ttu-id="eb0b6-570">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb0b6-570">Return value</span></span>

<span data-ttu-id="eb0b6-571">만든 싱크입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-571">The created sink.</span></span>

<span data-ttu-id="eb0b6-572">**PerceptionSimulation. PerceptionSimulationManager, LoadPerceptionSimulationRecording (System.string, PerceptionSimulation)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-572">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="eb0b6-573">지정 된 파일에서 기록을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-573">Load a recording from the specified file.</span></span>

<span data-ttu-id="eb0b6-574">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-574">Parameters</span></span>
* <span data-ttu-id="eb0b6-575">path-로드할 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-575">path - The path of the file to load.</span></span>
* <span data-ttu-id="eb0b6-576">팩터리-필요할 때 ISimulationStreamSink를 만들기 위해 기록에서 사용 하는 팩터리입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-576">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="eb0b6-577">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb0b6-577">Return value</span></span>

<span data-ttu-id="eb0b6-578">로드 된 기록입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-578">The loaded recording.</span></span>

<span data-ttu-id="eb0b6-579">**PerceptionSimulation, PerceptionSimulationManager, LoadPerceptionSimulationRecording (System.string, PerceptionSimulation, ISimulationStreamSinkFactory, PerceptionSimulation)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-579">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="eb0b6-580">지정 된 파일에서 기록을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-580">Load a recording from the specified file.</span></span>

<span data-ttu-id="eb0b6-581">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-581">Parameters</span></span>
* <span data-ttu-id="eb0b6-582">path-로드할 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-582">path - The path of the file to load.</span></span>
* <span data-ttu-id="eb0b6-583">팩터리-필요할 때 ISimulationStreamSink를 만들기 위해 기록에서 사용 하는 팩터리입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-583">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="eb0b6-584">콜백-녹음 상태를 다시 보고 하는 업데이트를 수신 하는 콜백입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-584">callback - A callback, which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="eb0b6-585">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb0b6-585">Return value</span></span>

<span data-ttu-id="eb0b6-586">로드 된 기록입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-586">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="eb0b6-587">PerceptionSimulation 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="eb0b6-587">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="eb0b6-588">다양 한 유형의 스트림 데이터를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-588">Describes the different types of stream data.</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

<span data-ttu-id="eb0b6-589">**PerceptionSimulation 데이터 형식입니다.**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-589">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="eb0b6-590">스트림 데이터 형식이 없음을 나타내는 데 사용 되는 센티널 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-590">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="eb0b6-591">**PerceptionSimulation. Head**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-591">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="eb0b6-592">헤드의 위치 및 방향에 대 한 데이터 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-592">Stream of data for the position and orientation of the head.</span></span>

<span data-ttu-id="eb0b6-593">**PerceptionSimulation. 직접**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-593">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="eb0b6-594">바늘의 위치 및 제스처에 대 한 데이터 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-594">Stream of data for the position and gestures of hands.</span></span>

<span data-ttu-id="eb0b6-595">**PerceptionSimulation. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-595">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="eb0b6-596">환경의 공간 매핑에 대 한 데이터 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-596">Stream of data for spatial mapping of the environment.</span></span>

<span data-ttu-id="eb0b6-597">**PerceptionSimulation. 보정**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-597">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="eb0b6-598">장치의 보정에 대 한 데이터 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-598">Stream of data for calibration of the device.</span></span> <span data-ttu-id="eb0b6-599">원격 모드의 시스템 에서만 보정 패킷을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-599">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="eb0b6-600">**PerceptionSimulation. 환경**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-600">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="eb0b6-601">장치 환경에 대 한 데이터 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-601">Stream of data for the environment of the device.</span></span>

<span data-ttu-id="eb0b6-602">**PerceptionSimulation. SixDofControllers**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-602">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="eb0b6-603">동작 컨트롤러에 대 한 데이터 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-603">Stream of data for motion controllers.</span></span>

<span data-ttu-id="eb0b6-604">**PerceptionSimulation입니다.**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-604">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="eb0b6-605">시뮬레이션 된 사람의 눈에 해당 하는 데이터 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-605">Stream of data with the eyes of the simulated human.</span></span>

<span data-ttu-id="eb0b6-606">**PerceptionSimulation를 구성 합니다.**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-606">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="eb0b6-607">장치의 디스플레이 구성을 사용 하 여 데이터 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-607">Stream of data with the display configuration of the device.</span></span>

<span data-ttu-id="eb0b6-608">**PerceptionSimulation 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-608">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="eb0b6-609">기록 된 모든 데이터 형식을 나타내는 데 사용 되는 센티널 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-609">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="eb0b6-610">PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="eb0b6-610">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="eb0b6-611">시뮬레이션 스트림에서 데이터 패킷을 수신 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-611">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="eb0b6-612">**PerceptionSimulation ISimulationStreamSink. OnPacketReceived (uint length, byte [] packet)**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-612">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="eb0b6-613">는 내부적으로 형식화 되 고 버전이 지정 되는 단일 패킷을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-613">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="eb0b6-614">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb0b6-614">Parameters</span></span>
* <span data-ttu-id="eb0b6-615">length-패킷의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-615">length - The length of the packet.</span></span>
* <span data-ttu-id="eb0b6-616">packet-패킷의 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-616">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="eb0b6-617">PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="eb0b6-617">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="eb0b6-618">ISimulationStreamSink을 만드는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-618">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="eb0b6-619">**PerceptionSimulation ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**</span><span class="sxs-lookup"><span data-stu-id="eb0b6-619">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="eb0b6-620">ISimulationStreamSink의 단일 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-620">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="eb0b6-621">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb0b6-621">Return value</span></span>

<span data-ttu-id="eb0b6-622">만든 싱크입니다.</span><span class="sxs-lookup"><span data-stu-id="eb0b6-622">The created sink.</span></span>
