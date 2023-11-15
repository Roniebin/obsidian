---
tags:
  - 알고리즘
  - Sort
  - ComputerScience
---
# 분할 정복 알고리즘 (Divde and Conquer)

### 특징

- 문제를 2개의 부분 문제로 분할
- 각 부분 문제의 크기가 일정하지 않은 형태의 divide and conquer 알고리즘

### 아이디어

  - 피봇(pivot)을 기준으로 pivot 보다 작은 숫자 -> 왼편, 큰 숫자 -> 오른편으 로 분할 (pivot은 그 사이에 놓음)
  - 분할된 subproblem에 대해서도 동일한 과정 진행
  
   ![[Pasted image 20231011164133.png]]


## 알고리즘 요약

1. Pivot 선정 
2. Pivot과 가장 왼쪽에 있는 숫자의 위치 교환 
3. Pivot 보다 큰 수와 작은 수를 각각 교환 
4. Pivot 보다 작으면서 가장 오른쪽에 있는 숫자와 pivot의 위치 교환 
5. Pivot 기준으로 왼쪽 부분과 오른쪽 부분으로 분할 
6. 분할된 각 부분에 대해 1-5번을 동일하게 수행


## [[시간 복잡도]] (Time Complexity)

- Quick sort의 성능은 pivot 선택에 의해 결정 
- Pivot 으로 가장 작은 숫자 or 가장 큰 숫자가 선택되면 분할이 한 부분으로 치우침
- Pivot 으로 항상 가장 작은 숫자가 선택되는 경우 == **<mark style="background: #FF5582A6;">최악의 경우</mark>**
    => 가장 작은 숫자가 선택되는 경우 , 모든 인덱스를 순회하기 때문에, 피봇(자기자신) 이후의            인덱스를 모두 계산 -> (n-1) + (n-2) + (n-3) + .... + 2 + 1 = n(n-1)/2 = O(n^2)

 - 최선의 경우 == 각 층에서 항상 절반씩 줄어듦
     비교 횟수 = O(n)

- 총 비교 횟수 
     O(n) X (층수) = O(n) X log n == <mark style="background: #FF5582A6;">최선의 경우</mark>의 시간 복잡도 O(nlogn)


## 특징

- 큰 입력에 대해 가장 좋은 성능을 보이는 알고리즘
-  모든 정렬 알고리즘 보다 좋은 성능을 가짐


# 코드 구현

```python
def QuickSort(bucket,start,end):
    if start >=end:
        return

    key=start #키는 첫번째 원소(피봇)
    i=start+1 #키 값의 바로 오른쪽 인덱스 /왼쪽 출발지점
    j=end
    temp=0

    while(i<=j): #엇갈릴때 까지 반복

        while(i <= j and bucket[i]<=bucket[key]):
            i+=1

        while(i <= j and bucket[j]>=bucket[key] and j>start):
            j-=1

        if i>j: # 현재 엇갈린 상태면 키값과 교체
            temp=bucket[j]
            bucket[j]=bucket[key]
            bucket[key]=temp
        else:
            temp=bucket[j]
            bucket[j]=bucket[i]
            bucket[i]=temp
    QuickSort(bucket,start,j-1)
    QuickSort(bucket,j+1,end)


number=10
array =[1,10,5,8,7,6,4,3,2,9]

QuickSort(array,0,number-1)

print(*array)
```


