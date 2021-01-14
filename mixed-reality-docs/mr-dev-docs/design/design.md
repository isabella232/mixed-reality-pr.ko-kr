---
title: 디자인 및 프로토타입 생성 시작
description: 만들 준비가 되면, 디자인 및 프로토타입 생성을 시작하는 데 필요한 기본 개념을 알아봅니다.
author: grbury
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 검색, 배포, 인덱스, 방문 페이지, 디자인, 개발, 자습서, 샘플 앱, 기본 사항, 사례 연구, 리소스, HoloLens 방법, 오픈 소스 프로젝트, 핵심 개념, 상호 작용, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f4a4ea50c45263f18079da76dd8dfd5f31e2af44
ms.sourcegitcommit: 44d0f2873c75003caf9d8d244ceaeb3faa89df63
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98110451"
---
# <a name="start-designing-and-prototyping"></a>디자인 및 프로토타입 생성 시작

![혼합 현실 디자인 요약](images/design-hero-image.png)

Mixed Reality 애플리케이션은 오늘날 전 세계의 다른 애플리케이션과 다르며 이를 설계하는 것은 어려운 작업입니다. 만들고 있는 현실 세계와 가상 세계의 새로운 조합뿐만 아니라 이 조합이 제공하는 새로운 사용자 환경도 고려해야 합니다. Mixed Reality는 큰 장소이므로 디자인 스펙트럼에 따라 중요한 지점을 선택하여 일련의 검사점으로 아래에 배치했습니다. 이러한 검사점은 순차적이어야 하지만, 이미 참여한 경우 다음 섹션 중 하나로 자유롭게 이동하세요. 

시작하려면 디자인 개요 비디오를 시청하세요.

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4LhlW]

## <a name="design-checkpoints"></a>디자인 검사점

다음 검사점을 사용하여 애플리케이션 아이디어와 개념을 혼합 현실 세계로 가져옵니다.

### <a name="1-getting-started"></a>1. 시작

모든 과정과 마찬가지로 Mixed Reality 애플리케이션을 설계하는 과정도 기본 사항에서 시작합니다. [Mixed Reality란?](../discover/mixed-reality.md) 및 [홀로그램이란?](../discover/hologram.md) 문서를 숙지하여 몰입형 디자인을 준비하는 것이 좋습니다. 자세히 살펴보았으면 Mixed Reality 디자인 과정을 시작할 준비가 된 것입니다.

![Holograms 앱 디자인에서 gif 시작하기](images/HandTracking2.gif)

