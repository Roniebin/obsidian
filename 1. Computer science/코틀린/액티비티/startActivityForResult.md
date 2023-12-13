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



```
```


```

```

```
```

```

```