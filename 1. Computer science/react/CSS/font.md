---
tags: ComputerScience, react
---
# font 와 관련된 대표적인 속성

``` CSS
#title{
	font-family : "사용할 글꼴 이름", <일반적인 글꼴 분류>;
	font-size:value;
	font-weight:normal|bold
	font-style:normal|italic|oblique;
}
```


# font-family

- 어떤 글꼴을 사용할것인지 결정
- 주의점 : 글꼴이름 띄어쓰기시 큰따옴표로 묶어야함

일반적인 글꼴 분류

serif
 각 글자의 모서리에 작은 테두리를 갖고있는 형태의 글꼴
sans-serif
 모서리에 테두리가 없어 깔끔한 선을 가짐
 컴퓨터의 모니터에서는 serif보다 가독성이 좋음
monospace
 모든 글자가 같은 가로길이를 가진 글꼴, 코딩시 주로사용
cursive
 사람이 쓴 손 글씨 모양의 글꼴
fantasy
 장식이 들어간 형태의 글꼴

# font size
px, em ,rem ,vw

px : 고정
em : 사용자가 글꼴크기 변경가능

16&em=pixel

1em == 16px

# font-weight

bold,500


# font-style

글꼴 스타일지정

normal, 일반적 글자형태
italic : 글자가 길울어진형태
oblique : 글자가 비스듬한 형태로 나타남


# 기타 많이 사용하는 속성

![[Pasted image 20240113213508.png]]

``` 
background-color:color |transparent //배경색 투명하게 할때
```

# border

- 테두리를 위한속성

border : border-width, border-style,border-color

border:1px solid black