|  검사점  |  결과  |
| --- | --- |
| [디자인 프로세스 확장](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | Microsoft 내부 및 외부의 디자이너로부터 수집한 Mixed Reality의 디자인 프로세스를 직접 살펴보세요. |
| [Mixed Reality 앱 유형](types-of-mixed-reality-apps.md) | 앱 환경이 Mixed Reality 스펙트럼에서 라이브 상태가 되는 위치를 결정합니다. |
| [Holograms 앱 디자인](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | 놀라운 HoloLens 앱을 만들기 위한 동작, 팁 및 권장 사항을 경험하면서 혼합 현실 UX 디자인의 기본 사항에 대해 알아봅니다(HoloLens 2의 Microsoft Store에서 다운로드 가능). |
| [MRTK 예제 허브](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4) | 혼합 현실을 위한 공통 공간 상호 작용 및 UX 구성 요소를 경험할 수 있습니다(HoloLens 2의 Microsoft Store에서 다운로드할 수 있음). |

### <a name="2-core-concepts"></a>2. 핵심 개념

VR 또는 AR용으로 개발하는지에 관계없이 유동적인 몰입형 환경을 설계하는 데 적용되는 몇 가지 핵심 개념이 있습니다. 사용자의 관점을 이해하고, 개체를 배치하며, 모든 사람이 편안하고 안전한지 확인하는 것이 이 과정의 가장 중요한 단계입니다. 이 섹션이 완료되면 상호 작용 디자인을 통해 수행할 수 있는 견고한 토대가 갖추어집니다.

![핵심 개념 예제 이미지](images/fragments-750px.jpg)

|  개념  |  결과  |
| --- | --- |
| [홀로그램 프레임](holographic-frame.md) | 헤드셋을 착용하면 현실 세계에 겹쳐진 콘텐츠가 사용자에게 표시되는 방법을 이해합니다. |
| [좌표계](coordinate-systems.md) | 물리적 공간인지, 아니면 직접 만든 가상 영역인지에 관계없이 의미 있는 위치에 홀로그램을 정확하게 배치하는 방법을 알아봅니다. |
| [공간 매핑](spatial-mapping.md) | 개체를 사용자의 세계에 고정하고, 현실 세계의 물리적 표면을 활용합니다. |
| [편안함 고려사항](comfort.md) | 자연 세계를 모방하는 방식으로 몰입형 콘텐츠를 만들고 제공하여 사용자의 편의와 안전을 보장합니다. |

### <a name="3-interaction-design"></a>3. 상호 작용 디자인

가상 환경의 아름다움과 몰입감에 관계없이 상호 작용이 없으면 쓸모가 없습니다. 이 섹션에서는 기본적인 상호 작용 모델, 손 및 모션 컨트롤러, 음성 입력 및 사용자로부터 시선 추적 데이터를 수집하는 방법을 안내합니다. 이 섹션이 완료되면 디자인 과정의 마지막 주요 항목인 사용자 환경을 다룰 준비가 됩니다.

![상호 작용 디자인 요소](images/UX_Hero_Manipulation.jpg)

|  개념  |  결과  |
| --- | --- |
| [상호 작용 모델](interaction-fundamentals.md) | 손, 눈, 음성 입력을 통해 사용자에게 직관적인 상호 작용을 제공합니다. |
| [실습 및 모션 컨트롤러](hands-and-tools.md) | 사용자의 손으로 가까운 거리에서 또는 정확한 상호 작용으로 먼 거리에서 홀로그램과 상호 작용하는 방법을 알아봅니다. |
| [음성 입력 ](voice-input.md) | 몰입형 앱에서 음성 명령을 입력으로 사용하여 주변의 홀로그램과 환경을 제어합니다.  |
| [시선 추적](eye-tracking.md) | 사용자가 보고 있는 항목에 대한 정보를 사용하여 홀로그램 환경에서 새로운 수준의 컨텍스트 및 인간 이해를 추가합니다. |

### <a name="4-user-experience-elements"></a>4. 사용자 환경 요소

이제 기본 상호 작용을 숙지했으므로 사용자 환경 요소의 세부 요소와 고유한 Mixed Reality 환경에 맞게 이를 조정하는 방법을 중점적으로 살펴볼 수 있습니다. 사용자에게 직관적인 환경을 만들면서 일반적인 동작, 자산 디자인, 개체 크기 조정 및 입력 체계에 대해 설명합니다. 이 섹션은 공식적인 Mixed Reality 디자인 과정의 끝을 나타내지만, [다음 작업](#whats-next) 섹션에는 계속 진행할 수 있는 더 많은 리소스가 있습니다.

![UX 요소](images/UX_Hero_BoundingBox.jpg)

|  개념  |  결과  |
| --- | --- |
| [공용 컨트롤 및 동작](app-patterns-landingpage.md) | 자주 사용되는 공간 상호 작용 및 UI 구성 요소에 대해 알아봅니다. |
| [색, 광원 및 재질](color-light-and-materials.md) | 색, 조명 및 재질을 고려한 Mixed Reality에 대한 품질 자산을 설계합니다. |
| [개체 크기 조정](scale.md) | 최대한 많은 현실 세계 시각적 신호를 통합하여 사용자가 개체의 위치, 크기 및 구성 요소를 이해하는 데 도움을 줍니다. |
| [입력 체계](typography.md) | 3차원 공간에서 명확하고 읽기 쉬운 텍스트를 사용하여 사용자에게 필요한 중요한 정보를 제공합니다. |

## <a name="whats-next"></a>다음 작업

디자이너 작업은 수행되지 않습니다(특히 새 패러다임에서 몰입형 환경을 만드는 법을 학습하는 경우). 다음 섹션에서는 이미 완료한 초보자 수준 디자인 자료와 Mixed Reality 개발 분야로 모두 안내합니다. 이러한 항목과 리소스는 순차적이지 않으므로 자유롭게 살펴보세요.

### <a name="choose-a-prototyping-option"></a>프로토타입 생성 옵션 선택  

:::row:::   
    :::column:::    
       [![Unity 배우기](images/logo-unity.png)](https://learn.unity.com/)<br>
        **[Unity 배우기](https://learn.unity.com/)**<br>
        Unity를 사용하여 대화형 환경을 만드는 방법을 알아봅니다. 처음부터 끝까지 수행하여 알아봅니다.
    :::column-end:::    
    :::column:::    
        [![Mixed Reality Toolkit(MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[Mixed Reality Toolkit(MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**<br>  
        공간 상호 작용 및 UI의 기본 구성 요소와 함께 Unity를 사용하여 혼합 현실 디자인 및 개발을 바로 시작합니다.   
    :::column-end:::
    :::column:::    
        [![혼합 현실 디자인 랩](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[혼합 현실 디자인 랩](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**<br>  
        MRTK의 기본 구성 요소를 사용하여 아름다운 혼합 현실 환경을 만드는 방법을 보여주는 샘플 앱을 다운로드하세요.
    :::column-end:::        
    :::column:::    
        [![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        VR을 위한 디자인. Microsoft Maquette를 사용하면 공간 프로토타입을 쉽고 빠르며 몰입감 있게 제작할 수 있습니다. 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="other-resources"></a>다른 리소스

:::row:::
    :::column:::
       [![기본 사항 이해](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)<br>
        **[기본 사항 이해](../discover/get-started-with-mr.md#understand-the-basics)**<br>
        혼합 현실을 정의하는 것이 무엇이며, 혼합 현실이 어떻게 사용되는지에 대해 더 잘 이해합니다.
    :::column-end:::
    :::column:::
        [![이벤트 참가](images/74-16.png)](../whats-new/sf-academy-events.md)<br>
         **[이벤트 참가](../whats-new/sf-academy-events.md)**<br>
        하드웨어를 살펴보고 첫 번째 HoloLens 2 애플리케이션을 만들기 위한 실습 자습서를 받으세요.
    :::column-end:::
    :::column:::
        [![도구 설치](images/74-17.png)](../develop/install-the-tools.md)<br>
         **[도구 설치](../develop/install-the-tools.md)**<br>
        설치 체크리스트를 사용하여 HoloLens와 혼합 현실용 앱을 빌드하는 데 필요한 도구를 구합니다.
    :::column-end:::
    :::column:::
        [![개발 시작](images/74-18.png)](../develop/development.md)<br>
        **[개발 시작](../develop/development.md)**<br>
        자신의 기술 수준, 작업 스타일 또는 플랫폼 관심 분야에 따라 개발 경로를 선택합니다.
    :::column-end:::
:::row-end:::

<br>

<br>
