---
title: 하드웨어 액세서리
description: Windows Mixed Reality에서 사용할 수 있는 액세서리 유형과이를 설정 하는 방법을 설명 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: 방법, 보조 프로그램, bluetooth, bt, 컨트롤러, 게임 패드, clicker, xbox, 하드웨어, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 동작 컨트롤러
ms.openlocfilehash: b9a58a34a88de01d1d2351ff0a5efbe4f99298db
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583321"
---
# <a name="hardware-accessories"></a>하드웨어 액세서리

Windows Mixed Reality 장치는 액세서리를 지원 합니다. Bluetooth 또는 USB 포트를 사용 하 여 지원 되는 액세서리를 PC의 모던 헤드셋에 쌍으로 연결할 수 있습니다.

HoloLens에서 Bluetooth 액세서리를 사용 하는 방법에 대 한 자세한 내용은 [bluetooth 및 USB 장치에 연결](/hololens/hololens-connect-devices)을 참조 하세요.

Windows Mixed Reality 몰입 형 헤드셋은 [응시](../design/gaze-and-commit.md) 및 [음성](../design/voice-input.md)이외의 입력을 위한 액세서리를 요구 합니다. 지원 되는 액세서리는 **키보드 및 마우스**, **게임 패드** 및 **[동작 컨트롤러](../design/motion-controllers.md)** 를 포함 합니다.

## <a name="pairing-bluetooth-accessories"></a>Bluetooth 액세서리 페어링

모바일 주변 장치를 몰입 형 헤드셋과 페어링 하는 것은 Bluetooth 주변 장치를 Windows 10 데스크톱 또는 모바일 장치와 페어링 하는 것과 비슷합니다.

1. 시작 메뉴에서 **설정** 앱을 엽니다.
2. **장치로** 이동
3. 슬라이더 스위치를 사용 하 여 꺼져 있는 경우 Bluetooth 라디오가 켜 세요.
4. Bluetooth 장치를 페어링 모드로 전환 합니다. 이 프로세스는 장치에 따라 다르지만 대부분의 Bluetooth 장치에서는 하나 이상의 단추를 누르고 있습니다.
5. 장치 이름이 Bluetooth 장치 목록에 표시 될 때까지 기다립니다. 장치를 선택 하는 경우 장치를 선택 하 고 **쌍** 단추를 선택 합니다. 근처에 많은 Bluetooth 장치가 있는 경우 연결 하려는 장치를 확인 하려면 Bluetooth 장치 목록의 맨 아래로 스크롤해야 할 수도 있습니다.
6. Bluetooth 주변 장치를 입력 기능 (예: Bluetooth 키보드)과 페어링 하는 경우 6 자리 또는 8 자리 pin이 표시 될 수 있습니다. 주변 장치에 pin을 입력 하 고 enter 키를 눌러 헤드셋과 페어링을 완료 해야 합니다.

## <a name="motion-controllers"></a>모션 컨트롤러

Windows Mixed Reality [동작 컨트롤러](../design/motion-controllers.md) 는 몰입 형 헤드셋에서 지원 되지만 HoloLens는 지원 되지 않습니다. 이러한 컨트롤러는 보기의 필드에서 정확 하 고 응답성이 뛰어난 이동 추적을 제공 합니다. 모던 헤드셋의 센서는 추적을 수행 합니다. 즉, 공간의 벽에 하드웨어를 설치할 필요가 없습니다. 각 컨트롤러에는 몇 가지 입력 방법이 있습니다.

![Windows Mixed Reality 동작 컨트롤러](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a>Bluetooth 키보드

영어 Qwerty 블루투스 키보드는 holographic 키보드를 사용할 수 있는 모든 곳에서 페어링 하 고 사용할 수 있습니다. 고품질 키보드를 사용 하면 차이점이 있으므로 [Microsoft Universal 폴딩 가능 키보드](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) 또는 [Microsoft Designer Bluetooth Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)을 사용 하는 것이 좋습니다.

## <a name="bluetooth-gamepads"></a>Bluetooth gamepads

특히 게임 패드 지원을 사용 하도록 설정 하는 앱 및 게임과 함께 컨트롤러를 사용할 수 있습니다. Gamepads는 HoloLens 사용자 인터페이스를 제어 하는 데 사용할 수 없습니다.

Xbox a S와 함께 제공 되는 xbox 무선 컨트롤러 또는 Xbox One S에서 Bluetooth 연결을 위한 액세서리로 판매 하 여 HoloLens 및 몰입 형 헤드셋에서 사용할 수 있습니다. HoloLens를 사용 하려면 먼저 Xbox 무선 컨트롤러를 [업데이트 해야](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) 합니다.

Bluetooth gamepads의 다른 브랜드는 Windows Mixed Reality 장치에서 작동할 수 있지만 지원은 응용 프로그램에 따라 달라 집니다.

## <a name="other-bluetooth-accessories"></a>기타 Bluetooth 액세서리

주변 장치는 Bluetooth HID 또는 GATT 프로필을 지원 하기만 하면 HoloLens와 쌍으로 연결할 수 있습니다. 키보드, 마우스 및 HoloLens Clicker 외에 다른 Bluetooth HID 및 GATT 장치에는 완전 한 기능을 제공 하기 위해 Microsoft HoloLens의 도우미 응용 프로그램이 필요할 수 있습니다.

지원 되지 않는 주변 장치는 다음과 같습니다.

* Bluetooth 오디오 프로필의 주변 장치는 지원 되지 않습니다.
* 스피커 및 헤드셋과 같은 Bluetooth 오디오 장치는 설정 앱에서 사용할 수 있지만, Microsoft HoloLens는 오디오 끝점으로 지원 되지 않습니다.
* Bluetooth 사용 전화 및 Pc는 페어링 및 파일 전송을 지원 하지 않습니다.

## <a name="unpairing-a-bluetooth-peripheral"></a>Bluetooth 주변 장치 페어링 해제

1. 시작 메뉴에서 **설정** 앱을 엽니다.
2. **장치로** 이동
3. Bluetooth 라디오가 꺼진 경우 켭니다.
4. 사용 가능한 Bluetooth 장치 목록에서 장치를 찾습니다.
5. 목록에서 장치를 선택 하 고 **제거** 단추를 선택 합니다.