---
title: 입력 애니메이션 기록
description: MRTK의 입력 애니메이션 기록 시스템에 대 한 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 81e49178a9f218e5d3be796ec6253ccabe5d44fc
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143911"
---
# <a name="input-animation-recording"></a><span data-ttu-id="09242-104">입력 애니메이션 기록</span><span class="sxs-lookup"><span data-stu-id="09242-104">Input animation recording</span></span>

<span data-ttu-id="09242-105">MRTK는 헤드 이동 및 직접 추적 데이터를 애니메이션 파일에 저장할 수 있는 기록 시스템을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-105">MRTK features an recording system by which head movement and hand tracking data can be stored in animation files.</span></span> <span data-ttu-id="09242-106">그런 다음 [입력 시뮬레이션 시스템](input-simulation-service.md)을 사용 하 여 기록 된 데이터를 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-106">The recorded data can then be played back using the [input simulation system](input-simulation-service.md).</span></span>

<span data-ttu-id="09242-107">입력 기록은 다양 한 상황에서 유용한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="09242-107">Recording input is a useful tool in a variety of situations:</span></span>

* <span data-ttu-id="09242-108">상호 작용, 조작, solvers 등에 대 한 자동화 된 테스트 만들기 이러한 테스트에 대 한 컨트롤러 및 손을 이동 하는 것은 시간이 많이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-108">Creating automated tests for interaction, manipulations, solvers, etc. Creating the movement of controllers and hands for these tests can be time consuming.</span></span> <span data-ttu-id="09242-109">입력을 직접 기록 하면 프로세스를 가속화 하 고 실제 데이터를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-109">Recording input directly can speed up the process and provide real-world data.</span></span>
* <span data-ttu-id="09242-110">애니메이션을 통한 UX 요소 사용을 교육 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-110">Teaching the use of UX elements through animations.</span></span>
  <span data-ttu-id="09242-111">사용자에 게 단추 및 다른 개체와 상호 작용 하는 방법을 표시 하면 학습 곡선을 매끄럽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-111">Showing users how to interact with buttons and other objects can smooth the learning curve.</span></span>
