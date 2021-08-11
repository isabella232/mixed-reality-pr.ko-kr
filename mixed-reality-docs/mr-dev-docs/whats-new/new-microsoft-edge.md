---
title: Windows Mixed Reality 및 새 Microsoft Edge
description: 예상되는 내용, 찾을 업데이트 및 알려진 문제를 포함하여 Mixed Reality 대한 새로운 Microsoft Edge 대해 알아봅니다.
author: mattzmsft
ms.author: mazeller
ms.date: 08/04/2020
ms.topic: article
keywords: edge, new, immersive web, microsoft edge, browser, vr, 360, 360 video, 360 viewer, webxr, webvr
ms.openlocfilehash: 51efc5c4d3afb4d46ba7722867514f740a9f60a4280652fdbd665134f83af23d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218825"
---
# <a name="the-new-microsoft-edge-for-windows-mixed-reality"></a>Windows Mixed Reality 대한 새 Microsoft Edge

[이제 새 Microsoft Edge 다운로드할 수](https://blogs.windows.com/windowsexperience/?p=173496)있지만 고객은 향후 몇 개월 동안 측정된 롤아웃 접근 방식에 따라 Windows 10 [을 사용하여 향후 업데이트를 설치할 때까지 기다릴](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)수도 있습니다. 

이 소식을 **통해 Windows Mixed Reality VR 헤드셋 고객에게 새 Microsoft Edge 예상되는 결과를 알리고 Windows Mixed Reality 향상된 검색 환경을 위해 보류 중인 업데이트를 보여 주려고** 했습니다.

## <a name="introducing-the-new-microsoft-edge"></a>새 Microsoft Edge 소개

새 Microsoft Edge [데스크톱의 Chromium 오픈 소스 프로젝트를 채택하여](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) 고객의 호환성을 높이고 웹 개발자를 위한 웹 조각화를 줄입니다. 또한 WebVR 대신 VR 헤드셋에 대한 몰입형 웹 환경을 만들기 위한 새로운 표준인 WebXR을 출시 시 지원합니다.

>[!IMPORTANT]
>최신 Windows 10 디바이스에 Microsoft Edge 설치하면 PC의 이전(레거시) 버전이 대체됩니다.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>새 Microsoft Edge 준비

Windows Mixed Reality 혼합 현실 홈 새 Microsoft Edge 사용하려는 VR 헤드셋 고객은 혼합 현실 홈 **Win32 애플리케이션(예: 새 Microsoft Edge)의 기본 지원을 위해 Windows 10 버전 1903** 이상으로 업그레이드해야 합니다. Windows 업데이트를 확인하거나 [Windows 10 최신 버전을 수동으로 설치합니다.](https://www.microsoft.com/en-us/software-download/windows10)

혼합 현실 홈 최상의 Microsoft Edge 환경을 위해 Windows 10 **버전 1903 이상에 대한 2020-01 누적 업데이트에 도착하는 새 Microsoft Edge 대한 몇 가지 주요 Windows Mixed Reality 최적화를** 기다리는 것이 좋습니다. 이 업데이트는 1월 말 Windows 업데이트에서 사용할 수 있습니다.

>[!IMPORTANT]
>이러한 업데이트를 받기 전에 새 Microsoft Edge 다운로드하도록 선택하는 경우 Windows Mixed Reality 동작에 몇 가지 알려진 문제가 있습니다(아래에서 확인할 수 있습니다).

## <a name="known-issues"></a>알려진 문제

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Windows 10 버전 1903 이상에 대한 2020-01 누적 업데이트에서 해결된 알려진 문제

- 새 Microsoft Edge 포함하여 Win32 앱을 시작하면 헤드셋 디스플레이가 잠시 중지합니다.
- Microsoft Edge 타일은 Windows Mixed Reality 시작 메뉴 사라집니다("클래식 앱" 폴더에서 찾을 수 있습니다).
- 이전 Microsoft Edge Windows 여전히 혼합 현실 홈 주위에 배치되지만 사용할 수 없습니다. 이러한 창을 활성화하려고 시도하여 데스크톱 앱에서 Edge가 시작됩니다.
- 혼합 현실 홈 하이퍼링크를 선택하면 혼합 현실 홈 대신 바탕 화면에서 웹 브라우저가 시작됩니다.
- WebVR Showcase 앱은 WebVR이 더 이상 지원되지 않는데도 혼합 현실 홈 있습니다.
- 키보드 시작 및 시각적 개체에 대한 일반적인 개선

### <a name="monitor-and-input-handling-issues"></a>모니터링 및 입력 처리 문제

Windows 10 버전 1903 이상에 대한 2020-01 누적 업데이트를 적용한 후 가상 모니터는 Windows Mixed Reality 세션 중에 **설정 > System > Display에** 일반 물리적 모니터로 표시됩니다. 일부 고객, 특히 두 개 이상의 실제 모니터를 사용 하 여 결과적으로 데스크톱 레이아웃 및 입력 처리에 문제가 발생할 수 있습니다.

**이런 일이 발생하는 이유**

Windows Mixed Reality 클래식 Win32 애플리케이션에 대한 지원은 [Windows 10 2019년 5월 업데이트](/windows/mixed-reality/enthusiast-guide/release-notes-may-2019)에서 도입되었습니다. 이 지원을 사용하려면 Win32 애플리케이션을 호스트할 가상 모니터를 만들어야 합니다. 새 Win32 애플리케이션이 시작될 때마다 다른 가상 모니터를 만들어야 합니다. 아쉽게도 가상 모니터를 만드는 작업은 헤드셋 디스플레이가 잠시 중지되는 집약적인 작업입니다. 고객은 이 환경이 불편하고 방해가 되는 환경이라는 피드백을 제공했습니다. 피드백 및 Win32 애플리케이션 사용 증가로 인해 Windows Mixed Reality 시작하는 동안 세 개의 가상 모니터를 미리 할당하기로 결정했습니다. 이렇게 하면 중단을 방지하고 고객이 헤드셋 디스플레이가 고정되지 않고 최대 3개의 동시 Win32 애플리케이션을 시작할 수 있습니다.

**해결 방법**

이후 일부 고객, 특히 여러 물리적 모니터가 있는 고객이 이 가상 모니터 사전 할당을 사용하지 않도록 설정하는 것을 선호한다는 피드백을 받았습니다. 고객이 제어할 수 있도록 다음 Windows 업데이트에서 사용할 수 있는 레지스트리 키 값 변경과 관련된 해결 방법을 사용하도록 설정했습니다.

- Windows 10 버전 2004용 2020-07 누적 업데이트 미리 보기(KB4568831)
- Windows 10 버전 1909용 2020-10 누적 업데이트 미리 보기(KB4580386)
- Windows 10 버전 1903용 2020-10 누적 업데이트 미리 보기(KB4580386)

>[!NOTE]
>레지스트리 키 값을 수정하는 것은 고급 사용자를 위한 것입니다.

>[!WARNING]
>가상 모니터 사전 할당을 사용하지 않으면 Windows Mixed Reality Win32 애플리케이션(예: Steam, 새 Microsoft Edge 또는 Google Chrome)을 시작할 때 헤드셋이 잠시 중지됩니다.

가상 모니터 사전 할당을 사용하지 않도록 설정하려면 다음을 수행합니다.
1. Windows **업데이트에서** 위에 나열된 Windows 10 누적 업데이트 미리 보기 버전 중 하나를 확인하고 사용 가능한 경우 업데이트를 설치합니다. Windows 업데이트 설정 페이지의 **선택적 업데이트** 또는 **고급 옵션에서** 업데이트를 찾을 수 있습니다.
2. **레지스트리 편집기** 시작
3. "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. "PreallocateVirtualMonitors" REG_DWORD 없는 경우 **편집 > 새로 만들기 > DWORD(32비트) 값을** 선택하고 이름으로 PreallocateVirtualMonitors를 입력하여 만듭니다.
5. "PreallocateVirtualMonitors" REG_DWORD 있는 경우(또는 방금 만든 경우) 항목을 두 번 클릭하고 "값 데이터"를 1(기본값)에서 0(영)으로 변경합니다.
    * TRUE - 1
    * FALSE - 0

이제 미리 할당하는 대신 Windows Mixed Reality Win32 애플리케이션을 시작하려고 하면 가상 모니터가 할당됩니다. 이를 다시 설정하고 가상 모니터 사전 할당을 다시 사용하도록 설정하려면 DWORD "값 데이터"를 1로 반환합니다.

### <a name="other-known-issues"></a>기타 알려진 문제

-   Mixed Reality 포털 닫히면 Windows Mixed Reality 열린 웹 사이트가 손실됩니다. Microsoft Edge 창은 혼합 현실 홈 배치된 위치에 유지됩니다.
- 360 뷰어 확장을 포함한 WebXR 환경은 하이브리드 GPU 설정으로 PC에서 올바르게 시작되지 않을 수 있습니다. 새 Microsoft Edge 미리 보기 기능을 사용하도록 설정하여 이 문제를 해결할 수 있습니다. 로 이동하여 `edge://flags` "다중 gpu"를 검색하고 **WebXR 다중 GPU 지원이라는** 플래그를 사용하도록 설정합니다.
-   Microsoft Edge 창의 오디오는 공간화되지 않습니다.
-   **360 뷰어 확장 버전 2.3.8에서 수정됨:** Windows Mixed Reality YouTube에서 360 비디오를 열면 헤드셋에서 비디오가 왜곡될 수 있습니다. Edge를 다시 시작하면 이 문제를 해결하기 위해 360 뷰어 확장을 보이지 않게 업데이트해야 합니다. 주소 표시줄에 을 `edge://system/` 입력하고 "확장" 옆에 있는 **확장** 단추를 선택하여 확장 버전을 확인할 수 있습니다.