---
tags:
  - ComputerScience
  - 다이나믹프로그래밍
---
# 배낭문제

- n개의 물건과 각 물건 i의 무게 wi와 가치 vi가 주어지고, 배낭의 용량이 C일 때, 배낭에 담을 수 있는 물건의 가치는?


### 실습코드

``` python
import numpy as np

n=20
d=[1,5,10,16]
INF=1000000
C=[INF]*(n+1)
C[0]=0


for j in range(1,n+1):
    for i in range(1,len(d)+1):
        if d[i-1]<=j and C[j-d[i-1]]+1<C[j]:

            C[j]=C[j-d[i-1]]+1

print(np.array(C))
```