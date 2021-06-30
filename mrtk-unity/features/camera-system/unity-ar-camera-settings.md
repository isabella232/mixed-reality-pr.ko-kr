---
title: Unity AR 카메라 설정
description: MRTK에서 AR 카메라를 사용하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, AR 카메라,
ms.openlocfilehash: e1c032805bc4b733cfcc51e1ceac5096c73715cf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121201"
---
# <a name="unity-ar-camera-settings-provider"></a>Unity AR 카메라 설정 공급자

Unity AR 카메라 설정 공급자는 Android 및 iOS 디바이스에서 혼합 현실 애플리케이션을 실행할 수 있도록 하는 실험적 MRTK 구성 요소입니다.

## <a name="unity-ar-camera-settings-provider-options"></a>Unity AR 카메라 설정 공급자 옵션

![Unity AR 카메라 설정 구성](../images/camera-system/UnityArSettingsConfiguration.png)

장면에 공급자를 추가하는 방법에 대한 가이드: [iOS 및 Android용 MRTK를 구성하는 방법](../../supported-devices/using-ar-foundation.md)

### <a name="tracking-settings"></a>추적 설정

Unity AR 카메라 설정 공급자는 추적이 수행되는 방식에 대한 구성 옵션을 허용합니다. 이러한 설정은 Unity AR 카메라 설정 공급자 구현에 따라 다릅니다.

**자세 소스**

자세 소스는 사용 가능한 유형의 증강 현실 추적 자세를 정의합니다. 일반적으로 이러한 값은 애플리케이션이 실행되는 디바이스의 구성 요소에 매핑됩니다.

사용 가능한 옵션은 다음 표에 설명되어 있습니다.

| 옵션 | Description |
| --- | --- |
| Center | 헤드 탑재 디바이스의 중심 눈입니다. |
| 색 카메라 | 모바일 디바이스의 색 카메라입니다. |
| Head | 헤드 탑재 디바이스의 헤드 눈이며, 보통 중심 눈 위에 약간 위에 있습니다. |
| 왼쪽 눈 | 헤드 탑재 디바이스의 왼쪽 눈입니다. |
| 왼쪽 자세 | 왼쪽 컨트롤러의 자세입니다. |
| 오른쪽 눈 | 헤드 탑재 디바이스의 오른쪽 눈입니다. |
| 오른쪽 자세 | 오른쪽 컨트롤러의 자세입니다. |

자세 원본의 기본값은 휴대폰 또는 태블릿과 같은 모바일 디바이스에서 투명하게 표시할 수 있도록 **색 카메라** 입니다.

**추적 유형**

추적 유형은 추적에 사용할 자세 부분을 정의합니다.

사용 가능한 옵션은 다음 표에 설명되어 있습니다.

| 옵션 | Description |
| --- | --- |
| 위치 | 디바이스의 위치입니다. |
| 회전 | 디바이스의 회전입니다. |
| 회전 및 위치 | 디바이스의 위치 및 회전입니다. |

추적 형식의 기본값은 **회전 및 위치** 이며, 가장 풍부한 추적 환경을 사용할 수 있습니다.

**업데이트 유형**

업데이트 유형은 프레임 처리 중에 자세 데이터가 샘플링되는 지점을 정의합니다.

사용 가능한 옵션은 다음 표에 설명되어 있습니다.

| 옵션 | Description |
| --- | --- |
| 렌더링 전 | 렌더링 직전에. |
| 업데이트 | 프레임의 업데이트 단계 중. |
| 렌더링 전 및 업데이트 | 업데이트 단계 중 및 렌더링 직전에 |

추적 형식의 기본값은 **업데이트 및 렌더링 전** 으로, 가장 낮은 추적 대기 시간을 사용하도록 설정합니다.

## <a name="see-also"></a>참조

- [카메라 시스템 개요](camera-system-overview.md)
- [카메라 설정 공급자 만들기](create-settings-provider.md)
