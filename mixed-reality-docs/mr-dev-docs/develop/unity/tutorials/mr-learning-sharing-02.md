---
title: Photon Unity 네트워킹 설정
description: 이 과정을 완료하여 HoloLens 2 혼합 현실 애플리케이션에서 Photon Unity Network를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, 다중 사용자 기능, Photon, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, PUN
ms.localizationpriority: high
ms.openlocfilehash: 28776e106b96d1265e435d60e7008b1d88c01060
ms.sourcegitcommit: cf8df1720ddb8236207ab581bc149edcc76e6199
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2021
ms.locfileid: "114702508"
---
# <a name="2-setting-up-photon-unity-networking"></a>2. Photon Unity 네트워킹 설정

이 자습서에서는 PUN(Photon Unity Networking)을 사용하여 공유 환경을 만들기 위해 준비합니다. PUN 앱을 만들고 PUN 자산을 Unity 프로젝트로 가져오고 Unity 프로젝트를 PUN 앱에 연결하는 방법을 알아봅니다.

## <a name="objectives"></a>목표

* PUN 앱을 만드는 방법 알아보기
* PUN 자산을 찾아서 가져오는 방법 알아보기
* Unity 프로젝트를 PUN 앱에 연결하는 방법 알아보기

## <a name="creating-and-preparing-the-unity-project"></a>Unity 프로젝트 만들기 및 준비

이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.

