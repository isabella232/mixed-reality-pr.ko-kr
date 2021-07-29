---
title: Kippy의 이스케이프 만들기
description: unreal Engine에서 HoloLens 2에 대 한 Kippy의 이스케이프 혼합 현실 응용 프로그램을 만드는 과정을 살펴볼 때에도 문의 하십시오.
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: unreal, unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 장치에 배포, PC, 설명서, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
appliesto:
- HoloLens 2
ms.openlocfilehash: 353df2f2f5bc9a1d70fc354fd3014f10c0ba95d9
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757118"
---
# <a name="the-making-of-kippys-escape"></a>Kippy의 이스케이프 만들기
![Kippy의 이스케이프 주인공 이미지](images/KippysEscape_1920.jpg)

Kippy가 아일랜드에서 남겨진 상태를 찾도록 합니다. 문제를 해결 하는 데 도움이 되는 문제를 해결 하는 데 도움이 될 것입니다. HoloLens 2에 스트랩을 Microsoft Store에서 [앱을 다운로드](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) 하거나 GitHub에서 [리포지토리](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) 를 복제 하 고 Kippy home safe를 가져옵니다.  

> [!IMPORTANT]
> GitHub 리포지토리에서 Kippy의 이스케이프를 작성 하는 경우 **unreal Engine 4.25** 이상을 사용 하 고 있는지 확인 합니다.

