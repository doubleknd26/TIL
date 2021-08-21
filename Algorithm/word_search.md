# 문자열 검색
hellohey 라는 문장에서 hey 을 검색하기

## Brute force
시간 복잡도: O(n*m) , n = hellohey.len , m = hey.len

```
hello hey|
hey      | 0
 hey     | 1
  hey    | 2
   hey   | 3
    hey  | 4
     hey | 5
      hey| 6
```

## KMP
불일치가 발생하기 전까지 같았던 부분은 스킵하면서 검색하는 방법.
prefix, suffix, pi
