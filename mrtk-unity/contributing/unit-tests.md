---
title: UnitTests
description: MRTK의 별칭을 확인하는 UnitTests입니다.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, UnitTest,
ms.openlocfilehash: 51a485ff258ceafb8841ff1b86e715b1623f3255
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489243"
---
# <a name="writing-and-running-tests-in-mrtk"></a><span data-ttu-id="fc073-104">MRTK에서 테스트 작성 및 실행</span><span class="sxs-lookup"><span data-stu-id="fc073-104">Writing and running tests in MRTK</span></span>

<span data-ttu-id="fc073-105">MRTK의 안정성을 보장하기 위해 MRTK에는 코드 변경 내용이 기존 동작을 회귀하지 않는지 확인하는 일련의 테스트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-105">To ensure MRTK is reliable, MRTK has a set of tests to ensure that changes to the code does not regress existing behavior.</span></span> <span data-ttu-id="fc073-106">MRTK와 같은 큰 코드베이스에서 테스트 검사를 잘 하는 것은 안정성과 변경 시 신뢰도에 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-106">Having good test coverage in a big codebase like MRTK is crucial for stability and having confidence when making changes.</span></span>

<span data-ttu-id="fc073-107">MRTK는 [NUnit](https://nunit.org/)의 Unity 통합을 사용하는 Unity [Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-107">MRTK uses the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) which uses a Unity integration of [NUnit](https://nunit.org/).</span></span> <span data-ttu-id="fc073-108">이 가이드에서는 MRTK에 테스트를 추가하는 방법에 대한 시작점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-108">This guide will provide a starting point on how to add tests to MRTK.</span></span> <span data-ttu-id="fc073-109">제공된 링크에서 조회할 수 있는 [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 및 [NUnit은](https://nunit.org/) 설명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-109">It will not explain the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) and [NUnit](https://nunit.org/) which can be looked up in the links provided.</span></span>

<span data-ttu-id="fc073-110">끌어오기 요청을 제출하기 전에 다음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-110">Before submitting a pull request, make sure to:</span></span>

1. <span data-ttu-id="fc073-111">변경 내용이 기존 동작을 회귀하지 않도록 테스트를 로컬로 실행합니다(테스트가 실패하는 경우 PR 완료가 허용되지 않습니다).</span><span class="sxs-lookup"><span data-stu-id="fc073-111">Run the tests locally so your changes don't regress existing behavior (completing PRs won't be allowed if any tests fail).</span></span>

1. <span data-ttu-id="fc073-112">버그를 수정하는 경우 테스트를 작성하여 수정 사항을 테스트하고 향후 코드 수정으로 다시 중단되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-112">If fixing a bug, write a test to test the fix and ensure that future code modifications won't break it again.</span></span>

1. <span data-ttu-id="fc073-113">기능을 작성하는 경우 새 테스트를 작성하여 예정된 코드 변경으로 인해 이 기능이 중단되는 것을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-113">If writing a feature, write new tests to prevent upcoming code changes breaking this feature.</span></span>

<span data-ttu-id="fc073-114">현재 playmode 테스트는 Unity 2018.4에서 실행되며 다른 버전의 Unity에서 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-114">Currently playmode tests are meant to be run in Unity 2018.4 and may fail in other versions of Unity</span></span>

## <a name="running-tests"></a><span data-ttu-id="fc073-115">테스트 실행</span><span class="sxs-lookup"><span data-stu-id="fc073-115">Running tests</span></span>

### <a name="unity-editor"></a><span data-ttu-id="fc073-116">Unity 편집기</span><span class="sxs-lookup"><span data-stu-id="fc073-116">Unity editor</span></span>

<span data-ttu-id="fc073-117">[Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) **창** 일반 Test Runner 있으며 사용 가능한 모든  >    >   MRTK 재생 및 편집 모드 테스트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-117">The [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) can be found under **Window** > **General** > **Test Runner** and will show all available MRTK play and edit mode tests.</span></span>

### <a name="command-line"></a><span data-ttu-id="fc073-118">명령줄</span><span class="sxs-lookup"><span data-stu-id="fc073-118">Command line</span></span>

