---
title: 장면 이해 SDK
description: 혼합 현실 앱에서 구성 요소, 메시 및 개체를 포함 하 여 장면 이해 SDK를 설치 하 고 사용 하는 방법에 대해 알아봅니다.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: 장면 이해, 공간 매핑, Windows Mixed Reality, Unity
ms.openlocfilehash: 9520ad604125705c60624254b097de5fc93021ec
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009383"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="63fd3-104">장면 이해 SDK 개요</span><span class="sxs-lookup"><span data-stu-id="63fd3-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="63fd3-105">장면 이해는 혼합 현실 장치에서 캡처하는 비구조적 환경 센서 데이터를 변환 하 고 강력한 추상 표현으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-105">Scene understanding transforms the unstructured environment sensor data that your Mixed Reality device captures and converts it into a powerful abstract representation.</span></span> <span data-ttu-id="63fd3-106">SDK는 응용 프로그램과 장면 이해 런타임의 통신 계층으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="63fd3-107">3D 표시를 위한 3D 장면 그래프, 2D 응용 프로그램의 경우 2D 사각형 및 패널과 같은 기존 표준 구문을 모방 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-107">It's aimed to mimic existing standard constructs, such as 3D scene graphs for 3D representations, and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="63fd3-108">구성 장면 이해를 모방 하는 것은 구체적인 프레임 워크에 매핑되므로 일반적인 SceneUnderstanding은 프레임 워크와 상호 작용 하는 다양 한 프레임 워크 간의 상호 운용성을 허용 하는 프레임 워크를 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-108">While the constructs Scene Understanding mimics will map to concrete frameworks, in general SceneUnderstanding is framework agnostic allowing for interoperability between varied frameworks that interact with it.</span></span> <span data-ttu-id="63fd3-109">장면 이해는 SDK의 역할을 발전 시킬 때 새로운 표현과 기능이 통합 프레임 워크 내에서 계속 노출 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="63fd3-110">이 문서에서는 먼저 개발 환경/사용법을 파악 하는 데 도움이 되는 개략적인 개념을 소개 하 고 특정 클래스 및 구문에 대 한 자세한 설명서를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-110">In this document, we will first introduce high-level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="63fd3-111">SDK는 어디에서 얻을 까 요?</span><span class="sxs-lookup"><span data-stu-id="63fd3-111">Where do I get the SDK?</span></span>

<span data-ttu-id="63fd3-112">SceneUnderstanding SDK는 NuGet을 통해 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="63fd3-113">SceneUnderstanding SDK</span><span class="sxs-lookup"><span data-stu-id="63fd3-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="63fd3-114">**참고:** 최신 릴리스는 미리 보기 패키지에 의존 하므로 시험판 패키지를 사용 하도록 설정 하 여 해당 릴리스를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-114">**Note:** the latest release depends on preview packages and you'll need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="63fd3-115">버전 0.5.2022 이상에서, 장면 이해는 c # 및 c + +에 대 한 언어 프로젝션을 지원 하 여 응용 프로그램에서 Win32 또는 UWP 플랫폼용 응용 프로그램을 개발할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-115">For version 0.5.2022-rc and later, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="63fd3-116">이 버전부터 SceneUnderstanding는 HoloLens2와의 통신에만 사용 되는 SceneObserver를 제한 하는 unity의 unity 지원 기능을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver, which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="63fd3-117">SceneUnderstanding에 Windows SDK 버전 18362 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="63fd3-118">Unity 프로젝트에서 SDK를 사용 하는 경우 [unity 용 NuGet](https://github.com/GlitchEnzo/NuGetForUnity) 을 사용 하 여 프로젝트에 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-118">If you're using the SDK in a Unity project, use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="63fd3-119">개념적 개요</span><span class="sxs-lookup"><span data-stu-id="63fd3-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="63fd3-120">장면</span><span class="sxs-lookup"><span data-stu-id="63fd3-120">The Scene</span></span>

