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