<span data-ttu-id="fc073-119">에 있는 [powershell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) 스크립트를 통해 테스트를 실행할 수도 `Scripts\test\run_playmode_tests.ps1` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-119">Tests can also be run by a [powershell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) script located at `Scripts\test\run_playmode_tests.ps1`.</span></span> <span data-ttu-id="fc073-120">그러면 playmode 테스트가 github/CI에서 실행되는 대로 정확하게 실행되고(아래 참조) 결과를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-120">This will run the playmode tests exactly as they are executed on github / CI (see below), and print results.</span></span> <span data-ttu-id="fc073-121">다음은 스크립트를 실행하는 방법의 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-121">Here are some examples of how to run the script</span></span>

<span data-ttu-id="fc073-122">Unity 2018.4(예: Unity 2018.4.26f1)를 통해 H:\mrtk.dev 있는 프로젝트에서 테스트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-122">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4 (for example Unity 2018.4.26f1)</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

<span data-ttu-id="fc073-123">Unity 2018.4를 사용하여 H:\mrtk.dev 있는 프로젝트에서 테스트를 실행하여 결과를 C:\playmode_test_out</span><span class="sxs-lookup"><span data-stu-id="fc073-123">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4, output results to C:\playmode_test_out</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

<span data-ttu-id="fc073-124">스크립트를 통해 playmode 테스트를 여러 번 실행할 수도 `run_repeat_tests.ps1` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-124">It's also possible to run the playmode tests multiple times via the `run_repeat_tests.ps1` script.</span></span> <span data-ttu-id="fc073-125">에서 사용 되는 모든 매개 변수를 `run_playmode_tests.ps1` 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-125">All parameters used in `run_playmode_tests.ps1` may be used.</span></span>

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a><span data-ttu-id="fc073-126">끌어오기 요청 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="fc073-126">Pull request validation</span></span>

<span data-ttu-id="fc073-127">MRTK의 CI는 모든 구성에서 MRTK를 빌드하고 모든 편집 및 재생 모드 테스트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-127">MRTK's CI will build MRTK in all configurations and run all edit and play mode tests.</span></span> <span data-ttu-id="fc073-128">`/azp run mrtk_pr`사용자에 게 충분 한 권한이 있는 경우 GITHUB PR에 주석을 게시 하 여 CI를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-128">CI can be triggered by posting a comment on the github PR `/azp run mrtk_pr` if the user has sufficient rights.</span></span> <span data-ttu-id="fc073-129">CI 실행은 PR의 ' 검사 ' 탭에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-129">CI runs can be seen in the 'checks' tab of the PR.</span></span>

<span data-ttu-id="fc073-130">모든 테스트를 성공적으로 통과 한 후에만 PR을 main에 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-130">Only after all of the tests have passed successfully can the PR be merged into main.</span></span>

### <a name="stress-tests--bulk-tests"></a><span data-ttu-id="fc073-131">스트레스 테스트/대량 테스트</span><span class="sxs-lookup"><span data-stu-id="fc073-131">Stress tests / bulk tests</span></span>

<span data-ttu-id="fc073-132">때로는 테스트가 가끔 실패 하 여 디버깅 하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-132">Sometimes tests will only fail occasionally which can be frustrating to debug.</span></span>

<span data-ttu-id="fc073-133">여러 테스트를 로컬로 실행 하려면 해당 하는 테스트 스크립트를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-133">To have multiple test runs locally, modify the according test scripts.</span></span> <span data-ttu-id="fc073-134">다음 python 스크립트는이 시나리오를 더 편리 하 게 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-134">The following python script should make this scenario more convenient.</span></span>

