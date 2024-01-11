---
tags: ComputerScience, react
---
# Context?

- 컴포넌트의 props를 통한 데이터 전달
- 데이터를 기존에 props 이용하여 전달하는 대신 , 컴포넌트 트리를이용해 전달하는 새로운 방식

# 언제 context를 사용할까
- 여러 개의 component 들이 접근해야하는 데이터
- 로그인 여부, 로그인정보,현재언어, ui 테마

# Context를 사용하기전에 고려할때

- 컴포넌트와 Context가 연동되면 재사용성이떨어짐
- 그렇기에 레벨이 많이 깊지 않은경우, 기존방식대로 props로 주는게 더 적합
