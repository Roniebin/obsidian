---
tags: 코딩애플, html
---
``` CSS
.grid-container{
    display:grid;
    
    grid-template-columns: 100px 100px 100px; //세로

	grid-template-rows: 100px 100px;//가로

}
```


# fr단위

- fraction
- 몇 등분한다
- 1배씩 차지


# 레이아웃 늘리기

``` CSS
.grid-nav{

    grid-column:1/4;
	// 세로선 5개중 1부터 4까지
	
}
```


# 자식에 이름쓰고 부모는 색칠

```CSS
.grid-container{

    display:grid;
    grid-template-columns: 100px 100px 100px 100px;
    grid-template-rows: 100px 100px 100px;
    grid-template-areas:
    "헤더 헤더 헤더 헤더"
    "사이드 . . ."
    "사이드 . . ."
}

.grid-container div{
    border:1px solid black;
}


body{
    background-color: blue;
}


.grid-nav{
    grid-area:헤더;
}

  
.grid-sidebar{
    grid-area:사이드;
}
```