---
tags:
  - ComputerScience
  - Sort
---
# 기수정렬 

- 각 자리수별로 정렬한다

![[Pasted image 20231117094158.png]]

queue를 자리수의 숫자의크기만큼 만들어놓고 넣는다
ex) 910 이면 0부터 9까지 만들어놓는다

---------
## 2가지 방법

##### LSD 기수 정렬 
- RadixSort는 1의 자리부터 k자리로 진행하는 경우, Least Significant 
    Digit(LSD) 기수 정렬 또는 RL (Right-to-Left) 기수 정렬이라고 부름

- 1의 자리부터하되 안정성을 유지해야한다

####  MSD 기수 정렬
- k자리로 부터 1의 자리로 진행하는 방식은 Most Significant 
   Digit (MSD) 기수 정렬 또는 LR (Left-to-right) 기수 정렬이라고 부름
----------------

- 메모리가 많이 소모되어 많이안쓰임

