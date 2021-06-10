---
title: 포팅 개요
description: HoloLens 및 VR용 Mixed Reality 기존 애플리케이션을 가져오기 위한 다양한 이식 옵션에 대한 개요입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, unity, middleware, engine, UWP, Win32
ms.openlocfilehash: 9b056bd81a725fea23c1e7f3bfcd9844680086c6
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600502"
---
# <a name="porting-overview"></a>포팅 개요

Mixed Reality 위해 기존 프로젝트를 포팅하거나 업그레이드하는 경우 포팅 여정은 앱이 Unity 또는 Unreal Engine으로 빌드되는지에 따라 달라지고 HoloLens(1세대) 또는 HoloLens 2 또는 SteamVR을 대상으로 합니다. 이 개요 페이지에는 각 플랫폼 및 디바이스에 대한 현재 권장 사항이 포함되어 있습니다. 이러한 프로세스는 항상 변경되기 때문에 다시 확인해야 합니다.

먼저 [Unity](#unity) 및 [Unreal](#unreal) 권장 사항에 따라 프로젝트 대상을 설정한 다음, 하나 이상의 포팅 시나리오를 따릅니다.

- [HoloLens(1세대)에서 HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Windows Mixed Reality 헤드셋](#windows-mixed-reality-headsets)
- [SteamVR 앱](#steamvr-applications)
- [2D UWP 앱](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>권장되는 프로젝트 대상

앱을 다른 대상 디바이스로 이식하는지 여부에 관계없이 프로젝트를 최신 상태로 유지하는 것이 중요합니다. 현재 권장 사항은 아래에 나열된 엔진 기반 리소스를 참조하세요.

### <a name="unity"></a>Unity

Mixed Reality 사용한 Unity 개발에 대한 현재 권장 사항은 **레거시 XR 패키지를 사용하는 Unity 2019 LTS입니다.** 프로젝트에서 Mixed Reality 도구 키트를 사용하는 경우 현재 **MRTK-Unity 2.5** 최신 버전인지 다시 확인합니다.

> [!CAUTION]
> 이 버전의 Unity에서 XR SDK를 사용할 수 있지만 Azure Spatial Anchors 현재 이 설정과 호환되지 않습니다. 이 권장 사항은 Unity용 Azure Spatial Anchors 패키지의 이후 릴리스로 업데이트될 예정입니다.
> 
> * Azure Spatial Anchors 필요하지 않은 경우 [XR용 Unity 프로젝트를 구성하고](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) [MRTK 및 XR SDK를 시작할](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk)수 있습니다.
> 
> * 현재 프로젝트에서 XR SDK를 사용하고 있고 Azure Spatial Anchors 사용하려는 경우 XR SDK를 제거하고 레거시 XR 패키지를 다시 설치하여 프로젝트 설정을 되돌려야 합니다.

### <a name="unreal"></a>Unreal

Mixed Reality Unreal 개발을 위한 현재 권장 사항은 **Unreal Engine 4.26입니다.** 프로젝트에서 Mixed Reality 도구 키트 UX 도구를 사용하는 경우 현재 **UXT 0.10인** 최신 버전을 사용하고 있는지 확인합니다.

## <a name="porting-scenarios"></a>포팅 시나리오

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>HoloLens 2 HoloLens(1세대) Unity 앱

HoloLens 2 이식하려는 기존 HoloLens(1세대) Unity 애플리케이션이 있는 경우 [HoloLens 이식 문서의](./porting-hl1-hl2.md)지침을 따르세요.

### <a name="windows-mixed-reality-headsets"></a>Windows Mixed Reality 헤드셋

OculusTar 또는 HP Reverb G2와 같은 다른 디바이스용 콘텐츠를 빌드한 경우 공급업체별 VR SDK 및 잠재적으로 입력 매핑 API의 대상을 변경해야 합니다. [몰입형 앱](porting-guides.md)포팅 가이드 에서 Unity 및 Unreal 이식 시나리오 모두에 대한 정보를 찾을 수 있습니다.

### <a name="steamvr-applications"></a>SteamVR 애플리케이션

Windows Mixed Reality 헤드셋에 대해 업데이트하려는 모든 SteamVR 환경은 [SteamVR 업데이트 가이드를](updating-your-steamvr-application-for-windows-mixed-reality.md)참조하세요.

### <a name="2d-universal-windows-applications"></a>2D 유니버설 Windows 애플리케이션

Windows Mixed Reality 몰입형 헤드셋 또는 HoloLens로 이식하려는 기존 2D UWP 앱이 있는 경우 Windows Mixed Reality [지침에 대한 이식 2D UWP 앱을](building-2d-apps.md) 따르세요.