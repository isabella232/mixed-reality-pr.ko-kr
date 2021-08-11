---
title: HoloLens(1세대) 및 Azure 309 - 애플리케이션 인사이트
description: 이 과정을 완료하여 Azure 애플리케이션 Insights 서비스를 사용하여 혼합 현실 애플리케이션 내에서 사용자 동작에 대한 분석을 수집하는 방법을 알아봅니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, application insights, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 549afbd1e5a3f42bb0540714500d31edf022d36511961e887ac9e927b9af1ea3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222334"
---
# <a name="hololens-1st-gen-and-azure-309-application-insights"></a>HoloLens(1세대) 및 Azure 309: Application Insights

<br>

>[!NOTE]
>Mixed Reality 아카데미 자습서는 HoloLens(1세대) 및 Mixed Reality 몰입형 헤드셋을 염두에 두고 설계되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다.  이러한 자습서는 HoloLens 2에 사용되는 최신 도구 집합 또는 상호 작용으로 업데이트되지 **_않습니다_**.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2 위해 개발하는 방법을 보여 주는 새로운 자습서 시리즈가 나중에 게시될 예정입니다.  이 알림은 해당 자습서가 게시될 때 해당 자습서에 대한 링크로 업데이트됩니다.

<br>

![final product -start](images/AzureLabs-Lab309-00.png)

이 과정에서는 Azure 애플리케이션 Insights API를 사용하여 사용자 동작에 대한 분석을 수집하는 혼합 현실 애플리케이션에 애플리케이션 Insights 기능을 추가하는 방법을 알아봅니다.

