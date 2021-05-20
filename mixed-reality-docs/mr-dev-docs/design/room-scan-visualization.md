---
title: 실내 스캔 시각화
description: 공간 매핑이 필요한 응용 프로그램은 장치를 사용 하 여 시간 및 세션 간에 데이터를 수집 합니다.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 앱 패턴, 디자인, HoloLens, 회의실 검색, 공간 매핑, 메시, 혼합 현실 헤드셋, windows mixed Reality 헤드셋, 가상 현실 헤드셋, HoloLens
ms.openlocfilehash: 87312a5d5361ac0e8c24a622cf69fe3e9b147ff5
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196408"
---
# <a name="room-scan-visualization"></a>실내 스캔 시각화

공간 매핑이 필요한 응용 프로그램은 장치를 사용 하 여 시간 및 세션 간에 데이터를 수집 합니다. 매핑 데이터의 완성도와 품질은 사용자가 수행한 탐색 크기, 탐색 이후 경과 된 시간, 장치에서 영역을 스캔 한 후 가구 및 문과 같은 개체가 이동 했는지 여부를 포함 하 여 많은 요인에 따라 달라 집니다.

유용한 공간 매핑 데이터를 보장 하기 위해 응용 프로그램 개발자는 다음과 같은 몇 가지 옵션을 사용할 수 있습니다.
* 이미 수집 된 것을 기반으로 합니다. 이 데이터는 처음에 완전 하지 않을 수 있습니다.
* 블 룸 제스처를 사용 하 여 Windows Mixed Reality 홈으로 이동한 다음 환경에 사용 하려는 영역을 탐색 하도록 사용자에 게 요청 합니다. 무선 탭을 사용 하 여 필요한 모든 영역이 장치에 알려져 있는지 확인할 수 있습니다.
* 자체 응용 프로그램에서 사용자 지정 탐색 환경을 구축 합니다.

이러한 모든 경우 탐색 중에 수집 된 실제 데이터는 시스템에 의해 저장 되며 응용 프로그램에서이 작업을 수행할 필요가 없습니다. 회의실 검색 시각화가 작동 하는 것을 확인 하려는 경우 아래 **Holograms-공간 인식** 비디오 데모 디자인을 확인 하세요.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*이 비디오는 "디자인 Holograms" HoloLens 2 앱에서 가져온 것입니다. [여기](https://aka.ms/dhapp)에서 전체 환경을 다운로드 하 고 활용해 보세요.*

## <a name="device-support"></a>디바이스 지원

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>실내 스캔 시각화</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a>사용자 지정 스캔 환경 구축

응용 프로그램은 사용자가 추가 단계를 수행 하 여 완성도와 품질을 향상 시킬 것인지 여부를 판단 하기 위해 환경 시작 시 공간 매핑 데이터를 분석할 수 있습니다. 분석에서 품질을 향상할 것으로 표시 하는 경우 개발자는 다음을 나타내기 위해 전 세계 오버레이에 대 한 시각화를 제공 해야 합니다.
* 사용자가 환경에 포함 해야 하는 총 볼륨의 양
* 사용자가 데이터 개선을 위해 이동 해야 하는 위치

사용자는 "좋은" 검사를 만드는 원인을 모릅니다. 평면도, 실제 벽으로부터의 거리 등 스캔을 평가하라는 메시지가 표시되거나 무엇을 찾아야 하는지 알려주어야 합니다. 개발자는 검색 또는 탐색 단계 중에 공간 매핑 데이터 새로 고침을 포함하는 피드백 루프를 구현해야 합니다.

대부분의 경우 필요한 검사 품질을 얻기 위해 수행해야 하는 작업을 사용자에게 알려주는 것이 가장 좋습니다. 예를 들어, 상한을 살펴보고, 가구 뒤를 살펴보는 등의 경우를 예로 들어 보겠습니다.

## <a name="cached-versus-continuous-spatial-mapping"></a>캐시된 공간 매핑과 연속 공간 매핑 비교

공간 매핑 데이터는 애플리케이션에서 사용할 수 있는 가장 많은 가중치의 데이터 원본입니다. 프레임이 끊어지거나 더듬이는 등의 성능 문제를 방지하려면 이 데이터를 신중하게 사용해야 합니다.

경험 중 활성 검사는 유용하고 해로울 수 있으므로 경험을 기반으로 사용할 방법을 결정해야 합니다.

### <a name="cached-spatial-mapping"></a>캐시된 공간 매핑

캐시된 공간 매핑 데이터가 있는 경우 애플리케이션은 일반적으로 공간 매핑 데이터의 스냅샷을 만들고 환경 중에 이 스냅샷을 사용합니다.

**이점**
* 환경이 실행되는 동안 시스템의 오버헤드가 감소하면 전력, 열 및 CPU 성능이 크게 향상됩니다.
* 공간 데이터의 변경으로 인해 중단되지 않기 때문에 기본 환경을 더 간단하게 구현할 수 있습니다.
* 물리학, 그래픽 및 기타 용도에 대한 공간 데이터의 사후 처리에 대한 단일 시간 비용입니다.

**단점**
* 실제 개체 또는 사람의 이동은 캐시된 데이터에 반영되지 않습니다. 예를 들어 애플리케이션은 지금 문을 닫을 때 열린 문을 고려할 수 있습니다.
* 캐시된 버전의 데이터를 유지하기 위해 잠재적으로 더 많은 애플리케이션 메모리가 있습니다.

이 방법의 좋은 사례는 제어된 환경 또는 테이블 상위 게임입니다.

### <a name="continuous-spatial-mapping"></a>연속 공간 매핑

특정 응용 프로그램은 계속 검색을 사용 하 여 공간 매핑 데이터를 새로 고칠 수 있습니다.

**이점**
* 응용 프로그램에 대 한 별도의 검색 또는 탐색 환경에서 작성 하지 않아도 됩니다.
* 실제 개체의 이동은 약간의 지연이 있지만 게임에서 반영할 수 있습니다.

**단점**
* 주요 환경 구현의 복잡성이 높아집니다.
* 이러한 시스템에서 변경 내용을 증분 방식으로 수집 필요가 있으므로 추가 그래픽 및 물리학 처리에서 발생할 수 있는 잠재적 오버 헤드입니다.
* 높은 전원, 열 및 CPU 영향.

이 메서드에 대 한 좋은 사례는 holograms가 개체를 이동 하는 것으로 예상 되는 경우입니다. 예를 들어 바닥의 드라이브가 열리거나 닫혀 있는지 여부에 따라 한 holographic 자동차를 사용 하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목

* [공간 매핑](spatial-mapping.md)
* [좌표계](coordinate-systems.md)
* [공간 음향 디자인](spatial-sound-design.md)