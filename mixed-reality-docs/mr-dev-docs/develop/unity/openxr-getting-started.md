---
title: Unity 용 Mixed Reality OpenXR 플러그 인 사용
description: Unity 프로젝트용 Mixed Reality OpenXR 플러그 인을 사용 하도록 설정 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 보강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작
ms.openlocfilehash: 97169507e2b61110d2d16580ba957feff3755258
ms.sourcegitcommit: aca5fddb98fbbd9aa22bdf8174d7fdcdb9d4c08a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2021
ms.locfileid: "107894027"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Unity 용 Mixed Reality OpenXR 플러그 인 사용

Unity 버전 2020.2부터 Microsoft의 Mixed Reality OpenXR 플러그 인 패키지는 UPM (Unity 패키지 관리자)를 사용 하 여 사용할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

* Unity 2020.3 LTS 이상
* Unity OpenXR plugin 1.1.1 이상
* Visual Studio 2019 이상
* HoloLens 2 앱 용 Unity에서 **UWP** 플랫폼 지원 설치

> [!NOTE]
> Windows PC에서 VR 응용 프로그램을 작성 하는 경우 Mixed Reality OpenXR 플러그 인이 반드시 필요한 것은 아닙니다. 그러나 HP 반향 G2 컨트롤러에 대 한 컨트롤러 매핑을 사용자 지정 하거나 HoloLens 2와 VR 헤드셋 모두에서 작동 하는 앱을 빌드하는 경우에는 플러그 인을 설치 하는 것이 좋습니다.

## <a name="setting-up-your-project-with-mrtk"></a>MRTK를 사용 하 여 프로젝트 설정

Unity용 MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다. MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼용 애플리케이션 개발을 가속화하기 위한 것입니다. 이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.

