---
title: MRTK 2.5 릴리스 정보
description: MRTK 버전 2.5에 대 한 릴리스 정보
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk,
ms.openlocfilehash: c9458e5236cc7de18eb27c3c3e13221a366c89a4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177517"
---
# <a name="microsoft-mixed-reality-toolkit-25-release-notes"></a><span data-ttu-id="e8f24-104">Microsoft Mixed Reality Toolkit 2.5 릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="e8f24-104">Microsoft Mixed Reality Toolkit 2.5 release notes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8f24-105">ARM64를 사용 하 여 Microsoft HoloLens 2 용으로 빌드된 응용 프로그램에 영향을 주는 알려진 컴파일러 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-105">There is a known compiler issue that impacts applications built for Microsoft HoloLens 2 using ARM64.</span></span> <span data-ttu-id="e8f24-106">이 문제는 2019 Visual Studio 버전 16.8 이상으로 업데이트 하 여 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-106">This issue is fixed by updating Visual Studio 2019 to version 16.8 or later.</span></span> <span data-ttu-id="e8f24-107">Visual Studio를 업데이트할 수 없는 경우에는 패키지를 가져와 `com.microsoft.mixedreality.toolkit.tools` 해결 방법을 적용 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e8f24-107">If you are unable to update Visual Studio, please import the `com.microsoft.mixedreality.toolkit.tools` package to apply a workaround.</span></span>

## <a name="whats-new-in-254"></a><span data-ttu-id="e8f24-108">2.5.4의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="e8f24-108">What's new in 2.5.4</span></span>

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a><span data-ttu-id="e8f24-109">UPM를 사용할 때 Oculus 통합으로 버그를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-109">Fixes a bug with Oculus Integration when using UPM</span></span>

<span data-ttu-id="e8f24-110">UPM를 사용 하는 경우 OculusXRSDKDeviceManagerProfile는 [시작 시 항상 prefabs로 설정](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160)되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-110">When using UPM, the OculusXRSDKDeviceManagerProfile would always have its [prefabs set to None on startup](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160).</span></span> <span data-ttu-id="e8f24-111">이 릴리스는 시작 시 prefabs의 작업 집합을 가리키도록 장치 관리자를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-111">This release configures the Device Manager to point to a working set of prefabs on startup.</span></span>

### <a name="fixes-an-issue-with-openxr-via-upm"></a><span data-ttu-id="e8f24-112">UPM를 통한 OpenXR 문제 해결</span><span class="sxs-lookup"><span data-stu-id="e8f24-112">Fixes an issue with OpenXR via UPM</span></span>

<span data-ttu-id="e8f24-113">OpenXR 공급자가 기본적으로 link.xml에 추가 되지 않아 Unity의 패키지 관리자를 통해 OpenXR 및 mrtk를 사용할 때 새 프로젝트가 장치에서 실행 되지 않는 문제를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-113">Fixes an issue where the OpenXR providers weren't added to the link.xml by default, causing new projects to fail to run on-device when using OpenXR and MRTK via Unity's Package Manager.</span></span> <span data-ttu-id="e8f24-114">업그레이드 된 기존 프로젝트는이를 수동으로 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-114">Existing projects that are upgraded will still need this added manually.</span></span>

## <a name="whats-new-in-253"></a><span data-ttu-id="e8f24-115">2.5.3의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="e8f24-115">What's new in 2.5.3</span></span>

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a><span data-ttu-id="e8f24-116">2.5.2에 도입 된 Oculus를 사용 하 여 회귀를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-116">Fixes a regression with Oculus introduced in 2.5.2</span></span>

<span data-ttu-id="e8f24-117">2.5.2 [에는 Oculus SDK를 통합할 때 빌드 문제가](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083)도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-117">2.5.2 introduced [a build issue when integrating the Oculus SDK](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083).</span></span> <span data-ttu-id="e8f24-118">이 릴리스는 해당 문제를 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-118">This release reverts that issue.</span></span>

## <a name="whats-new-in-252"></a><span data-ttu-id="e8f24-119">2.5.2의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="e8f24-119">What's new in 2.5.2</span></span>

### <a name="add-support-for-openxr"></a><span data-ttu-id="e8f24-120">OpenXR에 대 한 지원 추가</span><span class="sxs-lookup"><span data-stu-id="e8f24-120">Add support for OpenXR</span></span>

<span data-ttu-id="e8f24-121">Unity의 OpenXR 미리 보기 패키지 및 Microsoft의 Mixed Reality OpenXR 패키지에 대 한 초기 지원이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-121">Initial support for Unity's OpenXR preview package and Microsoft's Mixed Reality OpenXR package has been added.</span></span> <span data-ttu-id="e8f24-122">자세한 내용은 [MRTK/XRSDK 시작 페이지](../configuration/getting-started-with-mrtk-and-xrsdk.md), [Unity의 포럼 게시물](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)또는 [Microsoft 설명서](/windows/mixed-reality/develop/unity/openxr-getting-started) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-122">See [the MRTK/XRSDK getting started page](../configuration/getting-started-with-mrtk-and-xrsdk.md), [Unity's forum post](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/), or [Microsoft's documentation](/windows/mixed-reality/develop/unity/openxr-getting-started) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8f24-123">Unity의 OpenXR는 Unity 2020.3 이상 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-123">OpenXR in Unity is only supported on Unity 2020.3 and higher.</span></span>
> <span data-ttu-id="e8f24-124">또한 x64, ARM 및 ARM64 빌드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-124">It also only supports x64, ARM, and ARM64 builds.</span></span>

### <a name="boundary-visualization-errors-fixed"></a><span data-ttu-id="e8f24-125">경계 시각화 오류 수정 됨</span><span class="sxs-lookup"><span data-stu-id="e8f24-125">Boundary visualization errors fixed</span></span>

<span data-ttu-id="e8f24-126">바닥 또는 벽과 같은 경계 시각화는 이제 경계 프로필에 따라 적절 하 게 구성 되 고 런타임에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-126">Boundary visualizations, like the floor or walls, will now be properly configured and visible at runtime according to the boundary profile.</span></span>

### <a name="msbuild-for-unity-support"></a><span data-ttu-id="e8f24-127">Unity 지원 MSBuild</span><span class="sxs-lookup"><span data-stu-id="e8f24-127">MSBuild for Unity support</span></span>

<span data-ttu-id="e8f24-128">unity의 [새 패키지 지침](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)에 맞게 2.5.2 릴리스의 MSBuild에 대 한 지원이 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-128">Support for MSBuild for Unity has been removed as of the 2.5.2 release, to align with [Unity's new package guidance](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span></span>

