---
tags:
  - 아두이노
  - 임베디드시스템
  - ComputerScience
---
# INPUT_PULLUP 이 무엇인가?

- 아두이노 보드의 디지털 핀을 입력으로 설정하고 `INPUT_PULLUP`으로 설정하면 해당 핀에 내부 풀업 저항을 활성화


## `INPUT_PULLUP`이 하는 일


1. **입력 모드**: 
   지정된 디지털 핀을 입력으로 구성합니다. 이 모드에서 핀은 외부 장치나 센서의 상태를 읽는 데 사용할 수 있습니다. 예를 들어 버튼이나 스위치 같은 것을 읽을 때 사용됩니다.
    
2. **풀업 저항**: 
    핀이 `INPUT_PULLUP`으로 설정되면 아무것도 연결되지 않았을 때 기본적으로 HIGH를 읽습니다. 입력이 접지에 연결될 때(예: 버튼을 누를 때) LOW를 읽습니다.


``` cpp
const int buttonPin = 2;  // 사용 중인 핀으로 대체
int buttonState;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == LOW) {
    // 버튼이 눌린 경우
    // 여기에 코드를 작성합니다.
  }
}

```

## 이걸 왜하냐?

- 풀업 저항은 버튼이 눌리지 않을 때 핀이 정의된 상태(HIGH)에 있도록하여 불안정한 동작을 방지합니다.
