---
tags:
  - ComputerScience
  - Sort
---
# 선택정렬 (Selection Sort)

- 입력 배열 전체에서 <mark style="background: #FF5582A6;">최솟값을 선택</mark>하여 배열의 0번 원소와 자리를 바꾸고, 다음엔 0번 원소를 제외한 나머지 원소에서 최솟값을 선택하여, 배열의 1번 원소와 자리를 바꿈

## 수도코드

![[Pasted image 20231110125056.png]]


# 실습코드

``` python
A=[6,4,3,2,1,10,7,8]
n=len(A)

for i in range(0,n):    
    min=i                   # 스타트 위치를 최소로 일단둠
    for j in range(i+1,n):  # 스타트 다음위치부터 끝까지돌림
        if A[j]<A[min]:     # 스타트 다음위치부터 최소인덱스안과비교해 가장 최소값의 인덱스번호 추출
            min=j
    temp=A[i]
    A[i]=A[min]
    A[min]=temp

print(A)
```


## 시간복잡도

![[Pasted image 20231110132309.png]]


## 삽입정렬

