---
title: DirectX의 헤드 및 눈 응시
description: 네이티브 DirectX 앱에서 헤드 응시 및 눈 추적 으로부터 raycasting 데이터를 요청, 사용 및 압축 풀기 하는 방법에 대해 알아봅니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: 눈에 응시, 헤드-응시, 헤드 추적, 눈 추적, directx, 입력, holograms, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 8b3c63ac7a7edba0ce3173e024139e29d49757ab
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810173"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="af3d3-104">헤드-DirectX에서 응시 및 눈에 응시 입력</span><span class="sxs-lookup"><span data-stu-id="af3d3-104">Head-gaze and eye-gaze input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="af3d3-105">이 문서는 레거시 WinRT 네이티브 Api와 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="af3d3-106">새 네이티브 앱 프로젝트의 경우 **[OPENXR API](openxr-getting-started.md)** 를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="af3d3-107">Windows Mixed Reality에서 눈 및 헤드 응시 입력은 사용자가 원하는 항목을 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-107">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="af3d3-108">데이터를 사용 하 여 [head-응시 및 commit](../../design/gaze-and-commit.md)과 같은 기본 입력 모델을 구동 하 고 다양 한 상호 작용 형식에 대 한 컨텍스트를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-108">You can use the data to drive primary input models like [head-gaze and commit](../../design/gaze-and-commit.md), and provide context for different interaction types.</span></span> <span data-ttu-id="af3d3-109">API를 통해 사용할 수 있는 두 가지 유형의 응시 벡터 인 head-응시 및 눈에 주목 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-109">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="af3d3-110">둘 다 원점 및 방향을 사용 하 여 3 차원 광선으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-110">Both are provided as a three-dimensional ray with an origin and direction.</span></span> <span data-ttu-id="af3d3-111">그런 다음 응용 프로그램은 자신의 장면이 나 실제 세계에이를 다시 캐스팅 하 고 사용자가 대상으로 지정 하는 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-111">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="af3d3-112">**헤드-응시** 는 사용자의 헤드가 가리키는 방향을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-112">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="af3d3-113">헤드-응시는 장치 자체의 위치 및 정방향 방향으로, 위치는 두 표시 사이의 중심점으로 생각 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-113">Think of head-gaze as the position and forward direction of the device itself, with the position as the center point between the two displays.</span></span> <span data-ttu-id="af3d3-114">헤드-응시는 모든 혼합 현실 장치에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-114">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="af3d3-115">**눈** 에 보기는 사용자의 눈이 향하는 방향을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-115">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="af3d3-116">원점은 사용자의 눈 사이에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-116">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="af3d3-117">아이 추적 시스템을 포함 하는 혼합 현실 장치에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-117">It's available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="af3d3-118">[SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API를 통해 헤드 및 눈에 광선 모두에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-118">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="af3d3-119">[SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 를 호출 하 여 지정 된 타임 스탬프 및 [좌표계](coordinate-systems-in-directx.md)에서 새 SpatialPointerPose 개체를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-119">Call [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="af3d3-120">이 SpatialPointerPose는 헤드-응시 원점 및 방향을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-120">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="af3d3-121">눈동자 추적을 사용할 수 있는 경우에도 눈에 잘 응시 된 원본 및 방향을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-121">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

### <a name="device-support"></a><span data-ttu-id="af3d3-122">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="af3d3-122">Device support</span></span>

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="af3d3-123"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="af3d3-123"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="af3d3-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="af3d3-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="af3d3-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="af3d3-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="af3d3-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="af3d3-126"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="af3d3-127">헤드 게이즈(head-gaze)</span><span class="sxs-lookup"><span data-stu-id="af3d3-127">Head-gaze</span></span></td>
     <td><span data-ttu-id="af3d3-128">✔️</span><span class="sxs-lookup"><span data-stu-id="af3d3-128">✔️</span></span></td>
     <td><span data-ttu-id="af3d3-129">✔️</span><span class="sxs-lookup"><span data-stu-id="af3d3-129">✔️</span></span></td>
     <td><span data-ttu-id="af3d3-130">✔️</span><span class="sxs-lookup"><span data-stu-id="af3d3-130">✔️</span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="af3d3-131">눈-응시</span><span class="sxs-lookup"><span data-stu-id="af3d3-131">Eye-gaze</span></span></td>
     <td>❌</td>
     <td><span data-ttu-id="af3d3-132">✔️</span><span class="sxs-lookup"><span data-stu-id="af3d3-132">✔️</span></span></td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a><span data-ttu-id="af3d3-133">헤드-응시 사용</span><span class="sxs-lookup"><span data-stu-id="af3d3-133">Using head-gaze</span></span>

