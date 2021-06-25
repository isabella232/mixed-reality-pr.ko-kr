---
title: MRTK 없이 프로젝트 구성
description: Mixed Reality Toolkit 없이 Windows Mixed Reality 새 Unity 프로젝트를 구성하는 방법을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트, Windows Mixed Reality, UWP, XR, 성능
ms.openlocfilehash: 12c3272708c6375b550d87eac86fe13a60c1f36d
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906889"
---
# <a name="configuring-your-project-without-mrtk"></a>MRTK를 사용하지 않고 프로젝트 구성

WMR(Windows Mixed Reality)은 Windows 10 운영 체제의 일부로 도입된 Microsoft 플랫폼입니다. WMR 플랫폼을 사용하면 홀로그램 및 VR 디스플레이 디바이스에서 디지털 콘텐츠를 렌더링하는 애플리케이션을 빌드할 수 있습니다.

Microsoft와 커뮤니티는 WMR 환경을 자동으로 설정하는 [MRTK(Mixed Reality Toolkit)와](/windows/mixed-reality/mrtk-unity/configuration/usingupm) 같은 오픈 소스 도구를 만들었지만 많은 개발자는 처음부터 환경을 구축하려고 합니다.  다음 설명서에서는 MRTK 사용 여부에 관계없이 Mixed Reality 개발을 위한 프로젝트를 올바르게 설정하는 방법을 보여 드립니다.  변경해야 하는 설정은 프로젝트별 설정 및 장면별 설정의 두 가지 범주로 구분됩니다.

> [!NOTE]
> 나중에 언제든지 MRTK를 가져올 수 있으므로 수동 경로를 먼저 진행하기 위한 페널티가 없습니다.

WMR 수동 설정을 선택하는 경우 변경해야 하는 설정은 프로젝트당 및 장면당 두 가지 범주로 세분화됩니다.

## <a name="per-project-settings"></a>프로젝트별 설정

Desktop VR을 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택된 PC 독립 실행형 플랫폼을 사용하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-3.png)

HoloLens 2 대상으로 하는 경우 유니버설 Windows 플랫폼 전환해야 합니다.

1.  **파일 > 빌드 설정...** 을 선택합니다.
2.  플랫폼 목록에서 **유니버설 Windows 플랫폼** 선택하고 **플랫폼 전환을** 선택합니다.
3.  **Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.
4.  **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
5.  **Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.
6.  **UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.
7.  디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.

![유니버설 Windows 플랫폼 강조 표시된 Unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-4.png)

플랫폼을 설정하면 내보낼 때 2D 보기 대신 [몰입형 보기를](../../design/app-views.md) 만들도록 Unity에 알려야 합니다.

### <a name="for-xrsdk"></a>XRSDK의 경우 

1. Unity 편집기에서 **프로젝트 설정 > 편집으로** 이동하고 **XR 플러그 인 관리를** 선택합니다.

2. **XR 플러그 인 관리 설치를** 선택합니다.

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](images/wmr-config-img-5.png)

3. **시작 시 XR 초기화를** 선택하고 **Windows Mixed Reality**

![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](images/wmr-config-img-7.png)

4. **XR 플러그 인 관리 섹션을** 확장하고 **Univeral Windows 플랫폼 설정** 탭을 선택합니다.
5. Unity 2020 이상에서는 **OpenXR을** 확인하거나 **를 Windows Mixed Reality** 옵션이 표시됩니다. 
    * 런타임 중 하나를 선택할 수 있습니다.  HoloLens 2 또는 HP Reverb G2용으로 특별히 개발하고 **OpenXR을** 사용해 보려는 경우 OpenXR 상자를 선택하고 이 자습서로 돌아가기 전에 [Unity용 Mixed Reality OpenXR 플러그 인 사용](./xr-project-setup.md) 가이드를 검토하여 이러한 디바이스에 대해 올바르게 설정하세요.

> [!NOTE]
> Unity 2020 LTS부터 Microsoft는 OpenXR 개발을 수용하고 있습니다.  이 경로로 마이그레이션할 때 Unity 2021.1에서는 Windows XR 플러그 인이 더 이상 사용되지 않으며 2021.2에서 제거되어 OpenXR이 유일하게 지원되는 경로가 됩니다. 자세한 내용은 Mixed Reality [OpenXR 플러그 인 사용을](./xr-project-setup.md)참조하십시오.

6. **Windows Mixed Reality** 플러그 인을 선택하려는 경우 모든 확인란을 선택하고 **깊이 제출 모드를** **깊이 16비트로** 설정합니다.

