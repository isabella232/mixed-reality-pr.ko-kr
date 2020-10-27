---
title: 포팅 가이드
description: 기존 몰입 형 응용 프로그램을 Windows Mixed Reality로 이식 하는 방법을 설명 하는 단계별 연습입니다.
author: JBrentJ
ms.author: alexturn
ms.date: 07/07/2020
ms.topic: article
keywords: 포트, 포팅, unity, 미들웨어, 엔진, UWP, Win32
ms.openlocfilehash: 9822976ab7dac9ae7567e5f38ca44ceee646d098
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638548"
---
# <a name="porting-guides"></a>포팅 가이드

Windows 10에는 몰입 형 및 holographic 헤드셋을 직접 지원 합니다. Rift 또는 HTC Vive와 같은 다른 장치에 대 한 콘텐츠를 빌드한 경우 운영 체제의 플랫폼 API 위에 있는 라이브러리에 대 한 종속성이 있습니다. 기존 Win32 Unity VR 앱을 Windows Mixed Reality로 가져오면 공급 업체의 특정 VR Sdk 사용이 Unity의 공급 업체의 VR Api로 변경 됩니다.

## <a name="porting-overview"></a>포팅 개요

개략적인 수준에서 다음과 같은 단계를 수행 하 여 기존 콘텐츠를 이식할 수 있습니다.
1. **PC에서 Windows 10의 작성자 업데이트 (16299)를 실행 하 고 있는지 확인 합니다.** 이러한 빌드는 혼합 현실 개발에 가장 안정적이 아니므로 Insider Skip에서 preview 빌드를 수신 하는 것이 더 이상 권장 되지 않습니다.
2. **최신 버전의 그래픽 또는 게임 엔진으로 업그레이드 합니다.** 게임 엔진은 Windows 10 SDK 버전 10.0.15063.0 (4 월 2017에 릴리스된) 이상을 지원 해야 합니다.
3. **미들웨어, 플러그 인 또는 구성 요소를 업그레이드 합니다.** 앱에 구성 요소가 있는 경우 최신 버전으로 업그레이드 하는 것이 좋습니다.
4. **중복 된 sdk에 대 한 종속성을 제거** 합니다. 콘텐츠를 대상으로 하는 장치에 따라 Windows Api를 대상으로 지정할 수 있도록 해당 SDK (예: SteamVR)를 제거 하거나 조건부로 컴파일해야 합니다.
5. **빌드 문제를 해결 합니다.** 이때 포팅 연습은 앱, 엔진 및 구성 요소 종속성에 따라 다릅니다.

## <a name="common-porting-steps"></a>일반적인 포팅 단계

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. 올바른 개발 하드웨어가 있는지 확인 합니다.

[도구 설치](../install-the-tools.md#immersive-vr-headset-requirements) 페이지에 권장 되는 개발 하드웨어가 나열 됩니다.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. Windows 10의 최신 비행로 업그레이드

Windows Mixed Reality 플랫폼은 아직 개발 중입니다. Windows 참가자 [프로그램에 가입](https://insider.windows.com/) 하 여 "windows 참가자가 빠르게" 비행에 액세스 하는 것이 좋습니다.
1. [Windows 10 크리에이터 스 업데이트](https://www.microsoft.com/software-download/windows10) 설치
2. Windows 참가자 프로그램에 [참여](https://insider.windows.com/) 합니다.
3. [개발자 모드](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) 사용
4. **설정 > 업데이트 & 보안 섹션** 을 통해 [Windows Insider Fast flight](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) 로 전환 합니다.

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. Visual Studio의 최신 빌드로 업그레이드
* Visual Studio를 사용 하는 경우 가장 최근 빌드로 업그레이드 합니다.
* Visual Studio 2019 [의 도구 설치 페이지를](../install-the-tools.md#installation-checklist) 참조 하세요.

### <a name="4-choose-the-correct-adapter"></a>4. 올바른 어댑터를 선택 합니다.
* 두 개의 Gpu가 있는 노트북 같은 시스템에서 [올바른 어댑터를 대상](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)으로 합니다. 이는 ID3D11Device가 명시적 또는 암시적으로 (미디어 파운데이션) 해당 기능에 대해 생성 되는 Unity 및 네이티브 DirectX 앱에 적용 됩니다.

## <a name="unity-porting-guidance"></a>Unity 포팅 지침

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Unreal 포팅 지침

> [!IMPORTANT]
> HP 반향 G2 컨트롤러를 사용 하는 경우 추가 입력 매핑 지침은 [이 문서](../unreal/unreal-reverb-g2-controllers.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목
* [Windows Mixed Reality 최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [혼합 현실 성능 이해](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity에 대 한 성능 권장 사항](../unity/performance-recommendations-for-unity.md)
* [모션 컨트롤러](../../design/motion-controllers.md)
* [Unity의 제스처 및 모션 컨트롤러](../unity/gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR 추적](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [포팅 가이드](porting-guides.md)