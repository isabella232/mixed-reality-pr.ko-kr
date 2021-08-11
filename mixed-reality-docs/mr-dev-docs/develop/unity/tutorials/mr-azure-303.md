---
title: HoloLens(1세대) 및 Azure 303 - LUIS(자연어 이해)
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure LUIS(Language Understanding Intelligence Service)를 구현하는 방법을 알아봅니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, language understanding Intelligence Service, luis, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 443b5f2c186fbbb0a3e979b48ccc20b4c3d3b4f0bd9c93950e27e1f86d610c07
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218243"
---
# <a name="hololens-1st-gen-and-azure-303-natural-language-understanding-luis"></a>HoloLens(1세대) 및 Azure 303: LUIS(자연어 이해)

<br>

>[!NOTE]
>Mixed Reality 아카데미 자습서는 HoloLens(1세대) 및 Mixed Reality 몰입형 헤드셋을 염두에 두고 설계되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다.  이러한 자습서는 HoloLens 2에 사용되는 최신 도구 집합 또는 상호 작용으로 업데이트되지 **_않습니다_**.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2 위해 개발하는 방법을 보여 주는 새로운 자습서 시리즈가 나중에 게시될 예정입니다.  이 알림은 해당 자습서가 게시될 때 해당 자습서에 대한 링크로 업데이트됩니다.

<br>

이 과정에서는 Language Understanding API와 함께 Azure Cognitive Services 사용하여 혼합 현실 애플리케이션에 Language Understanding 통합하는 방법에 대해 알아봅니다.

![랩 결과](images/AzureLabs-Lab3-000.png)

*LUIS(Language Understanding)는* 사용자가 원하는 것을 자신의 단어로 추출하는 것과 같이 사용자 입력에서 의미를 만들 수 있는 기능을 애플리케이션에 제공하는 Microsoft Azure 서비스입니다. 이는 입력 정보를 이해하고 학습한 다음, 자세한 관련 정보로 회신할 수 있는 기계 학습을 통해 달성됩니다. 자세한 내용은 AZURE [LUIS(Language Understanding) 페이지를 방문하세요.](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)

이 과정을 완료하면 다음을 수행할 수 있는 혼합 현실 몰입형 헤드셋 애플리케이션이 있습니다.

1.  몰입형 헤드셋에 연결된 마이크를 사용하여 사용자 입력 음성을 캡처합니다. 
2.  캡처된 받아쓰기 를 *Azure Language Understanding Intelligent Service(* *LUIS)로* 보냅니다. 
3.  LUIS가 분석될 보내기 정보에서 의미를 추출하고 사용자 요청의 의도를 확인하도록 합니다.

개발에는 사용자가 음성 및/또는 응시를 사용하여 장면에 있는 개체의 크기와 색을 변경할 수 있는 앱 만들기가 포함됩니다. 모션 컨트롤러의 사용은 다루지 않습니다.

애플리케이션에서 결과를 디자인과 통합하는 방법은 사용자 에게 달려 있습니다. 이 과정은 Unity Project Azure 서비스를 통합하는 방법을 교육하기 위해 고안되었습니다. 이 과정에서 얻은 지식을 활용하여 혼합 현실 애플리케이션을 개선하는 것이 여러분의 작업입니다.

