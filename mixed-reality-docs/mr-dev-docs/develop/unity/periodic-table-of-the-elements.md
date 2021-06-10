---
title: 원소의 주기율표
description: Elements 샘플 앱의 주기적 테이블과 함께 Object 컬렉션을 사용하여 다양한 표면 형식의 3D 공간에서 개체 배열을 레이아웃하는 방법을 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 샘플 앱, 컨트롤, MRTK, Mixed Reality Toolkit, Unity, 샘플 앱, 예제 앱, 오픈 소스, Microsoft Store, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: ed8c35fc6467322c25b92924b134f176fa4a9b47
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743417"
---
# <a name="periodic-table-of-the-elements"></a>원소의 주기율표

>[!NOTE]
>이 문서에서는 혼합 현실 앱 개발에 대한 학습 및 제안을 공유하는 [Mixed Reality Design Labs에서](https://github.com/Microsoft/MRDesignLabs_Unity)만든 예비 샘플을 설명합니다. 디자인 관련 문서와 코드는 새로운 검색을 통해 발전할 것입니다.

[주기적 요소 테이블은](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) Microsoft Mixed Reality Design Labs의 오픈 소스 샘플 앱입니다. **[개체 컬렉션](../../design/object-collection.md)** 을 사용하여 다양한 표면 형식의 3D 공간에서 개체 배열을 레이아웃하는 방법을 알아봅니다. 또한 HoloLens의 표준 입력에 응답하는 상호 작용 가능한 개체를 만드는 방법을 알아봅니다. 이 프로젝트의 구성 요소를 사용하여 사용자 고유의 혼합 현실 앱 환경을 만들 수 있습니다.

![Elements 앱의 기간 테이블](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a>데모 동영상 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

혼합 현실 캡처 사용하여 HoloLens 2 기록

## <a name="about-the-app"></a>앱 정보

요소의 주기적 테이블은 화학 요소와 각 속성을 3D 공간에서 시각화합니다. 응시 및 에어 탭과 같은 HoloLens의 기본 상호 작용을 통합합니다. 사용자는 애니메이션 3D 모델을 통해 요소에 대해 알아볼 수 있습니다. 원통과 신경망으로 구성된 요소의 전자 셸과 해당 원통을 시각적으로 이해할 수 있습니다.

## <a name="background"></a>배경

HoloLens를 처음 접한 후 혼합 현실에서 주기적인 테이블 앱을 실험하고 싶습니다. 각 요소에는 텍스트와 함께 표시되는 많은 데이터 요소가 있기 때문에 3D 공간에서 입력 체계 컴퍼지션을 탐색하는 데 중요한 주제가 될 것이라고 생각합니다. 사용자에게 요소의 전자 모델을 시각화할 수 있는 기회를 제공하는 것은 이 프로젝트의 또 다른 흥미로운 부분입니다.

## <a name="design"></a>디자인

주기적 테이블의 기본 보기에서는 각 요소의 전자 모델이 포함된 3차원 상자를 생각해 보았습니다. 각 상자의 표면은 반투명하게 되어 사용자가 요소의 볼륨에 대한 대략적인 아이디어를 얻을 수 있습니다. 응시 및 에어 탭을 통해 사용자는 각 요소의 자세한 보기를 열 수 있습니다. 테이블 뷰와 세부 정보 보기 간의 전환을 원활하고 자연스럽게 만들기 위해 실제로 열리는 상자의 물리적 상호 작용과 유사하게 만들었습니다.

![디자인 스케치](images/640px-sketch20170406.jpg)<br>
*스케치 디자인*

세부 정보 보기에서 각 요소의 정보를 3D 공간에서 렌더링된 텍스트로 시각화하려고 했습니다. 애니메이션된 3D 전자 모델은 가운데 영역에 표시되며 다른 각도에서 볼 수 있습니다.

![상호 작용](images/640px-periodictable-interaction.jpg)

![프로토 타입](images/640px-periodictable-prototypes.jpg)<br>
*상호 작용 프로토타입*

사용자는 테이블 아래쪽의 단추를 에어 탭하여 표면 유형을 변경할 수 있습니다. 평면, 실린더, 구 및 분산형 간에 전환할 수 있습니다.

## <a name="common-controls-and-patterns-used-in-this-app"></a>이 앱에서 사용되는 일반적인 컨트롤 및 패턴

### <a name="interactable-object-button"></a>상호 작용 가능한 개체(단추)

[상호 작용 가능한 개체는](../../design/interactable-object.md) 기본 HoloLens 입력에 응답할 수 있는 개체입니다. 모든 개체에 쉽게 적용할 수 있는 프리팹/스크립트로 제공됩니다. 예를 들어 장면에서 커피 한 잔을 상호 작용 가능하도록 만들고 응시, 에어 탭, 탐색 및 조작 제스처와 같은 입력에 응답할 수 있습니다. [자세한 정보](../../design/interactable-object.md)

![nteractable 개체](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>개체 컬렉션

[개체 컬렉션은](../../design/object-collection.md) 여러 개체를 다양한 모양으로 레이아웃하는 데 도움이 되는 개체입니다. 평면, 실린더, 구 및 분산형을 지원합니다. 반경, 행 수 및 간격과 같은 추가 속성을 구성할 수 있습니다. [자세한 정보](../../design/object-collection.md)

![개체 컬렉션](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>기술 세부 정보

[Mixed Reality Design Labs GitHub에서](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)Elements 앱의 주기적 테이블에 대한 스크립트와 프리팹을 찾을 수 있습니다.

## <a name="porting-story-for-hololens-2"></a>HoloLens 2 대한 포팅 스토리

elements 앱의 주기적 테이블이 HoloLens 2 직관적 상호 작용으로 업데이트된 방법에 대한 스토리를 읽어보십시오.

[원소의 주기율표 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>작성자 정보

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>UX 디자이너 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>참조

* [MRTK 예제 허브](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(HoloLens 2의 Microsoft Store에서 다운로드)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(HoloLens 2의 Microsoft Store에서 다운로드)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [원소의 주기율표 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [갤럭시 익스플로러 2.0](galaxy-explorer-update.md)