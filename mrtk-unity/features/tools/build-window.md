---
title: 빌드 창
description: Unity용 MRTK의 빌드 창 사용에 대한 설명서입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 빌드, 빌드 창, 도구
ms.openlocfilehash: d01fefd09337e2639388a43d94bd8beb93716e3ef7f12a9c924b5755fb594447
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211391"
---
# <a name="build-window"></a>빌드 창
![빌드 & 배포 흐름](images/MRTK_BuildWindow0.png)

MRTK의 빌드 창을 사용하면 MRTK-Unity 프로젝트를 쉽게 빌드하고 & 배포할 수 있습니다. 한 번의 단추 클릭으로 Unity 프로젝트를 빌드하고 Visual Studio 솔루션을 생성할 수 있습니다(. SLN), UWP 앱 패키지(. APPX)를 입력하고 디바이스에 앱 패키지를 설치합니다. 


## <a name="unity-build-options"></a>Unity 빌드 옵션
![빌드 창 - Unity 빌드 옵션 1](images/MRTK_BuildWindow1.png)

이러한 장면들은 Unity Build 설정. 드롭다운 메뉴를 사용하여 대상 디바이스 유형을 변경할 수 있습니다.

## <a name="appx-build-options"></a>Appx 빌드 옵션
![빌드 창 - Appx 빌드 옵션 2](images/MRTK_BuildWindow2.png)

이 탭에는 Visual Studio 솔루션에 대한 구성이 표시됩니다. HoloLens 2 시선 추적 입력 기능을 사용하도록 설정하려면 **응시 입력 기능** 옵션을 선택합니다. 

사용자 지정 3D 앱 시작 관리자 아이콘에 대한 **3D 앱 시작 관리자 모델** 필드에서 .glb 파일을 할당할 수 있습니다. 자세한 내용은 [3D 앱 시작 관리자 디자인 지침을](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 참조하세요.

기본적으로 버전 지정 **옵션에서 자동 증가가** 선택되어 있습니다. AppX 버전은 자동으로 증가합니다.


## <a name="deploy-options"></a>배포 옵션
![빌드 창 - 배포 옵션 3](images/MRTK_BuildWindow3.png)

이 탭에서 장치 포털 대한 사용자 이름 및 암호를 입력하여 디바이스에 연결할 수 있습니다. 

페이지 아래쪽에서 생성된 앱 패키지 목록을 찾을 수 있습니다. 

