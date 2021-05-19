---
title: 코딩 지침
description: MRTK에 영향을 주는 경우 따라야 하는 코딩 원칙 및 규칙입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: 'Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, c #,'
ms.openlocfilehash: 8887e248bd550bdd7a59f19c16df1ec3647ceff7
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145246"
---
# <a name="coding-guidelines"></a>코딩 지침

이 문서에서는 MRTK에 영향을 주는 경우 따라야 하는 코딩 원칙 및 규칙을 간략하게 설명 합니다.

---

## <a name="philosophy"></a>방법은

### <a name="be-concise-and-strive-for-simplicity"></a>간결 하 고 간단 하 게 하기 위해 노력

가장 간단한 해결책은 가장 좋은 방법입니다. 이는 이러한 지침을 재정의 하는 것 이며 모든 코딩 작업의 목표입니다. 간단 하 게 하는 부분은 간결 하 고 기존 코드와 일치 합니다. 코드를 단순하게 유지 해 보세요.

판독기는 유용한 정보를 제공 하는 아티팩트를 발견 해야 합니다. 예를 들어 명확한 사항을 다시 말하지만 하는 주석은 추가 정보를 제공 하지 않으며 신호 비율로 노이즈를 늘립니다.

코드 논리를 간단 하 게 유지 합니다. 이는 가장 적은 수의 줄을 사용 하 여 식별자 이름 또는 중괄호 스타일의 크기를 최소화 하는 것과 관련 된 문이 아니라 개념의 수를 줄이고 친숙 한 패턴을 통해 해당 요소의 표시 유형을 최대화 하는 방법에 대해 설명 합니다.

### <a name="produce-consistent-readable-code"></a>일관성 있고 읽을 수 있는 코드를 생성 합니다.

코드 가독성은 낮은 결함 속도와 상호 관련 됩니다. 읽기 쉬운 코드를 만들기 위해 노력 합니다. 간단한 논리를 포함 하 고 기존 구성 요소를 다시 사용 하는 코드를 생성 하 여 정확성을 유지 하는 데 도움이 됩니다.

가장 기본적인 정확한 세부 정보부터 일관 된 스타일 및 서식 지정까지 생성 되는 모든 코드의 세부 정보입니다. 선호 하는 것과 일치 하지 않는 경우에도 코딩 스타일을 이미 존재 하는 것과 동일 하 게 유지 합니다. 그러면 전체 코드 베이스의 가독성이 향상 됩니다.

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a>편집기와 런타임에 구성 요소 구성 지원

MRTK는 Unity 편집기에서 구성 요소를 구성하고 프리팹을 로드하려는 사용자와 런타임에 개체를 인스턴스화하고 구성해야 하는 사용자 등 다양한 사용자 집합을 지원합니다.

모든 코드는 저장된 장면에서 GameObject에 구성 요소를 추가하고 코드에서 해당 구성 요소를 인스턴스화하여 작동합니다. 테스트에는 프리팹을 인스턴스화하고 인스턴스화하고 런타임에 구성 요소를 구성하는 테스트 사례가 모두 포함되어야 합니다.

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a>편집기에서 재생은 첫 번째 및 기본 대상 플랫폼입니다.

편집기에서 재생은 Unity에서 반복하는 가장 빠른 방법입니다. 고객이 신속하게 반복할 수 있는 방법을 제공하면 솔루션을 더 빠르게 개발하고 더 많은 아이디어를 시도할 수 있습니다. 즉, 반복 속도를 최대화하면 고객이 더 많은 성과를 달성할 수 있습니다.

모든 것이 편집기에서 작동하게 한 다음, 다른 플랫폼에서 작동하게 합니다. 편집기에서 계속 작동합니다. 편집기에서 재생에 새 플랫폼을 쉽게 추가할 수 있습니다. 앱이 디바이스에서만 작동하는 경우 편집기에서 재생을 작동시키기가 매우 어렵습니다.

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a>주의하여 새 공용 필드, 속성, 메서드 및 직렬화된 프라이빗 필드를 추가합니다.

공용 메서드, 필드, 속성을 추가할 때마다 MRTK의 공용 API 표면의 일부가 됩니다. 로 표시된 프라이빗 필드는 `[SerializeField]` 편집기에도 필드를 노출하며 공용 API 표면의 일부입니다. 다른 사람은 해당 공용 메서드를 사용하고, 공용 필드로 사용자 지정 프리팹을 구성하고, 종속성을 사용할 수 있습니다.

새 public 멤버는 신중하게 검사해야 합니다. 모든 공용 필드는 나중에 유지 관리해야 합니다. 공용 필드(또는 직렬화된 프라이빗 필드)의 형식이 MonoBehaviour에서 변경되거나 제거되면 다른 사람이 중단될 수 있습니다. 필드는 먼저 릴리스에서 더 이상 사용되지 않으며, 의존성이 있는 사용자에 대한 변경 내용을 마이그레이션하는 코드를 제공해야 합니다.

