---
title: HoloLens 연구 모드
description: 애플리케이션은 HoloLens 연구 모드를 사용하여 주요 디바이스 센서 스트림(깊이, 환경 추적 및 IR 반사도)에 액세스할 수 있습니다.
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: 연구 모드, cv, rs4, 컴퓨터 비전, 연구, HoloLens, HoloLens 2
ms.openlocfilehash: 57306307e4fd23870ae4cbcdb88773cfc858515f4d7ff0e27e26930bace54d65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193692"
---
# <a name="hololens-research-mode"></a>HoloLens 연구 모드

연구 모드는 HoloLens(1세대) 디바이스에서 도입되어 주요 센서, 특히 배포용이 아닌 연구 애플리케이션에 대한 액세스 권한을 부여합니다.  HoloLens 2 대한 연구 모드는 HoloLens 1의 기능을 유지하지만 다음 스트림에 대한 액세스를 추가합니다.

* **표시 광원 환경 추적 카메라** - 시스템에서 헤드 추적 및 지도 빌드에 사용하는 회색 크기 카메라입니다.
* **깊이 카메라** – 두 가지 모드로 작동합니다.  
    + 손 추적에 사용되는 AHAT, 높은 빈도(45FPS) 근사치 감지 첫 번째 버전의 짧은 throw 모드와 달리 AHAT는 1미터를 초과하는 단계 래핑을 통해 의사 깊이를 제공합니다. 
    + [공간 매핑에](../../design/spatial-mapping.md) 사용되는 긴 throw, 낮은 빈도(1-5 FPS) 원거리 감지

* **IR 리플렉트 스트림의 두 가지 버전** - HoloLens 깊이를 계산하는 데 사용됩니다. 이러한 이미지는 앰비언트 표시 광원에 의해 비추고 영향을 받지 않습니다.

HoloLens 2 사용하는 경우 아래의 추가 입력에도 액세스할 수 있습니다.

* **가속도계** – 시스템에서 X, Y 및 Z 축과 무게의 선형 가속을 결정하는 데 사용됩니다.
* **Gyro** – 시스템에서 회전을 결정하는 데 사용됩니다.
* **지자기계** – 시스템에서 절대 방향을 예측하는 데 사용됩니다.

> [!IMPORTANT]
> 연구 모드는 현재 공개 미리 보기로 제공됩니다. 

![연구 모드 앱 스크린샷](images/sensor-stream-viewer.jpg)<br>
*연구 모드에서 사용할 수 있는 8개의 센서 스트림을 표시하는 테스트 애플리케이션의 혼합 현실 캡처*

## <a name="usage"></a>사용량

연구 모드는 Computer Vision 및 로봇 공학 분야에서 새로운 아이디어를 탐색하는 교육 및 산업 연구원을 위해 설계되었습니다.  엔터프라이즈 환경에 배포되거나 Microsoft Store 또는 기타 배포 채널을 통해 사용할 수 있는 애플리케이션에는 사용할 수 없습니다.

또한 Microsoft는 향후 하드웨어 또는 OS 업데이트에서 연구 모드 또는 이와 동등한 기능이 지원될 것이라는 보증을 제공하지 않습니다. 그러나 이를 통해 새로운 아이디어를 개발하고 테스트하는 데 사용할 수 없습니다.

## <a name="security-and-performance"></a>보안 및 성능

연구 모드를 사용하도록 설정하면 연구 모드 기능을 사용하는 애플리케이션이 실행되고 있지 않더라도 정상 조건에서 HoloLens 2 사용하는 것보다 더 많은 배터리 전원이 사용됩니다.  이 모드를 사용하도록 설정하면 애플리케이션이 센서 데이터를 오용할 수 있으므로 디바이스의 전반적인 보안이 저하됩니다.  디바이스 보안에 대한 자세한 내용은 [HoloLens 보안 FAQ에서](/hololens/hololens-faq-security)확인할 수 있습니다.  

## <a name="device-support"></a>디바이스 지원
<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens 1세대</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
    </tr>
     <tr>
        <td>헤드 추적 카메라</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>깊이 & IR 카메라</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>가속도계</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>자이로스코프</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>지자기 센터</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a>연구 모드 사용(HoloLens 1세대 및 HoloLens 2)

연구 모드는 개발자 모드의 확장입니다. 시작하기 전에 디바이스의 개발자 기능을 사용하도록 설정하여 연구 모드 설정에 액세스해야 합니다. 

* **시작 메뉴 > 설정** 열고 **업데이트를** 선택합니다.
* **개발자용 을** 선택하고 **개발자 모드를** 사용하도록 설정합니다.
* 아래로 스크롤하여 **장치 포털** 을 사용하도록 설정합니다.

개발자 기능을 사용하도록 설정한 후 [디바이스 포털에 연결하여](/windows/uwp/debug-test-perf/device-portal-hololens) 연구 모드 기능을 사용하도록 설정합니다.

* 장치 포털 **시스템 > 연구 모드로** **이동합니다.**
* **센서 스트림에 대한 액세스 허용을** 선택합니다.
* 페이지 맨 위에 있는 **전원** 메뉴 항목에서 디바이스를 다시 시작합니다.

디바이스를 다시 시작하면 **장치 포털** 통해 로드된 애플리케이션이 연구 모드 스트림에 액세스할 수 있습니다.

![HoloLens 장치 포털 조사 모드 탭](images/ResearchModeDevPortal.png)<br>
*HoloLens 장치 포털 조사 모드 창*

> [!IMPORTANT]
> HoloLens 2 대한 연구 모드는 빌드 19041.1364부터 사용할 수 있습니다. 이전 빌드에서 액세스해야 하는 경우 Insider [Preview](/hololens/hololens-insider) 프로그램에 등록합니다. 자세한 내용은 [연구 모드 GitHub 리포지토리에서](https://github.com/microsoft/HoloLens2ForCV)찾을 수 있습니다.

### <a name="using-sensor-data-in-your-apps"></a>앱에서 센서 데이터 사용

애플리케이션은 미디어 파운데이션 사진 및 비디오 카메라 스트림에 [액세스하는](/windows/win32/medfound/microsoft-media-foundation-sdk) 것과 동일한 방식으로 센서 스트림 데이터에 액세스할 수 있습니다. 

HoloLens 개발에 작동하는 모든 API는 연구 모드에서도 사용할 수 있습니다. 특히 애플리케이션은 각 센서 프레임 캡처 시간에 HoloLens 6DoF 공간의 위치를 정확하게 알고 있습니다.

연구 모드 스트림 액세스, [intrinsics 및 extrinsics 사용,](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)스트림 기록 등을 보여주는 샘플 애플리케이션이 있습니다.
* [HoloLens(1세대)](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a>지원

HoloLens(1세대)의 경우 HoloLensForCV 리포지토리의 [문제 추적기를](https://github.com/Microsoft/HololensForCV/issues) 사용하여 피드백을 게시하고 알려진 문제를 추적합니다.

HoloLens 2 경우 HoloLens2ForCV 리포지토리의 [문제 추적기를](https://github.com/microsoft/HoloLens2ForCV/issues) 사용하여 피드백을 게시하고 알려진 문제를 추적합니다.

## <a name="see-also"></a>추가 정보

* [Microsoft 미디어 파운데이션](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [HoloLensForCV GitHub 리포지블리](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens2ForCV GitHub 리포지블리](https://github.com/microsoft/HoloLens2ForCV)
* [Windows 디바이스 포털 사용](using-the-windows-device-portal.md)