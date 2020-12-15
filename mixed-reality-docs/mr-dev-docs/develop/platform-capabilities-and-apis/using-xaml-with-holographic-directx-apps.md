---
title: 홀로그램 DirectX 앱에서 XAML 사용
description: DirectX 앱에서 2D XAML 보기와 몰입 형 보기 간 전환의 영향 및 XAML 뷰와 몰입 형 뷰를 효율적으로 사용 하는 방법을 설명 합니다.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: windows mixed reality, UWP, 앱 뷰 관리, xaml, 키보드, 연습, DirectX
ms.openlocfilehash: b062efadca9ccfe2e2caeb054f662becc0807b50
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530280"
---
# <a name="using-xaml-with-holographic-directx-apps"></a><span data-ttu-id="3430b-104">홀로그램 DirectX 앱에서 XAML 사용</span><span class="sxs-lookup"><span data-stu-id="3430b-104">Using XAML with holographic DirectX apps</span></span>

> [!NOTE]
> <span data-ttu-id="3430b-105">이 문서는 레거시 WinRT 네이티브 Api와 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="3430b-106">새 네이티브 앱 프로젝트의 경우 **[OPENXR API](../native/openxr-getting-started.md)** 를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)**.</span></span>

<span data-ttu-id="3430b-107">이 항목에서는 DirectX 앱에서 [2D XAML 보기와 몰입 형](../../design/app-views.md) 보기 간 전환의 영향 및 XAML 뷰와 몰입 형 뷰를 효율적으로 사용 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-107">This topic explains the impact of switching between [2D XAML views and immersive views](../../design/app-views.md) in your DirectX app, and how to make efficient use of both a XAML view and immersive view.</span></span>

## <a name="xaml-view-switching-overview"></a><span data-ttu-id="3430b-108">XAML 뷰 전환 개요</span><span class="sxs-lookup"><span data-stu-id="3430b-108">XAML view switching overview</span></span>

<span data-ttu-id="3430b-109">HoloLens에서 나중에 2D XAML 뷰를 표시할 수 있는 몰입 형 앱은 해당 XAML 뷰를 먼저 초기화 하 고 여기에서 몰입 형 뷰로 즉시 전환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-109">On HoloLens, an immersive app that may later display a 2D XAML view needs to initialize that XAML view first and immediately switch to an immersive view from there.</span></span> <span data-ttu-id="3430b-110">XAML은 응용 프로그램에서 모든 작업을 수행 하기 전에 로드 되므로 시작 시간이 약간 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-110">XAML will load before your app can do anything, which adds a small increase to your startup time.</span></span> <span data-ttu-id="3430b-111">XAML은 백그라운드에서 유지 되는 동안 앱 프로세스에서 메모리 공간을 계속 차지 합니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-111">XAML will continue to occupy memory space in your app process while it stays in the background.</span></span> <span data-ttu-id="3430b-112">시작 지연 및 메모리 사용의 양은 네이티브 뷰로 전환 하기 전에 XAML을 사용 하 여 앱이 수행 하는 작업에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-112">The amount of startup delay and memory usage depends on what your app does with XAML before switching to the native view.</span></span> <span data-ttu-id="3430b-113">처음에는 몰입 형 보기를 시작 하는 것을 제외 하 고 XAML 시작 코드에서 아무 작업도 수행 하지 않는 경우에는 영향이 크지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-113">If you do nothing in your XAML startup code at first except start your immersive view, the impact should be minor.</span></span> <span data-ttu-id="3430b-114">또한 holographic 렌더링은 몰입 형 보기에 직접 수행 되므로 해당 렌더링에 대해 XAML 관련 제한이 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-114">Also, because your holographic rendering is done directly to the immersive view, you'll avoid any XAML-related restrictions on that rendering.</span></span>

