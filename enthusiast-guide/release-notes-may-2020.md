---
title: 릴리스 정보-2020 년 5 월
description: 2020 년 5 월 Windows 10 업데이트에 대 한 Windows Mixed Reality 릴리스 정보를 최신 상태로 유지 합니다.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: 릴리스 정보, 버전, windows 10, 빌드, 19h1, os, 2020 년 5 월
ms.openlocfilehash: 462fcbfa10cfff8df23c970fd54ee0754a4d9472
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439173"
---
# <a name="windows-10-release-notes---may-2020"></a>Windows 10 릴리스 정보-2020 년 5 월

**Windows 10 2020 업데이트 (v2004)** 에는 혼합 현실 홈에서 Win32 응용 프로그램을 시작 하는 기능과 같은 VR (Windows Mixed Reality) 헤드셋의 새로운 기능이 포함 되어 있습니다. HoloLens (1 세대)는 월간 서비스 업데이트를 제공 하는 lts (장기 서비스)에 있습니다.

Windows Mixed Reality 모던 (VR) 헤드셋의 최신 PC 릴리스로 업그레이드 하 고, **설정 > 업데이트 & 보안** 을 열고 **업데이트 확인** 을 선택 합니다. Windows 10 PC에서 [Windows 미디어 만들기 도구](https://www.microsoft.com/software-download/windows10)를 사용 하 여 **Windows 10 2020 업데이트** 를 수동으로 설치할 수도 있습니다.

**데스크톱용 최신 릴리스**: Windows 10 v2004 (10.0.19041.264)

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality 모던 헤드셋의 업데이트

### <a name="introducing-the-new-microsoft-edge"></a>새 Microsoft Edge 소개

[이전에 발표](/windows/mixed-reality/new-microsoft-edge)한 대로 Windows Mixed Reality에서 새 Microsoft Edge 브라우저를 사용 하 여 더 나은 지원을 제공 했습니다. 새 Microsoft Edge는 Chromium 오픈 소스 프로젝트를 채택 하 여 고객에 게 더 나은 웹 호환성을 만들고 모든 웹 개발자를 위한 웹의 조각화를 줄일 수 있습니다. 또한 WebVR 대신 VR 헤드셋에 대 한 몰입 형 웹 환경을 만드는 새로운 표준인 WebXR도 지원 합니다.

### <a name="improved-settings-for-wmr"></a>WMR에 대 한 향상 된 설정

피드백을 주셔서 감사 합니다. 헤드셋 표시 페이지에서 설정을 추가 하 고 설명 했습니다.

* **내 홈의 시각적 품질이** 이 설정을 변경 하면 혼합 현실 집 환경 (절벽 집 및 Skyloft)에만 영향을 줍니다.

* **혼합 현실 홈에서 세부 효과 수준 및 효과 품질 조정** -이 변경 내용은 홈에서 사용 하는 일부 렌더링에 영향을 줍니다. 특히이 설정을 낮은 수준에서 높음으로 변경 하는 경우 다양 한 재질의 시각적 품질 (목재, 구체적 등)이 확장 됩니다.

* **앱 창 해상도 변경** -기본적으로 홈에서 시작 된 대부분의 2d 창은 720-p 해상도로 시작 됩니다. 수직 & 세로 방향으로 수동으로 크기를 조정할 수 있지만,이를 모두 1080p에서 시작 하도록 선택할 수도 있습니다. 이전에는이 옵션을 시각적 품질에서 매우 높은 (베타) 옵션으로 사용할 수 있었습니다. 이제 별도의 설정으로 적절 하 게 분할 했습니다.

* **환경 옵션** -이러한 옵션은 하드웨어에서 무제한 90 fps를 유지 해야 하는 시스템의 부하를 줄이기 위해 혼합 현실 환경을 조정 합니다. 이러한 추가 설정을 명시적으로 사용 하거나 사용 하지 않도록 설정 하거나, Windows 결정을 선택 하 여 추론을 설정 하거나 해제할 시기를 계속 결정할 수 있습니다.

* **해결 방법** -HP 반향 같은 고해상도 헤드셋이 있는 경우 네이티브 해상도로 실행 하거나 성능상의 이유로 해상도를 줄이는 것이 좋습니다. Samsung Odyssey 및 Odyssey +와 같은 이전 헤드셋은 단일 해상도만 지원 하므로 해당 헤드셋에서이 설정을 변경할 수 없습니다.

* **프레임 주기** -이제 헤드셋 디스플레이의 프레임 속도로 수동으로 설정 Windows 하거나, 해당 추론을 사용 하 여 60 hz 또는 90 hz가 더 적절 한지 확인할 수 있습니다.

* **보정** -이전 처럼 헤드셋에서 지 원하는 경우 IPD (interpupillary distance)를 조정할 수 있습니다.

* **입력 전환** -입력 포커스 전환 (Win + Y) 동작을 자동 (현재 상태 센서 피드백에 따라) 또는 수동으로 전환 합니다.

### <a name="new-cortana-app"></a>새 Cortana 앱

Windows에 대 한이 업데이트는 현재 영어로만 제공 되는 최신 버전의 Cortana 앱을 포함 하며, "사진 찍기" 및 "비디오 가져오기"와 같은 특정 혼합 현실 특정 명령을 더 이상 지원 하지 않습니다. 사용자는 새로운 Cortana를 사용 하 여 앱을 시작할 수 있으며, "다음 모임이 언제 인가요?"와 같은 새로운 생산성 중심 명령도 지원 합니다. 또는 "늦게 실행 중인 것으로 전자 메일 보내기 \< name \> "
    
### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>19041.546에서 제공 되는 추가 업데이트 (10 월 2020 일 출시)

이 데스크톱 월간 서비스 업데이트는 Windows Mixed Reality 장치에 대해 다음과 같은 변경 내용을 포함 합니다. 
* Windows Mixed Reality 헤드 탑재 디스플레이 (HMD)의 왜곡이 나 aberrations을 줄입니다. 
* 에는 예정 된 HP Windows Mixed Reality 동작 컨트롤러에 대 한 지원이 추가 되었습니다. 
* 90 hz를 달성할 수 없는 경우 특정 경우에 Windows Mixed Reality의 90-Hz 새로 고침 빈도 설정의 동작을 더 이상 자동으로 60 Hz로 전환 하지 않도록 변경 합니다. 

### <a name="help-us-improve"></a>개선할 수 있도록 도와 주세요!

호환성을 지속적으로 개선 하 고 있습니다.  Windows Mixed Reality 하는 동안 즐겨 사용 하는 클래식 Win32 응용 프로그램이 제대로 작동 하지 않는 경우 [피드백 허브](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)를 통해 피드백을 제출 하세요.

## <a name="prior-release-notes"></a>이전 릴리스 정보

* [릴리스 정보-2019 년 5 월](release-notes-may-2019.md)
* [릴리스 정보 - 2018년 10월](release-notes-october-2018.md)
* [릴리스 정보-4 월 2018](release-notes-april-2018.md)
* [릴리스 정보 - 2017년 10월](release-notes-october-2017.md)
* [릴리스 정보 - 2016년 8월](release-notes-august-2016.md)
* [릴리스 정보 - 2016년 5월](release-notes-may-2016.md)
* [릴리스 정보 - 2016년 3월](release-notes-march-2016.md)

## <a name="see-also"></a>참고 항목
* [모던 헤드셋 지원 (외부 링크)](./troubleshooting-windows-mixed-reality.md)
* [지원 HoloLens (외부 링크)](https://support.microsoft.com/products/hololens)
* [도구 설치](/windows/mixed-reality/develop/install-the-tools)
* [피드백 보내기](/windows/mixed-reality/give-us-feedback)