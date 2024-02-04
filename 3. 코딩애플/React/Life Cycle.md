---
tags: react, 코딩애플
---
# Life Cycle

- 페이지에 장착되다 (mount)
- 가끔 업데이트 된다 (update)
- 필요없으면 제거된다 (unmount)


# 이걸 왜 배우나?

- 이걸알면 내가 거기에 간섭 할 수 있다
- 간섭 == 코드실행
- hook == 갈고리
- ex) useEffect

# useEffect

- mount , update 시 코드 실행해주는 useEffect

# 의문 : 근데 그냥 html에 쓰는거랑 같지않나?

# 왜쓰는가?

- useEffect는 실행시간이 약간다름
- 랜더링이 다되고나서 실행이됨
- <mark style="background: #FF5582A6;">html 다 끝나고 실행이 됨</mark>
- 빠른 느낌을 줄 수 있음

----------------

# 이럴때 많이씀

#### 어려운 연산
#### 서버에서 데이터 가져오는작업
#### 타이머 장착하는거


# side Effect

- 함수의 핵심기능과 상관없는 부가기능


``` javascript
  useEffect(()=> {
    setTimeout(()=>{
      setDiscount(false);
    },2000)
  },[])
```

[] 이 없으면 update 나 mount 될때마다 실행됨

[] 안에 뭐가있으면 이안에 있는게 바뀌면 실행이되는거
위처럼 짜면 1회만 실행됨

[] 없으면 update 될때마다 됨



# 정리

- 재랜더링마다 코드실행하고싶으면
- 로드될때 딱한번만 뒤에 ,[] 이거넣으셈
- 컴포넌트 삭제될때 딱한번 할때
- return() 넣으셈 이안에 cleanup 함수 쓰셈
- 