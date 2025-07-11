# 문자열 뒤집기
문자열 s가 주어졌을 때, **문자열을 뒤집어서** 출력하세요.<br>
입력: "hello" -> 출력: "olleh"

# Java 풀이
```java
public String reverse(String s) {
    StringBuilder sb = new StringBuilder(s);
    return sb.reverse().toString();
}
```
