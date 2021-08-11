---
title: Windows Mixed Reality용 2D UWP 앱 업데이트
description: 이 문서에서는 HoloLens 및 Windows Mixed Reality 모던 헤드셋에서 실행 되도록 기존 2d 유니버설 Windows 플랫폼 앱을 업데이트 하는 방법을 간략하게 설명 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2d 앱, UWP, 플랫 앱, HoloLens, 모던 헤드셋, 앱 모델, 뒤로 단추, 앱 바, dpi, 해상도, 크기 조정, 포팅 HoloLens 1 세대, HoloLens 2, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 마이그레이션, Windows 10
ms.openlocfilehash: 2b0fa403394432f2cec80e44d27804b07934260e60281f5c70b68c7377d3e55e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195992"
---
# <a name="updating-2d-uwp-apps-for-windows-mixed-reality"></a>Windows Mixed Reality용 2D UWP 앱 업데이트

Windows Mixed Reality를 통해 사용자는 실제 및 디지털 세계에서 holograms 하는 것 처럼 볼 수 있습니다. 핵심 HoloLens 및 몰입 형 헤드셋 액세서리를 연결 하는 데스크톱 pc는 Windows 10 장치입니다. 저장소에서 2d 앱으로 거의 모든 유니버설 Windows 플랫폼 (UWP) 앱을 실행할 수 있습니다.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>혼합 현실 용 2D UWP 앱 만들기

2D 앱을 혼합 현실 헤드셋으로 가져오는 첫 번째 단계는 사용자의 데스크톱 모니터에서 표준 2D 앱으로 앱을 실행 하는 것입니다.

### <a name="building-a-new-2d-uwp-app"></a>새 2D UWP 앱 빌드

혼합 현실 용 새 2d 앱을 빌드하려면 표준 UWP (2d 유니버설 Windows 플랫폼) 앱을 빌드합니다. 해당 앱에 대 한 다른 앱 변경은 필요 하지 않으므로 혼합 현실에서 슬레이트로 실행 됩니다.

2D UWP 앱 빌드를 시작 하려면 [첫 번째 앱 만들기](/windows/uwp/get-started/your-first-app) 문서를 확인 하세요.

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>기존 2D 스토어 앱을 UWP로 가져오기

저장소에 2d Windows 앱이 이미 있는 경우 UWP (Windows 10 유니버설 Windows 플랫폼)를 대상으로 하는지 확인 합니다. 현재 스토어 앱에서 발생할 수 있는 모든 잠재적인 시작 지점은 다음과 같습니다.
<br>

