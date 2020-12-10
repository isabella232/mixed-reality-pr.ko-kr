---
title: Unity 및 Visual Studio 사용 모범 사례
description: Unity 및 Visual Studio를 사용 하 여 혼합 현실 응용 프로그램을 만드는 워크플로를 간소화 하기 위한 팁과 요령.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 배포, unity, visual studio, HoloLens, HoloLens 2, 모던 헤드셋, 모범 사례, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, UWP, Visual Studio Tools Windows SDK
ms.openlocfilehash: 9e80cad3e7154ae5548514297343db8efcdcb49e
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010264"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a><span data-ttu-id="1ace0-104">Unity 및 Visual Studio 사용 모범 사례</span><span class="sxs-lookup"><span data-stu-id="1ace0-104">Best practices for working with Unity and Visual Studio</span></span>

<span data-ttu-id="1ace0-105">Unity를 사용 하 여 혼합 현실 응용 프로그램을 만드는 경우 앱 패키지를 빌드하고 HoloLens 헤드셋에 배포 하려면 Unity와 Visual Studio 사이를 전환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-105">When you're creating a mixed reality application with Unity, you need to switch between Unity and Visual Studio to build and deploy the app package to HoloLens or an immersive headset.</span></span> <span data-ttu-id="1ace0-106">기본적으로 Visual Studio의 두 인스턴스는 Unity 스크립트를 수정 하 고 다른 하나는 장치에 배포 하 고 디버그 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-106">By default, two instances of Visual Studio are required - one instance to modify Unity scripts and another to deploy to the device and debug.</span></span> <span data-ttu-id="1ace0-107">다음 지침에 따라 단일 Visual Studio 인스턴스를 사용 하 여 Unity 프로젝트를 내보내는 빈도를 줄이고 디버깅 환경을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-107">The following instructions let you develop using a single Visual Studio instance, reducing the frequency of exporting Unity projects and improves the debugging experience.</span></span>

## <a name="improving-iteration-time"></a><span data-ttu-id="1ace0-108">반복 시간 향상</span><span class="sxs-lookup"><span data-stu-id="1ace0-108">Improving iteration time</span></span>

<span data-ttu-id="1ace0-109">Unity의 .NET scripting 백 엔드 지원은 Unity 2018에서 더 이상 사용 되지 않으며 Unity 2019 이상에서 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-109">Support for .NET scripting back-end in Unity is being deprecated in Unity 2018 and removed in Unity 2019+.</span></span> <span data-ttu-id="1ace0-110">따라서 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)로 전환 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-110">so we recommend you switch to [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html).</span></span> <span data-ttu-id="1ace0-111">그러나 Unity에서 Visual Studio로 빌드 시간이 길어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-111">However, you may experience longer build times from Unity to Visual Studio.</span></span> <span data-ttu-id="1ace0-112">더 빠른 반복을 위해 환경을 개선 하려면 최상의 컴파일 결과를 위해 환경을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-112">To improve for faster iteration, set up your environment for best compilation results:</span></span>

1) <span data-ttu-id="1ace0-113">매번 동일한 디렉터리에 프로젝트를 빌드하여 증분 빌드를 사용 하 여 미리 작성 된 파일을 다시 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-113">Use incremental building by building your project to the same directory every time, reusing the pre-built files there</span></span>
2) <span data-ttu-id="1ace0-114">프로젝트에 대 한 맬웨어 방지 소프트웨어 검색 사용 안 함 & 빌드 폴더</span><span class="sxs-lookup"><span data-stu-id="1ace0-114">Disable anti-malware software scans for your project & build folders</span></span>
   - <span data-ttu-id="1ace0-115">Windows 10 설정 앱에서 **바이러스 & 위협 방지** 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-115">Open **Virus & threat protection** under your Windows 10 settings app</span></span>
   - <span data-ttu-id="1ace0-116">**바이러스 & 위협 방지 설정** 에서 **설정 관리** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-116">Select **Manage Settings** under **Virus & threat protection settings**</span></span>
   - <span data-ttu-id="1ace0-117">**제외** 섹션에서 **제외 추가 또는 제거** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-117">Select **Add or remove exclusions** under the **Exclusions** section</span></span>
   - <span data-ttu-id="1ace0-118">**제외 추가** 를 선택 하 고 Unity 프로젝트 코드 및 빌드 출력을 포함 하는 폴더를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-118">Select **Add an exclusion** and select the folder containing your Unity project code and build outputs</span></span>