애플리케이션 Insights 개발자가 애플리케이션에서 분석을 수집하고 사용하기 쉬운 포털에서 관리할 수 있는 Microsoft 서비스입니다. 분석은 성능에서 수집하려는 사용자 지정 정보에 이르기까지 모든 것일 수 있습니다. 자세한 내용은 애플리케이션 [Insights 페이지를 방문하세요.](https://azure.microsoft.com/services/application-insights/)

이 과정을 완료하면 다음을 수행할 수 있는 혼합 현실 몰입형 헤드셋 애플리케이션이 있습니다.

1.  사용자가 장면을 응시하고 이동할 수 있습니다.
2.  장면 내 개체에 대한 응시 및 근접을 사용하여 *Application Insights Service로* 분석 전송을 트리거합니다.
3.  또한 앱은 서비스를 호출하여 지난 24시간 이내에 사용자가 가장 접근한 개체에 대한 정보를 가져옵니다. 해당 개체의 색이 녹색으로 변경됩니다.

이 과정에서는 Application Insights Service에서 Unity 기반 샘플 애플리케이션으로 결과를 얻는 방법을 배분합니다. 빌드할 수 있는 사용자 지정 애플리케이션에 이러한 개념을 적용하는 것은 사용자 에게 달려 있습니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 309: Application Insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정에서는 주로 몰입형(VR) 헤드셋을 Windows Mixed Reality 중점적으로 진행하지만 이 과정에서 학습한 내용을 Microsoft HoloLens 적용할 수도 있습니다. 과정을 진행하면서 HoloLens 지원하기 위해 사용해야 할 수 있는 변경 내용에 대한 메모를 볼 수 있습니다. HoloLens 사용하는 경우 음성 캡처 중에 일부 에코를 확인할 수 있습니다.

## <a name="prerequisites"></a>필수 조건

> [!NOTE]
> 이 자습서는 Unity 및 C#에 대한 기본적인 경험이 있는 개발자를 위해 설계되었습니다. 또한 이 문서 내의 필수 조건 및 작성된 지침은 작성 당시 테스트 및 확인된 내용을 나타냅니다(2018년 7월). [도구 설치](../../install-the-tools.md) 문서에 나열된 대로 최신 소프트웨어를 자유롭게 사용할 수 있지만, 이 과정의 정보가 아래 나열된 내용보다 최신 소프트웨어에서 찾을 수 있는 정보와 완벽하게 일치한다고 가정해서는 안 됩니다.

이 과정에서는 다음 하드웨어 및 소프트웨어를 사용하는 것이 좋습니다.

- 몰입형(VR) 헤드셋 개발을 위해 [Windows Mixed Reality 호환되는](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 개발 PC
- [개발자 모드를 사용하도록 설정된 Windows 10 Fall Creators Update(이상)](../../install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- 개발자 모드를 사용하도록 설정된 [Windows Mixed Reality 몰입형(VR) 헤드셋](../../../discover/immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](/hololens/hololens1-hardware)
- 기본 제공 마이크가 있는 마이크 세트(헤드셋에 기본 제공 마이크 및 스피커가 없는 경우)
- Azure 설정 및 애플리케이션 Insights 데이터 검색을 위한 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전에

이 프로젝트를 빌드하는 데 문제가 발생하지 않도록 하려면 이 자습서에서 언급한 프로젝트를 루트 또는 루트에 가까운 폴더에 만드는 것이 좋습니다(긴 폴더 경로로 인해 빌드 시 문제가 발생할 수 있습니다).

> [!WARNING] 
> *애플리케이션 Insights* 데이터가 전송되는 데는 시간이 걸리므로 기다려 십시오. 서비스에서 데이터를 받았는지 확인하려면 포털을 탐색하는 방법을 보여 줄 [14장 을](#chapter-14---the-application-insights-service-portal)확인하세요.

## <a name="chapter-1---the-azure-portal"></a>1장 - Azure Portal

애플리케이션 *Insights* 사용하려면 Azure Portal *Application Insights Service를* 만들고 구성해야 합니다.

1.  [Azure Portal](https://portal.azure.com)에 로그인합니다.

    > [!NOTE]
    > Azure 계정이 아직 없는 경우 만들어야 합니다. 클래스룸 또는 랩 상황에서 이 자습서를 따르는 경우 강사 또는 프록터 중 하나에 새 계정 설정에 대한 도움을 요청하세요.

2.  로그인한 후 왼쪽 위 모서리에서 **새로** 만들기를 클릭하고 *애플리케이션 Insights* 검색한 다음 **Enter 키를** 클릭합니다.

    > [!NOTE]
    > **New라는** 단어는 최신 포털에서 **리소스 만들기** 로 대체되었을 수 있습니다.

    ![Azure Portal](images/AzureLabs-Lab309-01.png)

3.  오른쪽의 새 페이지에서는 *Azure 애플리케이션 Insights* 서비스에 대한 설명을 제공합니다. 이 페이지의 왼쪽 아래에서 **만들기** 단추를 선택하여 이 서비스와의 연결을 만듭니다.

    ![Azure Portal](images/AzureLabs-Lab309-02.png)

4.  **만들기를** 클릭한 후:

    1.  이 서비스 인스턴스에 대해 원하는 **이름을** 삽입합니다.

    2.  **애플리케이션 유형으로** **일반** 을 선택합니다.

    3.  적절한 **구독** 을 선택합니다.

    4.  리소스 **그룹을** 선택하거나 새 리소스 그룹을 만듭니다. 리소스 그룹은 Azure 자산 컬렉션에 대한 액세스를 모니터링, 제어, 프로비전 및 관리하는 방법을 제공합니다. 모든 Azure 서비스를 단일 프로젝트(예: 이러한 과정)와 연결된 공용 리소스 그룹에 유지하는 것이 좋습니다.

        > Azure 리소스 그룹에 대해 자세히 알아보려면 [리소스 그룹 문서 를 방문하세요.](/azure/azure-resource-manager/resource-group-portal)

    5.  **위치** 를 선택합니다.

    6.  또한 이 서비스에 적용된 약관을 이해했다는 것을 확인해야 합니다.

    7.  **만들기** 를 선택합니다.

        ![Azure Portal](images/AzureLabs-Lab309-03.png)

5.  **만들기를** 클릭하면 서비스가 생성될 때까지 기다려야 합니다. 이 경우 1분 정도 걸릴 수 있습니다.

6.  서비스 인스턴스가 만들어지면 포털에 알림이 표시됩니다.

    ![Azure Portal](images/AzureLabs-Lab309-04.png)

7.  알림을 클릭하여 새 서비스 인스턴스를 탐색합니다.

    ![Azure Portal](images/AzureLabs-Lab309-05.png)

8.  알림에서 **리소스로 이동** 단추를 클릭하여 새 서비스 인스턴스를 탐색합니다. 새 *Application Insights Service* 인스턴스로 이동됩니다.

    ![Azure Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  이 웹 페이지를 열어 두면 쉽게 액세스할 수 있습니다. 수집된 데이터를 보기 위해 여기로 자주 돌아올 것입니다.

    > [!IMPORTANT]
    > 애플리케이션 Insights 구현하려면 **계측 키,** **애플리케이션 ID** 및 **API** 키의 세 가지 특정 값을 사용해야 합니다. 아래에서 서비스에서 이러한 값을 검색하는 방법을 확인할 수 있습니다. 이러한 값은 코드에서 곧 사용하므로 빈 *메모장* 페이지에서 유의해야 합니다.

9.  **계측 키** 를 찾으려면 서비스 함수 목록을 아래로 스크롤하고 **속성을** 클릭하면 표시되는 탭에 서비스 **키** 가 표시됩니다.

    ![Azure Portal](images/AzureLabs-Lab309-07.png)

10. **속성** 아래에서 클릭해야 하는 **API 액세스** 를 찾을 수 있습니다. 오른쪽 패널은 앱의 **애플리케이션 ID를** 제공합니다.

    ![Azure Portal](images/AzureLabs-Lab309-08.png)

11. 애플리케이션 **ID** 패널이 열려 있는 상태에서 **API 키 만들기를** 클릭하면 *API 키 만들기* 패널이 열립니다.

    ![Azure Portal](images/AzureLabs-Lab309-09.png)

12. 이제 *API 키 만들기* 패널에서 설명을 입력하고 **세 개의 상자를 선택합니다.**

13. **키 생성을** 클릭합니다. **API 키가** 만들어지고 표시됩니다. 

    ![Azure Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > **서비스 키가** 표시되는 유일한 시간이므로 지금 복사본을 만들어야 합니다.

## <a name="chapter-2---set-up-the-unity-project"></a>2장 - Unity 프로젝트 설정

다음은 혼합 현실로 개발하기 위한 일반적인 설정이며, 따라서 다른 프로젝트에 적합한 템플릿입니다.

1.  *Unity를* 열고 **새로** 만들기를 클릭합니다.

    ![Unity Project 설정](images/AzureLabs-Lab309-11.png)

2.  이제 Unity Project 이름을 제공하고 **MR Azure Application \_ \_ \_ Insights** 삽입해야 합니다. *템플릿이* **3D 로** 설정되어 있는지 확인합니다. *위치를* 적절한 위치로 설정합니다(루트 디렉터리에 가까울수록 좋습니다). 그런 다음 **프로젝트 만들기를** 클릭합니다.

    ![Unity Project 설정](images/AzureLabs-Lab309-12.png)

3.  Unity가 열려 있는 경우 기본 **스크립트 편집기가** **Visual Studio** 로 설정되어 있는지 확인하는 것이 좋습니다. 기본 **\> 설정 편집으로** 이동한 다음 새 창에서 **외부 도구** 로 이동합니다. **외부 스크립트 편집기를** **Visual Studio 2017로** 변경합니다. 기본 **설정** 창을 닫습니다.

    ![Unity Project 설정](images/AzureLabs-Lab309-13.png)

4.  다음으로, **파일 \> 빌드 설정** 이동하여 플랫폼 전환 단추를 클릭하여 플랫폼을 유니버설 Windows **플랫폼으로** **전환합니다.**

    ![Unity Project 설정](images/AzureLabs-Lab309-14.png)

5.  파일 **\> 빌드 설정** 이동하여 다음을 확인합니다.

    1.  **대상 디바이스가** **모든 디바이스로** 설정됩니다.

        > Microsoft HoloLens **대상 디바이스를** *HoloLens* 설정합니다.

    2.  **빌드 유형이** **D3D로** 설정됩니다.

    3.  **SDK가** **최신 설치로 설정됩니다.**

    4.  **빌드 및 실행이** **로컬 컴퓨터로 설정됩니다.**

    5.  장면을 저장하고 빌드에 추가합니다.

        1.  열린 장면 추가 를 선택하여 이 작업을 **수행합니다.** 저장 창이 나타납니다.

            ![Unity Project 설정](images/AzureLabs-Lab309-15.png)

        2. 이에 대한 새 폴더 및 이후 장면을 만든 다음 새 폴더 단추를 클릭하여 새 **폴더를** 만들고 이름을 **Scenes로 지정합니다.**

            ![Unity Project 설정](images/AzureLabs-Lab309-16.png)

        3. 새로 만든 **Scenes** 폴더를 열고 *파일 이름:* 텍스트 필드에 **ApplicationInsightsScene을** 입력한 **다음, 저장을** 클릭합니다.

            ![Unity Project 설정](images/AzureLabs-Lab309-17.png)

6.  **빌드 설정** 의 나머지 설정은 현재 기본값으로 유지되어야 합니다.

7.  빌드 **설정** 창에서 **플레이어 설정** 단추를 클릭하면 **Inspector가** 있는 공간에서 관련 패널이 열립니다.

    ![Unity Project 설정](images/AzureLabs-Lab309-18.png)

8. 이 패널에서 몇 가지 설정을 확인해야 합니다.

    1.  기타 **설정** 탭에서 다음을 수행합니다.

        1.  **런타임 버전** **스크립팅은** **실험적(.NET 4.6 동등)이어야 합니다.** 그러면 편집기를 다시 시작해야 합니다.

        2.  **스크립팅 백 엔드는** **.NET이어야 합니다.**

        3.  **API 호환성 수준은** **.NET 4.6이어야** 합니다.

        ![Unity Project 설정](images/AzureLabs-Lab309-19.png)

    2.  게시 **설정** 탭의 기능 아래에서 **다음을 확인합니다.**

        - **InternetClient**     

            ![Unity Project 설정](images/AzureLabs-Lab309-20.png)

    3.  패널의 아래쪽에 있는 **XR 설정(게시 설정** 아래에 **있음)에서** 가상 **현실 지원됨을** **틱하여 Windows Mixed Reality SDK가** 추가되었는지 확인합니다.

        ![Unity Project 설정](images/AzureLabs-Lab309-21.png)

9.  빌드 **설정** Unity **C# 프로젝트는** 더 이상 회색으로 표시됩니다. 이 옆에 있는 확인란을 선택합니다.

10.  빌드 설정 창을 닫습니다.

11.  장면을 저장하고 Project(파일  >  **저장 장면/파일**  >  **저장 프로젝트).**


## <a name="chapter-3---import-the-unity-package"></a>3장 - Unity 패키지 가져오기

> [!IMPORTANT]
> 이 과정의 Unity *구성* 요소 설정을 건너뛰고 코드를 계속 진행하려면 이 [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)를 자유롭게 다운로드하고 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져옵니다. 여기에는 다음 챕터의 DLL도 포함됩니다. 가져온 후 [**6장 에서 계속합니다.**](#chapter-6---create-the-applicationinsightstracker-class)

> [!IMPORTANT]
> Unity 내에서 애플리케이션 Insights 사용하려면 Newtonsoft DLL과 함께 DLL을 가져와야 합니다. 현재 Unity에는 가져온 후 플러그 인을 다시 구성해야 하는 알려진 문제가 있습니다. 버그가 해결된 후에는 이러한 단계(이 섹션의 4-7)가 더 이상 필요하지 않습니다.

애플리케이션 Insights 고유한 프로젝트로 가져오려면 [플러그 인이 포함된 '.unitypackage'를 다운로드했는지](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)확인합니다. 그런 후 다음을 수행합니다.

1.  자산 패키지 가져오기 사용자 지정 패키지 메뉴 옵션을 사용하여 **Unity에 .unitypackage를** **\> \> 추가합니다.**

2.  팝업되는 **Unity 패키지 가져오기** 상자에서 플러그 **인(및** 포함) 아래의 모든 것이 선택되어 있는지 확인합니다.

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-22.png)

3.  **가져오기** 단추를 클릭하여 프로젝트에 항목을 추가합니다.

4.  **Project** 보기에서 **플러그 인** 아래의 Insights 폴더로 이동하여 다음 플러그 *인만* 선택합니다.

    -   Microsoft.ApplicationInsights

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-23.png)

5.  이 *플러그 인을* 선택한 상태로 **모든 플랫폼의** **선택을 취소했는지** 확인하고 **WSAPlayer도** **선택 취소되었는지** 확인하고 **적용을** 클릭합니다. 이 작업을 수행하면 파일이 올바르게 구성되었는지 확인할 수 있습니다.

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > 플러그 인을 다음과 같이 표시하면 Unity 편집기에서만 사용할 수 있도록 구성됩니다. WSA 폴더에는 Unity에서 프로젝트를 내보낸 후 사용되는 다른 DLL 집합이 있습니다.

6.  다음으로, **Insights** 폴더 내에서 **WSA** 폴더를 열어야 합니다. 방금 구성한 것과 동일한 파일의 복사본이 표시됩니다. 이 파일을 선택한 다음, 검사기에서 **모든 플랫폼의** **선택을 취소했는지** 확인한 **다음, WSAPlayer만** **선택되어** 있는지 확인합니다.  **적용** 을 클릭합니다.

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-25.png)

7. 이제 *Newtonsoft* 플러그 인의 경우 **4-6단계를** 수행해야 합니다. 결과가 어떻게 표시되는지 아래 스크린샷을 참조하세요.

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>4장 - 카메라 및 사용자 컨트롤 설정

이 챕터에서는 사용자가 장면을 보고 이동할 수 있도록 카메라와 컨트롤을 설정합니다.

1.  계층 패널에서 빈 영역을 마우스 오른쪽 단추로 클릭한 다음 빈 **만들기** 를  >  클릭합니다.

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-26.png)

2.  비어 있는 새 GameObject의 이름을 **카메라 부모** 로 바꿉니다.

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-27.png)

3.  계층 구조 패널에서 빈 영역을 마우스 오른쪽 단추로 클릭한 **다음, 3D 개체** 를 클릭한 **다음, 구 를** 클릭합니다.

4.  구의 이름을 오른쪽 으로 **바꿉니다.**

5.  오른쪽의 **변환 배율** **을 0.1, 0.1, 0.1로** 설정합니다.

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-28.png)

6.  구 **충돌체** 구성 요소에서 **기어를** 클릭하여 오른쪽에서 *구 충돌체* 구성 요소를 제거한 다음 구성 **요소 를 제거합니다.**

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-29.png)

7.  계층 구조 패널에서 주 **카메라** 및 **오른쪽** 개체를 **카메라 부모** 개체로 끌어 갑니다.

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-30.png)

