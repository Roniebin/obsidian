---
tags:
  - 코틀린
  - 컬렉션타입
  - ComputerScience
---
# List,Set,Map

- List : 순서가 있는 데이터의 집합으로 데이터의 중복을 허용합니다.
-  Set : 순서가 없으며 데이터의 중복을 허용하지 않음
-  Map : 키와 값으로 이루어진 데이터의 집합으로 순서가 없으며 키의 중복을 허용하지 않음

Collection 타입의 클래스는 가변 클래스와 불변 클래스로 나뉨.
- 불변 클래스  : 초기 데이터 대입이후 변경 불가
-  가변 클래스 : 초기 대입이후 변경 또는 추가 가능


```kotlin
var data1=listOf<Int> (10,20,30)  
var data2=mutableListOf<Int>(10,20,30)  
  
data1[2]=2  // 에러 !!
data2.add(2,20)  // 2번자리에 20 이라는 값을 추가 (사이즈가 늘어남)

println("""  
    data1 size : ${data1.size}  
    data1 : ${data1[0]},${data1[1]},${data1[2]}  
    data2 size : ${data2.size}  
    data2 : ${data2[0]},${data2[1]},${data2[2]}  
    """.trimIndent())
```

#### add 와 set 차이

- `set`은 리스트 내 특정 위치의 요소를 변경하거나 대체하는데 사용되고, `add`는 자리에 새로운 요소를 추가하는데 사용됩니다.

-----------------------------------
# Map


- 키와 값으로 이루어진 데이터의 집합
-  Pair 객체를 이용 할 수도있고, '키 to 값' 형태로 이용할수도 있음

``` kotlin
var map=mapOf<String,String>(Pair("one","Hello") , "two" to "World" , "three" to "Worlddd")  
  
println("""  
    map size : ${map.size}  
    map : ${map.get("one")} , ${map.get("two")} ,${map["three"]}  
""".trimIndent())
```