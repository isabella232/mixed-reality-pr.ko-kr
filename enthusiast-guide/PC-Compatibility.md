---
title: Windows Mixed Reality PC 검사 앱
description: Windows Mixed Reality pc 검사 앱을 찾고 사용 하 여 Windows Mixed Reality 헤드셋을 구입 하기 전에 pc의 호환성을 테스트 하는 방법입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed reality, 가상 현실, VR, MR, 호환, 호환성, PC, 시스템 요구 사항
appliesto:
- Windows 10
ms.openlocfilehash: 463e7dfc2c95ed9efc70a87ebbb0dac08b134251401a1114f3b9a364aa197073
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188050"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Windows Mixed Reality PC 검사 앱

**[Windows Mixed Reality pc 검사](https://www.microsoft.com/store/p/windows-mixed-reality-pc-check/9nzvl19n7cnc)** 앱은 pc를 Windows Mixed Reality 실행할 준비가 되었는지 확인 하는 가장 좋은 방법입니다. Windows Mixed Reality pc 검사 앱은 Windows 10 버전 1607 이상이 설치 된 pc 에서만 작동 합니다. Windows 버전을 확인 하려면 검색 표시줄에 "winver"를 입력 하 고 명령을 실행 합니다. 1607 이전의 Windows 10 버전에서는 앱이 스토어에 계속 표시 되지만를 설치 하려고 하면 오류가 발생 합니다.

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

앱을 실행 한 후에는 다음 메시지 중 하나를 받게 됩니다.

* **잘 진행 하 고 있습니다.** Windows Mixed Reality를 실행 하는 데 사용 하는 PC가 있습니다.
* **거의 끝났습니다.** 이 PC는 Windows Mixed Reality을 실행할 수 있지만 일부 기능이 제한 될 수 있습니다.
* **혼합 현실를 실행할 수 없습니다.** 이 PC는 Windows Mixed Reality를 실행 하는 데 필요한 최소 요구 사항을 충족 하지 않습니다.

그런 다음 필요한 하드웨어, 드라이버 및 운영 체제에 대 한 PC의 분석을 가져옵니다.
![Windows Mixed Reality PC 확인 스크린샷](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>아이콘</th><th>의미</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">PC가 필요한 항목을 전달 합니다.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">지정 된 요구 사항에 대 한 PC에 문제가 있을 수 있습니다. 문제가 발생 하는 경우 PC의 문제를 해결 하거나 업그레이드 해야 할 수 있습니다.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">PC가 지정 된 항목의 요구 사항을 충족 하지 않습니다.</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>Windows Mixed Reality PC 검사 결과에 대 한 도움말 보기

Windows Mixed Reality을 설정 하거나 컴퓨터에서 Windows Mixed Reality PC 검사 앱을 실행할 때 호환성 보고서를 받게 됩니다. 다음은 표시 될 수 있는 내용에 대 한 세부 정보입니다.

### <a name="youre-good-to-go"></a>![이동 하는 것이 좋습니다.](images/glyph-succeeded.png)

좋은 소식 — PC가 Windows Mixed Reality를 실행할 수 있습니다. 컴퓨터 하드웨어와 구성 사이에 여전히 변형이 있다는 점에 유의 하세요. 혼합 현실 환경은 모든 PC에서 동일 하지 않을 수 있습니다.

>[!NOTE]
>"이 하드웨어 구성은 Windows Mixed Reality와 작동할 수 있지만 아직 테스트 되지 않았습니다." 라는 메시지가 표시 되 면 긴 세션의 Windows Mixed Reality를 실행할 때 몇 가지 성능 문제가 발생할 수 있습니다.

### <a name="youre-nearly-there"></a>![거의 완료 되었습니다.](images/glyph-warning.png)

PC에서 Windows Mixed Reality를 실행할 수 있어야 하지만 최상의 환경을 제공 하지 않을 수 있습니다. 그래픽이 지연 될 수 있으며 일부 앱 및 게임은 제대로 실행 되지 않을 수 있으며 일부는 실행 되지 않을 수 있습니다.

다음은 표시 될 수 있는 메시지와 이러한 메시지에 대해 수행할 작업입니다.

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>이 PC에는 단일 채널 RAM이 있는 통합 그래픽 카드가 있습니다.

통합 그래픽 카드는 이중 채널 RAM이 있는 pc에서 최상의 Windows Mixed Reality 환경을 제공 합니다. 성능 문제가 발생 하면 다음을 수행 합니다.

* [호환 되는 개별 그래픽 카드](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)를 설치 합니다.
* 추가 RAM 스틱을 설치 하 여 이중 채널 RAM을 만듭니다.
* [호환 되는 PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)로 전환 합니다.

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>이 PC에는 호환 되지 않는 PCIe 링크로 하이브리드 그래픽 구성이 있습니다.

PCIe는 *주변 구성 요소 상호 연결 Express* 를 나타냅니다. PC에서 그래픽 카드와 통신 하는 데 사용 하는 연결입니다. 구성이 작동할 수 있지만 문제가 발생 하는 경우 [호환 되는 PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)로 전환 해야 합니다.

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>이 PC의 그래픽 드라이버는 Windows Mixed Reality에서 제대로 작동 하지 않을 수 있습니다.

문제가 발생 하는 경우 Windows 업데이트를 사용 하 여 새 그래픽 드라이버를 다운로드 하거나 (**> 설정 > 업데이트 & 업데이트 확인**), PC 제조업체나 그래픽 카드 제조업체의 웹 사이트로 이동 하세요.

그래도 작동 하지 않으면 호환 되는 [그래픽 카드](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 를 추가 하거나 호환 되는 [PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)로 전환 해야 합니다.

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>이 PC의 프로세서는 Windows Mixed Reality에서 제대로 작동 하지 않을 수 있습니다.

이 PC의 프로세서는 코어가 충분 하지 않기 때문에 Windows Mixed Reality에서 제대로 작동 하지 않을 수 있습니다. Windows Mixed Reality 제대로 실행 되지 않으면 [호환 되](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 는 PC로 업데이트 하거나 [호환 되는 PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)로 전환 합니다.

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>이 PC에는 호환 되는 USB 구성이 없을 수 있습니다.

Windows Mixed Reality 실행 하는 데 문제가 발생 하는 경우:

* 사용 가능한 경우 헤드셋을 다른 USB 포트에 연결 합니다.
* 그래도 작동 하지 않으면 PC의 현재 USB 드라이버를 제거 하 고 Microsoft 드라이버를 다시 설치 합니다.

1. **시작** 을 선택한 다음 검색 상자에 **"장치 관리자"** 를 입력 합니다.
1. 결과에서 **장치 관리자** 를 선택 합니다.
1. 범용 직렬 버스 컨트롤러의 범주를 확장 하 고 나열 된 장치를 확인 한 다음 호환 되지 않는 드라이버를 모두 제거 합니다. 
 * 장치 이름 끝에 "Microsoft"가 없는 "확장 가능 호스트 컨트롤러" 항목이 목록에 포함 되어 있으면 드라이버가 Windows Mixed Reality와 호환 되지 않습니다. 제거 해야 합니다. 드라이버를 제거 하려면 목록에서 장치를 마우스 오른쪽 단추로 클릭 하 고 **장치 제거** 를 선택 합니다. **이 장치에 대 한 드라이버 소프트웨어 삭제** 확인란을 선택 하 고 **제거** 를 선택 합니다.
 * 이름에 "Etron"가 포함 된 "확장 가능한 호스트 컨트롤러" 항목이 목록에 포함 되어 있으면 해당 USB 컨트롤러가 Windows Mixed Reality와 호환 되지 않습니다. PC에서 다른 USB 포트를 사용 하거나 다른 USB 3.0 호스트 컨트롤러를 구입 해야 합니다.
1. PC를 다시 시작 합니다. 
1. 장치 관리자로 돌아가서 확장 가능한 호스트 컨트롤러 항목을 다시 찾습니다. 이제 장치 이름 끝에 "Microsoft"가 표시 되 면 이동 하는 것이 좋습니다. 그렇지 않은 경우 제거 단계를 반복 하 여 Microsoft 이외의 다른 버전의 드라이버를 제거 합니다.
* 그래도 작동 하지 않으면 컴퓨터에 PCIe USB 카드를 추가 합니다.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>이 PC에는 컨트롤러에 대 한 Bluetooth 4.0가 없습니다.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>이 PC에는 자체 기반 USB 포트가 없습니다.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>이 PC는 작동 하지만 고성능 Intel® 프로세서를 사용 하는 최상의 환경을 제공 합니다.

### <a name="cant-run-mixed-reality"></a>![혼합 현실 실행 불가](images/glyph-error.png)

 [Windows Mixed Reality PC 검사 결과에 대 한 도움말 보기](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
