---
title: 시선 추적
description: Holographic 환경에서 사용할 경우 HoloLens 2에 대 한 시각 추적 및 새로운 사용자 이해 수준을 알아봅니다.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: 눈 추적, 혼합 현실, 입력, 눈에 응시, 보정, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, 혼합 현실 도구 키트, 의도, 작업
ms.openlocfilehash: a4010e5244539909d2b04cdb9e2044672d1decab
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143239"
---
# <a name="eye-tracking-on-hololens-2"></a>HoloLens 2의 시선 추적

![MRTK의 아이 추적 데모](images/mrtk_et_scenemenu.jpg)

HoloLens 2를 사용 하면 개발자에 게 사용자가 보고 있는 항목에 대 한 정보를 사용할 수 있는 기능을 제공 하 여 holographic 환경 내에서 새로운 수준의 컨텍스트 및 인간 이해를 허용할 수 있습니다. 이 페이지에서는 개발자가 다양 한 사용 사례에 대 한 눈 추적을 활용 하는 방법 및 눈에 잘 맞는 사용자 상호 작용을 디자인할 때 검색할 사항을 설명 합니다. 

아이 추적 API는 사용자의 개인 정보를 염두에 두면 서 식별 가능한 정보, 특히 생체 인식을 피할 수 있도록 설계 되었습니다. 아이 추적 지원 응용 프로그램의 경우 사용자는 눈동자 추적 정보를 사용할 수 있는 권한을 앱에 부여 해야 합니다.

### <a name="device-support"></a>디바이스 지원

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>기능</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
</tr>
<tr>
     <td>눈-응시</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

<br>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>헤드 및 눈 추적 디자인 개념 데모

요약 및 눈 추적 디자인 개념이 작동 하는 것을 확인 하려는 경우 아래 [Holograms 추적 및 눈동자]() 추적 비디오 데모를 확인 하세요. 완료 되 면 특정 항목에 대 한 자세한 정보를 계속 확인할 수 있습니다.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

## <a name="calibration"></a>보정 

눈 추적을 정확 하 게 수행 하려면 각 사용자가 holographic 대상 집합을 확인 해야 하는 [눈 추적 사용자 보정](/hololens/hololens-calibration) 을 통과 해야 합니다. 이를 통해 장치는 사용자에 게 더 편안 하 고 높은 품질의 시청 환경을 제공 하 고 동시에 정확한 시각 추적을 보장 합니다. 

시각 추적은 대부분의 사용자에 게 작동 하지만 사용자가 성공적으로 보정할 수 없는 드문 경우도 있습니다. 보정은 다음을 비롯 한 다양 한 이유로 실패할 수 있습니다. 
* 사용자가 이전에 보정 프로세스를 옵트아웃 했음
* 사용자가 무시 하 고 보정 대상을 팔 로우 하지 않았습니다.
* 사용자에 게 시스템에서 아직 지원 하지 않는 특정 유형의 연락처 lenses 및가 있습니다. 
* 사용자에게 특정 눈 병과, 눈 상태 또는 시스템이 아직 지원하지 않는 안과가 있습니다.  
* HoloLens 바이저 또는 안경의 스미징, 눈 앞의 머리로 인한 집중적인 직접 스래핑 및 폐색과 같은 안정적인 시선 추적을 방해하는 외부 요소

개발자는 시선 추적 데이터를 사용할 수 없는 사용자(성공적으로 보정할 수 없는 사용자)에 대해 적절한 지원을 제공해야 합니다. 대체 솔루션에 대한 권장 사항은 이 페이지 아래쪽의 섹션에 있습니다. 

보정 및 원활한 환경을 보장하는 방법에 대해 자세히 알아보려면 [시선 추적 사용자 보정](/hololens/hololens-calibration) 페이지를 확인하세요.

<br>

## <a name="available-eye-tracking-data"></a>사용 가능한 시선 추적 데이터

