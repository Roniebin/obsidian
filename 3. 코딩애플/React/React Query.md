---
tags:
  - 코딩애플
  - react
---
# [[AJAX]] 성공/실패시 html 보여주려면?

- 몇초마다 자동으로 ajax 요청?
- 실패시 몇초후 요청재시도?
- prefetch?
- 이것들 쉽게 구현가능

# React Query

(항상 유용하진 않음)
실시간 데이터를 계속 가져와야하는 사이트들이 쓰면 굿



``` javascript
 let result=useQuery('작명',()=>{
    return axios.get("https://codingapple1.github.io/userdata.json").then((a)=>{
      return a.data
    })

  })
```

- 이렇게 useQuery로 감싸면 장점
- 1. 성공/실패/로딩중 쉽게 파악가능
- result 출력시 ajax와 관련된 유용한것들이 나옴

 result.data : 성공시에 데이터
 result.isloading : 로딩중일때 이게 true 가됨
 result.error : 실패시 true 가됨

로딩중일때 로딩중입니다 띄우고 싶으면


틈만나면 재요청해줌 == refetch

state 공유 안해도됨 

ajax 결과 캐싱기능