![Windows Mixed Reality 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>레거시 XR의 경우 

> [!CAUTION]
> 레거시 XR은 Unity 2019에서 더 이상 사용되지 않으며 Unity 2020에서 제거되었습니다.

1. 빌드 **설정...에서 플레이어 설정...을** **엽니다. 창** 및 **XR 설정** 그룹 확장
2. **XR 설정** 섹션에서 **가상 현실 지원됨을** 선택하여 가상 현실 디바이스 목록을 추가합니다.
3. **깊이 형식을** **16비트 깊이로** 설정하고 **깊이 버퍼 공유를** 사용하도록 설정
4. **스테레오 렌더링 모드를** **단일 패스 인스턴스로** 설정
5. 홀로그램 **Remoting을 사용하려면 WSA 홀로그램 Remoting 지원됨을** 선택합니다. 

![플레이어 설정 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>매니페스트 업데이트

이제 앱에서 홀로그램 렌더링 및 공간 입력을 처리할 수 있습니다. 그러나 앱은 특정 기능을 활용하기 위해 매니페스트에서 적절한 기능을 선언해야 합니다. 유니버설 Windows 플랫폼 > 게시 설정 > 기능에 **대한 플레이어 설정 > 설정으로** 가서 프로젝트 기능을 찾을 수 있습니다. 

내보내는 모든 향후 프로젝트에 포함하려면 Unity에서 매니페스트 선언을 만드는 것이 좋습니다. Mixed Reality 일반적으로 사용되는 Unity API를 사용하도록 설정하는 데 적용 가능한 기능은 다음과 같습니다.

|  기능  |  기능이 필요한 API | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver(HoloLens의 [공간 매핑](../../design/spatial-mapping.md) 메시에 대한 액세스) &mdash; *헤드셋의 일반적인 공간 추적에 필요한 기능이 없습니다.* | 
|  웹캠  |  PhotoCapture 및 VideoCapture | 
|  PicturesLibrary / VideosLibrary  |  각각 PhotoCapture 또는 VideoCapture(캡처된 콘텐츠를 저장할 때) | 
|  마이크  |  VideoCapture(오디오 캡처 시), DictationRecognizer, GrammarRecognizer 및 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer(Unity Profiler 사용) | 

### <a name="quality-settings"></a>품질 설정

HoloLens에는 모바일 클래스 GPU가 있습니다. 앱이 HoloLens를 대상으로 하는 경우 가장 빠른 성능을 위해 튜닝된 앱의 품질 설정으로 시작하여 전체 프레임 속도를 유지하는 것이 좋습니다.  개발 과정에서 더 나아가면 품질 및 성능의 적절한 균형을 찾기 위해 품질 설정을 향상하는 것을 고려할 수 있습니다. 

1.  **프로젝트 설정 편집 > 품질 >** 선택합니다. 
2.  **Windows 스토어** 로고 아래의 **드롭다운을**   선택하고 매우  **낮음 을** 선택합니다. Windows 스토어 열의 상자와 매우 낮은 행이 녹색이면 설정이 올바르게 적용된 것을 알 수 있습니다. 
3.  **그림자** 섹션에서 그림자   사용 안 **함을 선택합니다.** 

![품질 설정 섹션이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 창의 스크린샷](images/wmr-config-img-10.png)<br>
*Unity 품질 설정*

## <a name="per-scene-settings"></a>장면별 설정

### <a name="unity-camera-settings"></a>Unity 카메라 설정

**Virtual Reality Supported를** 선택하면 [Unity 카메라](camera-in-unity.md) 구성 요소가 머리 추적 [및 스테레오 범위 렌더링을 처리합니다.](../platform-capabilities-and-apis/rendering.md) 즉, Main Camera 개체를 사용자 지정 카메라로 바꿀 필요가 없습니다.

앱이 특히 HoloLens를 대상으로 하는 경우 디바이스의 투명 디스플레이에 최적화하기 위해 몇 가지 설정을 변경해야 합니다. 이러한 설정을 사용하면 홀로그램 콘텐츠를 실제 세계에 표시할 수 있습니다.

1. **계층** 구조에서 **주 카메라를** 선택합니다.
2. **Inspector(검사기)** 패널에서 변환 **위치를** **0, 0, 0으로** 설정하여 사용자의 머리 위치가 Unity 세계 원본에서 시작되도록 합니다.
3. **플래그 지우기를** **단색으로 변경합니다.**
4. **배경색을** **RGBA 0,0,0,0으로 변경합니다.** HoloLens에서 검은색이 투명하게 렌더링됩니다.
5. **클리핑 평면** 변경 - [HoloLens 권장](camera-in-unity.md#using-clipping-planes) 0.85(미터) 근처에 있습니다.

![Unity 편집기에서 열린 검사기 탭의 스크린샷](images/wmr-config-img-11.png)<br>
*Unity 카메라 설정*

> [!IMPORTANT]
> 새 카메라를 삭제하고 만드는 경우 새 카메라에 **MainCamera** 태그가 지정되어 있는지 확인합니다.

## <a name="next-steps"></a>다음 단계

이제 프로젝트가 준비되면 Mixed Reality 환경 개발을 시작할 수 있습니다.

* [핵심 구성 요소](unity-development-overview.md#2-core-building-blocks) 추가
* 사용 가능한 [플랫폼 기능 및 API](unity-development-overview.md#3-advanced-features) 확인
* [앱을 배포하는](../platform-capabilities-and-apis/using-visual-studio.md#) 방법 알아보기
* Mixed Reality [시뮬레이터](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 사용

## <a name="see-also"></a>참고 항목
* [도구 설치](../install-the-tools.md)