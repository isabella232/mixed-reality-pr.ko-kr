---
title: Unity를 통해 관리되는 디버깅
description: 이 문서에서는 Unity IL2CPP UWP 프로젝트에서 관리되는 디버거를 실행하는 방법을 설명합니다.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, Visual Studio, 디버깅, il2cpp, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, UWP
ms.openlocfilehash: 8e3967971220fa453f4e60639bd08f2554a8dd7e
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547077"
---
# <a name="managed-debugging-with-unity"></a><span data-ttu-id="37128-104">Unity를 통해 관리되는 디버깅</span><span class="sxs-lookup"><span data-stu-id="37128-104">Managed debugging with Unity</span></span>

<span data-ttu-id="37128-105">다음 단계에 따라 HoloLens 및 HoloLens 2 대한 Unity IL2CPP UWP 빌드에 관리되는 디버거를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="37128-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="37128-106">[멀티캐스트](https://en.wikipedia.org/wiki/Multicast)를 지원하는 네트워크에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37128-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="37128-107">**UWP 게시 설정 기능으로** 이동하여 **InternetClientServer** 및 **PrivateNetworkClientServer를** 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="37128-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![UWP 게시 설정 기능](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="37128-109">Unity UWP 빌드 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="37128-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="37128-110">개발 빌드</span><span class="sxs-lookup"><span data-stu-id="37128-110">Development Build</span></span>
    - <span data-ttu-id="37128-111">스크립트 디버깅</span><span class="sxs-lookup"><span data-stu-id="37128-111">Script Debugging</span></span>
    - <span data-ttu-id="37128-112">관리 디버거 대기(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="37128-112">Wait for Managed Debugger (optional)</span></span>

    ![UWP 빌드 설정](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="37128-114">Unity에서 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="37128-114">Build in Unity.</span></span>
5. <span data-ttu-id="37128-115">Visual Studio 솔루션에서 디바이스로 빌드하고 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="37128-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="37128-116">**디버그** 또는 **릴리스** 구성으로 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37128-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="37128-117">**마스터** 구성은 Unity 프로파일러를 사용하지 않도록 설정하고 최적의 디버깅을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37128-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="37128-118">필요에 따라 솔루션의 Package.appxmanifest에 있는 기능 목록에서 **인터넷(클라이언트 & Server)** 및 **프라이빗 네트워크(클라이언트 & Server)를** 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="37128-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="37128-119">디바이스가 PC와 동일한 네트워크에 연결되어 있는지 확인하고 디바이스에서 앱을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="37128-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="37128-120">디바이스가 USB를 통해 PC에 연결되어 **있지 않은지** 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="37128-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="37128-121">Unity에서 스크립트 중 하나를 두 번 클릭하고 Visual Studio 솔루션으로 이동하여 보고 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="37128-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="37128-122">디버그 -> Unity 디버거를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="37128-122">Debug -> Attach Unity Debugger.</span></span>

    ![Unity 디버거 연결](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="37128-124">목록에서 디바이스를 선택하고 "확인"을 클릭하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="37128-124">Select your device in the list and click "OK" to attach.</span></span>

    ![디바이스 목록](images/il2cpp-debugging-machines.png)
