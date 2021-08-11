---
ms.openlocfilehash: f579cb73389d23be5959d212d4243361f00a27b8475ce74a16acc2bffa7a192b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192184"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. HoloLens **Microsoft Store** 이동하여 **[홀로그램 Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 앱을 설치합니다.
1. HoloLens **홀로그램 Remoting Player** 앱을 시작합니다.
1. Unity에서 **편집** 메뉴로 이동하여 **Project 설정** 선택합니다.
1. **XR 플러그 인 관리를** 선택합니다.
1. Windows **독립 실행형** 탭이 선택되어 있는지 확인하고, 목록에서 **OpenXR** 및 **Windows Mixed Reality 기능 집합을** 찾고, 해당 확인란을 선택합니다.
1. **다음으로, 창** 메뉴로 이동하여 **XR** 하위 메뉴를 확장하고 **OpenXR Editor Remoting을** 선택합니다.

    ![XR 플러그 인 관리가 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](../images/openxr-features-img-02.png)

1. **편집기 Remoting 사용을** 클릭합니다.

    ![기능이 강조 표시된 Unity 편집기에서 열린 프로젝트 설정 패널의 스크린샷](../images/openxr-features-img-03.png)

1. **누락된 Dependencies 사용** 단추가 나타나면 해당 단추도 클릭합니다. 단추 위의 오류 상자는 사용 중인 기능과 이유를 설명합니다.
1. **원격 호스트 이름** 에 HoloLens IP 주소를 입력합니다.
   1. 필요에 따라 다른 설정을 변경합니다.
   1. 재생 모드가 시작되면 편집기에서 연결을 시도합니다.
1. 재생 단추를 선택하여 **재생** 모드를 시작하고 HoloLens 앱을 경험합니다. 재생 모드에서 C# 스크립트를 디버그하려면 [unity에 Visual Studio 연결합니다.](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)

> [!NOTE]
> 버전 0.1.0부터 홀로그램 Remoting 런타임은 앵커를 지원하지 않으며 ARAnchorManager 기능은 Remoting을 통해 작동하지 않습니다.  이 기능은 향후 릴리스에서 출시될 예정입니다.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 플러그 인](#tab/winxr)

1. HoloLens **Microsoft Store** 이동하여 **[홀로그램 Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 앱을 설치합니다.
1. HoloLens **홀로그램 Remoting Player** 앱을 시작합니다.
1. Unity에서 **편집** 메뉴로 이동하여 **Project 설정** 선택합니다.
1. **XR 플러그 인 관리를** 선택합니다.
1. **PC, Mac & Linux 독립 실행형** 탭이 선택되어 있는지 확인하고 목록에서 **Windows Mixed Reality** 찾아 확인란을 선택합니다.
1. **다음으로, 창** 메뉴로 이동하여 **XR** 하위 메뉴를 확장하고 **Windows XR 플러그 인 Remoting을** 선택합니다.
1. **에뮬레이션 모드를** **원격으로 디바이스 로** 설정합니다.
1. **원격 컴퓨터** 의 경우 HoloLens IP 주소를 입력합니다.
1. 연결하려면 다음 중 하나를 수행합니다.
   1. 수동으로 연결하려면 **재생 에서 커넥트** 선택을 취소하고 **커넥트** 선택합니다. **연결 상태가 연결됨으로** 변경되고 HoloLens 화면이 비어 있는 것을 볼 수 있습니다. 
   1. 자동으로 연결하려면 **재생에서 커넥트** 확인합니다. 재생 모드가 시작되면 편집기에서 연결을 시도합니다.
1. 재생 단추를 선택하여 **재생** 모드를 시작하고 HoloLens 앱을 경험합니다. 재생 모드에서 C# 스크립트를 디버그하려면 [unity에 Visual Studio 연결합니다.](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)

1. HoloLens **Microsoft Store** 이동하여 **[홀로그램 Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 앱을 설치합니다.
1. HoloLens **홀로그램 Remoting Player** 앱을 시작합니다.
1. Unity에서 **창** 메뉴로 이동하여 **XR** 하위 메뉴를 확장하고 **홀로그램 에뮬레이션(Unity** 2019에서 사용되지 않는 것으로 표시됨)을 선택합니다.
1. **에뮬레이션 모드를** **원격으로 디바이스 로** 설정합니다.
1. 1세대 HoloLens 또는 HoloLens 2 사용하는 경우 에 따라 **디바이스 버전을** 설정합니다.
1. **원격 컴퓨터** 의 경우 HoloLens IP 주소를 입력합니다.
1. **연결** 을 선택합니다. **연결 상태가 연결됨으로** 변경되고 HoloLens 화면이 비어 있는 것을 볼 수 있습니다. 
1. 재생 단추를 선택하여 **재생** 모드를 시작하고 HoloLens 앱을 경험합니다. 재생 모드에서 C# 스크립트를 디버그하려면 [unity에 Visual Studio 연결합니다.](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)
