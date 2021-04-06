---
title: 음성 명령 사용
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 앱에서 음성 명령을 설정하고 만들고 사용하는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, 음성 명령, 음성 입력
ms.localizationpriority: high
ms.openlocfilehash: 3aea23d5a259e555f47ca9ea41d77f345c977aeb
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982947"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="e7c7a-104">9. 음성 명령 사용</span><span class="sxs-lookup"><span data-stu-id="e7c7a-104">9. Using speech commands</span></span>

<span data-ttu-id="e7c7a-105">이 자습서에서는 음성 명령을 만드는 방법과 전역적으로 제어하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-105">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="e7c7a-106">음성 명령을 제어하는 개체를 사용자가 쳐다봐야 하는 로컬 음성 명령을 제어하는 방법에 대해서도 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-106">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="e7c7a-107">목표</span><span class="sxs-lookup"><span data-stu-id="e7c7a-107">Objectives</span></span>

* <span data-ttu-id="e7c7a-108">음성 명령을 만드는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="e7c7a-108">Learn how to create speech commands</span></span>
* <span data-ttu-id="e7c7a-109">전역적으로 및 로컬에서 음성 명령을 제어하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="e7c7a-109">Learn how to control speech commands globally and locally</span></span>

[!INCLUDE[](includes/ensuring-microphone-capabality.md)]

## <a name="creating-speech-commands"></a><span data-ttu-id="e7c7a-110">음성 명령 만들기</span><span class="sxs-lookup"><span data-stu-id="e7c7a-110">Creating speech commands</span></span>

