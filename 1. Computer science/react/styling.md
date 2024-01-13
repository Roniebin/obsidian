# Css 란

- Cascading style sheets (스타일링을 위한 언어)
- 계단식 스타일 시트
- element에 스타일이 적용되는 규칙 => Selector

# Css의 기본문법

크게 selector 와 style로 구성

h1 {color : green;font-size ;16px}
selector 나오고 style 나온다


# selector 의 유형

1. Element selector
	1. 선택자의 이름을 선택

``` CSS
h1 {
   color:green;
   }
```

1. ID selector

``` CSS
#section{
	background-color:black
}
```

1. Class selector
```CSS
 .medium{
 font-size:20px
 }
```

#### element selector 와 Class selector를 함께 사용할수도있음

``` CSS
p.medium{
   font-size :20px;
}

h1.medium{
	font-size:20px
}
```

1. Universal selector
	- 전체 element
```Css
*{
   font-size:20px;
   color:blue;
}
```


1 . Grouping selector
- 여러선택자를 그룹으로 묶어 하나의 스타일을 적용

```CSS
h1{
color:black}

```