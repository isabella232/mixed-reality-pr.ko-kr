---
title: 직접 상호 작용 예제
description: MRTK의 손 상호 작용 예제
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 손 상호 작용, 경계 컨트롤, 누를 수 있는 단추,
ms.openlocfilehash: 229933dfd2414e485da6c1a77a2ffb08c9982249
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908403"
---
# <a name="hand-interaction-examples-scene"></a><span data-ttu-id="f896f-104">손 상호 작용 예제 장면</span><span class="sxs-lookup"><span data-stu-id="f896f-104">Hand interaction examples scene</span></span>

![손 상호 작용 예제 1](../images/hand-interaction-examples/MRTK_HandInteractionExamples.png)

<span data-ttu-id="f896f-106">**HandInteractionExamples** 예제 장면에는 굴절된 손 입력을 강조하는 다양한 유형의 상호 작용 및 UI 컨트롤이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f896f-106">The **HandInteractionExamples** example scene contains various types of interactions and UI controls that highlight articulated hand input.</span></span> <span data-ttu-id="f896f-107">MRTK의 입력 시뮬레이션을 사용하면 Unity 편집기에서 손 추적 상호 작용을 경험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f896f-107">With MRTK's input simulation, you can experience hand-tracking interactions in Unity editor.</span></span> 

<span data-ttu-id="f896f-108">**HandInteractionExamples** 장면은 MRTK의 Examples 패키지에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f896f-108">**HandInteractionExamples** scene is included in the MRTK's Examples package.</span></span> <span data-ttu-id="f896f-109">Mixed Reality [기능](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 도구를 통해 **Mixed Reality Toolkit Examples** 패키지를 다운로드하고 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f896f-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="f896f-110">Unity에서 창 > 패키지 관리자 > 프로젝트 > 사용자 지정 메뉴를 사용하고 **도구 키트 예제 Mixed Reality 선택합니다.**</span><span class="sxs-lookup"><span data-stu-id="f896f-110">In Unity, use the menu Window > Package Manager > In Project > Custom and select **Mixed Reality Toolkit Examples**.</span></span> <span data-ttu-id="f896f-111">**데모 - HandTracking** 옆에 있는 **프로젝트로 가져오기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f896f-111">Click **Import into Project** button next to **Demos - HandTracking**.</span></span> <span data-ttu-id="f896f-112">Assets > Samples 폴더에서 **HandInteractionExamples** 장면을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f896f-112">You will be able to find **HandInteractionExamples** scene under Assets > Samples folder.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

* <span data-ttu-id="f896f-113">Mixed Reality 기능 도구를 사용하지 않는 경우 [MRTK GitHub의 릴리스 페이지에서](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage를** 직접 다운로드하여 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f896f-113">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

> [!NOTE]
> <span data-ttu-id="f896f-114">이 예제 장면에서는 *TextMesh Pro* 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f896f-114">This example scene uses *TextMesh Pro*.</span></span> <span data-ttu-id="f896f-115">장면을 열려면 장면을 가져오는 동안 해당 프롬프트가 표시되면 *'TMP Essentials 가져오기'를* 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f896f-115">To open the scene, click *'Import TMP Essentials'* when the respective prompt is shown during the import of the scene.</span></span> <span data-ttu-id="f896f-116">그러면 Unity에서 TextMesh Pro 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f896f-116">Unity will then import TextMesh Pro packages.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_TMP2.png" width="450" alt="Example TMP2">



<span data-ttu-id="f896f-117">**HandInteractionExamples** 장면에서 이러한 구성 요소를 경험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f896f-117">You can experience these components in **HandInteractionExamples** scene</span></span>

- [<span data-ttu-id="f896f-118">누를 수 있는 단추</span><span class="sxs-lookup"><span data-stu-id="f896f-118">Pressable button</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="f896f-119">경계 컨트롤</span><span class="sxs-lookup"><span data-stu-id="f896f-119">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="f896f-120">개체 조작자</span><span class="sxs-lookup"><span data-stu-id="f896f-120">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)
- [<span data-ttu-id="f896f-121">슬레이트</span><span class="sxs-lookup"><span data-stu-id="f896f-121">Slate</span></span>](../ux-building-blocks/slate.md)
- [<span data-ttu-id="f896f-122">슬라이더</span><span class="sxs-lookup"><span data-stu-id="f896f-122">Slider</span></span>](../ux-building-blocks/sliders.md)
- [<span data-ttu-id="f896f-123">시스템 키보드</span><span class="sxs-lookup"><span data-stu-id="f896f-123">System keyboard</span></span>](../ux-building-blocks/system-keyboard.md)
