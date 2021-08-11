---
title: HoloLens(1세대) 및 Azure 302 - 컴퓨터 비전
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램에서 Azure Computer Vision를 사용 하 여 제공 된 이미지 내의 시각적 콘텐츠를 인식 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 컴퓨터 비전, hololens, 모던, vr, Windows 10, Visual Studio
ms.openlocfilehash: 5cac40c2613187776ea9ec5ba1268f1422a084d32322e9c4aca6742ed75d05b2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226040"
---
# <a name="hololens-1st-gen-and-azure-302-computer-vision"></a>HoloLens (첫 번째 gen) 및 Azure 302: 컴퓨터 비전

<br>

>[!NOTE]
>Mixed Reality 아카데미 자습서는 HoloLens(1세대) 및 Mixed Reality 몰입형 헤드셋을 염두에 두고 설계되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다.  이러한 자습서는 HoloLens 2에 사용되는 최신 도구 집합 또는 상호 작용으로 업데이트되지 **_않습니다_**.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2를 개발 하는 방법을 설명 하는 앞으로 게시 될 새 자습서가 있습니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

이 과정에서는 혼합 현실 응용 프로그램에서 Azure Computer Vision 기능을 사용 하 여 제공 된 이미지 내의 시각적 콘텐츠를 인식 하는 방법을 알아봅니다.

인식 결과는 설명 태그로 표시 됩니다. Machine learning 모델을 학습 하지 않고도이 서비스를 사용할 수 있습니다. 구현에서 기계 학습 모델을 학습 해야 하는 경우 [MR 및 Azure 302b](mr-azure-302b.md)를 참조 하세요.

![랩 결과](images/AzureLabs-Lab2-000.png)

Microsoft Computer Vision는 개발자에 게 모든 클라우드에서 고급 알고리즘을 사용 하 여 이미지 처리 및 분석 (반환 정보 포함)을 제공 하도록 설계 된 Api 집합입니다. 개발자는 이미지 또는 이미지 URL을 업로드 하 고 Microsoft Computer Vision API 알고리즘은 사용자가 선택한 입력을 기준으로 시각적 콘텐츠를 분석 하 여 이미지의 유형 및 품질 식별, 사용자 얼굴 감지 (좌표 반환), 이미지 태그 지정, 이미지 분류 등의 정보를 반환할 수 있습니다. 자세한 내용은 [Azure Computer Vision API 페이지](https://azure.microsoft.com/services/cognitive-services/computer-vision/)를 참조 하세요.

이 과정을 완료 하면 다음과 같은 작업을 수행할 수 있는 혼합 현실 HoloLens 응용 프로그램이 만들어집니다.

1.  탭 제스처를 사용 하면 HoloLens 카메라가 이미지를 캡처합니다.
2.  이미지가 Azure Computer Vision API 서비스로 전송 됩니다. 
3.  인식 된 개체는 Unity 장면에 배치 된 간단한 UI 그룹에 나열 됩니다.

응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다. 이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다. 이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 302: Computer Vision</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정에서 주로 HoloLens에 중점을 둔 반면이 과정에서 학습 하는 내용을 Windows Mixed Reality 모던 (VR) 헤드셋에도 적용할 수 있습니다. 모던 (VR) 헤드셋은 액세스할 수 있는 카메라를 포함 하지 않으므로 PC에 연결 된 외부 카메라가 필요 합니다. 이 과정을 진행 하면서 모던 (VR) 헤드셋을 지원 하기 위해 사용 해야 하는 변경 내용에 대 한 정보를 볼 수 있습니다.

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
- PC에 연결 된 카메라 (몰입 형 헤드셋 개발용)
- Azure 설정 및 Computer Vision API 검색을 위한 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전에

1.  이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)
2.  HoloLens를 설정 하 고 테스트 합니다. HoloLens 설정에 대 한 지원이 필요한 경우 [HoloLens 설치 문서를 방문 해야](/hololens/hololens-setup)합니다. 
3.  새 HoloLens 앱 개발을 시작할 때 보정 및 센서 조정을 수행 하는 것이 좋습니다 (경우에 따라 각 사용자에 대해 해당 작업을 수행 하는 데 도움이 될 수 있음). 

