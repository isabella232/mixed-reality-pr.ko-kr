---
title: Unreal 프로젝트 설정
description: 최신 버전의 Unreal Engine 및 Mixed Reality Feature Tool로 프로젝트를 설정하는 방법을 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, 혼합 현실, 개발, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 홀로그램, 게임 개발, 혼합 현실 헤드셋, Windows Mixed Reality 헤드셋, 가상 현실 헤드셋, 최신, 도구, 시작, 기본 사항, unreal, 도구 키트, 허브, 설치, Windows, HoloLens, OpenXR, MRTK
ms.openlocfilehash: fee0e9a9deb92dffca742e19ebe27d2dd4cb53c0
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905592"
---
# <a name="setting-up-your-unreal-project"></a>Unreal 프로젝트 설정

HoloLens에 기본 제공되는 지원 기능을 최대한 활용하려면 [Unreal Engine 버전 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 이상을 설치하는 것이 좋습니다.

Epic Games 시작 관리자에서 **라이브러리** 탭으로 이동한 다음, **시작** 옆의 드롭다운 화살표를 선택하고 **옵션** 을 클릭합니다. **대상 플랫폼** 에서 **HoloLens 2** 를 선택하고 **적용** 을 클릭합니다.
![Unreal 설치 옵션 HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>Unreal용 Mixed Reality Toolkit 가져오기

![MRTK](../../design/images/MRTK_UX_Hero.png)

MRTK(Mixed Reality Toolkit)는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다. MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다. 도구 키트는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안되었습니다.

아직 혼합 현실 프로젝트가 없는 경우 [HoloLens 2 시작 자습서](tutorials/unreal-uxt-ch1.md)의 처음 세 섹션에 따라 MRTK 프로젝트를 준비합니다.

### <a name="introducing-the-mrtk-hub-for-unreal"></a>MRTK Hub for Unreal 소개

MRTK Hub를 사용하여 MRTK 플러그 인을 획득하는 것이 좋습니다. 이는 개발자가 Microsoft Mixed Reality 플러그 인을 검색하고 업데이트하여 Unreal 프로젝트에 추가할 수 있는 새로운 방법입니다. Unreal 편집기를 벗어나지 않고 플러그 인을 보고, 종속성을 확인하고, 프로젝트에 설치할 수 있습니다.

- 새 Microsoft Mixed Reality 플러그 인을 검색하고 이러한 플러그 인과 종속성을 Unreal 프로젝트에 설치합니다.
- Microsoft Mixed Reality 플러그 인을 최신 상태로 유지합니다.
- 더 이상 필요하지 않은 경우 프로젝트에서 Microsoft Mixed Reality 플러그 인을 제거합니다.

> [!NOTE]
> MRTK Hub for Unreal은 Unreal Engine 버전 4.26 이상에서만 사용할 수 있습니다. Unreal Engine 버전 4.25의 경우 [시작 섹션](unreal-development-overview.md#1-getting-started)에서 설명한 대로 Unreal Engine Marketplace 또는 GitHub에서 MRTK 플러그 인을 얻을 수 있습니다.

#### <a name="installing-the-mrtk-hub"></a>MRTK Hub 설치

[Unreal Engine Marketplace](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-toolkit-hub)에서 플러그 인을 다운로드하고, 프로젝트를 연 다음, _Plugins(플러그 인)_ 메뉴의 _Mixed Reality(혼합 현실)_ 섹션에서 플러그 인을 사용하도록 설정합니다. 메시지가 표시되면 편집기를 다시 시작합니다.

![MRTK Hub 플러그 인 사용](images/hub-enable-plugin.png)

프로젝트에 대한 플러그 인이 사용하도록 설정되면 도구 모음 단추에서 허브에 액세스할 수 있습니다.

![MRTK Hub 창 열기](images/hub-toolbar.png)

#### <a name="installing-mixed-reality-plugins"></a>혼합 현실 플러그 인 설치

허브를 사용하여 플러그 인을 설치하려면 프로젝트에 추가하려는 플러그 인을 선택한 다음, _Install(설치)_ 단추를 누릅니다. 플러그 인을 다운로드하려면 _Issues(문제)_ 상자에 충돌이 없는지 확인하고, _Confirm(확인)_ 을 누릅니다. 플러그 인이 다운로드되면 편집기를 다시 시작하라는 메시지가 표시됩니다. 아쉽게도 편집기는 자동으로 다시 시작할 수 없습니다. 이로 인해 설치가 완료되기 전에 새 편집기 인스턴스가 시작되는 경우가 있습니다.

![MRTK Hub를 사용하여 플러그 인 설치](images/hub-download.png)

편집기를 닫으면 다운로드한 플러그 인의 압축을 풀기 위해 진행률 표시줄과 함께 명령 프롬프트가 표시됩니다. 설치되는 각 플러그 인에 대해 하나의 명령 프롬프트가 표시됩니다. 압축 풀기가 완료되면 편집기를 다시 열고, [혼합 현실 개발 과정](unreal-quickstart.md)을 계속할 수 있습니다.

![명령 프롬프트를 통해 플러그 인 압축을 풀고 있는 MRTK Hub](images/hub-unpack.png)

> [!IMPORTANT]
> 플러그 인이 설치되면 다른 프로젝트 수준 플러그 인처럼 원본 제어에 체크 인해야 합니다.

#### <a name="updating-mixed-reality-plugins"></a>혼합 현실 플러그 인 업데이트

허브를 사용하여 플러그 인을 업데이트하려면 목록에서 업데이트할 플러그 인을 선택하고, _설치_ 단추를 누릅니다. 업데이트된 플러그 인을 다운로드하려면 _Issues(문제)_ 상자에 충돌이 없는지 확인하고, _Confirm(확인)_ 을 누릅니다. 편집기를 다시 시작하여 업데이트를 완료하라는 메시지가 표시됩니다. 플러그 인 업데이트는 편집기를 시작하는 동안 수행되므로 편집기를 다시 열기 전에 압축 풀기가 완료될 때까지 기다릴 필요가 없습니다.

![MRTK Hub를 통해 플러그 인 업데이트](images/hub-update.png)

#### <a name="removing-mixed-reality-plugins"></a>혼합 현실 플러그 인 제거

허브를 사용하여 플러그 인을 제거하려면 제거하려는 플러그 인을 선택한 다음, 드롭다운에서 설치한 버전을 선택합니다. 플러그 인을 제거하려면 _Issues(문제)_ 상자에 충돌이 없는지 확인하고, _Confirm(확인)_ 을 누릅니다. 편집기를 다시 시작하여 제거를 완료하라는 메시지가 표시됩니다.

![MRTK Hub를 통해 플러그 인 제거](images/hub-remove.png)

#### <a name="reviewing-changes-and-detecting-incompatibilities"></a>변경 내용 검토 및 비호환성 검색

허브 창의 아래쪽 섹션에서 프로젝트에 대한 정확한 변경 내용을 볼 수 있습니다. 여기서는 변경 시 문제가 발생할 수 있는 잠재적인 비호환성과 함께 프로젝트에서 추가하거나 제거할 플러그 인을 확인할 수 있습니다.

> [!NOTE]
> _Issues_ 목록은 Unreal Engine 버전 및 플러그 인 종속성 버전의 비호환성을 표시하지만, 자동으로 문제를 수정하거나 수정을 제안하지는 않습니다.

![호환되지 않는 플러그 인 설치 시도](images/hub-issues.png)

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unreal 로고 이미지](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal(GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Unreal에 MRTK를 사용하지 않으려면 모든 상호 작용과 동작을 직접 스크립팅해야 합니다.