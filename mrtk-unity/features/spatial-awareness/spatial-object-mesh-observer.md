---
title: 공간 개체 메시 관찰자
description: MRTK의 공간 메시 관찰자에 대 한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: f28f8dcb320332b8ff8942ae0b442c0817d6d0b790347daa419cfc24dc0d60fc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209126"
---
# <a name="spatial-object-mesh-observer"></a>공간 개체 메시 관찰자

Unity 편집기에서 환경 메시 데이터를 제공 하는 편리한 방법은 클래스를 사용 하는 것입니다 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) . *공간 개체 메시 관찰자* 는 공간 메시를 나타내기 위해 3d 모델 데이터를 가져올 수 있는 [공간 인식 시스템용](spatial-awareness-getting-started.md) 편집기 전용 데이터 공급자입니다. *공간 개체 메시 관찰자* 의 일반적인 용도 중 하나는 Microsoft HoloLens을 통해 검색 된 데이터를 가져와 Unity 내에서 다양 한 환경에 대 한 환경을 어떻게 활용할 수 있는지 테스트 하는 것입니다.

## <a name="getting-started"></a>시작

이 가이드에서는 *공간 개체 메시 관찰자* 를 설정 하는 과정을 안내 합니다. 이 기능을 사용 하도록 설정 하는 세 가지 주요 단계가 있습니다.

1. 공간 인식 시스템 프로필에 *공간 개체 메시 관찰자* 추가
1. 환경 메시 데이터 개체 설정
1. [메시 관찰자 프로필 속성의 나머지 구성](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a>*공간 개체 메시 관찰자* 프로필 설정

1. 원하는 *혼합 현실 Toolkit* 구성 프로필을 선택 하거나 장면에서 *혼합 현실 Toolkit* 개체를 선택 합니다.
1. *공간 인식 시스템* 탭을 열거나 확장 합니다.
1. *"공간 관찰자 추가"* 단추를 클릭 합니다.

    ![공간 관찰자 추가](../images/spatial-awareness/AddObserver.png)

1. *SpatialObjectMeshObserver* 유형 선택

    ![공간 개체 메시 관찰자 선택](../images/spatial-awareness/SelectObjectObserver.png)

1. 원하는 *공간 메시 개체* 를 선택 합니다. 기본적으로 관찰자는 예제 모델을 사용 하 여 구성 됩니다. 이 모델은 Microsoft HoloLens를 사용 하 여 만들어졌지만 [새 스캔 메시 개체를 만들](#acquiring-environment-scans)수 있습니다.
1. [메시 관찰자 프로필 속성의 나머지 구성](configuring-spatial-awareness-mesh-observer.md)

    ![메시 개체 선택](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a>공간 개체 메시 관찰자 프로필 정보

*공간 개체 메시 관찰자* 는 3d 모델에서 데이터를 로드 하므로 아래에 설명 된 표준 메시 관찰자 설정 중 일부를 사용할 수 없습니다.

**업데이트 간격**

*공간 개체 메시 관찰자* 는 모델이 로드 될 때 모든 메시를 응용 프로그램에 보냅니다. 업데이트 간의 시간 델타를 시뮬레이션 하지 않습니다. 응용 프로그램은 및를 호출 하 여 메시 이벤트를 다시 받을 수 있습니다 [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .

**고정 관찰자**

*공간 개체 메시 관찰자* 는 모든 3d 메시 개체가 고정 되어 있고 원본을 무시 하지 않는 것으로 간주 합니다.

**관찰자 모양 및 익스텐트**

*공간 개체 메시 관찰자* 는 전체 3d 메시를 응용 프로그램에 보냅니다. 관찰자 모양 및 익스텐트는 고려 되지 않습니다.

**세부 정보 및 삼각형/입방 미터**

관찰자는 응용 프로그램에 메시를 보낼 때 3D 모델 LODs를 찾으려고 시도 하지 않습니다.

## <a name="acquiring-environment-scans"></a>환경 검색 획득

이 섹션에서는 *공간 개체 메시 관찰자* 와 함께 사용할 *공간 메시 개체* 파일을 만들고 수집 하기 위한 추가 정보를 간략하게 설명 합니다.

### <a name="windows-device-portal"></a>Windows Device Portal

[Windows 장치 포털](/windows/mixed-reality/using-the-windows-device-portal) 은 Microsoft HoloLens 장치에서 공간 메시를 .obj 파일로 다운로드 하는 데 사용할 수 있습니다.

1. HoloLens를 사용 하 여 원하는 환경을 쉽게 탐색 하 고 볼 때 검색
1. Windows 장치 포털을 사용 하 여 HoloLens에 커넥트
1. *3D 보기* 페이지로 이동 합니다.
1. *공간 매핑* 섹션에서 *업데이트* 단추를 클릭 합니다.
1. *공간 매핑* 섹션에서 *저장* 단추를 클릭 하 여 obj 파일을 PC에 저장 합니다.

> [!NOTE]
> **HoloToolkit 파일**
>
> 많은 개발자 들은 이전에 HoloToolkit를 사용 하 여 환경을 검사 하 고 방 파일을 만들었습니다. 이제 혼합 현실 Toolkit는 Unity에서 gameobject로 이러한 파일을 가져와 관찰자에서 *공간 메시 개체로* 사용할 수 있습니다.

## <a name="see-also"></a>추가 정보

- [프로필](../profiles/profiles.md)
- [혼합 현실 Toolkit 프로필 구성 가이드](../../configuration/mixed-reality-configuration-guide.md)
- [공간 인식 시작](spatial-awareness-getting-started.md)
- [장치에서 메시 관찰자 구성](configuring-spatial-awareness-mesh-observer.md)
- [코드를 통해 메시 관찰자 구성](usage-guide.md)
- [Windows 디바이스 포털 사용](/windows/mixed-reality/using-the-windows-device-portal)
