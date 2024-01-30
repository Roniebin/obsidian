---
tags: react, 코딩애플
---
# URL 파라미터란?

``` javascript

 <Route path="/detail/:id" element={<DetailPage shoes={shoes}/>}/>
 
```

이런식으로 /detail/:id 으로 쓰면
detail/0 ,, detail/1 이렇게 뒤에 아무렇게 와도됨
이후

let {id}=useParams(); 을 통해 :id 자리에 있는 값을 가져옴

# find 함수를 통해 응용도 가능

``` javascript
var idx = props.shoes.find(function(shoe){

    return shoe.id ==id});
```

- 여러 오브젝트 중 urlparams 와 같은 객체를 선택