|  시작 지점  |  AppX 매니페스트 플랫폼 대상  |  이 유니버설를 만드는 방법 | 
|----------|----------|----------|
|  Windows Phone(Silverlight)  |  Silverlight 응용 프로그램 매니페스트 |  [WinRT로 마이그레이션](/previous-versions/windows/apps/dn642486(v=vs.105)) | 
|  Windows Phone 8.1 범용  |  8.1 플랫폼 대상을 포함 하지 않는 AppX 매니페스트  |  [앱을 유니버설 Windows 플랫폼로 마이그레이션](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows 매장 8  |  플랫폼 대상이 포함 되지 않은 8 개의 AppX 매니페스트  |  [앱을 유니버설 Windows 플랫폼로 마이그레이션](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows 매장 8.1 유니버설  |  8.1 플랫폼 대상을 포함 하지 않는 AppX 매니페스트  |  [앱을 유니버설 Windows 플랫폼로 마이그레이션](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 

현재 2d Unity 앱이 **PC, Mac & Linux 독립 실행형** 빌드 대상에서 Win32 앱으로 빌드된 경우 혼합 현실의 **유니버설 Windows 플랫폼** 빌드 대상으로 전환 합니다.

Windows를 사용 하 여 HoloLens 하도록 앱을 제한할 수 있는 방법에 대해 설명 합니다. Holographic [장치 제품군.](#publish-and-maintain-your-universal-app)

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Windows Mixed Reality 몰입 형 헤드셋에서 2d 앱 실행

데스크톱 컴퓨터에 2D 앱을 배포 하 고 모니터에서 사용해 본 적이 있다면 몰입 형 데스크톱 헤드셋에서 사용해 볼 준비가 된 것입니다.

mixed reality 헤드셋 내의 시작 메뉴로 이동 하 여 해당 위치에서 앱을 시작 하면 됩니다. Desktop shell과 holographic shell은 모두 동일한 UWP 앱 집합을 공유 하므로 Visual Studio에서 배포한 앱은 이미 존재 해야 합니다.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>모던 헤드셋 및 HoloLens 모두 대상 지정

축하합니다! 이제 앱이 UWP (Windows 10 유니버설 Windows 플랫폼)를 사용 하 고 있습니다.

이제 앱이 데스크톱, 모바일, Xbox, Windows Mixed Reality 모던 헤드셋, HoloLens 및 이후 Windows 장치와 같은 오늘날의 Windows 장치에서 실행할 수 있습니다. 그러나 실제로 이러한 모든 장치를 대상으로 하려면 앱이 Windows를 대상으로 하는지 확인 해야 합니다. 유니버설 장치 제품군.

### <a name="change-your-device-family-to-windowsuniversal"></a>장치 제품군을 Windows로 변경 합니다. 세계

이제 HoloLens에서 Windows 10 UWP 앱을 실행할 수 있도록 AppX 매니페스트로 이동 하겠습니다.
* **Visual Studio** 를 사용 하 여 앱의 솔루션 파일을 열고 앱 패키지 매니페스트로 이동 합니다.
* 솔루션의 appxmanifest.xml 파일을 마우스 오른쪽 단추로 클릭 하 고 **코드 보기** 로 이동 합니다 **.**<br>
  ![솔루션 탐색기의 appxmanifest.xml](images/openappxmanifest-500px.png)<br>
* 대상 플랫폼이 Windows 되는지 확인 합니다. 종속성 섹션의 Universal
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* Save!

개발 환경에 Visual Studio를 사용 하지 않는 경우 선택한 텍스트 편집기에서 **AppXManifest.xml** 를 열어 Windows를 대상으로 할 수 있습니다 **. 유니버설** *targetdevicefamily*.

### <a name="run-in-the-hololens-emulator"></a>HoloLens에서 실행 Emulator

이제 UWP 앱이 "Windows를 대상으로 합니다. 유니버설 "을 사용 하 여 앱을 빌드하고 [HoloLens Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md)에서 실행 합니다.
* [HoloLens Emulator를 설치](../install-the-tools.md)했는지 확인 합니다.
* Visual Studio에서 앱에 대 한 **x86** 빌드 구성을 선택 합니다.

  ![Visual Studio의 x86 빌드 구성](../platform-capabilities-and-apis/images/x86setting.png)<br>
* 배포 대상 드롭다운 메뉴에서 **HoloLens 에뮬레이터** 를 선택합니다.

  ![배포 대상 목록의 HoloLens Emulator](images/deployemulator-500px.png)<br>
* **디버그 > 디버깅 시작** 을 선택 하 여 앱을 배포 하 고 디버깅을 시작 합니다.
* 에뮬레이터가 시작 되 고 앱이 실행 됩니다.
* 키보드, 마우스 및 Xbox 컨트롤러를 사용 하 여 응용 프로그램을 시작할 수 있습니다.

  ![UWP 샘플로 로드 된 HoloLens Emulator](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>다음 단계

이 시점에서 다음 두 가지 중 하나가 발생할 수 있습니다.
1. 앱이 시작을 표시 하 고 Emulator에 배치 된 후 실행을 시작 합니다. 놀랍습니다.
2. 또는 2D 홀로그램에 대 한 로딩 애니메이션이 표시 되 면 로드는 중지 되 고 앱이 시작 화면에 표시 됩니다. 즉, 오류가 발생 하 여 혼합 현실에서 앱을 개발 하는 방법을 이해 하는 데 더 많은 조사가 필요 합니다.

HoloLens에서 UWP 앱을 중지 하는 가능한 문제를 해결 하기 위해 디버그 해야 합니다.

### <a name="running-your-uwp-app-in-the-debugger"></a>디버거에서 UWP 앱 실행

이러한 단계에서는 Visual Studio 디버거를 사용 하 여 UWP 앱을 디버깅 하는 과정을 안내 합니다.
* 아직 수행 하지 않은 경우 Visual Studio에서 솔루션을 엽니다. 대상을 **HoloLens Emulator** 변경 하 고 빌드 구성을 **x 86** 으로 변경 합니다.
* **디버그 > 디버깅 시작** 을 선택 하 여 앱을 배포 하 고 디버깅을 시작 합니다.
* 마우스, 키보드 또는 Xbox 컨트롤러를 사용 하 여 응용 프로그램을 전 세계에 두십시오.
* Visual Studio은 이제 앱 코드에서 중단 되어야 합니다.
  - 처리 되지 않은 오류로 인해 앱이 즉시 중단 되거나 중단 되지 않는 경우 앱의 핵심 기능에 대 한 테스트 통과를 통해 모든 것이 실행 중이 고 작동 하는지 확인 합니다. 아래 그림과 같은 오류가 표시 될 수 있습니다 (처리 중인 내부 예외). 앱 환경에 영향을 주는 내부 오류가 발생 하지 않도록 하려면 자동화 된 테스트 및 단위 테스트를 실행 하 여 모든 항목이 예상 대로 작동 하는지 확인 합니다.

![HoloLens 시스템 예외를 보여 주는 UWP 샘플로 로드 Emulator](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>UI 업데이트

이제 UWP 앱이 모던 헤드셋에서 실행 중이 고 2d 홀로그램로 HoloLens 되었습니다. 다음에는 멋진 것으로 확인 됩니다. 다음과 같은 몇 가지 사항을 고려해야 합니다.
* Windows Mixed Reality는 고정 해상도로 모든 2d 앱을 실행 하 고 853x480 유효 픽셀에 해당 하는 DPI를 적용 합니다. 설계가이 규모에서 구체화 되어야 하는 경우를 고려 하 여 HoloLens 및 몰입 (헤드셋)에서 환경을 개선 하려면 아래 디자인 지침을 검토 하세요.
* Windows Mixed Reality는 2d 라이브 타일을 [지원 하지 않습니다](../../design/app-model.md) . 핵심 기능에서 라이브 타일에 대 한 정보를 표시 하는 경우 해당 정보를 다시 앱으로 이동 하거나 [3d 앱 다운로드](../../distribute/3d-app-launcher-design-guidance.md)를 탐색 하는 것이 좋습니다.

### <a name="2d-app-view-resolution-and-scale-factor"></a>2D 앱 보기 해상도 및 배율 인수

![반응 형 디자인에서](images/scale-500px.png)

Windows 10는 모든 시각적 디자인을 실제 화면 픽셀에서 **유효 픽셀** 로 이동 합니다. 즉, 개발자는 효율적인 픽셀에 대 한 Windows 10 휴먼 인터페이스 지침에 따라 UI를 디자인 하 고, Windows 크기 조정을 사용 하면 장치, 해상도, DPI 등의 유용성에 대 한 효과적인 픽셀의 올바른 크기를 유지할 수 있습니다. 자세한 내용은 [MSDN의이 유용한](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design) 내용과이 [빌드 프레젠테이션](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx) 을 참조 하십시오.

다양 한 거리에서 전 세계에 앱을 제공 하는 고유한 기능을 사용 하는 경우에도 대화형/제스처를 사용 하 여 최상의 가독성을 얻을 수 있도록 TV와 유사한 거리를 표시 하는 것이 좋습니다. 이로 인해 Mixed Reality 홈의 가상 슬레이트는 다음 위치에 플랫 UWP 보기를 표시 합니다.

**1280x720, 150% DPI** (853x480 유효 픽셀)

이 해상도에는 다음과 같은 여러 가지 이점이 있습니다.
* 이 유효 픽셀 레이아웃은 태블릿 또는 소형 데스크톱과 동일한 정보 밀도를 가집니다.
* Xbox One에서 실행 되는 UWP 앱의 고정 DPI 및 유효 픽셀과 일치 하므로 장치 간에 원활한 환경을 사용할 수 있습니다.
* 이 크기는 전 세계의 앱에 대 한 운영 거리 범위에서 크기를 조정할 때 적절 하 게 보입니다.

### <a name="2d-app-view-interface-design-best-practices"></a>2D 앱 보기 인터페이스 디자인 모범 사례

**다음을 수행합니다.**
* 스타일, 글꼴 크기 및 단추 크기에 대한 [Windows 10 HIG(휴먼 인터페이스 지침)를](https://dev.windows.com/design) 따릅니다. HoloLens 앱이 호환되는 앱 패턴, 읽을 수 있는 텍스트 크기 및 적절한 적중 대상 크기 조정을 갖도록 하는 작업을 수행합니다.
* UI가 [반응형 디자인에](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design) 대한 모범 사례를 따라 HoloLens 고유 해상도 및 DPI를 가장 잘 살펴보도록 합니다.
* Windows "밝은" 색 테마 권장 사항을 사용합니다.

**안 함:**
* 혼합 현실에서 UI를 너무 크게 변경하여 사용자가 헤드셋 안팎에서 친숙한 경험을 갖도록 합니다.

### <a name="understand-the-app-model"></a>앱 모델 이해

혼합 현실용 앱 모델은 많은 [앱이](../../design/app-model.md) 함께 있는 Mixed Reality Home을 사용하도록 설계되었습니다. 이를 한 번에 여러 2D 앱을 실행하는 데스크톱과 동등한 혼합 현실이라고 생각하면 됩니다. 이는 앱 수명 주기, 타일 및 앱의 기타 주요 기능에 영향을 줍니다.

### <a name="app-bar-and-back-button"></a>앱 바 및 뒤로 단추

2D 보기는 콘텐츠 위에 앱 바로 데코레이트됩니다. 앱 바에는 앱별 개인화의 두 가지 지점이 있습니다.

**제목:** 앱 인스턴스와 연결된 타일의 *표시 이름을 표시합니다.*

**뒤로 단추:** 누를 때 *[BackRequested](/uwp/api/Windows.UI.Core.SystemNavigationManager)* 이벤트를 발생합니다. 뒤로 단추 표시 유형은 *[SystemNavigationManager.AppViewBackButtonVisibility](/uwp/api/Windows.UI.Core.SystemNavigationManager)* 에 의해 제어됩니다.

![2D 앱 보기의 앱 바 UI](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*2D 앱 보기의 앱 바 UI*

### <a name="test-your-2d-apps-design"></a>2D 앱 디자인 테스트

앱을 테스트하여 텍스트를 읽을 수 있고, 단추를 대상으로 지정하고, 전체 앱이 올바르게 보이는지 확인하는 것이 중요합니다. 해상도가 1280x720%로 설정된 데스크톱 헤드셋, HoloLens, 에뮬레이터 또는 터치 디바이스에서 [테스트할](../platform-capabilities-and-apis/testing-your-app-on-hololens.md) 수 @150 있습니다.

## <a name="new-input-possibilities"></a>새로운 입력 가능성

HoloLens 고급 깊이 센서를 사용하여 세계를 보고 사용자를 확인합니다. 이를 통해 [꽃](../../design/system-gesture.md#bloom) 및 에어 [탭](../../design/gaze-and-commit.md#composite-gestures)과 같은 고급 손 제스처를 사용할 수 있습니다. 강력한 마이크를 사용하면 음성 환경도 사용할 [수 있습니다.](../../design/voice-input.md)

데스크톱 헤드셋을 사용하면 사용자가 모션 컨트롤러를 사용하여 앱을 가리키고 조치를 취할 수 있습니다. 또한 응시로 개체를 대상으로 하는 게임 패드를 사용할 수도 있습니다.

Windows UWP 앱의 이러한 모든 복잡성을 처리하여 [응시,](../../design/gaze-and-commit.md)제스처, 음성 및 모션 컨트롤러 입력을 입력 메커니즘을 추상화한 [포인터 이벤트로](/windows/uwp/design/input/handle-pointer-input#pointer_events) 변환합니다. 예를 들어 사용자가 손으로 에어 탭을 수행하거나 모션 컨트롤러에서 Select 트리거를 가져왔을 수 있지만, 2D 애플리케이션은 입력의 위치를 알 필요가 없습니다. 터치 스크린에서처럼 2D 터치 누를 볼 수 있습니다.

UWP 앱을 HoloLens 가져올 때 입력에 대해 이해해야 하는 높은 수준의 개념/시나리오는 다음과 같습니다.
* [응시는](../../design/gaze-and-commit.md) 마우스로 가리키기 이벤트로 바뀌며, 예기치 않게 메뉴, 플라이아웃 또는 기타 사용자 인터페이스 요소를 트리거하여 앱을 둘러볼 때 팝업할 수 있습니다.
* 응시는 마우스 입력만큼 정확하지 않습니다. 터치 친화적인 모바일 애플리케이션과 비슷하게 HoloLens 적절한 크기의 적중 대상을 사용합니다. 앱의 가장자리 근처에 있는 작은 요소는 상호 작용하기 특히 어렵습니다.
* 스크롤에서 두 손가락 이동으로 이동하려면 사용자가 입력 모드를 전환해야 합니다. 앱이 터치 입력용으로 설계된 경우 두 손가락 이동 뒤에 주요 기능이 잠겨 있지 않은지 확인하는 것이 좋습니다. 그렇다면 두 손가락으로 이동이 시작될 수 있는 단추와 같은 대체 입력 메커니즘이 있는 것이 좋습니다. 예를 들어 지도 앱은 두 손가락으로 이동하면서 확대/축소할 수 있지만 더하기, 빼기 및 회전 단추를 사용하여 한 번의 클릭으로 동일한 확대/축소 상호 작용을 시뮬레이션할 수 있습니다.

[음성 입력은](../../design/voice-input.md) 혼합 현실 환경의 중요한 부분입니다. 헤드셋을 사용할 때 Windows 10 전원 Cortana 있는 모든 음성 API를 사용하도록 설정했습니다.

## <a name="publish-and-maintain-your-universal-app"></a>유니버설 앱 게시 및 유지 관리

앱이 실행되면 Microsoft Store [제출하도록](../../distribute/submitting-an-app-to-the-microsoft-store.md)앱을 패키지합니다.

## <a name="see-also"></a>추가 정보
* [앱 모델](../../design/app-model.md)
* [헤드 게이즈 및 커밋](../../design/gaze-and-commit.md)
* [모션 컨트롤러](../../design/motion-controllers.md)
* [음성 입력 ](../../design/voice-input.md)
* [Microsoft Store에 앱 제출](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [HoloLens 에뮬레이터 사용](../platform-capabilities-and-apis/using-the-hololens-emulator.md)