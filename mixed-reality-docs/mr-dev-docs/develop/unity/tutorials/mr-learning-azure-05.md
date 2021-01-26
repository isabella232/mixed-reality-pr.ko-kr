---
title: LUIS와 Azure Bot Service 통합
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 Azure Bot Service 및 자연어 이해를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, hololens 2, azure bot service, luis, 자연어, 대화 봇, azure cloud services, azure custom vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 7119dfd54c2b5384ff0e219a494ca8423fe4ebfc
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583380"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="acdca-104">5. Azure Bot Service 통합</span><span class="sxs-lookup"><span data-stu-id="acdca-104">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="acdca-105">이 자습서에서는 **HoloLens 2** 데모 애플리케이션에서 **Azure Bot Service** 를 사용하여 LUIS(Language Understanding)를 추가하고 **추적된 개체** 를 검색할 때 봇에서 사용자를 지원할 수 있도록 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-105">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="acdca-106">이 자습서는 2부로 구성되어 있습니다. 1부에서는 [봇 작성기](/composer/introduction)를 코드프리 솔루션으로 사용하여 봇을 만들고, 필요한 데이터를 봇에 공급하는 Azure Function을 간략히 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-106">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="acdca-107">2부에서는 Unity 프로젝트에서 **BotManager(스크립트)** 를 통해 호스팅된 Bot Service를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-107">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="acdca-108">목표</span><span class="sxs-lookup"><span data-stu-id="acdca-108">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="acdca-109">1부</span><span class="sxs-lookup"><span data-stu-id="acdca-109">Part 1</span></span>

* <span data-ttu-id="acdca-110">Azure Bot Service에 대한 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="acdca-110">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="acdca-111">봇 작성기를 사용하여 봇을 만드는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="acdca-111">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="acdca-112">Azure Function을 사용하여 Azure Storage에서 데이터를 제공하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="acdca-112">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="acdca-113">2부</span><span class="sxs-lookup"><span data-stu-id="acdca-113">Part 2</span></span>

* <span data-ttu-id="acdca-114">이 프로젝트에서 Azure Bot Service를 사용하도록 장면을 설정하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="acdca-114">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="acdca-115">봇과의 대화를 통해 개체를 설정하고 찾는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="acdca-115">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="acdca-116">Azure Bot Service 이해</span><span class="sxs-lookup"><span data-stu-id="acdca-116">Understanding Azure Bot Service</span></span>

<span data-ttu-id="acdca-117">**Azure Bot Service** 를 사용하면 개발자가 **LUIS** 를 통해 사용자와 자연스러운 대화를 유지할 수 있는 인텔리전트 봇을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-117">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="acdca-118">대화형 봇은 사용자가 애플리케이션과 상호 작용할 수 있는 방법을 확장할 수 있는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-118">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="acdca-119">봇은 [LUIS(Language Understanding)](/azure/bot-service/bot-builder-howto-v4-luis?preserve-view=true&tabs=csharp&view=azure-bot-service-4.0) 기능과 정교한 대화를 유지하기 위해 [QnA Maker](/azure/bot-service/bot-builder-howto-qna?preserve-view=true&tabs=cs&view=azure-bot-service-4.0)와 함께 기술 자료 역할을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-119">A Bot can act as a knowledge base with a [QnA Maker](/azure/bot-service/bot-builder-howto-qna?preserve-view=true&tabs=cs&view=azure-bot-service-4.0) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](/azure/bot-service/bot-builder-howto-v4-luis?preserve-view=true&tabs=csharp&view=azure-bot-service-4.0).</span></span>