<span data-ttu-id="3430b-115">CPU와 GPU의 메모리 사용량을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-115">The memory usage counts for both CPU and GPU.</span></span> <span data-ttu-id="3430b-116">Direct3D 11은 가상 그래픽 메모리를 교환할 수 있지만 일부 또는 모든 XAML GPU 리소스를 교체 하지 못할 수 있으며 성능 저하가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-116">Direct3D 11 can swap virtual graphics memory, but it might not be able to swap out some or all of the XAML GPU resources, and there might be a noticeable performance hit.</span></span> <span data-ttu-id="3430b-117">어떤 경우 든 XAML 기능을 로드 하지 않아도 앱에 대 한 공간이 확보 되 고 더 나은 환경을 제공 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-117">Either way, not loading any XAML features you don't need will leave more room for your app and provide a better experience.</span></span>

## <a name="xaml-view-switching-workflow"></a><span data-ttu-id="3430b-118">XAML 뷰 전환 워크플로</span><span class="sxs-lookup"><span data-stu-id="3430b-118">XAML view switching workflow</span></span>

<span data-ttu-id="3430b-119">XAML에서 몰입 형 모드로 직접 이동 하는 앱에 대 한 워크플로는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-119">The workflow for an app that goes directly from XAML to immersive mode is like so:</span></span>
* <span data-ttu-id="3430b-120">앱이 2D XAML 뷰에서 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-120">The app starts up in the 2D XAML view.</span></span>
* <span data-ttu-id="3430b-121">응용 프로그램의 XAML 시작 시퀀스는 현재 시스템이 holographic 렌더링을 지원 하는지 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-121">The app’s XAML startup sequence detects if the current system supports holographic rendering:</span></span>
* <span data-ttu-id="3430b-122">그렇다면 응용 프로그램은 몰입 형 뷰를 만들고 전경으로 즉시 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-122">If so, the app creates the immersive view and brings it to the foreground right away.</span></span> <span data-ttu-id="3430b-123">Xaml 뷰에서는 렌더링 클래스 및 자산 로드를 포함 하 여 Windows Mixed Reality 장치에서 필요 하지 않은 모든 항목에 대해 XAML 로드를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-123">XAML loading is skipped for anything not necessary on Windows Mixed Reality devices, including any rendering classes and asset loading in the XAML view.</span></span> <span data-ttu-id="3430b-124">앱에서 키보드 입력에 XAML을 사용 하는 경우에는 입력 페이지를 계속 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-124">If the app is using XAML for keyboard input, that input page should still be created.</span></span>
* <span data-ttu-id="3430b-125">그렇지 않으면 XAML 보기는 평소와 같이 비즈니스를 계속 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-125">If not, the XAML view can continue with business as usual.</span></span>

## <a name="tip-for-rendering-graphics-across-both-views"></a><span data-ttu-id="3430b-126">두 뷰 모두에서 그래픽을 렌더링 하기 위한 팁</span><span class="sxs-lookup"><span data-stu-id="3430b-126">Tip for rendering graphics across both views</span></span>

<span data-ttu-id="3430b-127">앱이 Windows Mixed Reality의 XAML 뷰에 대해 DirectX에서 약간의 렌더링을 구현 해야 하는 경우 가장 좋은 방법은 두 뷰 모두에서 사용할 수 있는 렌더러 하나를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-127">If your app needs to implement some amount of rendering in DirectX for the XAML view in Windows Mixed Reality, your best bet is to create one renderer that can work with both views.</span></span> <span data-ttu-id="3430b-128">렌더러는 두 뷰 모두에서 액세스할 수 있는 하나의 인스턴스여야 하며 2D와 holographic 렌더링 사이를 전환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-128">The renderer should be one instance that can be accessed from both views, and it should switch between 2D and holographic rendering.</span></span> <span data-ttu-id="3430b-129">이러한 방식으로 GPU 자산은 한 번만 로드 하 여 뷰를 전환할 때 로드 시간, 메모리 영향 및 교환 되는 리소스의 양을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="3430b-129">This way GPU assets only load once, which reduces load times, memory impact, and the amount of swapped resources when switching views.</span></span>