## <a name="whats-new-in-251"></a><span data-ttu-id="e8f24-129">2.5.1의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="e8f24-129">What's new in 2.5.1</span></span>

### <a name="package-dependency-errors-fixed"></a><span data-ttu-id="e8f24-130">패키지 종속성 오류가 수정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-130">Package dependency errors fixed</span></span>

<span data-ttu-id="e8f24-131">이 릴리스는 잘못 된 패키지 간 파일 종속성을 수정 합니다 (예: 표준 자산의 파일은 더 이상 Foundation의 파일을 잘못 참조 함).</span><span class="sxs-lookup"><span data-stu-id="e8f24-131">This release fixes incorrect inter-package file dependencies (ex: files in Standard Assets no longer incorrectly reference files in Foundation).</span></span> <span data-ttu-id="e8f24-132">버전 2.5.1 텍스트 메시 Pro에 대 한 명시적 종속성도 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-132">Version 2.5.1 also adds an explicit dependency on Text Mesh Pro.</span></span>

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a><span data-ttu-id="e8f24-133">자산/MRTK/셰이더에 복사 되는 표준 자산 패키지 셰이더</span><span class="sxs-lookup"><span data-stu-id="e8f24-133">Standard Assets package shaders copied to Assets/MRTK/Shaders</span></span>

<span data-ttu-id="e8f24-134">UPM를 통해 표준 자산 패키지를 설치 하는 경우 셰이더가 자산/m a s v k/셰이더 폴더로 복사 되어 더 이상 변경할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-134">When the Standard Assets package is installed via UPM, the shaders will be copied to the Assets/MRTK/Shaders folder so that they will no longer be immutable.</span></span> <span data-ttu-id="e8f24-135">이를 통해 다음에 프로젝트가 로드 될 때 레거시 동작을 되돌리는 URP (유니버설 렌더링 파이프라인)에 대해 업데이트 된 셰이더 문제가 해결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-135">This resolves the issue of shaders updated for the Universal Render Pipeline (URP) reverting the legacy behavior the next time the project is loaded.</span></span>

### <a name="fixed-teleport-cursor-sticking-to-hands"></a><span data-ttu-id="e8f24-136">손에 고정 된 텔레포트 커서</span><span class="sxs-lookup"><span data-stu-id="e8f24-136">Fixed teleport cursor sticking to hands</span></span>

<span data-ttu-id="e8f24-137">이 릴리스에서는 텔레포트 대상 커서가 시각적 개체에 집중 될 수 있는 [문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) 를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-137">This release fixes an [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) where the teleport destination cursor can stick to hand visuals.</span></span>

## <a name="whats-new-in-250"></a><span data-ttu-id="e8f24-138">2.5.0의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="e8f24-138">What's new in 2.5.0</span></span>

### <a name="unity-package-manager-upm-support"></a><span data-ttu-id="e8f24-139">UPM (Unity 패키지 관리자) 지원</span><span class="sxs-lookup"><span data-stu-id="e8f24-139">Unity Package Manager (UPM) support</span></span>

<span data-ttu-id="e8f24-140">이제 Unity 패키지 관리자를 사용 하 여 혼합 현실 Toolkit를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-140">The Mixed Reality Toolkit can now be managed using the Unity Package Manager.</span></span>

