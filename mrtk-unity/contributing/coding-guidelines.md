---
title: 코딩 지침
description: MRTK에 기여할 때 따라야 할 코딩 원칙 및 규칙입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, C#,
ms.openlocfilehash: 122c51962c55796c037302c7b79cc4df643a47b7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121441"
---
# <a name="coding-guidelines"></a>코딩 지침

이 문서에서는 MRTK에 기여할 때 따라야 하는 코딩 원칙과 규칙을 간략하게 설명합니다.

---

## <a name="philosophy"></a>철학

### <a name="be-concise-and-strive-for-simplicity"></a>간결하고 단순하게 하기 위해 노력합니다.

가장 간단한 솔루션이 가장 좋은 경우가 많습니다. 이는 이러한 지침의 재정의 목표이며 모든 코딩 작업의 목표가 되어야 합니다. 단순함의 일부는 간결하고 기존 코드와 일치합니다. 코드를 단순하게 유지해 보세요.

판독기는 유용한 정보를 제공하는 아티팩트만 발생해야 합니다. 예를 들어 명확한 내용을 다시 언급하는 주석은 추가 정보를 제공하지 않으며 노이즈 대 신호 비율을 늘림합니다.

코드 논리를 단순하게 유지합니다. 이는 가장 적은 수의 줄을 사용하고, 식별자 이름 또는 중괄호 스타일의 크기를 최소화하는 것이 아니라, 개념 수를 줄이고 익숙한 패턴을 통해 이러한 개념의 가시성을 극대화하는 것에 대한 명령문입니다.

### <a name="produce-consistent-readable-code"></a>일관되고 읽기 가능한 코드 생성

코드 가독성은 낮은 결함 비율과 관련이 있습니다. 읽기 쉬운 코드를 만들려고 노력합니다. 간단한 논리가 있는 코드를 만들고 기존 구성 요소를 다시 사용하는 것은 정확성을 보장하는 데에도 도움이 되도록 노력합니다.

가장 기본적인 정확성 세부 정보부터 일관된 스타일 및 서식 지정에 이르기까지 생성하는 코드의 모든 세부 정보가 중요합니다. 코딩 스타일이 기본 설정과 일치하지 않더라도 이미 존재하는 항목과 일관되게 유지합니다. 이렇게 하면 전체 코드베이스의 가독성이 향상됩니다.

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a>편집기와 런타임에 구성 요소 구성 지원

MRTK는 Unity 편집기에서 구성 요소를 구성하고 프리팹을 로드하려는 사용자와 런타임에 개체를 인스턴스화하고 구성해야 하는 사용자 등 다양한 사용자 집합을 지원합니다.

모든 코드는 저장된 장면에서 GameObject에 구성 요소를 추가하고 코드에서 해당 구성 요소를 인스턴스화하여 작동합니다. 테스트에는 프리팹을 인스턴스화하고 인스턴스화하고 런타임에 구성 요소를 구성하는 테스트 사례가 모두 포함되어야 합니다.

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a>편집기에서 재생은 첫 번째 및 기본 대상 플랫폼입니다.

편집기에서 재생은 Unity에서 반복하는 가장 빠른 방법입니다. 고객이 신속하게 반복할 수 있는 방법을 제공하면 솔루션을 더 빠르게 개발하고 더 많은 아이디어를 시도할 수 있습니다. 즉, 반복 속도를 최대화하면 고객이 더 많은 성과를 달성할 수 있습니다.

모든 것이 편집기에서 작동하게 한 다음, 다른 플랫폼에서 작동하게 합니다. 편집기에서 계속 작동합니다. 편집기에서 재생에 새 플랫폼을 쉽게 추가할 수 있습니다. 앱이 디바이스에서만 작동하는 경우 편집기에서 재생을 작동시키기가 매우 어렵습니다.

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a>주의하여 새 공용 필드, 속성, 메서드 및 직렬화된 프라이빗 필드를 추가합니다.

공용 메서드, 필드, 속성을 추가할 때마다 MRTK의 공용 API 표면의 일부가 됩니다. 로 표시된 프라이빗 필드는 `[SerializeField]` 편집기에도 필드를 노출하며 공용 API 표면의 일부입니다. 다른 사람은 해당 공용 메서드를 사용하고, 공용 필드로 사용자 지정 프리팹을 구성하고, 종속성을 사용할 수 있습니다.

