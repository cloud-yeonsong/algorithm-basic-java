# 배열 요소 합 구하기
정수 배열 arr가 주어졌을 때, **모든 요소의 합**을 반환하세요.<br>
입력: [1, 2, 3, 4] → 출력: 10

# Java 풀이
```java
public int sum(int[] arr) {
    int total = 0;
    for (int num : arr) {
        total += num;
    }
    return total;
}
```
