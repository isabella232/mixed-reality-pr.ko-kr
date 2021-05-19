---
title: 입력 기능 사용 도구
description: MRTK의 설명서 InputFeatureUsage 도구
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 0f2d3d3eb07d8b631f3f11a8b497a22a028a2f24
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145017"
---
# <a name="inputfeatureusage-tool"></a><span data-ttu-id="27737-104">InputFeatureUsage 도구</span><span class="sxs-lookup"><span data-stu-id="27737-104">InputFeatureUsage tool</span></span>

<span data-ttu-id="27737-105">InputFeatureUsage 도구는 개발자가 검색 된 입력 원본에 대해 사용 가능한 Unity Inputfeatureusage를 신속 하 게 결정할 수 있도록 하는 런타임 (장치 또는 편집기에서) 도구입니다 (예: 동작 컨트롤러 또는 트레일러)</span><span class="sxs-lookup"><span data-stu-id="27737-105">The InputFeatureUsage tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the available Unity InputFeatureUsages for a detected input source (ex: motion controller or articulated hand).</span></span>

> [!NOTE]
> <span data-ttu-id="27737-106">이 장면은 Unity 2019.3 이상 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="27737-106">This scene only works on Unity 2019.3 or later.</span></span>

<span data-ttu-id="27737-107">이 도구는 새 하드웨어 컨트롤러에 대 한 지원을 개발할 때 매우 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="27737-107">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="27737-108">또한 기존 컨트롤러에 대 한 지원 클래스에서 의심 스러운 제어 매핑 문제를 확인 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27737-108">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![InputFeatureUsage 도구](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a><span data-ttu-id="27737-110">InputFeatureUsage 도구 사용</span><span class="sxs-lookup"><span data-stu-id="27737-110">Using the InputFeatureUsage tool</span></span>

<span data-ttu-id="27737-111">InputFeatureUsage 도구를 시작 하려면 **Mrtk/tools/RuntimeTools/tools/InputFeatureUsageTool** 로 이동 하 여 **InputFeatureUsageTool** 장면을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="27737-111">To get started with the InputFeatureUsage tool, navigate to **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** and open the **InputFeatureUsageTool** scene.</span></span> <span data-ttu-id="27737-112">장면이 로드 되 면 프로젝트는 편집기에서 실행 하거나 재생 모드를 사용 하 여 실행 하거나 장치에서 빌드하여 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27737-112">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="27737-113">컨트롤러에 대 한 Unity의 매핑을 검사 하려면:</span><span class="sxs-lookup"><span data-stu-id="27737-113">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="27737-114">컨트롤러 연결</span><span class="sxs-lookup"><span data-stu-id="27737-114">Connect the controller</span></span>
- <span data-ttu-id="27737-115">각 단추를 누르고 각 축을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="27737-115">Press each button and move each axis</span></span>
- <span data-ttu-id="27737-116">표시의 기능 사용에 유의 하십시오.</span><span class="sxs-lookup"><span data-stu-id="27737-116">Note the feature usages in the display</span></span>
- <span data-ttu-id="27737-117">입력 시스템 데이터 공급자의 컨트롤러에 대 한 컨트롤 매핑을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="27737-117">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="27737-118">InputFeatureUsage 도구는 Microsoft Mixed Reality 도구 키트 구성 요소를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27737-118">The InputFeatureUsage tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="27737-119">Unity와 직접 통신 하 여 기능 사용을 확인 하 고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="27737-119">It directly communicates with Unity to determine and display the feature usages.</span></span>

### <a name="panels"></a><span data-ttu-id="27737-120">패널</span><span class="sxs-lookup"><span data-stu-id="27737-120">Panels</span></span>

<span data-ttu-id="27737-121">패널에는 검색 된 모든 Unity 입력 원본에 대해 보고 된 모든 InputFeatureUsages의 현재 상태가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27737-121">The panels display the current state of all reported InputFeatureUsages on all detected Unity input sources.</span></span>

<span data-ttu-id="27737-122">위쪽의 작은 패널에는 검색 된 모든 원본의 이름이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27737-122">The smaller panel along the top lists the names of all detected sources.</span></span>

## <a name="see-also"></a><span data-ttu-id="27737-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="27737-123">See also</span></span>

- [<span data-ttu-id="27737-124">입력 시스템 데이터 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="27737-124">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="27737-125">컨트롤러 매핑 도구</span><span class="sxs-lookup"><span data-stu-id="27737-125">Controller mapping tool</span></span>](controller-mapping-tool.md)
