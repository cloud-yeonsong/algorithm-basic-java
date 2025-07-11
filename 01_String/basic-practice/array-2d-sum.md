# 2차원 배열의 모든 합
2차원 배열이 주어졌을 때, 모든 요소의 합을 구하세요.<br>
입력: [[1, 2], [3, 4]] → 출력: 10

# Java 풀이(1)
```java
public int sum2D(int[][] arr) {
    int total = 0;
    for (int[] row : arr) {
        for (int val : row) {
            total += val;
        }
    }
    return total;
}
```
<br>
> 👩🏻‍💻 실수 주의! <br>
```java
int[][] arr = {
    {1, 2},
    {3, 4}
};

for (int[] row : arr) {
    System.out.println(Arrays.toString(row));
}
```
``` java
출력:
[1, 2]
[3, 4]
```
# Java 풀이(2)
```java
public int sum2D(int[][] arr) {
    int total = 0;
    for (int i = 0; i < arr.length; i++) {
        for (int j = 0; j < arr[i].length; j++) {
            total += arr[i][j];
        }
    }
    return total;
}
```
> arr.length -> 행의 개수<br>
> arr[i].length -> i번째 행의 열 개수
<br>