새 public 멤버는 신중하게 검사해야 합니다. 모든 공용 필드는 나중에 유지 관리해야 합니다. 공용 필드(또는 직렬화된 프라이빗 필드)의 형식이 MonoBehaviour에서 변경되거나 제거되면 다른 사람이 중단될 수 있습니다. 필드는 먼저 릴리스에서 더 이상 사용되지 않으며, 의존성이 있는 사용자에 대한 변경 내용을 마이그레이션하는 코드를 제공해야 합니다.

### <a name="prioritize-writing-tests"></a>쓰기 테스트 우선 순위 지정

MRTK는 다양한 기여자가 수정한 커뮤니티 프로젝트입니다. 이러한 기여자는 버그 수정/기능의 세부 정보를 알지 못하고 실수로 기능을 중단합니다. [MRTK는](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) 모든 끌어오기 요청을 완료하기 전에 연속 통합 테스트를 실행합니다. 테스트를 중단하는 변경 내용은 체크 인할 수 없습니다. 따라서 테스트는 다른 사람이 기능을 중단하지 않도록 하는 가장 좋은 방법입니다.

버그를 수정할 때 나중에 재발하지 않도록 테스트를 작성합니다. 기능을 추가하는 경우 기능이 작동하는지 확인하는 테스트를 작성합니다. 실험적 기능을 제외한 모든 UX 기능에 필요합니다.

## <a name="c-coding-conventions"></a>C# 코딩 규칙

### <a name="script-license-information-headers"></a>라이선스 정보 헤더 스크립팅

새 파일에 기여하는 모든 Microsoft 직원은 아래와 같이 새 파일의 맨 위에 다음과 같은 표준 라이선스 헤더를 추가해야 합니다.

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a>함수/메서드 요약 헤더

MRTK에 게시된 모든 공용 클래스, 구조체, 열거형, 함수, 속성, 필드는 아래와 같이 용도 및 사용에 대해 설명해야 합니다.

```c#
/// <summary>
/// The Controller definition defines the Controller as defined by the SDK / Unity.
/// </summary>
public struct Controller
{
    /// <summary>
    /// The ID assigned to the Controller
    /// </summary>
    public string ID;
}
```

이렇게 하면 모든 클래스, 메서드 및 속성에 대한 설명서가 제대로 생성되고 전파됩니다.

적절한 요약 태그 없이 제출된 모든 스크립트 파일은 거부됩니다.

### <a name="mrtk-namespace-rules"></a>MRTK 네임스페이스 규칙

Mixed Reality 도구 키트는 모든 기본 네임스페이스가 "Microsoft.MixedReality.Toolkit"로 시작하는 기능 기반 네임스페이스 모델을 사용합니다. 일반적으로 네임스페이스에서 도구 키트 계층(예: Core, Providers, Services)을 지정할 필요가 없습니다.

현재 정의된 네임스페이스는 다음과 같습니다.

- Microsoft.MixedReality.Toolkit
- Microsoft.MixedReality.Toolkit.Boundary
- Microsoft.MixedReality.Toolkit.Diagnostics
- Microsoft.MixedReality.Toolkit.Editor
- Microsoft.MixedReality.Toolkit.Input
- Microsoft.MixedReality.Toolkit.SpatialAwareness
- Microsoft.MixedReality.Toolkit.Teleport
- Microsoft.MixedReality.Toolkit.Utilities

형식이 많은 네임스페이스의 경우 범위 지정 사용을 돕기 위해 제한된 수의 하위 네임스페이스를 만들 수 있습니다.

인터페이스, 클래스 또는 데이터 형식에 대한 네임스페이스를 생략하면 변경이 차단됩니다.

### <a name="adding-new-monobehaviour-scripts"></a>새 MonoBehaviour 스크립트 추가

끌어오기 요청을 사용하여 새 MonoBehaviour 스크립트를 추가할 때 [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) 특성이 적용 가능한 모든 파일에 적용되는지 확인합니다. 이렇게 하면 구성 요소 추가 단추 아래의 편집기에서 구성 요소를 쉽게 *검색할* 수 있습니다. 구성 요소가 추상 클래스와 같은 편집기에서 표시될 수 없는 경우에는 특성 플래그가 필요하지 않습니다.

