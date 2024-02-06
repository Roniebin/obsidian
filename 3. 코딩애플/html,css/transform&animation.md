---
tags: html, 코딩애플
---
# 매끄러운 애니메이션 만들기

a- > b
: one-way  : transition 쓰면됨


# @keyframes

# transform 이라는속성

- rotate : 개체를 기울일때
- translateX : 옆으로 이동
- scale : 크기 변화줄때

``` HTML
 @keyframes 왔다갔다{

    0%{

        transform:rotate(0deg);

    }

    50%{

        transform:rotate(10deg);

    }

    75%{

        transform:rotate(-10deg);

    }

    100%{

        transform:rotate(0deg);

    }

}
```

# 왜 transform 쓰면 좋은가

- 성능 좋음

# margin 보다 transform 이 왜 더 빠른가?

- 웹브라우저는 html css코드를 그래픽으로 바꿔주는 간단한 프로그램
- 브라우저가 그림리는 순서
- 1. render tree 만들기 (css 정리한 참고자료)
- 2.layout 잡기 ( 박스그리는거)(width,heightmargin 등)
- 3.paint 하기 (색입히기) (color 속성들)
- 4.composite 처리 (쓸데없는 속도 transform,opacity처리)


- width 갑자기변경하려면 2번 단계를 거침 -> 뒤에있는 단계들도 다 다시해야함
- 근데 만약 color 를 바꾸면 3번단계부터
- 마지막 composite 변경하려면 4번단계만 다시
- 즉 실행속도가 빠르다.


- > 그래서 animation 할떄 transfomr 써라
- transform 이런건 다른쓰레드에서 처리해줌
- 원래 웹브라우저는 쓰레드 1 개만 사용(html,css javascript 다)


# 크기 키우기

 scale(2)