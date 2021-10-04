---
title: Windows Mixed Reality에서 Microsoft Edge 사용
description: Windows Mixed Reality에서 새 Microsoft Edge을 준비 하세요. 에는 필요한 변경 사항, 검색할 업데이트 및 알려진 문제가 포함 됩니다.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed reality, 가상 현실, VR, MR, 홈, 탐색, 가져오기, 앱, 게임, Microsoft Edge, chromium, Edge, 360, 360 video, 360 뷰어
ms.openlocfilehash: 2834adc7325f6b600a5cf5f65c74948e0feb2c57
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436701"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality 및 새 Microsoft Edge

[새 Microsoft Edge](https://www.microsoft.com/edge) 는 다운로드할 수 있으며 Windows 업데이트를 통해 고객에 게 자동으로 롤아웃 되기 시작 했습니다. 

새 Microsoft Edge는 바탕 화면에서 [Chromium 오픈 소스 프로젝트를 채택](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) 합니다. 이렇게 하면 고객에 게 더 나은 호환성이 생성 되며 웹 개발자의 조각화가 줄어듭니다. 또한 WebVR 대신 VR 헤드셋에 대 한 몰입 형 웹 환경을 만드는 새로운 표준인 WebXR 시작 시 지원 합니다.

>[!IMPORTANT]
>최신 Windows 10 또는 Windows 11 장치에 Microsoft Edge를 설치 하는 경우 PC의 이전 (레거시) 버전이 바뀝니다.

## <a name="installing-the-new-microsoft-edge"></a>새 Microsoft Edge 설치 

새 Microsoft Edge를 설치 하기 전에 **Windows 10 버전 1903 이상으로 업그레이드 하거나 Windows Mixed Reality의 새 Microsoft Edge 처럼 네이티브 Win32 응용 프로그램 지원을 위해 Windows 11로 업그레이드** 합니다. Windows 업데이트를 확인 하거나 [최신 버전의 Windows 10](https://www.microsoft.com/software-download/windows10) 또는 Windows 11을 수동으로 설치 합니다.

Windows 10 버전 1903 이상이 나 Windows 11이 있으면 새 Microsoft Edge를 사용할 수 있습니다. 새 Microsoft Edge Windows 업데이트를 통해 롤아웃 되지만, 더 빨리 원하는 경우 [Microsoft Edge 웹 사이트](https://www.microsoft.com/edge) 에서 새 Microsoft Edge를 수동으로 설치할 수 있습니다.

>[!IMPORTANT]
>새 Microsoft Edge는 VR 헤드셋을 위한 몰입 형 웹 환경을 만들기 위한 새로운 표준인 WebXR 지원으로 시작 됩니다. 새 Microsoft Edge를 설치 하는 경우 Microsoft Edge에서 더 이상 WebVR 환경을 재생할 수 없습니다. 

## <a name="known-issues"></a>알려진 문제

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Windows 10 버전 1903 이상 2020-01 누적 업데이트에서 해결 된 알려진 문제

- 새 Microsoft Edge을 포함 하 여 모든 Win32 앱을 시작 하면 헤드셋 디스플레이가 잠깐 중지 됩니다.
- Windows Mixed Reality 시작 메뉴에서 Microsoft Edge 타일이 사라집니다. "클래식 앱" 폴더에서 찾을 수 있습니다.
- 이전 Microsoft Edge에서 Windows는 여전히 혼합 현실 홈에 배치 되지만 사용할 수는 없습니다. 이러한 창을 활성화 하려고 하면 데스크톱 앱에서 Edge가 시작 됩니다.
- Mixed reality 홈에서 하이퍼링크를 선택 하면 혼합 현실 홈 대신 바탕 화면에서 웹 브라우저가 시작 됩니다.
- WebVR 전시 앱은 WebVR 더 이상 지원 되지 않더라도 혼합 현실 홈에 있습니다.
- 키보드 시작 및 시각적 개체에 대 한 일반적인 개선 사항

### <a name="monitor-and-input-handling-issues"></a>모니터 및 입력 처리 문제

Windows 10 버전 1903 이상에 대 한 2020-01 누적 업데이트를 수행한 후에는 Windows Mixed Reality 세션 중에 **> 표시 되는 > 시스템 설정** 일반 물리적 모니터로 가상 모니터가 표시 됩니다. 일부 고객, 특히 실제 모니터가 둘 이상인 경우 데스크톱 레이아웃 및 입력 처리와 관련 된 문제가 발생할 수 있습니다.

**이러한 상황이 발생 하는 이유**

Windows Mixed Reality의 클래식 Win32 응용 프로그램에 대 한 지원은 [Windows 10 2019년 5월 업데이트](/windows/mixed-reality/release-notes-may-2019)에 도입 되었습니다. 이 지원을 사용 하려면 Win32 응용 프로그램을 호스트 하는 가상 모니터를 만들어야 합니다. 새 Win32 응용 프로그램이 시작 될 때마다 다른 가상 모니터를 만들어야 합니다. 불행 하 게도 가상 모니터를 만드는 작업은 헤드셋 표시를 잠깐 중지 하는 데 많이 사용 되는 작업입니다. 고객은 경험을 불쾌 하 고 중단 하는 피드백을 제공 했습니다. 이러한 피드백 때문에 Win32 응용 프로그램의 사용량이 증가 함에 따라이 중단을 방지 하 고 고객이 헤드셋 표시를 중지 하지 않고 최대 3 개의 동시 Win32 응용 프로그램을 시작할 수 있도록 하는 동안 Windows Mixed Reality를 시작 하는 동안 3 개의 가상 모니터를 미리 할당 하기로 결정 했습니다.

**해결 방법**

일부 고객, 특히 여러 물리적 모니터를 사용 하는 고객에 게는이 가상 모니터 사전 할당을 사용 하지 않도록 설정 하는 것이 좋습니다. 고객에 게 더 많은 제어를 제공 하기 위해 다음과 같은 Windows 업데이트를 사용 하 여 레지스트리 키 값을 변경 하는 해결 방법을 사용 하도록 설정 했습니다.

- 2020-07 Windows 10 버전 2004에 대 한 누적 업데이트 미리 보기 (KB4568831)
- 2020-10 Windows 10 버전 1909에 대 한 누적 업데이트 미리 보기 (KB4580386)
- 2020-10 Windows 10 버전 1903에 대 한 누적 업데이트 미리 보기 (KB4580386)

>[!NOTE]
>레지스트리 키 값을 수정 하는 것은 고급 사용자를 위한 것입니다.

>[!WARNING]
>가상 모니터 미리 할당을 사용 하지 않도록 설정 하면 Windows Mixed Reality에서 Win32 응용 프로그램 (예: 스트림, 새 Microsoft Edge 또는 Google Chrome)을 시작할 때 헤드셋이 잠시 중단 될 수 있습니다.

가상 모니터 사전 할당을 사용 하지 않도록 설정 하려면:
1. 위에 나열 된 Windows 10 누적 업데이트 미리 보기 버전 중 하나에 대 한 **Windows 업데이트** 를 확인 하 고 사용 가능한 경우 업데이트를 설치 합니다. Windows 업데이트 설정 페이지의 **옵션 업데이트** 또는 **고급 옵션** 에서 업데이트를 찾을 수 있습니다.
2. **레지스트리 편집기** 시작
3. "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic로 이동 합니다. \"
4. "PreallocateVirtualMonitors" REG_DWORD 없는 경우 **> 새 > DWORD (32 비트) 값을 편집** 하 고 이름으로 preallocatevirtualmonitors를 입력 하 여 만듭니다.
5. "PreallocateVirtualMonitors" REG_DWORD 있는 경우 (또는 방금 만든 경우) 항목을 두 번 클릭 하 고 "값 데이터"를 1 (기본값)에서 0 (영)으로 변경 합니다.
    * TRUE-1
    * FALSE-0

이제 가상 모니터는 미리 할당 하는 대신 Windows Mixed Reality에서 Win32 응용 프로그램을 시작 하려고 할 때 할당 됩니다. 이를 다시 설정 하 고 가상 모니터 미리 할당을 다시 사용 하도록 설정 하려면 DWORD "값 데이터"를 1로 반환 합니다.

### <a name="other-known-issues"></a>기타 알려진 문제

-   Windows Mixed Reality에서 열리는 웹 사이트는 혼합 현실 포털을 닫으면 손실 됩니다. 하지만 Microsoft Edge Windows는 혼합 현실 홈에 배치 된 위치에 그대로 유지 됩니다.
- 하이브리드 GPU 설정이 있는 Pc에서는 360 뷰어 확장을 포함 하 여 WebXR 환경을 제대로 시작 하지 못할 수 있습니다. 새 Microsoft Edge에서 미리 보기 기능을 사용 하도록 설정 하면이 문제를 해결할 수 있습니다. 으로 이동 하 여 `edge://flags` "다중 gpu"를 검색 하 고 **WEBXR 다중 gpu 지원** 이라는 플래그를 사용 하도록 설정 합니다.
-   Microsoft Edge windows의 오디오는 spatialized 되지 않습니다.
-   **360 Viewer 확장 버전 2.3.8에서 수정** 됨: Windows Mixed Reality에서 YouTube의 360 비디오를 열면 비디오가 헤드셋에서 왜곡 될 수 있습니다. Edge를 다시 시작 하면이 문제를 해결 하기 위해 360 뷰어 확장이 업데이트 되지 않습니다. `edge://system/`주소 표시줄에를 입력 하 고 "확장" 옆의 **확장** 단추를 선택 하 여 어떤 확장 버전이 있는지 확인할 수 있습니다.