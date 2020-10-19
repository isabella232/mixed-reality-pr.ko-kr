---
title: Windows Mixed Reality 최소 PC 하드웨어 호환성 지침
description: Windows Mixed Reality와의 호환성을 위한 최소 PC 시스템 요구 사항을 요약 하는 차트입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 울트라, compatible, compatibility, system 요구 사항, PC
appliesto:
- Windows 10
ms.openlocfilehash: e21d2d18edbf2c94d156f14fa8c2598822a8bc7a
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174369"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality 최소 PC 하드웨어 호환성 지침

## <a name="features-and-experiences"></a>기능 및 환경

Windows 10은 windows Mixed Reality와 Windows Mixed Reality를 모두 구동 합니다. 사용자가 경험 하는 버전은 PC 하드웨어에 따라 달라 집니다.

Windows Mixed Reality를 사용 하는 경우 몇 가지 추가 기능과 기능을 얻을 수 있습니다.

* 시각적 개체와 더 높은 새로 고침 빈도 (초당 90 프레임)를 표시 합니다.
* 그래픽이 많은 게임을 비롯 한 더 많은 앱 및 환경
* 혼합 현실에 표시 되는 내용을 보여 주는 ' ' 미러 ' ' 창이 바탕 화면에 있습니다.
* 혼합 현실 환경의 비디오와 사진을 기록 하 고 공유 합니다.

## <a name="minimum-pc-hardware-guidelines"></a>최소 PC 하드웨어 지침

