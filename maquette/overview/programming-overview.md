---
title: 프로그래밍 개요
description: 스크립팅을 사용 하 여 Maquette 개체 및 인터페이스에 액세스 하는 방법을 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, 프로토타입, 혼합 현실, 가상 현실, VR, MR, 피드백, 피드백 허브, 버그
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935605"
---
# <a name="programming-overview"></a><span data-ttu-id="d27ce-104">프로그래밍 개요</span><span class="sxs-lookup"><span data-stu-id="d27ce-104">Programming overview</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->

![로고](../images/MaquetteIcon.png) <span data-ttu-id="d27ce-106">프로그래밍 개요</span><span class="sxs-lookup"><span data-stu-id="d27ce-106">Programming Overview</span></span>

<span data-ttu-id="d27ce-107">Microsoft Maquette는 [Jint](https://github.com/sebastienros/jint) 인터프리터에 따라 JavaScript (확장에 ECMAScript 5.1)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-107">Microsoft Maquette uses JavaScript (ECMAScript 5.1 with extensions) based on the [Jint](https://github.com/sebastienros/jint) interpreter.</span></span> <span data-ttu-id="d27ce-108">확장은 `.mqjs` 일반 javascript에서 Maquette javascript 파일을 구분 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-108">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
<span data-ttu-id="d27ce-109">Maquette 개체 및 인터페이스는 개체를 통해 액세스 하 고 스크립팅할 수 있습니다 `Maquette` .</span><span class="sxs-lookup"><span data-stu-id="d27ce-109">Maquette objects and interfaces are accessible and scriptable via the `Maquette` Object.</span></span> <span data-ttu-id="d27ce-110">Maquette 개체 및 인터페이스에 대 한 설명서는 Maquette의 API 참조에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-110">Documentation on Maquette Objects and interfaces are provided in Maquette's API Reference.</span></span>

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
<span data-ttu-id="d27ce-111">MaquetteScript는 새로운 추가 및 flux 이므로 변경이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-111">MaquetteScript is a new addition and in flux so changes should be expected.</span></span> <span data-ttu-id="d27ce-112">더 자세한 설명서와 업데이트가 곧 제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-112">More detailed documentation and updates available soon.</span></span>

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a><span data-ttu-id="d27ce-113">스크립팅에 집중</span><span class="sxs-lookup"><span data-stu-id="d27ce-113">Spotlights on Scripting</span></span>

* <span data-ttu-id="d27ce-114">TBD-샘플/자습서로 포커스가 있는 스크립팅 집중</span><span class="sxs-lookup"><span data-stu-id="d27ce-114">TBD - Scripting Spotlights focused as Samples/Tutorials</span></span>
  * <span data-ttu-id="d27ce-115">2x 이미지/캡션 – 스포트라이트 페이지에 연결</span><span class="sxs-lookup"><span data-stu-id="d27ce-115">2x Images/Caption – link to spotlight page</span></span>

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a><span data-ttu-id="d27ce-116">MaquetteScript 시작 하기</span><span class="sxs-lookup"><span data-stu-id="d27ce-116">Getting started with MaquetteScript</span></span>

* <span data-ttu-id="d27ce-117">Mqjs 및 .JS</span><span class="sxs-lookup"><span data-stu-id="d27ce-117">Mqjs vs. JS</span></span>
* <span data-ttu-id="d27ce-118">프로그래밍 모델</span><span class="sxs-lookup"><span data-stu-id="d27ce-118">Programming Model</span></span>
  * <span data-ttu-id="d27ce-119">편집 및 실행 중</span><span class="sxs-lookup"><span data-stu-id="d27ce-119">Editing vs. Running</span></span>
* <span data-ttu-id="d27ce-120">프로그래밍 워크플로 링크</span><span class="sxs-lookup"><span data-stu-id="d27ce-120">Link to Programming Workflow</span></span>
* <span data-ttu-id="d27ce-121">공유 결과에 대 한 링크</span><span class="sxs-lookup"><span data-stu-id="d27ce-121">Link to Sharing Results</span></span>

## <a name="programming-workflow"></a><span data-ttu-id="d27ce-122">프로그래밍 워크플로</span><span class="sxs-lookup"><span data-stu-id="d27ce-122">Programming workflow</span></span>

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
<span data-ttu-id="d27ce-123">TBD</span><span class="sxs-lookup"><span data-stu-id="d27ce-123">TBD</span></span>
* <span data-ttu-id="d27ce-124">REPL</span><span class="sxs-lookup"><span data-stu-id="d27ce-124">REPL</span></span>
* <span data-ttu-id="d27ce-125">스크립팅 작업</span><span class="sxs-lookup"><span data-stu-id="d27ce-125">Scripting operation</span></span>
* <span data-ttu-id="d27ce-126">디버거 작업</span><span class="sxs-lookup"><span data-stu-id="d27ce-126">Debugger operation</span></span>
* <span data-ttu-id="d27ce-127">디버깅 루프</span><span class="sxs-lookup"><span data-stu-id="d27ce-127">Debugging loop</span></span>
* <span data-ttu-id="d27ce-128">코드를 복사 하 여 붙여 넣으 시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="d27ce-128">Copy/Paste of code?</span></span>

## <a name="running-mqjs-scripts"></a><span data-ttu-id="d27ce-129">Mqjs 스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="d27ce-129">Running .mqjs scripts</span></span>

<!-- TODO(Stefan): Need screenshot -->
<span data-ttu-id="d27ce-130">MaquetteScript 파일을 실행 하려면 Maquette의 부록 창으로 이동 하 여 스크립팅 탭을 열고 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-130">To run a MaquetteScript .mqjs file, go to the companion windows of Maquette and open the scripting tab to locate scripts.</span></span>

> [!NOTE] 
> <span data-ttu-id="d27ce-131">일부 옵션은 스크립트를 제공 하지 않았으므로 아직 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-131">Some options will not work yet because we have not ship the scripts.</span></span>

## <a name="vscode-editor-workflow"></a><span data-ttu-id="d27ce-132">VSCode 편집기 워크플로</span><span class="sxs-lookup"><span data-stu-id="d27ce-132">VSCode Editor Workflow</span></span>

<span data-ttu-id="d27ce-133">VSCode 내에서 Maquette의 스크립트를 평가 하려면 사용자가 두 가지 명령을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-133">To evaluate script in Maquette from within VSCode, the user needs to know two commands:</span></span>

   <span data-ttu-id="d27ce-134">`CTRL-5` 선택한 텍스트 또는 커서가 있는 전체 줄을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-134">`CTRL-5` evaluates the selected text or the entire line where the cursor is located.</span></span> 

   <span data-ttu-id="d27ce-135">`CTRL-SHIFT-5` 전체 파일을 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-135">`CTRL-SHIFT-5` evaluates the entire file.</span></span>

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
<span data-ttu-id="d27ce-136">텍스트는 JavaScript 환경에서 계산 되는 Maquette로 전송 되며, 결과는 VSCode의 출력 콘솔로 다시 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-136">Text is sent to Maquette, evaluated in the JavaScript environment, and the result is sent back to the output console of VSCode.</span></span> <span data-ttu-id="d27ce-137">이를 REPL (읽기-평가-인쇄-루프)으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-137">This can be used as a REPL (read-eval-print-loop).</span></span>

## <a name="example-first-step"></a><span data-ttu-id="d27ce-138">예제 첫 번째 단계</span><span class="sxs-lookup"><span data-stu-id="d27ce-138">Example First Step</span></span>

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
<span data-ttu-id="d27ce-139">VSCode의 파일에 다음 코드를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-139">Copy the following code into a file in VSCode:</span></span>

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
<span data-ttu-id="d27ce-140">코드 또는 섹션을 선택 하 고 `CTRL-5` 실행 하도록 적중 합니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-140">Select the code or just sections and hit `CTRL-5` to execute.</span></span> <span data-ttu-id="d27ce-141">이렇게 하면 큐브가 생성 되 고 앞에 놓고 색이 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-141">This should create a cube, place it in front of you and change its color.</span></span>

<span data-ttu-id="d27ce-142">확장을 통해 더 많은 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-142">There are more examples to find through the extension.</span></span>

## <a name="sharing-results"></a><span data-ttu-id="d27ce-143">결과 공유</span><span class="sxs-lookup"><span data-stu-id="d27ce-143">Sharing Results</span></span>

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
<span data-ttu-id="d27ce-144">사용자/팀 간에 공유 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d27ce-144">How to share between users/teams</span></span>
* <span data-ttu-id="d27ce-145">Documents 디렉터리의 Zip 프로젝트</span><span class="sxs-lookup"><span data-stu-id="d27ce-145">Zip project in documents directory</span></span>
* <span data-ttu-id="d27ce-146">프로젝트를 파일 공유에 복사</span><span class="sxs-lookup"><span data-stu-id="d27ce-146">Copy project to file share</span></span>
* <span data-ttu-id="d27ce-147">Maquette 팀에 팀 공유 서브 미션의 파일 위치 추가</span><span class="sxs-lookup"><span data-stu-id="d27ce-147">Adding file location of team share Submissions to Maquette Team</span></span>

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
<span data-ttu-id="d27ce-148">TBD</span><span class="sxs-lookup"><span data-stu-id="d27ce-148">TBD</span></span>
* <span data-ttu-id="d27ce-149">포함, 상대/절대 경로를 사용 하는 코드에 대 한 참조, 모듈</span><span class="sxs-lookup"><span data-stu-id="d27ce-149">Includes, reference to code elsewhere with relative/absolute paths, modules</span></span>
* <span data-ttu-id="d27ce-150">라이브러리인?</span><span class="sxs-lookup"><span data-stu-id="d27ce-150">Libraries?</span></span>
* <span data-ttu-id="d27ce-151">런타임 지원</span><span class="sxs-lookup"><span data-stu-id="d27ce-151">Runtime support</span></span>
* <span data-ttu-id="d27ce-152">확인 되지 않은 외부-항목이 누락/충돌 하는 경우의 동작</span><span class="sxs-lookup"><span data-stu-id="d27ce-152">Unresolved Externals - Behavior when entries missing/crashing</span></span>
* <span data-ttu-id="d27ce-153">특정 개체와 연결 된 스크립트를 추가/편집/관찰할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="d27ce-153">Can we add/edit/observe script associated with specific objects?</span></span>
  * <span data-ttu-id="d27ce-154">이 스크립트를 다른 곳에 복사/붙여 넣을 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="d27ce-154">Can we copy/paste this script elsewhere?</span></span>
  * <span data-ttu-id="d27ce-155">개체 속성은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="d27ce-155">What about object properties?</span></span>
  * <span data-ttu-id="d27ce-156">내 장면에서 개체의 이름을 지정 하 시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="d27ce-156">Naming objects in my scene?</span></span> <span data-ttu-id="d27ce-157">(스크립트 이름 바꾸기)</span><span class="sxs-lookup"><span data-stu-id="d27ce-157">(renaming script with it)</span></span>
  * <span data-ttu-id="d27ce-158">개체와 연결 된 스크립트에 대 한 THIS 또는 SELF 키워드</span><span class="sxs-lookup"><span data-stu-id="d27ce-158">THIS or SELF keyword for script associated with an object</span></span>
  * <span data-ttu-id="d27ce-159">개체를 마우스 오른쪽 단추로 클릭 하면 해당 개체와 관련 된 코드 (및 모든 계층 구조)를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-159">If I right click on an object, can I see code associated with it (and all it's hierarchy)</span></span>
  * <span data-ttu-id="d27ce-160">UI에서 선택 하 여 VSCode의 코드에서 가져올 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="d27ce-160">Can I select in UI and be brought up at the code in VSCode?</span></span>
  * <span data-ttu-id="d27ce-161">스크립트 소스 파일에서 개체와 연결 된 코드를 "함께" 유지</span><span class="sxs-lookup"><span data-stu-id="d27ce-161">Keeping code associated with an object "together" in the script source file?</span></span>
  * <span data-ttu-id="d27ce-162">개체를 클릭할 때 속성 창을 개체 위로 가져오기</span><span class="sxs-lookup"><span data-stu-id="d27ce-162">Bring property window up of an object when I click on it?</span></span> <span data-ttu-id="d27ce-163">VR 및 주 탭에서</span><span class="sxs-lookup"><span data-stu-id="d27ce-163">In VR and in main tab?</span></span>
* <span data-ttu-id="d27ce-164">보안 문제</span><span class="sxs-lookup"><span data-stu-id="d27ce-164">Security Issues</span></span>
* <span data-ttu-id="d27ce-165">테스트-TBD 일 수 있지만 스크립트를 통해 비디오 또는 프레임 잡기를 제안할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-165">Testing – might be TBD but we could suggest video or frame grab by script</span></span>
* <span data-ttu-id="d27ce-166">버그 보고 메커니즘이 있는 경우 다른 사용자를 위해 스크립트를 통해 액세스할 수 있도록 설정할 수 있습니다. 후반</span><span class="sxs-lookup"><span data-stu-id="d27ce-166">If we have a bug reporting mechanism, we might make that accessible via script for others (?) …later</span></span>
* <span data-ttu-id="d27ce-167">배포 – 결과를 "공유" 하는 방법, EXE로 패키지</span><span class="sxs-lookup"><span data-stu-id="d27ce-167">Deployment – how to “share” the result, package as EXE</span></span>
* <span data-ttu-id="d27ce-168">데모 또는 spectating/모니터링 실행/제어</span><span class="sxs-lookup"><span data-stu-id="d27ce-168">Running/controlling a demo or spectating/monitoring</span></span>
* <span data-ttu-id="d27ce-169">플레이어 모드</span><span class="sxs-lookup"><span data-stu-id="d27ce-169">Player mode</span></span>
* <span data-ttu-id="d27ce-170">공유를 위해 "구성 요소"를 만드는 방법에 대 한 세그먼트가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-170">We might have a segment on how to make “components” for sharing?</span></span> <span data-ttu-id="d27ce-171">(tbd 일 수 있음)</span><span class="sxs-lookup"><span data-stu-id="d27ce-171">(might  be tbd)</span></span>
  * <span data-ttu-id="d27ce-172">#Include 있나요?</span><span class="sxs-lookup"><span data-stu-id="d27ce-172">Is there #include?</span></span> <span data-ttu-id="d27ce-173">이는 네임 스페이스 충돌이 있는 것으로 가정 하 고 있는 순수한 JS를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="d27ce-173">This handles pure JS I suppose but may have namespace conflicts.</span></span>
  * <span data-ttu-id="d27ce-174">Maquette가 JS 코드와 일치 하도록 명명 된 개체와 다른 maquette를 통합 하기 위해 수행할 수 있는 작업은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="d27ce-174">Is there anything we could do for a maquette to incorporate some other maquette with named objects to match JS code?</span></span>
