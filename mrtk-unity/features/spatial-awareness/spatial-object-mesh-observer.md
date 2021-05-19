---
title: 공간 개체 메시 관찰자
description: MRTK의 공간 메시 관찰자에 대한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 51963fca4fa76340089b84e400f2882763977f72
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144450"
---
# <a name="configuring-mesh-observers-for-the-editor"></a><span data-ttu-id="16dba-104">편집기를 위한 메시 관찰자 구성</span><span class="sxs-lookup"><span data-stu-id="16dba-104">Configuring mesh observers for the editor</span></span>

<span data-ttu-id="16dba-105">Unity 편집기에서 환경 메시 데이터를 제공하는 편리한 방법은 클래스를 사용하는 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 것입니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="16dba-106">*공간 개체 메시 관찰자는* 3D 모델 데이터를 가져와 공간 메시를 나타낼 수 있도록 하는 [공간 인식 시스템의](spatial-awareness-getting-started.md) 편집기 전용 데이터 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](spatial-awareness-getting-started.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="16dba-107">*공간 개체 메시 관찰자의* 일반적인 용도 중 하나는 Microsoft HoloLens 통해 스캔한 데이터를 가져와서 Unity 내에서 환경이 서로 다른 환경에 어떻게 적응하는지 테스트하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="16dba-108">시작</span><span class="sxs-lookup"><span data-stu-id="16dba-108">Getting started</span></span>

<span data-ttu-id="16dba-109">이 가이드에서는 *공간 개체 메시 관찰자* 를 설정하는 작업을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="16dba-110">이 기능을 사용하도록 설정하는 세 가지 주요 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="16dba-111">공간 인식 시스템 프로필에 *공간 개체 메시 관찰자* 추가</span><span class="sxs-lookup"><span data-stu-id="16dba-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="16dba-112">환경 메시 데이터 개체 설정</span><span class="sxs-lookup"><span data-stu-id="16dba-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="16dba-113">Mesh Observer 프로필 속성의 나머지 구성</span><span class="sxs-lookup"><span data-stu-id="16dba-113">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="16dba-114">*공간 개체 메시 관찰자* 프로필 설정</span><span class="sxs-lookup"><span data-stu-id="16dba-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="16dba-115">원하는 Mixed Reality *도구 키트* 구성 프로필을 선택하거나 장면에서 *Mixed Reality Toolkit 개체를* 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="16dba-116">공간 인식 *시스템* 탭을 열거나 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="16dba-117">*"공간 관찰자 추가"* 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-117">Click on *"Add Spatial Observer"* button</span></span>

    ![공간 관찰자 추가](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="16dba-119">*SpatialObjectMeshObserver* 형식 선택</span><span class="sxs-lookup"><span data-stu-id="16dba-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![공간 개체 메시 관찰자 선택](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="16dba-121">원하는 공간 *메시 개체* 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="16dba-122">기본적으로 관찰자는 예제 모델로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="16dba-123">이 모델은 Microsoft HoloLens 사용하여 만들었지만 새 검사 [메시 개체 를 만들](#acquiring-environment-scans)수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="16dba-124">메시 관찰자 프로필 속성의 나머지 구성</span><span class="sxs-lookup"><span data-stu-id="16dba-124">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

    ![메시 개체 선택](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="16dba-126">공간 개체 메시 관찰자 프로필 정보</span><span class="sxs-lookup"><span data-stu-id="16dba-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="16dba-127">*공간 개체 메시 관찰자* 는 3d 모델에서 데이터를 로드 하므로 아래에 설명 된 표준 메시 관찰자 설정 중 일부를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="16dba-128">**업데이트 간격**</span><span class="sxs-lookup"><span data-stu-id="16dba-128">**Update Interval**</span></span>

<span data-ttu-id="16dba-129">*공간 개체 메시 관찰자* 는 모델이 로드 될 때 모든 메시를 응용 프로그램에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="16dba-130">업데이트 간의 시간 델타를 시뮬레이션 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="16dba-131">응용 프로그램은 및를 호출 하 여 메시 이벤트를 다시 받을 수 있습니다 [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .</span><span class="sxs-lookup"><span data-stu-id="16dba-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="16dba-132">**고정 관찰자**</span><span class="sxs-lookup"><span data-stu-id="16dba-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="16dba-133">*공간 개체 메시 관찰자* 는 모든 3d 메시 개체가 고정 되어 있고 원본을 무시 하지 않는 것으로 간주 합니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="16dba-134">**관찰자 모양 및 익스텐트**</span><span class="sxs-lookup"><span data-stu-id="16dba-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="16dba-135">*공간 개체 메시 관찰자* 는 전체 3d 메시를 응용 프로그램에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="16dba-136">관찰자 모양 및 익스텐트는 고려 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="16dba-137">**세부 정보 및 삼각형/입방 미터**</span><span class="sxs-lookup"><span data-stu-id="16dba-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="16dba-138">관찰자는 응용 프로그램에 메시를 보낼 때 3D 모델 LODs를 찾으려고 시도 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="16dba-139">환경 검색 획득</span><span class="sxs-lookup"><span data-stu-id="16dba-139">Acquiring environment scans</span></span>

<span data-ttu-id="16dba-140">이 섹션에서는 *공간 개체 메시 관찰자* 와 함께 사용할 *공간 메시 개체* 파일을 만들고 수집 하기 위한 추가 정보를 간략하게 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="16dba-141">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="16dba-141">Windows Device Portal</span></span>

<span data-ttu-id="16dba-142">[Windows 장치 포털](/windows/mixed-reality/using-the-windows-device-portal) 은 Microsoft HoloLens 장치에서 공간 메시를 .obj 파일로 다운로드 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-142">The [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="16dba-143">HoloLens를 사용 하 여 원하는 환경을 간단히 탐색 하 고 보는 방법으로 검색</span><span class="sxs-lookup"><span data-stu-id="16dba-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="16dba-144">Windows 장치 포털을 사용 하 여 HoloLens에 연결</span><span class="sxs-lookup"><span data-stu-id="16dba-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="16dba-145">*3D 보기* 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="16dba-146">*공간 매핑* 섹션에서 *업데이트* 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="16dba-147">*공간 매핑* 섹션 아래의 *저장* 단추를 클릭하여 obj 파일을 PC에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="16dba-148">**HoloToolkit .room 파일**</span><span class="sxs-lookup"><span data-stu-id="16dba-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="16dba-149">많은 개발자가 이전에 HoloToolkit를 사용하여 환경을 검사하고 .room 파일을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="16dba-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="16dba-150">이제 Mixed Reality 도구 키트는 이러한 파일을 Unity에서 GameObjects로 가져오고 관찰자에서 공간 메시 개체로 사용할 수 있도록 *지원합니다.*</span><span class="sxs-lookup"><span data-stu-id="16dba-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="16dba-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="16dba-151">See also</span></span>

- [<span data-ttu-id="16dba-152">프로필</span><span class="sxs-lookup"><span data-stu-id="16dba-152">Profiles</span></span>](../profiles/profiles.md)
- [<span data-ttu-id="16dba-153">Mixed Reality 도구 키트 프로필 구성 가이드</span><span class="sxs-lookup"><span data-stu-id="16dba-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/mixed-reality-configuration-guide.md)
- [<span data-ttu-id="16dba-154">공간 인식 시작</span><span class="sxs-lookup"><span data-stu-id="16dba-154">Spatial Awareness Getting started</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="16dba-155">디바이스에서 메시 관찰자 구성</span><span class="sxs-lookup"><span data-stu-id="16dba-155">Configuring Mesh Observers on Device</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="16dba-156">코드를 통해 메시 관찰자 구성</span><span class="sxs-lookup"><span data-stu-id="16dba-156">Configuring Mesh Observers via code</span></span>](usage-guide.md)
- [<span data-ttu-id="16dba-157">Windows 디바이스 포털 사용</span><span class="sxs-lookup"><span data-stu-id="16dba-157">Using the Windows Device Portal</span></span>](/windows/mixed-reality/using-the-windows-device-portal)