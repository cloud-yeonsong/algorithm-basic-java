# 해시 (Hash)

> 데이터를 빠르게 검색, 삽입, 삭제할 수 있도록 도와주는 자료구조

<br>

## 1. HashMap

### 선언
```java
HashMap<String, Integer> map = new HashMap<>();
```

### 주요 메서드
```java
map.put("a", 1);               // 키-값 추가
map.get("a");                  // 키 "a"의 값 반환
map.containsKey("a");          // 키 존재 여부
map.containsValue(1);          // 값 존재 여부
map.remove("a");               // 키 "a" 삭제 (key와 value 모두 삭제됨)
map.remove("banana", 4);       // value가 4일 때만 삭제하고 true 반환, 5이면 삭제되지 않음(false 반환)
map.size();                    // 원소 개수
map.clear();                   // 전체 삭제
```

<br>

>예시
```java
Map<String, Integer> map = new HashMap<>();
map.put("banana", 4);

System.out.println(map.remove("banana", 4)); // true
System.out.println(map);                     // {}
```

<br>

### 요소 추가
```java
map.put("apple", 3);
```
> "apple"이라는 key 값에 값 3을 저장함<br>
> 같은 key가 이미 있으면 값을 덮어씀

<br>

### 값 가져오기
```java
int count = map.get("apple"); // → 3
```
> "apple"이라는 key에 해당하는 값을 반환함<br>
> key가 없으면 null 반환됨

<br>

### 순회
```java
for (String key : map.keySet()) {
    System.out.println(key + " : " + map.get(key));
}

for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " : " + entry.getValue());
}
```

<br>
 
### getOrDefault 
```java
int count = map.getOrDefault("banana", 0);
```
> "banana"라는 key가 없을 경우 기본값 0을 반환
> "banana"라는 key가 있을 경우 그 키의 값을 반환

<br>

## keySet()
```java
for (String key : map.keySet()) {
    System.out.println(key + " : " + map.get(key));
}
```
> 맵의 모든 key만 모은 Set을 반환<br>
> 반복문에서 key로 하나씩 꺼내서 get(key)로 value에 접근

<br>

## entrySet()
```java
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " : " + entry.getValue());
}
```
> (key, value) 한 쌍을 담은 Entry 객체 집합<br>
> getKey(), getValue() 메서드로 각각 접근 가능<br>
> 가장 일반적이고 효율적인 순회 방식

<br>


## 2. HashSet

### 선언
```java
HashSet<String> set = new HashSet<>();
```

### 주요 메서드
```java
set.add("apple");             // 요소 추가
set.contains("apple");        // 포함 여부 확인
set.remove("apple");          // 요소 제거
set.size();                   // 크기 반환
set.clear();                  // 전체 비우기
```

### 순회
```java
for (String s : set) {
    System.out.println(s);
}
```

### HashMap vs HashSet 비교

| 항목           | HashMap                                   | HashSet                     |
|----------------|--------------------------------------------|-----------------------------|
| 저장 구조       | `(Key, Value)` 쌍으로 저장                  | 단일 값(value)만 저장         |
| 값 접근         | `map.get(key)` 으로 key를 통해 값 조회     | `set.contains(value)`로 존재 여부 확인 |
| 중복 허용 여부   | Key는 중복 안됨, Value는 중복         | 모든 값 중복 안됨               |
| 정렬 여부        | 정렬 안됨 (순서 보장 안됨)                   |정렬 안됨 (순서 보장 안됨)                   |
| 주요 사용 목적   | 카운팅, 매핑, 빠른 조회                    | 중복 제거, 존재 여부 확인       |
| 시간 복잡도     | 평균 O(1)                                        | 평균 O(1)                                        |

---

<br>

> 👩🏻‍💻 실수주의!<br>
> - HashMap이나 HashSet은 순서를 보장하지 않음<br>
> - map.get("없는키")는 null 반환 → NullPointerException 조심<br>
> - map.get(key)은 해당 key에 대한 value를 반환!! 키 말고 값!!!
```java
Map<String, Integer> map = new HashMap<>();
map.put("apple", 3);

System.out.println(map.get("apple"));   // 출력: 3
System.out.println(map.get("banana"));  // 출력: null
```

<br>

> 👩🏻‍💻 <br>
> - keySet()은 key만 순회, entrySet()은 (key, value) 둘 다 사용 가능<br>
> - HashSet은 내부적으로 HashMap<K, Object> 기반으로 동작함<br>
> - map.put(1, 100); // 실제로는 map.put(Integer.valueOf(1), Integer.valueOf(100));<br>


