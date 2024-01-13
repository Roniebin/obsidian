---
tags: ComputerScience, react
---
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


--------------------

1 . Grouping selector
- 여러선택자를 그룹으로 묶어 하나의 스타일을 적용

```CSS
h1{
color:black
}

h2{
 color:black
}

p{
color:pink
}
```

```CSS
h1,h2,p{
color:black
}
```

# Element 의 상태와 관련된 selector

1. hover
	1. 마우스 커서가 element위에 올라왔을때,
2. active
	1. 주로 <a> 태그 (link)에 사용되는데, element가 클릭됬을때를 의미
2.  focus
		 주로 input 태그에 사용되는데 element가 초점을 갖고있을 경우를 의미
	4. checked
		 radio button이나 checkbox같은 유형의 input 태그가 체크되어있는경우를 의미
	5. first-child , : last-child
		 상위 element를 기준으로 각각 첫 번째child, 마지막 child일 경우를 의미



