---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638735"
---
# <a name="all-platforms"></a>[모든 플랫폼](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>HP 동작 컨트롤러 플러그 인 사용 

상호 작용 프로필 및 컨트롤러 매핑은 HP 동작 컨트롤러 플러그 인에 있습니다 .이 플러그 인은 컨트롤러 매핑을 사용 하지 않도록 설정 해야 합니다.

![OpenXRHPController 플러그 인 사용](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>시작 및 HMDPluginPriority 구성

SteamVR를 사용 하는 Unreal의 입력에는 몇 가지 차이점이 있습니다.  프로젝트를 설정할 때 먼저 vr를 추가 하 여 SteamVR의 새 입력 시스템을 사용 하는지 확인 **합니다. SteamVR. EnableVRInput = 1** 을 **엔진/Config/ConsoleVariables.ini** 의 **시작** 섹션으로 구성 합니다.  이 ini는 프로젝트 디렉터리가 아닌 엔진 설치 디렉터리에 있습니다.

![시작 구성 업데이트](../images/reverb-g2-img-07.png)

HP 동작 컨트롤러 플러그 인은 OpenXR를 사용 하도록 설정 합니다.  OpenXR를 사용 하지 않는 경우 ConsoleVariables.ini와 동일한 디렉터리에서 BaseEngine.ini SteamVR의 HMDPluginPriority를 편집 해야 합니다.  SteamVR 값을 OpenXRHMD 값 보다 크게 변경 합니다.

![HMDPluginPriority 구성을 업데이트 하는 중](../images/reverb-g2-img-08.png)


