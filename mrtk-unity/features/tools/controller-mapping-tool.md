---
title: 컨트롤러 매핑 도구
description: MRTK의 컨트롤러 매핑 도구에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 8c1da7ae6a46bd00599a77b1c4cbb0b2f7baa632
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176169"
---
# <a name="controller-mapping-tool"></a><span data-ttu-id="34b76-104">컨트롤러 매핑 도구</span><span class="sxs-lookup"><span data-stu-id="34b76-104">Controller mapping tool</span></span>

<span data-ttu-id="34b76-105">컨트롤러 매핑 도구는 개발자가 하드웨어 컨트롤러(예: 모션 컨트롤러)에 대한 Unity 입력 축 및 단추 매핑을 신속하게 확인할 수 있는 런타임(디바이스 또는 편집기) 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="34b76-105">The controller mapping tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the Unity input axis and button mappings for a hardware controller (ex: motion controller).</span></span>

<span data-ttu-id="34b76-106">이 도구는 새 하드웨어 컨트롤러에 대한 지원을 개발할 때 매우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="34b76-106">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="34b76-107">또한 기존 컨트롤러에 대한 지원 클래스에서 의심되는 컨트롤 매핑 문제를 확인하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b76-107">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![컨트롤러 매핑 도구](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a><span data-ttu-id="34b76-109">컨트롤러 매핑 도구 사용</span><span class="sxs-lookup"><span data-stu-id="34b76-109">Using the controller mapping tool</span></span>

<span data-ttu-id="34b76-110">컨트롤러 매핑 도구를 시작하려면 **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool로** 이동하여 **ControllerMappingTool** 장면을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="34b76-110">To get started with the controller mapping tool, navigate to **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** and open the **ControllerMappingTool** scene.</span></span> <span data-ttu-id="34b76-111">장면이 로드되면 프로젝트를 편집기에서 실행하거나, 재생 모드를 사용하거나, 디바이스에서 빌드 및 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b76-111">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="34b76-112">컨트롤러에 대한 Unity의 매핑을 검사하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="34b76-112">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="34b76-113">컨트롤러 커넥트</span><span class="sxs-lookup"><span data-stu-id="34b76-113">Connect the controller</span></span>
- <span data-ttu-id="34b76-114">각 단추를 누르고 각 축 이동</span><span class="sxs-lookup"><span data-stu-id="34b76-114">Press each button and move each axis</span></span>
- <span data-ttu-id="34b76-115">디스플레이의 매핑을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="34b76-115">Note the mappings in the display</span></span>
- <span data-ttu-id="34b76-116">컨트롤러에 대한 입력 시스템 데이터 공급자의 컨트롤 매핑 업데이트</span><span class="sxs-lookup"><span data-stu-id="34b76-116">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="34b76-117">컨트롤러 매핑 도구는 Microsoft Mixed Reality Toolkit 구성 요소를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34b76-117">The controller mapping tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="34b76-118">Unity와 직접 통신하여 컨트롤 매핑을 확인하고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="34b76-118">It directly communicates with Unity to determine and display the control mappings.</span></span>

### <a name="all-controls-display"></a><span data-ttu-id="34b76-119">모든 컨트롤 표시</span><span class="sxs-lookup"><span data-stu-id="34b76-119">All controls display</span></span>

<span data-ttu-id="34b76-120">큰 디스플레이 패널은 정의된 모든 Unity 입력 축 및 단추의 상태를 보고합니다(예: 축 10, 단추 3).</span><span class="sxs-lookup"><span data-stu-id="34b76-120">The large display panel reports the state of all defined Unity input axes and buttons (ex: Axis 10, Button 3).</span></span> <span data-ttu-id="34b76-121">이 패널은 컨트롤러의 상태에 대한 전체 보기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="34b76-121">This panel provides a complete view of the state of the controller.</span></span>

![모든 컨트롤 표시](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a><span data-ttu-id="34b76-123">활성 컨트롤 표시</span><span class="sxs-lookup"><span data-stu-id="34b76-123">Active controls display</span></span>

<span data-ttu-id="34b76-124">더 작고 좁은 디스플레이 패널에는 Unity 입력 축과 활성 상태의 단추(예: 단추를 누른 경우)가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="34b76-124">The smaller, narrow display panel shows the Unity input axed and buttons which are in an active state (ex: a button is pressed).</span></span> <span data-ttu-id="34b76-125">활성 컨트롤 표시는 컨트롤러 상태에 대한 읽기 쉬운 요약 보기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="34b76-125">The active controls display provides an easy to read summary view of the state of the controller.</span></span>

![활성 컨트롤 표시](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a><span data-ttu-id="34b76-127">참조</span><span class="sxs-lookup"><span data-stu-id="34b76-127">See also</span></span>

- [<span data-ttu-id="34b76-128">입력 시스템 데이터 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="34b76-128">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="34b76-129">InputFeatureUsage 도구</span><span class="sxs-lookup"><span data-stu-id="34b76-129">InputFeatureUsage tool</span></span>](input-feature-usage-tool.md)
