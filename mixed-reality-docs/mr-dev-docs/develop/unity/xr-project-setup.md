---
title: XR 구성 설정
description: HoloLens 응용 프로그램 개발에 대 한 최신 Unity XR 구성 권장 사항을 최신으로 유지 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: df7c5039c6cdcfa1e39dc96f0829611dd5209772
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394567"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="f2ba6-104">XR 구성 설정</span><span class="sxs-lookup"><span data-stu-id="f2ba6-104">Setting up your XR configuration</span></span>

<span data-ttu-id="f2ba6-105">새 Unity 프로젝트를 시작할 때 XR 요구 사항을 처리 하기 위한 세 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2ba6-105">When you start a new Unity project, you have three different options for handling your XR needs:</span></span> 
* <span data-ttu-id="f2ba6-106">OpenXR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="f2ba6-106">OpenXR plugin</span></span>
* <span data-ttu-id="f2ba6-107">Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="f2ba6-107">Windows XR plugin</span></span>
* <span data-ttu-id="f2ba6-108">레거시 XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="f2ba6-108">Legacy XR plugin</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="f2ba6-109">MRTK를 사용 하 여 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="f2ba6-109">Setting up your project with MRTK</span></span>

<span data-ttu-id="f2ba6-110">Unity용 MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ba6-110">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="f2ba6-111">MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼용 애플리케이션 개발을 가속화하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f2ba6-111">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="f2ba6-112">이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ba6-112">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f2ba6-113">MRTK 자습서 사용해보기</span><span class="sxs-lookup"><span data-stu-id="f2ba6-113">Try out our MRTK tutorials</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=winxr)

<span data-ttu-id="f2ba6-114">기능에 대한 자세한 내용은 [MRTK 설명서](/windows/mixed-reality/mrtk-unity)를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="f2ba6-114">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

### <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="f2ba6-115">OpenXR 지원과 함께 MRTK 사용</span><span class="sxs-lookup"><span data-stu-id="f2ba6-115">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="f2ba6-116">MRTK-Unity 2.7 릴리스는 혼합 현실 OpenXR 플러그 인에 대 한 향상 된 지원 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ba6-116">MRTK-Unity 2.7 release provides better supports for the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="f2ba6-117">혼합 현실 [기능 도구](welcome-to-mr-feature-tool.md) 를 다시 열어 혼합 현실 도구 키트 (아직 없는 경우)를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ba6-117">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="f2ba6-118">OpenXR 지원은 **Foundation** 패키지에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2ba6-118">OpenXR support is in the **Foundation** package.</span></span>

<span data-ttu-id="f2ba6-119">[OpenXR로 마이그레이션하](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)는 방법에 대 한 자세한 내용은 MRTK 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2ba6-119">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="f2ba6-120">**2.5.3** 보다 이전 버전의 MRTK 이전 버전에서 업그레이드 하는 경우 Asset **/MixedRealityToolkit/link.xml** 파일에 다음 줄이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ba6-120">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="f2ba6-121">이 줄은 MRTK 2.5.4 이상으로 시작한 경우 기본적으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2ba6-121">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="f2ba6-122">MRTK 없이 수동 설치</span><span class="sxs-lookup"><span data-stu-id="f2ba6-122">Manual setup without MRTK</span></span>

<span data-ttu-id="f2ba6-123">Microsoft 및 커뮤니티에서는 WMR 환경을 자동으로 설정 하는 [mrtk (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 와 같은 활용 도구를 만들었으므로 많은 개발자 들이 처음부터 환경을 구축 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2ba6-123">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]