[12장에서](#chapter-12--improving-your-luis-service)다루는 LUIS 학습을 여러 번 준비합니다. LUIS가 학습될수록 더 나은 결과를 얻을 수 있습니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 및 Azure 303: LUIS(자연어 이해)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 이 과정은 주로 WINDOWS MIXED REALITY 몰입형(VR) 헤드셋에 중점을 두지만 이 과정에서 학습한 내용을 Microsoft HoloLens 적용할 수도 있습니다. 과정을 진행하면서 HoloLens 지원하기 위해 사용해야 할 수 있는 변경 내용에 대한 메모를 볼 수 있습니다. HoloLens 사용하는 경우 음성 캡처 중에 일부 에코를 확인할 수 있습니다.

## <a name="prerequisites"></a>필수 조건

> [!NOTE]
> 이 자습서는 Unity 및 C#에 대한 기본적인 경험이 있는 개발자를 위해 설계되었습니다. 또한 이 문서 내의 필수 조건 및 작성된 지침은 작성 당시 테스트 및 확인된 내용을 나타냅니다(2018년 5월). [도구 설치](../../install-the-tools.md) 문서에 나열된 대로 최신 소프트웨어를 자유롭게 사용할 수 있지만, 이 과정의 정보는 아래 나열된 내용보다 최신 소프트웨어에서 찾을 수 있는 정보와 완벽하게 일치한다고 가정해서는 안 됩니다.

이 과정에서는 다음 하드웨어 및 소프트웨어를 사용하는 것이 좋습니다.

- 몰입형(VR) 헤드셋 개발을 위해 [Windows Mixed Reality 호환되는](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 개발 PC
- [개발자 모드를 사용하도록 설정된 Windows 10 Fall Creators Update(이상)](../../install-the-tools.md)
- [최신 Windows 10 SDK](../../install-the-tools.md)
- [Unity 2017.4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- 개발자 모드를 사용하도록 설정된 [Windows Mixed Reality 몰입형(VR) 헤드셋](../../../discover/immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](/hololens/hololens1-hardware)
- 기본 제공 마이크가 있는 마이크 세트(헤드셋에 기본 제공 마이크 및 스피커가 없는 경우)
- Azure 설정 및 LUIS 검색을 위한 인터넷 액세스

## <a name="before-you-start"></a>시작하기 전에

1.  이 프로젝트를 빌드하는 데 문제가 발생하지 않도록 하려면 이 자습서에서 언급한 프로젝트를 루트 또는 루트에 가까운 폴더에 만드는 것이 좋습니다(긴 폴더 경로로 인해 빌드 시 문제가 발생할 수 있습니다). 
2.  컴퓨터에서 받아쓰기를 사용하도록 허용하려면 **Windows 설정 > Privacy > Speech, Inking & Typing으로** 이동하여 Speech **Services 켜기 및 제안 입력** 단추를 누릅니다.
3.  이 자습서의 코드를 사용하면 머신에 설정된 **기본 마이크 디바이스에서** 기록할 수 있습니다. 기본 마이크 디바이스가 음성을 캡처하는 데 사용하려는 디바이스로 설정되어 있는지 확인합니다.
4.  헤드셋에 기본 제공 마이크가 있는 경우 *Mixed Reality 포털* 설정에서 *"헤드셋을 신으면 헤드셋 마이크로 전환"* 옵션이 켜져 있는지 확인합니다.

    ![몰입형 헤드셋 설정](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>1장 - Azure Portal 설정

Azure에서 *Language Understanding* 서비스를 사용하려면 애플리케이션에서 사용할 수 있도록 서비스의 인스턴스를 구성해야 합니다.

1.  [Azure Portal](https://portal.azure.com)에 로그인합니다.

    > [!NOTE]
    > Azure 계정이 아직 없는 경우 만들어야 합니다. 클래스룸 또는 랩 상황에서 이 자습서를 따르는 경우 강사 또는 프록터 중 하나에 새 계정 설정에 대한 도움을 요청하세요.

2.  로그인한 후 왼쪽 위 모서리에서 **새로** 만들기를 클릭하고 *Language Understanding* 검색한 다음 **Enter 키를** 클릭합니다. 

    ![LUIS 리소스 만들기](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > **New라는** 단어는 최신 포털에서 **리소스 만들기** 로 대체되었을 수 있습니다.
 
3.  오른쪽의 새 페이지에서는 Language Understanding 서비스에 대한 설명을 제공합니다. 이 페이지의 왼쪽 아래에서 **만들기** 단추를 선택하여 이 서비스의 인스턴스를 만듭니다.

    ![LUIS 서비스 만들기 - 법적 고지 사항](images/AzureLabs-Lab3-02.png)
 
4.  만들기를 클릭한 후에는 다음을 수행합니다.

    1. 이 서비스 인스턴스에 대해 원하는 **이름을** 삽입합니다.
    2. **구독** 을 선택합니다.
    3. LUIS 서비스를 처음 만드는 경우 적절한 **가격 책정 계층을** 선택합니다. *무료* 계층(F0)을 사용할 수 있어야 합니다. 이 과정에서는 무료 할당만으로도 충분합니다.
    4. 리소스 **그룹을** 선택하거나 새 리소스 그룹을 만듭니다. 리소스 그룹은 Azure 자산 컬렉션에 대한 액세스를 모니터링, 제어, 프로비전 및 관리하는 방법을 제공합니다. 단일 프로젝트(예: 이러한 과정)와 연결된 모든 Azure 서비스를 공통 리소스 그룹 아래에 유지하는 것이 좋습니다. 

        > Azure 리소스 그룹에 대해 자세히 알아보려면 [리소스 그룹 문서 를 방문하세요.](/azure/azure-resource-manager/resource-group-portal)

    5. 리소스 그룹의 **위치를** 결정합니다(새 리소스 그룹을 만드는 경우). 위치는 애플리케이션이 실행되는 지역에 있는 것이 가장 좋습니다. 일부 Azure 자산은 특정 지역에서만 사용할 수 있습니다.
    6. 또한 이 서비스에 적용된 약관을 이해했다는 것을 확인해야 합니다.
    7. **만들기** 를 선택합니다.

        ![LUIS 서비스 만들기 - 사용자 입력](images/AzureLabs-Lab3-03.png)
 
5.  **만들기를** 클릭하면 서비스가 생성될 때까지 기다려야 합니다. 이 경우 1분 정도 걸릴 수 있습니다.
6.  서비스 인스턴스가 만들어지면 포털에 알림이 표시됩니다. 
 
    ![새 Azure 알림 이미지](images/AzureLabs-Lab3-04.png)

7.  알림을 클릭하여 새 서비스 인스턴스를 탐색합니다.

    ![리소스 만들기 성공 알림](images/AzureLabs-Lab3-05.png)
 
8.  알림에서 **리소스로 이동** 단추를 클릭하여 새 서비스 인스턴스를 탐색합니다. 새 LUIS 서비스 인스턴스로 이동됩니다. 
 
    ![LUIS 키 액세스](images/AzureLabs-Lab3-06.png)

9.  이 자습서 내에서 애플리케이션은 서비스의 구독 키를 사용하여 수행되는 서비스를 호출해야 합니다.
10. *LUIS API* 서비스의 *빠른 시작* 페이지에서 첫 번째 단계인 *키 잡기로* 이동하고 키를 클릭합니다(키 아이콘으로 표시된 서비스 탐색 메뉴에 있는 파란색 하이퍼링크 키를 클릭하여 이를 달성할 수도 있음).  그러면 서비스 *키* 가 공개됩니다.
11. 나중에 프로젝트에서 필요하므로 표시된 키 중 하나의 복사본을 찍습니다. 
12. *서비스* 페이지에서 *Language Understanding 포털을* 클릭하여 LUIS 앱 내에서 새 서비스를 만드는 데 사용할 웹 페이지로 리디렉션됩니다. 

## <a name="chapter-2--the-language-understanding-portal"></a>2장 – Language Understanding Portal

이 섹션에서는 LUIS 포털에서 LUIS 앱을 만드는 방법을 알아봅니다. 

> [!IMPORTANT]
> 이 장 내에서 *엔터티,* *의도* 및 *발화* 설정은 LUIS 서비스를 빌드하는 첫 번째 단계일 뿐입니다. 더 정확하게 하기 위해 서비스를 여러 번 다시 학습해야 합니다. 서비스 재학습은 이 과정의 [마지막 챕터에서](#chapter-12--improving-your-luis-service) 다루므로 완료해야 합니다.

1.  *Language Understanding Portal* 에 도달하면 아직 로그인하지 않은 경우 Azure Portal 동일한 자격 증명으로 로그인해야 할 수 있습니다. 

    ![LUIS 로그인 페이지](images/AzureLabs-Lab3-07.png)
 
2.  LUIS를 처음 사용 하는 경우 시작 페이지의 아래쪽으로 스크롤하여 **LUIS 앱 만들기** 단추를 찾아 클릭 해야 합니다.

    ![LUIS 앱 만들기 페이지](images/AzureLabs-Lab3-08.png)
 
3.  로그인 한 후 **내 앱** (현재 해당 섹션에 있지 않은 경우)을 클릭 합니다. 그런 다음 **새 앱 만들기** 를 클릭할 수 있습니다.

    ![LUIS-내 앱 이미지](images/AzureLabs-Lab3-09.png)
 
4.  앱에 *이름을* 지정 합니다.
5.  앱이 영어와 다른 언어를 파악 해야 하는 경우 *문화권* 을 적절 한 언어로 변경 해야 합니다.
6.  여기에서 새 LUIS 앱에 대 한 *설명을* 추가할 수도 있습니다.

    ![LUIS-새 앱 만들기](images/AzureLabs-Lab3-10.png)

7.  **완료** 를 누르면 새 *LUIS* 응용 프로그램의 *빌드* 페이지가 입력 됩니다.
8.  여기에서 이해할 수 있는 몇 가지 중요 한 개념이 있습니다.

    -   *의도* 는 사용자의 쿼리 다음에 호출 될 메서드를 나타냅니다. *의도* 에 하나 이상의 *엔터티가* 있을 수 있습니다.
    -   *엔터티* 는 *의도* 와 관련 된 정보를 설명 하는 쿼리의 구성 요소입니다.
    -   *길이 발언* 는 개발자가 직접 학습 하는 데 사용 하는 개발자가 제공 하는 쿼리의 예입니다.

이러한 개념을 완벽 하 게 명확 하 게 이해 하지 못하는 경우이 과정에서이 장을 자세히 설명 하므로 걱정 하지 마세요.

이 과정을 빌드하는 데 필요한 *엔터티* 를 만드는 것부터 시작 합니다.

9.  페이지의 왼쪽에서 *엔터티* 를 클릭 한 다음 **새 엔터티 만들기** 를 클릭 합니다.

    ![새 엔터티 만들기](images/AzureLabs-Lab3-11.png)

10. 새 엔터티 *색* 을 호출 하 고 해당 형식을 *Simple* 로 설정한 후 **Done** 을 누릅니다.

    ![단순 엔터티 색 만들기](images/AzureLabs-Lab3-12.png)
 
11. 이 프로세스를 반복 하 여 라는 세 개의 단순 엔터티 (3)를 만듭니다.

    -   *업사이징*
    -   *줄이지*
    -   *대상*

결과는 아래 이미지와 같아야 합니다.

![엔터티 생성 결과](images/AzureLabs-Lab3-13.png)
 
이 시점에서 *의도* 만들기를 시작할 수 있습니다. 

> [!WARNING]
> **없음** 의도를 삭제 하지 마십시오.

12. 페이지의 왼쪽에서 **의도** 를 클릭 한 다음 **새 용도 만들기** 를 클릭 합니다.

    ![새 의도 만들기](images/AzureLabs-Lab3-14.png)

13. 새 *의도* **changeobjectcolor** 를 호출 합니다.

    > [!IMPORTANT]
    > 이 *의도* 이름은이 과정의 뒷부분에 나오는 코드 내에서 사용 되므로 최상의 결과를 위해 제공 된 대로 정확 하 게이 이름을 사용 합니다.

이름을 확인 한 후에는 의도 페이지로 리디렉션됩니다.

![LUIS-의도 페이지](images/AzureLabs-Lab3-15.png)

5 개 이상의 다른 *길이 발언* 를 입력 하 라는 텍스트 상자가 표시 됩니다.

> [!NOTE]
> LUIS는 모든 길이 발언를 소문자로 변환 합니다.

14. 맨 위 텍스트 상자에 다음 *Utterance* 을 삽입 합니다 (현재 텍스트 *형식이 5 개 예* 인 경우). )를 **입력** 하 고 enter 키를 누릅니다.

```
The color of the cylinder must be red
```

새 *Utterance* 이 아래 목록에 표시 됩니다.

동일한 프로세스를 수행 하 고 다음 6 개 (6) 길이 발언를 삽입 합니다.

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

만든 각 Utterance에 대해 LUIS에서 엔터티로 사용할 단어를 식별 해야 합니다. 이 예제에서는 모든 색을 *색* 엔터티로 레이블과 대상에 대 한 모든 가능한 참조를 *대상* 엔터티로 표시 해야 합니다.

15. 이렇게 하려면 첫 번째 Utterance에서 *실린더* 단어를 클릭 하 고 *대상* 을 선택 합니다.

    ![Utterance 대상 식별](images/AzureLabs-Lab3-16.png)
 
16. 이제 첫 번째 Utterance *빨간색* 이라는 단어를 클릭 하 고 *색* 을 선택 합니다.

    ![Utterance 엔터티 식별](images/AzureLabs-Lab3-17.png)
 
17. 다음 줄에 레이블을 지정 합니다. 여기서 *cube* 는 *대상* 이어야 하 고 *black* 은 *색* 이어야 합니다. 또한 제공 되는 *' this '*, *' it '* 및 *' this object '* 단어를 사용 하 여 특정 대상 유형을 사용할 수도 있습니다. 

18. 모든 길이 발언에 레이블이 붙은 엔터티가 있을 때까지 위의 프로세스를 반복 합니다. 도움이 필요 하면 아래 이미지를 참조 하세요.

    > [!TIP]
    > 엔터티로 레이블을 지정할 단어를 선택할 경우 다음을 수행합니다.
    > - 한 단어에 대해서만 클릭 하면 됩니다.
    > - 두 개 이상의 단어 집합의 경우 시작 부분을 클릭 한 다음 집합의 끝 부분을 클릭 합니다.

    > [!NOTE]
    > *토큰 뷰* 토글 단추를 사용 하 여 **엔터티/토큰 뷰** 간을 전환할 수 있습니다.

19. 결과는 아래 이미지에 표시 된 것과 같이 **엔터티/토큰 뷰** 를 표시 합니다.

    ![토큰 & 엔터티 보기](images/AzureLabs-Lab3-18.png)
  
20. 이 시점에서 페이지의 오른쪽 위에 있는 **학습** 단추를 누르고 작은 라운드 표시기가 녹색으로 전환 될 때까지 기다립니다. 이는 LUIS가 이러한 의도를 인식할 수 있도록 성공적으로 교육 되었음을 나타냅니다.

    ![LUIS 학습](images/AzureLabs-Lab3-19.png)
 
21. 실습으로, 엔터티 *대상*, *업사이징* 및 *다운 크기* 를 사용 하 여 **changeobjectsize** 라는 새로운 의도를 만듭니다.
22. 이전 의도와 동일한 프로세스를 수행 하 여 *크기* 변경에 대 한 길이 발언 8 (8)을 삽입 합니다.

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. 결과는 아래 이미지에 있는 것과 같아야 합니다.

    ![ChangeObjectSize 토큰/엔터티 설정](images/AzureLabs-Lab3-20.png) 

24. 두 의도, **Changeobjectcolor** 및 **changeobjectcolor** 를 모두 만들고 학습 한 후에는 페이지 맨 위에 있는 **게시** 단추를 클릭 합니다.

    ![LUIS 서비스 게시](images/AzureLabs-Lab3-21.png)

25. *게시* 페이지에서 LUIS 앱을 마무리 하 고 게시 하 여 코드에서 액세스할 수 있도록 합니다.

    1. 드롭다운을 **프로덕션** 으로 *게시를* 설정 합니다.
    2. 표준 시간대로 *표준* 시간대를 설정 합니다.
    3. **모든 예측 된 의도 점수를 포함** 하는 상자를 선택 합니다.
    4. **프로덕션 슬롯에 게시를** 클릭 합니다.

        ![게시 설정](images/AzureLabs-Lab3-22.png)

26. *리소스 및 키* 섹션에서 다음을 수행 합니다.

    1.  Azure Portal에서 서비스 인스턴스에 대해 설정한 지역을 선택 합니다.
    2.  아래 **Starter_Key** 요소를 확인 하 고 무시 합니다.
    3.  **키 추가** 를 클릭 하 고 서비스 인스턴스를 만들 때 Azure Portal에서 가져온 *키* 를 삽입 합니다. Azure와 LUIS 포털이 동일한 사용자에 게 로그인 하는 경우 *테 넌 트 이름*, *구독 이름* 및 사용 하려는 *키* 에 대 한 드롭다운 메뉴가 제공 됩니다 (이전에는 azure portal에서 제공한 것과 동일한 이름을 사용).

    > [!IMPORTANT] 
    > *끝점* 아래에서 삽입 한 키에 해당 하는 끝점의 복사본을 만든 후 코드에서 곧 사용할 수 있습니다.
 
## <a name="chapter-3--set-up-the-unity-project"></a>3 장-Unity 프로젝트 설정

다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.

1.  *Unity* 를 열고 **새로 만들기** 를 클릭 합니다. 

    ![새 Unity 프로젝트를 시작 합니다.](images/AzureLabs-Lab3-24.png)

2.  이제 Unity Project 이름, insert **MR_LUIS** 를 제공 해야 합니다. 프로젝트 형식이 **3d** 로 설정 되었는지 확인 합니다. 위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다. 그런 다음 **프로젝트 만들기** 를 클릭 합니다.

    ![새 Unity 프로젝트에 대 한 세부 정보를 제공 합니다.](images/AzureLabs-Lab3-25.png)
 
3.  Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio** 로 설정 되어 있는지 확인 하는 것이 좋습니다. > 기본 설정 편집으로 이동한 다음 새 창에서 **외부 도구** 로 이동 합니다. **외부 스크립트 편집기** 를 **Visual Studio 2017** 로 변경 합니다. **기본 설정** 창을 닫습니다.

    ![스크립트 편집기 기본 설정을 업데이트 합니다.](images/AzureLabs-Lab3-26.png)
 
4.  그런 다음 **파일 > 빌드 설정** 로 이동 하 고 플랫폼 **전환** 단추를 클릭 하 여 플랫폼을 **유니버설 Windows 플랫폼** 로 전환 합니다.

    ![설정 창을 빌드하고 platform을 UWP로 전환 합니다.](images/AzureLabs-Lab3-27.png)
 
5.  **파일 > 빌드 설정** 로 이동 하 여 다음을 확인 합니다.

    1. **대상 장치가** **모든 장치로** 설정 됨

        > Microsoft HoloLens의 경우 **대상 장치** 를 *HoloLens* 로 설정 합니다.

    2. **빌드 형식이** **D3D** 로 설정 됩니다.
    3. **SDK** 가 **최신 설치** 로 설정 됨
    4. **Visual Studio 버전이** **최신 설치** 로 설정 됨
    5. **빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨
    6. 장면을 저장 하 고 빌드에 추가 합니다.

        1. 이렇게 하려면 열려 있는 **장면 추가** 를 선택 합니다. 저장 창이 표시 됩니다.
        
            ![열린 장면 추가 단추를 클릭 합니다.](images/AzureLabs-Lab3-28.png)

        2. 이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을** 로 지정한 다음

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab3-29.png)

        3. 새로 만든 **장면** 폴더를 연 다음 *파일 이름*: 텍스트 필드에 **MR_LuisScene** 를 입력 하 고 **저장** 을 누릅니다.

            ![새 장면에 이름을 지정 합니다.](images/AzureLabs-Lab3-30.png)

    7. *빌드 설정* 의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.

6. *빌드 설정* 창에서 **플레이어 설정** 단추를 클릭 하면 *검사기* 가 있는 공간에서 관련 패널이 열립니다. 

    ![플레이어 설정을 엽니다.](images/AzureLabs-Lab3-31.png) 
 
7. 이 패널에서 몇 가지 설정을 확인 해야 합니다.

    1. **기타 설정** 탭에서 다음을 수행 합니다.

        1. **Scripting Runtime 버전** 은 **안정적** 이어야 합니다 (.net 3.5 해당).
        2. **Scripting 백엔드** 는 **.net** 이어야 합니다.
        3. **API 호환성 수준은** **.net 4.6** 이어야 합니다.

            ![다른 설정을 업데이트 합니다.](images/AzureLabs-Lab3-32.png)
      
    2. **게시 설정** 탭 내의 **기능** 아래에서 다음을 확인 합니다.

        1. **InternetClient**
        2. **마이크**

            ![게시 설정을 업데이트 하는 중입니다.](images/AzureLabs-Lab3-33.png)

    3. 패널의 아래쪽에서 **XR 설정** ( **게시 설정** 아래에 있음)에서 지원 되는 틱 **가상 현실** 은 **Windows Mixed Reality SDK** 가 추가 되었는지 확인 합니다.

        ![X R 설정를 업데이트 합니다.](images/AzureLabs-Lab3-34.png)

8.  *빌드 설정* _Unity c #_ 프로젝트가 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다. 
9.  빌드 설정 창을 닫습니다.
10. 장면 및 Project 저장 (**파일 > 장면/파일 저장 > 프로젝트** 저장).

## <a name="chapter-4--create-the-scene"></a>4 장-장면 만들기

> [!IMPORTANT]
> 이 과정의 *Unity 설정* 구성 요소를 건너뛰고 계속 해 서 코드를 계속 사용 하려면 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)를 다운로드 하 여 프로젝트에 [사용자 지정 패키지로](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 [5 장](#chapter-5--create-the-microphonemanager-class)에서 계속 합니다. 

1.  *계층 패널* 의 빈 영역을 마우스 오른쪽 단추로 클릭 하 고 **3d 개체** 아래에서 **평면** 을 추가 합니다.

    ![평면을 만듭니다.](images/AzureLabs-Lab3-35.png)

2.  *계층 구조* 내에서 마우스 오른쪽 단추를 클릭 하 여 더 많은 개체를 만들 경우 마지막 개체를 선택한 경우 선택한 개체가 새 개체의 부모가 됩니다. 계층 구조 내의 빈 공간을 마우스 왼쪽 단추로 클릭 한 다음 마우스 오른쪽 단추를 클릭 하지 마십시오.

3.  위의 절차를 반복 하 여 다음 개체를 추가 합니다.

    1. *Sphere*
    2. *실린더*
    3. *Cube*
    4. *3D 텍스트*

4.  결과 장면 *계층 구조* 는 아래 이미지에 있는 것과 같아야 합니다.

    ![장면 계층 설정입니다.](images/AzureLabs-Lab3-36.png)
 
5.  **기본 카메라** 를 마우스 왼쪽 단추를 클릭 하 여 선택 하 고, *검사기 패널* 에서 모든 구성 요소를 포함 하는 카메라 개체를 확인 합니다.
6.  *검사기 패널* 의 맨 아래에 있는 **구성 요소 추가** 단추를 클릭 합니다.

    ![오디오 소스 추가](images/AzureLabs-Lab3-37.png)
 
7.  위에 표시 된 것 처럼 *오디오 원본* 이라는 구성 요소를 검색 합니다.
8.  또한 기본 카메라의 *변형* 구성 요소가 (0, 0, 0)로 설정 되어 있는지 확인 합니다. 카메라의 *변형* 구성 요소 옆에 있는 **기어** 아이콘을 누르고 **다시 설정** 을 선택 하 여이 작업을 수행할 수 있습니다. *변환* 구성 요소는 다음과 같습니다.

    1.  *Position* 은 **0, 0,** 0으로 설정 됩니다.
    2.  *회전* 은 **0, 0, 0** 으로 설정 됩니다.

    > [!NOTE] 
    > Microsoft HoloLens의 경우 **기본 카메라** 의 **카메라** 구성 요소에 포함 된 다음도 변경 해야 합니다.
    > - **플래그 지우기:** 단색입니다.
    > - **배경** ' Black, Alpha 0 ' – 16 진수 색: #00000000.

9.  **평면** 을 마우스 왼쪽 단추를 클릭 하 여 선택 합니다. *검사기 패널* 에서 *변형* 구성 요소를 다음 값으로 설정 합니다.

    |   X축    | Y축 |   Z 축    |
    |:-----:|:----------------------:|:-----:|
    | 0     | -1                     | 0     |


10. **구를** 마우스 왼쪽 단추를 클릭 하 여 선택 합니다. *검사기 패널* 에서 *변형* 구성 요소를 다음 값으로 설정 합니다.

    |   X축    | Y축 |   Z 축    |
    |:-----:|:----------------------:|:-----:|
    | 2     | 1                      | 2     |

11. **원통** 을 마우스 왼쪽 단추를 클릭 하 여 선택 합니다. *검사기 패널* 에서 *변형* 구성 요소를 다음 값으로 설정 합니다.

    |   X축    | Y축 |   Z 축    |
    |:-----:|:----------------------:|:-----:|
    | -2    | 1                      | 2     |

12. **큐브** 를 마우스 왼쪽 단추를 클릭 하 여 선택 합니다. *검사기 패널* 에서 *변형* 구성 요소를 다음 값으로 설정 합니다.

    |        | 변환 *위치* |       |  \| |       | 변환- *회전* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **예**                   | **Z** |  \| | **X** | **예**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. **새 텍스트** 개체를 마우스 왼쪽 단추를 클릭 하 여 선택 합니다. *검사기 패널* 에서 *변형* 구성 요소를 다음 값으로 설정 합니다.

    |       | 변환 *위치* |       |  \| |       | 변환- *배율* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **예**                  | **Z** |  \| | **X** | **예**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. **텍스트 메시** 구성 요소의 **글꼴 크기** 를 **50** 로 변경 합니다.
15. **텍스트 메시** 개체의 *이름을* **받아쓰기 텍스트로** 변경 합니다.

    ![3D 텍스트 개체 만들기](images/AzureLabs-Lab3-38.png)
 
16. 이제 계층 구조 패널 구조가 다음과 같이 표시 됩니다.

    ![장면 뷰의 텍스트 메시](images/AzureLabs-Lab3-38b.png)


17. 최종 장면은 아래 이미지와 같습니다.

    ![장면 뷰입니다.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>5 장-MicrophoneManager 클래스 만들기

만들려는 첫 번째 스크립트는 *MicrophoneManager* 클래스입니다. 이를 수행 하 고 나면 *Luismanager*, *동작* 클래스 및 마지막으로 *응시* 클래스 (각 챕터에 도달 하는 경우에도 적용 됨)를 만듭니다.

*MicrophoneManager* 클래스는 다음을 담당 합니다.

-   헤드셋 또는 컴퓨터에 연결 된 기록 장치 검색 (기본 항목 중 하나)
-   오디오 (음성)를 캡처하고 받아쓰기를 사용 하 여 문자열로 저장 합니다.
-   음성이 일시 중지 되 면 받아쓰기를 *Luismanager* 클래스에 제출 합니다. 

이 클래스를 만들려면: 

1.  *Project 패널* 을 마우스 오른쪽 단추로 클릭 하 **> 폴더를 만듭니다**. 폴더 **스크립트** 를 호출 합니다. 

    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab3-40.png)
 
2.  **Scripts** 폴더를 만든 다음 두 번 클릭 하 여 엽니다. 그런 다음 해당 폴더 내에서 마우스 오른쪽 단추를 클릭 하 **> c # 스크립트를 만듭니다**. 스크립트 이름을 *MicrophoneManager* 로 합니다. 

3.  *MicrophoneManager* 을 두 번 클릭 하 여 *Visual Studio* 를 사용 하 여 엽니다.
4.  파일의 맨 위에 다음 네임 스페이스를 추가 합니다.

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  그런 다음 *MicrophoneManager* 클래스 안에 다음 변수를 추가 합니다.

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  이제 *활성 ()* 및 *Start ()* 메서드에 대 한 코드를 추가 해야 합니다. 이러한 작업은 클래스가 초기화 될 때 호출 됩니다.

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  이제 앱이 음성 캡처를 시작 및 중지 하는 데 사용 하는 메서드를 사용 하 여 곧 빌드 될 *Luismanager* 클래스에 전달 해야 합니다. 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  음성이 일시 중지 될 때 호출 되는 *받아쓰기 처리기* 를 추가 합니다. 이 메서드는 받아쓰기 텍스트를 *Luismanager* 클래스로 전달 합니다.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > 이 클래스는 사용 하지 않으므로 *Update ()* 메서드를 삭제 합니다.

9.  *Unity* 로 반환 하기 전에 *Visual Studio* 변경 내용을 저장 해야 합니다.

    > [!NOTE]
    > 이 시점에서 *Unity 편집기 콘솔 패널* 에 오류가 나타납니다. 코드는 다음 챕터에서 만들 *Luismanager* 클래스를 참조 하기 때문입니다.

## <a name="chapter-6--create-the-luismanager-class"></a>6 장 – LUISManager 클래스 만들기

Azure LUIS 서비스에 대 한 호출을 수행 하는 *Luismanager* 클래스를 만들 때입니다. 

이 클래스의 목적은 *MicrophoneManager* 클래스에서 받아쓰기 텍스트를 받고 분석 될 *Azure Language Understanding API* 로 보내는 것입니다.

이 클래스는 *JSON* 응답을 deserialize 하 고 *동작* 클래스의 적절 한 메서드를 호출 하 여 작업을 트리거합니다.

이 클래스를 만들려면: 

1.  **스크립트** 폴더를 두 번 클릭 하 여 엽니다. 
2.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> c # 스크립트 만들기** 를 클릭 합니다. 스크립트 이름을 *Luismanager* 로 합니다. 
3.  스크립트를 두 번 클릭 하 여 Visual Studio를 사용 하 여 엽니다.
4.  파일의 맨 위에 다음 네임 스페이스를 추가 합니다.

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  먼저 Azure에서 deserialize 된 JSON 응답을 나타내는 동일한 스크립트 파일 ( *Start ()* 메서드 위에 있는)의 *luismanager* **클래스 내에서 세 개의 클래스를** 만듭니다.

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  그런 다음, 다음 변수를 *Luismanager* 클래스 내에 추가 합니다.
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  LUIS 끝점을 지금 (LUIS 포털에서 수행할 수 있도록)에 두어야 합니다.

8.  이제 해제 *()* 메서드에 대 한 코드를 추가 해야 합니다. 이 메서드는 클래스가 초기화 될 때 호출 됩니다.

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  이제이 응용 프로그램에서 *MicrophoneManager* 클래스 로부터 받은 받아쓰기를 *LUIS* 로 보낸 다음 응답을 수신 및 deserialize 하는 데 사용 하는 메서드가 필요 합니다. 
10. 의도 및 연결 된 엔터티의 값이 확인 되 면 *동작* 클래스의 인스턴스에 전달 되어 의도 된 동작을 트리거합니다.

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. 결과 *AnalysedQuery* 를 읽고 엔터티를 확인 하는 *AnalyseResponseElements ()* 라는 새 메서드를 만듭니다. 이러한 엔터티가 결정 되 면 작업에서 사용할 *동작* 클래스의 인스턴스에 전달 됩니다.

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > *Start ()* 및 *Update ()* 메서드는이 클래스에서 사용 하지 않으므로 삭제 합니다.

12. *Unity* 로 반환 하기 전에 *Visual Studio* 변경 내용을 저장 해야 합니다.

> [!NOTE]
> 이 시점에서 *Unity 편집기 콘솔 패널* 에 몇 가지 오류가 표시 됩니다. 코드는 다음 챕터에서 만들 *동작* 클래스를 참조 하기 때문입니다.

## <a name="chapter-7--create-the-behaviours-class"></a>7 장 – 동작 클래스 만들기

*동작* 클래스는 *luismanager* 클래스에서 제공 하는 엔터티를 사용 하 여 작업을 트리거합니다.

이 클래스를 만들려면: 

1.  **스크립트** 폴더를 두 번 클릭 하 여 엽니다. 
2.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> c # 스크립트 만들기** 를 클릭 합니다. 스크립트 이름을 *동작* 로 합니다. 
3.  스크립트를 두 번 클릭 하 여 *Visual Studio* 를 사용 하 여 엽니다.
4.  그런 다음 *동작* 클래스 안에 다음 변수를 추가 합니다.

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  *활성 ()* 메서드 코드를 추가 합니다. 이 메서드는 클래스가 초기화 될 때 호출 됩니다.

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  다음 메서드는 이전에 만든 *Luismanager* 클래스에서 호출 되어 쿼리의 대상인 개체를 확인 한 다음 적절 한 작업을 트리거합니다.

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  *Findtarget ()* 메서드를 추가 하 여 현재 의도의 대상인 *gameobject* 를 확인 합니다. 이 메서드는 엔터티에 명시적 대상이 정의 되어 있지 않은 경우 대상의 기본값을 "gazed"로 *GameObject* 합니다.

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > *Start ()* 및 *Update ()* 메서드는이 클래스에서 사용 하지 않으므로 삭제 합니다.

8.  *Unity* 로 반환 하기 전에 *Visual Studio* 변경 내용을 저장 해야 합니다.

## <a name="chapter-8--create-the-gaze-class"></a>8 장-응시 클래스 만들기

이 앱을 완료 하는 데 필요한 마지막 클래스는 *응시* 클래스입니다. 이 클래스는 현재 사용자의 시각적 포커스에 있는 *GameObject* 에 대 한 참조를 업데이트 합니다.

이 클래스를 만들려면: 

1.  **스크립트** 폴더를 두 번 클릭 하 여 엽니다. 
2.  **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> c # 스크립트 만들기** 를 클릭 합니다. 스크립트 이름을 *응시* 로 합니다. 
3.  스크립트를 두 번 클릭 하 여 *Visual Studio* 를 사용 하 여 엽니다.
4.  이 클래스에 대해 다음 코드를 삽입 합니다.

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  *Unity* 로 반환 하기 전에 *Visual Studio* 변경 내용을 저장 해야 합니다.

## <a name="chapter-9--completing-the-scene-setup"></a>9 장-장면 설정 완료

1.  장면의 설정을 완료 하려면 Scripts 폴더에서 만든 각 스크립트를 *계층 패널* 의 **기본 카메라** 개체로 끕니다.
2.  **주 카메라** 를 선택 하 고 *검사기 패널* 에서 연결 된 각 스크립트를 볼 수 있어야 하며, 아직 설정 하지 않은 각 스크립트에 대 한 매개 변수가 있다는 것을 알 수 있습니다.

    ![카메라 참조 대상을 설정 합니다.](images/AzureLabs-Lab3-41.png)

3.  이러한 매개 변수를 올바르게 설정 하려면 다음 지침을 따르세요.

    1. *MicrophoneManager*:

        - *계층 패널* 에서 **받아쓰기 텍스트** 개체를 **받아쓰기 텍스트** 매개 변수 값 상자로 끌어옵니다.

    2. *계층 패널* 에서 *동작*:

        - **구** 개체를 *구* 참조 대상 상자로 끌어 옵니다.
        - **원통을** *원통* 참조 대상 상자로 끌어 옵니다.
        - **큐브를** *큐브* 참조 대상 상자로 끌어 옵니다.

    3. *응시:*

        - 응시 *최대 거리를* **300으로** 설정합니다(아직 설정하지 않은 경우). 

4.  결과는 아래 이미지와 같습니다.

    ![카메라 참조 대상을 표시합니다. 이제 설정됩니다.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>10장 – Unity 편집기에서 테스트

장면 설정이 제대로 구현되어 있는지 테스트합니다.

다음 사항을 확인합니다.

-   모든 스크립트는 **주 카메라** 개체에 연결됩니다. 
-   *주 카메라 검사기 패널의* 모든 필드가 제대로 할당됩니다.

1.  *Unity 편집기* 에서 **재생** 단추를 누릅니다. 앱은 연결된 몰입형 헤드셋 내에서 실행되어야 합니다.

2.  다음과 같은 몇 가지 발언을 시도합니다.

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > Unity 콘솔에서 기본 오디오 디바이스 변경에 대한 오류가 표시되면 해당 장면이 예상대로 작동하지 않을 수 있습니다. 혼합 현실 포털에서 헤드셋이 있는 헤드셋의 기본 제공 마이크를 처리하는 방식 때문입니다. 이 오류가 표시되면 장면을 중지하고 다시 시작하면 예상대로 작동합니다.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>11장 - UWP 솔루션 빌드 및 테스트용 로드

애플리케이션이 Unity 편집기에서 작동하는지 확인했으면 빌드 및 배포할 준비가 된 것입니다.

빌드하려면 다음을 수행합니다.

1.  **파일 > 저장을** 클릭하여 현재 장면을 저장합니다.
2.  파일 **> 빌드 설정** 이동합니다.
3.  **Unity C#** 프로젝트(UWP 프로젝트를 만든 후 코드를 보고 디버깅하는 데 유용함)라는 상자를 선택합니다.
4.  열린 **장면 추가를** 클릭한 다음 **빌드를** 클릭합니다.

    ![빌드 설정 창](images/AzureLabs-Lab3-43.png)

4.  솔루션을 빌드할 폴더를 선택하라는 메시지가 표시됩니다. 

5.  *BUILDS* 폴더를 만들고 해당 폴더 내에서 선택한 적절한 이름으로 다른 폴더를 만듭니다. 
6.  **폴더 선택을 클릭하여** 해당 위치에서 빌드를 시작합니다.
 
    ![빌드 폴더 만들기 ](images/AzureLabs-Lab3-44.png)
     ![ 빌드 폴더 선택](images/AzureLabs-Lab3-45.png)
 
7.  Unity 빌드가 완료되면(시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창을 열어야 합니다.

로컬 컴퓨터에 배포하려면 다음을 수행합니다.

1.  *Visual Studio* [이전 챕터](#chapter-10--test-in-the-unity-editor)에서 만든 솔루션 파일을 엽니다.
2.  솔루션 **플랫폼에서** **x86**, **로컬 머신** 을 선택합니다.
3.  솔루션 **구성에서** **디버그를** 선택합니다.

    > Microsoft HoloLens 경우 컴퓨터에 테더링되지 않도록 *원격 컴퓨터* 로 설정하는 것이 더 쉬울 수 있습니다. 그러나 다음을 수행해야 합니다.
    > - 설정 > Network & Internet > Wi-Fi > 고급 옵션 내에서 찾을 수 있는 HoloLens **IP 주소를** 알고 *있습니다.* IPv4는 사용해야 하는 주소입니다. 
    > - **개발자 모드가** **켜기인지 확인합니다.** *개발자용 설정 > 업데이트 & 보안 > 찾습니다.*

    ![앱 배포](images/AzureLabs-Lab3-46.png)
 
4.  **빌드 메뉴로** 이동하고 **솔루션 배포를** 클릭하여 애플리케이션을 컴퓨터에 테스트용으로 로드합니다.
5.  이제 앱이 설치된 앱 목록에 표시되고, 시작 준비가 되었습니다.
6.  앱이 시작되면 _마이크_ 에 대한 액세스 권한을 부여하라는 메시지가 표시됩니다. 동작 *컨트롤러,* 음성 *입력* 또는 *키보드를* 사용하여 **예** 단추를 누릅니다. 

## <a name="chapter-12--improving-your-luis-service"></a>12장 - LUIS 서비스 개선

>[!IMPORTANT] 
> 이 챕터는 매우 중요하며 LUIS 서비스의 정확도를 향상시키는 데 도움이 되도록 여러 번 반복해야 할 수 있습니다. 이 작업을 완료해야 합니다.

LUIS에서 제공하는 이해 수준을 개선하려면 새 발언을 캡처하고 사용하여 LUIS 앱을 다시 학습시켜야 합니다.

예를 들어 "증가" 및 "Upsize"를 이해하도록 LUIS를 학습했을 수 있지만 앱에서 "확대"와 같은 단어도 이해하기를 원하지 않나요?

애플리케이션을 여러 번 사용한 후에는 LUIS에서 모든 것을 수집하고 LUIS 포털에서 사용할 수 있습니다.

1.  이 [링크](https://www.luis.ai/home)및 로그인을 따라 포털 애플리케이션으로 이동합니다.
2.  MS 자격 증명을 사용하여 로그인한 후 *앱 이름* 를 클릭합니다.
3.  페이지 왼쪽에서 **엔드포인트 발화 검토** 단추를 클릭합니다.

    ![발화 검토](images/AzureLabs-Lab3-47.png)
 
4.  혼합 현실 애플리케이션에서 LUIS로 보낸 발화 목록이 표시됩니다.

    ![발화 목록](images/AzureLabs-Lab3-48.png)
 
몇 가지 강조 표시된 *엔터티 가 표시됩니다.* 

강조 표시된 각 단어를 마우스로 가리키면 각 발화 를 검토하고 올바르게 인식된 엔터티, 잘못된 엔터티 및 누락된 엔터티를 확인할 수 있습니다.

위의 예제에서는 "창"이라는 단어가 대상으로 강조 표시되었으므로 실수를 수정해야 했습니다. 이 실수는 마우스로 단어를 마우스로 가리키고 **레이블 제거** 를 클릭하여 수행됩니다.

![발화 확인 ](images/AzureLabs-Lab3-49.png)
 ![ 레이블 이미지 제거](images/AzureLabs-Lab3-50.png)
 
5.  완전히 잘못된 발화가 발견되면 화면 오른쪽의 삭제 단추를 사용하여 **삭제할** 수 있습니다.

    ![잘못된 발화 삭제](images/AzureLabs-Lab3-51.png)

6.  또는 LUIS가 발화가 올바르게 해석되었다고 생각되면 맞춤 의도에 추가 단추를 사용하여 이해의 **유효성을 검사할** 수 있습니다.

    ![맞춤 의도에 추가](images/AzureLabs-Lab3-52.png)

7.  표시된 모든 발화가 정렬되면 페이지를 다시 로드하여 더 많은 발화가 사용 가능한지 확인합니다.
8.  애플리케이션 이해를 향상시키기 위해 이 프로세스를 가능한 한 여러 번 반복하는 것이 매우 중요합니다. 

**즐거운 시간 보내세요!**

## <a name="your-finished-luis-integrated-application"></a>완성된 LUIS 통합 애플리케이션

축하합니다. Azure Language Understanding Intelligence Service를 활용하여 사용자가 말하는 내용을 이해하고 해당 정보에 대해 조치를 하는 혼합 현실 앱을 빌드했습니다.

![랩 결과](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

이 애플리케이션을 사용하는 동안 Floor 개체를 응시하고 색을 변경하라는 메시지가 표시될 수 있습니다. 애플리케이션이 바닥 색을 변경하지 못하게 하는 방법을 확인할 수 있나요?

### <a name="exercise-2"></a>연습 2

장면의 개체에 대한 추가 기능을 추가하여 LUIS 및 앱 기능을 확장해 보세요. 예를 들어 사용자가 말하는 내용에 따라 응시 적중 지점에서 새 개체를 만든 다음, 기존 명령과 함께 현재 장면 개체와 함께 해당 개체를 사용할 수 있습니다.