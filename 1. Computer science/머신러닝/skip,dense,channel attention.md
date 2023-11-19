---
tags:
  - ComputerScience
  - 머신러닝
---
# skip, dense을 적절하게 섞어서 최고의 머신러닝 모델을 만들어야해

#### what gpt said

머신러닝 모델을 만드는 데 있어 "skip"과 "dense"을 조합하는 것은 흥미로운 접근 방식이에요. 
Skip connections은 <mark style="background: #FF5582A6;">신경망의 깊이를 극복하고 그래디언트 소실 문제를 줄이는 데 도움을 줄 수 있어요</mark>.
한편으로는 dense layers는 <mark style="background: #FF5582A6;">복잡한 패턴을 학습하는 데 유용하며 모델의 복잡성을 높일 수 있어요</mark>. 
예를 들어, ResNet 같은 구조에서 skip connections을 사용하여 깊은 네트워크를 구축하고 dense layers를 추가하여 각 레이어의 표현력을 높일 수 있어요.


## Skip Connection

- 기존의 네트워크 아키텍처에서는 입력이 첫 번째 레이어를 거쳐 여러 레이어를 통과한 후 출력 레이어에서 결과를 생성합니다. 하지만 <mark style="background: #FF5582A6;">이 과정에서 심층 네트워크에서 그래디언트가 소실되거나 폭발하는 문제</mark>가 발생할 수 있습니다. 이를 해결하기 위해 스킵 연결은 몇 개의 레이어를 건너뛰어 이전 레이어의 출력을 현재 레이어의 출력에 직접 추가함으로써 정보가 직접적으로 흐를 수 있도록 돕습니다.
- 더 깊은 네트워크를 효과적으로 학습할 수 있게 합니다.