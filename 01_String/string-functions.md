# Java 문자열 처리 함수 & 정규표현식 정리

## split() + 정규표현식

| 구분자 | 의미 | 예시 입력 | 결과 |
|--------|------|------------|-------|
| `" "` | 공백 1개 기준 | `"a b c"` | `["a", "b", "c"]` |
| `"\\s+"` | 공백 1개 이상 (여러 개 허용) | `"a   b c"` | `["a", "b", "c"]` |
| `"\\."` | 점(.) 기준 | `"1.2.3"` | `["1", "2", "3"]` |
| `","` | 쉼표 기준 | `"a,b,c"` | `["a", "b", "c"]` |
| `""` | 문자 하나씩 | `"abc"` | `["a", "b", "c"]` |

> `\\s+`는 공백, 탭, 줄바꿈 등 모든 공백 문자 1개 이상을 의미하며 가장 많이 사용됨.

---

## trim()

```java
String s = "   hello world   ";
s.trim(); // "hello world"
```

- 문자열 **앞뒤 공백 제거**
- 중간 공백은 그대로 유지됨
- 공백만 있는 문자열 처리에도 유용함

---

## replace() vs replaceAll()

| 함수 | 설명 | 예시 |
|------|------|------|
| `replace("a", "b")` | 문자열 그대로 치환 | `"abc".replace("a", "x")` → `"xbc"` |
| `replaceAll("a", "b")` | 정규표현식 기반 치환 | `"a1a2".replaceAll("a", "*")` → `"*1*2"` |

---

## startsWith() / endsWith()

```java
String s = "hello";
s.startsWith("he"); // true
s.endsWith("lo");   // true
```

---

## substring()

```java
String s = "abcdef";
s.substring(2);      // "cdef"
s.substring(2, 4);   // "cd" (2 이상, 4 미만)
```

---

## charAt(i)

```java
String s = "abc";
s.charAt(0); // 'a'
```

---

## toCharArray()

```java
String s = "hello";
char[] arr = s.toCharArray(); // ['h', 'e', 'l', 'l', 'o']
```

---

## equals() vs ==

- 문자열은 `equals()`로 비교해야 정확함

```java
String a = "abc";
String b = "abc";
a.equals(b); // true
a == b;      // 주소 비교이므로 위험
```

> char은 == '' 이렇게 하면 됨
```java
char c = 'a';

if (c == 'a') {
    System.out.println("a입니다!");
}
```
> 👩🏻‍💻실수 주의!<br>
> "a"이렇게 하면 String 이니까 안되고 'a'로 해야함!! 
---

## 정규표현식 특수문자

| 표현식 | 의미 |
|--------|------|
| `\\s` | 공백 문자 (스페이스, 탭, 줄바꿈 등) |
| `\\S` | 공백이 아닌 문자 |
| `\\d` | 숫자 |
| `\\D` | 숫자가 아닌 문자 |
| `\\w` | 알파벳/숫자/밑줄(_) |
| `\\W` | 위 외의 문자 |
| `.`   | 아무 문자 1개 |
| `*`   | 0개 이상 |
| `+`   | 1개 이상 |
| `?`   | 0 또는 1개 |
| `\\.` | 문자 그대로의 점(.) |

---

## 실전에서 자주 쓰는 조합

```java
// 공백 여러 개 무시하고 나누기
String[] tokens = input.split("\\s+");

// 입력값 줄에서 숫자 2개 추출
String[] s = br.readLine().split(" ");
int a = Integer.parseInt(s[0]);
int b = Integer.parseInt(s[1]);

// 숫자만 남기기
String digits = input.replaceAll("[^0-9]", "");
```

---

## 문자열 함수 요약표

| 함수 | 설명 |
|------|------|
| `split()` | 문자열 나누기 |
| `trim()` | 앞뒤 공백 제거 |
| `replace()` | 일반 문자열 치환 |
| `replaceAll()` | 정규식 기반 치환 |
| `charAt(i)` | i번째 문자 반환 |
| `substring(i, j)` | 문자열 일부 추출 |
| `toCharArray()` | 문자 배열로 변환 |
| `equals()` | 문자열 비교 |
| `startsWith()` / `endsWith()` | 접두사/접미사 확인 |

---
