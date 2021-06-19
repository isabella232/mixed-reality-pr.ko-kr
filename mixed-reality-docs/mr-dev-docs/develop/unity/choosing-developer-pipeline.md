---
title: 개발자 파이프라인 선택
description: HoloLens 응용 프로그램 개발에 대 한 최신 Unity development development 파이프라인 권장 사항을 최신 상태로 유지 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394557"
---
# <a name="choosing-your-developer-pipeline"></a>개발자 파이프라인 선택

![Unity 로고 배너](../images/unity_logo_banner.png)<br>

현재 **Unity 2019.4 LTS를 설치 하 고 혼합 현실 개발용으로 레거시 기본 제공 XR를 사용 하는 것이 좋습니다** . 다른 Unity 구성으로 앱을 빌드할 수도 있습니다.

## <a name="mixed-reality-toolkit-recommended"></a>Mixed Reality Toolkit (권장)

Microsoft의 최신 권장 Unity 구성은 HoloLens 2에 대 한 혼합 현실 도구 키트 ...

### <a name="install-the-mixed-reality-feature-tool"></a>혼합 현실 기능 도구 설치

[Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)은 개발자가 혼합형 현실 기능 패키지를 검색하고 Unity 프로젝트에 추가하는 데 사용되는 새로운 방법입니다. 

이름 또는 범주로 패키지를 검색하고, 종속성을 확인하고, 가져오기 전에 프로젝트 매니페스트 파일에 대한 제안된 변경 내용도 볼 수 있습니다. 원하는 패키지의 유효성을 검사하면 Mixed Reality Feature Tool에서 사용자가 선택한 프로젝트로 해당 패키지를 다운로드합니다.

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a>Unity 용 Mixed Reality Toolkit 가져오기

![MRTK](../../design/images/MRTK_UX_Hero.png)

MRTK([Mixed Reality Toolkit](mrtk-getting-started.md))는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다. 

* [설치 및 사용 지침](welcome-to-mr-feature-tool.md#system-requirements)을 따르고 **Mixed Reality Toolkit Foundation** 패키지를 선택하여 Mixed Reality Toolkit 패키지를 설치합니다.

큐레이트된 [HoloLens](unity-development-overview.md#1-getting-started) 또는 [VR](unity-development-wmr-overview.md#1-getting-started) 개발 경험의 시작 섹션을 완료하는 것이 좋습니다. HoloLens용 Unity 개발 경험을 이미 따르고 있는 경우 아래 나열된 나머지 설정 단계를 완료하고 [HoloLens 2 시작 자습서](tutorials/mr-learning-base-01.md)를 계속 진행하세요.

> [!IMPORTANT]
> 설치 지침은 MRTK 및 Unity 릴리스의 안정적인 최신 조합인 **MRTK 2.6.1** 및 **Unity 2019.4 LTS** 를 대상으로 합니다.

> [!NOTE]
> Unity에 MRTK를 사용하지 않으려면 [모든 상호 작용과 동작을 직접 스크립팅](configure-unity-project.md)해야 합니다.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 배너](../images/MRTK-Unity-Banner.png)<br>**Mixed Reality Toolkit-Unity(GitHub)** </a><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a>수동 

TBD ...