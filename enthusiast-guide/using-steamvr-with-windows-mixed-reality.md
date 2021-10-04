---
title: Windows Mixed Reality 함께 SteamVR 사용
description: 호환되는 PC가 있는 Windows Mixed Reality 헤드셋 및 컨트롤러에서 SteamVR 게임을 설치하고 재생하는 방법을 알아봅니다.
author: qianw211
ms.author: v-qianwen
ms.date: 9/23/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, 게임, SteamVR, Steam, 시스템 요구 사항
ms.openlocfilehash: b06c5e0b9918a5277a2c31e391dbdbc1ef740110
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436718"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a>Windows Mixed Reality 함께 SteamVR 사용

Windows Mixed Reality 통해 사용자는 Windows Mixed Reality 몰입형 헤드셋에서 SteamVR 환경을 실행할 수 있습니다. Windows Mixed Reality 설치한 후 사용자는 데스크톱 또는 Steam 라이브러리에서 즐겨 찾는 SteamVR 애플리케이션을 시작하고 Windows 헤드셋에서 직접 재생할 수 있습니다.

## <a name="get-your-pc-ready"></a>PC 준비

* 보류 중인 업데이트가 없는지 확인합니다. **> 설정 > 업데이트 시작 & 보안 > Windows 업데이트를** 선택합니다. 업데이트를 사용할 수 있는 경우 **지금 설치를** 선택합니다. 사용할 수 있는 업데이트가 없는 경우 **업데이트 확인을** 선택한 다음, 새 업데이트를 설치합니다.
* PC 요구 사항은 Steam의 앱 및 콘텐츠에 따라 다릅니다. 제목당 최소 요구 사항을 참조하세요. GTX 1070 그래픽 카드(또는 이와 동등한) 및 Intel® Core™ i7 프로세서가 있는 PC는 광범위한 타이틀에 적합한 환경을 제공해야 합니다.
* [아직 설정하지](set-up-windows-mixed-reality.md) 않은 경우 Windows Mixed Reality 설정합니다. 

## <a name="set-up-windows-mixed-reality-for-steamvr"></a>SteamVR에 대한 Windows Mixed Reality 설정

1. [SteamVR을 다운로드하여 설치합니다.](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)
2. 준비가 되면 SteamVR을 시작합니다. SteamVR 자습서가 자동으로 시작되어야 합니다.

