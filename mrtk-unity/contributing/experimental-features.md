---
title: 실험적 기능
description: MRTK의 실험적 기능과 관련 된 문서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 341ba0ee3e5900cc52f1ef715232f49064102309
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121381"
---
# <a name="experimental-features"></a><span data-ttu-id="838d5-104">실험적 기능</span><span class="sxs-lookup"><span data-stu-id="838d5-104">Experimental features</span></span>

<span data-ttu-id="838d5-105">MRTK 팀에서 작업 하는 일부 기능은 세부 정보를 완전히 갖춰진 않는 경우에도 많은 초기 값이 있는 것 처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-105">Some features the MRTK team works on appear to have a lot of initial value even if we haven’t fully fleshed out the details.</span></span> <span data-ttu-id="838d5-106">이러한 유형의 기능을 위해 커뮤니티에서 일찍 볼 수 있는 기회를 원합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-106">For these types of features, we want the community to get a chance to see them early.</span></span> <span data-ttu-id="838d5-107">주기 초기에 있기 때문에 실험으로 표시 하 여 계속 진화 하 고 있으며 시간이 지남에 따라 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-107">Because they are early in the cycle, we label them as experimental to indicate that they are still evolving, and subject to change over time.</span></span>

## <a name="what-to-expect-from-an-experimental-feature"></a><span data-ttu-id="838d5-108">실험적 기능에서 예측할 수 있는 사항</span><span class="sxs-lookup"><span data-stu-id="838d5-108">What to expect from an experimental feature</span></span>

<span data-ttu-id="838d5-109">구성 요소가 실험적으로 표시 되어 있는 경우 다음을 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-109">If a component is marked experimental you can expect the following:</span></span>

- <span data-ttu-id="838d5-110">하위 폴더에 있는 사용법을 보여 주는 예제 장면 `MRTK/Examples/Experimental`</span><span class="sxs-lookup"><span data-stu-id="838d5-110">An example scene demonstrating usage, located under `MRTK/Examples/Experimental` sub-folder</span></span>
- <span data-ttu-id="838d5-111">실험적 기능에 문서를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-111">Experimental features may not have docs.</span></span>
- <span data-ttu-id="838d5-112">테스트는 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-112">They probably don't have tests.</span></span>
- <span data-ttu-id="838d5-113">실험적 기능은 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-113">Experimental features are subject to change.</span></span>

## <a name="experimental-feature-guidelines"></a><span data-ttu-id="838d5-114">실험적 기능 지침</span><span class="sxs-lookup"><span data-stu-id="838d5-114">Experimental feature guidelines</span></span>

### <a name="experimental-code-should-live-in-a-separate-folder"></a><span data-ttu-id="838d5-115">실험적 코드는 별도의 폴더에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-115">Experimental code should live in a separate folder</span></span>

<span data-ttu-id="838d5-116">실험적 코드는 최고 수준의 실험적 폴더와 실험적 기능 이름을 차례로 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-116">Experimental code should go into a top-level experimental folder followed by the experimental feature name.</span></span> <span data-ttu-id="838d5-117">예를 들어 새 기능 FooBar를 적용 하려는 경우 코드를 다음과 같이 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-117">For example, if trying to contribute a new feature FooBar, put code in the following:</span></span>

- <span data-ttu-id="838d5-118">예제 장면, 스크립트 이동 `MRTK/Examples/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="838d5-118">Example scenes, scripts go into `MRTK/Examples/Experimental/FooBar/`</span></span>
- <span data-ttu-id="838d5-119">구성 요소 스크립트, prefabs으로 이동 `MRTK/SDK/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="838d5-119">Component scripts, prefabs go into `MRTK/SDK/Experimental/FooBar/`</span></span>
- <span data-ttu-id="838d5-120">구성 요소 검사기 이동 `MRTK/SDK/Inspectors/Experimental/FooBar`</span><span class="sxs-lookup"><span data-stu-id="838d5-120">Component inspectors go into `MRTK/SDK/Inspectors/Experimental/FooBar`</span></span>

