---
ms.openlocfilehash: 639a96785e666cc3f5da3577ec3166f364753ed5
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603734"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

새 Mixed Reality 기능 도구 응용 프로그램을 사용 하 여 OpenXR 플러그 인을 설치 합니다. [설치 및 사용 지침](../../welcome-to-mr-feature-tool.md) 에 따라 **플랫폼 지원** 범주에서 **Mixed Reality OpenXR 플러그 인** 패키지를 선택 합니다.

![Open xr 플러그 인이 강조 표시 된 혼합 현실 기능 도구 패키지 창](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>빌드 대상 설정

데스크톱 VR를 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택 된 PC 독립 실행형 플랫폼을 사용 하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시 된 unity 편집기에서 열리는 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

HoloLens 2를 대상으로 하는 경우 유니버설 Windows 플랫폼로 전환 해야 합니다.

1. **파일 > 설정 빌드** ...를 선택 합니다.
2. 플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 선택 합니다.
3. **아키텍처** 를 **ARM64** 로 설정합니다.
4. **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
5. **Build Type(빌드 형식)** 을 **D3D Project(D3D 프로젝트)** 로 설정합니다.
6. **대상 SDK 버전** 을 **설치 된 최신** 버전으로 설정

![유니버설 Windows 플랫폼 강조 표시 된 unity 편집기에서 열리는 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>OpenXR에 대 한 XR 플러그 인 관리 구성

OpenXR을 Unity에서 런타임으로 설정 하려면 다음을 수행 합니다.

1. Unity 편집기에서 **편집 > Project** 으로 이동 설정
2. 설정 목록에서 **XR 플러그 인 관리** (MRFT를 사용 하 여 Mixed Reality OpenXR 플러그 인을 설치한 경우에는 이미 설치 되어 있어야 함)를 선택 합니다.
3. **XR On 시작 시 초기화** 상자를 선택 합니다.
4. 데스크톱 VR를 대상으로 하는 경우 PC 독립 실행형 탭 (모니터)을 그대로 유지 하 고 **OpenXR** 및 **Windows Mixed Reality 기능 집합** 확인란을 선택 합니다.
5. HoloLens 2를 대상으로 하는 경우 유니버설 Windows 플랫폼 탭 (Windows 로고)으로 전환 하 고 **OpenXR** 및 **Microsoft HoloLens 기능 집합** 상자를 선택 합니다.

![XR 플러그 인 관리를 강조 표시 한 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](../../images/openxr-img-05.png)

> [!IMPORTANT]
> **OpenXR 플러그 인** 옆에 노란색 경고 아이콘이 표시 되 면이 아이콘을 클릭 하 고 계속 하기 전에 **모두 수정** 을 선택 합니다. Unity Editor를 다시 시작해야 변경 내용이 적용될 수 있습니다.

![OpenXR 프로젝트 유효성 검사 창의 스크린샷](../../images/openxr-img-06.png)

### <a name="optimization"></a>Optimization

HoloLens 2를 개발 하는 경우에는 **혼합 현실 > Project > HoloLens 2 메뉴 항목에 권장 되는 프로젝트 설정 적용** 을 선택 하 여 더 나은 앱 성능을 얻을 수 있습니다.

![OpenXR가 선택 된 혼합 현실 메뉴 항목 열기의 스크린샷](../../images/openxr-img-08.png)

이제 Unity에서 OpenXR를 사용 하 여 개발을 시작할 준비가 되었습니다.  OpenXR 샘플을 사용 하는 방법을 알아보려면 다음 섹션을 계속 진행 합니다.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>OpenXR 및 HoloLens 2에 대 한 Unity 샘플 프로젝트

sample unity 프로젝트에 대 한 [OpenXR Mixed reality 샘플 리포지토리](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 를 확인 합니다. 보여주는 혼합 현실 OpenXR 플러그 인을 사용 하 여 HoloLens 2 또는 혼합 현실 헤드셋 용 unity 응용 프로그램을 빌드하는 방법입니다.

또는 빈 프로젝트에서 직접 시작할 준비가 되 면 [카메라 설정](../../camera-in-unity.md) 문서를 진행 하세요.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

> [!CAUTION]
> Windows XR 플러그 인은 unity 2021.1에서 더 이상 사용 되지 않으며 unity 2021.2에서 제거 될 예정입니다.  Unity 2020 개발의 경우 OpenXR 플러그 인을 대신 권장 합니다.

데스크톱 VR를 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택 된 PC 독립 실행형 플랫폼을 사용 하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시 된 unity 편집기에서 열리는 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

HoloLens 2를 대상으로 하는 경우 유니버설 Windows 플랫폼로 전환 해야 합니다.

1.  **파일 > 설정 빌드** ...를 선택 합니다.
2.  플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 선택 합니다.
3.  **아키텍처** 를 **ARM64** 로 설정합니다.
4.  **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
5.  **Build Type(빌드 형식)** 을 **D3D Project(D3D 프로젝트)** 로 설정합니다.
6.  **대상 SDK 버전** 을 **설치 된 최신** 버전으로 설정
7.  디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.

![유니버설 Windows 플랫폼 강조 표시 된 unity 편집기에서 열리는 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

플랫폼을 설정한 후에는 내보낼 때 Unity에서 2D 보기 대신 [몰입 형 보기](../../../../design/app-views.md) 를 만들도록 해야 합니다.

1. Unity 편집기에서 **편집 > Project 설정** 으로 이동 하 고 **XR 플러그 인 관리** 를 선택 합니다.

2. **XR 플러그 인 관리 설치** (표시 되는 경우)를 선택 합니다.

![XR 플러그 인 관리가 강조 표시 된 unity 편집기에서 열린 Project 설정 창의 스크린샷](../../images/wmr-config-img-5.png)

3. **시작 시 XR 초기화** 를 선택 하 고 **Windows Mixed Reality**

![XR 플러그 인 관리가 강조 표시 된 unity 편집기에서 열리는 Project 설정 창의 스크린샷](../../images/wmr-config-img-7.png)

4. **XR 플러그 인 관리**  >  **Windows Mixed Reality** 섹션을 선택 하 고 모든 상자를 선택 하 고 **깊이 버퍼 형식을** **깊이 버퍼 16 비트로** 설정 합니다.

![Windows Mixed Reality 섹션이 강조 표시 된 unity 편집기에서 열리는 Project 설정 창의 스크린샷](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

> [!CAUTION]
> 레거시 XR는 Unity 2019에서 더 이상 사용 되지 않으며 Unity 2020에서 제거 되었습니다.

데스크톱 VR를 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택 된 PC 독립 실행형 플랫폼을 사용 하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시 된 unity 편집기에서 열리는 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

HoloLens 2를 대상으로 하는 경우 유니버설 Windows 플랫폼로 전환 해야 합니다.

1.  **파일 > 설정 빌드** ...를 선택 합니다.
2.  플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 선택 합니다.
3.  **아키텍처** 를 **ARM64** 로 설정합니다.
4.  **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
5.  **Build Type(빌드 형식)** 을 **D3D Project(D3D 프로젝트)** 로 설정합니다.
6.  **대상 SDK 버전** 을 **설치 된 최신** 버전으로 설정
7.  디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.

![유니버설 Windows 플랫폼 강조 표시 된 unity 편집기에서 열리는 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

플랫폼을 설정한 후에는 내보낼 때 Unity에서 2D 보기 대신 [몰입 형 보기](../../../../design/app-views.md) 를 만들도록 해야 합니다.

1. 빌드 설정에서 **플레이어 설정** 열기 ... **** **XR 설정** 그룹을 확장 합니다.
2. **XR 설정** 섹션에서 가상 현실 **지원 됨** 을 선택 하 여 가상 현실 장치 목록을 추가 합니다.
3. **깊이 형식을** **16 비트 깊이로** 설정 하 고 **깊이 버퍼 공유 사용** 을 선택 합니다.
4. **Stereo Rendering Mode(스테레오 렌더링 모드)** 를 **Single Pass Instanced(단일 패스 인스턴스화됨)** 로 설정합니다.
5. Holographic play 모드 원격 기능을 사용 하려는 경우에는 **WSA Holographic Remoting 지원** 을 선택 합니다.

![플레이어 설정 섹션이 강조 표시 된 unity 편집기에서 열린 Project 설정 창의 스크린샷](../../images/wmr-config-img-9.png)
