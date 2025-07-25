# 단어 개수 세기
문자열 배열이 주어졌을 때, 각 단어가 몇 번 나오는지 세어보시오.<br><br> 
입력:
```java
String[] words = {"apple", "banana", "apple", "cherry", "banana"};
```

출력:
```java
apple: 2
banana: 2
cherry: 1
```

# Java 풀이
```java
public void countWords(String[] words) {
    HashMap<String, Integer> map = new HashMap<>();
    for (String word : words) {
        map.put(word, map.getOrDefault(word, 0) + 1);
    }

    for (String key : map.keySet()) {
        System.out.println(key + ": " + map.get(key));
    }
}
```

> 👩🏻‍💻 실수 주의! <br>
- HashMap은 put(key, value) <br>
- HashSet은 add(value) // 값만 저장 <br>

> map.getOrDefault(word, 0) <br>
- map에 "word"라는 key가 있으면 해당 value 가져오기, 없으면 0 반환 <br>





