---
title: DirectX의 좌표계
description: 공간 로케이터, 참조 프레임 및 공간 앵커를 사용 하 여 DirectX 및 혼합 현실의 좌표계에 대해 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: 혼합 현실, 공간 로케이터, 공간 참조 프레임, 공간 좌표 시스템, 공간 스테이지, 샘플 코드, 이미지 안정화, 공간 앵커, 공간 앵커 저장소, 추적 손실, 연습, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 055eff0bb04228cb0a19b9ea208bfc9c00ce2dbe
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006863"
---
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="04c7a-104">DirectX의 좌표계</span><span class="sxs-lookup"><span data-stu-id="04c7a-104">Coordinate systems in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="04c7a-105">이 문서는 레거시 WinRT 네이티브 Api와 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="04c7a-106">새 네이티브 앱 프로젝트의 경우 **[OPENXR API](openxr-getting-started.md)** 를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="04c7a-107">[좌표계](../../design/coordinate-systems.md) 는 Windows Mixed Reality api에서 제공 하는 공간 이해의 기반을 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-107">[Coordinate systems](../../design/coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="04c7a-108">오늘날에 장착 된 VR 또는 단일 방에 VR 장치는 추적 된 공간에 대 한 기본 좌표계를 하나 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-108">Today's seated VR or single-room VR devices establish one primary coordinate system for their tracked space.</span></span> <span data-ttu-id="04c7a-109">HoloLens와 같은 혼합 현실 장치는 사용자가 안내 하는 장치를 검색 하 고 학습할 수 있는, 정의 되지 않은 많은 환경을 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-109">Mixed Reality devices like HoloLens are designed for large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="04c7a-110">장치는 사용자의 방에 대 한 지식을 지속적으로 향상 시키기 위해 적응 하지만 앱 수명 동안 서로 관계를 변경 하는 좌표계를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-110">The device adapts to continually improving knowledge about the user's rooms, but results in coordinate systems that change their relationship to one another over the apps lifetime.</span></span> <span data-ttu-id="04c7a-111">Windows Mixed Reality는 전 세계에 연결 된 참조 프레임을 통해 장착 된 모던 헤드셋에서 다양 한 장치를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-111">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="04c7a-112">이 문서의 코드 조각은 현재 c + + [holographic 프로젝트 템플릿에](creating-a-holographic-directx-project.md)사용 되는 c + 17-So-far working 호환 c + +/winrt 대신 c + +/cx를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-112">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="04c7a-113">이 개념은 c + +/WinRT 프로젝트와 동일 하지만 코드를 변환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-113">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="04c7a-114">Windows의 공간 좌표계</span><span class="sxs-lookup"><span data-stu-id="04c7a-114">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="04c7a-115">Windows에서 실제 좌표계를 설명 하는 데 사용 되는 핵심 유형은 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>입니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-115">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="04c7a-116">이 형식의 인스턴스는 임의의 좌표계를 나타내며, 각 좌표계의 세부 정보를 이해 하지 않고도 두 좌표계 간에 변환 하는 데 사용할 수 있는 변환 행렬 데이터를 가져오는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-116">An instance of this type represents an arbitrary coordinate system, providing a method for getting transformation matrix data that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="04c7a-117">공간 정보를 반환 하는 메서드는 SpatialCoordinateSystem 매개 변수를 사용 하 여 이러한 좌표가 반환 될 때 가장 유용한 좌표계를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-117">Methods that return spatial information will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="04c7a-118">공간 정보는 사용자의 환경에서 점으로, 광선 또는 볼륨으로 표시 되 고 이러한 좌표의 단위는 항상 미터 단위로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-118">Spatial information is represented as points, rays, or volumes in the user's surroundings, and the units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="04c7a-119">SpatialCoordinateSystem에는 장치의 위치를 나타내는 것을 비롯 하 여 다른 좌표계와의 동적 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-119">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="04c7a-120">언제 든 지 장치는 다른 좌표계가 아닌 일부 좌표계를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-120">At any point, the device can locate some coordinate systems and not others.</span></span> <span data-ttu-id="04c7a-121">대부분의 좌표계에서 앱은 찾을 수 없는 기간을 처리할 준비를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-121">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="04c7a-122">응용 프로그램은 직접 SpatialCoordinateSystems를 만들지 않아야 합니다. 대신 인식 Api를 통해 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-122">Your application shouldn't create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="04c7a-123">인식 Api에는 좌표계의 세 가지 기본 소스가 있습니다. 각 소스는 [좌표계](../../design/coordinate-systems.md) 페이지에 설명 된 개념에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-123">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](../../design/coordinate-systems.md) page:</span></span>
* <span data-ttu-id="04c7a-124">고정 참조 프레임을 가져오려면 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> 을 만들거나 현재 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>에서 하나를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-124">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="04c7a-125">공간 앵커를 가져오려면 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-125">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="04c7a-126">참조의 연결 된 프레임을 가져오려면 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-126">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="04c7a-127">이러한 개체에서 반환 되는 모든 좌표계는 직각으로, + y up, + x를 오른쪽에, + z는 역방향입니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-127">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="04c7a-128">양의 x 방향에서 왼쪽 또는 오른쪽 손가락을 가리키고 양의 y 방향으로 curl 하 여 양의 z 축 점이 가리키는 방향을 기억할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-128">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="04c7a-129">엄지 방향이 사용자에 게 표시 되는 방향에 따라 해당 좌표계의 양의 z 축이 가리키는 방향이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-129">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="04c7a-130">다음 그림에서는 이러한 두 좌표계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-130">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="04c7a-131">![왼쪽 및 오른쪽 좌표계](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="04c7a-131">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="04c7a-132">*왼쪽 및 오른쪽 좌표계*</span><span class="sxs-lookup"><span data-stu-id="04c7a-132">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="04c7a-133"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> 클래스를 사용 하 여 연결 된 참조 또는 고정 프레임 프레임을 만들어 HoloLens 위치를 기반으로 SpatialCoordinateSystem에 부트스트랩 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-133">Use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference to bootstrap into a SpatialCoordinateSystem based on the HoloLens position.</span></span> <span data-ttu-id="04c7a-134">이 프로세스에 대 한 자세한 내용을 보려면 다음 섹션을 계속 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-134">Continue to the next section to learn more about this process.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="04c7a-135">공간 단계를 사용 하 여 전 세계에 holograms 두기</span><span class="sxs-lookup"><span data-stu-id="04c7a-135">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="04c7a-136">불투명 Windows Mixed Reality 몰입 형 헤드셋의 좌표계는 정적 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference:: Current</a> 속성을 사용 하 여 액세스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-136">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="04c7a-137">이 API는 다음을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-137">This API provides:</span></span>

