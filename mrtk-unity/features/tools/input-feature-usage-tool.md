---
title: 입력 기능 사용 도구
description: MRTK의 설명서 InputFeatureUsage 도구
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 413d2a3105294411f9c08f4a2add9365389ea783
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176120"
---
# <a name="input-feature-usage-tool"></a><span data-ttu-id="3ebac-104">입력 기능 사용 도구</span><span class="sxs-lookup"><span data-stu-id="3ebac-104">Input feature usage tool</span></span>

<span data-ttu-id="3ebac-105">InputFeatureUsage 도구는 개발자가 검색된 입력 소스(예: 모션 컨트롤러 또는 굴절된 손)에 대해 사용 가능한 Unity InputFeatureUsages를 신속하게 확인할 수 있도록 하는 런타임(디바이스 또는 편집기) 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="3ebac-105">The InputFeatureUsage tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the available Unity InputFeatureUsages for a detected input source (ex: motion controller or articulated hand).</span></span>

> [!NOTE]
> <span data-ttu-id="3ebac-106">이 장면만 Unity 2019.3 이상에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="3ebac-106">This scene only works on Unity 2019.3 or later.</span></span>

<span data-ttu-id="3ebac-107">이 도구는 새 하드웨어 컨트롤러에 대한 지원을 개발할 때 매우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ebac-107">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="3ebac-108">또한 기존 컨트롤러에 대한 지원 클래스에서 의심되는 컨트롤 매핑 문제를 확인하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ebac-108">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![InputFeatureUsage 도구](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a><span data-ttu-id="3ebac-110">InputFeatureUsage 도구 사용</span><span class="sxs-lookup"><span data-stu-id="3ebac-110">Using the InputFeatureUsage tool</span></span>

<span data-ttu-id="3ebac-111">InputFeatureUsage 도구를 시작하려면 **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool로** 이동하여 **InputFeatureUsageTool** 장면을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3ebac-111">To get started with the InputFeatureUsage tool, navigate to **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** and open the **InputFeatureUsageTool** scene.</span></span> <span data-ttu-id="3ebac-112">장면이 로드되면 프로젝트를 편집기에서 실행하거나, 재생 모드를 사용하거나, 디바이스에서 빌드 및 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ebac-112">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="3ebac-113">컨트롤러에 대한 Unity의 매핑을 검사하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3ebac-113">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="3ebac-114">컨트롤러 커넥트</span><span class="sxs-lookup"><span data-stu-id="3ebac-114">Connect the controller</span></span>
- <span data-ttu-id="3ebac-115">각 단추를 누르고 각 축 이동</span><span class="sxs-lookup"><span data-stu-id="3ebac-115">Press each button and move each axis</span></span>
- <span data-ttu-id="3ebac-116">디스플레이에서 기능 사용량을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="3ebac-116">Note the feature usages in the display</span></span>
- <span data-ttu-id="3ebac-117">컨트롤러에 대한 입력 시스템 데이터 공급자의 컨트롤 매핑 업데이트</span><span class="sxs-lookup"><span data-stu-id="3ebac-117">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="3ebac-118">InputFeatureUsage 도구는 Microsoft Mixed Reality Toolkit 구성 요소를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ebac-118">The InputFeatureUsage tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="3ebac-119">Unity와 직접 통신하여 기능 사용을 확인하고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3ebac-119">It directly communicates with Unity to determine and display the feature usages.</span></span>

### <a name="panels"></a><span data-ttu-id="3ebac-120">패널</span><span class="sxs-lookup"><span data-stu-id="3ebac-120">Panels</span></span>

<span data-ttu-id="3ebac-121">패널에는 감지된 모든 Unity 입력 소스에서 보고된 모든 InputFeatureUsages의 현재 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ebac-121">The panels display the current state of all reported InputFeatureUsages on all detected Unity input sources.</span></span>

<span data-ttu-id="3ebac-122">위쪽에 있는 작은 패널에는 검색된 모든 원본의 이름이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ebac-122">The smaller panel along the top lists the names of all detected sources.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ebac-123">참조</span><span class="sxs-lookup"><span data-stu-id="3ebac-123">See also</span></span>

- [<span data-ttu-id="3ebac-124">입력 시스템 데이터 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="3ebac-124">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="3ebac-125">컨트롤러 매핑 도구</span><span class="sxs-lookup"><span data-stu-id="3ebac-125">Controller mapping tool</span></span>](controller-mapping-tool.md)