<span data-ttu-id="af3d3-134">헤드-응시에 액세스 하려면  [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 를 호출 하 여 새 SpatialPointerPose 개체를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-134">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="af3d3-135">다음 매개 변수를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-135">Pass the following parameters.</span></span>
 - <span data-ttu-id="af3d3-136">헤드-응시에 대해 원하는 좌표계를 나타내는 [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 입니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-136">A [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the coordinate system you want for the head-gaze.</span></span> <span data-ttu-id="af3d3-137">이는 다음 코드의 *coordinateSystem* 변수로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-137">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="af3d3-138">자세한 내용은 [좌표계](coordinate-systems-in-directx.md) 개발자 가이드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="af3d3-138">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="af3d3-139">요청 된 head의 정확한 시간을 나타내는 [타임 스탬프](/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) 입니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-139">A [Timestamp](/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="af3d3-140">일반적으로 현재 프레임이 표시 되는 시간에 해당 하는 타임 스탬프를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-140">Typically, you'll use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="af3d3-141">현재 [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)를 통해 액세스할 수 있는 [HolographicFramePrediction](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) 개체에서이 예측 표시 타임 스탬프를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-141">You can get this predicted display timestamp from a  [HolographicFramePrediction](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="af3d3-142">이 HolographicFramePrediction 개체는 다음 코드의 *예측* 변수로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-142">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="af3d3-143">유효한 SpatialPointerPose 면 head position 및 정방향 방향은 속성으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-143">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="af3d3-144">다음 코드에서는 이러한 항목에 액세스 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-144">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="af3d3-145">눈동자 사용-응시</span><span class="sxs-lookup"><span data-stu-id="af3d3-145">Using eye-gaze</span></span>

<span data-ttu-id="af3d3-146">사용자가 눈에 잘 맞는 입력을 사용 하려면 장치를 처음 사용할 때 각 사용자가 [눈 추적 사용자 보정](/hololens/hololens-calibration) 을 통과 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-146">For your users to use eye-gaze input, each user has to go through an [eye tracking user calibration](/hololens/hololens-calibration) the first time they use the device.</span></span> <span data-ttu-id="af3d3-147">눈에 응시 API는 헤드-응시와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-147">The eye-gaze API is similar to head-gaze.</span></span>
<span data-ttu-id="af3d3-148">이 API는 동일한 [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API를 사용 합니다 .이 API는 장면에 대해 raycast 수 있는 광선 및 방향을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-148">It uses the same [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="af3d3-149">유일한 차이점은 사용 하기 전에 명시적으로 눈동자 추적을 사용 하도록 설정 해야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-149">The only difference is that you need to explicitly enable eye tracking before using it:</span></span>
1. <span data-ttu-id="af3d3-150">앱에서 눈 추적을 사용할 수 있는 사용자 권한을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-150">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="af3d3-151">패키지 매니페스트에서 "응시 입력" 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-151">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="af3d3-152">눈동자-응시 입력에 대 한 액세스 요청</span><span class="sxs-lookup"><span data-stu-id="af3d3-152">Requesting access to eye-gaze input</span></span>

<span data-ttu-id="af3d3-153">앱이 시작 되 면 [EyesPose:: RequestAccessAsync](/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) 를 호출 하 여 눈동자 추적에 대 한 액세스를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-153">When your app is starting up, call [EyesPose::RequestAccessAsync](/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="af3d3-154">필요한 경우 시스템에서 사용자에 게 묻는 메시지를 표시 하 고 액세스가 부여 된 후에 [GazeInputAccessStatus:: Allowed](/uwp/api/windows.ui.input.gazeinputaccessstatus) 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-154">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="af3d3-155">비동기 호출 이므로 약간의 추가 관리가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-155">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="af3d3-156">다음 예제에서는 분리 된 std:: thread를 회전 하 여 *m_isEyeTrackingEnabled* 이라는 멤버 변수에 저장 하는 결과를 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-156">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
<span data-ttu-id="af3d3-157">분리 된 스레드를 시작 하는 것은 비동기 호출을 처리 하는 한 가지 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-157">Starting a detached thread is just one option for handling async calls.</span></span> <span data-ttu-id="af3d3-158">C + +/WinRT. 지 원하는 새로운 [co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) 기능을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-158">You could also use the new [co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="af3d3-159">사용자에 게 권한을 요청 하는 또 다른 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-159">Here's another example for asking for user permission:</span></span>
-   <span data-ttu-id="af3d3-160">EyesPose:: IsSupported ()를 사용 하면 응용 프로그램에서 아이 트래커가 있는 경우에만 사용 권한 대화 상자를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-160">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there's an eye tracker.</span></span>
-   <span data-ttu-id="af3d3-161">GazeInputAccessStatus m_gazeInputAccessStatus; 이는 사용 권한 프롬프트를 다시 표시 하지 않도록 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-161">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="af3d3-162">*응시 입력* 기능 선언</span><span class="sxs-lookup"><span data-stu-id="af3d3-162">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="af3d3-163">*솔루션 탐색기* 에서 appxmanifest.xml 파일을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-163">Double-click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="af3d3-164">그런 다음 *기능* 섹션으로 이동 하 여 *응시 입력* 기능을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-164">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![입력 기능 응시](images/gaze-input-capability.png)

<span data-ttu-id="af3d3-166">그러면 appxmanifest.xml 파일의 *Package* 섹션에 다음 줄이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-166">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="af3d3-167">눈에 보기-응시 광선</span><span class="sxs-lookup"><span data-stu-id="af3d3-167">Getting the eye-gaze ray</span></span>

<span data-ttu-id="af3d3-168">ET에 대 한 액세스를 받은 후에는 모든 프레임에서 눈에 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-168">Once you have received access to ET, you're free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="af3d3-169">Head-응시와 마찬가지로 원하는 타임 스탬프 및 좌표계를 사용 하 여 [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 를 호출 하 여 [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-169">As with head-gaze, get the [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="af3d3-170">SpatialPointerPose는 [눈동자](/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) 속성을 통해 [EyesPose](/uwp/api/windows.perception.people.eyespose) 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-170">The SpatialPointerPose contains an [EyesPose](/uwp/api/windows.perception.people.eyespose) object through the [Eyes](/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="af3d3-171">이는 눈동자 추적을 사용 하는 경우에만 null이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-171">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="af3d3-172">여기에서 [EyesPose:: IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)를 호출 하 여 장치의 사용자에 게 눈 추적 보정이 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-172">From there, you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="af3d3-173">그런 다음, [응시](/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) 속성을 사용 하 여 눈에 SpatialRay 위치와 방향을 포함 하는 [](/uwp/api/windows.perception.spatial.spatialray) 를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-173">Next, use the [Gaze](/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the [SpatialRay](/uwp/api/windows.perception.spatial.spatialray) containing the eye-gaze position and direction.</span></span> <span data-ttu-id="af3d3-174">응시 속성은 null 일 수 있으므로이를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-174">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="af3d3-175">이는 보정 된 사용자가 일시적으로 눈동자를 닫는 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-175">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="af3d3-176">다음 코드에서는 눈에 잘 응시 하는 빛에 액세스 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-176">The following code shows how to access the eye-gaze ray.</span></span>

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-isnt-available"></a><span data-ttu-id="af3d3-177">눈동자 추적을 사용할 수 없는 경우 대체 (Fallback)</span><span class="sxs-lookup"><span data-stu-id="af3d3-177">Fallback when eye tracking isn't available</span></span>

<span data-ttu-id="af3d3-178">[눈 추적 디자인 문서](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available)에 설명 된 대로 디자이너와 개발자는 모두 아이 추적 데이터를 사용할 수 없는 인스턴스를 인식 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-178">As mentioned in our [eye tracking design docs](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available), both designers and developers should be aware of instances where eye tracking data may not be available.</span></span>

<span data-ttu-id="af3d3-179">데이터를 사용할 수 없는 다양 한 이유는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-179">There are various reasons for data being unavailable:</span></span>
* <span data-ttu-id="af3d3-180">사용자가 보정 되지 않음</span><span class="sxs-lookup"><span data-stu-id="af3d3-180">A user not being calibrated</span></span>
* <span data-ttu-id="af3d3-181">사용자가 자신의 눈 추적 데이터에 대 한 앱 액세스를 거부 했습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-181">A user has denied the app access to his/her eye tracking data</span></span>
* <span data-ttu-id="af3d3-182">HoloLens 센터 또는 머리카락의 스머지와 같은 임시 interferences 사용자의 눈을 occluding 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-182">Temporary interferences, such as smudges on the HoloLens visor or hair occluding the user's eyes.</span></span> 

<span data-ttu-id="af3d3-183">이 문서에서 일부 Api를 이미 언급 했지만, 다음에는이에 대 한 빠른 참조로 사용할 수 있는 눈 추적을 감지 하는 방법에 대 한 요약을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-183">While some of the APIs have already been mentioned in this document, in the following, we provide a summary of how to detect that eye tracking is available as a quick reference:</span></span> 

* <span data-ttu-id="af3d3-184">시스템이 아이 추적을 지원 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-184">Check that the system supports eye tracking at all.</span></span> <span data-ttu-id="af3d3-185">다음 *메서드* 를 호출 합니다. [EyesPose ()](/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span><span class="sxs-lookup"><span data-stu-id="af3d3-185">Call the following *method*: [Windows.Perception.People.EyesPose.IsSupported()](/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span></span>

* <span data-ttu-id="af3d3-186">사용자가 보정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-186">Check that the user is calibrated.</span></span> <span data-ttu-id="af3d3-187">다음 *속성* 을 호출 합니다. [EyesPose. IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span><span class="sxs-lookup"><span data-stu-id="af3d3-187">Call the following *property*: [Windows.Perception.People.EyesPose.IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span></span>   

* <span data-ttu-id="af3d3-188">사용자에 게 눈 추적 데이터를 사용할 수 있는 권한을 부여 했는지 확인 합니다. 현재 _' GazeInputAccessStatus '_ 를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-188">Check that the user has given your app permission to use their eye tracking data: Retrieve the current _'GazeInputAccessStatus'_.</span></span> <span data-ttu-id="af3d3-189">이 작업을 수행 하는 방법에 대 한 예제는 [응시 입력에 대 한 액세스 요청](/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input)에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-189">An example on how to do this is explained at [Requesting access to gaze input](/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span></span> 

<span data-ttu-id="af3d3-190">받은 눈동자 추적 데이터 업데이트 사이에 시간 제한을 추가 하 고, 아래 설명 된 대로 head-응시로 대체 하 여 눈동자 추적 데이터가 부실 하지 않은지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-190">You may also want to check that your eye tracking data isn't stale by adding a timeout between received eye tracking data updates and otherwise fallback to head-gaze as discussed below.</span></span>   
<span data-ttu-id="af3d3-191">자세한 내용은 [대체 디자인 고려 사항](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="af3d3-191">Visit our [fallback design considerations](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) for more information.</span></span>

<br>

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="af3d3-192">다른 입력과의 응시 상관 관계</span><span class="sxs-lookup"><span data-stu-id="af3d3-192">Correlating gaze with other inputs</span></span>

<span data-ttu-id="af3d3-193">경우에 따라 과거의 이벤트에 해당 하는 [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) 이 필요 하다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-193">Sometimes you may find that you need a [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="af3d3-194">예를 들어 사용자가 공중 탭을 사용 하는 경우 앱에서 원하는 내용을 알고 싶을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-194">For example, if the user does an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="af3d3-195">이러한 목적을 위해 시스템 입력 처리와 표시 시간 사이의 대기 시간 때문에 예측 된 프레임 시간에 [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 를 사용 하는 것은 정확 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-195">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="af3d3-196">또한 대상 지정을 위해 눈동자-응시를 사용 하는 경우 커밋 작업을 완료 하기 전에도 눈에 잘 이동 하는 경향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-196">Also, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="af3d3-197">이는 간단한 공기 탭에 대 한 문제는 적지만 긴 음성 명령을 빠른 시각 이동과 결합할 때 더 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-197">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="af3d3-198">이 시나리오를 처리 하는 한 가지 방법은 입력 이벤트에 해당 하는 기록 타임 스탬프를 사용 하 여  [SpatialPointerPose:: TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)에 대 한 추가 호출을 수행 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-198">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="af3d3-199">그러나 SpatialInteractionManager을 통해 라우팅하는 입력의 경우 더 쉬운 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-199">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="af3d3-200">[SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 에는 고유한 [TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-200">The [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its own [TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="af3d3-201">이를 호출 하면 추측 하지 않고 완벽 하 게 상호 관련 된 [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-201">Calling that will provide a perfectly correlated [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="af3d3-202">SpatialInteractionSourceStates로 작업 하는 방법에 대 한 자세한 내용은 DirectX 설명서 [에서 직접 및 동작 컨트롤러](hands-and-motion-controllers-in-directx.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="af3d3-202">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

<br>

## <a name="calibration"></a><span data-ttu-id="af3d3-203">보정</span><span class="sxs-lookup"><span data-stu-id="af3d3-203">Calibration</span></span>

<span data-ttu-id="af3d3-204">눈 추적을 정확 하 게 수행 하려면 각 사용자가 [눈 추적 사용자 보정](/hololens/hololens-calibration)을 진행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-204">For eye tracking to work accurately, each user is required to go through an [eye tracking user calibration](/hololens/hololens-calibration).</span></span> <span data-ttu-id="af3d3-205">이를 통해 장치는 사용자에 게 더 편안 하 고 높은 품질의 시청 환경을 제공 하 고 동시에 정확한 시각 추적을 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-205">This allows the device to adjust the system for a more comfortable and higher quality viewing experience for the user and to ensure accurate eye tracking at the same time.</span></span> <span data-ttu-id="af3d3-206">개발자는 사용자 보정을 관리 하기 위해 최종 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-206">Developers don’t need to do anything on their end to manage user calibration.</span></span> <span data-ttu-id="af3d3-207">시스템은 다음과 같은 상황에서 사용자에 게 장치를 보정할 것인지 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-207">The system will ensure that the user gets prompted to calibrate the device under the following circumstances:</span></span>
* <span data-ttu-id="af3d3-208">사용자가 처음으로 장치를 사용 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-208">The user is using the device for the first time</span></span>
* <span data-ttu-id="af3d3-209">사용자가 이전에 보정 프로세스를 옵트아웃 했음</span><span class="sxs-lookup"><span data-stu-id="af3d3-209">The user previously opted out of the calibration process</span></span>
* <span data-ttu-id="af3d3-210">사용자가 장치를 마지막으로 사용 했을 때 보정 프로세스가 성공 하지 못함</span><span class="sxs-lookup"><span data-stu-id="af3d3-210">The calibration process didn't succeed the last time the user used the device</span></span>

<span data-ttu-id="af3d3-211">개발자는 눈 추적 데이터를 사용할 수 없는 사용자를 적절 하 게 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af3d3-211">Developers should make sure to provide adequate support for users where eye tracking data may not be available.</span></span> <span data-ttu-id="af3d3-212">[HoloLens 2의 시각 추적](../../design/eye-tracking.md)에서 대체 솔루션에 대 한 고려 사항에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="af3d3-212">Learn more about considerations for fallback solutions at [Eye tracking on HoloLens 2](../../design/eye-tracking.md).</span></span>

<br>

## <a name="see-also"></a><span data-ttu-id="af3d3-213">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af3d3-213">See also</span></span>

* [<span data-ttu-id="af3d3-214">조정</span><span class="sxs-lookup"><span data-stu-id="af3d3-214">Calibration</span></span>](/hololens/hololens-calibration)
* [<span data-ttu-id="af3d3-215">DirectX의 좌표계</span><span class="sxs-lookup"><span data-stu-id="af3d3-215">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="af3d3-216">눈동자-HoloLens에서 응시 2</span><span class="sxs-lookup"><span data-stu-id="af3d3-216">Eye-gaze on HoloLens 2</span></span>](../../design/eye-tracking.md)
* [<span data-ttu-id="af3d3-217">입력 모델 응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="af3d3-217">Gaze and commit input model</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="af3d3-218">DirectX의 헤드 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="af3d3-218">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="af3d3-219">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="af3d3-219">Voice Input in DirectX</span></span>](voice-input-in-directx.md)