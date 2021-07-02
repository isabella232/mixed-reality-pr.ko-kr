---
title: 시각적 테마
description: 개요 시각적 테마 MRTK의 UX 자산에 대 한 유연한 제어
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, mrtk 테마,
ms.openlocfilehash: d97c470bf1d77299c6848990cdc69d886d432ecb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177172"
---
# <a name="visual-themes"></a><span data-ttu-id="0aef4-104">시각적 테마</span><span class="sxs-lookup"><span data-stu-id="0aef4-104">Visual themes</span></span>

<span data-ttu-id="0aef4-105">테마를 사용 하면 다양 한 상태 전환에 대 한 응답으로 UX 자산을 유연 하 게 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-105">Themes allow for flexible control of UX assets in response to various states transitions.</span></span> <span data-ttu-id="0aef4-106">이는 단추의 색을 변경 하 고 포커스에 대 한 응답으로 요소의 크기를 조정 하는 등의 작업이 포함 될 수 있습니다. 시각적 테마 프레임 워크는 두 가지 주요 부분, 즉 1) 구성 및 2) 런타임 엔진으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-106">This may involve changing a button's color, resizing an element in response to focus, etc. The Visual Themes framework is made up of two key pieces: 1) configuration and 2) runtime engines.</span></span>

<span data-ttu-id="0aef4-107">테마 [구성은](#theme-configuration) 속성 및 형식의 정의 이며, [테마 엔진](#theme-engines) 은 구성을 사용 하 고 변환, 자료 등을 업데이트 하는 논리를 구현 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-107">[Theme configurations](#theme-configuration) are definitions of properties and types while [Theme Engines](#theme-engines) are classes that consume the configurations and implement the logic to update transforms, materials, and more at runtime.</span></span>

## <a name="theme-configuration"></a><span data-ttu-id="0aef4-108">테마 구성</span><span class="sxs-lookup"><span data-stu-id="0aef4-108">Theme configuration</span></span>

<span data-ttu-id="0aef4-109">테마 구성은 런타임 시 테마 엔진을 초기화 하는 방법을 정의 하는 스크립트가 정의 된 [개체](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 입니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-109">Theme configurations are [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) that define how Theme Engines will be initialized at runtime.</span></span> <span data-ttu-id="0aef4-110">앱이 실행 중일 때 입력 또는 기타 상태 변경에 대 한 응답으로 사용할 속성 및 값을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-110">They define what properties and values to utilize in response to input or other state changes when the app is running.</span></span> <span data-ttu-id="0aef4-111">예 [를](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 들어, 테마 구성을 한 번 정의한 다음 여러 UX 구성 요소에서 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-111">As [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) assets, theme configurations can be defined once and then re-used across different UX components.</span></span>

<span data-ttu-id="0aef4-112">새 자산을 만들려면 [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-112">To create a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:</span></span>

1) <span data-ttu-id="0aef4-113">*Project 창을* 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-113">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="0aef4-114">  >  **혼합 현실 만들기 Toolkit**  >  **테마** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-114">Select **Create** > **Mixed Reality Toolkit** > **Theme**</span></span>

<span data-ttu-id="0aef4-115">예제 테마 구성 자산은에서 찾을 수 있습니다 `MRTK/SDK/Features/UX/Interactable/Themes` .</span><span class="sxs-lookup"><span data-stu-id="0aef4-115">Example Theme configuration assets can be found under `MRTK/SDK/Features/UX/Interactable/Themes`.</span></span>

![Inspector의 Theme Tabletableobject 예제](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a><span data-ttu-id="0aef4-117">상태</span><span class="sxs-lookup"><span data-stu-id="0aef4-117">States</span></span>

<span data-ttu-id="0aef4-118">새를 만들 때 [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) 가장 먼저 설정 해야 하는 상태는 사용할 수 있는 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-118">When creating a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme), the first thing to set is what states are available.</span></span> <span data-ttu-id="0aef4-119">상태 *속성은* 상태 마다 하나의 값을 가질 수 있도록 테마 구성에서 정의 해야 하는 값의 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-119">The *States* property indicates how many values a Theme configuration needs to define as there will be one value per state.</span></span> <span data-ttu-id="0aef4-120">위의 예제 이미지에서 Interactable 구성 요소 [에 대해 정의 된 기본 상태](interactable.md#general-input-settings) 는 *기본값*, *포커스*, *누름* 및 *사용 안 함* 입니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-120">In the example image above, the [default states defined for the Interactable](interactable.md#general-input-settings) component are *Default*, *Focus*, *Pressed*, and *Disabled*.</span></span> <span data-ttu-id="0aef4-121">이러한 특성은 `DefaultInteractableStates` (asset/MRTK/SDK/Features/UX/Interactable/States) 자산 파일에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-121">These are defined in the `DefaultInteractableStates` (Assets/MRTK/SDK/Features/UX/Interactable/States) asset file.</span></span>

<span data-ttu-id="0aef4-122">새 자산을 만들려면 [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-122">To create a new [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:</span></span>

1) <span data-ttu-id="0aef4-123">*Project 창을* 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-123">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="0aef4-124">  >  **Mixed Reality Toolkit**  >  **상태** 만들기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-124">Select **Create** > **Mixed Reality Toolkit** > **State**</span></span>

![Inspector의 상태 스크립트가 아닌 개체 예제](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="0aef4-126">[`State`](xref:Microsoft.MixedReality.Toolkit.UI.States)StateModel tableobject는 상태 목록과 이러한 상태에 대해 만들  의 유형을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-126">A [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject defines both the list of states as well as the type of *StateModel* to create for these states.</span></span> <span data-ttu-id="0aef4-127">*StateModel* 은 [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) 런타임에 현재 상태를 생성 하는 상태 시스템 논리를 확장 하 고 구현 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-127">A *StateModel* is a class that extends [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) and implements the state machine logic to generate the current state at runtime.</span></span> <span data-ttu-id="0aef4-128">이 클래스의 현재 상태는 일반적으로 런타임에 테마 엔진에서 재질 속성, GameObject 변환 등에 대해 설정할 값을 지시 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-128">The current state from this class is generally used by Theme Engines at runtime to dictate what values to set against material properties, GameObject transforms, and more.</span></span>

### <a name="theme-engine-properties"></a><span data-ttu-id="0aef4-129">테마 엔진 속성</span><span class="sxs-lookup"><span data-stu-id="0aef4-129">Theme engine properties</span></span>

<span data-ttu-id="0aef4-130">*상태* 외에 [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) 도 자산에는 이러한 엔진의 테마 엔진과 관련 속성이 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-130">Outside of *States*, a [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset also defines a list of Theme Engines and the associated properties for these engines.</span></span> <span data-ttu-id="0aef4-131">[테마 엔진](#theme-engines) 은 런타임에 GameObject에 대해 올바른 값을 설정 하는 논리를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-131">A [Theme engine](#theme-engines) again defines the logic to set the correct values against a GameObject at runtime.</span></span>

<span data-ttu-id="0aef4-132">자산은 여러 개의 [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) 테마 엔진을 정의 하 여 여러 GameObject 속성을 대상으로 하는 정교한 시각적 상태 전환을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-132">A [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset can define multiple Theme Engines to achieve sophisticated visual states transitions targeting multiple GameObject properties.</span></span>

<span data-ttu-id="0aef4-133">**테마 런타임**</span><span class="sxs-lookup"><span data-stu-id="0aef4-133">**Theme Runtime**</span></span>

<span data-ttu-id="0aef4-134">생성 될 테마 엔진의 클래스 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-134">Defines the class type of the Theme engine that will be created</span></span>

<span data-ttu-id="0aef4-135">**감속/가속**</span><span class="sxs-lookup"><span data-stu-id="0aef4-135">**Easing**</span></span>

<span data-ttu-id="0aef4-136">일부 *테마 엔진* 은 속성 [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) 를 true로 정의 하면 상태 간의 감속을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-136">Some *Theme Engines*, if they define their property [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) as true, support easing between states.</span></span> <span data-ttu-id="0aef4-137">예를 들어 상태 변경이 발생 하는 경우 두 색 사이를 lerping.</span><span class="sxs-lookup"><span data-stu-id="0aef4-137">For example, lerping between two colors when a state change occurs.</span></span> <span data-ttu-id="0aef4-138">*지속* 시간은 초 단위로 정의 됩니다. 시작 값부터 끝 값까지, *애니메이션 곡선은* 해당 기간 동안의 변경 속도를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-138">The *Duration* defines in seconds how long to ease from start value to end value and the *Animation Curve* defines the rate of change during that time period.</span></span>

<span data-ttu-id="0aef4-139">**셰이더 속성**</span><span class="sxs-lookup"><span data-stu-id="0aef4-139">**Shader properties**</span></span>

<span data-ttu-id="0aef4-140">일부 *테마 엔진* 은 속성 [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) 를 true로 정의 하면 런타임에 특정 셰이더 속성을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-140">Some *Theme Engines*, if they define their property [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) as true, will modify particular shader properties at runtime.</span></span> <span data-ttu-id="0aef4-141">*셰이더* 및 *속성* 필드는 대상으로 지정할 셰이더 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-141">The *Shader* and *Property* fields define the shader property to target.</span></span>

### <a name="create-a-theme-configuration-via-code"></a><span data-ttu-id="0aef4-142">코드를 통해 테마 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="0aef4-142">Create a theme configuration via code</span></span>

<span data-ttu-id="0aef4-143">일반적으로 Unity 검사기를 통해 테마 구성을 디자인 하기가 더 쉽지만 코드를 통해 런타임에 동적으로 테마를 생성 해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-143">In general, it is easier to design Theme configurations via the Unity inspector but there are cases where Themes must be dynamically generated at runtime via code.</span></span> <span data-ttu-id="0aef4-144">아래 코드 조각에서는이 작업을 수행 하는 방법에 대 한 예제를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-144">The code snippet below gives an example of how to accomplish this task.</span></span>

<span data-ttu-id="0aef4-145">개발을 신속 하 게 수행 하기 위해 다음 도우미 메서드는 설치를 간소화 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-145">To help expedite development, the following helper methods are useful for simplifying setup.</span></span>

<span data-ttu-id="0aef4-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) - [Interactable](interactable.md) 구성 요소에 사용 되는 네 가지 기본 상태 값을 사용 하 여 새 상태 스크립트가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) - creates a new States ScriptableObject with the four default state values used in the [Interactable](interactable.md) component.</span></span>

<span data-ttu-id="0aef4-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) -모든 테마 엔진은 해당 테마 런타임 유형에 필요한 올바른 속성을 사용 하 여 기본 구성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Every Theme Engine defines a default configuration with the correct properties needed for that Theme runtime type.</span></span> <span data-ttu-id="0aef4-148">이 도우미는 지정 된 테마 엔진 유형에 대 한 정의를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-148">This helper creates a definition for the given Theme Engine type.</span></span>

```c#
// This code example builds a Theme ScriptableObject that can be used with an Interactable component.
// A random color is selected for the on pressed state every time this code is executed.

// Use the default states utilized in the Interactable component
var defaultStates = Interactable.GetDefaultInteractableStates();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

// Create the Theme configuration asset
Theme testTheme = ScriptableObject.CreateInstance<Theme>();
testTheme.States = defaultStates;
testTheme.Definitions = new List<ThemeDefinition>() { newThemeType };
```

## <a name="theme-engines"></a><span data-ttu-id="0aef4-149">테마 엔진</span><span class="sxs-lookup"><span data-stu-id="0aef4-149">Theme engines</span></span>

<span data-ttu-id="0aef4-150">[테마 엔진](#theme-engines) 은 클래스에서 확장 되는 클래스입니다 [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) .</span><span class="sxs-lookup"><span data-stu-id="0aef4-150">A [Theme Engine](#theme-engines) is a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="0aef4-151">이러한 클래스는 런타임에 인스턴스화되고 앞에서 설명한 개체를 사용 하 여 구성 됩니다 [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) .</span><span class="sxs-lookup"><span data-stu-id="0aef4-151">These classes are instantiated at runtime and configured with a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object as outlined earlier.</span></span>

### <a name="default-theme-engines"></a><span data-ttu-id="0aef4-152">기본 테마 엔진</span><span class="sxs-lookup"><span data-stu-id="0aef4-152">Default theme engines</span></span>

<span data-ttu-id="0aef4-153">MRTK는 아래 나열 된 기본 테마 엔진 집합과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-153">MRTK ships with a default set of Theme Engines listed below:</span></span>

- [`InteractableActivateTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableActivateTheme)
- [`InteractableAnimatorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAnimatorTheme)
- [`InteractableAudioTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioTheme)
- [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
- [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
- [`InteractableGrabScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableGrabScaleTheme)
- [`InteractableMaterialTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableMaterialTheme)
- [`InteractableOffsetTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOffsetTheme)
- [`InteractableRotationTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableRotationTheme)
- [`InteractableScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableScaleTheme)
- [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme)
- [`InteractableStringTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStringTheme)
- [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
- [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

<span data-ttu-id="0aef4-154">기본 테마 엔진은에서 찾을 수 있습니다 `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .</span><span class="sxs-lookup"><span data-stu-id="0aef4-154">The default Theme Engines can be found under `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines`.</span></span>

### <a name="custom-theme-engines"></a><span data-ttu-id="0aef4-155">사용자 지정 테마 엔진</span><span class="sxs-lookup"><span data-stu-id="0aef4-155">Custom theme engines</span></span>

<span data-ttu-id="0aef4-156">설명한 대로 테마 엔진은 클래스에서 확장 되는 클래스로 정의 됩니다 [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) .</span><span class="sxs-lookup"><span data-stu-id="0aef4-156">As stated, a Theme Engine is defined as a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="0aef4-157">따라서 새 테마 엔진은이 클래스를 확장 하 고 다음을 구현 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-157">Thus, new Theme Engine need only extend this class and implement the following:</span></span>

#### <a name="mandatory-implementations"></a><span data-ttu-id="0aef4-158">필수 구현</span><span class="sxs-lookup"><span data-stu-id="0aef4-158">Mandatory implementations</span></span>

<span data-ttu-id="0aef4-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)`(f: MixedReality. Toolkit. U. InteractableThemeBase)</span><span class="sxs-lookup"><span data-stu-id="0aef4-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.SetValue)</span></span>

<span data-ttu-id="0aef4-160">로 식별할 수 있는 지정 된 속성의 경우 `ThemeStateProperty.Name` 대상 GameObject 호스트에서 현재 상태 값을 설정 합니다 (즉,</span><span class="sxs-lookup"><span data-stu-id="0aef4-160">For the given property, which can be identified by `ThemeStateProperty.Name`, set its current state value on the targeted GameObject host (i.e</span></span> <span data-ttu-id="0aef4-161">재질 색 등을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-161">set the material color, etc).</span></span> <span data-ttu-id="0aef4-162">*인덱스* 는 액세스할 현재 상태 값을 *나타내고, 0* 과 1 사이의 부동 소수점은 값 간의 감속/lerping에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-162">The *index* indicates the current state value to access and the *percentage*, a float between 0 and 1, is used for easing/lerping between values.</span></span>

<span data-ttu-id="0aef4-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(f: MixedReality. Toolkit. U. InteractableThemeBase)</span><span class="sxs-lookup"><span data-stu-id="0aef4-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetProperty)</span></span>

<span data-ttu-id="0aef4-164">로 식별할 수 있는 지정 된 속성의 경우 `ThemeStateProperty.Name` 대상 호스트 GameObject에 설정 된 현재 값을 반환 합니다 (즉,</span><span class="sxs-lookup"><span data-stu-id="0aef4-164">For the given property, which can be identified by `ThemeStateProperty.Name`, return the current value set on the targeted Host  GameObject (i.e</span></span> <span data-ttu-id="0aef4-165">현재 재질 색, 현재 로컬 위치 오프셋 등입니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-165">the current material color, the current local position offset, etc).</span></span> <span data-ttu-id="0aef4-166">이는 주로 상태를 감속 하는 경우 시작 값을 캐싱하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-166">This is primarily used for caching the start value when easing between states.</span></span>

<span data-ttu-id="0aef4-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(f: MixedReality. Toolkit. U. InteractableThemeBase.GetDefaultThemeDefinition)</span><span class="sxs-lookup"><span data-stu-id="0aef4-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetDefaultThemeDefinition)</span></span>

<span data-ttu-id="0aef4-168">[`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition)사용자 지정 테마에 필요한 기본 속성 및 구성을 정의 하는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-168">Returns a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object that defines the default properties and configuration needed for the custom theme</span></span>

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

<span data-ttu-id="0aef4-169">`SetValue()`인덱스 및/또는 백분율 구성을 사용 하도록 지정 하는 대신 ThemePropertyValue를 설정한 경우를 제외 하 고, 공개 정의의 보호 된 변형입니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-169">Protected variant of the public `SetValue()` definition, except provided ThemePropertyValue to set instead of directing to use index and/or percentage configuration.</span></span>

#### <a name="recommended-overrides"></a><span data-ttu-id="0aef4-170">권장 재정의</span><span class="sxs-lookup"><span data-stu-id="0aef4-170">Recommended overrides</span></span>

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

<span data-ttu-id="0aef4-171">제공 된 *GameObject* 매개 변수를 대상으로 하 고 *ThemeDefinition* 매개 변수에 정의 된 속성 및 구성을 사용 하 여 초기화 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-171">Perform any initialization steps here targeting the provided *GameObject* parameter and using the properties and configurations defined in the *ThemeDefinition* parameter.</span></span> <span data-ttu-id="0aef4-172">재정의를 시작할 때를 호출 하는 것이 좋습니다 `base.Init(host, settings)` .</span><span class="sxs-lookup"><span data-stu-id="0aef4-172">It is recommended to call `base.Init(host, settings)` at the beginning of an override.</span></span>

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

<span data-ttu-id="0aef4-173">사용자 지정 테마 엔진이 속성을 통해 구성 된 값 간의 감속/가속을 지원할 수 있으면이 고, [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing)</span><span class="sxs-lookup"><span data-stu-id="0aef4-173">If the custom Theme Engine can support easing between values which is configured via the [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) property.</span></span>

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

<span data-ttu-id="0aef4-174">사용자 지정 테마 엔진이 대상 셰이더 속성을 지원할 수 있는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-174">If the custom Theme Engine can support targeting shader properties.</span></span> <span data-ttu-id="0aef4-175">[`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)를 통해 셰이더 속성을 효율적으로 설정/가져오도록 기존 인프라의 이점을 활용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-175">It is recommended to extend from [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) to benefit from the existing infrastructure to efficiently set/get shader properties via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span></span> <span data-ttu-id="0aef4-176">셰이더 속성 정보는 및를 통해 각에 저장 됩니다 [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .</span><span class="sxs-lookup"><span data-stu-id="0aef4-176">The shader property information is stored in each [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) via [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) and [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName).</span></span>

> [!NOTE]
> <span data-ttu-id="0aef4-177">확장 하 [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) 는 경우 InteractableShaderTheme를 통해 [DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) 를 재정의 하는 것이 유용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-177">If extending [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme), it can also be useful to override the [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) via *new*.</span></span>
>
> <span data-ttu-id="0aef4-178">예제 코드: `protected new const string DefaultShaderProperty = "_Color";`</span><span class="sxs-lookup"><span data-stu-id="0aef4-178">Example code: `protected new const string DefaultShaderProperty = "_Color";`</span></span>
>
> <span data-ttu-id="0aef4-179">또한 아래에 있는 다음 클래스는 [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) 다시 [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 을 사용 하 여 셰이더 속성 값을 수정 하는 클래스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-179">Furthermore, the following classes below extend the [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) class which again uses [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) to modify shader property values.</span></span> <span data-ttu-id="0aef4-180">이 방법을 사용 하면 값이 변경 될 때 *MaterialPropertyBlocks* 에서 새로운 인스턴스 자료를 만들지 않으므로 [성능이 향상 됩니다](https://docs.unity3d.com/Manual/DrawCallBatching.html) .</span><span class="sxs-lookup"><span data-stu-id="0aef4-180">This approach [helps performance](https://docs.unity3d.com/Manual/DrawCallBatching.html) because *MaterialPropertyBlocks* do not create new instanced materials when values change.</span></span> <span data-ttu-id="0aef4-181">그러나 일반적인 [재질](https://docs.unity3d.com/ScriptReference/Material.html) 클래스 속성에 액세스 하는 경우에는 필요한 값이 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-181">However, accessing the typical [Material](https://docs.unity3d.com/ScriptReference/Material.html) class properties will not return expected values.</span></span> <span data-ttu-id="0aef4-182">*MaterialPropertyBlocks* 를 사용 하 여 현재 재질 속성 값 가져오기 및 유효성 검사 (즉,</span><span class="sxs-lookup"><span data-stu-id="0aef4-182">Use *MaterialPropertyBlocks* to get and validate current material property values (i.e</span></span> <span data-ttu-id="0aef4-183">*_Color* 또는 *_MainTex*).</span><span class="sxs-lookup"><span data-stu-id="0aef4-183">*_Color* or *_MainTex*).</span></span>
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

<span data-ttu-id="0aef4-184">이 테마 엔진이 초기화 될 때 수정 된 속성을 호스트 GameObject 설정 된 원래 값으로 다시 설정 하도록 테마에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-184">Directs the theme to reset any modified properties back to their original values that were set on the host GameObject when this theme engine was initialized.</span></span>  

### <a name="custom-theme-engine-example"></a><span data-ttu-id="0aef4-185">사용자 지정 테마 엔진 예제</span><span class="sxs-lookup"><span data-stu-id="0aef4-185">Custom theme engine example</span></span>

<span data-ttu-id="0aef4-186">다음 클래스는 사용자 지정 새 테마 엔진의 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-186">The class below is an example of a custom new Theme Engine.</span></span> <span data-ttu-id="0aef4-187">이 구현에서는 초기화 된 호스트 개체에서 [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) 구성 요소를 찾고 현재 상태를 기준으로 표시 유형을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-187">This implementation will find a [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) component on the initialized host object and control its visibility based on the current state.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

// This class demonstrates a custom theme to control a Host's MeshRenderer visibility
public class MeshVisibilityTheme : InteractableThemeBase
{
    // Bool visibility does not make sense for lerping
    public override bool IsEasingSupported => false;

    // No material or shaders are being modified
    public override bool AreShadersSupported => false;

    // Cache reference to the MeshRenderer component on our Host
    private MeshRenderer meshRenderer;

    public MeshVisibilityTheme()
    {
        Types = new Type[] { typeof(MeshRenderer) };
        Name = "Mesh Visibility Theme";
    }

    // Define a default configuration to simplify initialization of this theme engine
    // There is only one state property with a value per available state
    // This state property is a boolean that defines whether the renderer is enabled
    public override ThemeDefinition GetDefaultThemeDefinition()
    {
        return new ThemeDefinition()
        {
            ThemeType = GetType(),
            StateProperties = new List<ThemeStateProperty>()
            {
                new ThemeStateProperty()
                {
                    Name = "Mesh Visible",
                    Type = ThemePropertyTypes.Bool,
                    Values = new List<ThemePropertyValue>(),
                    Default = new ThemePropertyValue() { Bool = true }
                },
            },
            CustomProperties = new List<ThemeProperty>()
        };
    }

    // When initializing, cache a reference to the MeshRenderer component
    public override void Init(GameObject host, ThemeDefinition definition)
    {
        base.Init(host, definition);

        meshRenderer = host.GetComponent<MeshRenderer>();
    }

    // Get the current state of the MeshRenderer visibility
    public override ThemePropertyValue GetProperty(ThemeStateProperty property)
    {
        return new ThemePropertyValue()
        {
            Bool = meshRenderer.enabled
        };
    }

    // Update the MeshRenderer visibility based on the property state value data
    public override void SetValue(ThemeStateProperty property, int index, float percentage)
    {
        meshRenderer.enabled = property.Values[index].Bool;
    }
}
```

## <a name="end-to-end-example"></a><span data-ttu-id="0aef4-188">엔드투엔드 예제</span><span class="sxs-lookup"><span data-stu-id="0aef4-188">End-to-end example</span></span>

<span data-ttu-id="0aef4-189">이전 섹션에서 정의한 사용자 지정 테마 엔진을 확장 한 다음 코드 예제에서는 런타임에이 테마를 제어 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-189">Extending off of the custom Theme Engine defined in the earlier section, the code example below demonstrates how to control this theme at runtime.</span></span> <span data-ttu-id="0aef4-190">특히 MeshRenderer 표시 유형을 적절 하 게 업데이트 하도록 테마에서 현재 상태를 설정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-190">In particular, how to set the current state on the theme so the MeshRenderer visibility is updated appropriately.</span></span>

> [!NOTE]
> <span data-ttu-id="0aef4-191">`theme.OnUpdate(state,force)` 일반적으로 Update () 메서드에서 값 사이에 감속/lerping을 사용 하는 테마 엔진을 지원 하기 위해를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aef4-191">`theme.OnUpdate(state,force)` should generally be called in the Update() method to support Theme Engines that utilize easing/lerping between values.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

public class MeshVisibilityController : MonoBehaviour
{
    private MeshVisibilityTheme themeEngine;
    private bool hideMesh = false;

    private void Start()
    {
        // Define the default configuration. State 0 will be on while State 1 will be off
        var themeDefinition = ThemeDefinition.GetDefaultThemeDefinition<MeshVisibilityTheme>().Value;
        themeDefinition.StateProperties[0].Values = new List<ThemePropertyValue>()
        {
            new ThemePropertyValue() { Bool = true }, // show state
            new ThemePropertyValue() { Bool = false }, // hide state
        };

        // Create the actual Theme engine and initialize it with the GameObject we are attached to
        themeEngine = (MeshVisibilityTheme)InteractableThemeBase.CreateAndInitTheme(themeDefinition, this.gameObject);
    }

    private void Update()
    {
        // Update the theme engine to set our MeshRenderer visibility
        // based on our current state (i.e the hideMesh variable)
        themeEngine.OnUpdate(Convert.ToInt32(hideMesh));
    }

    public void ToggleVisibility()
    {
        // Alternate state of visibility
        hideMesh = !hideMesh;
    }
}
```

## <a name="see-also"></a><span data-ttu-id="0aef4-192">참조</span><span class="sxs-lookup"><span data-stu-id="0aef4-192">See also</span></span>

- [<span data-ttu-id="0aef4-193">상호 작용 가능</span><span class="sxs-lookup"><span data-stu-id="0aef4-193">Interactable</span></span>](interactable.md)
