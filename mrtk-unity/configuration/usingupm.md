---
title: Unity 패키지 관리자 사용
description: Unity 패키지 관리자 MRTK 사용
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK 패키지,
ms.openlocfilehash: 524783c48b82722aec26648ea54477a6c7bcd4ae
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177325"
---
# <a name="using-the-unity-package-manager"></a><span data-ttu-id="0fb0c-104">Unity 패키지 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="0fb0c-104">Using the Unity Package Manager</span></span>

<span data-ttu-id="0fb0c-105">버전 2.5.0부터는 [Mixed Reality 기능 도구를](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)사용하여 Microsoft Mixed Reality Toolkit Unity 2019.4 이상 버전을 사용하는 경우 UNITY 패키지 관리자(UPM)와 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb0c-105">Starting with version 2.5.0, using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), the Microsoft Mixed Reality Toolkit integrates with the Unity Package Manager (UPM) when using Unity 2019.4 and newer.</span></span>

## <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="0fb0c-106">Mixed Reality Feature Tool 사용</span><span class="sxs-lookup"><span data-stu-id="0fb0c-106">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="0fb0c-107">Mixed Reality 기능 [도구 시작에서](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 설명한 대로 [이 링크를](https://aka.ms/MRFeatureTool)사용하여 도구를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb0c-107">As described in [Welcome to the Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) you can download the tool using [this link](https://aka.ms/MRFeatureTool).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0fb0c-108">프로젝트의 매니페스트에 `Microsoft Mixed Reality` 섹션에 항목이 있는 경우 `scopedRegistries` 제거하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb0c-108">If the project's manifest has a `Microsoft Mixed Reality` entry in the `scopedRegistries` section, it is recommended that it be removed.</span></span>
>
> <span data-ttu-id="0fb0c-109">구성된 범위의 레지스트리를 제거하려면 로 `Edit`  >  `Project Settings`  >  `Package Manager` 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="0fb0c-109">To remove a configured scoped registry, please to to `Edit` > `Project Settings` > `Package Manager`.</span></span>
>
> ![범위가 있는 레지스트리 제거](../features/images/packaging/RemoveScopedRegistry.png)

<span data-ttu-id="0fb0c-111">기능을 검색할 때 MRTK 패키지가 제목 아래에 `Mixed Reality Toolkit` 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb0c-111">MRTK packages appear under the `Mixed Reality Toolkit` heading when discovering features.</span></span>

![기능 검색](../features/images/packaging/DiscoverFeatures.png)

<span data-ttu-id="0fb0c-113">기능을 선택할 때 필수 의존성과 관련될 필요가 없습니다. 도구는 자동으로 다운로드하여 프로젝트에 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb0c-113">When selecting features, there is no need to be concerned with required dependencies, the tool will automatically download and integrate them into the project.</span></span>

![필수 종속성](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="0fb0c-115">Unity 패키지 관리자 Mixed Reality 기능 관리</span><span class="sxs-lookup"><span data-stu-id="0fb0c-115">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="0fb0c-116">Mixed Reality Toolkit 패키지가 패키지 매니페스트에 추가되면 Unity 패키지 관리자 사용자 인터페이스를 사용하여 관리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb0c-116">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![MRTK Foundation UPM 패키지](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="0fb0c-118">Unity 패키지 관리자 사용하여 Mixed Reality Toolkit 패키지를 제거한 경우 [이전에 설명한 단계를](#using-the-mixed-reality-feature-tool)사용하여 다시 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb0c-118">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#using-the-mixed-reality-feature-tool).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="0fb0c-119">Mixed Reality Toolkit 예제 사용</span><span class="sxs-lookup"><span data-stu-id="0fb0c-119">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="0fb0c-120">자산 패키지(.unitypackage) 파일을 사용하는 경우와 달리 및 는 `com.microsoft.mixedreality.toolkit.examples` 예제 장면 및 자산을 자동으로 `com.microsoft.mixedreality.toolkit.handphysicsservice` 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0fb0c-120">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="0fb0c-121">하나 이상의 예제를 활용하려면 다음 단계를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="0fb0c-121">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="0fb0c-122">Unity 편집기에서 으로 이동합니다. `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="0fb0c-122">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="0fb0c-123">패키지 목록에서 를 선택합니다. `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="0fb0c-123">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="0fb0c-124">목록에서 원하는 샘플을 찾습니다. `Samples`</span><span class="sxs-lookup"><span data-stu-id="0fb0c-124">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="0fb0c-125">`Import into Project`을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb0c-125">Click `Import into Project`</span></span>

![샘플 가져오기](../features/images/packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="0fb0c-127">예제 패키지가 업데이트되면 Unity는 가져온 샘플을 업데이트하는 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0fb0c-127">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!NOTE]
> <span data-ttu-id="0fb0c-128">가져온 샘플을 업데이트하면 해당 샘플 및 관련 자산에 대해 변경된 내용을 덮어쓰게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fb0c-128">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fb0c-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fb0c-129">See Also</span></span>

- [<span data-ttu-id="0fb0c-130">패키지 Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="0fb0c-130">Mixed Reality Toolkit packages</span></span>](../packages/mrtk-packages.md)
