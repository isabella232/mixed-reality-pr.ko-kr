---
title: 직관적 상호 작용
description: 혼합 현실 플랫폼 전반에 얽혀 있는 간단하고 직관적인 상호 작용이라는 철학을 알아봅니다.
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 응시, 응시 타깃팅, 상호 작용, 디자인, hololens, MMR, 멀티모달, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens
ms.openlocfilehash: 37ac7475172977c8741c17817568cc9b5ad2a4e5
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "97847291"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="9558f-104">직관적인 상호 작용 소개</span><span class="sxs-lookup"><span data-stu-id="9558f-104">Introducing instinctual interactions</span></span>

![수동으로 원거리 조작](images/04_InteractionFundamentals.png)

<span data-ttu-id="9558f-106">간단하고 직관적인 상호 작용이라는 철학은 MR(혼합 현실) 플랫폼 전반에 얽혀 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-106">The philosophy of simple, instinctual interactions is interwoven throughout the mixed reality (MR) platform.</span></span> <span data-ttu-id="9558f-107">애플리케이션 디자이너와 개발자가 고객에게 쉽고 직관적인 상호 작용을 제공할 수 있도록 하는 3단계를 살펴보았습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-107">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="9558f-108">첫째, 센서와 입력 기술이 다중 모드 상호 작용 모델에 결합되도록 했습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-108">First, we've made sure our sensors and input technologies combine into multimodal interaction models.</span></span> <span data-ttu-id="9558f-109">이러한 상호 작용 모델에는 자연어 입력과 함께 손 및 시선 추적이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-109">These interaction models include hand and eye tracking along with natural language input.</span></span> <span data-ttu-id="9558f-110">연구에 따르면, 개별 입력보다는 다원적인 프레임워크 내의 설계와 개발이 직관적인 환경을 만드는 열쇠라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-110">Based on our research, designing and developing within a multimodal framework (and not based on individual inputs) is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="9558f-111">둘째, 여러 HoloLens 디바이스(HoloLens 2, HoloLens(1세대) 또는 HoloLens 및 VR)를 대상으로 하는 개발자가 많다는 점을 파악했습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-111">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span> <span data-ttu-id="9558f-112">따라서, 상호 작용 모델이 여러 디바이스에서 작동하도록 설계하고 있습니다(입력 기술이 디바이스마다 다를 수 있음).</span><span class="sxs-lookup"><span data-stu-id="9558f-112">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span> <span data-ttu-id="9558f-113">예를 들어 6DoF 컨트롤러 및 HoloLens 2가 있는 Windows 몰입형 헤드셋의 원거리 상호 작용은 모두 동일한 어포던스와 패턴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-113">For example, far interaction on a Windows Immersive headset with a 6DoF controller and HoloLens 2 both use identical affordances and patterns.</span></span> <span data-ttu-id="9558f-114">이렇게 하면 디바이스 간 애플리케이션을 쉽게 개발할 수 있고 자연스러운 느낌을 사용자 상호 작용에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-114">This makes it easy for cross-device application development and provides a natural feel to user interactions.</span></span> 

<span data-ttu-id="9558f-115">MR에서 효과적이고 매력적이며 신비한 수천 가지의 상호 작용이 가능하다는 것을 인식하는 한편, 의도적으로 단일 상호 작용 모델을 애플리케이션에 사용하는 것이 사용자의 성공과 뛰어난 환경을 보장하는 가장 좋은 방법임을 알게 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-115">While we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we've found that intentionally employing a single interaction model in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="9558f-116">따라서, 이 상호 작용 지침에는 다음 세 가지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-116">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="9558f-117">세 가지 주요 상호 작용 모델 및 각각에 필요한 구성 요소와 패턴에 대한 구체적인 지침</span><span class="sxs-lookup"><span data-stu-id="9558f-117">Specific guidance around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="9558f-118">당사 플랫폼이 제공하는 기타 혜택에 대한 추가 지침</span><span class="sxs-lookup"><span data-stu-id="9558f-118">Supplemental guidance about other benefits that our platform provides.</span></span>
* <span data-ttu-id="9558f-119">개발 시나리오에 적합한 상호 작용 모델을 선택하는 데 참고할 수 있는 일반 지침</span><span class="sxs-lookup"><span data-stu-id="9558f-119">General guidance to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="9558f-120">멀티모달 상호 작용 모델</span><span class="sxs-lookup"><span data-stu-id="9558f-120">Multimodal interaction models</span></span>

