---
tags: ComputerScience, 코틀린
---
# Intent 란 무엇인가

- "Intent"는 안드로이드 애플리케이션에서 컴포넌트 간에 통신이나 작업을 시작하기 위한 메시지 객체입니다. 안드로이드에서 Intent는 다음과 같은 몇 가지 주요 용도로 사용됩니다:

1. **액티비티 간의 전환(Activity Transition):** 가장 일반적으로 사용되는 용도 중 하나입니다. `Intent`를 사용하여 현재 실행 중인 액티비티에서 다른 액티비티로 이동할 수 있습니다.


``` kotlin
val intent = Intent(this,SubActivity :: class.java) // 다음 화면으로 이동하기위한 인텐트 객체 생성  
startActivity(intent)
```

2. **액티비티 간 데이터 전달(Data Passing):** `Intent`를 사용하여 데이터를 액티비티 간에 전달할 수 있습니다. 예를 들면 다음과 같습니다:
``` kotlin
intent.putExtra("key", "value");
```

3. **시스템 서비스와의 상호 작용:** `Intent`를 사용하여 시스템 서비스와 상호 작용할 수 있습니다. 예를 들면 카메라 앱을 호출하여 사진을 찍는 등의 작업이 포함될 수 있습니다

1. **브로드캐스트 메시지 송신(Broadcasting):** `Intent`를 사용하여 애플리케이션 내부나 시스템에서 발생한 이벤트를 다른 애플리케이션에 알릴 수 있습니다.



안드로이드에서 `Intent`는 애플리케이션 컴포넌트 간에 작업을 트리거하고 데이터를 전달하는 중요한 메커니즘입니다. 액티비티, 서비스, 브로드캐스트 리시버 등과 함께 다양한 컴포넌트에서 사용됩니다.

----------------------------------------

## 코틀린에서 안드로이드 앱을 개발할 때, Activity를 등록

**안드로이드 매니페스트 파일 수정:**

- `AndroidManifest.xml` 파일에서 액티비티를 등록해야 합니다.
- `<application>` 요소 안에 새로운 `<activity>` 요소를 추가합니다.

```kotlin
<application
    ...>
    <activity android:name=".YourActivity">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />
            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
    </activity>
</application>


```


### 1. `MAIN` Action:

`MAIN`은 앱의 주 진입점(activity)을 나타냅니다. 이는 사용자가 앱을 실행할 때 시작되는 주요 액티비티를 지정하는 데 사용됩니다.

### 2. `LAUNCHER` Category:

`LAUNCHER`는 앱의 시작 아이콘으로부터 시작된다는 것을 나타냅니다. 이것은 사용자가 디바이스 홈 화면에서 앱 아이콘을 탭하여 앱을 시작할 때 사용됩니다


위의 코드에서 ".YourMainActivity"는 앱의 메인 액티비티 클래스를 나타냅니다. 이 액티비티가 앱의 주 진입점이며, 또한 디바이스 홈 화면에서 시작될 수 있는 액티비티임을 나타냅니다.