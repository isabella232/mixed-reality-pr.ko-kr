---
ms.openlocfilehash: d7232ca645c2a8cfb2508b090fdb7ae02c2ab010
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984300"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="dccbe-101">Unity 2019/2020 + Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="dccbe-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="dccbe-102">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-102">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity Build Settings... 메뉴 경로](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="dccbe-104">Build Settings 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택하고, **Switch Platform(플랫폼 전환)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-104">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![플랫폼을 독립 실행형에서 전환하기 위해 UWP가 선택된 Unity Build Settings 창](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="dccbe-106">Unity에서 플랫폼 전환이 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-106">Wait for Unity to finish switching the platform:</span></span>

![진행 중인 Unity 플랫폼 전환](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="dccbe-108">Unity에서 플랫폼 전환이 완료되면 빨간색 **x** 아이콘을 클릭하여 Build Settings 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-108">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![닫기 아이콘이 강조 표시된 Unity 빌드 창](../images/mr-learning-base/base-02-section2-step1-4.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="dccbe-110">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="dccbe-110">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="dccbe-111">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-111">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity Build Settings... 메뉴 경로](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="dccbe-113">Build Settings(빌드 설정) 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택하고</span><span class="sxs-lookup"><span data-stu-id="dccbe-113">In the Build Settings window, select **Universal Windows Platform** and:</span></span>
1.  <span data-ttu-id="dccbe-114">**Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-114">Set **Target device** to **HoloLens**</span></span>
2.  <span data-ttu-id="dccbe-115">**Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-115">Set **Architecture** to **ARM 64**</span></span>
3.  <span data-ttu-id="dccbe-116">**Build Type(빌드 형식)** 을 **D3D Project(D3D 프로젝트)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-116">Set **Build Type** to **D3D Project**</span></span>
4.  <span data-ttu-id="dccbe-117">**Target SDK Version(대상 SDK 버전)** 을 **Latest Installed(최신 설치)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-117">Set **Target SDK Version** to **Latest Installed**</span></span>
5.  <span data-ttu-id="dccbe-118">**Minimum Platform Version(최소 플랫폼 버전)** 을 **10.0.18362** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-118">Set **Minimum Platform Version** to **10.0.18362**</span></span>
6.  <span data-ttu-id="dccbe-119">**Target Studio Version(대상 Studio 버전)** 을 **Latest Installed(최신 설치)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-119">Set **Visual Studio Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="dccbe-120">**Build and Run on(빌드 및 실행)** 을 **USB Device(USB 디바이스)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-120">Set **Build and Run on** to **USB Device**</span></span>
8.  <span data-ttu-id="dccbe-121">디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9.  <span data-ttu-id="dccbe-122">Switch Platform(플랫폼 전환) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-122">Click the Switch Platform button</span></span>


![유니버설 Windows 플랫폼 설정이 지정된 Unity 빌드 설정](../images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="dccbe-124">Unity에서 플랫폼 전환을 완료하면 빨간색 **x** 아이콘을 클릭하여 Build Settings(빌드 설정) 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-124">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="dccbe-125">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="dccbe-125">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="dccbe-126">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-126">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity Build Settings... 메뉴 경로](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="dccbe-128">Build Settings 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택하고, **Switch Platform(플랫폼 전환)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-128">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![플랫폼을 독립 실행형에서 전환하기 위해 UWP가 선택된 Unity Build Settings 창](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="dccbe-130">Unity에서 플랫폼 전환이 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-130">Wait for Unity to finish switching the platform:</span></span>

![진행 중인 Unity 플랫폼 전환](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="dccbe-132">Unity에서 플랫폼 전환이 완료되면 빨간색 **x** 아이콘을 클릭하여 Build Settings 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dccbe-132">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![닫기 아이콘이 강조 표시된 Unity 빌드 창](../images/mr-learning-base/base-02-section2-step1-4.png)
