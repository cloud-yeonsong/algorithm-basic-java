# 1. 배열 (Array)

### 선언
```java
int[] arr = new int[5];       // 크기 꼭 지정해야 함 !!
String[] str = new String[3]; // 참조형도 가능
```

### 배열 초기화
```java
int[] arr = {1, 2, 3};                      // 값 직접 넣기
String[] str = new String[]{"a", "b"};      // 문자열 배열
String[] str2 = {"a", "b"};                 // 생략형도 가능
```

### 원소 접근
```java
arr[0] = 10;
System.out.println(arr[0]);    // 0번째 요소 출력
```

### 배열 길이 확인
```java
arr.length;    // 배열의 길이 (괄호 X)
```

### 배열 전체 순회
```java
// 일반 for문
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}

// 향상된 for문 (for-each)
for (int n : arr) {
    System.out.println(n);
}
```
# 2. 2차원 배열 (2D Array)

### 선언 및 초기화
```java
int[][] grid = new int[2][3];          // 2행 3열 배열
int[][] grid2 = {{1, 2}, {3, 4}};      // 직접 초기화
```

### 접근 및 순회
```java
for (int i = 0; i < grid.length; i++) {
    for (int j = 0; j < grid[i].length; j++) {
        System.out.println(grid[i][j]);
    }
}

// 향상된 for문
for (int[] row : grid) {
    for (int val : row) {
        System.out.println(val);
    }
}
```

# 3. ArrayList

### 특징
- 크기 유동적 (자동 확장)
- 약간 느림 (배열보다)
- `int`, `char` 같은 기본형은 안됨
- `Integer`, `Character` 같은 참조형 사용
- 참조형 기본값: `null`, 기본형 기본값: `0`, `false`

### 선언 및 사용 예시
```java
ArrayList<String> list = new ArrayList<>();

list.add("hello");              // 값 추가
list.get(0);                    // 0번 인덱스 값
list.size();                    // 길이
list.remove(0);                 // 값 제거 (인덱스 기준)
list.clear();                   // 전체 삭제
list.contains("hello");         // 포함 여부 확인
list.set(0, "hi");              // 값 수정
```

## 요약 및 비교

| 항목 | 설명 |
|------|------|
| Array | 고정 크기, 기본형 사용 가능 |
| ArrayList | 동적 크기, 참조형만 가능 |

| 항목 | 설명 |
|------|------|
| arr.length | 배열의 길이 (변수) |
| list.size() | ArrayList의 길이 (메서드) |

### 내가 코테 풀면서 한 실수 모음.. (실수 주의!)
- `substring(start, end)`에서 end는 포함 안 됨!
- `ArrayList<int>` 안됨!! → `ArrayList<Integer>`로 써야 함
- int[] arr = new int[5];          // 크기 꼭 지정해야 함