### <a name="prioritize-writing-tests"></a>테스트 작성 우선 순위 지정

MRTK는 다양 한 참가자에 의해 수정 되는 커뮤니티 프로젝트입니다. 이러한 참가자는 버그 수정/기능의 세부 정보를 알 수 없으며 실수로 기능을 중단 합니다. [Mrtk](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) 는 모든 끌어오기 요청을 완료 하기 전에 연속 통합 테스트를 실행 합니다. 테스트를 중단 하는 변경 내용은 체크 인할 수 없습니다. 따라서 테스트는 다른 사용자가 기능을 중단 하지 않도록 하는 가장 좋은 방법입니다.

버그를 수정 하는 경우 나중에 회귀 하지 않도록 테스트를 작성 합니다. 기능을 추가 하는 경우 기능이 작동 하는지 확인 하는 테스트를 작성 합니다. 이는 실험적 기능을 제외한 모든 UX 기능에 필요 합니다.

## <a name="c-coding-conventions"></a>C # 코딩 규칙

### <a name="script-license-information-headers"></a>스크립트 라이선스 정보 헤더

새 파일을 사용 하는 모든 Microsoft 직원은 아래와 같이 새 파일의 맨 위에 다음과 같은 표준 라이선스 헤더를 추가 해야 합니다.

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a>함수/메서드 요약 헤더

MRTK에 게시 된 모든 public 클래스, 구조체, 열거형, 함수, 속성, 필드는 아래와 같이 목적 및 사용에 대해 설명 해야 합니다.

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

이렇게 하면 모든 클래스, 메서드 및 속성에 대 한 문서가 적절히 생성 되 고 disseminated 됩니다.

적절 한 요약 태그 없이 제출 된 모든 스크립트 파일은 거부 됩니다.

### <a name="mrtk-namespace-rules"></a>MRTK 네임 스페이스 규칙

Mixed Reality 도구 키트는 기능 기반 네임 스페이스 모델을 사용 합니다. 여기서 모든 기본 네임 스페이스는 "MixedReality"로 시작 합니다. 일반적으로 네임 스페이스에 도구 키트 계층 (예: 핵심, 공급자, 서비스)을 지정할 필요가 없습니다.

현재 정의 된 네임 스페이스는 다음과 같습니다.

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

검사기 클래스가 필요한 경우 Unity의 를 사용해 [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) 보세요. 이렇게 하면 inspector 클래스가 간소화 되 고 작업의 대부분이 Unity로 유지 됩니다.

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

Inspector 클래스에서 사용자 지정 렌더링이 필요한 경우 및를 활용 하세요 [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) . 이렇게 하면 Unity에서 렌더링 중첩 된 prefabs 및 수정 된 값을 올바르게 처리 합니다.

