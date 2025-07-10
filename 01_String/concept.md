# 문자열 (String)
선언: String s = "hello";
접근: s.charAt(i)
부분 문자열: s.substring(start, end) <b>end는 포함 안함</b>
결합: 
1. StringBuilder sb = new StringBuilder();
   sb.append("a").append(" ").append("b");
2. a + " " + b
3. a.concat("").concat(b)
4. .join(" ", "Hello", "World")
5. format("%s %s", a, b)
// 모두 결과는 Hello World

길이: s.length()

# 배열
선언: 
int[] arr = new int[5] <b>크기 꼭 지정해 줘야함</b>
String[] str = new String[5]

문자열:
String[] str = new String[]{"a", "b"};
String[] str = {"a", "b"}; <b>값을 넣을때는 바로 이렇게도 선언 가능</b>

ArrayList:
- 크기 유동적, 약간 느림
- 참조형(Integer, Charater, String) 사용 -> 참조형 기본값은 null
- 기본형(int, char, boolean)은 사용 안함 -> 기본형은 0, false
ArrayList<String> list = new ArrayList<>();
list.add("hello");
list.get(0); <b>이것도 인덱스?</b>
list.size();
list.remove(0); <b>인덱스</b>
list.clear(); <b>전체 삭제</b>
list.contains("hello"); <b>값 포함 여부</b>
list.set(0, "hi"); <b>값 수정</b>
