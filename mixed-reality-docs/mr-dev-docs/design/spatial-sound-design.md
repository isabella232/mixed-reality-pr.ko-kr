---
title: 혼합 현실 애플리케이션에서 공간 소리 사용
description: 공간 소리는 혼합 현실 애플리케이션의 몰입, 접근성 및 UX 디자인을 위한 강력한 도구입니다.
author: kegodin
ms.author: v-hferrone
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality, 공간 음향, 디자인, 스타일, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit, 제스처, 상호 작용, 감쇠
ms.openlocfilehash: d51fbdf16d7186c386f124c773f75dacc8c157fd
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489213"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>혼합 현실 애플리케이션에서 소리를 사용하는 방법

소리를 사용하여 애플리케이션 상태에 대한 사용자의 멘탈 모델을 알리고 강화할 수 있습니다. 적절한 경우 공간화를 사용하여 혼합 현실 세계에 소리를 배치합니다. 이러한 방식으로 감사자와 시각적 개체를 연결하면 상호 작용의 직관적인 특성을 더욱 강화하여 사용자 신뢰도를 높일 수 있습니다.
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>소리를 추가하는 경우

혼합 현실 애플리케이션은 2D 앱보다 소리에 대한 요구가 더 큰 경우가 많습니다. 이는 타일 인터페이스가 없기 때문입니다. 사용자에게 알리거나 상호 작용을 강화할 때 소리를 추가합니다.

### <a name="inform-and-reinforce"></a>정보 및 강화

* 알림과 같이 사용자가 시작하지 않은 이벤트의 경우 소리를 사용하여 변경이 발생했음을 사용자에게 알립니다.
* 상호 작용에는 여러 단계가 있을 수 있습니다. 소리를 사용하여 스테이지 전환을 강화합니다.

상호 작용, 이벤트 및 제안된 소리 특성에 대한 다음 예제를 참조하세요.

### <a name="exercise-restraint"></a>연습 연습

사용자에게 오디오 정보에 대한 무제한 용량이 없습니다.
* 각 소리는 중요하고 구체적인 정보를 전달해야 합니다.
* 앱이 사용자에게 알리기 위해 소리를 재생하면 일시적으로 다른 소리의 볼륨을 줄입니다.
* 단추 가리키기 소리(다음 정보 참조)의 경우 과도한 소리 트리거를 방지하기 위해 시간 지연을 추가합니다.

### <a name="dont-rely-solely-on-sounds"></a>소리만 사용 하지 않음

사용 되는 소리는 사용자에 게 유용 합니다. 그러나 소리가 꺼진 상태 에서도 응용 프로그램을 사용할 수 있는지 확인 합니다.
* 사용자가 청각 장애가 있을 수 있습니다.
* 응용 프로그램은 큰 환경에서 사용할 수 있습니다.
* 사용자에 게 장치 오디오를 사용 하지 않도록 설정 하는 개인 정보 문제나 기타 이유가 있을 수 있습니다.

## <a name="how-to-sonify-interactions"></a>Sonify 상호 작용 방법

혼합 현실의 상호 작용 형식에는 제스처, 직접 조작 및 음성이 포함 됩니다. 이러한 상호 작용의 소리를 선택 하거나 디자인 하려면 다음의 제안 된 특성을 사용 합니다.

### <a name="gesture-interactions"></a>제스처 상호 작용

