---
tags:
  - 알고리즘
  - Sort
  - ComputerScience
---
# 분할 정복 알고리즘 (Divde and Conquer)

**- 주어진 문제의 입력을 분할 하여 문제를 해결 하는 방식의 알고리즘**  

    - 분할한 입력에 대하여 각각 동일한 알고리즘을 적용하여 해를 계산
    - 이들의 해를 취합하여 원래 문제의 해를 구함


# 정의

- 입력이 2개인 부분 문제로 분할
- 부분 문제의 크기가 ½로 감소하는 divide and conquer 알고리즘 
- n개의 숫자들을 n/2개씩 2개의 부분 문제로 분할
- 각각의 부분 문제를 순환으로 합병 정렬
- 2개의 정렬된 부분을 합병하여 정렬 (정복) 
- 합병 과정이 문제를 정복하는 과정


## 입력 크기가 n일 때 총 분할 횟수

#### 총 분할 횟수: k 라고 가정

▪ 1번 분할 후 각 입력 크기: n/2
▪ 2번 분할 후 각 입력 크기: n/22 

▪                      ⋮

▪ k번 분할 후 각 입력 크기: n/2k 
▪ n/2k = 1일 때 분할 못함
▪ k = log2n

->  k == 몇 번 나눠지는지


## Merge Sort 도식화

![[Pasted image 20231011154606.png]] 


# [[시간 복잡도]] (Time Complexity)

### - 분할 과정

   - 배열의 중간 인덱스 계산
   - 2회의 순환 호출
   - O(1)

### - 합병 과정

   - 2개의 정렬된 배열 A와 B의 크기가 각각 m, n이라고 하면, 최대 비교 횟수 = (m+n-1) 
   - 합병의 시간 복잡도 = O(m+n)
   
![[Pasted image 20231011155421.png]]

### - 층별 비교 횟수

  - 각 층에서 모든 숫자(n=8)가 합병에 참여
  - 합병은 입력 크기에 비례하므로 각 층에서의 비교 횟수는 O(n)
  
![[Pasted image 20231011155554.png]]  

  -  층의 최대 개수
    => k=log2n

#### 합병 정렬의 시간 복잡도

=> (층수) X O(n)= log2n X O(n) = O(nlogn)


## 메모리 공간 문제

### 합병 정렬의 [[공간 복잡도]]: O(n) 

- 입력 위한 메모리 공간 + 입력과 같은 크기의 공간(임시 배열) 필요 
- 2개의 정렬된 부분을 하나로 합병하기 위해, 합병된 결과를 저장할 공간이 필요


## 코드 구현

```python
from math import floor

def Merge(bucket,p,middle,q):
    i=p                              #첫번째 버킷의 인덱스
    j=middle+1                       #또다른 버킷의 인덱스
    k=p                              #정렬될 배열의 인덱스

    while(i<=middle and j<=q):       #첫번째 버킷이나 두번째 버킷이 끝날때 까지
        if bucket[i]<=bucket[j]:
            sorted_bucket[k]=bucket[i]
            i+=1
        else :
            sorted_bucket[k]=bucket[j]
            j+=1
        k+=1
        
    if(i>middle):
        for idx in range(j,q+1):
            sorted_bucket[k]=bucket[idx]
            k+=1
    else:
        for idx in range(i,middle+1):
            sorted_bucket[k]=bucket[idx]
            k+=1
    for idx in range(p,q+1):          

        bucket[idx]=sorted_bucket[idx]  


def MergeSort(bucket,p,q):  # 크기 1개까지 나누기
    if p<q:
        middle= floor((p+q)/2)
        MergeSort(bucket,p,middle)
        MergeSort(bucket,middle+1,q)
        Merge(bucket,p,middle,q)

array=[37,10,22,30,35,13,25,24]
number=8
sorted_bucket=[0]*8

MergeSort(array,0,number-1)

print(*array)
```