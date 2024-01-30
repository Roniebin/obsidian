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


# Redux store 안에 모든걸넣지 마라

컴포넌트간 공유가필요없으면 useState 써라


# redux state 변경하려면

1. state 변경함수 만들기
2. export
3. dispatch(status 변경함수())


# 장점

- 사이즈가 커지면 한 state를 변경했을때 어디서 오류가낫는지 모름
- redux식으로하면 store에 변경함수만 뒤지면 되서 오류찾기 쉬움
