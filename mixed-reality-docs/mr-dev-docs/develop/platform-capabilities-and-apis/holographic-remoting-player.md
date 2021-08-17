---
title: 홀로그램 원격 플레이어
description: 홀로그램 Remoting Player 및 Wi-Fi를 통해 실시간으로 PC에서 HoloLens 홀로그램 콘텐츠 스트리밍에 대해 알아봅니다.
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 07/30/2021
ms.topic: article
keywords: HoloLens, 원격, 홀로그램 원격, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 진단, 성능
ms.openlocfilehash: c5574017c33379248f4bf412cb5b046fdf309d72
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184664"
---
# <a name="holographic-remoting-player"></a>홀로그램 원격 플레이어

>[!TIP]
>[홀로그램 원격의 기본 사항에 대해 알아봅니다.](holographic-remoting-overview.md)

>[!IMPORTANT]
>HoloLens 2 대한 홀로그램 Remoting은 주요 버전 변경입니다. [ **HoloLens(1세대)용** 원격 애플리케이션은](add-holographic-remoting.md) NuGet 패키지 버전 **1.x.x를** 사용해야 하며 [ **HoloLens 2** 원격 애플리케이션은](holographic-remoting-create-remote-wmr.md) **2.x.x 를** 사용해야 합니다. 즉, HoloLens 2 위해 작성된 원격 애플리케이션은 HoloLens(1세대)와 호환되지 않으며 그 반대의 경우도 마찬가지입니다.

[홀로그램 Remoting Player는 홀로그램 Remoting을](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40) 지원하는 PC 앱 및 게임에 연결하는 도우미 앱입니다. Player는 HoloLens(1세대) 및 HoloLens 2 모두 사용할 수 있습니다.  HoloLens Holographic Remoting을 지원하는 PC 앱은 HoloLens 2 Holographic Remoting을 지원하도록 업데이트해야 합니다. 지원되는 버전에 대한 질문이 있는 경우 앱 공급자에게 문의하세요.