8.  **주 카메라와** **오른쪽** 개체의 **변환 위치를** **0, 0, 0으로** 설정합니다.

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-31.png)

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>5장 - Unity 장면에서 개체 설정

이제 사용자가 상호 작용할 수 있는 장면에 대한 몇 가지 기본 셰이프를 만듭니다.

1.  계층 구조 패널 에서 빈 영역을 마우스 *오른쪽* 단추로 클릭한 **다음, 3D 개체** 에서 **평면** 을 선택합니다.

2.  평면 **변환 위치를** **0, -1, 0으로** 설정합니다.

3.  평면 **변환 배율** **을 5, 1, 5로** 설정합니다.

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-33.png)

4.  다른 도형을 더 쉽게 볼 수 있도록 **Plane** 개체와 함께 사용할 기본 재질을 만듭니다. *Project 패널로* 이동한 다음, 마우스 오른쪽 단추로 클릭한 **다음, 만들기를** 클릭하고 **폴더** 를 클릭하여 새 폴더를 만듭니다. 이름을 Materials 로 **지정합니다.**

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-34.png) ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-35.png)

5.  **Material** 폴더를 연 다음 마우스 오른쪽 단추를 클릭하고 **만들기,** **재질** 을 차례로 클릭하여 새 재질을 만듭니다. 이름을 **파란색으로** 지정합니다.

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-36.png) ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-37.png)

