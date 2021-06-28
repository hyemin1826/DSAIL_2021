[node2vec README.md]
Node2vec (Biased Walks)
=======================
* 편향된 2nd-order Random walk 사용 ⇒ Local(Homo)/Global(Structure) 선택 집중 가능
  + 참고
    - 1st-order random walk: node to node transition
    - 2nd-order random walk: edge to edge transition
* 이웃을 찾는 2가지 방법
  + BFS
    - Homo. 같은 그룹 내 node.
  + DFS
    - Structure. 구조적으로 같은 역할하는 node.
* 2가지 방법을 조정하는 방법
  + p(Return parameter)
    - p↓ ⇒ return 가능성↑ ⇒ BFS↑
    - p↑ ⇒ return 가능성↓ 
  + q(In-out parameter)
    - q↓ ⇒ 다른 node 이동 가능성↑ ⇒ DFS↑
    - q↑ ⇒ 다른 node 이동 가능성↓
* 계산 과정
  i. 랜덤 워크 확률 구함 (current state가 바뀔 때마다)
  ii. 각 노드에서 시작하는 길이 l의 랜덤 워크 r번 실행
  iii. SGD ⇒ node2vec 최적화
  + 참고
    - 시간복잡도: ~O(1/k(l-k)) per sample
    - 위의 세 단계는 병렬적으로 처리 가능 (?)
