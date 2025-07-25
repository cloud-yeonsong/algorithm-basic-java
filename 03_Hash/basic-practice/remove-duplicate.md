# 중복 숫자 제거하기
숫자 배열이 주어졌을 때, 중복을 제거한 숫자들을 출력하세요. (순서는 상관없음) <br><br> 
입력:
```java
int[] nums = {1, 2, 2, 3, 1, 4};
```

출력:
```java
[1, 2, 3, 4]
```
<br>

# Java 풀이(1)
```java
public void printUnique(int[] nums) {
    HashSet<Integer> set = new HashSet<>();
    for (int n : nums) {
        set.add(n);
    }
    System.out.println(set);
}
```


# Java 풀이(2)
```java
import java.io.*;
import java.util.*;

public class Main {
    public static void main(String[] args) throws IOException {
        // 입력 받기
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());

        // 정수 배열 만들기
        int[] nums = new int[st.countTokens()];
        for (int i = 0; i < nums.length; i++) {
            nums[i] = Integer.parseInt(st.nextToken());
        }

        // 중복 제거를 위한 HashSet 사용
        HashSet<Integer> set = new HashSet<>();
        for (int n : nums) {
            set.add(n);
        }

        // 출력
        List<Integer> result = new ArrayList<>(set);
        Collections.sort(result); // (보기 좋게 하려고 정렬 했음, 필수사항은 아님!)

        for (int n : result) {
            System.out.print(n + " ");
        }
    }
}
```



