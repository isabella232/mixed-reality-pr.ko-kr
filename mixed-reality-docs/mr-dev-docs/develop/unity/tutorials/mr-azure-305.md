---
title: HoloLens(1세대) 및 Azure 305 - 함수 및 스토리지
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Storage 및 함수를 구현 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 함수, storage, hololens, 모던, vr, Windows 10, Visual Studio
ms.openlocfilehash: 337b1d3fb23450325805237a6ba975861260760b7d37028b8d717bad99b9d233
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115194105"
---
# <a name="hololens-1st-gen-and-azure-305-functions-and-storage"></a>HoloLens (첫 번째 gen) 및 Azure 305: 함수 및 저장소

<br>

>[!NOTE]
>Mixed Reality 아카데미 자습서는 HoloLens(1세대) 및 Mixed Reality 몰입형 헤드셋을 염두에 두고 설계되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다.  이러한 자습서는 HoloLens 2에 사용되는 최신 도구 집합 또는 상호 작용으로 업데이트되지 **_않습니다_**.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2를 개발 하는 방법을 설명 하는 앞으로 게시 될 새 자습서가 있습니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br> 

![최종 제품-시작](images/AzureLabs-Lab5-00.png)

이 과정에서는 혼합 현실 응용 프로그램 내에서 Azure Storage 리소스를 사용 하 여 Azure Functions를 만들고 사용 하 고 데이터를 저장 하는 방법에 대해 설명 합니다.

*Azure Functions* 는 개발자가 Azure에서 작은 코드, ' 함수 '를 실행할 수 있도록 해 주는 Microsoft 서비스입니다. 이렇게 하면 다양 한 이점을 얻을 수 있는 로컬 응용 프로그램이 아닌 클라우드로 작업을 위임할 수 있습니다. *Azure Functions* 는 C \# , F \# , Node.js, Java 및 PHP를 비롯 한 몇 가지 개발 언어를 지원 합니다. 자세한 내용은 [Azure Functions 문서](/azure/azure-functions/functions-overview)를 참조 하세요.

*Azure Storage* 는 개발자가 데이터를 저장 하 고, 항상 사용 가능 하 고, 안전 하 고, 내구성이 있으며, 확장 가능 하 고, 중복 될 수 있는 보험 데이터를 저장할 수 있는 Microsoft 클라우드 서비스입니다. 즉, Microsoft는 모든 유지 관리 및 중요 한 문제를 처리 합니다. 자세한 내용은 [Azure Storage 문서](/azure/storage/common/storage-introduction)를 참조 하세요.

이 과정을 완료 하면 다음과 같은 작업을 수행할 수 있는 혼합 현실 모던 헤드셋 응용 프로그램이 만들어집니다.

1.  사용자가 장면을 응시 하도록 허용 합니다.
2.  사용자가 3D ' 단추 '에서 gazes 때 개체 생성을 트리거합니다.
3.  생성 된 개체는 Azure Function에 의해 선택 됩니다.
4.  각 개체가 생성 될 때 응용 프로그램은 *Azure Storage* 에 있는 *Azure 파일* 에 개체 형식을 저장 합니다.
5.  두 번째로 로드 되 면 *Azure 파일* 데이터가 검색 되 고 응용 프로그램의 이전 인스턴스에서 생성 작업을 재생 하는 데 사용 됩니다.

응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다. 이 과정은 Azure 서비스를 Unity Project와 통합 하는 방법을 배울 수 있도록 설계 되었습니다. 이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 및 Azure 305: 함수 및 스토리지</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정에서 주로 Windows Mixed Reality 모던 (VR) 헤드셋에 중점을 둔 반면이 과정에서 학습 하는 내용을 Microsoft HoloLens에도 적용할 수 있습니다. 과정을 진행할 때 HoloLens을 지원 하기 위해 사용 해야 하는 변경 내용에 대 한 정보를 볼 수 있습니다.

## <a name="prerequisites"></a>필수 조건

> [!NOTE]
> 이 자습서는 Unity 및 c #에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다. 또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다. [도구 설치](../../install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.

이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.

