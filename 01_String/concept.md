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

### 문자열 결합
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

## 요약 및 비교

| 항목 | 설명 |
|------|------|
| String | 불변 객체, 값 변경 시 새로 생성됨 |
| StringBuilder | 반복문 내 문자열 결합에 효율적 |


### 내가 코테 풀면서 한 실수 모음.. (실수 주의!)
- `substring(start, end)`에서 end는 포함 안 됨!
- 문자열 결합은 StringBuilder가 가장 효율적이므로 고민하지 말기!
- equals()로 문자열 비교해야지 == 쓰면 안됨!!