6.  새 **파란색** 재질을 선택한 후 *검사기* 를 살펴보고 **Albedo** 와 함께 사각형 창을 클릭합니다. 파란색을 선택합니다(아래 그림은 **16진수 색: \# 3592FFFF).** 선택한 후 닫기 단추를 클릭합니다.

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-38.png)

7.  재질 폴더의 새 **재질을** 장면 내에서 새로 만든 **평면** 로 끌어다 놓거나 *계층 구조* 내의 **Plane** 개체에 놓습니다.

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-39.png)

8.  계층 구조 패널 에서 빈 영역을 마우스 오른쪽 단추로 클릭한 다음 **3D 개체, 캡슐** 를 마우스 *오른쪽* 단추로 클릭합니다.

    -  **캡슐을** 선택한 후 **변환** *위치를* **-10, 1, 0으로** 변경합니다.

9.  계층 패널 에서 빈 영역을 마우스 *오른쪽* 단추로 클릭한 **다음, 3D 개체, 큐브 를** 차례로 클릭합니다.

    -  **큐브를** 선택한 후 **변환** *위치를* **0, 0, 10으로** 변경합니다.

10. 계층 구조 패널 에서 빈 영역을 마우스 *오른쪽* 단추로 클릭한 다음 **3D 개체, 구 를** 차례로 클릭합니다.

    -  **구를** 선택한 후 변환  *위치를* **10, 0, 0으로** 변경합니다.

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > 이러한 *위치* 값은 *제안 사항입니다.* 개체의 위치를 원하는 대로 자유롭게 설정할 수 있지만, 개체 거리가 카메라에서 너무 멀리 떨어져 있지 않으면 애플리케이션 사용자가 더 쉽게 설정할 수 있습니다.