<span data-ttu-id="9558f-121">Microsoft의 연구와 고객의 피드백에 따라 세 가지 기본 상호 작용 모델이 대부분의 혼합 현실 환경에 적합하다는 것이 발견되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-121">Based on our research and feedback from customers, we've discovered that three primary interaction models suit most mixed reality experiences.</span></span> <span data-ttu-id="9558f-122">여러 가지 면에서 상호 작용 모델은 워크플로를 완료하는 방법에 대한 사용자의 심리 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-122">In many ways, the interaction model is the user's mental model for how to complete a workflow.</span></span> <span data-ttu-id="9558f-123">각 상호 작용 모델은 고객의 요구에 맞게 최적화되어 있으며 올바르게 사용될 때 편리하고 강력하며 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-123">Each of these interaction models is optimized for a set of customer needs and is convenient, powerful, and usable when used correctly.</span></span> 

<span data-ttu-id="9558f-124">아래 차트는 간략한 개요입니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-124">The chart below is a simplified overview.</span></span> <span data-ttu-id="9558f-125">각 상호 작용 모델 사용에 대한 자세한 정보는 아래 페이지에서 이미지와 코드 샘플로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-125">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9558f-126"><strong>모델</strong></span><span class="sxs-lookup"><span data-stu-id="9558f-126"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="9558f-127"><strong>예제 시나리오</strong></span><span class="sxs-lookup"><span data-stu-id="9558f-127"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="9558f-128"><strong>적합</strong></span><span class="sxs-lookup"><span data-stu-id="9558f-128"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="9558f-129"><strong>하드웨어</strong></span><span class="sxs-lookup"><span data-stu-id="9558f-129"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9558f-130"><a href="hands-and-tools.md">실습 및 모션 컨트롤러</a></span><span class="sxs-lookup"><span data-stu-id="9558f-130"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="9558f-131">3D 공간 환경(예: 공간 레이아웃 및 디자인, 콘텐츠 조작 또는 시뮬레이션).</span><span class="sxs-lookup"><span data-stu-id="9558f-131">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="9558f-132">새로운 사용자에게 음성, 시선 추적 또는 헤드 게이즈(head-gaze)와 함께 사용하면 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-132">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="9558f-133">학습 기간이 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-133">Low learning curve.</span></span> <span data-ttu-id="9558f-134">손 추적 및 6DoF 컨트롤러에서 UX가 일관적입니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-134">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="9558f-135">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9558f-135">HoloLens 2</span></span><br><span data-ttu-id="9558f-136">몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="9558f-136">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9558f-137"><a href="hands-free.md">핸즈프리</a></span><span class="sxs-lookup"><span data-stu-id="9558f-137"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="9558f-138">현장 학습, 유지 보수와 같이 사용자의 손을 다른 일에 사용하고 있는 상황에 맞는 환경.</span><span class="sxs-lookup"><span data-stu-id="9558f-138">Contextual experiences where a user's hands are occupied, such as on-the-job learning and maintenance.</span></span></td>
        <td><span data-ttu-id="9558f-139">어느 정도 학습이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-139">Some learning required.</span></span> <span data-ttu-id="9558f-140">손을 사용할 수 없는 경우, 디바이스가 음성 및 자연어와 조화를 잘 이룹니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-140">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="9558f-141">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9558f-141">HoloLens 2</span></span><br><span data-ttu-id="9558f-142">HoloLens(1세대)</span><span class="sxs-lookup"><span data-stu-id="9558f-142">HoloLens (1st gen)</span></span><br><span data-ttu-id="9558f-143">몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="9558f-143">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9558f-144"><a href="gaze-and-commit.md">응시 및 커밋</a></span><span class="sxs-lookup"><span data-stu-id="9558f-144"><a href="gaze-and-commit.md">Gaze and commit</a></span></span></td>
        <td><span data-ttu-id="9558f-145">3D 프레젠테이션이나 데모와 같은 클릭 환경</span><span class="sxs-lookup"><span data-stu-id="9558f-145">Click-through experiences, for example, 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="9558f-146">모바일이 아닌 HMD에 대한 교육이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-146">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="9558f-147">액세스 가능한 컨트롤러에 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-147">Best for accessible controllers.</span></span> <span data-ttu-id="9558f-148">HoloLens(1세대)에 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-148">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="9558f-149">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9558f-149">HoloLens 2</span></span><br><span data-ttu-id="9558f-150">HoloLens(1세대)</span><span class="sxs-lookup"><span data-stu-id="9558f-150">HoloLens (1st gen)</span></span><br><span data-ttu-id="9558f-151">몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="9558f-151">Immersive headsets</span></span><br><span data-ttu-id="9558f-152">모바일 AR</span><span class="sxs-lookup"><span data-stu-id="9558f-152">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="9558f-153">사용자 상호 작용 환경의 차이를 방지하려면 단일 모델에 대한 지침을 처음부터 끝까지 따르는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-153">To avoid gaps in the user interaction experience, it's best to follow the guidance for a single model from beginning to end.</span></span>