혼합 현실에서 사용자는 마우스를 사용 하 여 단추와 상호 작용할 수 있습니다. 단추 동작은 일반적으로 사용자가 상호 작용을 취소할 수 있도록 단추를 누르는 대신를 해제할 때 발생 합니다. 이러한 단계를 보강 하려면 소리를 사용 합니다. 멀리 떨어져 있는 단추를 대상으로 하는 사용자를 지원 하기 위해 포인터 가리키기 소리를 사용 하는 것도 고려 합니다.
* 단추 누르기 소리는 짧게 tactile "클릭" 해야 합니다.<br/>예: [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 단추-"unpress" 소리는 유사한 tactile 느낌을 가져야 합니다. 누르기 소리 보다 더 높은 피치는 완료 강화 의미입니다.<br/>예: [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* 가리키기 소리의 경우 낮은 빈도 thud 또는 범프와 같이 약한 및 비 위협 사운드를 사용 하는 것이 좋습니다.

### <a name="direct-manipulation"></a>직접 조작

HoloLens 2 굴절형 손 추적은 사용자 인터페이스 요소의 직접 조작을 지원합니다. 다른 물리적 피드백이 없는 경우 소리는 중요합니다.

사용자가 키 스트로크의 맨 아래에 도달할 때 다른 표시를 얻지 못하기 때문에 *단추 누를* 소리가 중요합니다. 키 이동의 소리 표시는 작고, 미세하고, 폐색될 수 있습니다. 제스처 상호 작용과 마찬가지로 단추 누름은 클릭과 같은 짧고 바둑판식으로 들립니다. 언프레는 비슷한 클릭 소리가 나지만 피치가 높아야 합니다.
* 예: [MRTK_ButtonPress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 예: [MRTK_ButtonUnpress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)

잡기 또는 릴리스 작업을 시각적으로 확인하기는 어렵습니다. 사용자의 손은 종종 시각적 효과를 방해하며 하드 본드 개체에는 "잡기"라는 실제 시각적 아날로그가 없습니다. 소리는 성공적인 잡기 및 릴리스 상호 작용을 효과적으로 전달할 수 있습니다.
* 잡기 작업에는 개체 주위에 손가락이 닫히는 아이디어를 요구하는 짧고 약간 섞인 택실음이 있어야 합니다. 때로는 손의 동작을 전달하기 위해 잡기 소리로 이어지는 "whoosh" 소리도 있습니다.<br/>예: [MRTK_Move_Start.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* 릴리스 작업은 비슷하게 짧고 바둑판식으로 소리를 내야 합니다. 일반적으로 잡기 소리보다 낮은 피치이며 역순으로, 영향을 준 다음, 개체가 배치되고 있음을 알리는 "whoosh"입니다.<br/>예: [MRTK_Move_End.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_End.wav)

*그리기* 상호 작용은 사용자의 손 이동에 따라 결정되는 볼륨이 있는 지속적이고 반복되는 소리를 얻게 됩니다. 손을 빠르게 이동할 때 사용자의 손은 가만히 있고 가장 크게 이동할 때는 자동이어야 합니다.

### <a name="voice-interactions"></a>음성 상호 작용

음성 상호 작용에는 종종 미묘한 시각적 요소가 있습니다. 소리를 사용 하 여 상호 작용 단계를 보강 합니다. 더 많은 톤 소리를 사용 하 여 제스처와 직접 조작 소리를 구분할 수 있습니다.

* 음성 *명령 확인* 에는 양수의 톤을 사용 합니다. 증가 하는 톤 및 주요 음악 간격은 효과적입니다.
* 음성 명령 *실패* 에 대해 더 짧고 작은 음이 음을 사용 합니다. 음이 음을 방지 합니다. 대신 더 percussive 중립적인 소리를 사용 하 여 응용 프로그램이 상호 작용에서 이동 하 고 있음을 통신 합니다.
* 응용 프로그램에 절전 모드 해제 단어가 있는 경우 장치가 *수신 대기를 시작할* 때 짧은 gentle 톤을 사용 합니다. 응용 프로그램이 수신 대기 *하는 동안* 미묘한 루핑 소리를 사용 합니다.

### <a name="notifications"></a>공지

알림은 응용 프로그램 상태 변경 내용 및 사용자가 시작 하지 않은 기타 이벤트를 알립니다. 상태 변경은 프로세스 완료, 메시지 및 전화 통화를 포함할 수 있습니다.

혼합 현실에서 개체는 사용자의 뷰 필드에서 이동 하기도 합니다. 개체 유형과 동작 속도에 따라 달라 지는 spatialized 소리를 사용 하 여 *애니메이션 개체* 를 이동 합니다.
* 애니메이션의 끝에서 spatialized 소리를 재생 하 여 개체의 새 위치를 사용자에 게 알리는 데 도움이 됩니다.
* 점진적 이동의 경우 이동 중에 "whoosh" 소리가 있으면 사용자가 개체를 추적할 수 있습니다.

*메시지 알림* 경고음은 반복적으로 빠르게 들릴 수 있습니다. 중요 한 것은 아닙니다. 중간 범위의 포지티브 톤 소리가 적용 됩니다.

* 들어오는 통화 사운드는 휴대폰 벨 소리와 비슷한 품질을 가져야 합니다. 이러한 소리는 사용자가 통화에 응답할 때까지 재생되는 구를 반복합니다.
* 음성 통신 연결 및 연결 끊김에는 짧은 음음이 있어야 합니다. 연결에 성공했음을 나타내려면 연결 소리는 긍정적인 어조여야 합니다. 연결 끊기 소리는 호출 완료를 나타내는 중립 사운드여야 합니다.

## <a name="handle-spatialization"></a>공간화 처리

공간화는 스테레오 스피커 또는 스피커를 사용하여 혼합 현실 세계에 소리를 배치합니다.

### <a name="which-sounds-to-spatialize"></a>공간화할 소리

공간 위치가 있는 이벤트와 연결된 경우 소리를 공간화해야 합니다. 여기에는 UI, 구체화된 AI 음성 및 시각적 표시기가 포함됩니다.

*사용자 인터페이스* 요소를 공간화하여 사용자가 들은 스테레오 소리의 수를 제한하여 사용자의 음향 "공간"을 정리합니다. 오디오 피드백이 공간화되면 터치, 잡기 및 해제와 같은 조작 상호 작용이 더 자연스럽게 느낄 수 있습니다. 이러한 요소의 거리 감쇠에 대한 다음 정보를 고려합니다.

*시각적 표시기* 및 *구체화된 AI 음성을* 공간화하여 이러한 항목이 보기 필드 밖에 있을 때 사용자에게 직관적으로 알릴 수 있습니다.
    
반면, 잘 정의된 공간 위치가 없는 *얼굴 없는 AI 음성* 및 기타 요소에 대한 공간화를 피합니다. 관련 시각적 요소가 없는 공간화는 사용자가 찾을 수 없는 시각적 요소가 있다고 생각하는 데 방해가 될 수 있습니다.

공간화에는 약간의 CPU 비용이 있습니다. 대부분의 애플리케이션에는 동시에 재생된 두 개의 소리가 있습니다. 이 경우 공간화 비용은 무시할 수 있습니다. MRTK 프레임 속도 모니터를 사용하여 공간화 추가의 영향을 판단할 수 있습니다.

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>거리 기반 감쇠를 적용하는 시기 및 방법

실제 세계에서 멀리 떨어져 있는 소리는 더 조용한 것입니다. 오디오 엔진은 원본 거리를 기준으로이 감쇠를 모델링할 수 있습니다. 관련 정보를 통신할 때 거리 기반 감쇠를 사용 합니다.

*시각적 표시기*, *애니메이션 holograms* 및 기타 정보 사운드에 대 한 거리가 사용자와 관련이 있습니다. 거리 기반 감쇠를 사용 하 여 큐를 직관적으로 제공 합니다.

각 원본에 대 한 감쇠 곡선을 혼합 현실 세계 공간의 크기에 맞게 조정 합니다. 오디오 엔진의 기본 곡선은 종종 kilometer (최대 절반)의 공간을 차지 합니다.

단추 작업 및 기타 상호 작용 *의 점진적 단계* 를 보강 하는 소리는 감쇠를 적용 하지 않아야 합니다. 이러한 소리의 영향을 강화 단추와의 거리를 전달 하는 것 보다 중요 합니다. 많은 단추 클릭을 연속 해 서 사용할 수 있는 경우 특히 키보드를 사용 하면 변형이 혼란을 수 있습니다.

### <a name="which-spatialization-technology-to-use"></a>사용할 spatialization 기술

헤드폰 또는 HoloLens 스피커를 사용 하는 경우 HRTF (head 관련 전송 함수) 기반 spatialization 기술을 사용 합니다. 이러한 기술은 실제 세계의 헤드를 중심으로 하는 소리 전파를 모델링 합니다. 사운드 소스가 한 헤드의 먼 쪽에 있는 경우에도 소리는 감쇠 및 지연이 발생 하 여 먼 귀에 전파 됩니다. 스피커 패닝은 감쇠만 사용 하며, 오른쪽에 소리가 있을 때 왼쪽 귀에 전체 감쇠를 적용 하 고 다른 방법을 적용 합니다. 이 기술은 "정상적인 청각" 수신기가 될 수 있으며 한 가지 귀에서 청각 장애가 있는 수신기에 액세스할 수 없게 됩니다.

## <a name="next-steps"></a>다음 단계

* [Unity에서 공간 소리 사용](../develop/unity/spatial-sound-in-unity.md)
* [Roboraid의 사례 연구](case-study-using-spatial-sound-in-roboraid.md)
* [HoloTour의 사례 연구](case-study-spatial-sound-design-for-holotour.md)
