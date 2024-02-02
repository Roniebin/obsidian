---
tags: 코딩애플, html
---
body 기준

width:80%


이것의 문제 : pc에서 너무큼

# max-width

최대폭을 결정할때 사용

max-width:600px;
하면 최대폭 600px

이때 width는 content영역의 너비를 의미한
그래서 padding 주면 더 커질수있다

# 해결책 

padding,border을 포함해서 max결정해라
 
 - box-sizing:border-box;


# 브라우저 호환성

normalize.css 검색
