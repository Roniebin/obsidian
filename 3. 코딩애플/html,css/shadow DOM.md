---
tags: 코딩애플, html
---
# 숨겨진요소들

ex ) input file 태그

- 개발을 편하게해주기 위해
- file 하나만하면 버튼과 글이나옴

---------------

### 버튼에 배경색을 주고싶으면?

- pseudo-element : 요소 내부의 부분만 스타일 하고싶을때
- 그래서 이때 수도 엘리먼트를 사용

``` CSS
input[type=file] :: -webkit-file-upload-button{
	background:skyblue;
	border:none
}
```

- webkit : 크롬에서만 적용되는 스타일
- 정확히는 사파리 ,edge
- ms : explore
- firefox -moz-

*브라우저마다 shadow dom 까고 하면됨

--------------------

input -> range 나 placeholder 도 마찬가지로
shadow dom 까봐야함


``` CSS 

```