<span data-ttu-id="838d5-121">실험적 기능 이름 아래의 하위 폴더를 사용 하는 경우 MRTK의 동일한 폴더 구조를 미러링합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-121">When using sub-folders under the experimental feature name, try to mirror the same folder structure of MRTK.</span></span>

<span data-ttu-id="838d5-122">예를 들어, solvers는 다음과 같이 진행 됩니다. `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span><span class="sxs-lookup"><span data-stu-id="838d5-122">For example, solvers would go under `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span></span>

<span data-ttu-id="838d5-123">위쪽 근처의 장면 폴더에 장면 유지: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span><span class="sxs-lookup"><span data-stu-id="838d5-123">Keep scenes in a scene folder near the top: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span></span>

> [!NOTE]
> <span data-ttu-id="838d5-124">단일 실험적 루트 폴더가 없고 대신 실험을 만드는 것으로 간주 `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-124">We considered not having a single Experimental root folder and instead putting Experimental under say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity`.</span></span> <span data-ttu-id="838d5-125">실험 기능을 보다 쉽게 검색할 수 있도록 기준으로 폴더를 사용 하기로 결정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-125">We decided to go with folders at the base to make the experimental features easier to discover.</span></span>

### <a name="experimental-code-should-be-in-a-special-namespace"></a><span data-ttu-id="838d5-126">실험적 코드는 특수 네임 스페이스에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-126">Experimental code should be in a special namespace</span></span>

<span data-ttu-id="838d5-127">실험적 코드가 실험적이 아닌 위치와 일치 하는 실험적 네임 스페이스에 상주 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-127">Ensure that the experimental code lives in an experimental namespace that matches the non-experimental location.</span></span> <span data-ttu-id="838d5-128">예를 들어 구성 요소가 solvers의 일부인 경우 `Microsoft.MixedReality.Toolkit.Utilities.Solvers` 해당 네임 스페이스는 여야 합니다 `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .</span><span class="sxs-lookup"><span data-stu-id="838d5-128">For example, if your component is part of solvers at `Microsoft.MixedReality.Toolkit.Utilities.Solvers`, its namespace should be `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers`.</span></span>

