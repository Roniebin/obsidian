---
tags:
  - 코틀린
  - 컬렉션타입
  - ComputerScience
---

# Array 배열 표현

- 배열은 Array 클래스로 표현
-  배열의 데이터에 접근할 떄는 대괄호 [] 이용해도되고 set() 이나 get() 함수를 이용할 수도 있음

```kotlin
val data1: Array<Int> = Array(3,{0})  // 크기 3 , 모두 0으로 초기화
  
data1[0]=10  
data1[1]=20  
data1.set(2,30)  
  
println("""  
array size: ${data1.size}  
array data : ${data1[0]} , ${data1[1]} , ${data1.get(2)}  
"""  
)
```

### 기초 타입의 배열

- 기초 타입이라면 Array를 사용하지않고 Boolean , CharArray, DoubleArray, IntArray 클래스들을 사용할 수도있음

```kotlin
val data1: IntArray= IntArray(3,{0})  
val data2:BooleanArray= BooleanArray(3,{false})
```

- arrayOf() 라는 함수를 이용하면 배열을 선언할 때 값을 할당 할 수 도있음
-  기초타입을 대상으로하는 booleanArrayOf(), intArrayOf() 등등 제공

```kotlin
val data3 = intArrayOf(10,20,30)
```

--------------------
