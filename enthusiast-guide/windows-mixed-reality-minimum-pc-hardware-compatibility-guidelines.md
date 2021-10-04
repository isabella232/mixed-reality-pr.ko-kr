---
title: Windows Mixed Reality PC 호환성 지침
description: Windows Mixed Reality와의 호환성을 위한 최소 PC 시스템 요구 사항을 개략적으로 설명 하는 개요 차트입니다.
author: qianw211
ms.author: v-qianwen
ms.date: 09/22/2021
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 울트라, 호환, 호환성, 시스템 요구 사항, PC
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: af3228e76bc9ce54ef877b67e8e85a3bde25e140
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436735"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality 최소 PC 하드웨어 호환성 지침

![PC 호환성 주인공 이미지](images/pc-comp-hero.png)

## <a name="features-and-experiences"></a>기능 및 환경

Windows 10 및 Windows 11은 다양 한 PC 하드웨어 집합에서 다양 한 헤드셋에 Windows Mixed Reality 있습니다.  PC의 기능을 통해 어떤 환경을 사용할 수 있는지를 확인할 수 있습니다.
더 높은 최종 Pc를 사용 하면 몇 가지 추가 기능과 기능을 얻을 수 있습니다.

* 시각적 개체와 새로 고침 속도가 더 빠릅니다.
* 그래픽이 많은 게임을 비롯 한 더 많은 앱 및 환경
* 혼합 현실에 표시 되는 내용을 보여 주는 ' ' 미러 ' ' 창이 바탕 화면에 있습니다.
* 혼합 현실 환경의 비디오와 사진을 기록 하 고 공유 합니다.

## <a name="minimum-pc-hardware-guidelines"></a>최소 PC 하드웨어 지침

아래 하드웨어 지침을 검토 하 고 [혼합 현실 포털](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) 앱을 실행 하 여 PC가 Windows Mixed Reality를 실행할 수 있는지 확인 하세요.

정확한 설정에 따라 성능이 달라 집니다. 또한 사용 중인 모던 헤드셋 Windows Mixed Reality에 맞는 [포트가](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) PC에 있는지 확인 해야 합니다.

>[!NOTE]
>개발 Pc에 대 한 지침이 혼합 현실 앱을 실행 하는 소비자 Pc 보다 높습니다. 혼합 현실 개발자 라면 [권장 개발 PC 사양을 참조](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)하세요.

## <a name="mixed-reality-portal-app"></a>혼합 현실 포털 앱

