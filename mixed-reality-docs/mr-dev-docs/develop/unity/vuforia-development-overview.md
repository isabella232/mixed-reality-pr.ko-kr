---
title: Unity에서 Vuforia 사용
description: Vuforia를 사용하여 Unity에서 Windows Mixed Reality 애플리케이션을 빌드합니다.
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia, 표식, 좌표, 참조 프레임, 추적, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity, HoloLens, 디바이스 추적, 성능 모드, Vuforia 개발자 포털
ms.openlocfilehash: 1a21f4bb441a1ab0706b5916feaac0d691486626
ms.sourcegitcommit: 7160843723ccd6567490e2f4222219603f184d76
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232173"
---
# <a name="using-vuforia-engine-with-unity"></a>Unity에서 Vuforia 엔진 사용

Vuforia 엔진은 환경의 특정 이미지 및 개체에 AR 환경을 연결하는 기능인 HoloLens 중요한 기능을 제공합니다. 이 기능을 사용하여 산업 기업용 기계에 단계별 지침을 오버레이하거나 물리적 제품 또는 게임에 디지털 기능과 환경을 추가할 수 있습니다.

Vuforia 엔진은 AR 개발 프로세스를 보다 유연하게 만들 수 있는 광범위한 기능과 대상을 제공합니다. 최신 기능 중 하나인 Vuforia Model Targets는 상용 및 산업용 모두에 대한 주요 기능입니다. 모델 대상을 사용하면 애플리케이션이 컴퓨터, 자동차 또는 장난감과 같은 물리적 개체를 인식하고 CAD 또는 디지털 3D 모델을 기반으로 추적할 수 있습니다. 산업용으로 사용되는 경우 이 기능은 공장 또는 필드에 있는 동안 어셈블리 작업자 및 서비스 기술자에게 AR 작업 지침 및 절차 지침을 제공할 수 있습니다.

휴대폰 및 태블릿용으로 빌드된 기존 Vuforia 엔진 앱은 Unity에서 HoloLens 실행되도록 쉽게 구성할 수 있습니다. Vuforia 엔진을 사용하여 새 HoloLens 앱을 Surface Pro 및 Surface Book 같은 태블릿에 Windows 10 수도 있습니다.


## <a name="get-the-tools"></a>도구 얻기

권장 버전의 Visual Studio 및 Unity를 [설치한](../install-the-tools.md) 다음 Visual Studio 및 기본 설정 IDE 및 컴파일러를 사용하도록 Unity를 구성합니다. 

Unity를 설치할 때는 "Windows Store IL2CPP 스크립팅 백 엔드"를 설치해야 합니다.

여기에 설명된 대로 Vuforia 엔진 패키지를 [추가합니다.](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)

## <a name="getting-started-with-vuforia-engine"></a>Vuforia 엔진 시작

Vuforia 엔진 및 HoloLens 대한 학습을 위한 가장 좋은 시작점은 [Vuforia 엔진 HoloLens 샘플(Unity](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) 자산 저장소에서 사용 가능)입니다. 샘플은 HoloLens 배포할 수 있는 미리 구성된 장면을 포함하여 전체 HoloLens 프로젝트를 제공합니다.

이 장면에서는 Vuforia Image Targets를 사용하여 이미지를 인식하고 HoloLens 환경의 디지털 콘텐츠로 확대하는 방법을 보여줍니다. Vuforia 엔진 HoloLens 샘플에는 HoloLens 모델 대상 및 VuMarks의 사용을 보여주는 장면도 포함되어 있습니다. 장면에서 사용자 고유의 콘텐츠를 쉽게 대체하여 Vuforia 엔진을 사용하는 HoloLens 앱 만들기를 실험할 수 있습니다.



## <a name="configuring-a-vuforia-app-for-hololens"></a>HoloLens 대한 Vuforia 앱 구성

