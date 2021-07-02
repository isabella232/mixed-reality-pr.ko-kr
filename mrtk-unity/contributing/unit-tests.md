---
title: 테스트 작성 및 실행
description: MRTK의 안정성을 확인하기 위한 단위 테스트입니다.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, UnitTest,
ms.openlocfilehash: c8efb192982a1cb9ca07e91d29a69b11aaffc290
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177114"
---
# <a name="writing-and-running-tests"></a>테스트 작성 및 실행

MRTK의 안정성을 보장하기 위해 MRTK에는 코드 변경 내용이 기존 동작을 회귀하지 않도록 하는 일련의 테스트가 있습니다. MRTK와 같은 큰 코드베이스에서 테스트 검사를 잘 하는 것은 안정성과 변경 시 신뢰도에 매우 중요합니다.

MRTK는 [NUnit의](https://nunit.org/)Unity 통합을 사용하는 Unity [Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 사용합니다. 이 가이드에서는 MRTK에 테스트를 추가하는 방법에 대한 시작점을 제공합니다. 제공된 링크에서 조회할 수 있는 [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 및 [NUnit은](https://nunit.org/) 설명하지 않습니다.

끌어오기 요청을 제출하기 전에 다음을 확인합니다.

1. 변경 내용이 기존 동작을 회귀하지 않도록 테스트를 로컬로 실행합니다(테스트가 실패하는 경우 PR 완료가 허용되지 않습니다).

1. 버그를 수정하는 경우 테스트를 작성하여 수정 사항을 테스트하고 향후 코드 수정으로 다시 중단되지 않도록 합니다.

1. 기능을 작성하는 경우 새 테스트를 작성하여 예정된 코드 변경으로 인해 이 기능이 중단되는 것을 방지합니다.

현재 playmode 테스트는 Unity 2018.4에서 실행되며 다른 버전의 Unity에서 실패할 수 있습니다.

## <a name="running-tests"></a>테스트 실행

### <a name="unity-editor"></a>Unity 편집기

[Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) **창** 일반 Test Runner 있으며 사용 가능한 모든  >    >   MRTK 재생 및 편집 모드 테스트를 표시합니다.

### <a name="command-line"></a>명령 줄

에 있는 [powershell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) 스크립트를 통해 테스트를 실행할 수도 `Scripts\test\run_playmode_tests.ps1` 있습니다. 그러면 playmode 테스트가 github/CI에서 실행되는 대로 정확하게 실행되고(아래 참조) 결과를 출력합니다. 다음은 스크립트를 실행하는 방법의 몇 가지 예입니다.

Unity 2018.4(예: Unity 2018.4.26f1)를 통해 H:\mrtk.dev 있는 프로젝트에서 테스트를 실행합니다.

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

Unity 2018.4를 사용하여 H:\mrtk.dev 있는 프로젝트에서 테스트를 실행하여 결과를 C:\playmode_test_out

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

스크립트를 통해 playmode 테스트를 여러 번 실행할 수도 `run_repeat_tests.ps1` 있습니다. 에 사용되는 모든 매개 `run_playmode_tests.ps1` 변수를 사용할 수 있습니다.

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a>끌어오기 요청 유효성 검사

MRTK의 CI는 모든 구성에서 MRTK를 빌드하고 모든 편집 및 재생 모드 테스트를 실행합니다. 사용자에게 충분한 권한이 있는 경우 Github PR에 주석을 게시하여 CI를 트리거할 수 `/azp run mrtk_pr` 있습니다. CI 실행은 PR의 '검사' 탭에서 볼 수 있습니다.

모든 테스트가 성공적으로 통과된 후에만 PR을 main에 병합할 수 있습니다.

### <a name="stress-tests--bulk-tests"></a>스트레스 테스트/대량 테스트

경우에 따라 테스트가 가끔씩만 실패하여 디버그하는 것이 어려울 수 있습니다.

여러 테스트를 로컬로 실행하려면 테스트 스크립트에 따라 를 수정합니다. 다음 Python 스크립트를 통해 이 시나리오를 더 편리하게 만들 수 있습니다.

Python 스크립트를 실행하기 위한 필수 구성 요소에는 [Python 3.X가 설치되어 있습니다.](https://www.python.org/downloads/)

여러 번 실행해야 하는 단일 테스트의 경우:

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

명령줄에서 다음을[실행합니다(PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) 권장).

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

출력을 복사하여 테스트 파일에 붙여넣습니다. 다음 스크립트는 여러 테스트를 순서대로 실행하기 위한 것입니다.

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

이제 새 테스트 파일에 포함해야 합니다.

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

Test Runner를 열고 이제 반복적으로 호출할 수 있는 새 테스트를 관찰합니다.

## <a name="writing-tests"></a>테스트 작성

새 코드에 대해 추가할 수 있는 테스트에는 두 가지 유형이 있습니다.

* 재생 모드 테스트
* 모드 테스트 편집

### <a name="play-mode-tests"></a>재생 모드 테스트

MRTK 재생 모드 테스트에는 새 기능이 손이나 눈과 같은 다양한 입력 소스에 응답하는 방법을 테스트하는 기능이 있습니다.

새 재생 모드 테스트는 [BasePlayModeTests를](xref:Microsoft.MixedReality.Toolkit.Tests) 상속하거나 아래의 기본을 사용할 수 있습니다.

새 재생 모드 테스트를 만들려면 다음을 수행합니다.

* 자산 > MRTK > 테스트 > PlayModeTests로 이동합니다.
* 마우스 오른쪽 단추로 클릭하고 > 테스트 > C# 테스트 스크립트 만들기
* 기본 템플릿을 아래 구조로 바꾸기

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

### <a name="edit-mode-tests"></a>모드 테스트 편집

편집 모드 테스트는 Unity의 편집 모드에서 실행되며 Mixed Reality Toolkit 리포지온의 **MRTK**  >  **테스트**  >  **EditModeTests** 폴더 아래에 추가할 수 있습니다.
새 테스트를 만들려면 다음 템플릿을 사용할 수 있습니다.

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

### <a name="test-naming-conventions"></a>테스트 명명 규칙

테스트는 일반적으로 테스트하는 클래스 또는 테스트 중인 시나리오에 따라 이름을 지정해야 합니다.
예를 들어 테스트할 클래스를 지정합니다.

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

테스트 이름을 지정하는 것이 좋습니다.

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

테스트가 아닌 해당 파일과 유사한 폴더 계층 구조에 테스트를 배치하는 것이 좋습니다.
예를 들어:

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

이는 이러한 테스트 클래스가 있는 경우 각 클래스의 해당 테스트 클래스를 찾는 명확한 방법이 있는지 확인하기 위한 것입니다.

시나리오 기반 테스트 배치는 덜 정의됩니다. 예를 들어 테스트가 전체 입력 시스템을 연습하는 경우 해당 편집 모드 또는 재생 모드 테스트 폴더의 "InputSystem" 폴더에 배치하는 것이 좋습니다.

### <a name="test-script-icons"></a>테스트 스크립트 아이콘

새 테스트를 추가할 때 올바른 MRTK 아이콘을 갖도록 스크립트를 수정하세요. 이렇게 하기 쉬운 MRTK 도구가 있습니다.

1. Mixed Reality Toolkit 메뉴 항목으로 이동합니다.
1. 유틸리티, 업데이트, 아이콘을 차례로 클릭합니다.
1. 테스트를 클릭하면 업데이트가 자동으로 실행되어 아이콘이 누락된 테스트 스크립트가 업데이트됩니다.

### <a name="mrtk-utility-methods"></a>MRTK 유틸리티 메서드

이 섹션에서는 MRTK에 대한 테스트를 작성할 때 일반적으로 사용되는 코드 조각/메서드 중 일부를 보여줍니다.

MRTK를 설정하고 MRTK의 구성 요소와의 상호 작용을 테스트하는 데 도움이 되는 두 가지 유틸리티 클래스가 있습니다.

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

TestUtilities는 MRTK 장면 및 GameObjects를 설정하는 다음 메서드를 제공합니다.

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

[`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) 새 테스트가 MRTK에 추가된 동안 정기적으로 확장됨에 따라 이러한 유틸리티 클래스의 추가 메서드는 및 의 API 문서를 참조하세요.
