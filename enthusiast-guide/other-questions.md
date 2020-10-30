---
title: 기타 질문
description: 표준 소비자 지원 설명서를 벗어나는 추가 Windows 혼합 현실 문제 해결 팁입니다.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원, Windows Mixed Reality 제거, 지원 되는 언어
appliesto:
- Windows 10
ms.openlocfilehash: aa61148a115ae295c1dc64b575a2fae7b0111470
ms.sourcegitcommit: feceb21018ce1d966188a34bd1faeddfdc1b9544
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044462"
---
# <a name="other-questions"></a>기타 질문

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>내 그래픽 드라이버가 지원 되지 않습니다 (그래픽 드라이버 오류 오류가 발생 함).

"Dxdiag"를 검색 하 고 실행 합니다.

1.  결과가 "기본 렌더러" 이면 그래픽 드라이버가 설치 되어 있지 않습니다. 이 문제를 해결하려면
    * **Device Manager > 작업 > 하드웨어 변경 내용 검색** 으로 이동 합니다.
    * Windows 업데이트를 사용 하 여 드라이버를 업데이트 합니다.
    * 그래도 문제가 해결 되지 않으면 제조업체 웹 사이트로 이동 하 여 최신 드라이버 업데이트를 설치 합니다. 
    * GPU에 대 한 업데이트를 사용할 수 없는 경우 장치에서 WMR가 지원 되지 않을 수 있습니다. 이 것으로 생각 되 면 [지원](https://support.microsoft.com)담당자에 게 문의 하세요.
2.  "WDDM 2.1" 이상 버전을 가져오는 경우 그래픽 드라이버가 설치 되지만 최신 버전이 아닐 수 있습니다. 최신 버전을 가져오려면 다음을 수행 합니다.
    * Windows 업데이트를 사용 하 여 드라이버를 업데이트 합니다.
    * 업데이트에서 문제가 해결 되지 않으면 제조업체 웹 사이트로 이동 하 여 최신 드라이버 업데이트를 설치 합니다. 
    * GPU에 대 한 업데이트를 사용할 수 없는 경우 장치에서 WMR가 지원 되지 않을 수 있습니다. 이 것으로 생각 되 면 [지원](https://support.microsoft.com)담당자에 게 문의 하세요.
    
Windows Mixed Reality 설치에서 그래픽 카드가 요구 사항을 충족 하지 않는 것으로 생각 하 고 있다고 생각 되는 경우 헤드셋이 올바른 카드에 꽂혀 있는지 확인 합니다.

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>내 Samsung Odyssey 또는 Odyssey + 헤드셋 펌웨어 업데이트가 중단 됩니다.

Samsung는 "Samsung HMD Odyssey Setup" 및 "Samsung HMD Odyssey + Setup" 장치 도우미 앱을 통해 제공 되는 헤드셋 펌웨어 업데이트를 소유 하 고 게시 합니다. Samsung 펌웨어 업데이트 문제에 대 한 자세한 내용 및 도움을 보려면 Samsung 고객 서비스에 문의 하세요.

펌웨어 업데이트 프로세스가 중단 되 고 5 분 이상 진행 되지 않은 경우:
* 다른 모든 USB 장치를 일시적으로 분리 하 고 펌웨어 업데이트를 다시 시도 합니다.
* Samsung 헤드셋을 PC의 다른 USB 3.0 포트에 연결 합니다.
* Gb의 AORUS App Center와 같은 펌웨어 업데이트를 방해할 수 있는 설치 된 소프트웨어를 사용 하지 않도록 설정 하거나 제거 합니다.
* 다른 PC를 사용 하 여 Samsung 헤드셋 펌웨어 업데이트를 수행 합니다.

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>혼합 현실에서 내 PC 데스크톱에 액세스 어떻게 할까요??
Windows의 헤드셋에서 데스크톱 앱을 시작 합니다. 단추를 클릭 하 여 **모든 앱 > 데스크톱 >** 혼합 현실에서 PC 데스크톱에 액세스할 수 있습니다.

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>혼합 현실에서 여러 모니터를 확인 하려면 어떻게 해야 하나요?
기본적으로 데스크톱 앱은 자동으로 전환 하 여 포커스가 있는 모니터를 표시 합니다. 혼합 현실에서 모든 모니터를 보려면 다음을 수행 합니다. 
* 앱의 왼쪽 위 모서리에 있는 모니터 아이콘을 클릭 합니다.
* "모니터 자동 전환"을 사용 하지 않도록 설정 합니다.
* 보려는 모니터를 선택 합니다.
* 데스크톱 앱의 다른 인스턴스를 시작 합니다.
* 해당 인스턴스에 대해 보려는 모니터를 선택 합니다.
* 모든 실제 모니터에 대해 반복 합니다.
혼합 현실를 다시 시작할 때마다 각 데스크톱 앱에 표시 하려면 모니터를 다시 선택 해야 합니다. 

## <a name="my-desktop-app-only-shows-a-black-screen"></a>내 데스크톱 앱에는 검은색 화면만 표시 됩니다.
PC에 Nvidia 하이브리드 GPU가 있는 경우이 문제는 통합 된 GPU가 아닌 개별 GPU에서 runtimebroker.exe를 실행 하는 Nvidia 장치에 의해 발생할 수 있습니다. 이 문제를 해결 하려면[어떻게 할까요? "새 프로그램에 대 한 Optimus 설정 만들기"의](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)지침을 따르세요. C:\windows\system32\runtimebroker.exe 추가 하 고 "통합 그래픽" 프로세서에서 강제로 실행 하도록 합니다. 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Windows Mixed Reality를 사용 하는 경우 내 Wi-Fi 느려집니다.

2.4 g h z Wi-Fi 연결을 사용 하는 경우 동작 컨트롤러에서 Wi-fi 속도가 느려질 수 있습니다. 다음 작업 중 하나를 수행하세요.
* 사용할 수 있는 경우 5GHz Wi-Fi 연결로 전환 합니다. [자세히 알아봅니다](https://support.microsoft.com/en-us/help/4000461).
* 별도의 Bluetooth 어댑터를 사용 하 여 이동 컨트롤러를 PC에 연결 합니다. [권장 어댑터](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)를 참조 하세요.

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>PC를 연결 하 고 요금을 청구 하는 메시지를 받았습니다. 이유

노트북을 사용 하는 경우 Windows Mixed Reality는 PC가 완전히 충전 되 고 연결 된 경우에 가장 잘 작동 합니다. 

## <a name="what-is-the-experience-options-setting"></a>환경 옵션 설정은 무엇 인가요?

이 설정 ( **설정 > 혼합 현실 > 헤드셋 표시 > 환경 옵션** )을 사용 하면 Windows Mixed reality 성능 설정을 변경할 수 있습니다. 이를 통해 다양 한 콘텐츠를 통해 하드웨어 구성에 대 한 최상의 환경을 선택할 수 있습니다. 이러한 옵션은 다음과 같습니다.
* 자동: Windows Mixed Reality는 하드웨어 구성에 대 한 최상의 환경을 결정 합니다. 대부분의 사용자는이 옵션을 사용 하 여 시작 하는 것이 가장 좋습니다.
* 60Hz: 새로 고침 빈도를 60Hz로 설정 하 고 혼합 현실 포털에서 비디오 캡처 및 미리 보기와 같은 특정 기능을 끕니다.
* 90Hz: 새로 고침 빈도를 90Hz로 설정 합니다.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Windows Mixed Reality에서 지원 되는 언어는 무엇 인가요?

Windows Mixed Reality는 다음 언어로 제공 됩니다.
* 중국어 간체(중국)
* 영어(오스트레일리아)
* 영어(캐나다)
* 영어(영국)
* 영어(미국)
* 프랑스어(캐나다)
* 프랑스어(프랑스)
* 독일어(독일)
* 이탈리아어(이탈리아)
* 일본어(일본)
* 스페인어(멕시코)
* 스페인어(스페인)

PC가 다른 언어로 설정 되어 있지만 인터페이스가 영어 (미국)로 표시 되 고 음성 명령과 받아쓰기를 사용할 수 없는 경우 Windows Mixed Reality를 사용할 수 있습니다. Windows Mixed Reality 화면 키보드는 영어 (미국)만 해당 합니다. 텍스트를 다른 언어로 입력 하려면 PC에 연결 된 실제 키보드를 사용 합니다. 위에 나열 된 지원 되는 Windows Mixed Reality 언어 중 하나에서 받아쓰기를 사용할 수도 있습니다. 화면 키보드에서 마이크를 선택 하면 됩니다.

Windows Mixed Reality는 음성 명령 또는 받아쓰기 기능 없이도 다음 언어로 제공 됩니다.
* 중국어 번체 (대만 및 홍콩)
* 네덜란드어(네덜란드)
* 한국어(한국)
* 러시아어(러시아)

## <a name="i-have-questions-about-my-headset-hardware"></a>내 헤드셋 하드웨어에 대 한 질문이 있습니다.

헤드셋에 대 한 자세한 내용은 제조업체에서 확인 하세요. 상자에 제품 가이드가 있거나 제조업체의 웹 사이트를 사용해 볼 수 있습니다.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Windows Mixed Reality를 제거할 어떻게 할까요? 있나요?

1. PC에서 헤드셋의 연결을 끊습니다.
2. Windows Mixed Reality 포털을 닫습니다.
2. **시작 > 설정 > 혼합 현실** 로 이동 하 고 "제거"를 선택 합니다.

헤드셋을 다시 사용할 준비가 되 면 플러그 인을 시작 하 고 Windows Mixed Reality 포털에서 설치를 진행 합니다.

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>"Windows Mixed Reality 제거를 완료할 수 없습니다." 라는 메시지가 나타났습니다.

사용자 환경에 대 한 정보를 포함 하 여 일부 파일은 컴퓨터에 남아 있을 수 있습니다. 나중에 Windows Mixed Reality를 다시 설치 하려는 경우 문제가 발생할 수 있습니다. 레지스트리를 수정 하 고 Windows PowerShell을 사용 하 여 명령을 실행 하 여 PC에서 남아 있는 Windows 혼합 현실 정보를 수동으로 제거할 수 있습니다. _레지스트리를 잘못 수정 하면 심각한 문제가 발생할 수 있습니다. 이러한 단계를 신중 하 게 수행 해야 합니다. 추가 된 보호를 위해 수정 하기 전에 레지스트리를 백업 하 여 문제가는 때 복원할 수 있도록 합니다._ 자세한 내용은 [Windows에서 레지스트리를 백업 하 고 다시 작성 하는 방법](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows)을 참조 하세요. 

다음 명령을 사용 하 여 Windows mixed reality를 제거 합니다.
1. PC를 다시 시작 합니다.
2. **검색** 상자에 "regedit"를 입력 하 고 "예"를 선택 합니다.
3. 다음 레지스트리 값을 제거 합니다.
   <ul>
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>하 고 "FirstRunSucceeded"를 삭제 합니다.</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>하 고 "PreferDesktopSpeaker" 및 "PreferDesktopMic"를 삭제 합니다.</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>"DisableSpeechInput"를 삭제 합니다. 참고: Windows Mixed Reality를 사용 하는 PC의 모든 사용자 계정에 대해 HHKEY_CURRENT_USER의 레지스트리 항목을 삭제 해야 합니다.</li> 
    <li><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>"DeviceID" 및 "Mode"를 삭제 합니다.</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>하 고 "OnDeviceLearningCompleted"를 삭제 합니다.</li> 
   </ul>
4. 다음 레지스트리 키를 제거 합니다. <ul>
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></li><br/></ul>
5. 레지스트리 편집기를 닫습니다.
6.**C:\Users\user name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \LocalState** 로 이동 하 고 "RoomBounds.json"을 삭제 합니다. Windows Mixed Reality를 사용 하는 각 사용자에 대해이를 반복 합니다.
7. 관리자 cmd 프롬프트를 열고 **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** 로 이동 합니다. "헤드 추적 데이터" 폴더의 내용을 삭제 합니다 (폴더 자체는 아님).
8. "검색 상자"에 "powershell"을 입력 하 고 "Windows PowerShell"을 마우스 오른쪽 단추로 클릭 한 다음 "관리자 권한으로 실행"을 선택 합니다.
9. Windows PowerShell에서 다음을 수행 합니다. <ul>
   <li>명령 프롬프트에서 <b>Dism/Online/Get-Capabilities</b>을 복사 하 여 붙여 넣은 다음 enter 키를 누릅니다.</b></li> 
   <li>Holographic로 시작 하는 기능 Id를 복사 합니다 .이 항목이 없으면이 항목이 설치 되지 않은 것입니다. 이 경우에는 10 단계로 건너뜁니다.</li> 
   <li>다음 명령 프롬프트를 복사 하 여 붙여넣고 Enter 키를 누릅니다. <b>Dism/Online/Remove-Capability/CapabilityName: 마지막 단계에서 복사 된 기능 id</b></li>
   </ul>
10. PC를 다시 시작 합니다.

