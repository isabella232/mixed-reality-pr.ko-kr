---
title: 레거시 기본 제공 XR 지원 사용
description: 레거시 기본 제공 XR 지원을 사용 하 여 MRTK를 사용 하거나 사용 하지 않고 Unity 프로젝트를 설정 하는 방법을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, mixed reality, 개발, 시작, 새 프로젝트, Windows Mixed Reality, UWP, XR, 성능, 레거시, mrtk
ms.openlocfilehash: 09989b3b2b7fa1d351235a2cc9b885d4795dc2b6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088532"
---
# <a name="using-legacy-built-in-xr-support"></a><span data-ttu-id="5a5c1-104">레거시 기본 제공 XR 지원 사용</span><span class="sxs-lookup"><span data-stu-id="5a5c1-104">Using Legacy built-in XR support</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="5a5c1-105">MRTK를 사용 하 여 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="5a5c1-105">Setting up your project with MRTK</span></span>

<span data-ttu-id="5a5c1-106">Unity용 MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-106">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="5a5c1-107">MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼용 애플리케이션 개발을 가속화하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-107">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="5a5c1-108">이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-108">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5a5c1-109">MRTK 자습서를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-109">Try out our MRTK tutorials</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=wsa)

<span data-ttu-id="5a5c1-110">추가 기능에 대 한 자세한 내용은 [Mrtk의 설명서](/windows/mixed-reality/mrtk-unity) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-110">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="5a5c1-111">MRTK 없이 수동 설치</span><span class="sxs-lookup"><span data-stu-id="5a5c1-111">Manual setup without MRTK</span></span>

<span data-ttu-id="5a5c1-112">데스크톱 VR를 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택 된 PC 독립 실행형 플랫폼을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-112">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![PC, Mac & 독립 실행형 플랫폼이 강조 표시 된 unity 편집기에서 열리는 빌드 설정 창의 스크린샷](images/wmr-config-img-3.png)

<span data-ttu-id="5a5c1-114">HoloLens 2를 대상으로 하는 경우 유니버설 Windows 플랫폼로 전환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-114">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="5a5c1-115">**파일 > 빌드 설정** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-115">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="5a5c1-116">플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-116">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="5a5c1-117">**아키텍처** 를 **ARM 64** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-117">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="5a5c1-118">**대상 장치** 를 **HoloLens** 로 설정</span><span class="sxs-lookup"><span data-stu-id="5a5c1-118">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="5a5c1-119">**빌드 유형을** **D3D** 로 설정</span><span class="sxs-lookup"><span data-stu-id="5a5c1-119">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="5a5c1-120">**UWP SDK** 를 **최신 설치** 로 설정</span><span class="sxs-lookup"><span data-stu-id="5a5c1-120">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="5a5c1-121">디버그에 알려진 성능 문제가 있으므로 **빌드 구성을** **릴리스로** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![유니버설 Windows 플랫폼 강조 표시 된 unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-4.png)

<span data-ttu-id="5a5c1-123">플랫폼을 설정한 후에는 내보낼 때 Unity에서 2D 보기 대신 [몰입 형 보기](../../design/app-views.md) 를 만들도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-123">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="5a5c1-124">레거시 XR는 Unity 2019에서 더 이상 사용 되지 않으며 Unity 2020에서 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-124">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="5a5c1-125">빌드 설정에서 **플레이어 설정** ...을 엽니다. \*\*\*\* **XR 설정** 그룹을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-125">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="5a5c1-126">**XR 설정** 섹션에서 가상 현실 **지원 됨** 을 선택 하 여 가상 현실 장치 목록을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-126">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="5a5c1-127">**깊이 형식을** **16 비트 깊이로** 설정 하 고 **깊이 버퍼 공유** 를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-127">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="5a5c1-128">**단일 패스 인스턴스로** **스테레오 렌더링 모드** 설정</span><span class="sxs-lookup"><span data-stu-id="5a5c1-128">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="5a5c1-129">Holographic 원격 기능을 사용 하려는 경우에는 **WSA Holographic Remoting 지원** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a5c1-129">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![플레이어 설정 섹션이 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-9.png)