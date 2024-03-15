---
tags: ComputerScience, react
---
# 갈고리

# Hook 이란?

- state 관련함수
- lifecyle 관련함수
- 최적화 관련함수

모든 함수는 use로 시작

# useState()

- state 를 사용하기 위한 Hook

# 왜 변수에 ++ 로 올리는게아니라 setCount 등 함수로 업데이트?

- 직접적으로 변수를 수정하거나 `++` 연산자를 사용하면 React가 이를 감지하지 못해 제대로 동작하지 않을 수 있습니다.

``` jsx
import React, { useState } from 'react';

function ExampleComponent() {
  const [count, setCount] = useState(0);

  const incrementCount = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={incrementCount}>Increment Count</button>
    </div>
  );
}

export default ExampleComponent;
```

- `count++`와 같은 표현은 React에게 상태 변경이 발생했음을 알리지 않기 때문에 권장되지 않습니다.

# useState() 사용법

``` jsx
const [변수명,set함수명] =useState(초기값);
```

리턴값으로 배열이나옴


# useEffect()

- side effect를 수행하기 위한 Hook
   == 효과 , 영향 (부정적 의미 x)
- 다른 컴포넌트에 영향을 미칠 수 있으며, 렌더링 중에는 작업이 완료될 수 없기 때문

# useEffect() 사용법

```jsx
useEffecdt(이펙트 함수, 의존성 배열);
```

```jsx
useEffect(()=>{
// 컴포넌트가 마운트 된 이후,
// 의존성 배열에 있는 변수들 중 하나라도 값이 변경되었을 때 실행됨
// 의존성 배열에 빈 배열([])을 넣으면 마운트와 언마운트 시 단 한 번씩만 실행됨
// 의존성 배열 생략 시 컴포넌트 업데이트 시마다 실행됨
... 

return () => {
 // 컴포넌트가 마운트 헤제 되기 전에 실행됨
 ...
}
}, [의존성 변수1, 의존성 변수2], ...)
```


----------------

# useMemo() 란

Memoized value를 리턴하는 Hook

Memoized: 비용이높은, 호출결과를 저장해두었다가 ,이전에 저장된것을 반환 => 최적화를 위함

``` jsx
const memoizedValue = useMemo(
	() => {
		// 연산량이 높은작업 을 수행하여 결과를 반환
		return computeExpensiveValue(의존성 변수1 , 의존성 변수 2);
		
	},
	[의존성 변수1, 의존성 변수2]
)
```

- 의존성배열에 들어있는 변수가 변했을때만 새로 create함수로 결과값 반환
- 그게아니면 기존값 반환
- 랜더링할때 높은 연산량의 작업을 반복하는것을 피할수있음 => 빠른 랜더링 속도를 얻을수 있음

- 랜더링이 일어날때 실행되면 안될것을 넣으면 안됨
- useEffect에서 실행되야할 side Effect 같은것들
- 서버에서 데이터를 받아오거나 수동변경 = > 랜더링시 실행되면안됨

# useCallback()

- 값이 아닌 함수를 반환
- 의존성 배열값이 바뀌면 함수를 반환

``` jsx
const memoizedCallback = useCallback(
	()= >{
		doSomething(의존성 변수1, 의존성 변수2);
	},
	[의존성 변수1, 의존성 변수2]
)
```

# useRef()

reference 사용을위함

``` jsx
const refContainer=useRef(초기값);
```

변경가능한  current 를 가진 하나의 상자

-매번랜더링댈때 같은 reference 객체 리턴

내부데이터가 변경되었을때 별도로 알리지않는다
= > Callback ref 사용

--------------

# 훅의 규칙

1. <mark style="background: #FF5582A6;">무조건 최상위 레벨에서만 호출해야함</mark> => 조건문,반복문에서 호출하면 안됨
- 컴포넌트가 랜더링될때마다 매번같은순서로 호출되야함 
- 이렇게해야 다수의 useState훅과 useEffect훅 의 호출에서 state를 올바르게 관리가능

1. <mark style="background: #FF5582A6;">리엑트 함수 컴포넌트에서만 호출</mark>
- 일반 자바스크립트 함수 X