[`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html)사용자 지정 논리의 요구 사항으로 인해을 사용할 수 없는 경우 모든 사용이에 대해 래핑됩니다 [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) . 이렇게 하면 Unity가 지정 된 속성을 사용 하 여 중첩 된 prefabs 및 수정 된 값에 대해 검사기를 올바르게 렌더링 합니다.

또한 사용자 지정 inspector 클래스를로 데코레이팅하 려 고 [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) 합니다. 이 태그는 장면에서이 구성 요소를 사용 하는 여러 개체를 선택 하 여 수정할 수 있도록 합니다. 모든 새 inspector 클래스는 해당 코드가 장면에서이 상황에서 작동 하는지 테스트 해야 합니다.

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

### <a name="adding-new-scriptableobjects"></a>새 스크립트가 추가 된 개체 추가

새 스크립트를 추가할 때 [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) 특성이 적용 되는 모든 파일에 적용 되는지 확인 합니다. 이렇게 하면 자산 만들기 메뉴를 통해 편집기에서 구성 요소를 쉽게 검색할 수 있습니다. 특성 플래그는 구성 요소가 추상 클래스와 같은 편집기에 표시 되지 않는 경우에는 필요 하지 않습니다.

아래 예제에서는 해당 하는 경우 *하위 폴더* 를 MRTK 하위 폴더로 채워야 합니다. *Mrtk/Providers* 폴더에 항목을 배치 하는 경우 패키지는 *공급자* 가 됩니다. *Mrtk/Core* 폴더에 항목을 배치 하는 경우이 항목을 "프로필"로 설정 합니다.

아래 예제에서는 *MyNewService | MyNewProvider* 는 해당 하는 경우 새 클래스 이름으로 채워야 합니다. *MixedRealityToolkit* 폴더에 항목을 배치 하는 경우이 문자열을 비워 둡니다.

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a>로깅

새 기능을 추가 하거나 기존 기능을 업데이트 하는 경우 나중에 디버깅 하는 데 유용할 수 있는 흥미로운 코드에 DebugUtilities LogVerbose 로그를 추가 하는 것이 좋습니다. 로깅 및 추가 된 노이즈를 추가 하는 것 사이에는 장단점이 있으며,이로 인해 진단이 어려워집니다.

유용한 페이로드를 사용 하 여 로깅을 사용 하는 흥미로운 예는 다음과 같습니다.

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

이 로깅 유형은 [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) 일치 하지 않는 소스 검색 및 원본 손실 이벤트로 인해 발생 한 문제를 파악 하는 데 도움이 될 수 있습니다.

모든 프레임에 대해 발생 하는 데이터 및 이벤트에 대 한 로그를 추가 하지 마세요. 가장 적합 한 로깅에는 고유한 사용자 입력 (예: 사용자가 "클릭" 하 고 로그에 관심이 있는 변경 내용 및 이벤트 집합)에 의해 제어 되는 "흥미로운" 이벤트를 포함 해야 합니다. "사용자가 계속 제스처를 보유 하 고 있습니다."의 진행 상태는 모든 프레임에 관심이 없으며 로그에 과부하가 발생 합니다.

이 자세한 정보 표시 로깅은 기본적으로 설정 되어 있지 않습니다 ( [진단 시스템 설정](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging)에서 사용 하도록 설정 해야 함).

### <a name="spaces-vs-tabs"></a>공백 및 탭

이 프로젝트에 참여 하는 경우 탭 대신 4 개의 공백을 사용 하십시오.

### <a name="spacing"></a>간격

대괄호와 괄호 사이에 공백을 추가 하지 마십시오.

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

`PascalCase`속성에는 항상를 사용 합니다. `camelCase`및 필드를 사용 하는 경우를 제외 하 고 대부분의 필드에 사용 `PascalCase` `static readonly` `const` 합니다. 이에 대 한 유일한 예외는에서 필드를 serialize 해야 하는 데이터 구조에 대 한 것입니다 `JsonUtility` .

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

항상 모든 필드, 속성 및 메서드에 대 한 액세스 한정자를 선언 합니다.

- `private`파생 클래스에서 재정의 해야 하는 경우가 아니면 모든 UNITY API 메서드는 기본적으로 여야 합니다. 이 경우에 `protected` 는를 사용 해야 합니다.

- 필드는 항상 `private` `public` 또는 속성 접근자를 사용 해야 합니다 `protected` .

- 가능 하면 [식 본문 멤버](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) 와 [자동 속성](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) 사용

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

각 문 블록 뒤에 중괄호를 항상 사용 하 고 다음 줄에 삽입 합니다.

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

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a>Public 클래스, 구조체 및 열거형은 모두 자체 파일에 있어야 합니다.

클래스, 구조체 또는 열거형을 비공개로 설정할 수 있으면 동일한 파일에 포함 됩니다.  이를 통해 Unity의 컴파일 문제를 방지 하 고 적절 한 코드 추상화가 발생 하지 않도록 하 고 코드를 변경 해야 하는 경우 충돌 및 주요 변경 내용을 줄일 수 있습니다.

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

클래스 또는 구조체 외부에서 필드에 액세스해야 하는 경우 항상 전용 필드 및 공용 속성을 사용합니다.  private 필드와 public 속성을 함께 배치해야 합니다. 이렇게 하면 속성을 백업하는 내용과 스크립트로 필드를 수정할 수 있는 필드를 한눈에 쉽게 볼 수 있습니다.

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
| `NETFX_CORE` | False | True | 거짓 |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a>DateTime.Now보다 DateTime.UtcNow를 선호합니다.

DateTime.UtcNow는 DateTime.Now보다 빠릅니다. 이전 성능 조사에서 DateTime을 사용 하는 것을 발견 했습니다. 이제 Update () 루프에서 사용 될 때 상당한 오버 헤드를 추가 합니다. [다른 사용자는 동일한 문제에 도달 했습니다](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).

실제로 지역화 된 시간이 필요한 경우를 제외 하 고 UtcNow를 사용 하는 것이 좋습니다. 합법적인 이유는 사용자의 표준 시간대에 현재 시간을 표시 하려고 할 수 있습니다. 상대 시간을 처리 하는 경우 (즉, 마지막 업데이트와 현재 시간 사이의 델타) UtcNow를 사용 하 여 표준 시간대 변환의 오버 헤드를 방지 하는 것이 가장 좋습니다.

## <a name="powershell-coding-conventions"></a>PowerShell 코딩 규칙

MRTK codebase의 하위 집합은 파이프라인 인프라와 다양 한 스크립트 및 유틸리티를 위해 PowerShell을 사용 합니다. 새 PowerShell 코드는 [Poshcode 스타일](https://poshcode.gitbooks.io/powershell-practice-and-style/)을 따라야 합니다.

## <a name="see-also"></a>참고 항목

 [MSDN의 c # 코딩 규칙](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)