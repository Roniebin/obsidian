---
tags:
  - 코틀린
  - 함수
  - ComputerScience
---
# 고차 함수

- 고차 함수란 함수를 매개변수로 전달받거나 반환하는 함수를 의미

- 일반적으로는 람다식을 매개변수로 받거나 결과로 리턴  하는 함수를 의미함

- 코드 조각을 람다로 만들면 코드 중복 제거(고차 함수 목적)

```kotlin

fun calculator(a:Int ,b:Int, operation:(Int,Int)->Int)= operation(a,b)  
  
fun calculator1(a:Int ,b:Int, operation:(Int,Int)->Int) : Int{  
    return operation(a,b)  
}

fun main(args : Array<String>?){  
    val sum={x:Int,y:Int->x+y}  
    println(calculator(1,2,sum))  
    println(calculator(4,3, {a:Int,b:Int -> a-b}))  
}

```


------

이거 질문

``` kotlin

package com.example.practice.User  
  
import java.lang.Thread.sleep  
  
fun hofFun(arg:(Int)->Boolean):()->String  
{  
    val result=if(arg(10))  
    {  
        "valid"  
    }else {  
        "invalid"  
    }  
    return {"hofFun : $result"}  
  
}  
  
fun hofFun1(no1:Int,no2:Int,c:(Int,Int)->Int):Int {  
  
    return c(no1,no2)  
}  
  
fun main(args : Array<String>?){  
  
    val cc={no1:Int->no1>0}  
    val result=hofFun(cc)  
    println(result())  
  
  
    val sum={no1:Int,no2:Int -> no1+no2}  
    val a= hofFun1(1,3,sum)  
    println(a)  
}
```
---------------
