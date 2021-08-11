---
title: 레거시 기본 제공 XR 지원 사용
description: 레거시 기본 제공 XR 지원을 사용하여 MRTK 유무에 관계없이 Unity 프로젝트를 설정하는 방법을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트, Windows Mixed Reality, UWP, XR, 성능, 레거시, mrtk
ms.openlocfilehash: 534df0b9c4efbe62b00af6cccb74f4203c1557e9479b2101320bab3bbdb5e565
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192062"
---
# <a name="using-legacy-built-in-xr-support"></a>레거시 기본 제공 XR 지원 사용

## <a name="setting-up-your-project-with-mrtk"></a>MRTK를 통해 프로젝트 설정

Unity용 MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다. MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼용 애플리케이션 개발을 가속화하기 위한 것입니다. 이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.

> [!div class="nextstepaction"]
> [MRTK 자습서 사용해보기](./tutorials/mr-learning-base-02.md?tabs=wsa)

기능에 대한 자세한 내용은 [MRTK 설명서](/windows/mixed-reality/mrtk-unity)를 살펴보세요.

## <a name="manual-setup-without-mrtk"></a>MRTK 없이 수동 설정

Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-3.png)

HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼으로 전환해야 합니다.

1.  **파일 > 빌드 설정...** 를 선택합니다.
2.  플랫폼 목록에서 **유니버설 Windows 플랫폼을** 선택하고 **플랫폼 전환을** 선택합니다.
3.  **Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.
4.  **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
5.  **Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.
6.  **UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.
7.  디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.

![유니버설 Windows 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-4.png)

플랫폼을 설정하면 내보낼 때 2D 보기 대신 [몰입형 보기를](../../design/app-views.md) 만들도록 Unity에 알려야 합니다.

> [!CAUTION]
> 레거시 XR은 Unity 2019에서 더 이상 사용되지 않으며 Unity 2020에서 제거되었습니다.

1. 빌드 설정... 에서 **플레이어 설정...을 엽니다.** **창** 및 **XR 설정** 그룹 확장
2. **XR 설정** 섹션에서 가상 현실 **지원됨을** 선택하여 가상 현실 디바이스 목록을 추가합니다.
3. **깊이 형식을** **16비트 깊이로** 설정하고 **깊이 버퍼 공유를** 사용하도록 설정
4. **스테레오 렌더링 모드를** **단일 패스 인스턴스로** 설정
5. 홀로그램 **Remoting을 사용하려면 WSA 홀로그램 Remoting 지원됨을** 선택합니다. 

![플레이어 설정 섹션이 강조 표시된 unity 편집기에서 열린 Project 설정 창의 스크린샷](images/wmr-config-img-9.png)