<span data-ttu-id="acdca-120">[Azure Bot Service](/azure/bot-service/bot-service-overview-introduction?preserve-view=true&view=azure-bot-service-4.0)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="acdca-120">Learn more about [Azure Bot Service](/azure/bot-service/bot-service-overview-introduction?preserve-view=true&view=azure-bot-service-4.0).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="acdca-121">1부 - 봇 만들기</span><span class="sxs-lookup"><span data-stu-id="acdca-121">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="acdca-122">Unity 애플리케이션에서 봇을 사용하려면 먼저 봇을 개발하여 데이터를 제공하고 **Azure** 에서 호스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-122">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="acdca-123">봇의 목표는 데이터베이스에 저장된 *추적된 개체* 의 수를 계산하고, 해당 이름을 기준으로 *추적된 개체* 를 찾고, 사용자에게 이에 대한 몇 가지 기본 정보를 알려주는 기능을 제공하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-123">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="acdca-124">추적된 개체 Azure Function 빠르게 살펴보기</span><span class="sxs-lookup"><span data-stu-id="acdca-124">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="acdca-125">봇 만들기를 시작하지만 유용하게 만들려면 데이터를 가져올 수 있는 리소스를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-125">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="acdca-126">*봇* 에서 **추적된 개체** 의 수를 계산하고 이름을 기준으로 특정 개체를 찾고 세부 정보를 알려줄 수 있으므로 **Azure Table 스토리지** 에 액세스할 수 있는 간단한 Azure Function을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-126">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="acdca-127">추적된 개체 Azure 함수 프로젝트: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) 파일을 하드 드라이브에 다운로드하고 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-127">Download the Tracked Objects Azure Function project: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="acdca-128">이 Azure Function에는 기본 *HTTP* *GET* 호출을 통해 호출할 수 있는 **Count** 및 **Find** 의 두 가지 작업이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-128">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="acdca-129">코드는 **Visual Studio** 에서 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-129">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="acdca-130">[Azure Functions](/azure/azure-functions/functions-overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="acdca-130">Learn more about [Azure Functions](/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="acdca-131">**Count** 함수는 **Table 스토리지** 에서 테이블의 모든 **TrackedObjects** 를 매우 간단하게 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-131">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="acdca-132">반면 **Find** 함수는 *GET* 요청에서 *name* 쿼리 매개 변수를 사용하고, 일치하는 **TrackedObject** 를 **Table 스토리지** 에 쿼리하고, DTO를 JSON으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-132">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="acdca-133">이 **Azure Function** 은 **Visual Studio** 에서 직접 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-133">You can deploy this **Azure Function** directly from **Visual Studio**.</span></span>
<span data-ttu-id="acdca-134">[Azure Function 배포](/azure/devops/pipelines/targets/azure-functions?preserve-view=true&tabs=dotnet-core%2cyaml&view=azure-devops)에서 모든 관련 정보를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="acdca-134">Find here all information regarding [Azure Function deployment](/azure/devops/pipelines/targets/azure-functions?preserve-view=true&tabs=dotnet-core%2cyaml&view=azure-devops).</span></span>

<span data-ttu-id="acdca-135">배포가 완료되면 **Azure Portal** 에서 해당 리소스를 열고, *설정* 섹션 아래에서 **구성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-135">Once you have completed the deployment, in the **Azure Portal**, open the corresponding resource and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="acdca-136">**애플리케이션 설정** 에서 *연결 문자열* 을 **추적된 개체** 가 저장된 **Azure Storage** 에 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-136">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="acdca-137">**새 애플리케이션 설정** 을 클릭하고, 이름에 대해 **AzureStorageConnectionString** 을 사용하며, 값에 대해 올바른 *연결 문자열* 을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-137">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="acdca-138">그런 다음, **저장** 을 클릭합니다. 그러면 **Azure Function** 이 나중에 만들 *봇* 을 지원할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-138">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="acdca-139">대화 봇 만들기</span><span class="sxs-lookup"><span data-stu-id="acdca-139">Creating a conversation Bot</span></span>

