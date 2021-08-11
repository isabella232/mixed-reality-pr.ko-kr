---
title: Kippy의 이스케이프 만들기
description: Unreal Engine에서 HoloLens 2 Kippy의 Escape mixed reality 애플리케이션을 만드는 것을 살펴보면서 함께 진행합니다.
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 디바이스에 배포, PC, 설명서, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
appliesto:
- HoloLens 2
ms.openlocfilehash: 96799de948cf9e1cbca89b7e781f3f830fbc005810680d1164d04acb757b1a09
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208226"
---
# <a name="the-making-of-kippys-escape"></a>Kippy의 이스케이프 만들기
![Kippy의 이스케이프 영웅 이미지](images/KippysEscape_1920.jpg)

로봇이 절전 모드를 깨우면 자신이 아일랜드에 있는 것을 발견할 수 있습니다. 로켓 우주선으로 돌아가는 경로를 찾는 데 도움이 하려면 문제 해결모를 쌓아야 합니다. HoloLens 2 및 Microsoft Store [앱을 다운로드하거나](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) GitHub [리포지토리를](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) 복제하고 Kippy 홈 안전을 얻습니다.  

> [!IMPORTANT]
> GitHub 리포지토리에서 Kippy의 이스케이프를 빌드하는 경우 **Unreal Engine 4.25 이상** 을 사용하고 있는지 확인합니다.