3) <span data-ttu-id="1ace0-119">빌드에 SSD 사용</span><span class="sxs-lookup"><span data-stu-id="1ace0-119">Use an SSD for building</span></span>

<span data-ttu-id="1ace0-120">자세한 정보는 [IL2CPP에 대 한 빌드 시간 최적화](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 를 검토 하세요.</span><span class="sxs-lookup"><span data-stu-id="1ace0-120">Review [Optimizing Build Times for IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) for more info.</span></span> <span data-ttu-id="1ace0-121">또한 [IL2CPP Scripting 백 엔드에서 디버깅](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-121">Also, review [Debugging on IL2CPP Scripting Back-end](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).</span></span>

<span data-ttu-id="1ace0-122">[ *Unityscriptanalyzer* Visual Studio 확장](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)을 설치 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-122">Consider installing the [*UnityScriptAnalyzer* Visual Studio extension](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer).</span></span> <span data-ttu-id="1ace0-123">이 도구는 더 최적화 된 방식으로 작성할 수 있는 코드에 대 한 Unity c # 스크립트를 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-123">This tool analyzes your Unity C# scripts for code that can be written in a more optimized manner.</span></span>

## <a name="visual-studio-tools-for-unity"></a><span data-ttu-id="1ace0-124">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="1ace0-124">Visual Studio Tools for Unity</span></span>

<span data-ttu-id="1ace0-125">다운로드 [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)</span><span class="sxs-lookup"><span data-stu-id="1ace0-125">Download [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)</span></span>

<span data-ttu-id="1ace0-126">**Visual Studio Tools for Unity의 이점**</span><span class="sxs-lookup"><span data-stu-id="1ace0-126">**Benefits of Visual Studio Tools for Unity**</span></span>
* <span data-ttu-id="1ace0-127">중단점을 배치 하 고 변수와 복잡 한 식을 평가 하 여 Visual Studio에서 Unity의 편집기 내 재생 모드를 디버그 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-127">Debug Unity in-editor play mode from Visual Studio by putting breakpoints, evaluating variables and complex expressions.</span></span>
* <span data-ttu-id="1ace0-128">Unity 프로젝트 탐색기를 사용 하 여 Unity에서 표시 하는 것과 정확히 동일한 계층 구조를 사용 하 여 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-128">Use the Unity Project Explorer to find your script with the exact same hierarchy that Unity displays.</span></span>
* <span data-ttu-id="1ace0-129">Visual Studio 내에서 직접 Unity 콘솔을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-129">Get the Unity console directly inside Visual Studio.</span></span>
* <span data-ttu-id="1ace0-130">마법사를 사용 하 여 신속 하 게 스크립트를 만들거나 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-130">Use wizards to quickly create or navigate to scripts.</span></span>

## <a name="expose-c-class-variables-for-easy-tuning"></a><span data-ttu-id="1ace0-131">간편한 조정을 위해 c # 클래스 변수 노출</span><span class="sxs-lookup"><span data-stu-id="1ace0-131">Expose C# class variables for easy tuning</span></span>

<span data-ttu-id="1ace0-132">클래스 변수를 노출 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-132">There are two ways to expose class variables.</span></span> <span data-ttu-id="1ace0-133">[SerializeField] 특성을 전용 변수에 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-133">The recommended way is to add the [SerializeField] attribute to your private variables.</span></span> <span data-ttu-id="1ace0-134">Serialize 된 필드는 편집기에서 액세스할 수 있지만 프로그래밍 방식으로 노출 되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-134">Serialized fields can be accessed from the editor but not programmatically exposed.</span></span>  <span data-ttu-id="1ace0-135">다른 옵션은 c # 클래스 변수를 공용으로 설정 하 여 편집기 UI에이를 노출 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-135">The other option is to make C# class variables public to expose them in the editor UI.</span></span> 

<span data-ttu-id="1ace0-136">두 방법 모두 편집기에서 재생 하는 동안 변수를 쉽게 수정할 수 있습니다 .이는 상호 작용 정비공 속성을 튜닝 하는 데 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-136">Both approaches make it possible to easily tweak variables while playing in-editor, which is especially useful for tuning interaction mechanic properties.</span></span>

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a><span data-ttu-id="1ace0-137">Windows SDK 또는 Unity 업그레이드 후 UWP Visual Studio 솔루션 다시 생성</span><span class="sxs-lookup"><span data-stu-id="1ace0-137">Regenerate UWP Visual Studio solutions after Windows SDK or Unity upgrade</span></span>

<span data-ttu-id="1ace0-138">UWP Visual Studio 솔루션을 소스 제어에 체크 인 하면 새 Windows SDK 또는 Unity 엔진으로 업그레이드 한 후에 만료 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-138">UWP Visual Studio solutions checked in to source control can get out-of-date after upgrading to a new Windows SDK or Unity engine.</span></span> <span data-ttu-id="1ace0-139">Unity에서 새 UWP 솔루션을 빌드하고 체크 인 된 솔루션에 대 한 차이점을 병합 하 여 오래 된 솔루션을 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-139">You can resolve out-of-date solutions after by building a new UWP solution from Unity and merging differences into the checked-in solution.</span></span>

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a><span data-ttu-id="1ace0-140">텍스트 형식 자산을 사용 하 여 콘텐츠 변경 내용 비교</span><span class="sxs-lookup"><span data-stu-id="1ace0-140">Use text-format assets for easy comparison of content changes</span></span>

<span data-ttu-id="1ace0-141">자산을 텍스트 형식으로 저장 하면 Visual Studio에서 콘텐츠 변경 차이을 보다 쉽게 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-141">Storing assets in text format makes it easier to review content change diffs in Visual Studio.</span></span> <span data-ttu-id="1ace0-142">**편집 > 프로젝트 설정 > 편집기** 를 선택 하 여 자산을 텍스트 형식으로 저장 하 고, **강제로 텍스트** 를 변경 하 여 **자산 Serialization** 모드를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-142">You can store assets in text format by selecting **Edit > Project Settings > Editor** and change **Asset Serialization** mode to **Force Text**.</span></span> <span data-ttu-id="1ace0-143">그러나 텍스트 자산 파일 변경 내용을 병합 하는 것은 오류가 발생 하기 쉬우며 권장 되지 않으므로 소스 제어에서 단독 이진 체크 아웃을 사용 하도록 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1ace0-143">However, merging text asset file changes is error-prone and not recommended, so consider enabling exclusive binary checkouts in your source control.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ace0-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ace0-144">See also</span></span>
- [<span data-ttu-id="1ace0-145">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="1ace0-145">Visual Studio Tools for Unity</span></span>](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [<span data-ttu-id="1ace0-146">IL2CPP에 대 한 빌드 시간 최적화</span><span class="sxs-lookup"><span data-stu-id="1ace0-146">Optimizing Build Times for IL2CPP</span></span>](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [<span data-ttu-id="1ace0-147">*Unityscriptanalyzer* Visual Studio 확장</span><span class="sxs-lookup"><span data-stu-id="1ace0-147">*UnityScriptAnalyzer* Visual Studio extension</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)