HoloLens Vuforia 엔진 앱을 개발하는 것은 다른 디바이스용 Vuforia 엔진 앱을 개발하는 것과 근본적으로 동일합니다. 그런 다음, 아래 섹션에 설명된 빌드 설정 및 구성을 적용할 수 있습니다. Vuforia 엔진이 HoloLens 공간 매핑 및 위치 추적 시스템을 사용할 수 있도록 하는 데 필요합니다.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>HoloLens 대한 Vuforia 엔진 샘플 빌드 및 실행
1.  Unity 자산 저장소에서 [HoloLens Vuforia 엔진 샘플](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) 다운로드
2.  전원 [및 성능에 권장되는 Unity 엔진 옵션](performance-recommendations-for-unity.md) 적용
3.  빌드의 **장면에** 샘플 장면을 **추가합니다.**
4.  **빌드 설정** 열려 있는 **장면 추가** 단추를 클릭하여 빌드 플랫폼을 **UWP로** 전환합니다.
![image](https://user-images.githubusercontent.com/45470042/89573103-173daa80-d7f8-11ea-9284-931a7b6c913d.png)
5.  플레이어 **설정** 단추를 선택합니다.  
   * **UWP** 아이콘을 선택하고 **XR 설정** 섹션을 확장합니다.
   * Virtual **Reality Supported가** 사용하도록 설정되어 있는지 확인합니다.    
   * **Virtual Reality SDK에서 다음을 확인합니다.**
     * **창 Mixed Reality** 목록에 포함되며 깊이 **버퍼** 공유 사용이 사용하도록 설정됩니다. 
     * **깊이 형식은** **16비트 깊이로 설정됩니다.** 
   * **스테레오 렌더링 모드가** **단일 패스 인스턴스화로** 설정되어 있는지 확인합니다.
6.  게시 **설정** 섹션을 확장합니다.
   * **기능에서** Internet **Client, WebCam, Microphone** 및 **SpatialPerception이** 선택되어 있는지 확인합니다.
   * 참고: Surface Observer API를 사용하려는 경우에만 **SpatialPerception을** 선택해야 합니다.
   * **지원되는 디바이스 패밀리 아래에서** **홀로그램이** 선택되어 있는지 확인합니다. 
7.  해상도 **및 프레젠테이션 섹션을** 확장합니다.
   * **백그라운드에서 실행을** 사용하지 않도록 설정하면 앱이 백그라운드에 배치되면 Vuforia 엔진이 일시 중지되고 앱이 다시 시작되면 카메라에 다시 액세스할 수 있습니다. 
   * 기본 **방향** 드롭다운에서 **왼쪽 가로가** 선택되어 있는지 확인합니다.
8.  **빌드 설정** 창으로 **돌아가서 빌드를** 선택하여 Visual Studio 프로젝트를 생성합니다.
9.  Visual Studio 실행 파일을 빌드하고 HoloLens 설치합니다.

## <a name="the-vuforia-developer-portal"></a>Vuforia 개발자 포털

Vuforia 엔진 및 HoloLens 사용하여 자체 AR 환경을 만들려는 개발자는 developer.vuforia.com 에서 Vuforia 개발자 포털 등록해야 [합니다.](https://developer.vuforia.com/) 포털에서 개발자는 커뮤니티 토론에 참여할 수 있는 [Vuforia 엔진 포럼, 모든 Vuforia 엔진](https://developer.vuforia.com/forum) 기능에 대한 심층 설명서가 포함된 [라이브러리](https://library.vuforia.com/) 및 사용자가 고유한 사용자 지정 대상을 만들 수 있는 [Vuforia 대상 관리자에](https://developer.vuforia.com/target-manager) 액세스할 수 있습니다. 개발자는 [Vuforia](https://developer.vuforia.com/license-manager)라이선스 관리자 를 사용하여 무료 개발자 라이선스에 등록할 수도 있습니다.

## <a name="device-tracking-with-vuforia"></a>Vuforia를 통해 디바이스 추적

[디바이스 추적은](https://library.vuforia.com/features/environments/device-tracker-overview.html) 대상이 더 이상 보이지 않는 경우에도 추적을 유지 관리합니다. 위치 디바이스 추적기를 사용하도록 설정하면 모든 대상에 대해 자동으로 사용하도록 설정됩니다. HoloLens 애플리케이션의 경우 위치 디바이스 추적기가 Unity에서 자동으로 시작됩니다.

Vuforia 엔진은 카메라 추적 및 HoloLens 공간 추적에서의 자세를 자동으로 동기화하여 대상이 카메라에서 보이는지 여부에 관계없이 안정적인 대상 자세를 제공합니다.

프로세스가 자동으로 처리되므로 개발자가 프로그래밍할 필요가 없습니다.


**다음은 프로세스에 대한 높은 수준의 설명입니다.**
1. Vuforia의 대상 추적기가 대상을 인식합니다.
2. 그런 다음 대상 추적이 초기화됩니다.
3. 대상의 위치 및 회전을 분석하여 HoloLens 대한 강력한 자세 예상치를 제공합니다.
4. Vuforia 엔진은 대상의 자세를 HoloLens 공간 매핑 좌표 공간으로 변환합니다.
5. HoloLens 대상이 더 이상 보기에 없는 경우 추적을 인수합니다. 대상을 다시 볼 때마다 Vuforia는 계속해서 이미지와 개체를 정확하게 추적합니다.

검색되었지만 더 이상 보기에 없는 대상은 EXTENDED_TRACKED 보고됩니다. 이러한 경우 모든 대상에서 사용되는 DefaultTrackableEventHandler 스크립트는 계속 보강 콘텐츠를 렌더링합니다. 개발자는 사용자 지정 추적 가능한 이벤트 처리기 스크립트를 구현하여 이 동작을 제어할 수 있습니다.

## <a name="performance-mode-with-vuforia-engine"></a>Vuforia 엔진을 통해 성능 모드 

Vuforia 엔진을 통해 AR 환경을 익스텐트하고 CPU의 워크로드를 줄이기 위해 HoloLens 성능을 관리할 수 있습니다. Vuforia 엔진은 선택할 수 있는 세 가지 모드인 기본값, 속도 최적화 및 품질 최적화를 제공합니다. 

*   MODE_OPTIMIZE_SPEED 사용하면 HoloLens 디바이스에서 워크로드를 최소화할 수 있으며 AR 환경을 확장하는 데 적합합니다. 앱이 정적 개체/대상을 추적하는 상황에 권장됩니다.
*   MODE_DEFAULT 대부분의 시나리오에서 사용할 수 있는 표준 모드입니다.
*   MODE_OPTIMIZE_QUALITY 선택할 것으로 예상되는 이동 가능한 대상 또는 모델 대상을 추적하는 데 더 좋습니다.

**모드 설정**

Unity에서 성능 모드를 변경하려면 ARCamera GameObject의 구성 요소로 있는 Vuforia 구성(Ctrl+Shift+V/ Cmd+Shift+V)으로 이동합니다. 
*   카메라 디바이스 모드에 대한 드롭다운 메뉴를 선택하고 세 가지 옵션 중 하나를 선택합니다.


## <a name="see-also"></a>참고 항목
* [도구 설치](../install-the-tools.md)
* [좌표계](../../design/coordinate-systems.md)
* [공간 매핑](../../design/spatial-mapping.md)
* [Unity의 카메라](camera-in-unity.md)
* [Unity Visual Studio 솔루션 내보내기 및 빌드](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia 설명서: Windows 10 개발을 위해 Vuforia 엔진과 시작](https://library.vuforia.com/articles/Training/Getting-Started-with-Vuforia-for-Windows-10-Development.html)
* [Vuforia 설명서: Unity에서 Vuforia 엔진을 시작](https://library.vuforia.com/articles/Training/getting-started-with-vuforia-in-unity.html)
* [Vuforia 설명서: Unity에서 HoloLens 샘플 작업](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity.html)
* [Vuforia 설명서: Vuforia의 디바이스 추적](https://library.vuforia.com/features/environments/device-tracker-overview.html)
* [Vuforia 설명서: 프레임 속도 및 성능 최적화](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/Framerate-Optimization-for-Mixed-Reality-Apps.html)
