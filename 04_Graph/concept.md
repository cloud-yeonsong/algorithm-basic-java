# 그래프 (Graph) & DFS/BFS
> 개념은 알겠는데 문제만 풀려고 하면 잘 모르겠더라고요... 🤯 <br>
> 최대한 쉽게 풀어가면서 열심히 공부해보겠습니다!!<br>

<br>

## 1. 그래프 (Graph)
> 정점(노드)들이 서로 연결된 구조<br>
> 정점들 사이에 관계(간선)가 있는 모든 구조를 그래프라고 함
- 정점(Vertex): 점(ex. 도시, 사람, 노드)
- 간선(Edge): 정점끼리 연결하는 선(ex. 길, 친구관계)

EX.
```java
정점: A, B, C, D  
간선: A-B, A-C, B-D  
```

### 1-1. 그래프 표현 방식
> 인접 리스트 (보통 이걸 사용함)
```java
List<List<Integer>> graph = new ArrayList<>();
```
> 예시 그래프
```java
0: [1, 2]
1: [0, 3]
2: [0]
3: [1]
```
## 2. DFS (Depth-First-Search, 깊이 우선 탐색)
> 한 방향으로 끝까지 파고들기<br>
> 재귀로 자주 구현<br>

<br>

핵심코드
```java
void dfs(int node, boolean[] visited, List<List<Integer>> graph) {
    visited[node] = true;
    System.out.print(node + " ");

    for (int next : graph.get(node)) {
        if (!visited[next]) {
            dfs(next, visited, graph);
        }
    }
}
```

## 3. BFS (Breadth-Firt-Search, 너비 우선 탐색)
> 가까운 곳부터 넓게 퍼져나감<br>
> Queue 사용 (선입선출)<br>

<br>

핵심 코드
```java
void bfs(int start, boolean[] visited, List<List<Integer>> graph) {
    Queue<Integer> q = new LinkedList<>();
    q.offer(start);
    visited[start] = true;

    while (!q.isEmpty()) {
        int node = q.poll();
        System.out.print(node + " ");

        for (int next : graph.get(node)) {
            if (!visited[next]) {
                visited[next] = true;
                q.offer(next);
            }
        }
    }
}
```

## 요약 및 비교

### 내가 코테 풀면서 한 실수 모음.. (실수 주의!)
