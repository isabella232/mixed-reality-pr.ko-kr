---
ms.openlocfilehash: 3306a9925c55c24c4d72ecb58d7c744dd64b283e
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636316"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

[Mrtk의 구성 대화 상자](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) 는 XR SDK 및 레거시 WSA에 대해 깊이 버퍼 설정을 설정 하려고 하지만 해당 탭을 확인 하 고 Unity에서 설정을 확인 하는 것이 좋습니다.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Unity 앱이 Windows에 깊이 버퍼를 제공할지 여부를 설정 하려면 다음을 수행 합니다.

1. 프로젝트 설정 **편집** XR 플러그 인 관리로 이동 하 여  >    >   메뉴 항목이 확장 되어 있는지 확인 합니다.
2. 선택한 XR 런타임에 해당 하는 메뉴 항목을 클릭 합니다 (Windows Mixed Reality 또는 OpenXR). 또한 Windows 독립 실행형 및 유니버설 Windows 플랫폼에 대 한 탭을 사용할 수 있으므로 올바른 빌드 플랫폼이 선택 되었는지 확인 합니다.
3. 을 사용 하도록 설정 하 고 구성 하려면:
    1. OpenXR의 경우 **깊이 제출 모드** 드롭다운에서 깊이 형식 또는 "없음"을 선택 합니다.
    2. Windows Mixed Reality의 경우 **공유 깊이 버퍼** 확인란을 선택 하거나 선택 취소 합니다. 그런 다음 **깊이 버퍼 형식** 드롭다운에서 형식을 선택 합니다.

![Windows XR 플러그 인 깊이 설정 ](../../images/xrsdk-winxr-depth.png)
 ![ OpenXR 깊이 설정](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> 성능 향상을 위해 일반적으로 16 비트 깊이 버퍼를 사용 하는 것이 좋습니다. 그러나 16 비트 깊이 형식을 사용 하는 경우 Unity가이 설정에서 [스텐실 버퍼를 만들지](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 않으므로 일부 unity UI 스크롤 패널과 같이 스텐실 버퍼에 필요한 효과는 작동 하지 않습니다. 이와 반대로 *24 비트 깊이 형식을* 선택 하면 일반적으로 끝점 그래픽 플랫폼에 적용 되는 경우 [8 비트 스텐실 버퍼가](https://docs.unity3d.com/Manual/SL-Stencil.html) 생성 됩니다.

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Unity 앱이 Windows에 깊이 버퍼를 제공할지 여부를 설정 하려면 다음을 수행 합니다.

1. **편집**  >  **프로젝트 설정**  >  **플레이어**  >  **유니버설 Windows 플랫폼 탭**  >  **XR 설정** 으로 이동 합니다.
2. **Windows Mixed REALITY SDK** 항목을 확장 합니다.
3. **깊이 버퍼 공유 사용** 확인란을 선택 하거나 선택 취소 합니다. 새 프로젝트에서 깊이 버퍼 공유 사용은 기본적으로 선택 되어 있지만 이전 프로젝트에서는 기본적으로 선택 취소 되어 있을 수 있습니다.

![레거시 XR 깊이 설정](../../images/wmr-depth.png)

깊이 버퍼를 사용 하면 Windows에서 기본 카메라의 Unity에 설정 된 근처 및 far 비행기를 사용 하 여 깊이 버퍼의 정규화 된 픽셀 당 깊이 값을 측정 단위로 다시 정확히 매핑할 수 있으므로 시각적 품질을 향상 시킬 수 있습니다. 렌더링 과정에서 일반적인 방법으로 깊이 값이 처리 되는 경우에는 일반적으로 여기에 자세히 설명 해야 합니다 .이는 기존 색 픽셀을 통해 표시 되는 동안 깊이 버퍼에 쓰는 반투명 렌더링 패스가 다시 프로젝션을 혼동 하는 것입니다.  렌더링 패스에서 깊이 값이 정확 하지 않은 최종 깊이 픽셀을 많이 사용 하는 경우 "깊이 버퍼 공유 사용"을 선택을 취소 하면 시각적 품질이 향상 될 가능성이 높습니다.

> [!NOTE]
> 성능 향상을 위해 일반적으로 16 비트 깊이 버퍼를 사용 하는 것이 좋습니다. 그러나 16 비트 깊이 형식을 사용 하는 경우 Unity가이 설정에서 [스텐실 버퍼를 만들지](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 않으므로 일부 unity UI 스크롤 패널과 같이 스텐실 버퍼에 필요한 효과는 작동 하지 않습니다. 이와 반대로 *24 비트 깊이 형식을* 선택 하면 일반적으로 끝점 그래픽 플랫폼에 적용 되는 경우 [8 비트 스텐실 버퍼가](https://docs.unity3d.com/Manual/SL-Stencil.html) 생성 됩니다.