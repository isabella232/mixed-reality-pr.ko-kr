---
title: XR 구성 설정
description: HoloLens 애플리케이션 개발을 위한 최신 Unity XR 구성 권장 사항을 최신 상태로 유지합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, mixed reality 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: d265725caf95379dfa01baa6dad1b7927fbeca5c
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906946"
---
# <a name="setting-up-your-xr-configuration"></a>XR 구성 설정

새 Unity 프로젝트를 시작할 때 XR 요구 사항을 처리하기 위한 세 가지 옵션이 있습니다. 
* OpenXR 플러그 인
* Windows XR 플러그 인
* 레거시 XR 플러그 인

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>MRTK를 통해 프로젝트 설정

Unity용 MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다. MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼용 애플리케이션 개발을 가속화하기 위한 것입니다. 이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.

> [!div class="nextstepaction"]
> [MRTK 자습서 사용해보기](./tutorials/mr-learning-base-02.md?tabs=winxr)

기능에 대한 자세한 내용은 [MRTK 설명서](/windows/mixed-reality/mrtk-unity)를 살펴보세요.

### <a name="using-mrtk-with-openxr-support"></a>OpenXR 지원과 함께 MRTK 사용

MRTK-Unity 2.7 릴리스는 Mixed Reality OpenXR 플러그 인에 대한 향상된 지원을 제공합니다.

Mixed Reality [기능 도구를](welcome-to-mr-feature-tool.md) 다시 열어 아직 설치하지 않은 경우 Mixed Reality 도구 키트를 설치합니다. OpenXR 지원은 **Foundation** 패키지에 있습니다.

[OpenXR로 마이그레이션하는](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)자세한 내용은 MRTK 설명서를 참조하세요.

> [!NOTE]
> **2.5.3** 이전 버전의 MRTK에서 업그레이드하는 경우 다음 줄이 **Assets/MixedRealityToolkit.Generated/link.xml** 파일에 있는지 확인합니다.
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> MRTK 2.5.4 이상으로 시작한 경우 이 줄이 기본적으로 추가됩니다.

## <a name="manual-setup-without-mrtk"></a>MRTK 없이 수동 설정

Microsoft와 커뮤니티는 WMR 환경을 자동으로 설정하는 [MRTK(Mixed Reality Toolkit)와](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 같은 오픈 소스 도구를 만들었지만 많은 개발자는 처음부터 환경을 구축하려고 합니다.

[!INCLUDE[](includes/xr/manual-setup.md)]