---
title: Windows Mixed Reality PC 호환성 지침
description: Windows Mixed Reality 호환성을 위한 최소 PC 시스템 요구 사항을 간략하게 설명하는 개요 차트입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Ultra, 호환 가능, 호환성, 시스템 요구 사항, PC
appliesto:
- Windows 10
ms.openlocfilehash: e73b00dcf8d6974f06c22c3b0ab0771a8e1a5969
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143348"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>최소 PC 하드웨어 호환성 지침 Windows Mixed Reality

## <a name="features-and-experiences"></a>기능 및 환경

Windows 10 다양한 PC 하드웨어 세트에서 다양한 헤드셋을 Windows Mixed Reality 수 있습니다.  PC의 성능에 따라 사용할 수 있는 환경이 결정됩니다.
고급 PC를 사용하면 몇 가지 추가 기능과 기능을 얻을 수 있습니다.

* 더 선명한 시각적 개체와 더 높은 새로 고침 빈도.
* 그래픽 집약적인 게임을 포함하여 더 많은 앱과 환경.
* 혼합 현실에 표시되는 내용을 보여 주는 바탕 화면의 '미러' 창
* 혼합 현실 환경의 비디오 및 사진을 녹화하고 공유합니다.

## <a name="minimum-pc-hardware-guidelines"></a>최소 PC 하드웨어 지침

아래 하드웨어 지침을 검토하고 Mixed Reality 포털 앱을 실행하여 PC가 [Windows Mixed Reality](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) 실행할 수 있는지 확인합니다.

