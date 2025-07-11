# StringBuilder (Java)
- 문자열을 수정 가능한 객체로 만들어주는 클래스
- String과 달리 값을 변경할 때 새로운 객체를 생성하지 않아서 반복적인 문자열 조작에 효율적<br>

> String은 불변, 수정 시 새로운 객체가 만들어짐<br>
> StringBuilder는 가변, 내부 값을 직접 변경 가능

<br>

## 주요 메서드

| 메서드 | 설명 |
|--------|------|
| append() | 문자열, 숫자 등 다양한 값을 뒤에 추가함 |
| insert(int offset, String str) | 지정한 위치(offset)에 문자열을 삽입 |
| delete(int start, int end) | start부터 end-1까지 문자열을 삭제 |
| deleteCharAt(int index) | 지정한 인덱스의 문자 1개 삭제 |
| replace(int start, int end, String str) | start부터 end-1까지 문자열을 str로 교체 |
| reverse() | 문자열의 순서를 반전 |
| setCharAt(int index, char ch) | 지정한 인덱스의 문자를 교체 |
| substring(int start) | start부터 끝까지 문자열 추출 |
| substring(int start, int end) | start부터 end-1까지 문자열 추출 |
| toString()` | StringBuilder를 String으로 변환 |

<br>

## 사용 예시

```java
StringBuilder sb = new StringBuilder("hello");

sb.append(" world");              // → "hello world"
sb.insert(5, ",");                // → "hello, world"
sb.delete(5, 6);                  // → "hello world"
sb.setCharAt(0, 'H');             // → "Hello world"
sb.reverse();                     // → "dlrow olleH"
String result = sb.toString();   // String으로 변환
```

<br>

> 👩🏻‍💻 실수 주의!<br>
> sb.toString(); 잊지말자...
