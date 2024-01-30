# Redux?

- 컴포넌트들이 props 없이 state 공유가능


-----------------------------
# 설치 방법

- npm install @reduxjs/toolkit react-redux


------------------------
# 사용법

1. state들을 담을 js파일 생성
-> store.js 파일 생성

2. 이후 
 store.js  에 이거 그냥 복붙
``` javascript
import {configureStore} from "@reduxjs/toolkit"

export default configureStore({
    reducer:{

    }
})
```

3. index.js 가서 provider store={store}


---------------------
# 왜씀?

컴포넌트간에 state 공유가 귀찮을때!

-----------------------

# store 사용법

``` javascript
//useState 역할

createSlice({
    name :'state이름~',
    initialState: '값'
})
```