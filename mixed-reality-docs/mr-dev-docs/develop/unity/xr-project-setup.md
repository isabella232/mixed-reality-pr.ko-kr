---
title: XR 구성 설정
description: HoloLens 애플리케이션 개발을 위한 최신 Unity XR 구성 권장 사항을 최신 상태로 유지합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, mixed reality 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: d2904b9ea4771286b7091a8d5b7c599fcbd1244a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603729"
---
# <a name="setting-up-your-xr-configuration"></a>XR 구성 설정

Unity 버전을 [선택한](choosing-unity-version.md)후 다음 단계는 혼합 현실 앱을 빌드하는 데 사용할 XR 구성을 선택하는 것입니다.

## <a name="choosing-an-xr-configuration"></a>XR 구성 선택

새 Unity 프로젝트를 시작할 때 선택할 수 있는 다양한 XR 구성이 있습니다. **Mixed Reality OpenXR 플러그 인,** **Windows XR 플러그 인** 및 레거시 기본 제공 **XR.**

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>MRTK를 통해 프로젝트 설정

혼합 현실에 대한 Unity 프로젝트를 설정하는 가장 쉬운 방법은 MRTK(Mixed Reality Toolkit)를 이용하는 것입니다.  Unity용 MRTK는 놀라운 혼합 현실 애플리케이션을 쉽게 빌드할 수 있도록 설계된 오픈 소스 플랫폼 간 개발 키트입니다.

![MRTK](../../design/images/MRTK_UX_Hero.png)

MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.  MRTK 버전 2를 사용하면 Microsoft HoloLens, 몰입형(VR) 헤드셋 및 기타 여러 VR/AR 디바이스를 Windows Mixed Reality 애플리케이션 개발 속도를 단축할 수 있습니다. 이 프로젝트는 진입 장벽을 줄이는 것을 목표로 하며, 모든 사람이 혼합 현실 애플리케이션을 빌드하고 우리 모두가 성장함에 따라 커뮤니티에 다시 기여할 수 있도록 합니다.

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

Mixed Reality Toolkit 대한 자세한 내용은 [MRTK 설명서를 참조하세요.](/windows/mixed-reality/mrtk-unity)

## <a name="manual-setup-without-mrtk"></a>MRTK 없이 수동 설정

Microsoft와 커뮤니티는 혼합 현실에 대한 환경을 자동으로 설정하는 [MRTK(Mixed Reality Toolkit)와](/windows/mixed-reality/mrtk-unity) 같은 오픈 소스 도구를 만들었지만, 일부 개발자는 처음부터 환경을 구축하려고 할 수 있습니다.

[!INCLUDE[](includes/xr/manual-setup.md)]