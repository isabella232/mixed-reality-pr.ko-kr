---
title: 포팅 개요
description: 기존 응용 프로그램을 HoloLens 및 VR의 혼합 현실로 가져오기 위한 다양 한 이식 옵션에 대 한 개요입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: 포팅, unity, 미들웨어, 엔진, UWP, Win32
ms.openlocfilehash: 519dae088e689e0a6e617bf5e2b34f81cc2e265256c4844df7dd34e99172d536
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189423"
---
# <a name="porting-overview"></a>포팅 개요

혼합 현실에서 기존 프로젝트를 이식 하거나 업그레이드 하는 경우에는 앱이 Unity 또는 unreal Engine을 사용 하 여 빌드 되었는지, HoloLens (첫 번째 Gen) 또는 HoloLens 2 또는 SteamVR를 사용 하 여 빌드 되었는지 여부에 따라 포팅 상태가 달라 집니다. 이 개요 페이지에는 각 플랫폼 및 장치에 대 한 현재 권장 사항이 포함 되어 있습니다. 이러한 프로세스는 항상 변경 될 때 다시 확인 해야 합니다.

먼저 [Unity](#unity) 및 [unreal](#unreal) 권장 사항에 따라 프로젝트 대상을 설정 하 고 포팅 시나리오 중 하나 이상을 수행 합니다.

- [HoloLens (첫 번째 Gen) HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [몰입형 VR 헤드셋](#immersive-vr-headsets)
- [2D UWP 앱](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>권장 프로젝트 대상

앱을 다른 대상 장치로 포팅 하는지 여부에 관계 없이 프로젝트를 최신 상태로 유지 하는 것이 중요 합니다. 현재 권장 사항은 아래에 나열 된 엔진 기반 리소스를 참조 하세요.

### <a name="unity"></a>Unity

권장 Unity 및 MRTK 버전에 대 한 최신 지침은 [unity 버전 선택](../unity/choosing-unity-version.md) 페이지를 참조 하세요.

### <a name="unreal"></a>Unreal

권장 되는 Unreal 및 MRTK 버전에 대 한 최신 지침은 최신 [프로젝트 설정](../unreal/unreal-project-setup.md) 페이지를 참조 하세요.

## <a name="porting-scenarios"></a>포팅 시나리오

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>HoloLens 2 HoloLens (첫 번째 Gen) Unity 앱

HoloLens 2으로 이식할 기존 HoloLens (1 세대) Unity 응용 프로그램이 있는 경우 [HoloLens 포팅 문서의](./porting-hl1-hl2.md)지침을 따르세요.

### <a name="immersive-vr-headsets"></a>몰입형 VR 헤드셋

다른 VR 장치에 대 한 콘텐츠를 작성 한 경우에는 모든 공급 업체별 VR Sdk와 잠재적으로 입력 매핑 Api를 대상으로 지정 해야 합니다. [모던 앱 포팅 가이드](porting-guides.md)에서 Unity 및 unreal 포팅 시나리오에 대 한 정보를 찾을 수 있습니다.

Windows Mixed Reality 헤드셋에 대해 업데이트 하려는 SteamVR 환경의 경우 [SteamVR 업데이트 가이드](updating-your-steamvr-application-for-windows-mixed-reality.md)를 참조 하세요.

### <a name="2d-universal-windows-applications"></a>2d 유니버설 Windows 응용 프로그램

Windows Mixed Reality 몰입 형 헤드셋 또는 HoloLens으로 이식 하려는 기존 2d uwp 앱이 있는 경우 [에는 Windows Mixed Reality에 대 한 이식 하는 2d uwp 앱](building-2d-apps.md) 을 참조 하세요.