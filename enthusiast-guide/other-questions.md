---
title: 몰입형 하드웨어 실시간 FAQ
description: 표준 소비자 지원 설명서를 벗어나는 추가 Windows Mixed Reality 문제 해결 팁입니다.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, 문제 해결, 오류, 도움말, 지원, Windows Mixed Reality 제거, 지원되는 언어
appliesto:
- Windows 10
ms.openlocfilehash: 9de3ecfe2f2fc58a0afee0d7702b15131b15b12086d9f4f9851b3a9d4920afe3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219719"
---
# <a name="other-questions"></a>기타 질문

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>내 그래픽 드라이버가 지원되지 않습니다(그래픽 드라이버 오류 오류가 발생함).

"dxdiag"를 검색하고 실행합니다.

1.  결과가 "기본 렌더러"이면 그래픽 드라이버가 설치되지 않습니다. 이 문제를 해결하려면
    * 디바이스 **관리자 > 작업 > 하드웨어 변경 내용 검색으로** 이동합니다.
    * Windows 업데이트를 사용하여 드라이버를 업데이트합니다.
    * 그래도 문제가 해결되지 않으면 제조업체의 웹 사이트로 이동하여 최신 드라이버 업데이트를 설치합니다. 
    * GPU에 업데이트를 사용할 수 없는 경우 디바이스에서 WMR이 지원되지 않을 수 있습니다. 그렇게 해야 한다고 생각되면 [지원 담당자에게 문의합니다.](https://support.microsoft.com)
2.  "WDDM 2.1" 이하 버전이 있으면 그래픽 드라이버가 설치되지만 최신 버전이 아닐 수 있습니다. 최신 버전을 얻으려면 다음을 수행합니다.
    * Windows 업데이트를 사용하여 드라이버를 업데이트합니다.
    * 해당 업데이트로 문제가 해결되지 않으면 제조업체의 웹 사이트로 이동하여 최신 드라이버 업데이트를 설치합니다. 
    * GPU에 업데이트를 사용할 수 없는 경우 디바이스에서 WMR이 지원되지 않을 수 있습니다. 그렇게 해야 한다고 생각되면 [지원 담당자에게 문의합니다.](https://support.microsoft.com)

Windows Mixed Reality 설정에서 그래픽 카드가 요구 사항을 충족하지 않는다고 생각되는 경우 헤드셋이 올바른 카드에 연결되어 있는지 확인합니다.

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>내 Samsung Odyssey 또는 Odyssey+ 헤드셋 펌웨어 업데이트가 고정되었습니다.

Samsung은 "Samsung HMD Odyssey 설정" 및 "Samsung HMD Odyssey+ Setup" 디바이스 도우미 앱을 통해 제공되는 헤드셋 펌웨어 업데이트를 소유하고 게시합니다. 자세한 내용 및 Samsung 펌웨어 업데이트 문제에 대한 도움말은 Samsung 고객 서비스에 문의하세요.

펌웨어 업데이트 프로세스가 5분 넘게 진행되지 않은 경우:

* 다른 모든 USB 디바이스를 일시적으로 분리하고 펌웨어 업데이트를 다시 시도합니다.
* Samsung 헤드셋을 PC의 다른 USB 3.0 포트에 커넥트.
* Gigabyte의 AORUS App Center 같이 펌웨어 업데이트를 방해할 수 있는 설치된 소프트웨어를 사용하지 않도록 설정하거나 제거합니다.
* 다른 PC를 사용하여 Samsung 헤드셋 펌웨어를 업데이트합니다.

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>혼합 현실에서 내 PC 데스크톱에 액세스할 어떻게 할까요? 있나요?
**Windows Button > 모든 앱 > Desktop에서** 헤드셋에서 데스크톱 앱을 시작하여 혼합 현실에서 PC 데스크톱에 액세스합니다.

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>Mixed Reality 여러 모니터를 보려면 어떻게 해야 합니까?

기본적으로 데스크톱 앱은 자동으로 전환하여 포커스가 있는 모니터를 표시합니다. 혼합 현실에서 모든 모니터를 보려면 다음을 수행합니다.

* 앱의 왼쪽 위 모서리에서 모니터 아이콘을 선택합니다.
* "모니터 자동 전환"을 사용하지 않도록 설정합니다.
* 보려는 모니터를 선택합니다.
* 데스크톱 앱의 다른 인스턴스를 시작합니다.
* 해당 인스턴스에서 보려는 모니터를 선택합니다.
* 모든 물리적 모니터에 대해 반복합니다.
혼합 현실을 다시 시작할 때마다 각 데스크톱 앱에 표시할 모니터를 다시 선택해야 합니다.

## <a name="my-desktop-app-only-shows-a-black-screen"></a>내 데스크톱 앱에 검은색 화면만 표시

PC에 Nvidia 하이브리드 GPU가 있는 경우 통합 GPU 대신 불연속 GPU에서 runtimebroker.exe 실행하는 Nvidia 디바이스가 원인일 수 있습니다. 이 문제를 해결하려면 " 어떻게 할까요?[새 프로그램에 대한 Optimus 설정을 만들](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)수 있나요? " 아래의 지침을 따르세요. C:\windows\system32\runtimebroker.exe 추가하고 "통합 그래픽" 프로세서에서 강제로 실행하려면 입니다. 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Windows Mixed Reality 사용하는 경우 내 Wi-Fi 느려집니다.

2.4GHz Wi-Fi 연결을 사용하는 경우 모션 컨트롤러로 인해 Wi-Fi 속도가 느려질 수 있습니다.

* 5GHz Wi-Fi 연결로 전환합니다(사용 가능한 경우). [자세히 알아보기](https://support.microsoft.com/help/4000461).
* 별도의 Bluetooth 어댑터를 사용하여 모션 컨트롤러를 PC에 연결합니다. [권장 어댑터 를 참조하세요.](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>PC를 연결하고 요금을 청구하라는 메시지가 표시됩니다. 이유가 무엇일까요?

랩톱을 사용하는 경우 WINDOWS MIXED REALITY PC가 완전히 청구되고 전원이 연결되어 있을 때 가장 잘 작동합니다.

## <a name="what-is-the-experience-options-setting"></a>환경 옵션 설정이란?

**설정 > Mixed Reality > 헤드셋 표시 > 환경 옵션을** 사용하면 Windows Mixed Reality 성능 설정을 변경할 수 있습니다. 이렇게 하면 다양한 콘텐츠에서 하드웨어 구성에 가장 적합한 환경을 선택할 수 있습니다. 다음 세 가지 환경 옵션 중에서 선택할 수 있습니다.
* 자동: Windows Mixed Reality 하드웨어 구성에 가장 적합한 환경을 결정합니다. 대부분의 사람들에게 이 선택으로 시작하는 것이 가장 좋습니다.
* 60Hz: 새로 고침 속도를 60Hz로 설정하고 Mixed Reality 포털 비디오 캡처 및 미리 보기와 같은 특정 기능을 해제합니다.
* 90Hz: 새로 고침 속도를 90Hz로 설정합니다.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Windows Mixed Reality 지원되는 언어

Windows Mixed Reality 다음 언어로 제공됩니다.

* 중국어 간체(중국)
* 영어(호주)
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

PC가 다른 언어로 설정된 경우 Windows Mixed Reality 사용할 수 있습니다. 그러나 인터페이스는 영어(미국)로 표시되고 음성 명령과 받아쓰기 는 사용할 수 없습니다. Windows Mixed Reality 화상 키보드는 영어(미국)입니다. 다른 언어로 텍스트를 입력하려면 PC에 연결된 물리적 키보드를 사용합니다. 위에 나열된 지원되는 Windows Mixed Reality 언어 중 하나에서 받아쓰기를 사용할 수도 있습니다. 화면 키보드에서 마이크를 선택하기만 하면 됩니다.

Windows Mixed Reality 음성 명령 또는 받아쓰기 기능 없이 다음 언어로도 사용할 수 있습니다.
* 중국어 번체(대만 및 홍콩)
* 네덜란드어(네덜란드)
* 한국어(한국)
* 러시아어(러시아)

## <a name="i-have-questions-about-my-headset-hardware"></a>헤드셋 하드웨어에 대한 질문이 있습니다.

헤드셋에 대한 자세한 내용은 제조업체에 문의하세요. 상자에 제품 가이드가 있거나 제조업체의 웹 사이트를 사용해 볼 수 있습니다.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Windows Mixed Reality 제거할 어떻게 할까요? 있나요?

1. PC에서 헤드셋 연결을 끊습니다.
2. Windows Mixed Reality Portal을 닫습니다.
2. 시작 **> 설정 > Mixed Reality** 이동하여 "제거"를 선택합니다.

헤드셋 사용을 다시 시작할 준비가 되면 헤드셋을 연결하면 Windows Mixed Reality Portal에서 설치를 안내합니다.

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>"Windows Mixed Reality 제거를 완료할 수 없습니다." 메시지가 표시됩니다.

사용자 환경에 대한 정보를 포함한 일부 파일은 여전히 컴퓨터에 있을 수 있습니다. 이로 인해 나중에 Windows Mixed Reality 다시 설치하기로 결정한 경우 문제가 발생할 수 있습니다. 레지스트리를 수정하고 Windows PowerShell 사용하여 명령을 실행하여 PC에서 나머지 Windows Mixed Reality 정보를 수동으로 제거할 수 있습니다. _레지스트리를 잘못 수정하면 심각한 문제가 발생할 수 있습니다. 이러한 단계를 신중하게 수행해야 합니다. 추가 보호의 경우 문제가 발생할 경우 복원할 수 있도록 수정하기 전에 레지스트리를 백업합니다._ 자세한 내용은 [Windows 레지스트리를 백업 및 복원하는 방법을 참조하세요.](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows) 

다음 명령을 사용하여 혼합 현실 Windows 제거하려면 다음을 수행합니다.
1. PC를 다시 시작합니다.
2. **검색** 상자에 "regedit"을 입력한 다음, "예"를 선택합니다.
3. 다음 레지스트리 값을 제거합니다.
   <ul>
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>"FirstRunSucceeded"를 삭제합니다.</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>"PreferDesktopSpeaker" 및 "PreferDesktopMic"을 삭제합니다.</li> 
    <li><b> &gt; 설정\Holographic</b>을HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore"DisableSpeechInput"을 삭제합니다. 참고: HHKEY_CURRENT_USER 사용된 PC의 모든 사용자 계정에 대해 Windows Mixed Reality 레지스트리 항목을 삭제해야 합니다.</li> 
    <li><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>"DeviceID" 및 "Mode"를 삭제합니다.</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>"OnDeviceLearningCompleted"를 삭제합니다.</li> 
   </ul>
4. 다음 레지스트리 키를 제거합니다. <ul>
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></li><br/></ul>
5. 레지스트리 편집기를 닫습니다.
6.**C:\Users\user name\AppData\Local\Packages\Microsoft.Windows 이동합니다. HolographicFirstRun_cw5n1h2txyewy\LocalState를** 만들고 "RoomBounds.json"을 삭제합니다. Windows Mixed Reality 사용한 각 사용자에 대해 이 작업을 반복합니다.
7. 관리자 cmd 프롬프트를 열고 **C:\ProgramData\Windows HolographicDevices\SpatialStore\HoloLensSensors** 로 이동합니다. "HeadTracking data" 폴더의 내용을 삭제합니다(폴더 자체는 삭제하지 않음).
8."검색 상자"에 "powershell"을 입력하고 "Windows PowerShell"을 마우스 오른쪽 단추로 클릭한 다음 "관리자 권한으로 실행"을 선택합니다.
9.Windows PowerShell: <ul>
   <li>명령 프롬프트에서 <b>Dism /online /Get-Capabilities</b>를 복사하여 붙여넣은 다음 Enter 키를 누릅니다.</b></li> 
   <li>아날로그.Holographic.Desktop으로 시작하는 기능 ID를 복사합니다. 해당 항목이 없으면 항목이 설치되지 않으며 10단계로 건너뛸 수 있습니다.</li> 
   <li>다음 명령 프롬프트를 복사하여 붙여넣은 다음, Enter 키를 누릅니다. <b>Dism /online /Remove-Capability /CapabilityName: 마지막 단계에서 복사한 기능 ID</b></li>
   </ul>
10. PC를 다시 시작합니다.

