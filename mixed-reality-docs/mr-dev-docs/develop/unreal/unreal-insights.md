---
title: Unreal Insights를 사용하여 프로파일링
description: HoloLens 2에서 Unreal Insights를 사용 하는 방법에 대해 알아봅니다.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 개발, 프로 파일링, Unreal insights, 설명서, 가이드, 기능, holograms, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: b41d36679adfb35b5cc3561b8d5e7734654e7fb5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580835"
---
# <a name="profiling-with-unreal-insights"></a>Unreal Insights를 사용하여 프로파일링 

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) 는 Unreal Engine에서 데이터를 수집, 분석 및 시각화 하는 프로 파일링 시스템입니다. 프로 파일링 시스템은 응용 프로그램 성능이 향상 될 수 있는 최적화 병목 상태와 영역을 찾는 데 도움이 될 수 있습니다. 일반적으로 편집기에서 바로 Unreal Insights를 사용 하도록 설정 하지만 HoloLens 2의 경우 명령줄을 사용 해야 합니다.  

## <a name="setup"></a>설치 프로그램

Unreal를 사용 하면 실제 정보를 사용 하지 않는 명령줄 매개 변수를 사용 하 여 HoloLens 시작 관리자에서 "사용자 지정 프로필"을 만들고 구성할 수 있습니다.

1.  명령 프롬프트에서 **ipconfig** 명령을 사용 하 여 컴퓨터의 IP 주소를 찾습니다. IP 주소는 ipconfig에 나열 된 IPv4 주소입니다. 명령줄 매개 변수를 설정 하는 경우 나중에이 점을 염두에 두어야 합니다.

> [!IMPORTANT]
> VPN 뒤에 있는 경우 VPN을 통해 제공 되는 IP 주소를 대신 제공 해야 할 수 있습니다.

![Ipconfig 명령에 대 한 명령줄 결과의 스크린샷](images/unreal-insights-img-01.png)

2.  Unreal Engine 패널의 맨 위로 이동 하 고 **시작** 단추 아래에서 **Device Manager** 를 엽니다.

![장치 관리자가 강조 표시 된 시작 옵션의 스크린샷](images/unreal-insights-img-02.png)

3.  Device Manager에서 **목록에 없는 장치 추가** 를 선택 합니다.

![Unreal engine에서 열린 장치 관리자의 스크린샷](images/unreal-insights-img-03.png)

4. **플랫폼 선택** 을 클릭 하 고 **HoloLens** 를 선택 합니다.

![HoloLens가 강조 표시 된 목록에 없는 장치 드롭다운 추가의 스크린샷](images/unreal-insights-img-04.png)

5.  IPoverUSB를 사용 하는 경우 장치 식별자로 127.0.0.1:10080을 입력 합니다. 각 필드에 HoloLens 사용자 및 암호를 입력 하 고 원하는 대로 **표시 이름을** 입력 합니다.

> [!IMPORTANT]
> 장치 식별자는 1 단계에서 찾은 Unreal Insights를 실행 하는 컴퓨터가 아니라 HoloLens의 IP 주소입니다.

![장치 관리자의 HoloLens 장치 세부 정보 스크린샷](images/unreal-insights-img-05.png)

6.  **추가** 를 선택 하면 장치 관리자의 장치 목록에 HoloLens가 표시 됩니다.

![장치 목록에 추가 된 HoloLens 스크린샷](images/unreal-insights-img-06.png)

## <a name="launch"></a>Launch

1. **시작** 단추 아래 UE4 패널에서 **프로젝트 시작 관리자** 를 엽니다.

![프로젝트 시작 관리자가 강조 표시 된 시작 옵션의 스크린샷](images/unreal-insights-img-07.png)

2. 사용자 지정 **+** **시작 프로필** 아래에서 사용자 지정 프로필을 만들려면 단추를 선택 합니다. 만든 후에는 나중에 언제 든 지이 프로필을 편집할 수 있습니다.

