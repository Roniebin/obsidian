---
tags: ComputerScience, 코틀린
---
# 매니페스트에서 action 및 category의 의미

- `<intent-filter>` 내부의 `<action>` 및 `<category>` 요소는 AndroidManifest.xml 파일에서 컴포넌트(액티비티, 서비스, 브로드캐스트 리시버)에 대한 인텐트 필터를 정의하는 데 사용됩니다

- 특정 종류의 인텐트를 수락하도록 컴포넌트를 구성하는 데 사용됩니다.


### action 요소

- `action`은 컴포넌트가 수락할 인텐트의 액션을 지정합니다.
- 예를 들어, 앱이 특정 액션을 수신하도록하려면 `<action>` 요소를 사용하여 해당 액션을 정의해야 합니다.
- 앱의 컴포넌트는 이러한 액션을 처리할 수 있습니다.

``` kotlin
<intent-filter>
    <action android:name="android.intent.action.MAIN" />
    <action android:name="android.intent.action.VIEW" />
</intent-filter>
```

위의 예제에서는 두 가지 액션을 정의하고 있습니다. 첫 번째 액션은 `MAIN` 액션으로, 앱이 메인 액티비티로 시작될 때 발생하는 액션입니다. 두 번째 액션은 `VIEW` 액션으로, 데이터를 표시하려고 할 때 발생하는 액션입니다.

### category 요소

- `category`는 컴포넌트가 속할 카테고리를 지정합니다.
- 기본적으로 `DEFAULT` 카테고리가 사용되며, 대부분의 경우에는 이 카테고리를 지정합니다.
- 이외에도 다양한 카테고리가 있으며, 특정 동작이나 특성을 갖춘 컴포넌트에 대한 구분을 위해 사용됩니다

``` kotlin
<intent-filter>
    <category android:name="android.intent.category.DEFAULT" />
    <category android:name="android.intent.category.BROWSABLE" />
</intent-filter>

```

위의 예제에서는 `DEFAULT`와 `BROWSABLE` 두 가지 카테고리를 정의하고 있습니다. 대부분의 경우 `DEFAULT` 카테고리를 지정하며, `BROWSABLE`은 브라우저에서 열 수 있는 앱을 나타냅니다.


## 요약

`<action>`은 컴포넌트가 수락할 인텐트의 액션을, `<category>`는 카테고리를 정의합니다. 이러한 요소들은 Android 시스템이 앱의 컴포넌트를 적절한 시점에 호출할 때 사용되는 필터 역할을 합니다.