<span data-ttu-id="9558f-154">아래 섹션에서는 이러한 상호 작용 모델 중 하나를 선택하고 구현하는 단계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-154">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-youll-understand-our-guidance-on"></a><span data-ttu-id="9558f-155">이 페이지를 끝까지 마치면 다음에 대한 지침을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-155">By the end of this page, you'll understand our guidance on:</span></span>
 
* <span data-ttu-id="9558f-156">고객을 위한 상호 작용 모델 선택</span><span class="sxs-lookup"><span data-stu-id="9558f-156">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="9558f-157">상호 작용 모델 구현</span><span class="sxs-lookup"><span data-stu-id="9558f-157">Implementing the interaction model</span></span>
* <span data-ttu-id="9558f-158">상호 작용 모델 간 전환</span><span class="sxs-lookup"><span data-stu-id="9558f-158">Transitioning between interaction models</span></span>
* <span data-ttu-id="9558f-159">다음 단계 디자인</span><span class="sxs-lookup"><span data-stu-id="9558f-159">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="9558f-160">고객을 위한 상호 작용 모델 선택</span><span class="sxs-lookup"><span data-stu-id="9558f-160">Choose an interaction model for your customer</span></span>

<span data-ttu-id="9558f-161">일반적으로 개발자와 작성자는 고객이 가질 수 있는 상호 작용 유형에 대해 충분히 생각합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-161">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="9558f-162">고객 중심의 설계 방식을 권장하기 위해, 아래 지침에 따라 고객에게 최적화된 상호 작용 모델을 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-162">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="9558f-163">이 지침을 따르는 이유</span><span class="sxs-lookup"><span data-stu-id="9558f-163">Why follow this guidance?</span></span>

* <span data-ttu-id="9558f-164">신체적/인지적 노력, 직관성 및 학습 가능성을 포함하여 객관적이고 주관적인 기준에 따라 상호 작용 모델을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-164">We test our interaction models for objective and subjective criteria, including physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="9558f-165">상호 작용이 다르기 때문에, 시각/오디오 어포던스 및 개체 동작 역시 상호 작용 모델마다 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-165">Because interactions differ, visual/audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="9558f-166">여러 상호 작용 모델의 일부를 결합하면 어포던스 사이에 경쟁(예: 동시 손 광선과 헤드 게이즈(head-gaze) 커서)이 발생할 위험이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-166">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor.</span></span> <span data-ttu-id="9558f-167">그러면 사용자의 불편과 혼동을 초래할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-167">This can overwhelm and confuse users.</span></span>

