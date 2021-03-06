# 문자열 검색
hellohey 라는 문장에서 hey 을 검색한다고 했을 때, 어떤 방법이 있을까

<br>

## Brute Force
무식하게 풀기. 가능한 모든 비교를 다 해보는 방법.
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

## KMP
불일치가 발생하기 전까지 같았던 부분은 스킵하면서 검색하는 방법.  

**Term**  

- prefix: 접두사, 문자열의 왼쪽부터 시작해서 차례로 한개씩 더 읽어가면서 만듦.
- suffix: 접미사, 문자열의 오른쪽부터 시작해서 차례로 한개씩 더 읽어가면서 만듦.
- Failure Function (pi): 문자열 일치 여부를 검사하다가, 불일치(실패)가 발생했을 때, 불일치 발생 이전까지 일치했던 내용을 건너뛴 다음 검사 위치를 제공해주는 함수. 불필요하게 반복되는 부분 문자열 검사를 피할 수 있게 해준다.

**Code**

```java
static int[] getPi(String pattern) {
    char[] pArr = pattern.toCharArray();
    int[] pi = new int[pArr.length];
    int j=0;
    for (int i=1 ; i<pArr.length ; i++) {
        while (j > 0 && pArr[i] != pArr[j]) {
            // pArr[i] != pArr[j] 일때, j 인덱스의 값에서 i 인덱스의 값과 불일치가 발생했다는 의미이기 때문에
            // 그 전 (0 to j-1) 까지의 부분 문자열 중에서 가장 긴 접두사 == 접미사 의 개수인 pi[j-1] 를 j에 
            // 대입한다. 그렇게 했을 때, 만약 개수가 2개라면, pArr[2]가 될테니, 같은 것의 개수 2개 이후인 3번째
            // 부터 i와 비교를 다시 시작하게 되는 것이다.
            j = pi[j-1];
        }
        if (pArr[i] == pArr[j]) {
            // ++j 해주는 이유는 j는 인덱스이고, pi는 같은 prefix suffix 부분 문자열의 개수를 저장해야 하기 때문.
            pi[i] = ++j;
        }
    }
    return pi;
}
```

```java
static List<Integer> kmp(String s, String p) {
    List<Integer> ans = new ArrayList<>();
    int[] pi = getPi(p);
    char[] sArr = s.toCharArray();
    char[] pArr = p.toCharArray();
    int n = sArr.length;
    int m = pArr.length;
    int j = 0;
    
    for (int i=0 ; i<n ; i++) {
        while (j>0 && sArr[i] != pArr[j]) {
            j = pi[j-1];
        }
        if (sArr[i] == pArr[j]) {
            if (j == m-1) { // 만약, pattern 문자열이 마지막인 경우,
                ans.add(i-m+1); // original 문자열의 현 위치 i를 기준으로, pattern 문자열이 시작되는 index를 저장한다.
                j = pi[j]; // j는 다음 비교를 위해 pi[j] 즉, 0 ~ j까지의 문자열에서 가장 긴 prefix == suffix의 길이를 j의 인덱스로 할당해서 다음 비교를 진행한다.
            } else {
                j++;
            }
        }
    }
    return ans;
}
```

시간복잡도: O(n+m) or O(n)

- n: length of base string -> kmp()
- m: length of pattern string -> getPi()


