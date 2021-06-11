---
title: 예제 장면 실행
description: MRTK의 예제 장면을 획득하고 사용하는 방법을 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/07/2021
ms.topic: article
keywords: 혼합 현실 도구 키트, MRTK, 예제, HoloLens, HoloLens 2, 셰이더, 도구 설명, 손 상호 작용, 클리핑, 경계 상자, 단추, 손 메뉴, 슬레이트, 슬라이더
ms.openlocfilehash: 8ba4df237189f0de3bd869bc05bdf7e3c5451490
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111911871"
---
# <a name="example-scenes"></a><span data-ttu-id="f1d3d-104">예제 장면</span><span class="sxs-lookup"><span data-stu-id="f1d3d-104">Example scenes</span></span>

<span data-ttu-id="f1d3d-105">MRTK는 공간 사용자 환경을 위한 MRTK의 기능 및 구성 요소에 대해 설명하는 다양한 유형의 예제 장면을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3d-105">MRTK provides various types of example scenes that demonstrate MRTK's features and building blocks for spatial user experience.</span></span> <span data-ttu-id="f1d3d-106">예제 장면을 경험하고 분석하면 기능을 이해하고 프로젝트에 적용하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3d-106">Experiencing and dissecting example scenes could be helpful to understand the features and apply them to your projects.</span></span> 

## <a name="how-to-acquire-example-scenes"></a><span data-ttu-id="f1d3d-107">예제 장면을 얻는 방법</span><span class="sxs-lookup"><span data-stu-id="f1d3d-107">How to acquire example scenes</span></span>

### <a name="using-mixed-reality-feature-tool-and-unity-package-manager"></a><span data-ttu-id="f1d3d-108">Mixed Reality 기능 도구 및 Unity 패키지 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="f1d3d-108">Using Mixed Reality Feature Tool and Unity package manager</span></span>

<span data-ttu-id="f1d3d-109">Mixed Reality [기능](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 도구를 통해 **Mixed Reality Toolkit Examples** 패키지를 다운로드하고 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3d-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="f1d3d-110">Unity에서 **창 > 패키지 관리자 > 프로젝트 > 사용자 지정** 메뉴를 사용하고 도구 키트 예제 **Mixed Reality** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3d-110">In Unity, use the menu **Window > Package Manager > In Project > Custom** and select **Mixed Reality Toolkit Examples**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<span data-ttu-id="f1d3d-111">패널 오른쪽의 목록에서 예제 장면 이름 옆에 **있는 프로젝트로 가져오기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3d-111">From the list on the right side of the panel, click **Import into Project** button next to the example scene names.</span></span>  <span data-ttu-id="f1d3d-112">예를 들어 **데모 - HandTracking** 옆에 **있는 프로젝트로 가져오기** 단추를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3d-112">For example, you can click **Import into Project** button next to **Demos - HandTracking**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<span data-ttu-id="f1d3d-113">가져온 후에는 **자산 > 샘플** 폴더에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3d-113">Once imported, you will be able to find them under **Assets > Samples** folder.</span></span>
<span data-ttu-id="f1d3d-114">**HandInteractionExamples** 장면은 MRTK의 공간 상호 작용 및 UI 구성 요소의 경험을 시작하기에 좋은 장소입니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3d-114">**HandInteractionExamples** scene is a great place to start experiencing MRTK's spatial interactions and UI building blocks.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

### <a name="directly-downloading-and-importing-packages-from-github"></a><span data-ttu-id="f1d3d-115">GitHub에서 패키지 직접 다운로드 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="f1d3d-115">Directly downloading and importing packages from GitHub</span></span>

<span data-ttu-id="f1d3d-116">Mixed Reality 기능 도구를 사용하지 않는 경우 [MRTK GitHub의 릴리스 페이지에서](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage를** 직접 다운로드하여 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3d-116">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

<span data-ttu-id="f1d3d-117">**자산 > 패키지 가져오기 > 사용자 지정 패키지** 메뉴를 사용하여 다운로드한 .unitypackage를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3d-117">Use **Assets > Import Package > Custom Package** menu to import downloaded .unitypackage.</span></span> <span data-ttu-id="f1d3d-118">가져온 후 자산 > **MRTK > 예제 > 데모에서 예제** 장면을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3d-118">Once it is imported, you will be able to find example scenes under **Assets > MRTK > Examples > Demos**.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual1.png" width="650" alt="Example Manual 1"><br/>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual2.png" width="650" alt="Example Manual 2"><br/>