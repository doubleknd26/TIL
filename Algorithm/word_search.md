# 문자열 검색
hellohey 라는 문장에서 hey 을 검색하기

## Brute Force

```
hellohey|
hey     | 0
 hey    | 1
  hey   | 2
   hey  | 3
    hey | 4
     hey| 5
```
시간 복잡도: O(n*m)
<br>
<br>

## KMP
불일치가 발생하기 전까지 같았던 부분은 스킵하면서 검색하는 방법.  

- prefix: 접두사
- suffix: 접미사
- pi    : 접두사와 접미사가 일치하는 부분 문자열 중에서 가장 긴 것의 길이를 저장하는 배열. 단, 부분 문자열의 길이는 전체가 될 수 없음


