---
title: "JAVA 알고리즘 기초 24문제 (124문제 완성)"
categories: [Ureca, Algorithm]
tags: [java, Algorithm]
image:
  path: /assets/post/2025/ureca/solve.png
  alt: java
published: true
---

### 1. qr code
```java
class Solution {
    public String solution(int q, int r, String code) {
        String answer = "";
        for(int i = 0 ;i < code.length() ; i++){
            if(i % q == r) answer+=code.charAt(i);
        }
        return answer;
    }
}
```

### 2. 수열과 구간 쿼리 4
```java
class Solution {
    public int[] solution(int[] arr, int[][] queries) {
        for(int[] q:queries){
            int s=q[0];
            int e=q[1];
            int k=q[2];
            for(int i=s;i<=e;i++){
                if(i % k == 0) arr[i]++;
            }  
        }
        return arr;
    }
}
```

### 3. 특수 문자 출력하기
```java
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        System.out.println("!@#$%^&*(\\'\"<>?:;");
    }
}
```

### 4. 배열 만들기 6
```java
import java.util.*;
class Solution {
    public int[] solution(int[] arr) {
        ArrayList<Integer> stk=new  ArrayList();
        for(int i=0;i<arr.length;i++){
            if(stk.isEmpty()){
                stk.add(arr[i]);
            }else if(stk.get(stk.size()-1)==arr[i]){
                //stk는 리스트라 charAt()못쓰고 get으로
                //0부터 시작이니까 size()-1
                 stk.remove(stk.size() - 1);
            }else{
                stk.add(arr[i]);   
            }
        }
        if (stk.isEmpty()) return new int[] {-1};
        
        // ArrayList<Integer>를 int[]로 변환
        int[] answer = new int[stk.size()];
        for (int j = 0; j < stk.size(); j++) {
            answer[j] = stk.get(j);
        }
        return answer;   
    }
}
```

### 5. 왼쪽 오른쪽
```java
import java.util.*;

class Solution {
    public String[] solution(String[] str_list) {
    String[] str=new String[0];
        for (int i = 0; i < str_list.length; i++) {
            if ("l".equals(str_list[i])) {
                return Arrays.copyOfRange(str_list, 0, i);
            } else if ("r".equals(str_list[i])) {
                return Arrays.copyOfRange(str_list, i + 1, str_list.length);
            }
        }
        return str;
    }
}
```

### 6. 문자열 개수 세기
```java
class Solution {
    public int[] solution(String my_string) {
    int[] count = new int[52]; // A-Z (26개) + a-z (26개)
        for (char c : my_string.toCharArray()) {
            if (Character.isUpperCase(c)) { // 대문자 처리
                count[c - 'A'] += 1;
            } else if (Character.isLowerCase(c)) { // 소문자 처리
                count[c - 'a' + 26] += 1;
            }
        }
        return count;
    }
}
```

### 7. 배열 만들기 4
```java
import java.util.ArrayList;

class Solution {
    public int[] solution(int[] arr) {
        ArrayList<Integer> stk = new ArrayList<>();
        int i = 0;
        
        while (i < arr.length) {
            if (stk.isEmpty()) {
                stk.add(arr[i]);
                i++;
            } else if (stk.get(stk.size() - 1) < arr[i]) {
                stk.add(arr[i]);
                i++;
            } else {
                stk.remove(stk.size() - 1); // pop 대신 remove 사용, length대신 size 사용
            }
        }
        return stk.stream().mapToInt(j -> j).toArray(); //ArrayList를 int형으로 변환
    }
}
```

### 8. 두수의 합
```java
import java.math.BigInteger;
class Solution {
    public String solution(String a, String b) {
        BigInteger num1 = new BigInteger(a);
        BigInteger num2 = new BigInteger(b); //Integer.parseInt로 하기에는 너무 큰 숫자를 계산 할 수 없으므로 BigInteger 사용
        BigInteger sum = num1.add(num2); //BigInterger끼리 더할때는 add메서드 사용

        return sum.toString();
    }
}
```