<span data-ttu-id="63fd3-121">혼합 현실 장치는 환경에서 표시 되는 내용에 대 한 정보를 지속적으로 통합 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="63fd3-122">장면 이해는 이러한 모든 데이터 원본을 funnels 하나의 단일 단일 추상화를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="63fd3-123">장면 이해는 단일 항목의 인스턴스를 나타내는 [SceneObjects](scene-understanding-SDK.md#sceneobjects) 의 컴퍼지션 인 장면을 생성 합니다 (예: 벽/천장/바닥). 장면 개체 자체는이 SceneObject을 구성 하는 더 세분화 된 부분을 나타내는 [SceneComponents의 컴퍼지션입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-123">Scene Understanding generates Scenes, which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (for example, a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents, which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="63fd3-124">구성 요소의 예는 quads 및 메시 이지만 나중에 경계 상자, 충돌 망, 메타 데이터 등을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc.</span></span>

<span data-ttu-id="63fd3-125">원시 센서 데이터를 장면으로 변환 하는 프로세스는 보통 공간 (~ 50x50m)에 대해 보통 공간 (~ 10x10m)에서 몇 분이 걸릴 수 있으며, 따라서 응용 프로그램 요청 없이 장치에서 계산 되는 항목이 아닌 경우에 따라 비용이 많이 드는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="63fd3-126">대신, 요청 시 응용 프로그램에서 장면 생성이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="63fd3-127">SceneObserver 클래스에는 장면을 계산 하거나 Deserialize 할 수 있는 정적 메서드가 있습니다. 그러면이를 열거/상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="63fd3-128">"Compute" 작업은 요청 시 실행 되며 CPU에서 실행 되지만 별도의 프로세스 (혼합 현실 드라이버)에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="63fd3-129">그러나 다른 프로세스에서 계산을 수행 하는 동안 결과 장면 데이터는 응용 프로그램에서 장면 개체에 저장 되 고 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="63fd3-130">다음은이 프로세스 흐름을 보여 주고 장면 이해 런타임과 상호 작용 하는 두 개의 응용 프로그램 예제를 보여 주는 다이어그램입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![프로세스 다이어그램](images/SU-ProcessFlow.png)

<span data-ttu-id="63fd3-132">왼쪽에는 항상 자체 프로세스에서 실행 되 고 실행 되는 혼합 현실 런타임의 다이어그램이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-132">On the left-hand side is a diagram of the mixed reality runtime, which is always on and running in its own process.</span></span> <span data-ttu-id="63fd3-133">이 런타임은 장치 추적, 공간 매핑 및 전 세계의 이해를 위해 장면에서 이해 하는 기타 작업을 수행 하는 작업을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="63fd3-134">다이어그램의 오른쪽에는 장면 이해를 활용 하는 두 개의 이론적인 응용 프로그램이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="63fd3-135">첫 번째 응용 프로그램은 내부적으로 장면 이해 SDK를 사용 하는 MRTK를 사용 하 여 두 번째 앱은 별도의 두 장면 인스턴스를 계산 하 고 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-135">The first application interfaces with MRTK, which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="63fd3-136">이 다이어그램의 세 가지 장면은 모두 백그라운드의 개별 인스턴스를 생성 합니다. 드라이버는 한 장면의 응용 프로그램과 장면 개체 간에 공유 되는 전역 상태를 추적 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-136">All three Scenes in this diagram generate distinct instances of the scenes, the driver isn't tracking global state that is shared between applications and Scene Objects in one scene aren't found in another.</span></span> <span data-ttu-id="63fd3-137">장면 이해는 시간에 따라 추적 하는 메커니즘을 제공 하지만 SDK를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK.</span></span> <span data-ttu-id="63fd3-138">앱 프로세스의 SDK에서 추적 코드가 이미 실행 되 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-138">Tracking code is already running in the SDK in your app's process.</span></span>

<span data-ttu-id="63fd3-139">각 장면은 응용 프로그램의 메모리 공간에 해당 데이터를 저장 하기 때문에 장면 개체의 모든 기능 또는 내부 데이터가 항상 응용 프로그램의 프로세스에서 실행 된다고 가정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-139">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="63fd3-140">레이아웃</span><span class="sxs-lookup"><span data-stu-id="63fd3-140">Layout</span></span>

<span data-ttu-id="63fd3-141">장면 이해를 사용 하려면 런타임이 구성 요소를 논리적 및 물리적으로 표시 하는 방법을 알고 이해 하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-141">To work with Scene Understanding, it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="63fd3-142">장면은 주요 수정이 필요 하지 않고 미래의 요구 사항을 충족 하는 pliable 기본 구조를 유지 하면서 간단 하 게 선택 된 특정 레이아웃을 가진 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-142">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="63fd3-143">장면에서는 모든 구성 요소 (모든 장면 개체의 빌딩 블록)를 단순 목록에 저장 하 고 특정 구성 요소가 다른 항목을 참조 하는 참조를 통해 계층 구조와 컴퍼지션을 정의 하 여이를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-143">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="63fd3-144">아래에서는 플랫 및 논리적 형식으로 된 구조의 예를 보여 주고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-144">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="63fd3-145">논리적 레이아웃</span><span class="sxs-lookup"><span data-stu-id="63fd3-145">Logical Layout</span></span></th><th><span data-ttu-id="63fd3-146">물리적 레이아웃</span><span class="sxs-lookup"><span data-stu-id="63fd3-146">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="63fd3-147">장면</span><span class="sxs-lookup"><span data-stu-id="63fd3-147">Scene</span></span>
  <ul>
  <li><span data-ttu-id="63fd3-148">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="63fd3-148">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="63fd3-149">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="63fd3-149">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="63fd3-150">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="63fd3-150">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="63fd3-151">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="63fd3-151">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="63fd3-152">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="63fd3-152">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="63fd3-153">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="63fd3-153">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="63fd3-154">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="63fd3-154">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="63fd3-155">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="63fd3-155">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="63fd3-156">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="63fd3-156">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="63fd3-157">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="63fd3-157">SceneObject_1</span></span></li>
  <li><span data-ttu-id="63fd3-158">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="63fd3-158">SceneObject_2</span></span></li>
  <li><span data-ttu-id="63fd3-159">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="63fd3-159">SceneObject_3</span></span></li>
  <li><span data-ttu-id="63fd3-160">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="63fd3-160">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="63fd3-161">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="63fd3-161">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="63fd3-162">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="63fd3-162">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="63fd3-163">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="63fd3-163">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="63fd3-164">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="63fd3-164">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="63fd3-165">이 그림에서는 장면의 물리적 레이아웃과 논리적 레이아웃 간의 차이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-165">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="63fd3-166">왼쪽에는 장면을 열거할 때 응용 프로그램에 표시 되는 데이터의 계층적 레이아웃이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-166">On the left, we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="63fd3-167">오른쪽에는 장면이 필요한 경우 개별적으로 액세스할 수 있는 12 개의 고유 구성 요소로 구성 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-167">On the right, we see that the scene is comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="63fd3-168">새 장면을 처리할 때 응용 프로그램이이 계층 구조를 논리적으로 탐색 하는 것이 좋지만, 장면 업데이트를 추적할 때 일부 응용 프로그램은 두 장면 간에 공유 되는 특정 구성 요소를 대상으로 하는 경우에만 관심이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-168">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="63fd3-169">API 개요</span><span class="sxs-lookup"><span data-stu-id="63fd3-169">API overview</span></span>

<span data-ttu-id="63fd3-170">다음 섹션에서는 장면 이해의 구문에 대 한 개략적인 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-170">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="63fd3-171">이 섹션을 읽으면 장면이 표시 되는 방법 및 다양 한 구성 요소를 사용 하는 방법에 대 한 이해를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-171">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="63fd3-172">다음 섹션에서는이 개요에서 달았습니다 구체적인 코드 예제 및 추가 세부 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-172">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="63fd3-173">아래에 설명 된 모든 형식은 `Microsoft.MixedReality.SceneUnderstanding` 네임 스페이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-173">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="63fd3-174">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="63fd3-174">SceneComponents</span></span>

<span data-ttu-id="63fd3-175">이제 배경의 논리적 레이아웃을 이해 했으므로 이제 SceneComponents의 개념과 계층 구조를 작성 하는 데 사용 되는 방법을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-175">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they're used to compose hierarchy.</span></span> <span data-ttu-id="63fd3-176">SceneComponents는 메시 또는 쿼드 또는 경계 상자와 같은 단일 핵심 항목을 나타내는 SceneUnderstanding의 가장 세분화 된 decompositions입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-176">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, for example, a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="63fd3-177">SceneComponents은 독립적으로 업데이트 될 수 있고 다른 SceneComponents에서 참조할 수 있는 항목입니다. 따라서이 유형의 추적/참조 메커니즘을 허용 하는 단일 전역 속성의 고유 ID가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-177">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique ID, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="63fd3-178">Id는 장면 계층의 논리적 컴퍼지션 뿐만 아니라 개체 지 속성 (한 장면을 다른 장면으로 업데이트 하는 동작)에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-178">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="63fd3-179">새로 계산 된 모든 장면을 고유 하 게 처리 하 고 그 안의 모든 데이터를 열거 하는 경우 Id는 주로 사용자에 게 투명 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-179">If you're treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="63fd3-180">그러나 여러 업데이트에 대 한 구성 요소를 추적 하려는 경우 Id를 사용 하 여 장면 개체 간 SceneComponents을 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-180">However, if you're planning to track components over several updates you'll use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="63fd3-181">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="63fd3-181">SceneObjects</span></span>

<span data-ttu-id="63fd3-182">SceneObject은 "사물" (예: 벽, 층, 천장 등)의 인스턴스를 나타내는 SceneComponent입니다. Kind 속성으로 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-182">A SceneObject is a SceneComponent that represents an instance of a "thing" for example, a wall, a floor, a ceiling, etc.... expressed by their Kind property.</span></span> <span data-ttu-id="63fd3-183">SceneObjects는 기 하 도형 이므로 공간에서 해당 위치를 나타내는 함수와 속성이 있지만 기하학적 또는 논리적 구조는 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-183">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="63fd3-184">대신, SceneObjects는 다른 SceneComponents, 특히 SceneQuads 및 SceneMeshes를 참조 하 여 시스템에서 지 원하는 다양 한 표현을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-184">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads, and SceneMeshes, which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="63fd3-185">새 장면을 계산 하면 응용 프로그램에서 관심 있는 항목을 처리 하는 장면의 SceneObjects을 열거 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-185">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="63fd3-186">SceneObjects에는 다음 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-186">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="63fd3-187">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="63fd3-187">SceneObjectKind</span></span></th> <th><span data-ttu-id="63fd3-188">설명</span><span class="sxs-lookup"><span data-stu-id="63fd3-188">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="63fd3-189">배경</span><span class="sxs-lookup"><span data-stu-id="63fd3-189">Background</span></span></td><td><span data-ttu-id="63fd3-190">SceneObject는 인식 되는 다른 종류의 장면 개체 중 하나가 <b>아닌</b> 것으로 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-190">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="63fd3-191">이 클래스는 배경을 벽/층/천장 등이 아닌 것으로 알려진 경우 알 수 없는와 혼동 해서는 안 됩니다. unknown은 아직 분류 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-191">This class shouldn't be confused with Unknown where Background is known not to be wall/floor/ceiling etc.... while unknown isn't yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="63fd3-192">벽</span><span class="sxs-lookup"><span data-stu-id="63fd3-192">Wall</span></span></td><td><span data-ttu-id="63fd3-193">실제 벽입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-193">A physical wall.</span></span> <span data-ttu-id="63fd3-194">벽은 불균형 환경 구조로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-194">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="63fd3-195">Floor</span><span class="sxs-lookup"><span data-stu-id="63fd3-195">Floor</span></span></td><td><span data-ttu-id="63fd3-196">바닥은 한 번에 진행할 수 있는 모든 표면입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-196">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="63fd3-197">참고: 계단은 층이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-197">Note: stairs aren't floors.</span></span> <span data-ttu-id="63fd3-198">또한 해당 층은 walkable 표면을 가정 하므로 단일 층을 명시적으로 가정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-198">Also note, that floors assume any walkable surface and therefore there's no explicit assumption of a singular floor.</span></span> <span data-ttu-id="63fd3-199">다중 수준 구조, 경사 등 ... 모두 바닥으로 분류 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-199">Multi-level structures, ramps etc.... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="63fd3-200">Ceiling</span><span class="sxs-lookup"><span data-stu-id="63fd3-200">Ceiling</span></span></td><td><span data-ttu-id="63fd3-201">방의 위쪽 표면입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-201">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="63fd3-202">플랫폼</span><span class="sxs-lookup"><span data-stu-id="63fd3-202">Platform</span></span></td><td><span data-ttu-id="63fd3-203">Holograms를 놓을 수 있는 커다란 플랫 표면입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-203">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="63fd3-204">이는 테이블, countertops 및 기타 넓은 가로 표면을 나타내는 경향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-204">These tend to represent tables, countertops, and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="63fd3-205">World</span><span class="sxs-lookup"><span data-stu-id="63fd3-205">World</span></span></td><td><span data-ttu-id="63fd3-206">레이블 지정과 무관 한 기하학적 데이터의 예약 된 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-206">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="63fd3-207">EnableWorldMesh 업데이트 플래그를 설정 하 여 생성 된 메시는 세계로 분류 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-207">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="63fd3-208">알 수 없음</span><span class="sxs-lookup"><span data-stu-id="63fd3-208">Unknown</span></span></td><td><span data-ttu-id="63fd3-209">이 장면 개체는 아직 분류 되어 있으며 종류를 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-209">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="63fd3-210">이 개체는 아무것도 될 수 있으므로 배경과 혼동 해서는 안 됩니다. 시스템은 아직 충분히 강력한 분류로 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-210">This shouldn't be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="63fd3-211">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="63fd3-211">SceneMesh</span></span>

<span data-ttu-id="63fd3-212">SceneMesh은 삼각형 목록을 사용 하 여 임의 기하학적 개체의 기 하 도형에 근사치를 주는 SceneComponent입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-212">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="63fd3-213">SceneMeshes는 여러 다른 컨텍스트에서 사용 되며, watertight 셀 구조의 구성 요소를 나타내거나 장면에 연결 된 바인딩되지 않은 공간 매핑 메시를 나타내는 WorldMesh로 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-213">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh, which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="63fd3-214">각 메시와 함께 제공 되는 인덱스 및 꼭 짓 점 데이터는 모든 최신 렌더링 Api에서 삼각형 메시를 렌더링 하는 데 사용 되는 [꼭 짓 점 및 인덱스 버퍼](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) 와 동일한 익숙한 레이아웃을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-214">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="63fd3-215">장면 이해에서 메시는 32 비트 인덱스를 사용 하며 특정 렌더링 엔진에 대 한 청크로 분할 되어야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-215">In Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="63fd3-216">권선 순서 및 좌표계</span><span class="sxs-lookup"><span data-stu-id="63fd3-216">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="63fd3-217">장면 이해로 생성 된 모든 메시는 시계 방향 권선 순서를 사용 하 여 Right-Handed 좌표계에서 메시를 반환할 것으로 예상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-217">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="63fd3-218">참고: 191105 이전 OS 빌드에는 "세계" 메시가 이후에 수정 된 Counter-Clockwise 권선 순서로 반환 되는 알려진 버그가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-218">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="63fd3-219">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="63fd3-219">SceneQuad</span></span>

<span data-ttu-id="63fd3-220">SceneQuad는 3d 세계를 차지 하는 2d 표면을 나타내는 SceneComponent입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-220">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="63fd3-221">SceneQuads는 ARKit Arkit Eanchor 또는 Arkit 평면과 유사 하 게 사용할 수 있지만, 플랫 앱 또는 확대 된 UX에서 사용할 2d canvas로 더 높은 수준의 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-221">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high-level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="63fd3-222">quads에 대 한 2D 특정 Api가 제공 되어 배치 및 레이아웃을 간단 하 게 사용할 수 있으며, quads를 사용 하 여 개발 (렌더링 제외)을 개발 하는 것은 3d 메시 보다 2d 캔버스 작업에 더 유사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-222">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="63fd3-223">SceneQuad 셰이프</span><span class="sxs-lookup"><span data-stu-id="63fd3-223">SceneQuad shape</span></span>

<span data-ttu-id="63fd3-224">SceneQuads는 2d에서 경계가 지정 된 사각형 표면을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-224">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="63fd3-225">그러나 SceneQuads는 임의의 잠재적으로 복잡 한 모양 (예: 도넛형 모양의 표)을 포함 하는 표면을 나타냅니다. 쿼드 표면의 복합 셰이프를 나타내려면 GetSurfaceMask API를 사용 하 여 표면의 셰이프를 제공 된 이미지 버퍼에 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-225">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="63fd3-226">쿼드를 포함 하는 SceneObject에도 메쉬가 있으면 망상 삼각형은 렌더링 된 이미지와 동일 해야 하며, 둘 다 2d 또는 3d 좌표에서 표면의 실제 기 하 도형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-226">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="63fd3-227">SDK 세부 정보 및 참조 장면 이해</span><span class="sxs-lookup"><span data-stu-id="63fd3-227">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="63fd3-228">다음 섹션에서는 SceneUnderstanding의 기본 사항에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-228">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="63fd3-229">이 섹션에서는 SceneUnderstanding를 사용 하는 방법을 확인 하기 위해 샘플 응용 프로그램을 탐색 하는 데 충분 한 컨텍스트를 제공 해야 하는 기본 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-229">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="63fd3-230">초기화</span><span class="sxs-lookup"><span data-stu-id="63fd3-230">Initialization</span></span>

<span data-ttu-id="63fd3-231">SceneUnderstanding를 사용 하는 첫 번째 단계는 응용 프로그램에서 장면 개체에 대 한 참조를 얻는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-231">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="63fd3-232">이 작업은 두 가지 방법 중 하나로 수행할 수 있습니다. 즉, 드라이버에서 장면을 계산 하거나 과거에 계산 된 기존 장면을 deserialize 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-232">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="63fd3-233">후자는 혼합 현실 장치 없이 응용 프로그램 및 환경을 빠르게 프로토타입화 할 수 있는 개발 중 SceneUnderstanding 작업에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-233">The latter is useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="63fd3-234">SceneObserver를 사용 하 여 장면을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-234">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="63fd3-235">장면을 만들기 전에 응용 프로그램은 SceneUnderstanding를 지원 하는지 확인 하 고 SceneUnderstanding에 필요한 정보에 대 한 사용자 액세스를 요청할 수 있도록 장치를 쿼리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-235">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="63fd3-236">RequestAccessAsync ()를 호출 하지 않으면 새 장면을 계산 하는 작업이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-236">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="63fd3-237">다음으로는 혼합 현실 헤드셋을 기반으로 하는 새 장면을 계산 하 고 10 미터 반지름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-237">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10-meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a><span data-ttu-id="63fd3-238">데이터에서 초기화 (라고도 함)</span><span class="sxs-lookup"><span data-stu-id="63fd3-238">Initialization from Data (also known as.</span></span> <span data-ttu-id="63fd3-239">PC 경로)</span><span class="sxs-lookup"><span data-stu-id="63fd3-239">the PC Path)</span></span>

<span data-ttu-id="63fd3-240">직접 소비를 위해 장면을 계산할 수 있지만 나중에 사용할 수 있도록 serialize 된 형식으로 계산 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-240">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="63fd3-241">이는 개발자가 장치 없이 작업을 수행 하 고 장면 이해를 테스트할 수 있게 해 주는 개발에 유용한 것으로 입증 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-241">This has proven to be useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="63fd3-242">장면을 직렬화 하는 작업은 응용 프로그램에 의해 로컬에서 deserialize 되는 대신 응용 프로그램에 반환 되는 것과 거의 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-242">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="63fd3-243">사용자는 직접 deserialize 하거나 나중에 사용할 수 있도록 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-243">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="63fd3-244">SceneObject 열거형</span><span class="sxs-lookup"><span data-stu-id="63fd3-244">SceneObject Enumeration</span></span>

<span data-ttu-id="63fd3-245">이제 응용 프로그램에 장면이 있으므로 응용 프로그램은 SceneObjects를 보고 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-245">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="63fd3-246">**SceneObjects** 속성에 액세스 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-246">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a><span data-ttu-id="63fd3-247">구성 요소 업데이트 및 refinding 구성 요소</span><span class="sxs-lookup"><span data-stu-id="63fd3-247">Component update and refinding components</span></span>

<span data-ttu-id="63fd3-248">\**_FindComponent_* _ 라는 장면에서 구성 요소를 검색 하는 다른 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-248">There's another function that retrieves components in the Scene called \**_FindComponent_* _.</span></span> <span data-ttu-id="63fd3-249">이 함수는 추적 개체를 업데이트 하 고 나중에 백그라운드에서 찾을 때 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-249">This function is useful when updating tracking objects and finding them in later scenes.</span></span> <span data-ttu-id="63fd3-250">다음 코드는 이전 장면을 기준으로 새 장면을 계산 하 고 새 장면에서 바닥을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-250">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="63fd3-251">장면 개체에서 메시 및 Quads 액세스</span><span class="sxs-lookup"><span data-stu-id="63fd3-251">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="63fd3-252">SceneObjects 발견 되 면 응용 프로그램은 구성 된 quads/메시에 포함 된 데이터에 액세스 하려고 할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-252">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is composed of.</span></span> <span data-ttu-id="63fd3-253">이 데이터는 _*_Quads_*_ 및 _\*_메시_\*_ 속성을 사용 하 여 액세스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-253">This data is accessed with the _*_Quads_*_ and _*_Meshes_*_ properties.</span></span> <span data-ttu-id="63fd3-254">다음 코드는 floor 개체의 모든 quads 및 메시를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-254">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="63fd3-255">이는 장면 원점에 상대적인 변환을 포함 하는 SceneObject입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-255">Notice that it's the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="63fd3-256">이는 SceneObject가 "사물"의 인스턴스를 나타내므로 공간에 과정이, quads 및 망상은 부모를 기준으로 변환 되는 기 하 도형을 나타낸다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-256">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads, and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="63fd3-257">별도의 SceneObjects가 동일한 SceneMesh/SceneQuad SceneComponents를 참조할 수 있으며 SceneObject에 두 개 이상의 SceneMesh/SceneQuad가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-257">It's possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it's also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="63fd3-258">변형 처리</span><span class="sxs-lookup"><span data-stu-id="63fd3-258">Dealing with Transforms</span></span>

<span data-ttu-id="63fd3-259">장면 이해는 변환을 처리할 때 일반적인 3D 장면 표현과 맞추는 시도를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-259">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="63fd3-260">따라서 각 장면은 가장 일반적인 3D 환경 표현과 마찬가지로 단일 좌표계로 한정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-260">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="63fd3-261">SceneObjects는 각 좌표계에 상대적인 위치를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-261">SceneObjects each provide their location relative to that coordinate system.</span></span> <span data-ttu-id="63fd3-262">응용 프로그램이 단일 원본에서 제공 하는 것의 제한을 스트레치 하는 장면을 처리 하는 경우 SpatialAnchors에 SceneObjects을 고정 하거나 여러 개의 장면을 생성 하 고 함께 병합할 수 있습니다. 하지만 간단 하 게 하기 위해에 의해 정의 된 하나의 NodeId로 지역화 된 자체 원본에 watertight 장면이 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-262">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="63fd3-263">예를 들어 다음 Unity 코드는 Windows 인식 및 Unity Api를 사용 하 여 좌표계를 함께 맞추는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-263">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="63fd3-264">Unity의 세계 원본에 해당 하는 SpatialCoordinateSystem를 가져오는 방법에 대 한 자세한 내용은 [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) 및 [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) 에서 Windows 인식 api 및 [혼합 현실 네이티브 개체](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) 에 대 한 자세한 내용을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="63fd3-264">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin.</span></span>

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

<span data-ttu-id="63fd3-265">각 `SceneObject` 에는 해당 개체에 적용 되는 변환이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-265">Each `SceneObject` has a transform, which is then applied to that object.</span></span> <span data-ttu-id="63fd3-266">Unity에서 다음과 같이 올바른 전달 좌표로 변환 하 고 로컬 변환을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-266">In Unity we convert to right handed coordinates and assign local transforms as so:</span></span>

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a><span data-ttu-id="63fd3-267">Led</span><span class="sxs-lookup"><span data-stu-id="63fd3-267">Quad</span></span>

<span data-ttu-id="63fd3-268">Quads는 2D 배치 시나리오를 지원 하도록 설계 되었으며 2D canvas UX 요소에 대 한 확장으로 간주 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-268">Quads were designed to help 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="63fd3-269">Quads는 SceneObjects의 구성 요소이 고 3D로 렌더링 될 수 있지만 쿼드 Api 자체는 Quads이 2D 구조인 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-269">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="63fd3-270">익스텐트, 모양, 배치를 위한 Api 제공 등의 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-270">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="63fd3-271">Quads는 사각형 범위를 갖지만 임의의 모양의 2D 표면을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-271">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="63fd3-272">3D 환경 quads와 상호 작용 하는 이러한 2D 표면에서 배치를 사용 하도록 설정 하려면 이러한 상호 작용을 가능 하 게 하는 유틸리티를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-272">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="63fd3-273">현재 장면 이해에서는 _ *Findcentermostplacement*\* 및 **GetSurfaceMask** 와 같은 두 가지 함수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-273">Currently Scene Understanding provides two such functions, _ *FindCentermostPlacement*\* and **GetSurfaceMask**.</span></span> <span data-ttu-id="63fd3-274">FindCentermostPlacement는 개체를 배치할 수 있는 쿼드 위치를 찾고 개체에 가장 적합 한 위치를 찾으려고 시도 하는 상위 수준의 API로, 사용자가 제공 하는 경계 상자가 기본 화면에 유지 되도록 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-274">FindCentermostPlacement is a high-level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will stay on the underlying surface.</span></span>

> [!NOTE]
> <span data-ttu-id="63fd3-275">출력의 좌표는 다른 windows Rect 형식에 있는 것 처럼 (x = 0, y = 0) 왼쪽 위 모퉁이가 있는 "쿼드 공간"의 쿼드에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-275">The coordinates of the output are relative to the quad in "quad space" with the top left corner being (x = 0, y = 0), just as it would be with other windows Rect types.</span></span> <span data-ttu-id="63fd3-276">사용자 고유의 개체의 원본으로 작업할 때는이를 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-276">Be sure to take this into account when working with the origins of your own objects.</span></span> 

<span data-ttu-id="63fd3-277">다음 예에서는 가장 높은 배치 가능한 위치를 찾고 4 번째에 홀로그램을 고정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-277">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="63fd3-278">1-4 단계는 특정 프레임 워크/구현에 따라 달라 지지만 테마는 유사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-278">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="63fd3-279">4는 단지 공간에서 지역화 된 경계가 있는 2D 평면을 나타내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-279">It's important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="63fd3-280">엔진/프레임 워크에서 쿼드이 무엇 인지 확인 하 고 쿼드을 기준으로 개체를 루 팅 하면 holograms는 실제 세계와 관련 하 여 정확 하 게 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-280">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a><span data-ttu-id="63fd3-281">메시</span><span class="sxs-lookup"><span data-stu-id="63fd3-281">Mesh</span></span>

<span data-ttu-id="63fd3-282">메시는 개체 또는 환경의 기하학적 표현을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-282">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="63fd3-283">[공간 매핑](../../design/spatial-mapping.md), 메시 인덱스 및 각 공간 표면 메시와 함께 제공 되는 꼭 짓 점 데이터는 모든 최신 렌더링 api에서 삼각형 메시 렌더링에 사용 되는 꼭 짓 점 및 인덱스 버퍼와 동일한 친숙 한 레이아웃을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-283">Much like [spatial mapping](../../design/spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="63fd3-284">꼭 짓 점 위치는의 좌표계에서 제공 됩니다 `Scene` .</span><span class="sxs-lookup"><span data-stu-id="63fd3-284">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="63fd3-285">이 데이터를 참조 하는 데 사용 되는 특정 Api는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-285">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="63fd3-286">다음 코드에서는 메시 구조에서 삼각형 목록을 생성 하는 예제를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-286">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="63fd3-287">인덱스/꼭 짓 점 버퍼는 인덱스/꼭 짓 점 수를 >해야 합니다. 그렇지 않으면 효율적인 메모리 재사용을 허용 하는 크기를 임의로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-287">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory reuse.</span></span>

### <a name="collidermesh"></a><span data-ttu-id="63fd3-288">ColliderMesh</span><span class="sxs-lookup"><span data-stu-id="63fd3-288">ColliderMesh</span></span>

<span data-ttu-id="63fd3-289">장면 개체는 메시 및 ColliderMeshes 속성을 통해 메시 및 collider 메시 데이터에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-289">Scene objects provide access to mesh and collider mesh data via the Meshes and ColliderMeshes properties.</span></span> <span data-ttu-id="63fd3-290">이러한 메시는 항상 일치 합니다. 즉, 메시 속성의 i'th 인덱스가 ColliderMeshes 속성의 i'th 인덱스와 동일한 기 하 도형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-290">These meshes will always match, meaning that the i'th index of the Meshes property represents the same geometry as the i'th index of the ColliderMeshes property.</span></span> <span data-ttu-id="63fd3-291">런타임/개체가 collider 메시를 지 원하는 경우, 응용 프로그램에서 colliders를 사용 하는 모든 위치에서 ColliderMeshes를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-291">If the runtime/object supports collider meshes, you are guaranteed to get the lowest polygon, highest order approximation and it's good practice to use ColliderMeshes wherever your application would use colliders.</span></span> <span data-ttu-id="63fd3-292">시스템에서 colliders을 지원 하지 않는 경우 ColliderMeshes에 반환 된 메시 개체는 메시에 서 메모리 제약 조건을 줄이는 것과 동일한 개체가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-292">If the system does not support colliders the Mesh object returned in ColliderMeshes will be the same object as the mesh reducing memory constraints.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="63fd3-293">장면 이해로 개발</span><span class="sxs-lookup"><span data-stu-id="63fd3-293">Developing with scene understanding</span></span>

<span data-ttu-id="63fd3-294">이 시점에서 런타임 및 SDK를 이해 하는 장면의 핵심 구성 요소를 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-294">At this point, you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="63fd3-295">강력 하 고 복잡 한 점은 액세스 패턴, 3D 프레임 워크와의 상호 작용, 공간 계획, 방 분석, 탐색, 물리 등과 같은 고급 작업을 수행 하기 위해 이러한 Api 위에 작성할 수 있는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-295">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to do more advanced tasks like spatial planning, room analysis, navigation, physics, and so on.</span></span> <span data-ttu-id="63fd3-296">시나리오를 표현할 수 있도록 적절 한 방향으로 안내 하는 샘플에서이를 캡처해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-296">We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="63fd3-297">주소를 지정 하지 않는 샘플 또는 시나리오가 있으면 알려주세요. 그러면 필요한 항목을 문서화/프로토타입으로 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-297">If there are samples or scenarios we aren't addressing, let us know and we'll try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="63fd3-298">샘플 코드는 어디에서 얻을 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="63fd3-298">Where can I get sample code?</span></span>

<span data-ttu-id="63fd3-299">Unity 샘플 코드에 대 한 장면 이해는 [Unity 샘플 페이지](https://github.com/sceneunderstanding-microsoft/unitysample) 페이지에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-299">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="63fd3-300">이 응용 프로그램을 사용 하면 장치와 통신 하 여 다양 한 장면 개체를 렌더링 하거나, PC에서 serialize 된 장면을 로드 하 고, 장치 없이 장면 이해를 경험할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-300">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="63fd3-301">샘플 장면을 어디에서 얻을 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="63fd3-301">Where can I get sample scenes?</span></span>

<span data-ttu-id="63fd3-302">HoloLens2가 있는 경우 ComputeSerializedAsync의 출력을 파일에 저장 하 고 사용자의 편의를 위해이를 deserialize 하 여 캡처한 장면을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-302">If you have a HoloLens2, you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="63fd3-303">HoloLens2 장치가 없지만 장면 이해를 재생 하려는 경우에는 미리 캡처된 장면을 다운로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-303">If you don't have a HoloLens2 device but want to play with Scene Understanding, you'll need to download a pre-captured scene.</span></span> <span data-ttu-id="63fd3-304">장면 이해 샘플은 현재 사용자의 편의를 위해 다운로드 하 여 사용할 수 있는 직렬화 된 장면과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-304">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="63fd3-305">여기에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63fd3-305">You can find them here:</span></span>

[<span data-ttu-id="63fd3-306">장면 이해 샘플 장면</span><span class="sxs-lookup"><span data-stu-id="63fd3-306">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a><span data-ttu-id="63fd3-307">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63fd3-307">See also</span></span>

* [<span data-ttu-id="63fd3-308">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="63fd3-308">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="63fd3-309">장면 이해</span><span class="sxs-lookup"><span data-stu-id="63fd3-309">Scene understanding</span></span>](../../design/scene-understanding.md)
* [<span data-ttu-id="63fd3-310">Unity 샘플</span><span class="sxs-lookup"><span data-stu-id="63fd3-310">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
