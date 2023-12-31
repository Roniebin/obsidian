---
tags:
  - 트리
  - 알고리즘
  - ComputerScience
---
1. **정의**:
    
    최소 신장 트리는 주어진 가중 그래프(간선에 가중치가 할당된 그래프)에서 모든 노드를 연결하면서 모든 간선의 가중치 합이 최소인 트리를 의미합니다.
    
2. [[크루스칼 알고리즘]]과 [[프림 알고리즘]]:
    
    최소 신장 트리를 찾는 두 가지 주요 알고리즘은 크루스칼 알고리즘과 프림 알고리즘입니다. 크루스칼 알고리즘은 간선을 가중치 순으로 정렬하고 가장 낮은 가중치의 간선부터 선택하여 최소 신장 트리를 구성합니다. 프림 알고리즘은 하나의 노드에서 시작하여 점진적으로 트리를 확장하며, 항상 최소 가중치 간선을 선택합니다.
    
3. **응용 분야**:
    
    최소 신장 트리는 네트워크 디자인, 도로 건설 계획, 회로 설계, 클러스터링, 라우팅, 데이터 중심 구축, 스패닝 트리와 관련된 문제 해결 등 다양한 응용 분야에서 사용됩니다. 예를 들어, 도로 건설 계획에서 최소 신장 트리를 사용하면 최소한의 비용으로 모든 지역을 연결할 수 있습니다.
    
4. **최소 신장 트리의 특징**:
    
    - 그래프가 연결 그래프(모든 노드가 연결되어 있는)일 때만 최소 신장 트리가 존재합니다.
    - 최소 신장 트리는 간선 수가 노드 수에서 1을 뺀 것과 같습니다.
    - 최소 신장 트리는 사이클을 포함하면 안됩니다.

최소 신장 트리는 그래프 이론에서 중요한 주제 중 하나로, 다양한 알고리즘과 응용 분야에서 활용됩니다.