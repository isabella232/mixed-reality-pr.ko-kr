---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394587"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

새 Mixed Reality 기능 도구 애플리케이션을 사용하여 OpenXR 플러그 인을 설치합니다. 설치 [및 사용 지침에](../../welcome-to-mr-feature-tool.md) 따라 Mixed Reality Toolkit 범주에서 **Mixed Reality OpenXR 플러그 인** 패키지를 선택합니다.

![열려 있는 xr 플러그 인이 강조 표시된 Mixed Reality 기능 도구 패키지 창](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>빌드 대상 설정

Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.

1. **파일 > 빌드 설정...** 을 선택합니다.
2. 플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.
3. **Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.
4. **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
5. **Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.
6. **UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>OpenXR용 XR 플러그 인 관리 구성

OpenXR을 Unity의 런타임으로 설정하려면 다음을 수행합니다.

1. Unity 편집기에서 **프로젝트 설정 > 편집으로** 이동합니다.
2. 설정 목록에서 **XR 플러그 인 관리를** 선택합니다.
3. 시작 시 **XR 초기화** 및 **OpenXR** 확인란을 선택합니다.
4. HoloLens 2 대상으로 하는 경우 UWP 플랫폼에 있는지 확인하고 **Microsoft HoloLens 기능 집합을** 선택합니다.

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](../../images/openxr-img-05.png)

### <a name="optimization"></a>Optimization

HoloLens 2 위해 개발하는 경우 **Mixed Reality> OpenXR > 앱** 성능을 향상하기 위해 HoloLens 2 권장 프로젝트 설정 적용으로 이동합니다.

![OpenXR이 선택된 혼합 현실 메뉴 항목의 스크린샷](../../images/openxr-img-08.png)

> [!IMPORTANT]
> **OpenXR 플러그 인** 옆에 노란색 경고 아이콘이 표시되면 아이콘을 클릭하고 계속하기 전에 **모두 수정을** 선택합니다. Unity Editor를 다시 시작해야 변경 내용이 적용될 수 있습니다.

![OpenXR 프로젝트 유효성 검사 창의 스크린샷](../../images/openxr-img-06.png)

이제 Unity에서 OpenXR로 개발을 시작할 준비가 되었습니다.  OpenXR 샘플을 사용하는 방법을 알아보려면 다음 섹션으로 계속 진행하세요.

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>OpenXR 및 HoloLens 2 대한 Unity 샘플 프로젝트

Mixed Reality OpenXR 플러그 인을 사용하여 HoloLens 2 또는 Mixed Reality 헤드셋용 Unity 애플리케이션을 빌드하는 방법을 보여주는 샘플 Unity 프로젝트에 대한 OpenXR Mixed Reality [샘플 리포지션을](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 확인하세요.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.

1.  **파일 > 빌드 설정...** 을 선택합니다.
2.  플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.
3.  **Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.
4.  **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
5.  **Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.
6.  **UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.
7.  디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

플랫폼을 설정하면 내보낼 때 2D 보기 대신 [몰입형 보기를](../../../../design/app-views.md) 만들도록 Unity에 알려야 합니다.

1. Unity 편집기에서 **프로젝트 설정 > 편집으로** 이동하고 **XR 플러그 인 관리를** 선택합니다.

2. **XR 플러그 인 관리 설치를** 선택합니다.

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-5.png)

3. **시작 시 XR 초기화를** 선택하고 **Windows Mixed Reality**

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-7.png)

4. **XR 플러그 인 관리 섹션을** 확장하고 **Univeral Windows 플랫폼 설정** 탭을 선택합니다.
5. Unity 2020 이상에서는 **OpenXR을** 확인하거나 **를 Windows Mixed Reality** 옵션이 표시됩니다. 
    * 런타임 중 하나를 선택할 수 있습니다.  HoloLens 2 또는 HP Reverb G2용으로 특별히 개발하고 **OpenXR을** 사용해 보려는 경우 OpenXR 상자를 선택하고 이 자습서로 돌아가기 전에 [Unity용 Mixed Reality OpenXR 플러그 인 사용](../../openxr-getting-started.md) 가이드를 검토하여 이러한 디바이스에 대해 올바르게 설정하세요.

> [!NOTE]
> Unity 2020 LTS부터 Microsoft는 OpenXR 개발을 수용하고 있습니다.  이 경로로 마이그레이션할 때 Unity 2021.1에서는 Windows XR 플러그 인이 더 이상 사용되지 않으며 2021.2에서 제거되어 OpenXR이 유일하게 지원되는 경로가 됩니다. 자세한 내용은 Mixed Reality [OpenXR 플러그 인 사용을](../../openxr-getting-started.md)참조하십시오.

6. **Windows Mixed Reality** 플러그 인을 선택하려는 경우 모든 확인란을 선택하고 **깊이 제출 모드를** **깊이 16비트로** 설정합니다.

![Windows Mixed Reality 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-3.png)

HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.

1.  **파일 > 빌드 설정...** 을 선택합니다.
2.  플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.
3.  **Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.
4.  **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
5.  **Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.
6.  **UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.
7.  디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](../../images/wmr-config-img-4.png)

플랫폼을 설정하면 내보낼 때 2D 보기 대신 [몰입형 보기를](../../../../design/app-views.md) 만들도록 Unity에 알려야 합니다.

> [!CAUTION]
> 레거시 XR은 Unity 2019에서 더 이상 사용되지 않으며 Unity 2020에서 제거되었습니다.

1. 빌드 **설정...에서 플레이어 설정...을** **엽니다. 창** 및 **XR 설정** 그룹 확장
2. **XR 설정** 섹션에서 **가상 현실 지원됨을** 선택하여 가상 현실 디바이스 목록을 추가합니다.
3. **깊이 형식을** **16비트 깊이로** 설정하고 **깊이 버퍼 공유를** 사용하도록 설정
4. **스테레오 렌더링 모드를** **단일 패스 인스턴스로** 설정
5. 홀로그램 **Remoting을 사용하려면 WSA 홀로그램 Remoting 지원됨을** 선택합니다. 

![플레이어 설정 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](../../images/wmr-config-img-9.png)