* <span data-ttu-id="04c7a-138">좌표계</span><span class="sxs-lookup"><span data-stu-id="04c7a-138">A coordinate system</span></span>
* <span data-ttu-id="04c7a-139">플레이어의 장착 여부에 대 한 정보</span><span class="sxs-lookup"><span data-stu-id="04c7a-139">Information about whether the player is seated or mobile</span></span>
* <span data-ttu-id="04c7a-140">플레이어가 모바일 인지 여부를 탐색 하기 위한 안전한 영역의 경계입니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-140">The boundary of a safe area for walking around if the player is mobile</span></span>
* <span data-ttu-id="04c7a-141">헤드셋이 방향성 인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-141">An indication of whether the headset is directional.</span></span> 
* <span data-ttu-id="04c7a-142">공간 단계에 대 한 업데이트에 대 한 이벤트 처리기입니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-142">An event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="04c7a-143">먼저 공간 단계를 가져오고 그에 대 한 업데이트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-143">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="04c7a-144">**공간 스테이지 초기화** 에 대 한 코드</span><span class="sxs-lookup"><span data-stu-id="04c7a-144">Code for **Spatial stage initialization**</span></span>

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

<span data-ttu-id="04c7a-145">OnCurrentChanged 메서드에서 앱은 공간 단계를 검사 하 고 플레이어 환경을 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-145">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience.</span></span> <span data-ttu-id="04c7a-146">이 예제에서는 스테이지 경계의 시각화와 사용자가 지정한 시작 위치 및 단계의 보기 범위와 이동 속성 범위를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-146">In this example, we provide a visualization of the stage boundary and the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="04c7a-147">또한 단계를 제공할 수 없는 경우에는 자체의 고정 좌표계로 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-147">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="04c7a-148">**공간 스테이지 업데이트** 에 대 한 코드</span><span class="sxs-lookup"><span data-stu-id="04c7a-148">Code for **Spatial stage update**</span></span>

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

