---
tags: 코딩애플, html
---
# SASS 란 무엇인가

- css 대용언어 
- css 는 너무 원시적이고 김
- 조건문,반복문 등 프로그래밍스러운 문법이존재
-  코드한줄로 반복적인 부분을 쉽게 처리가능
- 큰 프로젝트시 도움이 많이됨

-------

# 개발 환경 

extention 에서 sass 다운

-----------------

# scss 는 브라우저가 못읽음

- css 로 변환해야함
- 변환시 extenstions 에서 받은 거 사용

- vscode 아래에 watch ~~ 클릭
- css 파일생성
- map 파일의 용도 : 크롬 개발자도구 디버깅용

------------------


# 사용법

1. 어려운 단어 기억할땐 변수를 쓴다.
	1. $변수명 : 저장해서 쓸값
	2. 사칙연산도 가능

``` CSS
$메인칼라 : #2a4cb2;
$기본사이즈 : 16px

.background{
    color:$메인칼라;
    font-size : $기본사이즈 - 2px;
}
.box{
    color:$메인칼라;
    font-size : $기본사이즈 + 2px;
}
```

 - 저렇게 기본사이즈 만들고 사칙연산으로 포인트 만듬
 - 근데 퍼센트는 사칙연산하면 에러남
- (+ / - ) 로 그냥 사용

 - 사실 css도있음

```CSS
:root {
  --main-color:red;
}

body {
  background-color: var(--main-color)
  font-size : calc(40px-20px)  // 덧셈 뺄셈도 가능
}
```



