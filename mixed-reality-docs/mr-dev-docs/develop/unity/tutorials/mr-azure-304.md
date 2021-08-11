---
title: HoloLens(1세대) 및 Azure 304 - 얼굴 인식
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 알아봅니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 얼굴 인식, hololens, 모던, vr, Windows 10, Visual Studio
ms.openlocfilehash: 2547b61669884c524fdd605240322dc9d568039b5a202d0a411317b0e83bd547
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219564"
---
# <a name="hololens-1st-gen-and-azure-304-face-recognition"></a>HoloLens (첫 번째 gen) 및 Azure 304: 얼굴 인식

<br>

>[!NOTE]
>Mixed Reality 아카데미 자습서는 HoloLens(1세대) 및 Mixed Reality 몰입형 헤드셋을 염두에 두고 설계되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다.  이러한 자습서는 HoloLens 2에 사용되는 최신 도구 집합 또는 상호 작용으로 업데이트되지 **_않습니다_**.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2를 개발 하는 방법을 설명 하는 앞으로 게시 될 새 자습서가 있습니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

![이 과정을 완료 한 결과](images/AzureLabs-Lab4-00.png)

이 과정에서는 Microsoft Face API와 함께 Azure Cognitive Services를 사용 하 여 혼합 현실 응용 프로그램에 얼굴 인식 기능을 추가 하는 방법에 대해 설명 합니다.

