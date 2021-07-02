---
title: 공간 개체 메시 관찰자
description: MRTK의 공간 메시 관찰자에 대 한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: db0b2f14d0a5d65140223d3fa3f4f5324ef2ba76
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176690"
---
# <a name="spatial-object-mesh-observer"></a><span data-ttu-id="9f2e2-104">공간 개체 메시 관찰자</span><span class="sxs-lookup"><span data-stu-id="9f2e2-104">Spatial object mesh observer</span></span>

<span data-ttu-id="9f2e2-105">Unity 편집기에서 환경 메시 데이터를 제공 하는 편리한 방법은 클래스를 사용 하는 것입니다 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) .</span><span class="sxs-lookup"><span data-stu-id="9f2e2-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="9f2e2-106">*공간 개체 메시 관찰자* 는 공간 메시를 나타내기 위해 3d 모델 데이터를 가져올 수 있는 [공간 인식 시스템용](spatial-awareness-getting-started.md) 편집기 전용 데이터 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](spatial-awareness-getting-started.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="9f2e2-107">*공간 개체 메시 관찰자* 의 일반적인 용도 중 하나는 Microsoft HoloLens을 통해 검색 된 데이터를 가져와 Unity 내에서 다양 한 환경에 대 한 환경을 어떻게 활용할 수 있는지 테스트 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="9f2e2-108">시작</span><span class="sxs-lookup"><span data-stu-id="9f2e2-108">Getting started</span></span>

