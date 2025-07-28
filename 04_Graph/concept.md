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

<br>

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

<br>

## 2. DFS (Depth-First-Search, 깊이 우선 탐색)
> 한 방향으로 끝까지 파고들기<br>
> **재귀**로 자주 구현<br>

<br>

핵심코드
```java
void dfs(int node, boolean[] visited, List<List<Integer>> graph) {
    visited[node] = true; // 이미 방문했으면 체크!(다시 안봐야하니까)
    System.out.print(node + " "); // 방문한 노드 출력

    for (int next : graph.get(node)) { // 현재 노드에 연결된 노드들을 하나씩 꺼내기
        if (!visited[next]) { // (1) 방문하지 않은 노드라면
            dfs(next, visited, graph); // (2) 그 노드로 다시 파고들기(재귀 호출)
        }
    }
}
```
> 1. **재귀** 사용, **현재 노드 기준**으로 탐색<br>
> 2. visited 배열은 중복 방문 방지용<br>
> 3. graph.get(node)는 인접 리스트에서 이웃 노드 가져오기<br>
<br>

## 3. BFS (Breadth-Firt-Search, 너비 우선 탐색)
> 가까운 곳부터 넓게 퍼져나감<br>
> Queue 사용 (선입선출)<br>

<br>

핵심 코드
```java
void bfs(int start, boolean[] visited, List<List<Integer>> graph) {
    Queue<Integer> q = new LinkedList<>();
    q.offer(start); // 시작 노드를 큐에 넣기
    visited[start] = true; // 시작 노드를 방문했다고 체크

    while (!q.isEmpty()) { // 큐가 빌 때까지 계속 탐색
        int node = q.poll(); // 큐에서 하나 꺼내기 (가장 오래된것) -> 방문!!
        System.out.print(node + " "); // 방문한 노드 출력

        for (int next : graph.get(node)) { // 현재 노드(큐에서 꺼낸 노드, 방문한 노드)의 이웃 노드들 다 확인
            if (!visited[next]) { // 아직 방문하지 않은 노드라면
                visited[next] = true; // 방문처리
                q.offer(next); // 큐에 넣어주기 (나중에 방문 할 수 있게)
            }
        }
    }
}
```
> 1. **큐** 사용, **가까운 노드**부터 탐색<br>
> 2. visited 배열은 중복 방문 방지용<br>
<br>

---

## 정리

### 쉬운 연습문제!!
문제: <br>
0번부터 3번까지 연결된 정점이 있는 그래프가 있습니다.<br>
DFS와 BFS 순서를 출력하세요.<br>

<br>

그래프 구조
```java
0 - 1  
|   |
2   3
```

<br>

입력: <br>
```java
정점 개수: 4  
간선:  
0 1  
0 2  
1 3  
```

<br>

DFS 출력 (시작: 0)
```java
0 1 3 2
```

<br>

BFS 출력 (시작: 0)
```java
0 1 2 3
```

<br>

Java 전체 코드 예제:
```java
import java.util.*;

public class Main {
    static List<List<Integer>> graph = new ArrayList<>();
    static boolean[] visited;

    public static void main(String[] args) {
        int n = 4;
        visited = new boolean[n];
        for (int i = 0; i < n; i++) graph.add(new ArrayList<>());

        // 그래프 간선 추가
        // 여기서 graph는 2차원 리스트이고, graph.get(0)은 0번 노드와 연결된 이웃 리스트를 의미한다.
        graph.get(0).add(1); // 0번 노드의 이웃 리스트를 꺼내고 0번 노드의 이웃에 1번 노드를 추가
        graph.get(0).add(2);
        graph.get(1).add(0);
        graph.get(1).add(3);
        graph.get(2).add(0);
        graph.get(3).add(1);

        System.out.print("DFS: ");
        dfs(0);
        System.out.println();

        visited = new boolean[n]; // 방문 배열 초기화
        System.out.print("BFS: ");
        bfs(0);
    }

    static void dfs(int node) {
        visited[node] = true;
        System.out.print(node + " ");
        for (int next : graph.get(node)) {
            if (!visited[next]) dfs(next);
        }
    }

    static void bfs(int start) {
        Queue<Integer> q = new LinkedList<>();
        q.offer(start);
        visited[start] = true;

        while (!q.isEmpty()) {
            int cur = q.poll();
            System.out.print(cur + " ");
            for (int next : graph.get(cur)) {
                if (!visited[next]) {
                    visited[next] = true;
                    q.offer(next);
                }
            }
        }
    }
}
```

<br>

### 요약 및 비교

| 항목           | DFS (깊이 우선 탐색)                   | BFS (너비 우선 탐색)                     |
|----------------|----------------------------------------|------------------------------------------|
| 구현 방식      | **재귀함수** (또는 스택)              | **Queue(큐)** 사용                       |
| 탐색 순서      | 한 방향으로 **끝까지 깊게** 파고듦     | 시작점에서 **가까운 노드부터** 탐색      |
| 사용 자료구조  | **스택** (재귀 호출 스택 포함)        | **큐 (Queue)**                           |
| 방문 순서 예시 | `0 → 1 → 3 → 2`                       | `0 → 1 → 2 → 3`                          |
| 방문 체크 방법 | 방문 시점에 `visited[node] = true`    | 큐에 넣을 때 `visited[node] = true`      |
| 구현 난이도    | 조금 더 쉬움 (재귀 구조 익숙하면)     | 구현 복잡도 약간 높음 (큐와 반복문 필요) |
| 사용 예시      | 미로 탐색, 백트래킹, 경로 존재 여부 등 | 최단 거리 탐색, 레벨 순서 탐색 등        |

### 정리 요약
- **DFS**: 깊게 파고드는 방식 → **재귀 함수** 사용
- **BFS**: 넓게 퍼지는 방식 → **큐(Queue)** 사용
- 'visited[]' 배열은 **중복 방문 방지용**

### 내가 코테 풀면서 한 실수 모음.. (실수 주의!)
- DFS는 재귀로 자주 구현되므로 스택 오버플로우에 주의...
- 최단거리는 BFS!!!

### 마지막으로...
> 열심히 해봤는데... 아직도 문제를 보면 눈앞이 캄캄해요.. ㅜㅜ<br>
> 더 노력하면 언젠가는 그래프의 달인이 될 수 있겠죠!.. 파이팅!!!<br>
> 다음은 문제들고 찾아오겠습니다..!