Kippy의 이스케이프는 Unreal Engine 4 및 Mixed Reality [UX Tools for Unreal로](https://github.com/microsoft/MixedReality-UXTools-Unreal)빌드된 오픈 [소스](/hololens/hololens2-hardware) HoloLens 2 샘플 앱입니다. 이 게시물에서는 첫 번째 원칙 및 시각적 디자인부터 환경 구현 및 최적화에 이르는 프로세스를 안내합니다. MRTK UX Tools를 사용하여 Mixed Reality 애플리케이션을 개발하는 자세한 내용은 [Unreal 개발 개요](unreal-development-overview.md)에서 확인할 수 있습니다.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>HoloLens 2 Microsoft Store 앱을 다운로드합니다.
HoloLens 2 디바이스가 있는 경우 앱을 직접 다운로드하여 디바이스에 설치할 수 있습니다.

<a href='//www.microsoft.com/store/apps/9nbd7gl86vkd?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="first-principles"></a>첫 번째 원칙 

Kippy의 이스케이프를 만들도록 설정했을 때 목표는 [Unreal Engine의 HoloLens 2 지원, HoloLens 2](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html)기능 및 Mixed Reality Toolkit 강조하는 환경을 만드는 것이었습니다. 개발자가 Unreal 및 HoloLens 2 사용하여 만들 수 있는 것을 상상해 보도록 영감을 주고자 했습니다.  

경험에 대한 세 가지 지침 원칙, 즉 재미있고 대화형이어야 하며 진입 장벽이 낮아야 했습니다. 처음 혼합 현실 사용자에게도 자습서를 진행할 필요가 없도록 환경을 직관적으로 만들고자 했습니다.  

## <a name="designing-the-game"></a>게임 디자인 

이 HoloLens 2 현재 게임에서 찾은 디자인 기능에 액세스할 수 있습니다. 개체는 손을 사용하여 직접 푸시하거나 조작하거나 시선 추적을 통해 대상으로 지정할 수 있습니다. 이러한 주요 기능은 Kippy의 이스케이프에서 빌드한 몇 가지 재미있는 순간 뒤에 있습니다.  

고유한 HoloLens 2 기능을 게임 디자인에 대한 지침으로 사용하여 몇 가지 작은 환경 시나리오의 범위를 지정했습니다. 아일랜드는 서로 다른 플레이어 높이에 맞게 조정될 수 있고 몇 가지 멋진 브리지 아이디어를 제공할 수 있기 때문에 의미가 있습니다. 우리는 누군가가 각 아일랜드에서 제공하는 이상한 에너지를 활용하여 익힌 기계체를 빌드했다는 아이디어로 sci-fi 기술을 충족하는 문화권의 테마를 구축했습니다. 각 아일랜드에는 시각적 관심을 만드는 데 도움이 되는 세부 정보인 고유한 모양과 느낌을 제공했습니다. 모델링과 텍스처링 간의 균형은 렌더링 성능을 위해 그리기 호출을 낮게 유지하므로 스타일이 있는 모양은 이를 염두에 두고 설계되었습니다. 

![초기 게임 디자인은 ](images/kippys-escape/kippys-escape-img-01.png)
 *환경의 모양에 대한 몇 가지 초기 스케치를 스케치합니다.*

![두 번째 아일랜드 렌더링의 ](images/kippys-escape/kippys-escape-img-02.png)
 *두 번째 아일랜드 렌더링*

짧은 프로덕션 일정 내에 유지하기 위해 부동 문자가 엄격한 애니메이션 주기 없이 의도와 감정을 캡처할 수 있다는 데 동의했습니다. Kippy가 출생했습니다! 눈과 최소한의 코로나 소리 효과를 통해 몇 가지 다른 식을 나타내며, 경험 전체에서 플레이어를 안내하는 데 도움이 될 수 있습니다. 

![눈에서 다른 식을 보여주는 Kippy](images/kippys-escape/kippys-escape-img-03.gif)

*눈에서 다른 식을 보여주는 Kippy*

![사용자가 장난감을 해결하는 데 시간이 너무 오래 걸리는 경우 Kippy는 사용자에게 힌트를 제공합니다.](images/kippys-escape/kippys-escape-img-04.gif)

*사용자가 장난감을 해결하는 데 시간이 너무 오래 걸리는 경우 Kippy는 사용자에게 힌트를 제공합니다.*

문자 및 환경 디자인 외에도 게임을 재미있게 만들기 위해 노력했습니다. 시선 추적을 통해 게임의 주요 부분을 강조 표시한 재질 및 소리 특성을 발생시키는 것이 가능했습니다. 공간 오디오는 플레이어의 주변 환경에서 수준의 느낌을 줍니다. 개체를 잡고, 단추를 누르고, 슬라이더를 조작할 수 있는 것은 혁신적인 플레이어 참여를 유도합니다. 이러한 연결 지점이 자연스럽게 보이게 하는 것이 중요했습니다. 

![브리지 케이블의 끝은 사용자의 손을 다가갈 때 후광이 납니다.](images/kippys-escape/kippys-escape-img-05.gif)

*브리지 케이블의 끝은 사용자의 손을 다가갈 때 후광이 납니다.*

## <a name="building-the-game-mechanics"></a>게임 메커니즘 빌드 

Kippy의 이스케이프는 Mixed Reality UX Tools 구성 요소를 많이 사용하여 게임 대화형(즉, 손 조작 행위자, 경계 컨트롤, 조작자, 슬라이더 및 단추)을 대화형으로 만듭니다.   

[손 조작 행위자를](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) 사용하면 홀로그램을 직접 조작하고 원거리로 조작할 수 있습니다. Kippy의 이스케이프가 시작되면 사용자에게 게임 위치를 설정할 수 있는 기회가 제공됩니다. 사용자의 손손에서 확장된 손 스텐을 통해 아래 gif에 보이는 것처럼 멀리 떨어져 있는 큰 홀로그램을 쉽게 조작할 수 있습니다.  

![손 조작 행위자 gif](images/kippys-escape/kippys-escape-img-06.gif)

자리 표시자 장면 자체는 UX Tools의 경계 컨트롤 구성 요소를 사용하여 끌어서 회전할 수 [있습니다.](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/BoundsControl.html)  

두 번째 아일랜드에서 사용자는 gem을 선택하고 일치하는 슬롯에 배치해야 합니다. gem에는 사용자가 조작자를 선택하고 배치할 수 있는 [조작자가](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html) 연결되어 있습니다. 

![조작자 예제 gif](images/kippys-escape/kippys-escape-img-07.gif)

[누를 수 있는 단추는](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html) 세 번째 아일랜드에서 사용할 수 있도록 하기 위한 키입니다.  

![누를 수 있는 단추 예제 gif](images/kippys-escape/kippys-escape-img-08.gif)

[슬라이더](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PinchSlider.html) 구성 요소가 네 번째 아일랜드에 표시되어 마지막 브리지가 발생하도록 트리거합니다.  

![슬라이더 구성 요소 예제 gif](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>HoloLens 2 최적화 

모바일 디바이스에서 실행하도록 빌드된 모든 환경을 사용하여 성능을 주시하는 것이 중요합니다. Unreal 4.25에는 모바일 다중 보기를 지원하는 주요 업데이트가 포함되어 렌더링 오버헤드를 크게 줄이고 프레임 속도를 높입니다. 최적화할 때 Unreal을 HoloLens 2 개발에 [권장되는](performance-recommendations-for-unreal.md) 다른 성능 설정을 확인하는 것이 좋습니다.  

물리학 개체는 성능에 여전히 비용이 많이 들기 때문에 몇 가지 훌륭한 해결 방법이 사용되었습니다. 예를 들어 세 번째 "브리지"에는 계단이 차단된 일부 차단선이 필요합니다. 물리학 개체로서 강제에 영향을 미치는 대신, 검사선은 스왑을 트리거하여 쇠사진 효과에 대한 정적 스태핑을 전환합니다. 

![HoloLens 2 gif에 최적화된 예제](images/kippys-escape/kippys-escape-img-10.gif) 

또한 다음을 통해 그리기 호출을 400개 이상에서 260개까지 줄였습니다. 
* 메시 복잡성 감소
* 메시 결합
* 초기 동적 조명 요소 중 일부 제거

수행할 수 있는 작업이 더 많을 수 있지만 성능과 시각적 품질 간에 균형이 양호하다고 생각했습니다.  

## <a name="try-it-out"></a>기능 직접 사용해 보기 

HoloLens 2 부팅하고 Microsoft Store 앱을 [다운로드하거나](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) GitHub [리포지토리를](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) 복제하고 직접 앱을 빌드합니다.  

## <a name="about-the-team"></a>팀 정보

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>잠재 고객 게임 디자이너</i><br>Jack은 현재 HoloLens 2 프로젝트 및 AltspaceVR을 포함하여 Microsoft용 Mixed Reality 환경으로 작업하며, 이전에는 HoloLens 플랫폼 팀의 디자이너였습니다.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>하계 Wu</b><br><i>Producer</i><br>하계는 혼합 현실 개발자 플랫폼에서 작업하며 팀의 Unreal Engine 관련 활동을 앞장서고 있습니다.</td>
</tr>
</table>

Kippy의 이스케이프를 실현하는 데 도움을 주신 [Framestore의](https://www.framestore.com/) 친구에게 특별히 감사드립니다. 문자 개발, 자산 디자인, 게임 프로그래밍에 이르기까지 이 프로젝트에 대한 협업은 매우 중요했습니다.