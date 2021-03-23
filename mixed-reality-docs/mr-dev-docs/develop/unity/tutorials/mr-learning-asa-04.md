---
title: Azure Spatial Anchor 피드백 표시
description: 이 과정을 완료하여 혼합 현실 애플리케이션에서 Azure Spatial Anchors의 피드백을 표시하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, 세션, 피드백 요소
ms.localizationpriority: high
ms.openlocfilehash: f5f92d8b19da6a449b8630d7f87e0719e438b4ab
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590675"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a><span data-ttu-id="c53f8-104">4. Azure Spatial Anchor에서 피드백 표시</span><span class="sxs-lookup"><span data-stu-id="c53f8-104">4. Displaying feedback from Azure Spatial Anchors</span></span>

<span data-ttu-id="c53f8-105">이 자습서에서는 ASA(Azure Spatial Anchors)를 사용하여 사용자에게 앵커 검색, 이벤트 및 상태에 대한 피드백을 제공하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-105">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="c53f8-106">목표</span><span class="sxs-lookup"><span data-stu-id="c53f8-106">Objectives</span></span>

* <span data-ttu-id="c53f8-107">현재 ASA 세션에 대한 필수 정보를 표시하는 UI 패널을 설정하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="c53f8-107">Learn how to set up a UI panel that displays essential information about the current ASA session</span></span>
* <span data-ttu-id="c53f8-108">사용자가 ASA SDK를 사용할 수 있도록 하는 피드백 요소 알아보기 및 살펴보기</span><span class="sxs-lookup"><span data-stu-id="c53f8-108">learn about and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="setting-up-asa-feedback-panel"></a><span data-ttu-id="c53f8-109">ASA 피드백 패널 설정</span><span class="sxs-lookup"><span data-stu-id="c53f8-109">Setting up ASA feedback panel</span></span>

<span data-ttu-id="c53f8-110">Hierarchy 창에서 **명령** > **TextContent** 개체를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-110">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object.</span></span> <span data-ttu-id="c53f8-111">**3D 개체** > **텍스트 - TextMeshPro** 를 선택하여 TextMeshPro 텍스트 개체를 명령 > TextContent 개체의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-111">Select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object:</span></span>

![새로 만든 TextMeshPro 개체가 선택된 Unity](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="c53f8-113">장면 작업을 더 쉽게 수행할 수 있도록 개체 왼쪽의 눈 아이콘을 클릭하여 ParentAnchor 개체에 대한 <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">장면 표시 유형</a>을 끄기로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="c53f8-114">이렇게 하면 게임 내 표시 유형을 변경하지 않고 [장면] 창에서 개체를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="c53f8-115">새로 만든 텍스트(TMP) 개체 **Feedback** 의 이름을 바꾼 다음, Inspector 창에서 명령 텍스트 아래에 깔끔하게 배치되도록 위치와 크기를 변경합니다. 예를 들어 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-115">Rename the newly created Text (TMP) object **Feedback**, then, in the Inspector window, change its position and size, so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="c53f8-116">사각형 변환 구성 요소의 **세로 위치** 를 -0.24로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-116">Change the Rect Transform component's **Pos Y** to -0.24.</span></span>
* <span data-ttu-id="c53f8-117">사각형 변환 구성 요소의 **너비** 를 0.555로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-117">Change the Rect Transform component's **Width** to 0.555.</span></span>
* <span data-ttu-id="c53f8-118">사각형 변환 구성 요소의 **높이** 를 0.1로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-118">Change the Rect Transform component's **Height** to 0.1.</span></span>

<span data-ttu-id="c53f8-119">그런 다음, 텍스트가 텍스트 영역 내에 깔끔하게 맞추도록 글꼴 속성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-119">Then choose font properties, so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="c53f8-120">TextMeshPro - 텍스트 구성 요소의 **글꼴 스타일** 을 굵게로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-120">Change the TextMeshPro - Text component's **Font Style** to Bold.</span></span>
* <span data-ttu-id="c53f8-121">TextMeshPro - 텍스트 구성 요소의 **글꼴 크기** 를 0.17로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-121">Change the TextMeshPro - Text component's **Font Size** to 0.17.</span></span>
* <span data-ttu-id="c53f8-122">TextMeshPro - 텍스트 구성 요소의 **맞춤** 을 가운데 및 중간으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-122">Change the TextMeshPro - Text component's **Alignment** to Center and Middle.</span></span>

![Feedback 개체가 구성된 Unity](images/mr-learning-asa/asa-04-section1-step1-2.png)

<span data-ttu-id="c53f8-124">Hierarchy 창에서 **Feedback** 개체를 선택한 다음, Inspector 창에서 **구성 요소 추가** 단추를 사용하여 **Anchor Feedback Script(스크립트)** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-124">In the Hierarchy window, select the **Feedback** object still, then in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="c53f8-125">**Feedback** 개체 자체를 **Anchor Feedback Script(스크립트)** 구성 요소의 **피드백 텍스트** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-125">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field.</span></span>

![Anchor Feedback Script 구성 요소가 구성된 Unity](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="c53f8-127">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-127">Congratulations</span></span>

<span data-ttu-id="c53f8-128">이 자습서에서는 UI 패널을 만드는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-128">In this tutorial, you learned how to create a UI panel.</span></span> <span data-ttu-id="c53f8-129">사용자에게 실시간 피드백을 제공하기 위한 Azure Spatial Anchors 환경의 현재 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c53f8-129">It displays the current status of the Azure Spatial Anchors experience for providing users with real-time feedback.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c53f8-130">다음 자습서: 5. Android 및 iOS용 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c53f8-130">Next Tutorial: 5. Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)