<span data-ttu-id="fc073-135">Python 스크립트를 실행 하기 위한 필수 구성 요소에는 Python 3.x이 [설치](https://www.python.org/downloads/)되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-135">Prerequisite for running the python script is having [Python 3.X installed](https://www.python.org/downloads/).</span></span>

<span data-ttu-id="fc073-136">여러 번 실행 해야 하는 단일 테스트:</span><span class="sxs-lookup"><span data-stu-id="fc073-136">For a single test that needs to be executed multiple times:</span></span>

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="fc073-137">명령줄에서 다음을 실행 합니다 ([PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) 권장).</span><span class="sxs-lookup"><span data-stu-id="fc073-137">Run the following from a command line ([PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) is recommended)</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

<span data-ttu-id="fc073-138">출력을 복사 하 여 테스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-138">Copy and paste the output into your test file.</span></span> <span data-ttu-id="fc073-139">다음 스크립트는 여러 테스트를 차례로 실행 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-139">The following script is for running multiple tests in sequence:</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

<span data-ttu-id="fc073-140">새 테스트 파일에는 다음이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-140">The new test file should now contain</span></span>

```c#
[UnityTest]
public IEnumerator A1MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A2MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A3MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A4MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="fc073-141">Test runner를 열고 이제 반복적으로 호출할 수 있는 새 테스트를 관찰 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-141">Open the test runner and observe the new tests that can now be called repeatedly.</span></span>

## <a name="writing-tests"></a><span data-ttu-id="fc073-142">테스트 작성</span><span class="sxs-lookup"><span data-stu-id="fc073-142">Writing tests</span></span>

<span data-ttu-id="fc073-143">새 코드에는 두 가지 유형의 테스트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-143">There are two types of tests that can be added for new code</span></span>

* <span data-ttu-id="fc073-144">재생 모드 테스트</span><span class="sxs-lookup"><span data-stu-id="fc073-144">Play mode tests</span></span>
* <span data-ttu-id="fc073-145">모드 테스트 편집</span><span class="sxs-lookup"><span data-stu-id="fc073-145">Edit mode tests</span></span>

### <a name="play-mode-tests"></a><span data-ttu-id="fc073-146">재생 모드 테스트</span><span class="sxs-lookup"><span data-stu-id="fc073-146">Play mode tests</span></span>

<span data-ttu-id="fc073-147">MRTK 재생 모드 테스트에는 새 기능이 손이나 눈과 같은 다양한 입력 소스에 응답하는 방법을 테스트하는 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-147">MRTK play mode tests have the ability to test how your new feature responds to different input sources such as hands or eyes.</span></span>

<span data-ttu-id="fc073-148">새 재생 모드 테스트는 [BasePlayModeTests를](xref:Microsoft.MixedReality.Toolkit.Tests) 상속하거나 아래의 기본을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-148">New play mode tests can inherit [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) or the skeleton below can be used.</span></span>

<span data-ttu-id="fc073-149">새 재생 모드 테스트를 만들려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-149">To create a new play mode test:</span></span>

* <span data-ttu-id="fc073-150">자산 > MRTK > 테스트 > PlayModeTests로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-150">Navigate to Assets > MRTK > Tests > PlayModeTests</span></span>
* <span data-ttu-id="fc073-151">마우스 오른쪽 단추로 클릭하고 C# 테스트 스크립트를 > > 테스트 만들기</span><span class="sxs-lookup"><span data-stu-id="fc073-151">Right click, Create > Testing > C# Test Script</span></span>
* <span data-ttu-id="fc073-152">기본 템플릿을 아래 구조로 바꾸기</span><span class="sxs-lookup"><span data-stu-id="fc073-152">Replace the default template with the skeleton below</span></span>

```c#
#if !WINDOWS_UWP
// When the .NET scripting backend is enabled and C# projects are built
// The assembly that this file is part of is still built for the player,
// even though the assembly itself is marked as a test assembly (this is not
// expected because test assemblies should not be included in player builds).
// Because the .NET backend is deprecated in 2018 and removed in 2019 and this
// issue will likely persist for 2018, this issue is worked around by wrapping all
// play mode tests in this check.

using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using NUnit.Framework;
using System;
using System.Collections;
using System.Linq;
using UnityEngine;
using UnityEngine.TestTools;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class ExamplePlayModeTests
    {
        // This method is called once before we enter play mode and execute any of the tests
        // do any kind of setup here that can't be done in playmode
        public void Setup()
        {
            // eg installing unity packages is only possible in edit mode
            // so if a test requires TextMeshPro we will need to check for the package before entering play mode
            PlayModeTestUtilities.InstallTextMeshProEssentials();
        }

        // Do common setup for each of your tests here - this will be called for each individual test after entering playmode
        // Note that this uses UnitySetUp instead of [SetUp] because the init function needs to await a frame passing
        // to ensure that the MRTK system has had the chance to fully set up before the test runs.
        [UnitySetUp]
        public IEnumerator Init()
        {
            // in most play mode test cases you would want to at least create an MRTK GameObject using the default profile
            TestUtilities.InitializeMixedRealityToolkit(true);
            yield return null;
        }

        // Destroy the scene - this method is called after each test listed below has completed
        // Note that this uses UnityTearDown instead of [TearDown] because the init function needs to await a frame passing
        // to ensure that the MRTK system has fully torn down before the next test setup->run cycle starts.
        [UnityTearDown]
        public IEnumerator TearDown()
        {
            PlayModeTestUtilities.TearDown();
            yield return null;
        }

        #region Tests

        /// <summary>
        /// Skeleton for a new MRTK play mode test.
        /// </summary>
        [UnityTest]
        public IEnumerator TestMyFeature()
        {
            // ----------------------------------------------------------
            // EXAMPLE PLAY MODE TEST METHODS
            // ----------------------------------------------------------
            // Getting the input system
            // var inputSystem = PlayModeTestUtilities.GetInputSystem();

            // Creating a new test hand for input
            // var rightHand = new TestHand(Handedness.Right);
            // yield return rightHand.Show(new Vector3(0, 0, 0.5f));

            // Moving the new test hand
            // We are doing a yield return here because moving the hand to a new position
            // requires multiple frames to complete the action.
            // yield return rightHand.MoveTo(new Vector3(0, 0, 2.0f));

            // Getting a specific pointer from the hand
            // var linePointer = PointerUtils.GetPointer<LinePointer>(Handedness.Right);
            // Assert.IsNotNull(linePointer);
            // ---------------------------------------------------------

            // Your new test here
            yield return null;
        }
        #endregion
    }
}
#endif
```

### <a name="edit-mode-tests"></a><span data-ttu-id="fc073-153">모드 테스트 편집</span><span class="sxs-lookup"><span data-stu-id="fc073-153">Edit mode tests</span></span>

<span data-ttu-id="fc073-154">편집 모드 테스트는 Unity의 편집 모드에서 실행되며 Mixed Reality Toolkit 리포지션의 **MRTK**  >  **테스트**  >  **EditModeTests** 폴더 아래에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-154">Edit mode tests are executed in Unity's edit mode and can be added under the **MRTK** > **Tests** > **EditModeTests** folder in the Mixed Reality Toolkit repo.</span></span>
<span data-ttu-id="fc073-155">새 테스트를 만들려면 다음 템플릿을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-155">To create a new test the following template can be used:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.

using NUnit.Framework;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class EditModeExampleTest
    {
        [Test]
        /// the name of this method will be used as test name in the unity test runner
        public void TestEditModeExampleFeature()
        {

        }
    }
}
```

