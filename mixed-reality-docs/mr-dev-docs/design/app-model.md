---
title: 앱 모델
description: Windows Mixed Reality는 최신 Windows 앱에 대 한 유니버설 Windows 플랫폼, 모델 및 환경에서 제공 하는 앱 모델을 사용 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, 앱 모델, 수명 주기, 일시 중단, 다시 시작, 타일, 보기, 계약, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, mrtk, 혼합 현실 Toolkit
ms.openlocfilehash: 5f15f0a2516a21cd6432e7f09df7950f8d832acc77ac77056f5bf1382500024e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221939"
---
# <a name="app-model"></a>앱 모델

Windows Mixed Reality은 최신 Windows 앱에 대 한 모델 및 환경인 UWP ( [유니버설 Windows 플랫폼](/windows/uwp/get-started/) )에서 제공 하는 앱 모델을 사용 합니다. UWP 앱 모델은 앱을 안전 하 게 설치, 업데이트, 버전 관리 및 제거 하는 방법을 정의 합니다. 또한 응용 프로그램 수명 주기를 제어 합니다. 앱이 실행 되는 방법, 절전 모드 및 중지 방법 및 상태를 유지할 수 있는 방법을 제어 합니다. 마지막으로, 앱 모델은 운영 체제, 파일 및 기타 앱과의 통합 및 상호 작용을 다룹니다.

![breakfast 영역에서 Windows Mixed Reality 홈으로 정렬 된 2d 앱](images/20160112-055908-hololens-500px.jpg)<br>
*Windows Mixed Reality 홈에 2d 보기가 정렬 된 앱*

## <a name="app-lifecycle"></a>앱 수명 주기

혼합 현실 앱의 수명 주기는 배치, 시작, 종료 및 제거와 같은 표준 앱 개념을 포함 합니다.

### <a name="placement-is-launch"></a>배치가 시작 됩니다.

모든 앱은 [Windows Mixed Reality 홈](../discover/navigating-the-windows-mixed-reality-home.md)에 앱 타일 ( [Windows 보조 타일](/uwp/api/Windows.UI.StartScreen.SecondaryTile)만)을 배치 하 여 혼합 현실에서 시작 됩니다. 배치 시 이러한 앱 타일은 앱 실행을 시작 합니다. 이러한 앱 타일은 배치 된 위치에 유지 되며, 언제 든 지 응용 프로그램으로 다시 전환 하려는 경우에도 시작 합니다.

![배치가 보조 타일을 세계에 배치 합니다.](images/slide1-600px.png)<br>
*배치가 보조 타일을 세계에 배치 합니다.*