<span data-ttu-id="e7c7a-111">Hierarchy(계층 구조) 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector(인스펙터) 창에서 MixedRealityToolkit > **입력** 탭을 선택하고 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-111">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="e7c7a-112">**Speech**(음성) 섹션 펼치기</span><span class="sxs-lookup"><span data-stu-id="e7c7a-112">Expand the **Speech** section</span></span>
* <span data-ttu-id="e7c7a-113">**DefaultMixedRealitySpeechCommandsProfile** 을 복제하여 적절한 이름(예: _GettingStarted_MixedRealitySpeechCommandsProfile_)을 지정</span><span class="sxs-lookup"><span data-stu-id="e7c7a-113">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="e7c7a-114">**Start Behaviour**(동작 시작)가 **Auto Start**(자동 시작)로 설정되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="e7c7a-114">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![음성 명령 만들기](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="e7c7a-116">MRTK 프로필을 복제하는 방법은 [MRTK 프로필 구성](mr-learning-base-03.md) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-116">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="e7c7a-117">Speech(음성) > **Speech Commands**(음성 명령) 섹션에서 **+ Add a New Speech Command**(새 음성 명령 추가) 단추를 4번 클릭하여 새 음성 명령 4개를 기존 음성 명령 목록에 추가한 다음, **키워드** 필드에 다음 문구를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-117">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="e7c7a-118">Enable Indicator(표시기 사용)</span><span class="sxs-lookup"><span data-stu-id="e7c7a-118">Enable Indicator</span></span>
* <span data-ttu-id="e7c7a-119">Enable Tap to Place(탭하여 위치 지정 사용)</span><span class="sxs-lookup"><span data-stu-id="e7c7a-119">Enable Tap to Place</span></span>
* <span data-ttu-id="e7c7a-120">Enable Bounds Control(범위 제어 사용)</span><span class="sxs-lookup"><span data-stu-id="e7c7a-120">Enable Bounds Control</span></span>
* <span data-ttu-id="e7c7a-121">Disable Bounds Control(범위 제어 사용 안 함)</span><span class="sxs-lookup"><span data-stu-id="e7c7a-121">Disable Bounds Control</span></span>

![새 음성 명령 추가](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="e7c7a-123">컴퓨터에 마이크가 없는 경우 음성 명령에 KeyCode를 할당하면 해당 키를 누를 때 명령을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-123">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="e7c7a-124">음성 명령 제어</span><span class="sxs-lookup"><span data-stu-id="e7c7a-124">Controlling speech commands</span></span>

<span data-ttu-id="e7c7a-125">Project 창에서 **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** 폴더로 이동하여 도구 설명 프리팹을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-125">In the Project window, navigate to the **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![도구 설명 폴더 열기](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="e7c7a-127">Hierarchy(계층 구조) 창에서 빈 지점을 마우스 오른쪽 단추로 클릭하고, **Create Empty**(빈 개체 생성)를 선택하여 빈 개체를 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-127">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="e7c7a-128">개체 이름을 **SpeechInputHandler_Global** 로 지정한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 **SpeechInputHandler** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-128">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="e7c7a-129">음성 명령을 트리거하기 위해 SpeechInputHandler 구성 요소가 있는 개체를 사용자가 쳐다보지 않아도 되도록, **Is Focus Required**(포커스 필요) 확인란을 **선택 취소**</span><span class="sxs-lookup"><span data-stu-id="e7c7a-129">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="e7c7a-130">음성 명령이 인식될 때 프리팹이 나타나도록, 프로젝트 창에서 **SpeechConfirmation Tooltip** 프리팹을 **Speech Confirmation Tooltip Prefab**(음성 확인 도구 설명 프리팹) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="e7c7a-130">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![음성 입력 처리기 구성 요소 구성](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="e7c7a-132">SpeechInputHandler 구성 요소에서 작은 **+** 아이콘을 3번 클릭하여 키워드 요소를 3개 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-132">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![음성 입력 처리기에 키워드 요소 추가](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="e7c7a-134">**Element 0**(요소 0)을 펼치고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-134">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="e7c7a-135">이전 섹션에서 만든 Enable Indicator(표시기 사용) 음성 명령을 참조하도록 **키워드** 필드에 **Enable Indicator**(표시기 사용)를 입력</span><span class="sxs-lookup"><span data-stu-id="e7c7a-135">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="e7c7a-136">작은 **+** 아이콘을 클릭하여 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="e7c7a-136">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="e7c7a-137">Hierarchy(계층 구조) 창에서 **Indicator**(표시기) 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="e7c7a-137">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e7c7a-138">**No Function**(함수 없음) 드롭다운에서 **GameObject** > **SetActive (bool)** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="e7c7a-138">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="e7c7a-139">인수 확인란이 **선택** 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="e7c7a-139">Check the argument checkbox, so it is **checked**</span></span>

![키워드 요소 0 구성](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="e7c7a-141">**Element 1**(요소 1)을 펼치고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-141">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="e7c7a-142">이전 섹션에서 만든 Enable Bounds Box(경계 상자 사용) 명령을 참조하도록 **키워드** 필드에 **Enable Bounds Box**(경계 상자 사용)를 입력</span><span class="sxs-lookup"><span data-stu-id="e7c7a-142">In the **Keyword** field, enter **Enable Bounds Control**, to reference the Enable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="e7c7a-143">작은 **+** 아이콘을 클릭하여 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="e7c7a-143">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="e7c7a-144">Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="e7c7a-144">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e7c7a-145">**No Function**(함수 없음) 드롭다운에서 **BoundsControl** > **bool enabled** 를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="e7c7a-145">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e7c7a-146">인수 확인란이 **선택** 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="e7c7a-146">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="e7c7a-147">작은 **+** 아이콘을 클릭하여 또 다른 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="e7c7a-147">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="e7c7a-148">Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="e7c7a-148">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e7c7a-149">**No Function**(함수 없음) 드롭다운에서 **ObjectManipulator** > **bool enabled** 를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="e7c7a-149">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e7c7a-150">인수 확인란이 **선택** 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="e7c7a-150">Check the argument checkbox, so it is **checked**</span></span>

![키워드 요소 1 구성](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="e7c7a-152">**Element 2**(요소 2)를 펼치고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-152">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="e7c7a-153">이전 섹션에서 만든 Disable Bounds Box(경계 상자 사용 안 함) 명령을 참조하도록 **키워드** 필드에 **Disable Bounds Box**(경계 상자 사용 안 함)를 입력</span><span class="sxs-lookup"><span data-stu-id="e7c7a-153">In the **Keyword** field, enter **Disable Bounds Control**, to reference the Disable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="e7c7a-154">작은 **+** 아이콘을 클릭하여 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="e7c7a-154">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="e7c7a-155">Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="e7c7a-155">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e7c7a-156">**No Function**(함수 없음) 드롭다운에서 **BoundsControl** > **bool enabled** 를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="e7c7a-156">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e7c7a-157">인수 확인란이 **선택 취소** 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="e7c7a-157">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="e7c7a-158">작은 **+** 아이콘을 클릭하여 또 다른 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="e7c7a-158">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="e7c7a-159">Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="e7c7a-159">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e7c7a-160">**No Function**(함수 없음) 드롭다운에서 **ObjectManipulator** > **bool enabled** 를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="e7c7a-160">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e7c7a-161">인수 확인란이 **선택 취소** 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="e7c7a-161">Verify that the argument checkbox is **unchecked**</span></span>

![키워드 요소 2 구성](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="e7c7a-163">Hierarchy(계층 구조) 창에서 RoverExplorer > **RoverAssembly** 개체를 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 **SpeechInputHandler** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-163">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="e7c7a-164">음성 명령을 트리거하기 위해 SpeechInputHandler 구성 요소(예: RoverAssembly)가 있는 개체를 사용자가 쳐다봐야 하도록, **Is Focus Required**(포커스 필요) 확인란을 **선택**</span><span class="sxs-lookup"><span data-stu-id="e7c7a-164">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="e7c7a-165">음성 명령이 인식될 때 프리팹이 나타나도록, 프로젝트 창에서 **SpeechConfirmation Tooltip** 프리팹을 **Speech Confirmation Tooltip Prefab**(음성 확인 도구 설명 프리팹) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="e7c7a-165">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Rover 어셈블리에 음성 입력 처리기 추가](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="e7c7a-167">SpeechInputHandler 구성 요소에서 작은 **+** 아이콘을 클릭하여 키워드 요소를 추가하고 새로 만든 요소를 펼친 후, 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-167">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="e7c7a-168">이전 섹션에서 만든 Enable Tap to Place(탭하여 위치 지정 사용) 명령을 참조하도록 **키워드** 필드에 **Enable Tap to Place**(탭하여 위치 지정 사용)를 입력</span><span class="sxs-lookup"><span data-stu-id="e7c7a-168">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="e7c7a-169">작은 **+** 아이콘을 클릭하여 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="e7c7a-169">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="e7c7a-170">Hierarchy(계층 구조) 창에서 개체 자체(즉, 동일한 **RoverAssembly** 개체)를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="e7c7a-170">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="e7c7a-171">**No Function**(함수 없음) 드롭다운에서 **TapToPlace** > **bool enabled** 를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="e7c7a-171">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="e7c7a-172">인수 확인란이 **선택** 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="e7c7a-172">Check the argument checkbox, so it is **checked**</span></span>

![Rover 어셈블리에서 음성 입력 처리기 구성](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="e7c7a-174">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-174">Congratulations</span></span>

<span data-ttu-id="e7c7a-175">이 자습서에서는 음성 명령을 만드는 방법과 전역적으로 제어하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-175">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="e7c7a-176">음성 명령을 제어하는 개체를 사용자가 쳐다봐야 하는 로컬 음성 명령을 제어하는 방법에 대해서도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-176">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="e7c7a-177">이것으로 [시작 자습서](mr-learning-base-01.md) 시리즈를 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-177">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="e7c7a-178">이 자습서를 통해 MRTK를 사용하여 처음부터 완전 혼합 현실 경험을 성공적으로 구축했습니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-178">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="e7c7a-179">다음 두 가지 자습서 시리즈인 [Azure Spatial Anchors 자습서](mr-learning-asa-01.md) 및 [다중 사용자 기능 자습서](mr-learning-sharing-01.md)에서는 먼저 Azure Spatial Anchors를 프로젝트에 통합하여 직접 만든 Rover Explorer 경험을 실제 세계에서 고정하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-179">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="e7c7a-180">그런 다음, 다중 사용자 기능을 프로젝트에 추가하여 사용자와 개체 움직임을 실시간으로 공유하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-180">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="e7c7a-181">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="e7c7a-181">Next Development Checkpoint</span></span>

<span data-ttu-id="e7c7a-182">앞서 설명한 Unity 개발 검사점 경험을 사용하는 경우 다음 작업은 Mixed Reality 앱의 핵심 구성 요소를 숙지하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-182">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e7c7a-183">기본 상호 작용</span><span class="sxs-lookup"><span data-stu-id="e7c7a-183">Basic interactions</span></span>](../../../out-of-scope/mrtk-101.md)

<span data-ttu-id="e7c7a-184">언제든지 [Unity 개발 검사점](../unity-development-overview.md#1-getting-started)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7c7a-184">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>