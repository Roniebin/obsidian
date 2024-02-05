---
tags:
  - 코딩애플
  - html
---
# pseudo-element란?

:: 이거로 하는거

- 내부의 일부분만 스타일줄때
	ex) 글의 첫글자만 스타일줄떄

	.pseudo :: first-letter //첫 글자만
	.pseudo :: first-line  //첫째줄만 
	:: after // 글의 맨마지막에 뭐넣을때 content 속성이같이
	:: before  // 내부 글자의 맨앞에 뭔가 추가할때
-
-------------------
# input 타입 file 커스텀시

style 넣어서 width: 300px 이런게아니라
이걸 스타일 할거면 class=input-file이런거만들고
수도 엘리먼트붙인다

.input-file :: file-selector-button {
	background:skyblue 
}

input file인데왜 버튼이랑 span이 있지?
이런 숨겨진거 커스텀할때 사용