*Azure Face API* 는 개발자에 게 클라우드에서 가장 높은 고급 얼굴 알고리즘을 제공 하는 Microsoft 서비스입니다. *Face API* 에는 특성을 사용한 얼굴 감지 및 얼굴 인식 이라는 두 가지 주요 기능이 있습니다. 이를 통해 개발자는 단지 얼굴에 대 한 그룹 집합을 설정 하 고 나중에 쿼리 이미지를 서비스로 보내 얼굴을 확인할 수 있습니다. 자세한 내용은 [Azure 얼굴 인식 페이지](https://azure.microsoft.com/services/cognitive-services/face/)를 참조 하세요.

이 과정을 완료 하면 다음과 같은 작업을 수행할 수 있는 혼합 현실 HoloLens 응용 프로그램이 만들어집니다.

1. **탭 제스처** 를 사용 하 여 온보드 HoloLens 카메라를 사용 하 여 이미지 캡처를 시작 합니다. 
2. 캡처된 이미지를 *Azure Face API* 서비스로 보냅니다.
3. *Face API* 알고리즘의 결과를 받습니다.
4. 단순한 사용자 인터페이스를 사용 하 여 일치 하는 사용자의 이름을 표시 합니다.

이렇게 하면 Face API 서비스에서 Unity 기반 혼합 현실 응용 프로그램으로 결과를 가져오는 방법을 배울 수 있습니다.

응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다. 이 과정은 Azure 서비스를 Unity Project와 통합 하는 방법을 배울 수 있도록 설계 되었습니다. 이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 304: 얼굴 인식</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정에서 주로 HoloLens에 중점을 둔 반면이 과정에서 학습 하는 내용을 Windows Mixed Reality 모던 (VR) 헤드셋에도 적용할 수 있습니다. 모던 (VR) 헤드셋은 액세스할 수 있는 카메라를 포함 하지 않으므로 PC에 연결 된 외부 카메라가 필요 합니다. 이 과정을 진행 하면서 모던 (VR) 헤드셋을 지원 하기 위해 사용 해야 하는 변경 내용에 대 한 정보를 볼 수 있습니다.

## <a name="prerequisites"></a>필수 조건

> [!NOTE]
> 이 자습서는 Unity 및 c #에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다. 또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다. [도구 설치](../../install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.

이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.

- Windows Mixed Reality 모던 (VR) 헤드셋 개발과 [호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC
- [개발자 모드를 사용 하도록 설정 된 Windows 10 Fall Creators Update 이상](../../install-the-tools.md)
- [최신 Windows 10 SDK](../../install-the-tools.md)
- [Unity 2017.4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- 개발자 모드를 사용 하는 [Windows Mixed Reality 모던 (VR) 헤드셋](../../../discover/immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](/hololens/hololens1-hardware)
- PC에 연결 된 카메라 (몰입 형 헤드셋 개발용)
- Azure 설정 및 Face API 검색을 위한 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전에

1.  이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)
2.  HoloLens를 설정 하 고 테스트 합니다. HoloLens 설정에 대 한 지원이 필요한 경우 [HoloLens 설치 문서를 방문 해야](/hololens/hololens-setup)합니다. 
3.  새 HoloLens 앱 개발을 시작할 때 보정 및 센서 조정을 수행 하는 것이 좋습니다 (경우에 따라 각 사용자에 대해 해당 작업을 수행 하는 데 도움이 될 수 있음). 

보정에 대 한 도움말을 보려면 [HoloLens 보정 문서에 대 한 링크를](/hololens/hololens-calibration#hololens-2)참조 하세요.

센서 조정에 대 한 도움말을 보려면 [HoloLens 센서 조정 문서에 대 한 링크를](/hololens/hololens-updates)참조 하세요.

## <a name="chapter-1---the-azure-portal"></a>1 장-Azure Portal

Azure에서 *Face API* 서비스를 사용 하려면 응용 프로그램에서 사용할 수 있도록 서비스 인스턴스를 구성 해야 합니다.

1.  먼저 [Azure Portal](https://portal.azure.com)에 로그인 합니다. 

    > [!NOTE]
    > 아직 Azure 계정이 없는 경우 새로 만들어야 합니다. 교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.

2.  로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 *Face API* 를 검색 한 후 **enter** 키를 누릅니다.

    ![face api 검색](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > 새 단어는 **새** 포털에서 **리소스 만들기** 로 대체 되었을 수 있습니다.

3.  새 페이지에 *Face API* 서비스에 대 한 설명이 제공 됩니다. 이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.

    ![face api 정보](images/AzureLabs-Lab4-02.png)

4.  **만들기** 를 클릭 하면 다음을 클릭 합니다.

    1. 이 서비스 인스턴스의 원하는 이름을 삽입 합니다.

    2. 구독을 선택합니다.

    3. 적절 한 가격 책정 계층을 선택 합니다. *Face API 서비스* 를 처음 만드는 경우 무료 계층 (명명 된 F0)을 사용할 수 있어야 합니다.

    4. 리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다. 

        > Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](/azure/azure-resource-manager/resource-group-portal)하세요.

    5. 나중에 사용 하는 UWP 앱 인 **Person 작성자** 는 위치에 ' 미국 서 부 '를 사용 해야 합니다.

    6. 또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.

    7. **만들기 *를 선택 합니다.**

        ![face api 서비스 만들기](images/AzureLabs-Lab4-03.png)

5.  **만들기 *를** 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이는 1 분 정도 걸릴 수 있습니다.

6.  서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.

    ![서비스 만들기 알림](images/AzureLabs-Lab4-04.png)

7.  알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.

    ![리소스 알림으로 이동](images/AzureLabs-Lab4-05.png)

8.  준비가 되 면 알림에서 리소스로 **이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.

    ![액세스 얼굴 api 키](images/AzureLabs-Lab4-06.png)

9.  이 자습서에서 응용 프로그램은 서비스에 대 한 호출을 수행 해야 합니다 .이 작업은 서비스의 ' 키 ' 구독을 사용 하 여 수행 됩니다. *Face API* 서비스의 *빠른 시작* 페이지에서 첫 번째 지점은 번호 1 이며 *키를 가져옵니다.*

10. *서비스* 페이지에서 파란색 **키** 하이퍼링크 (빠른 시작 페이지의 경우) 또는 서비스 탐색 메뉴 (왼쪽에서 ' 키 ' 아이콘으로 표시 됨)의 **키** 링크를 선택 하 여 키를 표시 합니다.

    > [!NOTE] 
    > 나중에 필요 하므로 키 중 하나를 기록 하 고 보호 합니다.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>2 장-' Person Maker ' UWP 응용 프로그램 사용

[Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)라는 미리 작성 된 UWP 응용 프로그램을 다운로드 해야 합니다. 이 앱은이 과정의 최종 제품이 아니므로 이후 프로젝트에서 사용 하는 Azure 항목을 만드는 데 도움이 되는 도구입니다.

**Person Maker** 를 사용 하면 사용자와 연결 된 Azure 항목 및 사용자 그룹을 만들 수 있습니다. 응용 프로그램은 추가 된 사용자의 얼굴을 인식 하기 위해 나중에 FaceAPI에서 사용할 수 있는 형식으로 필요한 모든 정보를 저장 합니다. 

> 중요 한 **사용자 작성자** 는 몇 가지 기본 제한을 사용 하 여 **무료 구독 계층** 에 대 한 분당 서비스 호출 수를 초과 하지 않도록 합니다. 제한이 발생 하면 위쪽의 녹색 텍스트가 빨강으로 변경 되 고 ' 활성 '으로 업데이트 됩니다. 이 경우 응용 프로그램을 대기 합니다. 다음에는 계속 해 서 face 서비스에 액세스할 수 있을 때까지 기다린 후 다시 사용할 수 있는 경우 ' 활성 '으로 업데이트 합니다.

이 응용 프로그램은 Face API를 모두 사용할 수 있도록 하는 *ProjectOxford* 라이브러리를 사용 합니다. 이 라이브러리는 NuGet 패키지로 무료로 제공 됩니다. 이와 유사한 Api에 대 한 자세한 내용은 [api 참조 문서를 참조](/azure/cognitive-services/face/apireference)하세요.

> [!NOTE] 
> 이러한 작업을 수행 하는 방법에 대 한 지침은 필요한 단계에 불과합니다. 이러한 작업을 수행 하는 방법은 문서에 나와 있습니다. **Person Maker** 앱을 통해 다음을 수행할 수 있습니다.
>
> - 연결할 여러 사람으로 구성된 그룹인 *Person* Group 을 만듭니다. Azure 계정을 사용하면 여러 개인 그룹을 호스트할 수 있습니다.
>
> - *Person* 그룹의 구성원인 Person 을 만듭니다. 각 사람에게는 연결된 여러 *Face* 이미지가 있습니다.
>
> -  *사람* 에 *얼굴 이미지를* 할당하여 Azure Face API 서비스에서 해당 *얼굴* 로 *사람을* 인식할 수 있도록 합니다.
>
> -  Azure *Face API 서비스를* *학습합니다.*

이 앱을 학습하여 사람을 인식하려면 개인 그룹에 추가하려는 각 사람의 10개(10개) 클로즈업 사진이 필요합니다. Windows 10 Cam 앱은 이러한 앱을 이용하는 데 도움이 될 수 있습니다. 이미지 파일 크기가 **4MB** 이하이며 **1KB** 이하인 jpg 또는 png 파일 형식으로 사진을 갖도록 각 사진이 명확해야 합니다(흐리거나, 모호하거나, 제목에서 너무 멀리 있지 않도록 방지).

> [!NOTE]
> 이 자습서를 수행하는 경우 HoloLens 배치할 때처럼 자신의 얼굴을 학습에 사용하지 마십시오. 동료 또는 동료 학생의 얼굴을 사용합니다.

**Person Maker** 실행:

1.  **PersonMaker** 폴더를 열고 *PersonMaker 솔루션을* 두 번 클릭하여 *Visual Studio.*

2.  *PersonMaker 솔루션이* 열리면 다음을 확인합니다.

    1. *솔루션 구성이* **디버그** 로 설정됩니다.

    2. *솔루션 플랫폼이* **x86으로** 설정됩니다.

    3. *대상 플랫폼은* **로컬 컴퓨터** 입니다.

    4.  *NuGet 패키지를 복원해야* 할 수도 있습니다(솔루션을 마우스  오른쪽 단추로 클릭하고 NuGet **패키지 복원** 선택).

3.  *로컬 컴퓨터를* 클릭하면 애플리케이션이 시작됩니다. 작은 화면에서는 더 아래로 스크롤하여 볼 수 있지만 모든 콘텐츠가 표시되지 않을 수 있습니다.

    ![person maker 사용자 인터페이스](images/AzureLabs-Lab4-07.png)

4.  Azure 내 *Face API* 서비스에서 있어야 하는 Azure **인증 키를** 삽입합니다.

5.  삽입:

    1. 개인 그룹 에 할당할 *ID입니다.*  ID는 공백 없이 소문자여야 합니다. 이 ID는 나중에 Unity 프로젝트에서 필요하기 때문에 기록해 둡다.
    2. *개인 그룹에* 할당할 이름입니다(공백이 있을 수 있습니다). 


6.  **사람 그룹 만들기** 단추를 누릅니다. 확인 메시지가 단추 아래에 나타납니다.

> [!NOTE]
> '액세스 거부' 오류가 있는 경우 Azure 서비스에 대해 설정한 위치를 확인합니다. 위에서 언급했듯이 이 앱은 '미국 서부'를 위해 설계되었습니다.

> [!IMPORTANT]
> **알려진 그룹 가져오기** 단추를 클릭할 수도 있습니다. 이는 이미 개인 그룹을 만들고 새 그룹을 만드는 대신 사용하려는 경우에 해당합니다. 알려진 그룹이 있는 *사람 그룹 만들기를* 클릭하면 그룹도 페치됩니다.

7.  만들려는 *사람의* *이름을* 삽입합니다.

    1. 사람 **만들기** 단추를 클릭합니다.

    2. 확인 메시지가 단추 아래에 나타납니다.

    3. 이전에 만든 사람을 삭제하려면 텍스트 상자에 이름을 쓰고 **사람 삭제를** 누릅니다.

8.  그룹에 추가하려는 사람의 사진 10개(10개)의 위치를 알고 있는지 확인합니다.

9.  **폴더 만들기 및 열기를** 눌러 개인과 연결된 폴더에 대한 Windows 탐색기를 엽니다. 폴더에 10개의 이미지를 추가합니다. *JPG* 또는 *PNG* 파일 형식이어야 합니다.

10. **Azure에 제출을** 클릭합니다. 카운터는 제출 상태를 표시한 다음 완료 시 메시지가 표시됩니다.

11. 카운터가 완료되고 확인 메시지가 표시되면 **학습을** 클릭하여 서비스를 학습합니다.

프로세스가 완료되면 Unity로 이동할 준비가 된 것입니다.

## <a name="chapter-3---set-up-the-unity-project"></a>3장 - Unity 프로젝트 설정

다음은 혼합 현실로 개발하기 위한 일반적인 설정이며, 따라서 다른 프로젝트에 적합한 템플릿입니다.

1.  *Unity를* 열고 **새로** 만들기를 클릭합니다. 

    ![새 Unity 프로젝트를 시작합니다.](images/AzureLabs-Lab4-08.png)

2.  이제 Unity Project 이름을 제공해야 합니다. **MR_FaceRecognition** 삽입합니다. 프로젝트 형식이 **3D 로** 설정되어 있는지 확인합니다. **위치를** 적절한 위치로 설정합니다(루트 디렉터리에 가까울수록 좋습니다). 그런 다음 **프로젝트 만들기를** 클릭합니다.

    ![새 Unity 프로젝트에 대한 세부 정보를 제공합니다.](images/AzureLabs-Lab4-09.png)

3.  Unity가 열려 있는 경우 기본 **스크립트 편집기가** **Visual Studio** 로 설정되어 있는지 확인하는 것이 좋습니다. 편집 **> 기본 설정으로** 이동한 다음 새 창에서 **외부 도구** 로 이동합니다. **외부 스크립트 편집기를** **Visual Studio 2017로** 변경합니다. 기본 **설정** 창을 닫습니다.

    ![스크립트 편집기 기본 설정을 업데이트합니다.](images/AzureLabs-Lab4-10.png)

4.  다음으로, **파일 > 빌드 설정** 이동하여 플랫폼 전환 단추를 클릭하여 플랫폼을 유니버설 Windows **플랫폼으로 전환합니다.** 

    ![설정 창을 빌드하고 플랫폼을 UWP로 전환합니다.](images/AzureLabs-Lab4-11.png)

5.  파일 **> 빌드 설정** 이동하여 다음을 확인합니다.

    1. **대상 디바이스가** **HoloLens**

        > 몰입형 헤드셋의 경우 **대상 디바이스를** *모든 디바이스로* 설정합니다.

    2. **빌드 유형이** **D3D로** 설정됩니다.
    3. **SDK가** **최신 설치로 설정됩니다.**
    4. **Visual Studio 버전이** 최신 **설치로 설정됩니다.**
    5. **빌드 및 실행이** **로컬 컴퓨터로 설정됩니다.**
    6. 장면을 저장하고 빌드에 추가합니다. 

        1. 열린 장면 추가 를 선택하여 이 작업을 **수행합니다.** 저장 창이 나타납니다.

            ![열린 장면 추가 단추를 클릭합니다.](images/AzureLabs-Lab4-12.png)

        2. 새 **폴더** 단추를 선택하여 새 폴더를 만들고 이름을 **Scenes로** 지정합니다.

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab4-13.png)

        3. 새로 만든 **Scenes** 폴더를 열고 **파일 이름:** 텍스트 필드에 **FaceRecScene을** 입력한 **다음, 저장을** 누릅니다.

            ![새 장면에 이름을 지정합니다.](images/AzureLabs-Lab4-14.png)

    7. *빌드 설정* 나머지 설정은 현재 기본값으로 유지되어야 합니다.

6. 빌드 *설정* 창에서 **플레이어 설정** 단추를 클릭하면 *Inspector가* 있는 공간에서 관련 패널이 열립니다. 

    ![플레이어 설정을 엽니다.](images/AzureLabs-Lab4-15.png)

7. 이 패널에서 몇 가지 설정을 확인해야 합니다.

    1. 기타 **설정** 탭에서 다음을 수행합니다.

        1. **런타임** **스크립팅** 버전은 **실험적** 버전이어야 합니다(.NET 4.6 동등). 이렇게 변경하면 편집기를 다시 시작해야 합니다.
        2. **스크립팅 백 엔드는** **.NET이어야 합니다.**
        3. **API 호환성 수준은** **.NET 4.6이어야** 합니다.

            ![다른 설정을 업데이트합니다.](images/AzureLabs-Lab4-16.png)
      
    2. 게시 **설정** 탭의 기능 아래에서 **다음을 확인합니다.**

        - **InternetClient**
        - **웹캠**

            ![게시 설정 업데이트](images/AzureLabs-Lab4-17.png)

    3. 패널의 아래쪽에 있는 **XR 설정(게시 설정** 아래에 **있음)에서** 가상 **현실 지원됨을** 틱하여 **Windows Mixed Reality SDK가** 추가되었는지 확인합니다.

        ![X R 설정 업데이트합니다.](images/AzureLabs-Lab4-18.png)

8.  빌드 *설정* Unity **C# 프로젝트는** 더 이상 회색으로 표시됩니다. 이 옆에 있는 확인란을 선택합니다. 
9.  빌드 설정 창을 닫습니다.
10. 장면을 저장하고 Project(**FILE > SAVE SCENE / FILE > SAVE PROJECT**).

## <a name="chapter-4---main-camera-setup"></a>4장 - 기본 카메라 설정

> [!IMPORTANT]
> 이 과정의 Unity *설정* 구성 요소를 건너뛰고 코드를 계속 진행하려면 [이 .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)를 다운로드하고 사용자 [지정 패키지](https://docs.unity3d.com/Manual/AssetPackages.html)로 프로젝트에 가져올 수 있습니다. 이 패키지에는 [5장에서](#chapter-5--import-the-newtonsoftjson-library)다루는 *Newtonsoft DLL* 가져오기도 포함되어 있습니다. 이를 가져온 후에는 [6 장](#chapter-6---create-the-faceanalysis-class)에서 계속할 수 있습니다.

1.  *계층* 패널에서 **기본 카메라** 를 선택 합니다.

2.  선택한 후에는 *검사기 패널* 에서 **주 카메라** 의 모든 구성 요소를 볼 수 있습니다.

    1. **카메라 개체** 의 이름을 **주 카메라로** 지정 해야 합니다 (철자 확인).

    2. 기본 카메라 **태그** 는 **maincamera** 로 설정 되어야 합니다 (철자 확인).

    3. **변환 위치가** **0, 0, 0** 으로 설정 되어 있는지 확인 합니다.

    4. **Clear 플래그** 를 **Solid 색** 으로 설정

    5. 카메라 구성 요소의 **배경색** 을 **검은색, 알파 0 (16 진수 코드: #00000000)** 으로 설정 합니다.

        ![카메라 구성 요소 설정](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>5 장-라이브러리에서 Newtonsoft.Js가져오기

> [!IMPORTANT]
> [마지막 챕터](#chapter-4---main-camera-setup)에서 '. unitypackage '를 가져온 경우이 챕터를 건너뛸 수 있습니다.

받아서 봇 서비스로 전송 되는 개체를 deserialize 하 고 serialize 할 수 있도록 라이브러리 *에Newtonsoft.Js* 를 다운로드 해야 합니다. 이 [unity 패키지 파일](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)에서 올바른 unity 폴더 구조를 사용 하 여 이미 구성 된 호환 버전을 찾을 수 있습니다. 

라이브러리를 가져오려면:

1.  Unity 패키지를 다운로드 합니다.
2.  **자산**, **패키지 가져오기**, **사용자 지정 패키지** 를 클릭 합니다.

    ![Newtonsoft.Js가져오기](images/AzureLabs-Lab4-20.png)

3.  다운로드 한 Unity 패키지를 찾고 열기를 클릭 합니다.
4.  패키지의 모든 구성 요소가 선택 인지 확인 하 고 **가져오기** 를 클릭 합니다.

    ![자산에 대 한 Newtonsoft.Js가져오기](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>6 장-FaceAnalysis 클래스 만들기

FaceAnalysis 클래스의 목적은 Azure 얼굴 인식 서비스와 통신 하는 데 필요한 메서드를 호스트 하는 것입니다. 

- 서비스를 캡처한 후 캡처 이미지는 분석 하 고 내 얼굴을 식별 하며 알려진 사람에 게 속해 있는지 확인 합니다. 
- 알려진 사용자가 있는 경우이 클래스는 해당 이름을 장면에 UI 텍스트로 표시 합니다.

*FaceAnalysis* 클래스를 만들려면:

 1. Project 패널에 있는 *자산 폴더* 를 마우스 오른쪽 단추로 클릭 한 다음 폴더 **만들기** 를 클릭  >  합니다. 폴더 **스크립트** 를 호출 합니다. 

    ![FaceAnalysis 클래스를 만듭니다.](images/AzureLabs-Lab4-22.png)

2.  위에서 만든 폴더를 두 번 클릭 하 여 엽니다. 
3.  폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음   >  **c # 스크립트** 만들기를 클릭 합니다. *FaceAnalysis* 스크립트를 호출 합니다. 
4.  새 *FaceAnalysis* 스크립트를 두 번 클릭 하 Visual Studio 2017를 사용 하 여 엽니다.
5.  *FaceAnalysis* 클래스 위에 다음 네임 스페이스를 입력 합니다.

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  이제 deserialising에 사용 되는 모든 개체를 추가 해야 합니다. 이러한 개체는 *FaceAnalysis* 스크립트 (아래쪽 중괄호 아래) **외부** 에 추가 해야 합니다. 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. *Start ()* 및 *Update ()* 메서드는 사용 되지 않으므로 지금 삭제 합니다. 

8.  *FaceAnalysis* 클래스 내에서 다음 변수를 추가 합니다.

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > **키** 와 **personGroupId** 을 이전에 만든 그룹의 서비스 키와 Id로 바꿉니다.

9.  Initialises *()* 메서드를 추가 합니다 .이 메서드는 클래스를 기본 카메라에 *ImageCapture* 클래스를 추가 하 고 레이블 생성 메서드를 호출 합니다.

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. *CreateLabel ()* 메서드를 추가 합니다 .이 메서드는 분석 결과를 표시 하는 *레이블* 개체를 만듭니다.

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. *DetectFacesFromImage ()* 및 *GetImageAsByteArray ()* 메서드를 추가 합니다. 이전에는 얼굴 인식 서비스를 요청 하 여 제출 된 이미지에서 가능한 얼굴을 검색 하 고, 후자는 캡처된 이미지를 바이트 배열로 변환 하는 데 필요 합니다.

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. *IdentifyFaces ()* 메서드를 추가 합니다 .이 메서드는 전송 된 이미지에서 이전에 검색 된 알려진 얼굴을 식별 하도록 *얼굴 인식 서비스* 에 요청 합니다. 요청은 이름이 아니라 식별 된 사람의 id를 반환 합니다.

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialize to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. *Getperson ()* 메서드를 추가 합니다. 이 메서드는 개인 id를 제공 하 여 식별 된 사람의 이름을 반환 하도록 *얼굴 인식 서비스* 에 요청 합니다.

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  Unity 편집기로 다시 이동 하기 전에 변경 내용을 **저장** 해야 합니다.
15.  Unity 편집기에서 Project 패널의 Scripts 폴더에 있는 FaceAnalysis 스크립트를 *계층 패널* 의 기본 카메라 개체로 끌어 옵니다. 새 스크립트 구성 요소가 기본 카메라에 추가 됩니다. 

![기본 카메라에 FaceAnalysis 두기](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>7 장-ImageCapture 클래스 만들기

*ImageCapture* 클래스의 목적은 *Azure 얼굴 인식 서비스* 와 통신 하는 데 필요한 메서드를 호스트 하 여 캡처할 이미지를 분석 하 고, 얼굴을 식별 하 고, 알려진 사람에 게 속하는지 확인 하는 것입니다. 알려진 사용자가 있는 경우이 클래스는 해당 이름을 장면에 UI 텍스트로 표시 합니다.

*ImageCapture* 클래스를 만들려면:
 
1.  이전에 만든 **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음, **만들기**, **c # 스크립트** 를 클릭 합니다. *ImageCapture* 스크립트를 호출 합니다. 
2.  새 *ImageCapture* 스크립트를 두 번 클릭 하 Visual Studio 2017를 사용 하 여 엽니다.
3.  ImageCapture 클래스 위에 다음 네임 스페이스를 입력 합니다.

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  *ImageCapture* 클래스 내에서 다음 변수를 추가 합니다.

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  클래스를 초기화 하는 데 필요한 *()* 및 *Start ()* 메서드를 추가 하 고 HoloLens 사용자의 제스처를 캡처할 수 있도록 허용 합니다.

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  사용자가 *탭* 제스처를 수행할 때 호출 되는 *TapHandler ()* 를 추가 합니다.

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  *ExecuteImageCaptureAndAnalysis ()* 메서드를 추가 합니다 .이 메서드는 이미지 캡처 프로세스를 시작 합니다.

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  사진 캡처 프로세스가 완료 되 면 호출 되는 처리기를 추가 합니다.

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. Unity 편집기로 다시 이동 하기 전에 변경 내용을 **저장** 해야 합니다.

## <a name="chapter-8---building-the-solution"></a>8 장-솔루션 빌드

응용 프로그램에 대 한 철저 한 테스트를 수행 하려면 HoloLens에 테스트용으로 로드 해야 합니다.

이렇게 하려면 먼저 다음을 확인 해야 합니다.

-   3 장에서 설명한 모든 설정이 올바르게 설정 됩니다. 
-   *FaceAnalysis* 스크립트는 주 카메라 개체에 연결 됩니다. 
-   *FaceAnalysis* 스크립트 내에서 **인증 키** 와 **그룹 Id** 가 모두 설정 되었습니다.

이 시점에서 솔루션을 빌드할 준비가 되었습니다. 솔루션이 구축 되 면 응용 프로그램을 배포할 준비가 됩니다.

빌드 프로세스를 시작 하려면 다음을 수행 합니다.

1.  파일, 저장을 차례로 클릭 하 여 현재 장면을 저장 합니다.
2.  파일, 빌드 설정로 이동 하 여 열려 있는 장면 추가를 클릭 합니다.
3.  Tick Unity c # 프로젝트를 확인 합니다.

    ![Visual Studio 솔루션 배포](images/AzureLabs-Lab4-24.png)

4.  빌드를 누릅니다. 이 작업을 수행 하면 Unity는 파일 탐색기 창을 시작 합니다. 여기에서 앱을 빌드할 폴더를 만들고 선택 해야 합니다. 이제 Unity 프로젝트 내에서 해당 폴더를 만들고 it 앱을 호출 합니다. 그런 다음 앱 폴더를 선택 하 고 폴더 선택을 누릅니다. 
5.  Unity는 응용 프로그램 폴더에서 프로젝트 빌드를 시작 합니다. 
6.  Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 파일 탐색기 창이 열립니다.

    ![Visual Studio에서 솔루션 배포](images/AzureLabs-Lab4-25.png)

7.  앱 폴더를 연 다음, MR_FaceRecognition 위에 표시 된 대로 새 Project 솔루션을 엽니다.


## <a name="chapter-9---deploying-your-application"></a>9 장-응용 프로그램 배포

HoloLens에 배포 하려면:

1.  HoloLens의 IP 주소가 필요 하며 (원격 배포의 경우) HoloLens **개발자 모드** 에 있는지 확인 해야 합니다. 이렇게 하려면 다음을 수행합니다.

    1. HoloLens를 입고 **설정** 를 엽니다.
    2. **네트워크 & 인터넷 > Wi-Fi > 고급 옵션** 으로 이동 합니다.
    3. **IPv4** 주소를 적어둡니다.
    4. 그런 다음 **설정** 으로 다시 이동한 다음 **개발자를 위한 & Security >를 업데이트** 합니다. 
    5. 에서 개발자 모드를 설정 합니다.

2.  새 Unity 빌드 ( *앱* 폴더)로 이동 하 고 *Visual Studio* 를 사용 하 여 솔루션 파일을 엽니다.
3.  솔루션 구성에서 **디버그** 를 선택 합니다.
4.  솔루션 플랫폼에서 **x86**, **원격 컴퓨터** 를 선택 합니다. 

    ![솔루션 구성 변경](images/AzureLabs-Lab4-26.png)
 
5.  **빌드 메뉴로** 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 HoloLens으로 테스트용으로 로드.
6.  이제 앱이 HoloLens에 설치 된 앱 목록에 표시 되 고, 시작할 준비가 되었습니다!

> [!NOTE]
> 모던 헤드셋에 배포 하려면 **솔루션 플랫폼** 을 *로컬 컴퓨터* 로 설정 하 고 **구성을** *디버그* 로 설정 하 고 *x 86* 을 **플랫폼** 으로 설정 합니다. 그런 다음 **빌드 메뉴** 를 사용 하 여 *솔루션 배포* 를 선택 하 여 로컬 컴퓨터에 배포 합니다. 


## <a name="chapter-10---using-the-application"></a>10 장-응용 프로그램 사용

1.  HoloLens를 입고 앱을 시작 합니다.
2.  *Face API* 등록 한 사용자를 확인 합니다. 확인할 사항은 다음과 같습니다.

    -  개인의 얼굴이 너무 멀리 떨어져 있으며 명확 하 게 표시 됩니다.
    -  환경 조명이 너무 어두움

3.  탭 제스처를 사용 하 여 사용자의 사진을 캡처합니다.
4.  앱이 분석 요청을 보내고 응답을 받을 때까지 기다립니다.
5.  사용자가 성공적으로 인식 되 면 사용자 이름이 UI 텍스트로 표시 됩니다.
6.  몇 초 마다 탭 제스처를 사용 하 여 캡처 프로세스를 반복할 수 있습니다.

## <a name="your-finished-azure-face-api-application"></a>완성 된 Azure Face API 응용 프로그램

축 하 합니다. Azure 얼굴 인식 서비스를 활용 하 여 이미지 내 얼굴을 감지 하 고 알려진 얼굴을 식별 하는 혼합 현실 앱을 빌드 했습니다.

![이 과정을 완료 한 결과](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

**Azure Face API** 는 단일 이미지에서 최대 64 얼굴을 검색할 수 있을 만큼 강력 합니다. 응용 프로그램을 확장 하 여 두 개 또는 세 개의 얼굴을 인식할 수 있도록 합니다.

### <a name="exercise-2"></a>연습 2

또한 **Azure Face API** 는 모든 종류의 특성 정보를 다시 제공할 수 있습니다. 응용 프로그램에이를 통합 합니다. 이는 [Emotion API](https://azure.microsoft.com/services/cognitive-services/emotion/)와 결합 될 때 훨씬 더 흥미롭습니다.