### 9. 문자열 여러번 뒤집기
```java
class Solution {
    public String solution(String my_string, int[][] queries) {
        // 1. 문자열을 char 배열로 변환: 문자열은 불변이라 수정하기 어렵기 때문에.
        char[] arr = my_string.toCharArray();
        // 2. queries 처리
        for (int[] query : queries) {
            int s = query[0];  // 시작 인덱스
            int e = query[1];  // 끝 인덱스

            // 3. 해당 범위 [s, e]를 뒤집기
            while (s < e) {
                // s, e 위치의 값을 교환
                char temp = arr[s];
                arr[s] = arr[e];
                arr[e] = temp;

                // 인덱스 갱신
                s++;
                e--;
            }
        }
        // 4. 배열을 다시 문자열로 변환하여 반환
        return new String(arr);
    }
}
```

### 10. 조건 문자열
```java
class Solution {
    public int solution(String ineq, String eq, int n, int m) {        
        if(ineq.equals(">")&&eq.equals("=")){
            return n >= m?1:0;
        }else if(ineq.equals("<")&&eq.equals("=")){
            return n <= m?1:0;
        }else if(ineq.equals(">")&&eq.equals("!")){
            return n > m ? 1: 0;
        }else if(ineq.equals("<")&&eq.equals("!")){
            return n < m ? 1: 0;
        }
        return 1; 
    }
}
```

## 11. 무작위로 K개의 수 뽑기
```java
import java.util.*;

class Solution {
    public int[] solution(int[] arr, int k) {
        int[] answer = new int[k];
        Arrays.fill(answer, -1); // -1로 채우기

        Set<Integer> set = new LinkedHashSet<>();
        for (int num : arr) set.add(num);

        int i = 0;
        for (int num : set) {
            if (i == k) break;
            answer[i++] = num;
        }
        return answer;
    }
}
```

## 12.수열과 구간 쿼리 2
```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] arr, int[][] queries) {
        int[] answer = new int[queries.length];
       
        for (int i = 0; i < queries.length; i++) {
            int s = queries[i][0], e = queries[i][1], k = queries[i][2];
            
            int min = -1; 
            for (int j = s; j <= e; j++) {
                if (arr[j] > k) {
                    if (min == -1 || arr[j] < min) {
                        min = arr[j];
                    }
                }
            }
            answer[i] = min;
        }
        return answer;
    }
}
```

## 13.정사각형으로 만들기
```java
class Solution {
    public int[][] solution(int[][] arr) {
        int rows = arr.length;
        int cols = arr[0].length; 
        
        if (rows > cols) {
            for (int i = 0; i < rows; i++) {
                int[] newRow = new int[rows];
                System.arraycopy(arr[i], 0, newRow, 0, cols);
// System.arraycopy(원본 배열, 복사할 항목의 시작 인덱스, 새 배열, 새 배열에서 붙여 넣을 시작 인덱스, 복사 개수) 
                arr[i] = newRow;
            }
        } else if (cols > rows) {
            int[][] newArr = new int[cols][cols];
            for (int i = 0; i < rows; i++) {
                System.arraycopy(arr[i], 0, newArr[i], 0, cols);
            }
            arr = newArr;
        }
        
        return arr;
    }
}
```

## 14. 그림 확대
```java
import java.util.Arrays;

class Solution {
    public String[] solution(String[] picture, int k) {
        int rows = picture.length;
        int cols = picture[0].length();
        String[] answer = new String[rows * k]; 
        
        for (int i = 0; i < rows; i++) {
            StringBuilder bigRow = new StringBuilder();
            for (int j = 0; j < cols; j++) {
                char c = picture[i].charAt(j); 
                bigRow.append(String.valueOf(c).repeat(k));
            }
            Arrays.fill(answer, i * k, (i + 1) * k, bigRow.toString()); 
            // answer 배열의 i * k부터 (i + 1) * k까지 bigRow로 채움
        }
        return answer;
    }
}
```

## 15. 문자열 겹쳐 쓰기
```java
class Solution {
    public String solution(String my_string, String overwrite_string, int s) {
        return my_string.substring(0, s) + overwrite_string + my_string.substring(s + overwrite_string.length(), my_string.length());
    }
}
```

## 16. a와 b 출력하기
```java
import java.util.Scanner;

public class Solution {
    static StringBuilder sb = new StringBuilder();
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();
        
        sb.append("a = ").append(a).append("\n").append("b = ").append(b);
        System.out.println(sb);
    }
}
```