> **참고:** SteamVR 설치의 고급 문제 해결을 위해 다음 소프트웨어 구성 요소가 설치되어 있는지 확인합니다.
> 1. [Steam을](http://store.steampowered.com/about/) 설치하고 **로그인하거나** **새 계정을 만듭니다.**
> 2. [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)를 설치합니다. 헤드셋을 연결한 후 Steam을 시작하면 SteamVR을 설치하라는 대화 상자가 표시됩니다. 대화 상자의 프롬프트에 따라 설치합니다.
    * 팝업이 표시되지 않으면 라이브러리의 *도구* 섹션으로 이동하여 SteamVR을 *설치합니다.* 목록에서 SteamVR을 찾은 다음, 마우스 오른쪽 단추를 클릭하고 *게임 설치를* 선택합니다.
> 3. [Windows Mixed Reality 설치합니다.](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

## <a name="set-up-windows-mixed-reality-for-steamvr-in-an-environment-without-internet-access"></a>인터넷에 액세스할 수 없는 환경에서 SteamVR에 대한 Windows Mixed Reality 설정

**휴대용 스토리지 디바이스에 필요한 미디어 저장**
1. 전체 인터넷 액세스가 가능한 PC에서 [Steam을](https://store.steampowered.com/app/250820/SteamVR/) 사용하여 위에서 설명한 대로 [SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) 및 [Windows Mixed Reality](http://store.steampowered.com/about/) 설치합니다.
2. Steam에서 라이브러리 섹션을 열고 "도구"라는 레이블이 있는 파트를 찾습니다.
3. SteamVR이 설치되면 "SteamVR" 항목을 마우스 오른쪽 단추로 클릭하고 결과 팝업 메뉴에서 "속성" 항목을 클릭합니다.
4. 여러 탭이 있는 새 창이 열립니다. "로컬 파일" 탭을 선택하고 "로컬 파일 찾아보기"라는 레이블이 있는 단추를 클릭합니다.
5. SteamVR 런타임을 포함하는 디렉터리를 엽니다. 이 전체 디렉터리(이름: SteamVR)를 선택한 이식 가능한 미디어(예: USB 썸 드라이브)에 복사합니다.
6. Windows Mixed Reality 및 대상 PC에 설치하려는 모든 SteamVR 호환 앱을 사용하여 동일한 작업을 수행합니다.

**대상 PC에서 SteamVR 실행**
1. 이식 가능한 스토리지 디바이스를 대상 PC에 연결한 후, SteamVR, MixedRealityVRDriver 및 기타 폴더를 대상 PC의 편리한 위치로 이동합니다.
![대상 PC에 설치된 SteamVR 및 Windows Mixed Reality](images/steamvr-install-files.png)

2. SteamVR 및 MixedRealityVRDriver가 동일한 폴더에 있는지 확인하여 명령 프롬프트를 엽니다. 이 예제에서는 포함하는 폴더가 *C:\SteamVRInstall에 있다고 가정합니다.* 이 경우 명령 프롬프트에서 다음을 실행해야 합니다.
```powershell
chdir "C:\SteamVRInstall"
.\SteamVR\bin\win64\vrpathreg.exe adddriver "C:\SteamVRInstall\MixedRealityVRDriver"
```
(32비트 버전의 Windows 실행하는 경우 위의 경로 부분이 `win64` 대신 있어야 `win32` 합니다.)

이렇게 하면 런타임이 사용자 지정 설치에서 SteamVR 드라이버에 대한 Windows Mixed Reality 찾을 수 있습니다.

4. SteamVR을 실행하려면SteamVR\bin\win64\vrstartup.exe에 있는 "vrstartup.exe" 파일을 두 번 *클릭하거나* 대상 *PC에서* 32비트 버전의 Windows 실행하는 경우SteamVR\bin\win32\vrstartup.exe.

자세한 내용 [및 문제 해결은 Steamworks 설명서 페이지를 참조하세요.](https://partner.steamgames.com/doc/features/steamvr/enterprise#2)

## <a name="play-steamvr-games"></a>SteamVR 게임 재생

1. 헤드셋을 PC에 커넥트 모션 컨트롤러를 켭니다.
2. Windows Mixed Reality 홈이 로드되고 컨트롤러가 표시되면 데스크톱에서 Steam 앱을 엽니다.
3. Steam 앱을 사용하여 Steam 라이브러리에서 SteamVR 게임을 시작합니다.

**팁:** 헤드셋을 끄지 않고 SteamVR 게임을 시작하려면 데스크톱 **앱(데스크톱 > 시작)을** 사용하여 Windows Mixed Reality 내에서 PC 데스크톱을 보고 상호 작용합니다.

## <a name="using-motion-controllers-with-steamvr"></a>SteamVR에서 모션 컨트롤러 사용

다른 게임에서는 모션 컨트롤러를 다르게 사용합니다. 다음은 시작하는 데 도움이 되는 몇 가지 기본 사항입니다.

* Steam 대시보드를 열려면 왼쪽 또는 오른쪽 엄지스틱에서 바로 아래로 누릅니다.
* SteamVR 게임을 종료하고 Windows Mixed Reality 홈으로 돌아가려면 Windows 단추를 누릅니다.

## <a name="changing-the-resolution"></a>해결 방법 변경

더 높은 해상도로 게임을 재생하려는 경우 언제든지 SteamVR -> 설정 -> 애플리케이션 창에서 애플리케이션 확인 슬라이더를 조정할 수 있습니다. **더 높은 해상도의 승수를 사용하는 경우 게임이 PC에 더 많은 부담을 줄 것으로 예상할 수 있습니다. 승수를 늘리고 성능 저하를 확인하는 경우 슬라이더를 기본 수준으로 다시 조정하고 게임을 다시 시작하여 변경 내용을 적용합니다.![애플리케이션 확인 조정](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a>여러 헤드셋 사용

VR을 좋아하는 경우 동일한 PC에서 두 개 이상의 VR 헤드셋을 정기적으로 사용할 수 있습니다. 이 경우 Windows Mixed Reality 헤드셋이 연결되면 SteamVR 게임이 항상 Windows Mixed Reality 헤드셋으로 시작됩니다. 다른 헤드셋에서 SteamVR 게임을 시작하려면 계속하기 전에 먼저 Windows Mixed Reality 헤드셋을 분리해야 합니다.

## <a name="preview-programs"></a>미리 보기 프로그램

Windows Mixed Reality 몰입형 헤드셋에서 SteamVR을 사용하는 성능, 안정성 및 전반적인 환경을 개선하기 위해 정기적인 업데이트를 릴리스합니다. 이러한 미리 보기 프로그램은 필요하지 않지만 업데이트를 더 빨리 더 자주 받으려는 경우 조인하는 것이 좋습니다(해당 업데이트에 대한 피드백을 제공하세요!).

### <a name="windows-mixed-reality-for-steamvr-beta"></a>Windows Mixed Reality VR 베타

Windows Mixed Reality는 SteamVR이 Windows Mixed Reality 헤드셋과 함께 작동할 수 있도록 하는 Steam Store에서 설치하는 구성 요소입니다.  이 "브리지"에 업데이트를 정기적으로 게시하고, Steam에서 자동으로 설치합니다.

업데이트를 더 자주 받으려면 공개 베타에 가입하는 것이 좋습니다.  업데이트는 먼저 베타 대상으로 이동하며, 모든 사용자에게 게시하기 전에 해당 피드백을 사용하여 업데이트의 품질이 높은지 확인합니다.  베타 프로그램이 아닌 경우 베타 사용자가 테스트한 후 동일한 수정 및 기능을 모두 얻게 됩니다.

조인하려면 다음을 수행합니다.

  1. Steam에서 **라이브러리** 메뉴 아래의 드롭다운을 사용하여 **소프트웨어** 로 필터링합니다.
  2. 목록에서 Windows Mixed Reality 마우스 오른쪽 **단추로** 클릭하고 **속성을** 선택합니다.
  3. **베타** 탭을 선택합니다.
  4. **"beta - public beta"로** 옵트인하고 **닫기를** 선택하여 확인합니다. 베타 액세스 코드 필드는 비워 두어야 합니다.
  
### <a name="steamvr-beta"></a>SteamVR 베타

SteamVR은 밸브에서 빌드 및 릴리스되며 모든 SteamVR 헤드셋에서 일반적입니다.  모든 사용자에게 게시하기 전에 베타 멤버에 대한 업데이트를 릴리스하는 유사한 모델을 따릅니다.

조인하려면 다음을 수행합니다.

  1. Steam에서 **라이브러리** 메뉴 아래의 드롭다운을 사용하여 **도구로 필터링합니다.**
  2. 목록에서 **SteamVR을** 마우스 오른쪽 단추로 클릭하고 **속성을** 선택합니다.
  3. **베타** 탭을 선택합니다.
  4. **"beta - public beta"로** 옵트인하고 **닫기를** 선택하여 확인합니다.  베타 액세스 코드 필드는 비워 두어야 합니다. ![ SteamVR에 대한 속성 대화 상자에서 SteamVR 베타로 전환합니다.](images/steamvr-beta.png)

### <a name="windows-insider-program"></a> Windows 참가자 프로그램

Windows Mixed Reality Windows 10 11의 일부이며 Windows.  SteamVR 사용자에게 영향을 주는 많은 수정 및 기능은 Windows OS와 함께 제공됩니다.  최신 Windows 10 11개의 미리 보기 빌드를 Windows 경우 [Windows 참가자 프로그램](https://insider.windows.com)조인하는 것이 좋습니다.

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a>SteamVR 앱에 대한 동작 다시 프로젝션 사용

Windows Mixed Reality 90 FPS 다시 프로젝션을 더 원활하게 만드는 실험적 동작 다시 프로젝션 기능이 있습니다.

동작 다시 프로젝션을 사용하도록 설정하면 모든 Steam VR 게임이 명목상 1/2 프레임 속도(90FPS 대신 45fps)로 렌더링되고, SteamVR에 대한 Windows Mixed Reality GPU에서 생성된 동작 벡터를 사용하여 다음 프레임을 추정합니다. 지정된 PC에서 60FPS+를 안정적으로 적중하는 SteamVR 게임의 경우, 이 경우 익숙한 환경을 유지하면서 간헐적인 아티팩트로 견고한 90FPS 환경이 생성됩니다.

사용 가능한 동작 다시 프로젝션 모드는 다음과 같습니다.

* **앱별 SteamVR 설정: SteamVR** 설정 UI를 통해 동작 다시 프로젝션을 제어할 수 있습니다. 그런 다음, SteamVR 설정 열고 Video > Per-Application Video 설정 이동하여 "Motion Smoothing"에 대한 옵션을 선택할 수 있습니다.
* **Auto**: 게임이 너무 느리게 렌더링 되어 90 FPS를 유지 하는 경우 동작 다시 프로젝션이 자동으로 켜 집니다. 게임에서 90 FPS를 유지 하기 시작 하거나 45 FPS 미만으로 렌더링을 시작 하면 동작 reprojection이 꺼집니다. 비동기 회전 reprojection은 항상 사용 됩니다.
* **동작 벡터**: 응용 프로그램이 항상 동작 벡터 재 프로젝션을 사용 하 여 절반 프레임 속도로 실행 되도록 합니다.
* **없음**: 동작 다시 프로젝션을 사용 하지 않습니다.

**Visual Artifacts 필요** 

1. 150% 보다 큰 응용 프로그램 해상도를 사용 하는 경우 흐리게 표시 될 수 있습니다. 동작 reprojection 사용 하는 경우 150% 보다 작은 값을 사용 하는 것이 좋습니다.
2. 특히 게임 HUDs 또는 메뉴에서 선명한 대비 모서리나 텍스트는 disocclusion 때문에 일시적으로 또는 왜곡 될 수 있습니다.
3. SteamVR Home 및 PC에서 50-60 FPS를 안정적으로 적중 하지 않는 많은 게임은이 모드에서 계속 해 서 더 나쁜 환경을 제공 합니다.
4. 일부 게임은 50% 속도 또는 대기 시간 (지연)으로 실행 되도록 보고 되었습니다. 아래 [Windows 피드백 허브](filing-feedback.md) 지침에 따라 이러한 게임을 보고 합니다.

처음에는 최근에 생성 된 NVidia Gpu에 대 한 실험적 지원이 제공 됩니다. 계속 해 서 더 많은 Gpu에서 동작 재 프로젝션 지원을 계속 반복 하 고 개선 하 고 있으며 사용자 의견을 기다리고 있습니다.

**지원 되는 gpu:** Windows Mixed Reality 호환 그래픽 드라이버가 설치 된 Nvidia GeForce GTX1060, AMD RX470 이상

동작 재 프로젝션을 사용 하려면:

1. 위의 지침을 사용 하 여 **SteamVR Beta에 대 한 Windows Mixed Reality** 를 옵트인 했는지 확인 합니다.
2. SteamVR 대시보드를 엽니다.
3. Windows Mixed Reality 로고가 있는 왼쪽의 단추를 선택 하 여 **SteamVR 설정에 대 한 Windows Mixed Reality** 를 엽니다.
4. 팝업 되는 UI에서 그래픽 탭을 선택 합니다.
5. 자동 동작 다시 프로젝션을 사용 하려면 "기본 SteamVR 앱 동작 reprojection 모드"에 대해 "자동"을 선택 합니다.

![SettingsUX로 lsr & LSR 표시기 사용](images/settingsux-enable-lsr.gif)

**동작 Reprojection 표시기**

동작 reprojection 표시기는 실험적 자동 동작 reprojection 기능을 사용 하 여 문제를 진단 하는 데 도움이 됩니다. True로 설정 하면 자동 동작 다시 프로젝션을 수행 하는 동안 헤드셋 표시의 왼쪽 위에 표시기가 표시 됩니다. 이 표시기의 색과 위치는 현재 동작 다시 프로젝션 모드에 해당 합니다. 예는 아래 다이어그램을 참조 하세요.

![mvLSR 지표](images/mvLSRIndicator.png)

녹색 = 응용 프로그램이 전체 프레임 속도로 렌더링 될 수 있으므로 동작 다시 프로젝션이 꺼져 있습니다.

사이안 = 응용 프로그램이 cpu 바인딩되어 있으므로 동작 다시 프로젝션이 설정 되어 있습니다.

Blue = 응용 프로그램이 gpu 바인딩되어 있으므로 동작 다시 프로젝션이 설정 되어 있습니다.

빨강 = 응용 프로그램이 절반 미만의 프레임 속도에서 실행 중 이므로 동작 다시 프로젝션이 꺼져 있습니다. 사용 하도록 설정 된 경우 슈퍼 샘플링을 줄여 보세요.

녹색 + 사이안 + Blue = 움직임 다시 프로젝션이 절반 프레임 속도 모드 이거나 응용 프로그램에서 동작 다시 프로젝션을 요청 했습니다.

## <a name="sharing-feedback-on-steamvr"></a>SteamVR에 대 한 의견 공유

사용자 의견은 Windows Mixed Reality SteamVR 환경을 개선 하는 데 유용 합니다. [Windows 피드백 허브](filing-feedback.md)를 통해 모든 피드백 및 버그를 제출 합니다. 사용자 의견을 최대한 활용 하려면 다음 제안 사항을 따르세요.

1. 피드백 허브에서 "사용자 의견의 종류는 무엇 인가요?"에서 새로운 문제를 보고 하 고 있음을 표시 합니다. 섹션을 위쪽으로 이동 합니다.
2. **Mixed Reality** 범주 및 **앱** 하위 범주를 선택 합니다.
3. 문제 요약에 "SteamVR" 라는 단어를 입력 합니다. 그러면 피드백을 쉽게 찾을 수 있습니다.
4. 문제를 해결 하는 동안 사용 했던 SteamVR 게임 또는 응용 프로그램을 설명 합니다.
5. 사용자 의견에 SteamVR 시스템 보고서를 연결 하는 것이 좋습니다. 이렇게 하면 문제를 진단 하는 데 도움이 될 수 있는 더 많은 로그가 제공 됩니다.
    1. SteamVR 창 (컨트롤러 상태를 표시 하는 작은 창)에서 제목을 선택 하 여 메뉴를 엽니다.
    2. "시스템 보고서 만들기"를 선택 합니다.
    3. 파일에 저장 합니다.
    4. 생성 된 파일을 피드백 허브 항목에 직접 연결 합니다.
6. SteamVR에 대 한 의견이 있는 경우 혼합 현실 성능 추적을 수집 합니다. 
    1. **내 문제 다시 만들기** 단추를 선택 합니다.
    2. "데이터 포함" 옆의 드롭다운에서 **혼합 현실 성능** 을 선택 합니다.
    3. 게임이 실행 중인지 확인 하 고 **캡처 시작** 을 선택 합니다.
    4. 게임을 재생 하 여 추적을 캡처하는 데 몇 초 정도 걸립니다. 추적을 10-15 초 넘게 캡처하지 마세요. 그렇지 않으면 너무 커서 제출할 수 없게 됩니다.
    5. **캡처 중지** 를 선택 합니다.
7. 나머지 필드를 완료 한 후 **제출** 을 선택 합니다.

공유에 대 한 질문이 나 의견이 있는 경우 [스트림 포럼](http://steamcommunity.com/app/719950/discussions/)에서 연락할 수도 있습니다.

## <a name="see-also"></a>참고 항목

* [Windows Mixed Reality를 사용 하 여 SteamVR 문제 해결](steamvr-questions.md)
* [Windows Mixed Reality에서 게임과 앱 사용](using-games-and-apps-in-windows-mixed-reality.md)
* [Unity에서 HP 컨트롤러 사용](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [Unreal에서 HP 컨트롤러 사용](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [버그 및 피드백 신고](filing-feedback.md)
