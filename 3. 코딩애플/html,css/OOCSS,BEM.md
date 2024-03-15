---
tags: 코딩애플, html
---

# OOCSS 방식

### Css 가 너무길어졌을때

- 빨간버튼,파란버튼을 만들어야한다면


# 초보들은 이렇게

```CSS
  

.btn-a{
    cursor:pointer;
    padding:15px;
    border:none;
    background:coral;
}

  

.btn-b{
    cursor:pointer;
    padding:15px;
    border:none;
    background:blueviolet;

}
```


# 고수들은 main 뼈대 css 따로 하나만들고

나머지 버튼특징만 따로분리해서 클래스만든다

즉, 뼈대 클래스와 특정한 클래스 이렇게 여러개 만들면됨

``` CSS
.btn{
    cursor:pointer;
    padding:15px;
    border:none;
}

.btn-red{
      background:red;
}
.btn-blue{
      background:blue;
}
```


- 장점
	- 유지보수 편리
	- css양이 줄어듬


# 만들어두면 편한 Utility class

```CSS
.f-small{
	font-size:12px;
}
.f-mid{
	font-size:16px;
}.f-lg{
	font-size:20px;
}
```


# class 작명시 창의력이 딸리면

- BEM :  block_elemnt_modifier
- 지금내가 만드는 덩어리들이 어떤역할을 하는지

```
<div class="profile">
	<<img class="profile__img">
```

- class="덩어리이름__역할--세부특징"