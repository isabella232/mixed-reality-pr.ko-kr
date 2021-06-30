---
title: 진단 시스템 개요
description: MRTK에서 진단을 사용 및 사용 하지 않도록 설정 하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 0de7b904a48453d6021cf7aed5835412c19b7884
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121781"
---
# <a name="diagnostic-system"></a><span data-ttu-id="49e33-104">진단 시스템</span><span class="sxs-lookup"><span data-stu-id="49e33-104">Diagnostic system</span></span>

<span data-ttu-id="49e33-105">Mixed Reality Toolkit 진단 시스템은 응용 프로그램 내에서 실행 되는 진단 도구를 제공 하 여 응용 프로그램 문제를 분석할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="49e33-105">The Mixed Reality Toolkit Diagnostic System provides diagnostic tools that run within the application to enable analysis of application issues.</span></span>

<span data-ttu-id="49e33-106">진단 시스템의 첫 번째 릴리스에는 응용 프로그램을 사용 하는 동안 성능 문제를 분석 하는 데 사용할 수 있는 [시각적 프로파일러가](using-visual-profiler.md) 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49e33-106">The first release of the Diagnostic System contains the [Visual Profiler](using-visual-profiler.md) to allow for analyzing performance issues while using the application.</span></span>

## <a name="getting-started"></a><span data-ttu-id="49e33-107">시작</span><span class="sxs-lookup"><span data-stu-id="49e33-107">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="49e33-108">전체 제품 개발 주기 전체에서 진단 시스템을 사용 하도록 설정 하 고 최종 버전을 빌드 및 릴리스 하기 전에 마지막 변경 내용으로 비활성화 하 **_는 것이 좋습니다._**</span><span class="sxs-lookup"><span data-stu-id="49e33-108">It is **_highly_** recommended that the Diagnostic System be enabled throughout the entire product development cycle and disabled as the last change prior to building and releasing the final version.</span></span>

<span data-ttu-id="49e33-109">진단 시스템 사용을 시작 하는 데는 두 가지 주요 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49e33-109">There are two key steps to start using the Diagnostic System.</span></span>

1. <span data-ttu-id="49e33-110">진단 시스템 [사용](#enable-diagnostics)</span><span class="sxs-lookup"><span data-stu-id="49e33-110">[Enable](#enable-diagnostics) the Diagnostic System</span></span>
2. <span data-ttu-id="49e33-111">진단 옵션 [구성](#configure-diagnostic-options)</span><span class="sxs-lookup"><span data-stu-id="49e33-111">[Configure](#configure-diagnostic-options) diagnostic options</span></span>

### <a name="enable-diagnostics"></a><span data-ttu-id="49e33-112">진단 사용</span><span class="sxs-lookup"><span data-stu-id="49e33-112">Enable diagnostics</span></span>

<span data-ttu-id="49e33-113">진단 시스템은 MixedRealityToolkit 개체 (또는 다른 [서비스 등록자](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 구성 요소)를 통해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="49e33-113">The diagnostics system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="49e33-114">다음 단계에서는 MixedRealityToolkit 개체를 사용 하는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49e33-114">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="49e33-115">다른 서비스 등록 기관 필요한 단계는 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49e33-115">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="49e33-116">장면 계층 구조에서 MixedRealityToolkit 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="49e33-116">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="49e33-118">검사기 패널에서 진단 시스템 섹션으로 이동 하 고 사용을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="49e33-118">Navigate the Inspector panel to the Diagnostics System section and check Enable</span></span>
1. <span data-ttu-id="49e33-119">진단 시스템 구현 선택</span><span class="sxs-lookup"><span data-stu-id="49e33-119">Select the Diagnostics System implementation</span></span>

    ![진단 시스템 구현 선택](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="49e33-121">기본 프로필의 사용자 `DefaultMixedRealityToolkitConfigurationProfile` (자산/m a s v k/SDK/프로필)에는 진단 시스템이 개체를 사용 하도록 미리 구성 되어 있습니다 [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) .</span><span class="sxs-lookup"><span data-stu-id="49e33-121">Users of the default profile, `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles), will have the diagnostics system pre-configured to use the [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) object.</span></span>

### <a name="configure-diagnostic-options"></a><span data-ttu-id="49e33-122">진단 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="49e33-122">Configure diagnostic options</span></span>

<span data-ttu-id="49e33-123">진단 시스템은 구성 프로필을 사용 하 여 표시할 구성 요소를 지정 하 고 해당 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49e33-123">The diagnostics system uses a configuration profile to specify which components are to be displayed and to configure their settings.</span></span> <span data-ttu-id="49e33-124">사용 가능한 구성 요소 설정에 대 한 자세한 내용은 [진단 시스템 구성](configuring-diagnostics.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="49e33-124">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information pertaining to the available component settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="49e33-125">빌드 및 배포 단계를 요구 하지 않고 응용 프로그램을 개발 하는 동안 Unity의 재생 모드를 사용할 수 있지만 대상 하드웨어 및 플랫폼에서 실행 되는 컴파일된 응용 프로그램을 사용 하 여 진단 시스템 결과를 평가 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="49e33-125">While it is possible to use Unity's Play Mode while developing applications without requiring the build and deploy steps, it is important to evaluate the diagnostics system results using a compiled application running on the target hardware and platform.</span></span>
>
> <span data-ttu-id="49e33-126">[Visual Profiler](using-visual-profiler.md)와 같은 성능 진단은 편집기 내에서 실행 될 때 실제 응용 프로그램 성능을 정확 하 게 반영 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49e33-126">Performance diagnostics, such as the [Visual Profiler](using-visual-profiler.md), may not accurately reflect actual application performance when run from within the editor.</span></span>

## <a name="see-also"></a><span data-ttu-id="49e33-127">참조</span><span class="sxs-lookup"><span data-stu-id="49e33-127">See also</span></span>

- [<span data-ttu-id="49e33-128">진단 API 설명서</span><span class="sxs-lookup"><span data-stu-id="49e33-128">Diagnostics API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [<span data-ttu-id="49e33-129">진단 시스템 구성</span><span class="sxs-lookup"><span data-stu-id="49e33-129">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
- [<span data-ttu-id="49e33-130">시각적 프로파일러 사용</span><span class="sxs-lookup"><span data-stu-id="49e33-130">Using the Visual Profiler</span></span>](using-visual-profiler.md)