> [!div class="nextstepaction"]
> [MRTK를 사용 하 여 프로젝트 설정](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

기능에 대한 자세한 내용은 [MRTK 설명서](/windows/mixed-reality/mrtk-unity)를 살펴보세요.

## <a name="manual-setup-without-mrtk"></a>MRTK 없이 수동 설치

새 Mixed Reality 기능 도구 응용 프로그램을 사용 하 여 OpenXR 플러그 인을 설치 합니다. [설치 및 사용 지침](welcome-to-mr-feature-tool.md) 을 따르고 Mixed reality Toolkit 범주의 **Mixed Reality OpenXR 플러그 인** 패키지를 선택 합니다.

![Open xr 플러그 인이 강조 표시 된 혼합 현실 기능 도구 패키지 창](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>빌드 대상 설정

데스크톱 VR를 대상으로 하는 경우 새 Unity 프로젝트에서 기본적으로 선택 된 PC 독립 실행형 플랫폼을 사용 하는 것이 좋습니다.

![PC, Mac & 독립 실행형 플랫폼이 강조 표시 된 unity 편집기에서 열리는 빌드 설정 창의 스크린샷](images/wmr-config-img-3.png)

HoloLens 2를 대상으로 하는 경우 유니버설 Windows 플랫폼로 전환 해야 합니다.

1.  **파일 > 빌드 설정** ...을 선택 합니다.
2.  플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 선택 합니다.
3.  **Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다.
4.  **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
5.  **Build Type(빌드 형식)** 을 **D3D** 로 설정합니다.
6.  **UWP SDK** 를 **Latest installed(최근에 설치)** 로 설정합니다.
7.  디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.

![유니버설 Windows 플랫폼 강조 표시 된 unity 편집기에서 열린 빌드 설정 창의 스크린샷](images/wmr-config-img-4.png)

플랫폼을 설정한 후에는 내보낼 때 Unity에서 2D 보기 대신 [몰입 형 보기](../../design/app-views.md) 를 만들도록 해야 합니다.

## <a name="configuring-xr-plugin-management-for-openxr"></a>OpenXR에 대 한 XR 플러그 인 관리 구성

OpenXR을 Unity에서 런타임으로 설정 하려면 다음을 수행 합니다.

1. Unity 편집기에서 **편집 > 프로젝트 설정** 으로 이동 합니다.
2. 설정 목록에서 **XR 플러그 인 관리** 를 선택 합니다.
3. **INITIALIZE XR On Startup** and **OpenXR** 상자를 선택 합니다.
4. HoloLens 2를 대상으로 하는 경우 UWP 플랫폼에 있는지 확인 하 고 **Microsoft HoloLens 기능 집합** 을 선택 합니다.

![XR 플러그 인 관리를 강조 표시 한 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-img-05.png)

## <a name="optimization"></a>최적화

HoloLens 2 용으로 개발 하는 경우 **> OpenXR> Mixed Reality로 이동 하 여 hololens 2에 권장 되는 프로젝트 설정을 적용** 하 여 더 나은 앱 성능을 얻을 수 있습니다.

![OpenXR가 선택 된 혼합 현실 메뉴 항목 열기의 스크린샷](images/openxr-img-08.png)

> [!IMPORTANT]
> **OpenXR 플러그 인** 옆에 빨간색 경고 아이콘이 표시 되 면이 아이콘을 클릭 하 고 계속 하기 전에 **모두 수정** 을 선택 합니다. Unity Editor를 다시 시작해야 변경 내용이 적용될 수 있습니다.

![OpenXR 프로젝트 유효성 검사 창의 스크린샷](images/openxr-img-06.png)

이제 Unity에서 OpenXR를 사용 하 여 개발을 시작할 준비가 되었습니다.  OpenXR 샘플을 사용 하는 방법을 알아보려면 다음 섹션을 계속 진행 합니다.

## <a name="try-out-the-unity-sample-scenes"></a>Unity 샘플 장면을 사용해 보세요.

### <a name="hololens-2-samples"></a>HoloLens 2 샘플

1. Unity 편집기에서 **창 > 패키지 관리자** 로 이동 합니다.
2. 패키지 목록에서 **Mixed Reality OpenXR 플러그 인** 을 선택 합니다.
3. **샘플 목록에서** 샘플을 찾고 **가져오기** 를 선택 합니다.

![Unity 편집기에서 open Reality OpenXR 플러그 인을 선택 하 고 샘플 가져오기 단추가 강조 표시 된 Unity 패키지 관리자의 스크린샷](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> 패키지가 업데이트 되 면 Unity는 가져온 샘플을 업데이트 하는 옵션을 제공 합니다.  가져온 샘플을 업데이트 하면 샘플 및 연결 된 자산에 대 한 모든 변경 내용이 덮어쓰여집니다.

## <a name="using-mrtk-with-openxr-support"></a>OpenXR 지원과 함께 MRTK 사용

MRTK-Unity 2.5.3 릴리스부터 혼합 현실 OpenXR 플러그 인을 지원 합니다.

1. 혼합 현실 [기능 도구](welcome-to-mr-feature-tool.md) 를 다시 열어 혼합 현실 도구 키트 (아직 없는 경우)를 설치 합니다. OpenXR 지원은 **Foundation** 패키지에 있습니다.
2. 검사기에서 MixedReality Toolkit 구성 요소 스크립트로 이동 하 고 **Defaultopenxrconfigurationprofile** 프로필로 전환 합니다.

    ![검사기의 Mixed Reality Toolkit 구성 요소에서 MRTK 구성 전환 스크린샷](images/openxr-img-11.png)

    1. [OpenXR로 마이그레이션하](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)는 방법에 대 한 자세한 내용은 MRTK 설명서를 참조 하세요.

> [!NOTE]
> 이전 버전의 MRTK에서 업그레이드 하는 경우 asset **/MixedRealityToolkit/link.xml** 파일에 다음 줄이 있는지 확인 합니다.
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> 이 줄은 MRTK 2.5.4 이상으로 시작한 경우 기본적으로 추가 됩니다.

## <a name="next-steps"></a>다음 단계

이제 OpenXR에 대해 프로젝트를 구성 하 고 샘플에 액세스할 수 있으므로, OpenXR 플러그 인에서 현재 지원 되는 [기능](openxr-supported-features.md) 을 확인 하세요.

## <a name="have-feedback"></a>피드백이 있나요?

OpenXR는 여전히 실험적 이므로 피드백을 제공 하는 데 도움이 되도록 피드백을 보내 주셔서 감사 합니다. [](https://aka.ms/unityforums) **Microsoft**  +  **OpenXR** 및 **HoloLens 2** 또는 **Windows Mixed Reality** 를 사용 하 여 포럼 게시물에 태그를 지정 하 여 Unity 포럼에서이를 찾을 수 있습니다.

## <a name="see-also"></a>참고 항목

* [MRTK를 사용하지 않고 프로젝트 구성](configure-unity-project.md)
* [Unity 권장 설정](recommended-settings-for-unity.md)
* [Unity의 권장 성능](performance-recommendations-for-unity.md#how-to-profile-with-unity)
