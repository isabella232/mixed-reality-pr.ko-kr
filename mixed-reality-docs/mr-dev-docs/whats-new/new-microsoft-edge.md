---
title: Windows Mixed Reality 및 새 Microsoft Edge
description: 예측 대상, 검색할 업데이트 및 알려진 문제를 포함 하 여 혼합 현실의 새로운 Microsoft Edge에 대해 알아봅니다.
author: mattzmsft
ms.author: v-vtieto
ms.date: 09/24/2021
ms.topic: article
keywords: edge, new, 몰입 형 웹, microsoft edge, browser, vr, 360, 360 video, 360 viewer, webxr, webvr
ms.openlocfilehash: ca849f63d2a755639bedba68c47e419528006a6d
ms.sourcegitcommit: 3176df29fb0c9508751bd370f1211031d50d2c14
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2021
ms.locfileid: "129148657"
---
# <a name="the-new-microsoft-edge-for-windows-mixed-reality"></a>Windows Mixed Reality에 대 한 새 Microsoft Edge

[이제 새로운 Microsoft Edge를 다운로드할 수](https://blogs.windows.com/windowsexperience/?p=173496)있지만, 고객은 향후 몇 개월 동안 측정 된 롤아웃 방법에 따라 [향후 업데이트가 Windows 10를 사용 하 여 설치 될 때까지 기다릴](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)수도 있습니다. 

이 뉴스를 사용 하면 **Windows Mixed Reality VR 헤드셋 고객이 새 Microsoft Edge에서 무엇을 인식 하 고 Windows Mixed Reality에서 향상 된 검색 환경을 위해 보류 중인 업데이트를 표시** 하도록 할 수 있습니다.

## <a name="introducing-the-new-microsoft-edge"></a>새 Microsoft Edge 소개

새 Microsoft Edge는 데스크톱의 [Chromium 오픈 소스 프로젝트를 채택](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) 하 여 고객에 게 더 나은 호환성을 만들고 웹 개발자를 위한 웹의 조각화를 줄일 수 있습니다. 또한 WebVR 대신 VR 헤드셋에 대 한 몰입 형 웹 환경을 만드는 새로운 표준인 출시 시 WebXR 지원 합니다.

>[!IMPORTANT]
>최신 Windows 10 장치에 Microsoft Edge를 설치 하는 경우 PC의 이전 (레거시) 버전이 바뀝니다.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>새 Microsoft Edge 준비

Windows Mixed Reality mixed reality 홈에서 새로운 Microsoft Edge를 사용 하려는 VR 헤드셋 고객은 혼합 현실 홈의 **Win32 응용 프로그램 (예: 새 Microsoft Edge)을 기본적으로 지원 하기 위해 Windows 10 버전 1903 이상으로 업그레이드** 해야 합니다. Windows 업데이트를 확인 하거나 [Windows 10 최신 버전을 수동으로 설치](https://www.microsoft.com/en-us/software-download/windows10)합니다.

혼합 현실 홈에서 가장 가능한 Microsoft Edge 환경을 위해 1 월 말에 Windows 업데이트에서 제공 해야 하는 **Windows 10 버전 1903에 대 한 2020-01 누적 업데이트 (이상)와 함께 제공 되는 새 Microsoft Edge에 대 한 일부 키 Windows Mixed Reality 최적화** 를 기다리는 것이 좋습니다.

>[!IMPORTANT]
>이러한 업데이트를 수행 하기 전에 새 Microsoft Edge를 다운로드 하도록 선택 하는 경우 Windows Mixed Reality에서 다음과 같은 알려진 문제가 발생할 수 있습니다. 자세한 내용은 아래를 참조 하세요.

## <a name="known-issues"></a>알려진 문제

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Windows 10 버전 1903 이상 2020-01 누적 업데이트에서 해결 된 알려진 문제

- 새 Microsoft Edge을 포함 하 여 모든 Win32 앱을 시작 하면 헤드셋 디스플레이가 잠깐 중지 됩니다.
- Windows Mixed Reality 시작 메뉴에서 Microsoft Edge 타일이 사라집니다. "클래식 앱" 폴더에서 찾을 수 있습니다.
- 이전 Microsoft Edge에서 Windows는 여전히 혼합 현실 홈에 배치 되지만 사용할 수는 없습니다. 이러한 창을 활성화 하려고 하면 데스크톱 앱에서 Edge가 시작 됩니다.
- Mixed reality 홈에서 하이퍼링크를 선택 하면 혼합 현실 홈 대신 바탕 화면에서 웹 브라우저가 시작 됩니다.
- WebVR 전시 앱은 WebVR 더 이상 지원 되지 않더라도 혼합 현실 홈에 있습니다.
- 키보드 시작 및 시각적 개체에 대 한 일반적인 개선 사항

### <a name="monitor-and-input-handling-issues"></a>모니터 및 입력 처리 문제

Windows 10 버전 1903 이상에 대 한 2020-01 누적 업데이트를 수행 하 고 나면 Windows Mixed Reality 세션 중에 **설정 > 시스템 > 표시** 되는 일반 물리적 모니터로 가상 모니터가 표시 됩니다. 특히 실제 모니터가 둘 이상 있는 일부 고객은 데스크톱 레이아웃 및 입력 처리와 관련 된 문제를 알 수 있습니다.

**이러한 상황이 발생 하는 이유**

Windows Mixed Reality의 클래식 Win32 응용 프로그램에 대 한 지원은 [Windows 10 2019년 5월 업데이트](/windows/mixed-reality/enthusiast-guide/release-notes-may-2019)에 도입 되었습니다. 이 지원을 사용 하려면 Win32 응용 프로그램을 호스트 하는 가상 모니터를 만들어야 합니다. 새 Win32 응용 프로그램이 시작 될 때마다 다른 가상 모니터를 만들어야 합니다. 불행 하 게도 가상 모니터를 만드는 작업은 헤드셋 표시를 잠깐 중지 하는 데 많이 사용 되는 작업입니다. 고객은이에 대 한 피드백을 사용자에 게 제공 하 여 불편을 경험 하 고 있습니다. 사용자 의견 및 향상 된 Win32 응용 프로그램 사용으로 인해 Windows Mixed Reality를 시작 하는 동안 3 개의 가상 모니터를 미리 할당 하기로 결정 했습니다. 이로 인해 중단이 발생 하지 않으며 고객이 헤드셋 표시 중지를 발생 시 키 지 않고 최대 3 개의 동시 Win32 응용 프로그램을 시작할 수 있습니다.

**해결 방법**

일부 고객, 특히 여러 물리적 모니터를 사용 하는 고객에 게는이 가상 모니터 사전 할당을 사용 하지 않도록 설정 하는 것이 좋습니다. 고객 제어를 제공 하기 위해 다음과 같은 Windows 업데이트에서 사용할 수 있는 레지스트리 키 값을 변경 하는 방법을 해결할 수 있습니다.

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

-   Microsoft Edge windows의 오디오는 spatialized 되지 않습니다.

## <a name="see-also"></a>참고 항목

* [WebXR 개요](../develop/javascript/webxr-overview.md)