먼저 [프로젝트 초기화 및 첫 번째 애플리케이션 배포](mr-learning-base-02.md)를 수행합니다. 단, [개체에 손 상호 작용 추가](mr-learning-base-02.md#adding-hand-interaction-to-an-object) 및 [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.

1. [Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정
2. [빌드 플랫폼 전환](mr-learning-base-02.md#switching-the-build-platform)
3. [TextMeshPro 필수 리소스 가져오기](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Mixed Reality Toolkit 가져오기 및 Unity 프로젝트 구성](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [장면 만들기 및 MRTK 구성](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) 및 장면에 적절한 이름(예: *MultiUserCapabilities*) 지정

그런 다음, [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 다음을 수행합니다.

1. **MRTK 구성 프로필** 을 **DefaultHoloLens2ConfigurationProfile** 로 변경
1. **공간 인식 메시 표시 옵션** 을 **폐색** 으로 변경

## <a name="enabling-additional-capabilities"></a>추가 기능 사용

Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 차례로 선택하여 [플레이어 설정] 창을 연 다음, **플레이어** >  **게시 설정** 섹션을 차례로 찾습니다.

![Unity Player 설정](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

**게시 설정** 에서 **기능** 섹션까지 아래로 스크롤하여 위의 [Unity 프로젝트 구성](mr-learning-base-02.md#configuring-the-unity-project) 단계 중에 사용하도록 설정한 **InternetClient**, **Microphone**, **SpatialPerception** 및 **GazeInput** 기능이 사용하도록 설정되어 있는지 다시 확인합니다.

그런 다음, 다음과 같은 추가 기능을 사용하도록 설정합니다.

* **InternetClientServer** 기능
* **PrivateNetworkClientServer** 기능

![Unity Capabilities 설정](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>자습서 자산 가져오기

AzurespatialAnchors SDK V2.7.1을 Unity 프로젝트에 추가합니다. 패키지를 추가하려면 이 [자습서](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)를 따르세요.


다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.
 
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.7.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.7.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.7.2.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.7.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.7.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.7.2.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.7.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.7.2/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.7.2.unitypackage)

자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.

![자습서 자산을 가져온 후의 Unity 계층 구조, 장면 및 프로젝트 창](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [자습서 자산 가져오기](mr-learning-base-04.md#importing-the-tutorial-assets) 지침을 참조할 수 있습니다.

> [!NOTE]
> MultiUserCapabilities 자습서 자산 패키지를 가져오면 유형 또는 네임스페이스가 누락되었음을 나타내는 [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246) 오류가 Console 창에 보입니다. 이것은 예상한 오류이며, 다음 섹션에서 PUN 자산을 가져오면 해결됩니다.

## <a name="importing-the-pun-assets"></a>PUN 자산 가져오기

Unity 메뉴에서 **Window** > **Asset Store** 를 선택하여 Asset Store 창을 열고 Exit Games에서 **PUN 2 - FREE** 를 검색하여 선택하고, **Download** 단추를 클릭하여 자산 패키지를 Unity 계정에 다운로드합니다.

다운로드가 완료되면 **Import** 단추를 클릭하여 Import Unity Package 창을 엽니다.

![PUN 2가 있는 Unity Asset Store - 무료](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.

![PUN 2 가져오기 창이 있는 Unity](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

Unity에서 Import(가져오기) 프로세스가 완료되면 Pun Wizard 창이 PUN Setup 메뉴가 로드된 상태로 나타납니다. 지금은 이 창을 무시하거나 닫으면 됩니다.

![PUN Setup 창이 있는 Unity](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a>PUN 애플리케이션 만들기

이 섹션에서는 Photon 계정이 없으면 만들고 새 PUN 앱을 만듭니다.

Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">대시보드</a>로 이동하여 로그인하고(사용할 계정이 있는 경우) 그렇지 않으면 **Create One** 링크를 클릭하여 지침에 따라 새 계정을 등록합니다.

![Photon 로그인 페이지](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

로그인되면 **Create a New App** 단추를 클릭합니다.

![Photon 대시보드 시작 페이지](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

Create a New Application(새 애플리케이션 만들기) 페이지에서 다음 값을 입력합니다.

* Photon 유형의 경우 PUN을 선택합니다.
* 이름에는 적절한 이름(예: _MRTK Tutorials_)을 입력합니다.
* 설명에는 적절한 설명(선택 사항)을 입력합니다.
* URL 필드는 비워둡니다.

그런 다음, **만들기** 단추를 클릭하여 새 앱을 만듭니다.

![Photon 애플리케이션 페이지 만들기](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

Photon에서 만들기 프로세스가 완료되면 새 PUN 앱이 대시보드에 나타납니다.

![Photon 애플리케이션 페이지](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>Unity 프로젝트를 PUN 애플리케이션에 연결

이 섹션에서는 Unity 프로젝트를 이전 섹션에서 만든 PUN 앱에 연결합니다.

Photon 대시보드에서 **App ID** 필드를 클릭하고 앱 ID 필드를 표시하여 클립보드에 복사합니다.

![App ID가 선택된 Photon 애플리케이션 페이지](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

Unity 메뉴에서 **Window** > **Photon Unity Networking** > **PUN Wizard** 를 선택하여 Pun Wizard 창을 열고 **Setup Project** 창을 클릭하여 PUN Setup 메뉴를 열어서 다음과 같이 구성합니다.

* **AppId or Email** 필드에 이전 단계에서 복사한 PUN App ID를 붙여넣습니다.

그런 다음, **Setup Project** 단추를 클릭하여 App ID를 적용합니다.

![App ID가 채워진 Unity PUN Setup 창](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

Unity에서 PUN 설정 프로세스가 완료되면 PUN Setup 메뉴에 **Done!** 이라는 메시지가 표시되고 Project 창에 **PhotonServerSettings** 자산이 자동으로 선택되고 해당 속성이 Inspector 창에 표시됩니다.

![Setup Project가 적용된 Unity PUN Setup 창](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a>축하합니다.

PUN 앱을 만들어서 Unity 프로젝트에 연결하는 데 성공했습니다. 다음 단계에서는 여러 사용자가 서로 볼 수 있도록 다른 사용자와 연결을 허용할 수 있습니다.

> [!div class="nextstepaction"]
> [다음 자습서: 3. 여러 사용자 연결](mr-learning-sharing-03.md)