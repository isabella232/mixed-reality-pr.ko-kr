---
title: Windows XR 플러그 인 사용
description: Windows XR 지원을 사용 하 여 MRTK를 사용 하거나 사용 하지 않고 Unity 프로젝트를 설정 하는 방법을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, mixed reality, 개발, 시작, 새 프로젝트, Windows Mixed Reality, UWP, XR, 성능, 레거시, mrtk, Windows
ms.openlocfilehash: 81d1c3113dcf2c301077bcfec44afa80bd5d9be3
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088582"
---
# <a name="using-windows-xr-plugin"></a>Windows XR 플러그 인 사용

Unity 2020를 대상으로 하는 개발자를 위해 Windows XR 플러그 인을 사용 하면 HoloLens 2 및 Windows Mixed Reality 헤드셋의 혼합 현실 기능에 액세스할 수 있습니다.  이 플러그 인은 Unity 2019 에서도 지원 되지만, 해당 버전에서이 플러그 인을 사용 하는 경우 Azure 공간 앵커와의 알려진 비 호환성은 있습니다.

Microsoft 및 커뮤니티에서는 WMR 환경을 자동으로 설정 하는 [mrtk (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 와 같은 활용 도구를 만들었으므로 많은 개발자 들이 처음부터 환경을 구축 하려고 합니다.  다음 설명서에서는 MRTK를 사용 하는지 여부에 관계 없이 혼합 현실 개발용으로 프로젝트를 올바르게 설정 하는 방법을 보여 줍니다.  변경 해야 하는 설정은 프로젝트 당 설정 및 장면 별 설정의 두 가지 범주로 구분 됩니다.

## <a name="setting-up-your-project-with-mrtk"></a>MRTK를 사용 하 여 프로젝트 설정

Unity용 MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다. MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼용 애플리케이션 개발을 가속화하기 위한 것입니다. 이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.

> [!div class="nextstepaction"]
> [MRTK 자습서를 사용해 보세요.](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=winxr)

추가 기능에 대 한 자세한 내용은 [Mrtk의 설명서](/windows/mixed-reality/mrtk-unity) 를 참조 하세요.

## <a name="manual-setup-without-mrtk"></a>MRTK 없이 수동 설치

데스크톱 VR를 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택 된 PC 독립 실행형 플랫폼을 사용 하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시 된 unity 편집기에서 열리는 빌드 설정 창의 스크린샷](images/wmr-config-img-3.png)

HoloLens 2를 대상으로 하는 경우 유니버설 Windows 플랫폼로 전환 해야 합니다.

1.  **파일 > 빌드 설정** ...을 선택 합니다.
2.  플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 선택 합니다.
3.  **아키텍처** 를 **ARM 64** 로 설정 합니다.
4.  **대상 장치** 를 **HoloLens** 로 설정
5.  **빌드 유형을** **D3D** 로 설정
6.  **UWP SDK** 를 **최신 설치** 로 설정
7.  디버그에 알려진 성능 문제가 있으므로 **빌드 구성을** **릴리스로** 설정 합니다.

![유니버설 Windows 플랫폼 강조 표시 된 unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-4.png)

플랫폼을 설정한 후에는 내보낼 때 Unity에서 2D 보기 대신 [몰입 형 보기](../../design/app-views.md) 를 만들도록 해야 합니다.

1. Unity 편집기에서 **편집 > 프로젝트 설정** 으로 이동 하 고 **XR 플러그 인 관리** 를 선택 합니다.

2. **XR 플러그 인 관리 설치** 를 선택 합니다.

![XR 플러그 인 관리가 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-5.png)

3. 시작 및 **Windows Mixed Reality** **에서 XR 초기화를** 선택 합니다.

![XR 플러그 인 관리가 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-7.png)

4. **XR 플러그 인 관리** 섹션을 확장 하 고 **유니버설 Windows 플랫폼 설정** 탭을 선택 합니다.
5. Unity 2020 이상 버전을 사용 하는 경우 **OpenXR** 또는 **Windows Mixed Reality** 를 확인 하는 옵션이 표시 됩니다. 
    * 런타임 중 하나를 선택할 수 있습니다.  HoloLens 2 또는 HP 반향 G2에 대해 구체적으로 개발 하 고 **OpenXR** 을 시도 하기로 결정 한 경우 OpenXR 상자를 선택 하 고이 자습서로 돌아가기 전에 [Mixed Reality OpenXR 플러그 인 Unity를 사용 하 여](openxr-getting-started.md) 이러한 장치에 대해 올바르게 설정 하는 가이드를 검토 합니다.

> [!NOTE]
> Unity 2020 LTS부터 Microsoft는 OpenXR을 사용 하 여 개발을 수용 하 고 있습니다.  이 경로로 마이그레이션하는 동안 Unity 2021.1에서 Windows XR 플러그 인이 지원 되지 않고 2021.2에서 OpenXR만 지원 됩니다. [Mixed Reality OpenXR 플러그 인을 사용 하 여](openxr-getting-started.md)에서 자세한 정보를 찾을 수 있습니다.

6. **Windows Mixed Reality** 플러그 인을 선택 하기로 결정 한 경우 모든 상자를 선택 하 고 **깊이 전송 모드** 를 **깊이 16 비트로** 설정 합니다.

![Windows Mixed Reality 섹션이 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-8.png)
