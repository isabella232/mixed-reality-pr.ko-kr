---
title: 하드웨어 액세서리
description: Windows Mixed Reality 사용할 수 있는 액세서리 유형과 이를 설정하는 방법을 설명합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: 방법, 액세서리, Bluetooth, bt, 컨트롤러, 게임 패드, 클릭기, xbox, 하드웨어, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 모션 컨트롤러
ms.openlocfilehash: a6776df9374fce3f1399de944be06c93ff6fdcb3e6f4a38dcc92453556857376
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188460"
---
# <a name="hardware-accessories"></a>하드웨어 액세서리

Windows Mixed Reality 디바이스는 액세서리를 지원합니다. Bluetooth 또는 USB 포트를 사용하여 지원되는 액세서리를 PC의 몰입형 헤드셋에 페어링할 수 있습니다.

HoloLens Bluetooth 액세서리 사용에 대한 자세한 내용은 Bluetooth [및 USB-C 디바이스에 대한 커넥트 참조하세요.](/hololens/hololens-connect-devices)

Windows Mixed Reality 몰입형 헤드셋에는 [응시](../design/gaze-and-commit.md) 및 [음성](../design/voice-input.md)외에 입력을 위한 액세서리가 필요합니다. 지원되는 액세서리에는 **키보드 및 마우스,** **게임 패드** 및 **[모션 컨트롤러가 포함됩니다.](../design/motion-controllers.md)**

## <a name="pairing-bluetooth-accessories"></a>Bluetooth 액세서리 페어링

Bluetooth 주변 장치를 몰입형 헤드셋과 페어링하는 것은 Bluetooth 주변 장치를 Windows 10 데스크톱 또는 모바일 디바이스와 페어링하는 것과 비슷합니다.

1. 시작 메뉴에서 **설정** 앱을 엽니다.
2. **디바이스로** 이동
3. 슬라이더 스위치를 사용하여 꺼져 있는 경우 Bluetooth 라디오 켜기
4. Bluetooth 디바이스를 페어링 모드로 배치합니다. 이 프로세스는 디바이스마다 다르지만 대부분의 Bluetooth 디바이스는 하나 이상의 단추를 누르고 있습니다.
5. 디바이스 이름이 Bluetooth 디바이스 목록에 표시되기를 기다립니다. 이 경우 디바이스를 선택한 **다음, 페어링** 단추를 선택합니다. 근처에 Bluetooth 디바이스가 많은 경우 Bluetooth 디바이스 목록의 맨 아래로 스크롤하여 페어링하려는 디바이스를 확인해야 할 수 있습니다.
6. 입력 기능(예: Bluetooth 키보드)과 Bluetooth 주변 장치를 페어링하는 경우 6자리 또는 8자리 핀이 표시될 수 있습니다. 주변 장치에서 해당 핀을 입력한 다음 Enter 키를 눌러 헤드셋과의 페어링을 완료해야 합니다.

## <a name="motion-controllers"></a>모션 컨트롤러

Windows Mixed Reality 모션 [컨트롤러는](../design/motion-controllers.md) 몰입형 헤드셋에서 지원되지만 HoloLens 않습니다. 이러한 컨트롤러는 보기 필드에서 정확하고 반응형 이동 추적을 제공합니다. 몰입형 헤드셋의 센서는 추적을 수행하므로 공간의 벽에서 하드웨어를 설치할 필요가 없습니다. 각 컨트롤러에는 여러 가지 입력 방법이 있습니다.

![Windows Mixed Reality 모션 컨트롤러](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a>키보드 Bluetooth

영어 Qwerty Bluetooth 키보드는 홀로그램 키보드를 사용할 수 있는 모든 곳에서 페어링하고 사용할 수 있습니다. 품질 키보드를 사용하면 차이가 있으므로 [Microsoft 유니버설 폴딩 가능 키보드](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) 또는 Microsoft Designer Bluetooth [Desktop을](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)사용하는 것이 좋습니다.

## <a name="bluetooth-gamepads"></a>게임 패드 Bluetooth

특히 게임 패드 지원을 사용하도록 설정하는 앱 및 게임과 함께 컨트롤러를 사용할 수 있습니다. 게임 패드는 HoloLens 사용자 인터페이스를 제어하는 데 사용할 수 없습니다.

Xbox One S 함께 제공되는 Xbox 무선 컨트롤러 또는 Xbox One S 기능 Bluetooth 연결용 액세서리로 판매되므로 HoloLens 및 몰입형 헤드셋과 함께 사용할 수 있습니다. Xbox 무선 컨트롤러를 [업데이트해야](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) HoloLens 사용할 수 있습니다.

Bluetooth 게임 패드의 다른 브랜드는 Windows Mixed Reality 디바이스에서 작동할 수 있지만 지원은 애플리케이션에 따라 달라집니다.

## <a name="other-bluetooth-accessories"></a>기타 Bluetooth 액세서리

주변 장치에서 Bluetooth HID 또는 GATT 프로필을 지원하는 한 HoloLens 페어링할 수 있습니다. 키보드, 마우스 및 HoloLens Clicker 외에 다른 Bluetooth HID 및 GATT 디바이스가 완벽하게 작동하려면 Microsoft HoloLens 도우미 애플리케이션이 필요할 수 있습니다.

지원되지 않는 주변 장치는 다음과 같습니다.

* Bluetooth 오디오 프로필의 주변 장치는 지원되지 않습니다.
* 스피커 및 헤드셋과 같은 Bluetooth 오디오 디바이스는 설정 앱에서 사용할 수 있지만 오디오 엔드포인트로 Microsoft HoloLens 지원되지 않습니다.
* Bluetooth 지원 휴대폰 및 PC는 페어링 및 파일 전송에 지원되지 않습니다.

## <a name="unpairing-a-bluetooth-peripheral"></a>Bluetooth 주변 장치 페어링

1. 시작 메뉴에서 **설정** 앱을 엽니다.
2. **디바이스로** 이동
3. 꺼져 있는 경우 Bluetooth 라디오 켜기
4. 사용 가능한 Bluetooth 디바이스 목록에서 디바이스 찾기
5. 목록에서 디바이스를 선택한 **다음, 제거** 단추를 선택합니다.