[혼합 현실 포털](https://www.microsoft.com/store/productid/9ng1h8b3zc7m) 은 PC를 Windows Mixed Reality 실행할 준비가 되었는지 확인 하는 가장 좋은 방법입니다.

앱을 실행 한 후에는 다음 메시지 중 하나를 받게 됩니다.

* **잘 진행 하 고 있습니다.**  PC가 혼합 현실 게임 및 환경을 실행할 준비가 되었습니다.
* **에서는 일부 기능을 지원 합니다.** PC에서 일부 혼합 현실 환경을 실행할 수 있습니다.
* **혼합 현실를 실행할 수 없습니다.** 이 PC는 Windows Mixed Reality를 실행 하는 데 필요한 최소 요구 사항을 충족 하지 않습니다.

그런 다음 필요한 하드웨어, 드라이버 및 운영 체제에 대 한 PC의 분석을 가져옵니다.
![Windows Mixed Reality PC 확인 스크린샷](images/screenshot-mr-pc-check.jpg)

| 아이콘 | 의미 |
| --- | --- |
| <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /> | PC가 필요한 항목을 전달 합니다. |
| <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /> | 지정 된 요구 사항에 대 한 PC에 문제가 있을 수 있습니다. 여러 문제를 해결 하는 경우 PC의 문제를 해결 하거나 업그레이드 해야 할 수 있습니다. 
| <img alt="Error" width="30" height="30" src="images/glyph-error.png" /> | PC가 지정 된 항목의 요구 사항을 충족 하지 않습니다. |

 [혼합 현실 포털 결과에 대 한 도움말 보기](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>호환성 지침

> [!IMPORTANT]
> microsoft는 이러한 Windows Mixed Reality PC 호환성 지침을 업데이트 하 고, 추가 하 고, 수정 하 고 있을 것입니다. 최신 지침 및 요구 사항은 정기적으로 다시 확인 하세요.

### <a name="high-resolution-headset-requirements"></a>고해상도 헤드셋 요구 사항

더 높은 해상도를 제공 하기 때문에 다음 요구 사항은 HP 반향 G1, G2 및 Omnicept 제품 라인에 적용 되어 90 Hz, 전체 해상도 환경을 최적화 합니다.

- Intel Core i5, i7, Intel Xeon E3-1240 v5 (동급 이상). AMD Ryzen 5 동급 이상  
- NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, 동급 이상  
- 메모리: 8gb RAM 이상  
- 1x 디스플레이 포트 1.3  
- 전원 공급 (또는 포함 된 전원 어댑터)이 포함 된 1x USB 3.0 유형 
- Windows 10 2019 년 5 월 업데이트 이상  
 
**기타 모든 WMR 호환 헤드셋** <br>
다른 모든 HMDs의 경우 다음 요구 사항을 참조 하세요.

| | Windows Mixed Reality 90hz pc | Windows Mixed Reality 60hz pc |
| --- | --- | --- |
| 운영 체제 | Windows 10 Fall Creators Update (RS3) 이상-Home, Pro, Business, 교육용 <br/>    (<b>참고</b>: N 버전에서 지원 되지 않거나 S 모드의 Windows 10 Pro) |
| 프로세서 | Intel Core i5 4590 (4 세대), 쿼드 코어 (또는 더 좋음) <br> AMD Ryzen 5 1400 3.4 Ghz (데스크톱), 쿼드 코어 (또는 더 좋음) | Intel Core i5 7200U (7 세대 모바일), Intel Hyper-Threading 기술을 사용 하도록 설정 된 듀얼 코어 <br> AMD Ryzen 5 1400 3.4 Ghz (데스크톱), 쿼드 코어 (또는 더 좋음) |
| RAM | 8gb DDR3-1600MHZ 이상 | 8gb DDR3-1600MHZ 듀얼 채널 (또는 더 좋음) |
| 사용 가능한 디스크 공간 | 10gb 이상 | 10gb 이상 |
| 그래픽 카드| <ul> <li>NVIDIA GTX 1060 이상 (이상) DX12 지원 불연속 GPU </li> <li>AMD RX 470/570 이상 DX12 지원 불연속 GPU </li> </ul> <br> <b>참고:</b> GPU는 PCIe 3.0 x4 + 링크 슬롯에서 호스팅되어야 합니다. |  <ul>  <li>통합 Intel HD Graphics 620 이상 (이상) DX12 지원 <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">되는 통합 GPU (모델이 더 큰지 확인)</a></li> <li>NVIDIA MX150 이상 (이상) 개별 GPU</li> <li>Nvidia GeForce GTX 1050 불연속 GPU</li> <li>Nvidia 965M 불연속 GPU</li> <li>AMD Radeon RX 460/560</li> </ul> <b>참고:</b> HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx 및 이거나 6xxx와 같은 이전 버전의 Gpu는 지원 되지 않습니다. |
| 그래픽 드라이버 | Windows 디스플레이 드라이버 모델 (WDDM) 2.2 |  |
| [그래픽 디스플레이 포트](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | HDMI 2.0 또는 DisplayPort 1.2 | HDMI 1.4 또는 DisplayPort 1.2 |
| 표시 | 연결 된 외부 또는 통합 VGA (800x600) 표시 (또는 더 좋음) | 
| [USB 연결](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | USB 3.0 | |
| Bluetooth 연결 ( [동작 컨트롤러](controllers-in-wmr.md) 의 경우) | Bluetooth 4.0 | |
| 예상 헤드셋 프레임 속도 | 90 Hz | 60 Hz |
| 고급 | USB 3.0 포트 | USB 3.0 포트 |

**추가 정보:**

* 최소 15 개의 화면이 포함 된 더 큰 랩톱을 사용 하는 것이 가장 좋습니다.
* 하이브리드 그래픽 구성은 Windows Mixed Reality 90hz와만 호환 됩니다. 하이브리드 구성의 불연속 그래픽 어댑터는 개별 그래픽 어댑터에 대 한 Windows Mixed Reality 지침에 나열 된 모든 요구 사항을 충족 해야 합니다.
* 90hz Windows Mixed Reality 실행 해야 하는 개별 그래픽 카드가 있지만 기본적으로 60hz (60 프레임/초)의 새로 고침 빈도를 사용 하는 경우 HDMI 2.0 어댑터에 대 한 전체 크기의 DisplayPort를 사용 하 여 헤드셋을 연결 하 고 90hz 새로 고침 빈도를 사용 하도록 설정 합니다.
* 다른 헤드셋은 다른 하드웨어 포트를 요구할 수 있으므로, 사용자의 컴퓨터에 헤드셋에 연결 하는 [데 필요한](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) 올바른 포트나 어댑터가 있는지 확인 하세요.

>[!NOTE]
>확인된 최소 사양을 충족하지 않는 불연속 및 통합 그래픽 하드웨어는 Windows Mixed Reality 대해 테스트, 확인 또는 최적화되지 않았으며 제대로 또는 전혀 작동하지 않을 수 있습니다.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality 및 Surface

Surface 디바이스에서 최상의 Windows Mixed Reality 환경을 위해 NVIDIA GeForce GTX 1060GB 및 16GB RAM 이상으로 구성된 최신 SurfaceBook(15")을 권장합니다.  이 구성은 모든 Windows Mixed Reality 기능을 지원하며 Windows Mixed Reality 대해 테스트되었습니다.  최신 Surface Book(13.5"), Surface Studio, Surface Laptop 및 Surface Pro(2017)은 Intel Core i5 CPU(이상) 및 8GB 이상의 RAM으로 구성된 경우 일부 Windows Mixed Reality 기능을 모두 지원합니다.

**요구 사항:**

* Surface 제품은 드라이버 업데이트가 Windows Mixed Reality 호환되어야 합니다. 이러한 드라이버는 업데이트 및 보안 > **업데이트 확인을 설정 > Surface에** 설치할 수 있습니다.
* Surface 제품에는 비디오 포트(Surface PC에 따라 미니 디스플레이포트 또는 USB-C)에서 Windows Mixed Reality 헤드셋용 HDMI 2.0까지의 [어댑터가](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) 필요합니다. HDMI AV 어댑터에 대한 Surface Mini-DisplayPort 최신 버전은 HDMI 2.0과 호환됩니다(이전 버전은 그렇지 않습니다). 마찬가지로 Surface <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">USB-C-HDMI 어댑터도 HDMI</a> 2.0과 호환됩니다.

## <a name="see-also"></a>참고 항목

* [커뮤니티에 질문하기](https://answers.microsoft.com)
* [지원을 요청합니다.](https://support.microsoft.com/contactus/)
* [Windows Mixed Reality 지원 PC에 권장되는 어댑터](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
