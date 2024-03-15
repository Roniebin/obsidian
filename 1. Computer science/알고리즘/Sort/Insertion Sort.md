---
tags: ComputerScience, Sort
---
- 배열을 정렬된 부분(앞부분)과 정렬 안된 부분(뒷부분)으로 나누고, 정렬 안 된 부분의 가장 왼쪽 원소를 정렬된 부분의 적절한 위치에 삽입하여 정렬되 도록 하는 과정을 반복

![[Pasted image 20231110133611.png]]


# 수도코드

![[Pasted image 20231110141707.png]]

# 실습코드

``` python
A=[6,4,3,5,7,8,9,1,2,88]
n=len(A)

for i in range(1,n):
    CurrentElement=A[i] # 정렬안된 부분의 가장 왼쪽원소
    j=i-1
    while(j>=0) and A[j]>CurrentElement:
        temp=A[j+1]
        A[j+1]=A[j]
        A[j]=temp
        j=j-1

    A[j+1]=CurrentElement

print(A)
```

## 시간복잡도

![[Pasted image 20231110141726.png]]

하지만 삽입정렬의 best case 는 O(N)

평균 case 는 O(n^2)