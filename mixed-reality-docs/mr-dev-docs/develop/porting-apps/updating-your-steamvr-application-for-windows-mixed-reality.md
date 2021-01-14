---
title: Windows Mixed Reality용 SteamVR 앱 업데이트
description: Windows Mixed Reality 헤드셋과의 호환성을 최대화 하기 위해 SteamVR 응용 프로그램을 업데이트 하는 최선의 방법입니다.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, Compatibility, 포팅, HoloLens 1 gen, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 마이그레이션, Windows 10, 스트림, 동작 컨트롤러, haptics
ms.openlocfilehash: c67eed489f626c804583592e496fcfaff5d8c291
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192631"
---
# <a name="updating-steamvr-apps-for-windows-mixed-reality"></a>Windows Mixed Reality용 SteamVR 앱 업데이트

개발자가 Windows Mixed Reality 헤드셋에서 실행할 SteamVR 환경을 테스트 하 고 최적화 하는 것이 좋습니다. 이 설명서에서는 Windows Mixed Reality에서 환경을 효율적으로 실행 하기 위해 수행할 수 있는 일반적인 개선 사항을 설명 합니다.

## <a name="initial-setup-instructions"></a>초기 설치 지침

Windows Mixed Reality에서 게임 또는 앱 테스트를 시작 하려면 먼저 [시작 가이드](https://aka.ms/WindowsMixedRealitySteamVR) 를 따르세요.

## <a name="controller-models"></a>컨트롤러 모델

1. 앱이 컨트롤러 모델을 렌더링 하는 경우:
    * [Windows Mixed Reality 동작 컨트롤러 모델](../../design/motion-controllers.md#rendering-the-motion-controller-model) 사용
    * IVRRenderModel:: GetComponentState를 사용 하 여 구성 요소 부분에 대 한 로컬 변환을 가져옵니다 (예: 포인터 포즈).
2. 활용 이라는 개념이 있는 환경은 입력 Api에서 컨트롤러를 구별 하기 위해 힌트를 가져와야 합니다 [(Unity 예제)](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) .

## <a name="controls"></a>컨트롤

컨트롤 레이아웃을 디자인 하거나 조정할 때 다음의 예약 된 명령 집합을 염두에 두어야 합니다.
1. **왼쪽 및 오른쪽 아날로그 엄지 스틱** 을 클릭 하면 **스트림 대시보드에** 예약 됩니다.

> [!NOTE]
> HP 반향 G2 컨트롤러를 사용 하는 경우 오른쪽 메뉴 단추를 클릭 하면 **스트림 대시보드에** 대해 예약 됩니다.

2. **Windows 단추** 는 항상 Windows Mixed Reality 홈으로 사용자를 반환 합니다.

가능 하면 기본적으로 엄지 스틱 기반 teleportation [Windows Mixed Reality home](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior와 일치 합니다.

## <a name="tooltips-and-ui"></a>도구 설명 및 UI

많은 VR 게임은 사용자에 게 앱 또는 게임의 가장 중요 한 명령을 알려 주는 동작 컨트롤러 도구 설명 및 오버레이를 활용 합니다. Windows Mixed reality의 응용 프로그램을 튜닝할 때 도구 설명이 Windows 컨트롤러 모델에 매핑되는지 확인 하는 환경에서이 부분을 검토 하는 것이 좋습니다.

또한 사용자 환경에 컨트롤러 이미지를 표시 하는 점이 있는 경우 Windows Mixed Reality 동작 컨트롤러를 사용 하 여 업데이트 된 이미지를 제공 해야 합니다.

## <a name="haptics"></a>Haptics

[Windows 10 4 월 2018 업데이트](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)부터 Windows Mixed Reality의 SteamVR 환경에 대 한 haptics가 지원 됩니다. SteamVR app 또는 game에 이미 haptics에 대 한 지원이 포함 된 경우 [Windows Mixed Reality 동작 컨트롤러](../../design/motion-controllers.md)에서 추가 작업 없이 작동 해야 합니다.

Windows Mixed Reality 동작 컨트롤러는 다른 SteamVR 동작 컨트롤러에서 발견 된 선형 작동기와는 달리 표준 haptics 모터를 사용 합니다. 이로 인해 약간 다르게 예상 되는 사용자 환경이 발생할 수 있습니다. 따라서 Windows Mixed Reality 동작 컨트롤러를 사용 하 여 haptics 디자인을 테스트 하 고 조정 하는 것이 좋습니다. 예를 들어 Windows Mixed Reality 동작 컨트롤러에서 짧은 햅 펄스 (5-10 밀리초)가 더 눈에 띄지 않을 수도 있습니다. 더 눈에 띄는 펄스를 생성 하려면 더 긴 "클릭" (40-70 밀리초)을 사용 하 여 모터를 다시 전원 꺼짐으로 설정 하기 전에 표시 하는 시간을 더 많이 제공 합니다.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Windows Mixed Reality 시작 메뉴에서 SteamVR apps 시작

스트림를 통해 배포 되는 VR 환경의 경우 최신 [windows 릴리스와](https://insider.windows.com)함께 [SteamVR에 대 한 Windows Mixed Reality를 업데이트](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) 했습니다. 이제 SteamVR 제목이 "모든 앱" 목록의 Windows Mixed Reality 시작 메뉴에 자동으로 표시 됩니다.

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality 로고

제목에 대 한 Windows Mixed Reality 지원을 표시 하려면 앱 방문 페이지의 "스토어 페이지 편집" 링크로 이동 하 여 "기본 정보" 탭을 선택 하 고 "가상 현실"까지 아래로 스크롤합니다. "Windows Mixed Reality 숨기기"를 선택 취소 한 다음 저장소에 게시 합니다.

## <a name="bugs-and-feedback"></a>버그 및 피드백

사용자 의견은 Windows Mixed Reality SteamVR 환경을 개선 하는 데 유용 합니다. [Windows 피드백 허브](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)를 통해 모든 피드백과 버그를 제출 합니다. [SteamVR 피드백을 최대한 활용 하는 방법에 대 한](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)몇 가지 팁은 다음과 같습니다.

공유에 대 한 질문이 나 의견이 있는 경우 [스트림 포럼](https://steamcommunity.com/app/719950/discussions/)에서 연락할 수도 있습니다.

## <a name="faqs-and-troubleshooting"></a>Faq 및 문제 해결

경험을 설정 하거나 재생 하는 일반적인 문제를 실행 하는 경우 [최신 문제 해결 단계를 확인](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)하세요.

## <a name="see-also"></a>참고 항목

* [도구 설치](../install-the-tools.md)
* [헤드셋 및 동작 컨트롤러 드라이버 기록](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality 최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
