---
title: MRTK를 사용 하지 않고 프로젝트 구성
description: 혼합 현실 도구 키트 없이 Windows Mixed Reality 용 새 Unity 프로젝트를 구성 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, mixed reality, 개발, 시작, 새 프로젝트, Windows Mixed Reality, UWP, XR, 성능
ms.openlocfilehash: 47ca4041e997d623d08fa1732f7039c655810bfc
ms.sourcegitcommit: b0fb5497bf9f280ba5610c30e4b9e5aa1cda52c9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104837422"
---
# <a name="configuring-your-project-without-mrtk"></a>MRTK를 사용하지 않고 프로젝트 구성

Windows Mixed Reality (WMR)는 Windows 10 운영 체제의 일부로 도입 된 Microsoft 플랫폼입니다. WMR 플랫폼을 사용 하면 holographic 및 VR 디스플레이 장치에서 디지털 콘텐츠를 렌더링 하는 응용 프로그램을 빌드할 수 있습니다.

Microsoft 및 커뮤니티에서는 WMR 환경을 자동으로 설정 하는 [mrtk (Mixed Reality Toolkit)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 와 같은 활용 도구를 만들었으므로 많은 개발자 들이 처음부터 환경을 구축 하려고 합니다.  다음 설명서에서는 MRTK를 사용 하는지 여부에 관계 없이 혼합 현실 개발용으로 프로젝트를 올바르게 설정 하는 방법을 보여 줍니다.  변경 해야 하는 설정은 프로젝트 당 설정 및 장면 별 설정의 두 가지 범주로 구분 됩니다.

> [!NOTE]
> 나중에 언제 든 지 MRTK를 가져올 수 있으므로 수동 경로를 먼저 이동 하는 데는 아무런 영향이 없습니다.

WMR 수동 설치를 선택 하는 경우 변경 해야 하는 설정은 프로젝트별 및 장면의 두 가지 범주로 구분 됩니다.

## <a name="per-project-settings"></a>프로젝트별 설정

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

### <a name="for-xrsdk"></a>XRSDK의 경우 

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

### <a name="for-legacy-xr"></a>레거시 XR의 경우 

> [!CAUTION]
> 레거시 XR는 Unity 2019에서 더 이상 사용 되지 않으며 Unity 2020에서 제거 되었습니다.

1. 빌드 설정에서 **플레이어 설정** ...을 엽니다. **** **XR 설정** 그룹을 확장 합니다.
2. **XR 설정** 섹션에서 가상 현실 **지원 됨** 을 선택 하 여 가상 현실 장치 목록을 추가 합니다.
3. **깊이 형식을** **16 비트 깊이로** 설정 하 고 **깊이 버퍼 공유** 를 사용 하도록 설정 합니다.
4. **단일 패스 인스턴스로** **스테레오 렌더링 모드** 설정
5. Holographic 원격 기능을 사용 하려는 경우에는 **WSA Holographic Remoting 지원** 을 선택 합니다. 

![플레이어 설정 섹션이 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>매니페스트를 업데이트 하는 중

이제 앱이 holographic 렌더링 및 공간 입력을 처리할 수 있습니다. 그러나 특정 기능을 활용 하려면 앱이 해당 매니페스트에 적절 한 기능을 선언 해야 합니다. **플레이어 설정 > 설정 유니버설 Windows 플랫폼 > 게시 설정 > 기능** 으로 이동 하 여 프로젝트 기능을 찾을 수 있습니다. 

내보낸 이후 모든 프로젝트에 포함 하기 위해 Unity에서 매니페스트 선언을 만드는 것이 좋습니다. 혼합 현실에 일반적으로 사용 되는 Unity Api를 사용 하는 데 적용 되는 기능은 다음과 같습니다.

|  기능  |  기능을 필요로 하는 Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (HoloLens의 [공간 매핑](../../design/spatial-mapping.md) 메시에 대 한 액세스) &mdash; *헤드셋의 일반 공간 추적에 필요한 기능이 없습니다* . | 
|  웹캠  |  사진 캡처 및 VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  각각 사진 캡처 또는 VideoCapture (캡처된 콘텐츠를 저장 하는 경우) | 
|  마이크  |  VideoCapture (오디오 캡처 시), DictationRecognizer, GrammarRecognizer 및 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (및 Unity 프로파일러를 사용 하려면) | 

### <a name="quality-settings"></a>품질 설정

HoloLens에는 모바일 클래스 GPU가 있습니다. 앱이 HoloLens를 대상으로 하는 경우 전체 프레임 속도를 유지 하기 위해 가장 빠른 성능을 위해 조정 된 앱의 품질 설정으로 시작 하는 것이 좋습니다.  개발에 대 한 추가 작업을 수행 하는 경우 품질 및 성능에 대 한 적절 한 균형을 찾기 위해 품질 설정을 upping 할 수 있습니다. 

1.  **편집 > 프로젝트 설정 > 품질** 을 선택 합니다. 
2.  **Windows 스토어** 로고 아래의 **드롭다운** 을 선택   하 고  **매우 낮음** 을 선택 합니다. Windows 스토어 열의 상자와 매우 낮은 행이 녹색 인 경우 설정이 올바르게 적용 됨을 알 수 있습니다. 
3.  **그림자**   섹션에서 **그림자 사용 안 함** 을 선택 합니다. 

![품질 설정 섹션이 강조 표시 된 unity 편집기에서 열리는 프로젝트 설정 창의 스크린샷](images/wmr-config-img-10.png)<br>
*Unity 품질 설정*

## <a name="per-scene-settings"></a>장면 별 설정

### <a name="unity-camera-settings"></a>Unity 카메라 설정

**가상 현실을 지원 됨** 을 선택 하면 [Unity 카메라](camera-in-unity.md) 구성 요소가 [헤드 추적 및 stereoscopic 렌더링](../platform-capabilities-and-apis/rendering.md)을 처리 합니다. 즉, 기본 카메라 개체를 사용자 지정 카메라로 바꿀 필요가 없습니다.

앱이 특별히 HoloLens를 대상으로 하는 경우에는 장치의 투명 디스플레이를 최적화 하기 위해 몇 가지 설정을 변경 해야 합니다. 이러한 설정을 통해 holographic 콘텐츠를 실제 세계에 표시할 수 있습니다.

1. **계층** 에서 **기본 카메라** 를 선택 합니다.
2. **검사기** 패널에서 변환 **위치** 를 **0, 0, 0** 으로 설정 하 여 사용자의 헤드 위치가 Unity 세계 원점에서 시작 되도록 합니다.
3. **Clear 플래그** 를 **Solid 색** 으로 변경 합니다.
4. **배경색** 을 **RGBA 0, 0**, 0, 0으로 변경 합니다. 검은색은 HoloLens에서 투명 하 게 렌더링 됩니다.
5. **클립 평면** 을 [HoloLens 권장](camera-in-unity.md#clip-planes) 0.85 (미터) 근처로 변경 합니다.

![Unity 편집기에서 열리는 검사기 탭의 스크린샷](images/wmr-config-img-11.png)<br>
*Unity 카메라 설정*

> [!IMPORTANT]
> 새 카메라를 삭제 하 고 만드는 경우 새 카메라에 **maincamera** 로 태그가 지정 되어 있는지 확인 합니다.

## <a name="next-steps"></a>다음 단계

이제 프로젝트가 준비 되었으므로 혼합 현실 환경 개발을 시작할 수 있습니다.

* [핵심 구성 요소](unity-development-overview.md#2-core-building-blocks) 추가
* 사용 가능한 [플랫폼 기능 및 api](unity-development-overview.md#3-advanced-features) 확인
* [앱을 배포](../platform-capabilities-and-apis/using-visual-studio.md#) 하는 방법 알아보기
* [혼합 현실 시뮬레이터](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 사용

## <a name="see-also"></a>참고 항목
* [도구 설치](../install-the-tools.md)