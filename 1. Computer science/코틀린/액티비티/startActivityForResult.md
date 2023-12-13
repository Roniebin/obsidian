---
tags: ComputerScience, 코틀린
---
일반적으로 **Activity**를 띄울 때는 **startActivity**()를 사용한다.
다른 방법으로는 **startActivityForResult**()도 있다.

### **1. 용도 차이**

**startActivity** : 새 액티비티를 열어줌 (**단방향**)

**startActivityForResult** : 새 액티비티를 열어줌 + 결과값 전달 (**쌍방향**)

**즉,** **결과값을 전달해주느냐 아니냐의 차이다.**

### **2. 실행 코드**

**- MainActivity에서 -> SubActivity를 여는 경우**


![[Pasted image 20231203161215.png]]끝에 인자 값으로 하나 더 들어가는 것을 볼 수 있다. ('**0**')
**int형 requestCode**인데 -> **원하는 숫자**를 넣어주면 된다.
여러 액티비티를 쓰는 경우, **어떤 Activity인지 식별하는 값**이다

## 3. startActivityForResult 사용법 예제

#### 1 **) startActivityForResult()**

****MainActivity에 작성한다.****

**MainActivity에서 SubActivity를 연다.**

#### 2**) setResult()**

**SubActivity 종료 시점에 작성한다.**

**RESULT_OK 또는 RESULT_CANCEL을 보내도 된다.**


#### **3) onActivityResult()**

**MainActivity에 작성한다.**

**결과를 받는 곳이다.**

출처: [https://jhshjs.tistory.com/49](https://jhshjs.tistory.com/49) [독학하는 1인 개발자:티스토리]



``` kotlin

// 메인 액티비티에서 다른 액티비티를 시작하는 코드
val intent = Intent(this, OtherActivity::class.java)
val requestCode = 123 // 양의 정수로 지정
startActivityForResult(intent, requestCode)
```


```kotlin
// OtherActivity에서 결과를 설정하는 코드
val resultIntent = Intent()
resultIntent.putExtra("resultKey", "Hello from OtherActivity!")
setResult(Activity.RESULT_OK, resultIntent)
finish()
```

```kotlin
// 메인 액티비티에서의 onActivityResult 메서드
override fun onActivityResult(requestCode: Int, resultCode: Int, data: Intent?) {
    super.onActivityResult(requestCode, resultCode, data)
    
    if (requestCode == 123) { // 요청 코드가 일치하는지 확인
        if (resultCode == Activity.RESULT_OK) {
            // 결과가 성공적으로 돌아왔을 때의 처리
            val resultData = data // 여기서 resultData에 결과 데이터가 들어 있습니다.
            val resultValue = data?.getStringExtra("resultKey")
            // 결과값을 사용하여 처리
            Log.d("MainActivity", "Result from OtherActivity: $resultValue")
        } else {
            // 결과가 실패했거나 취소된 경우의 처리
        }
    }
}

```