성능은 정확한 설정에 따라 달라집니다. 또한 PC에 사용하려는 Windows Mixed Reality 몰입형 헤드셋에 [적합한 포트가](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 있는지 확인해야 합니다.

>[!NOTE]
>개발 PC에 대한 지침은 혼합 현실 앱을 실행하는 소비자의 PC에 대한 지침보다 높습니다. 혼합 현실 개발자인 경우 [권장 개발 PC 사양을 참조하세요.](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)

## <a name="mixed-reality-portal-app"></a>앱 Mixed Reality 포털

[Mixed Reality 포털](https://www.microsoft.com/store/productid/9ng1h8b3zc7m) PC가 Windows Mixed Reality 실행할 준비가 되었는지 확인하는 가장 좋은 방법입니다.

앱을 실행하면 다음 메시지 중 하나가 표시됩니다.

* **잘 진행 하 고 있습니다.**  PC가 혼합 현실 게임 및 환경을 실행할 준비가 되었습니다.
* **에서는 일부 기능을 지원 합니다.** PC에서 일부 혼합 현실 환경을 실행할 수 있습니다.
* **혼합 현실를 실행할 수 없습니다.** 이 PC는 Windows Mixed Reality를 실행 하는 데 필요한 최소 요구 사항을 충족 하지 않습니다.

그런 다음 필요한 하드웨어, 드라이버 및 운영 체제에 대 한 PC의 분석을 가져옵니다.
![Windows Mixed Reality PC 확인 스크린샷](images/screenshot-mr-pc-check.jpg)

<table>
<tr>
<th>아이콘</th><th>의미</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">PC가 필요한 항목을 전달 합니다.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">지정 된 요구 사항에 대 한 PC에 문제가 있을 수 있습니다. 여러 문제를 해결 하는 경우 PC의 문제를 해결 하거나 업그레이드 해야 할 수 있습니다.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">PC가 지정 된 항목의 요구 사항을 충족 하지 않습니다.</td>
</tr>
</table>

 [혼합 현실 포털 결과에 대 한 도움말 보기](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>호환성 지침

> [!IMPORTANT]
> Microsoft는 이러한 Windows Mixed Reality PC 호환성 지침을 업데이트 하 고 추가 하 고 수정 하 고 있습니다. 최신 지침 및 요구 사항은 정기적으로 다시 확인 하세요.

### <a name="high-resolution-headset-requirements"></a>고해상도 헤드셋 요구 사항

더 높은 해상도를 제공 하기 때문에 다음 요구 사항은 HP 반향 G1, G2 및 Omnicept 제품 라인에 적용 되어 90 Hz, 전체 해상도 환경을 최적화 합니다.

<ul>
<li> Intel Core i5, i7, Intel 크 크 E3-1240 v5 (동급 이상). AMD Ryzen 5 동급 이상 </li>
<li> NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, 동급 이상 </li>
<li> 메모리: 8gb RAM 이상 </li>
<li> 1x 디스플레이 포트 1.3 </li>
<li> 전원 공급 (또는 포함 된 전원 어댑터)이 포함 된 1x USB 3.0 유형</li>
<li> Windows 10 2019 년 5 월 업데이트 이상 </li>
</ul>

**기타 모든 WMR 호환 헤드셋** <br>
다른 모든 HMDs의 경우 다음 요구 사항을 참조 하세요.

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 90 Hz Pc</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 60Hz Pc</th>
</tr><tr>
    <td style="vertical-align: middle">운영 체제</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 RS3 (Windows 10 용 작성자) 업데이트 (영문) () 이상-Home, Pro, Business, 교육용<br/>    (<b>참고</b>: N 버전 또는 Windows 10 Pro In S 모드에서는 지원 되지 않음)</td>
</tr><tr>
    <td style="vertical-align: middle">프로세서</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (4 세대), 쿼드 코어 (또는 더 좋음) <br>AMD Ryzen 5 1400 3.4 Ghz (데스크톱), 쿼드 코어 (또는 더 좋음)</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (7 세대 모바일), Intel Hyper-Threading 기술을 사용 하도록 설정 된 듀얼 코어 <br>AMD Ryzen 5 1400 3.4 Ghz (데스크톱), 쿼드 코어 (또는 더 좋음)</td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8gb DDR3-1600MHZ 이상</td>
    <td style="vertical-align: middle; text-align: center;">8gb DDR3-1600MHZ 듀얼 채널 (또는 더 좋음)</td>
</tr><tr>
    <td style="vertical-align: middle">사용 가능한 디스크 공간</td>
    <td style="vertical-align: middle; text-align: center;">10gb 이상</td>
    <td style="vertical-align: middle; text-align: center;">10gb 이상</td>
</tr><tr>
    <td style="vertical-align: middle">그래픽 카드</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul>
            <li>NVIDIA GTX 1060 이상 DX12 지원 불연속 GPU</li>
            <li>AMD RX 470/570 이상 DX12 지원 불연속 GPU </li>
            </ul>
            <b>참고:</b> GPU는 PCIe 3.0 x4+ 링크 슬롯에서 호스트되어야 합니다. </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>통합 Intel HD Graphics 620 이상 DX12 지원 통합 <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">GPU(모델이 더 큰지 확인)</a></li>
        <li>NVIDIA MX150 이상 불연속 GPU</li>
        <li>Nvidia GeForce GTX 1050 불연속 GPU</li>
        <li>Nvidia 965M 불연속 GPU</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>참고:</b> HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx 및 6xxx와 같은 이전 Intel GPU는 지원되지 않습니다.
    </td>
</tr><tr>
    <td style="vertical-align: middle">그래픽 드라이버</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">WDDM(Windows Display Driver Model) 2.2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">그래픽 표시 포트</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2.0 또는 DisplayPort 1.2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1.4 또는 DisplayPort 1.2</td>
</tr><tr>
    <td style="vertical-align: middle">표시</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">연결된 외부 또는 통합 VGA(800x600) 디스플레이(이상)</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">USB 연결</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">USB 3.0 </td>
</tr><tr>
    <td style="vertical-align: middle">Bluetooth <a href="controllers-in-wmr.md">연결(모션 컨트롤러의</a>경우)</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Bluetooth 4.0</td>
</tr><tr>
    <td style="vertical-align: middle">헤드셋 프레임 속도 예상</td>
    <td style="vertical-align: middle; text-align: center;">90Hz</td>
    <td style="vertical-align: middle; text-align: center;">60Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">고급</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 포트</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 포트</td>
</tr>
</table>

**추가 정보:**

* 화면이 15개 이상인 대형 랩톱이 가장 좋습니다.
* 하이브리드 그래픽 구성은 Windows Mixed Reality 90Hz와만 호환됩니다. 모든 하이브리드 구성의 불연속 그래픽 어댑터는 불연속 그래픽 어댑터에 대한 Windows Mixed Reality 지침에 나열된 모든 요구 사항을 충족해야 합니다.
* Windows Mixed Reality 90Hz를 실행해야 하는 불연속 그래픽 카드가 있지만 기본적으로 60Hz(초당 60프레임) 새로 고침 속도를 사용하는 경우 HDMI 2.0 어댑터에 대한 전체 크기 DisplayPort를 사용하여 헤드셋을 연결하고 90Hz 새로 고침 속도를 사용하도록 설정합니다.
* 헤드셋에 따라 다른 하드웨어 포트가 필요할 수 있으므로 PC에 올바른 포트 또는 헤드셋에 연결하는 [데 필요한 어댑터가](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) 있는지 확인합니다.

>[!NOTE]
>확인된 최소 사양을 충족하지 않는 불연속 및 통합 그래픽 하드웨어는 Windows Mixed Reality 대해 테스트, 확인 또는 최적화되지 않았으며 제대로 또는 전혀 작동하지 않을 수 있습니다.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality 및 Surface

Surface 디바이스에서 최상의 Windows Mixed Reality 환경을 위해 NVIDIA GeForce GTX 1060GB 및 16GB RAM 이상으로 구성된 최신 SurfaceBook(15")을 권장합니다.  이 구성은 모든 Windows Mixed Reality 기능을 지원하며 Windows Mixed Reality 대해 테스트되었습니다.  최신 Surface Book(13.5"), Surface Studio, Surface Laptop 및 Surface Pro(2017)은 모두 Intel Core i5 CPU(이상) 및 8GB 이상의 RAM으로 구성된 경우 일부 Windows Mixed Reality 기능을 지원합니다.

**요구 사항:**

* Surface 제품은 드라이버 업데이트가 Windows Mixed Reality 호환되어야 합니다. 이러한 드라이버는 설정 > 업데이트 및 **보안 > 업데이트 확인으로** 가서 Surface에 설치할 수 있습니다.
* Surface 제품에는 비디오 포트(Surface PC에 따라 미니 디스플레이포트 또는 USB-C)에서 Windows Mixed Reality 헤드셋용 HDMI 2.0까지의 [어댑터가](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) 필요합니다. HDMI AV 어댑터에 대한 Surface Mini-DisplayPort 최신 버전은 HDMI 2.0과 호환됩니다(이전 버전은 그렇지 않습니다). 마찬가지로 Surface <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">USB-C-HDMI 어댑터도 HDMI</a> 2.0과 호환됩니다.

## <a name="see-also"></a>참고 항목

* [커뮤니티에 질문하기](https://answers.microsoft.com)
* [지원을 요청합니다.](https://support.microsoft.com/contactus/)
* [Windows Mixed Reality 지원 PC에 권장되는 어댑터](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
