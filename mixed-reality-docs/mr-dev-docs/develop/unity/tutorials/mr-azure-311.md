---
title: HoloLens(1세대) 및 Azure 311 - Microsoft Graph
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Microsoft Graph 활용하고 생산성을 구동하는 데이터에 연결하는 방법을 알아봅니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, microsoft graph, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 16fb7853d202c39399b48595a17e7e9b2edf224f18d5e315c5ddcf4a0054d8f7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215265"
---
# <a name="hololens-1st-gen-and-azure-311---microsoft-graph"></a>HoloLens(1세대) 및 Azure 311 - Microsoft Graph

>[!NOTE]
>Mixed Reality 아카데미 자습서는 HoloLens(1세대) 및 Mixed Reality 몰입형 헤드셋을 염두에 두고 설계되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다.  이러한 자습서는 HoloLens 2에 사용되는 최신 도구 집합 또는 상호 작용으로 업데이트되지 **_않습니다_**.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2 위해 개발하는 방법을 보여 주는 새로운 자습서 시리즈가 나중에 게시될 예정입니다.  이 알림은 해당 자습서가 게시될 때 해당 자습서에 대한 링크로 업데이트됩니다.

이 과정에서는 *Microsoft Graph* 사용하여 혼합 현실 애플리케이션 내에서 보안 인증을 사용하여 Microsoft 계정 로그인하는 방법을 알아봅니다. 그런 다음 애플리케이션 인터페이스에서 예약된 모임을 검색하고 표시합니다.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* 다양한 Microsoft 서비스에 액세스할 수 있도록 설계된 API 세트입니다. Microsoft는 Microsoft Graph 관계로 연결된 리소스의 행렬이라고 설명합니다. 즉, 애플리케이션이 모든 종류의 연결된 사용자 데이터에 액세스할 수 있습니다. 자세한 내용은 Microsoft [Graph 페이지를 참조하세요.](https://developer.microsoft.com/graph)

개발에는 사용자가 응시하고 구를 탭하도록 지시하는 앱 만들기가 포함됩니다. 그러면 사용자에게 Microsoft 계정 안전하게 로그인하라는 메시지가 표시됩니다. 계정에 로그인하면 사용자는 해당 날로 예약된 회의 목록을 볼 수 있습니다.

이 과정을 완료하면 다음을 수행할 수 있는 혼합 현실 HoloLens 애플리케이션이 있습니다.

1.  탭 제스처를 사용하여 개체를 탭하면 사용자에게 Microsoft 계정에 로그인하라는 메시지가 표시됩니다(로그인할 앱 밖으로 이동한 다음 다시 앱으로 다시 이동).
2.  해당 날로 예약된 회의 목록을 봅니다. 

애플리케이션에서 결과를 디자인과 통합하는 방법은 사용자 에게 달려 있습니다. 이 과정은 Unity 프로젝트와 Azure 서비스를 통합하는 방법을 교육하기 위해 고안되었습니다. 이 과정에서 얻은 지식을 활용하여 혼합 현실 애플리케이션을 개선하는 것이 여러분의 작업입니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 311: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>필수 조건

> [!NOTE]
> 이 자습서는 Unity 및 C#에 대한 기본적인 경험이 있는 개발자를 위해 설계되었습니다. 또한 이 문서 내의 필수 조건 및 작성된 지침은 작성 당시 테스트 및 확인된 내용을 나타냅니다(2018년 7월). [도구 설치](../../install-the-tools.md) 문서에 나열된 대로 최신 소프트웨어를 자유롭게 사용할 수 있지만, 이 과정의 정보가 아래 나열된 내용보다 최신 소프트웨어에서 찾을 수 있는 정보와 완벽하게 일치한다고 가정해서는 안 됩니다.

이 과정에서는 다음 하드웨어 및 소프트웨어를 사용하는 것이 좋습니다.

- 개발 PC
- [개발자 모드를 사용하도록 설정된 Windows 10 Fall Creators Update(이상)](../../install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- 개발자 모드가 설정된 [Microsoft HoloLens](/hololens/hololens1-hardware)
- Azure 설정 및 Microsoft Graph 데이터 검색을 위한 인터넷 액세스
- 유효한 **Microsoft 계정(개인** 또는 직장/학교)
- 동일한 Microsoft 계정을 사용하여 현재 날에 예약된 몇 가지 회의

### <a name="before-you-start"></a>시작하기 전에

1.  이 프로젝트를 빌드하는 데 문제가 발생하지 않도록 하려면 이 자습서에서 언급한 프로젝트를 루트 또는 루트에 가까운 폴더에 만드는 것이 좋습니다(긴 폴더 경로로 인해 빌드 시 문제가 발생할 수 있습니다).
2.  HoloLens 설정하고 테스트합니다. HoloLens 설정을 지원해야 하는 경우 [HoloLens 설정 문서 를 방문하세요.](/hololens/hololens-setup) 
3.  새 HoloLens 앱 개발을 시작할 때 보정 및 센서 튜닝을 수행하는 것이 좋습니다(때로는 각 사용자에 대해 이러한 작업을 수행하는 데 도움이 될 수 있습니다). 

보정에 대한 도움말은 [HoloLens 보정 문서에 대한 이 링크를](/hololens/hololens-calibration#hololens-2)따르세요.

센서 튜닝에 대한 도움말은 [HoloLens 센서 튜닝 문서에 대한 링크를](/hololens/hololens-updates)따르세요.

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>1장 - 애플리케이션 등록 포털에서 앱 만들기

먼저 **애플리케이션 등록 포털** 에서 애플리케이션을 만들고 등록해야 합니다.

이 장에서는 *Microsoft Graph* 호출하여 계정 콘텐츠에 액세스할 수 있는 서비스 키도 찾을 수 있습니다.

1.  [Microsoft 애플리케이션 등록 포털로](https://apps.dev.microsoft.com) 이동하여 Microsoft 계정으로 로그인합니다. 로그인하면 **애플리케이션 등록 포털** 로 리디렉션됩니다.

2.  내 **애플리케이션** 섹션에서 **앱 추가** 단추를 클릭합니다.

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > **애플리케이션 등록 포털은** 이전에 *Microsoft Graph* 작업했는지 여부에 따라 다르게 보일 수 있습니다. 아래 스크린샷은 이러한 다양한 버전을 표시합니다.

3.  애플리케이션의 이름을 추가하고 **만들기를** 클릭합니다.

    ![](images/AzureLabs-Lab311-03.png)

4.  애플리케이션이 만들어지면 애플리케이션 기본 페이지로 리디렉션됩니다. 애플리케이션 **ID를** 복사하고 안전한 곳에 이 값을 기록해 두세요. 코드에서 곧 사용할 것입니다.

    ![](images/AzureLabs-Lab311-04.png)

5.  **플랫폼** 섹션에서 **네이티브 애플리케이션이** 표시되는지 확인합니다. *그렇지 않은* 경우 **플랫폼 추가를** 클릭하고 **네이티브 애플리케이션 을** 선택합니다.

    ![](images/AzureLabs-Lab311-05.png)

6.  동일한 페이지와 **Microsoft Graph 권한** 섹션에 Scroll down 애플리케이션에 대한 추가 권한을 추가해야 합니다. 위임된 권한 옆에 있는 **추가** **를 클릭합니다.**

    ![](images/AzureLabs-Lab311-06.png)

7.  애플리케이션에서 사용자의 일정에 액세스하도록 하려면 **Calendars.Read라는** 확인란을 선택하고 **확인을** 클릭합니다.

    ![](images/AzureLabs-Lab311-07.png)

8.  아래쪽으로 스크롤하여 **저장** 단추를 클릭합니다.

    ![](images/AzureLabs-Lab311-08.png)

9.  저장이 확인되고 **애플리케이션 등록 포털** 에서 로그아웃할 수 있습니다.

## <a name="chapter-2---set-up-the-unity-project"></a>2장 - Unity 프로젝트 설정

다음은 혼합 현실로 개발하기 위한 일반적인 설정이며, 따라서 다른 프로젝트에 적합한 템플릿입니다.

1.  *Unity를* 열고 **새로** 만들기를 클릭합니다.

    ![](images/AzureLabs-Lab311-09.png)

2.  Unity 프로젝트 이름을 제공해야 합니다. **MSGraphMR 을** 삽입합니다. 프로젝트 템플릿이 **3D 로** 설정되어 있는지 확인합니다. **위치를** 적절한 위치로 설정합니다(루트 디렉터리에 가까울수록 좋습니다). 그런 다음 **프로젝트 만들기를** 클릭합니다.

    ![](images/AzureLabs-Lab311-10.png)

3.  Unity가 열려 있는 경우 기본 **스크립트 편집기가** **Visual Studio** 로 설정되어 있는지 확인하는 것이 좋습니다. 기본 설정 **편집으로**  >   이동한 다음 새 창에서 **외부 도구** 로 이동합니다. **외부 스크립트 편집기를** **Visual Studio 2017로** 변경합니다. 기본 **설정** 창을 닫습니다.

    ![](images/AzureLabs-Lab311-11.png)

4.  **파일** 빌드 설정 이동하여  >   유니버설 **Windows 플랫폼을** 선택한 **다음, 플랫폼 전환** 단추를 클릭하여 선택 항목을 적용합니다.

    ![](images/AzureLabs-Lab311-12.png)

5.  **파일** 빌드 설정 동안  >  다음을 확인합니다.

    1. **대상 디바이스가** **HoloLens**
    2. **빌드 유형이** **D3D로** 설정됩니다.
    3. **SDK가** **최신 설치로 설정됩니다.**
    4. **Visual Studio 버전이** 최신 **설치로 설정됩니다.**
    5. **빌드 및 실행이** **로컬 컴퓨터로 설정됩니다.**
    6. 장면을 저장하고 빌드에 추가합니다.

        1. 열린 장면 추가 를 선택하여 이 작업을 **수행합니다.** 저장 창이 나타납니다.

            ![](images/AzureLabs-Lab311-13.png)

        2. 이 폴더 및 향후 장면에 대한 새 폴더를 만듭니다. 새 **폴더** 단추를 선택하여 새 폴더를 만들고 이름을 **Scenes로** 지정합니다.

            ![](images/AzureLabs-Lab311-14.png)

        3. 새로 만든 **Scenes** 폴더를 열고 *파일 이름*: 텍스트 필드에 **MR_ComputerVisionScene** 입력한 **다음, 저장을** 클릭합니다.

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Unity 장면은 Unity 프로젝트와 연결되어야 하며 *자산* 폴더 내에 저장해야 합니다. Scenes 폴더(및 기타 유사한 폴더)를 만드는 것은 Unity 프로젝트를 구성하는 일반적인 방법입니다.

    7.  *빌드 설정* 나머지 설정은 현재 기본값으로 유지되어야 합니다.

6.  빌드 *설정* 창에서 **플레이어 설정** 단추를 클릭하면 *Inspector가* 있는 공간에서 관련 패널이 열립니다. 

    ![](images/AzureLabs-Lab311-16.png)

7. 이 패널에서 몇 가지 설정을 확인해야 합니다.

    1. 기타 **설정** 탭에서 다음을 수행합니다.

        1.  **런타임 버전** **스크립팅은** **실험적(.NET** 4.6 동등)이어야 하며, 편집기를 다시 시작해야 합니다.

        2. **스크립팅 백 엔드는** **.NET이어야 합니다.**

        3. **API 호환성 수준은** **.NET 4.6이어야** 합니다.

            ![](images/AzureLabs-Lab311-17.png)

    2.  게시 **설정** 탭의 기능 아래에서 **다음을 확인합니다.**

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  패널의 아래쪽에 있는 **XR 설정(게시 설정** 아래에 **있음)에서** Virtual Reality **지원 을** 확인하여 **Windows Mixed Reality SDK가** 추가되었는지 확인합니다.

        ![](images/AzureLabs-Lab311-19.png)

8.  빌드 *설정* Unity *C# 프로젝트는* 더 이상 회색으로 표시됩니다. 이 옆에 있는 확인란을 선택합니다.

9.  *빌드 설정* 창을 닫습니다.

10.  장면 및 **프로젝트(FILE**  >  **SAVE SCENES / FILE SAVE**  >  **PROJECT)를 저장합니다.**

## <a name="chapter-3---import-libraries-in-unity"></a>3장 - Unity에서 라이브러리 가져오기

> [!IMPORTANT]
> 이 과정의 Unity *설정* 구성 요소를 건너뛰고 코드를 계속 진행하려면 이 [Azure-MR-311.unitypackage를](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)자유롭게 다운로드하고, 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 다음, [5장에서](#chapter-5---create-meetingsui-class)계속 진행하세요.

Unity 내에서 *Microsoft Graph* 사용하려면 **Microsoft.Identity.Client** DLL을 사용해야 합니다. Microsoft Graph SDK를 사용할 수 있지만 Unity 프로젝트를 빌드한 후(빌드 후 프로젝트 편집을 의미) NuGet 패키지를 추가해야 합니다. 필요한 DLL을 Unity로 직접 가져오는 것이 더 간단한 것으로 간주됩니다.

> [!NOTE]
> 현재 Unity에는 가져온 후 플러그 인을 다시 구성해야 하는 알려진 문제가 있습니다. 버그가 해결된 후에는 이러한 단계(이 섹션의 4-7)가 더 이상 필요하지 않습니다.

Microsoft *Graph* 사용자 고유의 프로젝트로 가져오려면 [MSGraph_LabPlugins.zip 파일을 다운로드합니다.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage) 이 패키지는 테스트된 라이브러리 버전으로 만들어졌습니다.

Unity 프로젝트에 사용자 지정 DLL을 추가하는 방법에 대해 자세히 알아보려면 [이 링크를 따르세요.](https://docs.unity3d.com/Manual/UsingDLL.html)

패키지를 가져오려면 다음을 수행합니다.

1.  자산 패키지 가져오기 사용자 지정 패키지 메뉴 옵션을 사용하여 Unity 패키지를 Unity에 **추가합니다.**  >    >   방금 다운로드한 패키지를 선택합니다.

2.  팝업되는 **Unity 패키지 가져오기** 상자에서 플러그 **인(및** 포함) 아래의 모든 것이 선택되어 있는지 확인합니다.

    ![](images/AzureLabs-Lab311-20.png)

3.  **가져오기** 단추를 클릭하여 프로젝트에 항목을 추가합니다.

4.  *Project 패널의* 플러그 **인** 아래에 있는 **MSGraph** 폴더로 이동하여 **Microsoft.Identity.Client라는** 플러그 인을 선택합니다.

    ![](images/AzureLabs-Lab311-21.png)

5.  플러그 *인을* 선택한 상태로 **모든 플랫폼이** 선택 취소되어 있는지 확인하고 **WSAPlayer도** 선택 취소되었는지 확인하고 **적용을** 클릭합니다. 이는 파일이 올바르게 구성되었는지 확인하기 위한 것입니다.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > 이러한 플러그 인을 표시하면 Unity 편집기에서만 사용할 수 있도록 구성됩니다. WSA 폴더에는 Unity에서 유니버설 Windows 애플리케이션으로 프로젝트를 내보낸 후 사용되는 다른 DLL 집합이 있습니다.

6.  다음으로 **MSGraph** 폴더 내에서 **WSA** 폴더를 열어야 합니다. 방금 구성한 것과 동일한 파일의 복사본이 표시됩니다. 파일을 선택한 다음, 검사기에서 다음을 수행합니다.

    -   모든 **플랫폼이** **선택 취소되어** 있고 **WSAPlayer만** **선택되어** 있는지 확인합니다. 

    -   **SDK가** **UWP로** 설정되고 **스크립팅 백 엔드가** **Dot Net으로** 설정되어 있는지 확인합니다.

    -   처리 **안 되는지** **확인합니다.**

        ![](images/AzureLabs-Lab311-23.png)

7.  **적용** 을 클릭합니다.

## <a name="chapter-4---camera-setup"></a>4장 - 카메라 설정

이 챕터에서 장면의 주 카메라를 설정합니다.

1.  계층 *구조 패널에서* **주 카메라** 를 선택합니다.

2.  이 옵션을 선택하면 *검사기* 패널에서 **주 카메라의** 모든 구성 요소를 볼 수 있습니다.

    1.  **Camera 개체의** 이름은 Main Camera(맞춤법)로 지정해야 합니다. 

    2.  Main Camera **태그는** **MainCamera(맞춤법** 유의)로 설정해야 합니다.

    3.  **변환 위치가** **0, 0, 0으로** 설정되어 있는지 확인합니다.

    4.  **플래그 지우기를** **단색으로** 설정

    5.  카메라 구성 요소의 **배경색을** **검은색, 알파 0(16진수** **코드: #00000000)으로** 설정합니다.

        ![](images/AzureLabs-Lab311-24.png)

3.  계층 구조 *패널의* 최종 개체 구조는 아래 이미지에 표시된 구조와 같아야 합니다.

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>5장 - MeetingsUI 클래스 만들기

만들어야 하는 첫 번째 스크립트는 **MeetingsUI이며,** 이 스크립트는 애플리케이션의 UI를 호스팅하고 채우는 것을 담당합니다(환영 메시지, 지침 및 모임 세부 정보).

이 클래스를 만들려면 다음을 수행합니다.

1.  Project 패널에서 **Assets 폴더를** *마우스 오른쪽 단추로* 클릭한   >  **다음, 폴더** 만들기를 선택합니다. 폴더 이름을 **Scripts 로 지정합니다.**

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  스크립트 **폴더를** 연 다음, 해당 폴더 내에서 C# 스크립트 **만들기를** 마우스 오른쪽  >  **단추로** 클릭합니다. 스크립트 이름을 **MeetingsUI로 지정합니다.**

    ![](images/AzureLabs-Lab311-28.png)

3.  새 **MeetingsUI** 스크립트를 두 번 클릭하여 *Visual Studio* 으로 엽니다.

4.  다음 네임스페이스를 삽입합니다.

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  클래스 내에 다음 변수를 삽입합니다.

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  그런 다음 **Start()** 메서드를 **바꾸고, Awake()** 메서드를 추가합니다. 클래스가 초기화될 때 호출됩니다.

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  *Meetings UI를* 만드는 메서드를 추가하고 요청 시 현재 모임으로 채웁니다.

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **Update()** 메서드를 **삭제하고** Unity로 돌아가기 전에 변경 내용을 Visual Studio **저장합니다.** 

## <a name="chapter-6---create-the-graph-class"></a>6장 - Graph 클래스 만들기

만들 다음 스크립트는 **Graph** 스크립트입니다. 이 스크립트는 사용자를 인증하고 사용자의 일정에서 현재 날의 예약된 모임을 검색하기 위한 호출을 담당합니다.

이 클래스를 만들려면 다음을 수행합니다.

1.  **스크립트** 폴더를 두 번 클릭하여 엽니다.

2.  Scripts 폴더 **내부를** 마우스 오른쪽 단추로 클릭하고 C# 스크립트 **만들기를**  >  클릭합니다. 스크립트 이름을 **로 Graph.**

3.  스크립트를 두 번 클릭하여 Visual Studio 엽니다.

4.  다음 네임스페이스를 삽입합니다.

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > 이 스크립트의 코드 부분은 [Precompile 지시문](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)을 중심으로 래핑됩니다. 이는 Visual Studio 솔루션을 빌드할 때 라이브러리와 관련된 문제를 방지하기 위한 것입니다.

5.  **Start()** 및 **Update()** 메서드는 사용되지 않기 때문에 삭제합니다.

6.  **Graph** 클래스 외부에서 다음 개체를 삽입합니다. 이 개체는 매일 예약된 모임을 나타내는 JSON 개체를 deserialize하는 데 필요합니다.

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  **Graph** 클래스 내에 다음 변수를 추가합니다.

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > **appId** 값을 **[1장,](#chapter-1---create-your-app-in-the-application-registration-portal)4단계에서** 적어 두는 **앱 ID로** 변경합니다. 이 값은 **애플리케이션 등록 포털의 애플리케이션 등록** 페이지에 표시되는 값과 동일해야 합니다.

8.  **Graph** 클래스 내에서 로그인 자격 증명을 삽입하라는 메시지를 사용자에게 표시할 **SignInAsync()** 및 **AquireTokenAsync()** 메서드를 추가합니다.

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successful, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  다음 두 가지 메서드를 추가합니다.

    1.  **BuildTodayCalendarEndpoint()**- 예약된 모임이 검색되는 일 및 시간 범위를 지정하는 URI를 빌드합니다.

    2.  **ListMeetingsAsync()**- *Microsoft Graph* 예약된 모임을 요청합니다.

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. 이제 **Graph** 스크립트를 완료했습니다. Unity로 돌아가기 전에 변경 내용을 Visual Studio **저장합니다.**

## <a name="chapter-7---create-the-gazeinput-script"></a>7장 - GazeInput 스크립트 만들기

이제 **GazeInput** 를 만듭니다. 이 클래스는 **주 카메라에서** 오는 **Raycast를** 사용하여 앞으로 프로젝션하여 사용자의 응시를 처리하고 추적합니다.

스크립트를 만들려면:

1.  **스크립트** 폴더를 두 번 클릭하여 엽니다.

2.  Scripts 폴더 **내부를** 마우스 오른쪽 단추로 클릭하고 C# 스크립트 **만들기를**  >  클릭합니다. 스크립트 이름을 **GazeInput으로 지정합니다.**

3.  스크립트를 두 번 클릭하여 Visual Studio 엽니다.

4.  Serialized할 수 있도록 **GazeInput** 클래스 위에 **\[ 'System.Serializable \]**' 태그를 추가하여 아래와 일치하도록 네임스페이스 코드를 변경합니다.

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  **GazeInput** 클래스 내에 다음 변수를 추가합니다.

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  **CreateCursor()** 메서드를 추가하여 장면에서 HoloLens 커서를 만들고 **Start()** 메서드에서 메서드를 호출합니다.

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  다음 메서드를 사용하면 Raycast를 응시하고 포커스가 있는 개체를 추적할 수 있습니다.

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
                HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  Unity로 돌아가기 전에 변경 내용을 Visual Studio **저장합니다.**

## <a name="chapter-8---create-the-interactions-class"></a>8장 - 상호 작용 클래스 만들기

이제 다음을 담당하는 **상호 작용 스크립트를** 만들어야 합니다.

-   **사용자가** 장면의 "단추"에서 로그와 상호 작용할 수 있도록 탭 상호 작용 및 **카메라 응시를** 처리합니다.

-   사용자가 상호 작용할 수 있도록 장면에서 "button" 개체에 로그를 만듭니다.

스크립트를 만들려면:

1.  **스크립트** 폴더를 두 번 클릭하여 엽니다.

2.  Scripts 폴더 **내부를** 마우스 오른쪽 단추로 클릭하고 C# 스크립트 **만들기를**  >  클릭합니다. 스크립트 **상호 작용** 의 이름을로 합니다.

3.  스크립트를 두 번 클릭 하 여 Visual Studio를 사용 하 여 엽니다.

4.  다음 네임 스페이스를 삽입 합니다.

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  **상호 작용** 클래스의 상속을 *MonoBehaviour* 에서 **GazeInput** 로 변경 합니다.

    ~~공용 클래스 상호 작용: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  **상호 작용** 클래스 내에서 다음 변수를 삽입 합니다.

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  **Start** 메서드를 대체 합니다. ' base ' 응시 클래스 메서드를 호출 하는 재정의 메서드입니다. **Start ()** 는 클래스가 초기화 되 고, 입력 인식을 등록 하 고, 장면에 로그인 *단추* 를 만들 때 호출 됩니다.

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  **CreateSignInButton ()** 메서드를 추가 합니다 .이 메서드는 장면의 로그인 *단추* 를 인스턴스화하고 해당 속성을 설정 합니다.

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  *탭* 사용자 이벤트에 대해 응답 하는 **GestureRecognizer_Tapped ()** 메서드를 추가 합니다.

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **Update ()** 메서드를 **삭제** 한 다음 Unity로 반환 하기 전에 Visual Studio에 **변경 내용을 저장** 합니다.

## <a name="chapter-9---set-up-the-script-references"></a>9 장-스크립트 참조 설정

이 장에서는 **기본 카메라** 에 **상호 작용** 스크립트를 저장 해야 합니다. 그런 다음이 스크립트는 필요한 위치에 다른 스크립트를 배치 하는 것을 처리 합니다.

-  아래 그림과 같이 *Project 패널* 의 **Scripts** 폴더에서 스크립트 **상호 작용** 을 **주 카메라** 개체로 끌어 옵니다.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>10 장-태그 설정

응시를 처리 하는 코드는 **SignInButton** 태그를 사용 하 여 사용자가 *Microsoft Graph* 에 로그인 하기 위해 상호 작용 하는 개체를 식별 합니다.

태그를 만들려면 다음을 수행 합니다.

1.  Unity 편집기의 *계층 패널* 에서 **주 카메라** 를 클릭 합니다.

2.  *Inspector 패널* 에서 **maincamera** *태그* 를 클릭 하 여 드롭다운 목록을 엽니다. **태그 추가** ...를 클릭 합니다.

    ![](images/AzureLabs-Lab311-30.png)

3.  단추를 클릭 **+** 합니다.

    ![](images/AzureLabs-Lab311-31.png)

4.  태그 이름을 **SignInButton** 로 작성 하 고 저장을 클릭 합니다.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>11 장-UWP에 Unity 프로젝트 빌드

이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었으므로 Unity에서 빌드할 수 있습니다.

1.  *빌드 설정* (**파일* > * 빌드 설정 * *)로 이동 합니다.

    ![](images/AzureLabs-Lab311-33.png)

2.  아직 없는 경우 tick **Unity C \# 프로젝트** 입니다.

3.  **빌드** 를 클릭한 다음 Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 **파일 탐색기** 창을 시작 합니다. 이제 해당 폴더를 만들고 이름을 **App** 으로 만듭니다. 그런 다음 **앱** 폴더를 선택 하 고 **폴더 선택** 을 클릭 합니다.

4.  Unity는 **응용** 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다.

5.  Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)

## <a name="chapter-12---deploy-to-hololens"></a>12 장-HoloLens에 배포

HoloLens에 배포 하려면:

1.  HoloLens의 IP 주소가 필요 하며 (원격 배포의 경우) HoloLens **개발자 모드** 에 있는지 확인 해야 합니다. 이렇게 하려면 다음을 수행합니다.

    1.  HoloLens를 입고 **설정** 를 엽니다.

    2.  **네트워크 & 인터넷**  >  **wi-fi**  >  **고급 옵션** 으로 이동 합니다.

    3.  **IPv4** 주소를 적어둡니다.

    4.  그런 다음 **설정** 으로 다시 이동한 다음 개발자를 위한 **& 보안을 업데이트** 합니다.  >  

    5.  **에서 개발자 모드를** 설정 합니다.

2.  새 Unity 빌드 ( **앱** 폴더)로 이동 하 고 **Visual Studio** 를 사용 하 여 솔루션 파일을 엽니다.

3.  **솔루션 구성** 에서 **디버그** 를 선택 합니다.

4.  **솔루션 플랫폼** 에서 **X86, 원격 컴퓨터** 를 선택 합니다. 원격 장치의 **IP 주소** (이 경우에는 HoloLens)를 삽입 하 라는 메시지가 표시 됩니다.

    ![](images/AzureLabs-Lab311-34.png)

5.  **빌드** 메뉴로 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 HoloLens 테스트용으로 로드.

6.  이제 앱이 HoloLens에 설치 된 앱 목록에 표시 되 고, 시작할 준비가 되었습니다!

## <a name="your-microsoft-graph-hololens-application"></a>Microsoft Graph HoloLens 응용 프로그램

축 하 합니다. Microsoft Graph를 활용 하 여 사용자 달력 데이터를 읽고 표시 하는 혼합 현실 앱을 빌드 했습니다.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

Microsoft Graph를 사용 하 여 사용자에 대 한 기타 정보 표시

-   사용자 전자 메일/전화 번호/프로필 사진

### <a name="exercise-1"></a>연습 1

음성 컨트롤을 구현 하 여 Microsoft Graph UI를 탐색 합니다.