### <a name="test-naming-conventions"></a><span data-ttu-id="fc073-156">테스트 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="fc073-156">Test naming conventions</span></span>

<span data-ttu-id="fc073-157">테스트는 일반적으로 테스트하는 클래스 또는 테스트 중인 시나리오에 따라 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-157">Tests should generally be named based on the class they are testing, or the scenario that they are testing.</span></span>
<span data-ttu-id="fc073-158">예를 들어 테스트할 클래스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-158">For example, given a to-be-tested class:</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

<span data-ttu-id="fc073-159">테스트 이름을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-159">Consider naming the test</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

<span data-ttu-id="fc073-160">테스트가 아닌 해당 파일과 유사한 폴더 계층 구조에 테스트를 배치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-160">Consider placing the test in a folder hierarchy that is similar to its corresponding non-test file.</span></span>
<span data-ttu-id="fc073-161">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="fc073-161">For example:</span></span>

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

<span data-ttu-id="fc073-162">이는 이러한 테스트 클래스가 있는 경우 각 클래스의 해당 테스트 클래스를 찾는 명확한 방법이 있는지 확인하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-162">This is to ensure that there's a clear an obvious way of finding each class's corresponding test class, if such a test class exists.</span></span>

<span data-ttu-id="fc073-163">시나리오 기반 테스트 배치는 덜 정의됩니다. 예를 들어 테스트가 전체 입력 시스템을 연습하는 경우 해당 편집 모드 또는 재생 모드 테스트 폴더의 "InputSystem" 폴더에 배치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-163">Placement of scenario based tests is less defined - if the test exercises the overall input system, for example, consider putting it into an "InputSystem" folder in the corresponding edit mode or play mode test folder.</span></span>

