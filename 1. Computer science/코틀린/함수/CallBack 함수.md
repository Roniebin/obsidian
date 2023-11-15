---
tags:
  - 코틀린
  - 함수
  - ComputerScience
---

키워드 : [[고차함수(Higher-order functions)]] , [[람다함수]] 

--------------

# Callback 함수란 도대체 무엇인가?

- 1. 다른 함수의 인자로써 이용되는 함수.
- 2. 어떤 이벤트에 의해 호출되어지는 함수


# 안드로이드에서 콜백함수란 무엇인가?

- 정의  
    - 함수의 파라미터로 들어온 함수를 콜백함수 라고한다.
    - 콜백함수는 특별한 문법이 있는게 아니라, 호출하는 방식의 측면으로 봐야한다.

- 용도                                                                                          
	- 어떤 함수가 호출되고 순차적으로 다음 작업을 실행할 때 사용한다. 보통 코드는 위에서 부터 순차적으로 실행하지만 비동기처리나, 이벤트 리스터 같은 경우는 순서를 보장해 주지 않기 때문에 콜백함수가 필요한 상황이 생긴다

	- 비동기처리에 주로 사용한다.


	 * 비동기 처리란? => [[동기와 비동기]]

------  

### 콜백 기본예제

``` kotlin
fun first(args:() -> Unit)  
{  
    println("first on")  
    args()  
}  
  
fun second()  
{  
    println("second on")  
}  
  
  
fun main(args : Array<String>?){  
    first(::second)  
}
```

---------------------

## Callback 함수 예제

- callback함수의 첫 번째 정의인 "다른 함수의 인자로써 이용되는 함수"의 관점

```kotlin
package com.example.practice.User  
  
import java.lang.Thread.sleep  
  
val printHello : () ->Unit ={println("Hello")}  
val printBye : () -> Unit = {println("Bye")}  
  
fun sleepAndExecute(sleepTimeSecond : Long, callback:()->Unit)  
{  
    println("sleep and Execute")  
    sleep(sleepTimeSecond)  
    callback()  
}  
  
  
fun main(args : Array<String>?){  
    sleepAndExecute(3000,printHello)  
    sleepAndExecute(5000,printBye)  
}
```

- 두 번째의 "어떤 이벤트에 의해 호출되어지는 함수" 라는 관점
-  "어떤일이 발생했다."

```kotlin
function onCableConnected()
{
	print("케이블이 연결되었습니다.")
}
// 케이블이 연결될 때 마다 전달된 onCableConnected가 호출된다고 가정
setOnCableConnected(onCableConnected)
```

---------------------

## 안드로이드에서 콜백이란 ?

```kotlin
package com.example.practice  
  
import androidx.appcompat.app.AppCompatActivity  
import android.os.Bundle  
import android.os.Handler  
import android.os.Looper  
import android.util.Log  
  
class MainActivity : AppCompatActivity() {  
      
    override fun onCreate(savedInstanceState: Bundle?){  
        //생략  
  
        super.onCreate(savedInstanceState)  
        setContentView(R.layout.activity_main)  
          
        callbackMethod(paramFunc = {  
            Log.d("myTag", "paramFunc 호출됨")  
        })  
    }  
  
    private fun callbackMethod( paramFunc : ()-> Unit){  
        Log.d("myTag","MainActivity called this func")  
        Handler(Looper.getMainLooper()).postDelayed({  
            paramFunc()  
        }, 1000L)  
    }  
}
```

- callbackMethod 가 실행되고 1초 뒤에 paramFunc가 호출되는 코드.

## 매개변수에 람다식이 있는경우 : 고차함수 호출 방법

```kotlin
package com.example.practice.test3  
  
fun highOrder(sum: (Int,Int)-> Int , a:Int,b:Int):Int  
{  
    return sum(a,b)  
}  
  
val sum22: (Int,Int)-> Int ={ a:Int,b:Int ->a+b}  
  
fun abc (x:Int,y:Int):Int{  
    return x+y  
}  
  
fun main()  
{  
    var result:Int  
    var result1:Int  
  
    var result2:Int  
    result=highOrder({x:Int,y:Int->x+y},1,2)        // 람다함수를 매개변수로 던질때  
    result1=highOrder(sum22,1,2)  
    result2=highOrder(::abc,1,2)  // 일반함수를 매개변수로 던질때  
    println(result)  
}
```

-------
# Call By Value

```kotlin
package com.example.practice.User  
  
import java.lang.Thread.sleep  
  
fun callByValue(b:Boolean):Boolean {  // 일반 변수 자료형으로 선언된 매개변수
    println("callbyvalue")  
    return b  
}  
	val lambda :() -> Boolean ={           // 마지막 값만 리턴값으로 반환
    println("lambda ")  
    true   
}  
fun main(args : Array<String>?){  
    val result= callByValue(lambda())  // 람다식함수 호출->값이 넘어감
    println(result)  
  
}  

// 결과 값 
lambda 
callbyvalue
true

```

-------
# Call By Name

```kotlin
package com.example.practice.User  
  
import java.lang.Thread.sleep  
  
fun callByName(b:()->Boolean):Boolean {    //람다식 함수 자료형으로 선언된 매개변수
    println("callbyName")  
    return b()  
}  
val lambda :() -> Boolean ={  
    println("lambda ")  
    true  
}  
fun main(args : Array<String>?){  
    val result= callByName(lambda)             //람다식 이름으로 호출
    println(result)  
  
}

// 결과 값
callbyName
lambda 
true

```

# 다른 함수의 참조에 의한 호출

``` kotlin
package com.example.practice.User  
  
import java.lang.Thread.sleep  
  
fun sum(x:Int,y:Int)=x+y  
  
fun funcParam(a:Int,b:Int , c:(Int,Int)->Int): Int  
{  
    return c(a,b)  
}  
  
fun main(args : Array<String>?){  
    funcParam (3,2,::sum)         // 일반함수를 매개변수로 보낼때 ::를 붙여야함
      
}
```