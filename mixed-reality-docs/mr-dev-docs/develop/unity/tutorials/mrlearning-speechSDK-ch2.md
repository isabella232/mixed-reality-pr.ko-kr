---
title: 로컬 음성-텍스트 변환을 위한 오프라인 모드 추가
description: 이 과정을 완료하여 혼합 현실 애플리케이션에서 로컬 음성-텍스트 변환을 위해 오프라인 모드를 추가하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, 음성 인식, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 2e7a48dc4bb64eb177e6fa290f4918345c3d642f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590155"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="e5bd8-104">2. 로컬 음성-텍스트 변환에 오프라인 모드 추가</span><span class="sxs-lookup"><span data-stu-id="e5bd8-104">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="e5bd8-105">이 자습서에서는 Azure 음성 인식을 통해 사용자가 정의하는 단어 또는 구에 따라 작업을 수행할 수 있는 명령을 실행하는 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-105">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="e5bd8-106">목표</span><span class="sxs-lookup"><span data-stu-id="e5bd8-106">Objectives</span></span>

* <span data-ttu-id="e5bd8-107">Azure 음성 인식을 사용하여 명령을 실행하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="e5bd8-107">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="e5bd8-108">지침</span><span class="sxs-lookup"><span data-stu-id="e5bd8-108">Instructions</span></span>

<span data-ttu-id="e5bd8-109">[계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **Lunarcom 실행 단어 인식기(스크립트)** 구성 요소를 Lunarcom 개체에 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="e5bd8-110">**실행 단어** 필드에서 적절한 구를 입력합니다(예: _터미널 활성화_).</span><span class="sxs-lookup"><span data-stu-id="e5bd8-110">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="e5bd8-111">**해제 단어** 필드에서 적절한 구(예: _터미널 해제_)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-111">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![Lunarcom 실행 단어 인식기 스크립트 구성 요소가 강조 표시된 Unity 편집기](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="e5bd8-113">Lunarcom 실행 단어 인식기(스크립트) 구성 요소는 MRTK의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-113">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="e5bd8-114">이 자습서의 자산과 함께 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="e5bd8-115">이전 자습서에서와 같이 이제 게임 모드로 들어가면 터미널 패널을 기본적으로 사용하도록 설정되어 있지만, **터미널 해제** 라는 해제 단어를 말하여 터미널 패널을 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-115">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![음성 인식 기능이 사용 중인 재생 모드의 Unity 편집기](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="e5bd8-117">그리고 **터미널 활성화** 라는 실행 단어를 말하여 터미널 패널을 다시 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-117">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![활성 터미널이 있는 재생 모드의 Unity 편집기](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="e5bd8-119">애플리케이션에서 Azure에 연결해야 하므로 컴퓨터/디바이스가 인터넷에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-119">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="e5bd8-120">Azure에 자주 연결할 수 없는 것으로 예상되는 경우 [음성 명령 사용](mr-learning-base-09.md) 지침에 따라 MRTK를 사용하여 음성 명령을 구현할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-120">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Using speech commands](mr-learning-base-09.md) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e5bd8-121">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-121">Congratulations</span></span>

<span data-ttu-id="e5bd8-122">Azure에서 구동하는 음성 명령을 구현했습니다.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-122">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="e5bd8-123">디바이스에서 애플리케이션을 실행하여 기능이 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-123">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="e5bd8-124">다음 자습서에서는 Azure 음성 번역을 사용하여 음성을 번역하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-124">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e5bd8-125">다음 자습서: 3. Azure Cognitive Services 음성 번역 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="e5bd8-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
