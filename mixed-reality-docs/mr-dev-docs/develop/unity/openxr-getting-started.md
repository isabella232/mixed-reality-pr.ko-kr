---
title: Unity 용 Mixed Reality OpenXR 플러그 인 사용
description: Unity 프로젝트용 Mixed Reality OpenXR 플러그 인을 사용 하도록 설정 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 보강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작
ms.openlocfilehash: 9e7f59c57d409d61df73e6d07659bf6c7242202c
ms.sourcegitcommit: 5784336a780486d05db6a627839efe47f08fac36
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97880605"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Unity 용 Mixed Reality OpenXR 플러그 인 사용

Unity 버전 2020.2부터 Microsoft의 Mixed Reality OpenXR 플러그 인 패키지는 UPM (Unity 패키지 관리자)를 사용 하 여 사용할 수 있습니다.

## <a name="prerequisites"></a>필수 조건

* Unity 2020.2 이상
* Unity OpenXR plugin 0.1.1 이상
* Visual Studio 2019 이상
* HoloLens 2 앱 용 Unity에서 **UWP** 플랫폼 지원 설치

> [!NOTE]
> Windows PC에서 VR 응용 프로그램을 작성 하는 경우 Mixed Reality OpenXR 플러그 인이 반드시 필요한 것은 아닙니다. 그러나 HP 반향 G2 컨트롤러에 대 한 컨트롤러 매핑을 사용자 지정 하거나 HoloLens 2와 VR 헤드셋 모두에서 작동 하는 앱을 빌드하는 경우에는 플러그 인을 설치 하는 것이 좋습니다.

## <a name="installing-the-mixed-reality-openxr-plugin"></a>Mixed Reality OpenXR 플러그 인 설치

혼합 현실 OpenXR 플러그 인을 사용 하기 전에 프로젝트에서 **OpenXR 플러그** 인 및 **XR 플러그 인 관리** 패키지를 설치 해야 합니다. 이미 설치한 경우 좋은 방법입니다! 그렇지 않으면 Mixed Reality OpenXR 플러그 인을 설치 하면 자동으로 종속성으로 설치 됩니다.

1. Unity 편집기에서 **편집 > 프로젝트 설정 > 패키지 관리자** 로 이동 합니다.
2. 범위가 지정 된 **레지스트리** 섹션을 확장 하 고, 다음 정보를 입력 하 고, **저장** 을 선택 합니다.
    * **이름을** **Microsoft Mixed Reality** 로 설정 합니다.
    * **URL** 설정 **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**
    * **범위** 를 mixedreality로 설정 **합니다.**

3. **고급 설정** 아래에서 **미리 보기 패키지 사용** 을 선택 합니다.

![프로젝트 설정에서 열려 있는 Unity 패키지 관리자 창의 스크린샷](images/openxr-img-01.png)

Unity 패키지 관리자는 *manifest.js* 이라는 매니페스트 파일을 사용 하 여 설치할 패키지와 설치할 수 있는 패키지를 확인 합니다.

> [!IMPORTANT]
> OpenXR는 Unity에서 여전히 실험적 이며 개발자 환경을 최적화 하기 위해이 프로세스는 시간이 지남에 따라 변경 될 수 있습니다.

### <a name="registering-the-mixed-reality-dependency"></a>Mixed Reality 종속성 등록

Microsoft Mixed Reality 범위 레지스트리가 매니페스트에 추가 된 후에는 OpenXR 패키지를 지정할 수 있습니다.

OpenXR 패키지를 추가 하려면:

1. Visual Studio Code와 같은 텍스트 편집기에서 **[Projectroot]/Packages/manifest.js을** 엽니다.
    1. 여기를 보려면 프로젝트 창의 왼쪽 패널에서 **패키지** 를 마우스 오른쪽 단추로 클릭 합니다. 그런 다음 **탐색기에서 표시** 를 클릭 합니다.
    ![프로젝트 창에 나열 된 패키지의 스크린샷](images/packages.png)
1. 다음과 같이 파일 *에서 패키지/manifest.js* 의 종속성 섹션을 수정 합니다.

    > [!IMPORTANT]
    > 매니페스트 파일에는 여기에 표시 된 것 보다 더 많은 종속성이 있을 수 있습니다. 이러한 항목을 삭제 하지 않고 OpenXR 종속성을 목록에 추가 하기만 하면 됩니다.

    ``` json
      "dependencies": {
        "com.microsoft.mixedreality.openxr": "0.1.1",
      }
    ```