11. 애플리케이션이 실행 중이면 장면 내의 개체를 식별할 수 있어야 합니다. 이를 위해서는 태그를 지정해야 합니다. 개체 중 하나를 선택하고 *검사기* 패널에서 **태그 추가...** 를 클릭합니다. 이 경우 *검사기를* 태그 & 계층 패널로 바꿉니다. 

    ![Unity 장면에서 ](images/AzureLabs-Lab309-41.png) 개체 설정 ![](images/AzureLabs-Lab309-42.png)

12. + **(더하기)** 기호를 클릭한 다음 태그 이름을 **ObjectInScene** 로 입력합니다.

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > 태그에 다른 이름을 사용하는 경우 이 변경이 *DataFromAnalytics*, *ObjectTrigger* 및 *Gaze*, 스크립트를 나중에 만들어 장면 내에서 개체를 찾아서 감지하도록 해야 합니다.

13. 태그를 만들었으므로 이제 세 개체 모두에 적용해야 합니다. *Hierarchy* 에서 Shift 키를 **누른** 채 **캡슐,** **큐브** 및 **구**, 개체를 클릭한 다음, *검사기* 에서 **태그** 와 함께 드롭다운 메뉴를 클릭한 다음, 만든 *ObjectInScene* 태그를 클릭합니다.

    ![Unity 장면에서 ](images/AzureLabs-Lab309-44.png) 개체 설정 ![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>6장 - ApplicationInsightsTracker 클래스 만들기

만들어야 하는 첫 번째 스크립트는 다음을 담당하는 **ApplicationInsightsTracker입니다.**

1.  Azure 애플리케이션 Insights 제출할 사용자 상호 작용을 기반으로 이벤트를 만듭니다.

2. 사용자 상호 작용에 따라 적절한 이벤트 이름 만들기

3. Application Insights Service 인스턴스에 이벤트 제출

이 클래스를 만들려면 다음을 수행합니다.

1.  *Project 패널을 마우스 오른쪽 단추로* 클릭한 다음 폴더 **만들기를**  >  클릭합니다. 폴더 이름을 **Scripts 로 지정합니다.**

    ![ApplicationInsightsTracker 클래스 만들기](images/AzureLabs-Lab309-46.png)  ![ApplicationInsightsTracker 클래스 만들기](images/AzureLabs-Lab309-47.png)

2.  스크립트 **폴더를** 만든 후 두 번 클릭하여 엽니다. 그런 다음 해당 폴더 내에서 C# 스크립트 **만들기를** 마우스 오른쪽  >  **단추로** 클릭합니다. 스크립트 이름을 **ApplicationInsightsTracker로 지정합니다.**

3.  새 **ApplicationInsightsTracker** 스크립트를 두 번 클릭하여 **Visual Studio** 으로 엽니다.

4.  스크립트 맨 위에 있는 네임스페이스를 아래와 같이 업데이트합니다.

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  클래스 내에 다음 변수를 삽입합니다.

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > [1장,](#chapter-1---the-azure-portal)9단계부터 설명한 대로 Azure Portal의 *서비스 키를* 사용하여 **instrumentationKey, applicationId 및 API_Key** 값을 적절하게 설정합니다.

6.  그런 다음 클래스가 초기화될 때 호출되는 **Start()** 및 **Awake()** 메서드를 추가합니다.

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  애플리케이션에서 등록한 이벤트 및 메트릭을 전송하는 메서드를 추가합니다.

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  *Unity* 로 돌아가기 전에 변경 내용을 *Visual Studio* 저장해야 합니다.

## <a name="chapter-7---create-the-gaze-script"></a>7장 - 응시 스크립트 만들기

만들 다음 스크립트는 **응시** 스크립트입니다. 이 스크립트는 사용자가 보고 있는 개체를 감지하기 위해 *주 카메라* 에서 앞으로 프로젝팅되는 *Raycast를* 만드는 작업을 담당합니다. 이 경우 *Raycast는* 사용자가 **ObjectInScene** 태그가 있는 개체를 보고 있는지 확인한 다음, 사용자가 해당 개체를 *응시하는* 시간 수를 계산해야 합니다.

1.  **스크립트** 폴더를 두 번 클릭하여 엽니다.

2.  Scripts 폴더 **내부를** 마우스 오른쪽 단추로 클릭하고 C# 스크립트 **만들기를**  >  클릭합니다. 스크립트 이름을 **Gaze로** 지정합니다.

3.  스크립트를 두 번 클릭하여 Visual Studio 엽니다.

4.  기존 코드를 다음으로 바꿉니다.

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  **이제 Awake()** 및 **Start() 메서드에** 대한 코드를 추가해야 합니다.

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  **Gaze** 클래스 내에서 **Update()** 메서드에 다음 코드를 추가하여 *Raycast를* 프로젝팅하고 대상 적중을 검색합니다.

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  **ResetFocusedObject()** 메서드를 추가하여 사용자가 개체를 볼 때 **Application Insights** 데이터를 보냅니다.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  이제 **응시** 스크립트를 완료했습니다. *Unity* 로 돌아가기 전에 변경 내용을 *Visual Studio* 저장합니다.

## <a name="chapter-8---create-the-objecttrigger-class"></a>8장 - ObjectTrigger 클래스 만들기

만들어야 하는 다음 스크립트는 **ObjectTrigger입니다.** 이 스크립트는 다음을 담당합니다.

- 충돌에 필요한 구성 요소를 주 카메라에 추가합니다.
- 카메라가 **ObjectInScene** 로 태그가 지정된 개체 근처에 있는지 감지합니다.

스크립트를 만들려면:

1.  **스크립트** 폴더를 두 번 클릭하여 엽니다.

2.  Scripts 폴더 **내부를** 마우스 오른쪽 단추로 클릭하고 C# 스크립트 **만들기를**  >  클릭합니다. 스크립트 이름을 **ObjectTrigger로 지정합니다.**

3.  스크립트를 두 번 클릭하여 Visual Studio 엽니다. 기존 코드를 다음으로 바꿉니다.

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  *Unity* 로 돌아가기 전에 변경 내용을 *Visual Studio* 저장해야 합니다.

## <a name="chapter-9---create-the-datafromanalytics-class"></a>9장 - DataFromAnalytics 클래스 만들기

이제 다음을 담당하는 **DataFromAnalytics** 스크립트를 만들어야 합니다.

- 카메라가 가장 접근한 개체에 대한 분석 데이터를 가져옵니다.
- Azure 애플리케이션 Insights *Service* 인스턴스와의 통신을 허용하는 서비스 키 를 사용하는 경우
- 이벤트 수가 가장 많은 에 따라 장면에서 개체를 정렬합니다.
- 가장 많이 접근한 개체의 재질 색을 *녹색으로* 변경합니다.

스크립트를 만들려면:

1.  **스크립트** 폴더를 두 번 클릭하여 엽니다.

2.  Scripts 폴더 **내부를** 마우스 오른쪽 단추로 클릭하고 C# 스크립트 **만들기를**  >  클릭합니다. 스크립트 이름을 **DataFromAnalytics로 지정합니다.**

3.  스크립트를 두 번 클릭하여 Visual Studio 엽니다.

4.  다음 네임스페이스를 삽입합니다.

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  스크립트 내에 다음을 삽입합니다.

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  **DataFromAnalytics** 클래스 내에서 **Start()** 메서드 바로 다음에 **FetchAnalytics()** 라는 메서드를 추가합니다. 이 메서드는 키 값 쌍 목록을 *GameObject* 및 자리 표시자 이벤트 수 번호로 채우는 작업을 담당합니다. 그런 다음 **GetWebRequest()** 코루틴을 초기화합니다. *Application Insights* 대한 호출의 쿼리 구조는 이 메서드 내에서 쿼리 *URL* 엔드포인트로도 찾을 수 있습니다.

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  **FetchAnalytics()** 메서드 바로 아래에 *IEnumerator* 를 반환하는 **GetWebRequest()** 라는 메서드를 추가합니다. 이 메서드는 특정 *GameObject* 에 해당하는 이벤트가 *Application Insights* 내에서 호출된 횟수를 요청합니다. 전송된 모든 쿼리가 반환되면 **DetermineWinner()** 메서드가 호출됩니다.

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readability).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  다음 메서드는 가장 높은 이벤트 수에 따라 *GameObject* 및 *Int* 쌍 목록을 정렬하는 **DetermineWinner()** 입니다. 그런 *다음, GameObject의* 재질 색을 *녹색으로* 변경합니다(개수가 가장 높은 피드백). 그러면 분석 결과가 있는 메시지가 표시됩니다.

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  *Application Insights* 받은 JSON 개체를 deserialize하는 데 사용할 클래스 구조체를 추가합니다. 이러한 클래스를 **DataFromAnalytics** 클래스 파일의 맨 아래에 클래스 정의 **외부에** 추가합니다.

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. *Unity* 로 돌아가기 전에 변경 내용을 *Visual Studio* 저장해야 합니다.

## <a name="chapter-10---create-the-movement-class"></a>10장 - Movement 클래스 만들기

**이동** 스크립트는 만들어야 하는 다음 스크립트입니다. IISConfigurator는 다음을 담당합니다.

- 카메라가 보고 있는 방향에 따라 주 카메라를 이동합니다.
- 장면 개체에 다른 모든 스크립트 추가

스크립트를 만들려면:

1.  **스크립트** 폴더를 두 번 클릭하여 엽니다.

2.  Scripts 폴더 **내부를** 마우스 오른쪽 단추로 클릭하고 C# 스크립트 **만들기를**  >  클릭합니다. 스크립트 이름을 **Movement** 로 지정합니다.

3.  스크립트를 두 번 클릭하여 *Visual Studio* 으로 엽니다.

4.  기존 코드를 다음으로 바꿉니다.

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  **Movement** 클래스 내의 빈 **Update()** 메서드 *아래에* 사용자가 손 컨트롤러를 사용하여 가상 공간에서 이동할 수 있는 다음 메서드를 삽입합니다.

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  마지막으로 **Update()** 메서드 내에 메서드 호출을 추가합니다.

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  *Unity* 로 돌아가기 전에 변경 내용을 *Visual Studio* 저장해야 합니다.

## <a name="chapter-11---setting-up-the-scripts-references"></a>11장 - 스크립트 참조 설정

이 챕터에서는 **이동** 스크립트를 **카메라 부모에** 배치하고 해당 참조 대상을 설정해야 합니다. 그런 다음, 해당 스크립트는 필요한 위치에 다른 스크립트를 배치하는 것을 처리합니다.

1.  *Project 패널의* 스크립트 폴더에서 **이동** 스크립트를 계층 *구조 패널* 에 있는 카메라 **부모** 개체로 끌어 **끕니다.**

    ![Unity 장면에서 스크립트 참조 설정](images/AzureLabs-Lab309-48.png)

2.  **카메라 부모** 를 클릭합니다. *계층* 패널 에서 오른쪽 **개체를** *[계층 구조] 패널의 [검사기] 패널에서* 참조 대상인 **컨트롤러** 로 끌어 들이고, 아래 이미지와 같이 **사용자 속도를** **5로** 설정합니다.

    ![Unity 장면에서 스크립트 참조 설정](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>12장 - Unity 프로젝트 빌드

이제 이 프로젝트의 Unity 섹션에 필요한 모든 것이 완료되었으므로 Unity에서 빌드할 차례입니다.

1.  빌드 **설정**, (**파일**  >  **빌드 설정**)로 이동합니다.

2.  빌드 **설정** 창에서 **빌드를** 클릭합니다.

    ![UWP 솔루션에 대한 Unity Project 빌드](images/AzureLabs-Lab309-50.png)

3.  **파일 탐색기** 창이 팝업되어 빌드 위치를 묻는 메시지가 표시됩니다. 왼쪽 위 모서리에서 **새 폴더를** 클릭하여 새 폴더를 만들고 이름을 **BUILDS로 지정합니다.**

    ![UWP 솔루션에 대한 Unity Project 빌드](images/AzureLabs-Lab309-51.png)

    1.  새 **BUILDS** 폴더를 열고 새 **폴더를** 한 번 더 사용하여 다른 폴더를 만들고 **이름을 MR Azure Application \_ \_ \_ Insights.**

        ![UWP 솔루션에 대한 Unity Project 빌드](images/AzureLabs-Lab309-52.png)

    2.  MR **\_ Azure \_ 애플리케이션 \_ Insights** 폴더를 선택한 후 폴더 **선택을** 클릭합니다. 프로젝트를 빌드하는 데 1분 정도 소요됩니다.

4.  *빌드* 다음에 **파일 탐색기** 새 프로젝트의 위치를 보여 줍니다.

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a>13장 - 컴퓨터에 MR_Azure_Application_Insights 앱 배포

로컬 머신에 **MR \_ Azure 애플리케이션 \_ \_ Insights** 앱을 배포하려면 다음을 수행합니다.

1.  **Visual Studio** MR Azure **\_ Application \_ \_ Insights** 앱의 솔루션 파일을 엽니다.

2.  솔루션 **플랫폼에서** **x86, 로컬 머신을** 선택합니다.

3.  솔루션 **구성에서** **디버그를** 선택합니다.

    ![UWP 솔루션에 대한 Unity Project 빌드](images/AzureLabs-Lab309-53.png)

4.  빌드 **메뉴로** 이동하고 **솔루션 배포를** 클릭하여 애플리케이션을 컴퓨터에 테스트용으로 로드합니다.

5.  이제 앱이 설치된 앱 목록에 표시되고, 시작 준비가 완료됩니다.

6. 혼합 현실 애플리케이션을 시작합니다.

7. 장면 주위로 이동하여 개체에 접근하여 보고, *Azure Insight Service가* 충분한 이벤트 데이터를 수집하면 가장 근접한 개체를 녹색으로 설정합니다.

> [!IMPORTANT] 
> 서비스에서 *이벤트 및 메트릭을* 수집하기 위한 평균 대기 시간은 약 15분이지만 경우에 따라 최대 1시간이 걸릴 수 있습니다.

## <a name="chapter-14---the-application-insights-service-portal"></a>14장 - Application Insights Service 포털

장면 주변을 로밍하고 여러 개체를 쳐다 보면 *Application Insights Service* 포털에서 수집된 데이터를 볼 수 있습니다.

1.  Application Insights Service 포털에 돌아가기.

2.  *메트릭 탐색기* 클릭합니다.

    ![수집된 데이터 살펴보기](images/AzureLabs-Lab309-54.png)

3.  애플리케이션과 관련된 *이벤트 및 메트릭을* 나타내는 그래프가 포함된 탭에서 열립니다. 위에서 설명한 대로 데이터가 그래프에 표시되는 데 약간의 시간(최대 1시간)이 걸릴 수 있습니다.

    ![수집된 데이터 살펴보기](images/AzureLabs-Lab309-55.png)

4.  애플리케이션 버전별 총 *이벤트* 수에서 *이벤트 표시줄을* 클릭하여 해당 이름의 이벤트에 대한 자세한 분석을 확인합니다.

    ![수집된 데이터 살펴보기](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>Application Insights Service 애플리케이션 완료

축하합니다. Application Insights Service를 활용하여 앱 내에서 사용자의 활동을 모니터링하는 혼합 현실 앱을 빌드했습니다.

![과정 결과](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>보너스 연습

**연습 1**

ObjectInScene 개체를 수동으로 만드는 대신 생성하고 스크립트 내에서 평면에 해당 좌표를 설정합니다. 이러한 방식으로 가장 인기 있는 개체가 무엇인지 Azure에 질문하고(응시 또는 근접 결과에서) 해당 개체 중 하나를 *추가로* 생성할 수 있습니다.

**연습 2**

애플리케이션 Insights 결과를 시간별로 정렬하여 가장 관련성이 큰 데이터를 얻고 애플리케이션에서 해당 시간 중요한 데이터를 구현합니다.