![사용자 지정 시작 프로필이 강조 표시 된 프로젝트 시작 관리자의 스크린샷](images/unreal-insights-img-08.png)

3. HoloLens 사용자 지정 시작 프로필에서 **프로필 편집** 단추를 선택 하 고 다음을 구성 합니다.
    * **책에서** **쿡** 를 선택 하 여 장치에 복사를 사용 하도록 설정 합니다.
    * 보관 **하 시겠습니까?** 를 선택 하 여 디스크 공간을 절약 하기  위해 삭제 하지 않고 생성 된 .appxbundle를 유지 하는 것이 좋습니다. 원하는 경우 .appxbundle의 위치를 지정 하 고 개발 빌드로 전환 합니다.

![책 및 HoloLens가 강조 표시 된 프로필 구성의 쿡 옵션 스크린샷](images/unreal-insights-img-09.png)

4. **빌드를 배포 하는 방법을** 설정 하 고, **장치에 복사** 하 여 UI의 **시작** 섹션을 활성화 합니다.

![장치에 복사를 사용 하는 배포 옵션이 강조 표시 된 프로젝트 시작 관리자의 스크린샷](images/unreal-insights-img-10.png)

5. **시작** 섹션에서 **추가 명령줄 매개 변수** 를 설정 합니다. 매개 변수는 번들로 패키지 되 고 시작 시 사용 되는 ue4commandline.txt 파일에 기록 됩니다. 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * 먼저 다음을 수행 하세요. **-tracehost = IP_OF_YOUR_PC-trace = Log, Bookmark, Frame, CPU, GPU, LoadTime, File, Net**
    * 사용 가능한 시작 매개 변수의 전체 목록은 [Unreal Insights 참조 설명서](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)에서 확인할 수 있습니다.

> [!NOTE]
> "IP_OF_YOUR_PC"는 1 단계에서 찾은 IP 주소입니다. 이는 HoloLens의 IP 주소가 아니라, Unreal Insights를 실행 하는 컴퓨터의 IP 주소입니다.

> [!IMPORTANT]
> 추적이 매우 빠르게 커질 수 있습니다. 추적 크기를 낮게 유지 하는 데 필요한 채널만 사용 하도록 설정 합니다.

![시작 구성 옵션의 스크린샷](images/unreal-insights-img-11.png)

6. 앱을 시작 하기 전에 Unreal Insights를 시작 합니다. 그렇지 않으면 실제 정보를 앱 이전에 적절 하 게 초기화할 수 없습니다.
    * Unreal Insights 실행 파일은 일반적으로 다음과 같이 이진 엔진 폴더에 저장 됩니다. "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![실행 되는 unreal insights 실행 파일의 스크린샷](images/unreal-insights-img-12.png)

6.  **뒤로** 를 선택 하 여 **프로젝트 시작 관리자** 대화의 루트로 돌아갑니다.
7.  편집기로 돌아와서 사용자 지정 시작 프로필에서 **시작** 을 클릭 합니다.

![사용자 지정 시작 프로필의 스크린샷](images/unreal-insights-img-13.png)

8.  프로젝트가 패키지 되 고 장치에 설치 되 고 시작 되었는지 확인 합니다.

## <a name="profiling"></a>프로파일링

Unreal Insights로 돌아가서 프로 파일링을 시작 하려면 장치에 대 한 **라이브** 연결을 선택 합니다.

프로젝트 간에 사용자 지정 프로필이 공유 됩니다. 여기에서 매번이 작업을 수행 하지 않고 만든 사용자 지정 프로필을 사용할 수 있습니다. [설정 섹션](#setup)에서 3 ~ 6 단계를 사용 하 여 사용 하지 않는 작업을 시작할 때마다 장치에 대 한 연결을 다시 만들어야 합니다.

## <a name="see-also"></a>참고 항목
* [Unreal Insights 설명서](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