<span data-ttu-id="9558f-168">다음은 각 상호 작용 모델에 대해 어포던스 및 동작을 최적화하는 방법에 대한 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-168">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span> <span data-ttu-id="9558f-169">새로운 사용자가 _"시스템이 작동하는지 어떻게 알 수 있나요?"_ , _"내가 무엇을 할 수 있는지 어떻게 알 수 있나요?"_ , _"내가 방금 한 일이 이해되었는지 어떻게 알 수 있나요?"_ 등과 유사한 질문을 하는 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-169">We often see new users have similar questions, such as _"how do I know the system is working"_, _"how do I know what I can do"_, and _"how do I know if it understood what I just did?"_</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9558f-170"><strong>모델</strong></span><span class="sxs-lookup"><span data-stu-id="9558f-170"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="9558f-171"><strong>작동하는지 어떻게 알 수 있나요?</strong></span><span class="sxs-lookup"><span data-stu-id="9558f-171"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="9558f-172"><strong>내가 무엇을 할 수 있는지 어떻게 알 수 있나요?</strong></span><span class="sxs-lookup"><span data-stu-id="9558f-172"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="9558f-173"><strong>내가 방금 한 일을 어떻게 알 수 있나요?</strong></span><span class="sxs-lookup"><span data-stu-id="9558f-173"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9558f-174"><a href="hands-and-tools.md">실습 및 모션 컨트롤러</a></span><span class="sxs-lookup"><span data-stu-id="9558f-174"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="9558f-175">손 메시, 손가락 끝 어포던스 또는 손/컨트롤러 광선이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-175">I see a hand mesh, a fingertip affordance, or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="9558f-176">내 손이 개체 가까이 있으면 잡을 수 있는 핸들이나 경계 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-176">I see grabbable handles, or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="9558f-177">가청음이 들리고 잡았다 놓을 수 있는 애니메이션이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-177">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9558f-178"><a href="gaze-and-commit.md">헤드 게이즈 및 커밋</a></span><span class="sxs-lookup"><span data-stu-id="9558f-178"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="9558f-179">내 시야의 가운데에 커서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-179">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="9558f-180">커서가 특정 개체 위에 있으면 상태가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-180">The cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="9558f-181">내가 행동을 하면 시각 및 청각 확인이 보이고 들립니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-181">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="9558f-182"><a href="hands-free.md">핸즈프리(헤드 게이즈(head-gaze) 및 드웰(dwell))</a></span><span class="sxs-lookup"><span data-stu-id="9558f-182"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="9558f-183">내 시야의 가운데에 커서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-183">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="9558f-184">상호 작용이 가능한 개체에 드웰(dwell)하면 진행률 표시기가 보입니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-184">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="9558f-185">내가 행동을 하면 시각 및 청각 확인이 보이고 들립니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-185">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9558f-186"><a href="hands-free.md">핸즈프리(음성 명령)</a></span><span class="sxs-lookup"><span data-stu-id="9558f-186"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="9558f-187">시스템이 무엇을 들었는지 보여주는 듣기 표시기와 자막이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-187">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="9558f-188">음성 프롬프트와 힌트가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-188">I get voice prompts and hints.</span></span> <span data-ttu-id="9558f-189">다음과 같이 말하는 경우: "이렇게 말 하세요~"</span><span class="sxs-lookup"><span data-stu-id="9558f-189">When I say: "What can I say?"</span></span> <span data-ttu-id="9558f-190">피드백이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-190">I see feedback.</span></span></td>
        <td><span data-ttu-id="9558f-191">명령을 하면 시각 및 청각 확인이 보이고 들리거나 필요할 때 명확성 UX가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-191">I see/hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="9558f-192">다음은 상호 작용 모델을 선택하는 데 도움이 되는 질문입니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-192">Below are questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="9558f-193">Q:  사용자가 홀로그램을 터치하고 정밀한 홀로그램 조작을 수행하기를 원하나요?</span><span class="sxs-lookup"><span data-stu-id="9558f-193">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="9558f-194">A:  만약 그렇다면, 정밀 타기팅 및 조작을 위한 손과 모션 컨트롤러 상호 작용 모델을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="9558f-194">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation.</span></span>
 