배치가 완료 되는 즉시 (앱에서 [앱 시작으로](app-model.md#protocols) 배치를 시작 하지 않은 경우) 앱이 시작 되기 시작 합니다. Windows Mixed Reality은 한 번에 제한 된 수의 앱을 실행할 수 있습니다. 앱을 시작 하 고 시작 하는 즉시 다른 활성 앱이 일시 중단 될 수 있습니다. 일시 중단 된 앱은 앱의 마지막 상태를 앱 타일에 배치 하는 위치에 따라 그대로 둡니다. resume 및 기타 수명 주기 이벤트를 처리 하는 방법에 대 한 자세한 내용은 [Windows 10 UWP 앱 수명 주기](/windows/uwp/launch-resume/app-lifecycle)를 참조 하세요.

![타일을 배치한 후 응용 프로그램 실행 중 ](images/slide2-500px.png) ![ , 일시 중지 됨 또는 실행 중이 아닌 앱에 대 한 상태 다이어그램 실행이 시작 됩니다.](images/ic576232-500px.png)<br>
*Left: 타일을 배치 하면 앱이 실행 되기 시작 합니다. Right: 실행 중, 일시 중단 됨 또는 실행 중이 아닌 앱에 대 한 상태 다이어그램입니다.*

### <a name="remove-is-closeterminate-process"></a>닫기/종료 프로세스 제거

전 세계에서 배치 된 앱 타일을 제거 하면 기본 프로세스가 닫힙니다. 이는 앱이 중지 되거나 문제가 있는 앱을 다시 시작 하는 데 유용할 수 있습니다.

### <a name="app-suspensiontermination"></a>앱 일시 중단/종료

[Windows Mixed Reality 홈](../discover/navigating-the-windows-mixed-reality-home.md)에서 사용자는 시작 메뉴에서 앱을 시작 하 고 전 세계에 앱 타일을 배치 하 여 앱에 대 한 진입점을 여러 개 만들 수 있습니다. 각 앱 타일은 다른 진입점으로 작동 하며 시스템에 별도의 타일 인스턴스가 있습니다. [FindAllAsync](/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) 에 대 한 쿼리는 각 응용 프로그램 인스턴스에 대해 **secondarytile** 발생 합니다.

UWP 앱이 일시 중단 되 면 현재 상태의 스크린샷이 사용 됩니다.

![일시 중단 된 앱에 대 한 스크린샷 표시](images/slide9-800px.png)<br>
*일시 중단 된 앱에 대 한 스크린샷 표시*

다른 Windows 10 셸에서의 한 가지 주요 차이점은 [CoreApplication](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) 및 [CoreWindow](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) 이벤트를 통해 앱이 앱 인스턴스 활성화를 알리는 방법입니다.

|  시나리오 |  Resuming  |  활성화됨 | 
|----------|----------|----------|
|  시작 메뉴에서 앱의 새 인스턴스를 시작 합니다.  |   |  새 [TileId](/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) 으로 **활성화** 됨 | 
|  시작 메뉴에서 앱의 두 번째 인스턴스를 시작 합니다.  |   |  새 **TileId** 으로 **활성화** 됨 | 
|  현재 활성 상태가 아닌 앱 인스턴스를 선택 합니다.  |   |  인스턴스와 연결 된 **TileId** 를 사용 하 여 **활성화** 됨 | 
|  다른 앱을 선택한 다음 이전에 활성화 된 인스턴스를 선택 합니다.  |  발생 한 다시 **시작**  |  | 
|  다른 앱을 선택한 다음 이전에 비활성화 된 인스턴스를 선택 합니다.  |  발생 한 다시 **시작**  |  그러면 인스턴스와 연결 된 **TileId** 를 사용 하 여 **활성화** 됩니다. | 

### <a name="extended-execution"></a>확장 된 실행

앱이 백그라운드에서 작업을 계속 하거나 오디오를 재생 해야 하는 경우도 있습니다. [백그라운드 작업](/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) 은 HoloLens에서 사용할 수 있습니다.

![앱이 백그라운드에서 실행 될 수 있습니다.](images/slide10-800px.png)<br>
*앱이 백그라운드에서 실행 될 수 있습니다.*

## <a name="app-views"></a>앱 보기

앱이 활성화 되 면 표시할 보기 유형을 선택할 수 있습니다. 앱의 **CoreApplication** 에는 항상 기본 [앱 보기](/uwp/api/Windows.UI.ViewManagement.ApplicationView) 와 만들려는 앱 보기 수가 있습니다. 바탕 화면에서 앱 보기를 창으로 간주할 수 있습니다. 혼합 현실 앱 템플릿은 기본 앱 뷰가 [몰입](app-views.md)인 Unity 프로젝트를 만듭니다. 

앱은 XAML과 같은 기술을 사용 하 여 추가 2d 앱 보기를 만들어 앱에서의 구매와 같은 Windows 10 기능을 사용할 수 있습니다. 앱이 다른 Windows 10 장치에 대 한 UWP 앱으로 시작 된 경우 기본 보기는 2d입니다. 그러나 volumetrically 환경을 보여 줄 수 있는 다른 앱 보기를 추가 하 여 혼합 현실에서 "강화" 할 수 있습니다. 전 세계 및 표면에서 앱의 사진을 flew는 슬라이드 쇼 단추가 몰입 형 앱 보기로 전환 된 XAML로 사진 뷰어 앱을 빌드하는 Imagine 합니다.

![실행 중인 앱에는 2D 뷰 또는 몰입 형 보기가 있을 수 있습니다.](images/slide3-800px.png)<br>
*실행 중인 앱에는 2D 뷰 또는 몰입 형 보기가 있을 수 있습니다.*

### <a name="creating-an-immersive-view"></a>몰입 형 보기 만들기

혼합 현실 앱은 [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace) 유형을 사용 하 여 얻을 수 있는 몰입 형 보기를 만듭니다.

순수 하 게 몰입 형 응용 프로그램은 데스크톱에서 시작 된 경우에도 항상 몰입 형 보기를 만들어야 합니다. 몰입 형 보기는 생성 된 위치에 관계 없이 항상 헤드셋에 표시 됩니다. 몰입 형 보기를 활성화 하면 혼합 현실 포털이 표시 되 고 사용자가 헤드셋에 넣을 수 있는 지침이 표시 됩니다.

데스크톱 모니터에서 2D 보기로 시작 하는 앱은 헤드셋에서 콘텐츠를 표시 하는 보조 몰입 형 보기를 만들 수 있습니다. 이에 대 한 예는 헤드셋에서 360도 비디오를 표시 하는 모니터의 2D 가장자리 창입니다.

![몰입 형 보기에서 실행 되는 앱은 하나만 표시 됩니다.](images/slide4-800px.png)<br>
*몰입 형 보기에서 실행 되는 앱은 하나만 표시 됩니다.*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality 홈의 2d 보기

몰입 형 보기 이외의 모든 항목은 전 세계에서 2D 보기로 렌더링 됩니다.

앱에는 데스크톱 모니터와 헤드셋 모두에 2D 보기가 있을 수 있습니다. 새 2D 보기는 모니터 또는 헤드셋에서이를 만든 뷰와 동일한 셸에 배치 됩니다. 현재는 앱 또는 사용자가 혼합 현실 홈 및 모니터 간에 2D 보기를 이동할 수 없습니다.

![2D 보기에서 실행 되는 앱은 혼합 된 세계의 공간을 다른 앱과 공유 합니다.](images/slide5-800px.png)<br>
*2D 뷰에서 실행 되는 앱은 다른 앱과 공간을 공유 합니다.*

### <a name="placement-of-additional-app-tiles"></a>추가 앱 타일 배치

[보조 타일 api](/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles)를 사용 하 여 전 세계에 2d 보기로 많은 앱을 추가할 수 있습니다. 이러한 "고정 된" 타일은 사용자가 입력 해야 하는 시작 화면으로 표시 되며 나중에 앱을 시작 하는 데 사용할 수 있습니다. Windows Mixed Reality 현재 라이브 타일로 2d 타일 콘텐츠를 렌더링 하는 것을 지원 하지 않습니다.

![앱은 보조 타일을 사용 하 여 여러 위치에 있을 수 있습니다.](images/slide6-800px.png)<br>
*앱은 보조 타일을 사용 하 여 여러 위치에 있을 수 있습니다.*

### <a name="switching-views"></a>뷰 전환

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>2D XAML 뷰에서 몰입 형 뷰로 전환

앱이 XAML을 사용 하는 경우 XAML [IFrameworkViewSource](/uwp/api/windows.applicationmodel.core.iframeworkviewsource) 는 응용 프로그램의 첫 번째 뷰를 제어 합니다. 앱이 몰입 형 환경으로 직접 시작 되도록 하려면 **CoreWindow** 을 활성화 하기 전에 앱이 몰입 형 보기로 전환 되어야 합니다.

[CreateNewView 및](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) [applicationviewswitcher](/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) 를 사용 하 여 활성 뷰로 만듭니다.

> [!NOTE]
>* XAML 뷰에서 몰입 형 뷰로 전환 하거나 앱을 시작한 슬레이트가 전 세계에서 제거 될 때 [Applicationviewswitchingoptions](/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) 플래그를 **switchasync** 로 지정 하지 마세요.
>* 전환 하려는 뷰와 연결 된 [디스패처](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) 를 사용 하 여 **switchasync** 를 호출 해야 합니다.
>* 가상 키보드를 시작 하거나 다른 앱을 활성화 해야 하는 경우 XAML 뷰로 다시 **async** 를 전환 해야 합니다.

![앱이 몰입 형 보기로 전환 될 때 2D 보기와 몰입 형 보기 간에 전환할 수 있습니다. ](images/slide7-600px.png) ![ 혼합 된 세계와 기타 앱은 사라집니다.](images/slide8-600px.png)<br>
*Left: 앱이 2D 보기와 몰입 형 보기 간에 전환할 수 있습니다. 오른쪽: 앱이 몰입 형 보기로 들어가면 Windows Mixed Reality 홈 및 기타 앱이 사라집니다.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>몰입 형 뷰에서 다시 키보드 XAML 뷰로 전환

보기 간에 앞뒤로 전환 하는 한 가지 일반적인 이유는 혼합 현실 앱에서 키보드를 표시 하는 것입니다. 앱이 2D 보기를 표시하는 경우에만 셸에서 시스템 키보드를 표시할 수 있습니다. 앱에서 텍스트 입력을 받아야 하는 경우 텍스트 입력 필드가 있는 사용자 지정 XAML 보기를 제공하고, 해당 필드로 전환한 다음, 입력이 완료된 후 다시 전환할 수 있습니다.

이전 섹션과 마찬가지로 **ApplicationViewSwitcher.SwitchAsync를** 사용하여 몰입형 보기에서 XAML 보기로 다시 전환할 수 있습니다.

## <a name="app-size"></a>앱 크기

2D 앱 보기는 항상 고정 가상 슬레이트에 표시됩니다. 이렇게 하면 모든 2D 보기에 정확히 동일한 양의 콘텐츠가 표시됩니다. 앱의 2D 보기 크기에 대한 자세한 내용은 다음과 같습니다.
* 크기를 조정하는 동안 앱의 가로 세로 비율이 유지됩니다.
* 앱 [해상도 및 배율 비율은](../develop/porting-apps/building-2d-apps.md#2d-app-view-resolution-and-scale-factor) 크기 조정에 의해 변경되지 않습니다.
* 앱은 전 세계에서 실제 크기를 쿼리할 수 없습니다.

![2D 앱이 고정 창 크기로 표시됨](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*2D 보기가 있는 앱은 고정 창 크기로 표시됩니다.*

## <a name="app-tiles"></a>앱 타일

시작 메뉴 핀에 표준 소형 타일 및 중간 타일을 사용하고 혼합 현실의 **모든 앱** 목록을 사용합니다. 

![Windows Mixed Reality 대한 시작 메뉴](images/start-500px.png)<br>
*Windows Mixed Reality 대한 시작 메뉴*

## <a name="app-to-app-interactions"></a>앱 간 상호 작용

앱을 빌드할 때 Windows 10 사용할 수 있는 풍부한 앱 간 통신 메커니즘에 액세스할 수 있습니다. 대부분의 새로운 프로토콜 API 및 파일 등록은 앱 시작 및 통신을 가능하게 하는 HoloLens 완벽하게 작동합니다. 

데스크톱 헤드셋의 경우 지정된 파일 확장명 또는 프로토콜과 연결된 앱은 데스크톱 모니터 또는 데스크톱 슬레이트에만 나타날 수 있는 Win32 앱일 수 있습니다.

### <a name="protocols"></a>프로토콜

HoloLens [Windows.System.시작 관리자 API를](/uwp/api/Windows.System.Launcher)통해 앱 시작 앱을 지원합니다.

다른 애플리케이션을 시작할 때 고려해야 할 몇 가지 사항이 있습니다.

* [LaunchUriAsync와](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)같은 비모달 시작 작업을 수행하는 경우 사용자는 상호 작용하기 전에 앱을 배치해야 합니다.

* [LaunchUriForResultsAsync를](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_)통해 모달을 시작하는 경우와 같이 모달 앱이 창 위에 배치됩니다.

* Windows Mixed Reality 배타적 보기 위에 애플리케이션을 오버레이할 수 없습니다. 시작된 앱을 표시하기 위해 Windows 사용자를 전 세계로 돌아가 애플리케이션을 표시합니다.

### <a name="file-pickers"></a>파일 선택기

HoloLens [FileOpenPicker](/uwp/api/Windows.Storage.Pickers.FileOpenPicker) 및 [FileSavePicker](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 계약을 모두 지원합니다. 그러나 파일 선택기 계약을 충족하는 앱이 미리 설치되어 있지 않습니다. 이러한 앱(예: OneDrive)은 Microsoft Store 설치할 수 있습니다.

파일 선택기 앱이 두 개 이상 설치된 경우 시작할 앱을 선택하기 위한 명확한 UI가 표시되지 않습니다. 대신 설치된 첫 번째 파일 선택기가 선택됩니다. 파일을 저장할 때 타임스탬프를 포함하는 파일 이름이 생성됩니다. 이 이미지는 사용자가 변경할 수 없습니다.

기본적으로 다음 확장은 로컬에서 지원됩니다.

|  앱  |  확장 | 
|----------|----------|
|  사진  |  bmp, gif, jpg, png, avi, mov, mp4, wmv | 
|  Microsoft Edge  |  htm, html, pdf, svg, xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>앱 계약 및 Windows Mixed Reality 확장

앱 계약 및 확장 지점을 사용하면 파일 확장명 처리 또는 백그라운드 작업 사용과 같은 보다 심층적인 운영 체제 기능을 활용하도록 앱을 등록할 수 있습니다. HoloLens 지원되는 계약 및 지원되지 않는 계약 및 확장 지점의 목록입니다.

|  계약 또는 확장  |  지원 여부 | 
|----------|----------|
| [계정 그림 공급자(확장)](/previous-versions/windows/apps/hh464906(v=win.10)#account_picture_provider) | 지원되지 않음 | 
| [경보](/previous-versions/windows/apps/hh464906(v=win.10)#alarm) | 지원되지 않음 | 
| [App service](/previous-versions/windows/apps/hh464906(v=win.10)#app_service) | 지원되지만 완벽하게 작동하지 않음 | 
| [약속 공급자](/previous-versions/windows/apps/hh464906(v=win.10)#appointmnets_provider) | 지원되지 않음 | 
| [AutoPlay(확장)](/previous-versions/windows/apps/hh464906(v=win.10)#autoplay) | 지원되지 않음 | 
| [백그라운드 작업(확장)](/previous-versions/windows/apps/hh464906(v=win.10)#background_tasts) | 부분적으로 지원됨(일부 트리거가 작동하지 않음) | 
| [업데이트 작업(확장)](/previous-versions/windows/apps/hh464906(v=win.10)#update_task) | 지원 여부 | 
| [캐시된 파일 업데이트기 계약](/previous-versions/windows/apps/hh464906(v=win.10)#cached_file_updater) | 지원 여부 | 
| [카메라 설정(확장)](/previous-versions/windows/apps/hh464906(v=win.10)#camera_settings) | 지원되지 않음 | 
| [전화 걸기 프로토콜](/previous-versions/windows/apps/hh464906(v=win.10)#dial_protocol) | 지원되지 않음 | 
| [파일 활성화(확장명)](/previous-versions/windows/apps/hh464906(v=win.10)#file_activation) | 지원 여부 | 
| [파일 열기 선택기 계약](/previous-versions/windows/apps/hh464906(v=win.10)#file_open_picker_contract) | 지원 여부 | 
| [파일 저장 선택기 계약](/previous-versions/windows/apps/hh464906(v=win.10)#file_save_picker_contract) | 지원 여부 | 
| [잠금 화면 호출](/previous-versions/windows/apps/hh464906(v=win.10)#lock_screen_call) | 지원되지 않음 | 
| [미디어 재생](/previous-versions/windows/apps/hh464906(v=win.10)#media_playback) | 지원되지 않음 | 
| [원격 재생 계약](/previous-versions/windows/apps/hh464906(v=win.10)#playto_contract) | 지원되지 않음 | 
| [미리 설치된 구성 작업](/previous-versions/windows/apps/hh464906(v=win.10)#preinstalled_config_task) | 지원되지 않음 | 
| [3D 인쇄 워크플로](/previous-versions/windows/apps/hh464906(v=win.10)#print_3d_workflow) | 지원 여부 | 
| [인쇄 작업 설정(확장)](/previous-versions/windows/apps/hh464906(v=win.10)#print_task_settings) | 지원되지 않음 | 
| [URI 활성화(확장)](/previous-versions/windows/apps/hh464906(v=win.10)#protocol_activation) | 지원 여부 | 
| [제한된 시작](/previous-versions/windows/apps/hh464906(v=win.10)#restricted_launch) | 지원되지 않음 | 
| [계약 검색](/previous-versions/windows/apps/hh464906(v=win.10)#search_contract) | 지원되지 않음 | 
| [설정 계약](/previous-versions/windows/apps/hh464906(v=win.10)#settings_contract) | 지원되지 않음 | 
| [계약 공유](/previous-versions/windows/apps/hh464906(v=win.10)#share_contract) | 지원되지 않음 | 
| [SSL/인증서(확장)](/previous-versions/windows/apps/hh464906(v=win.10)#ssl_certificates) | 지원 여부 | 
| [웹 계정 공급자](/previous-versions/windows/apps/hh464906(v=win.10)#web_account_provider) | 지원 여부 | 

## <a name="app-file-storage"></a>앱 파일 스토리지

모든 저장소는 [Windows 네임 스페이스](/uwp/api/Windows.Storage)를 통해 Storage 됩니다. HoloLens는 앱 저장소 동기화/로밍을 지원 하지 않습니다. 자세한 내용은 아래 설명서를 확인 하세요.

* [파일, 폴더 및 라이브러리](/windows/uwp/files/index)
* [설정과 기타 앱 데이터의 저장 및 검색](/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>알려진 폴더

UWP 앱에 대 한 자세한 내용은 [Knownfolders](/uwp/api/Windows.Storage.KnownFolders) 를 참조 하세요.

<table>
<tr>
<th> 속성</th><th> HoloLens에서 지원</th><th> 모던 헤드셋에서 지원 됨</th><th> Description</th>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>앱 캡처 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>카메라 롤 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">문서 라이브러리</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>문서 라이브러리를 가져옵니다. 문서 라이브러리는 일반적인 용도로 사용 되지 않습니다.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>음악 라이브러리를 가져옵니다.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>개체 3D 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>그림 라이브러리를 가져옵니다.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">목록과</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>재생 목록 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>저장 된 그림 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>비디오 라이브러리를 가져옵니다.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">홈 그룹</a></td><td></td><td style="text-align: center;">✔️</td><td>홈 그룹 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>미디어 서버 (DLNA의 디지털 동맹 네트워크 동맹) 장치 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>기록 된 호출 폴더를 가져옵니다.</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>이동식 장치 폴더를 가져옵니다.</td>
</tr>
</table>

## <a name="app-package"></a>앱 패키지

Windows 10를 사용 하면 더 이상 운영 체제를 대상으로 하는 것이 아니라 [하나 이상의 장치 제품군으로 앱을 대상](/windows/uwp/get-started/universal-application-platform-guide#device-families)으로 합니다. 장치 패밀리는 장치 제품군 내의 장치에서 예측할 수 있는 Api, 시스템 특성 및 동작을 식별 합니다. 또한 [Microsoft Store](../distribute/submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families)에서 앱을 설치할 수 있는 장치 집합을 결정 합니다.

* 데스크톱 헤드셋과 HoloLens를 모두 대상으로 하려면 앱을 Windows 대상으로 **합니다. 유니버설** 장치 제품군.
* 데스크톱 헤드셋만을 대상으로 하려면 앱을 Windows으로 대상으로 **합니다. 데스크톱** 장치 제품군.
* HoloLens만 대상으로 하려면 앱을 Windows 대상으로 **합니다. Holographic** 장치 제품군.

## <a name="see-also"></a>추가 정보

* [앱 보기](app-views.md)
* [혼합 현실에 사용되는 2D UWP 앱 업데이트](../develop/porting-apps/building-2d-apps.md)
* [3D 앱 시작 관리자 디자인 지침](../distribute/3d-app-launcher-design-guidance.md)
* [3D 앱 시작 관리자 구현](../distribute/implementing-3d-app-launchers.md)