<span data-ttu-id="acdca-140">Bot Framework 기반 대화 봇은 여러 가지 방법으로 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-140">There are several ways to develope a Bot Framework based conversational bot.</span></span> <span data-ttu-id="acdca-141">이 단원에서는 빠른 개발을 위한 완벽한 비주얼 디자이너인 [Bot Framework 작성기](/composer/) 데스크톱 애플리케이션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-141">In this lesson you will use the [Bot Framework Composer](/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="acdca-142">최신 릴리스는 [Github 리포지토리](https://github.com/microsoft/BotFramework-Composer/releases)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-142">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="acdca-143">Windows, Mac 및 Linux에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-143">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="acdca-144">**Bot Framework 작성기** 가 설치되면 애플리케이션을 시작하여 다음 인터페이스가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-144">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![Bot Framework Composer 홈](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="acdca-146">이 자습서에 필요한 대화 상자 및 트리거를 제공하는 봇 작성기 프로젝트가 준비되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-146">We have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span> <span data-ttu-id="acdca-147">Bot Framework Composer 프로젝트: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) 파일을 하드 드라이브에 다운로드하고 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-147">Download the Bot Framework Composer project: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="acdca-148">위쪽 메뉴 모음에서 **열기** 를 클릭하고, 다운로드한 **TrackedObjectsBot** 이라는 Bot Framework 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-148">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="acdca-149">프로젝트가 완전히 로드되면 프로젝트가 준비된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-149">After the project is fully loaded, you should see the project ready.</span></span>

![TrackedObjectsBot 프로젝트가 열려 있는 Bot Framework Composer](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="acdca-151">**대화 상자 패널** 을 볼 수 있는 왼쪽에 집중하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-151">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="acdca-152">**TrackedObjectsBot** 이라는 하나의 대화 상자가 있으며, 그 아래에는 여러 개의 **트리거** 가 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-152">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="acdca-153">[Bot Framework 개념](/composer/concept-dialog)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="acdca-153">Learn more about [Bot Framework concepts](/composer/concept-dialog).</span></span>

<span data-ttu-id="acdca-154">이러한 트리거는 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-154">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="acdca-155">Greeting</span><span class="sxs-lookup"><span data-stu-id="acdca-155">Greeting</span></span>

<span data-ttu-id="acdca-156">*사용자* 가 대화를 시작할 때 채팅 *봇* 의 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-156">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![TrackedObjectsBot 프로젝트 대화 상자 트리거 Greeting](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="acdca-158">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="acdca-158">AskingForCount</span></span>

<span data-ttu-id="acdca-159">이 대화 상자는 *사용자* 가 모든 **추적된 개체** 의 수를 계산하도록 요청할 때 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-159">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="acdca-160">트리거 구는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-160">These are the trigger phrases:</span></span>

>* <span data-ttu-id="acdca-161">count me all(모두 계산)</span><span class="sxs-lookup"><span data-stu-id="acdca-161">count me all</span></span>
>* <span data-ttu-id="acdca-162">how many are stored(저장된 수)</span><span class="sxs-lookup"><span data-stu-id="acdca-162">how many are stored</span></span>

![TrackedObjectsBot 프로젝트 대화 상자 트리거 AskForCount](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="acdca-164">[LUIS](/composer/how-to-use-luis)에서 지원하므로 *사용자* 는 이러한 구를 *사용자* 와 자연스럽게 대화할 수 있는 정확한 방법으로 요청할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-164">Thanks to [LUIS](/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="acdca-165">이 대화 상자에서 *봇* 은 **Count** Azure Function과도 통신하며, 나중에 이에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-165">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="acdca-166">Unknown Intent(알 수 없음 의도)</span><span class="sxs-lookup"><span data-stu-id="acdca-166">Unknown Intent</span></span>

<span data-ttu-id="acdca-167">*사용자* 의 입력이 다른 트리거 조건에 맞지 않고 질문을 다시 시도하여 사용자에게 응답하는 경우 이 대화 상자가 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-167">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![TrackedObjectsBot 프로젝트 대화 상자 트리거 Unknown Intent](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="acdca-169">FindEntity</span><span class="sxs-lookup"><span data-stu-id="acdca-169">FindEntity</span></span>

<span data-ttu-id="acdca-170">마지막 대화 상자는 *봇* 메모리에서 데이터를 분기하고 저장함으로써 더 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-170">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="acdca-171">사용자에게 **추적된 개체** 의 *이름* 을 요청하고, **Find** Azure Function에 대한 쿼리를 수행하고, 응답을 사용하여 대화를 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-171">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![TrackedObjectsBot 프로젝트 대화 상자 트리거 FindEntity](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="acdca-173">**추적된 개체** 가 없으면 사용자에게 이를 알리고 대화가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-173">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="acdca-174">문제가 있는 **추적된 개체** 가 있으면 부팅에서 사용 가능한 속성을 확인하고 이를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-174">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="acdca-175">봇 적응</span><span class="sxs-lookup"><span data-stu-id="acdca-175">Adapting the Bot</span></span>

<span data-ttu-id="acdca-176">**AskingForCount** 및 **FindEntity** 트리거에서 백 엔드와 통신해야 합니다. 즉 이전에 배포한 **Azure Function** 의 올바른 URL을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-176">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="acdca-177">대화 상자 패널에서 **AskingForCount** 를 클릭하고 *HTTP 요청 보내기* 작업을 찾습니다. 여기서는 **Count** 함수 엔드포인트에 대한 올바른 URL을 변경해야 하는 **URL** 필드를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-177">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![TrackedObjectsBot 프로젝트 AskingForCount 대화 상자 트리거 엔드포인트 구성](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="acdca-179">마지막으로, **FindEntity** 트리거를 찾고 *HTTP 요청 보내기* 작업을 찾습니다. **URL** 필드에서 URL을 **Find** 함수 엔드포인트로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-179">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![TrackedObjectsBot 프로젝트 FindEntity 대화 상자 트리거 엔드포인트 구성](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="acdca-181">모든 설정이 완료되면 이제 봇을 배포할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-181">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="acdca-182">Bot Framework 작성기가 설치되어 있으므로 여기서 직접 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-182">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="acdca-183">[봇 작성기에서 봇 게시](/composer/how-to-publish-bot)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="acdca-183">Learn more about [Publish a bot from Bot Composer](/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="acdca-184">더 많은 트리거 구, 새 응답 또는 대화 분기를 추가하여 봇을 자유롭게 재생해 보세요.</span><span class="sxs-lookup"><span data-stu-id="acdca-184">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="acdca-185">2부 - Unity에 모든 항목 배치</span><span class="sxs-lookup"><span data-stu-id="acdca-185">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="acdca-186">장면 준비</span><span class="sxs-lookup"><span data-stu-id="acdca-186">Preparing the scene</span></span>

<span data-ttu-id="acdca-187">[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** 폴더로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-187">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![ChatBotManager 프리팹이 선택된 Unity 프로젝트 창](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="acdca-189">여기서 **ChatBotManager** 프리팹을 [계층 구조] 장면으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-189">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="acdca-190">ChatBotManager가 장면에 추가되면 **채팅 봇 관리자** 구성 요소를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-190">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="acdca-191">[검사기]에서 입력해야 하는 빈 **Direct Line 비밀 키** 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-191">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="acdca-192">Azure Portal에서 이 자습서의 1부에서 만든 **봇 채널 등록** 형식의 리소스를 찾아서 *비밀 키* 를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-192">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![새로 추가된 ChatBotManager 프리팹이 여전히 선택된 Unity](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="acdca-194">이제 **ChatBotManager** 개체를 **ChatBotPanel** 개체에 연결된 **ChatBotController** 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-194">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="acdca-195">[계층 구조]에서 **ChatBotPanel** 을 선택합니다. 그러면 빈 **채팅 봇 관리자** 필드가 표시됩니다. **ChatBotManager** 개체를 [계층 구조]에서 빈 **채팅 봇 관리자** 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-195">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![ChatBotPanel이 구성된 Unity](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="acdca-197">다음으로, 사용자가 상호 작용할 수 있도록 **ChatBotPanel** 을 여는 방법이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-197">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="acdca-198">[장면] 창에서 **MainMenu** 개체에 *채팅 봇* 사이드 단추가 있음을 알 수 있습니다. 이 단추는 이 문제를 해결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-198">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="acdca-199">[계층 구조]에서 **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** 을 차례로 찾고, [검사기]에서 *ButtonConfigHelper* 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-199">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="acdca-200">**OnClick()** 이벤트 콜백에 빈 슬롯이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-200">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="acdca-201">**ChatBotPanel** 을 이벤트 슬롯으로 끌어서 놓고, 드롭다운 목록에서 *GameObject* 를 탐색한 다음, 하위 메뉴에서 *SetActive(부울)* 를 선택하고, 확인란을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-201">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![ButtonChatBot이 구성된 Unity](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="acdca-203">이제 주 메뉴에서 채팅 봇을 확인할 수 있으며, 해당 장면을 사용할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-203">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="acdca-204">테스트에 봇 배치</span><span class="sxs-lookup"><span data-stu-id="acdca-204">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="acdca-205">추적된 개체 수 요청</span><span class="sxs-lookup"><span data-stu-id="acdca-205">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="acdca-206">먼저 데이터베이스에 저장된 **추적된 개체** 의 수를 봇에 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-206">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="acdca-207">*텍스트 음성 변환* 과 같은 서비스를 사용하지 못할 수 있으므로 이번에는 HoloLens 2에서 애플리케이션을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-207">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="acdca-208">HoloLens 2에서 애플리케이션을 실행하고, 주 메뉴 옆에 있는 *채팅 봇* 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-208">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="acdca-209">봇에서 인사말을 보내면 이제 **개체의 수가 얼마나 되나요?** 라고 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-209">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="acdca-210">수량을 알려주고 대화가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-210">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="acdca-211">추적된 개체 요청</span><span class="sxs-lookup"><span data-stu-id="acdca-211">Asking about a tracked object</span></span>

<span data-ttu-id="acdca-212">이제 애플리케이션을 다시 실행하고, 이번에는 **추적된 개체 찾기** 를 요청합니다. 그러면 봇에서 사용자에게 "car"로 응답해야 하는 이름 또는 데이터베이스에 있는 것으로 확인된 다른 *추적된 개체* 의 이름을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-212">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="acdca-213">봇에서 설명 및 공간 앵커가 지정되어 있는지 여부와 같은 세부 정보를 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-213">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="acdca-214">존재하지 않는 **추적된 개체** 를 요청하고 봇에서 응답하는 방법을 확인해 보세요.</span><span class="sxs-lookup"><span data-stu-id="acdca-214">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="acdca-215">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-215">Congratulations</span></span>

<span data-ttu-id="acdca-216">이 자습서에서는 Azure Bot Framework를 사용하여 자연어 대화를 통해 애플리케이션과 상호 작용하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-216">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="acdca-217">사용자 고유의 봇을 개발하는 방법과 이를 실행할 수 있도록 하기 위해 이동한 모든 요소를 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-217">You learned how to develop your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="acdca-218">결론</span><span class="sxs-lookup"><span data-stu-id="acdca-218">Conclusion</span></span>

<span data-ttu-id="acdca-219">이 자습서 시리즈의 과정을 통해 **Azure 클라우드 서비스** 에서 새롭고 흥미로운 기능을 애플리케이션에 제공하는 방법을 경험했습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-219">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="acdca-220">이제 **Azure Storage** 를 사용하여 데이터와 이미지를 클라우드에 저장하고, **Azure Custom Vision** 을 사용하여 이미지를 연결하고 모델을 학습시키며, **Azure Spatial Anchors** 를 사용하여 개체를 로컬 컨텍스트에 가져오고, **LUIS에서 구동하는 Azure Bot Framework** 를 구현하여 새롭고 자연스러운 상호 작용 패턴에 적합한 대화형 봇을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acdca-220">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>