<span data-ttu-id="9f2e2-109">이 가이드에서는 *공간 개체 메시 관찰자* 를 설정 하는 과정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="9f2e2-110">이 기능을 사용 하도록 설정 하는 세 가지 주요 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="9f2e2-111">공간 인식 시스템 프로필에 *공간 개체 메시 관찰자* 추가</span><span class="sxs-lookup"><span data-stu-id="9f2e2-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="9f2e2-112">환경 메시 데이터 개체 설정</span><span class="sxs-lookup"><span data-stu-id="9f2e2-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="9f2e2-113">메시 관찰자 프로필 속성의 나머지 구성</span><span class="sxs-lookup"><span data-stu-id="9f2e2-113">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="9f2e2-114">*공간 개체 메시 관찰자* 프로필 설정</span><span class="sxs-lookup"><span data-stu-id="9f2e2-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="9f2e2-115">원하는 *혼합 현실 Toolkit* 구성 프로필을 선택 하거나 장면에서 *혼합 현실 Toolkit* 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="9f2e2-116">*공간 인식 시스템* 탭을 열거나 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="9f2e2-117">*"공간 관찰자 추가"* 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-117">Click on *"Add Spatial Observer"* button</span></span>

    ![공간 관찰자 추가](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="9f2e2-119">*SpatialObjectMeshObserver* 유형 선택</span><span class="sxs-lookup"><span data-stu-id="9f2e2-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![공간 개체 메시 관찰자 선택](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="9f2e2-121">원하는 *공간 메시 개체* 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="9f2e2-122">기본적으로 관찰자는 예제 모델을 사용 하 여 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="9f2e2-123">이 모델은 Microsoft HoloLens를 사용 하 여 만들어졌지만 [새 스캔 메시 개체를 만들](#acquiring-environment-scans)수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="9f2e2-124">메시 관찰자 프로필 속성의 나머지 구성</span><span class="sxs-lookup"><span data-stu-id="9f2e2-124">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

    ![메시 개체 선택](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="9f2e2-126">공간 개체 메시 관찰자 프로필 정보</span><span class="sxs-lookup"><span data-stu-id="9f2e2-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="9f2e2-127">*공간 개체 메시 관찰자* 는 3d 모델에서 데이터를 로드 하므로 아래에 설명 된 표준 메시 관찰자 설정 중 일부를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="9f2e2-128">**업데이트 간격**</span><span class="sxs-lookup"><span data-stu-id="9f2e2-128">**Update Interval**</span></span>

<span data-ttu-id="9f2e2-129">*공간 개체 메시 관찰자* 는 모델이 로드 될 때 모든 메시를 응용 프로그램에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="9f2e2-130">업데이트 간의 시간 델타를 시뮬레이션 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="9f2e2-131">응용 프로그램은 및를 호출 하 여 메시 이벤트를 다시 받을 수 있습니다 [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .</span><span class="sxs-lookup"><span data-stu-id="9f2e2-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="9f2e2-132">**고정 관찰자**</span><span class="sxs-lookup"><span data-stu-id="9f2e2-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="9f2e2-133">*공간 개체 메시 관찰자* 는 모든 3d 메시 개체가 고정 되어 있고 원본을 무시 하지 않는 것으로 간주 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="9f2e2-134">**관찰자 모양 및 익스텐트**</span><span class="sxs-lookup"><span data-stu-id="9f2e2-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="9f2e2-135">*공간 개체 메시 관찰자* 는 전체 3d 메시를 응용 프로그램에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="9f2e2-136">관찰자 모양 및 익스텐트는 고려 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="9f2e2-137">**세부 정보 및 삼각형/입방 미터**</span><span class="sxs-lookup"><span data-stu-id="9f2e2-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="9f2e2-138">관찰자는 응용 프로그램에 메시를 보낼 때 3D 모델 LODs를 찾으려고 시도 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="9f2e2-139">환경 검색 획득</span><span class="sxs-lookup"><span data-stu-id="9f2e2-139">Acquiring environment scans</span></span>

<span data-ttu-id="9f2e2-140">이 섹션에서는 *공간 개체 메시 관찰자* 와 함께 사용할 *공간 메시 개체* 파일을 만들고 수집 하기 위한 추가 정보를 간략하게 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="9f2e2-141">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="9f2e2-141">Windows Device Portal</span></span>

<span data-ttu-id="9f2e2-142">[Windows 장치 포털](/windows/mixed-reality/using-the-windows-device-portal) 은 Microsoft HoloLens 장치에서 공간 메시를 .obj 파일로 다운로드 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-142">The [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="9f2e2-143">HoloLens를 사용 하 여 원하는 환경을 쉽게 탐색 하 고 볼 때 검색</span><span class="sxs-lookup"><span data-stu-id="9f2e2-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="9f2e2-144">Windows 장치 포털을 사용 하 여 HoloLens에 커넥트</span><span class="sxs-lookup"><span data-stu-id="9f2e2-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="9f2e2-145">*3D 보기* 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="9f2e2-146">*공간 매핑* 섹션에서 *업데이트* 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="9f2e2-147">*공간 매핑* 섹션에서 *저장* 단추를 클릭 하 여 obj 파일을 PC에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="9f2e2-148">**HoloToolkit 파일**</span><span class="sxs-lookup"><span data-stu-id="9f2e2-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="9f2e2-149">많은 개발자 들은 이전에 HoloToolkit를 사용 하 여 환경을 검사 하 고 방 파일을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="9f2e2-150">이제 혼합 현실 Toolkit는 Unity에서 gameobject로 이러한 파일을 가져와 관찰자에서 *공간 메시 개체로* 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f2e2-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f2e2-151">참조</span><span class="sxs-lookup"><span data-stu-id="9f2e2-151">See also</span></span>

- [<span data-ttu-id="9f2e2-152">프로필</span><span class="sxs-lookup"><span data-stu-id="9f2e2-152">Profiles</span></span>](../profiles/profiles.md)
- [<span data-ttu-id="9f2e2-153">혼합 현실 Toolkit 프로필 구성 가이드</span><span class="sxs-lookup"><span data-stu-id="9f2e2-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/mixed-reality-configuration-guide.md)
- [<span data-ttu-id="9f2e2-154">공간 인식 시작</span><span class="sxs-lookup"><span data-stu-id="9f2e2-154">Spatial Awareness Getting started</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="9f2e2-155">장치에서 메시 관찰자 구성</span><span class="sxs-lookup"><span data-stu-id="9f2e2-155">Configuring Mesh Observers on Device</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="9f2e2-156">코드를 통해 메시 관찰자 구성</span><span class="sxs-lookup"><span data-stu-id="9f2e2-156">Configuring Mesh Observers via code</span></span>](usage-guide.md)
- [<span data-ttu-id="9f2e2-157">Windows 디바이스 포털 사용</span><span class="sxs-lookup"><span data-stu-id="9f2e2-157">Using the Windows Device Portal</span></span>](/windows/mixed-reality/using-the-windows-device-portal)
