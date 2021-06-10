---
title: Unity 패키지 관리자 사용
description: Unity 패키지 관리자에서 MRTK 사용
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK 패키지,
ms.openlocfilehash: e3e7a2d06cd38d7a9e8daf579f1a312904a86280
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345076"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a><span data-ttu-id="3119e-104">Mixed Reality Toolkit 및 Unity 패키지 관리자</span><span class="sxs-lookup"><span data-stu-id="3119e-104">Mixed Reality Toolkit and Unity Package Manager</span></span>

<span data-ttu-id="3119e-105">2.5.0 버전부터, [혼합 현실 기능 도구](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)를 사용 하 여 Microsoft Mixed reality Toolkit은 unity 2019.4 이상 버전을 사용 하는 경우에는 UPM (Unity 패키지 관리자)와 통합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3119e-105">Starting with version 2.5.0, using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), the Microsoft Mixed Reality Toolkit integrates with the Unity Package Manager (UPM) when using Unity 2019.4 and newer.</span></span>

## <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="3119e-106">Mixed Reality Feature Tool 사용</span><span class="sxs-lookup"><span data-stu-id="3119e-106">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="3119e-107">[Mixed Reality 기능 도구 시작](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 에 설명 된 대로 [이 링크](https://aka.ms/MRFeatureTool)를 사용 하 여 도구를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3119e-107">As described in [Welcome to the Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) you can download the tool using [this link](https://aka.ms/MRFeatureTool).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3119e-108">프로젝트의 매니페스트에 `Microsoft Mixed Reality` 섹션에 항목이 있는 경우 `scopedRegistries` 제거 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3119e-108">If the project's manifest has a `Microsoft Mixed Reality` entry in the `scopedRegistries` section, it is recommended that it be removed.</span></span>
>
> <span data-ttu-id="3119e-109">구성 된 범위가 지정 된 레지스트리를 제거 하려면을 (를) 참조 하세요 `Edit`  >  `Project Settings`  >  `Package Manager` .</span><span class="sxs-lookup"><span data-stu-id="3119e-109">To remove a configured scoped registry, please to to `Edit` > `Project Settings` > `Package Manager`.</span></span>
>
> ![범위가 지정 된 레지스트리 제거](../features/images/packaging/RemoveScopedRegistry.png)

<span data-ttu-id="3119e-111">MRTK 패키지는 기능을 검색할 때 제목 아래에 나타납니다 `Mixed Reality Toolkit` .</span><span class="sxs-lookup"><span data-stu-id="3119e-111">MRTK packages appear under the `Mixed Reality Toolkit` heading when discovering features.</span></span>

![검색 기능](../features/images/packaging/DiscoverFeatures.png)

<span data-ttu-id="3119e-113">기능을 선택 하는 경우 필요한 종속성을 걱정 하지 않아도 되며, 도구가 자동으로 다운로드 되어 프로젝트에 통합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3119e-113">When selecting features, there is no need to be concerned with required dependencies, the tool will automatically download and integrate them into the project.</span></span>

![필수 종속성](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="3119e-115">Unity 패키지 관리자를 사용 하 여 혼합 현실 기능 관리</span><span class="sxs-lookup"><span data-stu-id="3119e-115">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="3119e-116">혼합 현실 도구 키트 패키지는 패키지 매니페스트에 추가 된 후 Unity 패키지 관리자 사용자 인터페이스를 사용 하 여 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3119e-116">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![MRTK Foundation UPM 패키지](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="3119e-118">Unity 패키지 관리자를 사용 하 여 혼합 현실 도구 키트 패키지를 제거 하는 경우 [앞에서 설명한 단계](#using-the-mixed-reality-feature-tool)를 사용 하 여 다시 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3119e-118">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#using-the-mixed-reality-feature-tool).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="3119e-119">Mixed Reality Toolkit 예 사용</span><span class="sxs-lookup"><span data-stu-id="3119e-119">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="3119e-120">자산 패키지 (. unitypackage) 파일을 사용 하는 경우와 달리 `com.microsoft.mixedreality.toolkit.examples` `com.microsoft.mixedreality.toolkit.handphysicsservice` 예제 장면 및 자산을 자동으로 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3119e-120">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="3119e-121">하나 이상의 예제를 활용 하려면 다음 단계를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="3119e-121">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="3119e-122">Unity 편집기에서로 이동 합니다. `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="3119e-122">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="3119e-123">패키지 목록에서 다음을 선택 합니다. `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="3119e-123">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="3119e-124">목록에서 원하는 샘플 찾기 `Samples`</span><span class="sxs-lookup"><span data-stu-id="3119e-124">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="3119e-125">`Import into Project`을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3119e-125">Click `Import into Project`</span></span>

![샘플 가져오기](../features/images/packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="3119e-127">예제 패키지가 업데이트 되 면 Unity는 가져온 샘플을 업데이트 하는 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3119e-127">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!NOTE]
> <span data-ttu-id="3119e-128">가져온 샘플을 업데이트 하면 해당 샘플과 연결 된 자산에 대 한 변경 내용이 모두 덮어쓰여집니다.</span><span class="sxs-lookup"><span data-stu-id="3119e-128">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="3119e-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3119e-129">See Also</span></span>

- [<span data-ttu-id="3119e-130">혼합 현실 도구 키트 패키지</span><span class="sxs-lookup"><span data-stu-id="3119e-130">Mixed Reality Toolkit packages</span></span>](../packages/mrtk-packages.md)