- Windows Mixed Reality 모던 (VR) 헤드셋 개발과 [호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC
- [개발자 모드를 사용 하도록 설정 된 Windows 10 Fall Creators Update 이상](../../install-the-tools.md#installation-checklist)
- [최신 Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- 개발자 모드를 사용 하는 [Windows Mixed Reality 모던 (VR) 헤드셋](../../../discover/immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](/hololens/hololens1-hardware)
- Azure 리소스를 만들기 위한 Azure 계정에 대 한 구독
- Azure 설정 및 데이터 검색을 위한 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전에

이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)

## <a name="chapter-1---the-azure-portal"></a>1 장-Azure Portal

**Azure Storage 서비스** 를 사용 하려면 Azure Portal에서 **Storage 계정을** 만들고 구성 해야 합니다.

1.  [Azure Portal](https://portal.azure.com)에 로그인 합니다.

    > [!NOTE]
    > 아직 Azure 계정이 없는 경우 새로 만들어야 합니다. 교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.

2.  로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 *Storage 계정을* 검색 한 다음 **Enter 키** 를 누릅니다.

    ![azure 저장소 검색](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > 새 단어는 **새** 포털에서 **리소스 만들기** 로 대체 되었을 수 있습니다.

3.  새 페이지에 *Azure Storage 계정* 서비스에 대 한 설명이 제공 됩니다. 이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.

    ![서비스 만들기](images/AzureLabs-Lab5-02.png)

4.  **만들기** 를 클릭 하면 다음을 클릭 합니다.

    1.  계정에 대 한 *이름을* 삽입 합니다 .이 필드에는 숫자 및 소문자만 허용 됩니다.

    2.  *배포 모델* 에서 **Resource manager** 를 선택 합니다.

    3.  *계정 종류* 에 대해 **Storage (범용 v1)** 를 선택 합니다.

    4.  새 리소스 그룹을 만드는 경우 리소스 그룹의 *위치* 를 확인 합니다. 위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.

    5.  *복제* 의 경우 **읽기 액세스-지역 중복 저장소 (RA-GRS)** 를 선택 합니다.

    6.  *성능* 은 **표준** 을 선택합니다.

    7.  *보안 전송을* **사용 하지 않도록 설정** 해야 합니다.

    8.  *구독* 을 선택합니다.

    9. 리소스 그룹을 선택 하거나 새 *리소스 그룹* 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다. 

        > Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](/azure/azure-resource-manager/resource-group-portal)하세요.

    10. 또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.

    11. **만들기** 를 선택합니다.

        ![입력 서비스 정보](images/AzureLabs-Lab5-03.png)

5.  **만들기** 를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.

6.  서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.

    ![azure portal의 새 알림](images/AzureLabs-Lab5-04.png)

7.  알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.

    ![리소스로 이동](images/AzureLabs-Lab5-05.png)

8.  알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다. 새 *Storage 계정* 서비스 인스턴스로 이동 됩니다.

    ![액세스 키](images/AzureLabs-Lab5-06.png)

9.  *액세스 키* 를 클릭 하 여이 클라우드 서비스에 대 한 끝점을 표시 합니다. *메모장* 또는 유사한를 사용 하 여 나중에 사용할 수 있도록 키 중 하나를 복사 합니다. 또한 나중에 만들 *Azureservices* 클래스에서 사용 되는 *연결 문자열* 값을 기록해 둡니다.

    ![연결 문자열 복사](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>2 장-Azure Function 설정

이제 azure 서비스에서 **azure** **Function** 을 작성 합니다.

**Azure 함수** 를 사용 하 여 코드에서 클래식 함수를 사용 하 여 수행 하는 거의 모든 작업을 수행할 수 있습니다. azure 계정에 액세스 하기 위한 자격 증명이 있는 응용 프로그램에서이 함수에 액세스할 수 있다는 차이점이 있습니다.

Azure 함수를 만들려면 다음을 수행 합니다.

1.  *Azure Portal* 의 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 *함수 앱* 를 검색 한 다음 **Enter 키** 를 누릅니다.

    ![함수 앱 만들기](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > 새 단어는 **새** 포털에서 **리소스 만들기** 로 대체 되었을 수 있습니다.

2.  새 페이지에서는 Azure 함수 *앱* 서비스에 대한 설명을 제공합니다. 이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 선택하여 이 서비스와의 연결을 만듭니다.

    ![함수 앱 정보](images/AzureLabs-Lab5-09.png)

3.  **만들기를** 클릭한 후:

    1.  앱 *이름* 를 제공합니다. 여기서는 문자와 숫자만 사용할 수 있습니다(대문자 또는 소문자 허용).

    2.  원하는 *구독을* 선택합니다.

    3. 리소스 *그룹을* 선택하거나 새 리소스 그룹을 만듭니다. 리소스 그룹은 Azure 자산 컬렉션에 대한 액세스를 모니터링, 제어, 프로비전 및 관리하는 방법을 제공합니다. 단일 프로젝트(예: 이러한 랩)와 연결된 모든 Azure 서비스를 공통 리소스 그룹 아래에 유지하는 것이 좋습니다. 

        > Azure 리소스 그룹에 대해 자세히 알아보려면 [리소스 그룹 문서 를 방문하세요.](/azure/azure-resource-manager/resource-group-portal)

    4.  이 연습에서는 *선택한* **OS** 로 Windows 선택합니다.

    5.  호스팅 계획 에 대해 *사용* **계획을** 선택합니다.

    6.  리소스 그룹의 *위치를* 결정합니다(새 리소스 그룹을 만드는 경우). 위치는 애플리케이션이 실행되는 지역에 있는 것이 가장 좋습니다. 일부 Azure 자산은 특정 지역에서만 사용할 수 있습니다. 최적의 성능을 위해 스토리지 계정과 동일한 지역을 선택합니다.

    7.  *Storage* 경우 **기존 사용 을** 선택한 다음 드롭다운 메뉴를 사용하여 이전에 만든 스토리지를 찾습니다.

    8.  이 연습에서는 *애플리케이션 Insights* 끄기 상태로 둡니다.

        ![입력 함수 앱 세부 정보](images/AzureLabs-Lab5-10.png)

4.  **만들기** 단추를 클릭합니다.

5.  **만들기를** 클릭하면 서비스가 생성될 때까지 기다려야 합니다. 이 경우 1분 정도 걸릴 수 있습니다.

6.  서비스 인스턴스가 만들어지면 포털에 알림이 표시됩니다.

    ![새 Azure Portal 알림](images/AzureLabs-Lab5-11.png)

7.  알림을 클릭하여 새 서비스 인스턴스를 탐색합니다. 

    ![리소스 함수 앱으로 이동](images/AzureLabs-Lab5-12.png)

8.  알림에서 **리소스로 이동** 단추를 클릭하여 새 서비스 인스턴스를 탐색합니다. 새 *함수 앱* 서비스 인스턴스로 이동됩니다.

9.  함수 *앱* 대시보드에서 왼쪽 패널에 있는 *Functions* 위로 마우스를 가져간 다음 **+ (더하기)** 기호를 클릭합니다.

    ![새 함수 만들기](images/AzureLabs-Lab5-13.png)

10. 다음 페이지에서 **Webhook + API가** 선택되어 있는지 확인하고 *언어 선택에서* **CSharp** 를 선택합니다. 이 언어는 이 자습서에 사용되는 언어입니다. 마지막으로 **이 함수 만들기** 단추를 클릭합니다.

    ![웹 후크 csharp 선택](images/AzureLabs-Lab5-14.png)

11. 코드 페이지(run.csx)로 이동해야 합니다. 그렇지 않은 경우 왼쪽 패널 내의 함수 목록에서 새로 만든 함수를 클릭합니다.

    ![새 함수 열기](images/AzureLabs-Lab5-15.png)

12. 다음 코드를 함수에 복사합니다. 이 함수는 호출될 때 0에서 2 사이의 임의 정수를 반환합니다. 기존 코드에 대해 걱정하지 말고, 자유롭게 위에 붙여넣습니다.

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. **저장** 을 선택합니다.

14. 결과는 아래 이미지와 같습니다.

15. 함수 **URL 받기를** 클릭하고 표시된 *엔드포인트를* 기록해 둡다. 이 과정의 후반부에서 만들 *AzureServices* 클래스에 삽입해야 합니다.

    ![함수 엔드포인트를 얻습니다.](images/AzureLabs-Lab5-16.png)

    ![함수 엔드포인트 삽입](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>3장 - Unity 프로젝트 설정

다음은 Mixed Reality 개발하기 위한 일반적인 설정이며, 따라서 다른 프로젝트에 적합한 템플릿입니다.

혼합 현실 몰입형 헤드셋을 설정하고 테스트합니다.

> [!NOTE]
> 이 과정에는 모션 컨트롤러가 필요하지 **않습니다.** 몰입형 헤드셋 설정 지원이 필요한 경우 [혼합 현실 설정 문서 를 방문하세요.](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)

1.  Unity를 열고 **새로** 만들기를 클릭합니다.

    ![새 Unity 프로젝트 만들기](images/AzureLabs-Lab5-17.png)

2.  이제 Unity Project 이름을 제공해야 합니다. **MR_Azure_Functions** 삽입합니다. 프로젝트 형식이 **3D 로** 설정되어 있는지 확인합니다. *위치를* 적절한 위치로 설정합니다(루트 디렉터리에 가까울수록 좋습니다). 그런 다음 **프로젝트 만들기를** 클릭합니다.

    ![새 Unity 프로젝트에 이름 지정](images/AzureLabs-Lab5-18.png)

3.  Unity가 열려 있는 경우 기본 **스크립트 편집기가** **Visual Studio** 로 설정되어 있는지 확인하는 것이 좋습니다. 기본 설정 **편집으로**  >   이동한 다음 새 창에서 **외부 도구** 로 이동합니다. **외부 스크립트 편집기를** **Visual Studio 2017로** 변경합니다. 기본 **설정** 창을 닫습니다.

    ![Visual Studio를 스크립트 편집기로 설정](images/AzureLabs-Lab5-19.png)

4.  다음으로, **플랫폼** 전환 단추를 클릭하여 파일 빌드 설정 이동하여  >   플랫폼을 유니버설 **Windows 플랫폼으로** **전환합니다.**

    ![플랫폼을 uwp로 전환](images/AzureLabs-Lab5-20.png)

5.  파일   >  **빌드 설정** 이동하여 다음을 확인합니다.

    1. **대상 디바이스는** **모든 디바이스** 로 설정됩니다.

        > Microsoft HoloLens **대상 디바이스를** *HoloLens* 설정합니다.

    2. **빌드 유형이** **D3D로** 설정됩니다.

    3. **SDK가** **최신 설치로 설정됩니다.**

    4. **Visual Studio 버전이** 최신 **설치로 설정됩니다.**

    5. **빌드 및 실행이** **로컬 컴퓨터로 설정됩니다.**

    6. 장면을 저장하고 빌드에 추가합니다.

        1.  열린 장면 추가 를 선택하여 이 작업을 **수행합니다.** 저장 창이 나타납니다.

            ![열린 장면 추가](images/AzureLabs-Lab5-21.png)

        2.  이에 대한 새 폴더 및 이후의 장면을 만든 다음, 새 폴더 단추를 선택하여 새 **폴더를** 만들고 이름을 **Scenes로** 지정합니다.

            ![장면 폴더 만들기](images/AzureLabs-Lab5-22.png)

        3.  새로 만든 **Scenes** 폴더를 열고 **파일 이름:** 텍스트 필드에 **FunctionsScene 을** 입력한 **다음, 저장을** 누릅니다.

            ![함수 장면 저장](images/AzureLabs-Lab5-23.png)

6.  **빌드 설정** 나머지 설정은 현재 기본값으로 유지되어야 합니다.

    ![기본 빌드 설정을 그대로 둡니다.](images/AzureLabs-Lab5-24.png)

7.  빌드 *설정* 창에서 **플레이어 설정** 단추를 클릭하면 *Inspector가* 있는 공간에서 관련 패널이 열립니다.

    ![검사기에서 플레이어 설정](images/AzureLabs-Lab5-25.png)

8.  이 패널에서 몇 가지 설정을 확인해야 합니다.

    1.  기타 **설정** 탭에서 다음을 수행합니다.

        1.  **런타임 버전 스크립팅은** **실험적(.NET** 4.6 동등)이어야 하며, 편집기를 다시 시작해야 합니다.
        2.  **스크립팅 백 엔드는** **.NET이어야 합니다.**
        3.  **API 호환성 수준은** **.NET 4.6이어야** 합니다.

    2.  게시 **설정** 탭의 기능 아래에서 **다음을 확인합니다.**
        
        -  **InternetClient**

            ![기능 설정](images/AzureLabs-Lab5-26.png)

    3.  패널의 아래쪽에 있는 **XR 설정(게시 설정** 아래에 **있음)에서** 가상 **현실 지원됨을** 틱하여 **Windows Mixed Reality SDK가** 추가되었는지 확인합니다.

        ![XR 설정 설정](images/AzureLabs-Lab5-27.png)

9.  빌드 *설정* *Unity C# 프로젝트로* 돌아가면 더 이상 회색으로 표시됩니다. 이 옆에 있는 확인란을 선택합니다.

    ![틱 c# 프로젝트](images/AzureLabs-Lab5-28.png)

10.  빌드 설정 창을 닫습니다.

11. 장면을 저장하고 Project(FILE  >  **SAVE SCENE / FILE**  >  **SAVE PROJECT**).

## <a name="chapter-4---setup-main-camera"></a>4장 - 기본 카메라 설정

> [!IMPORTANT]
> 이 과정의 Unity *구성* 요소 설정을 건너뛰고 코드를 계속 진행하려면 [이 .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)를 다운로드하고 사용자 지정 [패키지](https://docs.unity3d.com/Manual/AssetPackages.html)로 프로젝트에 가져올 수 있습니다. 여기에는 다음 챕터의 DLL도 포함됩니다. 가져온 후 [7 장](#chapter-7---create-the-azureservices-class)에서 계속 진행 합니다. 

1.  *계층 패널* 에서 **주 카메라** 라는 개체를 찾을 수 있습니다 .이 개체는 응용 프로그램 "내부"에 있는 경우의 "헤드" 관점을 나타냅니다.

2.  앞의 Unity 대시보드를 사용 하 여 **기본 카메라 GameObject** 를 선택 합니다. *검사기 패널* (일반적으로 대시보드 내에서 오른쪽에 있음)에는 해당 *GameObject* 의 다양 한 구성 요소, 위쪽의 *변환* , *카메라* 및 기타 구성 요소가 표시 됩니다. 기본 카메라의 변환을 다시 설정 해야 올바른 위치에 배치 됩니다.

3.  이렇게 하려면 카메라의 *변형* 구성 요소 옆에 있는 **기어** 아이콘을 선택 하 고 **다시 설정** 을 선택 합니다.

    ![변환 다시 설정](images/AzureLabs-Lab5-29.png)

4.  그런 다음 **변형** 구성 요소를 다음과 같이 업데이트 합니다.

    |         |    변환 위치   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **예**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | 변환-회전 |       |
    | :---: | :------------------: | :----:|
    | **X** | **예**                | **Z** |
    | 0     | 0                    | 0     |

    |       | 변환-배율 |       |
    | :---: | :---------------: | :---: |
    | **X** | **예**             | **Z** |
    | 1     | 1                 | 1     |

    ![카메라 변환 설정](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>5 장-Unity 장면 설정

1.  *계층 패널* 의 빈 영역을 마우스 오른쪽 단추로 클릭 하 고 **3d 개체** 아래에서 **평면** 을 추가 합니다.

    ![새 평면 만들기](images/AzureLabs-Lab5-31.png)

2.  **평면** 개체가 선택 된 상태에서 *Inspector 패널* 의 다음 매개 변수를 변경 합니다.

    |       | 변환 위치 |       |
    | :---: | :------------------: | :---: |
    | **X** | **예**                | **Z** |
    | 0     | 0                    | 4     |

    |       | 변환-배율 |       |
    | :---: | :---------------: | :---: |
    | **X** | **예**             | **Z** |
    | 10    | 1                 | 10    |

    ![평면 위치 및 배율 설정](images/AzureLabs-Lab5-32.png)

    ![평면의 장면 보기](images/AzureLabs-Lab5-33.png)

3.  *계층 패널* 의 빈 영역을 마우스 오른쪽 단추로 클릭 하 고 **3d 개체** 아래에서 **큐브** 를 추가 합니다.

    1.  큐브 이름을 **GazeButton** 로 바꿉니다 (큐브를 선택 하 고 ' F2 '를 누릅니다).

    2.  *검사기 패널* 에서 다음 매개 변수를 변경 합니다.

        |       | 변환 위치 |       |
        | :---: | :------------------: |:-----:|
        | **X** | **예**                | **Z** |
        | 0     | 3                    | 5     |


        ![응시 단추 변환 설정](images/AzureLabs-Lab5-34.png)

        ![응시 단추 장면 보기](images/AzureLabs-Lab5-35.png)

    3.  **태그 드롭다운 단추** 를 클릭 하 고 **태그 추가** 를 클릭 하 여 *& 레이어 창 태그* 를 엽니다.

        ![새 태그 추가](images/AzureLabs-Lab5-36.png)

        ![더하기 더하기](images/AzureLabs-Lab5-37.png)

    4.  **+ (더하기)** 단추를 선택 하 고 *새 태그 이름* 필드에 **GazeButton** 를 입력 하 고 **저장** 을 누릅니다.

        ![새 태그 이름](images/AzureLabs-Lab5-38.png)

    5.  *계층 패널* 에서 **GazeButton** 개체를 클릭 하 고 *검사기 패널* 에서 새로 만든 **GazeButton** 태그를 할당 합니다.

        ![새 태그에 응시 단추 할당](images/AzureLabs-Lab5-39.png)

4.  *계층 패널* 에서 **GazeButton** 개체를 마우스 오른쪽 단추로 클릭 하 고 **빈 GameObject** ( *자식* 개체로 추가 됨)를 추가 합니다.

5.  새 개체를 **선택 하 고** 이름을 지정 합니다.

    1.  *검사기 패널* 에서 다음 매개 변수를 변경 합니다.

        |       | 변환 위치 |       |
        | :---: | :------------------: |:----: |
        | **X** |**예**                 | **Z** |
        | 0     | -1                   | 0     |

        ![셰이프 생성 지점 변환 업데이트](images/AzureLabs-Lab5-40.png)

        ![셰이프 생성 지점 장면 보기](images/AzureLabs-Lab5-41.png)

6.  다음으로, Azure 서비스의 상태에 대 한 피드백을 제공 하는 **3D 텍스트** 개체를 만듭니다.

    계층 패널에서 **GazeButton** 를 마우스 오른쪽 단추로 다시 클릭 하 고 **3d 개체**  >  **3d 텍스트** 개체를 *자식* 으로 추가 합니다.

    ![새 3D 텍스트 개체 만들기](images/AzureLabs-Lab5-42.png)

7.  **3D 텍스트** 개체의 이름을 **AzureStatusText** 로 바꿉니다.

8.  **AzureStatusText** 개체 변환을 다음과 같이 변경 합니다.

    |       | 변환 위치 |       |
    | :---: | :------------------: | :---: |
    | **X** | **예**                | **Z** |
    | 0     | 0                    | -0.6  |

    |       | 변환-배율 |       |
    | :---: | :---------------: | :---: |
    | **X** | **예**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > 아래 텍스트 메시 구성 요소가 업데이트될 때 수정될 예정이기 때문에 오프 센터처럼 보이는 경우 걱정하지 마세요.

9.  텍스트 **메시** 구성 요소를 아래와 일치하도록 변경합니다.

    ![텍스트 메시 구성 요소 설정](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > 여기서 선택한 색은 16진수 색인 **000000FF이지만** 자유롭게 직접 선택할 수 있지만 읽을 수 있는지 확인합니다.

10. 이제 계층 구조 패널 구조가 다음과 같이 표시됩니다.

    ![계층 구조의 텍스트 메시](images/AzureLabs-Lab5-43b.png)

10. 이제 장면은 다음과 같이 보입니다.

    ![장면 보기의 텍스트 메시](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>6장 - Unity용 Azure Storage 가져오기

Unity용 Azure Storage 사용하게 됩니다(자체에서 Azure용 .Net SDK를 활용함). 이에 대한 자세한 내용은 [Unity용 Azure Storage 문서에서](/sandbox/gamedev/unity/azure-storage-unity)확인할 수 있습니다.

현재 Unity에는 가져온 후 플러그 인을 다시 구성해야 하는 알려진 문제가 있습니다. 버그가 해결된 후에는 이러한 단계(이 섹션의 4-7)가 더 이상 필요하지 않습니다.

SDK를 사용자 고유의 프로젝트로 가져오려면 GitHub 에서 최신 ['.unitypackage'를](https://aka.ms/azstorage-unitysdk)다운로드했는지 확인합니다. 그런 후 다음을 수행합니다.

1.  자산 패키지 가져오기 사용자 지정 패키지 메뉴 옵션을 사용하여 **Unity에 .unitypackage** 파일을 **추가합니다.**  >    >  

2.  팝업되는 **Unity 패키지 가져오기** 상자의 플러그 **인** Storage 아래에서 모든 것을 선택할 수  >  있습니다. 이 과정에 필요하지 않기 때문에 다른 모든 사항의 선택을 취소합니다.

    ![패키지로 가져오기](images/AzureLabs-Lab5-45.png)

3.  **가져오기** 단추를 클릭하여 프로젝트에 항목을 추가합니다.

4.  *Project* 보기에서 *플러그 인* 아래의 Storage 폴더로 이동하고 다음 플러그 *인만* 선택합니다.

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![uncheck Any platform](images/AzureLabs-Lab5-46.png)

5.  *이러한 특정 플러그 인을* 선택한 상태로 모든 **플랫폼의 선택을 취소하고**  *WSAPlayer를* **선택 취소한** 다음 **적용을** 클릭합니다.

    ![플랫폼 dll 적용](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Unity 편집기에서만 사용할 수 있도록 이러한 특정 플러그 인을 표시합니다. 이는 Unity에서 프로젝트를 내보낸 후 사용되는 WSA 폴더에 동일한 플러그 인의 다른 버전이 있기 때문입니다.

6.  *Storage* 플러그 인 폴더에서 다음만 선택합니다.

    -   Microsoft.Data.Services.Client

        ![dll에 대해 set가 처리되지 않습니다.](images/AzureLabs-Lab5-48.png)

7.  *플랫폼 설정* **처리 안** 함을 선택하고 **적용을** 클릭합니다.

    ![처리를 적용하지 않습니다.](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Unity 어셈블리 패치가 이 플러그 인을 처리하는 데 어려움이 있으므로 이 플러그 인을 "처리 안 됨"으로 표시합니다. 플러그 인은 처리되지 않더라도 계속 작동합니다.

## <a name="chapter-7---create-the-azureservices-class"></a>7장 - AzureServices 클래스 만들기

만들려는 첫 번째 클래스는 *AzureServices* 클래스입니다.

*AzureServices* 클래스는 다음을 담당합니다.

-   Azure 계정 자격 증명 저장

-   Azure 앱 함수 호출

-   Azure Cloud Storage 데이터 파일 업로드 및 다운로드

이 클래스를 만들려면 다음을 수행합니다.

1.  Project 패널에 있는 *자산* 폴더를 마우스 오른쪽 단추로 클릭하고 폴더 **만들기를 클릭합니다.**  >   폴더 이름을 **Scripts 로 지정합니다.**

    ![새 폴더 만들기](images/AzureLabs-Lab5-50.png)

    ![call 폴더 - 스크립트](images/AzureLabs-Lab5-51.png)

2.  방금 만든 폴더를 두 번 클릭하여 엽니다.

3.  C# 스크립트 **만들기** 폴더 내부를 마우스 오른쪽  >  **단추로** 클릭합니다. *AzureServices 스크립트를 호출합니다.*

4.  새 *AzureServices* 클래스를 두 번 클릭하여 *Visual Studio.*

5.  *AzureServices의* 맨 위에 다음 네임스페이스를 추가합니다.

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  *AzureServices* 클래스 내에 다음 검사기 필드를 추가합니다.

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  그런 *다음, AzureServices* 클래스 내에 다음 멤버 변수를 추가합니다.

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > *엔드포인트* 및 *연결 문자열* 값을 Azure Portal에 있는 Azure Storage의 값으로 바꾸어야 합니다.

8.  이제 *Awake()* 및 *Start()* 메서드에 대한 코드를 추가해야 합니다. 이러한 메서드는 클래스가 초기화될 때 호출됩니다.

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > [이후 챕터에서](#chapter-10---completing-the-azureservices-class) *CallAzureFunctionForNextShape()에* 대한 코드를 작성합니다.

9.  *Update()* 메서드를 삭제합니다. 이 클래스는 이 메서드를 사용하지 않기 때문에 삭제합니다.

10. 변경 내용을 Visual Studio 저장한 다음 Unity로 돌아갑니다.

11. *AzureServices 클래스를* 클릭하여 Scripts 폴더에서 *계층 패널의* Main Camera 개체로 끌어다 끕니다.

12. 주 카메라를 선택한 다음, **GazeButton** 개체 아래에서 **AzureStatusText** 자식 개체를 잡고, *검사기* 의 **AzureStatusText** 참조 대상 필드 내에 배치하여 *AzureServices* 스크립트에 대한 참조를 제공합니다.

    ![azure status text reference target 할당](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>8장 - ShapeFactory 클래스 만들기

만들 다음 스크립트는 *ShapeFactory* 클래스입니다. 이 클래스의 역할은 요청 시 새 도형을 만들고 도형 기록 목록에서 만든 *도형의* 기록을 유지하는 것입니다. 셰이프를 만들 때마다 *도형 기록 목록이* *AzureService* 클래스에서 업데이트된 다음 *Azure Storage* 저장됩니다. 애플리케이션이 시작되면 저장된 파일이 *Azure Storage* 있는 경우 *생성된 셰이프가* 스토리지에서 제공되는지 또는 새 형태인지를 제공하는 **3D Text** 개체와 함께 도형 기록 목록이 검색되고 재생됩니다.

이 클래스를 만들려면 다음을 수행합니다.

1.  이전에 만든 **Scripts** 폴더로 이동합니다.

2.  C# 스크립트 **만들기** 폴더 내부를 마우스 오른쪽  >  **단추로** 클릭합니다. *스크립트 ShapeFactory를 호출합니다.*

3.  새 *ShapeFactory* 스크립트를 두 번 클릭하여 *Visual Studio* 으로 엽니다.

4.  *ShapeFactory* 클래스에 다음 네임스페이스가 포함되어 있는지 확인합니다.

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  아래에 표시된 변수를 *ShapeFactory* 클래스에 추가하고 *Start()* 및 *Awake()* 함수를 아래 함수로 대체합니다.

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  *CreateShape()* 메서드는 제공된 *정수* 매개 변수를 기반으로 기본 도형을 생성합니다. 부울 매개 변수는 현재 생성된 셰이프가 스토리지에서 생성되었는지 아니면 새 셰이프인지를 지정하는 데 사용됩니다. 이전 메서드 아래의 *ShapeFactory* 클래스에 다음 코드를 배치합니다.

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  Unity로 돌아가기 전에 변경 내용을 Visual Studio 저장해야 합니다.

8.  Unity 편집기로 돌아가서 *ShapeFactory* 클래스를 클릭하여 **Scripts** 폴더에서 계층 *구조 패널의* **주 카메라** 개체로 끌어다 끕니다.

9. 주 카메라를 선택하면 *ShapeFactory* 스크립트 구성 요소에 *생성 지점* 참조가 누락된 것을 알 수 있습니다. 이 문제를 해결하려면 **ShapeSpawnPoint** 개체를 *계층 구조 패널에서* 생성 **지점** 참조 대상으로 끕니다.

    ![셰이프 팩터리 참조 대상 설정](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>9장 - Gaze 클래스 만들기

만들어야 하는 마지막 스크립트는 *Gaze* 클래스입니다.

이 클래스는 사용자가 보고 있는 개체를 감지하기 위해 주 카메라에서 앞으로 프로젝싱되는 **Raycast를** 만드는 작업을 담당합니다. 이 경우 Raycast는 사용자가 장면에서 **GazeButton** 개체를 보고 있는지 확인하고 동작을 트리거해야 합니다.

이 클래스를 만들려면 다음을 수행합니다.

1.  이전에 만든 **Scripts** 폴더로 이동합니다.

2.  Project 패널에서 C# 스크립트 **만들기** 를 마우스 오른쪽  >  **단추로** 클릭합니다. *스크립트 응시* 를 호출합니다.

3.  새 *응시* 스크립트를 두 번 클릭하여 *Visual Studio 엽니다.*

4.  다음 네임스페이스가 스크립트의 맨 위에 포함되어 있는지 확인합니다.

    ```csharp
        using UnityEngine;
    ```

5.  그런 *다음, Gaze* 클래스 내에 다음 변수를 추가합니다.

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> 이러한 변수 중 일부는 *편집기* 에서 편집할 수 있습니다.

6.  *이제 Awake()* 및 *Start() 메서드에* 대한 코드를 추가해야 합니다.

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  GazeEnabled 부울이 전환되는 위치와 함께 Raycast 메서드를 실행하는 *Update()* 메서드와 함께 시작 시 커서 개체를 만드는 다음 코드를 추가합니다.

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. 다음으로, Raycast를 프로젝트하고 적중 대상을 검색하는 *UpdateRaycast()* 메서드를 추가합니다.

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

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

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. 마지막으로 새 도형을 만드는지 여부를 나타내는 GazeButton 개체의 현재 색을 토글하는 *ResetFocusedObject()* 메서드를 추가합니다.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  Unity로 돌아가기 전에 변경 내용을 Visual Studio 저장합니다.

11.  *Gaze* 클래스를 클릭하여 Scripts 폴더에서 *Hierarchy Panel* 의 **Main Camera** 개체로 끌어다 끕니다.

## <a name="chapter-10---completing-the-azureservices-class"></a>10장 - AzureServices 클래스 완료

다른 스크립트를 배치하면 이제 *AzureServices* 클래스를 *완료할* 수 있습니다. 이 작업을 수행하려면 다음을 수행합니다.

1.  *CreateCloudIdentityAsync()* 라는 새 메서드를 추가하여 Azure와 통신하는 데 필요한 인증 변수를 설정합니다.

    > 이 메서드는 도형 목록을 포함하는 이전에 저장된 파일이 있는지도 확인합니다.
    >
    > **파일이 발견되면** 사용자 *응시* 를 사용하지 않도록 설정하고 **Azure Storage 파일에** 저장된 모양 패턴에 따라 셰이프 만들기를 트리거합니다. 사용자가 볼 수 있습니다. **텍스트 메시는** 도형 원점에 따라 'Storage' 또는 '신규' 표시를 제공하게 됩니다.
    >
    > **파일이 없으면** 사용자가 장면에서 *GazeButton* 개체를 확인할 때 모양을 만들 수 있도록 **Gaze를** 사용하도록 설정합니다.

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  다음 코드 조각은 *Start()* 메서드 내의 코드 조각입니다. 여기서 *CreateCloudIdentityAsync()* 메서드를 호출합니다. 아래와 같이 현재 *Start()* 메서드를 자유롭게 복사해 보세요.

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  *CallAzureFunctionForNextShape()* 메서드에 대한 코드를 입력합니다. 이전에 만든 Azure *함수 앱을* 사용하여 셰이프 인덱스 요청합니다. 새 셰이프가 수신되면 이 메서드는 *셰이프를 ShapeFactory* 클래스로 전송하여 장면에 새 셰이프를 만듭니다. 아래 코드를 사용하여 *CallAzureFunctionForNextShape()* 본문을 완료합니다.

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  셰이프 기록 목록에 저장된 정수를 연결하고 *Azure Storage 파일에* 저장하여 문자열을 만드는 메서드를 추가합니다.

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  메서드를 추가하여 *Azure Storage* 파일에 저장된 텍스트를 검색하고 목록으로 *deserialize합니다.*

6.  이 프로세스가 완료되면 메서드는 사용자가 장면에 더 많은 모양을 추가할 수 있도록 응시를 다시 사용하도록 설정합니다.

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  Unity로 돌아가기 전에 변경 내용을 Visual Studio 저장합니다.

## <a name="chapter-11---build-the-uwp-solution"></a>11장 - UWP 솔루션 빌드

빌드 프로세스를 시작하려면 다음을 수행합니다.

1.  파일   >  **빌드 설정** 이동합니다.

    ![앱 빌드](images/AzureLabs-Lab5-54.png)

2.  **빌드** 를 클릭한 다음 Unity는 *파일 탐색기* 창을 시작하고, 여기서 앱을 빌드할 폴더를 선택해야 합니다. 이제 해당 폴더를 만들고 이름을 *앱으로* 지정합니다. 그런 *다음, 앱* 폴더를 선택한 후 **폴더 선택을** 누릅니다.

3.  Unity에서 *App* 폴더에 대한 프로젝트 빌드를 시작합니다.

4.  Unity 빌드가 완료되면(시간이 걸릴 수 있음) 빌드 위치에서 *파일 탐색기* 창이 열립니다(작업 표시줄이 항상 창 위에 표시되지는 않지만 새 창이 추가되었음을 알려 주시기 때문에 작업 표시줄 확인).

## <a name="chapter-12---deploying-your-application"></a>12장 - 애플리케이션 배포

애플리케이션을 배포하려면 다음을 수행합니다.

1.  [마지막 챕터](#chapter-11---build-the-uwp-solution)에서 만든 *App* 폴더로 이동합니다. 앱 이름이 '.sln' 확장명을 가진 파일이 표시되며, 이 파일은 두 번 클릭해야 하므로 *Visual Studio* 내에서 엽니다.

2.  솔루션 **플랫폼에서** **x86, 로컬 머신을** 선택합니다.

3.  솔루션 **구성에서** **디버그를** 선택합니다.

    > Microsoft HoloLens 경우 컴퓨터에 테더링되지 않도록 *원격 컴퓨터* 로 설정하는 것이 더 쉬울 수 있습니다. 그러나 다음을 수행해야 합니다.
    > - 설정  Network & 인터넷 Wi-Fi 고급 옵션 내에서 찾을 수 있는 **HoloLens** IP 주소를 알고  >    >    >  있습니다. IPv4는 사용해야 하는 주소입니다. 
    > - **개발자 모드가** **켜기인지 확인합니다.** 개발자용 **설정**  >  **업데이트 &**  >  **보안에 있습니다.**

    ![솔루션 배포](images/AzureLabs-Lab5-55.png)

4.  **빌드** 메뉴로 이동하고 **솔루션 배포를** 클릭하여 애플리케이션을 컴퓨터에 테스트용으로 로드합니다.

5.  이제 앱이 설치된 앱 목록에 표시되고, 시작 및 테스트할 준비가 되었습니다.

## <a name="your-finished-azure-functions-and-storage-application"></a>완료된 Azure Functions 및 Storage 애플리케이션

축하합니다. Azure Functions 및 Azure Storage 서비스를 모두 활용하는 혼합 현실 앱을 빌드했습니다. 앱은 저장된 데이터를 그리고 해당 데이터를 기반으로 작업을 제공할 수 있습니다.

![final product -end](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

두 번째 생성 지점 및 개체를 만든 지점을 생성하는 레코드를 만듭니다. 데이터 파일을 로드할 때 원래 생성된 위치에서 생성되는 도형을 재생합니다.

### <a name="exercise-2"></a>연습 2

매번 다시 열지 않고 앱을 다시 시작하는 방법을 만듭니다. **장면 로드는** 시작하기에 좋은 지점입니다. 이렇게 하면 앱에서 쉽게 다시 설정할 수 있도록 *Azure Storage* 의 저장된 목록을 지우는 방법을 만듭니다.