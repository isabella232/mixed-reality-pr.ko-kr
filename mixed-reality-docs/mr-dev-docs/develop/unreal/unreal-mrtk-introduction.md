---
title: MRTK for Unreal 소개
description: Mixed Reality Toolkit for Unreal이 새로운 혼합 현실 개발자에게 제공하는 모든 기능을 시작하세요.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 테스트, Mixed Reality Toolkit, MRTK 버전 2, MRTK, 도구, SDK, HoloLens, HoloLens 2, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 플랫폼 간
ms.openlocfilehash: 3d46b92dbf3182ca5a50a8e106d2b947e4f7120f
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394287"
---
# <a name="introducing-mrtk-for-unreal"></a>MRTK for Unreal 소개

![MRTK 배너 이미지](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>MRTK(Mixed Reality Toolkit)란?

MRTK는 HoloLens가 처음 릴리스된 이후부터 사용되어 온 놀라운 오픈 소스 도구 키트입니다. 기여 개발자 커뮤니티의 노력이 없었다면 오늘날의 도구 키트가 될 수 없었을 것입니다. 

MRTK-Unreal(Mixed Reality Toolkit for Unreal)은 플러그 인, 샘플 및 설명서의 형태로 구성된 구성 요소 세트로, Unreal Engine을 사용하여 혼합 현실 애플리케이션의 개발을 지원하도록 설계되었습니다. 현재 이 도구 키트는 다음과 같은 요소로 구성됩니다.
* [UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) - Hololens 2 애플리케이션용 UX 기능 구현을 위한 코드, 청사진 및 예제를 제공합니다.
* [Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal) - 성능 예산에 맞추면서 혼합 현실 애플리케이션의 시각적 충실도를 개선하는 데 도움이 됩니다.

[GitHub의 MRTK 설명서](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)를 살펴보고 [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) 또는 [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) 설치 가이드를 시작하세요.

### <a name="modular"></a>모듈식

모듈식으로 MRTK Unreal을 빌드했으므로 도구 키트의 모든 비트를 프로젝트에 적용할 필요가 없습니다. 필요한 플러그 인을 선택하고 적절하다고 생각할 때마다 추가하거나 제거할 수 있습니다. 이 방법을 통해 더 쉽게 프로젝트 크기를 더 작게 유지하고 관리할 수 있습니다.  

### <a name="performant"></a>성능 기준에 적합

모바일 플랫폼을 사용하는 경우 성능을 고려하여 MRTK Unreal을 구축했습니다. 이는 매우 중요하며, 도구가 사용자에게 불리하게 작동하지 않도록 하려 했습니다.

## <a name="project-setup"></a>프로젝트 설정

> [!div class="nextstepaction"]
> [Unreal Engine 및 MRTK 다운로드](unreal-project-setup.md)

## <a name="see-also"></a>참고 항목

* [도구 설치](../install-the-tools.md)
* [MRTK for Unreal을 사용한 개발](unreal-development-overview.md)
* [UX Tools - 설치 가이드(GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [UX Tools - 설명서 홈(GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [Graphics Tools - 설치 가이드(GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [Graphics Tools - 설명서 홈(GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)