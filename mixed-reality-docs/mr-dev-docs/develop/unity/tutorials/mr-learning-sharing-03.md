---
title: 여러 사용자 연결
description: 이 과정을 완료하여 HoloLens 2 혼합 현실 애플리케이션에서 여러 사용자를 연결하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, 다중 사용자 기능, Photon, MRTK, mixed reality toolkit, UWP, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: ba8a29844489a9153f970f6e39ff2022701c845711ffd9abc232d8da8eeb2e32
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200739"
---
# <a name="3-connecting-multiple-users"></a>3. 여러 사용자 연결

이 자습서에서는 라이브 공유 환경의 일부로 여러 사용자를 연결하는 방법을 알아봅니다. 자습서를 마치면 여러 디바이스에서 앱을 실행하여 각 사용자가 다른 사용자의 아바타가 움직이는 것을 실시간으로 보게 할 수 있습니다.

## <a name="objectives"></a>목표

* 공유 환경에서 여러 사용자를 연결하는 방법 알아보기

## <a name="preparing-the-scene"></a>장면 준비

이 섹션에서는 자습서 프리팹 중 일부를 추가하여 장면을 준비합니다.

Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** 폴더로 이동한 다음, 다음과 같은 프리팹을 클릭하고 Hierarchy 창으로 끌어서 장면에 추가합니다.

* **NetworkLobby** 프리팹
* **SharedPlayground** 프리팹

![새로 추가한 NetworkLobby 및 SharedPlayground 프리팹이 선택된 Unity](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

Project 창에서 **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** 폴더로 이동한 다음, 다음과 같은 프리팹을 클릭하고 Hierarchy 창으로 끌어서 장면에 추가합니다.

* **DebugWindow** 프리팹

![새로 추가한 DebugWindow 프리팹이 선택된 Unity](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>사용자 프리팹을 인스턴스화하도록 PUN 구성

이 섹션에서는 PhotonUser 프리펩을 사용하도록 프로젝트를 구성합니다.

Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** 폴더로 이동합니다.

Hierarchy 창에서 **NetworkLobby** 개체를 펼쳐서 **NetworkRoom** 자식 개체를 선택한 다음, Inspector 창에서 **Photon Room (Script)** 구성 요소를 찾아서 다음과 같이 구성합니다.

* **Photon User Prefab** 필드에 Resources 폴더의 **PhotonUser** 프리팹을 할당합니다.

![Photon Room 구성 요소가 부분적으로 구성된 Unity](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>여러 사용자 환경 체험

Unity 프로젝트를 빌드하고 HoloLens에 배포했으면 Unity로 돌아가서 HoloLens에서 앱이 실행되는 동안 게임 모드로 들어갑니다. 머리(HoloLens)를 움직이면 HoloLens 사용자 아바타가 움직이는 것을 볼 수 있습니다.

![네트워크 사용자를 사용하여 Unity를 보여주는 애니메이션](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 앱 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.

> [!CAUTION]
> 앱에서 Photon에 연결해야 하므로 컴퓨터/디바이스가 인터넷에 연결되어 있는지 확인합니다.

## <a name="congratulations"></a>축하합니다.

여러 사용자가 동일한 환경에 연결하여 서로의 움직임을 볼 수 있도록 프로젝트를 구성하는 데 성공했습니다. 다음 자습서에서는 개체의 움직임도 여러 디바이스에서 공유되도록 기능을 구현합니다.

> [!div class="nextstepaction"]
> [다음 자습서: 4. 여러 사용자와 개체 이동 공유](mr-learning-sharing-04.md)
