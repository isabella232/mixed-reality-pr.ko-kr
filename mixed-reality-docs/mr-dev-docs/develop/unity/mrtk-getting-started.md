---
title: Unity용 MRTK 소개
description: 플랫폼 간 Mixed Reality Toolkit이 새로운 혼합 현실 개발자에게 제공하는 모든 기능을 시작합니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 테스트, Mixed Reality Toolkit, MRTK 버전 2, MRTK, 도구, SDK, HoloLens, HoloLens 2, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 플랫폼 간
ms.openlocfilehash: b153c267e20b0f9609c2fe507512051b24a2b62b
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008832"
---
# <a name="introducing-mrtk-for-unity"></a>Unity용 MRTK 소개

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>MRTK(Mixed Reality Toolkit)란?

MRTK는 HoloLens가 처음 릴리스된 이후부터 사용되어 온 놀라운 오픈 소스 도구 키트입니다. 기여 개발자 커뮤니티의 노력이 없었다면 오늘날의 도구 키트가 될 수 없었을 것입니다. 가장 중요한 문제를 고려하기 위해 지난 3년간 개발자 커뮤니티의 피드백을 주의 깊게 살피면서 MRTK v2를 구축했습니다.  

Unity용 MRTK는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다. 도구 키트는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다. MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼용 애플리케이션 개발을 가속화하기 위한 것입니다. 이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

[GitHub에 대한 MRTK 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)를 살펴보고 [설치 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)를 시작하세요.


## <a name="new-with-mrtk-v2"></a>MRTK v2의 새로운 기능

여기서는 이러한 플랫폼 도구에 대한 약속을 강조하려고 합니다.  실제로 MRTK 버전 2를 사용하여 OOBE(Out-of-Box Setup Experience) 및 Mixed Reality 팁 애플리케이션과 같은 받은 편지함 환경을 개발했습니다. 또한 플랫폼에서 개발하는 것이 가장 좋은 방법이라고 생각하므로 새로운 HoloLens 2 기능이 MRTK를 통해 처음 공개될 것으로 예상할 수 있습니다. 

### <a name="modular"></a>모듈식

모듈식으로 빌드했으므로 도구 키트의 모든 비트를 프로젝트에 적용할 필요가 없습니다.  실제로 몇 가지 이점이 있습니다.  이를 통해 프로젝트 크기를 더 작게 유지하고 관리하기가 더 쉽습니다.  또한 스크립트 가능한 개체를 사용하여 빌드되고 인터페이스를 기반으로 하므로 포함된 구성 요소를 사용자 고유의 구성 요소로 바꿔 다른 서비스, 시스템 및 플랫폼을 지원할 수도 있습니다.

### <a name="cross-platform"></a>플랫폼 간

다른 플랫폼과 관련하여 플랫폼 간 지원이 제공됩니다.  이는 모든 단일 플랫폼이 지원된다는 것을 의미하지는 않지만, 빌드 대상을 다른 플랫폼으로 전환할 때 도구 키트 코드가 중단되지 않도록 했습니다.  모듈식 설계를 통한 견고성과 확장성은 ARCore, ARKit 및 OpenVR과 같은 여러 플랫폼을 지원하도록 앱을 설정합니다.

### <a name="performant"></a>성능 기준에 적합

모바일 플랫폼을 사용하는 경우 성능을 고려하여 구축했습니다.  이는 매우 중요하며, 도구가 사용자에게 불리하게 작동하지 않도록 하려 했습니다.

## <a name="see-also"></a>참고 항목

* [도구 설치](../install-the-tools.md)
* [MRTK - 설치 가이드(GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [MRTK - 설명서 홈(GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [HoloToolkit/MRTK에서 MRTK 버전 2로 포팅(GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