아래 예제에서 여기에 있는 *패키지는* 구성 요소의 패키지 위치로 채워야 합니다. *MRTK/SDK* 폴더에 항목을 배치하는 경우 패키지는 *SDK* 가 됩니다.

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a>새 Unity 검사기 스크립트 추가

일반적으로 MRTK 구성 요소에 대한 사용자 지정 검사자 스크립트를 만들지 않도록 합니다. Unity 엔진에서 처리할 수 있는 코드베이스의 추가 오버헤드 및 관리가 추가됩니다.

검사기 클래스가 필요한 경우 Unity의 를 사용해 [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) 보세요. 이렇게 하면 검사기 클래스가 간소화되고 대부분의 작업이 Unity에 남습니다.

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

inspector 클래스에 사용자 지정 렌더링이 필요한 경우 및 를 활용해 [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) 보세요. 이렇게 하면 Unity가 렌더링 중첩된 프리팹 및 수정된 값을 올바르게 처리합니다.

[`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html)사용자 지정 논리의 요구 사항으로 인해 를 사용할 수 없는 경우 모든 사용이 에 래핑되었는지 확인합니다. [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) 이렇게 하면 Unity가 지정된 속성을 통해 중첩된 프리팹 및 수정된 값에 대해 검사자를 올바르게 렌더링합니다.

또한 를 사용하여 사용자 지정 검사자 클래스를 데코레이트해 [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) 보세요. 이 태그는 장면에서 이 구성 요소가 있는 여러 개체를 함께 선택하고 수정할 수 있도록 합니다. 모든 새 검사기 클래스는 해당 코드가 장면에서 이 상황에서 작동하는지 테스트해야 합니다.

```c#
    // Example inspector class demonstrating usage of SerializedProperty & EditorGUILayout.PropertyField
    // as well as use of EditorGUI.PropertyScope for custom property logic
    [CustomEditor(typeof(MyComponent))]
    public class MyComponentInspector : UnityEditor.Editor
    {
        private SerializedProperty myProperty;
        private SerializedProperty handedness;

        protected virtual void OnEnable()
        {
            myProperty = serializedObject.FindProperty("myProperty");
            handedness = serializedObject.FindProperty("handedness");
        }

        public override void OnInspectorGUI()
        {
            EditorGUILayout.PropertyField(destroyOnSourceLost);

            Rect position = EditorGUILayout.GetControlRect();
            var label = new GUIContent(handedness.displayName);
            using (new EditorGUI.PropertyScope(position, label, handedness))
            {
                var currentHandedness = (Handedness)handedness.enumValueIndex;

                handedness.enumValueIndex = (int)(Handedness)EditorGUI.EnumPopup(
                    position,
                    label,
                    currentHandedness,
                    (value) => {
                        // This function is executed by Unity to determine if a possible enum value
                        // is valid for selection in the editor view
                        // In this case, only Handedness.Left and Handedness.Right can be selected
                        return (Handedness)value == Handedness.Left
                        || (Handedness)value == Handedness.Right;
                    });
            }
        }
    }
```

### <a name="adding-new-scriptableobjects"></a>새 ScriptableObjects 추가

새 ScriptableObject 스크립트를 추가할 때 [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) 특성이 적용 가능한 모든 파일에 적용되는지 확인합니다. 이렇게 하면 자산 만들기 메뉴를 통해 편집기에서 구성 요소를 쉽게 검색할 수 있습니다. 구성 요소가 추상 클래스와 같은 편집기에서 표시될 수 없는 경우에는 특성 플래그가 필요하지 않습니다.

아래 예제에서 *하위 폴더는* MRTK 하위 폴더(해당하는 경우)로 채워야 합니다. *MRTK/Providers* 폴더에 항목을 배치하는 경우 패키지는 *공급자 입니다.* *MRTK/Core* 폴더에 항목을 배치하는 경우 "프로필"로 설정합니다.

아래 예제에서 *MyNewService는 | 해당하는 경우 MyNewProvider를* 새 클래스 이름으로 채워야 합니다. *MixedRealityToolkit* 폴더에 항목을 배치하는 경우 이 문자열을 그대로 둡니다.

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a>로깅

새 기능을 추가하거나 기존 기능을 업데이트하는 경우 향후 디버깅에 유용할 수 있는 흥미로운 코드에 DebugUtilities.LogVerbose 로그를 추가하는 것이 좋습니다. 여기에는 로깅 추가와 노이즈가 추가되고 로깅이 충분하지 않음(진단이 어려워지게 함) 간에 절충이 있습니다.

로깅이 유용한 흥미로운 예제는 다음과 같습니다(흥미로운 페이로드와 함께).

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

이 유형의 로깅은 일치하지 않는 소스 검색 및 소스 손실 이벤트로 인해 발생한 와 같은 문제를 catch하는 데 도움이 될 수 [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) 있습니다.

모든 프레임에서 발생하는 데이터 및 이벤트에 대한 로그를 추가하지 않는 것이 좋습니다. 로깅은 고유한 사용자 입력(즉, 사용자의 "클릭"과 로그에 흥미로운 변경 내용 및 이벤트 집합)에 의해 구동되는 "흥미로운" 이벤트를 포함하는 것이 가장 좋습니다. 모든 프레임에 기록된 "사용자가 여전히 제스처를 보유하고 있습니다"라는 지속적인 상태는 흥미롭지 않으며 로그에 과부하가 붙습니다.

이 자세한 정보 로깅은 기본적으로 설정되지 [않습니다(진단 시스템 설정에서](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging)사용하도록 설정해야 합니다).

### <a name="spaces-vs-tabs"></a>공백과 탭

이 프로젝트에 기여할 때 탭 대신 4개의 공백을 사용해야 합니다.

### <a name="spacing"></a>간격

대괄호와 괄호 사이에 공백을 더 추가하지 마십시오.

#### <a name="dont"></a>안 함

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a>수행

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a>명명 규칙

속성에는 항상 `PascalCase` 를 사용합니다. `camelCase`및 필드에 대한 사용을 제외하고 대부분의 필드에 `PascalCase` `static readonly` `const` 사용합니다. 이에 대한 유일한 예외는 필드를 로 serialized해야 하는 데이터 구조에 대한 `JsonUtility` 것입니다.

#### <a name="dont"></a>안 함

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a>수행

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a>액세스 한정자

항상 모든 필드, 속성 및 메서드에 대한 액세스 한정자를 선언합니다.

- 파생 클래스에서 재정의해야 하는 경우가 아니면 모든 Unity API 메서드는 기본적으로 여야 `private` 합니다. 이 경우 `protected` 를 사용해야 합니다.

- 필드는 항상 `private` 또는 속성 접근자를 가진 이어야 `public` `protected` 합니다.

- 가능한 경우 [식 멤버](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) 및 [자동 속성](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) 사용

#### <a name="dont"></a>안 함

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a>수행

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a>중괄호 사용

항상 각 문 블록 다음에 중괄호를 사용하고 다음 줄에 배치합니다.

#### <a name="dont"></a>안 함

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a>안 함

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a>수행

```c#
private Foo()
{
    if (Bar==true)
    {
        DoThing();
    }
    else
    {
        DoTheOtherThing();
    }
}
```

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a>공용 클래스, 구조체 및 열거형은 모두 자체 파일로 이동해야 합니다.

클래스, 구조체 또는 열거형을 private으로 만들 수 있는 경우 동일한 파일에 포함할 수 있습니다.  이렇게 하면 Unity와 관련된 컴파일 문제를 방지하고 적절한 코드 추상화가 발생하도록 하고 코드를 변경해야 할 때 충돌 및 주요 변경 내용도 줄입니다.

#### <a name="dont"></a>안 함

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a>수행

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a>수행

MyStruct.cs

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

MyEnumType.cs

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

MyClass.cs

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a>열거형 초기화

모든 열거형이 0부터 올바르게 초기화되도록 하기 위해 .NET에서는 첫 번째(시작) 값을 추가하여 열거형을 자동으로 초기화하는 깔끔한 바로 가기를 제공합니다. (예: 값 1 = 0 나머지 값은 필요하지 않음)

#### <a name="dont"></a>안 함

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a>수행

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a>적절한 확장에 대한 열거형 순서

열거형이 나중에 확장될 가능성이 있는 경우 열거형 맨 위에 기본값을 정렬하면 열거형 인덱스가 새로운 추가에 영향을 받지 않습니다.

#### <a name="dont"></a>안 함

```c#
public enum SDKType
{
    WindowsMR,
    OpenVR,
    OpenXR,
    None, <- default value not at start
    Other <- anonymous value left to end of enum
}
```

#### <a name="do"></a>수행

```c#
/// <summary>
/// The SDKType lists the VR SDKs that are supported by the MRTK
/// Initially, this lists proposed SDKs, not all may be implemented at this time (please see ReleaseNotes for more details)
/// </summary>
public enum SDKType
{
    /// <summary>
    /// No specified type or Standalone / non-VR type
    /// </summary>
    None = 0,
    /// <summary>
    /// Undefined SDK.
    /// </summary>
    Other,
    /// <summary>
    /// The Windows 10 Mixed reality SDK provided by the Universal Windows Platform (UWP), for Immersive MR headsets and HoloLens.
    /// </summary>
    WindowsMR,
    /// <summary>
    /// The OpenVR platform provided by Unity (does not support the downloadable SteamVR SDK).
    /// </summary>
    OpenVR,
    /// <summary>
    /// The OpenXR platform. SDK to be determined once released.
    /// </summary>
    OpenXR
}
```

### <a name="review-enum-use-for-bitfields"></a>비트 필드에 대한 열거형 사용 검토

열거형이 값으로 여러 상태를 요구할 가능성이 있는 경우(예: 손수 = 왼쪽 & 오른쪽) 그런 다음, 열거형을 BitFlags로 올바르게 데코레이트하여 올바르게 사용할 수 있도록 해야 합니다.

Handedness.cs 파일에는 이에 대한 구체적인 구현이 있습니다.

### <a name="dont"></a>안 함

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a>수행

```c#
[Flags]
public enum Handedness
{
    None = 0 << 0,
    Left = 1 << 0,
    Right = 1 << 1,
    Both = Left | Right
}
```

### <a name="hard-coded-file-paths"></a>하드 코드된 파일 경로

문자열 파일 경로를 생성하고 특히 하드 코드된 문자열 경로를 작성하는 경우 다음을 수행합니다.

1. 또는 와 같이 가능하면 C#의 [ `Path` API를](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) `Path.Combine` `Path.GetFullPath` 사용합니다.
1. \ 또는 대신 / [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) 또는 를 \\ \\ 사용합니다.

이러한 단계를 수행하면 MRTK가 Windows 및 Unix 기반 시스템에서 모두 작동합니다.

### <a name="dont"></a>안 함

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a>수행

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a>Unity 권장 사항을 포함한 모범 사례

이 프로젝트의 대상 플랫폼 중 일부는 성능을 고려해야 합니다. 이 점을 염두에 두고 꽉 찬 업데이트 루프 또는 알고리즘에서 자주 호출되는 코드에 메모리를 할당할 때는 항상 주의해야 합니다.

### <a name="encapsulation"></a>캡슐화

클래스 또는 구조체 외부에서 필드에 액세스해야 하는 경우 항상 전용 필드 및 공용 속성을 사용합니다.  private 필드와 public 속성을 함께 배치해야 합니다. 이렇게 하면 속성을 백업하는 내용과 스크립트로 필드를 수정할 수 있는 필드를 한눈에 쉽게 확인할 수 있습니다.

> [!NOTE]
> 이에 대한 유일한 예외는 에서 필드를 serialization해야 하는 데이터 구조에 대한 것입니다. `JsonUtility` 여기서 데이터 클래스는 serialization이 작동하기 위해 모든 공용 필드를 가져야 합니다.

#### <a name="dont"></a>안 함

```c#
private float myValue1;
private float myValue2;

public float MyValue1
{
    get{ return myValue1; }
    set{ myValue1 = value }
}

public float MyValue2
{
    get{ return myValue2; }
    set{ myValue2 = value }
}
```

#### <a name="do"></a>수행

```c#
// Enable field to be configurable in the editor and available externally to other scripts (field is correctly serialized in Unity)
[SerializeField]
[ToolTip("If using a tooltip, the text should match the public property's summary documentation, if appropriate.")]
private float myValue; // <- Notice we co-located the backing field above our corresponding property.

/// <summary>
/// If using a tooltip, the text should match the public property's summary documentation, if appropriate.
/// </summary>
public float MyValue
{
    get => myValue;
    set => myValue = value;
}

/// <summary>
/// Getter/Setters not wrapping a value directly should contain documentation comments just as public functions would
/// </summary>
public float AbsMyValue
{
    get
    {
        if (MyValue < 0)
        {
            return -MyValue;
        }

        return MyValue
    }
}
```

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a>가능하면 값을 캐시하고 장면/프리팹에서 직렬화합니다.

HoloLens를 염두에 두고 장면 또는 프리팹의 성능 및 캐시 참조를 최적화하여 런타임 메모리 할당을 제한하는 것이 가장 좋습니다.

#### <a name="dont"></a>안 함

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a>수행

```c#
[SerializeField] // To enable setting the reference in the inspector.
private Renderer myRenderer;

private void Awake()
{
    // If you didn't set it in the inspector, then we cache it on awake.
    if (myRenderer == null)
    {
        myRenderer = gameObject.GetComponent<Renderer>();
    }
}

private void Update()
{
    myRenderer.Foo(Bar);
}
```

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a>재질에 대한 참조를 캐시하고 매번 ".material"을 호출하지 않습니다.

Unity는 ".material"을 사용할 때마다 새 재질을 만듭니다. 이 경우 제대로 정리되지 않으면 메모리 누수가 발생합니다.

#### <a name="dont"></a>안 함

```c#
public class MyClass
{
    void Update()
    {
        Material myMaterial = GetComponent<Renderer>().material;
        myMaterial.SetColor("_Color", Color.White);
    }
}
```

#### <a name="do"></a>수행

```c#
// Private references for use inside the class only
public class MyClass
{
    private Material cachedMaterial;

    private void Awake()
    {
        cachedMaterial = GetComponent<Renderer>().material;
    }

    void Update()
    {
        cachedMaterial.SetColor("_Color", Color.White);
    }

    private void OnDestroy()
    {
        Destroy(cachedMaterial);
    }
}
```

> [!NOTE]
> 또는 참조할 때마다 새 재질을 만들지 않는 Unity의 "SharedMaterial" 속성을 사용합니다.

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a>[플랫폼 종속 컴파일을](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) 사용하여 도구 키트가 다른 플랫폼에서 빌드를 중단하지 않도록 합니다.

- `WINDOWS_UWP`UWP 관련 비 Unity API를 사용하려면 를 사용합니다. 이렇게 하면 편집기 또는 지원되지 않는 플랫폼에서 실행하지 못하게 됩니다. 이는 와 `UNITY_WSA && !UNITY_EDITOR` 동일하며 를 위해 사용해야 합니다.
- `UNITY_WSA`를 사용하여 네임스페이스와 같은 UWP 관련 Unity API를 `UnityEngine.XR.WSA` 사용합니다. 플랫폼이 UWP로 설정된 경우 편집기에서 실행되며 빌드된 UWP 앱에서도 실행됩니다.

이 차트는 사용 사례 및 예상하는 빌드 설정에 따라 사용할 를 결정하는 데 도움이 될 수 `#if` 있습니다.

|플랫폼 | UWP IL2CPP | UWP .NET | 편집기 |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | False | False | True |
| `UNITY_WSA` | True | True | True |
| `WINDOWS_UWP` | True | True | False |
| `UNITY_WSA && !UNITY_EDITOR` | True | True | False |
| `ENABLE_WINMD_SUPPORT` | True | True | False |
| `NETFX_CORE` | False | True | False |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a>DateTime을 사용 하 여 UtcNow를 선호 합니다.

UtcNow가 DateTime 보다 빠릅니다. 이전 성능 조사에서 DateTime을 사용 하는 것을 발견 했습니다. 이제 Update () 루프에서 사용 될 때 상당한 오버 헤드를 추가 합니다. [다른 사용자는 동일한 문제에 도달 했습니다](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).

실제로 지역화 된 시간이 필요한 경우를 제외 하 고 UtcNow를 사용 하는 것이 좋습니다. 합법적인 이유는 사용자의 표준 시간대에 현재 시간을 표시 하려고 할 수 있습니다. 상대 시간을 처리 하는 경우 (즉, 마지막 업데이트와 현재 시간 사이의 델타) UtcNow를 사용 하 여 표준 시간대 변환의 오버 헤드를 방지 하는 것이 가장 좋습니다.

## <a name="powershell-coding-conventions"></a>PowerShell 코딩 규칙

MRTK codebase의 하위 집합은 파이프라인 인프라와 다양 한 스크립트 및 유틸리티를 위해 PowerShell을 사용 합니다. 새 PowerShell 코드는 [Poshcode 스타일](https://poshcode.gitbooks.io/powershell-practice-and-style/)을 따라야 합니다.

## <a name="see-also"></a>참조

 [MSDN의 c # 코딩 규칙](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)