# 문자열 개수 세기
문자열 배열이 주어졌을 때, "apple"이 몇 번 나오는지 반환하세요.
입력: ["banana", "apple", "apple"] → 출력: 2

# Java 풀이1
```java
public int countApple(String[] arr) {
    int count = 0;
    for (String s : arr) {
        if (s.equals("apple")) count++;
    }
    return count;
}
```

> 👩🏻‍💻 실수 주의!
String은 equals로 비교하자..

---

# Java 풀이2
```java
import java.io.*;
import java.util.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());

        StringTokenizer st = new StringTokenizer(br.readLine());
        int count = 0;

        for (int i = 0; i < N; i++) {
            if (st.nextToken().equals("apple")) {
                count++;
            }
        }

        System.out.println(count);
    }
}
```
