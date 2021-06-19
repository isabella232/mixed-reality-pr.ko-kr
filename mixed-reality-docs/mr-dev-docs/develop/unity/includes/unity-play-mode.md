---
ms.openlocfilehash: 40d24083ec83b9d6faebc00cf801d1f6f55fddd7
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392298"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. HoloLens에서 **Microsoft Store** 로 이동 하 여 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 앱을 설치 합니다.
1. HoloLens에서 **Holographic Remoting Player** 앱을 시작 합니다.
1. Unity에서 **편집** 메뉴로 이동 하 여 **프로젝트 설정** 을 선택 합니다.
1. **XR 플러그 인 관리** 를 선택 합니다.
1. **Windows 독립 실행형** 탭이 선택 되어 있는지 확인 하 고 목록에서 **OpenXR** 및 **windows Mixed Reality 기능 집합** 을 찾은 후 확인란을 선택 합니다.
1. 그런 다음 **창** 메뉴로 이동 하 여 **XR** 하위 메뉴를 확장 하 고 **OpenXR Editor 원격** 작업을 선택 합니다.

    ![XR 플러그 인 관리가 강조 표시 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](../images/openxr-features-img-02.png)

1. **편집기 원격 기능 사용** 을 클릭 합니다.

    ![기능이 강조 표시 된 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](../images/openxr-features-img-03.png)

1. 누락 된 **종속성 사용** 단추가 표시 되 면 클릭 합니다. 단추 위의 오류 상자에는 활성화 된 기능과 그 이유에 대 한 설명이 나와 있습니다.
1. **원격 호스트 이름** 에 HOLOLENS의 IP 주소를 입력 합니다.
   1. 필요에 따라 다른 설정을 변경 합니다.
   1. 재생 모드를 시작 하면 편집기에서 연결을 시도 합니다.
1. 재생 모드를 시작 하 고 HoloLens에서 앱을 경험 하려면 **재생** 단추를 선택 합니다. 재생 모드에서 c # 스크립트를 디버깅 하려면 [Visual Studio를 Unity에 연결](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)합니다.

> [!NOTE]
> 버전 0.1.0에서 Holographic Remoting 런타임은 앵커를 지원 하지 않으며 ARAnchorManager 기능은 원격 작업을 통해 작동 하지 않습니다.  이 기능은 이후 릴리스에서 제공 될 예정입니다.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 플러그 인](#tab/winxr)

1. HoloLens에서 **Microsoft Store** 로 이동 하 여 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 앱을 설치 합니다.
1. HoloLens에서 **Holographic Remoting Player** 앱을 시작 합니다.
1. Unity에서 **편집** 메뉴로 이동 하 여 **프로젝트 설정** 을 선택 합니다.
1. **XR 플러그 인 관리** 를 선택 합니다.
1. **Windows 독립 실행형** 탭이 선택 되어 있는지 확인 하 고 목록에서 **windows Mixed Reality** 를 찾은 다음 해당 확인란을 선택 합니다.
1. 그런 다음 **창** 메뉴로 이동 하 여 **XR** 하위 메뉴를 확장 하 고 **Windows XR 플러그 인 원격** 기능을 선택 합니다.
1. **에뮬레이션 모드** 를 **원격에서 장치로** 설정 합니다.
1. **원격 컴퓨터** 의 경우 HOLOLENS의 IP 주소를 입력 합니다.
1. 연결 하려면 다음 중 하나를 수행 합니다.
   1. 수동으로 연결 하려면 **재생 시 연결** 을 선택 취소 하 고 **연결** 을 선택 합니다. **연결 상태가** **연결 됨** 으로 변경 되 고 HoloLens에서 화면이 비어 있는 것을 볼 수 있습니다.
   1. 자동으로 연결 하려면 **재생 시 연결** 을 선택 합니다. 재생 모드를 시작 하면 편집기에서 연결을 시도 합니다.
1. 재생 모드를 시작 하 고 HoloLens에서 앱을 경험 하려면 **재생** 단추를 선택 합니다. 재생 모드에서 c # 스크립트를 디버깅 하려면 [Visual Studio를 Unity에 연결](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)합니다.

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)

1. HoloLens에서 **Microsoft Store** 로 이동 하 여 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 앱을 설치 합니다.
1. HoloLens에서 **Holographic Remoting Player** 앱을 시작 합니다.
1. Unity에서 **창** 메뉴로 이동 하 여 **XR** 하위 메뉴를 확장 하 고 **Holographic 에뮬레이션** (unity 2019에서 사용 되지 않는 것으로 표시 됨)을 선택 합니다.
1. **에뮬레이션 모드** 를 **원격에서 장치로** 설정 합니다.
1. 첫 번째 생성 HoloLens 또는 HoloLens 2를 사용 하는 경우에 따라 **장치 버전** 을 설정 합니다.
1. **원격 컴퓨터** 의 경우 HOLOLENS의 IP 주소를 입력 합니다.
1. **연결** 을 선택합니다. **연결 상태가** **연결 됨** 으로 변경 되 고 HoloLens에서 화면이 비어 있는 것을 볼 수 있습니다.
1. 재생 모드를 시작 하 고 HoloLens에서 앱을 경험 하려면 **재생** 단추를 선택 합니다. 재생 모드에서 c # 스크립트를 디버깅 하려면 [Visual Studio를 Unity에 연결](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)합니다.
