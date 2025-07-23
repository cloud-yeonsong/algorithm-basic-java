# Array & ArrayList 심화 개념 정리

## 1. ArrayList remove() 오버로딩 주의

### 메서드 차이

| 메서드 시그니처         | 의미                      |
|-------------------------|---------------------------|
| `remove(int index)`     | index 위치의 요소 삭제    |
| `remove(Object o)`      | 특정 객체를 찾아 삭제     |

> 예제
```java
ArrayList<Integer> list = new ArrayList<>(List.of(1, 2, 3, 2));

list.remove(2);                         // index 2 → 값 3 제거됨
list.remove(Integer.valueOf(2));        // 값 2 → 첫 번째 2 제거됨
```

> remove(2)는 index 2를 삭제한다는 뜻 !! <br>
> 값을 지우려면 Integer.valueOf()로 감싸야 함

<br>

## 2. 배열 정렬 및 복사

### 오름차순 정렬
```java
int[] arr = {5, 3, 1};
Arrays.sort(arr);   // [1, 3, 5]
```

### 내림차순 정렬
```java
Integer[] arr = {5, 3, 1};
Arrays.sort(arr, Collections.reverseOrder());  // [5, 3, 1]
```

<br>

> 👩🏻‍💻실수 주의!<br>
> (1) 기본형 int[]는 reverseOrder() 사용 불가 → Integer[]로 박싱 필요<br>
> (2) Array가 아니라 Arrays로 해야함... s를 안써서 오류났음!! 어이없지만 내가 한 실수... 흑 ㅜ<br>

<br>

### 배열 복사
```java
int[] origin = {1, 2, 3};

// 방법 1: Arrays.copyOf
// 배열 전체를 복사해서 새 배열을 리턴
int[] copy1 = Arrays.copyOf(origin, origin.length);

// 방법1 예시
int[] arr = {1, 2, 3};
int[] copy = Arrays.copyOf(arr, 5);  // → [1, 2, 3, 0, 0]


// 방법 2: System.arraycopy
// 기존 배열에서 원하는 범위를 선택해 복사
int[] copy2 = new int[origin.length];
System.arraycopy(origin, 0, copy2, 0, origin.length); // 원본 배열, 복사 시작 인덱스, 대상 배열, 내용을 넣을 시작 인덱스, 복사할 요소의 개수

// 방법2 예시
int[] origin = {1, 2, 3};
int[] dest = new int[5];

System.arraycopy(origin, 0, dest, 1, 3); // dest = [0, 1, 2, 3, 0]

```
> Arrays.copyOf()는 코드 간결(간단하게 전체 복사)<br>
> System.arraycopy()는 성능이 빠름(정교하게 부분 복사)!

<br>

## 3. 배열/리스트 변환

### 배열 -> 리스트
```java
String[] arr = {"a", "b"};

// 1. 고정 크기 리스트 (그냥 배열을 리스트처럼 사용할 수 있게 래핑 해주는 메서드)
List<String> list = Arrays.asList(arr);

// 2. 크기 변경 가능한 리스트 (복사해서 새 리스트 만들기!)
List<String> list = new ArrayList<>(Arrays.asList(arr));
```

### 리스트 -> 배열
```java
List<String> list = List.of("a", "b");
String[] arr = list.toArray(new String[0]); // new String[0]은 타입만 알려주고, 실제 크기는 자동 조절됨
```

<br>