보정에 대 한 도움말을 보려면 [HoloLens 보정 문서에 대 한 링크를](/hololens/hololens-calibration#hololens-2)참조 하세요.

센서 조정에 대 한 도움말을 보려면 [HoloLens 센서 조정 문서에 대 한 링크를](/hololens/hololens-updates)참조 하세요.

## <a name="chapter-1--the-azure-portal"></a>1 장-Azure Portal

Azure에서 *Computer Vision API* 서비스를 사용 하려면 응용 프로그램에서 사용할 수 있도록 서비스 인스턴스를 구성 해야 합니다.

1.  먼저 [Azure Portal](https://portal.azure.com)에 로그인 합니다. 

    > [!NOTE]
    > 아직 Azure 계정이 없는 경우 새로 만들어야 합니다. 교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.

2.  로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 *Computer Vision API* 를 검색 한 다음 **Enter 키** 를 누릅니다.

    ![Azure에서 새 리소스 만들기](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > 새 단어는 **새** 포털에서 **리소스 만들기** 로 대체 되었을 수 있습니다.
 
3.  새 페이지에 *Computer Vision API* 서비스에 대 한 설명이 제공 됩니다. 이 페이지의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.

    ![컴퓨터 비전 api 서비스 정보](images/AzureLabs-Lab2-01.png)
 
4.  **만들기** 를 클릭 하면 다음을 클릭 합니다.

    1. 이 서비스 인스턴스의 원하는 **이름을** 삽입 합니다.
    2. **구독** 을 선택합니다.
    3. 적절 한 **가격 책정 계층** 을 선택 합니다. *Computer Vision API* 서비스를 처음 만드는 경우 무료 계층 (명명 된 F0)을 사용할 수 있어야 합니다.
    4. 리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다. 리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다. 

        > Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](/azure/azure-resource-manager/resource-group-portal)하세요.

    5. 새 리소스 그룹을 만드는 경우 리소스 그룹의 위치를 확인 합니다. 위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다. 일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.

    6. 또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.
    7. 만들기를 클릭합니다.

        ![서비스 생성 정보](images/AzureLabs-Lab2-02.png)

5.  **만들기** 를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.
6.  서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.

    ![새 서비스에 대 한 새 알림 확인](images/AzureLabs-Lab2-03.png) 
 
7.  알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다. 

    ![리소스로 이동 단추를 선택 합니다.](images/AzureLabs-Lab2-04.png)
 
8. 알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다. 새 Computer Vision API 서비스 인스턴스로 이동 됩니다. 

    ![새 Computer Vision API 서비스 이미지](images/AzureLabs-Lab2-05.png)
 
9.  이 자습서에서 응용 프로그램은 서비스에 대 한 호출을 수행 해야 하며, 서비스의 구독 키를 사용 하 여 수행 됩니다.
10. *Computer Vision API* 서비스의 *빠른 시작* 페이지에서 첫 번째 단계로 이동 하 고 키를 클릭 한 다음 *키를 클릭* 합니다. 서비스 탐색 메뉴에서 키 아이콘으로 표시 되는 파란색 하이퍼링크 키 **를 클릭 하** 여이를 수행할 수도 있습니다. 이렇게 하면 서비스 *키* 가 표시 됩니다.
11. 프로젝트에서 나중에 필요 하므로 표시 된 키 중 하나를 복사 합니다. 

12. *빠른 시작* 페이지로 돌아가 여기에서 끝점을 인출 합니다. 사용자는 지역에 따라 다를 수 있습니다 (이 경우 나중에 코드를 변경 해야 하는 경우). 나중에 사용 하기 위해이 끝점의 복사본을 가져옵니다.

    ![새 Computer Vision API 서비스](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > 다양 한 끝점이 [여기](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)에 있는지 확인할 수 있습니다. 

## <a name="chapter-2--set-up-the-unity-project"></a>2 장-Unity 프로젝트 설정

다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.

1.  *Unity* 를 열고 **새로 만들기** 를 클릭 합니다. 

    ![새 Unity 프로젝트를 시작합니다.](images/AzureLabs-Lab2-06.png)

2.  이제 Unity Project 이름을 제공해야 합니다. **MR_ComputerVision** 삽입합니다. 프로젝트 형식이 **3D 로** 설정되어 있는지 확인합니다. **위치를** 적절한 위치로 설정합니다(루트 디렉터리에 가까울수록 좋습니다). 그런 다음 **프로젝트 만들기를** 클릭합니다.

    ![새 Unity 프로젝트에 대한 세부 정보를 제공합니다.](images/AzureLabs-Lab2-07.png)

3.  Unity가 열려 있는 경우 기본 **스크립트 편집기가** **Visual Studio** 로 설정되어 있는지 확인하는 것이 좋습니다. 편집 **> 기본 설정으로** 이동한 다음 새 창에서 **외부 도구** 로 이동합니다. **외부 스크립트 편집기를** **Visual Studio 2017로** 변경합니다. 기본 **설정** 창을 닫습니다.

    ![스크립트 편집기 기본 설정을 업데이트합니다.](images/AzureLabs-Lab2-08.png)

4.  다음으로 **파일 > 빌드 설정** 이동하여 유니버설 **Windows 플랫폼을** 선택한 **다음, 플랫폼 전환** 단추를 클릭하여 선택 항목을 적용합니다.

    ![설정 창을 빌드하고 플랫폼을 UWP로 전환합니다.](images/AzureLabs-Lab2-10.png)

5.  파일 > 있는 동안 **설정 빌드하고** 다음을 확인합니다.

    1. **대상 디바이스가** **HoloLens**

        > 몰입형 헤드셋의 경우 **대상 디바이스를** *모든 디바이스로* 설정합니다.

    2. **빌드 유형이** **D3D로** 설정됩니다.
    3. **SDK가** **최신 설치로 설정됩니다.**
    4. **Visual Studio 버전이** 최신 **설치로 설정됩니다.**
    5. **빌드 및 실행이** **로컬 컴퓨터로 설정됩니다.**
    6. 장면을 저장하고 빌드에 추가합니다.

        1. 열린 장면 추가 를 선택하여 이 작업을 **수행합니다.** 저장 창이 나타납니다.
        
            ![열린 장면 추가 단추를 클릭합니다.](images/AzureLabs-Lab2-11.png)

        2. 이에 대한 새 폴더 및 이후의 장면을 만든 다음, 새 폴더 단추를 선택하여 새 **폴더를** 만들고 이름을 **Scenes로** 지정합니다.

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab2-12.png)

        3. 새로 만든 **Scenes** 폴더를 열고 *파일 이름*: 텍스트 필드에 **MR_ComputerVisionScene** 입력한 **다음, 저장을** 클릭합니다.

            ![새 장면에 이름을 지정합니다.](images/AzureLabs-Lab2-13.png)

            > Unity 장면은 Unity Project 연결되어야 하며 *자산* 폴더 내에 저장해야 합니다. Scenes 폴더(및 기타 유사한 폴더)를 만드는 것은 Unity 프로젝트를 구성하는 일반적인 방법입니다.

    7. *빌드 설정* 나머지 설정은 현재 기본값으로 유지되어야 합니다.

6. 빌드 *설정* 창에서 **플레이어 설정** 단추를 클릭하면 *Inspector가* 있는 공간에서 관련 패널이 열립니다. 

    ![플레이어 설정을 엽니다.](images/AzureLabs-Lab2-14.png)

7. 이 패널에서 몇 가지 설정을 확인해야 합니다.

    1. 기타 **설정** 탭에서 다음을 수행합니다.

        1. **스크립팅 런타임 버전은** **안정적이어야** 합니다(.NET 3.5 동급).
        2. **스크립팅 백 엔드는** **.NET이어야 합니다.**
        3. **API 호환성 수준은** **.NET 4.6이어야** 합니다.

            ![다른 설정을 업데이트합니다.](images/AzureLabs-Lab2-15.png)
      
    2. 게시 **설정** 탭의 기능 아래에서 **다음을 확인합니다.**

        1. **InternetClient**
        2. **웹캠**

            ![게시 설정 업데이트](images/AzureLabs-Lab2-16.png)

    3. 패널의 아래쪽에 있는 **XR 설정(게시 설정** 아래에 **있음)에서** 가상 **현실 지원됨을** 틱하여 **Windows Mixed Reality SDK가** 추가되었는지 확인합니다.

        ![X R 설정 업데이트합니다.](images/AzureLabs-Lab2-17.png)

8.  빌드 *설정* _Unity C#_ 프로젝트로 돌아가면 더 이상 회색으로 표시됩니다. 이 옆에 있는 확인란을 선택합니다. 
9.  빌드 설정 창을 닫습니다.
10. 장면을 저장하고 Project(**FILE > SAVE SCENE / FILE > SAVE PROJECT**).

## <a name="chapter-3--main-camera-setup"></a>3장 - 기본 카메라 설정

> [!IMPORTANT]
> 이 과정의 Unity *설정* 구성 요소를 건너뛰고 코드를 계속 진행하려면 이 [.unitypackage를](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)다운로드하고, 프로젝트에 [사용자 지정 패키지](https://docs.unity3d.com/Manual/AssetPackages.html)로 가져온 다음, [5장](#chapter-5--create-the-resultslabel-class)에서 계속 진행하세요.

1.  계층 *구조 패널에서* **주 카메라** 를 선택합니다. 
2.  이 옵션을 선택하면 *검사기 패널* 에서 **주 카메라의** 모든 구성 요소를 볼 수 있습니다.

    1. **Camera 개체의** 이름은 Main Camera(맞춤법)로 지정해야 합니다. 
    2. Main Camera **태그는** **MainCamera로** 설정해야 합니다(맞춤법 유의하세요!).
    3. **변환 위치가** **0, 0, 0으로** 설정되어 있는지 확인합니다.
    4. **플래그 지우기를** **단색으로** 설정합니다(몰입형 헤드셋의 경우 무시).
    5. 카메라 구성 요소의 **배경색을** **검은색, 알파 0(16진수 코드: #00000000)으로** 설정합니다(몰입형 헤드셋의 경우 무시).

        ![카메라 구성 요소를 업데이트합니다.](images/AzureLabs-Lab2-18.png)
 
3.  다음으로, **주 카메라** 에 연결된 간단한 "Cursor" 개체를 만들어야 합니다. 이 개체를 사용하면 애플리케이션이 실행 중일 때 이미지 분석 출력을 배치할 수 있습니다. 이 커서는 카메라 포커스의 중심점을 결정합니다.

커서를 만들려면 다음을 수행합니다.

1.  계층 *구조 패널에서* **주 카메라를** 마우스 오른쪽 단추로 클릭합니다. **3D 개체** 아래에서 **Sphere 를** 클릭합니다.

    ![커서 개체를 선택합니다.](images/AzureLabs-Lab2-19.png)
 
2.  **구의** 이름을 **커서로** 바꾸고(커서 개체를 두 번 클릭하거나 개체가 선택된 'F2' 키보드 단추를 누름) **주 카메라** 의 자식으로 있는지 확인합니다.

3.  계층 *구조 패널에서* **커서** 를 마우스 왼쪽 단추로 클릭합니다. 커서를 선택한 후 *검사기 패널* 에서 다음 변수를 조정합니다.

    1. 변환 *위치를* **0, 0, 5로** 설정합니다.
    2. 크기 *조정을* **0.02, 0.02, 0.02로** 설정합니다.

        ![변환 위치 및 배율 을 업데이트합니다.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>4장 - 레이블 시스템 설정

HoloLens 카메라를 사용하여 이미지를 캡처하면 해당 이미지가 분석을 위해 Azure Computer Vision *API* Service 인스턴스로 전송됩니다. 

해당 분석의 결과는 태그라고 하는 인식된 개체의 **목록입니다.** 

레이블(세계 공간에서 3D 텍스트로)을 사용하여 사진을 찍은 위치에 이러한 태그를 표시합니다.

다음 단계에서는 **Label** 개체를 설정하는 방법을 보여 줍니다.

1.  계층 구조 패널의 아무 곳이나 마우스 오른쪽 단추로 클릭하고(현재 위치는 중요하지 않음) **3D 개체** 아래에서 **3D 텍스트를** 추가합니다. 이름을 **LabelText로 지정합니다.**

    ![3D Text 개체를 만듭니다.](images/AzureLabs-Lab2-21.png)
 
2.  계층 *구조 패널에서* **LabelText** 를 마우스 왼쪽 단추로 클릭합니다. **LabelText를** 선택한 후 *검사기 패널* 에서 다음 변수를 조정합니다.

    1. **위치를** **0,0,0으로 설정합니다.**
    2. 크기 **조정을** **0.01, 0.01, 0.01로** 설정합니다.
    3. 구성 요소 **텍스트 메시에서:**
    4. **텍스트** 내의 모든 텍스트를 "..."로 대체합니다.        
    5. **앵커를** **중간 센터로** 설정
    6. **맞춤을** **가운데로** 설정
    7. 탭 **크기를** **4로 설정합니다.**
    8. **글꼴 크기를** **50으로** 설정합니다.
    9. **색을** **#FFFFFFFF**

    ![텍스트 구성 요소](images/AzureLabs-Lab2-21-5.png)

3.  계층 패널 의 **LabelText를** *Project* *패널* 내의 *자산 폴더* 로 끌어다 붙입니다. 이렇게 하면 **LabelText가** Prefab이 되므로 코드에서 인스턴스화할 수 있습니다.

    ![LabelText 개체의 프리팹을 만듭니다.](images/AzureLabs-Lab2-22.png)
 
4.  계층 패널 에서 **LabelText를** 삭제해야 여는 장면에 표시되지 않습니다.  이제 Assets 폴더의 개별 인스턴스에 대해 를 호출하는 프리팹이기 때문에 장면 내에 유지할 필요가 없습니다. 
5.  계층 구조 *패널의* 최종 개체 구조는 아래 이미지에 표시된 구조와 같아야 합니다.

    ![계층 패널의 최종 구조입니다.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>5장 – ResultsLabel 클래스 만들기

만들어야 하는 첫 번째 스크립트는 다음을 담당하는 *ResultsLabel* 클래스입니다. 

- 카메라의 위치를 기준으로 적절 한 세계 공간에 레이블 만들기
- 이미지 분석에서 태그를 표시 합니다.

이 클래스를 만들려면: 

1.  *Project 패널* 을 마우스 오른쪽 단추로 클릭 한 다음 **> 폴더를 만듭니다**. 폴더 이름을 **스크립트** 로 합니다. 

    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab2-24.png)

2.  **Scripts** 폴더 만들기를 사용 하 여 두 번 클릭 하 여 엽니다. 그런 다음 해당 폴더 내에서를 마우스 오른쪽 단추로 클릭 하 고 **>만들기** 를 선택 하 고 **c # 스크립트** 를 선택 합니다. 스크립트 이름을 *ResultsLabel* 로 합니다. 

3.  새 *ResultsLabel* 스크립트를 두 번 클릭 하 여 **Visual Studio** 를 사용 하 여 엽니다.

4.  클래스 내에서 *ResultsLabel* 클래스에 다음 코드를 삽입 합니다.

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  *Unity* 로 반환 하기 전에 *Visual Studio* 변경 내용을 저장 해야 합니다.
7.  *Unity 편집기* 로 돌아가서 **Scripts** 폴더의 *ResultsLabel* 클래스를 클릭 하 여 *계층 패널* 의 **기본 카메라** 개체로 끕니다.
8.  **주 카메라** 를 클릭 하 고 *검사기 패널* 을 확인 합니다.

방금 카메라 안으로 끌어온 스크립트에서 **커서** 와 **레이블 Prefab** 의 두 필드가 있습니다.

9.  아래 이미지에 표시 된 것 처럼 *계층 패널* 에서 커서 라는 개체를 **커서** **라는 슬롯** 으로 끕니다.
10. 아래 이미지에 표시 된 것 처럼 *Project 패널* 의 *자산 폴더* 에서 Label **text** 라는 개체를 **Label Prefab** 이라는 슬롯으로 끕니다. 

    ![Unity 내에서 참조 대상을 설정 합니다.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>6 장 – ImageCapture 클래스 만들기

만들려는 다음 클래스는 *ImageCapture* 클래스입니다. 이 클래스는 다음을 담당 합니다.

-   HoloLens 카메라를 사용 하 여 이미지를 캡처하고 앱 폴더에 저장 합니다.
-   사용자 로부터 탭 제스처를 캡처하는 경우

이 클래스를 만들려면: 

1.  이전에 만든 **스크립트** 폴더로 이동 합니다. 
2.  폴더 내부를 마우스 오른쪽 단추로 클릭 하 **> c # 스크립트를 만듭니다**. *ImageCapture* 스크립트를 호출 합니다. 
3.  새 *ImageCapture* 스크립트를 두 번 클릭 하 여 **Visual Studio** 를 사용 하 여 엽니다.
4.  파일의 맨 위에 다음 네임 스페이스를 추가 합니다.

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  그런 다음 *ImageCapture* 클래스 내에서 *Start ()* 메서드 위의 다음 변수를 추가 합니다.

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
**TapsCount** 변수는 사용자에 게 캡처된 탭 제스처 수를 저장 합니다. 이 숫자는 캡처된 이미지의 이름을 지정 하는 데 사용 됩니다.

6.  이제 *활성 ()* 및 *Start ()* 메서드에 대 한 코드를 추가 해야 합니다. 이러한 작업은 클래스가 초기화 될 때 호출 됩니다.

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  탭 제스처가 발생할 때 호출 되는 처리기를 구현 합니다. 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
*TapHandler ()* 메서드는 사용자 로부터 캡처된 탭의 수를 늘리고 현재 커서 위치를 사용 하 여 새 레이블을 배치할 위치를 결정 합니다.

그런 다음이 메서드는 *ExecuteImageCaptureAndAnalysis ()* 메서드를 호출 하 여이 응용 프로그램의 핵심 기능을 시작 합니다.

8.  이미지를 캡처 및 저장 한 후에는 다음 처리기가 호출 됩니다. 프로세스가 성공적으로 실행 되 면 분석을 위해 결과가 아직 생성 중이 *VisionManager* 에 전달 됩니다.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  그런 다음 응용 프로그램이 이미지 캡처 프로세스를 시작 하 고 이미지를 저장 하는 데 사용 하는 메서드를 추가 합니다.

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> 이 시점에서 *Unity 편집기 콘솔 패널* 에 오류가 나타납니다. 코드는 다음 챕터에서 만들 *VisionManager* 클래스를 참조 하기 때문입니다.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>7 장 – Azure 및 이미지 분석 호출

생성 해야 하는 마지막 스크립트는 *VisionManager* 클래스입니다. 

이 클래스는 다음을 담당 합니다.

-   캡처된 최신 이미지를 바이트 배열로 로드 하 고 있습니다.
-   분석을 위해 바이트 배열을 *Azure Computer Vision API* 서비스 인스턴스로 보냅니다.
-   JSON 문자열로 응답을 수신 합니다.
-   응답을 deserialize 하 고 결과 태그를 *ResultsLabel* 클래스에 전달 합니다.
 
이 클래스를 만들려면:

1.  **스크립트** 폴더를 두 번 클릭 하 여 엽니다. 
2.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> c # 스크립트 만들기** 를 클릭 합니다. 스크립트 이름을 *VisionManager* 로 합니다. 
3.  새 스크립트를 두 번 클릭 하 여 Visual Studio를 사용 하 여 엽니다.
4.  *VisionManager* 클래스의 맨 위에서 다음과 같이 네임 스페이스를 업데이트 합니다.

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  스크립트의 맨 위에 있는 *VisionManager* 클래스 ( *Start ()* 메서드 위의)에서, 이제 AZURE에서 deserialize 된 JSON 응답을 나타내는 두 개의 *클래스* 를 *만들어야 합니다.*

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > *TagData* 및 *AnalysedObject* 클래스에는 Unity 라이브러리를 사용 하 여 deserialize 할 수 있도록 선언 앞에 *[]* 특성이 추가 되어야 합니다.

6.  VisionManager 클래스에서 다음 변수를 추가 해야 합니다.

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > **Authorizationkey** 변수에 **인증 키** 를 삽입 해야 합니다. 이 과정의 시작 부분에 [1 장](#chapter-1--the-azure-portal)에서 **인증 키** 를 기록 했습니다.

    > [!WARNING] 
    > **VisionAnalysisEndpoint** 변수는이 예제에서 지정한 것과 다를 수 있습니다. 미국 **서 부** 는 미국 서 부 지역에 대해 만든 서비스 인스턴스를 엄격히 의미 합니다. 이를 [끝점 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)로 업데이트 합니다. 다음과 같은 몇 가지 예가 있습니다.
    > - 유럽 서부: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 동남 아시아: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 오스트레일리아 동부: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  이제 절전 모드에 대 한 코드를 추가 해야 합니다. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  그런 다음 *ImageCapture* 클래스에 의해 캡처된 이미지의 분석 결과를 얻을 수 있는 코 루틴 (아래 정적 스트림 메서드 포함)를 추가 합니다. 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  *Unity* 로 반환 하기 전에 *Visual Studio* 변경 내용을 저장 해야 합니다.
10. Unity 편집기로 돌아가서 **Scripts** 폴더에서 *VisionManager* 및 *ImageCapture* 클래스를 클릭 하 여 *계층 패널* 의 **기본 카메라** 개체로 끕니다. 

## <a name="chapter-8--before-building"></a>8 장 – 빌드하기 전

응용 프로그램에 대 한 철저 한 테스트를 수행 하려면 HoloLens에 테스트용으로 로드 해야 합니다.
이렇게 하려면 먼저 다음을 확인 해야 합니다.

-   [2 장](#chapter-2--set-up-the-unity-project) 에서 설명한 모든 설정이 올바르게 설정 됩니다. 
-   모든 스크립트는 **주 카메라** 개체에 연결 됩니다. 
-   *기본 카메라 검사기 패널* 의 모든 필드가 제대로 할당 됩니다.
-   **Authorizationkey** 변수에 **인증 키** 를 삽입 해야 합니다.
-   *VisionManager* 스크립트에서 끝점을 확인 하 고 *사용자* 의 지역에 부합 하는지 확인 합니다 .이 문서에서는 기본적으로 *미국 서 부* 를 사용 합니다.

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>9 장-UWP 솔루션 빌드 및 응용 프로그램 테스트용으로 로드
이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었으므로 Unity에서 빌드할 수 있습니다.

1.  빌드 *설정* 파일로 이동 하  -  **> 빌드 설정** ...
2.  *빌드 설정* 창에서 **빌드** 를 클릭 합니다.

    ![Unity에서 앱 빌드](images/AzureLabs-Lab2-26.png)

3.  아직 없는 경우 tick **Unity c # 프로젝트** 입니다.
4.  **빌드** 를 클릭한 다음 Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 *파일 탐색기* 창을 시작 합니다. 이제 해당 폴더를 만들고 이름을 *App* 으로 만듭니다. 그런 다음 *앱* 폴더를 선택 하 고 **폴더 선택** 을 누릅니다. 
5.  Unity는 *응용* 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다. 
6.  Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 *파일 탐색기* 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)

## <a name="chapter-10--deploy-to-hololens"></a>10 장-HoloLens에 배포

HoloLens에 배포 하려면:

1.  HoloLens의 IP 주소가 필요 하며 (원격 배포의 경우) HoloLens **개발자 모드** 에 있는지 확인 해야 합니다. 이렇게 하려면 다음을 수행합니다.

    1. HoloLens를 입고 **설정** 를 엽니다.
    2. **네트워크 & 인터넷 > Wi-Fi > 고급 옵션** 으로 이동 합니다.
    3. **IPv4** 주소를 적어둡니다.
    4. 그런 다음 **설정** 으로 다시 이동한 다음 **개발자를 위한 & Security >를 업데이트** 합니다. 
    5. 에서 개발자 모드를 설정 합니다.

2.  새 Unity 빌드 ( *앱* 폴더)로 이동 하 고 *Visual Studio* 를 사용 하 여 솔루션 파일을 엽니다.
3.  솔루션 구성에서 **디버그를** 선택합니다.
4.  솔루션 플랫폼에서 **x86**, **원격 머신** 을 선택합니다. 

    ![Visual Studio 솔루션을 배포합니다.](images/AzureLabs-Lab2-27.png)
 
5.  **빌드 메뉴로** 이동하고 **솔루션 배포** 를 클릭하여 애플리케이션을 HoloLens 테스트용으로 로드합니다.
6.  이제 앱이 시작 준비가 된 HoloLens 설치된 앱 목록에 표시됩니다.

> [!NOTE]
> 몰입형 헤드셋에 배포하려면 **솔루션 플랫폼을** *로컬 머신으로* 설정하고 **구성을** *디버그로* 설정하고 *x86을* **플랫폼** 으로 설정합니다. 그런 다음, **빌드 메뉴** 를 사용하여 로컬 머신에 배포하고 *솔루션 배포를* 선택합니다. 

## <a name="your-finished-computer-vision-api-application"></a>완료된 Computer Vision API 애플리케이션

축하합니다. Azure Computer Vision API를 활용하여 실제 개체를 인식하고 표시된 내용에 대한 신뢰도를 표시하는 혼합 현실 앱을 빌드했습니다.

![랩 결과](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

*Tags* 매개 변수를 사용한 *것처럼(VisionManager* 내에서 사용되는 *엔드포인트* 내에서 입증된 대로) 다른 정보를 검색하도록 앱을 확장합니다. [여기에](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)액세스할 수 있는 다른 매개 변수를 살펴보세요.

### <a name="exercise-2"></a>연습 2

반환된 Azure 데이터를 더 대화적이고 읽기 가능한 방식으로 표시하여 숫자를 숨길 수 있습니다. 봇이 사용자에게 말하는 것처럼