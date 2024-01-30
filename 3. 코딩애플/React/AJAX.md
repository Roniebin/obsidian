---
tags:
  - react
  - 코딩애플
---
# AJAX 개념설명


서버에 데이터를 요청한다

서버 : 부탁하면 들어주는 프로그램

1. get / post
2. url


get 과 url 보내면 웹툰이온다

post 와 url 로 포스팅 할수도잇다


AJAX로 get요청가능
- 새로고침 없이도 데이터를 주고받을수있다
  
``` javascript
 <button onClick={()=>{axios.get('https://codingapple1.github.io/shop/data2.json')
.then((data)=>{console.log(data.data)})
.catch(()=>{
 console.log("실패")
  })
 }}>버튼</button>
```


-------------------------------
# post 할떄

``` javascript
   axios.post('/satdfds',{name : 'kim'})
```

# 많은 url에 한번에 보낼때

``` javascript
 Promise.all([axios.get('/url1'),axios.get('/url2')]).then(()=>{})
```


- JSON 데이터는 문자 취급이라 object데이터라도 전송,get가능
- 원래 문자데이터만 서버와 주고받을수있음


- 도착시 axios 가 array 로 바꿔주는거임


# fetch

- 쓰면 array로 바꾸는 작업을 따로 필요로함
- axios의 편리한점이 나타남