<span data-ttu-id="838d5-129">예제는 [이 PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="838d5-129">See [this PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) for an example.</span></span>

### <a name="experimental-features-should-have-an-experimental-attribute"></a><span data-ttu-id="838d5-130">실험적 기능에는 [실험적] 특성이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-130">Experimental features should have an [Experimental] attribute</span></span>

<span data-ttu-id="838d5-131">필드 중 `[Experimental]` 하나에 특성을 추가 하 여 기능을 실험적 이라고 표시 하 고 중요 한 변경 내용을 적용 하는 작은 대화 상자를 구성 요소 편집기에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-131">Add an `[Experimental]` attribute above one of your fields to have a small dialog appear in the component editor that mentions your feature is experimental and subject to significant changes.</span></span>

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a><span data-ttu-id="838d5-132">실험적 기능에 대 한 메뉴는 "실험적" 하위 메뉴 아래에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-132">Menus for experimental features should go under "Experimental" sub-menu</span></span>

<span data-ttu-id="838d5-133">편집기에서 메뉴에 명령을 추가할 때 실험적 기능이 "실험적" 하위 메뉴 아래에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-133">Ensure that experimental features are under "experimental" sub-menus when adding commands to menus in the editor.</span></span> <span data-ttu-id="838d5-134">다음은 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-134">Here are a few examples:</span></span>

<span data-ttu-id="838d5-135">최상위 메뉴 명령 추가:</span><span class="sxs-lookup"><span data-stu-id="838d5-135">Adding a top-level menu command:</span></span>

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

<span data-ttu-id="838d5-136">구성 요소 메뉴 추가:</span><span class="sxs-lookup"><span data-stu-id="838d5-136">Adding a component menu:</span></span>

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a><span data-ttu-id="838d5-137">설명서</span><span class="sxs-lookup"><span data-stu-id="838d5-137">Documentation</span></span>

<span data-ttu-id="838d5-138">실험적 기능에 대 한 설명서를 추가 하려면 다음 단계를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="838d5-138">Follow these steps to add documentation for your experimental feature:</span></span>

1. <span data-ttu-id="838d5-139">실험적 기능에 대 한 설명서는 `readme.md` 실험적 폴더의 파일로 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-139">Any documentation for an experimental feature should go in a `readme.md` file in the experimental folder.</span></span> <span data-ttu-id="838d5-140">예: MRTK/SDK/실험적/PulseShader/추가 정보.</span><span class="sxs-lookup"><span data-stu-id="838d5-140">For example, MRTK/SDK/Experimental/PulseShader/readme.md.</span></span>

1. <span data-ttu-id="838d5-141">*기능 개요* 아래에서 *실험적* 섹션의 링크를 추가 [`Documentation/toc.yml`](../toc.yml) 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-141">Under *Feature Overviews* Add a link in the *Experimental* section at [`Documentation/toc.yml`](../toc.yml).</span></span>

### <a name="minimize-impact-to-mrtk-code"></a><span data-ttu-id="838d5-142">MRTK 코드에 대 한 영향 최소화</span><span class="sxs-lookup"><span data-stu-id="838d5-142">Minimize impact to MRTK code</span></span>

<span data-ttu-id="838d5-143">MRTK가 변경 되 면 실험에서 작업을 수행할 수 있지만 예상치 못한 방식으로 다른 사용자에 게 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-143">While your MRTK change might get your experiment to work, it could impact other people in ways you do not expect.</span></span>
<span data-ttu-id="838d5-144">MRTK core 코드에 대 한 모든 재발으로 인해 끌어오기 요청이 되돌려집니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-144">Any regressions you make to the MRTK core code would result in your pull request getting reverted.</span></span>

<span data-ttu-id="838d5-145">실험적 폴더 이외의 폴더에는 0으로 변경 하는 것을 목표로 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-145">Aim to have zero changes in folders other than experimental folders.</span></span> <span data-ttu-id="838d5-146">다음은 실험적 변경을 수행할 수 있는 폴더 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-146">Here is a list of folders that can have experimental changes:</span></span>

- <span data-ttu-id="838d5-147">MRTK/SDK/실험적</span><span class="sxs-lookup"><span data-stu-id="838d5-147">MRTK/SDK/Experimental</span></span>
- <span data-ttu-id="838d5-148">MRTK/SDK/검사기/실험적</span><span class="sxs-lookup"><span data-stu-id="838d5-148">MRTK/SDK/Inspectors/Experimental</span></span>
- <span data-ttu-id="838d5-149">MRTK/예제/실험적</span><span class="sxs-lookup"><span data-stu-id="838d5-149">MRTK/Examples/Experimental</span></span>

<span data-ttu-id="838d5-150">이러한 폴더의 외부에 있는 변경 내용은 매우 신중 하 게 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-150">Changes outside of these folders should be treated very carefully.</span></span> <span data-ttu-id="838d5-151">실험적 기능에 MRTK core 코드에 대 한 변경 내용을 포함 해야 하는 경우 테스트 및 설명서를 포함 하는 별도의 끌어오기 요청으로 MRTK 변경 내용을 분할 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-151">If your experimental feature must include changes to MRTK core code, consider splitting out MRTK changes into a separate pull request that includes tests and documentation.</span></span>

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a><span data-ttu-id="838d5-152">실험적 기능을 사용 하면 사용자의 핵심 컨트롤 사용 능력에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-152">Using your experimental feature should not impact people's ability to use core controls</span></span>

<span data-ttu-id="838d5-153">대부분의 사람들은 ManipulationHandler 및 Interactable 단추와 같은 핵심 UX 구성 요소를 매우 자주 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-153">Most people use core UX components like the button, ManipulationHandler and Interactable very frequently.</span></span> <span data-ttu-id="838d5-154">사용자가 단추를 사용 하지 못하도록 하는 경우 실험적 기능을 사용 하지 않을 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-154">They will likely not use your experimental feature if it prevents them from using buttons.</span></span>

<span data-ttu-id="838d5-155">구성 요소를 사용 하는 경우 ManipulationHandler, BoundingBox 또는 interactable 단추가 중단 되어서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-155">Using your component should not break buttons, ManipulationHandler, BoundingBox, or interactable.</span></span>

<span data-ttu-id="838d5-156">예를 들어 [이 SCROLLABLEOBJECTCOLLECTION PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)에서 ScrollableObjectCollection를 추가 하면 사용자가 HoloLens 단추 prefabs를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-156">For example, in [this ScrollableObjectCollection PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), adding a ScrollableObjectCollection caused people to not be able to use the HoloLens button prefabs.</span></span> <span data-ttu-id="838d5-157">PR의 버그로 인해 발생 하는 것은 아니지만 기존 버그를 노출 하는 경우에도 PR을 체크 인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-157">Even though this was not caused by a bug in the PR (but rather exposed an existing bug), it prevented the PR from getting checked in.</span></span>

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a><span data-ttu-id="838d5-158">기능을 사용 하는 방법을 보여 주는 예제 장면을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-158">Provide an example scene that demonstrates how to use the feature</span></span>

<span data-ttu-id="838d5-159">사용자는 기능을 사용 하는 방법 및 테스트 하는 방법을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-159">People need to see how to use your feature, and how to test it.</span></span>

<span data-ttu-id="838d5-160">MRTK/example/실험적/YOUR_FEATURE 아래에 예제를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-160">Provide an example under MRTK/Examples/Experimental/YOUR_FEATURE</span></span>

### <a name="minimize-user-visible-flaws-in-experimental-features"></a><span data-ttu-id="838d5-161">실험적 기능에서 사용자에 게 보이는 결함 최소화</span><span class="sxs-lookup"><span data-stu-id="838d5-161">Minimize user visible flaws in experimental features</span></span>

<span data-ttu-id="838d5-162">다른 사용자는 실험적 기능을 사용 하지 않는 경우 해당 기능을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-162">Others will not use the experimental feature if it does not work, it will not graduate to a feature.</span></span>

<span data-ttu-id="838d5-163">대상 플랫폼에서 예제 장면을 테스트 하 고 예상 대로 작동 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-163">Test your example scene on your target platform, make sure it works as expected.</span></span> <span data-ttu-id="838d5-164">기능이 편집기에서 작동 하는지 확인 하 여 대상 플랫폼이 없더라도 사용자가 신속 하 게 반복 하 고 기능을 볼 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-164">Make sure your feature also works in editor, so people can rapidly iterate and see your feature even if they don’t have the target platform.</span></span>

## <a name="graduating-experimental-code-into-mrtk-code"></a><span data-ttu-id="838d5-165">MRTK 코드에 실험적 코드 졸업</span><span class="sxs-lookup"><span data-stu-id="838d5-165">Graduating experimental code into MRTK code</span></span>

<span data-ttu-id="838d5-166">기능이 매우 많은 사용을 표시 하는 경우에는 핵심 MRTK 코드를 졸업 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-166">If a feature ends up seeing quite a lot of use, then we should graduate it into core MRTK code.</span></span> <span data-ttu-id="838d5-167">이렇게 하려면 기능에 테스트, 설명서 및 예제 장면이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-167">To do this, the feature should have tests, documentation, and an example scene.</span></span>

<span data-ttu-id="838d5-168">MRTK 기능을 졸업 할 준비가 되 면 PR에 대해 확인 하는 문제를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-168">When you are ready to graduate the feature MRTK, create an issue to check in your PR against.</span></span> <span data-ttu-id="838d5-169">PR은이를 핵심 기능으로 만드는 데 필요한 모든 항목을 포함 해야 합니다. 테스트, 설명서 및 사용법을 보여 주는 예제 장면.</span><span class="sxs-lookup"><span data-stu-id="838d5-169">The PR should include all the things needed to make this a core feature: tests, documentation, and an example scene showing usage.</span></span>

<span data-ttu-id="838d5-170">또한 "실험적" 하위 공간을 제거 하려면 네임 스페이스를 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838d5-170">Also, don’t forget to update the namespaces to remove the “Experimental” subspace.</span></span>
