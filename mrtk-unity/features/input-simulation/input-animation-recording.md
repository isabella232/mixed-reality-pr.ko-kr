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
# <a name="input-animation-recording"></a>입력 애니메이션 기록

MRTK는 헤드 이동 및 직접 추적 데이터를 애니메이션 파일에 저장할 수 있는 기록 시스템을 제공 합니다. 그런 다음 [입력 시뮬레이션 시스템](input-simulation-service.md)을 사용 하 여 기록 된 데이터를 재생할 수 있습니다.

입력 기록은 다양 한 상황에서 유용한 도구입니다.

* 상호 작용, 조작, solvers 등에 대 한 자동화 된 테스트 만들기 이러한 테스트에 대 한 컨트롤러 및 손을 이동 하는 것은 시간이 많이 걸릴 수 있습니다. 입력을 직접 기록 하면 프로세스를 가속화 하 고 실제 데이터를 제공할 수 있습니다.
* 애니메이션을 통한 UX 요소 사용을 교육 합니다.
  사용자에 게 단추 및 다른 개체와 상호 작용 하는 방법을 표시 하면 학습 곡선을 매끄럽게 만들 수 있습니다.
* 정기적으로 사용 하는 동안 발생할 수 있는 예기치 않은 동작을 디버깅 합니다.
  기록 시스템은 백그라운드에서 최근 입력 기록을 허용 하는 "롤링 버퍼" 개념을 지원 합니다.
  [입력 기록 서비스](#input-recording-service)를 참조 하세요.

## <a name="recording-and-playback-services"></a>기록 및 재생 서비스

입력을 각각 기록 하 고 재생 하기 위한 두 개의 입력 시스템 서비스가 제공 됩니다.

### <a name="input-recording-service"></a>입력 기록 서비스

[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 기본 카메라 변환과 활성 손 컨트롤러의 데이터를 가져와서 내부 버퍼에 저장 합니다. 요청 시이 데이터는 저장소 및 이후 재생을 위해 이진 파일로 직렬화 됩니다.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="입력 애니메이션 기록" width="80%" alt="Recording diagram" class="center" />
</a>

입력 기록을 시작 하려면 함수를 호출 [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) 합니다. [`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) 기록을 일시 중지 하 고, 지금까지 기록한 데이터는 삭제 하지 않습니다 [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) . 필요한 경우를 사용 하 여이 작업을 수행 합니다.

기본적으로 기록 버퍼의 크기는 30초로 제한됩니다. 이렇게 하면 기록 서비스가 너무 많은 데이터를 누적하지 않고 백그라운드에서 기록을 유지한 다음 필요한 경우 마지막 30초를 저장할 수 있습니다. 시간 간격을 사용 하 여 변경할 수 [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) 있습니다는 속성 또는 기록을 사용 하 여 제한 되지 않을 수 있습니다는 [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) 옵션입니다.

기록 버퍼의 데이터는 [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) 함수를 사용하여 이진 파일에 저장할 수 있습니다.

이진 파일 형식에 대한 자세한 내용은 입력 애니메이션 파일 형식 사양 을 [참조하세요.](input-animation-file-format.md)

### <a name="input-playback-service"></a>입력 재생 서비스

[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) 는 입력 애니메이션 데이터가 있는 이진 파일을 읽은 다음 [InputSimulationService를](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) 통해 이 데이터를 적용하여 기록된 이동을 다시 만듭니다.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="입력 애니메이션 재생" width="80%" alt="Play Back diagram" class="center" />
</a>

입력 애니메이션 재생을 시작하려면 [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) 함수를 사용하여 파일에서 로드해야 합니다.

[재생,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play) [일시 중지](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)또는 [중지를](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) 호출하여 애니메이션 재생을 제어합니다.

현재 애니메이션 시간은 [LocalTime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 속성을 통해 직접 제어할 수도 있습니다.

> [!WARNING]
> 입력 애니메이션을 반복하거나 다시 설정하거나 [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 타임라인을 스크러빙하여 직접 설정하면 장면을 조작할 때 예기치 않은 결과가 발생할 수 있습니다. 입력 이동만 기록되며 개체 이동 또는 스위치 대칭 이동과 같은 추가 변경 내용은 다시 설정되지 않습니다. 되돌릴 수 없는 변경이 이루어진 경우 장면을 다시 로드해야 합니다.

### <a name="editor-tools-for-recording-and-playing-input-animation"></a>입력 애니메이션을 기록하고 재생하기 위한 편집기 도구

Unity 편집기에서는 입력 애니메이션을 기록하고 검사하기 위한 다양한 도구가 있습니다. 이러한 도구는 [입력 시뮬레이션 도구 창에서](input-simulation-service.md#input-simulation-tools-window)액세스할 수 _있으며, Mixed Reality 도구 키트 > 유틸리티 > 입력 시뮬레이션_ 메뉴에서 열 수 있습니다.

> [!NOTE]
> 입력 기록 및 재생은 재생 모드 중에만 작동합니다.

입력 기록 창에는 두 가지 모드가 있습니다.

* 재생 모드 중에 입력을 기록하고 애니메이션 파일에 저장하기 위한 _기록_

  기록 단추를 설정/해제 하는 경우 [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 입력을 기록할 수 있습니다.
  기록 단추를 해제할 때 파일 저장 선택이 표시 되 고 기록 된 입력 애니메이션이 선택한 대상에 저장 됩니다.

  이 모드에서 버퍼 시간 제한이 변경 될 수도 있습니다.

* 애니메이션 파일을 로드 한 다음 입력 시뮬레이션 시스템을 통해 입력을 다시 만드는 _재생_

  먼저이 모드에서 애니메이션을 로드 해야 합니다. 입력을 기록 모드로 기록한 후에는 결과 애니메이션이 자동으로 로드 됩니다. 또는 "로드" 단추를 클릭 하 여 기존 애니메이션 파일을 선택 합니다.

  왼쪽에서 오른쪽으로 시간 제어 단추는 다음과 같습니다.

  * 재생 시간을 애니메이션의 시작으로 _다시 설정_ 합니다.
  * 시간이 지남에 따라 애니메이션을 지속적으로 _재생_ 합니다.
  * _단계_ 1 회 단계를 진행 합니다.

  슬라이더는 애니메이션 타임 라인을 통해 삭제 하는 데에도 사용할 수 있습니다.

> [!WARNING]
> 입력 애니메이션을 반복 하거나 다시 설정 하거나 타임 라인을 삭제 하면 장면을 조작할 때 예기치 않은 결과가 발생할 수 있습니다. 입력 이동만 기록 되며, 개체 이동, 스위치 전환 등의 추가 변경 내용은 다시 설정 되지 않습니다. 취소할 수 없는 변경 내용이 있으면 장면을 다시 로드 해야 합니다.
