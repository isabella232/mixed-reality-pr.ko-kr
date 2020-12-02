---
title: HP 반향 G2 Faq
description: HP 반향 G2 헤드셋 사용에 대 한 자주 묻는 질문
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, 혼합 현실, 가상 현실, VR, MR, 문제 해결, 오류, 도움말, 지원, 성능
appliesto:
- Windows 10
ms.openlocfilehash: 7712641bad36b8759b9237abf14593f8c121e81b
ms.sourcegitcommit: 3eb4c1a79e9173a5c9b6d2284f34c0bceced402c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96501711"
---
# <a name="hp-reverb-g2-frequently-asked-questions"></a>HP 반향 G2 질문과 대답

## <a name="is-there-a-specific-order-i-should-follow-to-connect-my-headset-cables-to-a-pc"></a>헤드셋 케이블을 PC에 연결 하기 위해 수행 해야 하는 특정 주문이 있나요?

HP 권장 사항:

- PC 또는 전원 공급 장치에 연결 하기 전에 먼저 6-측정기 케이블을 헤드셋에 연결 합니다.
- 초기 설치 후 6 미터 케이블을 헤드셋에 연결 된 상태로 둡니다.
- 헤드셋을 사용 하지 않는 경우 6 미터 케이블에서 전원 어댑터의 연결을 끊습니다.

## <a name="what-should-i-do-to-get-a-crisper-image"></a>더 자세한 이미지를 가져오기 위해 수행 해야 하는 작업

디스플레이가 약간 흐리게 표시 되는 경우 다음과 같은 몇 가지 작업을 수행해 볼 수 있습니다.

- Lenses와 관련 하 여 눈이 가운데에 오도록 헤드셋이 정확히 위에 있는지 확인 합니다.
- IPD (interpupillary distance)를 조정 합니다. 반향 G2는 하드웨어 IPD를 사용 합니다. 이를 변경 하려면 헤드셋에서 IPD 조정을 찾습니다.
- 사용자 또는 연락처가 필요한 경우에는 여전히 필요 합니다.
- Lenses를 청소 해야 하는지 확인 합니다 (마이크로 파이버 천으로-fluids).
- 헤드셋의 고급 디자인으로 인해 Lcd가 준비 될 때까지 콜드 동안 장치를 시작할 때 처음 몇 분 안에 약간의 사소한 이미지 고스트가 있을 수 있습니다.

## <a name="i-am-getting-a-7-14-something-went-wrong-error-when-i-plug-in-my-headset"></a>내 헤드셋에 연결할 때 7-14 "문제가 발생 했습니다." 오류가 발생 합니다.

7-14 문제가 발생 했습니다. 코드는 일부 필수 USB2 구성 요소를 찾지 못했음을 의미 합니다.  HP 반향 G2의 추가 긴 케이블로 인해 USB 신호의 일부 공차가 더 엄격 합니다.  즉, 컴퓨터의 한 포트가 다른 포트 보다 안정적으로 작동할 수 있습니다.

7-14 "오류가 발생 했습니다." 오류가 표시 되 면 다음 단계를 수행해 보세요.

- 헤드셋 및 USB 컨트롤러에 대 한 최신 드라이버가 설치 되어 있는지 확인 합니다.
- Microsoft USB 드라이버를 사용 하 고 있는지 확인 합니다. "확장 가능한 호스트 컨트롤러" 장치의 이름에 "Microsoft"가 있어야 합니다.
- 컴퓨터의 다른 USB-3.0 포트에 케이블을 연결 해 보세요. (USB 유형-C 및 유형-A 포트 사용해 보기)
- 어댑터에 포함 된 USB C를 사용 하 여 다른 포트를 시도 합니다.
- 컴퓨터에 USB 허브를 통해 헤드셋을 연결 해 보세요.