2.  <span data-ttu-id="9558f-195">Q:  사용자가 실제 업무에서 손이 자유로워야 하나요?</span><span class="sxs-lookup"><span data-stu-id="9558f-195">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="9558f-196">A:  만약 그렇다면, 응시 및 음성 기반 상호 작용을 통해 유용한 핸즈프리 환경을 제공하는 핸즈프리 상호 작용 모델을 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="9558f-196">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="9558f-197">Q:  사용자가 MR 애플리케이션의 상호 작용을 학습할 시간이 있나요? 또는 가장 낮은 학습 곡선과의 상호 작용이 사용자에게 필요한가요?</span><span class="sxs-lookup"><span data-stu-id="9558f-197">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="9558f-198">A:  가장 낮은 학습 곡선과 가장 직관적인 상호 작용을 위해 사용자가 손을 상호 작용에 사용할 수 있는 한 손 및 모션 컨트롤러 모델을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-198">A:  For the lowest learning curve and most intuitive interactions, we recommend the Hands and motion controllers model, as long as users can use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="9558f-199">Q:  사용자가 가리키기 및 조작을 위해 모션 컨트롤러를 사용하나요?</span><span class="sxs-lookup"><span data-stu-id="9558f-199">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="9558f-200">A:  손 및 모션 컨트롤러 모델에는 모션 컨트롤러를 사용하는 유용한 환경을 위한 모든 지침이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-200">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="9558f-201">Q:  사용자가 접근성 컨트롤러나 일반적인 Bluetooth 컨트롤러(예: 클리커)를 사용하나요?</span><span class="sxs-lookup"><span data-stu-id="9558f-201">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="9558f-202">A:  모든 비 추적 컨트롤러에 대해서는 헤드 게이즈(head-gaze) 및 커밋 모델을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-202">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="9558f-203">사용자가 간단한 “대상 및 커밋” 기법으로 전체 환경을 탐색할 수 있도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-203">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="9558f-204">Q: 사용자가 UI 컨트롤의 밀집된 레이아웃을 탐색하는 것과는 대조적으로, “클릭”(예: 3D 슬라이드 쇼와 같은 환경)을 통한 환경에서 작업을 수행하나요?</span><span class="sxs-lookup"><span data-stu-id="9558f-204">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="9558f-205">A:  사용자가 많은 UI를 제어할 필요가 없는 경우 머리 응시 및 커밋에서 사용자가 대상 지정을 염려할 필요가 없는 학습 가능한 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-205">A:  If users don't need to control a lot of UI, Head-gaze and commit offers a learnable option where users don't have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="9558f-206">Q:  사용자가 HoloLens(1세대)와 HoloLens 2/Windows Mixed Reality 몰입형 헤드셋(VR)을 둘 다 사용하나요?</span><span class="sxs-lookup"><span data-stu-id="9558f-206">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="9558f-207">A:  머리 응시 및 커밋은 HoloLens(1세대)용 상호 작용 모델이므로 HoloLens(1세대)를 지원하는 작성자는 머리 응시 및 커밋을 사용자가 HoloLens(1세대) 헤드셋에서 경험하는 모든 기능 또는 모드에 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-207">A:  Since Head-gaze and commit are the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="9558f-208">여러 HoloLens 세대를 위한 훌륭한 환경을 만드는 방법에 대한 자세한 내용은 다음에 나오는 *상호 작용 모델 전환* 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9558f-208">See the next section on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="9558f-209">Q: 많은 공간을 사용하거나 공간 사이를 이동하는 모바일 사용자와 단일 공간에서 작업하는 경향이 있는 사용자는 어떤가요?</span><span class="sxs-lookup"><span data-stu-id="9558f-209">Q: What about users who are mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="9558f-210">A:  이러한 사용자에게는 모든 사용자 상호 작용 모델이 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-210">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="9558f-211">앱 디자인에 관련된 자세한 지침은 [서비스 예정](../out-of-scope/news.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-211">More guidance specific to app design [coming soon](../out-of-scope/news.md).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="9558f-212">상호 작용 모델 전환</span><span class="sxs-lookup"><span data-stu-id="9558f-212">Transitioning interaction models</span></span>
<span data-ttu-id="9558f-213">둘 이상의 상호 작용 모델을 사용해야 할 수도 있는 사용 사례도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-213">There are also use cases that might require using more than one interaction model.</span></span> <span data-ttu-id="9558f-214">예를 들어 애플리케이션의 만들기 흐름에는 _"손 및 모션 컨트롤러"_ 상호 작용 모델이 사용되지만, 현장 기술자를 위해 핸즈프리 모드를 사용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-214">For example, your application's creation flow uses the _"hands and motion controllers"_ interaction model, but you want to employ a hands-free mode for field technicians.</span></span> <span data-ttu-id="9558f-215">여러 상호 작용 모델이 환경에 필요한 경우, 특히 혼합 현실을 처음 접하는 경우 사용자는 한 모델에서 다른 모델로 전환하는 데 어려움을 겪을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-215">If your experience does require multiple interaction models, users might have difficulty transitioning from one model to another, especially when they're new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="9558f-216">개발자와 디자이너에게 더 많은 지침을 제공하기 위해 지속적으로 노력하고 있으며, 이를 통해 여러 MR 상호 작용 모델을 사용하는 방법, 시기 및 이유를 알려드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="9558f-216">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="9558f-217">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9558f-217">See also</span></span>
* [<span data-ttu-id="9558f-218">편안함</span><span class="sxs-lookup"><span data-stu-id="9558f-218">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="9558f-219">시선 기반 상호 작용</span><span class="sxs-lookup"><span data-stu-id="9558f-219">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="9558f-220">HoloLens 2의 시선 추적</span><span class="sxs-lookup"><span data-stu-id="9558f-220">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="9558f-221">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="9558f-221">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="9558f-222">응시 및 유지</span><span class="sxs-lookup"><span data-stu-id="9558f-222">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="9558f-223">손 - 직접 조작</span><span class="sxs-lookup"><span data-stu-id="9558f-223">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9558f-224">손 - 제스처</span><span class="sxs-lookup"><span data-stu-id="9558f-224">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="9558f-225">손 - 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="9558f-225">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="9558f-226">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="9558f-226">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="9558f-227">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="9558f-227">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="9558f-228">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="9558f-228">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="9558f-229">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="9558f-229">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="9558f-230">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="9558f-230">Voice input</span></span>](voice-input.md)


