---
tags:
  - ComputerScience
  - Sort
---
# 버블정렬 (Bubble Sort)

- 이웃하는 숫자를 비교하여 작은 수를 앞쪽으로 이동시키는 과정을 반복하여 정렬
- 작은 수는 배열의 앞부분으로 이동하는데, 배열을 좌우가 아니라 상하로 그려보면 정렬하는 과정에서 작은 수가 마치 <mark style="background: #FF5582A6;">거품처럼 위로 올라가는 것</mark>을 연상케 함

![[Pasted image 20231110121953.png]]
- 패스 (pass): 입력은 전반적으로 1번 처리하는 것
- 1번째 pass 결과를 살펴보면, 작은 수는 버블처럼 위로 1칸씩 올라감
- 가장 큰 수인 90은 맨 밑에, 즉, 배열의 가장 마지막에 위치
	-> 즉, 가장 큰 값은 항상 맨뒤로 -> 맨뒤에서 부터 앞으로 버블 처럼 정렬

# 수도코드

![[Pasted image 20231110122149.png]]

# 실습코드

``` python
A=[5,32,7,2,4,7,8,9,1,53]
n=len(A)

for i in range(1,n):  # 1패스 부터 n-1까지 패스는 총 n-1번 함
    for j in range (1,(n-i)+1): # 이전값을 뽑아와야하기에 1부터 시작하고 1패스할때마다 j범위는 1씩 줄어듬
        if A[j-1]>A[j]:         # 앞의 위치가 현재위치보다 크면 자리체인지
            temp=A[j-1]
            A[j-1]=A[j]
            A[j]=temp

print(A)
```

## 시간복잡도

![[Pasted image 20231110124113.png]]