<span data-ttu-id="04c7a-149">스테이지 경계를 정의 하는 꼭 짓 점 집합은 시계 방향으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-149">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="04c7a-150">Windows Mixed Reality shell은 사용자가 해당 영역에 접근 하는 경우 경계에서 울타리를 그리며 사용자의 용도에 맞게 walkable 영역을 triangularize 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-150">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it, but you may want to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="04c7a-151">다음 알고리즘을 사용 하 여 단계를 triangularize 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-151">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="04c7a-152">**공간 스테이지 triangularization** 코드</span><span class="sxs-lookup"><span data-stu-id="04c7a-152">Code for **Spatial stage triangularization**</span></span>

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="04c7a-153">고정 된 참조 프레임을 사용 하 여 holograms를 전 세계에 두기</span><span class="sxs-lookup"><span data-stu-id="04c7a-153">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="04c7a-154">[SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) 클래스는 사용자가 이동 하는 동안 사용자의 주변을 기준으로 [고정 된 상태로 유지](../../design/coordinate-systems.md#stationary-frame-of-reference) 되는 참조 프레임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-154">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](../../design/coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="04c7a-155">이 참조 프레임은 장치 근처의 좌표를 안정적으로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-155">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="04c7a-156">SpatialStationaryFrameOfReference의 한 가지 주요 사용은 holograms를 렌더링할 때 렌더링 엔진 내에서 기본 세계 좌표계로 작동 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-156">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="04c7a-157">SpatialStationaryFrameOfReference을 가져오려면 [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) 클래스를 사용 하 고 [Createstationaryframeofreferenceatcurrentlocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx)을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-157">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="04c7a-158">Windows Holographic 앱 템플릿 코드에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-158">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="04c7a-159">고정 참조 프레임은 전체 공간에 맞춰 최적 위치를 제공 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-159">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="04c7a-160">해당 참조 프레임 내의 개별 위치는 약간 드리프트 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-160">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="04c7a-161">이는 장치가 환경에 대해 더 자세히 알게 되기 때문에 정상입니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-161">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="04c7a-162">개별 holograms를 정확 하 게 배치 해야 하는 경우에는 SpatialAnchor를 사용 하 여 개별 홀로그램을 실제 세계의 위치에 고정 해야 합니다. 예를 들어 사용자가 특별 한 관심을 나타내는 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-162">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="04c7a-163">앵커 위치는 드리프트 되지 않지만 수정할 수 있습니다. 수정이 발생 한 후에는 다음 프레임에서 시작 하는 수정 된 위치를 앵커에서 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-163">Anchor positions don't drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="04c7a-164">공간 앵커를 사용 하 여 holograms을 전 세계에 두기</span><span class="sxs-lookup"><span data-stu-id="04c7a-164">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="04c7a-165">[공간 앵커](../../design/coordinate-systems.md#spatial-anchors) 는 시간이 지남에 따라 앵커가 유지 되도록 하는 시스템을 사용 하 여 실제 세계의 특정 위치에 holograms를 넣는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-165">[Spatial anchors](../../design/coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="04c7a-166">이 항목에서는 앵커를 만들고 사용 하는 방법과 앵커 데이터로 작업 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-166">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="04c7a-167">선택한 SpatialCoordinateSystem 내에서 임의 위치와 방향으로 SpatialAnchor을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-167">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="04c7a-168">장치는 현재 좌표계를 찾을 수 있어야 하 고, 시스템은 공간 앵커의 한도에 도달 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-168">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="04c7a-169">정의 된 SpatialAnchor의 좌표계는 초기 위치의 정확한 위치와 방향을 유지 하기 위해 지속적으로 조정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-169">Once defined, the coordinate system of a SpatialAnchor adjusts continually to keep the precise position and orientation of its initial location.</span></span> <span data-ttu-id="04c7a-170">그런 다음이 SpatialAnchor를 사용 하 여 정확한 위치의 사용자 환경에서 수정 된 것으로 표시 되는 holograms를 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-170">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="04c7a-171">앵커를 그대로 유지 하는 조정 효과는 앵커에서의 거리가 증가할수록 확대 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-171">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="04c7a-172">해당 앵커의 원점에서 약 3 미터 이상인 앵커를 기준으로 콘텐츠를 렌더링 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-172">You should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="04c7a-173">[CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) 속성은 장치에서 앵커의 정확한 위치를 조정할 때 감속/가속을 적용 하 여 앵커를 기준으로 콘텐츠를 배치 하는 데 사용할 수 있는 좌표계를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-173">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="04c7a-174">[RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) 속성 및 해당 [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) 이벤트를 사용 하 여 이러한 조정을 직접 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-174">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="04c7a-175">공간 앵커 유지 및 공유</span><span class="sxs-lookup"><span data-stu-id="04c7a-175">Persist and share spatial anchors</span></span>

<span data-ttu-id="04c7a-176">[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) 클래스를 사용 하 여 SpatialAnchor를 로컬로 유지 한 다음 동일한 HoloLens 장치에서 이후 앱 세션으로 다시 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-176">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="04c7a-177"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a>를 사용 하 여 로컬 SpatialAnchor에서 영 속 클라우드 앵커를 만들 수 있습니다. 그러면 앱이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-177">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="04c7a-178">여러 장치에서 공통 공간 앵커를 공유 하면 각 사용자가 실시간으로 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-178">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location in real time.</span></span> 

<span data-ttu-id="04c7a-179">HoloLens, iOS 및 Android 장치에서 비동기 홀로그램 지 속성에 대해 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-179">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="04c7a-180">내구성이 있는 클라우드 공간 앵커를 공유 하 여 여러 장치는 동시에 함께 제공 되지 않더라도 시간이 지남에 따라 동일한 지속형 홀로그램을 관찰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-180">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="04c7a-181">HoloLens 앱에서 공유 환경 빌드를 시작 하려면 5 분 <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 공간 앵커 HoloLens 빠른</a>시작을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="04c7a-181">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="04c7a-182">Azure 공간 앵커를 사용 하 여 실행 하면 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens에서 앵커를 만들고 찾을</a>수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-182">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="04c7a-183"><a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 및 iOS</a> 에 대 한 연습을 사용할 수 있으므로 모든 장치에서 동일한 앵커를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-183">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="04c7a-184">Holographic 콘텐츠에 대 한 SpatialAnchors 만들기</span><span class="sxs-lookup"><span data-stu-id="04c7a-184">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="04c7a-185">이 코드 샘플에서는 **누름** 제스처가 검색 될 때 앵커를 만들도록 Windows Holographic 앱 템플릿을 수정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-185">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="04c7a-186">그러면 큐브가 렌더링 단계 중에 앵커에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-186">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="04c7a-187">도우미 클래스에서 여러 앵커를 지원 하기 때문에이 코드 샘플을 사용 하려는 만큼의 큐브를 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-187">Since multiple anchors are supported by the helper class, we can place as many cubes as we want to use this code sample!</span></span>

> [!NOTE]
> <span data-ttu-id="04c7a-188">앵커의 Id는 앱에서 제어 하는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-188">The IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="04c7a-189">이 예제에서는 앱의 앵커 컬렉션에 현재 저장 되어 있는 앵커의 수를 기준으로 순차적으로 명명 스키마를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-189">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="04c7a-190">SpatialAnchorStore를 비동기적으로 로드 하 고 캐시 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-190">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="04c7a-191">다음을 포함 하 여이 지 속성을 처리 하는 데 도움이 되는 SampleSpatialAnchorHelper 클래스를 작성 하는 방법을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-191">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="04c7a-192">Platform:: String 키로 인덱싱된 메모리 내 앵커의 컬렉션을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-192">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="04c7a-193">로컬 메모리 내 컬렉션과 별도로 유지 되는 시스템의 SpatialAnchorStore에서 앵커를 로드 하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-193">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="04c7a-194">앱에서이 작업을 선택 하면 SpatialAnchorStore에 대 한 로컬 메모리 내 앵커 컬렉션을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-194">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="04c7a-195">[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)에 [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) 개체를 저장 하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-195">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="04c7a-196">클래스가 시작 되 면 SpatialAnchorStore를 비동기적으로 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-196">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="04c7a-197">이 작업에는 API가 앵커 저장소를 로드할 때 시스템 i/o가 포함 됩니다 .이 API는 비동기 방식으로 수행 되므로 i/o가 차단 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-197">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

<span data-ttu-id="04c7a-198">앵커를 저장 하는 데 사용할 수 있는 SpatialAnchorStore 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-198">You'll be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="04c7a-199">문자열에 해당 하는 키 값을 SpatialAnchors 데이터 값과 연결 하는 IMapView입니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-199">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="04c7a-200">이 샘플 코드에서는 도우미 클래스의 public 함수를 통해 액세스할 수 있는 개인 클래스 멤버 변수에이를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-200">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="04c7a-201">일시 중단/다시 시작 이벤트를 연결 하 여 앵커 저장소를 저장 하 고 로드 하는 것을 잊지 마세요.</span><span class="sxs-lookup"><span data-stu-id="04c7a-201">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="04c7a-202">앵커 저장소에 콘텐츠 저장</span><span class="sxs-lookup"><span data-stu-id="04c7a-202">Save content to the anchor store</span></span>

<span data-ttu-id="04c7a-203">시스템이 앱을 일시 중단 하는 경우 공간 앵커를 앵커 저장소에 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-203">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="04c7a-204">응용 프로그램의 구현에 필요한 것 처럼 다른 시간에 앵커 저장소에 앵커를 저장 하도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-204">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="04c7a-205">SpatialAnchorStore에 메모리 내 앵커를 저장할 준비가 되 면 컬렉션을 반복 하 여 각 컬렉션을 저장 해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-205">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="04c7a-206">앱이 다시 시작 될 때 앵커 저장소에서 콘텐츠 로드</span><span class="sxs-lookup"><span data-stu-id="04c7a-206">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="04c7a-207">앱이 다시 시작 될 때 또는 언제 든 지 앵커 저장소의 IMapView에서 사용자 고유의 SpatialAnchors의 메모리 내 데이터베이스로 전송 하 여 AnchorStore에 저장 된 앵커를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-207">You can restore saved anchors in the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors when your app resumes or at any time.</span></span>

<span data-ttu-id="04c7a-208">SpatialAnchorStore에서 앵커를 복원 하려면 원하는 각 항목을 자체 메모리 내 컬렉션에 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-208">To restore anchors from the SpatialAnchorStore, restore each one that you're interested in to your own in-memory collection.</span></span>

<span data-ttu-id="04c7a-209">사용자가 만든 SpatialAnchors에 문자열을 연결 하려면 SpatialAnchors의 고유한 메모리 내 데이터베이스가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-209">You need your own in-memory database of SpatialAnchors to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="04c7a-210">샘플 코드에서는 Windows:: Foundation:: Collections:: IMap을 사용 하 여 앵커를 저장 하도록 선택 합니다 .이를 통해 SpatialAnchorStore에 동일한 키와 데이터 값을 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-210">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="04c7a-211">복원 되는 앵커는 당장 과정이 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-211">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="04c7a-212">예를 들어 별도의 방에 있는 앵커 이거나 다른 빌딩에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-212">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="04c7a-213">AnchorStore에서 검색 된 앵커는 사용 하기 전에 locatability을 테스트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-213">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="04c7a-214">이 예제 코드에서는 AnchorStore에서 모든 앵커를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-214">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="04c7a-215">이는 요구 사항이 아닙니다. 앱은 구현에 의미가 있는 문자열 키 값을 사용 하 여 앵커의 특정 하위 집합을 선택 하 고 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-215">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="04c7a-216">필요한 경우 앵커 저장소 지우기</span><span class="sxs-lookup"><span data-stu-id="04c7a-216">Clear the anchor store, when needed</span></span>

<span data-ttu-id="04c7a-217">경우에 따라 앱 상태를 지우고 새 데이터를 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-217">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="04c7a-218">[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)를 사용 하 여이 작업을 수행 하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-218">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="04c7a-219">도우미 클래스를 사용 하 여 Clear 함수를 래핑하는 것은 거의 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-219">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="04c7a-220">도우미 클래스에는 SpatialAnchorStore 인스턴스를 소유 하는 책임이 있으므로 샘플 구현에서이 작업을 수행 하도록 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-220">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="04c7a-221">예: 앵커 좌표계와 고정 참조 프레임 좌표계 연결</span><span class="sxs-lookup"><span data-stu-id="04c7a-221">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="04c7a-222">앵커가 있고 앵커의 좌표계에 있는 항목을 다른 콘텐츠에 대해 이미 사용 하 고 있는 SpatialStationaryReferenceFrame와 연결 하려는 경우를 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-222">Let's say you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame you’re already using for your other content.</span></span> <span data-ttu-id="04c7a-223">[TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) 를 사용 하 여 앵커의 좌표계에서 고정 참조 프레임으로의 변환을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-223">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to get a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

<span data-ttu-id="04c7a-224">이 프로세스는 다음과 같은 두 가지 방법으로 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-224">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="04c7a-225">두 참조 프레임을 서로 비교 하 여 이해할 수 있는지 여부를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-225">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="04c7a-226">그렇다면 한 좌표계에서 다른 좌표계로 직접 이동 하는 변환을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-226">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="04c7a-227">이 정보를 사용 하면 두 참조 프레임 간의 개체 간 공간 관계를 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-227">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="04c7a-228">렌더링의 경우 원래 참조 프레임이 나 앵커를 기준으로 개체를 그룹화 하 여 더 나은 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-228">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="04c7a-229">각 그룹에 대해 별도의 그리기 패스를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-229">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="04c7a-230">뷰 행렬은 처음에 동일한 좌표계를 사용 하 여 생성 된 모델 변환이 있는 개체에 대해 보다 정확 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-230">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="04c7a-231">장치에 연결 된 참조 프레임을 사용 하 여 holograms 만들기</span><span class="sxs-lookup"><span data-stu-id="04c7a-231">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="04c7a-232">장치 위치에 연결 된 상태를 [유지](../../design/coordinate-systems.md#attached-frame-of-reference) 하는 홀로그램을 렌더링 하려는 경우가 있습니다. 예를 들어, 장치에서 해당 방향을 확인 하 고 공간에서 위치를 확인할 수 없을 때 정보 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-232">There are times when you want to render a hologram that [remains attached](../../design/coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="04c7a-233">이를 위해 참조의 연결 된 프레임을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-233">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="04c7a-234">SpatialLocatorAttachedFrameOfReference 클래스는 실제 기반이 아니라 장치에 상대적인 좌표계를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-234">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems, which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="04c7a-235">이 프레임에는 참조 프레임을 만들 때 사용자가 연결 된 방향을 가리키는 사용자의 주변을 기준으로 하는 고정 머리글이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-235">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="04c7a-236">이 참조 프레임의 모든 방향은 사용자가 장치를 회전 하는 경우에도 해당 고정 된 제목을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-236">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="04c7a-237">HoloLens의 경우이 프레임 좌표계의 원점은 사용자 헤드의 회전 중심에 위치 하 여 해당 위치는 헤드 회전의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-237">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="04c7a-238">앱은이 점에 상대적인 오프셋을 지정 하 여 사용자 앞에 holograms을 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-238">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="04c7a-239">SpatialLocatorAttachedFrameOfReference을 가져오려면 SpatialLocator 클래스를 사용 하 고 CreateAttachedFrameOfReferenceAtCurrentHeading를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-239">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="04c7a-240">이는 Windows Mixed Reality 장치의 전체 범위에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-240">This applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="04c7a-241">장치에 연결 된 참조 프레임 사용</span><span class="sxs-lookup"><span data-stu-id="04c7a-241">Use a reference frame attached to the device</span></span>

<span data-ttu-id="04c7a-242">이 섹션에서는 Windows Holographic 앱 템플릿에서 변경한 내용에 대해 설명 하 고이 API를 사용 하 여 장치에 연결 된 참조 프레임을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-242">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="04c7a-243">이 "연결 된" 홀로그램은 고정 또는 고정 된 holograms 함께 작동 하며, 장치에서 전 세계의 위치를 찾을 수 없는 경우에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-243">This "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="04c7a-244">먼저, SpatialStationaryFrameOfReference 대신 SpatialLocatorAttachedFrameOfReference를 저장 하도록 템플릿을 변경 했습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-244">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="04c7a-245">**HolographicTagAlongSampleMain** 에서:</span><span class="sxs-lookup"><span data-stu-id="04c7a-245">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="04c7a-246">**HolographicTagAlongSampleMain** 에서:</span><span class="sxs-lookup"><span data-stu-id="04c7a-246">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="04c7a-247">업데이트 중에는 이제 프레임 예측을 사용 하 여에서 가져온 타임 스탬프의 좌표계를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-247">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="04c7a-248">공간 포인터 포즈를 가져오고 사용자의 응시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-248">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="04c7a-249">Holographic shell이 사용자의 응시를 따르는 방법과 유사 하 게 사용자의 [응시](../../design/gaze-and-commit.md)를 따르기 위해 예제 홀로그램을 원합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-249">We want our example hologram to follow the user's [gaze](../../design/gaze-and-commit.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="04c7a-250">이를 위해 동일한 타임 스탬프에서 SpatialPointerPose을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-250">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="04c7a-251">이 SpatialPointerPose에는 [사용자의 현재 제목](gaze-in-directx.md)에 따라 홀로그램을 배치 하는 데 필요한 정보가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-251">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze-in-directx.md).</span></span>

<span data-ttu-id="04c7a-252">사용자가 편안 하 게 하기 위해 선형 보간 ("lerp")을 사용 하 여 일정 기간 동안 위치를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-252">For user comfort, we use linear interpolation ("lerp") to smooth the change in position over a period of time.</span></span> <span data-ttu-id="04c7a-253">이는 홀로그램을 응시로 잠그는 것 보다 사용자에 게 더 친숙 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-253">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="04c7a-254">태그를 따라 홀로그램의 위치도 Lerping 이동을 감소 시켜 홀로그램을 안정화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-254">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement.</span></span> <span data-ttu-id="04c7a-255">이러한 완충를 수행 하지 않은 경우 일반적으로 사용자 헤드의 imperceptible 이동으로 간주 되는 것으로 간주 되므로 사용자가 홀로그램 지터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-255">If we didn't do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="04c7a-256">**StationaryQuadRenderer::P Osit홀로그램 홀로그램**:</span><span class="sxs-lookup"><span data-stu-id="04c7a-256">From **StationaryQuadRenderer::PositionHologram**:</span></span>

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
><span data-ttu-id="04c7a-257">디버깅 패널의 경우 뷰를 액세스가 방해 하지 않도록 홀로그램의 위치를 약간 아래로 변경 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-257">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it doesn't obstruct your view.</span></span> <span data-ttu-id="04c7a-258">이러한 작업을 수행 하는 방법의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-258">Here's an example of how you might do that.</span></span>

<span data-ttu-id="04c7a-259">**StationaryQuadRenderer::P Osit. 홀로그램**:</span><span class="sxs-lookup"><span data-stu-id="04c7a-259">For **StationaryQuadRenderer::PositionHologram**:</span></span>

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="04c7a-260">카메라를 향하는 홀로그램 회전</span><span class="sxs-lookup"><span data-stu-id="04c7a-260">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="04c7a-261">홀로그램을 배치할 만큼 충분 하지 않습니다 (이 경우에는 쿼드). 또한 사용자에 게는 개체를 회전 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-261">It isn't enough to position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="04c7a-262">이 유형의 billboarding은 홀로그램을 사용자 환경의 일부로 유지할 수 있도록 하기 때문에 세계 공간에서 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-262">This rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="04c7a-263">뷰 공간 billboarding는 홀로그램이 표시 방향으로 잠겨 있으므로 편안 하지 않습니다. 이 경우에는 왼쪽 및 오른쪽 뷰 매트릭스 사이를 보간 하 여 스테레오 렌더링을 방해 하지 않는 뷰 공간 빌보드 변환을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-263">View-space billboarding isn't as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices to acquire a view-space billboard transform that doesn't disrupt stereo rendering.</span></span> <span data-ttu-id="04c7a-264">여기서는 X 및 Z 축을 중심으로 회전 하 여 사용자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-264">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="04c7a-265">**StationaryQuadRenderer:: Update** 에서:</span><span class="sxs-lookup"><span data-stu-id="04c7a-265">From **StationaryQuadRenderer::Update**:</span></span>

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a><span data-ttu-id="04c7a-266">연결 된 홀로그램 렌더링</span><span class="sxs-lookup"><span data-stu-id="04c7a-266">Render the attached hologram</span></span>

<span data-ttu-id="04c7a-267">이 예에서는 홀로그램을 배치할 SpatialLocatorAttachedReferenceFrame의 좌표계에서 홀로그램을 렌더링 하도록 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-267">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="04c7a-268">다른 좌표계를 사용 하 여 렌더링 하기로 결정 한 경우에는 장치 연결 참조 프레임의 좌표계에서 해당 좌표계로 변환을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-268">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="04c7a-269">From **HolographicTagAlongSampleMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="04c7a-269">From **HolographicTagAlongSampleMain::Render**:</span></span>

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

<span data-ttu-id="04c7a-270">간단하죠.</span><span class="sxs-lookup"><span data-stu-id="04c7a-270">That's it!</span></span> <span data-ttu-id="04c7a-271">그러면 홀로그램은 사용자의 응시 방향 앞에서 2 미터의 위치를 "추적" 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-271">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="04c7a-272">이 예제에서는 추가 콘텐츠도 로드 합니다. StationaryQuadRenderer를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04c7a-272">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="04c7a-273">추적 손실 처리</span><span class="sxs-lookup"><span data-stu-id="04c7a-273">Handling tracking loss</span></span>

<span data-ttu-id="04c7a-274">장치를 세계에서 찾을 수 없는 경우 앱은 "추적 손실"을 경험 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-274">When the device can't locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="04c7a-275">Windows Mixed Reality 앱은 위치 추적 시스템에 대 한 이러한 중단을 처리할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-275">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="04c7a-276">기본 SpatialLocator의 LocatabilityChanged 이벤트를 사용 하 여 이러한 중단을 관찰 하 고 응답을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-276">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="04c7a-277">**Appmain:: SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="04c7a-277">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="04c7a-278">앱이 LocatabilityChanged 이벤트를 수신 하는 경우 필요에 따라 동작을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-278">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="04c7a-279">예를 들어 PositionalTrackingInhibited 된 상태에서 앱은 정상 작업을 일시 중지 하 고 경고 메시지를 표시 하는 [태그를 따라 홀로그램](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) 을 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-279">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="04c7a-280">Windows Holographic 앱 템플릿에는 이미 생성 된 LocatabilityChanged 처리기가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-280">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="04c7a-281">기본적으로 위치 추적을 사용할 수 없는 경우 디버그 콘솔에 경고를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-281">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="04c7a-282">앱에서 필요에 따라 응답을 제공 하기 위해이 처리기에 코드를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-282">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="04c7a-283">**Appmain .cpp에서:**</span><span class="sxs-lookup"><span data-stu-id="04c7a-283">From **AppMain.cpp:**</span></span>

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a><span data-ttu-id="04c7a-284">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="04c7a-284">Spatial mapping</span></span>

<span data-ttu-id="04c7a-285">[공간 매핑](spatial-mapping-in-directx.md) api는 좌표계를 사용 하 여 표면 망상의 모델 변환을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="04c7a-285">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="04c7a-286">참조</span><span class="sxs-lookup"><span data-stu-id="04c7a-286">See also</span></span>
* [<span data-ttu-id="04c7a-287">좌표계</span><span class="sxs-lookup"><span data-stu-id="04c7a-287">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="04c7a-288">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="04c7a-288">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* <span data-ttu-id="04c7a-289"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="04c7a-289"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="04c7a-290">DirectX의 헤드 및 눈 응시</span><span class="sxs-lookup"><span data-stu-id="04c7a-290">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="04c7a-291">DirectX의 헤드 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="04c7a-291">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="04c7a-292">DirectX의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="04c7a-292">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
