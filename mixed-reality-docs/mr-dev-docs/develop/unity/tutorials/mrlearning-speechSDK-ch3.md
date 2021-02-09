---
title: Azure Cognitive Services 음성 번역 구성 요소 추가
description: 이 과정에서는 혼합 현실 애플리케이션에서 Azure Cognitive Services 음성 번역을 추가하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, 음성 인식, Windows 10, 음성 번역
ms.localizationpriority: high
ms.openlocfilehash: bcc966b63f4c3e5bb9e6d6a38dc7f0312b288402
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590145"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="c7a48-104">3. Azure Cognitive Services 음성 번역 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="c7a48-104">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="c7a48-105">이 자습서에서는 음성 번역을 프로젝트에 추가하여 음성을 세 가지 언어로 번역하고 전사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7a48-105">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="c7a48-106">목표</span><span class="sxs-lookup"><span data-stu-id="c7a48-106">Objectives</span></span>

* <span data-ttu-id="c7a48-107">Azure 음성 번역을 통합하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="c7a48-107">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="c7a48-108">지침</span><span class="sxs-lookup"><span data-stu-id="c7a48-108">Instructions</span></span>

<span data-ttu-id="c7a48-109">[계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **Lunarcom 번역 인식기(스크립트)** 구성 요소를 Lunarcom 개체에 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c7a48-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="c7a48-110">**대상 언어** 를 선택한 언어(예: _독일어_)로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c7a48-110">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="c7a48-112">Lunarcom 번역 인식기(스크립트) 구성 요소는 MRTK의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c7a48-112">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="c7a48-113">이 자습서의 자산과 함께 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7a48-113">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="c7a48-114">이제 게임 모드로 들어가면 먼저 위성 단추를 눌러 음성 번역을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7a48-114">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="c7a48-115">그런 다음, 마이크가 컴퓨터에 있다고 가정하여 사용자가 무언가를 말하면 음성이 선택한 언어로 번역되어 터미널 패널에 전사됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7a48-115">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="c7a48-117">애플리케이션에서 Azure에 연결해야 하므로 컴퓨터/디바이스가 인터넷에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c7a48-117">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="c7a48-118">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="c7a48-118">Congratulations</span></span>

<span data-ttu-id="c7a48-119">이제 프로젝트에서 사용자가 말하는 단어를 여러 다른 언어로 성공적으로 번역할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7a48-119">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="c7a48-120">디바이스에서 애플리케이션을 실행하여 기능이 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c7a48-120">Run the application on your device to ensure the feature is working properly.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c7a48-121">다음 자습서: 4. 의도 및 자연어 이해 설정</span><span class="sxs-lookup"><span data-stu-id="c7a48-121">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