* <span data-ttu-id="09242-112">정기적으로 사용 하는 동안 발생할 수 있는 예기치 않은 동작을 디버깅 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-112">Debugging unexpected behavior that may be encountered during regular use.</span></span>
  <span data-ttu-id="09242-113">기록 시스템은 백그라운드에서 최근 입력 기록을 허용 하는 "롤링 버퍼" 개념을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-113">The recording system supports a "rolling buffer" concept that allows recording recent input in the background.</span></span>
  <span data-ttu-id="09242-114">[입력 기록 서비스](#input-recording-service)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="09242-114">See [Input Recording Service](#input-recording-service).</span></span>

## <a name="recording-and-playback-services"></a><span data-ttu-id="09242-115">기록 및 재생 서비스</span><span class="sxs-lookup"><span data-stu-id="09242-115">Recording and playback services</span></span>

<span data-ttu-id="09242-116">입력을 각각 기록 하 고 재생 하기 위한 두 개의 입력 시스템 서비스가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="09242-116">Two input system services are provided to record and play back input respectively.</span></span>

### <a name="input-recording-service"></a><span data-ttu-id="09242-117">입력 기록 서비스</span><span class="sxs-lookup"><span data-stu-id="09242-117">Input recording service</span></span>

<span data-ttu-id="09242-118">[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 기본 카메라 변환과 활성 손 컨트롤러의 데이터를 가져와서 내부 버퍼에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-118">[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) takes data from the main camera transform and active hand controllers and stores it in an internal buffer.</span></span> <span data-ttu-id="09242-119">요청 시이 데이터는 저장소 및 이후 재생을 위해 이진 파일로 직렬화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="09242-119">When requested this data is then serialized into binary files for storage and later replay.</span></span>

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="입력 애니메이션 기록" width="80%" alt="Recording diagram" class="center" />
</a>

<span data-ttu-id="09242-121">입력 기록을 시작 하려면 함수를 호출 [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-121">To start recording input call the [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) function.</span></span> <span data-ttu-id="09242-122">[`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) 기록을 일시 중지 하 고, 지금까지 기록한 데이터는 삭제 하지 않습니다 [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) . 필요한 경우를 사용 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-122">[`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) will pause recording (but not discard the data recorded so far, use [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) to do this if needed).</span></span>

<span data-ttu-id="09242-123">기본적으로 기록 버퍼의 크기는 30초로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="09242-123">By default the size of the recording buffer is limited to 30 seconds.</span></span> <span data-ttu-id="09242-124">이렇게 하면 기록 서비스가 너무 많은 데이터를 누적하지 않고 백그라운드에서 기록을 유지한 다음 필요한 경우 마지막 30초를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-124">This allows the recording service to keep recording in the background without accumulating too much data, and then save the last 30 seconds when required.</span></span> <span data-ttu-id="09242-125">시간 간격을 사용 하 여 변경할 수 [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) 있습니다는 속성 또는 기록을 사용 하 여 제한 되지 않을 수 있습니다는 [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="09242-125">The time interval can be changed using the [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) property, or recording can be unlimited using the [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) option.</span></span>

<span data-ttu-id="09242-126">기록 버퍼의 데이터는 [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) 함수를 사용하여 이진 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-126">The data in the recording buffer can be saved in a binary file using the [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) function.</span></span>

<span data-ttu-id="09242-127">이진 파일 형식에 대한 자세한 내용은 입력 애니메이션 파일 형식 사양 을 [참조하세요.](input-animation-file-format.md)</span><span class="sxs-lookup"><span data-stu-id="09242-127">For details on the binary file format see [Input Animation File Format Specification](input-animation-file-format.md).</span></span>

### <a name="input-playback-service"></a><span data-ttu-id="09242-128">입력 재생 서비스</span><span class="sxs-lookup"><span data-stu-id="09242-128">Input playback service</span></span>

<span data-ttu-id="09242-129">[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) 는 입력 애니메이션 데이터가 있는 이진 파일을 읽은 다음 [InputSimulationService를](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) 통해 이 데이터를 적용하여 기록된 이동을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="09242-129">[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) reads a binary file with input animation data and then applies this data through the [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) to recreate the recorded movements.</span></span>

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="입력 애니메이션 재생" width="80%" alt="Play Back diagram" class="center" />
</a>

<span data-ttu-id="09242-131">입력 애니메이션 재생을 시작하려면 [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) 함수를 사용하여 파일에서 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-131">To start playing back input animation it should be loaded from a file using the [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) function.</span></span>

<span data-ttu-id="09242-132">[재생,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play) [일시 중지](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)또는 [중지를](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) 호출하여 애니메이션 재생을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-132">Call [Play](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play), [Pause](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play), or [Stop](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) to control the animation playback.</span></span>

<span data-ttu-id="09242-133">현재 애니메이션 시간은 [LocalTime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 속성을 통해 직접 제어할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-133">The current animation time can also be controlled directly with the [LocalTime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) property.</span></span>

> [!WARNING]
> <span data-ttu-id="09242-134">입력 애니메이션을 반복하거나 다시 설정하거나 [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 타임라인을 스크러빙하여 직접 설정하면 장면을 조작할 때 예기치 않은 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-134">Looping or resetting input animation or setting [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) directly by scrubbing the timeline may yield unexpected results when manipulating the scene!</span></span> <span data-ttu-id="09242-135">입력 이동만 기록되며 개체 이동 또는 스위치 대칭 이동과 같은 추가 변경 내용은 다시 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-135">Only the input movements are recorded, any additional changes such as moving objects or flipping switches will not be reset.</span></span> <span data-ttu-id="09242-136">되돌릴 수 없는 변경이 이루어진 경우 장면을 다시 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-136">Make sure to reload the scene if irreversible changes have been made.</span></span>

### <a name="editor-tools-for-recording-and-playing-input-animation"></a><span data-ttu-id="09242-137">입력 애니메이션을 기록하고 재생하기 위한 편집기 도구</span><span class="sxs-lookup"><span data-stu-id="09242-137">Editor tools for recording and playing input animation</span></span>

<span data-ttu-id="09242-138">Unity 편집기에서는 입력 애니메이션을 기록하고 검사하기 위한 다양한 도구가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-138">A number of tools exist in the Unity editor for recording and examining input animation.</span></span> <span data-ttu-id="09242-139">이러한 도구는 [입력 시뮬레이션 도구 창에서](input-simulation-service.md#input-simulation-tools-window)액세스할 수 _있으며, Mixed Reality 도구 키트 > 유틸리티 > 입력 시뮬레이션_ 메뉴에서 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-139">These tools can be accessed in the [input simulation tools window](input-simulation-service.md#input-simulation-tools-window), which can be opened from the _Mixed Reality Toolkit > Utilities > Input Simulation_ menu.</span></span>

> [!NOTE]
> <span data-ttu-id="09242-140">입력 기록 및 재생은 재생 모드 중에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-140">Input recording and playback only works during play mode.</span></span>

<span data-ttu-id="09242-141">입력 기록 창에는 두 가지 모드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-141">The input recording window has two modes:</span></span>

* <span data-ttu-id="09242-142">재생 모드 중에 입력을 기록하고 애니메이션 파일에 저장하기 위한 _기록_</span><span class="sxs-lookup"><span data-stu-id="09242-142">_Recording_ for recording input during play mode and saving it to animation files.</span></span>

  <span data-ttu-id="09242-143">기록 단추를 설정/해제 하는 경우 [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 입력을 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-143">When toggling on the recording button the [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) is enabled to record input.</span></span>
  <span data-ttu-id="09242-144">기록 단추를 해제할 때 파일 저장 선택이 표시 되 고 기록 된 입력 애니메이션이 선택한 대상에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="09242-144">When toggling off the recording button a file save selection is shown and the recorded input animation is saved to the selected destination.</span></span>

  <span data-ttu-id="09242-145">이 모드에서 버퍼 시간 제한이 변경 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-145">The buffer time limit can also be changed in this mode.</span></span>

* <span data-ttu-id="09242-146">애니메이션 파일을 로드 한 다음 입력 시뮬레이션 시스템을 통해 입력을 다시 만드는 _재생_</span><span class="sxs-lookup"><span data-stu-id="09242-146">_Playback_ for loading animation files and then recreating input through the input simulation system.</span></span>

  <span data-ttu-id="09242-147">먼저이 모드에서 애니메이션을 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-147">An animation must be loaded in this mode first.</span></span> <span data-ttu-id="09242-148">입력을 기록 모드로 기록한 후에는 결과 애니메이션이 자동으로 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="09242-148">After recording input in recording mode the resulting animation is automatically loaded.</span></span> <span data-ttu-id="09242-149">또는 "로드" 단추를 클릭 하 여 기존 애니메이션 파일을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-149">Alternatively click the "Load" button to select an existing animation file.</span></span>

  <span data-ttu-id="09242-150">왼쪽에서 오른쪽으로 시간 제어 단추는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-150">The time control buttons from left to right are:</span></span>

  * <span data-ttu-id="09242-151">재생 시간을 애니메이션의 시작으로 _다시 설정_ 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-151">_Reset_ the playback time to the start of the animation.</span></span>
  * <span data-ttu-id="09242-152">시간이 지남에 따라 애니메이션을 지속적으로 _재생_ 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-152">_Play_ animation continuously over time.</span></span>
  * <span data-ttu-id="09242-153">_단계_ 1 회 단계를 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-153">_Step_ forward one time step.</span></span>

  <span data-ttu-id="09242-154">슬라이더는 애니메이션 타임 라인을 통해 삭제 하는 데에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-154">The slider can also be used to scrub through the animation timeline.</span></span>

> [!WARNING]
> <span data-ttu-id="09242-155">입력 애니메이션을 반복 하거나 다시 설정 하거나 타임 라인을 삭제 하면 장면을 조작할 때 예기치 않은 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-155">Looping or resetting input animation or scrubbing the timeline may yield unexpected results when manipulating the scene!</span></span> <span data-ttu-id="09242-156">입력 이동만 기록 되며, 개체 이동, 스위치 전환 등의 추가 변경 내용은 다시 설정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="09242-156">Only the input movements are recorded, any additional changes such as moving objects or flipping switches will not be reset.</span></span> <span data-ttu-id="09242-157">취소할 수 없는 변경 내용이 있으면 장면을 다시 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="09242-157">Make sure to reload the scene if irreversible changes have been made.</span></span>
