# styled-components?


## 장점

- Css 파일 안열어도됨
- 다른 자바스크립트 파일 간섭 X , (이 페이지에만 적용되기때문)
- 로딩시간이 단축됨 -> 홈페이지구동에 필요한 css만 딱 로딩할수있기때문

# 대체 법
- App.module.css 이렇게 css파일을 작명해도 됨


# 나만의 버튼을 만들때 색을 다르게

``` CSS
let YellowBtn=styled.button`
  background : ${props => props.bg};
  color:${props => props.bg== 'orange' ? 'white':'black'};
  padding:10px;

`
`
```

- props 로 저렇게 뚤어놓으면 버튼을 저 props 로 만들어주세요