시선 응시 입력에 대한 특정 사용 사례에 대해 자세히 알아보기 전에 HoloLens 2 시선 추적 [API에서](/uwp/api/windows.perception.people.eyespose) 제공하는 기능을 간략하게 설명하려고 합니다. 개발자는 약 _30FPS(30Hz)에서_ 단일 시선 응시 광선(응시 원점 및 방향)에 액세스할 수 있습니다.
시선 추적 데이터에 액세스하는 방법에 대한 자세한 내용은 [DirectX에서 시선 응시를 사용하고 Unity에서 시선 응시를](../develop/native/gaze-in-directx.md) 사용하기 위한 개발자 가이드를 [참조하세요.](https://aka.ms/mrtk-eyes)

예측된 시선 응시는 실제 대상 주위의 시각적 각도에서 약 1.5도 이내입니다(아래 그림 참조). 약간의 부정확성이 예상되면 개발자는 이 하한 값을 중심으로 약간의 여백을 계획해야 합니다(예: 2.0-3.0도는 훨씬 더 편안하게 환경을 생성할 수 있음). 아래에서는 작은 대상 선택을 해결하는 방법을 자세히 설명합니다. 시선 추적이 정확히 작동하려면 각 사용자가 시선 추적 사용자 보정을 진행해야 합니다. 

![2m 거리에서 최적 대상 크기](images/gazetargeting-size-1000px.jpg)<br>
*2미터 거리에 있는 최적 대상 크기*

<br>

## <a name="use-cases"></a>사용 사례

시선 추적을 사용하여 애플리케이션에서는 사용자가 실시간으로 보는 곳을 추적할 수 있습니다. 다음 사용 사례에서는 혼합 현실의 HoloLens 2 대한 시선 추적에서 가능한 몇 가지 상호 작용에 대해 설명합니다.
이러한 사용 사례는 아직 Holographic Shell 환경(즉, HoloLens 2 시작할 때 표시되는 인터페이스)의 일부가 아닙니다.
[혼합 현실 도구 키트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)에서이 중 일부를 사용해 볼 수 있습니다 .이 도구 키트는 빠르고 간편 하 게 지원 되는 대상 선택 항목과 같은 눈 추적 사용에 대 한 몇 가지 흥미롭고 강력한 예제를 제공 하 고 사용자가 보는 내용에 따라 자동으로 텍스트를 스크롤합니다. 

### <a name="user-intent"></a>사용자 의도

사용자가 확인 하는 위치와 위치에 대 한 정보는 음성, 실습 및 컨트롤러와 같은 **다른 입력을 위한 강력한 컨텍스트** 를 제공 합니다.
이러한 컨텍스트를 다양한 작업에서 사용할 수 있습니다.
예를 들어,이는 홀로그램을 확인 하  고 *"선택"* ( [응시 및 커밋](gaze-and-commit.md)) 또는 "준비 중 ... *"* 이라고 하 고 사용자가 홀로그램을 배치할 위치를 확인 하 고, *"... "*. 이에 대한 예는 [Mixed Reality Toolkit - 시선 지원 대상 선택](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) 및 [Mixed Reality Toolkit - 시선 지원 대상 위치 지정](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html)에서 찾을 수 있습니다.

또한 사용자 의도에 대 한 예제에는 사용자가 합의서 등 가상 에이전트 및 대화형 holograms 참여를 개선 하기 위해 확인 하는 내용에 대 한 정보가 포함 될 수 있습니다. 예를 들어 가상 에이전트는 현재 표시 되는 내용에 따라 사용 가능한 옵션과 해당 동작을 조정할 수 있습니다. 

### <a name="implicit-actions"></a>암시적 작업

암시적 작업의 범주는 사용자 의도와 밀접하게 관련되어 있습니다.
Holograms 또는 사용자 인터페이스 요소는 사용자가 시스템과 상호 작용 하는 것 처럼 보이지만 시스템 및 사용자가 동기화 되는 것 처럼 보일 수 있는 instinctual 방식으로 반응 합니다. 한 가지 예는 사용자가 긴 텍스트를 읽을 수 있는 **눈에 잘 맞는 자동 스크롤** 입니다. 사용자가 텍스트 상자 아래쪽에 있으면 손가락을 떼지 않고 사용자를 읽기 흐름으로 유지할 수 있습니다.  
이에 대 한 주요 측면은 스크롤 속도가 사용자의 읽기 속도에 적응 하는 것입니다.
또 다른 예로, 사용자가 중심으로 하는 것과 정확히 일치 하는 것을 느낄 수 있는 **눈에 잘 지 원하는 확대/축소 및 이동** 이 있습니다. 확대/축소 속도를 트리거하거나 제어 하는 것은 음성 또는 직접 입력을 통해 제어할 수 있습니다 .이는 사용자에 게 불필요 한 제어를 제공 하는 데 중요 합니다. 이러한 디자인 고려 사항은 아래에서 자세히 설명 합니다. 확대하면 사용자는 거리 과정을 원활하게 따라 시선 응시를 사용하여 자신의 지역을 탐색할 수 있습니다.
이러한 유형의 상호 작용을 나타내는 데모 예제는 [Mixed Reality Toolkit - 시선 지원 탐색](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) 샘플에서 찾을 수 있습니다.

_암시적 작업에_ 대한 다른 사용 사례는 다음과 같습니다.
- **스마트 알림:** 보고 있는 위치에 알림이 팝업되는 것이 불편해 보이는 경우는 언제인가요? 사용자가 주의를 기울이는 것을 고려하여 사용자가 현재 주의를 기울이는 위치에서 알림을 오프셋하여 이 환경을 더 잘 만들 수 있습니다. 이렇게 하면 사용자의 읽기가 완료되면 방해가 제한되고 자동으로 해제됩니다. 
- **들여쓰기 홀로그램:** 홀로그램은 잡히면 은소하게 반응합니다. 이 범위는 약간 후광이 있는 UI 요소, 느리게 피어링하는 꽃에서 사용자를 다시 보기 시작하고 꼬리를 흔드는 가상 개까지 다양합니다. 이러한 상호 작용은 애플리케이션에서 연결성 및 만족도에 대한 흥미로운 의미를 제공할 수 있습니다.

### <a name="attention-tracking"></a>주의 추적

사용자가 보는 위치 또는 내용에 대한 정보는 매우 강력한 도구일 수 있습니다. 디자인의 유용성을 평가하고 워크플로의 문제를 식별하여 더 효율적으로 만들 수 있습니다.
시선 추적 시각화 및 분석은 다양한 애플리케이션 영역에서 일반적인 사례입니다. HoloLens 2 통해 3D 홀로그램을 실제 컨텍스트에 배치하고 그에 따라 평가할 수 있으므로 이 이해를 위한 새로운 차원을 제공합니다. [Mixed Reality 도구 키트는](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) 시선 추적 데이터를 로깅 및 로드하고 시각화하는 방법에 대한 기본 예제를 제공합니다.
Microsoft는 사용자가 시선 추적 정보를 사용하는 방법에 대해 정보를 제공하고 투명한 환경을 갖추도록 하면서 혁신을 촉진하는 데 최선을 다하고 있습니다.  개발자 및 UX 팀과 협력하여 타사에 대한 지침을 제공하여 환경이 사용자를 중심으로 배치되도록 할 것입니다.  

이 영역의 다른 응용 분야로 다음이 포함될 수 있습니다. 
-   **원격 시선 응시 시각화:** 원격 시선 응시 시각화: 원격 협력자가 보고 있는 내용을 시각화하여 즉각적인 피드백을 제공하고 보다 정확한 정보 처리를 용이하게 할 수 있습니다.
-   **사용자 연구 연구:** 주의 추적을 사용 하면 사용자가 방해 하지 않고 자연 스러운 환경을 통해 사용자의 instinctual 상호 작용을 개선 하는 방법에 대 한 자세한 정보를 얻을 수 있습니다. 눈 추적은 연구에서 참가자가 직접 연락 하지 않는 정보를 제공할 수 있으며, 그렇지 않은 경우에는 연구원에 의해 쉽게 누락 될 수 있습니다. 
-   **교육 및 성능 모니터링:** 실행 흐름에서 병목 상태를 보다 효과적으로 식별 하 여 작업 실행을 연습 하 고 최적화 합니다. 눈 추적은 자연 스러운 실시간 및 목표 정보를 제공 하 여 작업 공간에서 학습, 생산성 및 안전을 향상 시킬 수 있습니다. 
-   **디자인 평가, 마케팅 및 소비자 연구:** 아이 추적을 사용 하면 상용 회사에서 실제 환경에서 마케팅 및 소비자 연구를 수행 하거나 제품 또는 공간 디자인을 개선 하기 위해 사용자의 주의가 필요한 사항을 분석할 수 있습니다. 

### <a name="other-use-cases"></a>기타 사용 사례

- **게임:** 슈퍼 능력을 원하는 가요? 여기서 그 기회를 얻을 수 있습니다. Holograms에서 바랄 levitate 수 있습니다. 눈에서 레이저 빔를 체험해 보세요. [RoboRaid에서 HoloLens 2에 대해](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)사용해 보세요.
적을 돌로 설정 하거나 고정 합니다. X-광선을 사용해서 건물을 투시하세요. 상상하는 만큼 이루어집니다.
사용자를 과도 하 게 확인 하는 것이 좋습니다. 자세한 내용은 눈에 잘 맞는 [입력 디자인 지침](eye-gaze-interaction.md)을 참조 하세요.

- **표현 아바타:** 눈 추적은 라이브 눈 추적 데이터를 사용 하 여 사용자가 보고 있는 항목을 나타내는 아바타의 눈에 애니메이션 효과를 주는 3D 아바타 더 많은 표현을 지원 합니다. 

- **텍스트 입력:** 눈에 잘 드는 텍스트 입력에 대 한 대체 방법으로 눈 추적을 사용할 수 있습니다. 특히 음성 또는 손을 사용 하기 불편 한 경우입니다. 

<br>

## <a name="using-eye-gaze-for-interaction"></a>상호 작용을 위해 눈동자 사용-응시

빠른 이동 대상 지정을 활용 하는 상호 작용을 빌드하는 것은 어려울 수 있습니다.
한편, 눈은 눈에 눈길을 사용 하는 방법에 주의 해야 합니다. 그렇지 않으면 사용자가 경험을 과도 하 게 경험해 볼 수 있기 때문입니다. 반면 사용자를 흥미 하는 진정한 마법 환경을 만들 수도 있습니다. 도움을 주려면 [상호 작용에 대한 시선 응시에](eye-gaze-interaction.md)대한 주요 이점, 과제 및 디자인 권장 사항의 개요를 확인하세요. 
 
## <a name="fallback-solutions-when-eye-tracking-isnt-available"></a>시선 추적을 사용할 수 없는 경우의 대체 솔루션

드문 경우로 시선 추적 데이터를 사용할 수 없습니다.
가장 일반적인 이유가 아래에 나열되어 있기 때문일 수 있습니다.
* 시스템에서 사용자 를 [보정하지](/hololens/hololens-calibration)못했습니다.
* 사용자가 [보정](/hololens/hololens-calibration)을 건너뛰습니다.   
* 사용자가 보정되었지만 시선 추적 데이터를 사용할 수 있는 권한을 앱에 부여하지 않기로 결정했습니다.    
* 사용자에게 시스템이 아직 지원하지 않는 고유한 안경 또는 일부 시선 상태가 있습니다. 
* HoloLens 바이저 또는 안경의 스미징, 눈 앞의 머리로 인한 집중적인 직접 스래핑 및 폐색과 같은 안정적인 시선 추적을 방해하는 외부 요소입니다.

개발자는 이러한 사용자에 대한 적절한 대체 지원이 있는지 확인해야 합니다. [DirectX의 시선 추적](../develop/native/gaze-in-directx.md#fallback-when-eye-tracking-isnt-available) 페이지에서 시선 추적 데이터를 사용할 수 있는지 여부를 감지하는 데 필요한 API에 대해 설명합니다. 

일부 사용자는 시선 추적 데이터에 대한 액세스 권한을 취소하기로 결정했지만 시선 추적 데이터에 대한 액세스를 제공하지 않는 개인 정보 보호에 대한 유추 사용자 환경의 장단점으로도 문제가 되지 않을 수 있습니다. 앱에서 시선 추적을 사용하고 이 부분이 환경의 중요한 부분인 경우 사용자에게 명확하게 전달하는 것이 좋습니다.   

애플리케이션의 모든 잠재력을 경험하기 위해 애플리케이션에 시선 추적이 중요한 이유(일부 향상된 기능도 나열)를 사용자에게 알리면 사용자가 포기할 내용을 더 잘 이해할 수 있습니다. 사용자가 위 검사에 따라 시선 추적이 작동하지 않는 이유를 식별하고 잠재적인 문제를 신속하게 해결하기 위한 몇 가지 제안을 제공하도록 도와 주세요. 

예를 들어 시스템에서 눈 추적을 지원함을 감지할 수 있는 경우 사용자가 보정 되 고 사용자에 게는 해당 사용 권한도 부여 된 경우에도 사용자가 보정 하거나 폐색 되는 눈동자와 같은 일부 다른 문제를 가리킬 수 있습니다. 

자주 발생 하지 않는 사용자의 경우는 거의 없습니다. 따라서 앱에서 눈 추적을 사용 하도록 설정 하는 경우 미리 알림을 해제 하거나 사용 하지 않도록 설정 하 여 respectful 합니다.

### <a name="fall-back-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>기본 입력 포인터로 눈동자-응시를 사용 하 여 앱을 대체 합니다.

앱에서 포인터 입력으로 눈에 holograms를 사용 하 여 장면에서의 작업을 빠르게 선택 하 고, 아이 추적 데이터를 사용할 수 없는 경우 헤드-응시로 대체 하 여 헤드-응시 커서를 표시 하기 시작 하는 것이 좋습니다. 스위치를 사용할지 여부를 결정 하는 데 시간 제한 (예: 500 – 1500 밀리초)을 사용 하는 것이 좋습니다. 이 작업을 수행 하면 빠른 눈 동작 또는 윙크 및 깜박이 때문에 시스템이 일시적으로 추적을 손실할 수 있는 경우에도 커서가 나타나지 않습니다. Unity 개발자 인 경우 head-응시에 대 한 자동 대체는 혼합 현실 도구 키트에서 이미 처리 되었습니다. DirectX 개발자 라면이 스위치를 직접 처리 해야 합니다.

### <a name="fall-back-for-other-eye-tracking-specific-applications"></a>다른 눈 추적 관련 응용 프로그램을 대체 합니다.

앱은 눈에 맞게 조정 된 고유한 방식으로 눈에 잘 맞는 방식을 사용할 수 있습니다. 예를 들어 아바타의 눈에 애니메이션을 적용 하거나 눈에 잘 맞는 주의가 필요한 경우 시각적 주의 사항에 대 한 정확한 정보를 열 지도. 이 경우에는 명확한 대체 (fallback)가 없습니다. 눈동자 추적을 사용할 수 없는 경우 이러한 기능을 사용 하지 않도록 설정 해야 할 수 있습니다.
기능이 제대로 작동 하지 않는다는 것을 모를 수 있는 사용자에 게이를 명확 하 게 전달 하는 것이 좋습니다.

<br>

이 페이지에서는 HoloLens 2에 대 한 눈에 보기 및 눈에 잘 맞는 입력의 역할을 이해 하기 시작 하는 데 도움이 되는 유용한 개요를 제공 합니다. 개발을 시작 하려면 [holograms와의 상호 작용을 위해 눈길](eye-gaze-interaction.md)을 [내](https://aka.ms/mrtk-eyes) 는 역할에 대 한 정보를 확인 [하세요.](../develop/native/gaze-in-directx.md)

## <a name="see-also"></a>참고 항목

* [조정](/hololens/hololens-calibration)
* [편안함](comfort.md)
* [시선 응시 기반 상호 작용](eye-gaze-interaction.md)
* [눈-DirectX에서 응시](../develop/native/gaze-in-directx.md)
* [눈동자-Unity에서 응시 (혼합 현실 도구 키트)](https://aka.ms/mrtk-eyes)
* [응시 및 커밋](gaze-and-commit.md)
* [음성 입력 ](../out-of-scope/voice-design.md)