> [!NOTE]
> HP는 반향 G2 장치를 사용 하 여 마더보드에 기본 제공 되는 USB 컨트롤러만 사용 하는 것이 좋습니다.
> 장치에 연결할 수 없는 경우 [HP 지원](https://support.hp.com/us-en) 에 문의 하세요.

## <a name="i-am-getting-a-13-14-something-went-wrong-error-when-my-pc-resumes-from-hibernate-s4"></a>내 PC가 최대 절전 모드에서 다시 시작 될 때 13-14 "오류가 발생 했습니다." 오류가 발생 합니다 (S4).

경우에 따라 다시 시작 프로세스 중에 비디오 카드는 연결을 설정할 수 없기 때문에 PC에서 USB 유형 C를 분리 하 고 다시 연결 하면 연결을 설정 하는 데 도움이 될 수 있습니다.

## <a name="my-hp-motion-controller-joystick-will-sometimes-stick-to-one-side"></a>때로는 HP 모션 컨트롤러 조이스틱을 한 쪽에 두는 경우

이 문제는 조이스틱을 완전히 depressing 자유롭게 이동 하 여 해결할 수 있습니다.

## <a name="the-mixed-reality-portal-says-cant-run-mixed-reality-on-this-headset-but-this-worked-fine-with-my-previous-wmr-headset"></a>혼합 현실 포털은 "이 헤드셋에서 혼합 현실을 실행할 수 없습니다." 라고 표시 하지만 이전 WMR 헤드셋에서 제대로 작동 했습니다.

이는 HP 반향 G2에서 최상의 환경을 보장 하기 위해 더 강력한 PC가 필요한 경우에 발생할 수 있습니다. 자세한 내용은 최소 [PC 요구 사항](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 을 참조 하세요.

## <a name="it-looks-like-my-left-display-is-stretched-and-the-right-display-is-off-centered-and-half-black"></a>왼쪽 표시를 확대 하 고 오른쪽 표시를 가운데 맞춤 및 절반 검정으로 표시 하는 것 처럼 보입니다.

이 문제는 헤드셋이 네이티브 해상도에서 실행 되지 않는 경우에 발생할 수 있습니다. HP 반향 G2 HMD에서 고해상도 표시의 특성으로 인해 모든 시스템이 네이티브 해상도를 렌더링할 수 있는 것은 아닙니다. 이후 Windows 업데이트에는 헤드셋이 네이티브 해상도가 아닐 때 렌더링 문제를 해결 하는 수정이 있습니다.

시스템이 네이티브 해상도에서 렌더링할 수 없는 이유는 다음과 같습니다.

- 시스템의 DisplayPort는 1.3 호환 되지 않을 수 있습니다. 또는 4 레인을 모두 지원 하지 않을 수 있습니다.
- 어댑터를 사용 하는 경우 HBR3 호환이 지원 되지 않거나 4 레인을 모두 지원 하지 않을 수 있습니다.
- 시스템에 하이브리드 GPU가 있는 경우 DisplayPort에서 사용할 수 있는 대역폭을 제한할 수 있습니다.

## <a name="why-are-my-hp-motion-controller-models-not-showing-up-correctly-in-a-game"></a>내 HP 동작 컨트롤러 모델이 게임에 올바르게 표시 되지 않는 이유는 무엇 인가요?

대부분의 게임은 컨트롤러를 표시 하지 않거나 드라이버에 의해 설치 된 모델을 사용 하지 않지만, 일부 게임은 자신의 컨트롤러 모델을 사용자 지정 하거나 사용 가능한 입력에 대 한 상황에 맞는 도움말을 표시 하는 데 사용 됩니다. 일반적으로 게임의 기능을 차단 하지는 않지만 혼동 하거나 시각적으로 이어질 수 있습니다. 게임 자체의 업데이트를 통해서만 수정할 수 있습니다.

## <a name="my-steamvr-games-dont-appear-to-work-correctly-with-my-hp-motion-controllers"></a>내 SteamVR 게임이 HP 모션 컨트롤러에서 제대로 작동 하지 않는 것 같습니다.

개발자가 HP 모션 컨트롤러의 호환성을 위해 게임을 업데이트 하는 동안 스트림에서 가장 인기 있는 게임 대부분에 대 한 사용자 지정 컨트롤러 바인딩을 제공 했습니다. "SteamVR에 대 한 Windows Mixed Reality"를 버전 1.2.444로 완전히 업데이트 한 경우 게임이 실행 중일 때 이러한 바인딩을 자동으로 선택 해야 합니다. 그러나 현재 게임에서 작업을 등록 하지 않는 것으로 보이는 경우 SteamVR 설정 메뉴를 사용 하 여 사용자 지정 바인딩 프로필을 수동으로 검색할 수 있습니다.
원하는 작업

- 오른쪽 동작 컨트롤러의 메뉴 단추를 눌러 SteamVR 메뉴를 엽니다.
- SteamVR 메뉴의 오른쪽 아래 모서리에 있는 "설정" 아이콘을 선택 합니다.
- "컨트롤러" 탭을 선택 합니다.
- "컨트롤러 바인딩 관리" 옵션을 선택 합니다.

여기에서 활성 컨트롤러 바인딩을 "Custom"으로 변경 하 여 커뮤니티 공유 게임 바인딩을 시도 하는 옵션을 열 수 있습니다.
이 게임의 사용자 지정 게임 바인딩이 아직 공유 되지 않은 경우 (또는 시도한 사용자에 게 완전히 만족 하지 않는 경우) 사용자 지정 게임 바인딩을 만들고, 몇 가지 게임 세션 후에 커뮤니티를 공유 하 여 나머지 커뮤니티를 도울 수도 있습니다.