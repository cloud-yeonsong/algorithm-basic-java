# 문자열 (String)

### 선언
```java
String s = "hello";
```

### 접근
```java
s.charAt(i); // i번째 문자 (0부터)
```

### 부분 문자열
```java
s.substring(start, end); // end는 포함 안함
```

### 🔗 문자열 결합
```java
// 1. StringBuilder
StringBuilder sb = new StringBuilder();
sb.append("a").append(" ").append("b");

// 2. + 연산자
String result = a + " " + b;

// 3. concat
String result = a.concat(" ").concat(b);

// 4. join
String result = String.join(" ", "Hello", "World");

// 5. format
String result = String.format("%s %s", a, b);
```

> 모두 결과는 `"Hello World"`

### 길이 확인
```java
s.length();
```

# 배열 (Array)

### 선언
```java
int[] arr = new int[5];          // 크기 꼭 지정해야 함
String[] str = new String[5];
```

### 문자열 배열 초기화
```java
String[] str = new String[]{"a", "b"};
String[] str = {"a", "b"}; // 값 넣을 때는 이렇게도 가능
```

# ArrayList

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
| String | 불변 객체, 값 변경 시 새로 생성됨 |
| StringBuilder | 반복문 내 문자열 결합에 효율적 |

| 항목 | 설명 |
|------|------|
| Array | 고정 크기, 기본형 사용 가능 |
| ArrayList | 동적 크기, 참조형만 가능 |

> **이 문서는 Java로 코딩 테스트를 준비하며 정리한 개념 정리입니다.**  
