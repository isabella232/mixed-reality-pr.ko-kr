---
title: 레거시 기본 제공 XR 지원 사용
description: 레거시 기본 제공 XR 지원을 사용 하 여 MRTK를 사용 하거나 사용 하지 않고 Unity 프로젝트를 설정 하는 방법을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, mixed reality, 개발, 시작, 새 프로젝트, Windows Mixed Reality, UWP, XR, 성능, 레거시, mrtk
ms.openlocfilehash: b5faa48ec913c5095b12361318729b6f14276f30
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743500"
---
# <a name="using-legacy-built-in-xr-support"></a>레거시 기본 제공 XR 지원 사용

## <a name="setting-up-your-project-with-mrtk"></a>MRTK를 사용 하 여 프로젝트 설정

Unity용 MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다. MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼용 애플리케이션 개발을 가속화하기 위한 것입니다. 이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.

> [!div class="nextstepaction"]
> [MRTK 자습서 사용해보기](./tutorials/mr-learning-base-02.md?tabs=wsa)

기능에 대한 자세한 내용은 [MRTK 설명서](/windows/mixed-reality/mrtk-unity)를 살펴보세요.

## <a name="manual-setup-without-mrtk"></a>MRTK 없이 수동 설치

데스크톱 VR를 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택 된 PC 독립 실행형 플랫폼을 사용 하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시 된 unity 편집기에서 열리는 빌드 설정 창의 스크린샷](images/wmr-config-img-3.png)

HoloLens 2를 대상으로 하는 경우 유니버설 Windows 플랫폼로 전환 해야 합니다.

1.  **파일 > 빌드 설정** ...을 선택 합니다.
2.  플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 선택 합니다.
3.  **Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.
4.  **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
5.  **Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.
6.  **UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.
7.  디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.

![유니버설 Windows 플랫폼 강조 표시 된 unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-4.png)

플랫폼을 설정한 후에는 내보낼 때 Unity에서 2D 보기 대신 [몰입 형 보기](../../design/app-views.md) 를 만들도록 해야 합니다.

> [!CAUTION]
> 레거시 XR는 Unity 2019에서 더 이상 사용 되지 않으며 Unity 2020에서 제거 되었습니다.

1. 빌드 설정에서 **플레이어 설정** ...을 엽니다. **** **XR 설정** 그룹을 확장 합니다.
2. **XR 설정** 섹션에서 가상 현실 **지원 됨** 을 선택 하 여 가상 현실 장치 목록을 추가 합니다.
3. **깊이 형식을** **16 비트 깊이로** 설정 하 고 **깊이 버퍼 공유** 를 사용 하도록 설정 합니다.
4. **단일 패스 인스턴스로** **스테레오 렌더링 모드** 설정
5. Holographic 원격 기능을 사용 하려는 경우에는 **WSA Holographic Remoting 지원** 을 선택 합니다. 

![플레이어 설정 섹션이 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-9.png)