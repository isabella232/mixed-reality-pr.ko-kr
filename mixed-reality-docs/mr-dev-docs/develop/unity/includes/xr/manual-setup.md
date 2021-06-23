---
ms.openlocfilehash: c965eb1b4edc91421e0b8b2e96893a04431aef6e
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112535727"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

새 Mixed Reality 기능 도구 애플리케이션을 사용하여 OpenXR 플러그 인을 설치합니다. 설치 [및 사용 지침에](../../welcome-to-mr-feature-tool.md) 따라 **플랫폼 지원** 범주에서 **Mixed Reality OpenXR 플러그 인** 패키지를 선택합니다.

![열려 있는 xr 플러그 인이 강조 표시된 Mixed Reality 기능 도구 패키지 창](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>빌드 대상 설정

Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.

1. **파일 > 빌드 설정...** 을 선택합니다.
2. 플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.
3. **아키텍처** 를 **ARM64** 로 설정합니다.
4. **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
5. **Build Type(빌드 형식)** 을 **D3D Project(D3D 프로젝트)** 로 설정합니다.
6. **대상 SDK 버전을** 최신 **설치로** 설정

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>OpenXR용 XR 플러그 인 관리 구성

OpenXR을 Unity의 런타임으로 설정하려면 다음을 수행합니다.

1. Unity 편집기에서 **프로젝트 설정 > 편집으로** 이동합니다.
2. 설정 목록에서 **XR 플러그 인 관리를** 선택합니다.
3. **XR 플러그 인 관리가** 강조 표시된 ![ Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷이 표시되면 XR 플러그 인 관리 설치를 선택합니다.](../../images/wmr-config-img-5.png)
4. 시작 시 **XR 초기화** 상자를 선택합니다.
5. 데스크톱 VR을 대상으로 하는 경우 PC 독립 실행형 탭(모니터)을 유지하고 **OpenXR** 및 **Windows Mixed Reality 기능 집합** 상자를 선택합니다.
6. HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 탭(Windows 로고)으로 전환하고 **OpenXR** 및 **Microsoft HoloLens 기능 집합** 상자를 선택합니다.

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](../../images/openxr-img-05.png)

> [!IMPORTANT]
> **OpenXR 플러그 인** 옆에 노란색 경고 아이콘이 표시되면 아이콘을 클릭하고 계속하기 전에 **모두 수정을** 선택합니다. Unity Editor를 다시 시작해야 변경 내용이 적용될 수 있습니다.

![OpenXR 프로젝트 유효성 검사 창의 스크린샷](../../images/openxr-img-06.png)

### <a name="optimization"></a>Optimization

HoloLens 2 위해 개발하는 경우 앱 성능을 향상하려면 **Mixed Reality > 프로젝트 > HoloLens 2** 권장 프로젝트 설정 적용 메뉴 항목을 선택합니다.

![OpenXR이 선택된 혼합 현실 메뉴 항목의 스크린샷](../../images/openxr-img-08.png)

이제 Unity에서 OpenXR로 개발을 시작할 준비가 되었습니다.  OpenXR 샘플을 사용하는 방법을 알아보려면 다음 섹션으로 계속 진행하세요.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>OpenXR 및 HoloLens 2 대한 Unity 샘플 프로젝트

Mixed Reality OpenXR 플러그 인을 사용하여 HoloLens 2 또는 Mixed Reality 헤드셋용 Unity 애플리케이션을 빌드하는 방법을 보여주는 샘플 Unity 프로젝트에 대한 OpenXR Mixed Reality [샘플 리포지션을](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 확인하세요.

또는 빈 프로젝트에서 직접 시작할 준비가 되면 [카메라 설정](../../camera-in-unity.md) 문서로 진행합니다.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

> [!CAUTION]
> Windows XR 플러그 인은 Unity 2021.1에서 더 이상 사용되지 않으며 Unity 2021.2에서 제거될 예정입니다.  Unity 2020 개발의 경우 OpenXR 플러그 인을 대신 사용하는 것이 좋습니다.

Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.

1.  **파일 > 빌드 설정...** 을 선택합니다.
2.  플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.
3.  **아키텍처** 를 **ARM64** 로 설정합니다.
4.  **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
5.  **Build Type(빌드 형식)** 을 **D3D Project(D3D 프로젝트)** 로 설정합니다.
6.  **대상 SDK 버전을** 최신 **설치로** 설정
7.  디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

플랫폼을 설정하면 내보낼 때 2D 보기 대신 [몰입형 보기를](../../../../design/app-views.md) 만들도록 Unity에 알려야 합니다.

1. Unity 편집기에서 **프로젝트 설정 > 편집으로** 이동하고 **XR 플러그 인 관리를** 선택합니다.

2. 표시되는 경우 **XR 플러그 인 관리 설치를** 선택합니다.

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-5.png)

3. **시작 시 XR 초기화를** 선택하고 **Windows Mixed Reality**

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-7.png)

4. **XR 플러그 인 관리**  >  **Windows Mixed Reality** 섹션을 선택하고, 모든 확인란을 선택하고, **깊이 버퍼 형식을 깊이 버퍼** **16비트로** 설정합니다.

![Windows Mixed Reality 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

> [!CAUTION]
> 레거시 XR은 Unity 2019에서 더 이상 사용되지 않으며 Unity 2020에서 제거되었습니다.

Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.

1.  **파일 > 빌드 설정...** 을 선택합니다.
2.  플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.
3.  **아키텍처** 를 **ARM64** 로 설정합니다.
4.  **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
5.  **Build Type(빌드 형식)** 을 **D3D Project(D3D 프로젝트)** 로 설정합니다.
6.  **대상 SDK 버전을** 최신 **설치로** 설정
7.  디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

플랫폼을 설정하면 내보낼 때 2D 보기 대신 [몰입형 보기를](../../../../design/app-views.md) 만들도록 Unity에 알려야 합니다.

1. 빌드 **설정...에서 플레이어 설정...을** **엽니다. 창** 및 **XR 설정** 그룹 확장
2. **XR 설정** 섹션에서 **가상 현실 지원됨을** 선택하여 가상 현실 디바이스 목록을 추가합니다.
3. **깊이 형식을** **16비트 깊이로** 설정하고 **깊이 버퍼 공유 사용을** 선택합니다.
4. **Stereo Rendering Mode(스테레오 렌더링 모드)** 를 **Single Pass Instanced(단일 패스 인스턴스화됨)** 로 설정합니다.
5. 홀로그램 재생 모드 **Remoting을 사용하려면 WSA 홀로그램 Remoting 지원됨을** 선택합니다.

![플레이어 설정 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-9.png)
