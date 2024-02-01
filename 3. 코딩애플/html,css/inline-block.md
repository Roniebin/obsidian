---
tags: 코딩애플, html
---
# inline-block 이뭐냐

display:block 은 가로행 다차지 
div ,h ,p 등등

display:inline-block 은 크기만큼만 차지

옆으로 나란히 div 배치할때 사용
박스사이 공백제거가 귀찮음


# 상하정렬

 vertical-align:top;

baseline 이 옆에 존재하면 display:inline-block 요소들이 baseline위에 오려고함



# 이렇게도 가능

.navbar li{
    display:inline-block;
}