Windows Mixed reality를 사용 하는 최상의 경험을 위해 windows mixed reality 울트라 환경을 제공할 수 있는 새로운 [Windows 혼합 현실 지원 pc](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 또는 Windows 혼합 현실 호환 pc부터 시작 하세요. Windows Mixed Reality는 더 높은 새로 고침 속도, 더 많은 앱 및 경험을 포함 하 여 더 많은 그래픽을 많이 사용 하는 뛰어난 시각적 개체를 제공 합니다. 즉, 데스크톱에서 Windows Mixed Reality 경험을 미러링 하 고 다른 사람들과 환경을 녹화 하 고 공유할 수 있는 기능을 제공 합니다. 

PC에서 Windows Mixed Reality를 실행할 수 있는지 확인 하려면 아래 하드웨어 지침을 검토 하 고 [혼합 현실 포털 앱](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M)을 실행 하세요.

정확한 설정에 따라 성능이 달라 집니다. 또한 사용 중인 Windows Mixed Reality 모던 헤드셋에 적합 한 [포트가](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) PC에 있는지 확인 해야 합니다.

>[!NOTE]
>개발 Pc에 대 한 지침이 혼합 현실 앱을 실행 하는 소비자 Pc 보다 높습니다. 혼합 현실 개발자 라면 [권장 개발 PC 사양을 참조](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)하세요.


## <a name="mixed-reality-portal-app"></a>혼합 현실 포털 앱

혼합 현실 포털은 PC가 Windows Mixed Reality를 실행할 준비가 되었는지 확인 하는 가장 좋은 방법입니다. 

<a href="https://www.microsoft.com/store/productid/9ng1h8b3zc7m"><img alt="Download Mixed Reality Portal" src="images/WMR-PC-Check-app.png"/></a>

앱을 실행 한 후에는 다음 메시지 중 하나를 받게 됩니다.
* **잘 진행 하 고 있습니다.** PC는 Windows Mixed Reality를 실행 하는 데 필요한 기능을 제공 합니다.
* **에서는 일부 기능을 지원 합니다.** 이 PC는 Windows Mixed Reality를 실행할 수 있지만 일부 기능이 제한 될 수 있습니다.
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

 [혼합 현실 포털 결과에 대 한 도움말 보기](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)

## <a name="compatibility-guidelines"></a>호환성 지침
> [!IMPORTANT]
> Microsoft는 이러한 Windows Mixed Reality PC 호환성 지침을 업데이트 하 고 추가 하 고 수정 하 고 있습니다. 최신 지침 및 요구 사항은 정기적으로 다시 확인 하세요.

**HP 반향 호환 사양**<br>
더 높은 해상도로 인해 다음 요구 사항은 HP 반향 G1 & G2 제품 라인에 적용 되어 90 Hz, 전체 해상도 환경을 최적화 합니다. 

<ul>
<li> Intel Core i5, i7, Intel 크 크 E3-1240 v5 (동급 이상). AMD Ryzen 5 동급 이상 </li>
<li> NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, 동급 이상 </li> 
<li> 메모리: 8gb RAM 이상 </li> 
<li> 1x 디스플레이 포트 1.3 </li> 
<li> 전원 공급 (또는 포함 된 전원 어댑터)이 포함 된 1x USB 3.0 유형</li>
<li> Windows 10 2019 년 5 월 업데이트 이상 </li>
</ul>

**기타 모든 WMR 호환 헤드셋** <br>
다른 모든 HMD의 경우 다음 요구 사항을 참조 하세요. 

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 울트라 Pc</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality Pc</th>
</tr><tr>
    <td style="vertical-align: middle">운영 체제</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 RS3 (Windows 10 용 작성자) 업데이트 (영문) () 이상-Home, Pro, Business, 교육용<br/>    (<b>참고</b>: N 버전 또는 Windows 10 Pro In S 모드에서는 지원 되지 않음)</td>
</tr><tr>
    <td style="vertical-align: middle">프로세서</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (4 세대), 쿼드 코어 (또는 더 좋음) <br>AMD Ryzen 5 1400 3.4 Ghz (데스크톱), 쿼드 코어 (또는 더 좋음)</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (7 세대 모바일), Intel Hyper-Threading 기술을 사용 하도록 설정 된 듀얼 코어 <br>AMD Ryzen 5 1400 3.4 Ghz (데스크톱), 쿼드 코어 (또는 더 좋음)</td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8GB DDR3-1600MHZ 이상</td>
    <td style="vertical-align: middle; text-align: center;">8GB DDR3-1600MHZ 듀얼 채널 (또는 더 좋음)</td>
</tr><tr>
    <td style="vertical-align: middle">사용 가능한 디스크 공간</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">10gb 이상</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">10gb 이상</td>
</tr><tr>
    <td style="vertical-align: middle">그래픽 카드</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul> 
            <li>NVIDIA GTX 1060 이상 (이상) DX12 지원 불연속 GPU</li>
            <li>AMD RX 470/570 이상 DX12 지원 불연속 GPU </li>
            </ul>     
            <b>참고:</b> GPU는 PCIe 3.0 x4 + 링크 슬롯에서 호스팅되어야 합니다. </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>통합 Intel HD Graphics 620 이상 (이상) DX12 지원 <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">되는 통합 GPU (모델이 더 큰지 확인)</a></li>
        <li>NVIDIA MX150 이상 (이상) 개별 GPU</li>
        <li>Nvidia GeForce GTX 1050 불연속 GPU</li>
        <li>Nvidia 965M 불연속 GPU</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>참고:</b> HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx 및 이거나 6xxx와 같은 구형 Intel Gpu는 지원 되지 않습니다.
    </td>
</tr><tr>
    <td style="vertical-align: middle">그래픽 드라이버</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">WDDM (Windows Display Driver Model) 2.2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">그래픽 디스플레이 포트</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2.0 또는 DisplayPort 1.2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1.4 또는 DisplayPort 1.2</td>
</tr><tr>
    <td style="vertical-align: middle">표시</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">연결 된 외부 또는 통합 VGA (800x600) 표시 (또는 더 좋음)</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">USB 연결</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">USB 3.0 유형-A </td>
</tr><tr>
    <td style="vertical-align: middle">Bluetooth 연결 ( <a href="controllers-in-wmr.md">동작 컨트롤러</a>의 경우)</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Bluetooth 4.0</td>
</tr><tr>
    <td style="vertical-align: middle">예상 헤드셋 프레임 속도</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60 Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">전원</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 (유형 A) 포트</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 (유형 A) 포트</td>
</tr>
</table>



**추가 정보:**
* 더 큰 랩톱 (최소 15 개의 화면이 포함 된)이 가장 효과적으로 수행 됩니다.
* 최상의 환경을 위해 8 번째 Gen Intel® Core™ 또는 7 세대 Intel® Core™ i5 프로세서를 권장 합니다.
* 하이브리드 그래픽 구성은 Windows Mixed Reality Ultra과만 호환 됩니다. 하이브리드 구성의 불연속 그래픽 어댑터는 개별 그래픽 어댑터에 대 한 Windows Mixed Reality 지침에 나열 된 모든 요구 사항을 충족 해야 합니다.
* Windows Mixed Reality를 실행 해야 하는 불연속 그래픽 카드가 있는 경우에는 기본적으로 60 Hz (초당 60 프레임)의 새로 고침 빈도를 사용 하 고, 전체 크기의 DisplayPort를 사용 하는 HDMI 2.0 어댑터를 사용 하 여 헤드셋을 연결 하 고 90 Hz 새로 고침 빈도를 사용 하도록 설정 합니다.
* 다른 헤드셋은 다른 하드웨어 포트를 요구할 수 있으므로, 사용자의 컴퓨터에 헤드셋에 연결 하는 [데 필요한](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) 올바른 포트나 어댑터가 있는지 확인 하세요.

>[!NOTE]
>확인 된 최소 사양을 충족 하지 않는 불연속 및 통합 그래픽 하드웨어는 Windows Mixed Reality에서 테스트, 확인 또는 최적화 되지 않았으며 제대로 작동 하지 않거나 전혀 작동 하지 않을 수 있습니다.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality 및 Surface

Surface 장치에서 Windows Mixed Reality 환경을 최대한 활용 하려면 NVIDIA GeForce GTX 1060 및 16GB의 RAM을 사용 하 여 구성 된 SurfaceBook 2 (15 ")를 사용 하는 것이 좋습니다.  이 구성은 모든 Windows Mixed Reality 기능 @ 90Hz를 지원 하 고 Windows Mixed Reality의 직장 배지가 달린 테스트 및 테스트를 지원 합니다.  Surface Book 2 (13 "), Surface Studio, surface 랩톱 및 Surface Pro (2017)는 Intel Core i5 CPU (또는 더 나은) 및 최소 8GB의 RAM을 사용 하 여 구성 된 경우 일부 Windows Mixed Reality 기능을 지원 합니다.

**요구 사항:**
* Surface 제품은 Windows Mixed Reality와 호환 되도록 드라이버 업데이트가 필요 합니다. 이러한 드라이버는 **설정 > 업데이트 및 보안 > 업데이트 확인**으로 이동 하 여 화면에 설치할 수 있습니다.
* Surface 제품은 비디오 포트 (Surface PC에 따라 미니 DisplayPort 또는 USB-C)의 [어댑터](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) 를 Windows Mixed Reality 헤드셋의 HDMI 2.0에 필요 합니다. HDMI AV 어댑터에 Mini-DisplayPort 최신 버전의 Surface는 HDMI 2.0와 호환 됩니다 (이전 버전은 그렇지 않음). 마찬가지로, <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">Hdmi 어댑터와 Hdmi 어댑터</a> 는 hdmi 2.0와도 호환 됩니다.

>[!WARNING]
>일부 미니 DisplayPort 또는 USB-C에서 HDMI 어댑터는 HDMI 2.0을 지원 하지 않습니다. 모든 어댑터에서 명시적인 "HDMI 2.0" 호환성 또는 "4K" 호환성을 확인 하는 것이 좋습니다.

Windows Mixed Reality의 Surface 호환성에 대 한 자세한 내용은 아래 표에 나와 있습니다.

<table>
    <tr>
        <th> Surface 장치 </th><th> Windows Mixed Reality 기능이 지원 되나요? </th><th> 권장 구성 </th><th> 참고</th>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (원래)/Surface Pro 2 </td><td style="vertical-align: middle"> 없음 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro 3 </td><td style="vertical-align: middle"> 없음 </td><td> </td><td></td>
    </tr>
(Windows 10 Pro가 설치 된 경우) <tr>
        <td style="vertical-align: middle"> Surface Pro 4 </td><td style="vertical-align: middle"> 없음 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface 3 </td><td style="vertical-align: middle"> 없음 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book </td><td style="vertical-align: middle"> 없음 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> 성능 기반을 포함 하는 Surface Book </td><td style="vertical-align: middle"> 없음 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Go </td><td style="vertical-align: middle"> 없음 </td><td> </td><td></td>
    </tr>
<tr>
        <td style="vertical-align: middle"> Surface Book 2 (15 &quot; ) </td><td style="vertical-align: middle"> 전체 </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1060/16GB의 RAM </td>
        <td>
            <ul>
                <li><b>권장</b>: Surface 장치에서 Windows Mixed Reality 환경을 최대한 활용 하려면 NVIDIA GeForce gtx 1060 및 16GB의 RAM을 사용 하 여 구성 된 SurfaceBook 2 15를 사용 하는 것이 좋습니다.  이 구성은 Windows Mixed Reality로 테스트 되 고 직장 배지가 달린 모든 Windows Mixed Reality 기능을 지원 하 고 광범위 한 호환 앱과 게임을 활용할 수 있도록 합니다.</li>
                <li>NVIDIA GeForce GTX 1060 불연속 GPU는 Windows Mixed Reality Ultra @ 90Hz 환경을 제공 합니다.</li><br/>                <li>최상의 성능을 위해 Surface Book 2 용으로 특별히 릴리스된 Nvidia 그래픽 드라이버를 사용 하세요. 최신 드라이버는 Nvidia&#39;s 웹 사이트에서 사용할 수 있지만 테스트 되지 않았습니다.</li><br/>                <li><a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">SURFACE USB-C에서 HDMI 어댑터를</a> 요구 합니다 (다른 어댑터는 작동할 수 있지만 테스트 되지 않음).</li>
                <li><b>Surface dock에 대 한 참고</b>: surface dock의 전원 공급 장치 제한으로 인해 Windows Mixed Reality에서는 surface s 2를 사용 하 여 표면 도크를 사용 하는 것이 공식적으로 지원 되지 않습니다.</li><br/>                <li><b>Windows 10 버전 1803에 대 한 참고</b>: Windows 10 버전 1803을 다시 실행 하는&#39;경우 최신 성능 수정이 있는지 확인 하려면 OS 빌드 17134.137 이상 (KB4284848에 의해 설치 됨)을 다시&#39;확인 하세요. 자세한 내용은 <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>에 대 한 릴리스 정보를 참조 하세요.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book 2 (13.5 &quot; ) </td><td style="vertical-align: middle"> Partial </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1050/16GB의 RAM </td>
        <td>
            <ul>
                <li><b>참고</b>: Surface Book 2 (13 ")는 Windows mixed reality의 직장 배지가 달린가 아니지만 제한 된 수의 호환 앱과 게임을 사용할 수 있는 일부 Windows Mixed reality 기능을 지원 합니다.  성능은 사용자의 구성에 따라 달라 집니다.</li>
                <li>Intel Core i5/Intel HD Graphics 620 통합 GPU를 사용 하는 구성은 Windows 혼합 현실 @ 60Hz 환경을 제공 합니다.</li>
                <li>Intel Core i7/NVIDIA GeForce GTX 1050 불연속 GPU를 사용 하는 구성은 Windows Mixed Reality @ 90Hz 환경을 제공 합니다.</li>                       <li>최상의 성능을 위해 Surface Book 2 용으로 특별히 릴리스된 Nvidia 그래픽 드라이버를 사용 하세요. 최신 드라이버는 Nvidia&#39;s 웹 사이트에서 사용할 수 있지만 테스트 되지 않았습니다.</li>
                <li><a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">SURFACE USB-C에서 HDMI 어댑터를</a> 요구 합니다 (다른 어댑터는 작동할 수 있지만 테스트 되지 않음).</li>
                <li><b>Surface dock에 대 한 참고</b>: surface dock의 전원 공급 장치 제한으로 인해 Windows Mixed Reality에서는 surface s 2를 사용 하 여 표면 도크를 사용 하는 것이 공식적으로 지원 되지 않습니다.</li>
                <li><b>Windows 10 버전 1803에 대 한 참고</b>: Windows 10 버전 1803을 다시 실행 하는&#39;경우 최신 성능 수정이 있는지 확인 하려면 OS 빌드 17134.137 이상 (KB4284848에 의해 설치 됨)을 다시&#39;확인 하세요. 자세한 내용은 <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>에 대 한 릴리스 정보를 참조 하세요.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Studio </td><td style="vertical-align: middle"> Partial </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GeForce GTX 980m/16GB RAM </td>
        <td>
            <ul>
                <li><b>참고</b>: Surface Studio는 Windows mixed reality에 직장 배지가 달린 되지 않지만 몇 가지 Windows Mixed reality 기능을 지원 하 여 제한 된 수의 호환 되는 앱과 게임을 사용할 수 있도록 합니다.  성능은 사용자의 구성에 따라 달라 집니다.</li>
                <li>NVIDIA GeForce GTX 965m을 사용 하는 구성은 Windows 혼합 현실 @ 60Hz 환경을 제공 합니다.</li>
                <li>NVIDIA GeForce GTX 980m을 사용 하는 구성은 Windows 혼합 현실 @ 90Hz 환경을 제공 합니다.</li>
                <li>HDMI 2.0 어댑터에 대 한 Surface 미니 DisplayPort (다른 어댑터가 작동할 수 있지만 테스트 되지 않음)</li>
                <li>Windows Mixed Reality 헤드셋은 "+" 기호를 사용 하 여 USB 포트에 연결 해야 합니다.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (2017) </td><td style="vertical-align: middle"> Partial </td><td style="vertical-align: middle"> Intel Core i7/Intel® Iri™와 그래픽 640/16GB RAM </td>
        <td>
            <ul>
                <li><b>참고</b>: Surface Pro (2017)는 Windows mixed reality에 직장 배지가 달린 되지 않지만, 일부 Windows Mixed reality 기능을 지원 하므로 제한 된 수의 호환 되는 앱과 게임을 사용할 수 있습니다.  성능은 사용자의 구성에 따라 달라 집니다.</li>
                <li>Intel Core M3/Intel HD Graphics 615 통합 GPU를 사용 하는 구성은 <b>지원 되지 않습니다</b> .</li>
                <li>Intel Core i5/Intel HD Graphics 620 통합 GPU를 사용 하는 구성은 Windows 혼합 현실 @ 60Hz 환경을 제공 합니다.</li>
                <li>Intel Core i7/Intel® Iri™ 및 Graphics 640 integrated GPU를 사용 하는 구성은 Windows Mixed Reality @ 60Hz 환경을 제공 합니다.</li><br/><li>HDMI 2.0 어댑터에 대 한 Surface 미니 DisplayPort 필요 합니다 (다른 어댑터는 작동할 수 있지만 테스트 되지 않음).</li>
                <li>사용 중 <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">성능 슬라이더가</a> "최상의 성능"으로 설정 되어 있어야 합니다.</li>
            </ul>
        </td>
    </tr><br/>    <tr>
        <td style="vertical-align: middle"> Surface Laptop </td><td style="vertical-align: middle"> Partial </td><td style="vertical-align: middle"> Intel Core i7/Intel® Iri™와 그래픽 640/16GB RAM </td>
        <td>
            <ul>
                <li><b>참고</b>: Surface 노트북은 Windows mixed reality에 직장 배지가 달린 되지 않지만, 일부 Windows Mixed reality 기능을 지원 하므로 제한 된 수의 호환 되는 앱과 게임을 사용할 수 있습니다.  성능은 사용자의 구성에 따라 달라 집니다.</li>
                <li>Intel Core M3/Intel HD Graphics 615 통합 GPU를 사용 하는 구성은 <b>지원 되지 않습니다</b> .</li>
                <li>Intel Core i5/Intel HD Graphics 620 통합 GPU를 사용 하는 구성은 Windows 혼합 현실 @ 60Hz 환경을 제공 합니다.</li>
                <li>Intel Core i7/Intel® Iri™ 및 Graphics 640 integrated GPU를 사용 하는 구성은 Windows Mixed Reality @ 60Hz 환경을 제공 합니다.</li><br/><li>HDMI 2.0 어댑터에 대 한 Surface 미니 DisplayPort 필요 합니다 (다른 어댑터는 작동할 수 있지만 테스트 되지 않음).</li>
                <li>사용 중 <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">성능 슬라이더가</a> "최상의 성능"으로 설정 되어 있어야 합니다.</li>
            </ul>
        </td>
    </tr>
</table>

## <a name="see-also"></a>참고 항목
* [커뮤니티에 질문하기](https://answers.microsoft.com)
* [지원 문의](https://support.microsoft.com/contactus/)
* [Windows Mixed Reality 지원 Pc의 권장 어댑터](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
