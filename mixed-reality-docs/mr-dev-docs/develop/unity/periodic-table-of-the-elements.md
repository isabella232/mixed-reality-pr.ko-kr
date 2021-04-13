---
title: 원소의 주기율표
description: Elements 샘플 앱의 주기 테이블에서 개체 컬렉션을 사용 하 여 다양 한 표면 유형으로 3D 공간에서 개체의 배열을 레이아웃 하는 방법에 대해 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 샘플 앱, 컨트롤, MRTK, Mixed Reality Toolkit, Unity, 샘플 앱, 예제 앱, 오픈 소스, Microsoft Store, HoloLens, 혼합 현실 헤드셋, windows Mixed Reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 36491d230f9d236db77f34b9540f19609c7619ef
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300178"
---
# <a name="periodic-table-of-the-elements"></a>원소의 주기율표

>[!NOTE]
>이 문서에서는 혼합 현실 앱 개발에 대 한 학습 정보 및 제안을 공유 하는 위치를 [혼합 현실 디자인 랩에서](https://github.com/Microsoft/MRDesignLabs_Unity)만든 예비 샘플에 대해 설명 합니다. 디자인 관련 문서와 코드는 새로운 검색을 수행할 때 개선 됩니다.

[요소의 정기 테이블](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) 은 Microsoft의 혼합 현실 디자인 랩에서 오픈 소스 샘플 앱입니다. **[개체 컬렉션](../../design/object-collection.md)** 을 사용 하 여 다양 한 표면 형식으로 3d 공간에서 개체의 배열을 레이아웃 하는 방법에 대해 알아봅니다. 또한 HoloLens에서 표준 입력에 응답 하는 interactable 개체를 만드는 방법에 대해 알아봅니다. 이 프로젝트의 구성 요소를 사용 하 여 혼합 현실 앱 환경을 만들 수 있습니다.

![요소 앱의 기간 테이블](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a>데모 동영상 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

혼합 현실 캡처를 사용 하 여 HoloLens 2로 기록 됨

## <a name="about-the-app"></a>앱 정보

요소의 주기적 테이블은 시각화 요소와 각 속성을 3D 공간에 만듭니다. 이 도구는 응시 및 air 탭과 같은 HoloLens의 기본 상호 작용을 통합 합니다. 사용자는 애니메이션 3D 모델을 사용 하 여 요소에 대해 알아볼 수 있습니다. 이러한 사용자는 protons 및 neutrons로 구성 된 요소의 전자 핵심 이기를 시각적으로 이해할 수 있습니다.

## <a name="background"></a>배경

HoloLens를 처음 경험 한 후에는 혼합 현실에서 정기적으로 테이블 앱을 시험 하고자 했습니다. 각 요소에는 텍스트와 함께 표시 되는 데이터 요소가 많기 때문에 3D 공간에서 입력 컴퍼지션을 탐색 하는 것이 좋습니다. 사용자에 게 요소의 전자 모델을 시각화할 수 있는 기회를이 프로젝트의 또 다른 흥미로운 부분으로 제공 합니다.

## <a name="design"></a>디자인

정기적 테이블의 기본 보기에서는 각 요소의 전자 모델을 포함 하는 3 차원 상자를 사용할 수 있습니다. 사용자가 요소의 볼륨에 대 한 대략적인 아이디어를 얻을 수 있도록 각 상자의 표면이 반투명 하 게 표시 됩니다. 사용자는 응시 및 air 탭을 사용 하 여 각 요소의 자세히 보기를 열 수 있습니다. 테이블 뷰와 자세히 보기를 자연스럽 고 자연스럽 게 전환 하기 위해 실시간으로 열리는 상자의 물리적 상호 작용과 유사 합니다.

![스케치 디자인](images/640px-sketch20170406.jpg)<br>
*디자인 스케치*

자세히 보기에서는 원활 렌더링 된 텍스트를 사용 하 여 각 요소의 정보를 3D 공간에 시각화 하고자 했습니다. 애니메이션 3D 전자 모델은 가운데 영역에 표시 되며 다른 각도에서 볼 수 있습니다.

![상호 작용](images/640px-periodictable-interaction.jpg)

![모델링할](images/640px-periodictable-prototypes.jpg)<br>
*상호 작용 프로토타입*

사용자는 테이블 아래쪽의 단추를 눌러 표면 유형을 변경할 수 있습니다. 평면, 원통, 구 및 산 사이를 전환할 수 있습니다.

## <a name="common-controls-and-patterns-used-in-this-app"></a>이 응용 프로그램에서 사용 되는 공용 컨트롤 및 패턴

### <a name="interactable-object-button"></a>Interactable 개체 (button)

[Interactable 개체](../../design/interactable-object.md) 는 기본 HoloLens 입력에 응답할 수 있는 개체입니다. Prefab/스크립트로 제공 되며 개체에 쉽게 적용할 수 있습니다. 예를 들어 장면 interactable에서 커피 컵을 만들고 응시, 공중 탭, 탐색 및 조작 제스처와 같은 입력에 응답할 수 있습니다. [자세한 정보](../../design/interactable-object.md)

![nteractable 개체](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>개체 컬렉션

[개체 컬렉션](../../design/object-collection.md) 은 다양 한 모양의 여러 개체를 배치 하는 데 도움이 되는 개체입니다. 평면, 원통, 구 및 산을 지원 합니다. Radius, 행 수 및 간격과 같은 추가 속성을 구성할 수 있습니다. [자세한 정보](../../design/object-collection.md)

![개체 컬렉션](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>기술 세부 정보

[혼합 현실 디자인 실험 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)에서 Elements 앱의 주기 테이블에 대 한 스크립트 및 prefabs를 찾을 수 있습니다.

## <a name="porting-story-for-hololens-2"></a>HoloLens의 포팅 스토리 2

요소 앱의 주기 테이블이 HoloLens 2의 instinctual 상호 작용으로 업데이트 된 방법에 대 한 스토리를 읽어 보세요.

[원소의 주기율표 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>작성자 정보

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>UX 디자이너 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>참조

* [MRTK 예제 허브](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(HoloLens 2의 Microsoft Store에서 다운로드)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(HoloLens 2의 Microsoft Store에서 다운로드)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [원소의 주기율표 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [갤럭시 익스플로러 2.0](galaxy-explorer-update.md)