Kippy의 이스케이프는 unreal Engine 4로 빌드된 오픈 소스 [HoloLens 2](/hololens/hololens2-hardware) 샘플 앱 이며, [unreal 용 혼합 현실 UX 도구](https://github.com/microsoft/MixedReality-UXTools-Unreal)입니다. 이 게시물에서는 환경을 구현 하 고 최적화 하기 위한 첫 번째 원칙 및 시각적 디자인의 프로세스를 안내 합니다. MRTK UX 도구를 사용 하 여 혼합 현실 응용 프로그램을 개발 하는 방법에 대 한 자세한 내용은 [Unreal development 개요](unreal-development-overview.md)를 확인할 수 있습니다.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>HoloLens 2의 Microsoft Store에서 앱 다운로드
HoloLens 2 장치가 있는 경우 장치에서 앱을 직접 다운로드 하 여 설치할 수 있습니다.

<a href='//www.microsoft.com/store/apps/9nbd7gl86vkd?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="first-principles"></a>첫 번째 원칙 

Kippy의 이스케이프 만들기에서 목표는 [unreal Engine의 HoloLens 2 지원](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html), HoloLens 2의 기능 및 혼합 현실 Toolkit를 강조 하는 환경을 만드는 것 이었습니다. 개발자 들이 영감를 사용 하 여 만들 수 있는 작업을 상상 하는 개발자를 위해 노력 하 HoloLens 2 고 있습니다.  

환경에 대 한 세 가지 안내 원칙 (재미 있고 대화형이 필요 하 고 진입에 대 한 장벽을 낮음)을 제공 했습니다. 처음에는 혼합 된 현실 사용자에 게는 자습서를 사용 하지 않아도 되도록 충분히 직관적으로 경험을 원했습니다.  

## <a name="designing-the-game"></a>게임 디자인 

HoloLens 2는 현재 게임에서 다른 곳에서 찾을 수 없는 디자인 기능에 액세스할 수 있습니다. 사용자를 사용 하 여 개체를 직접 푸시되 나 조작 하거나 시각 추적을 대상으로 지정할 수 있습니다. 이러한 주요 기능은 Kippy의 이스케이프에서 작성 한 흥미로운 몇 분 뒤에 있습니다.  

게임 디자인을 위한 지침으로 고유한 HoloLens 2 기능을 사용 하 여 몇 가지 작은 환경 시나리오의 범위를 지정 했습니다. 다른 플레이어 높이에 맞게 조정 될 수 있고 몇 가지 오락 아이디어 아이디어를 제공 했기 때문에 제도를 이해 했습니다. 좋아하는에 대 한 배치의 테마는 각 아일랜드에서 제공 하는 이상한 에너지를 방해 하는 활용에 대 한 기계를 구축 했습니다. 각각은 시각적 효과를 만드는 데 도움이 되는 고유한 모양과 느낌을 제공 합니다. 모델링 및 질감 사이에 적절 한 균형을 유지 하면 렌더링 성능이 저하 될 수 있으므로 스타일을 염두에 두고 디자인 되었습니다. 

![초기 게임 디자인 ](images/kippys-escape/kippys-escape-img-01.png)
 *은 환경에 대 한 초기 스케치를 스케치 합니다* .

![두 번째 섬에 ](images/kippys-escape/kippys-escape-img-02.png)
 *대 한* 두 번째 섬 렌더링 렌더링

짧은 프로덕션 일정 내에서 유지 하기 위해 부동 문자가 엄격한 애니메이션 주기 없이 의도 및 emotion를 캡처할 수 있도록 합의 했습니다. Kippy. 눈에 최소형 vocal 음향 효과를 통해 몇 가지 다른 식을 표현 하 고 플레이어를 통해 플레이어를 안내할 수 있습니다. 

![눈동자를 통해 다양 한 식을 보여 주는 Kippy](images/kippys-escape/kippys-escape-img-03.gif)

*눈동자를 통해 다양 한 식을 보여 주는 Kippy*

![사용자가 퍼즐을 해결 하는 데 너무 오래 걸리는 경우 Kippy는 사용자에 게 힌트를 제공 합니다.](images/kippys-escape/kippys-escape-img-04.gif)

*사용자가 퍼즐을 해결 하는 데 너무 오래 걸리는 경우 Kippy는 사용자에 게 힌트를 제공 합니다.*

문자 및 환경 설계 외에도 게임을 재미 있게 하기 위한 노력을 율 했습니다. 아이 추적을 통해 게임의 주요 부분을 강조 표시 하는 재질 및 음향 특성을 실행할 수 있었습니다. 공간 오디오는 플레이어 환경의 집에서 수준을 느낌을 주는 데 도움이 됩니다. 개체를 잡고 단추를 누르고 슬라이더를 조작 하는 것은 혁신적인 플레이어 계약을 구동 합니다. 이러한 연결 지점이 자연스럽 게 확인 하는 것이 중요 했습니다. 

![사용자가 손 모양에 도달할 때 연결 케이블의 끝입니다.](images/kippys-escape/kippys-escape-img-05.gif)

*사용자가 손 모양에 도달할 때 연결 케이블의 끝입니다.*

## <a name="building-the-game-mechanics"></a>게임 메커니즘 구축 

Kippy의 이스케이프는 혼합 현실 UX 도구 구성 요소에 크게 의존 하 여 게임을 대화형으로 진행 하 고, 범위 컨트롤, 조작자, 슬라이더 및 단추를 만듭니다.   

[손 상호 작용 행위자](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) 는 holograms의 직접 조작과 직접 조작을 모두 가능 하 게 합니다. Kippy의 이스케이프 시작 부분에서 사용자에 게 게임의 위치를 설정할 수 있는 기회가 제공 됩니다. 빔 사용자의 palm에서 확장 하면 아래에 나와 있는 것 처럼 훨씬 멀리 떨어져 있는 holograms를 쉽게 조작할 수 있습니다.  

![직접 상호 작용 행위자 gif](images/kippys-escape/kippys-escape-img-06.gif)

UX 도구의 [범위 컨트롤](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/BoundsControl.html) 구성 요소를 사용 하 여 자리 표시자 장면 자체를 끌어서 회전할 수 있습니다.  

두 번째 아일랜드에서 사용자는 보석을 선택 하 여 일치 하는 슬롯에 넣어야 합니다. 보석에는 사용자가 선택 하 여 배치할 수 있도록 하는 [조작자](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html) 가 연결 되어 있습니다. 

![조작자 예제 gif](images/kippys-escape/kippys-escape-img-07.gif)

[Pressable 단추](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html) 는 세 번째 섬에서 사용할 폭탄를 가져오는 키입니다.  

![Pressable button 예제 gif](images/kippys-escape/kippys-escape-img-08.gif)

네 번째 섬에 [슬라이더](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PinchSlider.html) 구성 요소가 표시 되 고 발생 시킬 최종 브리지가 트리거됩니다.  

![Slider 구성 요소 예제 gif](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>HoloLens 2 최적화 

모바일 장치에서 실행 되도록 제작 된 환경을 사용 하 여 성능에 대 한 눈을 유지 하는 것은 매우 중요 합니다. Unreal 4.25에는 모바일 다중 뷰 지원에 대 한 주요 업데이트가 포함 되어 있습니다 .이로 인해 렌더링 오버 헤드가 크게 줄어들고 프레임 비율이 높아집니다. 최적화할 때 unreal을 사용 하 여 HoloLens 2 개발에 대 한 다른 [권장 성능 설정을](performance-recommendations-for-unreal.md) 확인 하는 것이 좋습니다.  

물리 개체는 여전히 성능에 대해 비용이 많이 들기 때문에 몇 가지 해결 방법을 사용 했습니다. 예를 들어 세 번째 "브리지"를 사용 하려면 stairway를 차단 하는 일부 이물질을 죠 합니다. 충격을 힘 개체로 강제 적용 하는 대신, 폭탄 detonation는 폭발을 트리거하고 폭발 파티클 효과에 대 한 정적 스톤을 전환 합니다. 

![HoloLens 2 gif에 대해 최적화 된 예제](images/kippys-escape/kippys-escape-img-10.gif) 

또한 다음을 수행 하 여 400 ~ 260의 그리기 호출을 자릅니다. 
* 메시 복잡성 감소
* 메시 조합
* 초기 동적 조명 요소 중 일부를 제거 하는 중

더 많은 작업을 수행할 수 있지만 성능 및 시각적 품질 간에는 잘 조화를 느낄 것입니다.  

## <a name="try-it-out"></a>기능 직접 사용해 보기 

HoloLens 2를 부팅 하 고 Microsoft Store에서 앱을 [다운로드](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) 하거나 GitHub에서 [리포지토리](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) 를 복제 하 고 앱을 직접 빌드합니다.  

## <a name="about-the-team"></a>팀 정보

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>잭 Caron</b><br><i>리드 게임 디자이너</i><br>현재는 HoloLens 2 프로젝트 및 AltspaceVR를 포함 하 여 Microsoft의 혼합 현실 환경에서 작동 하며, 이전에는 HoloLens 플랫폼 팀의 디자이너 였습니다.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>여름 Wu</b><br><i>Producer</i><br>여름은 혼합 현실 개발자 플랫폼에서 작동 하 고 팀의 실제 엔진 관련 활동을 수용 합니다.</td>
</tr>
</table>

Kippy의 탈출을 [Framestore](https://www.framestore.com/) 수 있도록 microsoft 친구에 게 감사 드립니다. 문자 개발, 자산 디자인, 게임 프로그래밍에 이르기까지,이 프로젝트에 대 한 공동 작업은 pivotal 되었습니다.