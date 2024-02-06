---
tags: html, 코딩애플
---
# SASS 핵심문법


# .scss 와 .sass 파일의 차이

- sass 파일은 괄호없이도 사용가능
- 택 1하면됨


# nesting 문법

``` CSS

.main-bg h4{
 font-size :16px;
}
 .main-bg button{
 color:red
 }
}

// 이런식으로 사용

.main-bg {
	h4{

	}
	.main-bg button{
	 color:red
	 }
}
```

- 관련있는 class 들 묶을때 좋음

# @extend 문법 

- class를 복사할때 사용
- 버튼을 여러개를 만들어야함-
- 빨간, 파란,초록 버튼


``` CSS

.btn-green
{
	width:100px;
	height:100px;
	padding:20px;
	color:green;
}

.btn-red
{
	width:100px;
	height:100px;
	padding:20px;
	color:red;
}

.btn-blue
{
	width:100px;
	height:100px;
	padding:20px;
	color:blue;
}


```

- 위의 코드를 밑으로

``` CSS
%btn{
	width:100px;
	height:100px;
	padding:20px;

}

// 변수와 다르게 여러줄가능한 @extend
.btn-green{
	@extend %btn;
	color:green
}

```


# 임시클래스는 단독으로 컴파일안됨

- 어디 넣으셈


----------------------

# @mixin 문법

상황가정

- 긴 코드를 짧은 단어로 축약할때 사용
- 긴 코드를 가변적으로 만들때 

```CSS

@mixin 폰트스타일($구멍){
	font-size:$구멍;
	letter-spacing:-1px;
}

h2{
 @include 작명(30px)
}
h3{
 @include 작명(20px)
}
h4{
 @include 작명(10px)
}

```

글자 중간에 $변수나 $파라미터넣을땐
#{$변수명}


-------------------

컴파일하기싫은파일은 _ 붙이기
_

# 다른파일 가져오기

- reset파일
- @use '/css/_reset';
# 다른파일 변수쓰려면

파일명.%변수


# 다른파일 mixin 쓰려면

@include파일명.mixin이름