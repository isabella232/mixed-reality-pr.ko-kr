---
title: 시선 추적 기본 설정
description: MRTK에서 눈 추적을 설정 하는 방법
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 눈 추적,
ms.openlocfilehash: d8b47639729381a41e4fe1e1db86700bf9323860553934a6da4dfa4b15de49eb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197459"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a>MRTK에서 눈 추적 시작

이 페이지에서는 앱에서 눈 추적을 사용 하도록 Unity MRTK 장면을 설정 하는 방법을 설명 합니다.
다음은 새로 새 장면으로 시작 하는 것으로 가정 합니다.
또는 직접 빌드할 수 있는 다양 한 예제를 사용 하 여 이미 구성 된 [Mrtk 눈 추적 예제](../../example-scenes/eye-tracking-examples-overview.md) 를 확인할 수 있습니다.

## <a name="eye-tracking-requirements-checklist"></a>눈 추적 요구 사항 검사 목록

눈 추적이 제대로 작동 하려면 다음 요구 사항을 충족 해야 합니다.
HoloLens 2에 대 한 눈 추적을 처음 접하는 경우 mrtk에서 눈 추적을 설정 하는 방법에 대해서는 걱정할 필요가 없습니다.
아래에서 각 항목을 처리 하는 방법에 대해 자세히 살펴보겠습니다.

1. _' 눈 응시 Data Provider '_ 을 입력 시스템에 추가 해야 합니다. 이는 플랫폼의 눈 추적 데이터를 제공 합니다.
2. 응용 프로그램 매니페스트에서 _' GazeInput '_ 기능을 사용 하도록 설정 해야 합니다.
   **unity 2019에서이 기능을 설정할 수 있지만 unity 2018 및 이전 버전에서는 Visual Studio 및 mrtk 빌드 도구를 통해이 기능을 사용할 수 있습니다.**
3. HoloLens는 현재 사용자에 대해 눈에 잘 보정 **되어야** 합니다. [사용자가 아이 보정 인지 여부를 검색 하는 샘플](eye-tracking-is-user-calibrated.md)을 확인 하세요.

### <a name="a-note-on-the-gazeinput-capability"></a>GazeInput 기능에 대 한 참고 사항

mrtk 제공 빌드 도구 (예: 혼합 현실 Toolkit-> 유틸리티-> 빌드 창)는 자동으로 GazeInput 기능을 사용 하도록 설정할 수 있습니다. 이렇게 하려면 ' Appx 빌드 옵션 ' 탭에서 ' 입력 기능 응시 '가 선택 되어 있는지 확인 해야 합니다.

![MRTK 빌드 도구](../../images/eye-tracking/mrtk_et_buildsetup.png)

이 도구는 Unity 빌드가 완료 된 후 AppX 매니페스트를 찾고 GazeInput 기능을 수동으로 추가 합니다.
**Unity 2019 이전에는 unity의 기본 제공 빌드 창 (예: 파일 > 빌드 설정)을 사용 하는 경우이 도구가 활성화 되지** 않습니다.

Unity 2019 이전에 Unity의 빌드 창을 사용 하는 경우 다음과 같이 Unity 빌드 후에 기능을 수동으로 추가 해야 합니다.

1. 컴파일된 Visual Studio 프로젝트를 열고 솔루션에서 _' appxmanifest.xml '_ 를 엽니다.
2. _기능_ 아래에서 _' GazeInput '_ 확인란을 선택 해야 합니다. _' GazeInput '_ 기능이 표시 되지 않으면 시스템이 [mrtk를 사용 하기 위한 필수 구성 요소](/windows/mixed-reality/develop/install-the-tools) (특히 Windows SDK 버전)를 충족 하는지 확인 합니다.

_다음 사항에 유의 하세요._ 새 빌드 폴더로 빌드하는 경우에만이 작업을 수행 해야 합니다.
즉, 이미 Unity 프로젝트를 빌드하고 이전에 appxmanifest.xml를 설정 했 고 동일한 폴더를 다시 대상으로 하는 경우에는 변경 내용을 다시 적용할 필요가 없습니다.

