---
title: 단위 테스트
description: 안정성의 MRTK를 확인 하는 테스트를 합니다.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 단위 테스트,
ms.openlocfilehash: 76d246634cf190787fcfd78c849a0bd6da3a2135
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144714"
---
# <a name="writing-and-running-tests-in-mrtk"></a>MRTK에서 테스트 작성 및 실행

MRTK가 안정적이 되도록 MRTK에는 코드의 변경으로 인해 기존 동작이 회귀 되지 않도록 하는 테스트 집합이 있습니다. MRTK와 같은 큰 코드 베이스에 좋은 테스트 검사가 있다면 안정성을 유지 하 고 변경할 때 자신감을 유지 하는 것이 중요 합니다.

MRTK는 [NUnit](https://nunit.org/)의 unity 통합을 사용 하는 [unity test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 를 사용 합니다. 이 가이드에서는 MRTK에 테스트를 추가 하는 방법에 대 한 시작점을 제공 합니다. 제공 된 링크에서 조회할 수 있는 [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 및 [NUnit](https://nunit.org/) 은 설명 하지 않습니다.

끌어오기 요청을 제출 하기 전에 다음을 확인 해야 합니다.

1. 변경 사항이 기존 동작을 회귀 하지 않도록 로컬에서 테스트를 실행 합니다. 테스트가 실패할 경우에는 Pr를 완료할 수 없습니다.

1. 버그를 수정 하는 경우에는 테스트를 작성 하 여 수정을 테스트 하 고 이후 코드 수정이 다시 중단 되지 않도록 합니다.

1. 기능을 작성 하는 경우 새 테스트를 작성 하 여 예정 된 코드 변경 내용이이 기능을 손상 시 키 지 않도록 합니다.

현재 playmode 테스트는 Unity 2018.4에서 실행 되며 다른 버전의 Unity에서 실패할 수 있습니다.

## <a name="running-tests"></a>테스트 실행

### <a name="unity-editor"></a>Unity 편집기

[Unity test runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 는 **Window**  >  **General**  >  **test runner** 에서 찾을 수 있으며 사용 가능한 mrtk 재생 및 편집 모드 테스트를 모두 표시 합니다.

### <a name="command-line"></a>명령 줄

에 있는 [powershell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) 스크립트를 통해 테스트를 실행할 수도 있습니다 `Scripts\test\run_playmode_tests.ps1` . 그러면 github/CI (아래 참조)에서 실행 되는 것과 동일 하 게 playmode 테스트가 실행 되 고 결과가 인쇄 됩니다. 스크립트를 실행 하는 방법에 대 한 몇 가지 예는 다음과 같습니다.

Unity 2018.4 (예: Unity 2018.4.26 f1)를 사용 하 여 H:\mrtk.dev에 있는 프로젝트에서 테스트를 실행 합니다.

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

Unity 2018.4를 사용 하 여 H:\mrtk.dev에 있는 프로젝트에서 테스트를 실행 하 고 결과를 C:\로 출력 playmode_test_out

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

스크립트를 통해 playmode 테스트를 여러 번 실행할 수도 있습니다 `run_repeat_tests.ps1` . 에 사용되는 모든 매개 `run_playmode_tests.ps1` 변수를 사용할 수 있습니다.

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a>끌어오기 요청 유효성 검사

MRTK의 CI는 모든 구성에서 MRTK를 빌드하고 모든 편집 및 재생 모드 테스트를 실행합니다. 사용자에게 충분한 권한이 있는 경우 Github PR에 댓글을 게시하여 CI를 트리거할 수 `/azp run mrtk_pr` 있습니다. CI 실행은 PR의 '검사' 탭에서 볼 수 있습니다.

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

MRTK play 모드 테스트는 새 기능이 실습 또는 눈동자와 같은 다른 입력 소스에 반응 하는 방식을 테스트 하는 기능을 제공 합니다.

새 재생 모드 테스트는 [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) 를 상속 하거나 아래를 사용할 수 있습니다.

새 재생 모드 테스트를 만들려면 다음을 수행 합니다.

* 자산 > MRTK > 테스트로 이동 > PlayModeTests
* 마우스 오른쪽 단추 클릭, > 테스트 만들기 > c # 테스트 스크립트
* 기본 템플릿을 아래 기본 템플릿으로 바꿉니다.

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

### <a name="edit-mode-tests"></a>편집 모드 테스트

편집 모드 테스트는 Unity의 편집 모드에서 실행 되며 혼합 현실 도구 키트 리포지토리의 **mrtk**  >  **테스트**  >  **EditModeTests** 폴더 아래에 추가할 수 있습니다.
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

일반적으로 테스트 하는 클래스 또는 테스트 하는 시나리오에 따라 테스트의 이름을 지정 해야 합니다.
예를 들어, 테스트를 거친 클래스가 있다고 가정 합니다.

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

테스트 이름 지정 고려

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

테스트를 해당 하는 비 테스트 파일과 비슷한 폴더 계층 구조에 배치 하는 것이 좋습니다.
예를 들면 다음과 같습니다.

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

이는 테스트 클래스가 있는 경우 각 클래스의 해당 테스트 클래스를 찾는 명확한 방법이 있는지 확인 하기 위한 것입니다.

시나리오 기반 테스트 배치가 정의 되어 있지 않습니다. 테스트에서 전체 입력 시스템을 실행 하는 경우, 예를 들어 해당 편집 모드 또는 재생 모드 테스트 폴더의 "InputSystem" 폴더에 저장 하는 것이 좋습니다.

### <a name="test-script-icons"></a>테스트 스크립트 아이콘

새 테스트를 추가 하는 경우 올바른 MRTK 아이콘을 포함 하도록 스크립트를 수정 하세요. 이 작업을 수행 하는 쉬운 MRTK 도구는 다음과 같습니다.

1. 혼합 현실 도구 키트 메뉴 항목으로 이동
1. 유틸리티, 업데이트, 아이콘을 차례로 클릭 합니다.
1. 테스트를 클릭 하면 업데이트 프로그램이 자동으로 실행 되어 해당 아이콘이 없는 모든 테스트 스크립트를 업데이트 합니다.

### <a name="mrtk-utility-methods"></a>MRTK 유틸리티 메서드

이 섹션에서는 MRTK에 대 한 테스트를 작성할 때 일반적으로 사용 되는 코드 조각/메서드 중 일부를 보여 줍니다.

MRTK를 설정 하 고 MRTK의 구성 요소와의 상호 작용을 테스트 하는 데 도움이 되는 두 가지 유틸리티 클래스가 있습니다.

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

TestUtilities는 MRTK 장면 및 Gameobject를 설정 하는 다음과 같은 방법을 제공 합니다.

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

[`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) 새 테스트가 MRTK에 추가 되는 동안에는 및의 API 문서를 참조 하 여 이러한 util 클래스의 추가 메서드를 정기적으로 확장 하 고 있습니다.