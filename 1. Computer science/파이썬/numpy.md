---
tags:
  - ComputerScience
  - python
---
# Numpy 
- 다차원 배열을 처리하는데 필요한 여러기능 제공
-  사용하려면 import 

``` python
import numpy as np
```

#### 1) 파이썬의 리스트를 사용하는 방법

- array() 함수의 인자로 리스트를 넣어 생성
``` python
import numpy as np

list1=[1,2,3,4]
a=np.array(list1)
print(a)
```


#### 2) numpy 에서 제공하는 함수를 사용하는 방법

- zeros() : 배열에 모두 0을 집어넣음
```python

import numpy as np

aa=np.zeros((2,2))
print(aa)
```