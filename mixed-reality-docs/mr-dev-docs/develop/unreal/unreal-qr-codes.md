---
title: Unreal의 QR 코드
description: Unreal 혼합 현실 애플리케이션에서 QR 코드를 설정하고, 사용하고, 추적하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 기능, 설명서, 가이드, 홀로그램, qr 코드, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 689ebe9b904b269c00078245b137bc21f2e56df2b441150c7c6b18c179ac51f4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115205163"
---
# <a name="qr-codes-in-unreal"></a>Unreal의 QR 코드

HoloLens 2는 웹캠을 사용하여 세계 공간에서 QR 코드를 볼 수 있습니다. 즉, 각 코드의 실제 세계 위치에서 홀로그램으로 렌더링합니다. HoloLens 2는 또한 공유 경험을 만들기 위해 여러 디바이스에서 동일한 위치에 홀로그램을 렌더링할 수 있습니다. 애플리케이션에 QR 코드를 추가하기 위한 모범 사례를 따라야 합니다.

- 자동 영역
- 조명 및 배경
- 크기, 거리 및 각도 위치

QR 코드가 앱에 배치될 때 [환경 고려 사항](/hololens/hololens-environment-considerations)에 특히 주의해야 합니다. 이러한 각각의 토픽에 대한 자세한 정보와 필요한 NuGet 패키지를 다운로드하는 방법에 대한 지침은 주 [QR 코드 추적](../platform-capabilities-and-apis/qr-code-tracking.md) 설명서에서 확인할 수 있습니다.

> [!CAUTION]
> QR 코드는 HoloLens에서 기본적으로 추적할 수 있는 유일한 이미지 유형입니다. Unreal의 **UARTrackedImage** 모듈은 HoloLens에서 지원되지 않습니다. 사용자 지정 이미지를 추적해야 하는 경우에는 타사 이미지 인식 라이브러리를 사용하여 디바이스의 [웹캠](unreal-hololens-camera.md)에 액세스한 후 이미지를 처리할 수 있습니다. 

## <a name="enabling-qr-detection"></a>QR 검색 사용

HoloLens 2는 웹캠을 사용하여 QR 코드를 확인해야 하므로 프로젝트 설정에서 사용하도록 설정해야 합니다.
- **편집 > 프로젝트 설정** 을 열고 **플랫폼** 섹션까지 아래로 스크롤한 다음, **HoloLens** 를 선택합니다.
    + **기능** 섹션을 확장하고 **웹캠** 을 선택합니다.  
- 또한 [ARSessionConfig 자산](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)을 추가하여 QR 코드 추적을 옵트인해야 합니다.

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a>추적된 QR 코드 설정

QR 코드는 Unreal의 AR 추적 기하 도형 시스템을 통해 추적 이미지로 표시됩니다. 이 작업을 수행하려면 다음을 수행해야 합니다.
1. 행위자 청사진을 만들고 **ARTrackableNotify** 구성 요소를 추가합니다.

![QR AR 추적 가능 알림](images/unreal-spatialmapping-artrackablenotify.PNG)

2. **ARTrackableNotify** 를 선택하고 **세부 정보** 패널에서 **이벤트** 섹션을 확장합니다.

![QR 이벤트](images/unreal-spatialmapping-events.PNG)

3. **추적 기하 도형 추가** 옆의 **+** 를 클릭하여 이벤트 그래프에 추가합니다.
    - [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 구성 요소 API에서 이벤트의 전체 목록을 확인할 수 있습니다.

![추적된 기하 도형 추가 시 노드 추가](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a>추적된 QR 코드 사용

다음 이미지의 이벤트 그래프는 QR 코드의 가운데에 점을 렌더링하고 그 데이터를 출력하는 데 사용되는 **OnUpdateTrackedImage** 이벤트를 보여 줍니다.

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

진행 상황은 다음과 같습니다.
1. 먼저 추적 이미지를 **ARTrackedQRCode** 에 캐스트하여 현재 업데이트된 이미지가 QR 코드인지 확인합니다.  
2. 인코딩된 데이터는 **QRCode** 변수에서 검색합니다. **GetLocalToWorldTransform** 위치에서 QR 코드의 왼쪽 위를, **GetEstimateSize** 로 크기를 가져올 수 있습니다.

코드에서 [QR 코드 좌표계를 가져올 수](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)도 있습니다.

## <a name="finding-the-unique-id"></a>고유 ID 찾기

모든 QR 코드에는 다음을 통해 찾을 수 있는 고유한 guid ID가 있습니다.
- **As ARTracked QRCode** 핀을 끌어서 놓고 검색하여 **고유 ID 가져오기**

![QR Guid](images/unreal-qr-guid.PNG)

QR 코드를 사용하기 위해서는 뒤에서 많은 작업이 필요하므로 이것이 전부는 아닙니다. 내부 작업을 더 상세히 설명하는 다음 링크를 확인해 보세요.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unreal 개발 검사점 경험을 수행하는 경우 Mixed Reality 플랫폼 기능과 API를 탐색하는 것이 좋습니다. 여기에서 다음 항목을 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [WinRT](unreal-winRT.md)

또는 디바이스나 에뮬레이터에서 앱 배포로 직접 이동합니다.

> [!div class="nextstepaction"]
> [디바이스에 배포](unreal-deploying.md)

언제든지 [Unreal 개발 검사점](unreal-development-overview.md#3-advanced-features)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목
* [공간 매핑](../../design/spatial-mapping.md)
* [홀로그램](../../discover/hologram.md)
* [좌표계](../../design/coordinate-systems.md)