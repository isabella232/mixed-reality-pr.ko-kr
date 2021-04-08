---
ms.openlocfilehash: 78605b17e93429ad974e1ca21e7859035f38d615
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088719"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="d3c83-101">Unity 2019/2020 + Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="d3c83-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="d3c83-102">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-102">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity Build Settings... 메뉴 경로](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="d3c83-104">Build Settings 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택하고, **Switch Platform(플랫폼 전환)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-104">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![플랫폼을 독립 실행형에서 전환하기 위해 UWP가 선택된 Unity Build Settings 창](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="d3c83-106">Unity에서 플랫폼 전환이 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-106">Wait for Unity to finish switching the platform:</span></span>

![진행 중인 Unity 플랫폼 전환](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="d3c83-108">Unity에서 플랫폼 전환이 완료되면 빨간색 **x** 아이콘을 클릭하여 Build Settings 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-108">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![닫기 아이콘이 강조 표시된 Unity 빌드 창](../images/mr-learning-base/base-02-section2-step1-4.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="d3c83-110">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="d3c83-110">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="d3c83-111">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-111">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity Build Settings... 메뉴 경로](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="d3c83-113">Build Settings(빌드 설정) 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택하고</span><span class="sxs-lookup"><span data-stu-id="d3c83-113">In the Build Settings window, select **Universal Windows Platform** and:</span></span>
1.  <span data-ttu-id="d3c83-114">**Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-114">Set **Target device** to **HoloLens**</span></span>
2.  <span data-ttu-id="d3c83-115">**Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-115">Set **Architecture** to **ARM 64**</span></span>
3.  <span data-ttu-id="d3c83-116">**Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-116">Set **Build Type** to **D3D**</span></span>
4.  <span data-ttu-id="d3c83-117">**Minimum Platform Version(최소 플랫폼 버전)** 을 **10.2.18362** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-117">Set **Minimum Platform Version** to **10.2.18362**</span></span>
5.  <span data-ttu-id="d3c83-118">**UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-118">Set **UWP SDK** to **Latest installed**</span></span>
6.  <span data-ttu-id="d3c83-119">디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-119">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
7.  <span data-ttu-id="d3c83-120">Switch Platform(플랫폼 전환) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-120">Click the Switch Platform button</span></span>


![유니버설 Windows 플랫폼 설정이 지정된 Unity 빌드 설정](../images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="d3c83-122">Unity에서 플랫폼 전환을 완료하면 빨간색 **x** 아이콘을 클릭하여 Build Settings(빌드 설정) 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-122">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="d3c83-123">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="d3c83-123">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="d3c83-124">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-124">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity Build Settings... 메뉴 경로](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="d3c83-126">Build Settings 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택하고, **Switch Platform(플랫폼 전환)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-126">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![플랫폼을 독립 실행형에서 전환하기 위해 UWP가 선택된 Unity Build Settings 창](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="d3c83-128">Unity에서 플랫폼 전환이 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-128">Wait for Unity to finish switching the platform:</span></span>

![진행 중인 Unity 플랫폼 전환](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="d3c83-130">Unity에서 플랫폼 전환이 완료되면 빨간색 **x** 아이콘을 클릭하여 Build Settings 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d3c83-130">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![닫기 아이콘이 강조 표시된 Unity 빌드 창](../images/mr-learning-base/base-02-section2-step1-4.png)