1. 파일을 저장 하 고 Unity 편집기로 다시 전환한 후 **패키지 관리자** 를 열어 플러그 인이 설치 되었는지 확인 합니다.

    ![혼합 현실 OpenXR 플러그 인이 강조 표시 된 unity 편집기에서 열리는 Unity 패키지 관리자의 스크린샷](images/openxr-img-03.png)

    > [!Note]
    > Unity 패키지 관리자를 사용 하 여 OpenXR 패키지를 제거 하는 경우 앞에서 설명한 단계를 사용 하 여 패키지를 다시 추가 해야 합니다.

## <a name="configuring-xr-plugin-management-for-openxr"></a>OpenXR에 대 한 XR 플러그 인 관리 구성

OpenXR을 Unity에서 런타임으로 설정 하려면 다음을 수행 합니다.

1. Unity 편집기에서 **편집 > 프로젝트 설정** 으로 이동 합니다.
2. 설정 목록에서 **XR 플러그 인 관리** 를 선택 합니다.
3. **INITIALIZE XR On Startup** and **OpenXR (미리 보기)** 상자를 선택 합니다.
4. HoloLens 2를 대상으로 하는 경우 UWP 플랫폼에 있는지 확인 하 고 **Microsoft HoloLens 기능 집합** 을 선택 합니다.

![XR 플러그 인 관리를 강조 표시 한 Unity 편집기에서 열리는 프로젝트 설정 패널의 스크린샷](images/openxr-img-05.png)

> [!IMPORTANT]
> **OpenXR 플러그 인 (미리 보기)** 옆에 빨간색 경고 아이콘이 표시 되는 경우 계속 하기 전에 아이콘을 클릭 하 고 **모두 수정** 을 선택 합니다. Unity 편집기를 다시 시작 해야 변경 내용이 적용 될 수 있습니다.

![OpenXR 프로젝트 유효성 검사 창의 스크린샷](images/openxr-img-06.png)

이제 Unity에서 OpenXR를 사용 하 여 개발을 시작할 준비가 되었습니다.  OpenXR 샘플을 사용 하는 방법을 알아보려면 다음 섹션을 계속 진행 합니다.

## <a name="optimization"></a>Optimization

HoloLens 2 용으로 개발 하는 경우 **> OpenXR> Mixed Reality로 이동 하 여 hololens 2에 권장 되는 프로젝트 설정을 적용** 하 여 더 나은 앱 성능을 얻을 수 있습니다.

![OpenXR가 선택 된 혼합 현실 메뉴 항목 열기의 스크린샷](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a>Unity 샘플 장면을 사용해 보세요.

하나 이상의 예제를 활용 하려면 **패키지 관리자** 에서 [arfoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) 를 설치 합니다.

![AR가 강조 표시 된 unity 편집기에서 open Unity 패키지 관리자의 스크린샷](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a>HoloLens 2 샘플

1. Unity 편집기에서 **창 > 패키지 관리자** 로 이동 합니다.
2. 패키지 목록에서 **Mixed Reality OpenXR 플러그 인** 을 선택 합니다.
3. **샘플 목록에서** 샘플을 찾고 **가져오기** 를 선택 합니다.

![Unity 편집기에서 open Reality OpenXR 플러그 인을 선택 하 고 샘플 가져오기 단추가 강조 표시 된 Unity 패키지 관리자의 스크린샷](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> 패키지가 업데이트 되 면 Unity는 가져온 샘플을 업데이트 하는 옵션을 제공 합니다.  가져온 샘플을 업데이트 하면 샘플 및 연결 된 자산에 대 한 모든 변경 내용이 덮어쓰여집니다.

## <a name="next-steps"></a>다음 단계

이제 OpenXR에 대해 프로젝트를 구성 하 고 샘플에 액세스할 수 있으므로, OpenXR 플러그 인에서 현재 지원 되는 [기능](openxr-supported-features.md) 을 확인 하세요.

## <a name="see-also"></a>추가 정보

* [MRTK를 사용하지 않고 프로젝트 구성](configure-unity-project.md)
* [Unity 권장 설정](recommended-settings-for-unity.md)
* [Unity의 권장 성능](performance-recommendations-for-unity.md#how-to-profile-with-unity)