### <a name="test-script-icons"></a><span data-ttu-id="fc073-164">테스트 스크립트 아이콘</span><span class="sxs-lookup"><span data-stu-id="fc073-164">Test script icons</span></span>

<span data-ttu-id="fc073-165">새 테스트를 추가할 때 올바른 MRTK 아이콘을 갖도록 스크립트를 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="fc073-165">When adding a new test, please modify the script to have the correct MRTK icon.</span></span> <span data-ttu-id="fc073-166">이 작업을 수행 하는 쉬운 MRTK 도구는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-166">There's an easy MRTK tool to do so:</span></span>

1. <span data-ttu-id="fc073-167">혼합 현실 도구 키트 메뉴 항목으로 이동</span><span class="sxs-lookup"><span data-stu-id="fc073-167">Go go the Mixed Reality Toolkit menu item</span></span>
1. <span data-ttu-id="fc073-168">유틸리티, 업데이트, 아이콘을 차례로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-168">Click on Utilities, then Update, then Icons</span></span>
1. <span data-ttu-id="fc073-169">테스트를 클릭 하면 업데이트 프로그램이 자동으로 실행 되어 해당 아이콘이 없는 모든 테스트 스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-169">Click on Tests, and the updater will run automatically, updating any test scripts missing their icons</span></span>

### <a name="mrtk-utility-methods"></a><span data-ttu-id="fc073-170">MRTK 유틸리티 메서드</span><span class="sxs-lookup"><span data-stu-id="fc073-170">MRTK Utility methods</span></span>

<span data-ttu-id="fc073-171">이 섹션에서는 MRTK에 대 한 테스트를 작성할 때 일반적으로 사용 되는 코드 조각/메서드 중 일부를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-171">This section shows some of the commonly used code snippets / methods when writing tests for MRTK.</span></span>

<span data-ttu-id="fc073-172">MRTK를 설정 하 고 MRTK의 구성 요소와의 상호 작용을 테스트 하는 데 도움이 되는 두 가지 유틸리티 클래스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-172">There are two Utility classes that help with setting up MRTK and testing interactions with components in MRTK</span></span>

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

<span data-ttu-id="fc073-173">TestUtilities는 MRTK 장면 및 Gameobject를 설정 하는 다음과 같은 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-173">TestUtilities provide the following methods to set up your MRTK scene and GameObjects:</span></span>

```c#
/// creates the mrtk GameObject and sets the default profile if passed param is true
TestUtilities.InitializeMixedRealityToolkit()

/// creates an empty scene prior to adding the mrtk GameObject to it
TestUtilities.InitializeMixedRealityToolkitAndCreateScenes();

/// sets the initial playspace transform and camera position
TestUtilities.InitializePlayspace();

/// destroys previously created mrtk GameObject and playspace
TestUtilities.ShutdownMixedRealityToolkit();
```

<span data-ttu-id="fc073-174">[`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) 새 테스트가 MRTK에 추가 되는 동안에는 및의 API 문서를 참조 하 여 이러한 util 클래스의 추가 메서드를 정기적으로 확장 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc073-174">Please refer to the API docs of [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) and [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) for further methods of these util classes as they're extended on a regular basis while new tests get added to MRTK.</span></span>