## <a name="setting-up-eye-tracking-step-by-step"></a>시각 추적 설정 단계별 설정

### <a name="setting-up-the-scene"></a>장면 설정

_' Mixed Reality Toolkit-> Configure ... '_ 를 클릭 하 여 _MixedRealityToolkit_ 를 설정 합니다. 메뉴 모음에서

![MRTK 구성](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a>아이 추적에 필요한 MRTK 프로필 설정

MRTK 장면을 설정한 후 MRTK에 대 한 프로필을 선택 하 라는 메시지가 표시 됩니다.
_DefaultMixedRealityToolkitConfigurationProfile_ 를 선택한 다음 _' 사용자 지정 & 복사 '_ 옵션을 선택할 수 있습니다.

![MRTK 프로필](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a>"아이 응시 데이터 공급자" 만들기

- MRTK 프로필의 _' 입력 '_ 탭을 클릭 합니다.
- 기본 항목 ( _' DefaultMixedRealityInputSystemProfile '_ )을 편집 하려면 옆의 _' 복제 '_ 단추를 클릭 합니다. _' 프로필 복제 '_ 메뉴가 나타납니다. 해당 메뉴의 아래쪽에서 _' 복제 '_ 를 클릭 하기만 하면 됩니다.
- 새 입력 프로필을 두 번 클릭 하 고 _' 입력 데이터 공급자 '_ 를 확장 한 다음 _' + Data Provider 추가 '_ 를 선택 합니다.
- 새 데이터 공급자를 만듭니다.
  - **유형** 아래에서 _' MixedReality. Toolkit를 선택 합니다. WindowsMixedReality '_  ->  _' WindowsMixedRealityEyeGazeDataProvider '_
  - **플랫폼** 의 경우 _' Windows Universal '_ 를 선택 합니다.

![MRTK 데이터 공급자](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a>Unity 편집기에서 눈 추적 시뮬레이션

Unity 편집기에서 눈 추적 입력을 시뮬레이션 하 여 HoloLens 2에 앱을 배포 하기 전에 이벤트가 올바르게 트리거되는지 확인할 수 있습니다.
눈에 지 응시 신호는 카메라의 위치를 아이 응시 원본으로 사용 하 고 카메라의 앞에 있는 벡터를 눈 응시 방향으로 사용 하 여 시뮬레이션 합니다.
이 방법은 초기 테스트에 유용 하지만 신속한 시각 이동에는 좋은 모조 아닙니다.
이를 위해 HoloLens 2에서 눈에 잘 맞는 상호 작용을 자주 테스트 하는 것이 좋습니다.

1. **시뮬레이션 된 눈동자 추적 사용**:
    - MRTK 구성 프로필에서 _' 입력 '_ 탭을 클릭 합니다.
    - 여기에서 _' 입력 데이터 공급자 '_  ->  _' 입력 시뮬레이션 서비스 '_ 로 이동 합니다.
    - _' DefaultMixedRealityInputSimpulationProfile '_ 을 복제 하 여 변경 합니다.
    - _' 눈 위치 시뮬레이트 '_ 확인란을 선택 합니다.

    ![MRTK 눈동자 시뮬레이트](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. **기본 헤드 응시 커서 사용 안 함**: 일반적으로 눈에 _잘 드는_ 커서를 표시 하지 않거나 매우 미묘한 커서를 사용 하지 않는 것이 좋습니다.
기본적으로 MRTK 응시 포인터 프로필에 연결 된 기본 헤드 응시 커서를 숨기는 것이 좋습니다.
    - Mrtk 구성 프로필-> _' 입력 '_  ->  _' 포인터 '_ 로 이동 합니다.
    - _' DefaultMixedRealityInputPointerProfile '_ 을 복제 하 여 변경 합니다.
    - ' _포인터 설정 '_ 위쪽에서 _' GazeCursor '_ 에 보이지 않는 커서 prefab을 할당 해야 합니다. MRTK Foundation에서 _' EyeGazeCursor '_ prefab를 선택 하 여이 작업을 수행할 수 있습니다.

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>응시 공급자에서 눈에 잘 맞는 응시 사용

HoloLens v1에서 헤드 응시는 기본 포인팅 기술로 사용 되었습니다.
헤드 응시는 [카메라](https://docs.unity3d.com/ScriptReference/Camera.html)에 연결 된 MRTK의 _GazeProvider_ 를 통해 계속 사용할 수 있지만, 입력 포인터 프로필의 응시 설정에서 _' IsEyeTrackingEnabled '_ 확인란을 선택 하 여 대신 눈동자 응시를 사용 하도록 선택할 수 있습니다.

>[!NOTE]
>개발자는 _' GazeProvider '_ 의 _' IsEyeTrackingEnabled '_ 속성을 변경 하 여 코드에서 눈에 맞는 응시와 헤드 기반 응시를 전환할 수 있습니다.  

>[!IMPORTANT]
>눈 추적 요구 사항 중 하나라도 충족 되지 않으면 응용 프로그램은 자동으로 head 기반 응시로 대체 됩니다.

### <a name="accessing-eye-gaze-data"></a>아이 응시 데이터 액세스

이제 장면 추적을 사용 하도록 장면을 설정 했으므로 스크립트에서 액세스 하는 방법을 살펴보겠습니다. EyeGazeProvider 및 [눈에 잘 지 원하는 대상 선택을](eye-tracking-target-selection.md) [통해 아이 추적 데이터에](eye-tracking-eye-gaze-provider.md) 액세스 합니다.

### <a name="testing-your-unity-app-on-a-hololens-2"></a>HoloLens 2에서 Unity 앱 테스트

아이 추적을 사용 하 여 앱을 빌드하는 것은 다른 HoloLens 2 mrtk 앱을 컴파일하는 방법과 비슷합니다. [*GazeInput 기능에 대 한 참고*](#a-note-on-the-gazeinput-capability)섹션에서 위에 설명 된 대로 *' 응시 입력 '* 기능을 사용 하도록 설정 했는지 확인 합니다.

#### <a name="eye-calibration"></a>눈 보정

마지막으로, HoloLens 2의 눈 보정을 실행 하는 것을 잊지 마세요.
사용자가 보정 되지 않은 경우에는 눈 추적 시스템에서 입력을 반환 하지 않습니다.
보정을 가져오는 가장 쉬운 방법은 센터를 위아래로 이동 하는 것입니다.
시스템 알림은 새로운 사용자에 게 환영 하 고 눈에 볼 수 있는 것으로 표시 되어야 합니다.
또는 시스템 설정에서 눈 보정을 찾을 수 있습니다. 설정 > 시스템 > 보정은 눈동자 보정 실행 >.

#### <a name="eye-tracking-permission"></a>아이 추적 권한

HoloLens 2에서 처음으로 앱을 시작 하는 경우 사용자에 게 눈동자 추적을 사용할 수 있는 권한을 요청 하는 메시지가 표시 됩니다.
표시 되지 않는 경우이는 일반적으로 _' GazeInput '_ 기능이 설정 되지 않았음을 나타냅니다.

권한 프롬프트가 한 번 표시 되 면 다시 자동으로 표시 되지 않습니다.
_"아이 추적 사용 권한 거부"_ 가 있는 경우 설정 > 개인 정보-> 앱에서이를 다시 설정할 수 있습니다.

---

이제 MRTK Unity 앱에서 눈 추적을 사용 하기 시작 합니다.
아이 추적 입력을 사용 하 고 프로젝트에서 다시 사용할 수 있는 스크립트를 편리 하 게 제공 하는 방법을 보여 주는 [MRTK 눈 추적 자습서와 샘플](../../example-scenes/eye-tracking-examples-overview.md) 을 확인 해야 합니다.

---
["MixedRealityToolkit의 눈동자 추적"으로 돌아가기](eye-tracking-main.md)