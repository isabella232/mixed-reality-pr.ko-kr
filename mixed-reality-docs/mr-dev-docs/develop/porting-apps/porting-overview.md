---
title: 포팅 개요
description: 기존 응용 프로그램을 HoloLens 및 VR의 혼합 현실로 가져오기 위한 다양 한 이식 옵션에 대 한 개요입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: 포팅, unity, 미들웨어, 엔진, UWP, Win32
ms.openlocfilehash: 268d98b45aa659614e0266bfd1add7c7ed2f684a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583586"
---
# <a name="porting-overview"></a>포팅 개요

혼합 현실에 대 한 기존 프로젝트를 이식 하거나 업그레이드 하는 경우에는 앱이 Unity 또는 Unreal Engine을 사용 하 여 빌드 되었는지, HoloLens (1 Gen) 또는 HoloLens 2 또는 SteamVR를 대상으로 하는지 여부에 따라 포팅 기능이 달라 집니다. 이 개요 페이지에는 각 플랫폼 및 장치에 대 한 현재 권장 사항이 포함 되어 있습니다. 이러한 프로세스는 항상 변경 될 때 다시 확인 해야 합니다.

먼저 [Unity](#unity) 및 [unreal](#unreal) 권장 사항에 따라 프로젝트 대상을 설정 하 고 포팅 시나리오 중 하나 이상을 수행 합니다.

- [Hololens (첫 번째 Gen)-HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Windows Mixed Reality 헤드셋](#windows-mixed-reality-headsets)
- [SteamVR 앱](#steamvr-applications)
- [2D UWP 앱](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>권장 프로젝트 대상

앱을 다른 대상 장치로 포팅 하는지 여부에 관계 없이 프로젝트를 최신 상태로 유지 하는 것이 중요 합니다. 현재 권장 사항은 아래에 나열 된 엔진 기반 리소스를 참조 하세요.

### <a name="unity"></a>Unity

혼합 현실에서 Unity 개발에 대 한 현재 권장 사항은 **레거시 XR 패키지를 사용 하는 unity 2019 LTS** 입니다. 프로젝트가 Mixed Reality Toolkit를 사용 하는 경우 현재 **Mrtk-Unity 2.5** 인 최신 버전을 사용 하 고 있는지 다시 확인 합니다.

> [!CAUTION]
> XR SDK는이 버전의 Unity와 함께 사용할 수 있지만, Azure 공간 앵커는 현재이 설정과 호환 되지 않습니다. 이 권장 사항은 Unity 용 Azure 공간 앵커 패키지의 이후 릴리스에서 업데이트 될 예정입니다. 
> 
> * Azure 공간 앵커가 필요 하지 않은 경우 [XR에 대 한 Unity 프로젝트를 구성](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) 하 고 [MRTK 및 XR SDK를 사용 하 여 시작할](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html)수 있습니다.
> 
> * 현재 프로젝트에서 XR SDK를 사용 하 고 있으며 Azure 공간 앵커를 사용 하려는 경우 XR SDK를 제거 하 고 레거시 XR 패키지를 다시 설치 하 여 프로젝트 설정을 되돌립니다.


### <a name="unreal"></a>Unreal 

혼합 현실에서의 실제 개발에 대 한 현재 권장 사항은 **Unreal Engine 4.26** 입니다. 프로젝트가 Mixed Reality Toolkit UX 도구를 사용 하는 경우 현재 **Uxt 0.10** 최신 버전을 사용 하 고 있는지 확인 합니다.

## <a name="porting-scenarios"></a>포팅 시나리오

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>Hololens (첫 번째 Gen) Unity 앱-HoloLens 2

HoloLens 2로 이식할 기존 HoloLens (첫 번째 Gen) Unity 응용 프로그램이 있는 경우 [hololens 포팅 문서의](./porting-hl1-hl2.md)지침을 따르세요.

### <a name="windows-mixed-reality-headsets"></a>Windows Mixed Reality 헤드셋

Oculus Rift 또는 HP 반향 G2와 같은 다른 장치에 대 한 콘텐츠를 빌드한 경우 공급 업체별 VR Sdk 및 잠재적으로 입력 매핑 Api의 대상을 변경 해야 합니다. [모던 앱 포팅 가이드](porting-guides.md)에서 Unity 및 unreal 포팅 시나리오에 대 한 정보를 찾을 수 있습니다.

### <a name="steamvr-applications"></a>SteamVR 응용 프로그램

Windows Mixed Reality 헤드셋에 대해 업데이트 하려는 SteamVR 환경의 경우 [SteamVR 업데이트 가이드](updating-your-steamvr-application-for-windows-mixed-reality.md)를 참조 하세요.

### <a name="2d-universal-windows-applications"></a>2D 유니버설 Windows 응용 프로그램

Windows Mixed Reality 몰입 형 헤드셋 또는 HoloLens로 이식 하려는 기존 2D UWP 앱이 있는 경우 [Windows Mixed reality 용 2D uwp 앱 포팅](building-2d-apps.md) 지침을 따르세요.