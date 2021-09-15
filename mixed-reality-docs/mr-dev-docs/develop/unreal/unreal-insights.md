---
title: Unreal Insights를 사용하여 프로파일링
description: HoloLens 2 Unreal Insights 사용하는 방법을 알아봅니다.
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 개발, 프로파일링, unreal insights, 설명서, 가이드, 기능, 홀로그램, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: a77d7795cd7e8c281ebaa2ef89bb6bc9152f5f9c
ms.sourcegitcommit: 5d13ff165f4d08a3b028935fb39539a45a30f7e8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779389"
---
# <a name="profiling-with-unreal-insights"></a>Unreal Insights를 사용하여 프로파일링

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) Unreal Engine에서 데이터를 수집, 분석 및 시각화하는 프로파일링 시스템입니다. 프로파일링 시스템은 최적화 병목 현상 및 앱 성능 향상을 사용할 수 있는 영역을 찾는 데 도움이 될 수 있습니다. 일반적으로 편집기에서 바로 Unreal Insights 사용하도록 설정하지만 HoloLens 2 명령줄을 사용해야 합니다.

## <a name="setup"></a>설치

Unreal을 사용하면 Unreal Insights 사용하도록 설정하는 명령줄 매개 변수를 사용하여 HoloLens 시작 관리자에서 "사용자 지정 프로필"을 만들고 구성할 수 있습니다.

1. 명령 프롬프트에서 **ipconfig** 명령을 사용하여 컴퓨터의 IP 주소를 찾습니다. IP 주소는 ipconfig에 나열된 IPv4 주소입니다. 나중에 명령줄 매개 변수를 설정할 때는 이 점을 염두에 두어야 합니다.

> [!IMPORTANT]
> VPN 뒤에 있는 경우 VPN을 통해 제공된 IP 주소를 대신 제공해야 할 수 있습니다.

![ipconfig 명령에 대한 명령줄 결과의 스크린샷](images/unreal-insights-img-01.png)

2. 주 편집기 창의 "편집" 도구 모음에서 **Project 설정** 엽니다.

![Project 설정 강조 표시된 편집 드롭다운의 스크린샷](images/unreal-insights-img-15.png)

3. **플랫폼** 헤더를 찾고 HoloLens 선택할 때까지 왼쪽 **패널을 Scroll down.**

![HoloLens 강조 표시된 왼쪽 Project 설정 패널의 플랫폼 섹션 스크린샷](images/unreal-insights-img-15.png)

4. **기능** 섹션에 "인터넷 클라이언트", "인터넷 클라이언트 서버" 및 "프라이빗 네트워크 클라이언트 서버"가 선택되어 있음을 확인합니다.

![인터넷 클라이언트, 인터넷 클라이언트 서버 및 프라이빗 네트워크 클라이언트 서버가 선택된 기능 옵션의 스크린샷](images/unreal-insights-img-14.png)

## <a name="launch"></a>Launch

1. **시작** 단추 아래의 UE4 패널에서 **Project 시작 관리자** 엽니다.

![프로젝트 시작 관리자가 강조 표시된 시작 옵션의 스크린샷](images/unreal-insights-img-07.png)

2. 사용자 **+** 지정 실행 프로필 아래에 사용자 지정 프로필을 만들려면 단추를 **선택합니다.** 만든 후에는 나중에 언제든지 이 프로필을 편집할 수 있습니다.

![사용자 지정 시작 프로필이 강조 표시된 프로젝트 시작 관리자의 스크린샷](images/unreal-insights-img-08.png)

3. HoloLens 사용자 지정 시작 **프로필에서** 프로필 편집 단추를 선택합니다. **빌드** 섹션에서 빌드 **UAT를** 확인하고 **추가 명령줄 매개 변수** 를 설정합니다.
   - 시작에 대해 다음을 시도합니다. **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**
   - [Unreal Insights 참조 설명서](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)에서 사용 가능한 시작 매개 변수의 전체 목록을 찾을 수 있습니다.

> [!NOTE]
> "IP_OF_YOUR_PC"는 1단계에서 찾은 IP 주소입니다. 이 주소는 HoloLens IP 주소가 아니라 Unreal Insights 실행하는 컴퓨터의 IP 주소입니다.

> [!IMPORTANT]
> 추적은 매우 빠르게 커질 수 있습니다. 추적 크기를 낮게 유지하는 데 필요한 채널만 사용하도록 설정합니다.

![프로필 구성의 빌드 옵션 스크린샷](images/unreal-insights-img-17.png)

4. Cook **to** **the Book을** 선택하여 디바이스에 복사를 사용하도록 설정합니다. **맵이 맵** 지도 선택되어 있는지 확인합니다.

![책별 쿡과 HoloLens 강조 표시된 프로필 구성의 쿡 옵션 스크린샷](images/unreal-insights-img-09.png)

5. **빌드를 로컬로 패키지** & **저장소로 패키지하는** 방법을 설정합니다. 나중에 필요하므로 선택한 파일 경로에 유의하세요.

![로컬로 패키지 및 저장으로 설정된 프로필 구성의 패키지 옵션 스크린샷](images/unreal-insights-img-18.png)

6. **빌드를 배포하려면 어떻게** 해야 합니까?를 **배포하지 않음으로** 설정합니다.

![배포가 배포 안 됨으로 설정된 프로필 구성의 배포 옵션 스크린샷](images/unreal-insights-img-19.png)

8. **뒤로를** 선택하여 **Project 시작 관리자** 대화 상자의 루트로 돌아갑니다.
9. 편집기로 돌아가서 사용자 지정 시작 프로필에서 **시작을** 클릭합니다.

![사용자 지정 시작 프로필의 스크린샷](images/unreal-insights-img-13.png)

10. 프로젝트가 빌드되는 것을 본 다음, appxbundle(5단계의 패키지 경로)을 디바이스 포털을 통해 HoloLens 배포합니다.

11. Unreal Insights 시작합니다. Unreal Insights 실행 파일은 일반적으로 "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"과 같이 이진 엔진 폴더에 저장됩니다.

![실행 중인 unreal insights 실행 파일의 스크린샷](images/unreal-insights-img-12.png)

12. HoloLens 앱을 시작합니다.

## <a name="profiling"></a>프로파일링

Unreal Insights 돌아가서 디바이스에 **대한 라이브** 연결을 선택하여 프로파일링을 시작합니다.

사용자 지정 프로필은 프로젝트 간에 공유됩니다. 여기에서 매번 이 작업을 수행하는 대신 만든 사용자 지정 프로필을 사용할 수 있습니다. [설치 섹션의](#setup)3~6단계를 통해 Unreal을 시작할 때마다 디바이스에 대한 연결을 다시 만들어야 합니다.

## <a name="see-also"></a>참고 항목

- [Unreal Insights 설명서](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)