![MRTK Foundation UPM 패키지](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="e8f24-142">MRTK UPM 패키지를 가져오는 데 필요한 몇 가지 수동 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-142">There are some manual steps required to import the MRTK UPM packages.</span></span> <span data-ttu-id="e8f24-143">자세한 내용은 [혼합 현실 Toolkit 및 Unity 패키지 관리자](../configuration/usingupm.md) 를 검토 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-143">Please review [Mixed Reality Toolkit and Unity Package Manager](../configuration/usingupm.md) for more information.</span></span>

### <a name="oculus-quest-xr-sdk-support"></a><span data-ttu-id="e8f24-144">Oculus Quest XR SDK 지원</span><span class="sxs-lookup"><span data-stu-id="e8f24-144">Oculus Quest XR SDK support</span></span>

<span data-ttu-id="e8f24-145">이제 MRTK는 기본 XR SDK 파이프라인을 사용 하 여 Oculus Quest 헤드셋 및 컨트롤러 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-145">MRTK now supports running Oculus Quest Headsets and Controllers using the native XR SDK pipeline.</span></span> <span data-ttu-id="e8f24-146">[Eric Provencher의](https://twitter.com/prvncher) MRTK-Quest에서 작업 하는 경우에도 [Oculus Integration Unity 패키지](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 에서 수동 추적을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-146">Hand tracking is also supported with the [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) thanks to [Eric Provencher's](https://twitter.com/prvncher) work on MRTK-Quest!</span></span>

<span data-ttu-id="e8f24-147">새 파이프라인을 사용 하 여 Oculus 퀘스트에서 장치를 배포 하는 방법에 대 한 지침은 [Oculus Quest 설치 가이드](../supported-devices/oculus-quest-mrtk.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-147">For instructions on how to deploy your device on the Oculus Quest using the new pipeline, see the [Oculus Quest Setup Guide](../supported-devices/oculus-quest-mrtk.md)</span></span>

### <a name="scrolling-object-collection"></a><span data-ttu-id="e8f24-148">스크롤 개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="e8f24-148">Scrolling Object Collection</span></span>

<span data-ttu-id="e8f24-149">MRTK UX 구성 요소는 실험적 기능에서 업그레이드 되었으며 colliders가 연결 되지 않은 개체에 대 한 지원이 추가 된 다양 한 크기의 3D 콘텐츠를 레이아웃 더 자유롭게 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-149">The MRTK UX component has been upgraded from an experimental feature and offers more freedom for layouting 3D content of different sizes with added support for objects that have no colliders attached.</span></span> <span data-ttu-id="e8f24-150">또한 콘텐츠 마스킹을 사용 하지 않도록 설정 하는 새로운 옵션이 추가 되어 프로토타입을 더 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-150">A new option for disabling content masking was also added, making prototyping easier.</span></span>

<span data-ttu-id="e8f24-151">자세한 내용은 [스크롤 개체 컬렉션](../features/ux-building-blocks/scrolling-object-collection.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-151">See [Scrolling Object Collection](../features/ux-building-blocks/scrolling-object-collection.md) for more information.</span></span>

![스크롤 개체 컬렉션](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a><span data-ttu-id="e8f24-153">텔레포트 포인터 애니메이션, 처리 및 소리 개선</span><span class="sxs-lookup"><span data-stu-id="e8f24-153">Teleport pointer animation, handling, and sound improvements</span></span>

<span data-ttu-id="e8f24-154">이제 텔레포트 포인터가 애니메이션 및 오디오 피드백을 개선 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-154">The teleport pointer now has improved animations and audio feedback.</span></span> <span data-ttu-id="e8f24-155">또한 주변 표면에서 멀리 떨어진 표면으로 전환할 때 더 부드럽게 처리 되도록 텔레포트 포인터의 처리를 개선 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-155">We also improved the handling of the teleport pointer so it handles smoother when transitioning from pointing at nearby surfaces to farther away surfaces.</span></span>

### <a name="input-simulation-cheat-sheet"></a><span data-ttu-id="e8f24-156">입력 시뮬레이션 참고 자료 시트</span><span class="sxs-lookup"><span data-stu-id="e8f24-156">Input simulation cheat sheet</span></span>

<span data-ttu-id="e8f24-157">이제 HandInteractionExamples 장면에는 입력 시뮬레이션에 대 한 도움말 페이지를 표시 하는 구성 가능한 바로 가기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-157">The HandInteractionExamples scene now has a configurable shortcut to show a help page for input simulation</span></span>

![입력 시뮬레이션 참고 자료 시트](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a><span data-ttu-id="e8f24-159">입력 시뮬레이션 눈동자 마우스로 응시</span><span class="sxs-lookup"><span data-stu-id="e8f24-159">Input simulation eye gaze with mouse</span></span>

<span data-ttu-id="e8f24-160">사용자는 이제 시각 추적을 시뮬레이션 하기 위해 마우스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-160">Users can now use the Mouse for simulating eye tracking.</span></span> <span data-ttu-id="e8f24-161">`Eye Simulation Mode`입력 시뮬레이션 프로필의 필드를 확인 하 고 마우스로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-161">See the `Eye Simulation Mode` field in the input simulation profile and set it to Mouse.</span></span> <span data-ttu-id="e8f24-162">이전 필드를 대체 `Simulate Eye Position` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-162">This replaces the previous `Simulate Eye Position` field.</span></span>

![아이 응시 마우스](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a><span data-ttu-id="e8f24-164">편집기 재생 모드의 입력 시뮬레이션 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="e8f24-164">Input simulation motion controller in editor Play Mode</span></span>

<span data-ttu-id="e8f24-165">이제 사용자는 편집자 재생 모드와 마찬가지로 동작 컨트롤러를 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-165">Users can now simulate motion controller just like hands in editor play mode.</span></span> <span data-ttu-id="e8f24-166">트리거, 잡기 및 메뉴 단추가 현재 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-166">The trigger, grab and menu buttons are currently supported.</span></span>

### <a name="conical-grab-pointer"></a><span data-ttu-id="e8f24-167">원추형 잡기 포인터</span><span class="sxs-lookup"><span data-stu-id="e8f24-167">Conical grab pointer</span></span>

<span data-ttu-id="e8f24-168">이제 구가 아닌 잡기에서 원뿔을 사용 하 여 근처 개체를 쿼리하도록 잡기 포인터를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-168">Grab pointers can now be configured to query for nearby objects using a cone from the grab point rather than a sphere.</span></span> <span data-ttu-id="e8f24-169">이는 원뿔을 사용 하 여 인접 개체를 쿼리 하는 기본 HoloLens 2 인터페이스의 동작과 매우 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-169">This more closely resembles the behavior from the default HoloLens 2 interface, which queries for nearby objects using a cone.</span></span> <span data-ttu-id="e8f24-170">또한 새를 사용 하도록 DefaultHoloLens2InputSystemProfile 조정 되었습니다 `ConicalGrabPointer` .</span><span class="sxs-lookup"><span data-stu-id="e8f24-170">The DefaultHoloLens2InputSystemProfile has also been adjusted to use the new `ConicalGrabPointer`.</span></span>

![원추형 잡기 포인터](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a><span data-ttu-id="e8f24-172">TestUtilities 패키지</span><span class="sxs-lookup"><span data-stu-id="e8f24-172">TestUtilities package</span></span>

<span data-ttu-id="e8f24-173">이제 패키지 (MixedReality. Toolkit가 있습니다. 2.5.0. unitypackage)-MRTK에서 종단 간 테스트를 만드는 데 사용 하는 PlayMode 및 Testutilities 테스트 인프라를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-173">There is now a package (Microsoft.MixedReality.Toolkit.Unity.TestUtilities.2.5.0.unitypackage) that contains the PlayMode and TestMode test infrastructure that the MRTK uses to create end-to-end tests.</span></span> <span data-ttu-id="e8f24-174">이 인프라는 MRTK 팀 자체에 매우 유용 하 게 사용 되었으며 소비자가이를 사용 하 여 자체 프로젝트에 테스트 검사를 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-174">This infrastructure has been extremely handy for the MRTK team itself, and we're excited to have consumers use this to add test coverage to their own projects.</span></span>

<span data-ttu-id="e8f24-175">다음 코드에서는 테스트 손을 만들고, 특정 위치에 표시 하 고, 이동 하 고, 옆으로 여는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-175">The following code shows how to create a test hand, show it at a certain location, move it around, and then pinch and open.</span></span>

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

<span data-ttu-id="e8f24-176">이러한 TestUtilities를 사용 하 여 테스트를 작성 하는 방법에 대 한 지침은 [테스트 작성](../contributing/unit-tests.md#writing-tests)에 대 한이 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-176">For instructions on how to write a test using these TestUtilities, see this section on [writing tests](../contributing/unit-tests.md#writing-tests).</span></span>

<span data-ttu-id="e8f24-177">이 인프라를 사용 하는 기존 테스트에 대 한 예제는 MRTK의 [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-177">For examples of existing tests that use this infrastructure, see MRTK's [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests).</span></span>

### <a name="support-for-the-leap-motion-451-unity-modules"></a><span data-ttu-id="e8f24-178">도약 동작 4.5.1 Unity 모듈 지원</span><span class="sxs-lookup"><span data-stu-id="e8f24-178">Support for the Leap Motion 4.5.1 Unity Modules</span></span>

<span data-ttu-id="e8f24-179">도약 동작 Unity 모듈 버전 4.5.1에 대 한 지원이 추가 되었으며 4.4.0 자산에 대 한 지원이 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-179">Support for the Leap Motion Unity Modules version 4.5.1 has been added and support for the 4.4.0 assets has been removed.</span></span> <span data-ttu-id="e8f24-180">현재 지원 되는 Leap 동작 Unity 모듈의 버전은 4.5.0 및 4.5.1입니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-180">The current supported versions of the Leap Motion Unity Modules are 4.5.0 and 4.5.1.</span></span>

<span data-ttu-id="e8f24-181">초기 Leap 동작 통합에 대 한 추가 단계도 있습니다. 자세한 내용은 [MRTK에서 Leap 동작 손 추적을 구성 하는 방법](../supported-devices/leap-motion-mrtk.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-181">There is also an additional step for initial Leap Motion integration, see [How to Configure the Leap Motion Hand Tracking in MRTK](../supported-devices/leap-motion-mrtk.md) for more information.</span></span>

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a><span data-ttu-id="e8f24-182">공간 인식 메시 관찰자는 자료의 사용자 지정을 더 잘 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-182">Spatial Awareness Mesh Observer better handles customization of materials</span></span>

<span data-ttu-id="e8f24-183">이 릴리스에서 `Windows Mixed Reality Spatial Mesh Observer` 및 `Generic XR SDK Spatial Mesh Observer` 구성 요소는 시각적 재질 처리를 개선 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-183">With this release, the `Windows Mixed Reality Spatial Mesh Observer` and the `Generic XR SDK Spatial Mesh Observer` components have improved visual material handling.</span></span> <span data-ttu-id="e8f24-184">이전에는 관찰자에 의해 메쉬가 업데이트 된 후에도 재질은 유지 됩니다 .이는 이전에 프로필에 구성 된 대로 기본 VisibleMaterial 다시 설정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-184">Materials are now preserved when a mesh has been updated by the observer where, previously, they were reset to the default VisibleMaterial as configured in the profile.</span></span>

<span data-ttu-id="e8f24-185">이렇게 하면 개발자가 메시 자료를 변경 하 고 변경 내용을 예기치 않게 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-185">This enables developers to alter the mesh material and not have the changes overwritten unexpectedly.</span></span>

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a><span data-ttu-id="e8f24-186">MixedRealityToolkit 폴더에 생성 된 Link.xml</span><span class="sxs-lookup"><span data-stu-id="e8f24-186">Link.xml created in the MixedRealityToolkit.Generated folder</span></span>

<span data-ttu-id="e8f24-187">Unity 패키지 관리자 MRTK가 도입 되면서 이제 MRTK가 없는 `link.xml` 경우 폴더에 파일을 씁니다 `Assets/MixedRealityToolkit.Generated` .</span><span class="sxs-lookup"><span data-stu-id="e8f24-187">With the introduction of Unity Package Manger MRTK, MRTK now writes a `link.xml` file to the `Assets/MixedRealityToolkit.Generated` folder, if none is present.</span></span> <span data-ttu-id="e8f24-188">이 파일을 추가 하는 것이 좋습니다 .이 파일을 소스 제어에 추가 하는 것이 좋습니다 `link.xml.meta` .</span><span class="sxs-lookup"><span data-stu-id="e8f24-188">It is recommended to add this file (and `link.xml.meta`) be added to source control.</span></span> <span data-ttu-id="e8f24-189">Link.xml은 Unity 링커의 [관리 코드](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) 제거 기능에 영향을 주는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-189">Link.xml is used to influence the [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) functionality of the Unity linker.</span></span>

<span data-ttu-id="e8f24-190">MRTK link.xml 파일에 대 한 자세한 내용은 [mrtk 및 관리 코드](../updates-deployment/mrtk-and-managed-code-stripping.md) 제거 문서에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-190">More information on the MRTK link.xml file can be found in the [MRTK and managed code stripping](../updates-deployment/mrtk-and-managed-code-stripping.md) article.</span></span>

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a><span data-ttu-id="e8f24-191">Unity 2019.3 +: MRTK 구성 대화 상자에서 더 이상 레거시 XR 지원 사용을 시도 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-191">Unity 2019.3+: MRTK configuration dialog no longer attempts to enable legacy XR support</span></span>

<span data-ttu-id="e8f24-192">Unity의 XR 플랫폼을 사용 하는 경우 충돌을 방지 하기 위해 레거시 XR 지원을 사용 하도록 설정 하는 옵션이 MRTK 구성 대화 상자에서 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-192">To avoid potential conflicts when using Unity's XR Platform, the option to enable legacy XR support has been removed from the MRTK configuration dialog.</span></span> <span data-ttu-id="e8f24-193">XR를 사용 하는 경우에는 Unity 2019에서 **편집**  >  **Project 설정**  >
 **Player**  >  **XR 설정**  >  **가상 현실 지원** 을 사용 하 여 레거시 지원을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-193">If desired, legacy XR support can be enabled, in Unity 2019, using **Edit** > **Project Settings** >
**Player** > **XR Settings** > **Virtual Reality Supported**.</span></span>

### <a name="reduction-in-initializeonload-overhead"></a><span data-ttu-id="e8f24-194">InitializeOnLoad 오버 헤드 감소</span><span class="sxs-lookup"><span data-stu-id="e8f24-194">Reduction in InitializeOnLoad overhead</span></span>

<span data-ttu-id="e8f24-195">여기서는 작업을 수행 하 여 InitializeOnLoad 처리기에서 실행 되는 작업의 양을 줄이고 내부 루프 개발 속도를 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-195">We've been doing work to reduce the amount of work that runs in InitializeOnLoad handlers, which should lead to improvements in inner loop development speed.</span></span> <span data-ttu-id="e8f24-196">InitializeOnLoad 처리기는 스크립트가 컴파일될 때마다 재생 모드를 시작 하기 전에 실행 되 고 편집기 시작 에서도 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-196">InitializeOnLoad handlers run every time a script is compiled, prior to entering play mode, and also at editor launch.</span></span> <span data-ttu-id="e8f24-197">이러한 처리기는 이제 훨씬 더 낮은 사례에서 실행 되므로 일반적인 Unity 응답성이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-197">These handlers now run in far fewer cases, resulting in general Unity responsiveness improvements.</span></span>

<span data-ttu-id="e8f24-198">일부 경우에는 다음을 수행 해야 하는 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-198">In some cases there was a tradeoff that had to be made:</span></span>

- <span data-ttu-id="e8f24-199">추가 통합 단계에 대 한 [도약 동작 손 추적 구성](../supported-devices/leap-motion-mrtk.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-199">See [Leap Motion Hand Tracking Configuration](../supported-devices/leap-motion-mrtk.md) for the extra integration step.</span></span>
- <span data-ttu-id="e8f24-200">ARFoundation을 사용 하는 사용자에 게는 시작 단계에 추가 수동 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-200">For those who are using ARFoundation, there's now an additional manual step in its getting started steps.</span></span>
  <span data-ttu-id="e8f24-201">새 단계는 [ARFoundation을](../supported-devices/using-ar-foundation.md#install-required-packages) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-201">See [ARFoundation](../supported-devices/using-ar-foundation.md#install-required-packages) for the new steps.</span></span>
- <span data-ttu-id="e8f24-202">HoloLens 2 [레거시 XR 파이프라인과 함께 홀로그램 Remoting을](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) 사용하는 경우 이제 수행할 [수동 단계가](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-202">For those who will be using [Holographic Remoting with legacy XR pipeline](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) on HoloLens 2, there is now a [manual step](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) to perform.</span></span>

### <a name="bounds-control-graduated"></a><span data-ttu-id="e8f24-203">경계 컨트롤이 자를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-203">Bounds control graduated</span></span>

![경계 컨트롤](../features/images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="e8f24-205">[경계 컨트롤은](../features/ux-building-blocks/bounds-control.md) 실험적 요소에서 벗어나며 다양한 새로운 기능과 버그 수정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-205">[Bounds control](../features/ux-building-blocks/bounds-control.md) graduated out of experimental and comes with a bunch of new features and tons of bug fixes.</span></span>
<span data-ttu-id="e8f24-206">다음은 이 업데이트의 주요 사항 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-206">Here a list of the highlights of this update:</span></span>

- <span data-ttu-id="e8f24-207">속성은 범위 제어를 쉽게 설정할 수 있는 구성으로 분할됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-207">properties are split into configurations which makes it easier to set up bounds control</span></span>
- <span data-ttu-id="e8f24-208">구성은 스크립팅 가능한 개체를 통해 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-208">configurations can be shared through scriptable objects</span></span>
- <span data-ttu-id="e8f24-209">모든 속성/스크립트 가능 속성은 런타임 구성 가능</span><span class="sxs-lookup"><span data-stu-id="e8f24-209">every property / scriptable property is runtime configurable</span></span>
- <span data-ttu-id="e8f24-210">범위 제어 조작이 더 이상 속성 변경 시 다시 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-210">bounds control rig isn't recreated on property changes anymore</span></span>
- <span data-ttu-id="e8f24-211">번역 핸들 지원</span><span class="sxs-lookup"><span data-stu-id="e8f24-211">translation handles support</span></span>
- <span data-ttu-id="e8f24-212">제약 조건 관리자를 통한 전체 제약 조건 지원</span><span class="sxs-lookup"><span data-stu-id="e8f24-212">full constraint support through constraint manager</span></span>
- <span data-ttu-id="e8f24-213">탄력적 시스템 통합(실험적)</span><span class="sxs-lookup"><span data-stu-id="e8f24-213">elastics system integration (experimental)</span></span>

<span data-ttu-id="e8f24-214">이전 경계 상자는 이제 더 이상 사용되지 않으며 경계 상자를 사용하는 기존 게임 개체는 마이그레이션 도구 또는 [경계 상자 검사자를](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control) [사용하여 업그레이드할](../features/tools/migration-window.md) 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-214">The old bounding box is now deprecated and existing game objects using bounding box can be [upgraded using the migration tool](../features/tools/migration-window.md) or the [bounding box inspector](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control).</span></span>

### <a name="constraint-manager-component"></a><span data-ttu-id="e8f24-215">제약 조건 관리자 구성 요소</span><span class="sxs-lookup"><span data-stu-id="e8f24-215">Constraint manager component</span></span>

<span data-ttu-id="e8f24-216">이제 새 제약 조건 [관리자 구성 요소](../features/ux-building-blocks/constraint-manager.md)를 통해 경계 제어 및 개체 조작자 둘 다에서 제약 조건을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-216">Constraints can now be used by both, bounds control and object manipulator via the new [constraint manager component](../features/ux-building-blocks/constraint-manager.md).</span></span> <span data-ttu-id="e8f24-217">두 구성 요소 모두 기본값당 제약 조건 관리자를 만들고 연결된 제약 조건을 자동으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-217">Both components will create a constraint manager per default and process any attached constraints automatically.</span></span>

<span data-ttu-id="e8f24-218">또한 자동 동작 제약 조건 관리자에는 사용자가 처리해야 하는 제약 조건을 결정할 수 있는 수동 모드도 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-218">Additionally to the automatic behavior constraint manager also comes with a manual mode that lets users decide which constraint should be processed.</span></span>
<span data-ttu-id="e8f24-219">이러한 이유로 속성 검사자에서 제약 조건을 표시하는 방법이 약간 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-219">For this reason the way we display constraints in the property inspector changed a bit.</span></span>

<img src="../features/images/constraint-manager/ManualSelection.png" width="600" alt="Inspector view showing manual constraint manager selection">

<span data-ttu-id="e8f24-220">이제 구성 요소에 적용되는 제약 조건이 제약 조건 관리자 구성 요소의 목록으로 표시되지만 제약 조건 관리자를 사용하는 구성 [요소(경계 컨트롤](../features/ux-building-blocks/bounds-control.md#constraint-system) 또는 [개체 조작자)에는](../features/ux-building-blocks/object-manipulator.md#constraint-manager)선택한 제약 조건 관리자 및 모드(자동 또는 수동)가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-220">The constraints that are applied to the component are now shown as a list in the constraint manager component whereas the component using the constraint manager (either [bounds control](../features/ux-building-blocks/bounds-control.md#constraint-system) or [object manipulator](../features/ux-building-blocks/object-manipulator.md#constraint-manager)) will now show the selected constraint manager and mode (auto or manual).</span></span>
<span data-ttu-id="e8f24-221">자세한 내용은 문서의 [제약 조건 관리자](../features/ux-building-blocks/constraint-manager.md) 섹션을 읽어보십시오.</span><span class="sxs-lookup"><span data-stu-id="e8f24-221">For more information read the [constraint manager](../features/ux-building-blocks/constraint-manager.md) section in our docs.</span></span>

### <a name="hololens-2-button-material-update"></a><span data-ttu-id="e8f24-222">HoloLens 2 단추 재질 업데이트</span><span class="sxs-lookup"><span data-stu-id="e8f24-222">HoloLens 2 button material update</span></span>

<span data-ttu-id="e8f24-223">MRC에서 검은색을 제거하도록 HoloLens 2 단추의 전면 재질이 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-223">Updated HoloLens 2 button's front cage material to remove black color in MRC.</span></span>

![HoloLens 2 단추 재질 업데이트](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a><span data-ttu-id="e8f24-225">설명 패널 업데이트, 이동 가능한 예제 장면</span><span class="sxs-lookup"><span data-stu-id="e8f24-225">Description panel update, movable example scene</span></span>

<span data-ttu-id="e8f24-226">설명 패널이 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-226">Updated description panel.</span></span> <span data-ttu-id="e8f24-227">(SceneDescriptionPanelRev.prefab) 새 디자인은 사용자가 전체 장면을 조정/이동할 수 있는 잡기 가능한 위쪽 막대를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-227">(SceneDescriptionPanelRev.prefab) New design provides a grabbable top bar which allows the user to adjust/move the entire scene.</span></span>

![설명 패널 업데이트](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a><span data-ttu-id="e8f24-229">공간 메시 시각화 - 에어 탭 시 펄스</span><span class="sxs-lookup"><span data-stu-id="e8f24-229">Spatial mesh visualization - pulse on air-tap</span></span>

<span data-ttu-id="e8f24-230">공간 메시의 펄스 셰이더 예제가 HoloLens 2 셸 동작과 일치하도록 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-230">Updated pulse shader example for the spatial mesh to match HoloLens 2's shell behavior.</span></span>

![에어 탭의 펄스](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system-experimental"></a><span data-ttu-id="e8f24-232">탄력적 시스템(실험적)</span><span class="sxs-lookup"><span data-stu-id="e8f24-232">Elastic system (experimental)</span></span>

![탄력적 시스템 2](../features/images/elastics/Elastics_Main.gif)

<span data-ttu-id="e8f24-234">MRTK는 이제 4차원 쿼터니언 Spring, 3차원 볼륨 Spring 및 간단한 선형 Spring 시스템에 대한 바인딩을 제공하는 다양한 extensible 및 flexible 서브클래스를 포함하는 [탄력적 시뮬레이션 시스템과](../features/experimental/elastic-system.md) 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-234">MRTK now comes with an [elastic simulation system](../features/experimental/elastic-system.md) that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="e8f24-235">현재 [탄력적 관리자를](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) 지원하는 다음 MRTK 구성 요소는 탄력적 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-235">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="e8f24-236">경계 컨트롤</span><span class="sxs-lookup"><span data-stu-id="e8f24-236">Bounds control</span></span>](../features/ux-building-blocks/bounds-control.md#elastics-experimental)
- [<span data-ttu-id="e8f24-237">개체 조작자</span><span class="sxs-lookup"><span data-stu-id="e8f24-237">Object manipulator</span></span>](../features/ux-building-blocks/object-manipulator.md#elastics-experimental)

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Expanding an elastic menu">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Grabbing an elastic coffee cup">

### <a name="joystick-experimental"></a><span data-ttu-id="e8f24-238">운석(실험적)</span><span class="sxs-lookup"><span data-stu-id="e8f24-238">Joystick (experimental)</span></span>

<span data-ttu-id="e8f24-239">큰 대상 개체를 제어할 수 있는 대용량 인터페이스의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-239">An example of joystick interface that can control a large target object.</span></span>

![조이스틱](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a><span data-ttu-id="e8f24-241">색 선택기(실험적)</span><span class="sxs-lookup"><span data-stu-id="e8f24-241">Color picker (experimental)</span></span>

<span data-ttu-id="e8f24-242">런타임에 개체의 재질 색을 쉽게 변경할 수 있는 실험적 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-242">An experimental control that makes it easy to change material colors on any object at runtime.</span></span>

![색 선택 컨트롤의 세 가지 메서드](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)

![색 선택 컨트롤의 네 가지 메서드](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

## <a name="breaking-changes"></a><span data-ttu-id="e8f24-245">주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="e8f24-245">Breaking changes</span></span>

### <a name="assembly-definition-files-changes"></a><span data-ttu-id="e8f24-246">어셈블리 정의 파일 변경 내용</span><span class="sxs-lookup"><span data-stu-id="e8f24-246">Assembly definition files changes</span></span>

<span data-ttu-id="e8f24-247">일부 asmdef 파일이 변경되었으며 이제 Unity 2018.4.13f1 이상만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-247">Some asmdef files are changed and are now only supporting Unity 2018.4.13f1 or later.</span></span> <span data-ttu-id="e8f24-248">이전 버전의 Unity에서 MRTK 2.5로 업데이트하면 컴파일 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-248">Compilation errors will show up when updating to MRTK 2.5 in earlier versions of Unity.</span></span> <span data-ttu-id="e8f24-249">이 문제는 프로젝트 창에서 로 이동한 다음 `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` 검사기에서 누락된 참조를 제거하여 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-249">This can be fixed by going to `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` in the project window and removing the missing reference in the inspector.</span></span> <span data-ttu-id="e8f24-250">및 를 통해 이러한 단계를 `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-250">Repeat those steps with `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` and `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef`.</span></span> <span data-ttu-id="e8f24-251">Unity 2019로 업그레이드할 때 이러한 세 asmdef 파일을 원래(즉, 수정되지 않은) 파일로 바꾸어 변경 내용을 되돌려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-251">Note you must revert the changes by replacing those three asmdef files with original (i.e. unmodified) ones when upgrading to Unity 2019.</span></span>

### <a name="imixedrealitypointermediator"></a><span data-ttu-id="e8f24-252">IMixedRealityPointerMediator</span><span class="sxs-lookup"><span data-stu-id="e8f24-252">IMixedRealityPointerMediator</span></span>

<span data-ttu-id="e8f24-253">이 인터페이스는 새 함수를 갖도록 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-253">This interface has been updated to have a new function:</span></span>

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

<span data-ttu-id="e8f24-254">DefaultPointerMediator를 서브클래스하지 않는 사용자 지정 포인터 중재자가 있는 경우 이 새 함수를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-254">If you have a custom pointer mediator that doesn't subclass DefaultPointerMediator, you will need to implement this new function.</span></span> <span data-ttu-id="e8f24-255">[이 문제가](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) 추가된 이유에 대한 자세한 배경은 이 문제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-255">See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) for more background on why this was added.</span></span> <span data-ttu-id="e8f24-256">이는 IPointerPreferences를 수행한 생성자의 존재에 따라 암시적으로 수행되지 않고 포인터 기본 설정이 중재자에 명시적으로 전달되도록 하기 위해 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-256">This was added to ensure that pointer preferences would be explicitly passed to the mediator, rather than having it be implicitly done based on the presence of a constructor that took a IPointerPreferences.</span></span>

### <a name="rest--device-portal-api"></a><span data-ttu-id="e8f24-257">Rest/장치 포털 API</span><span class="sxs-lookup"><span data-stu-id="e8f24-257">Rest / Device Portal API</span></span>

<span data-ttu-id="e8f24-258">`UseSSL`정적 속성이 에서 로 `Rest` `DevicePortal` 이동되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-258">The `UseSSL` static property has been moved from `Rest` to `DevicePortal`.</span></span>

<span data-ttu-id="e8f24-259">이전에 이 작업을 한 경우...</span><span class="sxs-lookup"><span data-stu-id="e8f24-259">If you did this previously...</span></span>

```csharp
Rest.UseSSL = true
```

<span data-ttu-id="e8f24-260">지금 이 작업을 수행합니다...</span><span class="sxs-lookup"><span data-stu-id="e8f24-260">Do this now...</span></span>

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a><span data-ttu-id="e8f24-261">Link.xml</span><span class="sxs-lookup"><span data-stu-id="e8f24-261">Link.xml</span></span>

<span data-ttu-id="e8f24-262">애플리케이션이 이전에 MRTK의 NuGet 배포를 사용했다면 `link.xml` 파일이 Foundation 패키지에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-262">If an application was previously using the NuGet distribution of the MRTK, the `link.xml` file has been removed from the Foundation package.</span></span> <span data-ttu-id="e8f24-263">코드 유지 규칙을 복원하려면 Unity에서 프로젝트를 한 번 열면 에 기본 파일이 만들어지게 `link.xml` `Assets/MixedRealityToolkit.Generated` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-263">To restore code preservation rules, opening the project in Unity once will create a default `link.xml` file in `Assets/MixedRealityToolkit.Generated`.</span></span> <span data-ttu-id="e8f24-264">이 파일(및 `link.xml.meta` )을 소스 제어에 추가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-264">It is recommended that this file (and `link.xml.meta`) be added to source control.</span></span>

### <a name="transform-constraint-changes"></a><span data-ttu-id="e8f24-265">Transform 제약 조건 변경</span><span class="sxs-lookup"><span data-stu-id="e8f24-265">Transform Constraint changes</span></span>

<span data-ttu-id="e8f24-266">TargetTransform 속성은 제약 조건 시스템에서 사용되지 않기 때문에 사용되지 않는 것으로 표시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-266">TargetTransform property has been marked as obsolete as it wasn't used by constraint system.</span></span> <span data-ttu-id="e8f24-267">제약 조건 논리는 Initialize 및 Apply 메서드에 전달된 변환을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-267">Constraint logic is based on the transform passed into Initialize and Apply methods.</span></span> <span data-ttu-id="e8f24-268">이 속성을 사용하는 파생된 사용자 제약 조건은 제약 조건 구성 요소의 변환을 저장하여 해당 구현에서 TargetTransform을 캐시하여 동일한 동작을 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-268">Derived user constraints that rely on this property can cache the TargetTransform in their implementation by storing the transform of the constraint component to achieve the same behavior.</span></span>

<span data-ttu-id="e8f24-269">저장된 초기 world pose `worldPoseOnManipulationStart` 데이터 형식이 MixedRealityPose에서 MixedRealityTransform으로 변경되었습니다. 여기에는 조작된 개체의 로컬 배율 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-269">The stored initial world pose `worldPoseOnManipulationStart` data type has been changed from MixedRealityPose to MixedRealityTransform, which includes the local scale value of the manipulated object.</span></span> <span data-ttu-id="e8f24-270">이 변경으로 초기 크기 조정 값을 더 이상 별도로 캐시할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-270">With this change it's not necessary to separately cache any initial scale values anymore.</span></span>

### <a name="new-property-in-imixedrealitydictationsystem"></a><span data-ttu-id="e8f24-271">IMixedRealityDictationSystem의 새 속성</span><span class="sxs-lookup"><span data-stu-id="e8f24-271">New property in IMixedRealityDictationSystem</span></span>

<span data-ttu-id="e8f24-272">`AudioClip`새 속성이 IMixedRealityDictationSystem 인터페이스에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-272">A new property `AudioClip` has been added to the IMixedRealityDictationSystem interface.</span></span> <span data-ttu-id="e8f24-273">`AudioClip`속성을 사용 하면 현재 받아쓰기 세션과 연결 된 오디오 클립에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-273">The `AudioClip` property enables access to the audio clip associated with the current dictation session.</span></span> <span data-ttu-id="e8f24-274">사용자는 인터페이스를 구현하는 스크립트에서 속성을 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-274">Users must implement the property in their scripts implementing the interface.</span></span>

### <a name="service-facades-turn-down"></a><span data-ttu-id="e8f24-275">서비스 외관이 꺼집니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-275">Service facades turn down</span></span>

<span data-ttu-id="e8f24-276">서비스 외관은 2.5에서 꺼지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-276">Services facades are being turned down in 2.5.</span></span> <span data-ttu-id="e8f24-277">이 기능은 원래 MRTK 프로필을 더 쉽게 구성하기 위해 추가되었습니다(각 MRTK의 서비스를 나타내는 가짜 장면 내 GameObjects를 만들어).</span><span class="sxs-lookup"><span data-stu-id="e8f24-277">This feature was originally added to make configuration of the MRTK profiles easier (by creating fake in-scene GameObjects that represented each of MRTK's services).</span></span> <span data-ttu-id="e8f24-278">장기적으로는 가짜 게임 내 개체를 만들고 동기화된 상태로 유지하려고 합니다(데이터 동기화 및 "진리 출처" 문제는 크기 조정 및 제대로 진행하기가 매우 어렵기 때문에).</span><span class="sxs-lookup"><span data-stu-id="e8f24-278">In the long run, we want to avoid creating fake in-game objects and trying to keep them in sync (as data sync and "source of truth" issues are notoriously difficult to scale and get right).</span></span>

<span data-ttu-id="e8f24-279">2.5에서는 프로젝트 업그레이드가 원활하게 진행되도록 서비스 외관 처리기가 유지됩니다. 2.5에서 열린 장면을 자동으로 수정하기 위해 프로젝트에 있는 모든 외관이 서비스 외관 처리기에 의해 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-279">In 2.5, the service facade handlers are kept around to ensure that project upgrade goes smoothly - any facades that exist in the project will be deleted by the service facade handler to ensure that scenes opened up in 2.5 get automatically fixed.</span></span>

<span data-ttu-id="e8f24-280">서비스 외관 기능과 연결된 나머지 코드는 이후 릴리스에서 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-280">The remaining code associated with the service facade feature will be removed in a future release.</span></span>

### <a name="addition-of-motion-controller-to-input-simulation-service"></a><span data-ttu-id="e8f24-281">입력 시뮬레이션 서비스에 모션 컨트롤러 추가</span><span class="sxs-lookup"><span data-stu-id="e8f24-281">Addition of motion controller to input simulation service</span></span>

<span data-ttu-id="e8f24-282">이제 모션 컨트롤러 시뮬레이션이 기존 손 시뮬레이션과 함께 편집기 재생 모드로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-282">Motion controller simulation is now offered in editor play mode along side the existing hand simulation.</span></span> <span data-ttu-id="e8f24-283">이 변경을 사용하도록 설정하기 위해 많은 현재 함수/필드/속성이 이제 사용되지 않는 것으로 표시되고 `InputSimulationService.cs` `MixedRealityInputSimulationProfile.cs` 가장 중요한 변경 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-283">To enable this change, many current functions/fields/properties are now marked obsolete, with `InputSimulationService.cs` and `MixedRealityInputSimulationProfile.cs` getting the most significant changes.</span></span> <span data-ttu-id="e8f24-284">관련 코드의 논리와 동작은 대체로 동일하게 유지되며, 대부분의 사용되지 않는 함수 등은 "hand"에 대한 참조를 보다 일반적인 용어 "컨트롤러"(예: 에서 로)로 바꾸는 것과 관련이 `DefaultHandSimulationMode` `DefaultControllerSimulationMode` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-284">The logic and behavior of relevant code largely remain the same, and the majority of obsoleted functions etc. are related to replacing reference to "hand" to the more generic term "controller" (e.g. from `DefaultHandSimulationMode` to `DefaultControllerSimulationMode`).</span></span> <span data-ttu-id="e8f24-285">새 이름을 얻는 것 외에도 특정 새 함수의 반환 형식이 이름/동작 변경 내용과 일치하도록 업데이트됩니다(예: `GetControllerDevice` 원본 기반이 `GetHandDevice` 이제 대신 를 `BaseController` `SimulatedHand` 반환함).</span><span class="sxs-lookup"><span data-stu-id="e8f24-285">Besides getting new names, the return type of certain new functions are updated to match the name/behavior change (e.g. `GetControllerDevice` based on the original `GetHandDevice` now returns `BaseController` instead of `SimulatedHand`).</span></span>

<span data-ttu-id="e8f24-286">`IInputSimulationService` 이제 새 속성 `MotionControllerDataLeft` 및 `MotionControllerDataRight` 가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-286">`IInputSimulationService` now has new properties `MotionControllerDataLeft` and `MotionControllerDataRight`.</span></span> <span data-ttu-id="e8f24-287">`MixedRealityInputSimulationProfile` 이제 특정 모션 컨트롤러 단추의 키보드 매핑에 대한 새 필드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-287">`MixedRealityInputSimulationProfile` now includes new fields for the keyboard mapping of certain motion controller buttons.</span></span>

## <a name="known-issues"></a><span data-ttu-id="e8f24-288">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="e8f24-288">Known issues</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="e8f24-289">CameraCache가 종료 시 새 카메라를 만들 수 있음</span><span class="sxs-lookup"><span data-stu-id="e8f24-289">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="e8f24-290">일부 상황(예: Unity 편집기에서 LeapMotion 공급자를 사용하는 경우)에서는 CameraCache가 종료 시 MainCamera를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-290">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="e8f24-291">자세한 내용은 [이 문제를](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-291">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="e8f24-292">Unity 패키지 관리자 통해 예제를 가져올 때 FileNotFoundException</span><span class="sxs-lookup"><span data-stu-id="e8f24-292">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="e8f24-293">프로젝트 경로의 길이에 따라 Unity 패키지 관리자 통해 예제를 가져오면 Unity 콘솔에서 FileNotFoundException 메시지가 생성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-293">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="e8f24-294">이로 인해 "누락된" 파일의 경로가 MAX_PATH(256자)보다 길기 때문에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-294">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="e8f24-295">해결하려면 프로젝트 경로의 길이를 줄이세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-295">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="e8f24-296">spatializer가 지정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-296">No spatializer was specified.</span></span> <span data-ttu-id="e8f24-297">애플리케이션은 공간 음향을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-297">The application will not support Spatial Sound</span></span>

<span data-ttu-id="e8f24-298">오디오 공간화기가 구성되지 않은 경우 "공간화기가 지정되지 않았습니다." 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-298">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="e8f24-299">Unity는 이러한 패키지에 공간화 도우미를 포함하기 때문에 XR 패키지가 설치되지 않은 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-299">This can occur if no XR package is installed, as Unity includes spatializers in these packages.</span></span>

<span data-ttu-id="e8f24-300">해결하려면 다음을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-300">To resolve, please ensure that:</span></span>

- <span data-ttu-id="e8f24-301">**창**  >  **패키지 관리자** 하나 이상의 XR 패키지가 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-301">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="e8f24-302">**Mixed Reality Toolkit**  >  **유틸리티**  >  **Unity Project 구성** 및 Audio **Spatializer** 선택</span><span class="sxs-lookup"><span data-stu-id="e8f24-302">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![오디오 공간화기 선택](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="e8f24-304">NullReferenceException: 개체 참조가 개체의 인스턴스로 설정되지 않음(SceneTransitionService.Ini초기화)</span><span class="sxs-lookup"><span data-stu-id="e8f24-304">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="e8f24-305">경우에 따라 를 `EyeTrackingDemo-00-RootScene` 열면 SceneTransitionService 클래스의 Initialize 메서드에서 NullReferenceException이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-305">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="e8f24-306">이 오류는 장면 전환 서비스의 구성 프로필이 설정되지 않아 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-306">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="e8f24-307">해결하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-307">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="e8f24-308">`MixedRealityToolkit`계층의 개체로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-308">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="e8f24-309">검사기 창에서 를 선택합니다. `Extensions`</span><span class="sxs-lookup"><span data-stu-id="e8f24-309">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="e8f24-310">확장하지 않으면 확장합니다. `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="e8f24-310">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="e8f24-311">값을 `Configuration Profile` **MRTKExamplesHubSceneTransitionServiceProfile로** 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-311">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

![장면 전환 수정](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a><span data-ttu-id="e8f24-313">Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="e8f24-313">Oculus Quest</span></span>

<span data-ttu-id="e8f24-314">현재 독립 실행형 플랫폼을 대상으로 할 [때 와 함께 Oculus XR 플러그 인을](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)사용하는 경우 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-314">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span> <span data-ttu-id="e8f24-315">업데이트에 대한 Oculus 버그 추적기/포럼/릴리스 노트를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-315">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="e8f24-316">버그는 다음과 같은 3가지 오류 집합으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-316">The bug is signified with this set of 3 errors:</span></span>

![Oculus XR 플러그 인 오류](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="e8f24-318">UnityUI 및 TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="e8f24-318">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="e8f24-319">드롭다운 및 굵은 글꼴 문자 간격의 기본 글꼴 크기가 변경된 최신 버전의 TextMeshPro(1.5.0 이상 또는 2.1.1 이상)에 대해 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-319">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![TMP 이미지](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="e8f24-321">이 작업은 이전 버전의 TextMeshPro로 다운그레이드하여 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8f24-321">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="e8f24-322">자세한 내용은 [문제 #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8f24-322">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>
