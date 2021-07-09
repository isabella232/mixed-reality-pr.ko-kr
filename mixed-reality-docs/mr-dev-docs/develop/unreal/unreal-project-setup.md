---
title: Unreal 프로젝트 설정
description: 최신 버전의 Unreal Engine 및 Mixed Reality Feature Tool로 프로젝트를 설정하는 방법을 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, mixed reality, 개발, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 홀로그램, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 8201e97ed35d11404928c1dfe94ad9b7e626e51b
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394615"
---
# <a name="setting-up-your-unreal-project"></a>Unreal 프로젝트 설정

HoloLens에 기본 제공되는 지원 기능을 최대한 활용하려면 [Unreal Engine 버전 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 이상을 설치하는 것이 좋습니다.

Epic Games 시작 관리자에서 **라이브러리** 탭으로 이동한 다음, **시작** 옆의 드롭다운 화살표를 선택하고 **옵션** 을 클릭합니다. **대상 플랫폼** 에서 **HoloLens 2** 를 선택하고 **적용** 을 클릭합니다.
![Unreal 설치 옵션 HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>Unreal용 Mixed Reality Toolkit 가져오기

![MRTK](../../design/images/MRTK_UX_Hero.png)

MRTK(Mixed Reality Toolkit)는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다. MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다. 도구 키트는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안되었습니다.

설치의 경우 큐레이션된 [Unreal 개발 경험](unreal-development-overview.md)의 [시작 섹션](unreal-development-overview.md#1-getting-started)을 완료하는 것이 좋습니다. Unreal 개발 경험을 이미 수행하고 있는 경우 아래 나열된 나머지 설정 단계를 완료하고 [HoloLens 2 시작 자습서](tutorials/unreal-uxt-ch1.md)를 계속 진행하세요.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 로고 이미지](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal(GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Unreal에 MRTK를 사용하지 않으려면 모든 상호 작용과 동작을 직접 스크립팅해야 합니다.