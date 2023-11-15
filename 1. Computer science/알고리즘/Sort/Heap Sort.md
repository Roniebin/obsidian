---
tags:
  - ComputerScience
  - Sort
---
# 이진 힙

- 힙 조건을 만족하는 <mark style="background: #FF5582A6;">완전 이진 트리</mark>
- 힙조건 : 각 노드 우선순위가 자식노드의 우선순위 보다 높음
- 최대힙 : 가장 큰 값이 root에 저장
- 최소힙 : 가장 작은 값이 root에 저장

![[Pasted image 20231115165004.png]]

#### Heap의 노드 관계 • 힙에서 부모와 자식의 관계 

- A[i]의 부모 = A[i/2] 
- 단, i가 홀수이면 i/2에서 정수 부분만 
- A[i]의 왼쪽 자식 = A[2i] 
- A[i]의 오른쪽 자식 = A[2i+1]