>[!TIP]
>버전 [2.2.0부터](holographic-remoting-version-history.md#v2.2.0) 홀로그램 Remoting 플레이어도 Windows Mixed Reality [실행](../../discover/navigating-the-windows-mixed-reality-home.md)중인 Windows PC에 사용할 수 있습니다.

>[!TIP]
>버전 [2.4.0부터](holographic-remoting-version-history.md#v2.4.0) [OpenXR API를](../native/openxr.md) 사용하는 원격 앱을 만들 수 있습니다. 시작하려면 [OpenXR API를 사용하여 홀로그램 원격 원격 앱 작성을 확인하세요.](holographic-remoting-create-remote-openxr.md)

## <a name="connecting-to-the-holographic-remoting-player"></a>홀로그램 Remoting Player에 연결

앱의 지침에 따라 홀로그램 Remoting Player에 연결합니다. 다음과 같이 Remoting Player의 기본 화면에서 볼 수 있는 HoloLens 디바이스의 IP 주소를 입력해야 합니다.

![홀로그램 원격 플레이어](images/holographicremotingplayer.png)

기본 화면이 표시되면 연결된 앱이 없다는 것을 알 수 있습니다.

홀로그램 Remoting 연결은 **암호화되지 않습니다.** 신뢰할 수 있는 보안 Wi-Fi 연결을 통해 항상 홀로그램 Remoting을 사용해야 합니다.

## <a name="quality-and-performance"></a>품질 및 성능

환경의 품질과 성능은 다음 세 가지 요인에 따라 달라집니다.
* **실행 중인 홀로그램 환경** - 고해상도 또는 매우 자세한 콘텐츠를 렌더링하는 앱은 더 빠른 PC 또는 더 빠른 무선 연결이 필요할 수 있습니다.
* **PC의 하드웨어** - PC를 초당 60프레임으로 홀로그램 환경을 실행하고 인코딩할 수 있어야 합니다. 그래픽 카드의 경우 일반적으로 GeForce GTX 970 또는 AMD Radeon R9 290 이상하는 것이 좋습니다. 다시 말하지만, 특정 환경의 경우 더 높거나 낮은 엔드 카드가 필요할 수 있습니다.
* **Wi-Fi 연결** - 홀로그램 환경이 Wi-Fi를 통해 스트리밍됩니다. 정체가 낮은 고속 네트워크를 사용하여 품질을 최대화합니다. Wi-Fi가 아닌 이더넷 케이블을 통해 연결된 PC를 사용하면 품질도 향상될 수 있습니다.

## <a name="diagnostics"></a>진단

연결 품질을 측정하려면 홀로그램 원격 플레이어의 기본 화면에 있는 동안 **"진단 사용"을** 말합니다. 진단을 사용하도록 설정하면 **HoloLens(1세대)에서** 앱에 다음이 표시됩니다.

* **FPS** - Remoting 플레이어가 수신하고 렌더링하는 초당 렌더링된 평균 프레임 수입니다. 이상적인 것은 60 FPS입니다.
* **대기 시간** - 프레임이 PC에서 HoloLens 이동하는 데 걸리는 평균 시간입니다. 낮을수록 좋습니다. 이는 주로 Wi-Fi 네트워크에 따라 달라집니다.

**HoloLens 2** 앱에 다음이 표시됩니다.

![홀로그램 원격 플레이어 진단](images/holographicremotingplayer-diag.png)

* **렌더링** - Remoting 플레이어가 마지막 1초 동안 렌더링한 프레임 수입니다. 네트워크를 통해 도착한 프레임 수와는 독립적입니다(비디오 **프레임** 참조). 렌더링된 프레임 사이의 평균/최대 렌더링 델타 시간(밀리초)이 표시됩니다.

* **비디오 프레임** - 표시되는 첫 번째 숫자는 비디오 프레임을 건너뛰고, 두 번째 숫자는 다시 사용되며, 세 번째 숫자는 비디오 프레임을 받습니다. 모든 숫자는 마지막 1초 동안의 개수를 나타냅니다.
    * ```Received frames``` 는 마지막 1초 동안 도착한 비디오 프레임의 수입니다. 정상 조건에서는 60이어야 하지만 그렇지 않은 경우 네트워크 문제로 인해 프레임이 삭제되거나 원격/원격 쪽에서 예상 속도로 프레임을 생성하지 않는다는 표시기입니다.
    * ```Reused frames``` 는 마지막 1초 동안 두 번 이상 사용된 비디오 프레임의 수입니다. 예를 들어 비디오 프레임이 늦게 도착하는 경우 플레이어의 렌더링 루프는 여전히 프레임을 렌더링하지만 이전 프레임에 이미 사용된 비디오 프레임을 *다시 사용해야* 합니다.
    * ```Skipped frames``` 는 플레이어의 렌더링 루프에서 사용되지 않은 비디오 프레임의 수입니다. 예를 들어 네트워크 지터는 도착하는 비디오 프레임이 더 이상 균등하게 분산되지 않는 효과를 가질 수 있습니다. 예를 들어 60Hz에서 실행할 때 더 이상 델타가 16.66밀리초가 아니라는 결과와 함께 시간이 지연되는 경우도 있습니다. 플레이어의 렌더링 루프에서 두 개의 틱 사이에 둘 이상의 프레임이 도착하는 경우 발생할 수 있습니다. 이 경우 플레이어는 항상 가장 최근에 받은 비디오 프레임을 표시해야 하며 하나 이상의 프레임을 *건너뜁니다.*

    >[!NOTE]
    >네트워크 지터를 연결 하는 경우 건너뛰고 다시 사용 된 프레임은 일반적으로 거의 동일합니다. 반면 건너뛴 프레임만 표시되는 경우 이는 플레이어가 대상 프레임 속도에 도달하지 않는다는 표시기입니다. 이 경우 문제를 진단할 때 최대 렌더링 델타 시간을 주시해야 합니다.

* **비디오 프레임 델타** - 지난 1초 동안 받은 비디오 프레임 간의 최소/최대 델타입니다. 이 숫자는 일반적으로 네트워크 지터로 인한 문제의 경우 건너뛰고 다시 사용하는 프레임과 상관 관계가 있습니다.
* **대기 시간** - 마지막 1초 동안의 평균 소요 시간(밀리초)입니다. 이 컨텍스트에서 소요 시간은 HoloLens 디스플레이에 해당 자세/원격 분석 데이터의 비디오 프레임을 표시할 때까지 HoloLens 원격/원격 쪽으로 자세/센서 데이터를 보내는 시간을 의미합니다.
* **삭제된 비디오 프레임** - 마지막 1초 동안 및 연결이 설정된 이후 삭제된 비디오 프레임의 수입니다. 삭제된 비디오 프레임의 주요 원인은 비디오 프레임이 순서대로 도착하지 않고 이미 최신 프레임이 있기 때문에 삭제해야 하는 경우입니다. 이는 *삭제된 프레임과* 비슷하지만 원인은 Remoting 스택의 하위 수준에 있습니다. 삭제된 비디오 프레임은 잘못된 네트워크 조건에서만 예상됩니다.

주 화면에서 **"진단 사용 안 함"을** 표시하여 진단을 해제할 수 있습니다.

## <a name="pc-system-requirements"></a>PC 시스템 요구 사항
* PC에서 Windows 10 1주년 업데이트 이후를 **실행해야 합니다.**
* GeForce GTX 970 또는 AMD Radeon R9 290 이상 그래픽 카드를 권장합니다.
* 무선 홉 수를 줄이려면 이더넷을 통해 PC를 네트워크에 연결하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목
* [홀로그램 Remoting 개요](holographic-remoting-overview.md)
* [HoloLens(1세대): 홀로그램 Remoting 추가](add-holographic-remoting.md)
* [Windows Mixed Reality API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-wmr.md)
* [OpenXR API를 사용하여 홀로그램 원격 원격 앱 작성](holographic-remoting-create-remote-openxr.md)
* [홀로그램 원격 소프트웨어 사용 조건](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인정보처리방침](https://go.microsoft.com/fwlink/?LinkId=521839)