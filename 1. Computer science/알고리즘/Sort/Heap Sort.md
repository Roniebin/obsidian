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
------------------------------
### 알고리즘 생각방향

5. 실행되는 코드 (메인 수행코드)

(1) 최대힙 트리를 생성

(2) 최대힙의 트리를 유지하기 때문에 루트노드는 최대값을 가져야한다.

(3) 마지막값과 루트노드를 자리를 바꾼다. -> 최대힙을 위반하게됨 -> 값을 바꾸 면 마지막값은 최대값을 가지게되는데 이것은 힙트리에서 제거하고 result 에 추가 해줌

(4) 힙 트리에서 제거후 A.pop()을 통해 heapSize 는 1 빼줌

이후 최대힙 위반을 수정하기위해 DownHeap() 함수를 써서 ,언제든 최대힙을 유지하도록한다.

(5) 결과값 출력

--------------------
# 실습코드

``` python
from math import floor

f=open('input.txt','r')
f1=open('output.txt','w')

A=[-1] # 0 번째 인덱스는 없는거
  
while True:
    line = f.readline()
    if not line: # 파일 읽기가 종료된 경우
        break
    A.append(int(line))
    
n=len(A)-1 # 노드의 개수 (마지막인덱스)

def BuildHeap():
    for i in range (floor(n/2),0,-1): # i번을 루트노드로 최대힙을 이루도록 해주는 함수
        DownHeap(i)

def DownHeap(i):
    leftChild=2*i
    rightChild=(2*i)+1

    if leftChild <=heapSize and A[leftChild] > A[i]: # 노드 개수를 벗어나지않고, 왼쪽자식이 부모노드보다 크면
        bigger=leftChild    # 큰 값의 인덱스를 bigger에 저장 (초기화 과정)
    else :
        bigger=i

    if rightChild <=heapSize and A[rightChild] > A[bigger]:
        bigger=rightChild   # 오른쪽자식이 더크면 bigger에 저장

    if bigger!=i : # 부모, 왼쪽, 오른쪽 노드 비교 후 제일 큰 값이 부모가아니면 (최대힙 성립 x)
        temp = A[i]
        A[i]=A[bigger]
        A[bigger]=temp
        DownHeap(bigger) # 바뀌고 나서 그자리에서 부터 또 밑으로 최대힙 되도록 함수 호출

result=[]
heapSize=n

# 힙생성
BuildHeap()

for i in range(1,n+1):
    temp=A[1]               # 루트와 힙의 마지막 노드교환
    A[1]=A[heapSize]
    A[heapSize]=temp
    result.insert(0,A[heapSize])  # 최대힙이기때문에 루트노드를 result에 저장
    A.pop() # 바꾼 최대값을 제거
    heapSize=heapSize-1     # 힙의 크기 감소
    DownHeap(1)              # 위배된 힙 조건을 만족시킴

for i in range(len(result)):
    f1.write(str(result[i])+"\n")
```