## 17. 전국 대회 선발 고사
```java
import java.util.stream.IntStream;
import java.util.Arrays;

class Solution {
    public int solution(int[] rank, boolean[] attendance) {
        int answer = 0;
        int[] trueRank = IntStream.range(0, rank.length)
                    .filter(i -> attendance[i])
                    .map(i -> rank[i])
                    .toArray();
        
        Arrays.sort(trueRank);
       
        for(int i = 0; i < rank.length; i++) {
            if(rank[i] == trueRank[0]) answer += i * 10000;
            else if(rank[i] == trueRank[1]) answer += i * 100;
            else if(rank[i] == trueRank[2]) answer += i;
        }
        return answer;
    }
}
```

## 18. 대소문자 바꿔서 출력하기.
```java
import java.util.Scanner;
import java.util.Arrays;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.next();
        String answer = "";
        
        for(String alpha: a.split("")) {
            if(alpha.equals(alpha.toUpperCase())) {
                answer += alpha.toLowerCase();
            } else {
                answer += alpha.toUpperCase();
            }
        } 
        System.out.println(answer);
    }
}
```

## 19. 배열 만들기 2
```java
import java.util.stream.IntStream;

class Solution {
    public int[] solution(int l, int r) {
        int[] answer = IntStream.range(l, r + 1)
            .filter(i -> Integer.toString(i).matches("[50]+"))
            .toArray();
        
        return answer.length == 0 ? new int[]{-1} : answer;
        
    }
}
```

## 20. 코드 처리하기
```java
class Solution {
    public String solution(String code) {
        String ret = "";
        String[] cArray = code.split("");
        boolean mode = false;
        
        for(int i = 0; i < code.length(); i++) {
            if(cArray[i].equals("1")) {
                mode = !mode;
            } else {
                if(!mode && i % 2 == 0) {
                    ret += cArray[i];
                } else if(mode && i % 2 != 0) {
                    ret += cArray[i];
                }
            }
        } 
        return ret.equals("") ? "EMPTY" : ret;
    }
}
```

## 21. 배열 조각하기
```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] arr, int[] query) {
        for(int i = 0; i < query.length; i++) {
            if(i % 2 == 0) {
                arr = Arrays.copyOfRange(arr, 0, query[i] + 1);
            } else {
                arr = Arrays.copyOfRange(arr, query[i], arr.length);
            }
        }
        
        return arr;
    }
}
```

## 22. 문자열 출력하기
```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.next();
        
        System.out.println(a);
    }
}
```

## 23. 주사위 게임 3
```java
import java.util.*;

class Solution {
    public int solution(int a, int b, int c, int d) {

        int[] arr = {a, b, c, d};
        Arrays.sort(arr);
        
        if(a == b && b == c && c == d) {
            return 1111 * a;
        } else if (arr[0] == arr[2]) {
            return (int)Math.pow(10 * arr[0] + arr[3], 2);
        } else if (arr[1] == arr[3]) {
            return (int)Math.pow(10 * arr[3] + arr[0], 2);
        } else if (arr[0] == arr[1] && arr[2] == arr[3]) {
            return (arr[0] + arr[2]) * Math.abs(arr[0] - arr[2]);
        } else if (arr[0] == arr[1]) {
            return arr[2] * arr[3];
        } else if (arr[1] == arr[2]) {
            return arr[0] * arr[3];
        } else if (arr[2] == arr[3]) {
            return arr[0] * arr[1];
        } else {
            return arr[0];
        }
    }
}
```

## 24. 정수를 나선형으로 배치하기
```java
class Solution {
    public int[][] solution(int n) {
        int[][] answer = new int[n][n]; // 정답 배열
        
        // 방향: 오른쪽(→), 아래(↓), 왼쪽(←), 위쪽(↑)
        int[] dx = {0, 1, 0, -1};
        int[] dy = {1, 0, -1, 0};
        
        int x = 0, y = 0, dir = 0; // 초기 위치 및 방향
        for (int num = 1; num <= n * n; num++) {
            answer[x][y] = num; // 현재 위치에 숫자 삽입
            
            // 다음 이동 위치
            int nx = x + dx[dir];
            int ny = y + dy[dir];
            
            // 범위를 벗어나거나 이미 숫자가 채워진 경우 방향 전환
            if (nx < 0 || nx >= n || ny < 0 || ny >= n || answer[nx][ny] != 0) {
                dir = (dir + 1) % 4; // 방향 변경
                nx = x + dx[dir];
                ny = y + dy[dir];
            }
            x = nx;
            y = ny;
        }
        return answer;
    }
}
```

--- 

<img src="/assets/post/2025/ureca/solve.png" alt='' width=1300px>


---

## END