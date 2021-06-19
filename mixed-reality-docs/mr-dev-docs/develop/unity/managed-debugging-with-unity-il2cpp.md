---
title: Unity를 사용 하 여 관리 디버깅
description: 이 문서에서는 Unity IL2CPP UWP 프로젝트에서 관리 되는 디버거를 실행 하는 방법을 설명 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, visual studio, 디버깅, il2cpp, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, UWP
ms.openlocfilehash: 48f5fbd4b2ac217a3f840117595aa36fb3d7c10e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394507"
---
# <a name="managed-debugging-with-unity"></a>Unity를 사용 하 여 관리 디버깅

HoloLens 및 HoloLens 2 용 Unity IL2CPP UWP 빌드에 관리 되는 디버거를 연결 하려면 다음 단계를 수행 합니다.

1. [멀티 캐스트](https://en.wikipedia.org/wiki/Multicast)를 지 원하는 네트워크에 있어야 합니다.
2. **UWP 게시 설정 기능** 으로 이동 하 여 **Internetclientserver** 및 **PrivateNetworkClientServer** 를 확인 합니다.

    ![UWP 게시 설정 기능](images/il2cpp-debugging-capabilities.png)

3. Unity UWP 빌드 설정 구성:
    - 개발 빌드
    - 스크립트 디버깅
    - 관리 되는 디버거 대기 (옵션)

    ![UWP 빌드 설정](images/il2cpp-debugging-build.png)

4. Unity에서 빌드합니다.
5. Visual Studio 솔루션에서 장치에 빌드 및 배포 합니다. **디버그** 또는 **릴리스** 구성을 사용 하 여 빌드해야 합니다. **마스터** 구성은 Unity 프로파일러를 사용 하지 않도록 설정 하 고 최적의 디버깅을 방지할 수 있습니다. 필요한 경우 솔루션에서 appxmanifest.xml의 기능 목록에 있는 **인터넷 (클라이언트 & 서버)** 및 **개인 네트워크 (클라이언트 & 서버)** 를 확인 합니다.
6. 장치가 PC와 동일한 네트워크에 연결 되어 있는지 확인 하 고 장치에서 앱을 시작 합니다.
7. 장치가 USB를 통해 PC에 연결 **되지** 않았는지 확인 합니다.
8. Unity에서 스크립트 중 하나를 두 번 클릭 하 고 표시 되는 Visual Studio 솔루션으로 이동 하 여 표시 하 고 편집 합니다.
9. 디버그 > Unity 디버거를 연결 합니다.

    ![Unity 디버거 연결](images/il2cpp-debugging-attach.png)

10. 목록에서 장치를 선택 하 고 "확인"을 클릭 하 여 연결 합니다.

    ![디바이스 목록](images/il2cpp-debugging-machines.png)

## <a name="see-also"></a>참조 

* [C # 디버깅](/visualstudio/get-started/csharp/tutorial-debugger)
